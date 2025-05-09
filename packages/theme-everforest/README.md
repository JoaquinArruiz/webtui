# @webtui/theme-everforest

A port of the [Everforest](https://github.com/sainnhe/everforest) color palette to [WebTUI](https://github.com/webtui/webtui).

Provides additional variants for the listed components in the base WebTUI library and supports both dark (default) and light themes with multiple contrast levels.

## Installation

Install the theme with your preferred package manager

```bash
bun i @webtui/theme-everforest
npm i @webtui/theme-everforest
yarn add @webtui/theme-everforest
pnpm i @webtui/theme-everforest
```

Ensure you import the theme **after** all the other stylesheets from `@webtui/css` or the styles will not be applied.

```css
@layer base, utils, components;

@import "@webtui/css/base.css";
@import "@webtui/css/components/typography.css";
/* ... */

@import "@webtui/theme-everforest";
```

Set the `data-webtui-theme` attribute on the `<html>` tag or a container element.

```html
<html data-webtui-theme="everforest-dark-medium"></html>
```

To only apply the theme to a specific element:

```html
<html data-webtui-theme="dark">
  <!-- Example base theme -->
  <body>
    <div data-webtui-theme="everforest-light-hard">
      <!-- everforest light-hard styles applied here -->
    </div>
    <div data-webtui-theme="everforest-dark-soft">
      <!-- Gruvbox dark-soft styles applied here -->
    </div>
  </body>
</html>
```

## Variants

Supports dark and light modes, each with hard, medium, and soft contrast levels.

```html
<!-- Dark Variants -->
<html data-webtui-theme="everforest-dark-hard">
  <html data-webtui-theme="everforest-dark-medium">
    <!-- Default: everforest-dark or everforest -->
    <html data-webtui-theme="everforest-dark-soft">
      <!-- Light Variants -->
      <html data-webtui-theme="everforest-light-hard">
        <html data-webtui-theme="everforest-light-medium">
          <!-- Default: everforest-light -->
          <html data-webtui-theme="everforest-light-soft"></html>
        </html>
      </html>
    </html>
  </html>
</html>
```

## Components

Components affected/modified by the theme:

- [Typography](#typography)
- [Badge](#badge)
- [Button](#button)

### Typography

- Colors headings from `h1` to `h6` using `var(--gb-green)`.
- Inline `<a>` tags are underlined and colored `var(--gb-blue)`, changing to `var(--gb-aqua)` on hover.
- Inline `<code>` tags are colored `var(--gb-orange)`.

```html
<h1>Heading 1</h1>
<!-- ... -->
<h6>Heading 6</h6>

<p><a href="https://example.com">Link</a> <code>Inline Code</code></p>
```

### Badge

Adds additional variants to badges matching Everforest accent colors.

```html
<span is-="badge" variant-="gray">gray</span>
<span is-="badge" variant-="red">red</span>
<!-- ... -->
<span is-="badge" variant-="aqua">aqua</span>
<span is-="badge" variant-="orange">orange</span>
```

### Button

Adds additional variants to buttons matching Everforest accent colors.

```html
<button variant-="gray">gray</button>
<button variant-="red">red</button>
<!-- ... -->
<button variant-="aqua">aqua</button>
<button variant-="orange">orange</button>
```

## CSS Variables

Adds the following CSS variables within the `base` layer.

Raw color tokens and base semantic variables (`--background*`, `--foreground*`) are defined within theme-specific variant blocks. Dark mode uses bright accents, Light mode uses standard/faded accents.

```css
@layer base {
  /* Common Dark Variables & Semantic Mapping */
  [data-webtui-theme|="everforest-dark"] {
    /* ... raw dark vars ... */
    --gb-orange: #fe8019; /* Bright Orange */

    /* Semantic Mapping (Dark) */
    --background0: var(--gb-dark-bg0);
    --background1: var(--gb-dark-bg1);
    --background2: var(--gb-dark-bg2);
    --background3: var(--gb-dark-bg3);
    --foreground0: var(--gb-dark-fg1);
    --foreground1: var(--gb-dark-fg2);
    --foreground2: var(--gb-dark-fg3);
  }

  /* Dark Contrast Specific bg0 */
  [data-webtui-theme="everforest-dark-hard"] {
    --gb-dark-bg0: #1d2021;
  }
  [data-webtui-theme="everforest-dark-medium"] {
    --gb-dark-bg0: #282828;
  }
  [data-webtui-theme="everforest-dark-soft"] {
    --gb-dark-bg0: #32302f;
  }

  /* Common Light Variables & Semantic Mapping */
  [data-webtui-theme|="everforest-light"] {
    /* ... raw light vars ... */
    --gb-orange: #d65d0e; /* Standard/Faded Orange */

    /* Semantic Mapping (Light) */
    --background0: var(--gb-light-bg0);
    --background1: var(--gb-light-bg1);
    --background2: var(--gb-light-bg2);
    --background3: var(--gb-light-bg3);
    --foreground0: var(--gb-light-fg1);
    --foreground1: var(--gb-light-fg2);
    --foreground2: var(--gb-light-fg3);
  }

  /* Light Contrast Specific bg0 */
  [data-webtui-theme="everforest-light-hard"] {
    --gb-light-bg0: #f9f5d7;
  }
  [data-webtui-theme="everforest-light-medium"] {
    --gb-light-bg0: #fbf1c7;
  }
  [data-webtui-theme="everforest-light-soft"] {
    --gb-light-bg0: #f2e5bc;
  }
}
```
