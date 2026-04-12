# Linear -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Linear-branded components.
Aesthetic: darkness as native medium -- precision engineering, luminance-stacking elevation.

---

## 1. Quick Color Reference

```
Page background:      #08090a   Marketing Black -- near-pure black canvas
Panel background:     #0f1011   Panel Dark -- sidebar/panel one step up
Elevated surface:     #191a1b   Level 3 Surface -- cards, dropdowns
Secondary surface:    #28282c   Hover states, lightest dark surface
Translucent card bg:  rgba(255,255,255,0.02)   Ghost-level surface
Translucent hover:    rgba(255,255,255,0.05)   Toolbar, badge surface
Brand CTA:            #5e6ad2   Brand Indigo -- the only chromatic color
Accent interactive:   #7170ff   Accent Violet -- links, active states
Accent hover:         #828fff   Light Violet -- hover on accent elements
Text primary:         #f7f8f8   Near-white -- never use pure #ffffff
Text secondary:       #d0d6e0   Silver Gray -- body copy, descriptions
Text tertiary:        #8a8f98   Muted Gray -- placeholders, metadata
Text quaternary:      #62666d   Subdued -- timestamps, disabled text
Border default:       rgba(255,255,255,0.08)   Semi-transparent white
Border subtle:        rgba(255,255,255,0.05)   Ultra-subtle containment
```

---

## 2. Quick Typography Reference

```
Display XL:  Inter Variable | 72px | weight 510 | line-height 1.00 | letter-spacing -1.584px | font-feature-settings: "cv01", "ss03"
Display:     Inter Variable | 48px | weight 510 | line-height 1.00 | letter-spacing -1.056px | font-feature-settings: "cv01", "ss03"
Heading 1:   Inter Variable | 32px | weight 400 | line-height 1.13 | letter-spacing -0.704px | font-feature-settings: "cv01", "ss03"
Heading 3:   Inter Variable | 20px | weight 590 | line-height 1.33 | letter-spacing -0.24px  | font-feature-settings: "cv01", "ss03"
Body Large:  Inter Variable | 18px | weight 400 | line-height 1.60 | letter-spacing -0.165px | font-feature-settings: "cv01", "ss03"
Body:        Inter Variable | 16px | weight 510 | line-height 1.50 | letter-spacing normal    | font-feature-settings: "cv01", "ss03"
Small:       Inter Variable | 15px | weight 400 | line-height 1.60 | letter-spacing -0.165px | font-feature-settings: "cv01", "ss03"
Caption:     Inter Variable | 13px | weight 510 | line-height 1.50 | letter-spacing -0.13px  | font-feature-settings: "cv01", "ss03"
Label:       Inter Variable | 12px | weight 510 | line-height 1.40 | letter-spacing normal    | font-feature-settings: "cv01", "ss03"
Code:        Berkeley Mono, ui-monospace, SF Mono | 14px | weight 400 | line-height 1.50 | letter-spacing normal
```

Key rules:
- `font-feature-settings: "cv01", "ss03"` on ALL Inter text -- non-negotiable for Linear identity
- Three weights: 400 (reading), 510 (emphasis/UI -- the signature weight), 590 (strong emphasis)
- Never use weight 700. Maximum is 590.
- Aggressive negative letter-spacing at display sizes, relaxing toward normal below 16px

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Linear visual identity:
- Background: `#08090a` (Marketing Black)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Build better products" at 48px Inter Variable, weight 510, line-height 1.00, letter-spacing -1.056px, color `#f7f8f8`, font-feature-settings: "cv01", "ss03"
- Subtitle: 18px Inter Variable, weight 400, line-height 1.60, letter-spacing -0.165px, color `#8a8f98`, max-width 560px, margin-top 24px, font-feature-settings: "cv01", "ss03"
- CTA button: background `#5e6ad2`, color `#ffffff`, 14px Inter Variable weight 510, font-feature-settings: "cv01", "ss03", padding 8px 16px, border-radius 6px, border: none
- CTA hover: background `#828fff`
- Ghost button: background `rgba(255,255,255,0.02)`, color `#e2e4e7`, 14px weight 510, font-feature-settings: "cv01", "ss03", padding 8px 16px, border-radius 6px, border: 1px solid `rgb(36,40,44)`
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<640px): headline 32px, letter-spacing -0.704px, subtitle 15px, section padding 48px 20px

### Feature Card

Create a feature card with Linear visual identity:
- Background: `rgba(255,255,255,0.02)` (translucent, never solid)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 8px
- Padding: 32px
- Title: 20px Inter Variable, weight 590, line-height 1.33, letter-spacing -0.24px, color `#f7f8f8`, font-feature-settings: "cv01", "ss03"
- Description: 15px Inter Variable, weight 400, line-height 1.60, letter-spacing -0.165px, color `#8a8f98`, font-feature-settings: "cv01", "ss03", margin-top 12px
- Hover: background shifts to `rgba(255,255,255,0.04)`, transition 200ms ease
- On mobile (<640px): padding 24px, title 18px

### CTA Button Row

Create a CTA button row with Linear visual identity:
- Layout: flex, gap 12px, align-items center
- Brand button: background `#5e6ad2`, color `#ffffff`, font 14px Inter Variable weight 510, font-feature-settings: "cv01", "ss03", padding 8px 16px, border-radius 6px, border: none, transition: background 200ms ease
- Brand hover: background `#828fff`
- Ghost button: background `rgba(255,255,255,0.02)`, color `#e2e4e7`, font 14px weight 510, font-feature-settings: "cv01", "ss03", padding 8px 16px, border-radius 6px, border: 1px solid `rgb(36,40,44)`, outline: none
- Ghost hover: background `rgba(255,255,255,0.05)`
- Pill button: background transparent, color `#d0d6e0`, font 12px weight 510, font-feature-settings: "cv01", "ss03", padding 0px 10px 0px 5px, border-radius 9999px, border: 1px solid `rgb(35,37,42)`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Linear visual identity:
- Background: `#0f1011` (Panel Dark), position sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.05)`
- Container: max-width 1200px, centered, padding 0 64px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Linear logomark SVG, left-aligned, color `#f7f8f8`
- Nav links: 13px Inter Variable, weight 510, color `#d0d6e0`, line-height 1.50, font-feature-settings: "cv01", "ss03", gap 24px, text-decoration none
- Nav link hover: color `#f7f8f8`, transition 150ms
- CTA button (right): background `#5e6ad2`, color `#ffffff`, 13px weight 510, font-feature-settings: "cv01", "ss03", padding 6px 12px, border-radius 6px
- On mobile (<768px): nav links collapse to hamburger menu

### Data Card / Metric Display

Create a metric display card with Linear visual identity:
- Background: `rgba(255,255,255,0.02)`
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px (featured)
- Padding: 32px
- Overline: 10px Inter Variable, weight 510, line-height 1.50, letter-spacing -0.15px, color `#62666d`, text-transform uppercase, font-feature-settings: "cv01", "ss03", margin-bottom 8px
- Metric value: 48px Inter Variable, weight 510, line-height 1.00, letter-spacing -1.056px, color `#f7f8f8`, font-feature-settings: "cv01", "ss03"
- Metric description: 15px Inter Variable, weight 400, line-height 1.60, letter-spacing -0.165px, color `#8a8f98`, font-feature-settings: "cv01", "ss03", margin-top 12px
- Status dot: 8px circle, background `#10b981`, border-radius 50%
- On mobile (<640px): metric value 32px, letter-spacing -0.704px, padding 24px

### Command Palette / Search Modal

Create a command palette with Linear visual identity:
- Background: `#191a1b` (Level 3 Surface)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Box-shadow: `rgba(0,0,0,0) 0px 8px 2px, rgba(0,0,0,0.01) 0px 5px 2px, rgba(0,0,0,0.04) 0px 3px 2px, rgba(0,0,0,0.07) 0px 1px 1px, rgba(0,0,0,0.08) 0px 0px 1px`
- Overlay backdrop: `rgba(0,0,0,0.85)`
- Search input: 16px Inter Variable, weight 400, color `#f7f8f8`, font-feature-settings: "cv01", "ss03", background transparent, border: none, padding 12px 14px
- Results list: padding 8px
- Result item: 13px Inter Variable, weight 510, color `#d0d6e0`, font-feature-settings: "cv01", "ss03", padding 8px 12px, border-radius 6px
- Result metadata: 12px weight 400, color `#62666d`
- Result hover: background `rgba(255,255,255,0.05)`
- On mobile: full-width, border-radius 0

---

## 4. Iteration Guide

1. **Always set `font-feature-settings: "cv01", "ss03"` on all Inter Variable text.** These OpenType features transform generic Inter into Linear's distinctive geometric typeface. Without them, the design looks like any Inter-based site. This applies to every text element, no exceptions.

2. **Letter-spacing scales with font size.** Follow this exact scale: -1.584px at 72px, -1.408px at 64px, -1.056px at 48px, -0.704px at 32px, -0.288px at 24px, -0.24px at 20px, -0.165px at 15-18px, normal at 16px body and below. If a heading has wrong tracking, fix it immediately.

3. **Surface elevation uses background opacity, not shadows.** On dark surfaces, depth is communicated by stepping up white opacity: `rgba(255,255,255, 0.02)` for flat, `0.04` for subtle, `0.05` for elevated. Never use solid colored backgrounds for cards or buttons on the dark canvas.

4. **Borders are always semi-transparent white.** Use `rgba(255,255,255,0.08)` as the standard border and `rgba(255,255,255,0.05)` for subtle. Never use solid dark colors like `#333333` as borders on dark backgrounds -- they look opaque and heavy.

5. **Brand indigo (`#5e6ad2` / `#7170ff`) is the only chromatic color.** Everything else is grayscale. If a generated component introduces warm colors, saturated blues, or any hue other than the brand violet, remove it. The achromatic palette is fundamental.

6. **Three weights, strict roles: 400, 510, 590.** 400 for reading body text, 510 for emphasis and UI (buttons, labels, nav -- this is the signature weight), 590 for strong announcements. Never use 700. If bold appears anywhere, replace it with 590.
