# 🧱 Page Object Model (POM) in Selenium
## 🔍 What is POM?
Page Object Model (POM) is a design pattern in Selenium that enhances test maintenance and reduces code duplication. It models each web page in your application as a separate Java class, encapsulating the page’s elements and behaviors.

## 🧠 Why Use POM?
- Maintainability: Changes in UI require updates only in the page class, not in every test.
- Reusability: Common actions (e.g., login, search) can be reused across multiple tests.
- Readability: Tests become cleaner and more readable, focusing on logic rather than UI details.
- Scalability: Supports large test suites with modular structure.

## 📅 When to Use POM?
##### Use POM when:
 - Your application has multiple pages or complex workflows.
 - You want to separate test logic from UI structure.
 - You aim to build a scalable and maintainable automation framework.

## 🧰 Structure of POM in Java + Selenium
##### 🔸 Page Class
```java
public class LoginPage {
    private WebDriver driver;

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

    public void login(String user, String pass) {
        usernameField.sendKeys(user);
        passwordField.sendKeys(pass);
        loginButton.click();
    }
}
```
## 🔸 Test Class (Using TestNG)
```java
public class LoginTest {
    WebDriver driver;

    @BeforeMethod
    public void setup() {
        driver = new ChromeDriver();
        driver.get("https://example.com/login");
    }

    @Test
    public void testLogin() {
        LoginPage loginPage = new LoginPage(driver);
        loginPage.login("admin", "admin123");
        // Add assertions here
    }

    @AfterMethod
    public void tearDown() {
        driver.quit();
    }
}
```
## 🧪 Test Suite Tool for POM: TestNG
#### 🧭 Why TestNG?
- Supports annotations like @Test, @BeforeMethod, @AfterMethod, etc.
- Allows grouping, prioritization, and parallel execution.
- Easily integrates with build tools like Maven and CI/CD pipelines.

## 📦 How to Execute POM Tests with TestNG?
#### 1. Create testng.xml
```xml
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name="AutomationSuite">
    <test name="LoginTests">
        <classes>
            <class name="com.example.tests.LoginTest"/>
        </classes>
    </test>
</suite>
```
#### 2. Run via IDE
Right-click on testng.xml → Run as → TestNG Suite

#### 3. Run via Maven
Add this to your pom.xml:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.0.0</version>
            <configuration>
                <suiteXmlFiles>
                    <suiteXmlFile>testng.xml</suiteXmlFile>
                </suiteXmlFiles>
            </configuration>
        </plugin>
    </plugins>
</build>
```
Then run:

```bash
mvn test
```
#### ✅ POM Summary
| Concept        | Description                                      |
|----------------|--------------------------------------------------|
| POM            | Design pattern to model web pages as classes     |
| Benefits       | Maintainability, reusability, readability        |
| Tool for Suite | TestNG                                           |
| Execution      | Via testng.xml in IDE or Maven                   |

## 🧭 Real-World Scenario: E-Commerce Login and Checkout
Imagine automating an e-commerce site like Amazon.You want to test:
  1. Logging in
  2. Searching for a product
  3. Adding it to the cart
  4. Checking out

#### 🔧 Without POM:
- You write all locators and actions in the test class.
- If the login page changes, you update every test that uses it.

#### 🧱 With POM:
- You create LoginPage.java, SearchPage.java, CartPage.java, and CheckoutPage.java.
- Each class handles its own locators and actions.
- Tests simply call methods like loginPage.login(), searchPage.search("Laptop").

### 🔄 Sequence Diagram of POM Execution
Here’s a simplified flow:

```Code
[TestNG Test Class]
       |
       v
[Initialize WebDriver]
       |
       v
[Create Page Object: LoginPage]
       |
       v
[Call loginPage.login()]
       |
       v
[LoginPage interacts with UI elements]
       |
       v
[Create Page Object: SearchPage]
       |
       v
[Call searchPage.search("Laptop")]
       |
       v
[SearchPage interacts with UI elements]
       |
       v
... (continues for CartPage, CheckoutPage)
```

#### 📁 Folder Structure
```Code
src/
├── pages/
│   ├── LoginPage.java
│   ├── SearchPage.java
│   ├── CartPage.java
│   └── CheckoutPage.java
├── tests/
│   └── ECommerceTest.java
└── testng.xml
```
#### 🧪 TestNG Integration
testng.xml
```xml
<suite name="ECommerceSuite">
  <test name="CheckoutFlow">
    <classes>
      <class name="tests.ECommerceTest"/>
    </classes>
  </test>
</suite>
```
#### Execution
- In IDE: Right-click testng.xml → Run as TestNG Suite
- In Maven: mvn test

## ✅ Benefits Recap
| Feature              | Benefit                                         |
|----------------------|--------------------------------------------------|
| Separation of concerns | UI logic isolated from test logic              |
| Reusability           | Page methods reused across tests                |
| Maintainability       | UI changes require updates only in page classes |
| Scalability           | Easy to add new pages and tests                 |