# Set up: what Orynex thinks with

[Deutsch](../de/einrichten.md) · [Overview](../README.md)

Orynex itself is free and has no server of its own. The answers are written by a language model, and that comes from you: **either an API key from a provider (cloud) or a model on your PC (local).** Both are set under *Account*.

## The quickest way: a free key from Groq

1. Sign in at [console.groq.com](https://console.groq.com) and create a key under *API Keys*. It starts with `gsk_`.
2. In Orynex, paste it under *Account → AI provider (cloud)* and press **Connect**.

Orynex recognises the provider from the key itself and picks the model. The key is checked once with the provider and then kept in the **Windows Credential Manager** — never in a file, never in the log. Orynex sends it only to that provider.

**What goes out:** with a cloud AI, your messages, the conversation and the context Orynex sends along go to the provider. What the provider does with them is governed by its terms, not by Orynex.

## Other providers

| Provider | Key starts with | Note |
| --- | --- | --- |
| Groq | `gsk_` | free tier; what Orynex was built against |
| OpenRouter | `sk-or-` | many models, free ones too |
| Anthropic | `sk-ant-` | checked with unit tests only, no live test yet |
| OpenAI | `sk-` | |
| xAI | `xai-` | |
| Google Gemini | `AIza` | checked with unit tests only, no live test yet |
| Cloudflare Workers AI | — | its own button, *Connect Cloudflare Workers AI* |

With several keys you switch in a dropdown; each provider remembers its model. NVIDIA no longer accepts a new key (one already stored keeps working).

**Free tiers have limits.** When you reach one, the chat says *"The provider's limit is reached"*. With *Account → Switch at the limit*, Orynex then goes on with your next provider instead of stopping. Every switch is announced, because the provider that takes over sees the conversation.

## Local: a model on your PC

Then no conversation leaves your computer.

1. Install [Ollama](https://ollama.com/download) (free).
2. In Orynex: *Account → AI: cloud or local → Local*.
3. Pick a model. Orynex shows what your PC can manage: *Minimum* from 4 GB of graphics memory, *Recommended* from 12 GB, *Advanced* from 32 GB. One click downloads it.

Local models are slower and less accurate than large cloud models and load the graphics card, processor and memory while they compute. llama.cpp and LM Studio work too but are experimental; the measured way is Ollama.

## Full Privacy

*Account → Full Privacy.* With it on, Orynex sends nothing to outside services: no cloud AI, no web search, weather, news, mail, calendar or GitHub, no voice input (it runs through a cloud service). It needs a local model. Under *Settings → Privacy*, Orynex counts every connection since it started; with Full Privacy it says *"No connection left your home network."*

## What else you can connect

All under *Account* or on its own page, all optional:

| | for | what you need |
| --- | --- | --- |
| **Web search** | looking up what changes | a Tavily key (free tier) |
| **Mail** | reading your inbox, sending if you allow it | an IMAP account with an app password, e.g. Gmail; Outlook.com/Hotmail do not work (Microsoft switched off password sign-in) |
| **Calendar** | reading appointments (easy) or adding them too | a secret iCal link, or your own Google project |
| **Telegram** | Orynex from your phone | your own bot from @BotFather |
| **Calls** | Orynex calls you, you call Orynex | the Linphone app and two free accounts |
| **GitHub** | reading issues, pull requests, CI | a token with read rights |

What to do with all this day to day is on the *Help* page in the app, each feature in a sentence or two.
