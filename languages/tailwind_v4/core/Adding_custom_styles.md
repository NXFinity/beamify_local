# Adding custom styles

Best practices for adding your own custom styles in Tailwind projects.

## Overview

Often the biggest challenge when working with a framework is figuring out what you're supposed to do when there's something you need that the framework doesn't handle for you.

Tailwind has been designed from the ground up to be extensible and customizable, so that no matter what you're building you never feel like you're fighting the framework.

This guide covers topics like customizing your design tokens, how to break out of those constraints when necessary, adding your own custom CSS, and extending the framework with plugins.

## Customizing your theme

If you want to change things like your color palette, spacing scale, typography scale, or breakpoints, add your customizations using the `@theme` directive in your CSS:

```css
@theme {
  --font-display: "Satoshi", "sans-serif";
  --breakpoint-3xl: 120rem;
  --color-avocado-100: oklch(0.99 0 0);
  --color-avocado-200: oklch(0.98 0.04 113.22);
  --color-avocado-300: oklch(0.94 0.11 115.03);
  --color-avocado-400: oklch(0.92 0.19 114.08);
  --color-avocado-500: oklch(0.84 0.18 117.33);
  --color-avocado-600: oklch(0.53 0.12 118.34);
  --ease-fluid: cubic-bezier(0.3, 0, 0, 1);
  --ease-snappy: cubic-bezier(0.2, 0, 0, 1);
  /* ... */
}
```

Learn more about customizing your theme in the theme variables documentation.

## Using arbitrary values

While you can usually build the bulk of a well-crafted design using a constrained set of design tokens, once in a while you need to break out of those constraints to get things pixel-perfect.

When you find yourself really needing something like `top: 117px` to get a background image in just the right spot, use Tailwind's square bracket notation to generate a class on the fly with any arbitrary value:

```html
<div class="top-[117px]">
  <!-- ... -->
</div>
```

This is basically like inline styles, with the major benefit that you can combine it with interactive modifiers like `hover` and responsive modifiers like `lg`:

```html
<div class="top-[117px] lg:top-[344px]">
  <!-- ... -->
</div>
```

This works for everything in the framework, including things like background colors, font sizes, pseudo-element content, and more:

```html
<div class="bg-[#bada55] text-[22px] before:content-['Festivus']">
  <!-- ... -->
</div>
```

### CSS Variables in arbitrary values

If you're referencing a CSS variable as an arbitrary value, you can use the custom property syntax:

```html
<div class="fill-(--my-brand-color) ...">
  <!-- ... -->
</div>
```

This is just a shorthand for `fill-[var(--my-brand-color)]` that adds the `var()` function for you automatically.

### Arbitrary properties

If you ever need to use a CSS property that Tailwind doesn't include a utility for out of the box, you can also use square bracket notation to write completely arbitrary CSS:

```html
<div class="[mask-type:luminance]">
  <!-- ... -->
</div>
```

This is _really_ like inline styles, but again with the benefit that you can use modifiers:

```html
<div class="[mask-type:luminance] hover:[mask-type:alpha]">
  <!-- ... -->
</div>
```

This can be useful for things like CSS variables as well, especially when they need to change under different conditions:

```html
<div class="[--scroll-offset:56px] lg:[--scroll-offset:44px]">
  <!-- ... -->
</div>
```

### Arbitrary variants

Arbitrary variants allow you to create on-the-fly selector modifications, similar to built-in pseudo-class variants like `hover:{utility}` or responsive variants like `md:{utility}` but using square bracket notation directly in your HTML:

```html
<ul role="list">
  {#each items as item}
    <li class="lg:[&:nth-child(-n+3)]:hover:underline">{item}</li>
  {/each}
</ul>
```

### Handling whitespace

When an arbitrary value needs to contain a space, use an underscore (`_`) instead and Tailwind will automatically convert it to a space at build-time:

```html
<div class="grid grid-cols-[1fr_500px_2fr]">
  <!-- ... -->
</div>
```

### Resolving ambiguities

Sometimes you need to be explicit about what kind of value you're providing when using arbitrary values. You can do this by adding a type prefix to the value:

```html
<!-- Size values -->
<div class="w-[length:100px]">...</div>
<div class="w-[percentage:50%]">...</div>

<!-- Color values -->
<div class="bg-[color:oklch(0.7_0.15_180)]">...</div>

<!-- URL values -->
<div class="bg-[url:/my-background.png]">...</div>
```

## Using custom CSS

### Adding base styles

Use the `@layer base` directive to add your own base styles, including things like custom fonts or resets:

```css
@layer base {
  @font-face {
    font-family: "Inter";
    src: url("/fonts/Inter.woff2") format("woff2");
  }

  h1 {
    @apply text-2xl font-bold;
  }
}
```

### Adding component classes

Use the `@layer components` directive to add your own component classes or override styles for any third-party components you're using:

```css
@layer components {
  .select2-dropdown {
    @apply rounded-lg shadow-md;
  }
}
```

### Using variants

Use the `@variant` directive to apply a Tailwind variant within custom CSS:

```css
.my-element {
  background: white;
  @variant dark {
    background: black;
  }
}
```

For multiple variants, use nesting:

```css
.my-element {
  background: white;
  @variant dark {
    @variant hover {
      background: black;
    }
  }
}
```

## Adding custom utilities

### Simple utilities

Use the `@utility` directive to add a custom utility to your project:

```css
@utility content-auto {
  content-visibility: auto;
}
```

You can now use this utility in your HTML with full variant support:

```html
<div class="content-auto hover:content-auto">
  <!-- ... -->
</div>
```

### Complex utilities

For more complex utilities that require multiple rules, use nesting:

```css
@utility scrollbar-hidden {
  &::-webkit-scrollbar {
    display: none;
  }
}
```

### Functional utilities

You can create functional utilities that accept an argument using the `--value()` function:

```css
@utility tab-* {
  tab-size: --value(--tab-size-*);
}
```

#### Matching theme values

Use `--value(--theme-key-*)` to match against theme keys:

```css
@theme {
  --tab-size-2: 2;
  --tab-size-4: 4;
  --tab-size-github: 8;
}

@utility tab-* {
  tab-size: --value(--tab-size-*);
}
```

#### Supporting bare values

Use `--value({type})` to support bare values of a specific type:

```css
@utility tab-* {
  tab-size: --value(integer);
}
```

#### Supporting arbitrary values

Use `--value([{type}])` to support arbitrary values:

```css
@utility tab-* {
  tab-size: --value([integer]);
}
```

## Adding custom variants

Create custom variants using the `@custom-variant` directive:

```css
@custom-variant theme-midnight {
  &:where([data-theme="midnight"] *) {
    @slot;
  }
}
```

You can use a shorthand syntax when nesting isn't required:

```css
@custom-variant theme-midnight (&:where([data-theme="midnight"] *));
```

For variants with multiple rules, use nesting:

```css
@custom-variant any-hover {
  @media (any-hover: hover) {
    &:hover {
      @slot;
    }
  }
}
``` 