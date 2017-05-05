#### Contents
- [Introduction](readme.md)
- [BEM](bem.md)
- [HTML Structure](htmlstructure.md)
- [CSS Structure](cssstructure.md) <- You are here
- [Classnames](classnames.md)
- [Bootstrap](bootstrap.md)
----

# CSS Structure

To prevent CSS files multiple 100s of lines long, we divide each file based on what they do.
We have 3 main categories, which are represented as folders.

- **General** - General styles such as buttons, forms, lists, etc.
- **Layout** - Layout specific elements that define the main layout of the website. Such as the header, footer, menu, and columns.
- **Elements** - Specific elements that are represented throughout pages, examples may include sliders, modals, and tabs.

Under these folders individual files are made based on the element. `_menu.scss` will of course have all the styles associated with the menu. Each file starts with the parent class such as `.menu`. No other parent elements will be found in this file unless they are highly relevant. Such as `.menu` and `.menu-trigger-mobile`, which may not be found in the parent element.

## Nesting and indenting
There are several ways to nest BEM based classes.

```
  .menu {
    &__item {
      &--modifier {

      }
    }
  }
```
```
  .menu {

  }

  .menu__item {
    &--modifier {

    }
  }
```

Both of these methods work and have their advantages and disadvantages. In the first example the child is nested under the parent. This makes for less writing. The main disadvantage of this is readability and also search-ability. You can no longer `ctrl+f` the classname.
Because of this I prefer the second method.

Modifiers are always stated in the main element. The same goes for complex selectors.

```
.menu__item {
  &:first-child {}

  &:hover,
  &:active {}

  &::before {}
}
```
#### Quick notes

- Classes are always separated with a newline in between.
- Pseudo elements are always given with double `::`, to represent that it is an element, unlike states such as `:hover`
- When a `:hover` is given, a `:active` should also be given. This is to give feedback to clicks on touchscreen devices.
- Double quotes `" "` are used wherever relevant.
- Indentation is done with 2 spaces.

## Media Queries

Media queries are always mobile-first and thus represented as `min-width`. A few standard breakpoints include:

```
  $max-width: // The maximum width of your layout;

  $breakpoints: (
    "mobile":           "(min-width: 460px)",
    "mobile-large":     "(min-width: 580px)",
    "tablet":           "(min-width: 768px)",
    "desktop":          "(min-width: 1024px)",
    "desktop-large":    "(min-width: 1200px)",
    "max-width":        "(min-width: #{$max-width})"
  );
```

This is a standard variable that should be available in every project. These media queries can than be used with the following mixin.

```
  @mixin mediaquery($size){
    $query: map-get($breakpoints, $size);

    @media #{$query}{
      @content;
    }
  }
```

This can be used with `@include mediaquery("tablet") { }`.

## Font Sizes
In order to make large fonts properly readable on all screens they should be scaled down with screen width, not just the media queries. This can be done with the following mixin.

```
@mixin flexibleFontSize($size: 10, $min-width: 560px) {
  font-size: $min-width * ($size / 100);

  @media (min-width: $min-width) {
    font-size: #{$size}vw;
  }

  @include mediaquery("max-width") {
    font-size: $max-width * ($size / 100);
  }
}
```

This can be used with `@include flexibleFontSize(5, 560px);`. Where first number is the font-size in view-width based on the maximum width of the layout. The second number represents the point where the font no longer scales down.
