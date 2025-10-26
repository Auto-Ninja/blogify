## 🧩 Methods in Java
A method in Java is a block of code that performs a specific task. It is defined inside a class and can be executed when called.

### 🔁 Method Syntax
```java
accessModifier returnType methodName(parameters) {
    // method body
}
```
Example
```java
public int add(int a, int b) {
    return a + b;
}
```
### 🎯 Return Types in Java Methods
The return type defines what a method returns after execution.

| Return Type  | Description                 | Example                          |
|--------------|-----------------------------|----------------------------------|
| `void`       | No return value             | `public void greet() { ... }`   |
| `int`        | Returns an integer          | `public int getAge() { ... }`   |
| `String`     | Returns a string            | `public String getName() { ... }` |
| `boolean`    | Returns true or false       | `public boolean isValid() { ... }` |
| Custom Type  | Returns an object of a class| `public Car getCar() { ... }`   |
### 🔐 Access Modifiers
Access modifiers control the visibility of methods:

## 🔐 Java Access Modifiers

| Modifier   | Access Level                          | Usage Example                     |
|------------|----------------------------------------|-----------------------------------|
| `public`   | Accessible from any class              | `public void show()`              |
| `private`  | Accessible only within the same class  | `private void calculate()`        |
| `protected`| Accessible within package and subclasses| `protected void display()`       |
| *default*  | Accessible within the same package     | `void log()` *(no modifier used)* |

Learn more about access modifiers

### 🧪 Using Methods in a Class
- ✅ With Object (Instance Method)
```java
public class Calculator {
    public int multiply(int a, int b) {
        return a * b;
    }
}
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator(); // create object
        int result = calc.multiply(4, 5);   // call method
        System.out.println(result);         // Output: 20
    }
}
```
- ✅ Without Object (Static Method)
```java
public class MathUtils {
    public static int square(int x) {
        return x * x;
    }
}
public class Main {
    public static void main(String[] args) {
        int result = MathUtils.square(6); // call static method directly
        System.out.println(result);       // Output: 36
    }
}
```
### 🧠 Summary
- Methods encapsulate logic and promote code reuse.
- Return types define what a method gives back.
- Access modifiers control visibility.
- Instance methods require objects; static methods do not.