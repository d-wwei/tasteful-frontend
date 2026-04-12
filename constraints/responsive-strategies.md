# Responsive Collapsing Strategies

Exact per-component, per-brand rules for what changes at each breakpoint transition. All values are literal px/rem extracted from the brand DESIGN.md files.

---

## Breakpoint Definitions

| Brand   | Small Mobile   | Mobile         | Large Mobile   | Tablet         | Desktop Small  | Desktop        | Large Desktop  |
|---------|----------------|----------------|----------------|----------------|----------------|----------------|----------------|
| Claude  | <479px         | 479-640px      | 640-767px      | 768-991px      | --             | 992px+         | --             |
| Stripe  | --             | <640px         | --             | 640-1024px     | --             | 1024-1280px    | >1280px        |
| Linear  | <600px         | 600-640px      | --             | 640-768px      | 768-1024px     | 1024-1280px    | >1280px        |
| Vercel  | <400px         | 400-600px      | --             | 600-768px / 768-1024px | 1024-1200px | 1200-1400px | >1400px        |

### Canonical Mapping (for cross-brand work)

When building multi-brand-compatible layouts, use these unified breakpoints as approximations:

| Canonical Name | Width         | Claude maps to     | Stripe maps to | Linear maps to   | Vercel maps to     |
|----------------|---------------|--------------------|----------------|------------------|--------------------|
| Mobile         | <640px        | Small + Mobile     | Mobile         | Mobile Small + Mobile | Mobile Small + Mobile |
| Tablet         | 640-1024px    | Large Mobile + Tablet | Tablet      | Tablet + Desktop Small | Tablet Small + Tablet |
| Desktop        | 1024-1280px   | Desktop            | Desktop        | Desktop          | Desktop Small + Desktop |
| Wide           | >1280px       | Desktop (same)     | Large Desktop  | Large Desktop    | Large Desktop      |

---

## Per-Component Collapsing Rules

### Hero Section

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Wide -> Desktop** | No change (64px Anthropic Serif/500, lh 1.10) | 56px sohne-var/300 -> no change at 1280px; content centers with tighter margins | 72px Inter Variable/510 -> no change at 1280px; generous margins collapse | 48px Geist/600 -> no change at 1400px; margins reduce |
| **Desktop -> Tablet** | Hero headline 64px -> 36px Anthropic Serif/500; subtitle 20px -> 18px; layout remains centered single-column; section padding 80-120px -> ~60px | Hero headline 56px -> 48px sohne-var/300; letter-spacing -1.4px -> -0.96px; padding reduces from 64px+ -> ~48px; subtitle 18px maintained | Hero headline 72px -> 48px Inter Variable/510; letter-spacing -1.584px -> -1.056px; vertical padding 80px+ -> ~60px; subtitle 18px -> 16px | Hero headline 48px maintained through tablet; letter-spacing -2.4px maintained; vertical padding 80-120px -> ~60px; subtitle 20px maintained |
| **Tablet -> Mobile** | Headline 36px -> ~25px Anthropic Serif/500; lh 1.10 -> 1.20; illustrations scale down proportionally; section padding ~60px -> ~40px; CTA button becomes full-width | Headline 48px -> 32px sohne-var/300; letter-spacing -0.96px -> -0.64px; section spacing 48px -> 40px; single-column stack; gradient decorations simplify | Headline 48px -> 32px Inter Variable/510; letter-spacing -1.056px -> -0.704px; section spacing 60px -> 48px; hero visuals simplify (fewer floating UI elements) | Headline scales down proportionally; letter-spacing reduces proportionally; section spacing 60px -> 48px; hero gradient softens/simplifies |

### Navigation

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Wide -> Desktop** | Full horizontal nav; sticky top; warm background; Anthropic Sans 17px/400-500; Terracotta CTA button; border 1px solid #f0eee6 (light) or #30302e (dark) | Full horizontal nav; sticky with backdrop blur(12px); sohne-var 14px/400; purple CTA right-aligned; 6px radius container | Full horizontal nav; dark sticky header on #0f1011; Inter Variable 13-14px/510; brand indigo CTA; bottom border rgba(255,255,255,0.05) | Full horizontal nav; white sticky; Geist 14px/500; dark pill CTA; shadow-border bottom |
| **Desktop -> Tablet** | Nav condenses; fewer visible links; CTA remains visible; padding reduces | Nav links begin hiding; core links + CTA remain; hamburger toggle appears at 1024px; 6px radius toggle button | Nav collapses to hamburger at 768px; command palette (Cmd+K) remains accessible | Nav begins condensing; product dropdowns collapse; hamburger appears |
| **Tablet -> Mobile** | Full hamburger collapse; logo + hamburger icon only; touch-optimized spacing; menu overlay on tap | Full hamburger menu; mobile toggle with 6px radius; stacked vertical menu on open | Full hamburger collapse; dark slide-out or overlay menu; search trigger prominent | Full hamburger collapse; logo + hamburger; stacked mobile menu; mobile menu toggle uses 50% radius circular button |

### Button

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | No size change; padding stays asymmetric (0px 12px 0px 8px) or balanced (8px 16px); radius 8-12px maintained | No change; padding 8px 16px; radius 4px; font 16px/400 maintained | No change; padding 8px 16px; radius 6px maintained | No change; padding 8px 16px; radius 6px maintained |
| **Tablet -> Mobile** | CTA buttons become full-width (width: 100%); button groups stack vertically with 8px gap; min-height 44px for touch targets; padding maintained | CTA buttons become full-width; button pairs stack vertically; padding 8px 16px maintained; radius 4px maintained; min-height 44px | CTA becomes full-width; ghost/subtle buttons stack; radius 6px maintained; padding maintained | CTA becomes full-width; button pairs stack vertically; increased vertical padding to 12px 16px; radius 6px maintained |

### Card Grid

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Wide -> Desktop** | 3-column grid (model cards); gap ~24px; card bg Ivory (#faf9f5); border 1px solid #f0eee6; radius 8px standard / 16px featured | 3-column feature grid; gap ~24px; card bg #ffffff; border 1px solid #e5edf5; radius 5-6px; blue-tinted shadow | 3-column feature grid; gap ~24px; card bg rgba(255,255,255,0.02); border 1px solid rgba(255,255,255,0.08); radius 8px | 3-column feature grid; gap ~32px; card bg #ffffff; shadow-border rgba(0,0,0,0.08) 0px 0px 0px 1px; radius 8px |
| **Desktop -> Tablet** | 3-col -> 2-col grid; card padding 24-32px maintained; gap reduces to ~16px; card title 25px Anthropic Serif maintained | 3-col -> 2-col grid; card internal padding maintained; gap reduces to ~20px; card shadows maintained | 3-col -> 2-col grid; card padding maintained; gap reduces to ~16px; screenshot cards may stack | 3-col -> 2-col grid; card padding maintained; gap reduces to ~24px; shadow stack maintained |
| **Tablet -> Mobile** | 2-col -> 1-col stack; cards span full width; gap 16px between cards; internal padding 24-32px maintained; card title may reduce from 25px -> 20px | 2-col -> 1-col stack; full-width cards; gap ~16px; card shadow maintained; internal padding maintained | 2-col -> 1-col stack; full-width cards; gap ~16px; translucent backgrounds maintained; padding reduces slightly | 2-col -> 1-col stack; full-width cards; gap ~16px; shadow-borders maintained; image cards maintain 12px top radius |

### Table / Data Display

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | Model comparison 3-col -> 2-col stacked; border-top separators (1px solid #e8e6dc) maintained; cell padding maintained | Financial data tables maintain structure; columns may reduce; font stays SourceCodePro 12px with "tnum" | Changelog timeline maintains single-column through all sizes; issue list tables may truncate columns | Metric cards maintain shadow-bordered layout; data may reflow to 2-col |
| **Tablet -> Mobile** | Model cards stack to single column with full-width cards; vertical dividers become horizontal separators | Tables get horizontal scroll (overflow-x: auto); container padding reduces; table font maintained at 12px SourceCodePro; "tnum" preserved | Timeline stays single-column; table data truncates or scrolls horizontally; monospace Berkeley Mono 14px maintained | Tables/data cards stack to single column; metric numbers scale down from 48px -> 32px Geist/600; horizontal scroll for wide data |

### Footer

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | Multi-column link sections condense; padding reduces proportionally; editorial rhythm maintained | Multi-column -> fewer columns; dark brand section (#1c1e54) maintained full-width; internal padding reduces | Multi-column -> 2-column; dark background maintained; link text 13px Inter Variable/510 maintained | Multi-column -> fewer columns; full-width borders maintained; link text 14px Geist/500 maintained |
| **Tablet -> Mobile** | Stacked single column; generous vertical spacing between link groups; section padding ~40px; Anthropic Sans 14-16px | Stacked single column; dark background maintained; vertical spacing ~32px between groups; text 14px sohne-var | Stacked single column; dark background maintained; section spacing ~32px; links stack vertically | Stacked single column; border-bottom 1px solid #171717 maintained; section spacing ~32px |

### Feature Section (Multi-Column Content)

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | 2-3 col -> 2-col; section heading 52px -> 40px Anthropic Serif/500; body text 17px maintained; dark/light section alternation maintained full-width; section vertical padding 80-120px -> ~60px | 2-3 col -> 2-col; section heading 32px sohne-var/300 maintained; letter-spacing -0.64px maintained; dark brand sections maintain full-width; padding reduces | 2-3 col -> 2-col; section heading 48px -> 32px Inter Variable/510; letter-spacing adjusts -1.056px -> -0.704px; section isolation via dark background maintained | 2-3 col -> 2-col; section heading 40px Geist/600 maintained; letter-spacing -2.4px maintained; section borders maintained |
| **Tablet -> Mobile** | All multi-col -> 1-col stack; section heading 40px -> ~32px; sub-heading 32px -> 25px; body large 20px -> 17px; illustrations scale proportionally; dark/light alternation preserved | All multi-col -> 1-col stack; section heading 32px maintained; body 16px maintained; section spacing 48px -> 40px; dark sections reduce internal padding | All multi-col -> 1-col stack; section heading 32px maintained; body 15px maintained; section spacing 60px -> 48px; product screenshots simplify | All multi-col -> 1-col stack; section heading 40px -> 32px; letter-spacing -2.4px -> -1.28px; section spacing 60px -> 48px; trust bar logos -> horizontal scroll |

### Form / Input

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | Inputs maintain padding (1.6px 12px); radius 12px; focus ring Focus Blue (#3898ec); multi-column forms -> 2-col; field labels Anthropic Sans 14px maintained | Inputs maintain 4px radius; border 1px solid #e5edf5; focus 1px solid #533afd; label 14px sohne-var; multi-col forms -> 2-col | Inputs maintain rgba(255,255,255,0.02) bg; border rgba(255,255,255,0.08); padding 12px 14px; radius 6px; multi-col -> 2-col | Inputs maintain shadow-border technique; focus outline 2px solid hsla(212,100%,48%,1); multi-col -> 2-col |
| **Tablet -> Mobile** | All forms single-column; full-width inputs; vertical padding increases to ensure 44px touch targets; field spacing ~16px; labels stack above inputs | All forms single-column; full-width inputs; padding 8px 16px maintained; min-height 44px; labels stack above fields | All forms single-column; full-width inputs; padding 12px 14px maintained; min-height 44px | All forms single-column; full-width inputs; min-height 44px touch targets; focus ring maintained |

### Image / Media

| Breakpoint Transition | Claude | Stripe | Linear | Vercel |
|-----------------------|--------|--------|--------|--------|
| **Desktop -> Tablet** | Product screenshots scale proportionally within rounded containers (16-32px radius); video embeds maintain 16:9; no art direction changes | Dashboard screenshots maintain blue-tinted shadow at all sizes; code blocks maintain SourceCodePro; card images keep 4-6px radius | Screenshots maintain border treatment (1px solid rgba(255,255,255,0.08)); top-rounded 12px; shadow rgba(0,0,0,0.4) 0px 2px 4px maintained | Screenshots maintain 1px solid #ebebeb border; top-rounded 12px 12px 0px 0px; shadow-borders maintained |
| **Tablet -> Mobile** | Illustrations maintain aspect ratios, scale to container width; screenshots remain rounded; no breakpoint-specific art direction | Hero gradient decorations simplify; screenshots scale to full width; blue-tinted shadow maintained but may reduce blur values; code blocks may scroll horizontally | Hero visuals simplify (fewer floating UI elements); screenshots maintain consistent radius; dark background ensures natural blending at any size | Hero gradient softens/simplifies; screenshots use responsive images; full-width sections maintain edge-to-edge; product screenshots scale proportionally |

---

## Typography Scale Collapsing (Exact px Values)

### Hero / Display Headline

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Wide (>1280px) | 64px / Anthropic Serif / 500 / lh 1.10 | 56px / sohne-var / 300 / lh 1.03 / ls -1.4px | 72px / Inter Variable / 510 / lh 1.00 / ls -1.584px | 48px / Geist / 600 / lh 1.00 / ls -2.4px to -2.88px |
| Desktop (1024px) | 64px (unchanged) | 56px (unchanged) | 72px (unchanged) | 48px (unchanged) |
| Tablet (768px) | 36px / lh 1.30 | 48px / lh 1.15 / ls -0.96px | 48px / lh 1.00 / ls -1.056px | 48px (maintained) |
| Mobile (<640px) | ~25px / lh 1.20 | 32px / lh 1.10 / ls -0.64px | 32px / lh 1.13 / ls -0.704px | Scales proportionally (est. 36-40px) |

### Section Heading

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | 52px / Anthropic Serif / 500 / lh 1.20 | 32px / sohne-var / 300 / lh 1.10 / ls -0.64px | 48px / Inter Variable / 510 / lh 1.00 / ls -1.056px | 40px / Geist / 600 / lh 1.20 / ls -2.4px |
| Tablet | ~40px / lh 1.20 | 32px (maintained) | 32px / lh 1.13 / ls -0.704px | 40px (maintained) |
| Mobile | ~32px / lh 1.20 | 32px (maintained) | 32px (maintained) | 32px / lh 1.25 / ls -1.28px |

### Sub-heading

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | 32px / Anthropic Serif / 500 / lh 1.10 | 26px / sohne-var / 300 / lh 1.12 / ls -0.26px | 24px / Inter Variable / 400 / lh 1.33 / ls -0.288px | 24px / Geist / 600 / lh 1.33 / ls -0.96px |
| Tablet | 32px (maintained) | 26px (maintained) | 24px (maintained) | 24px (maintained) |
| Mobile | ~25px / lh 1.20 | 22px / lh 1.10 / ls -0.22px | 20px / weight 590 / lh 1.33 / ls -0.24px | 20px (est.) / lh 1.33 |

### Body Text

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | 17px / Anthropic Sans / 400 / lh 1.60 | 16px / sohne-var / 300-400 / lh 1.40 | 16px / Inter Variable / 400 / lh 1.50 | 16px / Geist / 400 / lh 1.50 |
| Tablet | 17px (maintained) | 16px (maintained) | 16px (maintained) | 16px (maintained) |
| Mobile | 16px / lh 1.60 (min floor) | 16px (maintained) | 15px / lh 1.60 / ls -0.165px | 16px (maintained) |

---

## Spacing Collapsing (Exact px Values)

### Section Vertical Padding

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | 80-120px | 64px+ | 80px+ | 80-120px |
| Tablet | ~60px | ~48px | ~60px | ~60px |
| Mobile | ~40px | ~40px | ~48px | ~48px |

### Card Internal Padding

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | 24-32px | 24-32px | 24-32px | 24-32px |
| Tablet | 24-32px (maintained) | 24-32px (maintained) | 24-32px (maintained) | 24-32px (maintained) |
| Mobile | 24-32px (maintained; never below 16px) | 20-24px | 20-24px | 20-24px |

### Grid Gap

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | ~24px | ~24px | ~24px | ~32px |
| Tablet | ~16px | ~20px | ~16px | ~24px |
| Mobile | ~16px (stacked) | ~16px (stacked) | ~16px (stacked) | ~16px (stacked) |

### Page Horizontal Margin

| Breakpoint | Claude | Stripe | Linear | Vercel |
|------------|--------|--------|--------|--------|
| Desktop+ | Container max ~1200px, centered | Container max ~1080px, centered | Container max ~1200px, centered | Container max ~1200px, centered |
| Tablet | 32-40px side margins | 24-32px side margins | 24-32px side margins | 24-32px side margins |
| Mobile | 16-20px side margins | 16-20px side margins | 16-20px side margins | 16-20px side margins |

---

## Grid Column Collapsing

| Grid Layout | Desktop (>1024px) | Tablet (640-1024px) | Mobile (<640px) |
|-------------|-------------------|---------------------|-----------------|
| 3-column card grid | 3 columns | 2 columns | 1 column (stacked) |
| 2-column feature | 2 columns | 2 columns (tighter) | 1 column (stacked) |
| 4-column footer links | 4 columns | 2 columns | 1 column (stacked) |
| Hero with side content | Side-by-side | Side-by-side (tighter) | Stacked, content first |

All four brands follow this identical grid collapse pattern. No brand maintains multi-column layouts below 640px.

---

## Universal Responsive Rules (All Brands Agree)

These rules are consistent across Claude, Stripe, Linear, and Vercel:

1. **Touch targets >= 44px on mobile** -- All brands enforce minimum 44x44px interactive areas on touch devices.
2. **Single-column forms on mobile** -- All multi-column form layouts collapse to single column below 640px.
3. **Full-width CTA buttons on mobile** -- Primary action buttons expand to 100% width below 640px.
4. **Button groups stack vertically on mobile** -- Side-by-side button pairs become vertically stacked.
5. **Hamburger navigation on mobile** -- All brands collapse horizontal navigation to a hamburger toggle below their respective tablet breakpoints.
6. **Body text never drops below 15-16px** -- No brand reduces standard body text below 15px on any breakpoint.
7. **Font weight is breakpoint-invariant** -- No brand changes font weights across breakpoints; only sizes and letter-spacing change.
8. **Card border-radius is breakpoint-invariant** -- Corner radii remain identical at all sizes.
9. **Shadow systems are breakpoint-invariant** -- Shadow stacks, ring-borders, and elevation treatments remain consistent across all breakpoints.
10. **3-col -> 2-col -> 1-col stacking** -- Every brand follows this progressive grid collapse.
11. **Section spacing reduces by ~40% on mobile** -- Desktop section gaps (80-120px) compress to 40-48px on mobile.
12. **Footer stacks to single column on mobile** -- Multi-column footers become stacked link groups.
13. **Code blocks may horizontally scroll** -- All brands allow overflow-x: auto for code and data tables on narrow viewports.
14. **Image aspect ratios are preserved** -- No brand crops or art-directs images differently per breakpoint; they scale proportionally.

---

## Brand-Specific Responsive Techniques

### Claude

- **Progressive serif headline scaling**: The most dramatic type reduction of any brand -- 64px -> 36px -> ~25px across three steps. The serif typeface demands larger size reductions because serif letterforms lose legibility faster at small sizes.
- **Dark/light section alternation preserved at all breakpoints**: The chapter-like page rhythm is never collapsed; dark and light sections both go full-width at every size.
- **Illustrations scale, never hide**: Organic hand-drawn illustrations maintain visibility at all breakpoints. They scale proportionally but are never removed or simplified.
- **Editorial line-height maintained on mobile**: Body text keeps 1.60 line-height even on mobile -- the literary reading experience is not sacrificed for density.
- **Asymmetric button padding preserved**: The icon-first asymmetric padding (0px 12px 0px 8px) is maintained at all sizes.
- **Warm color palette is breakpoint-invariant**: No cool-toned fallbacks or adjustments at any breakpoint.

### Stripe

- **Weight 300 maintained everywhere**: The signature light headline weight never increases on mobile, even as sizes reduce. This is unusual -- most brands increase weight on mobile for legibility.
- **Progressive letter-spacing relaxation with size**: As headlines reduce (56px -> 48px -> 32px), letter-spacing relaxes from -1.4px -> -0.96px -> -0.64px. The tracking is tied to the font size, not the breakpoint.
- **Blue-tinted shadows preserved on mobile**: The signature rgba(50,50,93,0.25) shadow system is maintained on all breakpoints. Shadow blur/offset values may reduce but the color tint remains.
- **Financial data tables scroll horizontally**: Unlike other content which stacks, data tables get overflow-x: auto rather than reflowing. This preserves data integrity.
- **Dark brand sections (#1c1e54) go full-width on all sizes**: Internal padding reduces but the immersive dark background always spans edge-to-edge.
- **Hero gradient decorations simplify on mobile**: Complex ruby-to-magenta gradient effects reduce in complexity but don't disappear.

### Linear

- **Dark-mode-native means no light/dark switching**: The responsive strategy never introduces light surfaces on mobile. The near-black canvas (#08090a) is constant.
- **Three-step hero scaling with proportional tracking**: 72px/-1.584px -> 48px/-1.056px -> 32px/-0.704px. Letter-spacing is mathematically proportional to size (~2.2% of font size).
- **Semi-transparent borders maintained everywhere**: The rgba(255,255,255,0.05-0.08) border system works identically at all breakpoints because it relies on opacity, not fixed colors.
- **Luminance stacking is breakpoint-invariant**: Surface elevation via background opacity (0.02 -> 0.04 -> 0.05) works at any viewport size.
- **Changelog stays single-column at all sizes**: The timeline layout is inherently responsive; it never needs grid collapse.
- **Command palette (Cmd+K) remains accessible on tablet+**: The search/command palette trigger persists even when nav collapses, ensuring power-user access on smaller screens.
- **Hero visuals shed floating UI elements on mobile**: Rather than uniformly scaling, hero product screenshots remove decorative floating panels to reduce visual complexity.

### Vercel

- **Most aggressive letter-spacing of any brand**: -2.4px to -2.88px at 48px display. This tracking is ~5% of font size, nearly 2x tighter than Linear and Stripe. On mobile, it relaxes to -1.28px at 32px.
- **Shadow-as-border technique is perfectly responsive**: The box-shadow 0px 0px 0px 1px approach never needs media query adjustments because it lives in the shadow layer, not the box model.
- **Gallery whitespace compresses proportionally**: The enormous desktop vertical padding (80-120px) reduces but remains generous relative to other brands, even on mobile (~48px).
- **Trust bar transforms from grid to horizontal scroll**: Logo grids become horizontally scrollable carousels on mobile, avoiding tall stacked layouts.
- **Workflow pipeline may reflow**: The Develop -> Preview -> Ship horizontal pipeline may stack vertically on mobile, with each step becoming a full-width card.
- **Inner #fafafa shadow ring maintained on mobile**: The card inner-glow effect from the shadow stack is preserved at all breakpoints -- it is fundamental to the Vercel card identity.
- **Section borders (1px solid #171717) are breakpoint-invariant**: The full-width dark divider lines persist at every size, providing consistent section separation in the otherwise monochrome layout.
- **Metric card numbers scale**: Large display numbers (48px Geist/600) reduce to ~32px on mobile while maintaining the heavy weight and tight tracking.

---

## Responsive Implementation Notes

### CSS Custom Properties Strategy

All four brands use a base-unit spacing system (8px). Responsive adjustments should use CSS custom properties scoped to media queries:

```
--section-gap: 80px;         /* Desktop+ */
--section-gap: 60px;         /* Tablet */
--section-gap: 40px;         /* Mobile */

--hero-font-size: 64px;      /* Claude Desktop */
--hero-font-size: 36px;      /* Claude Tablet */
--hero-font-size: 25px;      /* Claude Mobile */
```

### Container Width Behavior

| Brand   | Max Container | Behavior at Max |
|---------|---------------|-----------------|
| Claude  | ~1200px       | Centered, editorial pace |
| Stripe  | ~1080px       | Centered, precision margins |
| Linear  | ~1200px       | Centered, generous dark padding |
| Vercel  | ~1200px       | Centered, gallery emptiness |

Below max container width, all brands switch to percentage-based widths with fixed horizontal margins (16-40px depending on breakpoint).

### Font Size Floor Rule

No text in any brand goes below these minimums:

| Text Role     | Minimum Size |
|---------------|-------------|
| Body          | 15px        |
| Caption       | 12px        |
| Label         | 10px        |
| Micro/Badge   | 7px (Vercel only) / 9.6px (Claude) / 8px (Stripe) / 10px (Linear) |
| Code          | 12px        |

These minimums hold regardless of breakpoint.

---

## Advanced Responsive Patterns

Extended guidance on spatial systems, container queries, optical adjustments, input method detection, and responsive image strategy. These patterns complement the per-component collapsing rules above.

### 4pt Base Grid Rationale

All four reference brands use an 8px spatial unit, but the underlying grid is 4pt. Why 4pt instead of 8pt:

- 8pt systems are too coarse -- you frequently need 12px (1.5 base units) for padding inside compact UI elements. An 8pt-only system forces you to choose between 8px (too tight) and 16px (too loose).
- 4pt granularity provides: 4, 8, 12, 16, 20, 24, 32, 48, 64, 96px as the standard spacing scale.
- The most-used values (8, 16, 24, 32) are multiples of both 4 and 8, so 4pt compatibility comes free.
- 12px and 20px fill critical gaps that an 8pt-only scale misses -- these values appear frequently in component padding, icon margins, and label spacing.

**Design rule**: Define the spacing scale on a 4pt grid. The scale does not need to include every multiple of 4 -- skip values that would create ambiguous hierarchy (e.g., both 28 and 32 are too close to be meaningfully different). A practical scale: 4, 8, 12, 16, 24, 32, 48, 64, 96px.

### Container Queries Guide

Container queries allow components to adapt based on the size of their container rather than the viewport. This solves a fundamental limitation of media queries: a card in a narrow sidebar and the same card in a wide main area need different layouts, but they share the same viewport.

#### When to Use Container Queries

| Scenario | Why Container Queries Win |
|----------|--------------------------|
| **Sidebar vs. main area** | Same card component needs compact layout in sidebar, expanded layout in main content |
| **Resizable panels** | Dashboard widgets that resize when users drag panel dividers |
| **Embedded widgets** | Components used across different sites/contexts with varying container widths |
| **Design system components** | Truly portable components that respond to their allocation, not the page |

#### When Viewport Queries Are Still Correct

| Scenario | Why Viewport Queries Win |
|----------|--------------------------|
| **Page-level layout** | Overall page structure (sidebar visibility, column count) responds to viewport |
| **Navigation collapse** | Hamburger trigger at specific viewport widths |
| **Full-bleed sections** | Sections that span the entire viewport width |
| **Font size scaling** | `clamp()` functions that reference viewport width |

**Design rule**: Use viewport queries for page layout decisions. Use container queries for component layout decisions. Most projects need both.

#### Container Query Sizing Types

| Type | What It Measures | Use Case |
|------|-----------------|----------|
| `inline-size` | Width only (most common) | Cards, widgets, sidebar content |
| `size` | Width and height | Rarely needed -- most layouts respond to width only |

**Caution**: An element with `container-type: inline-size` establishes containment, which affects how its children resolve percentage widths and how paint is handled. Do not apply `container-type` to every element -- apply it to the structural containers that wrap adaptive components.

### Visual Optical Adjustment Rules

Mathematical alignment often looks wrong to the human eye. Optical alignment corrects for perceptual quirks.

#### Text Optical Alignment

Text at `margin-left: 0` appears slightly indented because the first letterform has built-in sidebearing (internal whitespace). For visually flush alignment with elements above or below, apply a small negative margin (approximately -0.05em) to optically align the text edge with the container edge.

This adjustment is most visible on:
- Headlines at large sizes (24px+) where the sidebearing gap is proportionally large
- Left-aligned text that sits above or below a hard-edged element (image, divider, card border)

#### Icon Optical Centering

Geometrically centered icons often look off-center because their visual weight is not evenly distributed:
- **Play/arrow icons**: Point toward the right -- shift the icon ~1-2px right to optically center
- **Search/magnifying glass**: Handle extends down-left -- shift ~1px up and right
- **Notification bell**: Top-heavy -- shift ~1px down

**Design rule**: Always verify icon centering visually, not mathematically. The goal is perceptual centering, which rarely matches mathematical centering for asymmetric shapes.

#### Circle vs. Square Sizing

A circle inscribed in a square appears smaller than the square, even at identical dimensions. To make a circular avatar appear the same visual size as a square icon, the circle needs to be ~12% larger.

### Touch Target vs. Visual Size

Interactive elements have two sizes: the visual size (what the user sees) and the touch target (the tappable area). These can and should differ.

| Element Type | Visual Size | Touch Target | Gap Needed |
|-------------|------------|-------------|------------|
| Icon button | 24x24px | 44x44px min | 10px invisible padding per side |
| Text link in dense UI | Determined by font size | 44px tall | Expand via line-height or padding |
| Close button | 16x16px | 44x44px min | 14px invisible padding per side |
| Checkbox/radio | 16-20px | 44x44px min | Include label in the target area |

**Technique**: Extend touch targets using padding, pseudo-elements (absolute-positioned `::before` with negative inset), or transparent background areas. The visual element stays small; the interactive area extends invisibly.

**Spacing consequence**: Touch targets of adjacent elements must not overlap. Minimum 8px gap between adjacent touch targets -- measured from target edge to target edge, not visual edge to visual edge.

### Responsive Image Strategy

#### Format Selection

| Format | Best For | Browser Support |
|--------|----------|----------------|
| **AVIF** | Photographs, complex images -- best compression | Modern browsers (Chrome, Firefox, Safari 16+) |
| **WebP** | Photographs, illustrations -- good compression | All modern browsers |
| **PNG** | UI elements, icons, screenshots with text | Universal |
| **SVG** | Icons, logos, simple illustrations | Universal (not for photos) |

Use `<picture>` with format fallback: AVIF first, WebP second, JPEG/PNG fallback.

#### Responsive `srcset` Strategy

For photographs and content images:
- Generate 3-5 sizes: 400w, 800w, 1200w, 1800w, 2400w
- Use `sizes` attribute to tell the browser the expected display width at each breakpoint
- Let the browser choose the optimal source based on viewport + pixel density

**Design rule**: Do not generate more than 5 sizes per image. The diminishing returns of additional sizes are not worth the build complexity and CDN storage.

#### Art Direction vs. Resolution Switching

- **Resolution switching** (different sizes of the same image): Use `srcset` with `w` descriptors
- **Art direction** (different crops or compositions): Use `<picture>` with `<source media="...">` for each breakpoint

Art direction is needed when:
- A wide hero image should become a taller, tighter crop on mobile
- A product grid image should shift from a full-body shot to a close-up on small screens
- Background images need different focal points at different aspect ratios

### Input Method Detection

Screen size does not reliably indicate input method. A laptop with touchscreen has a mouse AND touch. A tablet with a keyboard has touch AND keys. Use CSS feature queries to adapt:

| Query | Detects | Design Response |
|-------|---------|----------------|
| `@media (pointer: fine)` | Mouse, trackpad | Standard-sized interactive elements (36px+ buttons) |
| `@media (pointer: coarse)` | Touch, stylus | Enlarged interactive elements (44px+ buttons, 48dp Android) |
| `@media (hover: hover)` | Device supports hover | Enable hover states (tooltips on hover, hover previews) |
| `@media (hover: none)` | No hover capability | Replace hover interactions with tap/click alternatives |
| `@media (any-pointer: coarse)` | At least one input is touch | Ensure all interactions work with touch |

**Design rule**: Never rely on hover for functionality. Hover states are enhancements for devices that support them. All information revealed on hover must be accessible through tap/click on devices without hover support.
