# Coinbase -- Design Guardrails

## Do's (10 items)

1. **Use `#ffffff` as the primary page background.**
   White is Coinbase's trust foundation — it signals the institutional sobriety
   of a platform holding billions in customer assets. The white canvas gives
   Coinbase Blue its full signal strength by contrast.
   Verify: the `<body>` or main page wrapper has `background-color: #ffffff`.

2. **Reserve Coinbase Blue (`#0052ff`) exclusively for interactive elements.**
   Buttons, links, active tab indicators, toggle-on states, and progress bars.
   The accent must remain scarce so it always reads as "this is clickable" or
   "this is active." When blue appears, the user's eye should move to it.
   Verify: `#0052ff` appears only on elements with interactive affordance —
   never on decorative backgrounds, illustrations, or passive text.

3. **Use the CDS semantic color triplet for financial data.**
   `#098551` green for gains, `#cf202f` red for losses, `#ed702f` amber for
   pending or warning states. These are not decoration — they are real-time
   financial signals. Users make money decisions based on these colors.
   Verify: positive price changes are green, negative are red, and neither
   color appears in contexts unrelated to financial direction.

4. **Apply `font-variant-numeric: tabular-nums` on all monetary values.**
   Prices, balances, percentages, and quantities must use tabular (fixed-width)
   numerals so digits align in columns and values are scannable at a glance.
   This is critical for portfolio tables and ticker displays.
   Verify: any element displaying a number followed by a currency symbol or
   percentage sign uses tabular numerics.

5. **Use Coinbase Sans as the sole typeface, with Inter as the fallback.**
   The full stack is `'Coinbase Sans', Inter, -apple-system, BlinkMacSystemFont, sans-serif`.
   Every element from display headlines to button labels uses this single family.
   The unified type system projects institutional coherence.
   Verify: no other font family appears in any CSS rule except the monospace
   stack for crypto addresses and code.

6. **Maintain the 8px spatial grid.**
   All padding, margin, and gap values must be multiples of 4px (with 8px as
   the primary unit). This creates the mechanical consistency that financial
   users trust. The grid applies to both marketing pages and trading screens.
   Verify: inspect any spacing value and confirm it divides evenly by 4.

7. **Use 8px border-radius for standard interactive elements.**
   Buttons, inputs, cards, and dropdowns all get 8px. Step up to 12px for
   featured containers and modals. Use 9999px for pills, toggles, and avatar
   circles. This three-tier system keeps the UI consistent.
   Verify: buttons are 8px, not 4px (too sharp) or 16px (too soft).

8. **Render crypto addresses and transaction hashes in monospace.**
   Wallet addresses (`0x1a2b...9z`), tx hashes, and contract addresses must
   use Coinbase Mono or JetBrains Mono. Truncate with middle ellipsis: show
   first 6 + last 4 characters. The full address goes in a copy-to-clipboard
   tooltip on hover or tap.
   Verify: any hex string on screen renders in monospace with middle truncation.

9. **Differentiate data-dense screens from marketing pages through spacing.**
   Trading and portfolio screens use tight spacing (8-12px gaps, compact rows
   under 64px height). Marketing and landing pages use generous spacing (80px
   section gaps, 96px hero padding). These are two distinct spacing modes.
   Verify: a portfolio table row is under 64px tall; a marketing section has
   at least 80px top/bottom padding.

10. **Ensure all interactive elements meet a 48px minimum touch target on mobile.**
    Buttons, table rows, and nav items must have at least 48px of tappable area.
    Crypto trading on mobile is high-stakes — mis-taps can trigger wrong trades.
    This applies to Buy/Sell buttons, asset row taps, and portfolio actions.
    Verify: tap every interactive element on a 375px viewport and confirm
    the target is large enough for comfortable one-thumb operation.

## Don'ts (10 items)

1. **Do not use Coinbase Blue (`#0052ff`) as a background fill on any surface.**
   A blue hero section, a blue card, a blue sidebar — all wrong. Blue is
   reserved for interactive UI. Using it as a surface fill eliminates its signal
   value and makes the brand look like a generic tech company.
   The only permitted blue surface is the accent tint `#eef4ff` for
   selected/active states.

2. **Do not use green (`#098551`) or red (`#cf202f`) for non-financial signals.**
   A green "success" badge next to a trading table creates dangerous ambiguity —
   does green mean "transaction succeeded" or "price went up"? In a financial
   product, these colors carry fiduciary meaning.
   Use Coinbase Blue for generic confirmations and `#9397a0` for neutral states.

3. **Do not introduce colors outside the defined palette.**
   No purple, teal, orange (beyond `#ed702f` warning), or custom blues.
   Coinbase's color discipline is deliberate — a narrow palette on a white
   surface creates the institutional trust that a crypto exchange requires.
   Every new color dilutes that trust.

4. **Do not use font-weight 700 or higher.**
   Coinbase Sans caps at weight 600 (semibold) for headings. Bold (700) creates
   visual aggression that contradicts the platform's calm authority. If a heading
   feels too light, increase the font size, not the weight.
   Verify: no CSS rule contains `font-weight: 700`, `bold`, or `bolder`.

5. **Do not use proportional numerals in financial data contexts.**
   Proportional numerals make number columns jitter, making it impossible to
   scan a portfolio quickly. Users compare prices by vertical column alignment.
   This is not a stylistic preference — it is a financial data legibility
   requirement.
   Verify: disable `font-variant-numeric: proportional-nums` in any table,
   ticker, or balance display.

6. **Do not use heavy drop shadows on cards.**
   Coinbase's elevation system is subtle: level-1 is barely visible, level-2 is
   only for overlapping UI (modals, popovers). A card with a prominent shadow
   looks like a 2014 Material Design mockup, not a modern financial product.
   Verify: no card has `box-shadow` blur exceeding 32px at opacity > 0.08.

7. **Do not round buttons beyond 8px or sharpen them below 6px.**
   8px is the system radius for interactive elements. A 16px or 24px radius
   turns buttons into pills — that reads as a toggle, not a CTA. A 2px or 0px
   radius feels like an enterprise admin panel, not a consumer product.
   Verify: primary and secondary buttons use `border-radius: 8px`.

8. **Do not display full-length crypto addresses without truncation.**
   A 42-character Ethereum address overwhelms any layout. Always truncate to
   `0x742d...2bD28` (6 prefix + 4 suffix) with middle ellipsis. The full
   address goes in a copy-to-clipboard tooltip, not inline text.
   Verify: no visible hex string exceeds approximately 14 characters.

9. **Do not apply marketing-level spacing to data screens.**
   80px section gaps and 96px hero padding belong on landing pages, not trading
   dashboards. A portfolio screen with marketing spacing wastes 60% of viewport
   on whitespace — users came to see prices, not art.
   Verify: data-dense screens use 8-16px gaps between rows, not 32px+.

10. **Do not use serif fonts, script fonts, or decorative typefaces anywhere.**
    Coinbase Sans is a geometric sans-serif designed for financial clarity.
    A serif headline or decorative accent font introduces friction and erodes
    the institutional trust that the unified type system builds.
    Verify: zero `serif` or decorative font-family declarations in the
    stylesheet. The only non-sans font allowed is monospace for addresses.

## Critical Violations (5 items)

1. **Coinbase Blue used as a surface fill.**
   Flooding any area with `#0052ff` as a background destroys the interactive
   signal-to-noise ratio. When everything is blue, nothing is a button. This is
   the single most common brand violation and the most damaging — it converts a
   precise, trustworthy financial interface into a generic "tech blue" page.
   The accent color must remain scarce: buttons, links, active indicators only.

2. **Green/red financial colors used for non-financial signals.**
   Using `#098551` for a "verified" badge or `#cf202f` for a form error in a
   screen that also shows price changes creates fiduciary confusion. Users may
   misread account status as market movement. In a platform where users make
   real-money decisions, color ambiguity is not a design issue — it is a
   liability. Use Coinbase Blue or neutral gray for non-financial status.

3. **Missing tabular numerics on financial data.**
   When prices and balances render in proportional numerals, column alignment
   breaks. Users scanning a portfolio cannot quickly compare values. This is
   not an aesthetic issue — it is a usability failure that can cause users to
   misread their own balances. Every number in a financial context must use
   `font-variant-numeric: tabular-nums`.

4. **Non-system fonts replacing Coinbase Sans.**
   Introducing a second typeface (especially a serif or display font) fractures
   the unified type identity. Coinbase Sans was custom-designed by Moniker in
   2022 specifically for financial clarity and brand cohesion. Replacing it with
   Roboto, Helvetica, or any other font removes the single most visible brand
   differentiator. The fallback is Inter, not a replacement.

5. **Heavy elevation shadows creating floating-card illusion.**
   Level-2+ shadows on standard content cards make the interface feel layered
   and complex rather than flat and trustworthy. Financial products need to feel
   grounded and transparent — cards should sit within the page, not hover above
   it. Reserve level-2 elevation for UI that genuinely overlaps: modals,
   dropdowns, tooltips, and popovers. Everything else stays at level-0 or
   level-1.
