### **Lecture 12 | Programming Methodology - Summary**

This lecture dives into **enumerations, characters, and strings** in Java. It introduces how to create meaningful constants through enumerations, the manipulation of **`char`** data types, and more advanced **string operations**—including **character processing**, **comparison**, and **reversing strings**. The lecture also emphasizes immutability and demonstrates how to use loops for string manipulation. These concepts are essential for text-based processing in Java.

Watch the full lecture [here](https://www.youtube.com/watch?v=GIP9MPFJmhI).

---

## **1. Enumerations: Creating Constants for Clarity**

**Enumerations** provide a way to define meaningful names for a set of related values (like class years or states).

- **Using Constants** to represent values:

  ```java
  public static final int FRESHMAN = 1;
  public static final int SOPHOMORE = 2;
  public static final int JUNIOR = 3;
  public static final int SENIOR = 4;
  public static final int GRADUATE = 5;
  ```

- Instead of using **raw numbers**, constants make the code more readable.

  ```java
  int year = FRESHMAN;
  if (year == JUNIOR) {
      System.out.println("Junior year!");
  }
  ```

- **Switch Statement Example**:
  ```java
  switch (year) {
      case FRESHMAN:
          System.out.println("Freshman");
          break;
      case SOPHOMORE:
          System.out.println("Sophomore");
          break;
      // Other cases...
  }
  ```

The advantage of using constants is that they **improve code clarity** and make it easier to maintain or update logic consistently across a program.

---

## **2. Working with Characters (`char`)**

Java's **`char`** data type stores **single characters** inside **single quotes**.

```java
char letter = 'A';
```

- **Special Characters** (Escape Sequences):
  - `\'` : Single quote
  - `\"` : Double quote
  - `\\` : Backslash
  - `\n` : Newline
  - `\t` : Tab

### **ASCII Table and Character Enumeration**

- Characters like **`A-Z`**, **`a-z`**, and **`0-9`** are **sequential in ASCII**.
  - `'A'` → 65
  - `'a'` → 97
  - `'0'` → 48
- **Operations on Characters**:

  ```java
  char nextChar = (char) (letter + 1);  // 'B'
  ```

- **Character Comparisons**:
  ```java
  if (letter >= 'A' && letter <= 'Z') {
      System.out.println("Uppercase letter");
  }
  ```

---

## **3. String Basics and Operations**

### **Immutability of Strings**

- Strings are **immutable**—once created, they cannot be changed.
- Modifying a string requires creating **new string instances**.

### **Creating Strings**

```java
String greeting = "Hello";
String emptyString = "";
```

- **Concatenation**:

  ```java
  String message = "CS" + 106 + "A";  // "CS106A"
  ```

- **Comparing Strings**:

  - **`==`** checks if two references point to the **same object**.
  - **`.equals()`** checks if two strings **contain the same characters**.

  ```java
  if (greeting.equals("Hello")) {
      System.out.println("Greetings!");
  }
  ```

---

### **Common String Methods**

1. **`length()`**: Returns the length of the string.

   ```java
   int len = greeting.length();  // 5
   ```

2. **`charAt(int index)`**: Returns the character at the specified index.

   ```java
   char firstChar = greeting.charAt(0);  // 'H'
   ```

3. **`substring(int start, int end)`**: Returns a substring from `start` to `end` (exclusive).

   ```java
   String sub = greeting.substring(1, 4);  // "ell"
   ```

4. **`indexOf(char c)`**: Finds the first occurrence of a character.

   ```java
   int index = greeting.indexOf('e');  // 1
   ```

5. **`compareTo(String other)`**: Compares strings lexicographically.
   - Returns **negative** if the first string is less, **zero** if equal, and **positive** if greater.

---

## **4. Iterating Over Strings**

You can **loop through a string** to process each character individually:

```java
for (int i = 0; i < greeting.length(); i++) {
    char ch = greeting.charAt(i);
    System.out.println(ch);
}
```

---

## **5. Example: Converting to Uppercase Manually**

Java provides the **`Character` class** to manipulate characters. Here’s how you could **convert a character to lowercase** manually:

```java
public char toLower(char ch) {
    if (ch >= 'A' && ch <= 'Z') {
        return (char) (ch + ('a' - 'A'));
    }
    return ch;  // Return unchanged if not uppercase
}
```

Alternatively, you can use the **`Character.toLowerCase()`** method:

```java
char lower = Character.toLowerCase('A');  // 'a'
```

---

## **6. Example: Reversing a String**

This method **reverses a string** by building a new string with characters in reverse order:

```java
public String reverseString(String input) {
    String result = "";
    for (int i = 0; i < input.length(); i++) {
        result = input.charAt(i) + result;
    }
    return result;
}
```

- Example:
  - Input: `"stressed"`
  - Output: `"desserts"`

---

## **7. Example: Palindrome Checker**

A **palindrome** reads the same forwards and backwards (e.g., `"racecar"`).

### **Palindrome Check Function**

```java
public boolean isPalindrome(String str) {
    for (int i = 0; i < str.length() / 2; i++) {
        if (str.charAt(i) != str.charAt(str.length() - 1 - i)) {
            return false;
        }
    }
    return true;
}
```

- This function compares characters **from the beginning and the end** moving toward the center.
- **Optimized for odd lengths**—the middle character is automatically skipped.

---

## **8. Key Takeaways**

1. **Enumerations**:

   - Use constants for readability and consistency (e.g., `FRESHMAN = 1`).

2. **Characters (`char`)**:

   - **Characters are primitive** types.
   - They are **enumerated as ASCII values**, which allow mathematical operations.
   - Use **`Character` class methods** for common tasks like checking if a character is a digit or letter.

3. **Strings**:

   - Strings are **immutable**—every modification creates a new string.
   - Use **`.equals()`** for string comparison (instead of `==`).
   - You can **concatenate strings** using `+`.

4. **String Iteration and Manipulation**:

   - Use **loops to process characters**.
   - Common string operations include **substring, indexOf, and compareTo**.

5. **Practical Applications**:
   - Reverse strings.
   - Check if a string is a palindrome.
   - Manipulate and analyze characters within strings.

These topics lay the foundation for text-based programming in Java, including tasks like **input validation**, **string comparison**, and **character processing**—all of which are critical in real-world software development.
