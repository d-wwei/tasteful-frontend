# Motion Deep Knowledge

Design-layer guidance for motion decisions: timing, easing, perceived performance, choreography patterns, and reduced-motion strategy. This file covers the "why" and "when" of motion design. For performance constraints (rendering steps, layer promotion, FLIP technique), see `motion-performance.md`. For code-level implementation, see `code-rules.md`.

---

## Duration: The 100/300/500 Rule

Duration is more important than easing. Wrong duration with perfect easing still feels broken. Right duration with generic easing still feels acceptable.

### Duration Tiers

| Duration | Use Case | Examples |
|----------|----------|---------|
| **100-150ms** | Instant feedback | Button press, toggle state, color change, checkbox, hover response |
| **200-300ms** | State transitions | Menu open/close, tooltip appear, dropdown reveal, tab switch |
| **300-500ms** | Layout changes | Accordion expand, modal entrance, drawer slide, page section reveal |
| **500-800ms** | Entrance choreography | Page load sequences, hero reveals, first-paint animations |

### Exit Duration Rule

Exit animations run at ~75% of entrance duration. Entering content earns user attention through gradual reveal; exiting content should clear quickly to not obstruct the next action.

| Entrance | Exit |
|----------|------|
| 300ms | 225ms |
| 500ms | 375ms |
| 200ms | 150ms |

**Design rationale**: The asymmetry exists because humans psychologically assign different values to arriving vs. departing content. Arrival is interesting (what is this?); departure is functional (clear the way). Slow exits feel like the interface is reluctant to respond.

### Duration Scaling by Distance

Longer travel distance requires slightly longer duration. An element moving 20px needs less time than one moving 400px. But the relationship is not linear -- doubling distance does not double duration.

| Travel Distance | Duration Adjustment |
|----------------|-------------------|
| <50px | Base tier (100-200ms) |
| 50-200px | Base tier (200-300ms) |
| 200-500px | Extended tier (300-400ms) |
| >500px (full-screen) | Maximum tier (400-500ms) |

Never exceed 500ms for any single UI animation. Beyond that, the interface feels sluggish regardless of how smooth the motion is.

---

## Easing: Exponential Curves

### Why Not `ease` or `linear`

`ease` is a compromise that fits no specific scenario perfectly. `linear` feels robotic and mechanical -- nothing in the physical world moves at constant velocity.

**Use exponential easing curves** because they mimic real-world physics: objects decelerate due to friction, accelerate due to gravity. These curves have fast initial movement that settles into a smooth stop (ease-out) or slow startup that builds momentum (ease-in).

### Easing Selection by Motion Type

| Motion Type | Easing | Why |
|-------------|--------|-----|
| **Element entering** | Ease-out (decelerate) | Object arrives with momentum and settles into place |
| **Element exiting** | Ease-in (accelerate) | Object picks up speed as it leaves, like falling away |
| **State toggle** (there and back) | Ease-in-out (symmetric) | Equal momentum on both sides of the transition |
| **Micro-interaction** (hover, press) | Ease-out-quart or ease-out-expo | Snap-fast start, silky-smooth settle |

### Exponential Curve Hierarchy

Ordered from subtle to dramatic:

| Curve | Feel | When to Use |
|-------|------|-------------|
| **Quart out** | Smooth, refined | Default for most UI transitions. The safe, tasteful choice. |
| **Quint out** | Slightly snappier | When you want motion to feel a bit more decisive |
| **Expo out** | Confident, snappy | Navigation transitions, significant state changes, hero animations |

### Avoid Bounce and Elastic

Bounce and elastic curves were fashionable in 2012-2016. They now read as dated and amateurish. Real objects do not bounce when they stop -- they decelerate smoothly due to friction. Overshoot effects draw attention to the animation mechanism itself rather than the content, violating the principle that motion should be felt but not noticed.

**Exception**: Playful, toy-like interfaces targeting children or casual gaming contexts. Even then, use with extreme restraint.

---

## Perceived Performance

### The 80ms Threshold

The human brain buffers sensory input for approximately 80ms to synchronize perception across senses. Anything that happens within 80ms of a user action feels instantaneous and simultaneous.

**Design implication**: Micro-interactions (button press feedback, toggle state change, hover response) should complete within 80ms of the triggering input. If the response takes 100-200ms, the user perceives a gap between their action and the result.

### The Speed-Value Paradox

Faster is not always better. For operations that users expect to take effort (complex searches, AI generation, financial calculations), an instant result can feel suspicious -- "Did it actually do anything?"

**Design technique**: For complex operations, add a brief artificial delay (200-500ms) with a meaningful loading state. The user perceives the system as "working hard" on their behalf.

### Active vs. Passive Wait Time

Passive waiting (staring at a spinner) feels 36% longer than the actual elapsed time. Active engagement (watching content progressively appear) feels shorter than actual time.

| Strategy | Mechanism | Perceived Effect |
|----------|-----------|-----------------|
| **Preemptive start** | Begin the transition animation immediately while data loads behind it | User sees motion → perceives work happening → wait feels shorter |
| **Progressive reveal** | Show content as it arrives (skeleton → text → images) | Continuous visual change keeps user engaged → wait feels shorter |
| **Optimistic UI** | Update immediately, sync with server in background | No perceived wait at all for low-stakes actions |
| **Skeleton screens** | Shape placeholders pulse softly while loading | Communicates "content is coming" without the stagnation of a spinner |

### Easing and Perceived Duration

The peak-end rule (from psychology) applies to animation: humans judge an experience by its peak and its ending, not by its average.

- **Ease-in toward completion**: An animation that accelerates toward its end (ease-in) compresses the perceived final moments. The user experiences the "fast ending" as the defining memory. Use for loading bars, progress indicators -- anything where "finishing fast" matters.
- **Ease-out for entrances**: An animation that decelerates (ease-out) creates a satisfying settle. The ending is smooth and controlled, leaving a positive impression. Use for content appearance, modal entrances -- anything where "arriving gracefully" matters.

---

## Motion Choreography Patterns

### Stagger (Sequential Reveal)

Items in a group appear one after another with a fixed delay between each.

**When to use**: List items, card grids, menu items, any group of similar elements appearing together.

**Design rules**:
- Per-item delay: 30-80ms (shorter for more items, longer for fewer)
- Total stagger duration cap: 500ms maximum. For 10 items at 50ms per item = 500ms total.
- If items exceed the cap, reduce per-item delay or only stagger the first 5-8 items; the rest appear simultaneously.
- Direction: stagger should follow the reading direction (top-to-bottom for vertical lists, left-to-right for horizontal grids).

### Cascade (Hierarchical Reveal)

Parent elements appear first, children follow. Unlike stagger (which is sequential among peers), cascade follows the containment hierarchy.

**When to use**: Page sections containing subsections, card with internal elements, dashboard with widgets.

**Design rules**:
- Container appears first (background, border)
- Primary content appears next (headline, key image) -- 50-100ms after container
- Secondary content appears last (body text, metadata, actions) -- 50-100ms after primary
- Total cascade for a single component: ≤300ms

### Morph (Shape Transformation)

An element transforms from one shape/size/position into another, maintaining visual continuity.

**When to use**: Navigation transitions where an element on Page A becomes an element on Page B (thumbnail to full-screen image, list item to detail view, FAB to form).

**Design rules**:
- Duration: 300-500ms (longer than standard transitions because the eye needs to track the transformation)
- Easing: Ease-in-out or expo-out (the transition needs momentum at start and smooth landing)
- Maintain at least one constant property during the morph (color, border-radius, or aspect ratio) so the eye can track the identity of the element

### Dissolve (Cross-Fade)

Content fades out while new content fades in simultaneously, optionally overlapping.

**When to use**: Tab content switching, image carousels, content that changes without spatial movement.

**Design rules**:
- Duration: 150-250ms (fast enough to feel responsive, slow enough to avoid flicker)
- The outgoing element's opacity should reach ~0.5 before the incoming element begins appearing at 0.5 -- slight overlap prevents a "black flash" where nothing is visible
- Easing: Linear or ease-in-out (cross-fades have no spatial dimension, so easing matters less)

---

## Reduced Motion Strategy

### Not Optional

Vestibular disorders affect approximately 35% of adults over 40. Motion sensitivity triggers real physical symptoms: dizziness, nausea, disorientation. Respecting `prefers-reduced-motion` is a medical accessibility requirement, not a nice-to-have.

### What to Preserve vs. What to Remove

| Category | Reduced Motion Behavior |
|----------|------------------------|
| **Spatial movement** (slides, transforms, parallax) | Replace with opacity fade or remove entirely |
| **Expansion** (accordion, dropdown) | Reduce to instant state change or fast opacity fade (100ms) |
| **Loading indicators** (spinners, progress bars) | Keep functional but slow down rotation; replace pulsing with static state |
| **Focus indicators** | Always preserve -- these are essential for accessibility |
| **Scroll-linked motion** | Disable entirely -- this is the most common trigger for vestibular symptoms |
| **Auto-playing animation** | Stop; offer user-initiated play |

### The Two-Tier Approach

**Tier 1** (remove): Anything that involves spatial displacement, parallax, scale changes, or rotation.
**Tier 2** (keep but modify): Opacity changes (cross-fades are generally safe), color transitions, and essential functional feedback (loading states).

**Design rule**: In reduced-motion mode, the interface should still communicate state changes. The information must still be conveyed -- just without spatial displacement.
