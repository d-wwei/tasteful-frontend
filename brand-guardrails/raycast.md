# Raycast -- Design Guardrails

## Do's (10 items)

1. **Use `#191A1F` as the primary launcher/page background.**
   This warm dark gray with a slight blue undertone matches macOS dark mode chrome and is the emotional foundation of the entire design.
   Verify: page `background-color` is `#191A1F`, not pure `#000000` or a warm brown-black.
   The slight blue-gray shifts it from "generic dark theme" to "macOS-native dark overlay."
   The raised surface (`#23252B`), elevated surface (`#2C2E36`), and overlay (`#363840`) follow the same cool-blue undertone in stepping increments.

2. **Apply `backdrop-filter: blur(40px) saturate(180%)` on glass panels.**
   The frosted glass effect is Raycast's signature depth model -- it makes the launcher feel like a macOS-native overlay, not a flat webpage.
   Verify: every translucent panel (`rgba(25,26,31,0.72)` or similar) has both blur AND saturation boost applied.
   Without `saturate(180%)`, the glass looks washed out and loses vibrancy.
   This applies to: navigation bar, command palette background, overlay panels, and marketing hero panels.
   Always pair with a translucent `rgba()` background -- the blur has no visible effect on a solid opaque surface.

3. **Use the brand gradient `linear-gradient(135deg, #FF6363, #E84393)` exclusively on primary CTAs and highest-signal moments.**
   This red-to-pink gradient is the most recognizable Raycast visual element after the app icon.
   Verify: the gradient appears only on the primary action button, loading bar, and hero accent.
   Never on surfaces, backgrounds, card fills, or secondary elements.
   Solid `#FF6363` is for secondary accents: icon tints, selection highlights, inline links.
   Rule of thumb: one gradient element per viewport. If two gradient elements are visible simultaneously, one should become solid accent instead.

4. **Display keyboard shortcut hints as first-class UI elements.**
   Use SF Mono at 11px weight 500 with bordered badges: `rgba(255,255,255,0.06)` background, `rgba(255,255,255,0.08)` border, 4px border-radius, `2px 6px` padding.
   Verify: action bars, list items, and tooltips include visible keyboard shortcut indicators.
   Shortcut badges must appear beside every actionable command in the palette and action bar.
   A Raycast UI without keyboard affordances is fundamentally incomplete -- the keyboard-first philosophy is the product's core identity, not a nice-to-have.

5. **Use semi-transparent white borders exclusively.**
   Standard: `rgba(255,255,255,0.10)`. Subtle: `rgba(255,255,255,0.06)`. Strong: `rgba(255,255,255,0.16)`.
   Verify: every border in the UI uses an `rgba(255,255,255,...)` value.
   Never use solid hex borders like `#333`, `#444`, or `#2c2c2c`.
   The transparency lets the background content influence border tone, which is essential for maintaining the glass panel aesthetic.
   On elevated surfaces, subtle borders (`0.06`) prevent visual noise. On interactive elements, strong borders (`0.16`) signal focus.

6. **Set base text size to 15px, not 16px.**
   Raycast's type scale follows macOS system typography: 15px base, 13px small, 11px caption.
   Verify: body text renders at 15px, search input at 15px, list item primary labels at 13px.
   If any text appears at the web-standard 16px, 14px, or 12px, it is off the macOS-native grid.
   The odd-number sizes (15, 13, 11) match SF Pro text rendering and create the system-level feel that distinguishes Raycast from web apps.

7. **Use `#ECECEC` for primary text, never pure `#ffffff`.**
   The slightly dimmed near-white reduces glare on dark surfaces and matches macOS system text rendering.
   Verify: headings and primary labels use `#ECECEC`.
   Reserve pure `#FFFFFF` strictly for text-on-accent (gradient button labels where maximum contrast is needed).
   Secondary text uses `rgba(255,255,255,0.55)`, tertiary uses `rgba(255,255,255,0.35)`.
   This three-tier text opacity system creates clear information hierarchy without introducing additional gray hex colors.

8. **Communicate elevation through background opacity stepping, not shadows.**
   The elevation ladder: `rgba(255,255,255,0.03)` flat, `0.04` subtle, `0.06` elevated, `0.08` hover.
   Verify: cards and list items use translucent backgrounds without `box-shadow`.
   Shadows are reserved exclusively for the launcher window itself (`level-2` and `level-3` tokens) and modals.
   This opacity-based elevation matches how macOS handles depth in its own UI -- NSVisualEffectView uses material blending, not drop shadows.

9. **Use Inter for marketing, SF Pro stack as fallback for native feel.**
   Font stack: `'Inter', -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif`.
   Verify: three weights only -- 400 (body reading), 500 (UI emphasis, labels, nav, buttons -- the workhorse weight), 600 (section headings and display text).
   Never use 700 or `font-weight: bold`. Maximum is 600.
   Weight 500 is the signature -- it appears on more elements than any other weight. If in doubt, use 500.

10. **Apply negative letter-spacing at all text sizes above caption.**
    Display/Section: `-0.025em`. Body/Title/Small: `-0.01em`. Caption (11px all-caps labels): positive `0.04em`.
    Verify: headings and body text have tighter tracking than Inter defaults.
    This subtle tightening matches macOS system type rendering and separates Raycast from generic Inter-based websites.
    The positive tracking on caption-level text is specifically for all-caps labels where wide spacing improves readability.

## Don'ts (10 items)

1. **Do not use opaque solid backgrounds on panels that should be glass.**
   If a nav bar, card, or overlay uses a solid hex like `#1a1a1a` instead of `rgba(25,26,31,0.72)` with blur, it kills the macOS-native feel.
   Violation: any panel intended as an overlay using a non-translucent `background-color` without `backdrop-filter`.
   The fix is always the same: switch to an `rgba()` background and add `backdrop-filter: blur(40px) saturate(180%)`.

2. **Do not use the brand gradient as a surface fill or background wash.**
   The gradient is high-signal -- it marks the single most important action on screen.
   Flooding a section background, hero area, or card surface with the red-to-pink gradient destroys the signal-to-noise ratio that makes the accent meaningful.
   Violation: `linear-gradient(135deg, #FF6363, #E84393)` applied to any element larger than a button or progress bar.
   If you need color in a large area, use the extended gradient at very low opacity as a subtle tint, not a fill.

3. **Do not introduce warm-toned or brown-tinted grays.**
   Raycast's dark palette has a cool-blue undertone (`#191A1F`, `#23252B`, `#2C2E36`), not warm browns or pure neutrals.
   Violation: background colors like `#1a1a1a`, `#2d2a27`, `#1e1d1b`, or any gray with visible yellow/brown warmth.
   The cool undertone is what makes the UI feel like macOS system chrome. Warm grays shift it toward a cozy/editorial aesthetic that belongs to a different brand.

4. **Do not use pure black (`#000000`) as a surface color.**
   Pure black creates harsh contrast against the rest of the palette and feels hostile on macOS, where even the darkest system surfaces are slightly lifted.
   The launcher background is `#191A1F` -- dark but breathable.
   Violation: `background-color: #000` or `#000000` on any visible surface element.
   Even overlays and backdrops should use `rgba(0,0,0,0.60)`, not solid black.

5. **Do not omit keyboard shortcut hints from interactive components.**
   Raycast is keyboard-first. Every actionable element in a command palette, action bar, or extension UI must show its shortcut.
   Violation: a command list or action bar rendered without visible keyboard shortcut badges.
   This is not optional decoration. The shortcut layer IS the primary interaction model. Mouse interaction is secondary.

6. **Do not use weight 700 or `font-weight: bold` anywhere.**
   The maximum weight is 600 (semibold) for section headings and display text.
   Raycast's type hierarchy uses weight contrast between 400/500/600 -- never 700.
   Violation: `font-weight: 700`, `font-weight: bold`, or `<b>`/`<strong>` tags that resolve to bold weight on any visible element.
   If an element needs more emphasis than 600, use size or color contrast instead.

7. **Do not use web-standard text sizes (16px, 14px, 12px) in the command palette or launcher UI.**
   The macOS-native scale is 15px/13px/11px -- all odd numbers.
   Using even-numbered sizes breaks the native feel and creates a subtle but perceptible mismatch with macOS system chrome.
   Violation: `font-size: 16px` on body, `14px` on metadata, or `12px` on captions inside any launcher-style component.
   Marketing pages have more flexibility, but the launcher/command palette components must use the native scale.

8. **Do not use solid hex colors for borders on glass panels.**
   Borders like `border: 1px solid #333` or `#2c2c2c` look opaque and heavy against translucent glass backgrounds.
   Violation: any `border-color` using a solid hex value (not `rgba()`) on a glass or translucent surface.
   Always use `rgba(255,255,255, 0.06-0.16)` to let the border breathe with the underlying content.

9. **Do not apply box-shadows to individual list items or cards.**
   Shadows are for the launcher window and modals only -- elements that float above the desktop.
   Cards inside the launcher get elevation from background opacity stepping, not drop shadows.
   Violation: `box-shadow` on a feature card, list item, result row, or inline element that is not a floating overlay.
   The only exception is the accent glow (`0 0 12px rgba(255,99,99,0.20)`) on gradient CTA buttons.

10. **Do not use positive letter-spacing on headings or body text.**
    Only caption-level (11px) all-caps labels get positive tracking (`0.04em`).
    Everything else uses negative tracking (`-0.025em` for display, `-0.01em` for body/small) or `normal`.
    Violation: `letter-spacing: 0.02em`, `0.05em`, or any positive value on headings, titles, or body paragraphs.
    Positive tracking on large text creates a "spaced out" feel that contradicts Raycast's dense, efficient aesthetic.

## Critical Violations (5 items)

1. **Opaque panels instead of glass.**
   If nav bars, overlays, or command palette containers use solid opaque backgrounds without `backdrop-filter: blur()`, the entire macOS-native identity collapses.
   The glass effect is not decorative -- it is the structural metaphor that makes Raycast feel like a system-level overlay rather than a web application.
   This is the single most common error and the most damaging. Every panel that sits above content must be translucent with blur.
   Detection: any overlay or floating panel with a solid `background-color` hex value and no `backdrop-filter` property.

2. **Brand gradient used as a surface or background.**
   The `#FF6363` to `#E84393` gradient must remain scarce -- its power comes from scarcity.
   When it appears on section backgrounds, card fills, or multiple buttons simultaneously, it becomes visual noise instead of a signal.
   The rule: one gradient element per viewport. Everything else uses solid `#FF6363` or `rgba(255,99,99,...)` at low opacity.
   Detection: `linear-gradient(135deg, #FF6363, #E84393)` on any element with width or height exceeding 300px, or more than one gradient element visible at the same scroll position.

3. **Light mode or white background as default.**
   Raycast is dark-native. The dark launcher aesthetic IS the brand.
   A light-background Raycast component is not "Raycast in light mode" -- it is a fundamentally different product.
   The dark surface is the canvas on which glass effects, accent gradients, and text hierarchy all depend.
   Light backgrounds make glass effects invisible, gradients garish, and the entire elevation system meaningless.
   Detection: `background-color: #fff`, `#ffffff`, `white`, or any background lightness value above 30%.

4. **Missing keyboard affordances.**
   A Raycast UI component without visible keyboard shortcuts is like a search engine without a search bar.
   Shortcut hints (SF Mono 11px, badge-styled with subtle borders) must appear in action bars, beside list items, and in tooltips.
   If the keyboard layer is invisible, the design fails the brand's core founding principle: keyboard-first productivity.
   Raycast users navigate entirely by keyboard -- every command, action, and navigation path has a shortcut, and it must be visible.
   Detection: any command palette, action bar, or extension list rendered without `<kbd>`-style shortcut badges.

5. **Pure black surfaces (`#000000`) or warm-brown grays.**
   The Raycast dark palette has specific cool-blue tinted grays: `#191A1F` (surface), `#23252B` (raised), `#2C2E36` (elevated), `#363840` (overlay).
   Using pure black makes the UI feel harsh and hostile. Using warm-brown grays (common in editorial/literary dark themes) makes it feel muddy and foreign.
   The cool blue-gray undertone is what creates the macOS-native system chrome feel. It is the most subtle and most important palette decision.
   Detection: any surface color that is pure `#000000`, or any gray where the blue channel is not the highest RGB component.
