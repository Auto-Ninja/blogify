# 🧪 WebElement Interactions 
#### 1. click()
Purpose: Simulates a mouse click on buttons, links, checkboxes, etc.
Example:
```java
WebElement loginBtn = driver.findElement(By.id("login"));
loginBtn.click();
```
#### 2. sendKeys(CharSequence...)
Purpose: Types text into input fields or simulates keyboard input.
Example:
```java
WebElement username = driver.findElement(By.name("username"));
username.sendKeys("admin");
```
#### 3. getText()
Purpose: Retrieves visible text from an element.
Example:
```java
WebElement message = driver.findElement(By.id("welcome"));
System.out.println(message.getText());
```
#### 4. isDisplayed()
Purpose: Checks if an element is visible on the page.
Example:
```java
WebElement banner = driver.findElement(By.className("promo"));
if (banner.isDisplayed()) {
    System.out.println("Banner is visible");
}
```
#### 5. isEnabled() and isSelected()
Purpose: Check if an element is interactable or selected (e.g., checkboxes).
Example:
```java
WebElement checkbox = driver.findElement(By.id("terms"));
if (!checkbox.isSelected()) {
    checkbox.click();
}
```
### 🎛️ Advanced Web Interactions
#### 1. Handling Dropdowns with Select Class
Use when: Working with ```<select>``` HTML tags.
Example:
```java
import org.openqa.selenium.support.ui.Select;

WebElement countryDropdown = driver.findElement(By.id("country"));
Select select = new Select(countryDropdown);
select.selectByVisibleText("United Kingdom");
select.selectByValue("UK");
select.selectByIndex(2);
```
#### 2. Mouse and Keyboard Actions with Actions Class
Use when: Performing hover, drag-and-drop, right-click, or keyboard simulation.
Example:
```java
import org.openqa.selenium.interactions.Actions;

Actions actions = new Actions(driver);
WebElement menu = driver.findElement(By.id("menu"));
actions.moveToElement(menu).perform(); // Hover

WebElement source = driver.findElement(By.id("drag"));
WebElement target = driver.findElement(By.id("drop"));
actions.dragAndDrop(source, target).perform();
```
#### 3. Handling Alerts, Popups, and Modal Dialogs
Use when: Dealing with JavaScript alerts or confirmation boxes.
Example:
```java
Alert alert = driver.switchTo().alert();
System.out.println(alert.getText());
alert.accept(); // or alert.dismiss();
```
#### 4. Working with Frames and Iframes
Use when: Interacting with content inside ```<iframe>``` or ```<frame>```.
Example:
```java
driver.switchTo().frame("frameName"); // or by index or WebElement
WebElement insideFrame = driver.findElement(By.id("submit"));
insideFrame.click();
driver.switchTo().defaultContent(); // Exit frame
```
#### 5. File Upload / Download Automation
##### File Upload:
Use when: ```<input type="file">``` is present.
Example:
```java
WebElement upload = driver.findElement(By.id("uploadFile"));
upload.sendKeys("C:\\Users\\user\\Documents\\resume.pdf");
```
##### File Download:
Approach: Configure browser profile to auto-download files.
Example (Chrome):
```java
ChromeOptions options = new ChromeOptions();
Map<String, Object> prefs = new HashMap<>();
prefs.put("download.default_directory", "C:\\Downloads");
options.setExperimentalOption("prefs", prefs);
WebDriver driver = new ChromeDriver(options);
```
### 🧠 Pro Tips
- Always use explicit waits for dynamic elements.
- Use Actions for complex gestures.
- Use Select only for ```<select>``` tags; otherwise, use XPath/CSS for custom dropdowns.
- For modal dialogs, ensure visibility before interacting.