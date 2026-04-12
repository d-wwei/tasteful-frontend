# Apple -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Apple-branded components.
Aesthetic: cinematic product theater with reductive minimalism -- every pixel serves the product.

---

## 1. Quick Color Reference

```
Surface light:        #f5f5f7   Light Gray -- blue-gray tint prevents sterility
Surface dark:         #000000   Pure Black -- immersive hero product showcases
Dark elevated:        #272729   Dark Surface 1 -- cards in dark sections
Button surface:       #fafafc   Button Default -- search/filter backgrounds
Button active:        #ededf2   Button Active -- pressed state
Accent CTA:          #0071e3   Apple Blue -- the ONLY chromatic color, interactive only
Link (light bg):     #0066cc   Link Blue -- inline text links on light
Link (dark bg):      #2997ff   Bright Blue -- links on black sections
Text light bg:       #1d1d1f   Near Black -- primary text, slightly warm
Text secondary:      rgba(0,0,0,0.8)   Black 80% -- slightly softened
Text tertiary:       rgba(0,0,0,0.48)  Black 48% -- disabled, carousel controls
Text on dark:        #ffffff   White -- text on dark backgrounds
Nav glass bg:        rgba(0,0,0,0.8)   Translucent Dark -- with blur
```

---

## 2. Quick Typography Reference

```
Display:     SF Pro Display, Helvetica Neue, sans-serif  | 56px | weight 600 | line-height 1.07 | letter-spacing -0.28px
Section:     SF Pro Display, Helvetica Neue, sans-serif  | 40px | weight 600 | line-height 1.10 | letter-spacing normal
Tile:        SF Pro Display, Helvetica Neue, sans-serif  | 28px | weight 400 | line-height 1.14 | letter-spacing  0.196px
Card Title:  SF Pro Display, Helvetica Neue, sans-serif  | 21px | weight 700 | line-height 1.19 | letter-spacing  0.231px
Body:        SF Pro Text, Helvetica Neue, sans-serif     | 17px | weight 400 | line-height 1.47 | letter-spacing -0.374px
Body Emph:   SF Pro Text, Helvetica Neue, sans-serif     | 17px | weight 600 | line-height 1.24 | letter-spacing -0.374px
Button Lg:   SF Pro Text, Helvetica Neue, sans-serif     | 18px | weight 300 | line-height 1.00 | letter-spacing normal
Button:      SF Pro Text, Helvetica Neue, sans-serif     | 17px | weight 400 | line-height 2.41 | letter-spacing normal
Link:        SF Pro Text, Helvetica Neue, sans-serif     | 14px | weight 400 | line-height 1.43 | letter-spacing -0.224px
Caption:     SF Pro Text, Helvetica Neue, sans-serif     | 14px | weight 400 | line-height 1.29 | letter-spacing -0.224px
Nav:         SF Pro Text, Helvetica Neue, sans-serif     | 12px | weight 400 | line-height 1.33 | letter-spacing -0.12px
Nano:        SF Pro Text, Helvetica Neue, sans-serif     | 10px | weight 400 | line-height 1.47 | letter-spacing -0.08px
```

Key rules:
- Optical sizing boundary: SF Pro Display at 20px+, SF Pro Text below 20px
- Negative letter-spacing at ALL sizes: -0.28px at 56px, -0.374px at 17px, -0.224px at 14px
- Extreme line-height range: 1.07 (headlines) to 2.41 (some buttons)
- Weight restraint: 300-700 range, most text at 400 and 600

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Apple visual identity:
- Background: `#000000` (pure black for immersive product showcase)
- Container: max-width 980px, centered, padding 100px 20px, text-align center
- Headline: "iPhone 16 Pro" at 56px SF Pro Display, weight 600, line-height 1.07, letter-spacing -0.28px, color `#ffffff`
- Subtitle: 21px SF Pro Display, weight 400, line-height 1.19, letter-spacing 0.231px, color `#ffffff`, margin-top 12px
- CTA row: flex, gap 20px, justify-content center, margin-top 20px
- "Learn more" link: color `#2997ff`, 14px SF Pro Text weight 400, letter-spacing -0.224px, text with right-arrow chevron, border: 1px solid `#2997ff`, border-radius 980px, padding 8px 20px
- "Buy" button: background `#0071e3`, color `#ffffff`, 17px SF Pro Text weight 400, padding 8px 15px, border-radius 8px
- Product image: centered, full-width within container, on solid black field
- On mobile (<480px): headline 40px, subtitle 17px, CTAs stack, padding 60px 20px

### Feature Card

Create a product card with Apple visual identity:
- Background: `#f5f5f7` (light gray)
- Border: none (Apple almost never uses visible borders)
- Border-radius: 8px
- Padding: 40px 32px, text-align center
- Product image: centered, 60-70% of card height, on solid background
- Title: 28px SF Pro Display, weight 400, line-height 1.14, letter-spacing 0.196px, color `#1d1d1f`, margin-top 24px
- Description: 14px SF Pro Text, weight 400, line-height 1.43, letter-spacing -0.224px, color `rgba(0,0,0,0.8)`, margin-top 8px
- Link pair: "Learn more" and "Shop" at 14px, color `#0066cc`, letter-spacing -0.224px, gap 20px, margin-top 12px
- On mobile (<480px): padding 24px, title 21px

### CTA Button Row

Create a CTA button row with Apple visual identity:
- Layout: flex, gap 20px, align-items center, justify-content center
- Primary button (Blue): background `#0071e3`, color `#ffffff`, font 17px SF Pro Text weight 400, padding 8px 15px, border-radius 8px, border: 1px solid transparent, cursor pointer, transition: all 250ms
- Primary hover: background brightens slightly
- Primary focus: outline 2px solid `#0071e3`, outline-offset 2px
- Pill link (Learn More): background transparent, color `#0066cc` (light bg) or `#2997ff` (dark bg), 14px weight 400, letter-spacing -0.224px, border: 1px solid currentColor, border-radius 980px, padding 8px 20px
- Pill hover: text-decoration underline
- Dark button: background `#1d1d1f`, color `#ffffff`, same padding, border-radius 8px
- On mobile (<480px): flex-direction column, buttons full-width, gap 12px

### Navigation Bar

Create the Apple navigation bar:
- Background: `rgba(0,0,0,0.8)` with `backdrop-filter: saturate(180%) blur(20px)`
- Position: sticky, top 0, z-index 100
- Height: 48px (compact)
- Container: max-width 980px, centered, display flex, align-items center, justify-content space-between
- Logo: Apple logomark SVG in `#ffffff`, 17x48px viewport
- Nav links: 12px SF Pro Text, weight 400, color `#ffffff`, gap 24px, text-decoration none, letter-spacing -0.12px
- Nav link hover: opacity 0.8, transition 150ms
- Right icons: search and bag icons in `#ffffff`
- On mobile (<834px): nav collapses to hamburger with full-screen overlay menu

### Data Card / Metric Display

Create a product spec card with Apple visual identity:
- Background: `#f5f5f7`
- Border: none
- Border-radius: 12px
- Padding: 32px
- Product name: 21px SF Pro Display, weight 700, line-height 1.19, letter-spacing 0.231px, color `#1d1d1f`
- Spec label: 12px SF Pro Text, weight 600, line-height 1.33, letter-spacing -0.12px, color `rgba(0,0,0,0.48)`, margin-top 16px
- Spec value: 17px SF Pro Text, weight 600, line-height 1.24, letter-spacing -0.374px, color `#1d1d1f`
- Comparison divider: 1px solid `rgba(0,0,0,0.04)`, margin 16px 0
- On mobile (<480px): padding 24px

### Dark Product Showcase (Brand-Specific)

Create a dark product showcase section with Apple visual identity:
- Background: `#000000`, full-width section
- Section padding: 100px 20px, text-align center
- Product name: 56px SF Pro Display, weight 600, line-height 1.07, letter-spacing -0.28px, color `#ffffff`
- Tagline: 28px SF Pro Display, weight 400, line-height 1.14, letter-spacing 0.196px, color `#ffffff`, margin-top 8px
- Product image: centered, maximum visual impact, on solid black — no backgrounds, no context
- CTA pair: margin-top 24px, flex, gap 20px, justify-content center
- "Learn more" pill: transparent bg, color `#2997ff`, border: 1px solid `#2997ff`, border-radius 980px, padding 8px 20px, 14px SF Pro Text
- "Buy" button: bg `#0071e3`, color `#ffffff`, border-radius 8px, padding 8px 15px, 17px SF Pro Text
- Followed by: `#f5f5f7` light section for product details (cinematic rhythm)
- On mobile (<480px): product name 40px, tagline 21px, padding 60px 20px

---

## 4. Iteration Guide

1. **Every interactive element gets Apple Blue (`#0071e3`).** No other accent colors anywhere. The entire chromatic budget is spent on this single blue. If another hue appears on a clickable element, remove it.

2. **Alternate dark and light sections for cinematic rhythm.** Black (`#000000`) for immersive product showcases. Light gray (`#f5f5f7`) for informational content. Each section change is a new scene. Never use gradients or textures.

3. **Respect the optical sizing boundary.** SF Pro Display at 20px and above. SF Pro Text at 19px and below. The font literally changes its DNA based on size. Mixing them at the wrong sizes breaks the optical optimization.

4. **Negative letter-spacing at ALL sizes.** Apple tracks tight universally: -0.28px at 56px, -0.374px at 17px, -0.224px at 14px, -0.12px at 12px. If text looks loose, check the letter-spacing.

5. **The navigation glass effect is non-negotiable.** `background: rgba(0,0,0,0.8)` + `backdrop-filter: saturate(180%) blur(20px)`. This translucent dark navigation that floats above content defines the Apple web experience. Never make it opaque.

6. **Products on solid color fields.** No backgrounds, no context, just the object as sculpture. The product photograph IS the design. UI recedes until invisible.
