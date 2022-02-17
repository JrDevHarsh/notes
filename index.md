# Objects in JavaScript

## What is object in javascript?

An object is simply a collection of properties in the form of name and value pairs. In JavaScript, almost "everything" is and object. We can define (and create) a JavaScript object with and `object literal`. Syntax for declaring objects in javascript is :

``` 
let person = {
    firstName: 'Junior',
    lastName: 'Senior',
    printName: function(){
        return this.firstName + " " + this.lastName;
    } 
}
```

### Object Property

The name:values pairs in JavaScript objects are called properties. Like `firstName` is an property of an object as well as `Junior` is property's value shown in above example.

### Object Methods

Object can also have methods. Methods are actions that can be performed on objects. Object properties can be both `primitive value`, other objects, and functions(). And object method is and object property containing a function definition.

> **Primitive value** is a value that has no properties or methods. asdsds. **Primitive data type** is data that has a primitive value. Following are some examples :
- string 
- number
- boolean
- null 
- undefined

## How to create an Object in JavaScript?

JavsScript has different ways to define or create an object:

-  Create an object with object literals

```
let person = {
    firstName: 'Junior',
    lastName: 'Senior',
    printName: function(){
        return this.firstName + " " + this.lastName;
    } 
}
```

- create an object with keyword `new`

> `new` is a keyword in JavaScript which is used to create and instance of an object that has a constructor function. In simple words, `new` keyword is used to create an object from a constructor function. 

```
const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```

- define an object `constructor` and then create objects of the constructed type.

```
// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

// Create two Person objects
const myFather = new Person("John", "Doe", 50, "blue");
```

- create and object using `Object.create()`

> `Object.create()` method creates a new object, using an existing object as the prototype of the newly created object.

```
const person = {
  isHuman: false,
  printIntroduction: function() {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  }
};

const me = Object.create(person);

me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

me.printIntroduction();
// expected output: "My name is Matthew. Am I human? true"
```

## Properties in JavaScript

Properties are the values associated with a JavaScript object or often describing attributes associated with a data structure. Following example will help you how to access property of an object:

```
let person = {
    name: 'Junior',
    age: 18
}
console.log(person.age); // We access it with dot notation(.), Result will be 18
console.log(person["age"]); // We access it with bracket notation([]), Result will be 18
let personAge = "age";
console.log(person[personAge]); // Result will be 18
```
> We can add new properties in an `existing object` by simply giving it a value.

```
person.gender = "Male";
```

> To delete a property from an object, we use `delete` keyword (delete th value of the property and property itself). `Avoid` to use it on prdefined JavaScript object properties.

```
delete person.gender; // First method
delete person["gender"] // Second method
```

## Nested Objects

Values in an object can be another object. In simple words, if existing object property's value has an object then we can say that the whole object is a nested object. For e.g.

```
myObj = {
  name:"John",
  age:30,
  cars: {
    car1:"Ford",
    car2:"BMW",
    car3:"Fiat"
  }
}
```

> In myObj object, `cars` property has a value of an object which makes myObj is an nested object. We can access nested object with `dot notation` and `bracket notation`.
```
myObj.cars.car1 // Result will be Ford
myObj["cars"]["car1"] // Result will be Ford
```

## Nested Objects and Arrays

Values in objects can be arrays, and values in arrays can be objects:

```
const myObj = {
  name: "John",
  age: 30,
  cars: [
    {name:"Ford", models:["Fiesta", "Focus", "Mustang"]},
    {name:"BMW", models:["320", "X3", "X5"]},
    {name:"Fiat", models:["500", "Panda"]}
  ]
}
```

> In above example, `myObj` object's property name called `cars` has an array which consist of object values in it. If we want to access the models of Ford then we can write like this:

```
myObj.cars[0].models // ["Fiesta", "Focus", "Mustang"]
```

## Methods in JavaScript

JavaScript methods are actions that can be performed on objects. A JavaScript method is a property containing a function definition. We can say that methods are `functions` stored as `object properties`.

```
const person = {
  firstName: "John",
  lastName: "Doe",
  id: 5566,
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
};
```

> In above example, `fullName` in person object is a method that will return the firstName and lastName of an object. We can `add method outside to an existing object` like we add properties to an object. To access an object method, we should have to write like this:

```
person.fullName(); // objectName.methodName()
```

## How to display JavaScript Objects?

There are differnt ways to display object in JavaScript like:

- Displaying the Object Properties by `name`

     ```
     console.log(person.id) // 5566
     ```
- Displaying the Object in a `Loop`

    ```
    const person = {
        name: "John",
        age: 30,
        city: "New York"
    };
    for (let element in person) {
        console.log(person[element]);
    };
    //John
    //30
    //New York
    ```

- Using `Object.values()` - it will convert the JavaScript object to an array 
    
    ```
    const person = {
        name: "John",
        age: 30,
        city: "New York"
    }; 
    const myArray = Object.values(person);
    console.log(myArray); // ["John", 30, "Ne York"]
    ```

- Using `JSON.stringify()` - it will convert JavaScript `objects, arrays, dates` to string except `functions` in objects.
    ```
    const person = {
        name: "John",
        age: 30,
        city: "New York"
    };
    let myString = JSON.stringify(person);
    console.log(myString); // {"name":"John","age":30,"city":"New York"}
    ```

## JavaScript Object Accessors

`Getters` and `setters` allow you to define Object Accessors (Computed Properties)

- Getter in JavaScript

    ```
    // How we define method in object?
    //Like this
    let person = {
        name: 'Alex',
        age: 13,
        display: function(){
            return this.name + " " + this.age;
        }
    } 
    person.display(); // Alex 13

    // But if we write like this
    let person = {
        name: 'Alex',
        age: 13,
        get display(){
            return this.name + " " + this.age;
        }
    }
    person.display; // Alex 13
    ```

> With 2nd syntax, we don't have to write `function` keyword anymore and we can simply access `method` in object with `objectName.methodName` without `parenthesis`.

- Setter in JavaScript

    ```
    let person = {
        name: 'Alex',
        age: undefined,
        set setAge(num){
            this.age = num;
        }
    }
    person.setAge = 18; // Alex 13
    ```

## JavaScript Object Constructor (Constructor Function)

Sometimes we need a "blueprint" for creating many objects of the same "type". The way to create an "object type", is to use an `object constructor function`. See the following example:

```
// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

// Create two Person objects
const myFather = new Person("John", "Doe", 50, "blue");
const myMother = new Person("Sally", "Rally", 48, "green");

// Display age
console.log(myFather.firstName); // John
console.log(myMother.firstName); // Sally
```

> We can add method and property to an existing objects

## JavaScript Object Prototype

All JavaScript objects inherit properties and methods from a prototype. For e.g.


```

// Let's do some work here:
// Open your Chrome(Or any web browser)
// Go to Developers Tool or Press Ctrl + Shift + I (Windows only) or F12
// Open Console section
// create an array with some elements and hit enter
    let arr = [1,2,3,4,5];
// now type 
    arr.
// You will notice that you got many suggestions like 
    .at
    .concat
    .constructor
    and so on
//These are a kind of methods and properties of array in JavaScript
```

> If you create an object in JavaScript, it will attached your object with some `hidden` properties and methods or functions without even letting you know.

All JavaScript objects inherit properties and methods from a prototype:

- Date objects inherit from Date.prototype
- Array objects inherit from Array.prototype
- Person objects inherit from Person.prototype

`Object.prototype` is on the top of the prototype inheritance chain.

### Adding Properties and Methods to Objects

Sometimes we want to add new properties (or methods) to an existing objects or to an object constructor. For e.g.

```
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

//adding new property to object constructor 
Person.prototype.nationality = "English";

//adding new method to object constructor 
Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```

## JavaScript Sets

JavaScript sets is a collection of `unique values`. Each value can only occur once in a Set. A Set can hold any value of any data type. 

### How to create a Set 

There are mainly three ways to create a Set:

- Passing an Array to `new Set()`

    ```
    const letters = new Set(["a","b","c"]);
    console.log(letters.size) // 3
    ```
- Create a new Set and use `add()` to add values

    ```
    // Create a Set
    const letters = new Set();

    // Add Values to the Set
    letters.add("a");
    letters.add("b");
    letters.add("c");
    console.log(letters.size) // 3
    ```

- Create a Set and `add variables`

    ```
    // Create Variables
    const a = "a";
    const b = "b";
    const c = "c";

    // Create a Set
    const letters = new Set();

    // Add Variables to the Set
    letters.add(a);
    letters.add(b);
    letters.add(c);
    ```

Following are eome methods for Set:

- `new Set()` - creates a new Set

    ```
    // Create a Set
    const letters = new Set();
    ```

- `add()` - adds a new element to the Set

    ```
    // Create a Set
    const letters = new Set();

    // Add Values to the Set
    letters.add("a");
    console.log(letters); // Set(1) {'a'}
    ```

- `delete()` - removes an element from a Set

    ```
    const letters = new Set(["a","b","c"]);
    letters.delete("a");
    console.log(letters); // Set(2) {'b', 'c'}
    ```

- `has()` - returns true if a value is exist
    
    ```
    const letters = new Set(["a","b","c"]);
    letters.has("a"); // true
    ```

- `clear()` - removes all elements from a Set

    ```
    const letters = new Set(["a","b","c"]);
    letters.clear();
    console.log(letters); // Set(0) {size: 0}
    ```

- `forEach()` - invokes a callback for each element

    ```
    const letters = new Set(["a","b","c"]);

    // List all entries
    letters.forEach (function(value) {
        console.log(value);
    });
    ```
- `values()` - returns an iterator with all values in a Set
- `key()` - same as values()
- `entries()` - returns an iterator with the [value, value] pairs from a Set 

    `size` returns a number (length) of elements.(property)

