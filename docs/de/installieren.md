# Orynex installieren

[English](../en/install.md) · [Übersicht](../README.md)

## Was du brauchst

| | |
| --- | --- |
| **Windows** | Windows 11, 64 Bit. Windows 10 ist nicht getestet. |
| **Platz** | rund 100 MB für Orynex selbst; ein lokales KI-Modell braucht zusätzlich 2–25 GB. |
| **Internet** | für eine Cloud-KI, die Websuche, Wetter, Mail und Kalender. Mit lokaler KI und *Full Privacy* geht Orynex ohne. |
| **Ein KI-Anbieter** | ein kostenloser API-Key reicht (z. B. von Groq), oder ein Modell auf deinem PC mit Ollama. Siehe [Einrichten](einrichten.md). |
| **Admin-Passwort** | einmal bei der Installation und bei jedem Update (Erklärung unten). |

Wie viel Arbeitsspeicher und Prozessor Orynex im Alltag braucht, ist noch nicht gemessen. Entwickelt und getestet wird auf einem Laptop mit 16 GB.

## 1 · Herunterladen

Den Installer gibt es auf der [Release-Seite](https://github.com/70cacao/Orynex/releases/latest): `Orynex_<Version>_x64-setup.exe`.

**Ob die Datei echt ist, kannst du prüfen.** In den Release-Notizen steht ihre SHA-256-Prüfsumme. In PowerShell:

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\Orynex_0.13.0_x64-setup.exe"
```

Stimmt die angezeigte Zahl mit der in den Release-Notizen überein, ist es genau die Datei, die veröffentlicht wurde.

## 2 · Die Warnung von Windows („Der Computer wurde durch Windows geschützt“)

Beim ersten Start zeigt Windows SmartScreen: *„Unbekannter Herausgeber“*.

**Warum:** Der Installer ist nicht mit einem gekauften Zertifikat signiert. Ein solches Zertifikat kostet jedes Jahr Geld; Orynex ist noch ein Privatprojekt. SmartScreen warnt bei jeder neuen, unsignierten Datei, auch wenn nichts an ihr falsch ist. Die Warnung sagt also: *„Windows kennt diese Datei noch nicht“*, nicht *„diese Datei ist gefährlich“*.

**Weiter:** auf **Weitere Informationen**, dann **Trotzdem ausführen**.

Wenn du dabei ein ungutes Gefühl hast, ist das vernünftig. Prüf vorher die Prüfsumme (oben) oder lad die Datei bei [VirusTotal](https://www.virustotal.com) hoch. Die Updates selbst sind signiert: Orynex installiert ein Update nur, wenn es mit dem Schlüssel unterschrieben ist, der in der App steckt.

## 3 · Der Installer

1. **Sprache wählen** (Deutsch oder Englisch). Orynex startet danach in dieser Sprache; umstellen kannst du jederzeit unter *Einstellungen → Darstellung*.
2. **Admin-Abfrage bestätigen.** Orynex wird nach `C:\Program Files\Orynex` installiert, für alle Konten auf dem PC. Das ist eine Sicherheitsentscheidung: Den Ordner kann ein normales Programm nicht verändern, und darauf verlässt sich der kleine Hilfsdienst unten.
3. **Zwei Vorgaben**, beide empfohlen:
   - **Privilege-Broker installieren** — ein kleiner Dienst für die wenigen Aktionen, die Administratorrechte brauchen. Orynex selbst läuft nie mit Admin-Rechten. Ohne den Broker geht alles andere ganz normal; solche Aktionen melden sich dann als „nicht verfügbar“.
   - **Beim Anmelden starten** — Orynex liegt dann als kleiner Kreis am Bildschirmrand, bis du ihn anfasst.

**Ohne Admin-Rechte** (z. B. ein Kinder- oder Firmenkonto): Jemand mit Admin-Passwort muss die Installation bestätigen, und das gilt auch für jedes Update.

## 4 · Der erste Start

Orynex erscheint als Kreis am Bildschirmrand, und die Ersteinrichtung öffnet sich. Jeder Schritt lässt sich überspringen und später wieder starten (*Hilfe → Einführung*). Der wichtigste Schritt ist der KI-Anbieter, ohne ihn antwortet Orynex nicht: [Einrichten](einrichten.md).

| Tastenkürzel | Was es tut | ändern unter |
| --- | --- | --- |
| `Strg + Umschalt + Leertaste` | Orynex öffnen | Einstellungen → Verhalten |
| `Strg + Alt + Umschalt + Esc` | **Not-Aus**: alles, was etwas verändert, hält sofort an | Einstellungen → Verhalten |
| `Pause` (halten) | Sprechtaste | Einstellungen → Verhalten |

## Updates

*Konto → Updates → Nach Updates suchen.* Orynex fragt GitHub nur, wenn du diesen Knopf drückst; einen automatischen Update-Check gibt es nicht. Ein gefundenes Update wird vor der Installation auf seine Signatur geprüft und braucht wie die Installation die Admin-Abfrage. Deine Chats, Einstellungen und Keys bleiben erhalten.

## Deinstallieren

*Windows-Einstellungen → Apps → Installierte Apps → Orynex → Deinstallieren.* Das entfernt das Programm, den Hilfsdienst und den Autostart.

**Absichtlich bleibt liegen**, damit eine Neuinstallation deinen Verlauf wiederfindet:

- deine Daten in `%APPDATA%\com.ceruleancircle.copilot` und `%LOCALAPPDATA%\com.ceruleancircle.copilot` (Chats, Gedächtnis, Einstellungen, Protokoll, Stimmen);
- deine Keys und Passwörter in der Windows-Anmeldeinformationsverwaltung.

Wie du beides ganz entfernst, steht unter [Daten sichern und löschen](rechte-und-daten.md#daten-sichern-und-löschen).
