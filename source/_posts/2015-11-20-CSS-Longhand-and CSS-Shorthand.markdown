---
layout: post
title:  "CSS Longhand and CSS Shorthand"
date:   2015-11-20 13:46:52
comments: true
categories: numeronyms, tips
---


CSS Longhand and CSS Shorthand. Have you been confused about which method to choose when writing a piece of CSS code. I present you with a quick walk-through in this post which will equip you henceforth to make better decisions on the methodology, however, always remember that one is concise and the other one is precise.

### Shorthand?

Shorthand property is a property that takes the values for other sets of CSS properties. Basically,

```css

    border: 1px solid blue;

```

is the same as

```css

    border-width: 1px;
    border-style: solid;
    border-color: blue;

```

Through this methodology we do not have to declare individual properties separately. This will save us from redundant and time/space consuming code.

In certain situations such as when it comes to padding and margin, always remember that the order matters.

```css

    padding: 1px 1px 1px 1px;

```

is the same as

```css

    padding-top: 1px;
    padding-right: 1px;
    padding-bottom: 1px;
    padding-left: 1px;

```

When in doubt always remember CLOCKWISE!

Now, let us see what happens when a property is left out of the declaration.

```css

    border: 1px blue;

```

In the above code we won’t be able to see the border anymore, which is because the border-style property was left out, for which it got the default value of none. Basically it got a property of

```css

    border: 1px none blue;

```

This concludes it for us that when a property value is left out in a shorthand declaration, that property takes on its default value (even if it has to override any previous value assigned for the same).

On an important note, we cannot use values like inherit, initial or unset, which are available for all the CSS properties, in shorthand notation.

### Longhand?

Yes, it is true that shorthand alternatives are handy. But, in certain rare situations they are of a disadvantage.
Take font shorthand property for example for a h4 tag.

```css

    font: 20px "courier new";

```
In the above shorthand code, no value is there for the font-weight property, hence the font-weight:bold(browser default style) will be overridden by the default value font-weight:normal causing the h4 element to lose its bold style, which may not has been intended.

So in these rare but important situations Longhand property are useful. Productivity aside, during development some developers/coders/programmers find longhand notations a lot easier to work with than the shorthand, mainly because in terms of readability and clarity it is indisputable.

