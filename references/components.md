# Aurora UI — Component Snippets

Copy-paste ready. All components use CSS variables from the starter template.

> ⚠️ **Emoji note**: Emoji render differently across platforms (Windows, macOS, iOS, Android, Linux). For production delivery, replace emoji icons with inline SVG or CSS-drawn shapes for consistent cross-platform appearance. Use emoji only for rapid prototyping or when the target platform is known.

---

## Nav Bar

```html
<nav class="nav">
  <div class="nav-logo">BRAND</div>
  <button class="nav-toggle" aria-label="Menu">☰</button>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```
```css
.nav { position:fixed; top:0; left:0; right:0; z-index:100; padding:var(--space-md) var(--space-xl); display:flex; justify-content:space-between; align-items:center; backdrop-filter:blur(20px); background:rgba(5,5,8,0.8); border-bottom:1px solid var(--border-subtle); }
.nav-logo { font-size:14px; font-weight:700; letter-spacing:3px; text-transform:uppercase; }
.nav-links { display:flex; gap:var(--space-lg); list-style:none; }
.nav-links a { color:var(--text-secondary); text-decoration:none; font-size:13px; }
.nav-links a:hover { color:var(--text-primary); }
.nav-toggle { display:none; background:none; border:none; color:var(--text-primary); font-size:24px; cursor:pointer; }
@media(max-width:768px) {
  .nav-links { display:none; flex-direction:column; position:absolute; top:100%; left:0; right:0; background:var(--bg-deep); padding:var(--space-lg); }
  .nav-links.open { display:flex; }
  .nav-toggle { display:block; }
}
```
```js
document.querySelector('.nav-toggle')?.addEventListener('click', () => {
  document.querySelector('.nav-links')?.classList.toggle('open');
});
```

---

## Buttons (4 variants)

```html
<button class="btn btn--primary">Get Started</button>
<button class="btn btn--secondary">Learn More</button>
<button class="btn btn--ghost">Cancel</button>
<button class="btn btn--link">Read more →</button>
<button class="btn btn--primary btn--sm">Small</button>
<button class="btn btn--primary btn--lg">Large</button>
```
```css
.btn { display:inline-flex; align-items:center; justify-content:center; gap:8px; padding:12px 24px; border:none; border-radius:var(--radius-lg); font-size:var(--text-sm); font-weight:600; cursor:pointer; transition:all var(--fast) ease; text-decoration:none; user-select:none; position:relative; overflow:hidden; }
.btn:focus-visible { outline:2px solid var(--accent); outline-offset:2px; }
.btn:disabled { opacity:0.5; cursor:not-allowed; }
.btn--primary { background:var(--accent); color:#000; }
.btn--primary:hover:not(:disabled) { transform:translateY(-2px); box-shadow:var(--shadow-md); }
.btn--secondary { background:var(--surface-2); color:var(--text-primary); border:1px solid var(--border-subtle); }
.btn--secondary:hover:not(:disabled) { background:var(--surface-3); border-color:var(--border-hover); }
.btn--ghost { background:transparent; color:var(--text-primary); }
.btn--ghost:hover:not(:disabled) { background:var(--surface-1); }
.btn--link { background:none; color:var(--accent); padding:4px 0; }
.btn--sm { padding:8px 16px; font-size:var(--text-xs); }
.btn--lg { padding:16px 32px; font-size:var(--text-base); }
```

---

## Feature Cards (3-column)

```html
<div class="features-grid">
  <div class="feature-card">
    <div class="feature-card-icon">⚡</div>
    <h3>Fast</h3>
    <p>Description here</p>
  </div>
  <div class="feature-card">
    <div class="feature-card-icon">🎨</div>
    <h3>Beautiful</h3>
    <p>Description here</p>
  </div>
  <div class="feature-card">
    <div class="feature-card-icon">🔒</div>
    <h3>Secure</h3>
    <p>Description here</p>
  </div>
</div>
```
```css
.features-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr)); gap:var(--space-xl); padding:var(--space-xl) 0; }
.feature-card { background:var(--surface-1); border:1px solid var(--border-subtle); border-radius:var(--radius-xl); padding:var(--space-xl); transition:border-color var(--normal) ease, transform var(--normal) var(--ease-spring); }
.feature-card:hover { border-color:var(--border-hover); transform:translateY(-4px); }
.feature-card-icon { font-size:32px; margin-bottom:var(--space-md); }
.feature-card h3 { font-size:var(--text-lg); margin-bottom:var(--space-sm); }
.feature-card p { font-size:var(--text-sm); color:var(--text-secondary); line-height:1.6; }
```

---

## Pricing Cards (3-tier)

```html
<div class="pricing-grid">
  <div class="pricing-card">
    <div class="pricing-tier">Starter</div>
    <div class="pricing-price">$49<span>/mo</span></div>
    <ul class="pricing-features">
      <li>1 page</li>
      <li>Basic animations</li>
    </ul>
    <button class="btn btn--secondary">Get Started</button>
  </div>
  <div class="pricing-card featured">
    <div class="pricing-tier">Pro</div>
    <div class="pricing-price">$99<span>/mo</span></div>
    <ul class="pricing-features">
      <li>5 pages</li>
      <li>Premium animations</li>
      <li>Source file</li>
    </ul>
    <button class="btn btn--primary">Get Started</button>
  </div>
  <div class="pricing-card">
    <div class="pricing-tier">Enterprise</div>
    <div class="pricing-price">$299<span>/mo</span></div>
    <ul class="pricing-features">
      <li>Unlimited pages</li>
      <li>Everything included</li>
    </ul>
    <button class="btn btn--secondary">Contact Us</button>
  </div>
</div>
```
```css
.pricing-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(260px,1fr)); gap:var(--space-xl); align-items:start; }
.pricing-card { background:var(--surface-1); border:1px solid var(--border-subtle); border-radius:var(--radius-xl); padding:var(--space-xl); text-align:center; transition:border-color var(--normal) ease,transform var(--normal) var(--ease-spring); }
.pricing-card:hover { border-color:var(--border-hover); transform:translateY(-4px); }
.pricing-card.featured { border-color:var(--accent); background:var(--surface-2); box-shadow:var(--shadow-glow); position:relative; }
.pricing-card.featured::before { content:"BEST VALUE"; position:absolute; top:-12px; left:50%; transform:translateX(-50%); background:var(--accent); color:#000; font-size:11px; font-weight:700; padding:4px 16px; border-radius:var(--radius-full); letter-spacing:1px; }
.pricing-tier { font-size:var(--text-sm); color:var(--text-secondary); letter-spacing:1px; text-transform:uppercase; }
.pricing-price { font-size:var(--text-5xl); font-weight:900; margin:var(--space-md) 0; }
.pricing-price span { font-size:var(--text-sm); font-weight:400; color:var(--text-secondary); }
.pricing-features { list-style:none; text-align:left; margin:var(--space-lg) 0; }
.pricing-features li { padding:8px 0; font-size:var(--text-sm); color:var(--text-secondary); border-bottom:1px solid var(--border-subtle); }
.pricing-features li::before { content:"✓ "; color:var(--accent); font-weight:700; }
```

---

## Form Input

```html
<div class="form-group">
  <label class="form-label" for="email">Email</label>
  <input class="form-input" id="email" type="email" placeholder="you@example.com">
  <p class="form-hint">We'll never share your email.</p>
</div>
```
```css
.form-group { margin-bottom:var(--space-lg); }
.form-label { display:block; font-size:var(--text-sm); font-weight:500; margin-bottom:var(--space-xs); color:var(--text-secondary); }
.form-input { width:100%; padding:12px var(--space-md); border:1px solid var(--border-subtle); border-radius:var(--radius-lg); background:var(--surface-1); font-size:var(--text-base); color:var(--text-primary); transition:border-color var(--fast) ease, box-shadow var(--fast) ease; }
.form-input:focus { outline:none; border-color:var(--accent); box-shadow:0 0 0 3px var(--accent-dim); }
.form-input.error { border-color:#ef4444; }
.form-input::placeholder { color:var(--text-muted); }
.form-error { font-size:var(--text-xs); color:#ef4444; margin-top:var(--space-xs); }
.form-hint { font-size:var(--text-xs); color:var(--text-muted); margin-top:var(--space-xs); }
```

---

## Footer (4-column)

```html
<footer class="footer">
  <div class="footer-grid">
    <div class="footer-brand">
      <h3>Brand</h3>
      <p>Tagline or description</p>
    </div>
    <div class="footer-col">
      <h4>Product</h4>
      <a href="#">Features</a>
      <a href="#">Pricing</a>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </div>
    <div class="footer-col">
      <h4>Legal</h4>
      <a href="#">Privacy</a>
      <a href="#">Terms</a>
    </div>
  </div>
  <div class="footer-bottom">© 2026 Brand. All rights reserved.</div>
</footer>
```
```css
.footer { border-top:1px solid var(--border-subtle); padding:var(--space-4xl) var(--space-xl) var(--space-xl); }
.footer-grid { display:grid; grid-template-columns:2fr repeat(3,1fr); gap:var(--space-xl); max-width:1200px; margin:0 auto; }
.footer-brand h3 { font-size:var(--text-lg); margin-bottom:var(--space-sm); }
.footer-brand p { font-size:var(--text-sm); color:var(--text-secondary); }
.footer-col h4 { font-size:var(--text-sm); font-weight:600; margin-bottom:var(--space-md); letter-spacing:1px; text-transform:uppercase; }
.footer-col a { display:block; font-size:var(--text-sm); color:var(--text-secondary); text-decoration:none; padding:4px 0; transition:color var(--fast) ease; }
.footer-col a:hover { color:var(--text-primary); }
.footer-bottom { max-width:1200px; margin:var(--space-xl) auto 0; padding-top:var(--space-xl); border-top:1px solid var(--border-subtle); font-size:var(--text-xs); color:var(--text-muted); text-align:center; }
@media(max-width:768px) { .footer-grid { grid-template-columns:1fr 1fr; } }
@media(max-width:480px) { .footer-grid { grid-template-columns:1fr; } }
```

---

## Toast

```html
<div class="toast-container"></div>
<button onclick="showToast('Saved successfully!','success')">Show Toast</button>
```
```css
.toast-container { position:fixed; top:var(--space-xl); right:var(--space-xl); z-index:10001; display:flex; flex-direction:column; gap:var(--space-md); }
.toast { background:var(--bg-elevated); border:1px solid var(--border-subtle); border-radius:var(--radius-lg); padding:var(--space-md) var(--space-lg); display:flex; align-items:center; gap:var(--space-md); box-shadow:var(--shadow-lg); animation:toastIn .3s ease forwards; max-width:400px; }
.toast.removing { animation:toastOut .3s ease forwards; }
.toast--success { border-left:3px solid #10b981; }
.toast--error { border-left:3px solid #ef4444; }
.toast--warning { border-left:3px solid #f59e0b; }
.toast--info { border-left:3px solid #3b82f6; }
.toast-close { background:none; border:none; color:var(--text-muted); cursor:pointer; font-size:18px; }
@keyframes toastIn { from{transform:translateX(100%);opacity:0} to{transform:translateX(0);opacity:1} }
@keyframes toastOut { from{transform:translateX(0);opacity:1} to{transform:translateX(100%);opacity:0} }
```
```js
function showToast(msg, type='info', duration=4000) {
  const c = document.querySelector('.toast-container') || (()=>{const c=document.createElement('div');c.className='toast-container';document.body.appendChild(c);return c;})();
  const t = document.createElement('div');
  t.className = `toast toast--${type}`;
  t.innerHTML = `<span>${msg}</span><button class="toast-close" aria-label="Close">&times;</button>`;
  c.appendChild(t);
  t.querySelector('.toast-close').onclick = ()=>{t.classList.add('removing');setTimeout(()=>t.remove(),300);};
  setTimeout(()=>{t.classList.add('removing');setTimeout(()=>t.remove(),300);}, duration);
}
```

---

## Modal

```html
<div class="modal-overlay" id="myModal">
  <div class="modal">
    <div class="modal-header">
      <h2>Title</h2>
      <button class="modal-close" onclick="closeModal('myModal')">&times;</button>
    </div>
    <div class="modal-body"><p>Content here</p></div>
    <div class="modal-footer">
      <button class="btn btn--ghost" onclick="closeModal('myModal')">Cancel</button>
      <button class="btn btn--primary">Confirm</button>
    </div>
  </div>
</div>
<button onclick="openModal('myModal')">Open Modal</button>
```
```css
.modal-overlay { position:fixed; inset:0; z-index:10000; background:rgba(0,0,0,0.6); backdrop-filter:blur(8px); display:flex; align-items:center; justify-content:center; opacity:0; visibility:hidden; transition:opacity var(--normal) ease,visibility var(--normal) ease; }
.modal-overlay.open { opacity:1; visibility:visible; }
.modal { background:var(--bg-elevated); border:1px solid var(--border-subtle); border-radius:var(--radius-xl); padding:var(--space-xl); max-width:500px; width:90%; max-height:80vh; overflow-y:auto; transform:scale(0.95) translateY(20px); transition:transform var(--normal) var(--ease-spring); }
.modal-overlay.open .modal { transform:scale(1) translateY(0); }
.modal-header { display:flex; justify-content:space-between; align-items:center; margin-bottom:var(--space-lg); }
.modal-header h2 { font-size:var(--text-xl); }
.modal-close { background:none; border:none; color:var(--text-secondary); font-size:24px; cursor:pointer; }
.modal-close:hover { color:var(--text-primary); }
.modal-body { font-size:var(--text-sm); color:var(--text-secondary); line-height:1.6; }
.modal-footer { display:flex; justify-content:flex-end; gap:var(--space-md); margin-top:var(--space-xl); }
```
```js
function openModal(id) { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }
```

---

## Accordion / FAQ

```html
<div class="accordion">
  <div class="accordion-item">
    <button class="accordion-trigger">Question 1? <span class="accordion-icon">▼</span></button>
    <div class="accordion-content"><p>Answer here</p></div>
  </div>
  <div class="accordion-item">
    <button class="accordion-trigger">Question 2? <span class="accordion-icon">▼</span></button>
    <div class="accordion-content"><p>Answer here</p></div>
  </div>
</div>
```
```css
.accordion-item { border-bottom:1px solid var(--border-subtle); }
.accordion-trigger { width:100%; background:none; border:none; padding:var(--space-lg) 0; font-size:var(--text-base); font-weight:600; color:var(--text-primary); text-align:left; cursor:pointer; display:flex; justify-content:space-between; align-items:center; }
.accordion-trigger:hover { color:var(--accent); }
.accordion-icon { transition:transform var(--normal) ease; }
.accordion-item.open .accordion-icon { transform:rotate(180deg); }
.accordion-content { max-height:0; overflow:hidden; transition:max-height var(--normal) ease, padding var(--normal) ease; }
.accordion-item.open .accordion-content { max-height:500px; padding-bottom:var(--space-lg); }
.accordion-content p { font-size:var(--text-sm); color:var(--text-secondary); line-height:1.6; }
```
```js
document.querySelectorAll('.accordion-trigger').forEach(t => {
  t.addEventListener('click', () => {
    const item = t.closest('.accordion-item');
    const open = item.classList.contains('open');
    document.querySelectorAll('.accordion-item').forEach(i => i.classList.remove('open'));
    if (!open) item.classList.add('open');
  });
});
```

---

## Tabs

```html
<div class="tabs">
  <div class="tab-list">
    <button class="tab-btn active" data-tab-target="#tab1">Tab 1</button>
    <button class="tab-btn" data-tab-target="#tab2">Tab 2</button>
  </div>
  <div class="tab-panel active" id="tab1"><p>Content 1</p></div>
  <div class="tab-panel" id="tab2"><p>Content 2</p></div>
</div>
```
```css
.tab-list { display:flex; border-bottom:1px solid var(--border-subtle); }
.tab-btn { background:none; border:none; padding:var(--space-md) var(--space-lg); font-size:var(--text-sm); color:var(--text-secondary); cursor:pointer; position:relative; transition:color var(--fast) ease; }
.tab-btn:hover { color:var(--text-primary); }
.tab-btn.active { color:var(--text-primary); }
.tab-btn.active::after { content:""; position:absolute; bottom:-1px; left:0; width:100%; height:2px; background:var(--accent); }
.tab-panel { display:none; padding-top:var(--space-lg); }
.tab-panel.active { display:block; }
```
```js
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    const panel = document.querySelector(btn.dataset.tabTarget);
    if (panel) panel.classList.add('active');
  });
});
```

---

## Badge / Tag

```html
<span class="badge badge--accent">New</span>
<span class="badge badge--success">Live</span>
<span class="badge badge--error">Sold Out</span>
<span class="badge badge--warning">Pending</span>
<span class="badge badge--muted">Draft</span>
```
```css
.badge { display:inline-flex; align-items:center; gap:4px; padding:2px 10px; border-radius:var(--radius-full); font-size:var(--text-xs); font-weight:600; }
.badge--accent { background:var(--accent-dim); color:var(--accent); }
.badge--success { background:rgba(16,185,129,0.15); color:#10b981; }
.badge--error { background:rgba(239,68,68,0.15); color:#ef4444; }
.badge--warning { background:rgba(245,158,11,0.15); color:#f59e0b; }
.badge--muted { background:var(--surface-2); color:var(--text-secondary); }
```

---

## Toggle Switch

```html
<label class="toggle">
  <input type="checkbox">
  <span class="toggle-slider"></span>
</label>
```
```css
.toggle { position:relative; display:inline-block; width:48px; height:26px; }
.toggle input { opacity:0; width:0; height:0; }
.toggle-slider { position:absolute; inset:0; background:var(--surface-2); border-radius:var(--radius-full); cursor:pointer; transition:background var(--fast) ease; }
.toggle-slider::before { content:""; position:absolute; width:20px; height:20px; left:3px; top:3px; background:white; border-radius:50%; transition:transform var(--fast) var(--ease-spring); }
.toggle input:checked+.toggle-slider { background:var(--accent); }
.toggle input:checked+.toggle-slider::before { transform:translateX(22px); }
.toggle input:focus-visible+.toggle-slider { outline:2px solid var(--accent); outline-offset:2px; }
```

---

## Stats Row

```html
<div class="stats-row">
  <div><div class="stat-number" data-target="150">0</div><div class="stat-label">Projects</div></div>
  <div><div class="stat-number" data-target="50">0</div><div class="stat-label">Clients</div></div>
  <div><div class="stat-number" data-target="99">0</div><div class="stat-label">Satisfaction %</div></div>
</div>
```
```css
.stats-row { display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:var(--space-xl); text-align:center; padding:var(--space-xl) 0; }
.stat-number { font-size:var(--text-5xl); font-weight:900; color:var(--accent); }
.stat-label { font-size:var(--text-sm); color:var(--text-secondary); margin-top:4px; }
```
```js
// Animate numbers on scroll
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const el = e.target;
      const target = parseInt(el.dataset.target);
      const start = performance.now();
      (function tick(now) {
        const p = Math.min((now-start)/2000, 1);
        el.textContent = Math.floor(target * (1-Math.pow(1-p,3)));
        if (p < 1) requestAnimationFrame(tick);
      })(start);
      observer.unobserve(el);
    }
  });
}, { threshold: 0.5 });
document.querySelectorAll('.stat-number').forEach(el => observer.observe(el));
```

---

## Empty State / 404

```html
<div class="empty-state">
  <div class="empty-state-icon">🔍</div>
  <h2>Nothing here yet</h2>
  <p>Description of what's missing</p>
  <button class="btn btn--primary">Go Home</button>
</div>
```
```css
.empty-state { text-align:center; padding:var(--space-4xl) var(--space-xl); }
.empty-state-icon { font-size:64px; margin-bottom:var(--space-lg); opacity:0.5; }
.empty-state h2 { font-size:var(--text-2xl); margin-bottom:var(--space-sm); }
.empty-state p { color:var(--text-secondary); margin-bottom:var(--space-xl); }
```

---

## Hero (Full-Screen)

✅ Best for: landing page first impression. Use with short headline + single CTA.
⚠️ Avoid when: user needs to start reading immediately (use compact hero instead).

```html
<section class="hero">
  <div class="hero-content">
    <p class="hero-eyebrow">FOR PRODUCT TEAMS</p>
    <h1 class="hero-title">Build faster.<br>Ship with confidence.</h1>
    <p class="hero-subtitle">Aurora helps you design, build, and deliver premium websites in hours, not weeks.</p>
    <div class="hero-actions">
      <button class="btn btn--primary btn--lg">Get Started Free</button>
      <button class="btn btn--ghost btn--lg">Watch Demo →</button>
    </div>
  </div>
  <div class="hero-visual">
    <div class="hero-gradient"></div>
  </div>
</section>
```
```css
.hero { min-height: 100vh; display:flex; align-items:center; padding:var(--space-4xl) var(--space-xl); position:relative; overflow:hidden; gap:var(--space-4xl); }
.hero-content { flex:1; max-width:640px; z-index:2; }
.hero-eyebrow { font-size:var(--text-xs); letter-spacing:3px; text-transform:uppercase; color:var(--accent); margin-bottom:var(--space-lg); }
.hero-title { font-size:var(--text-7xl); font-weight:900; line-height:0.95; letter-spacing:-0.03em; margin-bottom:var(--space-xl); }
.hero-subtitle { font-size:var(--text-lg); color:var(--text-secondary); line-height:1.6; max-width:480px; margin-bottom:var(--space-2xl); }
.hero-actions { display:flex; gap:var(--space-md); flex-wrap:wrap; }
.hero-visual { flex:1; min-height:400px; position:relative; }
.hero-gradient { position:absolute; inset:0; background:radial-gradient(ellipse at 30% 50%, var(--accent-dim), transparent 60%); }
@media(max-width:768px) { .hero { flex-direction:column; text-align:center; padding-top:var(--space-4xl); } .hero-title { font-size:var(--text-5xl); } .hero-subtitle { max-width:100%; } .hero-actions { justify-content:center; } .hero-visual { min-height:200px; width:100%; } }
```

---

## Compact Hero (Minimal)

For interior pages, dashboards, or when you want a smaller hero.

```html
<section class="hero-compact">
  <h1 class="hero-compact-title">About Us</h1>
  <p class="hero-compact-subtitle">We build tools that help teams design better websites.</p>
</section>
```
```css
.hero-compact { padding:var(--space-4xl) var(--space-xl) var(--space-2xl); text-align:center; max-width:640px; margin:0 auto; }
.hero-compact-title { font-size:var(--text-4xl); font-weight:800; margin-bottom:var(--space-md); }
.hero-compact-subtitle { font-size:var(--text-lg); color:var(--text-secondary); }
```

---

## Marquee / Logo Bar

✅ Best for: social proof (logos of clients/partners), visual break between sections.
⚠️ Avoid when: no logos to show, or you need users to read text (marquee is purely visual).

```html
<div class="marquee-container">
  <div class="marquee-track" aria-label="Trusted by leading companies">
    <div class="marquee-group">
      <span class="marquee-logo">COMPANY A</span>
      <span class="marquee-logo">COMPANY B</span>
      <span class="marquee-logo">COMPANY C</span>
      <span class="marquee-logo">COMPANY D</span>
      <span class="marquee-logo">COMPANY E</span>
      <span class="marquee-logo">COMPANY F</span>
    </div>
    <div class="marquee-group" aria-hidden="true">
      <span class="marquee-logo">COMPANY A</span>
      <span class="marquee-logo">COMPANY B</span>
      <span class="marquee-logo">COMPANY C</span>
      <span class="marquee-logo">COMPANY D</span>
      <span class="marquee-logo">COMPANY E</span>
      <span class="marquee-logo">COMPANY F</span>
    </div>
  </div>
</div>
```
```css
.marquee-container { overflow:hidden; padding:var(--space-2xl) 0; border-top:1px solid var(--border-subtle); border-bottom:1px solid var(--border-subtle); }
.marquee-track { display:flex; width:fit-content; animation:marqueeScroll 30s linear infinite; gap:var(--space-4xl); }
.marquee-group { display:flex; gap:var(--space-4xl); align-items:center; }
.marquee-logo { font-size:var(--text-lg); font-weight:700; letter-spacing:2px; color:var(--text-muted); white-space:nowrap; }
@keyframes marqueeScroll { from { transform:translateX(0); } to { transform:translateX(-50%); } }
@media(prefers-reduced-motion) { .marquee-track { animation:none; } }
```

---

## Showcase / Portfolio Grid

✅ Best for: creative portfolios, case studies, product screenshots.
⚠️ Avoid when: you have < 3 items (use feature cards instead).

```html
<section class="showcase">
  <div class="showcase-grid">
    <article class="showcase-card">
      <div class="showcase-thumb" style="background:linear-gradient(135deg,#1a3a5c,#2d8a5e)"></div>
      <div class="showcase-info">
        <span class="badge badge--accent">Design</span>
        <h3>Project Name</h3>
        <p>Brief description of the project and the impact it made.</p>
      </div>
    </article>
    <article class="showcase-card">
      <div class="showcase-thumb" style="background:linear-gradient(135deg,#5c1a3a,#8a5e2d)"></div>
      <div class="showcase-info">
        <span class="badge badge--accent">Development</span>
        <h3>Another Project</h3>
        <p>Brief description of the project and the impact it made.</p>
      </div>
    </article>
    <article class="showcase-card">
      <div class="showcase-thumb" style="background:linear-gradient(135deg,#1a5c3a,#2d5e8a)"></div>
      <div class="showcase-info">
        <span class="badge badge--accent">Branding</span>
        <h3>Third Project</h3>
        <p>Brief description of the project and the impact it made.</p>
      </div>
    </article>
  </div>
</section>
```
```css
.showcase { padding:var(--space-4xl) var(--space-xl); }
.showcase-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(320px,1fr)); gap:var(--space-xl); max-width:1200px; margin:0 auto; }
.showcase-card { border-radius:var(--radius-xl); overflow:hidden; border:1px solid var(--border-subtle); transition:transform var(--normal) var(--ease-spring), border-color var(--normal) ease; background:var(--surface-1); }
.showcase-card:hover { transform:translateY(-6px); border-color:var(--border-hover); }
.showcase-thumb { height:240px; display:flex; align-items:center; justify-content:center; }
.showcase-info { padding:var(--space-lg); }
.showcase-info .badge { margin-bottom:var(--space-sm); }
.showcase-info h3 { font-size:var(--text-lg); margin-bottom:var(--space-xs); }
.showcase-info p { font-size:var(--text-sm); color:var(--text-secondary); line-height:1.6; }
@media(max-width:480px) { .showcase-grid { grid-template-columns:1fr; } }
```

---

## How It Works (Steps)

✅ Best for: demystifying complex processes (signup flow, product workflow).
⚠️ Avoid when: the process is a single step or trivial.

```html
<section class="steps">
  <div class="steps-header">
    <h2>How It Works</h2>
    <p>Three simple steps to get started.</p>
  </div>
  <div class="steps-grid">
    <div class="step-card">
      <span class="step-number">01</span>
      <h3>Choose Your Style</h3>
      <p>Pick from 11 different aesthetics — or let us recommend one based on your brand.</p>
    </div>
    <div class="step-connector" aria-hidden="true"></div>
    <div class="step-card">
      <span class="step-number">02</span>
      <h3>Customize Content</h3>
      <p>Add your copy, images, and brand colors. Every section is built to fit your needs.</p>
    </div>
    <div class="step-connector" aria-hidden="true"></div>
    <div class="step-card">
      <span class="step-number">03</span>
      <h3>Ship in Hours</h3>
      <p>One HTML file, zero dependencies. Open in any browser or deploy to production.</p>
    </div>
  </div>
</section>
```
```css
.steps { padding:var(--space-4xl) var(--space-xl); text-align:center; }
.steps-header { max-width:600px; margin:0 auto var(--space-4xl); }
.steps-header h2 { font-size:var(--text-4xl); font-weight:800; margin-bottom:var(--space-md); }
.steps-header p { color:var(--text-secondary); font-size:var(--text-lg); }
.steps-grid { display:flex; gap:var(--space-xl); justify-content:center; align-items:flex-start; max-width:900px; margin:0 auto; }
.step-card { flex:1; text-align:center; padding:var(--space-xl); border-radius:var(--radius-xl); background:var(--surface-1); border:1px solid var(--border-subtle); transition:transform var(--normal) var(--ease-spring); }
.step-card:hover { transform:translateY(-4px); }
.step-number { display:inline-block; font-size:var(--text-5xl); font-weight:900; color:var(--accent); opacity:0.3; line-height:1; margin-bottom:var(--space-md); }
.step-card h3 { font-size:var(--text-lg); margin-bottom:var(--space-sm); }
.step-card p { font-size:var(--text-sm); color:var(--text-secondary); line-height:1.6; }
.step-connector { width:40px; height:2px; background:var(--border-subtle); align-self:center; flex-shrink:0; }
@media(max-width:768px) { .steps-grid { flex-direction:column; align-items:stretch; } .step-connector { width:100%; height:40px; /* vertical connector */ position:relative; } .step-connector::after { content:''; position:absolute; top:0; left:50%; width:2px; height:100%; background:var(--border-subtle); } }
```

---

## Team Section

Show the people behind the brand.

```html
<section class="team">
  <div class="team-header">
    <h2>Meet the Team</h2>
    <p>We're designers, engineers, and dreamers building the future of web design.</p>
  </div>
  <div class="team-grid">
    <div class="team-card">
      <div class="team-avatar" style="background:linear-gradient(135deg,#6366f1,#8b5cf6)"></div>
      <h3>Alex Chen</h3>
      <span class="team-role">CEO &amp; Founder</span>
      <p class="team-bio">10 years building design tools at Figma and Adobe.</p>
    </div>
    <div class="team-card">
      <div class="team-avatar" style="background:linear-gradient(135deg,#ec4899,#f43f5e)"></div>
      <h3>Sarah Kim</h3>
      <span class="team-role">Head of Design</span>
      <p class="team-bio">Award-winning designer with 50+ shipped products.</p>
    </div>
    <div class="team-card">
      <div class="team-avatar" style="background:linear-gradient(135deg,#14b8a6,#06b6d4)"></div>
      <h3>Marcus Rivera</h3>
      <span class="team-role">Lead Engineer</span>
      <p class="team-bio">Distributed systems expert and open source contributor.</p>
    </div>
  </div>
</section>
```
```css
.team { padding:var(--space-4xl) var(--space-xl); }
.team-header { text-align:center; max-width:600px; margin:0 auto var(--space-4xl); }
.team-header h2 { font-size:var(--text-4xl); font-weight:800; margin-bottom:var(--space-md); }
.team-header p { color:var(--text-secondary); font-size:var(--text-lg); }
.team-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:var(--space-xl); max-width:900px; margin:0 auto; }
.team-card { text-align:center; padding:var(--space-xl); border-radius:var(--radius-xl); background:var(--surface-1); border:1px solid var(--border-subtle); transition:transform var(--normal) var(--ease-spring); }
.team-card:hover { transform:translateY(-4px); }
.team-avatar { width:80px; height:80px; border-radius:50%; margin:0 auto var(--space-md); }
.team-card h3 { font-size:var(--text-lg); margin-bottom:4px; }
.team-role { font-size:var(--text-xs); color:var(--accent); letter-spacing:1px; text-transform:uppercase; }
.team-bio { font-size:var(--text-sm); color:var(--text-secondary); margin-top:var(--space-md); line-height:1.5; }
```

---

## Problem Statement / Pain Point

✅ Best for: landing pages where you need to hook user by naming their pain.
⚠️ Avoid when: the problem is obvious or the product solves everything (generic).

```html
<section class="problem">
  <div class="problem-content">
    <span class="problem-badge">THE PROBLEM</span>
    <h2>Designing a website shouldn't take weeks.</h2>
    <p>Most tools make you choose between speed and quality. Templates look generic. Custom builds are expensive. You end up with either a cookie-cutter page you hate or a budget you blew past.</p>
  </div>
  <div class="problem-quote">
    <blockquote>"We spent 3 months and $40k on a website that looked dated the day it launched."</blockquote>
    <cite>— Design Director at a Series A startup</cite>
  </div>
</section>
```
```css
.problem { padding:var(--space-4xl) var(--space-xl); display:grid; grid-template-columns:1fr 1fr; gap:var(--space-4xl); max-width:1000px; margin:0 auto; align-items:center; }
.problem-badge { font-size:var(--text-xs); letter-spacing:2px; color:var(--accent); margin-bottom:var(--space-lg); display:block; }
.problem h2 { font-size:var(--text-4xl); font-weight:800; line-height:1.1; margin-bottom:var(--space-lg); }
.problem p { font-size:var(--text-base); color:var(--text-secondary); line-height:1.7; }
.problem-quote { background:var(--surface-1); border-left:3px solid var(--accent); padding:var(--space-xl); border-radius:var(--radius-lg); }
.problem-quote blockquote { font-size:var(--text-lg); font-style:italic; color:var(--text-primary); line-height:1.5; margin-bottom:var(--space-sm); }
.problem-quote cite { font-size:var(--text-sm); color:var(--text-secondary); font-style:normal; }
@media(max-width:768px) { .problem { grid-template-columns:1fr; } }
```

---

## Newsletter Signup

Grow your audience with a minimal signup block.

```html
<section class="newsletter">
  <div class="newsletter-card">
    <h2>Stay in the loop</h2>
    <p>Get the latest updates, tips, and design inspiration delivered to your inbox.</p>
    <form class="newsletter-form" onsubmit="event.preventDefault(); showToast('Subscribed!','success')">
      <input class="form-input" type="email" placeholder="you@example.com" required>
      <button class="btn btn--primary" type="submit">Subscribe</button>
    </form>
    <p class="newsletter-note">No spam. Unsubscribe anytime.</p>
  </div>
</section>
```
```css
.newsletter { padding:var(--space-4xl) var(--space-xl); }
.newsletter-card { max-width:520px; margin:0 auto; text-align:center; padding:var(--space-3xl); border-radius:var(--radius-2xl); background:var(--surface-1); border:1px solid var(--border-subtle); }
.newsletter-card h2 { font-size:var(--text-3xl); font-weight:800; margin-bottom:var(--space-sm); }
.newsletter-card p { color:var(--text-secondary); margin-bottom:var(--space-xl); }
.newsletter-form { display:flex; gap:var(--space-md); }
.newsletter-form .form-input { flex:1; }
.newsletter-note { font-size:var(--text-xs); color:var(--text-muted); margin-top:var(--space-md); }
@media(max-width:480px) { .newsletter-form { flex-direction:column; } }
```
