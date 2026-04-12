# Revolut -- Design Guardrails

## Do's (10 items)

1. **Use Shark (`#191C1F`) as the primary page background.**
   This deep charcoal is the emotional foundation -- not pure black, not dark gray.
   The slight warmth prevents the clinical coldness of `#000000` while maintaining financial seriousness.
   Verify: page `background-color` is `#191C1F`.

2. **Reserve Cornflower Blue (`#7F84F6`) exclusively for primary CTAs and active-state indicators.**
   This violet-blue is Revolut's brand DNA. It must appear sparingly -- typically fewer than 3 instances per screen.
   Every accent instance should answer the question "what should the user tap next?"
   Verify: `#7F84F6` appears only on primary action buttons, active navigation indicators, and selected-state highlights.

3. **Apply `font-feature-settings: "tnum"` on every financial number.**
   Tabular numerals ensure decimal points align, columns stack cleanly, and amounts are scannable in dense transaction lists.
   This applies to balances, transaction amounts, percentages, exchange rates, and any quantitative data.
   Verify: every element displaying monetary values includes `"tnum"` in computed styles.

4. **Use Aeonik Pro as the sole typeface across all text elements.**
   All text -- headings, body, labels, buttons, numbers -- uses Aeonik Pro with system sans-serif fallback.
   No secondary display font, no decorative face.
   The geometric neutrality of Aeonik Pro lets financial data be the visual protagonist.
   Verify: `font-family` on all text elements starts with `'Aeonik Pro'`.

5. **Create elevation through background color stepping, not shadows.**
   The dark surface hierarchy is:
   - `#191C1F` (page) -> `#1E2226` (card) -> `#252A2F` (raised) -> `#2C3238` (overlay)
   Each step is a subtle lighten that reads as elevation on dark.
   Shadows are reserved for modals and bottom sheets where dramatic depth is needed.
   Verify: cards and containers use progressively lighter backgrounds rather than `box-shadow` for hierarchy.

6. **Use the strict weight hierarchy: 700 for balance, 600 for headings, 500 for interactive, 400 for body.**
   Weight is the primary tool for information hierarchy in a single-typeface system.
   - Balance number at 700: the heaviest element on any screen
   - Headings at 600: anchor sections and features
   - Interactive elements at 500: buttons, nav links, amounts in lists
   - Descriptions and body at 400: recede behind the data
   Verify: no heading uses weight 400, no body text uses weight 600+.

7. **Maintain the 64px transaction row grid.**
   Every transaction list row is 64px tall with a consistent internal layout:
   - 40px circular merchant icon
   - 12px gap to text stack
   - Flexible merchant-name/category column
   - Right-aligned amount with tabular numerals
   This grid is the most-viewed component in the app and must be pixel-consistent.
   Verify: transaction rows have `height: 64px` and consistent internal spacing.

8. **Use `rgba(255,255,255,0.08)` for default borders and `rgba(255,255,255,0.05)` for transaction separators.**
   Borders on dark surfaces are white-alpha, not solid gray values.
   The alpha approach ensures they adapt if surface colors shift between themes or tiers.
   Heavier borders at `rgba(255,255,255,0.15)` are for card outlines and section dividers.
   Verify: border colors use `rgba(255,255,255,...)` with appropriate opacity, never solid hex gray.

9. **Apply negative letter-spacing on headings 24px and above.**
   Large Aeonik Pro text needs tracking tightened to maintain visual cohesion:
   - `-0.3px` at 24-32px
   - `-0.5px` at 40px+
   Without this, headlines feel loose and unprofessional at financial-app scale.
   Verify: headings >= 24px have negative `letter-spacing`.

10. **Use translucent accent backgrounds for status indicators and badges.**
    Status colors at 12% opacity create a tinted-glass effect on dark:
    - Success: `rgba(76,208,128,0.12)`
    - Error: `rgba(244,91,105,0.12)`
    - Warning: `rgba(245,166,35,0.12)`
    - Accent selection: `rgba(127,132,246,0.12)`
    Never use solid color fills for badges -- the translucency is what integrates them into the dark surface.
    Verify: badge and status backgrounds use `rgba()` at 0.12 opacity, not solid fills.

## Don'ts (10 items)

1. **Do not use pure black (`#000000`) as a surface color.**
   Pure black creates 21:1 contrast with white text, causing eye strain during long financial-data sessions.
   Shark (`#191C1F`) is deliberately softened to reduce fatigue while maintaining depth.
   Violation: any surface element with `background-color: #000000` or `background: black`.

2. **Do not use Cornflower Blue as a surface fill or decorative background.**
   Large cornflower areas destroy the scarcity that makes the accent meaningful.
   A full-width `#7F84F6` banner looks like a different product entirely.
   The accent must remain a point source of attention, not an ambient wash.
   Violation: `background-color: #7F84F6` on any container, section, or card larger than a button.

3. **Do not omit `"tnum"` on financial numbers.**
   Proportional numerals in a transaction list cause amounts to jitter horizontally.
   This makes data feel unreliable -- users subconsciously lose confidence when digits don't stack.
   This is the single most common implementation error in financial UI generation.
   Violation: any monetary value, percentage, or exchange rate rendered without `font-feature-settings: "tnum"`.

4. **Do not use warm-toned grays.**
   Revolut's secondary text (`#8B9098`) and tertiary text (`#5C6370`) are cool-toned with a slight blue undertone.
   Warm grays (tan, brown, olive) belong to editorial brands like Claude or Airbnb, not fintech.
   Violation: any text or border color with a visible warm/yellow/brown cast.

5. **Do not use light-mode shadow values on dark backgrounds.**
   Standard `rgba(0,0,0,0.1)` shadows are invisible against `#191C1F`.
   When shadows are needed (modals, overlays, bottom sheets), they must be aggressive:
   `rgba(0,0,0,0.35)` minimum opacity to register against dark.
   Violation: shadow values below 0.2 opacity that produce no visible separation on Shark surfaces.

6. **Do not exceed 3 accent-colored elements per viewport.**
   Revolut's interface discipline means cornflower appears on:
   1. The primary CTA
   2. The active navigation indicator
   3. Perhaps one selected state
   More than 3 creates visual noise in a data-dense financial interface.
   Violation: 4+ elements on a single viewport using `#7F84F6` as foreground or background color.

7. **Do not use large border-radius (20px+) on buttons.**
   Button radius is 8px. Card radius is 12-16px. Only pill chips and the virtual card display use large rounding.
   Oversized button radii look playful and undermine financial credibility.
   Violation: `border-radius: 20px`, `24px`, or `9999px` on a primary or secondary action button.

8. **Do not repurpose financial status colors for non-financial semantics.**
   Green (`#4CD080`) and red (`#F45B69`) carry strict financial meaning:
   - Green = gain / positive change / completed transfer
   - Red = loss / negative change / failed transaction
   Using them for generic form validation, toasts, or decorative purposes dilutes their financial signal.
   Violation: success green or error red used outside a financial data context.

9. **Do not use solid white borders on dark surfaces.**
   Full-opacity white borders (`#FFFFFF` or `rgba(255,255,255,1)`) create harsh fracture lines on the dark canvas.
   All borders use `rgba(255,255,255, 0.05-0.15)` range.
   Violation: `border-color: #FFFFFF` or `border: 1px solid white` on any dark-surface element.

10. **Do not introduce secondary typefaces.**
    No serif for "premium" headings, no display font for marketing, no handwritten accent.
    Aeonik Pro carries the entire typographic identity. Introducing a second face breaks the systematic financial personality.
    Even Inter or SF Pro as "close enough" replacements have different metrics and geometry.
    Violation: any `font-family` declaration that does not begin with `'Aeonik Pro'`.

## Critical Violations (5 items)

1. **Light/white page background instead of Shark (`#191C1F`).**
   Revolut is dark-mode-native. A white background fundamentally changes the product personality
   from "premium financial instrument" to "generic fintech landing page."
   The dark canvas is the brand's most recognizable design choice and the first thing users identify.

2. **Missing tabular numerals on financial data.**
   When transaction amounts, balances, or percentages render in proportional numerals,
   the entire data layer feels untrustworthy. Digits jump around, decimal points misalign,
   and users subconsciously lose confidence in the numbers.
   This is not a visual preference -- it is a functional requirement for financial software.

3. **Cornflower Blue used as a decorative surface fill.**
   Filling cards, sections, or backgrounds with `#7F84F6` turns a surgical accent into wallpaper.
   The color's power comes from its restraint -- it signals "this is the thing to tap."
   Flooding it across surfaces removes that signal and makes the interface feel like a children's app.

4. **Wrong typeface replacing Aeonik Pro.**
   Inter, SF Pro, or Roboto are common AI-generated defaults. Each has different metrics,
   different geometry, different personality. Aeonik Pro's specific letter shapes --
   the geometric lowercase a, the even stroke widths, the precise x-height --
   define how Revolut looks at a glance. Substituting destroys brand recognition.

5. **Flat weight hierarchy -- all text at the same weight.**
   Without the 700/600/500/400 weight cascade, a financial interface loses its information architecture.
   The user cannot instantly distinguish:
   - Balance (700) from heading (600)
   - Heading (600) from transaction amount (500)
   - Amount (500) from description (400)
   In a data-dense app, weight hierarchy IS navigation.
