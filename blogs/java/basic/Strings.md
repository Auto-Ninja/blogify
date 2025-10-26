## ✨ Strings & StringBuilder in Java

Java provides powerful tools for handling text through the `String` class and the mutable `StringBuilder` class. This guide covers both, including operations, examples, and when to use each.

#### 🧠 What Is a String?
A `String` in Java is an object that represents a sequence of characters. Strings are **immutable**, meaning once created, their value cannot be changed.

#### ✅ Example
```java
String greeting = "Hello";
System.out.println(greeting.length()); // Output: 5
```
📋 Common String Operations

## 📋 Common String Methods in Java

| Method                  | Example Input                    | Output             | Description                          |
|-------------------------|----------------------------------|--------------------|--------------------------------------|
| `length()`              | `"Hello".length()`               | `5`                | Returns number of characters         |
| `charAt(1)`             | `"Hello".charAt(1)`              | `'e'`              | Gets character at index              |
| `substring(1, 4)`       | `"Hello".substring(1, 4)`        | `"ell"`            | Extracts substring                   |
| `toUpperCase()`         | `"hello".toUpperCase()`          | `"HELLO"`          | Converts to uppercase                |
| `toLowerCase()`         | `"HELLO".toLowerCase()`          | `"hello"`          | Converts to lowercase                |
| `trim()`                | `" Java ".trim()`                | `"Java"`           | Removes leading/trailing spaces      |
| `equals("Java")`        | `"Java".equals("Java")`          | `true`             | Checks exact match                   |
| `equalsIgnoreCase("java")` | `"Java".equalsIgnoreCase("java")` | `true`         | Case-insensitive match               |
| `compareTo("Apple")`    | `"Banana".compareTo("Apple")`    | `1`                | Lexicographical comparison           |
| `contains("lo")`        | `"Hello".contains("lo")`         | `true`             | Checks if substring exists           |
| `replace('l', 'x')`     | `"Hello".replace('l', 'x')`      | `"Hexxo"`          | Replaces characters                  |
| `split(",")`            | `"a,b,c".split(",")`             | `["a", "b", "c"]`  | Splits string into array             |
| `indexOf("l")`          | `"Hello".indexOf("l")`           | `2`                | First index of character             |
| `lastIndexOf("l")`      | `"Hello".lastIndexOf("l")`       | `3`                | Last index of character              |
| `startsWith("He")`      | `"Hello".startsWith("He")`       | `true`             | Checks prefix                        |
| `endsWith("lo")`        | `"Hello".endsWith("lo")`         | `true`             | Checks suffix                        |
| `isEmpty()`             | `"".isEmpty()`                   | `true`             | Checks if string is empty            |
| `concat(" World")`      | `"Hello".concat(" World")`       | `"Hello World"`    | Appends string                       |
| `matches("[A-Za-z]+")`  | `"Java".matches("[A-Za-z]+")`    | `true`             | Regex match                          |  

### 🧱 StringBuilder in Java
🔍 What Is StringBuilder?
StringBuilder is a mutable sequence of characters. It allows efficient string manipulation without creating new objects, unlike String.

✅ Example
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Output: Hello World
```
🧠 When to Use StringBuilder

| Use Case                          | Why It's Better                                         |
|----------------------------------|---------------------------------------------------------|
| Repeated string modifications    | Avoids creating multiple intermediate `String` objects |
| Loops that build strings dynamically | More efficient than concatenation (`+`)             |
| Performance-critical string operations  | Faster and less memory-intensive              |
| Thread safety not required       | `StringBuilder` is not synchronized                    |

🔄 Common StringBuilder Methods

## 🔄 Common StringBuilder Methods

| Method                 | Example Usage                     | Output             |
|------------------------|-----------------------------------|--------------------|
| `append(" World")`     | `"Hello".append(" World")`        | `"Hello World"`    |
| `insert(1, "ey")`      | `"Hello".insert(1, "ey")`         | `"Heyello"`        |
| `replace(1, 3, "i")`   | `"Hello".replace(1, 3, "i")`      | `"Hilo"`           |
| `delete(1, 3)`         | `"Hello".delete(1, 3)`            | `"Ho"`             |
| `reverse()`            | `"Hello".reverse()`               | `"olleH"`          |
| `toString()`           | `sb.toString()`                   | Converts to String |

🆚 String vs StringBuilder vs StringBuffer

## 🆚 String vs StringBuilder vs StringBuffer

| Feature       | `String`           | `StringBuilder`                         | `StringBuffer`                     |
|---------------|--------------------|-----------------------------------------|------------------------------------|
| Mutability    | Immutable           | Mutable                                 | Mutable                            |
| Thread-safe   | ✅ Yes              | ❌ No                                    | ✅ Yes                             |
| Performance   | Slower              | Fastest                                 | Slower than `StringBuilder`        |
| Use Case      | Constant strings    | Fast, single-threaded string manipulation | Multi-threaded environments     |

### 🔐 Immutable vs Mutable in Java
Understanding the difference between immutable and mutable objects is key to writing efficient and predictable Java code — especially when working with strings.

#### 🧊 Immutable
Definition: An object whose state cannot be changed after it is created.

Example: String in Java is immutable.

Behavior: Any modification (e.g., concatenation, replacement) creates a new object.

```java
String s1 = "Hello";
String s2 = s1.concat(" World"); // s1 remains "Hello", s2 is "Hello World"
```
Advantages:

- Thread-safe
- Predictable behavior
- Easy to debug

#### 🔧 Mutable
Definition: An object whose state can be changed after it is created.
Example: StringBuilder and StringBuffer are mutable.
Behavior: Modifications happen in-place, without creating new objects.

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // sb is now "Hello World"
```
Advantages:
- More memory-efficient for frequent changes
- Faster performance in loops or large-scale string operations

### 🧠 Summary Table
## 🧬 String vs StringBuilder Properties

| Property         | Immutable (`String`)     | Mutable (`StringBuilder`)       |
|------------------|---------------------------|----------------------------------|
| Can be changed   | ❌ No                     | ✅ Yes                           |
| Thread-safe      | ✅ Yes                    | ❌ No                            |
| Performance      | Slower                    | Faster                           |
| Memory usage     | Higher (new objects)      | Lower (in-place changes)         |