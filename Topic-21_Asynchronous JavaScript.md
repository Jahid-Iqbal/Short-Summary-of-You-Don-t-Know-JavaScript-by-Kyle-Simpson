
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
