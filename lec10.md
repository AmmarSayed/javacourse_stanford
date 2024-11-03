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
    setup(); // create the ball and added it to the screen

    // simulation ends when ball goes off right hand end of screen
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
  // determin if ball has dropped below the floor
    if (ball.getY() + DIAMETER >= getHeight()) {
      // change ball's Y velocity to now bounce upwords
        vy = -vy * BOUNCE_REDUCE;  // Reverse the Y and reduce speed

        // assume bounce will move the ball an amount above the
        // floor equal to the amount it would have dropped
        // below the floor
        double diff = ball.getY() - (getHeight() - DIAMETER);
        ball.move(0,-2*diff);
    }
}
```

### **Explanation:**

- **Setup**: Initializes the ball and places it on the canvas.
- **Animation Loop**: Continuously moves the ball and checks for collisions.
- **Collision Detection**: Reverses the ball's Y-velocity when it hits the bottom.

---

## **6. GLabel: Working with Text**

- **GLabel** displays text on the canvas and allows customization.
- **Centering Lables Example**:

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

## **7. Drawing Arcs with GArc**

- **`GArc`** allows drawing a **portion of a circle** or an oval.
- **Specifying an Arc**:
  - **Bounding Box**: Defines the rectangle containing the arc.
  - **Start Angle**: Starting angle in degrees.
  - **Sweep Angle**: How much of the circle to draw.

#### Example:

```java
// cx and cy are coorindates of window center
// d (diameter) is 0.8 times the screen height
GArc arc1 = new GArc(d, d, 0, 90); // same diameter height and width, start from digree 0, and draw till 90 degrees
GArc arc2 = new GArc(d, d, 45, 270); // same diameter height and width, start from digree 45 but counter, and draw till 270 degrees
GArc arc2 = new GArc(d, d, -90, 45); // draw an arc 90 degrees down clock-wise `down`, then draw 45 degrees as normal counter-clock-wise
add(arc1, cx - d / 2, cy - d / 2 ); // put the arc in the center of the screen
add(arc1, cx - d / 2, cy - d / 2 ); // put the arc in the center of the screen
arc1.setFilled(true);
```

- This code draws **half of a circle** starting at a **45-degree angle**.

---

## **8. Interfaces in Graphics**

- An **interface** defines a **set of methods** that can be shared across different classes.
- Interfaces in Java define a set of methods that a class can implement.
- They provide a way to group together classes that share common behavior, even if they don't have a direct hierarchical relationship.
- Interfaces allow for polymorphism, where objects of different classes can be treated as instances of a common interface and have their methods called in a uniform way.
- **Example `GFillable` Interface**:
  - Methods: `setFilled()`, `isFilled()`, `setFillColor(c)`, `getFillcolor()`
  - Implemented by: `GOval`, `GRect`, `GPolygon`
- **Example `GResizable` Interface**:
  - Method: `setSize(width,height)`, `setBounds()`
  - Implemented by: `GImage`, `GOval`, `GRect`
- **Example `GScalable` Interface**:
  - Method: `scale(sf)`, `scale(xx,xy)`. Where `( sf )` is scale factor
  - Implemented by: `GArc`, `GCompound`, `GLine`, `GImage`, `GOval`, `GPolygon`, `GRect`

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
