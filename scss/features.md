# Features

Sass/SCSS lets you use features that don't exist in CSS like variables, nesting, mixins, inheritance and other goodies.

### Variables

Variables is a way to store information that you want to reuse throughout your stylesheet.

```css
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

### Mixins

...

### Extend/Inheritance

...

### Nesting

You can nest your CSS selectors that follows the same hierarchy of your HTML. But don't nest too much as it's hard to maintain and is generally considered bad practice.

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

### 

### Partials

You can create partial SCSS files that contains parts of code. These can be included in other SCSS files.

```css
_partial.scss
```

### Import

You can now import other files. Notice that `_` and `.scss` is not included.

```css
@import 'partial';
```

### Operators

...

