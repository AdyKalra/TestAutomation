# Fluent Page Object Pattern C# Code

## Test’s Test Case

The primary goal of the example test for the Fluent Page Object Pattern is going to be to search for images in Bing with different settings.
1. Navigate to Bing site
2. Search for Term
3. Switch to Images tab
4. Change query settings

![1](https://automatetheplanet.com/wp-content/uploads/2015/05/fluent-page-objects-test-test-case-1024x315.png)

## Fluent Page Objects Implementation Code

If we don’t use Fluent Page Objects, our test looks like the code below.
[TestClass]
Public class FluentBingTests
{ 
    [TestInitialize]
    Public void SetupTest ()
    {
        Driver.StartBrowser ();
    }

    [TestCleanup]
    Public void TeardownTest ()
    {
        Driver.StopBrowser ();
    }

    [TestMethod]
    Public void SearchForImageNotFuent ()
    {
        P.BingMainPage bingMainPage = new P.BingMainPage ();
        bingMainPage.Navigate ();
        bingMainPage.Search ( "facebook");
        bingMainPage.ClickImages ();
        bingMainPage.SetSize (Sizes.Large);
        bingMainPage.SetColor (Colors.BlackWhite);
        bingMainPage.SetTypes (Types.Clipart);
        bingMainPage.SetPeople (People.All);
        bingMainPage.SetDate (Dates.PastYear);
        bingMainPage.SetLicense (Licenses.All);
    }
}

The primary goal of the Fluent Page Object Pattern is to enable you to use the power of method chaining. To achieve it, the BingMainPage should be slightly modified.

public class BingMainPage : BaseFluentPageSingleton<BingMainPage, BingMainPageElementMap, BingMainPageValidator>
{
    public BingMainPage Navigate(string url = "http://www.bing.com/")
    {
        base.Navigate(url);
        return this;
    }

    public BingMainPage Search(string textToType)
    {
        this.Map.SearchBox.Clear();
        this.Map.SearchBox.SendKeys(textToType);
        this.Map.GoButton.Click();
        return this;
    }

    public BingMainPage ClickImages()
    {
        this.Map.ImagesLink.Click();
        return this;
    }

    public BingMainPage SetSize(Sizes size)
    {
        this.Map.Sizes.SelectByIndex((int)size);
        return this;
    }

    public BingMainPage SetColor(Colors color)
    {
        this.Map.Color.SelectByIndex((int)color);
        return this;
    }

    public BingMainPage SetTypes(Types type)
    {
        this.Map.Type.SelectByIndex((int)type);
        return this;
    }

    public BingMainPage SetLayout(Layouts layout)
    {
        this.Map.Layout.SelectByIndex((int)layout);
        return this;
    }

    public BingMainPage SetPeople(People people)
    {
        this.Map.People.SelectByIndex((int)people);
        return this;
    }

    public BingMainPage SetDate(Dates date)
    {
        this.Map.Date.SelectByIndex((int)date);
        return this;
    }

    public BingMainPage SetLicense(Licenses license)
    {
        this.Map.License.SelectByIndex((int)license);
        return this;
    }
}

The most important part of the above code is that all methods return the current instance of the page.
return this;

Not quietly related to the pattern itself but interesting to point here is the way of choosing the different options. All of them are of type SelectElement. Here are the different settings elements that you can discover in the BingMainPageMap.
public SelectElement Sizes
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'Size']")));
    }
}

public SelectElement Color
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'Color']")));
    }
}

public SelectElement Type
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'Type']")));
    }
}

public SelectElement Layout
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'Layout']")));
    }
}

public SelectElement People
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'People']")));
    }
}

public SelectElement Date
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'Date']")));
    }
}

public SelectElement License
{
    get
    {
        return new SelectElement(this.browser.FindElement(By.XPath("//div/ul/li/span/span[text() = 'License']")));
    }
}

All of them use the same location technique- XPath expression that finds the div by its inner text.
I believe that it is a poor decision to switch settings through text variable, so in my implementation I use enums.
* Sample Settings Enum

public enum Dates
{
    All,
    Past24Hours,
    PastWeek,
    PastMonth,
    PastYear
}

This way the chosen enum value represents an integer from 0-4 that is the same as the index of the same values in the select element.

public BingMainPage SetDate(Dates date)
{
    this.Map.Date.SelectByIndex((int)date);
    return this;
}

## Create Fluent Page Validator

In order to keep the method chaining available even after a usage of validation methods, a modification of the BasePageValidator is mandatory too.
## Base Fluent Page Validator
# Not Fluent Version

public class BasePageValidator<M>
    where M : BasePageElementMap, new()
{
    protected M Map
    {
        get
        {
            return new M();
        }
    }
}

## Fluent Version

public class BasePageValidator<S, M, V>
    where S : BaseFluentPageSingleton<S, M, V>
    where M : BasePageElementMap, new()
    where V : BasePageValidator<S, M, V>, new()
{
    protected S pageInstance;

    public BasePageValidator(S currentInstance)
    {
        this.pageInstance = currentInstance;
    }

    public BasePageValidator()
    {
    }

    protected M Map
    {
        get
        {
            return new M();
        }
    }
}

All changes are applied to provide us access to the current Page instance, in order to be able to return it every time in our validation methods.
## Not Fluent BingMainPageValidator

public class BingMainPageValidator : BasePageValidator<BingMainPageElementMap>
{
    public void ResultsCount(string expectedCount)
    {
        Assert.IsTrue(this.Map.ResultsCountDiv.Text.Contains(expectedCount), "The results DIV doesn't contains the specified text.");
    }
}

## Fluent BingMainPageValidator

public class BingMainPageValidator : BasePageValidator<BingMainPage, BingMainPageElementMap, BingMainPageValidator>
{
    public BingMainPage ResultsCount(string expectedCount)
    {
        Assert.IsTrue(this.Map.ResultsCountDiv.Text.Contains(expectedCount), "The results DIV doesn't contains the specified text.");
        return this.pageInstance;
    }
}

Because of the changes in the BasePageValidator the BagePage classes should be modified to support the new fluent base validator.

[TestClass]
public class FluentBingTests
{ 
    [TestInitialize]
    public void SetupTest()
    {
        Driver.StartBrowser();
    }

    [TestCleanup]
    public void TeardownTest()
    {
        Driver.StopBrowser();
    }

    [TestMethod]
    public void SearchForImageFuent()
    {
        P.BingMainPage.Instance
                            .Navigate()
                            .Search("facebook")
                            .ClickImages()
                            .SetSize(Sizes.Large)
                            .SetColor(Colors.BlackWhite)
                            .SetTypes(Types.Clipart)
                            .SetPeople(People.All)
                            .SetDate(Dates.PastYear)
                            .SetLicense(Licenses.All);
    }
}

The fluent page objects significantly improve the readability of tests. Also, it is quite easy to write tests, thanks to the method chaining.

