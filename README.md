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

