### **Lecture 22 | Programming Methodology (Stanford) - Summary**

This lecture introduces the **NameSurfer** assignment and dives into the technical concepts necessary to create dynamic, resizable GUIs using **Java components** and **listeners**. The focus is on how to handle **resizing events** and how **containers and components** work together to build flexible programs.

Watch the full lecture [here](https://www.youtube.com/watch?v=AGUUQXO8eXk).

---

## **1. Introduction to the NameSurfer Assignment**

The **NameSurfer program** visualizes the popularity of names over the decades, based on U.S. Census data. The program:

- **Displays a graph** showing how a name's rank changed from 1900 to 2000.
- **Handles multiple names** (each in a different color).
- **Responds to window resizing**, adjusting the graph dynamically to fit the new window size.

Key Features:

- **Graphically display names** over time.
- **Handle dynamic resizing** so the layout remains responsive.
- **Keep track of multiple names and their ranks** while cycling through colors.

---

## **2. Handling Resizing with Java Components**

To understand how to build dynamic programs, the lecture discusses **Java components and containers**.

### **Key Concepts:**

1. **Components**: Anything that can appear in a window (e.g., buttons, text fields, canvases).
2. **Containers**: Components that can hold other components.  
   Example: A **GCanvas** can hold graphical objects like images or shapes.

   - **Programs** like `GraphicsProgram` or `ConsoleProgram` are also containers, as they hold other components (e.g., buttons, canvases).
   - Containers can contain other containers (e.g., a GCanvas inside a graphics program).

---

## **3. Making Programs Resizable**

The **GCanvas** can detect window resizing events, allowing dynamic adjustment of content. When the window size changes, the **component listener** detects the event, and the program redraws its content to fit the new size.

### **Setting Up Resizable Components:**

Instead of using a `GraphicsProgram`, **extend the `Program` class** directly to gain more control over the canvas:

```java
public class MyProgram extends Program {
    private MyCanvas canvas;

    public void init() {
        canvas = new MyCanvas();  // Create a custom canvas
        add(canvas);              // Add it to the program’s container
    }
}
```

---

## **4. Creating Custom Canvases with Listeners**

A **custom GCanvas** can implement the `ComponentListener` interface to respond to resizing events.

### **Example of a Custom Canvas:**

```java
public class MyCanvas extends GCanvas implements ComponentListener {

    public MyCanvas() {
        addComponentListener(this);  // Register as a component listener
    }

    @Override
    public void componentResized(ComponentEvent e) {
        update();  // Redraw content when resized
    }

    private void update() {
        removeAll();  // Clear the canvas
        GRect rect = new GRect(getWidth() / 2 - 25, getHeight() / 2 - 25, 50, 50);
        add(rect);  // Re-center the rectangle
    }

    // Other required methods (empty implementations)
    public void componentMoved(ComponentEvent e) {}
    public void componentShown(ComponentEvent e) {}
    public void componentHidden(ComponentEvent e) {}
}
```

- **`componentResized()`** is triggered when the window size changes.
- The `update()` method clears the canvas and **redraws the content centered** based on the new dimensions.

---

## **5. Example: Music Shop Program**

The **Music Shop program** demonstrates how to use **hash maps, custom canvases, and dynamic resizing** in Java. The program:

- Stores information about **albums** (name, band, and stock) in a **HashMap**.
- Displays the album information along with a **graphical representation of stock** using squares.
- Adjusts the size and layout dynamically based on **window resizing**.

### **Setting Up the Album Class:**

```java
public class Album {
    private String albumName;
    private String bandName;
    private int numInStock;

    public Album(String albumName, String bandName, int numInStock) {
        this.albumName = albumName;
        this.bandName = bandName;
        this.numInStock = numInStock;
    }

    public String getAlbumName() { return albumName; }
    public String getBandName() { return bandName; }
    public int getNumInStock() { return numInStock; }
}
```

### **Creating the HashMap to Store Albums:**

```java
private HashMap<String, Album> inventory = new HashMap<>();

private void loadInventory() throws IOException {
    BufferedReader reader = new BufferedReader(new FileReader("music-data.txt"));
    String line;
    while ((line = reader.readLine()) != null) {
        Album album = parseLine(line);
        inventory.put(album.getAlbumName(), album);
    }
    reader.close();
}
```

- **`parseLine()`** breaks the string from the file into parts (album name, band name, stock).
- The program **stores each album object** in the hash map with the album name as the key.

---

## **6. Displaying Dynamic Content on Resize**

The **Music Shop display** redraws content dynamically whenever the window is resized. It displays:

1. **Album information** (name, band, and stock).
2. **Squares representing stock** – the number of squares equals the number in stock, and their size adjusts based on window size.

### **Display Inventory Method:**

```java
public void displayInventory(Album album) {
    removeAll();  // Clear the canvas

    if (album != null) {
        // Display album details
        GLabel label = new GLabel(album.getAlbumName() + " by " + album.getBandName());
        add(label, getWidth() / 2 - label.getWidth() / 2, 20);

        // Draw squares representing stock
        int barLength = getWidth() / 20;
        for (int i = 0; i < album.getNumInStock(); i++) {
            GRect rect = new GRect(i * barLength, 50, barLength - 2, 20);
            add(rect);
        }
    }
}
```

- **Squares change size** dynamically based on the window width.
- **Album labels are centered** using `getWidth()` and `getHeight()`.

---

## **7. Implementing the NameSurfer Program**

The **NameSurfer assignment** requires similar logic:

- **Store name data** using a `HashMap`.
- **Draw graphs dynamically** and **adjust layout on resize**.
- **Handle multiple names** and **different colors** for each graph.

---

## **8. Key Takeaways**

- **Java programs are containers** that hold components like buttons, text fields, and canvases.
- **Custom canvases** can handle **component events**, including resizing, by implementing the `ComponentListener` interface.
- **HashMaps** are useful for storing and accessing structured data efficiently.
- **Dynamic resizing** is achieved by recalculating positions and sizes whenever the window size changes.

This lecture provides the **foundational techniques** needed to build responsive GUIs with **interactive graphics** and **resizable layouts**, which are crucial for the **NameSurfer** assignment.
