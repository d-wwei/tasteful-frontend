# Component Patterns & Best Practices

Strictly follow these patterns to avoid confusing or generic AI-generated interfaces.

## 1. Spatial Structure & Layout

- **8px Grid**: Space elements using multiples of 8 (`p-4` = 16px, `gap-6` = 24px, `m-8` = 32px).
- **White Space**: A feature, not emptiness. Give hero sections and cards room to breathe. Generous margins to group related items.
- **Mobile-First**: Design for 375px first, scale up. Breakpoints: 375 / 768 / 1024 / 1440.
- **Container Width**: Consistent `max-w-6xl` or `7xl` on desktop. Never arbitrary widths per page.
- **Viewport**: `min-h-dvh` over `100vh` on mobile. `width=device-width, initial-scale=1`.
- **Safe Areas**: Respect top/bottom safe areas for fixed headers, tab bars, CTA bars. Don't place UI under notch or gesture area.
- **Z-Index Scale**: Define layers: 0 / 10 / 20 / 40 / 100 / 1000. No arbitrary values.
- **Scroll Safety**: No nested scroll regions conflicting with main scroll. Add content insets for fixed bars.

## 2. Forms & Inputs

- **Column Layout**: Single-column for forms. Stack labels above inputs.
- **Button Labels**: Verb-first — "Save Settings", "Send Message", "Create Account". Never just "Submit".
- **Primary vs. Secondary**: ONE primary button per section. Mute secondary actions (ghost/outline for "Cancel").
- **Validation**: On blur, not keystroke. Error below the field, styled with danger color + icon. Include recovery path ("check your email format").
- **Required Fields**: Mark with asterisk or explicit indicator.
- **Helper Text**: Persistent below complex inputs, not just placeholder.
- **Focus Management**: Auto-focus first invalid field on submit error. Error summary at top with anchor links (for multiple errors).
- **Input Types**: Use semantic types (`email`, `tel`, `number`) for correct mobile keyboard.
- **Password**: Show/hide toggle. Support autofill (`autocomplete` / `textContentType`).
- **Long Forms**: Auto-save drafts. Confirm before dismissing unsaved changes. Multi-step → show progress indicator.
- **Disabled States**: Reduced opacity (0.38–0.5) + cursor change + semantic attribute. Must look non-interactive.

## 3. Data Display

- **Cards**: Strict hierarchy: `Media → Title → Meta/Subtitle → Action`. Never both heavy shadow AND heavy border — choose one.
- **Tables**: Right-align numbers. Distinct sticky headers (muted text, uppercase tracking, or light background). Sortable with `aria-sort`.
- **Empty States**: NEVER just "No items found." Design a proper empty state: subtle icon/illustration + helpful headline + clear primary CTA.
- **Loading States**: Skeleton/shimmer for >1s. Reserve space to prevent layout shift. Never a blank frame.
- **Read-Only vs. Disabled**: Visually and semantically distinct.

## 4. Charts & Data Visualization

- **Chart Type Match**: Trend → line, comparison → bar, proportion → pie/donut (≤5 categories, else bar).
- **Accessibility**: Colors + patterns/textures (not color alone). Legend visible near chart. `aria-label` summary. Keyboard-navigable elements.
- **Table Alternative**: Provide data table for screen readers alongside visual charts.
- **Interactive**: Tooltips on hover (web) / tap (mobile) with exact values. Legend clickable to toggle series.
- **Responsive**: Reflow or simplify on small screens. Don't render 1000+ raw points — aggregate.
- **Empty/Error**: "No data yet" + guidance, not blank axis. Load failure → error + retry action.
- **Polish**: Low-contrast gridlines (`gray-200`). Direct labeling for small datasets. Tabular figures for numbers.

## 5. Overlays (Modals & Drawers)

- **Backdrop**: Dark or blurred mask (`bg-black/50 backdrop-blur-sm`). Scrim 40–60% opacity for legibility.
- **Modals**: For focused tasks requiring immediate attention (delete confirmation, payment). Must trap focus + `Escape` to close.
- **Drawers**: Side panels for complex forms or detail views to maintain page context.
- **Sheet Dismiss**: Confirm before dismissing with unsaved changes. Swipe-down to dismiss on mobile.
- **Animation**: Animate from trigger source (scale+fade or slide-in) for spatial context.
- **NEVER** use modals for primary navigation flows — they break the user's path.

## 6. Navigation

- **Top Nav / Header**: Max 5–7 links. Clear active indicator (color, weight, underline). Hamburger only on mobile (`md:hidden`), **NEVER on desktop**.
- **Bottom Nav (Mobile)**: Max 5 items. Icon + text label — icon-only harms discoverability. Top-level screens only.
- **Tabs**: 2–7 items. Horizontal scroll on overflow (mobile), or accordion for dense content.
- **Back Behavior**: Predictable and consistent. Preserve scroll position, filter state, input on navigate-back.
- **Deep Linking**: All key screens reachable via URL/deep link.
- **Adaptive**: ≥1024px → sidebar nav. Small screens → bottom/top nav.
- **Search**: Easily reachable (top bar or tab). Provide recent/suggested queries.
- **Consistency**: Nav placement same across all pages. Don't mix Tab + Sidebar + Bottom Nav at same hierarchy.
- **Destructive Actions**: Visually separated from normal nav. Semantic danger color (red).

## 7. Icons & Visual Elements

- **No Emoji Icons**: Use vector SVG icons (Lucide, Heroicons, `@expo/vector-icons`). Emoji are font-dependent, inconsistent, unthemeable.
- **Consistent Family**: One icon set with matching stroke width and corner radius across the product.
- **Sizing Tokens**: `icon-sm`, `icon-md` (24pt), `icon-lg`. No arbitrary mixed sizes.
- **Filled vs. Outline**: One style per hierarchy level. Don't mix randomly.
- **Alignment**: Icons aligned to text baseline with consistent padding.
- **Contrast**: 4.5:1 for small icon elements, 3:1 for larger UI glyphs.

*Adhering to these rules ensures the interface feels solid, familiar, and highly professional.*
