# 📐 Single Responsibility Principle (SRP)

## ✅ What is SRP?

The **Single Responsibility Principle** states:

> "A class should have only one reason to change."

This means each class should focus on a **single task or responsibility**. If a class handles multiple concerns, changes in one area may affect unrelated functionality, making the system harder to maintain.


## 🛒 Real-World Example: E-Commerce Notification System

Imagine an e-commerce platform that sends notifications to users when:

- An order is placed
- A shipment is dispatched
- A promotion is launched

### ❌ Without SRP

```plaintext
[NotificationManager]
 ├── sendEmail()
 ├── sendSMS()
 ├── logNotification()
 └── formatMessage()
```
This class handles too many responsibilities: formatting, sending, and logging. Any change in one area (e.g., switching SMS provider) risks breaking others.

✅ With SRP
```plaintext
[EmailSender] → sends email
[SMSSender] → sends SMS
[MessageFormatter] → formats messages
[NotificationLogger] → logs notifications
[NotificationService] → orchestrates everything
```
Each class has one clear responsibility. Changes are isolated and easier to manage.

```java
// MessageFormatter.java
class MessageFormatter {
    String format(String type, String content) {
        return "[" + type + "] " + content;
    }
}

// EmailSender.java
class EmailSender {
    void send(String email, String message) {
        // logic to send email
    }
}

// SMSSender.java
class SMSSender {
    void send(String phone, String message) {
        // logic to send SMS
    }
}

// NotificationLogger.java
class NotificationLogger {
    void log(String message) {
        // save to log file or database
    }
}

// NotificationService.java
class NotificationService {
    MessageFormatter formatter = new MessageFormatter();
    EmailSender emailSender = new EmailSender();
    SMSSender smsSender = new SMSSender();
    NotificationLogger logger = new NotificationLogger();

    void notifyUser(String email, String phone, String type, String content) {
        String message = formatter.format(type, content);
        emailSender.send(email, message);
        smsSender.send(phone, message);
        logger.log("Notification sent: " + message);
    }
}
```
### 📌 Benefits of SRP
- ✅ **Maintainability**: Easier to update or fix one part without affecting others
- ✅ **Testability**: Each class can be tested independently
- ✅ **Reusability**: Components like MessageFormatter can be reused elsewhere
- ✅ **Scalability**: New channels (e.g., push notifications) can be added easily

### ⚠️ Common Pitfall

Avoid mixing unrelated logic in one class. If a class does more than one thing, ask: "Will I ever need to change one part without touching the other?" If yes, split it!