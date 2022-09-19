# Closure
>Closure is such a technique by which a function can access the local variable of its parent functions in its lexical scope.

Let say, you want to make mango juice. So, two of the main ingredients are mango and sugar. You need to check first whether these elements are available or not. So, closure will hold this information.  
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

