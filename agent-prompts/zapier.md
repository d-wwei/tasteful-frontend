# Zapier -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Zapier-branded components.
Aesthetic: warm automation energy -- friendly orange on cream canvas, playful but professional.

---

## 1. Quick Color Reference

```
Surface (page bg):    #fffdf9   Bridal Heath -- warm near-white with peach undertone
Card surface:         #fff3e6   Serenade -- warm cream with subtle orange glow
Interactive surface:  #ffecd2   Light Peach -- button backgrounds, hover fills
Accent CTA:          #ff4f00   Zap Orange -- International Orange, the energy of automation
Accent hover:        #e64500   Deep Orange -- darker for hover/pressed feedback
Accent secondary:    #fd7622   Pumpkin -- warm sibling for gradients and secondary emphasis
Accent gold:         #ffc43e   Sunglow -- badges, highlights, tertiary signals
Text primary:        #201515   Zapier Earth -- warm cocoa-black, never pure black
Text secondary:      #594a42   Warm Brown -- descriptions and body copy
Text tertiary:       #8c7b72   Warm Taupe -- metadata, timestamps, de-emphasized
Text on dark:        #c4b5ab   Sand Silver -- readable on dark Earth backgrounds
Border default:      #f0e6d8   Cream Border -- soft warm containment
Border prominent:    #e0d1c2   Warm Tan -- section dividers, emphasized borders
Dark surface:        #201515   Zapier Earth -- dark theme background
Success:             #13d0ab   Java Teal -- connected/active Zap status
Info:                #499df3   Picton Blue -- informational states and links
Error:               #d4351c   Warm Red -- error without mimicking Zap Orange
```

---

## 2. Quick Typography Reference

```
Display:    Degular, system-ui, sans-serif        | 64px | weight 700 | line-height 1.10 | letter-spacing -0.02em
Hero:       Degular, system-ui, sans-serif        | 52px | weight 700 | line-height 1.10 | letter-spacing -0.02em
Section:    Degular, system-ui, sans-serif        | 40px | weight 600 | line-height 1.20 | letter-spacing -0.02em
Subheading: Degular, system-ui, sans-serif        | 32px | weight 600 | line-height 1.20 | letter-spacing normal
Card Title: Degular, system-ui, sans-serif        | 24px | weight 600 | line-height 1.30 | letter-spacing normal
Body Large: Inter, system-ui, sans-serif          | 20px | weight 400 | line-height 1.55 | letter-spacing normal
Body:       Inter, system-ui, sans-serif          | 16px | weight 400 | line-height 1.55 | letter-spacing normal
Caption:    Inter, system-ui, sans-serif          | 14px | weight 400 | line-height 1.43 | letter-spacing normal
Label:      Inter, system-ui, sans-serif          | 12px | weight 500 | line-height 1.25 | letter-spacing 0.06em
Overline:   Inter, system-ui, sans-serif          | 11px | weight 600 | line-height 1.20 | letter-spacing 0.06em | text-transform uppercase
Code:       JetBrains Mono, Fira Code, monospace  | 14px | weight 400 | line-height 1.55 | letter-spacing normal
```

Key rules:
- Degular for ALL headlines (weights 600-700 -- bold presence, the brand's signature voice)
- Inter for ALL UI text (buttons, labels, nav, body)
- Body line-height is 1.55 -- friendly and approachable, not cramped
- Display headings use -0.02em letter-spacing for tight, punchy presence
- Overline labels use 0.06em wide tracking with uppercase

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Zapier visual identity:
- Background: `#fffdf9` (Bridal Heath)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Automate your work" at 64px Degular, weight 700, line-height 1.10, letter-spacing -0.02em, color `#201515`
- Subtitle: 20px Inter, weight 400, line-height 1.55, color `#594a42`, max-width 560px, margin-top 20px
- CTA button: background `#ff4f00`, color `#ffffff`, 16px Inter weight 500, padding 14px 28px, border-radius 8px, box-shadow: `0px 1px 2px rgba(32,21,21,0.12), inset 0px 1px 0px rgba(255,255,255,0.15)`, cursor pointer, transition: all 200ms ease
- CTA hover: background `#e64500`, transform: translateY(-1px), box-shadow: `0px 4px 12px rgba(32,21,21,0.08)`
- Secondary button: background `#ffecd2`, color `#3d2e25`, 16px Inter weight 500, padding 14px 28px, border-radius 8px, border: none
- Secondary hover: background `#ffe0b8`
- Button row gap: 12px, margin-top 32px
- Orange glow decoration: `box-shadow: 0px 0px 120px 40px rgba(255,79,0,0.06)` on a decorative pseudo-element behind hero text
- On mobile (<640px): headline drops to 36px, subtitle 17px, section padding 48px 20px, buttons stack full-width

### Feature Card

Create a feature card with Zapier visual identity:
- Background: `#ffffff` (white for max contrast on cream canvas)
- Border: 1px solid `#f0e6d8` (warm cream border)
- Border-radius: 12px
- Padding: 32px
- Box-shadow: `0px 1px 3px rgba(32,21,21,0.06), 0px 0px 0px 1px rgba(32,21,21,0.04)`
- Icon area: 48px square, background `#fff3e6` (Serenade), border-radius 12px, display flex, align-items center, justify-content center, margin-bottom 20px. Icon in `#ff4f00` (Zap Orange), 24px
- Title: 24px Degular, weight 600, line-height 1.30, color `#201515`, margin-bottom 8px
- Description: 16px Inter, weight 400, line-height 1.55, color `#594a42`
- Hover state: box-shadow: `0px 4px 12px rgba(32,21,21,0.08), 0px 0px 0px 1px rgba(32,21,21,0.04)`, transform: translateY(-2px), transition: all 200ms ease
- On mobile (<640px): padding 24px, title 20px

### CTA Button Row

Create a CTA button row with Zapier visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Zap Orange): background `#ff4f00`, color `#ffffff`, font 16px Inter weight 500, padding 14px 28px, border-radius 8px, border: none, box-shadow: `0px 1px 2px rgba(32,21,21,0.12), inset 0px 1px 0px rgba(255,255,255,0.15)`, cursor pointer, transition: all 200ms ease
- Primary hover: background `#e64500`, transform: translateY(-1px)
- Secondary button (Warm surface): background `#ffecd2`, color `#3d2e25`, font 16px Inter weight 500, padding 14px 28px, border-radius 8px, border: none
- Secondary hover: background `#ffe0b8`
- Ghost button (outline): background transparent, color `#ff4f00`, font 16px Inter weight 500, padding 14px 28px, border-radius 8px, border: 1.5px solid `#ff4f00`
- Ghost hover: background `#fff3e6`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Zapier visual identity:
- Background: `#fffdf9` (Bridal Heath), position sticky, top 0, z-index 100, backdrop-filter: blur(12px), background: rgba(255,253,249,0.92)
- Border-bottom: 1px solid `#f0e6d8`
- Container: max-width 1200px, centered, padding 0 64px, height 64px, display flex, align-items center, justify-content space-between
- Logo: Zapier wordmark + lightning bolt in `#201515`, left-aligned
- Nav links: 15px Inter, weight 500, color `#594a42`, line-height 1.0, gap 32px, text-decoration none
- Nav link hover: color `#201515`, transition 150ms
- CTA button (right): background `#ff4f00`, color `#ffffff`, 14px Inter weight 500, padding 10px 20px, border-radius 8px
- On mobile (<768px): nav links collapse to hamburger menu, CTA remains visible
- Dark variant: background `#201515`, border-bottom 1px solid `#3d2e25`, links color `#c4b5ab`, hover `#ffffff`

### Data Card / Metric Display

Create a metric display card with Zapier visual identity:
- Background: `#ffffff`
- Border: 1px solid `#f0e6d8`
- Border-radius: 12px
- Padding: 32px
- Box-shadow: `0px 1px 3px rgba(32,21,21,0.06), 0px 0px 0px 1px rgba(32,21,21,0.04)`
- Overline label: 11px Inter, weight 600, line-height 1.20, letter-spacing 0.06em, text-transform uppercase, color `#8c7b72`, margin-bottom 8px
- Metric value: 52px Degular, weight 700, line-height 1.10, color `#201515`
- Unit/suffix: same line, 24px Degular, weight 400, color `#8c7b72`
- Metric description: 16px Inter, weight 400, line-height 1.55, color `#594a42`, margin-top 8px
- Accent stripe (optional): 3px left border in `#ff4f00` for emphasis variant
- On mobile (<640px): metric value 36px, padding 24px

### Zap Flow / Automation Builder Card

Create a Zap Builder step card with Zapier visual identity:
- Outer container: background `#ffffff`, border-radius 16px, padding 0, overflow hidden, box-shadow: `0px 4px 12px rgba(32,21,21,0.08), 0px 0px 0px 1px rgba(32,21,21,0.04)`
- Step header: background `#fff3e6`, padding 16px 20px, display flex, align-items center, gap 12px, border-bottom: 1px solid `#f0e6d8`
- Step number: 28px width, 28px height, background `#ff4f00`, color `#ffffff`, border-radius 50%, display flex, align-items center, justify-content center, font 13px Inter weight 700
- Step label: 11px Inter, weight 600, letter-spacing 0.06em, text-transform uppercase, color `#8c7b72`
- App name: 16px Degular, weight 600, color `#201515`
- Step body: padding 20px, background `#ffffff`
- App icon: 36px square, border-radius 8px, border: 1px solid `#f0e6d8`, margin-right 12px
- Trigger/action text: 14px Inter, weight 400, color `#594a42`, line-height 1.55
- Connection line between steps: 2px wide, dashed, color `#e0d1c2`, centered vertically, height 32px, with animated pulse in `#ff4f00` opacity 0.4 when active
- Active Zap indicator: 8px circle, background `#13d0ab` (Java Teal), with `box-shadow: 0px 0px 0px 3px rgba(19,208,171,0.2)`
- Inactive indicator: 8px circle, background `#e0d1c2`
- On mobile (<640px): step body padding 16px, app icon 28px, connection line height 24px

---

## 4. Iteration Guide

1. **Warm cream canvas is the foundation.** Never use cold `#ffffff` as the page background. Use Bridal Heath (`#fffdf9`) for the page canvas. Pure white (`#ffffff`) is reserved for cards and inputs that need to float above the warm background.

2. **Degular for headlines, Inter for everything else.** Every heading from Display (64px) through Card Title (24px) uses Degular. All buttons, labels, nav links, and body text use Inter. If you see Inter in a headline or Degular on a button, fix it.

3. **Zap Orange is for action, not decoration.** `#ff4f00` appears on primary CTAs, active state indicators, link text, and connection-line pulses. Never use it as a background fill for sections, cards, or large surfaces. Its power comes from scarcity.

4. **Keep all neutrals warm-toned.** Every gray in the system carries a brown/peach undertone. If a generated component uses a cool blue-gray (like `#6b7280` or `#94a3b8`), replace it with the nearest warm equivalent: `#8c7b72` (Taupe), `#594a42` (Warm Brown), or `#a3927f` (Khaki).

5. **Use the warm shadow system.** Zapier shadows use `rgba(32,21,21,...)` as the base -- warm cocoa-tinted -- never neutral `rgba(0,0,0,...)`. Every shadow should feel like it belongs on the cream canvas.

6. **Workflow visual language.** Zapier's signature UI pattern is the step-by-step flow: numbered circles connected by dashed lines. Use this pattern for any sequential or process content. Active steps pulse in Zap Orange; completed steps show Java Teal.

7. **Playful but professional.** Zapier sits at the intersection of fun and trustworthy. Use the bounce easing (`cubic-bezier(0.34, 1.56, 0.64, 1)`) for celebratory moments (Zap success, connection made). Use standard ease for everyday interactions. Avoid stiff, corporate motion.

8. **Generous spacing, breathing room.** Section gaps of 80-120px. Card padding of 32px. The layout should feel open and inviting -- automation should feel effortless, not cramped.

9. **Orange gradient for hero energy.** When a section needs extra visual impact, use a subtle gradient from Zap Orange to Pumpkin (`#ff4f00` to `#fd7622`) on CTAs or decorative elements. Keep gradient usage limited to hero zones and featured moments.

10. **Status colors carry meaning.** `#13d0ab` (Java Teal) means connected/active/success. `#499df3` (Picton Blue) means info/pending. `#ffc43e` (Sunglow) means warning/attention. `#d4351c` (Warm Red) means error/disconnected. These are not decorative -- they are functional signals in the automation context.
