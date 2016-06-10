# Javascript


## Basic Code Snippets

### While-Loops

```javascript
// While-Loops

var bool = true;
while(bool){
    console.log("Less is more!");
    bool = false;
}

// or

var yeah = 6
while (yeah>1) {
    console.log("You too, "+yeah);
    yeah--;
}

```

### For-Loops & Arrays

```javascript
// For-loops & Arrays

var names = ["Lisa", "Julie", "Mateo", "Nic", "Thibaud"];
for (i=0; i<names.length; i++){
    console.log("I know someone called "+names[i]);
}

```


### Functions

```javascript
// functions

var matheyeah = function (number) {
    var newnumber = number * 10;
    console.log(newnumber);
};

matheyeah(4);
```

### If-Else & Return

```javascript
// if - else & return
// takes the number 48, processes it in the function
// "quarter" and gives it back to the if loop.

var quarter = function(number) {
    return number/4;
}

if (quarter(48) % 3 === 0 ) {
  console.log("The statement is true");
} else {
  console.log("The statement is false");
}
```

### Switch Statement

```javascript
var age = prompt("How old are you?");

switch(lunch){
  case '5':
    console.log("That's so young!");
    break;
  case '18':
    console.log("The best age!");
    break;
  default:
    console.log("I'm sure " + age + " is a great age.");
}
```

## Even smaller code snippets (functions)

- ``isNan`` checks to see if something is **not** a number (e.g. ``isNan("berry") = true``, ``isNan(41) = false``)
- ``var age = prompt("How old are you?");`` asks the user a question and puts the answer into the var ``age``.
- Logical operators:
    - and (``&&``)
    - or (``||``)
    - not (``!``), e.g. ``!true;   // => false``
- ``typeof``: figures out if something is a string, number, function or object: ``console.log( typeof someObject );`` = Object
- ``hasOwnProperty``: lets us know if an object has a particular property: ``
console.log( myObj.hasOwnProperty('name') );``--> can print "true" or "false"
- **Public**: Public means that properties of an object can be accessed outside the class (default). E.g. ``this.age = age;``.
- **Private**: Properties that stay private and can only be accessed directly in the class. Defined as a variable, e.g. ``var bankBalance = 7500;``.

<br><br>


