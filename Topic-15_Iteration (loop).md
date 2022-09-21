# Iterator and loops
>Iterator or loops are the easy and simple way to do a job repeatedly

There are many kinds of loops available. We will discuss some of them.

**`foor` loop::**  
A for loop iterates until a specified condition evaluates to `flase`. for loop use to iterates depending on below format.
```js
for([initialization]; [condition]; [increment]){
    statements
}
```
**initialization:**  
Some value need to be assigned to a variable. variable declaration and initialization happens here. Usually the value starts from 0. Such as,  
`var i=0;`

**Condition:**  
loop iterates depending on this condition expression. loop will continue as long as the condition is `true`. Such as,  
`i<5`

**Increment:**  
The increment or decrement operation executes here. Such as,  
`i++ or i--`.

Example:
```js
for(let i=0;i<5;i++){
    console.log(i);     // 0 1 2 3 4
}
```
Here, `let i=0` is initialization expression. loop starts traversing from value `i=0`. This initialization expression executes only once. Then check the condition whether `0<5`. If true then execute the statements `console.log(i);`. Then executes increment expression and now `i=1` then again check the condition `1<5`. If true then executes loop body.  
Execution steps:  
1. Initialization. Traverse only once.
2. checking condition.
3. statements
4. Increment  
Iteration-1: 1 2 4 3    i=0 condition: true  
Iteration-2: 4 2 3      i=1 condition: true  
Iteration-2: 4 2 3      i=2 condition: true  
Iteration-2: 4 2 3      i=3 condition: true  
Iteration-2: 4 2 3      i=4 condition: true  
Iteration-2: 2          i=5 condition: false  

**`for..in` loop:**  
`for..in` lop use to iterate over the indexes of an array and return the indexes.  

**Example:**
```js
var array=[10,20,30];
for(let keys in array){
    console.log(keys);          //0 1 2
    console.log(array[keys]);   //10 20 30
}
```
Here, the variable `keys` traverse on the indices of the array. In first iteration `keys=0` and prints that index number. `array[keys]` prints the value of that index. In second iteration, `keys=1` and in third iteration `keys=2`. So the final output is 0 1 2.

**`Iterator():`**  
Arrays have a built in iterator that iterates over the values of that array and return 2 parameter `value` and `done`. Value contains the value of the array and done contains a boolean value. iterator will traverse as long as `done: false`. Iterator is a property of `Symbol` object and iterates each time by calling the `next()` function.

**Example:**  
```js
var array=[5,6,7,8];
var it=array[Symbol.iterator]();
console.log(it.next()); //{value: 5, done: false}
console.log(it.next()); //{value: 6, done: false}
console.log(it.next()); //{value: 7, done: false}
console.log(it.next()); //{value: 8, done: false}
console.log(it.next()); //{value: undefined, done: true}
```

**`for..of` loop:**  
If you understand the `iterator` properly then you already almost understand the `for..of` loop. for..of loop iterates over the value depending on `Symbol.iterator` and return the value of the array.  

**Example:**
```js
var array=[5,6,7,8];
for(let keys of array){
    console.log(keys);  //5 6 7 8
}
```