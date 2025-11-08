# 🧰 Actions 
## 🧰 What Is the Actions Class?
The Actions class is part of the org.openqa.selenium.interactions package and provides a way to build and perform a chain of user interactions.

```java
Actions actions = new Actions(driver);
```

## 🖱️ Mouse Interactions with Actions
### 1. Hover Over an Element
```java
WebElement menu = driver.findElement(By.id("menu"));
Actions actions = new Actions(driver);
actions.moveToElement(menu).perform();
```
### 2. Click and Hold
```java
WebElement element = driver.findElement(By.id("drag"));
actions.clickAndHold(element).perform();
```
### 3. Right Click (Context Click)
```java
WebElement element = driver.findElement(By.id("context-menu"));
actions.contextClick(element).perform();
```
### 4. Double Click
```java
WebElement element = driver.findElement(By.id("double-click"));
actions.doubleClick(element).perform();
```
### 5. Drag and Drop
```java
WebElement source = driver.findElement(By.id("source"));
WebElement target = driver.findElement(By.id("target"));
actions.dragAndDrop(source, target).perform();
```
## ⌨️ Keyboard Interactions with Actions
### 1. Send Keys to an Element
```java
WebElement input = driver.findElement(By.id("search"));
actions.moveToElement(input).click().sendKeys("Selenium WebDriver").perform();
```
### 2. Keyboard Shortcuts (e.g., Ctrl + A, Ctrl + C)
```java
WebElement input = driver.findElement(By.id("text-box"));
input.sendKeys("Some text");

actions.keyDown(Keys.CONTROL)
       .sendKeys("a")
       .keyUp(Keys.CONTROL)
       .perform(); // Select all text
```
### 3. Press Enter or Tab
```java
actions.sendKeys(Keys.ENTER).perform();
```
## 🧪 Full Example: Mouse + Keyboard
```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.Keys;

public class ActionsDemo {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        driver.get("https://example.com");

        Actions actions = new Actions(driver);

        // Hover over menu
        WebElement menu = driver.findElement(By.id("menu"));
        actions.moveToElement(menu).perform();

        // Right-click
        WebElement context = driver.findElement(By.id("context"));
        actions.contextClick(context).perform();

        // Drag and drop
        WebElement drag = driver.findElement(By.id("drag"));
        WebElement drop = driver.findElement(By.id("drop"));
        actions.dragAndDrop(drag, drop).perform();

        // Keyboard input
        WebElement input = driver.findElement(By.id("search"));
        actions.moveToElement(input).click().sendKeys("Selenium").sendKeys(Keys.ENTER).perform();

        driver.quit();
    }
}
```
## ⚠️ Tips & Best Practices

| Tip                                 | Why It Matters                                  |
|-------------------------------------|--------------------------------------------------|
| Use `.perform()` at the end         | Executes the built action chain                  |
| Chain multiple actions              | Improves readability and control                 |
| Use `moveToElement()` before typing| Ensures focus is on the right element            |
| Use `keyDown()`/`keyUp()` for modifiers | Needed for Ctrl, Shift, Alt combinations     |