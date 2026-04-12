# Vercel -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Vercel-branded components.
Aesthetic: shadow-as-border philosophy -- compression as identity, gallery-like minimalism.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   Pure White -- gallery-like emptiness
Surface subtle:       #fafafa   Gray 50 -- inner shadow highlight, subtle tint
Text primary:         #171717   Vercel Black -- never pure #000000 for body text
Text secondary:       #4d4d4d   Gray 600 -- descriptions, secondary copy
Text tertiary:        #666666   Gray 500 -- muted links, tertiary text
Text placeholder:     #808080   Gray 400 -- disabled states
Border (shadow):      rgba(0,0,0,0.08)   Shadow-as-border -- replaces CSS borders
Border light:         #ebebeb   Gray 100 -- image outlines, dividers
Link:                 #0072f5   Link Blue -- primary link color
Focus ring:           hsla(212, 100%, 48%, 1)   Focus Blue -- accessibility ring
Badge bg:             #ebf5ff   Tinted Blue -- pill badge background
Badge text:           #0068d6   Dark Blue -- pill badge text
Workflow Ship:        #ff5b4f   Ship Red -- production workflow only
Workflow Preview:     #de1d8d   Preview Pink -- preview workflow only
Workflow Develop:     #0a72ef   Develop Blue -- development workflow only
```

---

## 2. Quick Typography Reference

```
Display:      Geist, Arial           | 48px | weight 600 | line-height 1.00-1.17 | letter-spacing -2.4px to -2.88px | font-feature-settings: "liga"
Section:      Geist, Arial           | 40px | weight 600 | line-height 1.20      | letter-spacing -2.4px             | font-feature-settings: "liga"
Subheading:   Geist, Arial           | 32px | weight 600 | line-height 1.25      | letter-spacing -1.28px            | font-feature-settings: "liga"
Card Title:   Geist, Arial           | 24px | weight 600 | line-height 1.33      | letter-spacing -0.96px            | font-feature-settings: "liga"
Body Large:   Geist, Arial           | 20px | weight 400 | line-height 1.80      | letter-spacing normal              | font-feature-settings: "liga"
Body:         Geist, Arial           | 16px | weight 400 | line-height 1.50      | letter-spacing normal              | font-feature-settings: "liga"
Button/Link:  Geist, Arial           | 14px | weight 500 | line-height 1.43      | letter-spacing normal              | font-feature-settings: "liga"
Caption:      Geist, Arial           | 12px | weight 500 | line-height 1.33      | letter-spacing normal              | font-feature-settings: "liga"
Mono Body:    Geist Mono, ui-monospace | 16px | weight 400 | line-height 1.50    | letter-spacing normal              | font-feature-settings: "liga"
Mono Label:   Geist Mono, ui-monospace | 12px | weight 500 | line-height 1.00    | letter-spacing normal, uppercase   | font-feature-settings: "liga"
```

Key rules:
- `font-feature-settings: "liga"` on ALL Geist text -- ligatures are structural
- Three weights: 400 (body), 500 (UI/interactive), 600 (headings)
- Most aggressive negative tracking of any major design system (-2.4px to -2.88px at display)
- Geist Mono uppercase for technical labels

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Vercel visual identity:
- Background: `#ffffff`
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Develop. Preview. Ship." at 48px Geist, weight 600, line-height 1.00, letter-spacing -2.4px, color `#171717`, font-feature-settings: "liga"
- Subtitle: 20px Geist, weight 400, line-height 1.80, color `#4d4d4d`, max-width 580px, margin-top 24px, font-feature-settings: "liga"
- CTA button (dark): background `#171717`, color `#ffffff`, 14px Geist weight 500, font-feature-settings: "liga", padding 8px 16px, border-radius 6px, border: none
- Ghost button (white): background `#ffffff`, color `#171717`, 14px Geist weight 500, font-feature-settings: "liga", padding 8px 16px, border-radius 6px, border: none, box-shadow: `rgb(235,235,235) 0px 0px 0px 1px`
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<600px): headline 32px, letter-spacing -1.28px, subtitle 16px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Vercel visual identity:
- Background: `#ffffff`
- Border: NONE (use shadow-as-border instead)
- Border-radius: 8px
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.08) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 2px, rgba(0,0,0,0.04) 0px 8px 8px -8px, #fafafa 0px 0px 0px 1px`
- Title: 24px Geist, weight 600, line-height 1.33, letter-spacing -0.96px, color `#171717`, font-feature-settings: "liga"
- Description: 16px Geist, weight 400, line-height 1.50, color `#4d4d4d`, font-feature-settings: "liga", margin-top 12px
- Hover: shadow intensifies subtly, transition 200ms ease
- On mobile (<600px): padding 24px, title 20px letter-spacing -0.4px

### CTA Button Row

Create a CTA button row with Vercel visual identity:
- Layout: flex, gap 12px, align-items center
- Dark button (primary): background `#171717`, color `#ffffff`, font 14px Geist weight 500, font-feature-settings: "liga", padding 8px 16px, border-radius 6px, border: none, transition: opacity 200ms ease
- Dark button hover: opacity 0.9
- White button (secondary): background `#ffffff`, color `#171717`, font 14px Geist weight 500, font-feature-settings: "liga", padding 0px 6px, border-radius 6px, border: none, box-shadow: `rgb(235,235,235) 0px 0px 0px 1px`
- White button hover: background `#fafafa`
- Pill badge: background `#ebf5ff`, color `#0068d6`, font 12px Geist weight 500, font-feature-settings: "liga", padding 0px 10px, border-radius 9999px, border: none
- On mobile (<600px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Vercel visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom (via shadow): box-shadow `rgba(0,0,0,0.08) 0px 0px 0px 1px` on the bottom edge, or `0px 1px 0px 0px rgba(0,0,0,0.08)`
- Container: max-width 1200px, centered, padding 0 64px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Vercel triangle logomark + wordmark, left-aligned, color `#171717`
- Nav links: 14px Geist, weight 500, color `#171717`, line-height 1.43, font-feature-settings: "liga", gap 24px, text-decoration none
- Nav link hover: color `#666666`, transition 150ms
- CTA button (right): background `#171717`, color `#ffffff`, 14px weight 500, font-feature-settings: "liga", padding 8px 16px, border-radius 6px
- On mobile (<768px): nav links collapse to hamburger (50% radius circular toggle)

### Data Card / Metric Display

Create a metric display card with Vercel visual identity:
- Background: `#ffffff`
- Border: NONE
- Border-radius: 12px
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.08) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 2px, rgba(0,0,0,0.04) 0px 8px 8px -8px, #fafafa 0px 0px 0px 1px`
- Label: 12px Geist Mono, weight 500, line-height 1.00, color `#666666`, font-feature-settings: "liga", text-transform uppercase, margin-bottom 12px
- Metric value: 48px Geist, weight 600, line-height 1.00, letter-spacing -2.4px, color `#171717`, font-feature-settings: "liga"
- Metric description: 16px Geist, weight 400, line-height 1.50, color `#4d4d4d`, font-feature-settings: "liga", margin-top 12px
- Badge (inline): background `#ebf5ff`, color `#0068d6`, 12px Geist weight 500, padding 0px 10px, border-radius 9999px
- On mobile (<600px): metric value 32px, letter-spacing -1.28px, padding 24px

### Workflow Pipeline Section

Create a workflow pipeline section with Vercel visual identity:
- Background: `#ffffff`
- Section padding: 80px 64px
- Container: max-width 1200px, centered
- Three columns, gap 32px, display grid, grid-template-columns repeat(3, 1fr)
- Step 1 -- Develop: accent color `#0a72ef`, step label 12px Geist Mono weight 500 uppercase color `#0a72ef`, font-feature-settings: "liga"
- Step 2 -- Preview: accent color `#de1d8d`, step label same format color `#de1d8d`
- Step 3 -- Ship: accent color `#ff5b4f`, step label same format color `#ff5b4f`
- Each step title: 24px Geist, weight 600, line-height 1.33, letter-spacing -0.96px, color `#171717`, font-feature-settings: "liga", margin-top 12px
- Each step description: 16px Geist, weight 400, line-height 1.50, color `#4d4d4d`, font-feature-settings: "liga", margin-top 8px
- Connecting line: 1px solid `#ebebeb` between steps
- On mobile (<768px): single column, steps stack vertically

---

## 4. Iteration Guide

1. **Use shadow-as-border, never CSS border.** The foundation of Vercel's depth system is `box-shadow: 0px 0px 0px 1px rgba(0,0,0,0.08)` replacing traditional `border: 1px solid`. This keeps borders in the shadow layer for smoother transitions and avoids box model side effects. The only exception is image outlines, which use `1px solid #ebebeb`.

2. **Letter-spacing scales aggressively with font size.** Follow this exact scale: -2.88px at 48px (maximum compression), -2.4px at 40-48px, -1.28px at 32px, -0.96px at 24px, -0.32px at 16px semibold, normal at 14px and below. Vercel has the most aggressive negative tracking of any major design system.

3. **Three weights only: 400, 500, 600.** 400 for body/reading, 500 for UI/interactive (buttons, links, captions), 600 for headings/emphasis. Never use 700 on body text -- only micro badges use it. If bold text appears in a component, change it to 600.

4. **Card shadows need all four layers.** The full Vercel card shadow is: `rgba(0,0,0,0.08) 0px 0px 0px 1px` (border ring) + `rgba(0,0,0,0.04) 0px 2px 2px` (subtle lift) + `rgba(0,0,0,0.04) 0px 8px 8px -8px` (ambient depth) + `#fafafa 0px 0px 0px 1px` (inner glow). The inner `#fafafa` ring is what gives Vercel cards their characteristic subtle glow.

5. **Color is functional, never decorative.** The palette is achromatic: `#171717` to `#ffffff` gray scale. The workflow colors (Ship Red `#ff5b4f`, Preview Pink `#de1d8d`, Develop Blue `#0a72ef`) are used ONLY in their specific pipeline context. Do not use them as accent colors for buttons, links, or decorative elements.

6. **Geist Mono uppercase for technical identity.** Whenever a label needs to feel "developer console" -- step labels, metadata tags, code annotations -- use Geist Mono at 12px weight 500, text-transform uppercase. This creates the connection between Vercel's marketing site and its product.
