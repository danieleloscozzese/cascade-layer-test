# cascade-layer-test

A tiny test repo with some CSS Cascade Layer examples.

The mechanism is simple enough: the rules in a layer override any other rules
of previous layers on the same element and property.

[MDN documents this](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_layers)

The concrete example here is the override of the style of the
[base values](./base-values.css) with the
[styles](./styles.scss).

If the stylesheet had no layers it would be the following:

```css
.heading {
  font-size: 2rem;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: 1.5em;
  font-weight: bold;
  text-decoration: none;
}
```

The source order isn't enoug here: the heading element selectors do not
override the class selector even though they select the same elements.

Instead, we have the following code:

```css
@layer base {
  .heading {
    font-size: 2rem;
  }
}

@layer styles {
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-size: 1.5em;
    font-weight: bold;
    text-decoration: none;
  }
}
```

The `styles` layer is later than `base` and so even the single element selector
overrides a class selector from the layer before.
