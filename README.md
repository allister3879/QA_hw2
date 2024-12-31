Diana Narynbekova, SE-2217

## SearchTest.java
```java
package diane_hw2;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;

public class SearchTest {
    public static void main(String[] args) {
        System.setProperty("webdriver.edge.driver", "C:\\Program Files\\msedgedriver.exe");
        
        WebDriver driver = new EdgeDriver();
        try {
           driver.get("https://www.youtube.com");
            
            WebElement searchBox = driver.findElement(By.name("search_query")); 
            searchBox.sendKeys("ASMR");
            searchBox.submit();
            
            Thread.sleep(3000);
            
            WebElement resultStats = driver.findElement(By.xpath("//ytd-video-renderer"));
            if (resultStats.isDisplayed()) {
                System.out.println("Search results displayed successfully.");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            driver.quit();
        }
    }
}
```
This code automates a search on YouTube using Selenium WebDriver. It initializes the Edge browser, navigates to YouTube, and locates the search bar using its name attribute. The script inputs "ASMR" into the search bar and submits the search. After a brief wait, it verifies if the search results are displayed by checking the visibility of a video element using its XPath. If successful, a confirmation message is printed. Finally, the browser is closed in the finally block, ensuring cleanup even if an exception occurs.
#### Demo
https://github.com/user-attachments/assets/c2183c08-92ba-4450-a0e5-a6557c6154ed

## LoginLogoutTest.java
```java
package diane_hw2;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.openqa.selenium.support.ui.ExpectedConditions;
import java.time.Duration;

public class LoginLogoutTest {
    public static void main(String[] args) {
        System.setProperty("webdriver.edge.driver", "C:\\Program Files\\msedgedriver.exe");

        WebDriver driver = new EdgeDriver();

        try {
            driver.get("https://practicetestautomation.com/practice-test-login/");

             WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(15));

             WebElement usernameField = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("username")));
            WebElement passwordField = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("password")));
            WebElement submitButton = wait.until(ExpectedConditions.elementToBeClickable(By.id("submit")));

             usernameField.sendKeys("student");
            passwordField.sendKeys("Password123");
            submitButton.click();

           WebElement successMessage = wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//h1[text()='Logged In Successfully']")));
            if (successMessage.isDisplayed()) {
                System.out.println("Login successful.");
            }

            WebElement logoutButton = wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//a[text()='Log out']")));
            logoutButton.click();

            WebElement loginButton = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("submit")));
            if (loginButton.isDisplayed()) {
                System.out.println("Logout successful.");
            }

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            driver.quit();
        }
    }
}
```
The code automates the login and logout process on a practice test website. It waits for the username, password fields, and submit button to become visible, then inputs credentials and submits the form. After confirming a successful login, it clicks the logout button and verifies that the login button reappears, confirming a successful logout.
#### Demo
https://github.com/user-attachments/assets/f24930c1-67da-4876-8a17-2860b1e8ecd7

## FlightBookingTest
```java
package diane_hw2;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.edge.EdgeDriver;

public class FlightBookingTest {
    public static void main(String[] args) {
        
    	System.setProperty("webdriver.edge.driver", "C:\\Program Files\\msedgedriver.exe");

        WebDriver driver = new EdgeDriver();
        try {
            driver.get("https://www.blazedemo.com/");
            
            WebElement departureCity = driver.findElement(By.name("fromPort")); 
            WebElement destinationCity = driver.findElement(By.name("toPort"));
            WebElement findFlightsButton = driver.findElement(By.xpath("//input[@value='Find Flights']"));
            
            departureCity.sendKeys("Paris");
            destinationCity.sendKeys("Buenos Aires");
            findFlightsButton.click();
            
            Thread.sleep(3000);
            
            
            WebElement chooseFlightButton = driver.findElement(By.xpath("//tbody/tr[3]/td[1]/input[1]"));
            chooseFlightButton.click();

          
            WebElement nameField = driver.findElement(By.id("inputName"));
            WebElement addressField = driver.findElement(By.id("address"));
            WebElement cityField = driver.findElement(By.id("city"));
            WebElement stateField = driver.findElement(By.id("state"));
            WebElement zipCodeField = driver.findElement(By.id("zipCode"));
            WebElement cardType = driver.findElement(By.id("cardType"));
            WebElement creditCardNumber = driver.findElement(By.id("creditCardNumber"));
            WebElement purchaseButton = driver.findElement(By.xpath("//input[@value='Purchase Flight']"));
            
            nameField.sendKeys("John Doe");
            addressField.sendKeys("123 Elm St");
            cityField.sendKeys("Springfield");
            stateField.sendKeys("IL");
            zipCodeField.sendKeys("62704");
            cardType.sendKeys("Visa");
            creditCardNumber.sendKeys("4111111111111111");
            purchaseButton.click();

          
            Thread.sleep(3000);
            WebElement confirmation = driver.findElement(By.tagName("h1"));
            if (confirmation.getText().equals("Thank you for your purchase today!")) {
                System.out.println("Flight booked successfully.");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            driver.quit();
        }
    }
}
```
The code automates the flight booking process on a demo website. It selects a departure and destination city, submits a flight search, and chooses a flight. Then, it fills in personal and payment details, and clicks the purchase button. After a brief wait, it checks for a confirmation message to verify that the flight was booked successfully.

#### Demo
https://github.com/user-attachments/assets/184fd135-3ae1-407e-9d93-38ed538df26f
