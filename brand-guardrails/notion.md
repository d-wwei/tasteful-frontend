# Notion -- Design Guardrails

## Do's (10 items)

1. **Use `#ffffff` white as the primary page background.**
   Notion's canvas is pure, bright white. The warmth in the design comes from the text color (`#37352f`) and secondary surfaces (`#f7f6f3`), not from the page itself. This is the opposite of brands like Claude (cream) or Linear (dark). White is the content-first foundation.
   Verify: `body` or main page wrapper has `background-color: #ffffff`. Never `#fafafa`, `#f5f4ed`, or any tinted white.

2. **Use `#37352f` (warm charcoal) for all primary text.**
   This is Notion's most distinctive design choice -- a warm near-black with a brown undertone that separates it from every product using pure black (`#000000`) or cool gray text. The warmth is subtle but essential: it makes the white page feel approachable rather than clinical.
   Verify: all heading and body text elements use `color: #37352f` on light backgrounds. Not `#000000`, not `#333333`, not any Tailwind gray like `#374151`.

3. **Use the full system font stack starting with `-apple-system`.**
   The font-family must be: `-apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif`. This is the Notion identity -- native platform typography with no custom display face. San Francisco on Mac, Segoe UI on Windows. The lack of a branded font is itself the brand statement: Notion feels like an extension of your operating system.
   Verify: no `@font-face` imports, no references to Inter, Roboto, Poppins, or any named font. The only exceptions are Notion's user-selectable serif (`Lyon-Text, Georgia`) and monospace (`iawriter-mono, Nitti, Menlo`).

4. **Separate elements with 1px solid `#e9e9e7` borders, not drop shadows.**
   Notion's visual hierarchy is border-driven. Cards, table cells, sidebar edges, and content dividers all use this single warm border color. The border-shadow at level-0 (`0 1px 0 rgba(55,53,47,0.09)`) is just a border simulation, not elevation. Real shadows (`level-1`, `level-2`) are reserved exclusively for floating overlays: dropdown menus, modals, command palette, and drag states.
   Verify: cards and containers use `border: 1px solid #e9e9e7` at rest. `box-shadow` is absent or zero on non-floating elements.

5. **Use `#f7f6f3` (warm off-white) for secondary surfaces.**
   Sidebar backgrounds, hover states on blocks, selected row highlights, and callout/code backgrounds all use this single secondary surface. It is warmer than `#f5f5f5` and distinctly different from cool grays. This one color handles most of Notion's surface layering.
   Verify: sidebar or secondary panel background is `#f7f6f3`. Block hover states shift to `#efefef`. Neither value is a cool gray.

6. **Apply weight 700 for H1/hero, 600 for H2/H3, 500 for UI elements, 400 for body.**
   Notion creates hierarchy through font-weight, not through font-family changes or dramatic size jumps alone. Each heading level has a specific weight assignment that must be maintained. Weight 500 is the UI tier: buttons, nav links, sidebar items. Weight 400 is for all body text and descriptions.
   Verify: H1 elements render at `font-weight: 700`, H2/H3 at `600`, buttons and nav at `500`, and body paragraphs at `400`. No heading uses 400; no body text uses 600+.

7. **Use 3px border-radius for small elements and 8px for cards/modals.**
   Notion's corners are tight and functional. Buttons get `3px`. Inline tags get `3px`. Inline code gets `3px`. Cards and modals get `8px`. Input fields get `4px`. This is a signature detail -- the tight radius communicates precision and tool-like efficiency. It is the opposite of the rounded, friendly aesthetic (12px+) used by products like Stripe or Linear.
   Verify: primary buttons use `border-radius: 3px`. No functional UI element uses radius larger than `8px`. The only exception is `9999px` pill-shaped status badges.

8. **Reserve Notion Blue (`#2eaadc`) exclusively for interactive elements.**
   Links, active sidebar items, selected database filters, focused inputs, and toggle-on states. It is a signal color meaning "clickable" or "currently active." The blue should never appear on static content. Inside the product, `#2eaadc` replaces the black CTA used on marketing pages. The accent hover variant `#2691bd` is used on hover.
   Verify: every instance of `#2eaadc` or `#2691bd` appears on an interactive or selected-state element. No decorative use.

9. **Use Notion's exact color-tint backgrounds for categorical content.**
   Tags, callouts, and status properties use these specific pastel tints: gray `#f1f1ef`, brown `#f3eeee`, orange `#f8ecdf`, yellow `#faf3dd`, green `#eef3ed`, blue `#e9f3f7`, purple `#f6f3f8`, pink `#f9f2f5`, red `#faecec`. Each tint is paired with a matching text color from Notion's palette (e.g., blue tint `#e9f3f7` with blue text `#337ea9`). These are not arbitrary -- they are Notion's visual language for categorization.
   Verify: tag and callout backgrounds use the exact brand tint hex values. Not opacity-based tints (e.g., `rgba(46,170,220,0.1)`), not Tailwind pastel classes, not arbitrary colors.

10. **Use solid black `#000000` for marketing CTA buttons.**
    On landing pages and marketing contexts, Notion's primary CTA is a solid black button with white text, `3px` border-radius, `14px` font-size at weight 500, padding `8px 14px`. This high-contrast black-on-white treatment is distinct from the blue accent used inside the product. The hover state softens to `#37352f` (warm charcoal).
    Verify: marketing hero CTAs use `background: #000000; color: #ffffff`. Not `#2eaadc` background. Not `#37352f` at rest.

## Don'ts (10 items)

1. **Do not use pure black `#000000` for text.**
   Notion's primary text color is `#37352f` -- a warm charcoal with brown undertone. Pure black looks harsh and creates too much contrast against the white page, destroying the warm approachability. The difference is subtle in isolation but dramatic in full-page context.
   Violation: any heading or body text with `color: #000000` or `color: black`. Exception: white text inside solid-black CTA buttons is fine.

2. **Do not use drop shadows for cards, containers, or section separation.**
   Notion's depth system is almost entirely flat. Borders handle all static separation. Shadows are reserved only for floating overlays: dropdown menus (`0 4px 12px rgba(0,0,0,0.08)`), modals (`0 12px 32px rgba(0,0,0,0.12)`), and active drag states. A card with a shadow at rest looks like Material Design, not Notion.
   Violation: any card, section, or container with `box-shadow` containing a Y-offset while not in a floating/overlay state.

3. **Do not use rounded corners above 8px on functional elements.**
   Notion's aesthetic is tight and efficient, not bubbly or playful. Buttons use `3px`, cards use `8px` at most. Large radii (12px, 16px, 24px, 32px) completely transform the personality from "precision tool" to "friendly consumer app." This is one of the strongest visual differentiators between Notion and products like Stripe, Figma, or Apple.
   Violation: `border-radius: 12px` or higher on any button, card, input, or container element.

4. **Do not introduce custom or decorative fonts.**
   No Google Fonts imports, no display typefaces, no handwriting fonts, no branded type. The system font stack is not a fallback -- it IS the design choice. Importing Inter, SF Pro, Poppins, or any named font destroys the native-platform feel. The only alternative fonts in the system are the user-selectable options: Lyon-Text (serif) and iawriter-mono (monospace).
   Violation: any `@import` or `@font-face` declaration for fonts outside Notion's three-option set (system sans, Lyon-Text serif, iawriter-mono).

5. **Do not use colored backgrounds for page sections.**
   Notion pages are white. There are no dark sections, no gradient sections, no colored hero backgrounds, no tinted section canvases in Notion's design language. Color backgrounds appear only inside inline content blocks: callouts, tags, database property chips. The section-alternating pattern (light/dark) that works for Claude or Linear is wrong for Notion.
   Violation: any `<section>`, `<div>`, or page-level element with a non-white `background-color`. Exception: sidebar uses `#f7f6f3`.

6. **Do not use Notion Blue (`#2eaadc`) as a surface fill or decorative element.**
   It is an interaction signal, not a brand surface. Using it as a card background, hero gradient, section fill, or large decorative area destroys its meaning as "this element is interactive." Notion Blue must remain scarce and functional. On marketing pages, the CTA is black -- not blue.
   Violation: `background: #2eaadc` or `background-color: #2eaadc` on any element that is not a small button, badge, toggle, or active-state indicator.

7. **Do not use uniform spacing between all elements.**
   Notion's block-based layout uses adjacency-aware spacing: tight within related content (4px between paragraphs), moderate between heading and body (16px), generous between sections (48-64px). List items adjacent to other list items compress together. Equal spacing everywhere (e.g., all blocks with `margin-bottom: 16px`) looks generic, not like Notion.
   Violation: identical `gap` or `margin` values applied uniformly to all block types without regard to adjacency context.

8. **Do not apply hover effects with color transitions, transforms, or gradients.**
   Notion hovers are a simple, fast (100ms) background shift to `#f7f6f3` or `#efefef`. There are no smooth color transitions, no gradient reveals, no scale transforms, no opacity fades, no "lift" effects on hover. The hover is binary: off-state background, on-state background. The speed is `transition: background 100ms ease` -- not 200ms, not 300ms.
   Violation: hover states using `transform: scale()`, `opacity` changes, `color` animation, gradient backgrounds, or transition durations above 150ms.

9. **Do not mix Notion's brand colors with arbitrary palette colors.**
   The full palette is precisely defined: 10 color families (default, gray, brown, orange, yellow, green, blue, purple, pink, red), each with text, background-tint, and icon variants. Introducing colors outside this closed system -- teal, indigo, lime, cyan, violet, emerald -- breaks the visual language that users recognize from the Notion product.
   Violation: any hex color not traceable to Notion's documented palette. Use the exact tint/text/icon hex values from the tokens file.

10. **Do not use heavy font weight (800, 900, black) on any element.**
    Notion's heaviest weight is 700, used only for H1 headings and hero headlines. Even 700 is used sparingly -- most of the interface runs at 400-600. The design relies on moderate weight contrast, not dramatic bold/thin tension. Ultra-bold weights feel aggressive and import a different design personality.
    Violation: `font-weight: 800`, `900`, or `font-weight: black` on any element. Also avoid `font-weight: 300` or lighter -- Notion does not use light/thin weights either.

## Critical Violations (5 items)

These are identity-destroying errors. A single instance of any critical violation means the output does not look like Notion.

1. **Cool gray or blue-gray text instead of warm charcoal `#37352f`.**
   This single color is Notion's DNA. Replacing it with `#333333`, `#374151`, `#1f2937`, or any Tailwind/Foundation gray collapses the warm, approachable identity into generic tech startup. The warm brown undertone in `#37352f` is what makes Notion feel human rather than mechanical.
   Detection: check computed `color` on heading and body elements. If the R and G channels are equal or the B channel is higher than G, the gray is cool-toned. In `#37352f`, note that R(0x37) > G(0x35) > B(0x2f) -- this warm cascade must be preserved.
   If the text is not warm-toned, it is not Notion.

2. **Drop shadows on cards or containers at rest.**
   Notion's flat, border-driven aesthetic is the single most visually distinctive element of the product UI. Adding `box-shadow` with any Y-offset to cards or content containers creates a Material Design, Apple, or Stripe visual language that is fundamentally incompatible with Notion's identity.
   Detection: search CSS for `box-shadow` on any element with class containing `card`, `container`, `section`, or `block`. If the shadow has `offsetY > 0` and the element is not a dropdown, modal, tooltip, or actively-being-dragged item, it is a violation.
   The correct approach: `border: 1px solid #e9e9e7`, no shadow.

3. **Custom or decorative display fonts replacing the system stack.**
   The system font stack (`-apple-system, BlinkMacSystemFont, Segoe UI...`) is not a development shortcut or a fallback. It IS the typographic identity. Notion deliberately chose to look like your operating system. San Francisco on macOS, Segoe UI on Windows, Roboto on Android. This platform-native feel is the reason Notion "disappears" into the OS.
   Detection: search for `@import`, `@font-face`, or any Google Fonts URL. Search for font-family declarations containing named fonts like `Inter`, `SF Pro`, `Poppins`, `Montserrat`, `Helvetica Neue` as primary (not fallback) values.
   The native feel is non-negotiable.

4. **Colored page/section backgrounds (dark sections, gradient heroes, tinted canvases).**
   Notion's page is white (`#ffffff`). The entire design language -- warm text color, border-driven separation, block-based spacing, adjacency-aware padding -- assumes content on a clean white canvas. Dark sections, gradient hero backgrounds, and tinted page areas are design patterns from other products (Claude uses parchment alternating with dark, Linear uses dark surfaces, Stripe uses gradient heroes). None of these exist in Notion's vocabulary.
   Detection: check `background-color` or `background` on `body`, `main`, `section`, and top-level `div` elements. Anything other than `#ffffff` (or `#f7f6f3` for sidebar specifically) is a violation.
   A non-white page background means it is not Notion.

5. **Large border-radius (12px+) on buttons and cards.**
   Notion's `3px` button radius and `8px` card radius are among its most recognizable micro-details. They communicate "this is a precision tool for work" rather than "this is a friendly consumer app." The tight corners are as much a part of Notion's identity as the system font stack.
   Detection: search CSS for `border-radius` values. Any value of `12px`, `16px`, `20px`, `24px`, or `32px` on buttons, cards, inputs, or containers is a violation. The `9999px` pill shape is permitted only on small status badges and filter chips.
   Rounding to 12px+ transforms the entire personality from efficient workspace to casual consumer product. This is not a matter of preference -- it is a personality change equivalent to swapping the font.

## Quick Self-Check

Before submitting any Notion-branded component, run through these five questions:

1. Is the page background exactly `#ffffff`? (Not cream, not off-white, not gray)
2. Is all primary text `#37352f`? (Not `#000000`, not any cool gray)
3. Does `font-family` start with `-apple-system`? (No custom font imports)
4. Are cards separated by `border: 1px solid #e9e9e7` with no `box-shadow`? (Flat, not elevated)
5. Are button corners `3px` and card corners `8px` or less? (Tight, not rounded)

If any answer is "no," the component does not look like Notion. Fix before shipping.
