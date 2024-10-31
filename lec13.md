### **Lecture 13 | Programming Methodology - Summary**

This lecture continues the deep dive into **strings** and **characters** in Java, introducing practical concepts such as **tokenization**, **string replacements**, and **encryption** using the **Caesar Cipher**. These topics build on the previous lecture’s foundation of string manipulation, preparing students for **string-heavy problem sets**.

Watch the full lecture [here](https://www.youtube.com/watch?v=QUrz8-Ltc-s).

---

## **1. Counting Uppercase Characters in a String**

The lecture begins with an example that **counts the number of uppercase characters** in a string using a **for loop** and the **`Character.isUpperCase()`** method.

**Example: Count Uppercase Characters**

```java
private int countUppercase(String str) {
    int count = 0;
    for (int i = 0; i < str.length(); i++) {
        char ch = str.charAt(i);
        if (Character.isUpperCase(ch)) {
            count++;
        }
    }
    return count;
}
```

- **Key Concepts**:
  - Use a **for loop** to iterate through each character.
  - Use **`Character.isUpperCase()`** to check if a character is uppercase.
  - Strings are processed **character by character** to perform tasks like counting.

---

## **2. String Replacement: Implementing Find and Replace**

The lecture covers **replacing a substring** in a larger string, like the **find-and-replace feature** in text editors. The method finds the **first occurrence** of a substring and replaces it with a new string.

### **Algorithm to Replace First Occurrence**

1. **Find the substring's first occurrence** using **`indexOf()`**.
2. **If found**, split the string into **three parts**:
   - Part before the substring.
   - Replacement string.
   - Part after the substring.
3. **Concatenate the three parts** into a new string.

**Example: Replace First Occurrence**

```java
private String replaceOccurrence(String str, String original, String replacement) {
    int index = str.indexOf(original);
    if (index == -1) {
        return str;  // No occurrence found.
    }
    return str.substring(0, index) + replacement +
           str.substring(index + original.length());
}
```

- **Key Points**:
  - **`indexOf()`** finds the first occurrence of a substring.
  - **`substring()`** extracts portions of the string to build the result.
  - This example highlights **immutability**—strings in Java cannot be modified in place.

---

## **3. String Tokenization**

### **What is Tokenization?**

- Tokenization splits a string into smaller pieces called **tokens**, typically separated by **whitespace** or **punctuation**.
- Java provides the **`StringTokenizer` class** to handle tokenization.

**Example: Basic Tokenization**

```java
import java.util.StringTokenizer;

private void printTokens(String line) {
    StringTokenizer tokenizer = new StringTokenizer(line);
    int count = 0;
    while (tokenizer.hasMoreTokens()) {
        System.out.println("Token " + count + ": " + tokenizer.nextToken());
        count++;
    }
}
```

- **Key Methods**:
  - **`hasMoreTokens()`**: Checks if more tokens are available.
  - **`nextToken()`**: Retrieves the next token.

### **Custom Delimiters**

You can provide a **custom delimiter string** to split tokens more flexibly.

```java
StringTokenizer tokenizer = new StringTokenizer(line, ", ");
```

This version uses **commas** and **spaces** as delimiters.

---

## **4. The Caesar Cipher: Simple Encryption**

The **Caesar Cipher** is a basic encryption technique where each letter in a message is **shifted by a fixed number** of positions in the alphabet. For example, with a **shift of 3**, 'A' becomes 'D'.

### **Caesar Cipher Concept**

- **Key**: The number of positions each letter shifts.
- **Wrap-around**: If shifting goes past 'Z', it wraps back to 'A'.

**Encryption Example (Shift = 3):**

- Plain text: **"HELLO"**
- Cipher text: **"KHOOR"**

---

### **Implementing the Caesar Cipher in Java**

**Encryption Method:**

```java
private String encryptCaesar(String str, int key) {
    String result = "";
    for (int i = 0; i < str.length(); i++) {
        char ch = str.charAt(i);
        result += encryptChar(ch, key);
    }
    return result;
}
```

- **Standard idiom for string processing**: Loop through each character, modify it, and build the result string.

---

### **Character Encryption with Wrap-Around Logic**

The **`encryptChar`** method handles both the **shifting** and **wrap-around** logic.

```java
private char encryptChar(char ch, int key) {
    if (!Character.isUpperCase(ch)) {
        return ch;  // Leave non-uppercase characters unchanged.
    }
    int shifted = (ch - 'A' + key) % 26 + 'A';
    return (char) shifted;
}
```

- **Modulus (`%`)** ensures **wrap-around** when the character goes past 'Z'.
- **Casting** to **`char`** converts the shifted integer back to a character.

---

## **5. Decrypting the Caesar Cipher**

To decrypt, simply **shift in the opposite direction** by **negating the key**.

**Example: Decrypt Using Negative Key**

```java
String decrypted = encryptCaesar(cipherText, -key);
```

If shifting by -3, it's equivalent to shifting forward by **23** (since `-3 % 26` is the same as `23`).

---

## **6. Handling Negative Keys with Modulo Arithmetic**

When the **key is negative**, ensure it correctly wraps around the alphabet.

**Key Modulo Logic:**

```java
if (key < 0) {
    key = (26 - (-key % 26)) % 26;
}
```

This ensures **negative shifts** are converted to valid positive shifts.

---

## **7. Full Example: Caesar Cipher Program**

The complete program includes encryption, decryption, and user interaction.

**Main Method Example:**

```java
public void run() {
    int key = readInt("Enter encryption key: ");
    String plainText = readLine("Enter plain text: ");
    String cipherText = encryptCaesar(plainText, key);
    System.out.println("Cipher text: " + cipherText);

    String decryptedText = encryptCaesar(cipherText, -key);
    System.out.println("Decrypted text: " + decryptedText);
}
```

- **User input** determines the **key** and **text to encrypt**.
- **Decryption** verifies the original text is correctly restored.

---

## **8. Key Takeaways**

1. **String Replacement**:

   - Use **`indexOf()`** and **`substring()`** for efficient string manipulation.

2. **Tokenization**:

   - Split text into **tokens** for further processing using **`StringTokenizer`**.

3. **Encryption**:

   - **Caesar Cipher** demonstrates basic encryption with character manipulation.
   - Use **modulus arithmetic** to handle wrap-around in shifting.

4. **String Manipulation Techniques**:
   - Use **loops** to iterate over strings.
   - Leverage **helper methods** for better **top-down design**.

These concepts are crucial for understanding **string-based problems** and **encryption techniques** used in software development. The **Caesar Cipher** is a great way to practice **character manipulation**, **modulus arithmetic**, and **string iteration**.
