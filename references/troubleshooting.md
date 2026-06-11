# Aurora UI — Troubleshooting Guide

When something doesn't look right, follow this diagnostic flow.

## 1. Page Shows Blank / White Screen

```
Step 1: Open browser DevTools (F12)
Step 2: Click Console tab
Step 3: Look for RED errors

Common fixes:
• "Uncaught SyntaxError" → Check for missing semicolons, unclosed brackets
• "X is not defined" → Variable name typo, or code runs before element exists
• "Cannot read property of null" → Element ID doesn't match HTML
→ Wrap in DOMContentLoaded: document.addEventListener('DOMContentLoaded', function() { ... });
```

## 2. CSS Not Applying

```
Check:
□ Styles are inside <style> tags (not .css files if single-file delivery)
□ Variable names match exactly (e.g., var(--accent) not var(--accent-color))
□ CSS selector matches HTML structure
□ No syntax error earlier in the CSS blocks the rest

Quick test: Add body { background: red !important; } — if page turns red, CSS is working.
```

## 3. Animations Not Working

```
Check:
□ prefers-reduced-motion is not active (testing in browser DevTools)
□ IntersectionObserver threshold is met (element is visible on screen)
□ GPU-accelerated properties only (transform, opacity)
□ No overflow: hidden on parent containers clipping the animation

Fix: Reduce animation complexity. Start with just opacity transition.
```

## 4. Mobile Layout Broken

```
Check:
□ Viewport meta tag present: <meta name="viewport" content="width=device-width, initial-scale=1.0">
□ No fixed-width elements (use max-width + width: 100%)
□ Media queries use min-width (mobile-first) not max-width (desktop-first)
□ Horizontal overflow: check for wide elements with overflow-x: hidden on body

Simulate: Open DevTools → Toggle Device Toolbar (Ctrl+Shift+M) → Select 375px width
```

## 5. Fonts Not Loading

```
Check:
□ font-display: swap is set (prevents invisible text)
□ Font URL is accessible (no CORS issues)
□ Fallback font is specified: font-family: 'Custom Font', -apple-system, sans-serif;

Fix: Use system fonts if custom fonts fail — they're always available.
```

## 6. CSP Blocking Resources (Console shows CSP errors)

```
Check CSP meta tag in <head>. Add missing sources:
• For images from external URL: add to img-src
• For fonts: add to font-src
• For API calls: add to connect-src

Example fix: <meta http-equiv="Content-Security-Policy" content="img-src 'self' https://example.com;">
```

## 7. JavaScript Not Running

```
Test: Add console.log('test') at the very end of <script> — check if it appears in console.

If NO:
  □ Script has syntax error (check DevTools Console for red text)
  □ Script runs before DOM is loaded — wrap in DOMContentLoaded
  □ Script is inside <script> tags, not <body> text

If YES but effects don't work:
  □ Check element selectors match actual HTML IDs/classes
  □ Check for JS errors in specific functions
```

## 8. "It looked right on my machine but not on the client's"

```
Likely causes:
• Different screen size → check responsive breakpoints
• Different browser → test Chrome, Edge, Firefox
• Different OS fonts → rely on system font stack, not custom fonts
• Browser zoom level → test at 100% zoom

Prevention: Always test in at least 2 browsers before delivery.
```

## 9. Client Says "I Don't Like It" — No Specifics

```
Ask structured questions — don't guess:

1. "What's the first thing that feels off to you?"
2. "Is it the colors, the layout, or the overall vibe?"
3. "Show me a website you DO like the style of"

Then use the 3-word technique: "Describe what you want in 3 words"
```

## 10. Recovery: Reset to Known-Good State

If you've made many changes and don't know what broke:

```
Option A: Open the starter template (templates/starter.html) and rebuild
Option B: Strip all animations — keep only base CSS + HTML structure
Option C: Remove scripts one by one to isolate the problem
```
