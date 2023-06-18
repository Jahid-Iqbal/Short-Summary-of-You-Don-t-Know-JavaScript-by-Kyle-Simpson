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
