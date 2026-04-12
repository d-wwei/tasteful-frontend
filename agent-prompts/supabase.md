# Supabase -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Supabase-branded components.
Aesthetic: dark-mode-native developer platform -- emerald green accents on near-black surfaces with border-defined depth.

---

## 1. Quick Color Reference

```
Surface (page bg):      #171717   Near-black canvas — the void everything floats on
Surface elevated:       #1c1c1c   Cards, panels, sidebars — one notch above the void
Surface overlay:        #232323   Modals, dropdowns, command palette
Surface code:           #11181C   Code blocks and SQL editor — Bunker, deepest dark
Accent green:           #3ecf8e   Emerald — CTAs, active states, success
Accent hover:           #2da672   Darkened green — hover, pressed states
Accent subtle:          rgba(62,207,142,0.12)  Selected rows, soft highlights
Brand green:            #34B27B   Jungle Green — logo mark, brand identity moments
Text primary:           #ededed   Headings, important content
Text secondary:         #8f8f8f   Body copy, descriptions, metadata
Text tertiary:          #5c5c5c   Placeholders, disabled, timestamps
Text on accent:         #030303   Text on green backgrounds
Text code:              #e0e0e0   Monospace content
Error:                  #f56565   Destructive, danger
Warning:                #f5a623   Caution, deprecation
Border default:         rgba(255,255,255,0.06)  Subtle separation
Border strong:          rgba(255,255,255,0.12)  Dividers, focus rings
```

---

## 2. Quick Typography Reference

```
Display:    Circular, -apple-system, sans-serif    | 48px | weight 700 | line-height 1.15 | tracking -0.02em
H1:         Circular, -apple-system, sans-serif    | 36px | weight 600 | line-height 1.15 | tracking -0.02em
H2:         Circular, -apple-system, sans-serif    | 30px | weight 600 | line-height 1.35
H3:         Circular, -apple-system, sans-serif    | 24px | weight 600 | line-height 1.35
Body Lg:    Circular, -apple-system, sans-serif    | 18px | weight 400 | line-height 1.55
Body:       Circular, -apple-system, sans-serif    | 15px | weight 400 | line-height 1.55
Small:      Circular, -apple-system, sans-serif    | 14px | weight 400 | line-height 1.43
XS:         Circular, -apple-system, sans-serif    | 13px | weight 400 | line-height 1.40
Code:       Source Code Pro, Menlo, monospace       | 13px | weight 400 | line-height 1.70
Overline:   Circular, -apple-system, sans-serif    | 11px | weight 600 | line-height 1.25 | tracking 0.08em | uppercase
```

Key rules:
- Circular (or system fallback) for ALL text — headings and body share the same family
- Source Code Pro for all monospace: SQL editors, inline code, terminal output, API references
- Body is 15px, not 16px — tighter than typical, matching Supabase's information-dense layout
- Display headlines use -0.02em tracking for optical tightness

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Supabase visual identity:
- Background: `#171717` (near-black canvas)
- Container: max-width 1100px, centered, padding 120px 48px
- Overline: 11px Circular, weight 600, uppercase, letter-spacing 0.08em, color `#3ecf8e`, margin-bottom 16px
- Headline: 48px Circular, weight 700, line-height 1.15, letter-spacing -0.02em, color `#ededed`
- Gradient text option: `background: linear-gradient(to right, #ededed, #8f8f8f); -webkit-background-clip: text; -webkit-text-fill-color: transparent`
- Subtitle: 18px Circular, weight 400, line-height 1.55, color `#8f8f8f`, max-width 560px, margin-top 20px
- CTA button: background `#3ecf8e`, color `#030303`, 14px weight 500, padding 8px 16px, border-radius 6px, transition 200ms
- CTA hover: background `#2da672`
- Secondary button: background transparent, border 1px solid `rgba(255,255,255,0.12)`, color `#ededed`, padding 8px 16px, border-radius 6px
- Secondary hover: border-color `rgba(255,255,255,0.24)`, background `rgba(255,255,255,0.04)`
- Button row: flex, gap 12px, margin-top 32px
- Terminal preview below hero: background `#11181C`, border 1px solid `rgba(255,255,255,0.06)`, border-radius 8px, padding 24px, margin-top 48px, font-family `Source Code Pro`, font-size 13px, line-height 1.70, color `#e0e0e0`
- On mobile (<640px): headline 32px, subtitle 16px, padding 64px 20px, buttons stack full-width

### Feature Card

Create a feature card with Supabase visual identity:
- Background: `#1c1c1c` (elevated surface)
- Border: 1px solid `rgba(255,255,255,0.06)`
- Border-radius: 8px
- Padding: 24px
- Icon area: 40px square, background `rgba(62,207,142,0.12)`, border-radius 8px, display flex align-items center justify-content center, color `#3ecf8e`, margin-bottom 16px
- Title: 18px Circular, weight 600, line-height 1.35, color `#ededed`, margin-bottom 8px
- Description: 15px Circular, weight 400, line-height 1.55, color `#8f8f8f`
- Hover: border-color `rgba(255,255,255,0.12)`, transition 200ms
- On mobile (<640px): padding 20px

### CTA Button Row

Create a CTA button row with Supabase visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#3ecf8e`, color `#030303`, font 14px Circular weight 500, padding 8px 16px, border-radius 6px, border none, cursor pointer, transition all 200ms ease-out
- Primary hover: background `#2da672`, box-shadow `0 0 16px rgba(62,207,142,0.15)`
- Primary active: transform scale(0.98)
- Ghost button: background transparent, color `#ededed`, border 1px solid `rgba(255,255,255,0.12)`, padding 8px 16px, border-radius 6px
- Ghost hover: background `rgba(255,255,255,0.04)`, border-color `rgba(255,255,255,0.24)`
- Danger button: background `rgba(245,101,101,0.12)`, color `#f56565`, border 1px solid `rgba(245,101,101,0.20)`, padding 8px 16px, border-radius 6px
- Danger hover: background `rgba(245,101,101,0.20)`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Supabase visual identity:
- Background: `#171717`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.06)`
- Backdrop-filter: blur(12px), background with alpha `rgba(23,23,23,0.85)` for glass effect
- Container: max-width 1100px, centered, padding 0 24px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Supabase wordmark, color `#ededed`, height 20px, left-aligned
- Nav links: 14px Circular weight 400, color `#8f8f8f`, gap 24px, text-decoration none
- Nav link hover: color `#ededed`, transition 150ms
- Active nav link: color `#ededed`
- CTA button (right): background `#3ecf8e`, color `#030303`, 13px weight 500, padding 6px 12px, border-radius 6px
- On mobile (<768px): nav links collapse to hamburger icon, CTA remains visible

### Dashboard Sidebar

Create a dashboard sidebar with Supabase visual identity:
- Background: `#1c1c1c`, width 240px, height 100vh, position fixed, left 0
- Border-right: 1px solid `rgba(255,255,255,0.06)`
- Padding: 16px 12px
- Project selector (top): padding 8px 12px, border-radius 6px, background `rgba(255,255,255,0.04)`, display flex, align-items center, gap 8px
- Project name: 14px weight 500, color `#ededed`
- Project icon: 24px square, background `#3ecf8e`, border-radius 4px, color `#030303`, font-weight 700, font-size 12px, display flex align-items center justify-content center
- Nav section label: 11px weight 600, uppercase, letter-spacing 0.08em, color `#5c5c5c`, padding 16px 12px 8px
- Nav item: 14px weight 400, color `#8f8f8f`, padding 6px 12px, border-radius 4px, cursor pointer, transition 100ms
- Nav item hover: background `rgba(255,255,255,0.04)`, color `#ededed`
- Nav item active: background `rgba(62,207,142,0.12)`, color `#3ecf8e`
- Nav item icon: 16px, margin-right 8px, opacity 0.7

### Database Table View / SQL Editor Panel (Brand-Specific)

Create a Supabase database table view and SQL editor panel:
- Overall layout: flex column, height 100%, background `#171717`
- **Table toolbar**: height 48px, padding 0 16px, display flex, align-items center, justify-content space-between, background `#1c1c1c`, border-bottom 1px solid `rgba(255,255,255,0.06)`
- Table name: 14px weight 600, color `#ededed`
- Row count badge: 13px weight 400, color `#5c5c5c`, margin-left 8px
- Toolbar actions (right): flex, gap 8px, buttons with 13px weight 500, color `#8f8f8f`, padding 4px 8px, border-radius 4px, hover background `rgba(255,255,255,0.04)`
- Insert row button: background `#3ecf8e`, color `#030303`, 13px weight 500, padding 4px 12px, border-radius 4px
- **Column headers**: height 36px, display grid, background `#1c1c1c`, border-bottom 1px solid `rgba(255,255,255,0.06)`, font-size 13px, weight 500, color `#5c5c5c`, text-transform none, padding 0 12px, align-items center
- Column header hover: color `#8f8f8f`
- Column type icon: 12px, color `#5c5c5c`, margin-right 4px (shows data type: int4, text, uuid, bool, timestamptz)
- **Table rows**: height 36px, display grid matching columns, border-bottom 1px solid `rgba(255,255,255,0.04)`, font-family `Source Code Pro`, font-size 13px, line-height 1.70, color `#e0e0e0`, padding 0 12px, align-items center
- Row hover: background `rgba(255,255,255,0.02)`
- Selected row: background `rgba(62,207,142,0.08)`, border-left 2px solid `#3ecf8e`
- NULL value display: color `#5c5c5c`, font-style italic, content "NULL"
- Boolean true: color `#3ecf8e`
- Boolean false: color `#8f8f8f`
- UUID column: font-family `Source Code Pro`, color `#8f8f8f`, font-size 12px
- **SQL editor pane** (below or split): background `#11181C`, min-height 200px, border-top 1px solid `rgba(255,255,255,0.06)`
- Editor header: height 40px, padding 0 16px, background `#1c1c1c`, display flex, align-items center, gap 12px, border-bottom 1px solid `rgba(255,255,255,0.06)`
- Run query button: background `#3ecf8e`, color `#030303`, 13px weight 500, padding 4px 12px, border-radius 4px, gap 4px with play icon
- Editor body: padding 16px, font-family `Source Code Pro`, font-size 13px, line-height 1.70, color `#e0e0e0`
- SQL keywords: color `#c792ea` (purple for SELECT, FROM, WHERE, INSERT, etc.)
- SQL strings: color `#c3e88d` (green for string literals)
- SQL numbers: color `#f78c6c` (orange for numeric values)
- SQL comments: color `#5c5c5c`, font-style italic
- Line numbers: color `#5c5c5c`, width 40px, text-align right, padding-right 16px, border-right 1px solid `rgba(255,255,255,0.04)`, user-select none

---

## 4. Iteration Guide

1. **Dark surfaces are the foundation — everything else is additive.** Start every component from `#171717` (canvas) or `#1c1c1c` (panel). The near-black void is not a background color; it IS the brand. Never introduce light surfaces unless building a documented light-mode variant.

2. **Depth comes from borders, not shadows.** Supabase defines spatial hierarchy through `rgba(255,255,255,0.06)` and `rgba(255,255,255,0.12)` border lines. Shadows are reserved for floating elements (dropdowns, modals) and even then are dark and heavy (`rgba(0,0,0,0.40+)`). If you reach for `box-shadow` on a card, stop — use a border instead.

3. **Green is the reward color.** `#3ecf8e` appears on: primary CTAs, active navigation states, success confirmations, and selected rows. It NEVER appears as: a decorative surface fill, a heading color, a background wash, or a passive UI element. The restraint is what makes it meaningful.

4. **Monospace is a first-class citizen.** `Source Code Pro` at 13px/1.70 is not a secondary typographic choice — it is central to Supabase's identity as a developer tool. Code blocks, SQL editors, API responses, table cell data, and terminal output all use monospace. Every Supabase-branded page should have visible monospace content.

5. **Information density over white space.** Supabase packs data into compact UI: 36px table rows, 56px nav height, 14px nav links, 6px border-radius. This is not minimalism — it is a tool-first aesthetic where every pixel earns its place. Resist the urge to add generous padding. The spacious moments (section gaps at 80px) exist to offset the dense tool areas.

6. **Border-radius is subtle.** 4px for small elements, 6px for buttons and inputs, 8px for cards and panels. Never exceed 12px except for hero sections. This keeps the interface feeling precise and engineered, not playful.

7. **Color syntax highlighting in code is part of the brand.** SQL keywords in purple (`#c792ea`), strings in green (`#c3e88d`), numbers in orange (`#f78c6c`), comments in muted gray (`#5c5c5c`). This palette is consistent across every code surface — editor, documentation examples, and marketing pages.

8. **Glassmorphism on navigation only.** The sticky nav uses `backdrop-filter: blur(12px)` with `rgba(23,23,23,0.85)`. This effect is NOT used on cards, panels, or other elements. It is a single intentional moment of visual sophistication at the top of the viewport.

9. **Button hierarchy is strict.** Green filled = primary/destructive-important action. Ghost with border = secondary action. Text-only = tertiary/cancel. Red-tinted = destructive. There is no "medium emphasis" button — the jump from green to ghost is intentional.

10. **Test every component on `#171717`.** If a component looks washed out or loses its edges when placed on the page background, it is under-differentiated. Increase border opacity or surface lightness by one step. If it looks like it is floating, it has too much shadow — reduce to border-only.
