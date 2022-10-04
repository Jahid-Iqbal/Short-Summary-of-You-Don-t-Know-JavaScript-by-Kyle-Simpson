
# Asynchronous JavaScript

>Multiple functions running in parallel is called **Asynchronous**. Executing program sequentially but when it has a blocking call, it doesn’t wait rather executing next line. 

A good example of Asynchronous behavior in JavaScript is *setTimeout().*  

**Let's have a look on below code:**
```js
var porcessOreder=()=>{ 
    setTimeout(()=>{
        console.log("Task 2");
    },3000);     
}
console.log("Task 1");   
porcessOreder();                
console.log("Task 3");
```
Output:  
```output
Task 1
Task 3
Task 2
````
You can see, system executed the Task 3 prior to Task 2. Because system needed to wait 3000ms or 3 sec to execute the Task 2. So it executed the Task 3 rather waiting for Task 2. So Task 2 & Task 3 executed in parallel.

Picture

**Asynchronous manner:** System doesn’t get stuck for an individual task. It will perform some other task in between. Such as, a waiter can take order from customer 1 and placed to kitchen. Order is in progress. So waiter can take order from other customer as well. So multiple task is ongoing in parallel, which is the main goal of asynchronous programming. Execution happens in following below steps.  

**Call Stack:** Pushes all the execution steps in call stack. Execution happens depending on call stack following LIFO manner.

**Web API:** While browser found any async function then it will be pushed to Web API. Web API will determine the time and act accordingly. By this time call stack will proceed further. Web API counts the timer mentioned in setTimeout() function and pushes the task to callback queue after finishing the mentioned time.

**Callback Queue:** Storing the async functions pushed by Web API. Web API pushes to call stack using Event loop. Callback queue follows the FIFO manner.

**Event-Loop:** Comparing between callback queue and call stack to push the pending tasks to call stack from callback queue. When the call stack is empty then the inline functions or tasks will be pushed to call stack. Sometimes the async functions take more time then usual. Such as, hundreds of setTimeout() functions are waiting in callback queue but call stack is busy with some other tasks, so setTimeout() functions need to wait longer even after completing the mentioned waiting time.