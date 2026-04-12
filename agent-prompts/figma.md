# Figma -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Figma-branded components.
Aesthetic: monochrome gallery with variable-weight precision -- black-and-white interface chrome with vibrant product content.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   Pure White -- gallery wall for product content
Interactive surface:  rgba(0,0,0,0.08)  Glass Dark -- subtle overlay for secondary buttons
Glass Light:          rgba(255,255,255,0.16)  Frosted glass for buttons on dark/colored surfaces
Text primary:        #000000   Pure Black -- the sole interface color
Text secondary:      #666666   Mid Gray -- descriptions and metadata
Text on dark:        #ffffff   White -- on gradient and dark surfaces
Error:               #f24822   Figma Red -- from the editor palette
Success:             #14ae5c   Figma Green -- from the editor palette
Border:              #e6e6e6   Light Gray -- minimal containment
```

---

## 2. Quick Typography Reference

```
Display:     figmaSans, system-ui, sans-serif   | 86px | weight 400 | line-height 1.00 | letter-spacing -1.72px | kern
Section:     figmaSans, system-ui, sans-serif   | 64px | weight 400 | line-height 1.10 | letter-spacing -0.96px | kern
Sub-heavy:   figmaSans, system-ui, sans-serif   | 26px | weight 540 | line-height 1.35 | letter-spacing -0.26px | kern
Sub-light:   figmaSans, system-ui, sans-serif   | 26px | weight 340 | line-height 1.35 | letter-spacing -0.26px | kern
Feature:     figmaSans, system-ui, sans-serif   | 24px | weight 700 | line-height 1.45 | letter-spacing normal  | kern
Body Large:  figmaSans, system-ui, sans-serif   | 20px | weight 330 | line-height 1.40 | letter-spacing -0.14px | kern
Body:        figmaSans, system-ui, sans-serif   | 16px | weight 400 | line-height 1.45 | letter-spacing -0.14px | kern
Body Light:  figmaSans, system-ui, sans-serif   | 18px | weight 320 | line-height 1.45 | letter-spacing -0.26px | kern
Mono Label:  figmaMono, SF Mono, monospace      | 18px | weight 400 | line-height 1.30 | letter-spacing  0.54px | uppercase
Mono Small:  figmaMono, SF Mono, monospace      | 12px | weight 400 | line-height 1.00 | letter-spacing  0.60px | uppercase
```

Key rules:
- Variable font precision: weight stops at 320, 330, 340, 450, 480, 540, 700
- Light base: most body text uses 320-340, creating an airy reading experience
- OpenType `font-feature-settings: "kern"` on ALL text
- Negative letter-spacing throughout, even body text (-0.14px)
- Mono for structure: figmaMono in uppercase with positive letter-spacing

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Figma visual identity:
- Background: vibrant multi-color gradient (electric green, bright yellow, deep purple, hot pink)
- Container: full-width, centered content, padding 120px 64px
- Headline: "Design together" at 86px figmaSans, weight 400, line-height 1.0, letter-spacing -1.72px, color `#ffffff`, font-feature-settings: "kern"
- Subtitle: 20px figmaSans, weight 330, line-height 1.40, letter-spacing -0.14px, color `#ffffff`, max-width 640px, margin-top 24px
- CTA button: background `#ffffff`, color `#000000`, 16px figmaSans weight 400, padding 8px 18px 10px, border-radius 50px (pill), border: none
- Secondary button: background `rgba(255,255,255,0.16)`, color `#ffffff`, padding 8px 18px 10px, border-radius 50px (pill)
- Focus state: dashed 2px outline (echoes Figma editor selection handles)
- Button row gap: 16px, margin-top 32px
- On mobile (<559px): headline drops to 48px, subtitle 16px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Figma visual identity:
- Background: `#ffffff`
- Border: none (clean gallery-wall feel)
- Border-radius: 8px
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.08) 0px 2px 8px`
- Section label: 18px figmaMono, weight 400, line-height 1.30, letter-spacing 0.54px, text-transform uppercase, color `#000000`, margin-bottom 16px
- Title: 24px figmaSans, weight 700, line-height 1.45, color `#000000`, margin-bottom 12px
- Description: 20px figmaSans, weight 330, line-height 1.40, letter-spacing -0.14px, color `#666666`
- On mobile (<559px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Figma visual identity:
- Layout: flex, gap 16px, align-items center
- Primary button (Black Pill): background `#000000`, color `#ffffff`, font 16px figmaSans weight 400, padding 8px 18px 10px, border-radius 50px, border: none, cursor pointer, transition: all 200ms ease
- Primary hover: background `#333333`
- Secondary button (Glass Dark): background `rgba(0,0,0,0.08)`, color `#000000`, font 16px weight 400, padding 8px 18px 10px, border-radius 50% (circle for icon buttons)
- Focus state: outline dashed 2px `#000000`, outline-offset 2px
- All text: font-feature-settings: "kern"
- On mobile (<559px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Figma visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#e6e6e6`
- Container: max-width 1440px, centered, padding 0 32px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Figma wordmark in `#000000`, left-aligned
- Product tabs: pill-shaped navigation (50px radius), figmaSans 16px weight 480, active tab: `#000000` bg + white text, inactive: transparent + `#000000` text
- CTA button (right): background `#000000`, color `#ffffff`, 16px figmaSans weight 400, padding 8px 18px 10px, border-radius 50px
- On mobile (<768px): product tabs become horizontal scroll, CTA remains visible

### Data Card / Metric Display

Create a metric display card with Figma visual identity:
- Background: `#ffffff`
- Border: none
- Border-radius: 8px
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.08) 0px 2px 8px`
- Section label: 12px figmaMono, weight 400, line-height 1.0, letter-spacing 0.6px, text-transform uppercase, color `#666666`, margin-bottom 12px
- Metric value: 64px figmaSans, weight 400, line-height 1.10, letter-spacing -0.96px, color `#000000`
- Description: 16px figmaSans, weight 330, line-height 1.45, letter-spacing -0.14px, color `#666666`, margin-top 12px
- On mobile (<559px): metric value 48px, padding 24px

### Product Tab Bar (Brand-Specific)

Create a product tab bar with Figma visual identity:
- Layout: flex, gap 8px, overflow-x auto, padding 8px
- Tab item: figmaSans 20px weight 480, line-height 1.40, letter-spacing -0.14px, padding 10px 20px, border-radius 50px (pill), cursor pointer, transition: all 150ms ease
- Active tab: background `#000000`, color `#ffffff`
- Inactive tab: background transparent, color `#000000`
- Hover on inactive: background `rgba(0,0,0,0.05)`
- Focus: outline dashed 2px `#000000`, outline-offset 2px
- Each tab represents a Figma product: Design, Dev Mode, Prototyping, Slides, etc.
- font-feature-settings: "kern" on all tab text
- On mobile (<559px): horizontal scroll with scroll-snap

---

## 4. Iteration Guide

1. **Interface is strictly black-and-white.** No colors in the interface chrome. Color exists only in product content, hero gradients, and embedded screenshots. If a component introduces a new hue, remove it.

2. **Use variable font weight stops precisely.** figmaSans uses 320, 330, 340, 450, 480, 540, 700 -- not the standard 400/500/600/700. The micro-differences between 330 and 340 are structurally significant. If you see `font-weight: 500` or `font-weight: 600`, replace with the nearest Figma stop.

3. **Pill and circular geometry everywhere.** Buttons use 50px radius (pill) or 50% (circle for icon buttons). Cards use 8px. Never use sharp corners on interactive elements.

4. **Dashed focus outlines, not solid.** All interactive elements use `outline: dashed 2px #000000` on focus. This echoes the selection handles in the Figma editor -- a meta-design choice connecting website and product.

5. **Negative letter-spacing by default.** Even body text runs at -0.14px. Display compresses to -1.72px. Only monospace labels use positive tracking (0.54px+). If body text looks loose, check the letter-spacing.

6. **Enable `font-feature-settings: "kern"` on all text.** Kerning is structural, not optional. Every text element must include this declaration.
