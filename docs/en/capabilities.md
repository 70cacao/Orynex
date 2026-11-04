# What Orynex can do, and what is planned

[Deutsch](../de/faehigkeiten.md) · [Overview](../README.md) · [Plain text for other AIs](https://raw.githubusercontent.com/70cacao/Orynex/main/docs/en/capabilities.md)

*State: Orynex 1.0.3, 4 November 2026. A Windows 11 desktop assistant, native (Rust, Tauri v2, React), free to use, with no account and no server of ours in between.*

**How to read the status:**

| Mark | Meaning |
|---|---|
| **In 1.0** | Released and tested; most of it in daily use by the developer |
| **In 1.0, tests only** | Released and tested, not yet seen on real services |
| **Experimental** | Released, little real use, may change |
| **Coming next** | Being built or next in line, not released |
| **Idea** | Wanted one day, nothing started, no promise |

## What it thinks with

| | Status |
|---|---|
| Your own key: Groq, xAI, OpenRouter | In 1.0 |
| OpenAI (same connection as Groq and xAI) | In 1.0 |
| Anthropic, Google Gemini (connections of their own) | In 1.0, tests only |
| Cloudflare Workers AI | In 1.0, tests only |
| A local model through Ollama: no key, nothing leaves the PC | In 1.0 |
| llama.cpp, LM Studio | Experimental |
| Moving to your next provider at a limit | In 1.0 |
| Full Privacy: no cloud at all | In 1.0 |

## What it does on your PC

Over sixty tools. What changes something asks first or can be undone, and everything that ran is listed.

| Area | What | Status |
|---|---|---|
| Programs | Start, bring to the front, close, open folders | In 1.0 |
| Files | Read folders and text files, with a block list for secrets | In 1.0 |
| Writing files | PDF, Word, PowerPoint, Markdown, text, CSV, JSON, HTML. Never overwrites | In 1.0 (PowerPoint looks plain) |
| Web | Search, read a page without a browser, open a page, news and RSS, weather | In 1.0 |
| Mail | Read, write with a card before each send (Outlook.com and Hotmail do not work) | In 1.0 |
| Calendar | Read through a link, add or change with your Google project | In 1.0 |
| Screen | Read it, click and type, only on your request | In 1.0 |
| Music and sound | Spotify plays what you asked for, media keys, volume | In 1.0 (a Spotify update can break it) |
| System | State of the PC, power plan, settings, clipboard, a checkup | In 1.0 |
| Windows notifications | Read them, answer in a messenger | In 1.0 |
| GitHub | Issues, pull requests, CI, read only | In 1.0 |
| Your own connections | MCP and OpenAPI, each capability approved by you | Experimental |
| Restart a service, set a process priority | Through a small helper with admin rights, needs a Pro licence | In 1.0 |

## Bigger jobs, without you

| | Status |
|---|---|
| **Tasks:** you approve goal and plan, Orynex works in the background, checks the result and gives you a report, with copy, PDF and send buttons | In 1.0 |
| **Rules:** by time, when a program starts, on new mail and more, each with a limit on how far it may go alone | In 1.0 |
| **Watchers:** prices, availability, news | In 1.0, tests only |
| **Scenes:** set up your desktop with one sentence | In 1.0 |
| **Flows:** several steps planned at once, across programs | Experimental (the model does not always pick them) |
| Offers habits you repeat as a rule, and prepares a morning report | In 1.0 |
| **Agents:** general rules, agents with rules of their own bound to folders. Orynex picks who works, at the desk, on Telegram and on a call. Files sent over Telegram go into the agent's folder | In 1.0.1 |

## Reaching it from away

| | Status |
|---|---|
| Telegram: text and voice messages, cards with yes and no, sends you messages and files | In 1.0 (a file sent by mail has not been used for real) |
| Calls: Orynex calls you and you call it, through the Linphone app and two free accounts, also with a locked PC | In 1.0 |
| It tells you on its own when something matters, with quiet hours and a daily limit | In 1.0 |

Your PC has to be on and awake. Orynex has no server.

## Memory and you

| | Status |
|---|---|
| Remembers what you tell it and what it learns from mail, shows everything, forgets on request | In 1.0 |
| Cleans up duplicates, keeps addresses and phone numbers from mail out of your requests | In 1.0 |
| Personality: presets, sliders, or your own words | In 1.0 |
| Trackers: food, water, sleep, training, habits, all on the PC | In 1.0 |
| Companion on the desktop, with a wardrobe | In 1.0 |
| German and English, hold-to-talk, voices that run on your PC | In 1.0 |

## Safety

| | Status |
|---|---|
| Keys only in the Windows Credential Manager | In 1.0 |
| Five risk rings and cards before anything serious | In 1.0 |
| Kill switch on a shortcut and by `/stop` | In 1.0 |
| Activity page with undo for what Orynex created | In 1.0 |
| A dialog to end Orynex if its window freezes | In 1.0 |
| Delete everything, keys included | In 1.0 (tried on a test profile) |
| Local log and a bug report you send yourself. No telemetry | In 1.0 |

## Known limits

Not code-signed, so Windows warns on the first start. Updating needs an administrator password. The phone browser is held back. More: [limits](limits.md).

## Coming next

In this order. Nothing here is released yet, and the order can change.

1. **Workbench.** Drop all your work in, and Orynex works through it.
2. **Your own workbenches.** Connect any MCP server and build your own bench; Orynex sees what fits together and suggests how to use it.
3. **Orynex learns your world.** It asks a good question now and then, picks the right moment, tells fact from guess. You can see, correct and delete all of it.
4. **Orynex Anywhere.** Your own website, hosted by your PC: a full, customisable interface for every feature, working on every device like an app, with accounts and permissions for other people. Together with it, the camera in a call: *"what is this?"*.
5. **Linux and Tails.** The local features on Linux, and a whole assistant on a Tails stick, installed with one command.

## Ideas, no promise

A companion that reacts to what you do and acts when you ask. Smart home. A car, read only. A watch.

*The everyday features stay free: chat, Telegram and the like. The big features for power users, such as agents, tasks and whole automated workflows, may need a Pro licence later. You can [request a Pro licence for a limited time](https://github.com/70cacao/Orynex/issues/new?title=Pro%20licence%20request) and enter it on the Account page.*
