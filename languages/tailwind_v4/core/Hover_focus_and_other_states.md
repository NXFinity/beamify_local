# Hover, focus, and other states

Using utilities to style elements on hover, focus, and more.

Every utility class in Tailwind can be applied _conditionally_ by adding a variant to the beginning of the class name that describes the condition you want to target.

For example, to apply the `bg-sky-700` class on hover, use the `hover:bg-sky-700` class:

```html
<button class="bg-sky-500 hover:bg-sky-700 ...">Save changes</button>
```

## How does this compare to traditional CSS?

When writing CSS the traditional way, a single class name would do different things based on the current state:

```css
.btn-primary {
  background-color: #0ea5e9;
}

.btn-primary:hover {
  background-color: #0369a1;
}
```

In Tailwind, rather than adding the styles for a hover state to an existing class, you add another class to the element that _only_ does something on hover:

```css
.bg-sky-500 {
  background-color: #0ea5e9;
}

.hover\:bg-sky-700:hover {
  background-color: #0369a1;
}
```

Notice how `hover:bg-sky-700` _only_ defines styles for the `:hover` state? It does nothing by default, but as soon as you hover over an element with that class, the background color will change to `sky-700`.

This is what we mean when we say a utility class can be applied _conditionally_ — by using variants you can control exactly how your design behaves in different states, without ever leaving your HTML.

Tailwind includes variants for just about everything you'll ever need, including:

* Pseudo-classes, like `:hover`, `:focus`, `:first-child`, and `:required`
* Pseudo-elements, like `::before`, `::after`, `::placeholder`, and `::selection`
* Media and feature queries, like responsive breakpoints, dark mode, and `prefers-reduced-motion`
* Attribute selectors, like `[dir="rtl"]` and `[open]`
* Child selectors, like `& > *` and `& *`

These variants can even be stacked to target more specific situations, for example changing the background color in dark mode, at the medium breakpoint, on hover:

```html
<button class="dark:md:hover:bg-fuchsia-600 ...">Save changes</button>
```

## Pseudo-classes

### :hover, :focus, and :active

Style elements on hover, focus, and active using the `hover`, `focus`, and `active` variants:

```html
<button class="bg-violet-500 hover:bg-violet-600 focus:outline-2 focus:outline-offset-2 focus:outline-violet-500 active:bg-violet-700 ...">
  Save changes
</button>
```

Tailwind also includes variants for other interactive states like `:visited`, `:focus-within`, `:focus-visible`, and more.

### :first, :last, :odd, and :even

Style an element when it is the first-child or last-child using the `first` and `last` variants:

```html
<ul role="list">
  {#each people as person}
    <!-- Remove top/bottom padding when first/last child -->
    <li class="flex py-4 first:pt-0 last:pb-0">
      <img class="h-10 w-10 rounded-full" src={person.imageUrl} alt="" />
      <div class="ml-3 overflow-hidden">
        <p class="text-sm font-medium text-gray-900 dark:text-white">{person.name}</p>
        <p class="truncate text-sm text-gray-500 dark:text-gray-400">{person.email}</p>
      </div>
    </li>
  {/each}
</ul>
```

### :first-of-type

Style an element if it's the first child of its type using the `first-of-type` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="ml-2 first-of-type:ml-6 ...">
      <!-- ... -->
    </a>
  {/each}
</nav>
```

### :last-of-type

Style an element if it's the last child of its type using the `last-of-type` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mr-2 last-of-type:mr-6 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :only-of-type

Style an element if it's the only child of its type using the `only-of-type` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mx-2 only-of-type:mx-6 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :nth-child()

Style an element at a specific position using the `nth` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mx-2 nth-3:mx-6 nth-[3n+1]:mx-7 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :nth-last-child()

Style an element at a specific position from the end using the `nth-last` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mx-2 nth-last-3:mx-6 nth-last-[3n+1]:mx-7 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :nth-of-type()

Style an element at a specific position, of the same type using the `nth-of-type` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mx-2 nth-of-type-3:mx-6 nth-of-type-[3n+1]:mx-7 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :nth-last-of-type()

Style an element at a specific position from the end, of the same type using the `nth-last-of-type` variant:

```html
<nav>
  <img src="/logo.svg" alt="Vandelay Industries" />
  {#each links as link}
    <a href="#" class="mx-2 nth-last-of-type-3:mx-6 nth-last-of-type-[3n+1]:mx-7 ...">
      <!-- ... -->
    </a>
  {/each}
  <button>More</button>
</nav>
```

### :empty

Style an element if it has no content using the `empty` variant:

```html
<ul>
  {#each people as person}
    <li class="empty:hidden ...">{person.hobby}</li>
  {/each}
</ul>
```

### :disabled

Style an input when it's disabled using the `disabled` variant:

```html
<input class="disabled:opacity-75 ..." />
```

### :enabled

Style an input when it's enabled using the `enabled` variant, most helpful when you only want to apply another style when an element is not disabled:

```html
<input class="enabled:hover:border-gray-400 disabled:opacity-75 ..." />
```

### :checked

Style a checkbox or radio button when it's checked using the `checked` variant:

```html
<input type="checkbox" class="appearance-none checked:bg-blue-500 ..." />
```

### :indeterminate

Style a checkbox or radio button in an indeterminate state using the `indeterminate` variant:

```html
<input type="checkbox" class="appearance-none indeterminate:bg-gray-300 ..." />
```

### :default

Style an option, checkbox or radio button that was the default value when the page initially loaded using the `default` variant:

```html
<input type="checkbox" class="default:outline-2 ..." />
```

### :optional

Style an input when it's optional using the `optional` variant:

```html
<input class="border optional:border-red-500 ..." />
```

### :required

Style an input when it's required using the `required` variant:

```html
<input required class="border required:border-red-500 ..." />
```

### :valid

Style an input when it's valid using the `valid` variant:

```html
<input required class="border valid:border-green-500 ..." />
```

### :invalid

Style an input when it's invalid using the `invalid` variant:

```html
<input required class="border invalid:border-red-500 ..." />
```

### :user-valid

Style an input when it's valid and the user has interacted with it, using the `user-valid` variant:

```html
<input required class="border user-valid:border-green-500" />
```

### :user-invalid

Style an input when it's invalid and the user has interacted with it, using the `user-invalid` variant:

```html
<input required class="border user-invalid:border-red-500" />
```

### :in-range

Style an input when its value is within a specified range limit using the `in-range` variant:

```html
<input min="1" max="5" class="in-range:border-green-500 ..." />
```

### :out-of-range

Style an input when its value is outside of a specified range limit using the `out-of-range` variant:

```html
<input min="1" max="5" class="out-of-range:border-red-500 ..." />
```

### :placeholder-shown

Style an input when the placeholder is shown using the `placeholder-shown` variant:

```html
<input class="placeholder-shown:border-gray-500 ..." placeholder="you@example.com" />
```

### :details-content

Style the content of a `<details>` element using the `details-content` variant:

```html
<details class="details-content:bg-gray-100 ...">
  <summary>Details</summary>
  This is a secret.
</details>
```

### :autofill

Style an input when it has been autofilled by the browser using the `autofill` variant:

```html
<input class="autofill:bg-yellow-200 ..." />
```

### :read-only

Style an input when it is read-only using the `read-only` variant:

```html
<input class="read-only:bg-gray-100 ..." />
``` 