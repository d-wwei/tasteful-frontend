# Uber -- Design Guardrails

## Do's (10 items)

1. **Use `#000000` as the primary page background.** This is the foundation of the Uber visual identity. Verify: page background matches this value.

2. **Reserve `#ffffff` for primary CTAs and interactive accents.** It is the high-signal brand color. Verify: accent appears only on buttons, links, and active states.

3. **Use `#ffffff` for primary text.** Maintain consistent text hierarchy. Verify: headings and body text use this color on dark surfaces.

4. **Use `#afafaf` for secondary and descriptive text.** Creates clear information hierarchy. Verify: metadata and descriptions use this muted tone.

5. **Maintain the brand's dark immersive atmosphere.** Dark surfaces recede so content can glow.

6. **Use the 8px spacing grid consistently.** All padding, margin, and gap values should be multiples of 4px or 8px.

7. **Apply appropriate border-radius for the brand.** Uber's geometry is rounded and approachable.

8. **Use weight 600+ for headings, 400 for body.** Clear weight hierarchy creates visual structure without visual noise.

9. **Keep shadows heavy enough for dark surfaces.** Light shadows are invisible on dark backgrounds.

10. **Ensure all interactive elements use the accent color consistently.** Links, buttons, and active states share `#ffffff`.

## Don'ts (10 items)

1. **Do not use light backgrounds for primary surfaces.** The dark immersion is core identity.

2. **Do not apply `#ffffff` as a decorative surface color.** It must remain scarce and high-signal.

3. **Do not introduce additional brand colors** beyond the defined palette. The color discipline is intentional.

4. **Do not use pure white (#ffffff) for primary text.** Use the brand's specific text color `#ffffff`.

5. **Do not skip the accent color on interactive elements.** Every clickable element should signal interactivity through `#ffffff`.

6. **Do not use arbitrary spacing values.** Stick to the 8px grid system.

7. **Do not use heavy font weights (800+) unless specifically part of the brand.** Most brands cap at 600-700.

8. **Do not use generic gray borders.** Use the brand's specific border tokens.

9. **Do not use subtle shadows on dark surfaces.** They're invisible.

10. **Do not mix brand fonts with generic system fonts** in visible UI elements.

## Critical Violations (5 items)

1. **Wrong background color.** Using white instead of `#000000` fundamentally changes the brand personality.

2. **Accent color used as surface fill.** Flooding the page with `#ffffff` destroys the signal-to-noise ratio that makes the accent meaningful.

3. **Missing typographic hierarchy.** Without clear weight contrast between headings and body, the design loses its structure.

4. **Light mode default when dark is the native state.** The dark atmosphere IS the brand identity.

5. **Generic design system tokens replacing brand-specific values.** Every color, font, and spacing value carries brand meaning.
