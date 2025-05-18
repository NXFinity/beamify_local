# Colors

Using and customizing the color palette in Tailwind CSS projects.

## Overview

Tailwind CSS includes a vast, beautiful color palette out of the box, carefully crafted by expert designers and suitable for a wide range of different design styles.

Every color in the default palette includes 11 steps, with 50 being the lightest, and 950 being the darkest. The entire color palette is available across all color-related utilities, including background color, border color, fill, caret color, and many more.

## Working with colors

### Using color utilities

Use color utilities like `bg-white`, `border-pink-300`, and `text-gray-950` to set the different color properties of elements in your design:

```html
<div class="flex items-center gap-4 rounded-lg bg-white p-6 shadow-md outline outline-black/5 dark:bg-gray-800">
  <span class="inline-flex shrink-0 rounded-full border border-pink-300 bg-pink-100 p-2 dark:border-pink-300/10 dark:bg-pink-400/10">
    <svg class="size-6 stroke-pink-700 dark:stroke-pink-500"><!-- ... --></svg>
  </span>
  <div>
    <p class="text-gray-700 dark:text-gray-400">
      <span class="font-medium text-gray-950 dark:text-white">Tom Watson</span> mentioned you in
      <span class="font-medium text-gray-950 dark:text-white">Logo redesign</span>
    </p>
    <p class="text-gray-500 dark:text-gray-500">9:37am</p>
  </div>
</div>
```

### Adjusting opacity

Control the opacity of any color utility by adding a slash followed by the opacity value:

```html
<div class="bg-blue-500/50">
  <!-- Background will be blue with 50% opacity -->
</div>
```

### Targeting dark mode

Add the `dark:` prefix to any color utility to apply it only when dark mode is active:

```html
<div class="bg-white dark:bg-gray-800">
  <p class="text-gray-900 dark:text-white">
    <!-- ... -->
  </p>
</div>
```

### Referencing in CSS

Access color values directly in your CSS using theme variables:

```css
.custom-element {
  background-color: var(--color-blue-500);
  border-color: var(--color-gray-200);
}
```

## Customizing your colors

### Overriding default colors

To override a default color, redefine its theme variables:

```css
@import "tailwindcss";

@theme {
  --color-blue-500: oklch(0.6 0.18 250);
  --color-red-500: oklch(0.65 0.25 30);
}
```

### Disabling default colors

To disable the default color palette, reset all color variables:

```css
@import "tailwindcss";

@theme {
  --color-*: initial;
}
```

### Using a custom palette

Define your own custom color palette:

```css
@import "tailwindcss";

@theme {
  --color-primary: oklch(0.7 0.15 180);
  --color-secondary: oklch(0.6 0.12 220);
  --color-accent: oklch(0.65 0.3 30);
}
```

### Referencing other variables

You can reference other color variables when defining new ones:

```css
@import "tailwindcss";

@theme {
  --color-primary-light: color-mix(in oklch, var(--color-primary), white 20%);
  --color-primary-dark: color-mix(in oklch, var(--color-primary), black 20%);
}
```

## Default color palette reference

The default color palette includes these color scales:

- Red (`--color-red-*`)
- Orange (`--color-orange-*`)
- Amber (`--color-amber-*`)
- Yellow (`--color-yellow-*`)
- Lime (`--color-lime-*`)
- Green (`--color-green-*`)
- Emerald (`--color-emerald-*`)
- Teal (`--color-teal-*`)
- Cyan (`--color-cyan-*`)
- Sky (`--color-sky-*`)
- Blue (`--color-blue-*`)
- Indigo (`--color-indigo-*`)
- Violet (`--color-violet-*`)
- Purple (`--color-purple-*`)
- Fuchsia (`--color-fuchsia-*`)
- Pink (`--color-pink-*`)
- Rose (`--color-rose-*`)
- Slate (`--color-slate-*`)
- Gray (`--color-gray-*`)
- Zinc (`--color-zinc-*`)
- Neutral (`--color-neutral-*`)
- Stone (`--color-stone-*`)

Each color includes shades from 50 to 950:

```css
@theme {
  --color-blue-50: oklch(0.971 0.025 264.053);
  --color-blue-100: oklch(0.94 0.05 264.054);
  --color-blue-200: oklch(0.89 0.075 264.055);
  --color-blue-300: oklch(0.82 0.11 264.056);
  --color-blue-400: oklch(0.7 0.15 264.057);
  --color-blue-500: oklch(0.551 0.157 264.059);
  --color-blue-600: oklch(0.48 0.145 264.06);
  --color-blue-700: oklch(0.4 0.13 264.061);
  --color-blue-800: oklch(0.3 0.11 264.062);
  --color-blue-900: oklch(0.25 0.09 264.063);
  --color-blue-950: oklch(0.2 0.07 264.064);
}
```

Additionally, there are two special colors:

```css
@theme {
  --color-black: #000;
  --color-white: #fff;
}
``` 