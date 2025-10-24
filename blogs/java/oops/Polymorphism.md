# 🔀 Polymorphism 

Polymorphism allows objects or methods to take on many forms. Java supports two main types: **Compile-Time (Static)** and **Run-Time (Dynamic)**.

---

## 1️⃣ Compile-Time Polymorphism (Method Overloading)

### 📌 Concept Diagram

```plaintext
[Calculator]
 ├── add(int, int)
 ├── add(double, double)
 └── add(int, int, int)
```

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```
#### 🧪 Usage
```java
Calculator calc = new Calculator();
calc.add(5, 10);        // int version
calc.add(5.5, 3.2);     // double version
calc.add(1, 2, 3);      // three-arg version
```
## 2️⃣ Run-Time Polymorphism (Method Overriding)
📌 Concept Diagram
```plaintext
[Animal] ← reference
   ↑
[Dog] or [Cat] ← actual object
```
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void sound() {
        System.out.println("Cat meows");
    }
}
```
#### 🧪 Usage
```java
Animal a;

a = new Dog();
a.sound();  // Output: Dog barks

a = new Cat();
a.sound();  // Output: Cat meows
```
## 🛒 Real-World Analogy: E-Commerce Payments
### 📌 Concept Diagram
```plaintext
[Payment] ← reference
   ↑
[CreditCard] or [PayPal] ← actual object
```
```java
class Payment {
    void processPayment() {
        System.out.println("Processing generic payment");
    }
}

class CreditCard extends Payment {
    void processPayment() {
        System.out.println("Processing credit card payment");
    }
}

class PayPal extends Payment {
    void processPayment() {
        System.out.println("Processing PayPal payment");
    }
}
```
#### 🧪 Usage
```java
Payment p;

p = new CreditCard();
p.processPayment();  // Output: Processing credit card payment

p = new PayPal();
p.processPayment();  // Output: Processing PayPal payment
```
### 📚 Summary

| Type          | Mechanism           | Resolution Time | Example                               |
|---------------|---------------------|------------------|---------------------------------------|
| Compile-Time  | Method Overloading   | Compile Time     | add(int, int) vs add(double, double) |
| Run-Time      | Method Overriding    | Runtime          | sound() in Dog vs Cat                 |
