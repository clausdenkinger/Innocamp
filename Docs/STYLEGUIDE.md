# Styleguide

Dieser Styleguide hält vorhandene Muster fest. Er soll verhindern, dass die Website durch einzelne Änderungen technisch oder optisch uneinheitlich wird.

## Code-Stil

### Allgemein

- Dateien bleiben in UTF-8 gespeichert; sichtbare deutsche Umlaute dürfen direkt geschrieben werden.
- Einrückung: zwei Leerzeichen, keine Tabulatoren.
- Namen beschreiben ihren Zweck, zum Beispiel `menuToggle` oder `.hero-actions`.
- Kommentare nur ergänzen, wenn der Grund einer Lösung nicht aus dem Code erkennbar ist.
- Keine ungenutzten Dateien, Regeln oder Variablen zurücklassen.
- Eine Änderung soll klein und thematisch zusammenhängend bleiben.

### HTML

- Semantische Elemente wie `header`, `nav`, `main`, `section`, `article` und `footer` verwenden.
- Überschriften bilden eine verständliche Reihenfolge: einmal `h1`, danach logisch `h2` und `h3`.
- Interaktive Elemente müssen per Tastatur erreichbar und verständlich beschriftet sein.
- Bilder benötigen einen sinnvollen Alternativtext; rein dekorative Elemente werden für Hilfstechnologien verborgen.
- Externe Links in einem neuen Tab behalten `rel="noreferrer"`.
- JavaScript-Haken verwenden beschreibende `data-*`-Attribute. Klassen dienen vor allem der Gestaltung.

### CSS

- Vorhandene Klassen folgen überwiegend einer englischen, kleingeschriebenen Schreibweise mit Bindestrichen, zum Beispiel `.site-header`.
- Wiederverwendete Farben, Schriften, Breiten und Höhen gehören als Variable in `:root`.
- Zuerst gilt das große Layout; Anpassungen stehen in den vorhandenen Media Queries bei `900px` und `640px`.
- Animationen müssen die vorhandene Abfrage `prefers-reduced-motion` respektieren.
- Neue Fokuszustände müssen deutlich sichtbar bleiben.
- Stark gerundete „Pillen“-Elemente passen derzeit nicht zum fast eckigen System (`--radius: 2px`).

### JavaScript

- `const` verwenden, solange eine Variable nicht neu zugewiesen werden muss.
- Moderne Browser-APIs und optionale Verkettung (`?.`) passen zum vorhandenen Stil.
- DOM-Elemente einmal am Anfang ermitteln, statt dieselbe Suche häufig zu wiederholen.
- Ereignisbehandlung klein halten und Zustandsänderungen in klar benannten Funktionen bündeln.
- Semikolons und doppelte Anführungszeichen beibehalten.
- Die Seite soll bei fehlendem Element möglichst nicht komplett abbrechen.

## Visuelle Gestaltung

Die folgenden Regeln sind aus `styles.css` und der bestehenden Seite abgeleitet und wurden als verbindlicher Projektstil bestätigt. Sie ersetzen kein möglicherweise außerhalb dieses Repositorys bestehendes Markenhandbuch.

### Farben

| Rolle | Vorhandener Wert | Verwendung |
| --- | --- | --- |
| Dunkles Grün | `#0a2721` | große dunkle Flächen, Buttons, Navigation |
| Textgrün | `#10211d` | Fließtext und Linienbasis |
| Warmes Papier | `#f0eee7` | heller Seitenhintergrund |
| Helles Weiß | `#fafaf6` | Text auf dunklen Flächen |
| Limette | `#d8ff5f` | wichtigste Akzente und Handlungsaufforderungen |
| Koralle | `#ff795f` | kleine zusätzliche Akzente |
| Bernstein | `#ffb556` | ergänzender Akzent |

Neue Farben nur ergänzen, wenn die vorhandene Palette die Aufgabe nicht erfüllt. Ausreichender Farbkontrast bleibt wichtiger als reine Ästhetik.

### Schriften

- Überschriften: **Manrope**.
- Fließtext: **DM Sans**.
- Beide Schriften werden zurzeit von Google Fonts geladen; als Rückfall dient `sans-serif`.
- Große Überschriften sind eng gesetzt, relativ leicht und haben eine negative Laufweite.
- Kleine Kennzeichnungen sind häufig großgeschrieben und weit gesperrt.

### Formensprache und Layout

- Ruhige, großzügige Flächen mit klaren Gittern und feinen Linien.
- Fast eckige Elemente statt stark abgerundeter Karten.
- Dunkles Grün und Papierfarbe tragen die großen Flächen; Limette markiert zentrale Aktionen.
- Inhaltsbreite höchstens 1180 Pixel, seitlicher Abstand auf kleinen Geräten mindestens 16 Pixel.
- Bewegungen sind ruhig und funktional; sie dürfen Inhalte nicht blockieren.
- Bilder sollen mit dem dunkelgrünen Gesamtbild harmonieren und in passender Größe komprimiert sein.
- Agenten müssen dieses Erscheinungsbild bewahren. Grundlegende Abweichungen benötigen vor der Umsetzung eine ausdrückliche Freigabe des Nutzers.

## Sprache und Inhalte

- Seitensprache ist Deutsch; kurze englische Leitbegriffe wie „Explore“ sind Teil der heutigen Gestaltung.
- Direkte, aktive und verständliche Sätze verwenden.
- Nutzeransprache im sichtbaren Inhalt bleibt beim „du“.
- Fakten wie Datum, Zielgruppe oder Programm nicht erfinden. Maßgeblich sind die offiziellen Programmseiten, die im Haupt-`README.md` verlinkt sind. Widersprüche oder Unklarheiten werden dem Nutzer gemeldet.
- Linktexte beschreiben ihr Ziel; „hier klicken“ vermeiden.

## Prüfliste für Agenten

- Passt die Änderung zu den vorhandenen Farben, Schriften und eckigen Formen?
- Ist sie bei Desktop-, Tablet- und Mobilbreite verständlich?
- Funktioniert sie mit Tastatur und reduzierter Bewegung?
- Sind Texte und Links korrekt und nachvollziehbar belegt?
- Wurden nur Dateien geändert, die für den Auftrag nötig sind?

## Verbindlichkeit

Das bestehende Erscheinungsbild ist verbindlich. Kleine Ergänzungen müssen erkennbar zum vorhandenen System gehören; ein Redesign oder eine grundlegende Abweichung darf ein Agent nicht ohne ausdrückliche Freigabe beginnen.
