# Nike -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Nike-branded components.
Aesthetic: kinetic retail cathedral -- monochromatic UI where product photography carries all emotional weight.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   White -- clean retail canvas
Surface secondary:    #f5f5f5   Light Gray -- search input, placeholders
Surface hover:        #e5e5e5   Hover Gray -- hover states
Surface dark:         #111111   Nike Black -- hero sections, not pure black
Text primary:        #111111   Nike Black -- main text color
Text secondary:      #707072   Secondary -- metadata, descriptions
Text disabled:       #9e9ea0   Disabled -- inactive elements
Error:               #d30005   Nike Red -- errors, sale badges
Success:             #007d48   Success Green -- confirmation
Link:                #1151ff   Link Blue -- text links
Border:              #cacacb   Border Secondary -- subtle borders
```

---

## 2. Quick Typography Reference

```
Display:     Nike Futura ND, Helvetica, sans-serif       | 96px | weight 400 | line-height 0.90 | uppercase | letter-spacing normal
Section:     Helvetica Now Display Medium, sans-serif     | 32px | weight 500 | line-height 1.10 | letter-spacing normal
Card Title:  Helvetica Now Display Medium, sans-serif     | 24px | weight 500 | line-height 1.15 | letter-spacing normal
Body Large:  Helvetica Now Text, sans-serif               | 20px | weight 400 | line-height 1.40 | letter-spacing normal
Body:        Helvetica Now Text, sans-serif               | 16px | weight 400 | line-height 1.40 | letter-spacing normal
Button:      Helvetica Now Text Medium, sans-serif        | 16px | weight 500 | line-height 1.25 | letter-spacing normal
Caption:     Helvetica Now Text Medium, sans-serif        | 14px | weight 500 | line-height 1.40 | letter-spacing normal
Small:       Helvetica Now Text, sans-serif               | 12px | weight 400 | line-height 1.33 | letter-spacing normal
```

Key rules:
- Nike Futura ND for massive uppercase display headlines ONLY
- Helvetica Now for all other text (heading, body, UI)
- Display line-height of 0.90 -- impossibly tight, typographic shockwave
- No text shadows, no gradients, no decorative type treatments

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Nike visual identity:
- Background: full-bleed athletic photography, edge-to-edge, no border-radius
- Overlay: subtle dark gradient from bottom for text readability
- Container: full-width, padding 64px
- Headline: "JUST DO IT" at 96px Nike Futura ND, weight 400, line-height 0.90, text-transform uppercase, color `#ffffff`, letter-spacing normal
- Subtitle: 20px Helvetica Now Text, weight 400, line-height 1.40, color `#ffffff`, max-width 600px, margin-top 16px
- CTA button: background `#ffffff`, color `#111111`, 16px Helvetica Now Text Medium weight 500, padding 12px 24px, border-radius 30px (pill), border: none
- On mobile (<600px): headline 48px, subtitle 16px, padding 32px 20px

### Feature Card

Create a product card with Nike visual identity:
- Background: `#ffffff`
- Border: none (shadow-free, border-minimal)
- Border-radius: 0px (full-bleed imagery fills edges)
- Image area: full-width, no border-radius, object-fit cover, aspect-ratio 4:5
- Card body: padding 12px 0
- Category label: 14px Helvetica Now Text Medium, weight 500, color `#111111`, text-transform uppercase
- Title: 16px Helvetica Now Text Medium, weight 500, line-height 1.25, color `#111111`
- Price: 16px Helvetica Now Text, weight 400, color `#111111`
- Description: 14px Helvetica Now Text, weight 400, color `#707072`
- On mobile (<600px): card stacks full-width

### CTA Button Row

Create a CTA button row with Nike visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Black Pill): background `#111111`, color `#ffffff`, font 16px Helvetica Now Text Medium weight 500, padding 12px 24px, border-radius 30px, border: none
- Primary hover: background `#28282a`
- Secondary button (White Pill): background `#ffffff`, color `#111111`, padding 12px 24px, border-radius 30px, border: 1px solid `#cacacb`
- Secondary hover: border-color `#111111`
- Text link: color `#111111`, 14px weight 500, text-decoration underline
- On mobile (<600px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Nike visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#e5e5e5`
- Container: max-width 1440px, centered, padding 0 48px, height 60px
- Logo: Nike Swoosh in `#111111`, left-aligned
- Nav links: 16px Helvetica Now Text Medium weight 500, color `#111111`, gap 24px
- Nav link hover: opacity 0.7
- Search: `#f5f5f5` background, border-radius 30px, 14px, padding 8px 16px
- Cart/Profile icons: `#111111`, right-aligned
- On mobile (<960px): hamburger menu, search prominent

### Data Card / Metric Display

Create a performance metric card with Nike visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e5e5e5`
- Border-radius: 8px
- Padding: 24px
- Category: 12px Helvetica Now Text Medium weight 500, text-transform uppercase, color `#707072`, margin-bottom 8px
- Metric value: 32px Helvetica Now Display Medium, weight 500, line-height 1.10, color `#111111`
- Description: 14px Helvetica Now Text, weight 400, color `#707072`, margin-top 8px
- On mobile (<600px): padding 16px

### Category Image Card (Brand-Specific)

Create a category navigation card with Nike visual identity:
- Full-bleed photography filling entire card, no border-radius
- Image: cover, aspect-ratio 3:4
- Overlay: linear-gradient from transparent to rgba(0,0,0,0.4) at bottom
- Category name: position absolute, bottom 24px, left 24px, 24px Helvetica Now Display Medium weight 500, color `#ffffff`
- CTA text: 14px weight 500, color `#ffffff`, text-decoration underline, below category name
- Hover: image scale 1.02, transition 300ms
- Grid layout: 3 columns on desktop, 1 column on mobile

---

## 4. Iteration Guide

1. **The UI is monochromatic.** Black, white, and grey only for interface chrome. Product photography provides all color. If a component introduces a hue to the UI, remove it.

2. **Nike Futura ND for display headlines only.** Massive uppercase at 0.90 line-height. All other text uses Helvetica Now family. If you see Futura on body text or Helvetica on a display headline, fix it.

3. **Full-bleed photography with zero border-radius.** Images fill their containers edge-to-edge. No rounded corners on hero images or product photography. The imagery IS the design.

4. **Pill-shaped buttons (30px radius).** Primary interactive elements are pills. Navigation and secondary buttons may use standard rounding. Never sharp-cornered CTA buttons.

5. **Shadow-free elevation.** Depth comes from grey shifts (`#ffffff` to `#f5f5f5` to `#e5e5e5`), not shadows. If a card has a prominent drop shadow, remove it.

6. **Athletic precision on the 8px grid.** Every measurement snaps to the spacing system. No arbitrary values. The discipline of sport extends to the pixel grid.
