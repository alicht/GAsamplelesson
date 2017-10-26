# GAsamplelesson

## What are prototypes?
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

## Pre-ES6 example
### Simple way to create objects via their prototype

Let's start by creating a new object using Object.create.
```
//new object
var shirt = {size:6, gender: "womens", construction: "slipper" };
```
We can build new objects using this existing object as a prototype: 
```
// creating a new object that uses shirt as a prototype
var magicShirt = Object.create ( shirt ); // whatever we pass in will be the prototype for the new object
-if we logged out magicShirt we'd see that it's exactly the same as shirt because it inherited all of shirt's properties
```
An Object inherits from its parent Object ie the prototype. Each time we create a new Object, that Object immediately and automatically has access to all of the properties defined in its parent Object. In our Shirt example, this means that every single time we make a new Shirt, they have access to all of the properties defined in the Constructor (size, gender, construction, etc).

###### can add new properties to magicShirt: 
```
magicShirt.color = "ruby";
magicShirt.material = "cotton";
magicShirt.usage = "daily";
```
## But this is very time consuming... a faster way is by introducing regular Constructor functions for prototypes.

Let's build a Constructor function- ie a function that will allow us to set up inheritance while also assigning specific property values. 

we'll start by creating a shirt Object again:
 
```
// we capitalize this function to distinguish it as a maker of an entire class of objects
function Shirt(shirtSize, shirtColor, shirtGender, constructionStyle){
  this.size = shirtSize; 
  this.color = shirtColor;
  this.gender = shirtGender;
  this.construction = constructionStyle;
}
```

Javascript's "new" keyword produces a new Object of the class (ie instantiates it)
```
var beachShirt = new Shirt(10, "blue", "womens", "flip-flop");

```

# ES6 introduces some new "gamechanging" syntax


In JavaScript we have Function Constructors, which have been the common way to build new objects until ES6. Unfortunately Function Constructors can be quite confusing to understand. To alleviate this, ES6 introduced the "class" keyword. 
Classes in ES6 are honestly just syntactis sugar- they don't add any additional functionality to what we already had in the language (ie constructors), they are just a simpler syntax for building the same objects as we had before.

## Implementing JavaScript's new "class" keyword 

Let's take a long at how a constructor would look like when we use class:

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

How could we refactor this so that we don't have to keep writing out the shared class properties and methods. Enter inheritance
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

In order to give an instance of a child class context (i.e., be able to use this), you must call super.



# Review
What is a class? What is new? How are they related?
What does it mean to use "inheritance" when working with classes?
How do we indicate that one class inherits from another?
What does super mean?











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

