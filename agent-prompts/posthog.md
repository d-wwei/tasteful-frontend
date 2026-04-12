# PostHog -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect PostHog-branded components.
Aesthetic: bold developer analytics -- playful, anti-corporate, data-obsessed with hedgehog personality.

---

## 1. Quick Color Reference

```
Surface dark (app bg):       #1d1f27   Dark Navy -- PostHog's native analytics canvas
Surface elevated:            #2c2e38   Slate -- cards, panels, sidebar on dark
Surface light (marketing):   #f9f9f9   Near White -- clean marketing/docs background
Surface elevated light:      #ffffff   White -- cards on light surfaces
Accent (PostHog Orange):     #f54e00   Brand Orange -- CTAs and high-signal brand moments only
Accent hover:                #e04600   Deeper Orange -- hover/pressed state
Accent light bg:             #fff1eb   Faint Orange -- light-mode selected/hover tint
Text primary (dark):         #eeefe9   Warm Off-White -- body text on dark surfaces
Text primary (light):        #151515   Near Black -- body text on light surfaces
Text secondary (dark):       #9ba0aa   Cool Gray -- descriptions, metadata on dark
Text secondary (light):      #6b7280   Mid Gray -- descriptions, metadata on light
Border (dark):               #3b3d4f   Subtle Slate -- separation on dark
Border (light):              #e5e7eb   Light Gray -- separation on light
Chart Blue:                  #1d8aed   Primary data series
Chart Purple:                #6c3ff2   Secondary data series
Chart Green:                 #42b983   Success/positive metrics
Chart Amber:                 #f1a82c   Warning/attention series
Chart Pink:                  #ff6384   Contrast series
Error:                       #f44336   Red -- distinct from brand orange
Success:                     #77b96c   Muted Green
Warning:                     #f1a82c   Amber
```

---

## 2. Quick Typography Reference

```
Display:   IBM Plex Sans, -apple-system, sans-serif  | 56px | weight 700 | line-height 1.15 | letter-spacing -0.02em
Hero sub:  IBM Plex Sans, -apple-system, sans-serif  | 40px | weight 700 | line-height 1.15 | letter-spacing -0.02em
Section:   IBM Plex Sans, -apple-system, sans-serif  | 32px | weight 600 | line-height 1.25 | letter-spacing normal
Title:     IBM Plex Sans, -apple-system, sans-serif  | 24px | weight 600 | line-height 1.25 | letter-spacing normal
Card head: IBM Plex Sans, -apple-system, sans-serif  | 20px | weight 600 | line-height 1.25 | letter-spacing normal
Body lg:   IBM Plex Sans, -apple-system, sans-serif  | 17px | weight 400 | line-height 1.50 | letter-spacing normal
Body:      IBM Plex Sans, -apple-system, sans-serif  | 15px | weight 400 | line-height 1.50 | letter-spacing normal
Small:     IBM Plex Sans, -apple-system, sans-serif  | 14px | weight 400 | line-height 1.50 | letter-spacing normal
Caption:   IBM Plex Sans, -apple-system, sans-serif  | 13px | weight 400 | line-height 1.50 | letter-spacing normal
Label:     IBM Plex Sans, -apple-system, sans-serif  | 12px | weight 500 | line-height 1.25 | letter-spacing normal
Overline:  IBM Plex Sans, -apple-system, sans-serif  | 11px | weight 600 | line-height 1.25 | letter-spacing 0.08em | text-transform uppercase
Code:      Source Code Pro, JetBrains Mono, monospace | 14px | weight 400 | line-height 1.60 | letter-spacing normal
```

Key rules:
- IBM Plex Sans for everything -- single-family system unifies brand and product
- Semibold (600) for section headings, bold (700) reserved for display/hero only
- Body line-height is 1.50 -- efficient for analytics UIs without feeling cramped
- Monospace only for code blocks, HogQL queries, and technical output
- Use `opacity` for text hierarchy variations rather than adding more gray values

---

## 3. Example Component Prompts

### Hero Section (Marketing)

Create a hero section with PostHog visual identity:
- Background: `#1d1f27` (Dark Navy) -- PostHog heroes are dark-mode native
- Container: max-width 1200px, centered, padding 96px 32px
- Headline: "The open source product analytics suite" at 56px IBM Plex Sans, weight 700, line-height 1.15, letter-spacing -0.02em, color `#eeefe9`
- Subtitle: 17px IBM Plex Sans, weight 400, line-height 1.50, color `#9ba0aa`, max-width 580px, margin-top 16px
- CTA button: background `#f54e00`, color `#ffffff`, 15px IBM Plex Sans weight 500, padding 10px 20px, border-radius 6px, border: none, cursor pointer, transition: background 150ms ease
- CTA hover: background `#e04600`
- Secondary button: background transparent, color `#eeefe9`, 15px weight 500, padding 10px 20px, border-radius 6px, border: 1px solid `#3b3d4f`
- Secondary hover: background `#2c2e38`, border-color `#565869`
- Button row: display flex, gap 12px, margin-top 24px, align-items center
- Decorative element: a subtle radial gradient `radial-gradient(ellipse at 50% 0%, rgba(245,78,0,0.08) 0%, transparent 60%)` behind the hero for depth
- On mobile (<640px): headline 36px, padding 48px 16px, buttons stack full-width, subtitle max-width 100%

### Feature Card

Create a feature card with PostHog visual identity:
- Background: `#2c2e38` (Slate)
- Border: 1px solid `#3b3d4f`
- Border-radius: 8px
- Padding: 24px
- Transition: border-color 150ms ease, box-shadow 150ms ease
- Icon area: 40px square, background `rgba(245,78,0,0.1)`, border-radius 8px, display flex, align-items center, justify-content center, margin-bottom 16px
- Icon: 20px, color `#f54e00`
- Title: 20px IBM Plex Sans, weight 600, line-height 1.25, color `#eeefe9`, margin-bottom 8px
- Description: 15px IBM Plex Sans, weight 400, line-height 1.50, color `#9ba0aa`
- Hover: border-color `#565869`, box-shadow `0 4px 16px rgba(0,0,0,0.20)`
- On mobile (<640px): padding 20px, title 18px

### CTA Button Row

Create a CTA button row with PostHog visual identity:
- Layout: display flex, gap 12px, align-items center
- Primary button (Orange): background `#f54e00`, color `#ffffff`, font 15px IBM Plex Sans weight 500, padding 10px 20px, border-radius 6px, border: none, cursor pointer, transition: background 150ms ease
- Primary hover: background `#e04600`
- Primary active: background `#cc3f00`
- Secondary button (Ghost): background transparent, color `#eeefe9`, font 15px IBM Plex Sans weight 500, padding 10px 20px, border-radius 6px, border: 1px solid `#3b3d4f`, transition: all 150ms ease
- Secondary hover: background `#2c2e38`, border-color `#565869`
- Light-mode primary: same orange, same specs
- Light-mode secondary: background transparent, color `#151515`, border: 1px solid `#e5e7eb`
- Light-mode secondary hover: background `#f0f0f0`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with PostHog visual identity:
- Background: `#1d1f27` (Dark Navy), position sticky, top 0, z-index 100, border-bottom: 1px solid `#3b3d4f`
- Container: max-width 1200px, centered, padding 0 32px, height 56px, display flex, align-items center, justify-content space-between
- Logo: PostHog hedgehog mark + wordmark, height 28px, left-aligned
- Nav links: 14px IBM Plex Sans, weight 500, color `#9ba0aa`, gap 24px, text-decoration none, transition: color 150ms
- Nav link hover: color `#eeefe9`
- Active nav link: color `#eeefe9`, position relative, with `::after` pseudo-element 2px tall, background `#f54e00`, bottom -1px, left 0, right 0
- CTA button (right): background `#f54e00`, color `#ffffff`, 14px weight 500, padding 8px 16px, border-radius 6px
- Light variant: background `#ffffff`, border-bottom 1px solid `#e5e7eb`, nav links color `#6b7280`, hover `#151515`, active `#151515`
- On mobile (<768px): nav links collapse to hamburger menu icon (24px), CTA remains visible

### Data Card / Metric Display

Create a metric display card with PostHog visual identity:
- Background: `#2c2e38` (Slate)
- Border: 1px solid `#3b3d4f`
- Border-radius: 8px
- Padding: 20px
- Overline label: 11px IBM Plex Sans, weight 600, line-height 1.25, letter-spacing 0.08em, text-transform uppercase, color `#6b7280`, margin-bottom 8px
- Metric value: 32px IBM Plex Sans, weight 600, line-height 1.25, color `#eeefe9`
- Trend indicator: display inline-flex, align-items center, gap 4px, margin-left 8px, font-size 13px, weight 500
- Trend up: color `#77b96c`, with upward arrow icon
- Trend down: color `#f44336`, with downward arrow icon
- Metric description: 13px IBM Plex Sans, weight 400, line-height 1.50, color `#6b7280`, margin-top 4px
- Sparkline area: height 40px, margin-top 12px, stroke `#1d8aed`, stroke-width 1.5px, fill `rgba(29,138,237,0.08)`
- On mobile (<640px): metric value 28px, padding 16px

### Dashboard Sidebar

Create a dashboard sidebar with PostHog visual identity:
- Background: `#111318` (Deepest Dark), width 220px, height 100vh, position fixed, top 0, left 0, padding 16px 0, overflow-y auto
- Logo: PostHog hedgehog icon 28px, padding 12px 16px, margin-bottom 8px
- Section label: 11px IBM Plex Sans, weight 600, letter-spacing 0.08em, text-transform uppercase, color `#6b7280`, padding 8px 16px
- Nav item: display flex, align-items center, gap 8px, padding 8px 16px, border-radius 6px (with 4px horizontal margin), font-size 14px, weight 400, color `#9ba0aa`, cursor pointer, transition: all 150ms
- Nav item icon: 18px, opacity 0.7
- Nav item hover: background `#2c2e38`, color `#eeefe9`
- Nav item active: background `rgba(245,78,0,0.1)`, color `#f54e00`, font-weight 500
- Nav item active icon: opacity 1, color `#f54e00`
- Divider: height 1px, background `#3b3d4f`, margin 8px 16px
- On mobile (<768px): sidebar becomes bottom sheet or hamburger overlay

### Analytics Dashboard / Funnel Chart Card

Create an analytics funnel card with PostHog visual identity:
- Container: background `#2c2e38`, border 1px solid `#3b3d4f`, border-radius 8px, padding 24px
- Header row: display flex, justify-content space-between, align-items center, margin-bottom 20px
- Title: 17px IBM Plex Sans, weight 600, color `#eeefe9`
- Date range picker: background `#35374a`, border 1px solid `#3b3d4f`, border-radius 6px, padding 6px 12px, font-size 13px, color `#9ba0aa`, cursor pointer
- Funnel bars container: display flex, flex-direction column, gap 0
- Funnel step row: display flex, align-items center, gap 16px, padding 12px 0, border-bottom 1px solid `#3b3d4f`
- Step number: 20px, weight 600, color `#6b7280`, flex 0 0 28px, text-align center
- Step bar wrapper: flex 1, position relative, height 36px
- Step bar fill: background `#1d8aed`, height 100%, border-radius 4px, min-width 24px, transition: width 350ms cubic-bezier(0.4, 0, 0.2, 1)
- Step bar fill gradient: for visual richness, apply `linear-gradient(90deg, #1d8aed, #36a2eb)`
- Step label: position absolute, left 12px, top 50%, transform translateY(-50%), font-size 13px, weight 500, color `#ffffff`, white-space nowrap
- Conversion rate: flex 0 0 64px, text-align right, font-size 14px, weight 600, color `#eeefe9`
- Drop-off label: font-size 12px, color `#f44336`, weight 500, margin-top 2px
- Overall conversion footer: margin-top 16px, padding-top 16px, border-top 1px solid `#3b3d4f`, display flex, justify-content space-between
- Footer label: 13px, weight 400, color `#6b7280`
- Footer value: 24px, weight 600, color `#77b96c` (for positive) or `#f44336` (for concerning rates)
- Empty state: center-aligned, hedgehog illustration placeholder, 15px text "No funnel data yet", color `#6b7280`, padding 48px
- On mobile (<640px): step labels move below bars, padding 16px

---

## 4. Iteration Guide

1. **Dark mode is the native state.** PostHog's analytics UI lives on `#1d1f27`. Light mode (`#f9f9f9`) is for marketing pages and documentation. If generating an app component, default to dark. If generating a landing page, use light. Never guess -- ask which context.

2. **Orange is scarce and sacred.** `#f54e00` appears only on primary CTA buttons, active sidebar items, and brand logo moments. It is never a surface fill, never a section background, never a decorative gradient. One orange element per viewport is the target density. If you have used orange on more than two elements in one screen, remove some.

3. **Single typeface, weight does the work.** IBM Plex Sans carries the entire brand. Hierarchy comes from weight (400/500/600/700) and size, not from switching font families. Bold (700) is reserved strictly for hero/display headlines. If you catch yourself reaching for Inter, Helvetica, or another sans -- replace it with IBM Plex Sans.

4. **Dense but not cluttered.** PostHog is an analytics product -- screens show lots of data. Use 4px base grid, tight 8px/12px gaps within components, generous 20-24px card padding. The density should feel information-rich without feeling chaotic. White space lives between sections, not within data-heavy cards.

5. **Borders define structure on dark, not shadows.** On dark surfaces, use 1px solid `#3b3d4f` borders for containment. Shadows are nearly invisible on dark backgrounds. Reserve `box-shadow` for dropdowns, tooltips, and overlays that need to float above the surface. Never use shadows as the primary containment strategy for cards.

6. **Chart colors are a curated sequence.** When showing data visualizations, always use the chart palette in order: Blue (`#1d8aed`), Purple (`#6c3ff2`), Orange (`#f54e00`), Green (`#42b983`), Amber (`#f1a82c`), Pink (`#ff6384`). Never randomize chart colors. Never use brand orange as the first/default chart color -- blue leads.

7. **Playful personality in copy, restrained in chrome.** PostHog's anti-corporate voice shows up in microcopy ("Your data. No cap."), hedgehog illustrations, and cheeky empty states. The UI chrome itself is disciplined and tool-like. Do not add rounded corners beyond 8px on app components, emoji in navigation labels, or cartoon-style decorations to functional UI.

8. **Monospace for data, not decoration.** Source Code Pro appears in HogQL query editors, code snippets, and API key displays. Never use monospace for labels, badges, or headings as a "techy" aesthetic choice. PostHog already looks technical from its data density -- monospace decoration is redundant.
