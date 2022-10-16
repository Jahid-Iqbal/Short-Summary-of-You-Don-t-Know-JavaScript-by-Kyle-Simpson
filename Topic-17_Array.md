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

**`push()` and `pop()`:**  
You can append or add new elements to an array using `array_name.push()`. The added item will always append at the end of the array.  
You can also delete array element using `pop()`. Last element of the array will be deleted.  
If you want to delete any item from the beginning then use `shift()` method and also add an element at the beginning with `unshift()` method. Function `unshift()` accept an element as parameter what you want to add and return the length of the array. `shift()` method return the deleted item.
```js
var array=[1,2,3];
array.push(4);
console.log(array); //[1, 2, 3, 4]
var poppedItem=array.pop();
console.log(array);
console.log("Popped item= "+poppedItem);    //4
var shiftedItem=array.shift();
console.log("Shifted item= "+shiftedItem);    //1
console.log(array);    //[2, 3]
var unshiftedItem=array.unshift(5);
console.log("Popped item= "+shiftedItem);    //3
console.log(array);    //[5, 2, 3]
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
**Deleting elements of Array:**  
You can delete the value of an specific index using `delete` keyword.
```js
var array=[1,2,3,4];
delete array[1];
console.log(array);     //[1, empty, 3, 4]
```
**Merging or concatenating two Arrays:**   
You can merge two arrays using `concat()` function. This function returns a new array and don't bother the existing arrays.
```js
var fruits1=["Mango","Banana"];
var fruits2=["Blueberry","Watermelon"];
var fruitsList=fruits1.concat(fruits2);
console.log(fruitsList);                //['Mango', 'Banana', 'Blueberry', 'Watermelon']
```
**`splice():`**  
You can add and remove items at a time using the function `splice()`. This function accepts 3 parameter like `splice(parameter1, parameter2, parameter3)` and returns an array of containing the deleted items.  
`parameter1` is the index number where you want to add new elements.  
`parameter2` is the number of elements you want to remove. If parameter1 is 0 means no addition then it removes from the beginning of the array but if parameter1 is some value like 2 then it will start removing from that index.  
`parameter3` is the value you want to add in the mentioned index in parameter1.
```js
var fruits1=["Mango","Banana"];
var fruits2=["Blueberry","Watermelon"];
var fruitsList=fruits1.concat(fruits2);
console.log(fruitsList);                //['Mango', 'Banana', 'Blueberry', 'Watermelon']

fruitsList.splice(2,0,"Apple","Orange", "Lemon");   ////['Mango', 'Banana', 'Apple', 'Orange', 'Lemon', 'Blueberry', 'Watermelon']
var deletedItem= fruitsList.splice(0,2);            ////['Mango', 'Banana', 'Apple', 'Orange', 'Lemon', 'Blueberry', 'Watermelon']
console.log("Deleted Item= "+deletedItem);  //Mango,Banana
fruitsList.splice(2,2, "Kiwi");         //['Apple', 'Orange', 'Kiwi', 'Watermelon']
```
Here,  `splice(2,0,"Apple","Orange", "Lemon")` means at index 2 the mentioned elements ("Apple","Orange", "Lemon") will be added. and no element will be removed as the parameter2 is 0.  
`splice(0,2)` means 2 elements will be removed from the beginning of the array as parameter1 is 0 or no addition.  
`splice(2,2, "Kiwi")` means 2 elements will be removed first starting from index 2 as parameter1 is 2 and then add an element ("Kiwi") at index 2.

**`slice():`**  
If you want to take a portion of an array then `slice()` function can be used. This function accepts 2 parameter like `slice(parameter1, parameter2)` and returns an array containing the section of an array.  
parameter1 is the starting index of the specified portion of the array. It can be negative value as well. Like as, -2 means the second element from the last index of the array.  
parameter2 is the ending index of the specified portion of the array. It can be negative as well. Like as, -2 means the second element from the last index of the array.

```js
var fruits1=["Mango","Banana"];
var fruits2=["Blueberry","Watermelon"];
var fruitsList=fruits1.concat(fruits2);
console.log(fruitsList);                //['Mango', 'Banana', 'Blueberry', 'Watermelon']
var slicedArray=fruitsList.slice(1,3);
console.log(slicedArray);               //['Banana', 'Blueberry']
var negativeSlice=fruitsList.slice(-3,-1);
console.log(negativeSlice);             //['Banana', 'Blueberry']
var negPosSlice=fruitsList.slice(-3,3);
console.log(negPosSlice);               //['Banana', 'Blueberry']
```
**`Array().fill():`**

The `fill()` method use to fill up the index with the specific value. This method accepts 3 parameter like `fill(value, startIndex, endIndex)`.  
value can be of any type. Like number or string.  
startIndex and endIndex can be of number type. This two fields means the starting index and the ending index of the array where the value will be pushed. This 2 fields can be empty as well. In that case, whole array index will be filled up with the value.
```js
var fillArray= Array(5).fill(5);
console.log(ar);                         //[5, 5, 5, 5, 5]
var fillArray2= Array(5).fill(5,1,3);
console.log(fillArray2);                 //[empty, 5, 5, empty, empty]
```
Here `Array(5)` means the array size and `fill(5)` means fill up the whole array with value 5. `fill(5,1,3)` means fill the index from 1 to 3 with value 5.

**`forEach()`:**

![forEach](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/forEach.png)  

`forEach(callback(currentValue, index, array))  `
index and array parameters are optional. The currentValue points to each element. For example, currentValue is Element1 now and index is 0 and array is the input array.

```js
const myArray=new Array(1,2,3);
myArray.forEach((element)=>{
    console.log(element);       //1 2 3
})
```
The `forEach()` loop iterates over array `myArray`. Each time it iterates over each element. Like as, in first iterates over element1 then element2 and so on.
The forEach loop returns undefined.

```js
const myArray=new Array(1,2,3);
const result=myArray.forEach((element)=>{
    console.log(element);
})
console.log(result);        //undefined
```

**Example:**
```js
const myCities=new Array("Dhaka","Gazipur");
const arrayInfo=(element,index)=>
console.log(element+" is located at index "+index+" in the myCities array.");

myCities.forEach((element,index)=>arrayInfo(element,index));
// Dhaka is located at index 0 in the myCities array.
// Gazipur is located at index 1 in the myCities array.
```

**`map()`:**  

![picture](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/map.png)  

`map` function accepts a callback function and that callback function accepts 3 parameter. First parameter is mandatory and rest are optional.  
`map(callback(currentValue, index, array))`  
The map() function return a new array.

```js
const myArray=new Array(1,2,3,5,7,9);
myArray.map((element,index,newArray)=>{
    newArray=element*index;
    console.log(newArray);      //0 2 6 15 28 45
})
```
Here `map()` function accepts a callback function with 3 parameters. element picks the array elements of `myArray`, index takes the index of the element of `myArray` and `newArray` is an array.  
`map()` function returns a new array.
```js
const myArray=new Array(1,2,3,5,7,9);
const resultArray=myArray.map((element)=>element=element*element
);
console.log(resultArray);   //[1, 4, 9, 25, 49, 81]
```

**Example:**  
Converting a JSON array to JavaScript object.
```js
const postJSON=[
    '{"postID":101,"commentsQuantity":5}',
    '{"postID":102,"commentsQuantity":10}',
    '{"postID":103,"commentsQuantity":15}'
]
var postArray=[];
postJSON.map((element)=>{ 
    postArray.push(JSON.parse(element));
});
console.log(postArray);

/*(3) [{…}, {…}, {…}]
0:{postID: 101, commentsQuantity: 5}
1:{postID: 102, commentsQuantity: 10}
2:{postID: 103, commentsQuantity: 15}*/
```

**`filter()`:**
![picture](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/filter.png)  

`filter` function accepts a callback function and that callback function accepts 3 parameter. First parameter is mandatory and rest are optional.  
`filter(callback(currentValue, index, array))`  
The `filter()` function returns a new array. JS engine checks the condition and generates true/false value implicitly and returns a new array consists of the true values.

```js
const myArray=new Array(1,2,3,5,7,9);
const newArray=myArray.filter(element=>element>3);
console.log(newArray);      //[5, 7, 9]
```

**`find()`:**  
Finding a specific value from an array.

![picture](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/find.png)  

`find` function accepts a callback function and that callback function accepts 3 parameter. First parameter is mandatory and rest are optional.  
`find(callback(currentValue, index, array))`  
The `find()` function returns an element. JS engine checks the condition and generates true/false value implicitly and returns the first true value.

```js
const array=["a",23,{},23,50];
var a=23;
const findElement=array.find((element)=>{
    return element===a;
});
console.log(findElement);   //23
```
`find()` method checked thr logic implicitly and returned the value as soon as found true.

**`every()` and `some()`:** 

![every](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/every.png)

check all the elements are following the condition or not. `every()` method returns `true` if all the elements return `true` and `false` if any of the element return `false`.

```js
const myArray=new Array(1,2,3,-5,7,9);
const checkPositiveNumbers=myArray.every((element=>typeof element==="number"&&element>0));
console.log(checkPositiveNumbers);      //false
```

![some](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/some.png)

check all the elements are following the condition or not. `some()` method returns `false` if all the elements return `false` and `true` if any of the element return `true`.

```js
const myArray=new Array(1,2,3,-5,7,9);
const checkPositiveNumbers=myArray.some((element=>typeof element==="number"&&element>0));
console.log(checkPositiveNumbers);      //true
```

**`includes()`:**  

![includes](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/includes.png)

Search to find out whether an specific element is present in the array or not. If found then return true. This method accepts the starting index as second parameter.  
N.B: This method works only on primitive elements of an array.

```js
const myArray=new Array(1,2,3,-5,7,9, [10,20],{a:100,b:200});
const checkElement=myArray.includes(3);
console.log(checkElement);              //true
console.log(myArray.includes(2,3));     //false. First parameter is the element and second parameter is the starting index
console.log(myArray.includes([10,20])); //false. includes method works on only primitive data.
```
