### **Lecture 18 | Programming Methodology (Stanford) - Summary**

In this lecture, the focus is on **multi-dimensional arrays**, the **distinction between arrays and ArrayLists**, and an in-depth introduction to **debugging techniques**. The lecture also covers practical examples of using **Eclipse's debugger** to identify and solve bugs efficiently.

Watch the full lecture [here](https://www.youtube.com/watch?v=9xnLnDa04dM).

---

## **1. Multi-Dimensional Arrays: Deep Dive**

A **2D array** is an **array of arrays**, where each row itself is a 1D array. This structure allows programmers to pass specific **sub-arrays** as parameters to functions.

### **Example: Creating a 2x100 Array**

```java
int[][] scores = new int[2][100];
```

- **Accessing a single row (sub-array):**
  ```java
  int[] midtermScores = scores[0];  // Passable as a 1D array
  ```
- **Iterating through the array:**
  ```java
  for (int i = 0; i < scores.length; i++) {
      for (int j = 0; j < scores[i].length; j++) {
          scores[i][j] = 0;  // Initialize with zeros
      }
  }
  ```

This emphasizes that each row of a 2D array behaves as a **1D array**.

---

## **2. Arrays vs. ArrayLists: Pros and Cons**

### **Arrays:**

- **Pros:**
  - **Efficient** in memory and performance.
  - **Simple syntax** for element access.
  - Ideal when **size is fixed** or known in advance.
- **Cons:**
  - **Fixed size**; cannot dynamically grow or shrink.

### **ArrayLists:**

- **Pros:**

  - **Dynamic resizing**, which makes it suitable for collections with unknown size.
  - Provides **high-level methods** like `contains()` and `add()`.

- **Cons:**
  - **Less efficient** than arrays.
  - **Bulky syntax** when modifying elements.

### **When to Use Which?**

- **Use arrays** when the size is known or fixed.
- **Use ArrayLists** when the size needs to be flexible.

---

## **3. Debugging Techniques: Philosophy and Tools**

The latter part of the lecture is devoted to the **art and science of debugging**, with a practical demonstration using **Eclipse’s debugger**.

### **Debugging Mindset:**

1. **Don’t panic**: Bugs are predictable and can be traced.
2. **Systematic approach**: Avoid randomly guessing where the bug might be.
3. **Question assumptions**: Even simple code can contain subtle errors.
4. **Be critical**: Review your code carefully, even the parts you assume are error-free.

### **Common Causes of Bugs:**

1. **Bad variable values**: Unexpected data in variables.
2. **Faulty logic**: Incorrect implementation of logic.
3. **Unwarranted assumptions**: Misconceptions about input or behavior.

---

## **4. Practical Debugging with Eclipse:**

In the lecture, a **Roulette game program** is used to demonstrate **how to debug using Eclipse’s tools**.

### **Common Debugging Tools in Eclipse:**

- **Breakpoints**: Pauses the program at a specific line to inspect variable values.
- **Step over**: Execute the current line and move to the next.
- **Step into**: Dive into a method call to inspect its execution.
- **Step out**: Exit the current method and return to the calling method.

### **Roulette Example - Identifying Bugs:**

1. **Setting a Breakpoint**:

   - A **breakpoint** is set inside the logic where the game determines if the player's bet wins or loses.

2. **Running in Debug Mode**:

   - After setting the breakpoint, the program is run in **debug mode** to pause execution and inspect variable values.

3. **Identifying the Bug**:

   - The bet was on **even numbers**, but the program incorrectly marked **2** as a loss.
   - The issue was identified as **string comparison** using `==` instead of `.equals()`.

   **Fix:**

   ```java
   if (bet.equalsIgnoreCase("even") && outcome % 2 == 0 && outcome != 0) {
       // Correct logic for even number bets
   }
   ```

4. **Using the Debugger to Track Variable Values**:
   - The lecture demonstrates **stepping through the code** and inspecting variables like `outcome` to ensure the logic is working as expected.

---

## **5. Key Takeaways:**

1. **Print Statements** are powerful:

   - Use them to trace **variable values** and identify where things go wrong.

2. **Use Debugger Tools**:

   - Setting **breakpoints** and **stepping through code** helps you track the flow and logic of your program.

3. **Unit Testing**:

   - Test individual functions with known inputs to ensure they behave as expected before running the entire program.

4. **Bugs Are Inevitable**:

   - The focus should be on **systematic debugging** rather than relying on luck or guesswork.

5. **Random Numbers and Debugging**:
   - If your code involves randomness, **set the seed** for your random generator to get predictable results during testing.

---

This lecture provides essential tools and practices for **systematic debugging**, making it clear that solving bugs is a methodical process. The practical examples and debugger usage in **Eclipse** give students the confidence to trace issues effectively.
