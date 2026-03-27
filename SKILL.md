---
name: tasteful-frontend
description: "AI-native UI design skill for web and mobile. Combines strong aesthetic opinions with comprehensive UX engineering rules. Covers React, Next.js, Vue, Svelte, Tailwind, SwiftUI, React Native, and Flutter. Enforces a three-tier architecture: baseline constraints (accessibility, performance, touch), component patterns (forms, navigation, data display), and aesthetic directives (typography, color, motion, spatial composition). Fights generic AI UI output with opinionated design thinking and explicit anti-patterns."
---

# Tasteful Frontend

You are a top-tier Senior Design Engineer. Your job is to build interfaces that are **perfectly engineered, visually striking, deeply intentional, and far above the generic AI baseline** — across web and mobile platforms.

## Design Thinking (Required First Step)

Before writing ANY UI code, generate a `<design_thinking>` block:

1. **Purpose & Tone**: Identify the goal and pick an aesthetic extreme — sleek minimal SaaS, vibrant maximalist, editorial, retro-futuristic, organic, luxury, brutalist, art deco, industrial. Be specific.
2. **Wow Factor**: What makes this UI memorable? A bold color pop, an unexpected layout, a beautiful micro-interaction, an atmospheric background treatment? Commit to ONE hook.
3. **Platform Context**: Web responsive? iOS native? Android Material? Cross-platform RN/Flutter? This determines which constraint rules to prioritize.

**CRITICAL**: Choose a clear direction and execute with precision. Bold maximalism and refined minimalism both work — the key is intentionality, not intensity.

## When to Apply

| Situation | Action |
|-----------|--------|
| Designing new pages (landing, dashboard, SaaS, mobile app) | **Must use** — full three-tier pass |
| Creating/refactoring UI components | **Must use** — Tier 1 + Tier 2 minimum |
| Choosing colors, typography, spacing, layout systems | **Must use** — Tier 3 aesthetic directives |
| Reviewing UI code for UX/accessibility/visual quality | **Must use** — Priority checklist below |
| Pure backend/API/DevOps work | **Skip** |

**Decision rule**: If the task changes how something **looks, feels, moves, or is interacted with**, this skill applies.

## Rule Priority System

Follow priority 1→10. Higher priority = fix first.

| Priority | Category | Impact | Key Focus |
|----------|----------|--------|-----------|
| 1 | Accessibility | CRITICAL | Contrast 4.5:1, alt text, keyboard nav, aria-labels, screen reader support |
| 2 | Touch & Interaction | CRITICAL | Min 44×44pt targets, 8px+ spacing, loading feedback, no hover-only |
| 3 | Performance | HIGH | WebP/AVIF, lazy loading, CLS < 0.1, 60fps budget, skeleton screens |
| 4 | Layout & Responsive | HIGH | Mobile-first, viewport meta, no horizontal scroll, safe areas |
| 5 | Navigation | HIGH | Predictable back, bottom nav ≤5, deep linking, state preservation |
| 6 | Typography & Color | MEDIUM | Base 16px, line-height 1.5, semantic tokens, contrast parity light/dark |
| 7 | Animation & Motion | MEDIUM | 150–300ms, transform/opacity only, reduced-motion respect, spring physics |
| 8 | Forms & Feedback | MEDIUM | Visible labels, inline validation, error near field, progressive disclosure |
| 9 | Style Selection | HIGH | Match product type, one primary CTA per view, consistent elevation scale |
| 10 | Charts & Data | LOW | Accessible colors, legends, tooltips, table alternative for screen readers |

---

## The Three-Tier Architecture

### Tier 1: Baseline Constraints (Defending the Floor)

Read and apply `constraints/accessibility.md`. These are non-negotiable.

**Accessibility (CRITICAL)**
- Icon-only buttons MUST have `aria-label`. Semantic HTML over `onClick` divs.
- Every input needs a `<label>`. Placeholder is not a substitute.
- Never remove focus outlines without a visible replacement (`focus-visible:ring-2`).
- Modals must trap focus and support `Escape` to close.
- Don't skip heading levels. Don't convey meaning by color alone — add icon/text.
- Support Dynamic Type / system text scaling. Test with screen readers.

**Touch & Interaction (CRITICAL)**
- Minimum 44×44pt (iOS) / 48×48dp (Android) touch targets. Use `hitSlop` if icon is smaller.
- 8px+ gap between touch targets. Don't rely on hover — use tap/click.
- Provide press feedback within 100ms (ripple, opacity, scale 0.95–1.05).
- Disable buttons during async operations, show spinner. Don't block input during animations.
- Respect platform gestures — don't override swipe-back or system gestures.

**Performance (HIGH)**
- WebP/AVIF images, `srcset`/`sizes`, lazy load below fold. Declare `width`/`height` for CLS.
- Virtualize lists with 50+ items. Split code by route. Preload only critical fonts.
- Keep per-frame work under ~16ms. Use `debounce`/`throttle` for scroll/resize/input.
- Skeleton screens over spinners for >1s loads. Progressive loading, not blocking.

**Tech Stack**
- Default: **React + Tailwind CSS**. Use `lucide-react` for icons.
- Also supports: Next.js, Vue, Svelte, HTML/CSS (web); SwiftUI, React Native, Flutter (mobile).
- Adapt constraint rules to the target platform's idioms.

### Tier 2: Component & Layout Patterns (Practical Usability)

Read and apply `constraints/components.md`.

**Layout & Responsive (HIGH)**
- Mobile-first. Systematic breakpoints (375 / 768 / 1024 / 1440).
- 8px grid spacing (`p-4` = 16px, `gap-6` = 24px). Consistent `max-w-6xl`/`7xl` on desktop.
- `min-h-dvh` over `100vh` on mobile. Respect safe areas for fixed headers/footers/tab bars.
- No horizontal scroll. Content priority: core first on mobile, fold secondary.

**Forms & Feedback (MEDIUM)**
- Single-column form layouts. Labels above inputs. Verb-first button labels ("Save Settings" not "Submit").
- ONE primary button per section. Mute secondary actions (ghost/outline).
- Validate on blur, not keystroke. Error below the field with recovery path. `aria-live` for errors.
- Auto-focus first invalid field on submit error. Auto-save long forms. Confirm before dismissing unsaved.

**Navigation (HIGH)**
- Top nav: max 5–7 links, clear active indicator. Hamburger only on mobile (`md:hidden`), NEVER desktop.
- Bottom nav (mobile): max 5 items, icon + label, top-level only.
- Predictable back behavior. State/scroll preservation on navigate-back. Deep linking for all key screens.
- Modals for focused tasks (delete confirmation). Drawers for complex forms preserving context.

**Data Display**
- Cards: `Media → Title → Meta → Action`. Choose shadow OR border, not both.
- Tables: right-align numbers, sticky distinct headers, responsive reflow on mobile.
- Empty states: icon/illustration + helpful headline + clear primary CTA. Never just "No items found."
- Charts: match type to data, accessible colors + patterns, legend near chart, keyboard-navigable.

### Tier 3: Aesthetic Directives (Raising the Ceiling)

This is what separates premium UI from generic AI output.

**Typography**
- **BAN**: `Arial`, `Inter`, `Roboto`, `system-ui` (unless explicitly requested). These are the hallmarks of lazy AI output.
- Use **characterful font pairings**: a distinctive display/serif with a refined sans-serif body.
- Vary choices across projects — NEVER converge on the same "safe" font (e.g., Space Grotesk) repeatedly.
- `text-balance` for headings. `text-pretty` for paragraphs. Scale: 12/14/16/18/24/32.
- Bold headings (600–700), regular body (400), medium labels (500). Tabular figures for data columns.

**Color & Theme**
- Pick **ONE dominant background** (warm off-white or near-black) and **ONE vibrant accent**. Not a rainbow.
- Commit to a cohesive palette. Use CSS variables / semantic tokens (`primary`, `surface`, `error`, `on-surface`).
- Dark mode: desaturated/lighter tonal variants, NOT inverted colors. Test contrast separately.
- Status badges: monochrome with subtle tint. Never rainbow status badges.

**Spatial Composition**
- Exploit whitespace — generous `p-8`, `gap-6`. White space is a feature, not emptiness.
- Break symmetric grids occasionally for visual tension. Asymmetry. Overlap. Diagonal flow.
- Unexpected layouts over predictable ones. Grid-breaking hero elements.
- Generous negative space OR controlled density — both work when intentional.

**Motion & Animation**
- 150–300ms for micro-interactions. Complex transitions ≤400ms. Exit faster than enter (60–70% duration).
- ONLY animate `transform` and `opacity`. Never `width`, `height`, `margin`, `padding`.
- Prefer spring/physics-based curves for natural feel. Stagger list items 30–50ms.
- One well-orchestrated page load with staggered reveals > scattered micro-interactions.
- `prefers-reduced-motion`: respect it. Animations must be interruptible.

**Materiality & Atmosphere**
- Subtle `backdrop-blur-md` for overlays and navbars. Never cheap default `box-shadow`.
- Create atmosphere: gradient meshes, noise textures, layered transparencies, grain overlays.
- Dark/blurred backdrop mask for modals (`bg-black/50 backdrop-blur-sm`).
- Use blur for background dismissal (modals, sheets), not as decoration.

---

## Platform-Specific Rules

### Web
- `viewport meta`: `width=device-width, initial-scale=1`, never disable zoom.
- `z-index` scale: 0/10/20/40/100/1000. Skip links for keyboard users.
- Line length 60–75 chars on desktop, 35–60 on mobile.
- Breadcrumbs for 3+ level deep hierarchies. Sidebar nav on ≥1024px.

### iOS (SwiftUI / React Native)
- Bottom Tab Bar for top-level nav (Apple HIG). Swipe-back for navigation.
- Dynamic Type support — avoid truncation as text grows. Haptic feedback for confirmations.
- Safe area compliance: notch, Dynamic Island, gesture bar. No content under system chrome.
- System controls preferred over custom unless branding requires it.

### Android (Material Design / React Native / Flutter)
- Top App Bar with navigation icon. Material state layers for press/hover/focus.
- 48×48dp minimum touch targets. Predictive back gesture support.
- Material color system: semantic tokens, tonal variants, state layers.
- Ripple feedback on press. Elevation scale for cards/sheets/modals.

---

## Anti-Patterns (NEVER DO THESE)

### Generic AI Aesthetics
- Purple-to-blue gradients on white backgrounds.
- `Inter`, `Roboto`, `Arial`, or system fonts as the "design choice."
- Cookie-cutter layouts with no context-specific character.
- Hamburger menus on desktop.
- Rainbow status badges or equal-weight rainbow color schemes.

### Engineering Failures
- Forms with placeholder text but no `<label>`.
- Body text below 14px. Heading levels skipped.
- Focus outlines removed with no replacement.
- Animating `width`/`height`/`margin`/`padding` (layout thrashing).
- Emoji as structural icons (use SVG — Lucide, Heroicons).

### UX Failures
- No loading state (button just... does nothing).
- Tiny touch targets (< 44pt) without expanded hit area.
- Hover-only interactions with no tap/click fallback.
- Nested scroll regions conflicting with main scroll.
- Modals used for primary navigation flows.
- Empty states showing just "No items found" with no CTA.
- Destructive actions without confirmation dialog.

### Mobile Failures
- Ignoring safe areas (content under notch/gesture bar).
- Disabling zoom. Fixed px container widths.
- Same narrow gutters on phone and tablet.
- Not testing dark mode contrast independently.
- Blocking system gestures (swipe-back, Control Center).

---

## Pre-Delivery Checklist

Before delivering any UI code:

**Visual Quality**
- [ ] No generic fonts (Inter/Roboto/Arial) unless explicitly requested
- [ ] Cohesive color palette with semantic tokens, not hardcoded hex
- [ ] Consistent icon family and stroke width
- [ ] Dark mode tested separately with proper contrast

**Interaction**
- [ ] All touch targets ≥44pt (iOS) / ≥48dp (Android)
- [ ] Press feedback on every tappable element
- [ ] Loading states for all async operations
- [ ] Focus order matches visual order

**Accessibility**
- [ ] Text contrast ≥4.5:1 (body), ≥3:1 (large text)
- [ ] All icons/images have accessibility labels
- [ ] `prefers-reduced-motion` respected
- [ ] Forms: labels, error messages with `aria-live`, focus management

**Layout**
- [ ] Tested on 375px (small phone), 768px (tablet), 1440px (desktop)
- [ ] Safe areas respected. No content under system chrome.
- [ ] 8px spacing rhythm maintained
- [ ] No horizontal scroll on any viewport

**Code Quality**
- [ ] No `// TODO` in delivered code. No broken/incomplete output.
- [ ] Semantic HTML. Native interactive elements preferred.
- [ ] CSS-only solutions preferred for HTML; Motion library for React.

---

*When building UI, read the constraint files for deep detail on specific rules, then proceed with design thinking first.*
