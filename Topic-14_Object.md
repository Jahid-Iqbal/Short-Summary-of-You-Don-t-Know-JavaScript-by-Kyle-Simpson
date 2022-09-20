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

**Modifying enumerable:**  
`enumerable` hide a property from the for..in loop. If `enumerable` will be `false` then that property cannot be accessible to for..in loop.
```js
var personalInfo={
    personAge: 30,
    personCity: "Dhaka"
};
Object.defineProperty(personalInfo,'personName',{
    value:"Ahmad",
    writable: true,
    configurable: true,
    enumerable: false
});
console.log(personalInfo.propertyIsEnumerable("personName"));   //false
for(var key in personalInfo){
    console.log(key);   //personAge personCity
}
```
In this code, `enumerable` of property `personName` updated to `false`. So, expectedly the for..in loop failed to fetch that property. The function `propertyIsEnumerable(property)` returns true if enumerable of that property is `true` and `false` otherwise.

**Constant Object Property:**  
The property of an object can be made constant by changing all the property (writable, configurable, enumerable) to `false`.  
**Example:**
```js
var personalInfo={
    personName:"Ahmad",
    personAge: 30,
    personCity: "Dhaka"
};
Object.defineProperty(personalInfo,'personName',{
    value:"Ahmad",
    writable: false,
    configurable: false,
    enumerable: false
});
personalInfo.personName="Abdullah";
console.log(personalInfo.personName);   //Ahmad
```
**preventExtensions():**  
This function prevents an object from further property extension. This function is a property of `Object` object and accepts an object as arguments or parameter.
```js
var personalInfo={
    personName:"Ahmad",
    personAge: 30,
};
Object.preventExtensions(personalInfo);
personalInfo.personCity="Dhaka";    //TypeError incase of strict mode
console.log(personalInfo);      //{personName: 'Ahmad', personAge: 30}
```
Here, after `preventExtensions()` function another property is added to object `personalInfo` but that did't add to that object property. In case of strict mode this extension would through `TypeError`.

**`seal():`**  
`seal()` function calls two other function implicitly. Those are `preventExtensions()` and `defineProperty()` with `configurable` false and `writable` true. So, after the `seal()` function, no extension will be applicable and no configuration can be changed apart from making `writable` false. 
```js
var personalInfo={
    personName:"Ahmad",
    personAge: 30,
};
Object.seal(personalInfo);
personalInfo.personCity="Dhaka";    //TypeError incase of strict mode

Object.defineProperty(personalInfo,personName,{
    writable: true,
    configurable:true,
    enumerable:true
});
console.log(personalInfo);      //Uncaught TypeError: Cannot define property Ahmad, object is not extensible
```
Here, after `seal()` function, tried to add another property to object `personalInfo` but failed as `seal()` prevented that. Again tried to change the configuration but shown `TypeError`.

**`freeze()`:**  
This function calls the `seal()` function implicitly with `writable` false. So no extension, change in value and change in configuration will be allowed after `freeze()` function. This function provides most immutability.
```js
var personalInfo={
    personName:"Ahmad",
    personAge: 30,
};
Object.freeze(personalInfo);
personalInfo.personCity="Dhaka";    //TypeError incase of strict mode

personalInfo.personAge=80;          ////TypeError incase of strict mode

Object.defineProperty(personalInfo,personName,{
    writable: true,
    configurable:true,
    enumerable:true
});
console.log(personalInfo);      //Uncaught TypeError: Cannot define property Ahmad, object is not extensible
```
Here, after `freeze()` function tried to add another property, changing the value and updating the configurations but all failed.