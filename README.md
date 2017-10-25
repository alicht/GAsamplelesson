# GAsamplelesson

# What are prototypes?

Prototypes are the underlying blueprint of an object, and are the baseline from which other instances of that particular object can be created. Javascript provides us with a very nice blueprint object that will pass those similiar properties to every single one of the objects we have made. by default, all objects in JavaScript are automatically created with the property prototype.

(show an object that has methods we created... but then also show how it has methods that are "invisible" ie that were there the whole time... run in browser and terminal to see results)


# Why is Prototype Important and When is it Used?
These are two important ways the prototype is used in JavaScript, as we noted above:

1. Prototype Property: Prototype-based Inheritance
Prototype is important in JavaScript because JavaScript does not have classical inheritance based on Classes (as most object oriented languages do), and therefore all inheritance in JavaScript is made possible through the prototype property.
In JavaScript, we implement inheritance with the prototype property.

Looking at concept of inheritance and how it relates JavaScript. 




# 2 Prototypal Constructors
When we create a use case of an Object, we use something called a Constructor. Constructors are used to create instances of objects.

Let's start by creating a new object.
```
//new object
var shoe = {size:6, gender: "womens", construction: "slipper" }
```

We say that an Object instance inherits from its parent object ie the prototype. What we mean is that each time we create a new Object (using the keyword 'new'), that Object immediately and automatically has access to all of the properties defined in the parent object. In our Shirt example, this means that every single time we make a new Shirt, they have access to all of the properties defined in the Constructor (size, gender, construction, etc)...and this is known as Prototypal Inheritance (more commonly referenced as just inheritance). 

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
# 3 Methods

How to create other types of shoes
var shoe = {size: undefined, gender: undefined, constructor: undefined}
// now to automate our property assignment
We need to determine common properties of a shoe class. 
Class- a set of objects that all share and inherit from the same basic prototype

Lets list common properties that we can expect ALL shoes to have and we're ready to build a constructor for our class.
Constructor- will allow us to set up inheritance while also assigning specific property values.
```
// we capitalize this function to distinguish it as a maker of an entire class of objects
function Shoe(shoeSize, shoeColor, shoeGender, constructionStyle){
this.size = shoeSize; 
thus.color = shoeColor;
this.gender = shoeGender;
this.construction = constructionStyle;
}
// this is going to refer to the new instance of the class that is made
```

Javascript's "new" keyword produces a new Object of the class (ie instantiates it)
```
var beachShoe = new Shoe(10, "blue", "womens", "flip-flop");
```
assign functions to a prototype
```
Shoe.prototype = {
putOn: function() {alert ("Shoe's On!");}, 
takeOff: function() {alert ("Shoe's Off!");}
}
```
Now every subsequent shoe function will inherit these for when it needs them. 
```
var beachShoe = new Shoe(10, "blue", "womens", "flip-flop");
```
Now when we call 
```
beachShoe.takeOff(); //will look and see that beachShoe has this takeOff method and since it doesn't, will go a level above and look at the Shoe object which DOES have it and will thus call it from there. 
```


run in console


-- why would coders use it?
INHERITANCE- passing down properties is called inheritance.
Inheritance helps prevent overcoding multiple properties and methods into similiar objects.

Programmers love inheritance, because it keeps our code neat and organized, and because it saves us from having to define all the properties belonging to an Object each time we need to make a new instance.



# Namespacing



# see also 
http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/

Inline-style: 
![alt text](https://memegenerator.net/instance/72706299/david-pumpkins-snl-any-questions "Logo Title Text 1")

