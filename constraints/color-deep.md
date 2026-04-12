# Color Deep Knowledge

Design-layer guidance for color decisions beyond basic palette selection. Covers the OKLCH color space, tinted neutral strategy, alpha transparency pitfalls, dark mode surface depth, contrast calculation, the 60-30-10 rule, semantic color frameworks, and color blindness testing. For code-level implementation, see `code-rules.md`.

---

## OKLCH Color Space

### Why OKLCH Is Better Than HSL

HSL (Hue, Saturation, Lightness) has a fundamental flaw: it is not perceptually uniform. "50% lightness" in yellow looks bright; "50% lightness" in blue looks dark. This means you cannot create a harmonious palette by keeping lightness constant and varying hue -- the results will look uneven to the human eye.

OKLCH fixes this. Its three channels:

| Channel | Range | What It Controls |
|---------|-------|-----------------|
| **L** (Lightness) | 0-100% | Perceived brightness -- equal steps look equal across all hues |
| **C** (Chroma) | 0-0.4+ | Color intensity/saturation -- 0 is achromatic gray |
| **H** (Hue) | 0-360 | Color wheel position |

**The key design benefit**: You can create a 10-step shade scale for any hue by evenly spacing lightness values, and each step will look perceptually equidistant. In HSL, creating an even-looking scale requires manual per-hue adjustment.

### Chroma Reduction at Extremes

As you move toward white (high lightness) or black (low lightness), reduce chroma. High chroma at extreme lightness values produces garish, unnatural colors.

| Lightness Range | Recommended Chroma | Effect |
|----------------|-------------------|--------|
| 80-100% (near white) | 0.01-0.08 | Soft tint, reads as "tinted white" |
| 50-80% (mid-range) | 0.08-0.20 | Full color expression |
| 20-50% (dark range) | 0.05-0.15 | Rich, deep color |
| 0-20% (near black) | 0.01-0.05 | Tinted black, subtle undertone |

**Design rule**: The base color (mid-lightness) carries full chroma. Every step toward white or black should reduce chroma proportionally. This creates scales that feel natural rather than artificial.

### Generating Harmonious Scales in OKLCH

To create a 10-step shade scale for a single hue:

1. Choose the base hue (H) and keep it constant across all steps.
2. Space lightness (L) from ~95% (lightest) to ~15% (darkest) in roughly equal steps.
3. Peak chroma (C) at the mid-lightness values (~40-60% L) and reduce toward both extremes.
4. The result: a perceptually uniform scale where each step feels equidistant.

---

## Tinted Neutral Strategy

### Pure Gray Is Dead

Every gray in a well-designed palette carries a subtle tint of the brand hue. Pure achromatic gray (`oklch(50% 0 0)`) has no personality -- it reads as "no decision was made."

The technique: add chroma of 0.005-0.015 to every neutral, using the brand's dominant hue angle.

| Brand Temperature | Hue Angle | Effect |
|-------------------|-----------|--------|
| Warm (Claude-like) | 50-80 (yellow-orange) | Grays feel parchment-like, inviting |
| Cool (Stripe-like) | 230-260 (blue) | Grays feel precise, professional, clean |
| Neutral-warm | 30-50 (amber) | Grays feel natural, organic |
| Neutral-cool | 200-230 (teal-blue) | Grays feel modern, tech-forward |

**Design rule**: The tint chroma should be barely perceptible in isolation (0.01) but clearly felt when comparing tinted neutrals against pure grays side by side. Subtle enough to be subconscious, strong enough to create cohesion.

### Tinted Neutral Cascade

The tint carries into every gray-derived element in the system:

- **Borders**: Tinted, not pure gray
- **Shadows**: Tinted or brand-colored, not `rgba(0,0,0,x)`
- **Placeholder text**: Tinted gray, not pure gray
- **Disabled states**: Tinted gray, not pure gray
- **Dividers**: Tinted gray, not pure gray
- **Background surfaces**: Tinted off-white, not pure white

If any element uses a pure achromatic gray while the rest are tinted, it creates a subtle discord -- like a single off-key note.

---

## Alpha Is a Design Smell

### The Problem with Transparency

Heavy reliance on alpha transparency (`rgba`, `hsla`, OKLCH with `/alpha`) usually signals an incomplete color palette. Instead of defining the exact color for each context, the designer uses transparency as a shortcut.

### Why Alpha Creates Problems

1. **Unpredictable contrast**: A semi-transparent element's final rendered color depends on what is behind it. Place the same `rgba(0,0,0,0.5)` overlay on a white surface and a blue surface -- the resulting colors are completely different. Contrast ratios become impossible to guarantee.
2. **Performance overhead**: Compositing semi-transparent layers is more expensive than rendering opaque colors.
3. **Stacking artifacts**: Multiple semi-transparent layers compound unpredictably. Two `rgba(0,0,0,0.1)` overlays stacked do not produce `rgba(0,0,0,0.2)`.

### When Alpha Is Appropriate

- **Focus rings**: The focus indicator overlays variable backgrounds -- alpha ensures visibility regardless of surface color.
- **Hover/pressed state overlays**: A `rgba(0,0,0,0.04)` hover overlay darkens any surface consistently.
- **Dark mode borders**: `rgba(255,255,255,0.08)` works on any dark surface (Linear's approach).
- **Scrim/backdrop overlays**: The semi-transparent overlay behind modals must show through to the content beneath.

### When Alpha Is a Smell

- **Text colors**: Text should have a defined, opaque color. Semi-transparent text produces contrast ratios that vary by background.
- **Surface colors**: Card backgrounds, section backgrounds, and component backgrounds should be opaque and defined.
- **Border colors** on light surfaces: Use an opaque tinted neutral, not a transparent overlay.

**Design rule**: If you find yourself using alpha for more than overlays and interaction states, you are missing palette entries. Define the actual computed color and add it to the token system.

---

## Dark Mode Surface Depth

### Dark Mode Is Not Inverted Light Mode

Inverting a light palette produces a broken dark experience. Dark mode requires fundamentally different design decisions.

### The Key Differences

| Property | Light Mode Approach | Dark Mode Approach |
|----------|--------------------|--------------------|
| **Depth** | Shadows create depth (darker shadow = higher) | Lighter surfaces create depth (brighter = higher) |
| **Text weight** | Normal weight (400) | Slightly reduced weight (350-400) -- light text on dark appears heavier |
| **Accent saturation** | Full chroma | Reduced chroma (desaturate 10-20%) -- vibrant colors are harsh on dark backgrounds |
| **Background** | White or near-white | Dark gray, never pure black (12-18% lightness in OKLCH) |
| **Borders** | Opaque tinted gray | Semi-transparent white (`rgba(255,255,255,0.05-0.08)`) |

### Surface Elevation on Dark

Instead of shadows (which are invisible against dark backgrounds), dark mode uses luminance stepping -- each elevation level is a slightly lighter surface:

| Level | Lightness | Example Use |
|-------|-----------|-------------|
| Base (deepest) | 5-8% | Page background, canvas |
| Level 1 | 10-12% | Sidebars, secondary panels |
| Level 2 | 14-18% | Cards, dropdowns, elevated containers |
| Level 3 | 20-25% | Hover states, active surfaces, highest elevation |

**Design rule**: The luminance difference between adjacent levels should be large enough to perceive as "above" but small enough to avoid stark banding. Increments of 3-5% lightness per level work well.

### Pure Black Is Almost Always Wrong

`#000000` (0% lightness) as a background creates excessive contrast with text, causing eye strain during extended reading. It also makes the interface feel like a void rather than a surface.

**Recommendation**: Use 8-18% lightness for dark backgrounds. Reserve true black (0-5%) only for the deepest canvas in cinematic or immersive contexts.

---

## Modern Contrast Calculation

### WCAG 2.x Contrast Ratio

The standard method: calculate the luminance ratio between foreground and background colors.

| Content | AA Minimum | AAA Target |
|---------|-----------|------------|
| Body text | 4.5:1 | 7:1 |
| Large text (18px+ or 14px bold) | 3:1 | 4.5:1 |
| UI components, non-text | 3:1 | Not defined |
| Decorative / non-informational | No requirement | No requirement |

### The Placeholder Gotcha

Placeholder text is body text -- it must meet 4.5:1 contrast. The ubiquitous light-gray placeholder that most implementations use typically fails WCAG. Design your placeholder color with a contrast checker, not by feel.

### Dangerous Color Combinations

These combinations frequently fail contrast or create readability problems:

- Light gray text on white -- the most common accessibility failure on the web
- Gray text on any colored background -- gray looks washed out and lifeless on color. Use a darker shade of the background color or transparent overlay instead
- Red on green (or reverse) -- indistinguishable to ~8% of men (protanopia/deuteranopia)
- Blue on red -- causes chromatic vibration, painful to read
- Yellow on white -- almost never passes contrast requirements
- Thin light text over images -- unpredictable contrast depending on image content

---

## The 60-30-10 Rule

### Visual Weight, Not Pixel Count

The 60-30-10 color distribution rule is about perceived visual weight, not measured area.

| Proportion | Role | What Goes Here |
|------------|------|---------------|
| **60%** | Dominant | Neutral backgrounds, white space, base surfaces -- the canvas |
| **30%** | Secondary | Text colors, borders, inactive states, secondary surfaces -- the structure |
| **10%** | Accent | Primary CTAs, highlights, focus states, interactive moments -- the signal |

**The critical insight**: The accent color works BECAUSE it is rare. If you spread the accent color across 30% of the interface, it loses its signaling power. The scarcity of accent color is what gives it impact.

### Applying the Rule

- Count the distinct color moments on any screen. If the accent appears more than 3-5 times in a viewport, it is overused.
- The "60% neutral" does not mean 60% pure white. It means 60% of visual weight is carried by your neutral palette (tinted whites, grays, surfaces).
- Status colors (success green, error red, warning amber) exist outside the 60-30-10 budget. They appear contextually and should be desaturated or alpha-reduced to avoid competing with the accent.

---

## Semantic Color Framework

Colors in a design system are not decorative -- they carry meaning. Define color roles explicitly.

### Status Colors

| Role | Meaning | Typical Hue | Design Constraint |
|------|---------|-------------|------------------|
| **Success** | Positive completion, valid state | Green (emerald, forest) | Never the only indicator -- pair with icon + text |
| **Error** | Failure, invalid state, destructive action | Red (rose, crimson) | Must meet 4.5:1 contrast for text |
| **Warning** | Caution, approaching limit, non-blocking issue | Orange/Amber | Must be distinguishable from error at a glance |
| **Info** | Neutral information, guidance, tips | Blue (sky, indigo) | Should not compete visually with the brand accent |

### Category Colors

Used to distinguish between types, groups, or sections (e.g., project labels, tag categories, chart series).

**Rule**: Limit to 5-8 distinct category colors. More than 8 categorical colors are indistinguishable to most viewers. If you need more categories, use shape, pattern, or position to differentiate -- not more colors.

### Guidance Colors

Colors that direct behavior:

- **Focus blue**: The universal keyboard focus indicator color. Even brands with no blue in their palette use blue for focus (Claude, Stripe, Vercel all use some form of blue for focus rings). This is a learned convention -- do not fight it.
- **Link color**: Must be distinguishable from surrounding text. Does not have to be blue, but must be consistently different.

---

## Color Blindness Testing

### The Scale of the Problem

~8% of men and ~0.5% of women have some form of color vision deficiency. For a product with 10,000 male users, ~800 experience color differently.

### Types and What They Cannot Distinguish

| Type | Prevalence | Confusion | Design Impact |
|------|-----------|-----------|---------------|
| **Deuteranopia** (green-blind) | ~5% of men | Red vs green, brown vs green | Error/success states must not rely on red/green alone |
| **Protanopia** (red-blind) | ~2.5% of men | Red vs green, red appears darker | Red text/icons may become invisible on dark backgrounds |
| **Tritanopia** (blue-blind) | ~0.01% | Blue vs yellow | Rare, but check blue-heavy interfaces |
| **Monochromacy** | Very rare | All color | Ensure information hierarchy works in grayscale |

### Testing Methods

1. **Browser DevTools**: Chrome/Edge DevTools > Rendering > Emulate vision deficiencies. Provides instant simulation of all major types.
2. **Design tool simulation**: Figma, Sketch, and most design tools have color blindness simulation plugins.
3. **The grayscale test**: Convert the screen to grayscale. If you can still understand the hierarchy, navigate the interface, and distinguish states, the design survives color blindness.
4. **Contrast checkers**: WebAIM Contrast Checker, Polypane, Stark -- verify that color combinations meet WCAG ratios.

### Design Rules for Color-Safe Interfaces

- Never use color as the sole differentiator. Always pair with icon, text, pattern, or position.
- Red/green pairs must have an additional distinguishing signal (icon shape, label text, position).
- Charts and data visualizations need shape or pattern encoding alongside color.
- Test every status state (success/error/warning) under deuteranopia simulation before shipping.
