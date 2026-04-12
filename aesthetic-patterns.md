# Aesthetic Pattern Library

Encodable design patterns extracted from Claude, Stripe, Linear, and Vercel. Each pattern is a concrete, token-level directive that can be applied conditionally based on the tone and aesthetic direction declared in `<design_thinking>`.

This file extends Tier 3 of `SKILL.md`. When a pattern's trigger keywords match the declared tone, apply that pattern's token adjustments during spec generation.

---

## How to Use This Library

1. During `<design_thinking>`, identify the tone (e.g., "refined minimal SaaS," "dark developer tool," "warm editorial").
2. Scan the trigger keywords below. Matching patterns become active directives.
3. Check the **Compatibility Matrix** at the bottom before combining patterns -- some conflict.
4. Apply each active pattern's token adjustments to `tokens.json` and note layout implications in `layout-spec.yaml`.

---

## The Patterns

### Pattern 1: Lightness as Luxury
**Source**: Stripe
**Trigger**: When tone includes "luxury," "premium," "financial," "refined," "whisper," "understated authority"
**Rule**: Use font-weight 300 for all display and headline text. Authority comes from the confidence NOT to shout. Reserve weight 400 for UI elements (buttons, links, navigation); never go above 400 in the primary font. Progressive negative letter-spacing tightens at larger sizes: approximately -0.02em at 48px+, relaxing toward 0 at body sizes.
**Token impact**:
- `typography.display.weight`: `300` (not the conventional 600-700)
- `typography.heading.weight`: `300`
- `typography.body.weight`: `300`
- `typography.button.weight`: `400`
- `typography.display.letterSpacing`: scale from `-1.4px` at 56px to `-0.26px` at 26px to `normal` at 16px
- `typography.display.lineHeight`: `1.03` to `1.15` (tight, allowing the lightness to create density)
- `color.text.heading`: deep navy (e.g., `#061b31`) rather than black -- warmth without weight
**Anti-pattern**: Using weight 600-700 for headlines because "headings should be bold." The convention that bold = important is the first assumption to shed. Lightness at large sizes creates more visual distinction than boldness, because it is unexpected.
**Example**: Stripe hero -- 56px, weight 300, letter-spacing -1.4px, line-height 1.03, color `#061b31`. The headline whispers with more authority than a shouting 700-weight ever could.

---

### Pattern 2: Darkness as Canvas
**Source**: Linear
**Trigger**: When tone includes "dark mode native," "developer tool," "precision," "engineering," "night mode," "starlight," "void"
**Rule**: Build on near-black as the native medium, not as an inverted light theme. Use a luminance-stepping model where elevation = lighter background opacity. The deepest canvas is near-pure black; each elevation step adds a fractional increment of white. Text is never pure white (`#ffffff`); use slightly tinted near-white to prevent eye strain.
**Token impact**:
- `color.surface.base`: `#08090a` (marketing/hero) or `#010102` (deepest void)
- `color.surface.level1`: `#0f1011` (panels, sidebars)
- `color.surface.level2`: `#191a1b` (cards, dropdowns, elevated containers)
- `color.surface.level3`: `#28282c` (hover states, highest elevation)
- `color.text.primary`: `#f7f8f8` (near-white, not pure white)
- `color.text.secondary`: `#d0d6e0` (cool silver)
- `color.text.tertiary`: `#8a8f98`
- `color.text.quaternary`: `#62666d`
- `color.border.default`: `rgba(255,255,255,0.08)` (semi-transparent white)
- `color.border.subtle`: `rgba(255,255,255,0.05)`
- `shadow.card`: use background luminance stepping, not drop shadows -- dark-on-dark shadows are invisible
- Button backgrounds: `rgba(255,255,255,0.02)` to `rgba(255,255,255,0.05)` (translucent, never solid)
**Anti-pattern**: Taking a light theme and inverting the colors. Dark-native means information hierarchy is managed through luminance gradation of backgrounds, not through shadow darkness. Solid-colored dark backgrounds on cards (e.g., `#1a1a2e`) destroy the translucency system.
**Example**: Linear card -- `rgba(255,255,255,0.02)` background, `1px solid rgba(255,255,255,0.08)` border, content at `#f7f8f8` / `#d0d6e0` / `#8a8f98` creating a three-tier text luminance hierarchy on a near-black canvas.

---

### Pattern 3: Compression as Identity
**Source**: Vercel (extreme), Stripe (moderate), Linear (moderate)
**Trigger**: When tone includes "engineered," "infrastructure," "compressed," "developer," "minified," "precision," "technical"
**Rule**: Apply aggressive negative letter-spacing at display sizes. Text should feel engineered, dense, and optimized -- like minified code. The compression ratio scales with font size: maximum compression at display sizes, relaxing to normal at body sizes. This creates a visual tension between compressed headlines and generous surrounding whitespace.
**Token impact**:
- At `48px+`: letter-spacing from `-2.4px` (Vercel extreme) to `-1.0px` (Linear/Stripe moderate)
- At `32px`: `-1.28px` (Vercel) to `-0.64px` (Stripe)
- At `24px`: `-0.96px` (Vercel) to `-0.26px` (Stripe)
- At `16px` and below: `normal` or very slight negative (`-0.165px` for Linear's body)
- `typography.display.lineHeight`: `1.00` to `1.03` (ultra-tight, complements the compression)

Three intensity levels:
| Intensity | 48px spacing | 32px spacing | Source |
|-----------|-------------|-------------|--------|
| Maximum   | -2.4px to -2.88px | -1.28px | Vercel |
| Standard  | -1.056px | -0.704px | Linear |
| Gentle    | -0.96px | -0.64px | Stripe |

**Anti-pattern**: Default letter-spacing (0) or positive letter-spacing on display text. Default tracking at large sizes looks loose and unintentional -- like the designer forgot to set it. Positive tracking at display sizes reads as old-fashioned or amateurish unless deliberately evoking a specific era.
**Example**: Vercel hero -- 48px, weight 600, letter-spacing -2.4px, line-height 1.00. The text feels compressed into a solid block, like infrastructure made visible.

---

### Pattern 4: Warmth as Humanity
**Source**: Claude
**Trigger**: When tone includes "warm," "editorial," "literary," "human," "trustworthy," "approachable," "organic," "parchment," "companion"
**Rule**: Build on warm-toned neutrals exclusively. Every gray in the system has a yellow-brown undertone -- no cool blue-grays anywhere. The background is parchment-toned (warm cream), not white. Accent color is earthy (terracotta, ochre, rust) rather than tech-standard purple/blue. Typography pairs a serif for headlines (authority, literary gravitas) with a clean sans for UI (utility, efficiency). Headline weight is a singular medium (500) -- consistent across all sizes like one author's voice.
**Token impact**:
- `color.surface.base`: warm cream like `#f5f4ed` (parchment)
- `color.surface.elevated`: `#faf9f5` (ivory)
- `color.surface.dark`: `#141413` (olive-tinted near-black, not cool black)
- `color.text.primary`: `#141413` (warm near-black)
- `color.text.secondary`: `#5e5d59` (olive gray)
- `color.text.tertiary`: `#87867f` (stone gray -- warm)
- `color.accent`: earthy tone like `#c96442` (terracotta) -- deliberately un-tech
- `color.border.default`: `#f0eee6` (cream-tinted)
- `color.border.emphasis`: `#e8e6dc` (warm sand)
- `typography.display.family`: serif (e.g., Georgia, Freight Display, Lora, or custom serif)
- `typography.display.weight`: `500` (single weight for all serif headings)
- `typography.body.family`: sans-serif (the utility complement)
- `typography.body.lineHeight`: `1.60` (generous, literary -- more book than dashboard)
- `typography.display.lineHeight`: `1.10` to `1.30` (tight but breathing)
**Anti-pattern**: Cool blue-grays in the neutral palette. Even one cool gray breaks the warm chromatic consistency. Also: using bold (700) on serif headlines -- it destroys the literary elegance. And pure white (`#ffffff`) as page background -- warmth requires tint.
**Example**: Claude hero -- 64px serif weight 500, line-height 1.10, on `#f5f4ed` parchment, text in `#141413`, subtitle in `#5e5d59` at 20px sans with 1.60 line-height. Terracotta `#c96442` CTA. Every element says "thoughtful companion," not "powerful tool."

---

### Pattern 5: Shadow as Architecture
**Source**: Vercel (primary), Stripe (secondary)
**Trigger**: When tone includes "structured," "architectural," "layered," "built," "precision depth," "premium cards"
**Rule**: Use multi-layer shadow stacks where each layer serves a distinct structural purpose. Shadows are not decorative blur -- they are architectural layers: one for the border simulation, one for near-elevation, one for far-elevation, and optionally one for inner glow. Each layer uses different offset, blur, spread, and opacity calibrated to create parallax-like depth.
**Token impact**:
- `shadow.card.standard` (Vercel model):
  ```
  rgba(0,0,0,0.08) 0px 0px 0px 1px,     /* border layer */
  rgba(0,0,0,0.04) 0px 2px 2px,           /* near shadow */
  rgba(0,0,0,0.04) 0px 8px 8px -8px,      /* far shadow (negative spread = contained) */
  #fafafa 0px 0px 0px 1px                  /* inner glow */
  ```
- `shadow.card.elevated` (Stripe model):
  ```
  rgba(50,50,93,0.25) 0px 30px 45px -30px,  /* far shadow, brand-tinted */
  rgba(0,0,0,0.1) 0px 18px 36px -18px       /* near shadow, neutral */
  ```
- Shadow opacity never exceeds `0.25` for any layer
- Negative spread values (`-30px`, `-18px`, `-8px`) keep shadows contained within the element's horizontal footprint
**Anti-pattern**: Single-layer `box-shadow` with generic gray (e.g., `0px 4px 16px rgba(0,0,0,0.1)`). This is the CSS equivalent of "I know I need a shadow but didn't think about why." Also: Material Design-style uniform elevation levels that ignore brand color in shadow.
**Example**: Vercel featured card -- four-layer shadow stack creating a card that feels structurally *built* rather than *floating*. The inner `#fafafa` ring creates a subtle glow that no single-layer shadow can achieve.

---

### Pattern 6: Ring as Border
**Source**: Claude (primary), Vercel (secondary), Linear (secondary)
**Trigger**: When tone includes "soft," "approachable," "subtle containment," "gentle," "refined," "borderless"
**Rule**: Replace traditional CSS `border` with `box-shadow: 0px 0px 0px 1px [color]`. This creates a border-like line in the shadow layer, which avoids box model dimension changes, enables smoother transitions, handles rounded corners without clipping, and has a subtler visual weight than hard borders. The ring color should match the design's tonal palette.
**Token impact**:
- `border.card`: replace with `shadow.ring` token
- `shadow.ring.light`: `0px 0px 0px 1px rgba(0,0,0,0.08)` (Vercel -- achromatic)
- `shadow.ring.warm`: `0px 0px 0px 1px #d1cfc5` (Claude -- warm gray ring)
- `shadow.ring.dark`: `0px 0px 0px 1px rgba(0,0,0,0.2)` (Linear -- on dark surfaces)
- `shadow.ring.brand`: `0px 0px 0px 1px [brand-color]` (brand-tinted variant)
- Hover states: adjust ring color or add a second ring layer
- Active/pressed: use `inset 0px 0px 0px 1px` at reduced opacity (Claude pattern)

Three tonal variants:
| Tone | Ring color | Source |
|------|-----------|--------|
| Warm | warm gray like `#d1cfc5` or `#e8e6dc` | Claude |
| Neutral | `rgba(0,0,0,0.08)` | Vercel |
| Dark surface | `rgba(0,0,0,0.2)` or `rgba(255,255,255,0.08)` | Linear |

**Anti-pattern**: Using `border: 1px solid #e0e0e0` as a reflexive containment strategy. Hard borders add visual weight and create box model arithmetic. They also transition poorly and clip at rounded corners on some renderers.
**Example**: Claude button -- `#e8e6dc 0px 0px 0px 0px, #d1cfc5 0px 0px 0px 1px`. The double-ring declaration (one at 0px, one at 1px) is a Claude-specific technique that creates an extremely controlled border appearance using only the shadow layer.

---

### Pattern 7: Typography as Brand DNA
**Source**: All four brands
**Trigger**: Always active when selecting fonts -- this pattern informs HOW to use the chosen typeface, not which typeface to choose
**Rule**: The font is not the brand -- the OpenType configuration and weight strategy IS the brand. Each top brand transforms a typeface into their own voice through specific OpenType feature sets and unconventional weight selections. When selecting a font, also define: (a) which OpenType features to enable globally, (b) a signature weight, and (c) a letter-spacing formula tied to font size.
**Token impact**:
- `typography.opentype.global`: define which features are enabled on ALL text
- `typography.opentype.data`: define features for numeric/tabular contexts

Brand-specific OpenType strategies:
| Brand | Font | Global Features | Data Features | Signature | Effect |
|-------|------|----------------|---------------|-----------|--------|
| Stripe | sohne-var | `"ss01"` | `"tnum"` | Alternate geometric glyphs | Cleaner, more modern letterforms |
| Linear | Inter Variable | `"cv01", "ss03"` | -- | Single-story `a`, geometric adjustments | Transforms Inter into "Linear's Inter" |
| Vercel | Geist | `"liga"` | `"tnum"` | Structural ligatures | Tighter, more efficient glyph combinations |
| Claude | Anthropic Serif/Sans | -- | -- | Serif/sans split by function | Serif = content authority, sans = UI utility |

**Anti-pattern**: Choosing a distinctive typeface and then using it at default settings. A custom font without OpenType configuration and a deliberate weight strategy is just a different font, not a brand voice. Also: using the same weight for headings and body (unless it is a deliberate single-weight strategy like Claude's 500-for-all-serifs).
**Example**: Linear enables `"cv01", "ss03"` on every Inter text element. Without these features, their pages would look like any other Inter-based site. With them, the lowercase `a` becomes single-story and several letterforms gain geometric precision -- it is Inter, but it is *Linear's* Inter.

---

### Pattern 8: Chromatic Restraint
**Source**: All four brands (each demonstrating a different restraint strategy)
**Trigger**: Always active -- this pattern defines how to limit color palette size
**Rule**: Top-tier brands use at most ONE chromatic accent color in their primary UI. Everything else is achromatic (grays/neutrals). The accent color is reserved for the highest-signal moments: primary CTAs and interactive states. Status colors (success, error, warning) exist but are muted or used at reduced opacity. The narrower the chromatic range, the more powerful each color use becomes.

Four restraint models:
| Model | Accent | Neutral tone | Status treatment | Source |
|-------|--------|-------------|-----------------|--------|
| Warm monochrome | Terracotta `#c96442` | Warm cream/brown grays | Warm-tinted, muted | Claude |
| Cool accent | Purple `#533afd` | Cool navy/blue grays | Alpha-reduced (0.2 opacity bg) | Stripe |
| Dark achromatic | Indigo `#5e6ad2` | Cool true grays | Green only, sparingly | Linear |
| Near-achromatic | Black `#171717` (CTA) | Pure grays | Workflow-specific (functional only) | Vercel |

**Token impact**:
- `color.accent`: ONE chromatic color, used for primary CTA and key interactive moments only
- `color.accent.hover`: darker/lighter variant of the single accent
- Status colors (`error`, `success`, `warning`): desaturated or at reduced alpha, harmonized with the base palette
- Decorative/gradient colors: allowed only in specific branded moments (hero, illustrations), never in UI chrome
- Maximum unique chromatic hues in the UI: 1-2 (excluding status)
**Anti-pattern**: Using 3+ chromatic colors in UI chrome. Purple buttons, blue links, green success, red errors, orange warnings, teal info -- this creates a rainbow that dilutes every color's signal. Also: using the accent color decoratively (backgrounds, gradients, dividers) instead of reserving it for action.
**Example**: Vercel's CTA button is `#171717` (black). Their *primary action color* is achromatic. The workflow colors (red, pink, blue) appear only in the Develop/Preview/Ship pipeline -- never in generic UI. This is chromatic restraint taken to its logical extreme.

---

### Pattern 9: Depth Hierarchy
**Source**: Vercel (light surfaces), Linear (dark surfaces), Stripe (branded shadows), Claude (ring-based)
**Trigger**: When designing elevation systems, card containment, or interactive state feedback
**Rule**: Define 4-6 explicit depth levels, each with a specific shadow treatment AND a specific use case. Never use shadows ad hoc. Each level should be perceptibly distinct from adjacent levels. The shadow technique should match the surface context (light vs. dark) and the brand's tonal strategy.

**Token impact** -- four depth philosophies:

**Light Surface Depth** (Vercel):
| Level | Shadow | Use |
|-------|--------|-----|
| 0 | none | Background |
| 1 | `rgba(0,0,0,0.08) 0px 0px 0px 1px` | Ring-border containment |
| 2 | Level 1 + `rgba(0,0,0,0.04) 0px 2px 2px` | Subtle card lift |
| 3 | Level 2 + `rgba(0,0,0,0.04) 0px 8px 8px -8px` + `#fafafa 0px 0px 0px 1px` | Featured card |

**Dark Surface Depth** (Linear):
| Level | Treatment | Use |
|-------|-----------|-----|
| 0 | `#08090a` bg | Deepest canvas |
| 1 | `rgba(255,255,255,0.02)` bg | First emergence |
| 2 | `rgba(255,255,255,0.05)` bg + `rgba(255,255,255,0.08)` border | Cards |
| 3 | Multi-layer stack with inset | Dialogs, command palette |

**Branded Shadow Depth** (Stripe):
| Level | Shadow | Use |
|-------|--------|-----|
| 0 | none | Background |
| 1 | `rgba(23,23,23,0.06) 0px 3px 6px` | Subtle ambient |
| 2 | `rgba(23,23,23,0.08) 0px 15px 35px` | Standard cards |
| 3 | `rgba(50,50,93,0.25) 0px 30px 45px -30px, rgba(0,0,0,0.1) 0px 18px 36px -18px` | Featured (brand-tinted) |

**Ring-Based Depth** (Claude):
| Level | Treatment | Use |
|-------|-----------|-----|
| 0 | none | Background |
| 1 | `1px solid #f0eee6` | Gentle containment |
| 2 | `0px 0px 0px 1px` ring shadow | Interactive states |
| 3 | `rgba(0,0,0,0.05) 0px 4px 24px` | Elevated (whisper-soft) |
| 4 | `inset 0px 0px 0px 1px` at 15% opacity | Pressed/active |

**Anti-pattern**: Using one shadow value for everything, or using shadows without a defined hierarchy. "Medium shadow" and "large shadow" without specific use cases is lazy elevation. Also: using Material Design's 24-level elevation system when 4-6 levels suffice.
**Example**: Stripe's Level 3 uses `rgba(50,50,93,0.25)` -- a blue-tinted shadow that echoes the navy brand palette. The shadow itself is *on brand*. Compare to a generic `rgba(0,0,0,0.15)` which communicates nothing about identity.

---

### Pattern 10: The Signature Weight
**Source**: Linear (`510`), Stripe (`300`), Vercel (`600`), Claude (`500` on serif only)
**Trigger**: When establishing a typographic system for a new project
**Rule**: Choose ONE unconventional font-weight as the project's signature -- a weight that most designers would not default to. This weight becomes the typographic fingerprint: the value that makes your text feel different from every other site using the same typeface. Variable fonts enable any weight from 1-999; do not restrict yourself to the conventional 100-step increments.

Signature weight strategies:
| Weight | Effect | When to use | Source |
|--------|--------|------------|--------|
| `300` | Ethereal, whispered authority | Luxury, finance, premium, understated | Stripe |
| `500` | Consistent, authoritative, singular voice | Editorial, literary, trust-focused (on serif) | Claude |
| `510` | Subtly emphasized without medium's heaviness | Developer tools, precision, modern | Linear |
| `590` | Strong but not bold, decisive | Strong emphasis complement to 510 | Linear |
| `600` | Confident, structural headings | Infrastructure, engineering, headlines-only | Vercel |

**Token impact**:
- `typography.signature.weight`: the chosen unconventional weight
- This weight should appear on the MOST VISIBLE text elements (headlines or primary UI, depending on strategy)
- Pair with 1-2 supporting weights only: the system should have 2-3 weights total, not 5+
- Variable font required if using non-100-step weights (510, 590, etc.)

Weight pairing strategies:
| Strategy | Signature | UI weight | Emphasis | Source |
|----------|-----------|-----------|----------|--------|
| Light-led | 300 | 400 | -- | Stripe |
| Medium-led | 510 | 400 | 590 | Linear |
| Heavy-led | 600 | 500 | 400 | Vercel |
| Uniform (serif) | 500 | 400-500 (sans) | -- | Claude |

**Anti-pattern**: Using 400 for body and 700 for headings. This is the Times New Roman of weight systems -- functional but invisible. Also: using 5+ different weights, which creates noise rather than hierarchy. And: choosing a distinctive weight but failing to apply it consistently (using 510 on some headings and 500 on others).
**Example**: Linear uses weight 510 -- a value between regular (400) and medium (500). This creates a subtle but pervasive emphasis that you *feel* without consciously noticing. It is the typographic equivalent of slightly increasing the saturation in a photograph: everything looks a bit more vivid, but you cannot point to why.

---

## Compatibility Matrix

Patterns can be combined, but some conflict. Check this matrix before activating multiple patterns.

### Conflicts (do NOT combine)

| Pattern A | Pattern B | Conflict reason |
|-----------|-----------|----------------|
| **Lightness as Luxury** (weight 300) | **The Signature Weight** at 600 | Mutually exclusive headline weight philosophies |
| **Darkness as Canvas** (near-black bg) | **Warmth as Humanity** (parchment bg) | Opposite surface strategies; pick one as primary. A dark-warm hybrid is possible (using Claude's `#141413` olive-black for dark sections) but requires careful execution |
| **Compression as Identity** (extreme, -2.4px) | **Warmth as Humanity** (serif headlines) | Extreme negative tracking destroys serif legibility. Serifs need breathing room. Gentle compression (-0.5px) is acceptable on serif |
| **Lightness as Luxury** (weight 300) | **Warmth as Humanity** (weight 500 serif) | Different weight philosophies. Can coexist if the serif is at 500 and a different sans headline is at 300, but this is a serif/sans split, not a combination |

### Strong Combinations

| Pattern A | Pattern B | Why they work |
|-----------|-----------|---------------|
| **Lightness as Luxury** | **Compression as Identity** (gentle) | Stripe's exact formula: weight 300 + moderate negative tracking = whispered density |
| **Lightness as Luxury** | **Shadow as Architecture** (Stripe model) | Light type + brand-tinted deep shadows = ethereal text floating above rich depth |
| **Darkness as Canvas** | **Compression as Identity** | Linear's formula: dark canvas + compressed display type = engineering precision |
| **Darkness as Canvas** | **Ring as Border** (dark variant) | Translucent borders on dark surfaces are the natural containment strategy |
| **Warmth as Humanity** | **Ring as Border** (warm variant) | Claude's formula: warm rings replace hard borders for gentle containment |
| **Warmth as Humanity** | **Chromatic Restraint** (warm monochrome) | Single earthy accent on warm neutrals = maximum tonal coherence |
| **Shadow as Architecture** | **Ring as Border** | These are complementary: rings for containment, multi-layer stacks for elevation. Vercel uses both simultaneously |
| **Compression as Identity** | **The Signature Weight** (any) | Tracking and weight are independent axes. Any weight can be compressed |
| **Chromatic Restraint** | Every pattern | Restraint never conflicts -- it amplifies whatever system it accompanies |
| **Typography as Brand DNA** | Every pattern | OpenType configuration is independent of visual strategy |
| **Depth Hierarchy** | Every pattern | Every design needs depth levels; the philosophy varies by surface tone |

### Brand Formula Quick Reference

Recreating a specific brand's aesthetic requires combining specific patterns:

| Brand | Patterns to activate | Key tokens |
|-------|---------------------|------------|
| **Stripe** | Lightness as Luxury + Compression (gentle) + Shadow as Architecture (Stripe) + Chromatic Restraint (cool accent) | weight 300, `"ss01"`, `rgba(50,50,93,0.25)` shadows, `#533afd` accent |
| **Linear** | Darkness as Canvas + Compression (standard) + Signature Weight (510) + Chromatic Restraint (dark achromatic) | weight 510, `"cv01","ss03"`, luminance stepping, `#5e6ad2` accent |
| **Vercel** | Compression (maximum) + Shadow as Architecture (Vercel) + Ring as Border + Chromatic Restraint (near-achromatic) | weight 600, `"liga"`, -2.4px tracking, multi-layer shadow stacks |
| **Claude** | Warmth as Humanity + Ring as Border (warm) + Signature Weight (500 serif) + Chromatic Restraint (warm monochrome) | weight 500 serif, parchment `#f5f4ed`, terracotta `#c96442`, ring shadows |

---

## Integration with SKILL.md

This file is a **Tier 3 extension**. It does not replace the Tier 3 aesthetic directives in SKILL.md -- it provides deeper, more specific guidance for each directive.

Mapping to existing Tier 3 sections:

| SKILL.md Tier 3 section | Patterns that extend it |
|------------------------|------------------------|
| Typography Tokens | Pattern 3 (Compression), Pattern 7 (Typography as Brand DNA), Pattern 10 (Signature Weight) |
| Color Tokens | Pattern 4 (Warmth), Pattern 8 (Chromatic Restraint) |
| Spatial Composition | Pattern 5 (Shadow as Architecture), Pattern 9 (Depth Hierarchy) |
| Motion Tokens | (Not covered -- these patterns address static visual properties) |
| Materiality | Pattern 2 (Darkness as Canvas), Pattern 6 (Ring as Border) |

**Loading instruction**: When SKILL.md's design thinking identifies a tone that matches any pattern trigger, load the relevant patterns from this file and apply their token-level directives. Multiple compatible patterns can be active simultaneously -- consult the compatibility matrix.

---

### Pattern 11: Polish Pass
**Source**: impeccable-style-universal/polish
**Trigger**: When the feature is functionally complete and entering final quality pass. Keywords: "polish," "refinement," "final pass," "shipping," "detail sweep," "pixel perfect"
**Rule**: Polish is a systematic audit across multiple dimensions, executed in a specific order of impact. The sequence: alignment and spacing first (structural defects are most visible), then typography consistency (hierarchy must be airtight), then interaction states (every interactive element needs all eight states), then micro-transitions (state changes must be animated appropriately), then content/copy consistency. Polish is never random -- it follows a checklist.
**Token impact**:
- **Alignment verification**: Every element snaps to the spacing scale. No arbitrary values (13px, 17px gaps). Enable grid overlay and inspect computed spacing.
- **Typography audit**: Same semantic elements use identical size/weight/color throughout. Line length is 45-75 characters for body text. No widows (single words on last line).
- **Interaction state completeness**: Every interactive element must have: default, hover, focus, active, disabled, loading, error, and success states. Missing states create broken experiences.
- **Transition smoothness**: All state changes animated at 150-300ms with ease-out-quart/quint/expo. Only transform and opacity animated. 60fps verified.
- **Tinted neutrals**: No pure gray (`oklch(X% 0 0)`) or pure black (`#000`) in the palette. Every neutral carries a 0.005-0.015 chroma tint matching the brand hue.
- **Gray-on-color check**: No gray text on colored backgrounds -- gray looks washed out on color. Use a darker shade of the background color or semi-transparent overlay instead.
- **Token consistency**: No hard-coded colors. Every value references a design token.
- **Touch targets**: 44x44px minimum on touch devices. Extended via padding or pseudo-elements if visual element is smaller.
- **Focus indicators**: Visible, high-contrast focus rings on every interactive element. Never removed without a clear replacement.
- **Reduced motion**: All animations respect `prefers-reduced-motion`. Test by enabling the preference.
**Anti-pattern**: Polishing before the feature is functionally complete. Polish applied to broken functionality is wasted effort. Also: polishing one component to perfection while leaving adjacent components rough -- consistent quality level matters more than peak quality on any single element.
**Example**: The difference between a good interface and a shipped interface: every button has all eight states, every spacing value is from the scale, every gray has a warm or cool tint, every transition is smooth, every focus ring is visible. None of these individually are remarkable; together they create the feeling of "this was made by someone who cares."

---

### Pattern 12: Quality Audit
**Source**: impeccable-style-universal/audit
**Trigger**: When evaluating the overall quality of an interface before or after implementation. Keywords: "audit," "review," "quality check," "assessment," "evaluation," "compliance check," "design QA"
**Rule**: A quality audit documents issues without fixing them. It generates a prioritized report organized by severity (critical, high, medium, low) across five dimensions. The audit starts with an anti-pattern check (does this look AI-generated?), then moves through accessibility, performance, theming, and responsive design. Every finding includes location, severity, impact description, standard violated (if applicable), and recommended fix. The output is a triage-ready document, not a narrative.
**Token impact**:
- **Anti-pattern verdict**: First pass checks for AI slop tells -- purple/cyan gradients, glassmorphism, gradient text, hero metrics in a card grid, generic fonts (Inter, Roboto), bounce/elastic easing, glow effects as affordances. A single AI slop tell drops the design quality score significantly.
- **Accessibility audit**: Contrast ratios (4.5:1 body text, 3:1 large text, 3:1 UI components), ARIA completeness, keyboard navigation, focus indicators, semantic HTML, form labeling, alt text, heading hierarchy. Reference WCAG AA as baseline, AAA as target for text contrast.
- **Performance audit**: Layout thrashing (animated width/height/top/left), expensive animations (non-compositor properties on large surfaces), missing optimization (no lazy loading, no will-change discipline), bundle size (unused dependencies).
- **Theming audit**: Hard-coded colors (not using tokens), broken dark mode (missing variants, poor dark contrast), inconsistent token usage (wrong tokens for context), theme switching gaps.
- **Responsive audit**: Fixed widths that break on mobile, touch targets below 44px, horizontal overflow, text scaling failures, missing mobile breakpoints.
- **Severity classification**: Critical = blocks core functionality or violates WCAG A. High = significant usability/accessibility impact or WCAG AA violations. Medium = quality issues, AAA violations, performance concerns. Low = minor inconsistencies, optimization opportunities.
**Anti-pattern**: Mixing severity levels inconsistently (calling everything "critical"). Reporting without impact explanation ("this is wrong" vs. "this is wrong because 8% of users cannot distinguish these colors"). Skipping positive findings -- noting what works well provides a baseline to protect. Providing generic recommendations instead of specific, actionable fixes.
**Example**: An audit report's executive summary: "14 issues found. 2 critical (missing focus traps on modal, form errors not linked to fields), 4 high (3 contrast failures, 1 keyboard trap), 5 medium (hard-coded colors, missing dark mode variants), 3 low (inconsistent icon sizes, minor spacing irregularities). Anti-pattern verdict: PASS -- no AI slop detected. Top priority: fix the 2 critical accessibility issues before next deploy."

---

### Pattern 13: Amplify Impact
**Source**: impeccable-style-universal/bolder
**Trigger**: When the design is functional but feels flat, boring, or indistinguishable from templates. Keywords: "bolder," "more impact," "more dramatic," "more personality," "more energy," "make it pop," "amplify," "hero moment," "visual drama"
**Rule**: Bold design is confident design -- it makes deliberate choices at extreme ends of the spectrum rather than safe choices in the middle. The core technique is contrast amplification: make big things BIGGER, small things smaller, heavy things heavier, light things lighter. Pick ONE hero moment per viewport and make it unmistakable. Every other element exists to support that focal point.
**Token impact**:
- **Typography amplification**: Replace generic fonts with distinctive choices. Create dramatic size jumps (3x-5x between body and display, not 1.5x). Pair extreme weight contrasts (900 with 200, not 600 with 400). Consider variable font width axis for condensed/extended display text. Monospace as intentional design accent (not as lazy developer default).
- **Spatial drama**: Extreme scale jumps between focal and supporting elements. Break the grid -- let hero elements escape their containers. Asymmetric layouts that create visual tension. Generous whitespace used as a design element (100-200px gaps, not 20-40px). Intentional element overlap for depth.
- **Color intensification**: Increase saturation toward more vibrant, energetic colors (without going neon). Commit to a dominant color strategy -- one bold color owns 60% of colored elements. Sharp, high-contrast accents that command attention. Rich, intentional gradients (multi-stop, brand-specific, NOT default purple-to-blue). Tinted neutrals that harmonize with the bold palette.
- **Motion choreography**: Staggered entrance animations with 50-100ms delays per element. Scroll-triggered reveals for progressive storytelling. Satisfying micro-interactions on hover and click. Smooth transitions using expo-out easing for confidence (not bounce/elastic -- they cheapen the effect).
- **Composition**: Clear focal points with dramatic treatment. Full-bleed elements that use the entire viewport. Unexpected proportions (70/30, 80/20 splits instead of safe 50/50). Diagonal flows that escape horizontal/vertical rigidity.
- **Surface and texture**: Dramatic shadows (large, soft, intentional). Mesh patterns, noise textures, halftone, duotone -- NOT glassmorphism (overused AI slop). Thick borders, decorative frames, custom shapes -- NOT rounded rectangles with a colored left border. Illustrative elements that reinforce brand rather than generic stock art.
**Anti-pattern**: Defaulting to the AI slop playbook when asked to be "bolder": cyan/purple gradients, glassmorphism, neon accents on dark backgrounds, gradient text, glow effects. These are the OPPOSITE of bold -- they are generic. Bold means distinctive, memorable, and confident. If someone showed the result and said "AI made this bolder," and the answer is immediately obvious, the design has failed. Also: making everything bold (then nothing is bold -- contrast requires restraint alongside drama). And: sacrificing readability for aesthetics (body text must always be readable).
**Example**: A hero section with a 72px condensed display heading at weight 800, letter-spacing -3px, surrounded by 120px of whitespace. A single terracotta-colored CTA button. Body text at 16px weight 300, creating a 5:1 size ratio and a dramatic weight contrast. The page background has a subtle noise texture. Below, feature cards use asymmetric 70/30 layout with large imagery. Every element is intentional, and the eye knows exactly where to look first, second, third.

---

### Pattern 14: Color Strategy
**Source**: impeccable-style-universal/colorize
**Trigger**: When establishing or refining the color system for a project. Keywords: "color palette," "color system," "colorize," "add color," "color strategy," "too monochromatic," "needs warmth," "color meaning"
**Rule**: Strategic color introduction follows a precise hierarchy: understand the current color state, identify where color adds meaning (not just decoration), choose 2-4 chromatic colors beyond neutrals, assign each color a semantic role, then distribute according to the 60-30-10 rule by visual weight. Color works because of restraint -- every color usage must have a purpose. The system should be built in OKLCH for perceptual uniformity.
**Token impact**:
- **OKLCH palette construction**: Build all palette scales in OKLCH. Lightness steps should be perceptually equidistant (impossible in HSL). Chroma peaks at mid-lightness (50-70% L, chroma 0.10-0.20) and reduces toward both extremes (near-white: chroma 0.01-0.08; near-black: chroma 0.01-0.05). Hue stays constant within a scale.
- **Tinted neutral cascade**: Replace all pure grays with brand-hue-tinted neutrals at chroma 0.005-0.015. The tint carries into borders, shadows, placeholders, disabled states, dividers, and surfaces. If any element uses a pure achromatic gray while others are tinted, it creates a subtle discord.
- **Semantic color roles**: Status colors (success/error/warning/info) exist outside the 60-30-10 budget. They appear contextually and should be desaturated or alpha-reduced to avoid competing with the brand accent. Category colors limited to 5-8 distinct hues (more categories need shape/pattern differentiation, not more colors).
- **60-30-10 by visual weight**: 60% neutral backgrounds and whitespace (the canvas). 30% text, borders, secondary surfaces (the structure). 10% accent -- CTAs, highlights, focus states (the signal). Count distinct accent-color moments per viewport; more than 3-5 means overuse.
- **Alpha discipline**: Alpha transparency is acceptable for overlays, hover states, and dark-mode borders. It is a design smell for text colors, surface colors, and light-mode borders -- these should be defined as opaque values in the token system.
- **Dark mode color rules**: Lighter surfaces create depth (not shadows). Reduce text weight slightly (light-on-dark text appears heavier). Desaturate accents by 10-20%. Use 8-18% lightness for backgrounds (never pure black). Borders as semi-transparent white (`rgba(255,255,255,0.05-0.08)`).
- **Color-blind safety**: Never rely on color alone. Every status differentiation pairs color with icon and text. Test under deuteranopia simulation before shipping. Charts and data visualizations need shape or pattern encoding alongside color.
**Anti-pattern**: Using 3+ chromatic colors in UI chrome (purple buttons, blue links, green success, red errors, orange warnings, teal info = rainbow that dilutes every color's signal). Using pure gray (`oklch(X% 0 0)`) for neutrals -- dead, personality-free. Putting gray text on colored backgrounds (use a darker shade of the background color). Using pure black (`#000`) for large areas. Using alpha transparency as a substitute for defining proper palette entries. The default purple-to-blue gradient (the most generic color choice in AI-generated design).
**Example**: A warm-toned project establishes its color system: OKLCH hue 60 (amber) at chroma 0.01 tints every neutral in the palette. The single accent is terracotta (`oklch(55% 0.15 35)`). Status colors are desaturated: success green at chroma 0.10 (not the vivid 0.20 default). The 60% is warm ivory surfaces, the 30% is warm gray text and borders, the 10% is terracotta on the primary CTA and key interactive moments. No other chromatic colors appear in the UI. The color system has six neutrals, one accent with three shades, and four status colors. That is the entire palette.
