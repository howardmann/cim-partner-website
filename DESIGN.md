---
version: alpha
name: PEAK Partner
description: Editorial, high-contrast neutral-and-accent design system for the CIM PEAK partner landing page. Single accent green carries every signal — interaction, "to-state" in shift language, leading rules on eyebrows, draw-in marks on the hero.
colors:
  ink: "#0a0a0a"
  ink-2: "#1f1f1f"
  bg: "#ffffff"
  bg-alt: "#f6f6f4"
  muted: "#5a5a58"
  line: "#e6e4de"
  line-strong: "#cfccc3"
  accent: "#0f6b4d"
  accent-soft: "#e7f2ed"
  accent-ink: "#0a4a35"
  accent-on-dark: "#3fb08a"
  amber: "#d97706"
  danger: "#dc2626"
  on-ink: "#ffffff"
  muted-on-ink: "#c9c7c0"
  divider-on-ink: "#1f1f1f"
typography:
  display:
    fontFamily: Inter
    fontSize: 68px
    fontWeight: 700
    lineHeight: 1.04
    letterSpacing: -0.028em
  h2:
    fontFamily: Inter
    fontSize: 44px
    fontWeight: 700
    lineHeight: 1.1
    letterSpacing: -0.022em
  h3:
    fontFamily: Inter
    fontSize: 22px
    fontWeight: 500
    lineHeight: 1.35
    letterSpacing: -0.012em
  hero-lead:
    fontFamily: Inter
    fontSize: 22px
    fontWeight: 500
    lineHeight: 1.35
    letterSpacing: -0.012em
  section-sub:
    fontFamily: Inter
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.6
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.55
  body-sm:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.55
  caption:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.55
  eyebrow:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0.14em
  mono-label:
    fontFamily: JetBrains Mono
    fontSize: 11px
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0.14em
  mono-data:
    fontFamily: JetBrains Mono
    fontSize: 13px
    fontWeight: 500
    lineHeight: 1.2
rounded:
  none: 0px
  xs: 2px
  sm: 4px
  md: 6px
  lg: 8px
spacing:
  px: 1px
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  2xl: 48px
  3xl: 64px
  4xl: 96px
  5xl: 120px
  container-max: 1180px
  gutter: 28px
components:
  btn-primary:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-ink}"
    rounded: "{rounded.sm}"
    padding: 12px 20px
    typography: "{typography.body-sm}"
  btn-primary-hover:
    backgroundColor: "{colors.accent}"
    textColor: "{colors.on-ink}"
  btn-ghost:
    backgroundColor: transparent
    textColor: "{colors.ink}"
    rounded: "{rounded.sm}"
    padding: 12px 20px
  btn-ghost-hover:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-ink}"
  btn-sm:
    padding: 8px 14px
    typography: "{typography.caption}"
  eyebrow:
    textColor: "{colors.muted}"
    typography: "{typography.eyebrow}"
  block:
    backgroundColor: "{colors.bg}"
    padding: 96px 0
  block-alt:
    backgroundColor: "{colors.bg-alt}"
  card-flat:
    backgroundColor: "{colors.bg}"
    rounded: "{rounded.sm}"
    padding: 28px
  callout:
    backgroundColor: "{colors.bg-alt}"
    textColor: "{colors.ink-2}"
    rounded: "{rounded.none}"
    padding: 28px 32px
  pitch:
    backgroundColor: "{colors.bg}"
    textColor: "{colors.ink-2}"
    rounded: "{rounded.sm}"
    padding: 28px 28px 28px 32px
  price-card:
    backgroundColor: "{colors.bg}"
    rounded: "{rounded.sm}"
    padding: 36px
  peak-intro:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-ink}"
    rounded: "{rounded.sm}"
    padding: 40px 48px
  quote-dark:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.on-ink}"
    rounded: "{rounded.none}"
    padding: 48px 56px
  feat-grid-cell:
    backgroundColor: "{colors.bg}"
    padding: 28px
  partner-card:
    backgroundColor: transparent
    padding: 28px 24px 32px
  partner-card-hover:
    backgroundColor: transparent
  site-footer:
    backgroundColor: "{colors.ink}"
    textColor: "#a8a59d"
    padding: 64px 0 40px
---

## Overview

Editorial Minimalism meets Industrial Data-Sheet. The page reads like a contemporary broadsheet that has been refit for a building-systems audience: deep ink headlines on warm-paper neutrals, a single accent green doing every load-bearing job, and monospace metadata where a designer would normally reach for a chip or a tag.

The page is desktop-first. Sections are roomy (`96px` block padding), grids are gap-`1px` so dividers come *from* the line color underneath rather than from per-cell borders, and decoration is rationed — when the accent appears (an eyebrow rule, a `::before` left-bar, a "to-state" word, a draw-in scribble under the headline) it is meant to be the *only* colored thing in that viewport.

The campaign metaphor is **"crossing the line"**: every section pairs a struck-through "from" state with an accented "to" state. Designers and writers should treat this as the page's first-class verb — the visual grammar (`from → to`, the diagonal in `cx-hero-crossing`, the line-through on `shift-from .from`, the accent on `shift-from .to`) is not interchangeable with generic comparison patterns.

## Colors

The palette is engineered around a single accent. Treat accent green as a *signal*, not a decoration — if you reach for it twice in one viewport, one of the two uses is probably wrong.

- **Ink (`#0a0a0a`)** — Headlines, body text, primary buttons, the dark inverted panels (`peak-intro`, `quote`, `cx-hero-crossing`, `site-footer`). The page's structural color.
- **Ink-2 (`#1f1f1f`)** — Secondary body weight; used inside pitch quotes, closer paragraphs, callouts. One step softer than ink so primary headlines still win.
- **Muted (`#5a5a58`)** — Captions, eyebrow text, section-sub, "from-state" words, nav inactive links. Always paired with ink; never used on the alt background for body copy.
- **Line (`#e6e4de`)** — Default divider. Sits behind grids that use the `gap: 1px` reveal trick (`.feat-grid`, `.stats`, `.logos`, `.rs-grid`).
- **Line-strong (`#cfccc3`)** — Heavier dividers (price-card border, brand divider in the nav). Reserved for places where the line itself is part of the composition.
- **Accent (`#0f6b4d`)** — The only chromatic color in the system. Reserved for: leading rule on eyebrows, "to-state" words in `shift-from`, `pitch::before` left bar, primary CTA hover, animated `deliver-mark` / `ai-mark` scribbles, `feat-num` and stat highlight numbers, callout left border, lanyard rank number.
- **Accent-soft (`#e7f2ed`)** — Hero radial glow only.
- **Accent-ink (`#0a4a35`)** — Darker accent for the `aw-callout` "52%" annotation on the assurance waterfall.
- **Accent-on-dark (`#3fb08a`)** — Lifted accent used *only* on ink backgrounds (radiologist dark cell, charts on dark). The base accent fails contrast on ink.
- **Amber (`#d97706`)** — "Later" / "shipping later" stage tab in `platform.css`, the amber status dot in the hero cards. Never used as a primary brand color.
- **Danger (`#dc2626`)** — Red status dot only. Not used for borders, type, or fills.
- **Bg-alt (`#f6f6f4`)** — Alternating section background to break vertical rhythm, and the fill of the `.callout` and `.roadmap` cells. Slightly warm — not pure grey.

### Surfaces & contrast

- Light surfaces: `{colors.bg}` and `{colors.bg-alt}`.
- Dark surfaces: `{colors.ink}` only. Inside ink panels, body copy uses `{colors.muted-on-ink}` (`#c9c7c0`) and dividers use `{colors.divider-on-ink}` (`#1f1f1f`) or the ink-on-ink hairline `#2b2b2b`.
- Ink on bg: 19:1 — comfortably AAA.
- Accent on bg: ~5.6:1 — AA for body, AA-large for UI; do not use accent for paragraph-length text.

## Typography

Two families. No third. **Inter** for everything that reads as language; **JetBrains Mono** for everything that reads as metadata (eyebrows, stat labels, "FROM → TO" tags, status badges, the lanyard kicker).

- **Display (`{typography.display}`)** — `clamp(40px, 5.2vw, 68px)`, 700, `-0.028em`. Hero headline only. `<em>` inside the display is non-italic and switches to `{colors.accent}` — that is the single approved emphasis treatment for the top of the page.
- **H2 / `.section-h` (`{typography.h2}`)** — `clamp(30px, 3.4vw, 44px)`, 700, `-0.022em`. Max-width 780px so headlines wrap to 2-3 lines and don't span the full grid.
- **Hero-lead (`{typography.hero-lead}`)** — 22px, 500. Sits between display and body — the one place medium weight is allowed in running prose.
- **Section-sub (`{typography.section-sub}`)** — 17px, muted, max-width 720px. The descender under an H2.
- **Body (`{typography.body-md}`)** — 16px / 1.55 base. Line length is enforced via `max-width` on the *parent*, not on `body` — 50–72ch depending on context.
- **Eyebrow (`{typography.eyebrow}`)** — 12px Inter, 500, uppercase, `0.14em` tracking, muted. Always prefixed by a 22px × 2px accent rule (`::before`). The eyebrow is the page's section-marker; every block has exactly one.
- **Mono label (`{typography.mono-label}`)** — JetBrains Mono, 11px, uppercase, `0.14em` tracking. Used for: `stage-label`, `feat-num`, `shift-from`, `stat-label`, `rs-label`, `lanyard-kicker`. Mono signals *data*, never *prose*.

### Type-feel rules

- Optical kerning via negative `letter-spacing` on display/H2/H3 — never on body or labels.
- Italic is reserved for the `.note` and `.aw-note` footnote treatments only. The hero display `<em>` is *not* italic — it overrides to non-italic intentionally.
- Numbers in stats and the lanyard rank use `font-feature-settings: "tnum" 1` where available (tabular figures).

## Layout

The page uses a single fixed-width wrapper, not a fluid grid.

- **Wrap (`.wrap`)** — `max-width: 1180px`, `0 28px` gutter, centered. Every section sits inside one.
- **Block rhythm** — `96px` top/bottom padding per `.block`, dropping to `72px` at tablet (≤ 980px). The hero gets `96px 0 88px` and shrinks to `64px 0` on tablet.
- **Section dividers** — `1px solid {colors.line}` *between* every block. There is no gutter band — the rule itself is the rhythm.
- **Alternating fill** — `.block.alt` paints `{colors.bg-alt}`. Use sparingly; two adjacent alt blocks defeat the rhythm.
- **Two-column splits** — `1.5fr 1fr` (hero, peak-intro), `1.1fr 1fr` (stuck split), `1fr 1fr` (econ, partner persona pair). All collapse to `1fr` at 980px with a fresh `48px` gap.
- **Multi-column grids** — Feature grid is `repeat(4, 1fr)` desktop → `repeat(2, 1fr)` tablet → `1fr` phone. The "1px-gap reveal" trick is canonical: parent paints `{colors.line}`, cells paint `{colors.bg}`, `gap: 1px` exposes the line color as dividers. Use this instead of per-cell borders.
- **Container queries** — Not used. All responsive behavior is centralized in `responsive.css` at two breakpoints: 980px (tablet) and 560px (phone).

### Breakpoints

| Token | Width | What changes |
|-------|-------|--------------|
| Desktop | `> 980px` | Full multi-column grids, nav links visible, hero visual visible |
| Tablet | `≤ 980px` | All 2-/3-/4-col grids collapse; nav links hidden; ghost CTA hidden; hero visual hidden |
| Phone | `≤ 560px` | Remaining grids → `1fr`; lanyard shrinks; quote tightens |

## Elevation & Depth

The system is deliberately *flat*. Shadows are reserved for two specific purposes and should not be used elsewhere.

- **Hero card stack** — `0 1px 0 rgba(0,0,0,0.02), 0 8px 24px rgba(15,107,77,0.06)`. A tinted, very soft drop with an accent green undertone — the cards float over `{colors.bg-alt}` and the shadow's green tint ties them to the page's accent without using accent as a fill.
- **Lanyard badge** — `0 12px 28px rgba(0,0,0,0.28)` (with a matching shadow on the foot strip at `0.24`). The lanyard is the *one* deliberately raised element on the page — it's an award; it should feel pinned over the dark quote panel like a real lanyard.
- **Hero radial glow** — `radial-gradient(circle, {colors.accent-soft} 0%, transparent 70%)` at `0.6` opacity, anchored top-right of the hero. Treated as atmospheric *light*, not as a card lift.

Everything else — buttons, callouts, cards, the price card, partner cards, quote, footer — has **no shadow**. Depth in this system comes from borders, dark inverted panels, and the `1px-gap` divider trick.

## Shapes

- **Default radius (`{rounded.sm}` = 4px)** — Buttons, cards, the peak-intro panel, grid wrappers, the price card.
- **Tighter radius (`{rounded.xs}` = 2px)** — The waterfall chart shell (`aw-chart-wrap`), the lanyard badge / foot strip.
- **Square (`{rounded.none}`)** — The `.callout`, the dark `.quote` panel, the `.cx-hero-crossing` section, the radiologist split cells. Editorial pull-quotes are intentionally flat-cornered to read as **pull-quotes, not as cards**.
- **Pill / fully rounded** — Only on the status `.dot` (`50%`) and the `.aw-callout` ::before marker (`999px`). Pills are never used for tags or buttons.
- **Hairlines** — All borders are `1px solid {colors.line}`. The accent left-bars on `.pitch::before` and `.callout` are `3px`. The eyebrow rule is `2px × 22px`.

The shape vocabulary is: **flat rectangles with 4px radius, with the occasional fully-square pull-quote.** Anything more elaborate (heavily rounded cards, asymmetric corners, beveled buttons) does not belong here.

## Components

### Buttons

`{components.btn-primary}` — Ink-fill primary, white text, 4px radius, with an animated `→ .arrow` child that nudges `3px` right on hover. Hover swaps fill *and* border to `{colors.accent}`. There is no disabled state because the page has no forms; the buttons are anchor links.

`{components.btn-ghost}` — Transparent fill, ink border, ink text. Hovers to the inverse (ink fill, white text). Used as the secondary CTA next to the primary `Apply` button.

`{components.btn-sm}` — Compact variant for the nav. Same vocabulary, smaller padding.

> Rule: never use accent as a button fill. The accent fill exists only as a *hover state* on the primary button. A flat green button at rest reads as a marketing CTA from a different design system.

### Eyebrow (section marker)

Every section begins with `<div class="eyebrow">…</div>`. Structure: `[accent rule] [10px gap] [mono-spaced uppercase muted text]`. The leading rule is the page's most-repeated accent appearance — it ties every section back to the brand.

The eyebrow text itself is **muted, not accent**. A page full of accent-colored eyebrows reads as stamped/templated; the rule alone carries the color.

### Section heading system

```
<eyebrow>SECTION NAME</eyebrow>
<h2 class="section-h">Sentence-case headline with terminal period.</h2>
<p class="section-sub">One paragraph, ≤ 720px, muted.</p>
[block body]
```

H2s use a terminal period — editorial voice, not marketing voice.

### Cards

`{components.card-flat}` — Default card pattern: white fill, 1px line border, 4px radius, 28px padding. The system's default container — use this unless there is a specific reason to use one of the specialized variants below.

`{components.pitch}` — Pull-quote card with a `3px` accent left-bar inset from top/bottom (not flush). The accent bar is the only color in the card. Used for the "sales-call lines" grid.

`{components.partner-card}` — Border-less card identified by a `2px` ink top-rule that turns accent on hover. No fill, no shadow — the rule is the entire card.

`{components.callout}` — `{colors.bg-alt}` fill with a `3px` accent left border. Square corners. Sits inline in prose as a pull-quote.

`{components.price-card}` — Stronger border (`line-strong`), 36px padding. The price `<span>` uses accent inline. Bullet list uses an accent `✓` glyph rendered via `::before`.

### Inverted (dark) panels

Three variants of "dark panel" exist; do not invent a fourth:

- `{components.peak-intro}` — 4px radius, 40px / 48px padding, holds a 2-column intro grid.
- `{components.quote-dark}` — Square corners, 48px / 56px padding, generous type. The lanyard hangs over its top-right.
- `cx-hero-crossing` — Full-bleed section (not a contained panel), 120px vertical padding, hosts the diagonal SVG and the "you / firms already across" split.

All three use `{colors.ink}` background, white headlines, `{colors.muted-on-ink}` body, and either `#2b2b2b` or `#1f1f1f` for in-panel hairlines.

### "From → To" pattern (campaign-critical)

The `shift-from` token, the `cx-cta-crossing` echo, and the `cx-hero-crossing` diagonal are one family. They share the same vocabulary: a struck-through muted "from" word, an accent "to" word, separated by an arrow or a diagonal stroke.

- `shift-from .from` — muted, `line-through` with `decoration-color rgba(90,90,88,0.55)`, `decoration-thickness: 1.5px`.
- `shift-from .arrow-right` — accent, sans-family, 18px, sits between from/to.
- `shift-from .to` — accent, weight 600.

This is the page's signature device. Do not loosen it (e.g. removing the strikethrough, swapping the arrow for an em-dash, using ink instead of accent for the "to" word).

### Data-grid (1px-gap reveal)

`.feat-grid`, `.stats`, `.logos`, `.rs-grid`, `.roadmap` all share one pattern: parent paints `{colors.line}`, `gap: 1px`, cells paint `{colors.bg}`. This produces pixel-perfect dividers without per-cell border math and survives both odd cell counts and responsive collapse.

When adding a new grid, copy this pattern rather than reaching for individual cell borders.

### Status dots

`.dot` (accent green default), `.dot.amber`, `.dot.red`. Used inline before status text in the hero card stack and the platform features. The dot is the *only* place red appears on the page.

### Animation

The system reserves animation for moments that pay off the campaign's "crossing" thesis:

- **Hero scribble marks** — `deliver-mark` (under "Come deliver it", 900ms at 1500ms delay) and `ai-mark` (under "AI", 700ms at 3200ms delay) draw in via `clip-path: inset(...)` over an SVG mask. The accent color stays in one place (the fill behind the mask). Both honor `prefers-reduced-motion`.
- **Crossing diagonal** — `cx-hero-crossing .cx-mark .stroke` draws in via `stroke-dasharray` over 1400ms. Reduced-motion users see it pre-drawn.
- **Waterfall chart** — `aw-chart-wrap` triggers a scroll-revealed Chart.js animation; the `52%` callout (`aw-callout`) fades in *after* the bars land via `.is-live` toggling opacity/translate.
- **Button arrow nudge** — 150ms transform on hover (`translateX(3px)`).

Anything else (parallax, scroll-tied transforms, looping motion) is out-of-scope for this system.

## Do's and Don'ts

**Do**

- Use the eyebrow + section-h + section-sub stack on every new section. The header rhythm *is* the design.
- Keep accent reserved. Ask: "Is there already an accent-colored thing in this viewport?" If yes, find a different way.
- Use the `gap: 1px` background-paint trick for any new grid of cells.
- Use mono for *data* (numbers, codes, status, "from → to" tags) and sans for *language*. Mono in running prose is a smell.
- Keep callouts and quotes square-cornered. They are editorial devices, not cards.
- Drop responsive overrides into `responsive.css` (centralized) rather than in component files — there are two existing component-local exceptions (`stuck.css`, `assurance.css`); follow that pattern only when the override is highly local.

**Don't**

- Don't paint an accent-fill button at rest. Accent is the *hover* state, by design.
- Don't introduce a third typeface. Inter and JetBrains Mono carry the whole system.
- Don't add shadows to cards or buttons. The two shadow uses (hero cards, lanyard) are explicit exceptions; the system's depth comes from borders.
- Don't use amber or red as brand colors. They are status-dot semantics only.
- Don't soften the "from → to" pattern (removing strikethrough, swapping the arrow, demuting the "from" word). It is the campaign's verb.
- Don't use accent green for paragraph-length text — it passes AA-large but fails AA-body against `{colors.bg}`.
- Don't reach for new radius values. `0 / 2 / 4 / 6 / 8` is the entire scale, and 4px does ~80% of the work.
- Don't add a third dark-panel variant. The three (`peak-intro`, `quote-dark`, `cx-hero-crossing`) already cover the use cases; a fourth dilutes the inverted-panel signal.
- Don't use `<em>` for prose emphasis — italic only appears in `.note` and `.aw-note`. The display `<em>` is a non-italic accent override.
