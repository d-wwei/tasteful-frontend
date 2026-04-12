# Claude (Anthropic) -- Design Guardrails

## Do's (10 items)

1. **Use Parchment (`#f5f4ed`) as the primary light page background.** This warm cream tone is the emotional foundation of the entire design. Verify: page `background-color` must be `#f5f4ed`, never `#ffffff` or any cool gray.

2. **Use Anthropic Serif at weight 500 for all headlines.** Every heading from Display (64px) through Feature Title (20.8px) uses exactly weight 500. Verify: no heading element renders Anthropic Serif at any weight other than 500.

3. **Use Terracotta Brand (`#c96442`) exclusively for primary CTAs and highest-signal brand moments.** It is the only chromatic button color in the system. Verify: `#c96442` appears only on primary action buttons and key brand accents, never as decorative fill.

4. **Keep every neutral warm-toned with a yellow-brown undertone.** The grays are `#5e5d59`, `#87867f`, `#4d4c48` -- never blue-gray or cool-gray variants. Verify: every neutral color in use falls within the warm gray family defined in the palette.

5. **Use ring shadows (`0px 0px 0px 1px`) for interactive element states.** Buttons and cards use the ring pattern (`#d1cfc5 0px 0px 0px 1px` etc.) instead of drop shadows. Verify: button/card hover and focus states use 0-offset 0-blur 1px-spread shadow, not traditional `box-shadow` with Y-offset.

6. **Maintain the serif/sans hierarchy: Anthropic Serif for content headlines, Anthropic Sans for UI.** The typographic identity splits authority (serif) from utility (sans). Verify: no headline uses Anthropic Sans; no button, label, or nav link uses Anthropic Serif.

7. **Set body text line-height to 1.60.** This is significantly more generous than typical (1.4-1.5) and creates the editorial reading experience. Verify: body paragraphs have `line-height: 1.60` or its equivalent.

8. **Alternate between light (Parchment) and dark (Near Black `#141413`) sections.** This creates a chapter-like page rhythm. Verify: the page contains at least one dark section break between light sections in any multi-section layout.

9. **Apply generous border-radius (12-32px) for a soft, approachable feel.** Standard buttons get 8px, primary buttons and inputs get 12px, featured containers get 16px, hero containers get 32px. Verify: no card or button uses radius below 6px.

10. **Use Ivory (`#faf9f5`) or Pure White (`#ffffff`) for card surfaces on Parchment backgrounds.** Cards should sit one luminance step above the background. Verify: cards on Parchment use `#faf9f5`; `#ffffff` is reserved for specific button surfaces.

## Don'ts (10 items)

1. **Do not use cool blue-grays anywhere in the palette.** Every gray must carry a yellow-brown undertone. Violation: any color with a blue or cool-gray hue (e.g., `#6b7280`, `#94a3b8`) in backgrounds, text, or borders.

2. **Do not use bold (700+) weight on Anthropic Serif.** Weight 500 is the ceiling for all serif text. Violation: `font-weight: 600`, `700`, or `bold` on any Anthropic Serif element.

3. **Do not introduce saturated colors beyond Terracotta.** The palette is deliberately muted. The only saturated color is `#c96442` and its variant `#d97757`. Violation: adding bright blues, greens, purples, or any high-chroma accent to the UI chrome.

4. **Do not use sharp corners (< 6px radius) on buttons or cards.** Softness is core to the identity. Violation: `border-radius: 0`, `2px`, or `4px` on any button or card element.

5. **Do not apply heavy drop shadows.** Depth comes from ring shadows and background color shifts, not traditional elevation shadows. Violation: `box-shadow` with blur > 24px at opacity > 0.05, or any shadow stack that creates a prominent floating effect.

6. **Do not use `#ffffff` as a page background.** The page canvas is Parchment (`#f5f4ed`) or Ivory (`#faf9f5`). Violation: `background-color: #ffffff` or `white` on the `<body>` or main page wrapper.

7. **Do not use geometric or tech-style illustrations.** Claude's visual personality uses organic, hand-drawn-feeling vector art in terracotta, black, and muted green. Violation: wireframe-style icons, 3D renders, or sharp geometric artwork.

8. **Do not reduce body line-height below 1.40.** The generous spacing supports the editorial personality. Violation: `line-height` of `1.2` or `1.3` on any paragraph or body text element.

9. **Do not use monospace fonts for non-code content.** Anthropic Mono is strictly for code blocks and terminal output. Violation: Anthropic Mono used for labels, badges, headings, or decorative text.

10. **Do not use Anthropic Sans for headlines.** The serif/sans split is the typographic identity. Violation: any `<h1>` through `<h6>` or heading-class element rendering in Anthropic Sans.

## Critical Violations (5 items)

1. **Cool-gray or blue-gray neutrals anywhere.** This single error collapses the entire warm, literary atmosphere into generic tech. The warm palette is the non-negotiable foundation.

2. **`#ffffff` page background instead of Parchment (`#f5f4ed`).** The parchment tone IS Claude's personality. A white background makes it look like every other product page.

3. **Sans-serif headlines.** The Anthropic Serif at weight 500 is the first thing a viewer notices. Replacing it with sans-serif destroys the "literary salon" identity and makes it indistinguishable from generic AI landing pages.

4. **Heavy drop shadows or material-design-style elevation.** Claude's depth system uses warm ring shadows and light/dark section alternation. Traditional shadow stacks feel foreign and overly aggressive.

5. **Terracotta used as a decorative surface color rather than a CTA accent.** Flooding the page with `#c96442` backgrounds or fills breaks the restraint that makes the accent meaningful. It must remain scarce and high-signal.
