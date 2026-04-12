# Vercel -- Design Guardrails

## Do's (10 items)

1. **Use Geist Sans with aggressive negative letter-spacing at display sizes.** The scale: `-2.4px` to `-2.88px` at 48px, `-1.28px` at 32px, `-0.96px` at 24px, `-0.32px` at 16px, normal at 14px. Verify: display headings have the most aggressive negative tracking of any major design system.

2. **Use shadow-as-border (`0px 0px 0px 1px rgba(0,0,0,0.08)`) instead of traditional CSS borders.** This technique moves borders into the shadow layer for smoother rendering. Verify: cards and containers use `box-shadow` with `0px 0px 0px 1px` spread instead of `border` property.

3. **Enable `font-feature-settings: "liga"` on all Geist text.** Ligatures are structural, not optional. Verify: every Geist Sans and Geist Mono element includes `"liga"` in computed font-feature-settings.

4. **Use the three-weight system strictly: 400 (body), 500 (UI/interactive), 600 (headings).** No bold (700) except micro-badges (7px). Verify: no text element above 7px uses `font-weight: 700` or `bold`.

5. **Apply workflow accent colors (Ship Red `#ff5b4f`, Preview Pink `#de1d8d`, Develop Blue `#0a72ef`) only within their workflow context.** These colors mark specific pipeline stages, not decorative accents. Verify: these colors appear only in the Develop/Preview/Ship workflow visualization, not elsewhere.

6. **Use multi-layer shadow stacks for cards.** The full stack: `rgba(0,0,0,0.08) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 2px, rgba(0,0,0,0.04) 0px 8px 8px -8px, #fafafa 0px 0px 0px 1px`. Verify: featured cards include all four layers, including the inner `#fafafa` ring.

7. **Keep the color palette achromatic.** Grays from `#171717` to `#ffffff` are the system. Verify: UI chrome contains no hue other than the workflow accents in their designated context.

8. **Use `#171717` (Vercel Black) instead of `#000000` for primary text.** The micro-warmth matters. Verify: heading and body text `color` is `#171717`, not `#000000`.

9. **Use Geist Mono uppercase with `"liga"` or `"tnum"` for technical labels.** This is the "developer console" voice. Verify: technical labels and code metadata render in Geist Mono with `text-transform: uppercase`.

10. **Include the inner `#fafafa` ring in card shadow stacks.** This creates the subtle inner glow that distinguishes Vercel cards. Verify: card shadows include `#fafafa 0px 0px 0px 1px` as the final layer.

## Don'ts (10 items)

1. **Do not use positive letter-spacing on Geist Sans.** It is always negative or zero. Violation: `letter-spacing` > `0` on any Geist Sans text at any size.

2. **Do not use weight 700 (bold) on body text.** 600 is the maximum, used only for headings. Violation: `font-weight: 700` or `bold` on any text above 7px.

3. **Do not use traditional CSS `border` on cards.** The shadow-border technique is the system. Violation: `border: 1px solid #ebebeb` on card containers instead of the `box-shadow: 0px 0px 0px 1px` pattern.

4. **Do not introduce warm colors (oranges, yellows, greens) into the UI chrome.** The system is achromatic outside workflow contexts. Violation: warm hues used in backgrounds, borders, or button colors.

5. **Do not apply workflow accent colors (Red/Pink/Blue) decoratively.** They are semantic, marking pipeline stages only. Violation: `#ff5b4f`, `#de1d8d`, or `#0a72ef` used in buttons, backgrounds, or UI chrome outside the workflow visualization.

6. **Do not use heavy shadows (> 0.1 opacity).** The shadow system is whisper-level. Violation: `box-shadow` with any layer exceeding `rgba(0,0,0,0.1)`.

7. **Do not increase body text letter-spacing.** Geist is designed to run tight. Violation: positive `letter-spacing` on any body or UI text.

8. **Do not use pill radius (9999px) on primary action buttons.** Pills are for badges and tags only. Violation: `border-radius: 9999px` on CTA or action buttons.

9. **Do not skip the inner `#fafafa` ring in card shadows.** It is the glow that makes the system work. Violation: card shadow stacks that end at the elevation layers without the `#fafafa 0px 0px 0px 1px` inner ring.

10. **Do not use `#000000` for primary text color.** `#171717` is the correct near-black. Violation: `color: #000000` on headings, body text, or navigation.

## Critical Violations (5 items)

1. **Traditional CSS borders instead of shadow-as-border.** The `0px 0px 0px 1px rgba(0,0,0,0.08)` shadow-border is Vercel's most distinctive component pattern. Using `border: 1px solid` destroys the technical sophistication.

2. **Positive or zero letter-spacing on display headlines.** Vercel's `-2.4px` to `-2.88px` tracking at 48px is the most aggressive compression in major design systems. Without it, headlines look generic and unengineered.

3. **Missing inner `#fafafa` ring on cards.** The four-layer shadow stack with the inner glow is what makes Vercel cards feel "built, not floating." Omitting the inner ring produces flat, lifeless containers.

4. **Warm accent colors in UI chrome.** Vercel's achromatic palette is a design philosophy -- "every unnecessary token is stripped away." Introducing warm hues makes it look like a different product entirely.

5. **Weight 700 (bold) on any prominent text.** Vercel's type hierarchy is 400/500/600 with no bold. Using 700 breaks the restrained, engineering-grade precision of the typography.
