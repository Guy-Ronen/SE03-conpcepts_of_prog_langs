# Encapsulation

The purpose of encapsulation is to create a protective barrier around the data, such that it can only be accessed and manipulated through the methods provided by the class.

In other words, encapsulation helps to enforce the idea of "data hiding", which means that the internal details of the class are hidden from the outside world, and can only be accessed through a well-defined interface of methods. 

This helps to prevent accidental modification of the data, and allows the class to maintain its internal consistency and validity.

# Example
In this example, we have a Car class that has three private fields: make, model, and year.

We also have three getter methods for each field, and three setter methods for each field.

The getter methods allow us to access the values of the fields. 

The setter methods allow us to change the values of the fields.

### 1. Car class with private fields
![1](1_car_class_with_private_fields.png)


### 2. Cannot print car make field
![2](2_cannot_print_car_make_field.png)

### 3. Creating getter methods for each field
![3](3_creating_getter_methods_for_each_field.png)

### 4. Printing make of car successful with getMake()
![4](4_printing_make_of_car_successful_with_getMake.png)

### 5. Cannot change the car year directly
![5](5_cannot_change_the_car_year_directly.png)

### 6. Creating setter method for each field
![6](6_creating_setter_method_for_each_field.png)

### 7. Calling all three setters in the constructor
![7](7_calling_all_three_setters_in_the_constructor.png)

### 8. Setting the year was successful
![8](8_setting_the_year_was_successful.png)

<strong>NOTE:</strong>
- In a real world use case, we would probably want to add some validation logic to the setter methods to ensure that the values being set are valid.

## Conclusion

In conclusion, encapsulation is a fundamental concept in object-oriented programming that refers to the practice of bundling data and methods that operate on that data into a class. 

The purpose of encapsulation is to create a protective barrier around the data, such that it can only be accessed and manipulated through the methods provided by the class.