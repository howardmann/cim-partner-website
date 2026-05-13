# PEAK partner landing page

Two builds live side-by-side in this repo:

| File                | Role                                                         |
| ------------------- | ------------------------------------------------------------ |
| `index.html` (root) | **Original, gold-standard reference.** Do not modify.        |
| `src/index.html`    | **Maintainable rebuild** using Tailwind CSS + component CSS. |

The goal of the rebuild is to make iterating on the page fast without hunting through a 1,147-line monolith.

> **Design language** — palette, typography, components, and the "crossing the line" campaign grammar — is documented in [`DESIGN.md`](./DESIGN.md). Read it before adding new sections or starting sibling pages (e.g. the upcoming peak-ai-landing-page).

## Folder layout

```
braindump/
├── index.html                 # Original — frozen reference
├── cim-logo.svg               # Original inline SVG (root)
├── copy.md                    # Content brief
│
├── package.json               # Tailwind v4 CLI + build scripts
├── README.md                  # This file
│
└── src/                       # Maintainable rebuild lives here
    ├── index.html             # Clean markup, each section clearly fenced
    ├── styles.css             # ⚙️ Built output (gitignored)
    ├── assets/
    │   ├── cim-logo.svg       # Dark-bg variant (for light nav)
    │   └── cim-logo-white.svg # Light-bg variant (for dark footer)
    └── styles/
        ├── main.css           # Entry: @import tailwind + @theme + component imports
        ├── base.css           # Reset, body, .wrap (page-width), .mono
        ├── responsive.css     # All media-query overrides in one place
        └── components/        # One file per logical component group
            ├── eyebrow.css
            ├── buttons.css
            ├── sections.css   # .block, .section-h, .section-sub
            ├── nav.css
            ├── hero.css
            ├── shift.css
            ├── stuck.css
            ├── platform.css   # peak-intro, stage-label, feat-grid, roadmap
            ├── pitch.css
            ├── economics.css
            ├── partners.css
            ├── logos-stats.css
            ├── final-cta.css
            └── footer.css
```

## Setup

```bash
npm install
```

## Development

Start Tailwind in watch mode — re-compiles `src/styles.css` whenever you edit any CSS under `src/styles/`:

```bash
npm run dev
```

Serve `src/` locally (Python's built-in server works fine):

```bash
npm run serve        # → http://localhost:4000
```

Then open the two tabs side-by-side to diff against the gold standard:

- `http://localhost:4000` → rebuilt version
- Open `index.html` at repo root as a file:// URL → original

## Production build

Minified output for deploy:

```bash
npm run build
```

## Design tokens

All brand colors, fonts, radii, and the container max-width are defined **once** in `src/styles/main.css` under `@theme`:

```css
@theme {
  --color-ink:         #0a0a0a;
  --color-accent:      #0f6b4d;
  --color-bg-alt:      #f6f6f4;
  /* ... */
  --font-sans: "Inter", ...;
  --font-mono: "JetBrains Mono", ...;
}
```

Changing a brand color — e.g. shifting the accent green — is a one-line edit that cascades to every component via CSS variables, and is simultaneously available as Tailwind utilities (`bg-accent`, `text-ink`, `border-line`, `font-mono`, etc.) anywhere in the HTML.

## Design system

[`DESIGN.md`](./DESIGN.md) is the source of truth for everything visual. Read it before adding markup or CSS — especially when starting sibling pages like peak-ai-landing-page, where drift from this system is the failure mode.

The load-bearing rules (the ones that hurt the page most when broken):

- **One accent.** `#0f6b4d` is a *signal*, not decoration. Never a button fill at rest (accent is the hover state). Never on paragraph-length text — it fails AA-body against `bg`.
- **Two typefaces.** Inter for language, JetBrains Mono for *metadata* (eyebrows, stat labels, FROM→TO tags, status). No third family. Mono in running prose is a smell.
- **Header rhythm.** Every section is `eyebrow` + `<h2 class="section-h">` (terminal period) + `<p class="section-sub">`. The header stack *is* the design.
- **From → To.** The `shift-from .from` / `.arrow-right` / `.to` pattern is the campaign's verb. Don't drop the strikethrough, don't swap the arrow, don't use ink instead of accent for the "to" word.
- **Grid dividers via `gap: 1px`.** Parent paints `line`, cells paint `bg`, gap exposes the line. Use this for every new grid — no per-cell borders.
- **Shapes.** Radius scale is `0 / 2 / 4 / 6 / 8` — 4px (`rounded.sm`) does ~80% of the work. Callouts and pull-quotes are square (`rounded.none`); they are editorial devices, not cards.
- **Flat by default.** The only shadows on the page are the hero card stack and the lanyard. No card/button shadows. Depth comes from borders and dark inverted panels.
- **Three dark panels, no more.** `peak-intro`, `quote-dark`, `cx-hero-crossing` cover every inverted use case. Don't invent a fourth.

When in doubt, grep the existing components in `src/styles/components/` and reuse the vocabulary before authoring new CSS.

## Adding a new section

1. **Read the relevant parts of [`DESIGN.md`](./DESIGN.md)** — at minimum *Colors*, *Typography*, and *Components*.
2. **Reuse an existing component** before writing new CSS — `card-flat`, `pitch`, `callout`, `peak-intro`, `quote-dark`, `partner-card`, `price-card` cover most needs. A new component should be justifiable against `DESIGN.md`'s component list.
3. Create `src/styles/components/<name>.css` containing an `@layer components { ... }` block.
4. Add one line to `src/styles/main.css`: `@import "./components/<name>.css";`
5. Add the corresponding markup block to `src/index.html` with a section-header comment, opening with the eyebrow + `section-h` + `section-sub` stack.
6. Re-run `npm run dev` — watch picks it up automatically.

## Deploy

```bash
npm run deploy
```

Runs `npm run build` (minified Tailwind output) then publishes `./src` to `cim-partner.surge.sh`. `src/.surgeignore` excludes the Tailwind source CSS under `src/styles/`.

## Hosted assets

Heavy media is kept out of the repo and hosted externally:

| Asset                  | Host   | URL                                                       |
| ---------------------- | ------ | --------------------------------------------------------- |
| `ai_analyst_square.mp4` | Vimeo  | https://vimeo.com/1191810559?share=copy&fl=sv&fe=ci       |

Used on the peak-ai-landing-page. Embed via Vimeo's player rather than re-uploading the source file.
# cim-partner-website
