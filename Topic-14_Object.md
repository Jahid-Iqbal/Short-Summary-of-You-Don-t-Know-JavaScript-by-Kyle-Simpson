# Object
>Object is a set of variables or methods where each one holds its own value.

Let say, an object has 3 variables. One of them of Number type, one is of String type and another one is Boolean type.  
**Example:**
```js
var personalInfo={
    personName: "Ahmad",
    personAge: 35,
    personIsAlive: true
};
```
The property names should be of string type always. If anything else is given then JS engine converts that into string implicitly. Such as,
```js
var object={
    365: "Updated version of MS office",
};
console.log(object[365]);
```
The property names can be dynamic. You can pass the property name as below.
```js
var personName="Ahmad";
var personalInfo={
    [personName+" designation"]: "Software Engineer",
    [personName+" qualification"]: "Bsc Engineer"
};
console.log(personalInfo);  //{Ahmad designation: 'Software Engineer', Ahmad qualification: 'Bsc Engineer'}
```
Here, you don't need to change the name each time it required. Just change once and the object will act accordingly.

**getOwnPropertyDescriptor():**  
An object has some configuration, depending on those that object can be modified. Such as, writable, enumerable and configurable. All of them are remain true by default. You can verify all the configuration using built in function `getOwnPropertyDescriptor()`.
```js
var personalInfo={
   myName: "Ahmad"
};
console.log(Object.getOwnPropertyDescriptor(personalInfo,"myName"));  //{value: 'Ahmad', writable: true, enumerable: true, configurable: true}
```
**defineProperty():**  
You can modify the default configuration of an object using function `defineProperty()`. This function accepts 3 parameters. First one is an object, second one is a property name of that object, third one is a set of configuration.

**Modifying writable:**  
`writable` holds the permission whether the value of that property can be changed anymore or not. If `writable` is `true` then value can be changed anytime anyway. If `writable` is `false` then value cannot be changed anymore anyway. In below code, making writable  `false`. After that `personName` updated but that did't reflected anyway. System printed the previous value `Ahmad`. In strict mode, updating name would lead to `TypeError`.
```js
var personalInfo={};
Object.defineProperty(personalInfo,'personName',{
    value:"Ahmad",
    writable: false,
    configurable: true,
    enumerable: true
});
personalInfo.personName="Mohammad"; //Not updated the value.
console.log(personalInfo.personName);   //Ahmad
```
**Modifying configurable:**  
`configurable` holds the permission of whether you can change the configuration of that object property anymore or not. If `configurable` is `true` then configuration can be changed anyway. If `configurable` is `false` then `enumerable` cannot be changed anyway, `writable` can be changed only from `true` to `false` not vice versa. The property won't be deleted in thin scenario.
```js
var personalInfo={};
Object.defineProperty(personalInfo,'personName',{
    value:"Ahmad",
    writable: true,
    configurable: false,
    enumerable: true
});
delete personalInfo.personName;         //Not deleted. Incase of strict mode it will show TypeError
console.log(personalInfo.personName);   //Ahmad
Object.defineProperty(personalInfo,'personName',{
    value:"Ahmad",
    writable: false,
    configurable: false,
    enumerable: false
});
console.log(personalInfo.personName);   //Uncaught TypeError TypeError: Cannot redefine property: personName  
```
Here, making `configurable` `false` and then tried to delete the property but did't work. In case of `strict mode` that would show `TypeError`. Again tried to update the configuration but system shown `TypeError`.