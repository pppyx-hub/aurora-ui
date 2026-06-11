# ✨ Aurora UI — Style-Driven Design System v9

> **11 aesthetics that change structure, not just colors.**  
> Compose, don't template. Every website unique. Every pixel earned.

[![Aurora UI](https://img.shields.io/badge/Aurora_UI-v9.0.0-0a0a0f?style=flat-square&labelColor=0a0a0f&color=c8ff00)](https://github.com/pppyx-hub/aurora-ui)

---

## What is Aurora UI?

Aurora UI is a **style-driven design system** for creating premium single-page websites (pure HTML/CSS/JS, single file, < 150KB) with a **complete product design workflow** — requirement analysis, design plan, build, code review, and delivery.

### Core Philosophy: Anti-Template

**Style is NOT a color swap. Style is STRUCTURE.** 11 aesthetics each fundamentally change the layout, spacing, content density, animation approach, AND which sections to include. A Wabi-Sabi environmental site looks nothing like a Brutalism one — because they're built from different structural rules.

### 11 Aesthetics

| Style | Vibe |
|-------|------|
| **Wabi-Sabi** | Stillness, void, muted earth tones, generous whitespace |
| **Brutalism** | Raw honesty, bold outlines, solid shadows, confrontation |
| **Dark Cinematic** (Default) | Immersion, deep blacks, glowing accents, particles |
| **Editorial** | High-fashion magazine, huge serif typography, asymmetric grid |
| **Pure White Premium** | Apple/Stripe/Linear quality, crisp, micro-interactions |
| **Y2K** | Holographic gradients, pixel fonts, Win95 UI, scanlines |
| **Memphis** | 80s post-modern chaos, geometric shapes, high-saturation |
| **Retro Vintage** | 1950s-70s warmth, mustard/rust/avocado, print textures |
| **Claymorphism** | Soft pillowy shapes, high border-radius, double shadows |
| **Parallax Scenic** | Layered depth, scroll-driven parallax, CSS gradient scenes |
| **Typography-Driven** | Type IS the design, massive scale, monochrome + one accent |

---

## Architecture

```
aurora-ui/
├── skill/
│   └── SKILL.md              # Main skill: workflow, section library, code review
├── references/
│   ├── style-tokens.md        # 11 styles' complete CSS token systems
│   ├── animation-lib.md       # 20+ copy-paste animation patterns
│   ├── motion-engine.md       # Spring physics, scroll-linked, gestures
│   ├── components.md          # Nav, hero, buttons, forms, showcase, etc.
│   └── troubleshooting.md     # Diagnostic flow for common issues
├── templates/
│   └── starter.html           # HTML5 skeleton with security meta tags
├── examples/
│   └── antiwar.html, bento-hero.html   # Legacy v3 examples
├── LICENSE
└── README.md
```

---

## Quick Start

### As a Hermes Agent Skill (Recommended)

```bash
# The skill is loaded automatically when working with aurora-ui
# Just tell the agent: "Use aurora-ui to build a landing page"
```

### Manual Use (Any AI/Editor)

1. Load `skill/SKILL.md` into your AI prompt
2. Reference the files in `references/` as needed
3. Start from `templates/starter.html` for a blank canvas

---

## 6-Stage Workflow

1. **Requirement Analysis** — Understand product, audience, constraints
2. **Design Plan (Style-Driven)** — Pick 1-2 styles, design structure per style
3. **Ask & Clarify** — 8 targeted questions before coding
4. **Build** — Compose sections, apply tokens, add effects sparingly
5. **Code Review** — Security, accessibility, performance, responsive checks
6. **Ship & Iterate** — Deliver, collect feedback, refine

---

## Section Library (15 Building Blocks)

| Block | Section | When to Use |
|-------|---------|-------------|
| A | Hero | Landing page first impression |
| B | Marquee | Visual break + social proof |
| C | Problem Statement | Hook by naming user's pain |
| D | Overview | Clear explanation |
| E | Features / Benefits | 3-6 capability cards |
| F | Stats / Metrics | Quantify impact |
| G | Showcase / Portfolio | Visual proof |
| H | How It Works | Demystify complexity |
| I | Social Proof | Third-party validation |
| J | Pricing | Investment options |
| K | Team / Founder | Humanize the brand |
| L | FAQ | Remove conversion objections |
| M | CTA | Final action push |
| N | Newsletter | Capture interest |
| O | Footer | Navigation + legal |

---

## Companion Skills

| Skill | Purpose |
|-------|---------|
| `aurora-client-kickoff` | Client conversation workflow — from vague brief to clear design plan |
| `aurora-fiverr-delivery` | Fiverr file packaging, delivery checklist, order response templates |

---

## Design Principles

| Principle | Meaning |
|-----------|---------|
| **Content-first spectacle** | Effects serve the story, not vice versa |
| **Mobile-first** | Base layout for 320px, enhance upward |
| **Zero vulnerabilities** | CSP, XSS-safe DOM, no eval |
| **GPU-accelerated only** | Animate `transform` + `opacity` only |
| **Every animation has intent** | No gratuitous motion |
| **Accessible by default** | WCAG AA, reduced-motion, keyboard nav |
| **Single file, zero deps** | One HTML file, inline CSS+JS, < 150KB |

---

## Version History

| Version | Date | Highlights |
|---------|------|------------|
| **v9.0.0** | 2026-06-07 | Complete rewrite: 11 styles, 15 sections, spring physics engine, motion engine, security-first code review, anti-template principle |
| **v3.0.0** | 2026-06-07 | Initial open-source release: cinematic techniques collection |

---

## License

MIT — feel free to use, modify, and distribute.
