---
date: 2020-10-11 12:00:00 +0000
title: "Economy of Expression"
summary: "Why the syntax of programming languages really matters."
type: "post"
categories: ["Programming"]
---

I've been thinking a lot lately about the differences between different programming languages. Languages can be celebrated over others for their features, e.g. static typing over dynamic typing, or supporting multiple inheritance, or the quality of their standard libraries. All of these are important, but I would like to argue that  *economy of expression* should be considered among a language's most important features.

In a language which has good economy of expression, developer productivity is increased for two big reasons: first, the same behaviour can be created with less code, which takes less time to write and has less room for syntactical mistakes. Second, when working with others or in a large project, it is easier to understand at a glance what some piece of code is doing, and hence takes less time to add something new.

Note that I am not advocating that languages should be as terse or brief as possible: that is economy of characters, not of expression. Something is expressive to the reader if it conveys its meaning, and something has good economy of expression if a lot of meaning can be conveyed with less verbose language. Excess boilerplate code is hard to read, and [readability is crucial](https://www.danjb.com/tech_blog/readable_code) in scenarios where code being easy to understand is important to the project's success, i.e. all software projects.

## Example

Let's compare some related languages in their ability to do two things, in the idiomatic style of each language.

In my job, I spend a lot of time working with the Salesforce platform, which provides a server-side language called [Apex](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_dev_guide.htm). This is derived from an early version of Java - so early in fact that it lacks support for generics! It certainly does not support lambda expressions, or higher-order functions of any kind.

### Task 1 - List Transformation

Let's imagine we have some Animals, and we want to list the ages of all the gorillas:

```java
public List<Integer> getGorillaAgesFrom(List<Animal> animals) {
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
public List<Integer> getGorillaAgesFrom(List<Animal> animals) {
  return animals.stream()
      .filter(animal -> animal.getSpecies().equals("Gorilla"))
      .map(animal::getAge)
      .collect(Collectors.toList());
}
```

And, finally, in [Kotlin](https://kotlinlang.org/):

```kotlin
fun getGorillaAgesFrom(animals: List<Animal>): List<Int> {
  return animals.filter { it.species == "Gorilla" }.map { it.age }
}
```

Java's huge advantage over Apex of supporting higher-order functions allows it to express the same idea as the Apex code in a much neater manner. Kotlin, which shortcuts traditional Java getters and setters using its property convention, and whose `Collections` implementation does away with the need for Java's calls to `stream()` and `collect()`, goes even further.

I would argue that even though the Java example is much-improved, the Kotlin code is so expressive that it almost reads like a single sentence. The syntax it lacks compared to the Java equivalent is purely boilerplate or logistical, meaning more of what remains expresses the programmer's intent. Comparing the Kotlin example with the Apex example is particularly eye-opening. Spare a thought for Apex developers who can't implement even rudimentary type-safe streams, due to the lack of generics support!

### Task 2 - Object Construction

For this exercise, Apex and Java are essentially the same, so I will just use Java.

Imagine we want to declare a type with the following:

- An immutable field that is always required
- A mutable field that is always required
- A mutable field that is optional, and has some default value

Barring the use of third-party libraries like [Lombok](https://projectlombok.org/), which had to be created to solve the problem I'm about to demonstrate, here's how this would be done in Java:

```java
public class Dummy {
  private final Object immutable;
  private Object mutable;
  private Object optional;

  public Dummy(Object immutable, Object mutable) {
    this(immutable, mutable, "Default");
  }

  public Dummy(Object immutable, Object mutable, Object optional) {
    this.immutable = immutable;
    this.mutable = mutable;
    this.optional = optional;
  }

  public Object getImmutable() {
    return immutable;
  }

  public Object getMutable() {
    return mutable;
  }

  public Object getOptional() {
    return optional;
  }

  public void setMutable(Object mutable) {
    this.mutable = mutable;
  }

  public void setOptional(Object optional) {
    this.optional = optional;
  }
}
```

And now, the Kotlin version:

```kotlin
class Dummy(val immutable: Any, var mutable: Any, var optional: Any = "Default")
```

There are a couple of things to note here. One, this code is much easier to write. Yes, modern IDEs can generate things like getters and setters for you, but shouldn't we let the compiler do that instead, as Kotlin's does? Two, the Kotlin version is not only equivalent, but easier to use from other Kotlin code. Kotlin allows default values for function parameters (including constructors, as we have just seen), but also lets you supply arguments in any order if you name them:

```kotlin
val dummy = Dummy(mutable = something, immutable = somethingElse)
```

This last feature has the added benefit of clearly labelling what each of the arguments is for, making the calling code more understandable.

These features remove much of the need for overloading methods, which in my opinion should be considered more a workaround than a pattern. Note that this also means Kotlin has little use for the builder pattern, since the primary constructor can be used so flexibly, and other initialization logic can go in a secondary constructor in the class body.

## Summary

I think that a lot of low-level design choices in programming revolve around making what you write easier to understand. Since languages differ in the expressiveness of their syntaxes, it seems sensible to me to be careful about which we choose to work with - to pick ones which are more expressive. Writing clean and simple code in a verbose and clumsy language, when a better alternative is available, is stepping over pounds to pick up pennies.
