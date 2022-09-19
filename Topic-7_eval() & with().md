# _eval()_ Function
>The eval() function evaluates javascript code represented as a string and return its completion values.
```js
eval(string:any)
```
eval function accepts a parameter of string type. It accepts javascript expression or code. It can be single or multiple statements even sequence of expressions.  
**Example:**
```js
function foo(str){
    eval(str);
    console.log(a,b,c);     //10 20 30
}
foo("var a=10;var b=20;var c=a+b");
```
Here, a sequence of statements passed as parameter to `eval()` function. Those statements executed inside eval and the return the results.  

**Not to use eval() function is recommended**  
* With eval(), malicious code can run inside the application without permission.
* With eval(), third party code can see the scope of the application.

# _with()_ Function
>with is used to make multiple property reference against an object without repeating the object reference itself each time.


```js
var personalInfo={
    personName: "Abdullah",
    age: 28,
    city: "Dhaka"
};
console.log(personalInfo);  //{personName: 'Abdullah', age: 28, city: 'Dhaka'}
personalInfo.personName="Abdur Rahman";
personalInfo.age=35;
city="Noakhali";
console.log(personalInfo);  //{personName: 'Abdur Rahman', age: 35, city: 'Dhaka'}
```
Here, an object `personalInfo` is declared to save multiple persons information. But problem is every time you need to use the object reference to save a new person's data. You can use `with()` function to avoid making reference of an object each time for individual person.  
**Example:**
```js
var personalInfo={
    personName: "Abdullah",
    age: 28,
    city: "Dhaka"
};
console.log(personalInfo);  //{personName: 'Abdullah', age: 28, city: 'Dhaka'}
with(personalInfo){
    personName="Abdur Rahman";
    age=35;
    city="Noakhali";
}
console.log(personalInfo);  //{personName: 'Abdur Rahman', age: 35, city: 'Noakhali'}
```
This time you can do the same task using `with()` function. You just need to pass the object as parameter and then initialize the variables.

**Variable lick scenario:**  
The `with` statement adds the given object to the head of the scope chain during the evaluation of its statement body.  
**Example:**
```js
function foo(obj){
    with(obj){
        a=5;
    }
}
var obj={
    b:71
};
console.log(a); //ReferenceError: a is not defined
foo(obj);
console.log(obj.a); //undefined
console.log(a);     //5 as with() function lifted the variable a to the global scope.
```
Here, object `obj` is defined with a variable b and passed through `with()` function as parameter. Inside `with` functions body variable `a` initialized. JavaScript engine tried to find out the source reference for variable `a`. When did't find under object `obj` then continued searching in scope chain and ended in global scope. That's why the variable a would be visible in global scope.

**The `with()` function is no longer recommended to use as it may lead some confusing bugs and compatibility issues.**