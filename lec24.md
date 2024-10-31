### **Lecture 24 | Programming Methodology (Stanford) - Summary**

Watch the full lecture [here](https://www.youtube.com/watch?v=lYZwJ6xyGNc).

This lecture dives into **building large-scale data structures** and managing complex data relationships efficiently. The focus is on designing systems with **consistent, scalable data management** using **Java collections**, such as `ArrayList` and `HashMap`. The examples revolve around building an **online music store**, giving insight into real-world software engineering challenges.

---

## **Key Topics Covered:**

### 1. **Data Management in Software**

- Many applications (like **online stores, social networks**, or **web search engines**) revolve around **managing large datasets**.
- The ability to **organize and manipulate data efficiently** is a key factor in the success of applications.

**Examples of Data Management:**

- Online stores track **products, transactions**, and **purchase recommendations**.
- Social networks manage **profiles, relationships**, and **activity feeds**.

---

## **Design Principles for Managing Data**

1. **Identify Nouns and Verbs:**

   - **Nouns**: Often correspond to **classes** (e.g., `Song`, `Album`).
   - **Verbs**: Correspond to **methods** or actions that objects perform (e.g., `addSong()` or `getPrice()`).

2. **Use of Unique Identifiers:**

   - A **unique identifier** ensures that no two entities are treated as the same.
     - Example: **Stanford ID** uniquely identifies a student.
     - In a **music store**, a combination of **song name + band name** could serve as a unique identifier.

3. **Determine What Changes and What Doesn’t:**
   - Some attributes remain **static** (e.g., song name or artist).
   - Others are **malleable** (e.g., price), meaning they can change during the program’s execution.

---

## **Working with Collections in Java**

Java collections offer flexible ways to manage **data objects** like songs or albums.

### **Collection Types:**

- **`ArrayList`**: Resizable array; useful when the size is unknown in advance.
- **`HashMap`**: Stores **key-value pairs**, useful when fast lookups are needed by a **unique key**.

**Common Collection Operations:**

- **`add()`**: Adds an item to the collection.
- **`remove()`**: Removes an item.
- **`contains()`**: Checks if the collection has a specific item.
- **`iterator()`**: Iterates over elements in a collection.

---

## **Building the FlyTunes Music Store**

This lecture uses the **FlyTunes music store** as an example to demonstrate how to organize and manipulate **songs and albums**.

### **Class Design for Song and Album:**

#### **`Song` Class:**

```java
public class Song {
    private String title;
    private String band;
    private double price;

    public Song(String title, String band, double price) {
        this.title = title;
        this.band = band;
        this.price = price;
    }

    public String getTitle() { return title; }
    public String getBand() { return band; }
    public double getPrice() { return price; }
    public void setPrice(double price) { this.price = price; }

    @Override
    public String toString() {
        return "\"" + title + "\" by " + band + " costs $" + price;
    }
}
```

- **Static data**: Song name and band name do not change.
- **Malleable data**: Price can be updated with `setPrice()`.

#### **`Album` Class:**

```java
public class Album {
    private String name;
    private ArrayList<Song> songs = new ArrayList<>();

    public Album(String name) {
        this.name = name;
    }

    public void addSong(Song song) {
        songs.add(song);
    }

    public Iterator<Song> getSongs() {
        return songs.iterator();
    }

    @Override
    public String toString() {
        return "Album: " + name;
    }
}
```

- An album contains a **list of songs**.
- The **`ArrayList`** dynamically grows as new songs are added.

---

## **Handling Data Consistency:**

- **Avoiding Duplicates**:
  - If a song is **both sold individually and included in an album**, the same **song object** should be referenced in both places.
  - This prevents inconsistencies when the song’s price is updated.

**Example:**

```java
if (songAlreadyExists) {
    return existingSong;  // Return the existing object reference
} else {
    Song newSong = new Song(title, band, price);
    songs.add(newSong);
    return newSong;
}
```

- **Shallow Copy**:
  - Multiple references point to the **same object**, ensuring consistency.
  - **Deep Copy**: Creates a separate copy of the object, which can lead to inconsistencies if not managed properly.

---

## **Managing Collections in the Store**

### **Using `ArrayList` to Store Songs:**

```java
private ArrayList<Song> songs = new ArrayList<>();

public void addSong(Song song) {
    songs.add(song);
}
```

- Stores all individual songs for sale.

### **Using `HashMap` for Albums:**

```java
private HashMap<String, Album> albums = new HashMap<>();

public void addAlbum(String name, Album album) {
    albums.put(name, album);
}
```

- Maps **album names** to **album objects** for fast lookups.

---

## **Implementing the Store Logic:**

The FlyTunes store provides basic functionality, such as:

- **Listing songs and albums**.
- **Adding songs and albums**.
- **Updating song prices**.

**Example: Listing All Songs:**

```java
public void listAllSongs() {
    for (Song song : songs) {
        System.out.println(song);
    }
}
```

**Example: Updating Song Price:**

```java
public void updateSongPrice(String title, String band, double newPrice) {
    for (Song song : songs) {
        if (song.getTitle().equals(title) && song.getBand().equals(band)) {
            song.setPrice(newPrice);
            break;
        }
    }
}
```

- This ensures the **price is updated everywhere** since all references point to the same song object.

---

## **Key Lessons:**

1. **Data Reuse**:

   - Avoid creating multiple objects for the same data. Use **shallow copies** and references to ensure consistency.

2. **Choosing the Right Data Structure**:

   - Use **`ArrayList`** for ordered collections where duplicates are allowed.
   - Use **`HashMap`** when fast lookups by a key are needed.

3. **Maintaining Data Integrity**:
   - Carefully manage **object references** to prevent inconsistencies when data changes.

---

## **Conclusion:**

This lecture demonstrates the **complexities of working with large-scale data structures** and how to maintain **consistency** across objects. It emphasizes the importance of **careful design and thoughtful data management** in software engineering. As applications grow, **reuse of data** and selecting the right data structures become crucial for **scalable and maintainable software**.
