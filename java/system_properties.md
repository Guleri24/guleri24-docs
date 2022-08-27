---
title: System Properties
parent: Java
has_children: false
---
Date: 6 Mar 2022

# System Properties

Java system properties determine the environemnt in which the Java program run. Starting a Java Virtual Machine (JVM) sets the system properties for that instance of the JVM.

Java maintains a set of system properties for its operations. Each **java system properties** is a key-value (String-String) pair. For example, one such system properties is "java.vm.vendor:GraalVM Community".

**NOTE:**
```
Please note that access to system properties can be restricted by the Java security manager and policy file. By default, Java programs have unrestricted access to all the system properties.
```

We can retrieve all the system properties via `System.getProperties()` or we can also retrieve individual property via `System.getProperty(key)` method.

In Java, we can use `System.getProperties()` to get all the system properties.

```
Properties properties = System.getProperties();
properties.forEach((k, v) -> System.out.println(k + ":" + v));
```

**Example**
```
SystemProperties.java

import java.util.Properties;

public class SystemProperties {
	public static void main(String[] args) {
		Properties properties = System.getProperties();
		properties.forEach((k, v) -> System.out.println(k + ":" + v));
	}
}
```

**Sorted System Properties**
```
SortedSystemProperties.java

import java.util.Properties;

public class SortedSystemProperties {
	public static void main(String[] args) {
		Properties properties = System.getProperties();

		LinkedHashMap<String, String> collect = properties.entrySet().stream()
			.collect(Collectors.toMap(k -> (String) k.getKey(), e -> (String) e.getValue())) 
			.entrySet().stream().sorted(Map.Entry.comparingByKey())
			.collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue, 
						(oldValue, newValue) -> oldValue, LinkedHashMap::new));

		collect.forEach((k, v) -> System.out.println(k + ":" + v));
	}
}
```



