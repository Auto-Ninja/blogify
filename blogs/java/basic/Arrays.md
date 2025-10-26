## 📦 What Is an Array in Java?
An array is a container object that holds a fixed number of values of a single data type. Each element is accessed by its index, starting from 0.


```java
int[] numbers = {10, 20, 30, 40};
System.out.println(numbers[2]); // Output: 30
```
### 🛠️ Uses of Arrays in Java
Arrays are used when:

You need to store multiple values of the same type (e.g., student scores, product prices).

You want fast access to elements using indices.

You need to perform operations like sorting, searching, or iteration.

You want to pass collections of data to methods.

### 🧬 Types of Arrays in Java
Java supports several types of arrays:

#### 1. Single-Dimensional Array
Stores elements in a linear form.

```java
int[] marks = new int[5];
marks[0] = 85;
```
#### 2. Multi-Dimensional Array
An array of arrays. Most commonly used is the 2D array.

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```
#### 3. Jagged Array
A special type of multi-dimensional array where sub-arrays can have different lengths.

```java
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[3];
jagged[2] = new int[1];
``` 
#### 4. Array of Objects
You can store objects in arrays too.

```java
String[] cars = {"Volvo", "BMW", "Ford"};
```
### 📋 Summary Table

| Type               | Description                  | Example                                 |
|--------------------|------------------------------|-----------------------------------------|
| Single-Dimensional | Linear list of elements      | `int[] arr = {1, 2, 3}`                 |
| Multi-Dimensional  | Matrix-style array           | `int[][] grid = {{1,2},{3,4}}`          |
| Jagged Array       | Uneven sub-arrays            | `int[][] jagged = new int[3][]`         |
| Array of Objects   | Stores objects like Strings or custom types | `String[] names = {"Alice", "Bob"}` |
