
# Callback in JavaScript

>Callback is a special kind of function that is passed as an argument to another function.

Suppose, you like to write a program to do calculation and display the result. You can save the result of a function `calculator` and pass it to another function `window` to display the results.
```js
function window(result) {
    console.log("Result= "+result)
  }
  function calculator(num1, num2) {
    let sum = num1 + num2;
    return sum;
  }
  let result = calculator(5, 5);
  window(result);
```
**Output:**
```output
Result= 10
```
You can also pass the value to `window` function by calling from inside `calculator` function.
```js
function window(result) {
    console.log("Result= "+result)
  }
  function calculator(num1, num2) {
    let sum = num1 + num2;
    window(sum);    //Calling function from inside calculator
  }
  calculator(5, 5);
  ```
**Output:**
```output
Result= 10
```
In 1<sup>st</sup> example both functions need to call separately and in 2<sup>nd</sup> example you can not prevent the calculator from displaying the result.  
Let's go to solve those problem by introducing **Callback**.
```js
function window(result) {
    console.log("Result= "+result)
  }
  function calculator(num1, num2, callback) {
    let sum = num1 + num2;
    callback(sum);
  }
  calculator(5, 5, window);     //Passing window function as argument.
```
**Output:**
```output
Result= 10
```
In these code snippet, `window` function is passed as an argument through `calculator` function. Here, any function can be passed as required or any manipulation can be done without touching the functions body.  

**Let's have another example:**
```js
var takeOrder=(customer,callback)=>{
    console.log("Order taken from "+customer);
    callback(customer);
}
var porcessOreder=(customer,callback)=>{
    setTimeout(()=>{
        console.log("Cooking completed of order of "+customer);
        console.log("Order processed for "+customer);
        callback(customer);
    },3000);
}
var completeOrder=(customer,callback)=>{
    console.log("Order served to "+customer);
    callback(customer);
}
var customerReview=(customer,review)=>{
    console.log(customer+" Review: "+review);
}
//Callback hell happened here
takeOrder("Mr. Simpson",(customer)=>{
    porcessOreder(customer,()=>{
        completeOrder(customer,()=>{
            customerReview(customer,"Excellent!");
        });
    });
});
```
**Output:**
```output
Order taken from Mr. Simpson
Cooking completed of order of Mr. Simpson
Order processed for Mr. Simpson
Order served to Mr. Simpson
Mr. Simpson Review: Excellent!
```
>Here, another problem is being created. When you will work with some giant program, you may need to call thousands of functions one inside another which will create a huge chain and that is very tough to maintain and won't be readable. That is called as **callback hell**.
```js
Callback Hell:

takeOrder("Mr. Simpson",(customer)=>{
    porcessOreder(customer,()=>{
        completeOrder(customer,()=>{
            customerReview(customer,"Excellent!");
        });
    });
});
```
To solve this callback hell problem JavaScript introduced [promise](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Topic-23_Promise.md). We will discuss in different session.