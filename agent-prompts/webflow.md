# Webflow -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Webflow-branded components.
Aesthetic: visual-builder precision -- dark canvas, electric blue accents, geometric type, monochromatic discipline.

---

## 1. Quick Color Reference

```
Surface (light bg):        #ffffff     White -- marketing pages, light sections
Surface subtle:            #f0f0f0     Gray 100 -- secondary light surface, card bg
Surface dark:              #080808     Near-black -- editor canvas, dark hero sections
Surface dark elevated:     #171717     Gray 900 -- panels on dark canvas
Surface dark card:         #222222     Gray 800 -- cards on dark backgrounds
Accent:                    #146ef5     Webflow Blue -- CTAs, links, interactive
Accent hover:              #1060d4     Webflow Blue darkened
Accent light:              rgba(20,110,245,0.12)  Blue tint for focus/selection
Text primary (light):      #080808     Primary text on white
Text secondary:            #5a5a5a     Gray 600 -- descriptions
Text tertiary:             #757575     Gray 500 -- metadata, placeholders
Text on dark:              #ffffff     Primary text on dark
Text on dark secondary:    #ababab     Gray 300 -- secondary on dark
Border light:              #e5e5e5     Borders on light surfaces
Border dark:               #363636     Gray 700 -- borders on dark surfaces
Error:                     #ee1d36     Webflow Red
Success:                   #00d722     Webflow Green
Warning:                   #ffae13     Webflow Yellow
Selection:                 rgba(20,110,245,0.95)  Text selection bg
```

Key color rule: **Each asset = black + white + one color.** Webflow's brand enforces monochromatic discipline. The only chromatic accent in any given composition is Webflow Blue `#146ef5`. Secondary brand colors (Purple `#7A3DFF`, Pink `#ED52CB`, Orange `#FF6B00`) exist but are reserved for illustrations and marketing campaigns -- never for UI chrome.

---

## 2. Quick Typography Reference

```
H0 (Hero):    Poppins, sans-serif        | 128px | weight 600 | line-height 1.04 | letter-spacing 0.01em
H1:           Poppins, sans-serif        | 85px  | weight 600 | line-height 1.04 | letter-spacing 0.01em
H2:           Poppins, sans-serif        | 56px  | weight 600 | line-height 1.04 | letter-spacing 0.01em
H3:           Poppins, sans-serif        | 37px  | weight 600 | line-height 1.04 | letter-spacing 0.01em
H4:           Poppins, sans-serif        | 24px  | weight 600 | line-height 1.30 | letter-spacing 0.02em
H5:           Poppins, sans-serif        | 16px  | weight 600 | line-height 1.30 | letter-spacing 0.02em
Eyebrow:      Inter, sans-serif          | 15px  | weight 500 | line-height 1.30 | letter-spacing 0.01em | uppercase
Body XXL:     Inter, sans-serif          | 34px  | weight 400 | line-height 1.60
Body XL:      Inter, sans-serif          | 24px  | weight 400 | line-height 1.60
Body:         Inter, sans-serif          | 16px  | weight 400 | line-height 1.60
Body SM:      Inter, sans-serif          | 15px  | weight 400 | line-height 1.65
Caption:      Inter, sans-serif          | 10px  | weight 500 | line-height 1.30 | letter-spacing 0.01em
Code:         JetBrains Mono, monospace  | 14px  | weight 400 | line-height 1.50
```

Key type rules:
- Poppins Semibold (600) for ALL headings -- geometric, modern, never bold (700+)
- Inter Regular (400) for ALL body text and UI -- clean, highly legible
- Heading line-height is 1.04 (extremely tight) -- this is the visual signature
- Body line-height is 1.60 (generous) -- the contrast between tight headings and airy body creates the Webflow rhythm

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Webflow visual identity:
- Background: `#080808` (dark canvas -- Webflow's signature dark hero)
- Container: max-width 1280px, centered, padding 160px 64px
- Headline: 85px Poppins, weight 600, line-height 1.04, letter-spacing 0.01em, color `#ffffff`
- Subtitle: 24px Inter, weight 400, line-height 1.60, color `#ababab` (Gray 300), max-width 640px, margin-top 24px
- CTA button: background `#146ef5`, color `#ffffff`, 16px Inter weight 500, padding 14px 28px, border-radius 8px, transition 200ms ease-out
- CTA hover: background `#1060d4`, box-shadow `0 0 0 3px rgba(20,110,245,0.25)`
- Secondary button: background transparent, border 1px solid `#363636`, color `#ffffff`, padding 14px 28px, border-radius 8px
- Secondary hover: border-color `#5a5a5a`, background `#171717`
- Button row: flex, gap 16px, margin-top 40px
- Gradient accent: optional subtle radial gradient from `rgba(20,110,245,0.08)` at center-top to transparent, creating a soft blue halo behind the headline
- On mobile (<768px): headline 37px, subtitle 16px, section padding 80px 20px, buttons stack full-width

### Feature Card

Create a feature card with Webflow visual identity:
- Background: `#171717` (dark elevated surface)
- Border: 1px solid `#363636`
- Border-radius: 12px
- Padding: 32px
- Icon area: 48px square, `#146ef5` accent icon or SVG, margin-bottom 24px
- Title: 24px Poppins, weight 600, line-height 1.30, letter-spacing 0.02em, color `#ffffff`
- Description: 16px Inter, weight 400, line-height 1.60, color `#ababab`
- Hover state: border-color transitions to `#5a5a5a`, background shifts to `#222222`, transition 200ms
- On mobile (<768px): padding 24px, title 20px

Light variant:
- Background: `#ffffff`, border 1px solid `#e5e5e5`
- Title color: `#080808`, description color: `#5a5a5a`
- Hover: box-shadow `0 4px 16px rgba(0,0,0,0.08), 0 12px 32px -4px rgba(0,0,0,0.06)`

### CTA Button Row

Create a CTA button row with Webflow visual identity:
- Layout: flex, gap 16px, align-items center
- Primary button: background `#146ef5`, color `#ffffff`, font 16px Inter weight 500, padding 14px 28px, border-radius 8px, border none, cursor pointer, transition all 200ms ease-out
- Primary hover: background `#1060d4`, box-shadow `0 0 0 3px rgba(20,110,245,0.25)`
- Ghost button (dark bg): background transparent, border 1px solid `#363636`, color `#ffffff`, padding 14px 28px, border-radius 8px
- Ghost hover: border-color `#5a5a5a`, background `#171717`
- Outline button (light bg): background transparent, border 1px solid `#146ef5`, color `#146ef5`, padding 14px 28px, border-radius 8px
- Outline hover: background `rgba(20,110,245,0.06)`
- Text link button: color `#146ef5`, font 16px Inter weight 500, padding 0, border none, background none, text-decoration underline on hover
- On mobile (<768px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Webflow visual identity:
- Background: `#080808` with `backdrop-filter: blur(12px)` and slight transparency `rgba(8,8,8,0.92)`, position sticky, top 0, z-index 100
- Container: max-width 1280px, centered, padding 0 32px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Webflow W mark in `#ffffff` (SVG), 32px height
- Nav links: 15px Inter, weight 400, color `#ababab`, gap 32px, text-decoration none, transition color 150ms
- Nav link hover: color `#ffffff`
- CTA button (right): background `#146ef5`, color `#ffffff`, 14px Inter weight 500, padding 10px 20px, border-radius 8px
- Mobile (<768px): hamburger menu icon replacing nav links, CTA remains visible
- Bottom border: 1px solid `#171717`

Light variant:
- Background: `rgba(255,255,255,0.92)`, backdrop-filter blur(12px)
- Logo color: `#080808`, nav links `#5a5a5a`, hover `#080808`
- Bottom border: 1px solid `#f0f0f0`

### Data Card / Metric Display

Create a metric display card with Webflow visual identity:
- Background: `#171717`
- Border: 1px solid `#363636`
- Border-radius: 12px
- Padding: 32px
- Eyebrow label: 10px Inter, weight 500, letter-spacing 0.01em, text-transform uppercase, color `#757575`, margin-bottom 8px
- Metric value: 56px Poppins, weight 600, line-height 1.04, color `#ffffff`
- Metric accent: optionally color the metric in `#146ef5` for emphasis
- Metric description: 15px Inter, weight 400, line-height 1.65, color `#ababab`, margin-top 12px
- Trend indicator: inline pill with `#00d722` background (up) or `#ee1d36` (down), 12px weight 500, border-radius 4px, padding 2px 8px
- On mobile (<768px): metric value 37px, padding 24px

### Visual Editor Panel / Styles Inspector

Create a styles inspector panel reflecting Webflow's editor UI:
- Panel background: `#222222` (Gray 800 -- editor panel surface)
- Panel border-left: 1px solid `#363636`
- Width: 320px, height 100vh, overflow-y auto
- Panel header: padding 16px, display flex, justify-content space-between, align-items center, border-bottom 1px solid `#363636`
- Panel title: 13px Inter, weight 600, color `#ffffff`, text-transform uppercase, letter-spacing 0.02em
- Section divider: 1px solid `#363636`, margin 0
- Property group: padding 16px
- Property label: 11px Inter, weight 500, color `#757575` (Gray 500), margin-bottom 6px
- Property input: background `#171717`, border 1px solid `#363636`, border-radius 4px, padding 6px 8px, color `#ffffff`, font 13px Inter, width 100%
- Property input focus: border-color `#146ef5`, box-shadow `0 0 0 2px rgba(20,110,245,0.25)`
- Color swatch: 24px square, border-radius 4px, border 1px solid `#363636`, display inline-block
- Slider track: height 4px, background `#363636`, border-radius 2px
- Slider thumb: 12px circle, background `#ffffff`, border 2px solid `#146ef5`
- Toggle on: background `#146ef5`, border-radius 12px, width 36px height 20px
- Toggle off: background `#363636`
- Dropdown: background `#171717`, border 1px solid `#363636`, border-radius 4px, color `#ffffff`, 13px Inter
- Section collapse chevron: 12px, color `#757575`, transition transform 200ms
- Scrollbar: 4px width, `#363636` track, `#5a5a5a` thumb, border-radius 2px

---

## 4. Iteration Guide

1. **Dark canvas is the native state.** Webflow's editor and marketing both default to dark (`#080808`). Start dark, then create light variants. If a component looks equally at home on white and black, you have the right neutrals. If it only works on white, you have missed the brand.

2. **Webflow Blue (`#146ef5`) is surgical, not decorative.** It appears on: primary CTAs, focus rings, active states, selected items, and the occasional accent icon. Never fill a card, section background, or illustration area with it. One blue element per visual group maximum.

3. **Heading line-height 1.04 is the signature.** Webflow's geometric headings sit extremely tight. If your headings look "normal," you have too much line-height. The tension between ultra-tight headings and generous (1.60) body text is the typographic identity.

4. **Geometric sans, not humanist sans.** Poppins (substitute for WF Visual Sans) has perfectly circular O's and even stroke width. Never substitute with humanist sans fonts (San Francisco, Helvetica) which have optical corrections that feel warm rather than precise.

5. **Monochromatic discipline: black + white + one color.** Every composition is grayscale plus one chromatic accent (usually Webflow Blue). This is an explicit brand rule. Introducing a second chromatic color (green success indicators, warm CTAs, gradient rainbows) violates the system.

6. **Borders define structure on dark surfaces.** Where light designs use shadows for depth, Webflow uses `#363636` borders (Gray 700) on dark surfaces. The 1px solid border is the primary depth signal in dark mode. Shadows are supplementary, never primary.

7. **The editor aesthetic is product-grade UI, not marketing fluff.** Components like the Styles Inspector should feel like real software: compact spacing (16px sections, 6px input padding), small type (11-13px), functional density. Marketing components can breathe more (120-160px section padding), but tool-UI components must feel dense and precise.

8. **Motion is build-enhance-reduce.** Transitions should feel like construction: elements layer in, not slide from off-screen. Default duration 200ms, easing ease-out. Hover states shift subtly (border-color change, background darken). No bounce, no elastic overshoot on functional UI.

9. **Gray scale is precise, not approximate.** Webflow defines exact gray steps: `#171717` / `#222222` / `#363636` / `#5a5a5a` / `#757575` / `#898989` / `#ababab` / `#d8d8d8` / `#f0f0f0`. Use these exact values. Approximate grays (`#333`, `#666`, `#999`) break the tonal precision.

10. **Every component should feel like part of a visual builder.** Webflow is a tool for designers. Components should communicate precision, control, and intentionality -- never whimsy. Clean edges, consistent radii, systematic spacing. The design should look like it was built by a design tool, because it was.
