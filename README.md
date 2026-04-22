# PEAK partner landing page

Two builds live side-by-side in this repo:

| File                | Role                                                         |
| ------------------- | ------------------------------------------------------------ |
| `index.html` (root) | **Original, gold-standard reference.** Do not modify.        |
| `src/index.html`    | **Maintainable rebuild** using Tailwind CSS + component CSS. |

The goal of the rebuild is to make iterating on the page fast without hunting through a 1,147-line monolith.

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

## Adding a new section

1. Create `src/styles/components/<name>.css` containing an `@layer components { ... }` block.
2. Add one line to `src/styles/main.css`: `@import "./components/<name>.css";`
3. Add the corresponding markup block to `src/index.html` with a section-header comment.
4. Re-run `npm run dev` — watch picks it up automatically.

## Deploy

The repo deploys to surge.sh. `.surgeignore` excludes dev-only files (`node_modules/`, `package.json`, source CSS). The root `index.html` remains canonical; `src/index.html` ships alongside it for parallel review.
# cim-partner-website
