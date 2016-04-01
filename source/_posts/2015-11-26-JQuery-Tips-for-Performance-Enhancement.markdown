---
layout: post
title:  "JQuery Tips for Performance Enhancement"
date:   2015-11-26 13:46:52
comments: true
categories: jquery, tips
---

We always start from a light weight page and try and try to keep the code as simple and straight forward as possible with a few exceptions. But, over the course of time, these exceptions accumulate and you have heavy dynamic website that you need to be optimized. Hence, it is always good to keep a few rules in mind when developing a web page or a dynamic JQuery based application.Below are listed some best common performance practices:

#### Always go lower from an #id
The fastest way to select an element is by #id.

```javascript

    $('#content').hide();

```

#### Use tags before classes

Since, the tag selector in JQuery maps to the native JavaScript method getElementsByTagName(). The best way is to prefix with a tag name and descend from an #id.

```javascript

    var receiveNewsletter = $('#nslForm input.on');

```
The class selector is the slowest. In browser with trident engine it loops through the entire DOM, which can be considered to be necessarily expensive. Hence, it is is preferable to not to put tag name before an #id.

```javascript

    var content = $('div#content');

```
It is also preferable not to descend from multiple #id.

```javascript

    var traffic_light = $('#content #traffic_light');

```

#### Cache the parent object
It is preferable to cache the parent object and then run queries on it.

```javascript

    var header = $('#header');
    var menu = header.find('.menu');
    var menu = $('.menu', header);

```

#### Optimize and adhere to Sizzle’s model
JQuery has been using Sizzle’s Javascript Library which is quite different from the selector engines of the past. The most obvious aspect is that it uses ‘right to left’ model unlike the ‘left to right’ model of the past.

```javascript

    var linkContacts = $('.contact-links div.side-wrapper');

```

instead of:

```javascript

    var linkContacts = $('a.contact-links .side-wrapper');

```

#### Use find() more than context
The .find() function seems to be faster. But this counts more when you have a lot of traversing a page with lots of DOM elements:

```javascript

    var divs = $('.testdiv', '#pageBody'); // 2353 on Firebug 3.6
    var divs = $('#pageBody').find('.testdiv'); // 2324 on Firebug 3.6 - The best time
    var divs = $('#pageBody .testdiv'); // 2469 on Firebug 3.6

```

### Use Chaining

It is better to chain than to cache.

```javascript

    $("#p1").css("color", "red").slideUp(2000).slideDown(2000);
```

#### Write selectors if needed
If you have selectors that you use often in your script – extend jQuery object $.expr[‘:’] and write your own selector.

```javascript

    $.extend($.expr[':'], {
    abovethefold: function(el) {
    return $(el).offset().top < $(window).scrollTop() + $(window).height();
    }
    });
    var nonVisibleElements = $('div:abovethefold'); // Select the elements

```

#### Cache JQuery Objects
Cache the objects that you require often.

```javascript

    var header = $('#header');
    var divs = header.find('div');
    var forms = header.find('form');

```

#### Wrap elements for DOM insertion
DOM insertion is considered to be very expensive and slow. Hence, do DOM manipulation less frequently.

```javascript

    var menu = '
    ';
    for (var i = 1; i < 100; i++) {
        menu += '
    ' + i + '';
    }
    menu += '';
    $('#header').prepend(menu);

    // Instead of doing:

    $('#header').prepend('
    ');
    for (var i = 1; i < 100; i++) {
        $('#menu').append('
    ' + i + '');
    }

```

#### Use Object Detection
It’s great that jQuery methods don’t throw a ton of errors at your users, but that doesn’t mean that as a developer you should just rely on that. Even though it won’t throw an error, jQuery will have to execute a number of useless functions before determining that an object doesn’t exist.

Use $.ajax() rather than $.get(), $.getJSON(), $.post()
For better performance you can use direct functions like $.ajax() rather than $.get(), $.getJSON(), $.post() because the last ones are shortcuts that call the $.ajax() function.

Use jQuery’s internal data()
Use the .data() function to store stuff for your elements:

```javascript

    $('#head').data('name', 'value');
    // later in your application:
    $('#head').data('name');

```

#### Use jQuery utility functions
Don’t forget about jQuery Utilities functions that can be very handy($.isFunction(), $.isArray(),$.each() etc).

Add “JS” class to your HTML Attribute
As soon as jQuery has loaded you use it to add a “JS” class to your HTML tag.

```javascript

	$('HTML').addClass('JS');

```

Because that only happens when javascript is enabled, you can use it to add CSS styles which only work if the user has JavaScript switched on

```css

  /* In your css */
    .JS #myDiv{display:none;}

```


So, what this means is that we can hide content when JavaScript is switched on and then use jQuery to show it when necessary, while those with JavaScript off see all of the content, as it’s not hidden.

#### Defer to $(window).load
It’s faster to use $(window).load() than $(document).ready(). though, this is situational and needs to be tested.

Leverage Event Delegation (a.k.a. Bubbling)
When you have a lot of elements in a container and you want to assign an event to all of them – use delegation to handle it.

```javascript

    $("table").delegate("td", "hover", function(){
        $(this).toggleClass("hover");
    });

```

#### Shorthand for the ready events
If you want to save some bits on compressing your js plugin – replace the $(document).onready() event:

```javascript

    // Instead of:
    $(document).ready(function (){
        // your code
    });
    // you can do:
    $(function (){
        // your code
    });

```

Happy Programming!