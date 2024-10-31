### **Lecture 19 | Programming Methodology (Stanford) - Summary**

This lecture covers **interfaces**, dives into the use of the **Map interface**, and introduces the concept of **iterators** in Java. It also provides practical insights on **HashMaps**, including their use cases, syntax, and methods.

[Watch the full lecture](https://www.youtube.com/watch?v=MxBx1km7WNk).

---

## **1. Revisiting Interfaces**

Interfaces in Java define a **common set of methods** that multiple classes can implement, even if the classes are unrelated.

- **Interfaces** promote **code reusability** and **generalization**.
- Syntax:
  ```java
  public class ClassName implements InterfaceName {
      // Implement interface methods here
  }
  ```

### **Difference between Interfaces and Inheritance:**

- **Inheritance**: Models a hierarchical relationship (e.g., a **Human** is a **Primate**).
- **Interface**: Allows **unrelated classes** to share common behavior (e.g., both **Humans** and **Dolphins** can implement an **Intelligence** interface).

---

## **2. Introduction to Maps and HashMaps**

A **Map** is a **collection of key-value pairs**. Think of it as similar to a **dictionary** or **phone book**, where you can look up a value (like a phone number) by its key (a person’s name).

- **Keys**: Unique identifiers (e.g., words in a dictionary).
- **Values**: Associated data for each key (e.g., word definitions).

### **Creating a HashMap**

A **HashMap** in Java stores key-value pairs and implements the **Map interface**. The **types of the keys and values** are specified in the angled brackets `<K, V>`.

```java
HashMap<String, String> dictionary = new HashMap<>();
```

You can also create **other types of maps**, like a phone book:

```java
HashMap<String, Integer> phoneBook = new HashMap<>();
```

---

## **3. Important Methods in HashMap**

1. **`put()`**: Adds a key-value pair.

   ```java
   phoneBook.put("Maron", 7236059);
   phoneBook.put("Jenny", 8675309);
   ```

2. **`get()`**: Retrieves the value associated with a given key.

   ```java
   Integer maronsNumber = phoneBook.get("Maron");
   ```

   - If the key doesn't exist, it returns `null`.

3. **`remove()`**: Removes a key-value pair by key.

   ```java
   phoneBook.remove("Maron");
   ```

4. **`containsKey()`**: Checks if a key exists in the map.

   ```java
   if (phoneBook.containsKey("Jenny")) { ... }
   ```

5. **`size()`**: Returns the number of key-value pairs.
   ```java
   int numberOfEntries = phoneBook.size();
   ```

---

## **4. Iterators and the KeySet Method**

### **What is an Iterator?**

An **iterator** provides a way to **traverse a collection** without exposing the underlying structure. It’s especially useful for **collections without guaranteed order**, like **HashMaps**.

### **Using Iterators with HashMaps:**

HashMaps do not have a natural order, but you can **iterate over their keys** using the `keySet()` method.

```java
Iterator<String> it = phoneBook.keySet().iterator();
while (it.hasNext()) {
    String name = it.next();
    System.out.println(name + ": " + phoneBook.get(name));
}
```

---

## **5. Enhanced For-Loop (For-Each Loop)**

Java offers a **simplified syntax** for iterating over collections, called the **enhanced for-loop** or **for-each loop**.

```java
for (String name : phoneBook.keySet()) {
    System.out.println(name + ": " + phoneBook.get(name));
}
```

- This loop abstracts away the need to manually manage an **iterator**.
- The **iterator** is implicitly created and used under the hood.

---

## **6. Case Sensitivity and Error Handling**

- **Keys in HashMaps are case-sensitive**: `"Maron"` is not the same as `"maron"`.
- Be careful when retrieving values from a map. If a key doesn’t exist, **`get()` returns `null`**.

  Example:

  ```java
  Integer number = phoneBook.get("Unknown");
  if (number == null) {
      System.out.println("Name not found.");
  }
  ```

---

## **7. Maps and Collections Hierarchy**

- **HashMap** is part of the **Java Collections Framework**.
- The **Map interface** allows for other implementations, such as:
  - **TreeMap**: Maintains keys in sorted order.
  - **HashMap**: Provides fast lookups with no guaranteed order.
- If you write code using the **Map interface** rather than a specific implementation, you can easily switch between different map types without changing your code.

---

## **8. Key Concepts from the Lecture**

1. **Abstract Thinking with Interfaces**:

   - Code against **interfaces** (e.g., `Map<String, Integer>`) to allow **flexibility** and **future-proofing**.

2. **Iterating Over Collections**:

   - Use **iterators** or **for-each loops** for easier traversal.

3. **No Intrinsic Order in HashMaps**:
   - Even if you add keys in a certain order, there is no guarantee that they will be retrieved in the same order.

---

## **9. Example Code from the Lecture**

### **Complete HashMap Example**

```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

public class PhoneBook {
    private Map<String, Integer> phoneBook;

    public PhoneBook() {
        phoneBook = new HashMap<>();
    }

    public void addEntry(String name, int number) {
        phoneBook.put(name, number);
    }

    public Integer getNumber(String name) {
        return phoneBook.get(name);
    }

    public void displayAllEntries() {
        for (String name : phoneBook.keySet()) {
            System.out.println(name + ": " + phoneBook.get(name));
        }
    }

    public static void main(String[] args) {
        PhoneBook book = new PhoneBook();
        book.addEntry("Maron", 7236059);
        book.addEntry("Jenny", 8675309);

        System.out.println("Maron's number: " + book.getNumber("Maron"));
        System.out.println("All entries:");
        book.displayAllEntries();
    }
}
```

---

## **10. Key Takeaways**

- **Interfaces** provide a way to generalize behavior across unrelated classes.
- **HashMaps** store key-value pairs and are widely used when you need **fast lookups**.
- **Iterators** allow you to traverse collections easily, especially for collections like HashMaps with no inherent order.
- The **enhanced for-loop** simplifies iteration and reduces the chance of errors.

This lecture equips you with the tools to **store and manage key-value data** effectively using **HashMaps** and **iterators**, along with insights into **interfaces** and **object-oriented design**.
