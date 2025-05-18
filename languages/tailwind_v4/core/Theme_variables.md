# Theme variables

Using utility classes as an API for your design tokens.

## Overview

Tailwind is a framework for building custom designs, and different designs need different typography, colors, shadows, breakpoints, and more.

These low-level design decisions are often called _design tokens_, and in Tailwind projects you store those values in _theme variables_.

### What are theme variables?

Theme variables are special CSS variables defined using the `@theme` directive that influence which utility classes exist in your project.

For example, you can add a new color to your project by defining a theme variable like `--color-mint-500`:

```css
@import "tailwindcss";

@theme {
  --color-mint-500: oklch(0.72 0.11 178);
}
```

Now you can use utility classes like `bg-mint-500`, `text-mint-500`, or `fill-mint-500` in your HTML:

```html
<div class="bg-mint-500">
  <!-- ... -->
</div>
```

Tailwind also generates regular CSS variables for your theme variables so you can reference your design tokens in arbitrary values or inline styles:

```html
<div style="background-color: var(--color-mint-500)">
  <!-- ... -->
</div>
```

Learn more about how theme variables map to different utility classes in the theme variable namespaces documentation.

#### Why @theme instead of :root?

Theme variables aren't _just_ CSS variables — they also instruct Tailwind to create new utility classes that you can use in your HTML.

Since they do more than regular CSS variables, Tailwind uses special syntax so that defining theme variables is always explicit. Theme variables are also required to be defined top-level and not nested under other selectors or media queries, and using a special syntax makes it possible to enforce that.

Defining regular CSS variables with `:root` can still be useful in Tailwind projects when you want to define a variable that isn't meant to be connected to a utility class. Use `@theme` when you want a design token to map directly to a utility class, and use `:root` for defining regular CSS variables that shouldn't have corresponding utility classes.

### Relationship to utility classes

Some utility classes in Tailwind like `flex` and `object-cover` are static, and are always the same from project to project. But many others are driven by theme variables, and can be customized by adding new theme variables or modifying existing ones.

For example, the `text-{size}` utilities are driven by the `--text-*` theme variables:

```css
@import "tailwindcss";

@theme {
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  /* ... */
}
```

These theme variables control both the font size and line height of each text size utility:

```html
<p class="text-sm">This text will be 0.875rem with appropriate line-height.</p>
```

### Theme variable namespaces

Theme variables are organized into different namespaces that control which utility classes they generate. For example, variables in the `--color-*` namespace generate color-related utilities like `text-*`, `bg-*`, and `border-*`.

Here are some of the most commonly used namespaces and the utilities they generate:

| Namespace | Example | Generated utilities |
| --------- | ------- | ------------------ |
| `--color-*` | `--color-blue-500` | `text-*`, `bg-*`, `border-*`, etc. |
| `--spacing-*` | `--spacing-4` | `p-*`, `m-*`, `gap-*`, etc. |
| `--text-*` | `--text-sm` | `text-*` |
| `--font-*` | `--font-sans` | `font-*` |
| `--leading-*` | `--leading-normal` | `leading-*` |
| `--tracking-*` | `--tracking-wide` | `tracking-*` |
| `--radius-*` | `--radius-lg` | `rounded-*` |
| `--shadow-*` | `--shadow-lg` | `shadow-*` |

Learn more about all available theme variable namespaces in the theme variable reference.

### Default theme variables

Tailwind includes a comprehensive set of default theme variables that provide a great starting point for most projects. These variables control everything from colors and spacing to typography and shadows.

Here's a small sample of the default theme variables:

```css
@import "tailwindcss";

@theme {
  /* Colors */
  --color-blue-500: oklch(0.551 0.157 264.059);
  --color-red-500: oklch(0.625 0.224 27.562);
  --color-green-500: oklch(0.637 0.163 142.73);
  
  /* Spacing */
  --spacing-4: 1rem;
  --spacing-8: 2rem;
  --spacing-12: 3rem;
  
  /* Typography */
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  
  /* ... */
}
```

You can find a complete list of all default theme variables in the default theme reference.

## Customizing your theme

### Extending the default theme

To add new theme variables without removing the defaults, simply define your new variables:

```css
@import "tailwindcss";

@theme {
  --color-brand: oklch(0.7 0.15 180);
  --text-2xs: 0.625rem;
}
```

This will make `text-brand`, `bg-brand`, etc. available in addition to all of the default color utilities, and add a new `text-2xs` utility alongside the default text size utilities.

### Overriding the default theme

To override a default theme variable, redefine it with your desired value:

```css
@import "tailwindcss";

@theme {
  --color-blue-500: oklch(0.6 0.18 250);
  --text-lg: 1.25rem;
}
```

This will replace the default values for these variables while preserving all other default theme variables.

### Using a custom theme

To completely replace the default theme with your own custom theme, reset all theme variables using `--*: initial`, then define your own variables:

```css
@import "tailwindcss";

@theme {
  --*: initial;
  
  /* Define your custom theme */
  --color-primary: oklch(0.7 0.15 180);
  --color-secondary: oklch(0.6 0.12 220);
  --spacing-unit: 0.25rem;
  --text-small: 0.875rem;
  --text-regular: 1rem;
  --text-large: 1.25rem;
}
```

### Defining animation keyframes

Use the `@keyframes` rule inside your `@theme` block to define custom animations:

```css
@import "tailwindcss";

@theme {
  --animate-bounce: bounce 1s infinite;
  
  @keyframes bounce {
    0%, 100% {
      transform: translateY(-25%);
      animation-timing-function: cubic-bezier(0.8, 0, 1, 1);
    }
    50% {
      transform: none;
      animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
    }
  }
}
```

### Referencing other variables

You can reference other theme variables when defining new ones:

```css
@import "tailwindcss";

@theme {
  --spacing-1: 0.25rem;
  --spacing-2: calc(var(--spacing-1) * 2);
  --spacing-4: calc(var(--spacing-2) * 2);
}
```

### Generating all CSS variables

Theme variables are automatically available as regular CSS variables, but if you want to use them in a context where the `@theme` directive isn't supported, you can generate them explicitly:

```css
@import "tailwindcss";

:root {
  --color-blue-500: oklch(0.551 0.157 264.059);
  --spacing-4: 1rem;
  /* ... */
}
```

### Sharing across projects

For larger organizations, you can share theme variables across projects by creating a shared CSS file:

theme.css
```css
@theme {
  --color-brand: oklch(0.7 0.15 180);
  --spacing-unit: 0.25rem;
  /* ... */
}
```

Then import it in your project:

```css
@import "tailwindcss";
@import "./theme.css";
```

## Using your theme variables

### With custom CSS

Reference theme variables in your custom CSS using `var()`:

```css
.custom-element {
  color: var(--color-blue-500);
  margin: var(--spacing-4);
  font-size: var(--text-lg);
}
```

### With arbitrary values

Use theme variables in arbitrary values in your HTML:

```html
<div class="text-[var(--color-brand)] p-[var(--spacing-4)]">
  <!-- ... -->
</div>
```

### Referencing in JavaScript

Access theme variables in JavaScript using `getComputedStyle()`:

```js
const colors = getComputedStyle(document.documentElement);
const brandColor = colors.getPropertyValue('--color-brand');
``` 