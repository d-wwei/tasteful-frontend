# Sentry -- Design Guardrails

## Do's (10 items)

1. **Use `#f9f8ff` as the primary light page background.** Sentry's dashboard surface is a faintly purple-tinted off-white, not pure white. This creates the subtle brand warmth that distinguishes Sentry from generic dev tools. Verify: page `background-color` is `#f9f8ff`, not `#ffffff` or a cool gray.

2. **Use `#ffffff` white for card and panel surfaces on the `#f9f8ff` background.** Data containers, issue lists, and dashboard widgets sit one step brighter than the page surface. This layering creates depth without shadows. Verify: `.card` and `.panel` elements use `#ffffff` background on the page surface.

3. **Reserve Sentry Purple (`#6a5fc1`) exclusively for interactive elements.** It signals "this is clickable" -- links, buttons, active tabs, selected rows, and focus indicators. Verify: every instance of `#6a5fc1` is on an element with `cursor: pointer`, a focus state, or an active indicator.

4. **Use the error severity color system correctly: pink for errors, orange for warnings, yellow for info, green for resolved, blue for debug.** Each level has a foreground color AND a 12% opacity wash background. Verify: severity badges use `#e1567c` / `rgba(225,86,124,0.12)` for errors, `#f4834f` / `rgba(244,131,79,0.12)` for warnings, etc.

5. **Use Rubik for all non-code text, IBM Plex Mono for all code text.** Sentry's typography is a strict two-font system. Rubik handles UI (nav, labels, headings, body). Plex Mono handles developer content (stack traces, error messages, file paths, code blocks). Verify: no `<code>`, `.stack-trace`, or `.error-message` element renders in Rubik; no heading or button renders in Plex Mono.

6. **Maintain Sentry's purple-tinted neutral scale.** The gray palette runs from `#E7E1EC` (light) through `#C6BECF`, `#9386A0`, `#776589`, to `#2B1D38` (dark), each carrying a subtle lavender-plum undertone. Verify: no blue-gray (like `#6b7280`) or warm-yellow gray (like `#6b6b5e`) appears in the palette.

7. **Use `#ececf1` recessed surfaces for inputs and code blocks.** Following Sentry's SCRAPS tactile depth model, form inputs and code containers appear "pushed into" the page. Verify: input fields have `background: #ececf1` and code blocks use either `#ececf1` (light context) or `#1F1633` (expanded dark context).

8. **Apply pill-shaped radius (`border-radius: 2em`) on primary and secondary CTA buttons.** The rounded pill shape is a SCRAPS signature. Standard UI elements use 6-8px radius. Verify: primary `.btn` uses `border-radius: 2em`; cards and panels use `border-radius: 6px` or `8px`.

9. **Implement tactile interaction feedback.** Buttons lift on hover (`translateY(-1px)`) and recess on press (`translateY(0)`). Focused inputs show a purple glow (`0 0 15px rgba(106,95,193,0.20)`). Verify: hover states include transform; focus states include the purple focus-ring shadow.

10. **Pack data densely in issue lists and tables.** Sentry users expect to see event counts, timestamps, assignees, severity indicators, and sparklines in compact rows. Use 12-14px text, 10-16px vertical padding, and small gaps. Verify: table rows are no taller than 48px with a single line of content; metadata fits on one line without wrapping.

## Don'ts (10 items)

1. **Do not use Sentry Purple (`#6a5fc1`) as a decorative surface fill.** A purple-tinted card background, a purple section, or a purple hero gradient destroys the signal-to-noise ratio. The accent must remain scarce so it reliably signals interactivity. Violation: any element with `background: #6a5fc1` that lacks a `cursor: pointer` or button role.

2. **Do not repurpose severity colors for non-severity purposes.** Error pink (`#e1567c`) is not a "fun accent." Warning orange (`#f4834f`) is not a "warm highlight." Using severity colors for decoration trains users to ignore them when they carry real meaning. Violation: severity color on a CTA button, decorative badge, or branding element.

3. **Do not make the entire dashboard dark by default.** Sentry's product UI is light-surface (`#f9f8ff` + white cards). Dark surfaces (`#1F1633`) are used for hero sections, code block expansions, and specific dark-mode contexts -- not as the default state. Violation: page `background-color: #1F1633` without explicit dark-mode intent.

4. **Do not use cool blue-gray or warm yellow-gray neutrals.** Every neutral in Sentry's system has a lavender-plum undertone. Introducing `#64748b` (blue-gray) or `#78716c` (warm stone) creates a color temperature mismatch. Violation: any gray value whose hue falls outside the purple-adjacent range (hue ~270-300).

5. **Do not use Rubik for stack traces or code content.** Monospaced text is not optional for developer-facing data. File paths, function names, error messages, and code snippets require IBM Plex Mono for alignment and readability. Violation: any `.stack-frame`, `.code-block`, or error message rendering in a proportional font.

6. **Do not add excessive whitespace to data tables and issue lists.** Sentry users scan hundreds of issues. Row padding above 16px, large gaps between metadata items, or oversized typography in tables wastes vertical space and forces unnecessary scrolling. Violation: table row height exceeding 56px for single-line content; body-size (16px) text used for table metadata.

7. **Do not use flat, square-cornered buttons.** Sentry's SCRAPS system defines two button shapes: pill (`border-radius: 2em`) for primary/secondary CTAs and rounded (`border-radius: 6px`) for toolbar actions. Sharp corners (0-2px) and no-radius buttons feel foreign. Violation: `border-radius: 0` or `border-radius: 2px` on any button element.

8. **Do not use heavy drop shadows for card elevation.** Sentry's depth comes from border + background layering, not shadow stacks. Light shadows (`0 1px 4px rgba(43,29,56,0.08)`) are acceptable; heavy Material-style shadows are not. Violation: `box-shadow` with blur > 16px at opacity > 0.15 on cards.

9. **Do not display charts without the correct severity color mapping.** Error metrics must use pink (#e1567c) for errors, orange (#f4834f) for warnings, green (#19ab27) for resolved. Arbitrary chart colors (random blues, teals, purples) break the user's mental model of severity-to-color associations. Violation: chart showing error data with non-standard color assignments.

10. **Do not use browser-default focus styles.** The blue outline clashes with Sentry's purple-toned system. All focused inputs and interactive elements must use the purple focus glow (`0 0 15px rgba(106,95,193,0.20)`) or a visible `#6a5fc1` ring. Violation: `outline: auto` or `outline: -webkit-focus-ring-color` on any interactive element.

## Critical Violations (5 items)

1. **All-dark dashboard as default surface.** Using `#1F1633` or any dark color as the primary page background transforms Sentry's light, clinical monitoring aesthetic into a generic dark dev-tool. The light surface (`#f9f8ff`) is Sentry's product identity -- dark surfaces are reserved for code contexts and hero sections only.

2. **Severity colors used as brand accents or decorative fills.** Error pink on a CTA button, warning orange as a card border, or info yellow as a highlight color trains users to ignore the severity system entirely. Sentry's severity palette is safety-critical UI: users depend on instant color recognition to triage hundreds of issues. Corrupting this mapping is a usability failure, not just a visual one.

3. **Purple accent flooding.** If more than 10% of visible screen area is filled with `#6a5fc1` or any purple-derived background, the accent has lost its signal function. The entire Sentry design system relies on purple being scarce and high-signal: links, active states, CTAs, and focus rings. Large purple surfaces make everything look interactive.

4. **Proportional font used for stack traces or error details.** Displaying function names, file paths, line numbers, or code context in Rubik (or any proportional font) makes stack traces unreadable. Column alignment breaks, line numbers misalign, and developers cannot scan error details effectively. IBM Plex Mono at 13px/1.65 line-height is non-negotiable for code content.

5. **Missing or incorrect error severity color system.** Displaying issue lists, error dashboards, or monitoring views without the pink/orange/yellow/green/blue severity mapping removes the most important visual triage tool in Sentry's UI. Users scan issue lists by color -- without correct severity colors, the interface becomes a wall of undifferentiated text.
