# 🔁 Liskov Substitution Principle (LSP)

## ✅ What is LSP?

The **Liskov Substitution Principle** states:

> "Objects of a superclass should be replaceable with objects of its subclasses without altering the correctness of the program."

In simpler terms:  
If class `B` is a subclass of class `A`, then we should be able to use `B` wherever `A` is expected — **without breaking the application**.

---

## 🛒 Real-World Example: E-Commerce Notification System

We already have a `NotificationChannel` interface with implementations like `EmailSender`, `SMSSender`, and `PushSender`.

### ✅ LSP-Compliant Design

```java
// NotificationChannel.java
interface NotificationChannel {
    void send(String message);
}

// EmailSender.java
class EmailSender implements NotificationChannel {
    public void send(String message) {
        System.out.println("Email sent: " + message);
    }
}

// SMSSender.java
class SMSSender implements NotificationChannel {
    public void send(String message) {
        System.out.println("SMS sent: " + message);
    }
}

// NotificationService.java
class NotificationService {
    void notifyUser(NotificationChannel channel, String message) {
        channel.send(message); // Works with any subclass of NotificationChannel
    }
}
```
### ✅ Usage
```java
NotificationService service = new NotificationService();
service.notifyUser(new EmailSender(), "Order confirmed!");
service.notifyUser(new SMSSender(), "Your package has shipped!");
```
- EmailSender and SMSSender can substitute NotificationChannel without breaking anything.
- This is LSP in action.

## ❌ LSP Violation Example
Let’s say we add a new DatabaseLogger class that implements NotificationChannel, but doesn’t actually send notifications:

```java
class DatabaseLogger implements NotificationChannel {
    public void send(String message) {
        throw new UnsupportedOperationException("Logging only, not a notification channel");
    }
}
```
Now if we do:
```java
service.notifyUser(new DatabaseLogger(), "Promo launched!");
```
💥 It throws an exception — this violates LSP because DatabaseLogger cannot truly substitute NotificationChannel.

```plaintext
[NotificationChannel] (interface)
 ├── [EmailSender] ✅
 ├── [SMSSender] ✅
 └── [DatabaseLogger] ❌ (breaks LSP)
 ```
## 📌 LSP Checklist
| ✅ Good | ❌ Bad |
| --- | --- |
| Subclass honors the contract of the base class | Subclass throws unexpected exceptions |
| Subclass preserves expected behavior | Subclass changes method meaning |
| Subclass can be used interchangeably | Subclass breaks client code |

## 🧠 Key Takeaways
LSP ensures polymorphism works safely.

Violations often happen when subclasses override methods improperly or don’t fully implement the interface.

Use interfaces and abstract classes carefully to define clear contracts.