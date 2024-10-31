### **Lecture 15 | Programming Methodology - Summary**

This lecture builds on the **concepts of pointers and memory** from the previous session, focusing on **references, object mutability, and file handling in Java**. Below is a structured summary of key topics covered.

Watch the full lecture [here](https://www.youtube.com/watch?v=ttbu9L4RdYs).

---

## **1. Memory Management Recap: Pointers and References**

### **References vs. Primitive Types**

- **Primitive Types:**

  - Data types like `int`, `double`, `char`, and `boolean`.
  - When passed to a method, **a copy** of the value is made (pass-by-value). Changes within the method **don’t affect the original variable**.

- **Object References:**
  - **Objects** are stored on the **heap**, and **references (pointers)** to these objects are stored on the **stack**.
  - When an **object** is passed to a method, **the reference (memory address)** is passed (pass-by-reference).
  - Changes made to the object **affect the original** because the reference points to the same memory location.

**Example:**

```java
Point p1 = new Point(1, 1);
Point p2 = p1;  // p2 points to the same object as p1.
p2.move(3, 4);  // This changes both p1 and p2, as they refer to the same memory location.
```

---

## **2. Null Dereference Errors**

If an object reference **points to null** (no actual object), calling a method on it leads to a **null dereference error**.

**Example:**

```java
Point p3;  // p3 is declared but not initialized.
p3.move(4, 5);  // Null dereference error! p3 points to nothing.
```

**Key Concept:**

- Always **initialize objects** before calling methods to avoid null pointer exceptions.

---

## **3. Encapsulation of Primitive Types**

Java provides **wrapper classes** for primitive types to allow them to behave like objects:

| Primitive Type | Wrapper Class |
| -------------- | ------------- |
| `int`          | `Integer`     |
| `double`       | `Double`      |
| `boolean`      | `Boolean`     |
| `char`         | `Character`   |

- These classes are **immutable**—once a value is set, it cannot be changed.
- To modify a value, a **new object must be created** with the updated value.

---

## **4. Introduction to File Handling in Java**

Java allows **reading from and writing to files**, essential for working with data outside the program.

### **Key Steps in File Handling**

1. **Open a File:**

   - Use a **BufferedReader** to read files.
   - Use a **PrintWriter** to write files.

2. **Read or Write Data:**

   - Use a **while loop** to read or write lines sequentially.

3. **Close the File:**
   - Always **close files** to free resources.

---

## **5. Reading Files with `BufferedReader`**

### **Code Example: Reading a File Line by Line**

```java
import java.io.*;

BufferedReader rd = new BufferedReader(new FileReader("students.txt"));

while (true) {
    String line = rd.readLine();  // Read next line
    if (line == null) break;  // End of file
    System.out.println(line);  // Print the line
}

rd.close();  // Close the file
```

**Explanation:**

- **`readLine()`** returns the next line from the file. If it reaches the **end of the file**, it returns `null`.
- Use a **while loop** to read all lines until `null` is encountered.
- **Always close the file** using `rd.close()`.

---

## **6. Writing Files with `PrintWriter`**

### **Code Example: Writing to a File**

```java
import java.io.*;

PrintWriter wr = new PrintWriter(new FileWriter("copy.txt"));

wr.println("This is a new line.");
wr.close();  // Close the file
```

**Key Concepts:**

- **`PrintWriter`** allows easy writing to files using `println()` just like printing to the console.
- If a file **already exists**, it will be **overwritten** without warning.

---

## **7. Handling Exceptions with `try-catch`**

When working with **files**, errors (like missing files) may occur. Java handles these using **exceptions**.

### **Code Example: Handling Exceptions with `try-catch`**

```java
import java.io.*;

try {
    BufferedReader rd = new BufferedReader(new FileReader("students.txt"));
    // Read file content here
    rd.close();
} catch (IOException ex) {
    System.out.println("Error: File not found.");
}
```

**Explanation:**

- If the file doesn’t exist, a **`FileNotFoundException`** or **`IOException`** is thrown.
- The **`try-catch` block** catches the exception and allows the program to **continue without crashing**.

---

## **8. Reusing Code: Encapsulating File Operations in a Method**

### **Code Example: Opening a File Safely**

```java
private BufferedReader openFile(String prompt) {
    BufferedReader rd = null;
    while (rd == null) {
        try {
            String name = readLine(prompt);
            rd = new BufferedReader(new FileReader(name));
        } catch (IOException ex) {
            System.out.println("Invalid file. Try again.");
        }
    }
    return rd;
}
```

**Explanation:**

- This method **prompts the user for a filename** and tries to open it.
- If the file doesn’t exist, it **catches the exception** and asks the user to try again.
- This method ensures that **only a valid file** is opened.

---

## **9. Copying Files Using Java**

### **Code Example: Copying a File Line by Line**

```java
BufferedReader rd = new BufferedReader(new FileReader("students.txt"));
PrintWriter wr = new PrintWriter(new FileWriter("copy.txt"));

while (true) {
    String line = rd.readLine();
    if (line == null) break;
    wr.println(line);  // Write line to new file
}

rd.close();
wr.close();
```

**Explanation:**

- This program **reads each line** from the input file (`students.txt`) and **writes it** to the output file (`copy.txt`).
- **Careful:** If `copy.txt` already exists, it will be **overwritten** without warning.

---

## **10. Throwing Exceptions in Java**

In some cases, your program might encounter exceptions that it **doesn’t know how to handle**. In such cases, you can **rethrow the exception** to let another part of the program handle it.

**Example: Rethrowing an Exception**

```java
try {
    // Some risky code
} catch (IOException ex) {
    throw new RuntimeException("Unexpected error", ex);
}
```

---

## **11. Key Takeaways**

1. **Objects and References:**

   - Understand how **object references** work and avoid **null pointer exceptions**.
   - Remember that **assigning one object reference to another** makes them point to the **same memory location**.

2. **File Handling:**

   - Use **BufferedReader** to read files and **PrintWriter** to write files.
   - **Always close files** after use to avoid resource leaks.
   - Be cautious when **writing to existing files** to avoid accidental overwriting.

3. **Exception Handling:**
   - Use **try-catch blocks** to gracefully handle errors.
   - **Rethrow exceptions** when you don’t know how to handle them.

---

This lecture offers essential insights into **memory management, references, and file handling**, equipping you with tools to manage files and avoid common programming pitfalls.
