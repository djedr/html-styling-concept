# A simpler styling model for HTML: idea and proof of concept

I argue that the model of styling introduced by CSS is fundamentally flawed in relying on complex nonlocal rules of precedence. Much time is wasted on dealing with them.

There is a simpler way to achieve abstraction of style from content. 

We should leverage the programming model of JavaScript (or any other programming language that follows well-established rules based on lambda calculus) instead of replacing it with idiosyncratic concepts such as cascading and specificity.

These idiosyncratic CSS concepts introduce more problems than solutions and are not tenable. They don't work in practice and are impossible to use effectively, even after extensive practice.

## Outline of the solution

It should be possible to style HTML elements more or less like so:

```html
<p data-style="class1, class2, class3('parameter')">
  contents
</p>
```

where `class1`, `class2`, and `class3` are abstractions which change the style of the `p` element.

These abstractions could be implemented on top of CSS classes or JavaScript-like functions, but the details are not important at this point. 

What is important is that they should be applied in the order they are specified in and that there should be a way to parametrize them.

## Proof of concept

* [css.html](css.html) -- this shows a minimal example of conflicting CSS rules
* [css+js.html](css+js.html) -- demonstrates how conflicts could be solved locally
* [js.html](js.html) -- another way to solve conflicts locally + demonstration of parametrizability
* [The problem with CSS](https://www.youtube.com/watch?v=q0Otp_W3V0Y) -- a more in-depth discussion of the problem and yet another custom solution

## Going further

Most likely the most fitting way to implement this at this point is to extend CSS with a syntax like:

```html
<p style="class1; class2; class3('parameter');">
  contents
</p>
```

We would also make CSS classes optionally parametrizable:

```css
.class(--param) {
  color: var(--param)
}
```
