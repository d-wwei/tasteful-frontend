# Cursor -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Cursor-branded components.
Aesthetic: warm-dark IDE workspace -- obsidian surfaces, blue-steel intelligence accents, monospace precision meets gothic display.

---

## 1. Quick Color Reference

```
Surface (page bg):    #14120b   Obsidian -- warm near-black with brown undertone from cursor.com
Surface subtle:       #1b1913   Sidebar -- warm dark panel, file trees, secondary areas
Surface elevated:     #26241e   Card -- warm charcoal for floating containers, dropdowns
Surface overlay:      #201e18   Overlay -- command palette, modal backdrops
Accent:              #4c9df3   Cursor Blue -- signature blue, AI interactions, active states
Accent hover:        #6bb0f7   Cursor Blue Light -- brighter on hover, interactive feedback
Accent muted:        rgba(76,157,243,0.12)  Blue wash -- selected rows, ghost highlights
Text primary:        #d7d6d5   Warm Light -- headlines and body, warm-tinted not blue-white
Text secondary:      #8a8884   Warm Mid -- descriptions, inactive tabs, metadata
Text tertiary:       #5c5a56   Warm Dim -- line numbers, timestamps, decorative text
Text on accent:      #ffffff   White -- text on blue accent backgrounds
Error:               #f14c4c   Diagnostic Red -- errors, git deletions, destructive actions
Success:             #73c991   Git Green -- additions, test pass, completion
Warning:             #e5c07b   Linter Amber -- warnings, caution states
Border hairline:     rgba(255,255,255,0.07)  Near-invisible panel edges
Border prominent:    rgba(255,255,255,0.12)  Card edges, input outlines, section dividers
AI glow:             rgba(76,157,243,0.08)   Inline suggestion background wash
Diff added:          rgba(115,201,145,0.15)  Git added line highlight
Diff removed:        rgba(241,76,76,0.15)    Git removed line highlight
```

---

## 2. Quick Typography Reference

```
Display:     Cursor Gothic, -apple-system, sans-serif  | 56px | weight 700 | line-height 1.15 | letter-spacing -0.02em
Section:     Cursor Gothic, -apple-system, sans-serif  | 36px | weight 700 | line-height 1.15 | letter-spacing -0.02em
Subsection:  Cursor Gothic, -apple-system, sans-serif  | 24px | weight 700 | line-height 1.20 | letter-spacing normal
Body Large:  Cursor Gothic, -apple-system, sans-serif  | 17px | weight 400 | line-height 1.50 | letter-spacing normal
Body:        Cursor Gothic, -apple-system, sans-serif  | 14px | weight 400 | line-height 1.50 | letter-spacing normal
Caption:     Cursor Gothic, -apple-system, sans-serif  | 12px | weight 400 | line-height 1.33 | letter-spacing normal
Micro:       Cursor Gothic, -apple-system, sans-serif  | 11px | weight 500 | line-height 1.25 | letter-spacing 0.02em
Code:        Berkeley Mono, JetBrains Mono, monospace   | 14px | weight 400 | line-height 1.60 | letter-spacing 0em
Code Small:  Berkeley Mono, JetBrains Mono, monospace   | 12px | weight 400 | line-height 1.60 | letter-spacing 0em
```

Key rules:
- Cursor Gothic for ALL display and UI text -- the brand's custom face
- Berkeley Mono for ALL code, terminal output, inline code, chat code blocks
- Headlines use weight 700 with tight letter-spacing (-0.02em)
- Body at 14px base (developer-dense, not marketing-generous)
- Monospace line-height is 1.60 for readability; UI text is 1.50

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Cursor visual identity:
- Background: `#14120b` (Obsidian -- warm dark, not neutral black)
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: "Build software with agents" at 56px Cursor Gothic, weight 700, line-height 1.15, letter-spacing -0.02em, color `#d7d6d5`
- Subtitle: 17px Cursor Gothic, weight 400, line-height 1.50, color `#8a8884`, max-width 560px, margin-top 20px
- CTA button: background `#4c9df3`, color `#ffffff`, 14px Cursor Gothic weight 500, padding 10px 20px, border-radius 6px, transition all 150ms ease-out
- CTA hover: background `#6bb0f7`, box-shadow `0 0 12px rgba(76,157,243,0.20)`
- Secondary button: background transparent, color `#d7d6d5`, border 1px solid `rgba(255,255,255,0.12)`, 14px weight 500, padding 10px 20px, border-radius 6px
- Secondary hover: border-color `rgba(255,255,255,0.24)`, background `rgba(255,255,255,0.04)`
- Button row: flex, gap 12px, margin-top 32px
- Optional: subtle gradient accent line above hero -- `linear-gradient(90deg, transparent, #4c9df3, transparent)` at 1px height, opacity 0.3
- On mobile (<640px): headline 36px, subtitle 15px, section padding 64px 20px, buttons stack full-width

### Feature Card

Create a feature card with Cursor visual identity:
- Background: `#1b1913` (Sidebar warm dark)
- Border: 1px solid `rgba(255,255,255,0.07)` (hairline border)
- Border-radius: 8px
- Padding: 24px
- Box-shadow: `0 2px 8px rgba(0,0,0,0.25)` (dark-surface elevation)
- Icon area: 40px square, border-radius 8px, background `rgba(76,157,243,0.12)`, display flex, align-items center, justify-content center; icon in `#4c9df3` at 20px
- Title: 24px Cursor Gothic, weight 700, line-height 1.20, color `#d7d6d5`, margin-top 16px, margin-bottom 8px
- Description: 14px Cursor Gothic, weight 400, line-height 1.50, color `#8a8884`
- Hover state: border-color `rgba(255,255,255,0.12)`, box-shadow `0 4px 16px rgba(0,0,0,0.35)`, transform translateY(-1px), transition all 200ms
- On mobile (<640px): padding 20px, title 20px

### CTA Button Row

Create a CTA button row with Cursor visual identity:
- Layout: flex, gap 12px, align-items center
- Primary button: background `#4c9df3`, color `#ffffff`, font 14px Cursor Gothic weight 500, padding 10px 20px, border-radius 6px, border none, cursor pointer, transition all 150ms ease-out
- Primary hover: background `#6bb0f7`, box-shadow `0 0 12px rgba(76,157,243,0.20)`
- Primary active: background `#3d8de0`, transform scale(0.98)
- Secondary button: background transparent, color `#d7d6d5`, border 1px solid `rgba(255,255,255,0.12)`, font 14px weight 500, padding 10px 20px, border-radius 6px
- Secondary hover: border-color `rgba(255,255,255,0.24)`, background `rgba(255,255,255,0.04)`
- Ghost button: background transparent, color `#8a8884`, border none, font 14px weight 500, padding 10px 12px
- Ghost hover: color `#d7d6d5`
- On mobile (<640px): flex-direction column, buttons full-width

### Navigation Bar

Create a navigation bar with Cursor visual identity:
- Background: `#14120b` (Obsidian), position sticky, top 0, z-index 100
- Backdrop-filter: blur(12px), background with alpha: `rgba(20,18,11,0.85)` for scroll transparency
- Border-bottom: 1px solid `rgba(255,255,255,0.07)`
- Container: max-width 1200px, centered, padding 0 24px, height 56px, display flex, align-items center, justify-content space-between
- Logo: Cursor wordmark in Cursor Gothic, weight 700, 18px, color `#d7d6d5`, letter-spacing -0.02em
- Nav links: 14px Cursor Gothic, weight 400, color `#8a8884`, gap 24px, text-decoration none, transition color 150ms
- Nav link hover: color `#d7d6d5`
- Nav link active: color `#4c9df3`
- CTA button (right): background `#4c9df3`, color `#ffffff`, 13px Cursor Gothic weight 500, padding 8px 16px, border-radius 6px
- On mobile (<768px): nav links collapse to hamburger icon (`#8a8884`), CTA remains visible, height stays 56px

### Data Card / Metric Display

Create a metric display card with Cursor visual identity:
- Background: `#1b1913` (Sidebar)
- Border: 1px solid `rgba(255,255,255,0.07)`
- Border-radius: 8px
- Padding: 24px
- Box-shadow: `0 2px 8px rgba(0,0,0,0.25)`
- Overline label: 11px Cursor Gothic, weight 500, letter-spacing 0.06em, text-transform uppercase, color `#5c5a56`, margin-bottom 8px
- Metric value: 36px Cursor Gothic, weight 700, line-height 1.15, letter-spacing -0.02em, color `#d7d6d5`
- Metric accent variant: color `#4c9df3` for highlighted metrics
- Metric description: 14px Cursor Gothic, weight 400, line-height 1.50, color `#8a8884`, margin-top 8px
- Sparkline/chart area (optional): 48px tall, stroke `#4c9df3` at 1.5px, fill `rgba(76,157,243,0.08)`
- On mobile (<640px): metric value 28px, padding 20px

### AI Chat Panel (Brand-Specific Component)

Create an AI chat panel reflecting Cursor's core AI interaction pattern:
- Panel background: `#14120b` (Obsidian), full height, width 360px, border-left 1px solid `rgba(255,255,255,0.07)`
- Panel header: height 48px, padding 0 16px, display flex, align-items center, justify-content space-between, border-bottom 1px solid `rgba(255,255,255,0.07)`
- Header title: 13px Cursor Gothic, weight 500, color `#d7d6d5`; model selector dropdown: 12px, color `#8a8884`, background `rgba(255,255,255,0.04)`, border-radius 4px, padding 4px 8px
- Message area: flex 1, overflow-y auto, padding 16px
- User message bubble: background `#26241e`, border-radius 8px, padding 12px 16px, margin-bottom 12px, max-width 85%
- User message text: 14px Cursor Gothic, weight 400, line-height 1.50, color `#d7d6d5`
- AI message: no bubble background (flat), padding 0 0 12px 0
- AI message text: 14px Cursor Gothic, weight 400, line-height 1.50, color `#d7d6d5`
- AI code block: background `#1b1913`, border 1px solid `rgba(255,255,255,0.07)`, border-radius 6px, padding 12px 16px, font 13px Berkeley Mono, line-height 1.60, color `#d7d6d5`, overflow-x auto
- Code block header: 11px Berkeley Mono, weight 400, color `#5c5a56`, padding 8px 16px, border-bottom 1px solid `rgba(255,255,255,0.07)`, display flex, justify-content space-between
- Copy button in code block: 11px, color `#5c5a56`, hover color `#d7d6d5`, cursor pointer
- AI thinking indicator: three dots pulsing in `#4c9df3`, opacity cycling 0.3 to 1.0, animation 1.4s infinite
- Input area: position sticky, bottom 0, padding 12px 16px, border-top 1px solid `rgba(255,255,255,0.07)`, background `#14120b`
- Input field: background `#1b1913`, border 1px solid `rgba(255,255,255,0.07)`, border-radius 8px, padding 10px 14px, font 14px Cursor Gothic, color `#d7d6d5`, placeholder color `#5c5a56`
- Input focus: border-color `#4c9df3`, box-shadow `0 0 0 2px rgba(76,157,243,0.15)`
- Send button: 32px circle, background `#4c9df3`, color `#ffffff`, border-radius 50%, position absolute right 8px in input
- Send button disabled (empty input): background `#26241e`, color `#5c5a56`
- On mobile (<768px): panel goes full-width as overlay, height 100vh, border-left none

### Inline Code Suggestion (Brand-Specific Component)

Create an inline code suggestion overlay reflecting Cursor's Tab completion pattern:
- Context: rendered inside a code editor area with background `#14120b`, font 14px Berkeley Mono, line-height 1.60
- Ghost text (AI suggestion): color `rgba(138,136,132,0.5)` -- dimmed secondary, clearly distinguished from typed code
- Ghost text on Tab accept: color transitions from ghost to `#d7d6d5` over 150ms
- Suggestion tooltip: appears 4px below ghost text end, background `#26241e`, border 1px solid `rgba(255,255,255,0.12)`, border-radius 6px, padding 6px 10px, box-shadow `0 4px 16px rgba(0,0,0,0.35)`
- Tooltip text: 11px Berkeley Mono, color `#8a8884`; keyboard shortcut: `Tab` badge in 10px Berkeley Mono, background `rgba(255,255,255,0.07)`, color `#d7d6d5`, padding 2px 6px, border-radius 3px, margin-left 6px
- Multi-line suggestion: highlighted block background `rgba(76,157,243,0.08)` (AI glow), left border 2px solid `rgba(76,157,243,0.30)`, padding-left 8px
- Accept animation: ghost text color fills in left-to-right over 120ms, the AI glow wash fades out over 200ms
- Dismiss: ghost text fades out in 80ms on Escape or continued typing in different direction

---

## 4. Iteration Guide

1. **Warm dark, never neutral.** The background is `#14120b` -- it has a brown/amber undertone, not a blue or neutral cast. Every gray in the system carries warmth. If you see `#1a1a1a`, `#333333`, or any blue-gray, replace it. `#1b1913`, `#26241e`, `#8a8884` are the palette.

2. **Blue accent is intelligence signal.** `#4c9df3` appears on AI-driven interactions, active states, and primary CTAs. It does NOT fill backgrounds. Use `rgba(76,157,243,0.12)` for selected-row washes and `rgba(76,157,243,0.08)` for suggestion highlights. The solid blue is for buttons and focused inputs only.

3. **Monospace + Gothic pairing is the identity.** Berkeley Mono for anything that is or represents code. Cursor Gothic for everything else. Never use monospace for labels or Gothic for code. The two typefaces meeting is what makes Cursor feel like an IDE that also has a brand.

4. **Developer-dense spacing.** Base text is 14px, not 16px. Padding is 24px on cards, not 32px. Nav height is 56px, not 64px. This density signals "tool for professionals" rather than "marketing page." Only marketing hero sections get generous spacing (120px+).

5. **Dark-surface shadows must be heavy.** On `#14120b`, a shadow at `rgba(0,0,0,0.05)` is invisible. Use `rgba(0,0,0,0.25)` minimum for level-1 and `rgba(0,0,0,0.40)` for modals. The `glow-accent` shadow (`rgba(76,157,243,0.20)`) is the only colored shadow in the system.

6. **Every component should feel like part of a code editor.** Hairline borders (`rgba(255,255,255,0.07)`), compact padding, monospace in code blocks, warm-dim tertiary text for metadata. If it could belong in any SaaS dashboard, it is not Cursor enough. Add the code-editor density and the warm-dark warmth.
