# Shopify -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Shopify-branded components.
Aesthetic: commerce green with polaris design system.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff
Accent:              #008060
Text primary:        #202223
Text secondary:      #6d7175
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

Create a hero section with Shopify visual identity:
- Background: `#ffffff` (light clean surface)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: 48px, weight 600, line-height 1.15, color `#202223`
- Subtitle: 20px, weight 400, line-height 1.50, color `#6d7175`, max-width 600px, margin-top 16px
- CTA button: background `#008060`, color `#ffffff`, 16px weight 500, padding 12px 24px, border-radius 8px
- On mobile (<640px): headline 32px, padding 48px 20px

### Feature Card

Create a feature card with Shopify visual identity:
- Background: `#ffffff`
- Border-radius: 8px
- Padding: 32px
- Title: 24px, weight 600, line-height 1.20, color `#202223`
- Description: 16px, weight 400, line-height 1.50, color `#6d7175`
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Shopify visual identity:
- Layout: flex, gap 12px
- Primary: background `#008060`, color `#ffffff`, padding 12px 24px, border-radius 8px
- Secondary: background transparent, border 1px solid `#008060`, color `#008060`, padding 12px 24px, border-radius 8px
- On mobile (<640px): stack full-width

### Navigation Bar

Create a navigation bar with Shopify visual identity:
- Background: `#ffffff`, position sticky, top 0
- Height: 64px, max-width 1200px, centered
- Logo: brand mark, color `#202223`
- Nav links: 14px weight 500, color `#6d7175`
- CTA button (right): background `#008060`, color white

### Data Card / Metric Display

Create a metric card with Shopify visual identity:
- Background: `#ffffff`
- Border-radius: 8px, padding 32px
- Metric: 32px weight 600, color `#202223`
- Label: 14px weight 400, color `#6d7175`

### Brand-Specific Component

Create a component showcasing Shopify's distinctive design pattern:
- Reflect the brand's polaris-system characteristic
- Use accent color `#008060` sparingly for high-signal moments
- Maintain the clean, light atmosphere

---

## 4. Iteration Guide

1. **Light surfaces are the foundation.** Start with white/light backgrounds for a clean canvas.

2. **Accent color is for high-signal moments only.** `#008060` appears on CTAs and key interactive elements. Never use it as a decorative surface fill.

3. **Maintain typographic hierarchy.** Headlines at 600+ weight, body at 400. The weight contrast creates visual structure.

4. **Respect the brand's spacing rhythm.** 8px base grid. Generous section spacing (80px+). Content should breathe.

5. **Use subtle shadows or surface color shifts for elevation.**

6. **Every component should feel unmistakably Shopify.** The polaris-system aesthetic is the brand's signature.
