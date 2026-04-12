# Bugatti -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Bugatti-branded components.
Aesthetic: ultra-luxury automotive with dark elegance.

---

## 1. Quick Color Reference

```
Surface (page bg):    #0a0a0a
Accent:              #c7a44a
Text primary:        #ffffff
Text secondary:      #8c8c8c
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

Create a hero section with Bugatti visual identity:
- Background: `#0a0a0a` (dark immersive surface)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: 48px, weight 600, line-height 1.15, color `#ffffff`
- Subtitle: 20px, weight 400, line-height 1.50, color `#8c8c8c`, max-width 600px, margin-top 16px
- CTA button: background `#c7a44a`, color `#000000`, 16px weight 500, padding 12px 24px, border-radius 8px
- On mobile (<640px): headline 32px, padding 48px 20px

### Feature Card

Create a feature card with Bugatti visual identity:
- Background: `#1a1a1a`
- Border-radius: 8px
- Padding: 32px
- Title: 24px, weight 600, line-height 1.20, color `#ffffff`
- Description: 16px, weight 400, line-height 1.50, color `#8c8c8c`
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Bugatti visual identity:
- Layout: flex, gap 12px
- Primary: background `#c7a44a`, color `#000000`, padding 12px 24px, border-radius 8px
- Secondary: background transparent, border 1px solid `#c7a44a`, color `#c7a44a`, padding 12px 24px, border-radius 8px
- On mobile (<640px): stack full-width

### Navigation Bar

Create a navigation bar with Bugatti visual identity:
- Background: `#0a0a0a`, position sticky, top 0
- Height: 64px, max-width 1200px, centered
- Logo: brand mark, color `#ffffff`
- Nav links: 14px weight 500, color `#8c8c8c`
- CTA button (right): background `#c7a44a`, color white

### Data Card / Metric Display

Create a metric card with Bugatti visual identity:
- Background: `#1a1a1a`
- Border-radius: 8px, padding 32px
- Metric: 32px weight 600, color `#ffffff`
- Label: 14px weight 400, color `#8c8c8c`

### Brand-Specific Component

Create a component showcasing Bugatti's distinctive design pattern:
- Reflect the brand's ultra-luxury characteristic
- Use accent color `#c7a44a` sparingly for high-signal moments
- Maintain the dark immersive atmosphere

---

## 4. Iteration Guide

1. **Dark surfaces are the foundation.** Start with dark backgrounds and let content provide color.

2. **Accent color is for high-signal moments only.** `#c7a44a` appears on CTAs and key interactive elements. Never use it as a decorative surface fill.

3. **Maintain typographic hierarchy.** Headlines at 600+ weight, body at 400. The weight contrast creates visual structure.

4. **Respect the brand's spacing rhythm.** 8px base grid. Generous section spacing (80px+). Content should breathe.

5. **Use heavy shadows for elevation on dark.**

6. **Every component should feel unmistakably Bugatti.** The ultra-luxury aesthetic is the brand's signature.
