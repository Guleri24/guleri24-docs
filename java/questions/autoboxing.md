---
title: Autoboxing
parent: Questions
has_children: true
nav_order: 1
---
Date: 14 Oct 2021

A place dedicated to questions related to Autoboxing ;-)


Q. How does autoboxing handle the following code fragment?
    
    Integer a = null;
    int b = a;

A. It results in a run-time error. Primitive type can store 
every value of their corresponding wrapper type except `null`.

Q Why does the first group of statements print `true` , but 
the second `false`?

    Integer a1 = 100;
    Integer a2 = 100;
    System.out.println(a1 == a2);   // true

    Integer b1 = new Integer(100);
    Integer b2 = new Integer(100);
    System.out.println(b1 == b2);   // false

    Integer c1 = 150;
    Integer c2 = 150;
    System.out.println(c1 == c2);   // false

A. The second prints `false` because `b1` and `b2` are references
to different Integer objects. The first and third code fragments
rely on autoboxing. Surprisingly the first prints true because
vlaues between `-128` and `127` apper to refer to the same immutable
Integer objects (Java's implementation of valueOf() retrives a cached
values if the integer is between -128 and 127), while Java constructs 
new objects for each integer outside this range.
