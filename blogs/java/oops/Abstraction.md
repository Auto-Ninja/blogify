# 🧠 Abstraction

Abstraction is the process of hiding internal implementation details and exposing only essential features. It helps developers focus on *what* an object does rather than *how* it does it.

---

## 🔍 Real-Life Analogy

```plaintext
[TV Remote]
 ├── Power Button
 ├── Volume Control
 └── Channel Switch
```
You use the remote without knowing the internal electronics—just the interface.

##  🛠️ Ways to Achieve Abstraction in Java

### 1️⃣ Abstract Class
```plaintext
[Animal] ← abstract class
   ↑
[Dog] ← concrete subclass
```
``` java
abstract class Animal {
    abstract void makeSound();  // abstract method

    void sleep() {
        System.out.println("Sleeping...");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}
```
Cannot instantiate Animal directly.
Dog must implement makeSound().

### 2️⃣ Interface
``` plaintext
[Vehicle] ← interface
   ↑
[Car] ← implementing class
```
``` java
interface Vehicle {
    void start();
}

class Car implements Vehicle {
    public void start() {
        System.out.println("Car starts");
    }
}
```
Provides full abstraction.
Allows multiple implementations.

### 🎯 When to Use Abstraction
Use abstraction when:

```plaintext
✔ You want to define a common contract
✔ You need to hide internal logic
✔ You’re building scalable APIs or frameworks
✔ You want to decouple high-level logic from low-level details
```
## 🛒 E-Commerce Example
```plaintext
[Payment] ← abstract class
   ↑
[CreditCard]   [PayPal] ← concrete classes
```
```java
abstract class Payment {
    abstract void processPayment();
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
### ✅ Benefits of Abstraction
```plaintext
✔ Simplifies complex systems
✔ Improves maintainability
✔ Enhances security
✔ Supports modular design
```