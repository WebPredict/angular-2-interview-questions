# Angular 2 Interview Questions... And Answers!

This is a collection of Angular 2 interview questions I've found online, along with possible reasonable answers for most of them. Feel free to contribute / send corrections.

Note: PA == Possible Answer (one of many valid ones), A == Answer.

## Animations Questions

**How do you define transition between two states?**

PA: Using the transition and animate function in an animations block like so: `animations: [transition('inactive => active'), animate('100 ms ease-in')]` 

**How do you define a wildcare state?**
A: Using the asterisk - example: `transition('* => active'), animate('100ms ease-in'))`


