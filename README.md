# asp-mvc-best-practices
Best practices when designing an ASP .NET MVC application


### Avoid Duplication in Razor views

Use view layouts and partial views adress this. Continuous refactoring of chtml file has to be done

### Processing vs Formatting 

You should not use Razor to perform business logic or manipulate your domain model objects in any way. 
Data formatting is a View matter, it should be kept in Razor code

### Domain-Driven-Design

-- Put model classes into a separate assembly whenever possible.
-- Avoid use of ViewBag, this breaks Domain driven design and benefits such as intelisense and compile-time checking are lost.

### css & js
-- Minify js & css and use Bundles:
Details in (https://chsakell.com/2015/02/15/asp-net-mvc-solution-architecture-best-practices/)
-- Place all of your CSS in the HEAD element. place js elements right before the closing tag of the <body> element.

### Thin Controllers
Keep controller as thin as possible, and separate View-centric controller from Api controller (those which manipulate data) :  http://henkmollema.github.io/web-api-in-mvc-6/


