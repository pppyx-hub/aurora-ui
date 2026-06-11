# Aurora UI — Style Tokens

Each style completely overrides the base `:root` CSS variables. Pick ONE when the user specifies a style.

---

## 11.1 Neo-Brutalism

Philosophy: Raw honesty over polished perfection. High contrast, bold outlines, solid shadows, clashing colors.

```css
:root {
  --bg: #fffef0;
  --text-primary: #000000;
  --text-secondary: #333333;
  --accent-1: #ff6b6b; --accent-2: #4ecdc4; --accent-3: #ffe66d;
  --accent-4: #a8e6cf; --accent-5: #dda0dd;
  --border-thick: 3px solid #000000;
  --border-medium: 2px solid #000000;
  --border-radius: 0px;
  --shadow-brutal: 4px 4px 0px #000000;
  --shadow-brutal-hover: 6px 6px 0px #000000;
  --font-primary: 'Space Mono', 'Courier New', monospace;
  --font-display: 'Archivo Black', 'Arial Black', sans-serif;
  --line-height: 1.3;
  --transition-brutal: transform 100ms ease;
}
```

---

## 11.2 Memphis Style (1980s Post-Modern)

Playful chaos. Abstract geometric shapes, high-saturation color clashes, retro pattern backgrounds.

```css
:root {
  --bg-memphis: #ffffff;
  --memphis-black: #000000;
  --memphis-pink: #ff69b4; --memphis-yellow: #ffd700;
  --memphis-blue: #1e90ff; --memphis-orange: #ff8c00;
  --memphis-purple: #9b59b6; --memphis-cyan: #00ffff;
  --memphis-border: 2px solid var(--memphis-black);
  --font-primary: 'Helvetica Neue', 'Arial', sans-serif;
  --font-display: 'Georgia', 'Times New Roman', serif;
}
```

---

## 11.3 Wabi-Sabi / Zen

Beauty in imperfection. Muted earth tones, generous whitespace, organic shapes, paper textures.

```css
:root {
  --bg-wabi: #f5f0e8; --bg-wabi-dark: #e8e0d0;
  --text-wabi: #3a3530; --text-wabi-light: #7a7268;
  --accent-wabi: #8b9a6d; --accent-wabi-2: #b8860b; --accent-wabi-3: #a0522d;
  --border-wabi: 1px solid rgba(58, 53, 48, 0.15);
  --border-radius-wabi: 2px;
  --shadow-wabi: none;
  --font-primary: 'Noto Serif SC', 'Source Han Serif', 'Georgia', serif;
  --font-display: 'Noto Serif SC', 'Songti', 'Times New Roman', serif;
  --font-accent: 'Noto Sans SC', 'Source Han Sans', sans-serif;
  --transition-wabi: 600ms cubic-bezier(0.25, 0.1, 0.25, 1);
}
```

---

## 11.4 Editorial / Minimalism

High-fashion magazine. Huge serif typography, asymmetric grid, extreme scale contrast.

```css
:root {
  --bg-editorial: #ffffff;
  --text-editorial: #0a0a0a;
  --text-editorial-light: #666666;
  --accent-editorial: #c41e3a;
  --border-editorial: 1px solid #e0e0e0;
  --font-display: 'Playfair Display', 'Bodoni', 'Didot', 'Georgia', serif;
  --font-body: 'Inter', 'Helvetica Neue', sans-serif;
  --font-caption: 'Inter', sans-serif;
  --text-editorial-hero: clamp(48px, 12vw, 160px);
  --text-editorial-heading: clamp(28px, 5vw, 64px);
  --text-editorial-body: clamp(14px, 1.2vw, 18px);
  --text-editorial-caption: 11px;
  --space-editorial: 120px;
  --space-editorial-lg: 200px;
}
```

---

## 11.5 Y2K / Retro Computer

Digital optimism. Holographic gradients, pixel fonts, Windows 95 UI, scanlines, glitch effects.

```css
:root {
  --bg-y2k: #0a0a1a;
  --y2k-silver: #c0c0c0;
  --y2k-cyan: #00ffff; --y2k-magenta: #ff00ff; --y2k-purple: #8800ff;
  --y2k-pink: #ff69b4; --y2k-blue: #0066ff;
  --gradient-holo: linear-gradient(135deg, #ff69b4, #00ffff, #8800ff, #ffd700, #ff69b4);
  --win-border-outset: 2px solid;
  --win-border-outset-colors: #ffffff #808080 #808080 #ffffff;
  --win-border-inset: 2px solid;
  --win-border-inset-colors: #808080 #ffffff #ffffff #808080;
  --font-primary: 'Inter', sans-serif;
  --font-display: 'MS Sans Serif', 'Arial', sans-serif;
  --font-pixel: 'Press Start 2P', 'Courier New', monospace;
  --scanline: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.1) 2px, rgba(0,0,0,0.05) 4px);
}
```

---

## 11.6 Retro / Vintage

Warm nostalgia 1950s-70s. Mustard, rust, avocado, teal. Geometric patterns, vintage textures.

```css
:root {
  --bg-retro: #f4e8d1;
  --retro-mustard: #d4a843; --retro-rust: #c45e24;
  --retro-avocado: #8a9a3a; --retro-teal: #2c7a7b; --retro-brown: #5c3d2e;
  --retro-cream: #faf0e6;
  --font-display: 'DM Serif Display', 'Playfair Display', serif;
  --font-body: 'Space Grotesk', 'Inter', sans-serif;
  --pattern-halftone: radial-gradient(circle, var(--retro-brown) 0.5px, transparent 0.5px);
}
```

---

## 11.7 Claymorphism

Soft, pillowy shapes. High border-radius, double inner shadows, pastel colors.

```css
:root {
  --bg-clay: #f0e6d3;
  --clay-color-1: #ffd5a0; --clay-color-2: #a0d2db; --clay-color-3: #d2b4de;
  --clay-color-4: #b8e6b8; --clay-color-5: #f5c6a0;
  --clay-shadow: inset 6px 6px 12px rgba(161,136,118,0.3), inset -6px -6px 12px rgba(255,255,255,0.6), 8px 8px 24px rgba(161,136,118,0.25);
  --radius-clay: 32px;
  --font-primary: 'Nunito', 'Quicksand', 'Baloo 2', sans-serif;
}
```

---

## 11.9 Parallax Scenic

Immersion through layered depth. Multiple parallax layers, scroll-driven depth illusion, rich CSS gradients.

```css
/* Scene backgrounds — pure CSS gradients, zero images */
.scene-forest { background: linear-gradient(180deg, #0a2a1a 0%, #0d3d22 20%, #1a5c3a 45%, #2d8a5e 70%, #4ade80 100%); }
.scene-ocean { background: linear-gradient(180deg, #0c1922 0%, #1a3a5c 25%, #1e6f8f 50%, #48cae4 75%, #90e0ef 100%); }
.scene-desert { background: linear-gradient(180deg, #f4845f 0%, #f7a044 25%, #f9c784 50%, #f9e4b0 75%, #fef7ed 100%); }
.scene-aurora { background: linear-gradient(180deg, #0a0a1a 0%, #0d2818 30%, #1a5c3a 50%, #00ff88 70%, #00ffcc 100%); background-size: 100% 200%; animation: auroraBg 8s ease-in-out infinite; }

.parallax-container { perspective: 2px; height: 100vh; overflow-x: hidden; overflow-y: auto; }
.parallax-bg { transform: translateZ(-1px) scale(1.5); }
.parallax-mid { transform: translateZ(-0.5px) scale(1.2); }
.parallax-fg { transform: translateZ(0); }
```

---

## 11.10 Typography-Driven

Type IS the design. Massive typography, animated letter spacing, monochrome + one accent.

```css
:root {
  --bg-type: #0a0a0a;
  --text-type: #f5f5f5;
  --accent-type: #ff3300;
  --text-hero-typography: clamp(80px, 20vw, 300px);
  --text-typography-weight: 900;
  --text-typography-spacing: -0.04em;
  --font-display: 'Inter', sans-serif;
  --font-display-weight: 900;
}
```

---

## 11.11 Pure White Premium

Apple/Stripe/Linear quality. White backgrounds, crisp black text, micro-interactions, grid precision.

```css
:root {
  --bg-primary: #ffffff; --bg-secondary: #fafafa; --bg-tertiary: #f5f5f5; --bg-elevated: #ffffff;
  --text-primary: #0a0a0a; --text-secondary: #6b7280; --text-tertiary: #9ca3af; --text-inverse: #ffffff;
  --accent: #0066ff; --accent-hover: #0052cc; --accent-dim: rgba(0,102,255,0.08);
  --border-subtle: 1px solid #e5e7eb; --border-hover: 1px solid #d1d5db; --border-focus: 2px solid #0066ff;
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.04); --shadow-md: 0 4px 12px rgba(0,0,0,0.06);
  --shadow-lg: 0 8px 32px rgba(0,0,0,0.08); --shadow-xl: 0 16px 48px rgba(0,0,0,0.1);
  --space-xl: 40px; --space-2xl: 64px; --space-3xl: 96px; --space-4xl: 128px;
  --font-primary: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Inter', sans-serif;
  --font-secondary: 'SF Pro Text', 'Inter', sans-serif;
  --font-mono: 'SF Mono', 'JetBrains Mono', 'Fira Code', monospace;
  --text-hero: clamp(40px, 6vw, 72px); --text-heading: clamp(24px, 3vw, 40px);
  --text-body: clamp(16px, 1.2vw, 18px); --text-small: 14px;
  --weight-regular: 400; --weight-medium: 500; --weight-semibold: 600; --weight-bold: 700;
  --transition-fast: 150ms cubic-bezier(0.2, 0, 0.2, 1);
  --transition-normal: 250ms cubic-bezier(0.2, 0, 0.2, 1);
  --transition-slow: 400ms cubic-bezier(0.2, 0, 0.2, 1);
  --radius-sm: 6px; --radius-md: 10px; --radius-lg: 14px; --radius-xl: 20px;
}
```


## 11.8 Dark Glass / Dark Cinematic (Default)

Deep dark backgrounds, glowing accents, glass panels, animated mesh gradients. Subtle noise texture.

**This is the default theme** when no style is specified. Uses Section 1 base tokens from SKILL.md (Dark Cinematic with Deep blacks #050508, glowing accents, particle systems, full-screen immersive scenes).

```css
/* Uses Section 1 base tokens from SKILL.md. No override needed. */
```

## Quick Reference: Which Style to Use

| Product Type | Recommended | Avoid |
|--------------|-------------|-------|
| SaaS / Startup | Pure White Premium, Dark Cinematic | Memphis, Y2K |
| Corporate | Pure White Premium, Editorial | Brutalism, Y2K, Memphis |
| Portfolio (Designer) | Typography-Driven, Brutalism | Pure White |
| Portfolio (Photographer) | Editorial, Wabi-Sabi | Brutalism, Claymorphism |
| E-commerce | Pure White Premium, Brutalism | Y2K, Memphis |
| Music / Festival | Brutalism, Y2K, Memphis | Pure White, Wabi-Sabi |
| Food / Restaurant | Retro Vintage, Wabi-Sabi | Y2K, Brutalism |
| Travel | Parallax Scenic, Retro Vintage | Typography-Driven |
| Wellness | Wabi-Sabi, Claymorphism | Y2K, Brutalism |
| Tech / AI | Dark Cinematic, Typography-Driven | Wabi-Sabi, Retro |
| Fashion / Luxury | Editorial, Pure White Premium | Brutalism, Claymorphism |
| Education | Claymorphism, Pure White Premium | Y2K, Memphis |
| Creative Agency | Brutalism, Typography-Driven, Memphis | Pure White |
