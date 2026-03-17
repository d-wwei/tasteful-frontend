# Tasteful Frontend Skill

[中文版](README_CN.md) | English Version

An AI-native frontend UI design skill built to generate modern, production-ready, and highly aesthetic web interfaces (React, Tailwind CSS, HTML/CSS). 

This skill moves beyond the generic "AI baseline" (often characterized by predictable layouts, overused fonts, and poor accessibility) by employing a **Three-Tier Architecture** that enforces both engineering rigor and striking visual design.

## Features

- **Tier 1: Baseline Constraints**: Accessibility by default. Enforces ARIA labels, semantic HTML, keyboard focus trapping, and strict motion performance limits.
- **Tier 2: Component Patterns**: Employs real-world SaaS best practices for forms, data display, overlays, and navigation (e.g., 8px grids, single-column forms, verb-first buttons).
- **Tier 3: Aesthetic Directives**: Elevates visual quality by banning overused generic fonts, enforcing deliberate spatial composition, restricting rainbow colors in favor of strong accents, and applying modern material effects (like Glassmorphism).
- **Design Thinking**: Forces the AI to define a bold aesthetic direction and intended "wow factor" before outputting any code.

## Directory Structure

```text
frontend-design/
├── SKILL.md                  # Main prompt/skill entry point
├── constraints/
│   ├── accessibility.md      # Baseline UI constraints (Accessibility & Performance)
│   └── components.md         # Validated design system component patterns
├── README.md                 # Documentation in English
└── README_CN.md              # Documentation in Chinese
```

## How to Use

To use this skill, ensure your AI agent (Cursor, Claude, or other local agents) is configured to read the `SKILL.md` file when prompted to generate frontend code. 

Example prompt to an agent equipped with this skill:
> "Using the Tasteful Frontend skill, build a beautiful SaaS dashboard settings page. I want a sleek dark mode vibe."

## Principles

1. **Accessibility is non-negotiable**.
2. **Intentional aesthetics over generic templates**.
3. **Usability through established patterns**.

---
*Created as the ultimate synthesis of top design skills.*
