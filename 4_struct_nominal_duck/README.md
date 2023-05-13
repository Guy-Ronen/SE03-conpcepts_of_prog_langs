## Structural, Nominal and Duck Typing

### Structural typing

Structural typing is a type system used in some programming languages, where type compatibility is based on the structure of the types rather than their explicit declaration. In other words, if two types have the same structure, they are considered compatible, even if they have different names.

Several programming languages support structural typing, including:

- TypeScript
- Go
- OCaml

### Example 1 - Customer and Person work (TypeScript):

```typescript
class Person {
    name: string;
}

class Customer {
    name: string;
}

const customer: Customer = new Person(); // works
```


### Example 2 - Customer and Person dont work when adding fields to customer:

```typescript
class Person {
    name: string;
}


class Customer {
    name: string;
    age: number;
}

const customer: Customer = new Person(); // error
```



### Example 3 - Person works with Customer when adding fields to customer:

```typescript
class Person {
    name: string;
}

class Customer {
    name: string;
    age: number;
}

const person: Person = new Customer(); // works
const customer: Customer = new Person(); // error - Property 'age' is missing in type 'Person' but required in type 'Customer'.
```

### Real-life example - creating a user with ID and Email:

```typescript
type ID = string;
type Email = string;

type User = {
  id: ID;
  email: Email;
};


function createUser(id: ID, email: Email){
    const user: User = {
        id,
        email
    }
    return user;
}

const newID = "123";
const newEmail = "test@gmail.com";

const RegularUser = createUser(newID, newEmail); // works

const swappedUser = createUser(newEmail, newID); // works

```
In this example, we can see that the function `createUser` works with both `ID` and `Email` types, even though they are just aliases for `string` type.


## Nominal typing

Nominal typing is a type system used in programming languages, where type compatibility is based on the name or label of the type rather than its structure. 

In other words, two types are considered compatible only if they have the same name or label, even if their structures or contents are different.

In nominal typing, types are usually explicitly declared through class or struct definitions, and their names are used to determine their compatibility. 

For example, in Java, two objects are only considered to be of the same type if they are instances of the same class or interface, even if their instance variables have the same type and values.

Here are some programming languages that use nominal typing:

- Java
- C#
- Swift
- Kotlin
- Rust

#### Example 1 - Customer and Person dont work (Java):

```java
class Person {
    String name;
}

class Customer {
    String name;
}

Customer customer = new Person(); // error
```


#### Real-life example - creating a user with ID and Email (rust):

```rust
struct ID = String;
struct Email = String;

struct User {
    id: ID,
    email: Email
}

// function to create a user
fn create_user(id: ID, email: Email) -> User {
    User {
        id,
        email
    }
}

fn main() {
    let id = String::from("123");
    let email = String::from("test@gmail.com");

    let regular_user = create_user(id, email); // works
    let swapped_user = create_user(email, id); // error - expected struct `ID`, found struct `Email`

}
```



## Duck typing 

Duck typing is a concept in programming that is related to, but not identical to, structural typing. 
In duck typing, an object's suitability for a particular use is determined by whether it has the necessary methods and properties, rather than by its actual type.

Languages that support duck typing are for example:
- Python
- Ruby
- JavaScript

The name "duck typing" comes from the phrase `"If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck".`

In other words, if an object behaves like the required object, then it can be treated as if it were that object.

Here's an example in Python:

```python
class Dog:
    def speak(self):
        print("Woof!")

class Cat:
    def speak(self):
        print("Meow!")

class Human:
    def talk(self):
        print("Hello!")

def speak_now(animal):
    animal.speak()

dog = Dog()
cat = Cat()
human = Human()

speak_now(dog) # prints "Woof!"
speak_now(cat) # prints "Meow!"
speak_now(human) # Throws an AttributeError because `Human` does not have a `speak()` method
```

## What are the differences between structural typing and duck typing?

The differences between structural typing and duck typing are subtle, but important:

- Structural typing is a type system where type compatibility is based on the structure of the types rather than their explicit declaration. In other words, if two types have the same structure, they are considered compatible, even if they have different names.

- Duck typing is a concept in programming that is related to, but not identical to, structural typing. In duck typing, an object's suitability for a particular use is determined by whether it has the necessary methods and properties, rather than by its actual type.

For example, in Python, the `speak_now` function takes an object as an argument, and calls its `speak` method. If the object has a `speak` method, then it can be treated as if it were a `Dog` or a `Cat`, even if it is not actually an instance of either class.