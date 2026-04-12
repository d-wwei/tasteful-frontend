# Component Patterns & Best Practices

These patterns guide **design spec generation**. For code-level implementation, see `code-rules.md`.

## 1. Spatial Structure & Layout

- **8px Grid**: Space all elements using multiples of 8px.
- **White Space**: Treat as a design feature, not emptiness. Give sections room to breathe.
- **Mobile-First**: Design for smallest screen first (375px), scale up. Breakpoints: 375 / 768 / 1024 / 1440.
- **Container Width**: Consistent maximum width on desktop. Never arbitrary widths per page.
- **Safe Areas**: Respect platform safe areas for fixed headers, tab bars, CTA bars.
- **Scroll Safety**: No nested scroll regions conflicting with main scroll.

## 2. Forms & Inputs

- **Single-column layouts** for forms. Labels above inputs.
- **Button labels**: Verb-first — "Save Settings", "Send Message", "Create Account". Never just "Submit".
- **ONE primary button** per section. Secondary actions are visually muted (ghost/outline).
- **Validation**: On blur, not keystroke. Error below the field with recovery path.
- **Required fields**: Marked with asterisk or explicit indicator.
- **Helper text**: Persistent below complex inputs, not just placeholder.
- **Error handling**: Auto-focus first invalid field on submit error. Error summary with anchor links for multiple errors.
- **Long forms**: Auto-save drafts. Confirm before dismissing unsaved changes. Multi-step forms show progress.
- **Disabled states**: Must look visually non-interactive. Reduced opacity + semantic indication.

## 3. Data Display

- **Cards**: Strict hierarchy: Media → Title → Meta/Subtitle → Action. Choose shadow OR border, not both.
- **Tables**: Right-align numbers. Distinct sticky headers. Sortable columns indicated visually.
- **Empty States**: NEVER just "No items found." Always: icon/illustration + helpful headline + clear primary CTA.
- **Loading States**: Skeleton/shimmer for >1s. Reserve space to prevent layout shift.
- **Read-Only vs. Disabled**: Visually and semantically distinct.

## 4. Charts & Data Visualization

- **Chart type match**: Trend → line, comparison → bar, proportion → pie/donut (≤5 categories, else bar).
- **Accessibility**: Colors + patterns (not color alone). Legend visible near chart.
- **Table alternative**: Provide data table for screen readers alongside visual charts.
- **Interactive**: Tooltips with exact values on hover/tap. Legend clickable to toggle series.
- **Responsive**: Reflow or simplify on small screens. Aggregate large datasets.
- **Empty/Error**: "No data yet" + guidance, not blank axes. Load failure → error + retry.

## 5. Overlays (Modals & Drawers)

- **Backdrop**: Dark or blurred mask (40–60% opacity) for legibility.
- **Modals**: For focused tasks requiring immediate attention (confirmations, payments).
- **Drawers**: Side panels for complex forms or detail views to maintain page context.
- **Dismiss safety**: Confirm before dismissing with unsaved changes.
- **Animation**: Animate from trigger source for spatial context.
- **NEVER** use modals for primary navigation flows.

## 6. Navigation

- **Top nav**: Max 5–7 links. Clear active indicator. Hamburger only on mobile, NEVER desktop.
- **Bottom nav (mobile)**: Max 5 items. Icon + text label. Top-level screens only.
- **Tabs**: 2–7 items. Horizontal scroll on overflow.
- **Back behavior**: Predictable and consistent. Preserve scroll position, filter state, input.
- **Deep linking**: All key screens reachable via URL/deep link.
- **Adaptive**: Desktop (≥1024px) → sidebar nav. Mobile → bottom/top nav.
- **Search**: Easily reachable. Provide recent/suggested queries.
- **Consistency**: Same nav placement across all pages.

## 7. Icons & Visual Elements

- **No emoji icons**: Use vector SVG icon libraries (Lucide, Heroicons, etc.).
- **Consistent family**: One icon set with matching stroke width across the product.
- **Sizing tokens**: Small, medium (24pt default), large. No arbitrary mixed sizes.
- **Style consistency**: One style (filled or outline) per hierarchy level.
- **Contrast**: 4.5:1 for small icons, 3:1 for larger UI glyphs.

*These patterns inform the `pages` and `navigation` sections of layout-spec.yaml.*
