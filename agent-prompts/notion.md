# Notion -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Notion-branded components.
Aesthetic: structured canvas with typographic hierarchy.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff
Accent:              #2eaadc
Text primary:        #37352f
Text secondary:      #787774
```

---

## 2. Quick Typography Reference

```
Display:     System font stack / brand font  | 48px | weight 600 | line-height 1.15
Section:     System font stack / brand font  | 32px | weight 600 | line-height 1.20
Body:        System font stack / brand font  | 16px | weight 400 | line-height 1.50
Caption:     System font stack / brand font  | 14px | weight 400 | line-height 1.43
```

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Notion visual identity:
- Background: `#ffffff` (light clean surface)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: 48px, weight 600, line-height 1.15, color `#37352f`
- Subtitle: 20px, weight 400, line-height 1.50, color `#787774`, max-width 600px, margin-top 16px
- CTA button: background `#2eaadc`, color `#ffffff`, 16px weight 500, padding 12px 24px, border-radius 8px
- On mobile (<640px): headline 32px, padding 48px 20px

### Feature Card

Create a feature card with Notion visual identity:
- Background: `#ffffff`
- Border-radius: 8px
- Padding: 32px
- Title: 24px, weight 600, line-height 1.20, color `#37352f`
- Description: 16px, weight 400, line-height 1.50, color `#787774`
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Notion visual identity:
- Layout: flex, gap 12px
- Primary: background `#2eaadc`, color `#ffffff`, padding 12px 24px, border-radius 8px
- Secondary: background transparent, border 1px solid `#2eaadc`, color `#2eaadc`, padding 12px 24px, border-radius 8px
- On mobile (<640px): stack full-width

### Navigation Bar

Create a navigation bar with Notion visual identity:
- Background: `#ffffff`, position sticky, top 0
- Height: 64px, max-width 1200px, centered
- Logo: brand mark, color `#37352f`
- Nav links: 14px weight 500, color `#787774`
- CTA button (right): background `#2eaadc`, color white

### Data Card / Metric Display

Create a metric card with Notion visual identity:
- Background: `#ffffff`
- Border-radius: 8px, padding 32px
- Metric: 32px weight 600, color `#37352f`
- Label: 14px weight 400, color `#787774`

### Brand-Specific Component

Create a component showcasing Notion's distinctive design pattern:
- Reflect the brand's content-first characteristic
- Use accent color `#2eaadc` sparingly for high-signal moments
- Maintain the clean, light atmosphere

---

## 4. Iteration Guide

1. **Light surfaces are the foundation.** Start with white/light backgrounds for a clean canvas.

2. **Accent color is for high-signal moments only.** `#2eaadc` appears on CTAs and key interactive elements. Never use it as a decorative surface fill.

3. **Maintain typographic hierarchy.** Headlines at 600+ weight, body at 400. The weight contrast creates visual structure.

4. **Respect the brand's spacing rhythm.** 8px base grid. Generous section spacing (80px+). Content should breathe.

5. **Use subtle shadows or surface color shifts for elevation.**

6. **Every component should feel unmistakably Notion.** The content-first aesthetic is the brand's signature.
