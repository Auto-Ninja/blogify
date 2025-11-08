
# TestNG is Test Next Generation.
It’s a testing framework inspired by JUnit and NUnit, designed to simplify a broad range of testing needs, from unit testing to integration and end-to-end testing. Let me know if you'd like a quick comparison between TestNG and JUnit.
## 🧪 What Is TestNG?
TestNG stands for Test Next Generation. It’s inspired by JUnit but offers more flexibility and control over test execution. It uses annotations to define test behavior and lifecycle.

## 🧩 Core TestNG Annotations and Their Usage
| Annotation       | Purpose                          | When It Runs                      |
|------------------|----------------------------------|-----------------------------------|
| `@BeforeSuite`   | Setup before entire suite        | Once before all tests             |
| `@AfterSuite`    | Cleanup after entire suite       | Once after all tests              |
| `@BeforeTest`    | Setup before `<test>` tag in XML | Before any test in that tag       |
| `@AfterTest`     | Cleanup after `<test>` tag       | After all tests in that tag       |
| `@BeforeClass`   | Setup before first method in class| Once per class                   |
| `@AfterClass`    | Cleanup after last method in class| Once per class                   |
| `@BeforeMethod`  | Setup before each test method    | Before every `@Test`              |
| `@AfterMethod`   | Cleanup after each test method   | After every `@Test`               |
| `@Test`          | Marks a test method              | Executes as a test                |
| `@Parameters`    | Injects parameters from XML      | Used with `@Test`                 |
| `@DataProvider`  | Supplies data to tests           | Used for data-driven testing      |
| `@Listeners`     | Hooks for logging/reporting      | Used for custom behavior          |

## 🧪 TestNG Lifecycle
```java
public class LoginTests {

    @BeforeSuite
    public void setupSuite() {
        System.out.println("🔧 Before Suite");
    }

    @BeforeClass
    public void setupClass() {
        System.out.println("🚀 Before Class");
    }

    @BeforeMethod
    public void setupMethod() {
        System.out.println("🔄 Before Method");
    }

    @Test
    public void testLoginValidUser() {
        System.out.println("✅ Test: Valid Login");
    }

    @Test
    public void testLoginInvalidUser() {
        System.out.println("❌ Test: Invalid Login");
    }

    @AfterMethod
    public void teardownMethod() {
        System.out.println("🔄 After Method");
    }

    @AfterClass
    public void teardownClass() {
        System.out.println("🧹 After Class");
    }

    @AfterSuite
    public void teardownSuite() {
        System.out.println("🧼 After Suite");
    }
}
```
## 📦 Advanced Features
### 1. Grouping Tests
```java
@Test(groups = {"smoke"})
public void testSearch() { ... }

@Test(groups = {"regression"})
public void testCheckout() { ... }
```
### 2. Data-Driven Testing
```java
@DataProvider(name = "loginData")
public Object[][] getData() {
    return new Object[][] {
        {"admin", "123"},
        {"user", "abc"}
    };
}

@Test(dataProvider = "loginData")
public void testLogin(String username, String password) {
    // use credentials
}
```
### 3. Parameterization via XML
```java
@Parameters({"browser"})
@Test
public void testLaunch(String browser) {
    System.out.println("Launching: " + browser);
}
```
### 4. Listeners for Logging & Reporting
```java
@Listeners(MyTestListener.class)
public class MyTests { ... }
```
## 🧠 Best Practices
- Use @BeforeMethod and @AfterMethod for test isolation.
- Use @DataProvider for scalable test coverage.
- Use @Listeners for custom logging, screenshots, and reporting.
- Organize tests with groups and XML suites for CI/CD.