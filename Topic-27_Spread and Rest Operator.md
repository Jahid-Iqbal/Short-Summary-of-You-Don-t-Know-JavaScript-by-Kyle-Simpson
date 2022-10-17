# Rest Parameters

![Rest](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/rest.png)

Accepting as many arguments through a single parameter. The parameter treats each arguments as an element of an array.

```js
const restParameter=(element1,element2, ...element3)=>{
    console.log(element1,element2,element3);
};
restParameter(1,2,3,4,5,6); //1 2 (4) [3, 4, 5, 6]
```
Here, a arrow function accepts 3 parameter but passed 6 arguments. So first 2 parameter accepts first 2 arguments and the rest parameter `element3` accepts the rest arguments as an array.

# Spread operator

![Spread](https://github.com/Jahid-Iqbal/Short-Summary-of-You-Don-t-Know-JavaScript-by-Kyle-Simpson/blob/main/Pictures/spread.png)

Passing an array as arguments but the function accepts each element of the array as an individual parameter.

```js
const spreadOperator=(name,age,city)=>{
    return `${name} is ${age} years old and he is living in ${city} city.`;
};

const person=["Abdullah",29,"Dhaka"];
console.log(spreadOperator(...person));  //Abdullah is 29 years old and he is living in Dhaka city.

const anotherPerson=[30,"Dhaka"];
console.log(spreadOperator("Abdur Rahman",...anotherPerson));    //Abdur Rahman is 30 years old and he is living in Dhaka city.
```

Here, an array `person` passed as an argument and each parameter of the function `spreadOperator` accepts each element of the array as an individual argument.

**In Rest parameter (...) 3 dots used in functions parameter and in Spread Operator (...) 3 dots used in passed arguments.**

**Example:** Concatenating two array:
```js
const a= [1,2,3];
const b=[4,5,6,7];
c=[...a,...b,8];
console.log(c);     //[1, 2, 3, 4, 5, 6, 7, 8]
```
**Example:** Copying an array to another array.

```js
const array= [1,2,3];
const newArray=[...array];
console.log(newArray);      //[1, 2, 3]
```