# What Orynex may do, and what happens to your data

[Deutsch](../de/rechte-und-daten.md) · [Overview](../README.md)

## What Orynex may do

Every permission is in one place: *Permissions*. A **level** sets them all at once; afterwards you can change each switch on its own.

| Level | allows |
| --- | --- |
| **Low** | reading Windows notifications |
| **Medium** | plus voice input, work context (which program is in front, never window titles) and learning from habits |
| **High** | plus controlling the screen, sending mail and appointments from mail |

**The same at every level:**

- **Anything that changes something asks first with a card** — a mail, a calendar entry, ending a program, a command. The card shows exactly what will happen (for a mail, the whole text), and your yes holds for exactly that. No answer means no.
- **If Orynex read someone else's text before** (a mail, a web page, the screen), it always asks before clicking or typing in another program. Outside text could have slipped instructions to the AI.
- **The kill switch** (`Ctrl + Alt + Shift + Esc`, from away `/stop` in Telegram) stops everything that changes something at once. Answering questions goes on.
- **Orynex never runs with administrator rights.** The few actions that need them go through the small helper service from the installation, and the kill switch stops those too.
- **No silent watching:** the screen is read only when you ask. The microphone is open only while you hold the push-to-talk key.

### Automations and tasks (when you are not looking)

Each rule under *Automations* says how far it may go without you, in five rings:

| Ring | may do without you |
| --- | --- |
| 0 · Read | weather, news, web search, system values |
| 1 · Read private | plus mail, calendar, files, notifications |
| 2 · Change locally | plus scenes that end nothing, media, opening apps and folders |
| 3 · Send out or end | plus mail to addresses on your list, ending programs |
| 4 · Irreversible | deleting, reading or controlling the screen — **never runs without you** |

Anything above a rule's ring waits 30 minutes for your yes on a card; after that it is no. A *task* (*As a task* in the chat) shows its plan and limits first and runs only after your yes.

### From away (Telegram, calls)

What comes from away goes through a **traffic light**: reading and harmless things run as at the PC; anything that goes out or ends something is checked by a second AI, which then asks you on the phone; the screen, commands and anything irreversible work only at the PC. Chats with Telegram bots are not end-to-end encrypted.

### Undo

What Orynex creates in its own data (a rule, an address on the mail list, a tracker entry, a timer, a note) can be taken back under *Activity* for seven days. Changes to the system (a program that was ended, the volume) cannot be brought back — which is why they ask first.

## What goes where

| What | where to |
| --- | --- |
| Your messages, the conversation, the context sent along | to your AI provider — with a local AI, nowhere |
| What Orynex reads from mail, calendar, screen, files | to your AI provider, when an answer needs it |
| Voice input (the recording) | to your AI provider for recognition, not stored |
| Text read aloud | nowhere (Windows voice, Piper), or to ElevenLabs if you choose it |
| Keys and passwords | into the Windows Credential Manager, nowhere else |
| Chats, memory, trackers, rules | onto this PC, nowhere else |

Orynex has **no telemetry** and no server of its own. Updates are looked for only when you press the button. Which connections went out since it started is listed under *Settings → Privacy*.

## Backup and deletion

**Where the data is:**

| Folder | contains |
| --- | --- |
| `%APPDATA%\com.ceruleancircle.copilot` | `orynex.db` (chats, memory, rules, trackers, contacts …), `prefs.json` (settings), the recording if you switched it on |
| `%LOCALAPPDATA%\com.ceruleancircle.copilot` | log files, voices, call data |
| Windows Credential Manager | API keys, app passwords, tokens (entries with `com.ceruleancircle.copilot` or `orynex-sip` in the name) |

The name `com.ceruleancircle.copilot` is a technical leftover from before Orynex was called Orynex; it stays so that an update loses nothing.

**Backup:** quit Orynex (right-click its icon in the taskbar's notification area → *Quit*), then copy the folder `%APPDATA%\com.ceruleancircle.copilot`. Keys are not part of it; you enter them again after a reinstall.

**Deleting in the app:**

- *Settings → Data:* clear the chat history, delete what was remembered, delete learned habits, delete remembered commands, delete the recording.
- *Memory:* forget single entries, or *Forget everything*.
- *Account:* remove each key and each connection on its own.

**Removing everything** (there is no single button for it yet):

1. Uninstall Orynex (see [Install](install.md#uninstalling)).
2. Delete the two folders above.
3. *Control Panel → Credential Manager → Windows Credentials*: remove the entries with `com.ceruleancircle.copilot` or `orynex-sip` in the name.
4. For Gmail, revoke the app password at `myaccount.google.com/apppasswords`; for Google Calendar and Telegram, revoke access there or delete the bot.
