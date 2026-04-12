# Figma -- Design Guardrails

## Do's (10 items)

1. **Use figmaSans with precise variable weight stops: 320, 330, 340, 450, 480, 540, 700.** These unusual intermediates create hierarchy through micro-differences. Verify: every `font-weight` value matches one of these stops, never standard values like 500 or 600.

2. **Enable `font-feature-settings: "kern"` on ALL text elements.** Kerning is structural, not optional. Verify: every text element includes `font-feature-settings: "kern"`.

3. **Keep the interface strictly black (`#000000`) and white (`#ffffff`).** Color exists only in product content, hero gradients, and embedded screenshots. Verify: no hex color other than `#000000`, `#ffffff`, or approved rgba overlays appears on interface chrome elements.

4. **Apply negative letter-spacing throughout.** Body text: -0.14px. Section headings: -0.96px. Display: -1.72px. Verify: no body or heading text has `letter-spacing: normal` or positive values (mono labels are the exception).

5. **Use pill (50px radius) geometry for all buttons and tabs.** Circle (50%) for icon buttons. Verify: all interactive elements use `border-radius: 50px` or `border-radius: 50%`, never standard 4-8px rounding.

6. **Use dashed 2px focus outlines on all interactive elements.** This echoes Figma editor selection handles. Verify: focus state uses `outline: dashed 2px #000000`, not solid outlines or box-shadow focus rings.

7. **Use figmaMono in uppercase with positive letter-spacing (0.54px+) for section labels.** Monospace labels are structural signposts. Verify: mono labels use `text-transform: uppercase` and positive `letter-spacing`, never lowercase or negative tracking.

8. **Set most body text at ultra-light weights (320-340).** The airy, ethereal reading experience is core to Figma's aesthetic. Verify: body and description text uses weight 320-340, not standard 400 regular.

9. **Use the hero gradient system for product showcases.** Vibrant multi-color gradients (green, yellow, purple, pink) belong in the hero and product sections. Verify: gradients appear only in designated showcase areas, not on UI chrome.

10. **Apply asymmetric vertical padding on pill buttons (8px top, 10px bottom).** This optical correction accounts for the pill shape. Verify: primary pill buttons use `padding: 8px 18px 10px`, not symmetric padding.

## Don'ts (10 items)

1. **Do not add colors to interface chrome elements.** The monochrome palette (`#000000` + `#ffffff`) is absolute. Violation: any color other than black, white, or approved rgba overlays on backgrounds, borders, or text that is not product content.

2. **Do not use standard font weights (400, 500, 600).** figmaSans has specific variable stops. Violation: `font-weight: 500` or `font-weight: 600` appearing on any text element.

3. **Do not use solid focus outlines.** The dashed pattern is the signature accessibility indicator. Violation: `outline-style: solid` on any interactive element's focus state.

4. **Do not use positive letter-spacing on body or heading text.** Only figmaMono labels get positive tracking. Violation: `letter-spacing` > 0 on any figmaSans text.

5. **Do not use sharp corners (< 50px) on buttons or tabs.** The pill/circle geometry is core identity. Violation: `border-radius` < 50px on any interactive button or tab (cards at 8px are separate).

6. **Do not increase body font weight above 450.** The light-weight aesthetic defines the reading experience. Violation: body text at weight 480, 540, or 700.

7. **Do not use heavy or colored shadows.** Figma uses shadows sparingly. Violation: `box-shadow` with opacity > 0.12 or any colored shadow (non-gray).

8. **Do not skip kerning.** Every text element requires `"kern"`. Violation: any text element missing `font-feature-settings: "kern"`.

9. **Do not use vibrant gradient colors on interface elements.** Gradients are reserved for hero/product showcases only. Violation: gradient background on buttons, cards, or navigation.

10. **Do not use traditional multi-layer shadow stacks.** Depth comes from background contrast (white on color), not shadow layering. Violation: more than one shadow layer on standard cards.

## Critical Violations (5 items)

1. **Colors in the interface chrome.** The strictly black-and-white interface is Figma's most distinctive visual constraint. Adding any hue to UI elements collapses the "gallery wall" metaphor that lets product content be the hero.

2. **Standard font weights instead of figmaSans variable stops.** Using 500 or 600 instead of 480 or 540 destroys the micro-weight precision that creates Figma's typographic sophistication. The unusual stops ARE the design system.

3. **Solid focus outlines replacing dashed.** The dashed 2px outline is a meta-design choice connecting the marketing website to the Figma editor's selection handles. Replacing it with solid outlines breaks this product-website link.

4. **Sharp-cornered buttons.** The pill (50px) and circle (50%) geometry creates the organic, tool-palette feel. Standard rounded-rectangle buttons make Figma look like every other SaaS product.

5. **Body text at regular weight (400+).** figmaSans at 320-340 creates the signature ethereal, airy reading experience. Regular-weight body text collapses the design into a generic sans-serif page.
