# BMW -- Design Guardrails

## Do's (10 items)

1. **Use pure white (`#ffffff`) as the primary page background.**
   BMW's digital presence mimics the clinical brightness of a dealership showroom floor —
   daylight LEDs on white surfaces. No cream, no warm gray, no off-white.
   Verify: `<body>` or main page wrapper has `background-color: #ffffff`.

2. **Use 0px border-radius on all cards, buttons, inputs, and image containers.**
   Zero-radius angular geometry is the single most recognizable characteristic of BMW's
   digital design language. It signals precision engineering — no softness, no rounding,
   no compromise. The sole exception is pill-shaped badges at `9999px`.
   Verify: every `border-radius` value in the component tree is `0px`.

3. **Use weight 300 (Light) for display-level headlines at 36px and above.**
   The thin-stroked, airy headline at large scale is BMW's typographic signature — it
   communicates confidence without raising its voice. This light weight at cinematic
   size is what separates BMW digital from every other automotive brand's bold-first approach.
   Verify: any headline at 36px or larger uses `font-weight: 300`, never 400, 500, or 600.

4. **Restrict BMW Blue (`#1c69d4`) to primary CTAs, active navigation indicators, and 2px accent hairlines.**
   Blue is the signal color: it marks actionable elements and nothing else. When blue is
   scarce, every blue element commands attention. A 2px blue top-border on a metric card
   is the maximum decorative use.
   Verify: `#1c69d4` appears only on interactive elements, progress indicators, and thin
   accent borders — never on surface fills, background blocks, or decorative shapes.

5. **Use uppercase, weight 700, 11px, letter-spacing 1.5px overline labels to categorize content blocks.**
   This overline pattern ("THE NEW BMW iX", "SPECIFICATIONS", "PERFORMANCE") is how BMW
   structures information hierarchy across every digital touchpoint. The overline anchors
   the reader before the main heading, creating a category > title > description flow.
   Verify: overline elements are `#757575` on light / `#a0a0a0` on dark,
   text-transform uppercase, exactly 11px with 1.5px tracking.

6. **Use Helvetica as the primary fallback typeface, followed by Arial.**
   BMWTypeNext is proprietary and unavailable to most systems. The fallback chain must be
   `'BMWTypeNext', Helvetica, Arial, sans-serif`. Helvetica matches BMWTypeNext's
   geometric proportions far better than system-ui or Inter.
   Verify: no `system-ui`, `San Francisco`, `Segoe UI`, or `Inter` appears in the font stack.

7. **Use Carbon Black (`#1a1a1a`) for dark sections with `#333333` borders and `#a0a0a0` secondary text.**
   BMW's dark mode is not a simple inversion. It has its own specific gray palette that
   avoids cool-blue or warm-brown tints. Dark heroes and feature showcases use this
   cinematic palette to frame vehicle photography and bold metrics.
   Verify: dark section backgrounds are `#1a1a1a`, dividers `#333333`,
   secondary text `#a0a0a0`, primary text `#ffffff`.

8. **Keep resting-state cards flat with zero shadow.**
   Elevation is reserved for interactive states (hover) and overlay elements (modals,
   dropdowns). A BMW card at rest sits flush against the surface, separated by a 1px
   `#e0e0e0` border. Shadow only appears on `:hover`, communicating "this is now active."
   Verify: cards have `box-shadow: none` by default; shadow appears only in hover or
   elevated overlay states.

9. **Space all elements on an 8px grid and set the container max-width to 1440px.**
   BMW's layouts are wider than most digital brands — cinematic and panoramic, like a
   widescreen automotive commercial. Content text blocks within that container are
   constrained to ~960px for readability.
   Verify: padding, margin, and gap values are multiples of 8 (4px for micro spacing);
   the outer container is 1440px; text content areas do not exceed 960px.

10. **Make all CTA buttons uppercase, 14px, weight 700, letter-spacing 0.5px, 0px radius, with generous padding (14px 32px).**
    BMW's button style is industrial — a precise rectangle with bold uppercase text.
    Primary fills BMW Blue; secondary uses a 1px solid border with transparent background.
    On hover, the secondary inverts (fills dark, text goes white).
    Verify: no sentence-case, no rounded corners, no lowercase text on any CTA.

## Don'ts (10 items)

1. **Do not round corners on cards, buttons, or containers.**
   BMW's entire design language is built on sharp angular geometry. A rounded corner —
   even 4px — breaks the engineered precision and makes the component look like it
   belongs to a fintech app, not a German automotive brand.
   Violation: any `border-radius` value between 1px and 9998px on cards, buttons, or inputs.

2. **Do not use BMW Blue (`#1c69d4`) as a background fill, card surface, or large decorative area.**
   Blue is a signal, not a surface. When blue covers more than ~5% of visible pixel area,
   it becomes noise instead of signal, and every CTA loses its magnetic pull.
   Violation: `background-color: #1c69d4` on any element larger than a button or 2px accent strip.

3. **Do not use warm-tinted backgrounds (cream, ivory, beige, parchment).**
   BMW's white is pure `#ffffff`, not `#f5f4ed` or `#faf9f5`. Warm backgrounds evoke
   editorial or hospitality brands, not precision engineering. The showroom is lit by
   daylight LEDs, not candles.
   Violation: any primary surface color with a yellow, brown, or warm undertone.

4. **Do not use display headlines at weight 400+ (Regular or above) at 36px and larger.**
   Bold or medium-weight large type reads as shouty and aggressive. BMW's signature is
   confidence at low volume — the Light (300) weight at display scale says "we do not
   need to shout because the engineering speaks for itself."
   Violation: `font-weight: 400`, `500`, `600`, or `700` on any headline 36px or larger.

5. **Do not load BMWTypeNext from Google Fonts or any external CDN.**
   BMWTypeNext is a proprietary typeface licensed exclusively to BMW Group. It is not
   available on Google Fonts, Adobe Fonts, or any public CDN. Any link claiming to serve
   it is either pirated or a different font entirely.
   Violation: any `<link>` tag or `@import` referencing public font services for BMWTypeNext.

6. **Do not use system-ui, San Francisco, Segoe UI, or Inter as fallback fonts.**
   These typefaces have distinct geometric or humanist characteristics that clash with
   BMWTypeNext's proportions. San Francisco is rounded and humanist; Segoe UI is
   distinctly Microsoft. Helvetica is the closest visual match.
   Violation: `system-ui`, `-apple-system` as primary fallback, `Inter`, or `Segoe UI`
   in the font-family declaration.

7. **Do not apply heavy drop shadows or material-design-style elevation layers.**
   BMW's depth model is minimal — flat surfaces with 1px borders at rest, surgical
   micro-shadows on hover. Stacked shadow layers feel like Google Material or iOS,
   not automotive precision.
   Violation: any shadow with opacity > 0.10, blur-radius > 32px, or multiple shadow
   layers on a resting-state element.

8. **Do not use sentence-case or lowercase text on CTA buttons.**
   BMW CTAs are always uppercase with expanded letter-spacing. Sentence-case buttons
   ("Configure now") look casual and break the industrial aesthetic. The uppercase
   treatment is part of the engineering-document visual language.
   Violation: any primary or secondary CTA button text without `text-transform: uppercase`.

9. **Do not introduce additional accent colors beyond the defined palette.**
   BMW's digital palette is deliberately limited: BMW Blue is the only chromatic accent.
   Adding purple highlights, teal accents, or gradient fills turns the interface into a
   consumer tech product. Error, success, and warning states are the sole exceptions.
   Violation: any hue outside the defined token palette appearing in the UI chrome.

10. **Do not use more than two type weights visible simultaneously in one viewport fold.**
    BMW's typographic system uses three weights total (300, 400, 700), but any single
    view should show at most two. Typical pairs: 300+400 for editorial sections,
    400+700 for data-heavy sections. Three visible weights create noise.
    Violation: weight 300 headings, weight 400 body, and weight 700 buttons all competing
    in the same fold without clear spatial separation.

## Critical Violations (5 items)

1. **Rounded corners on primary UI elements.**
   This is the single fastest way to destroy BMW's digital identity. The zero-radius
   philosophy is not a stylistic preference — it is the geometric DNA of the brand. A BMW
   interface with 8px rounded cards is visually indistinguishable from a generic SaaS
   dashboard. Every card, every button, every input must be razor-sharp at 0px.
   Audit every `border-radius` value in the stylesheet before shipping.

2. **Bold or semibold display headlines.**
   Weight 300 at display scale is what makes BMW typography recognizable across every
   touchpoint — from dealership digital signage to the bmw.com hero. Changing it to 600
   or 700 makes the design look like a sports news site, not a premium automotive brand.
   The light weight communicates engineering confidence: the message is clear enough that
   it does not need to shout.

3. **BMW Blue used as a surface color instead of an interaction signal.**
   A blue hero background, a blue card, or a blue sidebar collapses the entire signal
   hierarchy. When everything is blue, nothing is blue. BMW Blue must remain scarce — the
   one flash of color that draws the eye to exactly where the user should act next. If the
   blue area exceeds a button or a 2px accent line, it is a critical violation.

4. **Warm or tinted page backgrounds instead of pure white.**
   BMW's showroom aesthetic depends on clinical white surfaces. Warm cream (`#f5f4ed`),
   ivory (`#faf9f5`), or any yellowish tint instantly shifts the perception from
   "German engineering lab" to "artisan coffee shop." The only acceptable page backgrounds
   are `#ffffff` (light sections) and `#1a1a1a` (dark cinematic sections).

5. **Loading BMWTypeNext from Google Fonts or any unauthorized source.**
   This is both a brand integrity and legal issue. BMWTypeNext is proprietary. Any
   external font link pretending to serve it either serves a different font (breaking
   visual consistency) or serves a pirated copy (creating legal liability). The correct
   approach: include BMWTypeNext via self-hosted files in BMW-authorized projects, and
   rely on the Helvetica/Arial fallback chain everywhere else.
