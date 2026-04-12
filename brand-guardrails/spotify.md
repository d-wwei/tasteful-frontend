# Spotify -- Design Guardrails

## Do's (10 items)

1. **Use near-black backgrounds (`#121212`-`#1f1f1f`) for all primary surfaces.** Depth through shade variation is the foundation. Verify: page background is `#121212`, card surfaces are `#181818` or `#1f1f1f`, never lighter than `#252525`.

2. **Apply Spotify Green (`#1ed760`) only for play controls, active states, and primary CTAs.** It is the single functional accent. Verify: `#1ed760` appears only on play buttons, active indicators, and primary CTA buttons.

3. **Use pill shape (9999px) for navigation pills and small buttons, 500px for large buttons, 50% for circular controls.** The rounded geometry is core identity. Verify: all buttons use pill or circle radius, never standard 4-8px rounding.

4. **Apply uppercase + wide letter-spacing (1.4px-2px) on all button labels.** This creates the systematic "label" voice. Verify: button text uses `text-transform: uppercase` and `letter-spacing` of 1.4px or 2px.

5. **Use heavy shadows (0.3-0.5 opacity) for elevated elements on dark backgrounds.** Subtle shadows are invisible on dark surfaces. Verify: elevated cards, dropdowns, and menus use shadow opacity of at least 0.3.

6. **Maintain the bold/regular binary for typography.** Most text is 700 (bold) or 400 (regular). Verify: weight 600 appears sparingly, and no weights outside 400/600/700 are used.

7. **Use `#b3b3b3` (silver) for secondary and inactive text.** This muted tone creates hierarchy on dark surfaces. Verify: inactive nav items and secondary text use `#b3b3b3`, not brighter grays.

8. **Use `#000000` (black) for text on Spotify Green backgrounds.** Maximum contrast for the accent color. Verify: text on green buttons/surfaces is `#000000`, not white.

9. **Apply the inset border-shadow on input elements.** The combo `rgb(18,18,18) 0px 1px 0px, rgb(124,124,124) 0px 0px 0px 1px inset` creates a tactile recessed feel. Verify: search and text inputs use this specific shadow pattern.

10. **Keep typography compact (10px-24px range).** This is an app for scanning playlists, not a magazine. Verify: no text exceeds 24px, and most body/UI text is 14-16px.

## Don'ts (10 items)

1. **Do not use Spotify Green decoratively or on backgrounds.** It is functional-only: play, active, CTA. Violation: `background-color: #1ed760` on cards, sections, or decorative elements.

2. **Do not use light backgrounds for primary surfaces.** The dark immersion (`#121212`) is core identity. Violation: `#ffffff`, `#f5f5f5`, or any light color as a page or section background.

3. **Do not skip the pill/circle geometry on buttons.** Square or standard-radius buttons break the identity. Violation: `border-radius` < 50px on any button element (cards at 6-8px are separate).

4. **Do not use subtle shadows (< 0.2 opacity) on dark backgrounds.** They are invisible and useless. Violation: `box-shadow` with opacity < 0.2 as the primary elevation on dark surfaces.

5. **Do not add additional brand colors beyond the defined palette.** Green + achromatic grays is the complete system. Violation: introducing blues, purples, or warm colors for UI chrome.

6. **Do not use relaxed line-heights on UI text.** Spotify's typography is compact and dense. Violation: `line-height` > 1.5 on nav, button, or card text.

7. **Do not expose raw gray borders on dark surfaces.** Use shadow-based or inset borders instead. Violation: `border: 1px solid #333` or any visible solid border on cards.

8. **Do not use lowercase button labels.** All buttons use uppercase for the systematic label voice. Violation: button text without `text-transform: uppercase`.

9. **Do not use thin letter-spacing on buttons.** Wide tracking (1.4px+) is what separates button labels from content text. Violation: `letter-spacing: normal` or `letter-spacing` < 1px on button text.

10. **Do not use display-size text (> 24px).** The compact type system caps at 24px for section titles. Violation: any text above 24px in a standard UI context (marketing heroes may be an exception with explicit justification).

## Critical Violations (5 items)

1. **Light-mode page background.** Spotify's dark cocoon (`#121212`) is not a dark theme on a light design -- it IS the design. Rendering the UI on white fundamentally misrepresents the brand and destroys the immersive listening environment.

2. **Spotify Green used as a decorative surface color.** The power of `#1ed760` comes from its extreme restraint -- it appears only on play buttons and active states. Spreading it across backgrounds collapses the signal-to-noise ratio.

3. **Standard-radius buttons instead of pills/circles.** The pill (9999px) and circle (50%) geometry creates the premium audio device feel. Standard 8px-radius buttons make Spotify look like generic SaaS.

4. **Lowercase button labels without wide tracking.** Uppercase + 1.4px+ letter-spacing creates the systematic "label" voice that distinguishes interactive elements from content. Without it, buttons lose their identity.

5. **Subtle shadows on dark backgrounds.** On near-black surfaces, 0.05-0.1 opacity shadows are literally invisible. Using them means elevation doesn't exist. Heavy shadows (0.3-0.5) are required for the "floating in darkness" effect.
