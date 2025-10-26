## Control Flow in Java
Control flow in Java refers to the order in which statements and instructions are executed. Java provides several control flow mechanisms to make decisions, repeat actions, and alter execution paths.

### 🔁 Conditional Statements
#### if, else if, else
```java
int age = 20;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```
#### switch
```java
int day = 3;

switch (day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    default: System.out.println("Invalid day");
}
```
### 🔄 Looping Statements
#### for loop
```java
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}
```
#### while loop
```java
int i = 0;
while (i < 5) {
    System.out.println("i = " + i);
    i++;
}
```
#### do-while loop
```java
int i = 0;
do {
    System.out.println("i = " + i);
    i++;
} while (i < 5);
```
### ⏭️ Branching Statements
#### break
```java
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
    System.out.println(i);
}
```
#### continue
```java
for (int i = 0; i < 5; i++) {
    if (i == 2) continue;
    System.out.println(i);
}
```
#### return
```java
int square(int x) {
    return x * x;
}
````
### 📋 Summary Table

| Type        | Statement(s)               | Purpose                        |
|-------------|----------------------------|--------------------------------|
| Conditional | `if`, `else`, `switch`     | Make decisions                 |
| Looping     | `for`, `while`, `do-while` | Repeat code blocks             |
| Branching   | `break`, `continue`, `return` | Alter or exit flow early    |
