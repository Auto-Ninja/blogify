# 🧩 Interface Segregation Principle (ISP)

## ✅ What is ISP?

The **Interface Segregation Principle** states:

> "Clients should not be forced to depend on interfaces they do not use."

In other words, **don’t create fat interfaces**. Instead, split them into smaller, more specific ones so that classes only implement what they actually need.

---

## 🛒 Real-World Example: E-Commerce Notification System

Let’s say we have a `NotificationChannel` interface that includes multiple methods:

### ❌ Violates ISP

```java
interface NotificationChannel {
    void sendEmail(String message);
    void sendSMS(String message);
    void sendPush(String message);
}
```
Now, if we create an EmailSender class:
```java
class EmailSender implements NotificationChannel {
    public void sendEmail(String message) { ... }
    public void sendSMS(String message) { throw new UnsupportedOperationException(); }
    public void sendPush(String message) { throw new UnsupportedOperationException(); }
}
```
- EmailSender is forced to implement methods it doesn’t need.
- This violates ISP.

## ✅ ISP-Compliant Design
Split the interface into smaller, focused ones:
```java
interface EmailChannel {
    void sendEmail(String message);
}

interface SMSChannel {
    void sendSMS(String message);
}

interface PushChannel {
    void sendPush(String message);
}
```
Now each class only implements what it needs:
```java
class EmailSender implements EmailChannel {
    public void sendEmail(String message) { ... }
}

class SMSSender implements SMSChannel {
    public void sendSMS(String message) { ... }
}

class PushSender implements PushChannel {
    public void sendPush(String message) { ... }
}
```
```plaintext
[EmailChannel] → [EmailSender]
[SMSChannel] → [SMSSender]
[PushChannel] → [PushSender]

No class is forced to implement unused methods ✅
```
### 📌 Benefits of ISP
| Benefit | Description |
|---------|-------------|
| ✅ Cleaner Interfaces | Smaller, focused contracts |
| ✅ Better Maintainability | Less risk of breaking unrelated features |
| ✅ Easier Testing | Each class has fewer responsibilities |
| ✅ More Flexibility | Classes can mix and match interfaces as needed |
### ⚠️ Common Pitfall
Avoid designing interfaces that try to cover every possible use case. Instead, think in terms of roles or capabilities — and split accordingly.