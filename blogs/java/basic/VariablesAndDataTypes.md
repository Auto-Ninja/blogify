## 🧠 What Are Variables in Java?
A variable is a named memory location used to store data. In Java, every variable must be declared with a data type that defines the kind of value it can hold.

### ✅ Variable Declaration Syntax
```java
dataType variableName = value;
```
💡 Example
```java
int age = 25;
String name = "Alice";
boolean isMember = true;
```

### 🧩 Types of Variables in Java

| Type | Scope | Description |
|------|-------|-------------|
| Local | Inside methods or blocks | Exists only during method execution |
| Instance | Inside a class (non-static) | Belongs to each object |
| Static | Inside a class (with static) | Shared across all objects |

### 📦 Java Data Types Overview
Java has two categories of data types:

1. Primitive Data Types (8 types)
These are built-in and store simple values.

| Data Type | Description | Size | Allowed Values |
|-----------|------------|------|----------------|
| byte | Small integer | 8-bit | -128 to 127 |
| short | Medium integer | 16-bit | -32,768 to 32,767 |
| int | Standard integer | 32-bit | -2,147,483,648 to 2,147,483,647 |
| long | Large integer | 64-bit | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| float | Decimal number | 32-bit | ~±3.4e38 (7 digits precision) |
| double | Precise decimal | 64-bit | ~±1.8e308 (15 digits precision) |
| char | Single character | 16-bit | Unicode characters ('A', '9', '@') |
| boolean | True/false | 1-bit (logical) | true or false |

#### 💡 Primitive Example
```java
byte b = 100;
int age = 30;
float price = 19.99f;
char grade = 'A';
boolean isActive = true;
```

2. Reference (Non-Primitive) Data Types
These store objects and complex structures.

| Data Type | Description | Example |
|-----------|-------------|---------|
| String | Sequence of characters | "Hello" |
| Array | Collection of elements | int[] scores = {90, 80, 70}; |
| Class | Custom object | Product p = new Product(); |
| Interface | Contract for classes | Runnable r = new Task(); |

### 🧪 Example Program
```java
public class UserProfile {
    public static void main(String[] args) {
        String name = "Alice";
        int age = 28;
        boolean isPremium = true;
        double balance = 105.75;

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Premium Member: " + isPremium);
        System.out.println("Account Balance: $" + balance);
    }
}
```

### 📌 Summary Table
| Category | Type | Example | Allowed Values |
|----------|------|---------|----------------|
| Primitive | int | int age = 25; | -2.1B to +2.1B |
| Primitive | boolean | boolean active = true; | true, false |
| Primitive | char | char grade = 'A'; | Any Unicode char |
| Reference | String | String name = "Bob"; | Any text |
| Reference | Array | int[] scores = {90, 80}; | Multiple values |
| Reference | Class | Product p = new Product(); | Custom objects |