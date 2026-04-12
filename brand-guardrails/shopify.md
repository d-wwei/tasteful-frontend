# Shopify (Polaris) -- Design Guardrails

## Do's (10 items)

1. **Use `#f1f1f1` (gray canvas) as the page background with `#ffffff` card surfaces.**
   This gray-on-white spatial layering is the foundational Polaris pattern — content lives in elevated
   white cards atop a neutral canvas. The contrast between canvas and card is how merchants perceive
   information hierarchy.
   Verify: page `background-color` is `#f1f1f1` and primary content containers are `#ffffff`.

2. **Use Inter at the exact Polaris weights: 450 regular, 550 medium, 650 semibold, 700 bold.**
   Inter is a variable font and Polaris uses non-standard weight stops that are optically tuned for
   the admin UI density. Standard 400/500/600 will render at subtly wrong optical weights, breaking
   the carefully calibrated type hierarchy.
   Verify: every `font-weight` value is one of 450, 550, 650, or 700 — never 400, 500, or 600.

3. **Set default body text to 14px/20px, not 16px.**
   Polaris is an admin system optimized for information density. Table cells, descriptions, nav items,
   and body copy all use 14px with 20px line-height. This allows merchants to scan more data without
   scrolling — critical for order management and product listing workflows.
   Verify: the base font size is 14px and only prominent marketing-style text uses 16px.

4. **Apply shadow-100 (`0px 1px 0px 0px rgba(26,26,26,0.07)`) to card resting states.**
   This minimal 1px shadow is the Polaris signature depth cue — a hairline bottom edge that creates
   subtle baseline elevation without visual heaviness. It replaces traditional borders as the primary
   containment mechanism for card components.
   Verify: cards have `box-shadow: 0px 1px 0px 0px rgba(26, 26, 26, 0.07)` plus `border: 1px solid #e3e3e3`.

5. **Use the Polaris bevel shadow system for buttons.**
   Primary buttons get multi-layered inset shadows that create a physical, tactile feel:
   `inset 0 -1px 0 0 rgba(0,0,0,0.2), inset 0 1px 0 0 rgba(255,255,255,0.04)`.
   Pressed buttons shift to: `inset 0 2px 1px 0 rgba(0,0,0,0.2), inset 0 1px 1px 0 rgba(0,0,0,0.12)`.
   This bevel effect is unique to Polaris and is what makes Shopify buttons feel "clickable."
   Verify: buttons use inset shadow layers, not flat backgrounds or generic drop shadows.

6. **Reserve `#047b5d` (Commerce Green) strictly for success states and active badges.**
   Green means "active," "complete," or "positive change" in the Polaris semantic system.
   It appears on active status badges, positive trend indicators, success banners, and
   completion checkmarks. It is NOT the primary action color — that is `#303030`.
   Verify: green appears only on success indicators and positive state elements, never on primary CTA buttons.

7. **Use `#303030` (brand fill) for primary buttons and the admin top bar.**
   Shopify's primary action color is dark near-black, not green. The admin navigation is a dark
   `#303030` bar with white text and a translucent search field. This dark chrome frames the
   white content area, creating the workspace container metaphor.
   Verify: primary CTAs have `background: #303030` and the top navigation is dark-surfaced.

8. **Apply the Polaris spacing scale (4px base unit): 4, 8, 12, 16, 20, 24, 32, 40, 48, 64px.**
   Every padding, margin, and gap must land on this scale. Key Polaris-specific spacing:
   - Card padding: 16px (`--p-space-card-padding`)
   - Card content gap: 16px (`--p-space-card-gap`)
   - Button padding: 8px 16px
   - Button group gap: 8px (`--p-space-button-group-gap`)
   - Table cell padding: 6px (`--p-space-table-cell-padding`)
   Verify: all spacing values appear in the Polaris space token scale.

9. **Use the precise Polaris border-radius scale.**
   - Badges and small inline elements: 4px (`--p-border-radius-100`)
   - Buttons and inputs: 8px (`--p-border-radius-200`)
   - Cards and panels: 12px (`--p-border-radius-300`)
   - Featured containers and banners: 16px (`--p-border-radius-400`)
   - Avatars and pills: 9999px (`--p-border-radius-full`)
   Verify: no component uses a radius value outside this set (no 3px, 6px, 10px, 14px).

10. **Apply negative letter-spacing to headings 20px and above.**
    The Polaris letter-spacing scale tightens as size increases:
    - 20-24px headings: `letter-spacing: -0.2px`
    - 30px headings: `letter-spacing: -0.3px`
    - 36-40px display: `letter-spacing: -0.54px`
    - Body text (14-16px): `letter-spacing: 0` (normal)
    This tightening creates visual crispness at headline scale that separates Polaris from generic Inter usage.
    Verify: all headings at 20px+ have appropriate negative `letter-spacing`.

## Don'ts (10 items)

1. **Do not use a white (`#ffffff`) page background.**
   The admin background is `#f1f1f1`. White backgrounds eliminate the card-canvas contrast that
   defines Polaris spatial hierarchy. Without the gray canvas, cards lose their visual separation
   and the page becomes a flat, undifferentiated surface.
   Violation: `body { background: #ffffff }` or any white page wrapper.

2. **Do not use green as the primary action button color.**
   Commerce Green (`#047b5d`) is a semantic status color, not a CTA color. Primary buttons are
   `#303030`. The legacy `#008060` green was never used for primary buttons in modern Polaris —
   it was always reserved for success indicators.
   Violation: `button.primary { background: #047b5d }` or `#008060` as button background.

3. **Do not use standard font weights (400/500/600).**
   Polaris requires 450/550/650/700. Using standard stops makes Inter render at subtly wrong
   optical weights, which accumulates across a full admin page to create a noticeably different
   density feel — too light at 400, not differentiated enough between 500 and 600.
   Violation: any `font-weight: 400`, `font-weight: 500`, or `font-weight: 600` in the CSS.

4. **Do not set base body text to 16px.**
   Polaris defaults to 14px for body text. Using 16px across the board creates a loose,
   consumer-app feel that clashes with the dense, workflow-focused admin aesthetic. Merchants
   need to see product lists, order tables, and analytics — density is a feature, not a compromise.
   Violation: `body { font-size: 16px }` as a global default for admin interfaces.

5. **Do not use generic drop shadows.**
   Values like `box-shadow: 0 2px 8px rgba(0,0,0,0.1)` or `0 4px 12px rgba(0,0,0,0.15)` are
   foreign to Polaris. The shadow system uses specific tokens: shadow-100 (1px), shadow-200 (3px),
   shadow-300 (6px blur), up to shadow-600 (20px). Button depth comes from bevel insets, not drops.
   Violation: any shadow not matching a Polaris shadow token value.

6. **Do not use serif fonts anywhere.**
   Polaris is exclusively Inter (sans-serif) and system mono. There is no serif typeface in the
   system. Serif fonts introduce a literary or editorial tone that contradicts the utilitarian,
   tool-focused personality of the admin workspace.
   Violation: any serif font declaration (Georgia, Times, Merriweather, etc.) on any element.

7. **Do not use bright or saturated colors as decorative fills.**
   Polaris surfaces are white (`#ffffff`), light gray (`#f7f7f7`), or dark (`#303030`). Color
   appears only in semantic tokens: green for success, red for critical, amber for warning,
   blue for interactive/link. Never use these colors as section backgrounds or decorative fills.
   Violation: colored backgrounds like `#047b5d` as a section fill or `#005bd3` as a card surface.

8. **Do not render the admin navigation on a light background.**
   The top bar is always `#303030` (dark) with `#ffffff` text. A light-background nav loses
   the workspace framing that separates navigation from content. The dark-light split between
   nav and content area is a core Polaris spatial metaphor.
   Violation: nav background of `#ffffff`, `#f1f1f1`, or any light color.

9. **Do not use border-radius values outside the Polaris scale.**
   Random values like 3px, 6px, 10px, or 14px create visual inconsistency across the admin.
   Every radius must come from the Polaris token set: 0, 2, 4, 6, 8, 12, 16, 20, 30, 9999px.
   Violation: `border-radius: 3px`, `border-radius: 10px`, or any non-Polaris radius token.

10. **Do not mix Polaris admin patterns with consumer storefront patterns.**
    The admin uses: dense layouts, dark nav, 14px body text, bevel shadows, utilitarian icons.
    Consumer storefronts use: hero images, light nav, 16-18px text, lifestyle photography, large CTAs.
    These are two different design systems. Combining them creates visual incoherence.
    Violation: hero banner images, serif headlines, or lifestyle photography in an admin context.

## Critical Violations (5 items)

1. **White page background instead of gray canvas (`#f1f1f1`).**
   The gray-canvas-with-white-cards spatial model is the foundational visual identity of Polaris.
   Removing it collapses the entire depth hierarchy and makes the admin look like a flat consumer
   website. This is the single most distinctive Polaris trait — if you get nothing else right,
   get the gray canvas right. Would this apply to Linear or Notion? No — they use white. That is
   precisely why the gray canvas is Shopify-specific.

2. **Green primary CTA buttons instead of dark (`#303030`).**
   This is the most common Shopify design error. The BRAND color is green (in logos and marketing),
   but the BUTTON color in the admin is dark near-black. Using green CTAs makes the UI look like
   a Shopify clone from 2018, not the modern Polaris admin. The `#303030` primary with bevel
   shadows is the signature interaction pattern.

3. **Missing Inter font or using fallback system fonts as primary.**
   Inter is the identity typeface of Polaris. Without it, the specific weights (450, 550, 650),
   the negative letter-spacing tuning on headings, and the 4px-grid line-heights all break down.
   The design becomes generic sans-serif — visually indistinguishable from any other admin template.
   Always load Inter via Google Fonts or self-host it.

4. **Generic drop shadows replacing Polaris bevel/shadow tokens.**
   The bevel shadow system — multi-layered inset shadows on buttons creating a tactile 3D effect,
   plus the precise shadow-100 through shadow-600 elevation scale — is a design language unique
   to Polaris. Generic Material-style elevation shadows (blur-heavy, high-opacity) make the UI
   feel heavy, dark, and foreign to the Polaris ecosystem.

5. **16px body text default with standard font weights (400/600).**
   This combination — 16px base size + standard 400/600 weights — is the generic web app default.
   It creates a loose, consumer-app visual rhythm that contradicts Polaris's dense, workspace-optimized
   information hierarchy. The correct Polaris combination is 14px base + 450/650 weights. Getting
   this wrong makes every table, every list, every form feel wrong in aggregate even if individual
   components look fine in isolation.
