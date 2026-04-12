# Pinterest -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Pinterest-branded components.
Aesthetic: warm visual discovery -- clean white canvas, restrained red accent, soft rounded geometry, content-first masonry grid.
Design system: Gestalt (gestalt.pinterest.systems).

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   Pure white -- content is the color
Surface secondary:    #f9f9f9   Off-white -- card backgrounds on white
Surface tertiary:     #f1f1f1   Search bar, input fields
Accent (Pinterest Red): #e60023   Save button and primary CTAs only
Accent hover:         #cc0000   Darkened red for hover/press
Accent light:         #ffe0e0   Red wash for selected/active states
Text primary:         #111111   Near-black -- Gestalt standard, NOT #333 or #000
Text secondary:       #767676   Metadata, timestamps, descriptions
Text link:            #0074e8   Hyperlinks, secondary interactive elements
Border:               #cdcdcd   Card borders, separators
Border light:         #e9e9e9   Subtle dividers
Error:                #e60023   Same as brand red -- red = attention
Success:              #008753   Matchacado green
Warning:              #bd5b00   Firetini orange
Info:                 #0074e8   Skycicle blue
```

---

## 2. Quick Typography Reference

```
Display:     Pinterest Sans, -apple-system, sans-serif  | 36px | weight 700 | line-height 1.2
Heading:     Pinterest Sans, -apple-system, sans-serif  | 28px | weight 700 | line-height 1.2
Subheading:  Pinterest Sans, -apple-system, sans-serif  | 20px | weight 600 | line-height 1.3
Body:        Pinterest Sans, -apple-system, sans-serif  | 16px | weight 400 | line-height 1.4
Caption:     Pinterest Sans, -apple-system, sans-serif  | 14px | weight 400 | line-height 1.4
Small:       Pinterest Sans, -apple-system, sans-serif  | 12px | weight 400 | line-height 1.4
```

Key rules:
- Pinterest Sans is a custom geometric sans-serif by Grilli Type -- warm, rounded, forward-leaning
- Fallback stack: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif
- Only three weights in the system: 400 (body), 600 (subheadings/emphasis), 700 (headings/display)
- Gestalt caps at 36px for display -- no 48px or 64px super-display sizes
- Type scale is tightly controlled: 12, 14, 16, 20, 28, 36px -- no in-between values

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Pinterest visual identity:
- Background: `#ffffff` (pure white canvas)
- Container: max-width 1200px, centered, padding 80px 32px
- Headline: 36px Pinterest Sans, weight 700, line-height 1.2, color `#111111`
- Subtitle: 20px, weight 400, line-height 1.4, color `#767676`, max-width 560px, margin-top 12px
- CTA button (Save-style): background `#e60023`, color `#ffffff`, 16px weight 600, padding 12px 24px, border-radius 999px (pill shape), min-height 48px
- Secondary button: background `#f1f1f1`, color `#111111`, 16px weight 600, padding 12px 24px, border-radius 999px
- Button row gap: 12px, margin-top 24px
- Hero image area: masonry preview grid of 3-5 sample pins, border-radius 16px each, behind or beside text
- On mobile (<576px): headline 28px, single column, padding 48px 16px, buttons stack full-width

### Feature Card

Create a feature card with Pinterest visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e9e9e9`
- Border-radius: 16px (standard Gestalt rounding)
- Padding: 24px
- Box-shadow: none at rest; on hover: `0 2px 8px rgba(0,0,0,0.06)` with smooth 200ms transition
- Title: 20px, weight 600, line-height 1.3, color `#111111`, margin-bottom 8px
- Description: 16px, weight 400, line-height 1.4, color `#767676`
- Icon area: 40px circle, background `#f1f1f1`, centered icon in `#111111`, margin-bottom 16px
- On mobile (<576px): padding 16px, title 16px weight 600

### CTA Button Row

Create a CTA button row with Pinterest visual identity:
- Layout: flex, gap 12px, align-items center
- Primary (Pinterest Red pill): background `#e60023`, color `#ffffff`, font 16px Pinterest Sans weight 600, padding 12px 24px, border-radius 999px, border: none, min-height 48px, cursor pointer, transition: background 200ms ease
- Primary hover: background `#cc0000`
- Secondary (Gray pill): background `#f1f1f1`, color `#111111`, 16px weight 600, padding 12px 24px, border-radius 999px, border: none
- Secondary hover: background `#e9e9e9`
- Tertiary (Text button): background transparent, color `#111111`, 16px weight 600, padding 12px 16px, text-decoration: none
- Tertiary hover: background `#f1f1f1`, border-radius 8px
- Disabled state: opacity 0.4, cursor not-allowed
- On mobile (<576px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Pinterest visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 50, border-bottom: 1px solid `#e9e9e9`
- Height: 56px, max-width 100%, padding 0 16px
- Layout: flex, align-items center, justify-content space-between
- Logo: Pinterest wordmark or icon in `#e60023`, left-aligned, height 24px
- Search bar (center): flex-grow, background `#f1f1f1`, border-radius 999px, padding 8px 16px, font 16px color `#767676` placeholder text, focus: border 2px solid `#0074e8`, background `#ffffff`
- Nav icons (right): 24px icons in `#767676`, gap 16px, hover color `#111111`
- Notification badge: 8px circle, background `#e60023`, positioned top-right on bell icon
- On mobile (<576px): search bar collapses to icon, bottom tab bar replaces nav icons

### Data Card / Metric Display

Create a metric card with Pinterest visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e9e9e9`
- Border-radius: 16px
- Padding: 24px
- Metric value: 28px weight 700, color `#111111`
- Label: 14px weight 400, color `#767676`, margin-bottom 4px (above metric)
- Trend indicator: 14px weight 600, color `#008753` (up) or `#e60023` (down), with small arrow icon
- Sparkline or mini chart: 48px height, stroke `#e60023` at 2px, fill none
- On mobile (<576px): padding 16px, metric 20px weight 700

### Pin Card / Masonry Grid Item

Create a Pin card for masonry layout with Pinterest visual identity:
- **Container**: width 236px (desktop standard), variable height based on image aspect ratio, border-radius 16px, overflow hidden, background `#ffffff`, cursor pointer
- **Image area**: width 100%, aspect ratio varies (2:3 typical), object-fit cover, border-radius 16px (if standalone) or top-only if with text below
- **Image overlay on hover**: semi-transparent darkened overlay `rgba(0,0,0,0.4)`, transition opacity 200ms, reveals action buttons
- **Save button (on hover)**: positioned top-right over image, 12px from edges, background `#e60023`, color `#ffffff`, font 16px weight 600, padding 8px 16px, border-radius 999px, text "Save"
- **More options (on hover)**: bottom-right, 32px circle, background `rgba(255,255,255,0.9)`, icon `#111111`, 24px
- **Board selector (on hover)**: top-left, background `rgba(255,255,255,0.9)`, border-radius 8px, padding 4px 8px, font 14px weight 600 color `#111111`, dropdown arrow
- **Text area (below image)**: padding 8px 4px
  - Pin title: 14px weight 600, line-height 1.3, color `#111111`, max 2 lines with ellipsis overflow
  - Source/attribution: 12px weight 400, color `#767676`, with source favicon 16px circle
  - Pinner avatar: 24px circle, margin-right 4px, inline with attribution
- **Masonry grid**: CSS columns or absolute positioning, gutter 16px, responsive column count (2 on mobile, 3-4 tablet, 5-7 desktop)
- **Loading skeleton**: border-radius 16px, background `#f1f1f1`, shimmer animation 1.5s infinite
- On mobile: 2 columns, gutter 8px, no hover actions (tap to open, long-press for save)

---

## 4. Iteration Guide

1. **White is the canvas -- content is the color.** The page background is always `#ffffff`. Pinterest's visual identity comes from the user-generated imagery in the masonry grid, not from colored surfaces. Never add decorative background colors to the page chrome.

2. **Pinterest Red is for Save buttons and critical CTAs only.** `#e60023` appears on the Save button, primary action buttons, and error states. It should never fill backgrounds, cards, or decorative elements. If more than two red elements are visible simultaneously, you have used too much.

3. **Pill-shaped buttons for primary actions.** Pinterest's signature button shape is border-radius 999px (full pill). All primary CTAs, the Save button, and prominent secondary buttons use pill shape. Only tertiary/text buttons and card containers use smaller radii.

4. **16px rounded corners are the signature geometry.** Pin cards, modals, sheets, and content containers use border-radius 16px. This soft rounding is central to the warm, approachable feel. Never use sharp corners (< 8px) on content containers.

5. **The type scale caps at 36px.** Pinterest's Gestalt system is deliberately restrained -- no 48px+ display sizes. This keeps the focus on visual content rather than typographic drama. If you need hierarchy, use weight (700 vs 400) not size.

6. **Masonry layout is the brand signature.** The staggered, variable-height grid of pins is Pinterest's most recognizable UI pattern. Implement with CSS columns or absolute positioning, 16px gutter, responsive column count. Each pin has its own natural aspect ratio -- never crop to uniform height.

7. **Hover reveals, not persistent chrome.** Pin cards show action buttons (Save, More, Board selector) only on hover. At rest, the pin is just the image with minimal text. This keeps the grid visually clean and lets imagery breathe.

8. **Text color is #111111, not #333.** Gestalt uses near-black `#111111` for primary text -- darker and more definitive than the common `#333333`. Secondary text is `#767676`. Never use pure `#000000`.

9. **4px spacing grid.** Gestalt's base unit is 4px, not 8px. All spacing values are multiples of 4. Common values: 4, 8, 12, 16, 24, 32, 48, 64px.

10. **Shadows appear on hover, not at rest.** Pin cards sit flat on the white canvas with no shadow by default. On hover, a subtle `0 2px 8px rgba(0,0,0,0.06)` shadow lifts the card. This hover-reveal elevation is core to the Pinterest interaction model.
