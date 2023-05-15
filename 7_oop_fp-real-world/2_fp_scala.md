# Real world example: Rest API in Scala

link to prod: https://demo.codility.com/public-link/assessment_demo-rest_api_java_scala_demo/

## Requirements

You are required to write an API endpoint that will contain the following things:

`GET /users`

- The endpoint should return the 200 status code on a successful request.

- The endpoint should return data taken from a mocked-up database using the provided helper method getUsers which takes no arguments and returns a list of User objects.

- The definition of User is as follows:

```scala
User(id: Int, name: String, role: String)
```

- The endpoint should accept an optional query parameter called name which will contain a string.

- When the name is provided, all users whose name property is equal to the name query parameter must be returned.

- If no users with the given name are found, an empty list must be returned.
  When the query parameter is not provided, all users must be returned.

### Code

```scala
object RestApi extends DefaultJsonProtocol with SprayJsonSupport {

  implicit val userJsonFormat: RootJsonFormat[User] = jsonFormat3(User)

  val route: Route = (path("users") & get) {
    parameter("name".optional)
    (_.map(name => getUsers // getUsers is a pure helper method that returns a list of User objects and map is a higher-order function
    .filter(name => _.name == name)) // filter the list of users by name (lambda expression)
    .getOrElse(getUsers) // if no name is provided, return all users (function composition)
    .pipe(complete(_)) // complete the request with the list of users
    )
  }
}
```

### The code uses the following principles:

1. `Immutability:` the `User` case class is immutable and its fields cannot be changed once created.
   <br>

2. `Higher-order functions:` `complete() `and `pipe()` are both higher-order functions. They take other functions as input and return a function as output.
   In this case:

   - `complete()` takes a response entity as input and returns a Route.

   - `pipe()` takes a value as input and applies a function to it, returning the result.

   - `map()` takes the list of users as input and applies a function to it, returning the result.
     <br>

3. `Pure functions:` `getUsers()` is a pure function that takes no inputs and returns a list of `User` instances.
   It does not modify any state outside of its own scope.
   <br>

4. `Functional composition: `the `map()` method is used to compose the `getOrElse()` method and the `filter()` method.
<br>

5. `Function chaining:` the `getOrElse()` method and `pipe()` function are chained together to create a concise one-liner that retrieves the correct list of users and completes the HTTP response with that list.
   <br>

6. `Lambda expressions:` the `filter()` method is called with a lambda expression that filters the list of users by name.

### Advantages of FP over OOP

1. `FP is easier to reason about:` FP is based on the concept of pure functions, which are deterministic and predictable. Pure functions don't have side effects, so they can be reasoned about in isolation. This makes it easier to understand and debug code.
   <br>
2. `FP is easier to test:` Pure functions are easier to test because they don't have side effects. This makes it easier to write unit tests for pure functions.

### When code can't be purely functional?

In some cases, it's not possible to write purely functional code. For example:

1. `Input/output:` When an application needs to read or write data to a file or a database, this is considered a side effect and is not a pure function.
   <br>

2. `User interfaces:` Interacting with a user interface, such as a web page or a mobile app, is inherently stateful and can't be modeled purely with functions. In the code above, the `complete()` directive is not pure because it produces a side effect by sending an HTTP response to the client.
  <br>

3. `Time-dependent operations:` Functions that rely on the current time or perform time-related calculations, such as scheduling tasks, timeouts, or handling time-based events, are impure because their behavior can vary depending on when they are called.
   <br>

4. `Randomness:` Functions that generate random numbers or make use of random sources are impure since the output is non-deterministic and can vary across different invocations.
   <br>

5. `External services and resources (API's):` Functions that interact with external services, such as sending emails, accessing hardware devices, or integrating with third-party APIs, typically involve side effects and impurity.
