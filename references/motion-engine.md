# Aurora UI — Motion & Animation Engine

Spring physics, scroll-linked animation, gesture system, staggered timelines, and interactive depth effects. All vanilla JS, zero dependencies, GPU-accelerated.

---

## Spring Physics Engine (Core)

```javascript
class Spring {
  constructor(config = {}) {
    this.stiffness = config.stiffness || 120;
    this.damping = config.damping || 12;
    this.mass = config.mass || 1;
    this.position = 0;
    this.velocity = config.initialVelocity || 0;
    this.target = 0;
    this.running = false;
    this.onUpdate = null;
    this.onComplete = null;
  }
  springTo(target) {
    this.target = target;
    if (!this.running) { this.running = true; this._tick(); }
  }
  _tick() {
    if (!this.running) return;
    const displacement = this.position - this.target;
    const springForce = -this.stiffness * displacement;
    const dampingForce = -this.damping * this.velocity;
    const acceleration = (springForce + dampingForce) / this.mass;
    this.velocity += acceleration;
    this.position += this.velocity;
    const isSettled = Math.abs(displacement) < 0.01 && Math.abs(this.velocity) < 0.01;
    if (isSettled) {
      this.position = this.target; this.velocity = 0; this.running = false;
      if (this.onComplete) this.onComplete();
    }
    if (this.onUpdate) this.onUpdate(this.position);
    if (this.running) requestAnimationFrame(() => this._tick());
  }
  get value() { return this.position; }
}
```

**Presets:**
```javascript
const springPresets = {
  buttonHover:  { stiffness: 200, damping: 15, mass: 0.5 },
  cardTilt:     { stiffness: 80,  damping: 10, mass: 1.2 },
  modalOpen:    { stiffness: 150, damping: 12, mass: 0.8 },
  dropdownOpen: { stiffness: 250, damping: 18, mass: 0.3 },
  pageTransition: { stiffness: 40, damping: 8,  mass: 2.0 },
  stagger:      { stiffness: 300, damping: 20, mass: 0.2 },
};
```

---

## Magnetic Button (Spring)

```javascript
const springX = new Spring({ stiffness: 100, damping: 12, mass: 0.8 });
const springY = new Spring({ stiffness: 100, damping: 12, mass: 0.8 });
btn.addEventListener('mousemove', (e) => {
  const r = btn.getBoundingClientRect();
  springX.springTo((e.clientX - r.left - r.width/2) * 0.25);
  springY.springTo((e.clientY - r.top - r.height/2) * 0.25);
});
btn.addEventListener('mouseleave', () => { springX.springTo(0); springY.springTo(0); });
(function anim() {
  if (springX.running || springY.running) { btn.style.transform = `translate(${springX.value}px,${springY.value}px)`; requestAnimationFrame(anim); }
})();
```

---

## Press Gesture (Spring)

```javascript
function addPressGesture(el, config = {}) {
  const scale = config.scale || 0.95;
  const spring = new Spring({ stiffness: 300, damping: 20, mass: 0.5 });
  el.addEventListener('mousedown', () => spring.springTo(scale));
  el.addEventListener('mouseup', () => spring.springTo(1));
  el.addEventListener('mouseleave', () => spring.springTo(1));
  (function anim() {
    if (spring.running) {
      el.style.transform = `scale3d(${spring.value},${spring.value},${spring.value})`;
      requestAnimationFrame(anim);
    }
  })();
}
```

---

## Hover Lift (Spring)

```javascript
function addHoverLift(el, config = {}) {
  const liftY = config.liftY || -8;
  const spring = new Spring({ stiffness: 180, damping: 14, mass: 0.6 });
  el.addEventListener('mouseenter', () => spring.springTo(liftY));
  el.addEventListener('mouseleave', () => spring.springTo(0));
  (function anim() {
    if (spring.running) { el.style.transform = `translateY(${spring.value}px)`; requestAnimationFrame(anim); }
  })();
}
```

---

## Scroll Progress Tracker

```javascript
class ScrollProgress {
  constructor(element, onUpdate) {
    this.el = element; this.onUpdate = onUpdate;
    this._bound = this._onScroll.bind(this);
    window.addEventListener('scroll', this._bound, { passive: true });
    this._measure();
  }
  _measure() {
    this.rect = this.el.getBoundingClientRect();
    this.elHeight = this.el.offsetHeight;
    this.viewportH = window.innerHeight;
  }
  _onScroll() {
    this._measure();
    const start = this.viewportH - this.rect.top;
    const range = this.elHeight + this.viewportH;
    this.onUpdate(Math.max(0, Math.min(1, start / range)));
  }
  destroy() { window.removeEventListener('scroll', this._bound); }
}
```

---

## Horizontal Scroll (Sticky Container)

```html
<div class="hscroll-container">
  <div class="hscroll-track">
    <div class="hscroll-panel">Panel 1</div>
    <div class="hscroll-panel">Panel 2</div>
    <div class="hscroll-panel">Panel 3</div>
  </div>
</div>
```
```css
.hscroll-container { height: 400vh; position: relative; }
.hscroll-track { position: sticky; top: 0; height: 100vh; display: flex; overflow: hidden; }
.hscroll-track .hscroll-panel { min-width: 100vw; height: 100%; display:flex; align-items:center; justify-content:center; }
```
```javascript
const container = document.querySelector('.hscroll-container');
const track = document.querySelector('.hscroll-track');
window.addEventListener('scroll', () => {
  const rect = container.getBoundingClientRect();
  const scrollable = container.offsetHeight - window.innerHeight;
  const progress = Math.max(0, Math.min(1, -rect.top / scrollable));
  track.style.transform = `translateX(${progress * -(track.scrollWidth - window.innerWidth)}px)`;
}, { passive: true });
```

---

## Stagger Timeline

```javascript
class StaggerTimeline {
  constructor(parent, selector = '>*', config = {}) {
    this.parent = parent; this.selector = selector;
    this.duration = config.duration || 0.5; this.stagger = config.stagger || 0.06;
    this.delayChildren = config.delayChildren || 0.15;
    this.fromValue = config.fromValue || { opacity: 0, y: 30 };
    this.toValue = config.toValue || { opacity: 1, y: 0 };
  }
  play() {
    this.parent.querySelectorAll(this.selector).forEach((child, i) => {
      child.style.opacity = this.fromValue.opacity;
      child.style.transform = `translateY(${this.fromValue.y || 30}px)`;
      setTimeout(() => {
        child.style.transition = `opacity ${this.duration}s cubic-bezier(0.34,1.56,0.64,1), transform ${this.duration}s cubic-bezier(0.34,1.56,0.64,1)`;
        child.style.opacity = this.toValue.opacity;
        child.style.transform = `translateY(${this.toValue.y || 0}px)`;
      }, (this.delayChildren + i * this.stagger) * 1000);
    });
  }
}
```

---

## Vue-Kinesis: Translate (Parallax)

```javascript
function addTranslateEffect(el, config = {}) {
  const magnitude = config.magnitude || 20;
  const springX = new Spring({ stiffness: 60, damping: 10, mass: 1.5 });
  const springY = new Spring({ stiffness: 60, damping: 10, mass: 1.5 });
  el._updateTranslate = (e) => {
    const rect = el.getBoundingClientRect();
    const normX = (e.clientX - (rect.left + rect.width/2)) / (rect.width/2);
    const normY = (e.clientY - (rect.top + rect.height/2)) / (rect.height/2);
    springX.springTo(normX * magnitude);
    springY.springTo(normY * magnitude);
  };
  el.addEventListener('mousemove', el._updateTranslate);
  el.addEventListener('mouseleave', () => { springX.springTo(0); springY.springTo(0); });
  (function anim() {
    if (springX.running || springY.running) { el.style.transform = `translate(${springX.value}px,${springY.value}px)`; requestAnimationFrame(anim); }
  })();
}
```

---

## Vue-Kinesis: Rotate (Tilt)

```javascript
function addRotateEffect(el, config = {}) {
  const maxRotation = config.maxRotation || 15;
  const springX = new Spring({ stiffness: 80, damping: 12, mass: 1.2 });
  const springY = new Spring({ stiffness: 80, damping: 12, mass: 1.2 });
  el.addEventListener('mousemove', (e) => {
    const rect = el.getBoundingClientRect();
    const normX = (e.clientX - (rect.left + rect.width/2)) / (rect.width/2);
    const normY = (e.clientY - (rect.top + rect.height/2)) / (rect.height/2);
    springX.springTo(normY * maxRotation);
    springY.springTo(-normX * maxRotation);
  });
  el.addEventListener('mouseleave', () => { springX.springTo(0); springY.springTo(0); });
  (function anim() {
    if (springX.running || springY.running) {
      el.style.transform = `perspective(800px) rotateX(${springX.value}deg) rotateY(${springY.value}deg)`;
      requestAnimationFrame(anim);
    }
  })();
}
```

---

## Vue-Kinesis: Depth Scene

```javascript
class KinesisDepthScene {
  constructor(container, depthSelector = '.depth-layer') {
    this.layers = container.querySelectorAll(depthSelector);
    this.springMap = new WeakMap();
    this.layers.forEach(layer => {
      const depth = parseFloat(layer.dataset.depth) || 1;
      this.springMap.set(layer, {
        springX: new Spring({ stiffness: 50, damping: 8, mass: depth * 0.8 }),
        springY: new Spring({ stiffness: 50, damping: 8, mass: depth * 0.8 }),
        depth
      });
    });
    container.addEventListener('mousemove', (e) => {
      const rect = container.getBoundingClientRect();
      const normX = (e.clientX - (rect.left + rect.width/2)) / (rect.width/2);
      const normY = (e.clientY - (rect.top + rect.height/2)) / (rect.height/2);
      this.springMap.forEach(({ springX, springY, depth }) => {
        springX.springTo(normX * depth * 15);
        springY.springTo(normY * depth * 15);
      });
    });
    container.addEventListener('mouseleave', () => {
      this.springMap.forEach(({ springX, springY }) => { springX.springTo(0); springY.springTo(0); });
    });
    this._animate();
  }
  _animate() {
    let any = false;
    this.springMap.forEach(({ springX, springY }) => {
      if (springX.running || springY.running) any = true;
    });
    if (any) {
      this.springMap.forEach((s, l) => { l.style.transform = `translate(${s.springX.value}px,${s.springY.value}px)`; });
      requestAnimationFrame(() => this._animate());
    }
  }
}
```

---

## Scroll Parallax (Background Depth)

```html
<div class="parallax-scene" style="height:200vh;position:relative;overflow:hidden">
  <div class="parallax-layer" data-speed="0.2" style="position:absolute;inset:-20%;background:linear-gradient(180deg,#0a1628,#1a3a5c)"></div>
  <div class="parallax-layer" data-speed="0.5" style="position:absolute;inset:-10%;background:linear-gradient(180deg,#1a5c3a,#2d8a5e)"></div>
  <div class="parallax-content" style="position:relative;z-index:2;padding:100px 24px;text-align:center">
    <h1 style="font-size:clamp(32px,6vw,72px);color:white;text-shadow:0 2px 20px rgba(0,0,0,0.5)">Scroll to see depth</h1>
  </div>
</div>
```
```javascript
function initScrollParallax(container) {
  const layers = container.querySelectorAll('.parallax-layer');
  window.addEventListener('scroll', () => {
    const rect = container.getBoundingClientRect();
    const scrolled = -rect.top;
    layers.forEach(l => { l.style.transform = `translateY(${scrolled * parseFloat(l.dataset.speed)}px)`; });
  }, { passive: true });
}
```

---

## Composite Card (Tilt + Lift + Scroll)

```javascript
function createCompositeCard(card) {
  const springRX = new Spring({ stiffness: 80, damping: 10, mass: 1.2 });
  const springRY = new Spring({ stiffness: 80, damping: 10, mass: 1.2 });
  const springLift = new Spring({ stiffness: 200, damping: 16, mass: 0.5 });
  card.addEventListener('mousemove', (e) => {
    const rect = card.getBoundingClientRect();
    const normX = (e.clientX - (rect.left + rect.width/2)) / (rect.width/2);
    const normY = (e.clientY - (rect.top + rect.height/2)) / (rect.height/2);
    springRX.springTo(normY * 12); springRY.springTo(-normX * 12);
  });
  card.addEventListener('mouseleave', () => { springRX.springTo(0); springRY.springTo(0); springLift.springTo(0); });
  card.addEventListener('mouseenter', () => springLift.springTo(-12));
  (function render() {
    if (springRX.running || springRY.running || springLift.running) {
      card.style.transform = `translateY(${springLift.value}px) perspective(800px) rotateX(${springRX.value}deg) rotateY(${springRY.value}deg)`;
      requestAnimationFrame(render);
    }
  })();
}
```
