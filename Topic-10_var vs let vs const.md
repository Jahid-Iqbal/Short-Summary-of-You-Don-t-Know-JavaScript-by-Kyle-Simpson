# `var` vs `let` vs `const`
ES2015 or ES6 introduced two new ways to create variables. Those are `let` and `const`.  
**Scope:**  
`let` is block scoped whereas `var` is function scoped. Look on below 2 examples. same example is used for both types to show the difference.  
In first example a `var` variable is initialized inside the `if` block and can be accessible from out side that block but inside that function `foo` only.  
In second example, a `let` variable is initialized inside the `if` block and that cannot be accessible from outside that block.  
**Example:**
```js
//var example
function foo(){
    var a=true;
    if(a){
        var value=a;
        console.log(value);     //true
    }
    console.log(value);         //true
}
foo();
console.log(value);         //Uncaught ReferenceError ReferenceError: value is not defined
```
```js
//let example
function foo(){
    let a=true;
    if(a){
        let value=a;
        console.log(value);     //true
    }
    console.log(value);         //Uncaught ReferenceError ReferenceError: value is not defined
}
foo();
```
**Re-declaration:**  
`var` variables can be re-declare anywhere in that application but `let` variables cannot.
```js
(function(){
    //var example
    var a=true;
    if(a){
        console.log(a)  //true
    }
    var a=false;
    console.log(a);     //false
    //let example
    let b=true;
    console.log(b);
    let b=false;
    console.log(b);     //SyntaxError: Identifier 'b' has already been declared
})();
```
Here, you can see the `var` variable is re-declared as `var a=false;` and that can be executed normally. But when let is re-declared as `let b=false;` then system showed `SyntaxError`.  
**Hoisting:**  
`var` variables can be hoisted but `let` variables cannot. If you are not aware of Hoisting yet then look on the topic [Hoisting](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Topic-5_Hoisting.md).
```js
console.log(a);     //undefined
var a=10;
console.log(b);     //Uncaught ReferenceError ReferenceError: Cannot access 'b' before initialization
let b=100;
```
In these code, a is declared as `var` and initialized after printing statement but JS engine hoisted the variable to top of the application and print `undefined`. variable b is declared as `let` and initialized after the printing statement. As a result, system has shown `ReferenceError` as variable b can't be hoisted.  

## `const`
>Variable declared with const, maintain the constant values. That variable cannot be updated anymore through out that block scope.

* variables declared with `const` cannot be re-declared and hoisted.

```js
console.log(h);     //Uncaught ReferenceError ReferenceError: Cannot access 'h' before initialization
const h=100;
(function(){
    var a=true;
    if(a){
        const value=false
        console.log(value)  //false
    }
    const value=true;
    console.log(value);     //true    
})();
```
In above code, variable h is shown `ReferenceError` as can't be hoisted. Variable `value` can be declared outside the `if` block as this is block scoped.