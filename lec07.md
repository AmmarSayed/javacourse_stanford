### **Lecture 7 | Programming Methodology - Summary**

This lecture dives deeper into **looping constructs, casting, methods, and the concept of "loop-and-a-half"**, providing insights into **method decomposition, information hiding, and parameter passing**. It also touches on **returning objects from methods** and **using constants in larger programs**.

[Watch the full lecture here](https://www.youtube.com/watch?v=3oM9yT9kBBc).

---

### **1. Clarification on Casting**

- **Explicit casting** is required when **information loss** occurs (e.g., double to int).
  ```java
  double y = 3.5;
  int x = (int) y;  // Truncates 3.5 to 3
  ```
- No explicit cast needed when converting from a **smaller type to a larger type** (e.g., int to double).
  ```java
  double z = x;  // Automatically converts x (int) to 3.0 (double)
  ```

---

### **2. Loop-and-a-Half Pattern**

- **Indefinite loops** are used when the number of iterations is unknown.
- A **"loop-and-a-half"** executes a task at least once, using `while (true)` with a **break** statement to exit the loop.

#### Example: Loop to Sum User Input Until Zero

```java
public class Add extends ConsoleProgram {
  public static final int SENTINEL = 0;
  
  public void run(){
    int total = 0;
          
    int value = readInt("Enter a number (0 to stop): "); // request at least once

    while (val != SENTINEL) { // check if the value not equal to SENTINEL
        total += value;
        int value = readInt("Enter a number (0 to stop): "); // request for another input
    }
    System.out.println("Total: " + total);
  }
}
```

#### Example: Better Approach, Avoid Repeating Code

```java
public class Add extends ConsoleProgram {
  public static final int SENTINEL = 0;
  
  public void run(){
    int total = 0;
  
    while (true) {
        int value = readInt("Enter a number (0 to stop): ");
        if (value == SENTINEL) break;  // Exit the loop if sentinel value is entered
        total += value;
    }
    System.out.println("Total: " + total);
  }
}
```

- **Key Points:**
  - The **`while (true)`** loop ensures the body executes at least once.
  - The **break statement** exits the loop when a certain condition is met.

---

### **3. Comparison of `for` and `while` Loops**

- **For Loops**: Used when the number of iterations is known **(definite iteration)**.
  ```java
  for (int i = 0; i < 5; i++) {
      System.out.println(i);
  }
  ```
- **While Loops**: Used when the number of iterations is unknown **(indefinite iteration)**.
  ```java
  int i = 0;
  while (i < 5) {
      System.out.println(i);
      i++;
  }
  ```

---

### **4. Using Constants in Programs**

- Constants help **reduce errors** and **improve code readability**.
  ```java
  private static final int SENTINEL = 0;
  ```
- **Example:** Using a constant in a loop:
  ```java
  while (true) {
      int value = readInt("Enter a number: ");
      if (value == SENTINEL) break;
  }
  ```

---

### **5. Nesting Loops: Checkerboard Example**

- **Nested loops** are useful for creating **grids** or **checkerboard patterns**.

```java
for (int row = 0; row < 8; row++) {
    for (int col = 0; col < 8; col++) {
        int x = col * squareSize;
        int y = row * squareSize;
        GRect square = new GRect(x, y, squareSize, squareSize);
        square.setFilled((row + col) % 2 != 0);  // Alternate filled squares
        add(square);
    }
}
```

- **Explanation:**
  - The **outer loop** iterates over rows, and the **inner loop** iterates over columns.
  - **Modulus operator** `(row + col) % 2` ensures alternating filled squares.

---

### **6. Methods in Java**

- **Methods** are used to **decompose programs** into smaller, reusable units.

#### Anatomy of a Method:

```java
private int max(int a, int b) {
    if (a > b) return a;
    else return b;
}
```

- **Visibility**: `private` – Accessible only within the class.
- **Return Type**: `int` – The type of value the method returns.
- **Method Name**: `max`.
- **Parameters**: `int a, int b` – Inputs the method operates on.
- **Body**: Contains the logic of the method.

---

### **7. Predicate Methods**

- **Predicate methods** return **Boolean values**.

```java
private boolean isOdd(int n) {
    return n % 2 != 0;
}
```

- This method checks if a number is odd by returning `true` or `false`.

---

### **8. Returning Objects from Methods**

- Methods can **return objects**, not just primitive data types.

#### Example: Method Returning a Circle Object

```java
private GOval createCircle(int x, int y, int radius, Color color) {
    GOval circle = new GOval(x - radius, y - radius, 2 * radius, 2 * radius);
    circle.setFilled(true);
    circle.setColor(color);
    return circle;
}
```

- **Explanation:**

  - This method **creates and returns** a `GOval` object centered at `(x, y)`.
  - The **caller** can use the returned object as needed.

  Example of using the method:

  ```java
  GOval c = createCircle(100, 100, 50, Color.RED); // this gives back a GOval object
  add(c); // add it to the canvas

  // actually you can add it directly to the add method  
  add(createCircle(100, 100, 50, Color.RED));
  ```

---

### **9. Scope of Variables**

- **Variables declared inside methods** are **local** to that method and cannot be accessed outside.

```java
public void example() {
    int x = 5;  // x is only accessible within this method
}
```

- **Variables in loops** also have a limited scope within the loop.
  ```java
  for (int i = 0; i < 10; i++) {
      System.out.println(i);
  }
  // 'i' is not accessible here.
  ```

---

### **10. Example Program: Factorial Calculator**

#### Program to Compute Factorials:

```java
public class FactorialExample extends ConsoleProgram {
    private static final int MAX = 5;

    public void run() {
        for (int i = 0; i <= MAX; i++) {
            System.out.println(i + "! = " + factorial(i));
        }
    }

    private int factorial(int n) {
        int result = 1;
        for (int i = 1; i <= n; i++) {
            result *= i;
        }
        return result;
    }
}
```

- **Explanation:**
  - The `factorial` method computes the factorial of a given number.
  - **Factorial definition**: `n! = 1 * 2 * ... * n`.
  - Example output:
    ```
    0! = 1
    1! = 1
    2! = 2
    3! = 6
    4! = 24
    5! = 120
    ```

---

### **11. Summary of Key Concepts**

- **Loop-and-a-half**: Use `while (true)` with `break` for unknown iteration counts.
- **Nested loops**: Useful for generating **grid-like structures**.
- **Methods**: Enable **decomposition and code reuse**.
- **Returning Objects**: Methods can return **complex objects** like `GOval`.
- **Constants and Scope**: Manage constants and ensure variables have appropriate scopes.

This lecture reinforces **looping, methods, and code structure** to create maintainable programs. Practice using **methods, loops, and predicates** to solve real-world problems in your assignments!
