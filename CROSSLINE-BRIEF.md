# "Cross the line" — campaign brief & v2 audit

A later-session reference documenting (a) the intent behind turning this site into a "Cross the line" campaign, (b) every change made in `src/v2.html` vs the untouched `src/index.html`, and (c) what to audit when picking this back up.

---

## 1. The intent

The site already uses "cross the line" language in several places (shift closer, stuck heading, logos heading, final CTA). The copy is strong but the **visual motif is absent** — nothing in the UI enacts the crossing. The goal is to turn "Cross the line" into a **campaign-level visual grammar** that a reader feels at every scroll position, not just a phrase that appears four times.

### Strategic positioning (resolved in the grilling session)

| Decision | Choice | Why |
|---|---|---|
| Scope | **Campaign theme** (not brand tagline, not site-only motif) | CIM is the brand, PEAK is the product. "Cross the line" is a third voice — powerful enough for partner-facing collateral but not promoted to brand-tagline status. Loud on the partner site and deck, absent from CIM-corporate / product-UI surfaces. |
| Motif shape | **Texture + a singular Line moment** | Pure texture = no "the" moment. Pure singular = too austere. Mixed gives rhythm: small recurring accents build vocabulary, then one big payoff cashes it in. |
| Line character | **Two voices, one system** — hand-drawn wobble for practitioner (hero underlines); clean engineered line for platform (thresholds) | Wobble = "we're engineers like you, we marked this." Clean engineered line = "we built the platform you're crossing to." The industry reads blueprints / trend plots / BMS charts — survey-line aesthetics are native. |
| Narrative fix | **Front-load (Shape 1) + Thread (Shape 2)**; skip restructure | Five consecutive sections (platform → logos) currently go silent on the metaphor. Fix by planting the frame in the hero and threading visual lines through each section — not by reordering. |
| Orientation | **Vertical-primary**, not horizontal | "Cross the line" is a lateral-motion metaphor. A vertical line is a threshold the reader's *eye* crosses left-to-right in a single glance — no scroll trigger needed. Maps cleanly onto existing 2-col layouts. Horizontal capital-L band dropped entirely. |

### The three visual voices

| Voice | Grammar | Job | Where |
|---|---|---|---|
| **Wobble horizontal** | Hand-drawn SVG mask, accent-green, warm | Practitioner: "trust this word" | Hero underlines on "Come deliver it" and "AI" (existing, untouched) |
| **Engineered vertical line** | 1.5px accent-green stroke, mono tick-caps top & bottom, optional mono labels | Platform: "this is a threshold. cross it." | 5 new placements (see §3) |
| **Eyebrow horizontal dash** | Small accent-green segment before section label | Waypoint texture / connective tissue | All section eyebrows (existing) |

---

## 2. Files changed

```
src/v2.html                               ← NEW. Clone of index.html with treatments applied.
src/styles/components/crossline.css       ← NEW. All rules prefixed `cx-`; scoped to v2.
src/styles/main.css                       ← +1 line: import crossline.css last.
src/index.html                            ← UNTOUCHED. Gold-standard reference.
package.json                              ← playwright added as dev dep (for screenshot tooling).
```

CSS scoping rule: every new class is `cx-` prefixed and only referenced by `v2.html`. Nothing in `index.html` is affected by `crossline.css` even though it's imported in the shared `main.css`.

---

## 3. Per-section treatment matrix (v1 vs v2)

Compare `src/index.html` (v1, gold standard) vs `src/v2.html` (campaign treatment):

| Section | v1 (index.html) | v2 (v2.html) |
|---|---|---|
| **Hero eyebrow** | `PARTNER PROGRAM · FDD & MBCx` | `PARTNER PROGRAM · Cross the line` — frame planted in the first screen so bouncers still get the theme |
| **Hero underlines** | Wobble underlines on "Come deliver it" and "AI" | **Unchanged.** These are the practitioner voice and are working. |
| **Shift cards (3)** | Eyebrows like `RCx → MBCx` — plain arrow | `RCx ⊢──⊣ MBCx` — engineered crossing mark (tick + bar + tick, all accent-green). Animated scale-X draw-in. Micro-crossings on all three cards. |
| **Shift closer** | Single paragraph: *"Every RCx/MBCx firm… has to cross this line. You either hire a software team… or partner with one already on the other side."* | Setup sentence shortened; the binary choice is rebuilt as a visible crossing: **LEFT** `BUILD ALONE` + muted copy · **vertical accent line** with tick caps (draws in on viewport entry) · **RIGHT** `ALREADY ACROSS` + weighted copy |
| **Stuck section** | `.split` 2-col: headline/copy left, numbered list right | `.cx-split.stuck` — same 2-col, with a **vertical accent line with tick caps** as the central spine between the two columns |
| **Stuck callout** | Green `border-left` on the "tagging framework isn't a platform" callout | **Unchanged.** Already fits the grammar. |
| **Platform "One platform. Two divisions of labour" panel** | Dim dark-grey `border-left` on the right (CIM operates / Partner operates rows) | Wrapper gets `.cx-peak`; the divider is re-drawn as an **accent-green vertical line with tick-caps top & bottom**. Makes the literal "divisions of labour" an engineered threshold. |
| **Platform feature grids (`AI TODAY` / `AI ROADMAP`)** | Stage labels with hairline rules | **Unchanged.** Already in the grammar. |
| **Economics** | `.econ` 2-col: copy left, price card right | `.cx-split.econ` — same 2-col with a **vertical accent line between** copy and card. "Ask on the left, deal on the right." |
| **Partners (3-card grid)** | Card-top borders, standard layout | **Unchanged.** Three-way split doesn't fit a binary threshold metaphor. |
| **Logos + quote** | Heading "The firms already on the other side of the line" | **Unchanged.** Copy already pays off. |
| **Final CTA** | H2 "Cross the line with a platform, not a toolkit" | H2 unchanged. **New below the H2:** a tight `TOOLKIT │ PLATFORM` micro-crossing — `TOOLKIT` (mono, muted, strikethrough) · vertical accent line with tick-caps (draw-in animation) · `PLATFORM` (mono, bold, accent). The literal embodiment of the headline. Screenshot-worthy. |

### Reduced-motion support

All draw-in animations (`.cx-cross .bar`, `.cx-line.animated`) disable themselves under `prefers-reduced-motion: reduce`.

### Responsive

Below 820px: `.cx-split`, `.cx-closer`, and `.cx-cta-crossing` collapse to single-column, and vertical lines are hidden (they don't translate well narrow). Copy stacks.

---

## 4. How to view the comparison

```bash
npm run build                     # rebuild styles.css
python3 -m http.server 4321 --directory src &

# v1 (gold):
open http://127.0.0.1:4321/

# v2 (campaign):
open http://127.0.0.1:4321/v2.html
```

Playwright is now a project dev-dep (`package.json`), so screenshot scripts can run from repo:

```bash
node -e "const {chromium}=require('playwright'); (async()=>{ \
  const b=await chromium.launch(); const p=await (await b.newContext({viewport:{width:1440,height:900}})).newPage(); \
  await p.goto('http://127.0.0.1:4321/v2.html'); await p.waitForTimeout(4000); \
  await p.screenshot({path:'v2-full.png', fullPage:true}); await b.close(); })();"
```

---

## 5. Known open questions — audit checklist for next session

When auditing v2 later, check these explicitly:

1. **Does the final CTA crossing feel like a payoff, or like a decoration?** The whole campaign is supposed to land there. If it feels small or skippable, increase its scale or add the mono labels `BEFORE`/`AFTER` back in (currently dropped as redundant with Toolkit/Platform).
2. **Does the shift closer land as a *choice* or as a *fact*?** Left-side copy is deliberately muted; right-side is weighted. The visual hierarchy should make the right feel like the preferred path without being editorial.
3. **Is the platform panel's branded divider too subtle on dark background?** 1.5px accent-green on `#0a0a0a` — check it holds on a low-brightness monitor.
4. **Do the shift-card micro-crossings (`RCx ⊢──⊣ MBCx`) still read as arrows, or as boundaries?** Intended as boundaries. If readers still parse them as arrows, consider widening the bar or adding a tiny "BEFORE"/"NOW" axial mark.
5. **Narrative-silence sections (platform grids, partnership, partners, logos).** Did we thread enough texture that these don't feel absent from the campaign? If not, revisit Shape 2 — e.g., add tiny accent-green ticks before each section H2.
6. **Hero wobble underlines on "Come deliver it" and "AI"** — do they fight with the new engineered-vertical grammar, or complement it? They are the practitioner voice and should stay, but verify the grammars coexist cleanly.
7. **Responsive narrow viewport (<820px).** Vertical lines hide, copy stacks. Confirm the crossing metaphor still lands on mobile despite the lines being gone — the copy alone should carry.
8. **Accessibility.** All `cx-line` and `cx-cross` elements are `aria-hidden="true"` (pure decoration). Confirm screen readers still get a coherent reading of the shift closer / CTA now that the visual carries information.

---

## 6. Files to inspect first

| Priority | File | What to look at |
|---|---|---|
| 1 | `src/v2.html` | The 7 treatment sites. Search for `cx-` classes. |
| 2 | `src/styles/components/crossline.css` | All the new rules. Heavily commented — read the file-top overview first. |
| 3 | `src/index.html` | Baseline. Must remain untouched. |
| 4 | `src/styles/components/hero.css` | Wobble underline implementation — referenced by the "three voices" model. |
| 5 | `src/styles/main.css` | Confirms `crossline.css` is imported last (cascade order matters). |

---

## 7. What was explicitly NOT done

Kept out of scope so future-you doesn't hunt for them:

- **Horizontal capital-L Line band** between stuck and platform — considered, dropped when we pivoted to vertical-primary.
- **Post-Line chromatic shift** (pale-green wash on sections after the threshold) — considered, dropped because the boundary is no longer singular; vertical lines at multiple sites do that job.
- **Section-eyebrow waypoint numbering** (`01 SHIFT · 02 STUCK · …`) — considered, dropped because the copy uses boundary language, not journey language. Forcing a journey overlay would fight the copy.
- **Hero H1 or sub-head edit** — the H1 "Come deliver it" is strong. Only the eyebrow changed.
- **Logos / Partners grid changes** — three-way splits don't fit a binary threshold metaphor.
- **Restructuring the page order** — considered (move logos up to pair with stuck), rejected as high-risk for a shipped page.
