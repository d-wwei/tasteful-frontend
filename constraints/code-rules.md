# Code-Level Implementation Rules

These rules are for **design-to-code-runner** and other code-generation tools. They are NOT used during design spec generation — tasteful-frontend references `accessibility.md` and `components.md` instead.

## 1. Tech Stack Defaults

- **Web default**: React + Tailwind CSS. Use `lucide-react` for icons.
- **Also supported**: Next.js, Vue, Svelte, HTML/CSS (web); SwiftUI, React Native, Flutter (mobile).
- Adapt rules to target platform idioms.

## 2. CSS & HTML Rules

### Accessibility Implementation
- Icon-only buttons: `<button aria-label="Close modal"><LucideIcon aria-hidden="true" /></button>`
- Semantic HTML: Always prefer `<button>`, `<a>` over `onClick` on `<div>`/`<span>`.
- Every input MUST have a `<label>`. Placeholder is not a substitute.
- Focus indicators: `focus-visible:ring-2 focus-visible:ring-primary focus-visible:ring-offset-2`. Never remove outlines without visible replacement.
- Form errors: `aria-live="polite"` or `role="alert"`.
- Skip links: Provide "Skip to main content" for keyboard users (web).

### Layout Implementation
- `min-h-dvh` over `100vh` on mobile.
- `width=device-width, initial-scale=1` viewport meta. Never disable zoom.
- Tailwind spacing: `p-4` = 16px, `gap-6` = 24px, `m-8` = 32px.
- Container: `max-w-6xl` or `7xl` on desktop.
- Z-index scale: 0 / 10 / 20 / 40 / 100 / 1000. No arbitrary values.
- Hamburger nav: `md:hidden` only. NEVER on desktop.

### Touch Implementation
- Touch target extension: Use `hitSlop` if visual element is smaller than 44×44pt / 48×48dp.
- Tap delay removal: `touch-action: manipulation` (web).
- Press feedback: ripple, opacity change, scale (0.95–1.05). Restore on release.

### Performance Implementation
- Images: WebP/AVIF, responsive `srcset`/`sizes`, lazy load below fold. Declare `width`/`height` or `aspect-ratio` for CLS prevention.
- Fonts: `font-display: swap` or `optional`. Preload only critical fonts.
- Critical CSS: Prioritize above-the-fold styles. Inline critical CSS or early-loaded stylesheet.
- Code splitting: Split by route/feature (React Suspense / Next.js dynamic). Lazy load non-hero components.
- List virtualization: Virtualize lists with 50+ items.
- Main thread budget: ≤16ms per frame. `debounce`/`throttle` for scroll, resize, input events.

### Animation Implementation
- ONLY animate `transform` and `opacity`. Never `width`, `height`, `margin`, `padding`.
- `prefers-reduced-motion`: respect it. Reduce or disable animations.
- Animations must be interruptible by user tap/gesture.
- CSS-only solutions preferred for HTML; Motion library for React.

### Typography Implementation
- `text-balance` for headings. `text-pretty` for paragraphs.
- Tabular figures for data columns.
- Min 16px on mobile to avoid iOS auto-zoom.
- Truncation: ellipsis + full text via tooltip/expand.

### Component Implementation
- Modals: trap focus + `Escape` to close. Dark/blurred backdrop: `bg-black/50 backdrop-blur-sm`.
- Drawers: side panels for complex forms.
- Disabled states: Reduced opacity (0.38–0.5) + cursor change + semantic attribute.
- Password fields: Show/hide toggle. Support autofill (`autocomplete` / `textContentType`).
- Input types: Use semantic types (`email`, `tel`, `number`) for correct mobile keyboard.
- Overlays: Scrim 40–60% opacity. Animate from trigger source (scale+fade or slide-in).

## 3. Platform-Specific Code Rules

### Web
- `viewport meta`: `width=device-width, initial-scale=1`, never disable zoom.
- `z-index` scale: 0/10/20/40/100/1000. Skip links for keyboard users.
- Breadcrumbs for 3+ level deep hierarchies.

### iOS (SwiftUI / React Native)
- Dynamic Type support — avoid truncation as text grows.
- Haptic feedback for confirmations.
- Safe area compliance: notch, Dynamic Island, gesture bar.
- System controls preferred over custom unless branding requires it.

### Android (Material Design / React Native / Flutter)
- Material state layers for press/hover/focus.
- Predictive back gesture support.
- Ripple feedback on press.
- Elevation scale for cards/sheets/modals.

## 4. Anti-Patterns (Code Level)

### Engineering Failures
- Forms with placeholder text but no `<label>`.
- Focus outlines removed with no replacement.
- Animating `width`/`height`/`margin`/`padding` (layout thrashing).
- Emoji as structural icons (use SVG — Lucide, Heroicons, `@expo/vector-icons`).

### Code Quality
- No `// TODO` in delivered code. No broken/incomplete output.
- Semantic HTML. Native interactive elements preferred.

*This file is referenced by design-to-code-runner during implementation, NOT by tasteful-frontend during spec generation.*
