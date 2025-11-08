# 🌐 Browser Navigation 
Browser navigation is a fundamental aspect of web automation using Selenium WebDriver. It allows you to control the browser's history and load different web pages programmatically.
## 🚀 Key Navigation Methods
### 1. get(String url)
Purpose: Opens a web page.
Behavior: Waits until the page is fully loaded.

Example:
```java
WebDriver driver = new ChromeDriver();
driver.get("https://www.example.com");
```
### 2. navigate().to(String url)
Purpose: Similar to get(), but part of the navigate() interface.
Behavior: Allows chaining with other navigation methods.

Example:
```java
driver.navigate().to("https://www.google.com");
```
### 3. navigate().back()
Purpose: Simulates clicking the browser's back button.

Example:
```java
driver.navigate().back();
```
### 4. navigate().forward()
Purpose: Simulates clicking the browser's forward button.

Example:
```java
driver.navigate().forward();
```
### 5. navigate().refresh()
Purpose: Reloads the current page.

Example:
```java
driver.navigate().refresh();
```
## 🧪 Full Example: Java 17 + Selenium 4.X
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class BrowserNavigationDemo {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();

        // Open first page
        driver.get("https://www.example.com");

        // Navigate to another page
        driver.navigate().to("https://www.google.com");

        // Go back to previous page
        driver.navigate().back();

        // Go forward to Google again
        driver.navigate().forward();

        // Refresh the current page
        driver.navigate().refresh();

        // Close the browser
        driver.quit();
    }
}
```
## 🧠 Key Differences: get() vs navigate().to()
| Feature                     | `get()`     | `navigate().to()` |
|----------------------------|-------------|-------------------|
| Waits for page load        | ✅ Yes      | ✅ Yes            |
| Part of Navigation interface | ❌ No      | ✅ Yes            |
| Supports chaining          | ❌ No        | ✅ Yes            |
## ⚠️ Common Challenges
| Issue                          | Solution                                         |
|--------------------------------|--------------------------------------------------|
| Page not loading               | Use `WebDriverWait` for dynamic content          |
| Navigation too fast            | Add `Thread.sleep()` or wait between steps       |
| Stale elements after navigation| Re-locate elements after page change             |