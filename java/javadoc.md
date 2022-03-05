---
title: Documenting Java Code
parent: Java
has_children: false
---
Date: 5 Mar 2022

# Documenting Java Code
Documentation for Java code is often using `javadoc`. 
Javadoc was created by Sun Microsystems for the purpose of generating API documentation in HTML format from Java source code.

## Building Javadocs From the Command Line
The most basic usage of the tool is:
`javadoc JavaFile.java`
Which will generate HTMl from the Javadoc comments in `JavaFile.java`.

A more practical use of the command line tool, which will recursively read all java files in `[source-directory]`, create documentation for `[pacakge.name]` and all sub-packages, and place the generated HTML in the `[docs-directory]` is:

```
javadoc -d [docs-directory] -subpackages -sourcepath [source-directory] [package.name]
```

 

  
