# Polymorphism
Polymorphism is a programming concept that allows objects of different types to be treated as if they are of the same type, based on a shared interface or inheritance relationship. In other words, it allows objects to take on many different forms or shapes.

## Example

### 1. Animal class with eat method
![1](1_animal_calls_eat_in_main_function.png)

### 2. Animal class
![2](2_animal_class.png)

### 3. Dog class
![3](3_dog_class.png)

### 4. Dog class extends Animal and overrides eat method
![4](4_dog_class_overrides_eat_method.png)

### 5. Cat class extends Animal and overrides eat method
![5](5_cat_class_extends_animal_and_overrides_eat_method.png)

### 6. Main method calls eat method of all three classes
![6](6_main_method_calls_eat_method_of_all_three_classes.png)


### 7. Three different outputs get printed
![7](7_three_different_outputs_get_printed.png)

### 8. Dog has two eat methods (method overloading)
![8](8_dog_has_two_eat_methods-method_over_loading.png)


In this example, we have an Animal class with an eat method. We then have two subclasses of Animal: Dog and Cat. Both of these classes override the eat method to do something different. Finally, we have a main method that calls the eat method on all three classes. The output shows that each class has its own implementation of the eat method.



### Conclusion
In summary, polymorphism is a programming concept that allows objects of different types to be treated as if they are of the same type, based on a shared interface or inheritance relationship. It allows objects to take on many different forms or shapes. In Java, polymorphism is achieved through method overriding and method overloading.
