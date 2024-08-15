package swagLabs;

import java.util.List;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

import io.github.bonigarcia.wdm.WebDriverManager;

public class PlacingAnOrder {

	WebDriver driver;

	@BeforeTest
	public void browserSetUp(){
		WebDriverManager.chromedriver().setup();
		driver=new ChromeDriver();

		driver.manage().window().maximize();
		driver.get("https://www.saucedemo.com/");
	}

	@Test(priority=1)
	public void login(){
		driver.findElement(By.id("user-name")).sendKeys("standard_user");
		driver.findElement(By.id("password")).sendKeys("secret_sauce");
		driver.findElement(By.id("login-button")).click();
		driver.manage().timeouts().implicitlyWait(3, TimeUnit.SECONDS);
	}

	@Test(priority=2)
	public void addtoCart1(){
		driver.findElement(By.id("add-to-cart-sauce-labs-backpack")).click();
	}


	@Test(priority=3) 
	public void item2(){
		List<WebElement> alllist=driver.findElements(By.xpath("//a//div[@class='inventory_item_name ']"));

		for(WebElement ii:alllist) 
		{
			System.out.println(ii.getText());

			if(ii.getText().contains("Sauce Labs Onesie")) 
			{
				ii.click();
				driver.findElement(By.xpath("//button[@id='add-to-cart']")).click();
				break;
			}
        }
	}	


	@Test(priority=4)
	public void clickonCart(){
		driver.findElement(By.xpath("//a[@class='shopping_cart_link']")).click();

	}

	@Test(priority=5)
	public void checkOut(){
		driver.findElement(By.id("checkout")).click();

	}

	@Test(priority=6)
	public void infoCheckout(){
		driver.findElement(By.id("first-name")).sendKeys("magic");
		driver.findElement(By.id("last-name")).sendKeys("wonderland");
		driver.findElement(By.id("postal-code")).sendKeys("100000");
		driver.findElement(By.id("continue")).click();
		driver.manage().timeouts().implicitlyWait(3, TimeUnit.SECONDS);

	}

	@Test(priority=7)
	public void printOrder() {
		List<WebElement> cartSummary =driver.findElements(By.id("checkout_summary_container"));

		for(WebElement ii:cartSummary) {
			System.out.println(ii.getText());	
		}
	}

	@Test(priority=8)
	public void finish(){
		driver.findElement(By.id("finish")).click();
		driver.manage().timeouts().implicitlyWait(3, TimeUnit.SECONDS);

	}

	@Test(priority=9)
	public void backHome() {
		driver.findElement(By.id("back-to-products")).click();	


	}

	@AfterTest
	public void closeWindow(){
		driver.close();
	}
}
