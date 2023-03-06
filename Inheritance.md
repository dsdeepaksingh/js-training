# Inheritance in JavaScript

Inheritance is one of the most important concepts in Object-Oriented Programming. It allows creating new classes by extending an existing class. JavaScript is a prototype-based language, which means that it uses prototypes to implement inheritance. In this tutorial, we will explore inheritance in JavaScript.

### Prerequisites:

To understand inheritance in JavaScript, you need to have a basic understanding of the following concepts:

- Objects
- Constructors
- Prototypes
- Functions

## Creating a Base Class:

The first step in implementing inheritance is to create a base class. A base class is a class that contains common properties and methods that can be inherited by other classes.

Let's create a base class called "Vehicle" that has a "make" and "model" property and a "start" method:

```javascript
function Vehicle(make, model) {
	this.make = make;
	this.model = model;
}

Vehicle.prototype.start = function () {
	console.log("Starting " + this.make + " " + this.model);
};
```

In the above code, we have defined a constructor function "Vehicle" that takes two arguments "make" and "model". We have also defined a method "start" on the prototype of the "Vehicle" function.

Creating a Subclass:

Now that we have created a base class, we can create a subclass that inherits from the base class. A subclass is a class that inherits properties and methods from the base class.

Let's create a subclass called "Car" that inherits from the "Vehicle" class:

```javascript
function Car(make, model, year) {
	Vehicle.call(this, make, model);
	this.year = year;
}

Car.prototype = Object.create(Vehicle.prototype);
Car.prototype.constructor = Car;

Car.prototype.start = function () {
	console.log("Starting " + this.make + " " + this.model + " (" + this.year + ")");
};
```

In the above code, we have defined a constructor function "Car" that takes three arguments "make", "model", and "year". We have also called the "Vehicle" constructor using the "call" method to set the "make" and "model" properties of the Car instance.

We have also set the prototype of the "Car" function to be an instance of the "Vehicle" function using the "Object.create" method. This allows the "Car" function to inherit properties and methods from the "Vehicle" function.

We have also set the "constructor" property of the "Car.prototype" to point to the "Car" function. This is necessary because the "Object.create" method sets the "constructor" property to point to the "Vehicle" function.

Finally, we have defined a "start" method on the "Car.prototype" that overrides the "start" method of the "Vehicle.prototype". This method logs the make, model, and year of the car to the console.

## Creating an Instance of a Subclass:

Now that we have created a subclass, we can create an instance of it:

```javascript
var myCar = new Car("Honda", "Civic", 2021);
myCar.start(); // Starting Honda Civic (2021)
```

In the above code, we have created an instance of the "Car" class using the "new" operator and passed in the "make", "model", and "year" arguments.

We have also called the "start" method on the "myCar" instance, which logs the make, model, and year of the car to the console.

## Inheritance using Factory Function

In JavaScript, you can also achieve inheritance using factory functions. Factory functions allow you to create objects that inherit from a prototype object, similar to how prototypal inheritance works.

Here's an example of factory function inheritance in JavaScript:

```javascript
function createPerson(name, age) {
	let person = {};

	person.name = name;
	person.age = age;

	person.sayHello = function () {
		console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
	};

	return person;
}

let john = createPerson("John", 30);

function createEmployee(name, age, salary) {
	let employee = createPerson(name, age);

	employee.salary = salary;

	employee.saySalary = function () {
		console.log(`My salary is ${this.salary}.`);
	};

	return employee;
}

let jane = createEmployee("Jane", 25, 50000);

john.sayHello(); // logs "Hello, my name is John and I'm 30 years old."
jane.sayHello(); // logs "Hello, my name is Jane and I'm 25 years old."
jane.saySalary(); // logs "My salary is 50000."
```

In this example, we have a createPerson factory function that creates objects with name and age properties and a sayHello method. We then have a createEmployee factory function that creates objects with name, age, salary properties, and a saySalary method.

To achieve inheritance between the two factory functions, we call createPerson inside createEmployee and assign the resulting object to employee. This sets up the prototype chain so that employee inherits properties and methods from the person object created by createPerson.

By using factory function inheritance, we can create objects with unique properties and methods while still reusing code and inheriting behavior from a prototype object.

## Practice Exercises:

#### Exercise 1:

Create a class called Vehicle with the following properties:

make (string): representing the vehicle's make
model (string): representing the vehicle's model
year (number): representing the vehicle's year of manufacture
Create a subclass called Car that inherits from the Vehicle class with an additional property:

numDoors (number): representing the number of doors on the car
Create an instance of the Car class and set the values of its properties. Then, log the instance to the console.

#### Exercise 2:

Create a class called Shape with the following properties:

color (string): representing the shape's color
numSides (number): representing the number of sides on the shape
Create a subclass called Rectangle that inherits from the Shape class with additional properties:

width (number): representing the width of the rectangle
height (number): representing the height of the rectangle
Add a method to the Rectangle class called area() that calculates the area of the rectangle (width \* height).

Create an instance of the Rectangle class and set the values of its properties. Then, log the instance and its area to the console.

#### Exercise 3:

Create a class called Animal with the following properties:

species (string): representing the animal's species
numLegs (number): representing the number of legs the animal has
Create a subclass called Bird that inherits from the Animal class with additional properties:

canFly (boolean): representing whether or not the bird can fly
wingSpan (number): representing the bird's wingspan
Add a method to the Bird class called fly() that returns a string indicating whether or not the bird can fly.

Create an instance of the Bird class and set the values of its properties. Then, log the instance and the result of calling its fly() method to the console.
