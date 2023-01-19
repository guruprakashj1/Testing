# Testing - a keyword driven framework library for automation functional testing of web application using selenium and java 

Step 1: Create a keyword-driven framework library for automation functional testing of web applications using Selenium and Java.

Step 2: Define a set of keywords that will be used to drive the automation testing process. These keywords should be specific to the web application being tested and should include actions such as navigating to a specific page, entering text into a form field, clicking a button, etc. List follows  

navigate_to_page
click_button
enter_text
select_dropdown
submit_form
verify_text
verify_element_present
hover_over_element
switch_to_frame
switch_to_window
take_screenshot
scroll_to_element
wait_for_element
assert_url
assert_title
clear_field
drag_and_drop
right_click
double_click
execute_javascript

Keywords : [navigate_to_page, click_button, enter_text, select_dropdown, submit_form, verify_text, verify_element_present, hover_over_element, switch_to_frame, switch_to_window, take_screenshot, scroll_to_element, wait_for_element, assert_url, assert_title, clear_field, drag_and_drop, right_click, double_click, execute_javascript.]

Step 3: Create a spreadsheet that maps each keyword to a specific function in the Selenium and Java code. This will serve as a reference for the test automation team when creating test scripts.

Step 4: Create a class in Java that will be used to execute the keywords. This class should include methods that correspond to each keyword, and should utilize the Selenium library to perform the actions specified by the keyword.

Step 5: Create test scripts using the keywords defined in the spreadsheet. These scripts should utilize the methods in the Java class to perform the actions specified by the keywords.

Step 6: Execute the test scripts and record the results. Any issues or errors should be reported and addressed.

Step 7: Continuously update and maintain the keyword-driven framework library as needed, based on changes to the web application or new requirements for the automation testing process.

Detail implementation of keyword for the keyword-driven framework library for automation functional testing of web applications using Selenium and Java.


> navigate_to_page:

public void navigate_to_page(String url) {
    driver.get(url);
}

or


public void navigate_to_page(WebDriver driver,String url) {
    driver.get(url);
}
This code uses the Selenium WebDriver's get() method to navigate to the specified URL. The url variable passed in as a parameter is the target URL that the script should navigate to. The driver variable is an instance of the Selenium WebDriver class, which is used to interact with the web application being tested.

This keyword could be used in a test script like this:


navigate_to_page("https://www.google.com");
This would navigate the web driver to the google homepage.

click_button:

public void click_button(String buttonId) {
    WebElement button = driver.findElement(By.id(buttonId));
    button.click();
}
or


public void click_button(WebDriver driver,String buttonId) {
    WebElement button = driver.findElement(By.id(buttonId));
    button.click();
}
This code uses the Selenium WebDriver's findElement() method to locate the button on the web page by its id, and the click() method to simulate a click on the button. The buttonId variable passed in as a parameter is the id of the button that the script should click on.

This keyword could be used in a test script like this:


click_button("submit-button");
This would click on the button with the id "submit-button" on the web page.

Note: you can use different locators like xpath, css, classname, etc. It depends on the way the button is identified in the website HTML.


enter_text:

public void enter_text(String elementId, String text) {
    WebElement element = driver.findElement(By.id(elementId));
    element.clear();
    element.sendKeys(text);
}

or


public void enter_text(WebDriver driver,String elementId, String text) {
    WebElement element = driver.findElement(By.id(elementId));
    element.clear();
    element.sendKeys(text);
}

This code uses the Selenium WebDriver's findElement() method to locate the element on the web page by its id, the clear() method to clear any pre-existing text in the element, and the sendKeys() method to enter the specified text. The elementId variable passed in as a parameter is the id of the element that the script should enter text into, and the text variable is the text that should be entered.

select_dropdown:

public void select_dropdown(String elementId, String option) {
    Select dropdown = new Select(driver.findElement(By.id(elementId)));
    dropdown.selectByVisibleText(option);
}

or


public void select_dropdown(WebDriver driver,String elementId, String option) {
    Select dropdown = new Select(driver.findElement(By.id(elementId)));
    dropdown.selectByVisibleText(option);
}

This code uses the Selenium WebDriver's findElement() method to locate the dropdown element on the web page by its id, and the Select class to select an option from the dropdown. The elementId variable passed in as a parameter is the id of the dropdown element that the script should select an option from, and the option variable is the option that should be selected.

submit_form:

public void submit_form(String formId) {
    driver.findElement(By.id(formId)).submit();
}
or


public void submit_form(WebDriver driver,String formId) {
    driver.findElement(By.id(formId)).submit();
}

This code uses the Selenium WebDriver's findElement() method to locate the form on the web page by its id, and the submit() method to submit the form. The formId variable passed in as a parameter is the id of the form that the script should submit.

verify_text:

public boolean verify_text(String expectedText) {
    String actualText = driver.findElement(By.tagName("body")).getText();
    return actualText.contains(expectedText);
}

or


public boolean verify_text(WebDriver driver,String expectedText) {
    String actualText = driver.findElement(By.tagName("body")).getText();
    return actualText.contains(expectedText);
}


verify_element_present:

public boolean verify_element_present(String elementId) {
    try {
        driver.findElement(By.id(elementId));
        return true;
    } catch (NoSuchElementException e) {
        return false;
    }
}

hover_over_element:

public void hover_over_element(String elementId) {
    WebElement element = driver.findElement(By.id(elementId));
    Actions action = new Actions(driver);
    action.moveToElement(element).perform();
}

switch_to_frame:

public void switch_to_frame(String frameId) {
    driver.switchTo().frame(frameId);
}

switch_to_window:

public void switch_to_window(String windowTitle) {
    for (String handle : driver.getWindowHandles()) {
        driver.switchTo().window(handle);
        if (driver.getTitle().equals(windowTitle)) {
            break;
        }
    }
}

take_screenshot:

public void take_screenshot(String fileName) {
    File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
    try {
        FileUtils.copyFile(src, new File(fileName));
    } catch (IOException e) {
        e.printStackTrace();
    }
}

scroll_to_element:

public void scroll_to_element(String elementId) {
    WebElement element = driver.findElement(By.id(elementId));
    ((JavascriptExecutor) driver).executeScript("arguments[0].scrollIntoView(true);", element);
}

wait_for_element:

public void wait_for_element(String elementId) {
    WebDriverWait wait = new WebDriverWait(driver, 10);
    wait.until(ExpectedConditions.visibilityOfElementLocated(By.id(elementId)));
}

assert_url:

public void assert_url(String expectedUrl) {
    String actualUrl = driver.getCurrentUrl();
    Assert.assertEquals(expectedUrl, actualUrl);
}

assert_title:

public void assert_title(String expectedTitle) {
    String actualTitle = driver.getTitle();
    Assert.assertEquals(expectedTitle, actualTitle);
}

clear_field:

public void clear_field(String elementId) {
    driver.findElement(By.id(elementId)).clear();
}

drag_and_drop:

public void drag_and_drop(String sourceId, String targetId) {
    WebElement source = driver.findElement(By.id(sourceId));
    WebElement target = driver.findElement(By.id(targetId));
    Actions action = new Actions(driver);
    action.dragAnddrop(source, target).perform();
}

right_click:

public void right_click(String elementId) {
    WebElement element = driver.findElement(By.id(elementId));
    Actions action = new Actions(driver);
    action.contextClick(element).perform();
}

double_click:

public void double_click(String elementId) {
    WebElement element = driver.findElement(By.id(elementId));
    Actions action = new Actions(driver);
    action.doubleClick(element).perform();
}
execute_javascript:

public void execute_javascript(String script) {
    ((JavascriptExecutor) driver).executeScript(script);
}
The code is an examples and just one way of implementing each keyword, and the actual implementation might vary depending on the specific web application being tested and the requirements of the test automation process.

Also, please note that all these codes pass the driver as an argument, this is because to create a reusable library it is important to not to hard code the driver.
