# Linear -- Design Guardrails

## Do's (10 items)

1. **Enable `font-feature-settings: "cv01", "ss03"` on ALL Inter Variable text.** These features transform generic Inter into Linear's distinctive geometric typeface. Verify: every text element using Inter Variable includes both `cv01` and `ss03`.

2. **Use weight 510 as the default emphasis weight.** This between-weight (between regular 400 and medium 500) is Linear's signature. Verify: navigation labels, emphasized text, and UI labels use `font-weight: 510`, not `500` or `600`.

3. **Apply aggressive negative letter-spacing at display sizes.** The scale: `-1.584px` at 72px, `-1.408px` at 64px, `-1.056px` at 48px, `-0.704px` at 32px, relaxing toward normal below 24px. Verify: display headings have proportionally negative `letter-spacing`.

4. **Build on near-black backgrounds: `#08090a` for marketing, `#0f1011` for panels, `#191a1b` for elevated surfaces.** The dark-mode-native system uses three tiers of background darkness. Verify: page backgrounds match these hex values exactly; no generic dark grays like `#1a1a1a` or `#222222`.

5. **Use semi-transparent white borders (`rgba(255,255,255,0.05)` to `rgba(255,255,255,0.08)`) instead of solid dark borders.** These whisper-thin borders create structure without visual noise. Verify: card and container borders use `rgba(255,255,255,...)` at low opacity, never solid hex border colors.

6. **Keep button backgrounds nearly transparent: `rgba(255,255,255,0.02)` to `rgba(255,255,255,0.05)`.** Buttons are ghost-like on the dark canvas. Verify: non-CTA button backgrounds use `rgba(255,255,255,...)` at 0.02-0.05 opacity.

7. **Reserve Brand Indigo (`#5e6ad2` / `#7170ff`) exclusively for primary CTAs and interactive accents.** It is the only chromatic color in the system. Verify: `#5e6ad2` or `#7170ff` appears only on primary action buttons, active states, and links -- never as decorative fill.

8. **Use `#f7f8f8` for primary text, not pure `#ffffff`.** The near-white with a barely-warm cast prevents eye strain. Verify: heading and primary text `color` is `#f7f8f8`, not `#ffffff`.

9. **Apply the luminance stacking model for elevation.** Deeper surfaces are darker (`#08090a`), elevated surfaces are slightly lighter (`#191a1b`). Depth comes from background luminance stepping, not from shadows. Verify: elevated components use a lighter background shade than their parent.

10. **Use Berkeley Mono for all code and technical content.** The monospace companion has fallbacks to `ui-monospace, SF Mono, Menlo`. Verify: code blocks, terminal output, and technical labels render in Berkeley Mono, not Inter Variable.

## Don'ts (10 items)

1. **Do not use pure `#ffffff` as primary text color.** `#f7f8f8` prevents eye strain on dark backgrounds. Violation: `color: #ffffff` or `color: white` on body or heading text.

2. **Do not use solid colored backgrounds for non-CTA buttons.** Transparency is the system. Violation: buttons with opaque `background-color` like `#333333` or `#5e6ad2` (except the primary brand CTA).

3. **Do not apply Brand Indigo decoratively.** It is reserved for interactive and CTA elements only. Violation: `#5e6ad2` or `#7170ff` used as background color on cards, sections, or decorative elements.

4. **Do not use positive letter-spacing on display text.** Inter at large sizes always runs negative. Violation: `letter-spacing` > 0 on any text 24px or larger.

5. **Do not use visible/opaque borders on dark backgrounds.** Borders should be whisper-thin semi-transparent white. Violation: `border: 1px solid #333333` or any opaque hex border color on dark surfaces.

6. **Do not skip the OpenType features (`"cv01", "ss03"`).** Without them, it is generic Inter, not Linear's Inter. Violation: any Inter Variable text element missing `font-feature-settings: "cv01", "ss03"`.

7. **Do not use weight 700 (bold).** Linear's maximum weight is 590, with 510 as the workhorse. Violation: `font-weight: 700` or `font-weight: bold` on any text element.

8. **Do not introduce warm colors into the UI chrome.** The palette is cool gray with a blue-violet accent only. Violation: orange, amber, warm red, or warm green used in backgrounds, borders, or text (status green `#27a644` is acceptable only for status indicators).

9. **Do not use drop shadows for elevation on dark surfaces.** Traditional dark-on-dark shadows are nearly invisible and look wrong. Violation: `box-shadow` with significant Y-offset and blur used as the primary elevation mechanism.

10. **Do not use light-mode defaults on the marketing site.** The design is dark-mode-native, not a dark theme applied to a light design. Violation: white page backgrounds, dark-text-on-light-surface as the default state for marketing pages.

## Critical Violations (5 items)

1. **Missing `"cv01", "ss03"` on Inter Variable text.** Without these OpenType features, the typography is indistinguishable from any other Inter-based design system. This is the typographic identity.

2. **Opaque button backgrounds instead of `rgba(255,255,255,0.02-0.05)`.** The ghost-like transparency of buttons on dark canvas is what creates Linear's precision-engineered feel. Solid backgrounds make buttons look like generic dark-mode components.

3. **Light-mode page background.** Linear's marketing site is dark-mode-native (`#08090a`). Rendering it on white fundamentally misrepresents the brand.

4. **Brand Indigo used decoratively across surfaces.** The power of `#5e6ad2` comes from its extreme restraint -- it appears only on CTAs and active states. Spreading it across backgrounds or borders destroys the signal-to-noise ratio.

5. **Using weight 700 (bold) anywhere.** Linear's type hierarchy never exceeds 590. Bold weight makes the precision-engineered feel collapse into generic emphasis.
