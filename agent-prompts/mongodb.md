# MongoDB -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect MongoDB-branded components.
Aesthetic: developer-focused data platform -- dark ink surfaces, electric green accents, monospace precision.

Design system: LeafyGreen (mongodb.design). Fonts: MongoDB Value Serif (display), Euclid Circular A (body/UI), Source Code Pro (code). Palette anchored on MDB Ink (#001E2B) and LeafyGreen (#00ED64).

---

## 1. Quick Color Reference

```
Light mode:
  Surface (page bg):       #ffffff         white
  Surface secondary:       #F9FBFA         gray.light3 — cards, panels
  Accent (dark):           #00684A         green.dark2 — buttons on light bg
  Accent hover:            #00A35C         green.dark1 — button hover
  Text primary:            #001E2B         MDB Ink / LeafyGreen black
  Text secondary:          #5C6C75         gray.dark1
  Text disabled:           #889397         gray.base
  Link:                    #016BF8         blue.base
  Border:                  #E8EDEB         gray.light2
  Focus ring:              #0498EC         blue.light1

Dark mode (Atlas / shell):
  Surface:                 #001E2B         MDB Ink
  Surface secondary:       #112733         gray.dark4
  Surface tertiary:        #1C2D38         gray.dark3
  Accent:                  #00ED64         green.base — CTAs on dark bg
  Text primary:            #E8EDEB         gray.light2
  Text secondary:          #C1C7C6         gray.light1
  Border:                  #3D4F58         gray.dark2

Semantic:
  Error:                   #DB3030         red.base
  Error bg:                #FFEAE5         red.light3
  Success:                 #00684A         green.dark2
  Success bg:              #E3FCF7         green.light3
  Warning:                 #FFC010         yellow.base
  Warning bg:              #FEF7DB         yellow.light3
  Info:                    #016BF8         blue.base
  Info bg:                 #E1F7FF         blue.light3
```

---

## 2. Quick Typography Reference

```
Display:     'MongoDB Value Serif', Georgia, serif            | 48px | weight 700 | line-height 1.25
H1:          'Euclid Circular A', system sans-serif           | 36px | weight 600 | line-height 1.25
H2:          'Euclid Circular A', system sans-serif           | 28px | weight 600 | line-height 1.25
H3:          'Euclid Circular A', system sans-serif           | 24px | weight 600 | line-height 1.25
Body 1:      'Euclid Circular A', system sans-serif           | 16px | weight 400 | line-height 1.50
Body 2:      'Euclid Circular A', system sans-serif           | 14px | weight 400 | line-height 1.50
Caption:     'Euclid Circular A', system sans-serif           | 12px | weight 500 | line-height 1.25
Overline:    'Euclid Circular A', system sans-serif           | 11px | weight 600 | line-height 1.25 | uppercase, letter-spacing 0.5px
Code:        'Source Code Pro', monospace                     | 14px | weight 400 | line-height 1.60
Code small:  'Source Code Pro', monospace                     | 12px | weight 400 | line-height 1.60
```

Key rules:
- MongoDB Value Serif for marketing display headlines only (H1/H2 on landing pages)
- Euclid Circular A for all product UI: headings, body, buttons, labels, nav
- Source Code Pro for all code: queries, JSON documents, shell output, inline code
- Never use Source Code Pro for sentences or paragraphs -- only values, keys, and snippets
- Under 13px bold text, prefer Source Code Pro over Euclid Circular A for legibility

---

## 3. Example Component Prompts

### Atlas Navigation Bar

Create a navigation bar with MongoDB Atlas visual identity:
- Background: `#001E2B` (MDB Ink), position sticky, top 0, z-index 100
- Height: 56px, max-width 100%, padding 0 16px
- Logo: MongoDB leaf mark in `#00ED64` (green.base), 28px height, left-aligned
- Nav links: 14px Euclid Circular A weight 500, color `#C1C7C6` (gray.light1), gap 24px
- Active nav link: color `#ffffff`, border-bottom 2px solid `#00ED64`, padding-bottom 4px
- Nav link hover: color `#E8EDEB` (gray.light2), transition 150ms
- Right section: user avatar 32px circle, settings icon 20px in `#889397`
- CTA button (right): background `#00ED64`, color `#001E2B`, 13px weight 600, padding 6px 12px, border-radius 6px
- CTA hover: background `#00A35C`
- On mobile (<768px): hamburger menu icon replaces nav links, logo and CTA remain visible

### Hero Section (Marketing)

Create a hero section with MongoDB marketing visual identity:
- Background: `#001E2B` (MDB Ink) -- MongoDB marketing pages use dark hero
- Container: max-width 1200px, centered, padding 120px 64px
- Headline: 48px MongoDB Value Serif, weight 700, line-height 1.25, color `#ffffff`
- Subtitle: 18px Euclid Circular A, weight 400, line-height 1.50, color `#C1C7C6`, max-width 560px, margin-top 16px
- CTA button: background `#00ED64`, color `#001E2B`, 16px Euclid Circular A weight 600, padding 12px 24px, border-radius 6px
- CTA hover: background `#00A35C`
- Secondary button: background transparent, border 1px solid `#3D4F58`, color `#E8EDEB`, same size, border-radius 6px
- Secondary hover: border-color `#889397`
- Button row: flex, gap 12px, margin-top 32px
- Optional: code snippet preview block — background `#112733`, border 1px solid `#3D4F58`, border-radius 8px, padding 24px, Source Code Pro 14px in `#E8EDEB`, with syntax-colored keywords (`#00ED64` for strings, `#0498EC` for keys)
- On mobile (<640px): headline 32px, padding 64px 20px, buttons stack full-width

### Feature Card

Create a feature card with MongoDB visual identity:
- Background: `#ffffff` on light pages, `#112733` on dark pages
- Border: 1px solid `#E8EDEB` (light) or 1px solid `#3D4F58` (dark)
- Border-radius: 8px
- Padding: 32px
- Icon area: 40px square, background `#E3FCF7` (green.light3), border-radius 8px, centered icon in `#00684A`
- Title: 20px Euclid Circular A, weight 600, line-height 1.25, color `#001E2B` (light) or `#E8EDEB` (dark), margin-top 20px
- Description: 14px Euclid Circular A, weight 400, line-height 1.50, color `#5C6C75` (light) or `#C1C7C6` (dark), margin-top 8px
- Hover: border-color transitions to `#889397` (light) or `#5C6C75` (dark), 150ms ease
- On mobile (<640px): padding 24px, title 18px

### CTA Button Row

Create a CTA button row with MongoDB visual identity:
- Layout: flex, gap 12px, align-items center
- Primary (dark bg): background `#00ED64`, color `#001E2B`, 14px Euclid Circular A weight 600, padding 10px 20px, border-radius 6px, border none
- Primary hover: background `#00A35C`
- Primary (light bg): background `#00684A`, color `#ffffff`, same dimensions
- Primary (light bg) hover: background `#023430` (green.dark3)
- Secondary: background transparent, color `#001E2B` (light) or `#E8EDEB` (dark), border 1px solid `#E8EDEB` (light) or `#3D4F58` (dark), same padding, border-radius 6px
- Secondary hover: border-color darkens one step
- Danger: background `#DB3030`, color `#ffffff`, same dimensions
- Danger hover: background `#970606` (red.dark2)
- Disabled state: opacity 0.4, cursor not-allowed
- Focus ring: 2px solid `#0498EC`, offset 2px
- On mobile (<640px): flex-direction column, buttons stretch full-width

### Query Result Panel / Document View

Create a document viewer panel with MongoDB Atlas visual identity:
- Container: background `#001E2B` (MDB Ink), border-radius 8px, overflow hidden
- Toolbar: height 40px, background `#112733`, border-bottom 1px solid `#3D4F58`, padding 0 12px, flex, align-items center
- Toolbar label: 12px Euclid Circular A weight 600, color `#889397`, uppercase, letter-spacing 0.5px (e.g., "DOCUMENT" or "QUERY RESULTS")
- Toolbar actions: icon buttons 28px square, color `#889397`, hover color `#C1C7C6`, gap 4px
- Document body: padding 16px, overflow-y auto
- JSON rendering: Source Code Pro 14px, line-height 1.60, color `#E8EDEB`
  - Keys: `#0498EC` (blue.light1)
  - Strings: `#00ED64` (green.base)
  - Numbers: `#B45AF2` (purple.base)
  - Booleans/null: `#FFC010` (yellow.base)
  - ObjectId: `#5C6C75` (gray.dark1) italic
  - Brackets/braces: `#889397` (gray.base)
  - Commas/colons: `#5C6C75`
- Line numbers: 12px Source Code Pro, color `#3D4F58`, padding-right 12px, text-align right, user-select none
- Selected line: background `rgba(0, 237, 100, 0.06)` — subtle green highlight
- Expand/collapse toggle: caret icon 12px in `#889397`, rotate 90deg when expanded, transition 100ms
- Scrollbar: 6px width, thumb `#3D4F58`, track transparent, border-radius 3px
- Empty state: centered text "No documents found", 14px Euclid Circular A, color `#5C6C75`, with a muted leaf icon 48px in `#3D4F58`

### Aggregation Pipeline Stage

Create an aggregation pipeline stage card with MongoDB visual identity:
- Container: background `#112733`, border 1px solid `#3D4F58`, border-radius 8px, margin-bottom 8px
- Stage header: height 40px, padding 0 12px, flex, align-items center, justify-content space-between, cursor pointer
- Stage number: 12px Source Code Pro weight 600, color `#00ED64`, background `rgba(0, 237, 100, 0.1)`, padding 2px 8px, border-radius 4px (e.g., "1")
- Stage operator: 14px Source Code Pro weight 600, color `#E8EDEB`, margin-left 12px (e.g., "$match")
- Collapse icon: 16px, color `#889397`, transform rotate on expand
- Stage body (expanded): padding 12px, border-top 1px solid `#3D4F58`
- Code editor area: Source Code Pro 14px, color `#E8EDEB`, background `#1C2D38`, border-radius 4px, padding 12px, min-height 80px
- Add stage button: dashed border 1px `#3D4F58`, border-radius 8px, height 40px, flex center, 13px Euclid Circular A weight 500, color `#889397`, hover border-color `#00ED64` and color `#00ED64`
- Connector line: 2px solid `#3D4F58`, centered, height 8px between stages

---

## 4. Iteration Guide

1. **Dark ink is the product canvas.** Atlas, shell, and developer tools use `#001E2B` as the primary surface. Light mode (`#ffffff`) is for marketing pages and documentation. Never invert this: dark mode is not an alternative in MongoDB -- it is the native environment for data tools.

2. **Green is signal, not decoration.** `#00ED64` on dark surfaces and `#00684A` on light surfaces mark interactive elements and success states. Never flood a panel with green backgrounds. The accent earns its impact through scarcity.

3. **Source Code Pro is for data, Euclid is for UI.** Every query, JSON document, ObjectId, collection name, and shell command uses Source Code Pro. Every button label, heading, paragraph, and nav link uses Euclid Circular A. Mixing them (e.g., Source Code Pro for a heading, Euclid for an ObjectId) breaks the visual grammar.

4. **Respect the LeafyGreen border-radius system.** Buttons and inputs get 6px. Cards and modals get 8px. Featured containers get 12px. Badges and chips get 4px or pill (9999px). Never use round corners above 12px on standard components.

5. **Use semantic colors for status, not brand green.** Error is red (`#DB3030`), warning is yellow (`#FFC010`), info is blue (`#016BF8`), success is green (`#00684A`). Do not use the brand green accent for success badges -- use the darker green.dark2 to distinguish "success feedback" from "interactive accent."

6. **Build for information density.** MongoDB users work with large datasets. Panels should support dense table views (14px body, 12px captions, 8px row padding). Do not over-space developer tools the way you would a marketing page. Generous whitespace is for hero sections, not for the data grid.

7. **Code blocks have their own atmosphere.** Inside code panels, the background drops to `#112733` or `#1C2D38`, syntax colors follow the LeafyGreen semantic mapping (blue for keys, green for strings, purple for numbers, yellow for booleans), and line numbers are always present in `#3D4F58`.

8. **Focus states are blue, not green.** Keyboard focus uses `#0498EC` (blue.light1) as a 2px ring with 2px offset. This separates accessibility focus from interactive brand accent, preventing confusion between "focused" and "active."

9. **Every component should feel like it belongs in Atlas.** The design language is a developer console, not a consumer app. Prioritize clarity, density, and precision over playfulness. If a component looks like it could ship in Notion, it does not look like MongoDB.
