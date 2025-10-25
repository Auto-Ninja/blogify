# 🧩 Open/Closed Principle (OCP)

## ✅ What is OCP?

The **Open/Closed Principle** states:

> "Software entities (classes, modules, functions) should be **open for extension** but **closed for modification**."

This means you should be able to **add new functionality** without changing existing code. Instead of editing existing classes, you extend them.


## 🛒 Real-World Example: E-Commerce Notification System

Let’s say your system sends notifications via **Email** and **SMS**. Later, you want to add **Push Notifications**.

### ❌ Without OCP

```java
class NotificationService {
    void notify(String type, String message) {
        if (type.equals("email")) {
            // send email
        } else if (type.equals("sms")) {
            // send SMS
        } else if (type.equals("push")) {
            // send push notification
        }
    }
}
```
- Every time you add a new channel, you modify NotificationService.
- Violates OCP: not closed for modification.

### ✅ With OCP
Use abstraction and polymorphism to extend behavior:

```java
// NotificationChannel.java
interface NotificationChannel {
    void send(String message);
}

// EmailSender.java
class EmailSender implements NotificationChannel {
    public void send(String message) {
        // send email
    }
}

// SMSSender.java
class SMSSender implements NotificationChannel {
    public void send(String message) {
        // send SMS
    }
}

// PushSender.java
class PushSender implements NotificationChannel {
    public void send(String message) {
        // send push notification
    }
}

// NotificationService.java
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

You can now add new channels (e.g., WhatsAppSender) without touching NotificationService.

Follows OCP: open for extension, closed for modification.

```plaintext
[NotificationService]
 └── uses → [NotificationChannel Interface]
               ├── [EmailSender]
               ├── [SMSSender]
               └── [PushSender]
```
Add new: [WhatsAppSender] → no change to NotificationService
### 📌 Benefits of OCP
| Benefit | Description |
| --- | --- |
| ✅ Scalability | Add new features without breaking existing code |
| ✅ Maintainability | Reduces risk of bugs when adding functionality |
| ✅ Flexibility | Supports plugin-like architecture |
| ✅ Testability | Each channel can be tested independently |
### ⚠️ Common Pitfall
Avoid using if-else or switch statements to handle behavior that can be abstracted. Instead, use interfaces or inheritance to extend behavior.