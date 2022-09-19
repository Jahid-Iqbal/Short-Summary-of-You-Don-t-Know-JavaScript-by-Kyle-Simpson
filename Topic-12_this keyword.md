# `this` Keyword
>`this` is a keyword in JavaScript that use to point or refer objects or variables in various scope depending on function call. `this` keyword is concerned on from where the function is invoked.

**Different types of function call and working process of `this`:** 

**Default Binding:**   
If you use `this` inside a function then that will refer to global scope or. In case of strict mode it returns `undefined`.
```js
function foo(){
    console.log(this.a);    //10
}
var a=10;
foo();
```
Here, inside the function `foo` this.a used. that `this` referred to the global scope. That's why got the value of `a=10` which defined in global scope.

**Implicit Binding:**  
If you use `this` inside a function and that function is called from an object then `this` will refer to that object.
```js
function foo(){
    console.log(this.a);
}
var obj={
    a:42,
    foo:foo
};
console.log(obj.foo());     //42
```
Function `foo` contained a `this` and that function is called from an object `obj`. So, the `this` keyword referred to that object `obj` and fetch value of `a`.

**Explicit Binding:**  
If a function contains `this` keyword and you externally force that function to point an individual object using some built in functions then `this` keyword will refer that object.
```js
function foo(){
    console.log(this.a);
}
var obj={
    a:42,
};
console.log(foo.call(obj));     //42
```
The function `foo` is forced to point the object `obj` using default function `call()`.

**`new` Binding:**  
If you instantiated a function using `new` keyword then the variable gets the reference of that function. The `this` keyword refers to the newly created object.
```js
function foo(a){
    this.a=a;
}
var bar =new foo(2);
console.log(bar.a);     //2
console.log(bar.valueOf(a)) //foo {a: 2} 
```
Variable bar got the reference of function `foo` using `new` keyword. so `bar.a` got the value of function `foo`. Actually the `this` keyword referred to the prototype of that function. As `bar` got the reference of function `foo`, so `bar` also can access that value.