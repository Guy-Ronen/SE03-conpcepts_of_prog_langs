# Functional Composition

Functional composition is the process of combining two or more functions to produce a new function. 

For example, the following code snippet shows how to compose two functions in Scala:

```scala
val f: Int => Int = x => x + 1
val g: Int => Int = x => x * 2
val h: Int => Int = f andThen g
```

In this example, the `f` function adds 1 to its input, and the `g` function multiplies its input by 2. 

The `h` function is the composition of `f` and `g`, which means that it first applies `f` to its input and then applies `g` to the result of `f`. 

In this case, `h` adds 1 to its input and then multiplies the result by 2.

## Functional composition in Scala

Scala provides several ways to compose functions:

- `andThen()` is a method on the `Function1` trait that takes a function as input and returns a new function as output. The new function is the composition of the original function and the function passed to `andThen()`. 

For example:

  ```scala
  val f: Int => Int = x => x + 1
  val g: Int => Int = x => x * 2
  val h: Int => Int = f andThen g

  val x = 5
  println(h(x)) // prints 12 because h(x) = g(f(x)) = g(6) = 12
  ```
  
  In this example, `h` is the composition of `f` and `g`. It first applies `f` to its input and then applies `g` to the result of `f`.
<br>

- `compose()` is a method on the `Function1` trait that takes a function as input and returns a new function as output. The new function is the composition of the function passed to `compose()` and the original function. 

For example:

```scala

val f: Int => Int = x => x + 1
val g: Int => Int = x => x * 2
val h: Int => Int = f compose g // h(x) = f(g(x)) = f(10) = 11

val x = 5
println(h(x)) // prints 11 because h(x) = f(g(x)) = f(10) = 11
```
<br>

- `getOrElse()` is a method on the `Option` trait that takes a function as input and returns a value. If the `Option` is `Some`, then `getOrElse()` returns the value inside the `Some`. If the `Option` is `None`, then `getOrElse()` returns the result of applying the function to `None`. 

For example:

```scala
  val x: Option[Int] = Some(5) // Some is a subclass of Option that contains a value of type Int 
  val y: Option[Int] = None // None is a subclass of Option that contains no value

  val z = x.getOrElse(0) // z = 5
  val w = y.getOrElse(0) // w = 0
```

In this example, `x` is `Some(5)`, so `getOrElse()` returns `5`. 

And in the other case, `y` is `None`, so `getOrElse()` returns `0`.

