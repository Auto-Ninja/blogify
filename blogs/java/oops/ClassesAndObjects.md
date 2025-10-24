<!-- class.md -->

# 📘 Java Classes and Objects

> A foundational concept in Java that models real-world entities using classes and objects.

## 🧱 Class

A **class** is a blueprint for creating objects. It defines:
- Properties (fields)
- Behaviors (methods)

### Example:
```java
public class Car {
    String color;
    int speed;

    void drive() {
        System.out.println("Car is driving");
    }
}
```
## 🚗 Object

An object is an instance of a class. It holds actual values for the fields defined in the class.

### Example:
```java
Car myCar = new Car();
myCar.color = "Red";
myCar.speed = 100;
myCar.drive();
```

## ✨ new Keyword

The new keyword is used to instantiate a class. It:
- Allocates memory in the heap
- Calls the constructor to initialize the object
- Returns a reference to the object

### Syntax:
```java
ClassName obj = new ClassName();
```



