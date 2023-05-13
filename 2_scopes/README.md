In programming, a scope is a region of the code where a variable, function, or other identifier is defined and can be accessed. Scopes determine where in a program an identifier can be used, and also affect the visibility and lifetime of the identifier.

There are two main types of scopes in programming: local scope and global scope.

Local scope refers to variables, functions, and other identifiers that are defined within a specific block of code, such as a function or loop. These identifiers can only be accessed within the block where they are defined. 



### Local scope in python

```python
def my_function():
    local_variable = "local_variable"
    print(F"{local_variable} is a local variable")

my_function() # local_variable is a local variable
print(local_variable) # error
```





### Global scope in python

```python
global_variable = "global_varible"
def my_function():
    print(f"{global_variable} is a Global variable")

my_function() # global_varible is a Global variable
print(global_variable) # global_varible
```



