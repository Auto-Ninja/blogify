## 📦 Collections 
### 🔍 What Are Collections?
A collection is simply a container that holds multiple objects. Java provides a Collections Framework—a set of classes and interfaces—to store, retrieve, and manipulate groups of data efficiently.

### 🧠 Why Use Collections?
 - Arrays have fixed size. Collections are dynamic.
 - Collections offer built-in methods for sorting, searching, filtering, etc.
 - They help organize data logically (e.g., lists, sets, maps).

### 🧩 Common Collection Types
## 📦 Java Collection Types

| **Collection Type** | **Description**           | **Example**                          |
|---------------------|---------------------------|--------------------------------------|
| `List`              | Ordered, allows duplicates| Shopping cart items                  |
| `Set`               | Unordered, no duplicates  | Unique product categories            |
| `Map`               | Key-value pairs           | Product ID → Product details         |
| `Queue`             | FIFO structure            | Order processing queue               |


### ✅ Example: Using a List
```java
import java.util.*;

public class CartExample {
    public static void main(String[] args) {
        List<String> cart = new ArrayList<>();
        cart.add("Laptop");
        cart.add("Mouse");
        cart.add("Laptop"); // duplicates allowed

        System.out.println(cart);
    }
}
```
## 🧬 Generics
### 🔍 What Are Generics?
Generics allow you to write code that works with any data type while maintaining type safety. Instead of using raw types, you specify the type using angle brackets < >.

### 🧠 Why Use Generics?
- Prevents runtime errors (e.g., ClassCastException)
- Eliminates need for casting
- Makes code cleaner and more readable

### ✅ Example: List with Generics
```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
// names.add(123); // ❌ Compile-time error

String first = names.get(0); // No casting needed
System.out.println(first);
```
Without generics, you'd have to cast manually:

```java
List names = new ArrayList(); // raw type
names.add("Alice");
String first = (String) names.get(0); // manual cast
```
### 🛒 Real-World E-Commerce Scenario
#### 🛍️ Shopping Cart with Collections + Generics
```java
class Product {
    String name;
    double price;
    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
}

List<Product> cart = new ArrayList<>();
cart.add(new Product("Laptop", 999.99));
cart.add(new Product("Mouse", 49.99));
```
- List<Product> ensures only Product objects go into the cart.
- You can loop through the cart and calculate totals, apply discounts, etc.

✅ Summary
## 📊 Collections vs Generics in Java

| **Feature**   | **Collections**                          | **Generics**                                 |
|---------------|-------------------------------------------|----------------------------------------------|
| **Purpose**   | Store multiple objects                    | Add type safety to collections               |
| **Benefit**   | Dynamic storage, built-in methods         | Prevents errors, cleaner code                |
| **Real Use**  | Cart, catalog, orders                     | Ensures correct types in cart, catalog       |
