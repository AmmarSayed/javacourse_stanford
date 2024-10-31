### Summary of Lecture 2 | Programming Methodology (Stanford)

In this lecture, the professor introduces key programming concepts using **Karel the Robot** as a learning tool. The lecture focuses on basic commands, the structure of Karel programs, loops, conditionals, and good programming practices.

[Lecture 2 | Programming Methodology (Stanford) - YouTube](https://www.youtube.com/watch?v=0LoKDDRlfZc)

---

### **Key Topics Covered**

#### **Karel’s Basic Commands (Methods)**

Karel understands a limited set of basic commands:

1. **`move()`**: Moves Karel one step forward in the direction it is facing.
2. **`turnLeft()`**: Turns Karel 90 degrees to its left.
3. **`pickBeeper()`**: Picks up a beeper from Karel's current position.
4. **`putBeeper()`**: Places a beeper on the current corner.

---

#### **Creating and Running a Karel Program**

1. **Writing Karel Programs**:

   - The logic for Karel's behavior is encapsulated in a **`run()`** method.
   - **Syntax**: Each command is written with parentheses and followed by a semicolon (e.g., `move();`).

2. **Karel’s Program Structure**:

   - A Karel program needs to be defined as a **class** that extends the base `Karel` class:

     ```java
     import stanford.karel.*;

     public class MyKarelProgram extends Karel {
         public void run() {
             move();
             pickBeeper();
         }
     }
     ```

   - The **`import` statement** brings in predefined Karel behaviors from the Stanford library.

3. **Tabs and Indentation**:
   - Indentation makes the code readable, helping programmers understand which lines belong to a specific method or loop.

---

#### **Programming Concepts with Karel**

##### **Decomposition with Methods**:

- You can create new commands (methods) using **modular decomposition**:
  ```java
  private void turnRight() {
      turnLeft();
      turnLeft();
      turnLeft();
  }
  ```
- This improves readability and allows code reuse.

##### **Loops**:

1. **For Loop**: Use when you know the exact number of times a task needs to repeat.

   ```java
   for (int i = 0; i < 3; i++) {
       turnLeft();
   }
   ```

   - This loop turns Karel left three times (equivalent to a right turn).

2. **While Loop**: Use when the number of repetitions depends on a condition.
   ```java
   while (frontIsClear()) {
       move();
   }
   ```
   - Karel keeps moving forward until it hits a wall.

---

#### **Using Conditionals in Karel Programs**

1. **If Statement**:

   - Executes a block of code if a condition is true.

   ```java
   if (beepersPresent()) {
       pickBeeper();
   }
   ```

2. **If-Else Statement**:
   - Executes one block if the condition is true, another block if it is false.
   ```java
   if (beepersPresent()) {
       pickBeeper();
   } else {
       putBeeper();
   }
   ```

---

#### **Example Programs**

1. **Moving and Placing Beepers**:

   - The professor demonstrates a simple program where Karel moves to a corner, picks up a beeper, and places it elsewhere.

2. **Steeplechase Program**:
   - Karel navigates a series of hurdles of unknown heights. This example emphasizes the use of:
     - **For loops**: To ensure Karel checks all avenues.
     - **While loops**: To ascend and descend each hurdle.
     - **Decomposition**: Breaking the program into smaller methods like `jumpHurdle()` and `moveToWall()`.

---

#### **Programming Principles Emphasized**

1. **Readability and Software Engineering**:

   - Programs should be **readable** and easy for humans to understand.
   - Clear method names and modular design make programs maintainable.

2. **Handling Errors**:

   - If Karel tries to perform an invalid action (e.g., walking into a wall), the program crashes with an error.
   - Using **conditions** (e.g., `frontIsClear()`) ensures safe execution.

3. **Reusable Code**:
   - Use methods to **encapsulate repetitive behavior** (e.g., `turnRight()`), making the code cleaner and easier to maintain.

---

#### **Introduction to SuperKarel**

- **SuperKarel** is an enhanced version of Karel with additional built-in commands:
  - `turnRight()` and `turnAround()` are predefined in **SuperKarel**.
  - This reduces the need to manually define these frequently used commands.

---

### **Conclusion and Key Lessons**

This lecture introduced core programming concepts in an approachable way through Karel the Robot:

- **Loops**, **conditionals**, and **methods** are essential for creating flexible and reusable programs.
- **Decomposition** and **readability** are crucial in good software engineering.
- **Practice**: The students are encouraged to experiment with small, well-defined programs to build confidence in programming.

The lecture emphasizes that **writing readable code for humans** is more important than simply getting the computer to execute instructions correctly. This lesson sets the foundation for future assignments and more advanced programming with Java.
