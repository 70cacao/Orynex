# Bekannte Grenzen

[English](../en/limits.md) · [Übersicht](../README.md)

Was Orynex in Version 1.0 bewusst noch nicht kann oder wo es ein Risiko gibt, das wir kennen und in Kauf nehmen. Lieber hier als überrascht.

| Grenze | Warum |
| --- | --- |
| Der Installer ist nicht signiert; Windows SmartScreen warnt beim ersten Start ([was tun](installieren.md#2--die-warnung-von-windows-der-computer-wurde-durch-windows-geschützt)). Die Prüfsummen stehen in den Release-Notizen, die Updates selbst sind signiert. | ein Zertifikat kostet jedes Jahr; Orynex ist ein Privatprojekt |
| Installation und jedes Update brauchen ein Admin-Passwort. | Orynex liegt in `Program Files`, damit kein Programm es verändern kann; darauf stützt sich der Hilfsdienst für Admin-Aktionen |
| Anthropic und Google Gemini sind nur mit automatischen Tests geprüft, nicht mit einem echten Key. OpenAI und xAI laufen über denselben Weg wie Groq. | kein Key zum Testen |
| NVIDIA nimmt keinen neuen Key mehr an. | NVIDIAs Bedingungen erlauben den kostenlosen Zugang nur zum Entwickeln |
| Von unterwegs (Telegram, Anruf) geht es nur, solange dein PC an ist und Orynex läuft. | Orynex hat keinen Server; alles läuft auf deinem PC |
| Anrufe laufen über die Linphone-App und zwei Gratis-Konten, nicht über eine eigene Handy-App oder eine Telefonnummer. | keine Kosten, kein Server |
| Rückgängig gilt für das, was Orynex in seinen eigenen Daten anlegt (Regel, Mail-Liste, Tracker-Eintrag, Timer, Notiz), sieben Tage lang, einmal — nicht für Änderungen am System (ein beendetes Programm, die Lautstärke). | ein Rückweg, der nicht sicher hält, wäre ein falsches Versprechen |
| *Stopp* hält das Warten auf die KI sofort an; ein Werkzeug, das schon läuft, läuft zu Ende. | ein halb ausgeführtes Werkzeug wäre schlimmer |
| Aufgaben laufen nur, solange Orynex läuft. Nach einem Neustart steht eine laufende Aufgabe als *unterbrochen* da und wird nicht fortgesetzt; ein Schritt, der etwas geändert hat und dessen Ende fehlt, heißt *unklar* und wird nie von selbst wiederholt. | Fortsetzen kommt später |
| llama.cpp und LM Studio sind experimentell; Ollama ist der gemessene lokale Weg. Lokale Modelle sind langsamer und ungenauer als große Cloud-Modelle. | nicht gemessen |
| Eigene Verbindungen (MCP, OpenAPI) sind experimentell. | die Rechte sind geprüft (keine Verbindung erweitert still, was Orynex darf), aber kaum mit echten Servern benutzt |
| Der Handy-Browser (Orynex im Heimnetz) ist in 1.0 ausgeblendet. | nur halb gebaut |
| Einen Knopf, der alles samt Keys löscht, gibt es noch nicht; die Deinstallation lässt Daten und Keys absichtlich liegen ([so geht es von Hand](rechte-und-daten.md#daten-sichern-und-löschen)). | in Arbeit |
| In 0.14 sind noch einzelne Zeilen auf Deutsch, auch wenn die App auf Englisch steht: die Einträge auf der Seite *Log* und die Meldung bei einem ausgeschalteten Add-on. Die Fehlermeldungen selbst sind seit 0.14 übersetzt. | ist übersetzt und kommt mit der nächsten Version |
| Mail: Outlook.com- und Hotmail-Konten gehen nicht; Anhänge kann Orynex nicht senden. | Microsoft hat die Anmeldung per Passwort abgeschaltet |
| Was eine Cloud-KI mit deinen Nachrichten tut, regeln die Bedingungen deines Anbieters. Mit lokaler KI und Full Privacy geht nichts raus. | Orynex hat keinen eigenen Server und sieht nichts davon |
| Wie viel Arbeitsspeicher und Prozessor Orynex über Stunden braucht, ist noch nicht gemessen. | steht im Plan vor 1.0 |
