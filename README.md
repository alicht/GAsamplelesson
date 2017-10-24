# GAsamplelesson

Looking at concept of inheritance and how it relates JavaScript. When we code we want to build something that has a vast amount of objects, all of whom share a small bit of similiar functionality. Javascript provides us witha  very nice blueprint object that will pass those similiar properties to every single one of the objects we have made. 

-the objects we've built so far have some secret properties we've never seen before. These objects we're given properties just as soon as we've created them. ex: valueOf, constructor, toString, isProtoTypeOf. 

All of these come from an object's prototype. When a generic object is creted it's passed many important properties.

INHERITANCE- passing down properties is called inheritance.
Inheritance helps prevent overcoding multiple properties and methods into similiar objects.

All of the native JS data structures we've been learning about- like Array, String, Function, etc- inherit their properties and methods from their very own prototypes... and all those inherit from the Object prototype. 

# 2

Using inheritance we can create new objects with our existing objects as prototypes. 
//new object
var shoe = {size:6, gender: "womens", construction: "slipper" }
// creating a new object that uses shoe as a prototype
var magicShoe = Object.create ( shoe ); // whatever we pass in will be the prototype for the new object
-if we logged out magicShow we'd see that it's exactly the same as shoe because it inherited all of shoes properties

can add new properties to magicShoe: 
magicshoe.jewels = "ruby";
magicshoe.travelAction = "click heels";
magicshoe.actionRequired = 3;

How to create other types of shoes
var shoe = {size: undefined, gender: undefined, constructor: undefined}
// now to automate our property assignment
We need to determine common properties of a shoe class. 
Class- a set of objects that all share and inherit from the same basic prototype

Lets list common properties that we can expect ALL shoes to have and we're ready to build a constructor for our class.
Constructor- will allow us to set up inheritance while also assigning specific property values. 
// capitolize this function to distinguish it as a maker of an entire class of objects
function Shoe(shoeSize, shoeColor, shoeGender, constructionStyle){
this.size = shoeSize; 
thus.color = shoeColor;
this.gender = shoeGender;
this.construction = constructionStyle;
}
// this is going to refer to the new instance of the class that is made

Javascript's "new" keyword produces a new Object of the class (ie instantiates it)
var beachShoe = new Shoe(10, "blue", "womens", "flip-flop");

assign a constructor to a prototype 11:49


__proto__ vs protype
But Firefox and most versions of Safari and Chrome have a __proto__ “pseudo” property (an alternative syntax) that allows you to access an object’s prototype property. You will likely never use this __proto__ pseudo property, but you should know that it exists and it is simply a way to access an object’s prototype property in some browsers.

run in console

function PrintStuff (myDocuments) {
​this.documents = myDocuments;
}
​
​// We add the print () method to PrintStuff prototype property so that other instances (objects) can inherit it:​
PrintStuff.prototype.print = function () {
console.log(this.documents);
}
​
​// Create a new object with the PrintStuff () constructor, thus allowing this new object to inherit PrintStuff's properties and methods.​
​var newObj = new PrintStuff ("I am a new Object and I can print.");
​
​// newObj inherited all the properties and methods, including the print method, from the PrintStuff function. Now newObj can call print directly, even though we never created a print () method on it.​
newObj.print (); //I am a new Object and I can print.

# Why is Prototype Important and When is it Used?
These are two important ways the prototype is used in JavaScript, as we noted above:

1. Prototype Property: Prototype-based Inheritance
Prototype is important in JavaScript because JavaScript does not have classical inheritance based on Classes (as most object oriented languages do), and therefore all inheritance in JavaScript is made possible through the prototype property.
ALSO- Inheritance is a programming paradigm where objects (or Classes in some languages) can inherit properties and methods from other objects (or Classes). In JavaScript, you implement inheritance with the prototype property.

IMPORTANT BANANA EXAMPLE

2. Prototype Attribute: Accessing Properties on Objects
This prototype chain mechanism is essentially the same concept we have discussed above with the prototype-based inheritance, except we are now focusing specifically on how JavaScript accesses object properties and methods via the prototype object.






