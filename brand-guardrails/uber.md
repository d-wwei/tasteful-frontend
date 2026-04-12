# Uber -- Design Guardrails

## Do's (10 items)

1. **Use `#000000` as the primary page background on all marketing and brand surfaces.**
   Pure black is the emotional canvas of the Uber identity. The blackness is not decorative -- it is the brand.
   Verify: `<body>` or page wrapper `background-color` is exactly `#000000`.
   Dark grays like `#111111` or `#1a1a1a` are card surfaces, never the page canvas.

2. **Use Uber Move for headings (24px+) and Uber Move Text for body (18px and below).**
   Uber commissioned two font variants: the display cut (Uber Move) for large type and the text cut (Uber Move Text)
   for legibility at small sizes.
   Verify: font-family on headings includes `"Uber Move"` as first value; body text includes `"Uber Move Text"`.
   System fallback chain: `system-ui, "Helvetica Neue", Helvetica, Arial, sans-serif`.

3. **Create elevation on dark surfaces through luminance stepping, not shadows.**
   Depth is communicated by brightening the surface: `#000000` (ground) -> `#141414` (card) -> `#1a1a1a` (modal).
   Combine with `rgba(255,255,255,0.08)` luminance borders to define edges.
   Verify: on dark backgrounds, cards use a lighter `background-color` plus a white-alpha border,
   not `box-shadow` with dark colors.

4. **Reserve `#ffffff` as the sole accent color on dark surfaces.**
   White is the signal in a sea of black. It appears on primary CTA buttons, active navigation,
   and the most important text.
   Verify: the only non-gray, non-black color used for interactive elements on dark backgrounds
   is `#ffffff` (or `rgba(255,255,255,0.85)` for hover).

5. **Apply weight 500 as the default heading weight, 700 for hero display only.**
   Uber typography is medium-bold, not heavy. Weight 500 (medium) handles headings, nav links,
   and button labels. Weight 700 (bold) is reserved for the largest display text
   (52px hero headlines, key metric values).
   Verify: most heading elements use `font-weight: 500`. Only `h1` or display-class elements use 700.

6. **Maintain the 4px/8px spacing grid without exceptions.**
   Every padding, margin, gap, and dimension must be a multiple of 4px.
   Standard values: 4, 8, 12, 16, 24, 32, 48, 64, 80, 96px.
   Verify: inspect any spacing value -- it should be divisible by 4.
   Common violations: 5px, 10px, 15px, 22px, 30px.

7. **Use generous section padding (80-96px vertical) on the dark canvas.**
   Black amplifies perceived space. Content sections should float as islands in darkness,
   not be packed together.
   Verify: section `padding-top` and `padding-bottom` are 80px or greater on desktop.
   Hero sections use 96px minimum.

8. **Use 8px border-radius as the standard for buttons, cards, and inputs.**
   This is Uber's primary corner radius, matching the production app and website.
   Feature cards and modals step up to 12px.
   Verify: buttons have `border-radius: 8px`; cards have 8-12px; pill elements have `999px`.

9. **Use `#afafaf` for secondary text and `#6b6b6b` for tertiary.**
   Information hierarchy on dark surfaces depends on precise gray values.
   Primary text is white, secondary is mid-gray for descriptions and metadata,
   tertiary is dark gray for timestamps and disabled states.
   Verify: three distinct text color tiers are visible; secondary text is noticeably dimmer
   than headings but clearly legible.

10. **Integrate photography with the black canvas seamlessly.**
    Uber's visual language is photographic -- high-contrast images of cities, vehicles,
    and people in motion. Dark-toned photography blends into the `#000000` background
    without hard edges.
    Verify: hero images use dark photography or fade-to-black edges; no jarring
    white-background stock photos placed on dark sections.

## Don'ts (10 items)

1. **Do not use a light background (`#ffffff`, `#f5f5f5`, or any white/cream) as the page canvas.**
   The dark canvas IS the Uber brand identity. A white page turns Uber into a generic tech product.
   Verify: page `background-color` is `#000000`.
   Note: Uber's app uses light surfaces for maps and content areas; this rule applies to
   marketing, landing pages, and brand presentations.

2. **Do not introduce colored accents (blue, green, purple, orange) for UI chrome on dark surfaces.**
   The `#06c167` green belongs exclusively to Uber Eats contexts and success states.
   The `#276ef1` blue belongs to Freight and focus rings. No color should appear as a
   decorative accent, button color, or highlight on dark Uber surfaces.
   Verify: remove all color from the component -- it should still look complete and intentional.

3. **Do not use Inter, Helvetica, Roboto, or any generic sans-serif as the primary font.**
   Uber Move is the brand typeface. When it cannot load, the fallback chain is
   `system-ui, "Helvetica Neue", Helvetica, Arial, sans-serif` -- never another named design font.
   Verify: font-family declarations start with `"Uber Move"` or `"Uber Move Text"`,
   not `Inter`, `Roboto`, `SF Pro`, or `Arial`.

4. **Do not use traditional drop shadows (Y-offset + blur) on dark backgrounds.**
   `box-shadow: 0 4px 16px rgba(0,0,0,0.12)` is invisible on `#000000` and appears muddy
   on `#141414`. Dark elevation uses luminance: brighter surfaces and white-alpha borders.
   Verify: on any dark surface, `box-shadow` either does not exist or uses
   `rgba(255,255,255,...)` colors, not `rgba(0,0,0,...)`.

5. **Do not use visible card borders with solid gray hex colors on dark surfaces.**
   Borders on dark should be white-alpha (`rgba(255,255,255,0.08)`) to create a luminance edge,
   not solid colors like `#333333`, `#444444`, or `#2a2a2a`.
   Solid gray borders look flat and manufactured.
   Verify: card borders use `rgba(255,255,255,...)` notation, not hex gray values.

6. **Do not use font-weight 300 (light) or 200 (thin) on any text.**
   Uber typography is medium-to-bold. Light weights look fragile on dark backgrounds
   and contradict the brand's direct, confident voice.
   Verify: no element has `font-weight` below 400 (regular).

7. **Do not use gradient backgrounds or colorful overlays.**
   The Uber dark surface is flat pure black or flat dark gray. No linear-gradients,
   no radial-gradients, no semi-transparent color overlays on hero images.
   The only gradient permitted is a subtle black-to-transparent fade at photo edges
   for text legibility.
   Verify: no `background: linear-gradient(...)` with non-black colors.

8. **Do not use playful, rounded, or cartoon-style illustrations.**
   Uber's visual tone is urban, precise, and photographic. Bubbly illustrations,
   hand-drawn icons, emoji-style graphics, or colorful isometric art contradict
   the monochromatic, serious brand personality.
   Verify: visual assets are photographs or clean monoline icons, not illustrated
   characters or playful graphics.

9. **Do not crowd content on the dark canvas.**
   Dense, tightly-packed layouts that work on light backgrounds feel claustrophobic on black.
   The dark canvas demands generous spacing -- section gaps of 80px+, card padding of 32px+,
   and ample breathing room between text blocks.
   Verify: no section-to-section gap smaller than 64px on desktop;
   no card with less than 24px internal padding.

10. **Do not use decorative borders, divider lines, or visual separators extensively.**
    On the black canvas, content sections are separated by space, not lines.
    A horizontal rule or visible divider between sections adds visual noise
    to what should be clean darkness.
    Verify: sections are separated by `margin` or `padding` (80px+), not by `<hr>` elements
    or `border-bottom` on section containers.
    Subtle dividers within lists (1px `rgba(255,255,255,0.06)`) are acceptable.

## Critical Violations (5 items)

1. **Light/white page background on brand surfaces.**
   Using `#ffffff` or any light color as the page canvas destroys the entire Uber visual identity.
   The brand is built on the black canvas. This single error converts an Uber page into a
   generic white-background tech site. The dark canvas is the non-negotiable foundation --
   everything else (typography, spacing, photography) is calibrated for it.

2. **Colored accent replacing white as the primary interactive color.**
   Introducing a blue, green, or orange as the CTA button color on dark surfaces breaks
   the monochromatic system that defines Uber. The white-on-black button IS the signature
   interaction. Replacing it with `#276ef1` or `#06c167` makes the component look like
   Stripe or Spotify, not Uber.

3. **Generic font (Inter, Roboto, Helvetica) instead of Uber Move.**
   The typography is the most immediately recognizable element of Uber's design.
   Uber Move's specific letterforms, weight distribution, and spacing were designed
   for this brand. Substituting Inter or Roboto collapses the typographic identity
   into generic SaaS.

4. **Traditional dark drop shadows on dark surfaces.**
   Using `box-shadow: 0 4px 16px rgba(0,0,0,0.2)` on a `#141414` card sitting on `#000000`
   creates invisible or muddy depth. This reveals a fundamental misunderstanding of
   dark-surface design. Elevation on dark uses luminance (brighter surfaces,
   white-alpha borders), not traditional shadowing.

5. **Medium (400) or light (300) weight used uniformly across all text.**
   Uber's typographic hierarchy depends on weight contrast: 700 for display,
   500 for headings, 400 for body. When everything renders at the same weight
   (typically 400), the page loses its visual structure and hierarchy.
   On dark surfaces, this is especially damaging because white-on-black text at
   uniform weight creates a wall of undifferentiated information.
