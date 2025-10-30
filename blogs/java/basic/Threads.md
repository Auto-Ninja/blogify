## 🧠 What Are Threads in Java?
A thread is the smallest unit of execution in a Java program. It’s like a mini-program running inside your application. Java supports multithreading, which means multiple threads can run concurrently.

### 🔧 Why Use Threads?
- Parallelism: Run multiple tasks at the same time.
- Responsiveness: Keeps applications (like GUIs) responsive.
- Efficiency: Utilizes CPU cores better.
- Background Tasks: Handle tasks like file downloads, animations, or data processing without blocking the main program.

### ✅ Advantages of Threads
- Faster execution: Tasks run in parallel.
- Better resource use: Threads share memory space.
- Improved user experience: UI stays responsive.

### ❌ Disadvantages of Threads
- Complexity: Harder to debug and maintain.
- Synchronization issues: Risk of race conditions and deadlocks.
- Overhead: Too many threads can slow down performance.

### 🧩 Thread Features
| **Feature**         | **Description**                                      |
|---------------------|------------------------------------------------------|
| **Concurrency**     | Multiple threads run simultaneously                  |
| **Shared memory**   | Threads share data and resources                     |
| **Lightweight**     | Less overhead than full processes                    |
| **Lifecycle control** | Start, pause, resume, stop threads                  |
### 🛠️ Thread Methods
| **Method**     | **Purpose**                                 |
|----------------|---------------------------------------------|
| `start()`      | Begins thread execution                     |
| `run()`        | Contains the code to execute                |
| `sleep(ms)`    | Pauses thread for milliseconds              |
| `join()`       | Waits for another thread to finish          |
| `isAlive()`    | Checks if thread is still running           |
### 👶 Beginner-Friendly Example
#### 🔹 Using Thread Class
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // starts a new thread
    }
}
```
### 🔹 Using Runnable Interface
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread is running...");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();
    }
}
```
### 🛒 Real-World Use Case: E-Commerce
```plaintext
[Main Thread] → Handles user interface
 ├── [Thread 1] → Loads product images
 ├── [Thread 2] → Fetches recommendations
 └── [Thread 3] → Processes payment
```
Threads allow the app to:
- Load data in the background
- Keep UI responsive
- Process orders without delay

#### ✅ How to Use Threads
- Extend Thread class or implement Runnable
- Override run() method
- Create thread object
- Call start() to begin execution