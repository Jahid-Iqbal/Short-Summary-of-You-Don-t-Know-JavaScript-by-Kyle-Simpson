# Arrays
>Array is such a mechanism by which a collection of items can be stored in an individual variable.

```js
var array=[1,2,3];
```
**Why Array?**  
If you want to store 3 values then you will be required 3 variables declaration. Such as, `var a=1`. Using array you can store all three values to a single variable.  

**Creating an Array:**  
```js
const array_name=[value1, value2, value3,.....];
```
**Example:**
```js
const id=[101, 102, 103];
const name=["Ahmad","Abdullah","Abdur Rahman"];
```
You can also create an empty array and then assign values.
```js
var programmingLanguage=[];

programmingLanguage[0]="JavaScript";
programmingLanguage[1]="Java";
programmingLanguage[2]="Python";

console.log(programmingLanguage);   //['JavaScript', 'Java', 'Python']
```
Using JavaScript keyword `new`
```js
var programmingLanguage=new Array("JavaScript","Java","Python");

console.log(programmingLanguage);   //['JavaScript', 'Java', 'Python']
```

**Append Array Elements:**  
You can append or add new elements to an array using `array_name.push()`.
```js
var array=[1,2,3];
array.push(4);
console.log(array); //[1, 2, 3, 4]
```

**Accessing arrays elements:**  
You can access the elements of an array using the index number. Array index starts from 0.
```js
var river=["Padma", "Jamuna", "Meghna"];
var content=river[1];
console.log(content);
```
**Updating Arrays Contents:**  
You can update or replace the individual content of an array.
```js
var river=["Padma", "Jamuna", "Meghna"];
river[1]= "Sondha";

console.log(river);     //['Padma', 'Sondha', 'Meghna']
```
Arrays are special type of object. You can check the type of an array using keyword `typrof`.
```js
var river=["Padma", "Jamuna", "Meghna"];

console.log(typeof river);     //object
```
**Arrays contents can hold object as value:**  
Each content of an array can hold a object. Like, a content is holding functions value another is holding objects value. In below code, array[0] is holding a functions value, array[1] is holding the value of a built in function and array[2] is holding a regular value.

```js
function foo(){
    return 10*10;
}
var array=[];
array[0]=foo();
array[1]=Date.now();
array[2]="Cars";

console.log(array);     //[100, 1663768375574, 'Cars']
```
**Array length:**  
You can find out the length of the array using `array_name.length`.
```js
var array=[1,2,3,4];
var length =array.length;

console.log(length);    //4
```