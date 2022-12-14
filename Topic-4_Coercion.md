# Coercion
>Conversion between types is called Coercion.

There are two types of coercion:  
**Explicit Coercion:** Converting the types from one to another forcefully or using some functions are called Explicit Coercion.  
Example:  
```js
var s= "2022";
var n= Number(s);   //2022
```
**Implicit Coercion:** JavaScript engine use to do some conversion internally for doing some operations, that is called Implicit coercion.  
Example:
```js
var a=40;       //Number
var b="40";     //String
a==b;           //true
```
Here, string value is converted to number internally. `Number("40")` is 40.

**Explicitly Implicit Scenario:**
```js
var a= "71";
var b=a.toString();     //'71'
```
Here, 71 is a primitive value so `toString()` function should not work on variable a but it's worked. Because primitive value is boxed in an object wrapper implicitly and then that value coerced to string explicitly using `toString()`. That's why this scenario is called as Explicitly Implicit coercion.

**Type Coercion:**  
JavaScripts engine doing some automatic or implicit conversion of values from one type to another to perform operations is called Type Coercion.  
**Examples:**
```js
10+'10';    //1010
10-'10';    //0
```
**Type Coercion with + operator:**  
When adding two or more operands with + operator then JS engine performing addition operation. But if any of the operands is of string type then the integer value coerced/ converted to string and the do concatenation.  
**Example:**
```js
10+10+'22';	        // ‘2022’
10+10+20+'12'+'34';	// ‘401234’
null+'';            //'null'
null+undefined      //NaN
```
**Type coercion with - operator:**  
When performing subtraction operation, if any string value is there then that would be converted to number.  
**Example:**
```js
10-'10';    //0
100-'20';   //80
```
**Some strange coercion:**
```js
''-1;           //-1 as Number('') is 0
false-true;     //-1 as parsing false as 0 and true as 1.
null+10;        //10 as Number(null) is 0.
true=='true';   //false as Number(true) is 1 but Number('true') is NaN.
{}=={};         //false as objects compared by their reference not values.
null==undefined;//true as Boolean(null) is false and Boolean(undefined) is false.
```
### JSON.stringify():
Cover the value with quotation (''). Any JSON-safe value can be stringified. functions, objects, undefined and Symbol are not JSON-safe.  
Example:
```js
JSON.stringify(3);	    // '3'
JSON.stringify("3");	// '"3"'
```
A second parameter can be passed in `stringify()` function. That parameter can be either an array or function.  
**Passing an array (array of string) as parameter.** Here, a,b,c,d represent the properties of the object in serialized manner.  
```js
var object={
    a: 10,
    b: 20,
    c: [30,40,50]
};
JSON.stringify(object,[a,b,c,d]);    //{"a":32,"b":"43","c":[1,2,3]}
```
**Passing function as parameter.** That function accepts two parameter keys(k) and value(v). function traverse on that object where keys(k) traverse on the index and value(v) contains the content of that corresponding key. If any of the property of that object contains array then the key(k) traverse on individual index of that array as well.
```js
var object={
    a: 10,
    b: 20,
    c: [30,40,50]
};
JSON.stringify(object,function(k,v){
    if (k!==b)
        return v;   //{"a":32,"c":[1,2,3]}
});
```
A third parameter can be passed in `stringify()` function. That parameter can be either a number or string. If number then that number of white space prior to each line and if string then that string will be prior to each line. Max string size can be 10 char.
```js
var obj={
    a:32,
    b:"43",
    c:[1,2,3]
};

console.log(JSON.stringify(obj,null,5));
```
**Output:**
```
{
     "a": 32,
     "b": "43",
     "c": [
          1,
          2,
          3
     ]
}
```
**Comparison:**  
In comparison if two values are of different types like one is of number type and another is of string type then string need to be coerced into number.  
**Example:**
```js
var a=10;
var b="45";
b>a;        //true as b coerced to number
```
**Interesting Coercion:**  
`3==50;  //true`
Strange. How can it be possible????
```js
Number.prototype.valueOf= function(){
    return 3;
}
var a=new Number(50);
console.log(a==3);      //true
```
Here, `valueof()` is an object of `Number.prototype` which use to return primitive value of specified object. The object converted to a primitive data type. So, an implicit coercion is happening. `valueof()` is forced to return a specific value. That's why whatever value is passed to `Number()` function it returns the externally assigned value. So, when `var a=new Number(50);` is executed, the `valueof` function returns 3 and `a==3` is returning true.  
Same scenario happened in below program as well.
```js
var i=1
Number.prototype.valueOf= function(){
    return i++;
}
var a=new Number(50);
console.log(a==1&&a==2&&a==3);     //true
```
`a==1&&a==2&&a==3` is true. This is so funny. But actually that is possible. Here `valueof` returns value of i started from 1. Every time value incremented by one. That's why in first call `valueof` return 1 and then incremented to 2. In second call return the value 2 and incremented to 3 and so on.

**Output of `&&` and `||` Expressions:**
```js
let a=100;
let b=200;
let c="Last variable";
console.log(a&&b&&c);   //Last variable
console.log(a||b||c);   //100
```
In case of `&&` system will print the first false value. Such as if a is falsy then prints the value of a or if b is falsy but a is truthy then print the value of b. In case of `||` print the first true value. Such as if a is truthy then prints the value of a or if b is truthy but a is falsy then print the value of b.