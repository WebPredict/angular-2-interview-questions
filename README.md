# Angular 2 Interview Questions... And Answers!

This is a collection of Angular 2 interview questions I've found online, along with (hopefully) correct answers for most of them. Feel free to contribute / send corrections.

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


## Lifecycle Hooks Questions:

**What is the possible order of lifecycle hooks in Angular?**

A: ngOnChanges, ngOnInit, ngDoCheck, ngAfterContentInit, ngAfterContentChecked, ngAfterViewInit, ngAfterViewChecked, ngOnDestroy.

**When will ngOnInit be called?**

A: Called once, after the first ngOnChanges.

**How would you make use of onNgInit()?**

PA: fetch initial component data (e.g. from server).

**What would you consider a thing you should be careful doing on onNgInit()?**

A: ??

**What is the difference between onNgInit() and constructor() of a component?**

A: a directive’s data-bound input properties are not set until after construction, so that’s one difference.

## Pipes Questions:

**What is a pure pipe?**

A: A pipe that is only executed when Angular detects a pure change to the input value (e.g. new primitive object or new object reference).

**What is an impure pipe?**

A: A pipe that is executed during every component change detection cycle (i.e., often – every keystroke, mouse move).

**What is an async pipe?**

A: an impure pipe that accepts a promise or observable as input and eventually returns emitted values.

**What kind of data can be used with async pipe?**

A: stateful, asynchronous

**What types of pipes are supported in Angular 2?**

A: Pure and impure pipes (async pipes a kind of impure pipe).

## Routing Questions:

**What is the difference between RouterModule.forRoot() vs RouterModule.forChild()? Why is it important?**

A: forRoot is a convention for configuring app-wide Router service with routes, whereas forChild is for configuring the routes of lazy-loaded modules.

**How does loadChildren property work?**

A: the Router calls it to dynamically load lazy loaded modules for particular routes.

**When does a lazy loaded module get loaded?**

A: When its related route is first requested.

**How would you use a Route Guard?**

A: You would implement CanActivate or CanDeactivate and specify that guard class in the route path you’re guarding. 

**How would you intercept 404 errors in Angular 2?**

A: Can provide a final wildcard path like so: { path: ‘**’, component: PageNotFoundComponent }

**This link doesn't work. Why? How do I fix it?**
`<div routerLink='product.id'></div>`

A: `<a [routerLink]=”[’product.id’]”>{{product.id}}</a>`

## Styling Questions:

**How would you select a custom component to style it?**

A: TODO

**How do you reference the host of a component?**

A: let DI inject an ElementRef into the constructor of your component.

**What pseudo-class selector targets styles in the element that hosts the component?**

A: The :host pseudo class selector.

**How would you select all the child components' elements?**

A: with the @ViewChildren decorator, like for example:

`@ViewChildren(ChildDirective) viewChildren: QueryList<ChildDirective>;`

**How would you select a css class in any ancestor of the component host element, all the way up to the document root?**

A: using the :host-context() pseudo-class selector.

**What selector force a style down through the child component tree into all the child component views?**

A: use the /deep/ selector along with :host pseudo-class selector.

**What does :host-context() pseudo-class selector target?**

A: The :host-context() selector looks for a CSS class in any ancestor of the component host element, up to the document root.

**What does the following css do?**
`:host-context(.theme-light) h2 {
  background-color: red;
}`

A: Will change this component’s background-color to red if the context of the host has the .theme-light class applied.


## Forms Questions:

**When do you use template driven vs model driven forms? Why?**

A: Template driven forms make more sense for simpler forms, at least in terms of validation. Model driven or Reactive forms lend themselves to easier testing of the validation logic, so if that’s complex, Reactive forms make more sense. There’s also the issue of asynchronous (template driven forms) vs. synchronous (model driven).

**How do you submit a form?**

PA: use the ngSubmit event binding like so: `<form (ngSubmit)="onSubmit()" …>`

**What's the difference between NgForm, FormGroup, and FormControl? How do they work together?**

A: FormGroup tracks the value and validity state of a group of AbstractControl instances. FormControl does the same for an individual control. NgForm is a directive that Angular automatically attaches to each `<form>` tag. It has its own ‘valid’ property which is true only if every contained control is valid.

**What's the advantage of using FormBuilder?**

A: Reduces repetition and clutter by handling details of control creation for you.

**How do you add form validation to a form built with FormBuilder?**

A: pass in Validator objects along with the FormControl objects...

**What's the difference between dirty, touched, and pristine on a form element?**

A: dirty means it contains user data, touched means the user has at least done something with a particular control (perhaps just literally ‘touched’ it by giving it focus?), and pristine means the control has not been touched at all by the user.

**How can you access validation errors in the template to display error messages?**

PA: use formErrors

**What is async validation and how is it done?**

A: verifying some field using some asynchronous call (perhaps a server call)… return a `Promise<ValidationResult>` from your validator. When creating a FormControl object, you can pass an asynchronous validator into the constructor (e.g. `new FormControl(‘value’, syncValidator, asyncValidator)`).

