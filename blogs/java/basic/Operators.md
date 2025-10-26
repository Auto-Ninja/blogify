## ⚙️ Java Operators

Java operators are special symbols used to perform operations on variables and values. They are essential for arithmetic, logic, decision-making, and control flow in Java programs.

### 📋 Types of Operators

| Operator Type | Purpose                     | Example                |
| ------------- | --------------------------- | ---------------------- |
| Arithmetic    | Basic math operations       | a + b, a % b           |
| Relational    | Compare values              | a > b, a == b          |
| Logical       | Combine boolean expressions | a && b, !a             |
| Assignment    | Assign values               | a = 5, a += 3          |
| Unary         | Operate on one operand      | ++a, -a                |
| Bitwise       | Bit-level operations        | a & b, a << 2          |
| Ternary       | Conditional expression      | (a > b) ? a : b        |
| Instanceof    | Type checking               | obj instanceof String  |
| Type Cast     | Convert data types          | (int) 3.14, (double) 5 |

### 🧮 Arithmetic Operators

```java
int a = 10, b = 3;
System.out.println(a + b); // 13
System.out.println(a % b); // 1
```

### 🔍 Relational Operators

```java
int x = 5, y = 10;
System.out.println(x < y);  // true
System.out.println(x == y); // false
```

### 🔗 Logical Operators

```java
boolean a = true, b = false;
System.out.println(a && b); // false
System.out.println(a || b); // true
```

### 📝 Assignment Operators

```java
int x = 5;
x += 3; // x = x + 3 → 8
x *= 2; // x = x * 2 → 16
```

### ➕ Unary Operators

```java
int a = 5;
System.out.println(++a); // 6
System.out.println(-a);  // -6
```

### 🧠 Bitwise Operators

```java
int a = 5, b = 3;
System.out.println(a & b);  // 1
System.out.println(a << 1); // 10
```

### ❓ Ternary Operator

```java
int a = 10, b = 20;
int max = (a > b) ? a : b;
System.out.println(max); // 20
```

### 🧬 Instanceof Operator

```java
String s = "Hello";
System.out.println(s instanceof String); // true
```

### 🔄 Type Cast Operator

```java
double d = 9.7;
int i = (int) d;
System.out.println(i); // 9
```

### 📘 Java Operators Summary

Java provides a rich set of operators to perform operations on variables and values. These operators are categorized based on the type of operation they perform.

#### Arithmetic Operators
```plaintext
+ : Addition → a + b

- : Subtraction → a - b

* : Multiplication → a * b

/ : Division → a / b

% : Modulus (remainder) → a % b
```
#### Relational Operators
```plaintext
== : Equal to → a == b

!= : Not equal to → a != b

> : Greater than → a > b

< : Less than → a < b

>= : Greater than or equal to → a >= b

<= : Less than or equal to → a <= b
```
#### Logical Operators
```plaintext
&& : Logical AND → a && b (true if both are true)

|| : Logical OR → a || b (true if at least one is true)

! : Logical NOT → !a (true if a is false)
```
#### Assignment Operators
```plaintext
= : Assign → x = 10

+= : Add and assign → x += 5

-= : Subtract and assign → x -= 3

*= : Multiply and assign → x *= 2

/= : Divide and assign → x /= 4

%= : Modulus and assign → x %= 3
```
#### Unary Operators
```plaintext
+ : Unary plus → +a

- : Unary minus → -a

++ : Increment → ++a or a++

-- : Decrement → --a or a--

! : Logical NOT → !flag
```
#### Bitwise Operators
```plaintext
& : Bitwise AND → a & b

| : Bitwise OR → a | b

^ : Bitwise XOR → a ^ b

~ : Bitwise complement → ~a

<< : Left shift → a << 2

>> : Right shift → a >> 1

>>> : Unsigned right shift → a >>> 1
```
#### Ternary Operator
```plaintext
? : : Conditional → (a > b) ? a : b
```
#### Type Checking
```plaintext
instanceof : Checks object type → obj instanceof String
```
#### Type Casting
```plaintext
(type) : Converts data type → (int) 3.14
```