# asp-mvc-best-practices
Best practices when designing an ASP .NET MVC application


### Avoid Duplication in Razor views

Use view layouts and partial views adress this. Continuous refactoring of chtml file has to be done.

Implement helpers for reusable markup generation : using @helper directive inside Razor or by extending HtmlHelper (@Html object inside Razor views)

### Processing vs Formatting 

You should not use Razor to perform business logic or manipulate your domain model objects in any way. 
Data formatting is a View matter, it should be kept in Razor code

### Domain-Driven-Design

- Put model classes into a separate assembly whenever possible.

For applications with a large complex model, it's a good idea to create a separate assembly for the model to avoid accidently mixing concerns. You can then reference the model assembly in your ASP.NET MVC project.

- Avoid use of ViewBag, this breaks Domain driven design and benefits such as intelisense and compile-time checking are lost. Strongly typed Views are strongly recommended!

> Less duplicated business logic.
>The view is easier to read when there is no business logic present.
>Testing business rules is isolated to the model.

### css & js

For faster page loads:
- Minify js & css and use Bundles:
Details in (https://chsakell.com/2015/02/15/asp-net-mvc-solution-architecture-best-practices/)
- Place all of your CSS in the HEAD element. place js elements right before the closing tag of the '<body> element.

### Thin Controllers

Keep controller as thin as possible, and separate View-centric controller from Api controller (those which manipulate data) :  http://henkmollema.github.io/web-api-in-mvc-6/

### Avoid view-models boilerplate

Keep in mind that ViewModels add an extra layer on Models. There should be a good reason to use them and when used they could add boilerplate code. If you end up with creating viewmodels, i'd recommend you to use this framework http://automapper.org/ for object-object mapping

### Avoid parsing http stuff inside controllers

For this you should implement and use custom model binding logic. Model binding is a powerful and customizable feature that eliminates the grind and toil of dealing with HTTP
requests directly and lets us work with C# objects rather than dealing with Request.Form[] , Request.QueryString[] an even Session[].

Its keep your code clean and testable as binding data is lower layer that should not interfer with business logic


### Validation through DataAnnotation

Validation is the important part when working with any application. In ASP.NET MVC, we can implement validation on server side using DataAnnotation which is found in usingSystem.ComponentModel.DataAnnotations namespace.

It's preferred to put all validation logic in the model : when it's the case then validation has to be done in the frontend.

Note : In some scenarios validation is complex and needs to be done in the backend when repositories/services are involved.


### Explicitly name view in action methods

It's better to pass view name to View method.


### use POST/REDIRECT/GET pattern when submitting forms

According to the definition of the HTTP POST and GET verbs:

HTTP GET is used for non-changing (idempotent) data to your model.
HTTP POST is used for changing data to your model.


### Use Filters for Cross-cutting concerns

For concerns such as logging, authentication, profiling, exception handling etc.. you'd better use custom attributes and decorate your controllers and action using 

** for further reading ** 
https://blogs.msdn.microsoft.com/aspnetue/2010/09/17/best-practices-for-asp-net-mvc/
https://github.com/EduardoPires/EquinoxProject