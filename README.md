# Fibonacci-Spin-Generative-Art

A collection page for **Fibonacci's Spin** — two works rotating objects around a Fibonacci-set orbit. Built as a single-file HTML page, styled as a gallery-ready collection and licensing surface.

**Live:** `https://reyrove.github.io/Fibonacci-Spin-Generative-Art/`

---

## Overview

**Fibonacci's Spin** is a collection of two works, each rotating a set of objects around an orbit whose radii follow the Fibonacci sequence — 1, 1, 2, 3, 5, 8, 13, 21, 34. Every object has its own period, so the phase relationship between objects shifts continuously over time. The composition is never the same two frames in a row.

The two works differ only in their visual vocabulary:

- **Purple Golden Lines** — the orbit drawn with fine linear strokes in a deep purple.
- **Cyan Golden Ellipses** — the orbit drawn with flat oval forms in a luminous cyan.

Everything else — the sequence, the orbit, the phase, the tempo — is shared. Each work is an **edition of one**. The code is the edition; the animation is the work.

The page functions as a **collection and licensing surface** for fashion houses, textile studios, and surface designers. Both works can be licensed individually or as a pair, and the Fibonacci-orbit system can be commissioned as a new variation.

---

## Why This Is Not a Generative Series

The works in **Fibonacci's Spin** are different from the artist's other collections (Skyline Series, Portrait Series, Girih, Gothic Grid, Matrix Rain, Game of Seeds, and others). Those are **generative systems** — one seed produces infinitely many variations, and the page exists to browse, archive, and license them.

**Fibonacci's Spin** is different. Each work in the collection is a **single, fixed edition** — one specific arrangement, one specific motion, authored once and never re-seeded. The p5.js code ran once, the output was captured as a GIF, and that is the edition. Nothing is re-generated.

This changes the page in three ways:

1. **No archive.** There is nothing to archive when there is only one edition per work.
2. **No "New Seed" button.** Instead, the two works are presented side by side, each linking to its own dedicated page.
3. **No seed metadata.** The metadata describes the work's parameters — object count, palette, frame rate — not a seed.

The collection reads as an **edition page** rather than a generative catalogue.

---

## Features

### The Page

- **Hero diptych** — both works side by side in the cover, so the collection reads as a pair from the first screen
- **Two works grid** — each work shown with its own card, description, metadata, and a link to its dedicated page
- **Eight surface tiles** — each work presented across four aspect ratios (print, scarf, textile, wall)
- **Three process cards** — the shared logic behind both works: Fibonacci sequence, rotation and phase, fixed realisation
- **Collection-level commission** — licence both works together, commission a new spin, or build a private tool
- **Legal modal** — licensing, terms, and credits

### The Works

Both works are presented as **animated GIFs**, not live p5.js sketches.

- `images/purple-lines.gif` — Purple Golden Lines
- `images/cyan-ellipses.gif` — Cyan Golden Ellipses

The browser handles GIF playback natively. No JavaScript animation loop, no continuous canvas redraws. The page is very light.

### Surfaces

The eight surface tiles reuse the same two GIF files via CSS `background-image`:

- **Print (1:1)** — `background-size: contain`
- **Scarf (3:1)** — `background-size: 33.33% 100%` (three repeats horizontally)
- **Textile (4:3)** — `background-size: 50% 50%` (2×2 repeat)
- **Wall (2:3)** — `background-size: 100% 50%` (two repeats vertically)

Because the browser caches each GIF after the first load, the eight surface tiles reuse the same two files. Actual network transfer is ~2 MB, not ~16 MB.

### Interactions

- **← →** scroll the ribbon nav on mobile
- **Esc** closes the legal modal
- Hover states on nav links, work cards, and mockup images
- `prefers-reduced-motion` disables all transitions

---

## File Structure

```
Fibonacci-Spin-Generative-Art/
├── index.html                    # Single-file collection page
├── README.md
└── images/
    ├── fav.svg                   # Favicon
    ├── purple-lines.gif          # Work 01 — animated GIF
    ├── cyan-ellipses.gif         # Work 02 — animated GIF
    ├── tote.png                  # Mockup: tote bag
    ├── tee.png                   # Mockup: t-shirt
    └── cushion.png               # Mockup: cushion
```

No build step. No dependencies. No CDN except Google Fonts.

---

## Getting Started

1. Clone the repo:
   ```bash
   git clone https://github.com/reyrove/Fibonacci-Spin-Generative-Art.git
   cd Fibonacci-Spin-Generative-Art
   ```
2. Add the two GIFs to `images/` with the exact names above.
3. Add the three mockup PNGs (optional — they appear in the Commission section).
4. Open `index.html` in a browser.

That's it. The page loads both GIFs and presents the collection.

---

## The Two Works

### 01 / Purple Golden Lines

> In the graceful rotation of the Fibonacci sequence, where each number holds its place in the symphony of mathematics, there lies a sentimental journey woven with threads of nostalgia and wonder. Like the petals of a delicate flower unfolding under the soft light of dawn, the sequence blooms with hues of purple, casting a mesmerising spell that transcends time and space.

**Parameters:**
- Objects: lines
- Palette: purple golden
- Sequence: Fibonacci
- Edition: 1 of 1

**Repo:** `https://github.com/reyrove/Fibonacci-Spin-Purple-Golden-Lines`

### 02 / Cyan Golden Ellipses

> Fifty-five cerulean ellipses, drawn by the digital brushstrokes of p5.js, pirouette in a mesmerising dance across the canvas. Each frame, meticulously crafted at 31 frames per second, unveils a symphony of mathematics and aesthetics, choreographed by lines of code.

**Parameters:**
- Objects: 55 ellipses
- Palette: cyan golden
- Frame rate: 31 fps
- Edition: 1 of 1

**Repo:** `https://github.com/reyrove/Fibonacci-Spin-Cyan-Golden-Ellipses`

---

## How the Fibonacci Orbit Works

Although the works are fixed editions, the underlying system is generative in spirit. Here is the shared logic:

### The Sequence

The Fibonacci sequence — 1, 1, 2, 3, 5, 8, 13, 21, 34 — sets the orbit radii. Each object in the composition sits at one of the sequence numbers, so the work has eight distinct orbital shells. The result is a spatial structure that feels both regular and organic, because it is a structure the natural world uses too: sunflower spirals, pine cones, nautilus shells.

### The Phase

Every object rotates around the centre at its own period. The periods are set from the golden ratio (φ ≈ 1.618), so each object's period is a power of φ away from the next. Over time, the phase relationship between objects shifts continuously — the pattern passes through configurations that read as symmetry, opposition, and dispersal, all from the same simple rule.

### The Edition

Each work fixes one palette and one object type. **Purple Golden Lines** draws the orbit with fine linear strokes in a deep purple. **Cyan Golden Ellipses** draws it with flat oval forms in a luminous cyan. Nothing else differs. The edition is the code; the animation is the work.

---

## Customisation

### Change the filenames

The HTML expects:
- `images/purple-lines.gif`
- `images/cyan-ellipses.gif`

If your GIFs have different names, either rename the files or search-and-replace both strings in `index.html`. Each appears 12 times.

### Change the surface tiling

The eight surface tiles use inline `style` attributes for the tiling:

```html
<div class="surface-tile" style="aspect-ratio: 1; background-image: url('images/purple-lines.gif'); background-size: contain;"></div>
```

Adjust `aspect-ratio` and `background-size` to change how the GIF tiles within each surface. For example:

- **1:1 print** — `aspect-ratio: 1; background-size: contain`
- **3:1 scarf** — `aspect-ratio: 3 / 1; background-size: 33.33% 100%`
- **4:3 textile** — `aspect-ratio: 4 / 3; background-size: 50% 50%`
- **2:3 wall** — `aspect-ratio: 2 / 3; background-size: 100% 50%`

### Shrink the GIFs

If the page loads slowly, compress the GIFs. Tools to try:

- **gifski** (command line, high quality) — reduces frame count without visible loss
- **ezgif.com** (browser-based) — reduces palette, frame count, or dimensions
- **ffmpeg** — converts GIF → MP4 → back to GIF, often smaller

A 300 × 300 GIF with 20 frames typically runs under 500 KB and still looks good at the sizes shown on this page.

### Add a third work

The collection currently holds two works. To add a third:

1. Add the new GIF to `images/`.
2. Copy one of the `<article class="work-card">` blocks in the Works section and update the title, description, metadata, and GIF filename.
3. Add a corresponding surface block in the Surfaces section.
4. Update the collection statement to mention three works.

The layout handles any number of works — the grid expands gracefully.

### Update the collection statement

The statement currently says "a collection of two works." If you add or remove works, update this sentence in the statement section.

### Replace the mockup images

Swap the files in `images/` or update the `src` attributes in the Commission section:

```html
<img src="images/your-mockup.png" alt="..." loading="lazy" />
```

### Change the LinkedIn URL

The footer currently points to:
```
https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/
```

Double-check this matches your actual profile slug before publishing.

---

## Design System

| Token | Value | Use |
|-------|-------|-----|
| `--bg` | `#0a0a0a` | Page background |
| `--paper` | `#f4f1ea` | Light surface (Surfaces section) |
| `--gold` | `#b8935a` | Primary accent |
| `--gold-soft` | `#d4b483` | Italic emphasis |
| `--purple` | `#a78bd6` | Work 01 accent |
| `--cyan` | `#6fd6e8` | Work 02 accent |
| `--serif` | Cormorant Garamond | Headings, titles |
| `--mono` | DM Mono | Labels, metadata, UI |

Type scale, spacing, and section rhythm match the artist's other collections (Skyline, Portrait, Girih, Gothic Grid, Order to Chaos, Wallpaper Groups, Wandering Tiles, Food Grid, Framed Line, Deconstructed Stage, Layered Diagram, Japanese Patterns, Matrix Rain, Organic Shapes, Recursive Grid, Generative Lifeform, Game of Seeds). Responsive breakpoints at 900px, 720px, 560px, and 400px.

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Enter` / `Space` | Activate focused link or button |
| `Esc` | Close legal modal |

---

## Browser Support

Modern evergreen browsers with:

- Animated GIF support (universal)
- CSS custom properties (universal)
- `backdrop-filter` (Safari 9+, Chrome 76+, Firefox 103+)
- `aspect-ratio` CSS property (universal in modern browsers)

Fallback: the page works in any browser that can render an `<img>` tag with a GIF.

---

## Accessibility

- All images have descriptive `alt` text
- Legal modal traps focus, closes on `Esc` and overlay click
- `prefers-reduced-motion` disables all transitions
- All interactive elements have visible focus states (via browser default)
- Ribbon nav scrolls horizontally on mobile with a gradient mask

---

## Section Map

| Section | ID | Purpose |
|---------|-----|---------|
| Cover | — | Hero title + GIF diptych |
| Statement | `#statement` | Artist statement about the collection |
| Works | `#works` | Two work cards, each linking to its own page |
| Surfaces | `#surfaces` | Eight tiles — both works across four materials |
| Process | `#process` | Three process cards on the shared logic |
| Commission | `#commission` | Collection licensing + mockups + CTA |
| Colophon | — | Footer, links, legal |
| Legal modal | `#legalModal` | Licensing / Terms / Credits |

---

## Deployment (GitHub Pages)

1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, select `Deploy from a branch`.
4. Choose branch `main` and folder `/ (root)`.
5. Save — the site goes live at `https://reyrove.github.io/Fibonacci-Spin-Generative-Art/`.

---

## Notes on the Source

This page does not use p5.js. The two works were originally drawn as p5.js sketches; the animations were captured as GIFs and are presented here as images. The page is pure HTML and CSS.

**Why GIFs rather than live sketches:**

- The works are **fixed editions** — running them live would be redundant, since they always produce the same output.
- GIFs are lighter than continuous canvas redraws — the browser handles playback natively.
- The GIF files are cached after first load, so the 12 GIF instances on the page reuse just two files.
- The page has no external dependency beyond Google Fonts.

**One trade-off:** the GIF's frame rate is locked into the file. The p5.js sketches originally ran at 31 fps; the GIFs run at whatever rate was encoded. If the GIF was captured at 25 fps, that is what plays. To restore 31 fps, re-export the GIF at that rate.

---

## Related Repositories

| Repo | Theme |
|------|-------|
| [`Skyline-Series`](https://github.com/reyrove/Skyline-Series) | Themed cityscapes |
| [`Portrait-Series-Generative-Art`](https://github.com/reyrove/Portrait-Series-Generative-Art) | Generative faces |
| [`Girih-2-Generative-Art`](https://github.com/reyrove/Girih-2-Generative-Art) | Islamic geometric ornament |
| [`Gothic-Grid-Generative-Art`](https://github.com/reyrove/Gothic-Grid-Generative-Art) | Mosaic grid composition |
| [`Order-to-Chaos-Generative-Art`](https://github.com/reyrove/Order-to-Chaos-Generative-Art) | Gradient grid composition |
| [`Wallpaper-Groups-Generative-Art`](https://github.com/reyrove/Wallpaper-Groups-Generative-Art) | Crystallographic symmetry |
| [`Wandering-Tiles-Generative-Art`](https://github.com/reyrove/Wandering-Tiles-Generative-Art) | Line-drawing composition |
| [`Food-Grid-Generative-Art`](https://github.com/reyrove/Food-Grid-Generative-Art) | Illustrated food grid |
| [`Framed-Line-Generative-Art`](https://github.com/reyrove/Framed-Line-Generative-Art) | Gesture line composition |
| [`Deconstructed-Stage-Generative-Art`](https://github.com/reyrove/Deconstructed-Stage-Generative-Art) | Suprematist composition |
| [`Layered-Diagram-Generative-Art`](https://github.com/reyrove/Layered-Diagram-Generative-Art) | Layered linework composition |
| [`Japanese-Patterns-Generative-Art`](https://github.com/reyrove/Japanese-Patterns-Generative-Art) | Traditional motif composition |
| [`Matrix-Rain-Generative-Art`](https://github.com/reyrove/Matrix-Rain-Generative-Art) | Digital rain composition |
| [`Organic-Shapes-Generative-Art`](https://github.com/reyrove/Organic-Shapes-Generative-Art) | Layered petal-form composition |
| [`Recursive-Grid-Generative-Art`](https://github.com/reyrove/Recursive-Grid-Generative-Art) | Recursive subdivision composition |
| [`Generative-Lifeform-Generative-Art`](https://github.com/reyrove/Generative-Lifeform-Generative-Art) | Network / node-graph composition |
| [`Game-of-Seeds-Generative-Art`](https://github.com/reyrove/Game-of-Seeds-Generative-Art) | Cellular automaton composition |
| **`Fibonacci-Spin-Generative-Art`** | Fibonacci orbit collection *(this repo)* |

This is the first **collection page** in the family. Previous repos present a single work; this one presents two works that belong to the same system.

### Related Work Pages

The two works in this collection have their own repositories:

- [`Fibonacci-Spin-Purple-Golden-Lines`](https://github.com/reyrove/Fibonacci-Spin-Purple-Golden-Lines) — single work page
- [`Fibonacci-Spin-Cyan-Golden-Ellipses`](https://github.com/reyrove/Fibonacci-Spin-Cyan-Golden-Ellipses) — single work page

Each work page follows the same editorial template, but presents a single GIF as the hero, with the same surfaces, process, and commission structure.

---

## Credits

- **Design & Motion Systems** — Reyhaneh Daneshdoost
- **Typefaces** — Cormorant Garamond, DM Mono
- **Original works** — Purple Golden Lines · Cyan Golden Ellipses
- **Sequence reference** — Fibonacci (1, 1, 2, 3, 5, 8, 13, 21, 34) · golden ratio (φ ≈ 1.618)
- **Collection** — Fibonacci's Spin, Autumn 2026

---

## License

All artwork, code, and motion systems are the intellectual property of the artist. Works may not be reproduced, redistributed, resold, or adapted without a written licence.

For licensing, commissions, or private systems: **reyhanehdaneshdoost@gmail.com**