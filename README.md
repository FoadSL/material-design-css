# material-design-css

A **configurable Material Design 3 (MD3) design token library** for TailwindCSS v4. Pure CSS -- no JavaScript, no PostCSS plugins, no build steps.

Provides design tokens, utility classes, and CSS custom properties that implement the [Material Design 3](https://m3.material.io/) specification. Components are built separately by consuming teams -- this library provides the foundation they build on.

## Features

- **Full MD3 Token Coverage** -- Color, Typography, Shape, Motion, Elevation, State Layer, and Palette
- **Three-Tier Configuration** -- `--md-config-*` (user) -> `--md-sys-*` (system) -> Tailwind theme variables
- **Dark Mode** -- Automatic via `color-scheme` and CSS `light-dark()`, manual via `.light`/`.dark` classes
- **RTL/LTR Ready** -- Built-in support for Persian, Arabic, and English with per-language font overrides
- **Multi-Brand Theming** -- Override any token at any level for different products or clients
- **Prebuild Color Schemes** -- Drop-in palettes (blue, green, pink, yellow, light-green)
- **Production Hardened** -- CSS reset, reduced-motion support, `@property` registration, focus-visible states
- **Zero Dependencies** -- TailwindCSS v4 is an optional peer dependency

## Installation

```bash
npm install material-design-css
```

## Quick Start

### With TailwindCSS v4

Import the library in your main CSS file:

```css
@import "tailwindcss";
@import "material-design-css";
```

That's it. You now have access to all MD3 tokens as Tailwind utilities:

```html
<button class="bg-primary text-on-primary rounded-medium px-6 py-3 shadow-elevation-1
               transition-button state-layer-on-primary body-medium">
  Get Started
</button>
```

### Without TailwindCSS

Import the preset and individual utility files:

```js
import 'material-design-css/preset.css';
import 'material-design-css/color/bg-utilities.css';
import 'material-design-css/color/text-utilities.css';
import 'material-design-css/shape/shape-utilities.css';
import 'material-design-css/typography/typography-utilities.css';
import 'material-design-css/elevation/elevation-utilities.css';
import 'material-design-css/motion/transition-utilities.css';
import 'material-design-css/state-layer/state-layer-utilities.css';
```

## Token Systems

### Color

55 MD3 color tokens with automatic light/dark mode resolution.

| Tailwind Class | CSS Variable | Description |
|---|---|---|
| `bg-primary` | `--color-primary` | Primary brand color |
| `text-on-primary` | `--color-on-primary` | Text on primary surfaces |
| `bg-surface` | `--color-surface` | Default background |
| `text-on-surface` | `--color-on-surface` | Default text color |
| `border-outline` | `--color-outline` | Default border color |
| `bg-error` | `--color-error` | Error state color |
| `bg-primary-container` | `--color-primary-container` | Container variant |

Plus: secondary, tertiary, error, info, success, warning, surface variants, inverse colors, fixed colors, custom hues, and more.

### Tonal Palette

Full MD3 tonal palette with 13 tonal values (0-100) for each color role:

```html
<div class="bg-primary-90 text-primary-10">Light primary surface</div>
<div class="bg-secondary-40 text-secondary-100">Dark secondary</div>
```

### Typography

All 15 MD3 type roles across 5 scales (Display, Headline, Title, Body, Label) x 3 sizes (Large, Medium, Small):

```html
<!-- Shorthand utility (sets all type properties at once) -->
<h1 class="display-large">Page Title</h1>
<p class="body-medium">Body text</p>
<span class="label-small">Caption</span>

<!-- Or use individual Tailwind utilities -->
<h1 class="font-display-large text-display-large tracking-display-large leading-display-large">
  Page Title
</h1>
```

### Shape (Border Radius)

MD3 shape scale from `none` to `full`:

```html
<div class="rounded-none">0px</div>
<div class="rounded-extra-small">4px</div>
<div class="rounded-small">8px</div>
<div class="rounded-medium">12px</div>
<div class="rounded-large">16px</div>
<div class="rounded-extra-large">28px</div>
<div class="rounded-full">9999px</div>
```

### Motion (Easing & Duration)

MD3 easing curves (standard, emphasized, expressive) and duration tokens, plus semantic transition utilities:

```html
<!-- Semantic transitions (property-specific, no transition-property: all) -->
<button class="transition-button">Button with bg, color, shadow transitions</button>
<div class="transition-interactive">Hover/focus transitions</div>
<div class="transition-motion">Transform + opacity transitions</div>

<!-- Individual motion tokens -->
<div class="ease-emphasized duration-[var(--duration-medium1)]">Custom transition</div>
```

### Elevation

MD3 6-level elevation (shadow) and 5-level glow system:

```html
<!-- Standard shadows (for light surfaces) -->
<div class="shadow-elevation-0">Flat</div>
<div class="shadow-elevation-1">Subtle shadow</div>
<div class="shadow-elevation-3">Card shadow</div>
<div class="shadow-elevation-5">Dialog shadow</div>

<!-- Glow variant (for dark surfaces or accent elements) -->
<div class="shadow-glow-2">Soft glow</div>
<div class="shadow-glow-5">Strong glow</div>

<!-- With utility classes -->
<div class="elevation-2">Elevation level 2</div>
<div class="glow-3">Glow level 3</div>
```

### State Layer

MD3-compliant interactive state overlays with automatic hover, focus, press, and drag feedback:

```html
<button class="state-layer-on-primary bg-primary text-on-primary">
  <!-- Automatic: hover 8%, focus-visible 10%, press 10%, drag 16% -->
</button>

<!-- High emphasis variant (stronger feedback) -->
<button class="state-layer-high state-layer-primary">
  Important action
</button>

<!-- Disabled states -->
<button class="state-disabled" disabled>Can't click</button>
```

### Z-Index

13-level standardized z-index scale to prevent z-index wars:

```html
<header class="z-sticky">Sticky header (300)</header>
<div class="z-overlay">Overlay (500)</div>
<div class="z-modal">Modal dialog (700)</div>
<div class="z-tooltip">Tooltip (950)</div>
```

| Token | Value | Use Case |
|---|---|---|
| `z-hide` | -1 | Hidden elements |
| `z-base` | 0 | Default |
| `z-masked` | 100 | Behind masks |
| `z-mask` | 200 | Masks/backdrops |
| `z-sticky` | 300 | Sticky headers |
| `z-fixed` | 400 | Fixed elements |
| `z-overlay` | 500 | Overlays |
| `z-loader` | 600 | Loading states |
| `z-modal` | 700 | Modals/dialogs |
| `z-dropdown` | 800 | Dropdowns/menus |
| `z-notification` | 900 | Toasts/snackbars |
| `z-tooltip` | 950 | Tooltips |
| `z-above-all` | 1000000 | Emergency override |

### Spacing

Overrides Tailwind's spacing base to MD3's 4px grid unit. All native spacing utilities align automatically:

```html
<div class="p-1">4px padding</div>
<div class="p-2">8px padding</div>
<div class="p-4">16px padding</div>
<div class="gap-6">24px gap</div>
<div class="m-10">40px margin</div>
```

### Stroke (Border Width)

5-level border-width scale:

```html
<div class="border-stroke-narrow">1px border</div>
<div class="border-stroke-medium">2px border</div>
<div class="border-stroke-thick">4px border</div>
<div class="border-t-stroke-heavy">10px top border</div>
```

### Component Sizes

9-level component sizing scale (16px - 64px) for icons, avatars, buttons, and touch targets:

```html
<img class="size-component-x-small" src="avatar.png" />   <!-- 24x24 -->
<img class="size-component-medium" src="avatar.png" />     <!-- 32x32 -->
<img class="size-component-x-large" src="avatar.png" />    <!-- 48x48 -->
<button class="h-component-large w-component-3x-large">Wide button</button>
```

## Configuration

### Customizing Tokens

Override any token by setting `--md-config-*` variables before the import:

```css
@import "tailwindcss";

@layer theme {
  :root {
    /* Custom brand colors */
    --md-config-color-primary-light: #6750a4;
    --md-config-color-primary-dark: #d0bcff;

    /* Custom typography */
    --md-config-typeface-brand: "Inter", sans-serif;
    --md-config-typeface-plain: "Inter", sans-serif;

    /* Custom shape */
    --md-config-shape-corner-value-medium: 8px;

    /* Custom spacing base */
    --md-config-spacing-unit: 8px;
  }
}

@import "material-design-css";
```

### RTL Support (Persian / Arabic)

The library includes built-in RTL support with per-language font fallback chains:

```html
<html lang="fa" dir="rtl">
```

```css
:root {
  /* Shared font for all RTL languages */
  --md-config-typeface-brand-rtl: "Yekan Bakh", sans-serif;
  --md-config-typeface-plain-rtl: "Vazirmatn", sans-serif;
}
```

Or configure fonts per language:

```css
:root {
  /* Persian-specific fonts */
  --md-config-typeface-brand-fa: "Yekan Bakh", sans-serif;
  --md-config-typeface-plain-fa: "Vazirmatn", sans-serif;

  /* Arabic-specific fonts */
  --md-config-typeface-brand-ar: "Noto Sans Arabic", sans-serif;
  --md-config-typeface-plain-ar: "Noto Sans Arabic", sans-serif;
}
```

Fallback chain: per-language (`-fa`/`-ar`) -> shared RTL (`-rtl`) -> global -> `"Roboto"`.

Tailwind's `rtl:` / `ltr:` modifiers and logical properties (`ms-*`, `me-*`, `ps-*`, `pe-*`) handle directional layout.

### Dark Mode

Dark mode works automatically via OS preference (`prefers-color-scheme`). Override manually:

```html
<!-- OS preference (default) -->
<html>

<!-- Force light mode -->
<html class="light">

<!-- Force dark mode -->
<html class="dark">
```

### Prebuild Color Schemes

Drop-in color palettes to replace the default colors:

```css
@import "tailwindcss";
@import "material-design-css";
@import "material-design-css/prebuild-color/blue.css";
```

Available presets: `blue`, `green`, `pink`, `yellow`, `light-green`.

### Multi-Brand Theming

Scope tokens to a class or attribute for nested brand themes:

```css
.brand-a {
  --md-config-color-primary-light: #6750a4;
  --md-config-color-primary-dark: #d0bcff;
}

.brand-b {
  --md-config-color-primary-light: #006d3b;
  --md-config-color-primary-dark: #7ddb9a;
}
```

```html
<div class="brand-a">
  <button class="bg-primary text-on-primary">Brand A button</button>
</div>
<div class="brand-b">
  <button class="bg-primary text-on-primary">Brand B button</button>
</div>
```

## Selective Imports

Import only the modules you need:

```css
@import "tailwindcss";

/* Required: config (defaults + resolver + @property registration) */
@import "material-design-css/config";

/* Pick what you need */
@import "material-design-css/color/tailwind-theme.css";
@import "material-design-css/typography/tailwind-theme.css";
@import "material-design-css/shape/tailwind-theme.css";
@import "material-design-css/motion/tailwind-theme.css";
@import "material-design-css/elevation/tailwind-theme.css";
@import "material-design-css/state-layer/tailwind-theme.css";
@import "material-design-css/z-index/tailwind-theme.css";
@import "material-design-css/spacing/tailwind-theme.css";
@import "material-design-css/stroke/tailwind-theme.css";
@import "material-design-css/size/tailwind-theme.css";
@import "material-design-css/palette/tailwind-theme.css";
```

## Architecture

### Three-Tier Token System

```
User Overrides          System Defaults           Tailwind Theme
--md-config-*    -->    --md-sys-*          -->   --color-*, --radius-*, etc.
(your brand)            (with fallbacks)          (generates utilities)
```

### Layer Ordering

```css
@layer theme, md-config, md-resolver, md-prebuild, base, components, utilities;
```

| Layer | Purpose |
|---|---|
| `theme` | Tailwind's `@theme` declarations |
| `md-config` | Token defaults (`config/defaults.css`) |
| `md-resolver` | Light/dark mode resolution (`config/resolver.css`) |
| `md-prebuild` | Prebuild color scheme overrides |
| `base` | Reset, RTL defaults, reduced-motion |
| `components` | Component styles (your code) |
| `utilities` | Utility classes |

### File Structure

```
material-design-css/
├── index.css                  # Main entry point (imports everything)
├── preset.css                 # Non-Tailwind preset (config + variables)
├── config/
│   ├── index.css              # Config entry point
│   ├── defaults.css           # All token defaults (md-config layer)
│   ├── resolver.css           # light-dark() color resolution (md-resolver layer)
│   └── property-registration.css  # @property for smooth animations
├── color/
│   ├── tailwind-theme.css     # Color tokens → Tailwind @theme
│   ├── bg-utilities.css       # .bg-primary, .bg-surface, etc.
│   ├── text-utilities.css     # .text-on-primary, .text-on-surface, etc.
│   └── classic-utilities.css  # Non-Tailwind color classes (optional)
├── palette/
│   ├── tailwind-theme.css     # Tonal palette tokens → @theme
│   ├── bg-utilities.css       # .bg-primary-90, .bg-secondary-40, etc.
│   └── text-utilities.css     # .text-primary-10, .text-neutral-80, etc.
├── typography/
│   ├── tailwind-theme.css     # Font/size/tracking/leading tokens → @theme
│   ├── tailwind-utilities.css # Composite type scale (Tailwind @utility)
│   └── typography-utilities.css  # Shorthand classes (.display-large, etc.)
├── shape/
│   ├── tailwind-theme.css     # Border-radius tokens → @theme
│   └── shape-utilities.css    # .shape-none, .shape-medium, etc.
├── motion/
│   ├── tailwind-theme.css     # Easing + duration tokens → @theme
│   ├── transition-utilities.css  # Semantic transition classes
│   └── animation-utilities.css   # Semantic animation classes
├── elevation/
│   ├── tailwind-theme.css     # Shadow + glow tokens → @theme
│   └── elevation-utilities.css   # .elevation-*, .glow-* classes
├── state-layer/
│   ├── tailwind-theme.css     # State opacity tokens → @theme
│   └── state-layer-utilities.css # Interactive state layer classes
├── z-index/
│   └── tailwind-theme.css     # Z-index tokens → @theme
├── spacing/
│   └── tailwind-theme.css     # Spacing base override (4px grid)
├── stroke/
│   └── tailwind-theme.css     # Border-width tokens → @theme
├── size/
│   └── tailwind-theme.css     # Component size tokens → @theme
├── utilities/
│   ├── scrollbar.css          # scrollbar-thin, scrollbar-hidden, scrollbar-auto
│   └── content-visibility.css # content-auto, content-hidden (performance)
└── prebuild-color/
    ├── blue.css
    ├── green.css
    ├── pink.css
    ├── yellow.css
    └── light-green.css
```

## Production Features

### Accessibility

- **Reduced Motion** -- Automatically disables animations and transitions when the user has `prefers-reduced-motion: reduce` enabled (WCAG 2.1 SC 2.3.3).
- **Focus Visible** -- All focus states use `:focus-visible` (keyboard only), preventing unwanted outlines on mouse clicks.
- **Selection Colors** -- Text selection uses MD3 primary container colors.

### CSS Reset

Extends Tailwind's preflight with production-hardened rules:
- Dialog font normalization
- Autofill styling with design system colors
- Number input spinner removal
- Smooth scrolling (focus-within)
- Media element block display
- Label cursor inheritance

### Performance

- **`@property` Registration** -- State layer opacity properties are registered with the browser for smooth animated transitions (no discrete jumps).
- **Content Visibility Utilities** -- `content-auto`, `content-hidden`, `content-visible` for lazy-rendering off-screen sections.
- **Semantic Transitions** -- All transition utilities use explicit property lists (no `transition-property: all`).

### Scrollbar Styling

```html
<div class="scrollbar-thin">Thin scrollbar with MD3 colors</div>
<div class="scrollbar-hidden">Hidden scrollbar (content still scrollable)</div>
<div class="scrollbar-auto">Browser default scrollbar</div>
```

## Browser Support

- Chrome/Edge 85+
- Firefox 128+
- Safari 15.4+

Key CSS features used: `light-dark()`, `@property`, `@layer`, `content-visibility`, `:focus-visible`, `color-scheme`.

All features degrade gracefully in older browsers.

## Acknowledgments

This project was originally inspired by and built upon [`@sandlada/material-design-css`](https://github.com/sandlada/material-design-css), an open-source CSS library for Material Design Tokens with TailwindCSS v4 support. We extended it with a configurable three-tier token architecture, production-hardened base styles, additional token systems, and comprehensive dark mode / RTL / accessibility support.

## License

[MIT](LICENSE)
