# Baseline Accessibility & Performance Constraints

When generating UI components, you MUST adhere to the following baseline rules to ensure the output is production-grade. Do not compromise on these even for aesthetic reasons.

## 1. Interactive Elements & ARIA
- **Icon-Only Buttons**: Any button that contains only an icon MUST have an `aria-label` or `aria-labelledby` attribute explaining its function to screen readers.
  - *Wrong*: `<button><LucideIcon /></button>`
  - *Right*: `<button aria-label="Close modal"><LucideIcon aria-hidden="true" /></button>`
- **Semantic HTML**: Always prefer native interactive elements (`<button>`, `<a>`) over adding `onClick` handlers to `<div>` or `<span>`. 
- **Forms**: Every input must be associated with a `<label>`. Placeholder text is not a substitute for a label. 

## 2. Focus & Keyboard Navigation
- **Focus Indicators**: Never remove focus outlines without providing a highly visible custom replacement (e.g., `focus-visible:ring-2 focus-visible:ring-primary focus-visible:ring-offset-2`).
- **Modal Focus Trapping**: Modals, Dialogs, and Drawers must trap keyboard focus while open, and must support closure via the `<Escape>` key.

## 3. Motion & Performance
- **Reduced Motion**: Respect `prefers-reduced-motion`.
- **Property Animation**: Only animate compositor properties (e.g., `transform`, `opacity`). Never animate layout properties like `width`, `height`, `margin`, or `padding`, as this triggers expensive layout recalculations.
- **Duration**: Keep interaction feedback (hovers, clicks) under 200ms (`duration-200`). Entrance animations can be slightly longer but should use `ease-out`.

## 4. Typography
- **Hierarchy**: Do not skip heading levels (e.g., `<h2>` must not be followed immediately by `<h4>`).
- **Readability**: Ensure sufficient color contrast (WCAG AA minimum) between text and its background. Ensure body text is at least 14px (preferably 16px).
- **Text Wrapping**: Use `text-balance` for headings to prevent lonely words on the last line. Use `text-pretty` for paragraphs. 

*If your generated code violates any of these principles, you will explicitly fail the quality check.*
