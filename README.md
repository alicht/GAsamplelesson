# GAsamplelesson

# What are prototypes?

Prototypes are the underlying blueprint of an object. They are the base version of an object, and are the baseline from which  other instances of that particular object can be created. Javascript provides us with a very nice blueprint object that will pass those similiar properties to every single one of the objects we have made. by default, all objects in JavaScript are automatically created with the property prototype.

Looking at concept of inheritance and how it relates JavaScript. 

-- why would coders use it?
INHERITANCE- passing down properties is called inheritance.
Inheritance helps prevent overcoding multiple properties and methods into similiar objects.

Programmers love inheritance, because it keeps our code neat and organized, and because it saves us from having to define all the properties belonging to an Object each time we need to make a new instance.


# 2 Prototypal Inheritance / Constructors
When we create a use case of an Object, we use something called a Constructor. Constructors are used to create instances of objects.

Using inheritance we can create new objects with our existing objects as prototypes. 
```
//new object
var shoe = {size:6, gender: "womens", construction: "slipper" }
```

We say that an Object instance inherits from its parent object ie the prototype. What we mean is that each time we create a new Object (using the keyword 'new'), that Object immediately and automatically has access to all of the properties defined in the parent object. In our Person example, this means that every single time we make a new Person, they have access to all of the properties defined in the Constructor (firstName, lastName, eyeColor, etc)...and this is known as Prototypal Inheritance (more commonly referenced as just inheritance). 

Using inheritance we can create new objects with our existing objects as prototypes. 
```
//new object
var shoe = {size:6, gender: "womens", construction: "slipper" }
// creating a new object that uses shoe as a prototype
var magicShoe = Object.create ( shoe ); // whatever we pass in will be the prototype for the new object
-if we logged out magicShoe we'd see that it's exactly the same as shoe because it inherited all of shoes properties
```

can add new properties to magicShoe: 
```
magicShoe.jewels = "ruby";
magicShoe.travelAction = "click heels";
magicShoe.actionRequired = 3;
```

How to create other types of shoes
var shoe = {size: undefined, gender: undefined, constructor: undefined}
// now to automate our property assignment
We need to determine common properties of a shoe class. 
Class- a set of objects that all share and inherit from the same basic prototype

Lets list common properties that we can expect ALL shoes to have and we're ready to build a constructor for our class.
Constructor- will allow us to set up inheritance while also assigning specific property values.
```
// we capitolize this function to distinguish it as a maker of an entire class of objects
function Shoe(shoeSize, shoeColor, shoeGender, constructionStyle){
this.size = shoeSize; 
thus.color = shoeColor;
this.gender = shoeGender;
this.construction = constructionStyle;
}
// this is going to refer to the new instance of the class that is made
```

Javascript's "new" keyword produces a new Object of the class (ie instantiates it)
var beachShoe = new Shoe(10, "blue", "womens", "flip-flop");

assign a constructor to a prototype 11:49


__proto__ vs protype
But Firefox and most versions of Safari and Chrome have a __proto__ “pseudo” property (an alternative syntax) that allows you to access an object’s prototype property. You will likely never use this __proto__ pseudo property, but you should know that it exists and it is simply a way to access an object’s prototype property in some browsers.

run in console
```
function PrintStuff (myDocuments) {
this.documents = myDocuments;
}

// We add the print () method to PrintStuff prototype property so that other instances (objects) can inherit it:​
PrintStuff.prototype.print = function () {
console.log(this.documents);
}

// Create a new object with the PrintStuff () constructor, thus allowing this new object to inherit PrintStuff's properties and methods.
var newObj = new PrintStuff ("I am a new Object and I can print.");

// newObj inherited all the properties and methods, including the print method, from the PrintStuff function. Now newObj can call print directly, even though we never created a print () method on it.​
newObj.print (); //I am a new Object and I can print.
```

# Why is Prototype Important and When is it Used?
These are two important ways the prototype is used in JavaScript, as we noted above:

1. Prototype Property: Prototype-based Inheritance
Prototype is important in JavaScript because JavaScript does not have classical inheritance based on Classes (as most object oriented languages do), and therefore all inheritance in JavaScript is made possible through the prototype property.
ALSO- Inheritance is a programming paradigm where objects (or Classes in some languages) can inherit properties and methods from other objects (or Classes). In JavaScript, you implement inheritance with the prototype property.

IMPORTANT BANANA EXAMPLE

2. Prototype Attribute: Accessing Properties on Objects
This prototype chain mechanism is essentially the same concept we have discussed above with the prototype-based inheritance, except we are now focusing specifically on how JavaScript accesses object properties and methods via the prototype object.

# Namespacing



# see also 
http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/

