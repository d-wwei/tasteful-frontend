# Typography Deep Knowledge

Design-layer guidance for typography decisions beyond basic token selection. This file covers web font loading strategies, OpenType features beyond the per-brand rules in `opentype-rules.md`, variable font design applications, fallback metrics, and text-wrapping refinements. For code-level implementation details, see `code-rules.md`.

---

## Web Font Loading Strategies

### The Layout Shift Problem

Web fonts load asynchronously. When the custom font arrives and replaces the fallback, text reflows -- users see content jump. The design decision is which trade-off to accept.

### `font-display` Strategy Selection

| Strategy | Behavior | Use When | Trade-off |
|----------|----------|----------|-----------|
| `swap` | Show fallback immediately, swap when font loads | Body text, UI labels -- content must be readable instantly | Layout shift on swap (FOUT visible) |
| `optional` | Show fallback; only swap if font loads within ~100ms | Performance-critical pages, above-the-fold text | Font may never appear on slow connections |
| `fallback` | Brief invisible period (~100ms), then fallback, swap within ~3s | Headlines where FOUT is jarring but content must appear quickly | Short blank flash, possible shift |
| `block` | Invisible text up to ~3s, then fallback | Icon fonts only -- never for readable text | Text invisible during load (FOIT) |

**Design-layer decision**: `swap` is the safe default for body text. `optional` is the performance-maximizing choice when you have well-matched fallback metrics. Never use `block` for text content -- invisible text is a worse experience than a font swap.

### Fallback Metrics Matching

The goal is to minimize layout shift by making the fallback font occupy the same space as the custom font. Four override properties control this:

- **size-adjust**: Scales the fallback to match the custom font's overall character width. If the custom font renders wider than Arial, increase this above 100%.
- **ascent-override**: Matches the height above the baseline. Affects line box height.
- **descent-override**: Matches the depth below the baseline. Affects line box height.
- **line-gap-override**: Matches extra spacing between lines built into the font.

**Design implication**: When these four values are calibrated correctly, swapping from fallback to custom font produces near-zero layout shift. The text occupies the same bounding box before and after the swap.

### The Fontaine Approach

Fontaine (github.com/unjs/fontaine) automates fallback metric calculation. It reads the custom font's metrics tables and generates the four override values for common system fonts (Arial, Times New Roman, etc.).

**When to use**: Any project using custom web fonts. The tool eliminates guesswork from fallback metric matching and integrates into build pipelines. The design benefit is predictable layout stability during font loading.

### Font Subsetting Strategies

Loading an entire font file when only a fraction of glyphs are used wastes bandwidth and delays rendering. Subsetting removes unused glyphs.

| Strategy | Scope | When to Use |
|----------|-------|-------------|
| **Latin-only subset** | ~100-200 glyphs | Single-language sites targeting Western audiences |
| **Unicode-range splitting** | Multiple small files per script | Multi-language sites -- browser downloads only the range it needs |
| **Feature-based subset** | Remove unused OpenType features | When you know exactly which features you activate (e.g., only `ss01` and `tnum`) |
| **Display-only subset** | Only glyphs used in headlines | Display fonts used for a limited set of text (hero, headings) |

**Design-layer rule**: Subset aggressively for display fonts (which render limited text) and conservatively for body fonts (which must handle user-generated content, names, edge-case characters). A display font subset can be as small as 10-20KB; a full-character body font may need 50-100KB.

---

## Variable Font Design Applications

Variable fonts contain multiple axes of variation in a single file. Beyond the obvious weight axis, several axes unlock design possibilities.

### Common Axes and Their Design Uses

| Axis | Tag | What It Controls | Design Application |
|------|-----|-----------------|-------------------|
| Weight | `wght` | Stroke thickness (100-900+) | Signature weights like 510 (Linear) that fall between conventional steps |
| Width | `wdth` | Character width (75-125%) | Condensed headlines on narrow containers without switching fonts |
| Optical Size | `opsz` | Detail level for size | Auto-adjusts stroke contrast and spacing for readability at small sizes vs. display elegance at large sizes |
| Italic | `ital` | Upright to italic | True italic forms (not just slanted) for emphasis in editorial contexts |
| Slant | `slnt` | Oblique angle | Subtle forward lean for dynamic feeling without full italic |
| Grade | `GRAD` | Stroke weight without changing glyph width | Hover/active states that feel heavier without causing layout reflow |

### Grade as Interaction Feedback

The `GRAD` (grade) axis is particularly valuable for design: it increases visual weight without changing the width of any character. This means text can appear bolder on hover without reflowing adjacent content. Traditional weight changes (400 to 500) shift glyph widths and cause layout jitter.

**Design application**: Use grade shifts for hover states on navigation links, button labels, and interactive text elements where weight change is the desired feedback but layout stability is required.

### Optical Size for Automatic Readability

Fonts with an `opsz` axis adjust their internal design for the rendered size. At small sizes: wider spacing, larger x-height, open apertures, reduced stroke contrast. At large sizes: tighter spacing, refined details, higher stroke contrast.

**Design application**: Enable `font-optical-sizing: auto` globally. The font handles micro-adjustments that designers would otherwise need to specify manually at each size step. This is particularly valuable for type systems spanning from 12px captions to 72px display text.

---

## OpenType Feature Deep Guide

Beyond the per-brand rules in `opentype-rules.md`, these features apply universally regardless of brand.

### Numeric Features

| Feature | When to Activate | When to Avoid |
|---------|-----------------|---------------|
| `tnum` (tabular nums) | Data tables, price columns, metric dashboards -- any vertical number alignment | Running text, dates in prose, isolated numbers in sentences |
| `pnum` (proportional nums) | Body text, narrative content -- numbers that flow with text | Data columns, aligned numeric displays |
| `lnum` (lining nums) | UI labels, tables, all-caps contexts | Long-form editorial (old-style may be more appropriate) |
| `onum` (old-style nums) | Editorial body text, literary contexts -- numbers that sit on the baseline like lowercase letters | Data tables, UI elements, technical content |
| `frac` (fractions) | Recipe amounts, measurement displays, financial fractions | Running text where fractions are rare |

**Design rule**: The choice between lining and old-style numerals is a tone decision. Lining numerals (1234567890) feel technical and precise -- appropriate for SaaS, dashboards, engineering tools. Old-style numerals (with ascenders and descenders) feel literary and refined -- appropriate for editorial, luxury, publishing contexts.

### Text Features

| Feature | Purpose | Activation Context |
|---------|---------|--------------------|
| `kern` | Pair-specific spacing adjustments | Global -- enable on all text (usually on by default) |
| `liga` | Standard ligatures (fi, fl, ff) | Global for most fonts; disable in code/monospace contexts |
| `calt` | Contextual alternates | Global -- the font designer intended these substitutions |
| `smcp` / `c2sc` | Small caps / caps to small caps | Abbreviations, acronyms in running text, bylines |
| `case` | Case-sensitive forms | All-caps text -- adjusts punctuation and diacritics for uppercase context |

### Small Caps as Design Tool

True small caps (OpenType `smcp`) are not scaled-down capitals. They are separately designed glyphs with matching stroke weight and proportions. Use them for:

- **Abbreviations in body text**: "NASA" in small caps integrates with surrounding lowercase instead of shouting.
- **Bylines and attribution**: Author names in small caps create a distinct but restrained typographic voice.
- **Table headers**: Small caps headers distinguish from body text without the heaviness of bold or the size jump of larger text.

**Design caution**: Only use `smcp` when the font actually contains small cap glyphs. If it does not, the browser fakes them by scaling capitals down, which produces thin, anemic letterforms. Check feature support at wakamaifondue.com before activating.

---

## Text Wrapping Refinements

### `text-wrap: balance` for Headlines

Balances line lengths so no line is dramatically shorter than others. The result: headlines avoid the "runt" problem where one or two words sit alone on the final line.

**When to use**: All headings and short display text (up to ~6 lines). The browser redistributes words to equalize line lengths.

**When NOT to use**: Body paragraphs (too many lines for the algorithm), long-form content, or any text where left-aligned ragged-right is the intended rhythm.

### `text-wrap: pretty` for Body Text

Prevents single-word final lines (widows) in paragraphs. Less aggressive than `balance` -- it only adjusts the last few lines rather than redistributing the entire block.

**When to use**: Body paragraphs, descriptions, any multi-line running text.

**Design impact**: Eliminates the visual awkwardness of a single dangling word at the end of a paragraph. This is a micro-refinement that contributes to overall typographic polish.

### `tabular-nums` Usage Timing

Tabular (fixed-width) numerals ensure digits in columns align vertically. Each digit occupies the same horizontal space regardless of its shape (a "1" takes the same width as a "0").

**Activate `tabular-nums` when**:
- Numbers appear in vertical columns (tables, price lists, metric dashboards)
- Numbers animate or count up (prevents jitter from width changes)
- Multiple numbers need to align at decimal points

**Do NOT activate when**:
- Numbers appear in running text ("The year 2024 saw 13% growth") -- fixed-width digits create awkward spacing in prose
- Numbers are isolated and not compared to other numbers
- The font's default proportional numerals look better in the context

---

## Font Loading Priority

Design-level decisions about which fonts to load first:

1. **Critical font**: The body text font used above the fold. Preload this. Use `<link rel="preload" as="font" type="font/woff2" crossorigin>`.
2. **Secondary font**: Heading/display font if different from body. Load with `swap` but do not preload unless it is above the fold.
3. **Mono font**: Only loaded when code blocks are visible. Lazy load or defer.
4. **Icon font**: If used (prefer inline SVG instead), load with `block` display since icon fonts render as invisible squares without the font file.

**Design rule**: Never preload more than 2 font files. Each preloaded font competes with other critical resources (CSS, JS, images) for bandwidth during initial page load. Prioritize the font that renders the most visible text.
