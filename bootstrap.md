#### Contents
- [Introduction](readme.md)
- [BEM](bem.md)
- [HTML Structure](htmlstructure.md)
- [CSS Structure](cssstructure.md)
- [Classnames](classnames.md)
- [Bootstrap](bootstrap.md) <- You are here
----

# Bootstrap

Using bootstrap together with BEM is a little bit tricky, as they both have a very different way of doing things. However it can be done!

The bootstrap classnames should not be used on their own (unless relevant), instead the mixins should be used.

```
.content {
  @include make-row();
}

.content__column {
  @include make-column(12)
  @include make-sm-column(4);

  &--small {
    @include make-column(12);
    @include make-sm-(2);
  }
}
```

Using `@include` instead of `@extend` prevents huge class blocks from being created.

### A list of all relevant Bootstrap mixins

```
// Alerts
@include alert-variant($background, $border, $text-color);

// Background Variant
@include bg-variant($parent, $color);

// Border Radius
@include border-top-radius($radius);
@include border-right-radius($radius);
@include border-bottom-radius($radius);
@include border-left-radius($radius);

// Buttons
@include button-variant($color, $background, $border);
@include button-size($padding-vertical, $padding-horizontal, $font-size, $line-height, $border-radius);

// Center Block
@include center-block();

// Clearfix
@include clearfix();

// Forms
@include form-control-validation($text-color: #555, $border-color: #ccc, $background-color: #f5f5f5);
@include form-control-focus($color: $input-border-focus);
@include input-size($parent, $input-height, $padding-vertical, $padding-horizontal, $font-size, $line-height, $border-radius);

// Grid Framework
@include make-grid-columns($i: 1, $list: ".col-xs-#{$i}, .col-sm-#{$i}, .col-md-#{$i}, .col-lg-#{$i}");
@include float-grid-columns($class, $i: 1, $list: ".col-#{$class}-#{$i}");
@include calc-grid-column($index, $class, $type);
@include loop-grid-columns($columns, $class, $type);
@include make-grid($class);

// Grid
@include container-fixed($gutter: $grid-gutter-width);
@include make-row($gutter: $grid-gutter-width);
@include make-xs-column($columns, $gutter: $grid-gutter-width);
@include make-xs-column-offset($columns);
@include make-xs-column-push($columns);
@include make-xs-column-pull($columns);
@include make-sm-column($columns, $gutter: $grid-gutter-width);
@include make-sm-column-offset($columns);
@include make-sm-column-push($columns);
@include make-sm-column-pull($columns);
@include make-md-column($columns, $gutter: $grid-gutter-width);
@include make-md-column-offset($columns);
@include make-md-column-push($columns);
@include make-md-column-pull($columns);
@include make-lg-column($columns, $gutter: $grid-gutter-width);
@include make-lg-column-offset($columns);
@include make-lg-column-push($columns);
@include make-lg-column-pull($columns);

// Hide Text
@include text-hide();

// Image
@include img-responsive($display: block);
@include img-retina($file-1x, $file-2x, $width-1x, $height-1x);

// Labels
@include label-variant($color);

// List Group   
@include list-group-item-variant($state, $background, $color);

// Nav Divider
@include nav-divider($color: #e5e5e5);

// Nav Vertical Align
@include navbar-vertical-align($element-height);

// Opacity
@include opacity($opacity);

// Pagination
@include pagination-size($padding-vertical, $padding-horizontal, $font-size, $border-radius);

// Panels
@include panel-variant($border, $heading-text-color, $heading-bg-color, $heading-border);

// Progress Bar
@include progress-bar-variant($color);

// Reset Filter
@include reset-filter();

// Resize
@include resizable($direction);

// Responsive Visibility
@include responsive-visibility($parent);
@include responsive-invisibility($parent);

// Size
@include size($width, $height);
@include square($size);

// Tab Focus
@include tab-focus();

// Table Row
@include table-row-variant($state, $background);

// Text Emphasis
@include text-emphasis-variant($parent, $color);

// Text Overflow
@include text-overflow();
```
