# CLAUDE.md

Hinweise für Claude Code in diesem Repository.

## Projekt

- Repository: [555wolfman/Claude](https://github.com/555wolfman/Claude), Standard-Branch `main`
- Lokaler Checkout: `/home/olaf_claude/claude`
- Zweck: Arbeitsbereich für Claude Code auf dem Server `nc3`. Bisher noch kein Anwendungscode.

## Kommunikation

- Antworte auf Deutsch, außer der Benutzer schreibt auf Englisch.
- Passwörter, Tokens und andere Zugangsdaten gehören nie in Dateien, Commits oder Memory.

## Server-Umgebung (`nc3`)

- OS: Debian 13 (trixie), x86_64
- Benutzer für Claude: `olaf_claude` (sudo nur mit Passwort)
- Weitere Benutzer: `olaf`, `simon`, `nico`, `navi`, `nextcloud`

### Installierte Werkzeuge

| Werkzeug | Ort | Aktualisieren |
|---|---|---|
| GitHub CLI `gh` | `/usr/bin/gh` (offizielles apt-Repo `cli.github.com`) | `sudo apt upgrade` |
| Claude Code `claude` | `/usr/local/bin/claude` (systemweit, für alle Benutzer) | `sudo update-claude` |
| Podman | systemweit | `sudo apt upgrade` |

- `/usr/local/sbin/update-claude` lädt die neueste Claude-Code-Version, prüft die SHA256-Prüfsumme gegen das Manifest und installiert sie.
- Der Auto-Updater pro Benutzer ist in `/etc/claude-code/managed-settings.json` abgeschaltet (`DISABLE_AUTOUPDATER=1`), weil normale Benutzer `/usr/local/bin` nicht beschreiben können.
- Podman: Aktuell gibt es keine Pods oder Container, weder rootless noch als root.

## Git & GitHub

- `gh` ist als `555wolfman` angemeldet (HTTPS). Git nutzt `gh auth git-credential` als Credential-Helper.
- Commit-Identität: `555wolfman <github.com@weichware.com>`
- Commits und Pushes nur, wenn der Benutzer es verlangt.
