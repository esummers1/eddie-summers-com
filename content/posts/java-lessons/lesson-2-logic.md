---
date: 2019-05-10 21:00:00 +0000
title: "Java Lesson 2 - Operators and Branching Logic"
summary: "Java, like all good programming languages, has the usual set of mathematical and logical operators. We can use logical operators to determine which branch of a program is executed."
category: "Java Lessons"
---

Java, like all good programming languages, has the usual set of mathematical and logical operators. We can use logical operators to determine which branch of a program is executed.

Below are the mathematical operators:

```java
int i = 2 + 3;          // addition
int j = 5 - 4;          // subtraction
int k = 4 * 9;          // multiplication
int l = 8 / 2;          // division
int m = 9 % 2;          // modulo (remainder after division)
```

Boolean values can be passed or assigned as literals or as the result of expressions - e.g. `return 3 > 2;` is equivalent to `return true;`, although rather less clear. Expressions can be combined using the logical operators:

```java
// Less than - expression is true
boolean one = 2 < 3;

// Less than or equal to - expression is true
boolean two = 2 <= 3;

// Greater than - expression is true
boolean three = 3 > 2;

// Greater than or equal to - expression is true
boolean four = 3 >= 2;

// Is equal to - expression is false
boolean five = 7 == 8;

// Is not equal to - expression is true
boolean six = 7 != 8;

// AND operator - expression is false
boolean seven = true && false;

// OR operator - expression is true
boolean eight = true || false;

// OR is in brackets and evaluated first
boolean nine = true && (false || true);

// NOT operator (!) - expression is true
boolean ten = true && !false;
```

Expressions can be composed of arbitrarily many layers of these operators. In Java, AND will evaluate before OR if both are on the same level, but it's usually best to nest things properly in brackets to avoid confusion. Objects should be compared with the `Object.equals(object)` method rather than the `==` operator, but this is a topic we'll cover more later on.

To do something on the condition that some expression is true, we use `if` statements:

```java
int a = 5;
int b = 6;

if (a != b) {
    // do something
} else {
    // do something else
}
```

An `if` block can have as many `else if` blocks as you like - these specify a condition that must be true for the block they contain to be executed, just like `if`. If you do not provide an `else` block, and none of the `if` or `else if` conditions are true, all of the blocks will be skipped entirely. If one of your `else if` conditions is true _in addition_ to an earlier `if` or `else if` condition being true, it will be skipped - once one block is executed, **none of the others is checked**. So, for example:

```java
if (1 < 2) {
    // true, so this block will be entered
} else if (2 < 3) {
    // also true, but this block will never be entered
}
```

A common idiom is to evaluate a boolean value directly, i.e. `if (booleanVariable == true)` is equivalent to `if (booleanVariable)`. Also, rather than asking if something `== false`, it's simpler to say something like `if (!booleanVariable)`. So, for instance:

```java
boolean isRed = true;
boolean isBlue = false;
boolean isBlack = false;

// We want to do something if our colour is red, but only if it's not also black
if (isRed && !isBlack) {
    // do the thing
}
```
