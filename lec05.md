### **Lecture 5 | Programming Methodology - Summary**

[Watch the full lecture here](https://www.youtube.com/watch?v=NPzPnycCFuE).

This lecture introduces fundamental concepts of **Java programming**, including **variables, data types, assignments, and object-oriented programming** (OOP). It also dives into **graphics programming**, demonstrating how to create and manipulate visual elements like labels, rectangles, and ovals. Below is a concise breakdown of the topics discussed.

---

### **1. Variables in Java**

- **Definition**: A **variable** stores data that can change during program execution.  
  Each variable has:

  - **Name**: The reference to the stored value.
  - **Type**: Specifies the kind of data (e.g., integer, text).
  - **Value**: The actual data being stored.

- **Naming Rules**:

  - Must start with **a letter or an underscore**.
  - Can contain **letters, numbers, and underscores** (but not start with a number).
  - Must not use **reserved keywords** (e.g., `class`, `public`).

- **Primitive Data Types**:
  - **`int`**: Stores whole numbers (e.g., `int count = 5;`).
  - **`double`**: Stores decimal numbers (e.g., `double pi = 3.14;`).
  - **`boolean`**: Stores `true` or `false` (e.g., `boolean isActive = true;`).
  - **`char`**: Stores a single character (e.g., `char letter = 'A';`).

---

### **2. Assignments and Initialization**

- **Declaration**: Introducing a variable by defining its type.
  ```java
  int x;
  ```
- **Initialization**: Assigning an initial value during or after declaration.
  ```java
  int x = 3; // Declaration + Initialization
  x = 4;     // Assignment (updates value)
  ```
- **Assignment in Java vs Math**:
  - **`=`** means assigning a new value, not equality.
    ```java
    total = total + 1; // Adds 1 to total
    ```

---

### **3. Classes and Objects**

- **Class**: A **blueprint** for objects (e.g., `GLabel`, `GRect`).
- **Object**: A **specific instance** of a class created using the **`new`** keyword.

  ```java
  GLabel label = new GLabel("Hello, World!", 100, 75);
  ```

- **Class Hierarchy & Inheritance**:
  - **GObject** is a **parent class** for many graphical objects (like `GRect` and `GOval`), sharing common behaviors.

---

### **4. Java Graphics Programming Overview**

- **Graphics Program**: Uses the **`GraphicsProgram`** class to create visual elements (e.g., text, shapes).
- **Creating Visual Elements**:

  ```java
  GLabel label = new GLabel("Hello!", 50, 50);
  add(label);
  ```

- **Common Objects**:
  - **GLabel**: Displays text.
  - **GRect**: Draws rectangles.
  - **GOval**: Draws ovals.
  - **GLine**: Draws straight lines between two points.

---

### **5. Manipulating Graphics Objects**

- **Adding Objects to the Canvas**:

  - Use the **`add()`** method to display objects on the screen.
    ```java
    add(label);
    ```

- **Object Methods**:
  - **`setColor()`**: Changes the color of an object.
    ```java
    label.setColor(Color.RED);
    ```
  - **`move(dx, dy)`**: Moves an object by a certain number of pixels.
    ```java
    label.move(10, 0); // Moves 10 pixels right
    ```
  - **`setLocation(x, y)`**: Places an object at a specific location.
    ```java
    label.setLocation(100, 200);
    ```

---

### **6. Creating Geometrical Shapes**

- **GRect**: Creates a rectangle by specifying its **upper-left corner, width, and height**.

  ```java
  GRect rect = new GRect(10, 10, 50, 50);
  add(rect);
  ```

- **GOval**: Creates an oval **within a bounding rectangle**.

  ```java
  GOval oval = new GOval(300, 75, 200, 100);
  oval.setFilled(true);
  oval.setFillColor(Color.GREEN);
  add(oval);
  ```

- **GLine**: Draws a line between two points.
  ```java
  GLine line = new GLine(0, 0, 100, 100);
  add(line);
  ```

---

### **7. Working with Colors and Fill**

- **Setting Fill**:
  ```java
  rect.setFilled(true); // Makes the rectangle solid
  ```
- **Setting Fill Color**:

  ```java
  rect.setFillColor(Color.BLUE);
  ```

- **Color Import**:
  ```java
  import java.awt.Color;
  ```

---

### **8. Coordinate System in Graphics Programs**

- **(0, 0)** is the **upper-left corner** of the window.
- **X-axis**: Increases to the **right**.
- **Y-axis**: Increases **downward**.

---

### **9. Example: Fun Graphics Program**

```java
import acm.graphics.*;
import acm.program.*;
import java.awt.*;

public class FunGraphics extends GraphicsProgram {
    public void run() {
        GLabel label = new GLabel("Hello, World!", 100, 75);
        label.setFont("SansSerif-36");
        label.setColor(Color.RED);
        add(label);

        GRect rect = new GRect(10, 10, 50, 50);
        add(rect);

        GRect bigRect = new GRect(300, 75, 200, 100);
        bigRect.setFilled(true);
        bigRect.setFillColor(Color.RED);
        add(bigRect);

        GOval oval = new GOval(300, 75, 200, 100);
        oval.setFilled(true);
        oval.setFillColor(Color.GREEN);
        add(oval);

        GLine line = new GLine(100, 150, 200, 175);
        add(line);

        // Uncomment to add another line:
        // GLine missingLine = new GLine(0, 0, 100, 100);
        // add(missingLine);
    }
}
```

This program creates several graphical objects, assigns colors and fills, and adds them to the canvas.

---

### **10. Expressions and Operators**

- **Expressions**: Combine variables, constants, and operators to perform calculations.

  ```java
  int total = n1 + n2;
  ```

- **Java Operators**:

  - **`+`**: Addition or string concatenation.
  - **`-`**: Subtraction.
  - **`*`**: Multiplication.
  - **`/`**: Division (beware of integer division).
  - **`%`**: Remainder operator.

- **Remainder Example**:
  ```java
  int remainder = 7 % 2; // Result: 1
  ```

---

### **11. Common Errors to Avoid**

- **Forgetting to add objects** to the canvas:

  - Creating an object doesn’t display it unless **`add()`** is called.
    ```java
    // Common error:
    GLine line = new GLine(0, 0, 100, 100);
    // Forgot to add the line!
    ```

- **Misunderstanding assignment vs equality**:
  - **`=`** is for assignment, not mathematical equality.

---

### **12. Conclusion**

This lecture introduced **Java’s variable management**, **OOP concepts**, and **graphics programming**. It emphasized the importance of **assignments, class hierarchies, and object creation**. You also learned how to manipulate objects using various methods (like setting colors and positions).

**Practice Tip:** Experiment with **graphics programs** to develop a deeper understanding of Java’s object-oriented approach and visual capabilities!
