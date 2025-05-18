# box-decoration-break

Utilities for controlling how element fragments should be rendered across multiple lines, columns, or pages.

## Quick reference

| Class | Styles |
| --- | --- |
| `box-decoration-clone` | `box-decoration-break: clone` |
| `box-decoration-slice` | `box-decoration-break: slice` |

## Examples

### Basic example

Use the `box-decoration-slice` and `box-decoration-clone` utilities to control whether properties like background, border, border-image, box-shadow, clip-path, margin, and padding should be rendered as if the element were one continuous fragment, or distinct blocks:

```html
<span class="box-decoration-slice bg-linear-to-r from-indigo-600 to-pink-500 px-2 text-white ...">
  Hello<br />World
</span>

<span class="box-decoration-clone bg-linear-to-r from-indigo-600 to-pink-500 px-2 text-white ...">
  Hello<br />World
</span>
```

When using `box-decoration-slice` (the default), properties like backgrounds and borders are rendered as if the element was not broken by line breaks or column/page breaks.

With `box-decoration-clone`, each fragment of the element is rendered independently, with all background, border, and decorative properties applied to each box separately.

### Responsive design

Prefix a `box-decoration-break` utility with a breakpoint variant like `md:` to only apply the utility at medium screen sizes and above:

```html
<div class="box-decoration-clone md:box-decoration-slice ...">
  <!-- ... -->
</div>
```

Learn more about using variants in the variants documentation. 