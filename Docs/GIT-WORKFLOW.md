# Git-Workflow

## Git in Alltagssprache

Git ist die lokale Versionsgeschichte des Projekts. Es kann nachvollziehbare Speicherpunkte anlegen und Änderungen vergleichen oder zurückholen.

- **Arbeitsordner:** Hier liegen die Dateien, die gerade bearbeitet werden. In dieser Sitzung ist das `D:\Projekte\Innocamp Vibecoding`. Git meldet denselben Arbeitsbestand über den aufgelösten Pfad `C:\LaufwerkD\Projekte\Innocamp Vibecoding`. Es soll keine zweite Kopie angelegt werden.
- **Repository:** Der Arbeitsordner zusammen mit der unsichtbaren Versionsgeschichte im Unterordner `.git`.
- **Commit:** Ein beschrifteter lokaler Speicherpunkt. Ein Commit ist zunächst nur auf diesem Computer vorhanden.
- **Branch:** Ein benannter Arbeitszweig. Damit kann eine Änderung getrennt von der veröffentlichten Hauptversion vorbereitet werden.
- **Remote:** Ein verbundenes Repository im Internet. Dieses Projekt verwendet `origin` mit der Adresse `https://github.com/clausdenkinger/Innocamp.git`.
- **Push:** Das Übertragen lokaler Commits zum Remote. Ein Push auf `main` löst hier automatisch die Veröffentlichung über GitHub Pages aus.

## Historische Momentaufnahme vor dem ersten Dokumentationscommit

Dieser Abschnitt hält den Arbeitsstand vor dem ersten Dokumentationscommit am 18. November 2026 fest. Er ist keine Aussage über den aktuellen oder späteren Repository-Zustand und muss vor jeder Git-Aktion mit aktuellen Git-Befehlen neu geprüft werden.

- Aktiver Arbeitsbranch: `codex/docs-grundlage`.
- Ausgangspunkt dieses Branches: Release-Tag `v1.0.1`, Commit `d93a5f220139990d4425f5aad668222d670ce85f`.
- Uncommittete Änderungen: `README.md` ist geändert und `Docs/*.md` sind neu.
- Für diese Dokumentationsaufgabe wurde noch kein Commit erstellt.
- Lokales `main` und `Banner` enthalten zusätzlich den Commit `9ad3d978a2d22dd8d870549920ed3b20aef82042` (`Add application banner`). Dieser Commit gehört nicht zur Dokumentationsaufgabe und darf nicht durch Merge, Rebase oder eine andere Übernahme in ihren Commit oder Push gelangen.
- Remote: `origin` auf GitHub; Veröffentlichungsbranch: `main`. Beim Remote-Abruf am 18. November 2026 zeigte `origin/main` auf Commit `d93a5f220139990d4425f5aad668222d670ce85f`. Diese Angabe ist nur eine Momentaufnahme; der tatsächliche Remote-Stand muss unmittelbar vor jeder Push-Bewertung erneut abgerufen werden.

## Sicherer Ablauf für eine Änderung

Die folgende Arbeitsweise ist verbindlich:

1. **Ausgangslage lesen:** `git status`, aktuelle Branches und Remote-Unterschiede prüfen.
2. **Sicheren Branch wählen:** Nicht direkt auf `main` arbeiten. Einen eigenen, passend benannten Branch wie `codex/docs-grundlage` verwenden.
3. **Nur die Aufgabe bearbeiten:** Vorhandene fremde Änderungen nicht löschen, formatieren oder in den eigenen Commit aufnehmen.
4. **Änderungen prüfen:** Website im Browser testen und `git diff` lesen.
5. **Gezielt vormerken:** Nur die tatsächlich beabsichtigten Dateien zum Commit auswählen.
6. **Commit freigeben lassen:** Erst nach ausdrücklicher Freigabe einen kleinen, verständlich beschrifteten Speicherpunkt anlegen.
7. **Passende Prüfstufe durchführen:** Für Routineänderungen gelten die Kurzchecks; für Releases und erhöhte Risiken gilt die vollständige Prüfung.
8. **Erst danach pushen:** Ohne erfolgreiche Schutzkette wird nichts zum Remote übertragen.

## Branch-Regeln

- `main` steht für den veröffentlichungsfähigen Stand.
- Jede neue Aufgabe erhält einen eigenen Branch. Direkte Entwicklungsarbeit auf `main` ist nicht erlaubt.
- Branch-Namen kurz und beschreibend halten, für Codex-Agenten mit Präfix `codex/`, zum Beispiel `codex/mobile-menu-fix`.
- Vor einem Branch-Wechsel immer `git status` prüfen.
- Kein erzwungener Push (`--force`) auf gemeinsam verwendete Branches.
- Branches, Tags oder Commits nicht löschen, solange der Nutzer dies nicht ausdrücklich verlangt.
- Vor einer Übertragung immer lokale und entfernte Historie aktuell vergleichen; nicht blind zusammenführen oder überschreiben.
- Commits aus anderen lokalen Branches dürfen nicht durch Merge, Rebase, Cherry-Pick oder einen falsch gewählten Push unbeabsichtigt in die Aufgabe gelangen.

## Commit-Regeln

- Ein Commit behandelt genau ein zusammenhängendes Thema.
- Nachricht in Befehlsform und verständlich schreiben, zum Beispiel `Document architecture and Git workflow`.
- Keine automatisch erzeugten Sammelmeldungen wie `changes` oder `update`.
- Vor dem Commit `git diff --cached` lesen.
- Keine Nutzeränderungen ungefragt in einen Agenten-Commit aufnehmen.
- Bestehende Commits nicht mit `--amend`, Rebase oder Reset verändern, außer der Nutzer hat genau das beauftragt.
- Ein Agent darf einen Commit erst nach einer ausdrücklichen, auf den konkreten Commit bezogenen Freigabe anlegen.

## Push- und Veröffentlichungsregeln

- Ein Push verändert den Zustand auf GitHub und ist deshalb keine rein lokale Sicherung.
- Ein Push auf `main` startet laut `.github/workflows/pages.yml` die GitHub-Pages-Veröffentlichung.
- Agenten dürfen nur nach ausdrücklicher Freigabe committen oder pushen.
- Eine allgemeine oder frühere Erlaubnis und auch eine Aussage wie „push das“ gelten **nicht** als letzte Ausführungsfreigabe für den Push.
- Vor jedem Push muss die passende Stufe des zweistufigen Prüfmodells durchgeführt werden.
- Der kurze, konkrete Bestätigungsdialog bleibt vor jedem Push verpflichtend.
- Zugangsdaten niemals in Befehle, Dateien, Commit-Nachrichten oder Chat-Ausgaben kopieren.

## Verbindliches zweistufiges Prüfmodell

Die Prüftiefe richtet sich nach Umfang und Risiko. Kein Test und kein Review kann absolute Sicherheit garantieren.

### Stufe 1: Zwingende Kurzchecks für Routine-Pushes

Diese Stufe gilt für kleine, überschaubare Routineänderungen. Ein separater Review-Agent und eine vollständige Testsuite sind hier nicht standardmäßig erforderlich. Unmittelbar vor dem Push müssen mindestens folgende Kurzchecks stattfinden:

- Ziel-Remote und Zielbranch frisch abrufen und die Fast-Forward-Fähigkeit ohne Force-Push prüfen,
- die exakt zu übertragenden Commits, den vollständigen Diff und die Dateiliste kontrollieren,
- auf offensichtliche Geheimnisse, Zugangsdaten und unmittelbar erkennbare kritische Risiken prüfen,
- nur direkt relevante, bereits vorhandene schnelle Syntax-, Test- oder Build-Checks ausführen,
- prüfen, ob der Zielbranch eine Veröffentlichung auslösen kann.

Bei unklarem Ziel, unerwarteten Dateien oder Commits, fehlender Fast-Forward-Fähigkeit oder einem erkennbaren kritischen Risiko wird nicht gepusht. Zeigen die Kurzchecks ein erhöhtes oder nicht zuverlässig einschätzbares Risiko, ist stattdessen Stufe 2 erforderlich.

### Stufe 2: Vollständige Prüfung für Releases und erhöhte Risiken

Diese Stufe ist verpflichtend für größere Releases oder neue Versionen wie `1.1` sowie immer dann, wenn Umfang, Inhalt oder Kurzchecks ein erhöhtes Risiko zeigen. Ein eigens dafür beauftragter Review-Agent prüft unabhängig mindestens:

- den vollständigen Git-Diff, die Dateiliste und relevante Workflows,
- versehentlich gespeicherte Geheimnisse und Zugangsdaten,
- neue oder geänderte Abhängigkeiten und bekannte Schwachstellen, soweit prüfbar,
- offensichtliche Sicherheitsprobleme im geänderten Code,
- die vollständigen vorhandenen Tests sowie Lint- und Build-Prüfungen,
- Ziel-Remote, Zielbranch, Commitfolge, Fast-Forward-Fähigkeit und mögliche Veröffentlichung.

Der Review-Agent berichtet, was geprüft wurde, welche Prüfungen technisch nicht möglich waren und welche Risiken verbleiben. Auch diese vollständige Prüfung reduziert Risiken, kann aber niemals absolute Sicherheit garantieren.

Findet der Review ein bekanntes kritisches oder hohes Sicherheitsproblem, darf der Push nicht stattfinden. Dasselbe gilt bei einer wesentlichen Unsicherheit, die eine zuverlässige Bewertung verhindert. Das Problem wird dem Nutzer in Alltagssprache erklärt und muss zuerst geklärt oder behoben werden.

### Bestätigungsdialog vor jedem Push

Nach bestandener Kurz- oder Vollprüfung erscheint unmittelbar vor jedem Push eine neue, konkrete Bestätigung. Sie muss mindestens enthalten:

- **Ziel-Remote:** Wohin übertragen wird, einschließlich der bekannten Repository-Adresse.
- **Ziel-Branch:** Welcher Branch auf GitHub geändert wird.
- **Commits:** Welche konkreten Commits übertragen werden, mit kurzer Kennung und verständlicher Beschreibung.
- **Veröffentlichung:** Ob der Push eine öffentliche Veröffentlichung auslösen kann.
- **Alltagserklärung:** „Ein Push überträgt lokale Commits in das entfernte GitHub-Repository. Bei diesem Projekt kann ein Push auf `main` die öffentliche Website veröffentlichen.“
- **Prüfergebnis:** Zusammenfassung der durchgeführten Kurz- oder Vollprüfung und ihrer Grenzen.

Der Dialog verlangt eine eindeutige Bestätigung für genau diesen beschriebenen Push. Schweigen, eine frühere Zustimmung oder die bloße Aussage „push das“ reichen nicht aus.

### Push ausführen oder abbrechen

Erst nach der ausdrücklichen Bestätigung darf der exakt beschriebene Push ausgeführt werden. Ändern sich danach Remote, Branch, Commits, Diff oder Veröffentlichungswirkung, verfällt die Bestätigung und die gesamte Schutzkette beginnt erneut.

Ohne Bestätigung, bei Abweichungen oder bei einer nicht bestandenen Prüfung wird nicht gepusht.

## Sensible Daten

Sensible Daten sind zum Beispiel Passwörter, API-Schlüssel, Zugangstoken, private Schlüssel und nicht öffentliche personenbezogene Daten.

- Solche Daten niemals in dieses Repository schreiben.
- Vor jedem Commit auf neue Konfigurations- oder Geheimnisdateien achten, etwa `.env`, Schlüsseldateien oder Zugangsdaten.
- Wenn versehentlich ein Geheimnis in Git gelangt ist: nicht nur die Datei löschen. Sofort stoppen, den Nutzer informieren und den betroffenen Schlüssel außerhalb von Git sperren oder ersetzen lassen.
- Keine Inhalte der `.git`-Historie oder lokaler Konfigurationsverzeichnisse veröffentlichen.

## Regeln speziell für Codex-Agenten

- Zu Beginn immer Repository-Anweisungen, `git status` und den aktuellen Branch lesen.
- Nur auftragsrelevante Dateien ändern und bestehende Nutzerarbeit bewahren.
- Keine destruktiven Befehle wie `git reset --hard` oder ungefragtes Verwerfen von Dateien.
- Kein automatischer Commit, Push, Merge, Rebase, Tag oder Release ohne entsprechenden Auftrag.
- Vor Routine-Pushes die zwingenden Kurzchecks durchführen; vor Releases und bei erhöhtem Risiko die vollständige Prüfung mit separatem Review-Agenten durchführen.
- Vor jedem Push unabhängig von der Prüfstufe den konkreten Bestätigungsdialog durchführen.
- Frühere oder pauschale Freigaben niemals als Ersatz für die letzte Push-Bestätigung behandeln.
- Keine Remote-Änderung nur deshalb vornehmen, weil lokal alles funktioniert.
- Ausgeführte Prüfungen und nicht geprüfte Punkte transparent berichten.
- Bei widersprüchlicher Historie, Konflikten oder unklarem Zielbranch stoppen und den Nutzer fragen.

## Verbindliche Entscheidung

Jede Aufgabe wird auf einem eigenen Branch bearbeitet. Commit und Push sind Agenten nur nach ausdrücklicher Freigabe erlaubt. Für jeden Push gelten das [zweistufige Prüfmodell](#verbindliches-zweistufiges-prüfmodell) und der verpflichtende Bestätigungsdialog.
