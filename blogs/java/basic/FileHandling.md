## 📁 File Handling in Java
Java provides a rich set of APIs in the java.io and java.nio packages to handle files. You can read, write, and manipulate files using streams, buffers, and readers.

### 🔄 Key Concepts
#### 1. Stream
A stream is a sequence of data. 
Java uses:
- InputStream: for reading byte data
- OutputStream: for writing byte data
- Used for binary files (images, audio, etc.).

#### 2. Reader
A Reader reads character data from a file. 
Common types:
- FileReader: reads characters from a file
- InputStreamReader: bridges byte streams to character streams

#### 3. BufferedReader / BufferedWriter
Buffers improve performance by reducing disk access:
- BufferedReader: wraps a Reader to read text efficiently
- BufferedWriter: wraps a Writer to write text efficiently

### 📄 Reading and Writing .txt Files
✅ Read .txt using BufferedReader
```java
try (BufferedReader reader = new BufferedReader(new FileReader("data.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
✍️ Write .txt using BufferedWriter
```java
try (BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
    writer.write("Hello, world!");
    writer.newLine();
    writer.write("Java file handling.");
} catch (IOException e) {
    e.printStackTrace();
}
```
### 📊 Reading and Writing .csv Files
✅ Read .csv line by line
```java
try (BufferedReader reader = new BufferedReader(new FileReader("data.csv"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        String[] values = line.split(",");
        System.out.println(Arrays.toString(values));
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
✍️ Write .csv
```java
try (BufferedWriter writer = new BufferedWriter(new FileWriter("output.csv"))) {
    writer.write("Name,Age,Location");
    writer.newLine();
    writer.write("Alice,30,London");
} catch (IOException e) {
    e.printStackTrace();
}
```
### 🧾 Reading and Writing .json Files
Use libraries like Gson, Jackson, or org.json.

✅ Read .json using Gson
```java
import com.google.gson.Gson;
import java.io.FileReader;

class User {
    String name;
    int age;
}

try (FileReader reader = new FileReader("user.json")) {
    Gson gson = new Gson();
    User user = gson.fromJson(reader, User.class);
    System.out.println(user.name + " is " + user.age);
} catch (IOException e) {
    e.printStackTrace();
}
```
✍️ Write .json using Gson
```java
User user = new User();
user.name = "Alice";
user.age = 30;

try (FileWriter writer = new FileWriter("user.json")) {
    Gson gson = new Gson();
    gson.toJson(user, writer);
} catch (IOException e) {
    e.printStackTrace();
}
```
### 🧠 Summary Table

| File Type | Read Method                          | Write Method                         | Notes                          |
|-----------|--------------------------------------|--------------------------------------|--------------------------------|
| `.txt`    | `BufferedReader`, `FileReader`       | `BufferedWriter`, `FileWriter`       | For plain text                 |
| `.csv`    | `BufferedReader` + `split(",")`      | `BufferedWriter`                     | Parse rows and columns         |
| `.json`   | `Gson`, `Jackson`, `org.json`        | `Gson`, `Jackson`, `org.json`        | Requires external libraries    |