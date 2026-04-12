# Airbnb -- Design Guardrails

## Do's (10 items)

1. **Use `#222222` (warm near-black) for all primary text.** Never pure `#000000`. The warmth conveys Airbnb's welcoming, human personality. Verify: every primary text element uses `color: #222222`, not `#000000` or `black`.

2. **Apply the three-layer card shadow on all elevated surfaces.** The layers are: `rgba(0,0,0,0.02) 0px 0px 0px 1px` (border ring) + `rgba(0,0,0,0.04) 0px 2px 6px` (ambient) + `rgba(0,0,0,0.1) 0px 4px 8px` (lift). Verify: elevated cards and search bars use all three shadow layers, not a single-layer shortcut.

3. **Reserve Rausch Red (`#ff385c`) exclusively for primary CTAs and the logo.** It is the singular accent color in the system. Verify: `#ff385c` appears only on primary action buttons, search button, and the Airbnb logo.

4. **Use Airbnb Cereal VF at weight 500-700 for headings.** The warm, confident weight range is intentional. Verify: no heading or emphasized text uses weight below 500.

5. **Apply negative letter-spacing on heading text: -0.44px for card headings, -0.18px for feature titles.** Creates intimate, cozy headings. Verify: card titles and feature headings have appropriate negative `letter-spacing`.

6. **Use generous border-radius: 8px for buttons, 20px for cards, 32px for large containers, 50% for circular controls.** The tactile rounding is core to the brand. Verify: every interactive element matches its designated radius tier.

7. **Use circular (50%) buttons for all carousel and navigation controls.** The circular geometry is a signature pattern. Verify: prev/next arrows and nav controls use `border-radius: 50%`, not pill or rectangle.

8. **Apply `font-feature-settings: "salt"` on badge and caption elements.** The stylistic alternates create subtle glyph variations. Verify: badge (11px) and specific caption (14px) elements include `"salt"`.

9. **Make photography the primary visual content.** Listing cards are image-first with generous image area (60%+ of card). Verify: every listing card prioritizes the photo with adequate height.

10. **Use `#f2f2f2` for secondary button surfaces and circular nav controls.** This light gray creates tactile, pressable-feeling controls. Verify: secondary circular buttons use `background: #f2f2f2`.

## Don'ts (10 items)

1. **Do not use pure black (`#000000`) for text.** The warm near-black (`#222222`) is non-negotiable. Violation: `color: #000000` or `color: black` on any text element.

2. **Do not apply Rausch Red to backgrounds or large surface areas.** It is an accent-only color. Violation: `background-color: #ff385c` on cards, sections, or containers.

3. **Do not use thin font weights (300, 400) for any heading.** Weight 500 is the minimum for headings. Violation: `font-weight: 400` or `font-weight: 300` on `h1`-`h6` or heading-class elements.

4. **Do not use heavy shadows.** The three-layer system's maximum opacity is 0.1. Violation: any shadow layer with opacity > 0.12, or a single shadow with blur > 12px at any significant opacity.

5. **Do not use sharp corners (0-4px radius) on cards or large buttons.** Softness and tactility are core. Violation: `border-radius: 0`, `2px`, or `4px` on any card or primary button.

6. **Do not introduce additional brand colors beyond the Rausch/Luxe/Plus system.** The palette is strictly defined. Violation: adding blues, greens, or purples beyond `#428bff` (legal), `#460479` (luxe), and `#92174d` (plus).

7. **Do not override the palette token system.** Use `--palette-*` CSS variables for consistent theming. Violation: hardcoded color values that bypass the token system.

8. **Do not use single-layer shadows on cards.** The three-layer system creates warm, natural lift. Violation: a single `box-shadow` value on any card element.

9. **Do not use positive letter-spacing on headings.** Headings always run with negative tracking for intimacy. Violation: `letter-spacing` > 0 on any heading text.

10. **Do not use text-heavy cards without photography.** Airbnb's identity is visual-first. Violation: listing or feature cards that rely on text alone without an image area.

## Critical Violations (5 items)

1. **Pure `#000000` text instead of `#222222`.** This single change transforms the friendly, welcoming personality into a cold, corporate one. The warmth of near-black is the emotional foundation.

2. **Single-layer or missing card shadows.** The three-layer shadow system (border ring + ambient + lift) creates Airbnb's distinctive natural, photographic light quality. A single shadow makes cards feel flat and generic.

3. **Rausch Red used as a surface or background color.** Flooding the page with `#ff385c` destroys the "white gallery" metaphor where photography is the hero content. The red must remain scarce and high-signal.

4. **Sharp corners (< 8px) on cards.** The generous 20px card rounding creates the tactile, magazine-like browsing feel. Square cards make it look like a data table, not a travel magazine.

5. **Thin-weight headings (< 500).** Airbnb Cereal VF at weight 500-700 creates a warm, confident voice. Lightweight headings feel tentative and undermine the brand's "belong anywhere" authority.
