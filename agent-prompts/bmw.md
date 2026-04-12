# BMW -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect BMW-branded components.
Aesthetic: precision engineering showroom — angular, clinical, restrained. Every surface is flat, every corner is sharp, every color choice is deliberate. Think Munich headquarters lobby, not Silicon Valley startup.

---

## 1. Quick Color Reference

```
Surface (page bg):       #ffffff   Pure White — showroom-clean canvas, never cream or off-white
Surface subtle:          #f5f5f5   Whisper Gray — alternate sections, content wells
Surface dark:            #1a1a1a   Carbon Black — hero sections, dark mode, feature showcases
Surface silver:          #e8e8ed   Brushed Silver — secondary panels, metallic accent surfaces
Accent CTA:             #1c69d4   BMW Blue — singular interactive color, CTAs and active states only
Accent hover:           #0653b6   Focus Blue — darker on hover/active, never lighter
Accent muted:           #e8f0fb   Blue Tint — selected rows, subtle highlights, never surface fill
Text primary:           #262626   Charcoal — headings and body on light surfaces
Text secondary:         #757575   Meta Gray — descriptions, secondary copy
Text tertiary:          #b0b0b0   Silver — captions, timestamps, disabled
Text on dark:           #ffffff   White — text on Carbon Black
Text on dark secondary: #a0a0a0   Silver — secondary text on dark backgrounds
Border:                 #e0e0e0   Light Steel — dividers, table rules
Border strong:          #c0c0c0   Medium Steel — input outlines, emphasized borders
Error:                  #d30000   Signal Red — error states, like instrument cluster warnings
Success:                #007d48   Racing Green — confirmations, positive status
Warning:                #e5a100   Amber — caution, intermediate status
```

---

## 2. Quick Typography Reference

```
Display:     'BMWTypeNext', Helvetica, Arial, sans-serif  | 56px | weight 300 (Light) | line-height 1.10 | letter-spacing -0.5px
Section:     'BMWTypeNext', Helvetica, Arial, sans-serif  | 36px | weight 400          | line-height 1.20 | letter-spacing 0
Subheading:  'BMWTypeNext', Helvetica, Arial, sans-serif  | 24px | weight 400          | line-height 1.20 | letter-spacing 0
Body Large:  'BMWTypeNext', Helvetica, Arial, sans-serif  | 18px | weight 300          | line-height 1.50 | letter-spacing 0
Body:        'BMWTypeNext', Helvetica, Arial, sans-serif  | 16px | weight 400          | line-height 1.50 | letter-spacing 0
Caption:     'BMWTypeNext', Helvetica, Arial, sans-serif  | 14px | weight 400          | line-height 1.43 | letter-spacing 0
Overline:    'BMWTypeNext', Helvetica, Arial, sans-serif  | 11px | weight 700          | line-height 1.25 | letter-spacing 1.5px | uppercase
Small:       'BMWTypeNext', Helvetica, Arial, sans-serif  | 12px | weight 400          | line-height 1.33 | letter-spacing 0
Mono:        'SF Mono', Consolas, monospace               | 14px | weight 400          | line-height 1.50 | (VINs, specs only)
```

Key typographic rules:
- Weight 300 (Light) at display sizes is BMW's signature. It is not thin — it is precisely engineered to read as airy, confident, and unhurried.
- Weight 400 (Regular) for everything below 36px. Never use 500 or 600 for body text.
- Weight 700 (Bold) reserved exclusively for overline labels and navigation active states.
- Negative letter-spacing (-0.5px) only at display size. All other sizes use 0 or positive.
- BMWTypeNext is proprietary. Never load from Google Fonts. Fallback chain: Helvetica first, then Arial. System-ui is NOT an acceptable fallback — it introduces San Francisco/Segoe, which are visually incompatible.

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with BMW visual identity:
- Background: `#1a1a1a` (Carbon Black) — BMW heroes lead with dark, cinematic surfaces
- Container: max-width 1440px, centered, padding 120px 64px
- Overline: "THE NEW BMW iX" at 11px BMWTypeNext, weight 700, letter-spacing 1.5px, uppercase, color `#a0a0a0`, margin-bottom 16px
- Headline: "Electrifying Precision" at 56px BMWTypeNext, weight 300, line-height 1.10, letter-spacing -0.5px, color `#ffffff`
- Subtitle: 18px BMWTypeNext, weight 300, line-height 1.50, color `#a0a0a0`, max-width 560px, margin-top 20px
- CTA button: background `#1c69d4`, color `#ffffff`, 14px BMWTypeNext weight 700, letter-spacing 0.5px, uppercase, padding 14px 32px, border-radius 0px, border: none, transition: background 200ms ease
- CTA hover: background `#0653b6`
- Secondary button: background transparent, color `#ffffff`, border 1px solid `#ffffff`, same sizing as primary
- Secondary hover: background `rgba(255,255,255,0.08)`
- Button row gap: 16px, margin-top 40px
- Hero image: full-bleed or right-aligned vehicle silhouette with subtle fade into Carbon Black
- On mobile (<640px): headline drops to 36px, subtitle 16px, section padding 64px 20px, buttons stack full-width

### Feature Card

Create a feature card with BMW visual identity:
- Background: `#ffffff` (Pure White)
- Border: 1px solid `#e0e0e0` (Light Steel)
- Border-radius: 0px — sharp corners are non-negotiable
- Padding: 32px
- Box-shadow: none in resting state
- Hover shadow: `0px 1px 3px rgba(0,0,0,0.06), 0px 2px 8px rgba(0,0,0,0.04)` — barely perceptible lift
- Overline: 11px BMWTypeNext, weight 700, letter-spacing 1.5px, uppercase, color `#757575`, margin-bottom 12px
- Title: 24px BMWTypeNext, weight 400, line-height 1.20, color `#262626`, margin-bottom 12px
- Description: 16px BMWTypeNext, weight 400, line-height 1.50, color `#757575`
- Accent indicator: 2px solid `#1c69d4` left border on hover — a BMW Blue hairline that appears precisely on interaction
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with BMW visual identity:
- Layout: flex, gap 16px, align-items center
- Primary button (BMW Blue): background `#1c69d4`, color `#ffffff`, font 14px BMWTypeNext weight 700, letter-spacing 0.5px, uppercase, padding 14px 32px, border-radius 0px, border: none, cursor pointer, transition: background 200ms ease
- Primary hover: background `#0653b6`
- Secondary button (Outline): background transparent, color `#262626`, border 1px solid `#262626`, font 14px BMWTypeNext weight 700, letter-spacing 0.5px, uppercase, padding 14px 32px, border-radius 0px
- Secondary hover: background `#262626`, color `#ffffff`
- Dark variant primary: same BMW Blue
- Dark variant secondary: background transparent, color `#ffffff`, border 1px solid `#ffffff`
- Dark secondary hover: background `rgba(255,255,255,0.08)`
- Disabled state: opacity 0.4, cursor not-allowed
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with BMW visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#e0e0e0`
- Container: max-width 1440px, centered, padding 0 64px, height 72px, display flex, align-items center, justify-content space-between
- Logo: BMW roundel (24px height) + "BMW" wordmark in `#262626`, 16px weight 700, letter-spacing 1px, left-aligned
- Nav links: 14px BMWTypeNext, weight 400, color `#757575`, letter-spacing 0.3px, gap 32px, text-decoration none, text-transform uppercase
- Nav link hover: color `#262626`, transition 200ms
- Active nav link: color `#262626`, weight 700, border-bottom 2px solid `#1c69d4` offset 4px below text
- CTA button (right): background `#1c69d4`, color `#ffffff`, 14px weight 700, uppercase, padding 10px 24px, border-radius 0px
- On mobile (<768px): nav links collapse to hamburger icon (three horizontal lines, 1px stroke, `#262626`), CTA remains visible
- Dark variant: background `#1a1a1a`, border-bottom 1px solid `#333333`, links color `#a0a0a0`, hover `#ffffff`, logo white

### Data Card / Metric Display

Create a metric display card with BMW visual identity:
- Background: `#ffffff`
- Border: 1px solid `#e0e0e0`
- Border-radius: 0px
- Padding: 32px
- Overline label: 11px BMWTypeNext, weight 700, letter-spacing 1.5px, uppercase, color `#757575`, margin-bottom 8px
- Metric value: 56px BMWTypeNext, weight 300, line-height 1.10, letter-spacing -0.5px, color `#262626`
- Unit suffix: 24px weight 300, color `#757575`, margin-left 4px (e.g., "km/h", "kW", "sec")
- Metric description: 14px BMWTypeNext, weight 400, line-height 1.50, color `#757575`, margin-top 12px
- Accent bar: 2px `#1c69d4` at the top of the card — a BMW Blue hairline
- On mobile (<640px): metric value 40px, padding 24px

### Vehicle Configurator Card / Model Showcase

Create a vehicle model showcase card with BMW visual identity:
- Layout: vertical stack, border-radius 0px, overflow hidden
- Image area: aspect-ratio 16/9, background `#f5f5f5`, object-fit cover — vehicle photography on neutral gray
- Content area: padding 32px, background `#ffffff`, border 1px solid `#e0e0e0` (top border omitted since image sits above)
- Model name: 24px BMWTypeNext, weight 400, line-height 1.20, color `#262626` (e.g., "BMW iX xDrive50")
- Tagline: 14px BMWTypeNext, weight 400, color `#757575`, margin-top 4px (e.g., "The Ultimate Electric Driving Machine")
- Specs row: flex, gap 32px, margin-top 20px, padding-top 20px, border-top 1px solid `#e0e0e0`
- Each spec: vertical stack — value in 20px weight 300 color `#262626` (e.g., "523"), unit in 11px weight 700 uppercase letter-spacing 1.5px color `#757575` (e.g., "HORSEPOWER")
- Action row: flex, gap 16px, margin-top 24px
- Primary CTA: "Configure" — background `#1c69d4`, color `#ffffff`, 14px weight 700, uppercase, padding 12px 28px, border-radius 0px
- Secondary CTA: "Explore" — background transparent, color `#262626`, border 1px solid `#262626`, same styling
- Hover: primary shifts to `#0653b6`, secondary inverts to fill `#262626` color `#ffffff`
- On mobile (<640px): specs row wraps to 2x2 grid, gap 16px, buttons stack full-width

---

## 4. Iteration Guide

1. **Pure white is the canvas, not the exception.** BMW digital surfaces start from `#ffffff`. Never use cream, warm gray, or off-white. The showroom is lit by daylight LEDs, not candles. If a generated component has a tinted background on the page level, correct it to pure white immediately.

2. **Zero border-radius is the law.** Every card, button, input, image container, and panel uses `border-radius: 0px`. The only exception is pill-shaped tags/badges (`9999px`), and even those should be rare. If you see `8px`, `12px`, or `16px` radius on any BMW component, it is wrong. Replace with 0.

3. **Light weight at large size is the signature.** Display headlines use weight 300 at 56px. This combination — thin strokes at scale — is what separates BMW typography from generic automotive design. If a headline looks "punchy" or "bold," it has the wrong weight. BMW whispers at volume.

4. **BMW Blue is rationed.** `#1c69d4` appears on primary CTAs, active navigation indicators, progress bars, and 2px accent hairlines. It never appears as a background fill, card surface, or decorative element. If more than ~5% of the visible pixel area is BMW Blue, the design is wrong.

5. **Elevation comes from shadow, not surface color.** On light backgrounds, cards share the same `#ffffff` surface. Depth is communicated through `box-shadow` on hover, not through surface color contrast. The exception is section-level alternation (`#ffffff` vs `#f5f5f5`).

6. **Uppercase overlines structure information hierarchy.** BMW uses 11px, weight 700, letter-spacing 1.5px, uppercase labels above headings, metric values, and feature blocks. These overlines are always `#757575` on light and `#a0a0a0` on dark. They never use BMW Blue.

7. **Dark sections are cinematic, not inverted.** Carbon Black (`#1a1a1a`) sections use the same layout rules but with inverted text colors. Do not simply swap black/white — silver (`#a0a0a0`) replaces `#757575`, white replaces `#262626`, and borders shift to `#333333`.

8. **The grid is 8px and the container is 1440px wide.** BMW's layouts are wider than many brands, reflecting a cinematic widescreen aesthetic. Content within that container is constrained to 960px for readability. Double-check that generated components respect both the outer shell and inner content width.

9. **Buttons are uppercase, sharp, and high-contrast.** Every CTA uses uppercase text, 14px weight 700, letter-spacing 0.5px, and 0px radius. Primary fills BMW Blue; secondary uses a 1px solid border. There is no "ghost button" — BMW secondary buttons always have a visible border.

10. **Shadows are surgical, not decorative.** The resting state of most elements is flat (zero shadow). Shadow appears only on hover or for elevated overlays (modals, dropdowns). The maximum shadow opacity is 0.08. If a component looks like it floats by default, remove the shadow.
