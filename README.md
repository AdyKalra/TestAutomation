# TestAutomation

## Fluent Page Object Pattern in Automated Testing

* More efficient usage and improved readability are achievable through the incorporation of the Page Objects with Fluent API. The result will be Fluent Page Objects or Fluent Page Object Pattern.

###Fluent Interface 
####Definition

In software engineering, a fluent interface (as first coined by Eric Evans and Martin Fowler) is an implementation of an object-oriented API that aims to provide the most readable code.A fluent interface is typically implemented by using method cascading (concretely method chaining) to relay the instruction context of a subsequent call (but a fluent interface entails more than just method chaining).
* The context is defined through the return value of a called method-self-referential, where the new context is equivalent to the last context.
* Self-referential, where the new context is equivalent to the last contest terminated by the return of a void context.
* Terminated by the return of a void context.

![1](https://automatetheplanet.com/wp-content/uploads/2015/05/fluent-page-object-pattern-uml-diagram1-1024x622.png)

The classes and objects participating in this pattern are:

*Page Objects (BingMainPage)- Holds the actions that can be performed on the page like Search and Navigate. It exposes an easy access to the Page Validator through the Validate() method. The best implementations of the pattern hide the usage of the Element Map, wrapping it through all action methods.
*BasePage<S, M> – Gives access to the child’s page element map class and defines a standard navigation operation.
*BasePage<S, M, V> – Adds an instance to the child page’s validator class through the Validate method.
*BaseSingleton – This is an abstract class that contains a static property of its child instance BaseSingleton – This is an abstract class that holds a static property of its child instance.
*BaseElementMap – Provides easier access to current browser and functions to switch between different frames.
*BasePageValidator<S, M, V> – Gives all child validators instance to the current element map and the page object itself.

