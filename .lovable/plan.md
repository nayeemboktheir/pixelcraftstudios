

## Fix: Header and Hero Color Blending on Ebook Landing Page

**Problem**: The header and hero section both apply `var(--gradient-hero)` independently, causing the gradient to restart at the header/hero boundary — creating a visible color seam.

**Solution**: Wrap the header and hero in a single parent `div` that applies the gradient once, and make both the header and hero have transparent backgrounds. This way the gradient flows seamlessly across both sections.

### Changes in `src/pages/EbookLandingPage.tsx`

1. Wrap `<header>` and the hero `<section>` inside a single `<div style={{ background: "var(--gradient-hero)" }}>`.
2. Remove `style={{ background: "var(--gradient-hero)" }}` from both the `<header>` and the hero `<section>`.
3. Make header background transparent (just keep `sticky top-0 z-50` with `bg-transparent`). For sticky behavior, add a subtle `backdrop-blur` so it remains readable when scrolling over content.

This ensures one continuous gradient from top of header through the hero section bottom.

