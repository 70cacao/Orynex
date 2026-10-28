# Wenn etwas nicht geht

[English](../en/troubleshooting.md) · [Übersicht](../README.md)

Zuerst lohnt ein Blick auf *Übersicht → Selbsttest*. Dort steht für KI, Speicher, Websuche, Not-Aus, Hilfsdienst und Sensoren, ob sie laufen. **Grau heißt „nicht eingerichtet“, nicht „kaputt“.**

## Orynex antwortet nicht

| Was du siehst | Was dahintersteckt | Was hilft |
| --- | --- | --- |
| *„Mir fehlt noch ein KI-Anbieter“* | kein Key und kein lokales Modell | [Einrichten](einrichten.md) |
| *„Das Limit des Anbieters ist erreicht“* | der kostenlose Tarif ist gerade aufgebraucht | kurz warten, oder unter *Konto* einen zweiten Anbieter eintragen und *Bei Limit wechseln* einschalten |
| *„Der Anbieter hat den API-Key abgelehnt“* | Key falsch, abgelaufen oder widerrufen | beim Anbieter einen neuen Key anlegen, unter *Konto* ersetzen |
| *„Die lokale KI antwortet nicht“* | Ollama läuft nicht | Ollama starten, dann *Konto → Neu suchen* |
| *„Antwort abgebrochen“* | die Verbindung zum Anbieter ist mitten im Text gerissen | noch einmal fragen; der Teil, der schon da war, bleibt stehen |
| *„Full Privacy ist an — Cloud-KI ist gesperrt“* | Full Privacy erlaubt nur lokale KI | lokales Modell wählen oder Full Privacy aus |

## Eine Funktion fehlt oder ist grau

- **Ihr Add-on ist aus.** Unter *Add-ons* einschalten. Was aus ist, läuft gar nicht und wird der KI nicht angeboten.
- **Sie braucht eine Einrichtung**, z. B. Mail, Kalender oder Websuche. Im Selbsttest und unter *Werkzeuge* steht „Einrichtung nötig“.
- **Full Privacy ist an.** Dann sind Websuche, Wetter, News, Mail, Kalender, GitHub und die Spracheingabe aus.

## Sprache und Mikrofon

- *„Spracheingabe ist aus“*: unter *Einstellungen → Privatsphäre* einschalten.
- *„Der Zugriff auf das Mikrofon wurde abgelehnt“*: Zwei Stellen fragen getrennt, der Schalter in Orynex und Windows selbst. Unter *Windows-Einstellungen → Datenschutz und Sicherheit → Mikrofon* den Zugriff für Desktop-Apps erlauben.
- Die Sprechtaste `Pause` fehlt auf vielen Laptops. Unter *Einstellungen → Verhalten → Sprechtaste* eine andere Taste eintragen.

## Tastenkürzel greifen nicht

Ist eine Kombination schon von einem anderen Programm belegt, bleibt die bisherige aktiv, und Orynex sagt es (beim Not-Aus mit einem Hinweis oben im Fenster). Unter *Einstellungen → Verhalten* eine andere wählen.

## Benachrichtigungen fehlen

Das Lesen muss unter *Einstellungen → Privatsphäre* eingeschaltet sein, und Windows fragt beim ersten Mal noch einmal selbst um Erlaubnis.

## Updates

| Meldung | heißt |
| --- | --- |
| *„GitHub hat gerade keine Update-Info geliefert“* | Problem auf GitHubs Seite; später noch einmal versuchen |
| *„GitHub ist gerade nicht erreichbar“* / *„Der Download brach ab“* | Internetverbindung prüfen, noch einmal versuchen |
| *„Das Update trägt keine gültige Signatur“* | Orynex installiert es absichtlich nicht; bitte melden ([Sicherheit](../../SECURITY.md)) |
| Windows fragt nach einem Admin-Passwort | normal: Orynex liegt in `Program Files` ([warum](installieren.md#3--der-installer)) |

## Anrufe kommen nicht an

Die Seite *Anruf* zeigt oben den Status. Steht dort *„nicht angemeldet seit …“*, hat Orynex die Verbindung zum Anruf-Server verloren (oft nach einem WLAN-Wechsel) und meldet sich von selbst neu an. Steht dort *„meldet sich an … stimmen Konto und Passwort?“* länger als eine halbe Minute, stimmt die Anmeldung nicht.

## Orynex reagiert gar nicht mehr

1. Rechtsklick auf das Orynex-Symbol im Infobereich der Taskleiste (oft versteckt unter `^`) → *Beenden* (bis 0.13: *Quit*). Ab 0.14 steht *Beenden* auch unten in der Seitenleiste.
2. Hilft das nicht: Task-Manager → *Orynex* → *Task beenden*.
3. Orynex neu starten.

## Fehler melden

Ab Version 0.14 erstellt *Protokoll → Fehlerbericht erstellen* eine Datei in deinem Download-Ordner: die Protokolle der letzten drei Tage (Keys und Geheimnisse geschwärzt), den Selbsttest und die Version, **ohne** Chats, Einstellungen oder Keys. Es wird nichts automatisch verschickt.

Fehler meldest du unter [Issues](https://github.com/70cacao/Orynex/issues). Sicherheitslücken bitte **nicht** öffentlich: siehe [SECURITY.md](../../SECURITY.md).
