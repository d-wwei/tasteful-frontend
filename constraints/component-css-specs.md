# Component CSS Specs: Production-Ready Declarations

This document provides copy-paste CSS for the 5 pilot components across 4 brands. It supplements `component-visual-specs.md` (token-level) with exact, production-ready values.

---

## Brand Fingerprint: Cross-Reference of Divergent Properties

These are the CSS properties that most strongly encode brand identity. When switching brands, these are the lines that change.

| Property | Claude | Stripe | Linear | Vercel |
|----------|--------|--------|--------|--------|
| **font-family** | `"Anthropic Sans", Georgia, serif` (headings: `"Anthropic Serif"`) | `"sohne-var", "SF Pro Display", system-ui, sans-serif` | `"Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif` | `"Geist", Arial, sans-serif` |
| **font-feature-settings** | none | `"ss01"` | `"cv01", "ss03"` | `"liga"` |
| **border-radius (button)** | `8px` | `4px` | `6px` | `6px` |
| **border-radius (card)** | `8px` | `6px` | `8px` | `8px` |
| **border-radius (input)** | `12px` | `4px` | `6px` | `6px` |
| **border technique** | ring shadow `0 0 0 1px` | CSS `border` | CSS `border` (semi-transparent) | ring shadow `0 0 0 1px` |
| **shadow tint** | warm neutral `rgba(0,0,0,0.05)` | blue `rgba(50,50,93,0.25)` | luminance stepping (no drop shadow) | neutral layered stack |
| **primary accent** | `#c96442` (terracotta) | `#533afd` (purple) | `#5e6ad2` (indigo) | `#171717` (near-black) |
| **heading weight** | `500` (serif) | `300` (light) | `510-590` | `600` |
| **body text color** | `#5e5d59` (warm olive) | `#64748d` (cool slate) | `#8a8f98` (cool gray) | `#4d4d4d` (neutral gray) |
| **heading text color** | `#141413` (warm black) | `#061b31` (navy) | `#f7f8f8` (near-white) | `#171717` (near-black) |
| **page background** | `#f5f4ed` (parchment) | `#ffffff` (white) | `#08090a` (near-black) | `#ffffff` (white) |
| **focus ring color** | `#3898ec` (blue, a11y only) | `#533afd` (brand purple) | multi-layer shadow | `hsla(212,100%,48%,1)` (blue) |
| **hover model** | darken 8% | darken shade | lighten / opacity increase | invert (dark/light swap) |
| **letter-spacing (display)** | `normal` | `-0.96px` (at 48px) | `-1.056px` (at 48px) | `-2.4px` (at 48px) |
| **dark mode native** | No (light-first, dark sections) | No (light-first) | Yes (dark-first) | No (light-first, has dark mode) |

---

## 1. Button

### Claude -- Primary Button

```css
/* Claude -- Primary Button */
.btn-primary {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 1.0;
  letter-spacing: normal;
  color: #faf9f5;
  background: #c96442;
  padding: 9.6px 16.8px;
  border: none;
  border-radius: 8px;
  box-shadow: #c96442 0px 0px 0px 0px, #c96442 0px 0px 0px 1px;
  cursor: pointer;
  transition: background 150ms ease, box-shadow 150ms ease;
}
.btn-primary:hover {
  background: #b85a3c;
  box-shadow: #b85a3c 0px 0px 0px 0px, #b85a3c 0px 0px 0px 1px;
}
.btn-primary:focus-visible {
  outline: 2px solid #3898ec;
  outline-offset: 2px;
}
.btn-primary:active {
  background: #a8512f;
  box-shadow: inset 0px 0px 0px 1px rgba(0, 0, 0, 0.15);
}
.btn-primary:disabled {
  background: #c96442;
  opacity: 0.4;
  cursor: not-allowed;
  box-shadow: none;
}

/* Claude -- Primary Button (Dark Mode) */
.dark .btn-primary {
  background: #c96442;
  color: #faf9f5;
  box-shadow: #c96442 0px 0px 0px 0px, #c96442 0px 0px 0px 1px;
}
.dark .btn-primary:hover {
  background: #d97757;
}
```

### Claude -- Secondary Button

```css
/* Claude -- Secondary Button (Warm Sand) */
.btn-secondary {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 1.0;
  letter-spacing: normal;
  color: #4d4c48;
  background: #e8e6dc;
  padding: 9.6px 16.8px;
  border: none;
  border-radius: 8px;
  box-shadow: #e8e6dc 0px 0px 0px 0px, #d1cfc5 0px 0px 0px 1px;
  cursor: pointer;
  transition: background 150ms ease, box-shadow 150ms ease;
}
.btn-secondary:hover {
  background: #dddbd0;
  box-shadow: #dddbd0 0px 0px 0px 0px, #c2c0b6 0px 0px 0px 1px;
}
.btn-secondary:focus-visible {
  outline: 2px solid #3898ec;
  outline-offset: 2px;
}
.btn-secondary:active {
  background: #d4d2c7;
  box-shadow: inset 0px 0px 0px 1px rgba(0, 0, 0, 0.1);
}
.btn-secondary:disabled {
  background: #e8e6dc;
  color: #87867f;
  opacity: 0.5;
  cursor: not-allowed;
  box-shadow: none;
}

/* Claude -- Secondary Button (Dark Mode: inverted to dark charcoal) */
.dark .btn-secondary {
  background: #30302e;
  color: #faf9f5;
  box-shadow: #30302e 0px 0px 0px 0px, #30302e 0px 0px 0px 1px;
}
.dark .btn-secondary:hover {
  background: #3d3d3a;
}
```

### Claude -- Destructive Button

```css
/* Claude -- Destructive Button */
.btn-destructive {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 1.0;
  letter-spacing: normal;
  color: #ffffff;
  background: #b53333;
  padding: 9.6px 16.8px;
  border: none;
  border-radius: 8px;
  box-shadow: #b53333 0px 0px 0px 0px, #b53333 0px 0px 0px 1px;
  cursor: pointer;
  transition: background 150ms ease;
}
.btn-destructive:hover {
  background: #9e2c2c;
}
.btn-destructive:focus-visible {
  outline: 2px solid #3898ec;
  outline-offset: 2px;
}
.btn-destructive:active {
  background: #8a2525;
  box-shadow: inset 0px 0px 0px 1px rgba(0, 0, 0, 0.15);
}
.btn-destructive:disabled {
  background: #b53333;
  opacity: 0.4;
  cursor: not-allowed;
  box-shadow: none;
}
```

### Stripe -- Primary Button

```css
/* Stripe -- Primary Button */
.btn-primary {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "ss01";
  color: #ffffff;
  background: #533afd;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  box-shadow: none;
  cursor: pointer;
  transition: background 150ms ease;
}
.btn-primary:hover {
  background: #4434d4;
}
.btn-primary:focus-visible {
  outline: 2px solid #533afd;
  outline-offset: 2px;
}
.btn-primary:active {
  background: #2e2b8c;
}
.btn-primary:disabled {
  background: #533afd;
  opacity: 0.4;
  cursor: not-allowed;
}

/* Stripe -- Primary Button (Dark Section) */
.dark .btn-primary {
  background: #533afd;
  color: #ffffff;
}
.dark .btn-primary:hover {
  background: #665efd;
}
```

### Stripe -- Secondary/Ghost Button

```css
/* Stripe -- Secondary / Ghost Button */
.btn-secondary {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "ss01";
  color: #533afd;
  background: transparent;
  padding: 8px 16px;
  border: 1px solid #b9b9f9;
  border-radius: 4px;
  cursor: pointer;
  transition: background 150ms ease, border-color 150ms ease;
}
.btn-secondary:hover {
  background: rgba(83, 58, 253, 0.05);
  border-color: #533afd;
}
.btn-secondary:focus-visible {
  outline: 2px solid #533afd;
  outline-offset: 2px;
}
.btn-secondary:active {
  background: rgba(83, 58, 253, 0.1);
}
.btn-secondary:disabled {
  color: rgba(16, 16, 16, 0.3);
  border-color: rgb(212, 222, 233);
  background: transparent;
  cursor: not-allowed;
}

/* Stripe -- Secondary Button (Dark Section) */
.dark .btn-secondary {
  color: #ffffff;
  border-color: rgba(255, 255, 255, 0.2);
}
.dark .btn-secondary:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.4);
}
```

### Stripe -- Destructive Button

```css
/* Stripe -- Destructive Button */
.btn-destructive {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "ss01";
  color: #ffffff;
  background: #ea2261;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background 150ms ease;
}
.btn-destructive:hover {
  background: #d41d57;
}
.btn-destructive:focus-visible {
  outline: 2px solid #533afd;
  outline-offset: 2px;
}
.btn-destructive:active {
  background: #b8184a;
}
.btn-destructive:disabled {
  background: #ea2261;
  opacity: 0.4;
  cursor: not-allowed;
}
```

### Linear -- Primary Button

```css
/* Linear -- Primary Button */
.btn-primary {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-size: 14px;
  font-weight: 510;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "cv01", "ss03";
  color: #ffffff;
  background: #5e6ad2;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  box-shadow: none;
  cursor: pointer;
  transition: background 150ms ease;
}
.btn-primary:hover {
  background: #828fff;
}
.btn-primary:focus-visible {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px, 0px 0px 0px 2px #5e6ad2;
  outline: none;
}
.btn-primary:active {
  background: #4e5abc;
}
.btn-primary:disabled {
  background: #5e6ad2;
  opacity: 0.3;
  cursor: not-allowed;
}
```

### Linear -- Secondary/Ghost Button

```css
/* Linear -- Secondary / Ghost Button */
.btn-secondary {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-size: 14px;
  font-weight: 510;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "cv01", "ss03";
  color: #e2e4e7;
  background: rgba(255, 255, 255, 0.02);
  padding: 8px 16px;
  border: 1px solid rgb(36, 40, 44);
  border-radius: 6px;
  cursor: pointer;
  transition: background 150ms ease, border-color 150ms ease;
}
.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgb(52, 56, 60);
}
.btn-secondary:focus-visible {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px, 0px 0px 0px 2px #5e6ad2;
  outline: none;
}
.btn-secondary:active {
  background: rgba(255, 255, 255, 0.08);
}
.btn-secondary:disabled {
  color: #62666d;
  background: rgba(255, 255, 255, 0.01);
  border-color: rgb(30, 33, 36);
  cursor: not-allowed;
  opacity: 0.5;
}
```

### Linear -- Destructive Button

```css
/* Linear -- Destructive Button */
.btn-destructive {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-size: 14px;
  font-weight: 510;
  line-height: 1.0;
  letter-spacing: normal;
  font-feature-settings: "cv01", "ss03";
  color: #ffffff;
  background: #d93036;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background 150ms ease;
}
.btn-destructive:hover {
  background: #e54b50;
}
.btn-destructive:focus-visible {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px, 0px 0px 0px 2px #d93036;
  outline: none;
}
.btn-destructive:active {
  background: #c22a2f;
}
.btn-destructive:disabled {
  background: #d93036;
  opacity: 0.3;
  cursor: not-allowed;
}
```

### Vercel -- Primary Button

```css
/* Vercel -- Primary Button (Dark) */
.btn-primary {
  font-family: "Geist", Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  font-feature-settings: "liga";
  color: #ffffff;
  background: #171717;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  box-shadow: none;
  cursor: pointer;
  transition: background 200ms ease, color 200ms ease;
}
.btn-primary:hover {
  background: #ffffff;
  color: #171717;
  box-shadow: rgb(235, 235, 235) 0px 0px 0px 1px;
}
.btn-primary:focus-visible {
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: 2px;
}
.btn-primary:active {
  background: #333333;
  color: #ffffff;
}
.btn-primary:disabled {
  background: #171717;
  color: #ffffff;
  opacity: 0.4;
  cursor: not-allowed;
}

/* Vercel -- Primary Button (Dark Mode) */
.dark .btn-primary {
  background: #ffffff;
  color: #171717;
}
.dark .btn-primary:hover {
  background: #171717;
  color: #ffffff;
  box-shadow: rgb(51, 51, 51) 0px 0px 0px 1px;
}
```

### Vercel -- Secondary/Ghost Button

```css
/* Vercel -- Secondary / Ghost Button (White with shadow-border) */
.btn-secondary {
  font-family: "Geist", Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  font-feature-settings: "liga";
  color: #171717;
  background: #ffffff;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  box-shadow: rgb(235, 235, 235) 0px 0px 0px 1px;
  cursor: pointer;
  transition: background 200ms ease, color 200ms ease, box-shadow 200ms ease;
}
.btn-secondary:hover {
  background: #171717;
  color: #ffffff;
  box-shadow: #171717 0px 0px 0px 1px;
}
.btn-secondary:focus-visible {
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: 2px;
}
.btn-secondary:active {
  background: #333333;
  color: #ffffff;
}
.btn-secondary:disabled {
  color: #808080;
  background: #fafafa;
  box-shadow: rgb(235, 235, 235) 0px 0px 0px 1px;
  cursor: not-allowed;
  opacity: 0.5;
}

/* Vercel -- Secondary Button (Dark Mode) */
.dark .btn-secondary {
  background: transparent;
  color: #ffffff;
  box-shadow: rgb(51, 51, 51) 0px 0px 0px 1px;
}
.dark .btn-secondary:hover {
  background: #ffffff;
  color: #171717;
  box-shadow: rgb(235, 235, 235) 0px 0px 0px 1px;
}
```

### Vercel -- Destructive Button

```css
/* Vercel -- Destructive Button */
.btn-destructive {
  font-family: "Geist", Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  font-feature-settings: "liga";
  color: #ffffff;
  background: #ff5b4f;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  box-shadow: none;
  cursor: pointer;
  transition: background 200ms ease;
}
.btn-destructive:hover {
  background: #e84e43;
}
.btn-destructive:focus-visible {
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: 2px;
}
.btn-destructive:active {
  background: #d4443a;
}
.btn-destructive:disabled {
  background: #ff5b4f;
  opacity: 0.4;
  cursor: not-allowed;
}
```

---

## 2. Card

### Claude -- Card

```css
/* Claude -- Standard Card */
.card {
  font-family: "Anthropic Sans", Arial, sans-serif;
  background: #faf9f5;
  border: 1px solid #f0eee6;
  border-radius: 8px;
  padding: 24px;
  box-shadow: none;
  transition: box-shadow 150ms ease;
}
.card:hover {
  box-shadow: 0px 0px 0px 1px #d1cfc5, rgba(0, 0, 0, 0.05) 0px 4px 24px;
}
.card-title {
  font-family: "Anthropic Serif", Georgia, serif;
  font-size: 25px;
  font-weight: 500;
  line-height: 1.20;
  letter-spacing: normal;
  color: #141413;
  margin: 0 0 8px 0;
}
.card-body {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.60;
  letter-spacing: normal;
  color: #5e5d59;
  margin: 0 0 16px 0;
}
.card-action {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: #c96442;
  text-decoration: none;
  cursor: pointer;
}
.card-action:hover {
  color: #b85a3c;
}

/* Claude -- Card (Dark Mode) */
.dark .card {
  background: #30302e;
  border-color: #30302e;
}
.dark .card:hover {
  box-shadow: 0px 0px 0px 1px #4d4c48, rgba(0, 0, 0, 0.2) 0px 4px 24px;
}
.dark .card-title {
  color: #faf9f5;
}
.dark .card-body {
  color: #b0aea5;
}
.dark .card-action {
  color: #d97757;
}
```

### Stripe -- Card

```css
/* Stripe -- Standard Card */
.card {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  background: #ffffff;
  border: 1px solid #e5edf5;
  border-radius: 6px;
  padding: 24px;
  box-shadow: rgba(23, 23, 23, 0.08) 0px 15px 35px 0px;
  transition: box-shadow 150ms ease;
}
.card:hover {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 45px -30px, rgba(0, 0, 0, 0.1) 0px 18px 36px -18px;
}
.card-title {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 22px;
  font-weight: 300;
  line-height: 1.10;
  letter-spacing: -0.22px;
  color: #061b31;
  margin: 0 0 8px 0;
}
.card-body {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 16px;
  font-weight: 300;
  line-height: 1.40;
  letter-spacing: normal;
  color: #64748d;
  margin: 0 0 16px 0;
}
.card-action {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 14px;
  font-weight: 400;
  color: #533afd;
  text-decoration: none;
  cursor: pointer;
}
.card-action:hover {
  color: #4434d4;
}

/* Stripe -- Card (Dark Section: brand dark background) */
.dark .card {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.1);
  box-shadow: none;
}
.dark .card:hover {
  border-color: rgba(255, 255, 255, 0.2);
  box-shadow: rgba(3, 3, 39, 0.25) 0px 14px 21px -14px;
}
.dark .card-title {
  color: #ffffff;
}
.dark .card-body {
  color: rgba(255, 255, 255, 0.7);
}
.dark .card-action {
  color: #b9b9f9;
}
```

### Linear -- Card

```css
/* Linear -- Standard Card (dark-mode-native) */
.card {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 8px;
  padding: 20px;
  box-shadow: none;
  transition: background 150ms ease, border-color 150ms ease;
}
.card:hover {
  background: rgba(255, 255, 255, 0.04);
  border-color: rgba(255, 255, 255, 0.12);
}
.card-title {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 20px;
  font-weight: 590;
  line-height: 1.33;
  letter-spacing: -0.24px;
  color: #f7f8f8;
  margin: 0 0 8px 0;
}
.card-body {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 15px;
  font-weight: 400;
  line-height: 1.60;
  letter-spacing: -0.165px;
  color: #8a8f98;
  margin: 0 0 16px 0;
}
.card-action {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 14px;
  font-weight: 510;
  color: #7170ff;
  text-decoration: none;
  cursor: pointer;
}
.card-action:hover {
  color: #828fff;
}

/* Linear -- Card (Light Mode, if used) */
.light .card {
  background: #ffffff;
  border: 1px solid #e6e6e6;
}
.light .card-title {
  color: #0f1011;
}
.light .card-body {
  color: #62666d;
}
```

### Vercel -- Card

```css
/* Vercel -- Standard Card */
.card {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  background: #ffffff;
  border: none;
  border-radius: 8px;
  padding: 24px;
  box-shadow:
    rgba(0, 0, 0, 0.08) 0px 0px 0px 1px,
    rgba(0, 0, 0, 0.04) 0px 2px 2px,
    #fafafa 0px 0px 0px 1px;
  transition: box-shadow 200ms ease;
}
.card:hover {
  box-shadow:
    rgba(0, 0, 0, 0.08) 0px 0px 0px 1px,
    rgba(0, 0, 0, 0.04) 0px 2px 2px,
    rgba(0, 0, 0, 0.04) 0px 8px 8px -8px,
    #fafafa 0px 0px 0px 1px;
}
.card-title {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 24px;
  font-weight: 600;
  line-height: 1.33;
  letter-spacing: -0.96px;
  color: #171717;
  margin: 0 0 8px 0;
}
.card-body {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 16px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: normal;
  color: #4d4d4d;
  margin: 0 0 16px 0;
}
.card-action {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 500;
  color: #0072f5;
  text-decoration: none;
  cursor: pointer;
}
.card-action:hover {
  text-decoration: underline;
}

/* Vercel -- Card (Dark Mode) */
.dark .card {
  background: #171717;
  box-shadow:
    rgba(255, 255, 255, 0.08) 0px 0px 0px 1px,
    rgba(0, 0, 0, 0.2) 0px 2px 2px,
    #1a1a1a 0px 0px 0px 1px;
}
.dark .card:hover {
  box-shadow:
    rgba(255, 255, 255, 0.12) 0px 0px 0px 1px,
    rgba(0, 0, 0, 0.3) 0px 4px 8px -4px,
    #1a1a1a 0px 0px 0px 1px;
}
.dark .card-title {
  color: #ffffff;
}
.dark .card-body {
  color: #808080;
}
.dark .card-action {
  color: #0072f5;
}
```

---

## 3. Form Input

### Claude -- Form Input

```css
/* Claude -- Form Input: Label */
.input-label {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  color: #141413;
  display: block;
  margin-bottom: 4px;
}

/* Claude -- Form Input: Text Input */
.input-text {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.25;
  letter-spacing: normal;
  color: #141413;
  background: #ffffff;
  padding: 1.6px 12px;
  border: 1px solid #d1cfc5;
  border-radius: 12px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  transition: border-color 150ms ease;
}
.input-text::placeholder {
  color: #87867f;
}
.input-text:hover {
  border-color: #c2c0b6;
}
.input-text:focus {
  border-color: #3898ec;
  box-shadow: 0px 0px 0px 1px #3898ec;
}
.input-text:disabled {
  background: #f5f4ed;
  color: #87867f;
  border-color: #e8e6dc;
  cursor: not-allowed;
  opacity: 0.6;
}

/* Claude -- Form Input: Error State */
.input-text.error {
  border-color: #b53333;
  box-shadow: 0px 0px 0px 1px #b53333;
}
.input-error-message {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.43;
  color: #b53333;
  margin-top: 4px;
}

/* Claude -- Form Input (Dark Mode) */
.dark .input-label {
  color: #faf9f5;
}
.dark .input-text {
  background: #30302e;
  color: #faf9f5;
  border-color: #4d4c48;
}
.dark .input-text::placeholder {
  color: #87867f;
}
.dark .input-text:hover {
  border-color: #5e5d59;
}
.dark .input-text:focus {
  border-color: #3898ec;
  box-shadow: 0px 0px 0px 1px #3898ec;
}
```

### Stripe -- Form Input

```css
/* Stripe -- Form Input: Label */
.input-label {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.43;
  letter-spacing: normal;
  color: #273951;
  display: block;
  margin-bottom: 4px;
}

/* Stripe -- Form Input: Text Input */
.input-text {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 16px;
  font-weight: 300;
  line-height: 1.40;
  letter-spacing: normal;
  color: #061b31;
  background: #ffffff;
  padding: 8px 12px;
  border: 1px solid #e5edf5;
  border-radius: 4px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  transition: border-color 150ms ease, box-shadow 150ms ease;
}
.input-text::placeholder {
  color: #64748d;
}
.input-text:hover {
  border-color: #d6d9fc;
}
.input-text:focus {
  border-color: #533afd;
  box-shadow: 0px 0px 0px 1px #533afd;
}
.input-text:disabled {
  background: #f6f9fc;
  color: #64748d;
  border-color: #e5edf5;
  cursor: not-allowed;
  opacity: 0.6;
}

/* Stripe -- Form Input: Error State */
.input-text.error {
  border-color: #ea2261;
  box-shadow: 0px 0px 0px 1px #ea2261;
}
.input-error-message {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 13px;
  font-weight: 400;
  line-height: 1.50;
  color: #ea2261;
  margin-top: 4px;
}
```

### Linear -- Form Input

```css
/* Linear -- Form Input: Label */
.input-label {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 14px;
  font-weight: 510;
  line-height: 1.50;
  letter-spacing: -0.182px;
  color: #d0d6e0;
  display: block;
  margin-bottom: 4px;
}

/* Linear -- Form Input: Text Input */
.input-text {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 16px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: normal;
  color: #d0d6e0;
  background: rgba(255, 255, 255, 0.02);
  padding: 12px 14px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 6px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  transition: border-color 150ms ease, box-shadow 150ms ease, background 150ms ease;
}
.input-text::placeholder {
  color: #8a8f98;
}
.input-text:hover {
  border-color: rgba(255, 255, 255, 0.12);
  background: rgba(255, 255, 255, 0.03);
}
.input-text:focus {
  border-color: rgba(255, 255, 255, 0.15);
  box-shadow:
    rgba(0, 0, 0, 0.1) 0px 4px 12px,
    rgba(0, 0, 0, 0.2) 0px 0px 0px 1px;
  background: rgba(255, 255, 255, 0.04);
}
.input-text:disabled {
  background: rgba(255, 255, 255, 0.01);
  color: #62666d;
  border-color: rgba(255, 255, 255, 0.04);
  cursor: not-allowed;
  opacity: 0.5;
}

/* Linear -- Form Input: Error State */
.input-text.error {
  border-color: #d93036;
  box-shadow: 0px 0px 0px 1px rgba(217, 48, 54, 0.3);
}
.input-error-message {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 13px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: -0.13px;
  color: #d93036;
  margin-top: 4px;
}

/* Linear -- Form Input (Light Mode, if used) */
.light .input-label {
  color: #0f1011;
}
.light .input-text {
  background: #ffffff;
  color: #0f1011;
  border: 1px solid #e6e6e6;
}
.light .input-text::placeholder {
  color: #8a8f98;
}
.light .input-text:focus {
  border-color: #5e6ad2;
  box-shadow: 0px 0px 0px 1px #5e6ad2;
}
```

### Vercel -- Form Input

```css
/* Vercel -- Form Input: Label */
.input-label {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  color: #171717;
  display: block;
  margin-bottom: 4px;
}

/* Vercel -- Form Input: Text Input */
.input-text {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.43;
  letter-spacing: normal;
  color: #171717;
  background: #ffffff;
  padding: 8px 12px;
  border: none;
  border-radius: 6px;
  box-shadow: rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  transition: box-shadow 200ms ease;
}
.input-text::placeholder {
  color: #808080;
}
.input-text:hover {
  box-shadow: rgba(0, 0, 0, 0.12) 0px 0px 0px 1px;
}
.input-text:focus {
  box-shadow: none;
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: -1px;
}
.input-text:disabled {
  background: #fafafa;
  color: #808080;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 0px 0px 1px;
  cursor: not-allowed;
  opacity: 0.5;
}

/* Vercel -- Form Input: Error State */
.input-text.error {
  box-shadow: #ff5b4f 0px 0px 0px 1px;
}
.input-error-message {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 13px;
  font-weight: 400;
  line-height: 1.54;
  color: #ff5b4f;
  margin-top: 4px;
}

/* Vercel -- Form Input (Dark Mode) */
.dark .input-label {
  color: #ffffff;
}
.dark .input-text {
  background: #171717;
  color: #ffffff;
  box-shadow: rgba(255, 255, 255, 0.08) 0px 0px 0px 1px;
}
.dark .input-text::placeholder {
  color: #666666;
}
.dark .input-text:hover {
  box-shadow: rgba(255, 255, 255, 0.12) 0px 0px 0px 1px;
}
.dark .input-text:focus {
  box-shadow: none;
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: -1px;
}
```

---

## 4. Navigation

### Claude -- Navigation

```css
/* Claude -- Top Navigation Bar */
.nav {
  font-family: "Anthropic Sans", Arial, sans-serif;
  position: sticky;
  top: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 24px;
  background: #f5f4ed;
  border-bottom: 1px solid #f0eee6;
}
.nav-logo {
  font-family: "Anthropic Serif", Georgia, serif;
  font-size: 20px;
  font-weight: 500;
  color: #141413;
  text-decoration: none;
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 24px;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-link {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 17px;
  font-weight: 400;
  line-height: 1.0;
  letter-spacing: normal;
  color: #5e5d59;
  text-decoration: none;
  transition: color 150ms ease;
}
.nav-link:hover {
  color: #141413;
}
.nav-link:focus-visible {
  outline: 2px solid #3898ec;
  outline-offset: 2px;
  border-radius: 4px;
}
.nav-link.active {
  color: #141413;
  font-weight: 500;
}
.nav-cta {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 1.0;
  color: #faf9f5;
  background: #c96442;
  padding: 9.6px 16.8px;
  border: none;
  border-radius: 8px;
  box-shadow: #c96442 0px 0px 0px 0px, #c96442 0px 0px 0px 1px;
  cursor: pointer;
  text-decoration: none;
  transition: background 150ms ease;
}
.nav-cta:hover {
  background: #b85a3c;
}

/* Claude -- Navigation (Dark Mode) */
.dark .nav {
  background: #141413;
  border-bottom-color: #30302e;
}
.dark .nav-logo {
  color: #faf9f5;
}
.dark .nav-link {
  color: #b0aea5;
}
.dark .nav-link:hover {
  color: #faf9f5;
}
.dark .nav-link.active {
  color: #faf9f5;
}
```

### Stripe -- Navigation

```css
/* Stripe -- Top Navigation Bar */
.nav {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  position: sticky;
  top: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 24px;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: none;
  border-radius: 0;
}
.nav-logo {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 20px;
  font-weight: 300;
  color: #061b31;
  text-decoration: none;
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 24px;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-link {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.0;
  letter-spacing: normal;
  color: #061b31;
  text-decoration: none;
  transition: color 150ms ease;
}
.nav-link:hover {
  color: #533afd;
}
.nav-link:focus-visible {
  outline: 2px solid #533afd;
  outline-offset: 2px;
  border-radius: 4px;
}
.nav-link.active {
  color: #533afd;
  font-weight: 400;
}
.nav-cta {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.0;
  color: #ffffff;
  background: #533afd;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  transition: background 150ms ease;
}
.nav-cta:hover {
  background: #4434d4;
}

/* Stripe -- Navigation (Dark Section) */
.dark .nav {
  background: rgba(28, 30, 84, 0.9);
  backdrop-filter: blur(12px);
}
.dark .nav-logo {
  color: #ffffff;
}
.dark .nav-link {
  color: rgba(255, 255, 255, 0.8);
}
.dark .nav-link:hover {
  color: #ffffff;
}
.dark .nav-link.active {
  color: #ffffff;
}
```

### Linear -- Navigation

```css
/* Linear -- Top Navigation Bar (dark-mode-native) */
.nav {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  position: sticky;
  top: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 24px;
  background: #0f1011;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}
.nav-logo {
  color: #f7f8f8;
  text-decoration: none;
  /* Typically an SVG icon mark */
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 24px;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-link {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 14px;
  font-weight: 510;
  line-height: 1.50;
  letter-spacing: -0.182px;
  color: #d0d6e0;
  text-decoration: none;
  transition: color 150ms ease;
}
.nav-link:hover {
  color: #f7f8f8;
}
.nav-link:focus-visible {
  box-shadow: 0px 0px 0px 2px #5e6ad2;
  outline: none;
  border-radius: 4px;
}
.nav-link.active {
  color: #f7f8f8;
}
.nav-cta {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 14px;
  font-weight: 510;
  line-height: 1.0;
  color: #ffffff;
  background: #5e6ad2;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  text-decoration: none;
  transition: background 150ms ease;
}
.nav-cta:hover {
  background: #828fff;
}

/* Linear -- Navigation (Light Mode, if used) */
.light .nav {
  background: #f7f8f8;
  border-bottom-color: #e6e6e6;
}
.light .nav-link {
  color: #62666d;
}
.light .nav-link:hover {
  color: #0f1011;
}
.light .nav-link.active {
  color: #0f1011;
}
```

### Vercel -- Navigation

```css
/* Vercel -- Top Navigation Bar */
.nav {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  position: sticky;
  top: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 24px;
  background: #ffffff;
  box-shadow: rgba(0, 0, 0, 0.08) 0px 1px 0px;
}
.nav-logo {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 18px;
  font-weight: 600;
  color: #171717;
  text-decoration: none;
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 24px;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-link {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  color: #666666;
  text-decoration: none;
  transition: color 200ms ease;
}
.nav-link:hover {
  color: #171717;
}
.nav-link:focus-visible {
  outline: 2px solid hsla(212, 100%, 48%, 1);
  outline-offset: 2px;
  border-radius: 4px;
}
.nav-link.active {
  color: #171717;
  font-weight: 600;
}
.nav-cta {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  color: #ffffff;
  background: #171717;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  text-decoration: none;
  transition: background 200ms ease, color 200ms ease;
}
.nav-cta:hover {
  background: #ffffff;
  color: #171717;
  box-shadow: rgb(235, 235, 235) 0px 0px 0px 1px;
}

/* Vercel -- Navigation (Dark Mode) */
.dark .nav {
  background: #000000;
  box-shadow: rgba(255, 255, 255, 0.08) 0px 1px 0px;
}
.dark .nav-logo {
  color: #ffffff;
}
.dark .nav-link {
  color: #808080;
}
.dark .nav-link:hover {
  color: #ffffff;
}
.dark .nav-link.active {
  color: #ffffff;
}
.dark .nav-cta {
  background: #ffffff;
  color: #171717;
}
.dark .nav-cta:hover {
  background: #171717;
  color: #ffffff;
  box-shadow: rgb(51, 51, 51) 0px 0px 0px 1px;
}
```

---

## 5. Table

### Claude -- Table

```css
/* Claude -- Data Table */
.table {
  font-family: "Anthropic Sans", Arial, sans-serif;
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  background: #faf9f5;
  border: 1px solid #f0eee6;
  border-radius: 8px;
  overflow: hidden;
}

/* Claude -- Table Header */
.table thead {
  background: #f5f4ed;
}
.table th {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  color: #141413;
  text-align: left;
  padding: 10px 16px;
  border-bottom: 1px solid #f0eee6;
}
.table th[data-type="number"] {
  text-align: right;
}

/* Claude -- Table Body */
.table td {
  font-family: "Anthropic Sans", Arial, sans-serif;
  font-size: 15px;
  font-weight: 400;
  line-height: 1.60;
  letter-spacing: normal;
  color: #5e5d59;
  padding: 10px 16px;
  border-bottom: 1px solid #f0eee6;
}
.table td[data-type="number"] {
  font-family: "Anthropic Mono", monospace;
  font-size: 15px;
  text-align: right;
}
.table tbody tr:last-child td {
  border-bottom: none;
}

/* Claude -- Table: Alternating Rows */
.table.striped tbody tr:nth-child(even) {
  background: #f5f4ed;
}

/* Claude -- Table: Row Hover */
.table tbody tr:hover {
  background: #f0eee6;
}

/* Claude -- Table (Dark Mode) */
.dark .table {
  background: #30302e;
  border-color: #30302e;
}
.dark .table thead {
  background: #141413;
}
.dark .table th {
  color: #faf9f5;
  border-bottom-color: #30302e;
}
.dark .table td {
  color: #b0aea5;
  border-bottom-color: #30302e;
}
.dark .table.striped tbody tr:nth-child(even) {
  background: #141413;
}
.dark .table tbody tr:hover {
  background: #3d3d3a;
}
```

### Stripe -- Table

```css
/* Stripe -- Data Table */
.table {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  background: #ffffff;
  border: 1px solid #e5edf5;
  border-radius: 6px;
  overflow: hidden;
}

/* Stripe -- Table Header */
.table thead {
  background: #ffffff;
}
.table th {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 13px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: normal;
  color: #273951;
  text-align: left;
  padding: 10px 16px;
  border-bottom: 1px solid #e5edf5;
}
.table th[data-type="number"] {
  text-align: right;
  font-feature-settings: "ss01", "tnum";
}

/* Stripe -- Table Body */
.table td {
  font-family: "sohne-var", "SF Pro Display", system-ui, sans-serif;
  font-feature-settings: "ss01";
  font-size: 14px;
  font-weight: 300;
  line-height: 1.40;
  letter-spacing: normal;
  color: #64748d;
  padding: 10px 16px;
  border-bottom: 1px solid #e5edf5;
}
.table td[data-type="number"] {
  font-feature-settings: "ss01", "tnum";
  text-align: right;
}
.table tbody tr:last-child td {
  border-bottom: none;
}

/* Stripe -- Table: Alternating Rows */
.table.striped tbody tr:nth-child(even) {
  background: #f6f9fc;
}

/* Stripe -- Table: Row Hover */
.table tbody tr:hover {
  background: #f6f9fc;
}

/* Stripe -- Table (Dark Section) */
.dark .table {
  background: rgba(255, 255, 255, 0.03);
  border-color: rgba(255, 255, 255, 0.1);
}
.dark .table thead {
  background: rgba(255, 255, 255, 0.02);
}
.dark .table th {
  color: rgba(255, 255, 255, 0.7);
  border-bottom-color: rgba(255, 255, 255, 0.1);
}
.dark .table td {
  color: rgba(255, 255, 255, 0.5);
  border-bottom-color: rgba(255, 255, 255, 0.06);
}
.dark .table tbody tr:hover {
  background: rgba(255, 255, 255, 0.05);
}
```

### Linear -- Table

```css
/* Linear -- Data Table (dark-mode-native) */
.table {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 8px;
  overflow: hidden;
}

/* Linear -- Table Header */
.table thead {
  background: #0f1011;
}
.table th {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 13px;
  font-weight: 510;
  line-height: 1.50;
  letter-spacing: -0.13px;
  color: #f7f8f8;
  text-align: left;
  padding: 10px 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}
.table th[data-type="number"] {
  font-family: "Berkeley Mono", ui-monospace, "SF Mono", Menlo, monospace;
  text-align: right;
}

/* Linear -- Table Body */
.table td {
  font-family: "Inter Variable", "SF Pro Display", -apple-system, system-ui, sans-serif;
  font-feature-settings: "cv01", "ss03";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: normal;
  color: #d0d6e0;
  padding: 10px 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}
.table td[data-type="number"] {
  font-family: "Berkeley Mono", ui-monospace, "SF Mono", Menlo, monospace;
  font-size: 14px;
  text-align: right;
}
.table tbody tr:last-child td {
  border-bottom: none;
}

/* Linear -- Table: Alternating Rows */
.table.striped tbody tr:nth-child(even) {
  background: rgba(255, 255, 255, 0.04);
}

/* Linear -- Table: Row Hover */
.table tbody tr:hover {
  background: rgba(255, 255, 255, 0.05);
}

/* Linear -- Table (Light Mode, if used) */
.light .table {
  background: #ffffff;
  border: 1px solid #e6e6e6;
}
.light .table thead {
  background: #f7f8f8;
}
.light .table th {
  color: #0f1011;
  border-bottom-color: #e6e6e6;
}
.light .table td {
  color: #62666d;
  border-bottom-color: #f3f4f5;
}
.light .table tbody tr:hover {
  background: #f5f6f7;
}
```

### Vercel -- Table

```css
/* Vercel -- Data Table */
.table {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  background: #ffffff;
  border: none;
  border-radius: 8px;
  box-shadow: rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
  overflow: hidden;
}

/* Vercel -- Table Header */
.table thead {
  background: #fafafa;
}
.table th {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 500;
  line-height: 1.43;
  letter-spacing: normal;
  color: #171717;
  text-align: left;
  padding: 10px 16px;
  border-bottom: 1px solid #ebebeb;
}
.table th[data-type="number"] {
  font-family: "Geist Mono", ui-monospace, "SFMono-Regular", monospace;
  font-feature-settings: "tnum";
  text-align: right;
}

/* Vercel -- Table Body */
.table td {
  font-family: "Geist", Arial, sans-serif;
  font-feature-settings: "liga";
  font-size: 14px;
  font-weight: 400;
  line-height: 1.50;
  letter-spacing: normal;
  color: #4d4d4d;
  padding: 10px 16px;
  border-bottom: 1px solid #ebebeb;
}
.table td[data-type="number"] {
  font-family: "Geist Mono", ui-monospace, "SFMono-Regular", monospace;
  font-feature-settings: "tnum";
  text-align: right;
}
.table tbody tr:last-child td {
  border-bottom: none;
}

/* Vercel -- Table: Alternating Rows */
.table.striped tbody tr:nth-child(even) {
  background: #fafafa;
}

/* Vercel -- Table: Row Hover */
.table tbody tr:hover {
  background: #fafafa;
}

/* Vercel -- Table (Dark Mode) */
.dark .table {
  background: #171717;
  box-shadow: rgba(255, 255, 255, 0.08) 0px 0px 0px 1px;
}
.dark .table thead {
  background: #1a1a1a;
}
.dark .table th {
  color: #ffffff;
  border-bottom-color: #333333;
}
.dark .table td {
  color: #808080;
  border-bottom-color: #333333;
}
.dark .table.striped tbody tr:nth-child(even) {
  background: #1a1a1a;
}
.dark .table tbody tr:hover {
  background: #222222;
}
```

---

## Implementation Notes

### Font Loading Order

Each brand requires specific font loading. The CSS above assumes fonts are already loaded. Production font-face declarations:

```css
/* Claude: Custom Anthropic type family */
/* Load: Anthropic Serif (wght 500), Anthropic Sans (wght 400-500), Anthropic Mono (wght 400) */
/* Fallbacks: Georgia (serif), Arial (sans), monospace */

/* Stripe: Custom sohne-var variable font */
/* Load: sohne-var (wght 300-400), SourceCodePro (wght 500-700) */
/* Fallbacks: SF Pro Display, system-ui, sans-serif */

/* Linear: Inter Variable + Berkeley Mono */
/* Load: Inter Variable (wght 300-590), Berkeley Mono (wght 400) */
/* Fallbacks: SF Pro Display, -apple-system, system-ui, sans-serif */

/* Vercel: Geist Sans + Geist Mono */
/* Load: Geist (wght 400-600), Geist Mono (wght 400-500) */
/* Fallbacks: Arial, sans-serif / ui-monospace, SFMono-Regular */
```

### Transition Timing

| Brand | Default Duration | Easing | Notes |
|-------|-----------------|--------|-------|
| Claude | `150ms` | `ease` | Warm, organic feel |
| Stripe | `150ms` | `ease` | Clean, precise |
| Linear | `150ms` | `ease` | Consistent with app feel |
| Vercel | `200ms` | `ease` | Slightly slower, gallery-like |

### Dark Mode Strategy

| Brand | Strategy | Implementation |
|-------|----------|----------------|
| Claude | Light-first, dark sections via class | `.dark` class on section containers; alternating light/dark sections |
| Stripe | Light-first, brand-dark sections | `.dark` class for `#1c1e54` brand-dark sections |
| Linear | Dark-first (native) | Default CSS is dark; `.light` class for optional light contexts |
| Vercel | Light-first, full dark mode | `.dark` class on `<html>` or container; inverts the entire system |

### Shadow-as-Border vs CSS Border

Two brands (Claude, Vercel) use `box-shadow: 0px 0px 0px 1px` as their border mechanism. Two brands (Stripe, Linear) use CSS `border`. Key production differences:

```css
/* Shadow-border (Claude, Vercel): */
/* - Does not affect box model / dimensions */
/* - Rounds corners perfectly with border-radius */
/* - Transitions smoothly (opacity, color) */
/* - Cannot use border-collapse on tables (use separate + overflow: hidden) */
border: none;
box-shadow: rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;

/* CSS border (Stripe, Linear): */
/* - Adds to box model (use box-sizing: border-box) */
/* - Simpler to reason about */
/* - Works with border-collapse on tables */
border: 1px solid #e5edf5;
box-shadow: none;
```

### Disabled State Pattern

All four brands follow the same structural pattern with brand-specific values:

```css
/* Universal disabled pattern: */
:disabled {
  cursor: not-allowed;
  opacity: [0.3-0.6, brand-dependent];
  /* Remove hover/active transforms */
  /* Reduce color contrast */
  /* Remove or flatten shadows */
}
```

| Brand | Disabled Opacity | Additional Treatment |
|-------|-----------------|---------------------|
| Claude | `0.4-0.5` | Shadow removed, muted warm text |
| Stripe | `0.4` | Border lightens, text mutes to cool gray |
| Linear | `0.3-0.5` | Opacity reduction primary mechanism |
| Vercel | `0.4-0.5` | Shadow-border lightens, bg shifts to `#fafafa` |
