# Raycast -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Raycast-branded components.
Aesthetic: macOS-native dark launcher -- glass panels, vibrant red-orange-pink gradient accents, keyboard-first command palette.

---

## 1. Quick Color Reference

```
Launcher background:  #191A1F   Warm dark gray with slight blue -- macOS dark mode chrome
Raised panel:         #23252B   Sidebar, search area -- one step above launcher
Elevated surface:     #2C2E36   Hovered items, dropdowns, extension cards
Overlay surface:      #363840   Tooltips, context menus, action bar
Glass panel bg:       rgba(25, 26, 31, 0.72)  Frosted glass -- requires backdrop-filter: blur(40px)
Brand accent:         #FF6363   Raycast Red -- CTAs, loading bar, icon tint
Accent hover:         #FF7A7A   Lighter red for hover/focus feedback
Gradient start:       #FF6363   Red anchor of the signature gradient
Gradient end:         #E84393   Vibrant pink endpoint
Text primary:         #ECECEC   Near-white, warm -- never pure #ffffff
Text secondary:       rgba(255,255,255,0.55)  Descriptions, metadata
Text tertiary:        rgba(255,255,255,0.35)  Shortcut hints, placeholders
Border default:       rgba(255,255,255,0.10)  Card outlines, input fields
Border subtle:        rgba(255,255,255,0.06)  List separators inside glass
Selection:            rgba(255,99,99,0.16)    Active command item background
```

---

## 2. Quick Typography Reference

```
Display:    Inter, -apple-system, 'SF Pro Display', sans-serif  | 48px | weight 600 | line-height 1.15 | letter-spacing -0.025em
Section:    Inter, -apple-system, 'SF Pro Display', sans-serif  | 32px | weight 600 | line-height 1.20 | letter-spacing -0.025em
Title:      Inter, -apple-system, 'SF Pro Text', sans-serif     | 20px | weight 500 | line-height 1.30 | letter-spacing -0.01em
Base:       Inter, -apple-system, 'SF Pro Text', sans-serif     | 15px | weight 400 | line-height 1.45 | letter-spacing -0.01em
Small:      Inter, -apple-system, 'SF Pro Text', sans-serif     | 13px | weight 500 | line-height 1.45 | letter-spacing -0.01em
Caption:    Inter, -apple-system, 'SF Pro Text', sans-serif     | 11px | weight 500 | line-height 1.40 | letter-spacing 0.04em
Mono:       'SF Mono', 'JetBrains Mono', ui-monospace           | 12px | weight 400 | line-height 1.40 | letter-spacing normal
```

Key rules:
- Inter for marketing, SF Pro in native app. Both share geometric sans-serif DNA.
- Three weights: 400 (reading), 500 (UI emphasis, the default for labels and nav), 600 (headings only)
- macOS-native 15px base size, not the web-standard 16px. This matches system UI density.
- Negative letter-spacing at all sizes except caption and mono. Slightly tighter than default Inter.

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Raycast visual identity:
- Background: `#191A1F` (Launcher Background)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Your shortcut to everything" at 48px Inter, weight 600, line-height 1.15, letter-spacing -0.025em, color `#ECECEC`
- Subtitle: 18px Inter, weight 400, line-height 1.60, letter-spacing -0.01em, color `rgba(255,255,255,0.55)`, max-width 560px, margin-top 20px
- CTA button: background `linear-gradient(135deg, #FF6363, #E84393)`, color `#FFFFFF`, 15px Inter weight 500, padding 10px 20px, border-radius 8px, border: none, box-shadow: `0 0 12px rgba(255,99,99,0.20)`
- Ghost button: background `rgba(255,255,255,0.06)`, color `#ECECEC`, 15px weight 500, padding 10px 20px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.10)`, backdrop-filter: blur(8px)
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<640px): headline 32px, subtitle 15px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Raycast visual identity:
- Background: `rgba(255,255,255,0.03)` (translucent, never solid)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 32px
- Backdrop-filter: blur(20px) saturate(180%)
- Icon area: 40px square, 8px radius, background `rgba(255,99,99,0.10)`, icon tinted `#FF6363`, margin-bottom 20px
- Title: 20px Inter, weight 500, line-height 1.30, letter-spacing -0.01em, color `#ECECEC`
- Description: 15px Inter, weight 400, line-height 1.45, letter-spacing -0.01em, color `rgba(255,255,255,0.55)`, margin-top 8px
- Hover: background shifts to `rgba(255,255,255,0.05)`, border-color `rgba(255,255,255,0.12)`, transition 150ms ease
- On mobile (<640px): padding 24px, title 18px

### CTA Button Row

Create a CTA button row with Raycast visual identity:
- Layout: flex, gap 12px, align-items center
- Gradient button: background `linear-gradient(135deg, #FF6363 0%, #E84393 100%)`, color `#FFFFFF`, font 15px Inter weight 500, padding 10px 20px, border-radius 8px, border: none, box-shadow: `0 0 12px rgba(255,99,99,0.20)`, transition: all 200ms ease
- Gradient hover: box-shadow intensifies to `0 0 20px rgba(255,99,99,0.30)`, filter: brightness(1.05)
- Ghost button: background `rgba(255,255,255,0.04)`, color `#ECECEC`, font 15px weight 500, padding 10px 20px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.10)`, backdrop-filter: blur(8px)
- Ghost hover: background `rgba(255,255,255,0.08)`, border-color `rgba(255,255,255,0.16)`
- Pill badge: background `rgba(255,255,255,0.06)`, color `rgba(255,255,255,0.55)`, font 11px weight 500, letter-spacing 0.04em, padding 4px 10px, border-radius 9999px
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Raycast visual identity:
- Background: `rgba(25, 26, 31, 0.72)` (glass panel), backdrop-filter: blur(40px) saturate(180%), position sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.06)`
- Container: max-width 1200px, centered, padding 0 48px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Raycast wordmark, left-aligned, color `#ECECEC`
- Nav links: 13px Inter, weight 500, color `rgba(255,255,255,0.55)`, line-height 1.45, gap 28px, text-decoration none, letter-spacing -0.01em
- Nav link hover: color `#ECECEC`, transition 150ms ease
- CTA button (right): background `linear-gradient(135deg, #FF6363, #E84393)`, color `#FFFFFF`, 13px weight 500, padding 8px 16px, border-radius 8px
- On mobile (<768px): nav links collapse to hamburger, glass bg remains, CTA stays visible

### Data Card / Metric Display

Create a metric display card with Raycast visual identity:
- Background: `rgba(255,255,255,0.03)`
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 32px
- Backdrop-filter: blur(16px) saturate(180%)
- Overline: 11px Inter, weight 500, line-height 1.40, letter-spacing 0.04em, color `rgba(255,255,255,0.35)`, text-transform uppercase, margin-bottom 8px
- Metric value: 48px Inter, weight 600, line-height 1.15, letter-spacing -0.025em, color `#ECECEC`
- Metric description: 15px Inter, weight 400, line-height 1.45, letter-spacing -0.01em, color `rgba(255,255,255,0.55)`, margin-top 8px
- Status dot: 8px circle, background `#63BA89`, border-radius 50%
- Gradient accent bar: 3px height at top, background `linear-gradient(90deg, #FF6363, #E84393)`, border-radius 12px 12px 0 0
- On mobile (<640px): metric value 32px, padding 24px

### Command Palette / Extension Card

Create a command palette with Raycast visual identity:
- Overlay backdrop: `rgba(0,0,0,0.60)`, backdrop-filter: blur(4px)
- Palette container: width 750px, max-height 500px, background `#191A1F`, border: 1px solid `rgba(255,255,255,0.10)`, border-radius 12px, box-shadow: `0 16px 48px -8px rgba(0,0,0,0.50), 0 8px 16px -4px rgba(0,0,0,0.30)`, overflow hidden
- Search input area: height 52px, padding 0 16px, background `#23252B`, border-bottom: 1px solid `rgba(255,255,255,0.06)`, display flex, align-items center, gap 12px
- Search icon: 16px, color `rgba(255,255,255,0.35)`
- Search input: 15px Inter, weight 400, color `#ECECEC`, letter-spacing -0.01em, background transparent, border: none, flex 1, placeholder-color `rgba(255,255,255,0.35)`
- Results list: padding 8px, max-height 380px, overflow-y auto, scrollbar-width thin
- Result item: display flex, align-items center, gap 12px, padding 8px 12px, border-radius 6px, cursor pointer, transition: background 60ms ease
- Result item icon: 20px square, border-radius 4px, background `rgba(255,99,99,0.10)`, display flex, align-items center, justify-content center
- Result item label: 13px Inter, weight 500, color `#ECECEC`, letter-spacing -0.01em
- Result item description: 13px weight 400, color `rgba(255,255,255,0.35)`, margin-left auto
- Result item hover: background `rgba(255,99,99,0.16)` (selection highlight)
- Result item active: background `rgba(255,99,99,0.20)`
- Keyboard shortcut hint: font `'SF Mono', ui-monospace`, 11px weight 500, color `rgba(255,255,255,0.35)`, background `rgba(255,255,255,0.06)`, padding 2px 6px, border-radius 4px, border: 1px solid `rgba(255,255,255,0.08)`
- Action bar (bottom): height 40px, background `#23252B`, border-top: 1px solid `rgba(255,255,255,0.06)`, display flex, align-items center, padding 0 12px, gap 16px
- Action bar item: 11px Inter, weight 500, color `rgba(255,255,255,0.55)`, letter-spacing 0.04em, display flex, align-items center, gap 4px
- On mobile: full-width with 8px margin, border-radius 12px, max-height 70vh

---

## 4. Iteration Guide

1. **Glass morphism is the signature depth model.** Panels use `backdrop-filter: blur(40px) saturate(180%)` with `rgba()` backgrounds. The background must be translucent, not opaque. If a card or nav uses a solid hex background color, switch it to its rgba equivalent so desktop content bleeds through. This is what makes Raycast feel like a macOS-native overlay, not a web page.

2. **The gradient is the brand. Use it on highest-signal elements.** `linear-gradient(135deg, #FF6363, #E84393)` appears on primary CTAs, loading bars, and hero accents. It is never used as a surface fill or background wash. Solid `#FF6363` is for secondary accents (icon tints, selection). If a component has more than one gradient element visible simultaneously, one of them should be solid accent instead.

3. **Keyboard shortcut hints are a first-class UI element.** Display them using SF Mono at 11px with subtle bordered badges (`rgba(255,255,255,0.06)` bg, `rgba(255,255,255,0.08)` border, 4px radius). They appear in the action bar, beside list items, and in tooltips. A Raycast component without visible keyboard affordances is incomplete.

4. **Elevation via background opacity, not shadows.** On dark surfaces, depth is communicated by stepping up white opacity: `rgba(255,255,255,0.03)` for flat, `0.04` for subtle, `0.06` for elevated, `0.08` for hover. Shadows are reserved for the launcher window itself and modals. Do not add box-shadows to individual cards or list items.

5. **macOS-native 15px base text, not web-standard 16px.** The entire type scale is shifted down by 1px to match SF Pro Text rendering. Body is 15px, small is 13px, caption is 11px. If any text appears at 16px, 14px, or 12px, it is off-grid. The odd-number sizes match macOS system typography.

6. **Every surface border uses semi-transparent white.** Standard: `rgba(255,255,255,0.10)`. Subtle: `rgba(255,255,255,0.06)`. Strong: `rgba(255,255,255,0.16)`. Never use solid dark borders like `#333333` or `#444444` -- they look opaque and heavy against glass panels. The transparency lets the background influence the border tone.
