---
date: 2020-10-09 16:00:00 +0000
title: "Economy of Expression"
summary: "Why the syntax of programming languages really matters."
type: "post"
categories: ["Programming"]
---

I've been thinking a lot lately about the differences between different programming languages. Languages can be celebrated over others for their features, e.g. static typing over dynamic typing, or supporting multiple inheritance, or the quality of their standard libraries. All of these are valid, but I would like to argue that, outside of edge cases, *economy of expression* should be considered a language's most important feature. If a language has great standard libraries that save you a lot of code, it is the expressiveness of the code in your project that should be considered the primary victory.

Note that I am not advocating that languages should be as terse or brief as possible: this is an economy of characters, not of expression. Something is expressive to the reader if it conveys its meaning, and something has good economy of expression if a lot of meaning can be conveyed with less verbose language. Excess boilerplate code is hard to read, and [readability is crucial](https://www.danjb.com/tech_blog/readable_code) in scenarios where code being easy to understand is important to the project's success, i.e. all software projects.

## Example

Let's compare three related languages in their ability to do two things, in the idiomatic style of each language.

### Task 1 - List Transformation

At my job, I spend a lot of time working with the Salesforce platform, which provides a server-side language called Apex. This is derived from an early version of Java - so early in fact that it lacks support for generics! It certainly does not support lambda expressions, or higher-order functions of any kind.

Let's imagine we have some Animals, and we want to list the ages of all the gorillas:

```java
public List<Animal> getGorillaAgesFrom(List<Animal> animals) {
  List<Animal> gorillas = new List<Animal>();
  for (Animal animal : animals) {
    if (animal.species ==  'Gorilla') {
      gorillas.add(animal);
    }
  }

  List<Integer> ages = new List<Integer>();
  for (Animal gorilla : gorillas) {
    ages.add(gorilla.age);
  }
  return ages;
}
```

Now, for the same thing in modern Java:

```java
public List<Animal> getGorillaAgesFrom(List<Animal> animals) {
  return animals.stream()
      .filter(animal -> animal.getSpecies().equals("Gorilla"))
      .map(animal::getAge)
      .collect(Collectors.toList());
}
```

And, finally, in Kotlin:

```kotlin
fun getGorillaAgesFrom(animals: List<Animal>): List<Animal> {
  return animals.filter { it.species == "Gorilla" }.map { it.age }
}
```

Java's huge advantage over Apex of supporting higher-order functions allows it to express the same idea as the Apex code in a much neater manner. Kotlin, which shortcuts traditional Java getters and setters using its property convention, and whose `Collections` implementation does away with the need for Java's calls to `stream()` and `collect()`.

I would argue that even though the Java example is much-improved, the Kotlin code is so expressive that it almost reads as a sentence. The syntax it lacks compared to the Java equivalent is purely boilerplate or logistical, meaning more of what remains expresses the programmer's intent. Comparing the Kotlin example with the Apex example is particularly eye-opening. Spare a thought for Apex developers who can't implement even rudimentary type-safe streams, due to the lack of generics support.

### Task 2 - Object Construction

For this exercise, Apex and Java are essentially the same, so I will just use Java.

Imagine we want to declare a type with the following:

- One immutable field that is always required
- Two mutable fields that are always required
- Two mutable fields that are optional

Barring the use of third-party libraries like Lombok, which had to be created to solve the problem I'm about to demonstrate, here's how this would be done in Java:

TODO