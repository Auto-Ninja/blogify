# 🔍 Selenium Locators
## 🧱 What Are HTML Elements?
HTML elements are the building blocks of web pages. Each element represents a part of the page, such as:
```Html
Text: <p>, <h1>, <span>
Inputs: <input>, <textarea>, <select>
Buttons: <button>, <a>
Containers: <div>, <section>, <article>
Media: <img>, <video>, <audio>
```

Each element can have attributes like:

```html
<input type="text" id="username" name="user" class="form-control" />
```
These attributes (id, name, class) are what Selenium uses to locate and interact with elements.

## 🌐 What Is DOM Rendering?
DOM (Document Object Model) is the live representation of the HTML structure in the browser. When a page loads:

- 1 The browser parses the HTML.
- 2 It builds a DOM tree.
- 3 JavaScript and CSS can modify this tree dynamically.
- 4 Selenium interacts with this live DOM, not the raw HTML.

## 🔄 Dynamic DOM Rendering
Modern websites use JavaScript frameworks (React, Angular, Vue) to render elements dynamically:
- Elements may not exist at initial page load.
- They may appear after AJAX calls or user actions.
- Selenium must wait for these elements to be present.

## 🧭 Locator Strategy Recap (with DOM Context)

| Locator           | Best Use Case              | DOM Consideration             |
|-------------------|----------------------------|-------------------------------|
| `id`              | Unique and stable          | Fastest lookup                |
| `name`            | Forms and inputs           | Often used in legacy systems  |
| `className`       | Styling hooks              | May match multiple elements   |
| `tagName`         | Bulk operations            | Use with `findElements()`     |
| `linkText`        | Static links               | Avoid if text changes         |
| `partialLinkText` | Long or dynamic links      | Use with caution              |
| `xpath`           | Complex or dynamic DOM     | Supports traversal            |
| `cssSelector`     | Precise and fast           | Preferred for performance     |

### 1. ID Locator
Use when: Element has a unique id attribute.
Example:
```java
WebElement username = driver.findElement(By.id("user_login"));
username.sendKeys("admin");
```
### 2. Name Locator
Use when: name attribute is unique or consistent.
Example:
```java
WebElement email = driver.findElement(By.name("email"));
email.sendKeys("test@example.com");
```
### 3. ClassName Locator
Use when: Class is unique or used for styling single elements.
Caution: Avoid if multiple elements share the same class.
Example:
```java
WebElement button = driver.findElement(By.className("submit-btn"));
button.click();
```
### 4. TagName Locator
Use when: Targeting HTML tags like ```<input>, <a>, <img>```.
```java
List<WebElement> links = driver.findElements(By.tagName("a"));
for (WebElement link : links) {
    System.out.println(link.getText());
}
```
### 5. LinkText Locator
Use when: Link text is static and unique.
Example:
```java
driver.findElement(By.linkText("Forgot Password?")).click();
```
###  6. PartialLinkText Locator
Use when: Link text is long or dynamic.
Example:
```java
driver.findElement(By.partialLinkText("Forgot")).click();
```
### 7. XPath (Absolute & Relative)
Use when: No reliable attributes; supports complex queries.
Example:
```java
WebElement loginBtn = driver.findElement(By.xpath("//button[@type='submit']"));
loginBtn.click();
```
### 8. CSS Selector
Use when: Need speed and flexibility; preferred over XPath in many cases.
Example:
```java
WebElement searchBox = driver.findElement(By.cssSelector("input[name='q']"));
searchBox.sendKeys("Selenium");
```
## 🧠 Advanced Scenarios
### 🔁 Looping Through Elements
```java
List<WebElement> rows = driver.findElements(By.cssSelector("table tr"));
for (WebElement row : rows) {
    System.out.println(row.getText());
}
```
### ⏳ Handling Onload / Lazy Elements
```java
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement loaded = wait.until(ExpectedConditions.presenceOfElementLocated(By.id("lazy-loaded")));
```
### 🔄 Dynamic Element Example
```java
WebElement dynamic = driver.findElement(By.xpath("//div[contains(@id,'user_')]"));
```
### 🧩 Partially Loaded DOM
Use ExpectedConditions.visibilityOf() or ExpectedConditions.elementToBeClickable():
```java
WebElement button = wait.until(ExpectedConditions.elementToBeClickable(By.cssSelector(".btn-load")));
button.click();
```
## ⚠️ Common Challenges & Solutions

| Challenge                     | Solution                                      |
|------------------------------|-----------------------------------------------|
| Element not found            | Use `WebDriverWait`                           |
| StaleElementReferenceException | Re-locate after DOM update                 |
| Dynamic IDs                  | Use `XPath contains()`                        |
| Shadow DOM                   | Use `getShadowRoot()` in Selenium 4           |
| AJAX delays                  | Use `ExpectedConditions.invisibilityOf()`     |