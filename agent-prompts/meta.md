# Meta -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Meta-branded components.
Aesthetic: open, optimistic connectivity -- light-filled social surfaces where content and people feel close, effortless, and human.

---

## 1. Quick Color Reference

```
Surface (page bg):    #ffffff   Pure White -- clean canvas, the air between cards
Page fill:            #f0f2f5   Facebook Gray -- the subtle neutral fill behind feed cards
Card surface:         #ffffff   White Card -- every post, dialog, and container is a white card
Hover surface:        #f2f3f5   Hover Gray -- barely-there lift on interactive surfaces
Active surface:       #e4e6eb   Active Gray -- pressed state, visible depression
Blue tint:            #ebf5ff   Blue Wash -- selected/active state background tint
Accent (Meta Blue):   #0064e0   Meta Blue -- the signature color, CTAs, links, primary actions
Accent hover:         #0058c5   Blue Hover -- deeper blue for hover feedback
Accent light:         #0080fb   Light Blue -- badges, highlights, secondary blue moments
Green:                #42b72a   Success Green -- online indicators, confirmations
Red:                  #e41e3f   Notification Red -- notification badges, errors, destructive actions
Warning:              #f7b928   Amber -- caution states, attention signals
Text primary:         #050505   Near Black -- user names, headlines, primary content
Text secondary:       #65676b   Medium Gray -- timestamps, captions, metadata
Text tertiary:        #8a8d91   Light Gray -- placeholders, disabled labels
Border:               #dadde1   Border Gray -- card edges, input borders, dividers
Border subtle:        #e4e6eb   Inner Divider -- lighter separators within cards
Dark bg:              #18191a   Dark Mode Surface -- dark mode page background
Dark card:            #242526   Dark Mode Card -- elevated container in dark mode
```

---

## 2. Quick Typography Reference

```
Display:    Optimistic Display, system-ui, sans-serif  | 48px | weight 700 | line-height 1.15 | letter-spacing -0.5px
Section:    Optimistic Display, system-ui, sans-serif  | 32px | weight 700 | line-height 1.25 | letter-spacing normal
Title:      Optimistic Text, system-ui, sans-serif     | 24px | weight 600 | line-height 1.25 | letter-spacing normal
Subtitle:   Optimistic Text, system-ui, sans-serif     | 20px | weight 600 | line-height 1.34 | letter-spacing normal
Body Lg:    Optimistic Text, system-ui, sans-serif     | 17px | weight 400 | line-height 1.34 | letter-spacing normal
Base:       Optimistic Text, system-ui, sans-serif     | 15px | weight 400 | line-height 1.34 | letter-spacing normal
Caption:    Optimistic Text, system-ui, sans-serif     | 13px | weight 400 | line-height 1.34 | letter-spacing normal
Small:      Optimistic Text, system-ui, sans-serif     | 12px | weight 400 | line-height 1.25 | letter-spacing normal
```

Key rules:
- Optimistic Display for marketing/hero headlines (weight 700, reserved for 32px+)
- Optimistic Text for everything else (body, buttons, labels, card titles at 600)
- Facebook's base font size is 15px, NOT 16px -- this is a deliberate density choice
- Body line-height is 1.34, tighter than most, to maximize feed content density
- User names in feed render at 15px weight 600 -- same size as body, differentiated by weight alone

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Meta visual identity:
- Background: `#ffffff` (White)
- Container: max-width 1200px, centered, padding 96px 64px
- Headline: "Connect with Your World" at 48px Optimistic Display, weight 700, line-height 1.15, letter-spacing -0.5px, color `#050505`
- Subtitle: 20px Optimistic Text, weight 400, line-height 1.50, color `#65676b`, max-width 600px, margin-top 16px
- CTA button: background `#0064e0`, color `#ffffff`, 15px Optimistic Text weight 600, padding 10px 24px, border-radius 8px, box-shadow: `0px 1px 1px rgba(0,0,0,0.05), inset 0px 1px 0px rgba(255,255,255,0.15)`
- Secondary button: background `#e4e6eb`, color `#050505`, 15px Optimistic Text weight 600, padding 10px 24px, border-radius 8px
- Button row gap: 12px, margin-top 32px
- On mobile (<480px): headline 32px, subtitle 17px, padding 48px 16px, buttons stack full-width

### Feature Card

Create a feature card with Meta visual identity:
- Background: `#ffffff` (White)
- Border: 1px solid `#dadde1`
- Border-radius: 8px
- Padding: 24px
- Box-shadow: `0px 1px 2px rgba(0,0,0,0.10)`
- Title: 20px Optimistic Text, weight 600, line-height 1.25, color `#050505`, margin-bottom 8px
- Description: 15px Optimistic Text, weight 400, line-height 1.34, color `#65676b`
- Icon area: 48px circle, background `#ebf5ff`, centered icon in `#0064e0`, margin-bottom 16px
- Hover state: box-shadow shifts to `0px 2px 8px rgba(0,0,0,0.10), 0px 1px 2px rgba(0,0,0,0.06)`, border-color `#bec3c9`
- On mobile (<480px): padding 16px, title 17px

### CTA Button Row

Create a CTA button row with Meta visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button (Meta Blue): background `#0064e0`, color `#ffffff`, 15px Optimistic Text weight 600, padding 10px 24px, border-radius 8px, border: none, box-shadow: `0px 1px 1px rgba(0,0,0,0.05), inset 0px 1px 0px rgba(255,255,255,0.15)`, cursor pointer, transition: all 200ms ease
- Primary hover: background `#0058c5`
- Primary active: background `#004da6`, transform `scale(0.98)`
- Secondary button (Gray): background `#e4e6eb`, color `#050505`, 15px Optimistic Text weight 600, padding 10px 24px, border-radius 8px, border: none
- Secondary hover: background `#dadde1`
- Outline button: background transparent, color `#0064e0`, 15px weight 600, padding 10px 24px, border-radius 8px, border: 1px solid `#0064e0`
- Outline hover: background `#ebf5ff`
- On mobile (<480px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Meta visual identity:
- Background: `#ffffff`, position sticky, top 0, z-index 100
- Box-shadow: `0px 1px 2px rgba(0,0,0,0.10)` (the signature Facebook nav shadow)
- Container: max-width 1200px, centered, padding 0 16px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Meta wordmark or blue infinity symbol, left-aligned, 28px height
- Nav links: icon-based navigation in center, 24px icons, inactive color `#65676b`, active color `#0064e0` with 3px bottom border in `#0064e0`
- Active tab: add `#ebf5ff` background tint on hover, pill radius 8px
- Search: right-side, pill-shaped input (border-radius 9999px), background `#f0f2f5`, padding 8px 16px, 15px placeholder color `#8a8d91`
- Profile avatar: 36px circle, right-aligned, border-radius 50%
- On mobile (<768px): bottom navigation bar, 5 icon tabs, active indicator dot below icon

### Data Card / Metric Display

Create a metric display card with Meta visual identity:
- Background: `#ffffff` (White)
- Border: 1px solid `#dadde1`
- Border-radius: 8px
- Padding: 24px
- Box-shadow: `0px 1px 2px rgba(0,0,0,0.10)`
- Overline label: 12px Optimistic Text, weight 600, line-height 1.25, letter-spacing 0.5px, text-transform uppercase, color `#65676b`, margin-bottom 8px
- Metric value: 32px Optimistic Display, weight 700, line-height 1.25, color `#050505`
- Metric trend: 13px Optimistic Text, weight 600, color `#42b72a` (positive) or `#e41e3f` (negative), inline with metric, gap 8px
- Metric description: 15px Optimistic Text, weight 400, line-height 1.34, color `#65676b`, margin-top 8px
- Divider between metric groups: 1px solid `#e4e6eb`, margin 16px 0
- On mobile (<480px): metric value 24px, padding 16px

### Social Feed Card / Community Post

Create a social feed post card with Meta visual identity:
- Background: `#ffffff` (White)
- Border: none (cards float on `#f0f2f5` page background)
- Border-radius: 8px
- Box-shadow: `0px 1px 2px rgba(0,0,0,0.10)`
- Post header: flex row, gap 12px, padding 16px 16px 0
  - Avatar: 40px circle, border-radius 50%, object-fit cover
  - Name: 15px Optimistic Text weight 600, color `#050505`, cursor pointer, hover underline
  - Metadata: 13px Optimistic Text weight 400, color `#65676b` (timestamp + privacy icon)
  - More button: 36px circle, `#65676b` icon, hover background `#f2f3f5`, border-radius 50%
- Post body: 15px Optimistic Text weight 400, line-height 1.34, color `#050505`, padding 8px 16px 12px
  - Links inside text: color `#0064e0`, no underline, hover underline
  - "See more" toggle: 15px weight 600, color `#65676b`
- Media area: full-width image/video, max-height 500px, object-fit cover, no horizontal padding
- Reaction bar: flex, justify-between, padding 10px 16px, border-top 1px solid `#e4e6eb`
  - Reaction summary (left): row of 3 overlapping 18px reaction emoji circles + count in 15px weight 400 `#65676b`
  - Comment/share counts (right): 15px weight 400, color `#65676b`
- Action bar: flex, justify-evenly, padding 4px 8px, border-top 1px solid `#e4e6eb`
  - Like / Comment / Share buttons: 15px weight 600, color `#65676b`, padding 8px 0, flex 1, text-align center, border-radius 4px, hover background `#f2f3f5`
  - Active Like state: color `#0064e0`, icon filled
- On mobile (<480px): same layout scales naturally, padding 12px 12px 0

---

## 4. Iteration Guide

1. **White cards on gray is the Meta signature.** The primary layout pattern is white `#ffffff` cards floating on a `#f0f2f5` gray page fill. Feed cards, dialogs, and panels all follow this pattern. If the page background is white with no gray fill, it does not look like Meta.

2. **Meta Blue is high-signal only.** `#0064e0` appears on primary CTAs, text links, active navigation states, and the Like button active state. It never fills backgrounds or large surfaces. The restraint is what makes it powerful.

3. **Pill shapes are the interaction signature.** Search bars, chip filters, reaction pills, and status badges all use `border-radius: 9999px`. Standard containers use 8px. Mixing these two radii -- pill for interactive, 8px for structural -- is the visual grammar.

4. **Feed density is deliberate.** 15px base text, 1.34 line-height, 13px captions. Meta intentionally makes text smaller and tighter than typical web design to fit more content in the viewport. Do not increase body size to 16px or loosen line-height to 1.5 in feed contexts.

5. **Shadows are real elevation, not decoration.** Cards on `#f0f2f5` get `0px 1px 2px rgba(0,0,0,0.10)`. Popovers get stacked shadows. Modals get deep shadows. The shadow communicates z-index to the user. Never remove card shadows on gray backgrounds -- the shadow is what separates card from page.

6. **Every interactive surface has three states.** Default, hover (`#f2f3f5`), and active (`#e4e6eb`). These three grays create the tactile feedback loop that makes Meta products feel responsive. Skip the active state and it feels sluggish.

7. **User names carry the visual weight.** In feed contexts, the poster's name at 15px weight 600 is the primary hierarchy anchor. The timestamp at 13px weight 400 in `#65676b` is the secondary. This name-bold / time-muted pairing is the DNA of every Meta social surface.

8. **The three-column layout is sacred.** On desktop, Meta uses left sidebar (navigation, 280px) + center column (feed, ~680px) + right sidebar (contacts/ads, 280px). The feed column width is fixed, not responsive. It does not stretch to fill the viewport.

9. **Reactions add the only saturated color.** Outside of Meta Blue, the only high-chroma moments come from reaction emojis: Love red (`#f33e58`), Haha/Wow yellow (`#f7b928`), Angry orange (`#e9710f`). These bursts of color on an otherwise neutral canvas create emotional punctuation.

10. **Dark mode inverts, but keeps the architecture.** `#18191a` page background, `#242526` card surface, `#e4e6eb` text. Same shadows in slightly higher opacity. Same card-on-background pattern. Dark mode is a color swap, not a redesign.
