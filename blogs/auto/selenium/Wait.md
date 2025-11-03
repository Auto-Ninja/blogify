# Wait strategies
Wait strategies in Selenium are essential for handling dynamic web elements and avoiding flaky tests. Each type—Implicit, Explicit, Fluent, and Custom—serves a specific purpose depending on the scenario.

### 🕰️ 1. Implicit Wait
#### ✅ What It Is:
Sets a default wait time for the WebDriver to search for elements before throwing NoSuchElementException.
####  📌 When to Use:
- For simple applications with consistent load times.
- When most elements appear within a predictable timeframe.
#### 🧪 Example:
```java
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
```
#### ⚠️ Challenges:
- Applies globally to all elements.
- Can slow down tests unnecessarily.
- Doesn’t wait for conditions like visibility or clickability.

### ⏳ 2. Explicit Wait (WebDriverWait)
#### ✅ What It Is:
Waits for a specific condition to be true before proceeding (e.g., element is visible or clickable).

#### 📌 When to Use:
    - For dynamic elements that load asynchronously.
    - When you need to wait for specific conditions.
#### 🧪 Example:
``` java
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(15));
WebElement element = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("submit")));
element.click();
```
#### ⚠️ Challenges:
    - Must be written for each element.
    - Can clutter code if overused.

### 🔁 3. Fluent Wait
#### ✅ What It Is:
An advanced form of Explicit Wait that allows polling frequency and exception handling.
#### 📌 When to Use:
    - For highly dynamic content.
    - When you want to ignore specific exceptions (e.g., NoSuchElementException).
#### 🧪 Example:
```java
Wait<WebDriver> fluentWait = new FluentWait<>(driver)
    .withTimeout(Duration.ofSeconds(20))
    .pollingEvery(Duration.ofSeconds(2))
    .ignoring(NoSuchElementException.class);
WebElement element = fluentWait.until(driver -> driver.findElement(By.id("dynamic")));
```
#### ⚠️ Challenges:
    - Slightly more complex syntax.
    - Requires careful tuning of polling intervals.

### 🧠 4. Custom Wait Conditions
#### ✅ What It Is:
User-defined conditions using lambdas or custom logic.
#### 📌 When to Use:
    - When built-in ExpectedConditions don’t cover your scenario.
    - For waiting on non-element conditions (e.g., page title, URL change, API response).
#### 🧪 Example:
```java
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
wait.until(driver -> driver.getTitle().contains("Dashboard"));
```
Or for a custom condition:
```java
wait.until(driver -> {
    WebElement el = driver.findElement(By.id("status"));
    return el.getText().equals("Ready");
});
```
### 🧩 Choosing the Right Wait Strategy
| Scenario              | Recommended Wait     |
|-----------------------|----------------------|
| Static content        | Implicit Wait        |
| Dynamic elements      | Explicit Wait        |
| Highly volatile UI    | Fluent Wait          |
| Custom logic needed   | Custom Wait          |

### 🚧 Common Challenges & Solutions
| Challenge                      | Solution                                               |
|--------------------------------|--------------------------------------------------------|
| Flaky tests                    | Use Explicit or Fluent Waits with proper conditions    |
| StaleElementReferenceException| Re-locate element after wait                           |
| Slow tests                     | Avoid long Implicit Waits; prefer targeted Explicit Waits |
| Complex conditions             | Use Custom Waits with lambdas                          |

For deeper control and cleaner code, consider wrapping wait logic in utility methods

### 🧠 Why Wrap Waits in Utility Methods?
    - ✅ Avoid repetition: No need to write WebDriverWait logic every time.
    - ✅ Centralized control: Change wait durations or conditions in one place.
    - ✅ Improved readability: Test scripts focus on business logic, not wait mechanics.
    - ✅ Easier debugging: Add logging or exception handling in one place.

#### 🧪 Example: Wait Utility Class in Java 17 + Selenium 4.X
```java
import org.openqa.selenium.*;
import org.openqa.selenium.support.ui.*;
import java.time.Duration;

public class WaitUtils {

    private WebDriver driver;

    public WaitUtils(WebDriver driver) {
        this.driver = driver;
    }

    // Wait for element to be visible
    public WebElement waitForVisibility(By locator, int timeoutSeconds) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
        return wait.until(ExpectedConditions.visibilityOfElementLocated(locator));
    }

    // Wait for element to be clickable
    public WebElement waitForClickability(By locator, int timeoutSeconds) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
        return wait.until(ExpectedConditions.elementToBeClickable(locator));
    }

    // Wait for text to appear in element
    public boolean waitForText(By locator, String expectedText, int timeoutSeconds) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
        return wait.until(ExpectedConditions.textToBe(locator, expectedText));
    }

    // Wait for URL to contain a keyword
    public boolean waitForUrlContains(String keyword, int timeoutSeconds) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
        return wait.until(ExpectedConditions.urlContains(keyword));
    }

    // Custom Fluent Wait for dynamic elements
    public WebElement fluentWait(By locator, int timeoutSeconds, int pollingSeconds) {
        Wait<WebDriver> fluentWait = new FluentWait<>(driver)
            .withTimeout(Duration.ofSeconds(timeoutSeconds))
            .pollingEvery(Duration.ofSeconds(pollingSeconds))
            .ignoring(NoSuchElementException.class);

        return fluentWait.until(driver -> driver.findElement(locator));
    }
}
```
### 🧪 How to Use in Your Test Class
```java
WebDriver driver = new ChromeDriver();
WaitUtils waitUtils = new WaitUtils(driver);

driver.get("https://example.com");

// Wait for login button to be clickable
WebElement loginBtn = waitUtils.waitForClickability(By.id("login"), 10);
loginBtn.click();

// Wait for welcome message
waitUtils.waitForText(By.id("welcome"), "Hello, Admin!", 5);
```
### 🧩 Bonus: Add Logging or Screenshot on Timeout
You can enhance WaitUtils with:
    - Logging failed waits
    - Taking screenshots on timeout
    - Throwing custom exceptions

### 🧰 Updated WaitUtils Class with Logging & Screenshot
```java
import org.openqa.selenium.*;
import org.openqa.selenium.support.ui.*;
import java.io.File;
import java.io.IOException;
import java.nio.file.*;
import java.time.Duration;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class WaitUtils {

    private WebDriver driver;

    public WaitUtils(WebDriver driver) {
        this.driver = driver;
    }

    // Utility: Take screenshot
    private void takeScreenshot(String reason) {
        try {
            File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
            String timestamp = LocalDateTime.now().format(DateTimeFormatter.ofPattern("yyyyMMdd_HHmmss"));
            String filename = "screenshot_" + reason + "_" + timestamp + ".png";
            Path dest = Paths.get(System.getProperty("user.dir"), "screenshots", filename);
            Files.createDirectories(dest.getParent());
            Files.copy(src.toPath(), dest, StandardCopyOption.REPLACE_EXISTING);
            System.out.println("📸 Screenshot saved: " + dest);
        } catch (IOException e) {
            System.err.println("❌ Failed to save screenshot: " + e.getMessage());
        }
    }

    // Wait for element to be visible with logging and screenshot
    public WebElement waitForVisibility(By locator, int timeoutSeconds) {
        try {
            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
            return wait.until(ExpectedConditions.visibilityOfElementLocated(locator));
        } catch (TimeoutException e) {
            System.err.println("⚠️ Timeout waiting for visibility of: " + locator);
            takeScreenshot("visibility_timeout");
            throw e;
        }
    }

    // Wait for element to be clickable with logging and screenshot
    public WebElement waitForClickability(By locator, int timeoutSeconds) {
        try {
            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
            return wait.until(ExpectedConditions.elementToBeClickable(locator));
        } catch (TimeoutException e) {
            System.err.println("⚠️ Timeout waiting for clickability of: " + locator);
            takeScreenshot("clickable_timeout");
            throw e;
        }
    }

    // Wait for text to appear with logging and screenshot
    public boolean waitForText(By locator, String expectedText, int timeoutSeconds) {
        try {
            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(timeoutSeconds));
            return wait.until(ExpectedConditions.textToBe(locator, expectedText));
        } catch (TimeoutException e) {
            System.err.println("⚠️ Timeout waiting for text '" + expectedText + "' in: " + locator);
            takeScreenshot("text_timeout");
            return false;
        }
    }
}
```
### 🧪 How to Use in Your Tests
```java
WebDriver driver = new ChromeDriver();
WaitUtils waitUtils = new WaitUtils(driver);

driver.get("https://example.com");

try {
    WebElement loginBtn = waitUtils.waitForClickability(By.id("login"), 10);
    loginBtn.click();
} catch (TimeoutException e) {
    System.out.println("Login button not clickable. Check screenshot for details.");
}
```
### 📦 Screenshot Folder Structure
    - Screenshots are saved in a screenshots/ folder inside your project directory.
    - Filenames include the reason and timestamp for easy tracking.