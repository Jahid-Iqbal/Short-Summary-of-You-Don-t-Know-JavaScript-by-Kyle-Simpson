# Modules
>Module is the technique that allows us to perform a specific task using resources of different js files by importing them.

**Diagram:**  
![Photo](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/modules.png)  
**"main.js"**
```js
import {a} from './variables.js'
console.log(a);     //10
```
**variables.js**
```js
export var a=10;
```
You can import the variables from the `variables.js` file. Only those variables or functions can be imported whom have the `export` permission. Make sure to create a `package.json` file and add `{"type": "module"}`.

A module can be exported or imported in various ways. Such as,  

**Named Export:**  
Write down the keyword `export` to allow other files to access that resources. Use the resource name to import the files.
```js
//exportModule.js
export var foo= function(x,y){
    return x*y;
}

//importModule.js
import {foo} from './exportModule.js'
console.log(foo(2,4));      //8
```
**Default Export:**  
Use the key word `default` after `export`. A file can hold only one default value. You can named it while importing.
```js
//exportModule.js
export default "My name is Abdullah";

//importModule.js
import myName from './exportModule.js'
console.log(myName);    //My name is Abdullah
```
**Default and Named Export:**  
```js
//exportModule.js
export default "My name is Abdullah";
export var foo= function(x,y){
    return x*y;
}

//importModule.js
import myName,{foo} from './exportModule.js'
console.log(myName);    //My name is Abdullah
console.log(foo(5,5));  //25
```
**List Export:**  
declare the resources as normal process and make a block of `export`.
```js
//exportModule.js
var value=10;
var foo= function(x,y){
    return x*y;
}
export{
    value,
    foo
}

//importModule.js
import {value,foo} from './exportModule.js'
console.log(value);
console.log(foo(5,5));
```
**Rename Import:**  
You can rename the resources while importing. use keyword `as` to rename the resource. Like as `value as number`. The variable exported as `value` but imported as `number`.
```js
//exportModule.js
var value=10;
var foo= function(x,y){
    return x*y;
}
export{
    value,
    foo
}

//importModule.js
import {value as number,foo} from './exportModule.js'
console.log(number);    //10
console.log(foo(5,5));  //25
```
**Rename Export:**  
Rename the resources name using `as` while exporting. In below code, a function implemented as `foo` but export as `func`.
```js
//exportModule.js
var value=10;
var foo= function(x,y){
    return x*y;
}
export{
    value,
    foo as func
}

//importModule.js
import {value,func} from './exportModule.js'
console.log(number);    //10
console.log(func(5,5));  //25
```
**Import All:**  
Use the symbol `*` to import all resources of a file those have export permission. Need to allies the all operator which will represent the exported file. In below code, `all` is representing the file `exportModule.js`
```js
//exportModule.js
var value=10;
var foo= function(x,y){
    return x*y;
}
export{
    value,
    foo as func
}

//importModule.js
import * as all from './exportModule.js'
console.log(all.value);     //10
console.log(all.foo(5,5));  //25
```
