# Component Patterns & Best Practices

To avoid creating confusing or generic AI-generated interfaces, strictly follow these component-level design patterns.

## 1. Spatial Structure & Layout
- **8px Grid**: Space elements using multiples of 8 (e.g., `p-4` = 16px, `gap-6` = 24px, `m-8` = 32px in Tailwind).
- **White Space**: White space is a feature, not emptiness. Do not crowd elements. Give hero sections and discrete cards room to breathe. Use negative space (generous margins) to group related items logically.

## 2. Forms & Inputs
- **Column Layout**: Prefer single-column layouts for forms. They are significantly faster for users to scan and complete. Stack labels above inputs by default.
- **Button Labels**: Use verb-first phrasing. Instead of "Submit", use "Save Settings", "Send Message", or "Create Account".
- **Primary vs. Secondary CTAs**: There should only be ONE primary button per section or form. Mute secondary actions (e.g., use a ghost or outline button for "Cancel" or "Go Back").
- **Validation**: Show validation errors exactly where the error occurred, immediately below the input, styled clearly in red or with an icon.

## 3. Data Display
- **Cards**: Follow a strict visual hierarchy: `Media (Image/Icon) -> Title -> Meta/Subtitle -> Action`. Never use both a heavy shadow AND a heavy border—choose one for a cleaner look.
- **Tables**: Right-align numerical data. Ensure table headers are visually distinct (e.g., slightly muted text, uppercase tracking, or a light background fill) and sticky if the table is long. 
- **Empty States**: Do not just show "No items found". Design a proper empty state featuring: a subtle illustration or icon, a helpful headline, and a clear Primary CTA to create the first item.

## 4. Overlays (Modals & Drawers)
- **Visual Stacking**: Use a dark or blurred backdrop mask for overlays (`bg-black/50 backdrop-blur-sm`).
- **Modals vs. Drawers**: Use Modals for focused tasks requiring immediate attention or confirmation (e.g., deleting a file). Use Drawers (side panels) for complex forms or detail views to maintain context with the underlying page.

## 5. Navigation
- **Top Nav / Header**: Keep it clean. Maximum 5-7 top-level links. Use a clear active indicator. Only hide behind a hamburger menu on tablet/mobile screens (`md:hidden`), NEVER on desktop.
- **Tabs**: Best limited to 2-7 items. Use horizontal scroll if they overflow on mobile, or stack them into an accordion if they contain dense content.

*Adhering to these structural rules ensures the user interface feels solid, familiar, and highly professional.*
