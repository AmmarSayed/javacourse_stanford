### **Lecture 10 | Programming Methodology - Summary**

This lecture focuses on **object-oriented programming concepts** like **inheritance and class extension**, and **introduces graphics programming** using the **ACM Graphics Library**. It builds upon the student class example from the previous lecture and extends it through **subclasses**, followed by an introduction to **graphics components** and their usage in Java.

Watch the full lecture [here](https://www.youtube.com/watch?v=YpZCKVG4s5k).

---

## **1. Review of the Student Class**

- The class **encapsulates data** (e.g., `studentName`, `studentID`) and uses **private variables** with **public getters and setters** to control access.
- **Why Use Getters/Setters?**
  - They maintain **encapsulation** and protect how the data is accessed or modified.
  - Example: A student’s ID is set only during initialization and cannot be changed later.

### **Student Class Recap:**

```java
public class Student {
    private String studentName;
    private int studentID;
    private double unitsEarned;
    public static final int UNITS_TO_GRADUATE = 180;

    public Student(String name, int id) {
        studentName = name;
        studentID = id;
        unitsEarned = 0;
    }

    public String getName() {
        return studentName;
    }

    public int getID() {
        return studentID;
    }

    public double getUnits() {
        return unitsEarned;
    }

    public void setUnits(double units) {
        unitsEarned = units;
    }

    public boolean hasEnoughUnits() {
        return unitsEarned >= UNITS_TO_GRADUATE;
    }

    @Override
    public String toString() {
        return studentName + " (" + studentID + ")";
    }
}
```

---

## **2. Inheritance: Extending a Class**

Inheritance allows a **subclass** to reuse the properties and methods of a **superclass**.

### **Creating a Subclass: Frosh**

- **`Frosh` class** inherits from `Student` using the `extends` keyword.
- **Constructor with Super**: Calls the parent class constructor to **initialize shared properties** like `name` and `ID`.
- **Overriding Methods**: Provides a specialized implementation for `toString()`.

#### Example: Frosh Class

```java
public class Frosh extends Student {
    public Frosh(String name, int id) {
        super(name, id);  // Call the superclass constructor
        setUnits(0);  // Frosh start with 0 units
    }

    @Override
    public String toString() {
        return "Frosh: " + getName() + " (" + getID() + ")";
    }
}
```

- **Key Points about Overriding**:
  - A subclass can **override methods** from its parent class to provide customized behavior.
  - **Private variables** from the superclass (like `studentName`) are **not accessible directly** in the subclass. You need to use **public getters** (e.g., `getName()`).

---

## **3. ACM Graphics Library Overview**

- Graphics programs use **`GCanvas`** as a **drawing surface**, where you place various **`GObject`** elements like rectangles, ovals, lines, etc.
- **`GCanvas`** represents the background where objects are drawn.
- **Z-Order (Stacking Order)**: Newly added objects appear **on top** of older objects.

---

### **Key Methods of GCanvas / Graphics Program**

- **Adding and removing objects**:

  ```java
  add(object);  // Add a GObject to the canvas
  remove(object);  // Remove an object from the canvas
  removeAll();  // Clear the canvas
  ```

- **Pausing and Waiting for Click**:

  ```java
  pause(milliseconds);  // Pause for animation
  waitForClick();  // Wait for a mouse click to proceed
  ```

- **Retrieving Objects**:
  ```java
  GObject obj = getElementAt(x, y);  // Get object at a specific location
  ```

---

## **4. GObject: Drawing and Manipulating Objects**

### **Common GObject Methods**

- **Location and Movement**:

  ```java
  obj.setLocation(x, y);  // Set position
  obj.move(dx, dy);  // Move by dx and dy
  ```

- **Visibility**:

  ```java
  obj.setVisible(true);  // Make visible
  obj.setVisible(false);  // Make invisible without removing
  ```

- **Color**:

  ```java
  obj.setColor(Color.RED);  // Change object color
  ```

- **Z-order manipulation**:
  ```java
  obj.sendToFront();  // Bring to front
  obj.sendToBack();  // Send to back
  ```

---

## **5. Example: Bouncing Ball Animation**

This example demonstrates **animation** by moving a ball across the screen and bouncing it when it reaches the bottom.

#### Code for Bouncing Ball:

```java
private static final int DIAMETER = 30;
private static final double GRAVITY = 3.0;
private static final double BOUNCE_REDUCE = 0.9;
private static final int DELAY = 50;

private GOval ball;
private double vx = 5;  // X velocity
private double vy = 0;  // Y velocity

public void run() {
    setup();
    while (ball.getX() < getWidth()) {
        moveBall();
        checkForCollision();
        pause(DELAY);
    }
}

private void setup() {
    ball = new GOval(0, 100, DIAMETER, DIAMETER);
    ball.setFilled(true);
    add(ball);
}

private void moveBall() {
    vy += GRAVITY;
    ball.move(vx, vy);
}

private void checkForCollision() {
    if (ball.getY() + DIAMETER >= getHeight()) {
        vy = -vy * BOUNCE_REDUCE;  // Reverse and reduce speed
    }
}
```

### **Explanation:**

- **Setup**: Initializes the ball and places it on the canvas.
- **Animation Loop**: Continuously moves the ball and checks for collisions.
- **Collision Detection**: Reverses the ball's Y-velocity when it hits the bottom.

---

## **6. Drawing Arcs with GArc**

- **`GArc`** allows drawing a **portion of a circle** or an oval.
- **Specifying an Arc**:
  - **Bounding Box**: Defines the rectangle containing the arc.
  - **Start Angle**: Starting angle in degrees.
  - **Sweep Angle**: How much of the circle to draw.

#### Example:

```java
GArc arc = new GArc(50, 50, 100, 100, 45, 180);
add(arc);
```

- This code draws **half of a circle** starting at a **45-degree angle**.

---

## **7. GLabel: Working with Text**

- **GLabel** displays text on the canvas and allows customization.
- **Centering Text Example**:

```java
GLabel label = new GLabel("Hello, World!");
label.setFont("SansSerif-36");
label.setColor(Color.RED);

double x = (getWidth() - label.getWidth()) / 2;
double y = (getHeight() + label.getAscent()) / 2;
label.setLocation(x, y);
add(label);
```

- **Explanation**:
  - **Ascent**: Distance from the baseline to the top of the tallest character.
  - **Descent**: Distance below the baseline for letters like ‘g’ or ‘y’.
  - Use **ascent** to position text vertically.

---

## **8. Interfaces in Graphics**

- An **interface** defines a **set of methods** that can be shared across different classes.
- **Example: GFillable Interface**:
  - Methods: `setFilled()`, `isFilled()`
  - Implemented by: `GOval`, `GRect`, `GPolygon`

---

## **Summary**

This lecture covered **class inheritance, encapsulation, and subclassing** by extending the student class and creating **specializations like `Frosh`**. The second half introduced **graphics programming with the ACM library**, focusing on **drawing objects, animations, and text manipulation**.

Key Takeaways:

1. **Inheritance** allows **reuse and extension** of existing classes.
2. **Encapsulation** ensures that data is protected by controlling access via methods.
3. **Graphics programming** makes it easy to create interactive programs with the ACM library.
4. **Animation concepts** like **pausing** and **collision detection** enable dynamic behavior.
5. **Interfaces** provide a way to group methods across unrelated classes.

This sets the foundation for **game development** and **interactive applications** using Java.
