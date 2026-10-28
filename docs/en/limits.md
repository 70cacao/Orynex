# Known limits

[Deutsch](../de/grenzen.md) · [Overview](../README.md)

What Orynex 1.0 deliberately cannot do yet, or where there is a risk we know and accept. Better here than as a surprise.

| Limit | Why |
| --- | --- |
| The installer is not signed; Windows SmartScreen warns on the first start ([what to do](install.md#2--the-windows-warning-windows-protected-your-pc)). The checksums are in the release notes, and the updates themselves are signed. | a certificate costs money every year; Orynex is a private project |
| Installing and every update need an admin password. | Orynex lives in `Program Files` so that no program can change it; the helper for admin actions relies on that |
| Anthropic and Google Gemini are checked with automated tests only, not with a real key. OpenAI and xAI use the same path as Groq. | no key to test with |
| NVIDIA no longer accepts a new key. | NVIDIA's terms allow the free access for development only |
| From away (Telegram, calls), Orynex works only while your PC is on and Orynex is running. | Orynex has no server; everything runs on your PC |
| Calls go through the Linphone app and two free accounts, not through an app of its own or a phone number. | no cost, no server |
| Undo covers what Orynex creates in its own data (a rule, the mail list, a tracker entry, a timer, a note), for seven days, once — not changes to the system (an ended program, the volume). | a way back that does not hold for sure would be a false promise |
| *Stop* ends the wait for the AI at once; a tool that is already running finishes. | a half-run tool would be worse |
| Tasks run only while Orynex runs. After a restart, a running task shows as *interrupted* and is not resumed; a step that changed something and has no recorded end is *unclear* and is never repeated by itself. | resuming comes later |
| llama.cpp and LM Studio are experimental; Ollama is the measured local path. Local models are slower and less accurate than large cloud models. | not measured |
| Your own connections (MCP, OpenAPI) are experimental. | the full proof of permissions is still open |
| The phone browser (Orynex on your home network) is hidden in 1.0. | only half built |
| There is no button yet that deletes everything including keys; uninstalling leaves data and keys behind on purpose ([how to do it by hand](permissions-and-data.md#backup-and-deletion)). | in progress |
| Some error messages appear in German even when the app is set to English. | being translated |
| Mail: Outlook.com and Hotmail accounts do not work; Orynex cannot send attachments. | Microsoft switched off password sign-in |
| What a cloud AI does with your messages is governed by your provider's terms. With a local AI and Full Privacy nothing goes out. | Orynex has no server of its own and sees none of it |
| How much memory and processor Orynex uses over hours has not been measured yet. | planned before 1.0 |
