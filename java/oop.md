---
title: Object Oriented Programming
parent: Java
has_children: false
nav_order: 2
---
Date: 2 Mar 2022

# OOP - Object Oriented Programming
Is a programming paradigm where everything is represented as an object.

## Fundamentals
### Objects
An object is an entity that has states and behaviors.

* State tells us how the object looks or what properties it has.

* Behavior tells us what the object does.

### Classes
A class is a template or blueprint from which objects are created.

Imagine a class as cookie-cutter and objects as cookies.

## Principes of object-oriented programming
* Encapsulation
* Inheritance
* Abstraction
* Polymorphism

### Encapsulation
Is a process of wrapping code and data together into a single unit.

Imagine a capsule with mixture of several meds.
This can be achieved using `private` access modifiers that can't be accessed by anything outside the class.
And use `getter` and `setter` to access that value.

(In Java, these methods should follow JavaBeans naming standards.)

* Advantage
1. We can make a class `read-only` or `write-only`. 
2. Control over the data. (Logic + Setter = Control)
3. Data hiding. Other classes can't access private members of a class directly.

### Inheritance
Is a mechanism in which one object acquires all the states and behaviors of a parent object.
* Uses parent-child relationship (IS-A relationship).

** A rule of thumb in java: make instance variables `private` and instance methods `public`.

public instance methods and private instance variables (using getters and setters) get inherited.

#### Types of Inheritance in Java
1. Single
2. Multilevel
3. Hierarchical 
4. Multiple
5. Hybrid

* Class allows single, multilevel and hierarchical inheritances. 
* Interface allows multiple and hybrid inheritances.

Note: A class can extend only one class however it can implement any number of interfaces. An interface can extend more than one interfaces.

#### Relationships
1. IS-A relationship
Refers to inheritance or implementation

* Generalization
Uses an IS-A relationship from a specialization class to generalization class.

2. HAS-A relationship
An instance of one class HAS-A reference to an instance of another class.

* Aggregation
In this relationship, the existence of class A and B are not dependent on each other.

* Composition
In this relationship, class B can not exist without clas A - but class A can exist without class B.

* Advantage of inheritance
1. Code resuse.
2. You have more flexibility to change code.
3. You can use polymorphism: method overriding requires IS-A relationship.

### Abstraction
Is a process of hiding the implementation details and showing only functionality to the user.

In Java, we can achieve abstraction in two ways: 
* `abstract` class (0 to 100%)
* `interface` (100%)

The keyword `abstract` can be applied to classes and methods.
`abstract` and `final` or `static` can never be together.

#### 1. Abstract class
Can't be instantiated (can't create objects of abstract classes).  
They can have :
+ constrcutors
+ static methods
+ final methods

#### 2. Abstract methods
Does;t have implementation (no method body and ends up with a semi colon).
It shouldn't be marked as `private`.

#### 3. Abstract class and Abstract methods
* If at least one abstract method exists inside a class then the whole class should be abstract.
* We can have abstract class with no abstract methods.
* We can have any number of abstract as well as non-abstract methods inside an abstract class at the same time.
* The first concrete sub class of an abstract class must provide implementation to all abstract methods.
* If this doesn't happen, then the sub class also should be marked as abstract. 

#### When do we want to mark a class as abstract?
1. To force sub classes to implement abstract methods.
2. To solve having actual objects of that class.
3. To keep having a class reference.
4. To retain common class code.

### Interface
Is a blueprint of a class.
An interface is 100% abstract.
No constructors are allowed here. It represents an IS-A relationship

**NOTE** Interfaces only define required methods. We can not retain common code.

* An interface can have `only abstract methods`, not concrete methods. By default, interface methods are `public` and `abstract`. So inside the interface, we don't need to specify `public` and `abstract`.

So when a class implements an interface's method without specifying the access level of that method, the compiler will throw an error stating `Cannot reduce the visibility of the inherited method from interface". So that implmented method's access level must be set to `public`.

**NOTE** By default, interface variables are `public`, `static` and `final`.


