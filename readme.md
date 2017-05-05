# SCSS Styleguide
This is a styleguide to write consistent CSS across multiple projects. This styleguide sets to introduce a solid baseline to write coherent CSS which can easily be adopted by multiple developers working on the same project.

---
#### Contents
- [Introduction](readme.md)
- [BEM](bem.md)
- [HTML Structure](htmlstructure.md)
- [CSS Structure](cssstructure.md)
- [Classnames](classnames.md)
- [Bootstrap](bootstrap.md)

----
## Introduction
Writing solid front-end code is just as important as your back-end code. Even when it comes to "simple" things as CSS. Writing solid code can and will safe a lot of time in the long run. Having a consistent way of writing your CSS will help switching from project to project go much more smoothly.

This styleguide will introduce a way to write your CSS in a way that can easily be adopted across multiple projects with multiple developers. As a baseline we will use BEM (**Block**, **Element**, **Modifier**). BEM is a naming structure which sets to eliminate a lot of annoyances of CSS, namely nesting.

```
ul li a {} // The link is nested 3 deep, making it difficult to easily target it
ul a.link {} // Even though this link now has a classname, it is still overwritten by the previous statement
a#link {} // IDs always go first, no matter what
```
CSS like this can quickly become a mess to maintain, as you always have to think of nesting. BEM sets to eliminate nesting to prevent this.

----
#### Resources
- [BEM](http://getbem.com/naming/)
- [Boostrap 4](https://v4-alpha.getbootstrap.com/)
