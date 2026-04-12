# Component Visual Specs: Dual-Layer Model

This document fuses **behavior rules** (how to use components) with **visual specs** (how they look across brands). Every visual value references a design token, not a hardcoded value. The four reference brands -- Claude, Stripe, Linear, Vercel -- represent distinct points in the design space.

Token notation: `{category.token-name}` references the brand's token system. Actual values vary per brand.

---

## Component: Button

### Layer 1: Behavior Rules

_Source: components.md_

- **Button labels**: Verb-first -- "Save Settings", "Send Message", "Create Account". Never just "Submit".
- **ONE primary button** per section. Secondary actions are visually muted (ghost/outline).
- **Disabled states**: Must look visually non-interactive. Reduced opacity + semantic indication.
- **Touch targets**: Minimum 44x44px effective area on mobile.

### Layer 2: Visual Spec Template

#### Primary CTA Button

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| bg | `{color.accent}` | `#c96442` (terracotta) | `#533afd` (purple) | `#5e6ad2` (indigo) | `#171717` (near-black) |
| text | `{color.text-on-accent}` | `#faf9f5` (ivory) | `#ffffff` | `#ffffff` | `#ffffff` |
| font-family | `{font.ui}` | Anthropic Sans | sohne-var | Inter Variable | Geist |
| font-size | `{type.button}` | 16px | 16px | 14px | 14px |
| font-weight | `{type.button-weight}` | 400-500 | 400 | 510 | 500 |
| font-features | `{type.features}` | -- | `"ss01"` | `"cv01","ss03"` | `"liga"` |
| padding-y | `{spacing.button-y}` | 9.6px | 8px | 8px | 8px |
| padding-x | `{spacing.button-x}` | 16.8px | 16px | 16px | 16px |
| border-radius | `{radius.button}` | 8-12px | 4px | 6px | 6px |
| shadow | `{shadow.button}` | ring `0 0 0 1px {color.accent}` | none | none | none |
| hover | `{interaction.hover}` | darken 8% | `#4434d4` (darken) | `#828fff` (lighten) | invert to white bg/dark text |
| transition | `{motion.button}` | background 150ms | background 150ms | background 150ms | background 150ms |

#### Secondary Button

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| bg | `{color.surface-interactive}` | `#e8e6dc` (warm sand) | transparent | `rgba(255,255,255,0.02)` | `#ffffff` |
| text | `{color.text-secondary}` | `#4d4c48` | `#533afd` | `#e2e4e7` | `#171717` |
| border | `{border.interactive}` | none (ring-shadow) | `1px solid #b9b9f9` | `1px solid rgb(36,40,44)` | shadow `rgb(235,235,235) 0 0 0 1px` |
| border-radius | `{radius.button}` | 8px | 4px | 6px | 6px |
| shadow | `{shadow.button-secondary}` | ring `0 0 0 1px #d1cfc5` | none | `rgba(0,0,0,0.1) 0 4px 12px` (focus) | ring `rgb(235,235,235) 0 0 0 1px` |
| hover-bg | `{interaction.hover-secondary}` | subtle darken | `rgba(83,58,253,0.05)` | opacity increase | `#171717` (invert) |

#### Variant Matrix

| Variant | Pattern | Brands Using | Notes |
|---------|---------|-------------|-------|
| Filled primary | Solid accent bg, white text | All four | Universal -- the CTA |
| Ghost / outline | Transparent bg, accent text, visible border | Stripe, Linear | Border-defined, no fill |
| Ring-shadow | Shadow `0 0 0 1px` mimics border | Claude, Vercel | Shadow-layer border, not CSS border |
| Surface-tinted | Warm/neutral bg, muted text | Claude (`#e8e6dc`) | Workhorse secondary, no border needed |
| Dark-inverted | Dark bg, light text for light surfaces | Claude (`#30302e`), Vercel (`#171717`) | High-contrast inversion |
| Near-transparent | `rgba(255,255,255,0.02-0.05)` bg | Linear | Dark-mode-native ghost |
| Pill | `border-radius: 9999px` | Vercel (badges), Linear (filters) | NOT for primary CTA -- tags/filters only |

#### Cross-Brand Observations

**Consistent across all four:**
- Primary CTA uses the single brand accent color
- Button font-size clusters at 14-16px
- Padding is compact: 8px vertical, 16px horizontal
- One primary per section, secondaries visually recede

**Key divergences:**
- **Radius**: Claude rounds generously (8-12px), Stripe stays tight (4px), Linear/Vercel land at 6px. Radius encodes brand personality: warmer = rounder.
- **Border technique**: Claude and Vercel use shadow-as-border (`0 0 0 1px`). Stripe and Linear use traditional CSS border. Same visual outcome, different rendering layer.
- **Weight hierarchy**: Stripe uses 300 for CTA headlines (whisper authority). Others use 400-600 for button text. Stripe's lightness is intentional anti-convention.
- **Hover model**: Claude/Stripe darken on hover. Linear/Vercel lighten or invert. Dark-mode-native brands lighten; light-canvas brands darken.

---

## Component: Card

### Layer 1: Behavior Rules

_Source: components.md_

- **Strict hierarchy**: Media -> Title -> Meta/Subtitle -> Action. No exceptions.
- **Choose shadow OR border**, not both. (Note: Vercel and Claude deliberately violate this with shadow-as-border, which IS the border.)
- **Empty states**: NEVER just "No items found." Always: icon/illustration + helpful headline + clear primary CTA.
- **Loading states**: Skeleton/shimmer for >1s. Reserve space to prevent layout shift.

### Layer 2: Visual Spec Template

#### Standard Content Card

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| bg | `{color.surface-card}` | `#faf9f5` (ivory) | `#ffffff` | `rgba(255,255,255,0.02)` | `#ffffff` |
| border | `{border.card}` | `1px solid #f0eee6` | `1px solid #e5edf5` | `1px solid rgba(255,255,255,0.08)` | none (shadow-border) |
| border-radius | `{radius.card}` | 8px | 5-6px | 8px | 8px |
| shadow | `{shadow.card}` | `rgba(0,0,0,0.05) 0 4px 24px` | `rgba(50,50,93,0.25) 0 30px 45px -30px, rgba(0,0,0,0.1) 0 18px 36px -18px` | `rgba(0,0,0,0.2) 0 0 0 1px` | `rgba(0,0,0,0.08) 0 0 0 1px, rgba(0,0,0,0.04) 0 2px 2px, #fafafa 0 0 0 1px` |
| padding | `{spacing.card-internal}` | 24-32px | 24-32px | 20-24px | 24-32px |
| title-font | `{font.heading}` | Anthropic Serif | sohne-var | Inter Variable | Geist |
| title-size | `{type.card-title}` | 25px | 22px | 20px | 24px |
| title-weight | `{type.card-title-weight}` | 500 | 300 | 590 | 600 |
| title-color | `{color.text-heading}` | `#141413` | `#061b31` | `#f7f8f8` | `#171717` |
| body-size | `{type.body}` | 15-16px | 16px | 15px | 16px |
| body-color | `{color.text-body}` | `#5e5d59` | `#64748d` | `#8a8f98` | `#4d4d4d` |
| hover | `{interaction.card-hover}` | ring shadow intensifies | shadow layers intensify | bg opacity increase | shadow intensification |

#### Featured / Hero Card

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| border-radius | `{radius.card-featured}` | 16-32px | 8px | 12px | 12px |
| shadow | `{shadow.card-featured}` | whisper `rgba(0,0,0,0.05) 0 4px 24px` | blue-tinted multi-layer | multi-shadow stack | full stack + inner `#fafafa` ring |
| media-radius | `{radius.media}` | 16-32px | 4-6px | 12px top-rounded | 12px top-rounded |

#### Variant Matrix

| Variant | Pattern | Brands Using | Notes |
|---------|---------|-------------|-------|
| Border-contained | Thin solid border, no shadow | Claude (light), Stripe, Linear | Traditional containment |
| Shadow-bordered | `0 0 0 1px` shadow replaces border | Claude (interactive), Vercel | Border in shadow layer |
| Shadow-elevated | Multi-layer shadow stack | Stripe (blue-tinted), Vercel (neutral) | Depth through shadow parallax |
| Luminance-stepped | Background opacity defines depth | Linear | Dark-mode depth via `rgba(255,255,255, 0.02-0.05)` |
| Dark/light alternating | Section-level card by bg color swap | Claude, Stripe | Entire sections change ambient tone |
| Inner-glow | Inner `#fafafa` shadow ring | Vercel | Card "glows from within" |

#### Cross-Brand Observations

**Consistent across all four:**
- Internal padding clusters at 24-32px
- Title + body text two-color hierarchy (heading color + muted body color)
- Hover increases visual weight (shadow, opacity, or ring intensity)
- Featured cards use larger radius than standard cards

**Key divergences:**
- **Shadow philosophy**: Stripe uses brand-tinted shadows (`rgba(50,50,93,...)`). Claude uses warm-toned ring shadows. Linear uses luminance stepping. Vercel uses architectural multi-layer stacks. The shadow system IS the brand's depth personality.
- **Border color temperature**: Claude's borders are warm cream (`#f0eee6`). Stripe's are cool blue-gray (`#e5edf5`). Linear's are transparent white. Vercel eliminates borders entirely. Border temperature tracks brand warmth.
- **Title weight**: Stripe at 300 (whisper). Claude at 500 (medium serif). Linear at 590 (strong). Vercel at 600 (bold). Stripe is the outlier -- its lightness reads as luxury.

---

## Component: Form Input

### Layer 1: Behavior Rules

_Source: components.md_

- **Single-column layouts** for forms. Labels above inputs.
- **Validation**: On blur, not keystroke. Error below the field with recovery path.
- **Required fields**: Marked with asterisk or explicit indicator.
- **Helper text**: Persistent below complex inputs, not just placeholder.
- **Error handling**: Auto-focus first invalid field on submit error. Error summary with anchor links for multiple errors.
- **Long forms**: Auto-save drafts. Confirm before dismissing unsaved changes. Multi-step forms show progress.
- **Disabled states**: Must look visually non-interactive. Reduced opacity + semantic indication.

### Layer 2: Visual Spec Template

#### Text Input

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| bg | `{color.input-bg}` | `#ffffff` or `#faf9f5` | `#ffffff` | `rgba(255,255,255,0.02)` | `#ffffff` |
| text | `{color.text-input}` | `#141413` | `#061b31` | `#d0d6e0` | `#171717` |
| placeholder | `{color.text-placeholder}` | `#87867f` (stone) | `#64748d` (slate) | `#8a8f98` (tertiary) | `#808080` (gray-400) |
| border | `{border.input}` | warm borders | `1px solid #e5edf5` | `1px solid rgba(255,255,255,0.08)` | shadow `rgba(0,0,0,0.08) 0 0 0 1px` |
| border-radius | `{radius.input}` | 12px | 4px | 6px | 6px |
| padding-y | `{spacing.input-y}` | 1.6px (very compact) | 8px | 12px | 8px |
| padding-x | `{spacing.input-x}` | 12px | 12px | 14px | 12px |
| focus-ring | `{color.focus}` | `#3898ec` (blue) | `#533afd` (purple) | multi-layer shadow stack | `hsla(212,100%,48%,1)` (blue) |
| focus-style | `{border.focus}` | border-color change | `1px solid #533afd` | shadow intensifies | `2px solid` outline |
| label-font | `{font.ui}` | Anthropic Sans | sohne-var | Inter Variable | Geist |
| label-size | `{type.label}` | 14px | 14px | 14px | 14px |
| label-weight | `{type.label-weight}` | 400-500 | 400 | 510 | 500 |
| label-color | `{color.text-label}` | `#141413` | `#273951` | `#d0d6e0` | `#171717` |
| error-color | `{color.error}` | `#b53333` | -- (inferred red) | -- (inferred red) | -- (inferred red) |

#### Variant Matrix

| Variant | Pattern | Brands Using | Notes |
|---------|---------|-------------|-------|
| Traditional border | CSS border, color change on focus | Claude, Stripe, Linear | Standard approach |
| Shadow-border | `0 0 0 1px` shadow replaces border | Vercel | Consistent with card system |
| Brand-tinted focus | Focus ring matches brand accent | Stripe (`#533afd`) | Focus IS the brand color |
| Accessibility focus | Standard blue focus ring, sole cool color | Claude (`#3898ec`), Vercel (blue) | Blue reserved purely for a11y |
| Compact vertical | Minimal vertical padding | Claude (1.6px) | Tight, editorial density |
| Standard vertical | 8-12px vertical padding | Stripe, Linear, Vercel | Comfortable touch targets |

#### Cross-Brand Observations

**Consistent across all four:**
- Labels above inputs, 14px size
- Placeholder text is a muted version of body text color
- Focus state is visually distinct from resting state
- Border-radius matches the brand's button radius

**Key divergences:**
- **Focus ring color**: Claude and Vercel use standard blue (accessibility-only color). Stripe uses its brand purple. Linear uses shadow layers. The choice signals whether focus is a brand moment or an a11y utility.
- **Input radius**: Claude at 12px (generous) vs. Stripe at 4px (tight). This mirrors button radius -- the input radius = the button radius in each system.
- **Vertical padding**: Claude is radically compact (1.6px). The other three cluster at 8-12px. Claude prioritizes editorial density over comfort.
- **Border technique**: Vercel uses shadow-borders on inputs too -- the shadow-as-border philosophy is universal in their system, not card-specific.

---

## Component: Navigation

### Layer 1: Behavior Rules

_Source: components.md_

- **Top nav**: Max 5-7 links. Clear active indicator. Hamburger only on mobile, NEVER desktop.
- **Bottom nav (mobile)**: Max 5 items. Icon + text label. Top-level screens only.
- **Adaptive**: Desktop (>=1024px) -> sidebar nav. Mobile -> bottom/top nav.
- **Search**: Easily reachable. Provide recent/suggested queries.
- **Consistency**: Same nav placement across all pages.
- **Back behavior**: Predictable and consistent. Preserve scroll position, filter state, input.
- **Deep linking**: All key screens reachable via URL/deep link.

### Layer 2: Visual Spec Template

#### Sticky Top Navigation

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| bg | `{color.nav-bg}` | warm surface (parchment/ivory) | `#ffffff` with blur | `#0f1011` (panel dark) | `#ffffff` |
| position | `{layout.nav-position}` | sticky top | sticky top + blur backdrop | sticky top | sticky top |
| border-bottom | `{border.nav}` | `1px solid #f0eee6` (light) / `#30302e` (dark) | none (shadow) | `1px solid rgba(255,255,255,0.05)` | shadow `rgba(0,0,0,0.08) 0 0 0 1px` |
| link-font | `{font.ui}` | Anthropic Sans | sohne-var | Inter Variable | Geist |
| link-size | `{type.nav-link}` | 17px | 14px | 13-14px | 14px |
| link-weight | `{type.nav-weight}` | 400-500 | 400 | 510 | 500 |
| link-color | `{color.text-nav}` | `#141413` / `#5e5d59` | `#061b31` | `#d0d6e0` | `#171717` |
| link-features | `{type.features}` | -- | `"ss01"` | `"cv01","ss03"` | `"liga"` |
| active-indicator | `{interaction.nav-active}` | text color shift to foreground-primary | underline or weight shift | text lightens to `#f7f8f8` | weight 600 or underline |
| hover | `{interaction.nav-hover}` | color shift, no decoration | color shift | lighten text | color shift |
| cta-variant | `{component.nav-cta}` | Terracotta brand button | Purple button | Brand indigo button | Dark pill button |
| cta-position | `{layout.nav-cta-position}` | right-aligned | right-aligned | right-aligned | right-aligned |
| logo-position | `{layout.logo}` | left-aligned (wordmark) | left-aligned (wordmark) | left-aligned (icon mark) | left-aligned (wordmark) |
| mobile-trigger | `{component.mobile-menu}` | hamburger | hamburger | hamburger at 768px | hamburger |
| nav-radius | `{radius.nav}` | -- | 6px on container | -- | -- |
| backdrop-filter | `{effect.nav-blur}` | -- | `blur(12px)` | -- | -- |

#### Variant Matrix

| Variant | Pattern | Brands Using | Notes |
|---------|---------|-------------|-------|
| Warm surface nav | Nav bg matches page canvas tone | Claude (parchment) | Nav blends into page atmosphere |
| Glass nav | White bg + backdrop-filter blur | Stripe | Semi-transparent, floating feel |
| Dark native nav | Near-black bg matching page | Linear | Nav is part of dark canvas |
| Clean white nav | Pure white, shadow-border bottom | Vercel | Maximum contrast, minimal chrome |
| Command palette | Keyboard shortcut search (`Cmd+K`) | Linear | Search as command interface |
| Pill CTA | CTA button with pill radius | Vercel | Dark pill as action anchor |

#### Cross-Brand Observations

**Consistent across all four:**
- Sticky top positioning
- Logo left, CTA right
- Max 5-7 primary links
- Hamburger on mobile
- Link size clusters at 14-17px

**Key divergences:**
- **Nav link size**: Claude at 17px (editorial) vs. others at 13-14px (compact). Claude's nav reads like body text; others read like UI labels.
- **Background treatment**: Each nav bg matches its page canvas -- there is no "neutral" nav. The nav IS the brand's spatial container.
- **CTA style in nav**: Claude uses brand-colored button. Stripe uses brand-colored button. Vercel inverts to dark pill. Linear uses brand-colored button. The nav CTA is always the primary CTA variant.
- **Backdrop effects**: Only Stripe uses blur/glass. The others use opaque backgrounds. Blur adds perceived depth but requires careful performance consideration.

---

## Component: Table

### Layer 1: Behavior Rules

_Source: components.md_

- **Right-align numbers**. Always.
- **Distinct sticky headers**. Headers must be visually differentiated from body rows.
- **Sortable columns**: Indicated visually with directional icons.
- **Empty states**: NEVER just "No items found." Always: icon/illustration + helpful headline + clear primary CTA.
- **Loading states**: Skeleton/shimmer for >1s. Reserve space to prevent layout shift.
- **Responsive**: Horizontal scroll on mobile for data tables (from responsive behavior sections).

### Layer 2: Visual Spec Template

#### Data Table

| Property | Token Reference | Claude | Stripe | Linear | Vercel |
|----------|----------------|--------|--------|--------|--------|
| header-bg | `{color.surface-header}` | `#f5f4ed` or `#faf9f5` | `#ffffff` | `#0f1011` / `rgba(255,255,255,0.02)` | `#ffffff` or `#fafafa` |
| header-text | `{color.text-heading}` | `#141413` | `#061b31` | `#f7f8f8` | `#171717` |
| header-weight | `{type.header-weight}` | 500 | 400 | 510-590 | 500-600 |
| header-size | `{type.table-header}` | 14px | 13-14px | 13px | 14px |
| header-font | `{font.ui}` | Anthropic Sans | sohne-var | Inter Variable | Geist |
| header-features | `{type.features}` | -- | `"ss01"` | `"cv01","ss03"` | `"liga"` |
| row-bg | `{color.surface-row}` | `#faf9f5` (ivory) | `#ffffff` | `rgba(255,255,255,0.02)` | `#ffffff` |
| row-bg-alt | `{color.surface-row-alt}` | `#f5f4ed` (parchment) | `#f6f9fc` (faint blue) | `rgba(255,255,255,0.04)` | `#fafafa` |
| row-text | `{color.text-body}` | `#5e5d59` | `#64748d` | `#d0d6e0` | `#4d4d4d` |
| row-text-size | `{type.table-body}` | 15px | 14px | 14px | 14px |
| row-border | `{border.row-divider}` | `1px solid #f0eee6` | `1px solid #e5edf5` | `1px solid rgba(255,255,255,0.05)` | shadow `rgba(0,0,0,0.08) 0 0 0 1px` or `1px solid #ebebeb` |
| number-font | `{font.mono}` (for tabular data) | Anthropic Mono | sohne-var + `"tnum"` | Berkeley Mono | Geist Mono |
| number-features | `{type.number-features}` | -- | `"tnum"` | -- | `"tnum"` |
| number-align | `{layout.number-align}` | right | right | right | right |
| sort-icon | `{icon.sort}` | inline SVG | inline SVG | inline SVG | inline SVG |
| hover-row | `{interaction.row-hover}` | subtle bg shift | subtle bg shift | bg opacity increase | subtle bg shift |
| cell-padding-y | `{spacing.cell-y}` | 8-12px | 8-10px | 8-12px | 8-12px |
| cell-padding-x | `{spacing.cell-x}` | 12-16px | 12-16px | 12-16px | 12-16px |

#### Variant Matrix

| Variant | Pattern | Brands Using | Notes |
|---------|---------|-------------|-------|
| Bordered rows | Horizontal divider between rows | All four | Universal baseline |
| Striped rows | Alternating row background | All four (optional) | Subtle tint, not strong color |
| Warm borders | Border color has warm undertone | Claude (`#f0eee6`) | Borders carry brand temperature |
| Cool borders | Border color has blue/gray undertone | Stripe (`#e5edf5`) | Reinforces cool palette |
| Transparent borders | Semi-transparent white on dark | Linear | Dark-mode-native dividers |
| Shadow-borders | Shadow replaces CSS border | Vercel | Consistent with shadow system |
| Tabular numerals | OpenType `"tnum"` for number columns | Stripe, Vercel | Monospaced digits for alignment |
| Monospace numbers | Mono font for data columns | Claude (Anthropic Mono), Linear (Berkeley Mono) | Full mono font, not just features |

#### Cross-Brand Observations

**Consistent across all four:**
- Right-aligned numbers
- Header visually distinct from body (weight, color, or background)
- Horizontal row dividers
- Cell padding in the 8-16px range
- Hover state on rows

**Key divergences:**
- **Number treatment**: Stripe and Vercel use OpenType `"tnum"` on the same font. Claude and Linear switch to a dedicated monospace font. Both achieve columnar alignment; the mono font approach also changes the visual texture of data.
- **Border temperature**: Claude's row borders are warm cream. Stripe's are cool blue-gray. Linear's are transparent white. Vercel uses shadow-borders. The row divider carries the brand's color temperature.
- **Header weight**: Linear at 510-590 and Vercel at 500-600 use heavier headers. Claude at 500 and Stripe at 400 use lighter headers. Stripe's 400-weight headers continue its "whisper authority" pattern.

---

## Cross-Component Patterns

These patterns hold across all five components and all four brands.

### Universal Constants

| Pattern | Rule | Confidence |
|---------|------|------------|
| 8px base grid | All four brands use 8px as the spatial unit | High -- universal |
| Font features are non-negotiable | Each brand's OpenType settings (`ss01`, `cv01+ss03`, `liga`) apply to ALL text | High -- identity-level |
| Focus rings use blue | All brands use some form of blue for keyboard focus, even when blue is absent from the palette | High -- a11y convention |
| One accent color for CTA | Primary CTA uses the single brand accent; secondary recedes | High -- universal |
| Radius = personality | Generous = warm/approachable (Claude). Tight = precise/professional (Stripe). Moderate = engineered/clean (Linear, Vercel) | High -- observed pattern |

### Variation Dimensions

These are the axes along which brands diverge. When implementing a new brand, resolve each dimension.

| Dimension | Range | Effect |
|-----------|-------|--------|
| **Color temperature** | Warm (Claude) <---> Cool (Linear) | Affects every neutral: borders, shadows, backgrounds, text grays |
| **Border technique** | CSS border <---> Shadow-as-border | Vercel/Claude use shadows. Stripe/Linear use CSS borders. Affects hover transitions and box model |
| **Depth model** | Ring shadows (Claude) / Blue-tinted (Stripe) / Luminance stepping (Linear) / Layered stacks (Vercel) | Each brand has a unique shadow philosophy. No two are interchangeable |
| **Headline weight** | 300 (Stripe) <---> 600 (Vercel) | Lighter = luxury/whisper. Heavier = authority/engineering |
| **Radius scale** | 4px (Stripe) <---> 12-32px (Claude) | Tighter = precision. Rounder = warmth. This is the strongest personality signal |
| **Type personality** | Serif (Claude) / Custom sans (Stripe) / Geometric sans (Linear, Vercel) | Serif = editorial. Sans = technical. Custom = distinctive |
| **Dark/light native** | Light-native (Claude, Stripe, Vercel) <---> Dark-native (Linear) | Affects every default: text color, surface color, border opacity model |
| **Spacing density** | Compact (Stripe, Linear) <---> Editorial (Claude) | Affects line-height, padding, section spacing. Editorial demands more air |

### Brand-Specific Techniques Worth Noting

| Technique | Brand | Description |
|-----------|-------|-------------|
| Ring-shadow system | Claude | `0 0 0 1px` warm-toned rings as primary depth mechanism. Shadow pretending to be a border |
| Blue-tinted shadows | Stripe | `rgba(50,50,93,0.25)` -- shadows that carry brand color into the depth layer |
| Luminance stepping | Linear | Depth via `rgba(255,255,255, 0.02 -> 0.05)` bg opacity on dark. No drop shadows |
| Multi-layer shadow stacks | Vercel | Border + elevation + ambient + inner glow in one `box-shadow` declaration |
| Weight-300 headlines | Stripe | Lightest headline weight among major brands. Whisper authority |
| Serif/sans split | Claude | Only brand using serif for headlines and sans for UI. Editorial identity |
| 510 signature weight | Linear | Between regular (400) and medium (500). Unique emphasis without heaviness |
| Shadow-as-border universal | Vercel | Every component (cards, inputs, nav) uses shadow instead of CSS border |
| Warm-only neutrals | Claude | Every gray has a yellow-brown undertone. No cool grays anywhere |
| Dark-mode-first | Linear | Not a "dark theme applied to light" -- darkness is the native medium |

---

## Usage Guide

### For Design Spec Generation

1. Select a brand (or define a new one by resolving each variation dimension above).
2. For each component, apply Layer 1 behavior rules (universal).
3. Fill in Layer 2 by mapping the brand's tokens to the token references in the tables.
4. When a brand doesn't match an existing archetype, interpolate: resolve each variation dimension independently and compose.

### For New Brand Creation

1. Start with the **Variation Dimensions** table. Make a decision for each axis.
2. The decisions cascade: color temperature affects borders, shadows, and text. Radius affects buttons, cards, and inputs equally. Depth model affects cards, nav, and interactive states.
3. Use the **Variant Matrix** tables to select which variants your brand supports. Not every brand needs every variant.
4. Cross-reference against **Layer 1 behavior rules** -- visual style never overrides usability constraints (touch targets, focus rings, error states, etc.).

### Token Mapping Checklist

When implementing a brand, ensure these token categories are resolved:

- [ ] `{color.*}` -- accent, surfaces, text hierarchy (heading/body/muted/placeholder), borders, errors
- [ ] `{font.*}` -- heading family, ui family, mono family, OpenType features
- [ ] `{type.*}` -- size scale, weight scale, letter-spacing scale, line-height scale
- [ ] `{spacing.*}` -- base unit, button padding, card padding, input padding, section spacing
- [ ] `{radius.*}` -- button, card, card-featured, input, nav, pill
- [ ] `{shadow.*}` -- button, card, card-featured, elevation levels, focus ring
- [ ] `{border.*}` -- default, interactive, focus, row-divider, nav
- [ ] `{interaction.*}` -- hover (darken/lighten/invert), active, focus, transitions
- [ ] `{motion.*}` -- transition durations and easing curves

---

## Extended Component Specifications

The following components extend the dual-layer model established above. Each component has Layer 1 (universal behavior rules) and Layer 2 (visual spec template with token references). Brands resolve the token references using their own token systems.

---

## Component: Accordion

### Layer 1: Behavior Rules

- Use for progressive disclosure of long-form content -- headings are the primary navigation.
- Allow multiple sections open simultaneously unless space is critically constrained.
- Include a chevron icon aligned consistently on the right side of each header.
- Animate expand/collapse with a short ease-out transition (150-250ms). Use `grid-template-rows: 0fr/1fr` for height animation to avoid layout-tier `height` animation.
- Keyboard: Enter/Space toggles the focused header. Arrow keys move between accordion headers.
- Each header must have `aria-expanded` state. Content panels use `aria-controls` linked to the header.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| header-bg | `{color.surface-interactive}` | Typically matches page surface; may darken on hover |
| header-text | `{color.text-heading}` | Same heading color used across the system |
| header-weight | `{type.label-weight}` | Matches label weight -- accordion headers are functional labels |
| header-size | `{type.body}` or `{type.label}` | 14-16px depending on density |
| header-padding-y | `{spacing.input-y}` | 12-16px vertical -- provides 44px+ touch target |
| header-padding-x | `{spacing.card-internal}` | 16-24px horizontal -- matches card internal padding if nested |
| chevron-size | 16-20px | Proportional to header text size |
| chevron-color | `{color.text-tertiary}` | Muted -- not competing with header text |
| chevron-rotation | 0deg collapsed, 90deg or 180deg expanded | Animate rotation with same transition as content |
| divider | `{border.row-divider}` | 1px border between accordion items |
| content-padding | `{spacing.card-internal}` | Internal padding of the expanded content area |
| transition | 200ms ease-out-quart | Expand/collapse duration and easing |
| border-radius | `{radius.card}` | When used as standalone component; 0 when nested |

---

## Component: Alert / Toast

### Layer 1: Behavior Rules

- **Inline alerts**: Position close to relevant content. Include icon + color + text (never color alone). Provide dismiss action for non-critical alerts. Keep text to 1-2 sentences.
- **Toast notifications**: Auto-dismiss after 4-6 seconds for non-critical messages. Allow manual dismiss via close button or swipe. Stack multiple toasts with newest on top. Position consistently (bottom-right for desktop, top-center or bottom-center for mobile). Include undo action link for destructive operations.
- **Critical alerts**: Use `role="alert"` for screen reader announcement. Must not be the only way to convey critical information (pair with inline feedback).
- Semantic color coding: red for errors, amber for warnings, green for success, blue for info. Always pair color with an icon for color-blind accessibility.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.status-[type]-bg}` | Subtle tinted background: desaturated version of status color at ~10% opacity |
| text | `{color.text-body}` | Body text color, not the status color -- ensures readability |
| icon-color | `{color.status-[type]}` | Full-strength status color on the icon |
| border | `{color.status-[type]}` at reduced opacity | Left border accent (4px) or full border at 20-30% opacity |
| border-radius | `{radius.card}` | Matches card radius in the system |
| padding | `{spacing.card-internal}` | 12-16px for compact alerts, 16-24px for prominent alerts |
| toast-shadow | `{shadow.card-elevated}` | Elevated shadow -- toasts float above page content |
| toast-max-width | 400-480px | Prevents toast from spanning the full viewport |
| dismiss-btn | `{color.text-tertiary}` | Muted close icon, 44px touch target |
| transition-enter | 300ms ease-out | Slide-in or fade-in for toasts |
| transition-exit | 200ms ease-in | Faster exit than entrance |

---

## Component: Avatar

### Layer 1: Behavior Rules

- Support three sizes: small (24-32px), medium (40-48px), large (64-80px).
- Fallback chain: image -> initials -> generic icon. Each fallback must work gracefully.
- Use a subtle ring or border to separate the avatar from its background.
- For groups: stack with slight overlap (negative margin ~25% of avatar size). Show "+N" overflow indicator when count exceeds display limit (typically 3-5 visible).
- Circular crop is the standard. Square with rounded corners is acceptable for brand-specific contexts.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| border-radius | 50% (circle) | Standard; some brands use `{radius.card}` for square variant |
| border | `{border.default}` or `{shadow.ring}` | 2px solid white or 2px ring shadow for separation from background |
| bg (initials) | `{color.accent}` at 15-20% opacity | Tinted background with initials in accent color |
| text (initials) | `{color.accent}` | Accent color for initials text |
| font-weight (initials) | `{type.label-weight}` | 500-600 for readability at small sizes |
| font-size (initials) | ~40% of avatar diameter | Scales proportionally with avatar size |
| group-overlap | -25% of avatar width | Negative margin for stacked group display |
| group-border | 2px solid `{color.surface-base}` | White ring around each avatar in stack for separation |
| status-dot-size | 25% of avatar diameter | Online/offline indicator dot |
| status-dot-position | Bottom-right corner | Consistently positioned |

---

## Component: Badge / Tag / Chip

### Layer 1: Behavior Rules

- Keep text to 1-2 words -- badges are labels, not sentences.
- Use a limited palette mapped to clear semantics. More than 5-6 badge colors creates confusion.
- Ensure sufficient contrast between badge text and background (WCAG AA minimum).
- Pill shape (fully rounded, `border-radius: 9999px`) for status badges. Rounded rectangle for tags and categories.
- Avoid overuse -- if everything is badged, nothing stands out.
- Notification count badges: position top-right of the parent icon, minimum 16px diameter, max 2-3 digits.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.status-[type]-bg}` or `{color.surface-interactive}` | Subtle tinted bg for status; neutral for category tags |
| text | `{color.status-[type]}` or `{color.text-secondary}` | Status color for semantic badges; muted text for tags |
| font-size | 11-13px | Smaller than body text; must remain readable |
| font-weight | `{type.label-weight}` | 500-600 for readability at small sizes |
| padding-y | 2-4px | Compact vertical padding |
| padding-x | 6-10px | Horizontal padding proportional to text |
| border-radius (pill) | 9999px | Status badges, notification counts |
| border-radius (tag) | `{radius.button}` or 4-6px | Category tags, filter chips |
| border | `{border.default}` at subtle opacity | Optional -- adds definition on light backgrounds |
| dismiss-btn (removable) | 12-16px icon | For filter chips that can be removed |
| max-width | 200px | Truncate with ellipsis beyond this |

---

## Component: Breadcrumb

### Layer 1: Behavior Rules

- Show the full hierarchy path from root to current location.
- The current page is the last item and must not be a link.
- Use a subtle separator (/ or chevron) with adequate spacing.
- On mobile, truncate middle segments with an ellipsis menu -- show first item, ellipsis, and current item.
- Place near the top of content area, below the header/navigation.
- Use `<nav aria-label="Breadcrumb">` with an `<ol>` list for semantics.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| text-color (link) | `{color.text-secondary}` | Muted -- breadcrumbs are wayfinding, not primary content |
| text-color (current) | `{color.text-primary}` | Current page is stronger than ancestor links |
| font-size | `{type.label}` or 13-14px | Smaller than body text |
| font-weight | `{type.body-weight}` | Normal weight; current item may be slightly heavier |
| separator-color | `{color.text-tertiary}` | Very muted separator |
| separator-spacing | 8-12px on each side | Consistent gap around separators |
| hover (links) | `{color.text-primary}` or underline | Standard link hover pattern |
| truncation-trigger | Below ~480px container width | Switch to collapsed mode with ellipsis menu |

---

## Component: Checkbox / Radio

### Layer 1: Behavior Rules

- **Checkbox**: Multi-select from a list, or standalone for a single on/off choice. Support indeterminate state for "select all" with partial children selected.
- **Radio**: Mutually exclusive single-select. Always pre-select a sensible default when possible. Group under a fieldset with a legend.
- Align the control to the first line of its label, not the vertical center (important for multi-line labels).
- Minimum 44px touch target including the label area -- the label should be clickable.
- Stack vertically for 3+ options. Horizontal only for 2-3 short-label options.
- Group related items under a fieldset with a descriptive legend for screen reader context.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| control-size | 16-20px visual, 44px touch target | Visual indicator + invisible extended target |
| border (unchecked) | `{border.input}` | Same border treatment as text inputs |
| bg (unchecked) | `{color.input-bg}` | Same background as text inputs |
| bg (checked) | `{color.accent}` | Brand accent for checked state |
| check-icon-color | `{color.text-on-accent}` | White or light -- readable on accent background |
| border-radius (checkbox) | `{radius.input}` scaled to control size | Typically 3-4px for checkbox |
| border-radius (radio) | 50% | Always circular |
| label-color | `{color.text-body}` | Body text color |
| label-size | `{type.body}` | Body text size |
| label-gap | 8-12px | Space between control and label text |
| focus-ring | `{color.focus}` | Standard focus ring around the control |
| group-gap | 8-12px between items | Consistent spacing within the group |
| indeterminate-icon | Horizontal dash | Checkbox-specific indeterminate state |
| transition | 150ms ease-out | Check/uncheck animation |

---

## Component: Dialog / Modal

### Layer 1: Behavior Rules

- Use sparingly -- only for actions requiring immediate attention or focused input.
- Always provide close mechanisms: X button, Cancel action, and Escape key.
- Trap focus within the dialog while open. Return focus to trigger on close.
- Keep content concise -- if the modal needs scrolling, consider a full page.
- Use a semi-transparent backdrop to dim underlying content.
- **Destructive actions**: Use AlertDialog variant (requires explicit confirmation, no easy dismiss).
- Opening should not scroll the page unexpectedly. Lock body scroll while modal is open.
- Set initial focus to the first focusable element, or the dialog itself if no focusable content.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.surface-card}` | Card-level surface color |
| border-radius | `{radius.card-featured}` | Larger radius than standard cards -- dialogs are prominent |
| shadow | `{shadow.card-featured}` | Maximum elevation shadow |
| padding | 24-32px | Generous internal spacing |
| max-width | 480px (small), 640px (medium), 800px (large) | Size variants by content type |
| backdrop-color | `rgba(0,0,0,0.4-0.6)` | Semi-transparent overlay; darker = more focus on dialog |
| backdrop-blur | 0-4px (optional) | Subtle blur on backdrop; keep static, never animate |
| title-font | `{font.heading}` | Heading font family |
| title-size | `{type.card-title}` | 18-24px |
| title-weight | `{type.card-title-weight}` | Brand heading weight |
| close-btn-position | Top-right, 16px inset | Consistent positioning |
| close-btn-size | 24px visual, 44px touch target | Accessible close button |
| footer-padding | 16-24px | Action buttons area at bottom |
| footer-border-top | `{border.default}` (optional) | Visual separation between content and actions |
| transition-enter | 200-300ms ease-out | Scale from 0.95 + opacity 0 to 1 |
| transition-exit | 150-200ms ease-in | Faster exit |

---

## Component: Dropdown Menu

### Layer 1: Behavior Rules

- Triggered by a button, not by hover (touch devices cannot hover).
- Group related items with separators and optional group headings.
- Keyboard: Arrow keys navigate, Enter selects, Escape closes. Focus moves to first item on open.
- Keep to 7 +/- 2 items. Longer lists need search or sub-menus.
- Position intelligently to avoid viewport overflow -- flip to top if near bottom edge.
- Destructive actions (Delete, Remove) styled in error color, placed last, separated by divider.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.surface-card}` | Elevated surface |
| border | `{border.card}` or `{shadow.ring}` | Container definition |
| border-radius | `{radius.card}` | Matches card radius |
| shadow | `{shadow.card-elevated}` | Clear elevation above trigger |
| item-padding-y | 8-10px | Comfortable click/touch target height |
| item-padding-x | 12-16px | Horizontal padding |
| item-text | `{color.text-body}` | Standard text color |
| item-size | `{type.body}` or 14px | Readable menu text |
| item-hover-bg | `{color.surface-interactive}` at hover opacity | Subtle highlight |
| item-active-bg | `{color.accent}` at 8-12% opacity | Active/selected state |
| separator | `{border.row-divider}` | 1px divider between groups |
| group-heading | `{color.text-tertiary}`, 12px, `{type.label-weight}` | Muted, small group labels |
| destructive-color | `{color.error}` | Red for destructive items |
| icon-size | 16px | Optional leading icons, consistent size |
| icon-gap | 8-12px | Space between icon and text |
| min-width | 180px | Prevents overly narrow menus |
| max-height | 320px with scroll | Long menus get scroll overflow |
| transition | 150ms ease-out | Fast open animation |

---

## Component: Input Variants

### Layer 1: Behavior Rules (All Input Types)

- Single-column form layouts. Labels above inputs.
- Validation: on blur, not on every keystroke. Error below the field with recovery guidance.
- Required fields marked with asterisk or explicit indicator.
- Helper text persistent below complex inputs. Placeholder is NOT a label replacement.
- Error handling: auto-focus first invalid field on submit. Error summary with anchor links for multiple errors.
- Disabled states must look visually non-interactive. Reduced opacity + semantic indication.
- Use appropriate input types for mobile keyboard optimization (email, tel, url, number).

**Textarea-specific**: Allow vertical resizing, set min/max height, auto-grow preferred. Show character count for length-limited fields.

**Search input-specific**: Magnifying glass icon prefix. Support Cmd/Ctrl+K global shortcut. Show recent searches in dropdown. Clear button (x) once text is entered. Debounce input for server queries (200-300ms).

**Select-specific**: Prefer native select for simple cases (better a11y and mobile UX). Custom selects must have full keyboard support and ARIA attributes. Show placeholder ("Select an option...") when empty. For long lists, combine with combobox/search behavior.

### Layer 2: Visual Spec Template

See the existing Form Input component above for the base text input spec. The following are additional variants:

#### Textarea

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| min-height | 3-5 rows (72-120px) | Signals multi-line input expected |
| max-height | 240-400px | Prevent infinite growth |
| resize | vertical only | Allow user to resize height; prevent horizontal resize |
| character-count | `{color.text-tertiary}`, 12px | Bottom-right, muted, appears when limit is set |
| All other properties | Same as Text Input | Border, padding, focus, label, error follow text input spec |

#### Search Input

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| icon-prefix | Magnifying glass, `{color.text-tertiary}` | Left-aligned inside the input |
| icon-size | 16-20px | Proportional to input height |
| clear-button | X icon, appears when input has value | Right-aligned, 44px touch target |
| dropdown-bg | `{color.surface-card}` | Autocomplete suggestions panel |
| dropdown-shadow | `{shadow.card-elevated}` | Elevated above content |
| All other properties | Same as Text Input | Base input styling applies |

---

## Component: Pagination

### Layer 1: Behavior Rules

- Show first, last, and a window of pages around the current one.
- Use ellipsis (...) to indicate skipped pages, not dozens of page numbers.
- Provide Previous/Next buttons in addition to numbered pages.
- Clearly style the current page as selected (accent background or underline).
- Consider "Load more" button or infinite scroll for content feeds instead.
- On mobile, simplify to Previous/Next + current page indicator (e.g., "Page 3 of 12").

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| button-size | 32-40px square, 44px touch target | Each page number is a button |
| active-bg | `{color.accent}` | Current page highlighted with accent |
| active-text | `{color.text-on-accent}` | White/light on accent background |
| inactive-text | `{color.text-secondary}` | Muted page numbers |
| hover-bg | `{color.surface-interactive}` at hover opacity | Subtle hover feedback |
| border-radius | `{radius.button}` | Matches button radius in the system |
| gap | 4-8px | Space between page buttons |
| prev-next-style | Ghost button style | Previous/Next as secondary buttons |
| ellipsis-color | `{color.text-tertiary}` | Muted, non-interactive |
| font-size | `{type.label}` | 13-14px |
| font-weight | `{type.label-weight}` | Medium weight for readability |

---

## Component: Progress / Skeleton

### Layer 1: Behavior Rules

**Progress bar**:
- Show determinate bar when progress is measurable, indeterminate (pulsing) when unknown.
- Include percentage label for accessibility and clarity.
- Use status color coding: default (accent), error (red), success (green on completion).
- Animate smoothly -- no jarring jumps between values.

**Skeleton loader**:
- Match skeleton shape to actual content layout as closely as possible.
- Use a subtle shimmer/pulse animation -- not a spinner.
- Avoid skeletons for very fast loads (<300ms) -- show nothing or a brief delay.
- Show skeleton immediately on navigation. Replace atomically when data arrives.
- Use muted, low-contrast colors for skeleton blocks.

### Layer 2: Visual Spec Template

#### Progress Bar

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| track-bg | `{color.surface-interactive}` at 10-15% | Very subtle background track |
| fill-bg | `{color.accent}` | Brand accent for standard progress |
| fill-bg (success) | `{color.status-success}` | Green on completion |
| fill-bg (error) | `{color.status-error}` | Red on failure |
| height | 4-8px | Thin bar; 4px for subtle, 8px for prominent |
| border-radius | height / 2 (fully rounded) | Pill-shaped ends |
| label-size | `{type.label}` | Percentage text, typically right-aligned above bar |
| transition | 300ms ease-out | Smooth fill animation |

#### Skeleton

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.surface-interactive}` at 5-10% | Very subtle gray placeholder |
| shimmer-highlight | `{color.surface-interactive}` at 15-20% | Moving highlight in shimmer animation |
| border-radius | `{radius.card}` for blocks, 4px for text lines, 50% for avatars | Match actual content shapes |
| animation | 1.5-2s ease-in-out infinite | Slow, subtle shimmer pulse |
| text-line-height | 12-16px | Simulate text line dimensions |
| text-line-gap | 8-12px | Simulate line spacing |

---

## Component: Select

### Layer 1: Behavior Rules

- Prefer native `<select>` for simple use cases -- better accessibility and mobile UX.
- Custom selects must have full keyboard support: arrow keys navigate, Enter selects, Escape closes, type-ahead search.
- Show placeholder ("Select an option...") when no value is chosen.
- Group long option lists with headings or dividers.
- For searchable selects with many options, combine with combobox behavior.
- Selected option should be visually indicated (checkmark or accent highlight) in the dropdown.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| trigger-style | Same as Text Input | Matches input border, radius, padding, focus ring |
| chevron-icon | Downward chevron, `{color.text-tertiary}` | Right-aligned indicator |
| chevron-rotation | 180deg when open | Animated rotation on open/close |
| dropdown-bg | `{color.surface-card}` | Same as dropdown menu |
| dropdown-shadow | `{shadow.card-elevated}` | Elevated panel |
| dropdown-radius | `{radius.card}` | Matches card radius |
| option-padding | 8-10px vertical, 12-16px horizontal | Comfortable option sizing |
| option-hover | `{color.surface-interactive}` at hover opacity | Subtle highlight |
| option-selected-bg | `{color.accent}` at 8-12% opacity | Tinted background for selected |
| option-selected-icon | Checkmark in `{color.accent}` | Leading checkmark for selected option |
| max-dropdown-height | 240-320px | Scroll for long lists |

---

## Component: Switch / Toggle

### Layer 1: Behavior Rules

- Use for binary on/off settings that take effect immediately (no save button needed).
- Label the toggle with what it controls, not "On/Off."
- Show current state visually (thumb position + track color) and optionally with text label.
- Minimum 44px wide touch target.
- Do not use inside forms that require a Save action -- use checkboxes instead.
- `role="switch"` with `aria-checked` for screen readers.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| track-width | 44-52px | Wide enough for clear thumb travel |
| track-height | 24-28px | Proportional to width |
| track-bg (off) | `{color.surface-interactive}` at 20-30% | Muted when off |
| track-bg (on) | `{color.accent}` | Brand accent when active |
| track-radius | track-height / 2 | Fully rounded ends |
| thumb-size | track-height - 4px | Circular thumb with 2px gap from track edge |
| thumb-bg | `{color.surface-base}` (white) | White thumb on colored track |
| thumb-shadow | subtle `{shadow.card}` | Small elevation shadow on thumb |
| thumb-travel | track-width - thumb-size - 4px | Distance from off position to on position |
| focus-ring | `{color.focus}` | Standard focus ring on the track |
| transition | 200ms ease-out-quart | Smooth thumb slide |
| disabled-opacity | 0.4-0.5 | Reduced opacity for disabled state |

---

## Component: Tabs

### Layer 1: Behavior Rules

- Limit to 2-7 tabs. More options need scrollable tab bar or dropdown overflow.
- Clearly indicate active tab: bottom border, background fill, or bold text.
- Short, descriptive labels (1-2 words per tab).
- Tab content immediately below the tab bar with no visual gap.
- Keyboard: Arrow keys move between tabs. Tab key moves focus from tab bar to content.
- `role="tablist"` on container, `role="tab"` on each tab, `role="tabpanel"` on content panels.
- Consider swapping tabs for accordion on narrow viewports.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| tab-text (inactive) | `{color.text-secondary}` | Muted inactive tabs |
| tab-text (active) | `{color.text-primary}` | Full contrast active tab |
| tab-font-size | `{type.label}` | 14px -- same as nav labels |
| tab-font-weight (inactive) | `{type.body-weight}` | Normal weight |
| tab-font-weight (active) | `{type.label-weight}` | Heavier weight for active |
| active-indicator | 2-3px bottom border in `{color.accent}` | Underline-style active indicator |
| tab-padding-y | 10-14px | Vertical padding for 44px+ height |
| tab-padding-x | 12-20px | Horizontal padding per tab |
| tab-gap | 0-4px | Spacing between adjacent tabs |
| bar-border-bottom | `{border.default}` | Full-width border below tab bar |
| hover-bg | `{color.surface-interactive}` at hover opacity | Subtle hover state |
| transition | 150ms ease-out | Active indicator animation |

---

## Component: Tooltip

### Layer 1: Behavior Rules

- Use for supplementary info only -- never for essential content.
- Trigger on hover (desktop) and long-press (mobile). Show after 300ms delay. Hide on mouse leave.
- Keep text to a single sentence or a few words.
- Position intelligently to avoid viewport clipping -- flip direction as needed.
- Include a subtle arrow/caret pointing to the trigger element.
- `role="tooltip"` with `aria-describedby` linking trigger to tooltip.
- Never put interactive content (links, buttons) inside a tooltip. Use a popover instead.

### Layer 2: Visual Spec Template

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| bg | `{color.surface-dark}` or inverted surface | Dark bg for light theme tooltips; light bg for dark theme |
| text | `{color.text-on-dark}` or inverted text | High contrast text on tooltip background |
| font-size | 12-13px | Small, supplementary text |
| font-weight | `{type.body-weight}` | Normal weight |
| padding | 6-8px vertical, 10-14px horizontal | Compact but readable |
| border-radius | `{radius.button}` or 4-6px | Small radius |
| shadow | `{shadow.card}` | Subtle elevation |
| arrow-size | 6-8px | Proportional to tooltip size |
| max-width | 240-320px | Prevents overly wide tooltips |
| z-index | Highest layer (tooltip tier) | Above all other UI |
| transition-enter | 150ms ease-out with 300ms delay | Delayed appearance |
| transition-exit | 100ms ease-in | Fast disappearance |

---

## Component: Card (Expanded Variants)

Extends the base Card specification above with additional variant patterns.

### Layer 1: Additional Behavior Rules

- **Clickable cards**: Entire card surface is a link. Must have hover state on full card, not just internal elements. Use `<a>` wrapping or `onclick` on the card container.
- **Media cards**: Image + content layout. Image maintains aspect ratio (16:9, 4:3, or 1:1). Use `object-fit: cover` for consistent sizing in grids.
- **Metric/KPI cards**: Number-first hierarchy. Large display number -> label -> delta/trend indicator. Use `tabular-nums` for the primary metric.
- **Profile cards**: Avatar + name + role/title. Center-aligned for grid layouts, left-aligned for list layouts.

### Layer 2: Additional Variant Specs

#### Metric/KPI Card

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| metric-size | 32-48px | Large display number as focal point |
| metric-weight | `{type.display-weight}` or 600 | Heavy for impact |
| metric-features | `{type.number-features}` | `tnum` for aligned numbers |
| label-size | `{type.label}` | 12-14px below the metric |
| label-color | `{color.text-tertiary}` | Muted label |
| delta-color (positive) | `{color.status-success}` | Green for positive change |
| delta-color (negative) | `{color.status-error}` | Red for negative change |
| delta-size | `{type.label}` | Same size as label |
| All container properties | Same as Standard Card | bg, border, radius, shadow, padding |

#### Media Card

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| image-aspect-ratio | 16:9, 4:3, or 1:1 | Consistent within a grid |
| image-radius | `{radius.card}` top corners only | Rounded top, flush with card edges |
| image-object-fit | cover | Consistent sizing, no distortion |
| content-padding | `{spacing.card-internal}` | Below image area |
| All other properties | Same as Standard Card | |

---

## Component: Table (Expanded)

Extends the base Table specification above with additional patterns.

### Layer 1: Additional Behavior Rules

- **Selection**: Checkbox column on the left for bulk actions. Header checkbox selects/deselects all visible rows. Selected row count shown in toolbar.
- **Inline actions**: Action column on the right (Edit, Delete) or kebab menu per row. Destructive actions require confirmation.
- **Fixed columns**: First column (name/identifier) can be sticky on horizontal scroll for context preservation.
- **Density modes**: Default, compact, and comfortable. Compact reduces cell padding by ~30% for data-heavy views. Comfortable increases by ~30% for scannable views.
- **Responsive**: Below tablet breakpoint, transform data tables to card layout using `display: block` and `data-label` attributes, or use horizontal scroll (`overflow-x: auto`).

### Layer 2: Additional Variant Specs

#### Compact Density

| Property | Token Reference | Adjustment |
|----------|----------------|-----------|
| cell-padding-y | `{spacing.cell-y}` * 0.7 | ~6-8px instead of 8-12px |
| row-height | ~36px | Compact rows |
| font-size | 13px | Slightly smaller |

#### Comfortable Density

| Property | Token Reference | Adjustment |
|----------|----------------|-----------|
| cell-padding-y | `{spacing.cell-y}` * 1.3 | ~12-16px instead of 8-12px |
| row-height | ~48px | Spacious rows |
| font-size | 14-15px | Standard or slightly larger |

#### Selection Column

| Property | Token Reference | Design Notes |
|----------|----------------|-------------|
| checkbox-column-width | 44-48px | Fixed width, centered checkbox |
| selected-row-bg | `{color.accent}` at 5-8% opacity | Subtle accent tint on selected rows |
| selection-count-bar | Floating bar above table | Shows "N items selected" + bulk actions |
