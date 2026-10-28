# Security

[Deutsch unten](#deutsch)

## Reporting a vulnerability

Please **do not** open a public issue for a security problem. Use GitHub's private report instead: on this repository, **Security → Report a vulnerability**. Only the maintainer sees it.

Helpful to include: the Orynex version (*Account → Updates*), what you did, what happened, and what you expected. If it involves a file or a message that triggers it, describe it rather than attaching anything that contains your own data, keys or passwords.

You get an answer within a week. A confirmed problem is fixed in the next release, and the release notes say what was fixed once an update is out.

## Supported versions

Only the newest release gets fixes. Orynex updates itself with one click (*Account → Updates*), and every update is checked against the signing key built into the app before it installs.

## What counts

Anything that lets someone else — a web page, a mail, a document, a connected service, another program on the PC — make Orynex do something you did not approve, read something it should not, or get at your keys. In particular:

- a way past a confirmation card, the kill switch, Full Privacy, or an automation's ring;
- a key, password or token appearing in a file, the log or an error report;
- text from outside (a mail, a page, the screen) getting Orynex to act without asking;
- the privilege broker running something for a caller other than Orynex.

What Orynex already does about these is described in [Permissions and data](docs/en/permissions-and-data.md).

---

## Deutsch

### Eine Sicherheitslücke melden

Bitte **kein** öffentliches Issue. Stattdessen GitHubs private Meldung: in diesem Repository **Security → Report a vulnerability**. Nur der Entwickler sieht sie.

Hilfreich: die Orynex-Version (*Konto → Updates*), was du getan hast, was passiert ist und was du erwartet hättest. Löst eine Datei oder Nachricht das Problem aus, beschreib sie lieber, als etwas mit deinen eigenen Daten, Keys oder Passwörtern anzuhängen.

Du bekommst innerhalb einer Woche eine Antwort. Ein bestätigtes Problem wird im nächsten Release behoben, und die Release-Notizen sagen, was behoben wurde, sobald das Update draußen ist.

### Welche Versionen

Nur die neueste Version bekommt Korrekturen. Orynex aktualisiert sich mit einem Klick (*Konto → Updates*), und jedes Update wird vor der Installation gegen den Signatur-Schlüssel in der App geprüft.

### Was zählt

Alles, womit jemand anderes — eine Webseite, eine Mail, ein Dokument, ein verbundener Dienst, ein anderes Programm auf dem PC — Orynex dazu bringt, etwas zu tun, dem du nicht zugestimmt hast, etwas zu lesen, das es nicht soll, oder an deine Keys zu kommen. Was Orynex dagegen schon tut, steht unter [Rechte und Daten](docs/de/rechte-und-daten.md).
