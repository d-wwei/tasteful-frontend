# Framer -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Framer-branded components.
Aesthetic: motion-native creative tool -- electric blue energy on an infinite dark canvas, spring-physics animation DNA, glassmorphic interface panels.

---

## 1. Quick Color Reference

```
Canvas background:    #0a0a0a   Canvas Black -- the infinite dark canvas behind everything
Panel background:     #141414   Panel Dark -- sidebar, inspector, toolbar one step above canvas
Elevated surface:     #1c1c1c   Elevated -- cards, dropdowns, floating panels
Subtle surface:       #1a1a1a   Subtle -- card fills, section backgrounds
Hover surface:        #252525   Hover -- interactive element hover state
Translucent surface:  rgba(255,255,255,0.04)   Glassmorphic -- semi-transparent panels
Translucent hover:    rgba(255,255,255,0.08)   Glass hover -- translucent hover state
Framer Blue:          #0099ff   Brand Blue -- the only chromatic color, CTAs and high-signal moments
Blue hover:           #33adff   Lighter blue for hover states on accent elements
Deep Blue:            #0055ff   Secondary blue for gradients and emphasis
Blue glow:            rgba(0,153,255,0.15)   Ambient glow behind featured elements
Blue tint:            rgba(0,153,255,0.08)   Very faint accent fill for selected containers
Text primary:         #ffffff   Pure White -- headings and primary text
Text secondary:       #999999   Medium Gray -- body copy, descriptions
Text tertiary:        #666666   Muted Gray -- metadata, timestamps, placeholders
Text on accent:       #000000   Black -- text on Framer Blue buttons
Error:                #ff3b30   Red -- destructive actions
Success:              #30d158   Green -- publish success, positive status
Warning:              #ff9f0a   Amber -- caution states
Border standard:      rgba(255,255,255,0.08)   Semi-transparent white
Border subtle:        rgba(255,255,255,0.05)   Whisper-thin containment
Border prominent:     rgba(255,255,255,0.12)   Emphasized interactive borders
Focus ring:           rgba(0,153,255,0.5)   Blue focus indicator
Overlay:              rgba(0,0,0,0.75)   Modal backdrop
```

---

## 2. Quick Typography Reference

```
Display XL:  Inter, -apple-system, sans-serif  | 64px | weight 700 | line-height 1.10 | letter-spacing -0.96px
Display:     Inter, -apple-system, sans-serif  | 48px | weight 700 | line-height 1.10 | letter-spacing -0.96px
Section:     Inter, -apple-system, sans-serif  | 36px | weight 600 | line-height 1.20 | letter-spacing -0.48px
Heading:     Inter, -apple-system, sans-serif  | 24px | weight 600 | line-height 1.20 | letter-spacing -0.48px
Subheading:  Inter, -apple-system, sans-serif  | 20px | weight 600 | line-height 1.25 | letter-spacing normal
Body Large:  Inter, -apple-system, sans-serif  | 18px | weight 400 | line-height 1.60 | letter-spacing normal
Body:        Inter, -apple-system, sans-serif  | 16px | weight 400 | line-height 1.50 | letter-spacing normal
Small:       Inter, -apple-system, sans-serif  | 14px | weight 500 | line-height 1.43 | letter-spacing normal
Caption:     Inter, -apple-system, sans-serif  | 13px | weight 400 | line-height 1.40 | letter-spacing normal
Label:       Inter, -apple-system, sans-serif  | 12px | weight 500 | line-height 1.33 | letter-spacing normal
Micro:       Inter, -apple-system, sans-serif  | 11px | weight 500 | line-height 1.27 | letter-spacing 0.2px
Code:        SF Mono, Fira Code, monospace     | 14px | weight 400 | line-height 1.50 | letter-spacing normal
```

Key rules:
- Inter is the only font family. No serif, no decorative fonts.
- Four weights: 400 (reading), 500 (UI/labels), 600 (headings), 700 (display only)
- Negative letter-spacing at display sizes (-0.96px at 48px+, -0.48px at 24-36px), normal below
- Headlines are bold and punchy -- this is a creative tool, not a document editor

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Framer visual identity:
- Background: `#0a0a0a` (Canvas Black)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Design and ship sites" at 64px Inter, weight 700, line-height 1.10, letter-spacing -0.96px, color `#ffffff`
- Subtitle: 18px Inter, weight 400, line-height 1.60, color `#999999`, max-width 560px, margin-top 20px
- CTA button: background `#0099ff`, color `#000000`, 14px Inter weight 600, padding 10px 24px, border-radius 8px, border: none, transition: all 250ms cubic-bezier(0.2, 0.9, 0.3, 1.0)
- CTA hover: background `#33adff`, transform scale(1.02), box-shadow `0 0 20px rgba(0,153,255,0.15)`
- Ghost button: background transparent, color `#ffffff`, 14px weight 500, padding 10px 24px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.12)`
- Ghost hover: background `rgba(255,255,255,0.04)`, border-color `rgba(255,255,255,0.2)`
- Button row: flex, gap 12px, margin-top 32px
- Optional hero gradient: subtle radial gradient behind headline: `radial-gradient(ellipse at 50% 40%, rgba(0,153,255,0.06) 0%, transparent 70%)`
- On mobile (<640px): headline 36px, letter-spacing -0.48px, subtitle 16px, section padding 64px 20px, buttons stack full-width

### Feature Card

Create a feature card with Framer visual identity:
- Background: `#1a1a1a` (Subtle Surface)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 32px
- Title: 20px Inter, weight 600, line-height 1.25, color `#ffffff`, margin-bottom 12px
- Description: 16px Inter, weight 400, line-height 1.50, color `#999999`
- Icon area: 40px square, `#0099ff` accent, margin-bottom 16px
- Hover: background shifts to `#1c1c1c`, border-color `rgba(255,255,255,0.12)`, transition 250ms cubic-bezier(0.2, 0.9, 0.3, 1.0)
- Optional hover glow: box-shadow `0 0 20px rgba(0,153,255,0.06)`
- On mobile (<640px): padding 24px, title 18px

### CTA Button Row

Create a CTA button row with Framer visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Framer Blue): background `#0099ff`, color `#000000`, font 14px Inter weight 600, padding 10px 24px, border-radius 8px, border: none, cursor pointer, transition: all 250ms cubic-bezier(0.2, 0.9, 0.3, 1.0)
- Primary hover: background `#33adff`, transform scale(1.02), box-shadow `0 0 20px rgba(0,153,255,0.15)`
- Ghost button: background transparent, color `#ffffff`, font 14px Inter weight 500, padding 10px 24px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.12)`
- Ghost hover: background `rgba(255,255,255,0.04)`, border-color `rgba(255,255,255,0.2)`
- Subtle button: background `rgba(255,255,255,0.04)`, color `#999999`, font 13px Inter weight 500, padding 8px 16px, border-radius 6px, border: none
- Subtle hover: background `rgba(255,255,255,0.08)`, color `#ffffff`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Framer visual identity:
- Background: `rgba(10,10,10,0.85)` with `backdrop-filter: blur(12px)` (glassmorphic)
- Position: sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.05)`
- Container: max-width 1200px, centered, padding 0 24px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Framer motion mark, color `#ffffff`, left-aligned
- Nav links: 14px Inter, weight 500, color `#999999`, gap 32px, text-decoration none, transition color 150ms
- Nav link hover: color `#ffffff`
- CTA button (right): background `#0099ff`, color `#000000`, 13px Inter weight 600, padding 7px 16px, border-radius 6px
- On mobile (<768px): nav links collapse to hamburger icon, CTA remains visible

### Data Card / Metric Display

Create a metric display card with Framer visual identity:
- Background: `#1a1a1a`
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 12px
- Padding: 32px
- Overline label: 12px Inter, weight 500, line-height 1.33, letter-spacing 0.5px, text-transform uppercase, color `#666666`, margin-bottom 8px
- Metric value: 48px Inter, weight 700, line-height 1.10, letter-spacing -0.96px, color `#ffffff`
- Metric description: 16px Inter, weight 400, line-height 1.50, color `#999999`, margin-top 12px
- Status indicator: 8px circle, background `#30d158`, border-radius 50%
- Hover: subtle blue glow: box-shadow `0 0 20px rgba(0,153,255,0.06)`, transition 250ms
- On mobile (<640px): metric value 36px, letter-spacing -0.48px, padding 24px

### Canvas Toolbar / Component Inspector Panel

Create a canvas toolbar and component inspector panel with Framer visual identity:
- Toolbar container: background `#141414` (Panel Dark), border-radius 12px, border: 1px solid `rgba(255,255,255,0.08)`, padding 6px, display flex, gap 2px, box-shadow `0 4px 12px rgba(0,0,0,0.4)`
- Tool button (inactive): background transparent, color `#666666`, 24px icon size, padding 8px, border-radius 6px, transition all 150ms
- Tool button (hover): background `rgba(255,255,255,0.04)`, color `#999999`
- Tool button (active): background `rgba(0,153,255,0.08)`, color `#0099ff`
- Separator: 1px solid `rgba(255,255,255,0.05)`, height 24px, margin 0 4px
- Inspector panel: background `#141414`, width 260px, border-left 1px solid `rgba(255,255,255,0.05)`, padding 16px
- Inspector section title: 11px Inter, weight 500, letter-spacing 0.2px, text-transform uppercase, color `#666666`, margin-bottom 8px
- Inspector field label: 12px Inter, weight 500, color `#999999`, margin-bottom 4px
- Inspector input: background `#1c1c1c`, color `#ffffff`, 13px Inter weight 400, padding 6px 8px, border-radius 4px, border: 1px solid `rgba(255,255,255,0.08)`, width 100%
- Inspector input focus: border-color `rgba(0,153,255,0.5)`, box-shadow `0 0 0 2px rgba(0,153,255,0.15)`
- Inspector value scrubber: cursor ew-resize on numeric fields, blue highlight on drag
- Property group: margin-bottom 16px, padding-bottom 16px, border-bottom 1px solid `rgba(255,255,255,0.05)`
- Layer item: padding 6px 12px, border-radius 4px, 13px Inter weight 400, color `#999999`, transition background 100ms
- Layer item hover: background `rgba(255,255,255,0.04)`
- Layer item selected: background `rgba(0,153,255,0.08)`, color `#0099ff`

---

## 4. Iteration Guide

1. **The dark canvas is the infinite workspace.** Every Framer interface begins with `#0a0a0a` -- the near-black canvas that recedes to make content and design elements the focal point. Never use light backgrounds for primary surfaces. The canvas IS the tool identity.

2. **Framer Blue (`#0099ff`) is the single chromatic signal.** It appears on primary CTAs, active toolbar states, selection highlights, and keyboard focus rings. Never use it as decorative fill, background color, or section accent. Its power comes from extreme restraint -- when blue appears, it means "this is interactive."

3. **Motion is not decoration -- it is the product identity.** Framer is a motion design tool. Every transition should use spring-physics easing: `cubic-bezier(0.2, 0.9, 0.3, 1.0)` for the signature slight overshoot. Hover states should include subtle scale transforms (1.02x on buttons). Avoid linear or generic ease transitions.

4. **Use glassmorphic surfaces for navigation and toolbars.** The navigation bar uses `backdrop-filter: blur(12px)` over a semi-transparent dark background. This creates the creative-tool studio feel where tools float above the canvas. Solid opaque toolbars feel heavy and dated.

5. **Elevation uses shadow intensity, not luminance stacking alone.** Unlike some dark UIs that only step up background brightness, Framer uses real shadows on dark: `rgba(0,0,0,0.3)` to `rgba(0,0,0,0.5)` with visible blur. This gives floating panels physical presence on the canvas. Complement with blue glow (`rgba(0,153,255,0.15)`) for featured elements.

6. **Headlines are bold and punchy -- weight 700 at display sizes.** Framer markets itself as a creative power tool. Display headlines use Inter at weight 700 with aggressive negative tracking (-0.96px). This is deliberate: punchy, confident, not soft or literary. Body text drops to 400 for comfortable reading.

7. **Semi-transparent borders create structure without noise.** Use `rgba(255,255,255,0.08)` as standard, `rgba(255,255,255,0.05)` for subtle. Never use solid dark hex colors as borders on dark backgrounds -- they look heavy and opaque.

8. **The blue glow is Framer's energy signature.** Featured elements, active states, and hero backgrounds can use a faint `radial-gradient` or `box-shadow` in `rgba(0,153,255,0.06-0.15)`. This creates the "electric creative tool" atmosphere. Use sparingly -- one or two glow sources per viewport maximum.
