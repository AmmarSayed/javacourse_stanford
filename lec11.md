### **Lecture 11 | Programming Methodology - Summary**

In this lecture, the focus is on **advanced graphics programming** with the ACM library. The session introduces **GImage, GPolygon, and GCompound** for creating more complex visual elements, as well as **event-driven programming** using **mouse and keyboard listeners**. These concepts are essential for building interactive programs, such as the breakout game.

Watch the full lecture [here](https://www.youtube.com/watch?v=Iua9Klr0lfo).

---

## **1. GImage: Displaying Images in Graphics Programs**

- **GImage** allows you to display external images (like `.gif` or `.jpg`) in your program.
- **Creating and Adding GImage**:
  ```java
  GImage image = new GImage("stanford-seal.gif");
  add(image, 0, 0);  // Add image at (0, 0) on the canvas
  ```
- **File Location**:

  - The program looks for the image in the **project directory** or a subfolder named **`images/`**.
  - If the image isn’t found, it results in an error.

- **Resizing Images**:
  - GImage is **resizable**, allowing you to distort or stretch it.
  ```java
  image.scale(1.5, 0.5);  // Scale 1.5x in width, 0.5x in height
  ```

---

## **2. GPolygon: Creating Custom Shapes**

- **GPolygon** is used to create **polygons with any number of sides** by specifying **vertices**.
- **Reference Point**: All vertices are **relative to a reference point** (often the center of the shape).

### **Example: Creating a Diamond Shape**

```java
public GPolygon createDiamond(double width, double height) {
    GPolygon diamond = new GPolygon();
    diamond.addVertex(-width / 2, 0);  // Left point
    diamond.addVertex(0, -height / 2);  // Top point
    diamond.addVertex(width / 2, 0);  // Right point
    diamond.addVertex(0, height / 2);  // Bottom point
    return diamond;
}
```

- **Vertices vs. Edges**:
  - Use **`addVertex(x, y)`** to specify corner points.
  - Use **`addEdge(dx, dy)`** to add a new vertex **relative to the last one**.
- **Auto-closure**: Polygons automatically **close** by connecting the last vertex back to the first.

---

## **3. GCompound: Grouping Objects Together**

- **GCompound** allows grouping multiple GObjects into one object, which can be treated as a single unit.
- **Example: Creating a GFace (Face with Eyes, Nose, and Mouth)**:

```java
public class GFace extends GCompound {
    public GFace(double width, double height) {
        GOval head = new GOval(width, height);  // Head
        GOval leftEye = new GOval(width * 0.1, height * 0.1);  // Left eye
        GOval rightEye = new GOval(width * 0.1, height * 0.1);  // Right eye

        add(head, 0, 0);
        add(leftEye, width * 0.25, height * 0.25);
        add(rightEye, width * 0.75, height * 0.25);
    }
}
```

- **Adding GCompound to Canvas**:

  ```java
  GFace face = new GFace(100, 100);
  add(face, 50, 50);  // Add face at (50, 50) on the canvas
  ```

- **Use Case**: Grouping shapes simplifies **movement** and **scaling**. For example, the entire face can bounce as a single unit.

---

## **4. Event-Driven Programming with Mouse and Keyboard**

### **How Event Listeners Work**

- **Asynchronous Events**: Your program responds to user input (mouse clicks, key presses) as events occur.
- **Adding Listeners**:
  ```java
  addMouseListeners();  // Listen for mouse events
  addKeyListeners();    // Listen for keyboard events
  ```
- **Important**: Without listeners, your program cannot respond to events.

---

### **Mouse Event Listeners**

- **Common Mouse Methods**:
  - **`mouseClicked()`**: Called when the mouse is clicked.
  - **`mousePressed()`**: Called when the button is pressed.
  - **`mouseReleased()`**: Called when the button is released.
  - **`mouseDragged()`**: Called when the mouse is moved while holding the button down.
  - **`mouseMoved()`**: Called whenever the mouse moves.

#### **Example: Click for Face**

This example adds a new face at the location where the mouse is clicked.

```java
public class ClickForFace extends GraphicsProgram {
    public void init() {
        addMouseListeners();
    }

    public void mouseClicked(MouseEvent e) {
        GFace face = new GFace(30, 30);  // Create a new face
        add(face, e.getX(), e.getY());  // Add face at click location
    }
}
```

---

### **Keyboard Event Listeners**

- **Common Key Methods**:
  - **`keyPressed()`**: Called when a key is pressed.
  - **`keyReleased()`**: Called when the key is released.
  - **`keyTyped()`**: Called when a key is pressed and released.

---

## **5. Dragging Objects with Mouse Events**

This example allows the user to **drag shapes** on the screen by clicking and moving the mouse.

#### **Drag Objects Example**

```java
public class DragObjects extends GraphicsProgram {
    private GObject selectedObject;  // Track the object being dragged

    public void init() {
        GRect rect = new GRect(50, 50, 100, 100);
        GOval oval = new GOval(200, 50, 100, 100);
        add(rect);
        add(oval);
        addMouseListeners();
    }

    public void mousePressed(MouseEvent e) {
        selectedObject = getElementAt(e.getX(), e.getY());  // Get clicked object
    }

    public void mouseDragged(MouseEvent e) {
        if (selectedObject != null) {
            selectedObject.setLocation(e.getX(), e.getY());  // Move the object
        }
    }
}
```

- **`getElementAt(x, y)`**: Returns the topmost object at the given coordinates or `null` if no object is present.
- **Moving Objects**: The object is moved by **setting its new location** as the mouse drags it across the screen.

---

## **6. Animation Example: Bouncing Face**

This example builds on the **bouncing ball animation** by replacing the ball with a **bouncing face**.

#### **Bouncing Face Example**

```java
public void run() {
    GFace face = new GFace(50, 50);
    add(face, 0, 100);
    double vx = 5;  // X velocity
    double vy = 0;  // Y velocity

    while (true) {
        face.move(vx, vy);
        vy += 3;  // Simulate gravity
        pause(50);  // Pause for animation
    }
}
```

- **Replacing Objects Easily**: By creating reusable classes like **GFace**, you can replace objects (like a ball) with more complex shapes.

---

## **7. Final Game: UFO Shooter Example**

The UFO game demonstrates **animation and event handling**. A UFO moves toward the bottom of the screen, and the player must click to shoot it.

#### **Game Logic Overview**

1. **Animation Loop**:
   - Continuously update the positions of the UFO and bullets.
   - Detect collisions between the UFO and bullets.
2. **Mouse Listener**:
   - On each click, a new bullet is fired.
3. **Game Over**:
   - If the UFO reaches the bottom of the screen, the game ends.

---

## **Summary**

In this lecture, the focus is on **graphics programming and event-driven development**. You learned how to:

1. **Add images (GImage)** and **create custom shapes (GPolygon)**.
2. **Group objects (GCompound)** to simplify movement and scaling.
3. **Use event listeners** to respond to **mouse and keyboard input** asynchronously.
4. **Drag and move objects** using mouse events.
5. Build interactive programs, laying the foundation for games like **Breakout**.

These concepts enable the development of **dynamic, interactive applications** using Java and the ACM library.
