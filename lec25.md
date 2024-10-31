### **Lecture 25 | Programming Methodology (Stanford) - Summary**

Watch the full lecture [here](https://www.youtube.com/watch?v=YuVrg0RiPmM).

This lecture focuses on two key topics:

1. **Building a social network application** (FacePamphlet).
2. **Introduction to concurrency** in Java through threads.

---

## **Part 1: Social Network Application - FacePamphlet**

The assignment involves building a **mini social network** called **FacePamphlet**, focusing on **data management** and relationships between user profiles.

### **Core Components of FacePamphlet:**

1. **Profiles:**

   - Each profile has a **unique identifier (name)**, which acts as the primary way to differentiate users.
   - Profiles store:
     - **Status**: A string describing what the user is doing (e.g., “teaching”).
     - **Image**: An optional user image (using GImage).
     - **List of Friends**: A collection of friends (other profiles identified by their names).

2. **Friendship Model:**

   - **Reciprocal friendships**: If **Alice adds Bob as a friend**, Bob is also automatically added as Alice’s friend.
   - Friendships are **stored as lists of names** (i.e., unique profile identifiers).

3. **Basic Operations:**
   - **Create Profile**: Add a new profile.
   - **Update Profile**: Change status or add an image.
   - **Add Friend**: Link two profiles as friends.
   - **Delete Profile**: Remove a profile and ensure it is also removed from all friends’ lists.
   - **Look Up Profiles**: Search for and display an existing profile.

---

### **FacePamphlet UI Overview:**

- **UI Components:**

  - **Text fields** for name, status, and image input.
  - **Buttons** to add profiles, update status, add friends, and delete profiles.
  - **Display area** for the current profile, including the user’s name, status, image, and list of friends.

- **Example Workflow:**

  1. **Add a new profile** (e.g., "Maron Sahami").
  2. **Update status** ("teaching").
  3. **Upload an image** (e.g., `maron.jpg`).
  4. **Create more profiles** (e.g., "Julie Zelenski").
  5. **Add friends** (e.g., Maron adds Julie as a friend).
  6. **Lookup profiles** and view reciprocal friendships.
  7. **Delete profiles** and update the friends’ lists accordingly.

- **Case Sensitivity:**
  - Names are **case-sensitive** (e.g., "maron" and "Maron" are considered different profiles).
- **Error Handling:**
  - Display messages for invalid operations (e.g., adding a non-existent friend).
  - Handle missing images with appropriate error messages.

---

### **Core Takeaways:**

- **Focus on Data Management:**  
  The primary challenge is managing **profiles, friendships, and their attributes** efficiently.

- **Reciprocal Updates:**  
  When a profile is added, removed, or modified, ensure consistency across all related data (e.g., remove a deleted friend from all friend lists).

- **Extension Possibilities:**  
  You can add custom features (like resizing, dynamic content, or new friend features) if desired.

---

---

## **Part 2: Introduction to Concurrency and Threads**

In the second part of the lecture, Maron introduces the concept of **concurrency**, a fundamental idea in modern programming.

### **What is Concurrency?**

- **Concurrency** makes it look like **multiple tasks** are happening **simultaneously**.
- On most systems, only one processor executes instructions at a time.  
  However, tasks are **time-sliced**, meaning the CPU switches between tasks so quickly that it **appears** they are running simultaneously.

**Example from Breakout Game:**

- The ball, paddle, and collision detection **appear to run simultaneously**, but the program cycles through them quickly.

---

### **What are Threads?**

- A **thread** is a **lightweight process** that executes independently.
- Threads allow **multiple parts of a program** to run concurrently.

### **Runnable Interface in Java:**

- A class can **implement the `Runnable` interface** to define a task that can be run as a thread.
- The only required method is:
  ```java
  public void run() {
      // Code that defines the thread’s behavior
  }
  ```

### **Creating Threads in Java:**

1. **Create a class that implements `Runnable`.**
2. **Instantiate a new Thread**, passing the `Runnable` object.
3. **Start the thread** using the `start()` method.

**Example:**

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Running in a thread!");
    }
}

MyRunnable myRunnable = new MyRunnable();
Thread thread = new Thread(myRunnable);
thread.start();
```

---

### **Concurrency Example: Sliding Squares**

The first demo shows **multiple squares** sliding across the screen using **separate threads**.

1. **Slider Class:**

   - Each square is a **GRect** object that implements `Runnable`.
   - The `run()` method controls the movement of the square across the screen:
     ```java
     public void run() {
         while (true) {
             pause(40);
             move(5, 0);  // Move the square in the X-direction
         }
     }
     ```

2. **Creating Multiple Threads:**
   - Each time the user clicks the **"Slide" button**, a new square is created and added to a **new thread**.

**Result:**

- Multiple squares slide independently, demonstrating **concurrent execution** using threads.

---

### **Race Example: Multiple Threads Competing**

A more advanced example involves a **race** where multiple squares race across the screen.

1. **Shared Data Between Threads:**

   - All threads share a **common array** to track whether each square has finished the race.
   - When a square finishes, it marks its position in the shared array.

2. **Race Conditions:**  
   **Race conditions** occur when multiple threads **access shared data simultaneously** and **interfere with each other’s results**.

3. **Bug Example:**
   - When all squares finish at **nearly the same time**, they all mark themselves as winners due to a **race condition**.

---

### **Key Concepts in Thread Programming:**

- **Race Condition:**  
  When multiple threads access shared data concurrently, **unexpected behavior** can occur.
- **Synchronization:**  
  Developers must carefully **coordinate access to shared resources** to avoid inconsistencies.

---

---

## **Conclusion:**

This lecture covers **data management** through the FacePamphlet social network and introduces **concurrency** via Java threads. Both topics emphasize the importance of **managing complexity**, whether through efficient data structures or careful thread coordination.

### **Key Takeaways:**

1. **FacePamphlet** helps students practice **object-oriented programming** and **data management**.
2. **Concurrency** is a powerful concept but requires careful handling to avoid **race conditions**.
3. **Java threads** simplify concurrent programming but introduce challenges in **synchronization** and **shared data management**.
