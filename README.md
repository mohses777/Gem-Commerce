# Gum-Commerce

Static landing page built with HTML + Tailwind CSS (CDN) and local SVG assets.

## Run locally

1. Open `index.html` in your browser.
2. No build step is required (Tailwind is loaded via CDN).

## Project structure

- `index.html` - Page markup and Tailwind config (via `tailwind.config` in a script tag)
- `tailwind.config.js` - Tailwind config file (useful if you later move to a build pipeline)
- `assets/` - SVG icons and images used on the page

## Performance optimizations

### Lazy loading strategy
- **Hero image** (`hero.svg`): Uses `loading="eager"` + `fetchpriority="high"` for immediate loading (above-the-fold)
- **All other images**: Use `loading="lazy"` to defer loading until they're near the viewport
  - Small icons (food, premium, fresh, vet-developer, shield, payment logos)
  - Large images (dog-image, dog-eating, dog-food)

### Layout shift prevention
- All main images include explicit `width` and `height` attributes
- This reserves space before images load, preventing Cumulative Layout Shift (CLS)
- Improves Core Web Vitals score

### Image decoding
- All images use `decoding="async"` to prevent blocking the main thread during image decode

## Notes

- Uses the **Inter** font from Google Fonts.
- Uses a custom Tailwind theme (colors like `heading`, `text`, `primary`).
- All images include `alt` attributes for accessibility.
