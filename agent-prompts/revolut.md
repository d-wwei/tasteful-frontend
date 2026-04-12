# Revolut -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Revolut-branded components.
Aesthetic: dark-native fintech with restrained violet energy -- financial data density meets premium minimalism.

---

## 1. Quick Color Reference

```
Surface (page bg):     #191C1F   Shark -- dark canvas, never pure black
Surface card:          #1E2226   Elevated card -- one step above Shark
Surface raised:        #252A2F   Raised containers, modals, overlays
Accent CTA:            #7F84F6   Cornflower Blue -- Revolut's signature violet-blue
Accent hover:          #9599F8   Lighter cornflower for hover states
Accent pressed:        #6A6FE0   Deeper cornflower for pressed states
Accent muted bg:       rgba(127,132,246,0.12)   Selected rows, badge fills
Text primary:          #FFFFFF   Maximum contrast white
Text secondary:        #8B9098   Cool-toned gray for descriptions, metadata
Text tertiary:         #5C6370   Timestamps, disabled labels
Success (gain):        #4CD080   Positive financial change -- green
Error (loss):          #F45B69   Negative financial change -- coral-red
Warning:               #F5A623   Pending transactions -- amber
Border default:        rgba(255,255,255,0.08)   Subtle separation
Border prominent:      rgba(255,255,255,0.15)   Card outlines
```

---

## 2. Quick Typography Reference

```
Balance:     'Aeonik Pro', -apple-system, sans-serif  | 40px | weight 700 | line-height 1.10 | tracking -0.5px  | tnum
Display:     'Aeonik Pro', -apple-system, sans-serif  | 32px | weight 600 | line-height 1.20 | tracking -0.3px
Heading:     'Aeonik Pro', -apple-system, sans-serif  | 24px | weight 600 | line-height 1.20 | tracking -0.3px
Subheading:  'Aeonik Pro', -apple-system, sans-serif  | 20px | weight 600 | line-height 1.20 | tracking normal
Body Large:  'Aeonik Pro', -apple-system, sans-serif  | 17px | weight 400 | line-height 1.40 | tracking normal
Body:        'Aeonik Pro', -apple-system, sans-serif  | 15px | weight 400 | line-height 1.40 | tracking normal
Caption:     'Aeonik Pro', -apple-system, sans-serif  | 13px | weight 400 | line-height 1.40 | tracking normal
Micro:       'Aeonik Pro', -apple-system, sans-serif  | 11px | weight 500 | line-height 1.20 | tracking 0.8px
Tabular:     'Aeonik Pro', -apple-system, sans-serif  | 15px | weight 500 | line-height 1.40 | tnum
```

Key rules:
- `font-feature-settings: "tnum"` on ALL financial numbers -- tabular alignment is non-negotiable
- Aeonik Pro is a geometric sans-serif by CoType Foundry -- clean, neutral, modern
- Weight 500 for financial amounts in lists, weight 700 only for the primary account balance
- Weight 600 for section headings, 400 for body and descriptions
- Negative tracking on 24px+ headings, positive tracking on all-caps micro labels

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Revolut visual identity:
- Background: `#191C1F` (Shark dark)
- Container: max-width 1080px, centered, padding 80px 24px
- Headline: "One app. All things money." at 32px Aeonik Pro, weight 600, line-height 1.20, letter-spacing -0.3px, color `#FFFFFF`
- Subtitle: 17px Aeonik Pro, weight 400, line-height 1.40, color `#8B9098`, max-width 480px, margin-top 16px
- CTA button: background `#7F84F6`, color `#FFFFFF`, 15px Aeonik Pro weight 500, padding 12px 24px, border-radius 8px, border: none
- CTA hover: background `#9599F8`
- Secondary button: background transparent, color `#FFFFFF`, 15px weight 500, padding 12px 24px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.15)`
- Secondary hover: background `rgba(255,255,255,0.05)`
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<640px): headline 24px, subtitle 15px, section padding 48px 16px, buttons stack full-width

### Feature Card

Create a feature card with Revolut visual identity:
- Background: `#1E2226` (elevated surface)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 16px
- Padding: 24px
- Title: 20px Aeonik Pro, weight 600, line-height 1.20, color `#FFFFFF`
- Description: 15px Aeonik Pro, weight 400, line-height 1.40, color `#8B9098`, margin-top 8px
- Icon area: 44px square, background `rgba(127,132,246,0.12)`, border-radius 12px, centered cornflower icon
- Hover: border-color shifts to `rgba(255,255,255,0.15)`, transition 150ms
- On mobile (<640px): padding 20px, title 17px

### CTA Button Row

Create a CTA button row with Revolut visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#7F84F6`, color `#FFFFFF`, font 15px Aeonik Pro weight 500, padding 12px 24px, border-radius 8px, border: none, transition: background 150ms ease
- Primary hover: background `#9599F8`
- Primary pressed: background `#6A6FE0`
- Ghost button: background transparent, color `#FFFFFF`, font 15px Aeonik Pro weight 500, padding 12px 24px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.15)`
- Ghost hover: background `rgba(255,255,255,0.05)`, border-color `rgba(255,255,255,0.25)`
- Pill chip: background `rgba(127,132,246,0.12)`, color `#7F84F6`, font 13px weight 500, padding 6px 12px, border-radius 9999px
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Revolut visual identity:
- Background: `#191C1F`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.08)`
- Container: max-width 1080px, centered, padding 0 24px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Revolut wordmark in `#FFFFFF`, left-aligned
- Nav links: 15px Aeonik Pro, weight 500, color `#8B9098`, line-height 1.0, gap 24px, text-decoration none
- Nav link hover: color `#FFFFFF`, transition 150ms
- Nav link active: color `#FFFFFF`, position relative, ::after pseudo-element 2px height `#7F84F6` indicator bar
- CTA button (right): background `#7F84F6`, color `#FFFFFF`, 13px weight 500, padding 8px 16px, border-radius 8px
- On mobile (<640px): nav links collapse to hamburger, bottom tab bar with 5 icons

### Data Card / Metric Display

Create a metric display card with Revolut visual identity:
- Background: `#1E2226`
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 16px
- Padding: 24px
- Overline label: 11px Aeonik Pro, weight 500, line-height 1.20, letter-spacing 0.8px, text-transform uppercase, color `#5C6370`, margin-bottom 8px
- Metric value: 32px Aeonik Pro, weight 600, line-height 1.20, letter-spacing -0.3px, color `#FFFFFF`, font-feature-settings: "tnum"
- Metric trend: 13px Aeonik Pro weight 500, color `#4CD080` (positive) or `#F45B69` (negative), display inline-flex, align-items center, gap 4px with arrow icon
- Metric description: 15px Aeonik Pro, weight 400, line-height 1.40, color `#8B9098`, margin-top 8px
- On mobile (<640px): metric value 24px, padding 20px

### Transaction Card / Account Balance Display

Create a transaction list with account balance header using Revolut visual identity:
- **Balance header section:**
  - Background: `#191C1F` (flush with page)
  - Balance amount: 40px Aeonik Pro, weight 700, line-height 1.10, letter-spacing -0.5px, color `#FFFFFF`, font-feature-settings: "tnum"
  - Currency label: 13px weight 500, color `#8B9098`, margin-bottom 4px
  - Balance change: 15px weight 500, color `#4CD080` (positive) or `#F45B69` (negative), margin-top 4px
  - Account selector: pill-shaped, background `#252A2F`, border-radius 9999px, padding 6px 16px, 13px weight 500, color `#FFFFFF`, with chevron icon

- **Transaction list:**
  - Container: background `#1E2226`, border-radius 16px, overflow hidden
  - Section date header: 11px weight 500, text-transform uppercase, letter-spacing 0.8px, color `#5C6370`, padding 16px 16px 8px
  - Transaction row: height 64px, padding 0 16px, display flex, align-items center, border-bottom 1px solid `rgba(255,255,255,0.05)`
  - Merchant icon: 40px circle, background `#252A2F`, centered merchant logo or category icon
  - Merchant name: 15px weight 500, color `#FFFFFF`, flex 1, margin-left 12px
  - Transaction category: 13px weight 400, color `#5C6370`, below merchant name
  - Amount: 15px weight 500, color `#FFFFFF`, text-align right, font-feature-settings: "tnum"
  - Amount negative: color `#FFFFFF` (spending is neutral tone in Revolut)
  - Amount positive (refund/income): color `#4CD080`
  - Row hover: background `rgba(255,255,255,0.03)`
  - Row active/pressed: background `rgba(255,255,255,0.06)`

- **Empty state:**
  - Illustration: simple line art, cornflower accent color
  - Message: 17px weight 500, color `#FFFFFF`, centered
  - Submessage: 15px weight 400, color `#8B9098`, margin-top 8px

---

## 4. Iteration Guide

1. **Dark surfaces are the native state, not an option.** Every component starts on `#191C1F` Shark. Light mode is a secondary adaptation, not the default. If a generated component has white or light-gray backgrounds, it is wrong -- rebuild on Shark.

2. **Cornflower Blue is surgical, not decorative.** `#7F84F6` appears only on primary CTAs, active indicators, and the most important interactive moments. In a typical screen, fewer than 3 elements should use the accent color. If your component has cornflower on backgrounds, large fills, or decorative elements, you have overused it.

3. **Financial numbers MUST use tabular numerals.** Every monetary amount, percentage, or quantitative value needs `font-feature-settings: "tnum"`. This ensures columns align, decimal points stack, and the data-dense interface reads cleanly. Missing tnum on a balance display is a critical error.

4. **Elevation comes from background shifts, not shadows.** On dark surfaces, shadows are nearly invisible. Revolut creates hierarchy through progressively lighter surface colors: `#191C1F` -> `#1E2226` -> `#252A2F` -> `#2C3238`. Shadows exist only for modals and overlays where the depth must be dramatic (level-2 and level-3).

5. **Transaction rows are the atomic unit.** The transaction list is the most-viewed screen in any financial app. Every row follows a rigid grid: 40px circle icon / 12px gap / name+category stack / flexible space / right-aligned amount with tnum. Do not deviate from this structure.

6. **Aeonik Pro's geometry carries the personality.** The font is clean, geometric, and neutral -- it does not compete with the financial data. Weight distribution matters: 700 for the balance, 600 for headings, 500 for interactive text and amounts, 400 for descriptions. If all text is the same weight, the hierarchy is broken.
