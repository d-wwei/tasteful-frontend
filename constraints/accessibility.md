# Baseline Accessibility, Touch & Performance Constraints

These are non-negotiable. Do not compromise for aesthetics. These rules guide **design spec generation** — for code-level implementation details, see `code-rules.md`.

## 1. Interactive Elements

- All interactive elements must have accessible labels. Icon-only buttons require text alternatives.
- Prefer native interactive semantics over custom click handlers.
- Every input needs a visible label. Placeholder text is not a substitute.
- Never convey information by color alone — pair with icon or text (e.g., error = color + icon + message).
- Heading hierarchy must be sequential (h1→h6), no level skipping.

## 2. Focus & Keyboard Navigation

- All interactive elements must have visible focus indicators. Never remove focus visibility without a clear replacement.
- Tab order must match visual order. Full keyboard access for all interactions.
- Modals, dialogs, and drawers must trap focus while open and support dismissal via keyboard.
- After page transitions, focus should move to the main content region.

## 3. Touch & Interaction

- **Touch target size**: Minimum 44×44pt (iOS) / 48×48dp (Android). Extend hit area if visual element is smaller.
- **Touch spacing**: Minimum 8px gap between adjacent touch targets.
- **Press feedback**: Visual feedback within 100ms on every tappable element.
- **No hover dependency**: All interactions must work with tap/click. Hover is enhancement only.
- **Loading buttons**: Disable during async operations, show progress indicator.
- **Gesture safety**: Don't override platform system gestures (swipe-back, predictive back, control center).
- **Safe areas**: Keep interactive elements away from notch, Dynamic Island, gesture bar, screen edges.
- **No precision required**: Don't require pixel-perfect taps on small targets.

## 4. Motion & Performance

- MUST respect `prefers-reduced-motion`. Reduce or disable animations when user requests it.
- Only animate properties that don't trigger layout recalculation (transform, opacity).
- Micro-interactions: 150–300ms. Complex transitions: ≤400ms. Exit faster than enter (60–70% duration).
- Animations must be interruptible by user action.
- Never block user input during an animation.

## 5. Performance

- Images: Use modern formats (WebP/AVIF), responsive sizing, lazy load below fold. Reserve space to prevent layout shift.
- Fonts: Preload only critical fonts. Use swap/optional loading strategy.
- Progressive loading: Skeleton screens for operations >1s. Never long blocking spinners.
- Lists with 50+ items should be virtualized.

## 6. Typography Readability

- Body text minimum 14px (preferably 16px). Minimum 16px on mobile.
- WCAG AA contrast: 4.5:1 for normal text, 3:1 for large text — in both light AND dark mode.
- Line height: 1.5–1.75 for body text.
- Line length: 60–75 characters on desktop, 35–60 on mobile.
- Support system text scaling (Dynamic Type) without layout breakage on mobile.

## 7. Screen Reader Support

- All visual elements need meaningful accessibility labels. Logical reading order required.
- Form errors must be announced to assistive technology.
- Interactive states (selected, disabled, expanded) must be announced.
- Charts must have text summary describing the key insight.
- Toast notifications must not steal focus.

*These constraints inform design token choices (contrast ratios, spacing values, touch target dimensions) and layout spec decisions (component sizing, interaction patterns).*

---

## Deep Accessibility Reference

Extended guidance beyond the baseline constraints above. Organized by WCAG compliance level, keyboard navigation, focus management, color testing, and ARIA usage.

### WCAG Compliance Matrix

| Criterion | AA (Minimum) | AAA (Enhanced) | When AAA Is Required |
|-----------|-------------|----------------|---------------------|
| **Text contrast** | 4.5:1 | 7:1 | Government, healthcare, education, high-readability contexts |
| **Large text contrast** (18px+ / 14px bold) | 3:1 | 4.5:1 | When body text meets AAA, large text should too for consistency |
| **UI component contrast** (borders, icons, controls) | 3:1 | 4.5:1 (informal target) | When non-text elements carry critical information |
| **Focus indicator contrast** | 3:1 against adjacent colors | Enhanced visible area | Always -- focus visibility is non-negotiable |
| **Target size** | 24x24px (WCAG 2.2) | 44x44px | Touch interfaces, users with motor impairments |
| **Text spacing** | Must survive 1.5x line-height, 2x letter-spacing, 2x word-spacing without loss | -- | All web content |
| **Reflow** | Content usable at 400% zoom / 320px width | -- | All web content |
| **Motion** | Respect `prefers-reduced-motion` | Provide user control for all motion | When animations are integral to the experience |

**Design-level decision**: Target AA as the baseline for all projects. Target AAA for text contrast (7:1) when the audience includes older adults, users with low vision, or contexts where extended reading is expected (documentation, editorial, healthcare).

### Keyboard Navigation Deep Rules

#### Tab Order Principles

- Tab order must follow visual reading order (left-to-right, top-to-bottom for LTR languages).
- Never use `tabindex` values greater than 0. This overrides natural document order and creates unpredictable navigation.
- `tabindex="0"` adds an element to the natural tab order. Use only when a non-interactive element must be focusable.
- `tabindex="-1"` makes an element programmatically focusable (via JavaScript) but removes it from the tab sequence. Use for focus management (moving focus to a heading after navigation).

#### Expected Keyboard Patterns by Component

| Component | Expected Keys | Behavior |
|-----------|--------------|----------|
| **Button** | Enter, Space | Activates the button |
| **Link** | Enter | Follows the link |
| **Checkbox** | Space | Toggles checked state |
| **Radio group** | Arrow keys | Moves selection within the group |
| **Select / Dropdown** | Arrow keys, Enter, Escape | Navigate options, select, close |
| **Tabs** | Arrow keys (horizontal), Enter/Space | Switch between tabs |
| **Dialog / Modal** | Escape, Tab (trapped) | Close dialog, cycle through focusable elements |
| **Menu** | Arrow keys, Enter, Escape | Navigate items, activate, close |
| **Accordion** | Enter/Space, Arrow keys | Toggle section, move between headers |
| **Slider** | Arrow keys, Home, End | Adjust value, jump to min/max |
| **Tree view** | Arrow keys, Enter/Space | Navigate nodes, expand/collapse |

### Focus Trap Checklist

When a modal, dialog, drawer, or overlay opens:

- [ ] Focus moves to the first focusable element inside the container (or the container itself if it has `tabindex="-1"`)
- [ ] Tab cycling is confined within the container -- Tab from the last element loops back to the first; Shift+Tab from the first loops to the last
- [ ] Escape key closes the container
- [ ] On close, focus returns to the element that triggered the opening
- [ ] Background content is inert (`aria-hidden="true"` on the rest of the page, or `inert` attribute)
- [ ] Page scroll is prevented while the trap is active (the background should not scroll)
- [ ] Focus trap does not interfere with browser chrome or assistive technology navigation

### Color Blind Testing Tools

| Tool | Type | Best For |
|------|------|----------|
| **Chrome DevTools** > Rendering > Emulate vision deficiencies | Browser built-in | Quick checks during development |
| **Polypane** | Multi-viewport browser | Side-by-side comparison of normal vision and simulated deficiencies |
| **Stark** (Figma/Sketch plugin) | Design tool plugin | Checking designs before handoff to development |
| **Sim Daltonism** (macOS) | System-level filter | Testing any application, not just web |
| **Color Oracle** (cross-platform) | System-level filter | Free, works on any OS |
| **WebAIM Contrast Checker** | Web tool | Verifying specific color pair contrast ratios |

**Minimum testing protocol**: Before shipping any interface with status colors (success/error/warning), test under deuteranopia simulation (the most common form, affecting ~5% of men). If red and green states are indistinguishable, add icon or text differentiation.

### ARIA Role Quick Reference

ARIA supplements native HTML semantics. **Prefer native elements first** -- a `<button>` is always better than `<div role="button">`.

#### When ARIA Is Necessary

| Situation | ARIA Solution |
|-----------|--------------|
| Custom toggle/switch component | `role="switch"`, `aria-checked="true/false"` |
| Icon-only interactive element | `aria-label="descriptive text"` on the button |
| Expandable content | `aria-expanded="true/false"` on the trigger, `aria-controls="panel-id"` |
| Live content updates | `aria-live="polite"` (non-urgent) or `aria-live="assertive"` (urgent) on the update region |
| Required form field | `aria-required="true"` (supplement visible indicator) |
| Invalid form field | `aria-invalid="true"`, `aria-describedby="error-message-id"` |
| Disabled interactive element | `aria-disabled="true"` (when using `disabled` attribute is not possible) |
| Loading state | `aria-busy="true"` on the loading region |
| Tab interface | `role="tablist"`, `role="tab"`, `role="tabpanel"`, `aria-selected` |
| Dialog / Modal | `role="dialog"`, `aria-modal="true"`, `aria-labelledby="title-id"` |
| Navigation landmark | `role="navigation"` or `<nav>` with `aria-label` when multiple navs exist |

#### Common ARIA Mistakes

- **Overriding native semantics**: Adding `role="button"` to a `<button>` is redundant and can confuse screen readers.
- **Missing required attributes**: `role="slider"` requires `aria-valuemin`, `aria-valuemax`, and `aria-valuenow`.
- **Using `aria-label` on non-interactive elements**: Screen readers may ignore `aria-label` on `<div>` or `<span>` without a role.
- **Hiding content that should be accessible**: `aria-hidden="true"` on an interactive element makes it invisible to screen readers but still focusable by keyboard, creating a confusing ghost element.
- **Using `aria-live` too aggressively**: `aria-live="assertive"` interrupts the current screen reader announcement. Reserve for critical errors. Use `"polite"` for most updates.

### Announcement Strategy

| Event | Announcement Method | Priority |
|-------|-------------------|----------|
| Form validation error | `aria-live="assertive"` on error summary, `aria-describedby` on individual fields | Assertive -- user needs to know immediately |
| Toast/notification (success) | `role="status"` or `aria-live="polite"` | Polite -- announced after current speech |
| Loading started | `aria-busy="true"` on loading region | Implicit -- screen reader notes busy state |
| Loading complete | `aria-busy="false"`, optional `aria-live="polite"` announcement | Polite -- "Content loaded" |
| Dynamic content update (feed, chat) | `aria-live="polite"` on the container | Polite -- new messages announced in queue |
| Critical system alert | `role="alert"` (equivalent to `aria-live="assertive"`) | Assertive -- immediate interruption |
