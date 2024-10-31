### **Lecture 16 | Programming Methodology (Stanford) - Summary**

This lecture introduces **arrays and ArrayLists** in Java, including their syntax, operations, and nuances like pre- and post-increment operators. These are essential concepts for handling collections of data efficiently.

Watch the full lecture [here](https://www.youtube.com/watch?v=FUO3XEUVydk).

---

## **1. Arrays: Overview**

An **array** is a collection of elements of the same type, stored in contiguous memory locations. Arrays help store multiple values of the same data type efficiently.

### **Characteristics of Arrays:**

- **Homogeneous**: All elements in the array must be of the same type.
- **Fixed Size**: Once declared, the size of an array cannot change.
- **Ordered Collection**: Elements are indexed from **0 to (n-1)**.

**Example: Declaring an Array**

```java
int[] myArray = new int[5];  // Array of 5 integers
```

This creates an array with **5 elements**, each initialized to `0` (default for integers).

---

## **2. Accessing and Modifying Array Elements**

### **Using Indexes to Access Elements:**

```java
myArray[0] = 10;  // Assign 10 to the first element
System.out.println(myArray[0]);  // Output: 10
```

- **Indexes start from 0** (common convention in programming).
- If you access an **invalid index**, Java throws an **ArrayIndexOutOfBoundsException**.

---

## **3. Loops and Arrays**

### **Using Loops to Populate Arrays**

You can use **for loops** to iterate over the elements of an array.

```java
for (int i = 0; i < myArray.length; i++) {
    myArray[i] = i * 10;  // Assign multiples of 10 to each element
}
```

This loop assigns the values `0, 10, 20, 30, 40` to the elements of the array.

---

## **4. Pre-Increment vs. Post-Increment Operators**

Java supports two increment forms:

- **Post-increment (x++)**: Increments the value **after returning the current value**.
- **Pre-increment (++x)**: Increments the value **before returning it**.

**Example:**

```java
int x = 5;
int y = x++;  // y gets 5, x becomes 6

int z = ++x;  // x becomes 7, z gets 7
```

- Post-increment is frequently used in **array loops** to traverse elements.

---

## **5. Arrays of Objects**

You can create arrays to store **objects** like `GOval` instances.

```java
GOval[] circles = new GOval[4];  // Array of 4 GOval objects

// Initialize each element
for (int i = 0; i < circles.length; i++) {
    circles[i] = new GOval(0, 0, 100, 100);
}
```

Each element in the array initially holds `null` until you assign an object to it.

---

## **6. Passing Arrays to Methods**

Arrays in Java are **passed by reference**, meaning changes made to the array in a method affect the original array.

**Example: Passing an Array to a Method**

```java
public void modifyArray(int[] arr) {
    arr[0] = 99;  // Modifies the original array
}

int[] myArray = {1, 2, 3};
modifyArray(myArray);
System.out.println(myArray[0]);  // Output: 99
```

---

## **7. Array Size vs. Effective Size**

- **Declared Size**: The size of the array when declared.
- **Effective Size**: The number of elements actively used in the array.

**Example: Managing Effective Size**

```java
int[] scores = new int[500];  // Declared size
int numScores = 0;  // Effective size (how many scores we use)

// Adding a score
scores[numScores++] = 95;
```

---

## **8. Handling Sentinel Values**

A **sentinel value** is a special value used to indicate the **end of input**.

**Example: Using a Sentinel Value**

```java
while (true) {
    int score = readInt("Enter score: ");
    if (score == -1) break;  // Sentinel value to stop input
    scores[numScores++] = score;
}
```

---

## **9. ArrayLists: Dynamic Arrays**

Unlike arrays, **ArrayLists** can **grow and shrink dynamically**. They are part of the `java.util` package.

### **Declaring an ArrayList**

```java
import java.util.ArrayList;

ArrayList<String> stringList = new ArrayList<>();
```

- **ArrayList** is a **generic class**. You specify the type of elements using **angle brackets** (`<>`).

---

### **Common Methods of ArrayList:**

1. **Adding Elements**:

   ```java
   stringList.add("Hello");
   stringList.add("World");
   ```

   This appends elements to the end of the list.

2. **Getting Elements**:

   ```java
   String greeting = stringList.get(0);  // "Hello"
   ```

3. **Checking the Size**:

   ```java
   int size = stringList.size();  // Number of elements in the list
   ```

4. **Removing Elements**:
   ```java
   stringList.remove(1);  // Removes the element at index 1
   ```

---

## **10. Example: ArrayList Usage in Hangman**

For Part 3 of the **Hangman assignment**, you'll use an `ArrayList` to store guessed letters dynamically.

**Example: Using ArrayList in Hangman**

```java
ArrayList<Character> guessedLetters = new ArrayList<>();

// Add a guessed letter
guessedLetters.add('A');

// Check if a letter was guessed
if (guessedLetters.contains('A')) {
    System.out.println("Letter A was guessed.");
}
```

---

## **11. Avoiding Common Array Errors**

- **ArrayIndexOutOfBoundsException**: Occurs if you try to access an element outside the array’s bounds.
- **NullPointerException**: Happens if you try to access an object that has not been initialized.

---

## **12. Summary and Key Takeaways**

1. **Arrays**: Fixed-size, homogeneous collections, passed by reference.
2. **Pre-/Post-Increment Operators**: Useful in loops and array operations.
3. **Effective vs. Declared Size**: Manage effective size to avoid accessing uninitialized elements.
4. **ArrayList**: A dynamic alternative to arrays, allowing for flexible resizing and element management.
5. **Passing Arrays**: Arrays are passed by reference, so modifications in methods persist outside.

---

This lecture covers foundational concepts necessary for managing collections of data, whether through **arrays** or **ArrayLists**, and prepares you for **real-world applications** like Hangman.
