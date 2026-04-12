# OpenType Feature Context Rules

Concrete rules for WHEN and WHERE to activate OpenType features per brand. This file is the operational companion to Pattern 7 (Typography as Brand DNA) in `aesthetic-patterns.md`. Pattern 7 says "define which features to enable globally"; this file tells you exactly which elements get which features and what breaks if you get it wrong.

---

## Feature Reference

| Feature | Full Name | What It Does | Brands Using | CSS Syntax |
|---------|-----------|-------------|--------------|------------|
| `ss01` | Stylistic Set 1 | Alternate geometric letterforms (likely modified `a`, `g`, `l`) | Stripe | `font-feature-settings: "ss01"` |
| `cv01` | Character Variant 1 | Single-story lowercase `a` (replaces double-story default) | Linear | `font-feature-settings: "cv01"` |
| `ss03` | Stylistic Set 3 | Geometric adjustments to specific letterforms | Linear | `font-feature-settings: "ss03"` |
| `tnum` | Tabular Numbers | Fixed-width digits so columns of numbers align vertically | Stripe, Vercel | `font-feature-settings: "tnum"` |
| `liga` | Standard Ligatures | Connected/optimized glyph pairs (fi, fl, etc.) | Vercel | `font-feature-settings: "liga"` |

### Feature Interaction Rules

- `ss01` and `tnum` are **mutually exclusive** on Stripe. Never combine them on the same element.
- `cv01` and `ss03` are **always paired** on Linear. Never enable one without the other.
- `liga` is **universal** on Vercel -- every Geist element gets it, no exceptions.
- `tnum` is **context-triggered** -- it replaces the global feature set when numeric alignment matters, it does not stack on top of it.

---

## Per-Brand Rules

### Stripe -- sohne-var Features

**Font**: `sohne-var` (variable), fallback: `SF Pro Display`
**Mono**: `SourceCodePro`, fallback: `SFMono-Regular`

**Global rule**: `font-feature-settings: "ss01"` on ALL text rendered in sohne-var. This is non-negotiable. Without `ss01`, the page looks like generic sohne, not Stripe's sohne.

**Exception**: Tabular/financial data switches to `font-feature-settings: "tnum"` alone. The switch is total -- `ss01` is dropped, not stacked.

**Exception**: Code blocks use `SourceCodePro` with no `font-feature-settings`. The mono font carries its own personality.

**Exception**: Code Micro annotations (9px) use `SourceCodePro` with `"ss01"` -- this is the one place where the mono font inherits a stylistic set.

#### Context Matrix

| Context | Element Examples | Font | Features | Weight | Why |
|---------|-----------------|------|----------|--------|-----|
| Display headlines | Hero text, page titles | sohne-var | `"ss01"` | 300 | Brand identity -- alternate glyphs at maximum visibility |
| Section headings | Feature section titles | sohne-var | `"ss01"` | 300 | Consistent brand voice through heading hierarchy |
| Body text | Paragraphs, descriptions | sohne-var | `"ss01"` | 300 | Even body text carries the geometric alternates |
| Button labels | CTAs, action text | sohne-var | `"ss01"` | 400 | Alternate glyphs maintained; slightly heavier for UI affordance |
| Navigation links | Top nav, footer links | sohne-var | `"ss01"` | 400 | Brand consistency in navigation chrome |
| Captions / metadata | Timestamps, small labels | sohne-var | `"ss01"` | 300-400 | Alternate glyphs even at small sizes |
| Price displays | `$49.99/mo`, subscription tiers | sohne-var | `"tnum"` | 300-400 | Fixed-width digits for visual alignment; `ss01` DROPPED |
| Data tables | Revenue columns, metrics | sohne-var | `"tnum"` | 300-400 | Columns of numbers must align vertically |
| Chart axis labels | Y-axis values, data points | sohne-var | `"tnum"` | 300 | Small numeric labels need tabular alignment |
| Financial badges | Success/status with numbers | sohne-var | `"tnum"` | 300 | Numbers in badges align with surrounding data |
| Code blocks | API examples, syntax | SourceCodePro | none | 500 | Mono font has its own character; no feature override needed |
| Code bold | Keywords, emphasis in code | SourceCodePro | none | 700 | Bold variant of mono; features inherited from font design |
| Code labels | Technical labels (uppercase) | SourceCodePro | uppercase | 500 | Text-transform handles casing; no OT features |
| Code micro | Tiny annotations | SourceCodePro | `"ss01"` | 500 | Rare exception: mono + ss01 at smallest sizes |

#### CSS Implementation

```css
/* Global: every sohne-var element */
body {
  font-family: sohne-var, "SF Pro Display", sans-serif;
  font-feature-settings: "ss01";
}

/* Tabular data override -- REPLACES ss01, does not add to it */
.price,
.metric,
.table-cell-numeric,
.chart-label,
[data-numeric] {
  font-feature-settings: "tnum";
}

/* Code blocks -- different font family, no features */
code, pre, .code-block {
  font-family: SourceCodePro, SFMono-Regular, monospace;
  font-feature-settings: normal;
}
```

#### Decision Heuristic

Ask: "Is this element showing a number that needs to align with other numbers?" If yes, use `"tnum"`. For everything else in sohne-var, use `"ss01"`. If the element uses SourceCodePro, use no features (except the rare 9px micro annotation case).

---

### Linear -- Inter Variable Features

**Font**: `Inter Variable`, fallback: `SF Pro Display, -apple-system, system-ui, Segoe UI, Roboto, Oxygen, Ubuntu, Cantarell, Open Sans, Helvetica Neue`
**Mono**: `Berkeley Mono`, fallback: `ui-monospace, SF Mono, Menlo`

**Global rule**: `font-feature-settings: "cv01", "ss03"` on ALL text rendered in Inter Variable. These two features are inseparable -- they work as a unit to transform Inter into "Linear's Inter."

- `cv01` replaces the double-story `a` with a single-story variant (cleaner, more geometric)
- `ss03` adjusts additional letterforms for geometric consistency

**No exceptions for Inter text.** Every Inter element gets both features. There is no context where Inter runs without `cv01` + `ss03` on a Linear-styled page.

**Mono exception**: `Berkeley Mono` uses no `font-feature-settings`. It carries its own personality.

**No `tnum` usage detected.** Linear does not appear to use tabular numbers as a separate feature context. Numeric alignment is handled through layout (monospace or fixed-width containers) rather than OpenType switching.

#### Context Matrix

| Context | Element Examples | Font | Features | Weight | Why |
|---------|-----------------|------|----------|--------|-----|
| Display headlines | Hero text (72px, 64px, 48px) | Inter Variable | `"cv01", "ss03"` | 510 | Maximum brand visibility with signature weight |
| Section headings | Major section titles (32px) | Inter Variable | `"cv01", "ss03"` | 400 | Geometric alternates at heading scale |
| Sub-headings | Feature titles (20px) | Inter Variable | `"cv01", "ss03"` | 590 | Strong emphasis, still carrying brand glyphs |
| Body text | Paragraphs, descriptions | Inter Variable | `"cv01", "ss03"` | 400 | Reading text with brand-consistent letterforms |
| UI labels | Navigation, button text | Inter Variable | `"cv01", "ss03"` | 510 | Signature weight on functional text |
| Emphasized body | Strong body content | Inter Variable | `"cv01", "ss03"` | 590 | Semibold emphasis, features unchanged |
| De-emphasized body | Light supporting text | Inter Variable | `"cv01", "ss03"` | 300 | Even light text keeps the brand glyphs |
| Captions / metadata | Timestamps, small labels | Inter Variable | `"cv01", "ss03"` | 400-510 | Features never dropped at small sizes |
| Badge text | Status pills, tags | Inter Variable | `"cv01", "ss03"` | 510 | Consistent even in micro-UI |
| Tiny / overline | 10px uppercase labels | Inter Variable | `"cv01", "ss03"` | 400-510 | Features maintained at smallest sizes |
| Code blocks | API examples, syntax | Berkeley Mono | none | 400 | Mono font handles its own aesthetic |
| Code labels | Technical metadata | Berkeley Mono | none | 400 | No feature override on mono |

#### CSS Implementation

```css
/* Global: every Inter element */
body {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
}

/* Code blocks -- different font family, no features */
code, pre, .code-block {
  font-family: "Berkeley Mono", ui-monospace, "SF Mono", Menlo, monospace;
  font-feature-settings: normal;
}
```

#### Decision Heuristic

If the element uses Inter Variable, it gets `"cv01", "ss03"`. No exceptions, no overrides, no context switching. The only font-feature-settings change happens when you switch to Berkeley Mono (which gets `normal`). This is the simplest OpenType strategy of the four brands -- one rule, universally applied.

---

### Vercel -- Geist Features

**Font**: `Geist`, fallback: `Arial, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol`
**Mono**: `Geist Mono`, fallback: `ui-monospace, SFMono-Regular, Roboto Mono, Menlo, Monaco, Liberation Mono, DejaVu Sans Mono, Courier New`

**Global rule**: `font-feature-settings: "liga"` on ALL Geist text (both Sans and Mono). Ligatures are structural, not decorative -- they create tighter, more efficient glyph combinations that reinforce the "minified" aesthetic.

**Numeric override**: Specific caption/metric contexts use `"tnum"` for tabular number alignment. Unlike Stripe, Vercel's `tnum` usage is narrower -- it appears on Geist Mono captions and metric displays, not broadly across all numeric content.

**Mono rule**: Geist Mono also enables `"liga"`. Both Geist variants share the ligature feature. Geist Mono additionally uses `"tnum"` in specific technical label contexts.

#### Context Matrix

| Context | Element Examples | Font | Features | Weight | Why |
|---------|-----------------|------|----------|--------|-----|
| Display headlines | Hero text (48px) | Geist | `"liga"` | 600 | Ligatures at maximum size create tight display blocks |
| Section headings | Feature titles (40px, 32px) | Geist | `"liga"` | 600 | Structural ligatures maintain compression |
| Sub-headings | Card titles (24px) | Geist | `"liga"` | 500-600 | Ligatures active through heading hierarchy |
| Body text | Paragraphs, descriptions | Geist | `"liga"` | 400 | Even reading text benefits from tighter glyph pairs |
| Button labels | CTAs, action text | Geist | `"liga"` | 500 | Ligatures on compact UI text |
| Navigation links | Top nav, footer | Geist | `"liga"` | 500 | Consistent ligature treatment across chrome |
| Captions / metadata | Tags, timestamps | Geist | `"liga"` | 400-500 | Features maintained at small sizes |
| Metric displays | "10x faster", large numbers | Geist | `"liga"` | 600 | Display-size numbers with ligatures |
| Price / aligned numbers | Subscription tiers, data | Geist | `"tnum"` | 400-500 | Tabular alignment; ligatures implied by browser |
| Code blocks | Terminal output, syntax | Geist Mono | `"liga"` | 400 | Mono ligatures (e.g., `=>`, `!=`, `>=`) |
| Code labels | Technical labels (uppercase) | Geist Mono | `"liga"` | 500 | Uppercase mono with ligature support |
| Code captions | Metadata in code contexts | Geist Mono | `"tnum"` | 500 | Tabular numbers in technical captions |
| Micro badges | Tiny 7px uppercase labels | Geist | `"liga"` | 700 | Even at micro size, ligatures apply |
| Workflow labels | Develop/Preview/Ship | Geist Mono | `"liga"` | varies | Pipeline labels use mono + ligatures |

#### CSS Implementation

```css
/* Global: all Geist text */
body {
  font-family: Geist, Arial, sans-serif;
  font-feature-settings: "liga";
}

/* Tabular numeric contexts */
.metric-value,
.price,
.table-cell-numeric,
.code-caption-numeric {
  font-feature-settings: "tnum";
}

/* Geist Mono -- also gets ligatures */
code, pre, .code-block, .mono-label {
  font-family: "Geist Mono", ui-monospace, SFMono-Regular, monospace;
  font-feature-settings: "liga";
}

/* Geist Mono in tabular contexts */
.code-metric, .mono-numeric {
  font-family: "Geist Mono", ui-monospace, SFMono-Regular, monospace;
  font-feature-settings: "tnum";
}
```

#### Decision Heuristic

Default is `"liga"` on everything -- both Geist Sans and Geist Mono. Switch to `"tnum"` only when numbers must align in columns or when displaying financial/metric data in technical captions. Unlike Stripe where the switch is dramatic (ss01 dropped entirely), Vercel's switch is narrower because `liga` has less visual impact than `ss01` -- the browser may even keep ligatures active alongside `tnum` depending on rendering.

---

### Claude -- Anthropic Font Family

**Font**: `Anthropic Serif` (headlines), `Anthropic Sans` (body/UI), fallback: `Georgia` (serif), `Arial` (sans)
**Mono**: `Anthropic Mono`, fallback: `Arial`

**OpenType strategy**: Claude uses NO OpenType feature-settings. The brand's typographic identity comes from a completely different mechanism: a custom font family split by function (serif for content authority, sans for UI utility) rather than OpenType feature activation on a single typeface.

This is a fundamentally different approach. Stripe, Linear, and Vercel each take one font and transform it through OpenType features. Claude takes three related fonts and assigns them by role.

#### Font Selection Rules (replaces OpenType context matrix)

| Context | Element Examples | Font Family | Weight | Why |
|---------|-----------------|-------------|--------|-----|
| Display headlines | Hero text (64px) | Anthropic Serif | 500 | Serif = authority, gravitas, book-title presence |
| Section headings | Feature titles (52px, 36px) | Anthropic Serif | 500 | Consistent serif voice through heading hierarchy |
| Sub-headings | Card titles (32px, 25px) | Anthropic Serif | 500 | Single weight maintains "one author" consistency |
| Feature titles | Small headings (20px) | Anthropic Serif | 500 | Serif down to smallest heading level |
| Body serif | Editorial passages (17px) | Anthropic Serif | 400 | Long-form reading in serif for literary tone |
| Body large | Intro paragraphs (20px) | Anthropic Sans | 400 | Sans for functional reading; serif reserved for editorial |
| Body standard | Paragraphs (16px) | Anthropic Sans | 400-500 | Default UI body text in sans |
| Navigation | Top nav links (17px) | Anthropic Sans | 400-500 | Sans for UI affordance |
| Button labels | CTAs, actions | Anthropic Sans | 400-500 | Sans for interaction elements |
| Captions | Metadata, descriptions (14px) | Anthropic Sans | 400 | Small functional text in sans |
| Labels / overlines | Badges, tiny text (10-12px) | Anthropic Sans | 400-500 | Sans at micro sizes with letter-spacing |
| Code / terminal | Inline code, examples (15px) | Anthropic Mono | 400 | Mono strictly for code content |

#### CSS Implementation

```css
/* No font-feature-settings needed -- identity comes from font selection */

/* Serif: all headlines and editorial content */
h1, h2, h3, h4, h5, h6,
.display, .heading, .editorial-body {
  font-family: "Anthropic Serif", Georgia, serif;
  font-weight: 500; /* single weight for all serif */
}

/* Sans: UI, body, navigation */
body, p, nav, button, label, .caption {
  font-family: "Anthropic Sans", Arial, sans-serif;
}

/* Mono: code only */
code, pre, .code-block {
  font-family: "Anthropic Mono", Arial, monospace;
}
```

#### Decision Heuristic

Ask: "Is this content or UI?" Content headlines and editorial passages get Anthropic Serif at weight 500. Everything functional (navigation, buttons, body text, labels) gets Anthropic Sans. Code gets Anthropic Mono. No OpenType features are involved -- the brand voice comes from font family selection, not feature toggling.

---

## Cross-Brand Patterns

These patterns hold across all four brands and represent principles, not accidents.

### Universal Rules

1. **`tnum` is universal for numeric alignment.** Every brand that displays tabular data (Stripe, Vercel) uses `tnum` in that context. If you are showing numbers in columns, prices in a grid, or metrics side by side, activate `tnum`. This is not brand-specific -- it is a typography fundamental.

2. **Display-text features are mandatory, not decorative.** Stripe without `ss01`, Linear without `cv01`+`ss03`, Vercel without `liga` -- these are not the same brands. The features are identity-level, not enhancement-level. Treat them as non-negotiable as the font choice itself.

3. **Code blocks always use a dedicated mono font with minimal or no feature customization.** Stripe uses SourceCodePro, Linear uses Berkeley Mono, Vercel uses Geist Mono, Claude uses Anthropic Mono. The mono font carries its own design personality. Do not project the sans/serif font's OpenType features onto it (exception: Vercel's `liga` on Geist Mono, because both fonts are from the same family and share ligature design).

4. **Feature switching is total replacement, not accumulation.** When Stripe switches from `ss01` to `tnum`, it replaces the entire `font-feature-settings` value. CSS does not merge feature settings -- `font-feature-settings: "tnum"` on a child overrides `font-feature-settings: "ss01"` on the parent. This is the correct behavior; do not try to combine them with `"ss01", "tnum"`.

5. **Global features are set on `body` or the root element.** All four brands declare their OpenType features at the highest level and let inheritance handle propagation. Context-specific overrides (like `tnum` for tables) are applied on the specific elements that need them.

### The Three OpenType Strategies

| Strategy | Brands | How Identity Is Built |
|----------|--------|----------------------|
| **Feature transformation** | Stripe (`ss01`), Linear (`cv01`+`ss03`) | Take a known typeface, activate alternate glyphs to create a distinct variant |
| **Structural optimization** | Vercel (`liga`) | Enable ligatures that tighten glyph connections, reinforcing the compressed aesthetic |
| **Font family selection** | Claude (no features) | Use separate font families for different roles; identity comes from the serif/sans split, not from feature toggles |

---

## Anti-Patterns

### Never Do These

1. **NEVER combine `ss01` + `tnum` on the same element (Stripe).** CSS `font-feature-settings` is not additive across declarations. Setting `"ss01", "tnum"` simultaneously is not how Stripe uses these features -- they are context-switched, never stacked. If you see both on one element, the design is wrong.

2. **NEVER apply `cv01` without `ss03` on Linear.** These features are a designed pair. `cv01` alone gives you a single-story `a` but leaves other letterforms in their default geometric state, creating an inconsistent hybrid. Always declare both: `"cv01", "ss03"`.

3. **NEVER skip OpenType features because "they're subtle."** The difference between Inter and Linear's Inter, or sohne and Stripe's sohne, IS the feature set. Omitting features produces a generic-looking page that uses the right font but has the wrong voice. Test by toggling features off -- the shift is visible to a trained eye and subconsciously felt by everyone.

4. **NEVER apply OpenType features from one brand to another brand's font.** `ss01` is specific to sohne-var's glyph alternates. Applying `ss01` to Inter or Geist may activate completely different (or no) alternates. Feature sets are font-specific, not universal.

5. **NEVER use `font-feature-settings` on elements using a mono font (unless the brand explicitly does).** Only Vercel applies `liga` to Geist Mono, and only because both Geist variants are designed as a system with shared ligature tables. SourceCodePro and Berkeley Mono should run with `font-feature-settings: normal` or inherit nothing.

6. **NEVER add `tnum` to all numbers globally.** Tabular numbers have fixed widths, which can create awkward spacing in running text. "The year 2024 saw 13% growth" should use proportional (default) numbers. Only activate `tnum` when vertical alignment matters: tables, price columns, metric dashboards.

7. **NEVER declare `font-feature-settings: "liga"` and assume it enables ligatures on all fonts.** Ligatures require the font to contain ligature tables. Geist has them by design. If your fallback font (Arial, system-ui) does not have ligature tables, the declaration is silently ignored. This is correct behavior -- do not add fallback handling.

8. **NEVER use `font-variant-numeric: tabular-nums` AND `font-feature-settings: "tnum"` on the same element.** They do the same thing. `font-feature-settings` overrides `font-variant` when both are present. Pick one approach and be consistent. `font-feature-settings` is the pattern all four brands use.

---

## Implementation Checklist

When implementing a brand's typography:

- [ ] Set global `font-feature-settings` on `body` or root element
- [ ] Verify the feature string matches the brand exactly (order matters in some renderers)
- [ ] Create a CSS class or utility for numeric/tabular overrides
- [ ] Verify that code blocks use the correct mono font with correct (or no) feature settings
- [ ] Test feature rendering in target browsers (Safari, Chrome, Firefox handle OT features differently at edge cases)
- [ ] Inspect with browser DevTools > Computed > font-feature-settings to confirm inheritance is working
- [ ] Test `tnum` alignment by placing numbers in a column and checking vertical digit alignment
- [ ] Visually compare your implementation against the brand reference with features toggled on and off

---

## Quick Reference Card

```
Stripe:    body { font-feature-settings: "ss01" }
           .numeric { font-feature-settings: "tnum" }
           code { font-feature-settings: normal }

Linear:    body { font-feature-settings: "cv01", "ss03" }
           code { font-feature-settings: normal }

Vercel:    body { font-feature-settings: "liga" }
           .numeric { font-feature-settings: "tnum" }
           code { font-feature-settings: "liga" }

Claude:    /* No font-feature-settings -- identity via font-family selection */
           h1-h6 { font-family: "Anthropic Serif" }
           body   { font-family: "Anthropic Sans" }
           code   { font-family: "Anthropic Mono" }
```
