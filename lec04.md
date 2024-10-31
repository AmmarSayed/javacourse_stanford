### Summary of Lecture 4 | Programming Methodology (Stanford)

[Lecture 4 | Programming Methodology (Stanford) - YouTube](https://www.youtube.com/watch?v=nWheM30THaY)

This lecture marks a transition from Karel to Java programming and introduces the foundational concepts of computer science, programming, and object-oriented programming (OOP) through Java. Here are the key takeaways:

---

### **Key Takeaways**:

#### **History of Computing and Programming**:

- **Origins**: Computing devices like the abacus date back ~4,000 years, assisting with arithmetic.
- **Charles Babbage**: Designed the _Difference Engine_ and _Analytical Engine_ in the 1800s, which are early mechanical computing concepts.
- **Ada Byron (Lovelace)**: Recognized as the first programmer, writing programs for Babbage's unbuilt machine. Similar to modern practices of writing software for future hardware.
- **ENIAC (1946)**: One of the first large-scale electromechanical computers.
- **1971**: Birth of the microprocessor (Intel 4004), leading to rapid computer science developments still ongoing today.

#### **Difference Between Computer Science and Programming**:

- **Computer Science (CS)**: Not just programming but the study of _problem solving_ using computational methods. It includes algorithmic thinking, efficiency, and limitations of computation.
- **Analogy**: Programming is to computer science as building telescopes is to astronomy—it’s a tool, not the entire discipline.

#### **High-level vs. Low-level Languages**:

- **Binary**: Computers understand only _zeros_ and _ones_ (binary code).
- **High-level languages**: Java, C, C++, etc., are easier for humans to write and are compiled into low-level machine code the computer understands.
- **Compilation**: The process of converting source code into machine-readable code using a compiler like Eclipse.

#### **Java Compilation and Execution Process**:

- **Java Virtual Machine (JVM)**:
  - Java code is compiled into an intermediate bytecode (class files).
  - JVM on different platforms (Mac, PC, Linux) interprets the bytecode, enabling platform independence.
  - _Java Runtime Environment (JRE)_ provides the JVM and necessary libraries.

#### **Object-Oriented Programming (OOP) Concepts in Java**:

- **Class and Object**:
  - A _class_ is a blueprint for an object (e.g., the “Human” class).
  - An _object_ is an instance of a class (e.g., "Eduardo" is an instance of the “Human” class).
  - Each object inherits behaviors and properties from its class and superclass.
- **Class Hierarchies**:
  - Classes can extend each other to reuse and add new functionality (e.g., “SuperKarel” extends “Karel” with additional commands).
  - Java programs can involve multiple classes interacting with each other, just as Carol programs involved extending classes.

#### **Creating and Running Java Programs**:

- **Source Code**: Java programs are written in `.java` files containing the logic.
- **Graphics Programs**:
  - Java can create _graphical output_ by using classes like `GLabel` (text), `GRect` (rectangle), and `GOval` (oval/circle).
  - _Canvas Model_: Think of the graphics window as a blank canvas to which you can add graphical objects (like a collage).

#### **Examples from the Lecture**:

- **First Java Program**:
  - The `HelloProgram` example extends a `GraphicsProgram` and displays “Hello World” at a specific location on the screen.
- **Console Programs**:
  - Another example showed how a _console program_ asks the user for two integers, adds them, and prints the result.
  - Console programs work with text input/output, using commands like `readInt()` and `println()`.

#### **Graphics in Java**:

- **Graphics Objects**:
  - Classes like `GLabel`, `GRect`, and `GLine` define specific shapes and text elements.
  - Objects are added to the canvas using the `add()` method after being customized with properties (e.g., color, font).
- **Instance vs. Class**:
  - Objects are created from classes using the `new` keyword (e.g., `new GLabel("Hello World")`).
  - Modifying object properties before adding them to the canvas (e.g., changing font size, color).

---

### **Conclusion**:

- This lecture introduces the transition from Karel to Java, covering key programming concepts, Java’s structure, and its compilation process. It highlights fundamental OOP principles, the use of classes, objects, and hierarchies, and demonstrates practical examples of graphics and console-based Java programs.

- Students are encouraged to think of computer science beyond just coding and understand how Java's design offers platform independence through the JVM.
