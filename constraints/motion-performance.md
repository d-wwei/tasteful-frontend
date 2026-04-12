# Motion Performance Constraints

Design-layer guidance for understanding animation performance implications. This file helps designers make informed decisions about which motion approaches are achievable at 60fps and which will cause jank. For timing, easing, and choreography theory, see `motion-deep.md`. For code-level implementation, see `code-rules.md`.

---

## Rendering Steps: What Designers Need to Know

Every animation triggers work in the browser's rendering pipeline. The more work triggered, the more likely the animation drops frames.

### The Three Rendering Tiers

| Tier | Properties | Cost | Frame Budget Impact |
|------|-----------|------|-------------------|
| **Composite** | `transform`, `opacity` | Cheapest -- handled by the GPU | Nearly free. Animate these freely. |
| **Paint** | `color`, `background`, `border-color`, `box-shadow`, `filter`, `mask` | Medium -- the browser must repaint affected pixels | Acceptable on small, isolated elements. Problematic on large surfaces. |
| **Layout** | `width`, `height`, `top`, `left`, `margin`, `padding`, `font-size`, `grid-template-*` | Expensive -- triggers reflow of the entire document or subtree | Avoid animating continuously. One-shot transitions on small elements are tolerable. |

### Design Implications

- **Safe to animate anytime**: position (via `transform: translate`), scale (`transform: scale`), rotation (`transform: rotate`), opacity
- **Safe on small elements only**: background color transitions, border color, box-shadow intensity changes
- **Avoid animating**: width, height, padding, margin, top/left/right/bottom, font-size -- anything that changes the element's box model dimensions

**Design rule**: When specifying motion in a design spec, prefer transforms for positional changes. Instead of "the panel animates from width: 0 to width: 300px," specify "the panel scales from scaleX(0) to scaleX(1)" or "the panel translates from translateX(-300px) to translateX(0)." The visual result is often identical; the performance cost is dramatically different.

---

## FLIP Transition Technique

### The Design Principle

FLIP (First, Last, Invert, Play) enables layout-like animations using only compositor properties. The technique:

1. **First**: Record the element's starting position/size
2. **Last**: Apply the final layout state instantly (no animation)
3. **Invert**: Calculate the difference and apply a `transform` that makes the element appear to be back in its starting position
4. **Play**: Animate the removal of that transform, so the element glides from the old position to the new one

### When Designers Should Request FLIP

- **List reordering**: Items moving to new positions in a sorted or filtered list
- **Layout transitions**: Elements shifting between grid configurations (e.g., 3-column to 2-column)
- **Shared element transitions**: An element on one page becoming an element on the next page
- **Expand/collapse**: An element growing from a small state to a large state while content repositions around it

### Design Constraints of FLIP

- The animation is inherently constrained to `transform` and `opacity` -- you cannot FLIP changes to border-radius, color, or shadow during the transition. Those must change discretely (instant switch) or via a separate paint-tier animation.
- FLIP transitions look best at 300-500ms with expo-out or quart-out easing.
- Complex FLIP sequences (multiple elements repositioning simultaneously) require careful choreography to avoid visual chaos. Stagger the individual FLIP animations by 30-50ms.

---

## Blur Animation Constraints

### Why Blur Is Expensive

`filter: blur()` is a paint-tier operation. The browser must sample every pixel within the blur radius to compute the blurred output. Cost scales with both the blur radius and the surface area of the element.

### Hard Limits for Designers

| Rule | Limit | Rationale |
|------|-------|-----------|
| Maximum animated blur radius | 8px | Beyond 8px, per-frame computation exceeds budget on mid-range devices |
| Duration of blur animation | ≤300ms | Keep it short to minimize total frames computed |
| Usage frequency | One-time effect only | Never animate blur continuously or in loops |
| Surface area | Small elements only | Never blur-animate full-screen or large container surfaces |
| Preferred alternative | `opacity` + `transform` | Achieves a similar "soft appearance" effect at compositor cost |

### Backdrop Filter Caution

`backdrop-filter: blur()` is even more expensive than `filter: blur()` because it blurs the content *behind* the element, requiring the browser to composite, blur, and re-composite for every frame.

**Design rule**: Use `backdrop-filter` for static elements (glass-effect navigation bars that do not animate). Never animate `backdrop-filter` values. If you need a "glass appearing" effect, animate the element's `opacity` from 0 to 1 while the backdrop-filter remains at its final static value.

---

## Layer Promotion Principles

### What Layer Promotion Means for Design

When an element is promoted to its own GPU layer, it can be composited independently -- meaning transforms and opacity changes on that element do not require the browser to repaint anything else.

### When to Expect Layer Promotion

- Elements with active `transform` or `opacity` animations are typically auto-promoted
- Elements with `will-change: transform` or `will-change: opacity` are explicitly promoted
- Elements with `position: fixed` or `position: sticky` are often promoted

### Design Implications of Over-Promotion

Each promoted layer consumes GPU memory. Too many promoted layers (or very large promoted layers) can cause:

- **Memory pressure**: Each layer stores a full-resolution bitmap. A 1920x1080 layer at 2x display density = ~16MB of GPU memory.
- **Compositing overhead**: More layers = more work for the GPU to composite each frame.
- **Mobile degradation**: Mobile GPUs have significantly less memory and compositing bandwidth than desktop GPUs.

**Design rule**: Not every animated element needs to be on its own layer. Prioritize layer promotion for:
1. Elements that animate continuously during interaction (scroll-linked elements, drag handles)
2. Large elements that move or fade (modals, drawers, full-screen overlays)
3. Elements that overlap other animated elements

Do not promote:
- Static elements that never animate
- Many small elements simultaneously (e.g., every cell in a table)
- Very large surfaces (full-page backgrounds)

---

## View Transitions

### Design Considerations

The View Transition API enables animated transitions between page states (navigation, content swaps) with built-in cross-fade and morph capabilities.

### When to Use View Transitions

- **Navigation-level changes**: Page-to-page navigation where visual continuity helps orientation
- **Major content swaps**: Switching between significantly different views (list to detail, tab to tab)
- **Shared element morphs**: An element visually traveling from one page/view to another

### When NOT to Use View Transitions

- **Interaction-heavy UI**: Components that change frequently during user interaction (form inputs, real-time updates)
- **Interruptible flows**: User actions that need to be cancellable mid-animation
- **Sub-component state changes**: Tab panels, accordion content, dropdown reveals -- these need immediate, lightweight transitions, not full view transitions

### Design Constraints

- View transitions capture snapshots of old and new states. During the transition, interactive elements are temporarily inert.
- Size changes during view transitions may trigger layout-tier work. Morph transitions between different-sized elements require careful testing on target devices.
- View transitions add latency between the user's action and the final state. For rapid interactions (tab switching, filter application), this latency can feel sluggish.

---

## Scroll-Driven Animation Caution

### The Appeal and the Risk

Scroll-driven animations (elements that animate in response to scroll position) create engaging, dynamic experiences. They are also the most common source of motion performance issues and vestibular disorder triggers.

### Performance Rules

- **Use CSS Scroll Timeline** (when available) instead of JavaScript scroll event listeners. CSS scroll timelines run on the compositor thread and do not block the main thread.
- **Never poll scroll position** in JavaScript for animation. This causes layout reads on every frame and is the primary cause of scroll jank.
- **Use IntersectionObserver** for visibility-triggered animations. Observe once, animate once, unobserve. Do not re-animate elements that have already been revealed.
- **Limit scroll-driven animation to compositor properties** (transform, opacity). Scroll-driving a paint or layout property on a large surface will cause visible jank on most devices.

### Design Rules for Scroll Motion

- **Scroll-reveal animations should fire once**, not repeatedly. An element that fades in when scrolled into view should stay visible, not re-animate when scrolled away and back.
- **Parallax effects must be subtle**. A parallax ratio of 0.1-0.3 (element moves at 10-30% of scroll speed) is perceptible but not nauseating. Ratios above 0.5 are aggressive.
- **Always disable scroll-linked motion under `prefers-reduced-motion`**. Scroll-triggered spatial displacement is the single most common trigger for vestibular symptoms.
- **Test on low-end mobile devices**. Scroll-driven animations that feel smooth on a MacBook Pro may jank badly on a 3-year-old Android phone.

---

## Performance Testing Guidance for Designers

### What to Check Before Specifying Motion

1. **Surface area**: How large is the animated element? Full-screen animations are expensive; icon-sized animations are nearly free.
2. **Property tier**: Are you animating composite, paint, or layout properties? Composite is safe; paint is conditional; layout is expensive.
3. **Duration and frequency**: Is this a one-shot animation or continuous? One-shot paint-tier animations are acceptable; continuous ones are not.
4. **Device target**: Is this for desktop only, or must it perform on mobile? Mobile has ~3-5x less GPU budget.
5. **Concurrent animations**: How many elements animate simultaneously? More concurrent animations = more compositor work = more likely to drop frames.

### Frame Budget

At 60fps, each frame has 16.67ms of budget. Animation rendering must complete within this window. At 120fps (ProMotion displays), the budget halves to 8.33ms.

**Design rule**: If your design requires more than 3-4 simultaneous animations on different elements, test on the lowest-tier target device before committing. Stagger start times by 30-50ms to distribute the work across frames rather than front-loading it all into one frame.
