### **Lecture 9 | Programming Methodology - Summary**

In this lecture, the focus is on **writing custom classes, using strings, understanding objects and references**, and how **Java’s documentation system (Javadoc)** works. It builds on the concept of **encapsulation and object-oriented programming**, allowing developers to create **reusable components and manage data privately** within objects.

Watch the full lecture [here](https://www.youtube.com/watch?v=iYtri45lhtc).

---

## **1. Strings: Basic Introduction**

- **Strings** are a new data type representing a sequence of characters enclosed in **double quotes**.
- **Example of String usage**:
  ```java
  String greeting = "Hello, World!";
  String name = "Alice";
  int age = 25;
  String message = "Name: " + name + ", Age: " + age;
  System.out.println(message);
  ```
  - **Concatenation**: The `+` operator combines multiple strings and values into one string.
  - **Reading input as a String**:
    ```java
    String userInput = readLine("Enter your name: ");
    ```

---

## **2. Creating and Using Custom Classes**

- **Java Classes** encapsulate data (using instance variables) and behavior (via methods).
- **Structure of a Class**:

  ```java
  public class MyClass {
      // Instance variables
      private int value;

      // Constructor
      public MyClass(int startValue) {
          value = startValue;
      }

      // Method to increment value
      public int nextValue() {
          return value++;
      }
  }
  ```

- **How to Create Objects**:
  ```java
  MyClass obj = new MyClass(10);
  System.out.println(obj.nextValue());  // Outputs 10
  ```

### **Constructors**

- **Special method** that initializes an object when it is created. The constructor name **matches the class name** and does not return anything.
- You can have **multiple constructors** with different parameters (constructor overloading).

---

## **3. Encapsulation: Public vs. Private Access**

- **`public`**: Accessible from other classes.
- **`private`**: Only accessible within the class itself.

Example:

```java
public class Counter {
    private int value;  // Private instance variable

    public Counter(int start) {  // Public constructor
        value = start;
    }

    public int getValue() {  // Public method to access the value
        return value;
    }
}
```

- **Encapsulation ensures data integrity** by restricting direct access to variables, requiring controlled access through methods.

---

## **4. Instance vs. Class (Static) Variables**

- **Instance Variables**: Each object has its own copy.
- **Class (Static) Variables**: Shared by all instances of the class.

Example of a **static variable**:

```java
public class Student {
    private static int totalStudents = 0;  // Class variable

    public Student() {
        totalStudents++;  // Increment for every new student
    }

    public static int getTotalStudents() {
        return totalStudents;
    }
}
```

---

## **5. Objects and References**

- **Objects are passed by reference** in Java, meaning the original object is affected when modified inside a method.

### Example of Passing Objects by Reference:

```java
public void countFiveTimes(Counter counter) {
    for (int i = 0; i < 5; i++) {
        System.out.println(counter.nextValue());
    }
}
```

- When an object is passed to a method, **any changes made affect the original object**.

---

## **6. `this` Keyword**

- **`this`** refers to the current object’s instance.
- Useful when distinguishing between **parameters and instance variables** with the same name.

```java
public class Example {
    private int value;

    public Example(int value) {
        this.value = value;  // 'this.value' refers to the instance variable
    }
}
```

---

## **7. Class Variables and Static Fields**

- **Static fields** are shared across all instances of a class.
- Example of **class (static) variables**:

  ```java
  public class Counter {
      private static int sharedCounter = 0;

      public Counter() {
          sharedCounter++;
      }

      public static int getSharedCounter() {
          return sharedCounter;
      }
  }
  ```

---

## **8. Using Javadoc for Documentation**

- **Javadoc** is Java’s documentation tool that generates HTML pages from specially formatted comments.
- **Javadoc Syntax**:
  ```java
  /**
   * This method returns the name of the student.
   * @return the student's name
   */
  public String getName() {
      return name;
  }
  ```
- **Accessing Javadoc Documentation**:
  - You can browse the **Javadoc** for the ACM libraries used in this course [here](https://jtf.acm.org/javadoc/student/).

---

## **9. Full Example: Student Class**

This example demonstrates **class design, encapsulation, and the use of Javadoc**.

```java
/**
 * This class represents a student with a name, ID, and units earned.
 */
public class Student {
    private String name;
    private int id;
    private double units;

    public static final int UNITS_TO_GRADUATE = 180;

    /**
     * Creates a new student with the given name and ID.
     * @param name the student's name
     * @param id the student's ID number
     */
    public Student(String name, int id) {
        this.name = name;
        this.id = id;
        this.units = 0.0;
    }

    public String getName() {
        return name;
    }

    public void setUnits(double units) {
        this.units = units;
    }

    public boolean hasEnoughUnits() {
        return units >= UNITS_TO_GRADUATE;
    }

    @Override
    public String toString() {
        return name + " (" + id + ")";
    }
}
```

---

## **10. Running the Student Program**

This program uses the `Student` class to demonstrate object creation and method calling.

```java
public class Stanford extends ConsoleProgram {
    public void run() {
        Student ben = new Student("Ben Newman", 1001);
        ben.setUnits(179);

        System.out.println(ben.getName() + " has " + ben.units + " units.");
        System.out.println("Can graduate: " + ben.hasEnoughUnits());

        ben.setUnits(184);  // Increment units
        System.out.println("Can graduate: " + ben.hasEnoughUnits());

        System.out.println("Student Info: " + ben.toString());
    }
}
```

**Output:**

```
Ben Newman has 179.0 units.
Can graduate: false
Can graduate: true
Student Info: Ben Newman (1001)
```

---

## **Key Takeaways from Lecture 9**

1. **Custom Classes**: Learn to create your own classes with instance variables, constructors, and methods.
2. **Encapsulation**: Use `private` and `public` to control access to data.
3. **Javadoc**: Document your classes and methods using Javadoc comments.
4. **Static Variables**: Understand the difference between instance and static (class) variables.
5. **Objects and References**: Objects are passed by reference, allowing methods to modify them directly.

This lecture ties together **many core concepts** in Java, including **data encapsulation, reusability, and modular design**, which are essential for building maintainable software systems.
