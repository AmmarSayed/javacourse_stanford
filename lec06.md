### **Lecture 6 | Programming Methodology - Summary**

This lecture focuses on **arithmetic operations, input handling, Boolean logic, loops, and constants** in Java. It provides insights into handling **user input, expressions, data types, and control structures** such as **if-statements, switch statements, and loops**.

[Watch the full lecture here](https://www.youtube.com/watch?v=GPWah4wbwYs).

---

### **1. Handling User Input**

- **`readInt()`**: Reads an integer input from the user.
- **`readDouble()`**: Reads a double (real number) input from the user.
  ```java
  int num = readInt("Enter an integer: ");
  double value = readDouble("Enter a decimal number: ");
  ```

---

### **2. Arithmetic Operations and Division in Java**

- **Operators**: Java supports standard arithmetic operators:

  - **`+`**: Addition
  - **`-`**: Subtraction
  - **`*`**: Multiplication
  - **`/`**: Division
  - **`%`**: Remainder (modulus operator)

- **Integer vs Real Division**:

  - **Integer Division**: If both operands are integers, the result is an integer (fractional part is discarded).
    ```java
    int result = 5 / 2; // result = 2
    ```
  - **Real Division**: If either operand is a double, the result is a double.
    ```java
    double result = 5 / 2.0; // result = 2.5
    ```

- **Casting**: Temporarily treat a variable as a different type.

  ```java
  double y = (double) x / 2; // Ensures real division
  ```

- **Truncation with Casting**: Casting from double to int removes the fractional part.
  ```java
  double val = 2.9;
  int truncated = (int) val; // truncated = 2
  ```

---

### **3. Precedence of Operators**

- Operators follow standard rules of **precedence**:
  1. **Parentheses** `( )`: Evaluate first.
  2. **Multiplication, Division, and Modulus**: Evaluated from left to right.
  3. **Addition and Subtraction**: Evaluated last, from left to right.

Example:

```java
int x = 1 + 3 * 5 / 2; // x = 8
```

- **Use parentheses** to control evaluation order:
  ```java
  int result = (1 + 3) * 5 / 2; // result = 10
  ```

---

### **4. Constants in Java**

- Use **constants** to store values that don't change during execution.
  - **Syntax**: Declare constants using `final` and `static`.
  ```java
  private static final double PI = 3.14159;
  ```
- **Advantages of Constants**:
  1. Improves **code readability**.
  2. Prevents accidental changes to important values.
  3. **Centralizes** values, making them easy to update.

### **Definitions:**

#### 1. `public`

- **Accessibility**: A `public` field, method, or class is accessible from **anywhere in your code**—both inside the same package and from other packages.
- **Use case**: You generally use `public` for methods and constants that you want accessible from outside the class, like a public API.

#### 2. `private`

- **Accessibility**: A `private` field or method is accessible **only within the class it’s defined in**. Other classes, even in the same package, can’t access it.
- **Use case**: `private` is typically used to restrict access to fields and helper methods that shouldn’t be accessible from outside the class. It helps with **encapsulation** (hiding the internal implementation details).

#### 3. `static`

- **Behavior**: A `static` field or method belongs to the **class itself**, not to instances (objects) of the class.
- **Use case**:
  - **Static fields** are shared across all instances of the class, so if one instance changes the value, all other instances see the change. This is commonly used for **constants** (like `static final` values) or shared data, such as a counter.
  - **Static methods** can be called directly on the class, without needing an instance. Utility methods like `Math.sqrt()` are static because they don’t require an instance.

#### 4. `final`

- **Behavior**: The `final` keyword is used to declare **constants** or to **prevent modification**.
- **Use case**:
  - **Final variables**: If you declare a variable as `final`, you can assign it a value only once, either at the point of declaration or in the constructor if it’s an instance variable.
  - **Final methods**: Declaring a method as `final` prevents subclasses from overriding it.
  - **Final classes**: If a class is declared `final`, it cannot be subclassed (extended), which can be useful for security or optimization reasons.

#### Example

```java
public class Example {
    public static final int MAX_USERS = 100; // Constant (unchangeable and shared across instances)

    private String name; // Instance variable, accessible only within this class

    public Example(String name) {
        this.name = name; // Constructor to initialize the `name`
    }

    public String getName() {
        return this.name; // Public method, accessible from outside
    }

    public static void greet() {
        System.out.println("Hello from a static method!");
    }
}
```

In this example:

- `MAX_USERS` is a constant shared by all instances.
- `name` is a `private` variable, so it can only be accessed or modified within the `Example` class.
- `getName()` is a `public` method, allowing other classes to read `name`.
- `greet()` is a `static` method and can be called as `Example.greet()` without creating an instance of `Example`.

---

### **5. Boolean Logic and Expressions**

- **Boolean Variables**: Store `true` or `false` values.

  ```java
  boolean isActive = true;
  ```

- **Comparison Operators**:

  - `==`: Equals
  - `!=`: Not equals
  - `>`: Greater than
  - `<`: Less than
  - `>=`: Greater than or equal to
  - `<=`: Less than or equal to

- **Logical Operators**:

  - **`!`**: NOT – Inverts a Boolean value.
  - **`&&`**: AND – True if both operands are true.
  - **`||`**: OR – True if at least one operand is true.

- **Example of Boolean Logic**:

  ```java
  boolean isValid = (x != 1) && (x != 2);
  ```

- **Short-circuit Evaluation**: Java stops evaluating logical expressions as soon as the result is known.

  ```java
  boolean result = (5 > 3) || (4 < 2); // Second part is not evaluated.
  ```

- **Excample of useful case:**

```java
  p = (x != 0) && ((y/x) == 0); // Avoid division by 0. since ((y/x) == 0) is not preformed
```

---

### **6. Control Structures: If-Else and Switch Statements**

- **If-Else Statement**:

  ```java
  if (x % 2 == 0) {
      System.out.println("Even");
  } else {
      System.out.println("Odd");
  }
  ```

- **Cascading If-Else**:

  ```java
  if (score >= 90) {
      System.out.println("A");
  } else if (score >= 80) {
      System.out.println("B");
  } else {
      System.out.println("F");
  }
  ```

- **Switch Statement**: Used for multiple fixed options.
  ```java
  int day = readInt("Enter day (0-6): ");
  switch (day) {
      case 0: System.out.println("Sunday"); break;
      case 1: System.out.println("Monday"); break;
      default: System.out.println("Invalid day");
  }
  ```

---

### **7. Loops in Java**

#### **For Loop**

- Executes a block of code **a specific number of times**.

  ```java
  for (int i = 0; i < 5; i++) {
      System.out.println(i);
  }
  ```

- **Loop with Step Changes**:
  ```java
  for (int i = 6; i > 0; i -= 2) {
      System.out.println(i);
  }
  ```

#### **While Loop**

- Repeats as long as a condition is true.
  ```java
  int x = 15;
  while (x > 1) {
      System.out.println(x);
      x /= 2;
  }
  ```

---

### **8. Scope and Lifetime of Variables**

- **Scope**: The area of the program where a variable is accessible.
  - Variables **declared inside a loop or block** exist only within that block.
  ```java
  for (int i = 0; i < 5; i++) {
      System.out.println(i);
  }
  // 'i' is no longer accessible here.
  ```

---

### **9. Shorthand for Arithmetic Operations**

- **Increment and Decrement**:

  ```java
  x++; // Equivalent to x = x + 1;
  x--; // Equivalent to x = x - 1;
  ```

- **Compound Assignment Operators**:
  ```java
  x += 5; // Equivalent to x = x + 5;
  x -= 3; // Equivalent to x = x - 3;
  x *= 2; // Equivalent to x = x * 2;
  x /= 2; // Equivalent to x = x / 2;
  ```

---

### **10. Summary of Key Concepts**

- **Division**: Use casting or doubles to avoid integer division issues.
- **Constants**: Use `final` constants to prevent value changes.
- **Boolean Logic**: Use logical operators (`&&`, `||`, `!`) for conditions.
- **If-Else and Switch**: Control the flow of the program based on conditions.
- **Loops**: Use **for** and **while** loops for repetition, with careful attention to variable scope.

This lecture expands your understanding of **control structures, expressions, loops, and user input**, setting a foundation for more complex programming tasks. Practice using **arithmetic operations and control statements** to deepen your grasp of Java.
