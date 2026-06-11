# Aurora UI — Animation Library

Copy-paste ready. GPU-accelerated (transform + opacity only). All use CSS variables.

---

## Scroll-Driven Reveal (Intersection Observer)

✅ Best for: any section entering viewport. Low cost, high impact.
⚠️ Avoid when: element is already visible on load (use staggered reveal instead).

```javascript
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('revealed'); });
}, { threshold: 0.15, rootMargin: '0px 0px -50px 0px' });
```

---

## Character-by-Character Reveal

✅ Best for: hero headlines, short titles (< 30 chars). High visual impact.
⚠️ Avoid when: text > 50 chars or on slow connections (40ms per char × 100 chars = 4s wait).

```javascript
function splitTextIntoChars(el) {
  const text = el.textContent; el.innerHTML = '';
  text.split('').forEach((ch, i) => {
    const span = document.createElement('span');
    span.className = 'char';
    span.textContent = ch === ' ' ? ' ' : ch;
    span.style.transform = `translate(${(Math.random()-0.5)*80}px, ${(Math.random()-0.5)*80}px) rotate(${(Math.random()-0.5)*30}deg) scale(0.5)`;
    span.style.opacity = '0';
    el.appendChild(span);
  });
  el.querySelectorAll('.char').forEach((ch, i) => {
    setTimeout(() => {
      ch.style.transition = `transform 0.6s cubic-bezier(0.34,1.56,0.64,1), opacity 0.4s ease`;
      ch.style.transform = 'translate(0,0) rotate(0deg) scale(1)';
      ch.style.opacity = '1';
    }, i * 40);
  });
}
```

---

## Smooth Scroll (Lenis-style)

✅ Best for: story-driven pages with parallax or scroll-linked animations.
⚠️ Avoid when: user expects native scroll feel (docs, dashboards, long-form reading).

```javascript
class SmoothScroll {
  constructor(ease = 0.075) {
    this.current = 0; this.target = 0; this.ease = ease;
    window.addEventListener('scroll', () => { this.target = window.scrollY; }, { passive: true });
    this.animate();
  }
  animate() {
    this.current += (this.target - this.current) * this.ease;
    requestAnimationFrame(() => this.animate());
  }
}
```

---

## Curtain Transition (8-bar alternate)

```javascript
function playCurtainTransition(callback) {
  document.querySelectorAll('.curtain-bar').forEach((bar, i) => {
    const dir = i % 2 === 0 ? 'scaleY(0)' : 'scaleY(1)';
    const rev = i % 2 === 0 ? 'scaleY(1)' : 'scaleY(0)';
    bar.style.transformOrigin = i % 2 === 0 ? 'top' : 'bottom';
    bar.style.transition = `transform 0.4s cubic-bezier(0.76,0,0.24,1) ${i*0.06}s`;
    requestAnimationFrame(() => { bar.style.transform = rev; });
    setTimeout(() => { bar.style.transform = dir; if (callback) setTimeout(callback, 400 + i * 60); }, 400 + i * 60);
  });
}
```

---

## 3D Tilt Card

✅ Best for: feature cards, portfolio items, product showcases.
⚠️ Avoid when: page has > 12 cards (16 concurrent rAF listeners tax battery).

```javascript
document.querySelectorAll('.tilt-card').forEach(card => {
  card.addEventListener('mousemove', (e) => {
    const r = card.getBoundingClientRect();
    card.style.transform = `perspective(600px) rotateX(${((e.clientY-r.top-r.height/2)/(r.height/2))*-8}deg) rotateY(${((e.clientX-r.left-r.width/2)/(r.width/2))*8}deg) scale3d(1.03,1.03,1.03)`;
    card.style.transition = 'transform 0.1s ease-out';
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = 'perspective(600px) rotateX(0) rotateY(0) scale3d(1,1,1)';
    card.style.transition = 'transform 0.5s cubic-bezier(0.34,1.56,0.64,1)';
  });
});
```

---

## Magnetic Button

✅ Best for: primary CTAs, hero buttons. Subtle engagement trigger.
⚠️ Avoid when: touch-only devices (no hover state — does nothing).

```javascript
document.querySelectorAll('[data-magnetic]').forEach(btn => {
  let mx = 0, my = 0, x = 0, y = 0;
  btn.addEventListener('mousemove', e => {
    const r = btn.getBoundingClientRect();
    mx = (e.clientX - r.left - r.width/2) * 0.35;
    my = (e.clientY - r.top - r.height/2) * 0.35;
  });
  btn.addEventListener('mouseleave', () => { mx = 0; my = 0; });
  (function anim() {
    x += (mx - x) * 0.15; y += (my - y) * 0.15;
    btn.style.transform = `translate(${x}px,${y}px)`;
    requestAnimationFrame(anim);
  })();
});
```

---

## Spotlight Card Hover

```css
.spotlight-card {
  position: relative; overflow: hidden;
  --spot-x: 50%; --spot-y: 50%;
}
.spotlight-card::before {
  content: ""; position: absolute; inset: 0;
  background: radial-gradient(circle 180px at var(--spot-x) var(--spot-y), rgba(200,255,0,0.10) 0%, transparent 100%);
  opacity: 0; transition: opacity 0.3s ease; pointer-events: none; z-index: 2;
}
.spotlight-card:hover::before { opacity: 1; }
```
```javascript
document.querySelectorAll('.spotlight-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const r = card.getBoundingClientRect();
    card.style.setProperty('--spot-x', (e.clientX - r.left) + 'px');
    card.style.setProperty('--spot-y', (e.clientY - r.top) + 'px');
  });
});
```

---

## Glassmorphism Card

```css
.glass-card {
  background: var(--bg-glass);
  backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl);
  transition: border-color var(--normal) ease, box-shadow var(--normal) ease, transform var(--normal) var(--ease-spring);
}
.glass-card:hover {
  border-color: var(--border-hover);
  box-shadow: var(--shadow-xl), var(--shadow-glow);
  transform: translateY(-4px);
}
```

---

## Animated Gradient Background

✅ Best for: hero backgrounds, full-screen sections.
⚠️ Avoid when: content above it has text — gradient animation can make reading uncomfortable.

```css
.gradient-bg {
  background: radial-gradient(ellipse at 20% 50%, rgba(0,245,255,0.08) 0%, transparent 50%),
              radial-gradient(ellipse at 80% 20%, rgba(200,255,0,0.06) 0%, transparent 50%),
              radial-gradient(ellipse at 50% 80%, rgba(114,9,183,0.08) 0%, transparent 50%);
  background-size: 200% 200%;
  animation: gradientShift 12s ease-in-out infinite;
}
@keyframes gradientShift {
  0%,100% { background-position: 0% 50%; }
  25% { background-position: 100% 0%; }
  50% { background-position: 100% 100%; }
  75% { background-position: 0% 100%; }
}
```

---

## Liquid Mask Reveal

```css
.reveal-mask {
  clip-path: inset(0 100% 0 0);
  transition: clip-path 1s cubic-bezier(0.76,0,0.24,1);
}
.reveal-mask.revealed { clip-path: inset(0 0% 0 0); }
```

---

## Animated Gradient Border

```css
@property --a { syntax: '<number>'; inherits: false; initial-value: 0; }
.gliding-border::before {
  content: ""; position: absolute; inset: -2px;
  background: conic-gradient(from var(--a), transparent 0%, var(--accent) 10%, transparent 20%);
  mask: linear-gradient(#fff,#fff) content-box, linear-gradient(#fff,#fff);
  mask-composite: exclude; animation: borderRotate 4s linear infinite; z-index: -1;
}
@keyframes borderRotate { to { --a: 360; } }
```

---

## Shine Sweep

```css
.shine-sweep { position: relative; overflow: hidden; }
.shine-sweep::before {
  content: ""; position: absolute; top:0; left:-100%; width:50%; height:100%;
  background: linear-gradient(120deg, transparent, rgba(255,255,255,0.15), transparent);
}
.shine-sweep:hover::before { animation: shineSweep 0.8s ease forwards; }
@keyframes shineSweep { to { left: 150%; } }
```

---

## Ripple Effect

```css
/* @keyframes rippleExpand { to { transform:scale(1); opacity:0; } } */
```
```javascript
function createRipple(el, e) {
  const r = el.getBoundingClientRect();
  const size = Math.max(r.width, r.height) * 2;
  const ripple = document.createElement('span');
  ripple.style.cssText = `position:absolute; width:${size}px; height:${size}px;
    left:${e.clientX-r.left-size/2}px; top:${e.clientY-r.top-size/2}px;
    background:rgba(255,255,255,0.3); border-radius:50%;
    transform:scale(0); animation:rippleExpand 0.6s cubic-bezier(0,0,0.2,1) forwards;
    pointer-events:none;`;
  el.style.position='relative'; el.style.overflow='hidden';
  el.appendChild(ripple); setTimeout(() => ripple.remove(), 700);
}
```

---

## Staggered Children Reveal

```javascript
function staggerReveal(selector, cls = 'revealed') {
  document.querySelectorAll(selector).forEach((el, i) => {
    el.style.opacity = '0'; el.style.transform = 'translateY(20px)';
    el.style.transition = `opacity 0.5s ease ${i*0.08}s, transform 0.5s ease ${i*0.08}s`;
    requestAnimationFrame(() => { el.style.opacity = '1'; el.style.transform = 'translateY(0)'; });
  });
}
```

---

## Floating Blobs

✅ Best for: cinematic hero backgrounds, adding depth to dark themes.
⚠️ Avoid when: CPU budget is tight on mobile — `filter: blur(100px)` on large elements is expensive.

```css
.floating-blob { position:absolute; border-radius:50%; filter:blur(100px); pointer-events:none; will-change:transform; }
.blob-1 { width:500px; height:500px; animation:floatBlob 18s ease-in-out infinite; }
.blob-2 { width:400px; height:400px; animation:floatBlob 22s ease-in-out infinite reverse; }
@keyframes floatBlob {
  0%,100% { transform: translate(0,0) scale(1); }
  25% { transform: translate(60px,-80px) scale(1.1); }
  50% { transform: translate(-40px,60px) scale(0.9); }
  75% { transform: translate(80px,40px) scale(1.05); }
}
```

---

## 3D Press-Down Button

```css
.pressed-3d {
  box-shadow: 0 4px 0 rgba(0,0,0,0.3), 0 6px 12px rgba(0,0,0,0.4);
  transition: all var(--fast) ease; transform: translateY(0);
}
.pressed-3d:hover { box-shadow: 0 2px 0 rgba(0,0,0,0.3), 0 4px 8px rgba(0,0,0,0.3); transform: translateY(2px); }
.pressed-3d:active { transform: translateY(4px); box-shadow: 0 0px 0 rgba(0,0,0,0.3); }
```

---

## Scroll Progress Bar

```css
.scroll-progress {
  position:fixed; top:0; left:0; height:2px; background:var(--accent); width:0%; z-index:10000;
  will-change:width; transition:width 50ms linear;
}
```
```javascript
window.addEventListener('scroll', () => {
  const h = document.documentElement.scrollHeight - window.innerHeight;
  const bar = document.querySelector('.scroll-progress');
  if (bar && h > 0) bar.style.width = (window.scrollY / h * 100) + '%';
}, { passive: true });
```

---

## Animated Underline Link

```css
.underlined-link { position:relative; text-decoration:none; }
.underlined-link::after {
  content:""; position:absolute; bottom:-2px; left:0; width:100%; height:1px;
  background:var(--accent); transform:scaleX(0); transform-origin:left;
  transition:transform var(--normal) var(--ease-out-expo);
}
.underlined-link:hover::after { transform:scaleX(1); }
```

---

## SVG Stroke Draw

```css
.svg-draw { stroke-dasharray: 1000; stroke-dashoffset: 1000; animation: drawPath 2s ease forwards; }
@keyframes drawPath { to { stroke-dashoffset: 0; } }
```

---

## Glow Border Trace

```css
.trace-glow::after {
  content:""; position:absolute; width:6px; height:6px; background:var(--accent);
  border-radius:50%; box-shadow:0 0 12px var(--accent);
  offset-path: rect(0 0 100% 100% round var(--radius-xl));
  offset-distance:0%; animation:traceAround 3s linear infinite;
}
@keyframes traceAround { to { offset-distance:100%; } }
```

---

## Mask Flashlight

```css
.mask-reveal { position:relative; overflow:hidden; }
.mask-reveal::before {
  content:""; position:absolute; inset:0; background:var(--text-primary);
  -webkit-mask-image: radial-gradient(circle 100px at var(--mask-x,50%) var(--mask-y,50%), black, transparent);
  mask-image: radial-gradient(circle 100px at var(--mask-x,50%) var(--mask-y,50%), black, transparent);
  opacity:0; transition:opacity 0.3s ease;
}
.mask-reveal:hover::before { opacity:1; }
```
```javascript
document.querySelectorAll('.mask-reveal').forEach(el => {
  el.addEventListener('mousemove', e => {
    const r = el.getBoundingClientRect();
    el.style.setProperty('--mask-x', (e.clientX - r.left) + 'px');
    el.style.setProperty('--mask-y', (e.clientY - r.top) + 'px');
  });
});
```

---

## Number Counter

```javascript
function animateNumber(el, target, duration = 2000) {
  const start = performance.now();
  (function tick(now) {
    const p = Math.min((now - start) / duration, 1);
    const eased = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.floor(target * eased);
    if (p < 1) requestAnimationFrame(tick);
  })(start);
}
```
