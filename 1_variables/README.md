# Variables

In programming, a variable is a named storage location in the computer's memory that can hold a value, such as a number, a character, or a reference to an object. It's like a container that can store different values at different times.

Variables are used to store data and perform operations on that data within a program. They allow programmers to reference and manipulate data as it changes over time, and to reuse the same data in multiple places within a program.


### Mutables variables in typescript

```typescript
function main() {
    const immutabeVariable = "Hello World";
    console.log(immutabeVariable);


    let mutableVariable = "Hello mutable World";
    console.log(mutableVariable);

    mutableMessage = "this message has been changed";
    console.log(mutableMessage); // this message has been changed

    immutableMessage = "this message has been changed"; // error
}
```



### Imutables variables in rust

```rust
fn main() {
    let immutable_variable &str = "Hello World";
    println!("{}", immutable_variable); // Hello World

    let mut mutable_variable &str = "Hello mutable World";
    println!("{}", mutable_variable); // Hello mutable World

    mutable_variable = "this message has been changed";
    println!("{}", mutable_variable); // this message has been changed

    immutable_variable = "this message has been changed"; // error
}


