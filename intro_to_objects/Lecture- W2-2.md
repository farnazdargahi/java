# Objects, References, and Related Concepts

## 1. Objects and References
- A reference in Java is a variable that stores the *address* of an object in memory.
- Declaring a reference variable (e.g., `Car myCar;`) does not create the object, it just reserves a spot to hold a reference.
- To create an actual object, use the `new` operator:
  ```java
  Car myCar = new Car();
  ```
  This statement:
  - Allocates memory for a Car object.
  - Returns the address of that memory.
  - Stores that address in `myCar`.

 Common mistake: Trying to use a reference variable before assigning it to an object.

### Example
```java
public class TimeHrMin {
    int hours;
    int minutes;

    public void displayTime() {
        System.out.println(hours + " hours " + minutes + " minutes");
    }
}

public class TimeDemo {
    public static void main(String[] args) {
        // Step 1: Declare reference
        TimeHrMin travelTime;

        // Step 2: Create object
        travelTime = new TimeHrMin();

        // Step 3: Assign values and use
        travelTime.hours = 2;
        travelTime.minutes = 30;
        travelTime.displayTime();
    }
}
```
**Output:**
```
2 hours 30 minutes
```

### Class Activity – Objects and References

1. Create a class `Book` with fields:
   - `String title`
   - `String author`
2. Add a method `printDetails()` that prints the title and author.
3. In the main method:
   - Declare a `Book` reference variable without creating the object.
   - Try calling `printDetails()` before assigning an object (observe the error).
   - Create the object using `new` and then call `printDetails()`.

3. Add another `Book` object and assign it the same reference as the first. Change one’s title and see the effect on both.

---

## 2. The `this` Keyword
In Java, this is a special keyword that refers to the current object — the object whose method or constructor is currently being executed.
Think of it as saying: "Me, the current object."

 **Why do we use `this`?**

`this` is useful in three main cases:



### a) Differentiating between fields and parameters with the same name
When a method parameter has the same name as an instance field, `this` helps you refer to the field rather than the parameter.

**Example:**
```java
public class Rectangle {
    private double length;

    public void setLength(double length) {
        this.length = length; // field = parameter
    }
}
```
Without `this`, `length = length;` would just assign the parameter to itself.



### b) Calling another constructor in the same class (Constructor Chaining)
You can use `this(...)` inside a constructor to call another constructor in the same class.

**Example:**
```java
public class Book {
    String title;
    double price;

    public Book(String title) {
        this(title, 0.0); // Calls the second constructor
    }

    public Book(String title, double price) {
        this.title = title;
        this.price = price;
    }
}
``


## Example

```java
class ShapeSquare {
    private double sideLength;

    public void setSideLength(double sideLength) {
        this.sideLength = sideLength; // field = parameter
    }

    public double getArea() {
        return this.sideLength * this.sideLength;
    }
}

public class Test {
    public static void main(String[] args) {
        ShapeSquare square = new ShapeSquare();
        square.setSideLength(4.0);
        System.out.println("Area: " + square.getArea());
    }
}
```

**Output:**
```
Area: 16.0
```


### Class Activity – Using `this`
1. Create a `Student` class with:
   - Private field: `String name`
   - Method `setName(String name)` that uses `this` to assign the parameter to the field.
   - Method `printName()` to print the name.
2. In `main`:
   - Create a `Student` object.
   - Set the name using `setName()`.
   - Print the name.
3.Bonus:  
Add another constructor that takes `name` as a parameter and calls `this(name)` from the no-argument constructor.

---

## 3. Primitive Types vs Reference Types & Wrapper Classes

**Primitive type**: Directly stores the actual value.
Examples: 
  - int num = 5; → stores the number 5 directly.
  - double pi = 3.14; → stores 3.14 directly.

**Reference type**: Stores a memory address that points to an object in memory.
Examples:
  - String name = "John"; → stores a reference to a String object.
  - Car myCar = new Car(); → stores a reference to a Car object.

**Wrapper classes**: Special classes in Java that "wrap" primitive types into objects.
They allow primitive data to be used as objects and provide useful methods.

**Common wrapper classes:**

| Primitive | Wrapper    |
|-----------|-----------|
| int       | Integer   |
| double    | Double    |
| char      | Character |
| boolean   | Boolean   |

Many of Java's built-in classes, such as Java's Collection library, only work with objects. For example, a programmer can create an ArrayList containing Integer elements, e.g., ArrayList\<Integer\> frameScores; but not an ArrayList of int elements. Wrapper classes allow the program to create objects that store a single primitive type value, such as an integer or floating-point value. The wrapper classes also provide methods for converting between primitive types (e.g., int to double), between number systems (e.g., decimal to binary), and between a primitive type and a String representation. 

### Example
```java
import java.util.ArrayList;

public class StudentGrades {
    public static void main(String[] args) {
        // Store test scores for a student (ArrayList requires objects, so we use Double)
        ArrayList<Double> grades = new ArrayList<>();

        // Add grades
        grades.add(Double.valueOf(88.5));
        grades.add(Double.valueOf(92.0));
        grades.add(Double.valueOf(76.5));

        // Calculate average
        double total = 0;
        for (Double grade : grades) {
            total += grade.doubleValue();
        }
        double average = total / grades.size();

        // Display results
        System.out.println("Student Grades: " + grades);
        System.out.println("Average Grade: " + average);

        // Convert average to String for storing in a database
        String avgAsString = Double.toString(average);
        System.out.println("Average as String: " + avgAsString);

        // Check if the student passed (using a wrapper method)
        boolean passed = average >= 60.0;
        System.out.println("Passed: " + Boolean.toString(passed));
    }
}

```
**Output:**
```
Student Grades: [88.5, 92.0, 76.5]
Average Grade: 85.66666666666667
Average as String: 85.66666666666667
Passed: true

```

### Class Activity – Wrapper Classes
You are creating a simple inventory tracking tool for a store.
1- Create a program that:
Uses Integer to store a product’s stock quantity.
Uses Double to store the product’s price.
Uses Boolean to indicate if the product is on sale.

2- Print the stored values.
3- Use wrapper class methods to:
  - Use Integer.compare() to compare stock quantities of two products.
  - Use Double.sum() to add prices of two products.
  - Use Boolean.logicalAnd() to check if both products are on sale.

4- Display the results.

---

## 4. ArrayList in Java
In Java, sometimes we need a list of items whose size can grow or shrink at runtime — like a grocery list, course roster, or playlist.
Java provides the ArrayList class in the java.util package for this purpose.

-  An ArrayList is an ordered list of reference type elements.
-  It automatically resizes as elements are added or removed.
-  Each item in an ArrayList is called an element.
Before using ArrayList, we should import it:
```java
import java.util.ArrayList;
```

How to Declare and Create an ArrayList:
```java
ArrayList<Integer> vals = new ArrayList<Integer>();
```
Here:
- `vals` → reference variable that refers to an ArrayList of Integer objects.
- ArrayList does not store primitive types (like `int`, `double`) — it stores objects (use wrapper classes like `Integer`, `Double`).

A common beginner mistake:
```java
ArrayList<int> nums; //  ERROR: int is primitive
```

Common ArrayList Methods

| Method                | Description                               |
|-----------------------|-------------------------------------------|
| `.add(element)`       | Adds an element to the end                |
| `.get(index)`         | Returns the element at a given position   |
| `.set(index, element)`| Replaces element at given position        |
| `.remove(index)`      | Removes element at given position         |
| `.size()`             | Returns number of elements                |
| `.clear()`            | Removes all elements                      |
| `.contains(element)`  | Checks if element exists                  |

### Example – Basic ArrayList Operations
```java
import java.util.ArrayList;

public class GroceryList {
    public static void main(String[] args) {
        ArrayList<String> items = new ArrayList<String>();

        // Add elements
        items.add("Milk");
        items.add("Bread");
        items.add("Eggs");

        // Access element
        System.out.println("First item: " + items.get(0));

        // Replace element
        items.set(1, "Whole Grain Bread");

        // Remove element
        items.remove(0);

        // Display all items
        System.out.println("Grocery List: " + items);

        // Size
        System.out.println("Total items: " + items.size());
    }
}
```
**Output:**
```
First item: Milk
Grocery List: [Whole Grain Bread, Eggs]
Total items: 2
```

### Example: Finding the Nth most popular operating system.
```java
import java.util.ArrayList;
import java.util.Scanner;

public class OperatingSystems {
    public static void main(String[] args) {
        ArrayList<String> osList = new ArrayList<String>();
        osList.add("Windows");
        osList.add("macOS");
        osList.add("Linux");
        osList.add("Android");

        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a rank (1-4): ");
        int rank = sc.nextInt();

        System.out.println("The #" + rank + " OS is: " + osList.get(rank - 1));
    }
}
```

to Iterating Through ArrayLists we often use loops with ArrayLists.
```java
import java.util.ArrayList;

public class NumbersAverage {
    public static void main(String[] args) {
        ArrayList<Double> numbers = new ArrayList<Double>();
        numbers.add(4.5);
        numbers.add(3.2);
        numbers.add(5.8);

        double sum = 0.0;
        for (int i = 0; i < numbers.size(); i++) {
            sum += numbers.get(i);
        }

        double average = sum / numbers.size();
        System.out.println("Average: " + average);
    }
}
```

### Example
```java
import java.util.ArrayList;

class Review {
    String reviewer;
    int rating;

    Review(String reviewer, int rating) {
        this.reviewer = reviewer;
        this.rating = rating;
    }

    public String toString() {
        return reviewer + " rated: " + rating + "/5";
    }
}

public class ReviewList {
    public static void main(String[] args) {
        ArrayList<Review> reviews = new ArrayList<Review>();

        reviews.add(new Review("Alice", 5));
        reviews.add(new Review("Bob", 4));

        for (Review r : reviews) {
            System.out.println(r);
        }
    }
}
```
**Output:**
```
Alice rated: 5/5
Bob rated: 4/5
```

### In-Class Activity – Managing a To-Do List

1. Create an `ArrayList<String>` called `tasks`.
2. Add at least five tasks (strings) to the list.
3. Print all tasks.
4. Replace one task using `.set()`.
5. Remove one task using `.remove()`.
6. Print how many tasks remain using `.size()`.
---
### 5.Java Documentation
Java Documentation refers to the process of writing clear, descriptive comments in your Java code so that other developers (and your future self) can understand it.
Java provides a tool called Javadoc that can automatically generate HTML documentation from special comments in your source code.
Javadoc is a documentation generator that comes with the JDK.
It uses special multi-line comments called documentation comments.

These comments start with:
```java
/** ... */
```
Placed before classes, methods, constructors, and fields.

Can include special tags like `@param`, `@return`, and `@author`.

### Example:

```java
/**
 * This class represents a simple calculator that can perform basic operations.
 * <p>
 * It supports addition and subtraction for now.
 * </p>
 * @author John Doe
 * @version 1.0
 */
public class Calculator {
    /**
     * Adds two integers.
     * @param a The first integer
     * @param b The second integer
     * @return The sum of a and b
     */
    public int add(int a, int b) {
        return a + b;
    }

    /**
     * Subtracts one integer from another.
     * @param a The integer to subtract from
     * @param b The integer to subtract
     * @return The difference a - b
     */
    public int subtract(int a, int b) {
        return a - b;
    }
}
```

**Common Javadoc Tags**

| Tag         | Meaning |
|-------------|---------|
| @author     | Author of the class |
| @version    | Version number of the class |
| @param      | Describes a method parameter |
| @return     | Describes the return value |
| @throws / @exception | Describes exceptions a method can throw |
| @see        | Links to another class or method |


---
### 6.Generating Javadoc in IntelliJ IDEA.
1- Go to Tools → Generate JavaDoc.
2- In the dialog:
- Scope: Choose Whole project or specific packages/classes.
- Output directory: Select where the HTML documentation should be saved.

3- Click OK.

IntelliJ will generate the HTML docs in the selected folder — open the index.html file to view them in your browser.

### Example: Small Program with Documentation
```java
/**
 * A simple program to demonstrate Javadoc usage.
 */
public class Greeting {
    /**
     * Prints a greeting message.
     * @param name The name of the person to greet
     */
    public void sayHello(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        Greeting g = new Greeting();
        g.sayHello("Alice");
    }
}
```
----

### Example: ElapsedTime.java

```java
/**
 * A class representing an elapsed time measurement in hours and minutes.
 * 
 * @author Mary Adams
 * @version 1.0
 */
public class ElapsedTime {
    
    /**
     * The hours portion of the time.
     */
    private int hours;
    
    /**
     * The minutes portion of the time.
     */
    private int minutes;

    /**
     * Constructor initializing hours to timeHours and minutes to timeMins.
     * 
     * @param timeHours hours portion of time
     * @param timeMins  minutes portion of time
     */   
    public ElapsedTime(int timeHours, int timeMins) {
        hours   = timeHours;
        minutes = timeMins;
    }
    
    /**
     * Default constructor initializing all fields to 0.
     */   
    public ElapsedTime() {
        hours = 0;
        minutes = 0;
    }
    
    /**
     * Prints the time represented by an ElapsedTime object in hours and minutes.
     */
    public void printTime() {
        System.out.print(hours + " hour(s) " + minutes + " minute(s)");
    }
    
    /**
     * Sets the time to timeHours:timeMins.
     * 
     * @param timeHours hours portion of time
     * @param timeMins  minutes portion of time
     */
    public void setTime(int timeHours, int timeMins) {
        hours = timeHours;
        minutes = timeMins;
    }

    /**
     * Returns the total time in minutes.
     * 
     * @return an int value representing the elapsed time in minutes.
     */
    public int getTimeMinutes() {
        return ((hours * 60) + minutes);
    }
}
```

```java
import java.util.Scanner;

/**
 * This program calculates the difference between two user-entered times.
 * This class contains the program's main() method and is not meant to be instantiated.
 * 
 * @author Mary Adams
 * @version 1.0
 */
public class TimeDifference {
    
    /**
     * Asks for two times, creating an ElapsedTime object for each,
     * and uses ElapsedTime's getTimeMinutes() method to properly 
     * calculate the difference between both times.
     * 
     * @param args command-line arguments
     * @see ElapsedTime#getTimeMinutes()
     */
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        int timeDiff;     
        int userHours;
        int userMins;
        
        ElapsedTime startTime = new ElapsedTime(); // Starting time
        ElapsedTime endTime = new ElapsedTime();   // Ending time

        // Read starting time
        System.out.print("Enter starting time (hrs mins): ");
        userHours = scnr.nextInt();
        userMins = scnr.nextInt();
        startTime.setTime(userHours, userMins);
                
        // Read ending time
        System.out.print("Enter ending time (hrs mins): ");
        userHours = scnr.nextInt();
        userMins = scnr.nextInt();
        endTime.setTime(userHours, userMins);

        // Calculate difference in minutes
        timeDiff = endTime.getTimeMinutes() - startTime.getTimeMinutes(); 
        
        System.out.println("Time difference is " + timeDiff + " minutes");
    }
}
```

- A Doc comment associated with a class is written immediately before the class definition.
- The main description typically describes the class's purpose.
- Common block tags:
    - `@author` – Author name
    - `@version` – Version number
    - `@param` – Method parameter description
    - `@return` – Method return value description
    - `@see` – Links to another class or method

When referring to a method, the `@see` tag requires the format:  
`ClassName#methodName()`.

- Private class members are not included in Javadoc by default.
- API documentation is intended to describe the public interface available to other programmers.
- To include private members, use the `-private` flag when generating documentation.


### In-Class Activity – Document Your Code

1. Create a class called `Rectangle` with:
   - Two fields: `length` and `width`.
   - A constructor to initialize these fields.
   - A method `getArea()` that returns the area.
2. Add Javadoc comments for:
   - The class (with `@author`)
   - The constructor (with `@param`)
   - The `getArea()` method (with `@return`)
3. Generate HTML documentation using the `javadoc` tool.
---
### 7. Static fields and methods
The keyword static indicates a variable is allocated in memory only once during a program's execution. Static variables reside in the program's static memory region and have a global scope. Thus, static variables can be accessed from anywhere in a program.

In a class, a static field is a field of the class instead of a field of each class object. Thus, static fields are independent of any class object, and can be accessed without creating a class object. Static fields are declared and initialized in the class definition. Within a class method, a static field is accessed using the field name. A public static field can be accessed outside the class using dot notation: ClassName.fieldName.

Static fields are also called class variables, and non-static fields are also called instance variables.

<img width="698" alt="Screen Shot 2023-01-25 at 7 37 42 AM" src="https://user-images.githubusercontent.com/11669149/214606881-90ed6250-e618-4941-8421-c759bde79b04.png">

1. The Store class' static field nextId is declared and initialized in the Store class definition. Only one instance of the field nextId will exist in memory.   
2. When a Store object is created, memory is allocated for the object's name, type, and id fields, but not the static field nextId.   
3. The constructor assigns an object's id with nextId, and then increments nextId. Each time an object is created, nextId is incremented. Thus, each object will have a unique id.   
4. Any class method can access or mutate a static field. Because nextId is public, nextId can also be accessed outside the class using the member access operator (.)
## Static member methods
A static member method is a class method that is independent of class objects. Static member methods are typically used to access and mutate private static fields from outside the class. Since static methods are independent of class objects, the this parameter is not passed to a static member method. So, a static member method can only access a class' static fields.

### Example - Static member method used to access a private static field

    
``` java
public class Store {   
   // Declare and initialize private static field
   private static int nextId = 101;   

   // Define private fields 
   private String name;
   private String type;
   private int id;

   public Store(String storeName, String storeType) {
      name = storeName;
      type = storeType;
      id = nextId;

      ++nextId;   // Increment each time a Store object is created
   }

   public int getId() {
      return id;
   }
   
   public static int getNextId() {
      return nextId;
   }
}


```

    
``` java
public class NewStores {
   public static void main(String[] args) {
      Store store1 = new Store("Macy's", "Department");
      Store store2 = new Store("Albertsons", "Grocery");
      Store store3 = new Store("Ace", "Hardware");
    
      System.out.println("Store 1's ID: " + store1.getId());
      System.out.println("Store 2's ID: " + store2.getId());
      System.out.println("Store 3's ID: " + store3.getId());
      System.out.println("Next ID: " + Store.getNextId());
   }
}
```
### In-Class Activity – Static Members and Methods

**Step 1** – Create the Class

Write a Java class called BankAccount with:
- Static field

```java
private static int accountCounter = 1000; // shared across all accounts
```
- Instance fields

```java
private String accountHolder;
private int accountNumber;
```

- Constructor that Accepts `accountHolder`, Assigns `accountNumber = current accountCounter`and Increments `accountCounter` by 1

- Static method
```java
public static int getTotalAccounts() // returns the total accounts created.
```

- Instance method
```java
public void displayInfo() // prints account holder and account number.
```

**Step 2** – Write the Main Class

Create a class BankSystem with `main()`:

1. Create three BankAccount objects with different account holders.
2. Display each account’s info using `displayInfo()`.
3. Use the static method `BankAccount.getTotalAccounts()` to print the total number of accounts created.


**Expected Output**
```yaml
Account Holder: Alice | Account Number: 1000
Account Holder: Bob   | Account Number: 1001
Account Holder: Carol | Account Number: 1002
Total Accounts Created: 3
```
































