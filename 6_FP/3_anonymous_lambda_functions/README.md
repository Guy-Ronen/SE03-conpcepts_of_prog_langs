# Anonymous Lambda Functions
Anonymous functions (also known as lambda functions) are functions that do not have a name and are defined inline within another expression. 

They are a common feature of many functional programming languages, and they are often used to express simple functions concisely.

Here's an example of an anonymous function in Python:

```python
result = (lambda x: x ** 2)(3)
print(result) # prints 9
```

In this example, we define an anonymous function using the lambda keyword. The function takes an argument x and returns the square of x. 
We then immediately call the function with an argument of 3, and store the result in the result variable.

Here's an example of an anonymous function in Scala:

```scala
val result = ((x: Int) => x * 2)(3)
println(result) // prints 6
```

In this example, we define an anonymous function using the => syntax. The function takes an argument x of type Int and returns the value of x multiplied by 2. We then immediately call the function with an argument of 3, and store the result in the result variable.

### The characteristics of anonymous functions are:

1. They are defined inline within another expression, such as a function call or another expression.
<br>

2. They do not have a name, and are instead assigned to a variable or passed directly as an argument to another function.
<br>

3. They are often used to express simple functions concisely, without the need for a full function definition.
<br>

4. They can capture variables from their enclosing scope, which allows them to be used as a powerful tool for creating closures.

### Anonymous functions are useful for:

1. `Passing as arguments to higher-order functions:` Anonymous functions can be passed directly as arguments to higher-order functions, such as map, filter, and reduce.

For example, suppose you have a list of numbers and you want to square each number in the list. You could use the map function to do this:

```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = map(lambda x: x ** 2, numbers)
print(list(squared_numbers)) # prints [1, 4, 9, 16, 25]
```
<br>

2. `Returning as the result of a function:` Anonymous functions can be returned directly as the result of a function, which allows you to create functions that generate other functions.

For example, suppose you want to create a function that returns a function that multiplies a number by a given factor. You could do this using an anonymous function:

```python
def create_multiplier(factor):
    return lambda x: x * factor

double = create_multiplier(2)
print(double(5)) # prints 10
```


### Real-world examples: 
One common use case for lambda functions is in sorting and filtering data in lists or other data structures. For example, suppose you have a list of dictionaries representing employees in a company, and you want to sort the list by the employee's last name:

```python
employees = [
    {'first': 'Alice', 'last': 'Smith'},
    {'first': 'Bob', 'last': 'Johnson'},
    {'first': 'Charlie', 'last': 'Brown'}
]

employees_sorted = sorted(employees, key=lambda e: e['last'])
print(employees_sorted) 
# prints [{'first': 'Charlie', 'last': 'Brown'}, {'first': 'Bob', 'last': 'Johnson'}, {'first': 'Alice', 'last': 'Smith'}]
```
