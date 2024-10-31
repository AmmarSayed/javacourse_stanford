### **Lecture 14 | Programming Methodology - Summary**

This lecture dives deep into **computer memory management**, explaining how memory works in programming, particularly focusing on **Java**. The discussion covers fundamental topics such as **bits, bytes, hexadecimal representation, heap vs. stack memory**, and object management. The lecture emphasizes the importance of understanding memory to avoid common programming pitfalls.

Watch the full lecture [here](https://www.youtube.com/watch?v=W8nNdNZ40EQ).

---

## **1. Bits, Bytes, and Memory Units**

**Bits and Bytes:**

- **Bit:** The smallest unit of memory, representing a **0 or 1** (binary digit).
- **Byte:** A group of **8 bits**.
- **Word:** A unit of memory, typically **4 bytes (32 bits)** on many systems, which is often used to store integers.

**Larger Memory Units:**

- **Kilobyte (KB):** 1024 bytes (2¹⁰).
- **Megabyte (MB):** 1024 KB (2²⁰).
- **Gigabyte (GB):** 1024 MB (2³⁰).
- **Terabyte (TB):** 1024 GB (2⁴⁰).
- **Petabyte (PB), Exabyte (EB), Zettabyte (ZB), Yottabyte (YB):** Higher orders of memory units.

> Fun fact: The **Library of Congress**'s collection is approximately **10 TB** of data, while all **spoken words by humanity** are estimated to require around **5 EB** of storage.

---

## **2. Hexadecimal and Memory Representation**

Computers often represent memory addresses in **hexadecimal (base 16)** to simplify reading large binary values.

- **Hexadecimal Format:**
  - **Digits:** 0–9, followed by letters **A–F** (representing 10–15).
  - **Example:** The hexadecimal number **2B** is equivalent to **43** in decimal (2 × 16 + 11).

**Memory Layout:**

- Memory addresses are stored in **hexadecimal** to differentiate **locations** from the actual data stored in memory.

---

## **3. Understanding Memory Allocation: Stack vs. Heap**

### **Static Variables / Constants**

- Stored in a **special memory section** at program startup.
- Their values are fixed and accessible throughout the program’s lifecycle.

### **Heap Memory**

- Stores **dynamically allocated objects** created using the `new` keyword.
- **Garbage collection** reclaims memory once the object is no longer referenced.
- **Heap grows downward** in memory, starting from a high address.

### **Stack Memory**

- Stores **local variables** and **method parameters**.
- Each function call generates a **stack frame** containing its local data.
- When the function returns, the **stack frame is popped off** the stack.
- **Stack grows upward** from high to low memory addresses.

**Diagram:**

```
Heap (grows downward)
   |
   |
Static Variables/Constants
   |
Stack (grows upward)
```

---

## **4. Java's Memory Model: Objects and Variables**

### **Objects and the Heap**

- When you create an object using `new`, it is allocated on the **Heap**.
- Example:

```java
Point p1 = new Point(2, 3);
```

- The **address** of the object is stored in the **local variable** on the **stack**. For instance, `p1` stores the **address of the Point object** on the Heap.

---

### **Stack Frame and Method Calls**

- When a method is invoked, a **stack frame** is created on the stack.
- The **this pointer** is implicitly passed to refer to the object that called the method.

**Example: Method Call Stack Frame**

```java
p1.move(10, 11);
```

- **`this` pointer:** Stores the address of the calling object (`p1`).
- **Parameters (`dx`, `dy`):** Stored locally in the stack frame.

**Memory Layout Example:**

- **Heap**: `p1` object with instance variables (`x`, `y`).
- **Stack**: Method call frame containing the `this` pointer and parameters.

---

## **5. Key Concept: Pointer Semantics**

In Java, **variables that refer to objects** store **memory addresses** (pointers) to the actual objects in the Heap.

**Example:**

```java
Point p1 = new Point(2, 3);
Point p2 = p1;  // p2 points to the same object as p1.
p2.move(10, 10);  // Modifies the same object.
```

- **Both `p1` and `p2` point to the same memory location**. Modifying `p2` affects `p1` as well, since they reference the same object.

---

## **6. String Comparison and Object Identity**

Since **strings are objects**, the **`==` operator** compares the **memory addresses** (not the content).

**Incorrect String Comparison:**

```java
String s1 = "hello";
String s2 = "hello";
System.out.println(s1 == s2);  // False, different memory addresses.
```

**Correct String Comparison:**

```java
System.out.println(s1.equals(s2));  // True, compares content.
```

- Use **`.equals()`** to compare **content**, not **memory addresses**.

---

## **7. Practical Example: Managing Object Memory**

**Creating and Assigning Objects:**

```java
Point p1 = new Point(1, 1);
Point p2 = p1;  // p2 points to the same object.
```

- **Both `p1` and `p2`** store the **same memory address**.
- **Modifying one** affects the other since they **share the same reference**.

---

## **8. Garbage Collection**

Java's **garbage collector** reclaims memory that is no longer referenced.

- If no variable points to an object, the memory is **"garbage"** and will be **reclaimed**.
- **Developers do not need to manually free memory**, unlike languages like C or C++.

---

## **9. Recap: Memory Management Overview**

1. **Stack vs. Heap:**

   - **Stack:** Local variables, method parameters, grows upward.
   - **Heap:** Dynamically allocated objects, grows downward.

2. **Pointers and References:**

   - Variables store **addresses** of objects.
   - Multiple variables can **point to the same object**, leading to shared state.

3. **Garbage Collection:**

   - Java automatically reclaims unused memory.

4. **Correct String Comparison:**
   - Use **`.equals()`** to compare string contents.

---

## **Conclusion**

This lecture provides a comprehensive understanding of **memory management** in Java, a crucial skill for developing efficient software. It emphasizes the **differences between stack and heap memory**, explains how **objects are managed** using pointers, and highlights the importance of **understanding memory allocation** to avoid common bugs.

Understanding these concepts will help you write better code by knowing **how memory works behind the scenes**, avoiding **unintentional object sharing**, and **leveraging garbage collection** effectively.
