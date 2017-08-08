---
layout: post
title: You Don't Know JS (1) - Closures
categories: [CS3216, Blog]
tags: [javascript, asynchronous]
description: Most Javascript developers get by without ever having to understand closures. You could get by without closure, but developing an understanding of closures will allow you to unlock more of Javascript's potential.
---

In an effort to prepare myself for CS3216, I spent the last two weeks refreshing my javascript knowledge. Having heard stellar reviews of the [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS) series, I decided to dive deep into it hoping to develop a more complete understanding of the world's most misunderstood language.

In this blog post series, I will share some of the insights that I have developed studying the book series. I will attempt to explore concepts in an javascript-experience agnostic manner for the benefit of non javascript developers. 

Let's get started.



### Closures

Most Javascript developers get by without ever having to understand closures. You could get by without closure, but developing an understanding of closures will allow you to unlock more of Javascript's potential. To gain a deep understanding of closures, let us begin from the bottom.



##### Javascript is compiled

While Javascript behaves like an interpreted language, it is in fact compiled. 



##### Lexical scoping vs Dynamic scoping

The implications of Javascript being compiled is that it has two scopes:

- Lexical scope - the scope of a function during compile time. 
- Dynamic scope - the scope of a function during run time. 

While interpreted languages only have a dynamic scope to worry about, compiled languages have to juggle both the dynamic and interpreted scopes. 

For the benefit of those who do not understand scopes, the scope is the list of environments that the function has access to. Let me illustrate this concept using the below code snippet.

```javascript
"use strict";

var foo = 'a';

function bar() {
  var foo = 'b';
  console.log(foo); //prints 'b'
};

function bar2() {
  console.log(foo) //prints 'a'
};

bar();
bar2();
console.log(foo); //prints 'a'
```

On top of having access to their own scopes, the functions bar and bar2 both have access to the global scope. This is why function bar2 is able to print foo as 'a' even though foo is not declared explicitly within bar2. 



##### Closures

In Javascript, functions are first-class citizens. This means that Javascript supports the passing of functions as arguments into other functions.

Closures are the result of two of Javascripts properties:

- Compiled (thus, having compile time and run time scopes)
- First-class functions (thus, able to execute functions outside of their lexical scope)

Closures occur when a function is being executed outside of its lexical scope. In a closure, a function remembers its lexical scope even when executed outside of its lexical scope.

```javascript
"use strict";

function foo() {
  var bar = 'bar';
  function baz() {
    console.log(bar);
  };
  bam(baz);
};

function bam(func) {
  func(); //prints "bar"
};

foo();
```

In the above example, the function baz is being passed out of the function foo into the global function bam. On line 12 when we execute the function func(), we are still able to access the lexical scope of function baz even though func is being executed outside of the lexical scope of baz.

While closures seem obvious enough when we program synchronously, it begins to get tricky once we program asynchronously. 



##### When closures get tricky - Requires some Javascript experience

Observe the below asynchronous code snippet:

```javascript
for (var i=1 ; i<=5 ; i++) {
  setTimeout(function(){
    console.log(i);
  }, i*1000);
};
```

What does it print?

- Most developers would guess [1,2,3,4,5], but it actually prints [6,6,6,6,6]. Test it out yourself to be convinced of this.

Why do we not get [1,2,3,4,5]?

- For each iteration of the loop, we call an asynchronous function over the same exact global scope. There is no new scope created within each iteration of the loop. Hence, all of the functions print 6 since they are enclosed by the same global scope.

So how do we get the asynchronous functions to print [1,2,3,4,5]?



##### Solution 1 : The Let keyword

```javascript
for (let i=1 ; i<=5 ; i++) {
  setTimeout(function(){
    console.log(i);
  }, i*1000);
};
```

The let keyword ([introduced in ES6](https://github.com/lukehoban/es6features)) creates a new closure within each iteration of the loop. Hence, each of the asynchronous functions are enclosed within a different dynamic scope.



##### Solution 2: Immediately Invoked Function Expressions (IIFE)

```javascript
for (let i=1 ; i<=5 ; i++) {
  (function (i) {
    setTimeout(function(){
      console.log(i);
    }, i*1000);
  })(i);
};
```

For those who are not familiar with function expressions and IIFEs, read [this](http://adripofjavascript.com/blog/drips/an-introduction-to-iffes-immediately-invoked-function-expressions.html).

Similiar to the let keyword, IIFEs also allows us to enclose each iteration of the loop within a different dynamic scope.

