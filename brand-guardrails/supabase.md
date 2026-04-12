# Supabase -- Design Guardrails

## Do's (10 items)

1. **Use `#171717` as the primary page background and `#1c1c1c` for elevated panels.**
   These two surfaces create the entire spatial hierarchy. The one-stop difference between canvas and panel is what makes Supabase feel layered without shadows.
   Verify: page `background-color` is `#171717`; cards, sidebars, and toolbars use `#1c1c1c`.

2. **Define depth through borders, not shadows.**
   Supabase uses `rgba(255,255,255,0.06)` for default separation and `rgba(255,255,255,0.12)` for strong dividers. This border-defined depth is the brand's spatial signature.
   Verify: cards use `border: 1px solid rgba(255,255,255,0.06)` for elevation. Shadows appear only on floating elements (dropdowns, modals, command palette).

3. **Reserve `#3ecf8e` exclusively for primary actions, active states, and success.**
   It is the highest-signal color in the system. The restraint is what makes it meaningful.
   Verify: emerald green appears only on primary CTA buttons, active navigation items, selected row indicators, success states, and the Run button in SQL editors. Count total uses -- if more than 3-4 green elements are visible simultaneously, the signal is diluted.

4. **Use `Source Code Pro` (or monospace fallback) for all technical content.**
   SQL queries, inline code, API responses, table cell data, terminal output, and code blocks must render in monospace at 13px with 1.70 line-height. Monospace content is central to Supabase's identity as a developer tool.
   Verify: no code content renders in Circular or any sans-serif font. Every developer-facing page should have visible monospace content.

5. **Maintain the compact, tool-first density.**
   Table rows at 36px height, nav at 56px, buttons with 8px 16px padding, 6px border-radius on controls. The dense areas offset the generous section gaps.
   Verify: dashboard components do not have luxury-level padding (no 48px+ card padding, no 80px+ header heights). Information density is an explicit design goal.

6. **Apply syntax highlighting consistently across all code surfaces.**
   SQL keywords: `#c792ea` (purple). String literals: `#c3e88d` (green). Numbers: `#f78c6c` (orange). Comments: `#5c5c5c` (muted italic).
   Verify: these four colors appear in every code block, SQL editor, and documentation example. Never display code as monochrome white text.

7. **Use the `#11181C` Bunker color for all code block backgrounds.**
   This is darker than the panel surface (`#1c1c1c`) -- code lives in its own visual trench. The distinction creates a clear "editor zone" that users recognize instantly.
   Verify: code blocks and SQL editors use `#11181C`, not `#1c1c1c` or `#171717`.

8. **Apply glassmorphism only to the sticky navigation bar.**
   `backdrop-filter: blur(12px)` with `rgba(23,23,23,0.85)` background. This is a single-point design decision that adds sophistication without becoming a pattern.
   Verify: blur effects appear nowhere else in the UI -- not on cards, modals, tooltips, or sidebars.

9. **Show data types in table column headers.**
   Display PostgreSQL type annotations (int4, text, uuid, bool, timestamptz) as small monospace labels next to column names in `#5c5c5c`. This is what distinguishes Supabase's table view from a generic data grid.
   Verify: table views include type information, rendered in `Source Code Pro` at 10-11px.

10. **Use `rgba(62,207,142,0.12)` as the accent-subtle background for selected states.**
    Selected table rows, active sidebar items, and highlighted list elements use this low-opacity green tint -- never a solid green background. The background is barely visible; the left border accent (`2px solid #3ecf8e`) provides the strong signal.
    Verify: selected states use the tinted background with a green left-border indicator.

## Don'ts (10 items)

1. **Do not use light or white backgrounds for any primary surface.**
   Supabase is dark-mode-native. `#ffffff`, `#f5f5f5`, or any light gray as a page or card background is a fundamental identity violation.
   The dark canvas is not a theme option -- it IS the brand.

2. **Do not use `#3ecf8e` as a heading color, decorative fill, or background wash.**
   Green text for headings makes them look like links. Green surface fills destroy the scarcity that makes the accent meaningful.
   If a design has green on anything other than buttons, active states, and success badges, it is overusing the accent.

3. **Do not apply traditional drop shadows to cards and panels.**
   On dark surfaces, `box-shadow: 0 2px 8px rgba(0,0,0,0.1)` is invisible. Heavier shadows look like floating islands rather than interface panels.
   Use border-defined depth. The only permitted shadows are on floating elements (dropdowns, modals) with heavy opacity (0.40+).

4. **Do not use pure white (`#ffffff`) for text.**
   Primary text is `#ededed` -- slightly dimmed to reduce eye strain on dark backgrounds. Pure white creates harsh contrast that makes the interface feel unrefined and fatiguing.
   Verify: no text element renders at `#ffffff`.

5. **Do not display code in sans-serif fonts.**
   Every code surface -- inline snippets, editor panes, API responses, terminal output -- must use `Source Code Pro` or a monospace fallback. Sans-serif code destroys the developer-tool credibility.
   If an inline `<code>` tag renders in Circular/Inter, it is broken.

6. **Do not use border-radius above 12px on functional UI elements.**
   Buttons: 6px. Cards: 8px. Inputs: 6px. The maximum is 12px for featured containers. Using 16px+ radius makes the interface look consumer-friendly rather than developer-precise.
   Exception: pill badges at `9999px` for status indicators only.

7. **Do not add decorative gradients or color washes to surfaces.**
   Supabase surfaces are flat solid colors (`#171717`, `#1c1c1c`, `#232323`). Gradient backgrounds, mesh gradients, or noise textures on functional surfaces are not part of the system.
   The only gradient permitted is the optional text gradient on hero headlines.

8. **Do not use `#8f8f8f` for headings or primary content.**
   `#8f8f8f` is the secondary text color -- for descriptions, metadata, and supporting copy. Using it on headings creates a washed-out, low-contrast layout that fails WCAG guidelines on dark backgrounds.
   Headings must use `#ededed`.

9. **Do not make navigation links green or underlined.**
   Nav links are `#8f8f8f` at rest, `#ededed` on hover. Only the active state uses green (as a left-border or icon tint, not as text color in the main nav).
   Underlines are not part of the navigation pattern.

10. **Do not use colored status indicators without their semantic meaning.**
    Green (`#3ecf8e`) = success/active/connected. Red (`#f56565`) = error/destructive/disconnected. Amber (`#f5a623`) = warning/caution/deprecated. These carry specific meaning in a database management context.
    Never use red for non-error decorative elements or green for non-success indicators.

## Critical Violations (5 items)

1. **Light-mode default on a Supabase-branded page.**
   This is the single most destructive error. The dark canvas (`#171717`) is the emotional and functional foundation of the brand.
   A white or light-gray background fundamentally changes the product's character from "developer tool" to "generic SaaS."
   Every Supabase component must render on dark surfaces unless explicitly building a documented light-theme variant.
   How to detect: check `<body>` or root wrapper `background-color`. Must be `#171717` or darker.
   How to fix: set `background: #171717` on body, `color: #ededed` as default text.

2. **Green accent flooding -- emerald used as surface fill or heading color.**
   When `#3ecf8e` appears on card backgrounds, section fills, heading text, or decorative borders, it ceases to function as a signal color.
   The entire visual hierarchy collapses because the eye no longer knows where to look.
   Green must remain scarce: primary CTA buttons, active states, success badges, and the Run button in SQL editors.
   How to detect: count green elements visible on any single viewport. More than 4 is a violation.
   How to fix: replace green surface fills with `#1c1c1c` + border. Replace green headings with `#ededed`.

3. **Sans-serif code rendering.**
   Displaying SQL queries, API keys, code snippets, or terminal output in Circular or any proportional font breaks the developer-tool contract.
   Monospace content signals "this is machine-readable" and enables visual alignment of data columns.
   Using sans-serif for code makes Supabase look like a marketing page pretending to be a tool.
   How to detect: inspect any `<code>`, `<pre>`, or `.code-block` element's computed `font-family`.
   How to fix: apply `font-family: 'Source Code Pro', Menlo, monospace` to all code elements.

4. **Shadow-based depth on dark surfaces.**
   Light-mode shadow patterns (`0 2px 8px rgba(0,0,0,0.1)`) are invisible on `#171717`.
   Attempting to create depth with shadows instead of borders results in either invisible layering or floating-island artifacts.
   Supabase's spatial hierarchy is built on border lines and surface-color stepping.
   How to detect: inspect card/panel elements for `box-shadow` properties. Static cards should have none.
   How to fix: remove `box-shadow`, add `border: 1px solid rgba(255,255,255,0.06)`. Use `#1c1c1c` background against `#171717` canvas.

5. **Generic data grid without PostgreSQL semantics.**
   Supabase is a Postgres management tool, not a spreadsheet.
   Table views must display column data types (int4, text, uuid, timestamptz), render NULL values with italic muted styling, show boolean values with green/gray differentiation, and display UUIDs in monospace.
   A plain table with string data in sans-serif is a generic HTML table -- not a Supabase component.
   How to detect: check table headers for type annotations; check cell rendering for type-specific formatting.
   How to fix: add `<span class="col-type">` next to column names. Style NULL as `color: #5c5c5c; font-style: italic`. Style booleans with `#3ecf8e` (true) / `#8f8f8f` (false).
