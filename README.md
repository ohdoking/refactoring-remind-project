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


# Bad smells in Code
## Duplicated Code
* *Extract Method* and invoke the code from both places
* *Pull Up Field*
* *Form Template Method*
* if the method do the same things with a different algorithms, you can choose the clearer of the tow algorithms and use *Substitute Algorithm*


## Long Method
* decomposing method
* Long method meaning is not method length, Semanctic distance between what the method does and how it does it
* *Extract Method*
* use Replace temp with query to eliminate the temp variable.
* Long lists of parameters can be slimmed down with *Introduced Parameter Object* and *Preserve Whole Object*.
* if you’ve tried that, and you still have too many temps and parameters, you have to use *Replace Method with Method Object*.
* conditionals and loops -> *Decompose Conditional* to deal with conditional expression


## Large Class
* Extract Class to bundle a number of the variables
* if the component makes sense as a subclass, you’ll find *Extract Subclass* often is easier.
* Sometimes a class does not use all of its instance variables all of the time. If so, you may be able to *Extract Class* or *Extract Subclass* many times. 
* As with a class with a huge wad of variables, the usual solution for a class with too much code is either to *Extract Class* or *Extract Subclass*. 
* A useful trick is to determine how clients use the class and to use *Extract Interface* for each of those uses.
* when you may require keeping some duplicate data in both places and keeping the data in sync, you use *Duplicate Observed Data*.


## Long Parameter List
* Use *Replace Parameter with Method* when you can get the data in one parameter by making a request of an object you already know about.
* Use *Preserve Whole Object* to take a bunch of data gleaned from an object and replace it with the object itself.
* If you have several data items with no logical object, use *Introduce Parameter Object*.


## Divergent Change
* to clean this up you identify everything that changes for a particular cause and use *Extract Class* put them all together.


## Shotgun Surgery
* Shotgun surgery is similar to divergent change but is the opposite.
* when every  time you make a kind of change, you have to make a lot of little changes to a lot of different classes, you want to use *Move Method* and *Move Field* to put all the changes into a single class
* often you can use *Inline Class* to bring a whole bunch of behavior together
* Divergent change is one class that suffers many kinds of changes, and shotgun surgery is one change that alters many classes 


## Feature Envy
* the most common focus of the envy is the data
* the method clearly wants to be elsewhere, so you use *Move Method* to get it there
* only part of the method suffered from envy; it that case use *Extract Method* on the jealous bit and *Move Method* to give it a dream house.


## Data clumps
* The first step is to look for where the clumps appear as fields. Use Extract Class on the fields to turn the clumps into an object
* turn your attention to method signature suing Introduce Parameter Object or Preserve Whole Object to slim them down.


## Primitive Obsession
* Record types(allow you to structure data into meaningful groups) and Primitive types(are your building blocks)
* If the data value is a type code, use *Replace Type Code with Class* if the value does not affect behavior. If you have conditionals that depend on the type code, use *Replace Type Code with Subclasses* or *Replace Type Code with State/Strategy*. 
* If you have a group of fields that should go together, use ㅠ. If you see these primitives in parameter lists, try a civilizing dose of *Introduce Parameter Object*. If you find yourself picking apart an array, use *Replace Array with Object*. 


## Switch Statements
* you want the method of class that hosts the type code value. So use *Extract Method* to extract the switch statement then *Move Method* to get it onto the class where the polymorphism is need
* at the point you have to decide whether to *Replace Type Code with Subclasses* or *Replace Type code with State/Strategy* 
* when you have set up the inheritance structure, you can use *Replace Conditional with Polymorphism*.
* if you only have a few case that affect a single method and you don’t expect them to change, then polymorphism is overkill, in this case *Replace Parameter with Explicit Methods* is a good option. If one of your conditional case is a null, try *Introduce Null Object*


## Parallel Inheritance Hierarchies
* paroled inheritance hierarchies is really a special case of shotgun surgery. 
* if you use *Move Method* and *Move Field* , the hierarchy on the referring class disappears. 


## Lazy Class
* Lazy class has been downsized with refactoring
* if you have subclasses the aren’t doing enough, try to use *Collapse Hierarchy*.
* Nearly useless components should be subjected to *Inline Class*.


## Speculative Generality(추측성 일반화)
* if you have abstract classes that aren’t doing much, use *Collapse Hierarchy*.
* Unnecessary delegation can be removed with *Inline Class*.
* Method with unused parameters should be subject to *Remove Parameter*.
* Methods named with odd abstract names should be brought down to each with *Renamed Method*.


## Temporary Field
* Use *Extract Class* to create a home for the poor orphan variables.
* put all the code that concerns the variables into the component. You may also be able to eliminate conditional code by using *Introduce Null Object* to create an alternative component for when the variables aren’t valid.


## Message Chains
* The move the use here is *Hide Delegate*.
* See whether you can use *Extract Method* to take a piece of the code that uses it and then *Move Method* to push it down the chain.


## Middle Man
* You look at a class’s interface and find half the methods are delegating to this other class. After a while it is time to use *Remove Middle Man* and take to the object that really knows what’s going on
* If only a few methods aren’t doing much, use *Inline Method* to inline them into the caller
* if there is additional behavior, you can use *Replace Delegation with Inheritance* to turn the middle man into a subclass of the real object.

## Inappropriate Intimacy
* Overintimate classes need to be broken up as lovers were in ancient days. Use *Move Method* and *Move Field* to separate the pieces to reduce the intimacy. 
* See whether you can arrange a *Change Bidirectional Association to Unidirectional*. 
* If the classes do have common interests, use *Extract Class* to put the commonality in a safe place and make honest classes of them. 
* Or use *Hide Delegate* to let another class act as go-between. 
* Inheritance often can lead to overintimacy. Subclasses are always going to know more about their parents than their parents would like them to know. If it’s time to leave home, apply *Replace Delegation with Inheritance*. 


## Alternative Classes with Different Interfaces
* Keep using *Move Method* to move behavior to the classes until the protocols are the same. 
* If you have to redundantly move code to accomplish this, you may be able to use *Extract Superclass* to atone. 


## Incomplete Library Class
* if there are just a couple of methods that you wish the library class had, use *Introduce Foreign Method*.
* If there is a whole load of extra behavior, you need *Introduce Local Extension*.


## Data Class
* in early states these classes may have public fields. If so, you should immediately apply *Encapsulate Field* before anyone notices
* if you have collection fields, check to see whether they are properly encapsulated and apply *Encapsulate Collection* if they aren’t Use *Remove Setting Method* on any field that should not be changed.
* Look for where these getting and setting methods are used by other classes. Try to use *Move Method* to move behavior into the data class.
* if you can’t move a whole method, use *Extract Method* to create a method that can be moved.
* After a while you can start using *Hide Method* on the getters and setters.


## Refused Bequest
* The traditional story is that this means the hierarchy is wrong. You need to create a new sibling class and use *Push Down Method* and *Push Down Field* to push all the unused methods to 
the sibling. 
* We don’t mind refusing implementations, but refusing interface gets us on our high horses. In this case, however, don’t fiddle with the hierarchy; you want to gut it by applying *Replace Inheritance with Delegation*. 


## Comments
* It’s surprising how often you look at thickly commented code and notice that the comment are there because the code is bad.
* if we need a comment to explain what a block of code does, try *Extract Method*
* if the method is already extracted but you still need a comment to explain what it does, use *Rename Method*.
* If you need to state some rules about the required state of the system, use *Introduce Assertion*. 
* When you feel the need to write a comment, first try to refactor the code so that any comment becomes superfluous. 



** Any fool can write code that a computer can understand. Good programmers write code that humans can understand.


# Reference 

* Refactoring written by M.Folwer
* [Refactoring and Design Patterns](https://refactoring.guru/)
* [WikiDocs](https://wikidocs.net)
