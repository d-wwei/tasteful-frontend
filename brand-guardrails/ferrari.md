# Ferrari -- Design Guardrails

## Do's (10 items)

1. **Use `#0c0c0c` (Nero Profondo) as the primary page background.** This near-black tone is the cinematic canvas that makes photography and Rosso Corsa accents register with maximum impact. It is not pure `#000000` -- the slight warmth allows card surfaces (`#161616`) to layer on top with visible separation. Verify: the `<body>` or root wrapper background is `#0c0c0c`.

2. **Reserve Rosso Corsa (`#dc0000`) for primary CTAs, active navigation, and overline labels only.** This red is among the most recognized brand colors in the world. Its power comes from scarcity. It should appear on: primary action buttons, the active nav link, overline category tags above headlines, and thin 2px accent borders on key cards. Count the red: no more than 5% of any viewport should be Rosso Corsa. Verify: `#dc0000` never appears as a surface fill, card background, or decorative gradient.

3. **Use sharp edges (`border-radius: 0px`) on all buttons and minimal radius (4px max) on cards.** Ferrari's design language expresses engineering precision, not consumer-friendly softness. Buttons are always sharp-cornered rectangles. Cards use 4px radius at most. This is the visual equivalent of a machined carbon fiber component -- no unnecessary curves. Verify: no button element uses border-radius above 0px; no card element uses border-radius above 4px.

4. **Apply uppercase with wide letter-spacing for navigation, overlines, and button labels.** The Ferrari voice of authority uses `text-transform: uppercase` with `letter-spacing: 0.08em` to `0.12em` on all commanding text: nav links, overline tags, CTA labels, and category headers. This creates the same precision feel as dashboard gauges in a cockpit. Verify: every nav link and button label is uppercase with tracking >= 0.08em.

5. **Render performance data in monospace (`SF Mono`, `Roboto Mono`).** Horsepower, torque, 0-100 times, max speed, lap times, and weight figures must use the monospace font stack. This channels racing telemetry and distinguishes hard data from descriptive prose. The visual contrast between monospace numbers and sans-serif prose is a key brand differentiator. Verify: any numerical performance metric uses the `font-mono` token, never the display or body font.

6. **Use full-bleed photography with gradient overlays for text legibility.** Every hero section and vehicle showcase must have a bottom-to-top gradient: `linear-gradient(to top, #0c0c0c 0%, transparent 60%)`. This ensures white text is always legible over photography while preserving the cinematic quality of the image. Adjust the surface color in the gradient to match the underlying section background (e.g., `#161616` if text sits on a card). Verify: no text sits directly on an un-graded photograph.

7. **Maintain the two-tier width system: 1440px for photography, 1200px for content.** Vehicle imagery and hero sections use `max-width: 1440px` to fill wide displays edge-to-edge. Text content, card grids, and spec displays cap at `max-width: 1200px`. This hierarchy ensures the car always dominates the visual field. Verify: text containers never exceed 1200px; image containers can extend to 1440px.

8. **Use cinematic motion timings (350ms standard, 600-1000ms for reveals).** Ferrari's transitions feel like camera movements, not app UI snaps. Standard card hovers and state changes use 350ms with `cubic-bezier(0.25, 0.1, 0.25, 1)`. Hero image reveals and vehicle showcase animations use 600-1000ms with `cubic-bezier(0.16, 1, 0.3, 1)` for dramatic deceleration. Verify: no transition duration is below 200ms except micro-interactions (color shifts).

9. **Use heavier shadows than standard dark mode.** Shadows at `rgba(0,0,0,0.05)` are invisible on near-black surfaces. Cards need `rgba(0,0,0,0.40)` minimum for subtle lift. Modals and elevated panels use `rgba(0,0,0,0.60)`. The Rosso Corsa glow shadow (`0 0 20px -4px rgba(220,0,0,0.25)`) replaces generic blue focus indicators on primary CTAs. Verify: no shadow uses opacity below 0.20 on dark backgrounds.

10. **Use Oro Ferrari (`#c5a258`) exclusively for heritage and premium tier elements.** The gold accent represents the Scuderia legacy -- the Prancing Horse's original shield background. It appears on heritage badges, limited edition markers, and premium tier labels. Never combine gold and Rosso Corsa in the same element; they represent different brand lineages. Verify: `#c5a258` appears only on heritage-related elements, never on standard CTAs or decorative surfaces.

## Don'ts (10 items)

1. **Do not use light or white backgrounds for any primary surface.** Ferrari's digital identity is built on cinematic darkness. The darkest surface is `#0c0c0c`, the lightest permissible is `#1e1e1e` (Grigio Scuro). Any surface lighter than `#222222` breaks the immersive atmosphere. Violation: `background-color: #ffffff`, `#f5f5f5`, or any color with lightness above 15%.

2. **Do not flood surfaces with Rosso Corsa.** Using `#dc0000` as a card background, section fill, or large gradient area destroys the scarcity that makes the red powerful. Ferrari.com itself uses red on less than 3% of any viewport. The moment red becomes wallpaper, it loses its signal. Violation: any element larger than a button using `#dc0000` as its background fill.

3. **Do not use rounded corners (> 4px) on buttons or cards.** Pill-shaped buttons (`border-radius: 9999px`), generously rounded cards (8px, 12px, 16px), and soft interactive elements feel consumer-grade and antithetical to Ferrari's precision engineering aesthetic. The only exception is pill-shaped tags/badges for metadata. Violation: `border-radius` above 4px on any button, card, or container element.

4. **Do not load Google Fonts or web font CDNs.** Ferrari Sans is a proprietary typeface. The system falls back to `Helvetica Neue`, Helvetica, and Arial, which are already installed on virtually every device. Loading Inter, Roboto, Open Sans, or any Google Font introduces a foreign typographic personality that conflicts with the brand. Violation: any `@import url('fonts.googleapis.com/...')` or `<link>` to a font CDN.

5. **Do not use body text in uppercase.** Uppercase is reserved for commanding text only: navigation, overlines, button labels, and category tags. Paragraphs, descriptions, and editorial text must remain in sentence case. Uppercase body text reads as shouting and destroys the sophisticated editorial tone. Violation: `text-transform: uppercase` on any `<p>`, body-class, or description element.

6. **Do not mix gold and Rosso Corsa in the same component.** These represent different Ferrari lineages: gold is Scuderia heritage, red is racing performance. Placing both colors on the same button, card, or badge creates visual noise and dilutes both signals. Violation: any single component containing both `#dc0000` and `#c5a258` as active design elements.

7. **Do not use lightweight shadows on dark surfaces.** Shadows with opacity below 0.20 are functionally invisible on `#0c0c0c` backgrounds. If a shadow exists, it must be perceptible. Using imperceptible shadows adds CSS weight with zero visual benefit. Violation: `box-shadow` with `rgba(0,0,0,0.05)` or `rgba(0,0,0,0.08)` on dark backgrounds.

8. **Do not use decorative illustrations, emoji, or cartoon-style icons.** Ferrari's visual language is photographic and typographic. Icons must be thin-line strokes (1-1.5px weight) in white or `#999999`. Filled icons, gradient icons, 3D renders, and decorative illustrations have no place in the system. Violation: any filled/gradient icon, emoji character, or illustration-style graphic in the UI.

9. **Do not use snappy/instant transitions (< 150ms) for layout changes.** Quick, bouncy transitions feel like consumer app UI. Ferrari's motion should evoke cinema -- smooth, weighty, deliberate. Color-shift micro-interactions can be 100-150ms, but any element that moves, resizes, or appears/disappears needs 200ms minimum. Violation: `transition-duration` below 200ms on any layout, opacity, or transform animation.

10. **Do not place text directly on un-graded photography.** White text on a bright area of a vehicle photo becomes illegible. Every photographic background needs a gradient overlay or a semi-transparent dark panel (`rgba(0,0,0,0.85)`) behind the text. The overlay is not optional -- it is a structural requirement of the dark-on-photography system. Violation: any text element positioned over an `<img>` or `background-image` without an intermediary gradient or overlay.

## Critical Violations (5 items)

1. **Light or white page background instead of `#0c0c0c`.** The cinematic darkness is not a theme preference -- it IS the Ferrari digital identity. A white background makes Ferrari look like every other automotive configurator. The dark canvas is what makes the photography cinematic, the Rosso Corsa electric, and the vehicle the unmistakable hero. This single error collapses the entire brand.

2. **Rosso Corsa used as a surface fill or section background.** A red section, a red card, a red hero background -- any of these destroy the ratio that makes `#dc0000` meaningful. On ferrari.com, the red appears on thin buttons, single-word labels, and 2px accent lines. The restraint is the luxury. The moment red becomes abundant, Ferrari becomes a generic sports brand.

3. **Rounded, soft, consumer-grade buttons replacing sharp-edged Ferrari CTAs.** Pill buttons and large border-radius destroy the engineered-precision personality. Ferrari's buttons should feel like machined controls in a cockpit, not friendly consumer app elements. A 12px or 9999px border-radius on a CTA signals the wrong product category entirely.

4. **Google Fonts or non-system web fonts loaded instead of proprietary font stack.** Loading Inter, Roboto, or any Google Font introduces a completely different typographic DNA. Ferrari Sans has a specific geometric tension that Helvetica Neue approximates better than any webfont. The fallback stack is deliberate -- do not "improve" it with a generic sans-serif.

5. **Performance data rendered in body font instead of monospace.** When horsepower, torque, and lap times appear in the same sans-serif as marketing prose, the technical credibility evaporates. The monospace treatment is what makes "830 cv" feel like instrument data rather than advertising copy. This is the visual equivalent of a Ferrari dashboard vs. a brochure.
