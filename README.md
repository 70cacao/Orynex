# Orynex

A Windows 11 desktop assistant that lives at the edge of your screen. It answers,
it acts on the machine, and it keeps what it learns on the machine.

**[→ Download Orynex 0.3.1](https://github.com/70cacao/Orynex/releases/download/v0.3.1/Orynex_0.3.1_x64-setup.exe)** · Windows 11 · 87 MB · [release notes](https://github.com/70cacao/Orynex/releases/tag/v0.3.1)

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

**4 · Give it a key. Nothing works before this.** Open the workspace — hover the
dot at the top edge, then the ⤢ button — and go to **Account → KI-Anbieter**.
Paste an API key and press Verbinden. **The provider is detected from the key
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

Nothing leaves the machine except the call to the model provider. Conversation
history, the searchable memory, the decision log and every learned pattern live
in a local SQLite database.

**You bring your own key.** Orynex has no server between you and the provider:
your key goes into the Windows Credential Manager, and the client calls the
provider directly. Six providers are supported, with tool calling, vision and
streaming across all of them.

## Four stages, one application

It grows only as far as the task needs.

| | |
| --- | --- |
| **Orb** | A dot at the edge of the screen. Idle, ambient, out of the way. |
| **Bar** | Hover it: CPU, GPU, memory, battery, media controls. |
| **Quick panel** | One question, or one of the programs you named yourself. |
| **Workspace** | The full window — chat, tools, memory, decision log, settings. |

## What it can do

Around thirty tools, grouped by area, each one declaring what it needs before it
runs: start and focus applications, media and volume, system state, clipboard,
web search and opening pages, RSS feeds, weather, reading Windows notifications
and replying in a messenger, reading the screen, and a set of read-only GitHub
tools.

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

Currently **816 tests** green, alongside a written architecture and a decision
log that records why things are the way they are rather than only what they do.

## Availability

**[Orynex 0.3.1](https://github.com/70cacao/Orynex/releases/tag/v0.3.1)** — a
pre-release, published on 8 September 2026.

It is **not code-signed**. Windows SmartScreen will say *"unknown publisher"*;
that is about the missing certificate, not about the file. **More info → Run
anyway** gets past it. A certificate costs several hundred euros a year and this
is a hobby project so far — saying so plainly seemed better than waiting.

## Licence

Proprietary — see [LICENSE](LICENSE). All rights reserved. The software may be
used, once distributed, but not modified, redistributed or published. This is
not an open-source project and code contributions are not accepted.

For licensing enquiries: micha@ceruleancircle.com
