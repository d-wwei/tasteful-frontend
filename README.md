# Tasteful Frontend

[中文版](README_CN.md) | English Version

An AI-native UI design skill for building modern, production-grade, and visually striking interfaces across **web and mobile** platforms. Supports React, Next.js, Vue, Svelte, Tailwind CSS, SwiftUI, React Native, and Flutter.

This skill fights generic "AI slop" — predictable layouts, overused fonts, poor accessibility — with a **Three-Tier Architecture** that enforces engineering rigor while raising the visual ceiling.

## What's New in v1.0

This version is a synthesis of [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend) (aesthetic philosophy) and [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (comprehensive UX rule system), powered by [Remix](https://github.com/d-wwei/remix).

- **10-category rule priority system** (CRITICAL → LOW) for systematic design decisions
- **Mobile platform support** — iOS (SwiftUI/HIG), Android (Material Design), React Native, Flutter
- **Expanded constraint files** — accessibility rules from 34 → 74 lines, component patterns from 36 → 78 lines
- **Pre-delivery checklist** — visual quality, interaction, accessibility, layout, code quality
- **Deeper coverage** — touch targets, gesture safety, skeleton loading, safe areas, spring physics, semantic color tokens, screen reader support

## Features

### Three-Tier Architecture

- **Tier 1: Baseline Constraints** — Accessibility, touch interaction, and performance. Non-negotiable. Enforces ARIA labels, 44pt touch targets, focus trapping, motion performance, lazy loading, and screen reader compatibility.
- **Tier 2: Component & Layout Patterns** — Real-world best practices for forms, navigation, data display, overlays, and responsive layout. 8px grid, single-column forms, verb-first buttons, empty state CTAs, adaptive navigation.
- **Tier 3: Aesthetic Directives** — The soul of this skill. Bans overused fonts (Inter, Roboto, Arial), enforces bold color philosophy (one dominant + one accent), demands intentional spatial composition, and applies modern material effects (glassmorphism, grain, atmospheric backgrounds).

### Design Thinking First

Forces the AI to define a bold aesthetic direction, platform context, and a "wow factor" hook before writing any code.

### Rule Priority System

10 rule categories ranked by impact (CRITICAL → LOW), adapted from production UX guidelines referencing Apple HIG, Material Design, and WCAG standards.

### Anti-AI-Slop Anti-Patterns

Explicit blacklist of generic AI aesthetics, engineering failures, UX mistakes, and mobile-specific pitfalls.

## Directory Structure

```text
frontend-design/
├── SKILL.md                  # Main skill entry point (240 lines)
├── constraints/
│   ├── accessibility.md      # Accessibility, touch, performance, screen reader rules
│   └── components.md         # Component patterns, navigation, forms, charts, icons
├── README.md                 # English documentation
└── README_CN.md              # Chinese documentation
```

## How to Use

### Claude Code

The skill is auto-detected when placed in `~/.claude/skills/`. Invoke with:

```
/tasteful-frontend
```

Or reference it naturally:

> "Build a SaaS dashboard settings page with a dark mode aesthetic."

### Other AI Agents (Cursor, Windsurf, etc.)

Point your agent to read `SKILL.md` as a system prompt or context file when generating frontend code.

### Example Prompts

- "Build a landing page for a fintech product. I want a luxury, editorial feel."
- "Create a mobile app onboarding flow for iOS. SwiftUI, minimal and warm."
- "Redesign this dashboard table with proper empty states and loading skeletons."
- "Review this React component for accessibility and touch target compliance."

## Principles

1. **Accessibility is non-negotiable** — every rule exists because real users need it.
2. **Intentional aesthetics over generic templates** — bold choices, not safe defaults.
3. **Platform-aware** — respect iOS HIG, Material Design, and web conventions.
4. **Prescriptive, not encyclopedic** — actionable rules, not a reference manual.

## Credits

Synthesized from:
- [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend) — aesthetic philosophy and three-tier architecture
- [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) — comprehensive UI/UX rule system and mobile platform rules
- [Anthropic's frontend design guidelines](https://docs.anthropic.com) — anti-AI-slop design thinking

Built with [Remix](https://github.com/d-wwei/remix) — universal artifact reconstruction tool.

---

MIT License
