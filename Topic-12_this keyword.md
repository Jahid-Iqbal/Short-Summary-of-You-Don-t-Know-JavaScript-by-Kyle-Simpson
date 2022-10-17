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

If you don't want to bother the function call or `this` reference then you can wrap the explicit call anyway. This way of wrapping is called **Hard Binding.**  
**Example:**
```js
function foo(){
    console.log(this.a);
}
var obj={
    a:42,
};
var bar=()=>{
    foo.call(obj);
    }
console.log(bar());     //42

```

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

**`this` in method:**  
If you call a function as a method of an object, `this` will refer to that object scope.
```js
var obj={
    myName: "Abdullah",
    display(){
        console.log("My name is "+this.myName);     //My name is Abdullah
    }
};
obj.display();
```
`display()` is a method of an object `obj`. `this` of that method referred to the variable `myName` of that object scope.

**call() vs apply():**  
Both the functions are used to implement explicit binding. A subtle difference is there. `call()` function accepts an object and some arguments as parameter but `apply()` function accepts an object and an array or arguments as parameter.

**`call():`**
```js
function foo(std1,std2,std3){
    return std1+this.marks1+"\n"+std2+this.marks2+"\n"+std3+this.marks3;
}
var obj={
    marks1:80,
    marks2:90,
    marks3:95,
};
console.log(foo.call(obj,"Abdullah ","Abdur Rahman ","Abdul Awal "));
// Abdullah 80
// Abdur Rahman 90
// Abdul Awal 95
```
Here, call function forced the function `foo` to referred the object `obj` and accepted another 3 arguments as parameter.

**`apply():`**
```js
function foo(std1,std2,std3){
    return std1+this.marks1+"\n"+std2+this.marks2+"\n"+std3+this.marks3;
}
var obj={
    marks1:80,
    marks2:90,
    marks3:95,
};
console.log(foo.apply(obj,["Abdullah ","Abdur Rahman ","Abdul Awal "]));
// Abdullah 80
// Abdur Rahman 90
// Abdul Awal 95
```
The `apply()` function forced the function `foo` to referred the object `obj` and accepted an array or arguments as parameter.

**`bind():`**  
When we pass a method as a callback to another function, there is always a risk of losing the intended receiver of the method, making the this argument set to the global object instead.  
The `bind()` method allows us to permanently tie a `this` argument to a value. In below code snippet, `bind()` function referred to object `obj` and always refer to the value of that object.
```js
var obj={
    myName:"Abdullah",
    display(){
        console.log("My name is "+this.myName); //My name is Abdullah
    }
};
setTimeout(obj.display.bind(obj),1000);
```
The `this` argument cannot be changed anymore even using `call()` or `apply()` function.

**`this` inside `setTimeout()` method:**  

`this` keyword return undefined when using inside the `setTimeout()` function.
```js
const str={
    value: 100,
    greet: function greet(){
        setTimeout(function (){
            console.log(this.value); //undefined
        }, 1000);
    }
}
str.greet();
```
You can solve the following problem using some techniques.

**Solution 01:** Using variable declaration.  `const self=this;`
```js
const str={
    value: 100,
    greet: function greet(){
        const self=this;
        setTimeout(function (){
            console.log(self.value);    //100
        }, 1000);
    }
}

str.greet();
```

**Solution 02:** Using `bind()` method
```js
const str={
    value: 100,
    greet: function greet(){
        setTimeout(function (){
            console.log(this.value);    //100
        }.bind(this), 1000);
    }
}
str.greet();
```

**Solution 03:** Using arrow function.
```js
const str={
    value: 100,
    greet: function greet(){
        setTimeout(()=>{
            console.log(this.value);    //100
        }, 1000);
    }
}

str.greet();
```

**`this` and `arrow` function:**  
this keyword refers to the global object while using inside the arrow function.
```js
const str={
    value: 100,
    greet: ()=>{
        console.log(this);      //Window
    }
}
str.greet();
```