---
layout: post
title:  "A Thing Or Two About Javascript Functions"
date:   2015-11-26 13:46:52
comments: true
categories: javascript
---
Being a JavaScript developer since quite some time now, I have been displeased on how fellow developers do not seem to comprehend JavaScript functions and their associated Jargons properly. This can be seen as a consequence of taking them for granted, thinking how different can they be from functions in other programming languages. Truth be told, they are not so different but there are subtle differences that need to be accounted for, especially when you term yourself as a JavaScript programming. Frankly, I’m writing this post because I recently met a developer with really good programming skills but failed on some basics of JavaScript functions. Though, I would still say that this post is meant for the noobs and if you’re not a noob you can just scrap those this post.Knowing the different ways of expressing and defining functions opens up the possibility of implementing a logic in a more optimal way in JavaScript.

### Function declaration and function expression

When you state a function with the keyword, it becomes a function declaration and when you put the JavScript function declaration in a JavScript expression it becomes a function expression.

```javascript

    // Function declaration
    function function_name() {};
    // Function expression
    var function_name = function() {};

```
All JavaScript functions are hoisted. Hoisted means that it is moved up in the scope. ence writing a function call before the function declaration works.

```javascript

    function_name();//function call[WORKS]
    function function_name(){};

```

But when you can’t do the same when the function is used in an expression.

```javascript

    function_name();//function call[WON'T WORK]
    var function_name = function(){};

```
### Self Invoking or Immediately Invoking Function Expression (IIFE)

It’s a function expression, the code of which gets executed immediately, unusually only once. You can create one by simply adding () (syntax used for calling a function) right after a function expression. As you can see below it can be anonymous.

```javascript

    (function optional_function_name() {
      //body
    }());

```
or

```javascript

    (function optional_function_name() {
      //body
    })();

```

The parenthesis around the function declaration converts it to an expression and then adding () after it calls the function. There are different ways of doing the same.

```javascript

    // Some of the ways to create IIFEs
    !function() { /* ... */ }();
    +function() { /* ... */ }();
    new function() { /* ... */ };

```
IIFE is ideal for writing code that needs to execute only once, namespacing, creating closures, creating private variables etc.

### Methods

When a function is an object’s property, it is called method. I’m not much of a jargon nazi, but I cannot emphasis on this enough little terminology. Since a function is also an object, a function inside another function is also a method.

```javascript

    var calc = {
      add : function(a,b){return a+b},
      sub : function(a,b){return a-b}
    }
    console.log(calc.add(1,2)); //3
    console.log(calc.sub(80,2)); //78
    function add(a){
      return function(b){return a+b;}
    }
    console.log(add(1)(2)); // Output is 3

```

### Arrow Functions (ES6 Standard) [Only in Firefox]

A new function definition from ES6 Standard provides a shorter syntax for function expression. Though, this methodology has quite caught on, it worthwhile to note it.

```javascript

    () => { /* body */ }

```

So a function expression

```javascript

    var sing = function(){
      console.log('singing...')
    };

```
can be written as

```javascript

    var sing = () => {
      console.log('singing...')
    };

```

Please note that these functions are anonymous and does not have its own this value, this inside it will be same as this in the enclosing code.

What is the point of this? It comes in handy when minimizing code

```javascript

    setInterval(function () {
      console.log('message')
    }, 1000);

```

can be written as

```javascript

    setInterval(() => console.log('message'), 1000);

```

### Generator Functions (ES6 Standard) [Only in Firefox]

Generator functions are capable of halting and continuing its execution.

```javascript

    function* function_name(){}
    //or
    function *function_name(){}

```

Generator functions create iterators. The iterator’s next method is then used to execute the code inside the generator function until the yield keyword is reached.

```javascript

    function *generator_func(count) {
    for(var i=0;i<count;i++){
    yield i+1;
    }
    }

    var itr = generator_func(4);
    console.log(itr.next()); //Object { value: 1, done: false }
    console.log(itr.next()); //Object { value: 2, done: false }
    console.log(itr.next()); //Object { value: 3, done: false }
    console.log(itr.next()); //Object { value: 4, done: false }
    console.log(itr.next()); //Object { value: undefined, done: true }
    console.log(itr.next()); //Object { value: undefined, done: true }
```

There’s also a yield* expression which passes the value to another generator function

```javascript

    function *fruits(fruit) {
    yield* veggies(fruit);
    yield "Grapes";
    }

    function *veggies(fruit){
    yield fruit + " and Spinach";
    yield fruit + " and Broccoli";
    yield fruit + " and Cucumber";
    }

    var itr = fruits("Apple");
    console.log(itr.next().value); //"Apple and Spinach"
    console.log(itr.next().value); //"Apple and Broccoli"
    console.log(itr.next().value); //"Apple and Cucumber"
    console.log(itr.next().value); //"Grapes"
    console.log(itr.next().value); //undefined

```

Anyhow, these are a few points that every JavaSript programming, a noob or a pro, needs to be familiar with.

Happy Programming!

