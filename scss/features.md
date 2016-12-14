# Features

Sass/SCSS lets you use features that don't exist in CSS like variables, nesting, mixins, inheritance and other goodies.

### Variables

Variables is a way to store information that you want to reuse throughout your stylesheet.

```css
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

### Mixins

A mixin lets you make groups of CSS declarations that you want to reuse throughout your site.

```css
@mixin transition($seconds) {
  -o-transition: all $seconds ease-in-out;
  -webkit-transition: all $seconds ease-in-out;
  -moz-transition: all $seconds ease-in-out;
  transition: all $seconds ease-in-out;
}

.box { 
  @include transition(.5s); 
}
```

When your CSS is generated it'll look like this:

```css
.box {
  -o-transition: all .5s ease-in-out;
  -webkit-transition: all .5s ease-in-out;
  -moz-transition: all .5s ease-in-out;
  transition: all .5s ease-in-out;
}
```

### Extend/Inheritance

`@extend` lets you share a set of CSS properties from one selector to another. It helps keeping your SCSS DRY\(don't repeat yourself\).

```css
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}
```

When your CSS is generated it'll look like this:

```css
.message, .success, .error {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}
```

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

Doing math in your CSS is very helpful. SCSS has a handful of standard math operators like `+`, `-`, `*`, `/`, and `%`.

