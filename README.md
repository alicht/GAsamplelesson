# GAsamplelesson

* ES6 introduces the class keyword. This new class syntax just provides an alternative way to create plain old JavaScript objects.

# What are prototypes?
Prototypes are the underlying blueprint of an object, and form the baseline from which other instances of an object can be created. 
* Every object in JavaScript has a special related object called the prototype. Through using Prototypes we can simply and efficiently share behavior and data between multiple objects.

* In code a prototype looks like this:
```
vehicle.prototype = machine
// machine is the prototype of vehicle

car.prototype = vehicle
// vehicle is the prototype of car
```
This is a prototype chain:
```
car -> vehicle -> machine
```
When JavaScript looks for a property that doesn't exist in a particular object (e.g. car), it will attempt to look for that property in each object on the prototype chain (e.g. first in vehicle, then in machine). It will walk along the chain until it finds the attribute or return undefined if it can't be found

----



# Why is Prototype Important and When is it Used?
These are two important ways Prototypes are used in JavaScript:

# 1. Prototype-based Inheritance

-- but first: what is INHERITANCE and why would coders want to use it?
INHERITANCE- passing down properties is called inheritance. Inheritance helps prevent overcoding multiple properties and methods into similiar objects.

Programmers love inheritance, because it keeps our code neat and organized, and because it saves us from having to define all the properties belonging to an Object each time we need to make a new instance.

Prototype is important in JavaScript because JavaScript does not have Class based inheritance (as most object oriented languages do), and therefore all inheritance in JavaScript is made possible through the prototype property.


# 2 Prototypal Constructors
We create Constructor functions with our prototypes, and we can easily create new instances of an object. 
When we create a use case of an Object, we use something called a Constructor. Constructors are used to create instances of objects.

Let's start by creating a new object.
```
//new object
var shirt = {size:6, gender: "womens", construction: "slipper" }
```

We say that an Object instance inherits from its parent object ie the prototype. What we mean is that each time we create a new Object (using the keyword 'new'), that Object immediately and automatically has access to all of the properties defined in the parent object. In our Shirt example, this means that every single time we make a new Shirt, they have access to all of the properties defined in the Constructor (size, gender, construction, etc)...and this is known as Prototypal Inheritance (more commonly referenced as just inheritance). 

Using inheritance we can create new objects with our existing objects as prototypes. 
```
// creating a new object that uses shirt as a prototype
var magicShirt = Object.create ( shirt ); // whatever we pass in will be the prototype for the new object
-if we logged out magicShirt we'd see that it's exactly the same as shoe because it inherited all of shoes properties
```

can add new properties to magicShoe: 
```
magicShirt.jewels = "ruby";
magicShirt.travelAction = "click heels";
magicShirt.actionRequired = 3;
```
# 3 Instantiating an object with values

How to create other types of shirts
```
var shirt = {size: undefined, gender: undefined, constructor: undefined}
// now to automate our property assignment
```
We need to determine common properties of a shoe class. 
Class- a set of objects that all share and inherit from the same basic prototype

Lets list common properties that we can expect ALL shoes to have and we're ready to build a constructor for our class.
Constructor- will allow us to set up inheritance while also assigning specific property values.
```
// we capitalize this function to distinguish it as a maker of an entire class of objects
function Shirt(shirtSize, shirtColor, shirtGender, constructionStyle){
this.size = shirtSize; 
thus.color = shirtColor;
this.gender = shirtGender;
this.construction = constructionStyle;
}
// this is going to refer to the new instance of the class that is made
```

Javascript's "new" keyword produces a new Object of the class (ie instantiates it)
```
var beachShirt = new Shirt(10, "blue", "womens", "flip-flop");
```

# 4
* ES6

In JavaScript we have Function Constructors, which have been the common way to build new objects until ES6. Unfortunately Function Constructors can be quite confusing to understand (especially if you want to model inheritance). To alleviate this, ES6 introduces the class syntax.

Classes in ES6 don't add any functionality to what we already have in the language, they are just a simpler syntax for building the same objects as we had before.


run in console

Although OOP can help us keep our Javascript nice and clean, it's still easy to duplicate code when defining multiple classes. Consider the following example...
```
class Dog {
  constructor(name, breed, tail){
    this.name = name;
    this.breed = breed;
    this.waggingTail = tail;
    this.diet = [];
  }
  eat(food){
    this.diet.push(food);
    console.log(this.diet);
  }
  bark(){
    return `Bark! Hello, this is dog. My name is ${this.name}`
  }
}

class Cat {
  constructor(name, breed, numLives){
    this.name = name;
    this.breed = breed;
    this.numLives = numLives;
    this.diet = [];
  }
  eat(food){
    this.diet.push(food);
    console.log(this.diet);
  }
  meow(){
    return `Meow! I am not a dog! My name is ${this.name}`
  }
}
```

Here we have two classes: Dog and Cat. They have some things in common: name, breed, diet and eat. They do differ, however, in that one barks and the other meows.

Imagine that we had to create a number of other classes - Horse, Goat, Pig, etc. - all of which share the same aforementioned properties but also have methods that are particular to the class.

How could we refactor this so that we don't have to keep writing out the shared class properties and methods. Enter inheritance (think genetics, not money from your rich uncle)
```
class Animal{
  constructor(name, breed){
    this.name = name;
    this.breed = breed;
    this.diet = [];
  }
  eat(food){
    this.diet.push(food);
    console.log(this.diet);
  }
}
```

const dog = new Animal("Fido", "Beagle");
Here we've defined an Animal class. It contains the properties and methods that are common among specific animal classes. Wouldn't it be nice if Dog and Cat could just reference this "parent" Animal class so that the only things we need to put in their "child" class definitions are the properties and methods that are particular to them (e.g., bark, meow).

Lucky for us, we can do that...
```
class Animal {
  constructor(name, breed){
    this.name = name;
    this.breed = breed;
    this.diet = [];
  }
  eat(food){
    this.diet.push(food);
    console.log(this.diet);
  }
}

class Dog extends Animal {
  constructor(name, breed, tail){
    this.waggingTail = tail;
  }
  bark(){
    return `Bark! Hello, this is dog. My name is ${this.name}`
  }
}

class Cat extends Animal {
  constructor(name, breed, numLives){
    this.numLives = numLives;
  }
  meow(){
    return `Meow! I am not a dog! My name is ${this.name}`
  }
}
```
The clincher is extends. Whatever class is to the left of the extends keyword should inherit the properties and methods that belongs to the class to the right of the keyword. Let's see if this works...

// Let's test out our parent. It just needs a name and breed.
```
const goat = new Animal("Gregory", "Mountain Goat");
```
// And now the children.
```
const fido = new Dog("Fido", "Beagle", true);
console.log(fido); // "this is not defined"
```
That didn't work out the way we expected. That's because we're forgetting one thing. When creating an instance of a child class, we need to make sure it invokes the constructor of the parent (Animal) class.

We can do that using the keyword super()
```
class Dog extends Animal {
  constructor(name, breed, tail){
    super(name, breed);
    this.waggingTail = tail;
  }
  bark(){
    return `Bark! Hello, this is dog. My name is ${this.name}`
  }
}
```
super() calls the constructor of the parent class. In the above example, once super does what it needs to do, it then runs through the rest of Dogs constructor.


















# Namespacing

The  concept of namespacing as it applies to programming is that we give all of our variables/functions/objects/etc unique names so we don't accidentally end up repeating them later in our code. The reason for this is that as applications growmay mistakenly reuse a name which we had already assigned which can mess up our entire code.
The easiest way to think about namespacing is that you've got your code laid out in a hierarchy, like the outline for an essay. If the top level of your essay is called MY_ESSAY, then everything that follows MY_ESSAY (all the paragraphs, citations, etc) belong to MY_ESSAY, and nothing else. MY_ESSAY is what is known as a global object. The same rules apply with inheritance in JavaScript. To go back to our Person example:

Person is the global object -- and everything inside of Person (and therefore, everything inside of every instance of Person) belongs solely to the Person object
this is namespacing, and it helps us to keep our code tidy and packaged up.
For a better explanation of namespacing, read this.



# see also 
http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/

Inline-style: 
![alt text](https://memegenerator.net/instance/72706299/david-pumpkins-snl-any-questions "Logo Title Text 1")

