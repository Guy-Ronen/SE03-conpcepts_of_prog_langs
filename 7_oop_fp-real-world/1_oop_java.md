# Real world example: Rest API in Java

link to prod: https://demo.codility.com/public-link/assessment_demo-rest_api_java_scala_demo/

### Requirements
You are required to write an API that will contain the following endpoint:

GET /users

* endpoint should return status code 200 on a successful request;

* endpoint should return the data taken from the mocked-up database using the provided helper repository's method `repository.findAll()`. 
    - This function returns an array of user objects containing `id` (Integer), `name` (String) and `role` (String).

* endpoint should accept a query parameter `name` which contains a string;

* when parameter `name` is provided, only users whose name property is equal to the `name` query parameter must be returned. 

* If no users with the given `name` are found, an empty array must be returned.

### Solution:
```java
package com.example.rest;

import com.example.dto.UserDto;
import com.example.repository.UserRepository;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

import static java.util.stream.Collectors.toList;

@RestController
@RequestMapping("users")
public class UserRestController {

    // Encapsulation: the instance variable is declared private to prevent direct access to it from other classes
    private final UserRepository repository;

    // Encapsulation: the constructor takes a UserRepository object as its argument and initializes an instance variable with it
    UserRestController(UserRepository repository) {
        this.repository = repository;
    }

    // Abstraction: the method provides an abstraction of a RESTful API endpoint for interacting with user data
    @GetMapping
    public ResponseEntity<List<UserDto>> create(@RequestParam(required = false) String name) {

        List<UserDto> users = getUsers(name);

        return ResponseEntity.ok(users);
    }

    // Abstraction: the method is a helper method that abstracts away the details of how the users are retrieved from the User Repository
    private List<UserDto> getUsers(String name) {

        List<UserDto> users = repository.findAll(); //

        if (name != null) {
            return users.stream()
                    .filter(user -> user.getName().equals(name)) // encapsulation: the user.getName() method is private. We cant access it directly.
                    .collect(toList());
        } else {
            return users;
        }
    }
}
```

### Explanation
Here's how the Java code is utilizing OOP principles:

1. Encapsulation: The `UserRestController` class and its methods are all declared public, allowing them to be accessed from other classes. 

The class has a constructor that takes a `UserRepository` object as its argument and initializes an instance variable with it. 

The instance variable is declared private to prevent direct access to it from other classes, encapsulating the internal state of the class.

2. Abstraction: The `UserRestController` class provides an abstraction of a RESTful API endpoint for interacting with user data. 

The `create()` method returns a `ResponseEntity` object containing a list of `UserDto` objects. The `getUsers()` method is a helper method that abstracts away the details of how the users are retrieved from the `UserRepository`.


### Advantages of OOP over FP
* OOP is a more natural way of thinking about the world. It's easier to understand and reason about than FP.

* OOP is more flexible than FP. It allows you to change the behavior of an object at runtime by changing its state, whereas FP requires you to create a new function for each behavior.

* OOP is more efficient than FP. It allows you to reuse code by creating classes that can be instantiated multiple times, whereas FP requires you to create a new function for each behavior.