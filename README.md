# ✨ Aurora UI — Cinematic Web Design System

> **Premium, award-caliber web UI components and techniques.**  
> Born from Lusion, Apple, Linear, Stripe, and Awwwards-winning inspiration.  
> Zero dependencies. Pure vanilla HTML/CSS/JS. One file.

![Aurora UI Banner](https://img.shields.io/badge/Aurora_UI-v3.0-0a0a0f?style=flat-square&labelColor=0a0a0f&color=c8ff00)

---

## What is Aurora UI?

Aurora UI is both a **design system** and a **Hermes Agent skill** for creating stunning single-page websites with cinematic visual effects. It distills award-winning web design patterns — scroll-driven narratives, 3D carousels, particle ribbons, spring physics animations, glassmorphism, magnetic interfaces, and more — into **25+ ready-to-use techniques** with a unified design language.

**The Aurora Principle:** *Spectacular Minimalism* — every pixel intentional, every animation meaningful, zero framework bloat.

### ✨ What You Can Build

| Technique | Description |
|-----------|-------------|
| Scroll Narratives | Lenis-style smooth scroll with inertia + progress mapping |
| 3D Carousel | Perspective-driven horizontal scroll with depth |
| Spring Physics | Character-by-character text reveals with spring easing |
| Particle Ribbons | Canvas-based simplex noise ribbons that respond to scroll |
| Glassmorphism | Linear-style glass cards with blur and subtle borders |
| Mesh Gradients | Stripe-style animated gradient backgrounds |
| Magnetic Cursor | Elements that pull toward the cursor with spring dynamics |
| Curtain Transitions | Dramatic section transitions with staggered bars |
| Animated Borders | CSS `@property` conic gradient borders + glow traces |
| Spotlight Cards | Mouse-tracked radial gradient overlays |
| Bento Grids | Apple-style adaptive grid layouts |
| Tilt 3D Cards | Perspective tilt on hover with spring return |
| Liquid Reveals | Clip-path mask transitions |
| And more… | 25+ techniques in total, all production-ready |

### 🎨 Design Token System

Aurora UI ships with a comprehensive CSS custom property system covering:

- **Accent colors** — configurable primary + dim variants
- **Deep space palette** — 5-level dark background hierarchy
- **Surface system** — 3-tier surface opacity + 4-tier text hierarchy
- **8pt spacing grid** — Apple/Linear-style `--space-xs` through `--space-4xl`
- **Typography scale** — `--text-xs` through `--text-9xl`
- **Radius system** — `--radius-sm` through `--radius-full`
- **Spring easing** — `--ease-spring` (0.34, 1.56, 0.64, 1)
- **Shadow depth** — 4-tier + glow variants
- **Blur system** — `--blur-sm` through `--blur-xl`

All tokens are customizable — change your accent color and the whole system adapts.

---

## 🚀 Quick Start

### Option 1: As a Hermes Agent Skill

If you use [Hermes Agent](https://hermes-agent.nousresearch.com):

```bash
# Install the skill
hermes skills install pppyx-hub/aurora-ui

# Or clone and install manually
git clone https://github.com/pppyx-hub/aurora-ui.git
hermes skills install ./aurora-ui/skill
```

Then load it in any Hermes session:
```
# Ask your agent to load the skill
skill_view(name='aurora-ui')
```

### Option 2: Standalone (No Hermes)

Just open any example file in your browser:

```bash
git clone https://github.com/pppyx-hub/aurora-ui.git
cd aurora-ui/examples
# Open any .html file in your browser
```

Each example is a self-contained single HTML file — zero build step, zero dependencies.

### Option 3: Build Your Own

1. Copy the CSS custom properties from `docs/quick-reference.md` into your project
2. Pick the components you need from `examples/`
3. Mix and match — everything is designed to compose together

---

## 📂 Repository Structure

```
aurora-ui/
├── README.md                 # You are here
├── LICENSE                   # MIT
├── skill/
│   └── SKILL.md              # Hermes Agent skill (full reference)
├── examples/
│   ├── bento-hero.html       # Bento grid hero with particle ribbon
│   ├── carousel-showcase.html# 3D carousel + curtain transitions
│   ├── pricing-cards.html    # Pricing with animated borders + toggle
│   └── landing-complete.html # Full page: every technique combined
└── docs/
    └── quick-reference.md    # Design tokens + technique index
```

---

## 🎯 Features At a Glance

- **Zero dependencies** — Pure HTML/CSS/JS. No frameworks, no build tools.
- **Single-file philosophy** — Each example is one self-contained HTML file.
- **GPU-accelerated** — Animates only `transform` and `opacity`. 60 FPS guaranteed.
- **Accessibility-first** — WCAG AA contrast, `prefers-reduced-motion` support, keyboard navigation.
- **Responsive** — Mobile-first with touch-aware interactions.
- **Dark cinematic aesthetic** — Deep backgrounds, luminous accents, atmospheric depth.
- **Performance budget** — Each page < 150KB uncompressed.

### Performance Rules (Hard Constraints)

| Rule | Why |
|------|-----|
| Animate only `transform` + `opacity` | GPU compositing, no layout thrashing |
| Max 500 particles per canvas | Keep 60 FPS on mobile |
| `{ passive: true }` on scroll handlers | Never block the scroll thread |
| `IntersectionObserver` over scroll events | Browser-optimized reveal detection |
| Max 2-3 concurrent canvas systems | GPU memory budget |
| `backdrop-filter: blur()` ≤ 20px | Mobile rendering cost |
| Debounce resize to 250ms | Avoid layout storms |

---

## 🖥️ Browser Support

- Chrome 90+ / Edge 90+
- Firefox 90+
- Safari 15+
- iOS Safari 15+

---

## 📜 License

MIT — use it freely in personal and commercial projects. See [LICENSE](LICENSE).

---

## 🙏 Inspiration & Credits

Aurora UI synthesizes patterns and techniques from the best in web design:

- **[Lusion](https://lusion.co/)** — 3D scroll narratives, particle systems
- **[Apple](https://www.apple.com/)** — Minimalist elegance, scroll reveals
- **[Linear](https://linear.app/)** — Glassmorphism, dark premium UI
- **[Stripe](https://stripe.com/)** — Animated mesh gradients
- **[21st.dev](https://21st.dev/)** — Magnetic buttons, animated borders, tilt cards
- **[Awwwards](https://www.awwwards.com/)** / **[FWA](https://thefwa.com/)** — Award-winning structural patterns

---

Built with ✨ by [pppyx](https://github.com/pppyx-hub)
