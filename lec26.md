### **Lecture 26 | Programming Methodology (Stanford) - Summary**

Watch the full lecture [here](https://www.youtube.com/watch?v=Qi6L9lfbyyQ).

This lecture covers **transitioning from ACM libraries** to **standard Java** and introduces the use of **main methods**, **jar files**, and deploying Java programs. The goal is to help students move beyond ACM libraries and understand **how Java applications run independently**.

---

## **Part 1: Understanding `main()` Method in Java**

1. **Where Programs Start in Java:**

   - Standard Java applications **start at the `main()` method**.
   - ACM libraries provided a `run()` method to simplify starting applications for students, **hiding `main()` behind the scenes**.
   - Now, students learn how **Java programs actually begin execution**.

2. **Structure of `main()` Method:**

   ```java
   public static void main(String[] args) {
       // Code that runs when the program starts
   }
   ```

   - **`public`**: Accessible anywhere.
   - **`static`**: Belongs to the class, not an object.
   - **`void`**: Doesn’t return a value.
   - **`String[] args`**: Array of arguments passed from the command line (optional).

3. **How ACM's `program.run()` Works Internally:**

   - ACM libraries automatically generate a `main()` method that **creates an object** of your program and **calls `run()`**.
   - Example:
     ```java
     new NameSurfer().start(args);
     ```

4. **Why Use the `main()` Method Now?**
   - **Writing `main()` increases portability** and makes programs **standard Java-compliant**.
   - When transitioning to **non-ACM environments** (e.g., deploying apps), using `main()` becomes necessary.

---

## **Part 2: Creating and Exporting Jar Files**

1. **What is a Jar File?**

   - A **Java Archive (JAR)** is a **packaged collection of compiled class files and resources** (like data files and images).
   - You can think of it as a **zipped executable** that can run on any Java-enabled system.

2. **How to Export a Jar File:**

   - **Steps in Eclipse:**
     1. Right-click your project → **Export** → **Java → JAR File**.
     2. Select the **default package** containing your class files.
     3. **Specify the export destination** (where to save the JAR).
     4. Generate a **manifest file** (contains metadata, like which class to run).
     5. Set the **entry point** (main class) by specifying which class contains the `main()` method.

3. **Manifest File:**

   - A **manifest** tells Java **which class to run** when the jar is executed.
   - Example:
     ```
     Manifest-Version: 1.0
     Main-Class: NameSurfer
     Class-Path: acm.jar NameSurfer.jar
     ```

4. **How to Use the Jar:**
   - After creating the jar, **double-click it** to run the application.
   - You can **package the jar** with data files (e.g., `names.dat`) to send the full program to others.

---

## **Part 3: Deploying Java Applications as Web Applets**

1. **Running Java Programs in a Web Browser:**

   - You can **embed Java programs into web pages** using **applets**.

2. **Example HTML for an Applet:**

   ```html
   <html>
     <body>
       <applet archive="NameSurfer.jar" code="NameSurfer.class" width="700" height="500"> </applet>
     </body>
   </html>
   ```

   - This snippet loads and displays the `NameSurfer` application directly within the browser.

3. **Limitations of Applets:**
   - Applets **cannot access the local file system** for security reasons.
   - To provide data, you can either:
     - **Embed data directly** in your program (as arrays).
     - **Include data files** within the jar.

---

## **Part 4: Introduction to Standard Java Programming**

1. **Differences between ACM Libraries and Standard Java:**

   - ACM libraries **simplified many concepts** for students (like window management and event handling).
   - Standard Java requires more **manual setup** (e.g., using `JFrame` for windows, adding event listeners explicitly).

2. **Hello World Example (Standard Java):**

   ```java
   public class HelloWorld {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }
   ```

   - Output is displayed on the **system console**, not a dedicated window.

3. **Graphical Hello World Example:**

   - A graphical program in standard Java involves:
     - **Creating a JFrame** for the window.
     - **Adding components** like JLabels for content.
   - Example:
     ```java
     JFrame frame = new JFrame("Hello World");
     JLabel label = new JLabel("Hello, World!", SwingConstants.CENTER);
     frame.add(label);
     frame.setSize(500, 300);
     frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
     frame.setVisible(true);
     ```

4. **Interactive Hello World Example:**

   - Adding **Mouse Listeners** for interactivity requires implementing the `MouseListener` interface.
   - Example:

     ```java
     public class MovingLabel extends JComponent implements MouseListener {
         private String text = "CS106A Rocks!";
         private int x = 50, y = 50;

         public MovingLabel() {
             addMouseListener(this);
         }

         public void paintComponent(Graphics g) {
             g.drawString(text, x, y);
         }

         public void mouseClicked(MouseEvent e) {
             x = e.getX();
             y = e.getY();
             repaint();
         }
     }
     ```

---

## **Part 5: Resources for Learning Standard Java**

1. **Recommended Books:**

   - **"Learning Java"** – A practical introduction to Java.
   - **Java Programming Language Specification** – Detailed language reference.
   - **Big Java** – Comprehensive guide with in-depth topics.
   - **Java Server Programming** – Advanced book focused on web-based Java applications.

2. **Next Steps After This Course:**
   - Explore **standard Java libraries** and learn more advanced topics.
   - Continue building **desktop or web applications** using Java tools.
   - Use the **ACM libraries** in future projects if they simplify your workflow.

---

## **Conclusion**

This lecture provides a bridge from the **simplified ACM environment** to **standard Java programming**, teaching students how to:

1. Use the **main() method** as the entry point for Java programs.
2. **Package applications** into JAR files for sharing.
3. Deploy **Java programs on the web** as applets.
4. Understand the **advantages of the ACM libraries** and how they simplify certain tasks.

With these tools, students are ready to move beyond classroom projects, **share their applications**, and explore deeper aspects of Java programming.
