# 🧩 Core Terminologies in Test Automation
## 🔹 Test Case
A set of conditions or steps to validate a specific feature or functionality.

## 🔹 Test Suite
A collection of test cases grouped for execution.

## 🔹 Test Script
Automated code that performs the steps defined in a test case.

## 🔹 Assertion
A statement that verifies expected vs. actual outcomes (e.g., assertEquals() in TestNG).

## 🔹 Test Runner
Tool or framework that executes test scripts (e.g., TestNG, JUnit).

## 🔹 Test Coverage
The percentage of code or functionality tested by automation.

## 🧪 Types of Testing
### 1. Unit Testing
Purpose: Validates individual components or functions.

Tools: JUnit (Java), NUnit (.NET), PyTest (Python)

When to Use: During development to catch bugs early.

### 2. Integration Testing
Purpose: Ensures modules or services work together.

Tools: TestNG, Postman (for APIs), REST Assured

When to Use: After unit testing, before system testing.

###  3. Functional Testing
Purpose: Verifies that software behaves according to requirements.

Tools: Selenium, Cypress, Playwright

When to Use: For UI and business logic validation.

### 4. Regression Testing
Purpose: Checks that new changes haven’t broken existing functionality.

Tools: Selenium Grid, TestNG with retry logic

When to Use: After bug fixes, enhancements, or releases.

### 5. Smoke Testing
Purpose: Quick check to ensure basic functionality works.

Tools: Any test framework with a small test suite

When to Use: Before deeper testing begins.

### 6. Sanity Testing
Purpose: Focused check on a specific module or bug fix.

Tools: Same as smoke testing, but more targeted

When to Use: After receiving a new build with minor changes.

### 7. Performance Testing
Purpose: Measures responsiveness, stability, and scalability.

Tools: JMeter, Gatling, Locust

When to Use: Before production deployment or under load conditions.

### 8. Load Testing
Purpose: Simulates high user traffic to test system limits.

Tools: Apache JMeter, BlazeMeter

When to Use: For web apps, APIs, and backend services.

### 9. Security Testing
Purpose: Identifies vulnerabilities and ensures data protection.

Tools: OWASP ZAP, Burp Suite

When to Use: Before public release or compliance audits.

### 10. End-to-End (E2E) Testing
Purpose: Validates complete workflows from start to finish.

Tools: Selenium, Cypress, Robot Framework

When to Use: For critical user journeys like login, checkout, etc.


## 🛠️ Automation Framework Concepts
### 🔹 Page Object Model (POM)
Design pattern that models each page as a class to improve maintainability.

### 🔹 Data-Driven Testing
Uses external data (Excel, JSON, CSV) to run tests with multiple inputs.

### 🔹 Keyword-Driven Testing
Uses keywords to define actions, separating logic from implementation.

### 🔹 Behavior-Driven Development (BDD)
Uses natural language (e.g., Gherkin) to define test scenarios (e.g., Cucumber).

## 🔄 Execution and Reporting
### 🔹 CI/CD
Continuous Integration and Continuous Deployment pipelines that automate testing and delivery.

## 🔹 Test Environment
The setup (hardware, OS, browser) where tests are executed.

## 🔹 Test Report
Summary of test results, often including logs, screenshots, and metrics.

## 🔹 Flaky Test
A test that passes or fails inconsistently due to timing or environment issues.

## 📦 Tools and Technologies
| Category         | Examples                                 |
|------------------|-------------------------------------------|
| Test Frameworks  | TestNG, JUnit, NUnit                      |
| Automation Tools | Selenium, Cypress, Playwright             |
| CI/CD Platforms  | Jenkins, GitHub Actions, Azure DevOps     |
| Reporting        | ExtentReports, Allure, ReportNG           |
| Version Control  | Git, GitHub, Bitbucket                    |
