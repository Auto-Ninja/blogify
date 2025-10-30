## Repository Pattern
The Repository Pattern is a design pattern that abstracts data access logic and provides a clean interface for querying and persisting domain objects. It’s used to separate business logic from database operations, making code more maintainable, testable, and scalable.

### 🧠 What Is the Repository Pattern?
The Repository Pattern acts as a middle layer between the business logic and the data source (like a database or API). It hides the details of data access and provides a collection-like interface for accessing domain objects.

#### ✅ Why Use It?
- Decouples business logic from data access
- Centralizes data logic in one place
- Improves testability (e.g., mock repositories)
- Supports multiple data sources (e.g., switch from SQL to NoSQL easily)
- Reduces duplication of query code

### 🧱 Structure
```plaintext
[Service Layer]
     ↓
[Repository Interface]
     ↓
[Repository Implementation]
     ↓
[Data Source (DB, API, etc.)]
```
### 💻 Java Example
#### 1. Define a Domain Model
```java
public class Product {
    private int id;
    private String name;
    private double price;
    // Getters and setters
}
```
#### 2. Create a Repository Interface
```java
public interface ProductRepository {
    Product findById(int id);
    List<Product> findAll();
    void save(Product product);
    void delete(int id);
}
```
#### 3. Implement the Repository
```java
public class ProductRepositoryImpl implements ProductRepository {
    private Connection connection;

    public ProductRepositoryImpl(Connection connection) {
        this.connection = connection;
    }

    public Product findById(int id) {
        // JDBC logic to fetch product by ID
    }

    public List<Product> findAll() {
        // JDBC logic to fetch all products
    }

    public void save(Product product) {
        // JDBC logic to insert/update product
    }

    public void delete(int id) {
        // JDBC logic to delete product
    }
}
```
### 🛒 Real-World E-Commerce Example
#### Scenario: Product Catalog Management
In an e-commerce platform:
- The ProductRepository handles all database operations for products.
- The OrderRepository manages order persistence.
- The UserRepository deals with customer data.

This allows the business logic (e.g., checkout, recommendations, inventory updates) to remain clean and focused, while the repository handles all the data access behind the scenes.

```plaintext
[CheckoutService]
 ├── getProductById() → ProductRepository
 ├── saveOrder() → OrderRepository
 └── updateInventory() → InventoryRepository
```
### 📚 Summary
| **Aspect**      | **Benefit**                                         |
|------------------|-----------------------------------------------------|
| **Abstraction**  | Hides data access complexity                        |
| **Reusability**  | Centralized, reusable logic                         |
| **Testability**  | Easy to mock for unit testing                       |
| **Flexibility**  | Swap data sources with minimal change               |