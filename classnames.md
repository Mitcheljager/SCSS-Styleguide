#### Contents
- [Introduction](readme.md)
- [BEM](bem.md)
- [HTML Structure](htmlstructure.md)
- [CSS Structure](cssstructure.md)
- [Classnames](classnames.md) <- You are here
- [Bootstrap](bootstrap.md)
----

# Classnames

A good classname should tell what the class is without having to look at other context. The name should describe what the element does, not what it looks like. `.menu__item--yellow` Should not be used, instead it would be `.menu__name--highlight` or something similar.

```
  .item--modifier
  .item--is-state
```
- A modifier should be used when a an element has a permanent effect, such as a different style.
- A state, indicated by `--is-*` should be used for a style that might change with an action, such as `.modal--is-active`.

## Rules
Classnames should be clear and consistent.
- Never use abbreviations. `.button`, not `.btn`. `--large`, not `--lg`.
- Use similar names where relevant such as `.list__item` and `.menu__item`.
- Use Kebab-case where relevant. `.long-item-name--modifier-name`

## Variables
Variables are similar to classnames in that they should tell what they do, not what they look like.

```
  $light;
  $lighter;
  $lighest;

  $red;
  $blue;
```

These are examples of bad variable names. The first leave no room for expansion. The colors leave no room for change. 
