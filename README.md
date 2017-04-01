# Angular 2 Interview Questions... And Answers!

This is a collection of Angular 2 interview questions I've found online, along with possible reasonable answers for most of them. Feel free to contribute / send corrections.

Note: PA == Possible Answer (one of many valid ones), A == Answer.

## Animations Questions

**How do you define transition between two states?**

PA: Using the transition and animate function in an animations block like so: `animations: [transition('inactive => active'), animate('100 ms ease-in')]` 

**How do you define a wildcare state?**
A: Using the asterisk - example: `transition('* => active'), animate('100ms ease-in'))`

## Template Syntax Questions

**What is a template reference variable, and how would you use it?**

A: A variable (defined using a #) in a component template, which can be referenced in other parts of the template. For example, a template variable for a form can then be referenced by other elements of the form.

**What are the possible ways to bind component properties to an associated template?**

A: interpolation binding, one way binding, two way binding.

## Component/Directive Questions

**What is the minimum definition of a component?**

A: A class with a Component decorator specifying a template.

**What is the difference between a component and a template?**

A: A component is a directive with a template (representing a view).

**What are different kinds of directives supported in Angular 2?**

A: Structural, directive, component, and attribute directives.

**How do components communicate with each other?**

A: Various ways - for example: Input/Output properties, services, ViewChild/ViewContent...

**How do you create two way data binding in Angular 2.0?**

Answer: By using the two-way binding syntax [()] along with ngModel…

**How would you create a component to display error messages throughout your application?**

A: Set up an ErrorHandler... TODO 

**How would you support logging in your Angular app?**

PA: Set up angular2-logger, which is a package inspired by log4j. 

**How do you resolve a template URL relative to a Component class?**

A: By specifying the moduleId to be module.id in the Component decorator. (Note: while this is still needed when using SystemJS, it is not necessary anymore when using Webpack module bundler for Angular 2 projects.)


## NgModules Questions:

**What is the purpose of NgModule?**

A: to give Angular information on a particular module’s contents, through decorator properties like: declarations, imports, exports, providers, etc.

**How do you decide to create a new NgModule?**

A: Typically for a nontrivial feature in an application, that will involve a collection of related components and services.

**What are the attributes that you can define in an NgModule annotation?**

A: declarations, imports, exports, providers, bootstrap

**What is the difference between a module's forRoot() and forChild() methods and why do you need it?**

A: forRoot and forChild are conventional names for methods that deliver different import values to root and feature modules.

**What would you have in a shared module?**

A: common components, directives, and pipes used in other modules in your application.

**What would you not put shared module?**

A: services that should not have multiple instances created for the application.

**What module would you put a singleton service whose instance will be shared throughout the application (e.g. ExceptionService andLoggerService)?**

A: Root Module

**What is the purpose of exports in an NgModule?**

A: provide components, directives, pipes to other modules for their usage.

**Why is it bad if SharedModule provides a service to a lazy loaded module?**
A: TODO

**Can we import a module twice?**

A: yes, and the latest import will be what is used.

**Can you re-export classes and modules?**

A: Yes (?)

**What kind of classes can you import in an angular module?**

A: Components, pipes, directives

## Services Questions:

**What is the use case of services?**

A: One very common use case is providing data to components, often by fetching it from a server. Though there’s no real definition of service from Angular point of view – it could do almost anything (e.g., logging is another common use case, among many).

**How are the services injected to your application?**

A: Via Angular’s DI (Dependency Injection) mechanism

**Why is it a bad idea to create a new service in a component like the one below?**
`let service = new DataService();`

A: The object may not be created with its needed dependencies.

**How to make sure that a single instance of a service will be used in an entire application?**

A: Provide it in the root module.

**Why do we need provider aliases? And how do you create one?**

A: To substitute an alternative implementation for a provider.  Can create like so: `{ provide: LoggerService, useClass: DateLoggerService }`
