# javascript-oop-interview-questions-fresher
Welcome! This repository contains **JavaScript Object-Oriented Programming (OOP) interview questions** for **freshers**. It covers **basic to advanced topics**, with **MCQs**, **coding examples**, and explanations.

---

## Table of Contents
1. [Basics of OOP](#basics-of-oop)
2. [Classes and Objects](#classes-and-objects)
3. [Methods and Properties](#methods-and-properties)
4. [Inheritance](#inheritance)
5. [Polymorphism](#polymorphism)
6. [Access Modifiers](#access-modifiers)
7. [Prototype & Prototype Chain](#prototype--prototype-chain)
8. [MCQs](#mcqs)

---
## Basics of OOP
- **What is OOP in JavaScript?**  
  Object-Oriented Programming (OOP) is a way to structure code using **objects** that contain **properties (data)** and **methods (functions)**.

- **Class vs Object:**  
  | Class (Blueprint) | Object (Instance) |
  |-----------------|----------------|
  | Template for objects | Real object created from class |
  | Cannot hold real data | Holds actual data |
  | Example: Recipe | Example: Cake made from recipe |

---

## Four Main Principles of OOP

1. **Encapsulation**  
   Wrapping **data** and **methods** together in an object. This helps **hide internal details** and protects object integrity.

2. **Abstraction**  
   Hiding unnecessary details and exposing only **essential functionality** to the user. It simplifies complex systems.

3. **Inheritance**  
   Allows **child objects or classes** to inherit **properties and methods** from parent objects/classes. This promotes **code reuse**.

4. **Polymorphism**  
   The ability to use a **single method or interface** in multiple ways. This allows objects to behave differently based on context.

---

## Classes and Objects
```javascript
// Class
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  greet() {
    console.log("Hi, I am " + this.name);
  }
}

// Object (instance)
const person1 = new Person("Mohsin", 24);
person1.greet(); // Hi, I am Mohsin
```
## Methods and Properties

In **JavaScript OOP**, methods and properties define the **behavior and data** of objects. There are different types of methods and ways to define properties.

---

### Instance Methods
- Belong to the **object instance** created from a class.  
- Can access instance properties using `this`.  

```javascript
class Person {
  constructor(name, age) {
    this.name = name; // instance property
    this.age = age;
  }

  greet() { // instance method
    console.log(`Hi, I am ${this.name}`);
  }
}

const person1 = new Person("Mohsin", 24);
person1.greet(); // Hi, I am Mohsin
```
### 3.2 Static Methods
- Static methods **belong to the class itself**, not to object instances.  
- They are useful for **utility or helper functions** that don’t need instance data.  

**Example:**
```javascript
class Calculator {
  static add(a, b) {
    return a + b;
  }
}

console.log(Calculator.add(5, 3)); // 8

const calc = new Calculator();
console.log(calc.add(5, 3)); // Error! add is not a function
```
### Getters and Setters
- **Getters** allow reading property values.  
- **Setters** allow setting property values with optional validation.  
- They provide **encapsulation** by controlling access to private or protected data.

**Example:**
```javascript
class Person {
  constructor(name) {
    this._name = name; // protected-by-convention property
  }

  // Getter
  get name() {
    return this._name;
  }

  // Setter
  set name(value) {
    if(value.length > 0) this._name = value;
    else console.log("Name cannot be empty");
  }
}

const person1 = new Person("Mohsin");
console.log(person1.name); // Mohsin

person1.name = "Khan"; // sets new name
console.log(person1.name); // Khan
```
## Inheritance

**Inheritance** in JavaScript OOP allows a **child class/object** to inherit **properties and methods** from a **parent class/object**. This promotes **code reuse** and helps create **hierarchical relationships**.

---

### 4.1 Single Inheritance
- A child class inherits from **one parent class**.  
- The child can access **all public and protected properties/methods** of the parent.

```javascript
class Animal {
  eat() {
    console.log("Animal eats");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Dog barks");
  }
}

const dog = new Dog();
dog.eat();  // Animal eats (inherited)
dog.bark(); // Dog barks (own method)
```
### 4.2 Multilevel Inheritance

- **Multilevel Inheritance** occurs when a class inherits from a class, which itself inherits from another class.  
- This shows a **hierarchical relationship** between multiple classes and allows **child classes to access properties and methods** of all ancestors.

```javascript
class Animal {
  eat() {
    console.log("Animal eats");
  }
}

class Mammal extends Animal {
  sleep() {
    console.log("Mammal sleeps");
  }
}

class Dog extends Mammal {
  bark() {
    console.log("Dog barks");
  }
}

const dog = new Dog();
dog.eat();   // Animal eats
dog.sleep(); // Mammal sleeps
dog.bark();  // Dog barks
```
## Polymorphism

**Polymorphism** is a core principle of OOP that allows the **same method or interface** to be used in **different ways** depending on the context.  

In JavaScript, polymorphism is mostly achieved through:

1. **Method Overriding** (runtime polymorphism)  
2. **Simulated Function Overloading** (manual approach, since JS does not support compile-time overloading)

---

### 5.1 Types of Polymorphism
Polymorphism can be divided into **two main types**:

1. **Compile-Time Polymorphism (Static Polymorphism)**  
   - Achieved using **function overloading** or **operator overloading**.  
   - JS does not support true compile-time overloading, but we can **simulate it** using **default parameters, rest parameters, or arguments object**.  

2. **Run-Time Polymorphism (Dynamic Polymorphism)**  
   - Achieved using **method overriding** or **virtual functions**.  
   - The function that gets executed is determined **at runtime** based on the object calling it.

---

### 5.2 Example of Method Overriding (Run-Time Polymorphism)
```javascript
class Animal {
  makeSound() {
    console.log("Some generic sound");
  }
}

class Dog extends Animal {
  makeSound() {
    console.log("Woof! Woof!");
  }
}

class Cat extends Animal {
  makeSound() {
    console.log("Meow! Meow!");
  }
}

const dog = new Dog();
const cat = new Cat();

dog.makeSound(); // Woof! Woof!
cat.makeSound(); // Meow! Meow!
```
### 5.3 Example of Simulated Function Overloading (Compile-Time Polymorphism)

- JavaScript **does not support true function overloading** like Java or C++, but we can **simulate it** using:
  - **Default parameters**
  - **Rest parameters**
  - **Arguments object**

**Example using default parameters:**
```javascript
function add(a, b) {
  if (b === undefined) return a + a; // single argument
  return a + b;                     // two arguments
}

console.log(add(5));    // 10
console.log(add(5, 3)); // 8
```
## Access Modifiers

Access modifiers are keywords used in object-oriented programming to set the accessibility of class members (properties and methods). In JavaScript (ES6+), access modifiers include `public`, `private`, and `protected` (via convention or TypeScript).  

### 1. Public
- Members are accessible from anywhere (default in JavaScript).
```javascript
class User {
  name; // public by default
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

const user = new User("Mohsin");
console.log(user.name); // Accessible
user.greet();           // Accessible
```
## Private Access Modifier

- Private members are only accessible **within the class**.  
- In modern JavaScript (ES6+), private fields are denoted using `#`.

### Example:
```javascript
class User {
  #password; // private field
  constructor(name, password) {
    this.name = name;
    this.#password = password;
  }

  showPassword() {
    console.log(this.#password); // Accessible inside the class
  }
}

const user = new User("Mohsin", "12345");
console.log(user.#password); // ❌ Error: Private field '#password' must be declared in an enclosing class
user.showPassword();         // ✅ Outputs: 12345
```
## Protected (Convention-based)

- JavaScript does **not have built-in protected access** like some other languages.  
- By **convention**, an underscore `_` is used to indicate a member is intended to be "protected" (accessible in subclasses but not outside the class).

### Example:
```javascript
class User {
  _role; // protected by convention
  constructor(name, role) {
    this.name = name;
    this._role = role;
  }
}

class Admin extends User {
  showRole() {
    console.log(this._role); // ✅ Accessible in subclass
  }
}

const admin = new Admin("Mohsin", "Admin");
admin.showRole();      // ✅ Outputs: Admin
console.log(admin._role); // ❌ Should not be accessed outside class (by convention)
```
## Prototype & Prototype Chain

In JavaScript, every object has a **prototype**, which is another object that it inherits properties and methods from. This forms a **prototype chain** used for property/method lookup.

### 1. Prototype
- A prototype is an object from which other objects inherit properties and methods.
- All JavaScript objects have a prototype except the base `Object`.

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person("Mohsin", 24);
person1.greet(); // Outputs: Hello, my name is Mohsin
```
## Prototype Chain

- In JavaScript, objects can inherit properties and methods from other objects via a **prototype chain**.  
- When accessing a property or method, JavaScript first looks in the object itself. If not found, it searches up the prototype chain until it finds it or reaches `null`.

### Example:
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person("Mohsin");

console.log(person1.name);           // ✅ Found in object: "Mohsin"
console.log(person1.greet());        // ✅ Found in prototype: "Hello, my name is Mohsin"
console.log(person1.__proto__ === Person.prototype);        // true
console.log(Person.prototype.__proto__ === Object.prototype); // true
console.log(Object.prototype.__proto__);                   // null (end of chain)
```
## MCQs

### 1. Which of the following is **not a principle of OOP**?  
a) Encapsulation  
b) Inheritance  
c) Abstraction  
d) Recursion  

**Answer:** d) Recursion

---

### 2. Which access modifier is **default in JavaScript classes**?  
a) private  
b) public  
c) protected  
d) internal  

**Answer:** b) public

---

### 3. How do you declare a **private field** in JavaScript?  
a) `_fieldName`  
b) `#fieldName`  
c) `$fieldName`  
d) `private fieldName`  

**Answer:** b) `#fieldName`

---

### 4. What is **encapsulation** in JavaScript?  
a) Hiding internal details and exposing only the necessary interface  
b) Ability to create multiple classes from one  
c) Sharing methods using prototype  
d) Overriding a method in child class  

**Answer:** a) Hiding internal details and exposing only the necessary interface

---

### 5. Which keyword is used to create a class in JavaScript?  
a) `function`  
b) `object`  
c) `class`  
d) `new`  

**Answer:** c) `class`

---

### 6. What is the main purpose of **abstraction**?  
a) Show only relevant information and hide complexity  
b) Allow objects to share methods  
c) Make a class inherit from another class  
d) Convert an object to JSON  

**Answer:** a) Show only relevant information and hide complexity

---

### 7. Which of the following statements about **inheritance** is true?  
a) A class can inherit properties and methods from another class  
b) JavaScript does not support inheritance  
c) Inheritance only works with functions, not classes  
d) Prototype has nothing to do with inheritance  

**Answer:** a) A class can inherit properties and methods from another class

---

### 8. Which of the following is an example of **polymorphism** in JavaScript?  
a) Using the same method name with different implementations  
b) Hiding private fields with `#`  
c) Using the prototype chain to share methods  
d) Declaring multiple classes  

**Answer:** a) Using the same method name with different implementations

---

### 9. Which of the following is **true about prototype chain**?  
a) Every object has a prototype except `Object.prototype`  
b) Prototype chain allows property/method lookup in parent objects  
c) Prototype methods are shared across instances  
d) All of the above  

**Answer:** d) All of the above

---

### 10. What is **method overriding**?  
a) Redefining a parent class method in a child class  
b) Calling a function multiple times  
c) Creating multiple functions with the same name in one class  
d) Deleting a method from an object  

**Answer:** a) Redefining a parent class method in a child class

---

### 11. Which of the following is an example of **runtime polymorphism** in JavaScript?  
a) Method overriding in subclasses  
b) Private fields with `#`  
c) Static methods in a class  
d) Using `new Object()`  

**Answer:** a) Method overriding in subclasses

---

### 12. What is the output of the following code?
```javascript
class Person {
  #age = 25;
}
const p = new Person();
console.log(p.#age);
```
a) 25
b) undefined
c) Error
d) null
**Answer:**: c) Error (private field cannot be accessed outside the class)
### 13. How are protected members represented in JavaScript?

a) #field  
b) _field (by convention)  
c) protected field  
d) field  

**Answer:** b) _field (by convention)

---

### 14. Which statement is true about objects in JavaScript?

a) Objects can have properties and methods  
b) Objects inherit from prototypes  
c) Objects are dynamic (properties can be added/removed)  
d) All of the above  

**Answer:** d) All of the above

---

### 15. What is constructor in a JavaScript class?

a) A function to create and initialize objects  
b) A property of the class  
c) A type of variable  
d) A method to delete objects  

**Answer:** a) A function to create and initialize objects


