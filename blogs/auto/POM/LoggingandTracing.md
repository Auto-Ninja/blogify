# Logging and Tracing 
Logging and tracing in TestNG, Selenium, and POM frameworks help track test execution, debug failures, and generate detailed reports for analysis. You can implement this using tools like Log4j, SLF4J, or built-in Java logging.

## 🧭 Why Logging and Tracing Matter
- Debugging: Identify where and why a test failed.
- Audit Trail: Record what actions were performed and in what order.
- Reporting: Enhance test reports with detailed logs.
- Maintenance: Easier to troubleshoot flaky or failing tests.

## 🛠️ Logging in a POM Framework
### 🔹 Step 1: Add Log4j2 to Your Project
If using Maven, add this to your pom.xml:

```xml
<dependency>
  <groupId>org.apache.logging.log4j</groupId>
  <artifactId>log4j-core</artifactId>
  <version>2.20.0</version>
</dependency>
<dependency>
  <groupId>org.apache.logging.log4j</groupId>
  <artifactId>log4j-api</artifactId>
  <version>2.20.0</version>
</dependency>
```
### 🔹 Step 2: Create log4j2.xml Configuration
```xml
<Configuration status="WARN">
  <Appenders>
    <Console name="Console" target="SYSTEM_OUT">
      <PatternLayout pattern="%d{HH:mm:ss} [%t] %-5level %logger{36} - %msg%n"/>
    </Console>
    <File name="FileLogger" fileName="logs/test.log">
      <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n"/>
    </File>
  </Appenders>
  <Loggers>
    <Root level="info">
      <AppenderRef ref="Console"/>
      <AppenderRef ref="FileLogger"/>
    </Root>
  </Loggers>
</Configuration>
```
### 🔹 Step 3: Use Logger in Page and Test Classes
```java
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class LoginPage {
    private static final Logger logger = LogManager.getLogger(LoginPage.class);

    public void login(String user, String pass) {
        logger.info("Attempting to log in with user: " + user);
        usernameField.sendKeys(user);
        passwordField.sendKeys(pass);
        loginButton.click();
        logger.info("Login button clicked");
    }
}
```

## 🧩 What is a TestListener?
A TestListener implements the ITestListener interface from TestNG. It provides callback methods that are triggered during different stages of test execution.

### 🔧 Key Methods in ITestListener
| Method           | Trigger                                 |
|------------------|------------------------------------------|
| onTestStart()    | Before a test method starts              |
| onTestSuccess()  | When a test method passes                |
| onTestFailure()  | When a test method fails                 |
| onTestSkipped()  | When a test method is skipped            |
| onStart()        | Before any test starts in the suite      |
| onFinish()       | After all tests finish in the suite      |

## 🔍 Tracing in TestNG
### 🔸 Use ITestListener for Execution Tracing

```java
import org.testng.ITestListener;
import org.testng.ITestResult;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class TestListener implements ITestListener {
    private static final Logger logger = LogManager.getLogger(TestListener.class);

    @Override
    public void onTestStart(ITestResult result) {
        logger.info("Test Started: " + result.getName());
    }

    @Override
    public void onTestSuccess(ITestResult result) {
        logger.info("Test Passed: " + result.getName());
    }

    @Override
    public void onTestFailure(ITestResult result) {
        logger.error("Test Failed: " + result.getName());
        ScreenshotUtil.captureScreenshot(result.getName());
    }

    @Override
    public void onTestSkipped(ITestResult result) {
        logger.warn("Test Skipped: " + result.getName());
    }

    @Override
    public void onStart(ITestResult result) {
        logger.info("Test Suite Started");
    }

    @Override
    public void onFinish(ITestResult result) {
        logger.info("Test Suite Finished");
    }
}
```
## 📦 How to Register the Listener
### Option 1: In testng.xml
```xml
<listeners>
  <listener class-name="com.example.listeners.TestListener"/>
</listeners>
```
### Option 2: Using @Listeners Annotation
```java
@Listeners(com.example.listeners.TestListener.class)
public class LoginTest {
    // your test methods
}
```

### 📸 Capture Test Failure with Screenshot
#### 🔹 Screenshot Utility
```java
public class ScreenshotUtil {
    public static void captureScreenshot(String testName) {
        File src = ((TakesScreenshot) Base.driver).getScreenshotAs(OutputType.FILE);
        try {
            FileUtils.copyFile(src, new File("screenshots/" + testName + ".png"));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
Call this in onTestFailure() of your listener.


## 🔁 Retry Failed Test Cases
### 🔹 Custom Retry Analyzer
Implement IRetryAnalyzer:

```java
public class RetryAnalyzer implements IRetryAnalyzer {
    private int retryCount = 0;
    private static final int maxRetryCount = 2;

    public boolean retry(ITestResult result) {
        if (retryCount < maxRetryCount) {
            retryCount++;
            return true;
        }
        return false;
    }
}
```
Apply to test method:

```java
@Test(retryAnalyzer = RetryAnalyzer.class)
public void testLogin() {
    // test logic
}
```
## 🧠 Why Use Custom Retry?
- Handle flaky tests due to network or timing issues.
- Improve test stability in CI/CD pipelines.
- Avoid false negatives in reports.


## Complete Java implementation
Here’s a complete Java implementation of a Selenium + TestNG + POM framework that includes:
  ✅ Page Object Model
  ✅ Logging with Log4j2
  ✅ Screenshot capture on failure
  ✅ TestNG Listener
  ✅ Retry Analyzer

### 🧰 Project Structure
```code
src/
├── base/
│   └── BaseTest.java
├── pages/
│   └── LoginPage.java
├── tests/
│   └── LoginTest.java
├── utils/
│   ├── ScreenshotUtil.java
│   └── RetryAnalyzer.java
├── listeners/
│   └── TestListener.java
└── resources/
    └── log4j2.xml
```

### 🔹 BaseTest.java
```java
package base;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;

public class BaseTest {
    protected WebDriver driver;

    @BeforeMethod
    public void setup() {
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://example.com/login");
    }

    @AfterMethod
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}
```

### 🔹 LoginPage.java
```java
package pages;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class LoginPage {
    private WebDriver driver;
    private static final Logger logger = LogManager.getLogger(LoginPage.class);

    @FindBy(id = "username")
    private WebElement usernameField;

    @FindBy(id = "password")
    private WebElement passwordField;

    @FindBy(id = "loginBtn")
    private WebElement loginButton;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    public void login(String username, String password) {
        try {
            logger.info("Entering username");
            usernameField.sendKeys(username);
            logger.info("Entering password");
            passwordField.sendKeys(password);
            logger.info("Clicking login button");
            loginButton.click();
        } catch (Exception e) {
            logger.error("Login failed", e);
            throw e;
        }
    }
}
```
### 🔹 LoginTest.java
```java 
package tests;

import base.BaseTest;
import org.testng.annotations.Listeners;
import org.testng.annotations.Test;
import pages.LoginPage;
import utils.RetryAnalyzer;

@Listeners(listeners.TestListener.class)
public class LoginTest extends BaseTest {

    @Test(retryAnalyzer = RetryAnalyzer.class)
    public void testLogin() {
        LoginPage loginPage = new LoginPage(driver);
        loginPage.login("admin", "admin123");
        // Add assertions here
    }
}
```
### 🔹 ScreenshotUtil.java
```java
package utils;

import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.apache.commons.io.FileUtils;
import java.io.File;
import java.io.IOException;

public class ScreenshotUtil {
    public static void captureScreenshot(WebDriver driver, String testName) {
        File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
        try {
            FileUtils.copyFile(src, new File("screenshots/" + testName + ".png"));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
### 🔹 RetryAnalyzer.java
```java
package utils;

import org.testng.IRetryAnalyzer;
import org.testng.ITestResult;

public class RetryAnalyzer implements IRetryAnalyzer {
    private int retryCount = 0;
    private static final int maxRetryCount = 2;

    public boolean retry(ITestResult result) {
        if (retryCount < maxRetryCount) {
            retryCount++;
            return true;
        }
        return false;
    }
}
``` 
### 🔹 TestListener.java
```java 
package listeners;

import org.testng.ITestListener;
import org.testng.ITestResult;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import utils.ScreenshotUtil;
import base.BaseTest;

public class TestListener implements ITestListener {
    private static final Logger logger = LogManager.getLogger(TestListener.class);

    public void onTestFailure(ITestResult result) {
        logger.error("Test Failed: " + result.getName());
        Object currentClass = result.getInstance();
        WebDriver driver = ((BaseTest) currentClass).driver;
        ScreenshotUtil.captureScreenshot(driver, result.getName());
    }

    public void onTestStart(ITestResult result) {
        logger.info("Test Started: " + result.getName());
    }

    public void onTestSuccess(ITestResult result) {
        logger.info("Test Passed: " + result.getName());
    }

    public void onTestSkipped(ITestResult result) {
        logger.warn("Test Skipped: " + result.getName());
    }
}
```
### 🔹log4j2.xml (in resources/)
```xml
<Configuration status="WARN">
  <Appenders>
    <Console name="Console" target="SYSTEM_OUT">
      <PatternLayout pattern="%d{HH:mm:ss} %-5level %logger{36} - %msg%n"/>
    </Console>
    <File name="FileLogger" fileName="logs/test.log">
      <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n"/>
    </File>
  </Appenders>
  <Loggers>
    <Root level="info">
      <AppenderRef ref="Console"/>
      <AppenderRef ref="FileLogger"/>
    </Root>
  </Loggers>
</Configuration>
```

## ✅ Summary
| Feature               | Purpose                                         |
|------------------------|-------------------------------------------------|
| Logging                | Track actions and debug failures                |
| TestListener           | Hook into test lifecycle for logging and screenshots |
| Screenshot on Failure  | Visual evidence for debugging                   |
| Retry Analyzer         | Rerun flaky tests automatically                 |
