# Classes in JavaScript

The class keyword was introduced in ECMAScript 2015 (ES6) as a new way to define objects and object-oriented programming in JavaScript. A class is a blueprint for creating objects that share the same properties and methods.

### Syntax

Here's the basic syntax for defining a class:

```javascript
class ClassName {
	// class body
}
```

### Example

Here's an example of a simple Person class:

```javascript
class Person {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}

	sayHello() {
		console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
	}
}

const person = new Person("Alice", 30);
person.sayHello(); // output: "Hello, my name is Alice and I am 30 years old."
```

## Constructor

The constructor method is a special method inside a class that gets called when a new object is created using the new keyword. It's used to initialize the object's properties.

### Example

Here's an example of a class with a constructor method:

```javascript
class Person {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}
}
```

## Properties

Properties are the data that a class contains. They're defined inside the class's constructor method.

### Example

Here's an example of a class with properties:

```javascript
class Person {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}
}
```

## Methods

Methods are functions that a class can perform. They're defined outside of the constructor method, but still inside the class.

### Example

Here's an example of a class with methods:

```javascript
class Person {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}

	sayHello() {
		console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
	}
}
```

## Inheritance

Inheritance allows you to create a new class based on an existing class. The new class inherits the properties and methods of the existing class.

### Example

Here's an example of a Student class that inherits from the Person class:

```javascript
class Student extends Person {
	constructor(name, age, grade) {
		super(name, age);
		this.grade = grade;
	}

	study() {
		console.log(`${this.name} is studying in grade ${this.grade}.`);
	}
}

const student = new Student("Bob", 15, 9);
student.sayHello(); // output: "Hello, my name is Bob and I am 15 years old."
student.study(); // output: "Bob is studying in grade 9."
```

In this example, the `Student` class extends the Person class using the extends keyword. The constructor method of the Student class uses the `super` keyword to call the constructor method of the `Person` class and pass in the `name` and `age` parameters. The `study` method is defined on the `Student` class.

## Static Methods

Static methods are methods that are defined on the class itself, rather than on its instances. They're called on the class, rather than on an object.

### Example

Here's an example of a class with a static method:

```javascript
class MathUtils {
	static add(x, y) {
		return x + y;
	}
	static subtract(x, y) {
		return x - y;
	}
}

console.log(MathUtils.add(2, 3)); // output: 5
console.log(MathUtils.subtract(5, 2)); // output: 3
```

In this example, the `MathUtils` class defines two static methods, `add` and `subtract`. These methods can be called directly on the class, without creating an instance of the class.

## Getters and Setters

Getters and setters are special methods that allow you to get and set the values of an object's properties.

### Example

Here's an example of a class with getters and setters:

```
class Person {
  constructor(name, age) {
    this._name = name;
    this._age = age;
  }

  get name() {
    return this._name;
  }

  set name(name) {
    this._name = name;
  }

  get age() {
    return this._age;
  }

  set age(age) {
    if (age > 0 && age < 120) {
      this._age = age;
    } else {
      console.error('Invalid age');
    }
  }
}

const person = new Person('Alice', 30);
console.log(person.name); // output: "Alice"
person.name = 'Bob';
console.log(person.name); // output: "Bob"
console.log(person.age); // output: 30
person.age = 150; // output: "Invalid age"
```

In this example, the `Person` class defines getters and setters for the `name` and `age` properties. The getter for `name` simply returns the value of the `_name` property, while the setter for `name` sets the value of the `_name` property. The getter and setter for `age` perform some validation on the input value before setting the value of the `_age` property.

## Private Properties and Methods

Private properties and methods are properties and methods that are only accessible within the class.

### Example

Here's an example of a class with private properties and methods:

```javascript
class Person {
	#secret = "my secret";

	#privateMethod() {
		console.log("This is a private method.");
	}

	sayHello() {
		console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.My secret is ${this.#secret}.`);
		this.#privateMethod();
	}
}

const person = new Person("Alice", 30);
person.sayHello(); // output: "Hello, my name is Alice and I am 30 years old. My secret is my secret. This is a private method."
console.log(person.#secret); // output: "Uncaught SyntaxError: Private field '#secret' must be declared in an enclosing class"
person.#privateMethod(); // output: "Uncaught SyntaxError: Private field '#privateMethod' must be declared in an enclosing class"
```

In this example, the `Person` class defines a private property `#secret` and a private method `#privateMethod`. These can only be accessed within the `Person` class, and not from outside the class. The `sayHello` method can access the private property and method, but code outside the class cannot access them.
