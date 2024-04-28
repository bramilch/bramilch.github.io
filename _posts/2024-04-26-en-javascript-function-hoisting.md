---
layout: post
title: "JavaScript Functions and Hoisting "
author: bramilch
date: 2024-04-26 18:00:00 +0900
categories: [Frontend, Data Engineering]
tags: [Frontend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
---

<br>

> 2024/04/26: Drafted  
> 2024/04/27: Revised the text. Context, unclear wording, etc.
 
※ There may be errors in the content.
※ This article is a summary of the content of NAVER Connect Foundation's Boost Course Web Programming (Full Stack) lecture and supplemented by myself.

<br>

**Table of Contents**

- [JavaScript function characteristics, Call Stack, default return value, keyword arguments](#javascript-function-characteristics-call-stack-default-return-value-keyword-arguments)
- [Function Declarations, Function Expressions, and Hoisting](#function-declarations-function-expressions-and-hoisting)

<br>

## JavaScript function characteristics, Call Stack, default return value, keyword arguments

<br>

- Functions matter a lot in JavaScript

- Being good at JavaScript means being good with JavaScript functions.

- Understanding the call stack, which is a series of calls to functions, is critical for implementing program logic, debugging, and improving performance.

- JavaScript functions are supposed to return undefined, which means nothing.
  - In other languages, there is no such thing as void, which means that a function returns nothing (no return value).

<br>

```
function test(){};
console.log(test());
```

Console results:

```
undefined
```

<br>

- Because function parameters are supposed to return undefined even if they have nothing in them, even if you don't write down the parameter names.

- Inside function, the keyword that creates the function, return seems to return the undefined datatype.

- Different number of parameters and arguments in a function does not cause an error, only the order and number of function parameters.

- Arguments passed as function parameters do not need to be declared as variables.
  When the function is executed, the key:value object local variable is automatically created with the variable name **_arguments_** inside it, and can be accessed one by one.

- By creating an arguments variable inside the function declaration expression function keyword, it seems to receive all the arguments passed in the call as object.

<br>

> <span style="font-size:1.2em;">**_arguments should be used with care. They should only be used when necessary and intended, such as to check the number of arguments being passed, and should not be tampered with because they are vulnerable to changes, such as the possibility of changing the value of a function's arguments._**</span>

<br>

## Function Declarations, Function Expressions, and Hoisting

<br>

- There are two ways to create a function in JavaScript.  
  > **1. function declarations (which directly create a function object)**  
  > **2. function expressions (which assign a function to a variable).**

- JavaScript executes code in a hoisting fashion, where the JS parser collects the variable declarations first, and the function is fetched in its entirety (in a function expression, only the variable to which the function is assigned is fetched), dragged to the top, and declared first.

- Calling a function in a function expression with undefined because you only declared the variable in the function expression and did not assign a value can cause an error.

<br>

> <span style="font-size:1.2em;"> **_Function expressions are therefore dependent on the variable to which the function is assigned and the order of the function's codeline._**</span>
