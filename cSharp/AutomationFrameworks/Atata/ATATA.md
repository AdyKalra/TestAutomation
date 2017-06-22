# Name - ATATA
### URL - https://atata-framework.github.io/
### Features
1. WebDriver 
Based on Selenium WebDriver and preserves all its features.
2. Page Object
Provides unique fluent page object pattern that is easy to implement and maintain.
3. Components
Supports a rich set of HTML components.
4. Integration
Works on any .NET test engine (e.g. NUnit, xUnit) as well as on CI systems like TeamCity or TFS.
5. Triggers
A bunch of triggers to bind with different component events.
6. Verification
A set of methods and triggers for the component and data verification.
7. Configurable
Defines the default component search strategies as well as additional settings.
8. Logging
Built-in customizable logging and screenshot capturing functionality.
9. Extensible
Atata.Bootstrap and Atata.KendoUI packages have a set of ready to use components.

* Download the sampleproject from https://github.com/atata-framework/atata-sample-app-tests
The Demo Project tests application demonstrates different testing approaches and features of the Atata framework. It uses Atata Sample App (repository) as a testing website and NUnit 3 as a test engine.

# Getting Started

## Installation

* To get started just install the Atata NuGet package.
PM> Install-Package Atata

# Tutorials 
* https://www.codeproject.com/Articles/1158365/Atata-New-Test-Automation-Framework

# Run Tests
Build the solution
Tests -> Run all tests

# Explanation

* I would like to show the usage of the framework using the demo website. It is simple website that contains the following: Sign In page, Users page, User Details page and User Edit window.

* The test project will use the NuGet packages: Atata, Atata.Bootstrap, Selenium.WebDriver, Selenium.Support, WebDriver.ChromeDriver.win32, NUnit and NUnit3TestAdapter.

* I use NUnit but it is not required, you can use any .NET testing framework like MSTest or SpecFlow. But for me NUnit fits the best.

* Let's try to implement an auto-test for the following test case:

1. Sign In
2. Click "New" button on User List page
3. Create a new user
4. Verify the new user's data on User List page
5. Navigate to the user's details
6. Verify the user's details

* Any page can be represented with the page object. I will try to explain the Atata's stuff step by step. To start we need to implement the page object class for Sign In page.

