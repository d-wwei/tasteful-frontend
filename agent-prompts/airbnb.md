# Airbnb -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Airbnb-branded components.
Aesthetic: warm travel magazine with photography-first cards -- inviting, tactile, browse-worthy.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   Pure White -- clean canvas where photography is the color
Card surface:         #ffffff   White -- listing cards with three-layer shadow
Secondary surface:    #f2f2f2   Light Surface -- circular nav buttons, secondary controls
Brand accent:        #ff385c   Rausch Red -- named after Airbnb's first address, singular accent
Brand hover:         #e00b41   Deep Rausch -- pressed/dark variant
Text primary:        #222222   Near Black -- warm, never pure black
Text secondary:      #6a6a6a   Secondary Gray -- descriptions
Text focused:        #3f3f3f   Focused Gray -- focused state
Text disabled:       rgba(0,0,0,0.24)   Disabled -- reduced opacity
Border:              #dddddd   Border Gray -- cards and dividers
Info Blue:           #428bff   Legal Blue -- informational links
```

---

## 2. Quick Typography Reference

```
Section:     Airbnb Cereal VF, Circular, sans-serif  | 28px | weight 700 | line-height 1.43 | letter-spacing normal
Card Title:  Airbnb Cereal VF, Circular, sans-serif  | 22px | weight 600 | line-height 1.18 | letter-spacing -0.44px
Sub-heading: Airbnb Cereal VF, Circular, sans-serif  | 21px | weight 700 | line-height 1.43 | letter-spacing normal
Feature:     Airbnb Cereal VF, Circular, sans-serif  | 20px | weight 600 | line-height 1.20 | letter-spacing -0.18px
UI Medium:   Airbnb Cereal VF, Circular, sans-serif  | 16px | weight 500 | line-height 1.25 | letter-spacing normal
Button:      Airbnb Cereal VF, Circular, sans-serif  | 16px | weight 500 | line-height 1.25 | letter-spacing normal
Body:        Airbnb Cereal VF, Circular, sans-serif  | 14px | weight 400 | line-height 1.43 | letter-spacing normal
Caption:     Airbnb Cereal VF, Circular, sans-serif  | 14px | weight 600 | line-height 1.43 | font-feature-settings: "salt"
Badge:       Airbnb Cereal VF, Circular, sans-serif  | 11px | weight 600 | line-height 1.18 | font-feature-settings: "salt"
Micro:       Airbnb Cereal VF, Circular, sans-serif  |  8px | weight 700 | line-height 1.25 | letter-spacing 0.32px | uppercase
```

Key rules:
- Warm weight range: 500-700 dominate, no thin weights for headings
- Negative tracking on headings: -0.44px on card titles, -0.18px on features
- `"salt"` OpenType feature on specific caption/badge elements for stylistic alternates
- Variable font with discrete stops at 400, 500, 600, 700

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Airbnb visual identity:
- Background: `#ffffff`
- Container: max-width 1440px, centered, padding 80px 64px
- Headline: "Find your next adventure" at 28px Airbnb Cereal VF, weight 700, line-height 1.43, color `#222222`
- Search bar: white background, three-layer card shadow: `rgba(0,0,0,0.02) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 6px, rgba(0,0,0,0.1) 0px 4px 8px`, border-radius 32px, padding 16px 24px
- Search text: 14px Airbnb Cereal VF weight 400, color `#222222`
- Search button: background `#ff385c`, border-radius 50% (circle), white search icon, padding 12px
- On mobile (<550px): headline 22px, search stacks vertically, padding 48px 20px

### Feature Card

Create a listing card with Airbnb visual identity:
- Background: `#ffffff`
- Border-radius: 20px
- Box-shadow: `rgba(0,0,0,0.02) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 6px, rgba(0,0,0,0.1) 0px 4px 8px`
- Image area: top of card, 16:10 aspect ratio, border-radius 20px 20px 0 0, object-fit cover
- Heart overlay: position absolute, top 12px, right 12px, white with dark shadow outline
- Card body padding: 12px 0
- Title: 16px Airbnb Cereal VF, weight 600, line-height 1.25, color `#222222`, margin-bottom 4px
- Rating: 14px weight 400, color `#222222`, inline with star icon
- Description: 14px weight 400, color `#6a6a6a`, line-height 1.43
- Price: 14px weight 600, color `#222222` + " night" in weight 400
- On mobile (<550px): full-width card, image height 220px

### CTA Button Row

Create a CTA button row with Airbnb visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Dark): background `#222222`, color `#ffffff`, font 16px Airbnb Cereal VF weight 500, padding 14px 24px, border-radius 8px, border: none, cursor pointer, transition: all 200ms
- Primary hover: background shifts toward `#ff385c` brand red
- Primary focus: box-shadow `0 0 0 2px #222222`, transform scale(0.92)
- Secondary button (Outline): background transparent, color `#222222`, 16px weight 500, padding 14px 24px, border: 1px solid `#222222`, border-radius 8px
- Circular nav button: background `#f2f2f2`, color `#222222`, border-radius 50%, padding 8px, hover: box-shadow `rgba(0,0,0,0.08) 0px 4px 12px`
- On mobile (<550px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Airbnb visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#eeeeee`
- Container: max-width 1440px, centered, padding 0 40px, height 80px, display flex, align-items center, justify-content space-between
- Logo: Airbnb logo in `#ff385c` (Rausch Red), left-aligned
- Center: search bar with border-radius 32px, shadow: three-layer card shadow, padding 8px 16px
- Right: "Become a Host" text link 14px weight 500, user avatar circle (50% radius), menu icon
- On mobile (<744px): simplified header, search becomes compact, menu button replaces right content

### Data Card / Metric Display

Create a metric display card with Airbnb visual identity:
- Background: `#ffffff`
- Border-radius: 20px
- Box-shadow: `rgba(0,0,0,0.02) 0px 0px 0px 1px, rgba(0,0,0,0.04) 0px 2px 6px, rgba(0,0,0,0.1) 0px 4px 8px`
- Padding: 32px
- Metric value: 28px Airbnb Cereal VF, weight 700, line-height 1.43, color `#222222`
- Metric label: 14px weight 400, color `#6a6a6a`, margin-top 4px
- Trend indicator: 14px weight 600, color `#008a05` (positive) or `#c13515` (negative)
- On mobile (<550px): padding 24px, metric value 22px

### Category Pill Bar (Brand-Specific)

Create a category filter bar with Airbnb visual identity:
- Layout: flex, overflow-x auto, gap 32px, padding 16px 0, border-bottom 1px solid `#eeeeee`
- Category item: flex-direction column, align-items center, gap 8px, cursor pointer, min-width 56px
- Icon: 24px grayscale icon, opacity 0.7
- Label: 12px Airbnb Cereal VF weight 600, color `#6a6a6a`, line-height 1.33
- Active state: color `#222222`, border-bottom 2px solid `#222222`, opacity 1.0
- Hover: opacity 1.0, color `#222222`
- Circular prev/next arrows: 32px, background `#ffffff`, border: 1px solid `#dddddd`, border-radius 50%, box-shadow on hover
- Scroll behavior: scroll-snap-type: x mandatory
- On mobile (<550px): horizontal scroll preserved, gap reduced to 24px

---

## 4. Iteration Guide

1. **Photography is the hero.** The white canvas exists to showcase listing photos. If a component feels empty without color, add a photo rather than a background color. Every card is image-first.

2. **Rausch Red (`#ff385c`) is the singular accent.** Use it for primary CTAs, the logo, and high-signal brand moments only. Never as a background fill or decorative surface. If another color creeps in, remove it.

3. **Three-layer shadows create warm, natural lift.** Always use all three layers: `rgba(0,0,0,0.02) 0px 0px 0px 1px` (border ring) + `rgba(0,0,0,0.04) 0px 2px 6px` (ambient) + `rgba(0,0,0,0.1) 0px 4px 8px` (lift). Never use a single-layer shadow or a heavy drop shadow.

4. **Near-black (`#222222`) for all text, never pure `#000000`.** The warmth of near-black matters for the friendly, welcoming tone. Check every text element.

5. **Generous border-radius.** 8px for buttons, 20px for cards, 32px for large containers, 50% for circular controls. Sharp corners (0-4px) are only for small inline links.

6. **Weight 500 minimum for headings.** Airbnb's type is warm and confident. No thin weights (300, 400) for any heading element. The weight range is 500/600/700.
