# Webflow -- Design Guardrails

## Do's (10 items)

1. **Default to dark canvas (`#080808`) for primary surfaces.** Webflow's editor, marketing site, and brand collateral all start dark. Light (`#ffffff`) is the alternate mode, not the default. Verify: the hero section and primary containers use `#080808` or `#171717`, not white.

2. **Use Webflow Blue (`#146ef5`) exclusively for primary CTAs, focus rings, and selected states.** This is the only chromatic accent in the system. It must remain high-signal and scarce. Verify: `#146ef5` appears only on primary action buttons, active nav items, focused inputs, and toggle-on states -- never as a surface fill or decorative element.

3. **Set heading line-height to 1.04 (104%).** This ultra-tight line-height on geometric Poppins headings is Webflow's typographic signature. It creates visual density that contrasts with the generous 1.60 body text spacing. Verify: all H0-H3 headings have `line-height: 1.04`; H4-H5 use `1.30`.

4. **Use the exact 9-step gray scale for all neutral colors.** The scale is: `#171717` / `#222222` / `#363636` / `#5a5a5a` / `#757575` / `#898989` / `#ababab` / `#d8d8d8` / `#f0f0f0`. These are Webflow's official Gray 900 through Gray 100. Verify: every neutral color in the component matches one of these exact hex values.

5. **Enforce monochromatic discipline: black + white + one color per composition.** This is an explicit Webflow brand rule ("Each asset should include black, white, and one color"). The one color is `#146ef5` for UI contexts. Verify: no second chromatic hue (warm orange, green, purple) appears in the UI chrome. Semantic colors (`#ee1d36` error, `#00d722` success) are the only exceptions and must be used sparingly for status indicators only.

6. **Use `#363636` (Gray 700) borders as the primary depth signal on dark surfaces.** Where light themes use shadows, Webflow uses 1px solid borders to create structure. Verify: dark-mode cards and panels use `border: 1px solid #363636`, not box-shadows, as the primary containment method.

7. **Use Poppins Semibold (600) for all headings and Inter Regular (400) for all body text.** This is the Google Fonts equivalent of WF Visual Sans + WF Visual Sans Text. Verify: no heading uses Inter; no body text uses Poppins; heading weight is exactly 600, never 700 or bold.

8. **Apply letter-spacing `0.01em` on H0-H3 headings and `0.02em` on H4-H5.** Webflow's brand typography specifies precise tracking values. Verify: heading elements include the correct `letter-spacing` value for their tier.

9. **Maintain 8px-based spacing grid with generous section padding (120-160px) on marketing pages.** Tool-UI panels use tighter spacing (16px sections, 6-8px padding). The contrast between expansive marketing rhythm and dense tool-UI rhythm is intentional. Verify: section padding is 120px+ on marketing, 16px on editor panels.

10. **Apply backdrop-filter blur on sticky navigation and floating panels.** Webflow uses glassmorphism-lite with `backdrop-filter: blur(12px)` and semi-transparent backgrounds (`rgba(8,8,8,0.92)` dark, `rgba(255,255,255,0.92)` light). Verify: sticky nav has both `backdrop-filter` and transparent background, not a solid opaque background.

## Don'ts (10 items)

1. **Do not default to white (`#ffffff`) page backgrounds.** White is for alternate/light sections, not the primary canvas. Opening on white instead of dark breaks the Webflow brand's visual-builder personality. The dark canvas communicates "professional creative tool," not "generic SaaS."

2. **Do not use Webflow Blue (`#146ef5`) as a surface fill, section background, or card background.** Filling areas with the accent color destroys its signal-to-noise ratio. The blue must remain a point accent, not an area fill. One blue element per visible group maximum.

3. **Do not introduce a second chromatic color into UI chrome.** Warm orange CTAs, teal links, purple gradients -- all violate the monochromatic discipline. The only exceptions are semantic status colors (`#ee1d36`, `#00d722`, `#ffae13`) and only for their designated status purpose.

4. **Do not use approximate grays (`#333`, `#666`, `#999`, `#ccc`).** Webflow's gray scale is precisely defined. Shorthand or approximate grays create inconsistent tonal relationships. Every gray must match one of the 9 official steps exactly.

5. **Do not use humanist sans-serif fonts (San Francisco, Helvetica, Segoe UI) as heading substitutes.** Webflow's typography is geometric (perfectly circular O, even stroke weight). Humanist fonts have optical corrections that feel warm and organic -- the opposite of Webflow's precision aesthetic. Use Poppins as the heading fallback, Inter for body.

6. **Do not set heading line-height above 1.15.** Webflow's H0-H3 use 1.04; H4-H5 use 1.30. Any value above 1.15 on primary headings makes them look generic and loses the tight, controlled density that defines the brand's typographic voice.

7. **Do not use heavy drop shadows as the primary depth mechanism on dark surfaces.** On dark backgrounds, shadows are nearly invisible. Webflow uses `#363636` borders instead. Shadows on dark surfaces create muddy halos rather than clear depth. Reserve shadows for light-surface components only.

8. **Do not use rounded corners above 16px on functional UI elements.** Cards get 12px, buttons get 8px, inputs get 4px. Pill shapes (9999px) are reserved for tags and badges only. Over-rounding makes precise tool-UI look toy-like.

9. **Do not apply decorative gradients or multi-color background effects.** Webflow's visual language is flat, monochromatic, and precise. The only permitted gradient is a subtle single-hue fade: `rgba(20,110,245,0.08)` to transparent for background glow effects. No rainbow gradients, no multi-stop color transitions.

10. **Do not use bounce or elastic easing on functional transitions.** Webflow's motion language is "build, enhance, reduce" -- constructive and controlled. Use ease-out with 120-200ms duration for UI state changes. Playful physics-based animation is for marketing hero sequences only, never for buttons, dropdowns, or panel transitions.

## Critical Violations (5 items)

1. **White page background as default.** The dark canvas IS the Webflow identity. A component set that only works on white has missed the brand entirely. Every marketing page should open on `#080808`; every tool-UI panel should use `#222222`. White is the exception, not the rule.

2. **Webflow Blue (`#146ef5`) used as a surface fill or appearing on more than one element per visual group.** The moment blue floods a section background, card surface, or illustration area, the monochromatic discipline collapses. The blue must feel like a laser pointer -- precise, momentary, high-contrast against the grayscale world.

3. **Heading line-height at or above 1.20 on H0-H3.** The 1.04 tight heading is not a subtle refinement -- it is the single most distinctive visual feature of Webflow typography. Generic 1.2 or 1.15 line-height makes the design indistinguishable from any Inter-based tech site.

4. **Approximate or arbitrary gray values replacing the official scale.** Using `#333333` instead of `#363636`, or `#aaaaaa` instead of `#ababab`, introduces tonal drift that compounds across a page. The 9-step gray scale is engineered for specific contrast ratios and must be used verbatim.

5. **Multiple chromatic colors in a single composition.** If a card uses blue accent AND green success AND orange warning AND purple badge in the same view, the monochromatic rule is broken. Semantic colors appear only at the moment of status display, never as persistent visual accents. The composition should read as "grayscale + one blue spark."
