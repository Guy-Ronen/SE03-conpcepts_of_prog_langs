Inheritance is a key concept in object-oriented programming that allows a new class to be based on an existing class, inheriting its properties and methods. This can help to reduce code duplication and increase code reuse, by allowing similar classes to share a common base implementation.

There are several types of inheritance, including single inheritance, multiple inheritance, and interface-based inheritance. Let's take a look at each of these in turn, with some examples in Java.

## Single Inheritance
Single inheritance is the most basic type of inheritance, where a new class is derived from a single existing class. The new class inherits all the properties and methods of the existing class, and can also add new properties and methods of its own.

```java

// Define a class 'Vehicle'
class Vehicle {
  public void drive() {
    System.out.println("Driving a vehicle");
  }
}
// Define a class 'Car' that inherits from 'Vehicle'

class Car extends Vehicle {
  public void accelerate() {
    System.out.println("Accelerating a car");
  }
}

public class Main {
  public static void main(String[] args) {
    Car car = new Car();
    car.drive(); // Driving a vehicle
    car.accelerate(); // Accelerating a car
  }
}
```
In this example, we have a Vehicle class with a drive() method, and a Car class that inherits from Vehicle and adds a new accelerate() method. When we create a new Car object and call its methods, we can see that it can both drive and accelerate, because it inherits from Vehicle.

## Multiple Inheritance

Multiple inheritance allows a new class to inherit from multiple existing classes, combining their properties and methods into a single class. This can be useful when we want to create a new class that has features from multiple existing classes.

```python

# Define a class 'Vehicle'
class Vehicle:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def drive(self):
        print(f"{self.make} {self.model} is being driven.")



# Define another class 'Radio'
class Radio:
    def __init__(self, station):
        self.station = station

    def play(self):
        print(f"Playing {self.station} radio station.")


# Define a class 'Car' that inherits from both 'Vehicle' and 'Radio'
class Car(Vehicle, Radio):
    def __init__(self, make, model, station):
        super().__init__(make, model)
        super(Radio, self).__init__(station)

my_car = Car("Toyota", "Camry", "102.5")

my_car.drive() # Toyota Camry is being driven.
my_car.play() # Playing 102.5 radio station.
```

One thing to consider is that multiple inheritance can cause problems with conflicts or ambiguities when different classes define conflicting properties or methods. To avoid these issues, many programming languages (including Java) do not support multiple inheritance.


## Interface-based Inheritance
Interface-based inheritance is a way to define a set of methods that a class must implement, without specifying any implementation details. This can be useful when we want to ensure that different classes have the same basic functionality, but with different implementation details.

```java
// Define an interface 'Drawable'
interface Drawable {
    void draw();
}

// Define a class 'Circle' that implements 'Drawable'
class Circle implements Drawable {
    public void draw() {
        System.out.println("Drawing a circle.");
    }
}

// Define a class 'Rectangle' that implements 'Drawable'
class Rectangle implements Drawable {
    public void draw() {
        System.out.println("Drawing a rectangle.");
    }
}

// Define a class 'Shape' that accepts objects that implement 'Drawable'
class Shape {
    private Drawable drawable;

    public Shape(Drawable drawable) {
        this.drawable = drawable;
    }

    public void draw() {
        drawable.draw();
    }
}

// Create instances of the 'Circle' and 'Rectangle' classes
Circle myCircle = new Circle();
Rectangle myRectangle = new Rectangle();

// Create an instance of the 'Shape' class using the 'Circle' object
Shape shapeFromCircle= new Shape(myCircle);

// Create an instance of the 'Shape' class using the 'Rectangle' object
Shape shapeFromRectangle = new Shape(myRectangle);

// Call the 'draw()' method on the 'Shape' objects
shapeFromCircle.draw(); // Drawing a circle.
shapeFromRectangle.draw(); // Drawing a rectangle.

```