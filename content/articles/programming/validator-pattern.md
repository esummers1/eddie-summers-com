---
date: 2022-09-06 10:00:00 +0000
title: "Validator Pattern"
summary: "A simple way to express reusable validation rules."
type: "post"
categories: ["Programming"]
---

Needing to validate that the properties of some data match your expectations is a common problem, whether that's validating that the invariants of some domain construct are respected, or that the format of a request received from a client is as you expect. Some languages allow you to express rules like this as [part of the type system](http://blog.cleancoder.com/uncle-bob/2021/06/29/MoreOnTypes.html), but for languages that don't, we can do better than the usual chain of `if`/`else if` statements.

The example below assumes you're using Kotlin on the Spring framework, and want to take advantage of [request-context exception handling](https://spring.io/blog/2013/11/01/exception-handling-in-spring-mvc). You may not wish to throw an exception immediately when a rule fails, but instead e.g. return a `false` value if any rule is violated, and make a decision based on that.

## Elements

First, we need to define a `Rule`, to express a reusable constraint:

```kotlin
interface Rule {
  fun isInvalid(): Boolean
  fun fail()
}
```

Next, a `Validator` to manage and execute a list of `Rules`. For readers unfamiliar with Kotlin, `apply` is a [scope function](https://kotlinlang.org/docs/scope-functions.html) allowing us to execute the lambda and return `this` in one step.

```kotlin
class Validator(private val rules: MutableList<Rule> = mutableListOf()) {

  fun validate() = rules.firstOrNull { it.isInvalid() }?.fail()

  fun specify(rule: Rule) = this.apply { rules.add(rule) }
}
```

Now, we can define a few `Rules`, e.g.:

```kotlin
class ShouldInclude(private val value: Any?, private val description: String) : Rule {
  override fun isInvalid() = value == null
  override fun fail() {
    throw InvalidPayloadException("$description field is missing from the request.")
  }
}

class ShouldHaveStrongPassword(private val password: String) : Rule {
  override fun isInvalid(): Boolean = password.length < 16
  override fun fail() = throw WeakPasswordException()
}

class ShouldHaveUniqueUsername(
  private val username: String,
  private val userService: UserService
) : Rule {
  override fun isInvalid(): Boolean = userService.getByUsername(username) != null
  override fun fail() = throw DuplicateUsernameException()
}
```

## Example

So if we now wanted to validate that a request to register a new user was valid, we could use them like so:

```kotlin
@PostMapping
fun register(@RequestBody body: RegistrationRequest): ResponseEntity<Any> {

  Validator()
    .specify(ShouldInclude(body.firstName, "First name"))
    .specify(ShouldInclude(body.surname, "Surname"))
    .specify(ShouldInclude(body.email, "Email address"))
    .specify(ShouldInclude(body.password, "Password"))
    .specify(ShouldHaveStrongPassword(body.password!!))
    .specify(ShouldHaveUniqueUsername(body.email!!, userService))
    .validate()

  userService.register(...)

  return ResponseEntity(HttpStatus.CREATED)
}
```

Rules with a general scope like `ShouldInclude` or e.g. `ShouldBeValidUserId` can be reused in multiple places, and since we throw the relevant exception (or return `false`, if you prefer) the moment we encounter a failing rule, we can order them so that inputs to later rules can be assumed to be valid according to earlier constraints. In the example controller method above, we can cast `body.email` and `body.password` to non-nullable `Strings` with `!!` because we've already checked them with `ShouldInclude`.

## Going Further

Naming constraints using `Rule` types allows you to represent the validation logic in a more declarative style. If you had a need for it you could create special combination rules like `AndRule` or `OrRule` that compose their constraints from other rules, and treat them specially in the `Validator`, so as to say something like:

```kotlin
Validator()
  .specifyEither(
    ShouldBeValidUserId(body.userId),
    ShouldBeValidEmailAddress(body.email)
  )
  ...
  .validate()
```
