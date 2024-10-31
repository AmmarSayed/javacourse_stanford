### **Lecture 17 | Programming Methodology (Stanford) - Summary**

This lecture dives deeper into **multi-dimensional arrays**, **ArrayLists**, and introduces the concept of **template classes** and **box-unboxing** in Java. There’s also a creative section on manipulating **images as arrays of pixels**, making programming concepts practical and visually engaging.

Watch the full lecture [here](https://www.youtube.com/watch?v=YJ9FlCFi3c8).

---

## **1. Multi-Dimensional Arrays**

A **multi-dimensional array** is essentially an **array of arrays**. These are useful when you need to store data in more than one dimension, like a **matrix**.

### **Example: Declaring a 2D Array (Matrix)**

```java
int[][] matrix = new int[2][3];  // 2 rows, 3 columns

// Assigning values
matrix[0][1] = 5;  // Row 0, Column 1 gets value 5
```

- **Indexing:** `matrix[row][col]`
- A **2x3 matrix** looks like:
  ```
  [ [0, 5, 0],
    [0, 0, 0] ]
  ```

**Iterating through a matrix:**

```java
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        matrix[i][j] = 1;  // Set all elements to 1
    }
}
```

- You can generalize this to **3D arrays** (e.g., `int[][][] cube`) by adding more bracket pairs.

---

## **2. ArrayLists: The Flexible Alternative to Arrays**

**ArrayLists** provide a more dynamic way to store collections of elements. Unlike arrays, **ArrayLists** can grow or shrink automatically.

### **Declaring and Using an ArrayList**

```java
import java.util.ArrayList;

ArrayList<String> stringList = new ArrayList<>();
stringList.add("Hello");
stringList.add("World");
System.out.println(stringList.get(1));  // Output: World
```

- **Advantages:**
  - No need to define the size upfront.
  - Supports **adding, removing, and resizing** dynamically.

---

### **ArrayList Methods:**

1. **Adding elements**:
   ```java
   stringList.add("Stanford");
   ```
2. **Getting elements**:
   ```java
   String item = stringList.get(0);  // "Hello"
   ```
3. **Checking size**:
   ```java
   int size = stringList.size();  // 3
   ```
4. **Removing elements**:
   ```java
   stringList.remove("World");  // Removes "World"
   ```
5. **Clearing all elements**:
   ```java
   stringList.clear();  // List is now empty
   ```

---

## **3. Templates and Wrapper Classes in ArrayLists**

**ArrayLists** only store **objects**, not primitive types. To store primitive values like `int` or `double`, you use **wrapper classes**:

- `int` → `Integer`
- `double` → `Double`
- `boolean` → `Boolean`

**Boxing** and **unboxing** automatically convert between primitives and their wrapper objects.

### **Example: Using ArrayLists with Integers**

```java
ArrayList<Integer> intList = new ArrayList<>();
intList.add(5);  // Automatically boxed to Integer(5)
int x = intList.get(0);  // Automatically unboxed to int
```

This automatic conversion simplifies working with **primitive types in ArrayLists**.

---

## **4. Arrays vs. ArrayLists**

- **Arrays**: Fixed size, better performance.
- **ArrayLists**: Dynamic size, more convenient to use.

Both arrays and ArrayLists can store **objects**:

```java
ArrayList<GLabel> labels = new ArrayList<>();
labels.add(new GLabel("Hello"));
```

---

## **5. Working with Images as Arrays**

In Java, **images are grids of pixels**, where each pixel’s color is encoded as an **integer** with **RGB** values (red, green, blue).

### **Accessing Pixels in a GImage:**

```java
int[][] pixels = image.getPixelArray();
int width = pixels[0].length;  // Number of columns
int height = pixels.length;    // Number of rows
```

---

### **Example: Converting an Image to Grayscale**

1. **Extract RGB values** from each pixel.
2. **Calculate luminosity** using weights:
   - Luminosity = `0.3 * red + 0.6 * green + 0.1 * blue`
3. **Set the RGB values to the same luminosity** to create grayscale.

```java
for (int i = 0; i < height; i++) {
    for (int j = 0; j < width; j++) {
        int pixel = pixels[i][j];
        int red = GImage.getRed(pixel);
        int green = GImage.getGreen(pixel);
        int blue = GImage.getBlue(pixel);

        int luminosity = (int)(0.3 * red + 0.6 * green + 0.1 * blue);
        int grayPixel = GImage.createRGBPixel(luminosity, luminosity, luminosity);
        pixels[i][j] = grayPixel;
    }
}
GImage grayImage = new GImage(pixels);
```

This process converts a color image to **black and white** by equalizing the red, green, and blue components.

---

## **6. Fun with Graphics: Moving Labels**

A creative example from the lecture involves dynamically moving **GLabels** on a canvas to simulate a waterfall effect.

### **Code: Moving Labels Down with Each Click**

```java
ArrayList<GLabel> labels = new ArrayList<>();

// Create and add a new label with each click
public void mouseClicked(MouseEvent e) {
    GLabel label = new GLabel("#" + labels.size());
    label.setFont("Courier-18");
    add(label, 10, 30);

    // Move all existing labels down
    for (GLabel l : labels) {
        l.move(0, label.getHeight());
    }
    labels.add(label);
}
```

With each click, the labels **move down** to make room for the new one, creating a dynamic **waterfall-like effect**.

---

## **7. Key Takeaways from the Lecture**

1. **Multi-dimensional arrays** offer flexibility for working with grids or matrices.
2. **ArrayLists** are a powerful alternative to arrays, providing dynamic resizing and easy-to-use methods.
3. **Templates** and **wrapper classes** enable working with primitive types in ArrayLists.
4. **Images** can be manipulated as arrays of pixels, opening up creative possibilities for graphics programs.
5. Java's **object-oriented features** make it easy to pass and modify arrays, ArrayLists, and objects across methods.

This lecture concludes with fun and practical applications of arrays and ArrayLists, reinforcing concepts while showcasing the **versatility of Java**.
