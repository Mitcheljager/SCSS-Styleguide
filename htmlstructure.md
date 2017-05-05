#### Contents
- [Introduction](readme.md)
- [BEM](bem.md)
- [HTML Structure](htmlstructure.md) <- You are here
- [CSS Structure](cssstructure.md)
- [Classnames](classnames.md)
- [Bootstrap](bootstrap.md)
----

# HTML Structure
It's important to write your HTML in a way that is easy to read and understand. Not just by you, but by bots! Google is getting smarter by the day, and we can give it a little hand by writing clear HTML. This is where [semantics](http://www.hongkiat.com/blog/freebies-web-designer-oct-2015/) come in!

## Semantics
Semantics are elements that tell your browser/bots what is going on. A few simple examples include tags as `form`, `strong`, `img`. These are of course widely used and have their own attributes associated with them. Better examples would be:

```
  <article>
  <aside>
  <details>
  <figcaption>
  <figure>
  <footer>
  <header>
  <main>
  <mark>
  <nav>
  <section>
  <summary>
  <time>
```

Each element has their own function and can tell bots what is going on. This way search engines can render things based on what you tell it:

![](http://i.imgur.com/BLQ52x8.png)

![](http://i.imgur.com/5X6cDjF.png)

## Structure

With proper semantics a webpage might look something like this:
```
<nav></nav>

<header></header>

<main>
  <section></section>

  <section></section>

  <section>
    <article>
      <figure>
        <img />
      </figure>
      <figcaption></figcaption>

      <p></p>    
    </article>
    <aside></aside>
  </section>
</main>

<footer>
  <nav></nav>

  <address></address>
</footer>
```

`<section>` Is to be used for any full element on a page that could also be represented without context around it. A `<div>` is for elements that aren't necessarily readable content.

**Elements should be used smartly and efficiently.**
```
  <nav>
    <ul>
      <li><a></a></li>
      <li><a></a></li>
      <li><a></a></li>
      <li><a></a></li>
    </ul>
  </nav>
```
```
  <nav>
    <a></a>
    <a></a>
    <a></a>
    <a></a>
  </nav>
```

The second example provides exactly the same context as the first, while being way more readable. With proper css to back it, very little elements can be used per element.

**Another example**
```
  <article>
    <div>
      <img />
    </div>
    <div>
      <h1></h1>
      <p></p>
    </div>
  </article>
```
```
  <article>
    <img />

    <h1></h1>
    <p></p>
  </article>
```

While the first one provides `divs` to easily manipulate in your css, it should in most cases not be necessary. The less elements you use, the better.
