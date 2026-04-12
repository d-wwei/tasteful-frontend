# Superhuman -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Superhuman-branded components.
Aesthetic: precision dark interface — keyboard-first, sub-100ms, purple accent glow on void-black.

---

## 1. Quick Color Reference

```
Surface (deepest bg):    #1B1B1B   Cod Gray — the void emails float above
Surface raised:          #232323   Raised — sidebar panels, email list pane
Surface elevated:        #2C2C2C   Elevated — selected thread, compose window, modals
Surface overlay:         #353535   Overlay — command palette (Cmd+K), dropdowns
Surface highest:         #3E3E3E   Highest — tooltips, toasts, topmost layer

Accent:                  #6C56F0   Superhuman Purple — primary CTA, focused states
Accent hover:            #8270F4   Purple hover — lighter feedback on interaction
Accent subtle:           rgba(108,86,240,0.12)   Selected row background tint
Accent glow:             rgba(108,86,240,0.25)   Focus ring outer glow

Text primary:            #FFFFFF   Pure white — sender names, subjects, headings
Text secondary:          rgba(255,255,255,0.65)  White 65% — email body, preview, timestamps
Text tertiary:           rgba(255,255,255,0.40)  White 40% — placeholders, disabled, metadata

Error:                   #F04438   Error red — failed sends, destructive
Success:                 #32D583   Success green — sent confirm, inbox zero
Warning:                 #F5A623   Warning amber — snooze, remind-me
Info:                    #36A3F7   Info blue — read receipts, links

Border subtle:           rgba(255,255,255,0.06)  Row separators, panel edges
Border default:          rgba(255,255,255,0.10)  Card outlines, input fields
Border strong:           rgba(255,255,255,0.16)  Focused inputs, active panels
```

---

## 2. Quick Typography Reference

```
Display:     -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 36px | weight 600 | line-height 1.20 | letter-spacing -0.02em
Section:     -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 24px | weight 600 | line-height 1.20 | letter-spacing -0.02em
Title:       -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 18px | weight 500 | line-height 1.20 | letter-spacing normal
Body:        -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 15px | weight 400 | line-height 1.50 | letter-spacing normal
Small:       -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 13px | weight 400 | line-height 1.40 | letter-spacing normal
Caption:     -apple-system, BlinkMacSystemFont, system-ui, sans-serif  | 11px | weight 500 | line-height 1.25 | letter-spacing 0.06em
Mono:        'SF Mono', ui-monospace, monospace                        | 12px | weight 500 | line-height 1.25 | letter-spacing 0.02em
```

Key rules:
- System fonts ONLY — zero network requests, zero FOUT, sub-100ms text render
- Weight 500 for interactive labels (unread senders, nav items, buttons)
- Weight 600 for headings only — never 700+ (the app feels sharp, not heavy)
- Monospace exclusively for keyboard shortcut hints (K, E, J, Cmd+K)
- 15px base (not 16px) — optimized for email body readability at dense layout

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Superhuman visual identity:
- Background: `#1B1B1B` (Cod Gray — the void)
- Container: max-width 1400px, centered, padding 96px 48px
- Headline: "The fastest email experience ever made" at 36px system sans, weight 600, line-height 1.20, letter-spacing -0.02em, color `#FFFFFF`
- Subtitle: 15px system sans, weight 400, line-height 1.50, color `rgba(255,255,255,0.65)`, max-width 520px, margin-top 16px
- CTA button: background `#6C56F0`, color `#FFFFFF`, 14px weight 500, padding 10px 20px, border-radius 6px, transition 100ms
- CTA hover: background `#8270F4`, box-shadow `0 0 0 2px #6C56F0, 0 0 8px rgba(108,86,240,0.25)`
- Secondary link: color `rgba(255,255,255,0.65)`, 14px weight 400, text-decoration underline, underline-offset 3px
- Button row gap: 16px, margin-top 32px
- Keyboard hint below CTA: 11px monospace, weight 500, color `rgba(255,255,255,0.40)`, letter-spacing 0.06em, content "Press ⌘K to get started"
- On mobile (<640px): headline 28px, padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Superhuman visual identity:
- Background: `#232323` (raised surface)
- Border: 1px solid `rgba(255,255,255,0.06)`
- Border-radius: 8px
- Padding: 24px
- No box-shadow (elevation via background color, not shadow — Superhuman philosophy)
- Title: 18px system sans, weight 500, line-height 1.20, color `#FFFFFF`, margin-bottom 8px
- Description: 15px system sans, weight 400, line-height 1.50, color `rgba(255,255,255,0.65)`
- Icon area: 32px square, accent `#6C56F0` for active states, `rgba(255,255,255,0.40)` default
- Hover state: background shifts to `#2C2C2C`, border-color `rgba(255,255,255,0.10)`, transition 100ms
- On mobile (<640px): padding 20px, title 16px

### CTA Button Row

Create a CTA button row with Superhuman visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#6C56F0`, color `#FFFFFF`, font 14px system sans weight 500, padding 10px 20px, border-radius 6px, border: none, transition all 100ms ease
- Primary hover: background `#8270F4`
- Primary keyboard-focus: box-shadow `0 0 0 2px #1B1B1B, 0 0 0 4px #6C56F0` (double-ring pattern)
- Secondary button: background `#2C2C2C`, color `#FFFFFF`, font 14px system sans weight 500, padding 10px 20px, border-radius 6px, border 1px solid `rgba(255,255,255,0.10)`
- Secondary hover: background `#353535`, border-color `rgba(255,255,255,0.16)`
- Ghost button: background transparent, color `rgba(255,255,255,0.65)`, padding 10px 16px, border-radius 6px, no border
- Ghost hover: background `rgba(255,255,255,0.06)`, color `#FFFFFF`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Superhuman visual identity:
- Background: `#1B1B1B`, position sticky, top 0, z-index 100, backdrop-filter: none (opaque, no blur — speed over decoration)
- Border-bottom: 1px solid `rgba(255,255,255,0.06)` (barely visible separator)
- Container: max-width 1400px, centered, padding 0 48px, height 48px, display flex, align-items center, justify-content space-between
- Logo: Superhuman wordmark in `#FFFFFF`, left-aligned, 15px weight 600
- Nav links: 13px system sans, weight 500, color `rgba(255,255,255,0.65)`, gap 24px, text-decoration none
- Nav link hover: color `#FFFFFF`, transition 100ms
- Nav link active: color `#FFFFFF`, position relative, after pseudo-element: 2px height, width 100%, background `#6C56F0`, bottom -13px (underline indicator)
- CTA button (right): background `#6C56F0`, color `#FFFFFF`, 13px weight 500, padding 8px 16px, border-radius 6px
- Keyboard hint: hidden on mobile, 11px monospace, color `rgba(255,255,255,0.40)`, content "⌘K"
- On mobile (<640px): height 44px, padding 0 16px, nav links collapse to hamburger icon, CTA remains

### Data Card / Metric Display

Create a metric display card with Superhuman visual identity:
- Background: `#232323` (raised surface)
- Border: 1px solid `rgba(255,255,255,0.06)`
- Border-radius: 8px
- Padding: 24px
- Overline label: 11px system sans, weight 500, line-height 1.25, letter-spacing 0.06em, text-transform uppercase, color `rgba(255,255,255,0.40)`, margin-bottom 8px
- Metric value: 36px system sans, weight 600, line-height 1.20, letter-spacing -0.02em, color `#FFFFFF`
- Metric delta (optional): 13px weight 500, color `#32D583` (positive) or `#F04438` (negative), displayed inline after value with 8px gap
- Metric description: 13px system sans, weight 400, line-height 1.40, color `rgba(255,255,255,0.65)`, margin-top 8px
- On mobile (<640px): metric value 28px, padding 20px

### Email Thread / Inbox Row

Create an inbox row component with Superhuman visual identity:
- Layout: flex, height 44px, align-items center, padding 0 16px, gap 12px, cursor pointer
- Background: transparent (inherits from surface)
- Selected state: background `rgba(108,86,240,0.12)` (accent subtle wash)
- Hover state: background `rgba(255,255,255,0.03)`, transition 50ms (instant feel)
- Border-bottom: 1px solid `rgba(255,255,255,0.06)` (hairline separator)
- Avatar: 24px circle, border-radius 9999px, background `#353535`, flex-shrink 0
- Sender name (unread): 13px system sans, weight 500, color `#FFFFFF`, flex 0 0 160px, overflow hidden, text-overflow ellipsis, white-space nowrap
- Sender name (read): weight 400, color `rgba(255,255,255,0.65)`
- Subject: 13px weight 500 (unread) / 400 (read), color `#FFFFFF` / `rgba(255,255,255,0.65)`, flex 0 0 auto, max-width 300px, overflow hidden, text-overflow ellipsis
- Preview snippet: 13px weight 400, color `rgba(255,255,255,0.40)`, flex 1 1 auto, overflow hidden, text-overflow ellipsis, white-space nowrap, margin-left 4px
- Separator dash: " — " between subject and preview, color `rgba(255,255,255,0.25)`
- Timestamp: 11px weight 400, color `rgba(255,255,255,0.40)`, flex-shrink 0, text-align right, min-width 48px
- Snooze indicator (optional): 11px, color `#F5A623`, content "🕐" or clock icon
- Keyboard navigation focus: outline none, box-shadow `inset 0 0 0 2px #6C56F0` (inset ring — does not shift layout)
- On mobile: sender 120px, hide preview snippet, timestamp abbreviate to "2h" format

---

## 4. Iteration Guide

1. **Dark surfaces define the hierarchy — not shadows.** Superhuman uses five grays (`#1B1B1B` through `#3E3E3E`) where proximity to user = lighter surface. Do NOT reach for drop shadows to create depth. A background color shift of +10 in hex is more Superhuman than any shadow. Only modals and the command palette get actual box-shadow.

2. **System fonts are the speed identity.** Zero Google Fonts, zero custom web fonts, zero `@font-face`. The font stack is `-apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif`. If you see a `<link>` tag loading Inter, Helvetica Neue from CDN, or any custom font, delete it. Speed IS the brand.

3. **Purple accent is surgical.** `#6C56F0` appears on: primary CTA buttons, selected/focused states, active navigation indicators, and keyboard focus rings. It does NOT appear on: backgrounds, section fills, decorative gradients, or body text. Count purple elements on screen — if more than 3, you have overused it.

4. **Keyboard focus gets a purple glow halo.** Every focusable element must show `box-shadow: 0 0 0 2px #1B1B1B, 0 0 0 4px #6C56F0` on `:focus-visible`. The dark gap ring ensures the purple glow reads against both dark and elevated surfaces. This is non-negotiable — keyboard navigation is the product's core identity.

5. **Density over whitespace.** Superhuman is NOT a marketing-site-with-breathing-room. Inbox rows are 44px tall. Padding is tight (12-24px, not 32-48px). Gaps are 8-12px. The information density of a professional tool, not a lifestyle brand. If your component has > 32px padding, question it.

6. **Motion is felt, not seen.** Transitions are 50-150ms with snap easing (`cubic-bezier(0.2, 0, 0, 1)`). Nothing slides in. Nothing bounces. Nothing fades for 300ms. The only spring easing is the inbox zero celebration. Everything else is instantaneous or near-instantaneous.

7. **Monospace is only for keyboard hints.** `SF Mono` or `ui-monospace` appears exclusively in keyboard shortcut badges ("K", "E", "⌘K", "Cmd+Shift+P"). Never for headings, labels, or decorative text. The shortcut hint format: 11px, weight 500, letter-spacing 0.06em, background `#2C2C2C`, padding 2px 6px, border-radius 4px, color `rgba(255,255,255,0.40)`.

8. **Borders are near-invisible.** Use `rgba(255,255,255,0.06)` for most dividers — they should be felt more than seen. `rgba(255,255,255,0.10)` is for card outlines and inputs. `rgba(255,255,255,0.16)` is reserved for focused/active states. If a border is clearly visible at arm's length, it is too strong.

9. **Text hierarchy through opacity, not color.** Primary text is pure `#FFFFFF`. Secondary is `rgba(255,255,255,0.65)`. Tertiary is `rgba(255,255,255,0.40)`. This is Superhuman's explicit dark-theme approach from their design research — opacity-based hierarchy reduces eye strain in low-light environments compared to distinct gray hex values.

10. **Every component must feel like it responds to a keyboard shortcut.** Even if you are building a marketing page, include keyboard hint affordances. A button should look like pressing a key would activate it. A card should look like pressing J/K would navigate to it. The keyboard-first philosophy permeates even visual-only contexts.
