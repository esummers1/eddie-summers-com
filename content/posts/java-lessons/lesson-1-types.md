---
date: 2019-05-10 20:00:00 +0000
title: "Java Lesson 1 - Types and Variables"
summary: "In Java, there are two kinds of types: **primitives** and **objects**. The chief difference is that objects can have behaviour (methods) and can be defined; primitives do not have behaviour and are baked in."
category: "Java Lessons"
---

In Java, there are two kinds of types: **primitives** and **objects**. The chief difference is that objects can have behaviour (methods) and can be defined; primitives do not have behaviour and are baked in.

All variables - items in memory which hold a value - must have a declared type, because Java is a strongly and statically typed language. Here are the most commonly used primitives:

```java
int i = 5;          // 32-bit whole number
long l = 8;         // 64-bit whole number
float f = 3.4;      // 32-bit decimal number
double d = 6.7;     // 64-bit decimal number
boolean b = true;   // true/false
char c = 't';       // single character
```

Note the declaration and initialization syntax - `int i;` is sufficient to create the variable `i`, but we can assign it a value at the same time if we wish.

An object is an instance of a class, and its type is the name of the class, which is to be capitalized. There are many built-in types, including the essential `String`. There are also "boxed primitive" types, which are essentially the object versions of the primitives, such as `Integer`.

Objects can be created through constructors, or returned from static factory methods (more on these later). A constructor is invoked with the `new` keyword, e.g.:

```java
// Use of constructor, with argument (System.in)
Scanner scanner = new Scanner(System.in);

// Special case - 'interned' from literal
String s = "hello world";
```
