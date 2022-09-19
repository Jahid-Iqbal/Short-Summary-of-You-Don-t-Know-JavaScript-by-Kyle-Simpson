# Strict Mode
>Following more appropriate set of guidelines in writing javascript programs.

The keyword `"use strict"` is used to define strict mode. Such a definition is under `directive prologue`. Strict mode makes it easier to write secure JavaScript. Because every time when you use bad syntax, it will convert it to real errors.

**Example:**  
Normal Mode:
```js
a=10;
console.log(a);     //10
```
Strict Mode:
```js
"use strict"
a=10;
console.log(a); //ReferenceError: a is not defined
```
In normal mode, JS engine declare the variable a as `var a=undefined;` implicitly but in strict mode doesn't do it. That's why showing `ReferenceError`.
