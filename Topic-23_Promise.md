# Promise
>Intending to complete a task which can be success or rejected.

Let say, Abdullah made a promise to his manager to complete the project by the deadline. He might complete the task within the deadline or fail to do so.  

`Promise()` accepts an anonymous function and that function accepts 2 parameter. First parameter is success and second one is reject. In calling the promise then() function passed an anonymous function with a parameter. The then() function invoked the success and the catch() function invoked the reject internally.

```js
var meetDeadline=false;
let promise=new Promise(function(resolve,reject){
    if (meetDeadline)
        resolve("Project completed within deadline");
    else
        reject("Project didn't complete within deadline");
});

promise
.then(function(value){
    console.log(value);
})
.catch(function(error){
    console.log(error);
});
```
Example using multiple then() functions. You can use only one catch() against all then.
```js
var statusP=true;
var marks=90;
function enroll(){
    let promise=new Promise(function(resolve,reject){
        setTimeout(function(){
            if(statusP)
                resolve();
            else
                reject("Payment not successful.");
        });
    });
    return promise;
}
function progress(){
    let promise=new Promise(function(resolve,reject){
        setTimeout(function(){
            if(marks>80)
                resolve();
            else
                reject("You failed");
        });
    });
    return promise;
}
function certified(){
    let promise=new Promise(function(resolve,reject){
        setTimeout(function(){
            resolve("Congratulations! You are certified.");
        },2000);
    });
    return promise;
}
enroll()
.then(progress)
.then(certified)
.then(function(value){
    console.log(value);
})
.catch(function(error){
    console.log(error);
});
```