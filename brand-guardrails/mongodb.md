# Mongodb -- Design Guardrails

## Do's (10 items)

1. **Use `#ffffff` as the primary page background.** This is the foundation of the Mongodb visual identity. Verify: page background matches this value.

2. **Reserve `#00684a` for primary CTAs and interactive accents.** It is the high-signal brand color. Verify: accent appears only on buttons, links, and active states.

3. **Use `#21313c` for primary text.** Maintain consistent text hierarchy. Verify: headings and body text use this color on light surfaces.

4. **Use `#65727b` for secondary and descriptive text.** Creates clear information hierarchy. Verify: metadata and descriptions use this muted tone.

5. **Maintain the brand's clean light atmosphere.** Light surfaces create a clean canvas for content.

6. **Use the 8px spacing grid consistently.** All padding, margin, and gap values should be multiples of 4px or 8px.

7. **Apply appropriate border-radius for the brand.** Mongodb's geometry is rounded and approachable.

8. **Use weight 600+ for headings, 400 for body.** Clear weight hierarchy creates visual structure without visual noise.

9. **Keep shadows subtle and minimal.** Heavy shadows feel foreign to the clean aesthetic.

10. **Ensure all interactive elements use the accent color consistently.** Links, buttons, and active states share `#00684a`.

## Don'ts (10 items)

1. **Do not use dark backgrounds for primary surfaces.** The light clean canvas is core identity.

2. **Do not apply `#00684a` as a decorative surface color.** It must remain scarce and high-signal.

3. **Do not introduce additional brand colors** beyond the defined palette. The color discipline is intentional.

4. **Do not use pure black (#000000) for primary text.** Use the brand's specific text color `#21313c`.

5. **Do not skip the accent color on interactive elements.** Every clickable element should signal interactivity through `#00684a`.

6. **Do not use arbitrary spacing values.** Stick to the 8px grid system.

7. **Do not use heavy font weights (800+) unless specifically part of the brand.** Most brands cap at 600-700.

8. **Do not use generic gray borders.** Use the brand's specific border tokens.

9. **Do not use heavy drop shadows.** They feel foreign to the brand.

10. **Do not mix brand fonts with generic system fonts** in visible UI elements.

## Critical Violations (5 items)

1. **Wrong background color.** Using black instead of `#ffffff` fundamentally changes the brand personality.

2. **Accent color used as surface fill.** Flooding the page with `#00684a` destroys the signal-to-noise ratio that makes the accent meaningful.

3. **Missing typographic hierarchy.** Without clear weight contrast between headings and body, the design loses its structure.

4. **Dark mode default when light is the native state.** The light atmosphere IS the brand identity.

5. **Generic design system tokens replacing brand-specific values.** Every color, font, and spacing value carries brand meaning.
