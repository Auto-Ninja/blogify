# 🔗 Coupling vs 📦 Cohesion – Software Design Principles
Understanding **coupling** and **cohesion** is essential for building maintainable, scalable, and modular software systems.

---

## 🔗 What Is Coupling?

**Coupling** refers to the degree of interdependence between software modules. It measures how closely connected two classes or components are.

### ✅ Types of Coupling

| Type          | Description                                         | Example                                             |
|---------------|-----------------------------------------------------|-----------------------------------------------------|
| **Low Coupling**  | Modules interact through well-defined interfaces. Changes in one module don’t affect others. | `OrderService` calls `PaymentService` via an interface. |
| **High Coupling** | Modules are tightly connected. A change in one module may break others. | `OrderService` directly handles payment logic. |

### 📌 Visual Diagram

```plaintext
Low Coupling:
[OrderService] → [PaymentService]

High Coupling:
[OrderService ↔ Payment Logic Embedded]
```
```java
// Low Coupling
class PaymentService {
    void processPayment() { ... }
}

class OrderService {
    PaymentService paymentService = new PaymentService();
    void placeOrder() {
        paymentService.processPayment();
    }
}
```
## 📦 What Is Cohesion?
Cohesion refers to how closely related the responsibilities of a single module are. It measures how focused a class is on a single task.

### ✅ Types of Cohesion

| Type          | Description                                   | Example                                           |
|---------------|-----------------------------------------------|---------------------------------------------------|
| **High Cohesion** | A class performs one well-defined task.     | `InvoiceService` handles invoice generation only. |
| **Low Cohesion**  | A class performs unrelated tasks.           | `UtilityClass` handles logging, emailing, and calculations. |

### 📌 Visual Diagram
```plaintext
High Cohesion:
[InvoiceService]
 ├── calculateTotal()
 └── printInvoice()

Low Cohesion:
[UtilityClass]
 ├── calculateTotal()
 ├── sendEmail()
 └── logActivity()
```
```java
// High Cohesion
class InvoiceService {
    void calculateTotal() { ... }
    void printInvoice() { ... }
}

// Low Cohesion
class UtilityClass {
    void calculateTotal() { ... }
    void sendEmail() { ... }
    void logActivity() { ... }
}
```
## 🛒 Real-World E-Commerce Analogy
```plaintext
[CartService] → [InventoryService]
   ↑ cohesive      ↑ loosely coupled
CartService only handles cart operations → High Cohesion
```
InventoryService is accessed via interface → Low Coupling

### ✅ Best Practices
```plaintext
✔ Aim for LOW Coupling
✔ Aim for HIGH Cohesion
✔ Use interfaces and dependency injection
✔ Refactor large classes into focused modules
✔ Avoid mixing unrelated responsibilities
```
## 📚 Summary Table
| Principle | Goal                  | Benefit                             |
|-----------|-----------------------|-------------------------------------|
| Coupling  | Reduce interdependence | Easier maintenance and testing      |
| Cohesion  | Increase internal focus | Better readability and reusability  |