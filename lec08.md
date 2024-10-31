### **Lecture 8 | Programming Methodology - Summary**

This lecture explores **information hiding, parameter passing, local vs. instance variables**, and **random number generation** in programming. The analogies (toasters, gift shops, etc.) emphasize how **methods, variables, and objects** operate independently yet interact efficiently.

Watch the full lecture [here](https://www.youtube.com/watch?v=W2ysz_6AyJE).

---

## **1. Information Hiding and Methods**

- **Information hiding** abstracts the complexity of operations.
  - Example: A **toaster** hides how bread is turned into toast – the user only interacts with inputs (bread) and outputs (toast).
- The idea: **Users don't need to know how methods work internally**, only their inputs and outputs.

```java
private void intro() {
    System.out.println("Welcome to the program!");
}
```

- **Void methods** like `intro` do not return values and don't require a `return` statement unless you explicitly use `return;` to exit early.

---

## **2. Parameter Passing and Local Variables**

- When passing **parameters to a method**, **only a copy** of the value is passed – **not the actual variable**. This is known as **pass-by-value**.

### Example: Pass-by-Value

```java
public void run() {
    int x = 3;
    addFive(x);  // Passes a copy of x
    System.out.println(x);  // Still prints 3
}

private void addFive(int x) {
    x += 5;  // Modifies the local copy
}
```

- **Explanation:** The original `x` in `run` is unaffected by changes inside `addFive` because only a **copy** is passed.

---

## **3. Returning Values from Methods**

- To modify a variable in a calling method, you need to **return the modified value** and **assign it back**.

### Example: Returning a Modified Value

```java
public void run() {
    int x = 3;
    x = addFive(x);  // Assign the returned value
    System.out.println(x);  // Prints 8
}

private int addFive(int x) {
    return x + 5;
}
```

---

## **4. Local Variables vs. Instance Variables**

### **Local Variables:**

- Declared **inside a method** and only accessible within that method.
- **Destroyed** when the method finishes.

### **Instance Variables:**

- Declared **outside methods but inside a class**.
- **Accessible to all methods** within the class.
- **Persist** as long as the object exists.

### Example: Declaring Instance Variables

```java
public class WaterBottle {
    private double fullness;  // Instance variable

    public void fill(double amount) {
        fullness = amount;
    }

    public double getFullness() {
        return fullness;
    }
}
```

- Each **instance** of `WaterBottle` gets its own `fullness` variable.

---

## **5. Random Number Generation**

- Random numbers are useful in games and simulations.
- **Java's Random Generator** is part of the **ACM libraries** and can produce random values of different types.

### How to Use the Random Generator

```java
import acm.util.*;

public class SimpleRandom extends ConsoleProgram {
    private RandomGenerator rgen = RandomGenerator.getInstance();

    public void run() {
        int roll = rgen.nextInt(1, 6);  // Simulate dice roll
        System.out.println("You rolled: " + roll);
    }
}
```

- **`nextInt(1, 6)`** returns a random integer between 1 and 6 (inclusive).

---

### **6. Random Generator Methods**

- **`nextInt(int low, int high)`**: Returns a random integer between `low` and `high` (inclusive).
- **`nextDouble(double low, double high)`**: Returns a random double in the given range.
- **`nextBoolean()`**: Returns `true` or `false` with equal probability.
- **`nextColor()`**: Returns a random color.

---

## **7. Seeding the Random Generator**

- To generate a **predictable sequence** of random numbers for debugging, you can **set the seed**.

### Example: Setting the Seed

```java
public void run() {
    rgen.setSeed(1);  // Set the seed for repeatable results
    System.out.println("You rolled: " + rgen.nextInt(1, 6));
}
```

- **Explanation:** If you set the same seed, you’ll get the same sequence of random numbers across multiple runs.

---

## **8. Debugging with Random Sequences**

- **Setting a seed** helps you reproduce the same random number sequence across different runs, making debugging easier.

  **Without setting a seed:**

  - Different runs generate different sequences, making bugs hard to find.

  **With a seed:**

  - The sequence is predictable and repeatable, making it easier to trace errors.

---

## **9. Summary of Key Concepts**

- **Methods**: Encapsulate code and hide complexity (like toasters and gift shops).
- **Parameter Passing**: Java uses **pass-by-value**, meaning changes to parameters inside a method do not affect the original variable.
- **Local vs. Instance Variables**:
  - Use **local variables** for short-term calculations.
  - Use **instance variables** to maintain the state of an object between method calls.
- **Random Number Generator**:
  - Use `RandomGenerator` to generate random numbers, doubles, Booleans, and colors.
  - **Set a seed** to generate repeatable sequences for debugging.

---

This lecture emphasizes **good software engineering practices**, including **information hiding, proper use of variables**, and **predictable behavior with random sequences**. With these skills, you'll be better equipped to write modular, reusable, and maintainable code.
