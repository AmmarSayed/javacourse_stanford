### **Lecture 20 | Programming Methodology (Stanford) - Summary**

This lecture focuses on **Graphical User Interfaces (GUIs)** in Java, specifically using **interactors** such as buttons, sliders, checkboxes, radio buttons, combo boxes, and text fields. These components enable **user interaction** with your program through a **graphical interface**.

Watch the full lecture [here](https://www.youtube.com/watch?v=b8OLOWWxvx0).

---

## **1. Introduction to GUIs and Interactors**

- A **GUI** is a **Graphical User Interface** that lets users interact with an application via **visual elements** (e.g., buttons, sliders, combo boxes).
- **Interactors**: Components that allow users to **input data** or **interact** with the program.

Examples of Interactors:

- **Buttons**
- **Sliders**
- **Checkboxes**
- **Radio Buttons**
- **Combo Boxes (Drop-Down Menus)**
- **Text Fields**

---

## **2. Java Libraries for GUI Programming**

To use interactors, you need to import:

```java
import java.awt.event.*;   // Handles events like button clicks
import javax.swing.*;      // Provides GUI components like buttons, checkboxes
```

---

## **3. The Window Layout Regions in Java Programs**

A Java program window is divided into **five regions**:

- **North**
- **South**
- **East**
- **West**
- **Center**

Previously, only the **center** region was used (e.g., for a canvas). Now, **interactors** can be placed in the **north, south, east, or west regions**. When an interactor is added, its corresponding region becomes visible.

---

## **4. Creating and Adding a Button**

### **Creating a Button:**

```java
JButton button = new JButton("Hi");
```

- This creates a button labeled "Hi" but doesn’t display it yet.

### **Adding the Button to the Window:**

```java
add(button, SOUTH);
```

- The `add()` method places the button in the **southern control bar**.

### **Adding Action Listeners:**

To respond to button clicks, you need to **add an action listener**:

```java
addActionListeners();
```

- This enables the program to detect user actions (like button presses).

---

## **5. Handling Button Clicks with `actionPerformed()`**

When a button is clicked, the **`actionPerformed()`** method is called automatically.

```java
public void actionPerformed(ActionEvent e) {
    String cmd = e.getActionCommand();  // Get the button’s label
    if (cmd.equals("Hi")) {
        println("Hello");
    }
}
```

- **`getActionCommand()`** returns the label of the button that was clicked.
- Use **conditional logic** to perform specific actions based on which button was pressed.

---

## **6. Example: Multiple Buttons with `actionPerformed()`**

```java
JButton helloButton = new JButton("Hello");
JButton csButton = new JButton("CS106A");
JButton basketButton = new JButton("Basket Weaving");

add(helloButton, NORTH);
add(csButton, SOUTH);
add(basketButton, SOUTH);

addActionListeners();
```

In `actionPerformed()`:

```java
public void actionPerformed(ActionEvent e) {
    String cmd = e.getActionCommand();
    if (cmd.equals("Hello")) {
        println("Hello there!");
    } else if (cmd.equals("CS106A")) {
        println("CS106A rocks!");
    } else if (cmd.equals("Basket Weaving")) {
        println("Not so much.");
    }
}
```

---

## **7. Adding Checkboxes**

Check if a **checkbox** is selected using `isSelected()`:

```java
JCheckBox showFront = new JCheckBox("Front");
showFront.setSelected(true);   // Initially checked

add(showFront, SOUTH);

boolean isSelected = showFront.isSelected();  // Check its state
```

- **Checkboxes** allow users to toggle options on or off.

---

## **8. Using Radio Buttons**

### **Creating and Grouping Radio Buttons:**

```java
JRadioButton small = new JRadioButton("Small");
JRadioButton medium = new JRadioButton("Medium");
JRadioButton large = new JRadioButton("Large");

ButtonGroup sizeGroup = new ButtonGroup();
sizeGroup.add(small);
sizeGroup.add(medium);
sizeGroup.add(large);

add(small, SOUTH);
add(medium, SOUTH);
add(large, SOUTH);
medium.setSelected(true);  // Default to medium size
```

- **Radio buttons** must be placed in a **ButtonGroup** to ensure only one can be selected at a time.

---

## **9. Combo Boxes (Drop-Down Menus)**

A **combo box** allows users to select one option from a drop-down list.

### **Creating a Combo Box:**

```java
JComboBox<String> colorChooser = new JComboBox<>();
colorChooser.addItem("Black");
colorChooser.addItem("Blue");
colorChooser.addItem("Green");
colorChooser.addItem("Red");

colorChooser.setEditable(false);  // Disable typing new values
colorChooser.setSelectedItem("Black");  // Default selection

add(new JLabel("Color: "), SOUTH);  // Add label before combo box
add(colorChooser, SOUTH);
```

Retrieve the selected value:

```java
String selectedColor = (String) colorChooser.getSelectedItem();
```

---

## **10. Putting It All Together: GUI-Based Face Drawing App**

This example uses buttons, checkboxes, radio buttons, and a combo box to create an interactive face-drawing program.

1. **Clear Button**: Removes all faces from the canvas.
2. **Checkbox**: Toggles between showing the **front or back** of the face.
3. **Radio Buttons**: Select the **size** of the face (small, medium, or large).
4. **Combo Box**: Select the **color** of the face.

---

### **Key Methods in the App**

**Mouse Listener for Drawing Faces:**

```java
public void mouseClicked(MouseEvent e) {
    double size = getDiameterSize();
    GObject face;

    if (showFront.isSelected()) {
        face = new GFace(size, size);  // Front of face
    } else {
        face = new GOval(size, size);  // Back of face (oval)
    }

    face.setColor(getCurrentColor());
    add(face, e.getX(), e.getY());
}
```

**Determine Selected Size (Radio Buttons):**

```java
private double getDiameterSize() {
    if (small.isSelected()) return 20;
    if (medium.isSelected()) return 40;
    if (large.isSelected()) return 60;
    return 0;
}
```

**Get Selected Color (Combo Box):**

```java
private Color getCurrentColor() {
    String color = (String) colorChooser.getSelectedItem();
    switch (color) {
        case "Blue": return Color.BLUE;
        case "Green": return Color.GREEN;
        case "Red": return Color.RED;
        default: return Color.BLACK;
    }
}
```

---

## **11. Key Takeaways**

1. **GUIs allow interactive programs** by using components like buttons, checkboxes, radio buttons, and combo boxes.
2. **Interactors must be added to specific regions** (north, south, east, or west) to appear on the screen.
3. **Action listeners** detect button clicks, while **state checks** determine the current state of checkboxes and radio buttons.
4. **Radio buttons must be grouped** to ensure only one option is selected at a time.
5. **Combo boxes** simplify selection from a list of predefined values.

This lecture provides the tools to **build interactive Java applications**, making it easier to engage users through **intuitive graphical interfaces**.
