# HTML Preview Adapter

Generates self-contained HTML files from design specs. Two modes:

- **Preview Mode** — Style guide for direction validation (color swatches, type samples, layout skeleton)
- **Demo Mode** — Complete page for deliverable output (real components, responsive behavior, interaction states)

No external dependencies — opens in any browser.

---

## Preview Mode (Style Guide)

### Push: Spec → Preview

When the user requests a preview, or after generating a new spec:

1. **Read `tokens.json`** and convert to CSS custom properties:
   - Color tokens → `--color-surface: #0f172a;`
   - Typography tokens → `--font-display: "Space Grotesk";` + Google Fonts `<link>`
   - Spacing tokens → `--spacing-md: 16px;`
   - Motion tokens → `--duration-normal: 200ms;`
   - Shadow tokens → `--shadow-md: 0 4px 12px -2px rgba(0,0,0,0.1);`

2. **Read `layout-spec.yaml`** and generate page skeleton:
   - `meta.tone` and `meta.wow_factor` displayed as header context
   - `layout.structure` rendered as flexbox/grid skeleton
   - `pages[].sections` rendered as labeled placeholder blocks
   - `navigation` rendered as nav bar skeleton

3. **Generate single-file `preview.html`** containing:
   - `<style>` block with all CSS custom properties from tokens
   - Google Fonts `<link>` for font-display and font-body
   - Color swatches section showing all color tokens
   - Typography samples showing font pairings at each scale
   - Spacing visualization showing the spacing scale
   - Page layout skeleton from layout-spec
   - Component samples (buttons, cards, inputs) using token values

4. **Open in browser**: `open preview.html` (macOS) or `xdg-open preview.html` (Linux)

## Pull: Not Supported

HTML preview is read-only. To modify design decisions, edit the spec directly or use Penpot/Figma adapter.

## Diff: Not Applicable

No bidirectional sync.

## Template Structure

The generated preview.html should follow this structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{meta.project} — Design Preview</title>
  <link href="https://fonts.googleapis.com/css2?family={font-display}:wght@400;600;700&family={font-body}:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      /* Generated from tokens.json */
    }
    /* Preview layout styles */
  </style>
</head>
<body>
  <header>
    <h1>{meta.project}</h1>
    <p>Tone: {meta.tone} | Wow Factor: {meta.wow_factor} | Platform: {meta.platform}</p>
  </header>

  <section id="colors">
    <h2>Color Palette</h2>
    <!-- Color swatches with name, hex value, and contrast ratio against surface -->
  </section>

  <section id="typography">
    <h2>Typography</h2>
    <!-- Display font sample at each scale -->
    <!-- Body font sample at each scale -->
  </section>

  <section id="spacing">
    <h2>Spacing Scale</h2>
    <!-- Visual blocks showing spacing scale -->
  </section>

  <section id="components">
    <h2>Component Samples</h2>
    <!-- Primary button, secondary button, input field, card using tokens -->
  </section>

  <section id="layout">
    <h2>Page Layout</h2>
    <!-- Skeleton rendering of layout-spec structure -->
  </section>
</body>
</html>
```

### Preview Mode Limits

- Shows token values and layout skeleton only — no real component behavior
- No interaction or animation preview
- No dark mode toggle (would require JavaScript)
- Font loading requires internet connection for Google Fonts
- Suitable for **direction validation**, not detailed design review
- For detailed review, use Penpot or Figma adapter, or switch to Demo Mode

---

## Demo Mode (Complete Page)

When invoked in demo mode (`/tasteful-frontend demo`), the adapter generates a complete, deliverable page instead of a style guide.

### Input

1. **`tokens.json`** — all three layers (primitive + semantic + component) resolved to final values
2. **`layout-spec.yaml`** — complete page structure with sections, components, responsive rules, interaction patterns
3. **`agent-prompts/{brand}.md`** — component-level rendering specs (exact px/hex/shadow values). If no brand match, use token values directly.

### Output Structure

The generated `.design/demo.html` must include all seven of the following:

1. **Full page layout** — rendered sections matching layout-spec (not placeholder blocks). Each `pages[].sections` entry becomes a real HTML section with appropriate semantic elements.

2. **Real content** — lorem ipsum is acceptable for body text, but structure must match the spec: hero with headline + subtitle + CTA, feature grid with cards, pricing table if specified, footer with links, etc. No "Section 1" / "Section 2" labels.

3. **Responsive behavior** — media queries at all specified breakpoints (typically 375 / 768 / 1024 / 1440), with layout changes: sidebar collapse, grid column reflow, font size adjustments, spacing reduction on mobile.

4. **Interaction states** — hover effects on buttons/cards/links, focus rings on interactive elements, active states on buttons. CSS-only, no JavaScript required. Use `transition` with duration tokens.

5. **Dark mode** — if tokens define a dark mode set, include `@media (prefers-color-scheme: dark)` with dark token overrides as CSS custom property reassignment. If no dark tokens exist, skip.

6. **Typography** — Google Fonts `<link>` for brand fonts with proper weights (400, 500, 600, 700 as needed). Fallback stack specified. Type scale applied to headings, body, labels, captions.

7. **Component fidelity** — buttons, cards, inputs, navigation rendered with exact token values: border-radius from `radius` tokens, box-shadow from `shadow` tokens, spacing from `spacing` tokens, colors from semantic/component token layers. No hardcoded values.

### Template Skeleton

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{meta.project} — Demo</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family={font-display}:wght@400;600;700&family={font-body}:wght@400;500&display=swap" rel="stylesheet">
  <style>
    /* ── Token Layer ── */
    :root {
      /* Primitive tokens (raw values) */
      --slate-50: #f8fafc;
      --slate-900: #0f172a;
      /* ... all primitives ... */

      /* Semantic tokens (referencing primitives) */
      --color-surface: var(--slate-900);
      --color-accent: var(--coral-500);
      --color-text: var(--slate-50);
      /* ... all semantics ... */

      /* Component tokens (referencing semantics) */
      --button-primary-bg: var(--color-accent);
      --card-bg: var(--color-surface-subtle);
      /* ... all component tokens ... */

      /* Typography */
      --font-display: "Space Grotesk", sans-serif;
      --font-body: "Inter", sans-serif;

      /* Spacing (8px grid) */
      --spacing-xs: 4px;
      --spacing-sm: 8px;
      --spacing-md: 16px;
      --spacing-lg: 24px;
      --spacing-xl: 32px;
      --spacing-2xl: 48px;

      /* Motion */
      --duration-fast: 150ms;
      --duration-normal: 200ms;
      --duration-slow: 300ms;
      --easing-default: cubic-bezier(0.4, 0, 0.2, 1);

      /* Shadows */
      --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
      --shadow-md: 0 4px 12px -2px rgba(0,0,0,0.1);
      --shadow-lg: 0 12px 32px -4px rgba(0,0,0,0.15);

      /* Radii */
      --radius-sm: 4px;
      --radius-md: 8px;
      --radius-lg: 16px;
    }

    /* ── Dark Mode Override ── */
    @media (prefers-color-scheme: dark) {
      :root {
        --color-surface: var(--slate-900);
        --color-text: var(--slate-50);
        /* ... dark overrides ... */
      }
    }

    /* ── Reset + Base ── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: var(--font-body);
      color: var(--color-text);
      background: var(--color-surface);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    /* ── Component Styles ── */
    .btn-primary {
      background: var(--button-primary-bg);
      color: var(--button-primary-text);
      padding: var(--spacing-sm) var(--spacing-lg);
      border-radius: var(--radius-md);
      border: none;
      font-weight: 600;
      cursor: pointer;
      transition: all var(--duration-fast) var(--easing-default);
    }
    .btn-primary:hover { opacity: 0.9; transform: translateY(-1px); }
    .btn-primary:focus-visible { outline: 2px solid var(--color-accent); outline-offset: 2px; }
    .btn-primary:active { transform: translateY(0); }

    .card {
      background: var(--card-bg);
      border-radius: var(--radius-lg);
      padding: var(--spacing-lg);
      box-shadow: var(--shadow-md);
      transition: box-shadow var(--duration-normal) var(--easing-default);
    }
    .card:hover { box-shadow: var(--shadow-lg); }

    /* ... more component styles from component tokens ... */

    /* ── Layout ── */
    .container { max-width: 1200px; margin: 0 auto; padding: 0 var(--spacing-lg); }

    /* ── Responsive ── */
    @media (max-width: 1024px) {
      /* Tablet: sidebar collapse, grid adjustments */
    }
    @media (max-width: 768px) {
      /* Tablet-small: single column, reduced spacing */
    }
    @media (max-width: 375px) {
      /* Mobile: full-width, stacked layout, smaller type */
    }
  </style>
</head>
<body>
  <nav>
    <!-- Navigation from layout-spec.navigation -->
  </nav>
  <main>
    <section class="hero">
      <!-- Hero: headline (font-display, scale-2xl), subtitle, CTA buttons -->
    </section>
    <section class="features">
      <!-- Feature cards grid from layout-spec sections -->
    </section>
    <!-- ... more sections matching layout-spec pages[].sections ... -->
  </main>
  <footer>
    <!-- Footer from layout-spec -->
  </footer>
</body>
</html>
```

### Quality Bar

The demo.html must meet ALL of the following:

- **Looks like a real page** — a landing page, dashboard, or app screen. NOT a component library, NOT a style guide, NOT a wireframe.
- **Zero hardcoded values** — every color, font, spacing, shadow, radius value must come from CSS custom properties mapped to tokens. Grep for hex codes outside `:root` → should find zero.
- **Responsive at all breakpoints** — open at 375px, 768px, 1024px, 1440px and verify layout changes appropriately.
- **Passes the Pre-Delivery Checklist** — same checklist as spec mode (contrast ratios, touch targets, loading strategy, etc.) applies to demo output.
- **Interaction states work** — hover a button, tab through focusable elements, click — visual feedback must be present.
- **Font loads correctly** — Google Fonts link uses correct family names and weights. Page looks correct with fonts loaded.

### Demo Mode Limits

- No JavaScript — interactions are CSS-only (`:hover`, `:focus-visible`, `:active`, `@media`)
- No real backend data — content is static lorem ipsum or spec-defined copy
- No animation orchestration — page load animations would require JS; motion tokens apply to hover/focus transitions only
- Font loading requires internet for Google Fonts
- Single-file constraint means no image assets — use CSS gradients, SVG inline, or placeholder blocks for images
