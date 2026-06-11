---
name: aurora-ui
description: AI-driven design system where style dictates structure. 11 aesthetics (10 unique + 1 default), modular section composition, spring-physics motion engine. Workflow + style intelligence + security + accessibility.
color: cyan
emoji: ✨
vibe: Style is structure, not decoration. Make each website unique.
tags: [web-ui, animation, creative-coding, premium-design, accessibility, frontend-security, responsive, production-ready, design-systems, diverse-aesthetics, design-workflow, requirement-analysis, code-review, modular-design, style-driven-design, anti-template, spring-physics, scroll-animation, gesture-system, parallax, motion-dev, kinesis]
created_at: 2026-06-07
agent_created: true
version: 9.0.0
---

# Aurora UI — Style-Driven Design System v9

> "Style is NOT a color swap. Style is STRUCTURE. The same topic in 12 styles = 12 completely different websites."

Create premium single-page websites (pure HTML/CSS/JS, single file, < 150KB) with **a complete product design workflow** — from requirement analysis through code review — plus **11 diverse visual aesthetics** (10 unique + 1 default Dark Cinematic) where **each style fundamentally changes the layout, structure, and content organization**.

## 🚨 ANTI-TEMPLATE PRINCIPLE

**The rule**: **The same topic designed in 11 different styles must produce 11 completely different websites.** Not 11 pages with different CSS variables but the same structure.

| Style | Wabi-Sabi environmental site SHOULD look like... | Brutalism SHOULD look like... |
|-------|--------------------------------------------------|-------------------------------|
| **Layout** | ONE quiet scene. Large whitespace. Minimal text. | Aggressive typography. Raw borders. Uncomfortable. |
| **Sections** | Maybe NO hero, NO marquee, NO grid. 1-4 sparse sections. | 2-6 aggressive sections. Horizontal scroll possible. |
| **Effects** | Slow fade-in, paper texture, stillness | Hard cuts, glitch text, zero spring physics |

**Style changes everything**: layout, spacing, content density, typography scale, animation approach, AND which sections to include.

---

## WORKFLOW — 6 Stages

### Stage 1: REQUIREMENT ANALYSIS

Do NOT write code. Instead:
1. Understand the product purpose (brand awareness? product showcase? informational?)
2. Identify the target audience
3. Extract key requirements (sections, content, interactive elements)
4. Define constraints (single page? brand colors?)

**Output**: A concise requirements summary (3-5 bullet points) for user confirmation.

### Stage 2: DESIGN PLAN (Style-Driven Structure)

1. **Choose a visual style** — Present 2-3 appropriate styles from the Style Selection Guide below.
2. **Style-Driven Structure Design** — Each style has a fundamentally different layout philosophy. Do NOT use the same sections for every style.
3. **Define the structural flow** for this SPECIFIC style — layout approach, not generic sections.
4. **Pick effects that match the style's philosophy** — Effects are part of the structural language.
5. **Present the plan** with structural differences highlighted.

### Stage 3: ASK & CLARIFY

Before coding, ask targeted questions. **Never assume details the user hasn't provided.**

```
📝 Quick Questions:
1. Content: Specific copy ready, or placeholder content?
2. Brand: Specific brand name, tagline, or color preferences?
3. Style: [Reconfirm chosen style]
4. Priority: Visual impact, information clarity, or interactivity?
5. Vibe: Describe your ideal page in 3 words.
6. Sections: Any sections you definitely want / don't want?
7. Structure: Linear storytelling or free-form exploration?
8. Feel: Quiet and contemplative, or bold and aggressive?
```

**Wait for answers. Only then proceed.**

### Stage 3b: STYLE × STRUCTURE ALIGNMENT CHECK

> **"If I showed this design without telling the style, could they guess which style it is?"**

If you can't tell the difference between the Wabi-Sabi version and the Brutalism version — **redo the design plan**.

### Stage 4: BUILD

1. Start from the style tokens (Section 1 base, overridden by chosen style)
2. Build sections in narrative order (Section 13 composition)
3. Add effects sparingly — Max 2-3 animation types per page
4. **Security first** — CSP meta tags, XSS-safe DOM
5. **Mobile-first** — Base layout for 320px
6. **Zero external images** — CSS gradients, SVG patterns, canvas only
7. **Maintain rhythm** — Alternate heavy (visual) and light (text) sections

### Stage 5: CODE REVIEW

Before showing result:
1. **Visual fidelity** — Style tokens correctly applied?
2. **Security audit** — CSP set? XSS-safe? No `eval()`?
3. **Accessibility** — WCAG AA contrast? Keyboard nav? `prefers-reduced-motion`?
4. **Performance** — GPU-only animations? < 150KB? No layout thrashing?
5. **Responsive** — Works on mobile (320px), tablet (768px), desktop (1280px)?
6. **Interactions** — `:hover`, `:active`, `:focus`, `:disabled` states?
7. **Content quality** — Readable placeholders? Proper hierarchy?

### Stage 6: SHIP & ITERATE

1. Present the file
2. Summarize what was built
3. Ask for feedback
4. Iterate based on feedback

---

## Design Principles

| Principle | What It Means |
|-----------|--------------|
| **Content-first spectacle** | Effects serve the story, not the other way around |
| **Mobile-first** | Base layout for 320px, enhance for larger screens |
| **Zero vulnerabilities** | CSP, XSS-safe DOM, SRI on externals |
| **GPU-accelerated only** | Animate `transform` + `opacity`. Nothing else. |
| **Every animation has intent** | No gratuitous motion |
| **Accessible by default** | WCAG AA, reduced-motion, keyboard navigation |
| **Single file, zero deps** | One HTML file, inline CSS+JS, < 150KB |
| **Compose, don't template** | Dynamic section architecture, not rigid layouts |

---

## 1. Base CSS Token System (Dark Cinematic — Default)

```css
:root {
  --accent: #c8ff00; --accent-dim: rgba(200, 255, 0, 0.15);
  --bg-deep: #050508; --bg-primary: #0a0a0f; --bg-elevated: #12121a;
  --bg-glass: rgba(10, 10, 15, 0.65);
  --surface-1: rgba(255,255,255,0.03); --surface-2: rgba(255,255,255,0.06); --surface-3: rgba(255,255,255,0.10);
  --text-primary: rgba(255,255,255,0.95); --text-secondary: rgba(255,255,255,0.60);
  --text-tertiary: rgba(255,255,255,0.35); --text-muted: rgba(255,255,255,0.15);
  --border-subtle: rgba(255,255,255,0.08); --border-hover: rgba(255,255,255,0.15);
  --space-xs: 4px; --space-sm: 8px; --space-md: 16px; --space-lg: 24px;
  --space-xl: 32px; --space-2xl: 48px; --space-3xl: 64px; --space-4xl: 96px;
  --text-xs: .75rem; --text-sm: .875rem; --text-base: 1rem; --text-lg: 1.125rem;
  --text-xl: 1.25rem; --text-2xl: 1.5rem; --text-3xl: 1.875rem; --text-4xl: 2.25rem;
  --text-5xl: 3rem; --text-6xl: 3.75rem; --text-7xl: 4.5rem; --text-8xl: 6rem; --text-9xl: 8rem;
  --radius-sm: 4px; --radius-md: 8px; --radius-lg: 12px; --radius-xl: 16px; --radius-2xl: 24px;
  --ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --fast: 150ms; --normal: 300ms; --slow: 500ms;
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.3); --shadow-md: 0 4px 12px rgba(0,0,0,0.4);
  --shadow-lg: 0 8px 32px rgba(0,0,0,0.5); --shadow-xl: 0 16px 48px rgba(0,0,0,0.6);
  --shadow-glow: 0 0 40px rgba(200,255,0,0.15);
  --blur-sm: blur(8px); --blur-md: blur(12px); --blur-lg: blur(20px);
  --safe-top: env(safe-area-inset-top, 0px); --safe-bottom: env(safe-area-inset-bottom, 0px);
}
```

> **Style Override**: When user picks a style, override the `:root` with that style's tokens.
> - **11 styles with full token systems**: see `references/style-tokens.md`
> - **Default (no style)**: use Section 1 tokens above (Dark Cinematic)

---

## 11.0 Style × Structure Mapping

| Style | Layout | Density | Spacing | Animation | Sections | Grid |
|-------|--------|---------|---------|-----------|----------|------|
| **Wabi-Sabi** | Stillness, void | Very low (1-3) | Extremely generous | Almost none | 1-4 | Non-grid |
| **Brutalism** | Confrontation, raw | High, chaotic | Uneven | Glitch, hard cuts | 2-6 | Broken grid |
| **Dark Cinematic** | Immersion, depth | Medium-high | Deep, layered | Particles, parallax | 3-8 | Full-bleed |
| **Editorial** | Magazine | Medium | Rhythmic | Page-turn, reveals | 4-10 | Asymmetric |
| **Pure White** | Clarity, IA | Medium-high | Precise | Micro-interactions | 4-8 | Strict grid |
| **Y2K** | Digital chaos | High, layered | Retro UI | Glitch, scanlines | 4-8 | Win95 grid |
| **Memphis** | Playful noise | High | Asymmetric, random | None needed | 3-7 | Chaotic |
| **Retro Vintage** | Analog warmth | Medium | Print-style | Film grain | 4-8 | Magazine |
| **Claymorphism** | Soft, playful | Medium | Rounded, spaced | Squish, bounce | 3-6 | Tile grid |
| **Parallax Scenic** | Depth, journey | Low-medium | Layered depth | Scroll parallax | 2-5 | Full-bleed |
| **Typography-Driven** | Type as art | Very low | Typography rhythm | Kinetic type | 1-4 | Text-only |

---

## Style Selection Guide

| Product Type | Recommended | Avoid |
|--------------|-------------|-------|
| SaaS / Startup | Pure White Premium, Dark Cinematic | Memphis, Y2K |
| Corporate | Pure White Premium, Editorial | Brutalism, Y2K, Memphis |
| Portfolio (Designer) | Typography-Driven, Brutalism | Pure White |
| Portfolio (Photographer) | Editorial, Wabi-Sabi | Brutalism |
| E-commerce | Pure White Premium, Brutalism | Y2K, Memphis |
| Music / Festival | Brutalism, Y2K, Memphis | Pure White, Wabi-Sabi |
| Food / Restaurant | Retro Vintage, Wabi-Sabi | Y2K, Brutalism |
| Travel | Parallax Scenic, Retro Vintage | Typography-Driven |
| Wellness | Wabi-Sabi, Claymorphism | Y2K, Brutalism |
| Tech / AI | Dark Cinematic, Typography-Driven | Wabi-Sabi, Retro |
| Fashion / Luxury | Editorial, Pure White Premium | Brutalism, Claymorphism |
| Education | Claymorphism, Pure White Premium | Y2K, Memphis |
| Creative Agency | Brutalism, Typography-Driven, Memphis | Pure White |

---

## 13. Section Library (15 Building Blocks)

> Each section is an independent building block. Choose dynamically — you NEVER use all 15 for every page.

| Block | Name | Purpose | When to skip |
|-------|------|---------|--------------|
| A | HERO | First impression — "what is this?" in 3s | Tool/utility pages |
| B | MARQUEE | Visual break + energy | Zen/quiet aesthetics |
| C | PROBLEM STATEMENT | "You understand my pain" | Portfolios, obvious problems |
| D | OVERVIEW | Clear explanation of what this is | Simple brands |
| E | FEATURES / BENEFITS | 3-6 capability cards | Non-product pages |
| F | STATS / METRICS | Quantify impact | New startups with no metrics |
| G | SHOWCASE / WORK | Visual proof through samples | Non-creative businesses |
| H | HOW IT WORKS | Demystify complexity | Simple one-click products |
| I | SOCIAL PROOF | Third-party validation | Can be faked for portfolio |
| J | PRICING | Investment options | Free products, custom-quote-only |
| K | TEAM / FOUNDER | Humanize the brand | Anonymous products |
| L | FAQ | Remove conversion objections | Simple pages |
| M | CTA | Final push — the one action | Always include |
| N | NEWSLETTER | Capture interest | Not applicable |
| O | FOOTER | Navigation + legal | Minimal pages |

### Section Composition Patterns

```
Marketing Page:    A → E → I → J → M → O
SaaS Homepage:     A → E → H → I → J → M → O
Creative Portfolio: A → G → K → I → M → O
Personal Portfolio: A → G → K → I → M → O
Brand Website:     A → C → E → F → K → I → M → O
Event / Conference: A → G → H → I → M → O
```

### Narrative Rules
1. Hero MUST be first
2. Understanding before trust (Features → Stats → Testimonials)
3. Social proof near conversion points
4. Alternate heavy/light sections for rhythm
5. End with a clear next step

### Style × Composition Rule

> **Before choosing sections, ask: "What would this style ACTUALLY use?"**
> - Wabi-Sabi: 1-4 sparse sections, large gaps, maybe no hero, no stats, no CTA
> - Brutalism: 2-6 aggressive sections, no symmetry, maybe horizontal scroll
> - Pure White: 4-8 precise sections, strict grid, micro-interactions
> - Dark Cinematic: 3-8 immersive sections, full-bleed, particles, depth layers

---

## 14. Code Review Checklist

### Security (MUST)
- CSP meta tag in `<head>` (script-src, style-src, img-src)
- No `eval()`, `setTimeout(string)`, `Function(string)`
- All user content via `textContent` (not `innerHTML`)
- External URLs validated with `new URL()`
- No inline event handlers (`onclick="..."`)

### Accessibility
- All interactive elements have `:focus-visible` styles
- Color contrast: body ≥ 4.5:1, large text ≥ 3:1
- `prefers-reduced-motion` respected
- Semantic HTML (h1→h6, nav, main, section, footer)
- Touch targets ≥ 44×44px

### Performance
- Animations use `transform` + `opacity` ONLY
- No layout thrashing (scroll events don't force reflow)
- IntersectionObserver > scroll event listeners
- Single particle system max
- `backdrop-filter` blur ≤ 20px
- `< 150KB` uncompressed
- No external image dependencies

### Responsive
- Mobile-first media queries
- Breakpoints: 320px, 640px, 768px, 1024px, 1280px
- Safe area insets (iPhone notch)
- Touch interactions work (`:active` states)
- No horizontal scrollbar on any breakpoint

### Visual & Content
- Style tokens match chosen aesthetic
- No visual clutter (effects serve content)
- Readable placeholder text (not Lorem Ipsum where possible)
- CTAs are action-oriented ("Start free trial" not "Submit")

---

## Reference Files

| Topic | File | Contents |
|-------|------|----------|
| **Style Tokens** | `references/style-tokens.md` | 11 styles' complete CSS token systems |
| **Animation Library** | `references/animation-lib.md` | 20+ copy-paste animation patterns |
| **Motion Engine** | `references/motion-engine.md` | Spring physics, scroll-linked, gestures, Kinesis |
| **Components** | `references/components.md` | Nav, buttons, cards, forms, modals, hero, showcase, steps, team, etc. |
| **Troubleshooting** | `references/troubleshooting.md` | Diagnostic flow for blank pages, CSS, animations, mobile |
| **Starter Template** | `templates/starter.html` | HTML5 skeleton with security meta tags |

---

**Aurora UI v9**: Style-driven design. 11 aesthetics that change structure, not just colors. Compose, don't template. Every website unique. Every style intentional. Every pixel earned. Every line of code secure.

---

## Companion Skills

| Skill | Purpose |
|-------|---------|
| `aurora-client-kickoff` | Client conversation workflow — from vague brief to clear design plan |
| `aurora-fiverr-delivery` | Fiverr file packaging, delivery checklist, order response templates |
