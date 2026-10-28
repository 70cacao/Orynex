# When something does not work

[Deutsch](../de/fehlerbehebung.md) · [Overview](../README.md)

Start with *Overview → Self-check*. It shows for the AI, storage, web search, kill switch, helper service and sensors whether they run. **Grey means "not set up", not "broken".**

## Orynex does not answer

| What you see | What is behind it | What helps |
| --- | --- | --- |
| *"I still need an AI provider"* | no key and no local model | [Set up](setup.md) |
| *"The provider's limit is reached"* | the free tier is used up for now | wait a little, or add a second provider under *Account* and switch on *Switch at the limit* |
| *"The provider rejected the API key"* | key wrong, expired or revoked | create a new key with the provider, replace it under *Account* |
| *"The local AI does not answer at …"* | Ollama is not running | start Ollama, then *Account → Search again* |
| *"Answer cut off"* | the connection to the provider broke mid-text | ask again; the part that already came stays |
| *"Full Privacy is on — cloud AI is blocked"* | Full Privacy allows only a local AI | pick a local model or switch Full Privacy off |

## A feature is missing or greyed out

- **Its add-on is off.** Switch it on under *Add-ons*. What is off does not run at all and is not offered to the AI.
- **It needs setting up**, e.g. mail, calendar or web search. The self-check and *Tools* say "needs setup".
- **Full Privacy is on.** Then web search, weather, news, mail, calendar, GitHub and voice input are off.

## Voice and microphone

- *"Voice input is off"*: switch it on under *Settings → Privacy*.
- *"Access to the microphone was denied"*: two places ask separately, the switch in Orynex and Windows itself. Under *Windows Settings → Privacy & security → Microphone*, allow access for desktop apps.
- Many laptops have no `Pause` key. Enter another one under *Settings → Behaviour → Push-to-talk key*.

## Shortcuts do nothing

If another program already uses a combination, the previous one stays active and Orynex says so (for the kill switch with a notice at the top of the window). Pick another under *Settings → Behaviour*.

## Notifications are missing

Reading them must be switched on under *Settings → Privacy*, and Windows asks once more for permission itself the first time.

## Updates

| Message | means |
| --- | --- |
| *"GitHub delivered no update information right now"* (currently still shown in German) | a problem on GitHub's side; try again later |
| *"GitHub cannot be reached"* / *"The download broke off"* | check the internet connection, try again |
| *"The update carries no valid signature"* | Orynex deliberately does not install it; please report it ([Security](../../SECURITY.md)) |
| Windows asks for an admin password | normal: Orynex lives in `Program Files` ([why](install.md#3--the-installer)) |

## Calls do not come through

The *Call* page shows the status at the top. If it says *"not signed in since …"*, Orynex lost its connection to the call server (often after a Wi-Fi change) and signs in again by itself. If it says *"signing in … are account and password right?"* for more than half a minute, the sign-in is wrong.

## Orynex does not react at all

1. Right-click the Orynex icon in the taskbar's notification area (often hidden under `^`) → *Quit*. From 0.14 *Quit* is also at the bottom of the sidebar.
2. If that does not help: Task Manager → *Orynex* → *End task*.
3. Start Orynex again.

## Reporting a bug

From version 0.14, *Log → Create error report* puts a file into your Downloads folder: the logs of the last three days (keys and secrets blacked out), the self-check and the version — **without** chats, settings or keys. Nothing is sent automatically.

Report bugs under [Issues](https://github.com/70cacao/Orynex/issues). Security problems please **not** in public: see [SECURITY.md](../../SECURITY.md).
