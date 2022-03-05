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

Non-required parts:
* The name args is a variable name, so it can be called anything you want, although it is typically called args.
* Whether its parameter type is an array(`String[] args`) or Varargs(`String... args`) does not matter because arrays can be passed into varargs.

**Note:** A single application may have multiple classes containing an entry point (main) method. The entry method. The entry point of the application is determined by the class name passed as an arguments to the java command.

Inside the main method, we see the following statement:
`System.out.println("Hello World");`

Let's break down this statement element by element:

Element : Purpose
* `System` : This denotes that the subsequent expression will call upon the `System` class, from the `java.lang` package.

* `.` : This is a "dot operator". Dot operators provide you access to a classes members; i.e. its fields (variables) and its methods. In this case, this dot operator allows you to reference the out static field within the `System` class.

* `out` : This is the name of the static field of `PrintStream` type within the `System` class containing the standard output functionality.

* `.` : This is another dot operator. This dot operator provides access to the println method within the out variable.

* `println` : This is the name of a method within the `PrintStream` class. This method in particular prints the contents of the parameters into the console and inserts a newline after.

* `(` : This parenthesis indicates that a method is being accessed (and not a field) and begins the parameters being passed into the println method.

* `"Hello World"` : This is the `String` literal that is passed as a parameter, into the `println` method.

* `)` : This parenthesis signifies the closure of the parameters being passed into the `println` method.

* `;` : This semicolon marks the end of the statement.

**Note:** Each statement in Java must end with a semicolon(;).

The method body and class body are then closed.

```
	} // end of main function scope
} 	  // end of class HelloWorld scope
```


  
