## Requirements

You are required to write an API endpoint that will contain the following things:

GET /users

- The endpoint should return the 200 status code on a successful request.

- The endpoint should return data taken from a mocked-up database using the provided helper method getUsers which takes no arguments and returns a list of User objects.

- The definition of User (provided under com.example.Domain.User) is as follows:

```scala
final case class User(id: Int, name: String, role: String)
```

- The endpoint should accept an optional query parameter called name which will contain a string.

- When the name is provided, all users whose name property is equal to the name query parameter must be returned.

- If no users with the given name are found, an empty list must be returned.
  When the query parameter is not provided, all users must be returned.

### Code

```scala
package com.example

import akka.http.scaladsl.marshallers.sprayjson.SprayJsonSupport
import akka.http.scaladsl.server.Directives.{complete, _}
import akka.http.scaladsl.server.Route
import spray.json.{DefaultJsonProtocol, RootJsonFormat}
import com.example.Domain.User
import com.example.Database.getUsers
import scala.util.chaining.scalaUtilChainingOps

object RestApi extends DefaultJsonProtocol with SprayJsonSupport {

  // Define a JSON format for the User case class
  implicit val userJsonFormat: RootJsonFormat[User] = jsonFormat3(User)

  // Define a route for the "/users" endpoint that accepts GET requests
  val route: Route = (path("users") & get) {
    parameter("name".optional)
    (_.map(name => getUsers.filter(user => user.name == name)) // filter the list of users by name using a lambda expression

    // if no "name" parameter is present, return the entire list of users
    .getOrElse(getUsers)
    // pipe the resulting list of users into the `complete` directive to construct the HTTP response
    .pipe(complete(_))
    )
    }
}
```

### The code uses the following principles:

1. Immutability: the `User` case class is immutable and its fields cannot be changed once created.

2. Higher-order functions: `complete() `and `pipe()` are both higher-order functions. `complete()` takes a response entity as input and returns a Route.
   `pipe()` takes a value as input and applies a function to it, returning the result.

3. Pure functions: `getUsers` is a pure function that takes no inputs and returns a list of User instances. It does not modify any state outside of its own scope.

4. Functional composition: the `getOrElse()` method and `pipe()` function are composed together to handle the case where a parameter is not provided. If a name parameter is present, `filter()` is called to return a list of users with a matching name. Otherwise, getUsers is called to return all users.

5. Function chaining: the `getOrElse()` method and `pipe()` function are chained together to create a concise one-liner that retrieves the correct list of users and completes the HTTP response with that list.

6. Lambda expressions: the `filter()` method is called with a lambda expression that filters the list of users by name.

### Advantages of FP over OOP

1. FP is easier to reason about: FP is based on the concept of pure functions, which are deterministic and predictable. Pure functions don't have side effects, so they can be reasoned about in isolation. This makes it easier to understand and debug code.

2. FP is easier to test: Pure functions are easier to test because they don't have side effects. This makes it easier to write unit tests for pure functions.

### When code can't be purely functional?

In some cases, it's not possible to write purely functional code. For example:

1. `Input/output:` When an application needs to read or write data to a file or a database, this is considered a side effect and is not a pure function. While it's possible to abstract away the side effect using monads or other functional constructs, the underlying operation is still impure.

2. `User interfaces:` Interacting with a user interface, such as a web page or a mobile app, is inherently stateful and can't be modeled purely with functions. User input can't be predicted, so it's impossible to write a pure function that takes a user's input and produces a predictable output.

3. `Concurrency:` Managing concurrency and parallelism can be challenging in functional programming, especially when working with mutable data structures. Locks and other concurrency constructs introduce side effects and can make code impure.
