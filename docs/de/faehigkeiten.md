# Was Orynex kann, und was geplant ist

[English](../en/capabilities.md) · [Übersicht](../README.md) · [Rohtext für andere KIs](https://raw.githubusercontent.com/70cacao/Orynex/main/docs/de/faehigkeiten.md)

*Stand: Orynex 1.0.0, 3. November 2026. Ein Desktop-Assistent für Windows 11, nativ (Rust, Tauri v2, React), kostenlos nutzbar, ohne Konto und ohne einen Server von uns dazwischen.*

**So liest du den Stand:**

| Zeichen | Heißt |
|---|---|
| **In 1.0** | Veröffentlicht und getestet; das meiste beim Entwickler täglich im Einsatz |
| **In 1.0, nur Tests** | Veröffentlicht und getestet, an echten Diensten noch nicht gesehen |
| **Experimentell** | Veröffentlicht, wenig echt benutzt, kann sich ändern |
| **Kommt als Nächstes** | Im Bau oder als Nächstes dran, nicht veröffentlicht |
| **Idee** | Irgendwann gewollt, nichts angefangen, kein Versprechen |

## Womit es denkt

| | Stand |
|---|---|
| Dein eigener Key: Groq, xAI, OpenRouter | In 1.0 |
| OpenAI (dieselbe Anbindung wie Groq und xAI) | In 1.0 |
| Anthropic, Google Gemini (eigene Anbindungen) | In 1.0, nur Tests |
| Cloudflare Workers AI | In 1.0, nur Tests |
| Lokales Modell über Ollama: kein Key, nichts verlässt den PC | In 1.0 |
| llama.cpp, LM Studio | Experimentell |
| Wechsel zum nächsten Anbieter am Limit | In 1.0 |
| Full Privacy: gar keine Cloud | In 1.0 |

## Was es an deinem PC tut

Über sechzig Werkzeuge. Was etwas ändert, fragt vorher oder lässt sich zurücknehmen, und alles, was lief, steht in einer Liste.

| Bereich | Was | Stand |
|---|---|---|
| Programme | Starten, nach vorne holen, schließen, Ordner öffnen | In 1.0 |
| Dateien | Ordner und Textdateien lesen, mit Sperrliste für Geheimnisse | In 1.0 |
| Dateien schreiben | PDF, Word, PowerPoint, Markdown, Text, CSV, JSON, HTML. Überschreibt nie | In 1.0 (PowerPoint sieht schlicht aus) |
| Web | Suchen, Seite ohne Browser lesen, Seite öffnen, Nachrichten und RSS, Wetter | In 1.0 |
| Mail | Lesen, schreiben mit Karte vor jedem Senden (Outlook.com und Hotmail gehen nicht) | In 1.0 |
| Kalender | Lesen über einen Link, eintragen und ändern mit deinem Google-Projekt | In 1.0 |
| Bildschirm | Lesen, klicken und tippen, nur auf deine Bitte | In 1.0 |
| Musik und Ton | Spotify spielt, was du wolltest, Medientasten, Lautstärke | In 1.0 (ein Spotify-Update kann es brechen) |
| System | Zustand des PCs, Energieplan, Einstellungen, Zwischenablage, Checkup | In 1.0 |
| Windows-Benachrichtigungen | Lesen, im Messenger antworten | In 1.0 |
| GitHub | Issues, Pull Requests, CI, nur lesend | In 1.0 |
| Eigene Verbindungen | MCP und OpenAPI, jede Fähigkeit von dir freigegeben | Experimentell |
| Dienst neu starten, Prozess-Priorität setzen | Über einen kleinen Helfer mit Admin-Rechten, braucht eine Pro-Lizenz | In 1.0 |

## Größere Arbeit, ohne dich

| | Stand |
|---|---|
| **Aufgaben:** du gibst Ziel und Plan frei, Orynex arbeitet im Hintergrund, prüft das Ergebnis und gibt dir einen Bericht, mit Knöpfen für Kopieren, PDF und Schicken | In 1.0 |
| **Regeln:** nach Uhrzeit, beim Start eines Programms, bei neuer Mail und mehr, jede mit einer Grenze, wie weit sie allein gehen darf | In 1.0 |
| **Wächter:** Preise, Verfügbarkeit, Nachrichten | In 1.0, nur Tests |
| **Szenen:** den Desktop mit einem Satz einrichten | In 1.0 |
| **Abläufe:** mehrere Schritte auf einmal geplant, über Programme hinweg | Experimentell (das Modell wählt sie nicht immer) |
| Bietet wiederholte Gewohnheiten als Regel an, bereitet einen Morgenbericht vor | In 1.0 |

## Von unterwegs

| | Stand |
|---|---|
| Telegram: Text und Sprachnachrichten, Karten mit Ja und Nein, schickt dir Nachrichten und Dateien | In 1.0 (eine Datei per Mail ist noch nicht echt gelaufen) |
| Anruf: Orynex ruft dich an und du rufst Orynex an, über die Linphone-App und zwei Gratis-Konten, auch bei gesperrtem PC | In 1.0 |
| Meldet sich von selbst, wenn etwas wichtig ist, mit Ruhezeit und Tageslimit | In 1.0 |

Dein PC muss an und wach sein. Orynex hat keinen Server.

## Gedächtnis und du

| | Stand |
|---|---|
| Merkt sich, was du sagst und was es aus Mails lernt, zeigt alles, vergisst auf Wunsch | In 1.0 |
| Räumt Doppeltes auf, hält Adressen und Telefonnummern aus Mails aus deinen Anfragen heraus | In 1.0 |
| Persönlichkeit: Voreinstellungen, Regler oder eigene Worte | In 1.0 |
| Tracker: Essen, Wasser, Schlaf, Training, Gewohnheiten, alles auf dem PC | In 1.0 |
| Begleiter auf dem Desktop, mit Garderobe | In 1.0 |
| Deutsch und Englisch, Sprechtaste, Stimmen, die auf deinem PC laufen | In 1.0 |

## Sicherheit

| | Stand |
|---|---|
| Keys nur in der Windows-Anmeldeinformationsverwaltung | In 1.0 |
| Fünf Risiko-Ringe und Karten vor allem Ernsten | In 1.0 |
| Not-Aus per Tastenkürzel und mit `/stop` | In 1.0 |
| Aktivitäts-Seite mit Rückgängig für das, was Orynex angelegt hat | In 1.0 |
| Ein Dialog, der Orynex beendet, wenn das Fenster einfriert | In 1.0 |
| Alles löschen, samt Keys | In 1.0 (im Testprofil ausprobiert) |
| Lokales Protokoll und ein Fehlerbericht, den du selbst verschickst. Keine Telemetrie | In 1.0 |

## Bekannte Grenzen

Nicht signiert, Windows warnt deshalb beim ersten Start. Updates brauchen ein Admin-Passwort. Der Handy-Browser ist zurückgehalten. Mehr: [Grenzen](grenzen.md).

## Kommt als Nächstes

In dieser Reihenfolge. Nichts davon ist veröffentlicht, und die Reihenfolge kann sich ändern.

1. **Agenten.** Grundregeln für alle, und Agenten mit eigenen Vorgaben, an Ordner gebunden. Orynex wählt, wer arbeitet, auch über Telegram und am Telefon, und legt ab, was du schickst, im richtigen Ordner. *Im Bau.*
2. **Workbench.** Alle Arbeit reinwerfen, Orynex arbeitet sie ab.
3. **Eigene Workbenches.** Beliebige MCP-Server verbinden, eigene Bench bauen; Orynex sieht, was zusammenpasst, und schlägt vor, wie es damit arbeitet.
4. **Orynex lernt deine Welt kennen.** Es stellt ab und zu eine gute Frage, wählt den richtigen Moment, trennt Fakt von Vermutung. Du kannst alles einsehen, korrigieren und löschen.
5. **Orynex Anywhere.** Deine eigene Website, gehostet von deinem PC: eine vollständige, frei anpassbare Oberfläche für jedes Feature, auf jedem Gerät wie eine App, mit Konten und Rechten für andere Leute. Damit zusammen die Kamera im Anruf: *„was ist das?“*.
6. **Linux und Tails.** Die lokalen Funktionen unter Linux, und ein ganzer Assistent auf einem Tails-Stick, mit einem Befehl installiert.

## Ideen, kein Versprechen

Ein Begleiter, der auf das reagiert, was du tust, und auf Bitte handelt. Smart Home. Ein Auto, nur lesend. Eine Uhr.

*Was heute kostenlos ist, bleibt es. Ob später etwas kostet, ist offen.*
