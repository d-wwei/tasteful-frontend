# Nike -- Design Guardrails

## Do's (10 items)

1. **Use `#111111` (Nike Black) for all primary text and dark buttons.** Deliberately not pure `#000000` for a fractionally softer reading experience. Verify: primary text uses `#111111`, not `#000000`.

2. **Use Nike Futura ND exclusively for large uppercase display headlines.** This custom condensed typeface with 0.90 line-height creates typographic shockwaves. Verify: display text uses Nike Futura ND with `text-transform: uppercase` and `line-height: 0.90`.

3. **Use Helvetica Now for all non-display text.** Helvetica Now Display Medium for headings, Helvetica Now Text for body. Verify: no body, button, or nav text uses Nike Futura ND.

4. **Use pill-shaped buttons (30px radius) for primary CTAs.** The smooth oval is the signature interactive element. Verify: primary action buttons use `border-radius: 30px`.

5. **Fill imagery edge-to-edge with zero border-radius.** Product and athletic photography must bleed to container edges. Verify: hero images and product photos have `border-radius: 0`.

6. **Maintain shadow-free, border-minimal elevation.** Differentiate surfaces through grey shifts (`#ffffff` → `#f5f5f5` → `#e5e5e5`). Verify: no prominent `box-shadow` on cards or containers.

7. **Use the Podium CDS grey scale for all neutral surfaces.** Snow (`#fafafa`), Light Gray (`#f5f5f5`), Hover Gray (`#e5e5e5`). Verify: secondary surfaces use these specific hex values.

8. **Keep the UI monochromatic — color comes from product only.** Interface chrome is strictly black/white/grey. Verify: no chromatic colors in backgrounds, borders, or UI text (semantic colors excepted).

9. **Use `#707072` for secondary text throughout.** This specific grey maintains consistent hierarchy. Verify: descriptions, metadata, and timestamps use `#707072`.

10. **Snap all measurements to the 8px grid.** Athletic discipline extends to spacing. Verify: padding, margin, and gap values are multiples of 4px or 8px.

## Don'ts (10 items)

1. **Do not use pure black (`#000000`) for text or buttons.** Nike Black is `#111111`. Violation: `color: #000000` or `background: #000000` on any interface element.

2. **Do not add chromatic colors to UI chrome.** Color exists only in product content and semantic states. Violation: blue, red, or any hue used on backgrounds, borders, or non-semantic UI elements.

3. **Do not apply border-radius to product photography.** Full-bleed is core. Violation: `border-radius` > 0 on hero images or product photos.

4. **Do not use drop shadows for elevation.** Surface differentiation uses grey shifts only. Violation: `box-shadow` with visible Y-offset and blur on cards or containers.

5. **Do not use Nike Futura ND for body text or buttons.** It is exclusively for massive uppercase display. Violation: Futura on any text below 48px or without uppercase transform.

6. **Do not use relaxed line-heights on display text.** 0.90 is the signature compression. Violation: `line-height` > 1.0 on Nike Futura ND display headings.

7. **Do not use sharp-cornered (< 8px) primary CTA buttons.** Pills (30px) are the standard. Violation: `border-radius: 4px` on primary action buttons.

8. **Do not introduce gradients on UI surfaces.** The design system is flat-color only. Violation: CSS gradients on buttons, cards, or section backgrounds.

9. **Do not use decorative type treatments.** No text shadows, text gradients, or ornamental typography. Violation: `text-shadow`, `background-clip: text`, or decorative font styling.

10. **Do not mix font families within the same hierarchy level.** Futura for display, Helvetica for everything else. Violation: Helvetica in a display context or Futura in a body context.

## Critical Violations (5 items)

1. **Colors in the UI chrome.** Nike's monochromatic interface lets product be the only color source. Adding hues to buttons, borders, or backgrounds destroys this retail cathedral aesthetic.

2. **Rounded product photography.** Full-bleed, edge-to-edge imagery with zero radius is how Nike fills every pixel with kinetic energy. Rounded corners add visual padding that undermines the impact.

3. **Nike Futura ND on body text.** The condensed display face at 0.90 line-height is designed for massive impact headlines. Using it for UI text creates illegible, cramped components.

4. **Drop shadows on cards.** Nike achieves elevation through grey surface shifts. Adding shadows introduces a design language foreign to the Podium CDS system.

5. **Relaxed display line-height (> 1.0).** The 0.90 line-height on Nike Futura ND creates the typographic shockwave that punches through hero imagery. Loosening it removes the athletic energy.
