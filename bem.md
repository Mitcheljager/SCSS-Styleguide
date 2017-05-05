#### Contents
- [Introduction](readme.md)
- [BEM](bem.md) <- You are here
- [HTML Structure](htmlstructure.md)
- [CSS Structure](cssstructure.md)
- [Classnames](classnames.md)
- [Bootstrap](bootstrap.md)
----

# BEM
----
BEM, *or Block, Element, Modifier*, is a CSS naming structure which seeks to eliminate a lot of the annoyances that come with CSS. The biggest example being nesting. It is meant to give more meaning to your classnames and in term make it easier to understand what is going on.

```
  .block {}
  .block__element {}
  .block--modifier {}
```

- `.block` is the parent element.
- `.block__element` is a descendent (However deep) of `.block`
- `.block--modifier` represents a different form of the main element. This can be a different style, or a state it is in, such as `is--active`.

You always target a class, never just an element such as `.block a`. Not only to prevent nesting, but also to prevent targeting unwanted elements.

##### Think of the children
An element will **never** feature double descendants such as `block__element__child`. A classname should always tell what it is, and not where it is. Using double child elements would defeat this purpose.

A child of a modifier can be targeted in multiple ways.

```
  .block--modifier__element {}
  .block__element--modifier {}
  .block--modifier .block__element {}
```

- `.block--modifier__element` is clear but can result in a lot of classnames
- `.block__element--modifier` should only be used in situations where the element could also change without the parent modifier
- `.block--modifier .block__element` is the easiest way of doing it without creating clutter in the HTML. It does however partially defeat the point of not having any nesting. Despite of that, this is my preferred method, as it leaves the most neat HTML.

## A practical example
```
  <form class="form">
    <div class="form__group">
      <input class="form__input" type="text">
      <label class="input__label">I am labelled</label>
    </div>

    <div class="form__group">
      <input class="form__input--large" type="text">
      <label class="input__label">I am labelled</label>
    </div>
  </form>
```
```
  .form {}

  .form__group {}

  .form__input{

    &--large {}
  }

  .form__label {}
```

`.form` is targeted, not `form`. In it several elements can be found on different levels of nesting, yet each is described as a descendant of `.form__*`. This way it is clear where to find an element, without restricting it to it's position. `.form__input` could now be placed at top level, with the CSS having to change.

**BEM**
```
  <div class="media">
    <img class="media__image" />
    <p class="media__content"></p>
  </div>
```

**Traditional CSS**

```
  <div class="media">
    <img class="image">
    <p class="content"></p>
  </div>
```
In this example the benefit of the nested style of classnames is clearly visible. Without context of it's parent element the class `.content` tells nothing of where to find it and what it's function is. Where as `.media__content` clearly tells you where to find it.

## When not to BEM

It's easy to go overboard with BEM. A good example are simple modifier classes.
```
  .element--bold {}
  .bold {}
```
The first one clearly tells you what is going on, but you might enter a situation where `bold` might be used on a multitude of different elements. In this case a simple `.bold` class might be a better option to prevent clutter.

```
  .title__tagline {}  
  .tagline {}
```
While the first one clearly describes what is going on with `tagline`, you might run in to situations where you want to use `.tagline` by itself. In this case it is better to use a standalone class.

Things like this can be a little bit difficult to judge.
