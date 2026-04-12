# Stripe -- Design Guardrails

## Do's (10 items)

1. **Enable `font-feature-settings: "ss01"` on every `sohne-var` text element.** The stylistic set modifies glyph shapes to create Stripe's geometric, modern feel. Verify: every element using `sohne-var` includes `font-feature-settings: "ss01"` in its computed styles.

2. **Use weight 300 for all headlines and body text.** Lightness is the signature -- the text is so confident it does not need weight to command attention. Verify: headline and body `font-weight` is `300`; weight 400 is reserved only for buttons, links, and navigation.

3. **Apply blue-tinted shadows (`rgba(50,50,93,0.25)`) for all elevated elements.** The primary shadow color echoes the navy-purple brand palette. Verify: no card, dropdown, or popover uses neutral gray shadows (`rgba(0,0,0,...)` alone) -- the blue-tinted layer must be present.

4. **Use Deep Navy (`#061b31`) for headings instead of `#000000`.** The warmth of this near-black blue adds premium depth. Verify: heading `color` is `#061b31`, never `#000000` or `#111111`.

5. **Keep border-radius between 4px and 8px.** Conservative rounding is intentional -- nothing pill-shaped, nothing harsh. Verify: `border-radius` on buttons is `4px`, on cards is `4px`-`8px`, and no element exceeds `8px` radius except compound bottom-rounding.

6. **Use `"tnum"` for any tabular or financial number display.** Tabular numerals ensure columns of figures align precisely. Verify: any data table, chart axis, or financial figure has `font-feature-settings: "tnum"` (not `"ss01"`).

7. **Layer shadows with blue-tinted far + neutral close for depth parallax.** The standard pattern: `rgba(50,50,93,0.25) 0px Y1 B1 -S1, rgba(0,0,0,0.1) 0px Y2 B2 -S2`. Verify: elevated card shadows contain exactly two layers with the branded blue shadow at a larger offset.

8. **Use `#533afd` (Stripe Purple) as the primary interactive and CTA color.** All primary buttons, active states, and links use this saturated violet. Verify: primary CTAs render `#533afd` background; links render `#533afd` text.

9. **Use `SourceCodePro` at 12px/weight 500 with line-height 2.00 for all code.** The generous code line-height is a deliberate readability choice. Verify: code blocks use `SourceCodePro` family with `line-height: 2.00`.

10. **Apply negative letter-spacing that scales with font size.** The progression: `-1.4px` at 56px, `-0.96px` at 48px, `-0.64px` at 32px, `-0.26px` at 26px, `normal` at 16px and below. Verify: display-size text has negative `letter-spacing` proportional to its font size.

## Don'ts (10 items)

1. **Do not use weight 600-700 for `sohne-var` headlines.** Weight 300 is the brand voice. Violation: `font-weight: 600` or `bold` on any `sohne-var` heading element.

2. **Do not use large border-radius (12px+, pill shapes) on cards or buttons.** Stripe is architecturally conservative. Violation: `border-radius: 12px`, `16px`, `9999px`, or `50%` on any button or card.

3. **Do not use neutral gray shadows.** Always tint with blue (`rgba(50,50,93,...)`). Violation: card shadow using only `rgba(0,0,0,...)` without the blue-tinted layer.

4. **Do not skip `"ss01"` on any `sohne-var` text.** The alternate glyphs define the personality. Violation: any `sohne-var` element missing `font-feature-settings: "ss01"`.

5. **Do not use pure black (`#000000`) for headings.** Always `#061b31` Deep Navy. Violation: heading `color: #000000` or `color: black`.

6. **Do not use warm accent colors (orange, yellow, amber) for interactive elements.** Purple is the primary interactive color. Violation: any button or link styled with warm hues.

7. **Do not apply positive letter-spacing at display sizes.** Stripe tracks tight at all sizes above 16px. Violation: `letter-spacing` > `0` on any text 18px or larger.

8. **Do not use Ruby (`#ea2261`) or Magenta (`#f96bee`) for buttons or links.** These accents are decorative and gradient-only. Violation: Ruby or Magenta as `background-color` on any interactive element.

9. **Do not use a dark-mode page background other than Brand Dark (`#1c1e54`).** Dark sections use deep branded indigo, not black or generic dark gray. Violation: `background-color: #000000`, `#111111`, or `#1a1a1a` for dark sections.

10. **Do not mix `"ss01"` and `"tnum"` on the same element.** They serve different contexts -- `ss01` for display/body, `tnum` for tabular data. Violation: `font-feature-settings: "ss01", "tnum"` on a single element.

## Critical Violations (5 items)

1. **Missing `"ss01"` on `sohne-var` text.** Without the stylistic set, the typography falls back to generic sohne letterforms and the entire brand personality evaporates. This is the single most impactful error.

2. **Bold (600-700) weight on headlines.** Stripe's whisper-weight 300 headlines are the defining visual move. Using bold turns Stripe into any other fintech site.

3. **Neutral gray shadows instead of blue-tinted.** The `rgba(50,50,93,0.25)` shadow color is what makes even elevation feel on-brand. Replacing it with generic black shadows removes the atmospheric depth.

4. **Pure black headings (`#000000`) instead of Deep Navy (`#061b31`).** The deep navy carries warmth and premium feel. Pure black is harsh and breaks the tonal consistency.

5. **Pill-shaped (9999px) or large-radius (16px+) buttons.** Stripe's conservative 4px radius is architecturally intentional. Large rounding makes the design look like a consumer app rather than financial infrastructure.
