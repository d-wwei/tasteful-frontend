# Notion -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Notion-branded components.
Aesthetic: content-first canvas -- warm-neutral minimalism with block-based rhythm and system typography.

---

## 1. Quick Color Reference

```
Surface (page bg):       #ffffff   Clean white canvas — content-first, zero decoration
Surface subtle:          #f7f6f3   Warm off-white — sidebar background, secondary surfaces
Surface hover:           #efefef   Block hover state — light warm gray
Accent (Notion Blue):    #2eaadc   Links, selected states, interactive highlights
Accent hover:            #2691bd   Darker Notion Blue for hover
Text primary:            #37352f   Warm charcoal — Notion's signature text color, never pure black
Text secondary:          #787774   Medium warm gray — descriptions, metadata
Text tertiary:           #9b9a97   Light warm gray — placeholders, timestamps
Icon default:            #55534e   Slightly lighter than text-primary for icons
CTA black:               #000000   Solid black — marketing page buttons
CTA black hover:         #37352f   Warm charcoal hover on black buttons
Border:                  #e9e9e7   Standard warm border — dividers, table lines
Border dark:             #d3d1cb   Emphasized border — active states
Bg gray tint:            #f1f1ef   Callout blocks, inline code backgrounds, tag fills
Bg orange tint:          #f8ecdf   Orange highlight background
Bg yellow tint:          #faf3dd   Yellow highlight background
Bg blue tint:            #e9f3f7   Blue highlight background
Bg green tint:           #eef3ed   Green highlight background
Bg red tint:             #faecec   Red/error background tint
Notion Brown:            #9b6f50   Brown text/icon accent
Notion Orange:           #d9730d   Orange icon accent
Notion Red:              #e03e3e   Destructive actions, error states
Notion Green:            #448361   Success states, green icon
Notion Purple:           #9065b0   Purple tag/icon accent
Notion Pink:             #c14c8a   Pink icon accent
Error:                   #eb5757   Validation errors
Success:                 #4dab9a   Success teal-green
Warning:                 #f7c948   Warning yellow
```

---

## 2. Quick Typography Reference

```
Hero:       -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 40px | weight 700 | line-height 1.15
H1:         -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 30px | weight 700 | line-height 1.30
H2:         -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 24px | weight 600 | line-height 1.30
H3:         -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 20px | weight 600 | line-height 1.30
Body:       -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 16px | weight 400 | line-height 1.50
UI/Caption: -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 14px | weight 500 | line-height 1.43
Small:      -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif | 12px | weight 400 | line-height 1.33
Code:       iawriter-mono, Nitti, Menlo, Courier, monospace                           | 14px | weight 400 | line-height 1.50
```

Key rules:
- Single font stack for everything -- system fonts only, no custom display face
- Weight hierarchy does the work: 700 for H1/hero, 600 for H2/H3, 500 for UI, 400 for body
- Never use font-weight above 700 -- Notion does not use 800 or 900
- Body line-height is 1.50 -- slightly tighter than editorial sites, optimized for block rhythm
- Notion offers three user-selectable fonts (Default/sans, Serif/Lyon-Text, Mono/iawriter-mono) but the brand identity is the default sans system stack

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Notion visual identity:
- Background: `#ffffff` (clean white canvas)
- Container: max-width 900px, centered, padding 96px horizontal (desktop), 24px (mobile)
- Vertical padding: 80px top, 64px bottom
- Headline: "Your wiki, docs, & projects. Together." at 40px system font stack, weight 700, line-height 1.15, color `#37352f`, max-width 720px
- Subtitle: 16px system font stack, weight 400, line-height 1.50, color `#787774`, max-width 540px, margin-top 16px
- CTA button: background `#000000`, color `#ffffff`, 14px weight 500, padding 8px 14px, border-radius 3px, no box-shadow, cursor pointer
- CTA hover: background `#37352f`
- Secondary link: color `#2eaadc`, 14px weight 500, text-decoration underline on hover, margin-left 16px
- On mobile (<640px): headline 28px, subtitle 14px, section padding 48px 24px, CTA full-width

### Feature Card (Notion Block Card)

Create a feature card with Notion block-card visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e9e9e7`
- Border-radius: 8px
- Padding: 24px
- No box-shadow at rest (flat, border-driven separation)
- Hover: background shifts to `#f7f6f3`, transition 100ms ease
- Title: 16px system font stack, weight 600, line-height 1.30, color `#37352f`, margin-bottom 8px
- Description: 14px system font stack, weight 400, line-height 1.50, color `#787774`
- Icon: 24px, color `#55534e`, margin-bottom 12px -- use simple line icons (not filled)
- Optional colored icon: use Notion color accents (`#d9730d`, `#448361`, `#337ea9`, `#9065b0`) for categorical differentiation
- On mobile (<640px): padding 16px, single column layout

### CTA Button Row

Create a CTA button row with Notion visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Black): background `#000000`, color `#ffffff`, font 14px system stack weight 500, padding 8px 14px, border-radius 3px, border: none, cursor pointer, transition: background 100ms ease
- Primary hover: background `#37352f`
- Secondary button (Blue link): background transparent, color `#2eaadc`, font 14px weight 500, padding 8px 14px, border: none, text-decoration none
- Secondary hover: text-decoration underline
- Outline button (when needed): background transparent, color `#37352f`, font 14px weight 500, padding 7px 13px, border: 1px solid `#e9e9e7`, border-radius 3px
- Outline hover: background `#f7f6f3`
- On mobile (<640px): flex-direction column, buttons full-width, gap 8px

### Navigation Bar (Notion Sidebar-Style)

Create a navigation bar with Notion visual identity:
- Top bar: background `#ffffff`, position sticky, top 0, z-index 100, height 45px
- Border-bottom: 1px solid `#e9e9e7`
- Container: max-width 1200px, centered, padding 0 16px, display flex, align-items center, justify-content space-between
- Logo: Notion wordmark in `#37352f`, font-size 18px, weight 700, letter-spacing -0.5px (or SVG logo)
- Nav links: 14px system font stack, weight 500, color `#787774`, gap 24px, text-decoration none
- Nav link hover: color `#37352f`, transition 100ms
- CTA button (right): background `#000000`, color `#ffffff`, 14px weight 500, padding 6px 12px, border-radius 3px
- Sidebar variant: width 240px, background `#f7f6f3`, border-right 1px solid `#e9e9e7`, padding 12px 8px
- Sidebar item: 14px weight 500, color `#787774`, padding 4px 8px, border-radius 3px, display flex, align-items center, gap 8px
- Sidebar item hover: background `#efefef`
- Sidebar item active: background `#efefef`, color `#37352f`
- On mobile (<768px): top bar only, hamburger menu replaces sidebar

### Data/Content Block Display

Create a content block display with Notion visual identity:
- Container: max-width 900px, centered, padding 0 96px (desktop), 0 24px (mobile)
- Block spacing: 4px between adjacent text blocks, 16px between heading and following block, 24px before a heading
- Text block: 16px system font stack, weight 400, line-height 1.50, color `#37352f`
- Callout block: background `#f1f1ef` (bg-gray), border-radius 3px, padding 16px 16px 16px 12px, display flex, gap 8px
- Callout icon: 20px, flex-shrink 0
- Callout text: 16px, weight 400, color `#37352f`, line-height 1.50
- Inline code: background `#f1f1ef`, color `#eb5757` (red tint for visibility), padding 2px 4px, border-radius 3px, font-family iawriter-mono/Menlo/monospace, font-size 14px
- Divider: border-top 1px solid `#e9e9e7`, margin 8px 0
- Toggle block: 16px, weight 400, color `#37352f`, with disclosure triangle `#787774` at left
- On mobile (<640px): page padding collapses to 24px

### Brand-Specific: Notion Database View / Kanban Card

Create a Notion-style database kanban card:
- Board background: `#ffffff`
- Column container: min-width 260px, max-width 340px
- Column header: 14px system font stack, weight 600, color `#37352f`, padding 8px 0, display flex, align-items center, gap 8px
- Column header count: 12px weight 400, color `#9b9a97`, background none
- Card: background `#ffffff`, border: 1px solid `#e9e9e7`, border-radius 3px, padding 8px 10px, margin-bottom 6px, cursor grab
- Card hover: background `#f7f6f3`, transition 100ms
- Card title: 14px weight 400, color `#37352f`, line-height 1.43
- Card property tag: display inline-flex, font-size 12px, weight 400, padding 2px 6px, border-radius 3px, background color-tint (e.g., `#e9f3f7` for blue, `#eef3ed` for green), color matching Notion accent (e.g., `#337ea9` for blue, `#448361` for green)
- Card property text: 12px weight 400, color `#9b9a97`
- Card cover image: width 100%, height 120px, object-fit cover, border-radius 3px 3px 0 0, margin -8px -10px 8px -10px
- Add new card: 14px weight 400, color `#9b9a97`, padding 8px 10px, cursor pointer
- Add new card hover: background `#f7f6f3`, color `#37352f`
- Drag shadow: `0 12px 32px rgba(0,0,0,0.12)` (level-2 shadow during drag)
- On mobile (<640px): single column scroll, card full-width with 16px horizontal padding

---

## 4. Iteration Guide

1. **White canvas is non-negotiable.** The page background must be `#ffffff` -- never off-white, never cream, never gray. Content sits on a clean, bright white canvas. The warmth comes from `#37352f` text and `#f7f6f3` secondary surfaces, not from the page itself. Verify: `body { background: #ffffff }`.

2. **Use `#37352f` for all primary text, never `#000000`.** Notion's warm charcoal is the single most distinctive color in the system. Pure black looks harsh against the warm neutral palette. Verify: no text element uses `color: #000000` except inside solid-black CTA buttons.

3. **Borders do the heavy lifting, not shadows.** Notion separates elements with 1px solid `#e9e9e7` borders, not drop shadows. Shadow level-0 (`0 1px 0 rgba(55,53,47,0.09)`) is a border-simulation, not elevation. Reserve actual shadows (level-1, level-2) exclusively for floating elements: dropdowns, modals, tooltips, and drag states. Verify: cards and sections use border, not box-shadow.

4. **Respect block adjacency spacing.** Notion's spacing is not uniform -- it is context-aware. Text-to-text gaps are tight (4px). Heading-to-body gaps are moderate (16px). Section breaks are generous (24-48px). List items adjacent to list items compress together. If every gap is the same size, the layout does not feel like Notion.

5. **System font stack with no fallback to Inter or custom fonts.** The font declaration must start with `-apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif`. Do not substitute with Inter, SF Pro, or any named font. The whole point of Notion's type system is native platform feel. Verify: font-family CSS property uses the system stack.

6. **Accent blue (`#2eaadc`) is for interaction signals only.** Links, selected sidebar items, active toggle states, and focused inputs. Never use it as a decorative fill, card background, or gradient ingredient. If an element is not interactive, it does not get Notion Blue. Verify: every instance of `#2eaadc` is on a clickable or focusable element.
