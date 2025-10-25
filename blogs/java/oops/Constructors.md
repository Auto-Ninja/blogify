### 🏗️ What Is a Constructor?
A constructor is a special method in Java that is called when an object is created. Its job is to initialize the object.

✅ Key Characteristics
- Has the same name as the class
- No return type (not even void)
- Automatically invoked when new is used

💡 Example
```java
class Product {
    String name;
    double price;

    Product() {
        name = "Unknown";
        price = 0.0;
    }
}
```

## 🧩 Types of Constructors

| Type                     | Description                                         | Example                               |
|--------------------------|-----------------------------------------------------|---------------------------------------|
| Default Constructor       | No parameters; sets default values                  | `Product()`                          |
| Parameterized Constructor  | Accepts parameters to set custom values             | `Product(String name, double price)` |
| Copy Constructor          | Creates a new object by copying another             | `Product(Product other)` (manual in Java) |

### 🎯 Why Use Constructors?
- To initialize fields when an object is created
- To enforce required values at creation
- To support overloading for flexibility
- To simplify object setup in complex classes

### 🧬 Constructors with Inheritance
When a class inherits from another, the parent constructor is called first. You can use `super()` to invoke it.

💡 Example
```java
class Product {
    String name;
    Product(String name) {
        this.name = name;
    }
}

class Book extends Product {
    String author;

    Book(String name, String author) {
        super(name); // calls Product constructor
        this.author = author;
    }
}
```

✅ Notes
- If the parent has no default constructor, you must call `super(...)`
- Constructors are not inherited, but they can be chained

### 🔁 Constructor Overloading
Yes, constructors can be overloaded — meaning you can define multiple constructors with different parameter lists.

💡 Example
```java
class Product {
    String name;
    double price;

    Product() {
        this("Unknown", 0.0);
    }

    Product(String name) {
        this(name, 0.0);
    }

    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
}
```
- Overloading improves flexibility
- You can use `this(...)` to call another constructor in the same class


### 📊 Constructor Features Summary

| Feature                   | Supported? | Notes                                      |
|---------------------------|------------|--------------------------------------------|
| Default Constructor        | ✅         | Auto-created if no other constructor exists |
| Parameterized Constructor   | ✅         | Custom initialization                       |
| Copy Constructor           | ✅ (manual) | Java doesn’t auto-generate it              |
| Inheritance Support        | ✅         | Use super() to call parent constructor      |
| Overloading               | ✅         | Multiple constructors with different parameters |


### 🧩 What Is a Parameterized Constructor?
A parameterized constructor is a constructor that accepts arguments to initialize an object with specific values.

```java
class Product {
    String name;
    double price;

    // Parameterized constructor
    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
}
```

### 📦 All Parameterized Constructor Examples

1. ✅ Basic Parameterized Constructor
```java
class User {
    String username;
    int age;

    User(String username, int age) {
        this.username = username;
        this.age = age;
    }
}
```

2. 🔁 Constructor Overloading
Multiple constructors with different parameter lists:
```java
class Book {
    String title;
    String author;
    double price;

    Book(String title) {
        this.title = title;
        this.author = "Unknown";
        this.price = 0.0;
    }

    Book(String title, String author) {
        this.title = title;
        this.author = author;
        this.price = 0.0;
    }

    Book(String title, String author, double price) {
        this.title = title;
        this.author = author;
        this.price = price;
    }
}
```

3. 🔗 Constructor Chaining (Using `this()`)
```java
class Customer {
    String name;
    String email;

    Customer(String name) {
        this(name, "not_provided@example.com");
    }

    Customer(String name, String email) {
        this.name = name;
        this.email = email;
    }
}
```

4. 🧬 Parameterized Constructor with Inheritance
```java
class Product {
    String name;

    Product(String name) {
        this.name = name;
    }
}
class Electronics extends Product {
    int warranty;

    Electronics(String name, int warranty) {
        super(name); // calls Product constructor
        this.warranty = warranty;
    }
}
```

5. 📋 Copy Constructor (Manual in Java)
```java
class Order {
    int orderId;
    String item;

    Order(int orderId, String item) {
        this.orderId = orderId;
        this.item = item;
    }

    // Copy constructor
    Order(Order other) {
        this.orderId = other.orderId;
        this.item = other.item;
    }
}
```
### 📌 Summary Table

| Type       | Description                                      | Example                               |
|------------|--------------------------------------------------|---------------------------------------|
| Basic      | Initializes fields with parameters                | `User(String name, int age)`         |
| Overloaded | Multiple constructors with different parameters   | `Book(String title, ...)`            |
| Chained    | Calls another constructor in same class           | `this(name, email)`                   |
| Inherited  | Calls parent constructor                           | `super(name)`                         |
| Copy       | Creates object from another                       | `Order(Order other)`                  |