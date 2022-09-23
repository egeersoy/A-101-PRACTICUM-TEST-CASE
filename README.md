# A-101-PRACTICUM-TEST-CASE
selenium java


package tests;

import org.junit.Assert;
import org.openqa.selenium.By;
import org.openqa.selenium.StaleElementReferenceException;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.openqa.selenium.support.ui.Select;

import java.time.Duration;
import java.util.UUID;
import java.util.concurrent.atomic.AtomicReference;

public class test11 {
    private WebDriver driver;
    private String baseUrl;
    private WebElement element;

    public static void main(String[] args) throws InterruptedException {

        System.setProperty("webdriver.chrome.driver", "drivers/chromedriver.exe");
        WebDriver driver = new ChromeDriver();

        Actions action = new Actions(driver);

        driver.get("https://www.a101.com.tr/");
        driver.manage().window().maximize();
        driver.navigate().refresh();

        System.out.println("A101 sitesine başarıyla giriş yapıldı.");


        WebElement mainpage0 = driver.findElement(By.id("CybotCookiebotDialogBodyLevelButtonLevelOptinAllowAll"));
        mainpage0.click();

        WebElement mainpage1 = driver.findElement(By.cssSelector("[title*='GİYİM & AKSESUAR']"));
        action.moveToElement(mainpage1).build().perform();
        Thread.sleep(1000);
        mainpage1.click();

        System.out.println("Giyim ve Aksesuar sekmesi başarıyla açıldı.");

        WebElement mainpage2 = driver.findElement(By.cssSelector("div.categories > ul > li:nth-child(6) > a"));
        Thread.sleep(1000);
        mainpage2.click();

        System.out.println("Kadın İç Giyim sekmesi başarıyla açıldı.");

        AtomicReference<WebElement> mainpage3 = new AtomicReference<>();

        new WebDriverWait(driver, Duration.ofSeconds(4))
                .ignoring(StaleElementReferenceException.class)
                .until((WebDriver d) -> {
                    mainpage3.set(d.findElement(By.cssSelector("a[data-name=\"category_ids\"][data-value=\"1567\"]")));
                    return true;
                });
        mainpage3.get().click();

        System.out.println("Dizaltı Çorap sekmesi başarıyla açıldı.");

        Thread.sleep(4000);
        AtomicReference<WebElement> baslik = new AtomicReference<>();

        new WebDriverWait(driver, Duration.ofSeconds(15))
                .ignoring(StaleElementReferenceException.class)
                .until((WebDriver d) -> {
                    baslik.set(d.findElement(By.cssSelector("div.products-list > div > ul > li:nth-child(1) > article > a > div > header > hgroup > h3")));
                    return true;
                });
            Assert.assertTrue(baslik.get().getText().contains("Siyah"));

        AtomicReference<WebElement> siyahcorap = new AtomicReference<>();

        new WebDriverWait(driver, Duration.ofSeconds(15))
                .ignoring(StaleElementReferenceException.class)
                .until((WebDriver d) -> {
                    siyahcorap.set(d.findElement(By.cssSelector("body > section > section.page-list.js-container > div:nth-child(3) > div.content > div > div.col-md-10.col-sm-9 > div.products-list > div > ul > li:nth-child(1) > article > div > div.add-basket.js-add-basket-area > div.count > a")));
                    return true;
                });

        System.out.println("Siyah Çorap Doğrulaması başarıyla yapıldı.");

        siyahcorap.get().click();

        System.out.println("Siyah Çoraba başarıyla tıklandı.");


        WebElement sepeteekle = driver.findElement(By.cssSelector("body > section > section.page-product.js-product-container.js-product-init > div.container > div.content > div > div.row > div.col-sm-3 > div.product-buy-info.js-product-buy-info > button"));

        Thread.sleep(1000);
        sepeteekle.click();

        System.out.println("Ürün sepete başarıyla eklendi.");

        WebElement alisverisedevam = driver.findElement(By.cssSelector("#js-modal-basket > div.right-side > a.button.green.block"));
        Thread.sleep(1000);
        alisverisedevam.click();

        WebElement sepetim = new WebDriverWait(driver, Duration.ofSeconds(4))
                .until(dr -> dr.findElement(By.xpath("/html/body/section/header/div/div[2]/div[2]/a[4]")));
        Thread.sleep(1000);
        sepetim.click();

        System.out.println("Sepetim sekmesine başarıyla gidildi.");

        WebElement sepetonay = driver.findElement(By.cssSelector("body > section > div.page-basket > div.container.js-basket-container > div > div.col-sm-3 > div > a"));
        Thread.sleep(2000);
        sepetonay.click();

        System.out.println("Sepet başarıyla onaylandı.");

        WebElement nouye = driver.findElement(By.cssSelector("body > section > div.page-auth > div > div.row.js-block-user.login-row > div:nth-child(1) > div.auth__form__proceed__wrapper > a"));
        Thread.sleep(2000);
        nouye.click();

        System.out.println("Üyeliksiz işleme başarıyla devam edildi.");

        WebElement uyelik = driver.findElement(By.cssSelector("body > section > div.page-auth > div > div.row.js-block-email > div > div > form > div.field > input"));
        Thread.sleep(1000);
        uyelik.click();
        uyelik.sendKeys(String.join("",UUID.randomUUID().toString().split("-")) + "@hotmail.com");

        WebElement devamet = driver.findElement(By.cssSelector("body > section > div.page-auth > div > div.row.js-block-email > div > div > form > button"));
        Thread.sleep(3000);
        devamet.click();

        System.out.println("E-mail başarıyla girildi.");

        WebElement adres = new WebDriverWait(driver, Duration.ofSeconds(6))
                .until(dr -> dr.findElement(By.xpath("/html/body/section/section/div/div[2]/div/div[1]/div/div[1]/div[2]/ul[2]/li/a")));
        adres.click();

        WebElement adresbasligi = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(3) > div > div > label > input[type=text]"));
        adresbasligi.click();
        adresbasligi.sendKeys("Ev Adresi");

        WebElement ad = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(4) > div:nth-child(1) > div > label > input[type=text]"));
        ad.click();
        ad.sendKeys("Ege");

        WebElement soyad = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(4) > div:nth-child(2) > div > label > input[type=text]"));
        soyad.click();
        soyad.sendKeys("Ersoy");

        WebElement telefon = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(5) > div > div > label > input"));
        telefon.click();
        telefon.sendKeys("5301362241");

        WebElement il = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(7) > div:nth-child(1) > div > label > div > select"));
        il.click();
        Select il1 = new Select(driver.findElement(By.name("city")));
        il1.selectByVisibleText("KOCAELİ");

        WebElement ilce = new WebDriverWait(driver, Duration.ofSeconds(6))
                .until(dr -> dr.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(7) > div:nth-child(2) > div > label > div > select")));
        ilce.click();
        Thread.sleep(1000);
        Select ilce1 = new Select(driver.findElement(By.name("township")));
        ilce1.selectByVisibleText("İZMİT");

        WebElement mahalle = new WebDriverWait(driver, Duration.ofSeconds(6))
                .until(dr -> dr.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(8) > label > div > select")));
        mahalle.click();
        Thread.sleep(1000);
        Select mahalle1 = new Select(driver.findElement(By.name("district")));
        mahalle1.selectByVisibleText("AKARCA MAH");

        WebElement tamadres = driver.findElement(By.cssSelector("#js-orders-modal-container > div > div.modal-content > form > div:nth-child(9) > label > textarea"));
        Thread.sleep(1000);
        tamadres.click();
        tamadres.sendKeys("Hekimoğlu Sokak , C-1-4 Blok Daire:15 , Kocaeli/İzmit");

        WebElement kaydet = driver.findElement(By.xpath("//*[@id=\"js-orders-modal-container\"]/div/div[2]/form/button[1]"));
        Thread.sleep(2000);
        kaydet.click();

        System.out.println("Kullanıcı bilgileri başarıyla girildi.");

        Thread.sleep(2000);
        WebElement ilerle = driver.findElement(By.cssSelector("body > section > section > div > div.checkout-addresses.js-tab-content.active > div > div.col-sm-9 > div > div.continue > form > div.cargo > button"));
        ilerle.click();

        System.out.println("Ödeme sayfasına başarıyla girildi.");

        Assert.assertTrue(driver.getCurrentUrl().equals("https://www.a101.com.tr/orders/checkout/"));

        System.out.println("Ödeme sayfası başarıyla açılıyor.");

    }


}
