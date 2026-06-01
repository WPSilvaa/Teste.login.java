</> Java

import pages.LoginPage;
import org.junit.jupiter.api.*;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {

    WebDriver driver;

    @BeforeEach
    public void iniciar(){

        driver = new ChromeDriver();

        driver.get("https://www.saucedemo.com");
        driver.manage().window().maximize();
    }

    @Test
    public void loginComSucesso(){

        LoginPage login = new LoginPage(driver);

        login.preencherUsuario("standard_user");
        login.preencherSenha("secret_sauce");
        login.clicarLogin();

        Assertions.assertTrue(
            driver.getCurrentUrl().contains("inventory")
        );
    }

    @AfterEach
    public void finalizar(){
        driver.quit();
    }
}
