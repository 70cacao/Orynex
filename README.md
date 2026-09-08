# CoPilot

A Windows 11 desktop assistant that lives at the edge of your screen. It answers,
it acts on the machine, and it keeps what it learns on the machine.

**Status: in development. Not released, and the source is not public.** This
repository is the project's public face — what it is, how it is built, and what
it deliberately does not do. See [LICENSE](LICENSE): all rights reserved.

---

## What it is

Most assistants are a website in a window. CoPilot is a native application: Rust
and [Tauri v2](https://tauri.app) underneath, React and TypeScript on top, and it
talks to the Windows APIs directly. **No Python, no second runtime** — one binary
and an installer.

Nothing leaves the machine except the call to the model provider. Conversation
history, the searchable memory, the decision log and every learned pattern live
in a local SQLite database.

**You bring your own key.** CoPilot has no server between you and the provider:
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
- **Nothing is proposed from what it has learned.** CoPilot observes which
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

Currently **807 tests** green, alongside a written architecture and a decision
log that records why things are the way they are rather than only what they do.

## Availability

There is no download yet. When there is, it will be a signed installer published
here.

## Licence

Proprietary — see [LICENSE](LICENSE). All rights reserved. The software may be
used, once distributed, but not modified, redistributed or published. This is
not an open-source project and code contributions are not accepted.

For licensing enquiries: micha@ceruleancircle.com
