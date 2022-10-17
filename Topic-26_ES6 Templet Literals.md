# Template Literals

An update came in ECMAScript2015 (ES6) in concatenation statements.

**Pre-ES6 Template:**
```js
const personName="Abdullah";
const personAge=30;
const personCity="Dhaka";

const personDetails= personName+" is "+ personAge+ " years old and he is living in " +personCity +" city.";
console.log(personDetails);     //Abdullah is 30 years old and he is living in Dhaka city.
```
**ES6 Template:** conditional statements also can be written here.

```js
const personName="Abdullah";
const personAge=30;
const personCity="Dhaka";
const maritalStatus=true;

const personDetails= `${personName} is ${personAge} years old, his marital status is ${maritalStatus ? "Married" : "Unmarried"} and he is living in ${personCity} city.`;
console.log(personDetails);     //Abdullah is 30 years old, his marital status is Married and he is living in Dhaka city.
```