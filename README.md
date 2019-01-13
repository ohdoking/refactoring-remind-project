# Refactoring
1. What is Refactoring?
2. Principles in Refactoring 
3. Bad smell in code
4. Building Test
5. Toward a Catalog of refectorings 
6. Composing method
7. Moving features between Objects
8. Organizing Data
9. Simplifying conditional expressions.
10. Making method code simpler
11. Dealing with generalization.
12. Big refactoring 
13. Refactoring, reuse, and reality
14. Refactoring tools.

# What is Refactoring?

### First step in Refactoring 

I need to build a sold set of tests for that section of code. The test are essential because even though I follow refactorings structured to avoid most of the opportunities for introducing bugs, I’m still human and still make mistakes. Thus I need solid test.

TEST is such an important part of refactoring!

### Decomposing and redistributing the statement method.

split up the long method and move the pieces to better classes.
Smaller pieces of code then to make things more manageable.
* Switch statement 

Analyze the code to figure out what to do with the local variables 
Tool
* Refactoring Browser(smalltalk)

*comment* is essential for don’t forget what I learned or fixed

### Removing temp valuable 

### making inheritance.


# Principles in Refactoring.
## What is refactoring?
*Refactoring*
* (noun) a change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior.
*  (verb) to restructure software by applying a series of refactorings without changing its observable behavior.

### need to distinguish adding function and refactoring. 

*Adding function*
* just add new capabilities

*Refactoring*
* make a point of not adding function, only restructured the code

## Why should you Refactor?
Refactoring is not cure for all software ills like “silver bullet” but. It is as valuable tool, a pair of silver pliers that helps you keep a good grip on your code. 

### Refactoring improves the design of software

* Refactoring improves the design of software.
* Refactoring makes software easier to understand.
* Refactoring helps you find bugs.
* Refactoring helps you program faster.

## When should you refactor? 
* The Rule of Three(Three strikes and you refactor )
* Refactor when you add function
* Refactor when you need a fix a bug
* Refactor as you do a code review

Indirection can pay for itself. 
* To enable sharing of logic.
* To explain intention and implementation separately.
* To isolate change.
* To encode conditional logic .

## Problems with Refactoring
### Databases
### Changing interfaces
* Don’t publish interfaces prematurely. Modify your code ownership policies to smooth refactoring. 

### Design changes that are difficult to refactor

### When shouldn’t you refactor?
* a deadline is near

### Refactoring and Design
One argument is that refactoring can be an alternative to upfront design.
An important result of this change in emphasis is a greater movement toward simplicity of design. 
Refactoring can lead to simpler designs without sacrificing flexibility 

### Refactoring and Performance 
* three general approaches to writing fast software 
- The most serious of these is time budgeting, used often in hard real-time systems .  
- The second approach is the constant attention approach. 
- The third approach to performance improvement takes advantage of this 90 percent statistic 
* Having a well-factored program helps with this style of optimization in two ways. 
- First, it gives you time to spend on performance tuning. 
-  Second, with a well-factored program you have finer granularity for your performance analysis. Your profiler leads you to smaller parts of the code, which are easier to tune. 



** Any fool can write code that a computer can understand. Good programmers write code that humans can understand.