# IIFE (Immediately Invoked Function Expression)

>IIFE is a pattern in javascript that is used to execute a function just after the declaration. No need to call or invoke the function externally. Declaration and execution happen consecutively.

Example:
```js
(function(){
    console.log("Hello dear. I am IIFE.");
})();
```
Here, the function is declared and executed consecutively. Not required to call from somewhere else. The JS engine executes the function just right after the parenthesis `()`.

Another example:
```js
(function(){
    var myName="Abdur Rahman";
    function displayName(myName){
        console.log("My name is "+myName);
    }
    displayName(myName);
})();
```
As you can see, all the functions and required variables are declared inside the IIFE. So, the global scope won't be affected anyhow.