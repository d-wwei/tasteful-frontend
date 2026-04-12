# Tesla -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Tesla-branded components.
Aesthetic: radical subtraction -- full-viewport cinematic photography with near-zero UI chrome.

Every component exists to FRAME photography. The image is the design. UI elements are transparent scaffolding.

---

## 1. Quick Color Reference

```
Surface (page bg):       #ffffff    Pure white canvas
Surface dark:            #000000    Cinematic black sections
Surface section:         #f4f4f4    Subtle differentiation
Nav glass:               rgba(255,255,255,0.72)   Frosted backdrop
Accent (Tesla Blue):     #3e6ae1    SOLE chromatic color -- primary CTA only
Accent hover:            #3457b8    Darker blue on hover
Text primary:            #171a20    Near-black with blue undertone
Text secondary:          #5c5e62    Medium gray body copy
Text tertiary:           #393c41    Sub-nav, menu items
Text on dark:            #ffffff    White over photography/black
Text on dark secondary:  #ababab    Muted white on dark
Border:                  #d0d1d2    Specs dividers, option outlines
Border subtle:           #e8e8e8    Ghost button borders
```

---

## 2. Quick Typography Reference

```
Hero:       "Universal Sans Display", "Gotham SSm A", "Gotham SSm B", Helvetica, Arial, sans-serif  | 64px | weight 300 | line-height 1.10 | letter-spacing -0.5px
Display:    "Universal Sans Display", "Gotham SSm A", "Gotham SSm B", Helvetica, Arial, sans-serif  | 40px | weight 300 | line-height 1.20
Title:      "Universal Sans Display", "Gotham SSm A", "Gotham SSm B", Helvetica, Arial, sans-serif  | 24px | weight 400 | line-height 1.20
Body:       "Universal Sans Text", "Gotham SSm A", "Gotham SSm B", Helvetica, Arial, sans-serif     | 17px | weight 400 | line-height 1.50
Caption:    "Universal Sans Text", "Gotham SSm A", "Gotham SSm B", Helvetica, Arial, sans-serif     | 14px | weight 400 | line-height 1.43
```

Key rules:
- Weight 300 (light) for ALL large headlines -- this is the Tesla signature
- Weight 500 is the MAXIMUM weight used anywhere (CTA buttons, nav)
- Never use 600, 700, or bold -- Tesla headings feel airy, not assertive
- 17px body text, not 16px
- Negative letter-spacing (-0.5px) on hero headlines

---

## 3. Example Component Prompts

### Hero Section (Full-Bleed Photography)

Create a hero section with Tesla visual identity:
- Layout: FULL VIEWPORT height (100vh), width 100%, no max-width
- Background: full-bleed photograph, `background-size: cover`, `background-position: center`
- Dark overlay: `linear-gradient(to bottom, rgba(0,0,0,0.1) 0%, rgba(0,0,0,0.4) 100%)` over imagery
- Content positioned at bottom center, padding-bottom 120px, text-align center
- Vehicle name: 64px, weight 300, line-height 1.10, letter-spacing -0.5px, color `#ffffff`, text-shadow `0 1px 4px rgba(0,0,0,0.3)`
- Tagline: 17px, weight 400, line-height 1.50, color `#ffffff`, opacity 0.85, margin-top 8px
- CTA row: flex, gap 24px, justify-content center, margin-top 24px
- Primary CTA: background `#3e6ae1`, color `#ffffff`, 14px weight 500, padding 8px 56px, border-radius 4px, border none, letter-spacing 0.5px, text-transform none
- Secondary CTA: background `rgba(255,255,255,0.15)`, color `#ffffff`, 14px weight 500, padding 8px 56px, border-radius 4px, border 3px solid `#ffffff`, backdrop-filter blur(8px)
- On mobile (<600px): vehicle name 40px, CTA stack vertical full-width, padding-bottom 80px

### Feature Showcase Section (Photo Left/Right)

Create a feature section with Tesla visual identity:
- Layout: full-width, min-height 100vh, display grid, grid-template-columns 1fr 1fr
- One column: full-bleed photograph, `object-fit: cover`, no border-radius, edge-to-edge
- Other column: background `#ffffff`, display flex, flex-direction column, justify-content center, padding 80px 64px
- Section label: 12px, weight 500, letter-spacing 1px, text-transform uppercase, color `#5c5e62`, margin-bottom 16px
- Heading: 40px, weight 300, line-height 1.20, color `#171a20`
- Description: 17px, weight 400, line-height 1.50, color `#5c5e62`, margin-top 16px, max-width 480px
- Inline link: color `#171a20`, 14px, weight 500, text-decoration underline, underline-offset 4px
- NO box shadows, NO border-radius, NO card containers
- Alternate photo left/right between sections
- On mobile (<600px): stack vertical, photo section height 50vh, text padding 48px 24px

### CTA Button Row

Create a CTA button row with Tesla visual identity:
- Layout: flex, gap 24px, align-items center, justify-content center
- Primary button (rare -- Tesla Blue): background `#3e6ae1`, color `#ffffff`, font 14px weight 500, padding 8px 56px, border-radius 4px, border none, cursor pointer, transition opacity 300ms ease
- Primary hover: opacity 0.85
- Ghost button (common on dark): background transparent, color `#ffffff`, font 14px weight 500, padding 8px 56px, border-radius 4px, border 3px solid `#ffffff`
- Ghost hover: background `rgba(255,255,255,0.1)`
- Ghost button on light: background transparent, color `#171a20`, font 14px weight 500, padding 8px 56px, border-radius 4px, border 3px solid `#171a20`
- Ghost hover on light: background `rgba(23,26,32,0.05)`
- Underline link (most common Tesla CTA): no button styling at all -- just 14px, weight 500, color `#171a20`, border-bottom 1px solid `#171a20`, padding-bottom 2px
- On mobile (<600px): flex-direction column, buttons full-width, gap 12px

### Navigation Bar (Transparent Overlay)

Create a navigation bar with Tesla visual identity:
- Position: fixed, top 0, left 0, width 100%, z-index 1000
- Background: transparent (overlays hero photography), transitions to `rgba(255,255,255,0.72)` with `backdrop-filter: blur(16px)` on scroll
- Height: 52px, display flex, align-items center, justify-content space-between
- Container: max-width none (full-width), padding 0 40px
- Logo: Tesla wordmark SVG, color `#ffffff` on dark hero, transitions to `#171a20` on scroll
- Nav links: 14px weight 500, color `#ffffff` on hero, transition to `#393c41` on scroll, gap 20px, no text-decoration
- Nav link hover: opacity 0.7
- Right side: Account icon, globe icon, hamburger menu icon -- all 14px, no labels
- On mobile (<900px): only logo + hamburger visible, slide-out full-screen overlay menu with links at 24px weight 300
- Shadow: none in transparent state; `0 1px 4px rgba(0,0,0,0.06)` when scrolled
- Transition: all 300ms ease

### Specs Display (Clean Data Grid)

Create a vehicle specs display with Tesla visual identity:
- Background: `#ffffff`
- Container: max-width 1120px, centered, padding 120px 24px
- Section heading: 40px, weight 300, line-height 1.20, color `#171a20`, text-align center, margin-bottom 80px
- Grid layout: display grid, grid-template-columns repeat(3, 1fr), gap 0
- Each spec cell: text-align center, padding 48px 24px, border-bottom 1px solid `#d0d1d2`
- Spec value: 24px, weight 300, color `#171a20`, margin-bottom 8px
- Spec label: 14px, weight 400, color `#5c5e62`
- Spec suffix/unit: same size as value, weight 300
- Last row: border-bottom none
- NO background color alternation, NO shadows, NO icons
- On mobile (<600px): grid-template-columns 1fr, each cell border-bottom 1px solid `#d0d1d2`

### Brand-Specific: Full-Bleed Photo Gallery (Scroll-Driven)

Create a Tesla-signature scroll-driven photo gallery:
- Layout: vertical stack of full-viewport (100vh) sections, each with a different vehicle photograph
- Each section: width 100%, height 100vh, position relative, overflow hidden
- Background image: `object-fit: cover`, full-bleed, no border-radius, no margin
- Content overlay: position absolute, bottom 120px, left 50%, transform translateX(-50%), text-align center
- Vehicle name: 40px, weight 300, color `#ffffff`, text-shadow `0 1px 4px rgba(0,0,0,0.3)`
- Price/tagline: 17px, weight 400, color `#ffffff`, opacity 0.8, margin-top 8px
- CTA pair below text: ghost buttons with white borders (see CTA Button Row ghost variant)
- Scroll behavior: `scroll-snap-type: y mandatory` on parent, `scroll-snap-align: start` on each section
- Parallax effect: background image translates at 0.15x scroll rate via `transform: translateY(calc(var(--scroll-y) * 0.15))`
- Crossfade between sections: 500ms ease transition
- Mobile: vehicle name 28px, CTAs stack vertical

---

## 4. Iteration Guide

1. **Photography IS the design.** Every section should either contain a full-bleed photograph or exist to support one. If your layout has sections with no imagery, it is not Tesla. The white space between text and the edge of a photo is where the brand lives.

2. **Full-bleed means FULL-bleed.** No max-width containers wrapping images. No border-radius on photographs. No padding between the image and the viewport edge. Images touch all four edges of their section. Text content uses max-width containers; images never do.

3. **Use weight 300 for headlines, never 600+.** Tesla's typographic signature is airy, light headings that recede behind the photography. Heavy type competes with the image. If your headline weight exceeds 500, it is wrong.

4. **The blue accent (`#3e6ae1`) appears at most twice per viewport.** On the "Custom Order" button and possibly one text link. Everything else is monochromatic black/white/gray. If you can count more than two blue elements visible at any scroll position, reduce.

5. **Ghost buttons over photography.** On dark/photo backgrounds, CTAs are transparent with white borders -- never filled blue buttons over imagery. The blue button appears only on white backgrounds. This preserves the cinematic atmosphere.

6. **Zero decoration.** No icons in navigation. No divider ornaments. No gradient backgrounds. No background patterns. No card shadows. No badge pills. The only visual elements are: photography, text, thin borders, and the occasional blue button.

7. **Monochromatic restraint.** Outside of the blue accent, the entire palette is grayscale: `#000000`, `#171a20`, `#393c41`, `#5c5e62`, `#ababab`, `#d0d1d2`, `#f4f4f4`, `#ffffff`. If you reach for any other color, stop.

8. **Navigation disappears into the hero.** The nav bar starts fully transparent with white text over the hero image. It should feel like it does not exist until needed. On scroll, it transitions to frosted glass. Never start with a solid white nav.

9. **100vh sections, not scrollable content blocks.** Tesla organizes content as a stack of full-viewport slides, not as a long-scrolling page with cards. Each section is a full 100vh "frame." Scroll-snap is characteristic.

10. **Alternate light and dark full-bleed zones.** White text on cinematic photo -> specs on white background -> dark photo section -> features on white -> photo gallery. This rhythm of light/dark/photo creates the Tesla scrolling experience.
