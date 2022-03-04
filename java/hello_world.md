---
title: Hello World
parent: Java
has_children: false
nav_order: 1
---
Date: 4 Mar 2022

# A closer look at the Hello World program
```
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

This "Hello World" program is a single file, which consists of `HelloWorld` class definition, a main method, and a statement inside the main method.

`public class HelloWorld`

The `class` keyword begins the class definition for a class named `HelloWorld`. Every Java application contains at least one class definition.

`public static void main(String[] args) {`

This is an entry point method (defined by its name and signature of `public static void main(String[]))` from which the `JVM` can run your program. Every Java program should have one. It is:

* public:
Meaning that the method can be called from anywhere mean from outside the program as well.

* static:
Meaning it exists and can be run by itself(at the class level without creating an object).

* void:
Meaning it returns no value. 

**Note:** This is unlike C and C++ where a return code such as int is expected (Java's way is System.exit()).

The main method accepts:
* An array(typically called `args`) of `String`s passed as arguments to main function (e.g. from command line arguments).

Almost all this is required for a Java entry point method.
