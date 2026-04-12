# Ferrari -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Ferrari-branded components.
Aesthetic: cinematic chiaroscuro -- deep black surfaces, surgical Rosso Corsa accents, Italian luxury restraint. Photography does the talking; the interface recedes.

---

## 1. Quick Color Reference

```
Surface (page bg):    #0c0c0c   Nero Profondo -- cinematic depth, not pure black
Card surface:         #161616   Carbon Fiber -- elevated panels, spec containers
Secondary surface:    #1e1e1e   Grigio Scuro -- footer, nav dropdowns
Accent CTA:          #dc0000   Rosso Corsa -- THE Ferrari red, extreme restraint
Accent hover:        #ff1a1a   Rosso Vivace -- brighter red, never at rest
Accent pressed:      #8b0000   Rosso Scuro -- darkened for pressed states
Gold accent:         #c5a258   Oro Ferrari -- Scuderia badges, heritage, premium tier
Text primary:        #ffffff   Bianco Puro -- headlines, vehicle names
Text secondary:      #999999   Argento -- body copy, descriptions
Text tertiary:       #666666   Grigio Medio -- metadata, spec labels
Text on accent:      #ffffff   White on Rosso Corsa
Error:               #ff3333   Distinct from brand red (lighter, more orange)
Success:             #00b050   Verde Semaforo -- green light, go signal
Warning:             #f5a623   Giallo Modena -- amber, Prancing Horse heritage
Border default:      rgba(255,255,255,0.08)  Whisper containment
Border hover:        rgba(255,255,255,0.15)  Interaction reveal
Border accent:       rgba(220,0,0,0.30)      Red glow, active state
```

---

## 2. Quick Typography Reference

```
Hero:       'Ferrari Sans', 'Helvetica Neue', sans-serif  | 72px | weight 300 | line-height 1.05 | letter-spacing -0.02em
Display:    'Ferrari Sans', 'Helvetica Neue', sans-serif  | 48px | weight 700 | line-height 1.15 | letter-spacing -0.02em
Section:    'Ferrari Sans', 'Helvetica Neue', sans-serif  | 32px | weight 700 | line-height 1.15 | letter-spacing normal
Subheading: 'Ferrari Sans', 'Helvetica Neue', sans-serif  | 24px | weight 500 | line-height 1.15 | letter-spacing normal
Body Large: 'Ferrari Sans', 'Helvetica Neue', sans-serif  | 18px | weight 400 | line-height 1.55 | letter-spacing normal
Body:       'Ferrari Sans', 'Helvetica Neue', sans-serif  | 16px | weight 400 | line-height 1.55 | letter-spacing normal
Caption:    'Ferrari Sans', 'Helvetica Neue', sans-serif  | 14px | weight 400 | line-height 1.43 | letter-spacing normal
Overline:   'Ferrari Sans', 'Helvetica Neue', sans-serif  | 11px | weight 500 | line-height 1.25 | letter-spacing 0.12em | text-transform uppercase
Mono:       'SF Mono', 'Roboto Mono', monospace            | 15px | weight 400 | line-height 1.50 | letter-spacing -0.01em
```

Key rules:
- Ferrari Sans is proprietary. DO NOT load Google Fonts. Fallbacks handle rendering.
- Hero headlines use weight 300 (light) for elegance at large sizes. Display/section use 700 (bold) for authority.
- Overline labels are always uppercase with wide letter-spacing (0.12em). They precede headlines like a category tag.
- Body line-height is 1.55 -- generous enough for editorial reading on dark backgrounds.
- Monospace is reserved for performance data: horsepower, torque, lap times, 0-100 km/h.

---

## 3. Example Component Prompts

### Hero Section (Cinematic Vehicle Reveal)

Create a hero section with Ferrari visual identity:
- Background: `#0c0c0c` (Nero Profondo), full-viewport height `100vh`
- Hero image: full-bleed background with `object-fit: cover`, dark gradient overlay from bottom `linear-gradient(to top, #0c0c0c 0%, transparent 60%)`
- Container: max-width 1440px, centered, padding 0 64px, positioned at bottom of viewport
- Overline: "THE NEW" at 11px Ferrari Sans, weight 500, letter-spacing 0.12em, text-transform uppercase, color `#dc0000` (Rosso Corsa), margin-bottom 16px
- Headline: vehicle name at 72px Ferrari Sans, weight 300, line-height 1.05, letter-spacing -0.02em, color `#ffffff`, text-transform uppercase
- Subtitle: 18px Ferrari Sans, weight 400, line-height 1.55, color `#999999`, max-width 560px, margin-top 20px
- CTA button: background `#dc0000`, color `#ffffff`, 14px Ferrari Sans weight 500, letter-spacing 0.08em, text-transform uppercase, padding 14px 32px, border-radius 0px (sharp edges), border: none
- CTA hover: background `#ff1a1a`, box-shadow `0 0 20px -4px rgba(220,0,0,0.25)`
- Secondary link: color `#ffffff`, 14px weight 500, letter-spacing 0.08em, text-transform uppercase, text-decoration none, border-bottom 1px solid `rgba(255,255,255,0.3)`, padding-bottom 2px
- Button row: flex, gap 24px, margin-top 40px, margin-bottom 80px
- On mobile (<640px): headline 40px, subtitle 16px, padding 0 20px, gradient starts at 70%

### Feature Card (Vehicle Attribute)

Create a feature card with Ferrari visual identity:
- Background: `#161616` (Carbon Fiber)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 4px
- Padding: 32px
- Overline: 11px Ferrari Sans, weight 500, letter-spacing 0.12em, text-transform uppercase, color `#dc0000`, margin-bottom 12px
- Title: 24px Ferrari Sans, weight 700, line-height 1.15, color `#ffffff`, margin-bottom 12px
- Description: 16px Ferrari Sans, weight 400, line-height 1.55, color `#999999`
- Optional icon area: 40px, color `#dc0000`, margin-bottom 16px -- use thin line icons (not filled)
- Hover state: border-color transitions to `rgba(255,255,255,0.15)`, background shifts to `#1a1a1a`
- Transition: all 350ms cubic-bezier(0.25, 0.1, 0.25, 1)
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Ferrari visual identity:
- Layout: flex, gap 24px, align-items center
- Primary button (Rosso Corsa): background `#dc0000`, color `#ffffff`, font 14px Ferrari Sans weight 500, letter-spacing 0.08em, text-transform uppercase, padding 14px 32px, border-radius 0px (sharp, engineered), border: none, cursor pointer, transition all 200ms ease
- Primary hover: background `#ff1a1a`, box-shadow `0 0 20px -4px rgba(220,0,0,0.25)`
- Primary pressed: background `#8b0000`
- Secondary button (Ghost): background transparent, color `#ffffff`, font 14px weight 500, letter-spacing 0.08em, text-transform uppercase, padding 14px 32px, border: 1px solid `rgba(255,255,255,0.15)`, border-radius 0px
- Secondary hover: border-color `rgba(255,255,255,0.30)`, background `rgba(255,255,255,0.03)`
- Gold variant (Heritage): background `#c5a258`, color `#0c0c0c`, same sizing, border: none
- Gold hover: background `#d4b36a`
- On mobile (<640px): flex-direction column, buttons full-width, text-align center

### Navigation Bar

Create a navigation bar with Ferrari visual identity:
- Background: `#0c0c0c` with `backdrop-filter: blur(12px)` and `background: rgba(12,12,12,0.92)`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `rgba(255,255,255,0.06)`
- Container: max-width 1440px, centered, padding 0 64px, height 72px, display flex, align-items center, justify-content space-between
- Logo zone (left): Ferrari wordmark or Prancing Horse in `#ffffff`, height 28px
- Nav links (center): 12px Ferrari Sans, weight 500, letter-spacing 0.10em, text-transform uppercase, color `#999999`, gap 40px, text-decoration none
- Nav link hover: color `#ffffff`, transition 200ms
- Nav link active: color `#dc0000`
- CTA button (right): background `#dc0000`, color `#ffffff`, 11px weight 500, letter-spacing 0.08em, text-transform uppercase, padding 10px 24px, border-radius 0px
- On mobile (<768px): nav links collapse to hamburger icon (white, 24px), CTA remains visible, height reduces to 64px

### Performance Specs Display (Data Card)

Create a performance specs card with Ferrari visual identity:
- Background: `#161616` (Carbon Fiber)
- Border: 1px solid `rgba(255,255,255,0.08)`
- Border-radius: 4px
- Padding: 40px
- Layout: CSS Grid, 3 columns on desktop, 2 on tablet, 1 on mobile
- Each spec item:
  - Overline label: 11px Ferrari Sans, weight 500, letter-spacing 0.12em, text-transform uppercase, color `#666666`, margin-bottom 8px
  - Value: 40px monospace (`SF Mono`), weight 400, color `#ffffff`, letter-spacing -0.01em
  - Unit suffix: 16px Ferrari Sans, weight 400, color `#666666`, margin-left 4px (inline with value)
  - Divider: 1px solid `rgba(255,255,255,0.06)` between items (horizontal on mobile, vertical on desktop)
- Example data: "830" cv | "9,500" rpm | "2.9" s (0-100 km/h) | "340" km/h | "725" Nm | "1,385" kg
- Rosso Corsa accent: thin 2px left border on the card container, color `#dc0000`
- On mobile (<640px): single column, value drops to 32px, padding 24px

### Vehicle Showcase / Performance Card

Create a vehicle showcase card with Ferrari visual identity:
- Outer wrapper: background `#0c0c0c`, padding 120px 64px (section-level spacing)
- Card: max-width 1200px, centered, background `#161616`, border 1px solid `rgba(255,255,255,0.08)`, border-radius 4px, overflow hidden
- Image region (top 60%): full-width vehicle photograph, `object-fit: cover`, aspect-ratio 16/9, gradient overlay at bottom `linear-gradient(to top, #161616 0%, transparent 40%)`
- Content region (bottom): padding 40px 48px
  - Overline: "V12 BERLINETTA" at 11px, weight 500, letter-spacing 0.12em, uppercase, color `#dc0000`, margin-bottom 12px
  - Vehicle name: "Ferrari 12Cilindri" at 40px Ferrari Sans, weight 300, line-height 1.10, color `#ffffff`
  - Description: 16px Ferrari Sans, weight 400, line-height 1.55, color `#999999`, max-width 600px, margin-top 16px
  - Spec row (inline): flex, gap 40px, margin-top 32px, border-top 1px solid `rgba(255,255,255,0.08)`, padding-top 32px
    - Each spec: label (11px uppercase `#666666`) above value (24px monospace `#ffffff`)
    - Example: "POWER" / "830 cv" | "0-100 KM/H" / "2.9 s" | "MAX SPEED" / "340 km/h"
  - CTA row: margin-top 40px, flex, gap 24px
    - Primary: "DISCOVER" button in Rosso Corsa
    - Secondary: "CONFIGURE" ghost button
- On mobile (<640px): padding 48px 20px outer, 24px inner, vehicle name 28px, spec row wraps to 2-col grid, image aspect-ratio 4/3

---

## 4. Iteration Guide

1. **Black is the canvas, photography is the paint.** Every section begins with `#0c0c0c`. Content emerges from darkness. Vehicle photography should be full-bleed, edge-to-edge, cinematic. The interface exists to frame the car, not to decorate.

2. **Rosso Corsa is ammunition, not wallpaper.** `#dc0000` appears on primary CTAs, active navigation states, overline labels, and thin accent borders. Count the red pixels: if more than 5% of any viewport is red, you have overshot. The restraint IS the luxury.

3. **Sharp edges express engineering precision.** Buttons use `border-radius: 0px`. Cards use 4px maximum. This is not a consumer app -- it is a precision instrument. Pill shapes and rounded corners feel casual and wrong here.

4. **Uppercase with wide tracking is the voice of authority.** Navigation, overlines, button labels, and category tags all use text-transform uppercase with letter-spacing 0.08-0.12em. Body text is never uppercase. This creates a clear split between "commanding" text and "describing" text.

5. **Performance data gets monospace treatment.** Horsepower, torque, speed, weight, lap times -- any number that proves the car's capability renders in monospace (SF Mono). This channels the racing telemetry aesthetic and differentiates data from prose.

6. **Shadows on dark must be heavier than you think.** Standard `rgba(0,0,0,0.05)` shadows are invisible on `#0c0c0c`. Use `rgba(0,0,0,0.40)` minimum for subtle lift, `rgba(0,0,0,0.60)` for prominent elevation. The Rosso Corsa glow shadow (`rgba(220,0,0,0.25)`) replaces traditional blue focus rings.

7. **Gold (`#c5a258`) is the heritage accent.** Use it for Scuderia Ferrari badges, limited edition markers, and premium tier indicators. Never mix gold and red in the same element -- they represent different brand lineages (heritage vs. racing).

8. **Cinematic motion, not snappy UI.** Standard transitions use 350ms, hero reveals use 600-1000ms. The easing curve `cubic-bezier(0.16, 1, 0.3, 1)` creates a dramatic deceleration that feels like a camera dolly shot settling into position.

9. **The gradient overlay is non-negotiable on photography.** Every full-bleed image needs `linear-gradient(to top, #0c0c0c 0%, transparent 60%)` (or matching surface color) to ensure text legibility. Text sitting directly on ungraded photography is a critical violation.

10. **Content width splits at two breakpoints.** Photography and hero sections span 1440px. Text content and card grids cap at 1200px. This creates a visual hierarchy where the car always feels bigger than the words describing it.
