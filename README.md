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
