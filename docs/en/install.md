# Installing Orynex

[Deutsch](../de/installieren.md) · [Overview](../README.md)

## What you need

| | |
| --- | --- |
| **Windows** | Windows 11, 64-bit. Windows 10 is not tested. |
| **Space** | about 100 MB for Orynex itself; a local AI model needs several GB more. |
| **Internet** | for a cloud AI, web search, weather, mail and calendar. With a local AI and *Full Privacy*, Orynex works without it. |
| **An AI provider** | a free API key is enough (Groq, for example), or a model on your PC with Ollama. See [Set up](setup.md). |
| **Admin password** | once for installing and for every update (explained below). |

How much memory and processor Orynex uses day to day has not been measured yet. It is developed and tested on a laptop with 16 GB.

## 1 · Download

The installer is on the [release page](https://github.com/70cacao/Orynex/releases/latest): `Orynex_<version>_x64-setup.exe`.

**You can check that the file is genuine.** The release notes give its SHA-256 checksum. In PowerShell:

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\Orynex_0.13.0_x64-setup.exe"
```

If the number shown matches the one in the release notes, it is exactly the file that was published.

## 2 · The Windows warning ("Windows protected your PC")

On the first start, Windows SmartScreen says: *"Unknown publisher"*.

**Why:** the installer is not signed with a bought certificate. Such a certificate costs money every year, and Orynex is still a private project. SmartScreen warns about every new unsigned file, even when nothing is wrong with it. The warning means *"Windows does not know this file yet"*, not *"this file is dangerous"*.

**To go on:** click **More info**, then **Run anyway**.

If that feels uncomfortable, that is a reasonable instinct. Check the checksum first (above), or upload the file to [VirusTotal](https://www.virustotal.com). The updates themselves are signed: Orynex installs an update only if it is signed with the key built into the app.

## 3 · The installer

1. **Pick a language** (German or English). Orynex starts in it; you can switch any time under *Settings → Appearance*.
2. **Confirm the admin prompt.** Orynex installs into `C:\Program Files\Orynex`, for every account on the PC. That is a security decision: an ordinary program cannot change that folder, and the small helper below relies on it.
3. **Two defaults**, both recommended:
   - **Install the privilege broker** — a small service for the few actions that need administrator rights. Orynex itself never runs with admin rights. Without the broker everything else works as usual; those actions simply report themselves as unavailable.
   - **Start when I log on** — Orynex then rests as a small circle at the edge of the screen until you touch it.

**Without admin rights** (a child's or a work account, for example): someone with the admin password has to confirm the installation, and every update too.

## 4 · The first start

Orynex appears as a circle at the edge of the screen, and the first-run setup opens. Every step can be skipped and started again later (*Help → Introduction*). The one that matters is the AI provider — without it Orynex does not answer: [Set up](setup.md).

| Shortcut | What it does | change under |
| --- | --- | --- |
| `Ctrl + Shift + Space` | open Orynex | Settings → Behaviour |
| `Ctrl + Alt + Shift + Esc` | **kill switch**: everything that changes something stops at once | Settings → Behaviour |
| `Pause` (hold) | push-to-talk | Settings → Behaviour |

## Updates

*Account → Updates → Check for updates.* Orynex asks GitHub only when you press that button; there is no automatic update check. An update it finds is checked for its signature before it installs, and like the installation it needs the admin prompt. Your chats, settings and keys are kept.

## Uninstalling

*Windows Settings → Apps → Installed apps → Orynex → Uninstall.* That removes the program, the helper service and the autostart.

**Left behind on purpose**, so a reinstall finds your history:

- your data in `%APPDATA%\com.ceruleancircle.copilot` and `%LOCALAPPDATA%\com.ceruleancircle.copilot` (chats, memory, settings, logs, voices);
- your keys and passwords in the Windows Credential Manager.

How to remove both completely: [Backup and deletion](permissions-and-data.md#backup-and-deletion).
