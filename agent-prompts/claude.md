# Claude (Anthropic) -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Claude-branded components.
Aesthetic: literary salon on parchment -- warm, unhurried, editorial.

---

## 1. Quick Color Reference

```
Surface (page bg):    #f5f4ed   Parchment -- warm cream evoking premium paper
Card surface:         #faf9f5   Ivory -- barely lighter than Parchment for layering
Interactive surface:  #e8e6dc   Warm Sand -- button backgrounds, prominent surfaces
Accent CTA:          #c96442   Terracotta Brand -- earthy, the only chromatic color
Accent hover:        #d97757   Coral -- lighter warm variant of Terracotta
Text primary:        #141413   Near Black -- warm olive-tinted dark, never pure black
Text secondary:      #5e5d59   Olive Gray -- warm medium-dark for body copy
Text tertiary:       #87867f   Stone Gray -- metadata, footnotes
Text on dark:        #b0aea5   Warm Silver -- parchment-tinted for dark surfaces
Border light:        #f0eee6   Border Cream -- barely visible warm containment
Border prominent:    #e8e6dc   Border Warm -- section dividers, emphasized borders
Dark surface:        #30302e   Dark Surface -- warm charcoal for dark sections
```

---

## 2. Quick Typography Reference

```
Display:    Anthropic Serif, Georgia, serif        | 64px | weight 500 | line-height 1.10 | letter-spacing normal
Section:    Anthropic Serif, Georgia, serif        | 52px | weight 500 | line-height 1.20 | letter-spacing normal
Subheading: Anthropic Serif, Georgia, serif        | 32px | weight 500 | line-height 1.10 | letter-spacing normal
Body Large: Anthropic Sans, system-ui, sans-serif  | 20px | weight 400 | line-height 1.60 | letter-spacing normal
Body:       Anthropic Sans, system-ui, sans-serif  | 16px | weight 400 | line-height 1.60 | letter-spacing normal
Caption:    Anthropic Sans, system-ui, sans-serif  | 14px | weight 400 | line-height 1.43 | letter-spacing normal
Label:      Anthropic Sans, system-ui, sans-serif  | 12px | weight 500 | line-height 1.25 | letter-spacing 0.12px
Code:       Anthropic Mono, monospace              | 15px | weight 400 | line-height 1.60 | letter-spacing -0.32px
```

Key rules:
- Serif for ALL headlines (weight 500 only -- no bold, no light)
- Sans for ALL UI text (buttons, labels, nav, body)
- Body line-height is 1.60 -- more generous than most tech sites
- No font-feature-settings required

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Claude/Anthropic visual identity:
- Background: `#f5f4ed` (Parchment)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Thoughtful AI" at 64px Anthropic Serif, weight 500, line-height 1.10, letter-spacing normal, color `#141413`
- Subtitle: 20px Anthropic Sans, weight 400, line-height 1.60, color `#5e5d59`, max-width 580px, margin-top 24px
- CTA button: background `#c96442`, color `#faf9f5`, 16px Anthropic Sans weight 500, padding 9.6px 16.8px, border-radius 12px, box-shadow: `#c96442 0px 0px 0px 0px, #c96442 0px 0px 0px 1px`
- Secondary button: background `#e8e6dc`, color `#4d4c48`, 16px weight 400, padding 0px 12px 0px 8px, border-radius 8px, box-shadow: `#e8e6dc 0px 0px 0px 0px, #d1cfc5 0px 0px 0px 1px`
- Button row gap: 12px, margin-top 32px
- On mobile (<640px): headline drops to 36px, subtitle 17px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Claude visual identity:
- Background: `#faf9f5` (Ivory)
- Border: 1px solid `#f0eee6` (Border Cream)
- Border-radius: 8px
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.05) 0px 4px 24px` (whisper elevation)
- Title: 25.6px Anthropic Serif, weight 500, line-height 1.20, color `#141413`, margin-bottom 12px
- Description: 16px Anthropic Sans, weight 400, line-height 1.60, color `#5e5d59`
- Icon area: 48px square, terracotta `#c96442` accent, margin-bottom 20px
- Hover state: box-shadow intensifies to `0px 0px 0px 1px #d1cfc5, rgba(0,0,0,0.05) 0px 4px 24px`
- On mobile (<640px): padding 24px, title 20.8px

### CTA Button Row

Create a CTA button row with Claude visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Terracotta): background `#c96442`, color `#faf9f5`, font 16px Anthropic Sans weight 500, padding 9.6px 16.8px, border-radius 12px, border: none, box-shadow: `#c96442 0px 0px 0px 0px, #c96442 0px 0px 0px 1px`, cursor pointer, transition: all 200ms cubic-bezier(0.16, 1, 0.3, 1)
- Primary hover: background `#d97757`
- Secondary button (Warm Sand): background `#e8e6dc`, color `#4d4c48`, font 16px weight 400, padding 0px 12px 0px 8px, border-radius 8px, border: none, box-shadow: `#e8e6dc 0px 0px 0px 0px, #d1cfc5 0px 0px 0px 1px`
- Secondary hover: box-shadow ring shifts to `#c2c0b6`
- Dark variant button: background `#30302e`, color `#faf9f5`, same padding, border-radius 8px, box-shadow: `#30302e 0px 0px 0px 0px, #30302e 0px 0px 0px 1px`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Claude visual identity:
- Background: `#f5f4ed` (Parchment), position sticky, top 0, z-index 100
- Border-bottom: 1px solid `#f0eee6`
- Container: max-width 1200px, centered, padding 0 64px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Anthropic wordmark in `#141413`, left-aligned
- Nav links: 17px Anthropic Sans, weight 400, color `#5e5d59`, line-height 1.0, gap 32px, text-decoration none
- Nav link hover: color `#141413`, transition 150ms
- CTA button (right): background `#c96442`, color `#faf9f5`, 15px Anthropic Sans weight 500, padding 8px 16px, border-radius 12px
- On mobile (<768px): nav links collapse to hamburger, CTA remains visible
- Dark variant: background `#141413`, border-bottom 1px solid `#30302e`, links color `#b0aea5`, hover `#faf9f5`

### Data Card / Metric Display

Create a metric display card with Claude visual identity:
- Background: `#faf9f5` (Ivory)
- Border: 1px solid `#f0eee6`
- Border-radius: 16px (featured container)
- Padding: 32px
- Box-shadow: `rgba(0,0,0,0.05) 0px 4px 24px`
- Overline label: 10px Anthropic Sans, weight 400, line-height 1.60, letter-spacing 0.5px, text-transform uppercase, color `#87867f`, margin-bottom 8px
- Metric value: 52px Anthropic Serif, weight 500, line-height 1.20, color `#141413`
- Metric description: 16px Anthropic Sans, weight 400, line-height 1.60, color `#5e5d59`, margin-top 12px
- On mobile (<640px): metric value 36.8px, padding 24px

### Dark Section Variant

Create a dark feature section with Claude visual identity:
- Background: `#141413` (Near Black)
- Section padding: 120px 64px
- Container: max-width 1200px, centered
- Section headline: 52px Anthropic Serif, weight 500, line-height 1.20, color `#faf9f5`
- Body text: 17px Anthropic Sans, weight 400, line-height 1.60, color `#b0aea5`
- Card inside dark section: background `#30302e`, border 1px solid `#30302e`, border-radius 8px, padding 32px
- Card title: 25.6px Anthropic Serif, weight 500, line-height 1.20, color `#faf9f5`
- Card description: 15px Anthropic Sans, weight 400, color `#b0aea5`
- CTA button on dark: background `#141413`, color `#b0aea5`, 16px weight 500, padding 9.6px 16.8px, border-radius 12px, border: 1px solid `#30302e`
- On mobile (<640px): section padding 48px 20px, headline 36px

---

## 4. Iteration Guide

1. **Always specify warm backgrounds.** Never use `#ffffff` as page background. Use Parchment (`#f5f4ed`) for light sections and Near Black (`#141413`) for dark sections. Cards sit on Ivory (`#faf9f5`), not white.

2. **Serif for headlines, sans for everything else.** Every headline must use Anthropic Serif at weight 500 -- no other weight. All buttons, labels, nav links, and body text use Anthropic Sans. If you see a sans-serif headline or a bold serif, fix it.

3. **Use ring shadows, not drop shadows.** Claude's depth system is built on `0px 0px 0px 1px` ring patterns in warm colors (`#d1cfc5`, `#c2c0b6`, `#f0eee6`). The only traditional shadow allowed is the whisper elevation: `rgba(0,0,0,0.05) 0px 4px 24px`. Never use generic gray drop shadows.

4. **Keep all neutrals warm-toned.** Every gray in the system has a yellow-brown undertone. If a generated component uses a cool blue-gray (like `#6b7280` or `#94a3b8`), replace it with the nearest warm equivalent from the palette: `#87867f` (Stone), `#5e5d59` (Olive), or `#4d4c48` (Charcoal).

5. **Maintain generous line-height on body text.** Body text uses 1.60 line-height, which is unusually spacious. Resist the urge to tighten it. This generous spacing is what gives Claude's design its literary, editorial quality.

6. **Alternate light and dark sections for rhythm.** The page should read like chapters in a book -- Parchment light sections alternating with Near Black dark sections. Each section shift creates a natural reading pause and visual "room change."
