# HTML Preview Adapter

Generates a self-contained HTML file that visually renders the design spec for quick validation. No external dependencies — opens in any browser.

## Push: Spec → Preview

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

## Limits

- Shows token values and layout skeleton only — no real component behavior
- No interaction or animation preview
- No dark mode toggle (would require JavaScript)
- Font loading requires internet connection for Google Fonts
- Suitable for **direction validation**, not detailed design review
- For detailed review, use Penpot or Figma adapter instead
