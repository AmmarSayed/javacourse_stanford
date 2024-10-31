### **Lecture 21 | Programming Methodology (Stanford) - Summary**

This lecture continues the discussion on **interactors** (buttons, text fields, etc.) and explores new ways to create **interactive GUIs** in Java. The session focuses on using **text fields**, **event handling**, and **layouts**, along with techniques for **combining text, graphics, and interactors**.

Watch the full lecture [here](https://www.youtube.com/watch?v=RJfQK6iAN4M).

---

## **1. Action Listeners Review**

- **Action Listeners** detect when a user interacts with buttons or other components.
- **Action Events** trigger the `actionPerformed()` method when a button is clicked.

### Example:

```java
public void actionPerformed(ActionEvent e) {
    String cmd = e.getActionCommand();  // Get the button's name
    if (cmd.equals("Hi")) {
        println("Hello there!");
    }
}
```

- The `getActionCommand()` method returns the **name** of the interactor that generated the event.
- Another way to handle actions is by using `getSource()` to get a **reference to the object** that caused the event.

### **Using `getSource()` Example:**

```java
if (e.getSource() == myButton) {
    println("You clicked the button!");
}
```

- **Comparison between `getSource()` and `getActionCommand()`**:
  - Use **`getSource()`** if you need to compare **object references**.
  - Use **`getActionCommand()`** if comparing **interactor names** is sufficient.

---

## **2. Text Fields and Event Handling**

A **JTextField** allows users to enter text in a GUI. When the user presses **Enter**, an **action event** is triggered.

### **Creating a Text Field:**

```java
JTextField textField = new JTextField(10);  // Max 10 characters
textField.addActionListener(this);  // Register it to generate events
add(textField, SOUTH);  // Add it to the GUI
```

### **Handling Text Field Input:**

```java
public void actionPerformed(ActionEvent e) {
    if (e.getSource() == textField) {
        println("Hello, " + textField.getText());
    }
}
```

- **Add Labels** to text fields to make them more user-friendly:

```java
add(new JLabel("Name:"), SOUTH);
add(textField, SOUTH);
```

---

## **3. Managing Layouts**

Layouts control how components are arranged in the window.

### **Border Layout (Default Layout):**

- Divides the window into **north, south, east, west, and center** regions.
- **Only visible** if interactors are added to the regions.

### **Grid Layout:**

- Arranges components in a **grid of rows and columns**.

```java
setLayout(new GridLayout(2, 3));  // 2 rows, 3 columns
```

- Components are added **sequentially**:

```java
add(new JButton("Button 1"));
add(new JButton("Button 2"));
```

**Grid Layout Example:**

- Buttons fill the entire space in each cell:

```java
setLayout(new GridLayout(2, 3));  // Two rows and three columns
add(new JButton("1"));
add(new JButton("2"));
add(new JButton("3"));
```

---

## **4. Using Specialized Layouts (Table Layout)**

- **Table Layout** works similarly to Grid Layout but **only gives each component as much space as needed**.
- **Why Table Layout?**
  - Avoids oversized components, unlike Grid Layout.

---

## **5. Temperature Converter Example**

This program demonstrates how to combine **buttons** and **text fields** for input and conversion.

### **Program Overview:**

- **Two input fields**: one for **Fahrenheit** and one for **Celsius**.
- **Two buttons**: Convert **Fahrenheit to Celsius** and vice versa.

### **Code Snippet:**

```java
// Create the layout
setLayout(new TableLayout(2, 3));  // 2 rows, 3 columns

// Fahrenheit to Celsius components
add(new JLabel("Fahrenheit:"));
IntField fahrenheitField = new IntField(32);
add(fahrenheitField);
add(new JButton("F -> C"));

// Celsius to Fahrenheit components
add(new JLabel("Celsius:"));
IntField celsiusField = new IntField(0);
add(celsiusField);
add(new JButton("C -> F"));
```

### **Event Handling:**

```java
public void actionPerformed(ActionEvent e) {
    String cmd = e.getActionCommand();
    if (cmd.equals("F -> C")) {
        int fahrenheit = fahrenheitField.getValue();
        int celsius = (fahrenheit - 32) * 5 / 9;
        celsiusField.setValue(celsius);
    } else if (cmd.equals("C -> F")) {
        int celsius = celsiusField.getValue();
        int fahrenheit = celsius * 9 / 5 + 32;
        fahrenheitField.setValue(fahrenheit);
    }
}
```

---

## **6. Combining Text, Graphics, and Interactors**

This example shows how to integrate **text fields, graphics, and interactors** in the same program.

### **Program Overview:**

- **Two canvases**: Left and right.
- **A text field** to accept user input.
- **Two buttons** to draw rectangles on either the left or right canvas.

### **Code Snippet:**

```java
// Set up the layout with two canvases
setLayout(new GridLayout(1, 3));

leftCanvas = new GCanvas();
add(leftCanvas);

rightCanvas = new GCanvas();
add(rightCanvas);
```

### **Adding Interactors:**

```java
add(new JLabel("Enter text:"), SOUTH);
textField = new JTextField(10);
add(textField, SOUTH);
textField.addActionListener(this);

add(new JButton("Draw Left"), SOUTH);
add(new JButton("Draw Right"), SOUTH);
```

### **Handling Button Clicks and Text Input:**

```java
public void actionPerformed(ActionEvent e) {
    String cmd = e.getActionCommand();
    if (cmd.equals("Draw Left")) {
        GRect rect = new GRect(50, 20);
        leftCanvas.add(rect, 20, leftY);
        leftY += 30;
    } else if (cmd.equals("Draw Right")) {
        GRect rect = new GRect(50, 20);
        rightCanvas.add(rect, 20, rightY);
        rightY += 30;
    } else if (e.getSource() == textField) {
        println("You typed: " + textField.getText());
    }
}
```

- **Result:**
  - Clicking the **"Draw Left"** or **"Draw Right"** button adds rectangles to the respective canvases.
  - Typing into the text field and hitting **Enter** displays the text in the console.

---

## **7. Key Takeaways**

1. **Action Listeners** can handle multiple interactors, including buttons and text fields.
2. Use **`getSource()`** to compare objects directly and **`getActionCommand()`** to compare interactor names.
3. **Layouts** (Grid, Table) control how components are arranged and resized.
4. Combining **text fields, graphics, and interactors** allows for more dynamic, interactive programs.

This lecture demonstrated how to build **more complex GUIs** with multiple types of components, handling user input flexibly with **text fields and buttons**, and organizing components neatly with **layouts**.
