# Closure
>Closure is such a technique by which a function can access the local variable of its parent functions in its lexical scope.

A closure is being created when a function is declared.  

**Example:**  
Let say, you want to make mango juice. So, two of the main ingredients are mango and sugar. You need to check first whether these elements are available or not. So, closure will hold this information for you.  
**Let's implement the scenario in JavaScripts code.**
```js
var season="Summer";
(function checkMango(){
    var mango=true;
    (function checkSugar(){
        var sugar=true;
        (function makeJuice(){
            var juice=true;
            if(mango&&sugar&&juice){
                console.log("All ingredients are available as this is "+season+"season");
            }
        })();
    })();
})();
```
![Execution process](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/closure.png)

Here, just look at the code and the snap. You want to make juice under function `makeJuice()`. Function `makeJuice()` required the value of variables `mango`,`sugar` , `juice` and `season`. Just follow the snap, `season` belongs to global scope, so the closure holds the value `season: 'Summer'`. `mango` belongs to the function scope of `checkMango`,so Closure (checkMango) holds the value`mango:true`. `sugar` belongs to the function scope `checkSugar`, so Closure (checkSugar) holds the value `sugar:true`.  
So, for each function a closure is assigned and hold the necessary information for further use.

**Closure provides both read and write access:**  
Closure provide the reference of the variables. So, you can modify that variable as well.
```js
var season="Summer";
(function checkMango(){
    var mango=true;
    function checkSugar(){
        mango=false;
    }
    checkSugar();
    console.log(mango);     //false
})();
```
The Closure (checkMango) holds the value `mango=true` and provided the reference to the function `checkSugar`. So, inside function `checkSugar` the variable mango re-assigned as `mango=false`. You can see from the code the value of `mango` changed in source. That's why after executing `checkSugar` function, value of variable `sugar` changed.

**Closure in loop:**  
Closure works behind the loop iterations as well.
```js
for(var i=0;i<5;i++){
    /*........*/
}
```
The for loop iterates 5 times starting from 0. So, every time the value of i is incremented. But who holds the value of `i` ???  
Closure holds the value of `i`. A closure created behind the loop and holds the value of `i`. If i is declared with `var` then closure holds a single `i` and increment that. So, previous value is erased. But if declared with `let` then every time it declared a new `i` and assign the value.

**Example:**

```js
var funcs = [];
for (var i = 0; i < 3; i++) {
  funcs[i] = function() {
    console.log("My value:", i);
  };
}
for (let j = 0; j < 3; j++) {
  funcs[j]();
}
```

**Q. How JavaScript engine determines which value need to store in closure?**

**Answer:** In JavaScript, closures are created when a function is defined within another function and the inner function refers to variables from the outer function's scope. The concept of closures allows the inner function to maintain access to those variables even after the outer function has finished executing.

When a JavaScript engine encounters a function that uses variables from its parent scope, it determines which values need to be stored in the closure by analyzing the function's lexical environment. The lexical environment is an internal data structure that contains all the variables and their values within a particular scope.

When a function is defined, the JavaScript engine creates a closure, which consists of the function's code and a reference to its lexical environment. This closure is created in memory, allowing the inner function to access variables from the outer function's scope.

The JavaScript engine analyzes the inner function's code to determine which variables are referenced inside it. If a variable is referenced, the engine checks if the variable is defined within the inner function's scope. If not, it checks the outer scope, and this process continues until it finds the variable or reaches the global scope.

Once the JavaScript engine identifies the variables that are referenced by the inner function but are not defined within its own scope, it includes those variables in the closure. This means that the values of those variables will be preserved, even if the outer function has finished executing.

The process of determining which values to store in a closure is based on the lexical scoping rules of JavaScript. It ensures that the inner function has access to the variables it needs, even if those variables are not directly defined within its scope.

**Q. what is lexical environment?**

**Answer:** A lexical environment is an internal data structure used by JavaScript engines to keep track of variables, functions, and their scopes during the execution of a program. It defines the association between variable names and their corresponding values within a specific scope.

In simpler terms, a lexical environment represents the environment or context in which a piece of code is executed. It consists of two main components:

- **Environment Record:** It is a record of all the variables, functions, and their respective identifiers (names) defined within the scope. The environment record acts as a storage container for these identifiers and their values.

- **Outer Environment Reference:** It refers to the lexical environment of the outer (enclosing) scope. This reference allows for the concept of nested or nested scopes, where an inner scope has access to variables and functions defined in its outer scopes.

The lexical environment is created during the creation phase of the execution context for a function or block of code. It is used to resolve variable and function references during the execution phase. When a variable is accessed or modified, the JavaScript engine consults the lexical environment to find the appropriate identifier and its associated value.

Lexical scoping refers to the concept that the visibility of variables is determined by their location or position in the source code. In other words, variables are resolved based on their lexical (static) context rather than the runtime context.

Lexical environments play a crucial role in enabling features such as closures, where an inner function retains access to variables in its parent scope even after the parent function has finished executing. The lexical environment ensures that the inner function can still reference and access those variables through the closure's reference to its parent's lexical environment.

**Q. How the value of a determines or stored in below code snippet?**

```js
function foo(){
    var a=10;

    function bar(){
        console.log("b="+b);
        var b=1055;
        function laila(){
            var c;
            console.log(c);
        }
        laila();
    }

    bar();

    console.log(a);
}
foo();
```

In the given code snippet, the value of variable `a` is determined and stored in the lexical environment of the `foo` function.

When the `foo` function is executed, a new execution context is created for it, including its own lexical environment. Within this lexical environment, the variable `a` is declared and assigned the value `10`.

The `bar` function is defined within the `foo` function's scope. When the `bar` function is invoked, a new execution context is created for it, with its own lexical environment. The lexical environment of `bar` includes a reference to the lexical environment of its parent scope, which is the lexical environment of `foo`.

Inside the `bar` function, there is a console.log statement that references the variable b before it is declared. This is called a `"hoisting"` behavior in JavaScript, where variable declarations are moved to the top of their scope during the compilation phase. However, the assignment (var b = 1055;) is not hoisted, so the value of b will be undefined at that point in the code.

When the `laila` function is defined within the `bar` function, it also gets its own lexical environment. However, since there are no variables defined within the `laila` function that reference the outer scope, the value of a is not directly stored in the lexical environment of `laila`.

After the `bar` function finishes executing, the execution context is popped off the call stack, but the lexical environment of `foo` remains intact. Therefore, the value of a is still stored within the lexical environment of `foo`.

Finally, the console.log(a) statement outside the `bar` function outputs the value of a as 10, as it accesses the variable a from the lexical environment of the `foo` function.

In summary, the value of a is determined and stored within the lexical environment of the `foo` function and remains accessible even after the execution of the `bar` function.

