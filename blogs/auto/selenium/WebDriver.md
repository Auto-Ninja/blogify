# 🧭Selenium WebDriver

## 🧭 What Is Selenium WebDriver?
Selenium WebDriver is a browser automation API that lets you write scripts in Java (or other supported languages) to control browsers like Chrome, Firefox, Edge, and Safari. It interacts directly with the browser using native automation protocols, ensuring fast and reliable execution.

### 🚀 Key Features in Selenium 4.x
| Feature                   | Description                                                                 |
|---------------------------|------------------------------------------------------------------------------|
| W3C WebDriver Standard    | Ensures consistent behavior across browsers using a unified protocol.       |
| Relative Locators         | Locate elements based on their position relative to other elements.         |
| Improved Selenium Grid    | Supports Docker, live node monitoring, and better scalability.              |
| DevTools Protocol Support | Enables access to browser internals like network logs and performance data. |
| Window and Tab Management | Easily switch between tabs and windows.                                     |
| Enhanced Waits            | FluentWait and WebDriverWait for dynamic content handling.                  |
| Screenshot Capabilities   | Capture full-page or element-level screenshots.                             |
| Better Exception Handling | More descriptive error messages and stack traces.                           |


### 💻 Java Example Using Selenium 4.x
```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.locators.RelativeLocator;
import org.openqa.selenium.OutputType;
import org.apache.commons.io.FileUtils;
import java.io.File;

public class Selenium4Example {
    public static void main(String[] args) throws Exception {
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();

        driver.get("https://example.com");

        WebElement heading = driver.findElement(By.tagName("h2"));
        WebElement inputBelow = driver.findElement(RelativeLocator.with(By.tagName("input")).below(heading));
        inputBelow.sendKeys("Selenium 4 Rocks!");

        File screenshot = inputBelow.getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(screenshot, new File("input_screenshot.png"));

        driver.quit();
    }
}
```
### ✅ Demonstrates:
- Relative locators
- Element-level screenshot
- W3C-compliant WebDriver

## 🧩 Understanding System.setProperty("webdriver.chrome.driver", "...")
This line sets a JVM system property to tell Selenium where to find the ChromeDriver executable:

```java
System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
```
- Required before initializing ChromeDriver
- Without it, Selenium throws: “The path to the driver executable must be set…”
- Must match the installed Chrome version

## 🖥️ How to Check ChromeDriver Version on Windows 11

### Locate ChromeDriver:
- Manually downloaded: Check C:\Program Files, Downloads, or custom folders
- Installed via Chocolatey: Run where chromedriver in Command Prompt
### Check Version:
```bash
chromedriver --version
```
Example output:
```Code
ChromeDriver 117.0.5938.92
```
### Match with Chrome Browser:
 - Open Chrome → chrome://version
 - Ensure major versions match (e.g., Chrome 117 → ChromeDriver 117)

## 🔒 Restricting to a Specific Version
###  Manual Control:
- Download and store a specific version from the ChromeDriver site

### WebDriverManager (Java):
```java
WebDriverManager.chromedriver().driverVersion("117.0.5938.92").setup();
```
- Automatically downloads and sets the correct version
- Prevents mismatches and manual updates

## 📦 Does ChromeDriver Download Every Time?
- Manual setup: No, uses local binary unless path changes
- WebDriverManager: Downloads once and caches unless:
- - Version changes
- - Cache is cleared
- - You force an update

## 🧠 Interview Insights: Hidden Details
- System.setProperty is Java-specific; other languages use different mechanisms
- ChromeDriver must be executable and match OS architecture (32-bit vs 64-bit)
- Use ChromeOptions to set capabilities like headless mode or incognito

## 🧪 WebDriver vs WebElement

### 🔹 WebDriver
Controls the browser.

```java
driver.get("https://example.com");
driver.navigate().back();
driver.manage().window().maximize();
driver.quit();
```
### 🔹 WebElement
Represents a DOM element.

```java
WebElement loginButton = driver.findElement(By.id("login"));
loginButton.click();
loginButton.sendKeys("text");
loginButton.getText();
loginButton.getAttribute("value");
loginButton.isDisplayed();
loginButton.isEnabled();
loginButton.isSelected();
```
### 🔸 Combined Example
```java
WebDriver driver = new ChromeDriver();
driver.get("https://example.com");

WebElement searchBox = driver.findElement(By.name("q"));
searchBox.sendKeys("Selenium 4");
searchBox.submit();

driver.quit();
```

## 🧱 WebDriver Architecture

Selenium WebDriver follows a client-server architecture:
- Client: Your test script written in Java, Python, etc.
- WebDriver API: Sends commands from your script to the browser.
- Browser Driver: A bridge between Selenium and the browser (e.g., ChromeDriver for Chrome).
- Browser: Executes the commands (like clicking buttons or entering text).

### How It Works:
- You write a test script.
- Selenium sends commands to the browser driver.
- The driver translates them into browser-native actions.
- The browser performs those actions and sends results back.

## 🚦 Starting and Stopping a Session
### Start: Create a WebDriver object:

```java
WebDriver driver = new ChromeDriver();
```
This opens a new browser window and starts a session.

### Stop: Close the browser and end the session:
```java
driver.quit();
```
## 🌐 Loading Different Browsers
Selenium supports multiple browsers. You need the correct driver for each:
- Chrome → ChromeDriver
- Firefox → GeckoDriver
- Edge → EdgeDriver
- Safari → Built-in support on macOS

Example:
```java
WebDriver chrome = new ChromeDriver();
WebDriver firefox = new FirefoxDriver();
WebDriver edge = new EdgeDriver();
```

## 🍪 What Are Cookies?
Cookies are small pieces of data stored by the browser to remember:
- Login sessions
- User preferences
- Shopping cart contents

### 🔧 Handling Cookies in Selenium
```java
driver.manage().getCookies(); // Get all cookies
driver.manage().addCookie(new Cookie("user", "John"));
driver.manage().deleteCookieNamed("user");
```
✅ Use cookies to:
- Simulate logged-in users
- Test personalization
- Maintain session state

## 🎛️ Browser Options
``` java
ChromeOptions options = new ChromeOptions();
options.addArguments("--headless", "--incognito");
WebDriver driver = new ChromeDriver(options);
``` 
Common options:
- --headless: Run without UI
- --incognito: Private mode
- --disable-extensions: Disable plugins

## 📄 What Is Page Load?
Page load refers to the process of a browser retrieving and rendering a web page. This includes:
- Downloading HTML, CSS, JavaScript
- Rendering the DOM (Document Object Model)
- Executing scripts
- Loading images, fonts, and other resources

In Selenium, page load matters because your script needs to interact with elements after they’re available. If Selenium tries to click a button before the page finishes loading, it may throw an error like ElementNotInteractableException.

## 🎛️ Why Are There Different pageLoadStrategy Options?
Selenium 4 introduced the pageLoadStrategy setting to give developers control over how long Selenium waits for a page to load. This is useful for optimizing test speed and reliability.

### Available Strategies:
| Strategy | Behavior                                                   |
|----------|------------------------------------------------------------|
| normal   | Waits for the entire page to load (default)               |
| eager    | Waits only for the DOMContentLoaded event                 |
| none     | Doesn’t wait at all — proceeds immediately                |


### ✅ When to Use Each Strategy
| Strategy | Use Case                                                                                   |
|----------|---------------------------------------------------------------------------------------------|
| normal   | Full page validation, visual testing, or when interacting with late-loading elements       |
| eager    | Form submissions, DOM-based interactions, faster test cycles                               |
| none     | Advanced users managing load manually, API-heavy apps, or when using custom waits          |


### 🧪 How to Set It in Code
```java
ChromeOptions options = new ChromeOptions();
options.setPageLoadStrategy(PageLoadStrategy.EAGER);
WebDriver driver = new ChromeDriver(options);
```
## 🕵️ What Is a Proxy?
A proxy routes traffic through an intermediary server.

```java
Proxy proxy = new Proxy();
proxy.setHttpProxy("myproxy:8080");
options.setProxy(proxy);
```
✅ Use cases:
- Simulate different locations
- Bypass firewalls
- Monitor traffic

### 🏢 Why Organizations Use Proxies
- Security: Filter malicious content
- Monitoring: Track usage and logs
- Access Control: Restrict external sites
- Compliance: Enforce data policies

### Using Proxy in Selenium
```java
import org.openqa.selenium.Proxy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class ProxyExample {
    public static void main(String[] args) {
        // Set up proxy configuration
        Proxy proxy = new Proxy();
        proxy.setHttpProxy("myproxy.example.com:8080");
        proxy.setSslProxy("myproxy.example.com:8080");

        // Apply proxy to ChromeOptions
        ChromeOptions options = new ChromeOptions();
        options.setProxy(proxy);

        // Initialize WebDriver with proxy
        WebDriver driver = new ChromeDriver(options);

        // Navigate to a site
        driver.get("https://example.com");

        // Close browser
        driver.quit();
    }
}
```
#### 🔐 Notes:
- Replace "myproxy.example.com:8080" with your organization's proxy address.
- You can also configure authentication if required using third-party tools or browser profiles.