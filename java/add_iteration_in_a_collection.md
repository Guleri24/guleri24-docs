---
title: Add iteration in a collection
parent: Java
has_children: false
nav_order: 1
---
Date: 14 Oct 2021

# To implement iteration in a collection
* Include the following import statement so that our code can refer
to Java's `java.util.Iterator` interface:

    import java.util.Iterator;

* Add the following to the class declaration, a promise to provide an
`iterator()` method, as specified in the `java.util.Iterable` interface:

    implements Iterable<Item>

    e.g public class Bag<Element> implements Iterable<Element> { } 

* Implement a method `iterator()` that returns an object from a class 
that implements the `Iterator` interface:

    public Iterator<Item> iterator() {
        return new LinkedIterator();
    }

* Implement a nested class that implements the `Iterator` interface
by including the methods `hasNext()`, `next()`, and `remove()`.
