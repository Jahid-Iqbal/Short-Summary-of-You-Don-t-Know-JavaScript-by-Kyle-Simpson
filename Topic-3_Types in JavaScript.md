# Types in JavaScript
>"JavaScript has typed values, not typed variables."  

Means, you don't need to declare the variable with specific type. You can declare variable like `var a;`. Here you don't need to declare, what kind of value (number, string etc.) you want to store in a. Each value holds its type. Variable will act accordingly as the value type. Such as, `var a=10;` here variable a will act as number as the value (10) type is number. `var s="string";` s is of string type.

>JavaScript uses the latter approach, dynamic typing, meaning variables can hold values of any type without any type enforcement.

**Available types in JavaScript:**  
*Primitive types:*  
number  
string  
boolean  
null  
undefined  
symbol  
*Non-Primitive types:*  
object

***typeof:*** Checking the type of a value/ variable.
```js
var a=10;
typeof a;   //number
```
**undefined vs undeclared:**  
Variable that has no value assigned yet is showing *undefined*.  
```js
var a;	
typeof a;	//undefined
```
The variable that has not been declared on that scope showing *undeclared.*  
```js
b;	
typeof b;   //Refferenceerror: b is not defined	
```
### Falsy & Truthy: 
Some values use to show result as “false” always. Other than the mentioned list all values will be true.
**Falsy list:**  
“”  
0, -0  
NaN  
null & undefined  
false  

