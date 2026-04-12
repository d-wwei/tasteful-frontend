# Uber -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Uber-branded components.
Aesthetic: dark ride-share with monochromatic precision -- black canvas, white signal, luminance-based depth.

DARK BRAND: All components render on `#000000` backgrounds by default. White is accent, not surface.

---

## 1. Quick Color Reference

```
Surface (page bg):       #000000   Pure Black -- the canvas, always the default
Surface elevated:        #141414   Dark Gray -- cards, panels, nav overlays
Surface raised:          #1a1a1a   Slightly Lighter -- modals, popovers, active states
Accent:                  #ffffff   Pure White -- the ONLY accent on dark surfaces
Accent hover:            rgba(255,255,255,0.85)  Dimmed White -- hover/pressed states
Text primary:            #ffffff   White -- headings, body text on dark
Text secondary:          #afafaf   Mid Gray -- descriptions, metadata, inactive nav
Text tertiary:           #6b6b6b   Dark Gray -- timestamps, fine print, disabled
Text on accent:          #000000   Black -- text on white buttons
Uber Green (Eats):       #06c167   Sub-brand green -- success states only
Uber Blue (Freight):     #276ef1   Sub-brand blue -- focus rings only
Warning:                 #f5a623   Amber -- surge pricing, caution alerts
Error:                   #e11d48   Red -- cancellation, critical errors
Border dark:             rgba(255,255,255,0.08)  Barely visible luminance edge
Border dark prominent:   rgba(255,255,255,0.15)  Dividers, active states
```

---

## 2. Quick Typography Reference

```
Display:    "Uber Move", system-ui, sans-serif     | 52px | weight 700 | line-height 1.10 | letter-spacing -0.02em
Heading:    "Uber Move", system-ui, sans-serif     | 36px | weight 500 | line-height 1.10 | letter-spacing -0.02em
Title:      "Uber Move", system-ui, sans-serif     | 24px | weight 500 | line-height 1.25 | letter-spacing 0
Subtitle:   "Uber Move Text", system-ui, sans-serif| 18px | weight 500 | line-height 1.25 | letter-spacing 0
Body:       "Uber Move Text", system-ui, sans-serif| 16px | weight 400 | line-height 1.50 | letter-spacing 0
Caption:    "Uber Move Text", system-ui, sans-serif| 14px | weight 400 | line-height 1.43 | letter-spacing 0
Small:      "Uber Move Text", system-ui, sans-serif| 12px | weight 400 | line-height 1.33 | letter-spacing 0
```

Key rules:
- Uber Move (display variant) for all headings at 24px and above
- Uber Move Text (text variant) for body, captions, UI labels at 18px and below
- Weight 500 is the workhorse heading weight. 700 reserved for hero display only
- Tight letter-spacing (-0.02em) on display sizes (36px+) for dense, confident feel
- Never use weight 300/light -- Uber typography is medium-to-bold, never thin

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Uber visual identity:
- Background: `#000000` (pure black canvas)
- Container: max-width 1200px, centered, padding 96px 64px
- Headline: "Move the way you want" at 52px Uber Move, weight 700, line-height 1.10, letter-spacing -0.02em, color `#ffffff`
- Subtitle: 18px Uber Move Text, weight 400, line-height 1.50, color `#afafaf`, max-width 560px, margin-top 20px
- CTA button: background `#ffffff`, color `#000000`, 16px Uber Move Text weight 500, padding 14px 28px, border-radius 8px, border: none, cursor pointer, transition: background 150ms ease-out
- CTA hover: background `rgba(255,255,255,0.85)`
- Secondary button: background transparent, color `#ffffff`, border 1px solid `rgba(255,255,255,0.15)`, 16px weight 500, padding 14px 28px, border-radius 8px
- Secondary hover: border-color `rgba(255,255,255,0.30)`
- Button row: flex, gap 16px, margin-top 40px
- Hero image area: right half or full-width background, dark photography with high contrast, no gradient overlays -- Uber lets photography speak
- On mobile (<480px): headline 36px, subtitle 16px, padding 64px 20px, buttons stack full-width, gap 12px

### Feature Card

Create a feature card with Uber visual identity:
- Background: `#141414` (elevated dark surface)
- Border: 1px solid `rgba(255,255,255,0.08)` (luminance border, NOT traditional shadow)
- Border-radius: 12px
- Padding: 32px
- No box-shadow -- elevation comes from surface color stepping and luminance borders, not drop shadows
- Icon area: 48px square container, `rgba(255,255,255,0.08)` background, border-radius 8px, icon in `#ffffff` at 24px, margin-bottom 24px
- Title: 24px Uber Move, weight 500, line-height 1.25, color `#ffffff`, margin-bottom 8px
- Description: 16px Uber Move Text, weight 400, line-height 1.50, color `#afafaf`
- Hover state: border-color shifts to `rgba(255,255,255,0.15)`, transition 150ms ease-out
- On mobile (<480px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Uber visual identity:
- Layout: flex, gap 16px, align-items center
- Primary button (White on Black): background `#ffffff`, color `#000000`, font 16px Uber Move Text weight 500, padding 14px 28px, border-radius 8px, border: none, cursor pointer, transition: background 150ms ease-out
- Primary hover: background `rgba(255,255,255,0.85)`
- Primary active: background `rgba(255,255,255,0.75)`, transform scale(0.98), transition 100ms
- Secondary button (Ghost): background transparent, color `#ffffff`, border 1px solid `rgba(255,255,255,0.15)`, font 16px weight 500, padding 14px 28px, border-radius 8px
- Secondary hover: border-color `rgba(255,255,255,0.30)`, background `rgba(255,255,255,0.04)`
- Tertiary button (Text only): background transparent, color `#ffffff`, font 16px weight 500, padding 14px 8px, border: none, text-decoration underline with underline-offset 4px
- Dark surface variant (inverted): Primary becomes background `#000000`, color `#ffffff`, border 1px solid `rgba(255,255,255,0.15)` on light surfaces
- On mobile (<480px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Uber visual identity:
- Background: `#000000`, position sticky, top 0, z-index 100
- No border-bottom -- Uber nav is borderless, flush with the black canvas
- Container: max-width 1200px, centered, padding 0 64px, height 72px, display flex, align-items center, justify-content space-between
- Logo: Uber wordmark SVG in `#ffffff`, height 20px, left-aligned
- Nav links: 14px Uber Move Text, weight 500, color `#afafaf`, gap 32px, text-decoration none, transition: color 150ms ease-out
- Nav link hover: color `#ffffff`
- Nav link active: color `#ffffff`, no underline -- active state is color-only
- CTA button (right): background `#ffffff`, color `#000000`, 14px Uber Move Text weight 500, padding 10px 20px, border-radius 8px
- Mobile (<768px): nav links collapse to hamburger icon (3 horizontal lines, `#ffffff`, 24px), CTA remains visible
- Mobile menu: full-screen overlay, background `#000000`, links stacked vertically at 24px Uber Move weight 500, padding 24px, gap 24px

### Metric Display

Create a metric display component with Uber visual identity:
- Background: `#141414` (elevated surface)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 32px
- Overline label: 12px Uber Move Text, weight 500, line-height 1.33, text-transform uppercase, letter-spacing 0.08em, color `#6b6b6b`, margin-bottom 12px
- Metric value: 52px Uber Move, weight 700, line-height 1.10, letter-spacing -0.02em, color `#ffffff`
- Metric unit/suffix: same line as value, 24px Uber Move, weight 500, color `#afafaf`, margin-left 4px
- Description: 14px Uber Move Text, weight 400, line-height 1.43, color `#afafaf`, margin-top 12px
- Trend indicator: inline pill, 12px weight 500, padding 4px 8px, border-radius 999px. Positive: background `rgba(6,193,103,0.12)`, color `#06c167`. Negative: background `rgba(225,29,72,0.12)`, color `#e11d48`
- Grid layout: display grid, grid-template-columns repeat(auto-fit, minmax(240px, 1fr)), gap 16px
- On mobile (<480px): padding 24px, metric value 36px, single column

### Brand-Specific: Ride Pricing Card

Create a ride pricing card with Uber visual identity -- the signature component that appears when selecting a ride type:
- Background: `#141414` (elevated surface)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 0 (internal layout handles spacing)
- Structure: horizontal row, 80px height, display flex, align-items center, padding 16px 20px, gap 16px
- Vehicle icon: 48x48 container, no background, vehicle silhouette illustration or icon in `#ffffff`
- Content area: flex 1, display flex, flex-direction column, gap 2px
  - Ride name: 16px Uber Move Text, weight 500, color `#ffffff` (e.g., "UberX", "Comfort", "Black")
  - ETA / details: 14px Uber Move Text, weight 400, color `#afafaf` (e.g., "4 min away -- 3:42 PM dropoff")
- Price area: text-align right
  - Price: 16px Uber Move Text, weight 500, color `#ffffff` (e.g., "$24.50")
  - Surge indicator (when active): 12px weight 500, color `#f5a623`, display flex, align-items center, gap 4px with lightning bolt icon
- Selected state: border-color `#ffffff`, background `#1a1a1a`
- Hover state: background `#1a1a1a`, transition 150ms ease-out
- List container: display flex, flex-direction column, gap 0, border-radius 12px, overflow hidden. Each card separated by 1px solid `rgba(255,255,255,0.06)` divider
- Promo badge (optional): position absolute, top -8px, right 16px, 12px Uber Move Text weight 500, padding 4px 10px, background `#06c167`, color `#ffffff`, border-radius 999px, text-transform uppercase
- On mobile: full-width, padding 14px 16px

---

## 4. Iteration Guide

1. **Black is the canvas, not a color choice.** Every component starts on `#000000`. This is not "dark mode" -- it is the brand's native state. The pure black lets content and photography deliver all visual energy. Never replace it with dark gray (`#1a1a1a`, `#222`) as the page background.

2. **White is the only accent.** On dark surfaces, `#ffffff` is the accent color. It appears on primary CTA buttons, active nav states, and high-priority text. Do not introduce colored accents (blue, green, orange) for UI chrome -- those are reserved for sub-brands (Eats green, Freight blue) and semantic states (error, warning).

3. **Luminance-based elevation, not shadows.** On dark backgrounds, depth is created by stepping surface brightness: `#000000` (ground) to `#141414` (elevated) to `#1a1a1a` (raised). Combine with `rgba(255,255,255,0.08)` luminance borders. Traditional drop shadows are invisible on black and look wrong on dark gray. Only use box-shadow on light surface variants.

4. **Bold, direct typography at display sizes.** Uber Move at 52px/700 weight is the hero statement. At heading/title sizes, weight 500 provides authority without shouting. Body text at 400 weight creates clear hierarchy. The tight letter-spacing (-0.02em) at display sizes gives density and confidence. Never use weight 300/light -- Uber is medium-to-bold.

5. **Photography integration, not illustration.** Uber's visual language is photographic -- high-contrast cityscapes, vehicle interiors, people in motion. Dark photography on the black canvas creates seamless integration. Avoid illustrated/cartoon graphics, geometric patterns, or gradient backgrounds. When using photography, no overlays or filters -- let the image breathe.

6. **Monochromatic restraint is the identity.** The palette is black, white, and gray. Period. A well-designed Uber page should look striking even in grayscale. If removing all color from your component changes its character, you have too much color. The `#06c167` green and `#276ef1` blue are strictly sub-brand and semantic -- never decorative.

7. **Generous spacing on the dark canvas.** Section padding of 80-96px vertical gives each section room to breathe. The black canvas amplifies whitespace -- content islands floating in darkness. Do not crowd elements. Card padding minimum 32px. Component gaps minimum 16px.

8. **8px and 4px grid, no exceptions.** Every dimension -- padding, margin, gap, height -- must be a multiple of 4px. Most values land on 8px multiples (8, 16, 24, 32, 48, 64, 80, 96). The 4px sub-grid handles fine adjustments (4, 12, 20, 28). Arbitrary values like 15px, 22px, or 37px break the system.
