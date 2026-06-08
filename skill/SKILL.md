---
name: aurora-ui
description: Premium cinematic web UI creation skill combining award-winning animation techniques from Lusion, Apple, Linear, Stripe, 21st.dev community, and Awwwards-winning sites. Delivers stunning single-file HTML/CSS/JS websites with scroll-driven narratives, 3D effects, particle systems, spring physics, glassmorphism, animated borders, micro-interactions, and minimalist premium aesthetics.
color: cyan
emoji: ✨
vibe: Creates cinematic, award-caliber web experiences that blend Lusion-level visual spectacle with Apple-level minimalist elegance. Every pixel intentional. Every animation meaningful.
tags: [web-ui, animation, creative-coding, premium-design, scroll-narrative, glassmorphism, particle-system]
created_at: 2026-06-07
agent_created: true
version: 3.0.0
---

# Aurora UI — Cinematic Web Design System

> "Make it spectacular, but make every pixel earn its place."

Create premium, cinematic single-page websites using pure HTML/CSS/JS with award-level visual effects. This skill combines techniques from **Lusion** (3D scroll narratives, particle systems), **Apple** (minimalist elegance, scroll-linked text reveals), **Linear** (glassmorphism, dark premium UI, subtle gradients), **Stripe** (animated mesh gradients), **21st.dev community** (magnetic buttons, animated numbers, glowing borders, 3D tilt cards), and **Awwwards/FWA** winners.

## Core Design Philosophy

### The Aurora Principle: "Spectacular Minimalism"
1. **Content-first spectacle** — Effects serve the story, not the other way around
2. **Performance is non-negotiable** — GPU-accelerated, 60 FPS, no layout thrashing
3. **Every animation has intent** — No gratuitous motion; each effect has a narrative purpose
4. **Dark cinematic aesthetic** — Deep backgrounds, luminous accents, atmospheric depth
5. **Pure vanilla** — Zero framework dependencies. Single HTML file. Fast load.

### Color System (Aurora Tokens)
```css
:root {
  /* Primary accent — aurora cyan-green */
  --accent: #c8ff00;
  --accent-dim: rgba(200, 255, 0, 0.15);

  /* Deep space background palette */
  --bg-deep: #050508;
  --bg-primary: #0a0a0f;
  --bg-elevated: #12121a;
  --bg-glass: rgba(10, 10, 15, 0.65);

  /* Surface hierarchy */
  --surface-1: rgba(255, 255, 255, 0.03);
  --surface-2: rgba(255, 255, 255, 0.06);
  --surface-3: rgba(255, 255, 255, 0.10);

  /* Text hierarchy (Apple-style) */
  --text-primary: rgba(255, 255, 255, 0.95);
  --text-secondary: rgba(255, 255, 255, 0.60);
  --text-tertiary: rgba(255, 255, 255, 0.35);
  --text-muted: rgba(255, 255, 255, 0.15);

  /* Border luminance */
  --border-subtle: rgba(255, 255, 255, 0.08);
  --border-hover: rgba(255, 255, 255, 0.15);
  --border-accent: rgba(200, 255, 0, 0.30);

  /* Gradient system (Stripe-style mesh) */
  --gradient-mesh: radial-gradient(ellipse at 20% 50%, rgba(0, 245, 255, 0.08) 0%, transparent 50%),
                   radial-gradient(ellipse at 80% 20%, rgba(200, 255, 0, 0.06) 0%, transparent 50%),
                   radial-gradient(ellipse at 50% 80%, rgba(114, 9, 183, 0.08) 0%, transparent 50%);

  /* Spacing (8pt grid, Apple/Linear style) */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --space-2xl: 48px;
  --space-3xl: 64px;
  --space-4xl: 96px;

  /* Typography scale */
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-3xl: 1.875rem;
  --text-4xl: 2.25rem;
  --text-5xl: 3rem;
  --text-6xl: 3.75rem;
  --text-7xl: 4.5rem;
  --text-8xl: 6rem;
  --text-9xl: 8rem;

  /* Border radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-2xl: 24px;
  --radius-full: 9999px;

  /* Transition timings (spring-inspired easing) */
  --ease-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-in-out-quad: cubic-bezier(0.45, 0, 0.55, 1);
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --duration-xslow: 800ms;

  /* Shadows (Linear-style depth) */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 8px 32px rgba(0, 0, 0, 0.5);
  --shadow-xl: 0 16px 48px rgba(0, 0, 0, 0.6);
  --shadow-glow: 0 0 40px rgba(200, 255, 0, 0.15);
  --shadow-glow-lg: 0 0 80px rgba(200, 255, 0, 0.20);

  /* Backdrop blur (Apple-style glass) */
  --blur-sm: blur(8px);
  --blur-md: blur(12px);
  --blur-lg: blur(20px);
  --blur-xl: blur(40px);
}
```

## Animation Toolkit (Proven Techniques)

### 1. Scroll-Driven Narratives
```javascript
// Lenis-style smooth scroll with inertia
class SmoothScroll {
  constructor() {
    this.current = 0;
    this.target = 0;
    this.ease = 0.075;
    this.init();
  }
  init() {
    window.addEventListener('scroll', () => { this.target = window.scrollY; }, { passive: true });
    this.animate();
  }
  animate() {
    this.current += (this.target - this.current) * this.ease;
    requestAnimationFrame(() => this.animate());
  }
}

// Scroll progress mapping (Lusion-style)
function getScrollProgress(element) {
  const rect = element.getBoundingClientRect();
  const sectionHeight = element.offsetHeight - window.innerHeight;
  if (sectionHeight <= 0) return 0;
  return Math.max(0, Math.min(1, -rect.top / sectionHeight));
}

// Intersection Observer for reveal animations
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('revealed');
    }
  });
}, { threshold: 0.15, rootMargin: '0px 0px -50px 0px' });
```

### 2. 3D Perspective Carousel
```css
.carousel-stage {
  perspective: 2000px;
  perspective-origin: 50% center;
  transform-style: preserve-3d;
}
.carousel-stage {
  transform: translateX(-200px) rotateY(-3deg);
}
.carousel {
  display: flex;
  gap: 80px;
  width: max-content;
  flex-shrink: 0;
}
.carousel-card {
  flex-shrink: 0;
  width: 70vw;
  max-width: 900px;
  height: 70vh;
}
```

### 3. Spring Physics Text Animation
```javascript
function splitTextIntoChars(element) {
  const text = element.textContent;
  element.innerHTML = '';
  element.style.display = 'inline-block';
  text.split('').forEach((char, i) => {
    const span = document.createElement('span');
    span.className = 'char';
    span.textContent = char === ' ' ? '\u00A0' : char;
    span.style.transform = `translate(${(Math.random() - 0.5) * 80}px, ${(Math.random() - 0.5) * 80}px) rotate(${(Math.random() - 0.5) * 30}deg) scale(0.5)`;
    span.style.opacity = '0';
    span.style.transition = 'none';
    element.appendChild(span);
  });
}
function animateCharsIn(chars, index = 0) {
  if (index >= chars.length) return;
  const delay = index * 25;
  setTimeout(() => {
    const char = chars[index];
    char.style.transition = `transform ${0.5 + Math.random() * 0.3}s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.4s ease-out`;
    char.style.transform = 'translate(0, 0) rotate(0deg) scale(1)';
    char.style.opacity = '1';
    animateCharsIn(chars, index + 1);
  }, delay);
}
```

### 4. Curtain Transition Effect
```javascript
function playCurtainTransition(callback) {
  const bars = document.querySelectorAll('.curtain-bar');
  bars.forEach((bar, i) => {
    const direction = i % 2 === 0 ? 'scaleY(0)' : 'scaleY(1)';
    const reverse = i % 2 === 0 ? 'scaleY(1)' : 'scaleY(0)';
    bar.style.transformOrigin = i % 2 === 0 ? 'top' : 'bottom';
    bar.style.transition = `transform 0.4s cubic-bezier(0.76, 0, 0.24, 1) ${i * 0.06}s`;
    requestAnimationFrame(() => { bar.style.transform = reverse; });
    setTimeout(() => {
      bar.style.transform = direction;
      if (callback) setTimeout(callback, 400 + i * 60);
    }, 400 + i * 60);
  });
}
```

### 5. Canvas Particle Ribbon (Simplex Noise Driven)
```javascript
class Ribbon {
  constructor(index, segmentCount = 40) {
    this.index = index;
    this.segments = [];
    this.segmentCount = segmentCount;
    this.amplitude = 30 + Math.random() * 40;
    this.speed = 0.3 + Math.random() * 0.4;
    this.phase = Math.random() * Math.PI * 2;
    for (let i = 0; i < segmentCount; i++) {
      this.segments.push({ x: 0, y: 0, targetX: 0, targetY: 0, vx: 0, vy: 0 });
    }
  }
  update(scrollProgress, time) {
    const w = canvasWidth;
    const h = canvasHeight;
    for (let i = 0; i < this.segmentCount; i++) {
      const t = i / (this.segmentCount - 1);
      const baseX = t * w;
      const scrollWave = Math.sin(t * Math.PI * 2 + time * this.speed + this.phase) * this.amplitude;
      const scrollAmp = scrollProgress * this.amplitude * 2;
      this.segments[i].targetX = baseX;
      this.segments[i].targetY = this.yBase + scrollWave + scrollAmp * Math.sin(t * Math.PI);
      const dx = this.segments[i].targetX - this.segments[i].x;
      const dy = this.segments[i].targetY - this.segments[i].y;
      this.segments[i].vx += dx * 0.04;
      this.segments[i].vy += dy * 0.04;
      this.segments[i].vx *= 0.88;
      this.segments[i].vy *= 0.88;
      this.segments[i].x += this.segments[i].vx;
      this.segments[i].y += this.segments[i].vy;
    }
  }
  draw(ctx) {
    if (this.segments.length < 2) return;
    ctx.beginPath();
    ctx.moveTo(this.segments[0].x, this.segments[0].y);
    for (let i = 1; i < this.segments.length - 1; i++) {
      const xc = (this.segments[i].x + this.segments[i + 1].x) / 2;
      const yc = (this.segments[i].y + this.segments[i + 1].y) / 2;
      ctx.quadraticCurveTo(this.segments[i].x, this.segments[i].y, xc, yc);
    }
    const alpha = 0.15 + (1 - this.index / RIBBON_COUNT) * 0.25;
    ctx.strokeStyle = `rgba(200, 255, 0, ${alpha})`;
    ctx.lineWidth = 1.5;
    ctx.stroke();
  }
}
```

### 6. Mouse Tracking + Spotlight Effect
```javascript
function initCardSpotlights() {
  document.querySelectorAll('.carousel-card').forEach(card => {
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      card.style.setProperty('--spot-x', x + 'px');
      card.style.setProperty('--spot-y', y + 'px');
    });
  });
}
```

```css
.carousel-card {
  background-image: radial-gradient(
    circle 180px at var(--spot-x, 50%) var(--spot-y, 50%),
    rgba(200, 255, 0, 0.08) 0%,
    transparent 100%
  );
}
```

### 7. Glassmorphism Card Pattern
```css
.glass-card {
  background: var(--bg-glass);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl);
  box-shadow: var(--shadow-lg);
  transition: border-color var(--duration-normal) ease,
              box-shadow var(--duration-normal) ease,
              transform var(--duration-normal) var(--ease-spring);
}
.glass-card:hover {
  border-color: var(--border-hover);
  box-shadow: var(--shadow-xl), var(--shadow-glow);
  transform: translateY(-4px);
}
```

### 8. Animated Gradient Background (Stripe-style)
```css
.gradient-bg {
  background: var(--gradient-mesh);
  background-size: 200% 200%;
  animation: gradientShift 12s ease-in-out infinite;
}
@keyframes gradientShift {
  0%, 100% { background-position: 0% 50%; }
  25% { background-position: 100% 0%; }
  50% { background-position: 100% 100%; }
  75% { background-position: 0% 100%; }
}
```

### 9. Magnetic Cursor Effect
```javascript
class MagneticCursor {
  constructor() {
    this.x = 0; this.y = 0;
    this.ringX = 0; this.ringY = 0;
    this.mouseX = 0; this.mouseY = 0;
    this.isHovering = false;
    this.strength = 0.4;
    this.ringEase = 0.15;
    this.init();
  }
  init() {
    document.addEventListener('mousemove', (e) => {
      this.mouseX = e.clientX;
      this.mouseY = e.clientY;
      this.isHovering = e.target.closest('[data-magnetic]') !== null;
    });
    this.animate();
  }
  animate() {
    this.x += (this.mouseX - this.x) * (this.isHovering ? this.strength : 0.35);
    this.y += (this.mouseY - this.y) * (this.isHovering ? this.strength : 0.35);
    this.ringX += (this.x - this.ringX) * this.ringEase;
    this.ringY += (this.y - this.ringY) * this.ringEase;
    requestAnimationFrame(() => this.animate());
  }
}
```

### 10. Page Turn Card Effect
```javascript
function playPageTurnEffect(callback) {
  const card = document.querySelector('.carousel-card.active-card');
  if (!card) { callback && callback(); return; }
  const leftHalf = document.createElement('div');
  const rightHalf = document.createElement('div');
  leftHalf.className = 'page-flip left-half';
  rightHalf.className = 'page-flip right-half';
  card.appendChild(leftHalf);
  card.appendChild(rightHalf);
  requestAnimationFrame(() => {
    leftHalf.style.transition = 'transform 0.6s cubic-bezier(0.76, 0, 0.24, 1)';
    leftHalf.style.transform = 'rotateY(-180deg)';
    rightHalf.style.transition = 'transform 0.6s cubic-bezier(0.76, 0, 0.24, 1) 0.1s';
    rightHalf.style.transform = 'rotateY(180deg)';
    setTimeout(() => {
      leftHalf.remove();
      rightHalf.remove();
      callback && callback();
    }, 800);
  });
}
```

### 11. Liquid Mask Reveal (Clip-path)
```css
.reveal-mask {
  clip-path: inset(0 100% 0 0);
  transition: clip-path 1s cubic-bezier(0.76, 0, 0.24, 1);
}
.reveal-mask.revealed {
  clip-path: inset(0 0% 0 0);
}
```

### 12. Number Counter Animation
```javascript
function animateNumberScroll(element, target, duration = 1500) {
  const start = 0;
  const startTime = performance.now();
  function update(currentTime) {
    const elapsed = currentTime - startTime;
    const progress = Math.min(elapsed / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    const current = Math.floor(start + (target - start) * eased);
    element.textContent = current;
    if (progress < 1) requestAnimationFrame(update);
  }
  requestAnimationFrame(update);
}
```

### 13. Animated Gradient Border
```css
@property --a {
  syntax: "<number>";
  inherits: false;
  initial-value: 0;
}
.gliding-border {
  position: relative;
  border-radius: var(--radius-xl);
  overflow: hidden;
}
.gliding-border::before {
  content: "";
  position: absolute;
  inset: -2px;
  background: conic-gradient(from var(--a), transparent 0%, var(--accent) 10%, transparent 20%);
  mask: linear-gradient(#fff, #fff) content-box, linear-gradient(#fff, #fff);
  mask-composite: exclude;
  animation: borderRotate 4s linear infinite;
  z-index: -1;
}
@keyframes borderRotate {
  to { --a: 360; }
}
@supports not (animation: --a linear) {
  .gliding-border::before { background: conic-gradient(from 0deg, var(--accent), var(--accent)); }
}
```

### 14. Glow Border Trace
```css
.trace-glow { position: relative; overflow: visible; }
.trace-glow::after {
  content: "";
  position: absolute;
  width: 6px; height: 6px;
  background: var(--accent);
  border-radius: 50%;
  box-shadow: 0 0 12px var(--accent), 0 0 24px var(--accent);
  offset-path: rect(0 0 100% 100% round var(--radius-xl));
  offset-distance: 0%;
  animation: traceAround 3s linear infinite;
}
@keyframes traceAround { to { offset-distance: 100%; } }
```

### 15. Magnetic Button (Spring Physics)
```javascript
class MagneticButton {
  constructor(element) {
    this.el = element;
    this.rect = element.getBoundingClientRect();
    this.x = 0; this.y = 0;
    this.mouseX = 0; this.mouseY = 0;
    this.strength = 0.35;
    this.springEase = 0.15;
    this.tiltX = 0; this.tiltY = 0;
    this.maxTilt = 12;
    this.init();
  }
  init() {
    this.el.addEventListener('mousemove', (e) => {
      const rect = this.el.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;
      this.mouseX = (e.clientX - centerX) * this.strength;
      this.mouseY = (e.clientY - centerY) * this.strength;
      this.tiltX = (e.clientY - centerY) / (rect.height / 2) * -this.maxTilt;
      this.tiltY = (e.clientX - centerX) / (rect.width / 2) * this.maxTilt;
    });
    this.el.addEventListener('mouseleave', () => { this.mouseX = 0; this.mouseY = 0; this.tiltX = 0; this.tiltY = 0; });
    this.animate();
  }
  animate() {
    this.x += (this.mouseX - this.x) * this.springEase;
    this.y += (this.mouseY - this.y) * this.springEase;
    this.el.style.transform = `translate(${this.x}px, ${this.y}px) rotateX(${this.tiltX}deg) rotateY(${this.tiltY}deg)`;
    requestAnimationFrame(() => this.animate());
  }
}
```

### 16. Card 3D Tilt Effect
```javascript
class TiltCard {
  constructor(element) {
    this.el = element;
    this.rect = element.getBoundingClientRect();
    this.init();
  }
  init() {
    this.el.addEventListener('mousemove', (e) => {
      this.rect = this.el.getBoundingClientRect();
      const x = (e.clientX - this.rect.left) / this.rect.width;
      const y = (e.clientY - this.rect.top) / this.rect.height;
      const tiltX = (y - 0.5) * -10;
      const tiltY = (x - 0.5) * 10;
      this.el.style.transform = `perspective(600px) rotateX(${tiltX}deg) rotateY(${tiltY}deg) scale3d(1.02, 1.02, 1.02)`;
      this.el.style.transition = 'transform 0.1s ease-out';
    });
    this.el.addEventListener('mouseleave', () => {
      this.el.style.transform = 'perspective(600px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)';
      this.el.style.transition = 'transform 0.5s cubic-bezier(0.34, 1.56, 0.64, 1)';
    });
  }
}
```

### 17. Spotlight Card Hover
```css
.spotlight-card { position: relative; overflow: hidden; --spot-x: 50%; --spot-y: 50%; }
.spotlight-card::before {
  content: ""; position: absolute; inset: 0;
  background: radial-gradient(circle 150px at var(--spot-x) var(--spot-y), rgba(200, 255, 0, 0.12) 0%, transparent 100%);
  opacity: 0; transition: opacity 0.3s ease; pointer-events: none; z-index: 2;
}
.spotlight-card:hover::before { opacity: 1; }
.spotlight-card::after {
  content: ""; position: absolute; inset: 0; border-radius: inherit; padding: 1px;
  background: radial-gradient(circle 150px at var(--spot-x) var(--spot-y), var(--accent) 0%, transparent 100%);
  mask: linear-gradient(#fff, #fff) content-box, linear-gradient(#fff, #fff);
  mask-composite: exclude; opacity: 0; transition: opacity 0.3s ease; pointer-events: none; z-index: 3;
}
.spotlight-card:hover::after { opacity: 0.6; }
```
```javascript
document.querySelectorAll('.spotlight-card').forEach(card => {
  card.addEventListener('mousemove', (e) => {
    const rect = card.getBoundingClientRect();
    card.style.setProperty('--spot-x', (e.clientX - rect.left) + 'px');
    card.style.setProperty('--spot-y', (e.clientY - rect.top) + 'px');
  });
});
```

### 18. Shine Sweep Effect
```css
.shine-sweep { position: relative; overflow: hidden; }
.shine-sweep::before {
  content: ""; position: absolute; top: 0; left: -100%; width: 50%; height: 100%;
  background: linear-gradient(120deg, transparent 0%, rgba(255,255,255,0.15) 50%, transparent 100%);
  transition: none;
}
.shine-sweep:hover::before { animation: shineSweep 0.8s ease forwards; }
@keyframes shineSweep { to { left: 150%; } }
```

### 19. Ripple/Burst Effect (Button)
```javascript
function createRipple(element, e) {
  const rect = element.getBoundingClientRect();
  const size = Math.max(rect.width, rect.height) * 2;
  const ripple = document.createElement('span');
  ripple.style.cssText = `
    position: absolute; width: ${size}px; height: ${size}px;
    left: ${e.clientX - rect.left - size / 2}px; top: ${e.clientY - rect.top - size / 2}px;
    background: rgba(255, 255, 255, 0.3); border-radius: 50%;
    transform: scale(0); animation: rippleExpand 0.6s cubic-bezier(0.4,0,0.2,1) forwards;
    pointer-events: none;
  `;
  element.style.position = 'relative';
  element.style.overflow = 'hidden';
  element.appendChild(ripple);
  setTimeout(() => ripple.remove(), 700);
}
```

### 20. Animated Underline Link
```css
.underlined-link { position: relative; text-decoration: none; color: var(--text-primary); }
.underlined-link::after {
  content: ""; position: absolute; bottom: -2px; left: 0; width: 100%; height: 1px;
  background: var(--accent); transform: scaleX(0); transform-origin: left;
  transition: transform var(--duration-normal) var(--ease-out-expo);
}
.underlined-link:hover::after { transform: scaleX(1); }
```

### 21. Staggered Children Reveal
```javascript
function staggerReveal(selector) {
  const elements = document.querySelectorAll(selector);
  elements.forEach((el, i) => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = `opacity 0.5s ease ${i * 0.08}s, transform 0.5s ease ${i * 0.08}s`;
    requestAnimationFrame(() => {
      el.style.opacity = '1';
      el.style.transform = 'translateY(0)';
    });
  });
}
```

### 22. Press-Down 3D Button
```css
.pressed-3d {
  border: none; padding: 12px 28px; border-radius: var(--radius-lg);
  background: var(--accent); color: #000; font-weight: 600;
  box-shadow: 0 4px 0 rgba(0,0,0,0.3), 0 6px 12px rgba(0,0,0,0.4);
  transition: all var(--duration-fast) ease; transform: translateY(0);
}
.pressed-3d:hover { box-shadow: 0 2px 0 rgba(0,0,0,0.3), 0 4px 8px rgba(0,0,0,0.3); transform: translateY(2px); }
.pressed-3d:active { transform: translateY(4px); box-shadow: 0 0px 0 rgba(0,0,0,0.3), 0 2px 4px rgba(0,0,0,0.3); }
```

### 23. Floating / Breathing Background Blobs
```css
.floating-blob { position: absolute; border-radius: 50%; filter: blur(80px); opacity: 0.3; animation: floatBlob 15s ease-in-out infinite; pointer-events: none; will-change: transform; }
.floating-blob:nth-child(1) { width: 400px; height: 400px; background: radial-gradient(circle, rgba(0,245,255,0.3), transparent); animation-duration: 18s; }
.floating-blob:nth-child(2) { width: 300px; height: 300px; background: radial-gradient(circle, rgba(200,255,0,0.2), transparent); animation-duration: 22s; animation-delay: -5s; }
.floating-blob:nth-child(3) { width: 350px; height: 350px; background: radial-gradient(circle, rgba(114,9,183,0.25), transparent); animation-duration: 20s; animation-delay: -10s; }
@keyframes floatBlob {
  0%, 100% { transform: translate(0, 0) scale(1); }
  25% { transform: translate(60px, -80px) scale(1.1); }
  50% { transform: translate(-40px, 60px) scale(0.9); }
  75% { transform: translate(80px, 40px) scale(1.05); }
}
```

### 24. CSS Bento Grid Layout (Apple-style)
```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(120px, auto);
  gap: var(--space-md);
}
.bento-item {
  background: var(--surface-1); border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl); padding: var(--space-lg);
  transition: border-color var(--duration-normal) ease, transform var(--duration-normal) var(--ease-spring);
}
.bento-item:hover { border-color: var(--border-hover); transform: translateY(-2px); }
.bento-item.span-2 { grid-column: span 2; }
.bento-item.span-3 { grid-column: span 3; }
.bento-item.row-2 { grid-row: span 2; }
@media (max-width: 768px) { .bento-grid { grid-template-columns: repeat(2, 1fr); } .bento-item.span-3 { grid-column: span 2; } }
@media (max-width: 480px) { .bento-grid { grid-template-columns: 1fr; } .bento-item.span-2, .bento-item.span-3 { grid-column: span 1; } }
```

### 25. Scroll-Driven Progress Bar
```css
.scroll-progress {
  position: fixed; top: 0; left: 0; height: 3px;
  background: linear-gradient(90deg, var(--accent), rgba(0,245,255,0.8));
  width: 0%; z-index: 10000; will-change: width; transition: width 50ms linear;
}
```
```javascript
function updateScrollProgress() {
  const scrollTop = window.scrollY;
  const docHeight = document.documentElement.scrollHeight - window.innerHeight;
  const progress = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
  const bar = document.querySelector('.scroll-progress');
  if (bar) bar.style.width = progress + '%';
}
window.addEventListener('scroll', updateScrollProgress, { passive: true });
```

### 26. Skeleton Loading Pattern
```css
.skeleton {
  background: linear-gradient(90deg, var(--surface-1) 25%, var(--surface-2) 50%, var(--surface-1) 75%);
  background-size: 200% 100%;
  animation: shimmer 1.5s ease-in-out infinite;
  border-radius: var(--radius-md);
}
@keyframes shimmer { 0% { background-position: 200% 0; } 100% { background-position: -200% 0; } }
```

### 27. SVG Mask Flashlight Reveal
```css
.mask-reveal { position: relative; overflow: hidden; }
.mask-reveal::before {
  content: ""; position: absolute; inset: 0; background: var(--text-primary);
  -webkit-mask-image: radial-gradient(circle 100px at var(--mask-x, 50%) var(--mask-y, 50%), black 0%, transparent 100%);
  mask-image: radial-gradient(circle 100px at var(--mask-x, 50%) var(--mask-y, 50%), black 0%, transparent 100%);
  opacity: 0; transition: opacity 0.3s ease;
}
.mask-reveal:hover::before { opacity: 1; }
```
```javascript
document.querySelectorAll('.mask-reveal').forEach(el => {
  el.addEventListener('mousemove', (e) => {
    const rect = el.getBoundingClientRect();
    el.style.setProperty('--mask-x', (e.clientX - rect.left) + 'px');
    el.style.setProperty('--mask-y', (e.clientY - rect.top) + 'px');
  });
});
```

## Performance Checklist (Hard Rules)
1. **GPU only** — Animate `transform` + `opacity`. Never animate `width`, `height`, `top`, `left`, `margin`, `padding`, `border-width`.
2. **Canvas budget** — Max 1-2 canvas elements. Max 500 particles per canvas. `requestAnimationFrame` only.
3. **Scroll handlers** — `{ passive: true }`. IntersectionObserver for reveals. Pre-calculate on load, not per frame.
4. **Resize debounce** — 250ms.
5. **backdrop-filter** — Max 20px blur. Sparse usage only.
6. **will-change** — Only on actively animating elements. Remove after animation.
7. **File size** — Single HTML < 150KB uncompressed.

## Accessibility Standards
1. **Contrast** — ≥ 4.5:1 normal text, ≥ 3:1 large text (WCAG AA).
2. **prefers-reduced-motion** — Always provide a fallback.
3. **Touch support** — `@media (hover: hover) and (pointer: fine)` for hover targets.
4. **Keyboard** — All interactive elements must work without mouse. Use `:focus-visible`.
5. **Semantic HTML** — Proper headings, nav, main, section, footer.
6. **No sticky hover on touch** — Detect touch and skip hover states.

## Standard Section Flow (Award-Winning Structure)
```
1. LOADER — Overlapping masks + percentage counter (0→100)
2. HERO — Full viewport, giant title with char-by-char reveal, subtle floating elements, scroll hint
3. MARQUEE — Infinite scrolling text banner
4. WORK — Horizontal scroll carousel (sticky + translateX), canvas particle ribbons, curtain transitions
5. PROCESS — Timeline with scroll-driven fill, alternating steps
6. PRICING — Toggle monthly/yearly, glass cards, staggered reveal, animated borders
7. ABOUT — Stats with number counter, mission text
8. CONTACT — CTA section with gradient background
9. FOOTER — Minimal links, social icons
```

## Quick Start Template
1. Define brand — name, tagline, accent color, sections
2. Set up skeleton — HTML structure + CSS variables
3. Build the loader — mask animation + counter
4. Create hero — full viewport, big text, character animation
5. Add marquee — infinite scroll banner
6. Add floating blobs — atmospheric background depth
7. Build work carousel — sticky container, horizontal flex cards
8. Add particles — canvas behind work section
9. Implement transitions — curtain effect, page flip
10. Add process timeline — scroll-driven fill
11. Build pricing cards — toggle, glass effect, stagger reveal, animated borders
12. Add about section — bento grid, number counter, stats
13. Contact + footer — clean CTA with magnetic button, minimal links
14. Polish — cursor effects, hover states, micro-interactions
15. Test — performance, responsiveness, all interactions

## Anti-Patterns (What NOT To Do)
1. **Never** use jQuery or any framework — vanilla HTML/CSS/JS only
2. **Never** animate `width`, `height`, `top`, `left` — use `transform` and `scale`
3. **Never** put heavy logic in scroll handlers — use IntersectionObserver
4. **Never** use more than 2-3 concurrent particle systems
5. **Never** make text unreadable with effects — content always wins
6. **Never** use `overflow: hidden` on scroll-container sections that need horizontal overflow
7. **Never** skip pre-calculating dimensions — measure on load, not per frame
8. **Avoid** backdrop-filter blur > 20px — mobile performance killer
9. **Avoid** too many glassmorphism panels — use sparingly
10. **Avoid** spring physics on every element — use selectively for maximum impact

---

**Aurora UI**: Where cinematic spectacle meets minimalist precision. Every effect intentional. Every pixel earned.
