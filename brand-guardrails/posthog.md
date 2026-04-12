# PostHog -- Design Guardrails

## Do's (10 items)

1. **Use `#1d1f27` (Dark Navy) as the primary app background for analytics and dashboard views.**
   PostHog's product lives on dark surfaces. Every dashboard, insight, and settings page renders
   on this navy-black canvas. The slight blue undertone prevents the void feeling of pure black
   while supporting hours of screen time without eye strain.
   Verify: the main `background-color` on any app-context component is `#1d1f27`, not white, not
   pure black. Cards and panels use `#2c2e38` (Slate) for one step of elevation above the canvas.

2. **Use `#f9f9f9` (Near White) as the primary background for marketing and documentation pages.**
   PostHog splits its identity: dark for the product, light for the website. Landing pages, blog
   posts, and docs use this near-white to feel welcoming and readable in ambient lighting.
   Verify: marketing pages use `#f9f9f9` as page background. Cards sit on `#ffffff`. Never use
   the dark palette tokens on marketing pages, and never use the light palette in the app shell.

3. **Reserve PostHog Orange (`#f54e00`) strictly for primary CTAs, active navigation states, and brand marks.**
   Orange is the only high-chroma color in the interface chrome. It must remain scarce to retain
   signal value -- one orange element per viewport section is the target density. The scarcity is
   what makes it a signal rather than a decoration.
   Verify: `#f54e00` appears only on primary action buttons, active sidebar indicators, and the
   logo. Count the orange elements per screen -- if more than two, reduce.

4. **Use IBM Plex Sans as the sole typeface for all UI and marketing content.**
   PostHog unifies its entire visual language through a single font family. Weight and size create
   hierarchy, not font-family switching. IBM Plex Sans was chosen for its humanist warmth, which
   softens the data-dense interface without sacrificing technical credibility.
   Verify: no heading, button, label, or body element uses Inter, Helvetica, Arial, or any other
   sans-serif. IBM Plex Sans must be the first entry in every `font-family` stack.

5. **Use 1px solid `#3b3d4f` borders as the primary containment strategy on dark surfaces.**
   On PostHog's dark canvas, borders provide structure that shadows cannot. Every card, panel,
   table, and input field on dark uses this border for visual separation. Borders are visible and
   reliable on dark backgrounds; shadows are not.
   Verify: dashboard cards and panels use `border: 1px solid #3b3d4f`, not `box-shadow` as
   primary containment. Inputs use the same border or `#565869` for focus emphasis.

6. **Apply the chart color sequence in order: Blue, Purple, Orange, Green, Amber, Pink.**
   PostHog's data visualization palette is curated for colorblind accessibility and maximum
   distinction between adjacent series. Blue (`#1d8aed`) always leads as the primary series
   because it is the most neutral and legible data color on both dark and light backgrounds.
   Verify: the first data series in any chart is blue, not orange, not random. The full sequence:
   `#1d8aed` > `#6c3ff2` > `#f54e00` > `#42b983` > `#f1a82c` > `#ff6384`.

7. **Use semibold (600) for section headings and bold (700) only for display/hero text.**
   PostHog's typographic hierarchy is weight-driven. Semibold (600) handles all headings within
   the product -- page titles, card headers, settings labels, table column headers. Bold (700) is
   reserved for marketing hero headlines at 40px or above where impact matters.
   Verify: in-app headings use `font-weight: 600`, not 700. Only display text at 40px+ gets 700.

8. **Maintain the 4px base grid for all spacing within analytics components.**
   PostHog displays dense data -- funnels, retention tables, event streams. The 4px grid allows
   tight 8px gaps between data rows and 4px inline spacing while keeping everything aligned.
   Common values: 4px (inline), 8px (tight), 12px (standard), 16px (comfortable), 20-24px (card
   padding). All multiples of 4.
   Verify: padding, margin, and gap values within data-heavy components are multiples of 4px.

9. **Use the three-step text color system for hierarchy on dark surfaces.**
   PostHog's dark mode uses `#eeefe9` (primary), `#9ba0aa` (secondary), and `#6b7280` (tertiary)
   as a controlled three-tier hierarchy. Primary for headings and key values. Secondary for
   descriptions and body text. Tertiary for timestamps, helper text, and de-emphasized metadata.
   Verify: all text on dark surfaces uses one of these three values. No custom grays. If a fourth
   shade appears, map it to the nearest of the three.

10. **Distinguish app-context components from marketing-context components.**
    PostHog's product UI (dashboards, insights, settings) uses dense layouts, dark backgrounds,
    and functional border-radius (6-8px). Marketing UI (landing pages, feature tours, pricing)
    uses generous spacing, light backgrounds, and larger radius (8-12px). These are two different
    visual systems sharing one typeface and one accent color.
    Verify: a dashboard card uses `border-radius: 8px` and 20-24px padding on dark. A marketing
    card uses `border-radius: 12px` and 32px padding on light. They should not look identical.

## Don'ts (10 items)

1. **Do not use `#f54e00` as a surface fill, section background, or gradient base.**
   Orange as a background destroys PostHog's restrained, tool-like aesthetic and makes the brand
   color meaningless. Orange is a point, not an area. Its power comes from contrast with the dark
   or light canvas surrounding it.
   Violation: any element with `background: #f54e00` that is not a button or a small badge (<48px
   tall). Never apply orange as a hero section background, card fill, or sidebar background.

2. **Do not use pure black (`#000000`) as a background.**
   PostHog's darkest surface is `#111318` (deepest dark for sidebars). The main canvas is
   `#1d1f27`. Pure black looks harsh and creates excessive contrast against the off-white text,
   causing visual fatigue during the long sessions analytics users spend in the product.
   Violation: `background-color: #000000` or `background: black` on any surface element.

3. **Do not use pure white (`#ffffff`) as an app background in dark mode.**
   White surfaces inside the analytics product create jarring contrast against the dark canvas.
   White is reserved for card surfaces on light-mode marketing pages only. In the app shell,
   the lightest surface is `#3b3d4f` (hover state).
   Violation: `background: #ffffff` on any component intended for the dark app context.

4. **Do not introduce font families beyond IBM Plex Sans and Source Code Pro.**
   The single-family system is PostHog's typographic identity. Adding Inter, Roboto, Helvetica,
   or any other typeface creates visual inconsistency and undermines the unified feel that IBM
   Plex Sans provides across the entire product and website.
   Violation: any `font-family` declaration that does not start with `IBM Plex Sans` (for UI)
   or `Source Code Pro` (for code). System fallbacks after the primary font are acceptable.

5. **Do not use border-radius above 8px on app-context components.**
   PostHog's product UI is tool-like and functional. Marketing pages allow up to 12px. But
   dashboard cards, buttons, inputs, and dropdowns within the app cap at 8px. The preferred
   radius for buttons and inputs is 6px. Pill shapes (9999px) are allowed only for small badges
   and status indicators.
   Violation: `border-radius: 12px` or `16px` on a dashboard card, insight panel, modal, or
   settings form element.

6. **Do not apply heavy drop shadows on dark surfaces.**
   Shadows are nearly invisible on dark backgrounds and waste rendering effort. If you make them
   visible by increasing opacity, they look like dark smudges. On PostHog's dark canvas, borders
   provide the structural containment that shadows provide on light surfaces.
   Violation: `box-shadow` with blur > 4px and opacity > 0.15 on any element rendered on
   `#1d1f27` or `#2c2e38`. Exception: dropdowns, tooltips, and modals that float above the page.

7. **Do not use brand orange as the default/first chart color.**
   Blue (`#1d8aed`) is always the primary data series. Using orange first makes every chart look
   like a brand exercise instead of a data tool. Orange appears as the third series in the default
   palette, or when a single metric needs explicit highlighting against neutral chart colors.
   Violation: the first series in a line chart, bar chart, or funnel using `#f54e00`. Orange is
   series 3, never series 1.

8. **Do not use weight 700 (bold) for in-app headings.**
   Bold is reserved for display text at 40px+ on marketing pages. In-app headings use semibold
   (600) for a professional, tool-like feel that scales well across the many heading sizes in a
   complex analytics product. Bold in-app headings look heavy-handed and reduce readability.
   Violation: any heading below 32px size using `font-weight: 700` or `font-weight: bold`.
   Dashboard titles, card titles, and settings headings must use weight 600.

9. **Do not use monospace fonts for decorative or branding purposes.**
   Source Code Pro is strictly for code blocks, HogQL queries, API keys, and technical output.
   Using monospace for badges, labels, or headings as a "developer chic" aesthetic undermines
   the clean IBM Plex Sans identity. PostHog already communicates "developer tool" through its
   data density and dark interface -- monospace decoration is redundant.
   Violation: monospace `font-family` on any non-code element: navigation labels, badges,
   overline text, headings, or decorative elements.

10. **Do not add playful illustrations or emoji to functional UI chrome.**
    PostHog's personality shows in microcopy, empty states, and the hedgehog mascot in appropriate
    brand moments. The functional UI -- navigation, data tables, form controls, toolbar buttons --
    must remain clean and tool-like. Playfulness lives in the content layer, not the chrome layer.
    Violation: hedgehog illustrations inside sidebar navigation, emoji in tab labels, cartoon
    borders on input fields, gradient decorations on data tables, or animated mascots in toolbars.

## Critical Violations (5 items)

1. **Orange surface flood.**
   Using `#f54e00` as a background color on any container larger than a button. This single error
   transforms PostHog from a precision analytics tool into a garish brand exercise. The orange
   must remain a point accent, never an area fill. If orange covers more than approximately 5% of
   any screen's pixel area, something is wrong. The fix: reduce orange to buttons and small
   indicators only. Use `#3d2a1f` (accent-muted) for orange-tinted dark backgrounds if needed.

2. **Pure black background instead of Dark Navy.**
   Using `#000000` instead of `#1d1f27` collapses the carefully calibrated dark palette. PostHog's
   navy-black has just enough blue to feel sophisticated rather than void-like. Every surface
   color in the dark theme -- `#2c2e38`, `#35374a`, `#3b3d4f` -- is calibrated relative to this
   specific base. Replacing it with pure black breaks the entire elevation system and makes the
   UI feel like a terminal rather than a modern analytics product.

3. **Wrong typeface.**
   Using Inter, Helvetica, or system-ui as primary instead of IBM Plex Sans. PostHog chose Plex
   specifically for its humanist warmth -- the slightly wider letterforms and open counters soften
   the data-dense interface and differentiate PostHog from the sea of Inter-based SaaS products.
   Losing IBM Plex Sans makes PostHog visually indistinguishable from generic developer tooling.

4. **Shadows replacing borders on dark cards.**
   Using `box-shadow` as the primary containment for dashboard cards instead of
   `1px solid #3b3d4f`. On dark backgrounds, shadows are either invisible (wasted) or artificially
   brightened (ugly). Border-driven containment is PostHog's structural language on dark surfaces.
   Replacing it with shadow-driven elevation imports a light-mode design pattern that fails
   fundamentally on dark. The fix: borders on dark, shadows allowed on light.

5. **Chart colors randomized or orange-first.**
   Using random colors for data series, or leading with brand orange. PostHog's chart palette is
   deliberately sequenced for colorblind accessibility and visual distinction. Blue first, purple
   second, orange third. Randomizing this sequence, or leading with orange to "reinforce the
   brand," makes charts harder to read and looks amateurish in a product where data legibility is
   the core value proposition. The fix: always apply the chart color array in order.
