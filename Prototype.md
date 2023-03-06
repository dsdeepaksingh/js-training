# Prototypes in JavaScript

Prototypes are the backbone of object-oriented programming in JavaScript and are used to create and share functionality between objects.

## What is a Prototype in JavaScript?

In JavaScript, a prototype is an object that serves as a blueprint for other objects. Every object in JavaScript has a prototype, which can be either another object or null. When a property or method is accessed on an object, JavaScript first looks for it on the object itself. If it is not found, it then looks for it on the object's prototype, and so on up the prototype chain until it reaches the root object.

## How to create objects using Prototypes.

To create an object using a prototype, we use the constructor function. A constructor function is a function that creates objects with a specific prototype. Here is an example:

Here is an example:

```javascript
function Person(name, age) {
	this.name = name;
	this.age = age;
}

let person1 = new Person("John", 30);
let person2 = new Person("Jane", 25);
```

In this example, the Person function is the constructor function. It creates objects with the Person.prototype object as their prototype. The new keyword is used to create a new object with the Person.prototype object as its prototype.

## How to add properties and methods to prototypes

To add properties and methods to a prototype, we can simply assign them to the prototype object. Here is an example:

```javascript
function Person(name, age) {
	this.name = name;
	this.age = age;
}

Person.prototype.greet = function () {
	console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

let person1 = new Person("John", 30);
let person2 = new Person("Jane", 25);

person1.greet(); // Output: "Hello, my name is John and I am 30 years old."
person2.greet(); // Output: "Hello, my name is Jane and I am 25 years old."
```

In this example, we added a greet method to the Person.prototype object. This method is then available to all objects created with the Person constructor function.

## How to inherit properties and methods from prototypes

To inherit properties and methods from a prototype, we can simply access them on the object. If the property or method is not found on the object, JavaScript will look for it on the object's prototype. Here is an example:

```javascript
function Animal(name) {
	this.name = name;
}

Animal.prototype.makeSound = function () {
	console.log("This animal makes a sound.");
};

function Dog(name) {
	Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.makeSound = function () {
	console.log("This dog barks.");
};

let dog1 = new Dog("Buddy");
dog1.makeSound(); // Output: "This dog barks."
```

In this example, the Dog constructor function inherits the makeSound method from the Animal prototype. We do this by setting the Dog.prototype object to a new object that has the Animal.prototype object as its prototype.

## How to override prototype properties and methods

To override a prototype property or method, we can simply assign a new value to it on the object. Here is an example:

```javascript
function Animal(name) {
	this.name = name;
}

Animal.prototype.makeSound = function () {
	console.log("This animal makes a sound.");
};

function Dog(name) {
	Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.makeSound = function () {
	console.log("This dog barks.");
};

let dog1 = new Dog("Buddy");
dog1.makeSound(); // Output: "This dog barks."
```

In this example, we overrode the makeSound method of the Dog prototype with a new method that logs "This dog barks." instead of the default "This animal makes a sound." method.

## Practice Exercises

#### Exercise 1:

Create a constructor function called Person that takes two arguments name and age. Add a method called introduce to the Person.prototype object that logs "Hello, my name is {name} and I am {age} years old." to the console.

Create two instances of the Person object, one called person1 with the name "John" and age 30, and one called person2 with the name "Jane" and age 25. Call the introduce method on both instances and check that they output the correct message to the console.

#### Exercise 2:

Create a constructor function called Shape that takes one argument type. Add a method called area to the Shape.prototype object that returns 0. Override the area method in each of the following shape constructor functions:

Square: takes one argument sideLength and calculates the area by multiplying the sideLength by itself.
Rectangle: takes two arguments width and height and calculates the area by multiplying the width by the height.
Circle: takes one argument radius and calculates the area by multiplying pi (Math.PI) by the radius squared.
Create an instance of each shape object and call the area method on each instance, checking that the correct value is returned.

#### Exercise 3:

Create a constructor function called Vehicle that takes one argument type. Add a method called drive to the Vehicle.prototype object that logs "Driving a {type} vehicle." to the console.

Create two constructor functions called Car and Bike that inherit from the Vehicle prototype. Override the drive method in each of the constructor functions to log a different message.

Create an instance of each vehicle object and call the drive method on each instance, checking that the correct message is output to the console.

#### Exercise 4:

Create a constructor function called BankAccount that takes two arguments owner and balance. Add a method called deposit to the BankAccount.prototype object that adds a specified amount to the balance. Add a method called withdraw to the BankAccount.prototype object that subtracts a specified amount from the balance. Add a method called getBalance to the BankAccount.prototype object that returns the current balance.

Create an instance of the BankAccount object and assign it to a variable called account1. Deposit $100 into account1 using the deposit method. Withdraw $50 from account1 using the withdraw method. Call the getBalance method on account1 and check that the correct balance is output to the console.
