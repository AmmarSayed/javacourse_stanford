### **Lecture 23 | Programming Methodology (Stanford) - Summary**

Watch the full lecture [here](https://www.youtube.com/watch?v=4ytrc3AsaHM).

This lecture, presented by TA Ben, focuses on the **concepts of searching, sorting, and algorithmic efficiency**. These fundamental computer science topics help students grasp the importance of **optimized data handling** in programming. Additionally, the lecture introduces **binary search, selection sort, and the radix sort** as examples of efficient algorithms.

---

## **Key Topics Covered:**

### 1. **Introduction to Algorithmic Efficiency**

- Computers can handle **large-scale data problems** faster than humans by employing optimized algorithms.
- Understanding how to **search and sort** efficiently is essential since these operations appear in many programming scenarios.
- The lecture also touches on **CS 106B** topics, giving students a taste of what's to come, such as thinking about **problems on a larger scale**.

---

## **Searching Algorithms**

### **Linear Search**

- **Linear search** checks each element of an array one by one until it finds the desired element or confirms that it doesn’t exist.
- **Drawback**: The time taken grows **linearly** with the size of the input, making it inefficient for large datasets.

**Example:**

```java
public int linearSearch(int[] array, int key) {
    for (int i = 0; i < array.length; i++) {
        if (array[i] == key) {
            return i; // Return index if found
        }
    }
    return -1; // Return -1 if not found
}
```

- **Simulation**: Searching through **area codes** demonstrates how inefficient linear search becomes as the dataset grows.

### **Binary Search**

- **Binary search** works on **sorted arrays**. It repeatedly divides the search space in half, eliminating one half at each step.
- **Efficiency**: With each iteration, the size of the search space is halved, making binary search **logarithmic** in performance—i.e., \(O(\log n)\).

**Binary Search Code:**

```java
public int binarySearch(int[] array, int key) {
    int left = 0;
    int right = array.length - 1;

    while (left <= right) {
        int mid = (left + right) / 2;
        if (array[mid] == key) {
            return mid; // Key found
        } else if (array[mid] < key) {
            left = mid + 1; // Search right half
        } else {
            right = mid - 1; // Search left half
        }
    }
    return -1; // Key not found
}
```

- **Binary Search Simulation**: When applied to a sorted array, the search runs **much faster** than linear search, especially with large datasets.
- **Pitfall**: Be cautious with integer overflow when calculating the midpoint:
  ```java
  int mid = left + (right - left) / 2; // Avoid overflow
  ```

---

## **Algorithmic Efficiency: Logarithmic vs. Linear Growth**

- **Linear search** takes \(O(n)\) time—search time scales directly with input size.
- **Binary search** takes \(O(\log n)\) time—search time grows very slowly, even as the input size becomes enormous.

For example:

- Searching through **1 billion elements** with binary search requires only about **30 comparisons**.

---

## **Sorting Algorithms**

Sorting imposes an **order on a dataset**, making future searches faster (e.g., binary search). Sorting itself can take time, so choosing the right algorithm matters.

### **Selection Sort**

- **Selection sort** is simple but inefficient. It repeatedly selects the smallest (or largest) element and swaps it into its correct position.

**Selection Sort Code:**

```java
public void selectionSort(int[] array) {
    for (int i = 0; i < array.length - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < array.length; j++) {
            if (array[j] < array[minIndex]) {
                minIndex = j;
            }
        }
        // Swap elements
        int temp = array[i];
        array[i] = array[minIndex];
        array[minIndex] = temp;
    }
}
```

- **Time Complexity**: \(O(n^2)\). Sorting 10,000 elements can take a **very long time** using selection sort.
- **Simulation**: The lecture visually demonstrates how selection sort swaps elements to gradually build a sorted array.

---

## **Algorithmic Analysis of Selection Sort**

- The **running time** depends on how many times the algorithm examines elements.
- For an array of size \(n\), the algorithm examines \(n + (n-1) + (n-2) + \dots + 1\) elements.
- This sum simplifies to **\(n^2 / 2\)**, so selection sort is \(O(n^2)\).

**Insight**:

- Selection sort becomes **impractical** for large datasets. Even doubling the input size makes the runtime **four times longer**.

---

## **Improving Sorting: Radix Sort**

### **Introduction to Radix Sort**

- **Radix sort** works by sorting numbers **digit by digit**, from least significant to most significant.
- Example: Sorting 3-digit numbers by processing **one digit at a time** using buckets for each possible value (0–9).

**Steps**:

1. Sort all numbers by the **rightmost digit**.
2. Reassemble the numbers.
3. Sort by the **second digit**, then by the **third digit**.

- After all digits are processed, the numbers are **fully sorted**.

### **Efficiency of Radix Sort**

- Radix sort can be **much faster** than selection sort for certain types of data because it operates in **linear time**, \(O(n \cdot k)\), where \(k\) is the number of digits.

---

## **Trade-offs Between Searching and Sorting**

- **Sorting before searching** (for binary search) makes sense if you plan to search multiple times, as the initial sorting cost can be amortized over many searches.
- However, if you only need to search **once**, a **linear search** might be more practical since sorting takes time.

---

## **Summary and Key Takeaways**

- **Linear search** is straightforward but slow for large datasets: \(O(n)\).
- **Binary search** is much faster for sorted data: \(O(\log n)\).
- **Selection sort** is simple but inefficient: \(O(n^2)\).
- **Radix sort** offers a more efficient way to sort under certain conditions: \(O(n \cdot k)\).

**Algorithmic efficiency** matters because the **right choice of algorithm** can drastically reduce runtime for large-scale problems. This lecture offers a glimpse into **CS 106B**, where more advanced algorithms and data structures are explored.
