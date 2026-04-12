# Shopify (Polaris) -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Shopify-branded components.
Aesthetic: Polaris admin — merchant-focused workspace with gray canvas, white card surfaces, bevel-shadow depth, and restrained commerce-green accents.

---

## 1. Quick Color Reference

```
Page bg (canvas):    #f1f1f1   Gray Canvas -- neutral admin background behind cards
Card surface:        #ffffff   White -- primary content containers
Surface hover:       #f7f7f7   Light Gray -- interactive surface feedback
Surface secondary:   #f7f7f7   Subtle Gray -- filters, sidebars, secondary panels
Brand fill:          #303030   Near Black -- primary buttons, nav chrome, dark UI fill
Brand fill hover:    #1a1a1a   Darker -- deepened on interaction
Success / Green:     #047b5d   Commerce Green -- positive states, success badges
Critical:            #c70a24   Red -- destructive actions, error states
Warning:             #ffb800   Amber -- caution banners, warnings
Info:                #91d0ff   Light Blue -- informational badges
Text primary:        #303030   Near Black -- headings and body text
Text secondary:      #616161   Medium Gray -- descriptions, metadata
Text link:           #005bd3   Interactive Blue -- hyperlinks, linked actions
Border:              #e3e3e3   Light Border -- card edges, dividers, table rows
Focus ring:          #005bd3   Interactive Blue -- keyboard focus indicator
Icon default:        #4a4a4a   Icon Gray -- standard icon fill
```

---

## 2. Quick Typography Reference

```
Display:      Inter, -apple-system, sans-serif  | 40px | weight 700 | line-height 48px | letter-spacing -0.54px
Heading XL:   Inter, -apple-system, sans-serif  | 30px | weight 650 | line-height 40px | letter-spacing -0.3px
Heading LG:   Inter, -apple-system, sans-serif  | 24px | weight 650 | line-height 32px | letter-spacing -0.2px
Heading MD:   Inter, -apple-system, sans-serif  | 20px | weight 650 | line-height 28px | letter-spacing -0.2px
Body:         Inter, -apple-system, sans-serif  | 14px | weight 450 | line-height 20px | letter-spacing 0
Body LG:      Inter, -apple-system, sans-serif  | 16px | weight 450 | line-height 24px | letter-spacing 0
Caption:      Inter, -apple-system, sans-serif  | 13px | weight 450 | line-height 20px | letter-spacing 0
Small:        Inter, -apple-system, sans-serif  | 12px | weight 450 | line-height 16px | letter-spacing 0
Badge:        Inter, -apple-system, sans-serif  | 11px | weight 550 | line-height 16px | letter-spacing 0
Mono:         ui-monospace, SFMono-Regular, monospace | 13px | weight 450 | line-height 20px
```

Key rules:
- Polaris uses Inter exclusively — no serif fonts anywhere
- Regular weight is 450 (not standard 400), medium 550, semibold 650
- 14px is the default body size, NOT 16px — Polaris optimizes for information density
- All line-heights snap to the 4px grid (16, 20, 24, 28, 32, 40, 48)
- Negative letter-spacing on headings 20px+ for tighter headlines

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Shopify/Polaris visual identity:
- Background: `#f1f1f1` (Gray Canvas — the admin page background)
- Container: max-width 1040px, centered, padding 64px 20px
- Headline: "Build your business" at 40px Inter, weight 700, line-height 48px, letter-spacing -0.54px, color `#303030`
- Subtitle: 16px Inter, weight 450, line-height 24px, color `#616161`, max-width 600px, margin-top 16px
- CTA button: background `#303030`, color `#ffffff`, 14px Inter weight 550, padding 8px 16px, border-radius 8px, box-shadow: `inset 0 -1px 0 0 rgba(0,0,0,0.2), inset 0 1px 0 0 rgba(255,255,255,0.04)` (Polaris bevel), cursor pointer
- CTA hover: background `#1a1a1a`
- Secondary button: background `#ffffff`, color `#303030`, 14px weight 550, padding 8px 16px, border-radius 8px, box-shadow: `0px 0px 0px 1px rgba(0,0,0,0.08) inset, 0px -1px 0px 0px rgba(0,0,0,0.2) inset, 0px 1px 0px 0px rgba(255,255,255,0.04) inset`
- Button row gap: 8px, margin-top 24px
- On mobile (<490px): headline drops to 30px, line-height 40px, section padding 32px 16px, buttons stack full-width

### Feature Card

Create a feature card with Shopify/Polaris visual identity:
- Background: `#ffffff` (white card surface)
- Border: 1px solid `#e3e3e3`
- Border-radius: 12px
- Padding: 16px (Polaris card-padding standard)
- Box-shadow: `0px 1px 0px 0px rgba(26, 26, 26, 0.07)` (shadow-100 — the subtle card resting shadow)
- Title: 16px Inter, weight 650, line-height 24px, color `#303030`, margin-bottom 8px
- Description: 14px Inter, weight 450, line-height 20px, color `#616161`
- Icon area: 40px square container, 20px icon inside, color `#4a4a4a`, background `#f7f7f7`, border-radius 8px, margin-bottom 12px
- Hover state: box-shadow shifts to shadow-200 `0px 3px 1px -1px rgba(26, 26, 26, 0.07)`, border-color stays `#e3e3e3`
- On mobile (<490px): padding 12px, icon area 32px square

### CTA Button Row

Create a CTA button row with Shopify/Polaris visual identity:
- Layout: flex, gap 8px (Polaris button-group-gap), align-items center
- Primary button (Brand fill): background `#303030`, color `#ffffff`, font 14px Inter weight 550, padding 8px 16px, border-radius 8px, border: none, box-shadow: `inset 0 -1px 0 0 rgba(0,0,0,0.2), inset 0 1px 0 0 rgba(255,255,255,0.04)`, cursor pointer, transition: background 150ms cubic-bezier(0.25, 0.1, 0.25, 1), min-height 36px
- Primary hover: background `#1a1a1a`
- Primary active/pressed: background `#1a1a1a`, box-shadow: `inset 0 2px 1px 0 rgba(0,0,0,0.2), inset 0 1px 1px 0 rgba(0,0,0,0.12)`
- Secondary button (Default): background `#ffffff`, color `#303030`, font 14px weight 550, padding 8px 16px, border-radius 8px, border: none, box-shadow: `0px 0px 0px 1px rgba(0,0,0,0.08) inset`, min-height 36px
- Secondary hover: background `#f7f7f7`
- Critical button: background `#c70a24`, color `#ffffff`, same padding/radius, box-shadow: `inset 0 -1px 0 0 rgba(0,0,0,0.2), inset 0 1px 0 0 rgba(255,255,255,0.04)`
- On mobile (<490px): flex-direction column, buttons full-width

### Navigation Bar (Admin Top Bar)

Create a navigation bar with Shopify/Polaris admin identity:
- Background: `#303030` (brand dark surface — the Shopify admin top bar is dark), height 56px
- Container: width 100%, padding 0 16px, display flex, align-items center, justify-content space-between
- Logo: Shopify bag icon or wordmark in `#ffffff`, left side, 32px height
- Search bar (center): background `rgba(255,255,255,0.12)`, color `#e3e3e3`, placeholder `rgba(255,255,255,0.5)`, 14px Inter weight 450, padding 8px 12px, border-radius 8px, border: 1px solid `rgba(255,255,255,0.08)`, flex 1, max-width 580px, margin 0 16px
- Search focus: background `#ffffff`, color `#303030`, border-color `#005bd3`
- Right icons: 20px, color `rgba(255,255,255,0.8)`, gap 12px, hover: color `#ffffff`
- Avatar (far right): 28px circle, background `#047b5d`, color `#ffffff`, 12px Inter weight 650
- On mobile (<768px): search bar collapses to icon, gap tightens to 8px

### Data Card / Metric Display

Create a metric display card with Shopify/Polaris visual identity:
- Background: `#ffffff` (white card surface)
- Border: 1px solid `#e3e3e3`
- Border-radius: 12px
- Padding: 16px
- Box-shadow: `0px 1px 0px 0px rgba(26, 26, 26, 0.07)` (shadow-100)
- Overline label: 13px Inter, weight 450, line-height 20px, color `#616161`, margin-bottom 4px
- Metric value: 30px Inter, weight 650, line-height 40px, letter-spacing -0.3px, color `#303030`
- Trend indicator: 13px Inter, weight 550, color `#047b5d` for positive / `#c70a24` for negative, with inline arrow icon, margin-top 4px
- Metric description: 13px Inter, weight 450, line-height 20px, color `#616161`, margin-top 8px
- Sparkline area (optional): height 40px, stroke `#047b5d` at 1.5px, fill `rgba(4, 123, 93, 0.08)`, margin-top 12px
- On mobile (<490px): metric value 24px line-height 32px, padding 12px

### Polaris Resource List / Product Card

Create a product resource list item with Shopify/Polaris visual identity — the signature admin pattern:
- Container: background `#ffffff`, border-bottom 1px solid `#e3e3e3`, padding 12px 16px, display flex, align-items center, gap 12px, cursor pointer, transition background 100ms
- Container hover: background `#f7f7f7`
- Thumbnail: 40px square, border-radius 4px, border: 1px solid `#e3e3e3`, object-fit cover, flex-shrink 0
- Content area: flex 1, min-width 0
- Product title: 14px Inter, weight 550, line-height 20px, color `#303030`, text-overflow ellipsis, white-space nowrap, overflow hidden
- Product subtitle: 13px Inter, weight 450, line-height 20px, color `#616161`, margin-top 2px
- Status badge: display inline-flex, align-items center, padding 2px 8px, border-radius 9999px, font 11px Inter weight 550, line-height 16px
  - Active: background `rgba(4, 123, 93, 0.12)`, color `#014b40`
  - Draft: background `rgba(97, 97, 97, 0.12)`, color `#616161`
  - Archived: background `rgba(199, 10, 36, 0.12)`, color `#8e0b21`
- Price (right-aligned): 14px Inter, weight 450, line-height 20px, color `#303030`, flex-shrink 0
- Checkbox (left, optional): 18px square, border-radius 4px, border 2px solid `#8c8c8c`, checked: background `#303030` with white checkmark
- First item in list: border-top-left-radius 12px, border-top-right-radius 12px
- Last item in list: border-bottom-left-radius 12px, border-bottom-right-radius 12px, border-bottom none
- Entire list wrapper: border 1px solid `#e3e3e3`, border-radius 12px, overflow hidden, box-shadow `0px 1px 0px 0px rgba(26, 26, 26, 0.07)`
- On mobile (<490px): thumbnail 32px, title and subtitle stack tighter, price moves below subtitle

---

## 4. Iteration Guide

1. **Gray canvas with white cards is the spatial foundation.** The page background is ALWAYS `#f1f1f1` (gray canvas). Content lives in white cards (`#ffffff`) with `#e3e3e3` borders and shadow-100. Never use a white page background — the gray-white contrast IS Polaris identity. If you see white-on-white, the design is broken.

2. **Brand fill is dark (#303030), not green.** Primary buttons and nav chrome use `#303030` with bevel inset shadows. Shopify Green (`#047b5d`) is reserved for success states, active badges, and positive indicators. It is NOT the button color. If a primary CTA is green, it is wrong.

3. **14px is the default body size, not 16px.** Polaris optimizes for information-dense admin UIs. Body text, table cells, nav links, and descriptions all default to 14px/20px. Use 16px only for prominent descriptions and marketing content. If everything is 16px, the design is too loose.

4. **Use Polaris bevel shadows for tactile depth.** Buttons get multi-layered inset shadows that create a bevel/3D effect: `inset 0 -1px 0 0 rgba(0,0,0,0.2), inset 0 1px 0 0 rgba(255,255,255,0.04)`. Cards get shadow-100: `0px 1px 0px 0px rgba(26, 26, 26, 0.07)`. Never use generic `box-shadow: 0 2px 8px rgba(0,0,0,0.1)` — Polaris shadows are precise and minimal.

5. **Weight 450 for body, 550 for medium, 650 for headings.** Polaris uses non-standard font weights because Inter is a variable font. If you use 400/500/600 you will get subtly wrong rendering. Always use the exact Polaris weights.

6. **Everything snaps to 4px grid.** Spacing uses the Polaris scale: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64. Line-heights are 16, 20, 24, 28, 32, 40, 48. If a measurement is not a multiple of 4, verify it against the token scale.

7. **Cards have 12px border-radius, buttons 8px.** The Polaris radius scale is precise: badges/small elements 4px, inputs/buttons 8px, cards/panels 12px, hero containers 16px, avatars/pills 9999px. Never use 6px or 10px — they are not in the scale.

8. **Status colors have specific semantic roles.** Green (`#047b5d`) = success/active. Red (`#c70a24`) = critical/destructive. Amber (`#ffb800`) = warning. Blue (`#005bd3`) = interactive/link. Each badge and indicator must use its semantic color, not arbitrary decorative color.

9. **The admin top bar is dark (#303030).** The navigation is always a dark surface with light text. This dark-light inversion between nav and content creates the workspace structure. Never render the admin nav on a light background.

10. **Negative letter-spacing on headings.** Text at 20px+ always applies tighter tracking: -0.2px at 20-24px, -0.3px at 30px, -0.54px at 36-40px. Body text stays at 0. This creates visual crispness at headline scale that separates Polaris from generic Inter usage.
