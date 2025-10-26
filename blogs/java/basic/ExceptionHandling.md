## ⚠️ Exception Handling in Java

Exception handling in Java is a mechanism to gracefully handle runtime errors, ensuring the program continues running or fails predictably.

### 🔍 What Is an Exception?
An exception is an event that disrupts the normal flow of a program during execution. Java uses a structured approach to catch and handle these events using:

```java
try {
    // Code that might throw an exception
} catch (ExceptionType e) {
    // Handle the exception
} finally {
    // Optional: always executes
}
```
### 🧬 Types of Exceptions

| Type       | Description                                      | Examples                                 |
|------------|--------------------------------------------------|------------------------------------------|
| Checked    | Must be handled at compile time                  | `IOException`, `SQLException`            |
| Unchecked  | Occur at runtime; not required to be caught      | `NullPointerException`, `ArithmeticException` |
| Errors     | Serious issues that applications should not try to handle | `OutOfMemoryError`, `StackOverflowError` |

### 🧹 How to Dispose an Object
Java has automatic garbage collection, but for resources like files, sockets, or database connections, you should release them manually.

✅ Use finally or try-with-resources
Using finally:
```java
FileInputStream fis = null;
try {
    fis = new FileInputStream("data.txt");
    // Read file
} catch (IOException e) {
    System.out.println("Error reading file");
} finally {
    if (fis != null) {
        try {
            fis.close(); // Dispose manually
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
Using try-with-resources (recommended):
```java
try (FileInputStream fis = new FileInputStream("data.txt")) {
    // Read file
} catch (IOException e) {
    System.out.println("Error reading file");
}
```
### 🔁 Will a Method Always Return When an Exception Occurs?
- If an exception is not caught, the method exits immediately and the exception propagates up the call stack.

- If the exception is caught, the method can return from the catch or finally block.

- If no return is provided and the method expects one, the compiler will throw an error.

Example:
```java
public String getUserName(int id) {
    try {
        return fetchFromDB(id); // might throw SQLException
    } catch (SQLException e) {
        return "Guest"; // fallback return
    }
}
```
## 🔗 Multiple Exception Handling
Java allows multiple catch blocks or a multi-catch block.

Multiple catch:
```java
try {
    int[] arr = new int[3];
    System.out.println(arr[5]); // ArrayIndexOutOfBoundsException
    int x = 10 / 0;             // ArithmeticException
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Index error");
} catch (ArithmeticException e) {
    System.out.println("Math error");
}
```
Multi-catch (Java 7+):
```java
try {
    // risky code
} catch (IOException | SQLException e) {
    System.out.println("I/O or SQL error: " + e.getMessage());
}
```
### 🧨 Custom Exceptions
Custom exceptions help represent domain-specific errors.

Define a Custom Exception:
```java
class PaymentFailedException extends Exception {
    public PaymentFailedException(String message) {
        super(message);
    }
}
```
Use It:
```java
public void processPayment(double amount) throws PaymentFailedException {
    if (amount <= 0) {
        throw new PaymentFailedException("Invalid payment amount.");
    }
}
```
## 🛒 E-Commerce Scenarios
### Multiple Exception Handling in E-Commerce

| Scenario            | Exceptions Handled                                      |
|---------------------|---------------------------------------------------------|
| Checkout            | `PaymentFailedException`, `IOException`, `NullPointerException` |
| Inventory Update    | `SQLException`, `ArrayIndexOutOfBoundsException`        |
| User Authentication | `AuthenticationException`, `IOException`               |

### Custom Exception Examples

| Exception Name             | Purpose                                      | Use Case                  |
|----------------------------|----------------------------------------------|---------------------------|
| `PaymentFailedException`   | Payment gateway error or invalid amount      | During checkout           |
| `ProductNotFoundException` | Product ID not found in catalog              | Viewing product details   |
| `OutOfStockException`      | Product quantity is zero                     | Adding to cart            |
| `InvalidCouponException`   | Coupon code is expired or invalid            | Applying discount         |
| `UserNotAuthorizedException` | User lacks permission for action           | Accessing admin panel     |
### 🔁 Exception Propagation to Base Class or Parent

If a method throws an exception and doesn’t catch it, the exception propagates up the call stack to the calling method. This continues until it’s caught or the program terminates.

Example:
```java
class OrderService {
    public void placeOrder() throws Exception {
        validateStock(); // may throw exception
    }

    public void validateStock() throws Exception {
        throw new Exception("Out of stock");
    }
}

public class Main {
    public static void main(String[] args) {
        OrderService service = new OrderService();
        try {
            service.placeOrder();
        } catch (Exception e) {
            System.out.println("Order failed: " + e.getMessage());
        }
    }
}
```
🔁 Flow:
- placeOrder() calls validateStock()
- validateStock() throws an exception
- placeOrder() doesn’t catch it, so it propagates to main()
- main() catches and handles it

### 🧠 Summary

| Concept                | Key Point                                                                 |
|------------------------|---------------------------------------------------------------------------|
| Exception Types        | Checked, Unchecked, Errors                                                |
| Object Disposal        | Use `finally` or `try-with-resources`                                     |
| Return on Exception    | Only if caught; otherwise, method exits                                   |
| Multiple Exceptions    | Use multiple `catch` blocks or multi-catch                                |
| Custom Exceptions      | Extend `Exception` or `RuntimeException` for domain-specific errors       |
| E-Commerce Use Cases   | Handle payment, inventory, and user errors with custom exceptions         |
| Exception Propagation  | Uncaught exceptions move up the call stack until handled or crash occurs |