# Orynex

A Windows 11 desktop assistant that lives at the edge of your screen. It answers,
it acts on the machine, and it keeps what it learns on the machine.

**[→ Download Orynex 0.4.9](https://github.com/70cacao/Orynex/releases/download/v0.4.9/Orynex_0.4.9_x64-setup.exe)** · Windows 11 · 87 MB · [release notes](https://github.com/70cacao/Orynex/releases/tag/v0.4.9)

**New in 0.4.9: scenes** — *"Gaming"* starts Discord, pauses Spotify and brings Valorant to the front, from one chip or by typing its name. No AI involved, so no tokens and no wait — [see below](#scenes). Since 0.4.6 the AI can also run on your own PC, with a Full Privacy switch — [see below](#cloud-or-local-and-full-privacy).

**Status: pre-release, and the source is not public.** It is not code-signed yet,
so Windows will warn about an unknown publisher — the release notes say why, and
what else is unfinished. This repository is the project's public face: what it
is, how it is built, and what it deliberately does not do. See
[LICENSE](LICENSE): all rights reserved.

---

## Install

**1 · Download and run it.** Windows will stop you: *"Windows protected your PC —
unknown publisher"*. That is the missing code-signing certificate, not the file.
Click **More info**, then **Run anyway**. If you would rather not — that is a
reasonable instinct and there is nothing here to argue with it.

**2 · Say yes to the admin prompt.** It installs into `Program Files` and
registers one small helper that runs elevated. The assistant itself never does
(see below).

**3 · Pick a language,** then two choices with sensible defaults: install the
privilege broker (say yes — without it a few actions report themselves as
unavailable), and start with Windows.

**4 · Choose where the AI runs. Nothing works before this.** Open the workspace —
hover the dot at the top edge, then the ⤢ button — and go to **Account**.

*Local:* install [Ollama](https://ollama.com/download), then in **KI: Cloud oder
Lokal** pick a model you already have, or choose one from the tiers Orynex shows
for your GPU — *Minimum* from 4 GB, *Empfohlen* 12–16 GB, *Advanced* from 32 GB —
and download it with one click. No key, no account.

*Cloud:* under **KI-Anbieter (Cloud)**,
paste an API key and press Verbinden. **The provider is detected from the key
itself**, so there is nothing to choose: `gsk_…` is Groq, `sk-…` OpenAI or
Anthropic, `AIza…` Google, and so on. The key is checked once against the
provider and then goes into the Windows Credential Manager — never into a file,
never into a log.

> **No key yet?** Groq issues one free at [console.groq.com](https://console.groq.com)
> and is what this was built against. There is no account with *me* and no server
> in between — your key talks to your provider, directly.

**5 · Optional:** a [Tavily](https://tavily.com) key on the same page turns on web
search. Everything else works without it.

**Uninstalling** is the ordinary way: Settings → Apps → Orynex. Your conversations,
notes and settings are deliberately left behind, in
`%APPDATA%\com.ceruleancircle.copilot` — uninstalling an app is not the same as
asking it to forget. Delete that folder if you want it gone.

## What it is

Most assistants are a website in a window. Orynex is a native application: Rust
and [Tauri v2](https://tauri.app) underneath, React and TypeScript on top, and it
talks to the Windows APIs directly. **No Python, no second runtime** — one binary
and an installer.

Conversation history, the searchable memory, the decision log and every learned
pattern live in a local SQLite database. What leaves the machine is the request to
the model — unless the model runs locally — and the calls a tool makes when you
ask for something outside it, like the weather or your calendar. With Full Privacy
on, Orynex makes neither.

**You bring your own key — or your own model.** Orynex has no server between you
and the provider: your key goes into the Windows Credential Manager, and the
client calls the provider directly. Six cloud providers are supported (Anthropic,
OpenAI, OpenRouter, Groq, xAI, Google Gemini), with tool calling, vision and
streaming across all of them — and local models through Ollama or any
OpenAI-compatible server on your PC.

## Cloud or Local, and Full Privacy

Orynex owns the harness: the tools, the safety checks, the memory, the interface.
The language model is a replaceable part. Two switches decide how much of it stays
home.

| Switch | What it does |
| --- | --- |
| **Cloud or Local** | Cloud uses your own API key. Local uses a model on your PC through Ollama (or LM Studio and similar): Orynex finds the runtime, lists what you have, suggests models in three tiers by GPU memory, downloads one on a click and loads it right away, so the first answer does not wait. |
| **Full Privacy** | Orynex sends nothing to an external AI or cloud service. Cloud AI is locked; tools that call outside services — web search, weather, news, mail, calendar, GitHub — are off; speech input, which uses a cloud transcription service, is off. |

What makes that more than a label — each of these is a rule in code with a test
that fails if the rule is removed:

- **No silent fallback.** If the local model fails, you get an error that says what
  to do. Orynex never quietly asks a cloud provider instead, even with a key stored,
  and Full Privacy never quietly changes your model either.
- **Every model gets the same checks.** A local model is exactly as untrusted as a
  cloud one: its tool calls pass the same kill switch, privacy gate, permission
  check and argument validation.
- **Local means this machine.** Local addresses are accepted on loopback only, no
  API key is ever sent to a local server, and Ollama's own *cloud* models — which
  answer on the same local port but compute elsewhere — are refused in Local mode.
- **Enough context.** Orynex asks Ollama for an 8 192-token context through its
  native API; left alone, Ollama cuts long prompts to 4 000 tokens on most GPUs
  without saying so.
- **Measured on a real machine, not assumed.** On a 4 GB laptop GPU, a small local
  model could not follow the extra "which area?" round Orynex uses to save cloud
  tokens (0 of 12), but picked the right tool from the full list in 12 of 18 runs —
  so local turns skip that round, since local tokens cost nothing. Preloading the
  model cut the first answer from ~50 seconds to ~0.3.

What it does **not** claim: that nothing leaves your PC. Windows, your other
programs and a page you ask Orynex to open are not Orynex's to promise. A local
model can also be slower and less accurate than a large cloud model — the
capabilities stay the same, how well a model uses them does not.

## Four stages, one application

It grows only as far as the task needs.

| | |
| --- | --- |
| **Orb** | A dot at the edge of the screen. Idle, ambient, out of the way. |
| **Bar** | Hover it: CPU, GPU, memory, battery, media controls. |
| **Quick panel** | One question, or one of the programs you named yourself. |
| **Workspace** | The full window — chat, tools, memory, decision log, settings. |

## Scenes

Several programs, one press. A scene is a name and up to six steps, and a step
is one of four things: **start a program** (or bring it forward if it runs, or
leave it alone if it already is — pressing twice starts nothing twice), **open a
web address**, **open a Spotify search**, or **play, pause or skip in a named
app**. Nothing else, on purpose: a scene runs days after it was written, with
nobody watching, so every step has to mean the same thing tomorrow. A click on
*"Send"* in another program does not — so scenes never click — and a play/pause
*toggle* would start the music it was meant to stop, so there is none.

Make one in the settings, or say *"open discord and spotify"* in the chat and keep
what happened under a name. It sits as a chip in the quick panel, and its name
typed alone into the chat runs it — without the AI. Every step goes through the
same permission checks as a tool the AI calls, and the kill switch stops a scene
between two steps.

## What it can do

Around thirty tools, grouped by area, each one declaring what it needs before it
runs: start and focus applications and open folders, media and volume, system
state, clipboard, web search and opening pages, RSS feeds, weather, reading mail
and Google Calendar, reading Windows notifications and replying in a messenger,
reading the screen, and a set of read-only GitHub tools.

The model does not get a free hand. A shortlist round narrows thirty tools to the
handful that could plausibly matter before any of them is offered, and a phrase
that has already resolved to exactly one tool runs again without asking the model
at all.

## What it deliberately does not do

This part matters more than the feature list.

- **The application never runs as administrator.** The handful of actions that
  genuinely need admin rights go through a separate, small helper process
  registered as a scheduled task. The surface that runs elevated stays small
  enough to read in one sitting.
- **Every tool declares the capability it needs**, and the check happens in the
  router before the tool runs — never inside the tool. A new tool cannot quietly
  grant itself something.
- **Secrets are never in a configuration file or a log.** They live in the
  Windows Credential Manager, and the provider key never leaves the module that
  talks to the provider.
- **Screen perception and control are explicit, opt-in and on demand.** No silent
  background capture, no autonomous clicking. Consent is asked for, the click
  marker is shown *before* anything is pressed, and every screen action is
  logged.
- **Nothing is proposed from what it has learned.** Orynex observes which
  programs and tools you use together and counts them, and that is where it
  stops. The counts are visible and deletable; nothing acts on them.
- **Deletion is complete.** Clearing the history removes the transcript *and* its
  search index, in that order — an index that outlives its source is a privacy
  defect, not an untidiness.

## Memory

A small local model turns conversations, notes and documents into vectors —
about 130 MB shipped with the application, so retrieval works with no network
and no second service. Vector search is fused with SQLite's own full-text search,
because the things people ask about by name — a file, a version, an error string
— are exactly what embeddings are worst at.

What was retrieved, what it scored, and why a turn decided what it decided is
visible on the decision log. The assistant does not get to be a black box on its
own machine.

## Built with

Rust · Tauri v2 · React · TypeScript · SQLite (FTS5) · ONNX Runtime · native
Windows APIs · NSIS

Currently **1 176 tests** green, alongside a written architecture and a decision
log that records why things are the way they are rather than only what they do.
Security rules are checked by mutation: remove the rule, and a test has to fail.

## Availability

**[Orynex 0.4.9](https://github.com/70cacao/Orynex/releases/tag/v0.4.9)** — a
pre-release, published on 18 September 2026. Scenes have been driven by hand
against a real desktop, including pressing one twice. The local path has been run against
a real Ollama with a small model, and the fix in this release was measured
through the app's own request builder rather than by hand; larger models follow
Ollama's published sizes and have not been run here. Mail and calendar are not yet tried against real
accounts, and the AI-driven half of cross-app automation is not built yet. The release notes list what else is unfinished.

It is **not code-signed**. Windows SmartScreen will say *"unknown publisher"*;
that is about the missing certificate, not about the file. **More info → Run
anyway** gets past it. A certificate costs several hundred euros a year and this
is a hobby project so far — saying so plainly seemed better than waiting.

## Licence

Proprietary — see [LICENSE](LICENSE). All rights reserved. The software may be
used, once distributed, but not modified, redistributed or published. This is
not an open-source project and code contributions are not accepted.

For licensing enquiries: micha@ceruleancircle.com
