# Scope
>Scope in JavaScript refers the range or boundary where variables or methods live or visible or accessible.

Such as,
```js
var a=10;
function foo()
{
    var a=100;
    console.log(a);
}
foo();              //100
console.log(a);     //10
```
Here, a defines inside and outside of the function. `a=100;` is visible or accessible only inside the function body which means that function body is the scope for `a=100`.  
Javascript hs global scope, module scope, function scope, block scope and lexical scope.  
### Global Scope:
Variable defined outside the block or function have global scope. Variables in global scope can be accessed from anywhere in that application.
```js
var a=10;
function foo()
{
    console.log(a); //10
}
foo();
console.log(a);     //10
```
Here, a is defined in global scope and can be accessed fom inside the function body of function scope.  
Another way of creating global variable is to use `window` object.
```js
window.a=10;
function foo()
{
    console.log(a); //10
}
foo();
console.log(a);     //10
```
Please note that this practice is a bad practice.  
### Function Scope:
Function scope refers the parameter and variable defined inside the function are visible anywhere within the function.  
```js
var a="Outside the function";
function scope()
{
    var a="Inside the function"
    console.log(a);     //Inside the function
}
scope();
console.log(a);         //Outside the function
```
Here, variable a is defined inside the function `scope()` and can be accessed only inside the function body. Outside the function printing a which is declared in global scope.
### Block Scope:
Block scope is defined with curly braces {}. Variables declared inside the block are visible everywhere of that block scope.

Javascript is function scoped whereas other languages are block scoped.
```js
// C language has block scope
int a=1;
{
    int a=5;
    printf("%d", a);    //5
}
printf("%d", a);        //1
```
```js
// JavaScript has not block scope
var a=1;
{
    var a=5;
    console.log(a);     //5
}
console.log(a);         //5
```
In ES6, JavaScript introduced new variable types `let` and `const`. Those are block scoped.
```js
let a=1;
{
    let a=5;
    console.log(a);     //5
}
console.log(a);         //1
```
### Lexical Scope:
The ability of accessing the variables that are defined in outer scope from inner functions or block.
```js
function scope()
{
    var a="Inside the function scope"
    console.log(a);     //Inside the function scope
    (function innerFunction(){
        console.log(a); //Inside the function scope
    })();
}
scope();
```
Here variable a is defined in the scope of function `scope()`. Still that variable is visible inside the function `innerFunction()`. variables are defined in outer scope can be accessed from inner scope as well.
### Scope Chaining:
Every scope has a link with corresponding parent scope. JavaScript searches a variable through the parents scope maintaining a chain. That manner is called scope chaining.
```js
var global="Global";
(function chain1(){
    c1="Chain 1";
    (function chain2(){
        c2="Chain 2";
        (function chain3(){
            c3="Chain 3";
            console.log(c3+"=>"+c2+"=>"+c1+"=>"+global);    //Chain 3=>Chain 2=>Chain 1=>Global
        })();
    })();
})();
```
The `chain3()` function can access the local variable `c2`,`c1` and even global variable `global`. Here, the scope of `chain3()` function maintain the the chain to find out the required variable towards chain2, chain 1 and global.