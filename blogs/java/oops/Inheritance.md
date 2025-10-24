# 🧬 Inheritance 

Inheritance is a fundamental concept in Object-Oriented Programming (OOP) that allows one class to inherit fields and methods from another. It promotes code reuse, logical hierarchy, and modular design.

---

## 📘 What Is Inheritance?

Inheritance enables a **child class (subclass)** to acquire properties and behaviors from a **parent class (superclass)**.

### 🔑 Benefits
- **Code Reusability**: Common logic written once in the parent class.
- **Extensibility**: Child classes can override or extend parent behavior.
- **Maintainability**: Centralized updates in the parent class.

---

## 🧩 Types of Inheritance in Java

Java supports several types of inheritance. Here's a breakdown with visual diagrams and code examples.

---

### 1. Single Inheritance

One class inherits from another.

```plaintext
   [Animal]
      ↑
   [Dog]
```
```java

class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}
```
### 2. Multilevel Inheritance
A class inherits from a subclass which itself inherits from another class.

``` plaintext
   [Animal]
      ↑
   [Dog]
      ↑
 [Puppy]
```
```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

class Puppy extends Dog {
    void weep() {
        System.out.println("Weeping...");
    }
}
```
### 3. Hierarchical Inheritance
Multiple classes inherit from a single parent class.

```plaintext
         [Animal]
         ↑     ↑
     [Dog]   [Cat]
```
```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Meowing...");
    }
}

```
### 4. Multiple Inheritance (via Interfaces)
Java does not support multiple inheritance with classes but allows it through interfaces.

``` plaintext
 [Flyable]   [Swimmable]
      ↑         ↑
         [Duck]
```
```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() {
        System.out.println("Flying...");
    }

    public void swim() {
        System.out.println("Swimming...");
    }
}
```
### 5. Hybrid Inheritance
Combination of multiple types, achieved using interfaces.
```plaintext
 [Animal]     [Pet]
      ↑         ↑
         [Dog]
```
```java
interface Animal {
    void eat();
}

interface Pet {
    void play();
}

class Dog implements Animal, Pet {
    public void eat() {
        System.out.println("Eating...");
    }

    public void play() {
        System.out.println("Playing...");
    }
}
```
## 🛒 Real-World E-Commerce Example
```plaintext
         [User]
         ↑     ↑
   [Customer] [Admin]
         ↑
 [PremiumCustomer]
```
```java
class User {
    String name;
    String email;
}

class Customer extends User {
    String cartId;
}

class Admin extends User {
    void manageUsers() { ... }
}

class PremiumCustomer extends Customer {
    int loyaltyPoints;
}
```
### 📚 Summary
Inheritance helps structure applications by modeling real-world relationships and promoting clean, maintainable code. 
- Share common logic across classes
- Build scalable systems
- Implement role-based behaviors
