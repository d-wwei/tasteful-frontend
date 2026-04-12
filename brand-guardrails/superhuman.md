# Superhuman -- Design Guardrails

## Do's (10 items)

1. **Use `#1B1B1B` (Cod Gray) as the primary page background.**
   This near-black void is the canvas that makes the five-shade gray elevation system work. Lighter grays (`#232323`, `#2C2C2C`, `#353535`, `#3E3E3E`) float above it — proximity to the user maps to surface lightness.
   Every elevation step is roughly +9-10 in hex value, creating a physical-light metaphor where nearer surfaces catch more light.
   Verify: `body` or main wrapper `background-color` is `#1B1B1B`, and every elevated surface uses one of the four lighter shades — never an arbitrary dark color.

2. **Use system font stacks exclusively — zero network font requests.**
   The font stack is `-apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif`.
   No Google Fonts, no CDN-loaded typefaces, no `@font-face` declarations for display or body text.
   Superhuman's speed identity depends on zero font network requests and sub-100ms text render. The system font IS the brand font.
   Verify: no `<link>` tags loading external fonts; no `@import url()` in CSS; no custom font files in the project; no references to Inter, Helvetica Neue, Roboto, or other web fonts.

3. **Reserve `#6C56F0` (Superhuman Purple) strictly for interactive states and primary CTAs.**
   It appears on: primary buttons, keyboard focus rings, selected/active indicators, progress bars, and the caret in inputs. It does NOT appear on: backgrounds, section fills, decorative gradients, text color, or icons in their default state.
   Verify: count purple-colored elements visible on any given screen — if more than 3 non-interactive elements use `#6C56F0`, the accent is diluted past the point of signal.

4. **Implement keyboard focus with the double-ring glow pattern on every focusable element.**
   Every focusable element must show `box-shadow: 0 0 0 2px #1B1B1B, 0 0 0 4px #6C56F0` on `:focus-visible`.
   The dark inner ring (matching the page background) ensures the purple glow reads against any surface shade in the elevation system.
   Add the optional outer glow `0 0 8px rgba(108,86,240,0.25)` for high-priority focus targets like the command palette input.
   Verify: tab through every interactive element — each must show the purple glow ring; none may rely solely on browser default outlines or have no visible focus indicator at all.

5. **Use opacity-based text hierarchy on dark surfaces.**
   Primary text is `#FFFFFF`. Secondary is `rgba(255,255,255,0.65)`. Tertiary is `rgba(255,255,255,0.40)`.
   This follows Superhuman's published dark-theme research — opacity-based hierarchy reduces eye strain in low-light environments more effectively than distinct gray hex values, because the text color adapts naturally when the surface shade changes.
   Verify: body text, preview snippets, and timestamps use the 65% or 40% opacity values, not hard-coded grays like `#A0A0B8` or `#999999`.
   Inspect with devtools to confirm `rgba` values are used, not resolved hex equivalents.

6. **Keep inbox rows at 44px height with tight horizontal padding (8-16px).**
   This density defines the information architecture of a professional email tool — every pixel of vertical space is a message the user can see without scrolling.
   The 44px row also aligns with common touch target minimums for mobile, making it the sweet spot between density and usability.
   Verify: list items in email-like layouts use exactly 44px height; internal horizontal padding stays in the 8-16px range.
   Vertical padding within the row is 0 — height is controlled by the container, not padding.

7. **Use a 4px base grid for all spacing values.**
   Every padding, margin, and gap must be a multiple of 4px: 2, 4, 8, 12, 16, 20, 24, 32, 48. Superhuman's density demands a tighter grid than the common 8px base used in marketing sites. The 4px grid allows the fine-grained spacing control needed for email-density interfaces.
   Verify: inspect computed styles — no spacing value should be an odd number (except 1px borders) or a non-multiple of 4. Common violations: 5px padding, 10px gaps, 15px margins.

8. **Apply weight 500 to interactive labels and weight 600 to headings only.**
   Unread sender names, active nav items, and button labels use 500. Section headings and display text use 600. Body text and secondary content use 400. This three-tier weight system creates hierarchy without the heaviness that comes from 700+ weights.
   Verify: no element in the UI uses `font-weight: 700`, `font-weight: bold`, or `<b>` / `<strong>` in structural chrome. Email content authored by users is exempt from this rule.

9. **Make transitions sub-150ms with snap easing for all micro-interactions.**
   The default interaction timing is `100ms cubic-bezier(0.2, 0, 0, 1)` — a fast-attack, no-bounce curve.
   Hover states use 50-100ms. Focus rings use 100ms. Panel and modal transitions get up to 250ms with smooth easing `cubic-bezier(0.16, 1, 0.3, 1)`. Nothing else gets more time.
   Verify: no `transition-duration` exceeds 250ms; no easing uses `ease-in-out` or `ease` (these feel sluggish at Superhuman's speed standard).
   No `animation-duration` exceeds 400ms except the single inbox-zero celebration.

10. **Display keyboard shortcut hints using monospace at 11px with a badge container.**
    Keyboard shortcut badges use `'SF Mono', ui-monospace, monospace` at 11px, weight 500, letter-spacing 0.06em.
    Badge styling: background `#2C2C2C`, padding 2px 6px, border-radius 4px, border 1px solid `rgba(255,255,255,0.10)`.
    They appear next to actions, in the command palette results, and as inline hints in tooltips.
    Verify: shortcut hints render in monospace — never in the body sans-serif.
    The badge background is one of the five elevation grays; the border uses the default border opacity token.

## Don'ts (10 items)

1. **Do not use light backgrounds for any primary surface.**
   Superhuman is dark-native — there is no light mode, no theme toggle, no "inverted section" pattern.
   The five-shade gray system (`#1B1B1B` through `#3E3E3E`) is the complete surface palette.
   Violation: any `background-color` lighter than `#3E3E3E` on a structural element.
   The only exception is text-on-accent scenarios inside small elements like badges or buttons where white text sits on `#6C56F0`.

2. **Do not load custom fonts via CDN, Google Fonts, or `@font-face`.**
   Every external font request adds 100-400ms latency and directly contradicts the speed-first brand promise. Superhuman users chose this product for sub-100ms responsiveness — adding font loading latency is like putting a speed bump in a race car.
   Violation: any `<link rel="stylesheet" href="https://fonts.googleapis.com/...">`, any `@font-face` block for display or body text, any reference to Inter, Helvetica Neue, Roboto, or other web fonts in the stylesheet.

3. **Do not use `#6C56F0` as a decorative background fill or gradient.**
   Purple sections, purple hero backgrounds, purple-to-black gradients as decorative surfaces — all violate the accent's signal role. The purple must remain surgical.
   Violation: any `background-color: #6C56F0` on a container larger than a button (> ~48px height and > ~200px width); any `linear-gradient` or `radial-gradient` using `#6C56F0` as a dominant color covering a significant area.

4. **Do not use drop shadows to create elevation on non-overlay elements.**
   Superhuman achieves depth through background color steps, not shadow stacks. Shadows are reserved exclusively for overlays: modals, the command palette, tooltips, and dropdown menus. Cards, panels, sidebar, and list items NEVER get box-shadow for elevation.
   Violation: `box-shadow` with Y-offset > 0 on cards, panels, sidebar panes, or list items. These elements should differ from their parent only via background color.

5. **Do not use visible borders on inbox rows or list items.**
   Row separation uses `rgba(255,255,255,0.06)` — a hairline that is felt at the perceptual level, not consciously seen. This is intentional: visible row borders create visual noise in a list that a user scans hundreds of times per day.
   Violation: any border on list/row items with opacity > 0.10; any border using a solid hex color (like `#333`, `#444`, `#555`); any `border-width` > 1px on row-like elements.

6. **Do not exceed 250ms for any transition or 400ms for any animation.**
   The app feels instantaneous because nothing lingers in mid-transition. A 300ms fade feels laggy in this speed context. The single exception is the inbox-zero celebration animation, which may use spring easing up to 400ms because it is a deliberate moment of delight.
   Violation: any `transition-duration` > 250ms; any `animation-duration` > 400ms (except inbox-zero); any use of `ease-in-out` or `ease` as easing functions; any `@keyframes` animation that visibly slides, bounces, or pulses.

7. **Do not use monospace fonts for non-keyboard-shortcut content.**
   `SF Mono` and `ui-monospace` appear exclusively in keyboard hint badges and inline code within email bodies. They never appear as headings, labels, timestamps, body text, or decorative text.
   Violation: monospace font family used for any element that is not a keyboard shortcut badge or a `<code>` / `<pre>` block inside email content. Timestamps especially must NOT be monospace — they use the system sans at 11px.

8. **Do not use weight 700, `bold`, or `<strong>` in UI chrome.**
   The weight ceiling is 600 (semibold) for headings. Visual emphasis comes from size, color, and opacity contrast — not from heavier strokes. The three-tier weight system (400/500/600) is sufficient for all hierarchy needs.
   Violation: any `font-weight: 700`, `font-weight: bold`, `<b>`, or `<strong>` in navigation, buttons, cards, panels, or any structural UI element. User-authored email content is exempt.

9. **Do not add rounded corners larger than 12px on functional UI elements.**
   The radius scale is: buttons 6px, cards/modals 8px, command palette 12px. Large radii (16px, 20px, 32px) belong to marketing contexts — never to the app interface, which must feel sharp and professional.
   Violation: `border-radius: 16px` or higher on buttons, inputs, list items, panels, or modals within the application UI. The `9999px` pill radius is exclusively for avatars, status dots, and toggle switches.

10. **Do not use colored text for status messages when a subtle background tint is available.**
    Superhuman communicates error, success, warning, and info states via `rgba(status-color, 0.12)` background tints paired with small colored icons or dots. Body text inside status messages stays `#FFFFFF` or `rgba(255,255,255,0.65)` — never the status color itself.
    Violation: body text with `color: #F04438` (error) or `color: #32D583` (success) for status messages. The correct pattern is: neutral-colored text on a 12%-opacity tinted background, with a small colored dot or icon as the status signal.

## Critical Violations (5 items)

1. **Light or white page background.**
   Using `#FFFFFF`, `#F5F5F5`, `#FAFAFA`, or any luminance above `#3E3E3E` as the primary surface destroys the five-shade elevation system and the product's entire visual identity.
   Dark is not a theme option — it is the only mode. There is no "light Superhuman."
   This violation is unrecoverable without full redesign because every color, opacity, shadow, and contrast ratio in the system is calibrated against the dark canvas.

2. **External font loading of any kind.**
   A `<link>` to Google Fonts, a `@font-face` declaration for body/display text, or any custom font file contradicts the core speed promise at the identity level.
   Superhuman users pay premium pricing for sub-100ms responsiveness.
   Adding 200ms+ of font loading — visible as FOUT or layout shift — is the design equivalent of false advertising.
   The system font stack (`-apple-system, BlinkMacSystemFont, system-ui, sans-serif`) is not a fallback. It IS the brand typography.

3. **Purple used as a surface color, gradient background, or decorative fill.**
   Flooding a hero section, sidebar, card background, or section with `#6C56F0` collapses the signal-to-noise ratio that makes the accent meaningful.
   When purple is everywhere, it indicates nothing.
   The accent must remain scarce — appearing only on interactive elements (buttons, focus rings, active indicators) and nowhere else.
   If you squint at the screen and see purple as a dominant color rather than a punctuation mark, the design is broken.

4. **Missing or incorrect keyboard focus indicators.**
   If tabbing through interactive elements produces no visible focus state — or produces the browser's default blue outline instead of the purple glow ring — the component fails Superhuman's core interaction paradigm.
   The keyboard IS the primary input device, not a secondary accessibility concern.
   Every focusable element must show the double-ring pattern: `box-shadow: 0 0 0 2px #1B1B1B, 0 0 0 4px #6C56F0` on `:focus-visible`.
   The dark gap ring between the element and the purple glow is not decorative — it ensures visibility against all five surface shades.

5. **Slow transitions (> 300ms) or decorative animations.**
   Slide-in panels, bounce effects, parallax scrolling, loading spinners that play for dramatic effect, fade-in-up entrance animations — all violate the speed-as-identity principle.
   Superhuman feels fast because nothing moves slowly enough to be perceived as movement.
   Interactions are state changes, not performances.
   Maximum 100ms for hover/focus micro-interactions, 150ms for panel transitions, 250ms for modals, and nothing else.
   If a user can consciously observe an animation playing (rather than perceiving an instant state change), it is too slow for this brand.
