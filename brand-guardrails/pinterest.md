# Pinterest -- Design Guardrails

## Do's (10 items)

1. **Use `#ffffff` as the primary page background.**
   Pinterest's canvas is pure white because the content IS the color. User-generated
   imagery -- photography, illustrations, recipes, interiors -- provides all the
   visual richness. The white page ensures every pin image pops at full saturation
   without competing with colored chrome.
   Verify: `<body>` or main page wrapper uses `background-color: #ffffff`. No cream,
   no off-white, no warm gray as the primary surface.

2. **Reserve `#e60023` exclusively for Save buttons and primary CTAs.**
   Pinterest Red is the highest-signal color in the entire product. It means "save
   this" or "do this now." The entire interaction model -- browse, discover, save --
   depends on red being instantly recognizable as the action trigger.
   Verify: the red accent appears only on Save buttons, primary action buttons,
   error states, and the logo. Count visible red elements -- if more than two are
   simultaneously visible in a viewport, red has leaked into decoration.

3. **Use `#111111` for primary text -- not `#333333`, not `#000000`.**
   Gestalt's near-black is a deliberate choice. `#000000` is too harsh against the
   white canvas and creates uncomfortable contrast for extended reading. `#333333`
   is too light and reads as secondary text. `#111111` hits the balance: definitive
   but not aggressive, with neutral (not warm, not cool) undertone.
   Verify: all `<h1>` through `<h6>` elements and body text use `#111111`.

4. **Apply border-radius 16px to all pin cards, content containers, modals, and sheets.**
   The 16px radius is Pinterest's geometric signature -- soft enough to feel warm
   and approachable, structured enough to not look like a toy. This specific value
   (Gestalt rounding-400) is deliberate: 8px feels too corporate, 24px too playful.
   16px is the center of Pinterest's visual personality.
   Verify: every card-like element uses exactly 16px radius. Pin cards, board
   thumbnails, sheet modals, and content containers all share this value.

5. **Use pill shape (border-radius 999px) for primary and secondary buttons.**
   The fully-rounded pill button is Pinterest's most recognizable interactive element.
   It distinguishes buttons from cards (which use 16px corners) and creates a clear
   visual grammar: pills are for actions, rounded rectangles are for content.
   The Save button, Follow button, and all prominent CTAs use this shape.
   Verify: primary and secondary action buttons use `border-radius: 999px`. Only
   tertiary/inline text buttons or icon-only buttons skip the pill.

6. **Implement masonry (staggered) grid layout for any collection of visual content.**
   The variable-height pin grid is Pinterest's brand signature and its most
   recognizable UI pattern globally. Each pin preserves its image's natural aspect
   ratio, creating an organic, magazine-like visual rhythm. This is not a layout
   preference -- it is the product's identity.
   Verify: use CSS columns or absolute positioning, 16px gutter, responsive column
   count (2 on mobile, 3-4 on tablet, 5-7 on desktop). No uniform-height grids
   where pin-like visual content is being displayed.

7. **Show pin action buttons only on hover (desktop) or long-press (mobile).**
   Save button, board selector, and more-options icon appear on mouseover with a
   semi-transparent dark overlay (`rgba(0,0,0,0.4)`) over the pin image. At rest,
   pins are clean images with minimal text below. This hover-reveal pattern keeps
   the grid visually clean and lets the content breathe.
   Verify: pin cards at rest show no action buttons overlaying the image. Hover
   state reveals the `#e60023` Save button top-right with a dark scrim behind it.

8. **Use the Gestalt 4px spacing grid consistently.**
   Gestalt's base spatial unit is 4px, not 8px. All padding, margin, and gap values
   must be multiples of 4. The common scale: 4, 8, 12, 16, 24, 32, 48, 64px.
   This tight grid creates the precise, app-like feel that distinguishes Pinterest
   from more editorial layouts.
   Verify: no spacing values like 5px, 10px, 15px, 18px, or 22px appear. Every
   value divides evenly by 4.

9. **Limit the type scale to six Gestalt sizes: 12, 14, 16, 20, 28, 36px.**
   Pinterest deliberately caps display text at 36px to keep focus on visual content.
   The platform's purpose is visual discovery -- typography supports but never
   dominates. This tight, six-step scale prevents typographic sprawl and keeps
   hierarchy clean with minimal variation.
   Verify: no `font-size` values outside the set {12, 14, 16, 20, 28, 36}px. If
   you find 48px or 64px headings, they violate the Gestalt scale.

10. **Use exactly three font weights: 400 (body), 600 (emphasis), 700 (headings).**
    The weight triad creates hierarchy without visual noise. 400 handles body text,
    descriptions, and metadata. 600 handles subheadings, button labels, and
    in-context emphasis. 700 handles display headings and page titles.
    No in-between values exist in the system.
    Verify: no `font-weight: 300`, `500`, `800`, or `900` values. The three-weight
    system is complete as defined.

## Don'ts (10 items)

1. **Do not use dark or colored backgrounds for primary surfaces.**
   Pinterest is a white-canvas product. A Pinterest-branded page with a dark primary
   surface, or a colored wash (beige, cream, blue, pastel), fundamentally alters the
   brand identity. The white background is not a neutral default -- it is an active
   design decision that makes imagery the protagonist.
   Verify: `<body>` background is `#ffffff`. Dark mode exists as a user preference
   but is not the default brand identity.

2. **Do not apply `#e60023` as a background fill, decorative surface, or gradient base.**
   Using Pinterest Red as a card background, hero section fill, or gradient component
   destroys the signal-to-noise ratio that makes the Save button meaningful. If the
   background is red and the Save button is red, the button disappears. The entire
   browse-and-save interaction model breaks.
   Verify: `#e60023` never appears as a `background-color` on any element larger
   than a button.

3. **Do not use uniform-height grids where masonry layout is appropriate.**
   A Pinterest-branded content grid that forces all items to the same height
   contradicts the platform's core visual principle. Images have natural aspect
   ratios -- a portrait photo, a landscape recipe image, and a square illustration
   should each display at their own proportions. Forcing uniform height crops
   content and removes the organic visual rhythm that defines Pinterest.
   Verify: if displaying pin-like image content in a grid, heights vary per item.

4. **Do not use border-radius less than 8px on any card or button.**
   Pinterest's geometry is soft and rounded. Corners below 8px (especially 0px, 2px,
   4px) feel sharp, industrial, and angular -- the opposite of Pinterest's warm,
   approachable identity. Even utility elements like inputs and dropdowns get at
   least 8px. The only 0px radius permitted is for the page edge itself.
   Verify: no `border-radius: 0`, `2px`, or `4px` on cards, buttons, or inputs.

5. **Do not use heavyweight fonts (800+) or thin/light weights (100-300).**
   Gestalt's three-weight system (400/600/700) is the complete typographic palette.
   Ultra-bold creates aggressive visual weight that competes with imagery. Ultra-light
   creates fragile, hard-to-read text that undermines the approachable feel.
   Pinterest Sans was designed for the 400-700 range specifically.
   Verify: no `font-weight` values outside the {400, 600, 700} triad.

6. **Do not introduce saturated accent colors beyond the defined palette.**
   Pinterest's chrome is neutral (black, white, gray) with red as the sole chromatic
   accent in the UI. Adding bright blues, greens, purples, or oranges to the UI
   chrome -- as button colors, card accents, or decorative borders -- breaks the
   strict color restraint that makes the red accent powerful.
   Semantic status colors (`#008753` green, `#0074e8` blue, `#bd5b00` orange)
   are for inline status indicators only, never decorative elements.

7. **Do not show persistent action buttons on pin cards.**
   The Save button, board selector, and options menu must appear only on hover
   (desktop) or long-press (mobile). Permanently visible action chrome over every
   pin image creates visual noise that competes with the content. The masonry grid
   should read as a wall of images, not a wall of buttons.
   Verify: pin cards in their default (non-hovered) state display no overlaid UI.

8. **Do not use font sizes between Gestalt scale steps.**
   Values like 13px, 15px, 17px, 18px, 22px, 24px, or 32px do not exist in the
   Gestalt type scale. The six-step system (12/14/16/20/28/36) was designed to
   create clear hierarchy with minimal steps. Half-steps weaken the hierarchy by
   creating indistinguishable size differences that confuse rather than guide.
   Verify: every `font-size` value maps to one of the six Gestalt steps.

9. **Do not use heavy drop shadows at rest on pin cards.**
   Pin cards sit flat on the white canvas with no shadow by default. Elevation
   appears only on hover (`0 2px 8px rgba(0,0,0,0.06)`) or for overlapping UI
   (modals, sheets). Persistent heavy shadows on every card in the masonry grid
   create a cluttered, noisy page that fights the clean, content-first aesthetic.
   Verify: pin cards in their default state have no box-shadow. Shadow appears
   only on `:hover` with subtle values.

10. **Do not use the Pinterest logo or wordmark in non-brand colors.**
    The Pinterest logo renders in `#e60023` on light surfaces or `#ffffff` on dark
    surfaces. Never apply the logo in black, gray, blue, gradient, or any custom
    color. The red logo is legally protected and brand-specified -- deviation is not
    a design decision, it is a brand guidelines violation.
    Verify: any Pinterest logo usage is exactly `#e60023` or `#ffffff`.

## Critical Violations (5 items)

1. **Uniform-height grid instead of masonry layout for pin-like content.**
   The staggered, variable-height masonry grid is the single most recognizable
   element of Pinterest's visual identity worldwide. It is what makes a page "look
   like Pinterest" before any other element registers. Replacing it with a uniform
   grid of equal-height cards removes the brand signature entirely. This is not a
   layout preference -- it is the product. A Pinterest-branded page without masonry
   layout is like a map application without a map.

2. **Pinterest Red (`#e60023`) used as a surface fill or background color.**
   When red floods the page -- as hero background, card fill, section wash, or
   gradient base -- the Save button loses its meaning. The browse-and-save interaction
   model depends on red being the rarest, most attention-grabbing color on screen.
   A red background inverts this: everything screams, nothing signals. This is the
   most damaging color violation because it breaks the product's core interaction,
   not just its visual style.

3. **Sharp corners (< 8px radius) on cards or buttons.**
   Pinterest's soft 16px rounding on cards and 999px pills on buttons create the
   warm, friendly, approachable geometry that distinguishes it from angular
   enterprise and developer-tool UIs. Sharp corners collapse this identity into
   generic design. The roundness is not decorative -- it communicates that Pinterest
   is a place for creative inspiration, not a dashboard for data analysis.

4. **Wrong primary text color (`#333333` or `#000000` instead of `#111111`).**
   `#333333` is the most common error because many designers default to it. But
   Gestalt specifies `#111111` precisely. At 16px body text on white, the difference
   is visible: `#333` reads slightly washed, `#000` reads harsh, `#111` reads clean
   and confident. This extends to every heading and body element. Getting text color
   wrong shifts the entire visual tone of the page subtly but pervasively.

5. **Type scale exceeding 36px or using non-Gestalt sizes.**
   Gestalt deliberately caps the type scale at 36px to keep typography subordinate
   to visual content. Pinterest is an image-first platform -- a 48px or 64px headline
   elevates text above imagery, inverting the content hierarchy. The platform's
   purpose is visual discovery, not reading. If typography dominates the viewport,
   the design has fundamentally misunderstood what Pinterest is.
