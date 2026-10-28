# Was Orynex darf, und was mit deinen Daten passiert

[English](../en/permissions-and-data.md) · [Übersicht](../README.md)

## Was Orynex darf

Alle Freigaben stehen an einem Ort: *Rechte*. Eine **Stufe** stellt sie auf einmal, danach kannst du jeden Schalter einzeln ändern.

| Stufe | erlaubt |
| --- | --- |
| **Wenig** | Windows-Benachrichtigungen lesen |
| **Mittel** | dazu Spracheingabe, Arbeitskontext (welches Programm vorne ist, nie Fenstertitel) und Lernen aus Gewohnheiten |
| **Viel** | dazu Bildschirm steuern, Mails senden und Termine aus Mails |

**In jeder Stufe gleich:**

- **Was etwas verändert, fragt vorher per Karte** — eine Mail, ein Kalendereintrag, ein Programm beenden, ein Befehl. Die Karte zeigt genau, was passiert (bei einer Mail der ganze Text), und dein Ja gilt nur für genau das. Ohne Antwort heißt es Nein.
- **Hat Orynex vorher fremden Text gelesen** (eine Mail, eine Webseite, den Bildschirm), fragt es vor Klicks und Tippen in anderen Programmen immer. Fremder Text könnte der KI Anweisungen untergeschoben haben.
- **Der Not-Aus** (`Strg + Alt + Umschalt + Esc`, unterwegs `/stop` in Telegram) hält sofort alles an, was etwas verändert. Fragen beantworten geht weiter.
- **Orynex läuft nie mit Administratorrechten.** Die wenigen Aktionen, die welche brauchen, laufen über den kleinen Hilfsdienst aus der Installation und hören beim Not-Aus ebenfalls auf.
- **Kein stilles Mitschauen:** Der Bildschirm wird nur gelesen, wenn du darum bittest. Das Mikrofon ist nur offen, solange du die Sprechtaste hältst.

### Automationen und Aufgaben (wenn du nicht hinsiehst)

Jede Regel unter *Automationen* sagt, wie weit sie ohne dich gehen darf, in fünf Ringen:

| Ring | darf ohne dich |
| --- | --- |
| 0 · Lesen | Wetter, News, Websuche, Systemwerte |
| 1 · Privat lesen | dazu Mails, Kalender, Dateien, Benachrichtigungen |
| 2 · Lokal ändern | dazu Szenen ohne Beenden, Medien, Apps und Ordner öffnen |
| 3 · Raus oder beenden | dazu Mail an Adressen deiner Liste, Programme beenden |
| 4 · Unumkehrbar | Löschen, Bildschirm lesen oder steuern — **läuft nie ohne dich** |

Was über dem Ring der Regel liegt, wartet 30 Minuten auf dein Ja per Karte; danach gilt Nein. Eine *Aufgabe* (im Chat „Als Aufgabe“) zeigt vorher Plan und Grenzen und läuft erst nach deinem Ja.

### Von unterwegs (Telegram, Anruf)

Was von unterwegs kommt, läuft über eine **Ampel**: Lesen und Harmloses läuft wie am PC; was nach draußen geht oder etwas beendet, prüft eine zweite KI und fragt dich dann auf dem Handy; Bildschirm, Befehle und Unumkehrbares gehen nur am PC. Chats mit Telegram-Bots sind nicht Ende-zu-Ende-verschlüsselt.

### Rückgängig

Was Orynex in seinen eigenen Daten anlegt (eine Regel, eine Adresse auf der Mail-Liste, einen Tracker-Eintrag, einen Timer, eine Notiz), kannst du unter *Aktivität* sieben Tage lang zurücknehmen. Änderungen am System (ein beendetes Programm, die Lautstärke) lassen sich nicht zurückholen; deshalb fragen sie vorher.

## Was wohin geht

| Was | wohin |
| --- | --- |
| Deine Nachrichten, der Verlauf, der mitgeschickte Kontext | an deinen KI-Anbieter — bei lokaler KI nirgendwohin |
| Was Orynex aus Mails, Kalender, Bildschirm, Dateien liest | an deinen KI-Anbieter, wenn es für eine Antwort gebraucht wird |
| Spracheingabe (die Aufnahme) | an deinen KI-Anbieter zur Erkennung, nicht gespeichert |
| Vorgelesener Text | nirgendwohin (Windows-Stimme, Piper), oder an ElevenLabs, wenn du es wählst |
| Keys und Passwörter | in die Windows-Anmeldeinformationsverwaltung, sonst nirgendwohin |
| Chats, Gedächtnis, Tracker, Regeln | auf diesen PC, nirgendwohin sonst |

Orynex hat **keine Telemetrie** und keinen eigenen Server. Updates werden nur gesucht, wenn du den Knopf drückst. Welche Verbindungen seit dem Start nach draußen gingen, steht unter *Einstellungen → Privatsphäre*.

## Daten sichern und löschen

**Wo die Daten liegen:**

| Ordner | darin |
| --- | --- |
| `%APPDATA%\com.ceruleancircle.copilot` | `orynex.db` (Chats, Gedächtnis, Regeln, Tracker, Kontakte …), `prefs.json` (Einstellungen), auf Wunsch der Mitschnitt |
| `%LOCALAPPDATA%\com.ceruleancircle.copilot` | Protokolldateien, Stimmen, Anruf-Daten |
| Windows-Anmeldeinformationsverwaltung | API-Keys, App-Passwörter, Tokens (Einträge mit `com.ceruleancircle.copilot` oder `orynex-sip` im Namen) |

Der Name `com.ceruleancircle.copilot` ist ein technischer Rest aus der Zeit, bevor Orynex Orynex hieß; er bleibt, damit beim Update nichts verloren geht.

**Sichern:** Orynex beenden (Rechtsklick auf das Symbol im Infobereich der Taskleiste → *Beenden*), dann den Ordner `%APPDATA%\com.ceruleancircle.copilot` kopieren. Keys sichert das nicht mit; die trägst du nach einer Neuinstallation neu ein.

**Löschen in der App:**

- *Einstellungen → Daten:* Chatverlauf löschen, Gemerktes löschen, gelernte Gewohnheiten löschen, gemerkte Befehle löschen, Mitschnitt löschen.
- *Gedächtnis:* einzelne Einträge vergessen, oder *Alles vergessen*.
- *Konto:* jeden Key und jede Verbindung einzeln entfernen.

**Alles restlos entfernen** (einen Knopf dafür gibt es noch nicht):

1. Orynex deinstallieren (siehe [Installieren](installieren.md#deinstallieren)).
2. Die beiden Ordner oben löschen.
3. *Systemsteuerung → Anmeldeinformationsverwaltung → Windows-Anmeldeinformationen*: die Einträge mit `com.ceruleancircle.copilot` oder `orynex-sip` im Namen entfernen.
4. Bei Gmail das App-Passwort unter `myaccount.google.com/apppasswords` widerrufen; bei Google Kalender und Telegram den Zugang dort widerrufen bzw. den Bot löschen.
