# Java OOP Fundamentals – Detailed Lecture Notes

## Real-World Analogy: Grouping Things into Objects
In our daily life, we group related information and actions into single units called objects.
For example, a Car is not thought of as 'four wheels', 'an engine', and 'a steering wheel' separately.
Instead, it is an object with attributes (color, speed) and behaviors (drive, brake, accelerate).
Programming uses the same idea: grouping data and methods into an object makes programs easier to design and understand.

## Why Use OOP?
Object-Oriented Programming (OOP) helps solve common programming problems by organizing code into objects.
Benefits include:
- Organization: Code for each concept is grouped together.
- Reusability: Classes can be reused to create multiple objects without rewriting code.
- Maintainability: Changes can be made in one place instead of multiple scattered locations.
- Encapsulation: Hides the internal details and protects data.
- Abstraction: Lets you focus on what an object does rather than how it works internally.

## Key Terms
- Class: A blueprint or template for creating objects, defining fields and methods.
- Object: An instance of a class; a specific realization of the blueprint.
- Field (Attribute): Variables inside a class that store data for the object.
- Method: Functions inside a class that define the behavior of objects.
- Access Modifier: Determines who can access fields/methods (public, private, protected).

## Car Class Example
Example of a simple class in Java:
```java
public class Car {
    String color;
    int speed;
    void drive() {
        System.out.println("Driving...");
    }
}
```
Here, 'color' and 'speed' are fields, and 'drive()' is a method.

## Creating and Using an Object
Steps to create and use a Car object:
```java
Car myCar = new Car();  // Create object
myCar.color = "Red";    // Set field value
myCar.speed = 50;       // Set another field
myCar.drive();          // Call method
```
This shows how to create an object, assign data, and call its methods.

## Example 1 to Run

```java
// Car.java
public class Car {
    // Fields (data)
    String color;
    int speed;

    // Method (behavior)
    void drive() {
        System.out.println(color + " car is driving at " + speed + " km/h.");
    }
}
```

```java
public class CarDemo {
    public static void main(String[] args) {
        // Step 1: Create an object of Car
        Car myCar = new Car();

        // Step 2: Set field values
        myCar.color = "Red";
        myCar.speed = 50;

        // Step 3: Call method
        myCar.drive();
    }
}
```

### Sample Output
```
Red car is driving at 50 km/h.
```

## Example 2 to Run

```java
// Restaurant.java
public class Restaurant {
    // Private fields (data)
    private String name;
    private String location;
    private int seatingCapacity;

    // Public method to set restaurant details
    public void setDetails(String n, String loc, int capacity) {
        name = n;
        location = loc;
        seatingCapacity = capacity;
    }

    // Public method to open the restaurant
    public void openRestaurant() {
        System.out.println(name + " at " + location + " is now open!");
    }

    // Public method to display details
    public void displayInfo() {
        System.out.println("Restaurant Name: " + name);
        System.out.println("Location: " + location);
        System.out.println("Seating Capacity: " + seatingCapacity);
    }
}
```
```java
// RestaurantDemo.java
public class RestaurantDemo {
    public static void main(String[] args) {
        // Step 1: Create a Restaurant object
        Restaurant myRestaurant = new Restaurant();

        // Step 2: Set the restaurant details
        myRestaurant.setDetails("Ocean View", "San Diego", 80);

        // Step 3: Call methods
        myRestaurant.openRestaurant();
        myRestaurant.displayInfo();
    }
}
```
### Sample Output
```
Ocean View at San Diego is now open!
Restaurant Name: Ocean View
Location: San Diego
Seating Capacity: 80

```

## Constructors – Initializing Objects
A constructor is a special method that runs when a new object is created.
It has the same name as the class, has no return type, and is used to initialize fields.
Example:
```java
public class Car {
    String color;
    int speed;
    public Car(String c, int s) {
        color = c;
        speed = s;
    }
}
Car myCar = new Car("Red", 50);
```

## Encapsulation – Protecting Data
Encapsulation hides the internal state of an object and controls how data is accessed or modified.
Fields are marked private, and public getter and setter methods are provided for access.
Example:
```java
private String color;
public void setColor(String c) { color = c; }
public String getColor() { return color; }
```

## Mutators and Accessors
- Mutator (setter): Changes a field value, often with validation.
- Accessor (getter): Retrieves a field value.
Example with validation:
```java
public void setSpeed(int s) {
    if (s >= 0) {
        speed = s;
    }
}
public int getSpeed() {
    return speed;
}
```

## Full Car Class Example
Full example combining all concepts:
```java
public class Car {
    private String color;
    private int speed;

    public Car(String c, int s) {
        color = c;
        speed = s;
    }

    public void drive() {
        System.out.println(color + " car is driving at " + speed + " km/h");
    }

    public void accelerate(int increment) {
        speed += increment;
        System.out.println("Accelerated to " + speed + " km/h");
    }

    public void brake(int decrement) {
        speed -= decrement;
        if (speed < 0) speed = 0;
        System.out.println("Slowed down to " + speed + " km/h");
    }

    public String getColor() { return color; }
    public void setColor(String c) { color = c; }
}
```

## Using the Car Class
Example usage:
```java
Car myCar = new Car("Red", 50);
myCar.drive();
myCar.accelerate(20);
myCar.brake(10);
```

## Summary
- Class = blueprint, Object = instance.
- Fields store data, Methods define actions.
- Constructors initialize objects.
- Encapsulation protects and controls access to data.

