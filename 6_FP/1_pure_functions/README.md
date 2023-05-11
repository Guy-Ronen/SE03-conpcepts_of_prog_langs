# Pure funcitons
The concept of pure functions is a fundamental principle in functional programming. A pure function is a function that always returns the same output for a given input and does not have any side effects. This means that a pure function does not modify any data outside of its local scope, and it does not rely on any external state or mutable variables. Because of these properties, pure functions are predictable, testable, and composable.

## Some of the characteristics of pure functions are:
1. `Deterministic:` A pure function always returns the same output for a given set of inputs, regardless of the context in which it is called. This makes the function predictable and easy to reason about.

2. `No side effects:` A pure function does not modify any data outside of its local scope, and it does not rely on any external state or mutable variables. This means that it does not have any side effects, such as modifying global variables or performing input/output operations.

3. `Referentially transparent:` A pure function is referentially transparent, which means that it can be replaced with its return value without affecting the behavior of the program. This property makes it easier to reason about the behavior of the program and to compose functions together.

4. `Idempotent:` A pure function is idempotent, which means that calling it multiple times with the same input values will always produce the same output value. This makes it safe to call the function multiple times without worrying about unintended side effects.

5. `Testable:` Because a pure function always returns the same output for a given set of inputs, it is easy to write tests for it. You can simply call the function with different input values and compare the output to the expected value.


Here is an example of a pure function that takes two numbers as input and returns their sum:

```scala
def add(x: Int, y: Int): Int = x + y

add(1, 2) // 3

```

In here we can see that the function always returns the same output for a given set of inputs, and it does not modify any data outside of its local scope. 

Therefore, it is a pure function.

## Real world example- Email validator

```scala
def isValidEmail(email: String): Boolean = {
  val emailRegex = "^[\\w\\.-]+@([\\w\\-]+\\.)+[A-Z]{2,4}$".r
  email match {
    case emailRegex(_*) => true
    case _ => false
  }
}


val shouldBeAValidEmail = isValidEmail("guy@gmail.com") // true

val shouldBeAValidEmailAgain = isValidEmail("guy@gmail.com") // true

val invalidEmail = isValidEmail("guy") // false
```