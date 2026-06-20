# Foliendesign – Style Guide

## Schriften

| Verwendung | Schriftart |
|---|---|
| **Text & Titel** | `'JetBrains Mono', 'Fira Code', monospace` |
| **Code** | `PT Mono` |

---

## Style Guide

### 1a. Überschrift – Technische Folien (SIMD, AVX, Speicher, etc.)

| Eigenschaft | Wert |
|---|---|
| Schrift | JetBrains Mono / Fira Code |
| Größe | `2.8rem` |
| Gewicht | `900` |
| Farbe | `#b1c7f3` |
| Ausrichtung | zentriert (Default durch `layout: center`) |

### 1b. Überschrift – Nicht-technische Folien (Personen, Kontakt, Quellen)

| Eigenschaft | Wert |
|---|---|
| Schrift | JetBrains Mono / Fira Code |
| Größe | `2.8rem` |
| Gewicht | `900` |
| Farbe | `#191c1e` |
| Ausrichtung | linksbündig (`text-align: left`) |
| Abstand nach unten | `1.2rem` |

Betroffene Folien: `jason.md`, `jvm.md`, `contact.md`, `sources.md`

### 2. Unterkapitelüberschrift (Sub-Title / Tagline)

| Eigenschaft | Wert |
|---|---|
| Schrift | JetBrains Mono / Fira Code |
| Größe | `0.85rem` |
| Gewicht | `700` |
| Farbe | `#fea619` (Akzent) oder `#778cb5` (dezent) |

### 3. Text (Fließtext / Labels / Werte)

| Eigenschaft | Wert |
|---|---|
| Schrift | JetBrains Mono / Fira Code |
| Größe | `0.65rem` |
| Gewicht | `700` |
| Farbe | `#ffffff` (auf dunklem Grund) |

### 4. Kommentar (Anmerkung / Hinweis / Quellenangabe)

| Eigenschaft | Wert |
|---|---|
| Schrift | JetBrains Mono / Fira Code |
| Größe | `0.8rem` |
| Gewicht | `400` |
| Farbe | `#999` |

### 5. Code-Blöcke

| Eigenschaft | Wert |
|---|---|
| Schrift | `PT Mono` |
| Größe | `1.5rem` |

---

## Abstände

### Vertikale Abstände (`gap`)

| Kontext | Wert |
|---|---|
| Großer Abstand (Sektionen) | `1.2rem` – `1.5rem` |
| Mittlerer Abstand (Gruppen) | `0.5rem` – `0.8rem` |
| Enger Abstand (Items) | `0.3rem` – `0.4rem` |
| Sehr eng (Zellen/Lanes) | `0.1rem` – `0.25rem` / `2px` – `3px` |

### Innenabstände (`padding`)

| Kontext | Wert |
|---|---|
| Box / Karte (groß) | `0.8rem 1.5rem` |
| Box / Karte (mittel) | `0.5rem 1rem` – `0.6rem 1.2rem` |
| Badge / Chip | `0.3rem 0.6rem` |
| Zelle (klein) | `0.3rem 0` – `0.4rem 0` |

### Außenabstände (`margin`)

| Kontext | Wert |
|---|---|
| Titel nach unten (technisch) | `0.4rem` – `0.5rem` |
| Titel nach unten (nicht-technisch) | `1.2rem` |
| Abstand vor Abschluss | `0.5rem` – `0.6rem` |
| Abstand vor Kommentar | `0.8rem` – `1rem` |

### Quellenreferenz (`.ref`)

| Eigenschaft | Wert |
|---|---|
| Position | `fixed` |
| Unten | `1rem` |
| Rechts | `1.5rem` |

---

## Allgemeine Regeln

### Zentrierung

Alle Folieninhalte werden primär **mittig** platziert (`layout: center` oder `align-items: center; justify-content: center`). Ausnahmen sind Folien mit besonderen Layout-Anforderungen (z. B. Quellenverzeichnis mit linksbündiger Tabelle) sowie nicht-technische Folien, deren Überschrift linksbündig (`text-align: left`) gesetzt wird.

### Farben

Nicht im Style Guide definierte Farben werden aus dem Farbsystem der `DESIGN.md` bezogen:

| DESIGN.md-Key | Hex | Verwendung |
|---|---|---|
| `primary` | `#000f27` | Dunkelster Hintergrund |
| `primary-container` | `#0b2447` | Karten-/Box-Hintergrund |
| `on-primary-container` | `#778cb5` | Dezente Texte, Labels |
| `inverse-primary` | `#b1c7f3` | Überschriften, helle Akzente |
| `secondary-container` | `#fea619` | Warme Akzente (Amber) |
| `tertiary-container` | `#009d8d` | Grüne Akzente (Teal) |
| `on-primary-fixed-variant` | `#32476c` | Rahmen, Borders |
| `outline` | `#74777f` | Kommentare, schwache Texte |
| `on-surface` | `#191c1e` | Dunkler Fließtext |
| `on-surface-variant` | `#44474e` | Sekundärtext |
