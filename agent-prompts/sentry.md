# Sentry -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Sentry-branded components.
Aesthetic: data-dense monitoring dashboard with restrained purple accent.
Design system: S.C.R.A.P.S. (Standardized Collection of Reusable Assets & Patterns for Sentry).

---

## 1. Quick Color Reference

```
Surface (page bg):       #f9f8ff    Faint purple-tinted off-white (light dashboard)
Card surface:            #ffffff    Clean white for data containers and panels
Recessed surface:        #ececf1    Inputs, code blocks -- tactile depth
Dark surface:            #1F1633    Hero sections, dark mode base (deep aubergine)
Accent (Sentry Purple):  #6a5fc1    Links, buttons, active states -- THE brand color
Accent hover:            #8277cf    Lighter purple for hover/lift
Accent wash:             rgba(106,95,193,0.08)  Selected rows, active tab backgrounds
Text primary:            #2B1D38    Deep plum-black (gray500)
Text secondary:          #776589    Muted purple-gray for labels (gray400)
Text tertiary:           #9386A0    Softer purple-gray for metadata (gray300)
Text on dark:            #E7E1EC    Pale lavender on dark surfaces (gray100)
Border:                  #cfcfdb    Default border
Border light:            #ececf1    Table rows, card dividers
Error (fatal/error):     #e1567c    Pink-red for critical issues
Warning:                 #f4834f    Coral-orange for warnings
Info:                    #f2b712    Gold-yellow for informational events
Success (resolved):      #19ab27    Green for healthy/resolved
Debug:                   #0099e0    Blue for debug-level events
```

---

## 2. Quick Typography Reference

```
Display:     Rubik, -apple-system, sans-serif   | 40px | weight 700 | line-height 1.20
Section:     Rubik, -apple-system, sans-serif   | 32px | weight 700 | line-height 1.20
Title:       Rubik, -apple-system, sans-serif   | 24px | weight 700 | line-height 1.20
Subtitle:    Rubik, -apple-system, sans-serif   | 20px | weight 500 | line-height 1.30
Body:        Rubik, -apple-system, sans-serif   | 16px | weight 400 | line-height 1.50
Caption:     Rubik, -apple-system, sans-serif   | 14px | weight 400 | line-height 1.43
Small:       Rubik, -apple-system, sans-serif   | 12px | weight 500 | line-height 1.25
Code:        IBM Plex Mono, Consolas, monospace  | 13px | weight 400 | line-height 1.65
```

Key rules:
- Rubik for ALL text -- Sentry's brand typeface (slightly squared with rounded corners)
- IBM Plex Mono for ALL code, stack traces, and error details
- Headings use weight 700, body uses 400, UI labels use 500
- Code line-height is generous (1.65) for stack trace readability
- Load Rubik via Google Fonts: `family=Rubik:wght@400;500;700`

---

## 3. Error Severity Color System

Sentry's severity palette is load-bearing UI -- not decoration. Each level has a foreground and a subtle wash background:

```
Fatal/Error:   #e1567c  foreground  |  rgba(225,86,124,0.12)  wash  -- Issue list, error badges
Warning:       #f4834f  foreground  |  rgba(244,131,79,0.12)  wash  -- Warning-level events
Info:          #f2b712  foreground  |  rgba(242,183,18,0.12)  wash  -- Informational events
Debug:         #0099e0  foreground  |  rgba(0,153,224,0.12)   wash  -- Debug trace events
Resolved:      #19ab27  foreground  |  rgba(25,171,39,0.12)   wash  -- Resolved issues, healthy
```

Rules:
- Severity colors appear ONLY on severity indicators: level badges, sparklines, chart segments, status dots
- Never use severity colors for generic decoration, backgrounds, or branding
- Error pink (#e1567c) is NOT a brand accent -- it is a functional signal color
- In charts and graphs, map severity colors to their corresponding data series

---

## 4. Example Component Prompts

### Hero Section

Create a hero section with Sentry visual identity:
- Background: `#1F1633` (deep aubergine dark surface)
- Container: max-width 1200px, centered, padding 96px 64px
- Headline: 40px Rubik, weight 700, line-height 1.20, color `#ffffff`
- Subtitle: 20px Rubik, weight 400, line-height 1.50, color `#C6BECF` (gray200), max-width 600px, margin-top 16px
- CTA button: background `#6a5fc1`, color `#ffffff`, 16px Rubik weight 500, padding 12px 28px, border-radius 2em (pill), box-shadow: none at rest
- CTA hover: background `#8277cf`, transform translateY(-1px) -- SCRAPS tactile lift
- Secondary button: background transparent, border 1px solid `#6a5fc1`, color `#6a5fc1`, same padding and radius
- Button row: flex, gap 12px, margin-top 32px
- On mobile (<640px): headline 28px, subtitle 17px, padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Sentry visual identity:
- Background: `#ffffff` (card surface)
- Border: 1px solid `#ececf1` (border-light)
- Border-radius: 8px
- Padding: 24px
- Box-shadow: `0 1px 4px rgba(43,29,56,0.08)` (level-1 at rest)
- Hover: box-shadow `0 4px 16px rgba(43,29,56,0.12)` (level-2 lift), transition 200ms
- Title: 20px Rubik, weight 700, line-height 1.20, color `#2B1D38`
- Description: 14px Rubik, weight 400, line-height 1.50, color `#776589`
- Icon area: 40px square, background `rgba(106,95,193,0.08)`, border-radius 8px, icon in `#6a5fc1`
- On mobile (<640px): padding 20px, title 18px

### CTA Button Row

Create a CTA button row with Sentry visual identity:
- Layout: flex, gap 12px, align-items center
- Primary (Pill): background `#6a5fc1`, color `#ffffff`, 16px Rubik weight 500, padding 12px 28px, border-radius 2em, border none, cursor pointer, transition all 200ms
- Primary hover: background `#8277cf`, transform translateY(-1px) -- tactile lift
- Primary active: transform translateY(0) -- tactile press
- Secondary (Outline): background transparent, color `#6a5fc1`, border 1px solid `#6a5fc1`, padding 12px 28px, border-radius 2em
- Secondary hover: background `rgba(106,95,193,0.08)`
- Quiet variant: background transparent, color `#6a5fc1`, border none, padding 12px 16px, text-decoration underline on hover
- On mobile (<640px): flex-direction column, buttons full-width, text-align center

### Navigation Bar

Create a navigation bar with Sentry visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#ececf1`
- Container: max-width 1200px, centered, padding 0 24px, height 56px, display flex, align-items center
- Logo: Sentry wordmark in `#2B1D38`, left-aligned
- Nav links: 14px Rubik weight 500, color `#776589`, gap 24px, text-decoration none
- Nav link hover: color `#2B1D38`, transition 150ms
- Active nav link: color `#6a5fc1`, border-bottom 2px solid `#6a5fc1`, padding-bottom 2px
- CTA button (right): background `#6a5fc1`, color white, 14px weight 500, padding 8px 20px, border-radius 2em
- On mobile (<768px): nav links collapse to hamburger, CTA remains visible
- Dark variant: background `#1F1633`, border-bottom 1px solid rgba(255,255,255,0.1), links color `#C6BECF`

### Issue List / Data Table

Create an issue list table with Sentry visual identity:
- Container: background `#ffffff`, border 1px solid `#ececf1`, border-radius 8px, overflow hidden
- Table header: background `#f9f8ff`, padding 12px 16px, font 12px Rubik weight 500, color `#9386A0`, text-transform uppercase, letter-spacing 0.5px, border-bottom 1px solid `#ececf1`
- Table row: padding 12px 16px, border-bottom 1px solid `#ececf1`, transition background 100ms
- Row hover: background `rgba(106,95,193,0.04)`
- Issue title: 14px Rubik weight 500, color `#2B1D38`, cursor pointer
- Issue title hover: color `#6a5fc1`
- Issue metadata: 12px Rubik weight 400, color `#9386A0` -- project name, first/last seen
- Error count badge: 12px Rubik weight 500, color `#e1567c`, background `rgba(225,86,124,0.12)`, padding 2px 8px, border-radius 3px
- Severity dot: 8px circle, filled with severity color, margin-right 8px, inline with title
- Assignee avatar: 24px circle, border 2px solid `#ffffff`, margin-left auto
- Graph sparkline: 60px wide, 24px tall, stroke `#6a5fc1`, stroke-width 1.5px, fill none

### Error Stack Trace Panel (Brand-Specific)

Create an error stack trace panel with Sentry visual identity:
- Outer container: background `#ffffff`, border 1px solid `#ececf1`, border-radius 8px, overflow hidden
- Panel header: background `#f9f8ff`, padding 16px 20px, display flex, align-items center, justify-content space-between, border-bottom 1px solid `#ececf1`
- Error title: 16px Rubik weight 700, color `#2B1D38`
- Error type badge: 12px Rubik weight 500, color `#e1567c`, background `rgba(225,86,124,0.12)`, padding 2px 10px, border-radius 3px
- Error message: 14px IBM Plex Mono, weight 400, color `#776589`, padding 16px 20px, background `#ececf1` (recessed surface), border-bottom 1px solid `#cfcfdb`
- Stack frame list: padding 0, list-style none
- Stack frame (collapsed): padding 10px 20px, border-bottom 1px solid `#ececf1`, cursor pointer, display flex, align-items baseline, gap 8px
- Frame function name: 13px IBM Plex Mono weight 500, color `#2B1D38`
- Frame file path: 13px IBM Plex Mono weight 400, color `#9386A0`, flex 1, text-align right, overflow hidden, text-overflow ellipsis
- Frame line number: 12px IBM Plex Mono weight 400, color `#6a5fc1`, white-space nowrap
- Stack frame (expanded): background `#1F1633` (dark surface), padding 0
- Code context: 13px IBM Plex Mono, line-height 1.65, color `#E7E1EC`, padding 0
- Line numbers gutter: 48px wide, background `rgba(0,0,0,0.2)`, color `#9386A0`, text-align right, padding-right 12px, user-select none
- Active line (error line): background `rgba(225,86,124,0.20)`, border-left 3px solid `#e1567c`
- Context lines: background transparent
- Frame app badge (in-app vs library): 10px Rubik weight 500, uppercase, letter-spacing 0.5px, color `#19ab27` for in-app frames, color `#9386A0` for library frames
- Collapse/expand icon: 12px, color `#9386A0`, rotates 90deg when expanded, transition transform 150ms
- Raw stack trace toggle: 12px Rubik weight 500, color `#6a5fc1`, cursor pointer, float right in header

---

## 5. Iteration Guide

1. **Light dashboard is the native surface.** Sentry's product UI uses `#f9f8ff` as the page background with white `#ffffff` cards. Dark surfaces (`#1F1633`) appear in hero sections, code blocks, and expanded stack frames -- not as the default. Do not build an all-dark dashboard unless specifically requested.

2. **Purple is strictly for interactivity, never for decoration.** `#6a5fc1` appears on clickable links, active tabs, selected states, CTA buttons, and focus indicators. It never fills large surfaces, card backgrounds, or decorative blocks. If more than 10% of visible pixels are purple, something is wrong.

3. **Severity colors are functional signals, not brand accents.** The error pink (#e1567c), warning orange (#f4834f), info yellow (#f2b712), and success green (#19ab27) exist solely to communicate severity levels. Never repurpose them for decoration, CTAs, or non-severity UI.

4. **All neutrals carry a purple undertone.** Sentry's gray scale runs from `#E7E1EC` (gray100) through `#2B1D38` (gray500), each with a subtle lavender-plum tint. If a generated component introduces a cool blue-gray like `#6b7280`, replace it with `#9386A0` (gray300) or `#776589` (gray400).

5. **Stack traces and code blocks use recessed depth.** Following SCRAPS tactile principles, code containers use `#ececf1` recessed backgrounds (light) or `#1F1633` dark backgrounds. Inputs appear "pushed into" the page surface. Buttons "lift" on hover with `translateY(-1px)`.

6. **Data density is a feature, not a flaw.** Sentry's UI intentionally packs information -- event counts, timestamps, assignees, sparklines, severity dots -- into compact rows. Do not add excessive whitespace to issue lists or data tables. Use 12-14px text sizes and 10-16px vertical padding for rows.

7. **Pill-shaped buttons for primary CTAs.** Sentry's SCRAPS system uses `border-radius: 2em` for primary and secondary buttons. Standard UI elements (inputs, cards, panels) use `6px` or `8px` radius. Never mix pill radius on non-button elements.

8. **IBM Plex Mono for everything code.** Stack traces, error messages, file paths, line numbers, code snippets -- all use IBM Plex Mono at 13px. Rubik handles all non-code text. Never use Rubik for code or Plex Mono for UI labels.

9. **Charts follow severity color mapping.** When displaying error data in charts, map Fatal/Error to pink (#e1567c), Warning to orange (#f4834f), Info to yellow (#f2b712), and healthy/resolved to green (#19ab27). Purple (#6a5fc1) is for aggregate or non-severity series.

10. **Focus states use purple glow.** Focused inputs and interactive elements get a `0 0 15px rgba(106,95,193,0.20)` shadow -- the SCRAPS signature focus ring. Never use browser-default blue outlines.
