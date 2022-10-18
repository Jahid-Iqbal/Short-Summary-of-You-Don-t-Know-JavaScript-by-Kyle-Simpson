# Array Destructuring

If you want to assign each element of an array to individual variable then you need to do the following

```js
const myArray=[1,2,3];
let elementA=myArray[0];
let elementB=myArray[1];
let elementC=myArray[2];
```
But ES6 introduces an easier way to do the same as follows
```js
const myArray=[1,2,3];
let [a,b,c]=myArray;
console.log(a,b,c);     //1 2 3
```
What if the number of variables is lees than the array size.

```js
const myArray=[1,2];
let [a,b,c]=myArray;
console.log(a,b,c);     //1 2 undefined
```
Assigning default value.

```js
const myArray=[1,2];

let [a,b,c=3]=myArray;

console.log(a,b,c);         //1 2 3
console.log(myArray[2]);    //undefined
```
Skipping some elements of the array
```js
const myArray=[1,2,3,4];

let [,a, ,b]=myArray;   //skipping the elements using blank space

console.log(a,b,);  //2 4
```
Rest parameter:

```js
const myArray=[1,2,3,4,5,6];

let [a,b,...c]=myArray;

console.log(a,b,c);     //1 2 (4) [3, 4, 5, 6]
```
Spread Operator:
```js
const myArray=[1,2,3,4,5,6];

let a=[...myArray];

console.log(a);     //[1, 2, 3, 4, 5, 6]
```

# Object Destructuring
If you want to assign each property of an object to individual variable then you need to do the following

```js
const object-{
    a:20,
    b:30
}
const propertyA=object.a;
const propertyB=object.b;
console.log(propertyA, propertyB);  //20 30
```
But ES6 introduces an easier way to do the same as follows

```js
const object={
    a: 20,
    b:30
};
const {propertyA,propertyB}=object;
console.log(propertyA,propertyB);       //20 30
```