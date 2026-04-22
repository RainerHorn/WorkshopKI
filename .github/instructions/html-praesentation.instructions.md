# Instructions: Scroll-freie HTML-Präsentation

Dieses Dokument beschreibt, wie Inhalte (z. B. aus einer README.md) als scroll-freie,
verlinkte HTML-Präsentation aufgebaut werden. Basis sind immer
`Templates/template.html` und `Templates/styles.css`.

---

## Grundprinzip

Jede Folie nimmt exakt den sichtbaren Viewport ein (`100vw × 100vh`).
Kein Scrollen — Navigation ausschließlich über Buttons oder Pfeiltasten.

---

## Dateistruktur

### Bevorzugt: Einzeldatei mit JavaScript-Steuerung

Eine HTML-Datei enthält alle Folien. JS zeigt jeweils genau eine Folie an.

```
index.html          ← alle Folien als .slide-Divs
Templates/
  template.html
  styles.css
```

### Alternativ: Mehrere verlinkte HTML-Dateien

Jede Folie ist eine eigene Datei; Navigation per `<a href="...">`.

```
slide-01-titel.html
slide-02-ueberblick.html
slide-03-aufgabe-a.html
...
Templates/
  template.html
  styles.css
```

---

## Foliengliederung aus dem README

Leite die Folien aus dem README ab — **eine Folie pro Abschnitt oder Aufgabe**:

| Folie | Inhalt aus README |
|-------|-------------------|
| 1 | Titel, Ziel, Zielgruppe |
| 2 | Lernziele |
| 3 | Voraussetzungen |
| 4 | Zeitplan / Ablaufübersicht |
| 5 | Block 1: Einstieg |
| 6 | Block 2: Präsentation – Inhaltsliste |
| 7 | Block 3: Live-Demo |
| 8 | Beispiel A: Textzusammenfassung |
| 9 | Beispiel B: Q&A auf eigene Inhalte |
| 10 | Beispiel C: Code-Unterstützung |
| 11 | Block 5: Review & Abschluss |
| 12 | Vorbereitung & Material |

Passe die Aufteilung an, wenn Inhalte nicht auf eine Folie passen.

---

## HTML-Grundstruktur (Einzeldatei)

Starte mit einer Kopie von `Templates/template.html`. Ersetze den Bereich
`.container` und das `.nav-menu` durch folgende Struktur:

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Workshop: Lokale LLMs</title>
    <link rel="stylesheet" href="Templates/styles.css">
    <style>
        /* Slide-Layout – ergänzt styles.css */
        html, body {
            height: 100%;
            overflow: hidden;
            margin: 0;
            padding: 0;
        }
        .slide-container {
            width: 100vw;
            height: 100vh;
            position: relative;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        .slide {
            position: absolute;
            inset: 0;
            display: none;
            flex-direction: column;
            padding: 2.5rem 3rem;
            box-sizing: border-box;
            overflow: hidden;
        }
        .slide.active {
            display: flex;
        }
        /* Folie als weißes Container-Panel */
        .slide-panel {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
            overflow: hidden;
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        .slide-panel .header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 1.2rem 2rem;
            flex-shrink: 0;
        }
        .slide-panel .header h1 {
            font-size: 1.8rem;
            margin: 0 0 0.2rem 0;
            font-weight: 700;
        }
        .slide-panel .header p {
            font-size: 1rem;
            opacity: 0.85;
            margin: 0;
        }
        .slide-panel .content {
            padding: 1.5rem 2rem;
            overflow: hidden;
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }
        /* Zweispaltiges Layout */
        .two-col {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
            flex: 1;
        }
        /* Navigation */
        .slide-nav {
            position: fixed;
            bottom: 1.2rem;
            right: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.6rem;
            z-index: 1000;
        }
        .slide-nav-btn {
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            border: none;
            border-radius: 50%;
            width: 48px;
            height: 48px;
            font-size: 1.3rem;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(30,60,114,0.5);
            transition: box-shadow 0.2s, transform 0.2s;
        }
        .slide-nav-btn:hover {
            box-shadow: 0 6px 20px rgba(30,60,114,0.7);
            transform: translateY(-2px);
        }
        .slide-nav-btn:disabled {
            opacity: 0.35;
            cursor: default;
            transform: none;
        }
        .slide-counter {
            position: fixed;
            bottom: 1.4rem;
            left: 50%;
            transform: translateX(-50%);
            color: rgba(255,255,255,0.85);
            font-size: 0.95rem;
            font-family: 'Segoe UI', sans-serif;
            letter-spacing: 0.05em;
        }
        /* Folientitel-Folie (ohne Panel, zentriert) */
        .slide-title {
            display: none;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
        }
        .slide-title.active {
            display: flex;
        }
        .slide-title h1 {
            font-size: clamp(2rem, 5vw, 3.5rem);
            margin-bottom: 1rem;
        }
        .slide-title p {
            font-size: clamp(1rem, 2.5vw, 1.5rem);
            opacity: 0.9;
        }
    </style>
</head>
<body>

<div class="slide-container">

    <!-- Folie 1: Titelfolie -->
    <div class="slide slide-title active" id="slide-1">
        <div>
            <h1>Workshop: Lokale LLMs in der Praxis</h1>
            <p>3–4 Stunden · Hands-on · Datenschutzkonform</p>
        </div>
    </div>

    <!-- Folie 2: Inhaltsfolie (Beispiel) -->
    <div class="slide" id="slide-2">
        <div class="slide-panel">
            <div class="header">
                <h1>Lernziele</h1>
                <p>Was du am Ende dieses Workshops kannst</p>
            </div>
            <div class="content">
                <!-- Inhalt mit styles.css-Klassen -->
                <div class="intro">
                    <p>Am Ende des Workshops kannst du...</p>
                </div>
                <ul>
                    <li>den Unterschied zwischen Cloud-LLMs und lokalen LLMs erklären</li>
                    <li>typische lokale LLM-Setups benennen</li>
                    <li>Prompts strukturiert formulieren</li>
                    <li>2–3 praktische Aufgaben mit einem lokalen Modell umsetzen</li>
                    <li>Chancen und Grenzen lokaler LLMs einschätzen</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- Weitere Folien hier einfügen ... -->

</div>

<!-- Navigation -->
<nav class="slide-nav">
    <button class="slide-nav-btn" id="btn-prev" title="Zurück" onclick="goTo(currentSlide - 1)">◀</button>
    <button class="slide-nav-btn" id="btn-next" title="Weiter" onclick="goTo(currentSlide + 1)">▶</button>
</nav>
<div class="slide-counter" id="slide-counter">1 / 1</div>

<script>
    let currentSlide = 0;
    const slides = document.querySelectorAll('.slide, .slide-title');

    function goTo(n) {
        slides[currentSlide].classList.remove('active');
        currentSlide = Math.max(0, Math.min(n, slides.length - 1));
        slides[currentSlide].classList.add('active');
        document.getElementById('slide-counter').textContent =
            `${currentSlide + 1} / ${slides.length}`;
        document.getElementById('btn-prev').disabled = (currentSlide === 0);
        document.getElementById('btn-next').disabled = (currentSlide === slides.length - 1);
    }

    document.addEventListener('keydown', e => {
        if (e.key === 'ArrowRight' || e.key === 'ArrowDown' || e.key === ' ') goTo(currentSlide + 1);
        if (e.key === 'ArrowLeft'  || e.key === 'ArrowUp')                     goTo(currentSlide - 1);
    });

    // Initialisierung
    goTo(0);
</script>

</body>
</html>
```

---

## CSS-Klassen aus `styles.css` für Folieninhalte

Nutze diese Klassen innerhalb von `.slide-panel .content`:

| Klasse | Zweck |
|--------|-------|
| `.intro` | Einführungstext / Kontextbox (grau-blau) |
| `.task` | Arbeitsauftrag (grün) |
| `.question` | Kontrollfragen (gelb) |
| `.tech-specs` | Technische Details (hellblau) |
| `.warning` | Wichtige Hinweise (rot) |
| `.praxis-box` | Praxistipps (grün) |
| `.comparison-table` | Vergleichstabellen |
| `.phases` + `.phase` | Kacheldarstellung von Phasen |
| `.accordion` | Aufklappbare Zusatzinformationen |

---

## Schriftgrößen (Präsentationsstandard)

Folien sind für die Projektion und Lesbarkeit aus größerer Entfernung ausgelegt.
**Grundregel: Fließtext mindestens 2 rem (≈ 32 pt).**

| Element | Mindestgröße |
|---------|-------------|
| Fließtext, Listeneinträge, Tabelleninhalt | **1.9–2.0 rem** |
| Kartentitel, Spaltenüberschriften (`h4`) | **2.0 rem** |
| Panel-Header (`h1`) | **1.8–2.2 rem** (bleibt wie im Template) |
| Hinweis-/Info-Boxen | **1.9 rem** |
| Emoji-Icons in Kacheln | **2.5–3.0 rem** |
| Progress-Legende | `clamp(0.65rem, 1.1vw, 0.8rem)` (bleibt klein) |

Wenn Inhalte bei dieser Größe nicht auf die Folie passen:
- Text kürzen (Sätze auf das Wesentliche reduzieren)
- Listeneinträge auf max. 4–5 reduzieren
- Tabellenspalten verschlanken oder Zeilen entfernen
- **Nie** die Schrift unter 1.8 rem verkleinern, um Platz zu sparen

---

## Inhaltsregeln für scroll-freie Folien

- **Ein Thema pro Folie** — bei zu viel Inhalt aufteilen
- Aufzählungen: **maximal 4–5 Punkte** pro Folie
- Tabellen: maximal **4 Zeilen** sichtbar
- Bei zwei Themenbereichen nebeneinander: `.two-col`-Layout nutzen
- **Kein `overflow: scroll`** auf `.slide` oder `.slide-panel .content` setzen
- **Keine Zeitangaben** auf Folien (keine Minutenangaben wie „15–20 min", keine Gesamtdauer)

---

## Dateilänge und Aufteilung

- **Maximale Länge einer HTML-Datei: ca. 500 Zeilen**
- Mehrere Folien pro Datei sind ausdrücklich erlaubt und bevorzugt
- Wenn eine Datei die Grenze überschreitet, Folgefolien in eine neue Datei auslagern
- Benennungsschema für aufgeteilte Dateien: `praesentation.html`, `praesentation-2.html`, `praesentation-3.html`
- Zwischen den Dateien mit dem „← Zurück / Weiter →"-Link am Ende jeder Datei verlinken
- Die JavaScript-Legende und `goTo()`-Logik in jeder Teildatei separat einbinden

---

## Verlinkter Mehrseiten-Ansatz

Wenn einzelne HTML-Dateien pro Folie gewünscht sind:

```html
<!-- Navigationsfooter in jeder Datei -->
<nav class="slide-nav">
    <a href="slide-01.html" class="slide-nav-btn">◀</a>
    <a href="slide-03.html" class="slide-nav-btn">▶</a>
</nav>
<div class="slide-counter">2 / 12</div>
```

Benennungsschema: `slide-NN-kurzname.html` (z. B. `slide-01-titel.html`)

---

## Anpassung des Templates

1. Kopiere `Templates/template.html` als Ausgangsbasis
2. Binde `Templates/styles.css` per `<link rel="stylesheet">` ein
3. Ersetze `.container` + `.nav-menu` durch `.slide-container` + `.slide-nav`
4. Das MMBBSBOT-Script beibehalten oder entfernen je nach Einsatzszenario
5. Inline-CSS aus dem Template-`<script>`-Block kann durch den `<link>`-Tag ersetzt werden, wenn nicht in Moodle eingebettet

---

## Progress-Legende

Auf jeder Folie soll eine fixierte Legende oben anzeigen, in welchem Abschnitt man sich befindet.

### CSS-Grundstruktur

```css
#legend {
    position: fixed;
    top: 0; left: 0; right: 0;
    height: 2.8rem;
    display: flex;
    align-items: stretch;
    z-index: 500;
    background: rgba(15, 30, 70, 0.55);
    backdrop-filter: blur(6px);
    border-bottom: 1px solid rgba(255,255,255,0.12);
}
.legend-section {
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.35rem;
    font-family: 'Segoe UI', sans-serif;
    font-size: clamp(0.65rem, 1.1vw, 0.8rem);
    color: rgba(255,255,255,0.45);
    cursor: pointer;
    border-right: 1px solid rgba(255,255,255,0.08);
    transition: background 0.2s, color 0.2s;
    position: relative;
}
.legend-section.active {
    background: rgba(255,255,255,0.15);
    color: white;
    font-weight: 600;
}
.legend-section.active::after {
    content: '';
    position: absolute;
    bottom: 0; height: 2px; width: 100%;
    background: linear-gradient(90deg, #667eea, #90caf9);
}
```

### HTML-Struktur

```html
<nav id="legend">
    <div class="legend-section active" data-section="0" onclick="goToSection(0)">
        <span class="legend-dot"></span> Einstieg
    </div>
    <div class="legend-section" data-section="1" onclick="goToSection(1)">
        <span class="legend-dot"></span> Grundlagen
    </div>
    <!-- weitere Abschnitte ... -->
</nav>
```

### JavaScript-Integration

```js
// Abschnittsgrenzen (0-basierte Folien-Indizes)
const sections = [
    { start: 0,  end: 1  },   // Einstieg
    { start: 2,  end: 4  },   // Grundlagen
    // ...
];
const legendItems = document.querySelectorAll('.legend-section');

function getSectionIndex(slideIdx) {
    for (let i = sections.length - 1; i >= 0; i--) {
        if (slideIdx >= sections[i].start) return i;
    }
    return 0;
}

function updateLegend(slideIdx) {
    const active = getSectionIndex(slideIdx);
    legendItems.forEach((el, i) => el.classList.toggle('active', i === active));
}

function goToSection(idx) { goTo(sections[idx].start); }
```

- `goTo()` muss am Ende `updateLegend(currentSlide)` aufrufen
- `.slide` und `.slide-title` brauchen `padding-top: 2.8rem` (Platz für die Legende)
- Klick auf einen Abschnitt springt direkt zur ersten Folie dieses Blocks

---

## Tastaturnavigation

| Taste | Aktion |
|-------|--------|
| `→` / `↓` / `Leertaste` | Nächste Folie |
| `←` / `↑` | Vorherige Folie |
