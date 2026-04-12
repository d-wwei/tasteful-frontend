# Coinbase -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Coinbase-branded components.
Aesthetic: institutional crypto trust — clean white surfaces, Coinbase Blue restraint, financial-grade data clarity.

Typography: Coinbase Sans (custom typeface by Moniker, 2022). Publicly available at coinbase.com/press.
Fallback stack: Inter, -apple-system, BlinkMacSystemFont, sans-serif.

---

## 1. Quick Color Reference

```
Surface (page bg):     #ffffff     Pure white — trust foundation
Surface subtle:        #f9fafb     Gray50 — cards on white, sidebar bg
Accent (Coinbase Blue): #0052ff    Blue500 / bgPrimary — CTAs, links, active states
Accent hover:          #014cec     Blue550 — interactive hover
Accent tint:           #eef4ff     Selected rows, active badge bg
Text primary:          #0a0b0d     Black / Woodsmoke — headings, body
Text secondary:        #5b616e     Gray700 — descriptions, metadata
Text tertiary:         #9397a0     Gray500 — placeholders, timestamps
Border:                #dcdfe4     Gray200 — card edges, dividers
Border subtle:         #eef0f3     Gray100 — inner separators
Error / negative:      #cf202f     Red500 — price drops, form errors
Success / positive:    #098551     Green500 — price gains, confirmations
Warning:               #ed702f     Amber500 — pending states, gas warnings
```

---

## 2. Quick Typography Reference

```
Display:   'Coinbase Sans', Inter, sans-serif  | 48px | weight 600 | line-height 1.15 | tracking -0.02em
Title 1:   'Coinbase Sans', Inter, sans-serif  | 36px | weight 600 | line-height 1.20 | tracking -0.02em
Title 2:   'Coinbase Sans', Inter, sans-serif  | 28px | weight 600 | line-height 1.25 | tracking -0.01em
Title 3:   'Coinbase Sans', Inter, sans-serif  | 24px | weight 600 | line-height 1.25 | tracking 0
Headline:  'Coinbase Sans', Inter, sans-serif  | 20px | weight 600 | line-height 1.30 | tracking 0
Body:      'Coinbase Sans', Inter, sans-serif  | 16px | weight 400 | line-height 1.50 | tracking 0
Label:     'Coinbase Sans', Inter, sans-serif  | 14px | weight 500 | line-height 1.43 | tracking 0
Caption:   'Coinbase Sans', Inter, sans-serif  | 12px | weight 500 | line-height 1.33 | tracking 0.06em | uppercase
Legal:     'Coinbase Sans', Inter, sans-serif  | 11px | weight 400 | line-height 1.45 | tracking 0
Mono:      'Coinbase Mono', 'JetBrains Mono', monospace | 14px | weight 400 | line-height 1.50 | tracking 0
```

Key rules:
- Single font family for all text (Coinbase Sans) — unified, institutional feel
- Weight 600 for all headings, 500 for labels/buttons, 400 for body
- Caption is uppercase with wide tracking — used for table headers, category labels
- Monospace for crypto addresses, transaction hashes, and code snippets only

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Coinbase visual identity:
- Background: `#ffffff` (clean white surface)
- Container: max-width 1200px, centered, padding 96px 64px
- Headline: 48px Coinbase Sans, weight 600, line-height 1.15, letter-spacing -0.02em, color `#0a0b0d`
- Subtitle: 20px Coinbase Sans, weight 400, line-height 1.50, color `#5b616e`, max-width 560px, margin-top 16px
- CTA button: background `#0052ff`, color `#ffffff`, 16px weight 500, padding 12px 24px, border-radius 8px, border: none, cursor: pointer
- CTA hover: background `#014cec`
- Secondary button: background `#ffffff`, color `#0052ff`, 16px weight 500, padding 12px 24px, border-radius 8px, border: 1px solid `#dcdfe4`
- Secondary hover: border-color `#0052ff`
- Button row: flex, gap 12px, margin-top 32px
- Trust badge area: flex row of partner logos, 14px weight 400 label "Trusted by millions", color `#9397a0`, margin-top 48px
- On mobile (<480px): headline 32px, subtitle 17px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Coinbase visual identity:
- Background: `#ffffff`
- Border: 1px solid `#eef0f3` (subtle border)
- Border-radius: 12px
- Padding: 32px
- Box-shadow: `0 1px 2px rgba(0,0,0,0.05), 0 2px 8px rgba(0,0,0,0.04)` (level-1 elevation)
- Icon area: 48px circle, background `#eef4ff` (accent tint), Coinbase Blue icon inside, margin-bottom 20px
- Title: 24px Coinbase Sans, weight 600, line-height 1.25, color `#0a0b0d`, margin-bottom 8px
- Description: 16px weight 400, line-height 1.50, color `#5b616e`
- Link: 16px weight 500, color `#0052ff`, no underline, flex with right-arrow icon
- Hover: box-shadow intensifies to level-2, border-color `#dcdfe4`, transition 200ms ease
- On mobile (<480px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Coinbase visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#0052ff`, color `#ffffff`, font 16px Coinbase Sans weight 500, padding 12px 24px, border-radius 8px, border: none, cursor: pointer, transition: background 150ms ease
- Primary hover: background `#014cec`
- Primary active: background `#003ecb` (10% darker)
- Secondary button: background `#ffffff`, color `#0a0b0d`, font 16px weight 500, padding 12px 24px, border-radius 8px, border: 1px solid `#dcdfe4`
- Secondary hover: border-color `#0052ff`, color `#0052ff`
- Ghost button: background transparent, color `#0052ff`, font 16px weight 500, padding 12px 16px, border: none
- Ghost hover: background `#eef4ff`
- Disabled state: opacity 0.4, cursor not-allowed, no hover effect
- On mobile (<480px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Coinbase visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#eef0f3`
- Container: max-width 1200px, centered, padding 0 24px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Coinbase wordmark in `#0052ff` (brand blue logo), left-aligned
- Nav links: 14px Coinbase Sans, weight 500, color `#5b616e`, gap 32px, text-decoration none
- Nav link hover: color `#0a0b0d`, transition 150ms
- Nav link active: color `#0052ff`, position relative, with 2px bottom border in `#0052ff`
- CTA button (right): background `#0052ff`, color `#ffffff`, 14px weight 500, padding 8px 16px, border-radius 8px
- On mobile (<768px): nav links collapse to hamburger icon (`#0a0b0d`), CTA stays visible
- Backdrop-filter: blur(8px) with background `rgba(255,255,255,0.92)` for scroll-through effect

### Data Table / Portfolio View

Create a portfolio data table with Coinbase visual identity:
- Container: background `#ffffff`, border: 1px solid `#eef0f3`, border-radius 12px, overflow hidden
- Table header: background `#f9fafb`, padding 12px 16px, font 12px weight 500, color `#9397a0`, text-transform uppercase, letter-spacing 0.06em
- Table row: padding 16px, border-bottom 1px solid `#eef0f3`, display flex, align-items center
- Row hover: background `#f9fafb`, transition 100ms
- Asset name: 16px weight 500, color `#0a0b0d`, with 32px circle token icon left-aligned
- Price: 16px weight 400, color `#0a0b0d`, tabular-nums font-variant
- Change (positive): 14px weight 500, color `#098551`, prefix "+"
- Change (negative): 14px weight 500, color `#cf202f`, prefix "-"
- Sparkline: 64px wide, 24px tall, 1.5px stroke, color matches change direction
- Holdings: 16px weight 400, color `#0a0b0d`, right-aligned
- On mobile (<768px): hide sparkline column, stack price/change vertically

### Crypto Asset Card / Price Ticker

Create a crypto asset card with Coinbase visual identity:
- Background: `#ffffff`
- Border: 1px solid `#eef0f3`, border-radius 12px
- Padding: 24px
- Top row: flex, space-between, align-items center
- Token icon: 40px circle with token brand color background, white icon
- Token name: 16px weight 600, color `#0a0b0d` (e.g. "Bitcoin")
- Token symbol: 14px weight 400, color `#9397a0` (e.g. "BTC")
- Price: 28px weight 600, color `#0a0b0d`, font-variant-numeric: tabular-nums, margin-top 16px
- 24h change: 14px weight 500, margin-top 4px
- If positive: color `#098551`, display as "+2.34%" with up-arrow icon
- If negative: color `#cf202f`, display as "-1.12%" with down-arrow icon
- Sparkline chart: full width, height 64px, margin-top 16px, stroke 2px
- Sparkline color: `#098551` if positive period, `#cf202f` if negative
- Sparkline gradient fill: same color at 10% opacity to transparent
- Action buttons row: flex, gap 8px, margin-top 20px
- "Buy" button: background `#0052ff`, color `#ffffff`, 14px weight 500, padding 10px 20px, border-radius 8px, flex: 1
- "Sell" button: background `#ffffff`, border 1px solid `#dcdfe4`, color `#0a0b0d`, 14px weight 500, padding 10px 20px, border-radius 8px, flex: 1
- Hover on card: box-shadow transitions to level-2 elevation
- On mobile (<480px): padding 16px, price 24px

---

## 4. Iteration Guide

1. **White is the foundation — never darken the page canvas.** Coinbase's trust identity starts with `#ffffff` page backgrounds. The product handles billions in assets; the clean white surface signals institutional reliability. Use `#f9fafb` only for inset areas like table headers and sidebar backgrounds, never as the primary page background.

2. **Coinbase Blue is a verb, not a noun.** `#0052ff` marks actions: buttons you click, links you follow, states that are active. It never decorates. If an element is not interactive, it does not get Coinbase Blue. The accent tint `#eef4ff` is the only blue permitted on non-interactive surfaces (selected rows, active badges).

3. **Financial data demands tabular numerics.** Every price, balance, percentage, and quantity must use `font-variant-numeric: tabular-nums` so digits align in columns. Crypto portfolios live or die by scannable number columns. Monospace (`Coinbase Mono`) is reserved for addresses and hashes, not prices.

4. **Color encodes financial direction — green up, red down, nothing else.** Positive changes use `#098551`, negative use `#cf202f`. These colors never appear elsewhere in the UI. Do not use green for generic success badges or red for generic error styling in trading contexts — that creates dangerous ambiguity with price signals.

5. **Dense data, generous marketing.** Trading screens use tight spacing (8-12px gaps, 48-56px row heights). Marketing pages use generous spacing (80px section gaps, 96px hero padding). Never apply marketing spacing to data-dense screens or data-dense spacing to marketing pages.

6. **One font family, strict weight discipline.** Coinbase Sans everywhere. Weight 600 for headings, 500 for interactive elements (buttons, links, labels), 400 for body text. No weight 700+ exists in the system. If you see bold (700), fix it to 600.

7. **Border-radius 8px is the workhorse.** Buttons, inputs, standard cards, dropdowns — all 8px. Featured containers and modals step up to 12px. Pills (toggles, tags) go to 9999px. Do not use 4px on cards or 16px on buttons — both break the system.

8. **Shadows are functional, not decorative.** Level-1 shadows (subtle card lift) are the maximum for inline content. Level-2 (modals, popovers) appears only for overlapping UI. If a card has level-2 shadow by default, reduce it — elevation inflation destroys the depth hierarchy.

9. **Crypto addresses and hashes are always monospace.** Wallet addresses (`0x1234...abcd`), transaction hashes, and contract addresses must render in Coinbase Mono or JetBrains Mono. Truncate long addresses with ellipsis in the middle: `0x1234...abcd` (show first 6 + last 4 characters).

10. **Mobile trading is not a shrunk desktop.** On mobile, hide sparkline columns, stack price and percentage change vertically, increase touch targets to 48px minimum. The nav collapses to hamburger but the primary CTA ("Trade" / "Buy") always stays visible.
