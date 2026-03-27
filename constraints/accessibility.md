# Baseline Accessibility, Touch & Performance Constraints

These are non-negotiable. Do not compromise for aesthetics.

## 1. Interactive Elements & ARIA

- **Icon-Only Buttons**: MUST have `aria-label` or `aria-labelledby`.
  - *Wrong*: `<button><LucideIcon /></button>`
  - *Right*: `<button aria-label="Close modal"><LucideIcon aria-hidden="true" /></button>`
- **Semantic HTML**: Always prefer `<button>`, `<a>` over `onClick` on `<div>`/`<span>`.
- **Forms**: Every input MUST have a `<label>`. Placeholder is not a substitute.
- **Color not only**: Don't convey info by color alone — add icon or text (e.g., error = red + icon + message).
- **Skip links**: Provide "Skip to main content" for keyboard users (web).
- **Heading hierarchy**: Sequential h1→h6, no level skipping.

## 2. Focus & Keyboard Navigation

- **Focus Indicators**: Never remove focus outlines without a visible replacement: `focus-visible:ring-2 focus-visible:ring-primary focus-visible:ring-offset-2`.
- **Tab Order**: Must match visual order. Full keyboard support for all interactive elements.
- **Modal Focus Trapping**: Modals, Dialogs, Drawers must trap focus while open and support `Escape` to close.
- **Route Change Focus**: After page transition, move focus to main content region for screen readers.
- **Keyboard Shortcuts**: Preserve system and a11y shortcuts. Offer keyboard alternatives for drag-and-drop.

## 3. Touch & Interaction (Mobile + Web)

- **Touch Target Size**: Min 44×44pt (Apple HIG) / 48×48dp (Material Design). Extend hit area with `hitSlop` if visual element is smaller.
- **Touch Spacing**: Min 8px/8dp gap between touch targets.
- **Press Feedback**: Visual feedback within 100ms — ripple, opacity change, scale (0.95–1.05). Restore on release.
- **No Hover Dependency**: Don't rely on hover for primary interactions. Use tap/click.
- **Loading Buttons**: Disable during async, show spinner or progress indicator.
- **Gesture Safety**: Don't override system gestures (iOS swipe-back, Android predictive back, Control Center). One primary gesture per region.
- **Safe Areas**: Keep touch targets away from notch, Dynamic Island, gesture bar, screen edges.
- **No Precision Required**: Don't require pixel-perfect taps on small icons or thin edges.
- **Tap Delay**: Use `touch-action: manipulation` to remove 300ms delay (web).

## 4. Motion & Performance

- **Reduced Motion**: MUST respect `prefers-reduced-motion`. Reduce or disable animations when requested.
- **Property Animation**: ONLY animate `transform` and `opacity`. Never `width`, `height`, `margin`, `padding`.
- **Duration**: Micro-interactions 150–300ms. Complex transitions ≤400ms. Exit animations = 60–70% of enter duration.
- **Interruptible**: User tap/gesture must cancel in-progress animations immediately.
- **No Blocking**: Never block user input during an animation.

## 5. Performance

- **Image Optimization**: WebP/AVIF, responsive `srcset`/`sizes`, lazy load below fold. Declare `width`/`height` or `aspect-ratio` for CLS prevention.
- **Font Loading**: `font-display: swap` or `optional`. Preload only critical fonts — don't preload every variant.
- **Critical CSS**: Prioritize above-the-fold styles. Inline critical CSS or early-loaded stylesheet.
- **Code Splitting**: Split by route/feature (React Suspense / Next.js dynamic). Lazy load non-hero components.
- **List Virtualization**: Virtualize lists with 50+ items for memory and scroll performance.
- **Main Thread Budget**: ≤16ms per frame for 60fps. Move heavy tasks off main thread.
- **Progressive Loading**: Skeleton screens / shimmer for >1s operations. Never long blocking spinners.
- **Debounce/Throttle**: Required for scroll, resize, input events.

## 6. Typography Readability

- **Minimum Size**: Body text ≥14px (preferably 16px). Min 16px on mobile to avoid iOS auto-zoom.
- **Heading Hierarchy**: Sequential levels, never skip.
- **Contrast**: WCAG AA minimum (4.5:1 normal text, 3:1 large text) in both light AND dark mode.
- **Line Height**: 1.5–1.75 for body text.
- **Line Length**: 60–75 chars on desktop, 35–60 on mobile.
- **Text Wrapping**: `text-balance` for headings, `text-pretty` for paragraphs.
- **Truncation**: Prefer wrapping. When truncating, use ellipsis + provide full text via tooltip/expand.
- **Dynamic Type**: Support system text scaling without layout breakage (mobile).

## 7. Screen Reader Support

- **VoiceOver/TalkBack**: Meaningful `accessibilityLabel`/`accessibilityHint`. Logical reading order.
- **ARIA Live Regions**: Form errors use `aria-live="polite"` or `role="alert"`.
- **Accessibility Traits**: Correct roles/states — selected, disabled, expanded must be announced.
- **Charts**: Provide text summary or `aria-label` describing the chart's key insight.
- **Toasts**: Must not steal focus. Use `aria-live="polite"`.

*If your generated code violates any of these principles, it fails the quality check.*
