# Aurora UI — Quick Reference

## 🎨 CSS Custom Properties (Design Tokens)

```css
:root {
  /* Accent */
  --accent: #c8ff00;
  --accent-dim: rgba(200, 255, 0, 0.15);

  /* Backgrounds */
  --bg-deep: #050508;
  --bg-primary: #0a0a0f;
  --bg-elevated: #12121a;
  --bg-glass: rgba(10, 10, 15, 0.65);

  /* Surfaces */
  --surface-1: rgba(255, 255, 255, 0.03);
  --surface-2: rgba(255, 255, 255, 0.06);
  --surface-3: rgba(255, 255, 255, 0.10);

  /* Text */
  --text-primary: rgba(255, 255, 255, 0.95);
  --text-secondary: rgba(255, 255, 255, 0.60);
  --text-tertiary: rgba(255, 255, 255, 0.35);

  /* Borders */
  --border-subtle: rgba(255, 255, 255, 0.08);
  --border-hover: rgba(255, 255, 255, 0.15);
  --border-accent: rgba(200, 255, 0, 0.30);

  /* Easing */
  --ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
}
```

## 🧩 Technique Index

| # | Technique | File | Type |
|---|-----------|------|------|
| 1 | Smooth Scroll + Scroll Progress | `skill/SKILL.md` | JS |
| 2 | 3D Perspective Carousel | `skill/SKILL.md` | CSS/JS |
| 3 | Spring Physics Text Reveal | `skill/SKILL.md` | JS |
| 4 | Curtain Transition | `skill/SKILL.md` | JS |
| 5 | Canvas Particle Ribbon | `skill/SKILL.md` | Canvas |
| 6 | Mouse Spotlight | `examples/bento-hero.html` | JS |
| 7 | Glassmorphism Card | `skill/SKILL.md` | CSS |
| 8 | Animated Mesh Gradient | `skill/SKILL.md` | CSS |
| 9 | Magnetic Cursor | `skill/SKILL.md` | JS |
| 10 | Page Turn Card | `skill/SKILL.md` | JS |
| 11 | Liquid Mask Reveal | `skill/SKILL.md` | CSS |
| 12 | Number Counter | `skill/SKILL.md` | JS |
| 13 | Animated Gradient Border | `skill/SKILL.md` | CSS |
| 14 | Glow Border Trace | `skill/SKILL.md` | CSS |
| 15 | Magnetic Button | `skill/SKILL.md` | JS |
| 16 | Card 3D Tilt | `skill/SKILL.md` | JS |
| 17 | Spotlight Card Hover | `skill/SKILL.md` | CSS/JS |
| 18 | Shine Sweep | `skill/SKILL.md` | CSS |
| 19 | Ripple Effect | `skill/SKILL.md` | JS |
| 20 | Animated Underline | `skill/SKILL.md` | CSS |
| 21 | Staggered Reveal | `skill/SKILL.md` | JS |
| 22 | 3D Press Button | `skill/SKILL.md` | CSS |
| 23 | Floating Blobs | `examples/bento-hero.html` | CSS |
| 24 | Bento Grid | `examples/bento-hero.html` | CSS |
| 25 | Scroll Progress Bar | `examples/bento-hero.html` | CSS/JS |
| 26 | Skeleton Loading | `skill/SKILL.md` | CSS |
| 27 | SVG Mask Flashlight | `skill/SKILL.md` | CSS/JS |

## ⚡ Performance Rules

- Animate only `transform` + `opacity` (GPU compositing)
- Max 500 particles per canvas element
- Use `{ passive: true }` on scroll handlers
- Use IntersectionObserver over scroll events
- Max 2-3 concurrent canvas systems
- `backdrop-filter: blur()` ≤ 20px
- Resize debounce: 250ms
- Single HTML file < 150KB

## ♿ Accessibility Checklist

- [ ] WCAG AA contrast (≥ 4.5:1 normal, ≥ 3:1 large)
- [ ] `prefers-reduced-motion` fallback
- [ ] Touch-aware: `@media (hover: hover) and (pointer: fine)`
- [ ] Keyboard navigable with `:focus-visible`
- [ ] Semantic HTML5 landmarks
- [ ] No sticky hover states on touch devices

## 🏗️ Section Flow (Standard)

```
LOADER → HERO → MARQUEE → WORK (carousel + particles)
  → PROCESS (timeline) → PRICING (toggle + glass cards)
  → ABOUT (stats + bento) → CONTACT (CTA) → FOOTER
```
