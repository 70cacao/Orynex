# Einrichten: womit Orynex denkt

[English](../en/setup.md) · [Übersicht](../README.md)

Orynex selbst ist kostenlos und hat keinen eigenen Server. Die Antworten schreibt ein Sprachmodell, und das kommt von dir: **entweder ein API-Key eines Anbieters (Cloud) oder ein Modell auf deinem PC (lokal).** Eingestellt wird beides unter *Konto*.

## Der schnellste Weg: ein kostenloser Key von Groq

1. Auf [console.groq.com](https://console.groq.com) anmelden und unter *API Keys* einen Key anlegen. Er beginnt mit `gsk_`.
2. In Orynex unter *Konto → KI-Anbieter (Cloud)* einfügen und **Verbinden** drücken.

Orynex erkennt den Anbieter am Key selbst und wählt das Modell. Der Key wird einmal beim Anbieter geprüft und liegt danach in der **Windows-Anmeldeinformationsverwaltung**, nie in einer Datei und nie im Protokoll. Orynex schickt ihn nur an diesen Anbieter.

**Was dabei rausgeht:** Mit einer Cloud-KI gehen deine Nachrichten, der Gesprächsverlauf und was Orynex an Kontext mitschickt an den Anbieter. Was der Anbieter damit tut, regeln seine Bedingungen, nicht Orynex.

## Andere Anbieter

| Anbieter | Key beginnt mit | Hinweis |
| --- | --- | --- |
| Groq | `gsk_` | kostenloser Tarif, damit wurde Orynex gebaut |
| OpenRouter | `sk-or-` | viele Modelle, auch kostenlose |
| Anthropic | `sk-ant-` | nur mit Unit-Tests geprüft, noch kein Live-Test |
| OpenAI | `sk-` | |
| xAI | `xai-` | |
| Google Gemini | `AIza` | nur mit Unit-Tests geprüft, noch kein Live-Test |
| Cloudflare Workers AI | — | eigener Knopf *Cloudflare Workers AI verbinden* |

Mit mehreren Keys schaltest du per Auswahlliste um; jeder Anbieter merkt sich sein Modell. NVIDIA nimmt keinen neuen Key mehr an (ein schon gespeicherter läuft weiter).

**Kostenlose Tarife haben Limits.** Erreichst du eins, steht im Chat *„Das Limit des Anbieters ist erreicht“*. Mit *Konto → Bei Limit wechseln* macht Orynex dann mit deinem nächsten Anbieter weiter, statt abzubrechen. Jeder Wechsel wird angesagt, denn der Anbieter, der übernimmt, sieht das Gespräch.

## Lokal: ein Modell auf deinem PC

Dann verlässt kein Gespräch deinen Rechner.

1. [Ollama](https://ollama.com/download) installieren (kostenlos).
2. In Orynex *Konto → KI: Cloud oder Lokal → Lokal*.
3. Ein Modell wählen. Orynex zeigt, was dein PC schafft: *Minimum* ab 4 GB Grafikspeicher, *Empfohlen* ab 12 GB, *Fortgeschritten* ab 32 GB. Ein Klick lädt es herunter.

Lokale Modelle sind langsamer und ungenauer als große Cloud-Modelle und belasten Grafikkarte, Prozessor und Arbeitsspeicher, solange sie rechnen. llama.cpp und LM Studio gehen auch, sind aber experimentell; gemessen ist der Weg über Ollama.

## Full Privacy

*Konto → Full Privacy.* Ist der Schalter an, schickt Orynex nichts an externe Dienste: keine Cloud-KI, keine Websuche, kein Wetter, keine News, keine Mail, kein Kalender, kein GitHub, keine Spracheingabe (die läuft über einen Cloud-Dienst). Dafür braucht es ein lokales Modell. Unter *Einstellungen → Privatsphäre* zählt Orynex jede Verbindung seit dem Start; mit Full Privacy steht dort *„Keine Verbindung hat dein Heimnetz verlassen.“*

## Was man sonst noch verbinden kann

Alles unter *Konto* oder auf der eigenen Seite, alles freiwillig:

| | wofür | was du brauchst |
| --- | --- | --- |
| **Websuche** | Nachschlagen, was sich ändert | einen Tavily-Key (kostenloser Tarif) |
| **Mail** | Postfach lesen, auf Wunsch senden | ein IMAP-Konto mit App-Passwort, z. B. Gmail; Outlook.com/Hotmail gehen nicht (Microsoft hat die Anmeldung per Passwort abgeschaltet) |
| **Kalender** | Termine lesen (einfach) oder auch eintragen | einen geheimen iCal-Link, oder ein eigenes Google-Projekt |
| **Telegram** | Orynex vom Handy aus | einen eigenen Bot von @BotFather |
| **Anruf** | Orynex ruft dich an, du rufst Orynex an | die Linphone-App und zwei Gratis-Konten |
| **GitHub** | Issues, Pull Requests, CI lesen | ein Token mit Leserechten |

Was man im Alltag damit tut, erklärt die Seite *Hilfe* in der App, jede Funktion in ein, zwei Sätzen.
