# Week 1 Report — Transforming Wireframes into Static Web Pages

## Overview
Because no specific wireframe image was supplied in the prompt, I implemented a **standard marketing/landing-page wireframe** that appears frequently in product designs:

- Sticky header with logo + navigation + CTA
- Hero (two-column on desktop, stacked on mobile)
- 3-up feature card grid
- Two-column “How it works” section (steps + design notes)
- 3-up testimonial cards
- 3-up pricing cards with a featured plan
- FAQ accordion
- Footer + simple contact/CTA band

This provides a realistic practice target for translating common wireframe patterns into HTML/CSS while keeping the layout clean and consistent.

## Semantic HTML decisions
- Used structural landmarks: `header`, `nav`, `main`, `section`, `footer`.
- Each section has a clear heading (`h2`) and supporting text to match a typical wireframe hierarchy.
- Testimonials use `figure` + `blockquote` + `figcaption` for correct semantics.
- FAQ uses button-based headers (`button` inside `h3`) so it’s keyboard accessible.

## Layout strategy
### 1) Container + spacing system
- Implemented a reusable `.container` with a max width (`--container: 1120px`).
- Established spacing tokens (`--space-*`) and applied them consistently to reduce “off-by-a-few-pixels” drift.

### 2) Grid + flex patterns
- Header row uses flex for alignment.
- Repeated patterns use grid:
  - `.hero-grid` (2 columns desktop → 1 column mobile)
  - `.grid-3` for feature/testimonial cards (3 → 1)
  - `.pricing-grid` (3 → 1)
  - `.two-col` for content + aside (2 → 1)

### 3) Component reuse
Buttons (`.btn`, `.btn-primary`, `.btn-ghost`), cards (`.card`), and inputs (`.input`) were defined once and reused across the page to mimic a consistent “design system” style.

## Responsiveness approach
Mobile-first was used for many components, then enhanced via breakpoints:

- `@media (max-width: 980px)`:
  - hero becomes stacked
  - two-column sections become single-column
  - pricing collapses to one column
- `@media (max-width: 860px)`:
  - desktop nav/CTA hidden
  - hamburger menu enabled
- `@media (max-width: 520px)`:
  - tighter container padding
  - metrics stack for readability

These breakpoints are intentionally simple and align with common wireframe expectations.

## Interactions (small JS additions)
Although the task is “static”, two small interactions were included because they appear in real wireframes:

- **Mobile menu toggle** (updates `aria-expanded`, uses `hidden` attribute)
- **FAQ accordion** (single-open behavior; accessible buttons)


## Challenges & how they were solved
1. **No exact wireframe provided**
   - Solution: implement a canonical wireframe layout that demonstrates common section types and spacing.

2. **Keeping spacing consistent across sections**
   - Solution: use a small spacing token set (`--space-*`) and reuse layout primitives (`.container`, `.grid-3`, `.section-head`).

3. **Avoiding “desktop-only” layouts**
   - Solution: define how every grid collapses, and ensure nav is usable on mobile with a collapsible menu.

