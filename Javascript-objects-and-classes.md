# Javascript: Objects & Classes


- **Class**: The recipe. Defines the characteristics of the object. It is a template definition of variables and methods of an object.
- **Object**: The cake that's baked with the recipe. An Instance of a class.


<br>
## Defining objects
- objects are in associative arrays

```javascript
// creating a new objects.
// "name" is the key/property, "Lisa" is the value.

var me = new Object();
me.name="Lisa";
me.age=18;

//OR

var me = new Object();
me["name"] = "Lisa";
me["age"] = 18;

//OR

var me = {
    name: "Lisa",
    age: 18
};


//Saving objects in a new var with
//ObjectName.PropertyName (="dot-Notation")

var LisasAge = me.age;
//OR
var LisasAge= me["age"];

//Accessing objects with object[key]:
for (var key in me) {
    if (name===me[key].name) {
        console.log(me[key]);
        return(me[key]);
    }
}

// Accessing all keys with a for-loop:
for (var property in me) {
    console.log(property);
}

//Accessing all values of keys in a for-loop:
for (var i in me) {
    console.log(me[i]);
}


```
<br>
## Methods
- similar to functions, but:
- can be used to change object property values
- can be used to make calculations with object properties (functions can't do that!)

```javascript
var bob = {
    name: "Bob Smith",
    setAge: function (newAge){
        bob.age = newAge;
    },
    getYearOfBirth: function () {
        return 2014 - bob.age;
    }
};

bob.setAge(40);
```
<br>
## "This" keyword
- The keyword ``this`` acts as a placeholder, and will refer to **whichever object called that method** when the method is actually used.
- ``yeahAge`` equals the function that takes the new age. bob.age gets overwritten by the new equavation "bob.age=50" that can be found inside the yeahAge function.
- **The computer looks very hard for new properties to overwrite old ones, even in subfunctions!**

```javascript
var yeahAge = function (newAge) {
  this.age = newAge;
};

var bob = new Object();
bob.age = 30;
// console.log(bob.age) prints 30
bob.setAge = yeahAge;
// console.log(bob.age) still prints 30!!

bob.setAge(50);
// console.log(bob.age) prints 50

```
<br>
## Classes
- get created with with "Coding Constructors"
- Why is this Cat constructor so cool? It means if we have many cats and wanted to create an object for each cat, we could just use this constructor with the properties already defined.
- we don't have to define all properties (-->"breed")
- ``console.log("Cat1's species is " + cat1.breed + " and he is " + cat1.age);`` prints the breed, because it's always the same for all of them

```javascript
function Cat(age, color) {
  this.age = age;
  this.birthday = function() {
    return 2014-this.age;
  }
  this.color = color;
  this.breed = "cute";
}

var cat1 = new Cat(40,"brown");
var cat2 = new Cat(20, "brown");

//do maths
var ageDifference = function(cateins, catzwei) {
    return cateins.age - catzwei.age;
}

var diff = ageDifference(cat1,cat2);

//Add a method to a class with extending the prototype:
Cat.prototype.WhatNoise = function() {
  console.log("Miau!");
};

// Defining a new Class (Chesirecats) that inherits the
// properties of the Cat-class
Chesirecats.prototype = new Cat();


```
