# 🔄 Dependency Inversion Principle (DIP)

## ✅ What is DIP?

The **Dependency Inversion Principle** states:

> "High-level modules should not depend on low-level modules. Both should depend on abstractions."

And:

> "Abstractions should not depend on details. Details should depend on abstractions."

This principle encourages **decoupling** by introducing **interfaces or abstract classes** between high-level logic and low-level implementations.

---

## 🛒 Real-World Example: E-Commerce Notification System

Let’s say `NotificationService` sends messages using `EmailSender` and `SMSSender`.

### ❌ Violates DIP

```java
class NotificationService {
    EmailSender emailSender = new EmailSender();
    SMSSender smsSender = new SMSSender();

    void notify(String message) {
        emailSender.send(message);
        smsSender.send(message);
    }
}
```
- NotificationService directly depends on concrete classes.
- Any change in EmailSender or SMSSender affects NotificationService.

## ✅ DIP-Compliant Design
Introduce an abstraction:
```java
interface NotificationChannel {
    void send(String message);
}
```
Implementations:
```java
class EmailSender implements NotificationChannel {
    public void send(String message) { ... }
}

class SMSSender implements NotificationChannel {
    public void send(String message) { ... }
}
```
High-level module depends on abstraction:
```java
class NotificationService {
    List<NotificationChannel> channels;

    NotificationService(List<NotificationChannel> channels) {
        this.channels = channels;
    }

    void notifyAll(String message) {
        for (NotificationChannel channel : channels) {
            channel.send(message);
        }
    }
}
```
Now NotificationService is decoupled from specific implementations.

```plaintext
[NotificationService] → depends on → [NotificationChannel Interface]
                                ↑
                [EmailSender] [SMSSender] [PushSender]
```
- High-level module (NotificationService) depends on abstraction.
- Low-level modules (EmailSender, etc.) implement the abstraction.

| Benefit | Description |
|---|---|
| ✅ Decoupling | High-level logic is independent of implementation details |
| ✅ Flexibility | Swap implementations without changing core logic |
| ✅ Testability | Easily mock interfaces for unit testing |
| ✅ Maintainability | Changes in low-level modules don’t ripple upward |
### ⚠️ Common Pitfall
Avoid directly instantiating concrete classes in high-level modules. Use constructor injection, factories, or dependency injection frameworks to supply dependencies.