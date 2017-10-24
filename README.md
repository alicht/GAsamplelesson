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




