# Hoisting
>JavaScript use to lift all the function and variable declarations on top of the code of its enclosing scope. Functions go to the very top, so will sit above all of the variable declarations.

**Example:**
```js
console.log(myName);        //undefined
var myName="Mr. Simpson";
function foo(){
    console.log("Hoisting case study");
}
foo();                      //Hoisting case study
```
After hoisting:
```js
var myName=undefined;       //variable hoisted to top
console.log(myName);
foo();                      //function hoisting
myName="Mr. Simpson";
function foo(){
    console.log("Hoisting case study");
}
```
Here, variable myName is declared and initialized right after the printing statement. So, system should print `Reference error` but print `undefined` instead. JavaScript engine lifted the variable declaration on top and assigned as `var myName=undefined;`. Initialization is not hoisted. Function `foo()` also hoisted.   
If any variables or functions are declared as `const` then that cannot be hoisted.  
**Example:**
```js
console.log(myName);    //Uncaught ReferenceError ReferenceError: Cannot access 'myName' before initialization
const myName="Mr. Simpson";
```
Anonymous functions also cannot be hoisted.  
**Usual case:**
```js
var func=function(){
    console.log("Am I hoisted?");
}
func();     //Am I hoisted?
```
**Hoisted:**
```js
func();     //Uncaught TypeError TypeError: func is not a function
var func=function(){
    console.log("Am I hoisted?");
}
```
Here, after hoisting `func()` lifted on top but showing TypeError as system treated `func` as a variable.

Consider the below Example. This code will be more understandable when you have clear view on [scope](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Topic-6_Scope.md).
```js 
//global scope
console.log(global);    //undefined
var global = 'now it is declared';

hoisting();

function hoisting(){    //block scope of function hoisting
  console.log(local);  //undefined
  var local = 'declared differently';
  
  console.log(local);      //declared differently
}                       //block scope ends

//global scope ends
```
Starting from the very top, when code is executed in Javascript, an execution context is set up. There are two major types of execution contexts in JS — Global execution context and Function execution context. Since Javascript is based on a single threaded execution model, only one piece of code can be executed at a time. For our code, the process is as follows :
The variable `local` is hoisted on top inside the function block and printed `undefined`. The `global` variable hoisted on top of global scope and printed `undefined`.