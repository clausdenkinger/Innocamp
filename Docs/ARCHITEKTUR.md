# Softwarearchitektur

## Was „Softwarearchitektur“ hier bedeutet

Softwarearchitektur ist der Bauplan der Website: Welche Dateien haben welche Aufgabe, und wie gelangen Inhalt, Gestaltung und Verhalten gemeinsam in den Browser?

## Der heutige Aufbau

```text
Innocamp Vibecoding/
├── .github/workflows/pages.yml  Veröffentlichung über GitHub Pages
├── assets/
│   ├── favicon.svg              kleines Symbol im Browser-Tab
│   └── innovationcamp-hero.jpg  großes Bild im Kopfbereich
├── Docs/                        Arbeitsregeln für Menschen und Agenten
├── index.html                   Inhalt und Seitenstruktur
├── styles.css                   Farben, Schriften, Layout und Animationen
├── script.js                    Menü, Scroll-Effekt und Einblendungen
├── README.md                    kurze öffentliche Projektbeschreibung
├── robots.txt                   Hinweis für Suchmaschinen
└── .nojekyll                    verhindert eine zusätzliche Jekyll-Verarbeitung
```

Es handelt sich um eine **statische Website**. Das bedeutet: Der Browser lädt fertige Dateien; auf einem Server wird dabei kein Programmcode ausgeführt.

## So spielen die Dateien zusammen

1. Der Browser öffnet `index.html`.
2. `index.html` lädt `styles.css` für die sichtbare Gestaltung.
3. `index.html` lädt `script.js` mit `defer`. Dadurch wird das JavaScript erst ausgeführt, wenn die HTML-Struktur gelesen wurde.
4. CSS lädt zwei Google-Schriften und das große Bild aus `assets/`.
5. JavaScript ergänzt kleine Interaktionen, ist aber nicht für die eigentlichen Inhalte zuständig.

## Zuständigkeiten

### `index.html`: Inhalt und Bedeutung

Hier stehen Überschriften, Abschnitte, Links, Navigation und zugängliche Beschriftungen. Neue Inhaltsbereiche gehören als semantische HTML-Elemente hierher, zum Beispiel `section`, `article` oder `nav`.

### `styles.css`: Aussehen und Anpassung an Geräte

Hier liegen zentrale Designwerte als CSS-Variablen, das Desktop-Layout, zwei responsive Stufen bei 900 und 640 Pixeln sowie Regeln für reduzierte Bewegung. Wiederkehrende Werte sollen über die Variablen in `:root` gesteuert werden.

### `script.js`: Verhalten

Das JavaScript übernimmt derzeit vier begrenzte Aufgaben:

- mobiles Menü öffnen und schließen,
- Menü mit der Escape-Taste schließen,
- Kopfzeile nach dem Scrollen verändern,
- Elemente beim Sichtbarwerden einblenden und das Footer-Jahr aktualisieren.

Neue Logik soll nur hier landen, wenn HTML und CSS allein nicht ausreichen.

### `.github/workflows/pages.yml`: Veröffentlichung

GitHub startet diesen Ablauf bei einem Push auf `main` oder manuell. Der gesamte Projektordner wird als GitHub-Pages-Artefakt veröffentlicht. Es gibt keinen Build-Schritt.

## Leitplanken für Weiterentwicklungen

- Die einfache Struktur bleibt erhalten, solange sie den Bedarf erfüllt.
- Kein Framework, Paketmanager oder Build-System ohne ausdrückliche Entscheidung des Nutzers einführen.
- Inhalte, Gestaltung und Verhalten in den jeweils zuständigen Dateien halten.
- Für neue Bilder den Ordner `assets/` verwenden und verständliche Dateinamen wählen.
- Externe Abhängigkeiten sparsam einsetzen. Aktuell werden nur Google Fonts extern geladen.
- Änderungen müssen auf großen und kleinen Bildschirmen sowie per Tastatur nutzbar bleiben.
- Wichtige Inhalte dürfen nicht ausschließlich durch JavaScript verfügbar sein.
- Termine, Zielgruppe und Programminhalte müssen mit den offiziellen Programmseiten abgeglichen werden, die im Haupt-`README.md` verlinkt sind.

## Qualität prüfen

Da keine automatisierten Tests vorhanden sind, ist derzeit eine Prüfung im Browser nötig:

1. Seite ohne sichtbare Fehler öffnen.
2. Alle Navigations- und externen Links ausprobieren.
3. Desktop- und Mobilbreite prüfen, besonders unter 900 und 640 Pixeln.
4. Mobiles Menü mit Maus, Tastatur und Escape-Taste testen.
5. Fokusmarkierungen, Sprunglink und reduzierte Bewegung nicht beschädigen.
6. Browser-Konsole auf JavaScript-Fehler prüfen.

## Mögliche spätere Entscheidungen

- Soll die Website dauerhaft ohne Build-System bleiben, auch wenn sie wächst?
- Soll später eine automatische Prüfung für HTML, CSS, Links oder Barrierefreiheit ergänzt werden?

Diese Punkte sind keine Freigabe, die Architektur eigenständig zu verändern. Eine solche Änderung benötigt eine ausdrückliche Entscheidung des Nutzers.
