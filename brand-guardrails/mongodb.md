# MongoDB -- Design Guardrails

## Do's (10 items)

1. **Use `#001E2B` (MDB Ink) as the primary surface for developer tools and data panels.**
   Atlas, Compass, and shell interfaces all sit on this dark ink canvas. It is the visual foundation of every MongoDB product interface.
   Verify: any panel displaying data, queries, or documents uses `#001E2B` as its background, not white or generic dark gray.
   Exception: marketing pages and documentation use `#ffffff` (white) as the primary surface.

2. **Use `#00684A` (green.dark2) as the primary button color on light surfaces, and `#00ED64` (green.base) on dark surfaces.**
   The accent flips based on surface luminance to maintain WCAG AA contrast.
   On light: primary CTA background `#00684A`, text `#ffffff`. Hover: `#023430` (green.dark3).
   On dark: primary CTA background `#00ED64`, text `#001E2B`. Hover: `#00A35C` (green.dark1).
   Verify: never use `#00ED64` on a white surface (insufficient contrast) or `#00684A` on `#001E2B` (too dark to read).

3. **Use Euclid Circular A for all UI text: headings, body, buttons, labels, navigation.**
   This is LeafyGreen's primary typeface and must carry every word a user reads in the product interface.
   Fallback stack: `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`.
   Verify: no UI text element renders in a generic sans-serif, Georgia, or Source Code Pro (unless it represents data).

4. **Use Source Code Pro for all code, queries, JSON, ObjectIds, collection names, and shell output.**
   Monospace text is the visual signal that content is machine-readable data.
   Fallback stack: `'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace`.
   Verify: every `<code>`, `<pre>`, inline code snippet, or data-value element uses Source Code Pro.

5. **Apply the LeafyGreen semantic color system for status states.**
   Error: `#DB3030` (red.base) with `#FFEAE5` (red.light3) background.
   Warning: `#FFC010` (yellow.base) with `#FEF7DB` (yellow.light3) background.
   Info: `#016BF8` (blue.base) with `#E1F7FF` (blue.light3) background.
   Success: `#00684A` (green.dark2) with `#E3FCF7` (green.light3) background.
   Verify: each status type uses its designated color pair, not a tinted version of the brand green.

6. **Use 6px border-radius on buttons and inputs, 8px on cards and modals.**
   These are the LeafyGreen default radii. Badges and chips use 4px. Featured containers use 12px.
   Verify: no button uses radius above 6px; no card uses radius below 6px or above 12px.
   The pill radius (9999px) is reserved exclusively for tags and toggle indicators.

7. **Apply `#0498EC` (blue.light1) as the keyboard focus ring.**
   Focus indicators must be a 2px solid ring with 2px offset in blue, not green.
   This separates accessibility focus from interactive brand accent.
   Verify: tabbing through interactive elements produces a visible blue outline, distinct from the green active/selected state.

8. **Use the LeafyGreen gray scale for all neutral colors.**
   The full scale: `#112733` (dark4), `#1C2D38` (dark3), `#3D4F58` (dark2), `#5C6C75` (dark1), `#889397` (base), `#C1C7C6` (light1), `#E8EDEB` (light2), `#F9FBFA` (light3).
   These cool-toned grays with teal undertones are specific to MongoDB's visual identity.
   Verify: every gray in use matches a value from this scale, not generic CSS grays like `#333`, `#666`, `#ccc`.

9. **Design data panels for information density.**
   MongoDB users interact with documents, collections, and aggregation results containing hundreds of fields.
   Use 14px body text, 12px captions, 8px vertical cell padding, and compact table layouts.
   Line numbers in code panels use 12px Source Code Pro in `#3D4F58`.
   Verify: data-intensive views prioritize information density over decorative whitespace.

10. **Provide both light and dark surface variants for every card and panel component.**
    Atlas supports light marketing pages and dark product panels within the same application.
    Light variant: background `#ffffff`, border `1px solid #E8EDEB`, text `#001E2B`.
    Dark variant: background `#112733`, border `1px solid #3D4F58`, text `#E8EDEB`.
    Verify: each card component has explicit styles for both surface contexts.

## Don'ts (10 items)

1. **Do not use white (`#ffffff`) as the surface for data tools, query panels, or document viewers.**
   White is reserved for marketing pages and documentation. The product surface is `#001E2B`.
   Violation: a query editor, document panel, or aggregation builder sitting on a white background.
   Why it matters: the dark canvas provides contrast for syntax-colored code and reduces eye strain during long data sessions.

2. **Do not use `#00ED64` (green.base) as a surface fill or large background area.**
   The bright green is exclusively for text-on-dark, button fills, and active-state indicators.
   Violation: a green background panel, a green header bar, a green sidebar, or any area larger than a button filled with `#00ED64`.
   Why it matters: the accent earns its electric impact through scarcity against the dark ink canvas.

3. **Do not use generic warm-toned grays.**
   MongoDB's grays are cool-toned with teal/blue undertones from the LeafyGreen palette.
   Violation examples: `#5e5d59`, `#87867f`, `#f5f4ed`, `#f8f8f8`, or any neutral with a warm yellow-brown undertone.
   Why it matters: warm grays collapse the MongoDB identity into a generic note-taking or editorial aesthetic.

4. **Do not use Source Code Pro for UI labels, headings, or paragraph text.**
   Monospace is exclusively for machine-readable content: code, queries, data values.
   Violation: a button labeled in Source Code Pro, a heading in monospace, body paragraphs in code font.
   Exception: under 13px bold text may use Source Code Pro for improved legibility per LeafyGreen guidelines.

5. **Do not use MongoDB Value Serif in product UI.**
   The serif typeface is reserved for marketing display headlines at 48px+ on landing pages and blog headers.
   Violation: MongoDB Value Serif in a dashboard heading, modal title, sidebar label, or any product interface element.
   Why it matters: serif in the product UI conflicts with the technical, tool-like character of Atlas and Compass.

6. **Do not apply border-radius above 12px on standard components.**
   LeafyGreen uses subtle, precise rounding: 4px for chips, 6px for buttons, 8px for cards, 12px for featured.
   Violation: 16px+ radius on buttons, cards, or inputs, creating a bubbly appearance foreign to the system.
   Why it matters: excessive rounding signals consumer-app aesthetics, not developer-tool precision.

7. **Do not use green for error, warning, or informational states.**
   Each status has its own dedicated color in the LeafyGreen semantic system.
   Violation: a warning banner in green, an info badge in green, or a toast using green for a non-success message.
   Why it matters: overloading green with multiple meanings makes the user color-blind to severity in database operations.

8. **Do not omit line numbers in code blocks and query panels.**
   MongoDB developers expect numbered lines for reference in shell output, aggregation pipelines, and JSON documents.
   Violation: a code block or query panel without visible line numbers in a data-facing context.
   Style: 12px Source Code Pro, color `#3D4F58`, right-aligned, user-select none, padding-right 12px.

9. **Do not use drop shadows as the primary elevation mechanism on dark surfaces.**
   On `#001E2B`, depth comes from surface color stepping (dark4 -> dark3 -> dark2) and subtle borders.
   Violation: heavy drop shadows (`box-shadow` with blur > 20px at opacity > 0.1) on panels inside the dark Atlas environment.
   Why it matters: drop shadows on dark backgrounds create ghostly halos that fight the clean ink atmosphere.

10. **Do not use consumer-app styling patterns in developer interfaces.**
    MongoDB targets developers, data engineers, and DBAs. The UI language is technical and precise.
    Violation: rounded avatars with thick ring borders, gradient backgrounds, playful illustrations, emoji in UI labels, confetti animations, or gamification elements.
    Why it matters: every decorative element in a data tool is noise that competes with the signal (the data itself).

## Critical Violations (5 items)

1. **White background on developer tool panels.**
   Using `#ffffff` instead of `#001E2B` for query editors, document viewers, or aggregation builders fundamentally betrays the Atlas product identity.
   The dark ink canvas is where developers live -- replacing it with white makes the interface feel like a generic CRUD app, not a database platform.
   The dark surface provides essential contrast for syntax-colored JSON documents and shell output.

2. **Green.base (`#00ED64`) used as a surface fill.**
   Flooding any area larger than a button with bright green destroys the accent's signal value.
   The green earns its electric impact through extreme scarcity: a single CTA button, a status dot, an active tab indicator -- always small, always surrounded by ink.
   Using it as a header background or sidebar fill is the visual equivalent of a database that indexes every field.

3. **Euclid Circular A used for code, or Source Code Pro used for UI text.**
   This font-role violation breaks the foundational visual grammar of the entire system.
   Euclid = human-readable UI. Source Code Pro = machine-readable data.
   When a query renders in Euclid or a button renders in monospace, the interface loses its ability to signal what is data vs. what is control.
   This is the typography equivalent of mixing up your collection names and your field names.

4. **Warm-toned gray palette replacing LeafyGreen's cool grays.**
   MongoDB's grays carry a distinctive cool teal undertone (`#001E2B` -> `#112733` -> `#1C2D38` -> `#3D4F58`).
   Swapping these for warm beige/brown grays (the kind used by editorial or note-taking apps) collapses the entire visual identity.
   The cool-toned palette is what makes MongoDB look like infrastructure, not stationery.

5. **Missing semantic color differentiation.**
   Using brand green for all status states (error, warning, info, success) makes the interface monochromatic in the worst way.
   Each state has a dedicated hue: red for errors, yellow for warnings, blue for info, green for success.
   When everything important is green, nothing is. The user loses the ability to parse severity at a glance.
   In database operations, a dropped collection must look visually different from a successful insert -- there is no second chance.
