# Tesla -- Design Guardrails

## Do's (10 items)

1. **Use full-bleed photography as the primary design element in every major section.**
   The photograph IS the layout. Hero sections, feature showcases, and gallery sections must contain edge-to-edge imagery with no padding, no border-radius, and no max-width constraint.
   - Verify: every section above the fold contains a full-viewport photograph touching all four edges.
   - Images use `width: 100%`, `object-fit: cover`, zero margin, zero padding.
   - Photographic content drives the emotional tone; UI elements are transparent scaffolding over it.

2. **Use `#ffffff` as the primary light page background and `#000000` for cinematic dark sections.**
   Tesla alternates between pure white content zones and true black photographic zones.
   - Verify: light sections use exactly `#ffffff`, dark sections use exactly `#000000`.
   - Never use `#f5f5f5`, `#fafafa`, or `#1a1a1a` as primary section backgrounds.
   - `#f4f4f4` is reserved for specs/configurator zones only, not as a primary page canvas.

3. **Apply the Tesla Blue accent (`#3e6ae1`) exclusively to primary CTA buttons and critical interactive links.**
   This is the SOLE chromatic color in the entire system.
   - Verify: at most two blue elements visible at any scroll position.
   - No blue backgrounds, no blue borders on non-interactive elements, no blue decorative use.
   - The blue must feel like a rare signal in a monochromatic world -- if it appears frequently, it loses its power.

4. **Use weight 300 (light) for hero and section headlines.**
   Tesla's typographic signature is airy, recessive headings that do not compete with photography.
   - Verify: hero text uses `font-weight: 300`, section headings use 300.
   - Weight 500 is the absolute maximum used anywhere (CTA buttons, nav links).
   - No heading should render at weight 600, 700, or bold. Check `font-weight` on all `h1`-`h4`.

5. **Build layouts as full-viewport (100vh) stacked sections with scroll-snap.**
   Tesla structures pages as a vertical stack of full-screen slides, not as a continuous scroll with card grids.
   - Verify: major sections have `min-height: 100vh`.
   - Parent container uses `scroll-snap-type: y mandatory` on desktop.
   - Each section is a self-contained "frame" -- one idea, one photograph, one CTA pair.

6. **Keep the navigation bar transparent, overlaying the hero photography.**
   The nav starts as a transparent bar with white text/icons floating over the hero image.
   - Verify: nav `background` starts as `transparent`, not solid white.
   - On scroll, transitions to frosted glass: `backdrop-filter: blur(16px)`, background `rgba(255,255,255,0.72)`.
   - Nav height: 52px. Transition duration: 300ms ease.

7. **Use ghost buttons (transparent with white/dark borders) for CTAs over photography.**
   On dark hero and photo backgrounds, buttons are transparent with 3px solid white borders.
   - Verify: no filled blue button sits on top of a photograph or dark background.
   - Blue-filled buttons appear only on white/light backgrounds.
   - Ghost button spec: `background: transparent`, `border: 3px solid #ffffff`, `border-radius: 4px`, `padding: 8px 56px`.

8. **Maintain extreme negative space with 120-200px vertical section padding.**
   Tesla's premium feel comes from vast breathing room inside sections.
   - Verify: section padding-top/bottom is at least 120px on desktop.
   - Text content blocks use `max-width: 680px` (narrow) or `1120px` (wide), always centered.
   - Hero content is positioned at the bottom of the viewport with `padding-bottom: 120px`.

9. **Apply monochromatic text hierarchy using only the grayscale palette.**
   - Primary text: `#171a20` (near-black, blue undertone)
   - Secondary: `#5c5e62` (medium gray, body copy)
   - Tertiary: `#393c41` (dark gray, sub-nav)
   - Muted: `#8e8e8e` (light gray, footnotes)
   - On dark: `#ffffff`, on-dark-secondary: `#ababab`
   - Verify: every text element uses a color from this list. No blues, no warm grays, no off-whites on light backgrounds.

10. **Use 17px (not 16px) for body text with weight 400 and line-height 1.50.**
    Tesla's body copy is slightly larger than the web default, creating comfortable readability.
    - Verify: body paragraphs render at `font-size: 17px`.
    - Font: `"Universal Sans Text"` stack with Gotham SSm and Helvetica fallbacks.
    - Never reduce body text below 14px (captions only).

## Don'ts (10 items)

1. **Do not use card-based grid layouts.**
   Tesla does NOT use 2x2 or 3x3 card grids with shadow, border-radius, and padding.
   - Violation: `display: grid` or `display: flex` container arranging 3+ elevated "cards" with shadows in a grid.
   - Content is presented in full-width sections, split-screen layouts (50/50 photo + text), or full-bleed galleries.
   - The "three cards in a row" pattern is the most common Tesla-violation in the wild.

2. **Do not add border-radius to photographs.**
   Photography must be sharp-edged and full-bleed.
   - Violation: any `border-radius` value on `<img>` elements or photo containers.
   - Rounded corners on images are antithetical to the cinematic gallery aesthetic.
   - The only exception: modal dialog containers (8px radius) and rare configurator panels.

3. **Do not use font weights of 600, 700, or bold on any element.**
   Tesla's heaviest common weight is 500 (CTA buttons). Even headings use 300-400.
   - Violation: `font-weight: 600`, `700`, `800`, `900`, or `bold` on any text element including headings.
   - Bold type fights the photography and destroys the airy, premium feel.
   - This is the most counterintuitive rule -- "important" text is made LIGHT, not heavy.

4. **Do not apply box-shadow to section containers or content blocks.**
   Tesla achieves depth through photography layering and light/dark contrast, never through CSS shadows.
   - Violation: `box-shadow` on any element other than the scrolled navigation bar.
   - The only shadow in the system: `0 1px 4px rgba(0,0,0,0.06)` on the nav after scroll.
   - No card elevation, no "floating" containers, no material-design shadow stacks.

5. **Do not introduce additional chromatic colors.**
   The palette is monochromatic (black/white/gray) plus one single blue.
   - Violation: any non-grayscale, non-blue color used in the UI chrome.
   - No red CTAs, no green success banners in the main UI, no orange highlights, no gradients.
   - The only exceptions: error (`#c00000`) and success (`#008a00`) states in form validation only.

6. **Do not constrain hero images with max-width containers.**
   Text content uses `max-width: 1120px` or `680px`. Images must break out to 100% viewport width.
   - Violation: a hero photograph wrapped in a centered container that leaves whitespace on left and right.
   - Full-bleed means full-bleed: `width: 100%`, `max-width: none`.
   - Even in split-screen layouts, the photo column touches the viewport edge.

7. **Do not use icon-heavy navigation or feature sections.**
   Tesla nav has 5 text links and 2-3 utility icons maximum.
   - Violation: more than 3 icons visible in the navigation, or icon grids used to represent features.
   - Feature sections use photography, not icon + text cards.
   - No feature-icon rows (the "four icons with labels" pattern is explicitly wrong for Tesla).

8. **Do not use gradient backgrounds on sections.**
   Tesla sections are solid `#ffffff`, solid `#000000`, `#f4f4f4`, or a full-bleed photograph.
   - Violation: `linear-gradient` or `radial-gradient` as a section `background` not overlaying a photo.
   - The only permitted gradient: a subtle dark overlay on photography for text legibility.
   - No "hero gradient" backgrounds, no gradient CTA buttons, no gradient text.

9. **Do not use large border-radius on buttons (12px+).**
   Tesla buttons have sharp or barely-rounded corners (4px).
   - Violation: `border-radius: 12px`, `16px`, `24px`, or `9999px` on any button element.
   - Pill-shaped or heavily rounded buttons belong to Apple, not Tesla.
   - Both filled and ghost buttons use 4px radius consistently.

10. **Do not start the navigation bar with a solid white or colored background.**
    The nav must begin transparent over the hero image and transition on scroll.
    - Violation: nav bar with `background: #ffffff` or `background: white` in its default state.
    - A solid nav at page load destroys the immersive full-bleed hero experience.
    - The nav should feel invisible until the user scrolls past the hero section.

## Critical Violations (5 items)

1. **Card grid layout instead of full-bleed sections.**
   Arranging content in 2-3 column card grids with shadows and rounded corners is the single most common mistake.
   Tesla's layout DNA is full-width horizontal bands, not a dashboard of cards.
   This error collapses the cinematic, gallery-wall identity into a generic SaaS layout.
   Test: remove the Tesla colors -- does the layout still look like a card-based product page? If yes, it is wrong.

2. **Multiple accent colors or colorful palette.**
   Adding red, orange, green, or purple as additional UI accents beside blue destroys the monochromatic restraint.
   Tesla's power comes from the fact that `#3e6ae1` is the ONLY chromatic color -- everything else is grayscale.
   More color = less Tesla. This applies to section backgrounds, borders, badges, and any decorative element.
   Test: convert the page to grayscale -- does it lose its identity? For Tesla, it should look almost identical.

3. **Heavy drop shadows on containers.**
   Any visible `box-shadow` with blur > 4px and opacity > 0.06 on content containers.
   Tesla is shadowless. Depth comes from photography and light/dark section alternation.
   Adding material-design elevation makes it look like Google, not Tesla.
   Test: remove all `box-shadow` declarations -- does the visual hierarchy survive? For Tesla, it must.

4. **Bold type throughout (weight 600-700 on headings).**
   Using bold/semibold headings makes the design feel assertive and corporate.
   Tesla headings are light (300) -- they whisper rather than shout, allowing the photography to dominate.
   Bold headings over a photo create visual competition instead of harmony.
   Test: squint at the page -- is the typography or the photography the dominant element? For Tesla, photography wins.

5. **No photography -- text-only layout on white.**
   A Tesla-branded page with no full-bleed imagery is not Tesla.
   The photography is not decoration; it IS the primary content. A page of text blocks, cards, and buttons on white
   with the Tesla color palette is just a generic page painted blue.
   Every major section must reference or contain imagery. The page should feel like a gallery exhibition, not a document.
   Test: would this layout apply equally well to Shopify or Stripe? If yes, it has not captured Tesla's identity.
