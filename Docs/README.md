# Projektdokumentation

Diese Dokumentation ist die gemeinsame Arbeitsgrundlage für Menschen und Codex-Agenten. Sie beschreibt, **wie das Projekt heute aufgebaut ist**, **wie Änderungen aussehen sollen** und **wie sie sicher mit Git gespeichert werden**.

> Wichtig: Die Dokumentation beschreibt den vorgefundenen Stand vom 18. November 2026. Die vier grundlegenden Arbeitsregeln wurden anschließend vom Nutzer ausdrücklich bestätigt.

## Die drei Dokumente

1. [Softwarearchitektur](ARCHITEKTUR.md) – Welche Dateien es gibt, wie sie zusammenspielen und wo neue Funktionen hingehören.
2. [Styleguide](STYLEGUIDE.md) – Wie HTML, CSS, JavaScript, Texte und die sichtbare Gestaltung einheitlich bleiben.
3. [Git-Workflow](GIT-WORKFLOW.md) – Wie Änderungen lokal gespeichert, geprüft und sicher zu GitHub übertragen werden.

## Projekt in einem Satz

Das Projekt ist eine kleine, responsive deutschsprachige Informationsseite zum **InnoCamp BW 2026**. Sie läuft direkt im Browser und benötigt aktuell weder ein Framework noch einen Build-Schritt.

## Was bereits sicher feststeht

- Die Anwendung besteht aus `index.html`, `styles.css` und `script.js`.
- Bilder und das Favicon liegen im Ordner `assets/`.
- Die Veröffentlichung erfolgt per GitHub Actions und GitHub Pages.
- Ein Push auf den Branch `main` startet die Veröffentlichung.
- Die Seite berücksichtigt verschiedene Bildschirmgrößen sowie Tastaturbedienung und reduzierte Bewegung.
- Es gibt aktuell keine automatisierten Tests, keinen Paketmanager und keine Build-Konfiguration.

## Verbindliche Grundentscheidungen

1. **Eigener Branch pro Aufgabe:** Jede Änderung wird in einem getrennten Arbeitszweig vorbereitet und geprüft.
2. **Commit und Push nur nach ausdrücklicher Freigabe:** Agenten dürfen beides nicht selbstständig ausführen. Für einen Push gilt zusätzlich die Schutzkette im [Git-Workflow](GIT-WORKFLOW.md#verbindliche-schutzkette-vor-jedem-push).
3. **Bestehendes Design bewahren:** Farben, Schriften, Abstände, Formensprache und Verhalten bilden den verbindlichen Ausgangspunkt.
4. **Offizielle Programmseiten sind maßgeblich:** Termine, Zielgruppe und Programminhalte werden mit den im Haupt-README genannten offiziellen Quellen abgeglichen.

## Pflege dieser Dokumentation

Wenn sich Technik, Dateistruktur, Gestaltung oder Git-Ablauf ändern, muss derselbe Auftrag auch die passende Datei in `Docs/` aktualisieren. Ein Agent darf diese Grundentscheidungen nicht stillschweigend aufweichen oder umgehen.
