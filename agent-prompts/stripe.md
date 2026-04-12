# Stripe -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Stripe-branded components.
Aesthetic: weight-300 elegance with blue-tinted shadows -- technical luxury for fintech.

---

## 1. Quick Color Reference

```
Surface (page bg):     #ffffff   Pure White -- clean canvas
Dark section:          #1c1e54   Brand Dark -- deep indigo for immersive sections
Darkest neutral:       #0d253d   Dark Navy -- almost-black with blue undertone
Accent CTA:            #533afd   Stripe Purple -- saturated blue-violet
Accent hover:          #4434d4   Purple Hover -- darker for hover states
Text heading:          #061b31   Deep Navy -- never use pure black for headings
Text body:             #64748d   Slate -- secondary descriptions, captions
Text label:            #273951   Dark Slate -- form labels, secondary headings
Border default:        #e5edf5   Soft Blue -- cards, dividers, containers
Border active:         #b9b9f9   Lavender Purple -- selected/active state borders
Decorative ruby:       #ea2261   Ruby -- gradient/decorative only, not interactive
Decorative magenta:    #f96bee   Magenta -- gradient endpoints only
```

---

## 2. Quick Typography Reference

```
Display Hero:   sohne-var, SF Pro Display  | 56px | weight 300 | line-height 1.03 | letter-spacing -1.4px  | font-feature-settings: "ss01"
Display Large:  sohne-var, SF Pro Display  | 48px | weight 300 | line-height 1.15 | letter-spacing -0.96px | font-feature-settings: "ss01"
Section:        sohne-var, SF Pro Display  | 32px | weight 300 | line-height 1.10 | letter-spacing -0.64px | font-feature-settings: "ss01"
Subheading:     sohne-var, SF Pro Display  | 22px | weight 300 | line-height 1.10 | letter-spacing -0.22px | font-feature-settings: "ss01"
Body Large:     sohne-var, SF Pro Display  | 18px | weight 300 | line-height 1.40 | letter-spacing normal   | font-feature-settings: "ss01"
Body:           sohne-var, SF Pro Display  | 16px | weight 300 | line-height 1.40 | letter-spacing normal   | font-feature-settings: "ss01"
Button:         sohne-var, SF Pro Display  | 16px | weight 400 | line-height 1.00 | letter-spacing normal   | font-feature-settings: "ss01"
Caption:        sohne-var, SF Pro Display  | 13px | weight 400 | line-height 1.00 | letter-spacing normal   | font-feature-settings: "ss01"
Caption Tab:    sohne-var, SF Pro Display  | 12px | weight 300 | line-height 1.33 | letter-spacing -0.36px  | font-feature-settings: "tnum"
Code:           SourceCodePro, SFMono-Regular | 12px | weight 500 | line-height 2.00 | letter-spacing normal
```

Key rules:
- `font-feature-settings: "ss01"` on ALL sohne-var text -- this is the brand's typographic DNA
- Use `"tnum"` instead of `"ss01"` for tabular/financial numbers (never combine them)
- Weight 300 for headlines AND body -- lightness is the signature
- Weight 400 only for buttons, links, and navigation
- Negative letter-spacing tightens proportionally with size

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Stripe visual identity:
- Background: `#ffffff`
- Container: max-width 1080px, centered, padding 80px 64px
- Headline: "Ship Faster" at 56px sohne-var, weight 300, line-height 1.03, letter-spacing -1.4px, color `#061b31`, font-feature-settings: "ss01"
- Subtitle: 18px sohne-var, weight 300, line-height 1.40, color `#64748d`, max-width 540px, margin-top 20px, font-feature-settings: "ss01"
- CTA button: background `#533afd`, color `#ffffff`, 16px sohne-var weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px, border: none, cursor pointer
- CTA hover: background `#4434d4`
- Ghost button: background transparent, color `#533afd`, 16px weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px, border: 1px solid `#b9b9f9`
- Ghost hover: background `rgba(83,58,253,0.05)`
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<640px): headline 32px, letter-spacing -0.64px, subtitle 16px, section padding 40px 20px, buttons stack full-width

### Feature Card

Create a feature card with Stripe visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e5edf5`
- Border-radius: 6px
- Padding: 32px
- Box-shadow: `rgba(50,50,93,0.25) 0px 30px 45px -30px, rgba(0,0,0,0.1) 0px 18px 36px -18px`
- Title: 22px sohne-var, weight 300, line-height 1.10, letter-spacing -0.22px, color `#061b31`, font-feature-settings: "ss01"
- Description: 16px sohne-var, weight 300, line-height 1.40, color `#64748d`, font-feature-settings: "ss01", margin-top 12px
- Hover: shadow intensifies, transition 300ms ease
- On mobile (<640px): padding 24px, title 18px letter-spacing normal

### CTA Button Row

Create a CTA button row with Stripe visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#533afd`, color `#ffffff`, font 16px sohne-var weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px, border: none, transition: background 200ms ease
- Primary hover: background `#4434d4`
- Ghost button: background transparent, color `#533afd`, font 16px sohne-var weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px, border: 1px solid `#b9b9f9`
- Ghost hover: background `rgba(83,58,253,0.05)`
- Info button: background transparent, color `#2874ad`, font 14px weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px, border: 1px solid `rgba(43,145,223,0.2)`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Stripe visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100, backdrop-filter: blur(12px)
- Container: max-width 1080px, centered, padding 0 64px, height 60px, display flex, align-items center, justify-content space-between
- Border-radius on nav container: 6px (when floating)
- Logo: Stripe wordmark left-aligned in `#061b31`
- Nav links: 14px sohne-var, weight 400, color `#061b31`, line-height 1.0, font-feature-settings: "ss01", gap 24px, text-decoration none
- Nav link hover: color `#533afd`, transition 150ms
- CTA button (right): background `#533afd`, color `#ffffff`, 14px weight 400, font-feature-settings: "ss01", padding 8px 16px, border-radius 4px
- On mobile (<640px): nav links collapse to hamburger with 6px radius toggle button

### Data Card / Metric Display

Create a metric display card with Stripe visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e5edf5`
- Border-radius: 8px (featured)
- Padding: 32px
- Box-shadow: `rgba(23,23,23,0.08) 0px 15px 35px 0px`
- Label: 13px sohne-var, weight 400, line-height 1.0, color `#64748d`, font-feature-settings: "ss01", margin-bottom 8px
- Metric value: 48px sohne-var, weight 300, line-height 1.15, letter-spacing -0.96px, color `#061b31`, font-feature-settings: "tnum"
- Metric description: 16px sohne-var, weight 300, line-height 1.40, color `#64748d`, font-feature-settings: "ss01", margin-top 12px
- Success badge (inline): background `rgba(21,190,83,0.2)`, color `#108c3d`, 10px sohne-var weight 300, padding 1px 6px, border-radius 4px, border: 1px solid `rgba(21,190,83,0.4)`
- On mobile (<640px): metric value 32px, letter-spacing -0.64px, padding 24px

### Dark Brand Section

Create a dark brand section with Stripe visual identity:
- Background: `#1c1e54` (Brand Dark indigo -- not black, not gray)
- Section padding: 80px 64px
- Container: max-width 1080px, centered
- Headline: 32px sohne-var, weight 300, line-height 1.10, letter-spacing -0.64px, color `#ffffff`, font-feature-settings: "ss01"
- Body text: 16px sohne-var, weight 300, line-height 1.40, color `rgba(255,255,255,0.7)`, font-feature-settings: "ss01"
- Cards inside: background `rgba(255,255,255,0.06)`, border 1px solid `rgba(255,255,255,0.1)`, border-radius 6px, padding 24px
- Card title: 22px weight 300, color `#ffffff`, font-feature-settings: "ss01"
- Card body: 14px weight 300, color `rgba(255,255,255,0.7)`, font-feature-settings: "ss01"
- On mobile (<640px): section padding 40px 20px, headline 26px, letter-spacing -0.26px

---

## 4. Iteration Guide

1. **Never forget `font-feature-settings: "ss01"` on sohne-var text.** This is non-negotiable. The `ss01` stylistic set modifies character shapes (alternate a, g, l forms) to create Stripe's geometric personality. Without it, the typography is generic. Use `"tnum"` only for financial data in tables and charts.

2. **Weight 300 is the default, not weight 400.** Stripe's most distinctive choice is using light-weight headlines. Weight 400 is reserved exclusively for buttons, links, and navigation. If a heading is generated at 400 or above, reduce it to 300.

3. **Shadows must be blue-tinted.** The signature shadow formula is: `rgba(50,50,93,0.25) 0px Y1 B1 -S1, rgba(0,0,0,0.1) 0px Y2 B2 -S2` where the first layer (blue-tinted, far) and second layer (neutral, near) create a parallax depth effect. Never use neutral-only gray shadows.

4. **Heading color is `#061b31`, never `#000000`.** Deep navy replaces black throughout the system. The warmth of this dark blue is what separates Stripe from generic designs. Body text is `#64748d` (slate), labels are `#273951` (dark slate).

5. **Border-radius stays in the 4px-8px range.** Stripe uses conservative rounding -- 4px for buttons/badges, 5-6px for cards, 8px maximum for featured elements. Never use pill shapes (9999px) or large rounding (12px+) on action elements.

6. **Dark sections use `#1c1e54`, not black.** The branded deep indigo creates an immersive experience that stays on-brand. Text on dark sections uses white (`#ffffff`) for headings and `rgba(255,255,255,0.7)` for body text.
