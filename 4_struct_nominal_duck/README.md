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

### Example 2 - Customer and Person don't work when adding fields to customer:

```typescript
class Person {
  name: string;
}

class Customer {
  name: string;
  age: number;
}

const customer: Customer = new Person(); // error - Property 'age' is missing in type 'Person' but required in type 'Customer'.
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

person.name = "John"; // works
person.age = 30; // works

console.log(person); // Person { name: 'John', age: 30 }

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

function createUser(id: ID, email: Email) {
  const user: User = {
    id,
    email,
  };
  return user;
}

const newID = "123";
const newEmail = "test@gmail.com";

const regularUser = createUser(newID, newEmail); // works
console.log(regularUser); // { id: '123', email: 'test@gmail' }

const swappedUser = createUser(newEmail, newID); // works
console.log(swappedUser); // { id: 'test@gmail', email: '123' }
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

Customer customer = new Person(); // error - incompatible types: Person cannot be converted to Customer
```

#### Real-life example - creating a user with ID and Email (Rust):

```rust

// define ID and Email structs
struct ID {
    id: String,
}

struct Email {
    email: String,
}

// define User struct that uses ID and Email structs as fields 
struct User<'a> {
    id: &'a ID,
    email: &'a Email,
}

// define a function that creates a new user with ID and Email structs as parameters 
fn create_user<'a>(id: &'a ID, email: &'a Email) -> User<'a> {
    User { id, email }
}

fn main() {
    let new_id = ID {
        id: String::from("123"),
    };

    let new_email = Email {
        email: String::from("test@gmail.com"),
    };

    create_user(&new_id, &new_email); // works

    create_user(&new_email, &new_id); // error - expected struct `ID`, found struct `Email`
}
```

## Duck typing

Duck typing is a concept in programming that is related to, but not identical to structural typing.

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

- Structural typing is a static type system based on the structure of types, while duck typing is a dynamic typing concept based on behavior.

- Structural typing relies on type compatibility through the structure of types, while duck typing focuses on the presence of required behavior.

- Structural typing is enforced at compile-time, while duck typing is typically enforced at runtime.

- Structural typing is more common in statically-typed languages, while duck typing is more common in dynamically-typed languages.


Here is an example of how two classes cannot be structurally compatible, but can be duck-typed:

```python 

# Here is a human class with lots of methods 

class Human:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def speak(self):
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")
    

    def walk(self):
        print("I am walking.")
    
    def eat(self):
        print("I am eating.")
    
    def sleep(self):
        print("I am sleeping.")


# Here is a duck class with only two methods

class Duck:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        print(f"Quack, my name is {self.name}.")
    
    def quack(self):
        print("Quack, quack!")

def speak_now(animal):
    animal.speak()


human = Human("John", 30)
duck = Duck("Daffy")

speak_now(human) # My name is John and I am 30 years old.

speak_now(duck) # Quack, my name is Daffy.
```

As you can see, Human and Duck are NOT compatible types, because they have different structures, however they are both compatible with the speak_now function, because they both have a speak method (duck typing)