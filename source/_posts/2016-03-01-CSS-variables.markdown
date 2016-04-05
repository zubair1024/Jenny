---
layout: post
title:  "CSS Variables"
date:   2016-03-01 13:46:52
comments: true
categories: css,variables,tips
---


The good news is that variables are now supported in vanilla CSS.

Variables in CSS  follow the same scope and inheritance rules that CSS generally follows. The easiest location to place your variables is at the root level, which will allow any class, pseudo class selector to inherit it.

```css

    :root{
        --roamworks-black: #000;
    }

```

To access the value use the var() syntax:

```css

    .header-body{
        background-color: var(--roamworks-black);
    }

```


How and where is the use for these variables? Well, it will come of use in situations in which a single value is repeated through the stylesheet, such as colors for a theme (quite the same reason we are using a CSS Pre-processor right now). There a plus side to using this method since more meaningful names can we given to the variables to make development and debugging of style-sheets a breeze.


```css

    :root{
        --primary-color: #000;
        --secondary-color: #AA3939;
        --shadow: 0 2px 1px 0 #000;
    }


    html{
        background-color: var(--primary-color);
    }


    button{
        color: var(--secondary-color);
        box-shadow: var(--shadow);
    }

```


Here are some really neat tricks you can use such as using fallbacks are demotrated below:

```css

    width: var(--width, 20%);

```

Or the use of nested/cascaded variables such as:

```css

    --primary: #000;
    --background-gradient: linear-gradient(to top, var(--primary), #FFF);

```

Only Firefox supports CSS variables out the box. However, versions >=49 of Chrome will also ship with the feature enabled.



