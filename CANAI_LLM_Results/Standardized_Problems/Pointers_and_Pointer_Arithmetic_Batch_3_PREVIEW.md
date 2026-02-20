# Problem Batch Preview: Pointers and Pointer Arithmetic
**Batch Number:** 3 | **Total Problems:** 100

---

## Problem 1 - openai/gpt-oss-120b - Iteration 51
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑stop information system. Each bus stop is identified by a unique integer ID, has a human‑readable name (max 30 characters), and stores the distance in meters to the next stop on the route. The authority wants a small C program that lets a user **add**, **list**, **search**, and **remove** bus stops while practicing pointer arithmetic and dynamic memory management.

## Requirements  

1. **Data Representation**  
   * Define a `struct BusStop` that contains:  
     ```c
     int id;                 // unique identifier
     char name[31];          // null‑terminated name (max 30 chars)
     int distanceToNext;    // meters to the next stop
     ```  
2. **Dynamic Array**  
   * The program must store the bus stops in a **dynamically allocated array** that can grow or shrink as stops are added or removed.  
   * Use pointer arithmetic (not array indexing) to traverse, insert, and delete elements.  

3. **Menu‑Driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1 – Add a new stop** – Prompt for `id`, `name`, and `distanceToNext`. Insert the new stop at the **end** of the array.  
   * **2 – List all stops** – Print each stop on its own line in the order stored.  
   * **3 – Find a stop by ID** – Prompt for an `id` and display the matching stop’s details. If not found, print “Stop not found.”  
   * **4 – Delete a stop by ID** – Prompt for an `id`. Remove the stop from the array, shifting subsequent elements left to fill the gap. If the ID does not exist, print “Stop not found.”  
   * **5 – EXIT** – Terminate the program gracefully, freeing any allocated memory.  

4. **Function Requirements**  
   * Implement a function `void displayStop(const struct BusStop *p);` that prints a single bus stop in the format:  
     ```
     ID: <id>, Name: <name>, Distance to next: <distance>m
     ```  
   * All other logic (adding, listing, searching, deleting) must be placed in separate helper functions of your choosing, but **no more than three functions** in total besides `main`.  

5. **Error Handling**  
   * If memory allocation (`malloc`/`realloc`) fails, print “Memory allocation error.” and return to the menu.  
   * The program should not crash on malformed input; you may assume the user enters integers where integers are expected.  

## Example Input / Output  

```
--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 1
Enter ID: 101
Enter name: Central Station
Enter distance to next (m): 850

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 1
Enter ID: 102
Enter name: Riverside
Enter distance to next (m): 620

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 2
ID: 101, Name: Central Station, Distance to next: 850m
ID: 102, Name: Riverside, Distance to next: 620m

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 3
Enter ID to search: 102
ID: 102, Name: Riverside, Distance to next: 620m

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 4
Enter ID to delete: 101
Stop with ID 101 deleted.

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 2
ID: 102, Name: Riverside, Distance to next: 620m

--- Bus Stop Manager ---
1) Add a new stop
2) List all stops
3) Find a stop by ID
4) Delete a stop by ID
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct BusStop`.  
* **Display Function** – The details of **ONE** specific bus stop must be printed by a function named `displayStop`.  
* **Menu Exit** – Option **5** (or the keyword “EXIT”) must be provided to terminate the program.  
* **Function Limit** – Aside from `main`, you may implement **at most three** additional functions. One of them must be `displayStop`; the remaining two may be used for any other logical grouping you deem appropriate.  
* **Pointer Arithmetic** – All traversals, insertions, and deletions of the dynamic array must use pointer arithmetic (`*(ptr + i)`, `ptr++`, etc.) rather than the array‑subscript operator (`arr[i]`).  

Write a complete, well‑commented C program that satisfies the above specifications.

---

## Problem 2 - openai/gpt-oss-120b - Iteration 52
# STEP 1: PROBLEM  

## Background  
The university’s **Campus Navigation System** stores the coordinates of every building on a 2‑D map.  Each building is represented by a `struct Building` that contains the building’s name (a short string) and its (x, y) location.  The system must allow a user to enter a list of buildings, then query the distance between any two buildings that the user selects.  Because the course just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of `Building` structures directly through pointers rather than using array indexing.

## Requirements  

1. **Input the building list**  
   * Prompt the user for the number of buildings `N` (1 ≤ N ≤ 100).  
   * For each building, read:  
     * A name (max 30 characters, no spaces).  
     * An integer `x` coordinate.  
     * An integer `y` coordinate.  

2. **Menu‑driven interaction** (the program must present a menu after the list is entered)  
   * **1** – *Display all buildings*: list each building’s index (starting at 0), name, and coordinates.  
   * **2** – *Show distance*: ask for two building indices `i` and `j`, then compute and display the Euclidean distance between them, rounded to two decimal places.  
   * **3** – *Exit*: terminate the program.  

3. **Pointer arithmetic**  
   * The array of `Building` structures must be allocated dynamically (`malloc`/`new`).  
   * All traversals of the array must be performed with pointer arithmetic (e.g., `ptr = base; ptr < base + N; ++ptr`). Direct indexing like `array[i]` is **not** allowed.  

4. **Functions**  
   * Implement a function `void displayBuilding(const Building *b)` that prints the details of a single building (index, name, coordinates).  
   * Implement a function `double computeDistance(const Building *a, const Building *b)` that returns the Euclidean distance between two buildings.  

5. **Error handling**  
   * If the user enters an invalid menu option or an out‑of‑range building index, display an appropriate error message and re‑show the menu.  

## Example  

```
Enter number of buildings: 3
Building #0 name: Library
Library x: 10
Library y: 5
Building #1 name: Cafeteria
Cafeteria x: 2
Cafeteria y: 8
Building #2 name: Gym
Gym x: 14
Gym y: 9

--- Campus Navigation Menu ---
1) Display all buildings
2) Show distance between two buildings
3) Exit
Choose an option: 1

[0] Library      (10, 5)
[1] Cafeteria    (2, 8)
[2] Gym          (14, 9)

--- Campus Navigation Menu ---
1) Display all buildings
2) Show distance between two buildings
3) Exit
Choose an option: 2
Enter first building index: 0
Enter second building index: 2
Distance between Library and Gym: 9.22

--- Campus Navigation Menu ---
1) Display all buildings
2) Show distance between two buildings
3) Exit
Choose an option: 3
Goodbye!
```

## ### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be a `struct Building` containing at least a `char name[31]`, and two `int` fields for the coordinates.  
* **Function naming** – The function that prints a single building’s details must be named exactly `displayBuilding`.  
* **Pointer‑only traversal** – Inside `main` (and any helper functions) you may **only** move through the building array using pointer arithmetic; the `[]` subscript operator is prohibited for traversing the list.  
* **Menu exit option** – The menu must include an explicit option **3** labelled “Exit” that terminates the program.  

*Optional (for extra credit):*  
* Use `const` qualifiers appropriately for parameters that are not modified.  
* Free any dynamically allocated memory before exiting.  

---

## Problem 3 - openai/gpt-oss-120b - Iteration 53
# STEP 1: PROBLEM  

## Background  
The archaeology department of **Nova University** has digitized a collection of ancient pottery shards. Each shard is described by three attributes:

1. **ID** – a unique integer identifier.  
2. **Weight** – a floating‑point value (grams).  
3. **Era** – a short string (max 10 characters) indicating the historical period (e.g., `"Bronze"`).

The department wants a small C program that stores a *dynamic* list of shards, lets the user add new shards, and then allows inspection of any shard by its position in the list. The professor wants the students to practice **pointers**, **dynamic memory allocation**, and **pointer arithmetic**.

## Requirements  

Write a C program that:

1. **Defines** a `struct Shard` containing the three attributes listed above.  
2. **Allocates** an array of `struct Shard` on the heap whose size can grow as the user adds new shards.  
3. **Provides a menu** with the following options (the user selects a number):  
   1. **Add a shard** – Prompt for ID, weight, and era, then store the shard at the end of the current list.  
   2. **Display a shard** – Prompt for an index `i` (0‑based). Use a *separate function* named `displayShard` that receives a pointer to a `struct Shard` and prints the shard’s details in the format shown below.  
   3. **List all shards** – Walk through the dynamic array using **pointer arithmetic** (no array indexing `[]`) and print each shard’s details.  
   4. **Exit** – Terminates the program. *(The exit option **must** be present and clearly numbered in the menu.)*  

4. **Manages memory** correctly:  
   * When the list needs to grow, reallocate the array using `realloc`.  
   * Upon exiting, free any allocated memory.  

5. **Handles invalid input** gracefully (e.g., requesting a shard at an out‑of‑range index should print an error message and return to the menu).

## Example Interaction  

```
=== Shard Manager ===
1. Add a shard
2. Display a shard
3. List all shards
4. Exit
Choose an option: 1

Enter ID: 101
Enter weight (g): 23.5
Enter era (max 10 chars): Bronze
Shard added.

=== Shard Manager ===
1. Add a shard
2. Display a shard
3. List all shards
4. Exit
Choose an option: 1

Enter ID: 202
Enter weight (g): 45.2
Enter era (max 10 chars): Iron
Shard added.

=== Shard Manager ===
1. Add a shard
2. Display a shard
3. List all shards
4. Exit
Choose an option: 2

Enter index of shard to display: 0
Shard #0:
  ID   : 101
  Weight: 23.50 g
  Era   : Bronze

=== Shard Manager ===
1. Add a shard
2. Display a shard
3. List all shards
4. Exit
Choose an option: 3

Shard #0:
  ID   : 101
  Weight: 23.50 g
  Era   : Bronze
Shard #1:
  ID   : 202
  Weight: 45.20 g
  Era   : Iron

=== Shard Manager ===
1. Add a shard
2. Display a shard
3. List all shards
4. Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct` named `Shard`.  
* **Function Requirement** – The logic for displaying the details of **one specific shard** must be placed in a function with the exact prototype:  
  ```c
  void displayShard(const struct Shard *s);
  ```  
* **Pointer Arithmetic Requirement** – When listing all shards (menu option 3), you **must** traverse the dynamic array using pointer arithmetic (`ptr = ptr + 1;`) and **must not** use the subscript operator `[]`.  
* **Menu Exit Requirement** – The menu must include a clearly numbered option (e.g., `4. Exit`) that terminates the program.  

*Optional (for extra credit)*: Implement input validation so that the era string is truncated to 10 characters if the user enters a longer word.  

---  

*The problem is deliberately scoped for students who have just learned about pointers, dynamic allocation, and pointer arithmetic, while also reinforcing good modular design.*

---

## Problem 4 - openai/gpt-oss-120b - Iteration 54
# STEP 1: PROBLEM  

## Background  
The university’s archaeology department is digitizing its collection of artifacts. Each artifact has a **name**, the **year it was discovered**, and an **estimated monetary value**. The department wants a simple console program that stores a list of artifacts in memory, lets a user add new entries, view the current list, look up a specific artifact, and remove an artifact when it is loaned out.  

Because the class has just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of artifacts directly through pointers rather than using array‑index notation.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Artifact` that contains:  
     * `char name[51]` – the artifact’s name (max 50 characters, null‑terminated).  
     * `int year` – the year the artifact was discovered.  
     * `double value` – estimated monetary value in dollars.  

2. **Dynamic Storage**  
   * The program must allocate a dynamic array of `Artifact` objects on the heap (using `malloc`/`realloc` or `new`).  
   * The array may grow as new artifacts are added.  

3. **Menu‑driven Interface** (the menu is **required**).  
   * Display a menu with the following options:  
     1. **Add an artifact** – prompt for name, year, and value, then append it to the array.  
     2. **List all artifacts** – print each artifact’s details in the order they were added.  
     3. **Find an artifact by name** – ask for a name, search the array, and display the matching artifact (if any).  
     4. **Remove an artifact by name** – ask for a name, delete the first matching artifact, and shrink the array accordingly.  
     5. **EXIT** – terminate the program. *(The number/keyword for this option must be clearly stated.)*  

4. **Pointer Arithmetic**  
   * All traversals of the artifact array (e.g., listing, searching, removing) must be performed with pointer arithmetic (`ptr`, `ptr+1`, etc.). **Do not** use the subscript operator `[]` for these operations.  

5. **Functions**  
   * Implement a function `void displayArtifact(const struct Artifact *a);` that prints the details of a single artifact in the format shown in the example.  
   * All other functionality (adding, listing, searching, removing) may be placed in additional helper functions, but **no** other function may directly print an artifact’s fields; they must call `displayArtifact`.  

6. **Memory Management**  
   * When the program exits, release any dynamically allocated memory.  

---

## Example Interaction  

```
=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 1

Enter artifact name: Golden Mask
Enter discovery year: 1922
Enter estimated value: 1250000.50
Artifact added.

=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 1

Enter artifact name: Clay Pot
Enter discovery year: 1985
Enter estimated value: 3500
Artifact added.

=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 2

--- Artifact List ---
Name: Golden Mask
Year: 1922
Value: $1250000.50

Name: Clay Pot
Year: 1985
Value: $3500.00
--------------------

=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 3

Enter name to find: Clay Pot
--- Artifact Found ---
Name: Clay Pot
Year: 1985
Value: $3500.00
-----------------------

=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 4

Enter name to remove: Golden Mask
Artifact removed.

=== Artifact Tracker ===
1) Add an artifact
2) List all artifacts
3) Find an artifact by name
4) Remove an artifact by name
5) EXIT
Select an option: 5

Goodbye!
```

*Note:* The output formatting of the artifact details must be performed **only** by `displayArtifact`.

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Artifact`.  
* **Display Function** – The logic for displaying the details of **ONE** specific artifact must be in a function named `displayArtifact`.  
* **Pointer‑Only Traversal** – When iterating over the dynamic array, use pointer arithmetic (`Artifact *p = base; p < end; ++p`) rather than array indexing (`array[i]`).  
* **Menu Exit Option** – The menu must contain a clearly labeled option (e.g., `5) EXIT`) that terminates the program.  
* **Memory Clean‑up** – All allocated memory must be freed before program termination.  

---  

Write a program that satisfies the above specifications, demonstrating correct use of pointers, pointer arithmetic, dynamic memory, and modular design.

---

## Problem 5 - openai/gpt-oss-120b - Iteration 55
# STEP 1: PROBLEM  

## Background  
The university’s **Campus Navigation System** stores the locations of all campus buildings in a dynamically allocated array. Each building is described by a `struct Building` that contains the building’s name (a short string) and its distance in meters from the main gate.  

Your task is to write a small C program that lets a user **search** for a building by name and **display** its information. The program must demonstrate the use of pointers, pointer arithmetic, and dynamic memory management.

## Requirements  

1. **Data structure**  
   * Define a `struct Building` with the following members:  
     ```c
     char name[32];      // building name, null‑terminated
     int  distance;      // distance from the main gate (meters)
     ```  

2. **Dynamic allocation**  
   * At program start, read an integer `N` (1 ≤ N ≤ 100) – the number of buildings.  
   * Allocate an array of `N` `struct Building` objects on the **heap** using `malloc`.  

3. **Input of building data**  
   * For each building, read a line containing the name (single word, no spaces) and the distance, e.g.:  
     ```
     Library 250
     ```

4. **Menu** (must be presented after the data are read)  
   * The menu must contain the following options (the numbers are mandatory):  
     ```
     1. Search for a building
     2. List all buildings
     3. EXIT
     ```  
   * The program repeats the menu until the user selects **3. EXIT**.

5. **Option 1 – Search**  
   * Prompt the user to enter a building name.  
   * Using **pointer arithmetic only** (no array indexing `[]`), scan the dynamically allocated array to find a building whose `name` matches the query (case‑sensitive).  
   * If found, call a function `void displayBuilding(const struct Building *b);` that prints the building’s details in the format:  
     ```
     Building: <name>, Distance from gate: <distance> meters
     ```  
   * If not found, print:  
     ```
     Building not found.
     ```

6. **Option 2 – List all**  
   * Iterate through the array (again using only pointer arithmetic) and call `displayBuilding` for each entry.

7. **Cleanup**  
   * Before terminating, free the memory allocated for the building array.

## Example Input / Output  

```
Enter number of buildings: 3
Library 250
Gym 120
Cafeteria 80

--- Campus Navigation Menu ---
1. Search for a building
2. List all buildings
3. EXIT
Choose an option: 2

Building: Library, Distance from gate: 250 meters
Building: Gym, Distance from gate: 120 meters
Building: Cafeteria, Distance from gate: 80 meters

--- Campus Navigation Menu ---
1. Search for a building
2. List all buildings
3. EXIT
Choose an option: 1
Enter building name: Gym
Building: Gym, Distance from gate: 120 meters

--- Campus Navigation Menu ---
1. Search for a building
2. List all buildings
3. EXIT
Choose an option: 3
Goodbye!
```

## ### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be represented by a `struct Building`.  
* **Function requirement** – The logic for displaying a single building’s details must reside in a function named `displayBuilding`. Its prototype must be exactly:  
  ```c
  void displayBuilding(const struct Building *b);
  ```  
* **Pointer arithmetic only** – When traversing the building array (both for searching and listing), you may **not** use the subscript operator `[]`. Use pointer increment/decrement (`ptr++`, `ptr + i`, etc.).  
* **Menu requirement** – The program must present a menu as described, and option **3** must be the explicit “EXIT” choice.  
* **Single‑function rule** – Apart from `main` and `displayBuilding`, you may not add additional user‑defined functions. All other logic must be placed inside `main`.  

Write the program in standard C (C99 or later). Ensure it compiles without warnings and runs correctly on typical test cases.

---

## Problem 6 - openai/gpt-oss-120b - Iteration 56
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its inventory system. Each book in the collection is represented by a small record that stores the book’s **ISBN**, **title**, and the **number of copies** currently on the shelf. The library staff wants a simple console program that can store a fixed‑size list of books, let the user add new books, look up a book by its ISBN, and display all stored books.  

Because the course has just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of book records through pointers rather than using the usual `array[index]` syntax.

## Requirements  

1. Define a `struct Book` containing:  
   * `char isbn[14];`   // 13‑digit ISBN plus terminating null  
   * `char title[51];` // up to 50 characters plus terminating null  
   * `int copies;`  

2. The program shall maintain an array capable of holding **up to 20** `Book` records.  

3. Present a **menu** that repeats until the user chooses to exit. The menu must contain the following options (the number shown is the option the user must type):  

   1. **Add a new book** – Prompt for ISBN, title, and copies. If the array is already full, display an error message.  
   2. **Find a book by ISBN** – Prompt for an ISBN, search the array, and if found call a function `displayBook` (see below) to show its details; otherwise print “Book not found.”  
   3. **List all books** – Traverse the whole array and call `displayBook` for each stored record.  
   4. **Exit** – Terminate the program.  

4. All traversals of the book array **must be performed using pointer arithmetic** (e.g., incrementing a `Book *` pointer). Direct indexing such as `books[i]` is **not allowed**.  

5. The function `void displayBook(const Book *p)` must receive a pointer to a `Book` and print the ISBN, title, and number of copies in a readable format.  

6. Input validation is minimal: you may assume the user enters data of the correct type and length.

## Example Input / Output  

```
--- Library Inventory Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added successfully.

--- Library Inventory Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Choose an option: 2

Enter ISBN to search: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

--- Library Inventory Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Choose an option: 3

ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

--- Library Inventory Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book` as described.  
* **Function Requirement** – The details of a single book must be displayed by a function named `displayBook`.  
* **Pointer‑Arithmetic Requirement** – All loops that walk through the array of books must use a pointer (`Book *ptr`) and pointer increment (`ptr++`). Direct array indexing (`books[i]`) is prohibited.  
* **Menu Requirement** – The program must present a menu and **must include an explicit “Exit” option (option 4 in the example)** that terminates the program.  

Write the program in C (C99 or later) satisfying all the above specifications.

---

## Problem 7 - openai/gpt-oss-120b - Iteration 57
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its inventory system. Each book in the collection is represented by a small record that stores the book’s ISBN (as a 13‑digit integer), the title (a short string), and the number of copies currently on the shelf. The library wants a simple command‑line tool that lets a librarian **add**, **list**, **search**, and **remove** books while practising pointer arithmetic.

## Requirements  
Write a C program that manages an array of `Book` structures dynamically allocated on the heap. The program must provide a text‑based menu with the following options:

1. **Add a new book** – Prompt for ISBN, title, and copy count, then store the new record at the end of the current array (use `realloc` to grow the array).  
2. **List all books** – Display every stored book in the order they were added.  
3. **Search by ISBN** – Prompt for an ISBN, locate the matching book using pointer arithmetic (do **not** use array indexing `[]`), and display its details via a helper function `displayBook`. If the ISBN is not found, print “Book not found.”  
4. **Remove a book** – Prompt for an ISBN, locate the book using pointer arithmetic, remove it by shifting the later elements forward, and shrink the array with `realloc`. If the ISBN is not found, print “Book not found.”  
5. **Exit** – Terminate the program gracefully, freeing all allocated memory.

The program should continue to show the menu after each operation until the user selects **Exit**.

### Input / Output Example  

```
=== Library Inventory Menu ===
1. Add Book
2. List Books
3. Search by ISBN
4. Remove Book
5. Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies on shelf: 4
Book added.

=== Library Inventory Menu ===
1. Add Book
2. List Books
3. Search by ISBN
4. Remove Book
5. Exit
Choose an option: 2

--- Book List ---
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Inventory Menu ===
1. Add Book
2. List Books
3. Search by ISBN
4. Remove Book
5. Exit
Choose an option: 3

Enter ISBN to search: 9780131103627
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Inventory Menu ===
1. Add Book
2. List Books
3. Search by ISBN
4. Remove Book
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity must be a `struct` named `Book` containing at least:
   - `unsigned long long isbn;`
   - `char title[101];`  (maximum 100 characters + null terminator)
   - `int copies;`

2. **Function Requirement** – The logic for displaying the details of **one** specific book must reside in a function with the exact prototype:  

   ```c
   void displayBook(const Book *b);
   ```

   This function must be called from the search operation (and may be reused elsewhere).

3. **Pointer Arithmetic** – All traversals of the dynamic array (e.g., in list, search, remove) must use pointer arithmetic (`*ptr`, `ptr + i`, etc.) **without** employing the array subscript operator `[]`.

4. **Memory Management** – Use `malloc`/`realloc` to create and resize the array, and `free` all allocated memory before exiting.

5. **Menu Exit Option** – The menu must include a distinct option (number **5**) labeled “Exit” that terminates the program.  

6. **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but the entire solution must be contained in a single source file.  

7. **No Global Variables** – All data, including the pointer to the dynamic array and its size, must be managed inside `main` (or passed explicitly to helper functions).  

Follow these constraints closely; they are part of the grading rubric.

---

## Problem 8 - openai/gpt-oss-120b - Iteration 58
# STEP 1: PROBLEM  

## Background  
The campus library has just digitized its catalogue of **books**. Each book record stores the title, the year it was published, and the number of copies currently on the shelf. The library wants a small console program that lets a user browse the catalogue, look up a specific book, and update the number of copies when a book is borrowed or returned.  

Because the course has just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of book records directly through pointers rather than using array indexing (`[]`).  

## Requirements  

Write a C program that:

1. **Defines a `struct Book`** containing:  
   - `char title[51];`   // up to 50 characters plus terminating `\0`  
   - `int  year;`  
   - `int  copies;`  

2. **Creates an array of 5 `Book` objects** with data of your choice (hard‑coded in the program).  

3. **Presents a menu** that repeats until the user chooses to exit:  

   | Option | Description |
   |--------|-------------|
   | 1      | List all books (display title, year, copies) |
   | 2      | Search for a book by title (exact match, case‑sensitive) and display its details |
   | 3      | Borrow a book – decrement `copies` by 1 (only if copies > 0) |
   | 4      | Return a book – increment `copies` by 1 |
   | 5      | **EXIT** the program |

4. For option **2**, the program must call a function `void displayBook(const Book *b)` that prints the information of the supplied book.  

5. All traversals of the book array **must be performed using pointer arithmetic** (e.g., `Book *p = books; p < books + 5; ++p`). Direct indexing (`books[i]`) is not allowed.  

6. The program should validate user input where appropriate (e.g., cannot borrow a book with zero copies).  

## Example Input / Output  

```
=== Library Catalogue ===
1. List all books
2. Search by title
3. Borrow a book
4. Return a book
5. EXIT
Choose an option: 1

Title: The C Programming Language   Year: 1978   Copies: 3
Title: Clean Code                  Year: 2008   Copies: 2
Title: Introduction to Algorithms  Year: 1990   Copies: 4
Title: Design Patterns             Year: 1994   Copies: 1
Title: The Pragmatic Programmer   Year: 1999   Copies: 5

=== Library Catalogue ===
1. List all books
2. Search by title
3. Borrow a book
4. Return a book
5. EXIT
Choose an option: 2
Enter title to search: Clean Code

Title: Clean Code   Year: 2008   Copies: 2

=== Library Catalogue ===
1. List all books
2. Search by title
3. Borrow a book
4. Return a book
5. EXIT
Choose an option: 3
Enter title to borrow: Design Patterns
Book borrowed successfully. Remaining copies: 0

=== Library Catalogue ===
1. List all books
2. Search by title
3. Borrow a book
4. Return a book
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented by a `struct Book`.  
- **Display Function:** Details of a single book must be printed by a function named `displayBook` with the prototype `void displayBook(const Book *b);`.  
- **Pointer Arithmetic Only:** All access to the `books` array must use pointers (`*`, `->`, `++`, `--`, pointer addition/subtraction). The use of the subscript operator `[]` on the `books` array is prohibited.  
- **Menu Exit Option:** The menu must include a distinct option (number **5**) labeled **EXIT** that terminates the program.  

*Note:* The program should be written in standard C (C99 or later) and compile without warnings.

---

## Problem 9 - openai/gpt-oss-120b - Iteration 59
# STEP 1: PROBLEM  

## Background  
The kingdom’s archivist is digitising the inventory of **magical treasure chests** stored in the royal vault.  
Each chest has a unique identifier, a weight (in kilograms), and a description of its contents.  
The archivist wants a small C program that can store a collection of chests, allow the user to add new chests, list all stored chests, and display the details of a single chest on request.  

Because the vault’s records are massive, the archivist insists that the program manipulate the collection **only with pointers and pointer arithmetic** – no array‑subscript notation (`[]`) may be used for traversing the list.

## Requirements  

1. **Data Representation**  
   * Define a `struct Chest` that contains:  
     - `int id;`     // unique identifier  
     - `float weight;` // weight in kilograms  
     - `char description[51];` // null‑terminated string (max 50 characters)  

2. **Program Functionality**  
   * Present a simple text menu (repeat until the user chooses to exit):  
     1. **Add a new chest** – prompt for `id`, `weight`, and `description`. Store the chest in a dynamically allocated array that can grow as needed.  
     2. **List all chests** – print the `id` and `weight` of every chest stored so far.  
     3. **Show chest details** – ask for an `id` and display the full information (`id`, `weight`, `description`) of the matching chest.  
     4. **Exit** – terminate the program.  

   * The program must **use pointer arithmetic** to iterate over the dynamic array when listing or searching chests (e.g., `Chest *p = base; p < base + count; ++p`). Direct indexing (`base[i]`) is not allowed in those parts.  

3. **Memory Management**  
   * The array of `Chest` objects must be allocated with `malloc`/`realloc`.  
   * All allocated memory must be freed before the program exits.  

4. **User Interaction**  
   * Input is read from `stdin`; output is written to `stdout`.  
   * The menu should be redisplayed after each operation (except Exit).  

## Example Input / Output  

```
--- Royal Vault Inventory ---
1) Add a new chest
2) List all chests
3) Show chest details
4) Exit
Choose an option: 1

Enter chest id: 101
Enter weight (kg): 12.5
Enter description (max 50 chars): Golden Crown
Chest added.

--- Royal Vault Inventory ---
1) Add a new chest
2) List all chests
3) Show chest details
4) Exit
Choose an option: 1

Enter chest id: 202
Enter weight (kg): 7.3
Enter description (max 50 chars): Emerald Scepter
Chest added.

--- Royal Vault Inventory ---
1) Add a new chest
2) List all chests
3) Show chest details
4) Exit
Choose an option: 2

Stored chests:
ID: 101, Weight: 12.50 kg
ID: 202, Weight: 7.30 kg

--- Royal Vault Inventory ---
1) Add a new chest
2) List all chests
3) Show chest details
4) Exit
Choose an option: 3

Enter chest id to view: 202
Chest Details:
ID: 202
Weight: 7.30 kg
Description: Emerald Scepter

--- Royal Vault Inventory ---
1) Add a new chest
2) List all chests
3) Show chest details
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Chest` as described above.  
2. **Function Requirement** – The logic for displaying the full details of a single chest **must** be placed in a function with the exact prototype:  

   ```c
   void displayChest(const struct Chest *c);
   ```  

3. **Pointer‑Arithmetic Requirement** – When iterating over the dynamic array (for listing or searching), you **must** use pointer arithmetic (`*p`, `p++`, `p + n`, etc.). Direct array indexing (`array[i]`) is prohibited in those sections.  
4. **Menu Exit Requirement** – The menu must include an explicit option to **Exit** the program, numbered **4** as shown in the example. Selecting this option ends the program after freeing all allocated memory.  

*The problem is intended for students who have just completed a unit on pointers and pointer arithmetic; therefore, no advanced C features (e.g., linked lists, file I/O) are required.*

---

## Problem 10 - openai/gpt-oss-120b - Iteration 60
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its computer system. The new system must keep a **tiny in‑memory catalogue** of the most‑recently added books. Each book is represented by a `struct` containing its ISBN, title, and the number of copies available. Because the catalogue is stored in a fixed‑size array, you will need to use **pointers** and **pointer arithmetic** to navigate the array, add new entries, and look up information.

## Requirements  

Write a C program that implements a simple menu‑driven catalogue with the following capabilities:

1. **Add a Book** – Prompt the user for ISBN (a 13‑digit integer), title (a single‑word string, max 30 characters), and copies (non‑negative integer).  
   - The new book is stored at the first free slot in the array.  
   - If the array is full (capacity 10), display an error message and do not add the book.

2. **Find a Book by ISBN** – Ask for an ISBN, search the array using pointer arithmetic, and display the book’s details if found; otherwise, print “Book not found”.

3. **List All Books** – Walk through the array with pointers and print the details of every stored book in the order they were added.

4. **Remove a Book** – Ask for an ISBN, locate the book, and remove it by shifting all later elements one position toward the front (again using pointers). Decrease the count of stored books.

5. **Exit** – Terminate the program.

The program must continue to show the menu after each operation until the user selects the **Exit** option.

## Example Input / Output  

```
=== Library Catalogue ===
1) Add a Book
2) Find a Book by ISBN
3) List All Books
4) Remove a Book
5) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: CProgramming
Enter copies: 3
Book added successfully.

=== Library Catalogue ===
1) Add a Book
2) Find a Book by ISBN
3) List All Books
4) Remove a Book
5) EXIT
Choose an option: 3

Current books (3 total):
ISBN: 9780131103627 | Title: CProgramming | Copies: 3

=== Library Catalogue ===
1) Add a Book
2) Find a Book by ISBN
3) List All Books
4) Remove a Book
5) EXIT
Choose an option: 5

Goodbye!
```

*(The example shows only a subset of possible interactions.)*

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity must be a `struct` named `Book` with the fields:  
   ```c
   typedef struct {
       long long isbn;          // 13‑digit ISBN
       char title[31];          // null‑terminated string, max 30 chars
       int copies;              // non‑negative
   } Book;
   ```

2. **Function Requirement** – The logic for displaying the details of **one specific book** must be encapsulated in a function with the exact prototype:  
   ```c
   void displayBook(const Book *b);
   ```

3. **Pointer Arithmetic** – All traversals of the book array (searching, listing, shifting during removal) must be performed with pointers and pointer arithmetic; use of array indexing (`books[i]`) for these operations is **not allowed**.

4. **Menu Implementation** – The menu must include a distinct option to **EXIT** the program. The option number must be **5** (as shown in the example). Selecting this option ends the program.

5. **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but all code must reside in a single source file.

6. **Maximum Capacity** – The catalogue can hold at most **10** books. Use a constant (e.g., `#define MAX_BOOKS 10`) to represent this limit.  

Follow these constraints closely; the grading will verify each one.

---

## Problem 11 - llama-3.3-70b-versatile - Iteration 46
# STEP 1: PROBLEM
In a small library, books are organized on shelves using a unique identifier for each book. The library wants to create a simple program to manage its book collection. The program should allow users to add, remove, and display books. Each book has a unique identifier (ID), title, author, and number of pages.

The program should utilize pointers and pointer arithmetic to efficiently manage the collection of books.

## REQUIREMENTS:
1. The program should allow users to add a new book to the collection.
2. The program should allow users to remove a book from the collection by its ID.
3. The program should display all books in the collection.
4. The program should display the details of a specific book by its ID.

## EXAMPLE:
If the user adds two books with the following details:
- Book 1: ID = 1, Title = "Book1", Author = "Author1", Pages = 100
- Book 2: ID = 2, Title = "Book2", Author = "Author2", Pages = 200

The program should display:
- All books: 
  - Book 1: ID = 1, Title = "Book1", Author = "Author1", Pages = 100
  - Book 2: ID = 2, Title = "Book2", Author = "Author2", Pages = 200
- Book with ID 1: 
  - Book 1: ID = 1, Title = "Book1", Author = "Author1", Pages = 100

### CONSTRAINTS:
- Must use a 'struct' to represent a book.
- The logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu options are:
  - 1: Add a new book
  - 2: Remove a book by ID
  - 3: Display all books
  - 4: Display a book by ID
  - 5: EXIT the program
- The program must dynamically allocate memory for each new book and deallocate memory when a book is removed.

Note: The program should handle invalid inputs and edge cases, such as removing a non-existent book or displaying a book with an invalid ID.

---

## Problem 12 - llama-3.3-70b-versatile - Iteration 47
# STEP 1: PROBLEM
In a university setting, student records are maintained using a database system. The system stores information such as the student's ID, name, and grade point average (GPA). To efficiently manage these records, the system utilizes pointers and pointer arithmetic to navigate through the database. 

You are tasked with designing a simple console-based program that allows users to interact with this database system. The program should enable users to add new student records, display all existing records, and search for a specific student by their ID.

### REQUIREMENTS
- The program must allow users to add new student records to the database.
- The program must be able to display all existing student records in the database.
- The program must enable users to search for a specific student by their ID and display their details.
- The database should be represented using an array of structures, where each structure represents a student record.
- The program must handle a maximum of 100 student records.

### EXAMPLE
If the database contains the following student records:
- Student 1: ID = 1, Name = "John Doe", GPA = 3.5
- Student 2: ID = 2, Name = "Jane Doe", GPA = 3.8
- Student 3: ID = 3, Name = "Bob Smith", GPA = 3.2

When the user chooses to display all records, the program should output:
```
Student ID: 1, Name: John Doe, GPA: 3.5
Student ID: 2, Name: Jane Doe, GPA: 3.8
Student ID: 3, Name: Bob Smith, GPA: 3.2
```
If the user searches for a student with ID = 2, the program should output:
```
Student ID: 2, Name: Jane Doe, GPA: 3.8
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (student record).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all user interactions and database operations.
- The program must include a menu with the following options:
  1. Add new student record
  2. Display all student records
  3. Search for a student by ID
  4. EXIT the program

Note: The user can exit the program by selecting the 'EXIT' option (option 4).

---

## Problem 13 - llama-3.3-70b-versatile - Iteration 48
# STEP 1: PROBLEM
You are the curator of a university museum, and you need to manage the collection of artifacts. Each artifact has a unique identifier, name, type, and year of acquisition. To efficiently store and retrieve information about these artifacts, you decide to use an array of structures, where each structure represents an artifact. You want to create a program that allows you to add, display, and search for artifacts in the collection.

The program should have the following functionality:
1. Initialize an array of structures to store information about the artifacts.
2. Provide a menu-driven interface to add, display, and search for artifacts.
3. When adding an artifact, prompt the user to enter the unique identifier, name, type, and year of acquisition.
4. When displaying artifacts, show all the artifacts in the collection.
5. When searching for an artifact, prompt the user to enter the unique identifier or name of the artifact, and display the details of the matching artifact(s).

### EXAMPLE
If the user adds the following artifacts:
- Artifact 1: ID = 1, Name = "Vase", Type = "Ceramic", Year = 2010
- Artifact 2: ID = 2, Name = "Painting", Type = "Art", Year = 2015
- Artifact 3: ID = 3, Name = "Sculpture", Type = "Metal", Year = 2020

The program should display the following output when the user chooses to display all artifacts:
```
Artifact 1:
ID: 1
Name: Vase
Type: Ceramic
Year: 2010

Artifact 2:
ID: 2
Name: Painting
Type: Art
Year: 2015

Artifact 3:
ID: 3
Name: Sculpture
Type: Metal
Year: 2020
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (i.e., the artifact).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu-driven interface.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.
- The menu options are as follows:
  1. Add an artifact
  2. Display all artifacts
  3. Search for an artifact by ID
  4. Search for an artifact by name
  5. EXIT the program

Note: The program should use pointer arithmetic to manipulate the array of structures.

---

## Problem 14 - llama-3.3-70b-versatile - Iteration 49
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their name, student ID, and GPA. You want to create a program to manage this data using pointers and pointer arithmetic. The program should allow users to add students, display all students, and search for a specific student by ID.

The program will store student information in a dynamically allocated array of structures, where each structure represents a student. The user will interact with the program through a simple menu.

### REQUIREMENTS
1. The program must store student information in a dynamically allocated array of structures.
2. The program must provide a menu for the user to add a student, display all students, search for a student by ID, and exit the program.
3. When adding a student, the program must prompt the user to enter the student's name, ID, and GPA.
4. When displaying all students, the program must print each student's name, ID, and GPA.
5. When searching for a student by ID, the program must display the student's name, ID, and GPA if found, or a message indicating that the student was not found.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add student
2. Display all students
3. Search for student by ID
4. Exit

Enter your choice: 1
Enter student name: John Doe
Enter student ID: 12345
Enter student GPA: 3.5

Menu:
1. Add student
2. Display all students
3. Search for student by ID
4. Exit

Enter your choice: 2
Student 1:
Name: John Doe
ID: 12345
GPA: 3.5

Menu:
1. Add student
2. Display all students
3. Search for student by ID
4. Exit

Enter your choice: 3
Enter student ID to search: 12345
Student found:
Name: John Doe
ID: 12345
GPA: 3.5
```

### CONSTRAINTS
* The solution must be implemented using a `struct` to represent the student data entity.
* The logic for displaying the details of all students must be in a function called `displayAllStudents`.
* The logic for searching for a student by ID must be in a function called `searchStudent`.
* The program must use pointer arithmetic to access and manipulate the student data.
* The menu option to exit the program is option 4.

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks.

---

## Problem 15 - llama-3.3-70b-versatile - Iteration 50
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As part of an introductory programming course, you've been tasked with designing a simple program to manage student records using pointers and pointer arithmetic. The program should allow users to add, display, and modify student records.

The background story is that the university wants to automate its student record-keeping system. The system should store the student's ID, name, and GPA. The university wants a simple text-based interface to interact with the system.

The program's functionality requirements are as follows:
1. Initialize an array of student records with a fixed size (e.g., 10).
2. Provide a menu-driven interface to add, display, and modify student records.
3. When adding a record, prompt the user for the student's ID, name, and GPA.
4. When displaying records, show all existing student records.
5. When modifying a record, prompt the user for the student's ID and then update the corresponding record's name and GPA.
6. Handle cases where the array is full or empty.

Here is a simple example of expected input/output:
```
Menu:
1. Add student record
2. Display student records
3. Modify student record
4. Exit
Choose an option: 1
Enter student ID: 1
Enter student name: John Doe
Enter student GPA: 3.5

Menu:
1. Add student record
2. Display student records
3. Modify student record
4. Exit
Choose an option: 2
Student ID: 1, Name: John Doe, GPA: 3.5

Menu:
1. Add student record
2. Display student records
3. Modify student record
4. Exit
Choose an option: 3
Enter student ID: 1
Enter new student name: Jane Doe
Enter new student GPA: 3.8

Menu:
1. Add student record
2. Display student records
3. Modify student record
4. Exit
Choose an option: 2
Student ID: 1, Name: Jane Doe, GPA: 3.8
```

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu and user input.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4. 
- The program should handle memory allocation and deallocation using pointers and pointer arithmetic.

---

## Problem 16 - llama-3.3-70b-versatile - Iteration 51
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. To efficiently manage the books, the library uses a pointer-based system to keep track of the books on each shelf. As a programmer, you are tasked with designing a simple program that demonstrates the use of pointers and pointer arithmetic to manage the books on a shelf.

The program should allow users to add books to the shelf, display the details of all books on the shelf, and display the details of a specific book. The shelf can hold a maximum of 100 books.

### REQUIREMENTS
1. The program should have a menu-driven interface with the following options:
   - Add a book to the shelf
   - Display all books on the shelf
   - Display a specific book
   - Exit the program
2. The program should use a struct to represent a book, with fields for the unique identifier, title, author, and publication year.
3. The program should use pointers and pointer arithmetic to manage the books on the shelf.
4. The program should validate user input to ensure that the shelf does not exceed its maximum capacity.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book to the shelf
2. Display all books on the shelf
3. Display a specific book
4. Exit the program
Enter your choice: 1
Enter book ID: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
Book added successfully!

Menu:
1. Add a book to the shelf
2. Display all books on the shelf
3. Display a specific book
4. Exit the program
Enter your choice: 2
Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020

Menu:
1. Add a book to the shelf
2. Display all books on the shelf
3. Display a specific book
4. Exit the program
Enter your choice: 3
Enter book ID: 1
Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020

Menu:
1. Add a book to the shelf
2. Display all books on the shelf
3. Display a specific book
4. Exit the program
Enter your choice: 4
Exiting the program...
```

### CONSTRAINTS
- The solution must be implemented using a single struct to represent a book.
- The logic for displaying the details of all books on the shelf must be in a function called `displayAllBooks`.
- The logic for displaying the details of a specific book must be in a function called `displayBook`.
- The program must include a specific menu option to EXIT the program, which is option 4.
- The solution must use pointers and pointer arithmetic to manage the books on the shelf.

---

## Problem 17 - llama-3.3-70b-versatile - Iteration 52
# STEP 1: PROBLEM
You are a curator at a local museum, tasked with managing the collection of artifacts. Each artifact has a unique identifier, name, description, and acquisition year. To efficiently store and manage this information, you decide to create a program that utilizes pointers and pointer arithmetic to handle the data.

The program should allow users to add new artifacts, display all artifacts, and search for a specific artifact by its identifier. The identifiers are integers starting from 1 and incrementing for each new artifact added.

### REQUIREMENTS
1. The program must allow users to add new artifacts with their details (identifier, name, description, and acquisition year).
2. The program must display all artifacts in the collection, showing their details.
3. The program must allow users to search for a specific artifact by its identifier and display its details if found.
4. The program must handle memory allocation for the artifact collection dynamically.

### EXAMPLE INPUT/OUTPUT
- When adding an artifact: The user inputs the name, description, and acquisition year. The identifier is automatically assigned based on the number of artifacts already in the collection.
- Displaying all artifacts: The program lists all artifacts with their details.
- Searching for an artifact: The user inputs the identifier of the artifact to search for, and the program displays its details if the identifier is valid.

### CONSTRAINTS
- Must use a `struct` to represent an artifact, containing fields for the identifier, name, description, and acquisition year.
- Logic for displaying the details of all artifacts must be in a function called `displayAllArtifacts`.
- The solution must be implemented with a single function besides `main()` for handling user input and operations, named `handleUserInput`.
- The program must include a menu with the following options:
  1. Add a new artifact
  2. Display all artifacts
  3. Search for an artifact by identifier
  4. EXIT the program
- MANDATORY CONSTRAINT FOR MENU: The program must exit when the user selects option 4 (EXIT).

---

## Problem 18 - llama-3.3-70b-versatile - Iteration 53
# STEP 1: PROBLEM
In a small library, books are organized on shelves using a unique identifier for each book. The librarian wants a simple program to manage the books, focusing on the use of pointers and pointer arithmetic for efficient memory management. The program should allow the librarian to add books, display all books, and find a specific book by its identifier.

Background:
The library has a collection of books, each with a unique identifier, title, and author. The librarian needs a program that can efficiently store and retrieve information about these books.

Requirements:
1. The program must store book information in memory using pointers.
2. The program must provide options to add a new book, display all books, and find a book by its identifier.
3. The program must use pointer arithmetic to navigate through the stored book information.
4. The program must handle memory allocation and deallocation for the books.

### CONSTRAINTS
- Must use a 'struct' to represent the book, containing the unique identifier, title, and author.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must implement a menu-driven interface with the following options:
  1. Add a new book
  2. Display all books
  3. Find a book by identifier
  4. EXIT the program
- When the user chooses to EXIT, the program must free all allocated memory before terminating.

Example of expected Input/Output:
```
Menu:
1. Add a new book
2. Display all books
3. Find a book by identifier
4. EXIT

Choose an option: 1
Enter book identifier: 1
Enter book title: Introduction to CS
Enter book author: John Doe

Choose an option: 2
Book 1:
Identifier: 1
Title: Introduction to CS
Author: John Doe

Choose an option: 3
Enter book identifier to find: 1
Book found:
Identifier: 1
Title: Introduction to CS
Author: John Doe

Choose an option: 4
Exiting program...
```

---

## Problem 19 - llama-3.3-70b-versatile - Iteration 54
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a program to manage the books in your library. Each book has a title, author, and publication year. You want to store the information of all the books in an array and perform various operations on this array using pointers and pointer arithmetic.

Background:
The library has a collection of books, and the manager wants to be able to add new books, display the details of all books, and search for a specific book by its title.

Requirements:
1. The program must store the information of all the books in an array of structures, where each structure represents a book.
2. The program must have a function to add a new book to the array.
3. The program must have a function to display the details of all the books in the array.
4. The program must have a function to search for a specific book by its title and display its details.
5. The program must have a menu-driven interface to perform the above operations.

### CONSTRAINTS
- The solution must be implemented using pointers and pointer arithmetic.
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
- The program must include a menu option to EXIT the program. The EXIT option must be numbered as 5.

Example of expected Input/Output:
```
Menu:
1. Add a new book
2. Display all books
3. Search for a book by title
4. Display book details
5. EXIT

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Menu:
1. Add a new book
2. Display all books
3. Search for a book by title
4. Display book details
5. EXIT

Choose an option: 2
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Menu:
1. Add a new book
2. Display all books
3. Search for a book by title
4. Display book details
5. EXIT

Choose an option: 5
Exiting the program...
```
Note: The above example is a simplified representation of the expected input/output. The actual program may have more features and error handling.

---

## Problem 20 - llama-3.3-70b-versatile - Iteration 55
# STEP 1: PROBLEM
In a university setting, students are often required to manage their course enrollments and grades. To simplify this process, we want to create a program that uses pointers and pointer arithmetic to manage student records. The program should allow users to add, display, and update student information.

The program will store student records, each containing the student's ID, name, and grade point average (GPA). The background story is that the university wants to implement a simple system to keep track of student records, and we are tasked with designing this system.

The requirements for the program's functionality are as follows:
1. The program should allow users to add new student records.
2. The program should display all student records.
3. The program should allow users to update the GPA of a specific student.
4. The program should display the details of a specific student.

Here's a simple example of expected input/output:
```
Enter the number of students: 2
Enter student ID: 1
Enter student name: John
Enter student GPA: 3.5
Enter student ID: 2
Enter student name: Jane
Enter student GPA: 3.8

Displaying all students:
ID: 1, Name: John, GPA: 3.5
ID: 2, Name: Jane, GPA: 3.8

Enter the ID of the student to update: 1
Enter the new GPA: 3.6

Displaying all students:
ID: 1, Name: John, GPA: 3.6
ID: 2, Name: Jane, GPA: 3.8
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (student record).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all the operations (add, display, update).
- The program must include a menu with the following options:
  1. Add a new student
  2. Display all students
  3. Update a student's GPA
  4. Display a specific student's details
  5. EXIT the program
- The program must use pointer arithmetic to manage the student records.

Note: The menu option to EXIT the program is option 5. When this option is chosen, the program should terminate cleanly.

---

## Problem 21 - llama-3.3-70b-versatile - Iteration 56
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their name, student ID, and GPA. You want to create a program that can efficiently manage and display student information using pointers and pointer arithmetic.

Background: 
The university has a large number of students, and the system needs to be able to handle this data efficiently. The program should be able to store student information, display specific student details, and update student information.

Requirements:
1. The program should be able to store information about a maximum of 100 students.
2. The program should have a menu that allows users to:
   - Add a new student
   - Display all students
   - Display a specific student by ID
   - Update a student's GPA
   - Exit the program
3. The program should use pointers and pointer arithmetic to manage the student data.

Example:
If the user chooses to add a new student, they should be prompted to enter the student's name, ID, and GPA. If the user chooses to display all students, the program should display the name, ID, and GPA of all students in the database.

Example Input/Output:
```
Menu:
1. Add a new student
2. Display all students
3. Display a specific student by ID
4. Update a student's GPA
5. Exit

Enter your choice: 1
Enter student name: John Doe
Enter student ID: 12345
Enter student GPA: 3.5

Menu:
1. Add a new student
2. Display all students
3. Display a specific student by ID
4. Update a student's GPA
5. Exit

Enter your choice: 2
Student 1:
Name: John Doe
ID: 12345
GPA: 3.5
```

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the student data entity.
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The program must use a single array to store all student data, and pointers and pointer arithmetic to manage and access this data.
- If a menu is implemented, the program must include a specific menu option to EXIT the program, which is option 5. When this option is chosen, the program should terminate and return control to the operating system.

---

## Problem 22 - llama-3.3-70b-versatile - Iteration 57
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a programmer, you have been tasked with designing a simple program to manage student records using pointers and pointer arithmetic.

Background:
The program should be able to store student records, which include the student's ID, name, and GPA. The program should also be able to display the details of all students or a specific student.

Requirements:
1. The program should be able to store a maximum of 100 student records.
2. The program should have a menu that allows the user to:
   - Add a new student record
   - Display all student records
   - Display a specific student record by ID
   - Exit the program
3. When adding a new student record, the program should prompt the user to enter the student's ID, name, and GPA.

Example:
If the user chooses to add a new student record with ID 1, name "John Doe", and GPA 3.5, and then chooses to display all student records, the output should be:
```
Student ID: 1
Name: John Doe
GPA: 3.5
```

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the student record.
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The program must use pointer arithmetic to access and manipulate the student records.
- The program must include a menu option to EXIT the program, which is option 4.

Example Menu:
```
1. Add a new student record
2. Display all student records
3. Display a specific student record by ID
4. Exit the program
```

---

## Problem 23 - llama-3.3-70b-versatile - Iteration 58
# STEP 1: PROBLEM
You are a librarian responsible for managing a collection of books in a university library. Each book has a unique identifier, title, author, and publication year. You want to create a program to store and display information about these books. Since the number of books can be large, you want to use pointers and pointer arithmetic to efficiently manage the memory.

The program should allow users to add new books, display all books, and search for a specific book by its identifier. The user should be able to navigate through a menu to perform these operations.

### REQUIREMENTS
1. The program should store book information in a struct called `Book`.
2. The program should have a menu with the following options:
   - Add a new book
   - Display all books
   - Search for a book by identifier
   - Exit the program
3. When adding a new book, the program should prompt the user to enter the book's identifier, title, author, and publication year.
4. When displaying all books, the program should print the details of each book in the following format: "Identifier: XXX, Title: XXX, Author: XXX, Publication Year: XXX".
5. When searching for a book by identifier, the program should prompt the user to enter the identifier and then display the details of the book if found.

### EXAMPLE
Input:
```
1. Add a new book
Identifier: 1
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020
2. Add a new book
Identifier: 2
Title: Data Structures and Algorithms
Author: Jane Doe
Publication Year: 2019
3. Display all books
```
Output:
```
Identifier: 1, Title: Introduction to Computer Science, Author: John Smith, Publication Year: 2020
Identifier: 2, Title: Data Structures and Algorithms, Author: Jane Doe, Publication Year: 2019
```

### CONSTRAINTS
- Must use a `struct` to represent the `Book` entity.
- The solution must be implemented with a single function besides `main()`, called `manageBooks()`, which will contain the logic for the menu and book management.
- The program must use pointers and pointer arithmetic to manage the memory for the books.
- The `manageBooks()` function should dynamically allocate memory for each new book added.
- The program must have a specific menu option to EXIT the program, which is option 4.

Note: The program should handle memory deallocation when the user exits the program to prevent memory leaks.

---

## Problem 24 - llama-3.3-70b-versatile - Iteration 59
# STEP 1: PROBLEM
In a small university, the administration wants to keep track of the details of its students, including their names, student IDs, and GPAs. To efficiently manage this data, the administration has decided to use a C program that utilizes pointers and pointer arithmetic.

The program should be able to store student data in memory and perform basic operations such as displaying student details and calculating the average GPA of all students. The university has a limited number of students, so the program should be able to handle a maximum of 100 students.

The program's functionality should include the following requirements:
1. The program should prompt the user to input the number of students they want to store.
2. For each student, the program should ask for the student's name, student ID, and GPA, and store this data in memory using pointers and pointer arithmetic.
3. The program should have an option to display the details of all students.
4. The program should have an option to calculate and display the average GPA of all students.
5. The program should have an option to display the details of a specific student based on their student ID.

Here's a simple example of expected input/output:
```
Enter the number of students: 2
Enter student 1's name: John
Enter student 1's ID: 1234
Enter student 1's GPA: 3.5
Enter student 2's name: Alice
Enter student 2's ID: 5678
Enter student 2's GPA: 3.8

Menu:
1. Display all students
2. Calculate average GPA
3. Display specific student
4. Exit

Enter your choice: 1
Student 1: John, ID: 1234, GPA: 3.5
Student 2: Alice, ID: 5678, GPA: 3.8
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student data entity.
- The logic for displaying the details of all students must be in a function called `displayAllStudents`.
- The logic for calculating and displaying the average GPA must be in a function called `calculateAverageGPA`.
- The logic for displaying the details of a specific student must be in a function called `displaySpecificStudent`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4. The program should terminate when the user chooses this option.

---

## Problem 25 - llama-3.3-70b-versatile - Iteration 60
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a simple cataloging system where each book is represented by its title, author, and publication year. To efficiently manage the collection, you need to create a program that stores information about each book and allows users to interact with the catalog.

The program should store the book information in memory using pointers and pointer arithmetic. The user should be able to add a new book to the catalog, display all books, and search for a specific book by title.

### REQUIREMENTS
1. The program must store book information in memory using pointers and pointer arithmetic.
2. The program must allow users to add new books to the catalog.
3. The program must display all books in the catalog.
4. The program must allow users to search for a specific book by title.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a new book:
Title: "Introduction to Computer Science"
Author: "John Doe"
Year: 2020

Add another book:
Title: "Data Structures and Algorithms"
Author: "Jane Smith"
Year: 2019

Display all books:
Book 1:
Title: "Introduction to Computer Science"
Author: "John Doe"
Year: 2020

Book 2:
Title: "Data Structures and Algorithms"
Author: "Jane Smith"
Year: 2019

Search for a book by title: "Introduction to Computer Science"
Book found:
Title: "Introduction to Computer Science"
Author: "John Doe"
Year: 2020
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for searching for a book by title must be in a function called `searchBookByTitle`.
- The program must have a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Search for a book by title
  4. EXIT (to exit the program)

If a menu is implemented, the program must include a specific menu option to EXIT the program by selecting option 4 or typing "EXIT".

---

## Problem 26 - llama-3.3-70b-versatile - Iteration 31
# STEP 1: PROBLEM
In a university setting, it's common to keep track of student information, including their names, student IDs, and grades. As a Computer Science professor, you want to design a program that uses pointers and pointer arithmetic to manage this information efficiently. The program should be able to store, display, and update student records.

Background:
The university has a limited number of students, and the program should be able to handle up to 100 students. Each student has a name, a unique student ID, and a grade point average (GPA).

Requirements:
1. The program should store student information in an array of structures, where each structure represents a student.
2. The program should have a menu-driven interface with the following options:
   - Add a new student record
   - Display all student records
   - Update a student record
   - Display the details of a specific student
   - Exit the program
3. The program should use pointers and pointer arithmetic to navigate and manipulate the student records.

Example Input/Output:
```
Menu:
1. Add a new student record
2. Display all student records
3. Update a student record
4. Display the details of a specific student
5. Exit the program

Choose an option: 1
Enter student name: John Doe
Enter student ID: S1234
Enter GPA: 3.5

Choose an option: 2
Student Records:
Name: John Doe, ID: S1234, GPA: 3.5

Choose an option: 4
Enter student ID: S1234
Name: John Doe, ID: S1234, GPA: 3.5
```

### CONSTRAINTS
- The program must use a `struct` to represent a student, with members for name, student ID, and GPA.
- The logic for displaying the details of one specific student must be in a function called `displayStudent`.
- The solution must be implemented using pointers and pointer arithmetic.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5. When this option is chosen, the program should terminate cleanly.

---

## Problem 27 - llama-3.3-70b-versatile - Iteration 32
# STEP 1: PROBLEM
Topic: Pointers and Pointer Arithmetic

Background: 
A university library wants to manage its collection of books using a simple program. The library has a large collection of books, and each book has a title, author, and publication year. The library wants to store the books in an array and perform various operations such as displaying the details of a specific book, searching for books by author, and updating the publication year of a book.

Requirements:
1. The program should store the books in an array of structures, where each structure represents a book with its title, author, and publication year.
2. The program should have a function to display the details of a specific book.
3. The program should have a function to search for books by author and display their details.
4. The program should have a function to update the publication year of a book.
5. The program should have a menu-driven interface to perform the above operations.

Example Input/Output:
```
Enter the number of books: 3
Enter title of book 1: Book1
Enter author of book 1: Author1
Enter publication year of book 1: 2010
Enter title of book 2: Book2
Enter author of book 2: Author2
Enter publication year of book 2: 2015
Enter title of book 3: Book3
Enter author of book 3: Author1
Enter publication year of book 3: 2020

Menu:
1. Display book details
2. Search for books by author
3. Update publication year
4. EXIT

Enter your choice: 1
Enter the index of the book (0-2): 1
Title: Book2
Author: Author2
Publication Year: 2015
```

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent a book.
- The logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The menu option to EXIT the program is '4' or the keyword 'EXIT'.
- If a menu is implemented, it must include options to perform the required operations, and the program should continue to run until the user chooses to EXIT. 
- The program should use pointer arithmetic to access and manipulate the book structures in the array.

---

## Problem 28 - llama-3.3-70b-versatile - Iteration 33
# STEP 1: PROBLEM
In a small library, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The librarian wants to create a program to manage the books using pointers and pointer arithmetic. The program should be able to store information about each book, display the details of a specific book, and allow the librarian to navigate through the collection.

The program's functionality should include:
1. Storing information about each book in memory using pointers.
2. Displaying the details of a specific book.
3. Allowing the librarian to navigate through the collection.

Here is a simple example of expected input/output:
```
Enter the number of books: 3
Enter book 1 details:
Enter book ID: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
Enter book 2 details:
Enter book ID: 2
Enter book title: Book2
Enter book author: Author2
Enter book publication year: 2021
Enter book 3 details:
Enter book ID: 3
Enter book title: Book3
Enter book author: Author3
Enter book publication year: 2022

Menu:
1. Display book details
2. Navigate to next book
3. Navigate to previous book
4. EXIT

Choose an option: 1
Enter book ID: 2
Book ID: 2
Book title: Book2
Book author: Author2
Book publication year: 2021
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` to handle the menu and navigation.
- If a menu is implemented, it must include a specific menu option to EXIT the program by choosing option `4` or typing `EXIT`. 

Note: The program should handle invalid inputs and edge cases, such as navigating beyond the first or last book in the collection.

---

## Problem 29 - llama-3.3-70b-versatile - Iteration 34
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As the Computer Science professor, you have been tasked with designing a program to manage student records using pointers and pointer arithmetic.

Background:
The university wants to keep track of student information, including their names, student IDs, and GPA. The program should be able to store, display, and update student records.

Requirements:
1. The program should be able to store a maximum of 100 student records.
2. Each student record should contain the student's name, student ID, and GPA.
3. The program should be able to display all student records.
4. The program should be able to update a specific student record.
5. The program should be able to search for a student record by student ID.

Example of expected Input/Output:
```
Enter the number of student records: 2
Enter student name: John Doe
Enter student ID: 1234
Enter GPA: 3.5
Enter student name: Jane Doe
Enter student ID: 5678
Enter GPA: 3.8

Displaying all student records:
Name: John Doe, ID: 1234, GPA: 3.5
Name: Jane Doe, ID: 5678, GPA: 3.8

Update student record:
Enter student ID: 1234
Enter new GPA: 3.6

Displaying all student records:
Name: John Doe, ID: 1234, GPA: 3.6
Name: Jane Doe, ID: 5678, GPA: 3.8
```

### CONSTRAINTS
- Must use a `struct` to represent the student record.
- Logic for displaying the details of ONE specific student record must be in a function called `displayStudent`.
- The solution must be implemented with a single function besides `main()` to handle all menu options.
- The program must include a menu with the following options:
  1. Add student record
  2. Display all student records
  3. Update student record
  4. Search for student record by ID
  5. EXIT

Note: To EXIT the program, the user must select option 5.

---

## Problem 30 - llama-3.3-70b-versatile - Iteration 35
# STEP 1: PROBLEM
In the field of Computer Science, understanding pointers and pointer arithmetic is crucial for efficient memory management and data manipulation. Consider a simple library management system where books are stored on shelves. Each book has a unique identifier (ISBN), title, author, and publication year. The library wants to develop a program to manage its book collection.

The program should be able to store information about each book and perform basic operations such as adding a new book, displaying all books, and searching for a specific book by its ISBN. The program will use an array to store the books and pointers to navigate through the array.

### REQUIREMENTS
1. The program must allow users to add new books to the collection.
2. It must display all the books in the collection.
3. It must allow users to search for a specific book by its ISBN.
4. The program must handle cases where the collection is empty or the book is not found.

### EXAMPLE
Input:
- Add a book with ISBN "1234567890", title "Introduction to Programming", author "John Doe", and publication year "2020".
- Add another book with ISBN "9876543210", title "Data Structures", author "Jane Smith", and publication year "2019".
- Display all books.
- Search for a book with ISBN "1234567890".

Output:
- When displaying all books, the program should list each book's details (ISBN, title, author, publication year).
- When searching for a book with ISBN "1234567890", the program should display the book's details if found, or a message indicating that the book is not in the collection.

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented with a single array to store all books and pointers to navigate through this array.
- If a menu is implemented, it must include options to add a book, display all books, search for a book, and exit the program. The exit option must be clearly labeled as "5. Exit" or a similar clear instruction to exit the program. 

Example Menu:
1. Add a new book
2. Display all books
3. Search for a book by ISBN
4. Clear the collection
5. Exit

---

## Problem 31 - llama-3.3-70b-versatile - Iteration 36
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The library uses an array to store information about the books. You are tasked with designing a program that allows users to interact with this array of books using pointers and pointer arithmetic.

The program should have the following functionality:
1. Initialize an array of 10 books with default values.
2. Display a menu that allows users to:
   - Add a new book to the array
   - Display all books in the array
   - Search for a book by its title
   - Exit the program
3. When adding a new book, the program should prompt the user for the book's title, author, and publication year.
4. When displaying all books, the program should print the title, author, and publication year of each book.

### CONSTRAINTS
- Must use a 'struct' to represent a book, with members for title, author, publication year, and a unique identifier.
- The solution must be implemented with a single function besides main() to handle the menu options and book operations.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- To exit the program, the user must select menu option 4, labeled "EXIT".

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. EXIT

Select an option: 1
Enter book title: Introduction to CS
Enter book author: John Smith
Enter book publication year: 2020

Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. EXIT

Select an option: 2
Book 1:
Title: Introduction to CS
Author: John Smith
Publication Year: 2020

Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. EXIT

Select an option: 4
Exiting the program...
```

---

## Problem 32 - llama-3.3-70b-versatile - Iteration 37
# STEP 1: PROBLEM
You are the curator of a university's library system, and you want to create a simple program to manage the books in the library. The library has a collection of books, each with a unique title, author, and publication year. You need to create a program that can store and display information about these books.

The program should allow users to add new books to the collection, display all the books in the collection, and search for a specific book by its title. The program will use pointers and pointer arithmetic to manage the collection of books.

### REQUIREMENTS
1. The program should be able to store a maximum of 100 books in the collection.
2. The program should allow users to add new books to the collection.
3. The program should be able to display all the books in the collection.
4. The program should be able to search for a specific book by its title.
5. The program should display the details of the book(s) found during the search.

### EXAMPLE
Input:
```
Add a new book:
Title: "Introduction to Computer Science"
Author: "John Doe"
Year: 2020

Add another book:
Title: "Data Structures and Algorithms"
Author: "Jane Smith"
Year: 2019

Display all books:
1. "Introduction to Computer Science" by John Doe (2020)
2. "Data Structures and Algorithms" by Jane Smith (2019)

Search for a book:
Title: "Introduction to Computer Science"
1. "Introduction to Computer Science" by John Doe (2020)
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The logic for searching for a specific book must be in a function called `searchBook`.
- The program must use pointers and pointer arithmetic to manage the collection of books.
- A menu must be implemented to allow users to interact with the program. The menu options are:
  1. Add a new book
  2. Display all books
  3. Search for a book
  4. EXIT (to exit the program)
- The program must use a single array to store all the books, and the array must be dynamically allocated using pointers. 

Note that the program should handle cases where the user tries to add more than 100 books, and it should also handle cases where the user searches for a book that does not exist in the collection.

---

## Problem 33 - llama-3.3-70b-versatile - Iteration 38
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, and you want to manage the details of the department's faculty members using a C program. Each faculty member has a unique ID, name, and age. You want to store the details of all faculty members in an array and perform various operations on the array.

Background: 
The department currently has a limited number of faculty members, and you expect the number to grow in the future. You want a program that can efficiently store and manage the details of all faculty members.

Requirements:
1. The program must store the details of all faculty members in an array of structures, where each structure represents a faculty member.
2. The program must have a menu-driven interface with the following options:
   - Add a new faculty member
   - Display the details of all faculty members
   - Display the details of a specific faculty member by ID
   - Update the details of a specific faculty member by ID
   - Exit the program
3. The program must use pointer arithmetic to access and modify the details of faculty members in the array.

Example of expected Input/Output:
```
Menu:
1. Add a new faculty member
2. Display all faculty members
3. Display a specific faculty member
4. Update a faculty member
5. Exit

Enter your choice: 1
Enter faculty member ID: 1
Enter faculty member name: John Doe
Enter faculty member age: 30

Menu:
1. Add a new faculty member
2. Display all faculty members
3. Display a specific faculty member
4. Update a faculty member
5. Exit

Enter your choice: 2
Faculty Member ID: 1, Name: John Doe, Age: 30

Menu:
1. Add a new faculty member
2. Display all faculty members
3. Display a specific faculty member
4. Update a faculty member
5. Exit

Enter your choice: 5
Exiting the program...
```

### CONSTRAINTS
- Must use a 'struct' to represent a faculty member.
- The logic for displaying the details of ONE specific faculty member must be in a function called 'displayFacultyMember'.
- The solution must be implemented with a single function besides 'main()' to handle the menu-driven interface, and this function should be called 'handleMenu'.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5 in this case.
- The program must use pointer arithmetic to access and modify the details of faculty members in the array.

---

## Problem 34 - llama-3.3-70b-versatile - Iteration 39
# STEP 1: PROBLEM
In a university setting, students often need to manage their grades for various courses. As a Computer Science professor, you want to create a program that allows students to store and manipulate their grades using pointers and pointer arithmetic. The program should be able to store student information, including their name, student ID, and grades for multiple courses.

The program should have the following functionality:
1. Store student information, including name, student ID, and grades for up to 5 courses.
2. Display all student information.
3. Calculate the average grade for a specific student.
4. Sort students by their average grade in ascending order.

### CONSTRAINTS
* The solution must be implemented using a `struct` to represent the student data entity.
* Logic for displaying the details of all students must be in a function called `displayStudents`.
* Logic for calculating the average grade of a student must be in a function called `calculateAverageGrade`.
* The program must have a menu-driven interface with the following options:
	1. Add a new student
	2. Display all students
	3. Calculate average grade for a specific student
	4. Sort students by average grade
	5. EXIT the program

### EXAMPLE INPUT/OUTPUT
Example input:
```
Enter student name: John Doe
Enter student ID: 12345
Enter grades for 5 courses (space-separated): 90 80 70 85 95
```
Example output:
```
Student Name: John Doe
Student ID: 12345
Grades: 90 80 70 85 95
Average Grade: 84.0
```
Note: The program should be able to handle multiple students and display their information accordingly.

To exit the program, the user should select option 5 (EXIT) from the menu.

---

## Problem 35 - llama-3.3-70b-versatile - Iteration 40
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a Computer Science professor, you want to design a program that utilizes pointers and pointer arithmetic to manage student data. The program should be able to store student details, display specific student information, and navigate through the records using pointer arithmetic.

The program's primary data entity is a student, which has the following attributes:
- Student ID (integer)
- Name (character array of maximum length 50)
- Grade (float)

### REQUIREMENTS
1. The program must store a maximum of 10 student records in an array of structs.
2. The program must have a function to input student details and store them in the array.
3. The program must have a function to display all student records.
4. The program must have a function to display the details of a specific student given their student ID.
5. The program must use pointer arithmetic to navigate through the array of student records.

### EXAMPLE INPUT/OUTPUT
Input:
```
Enter the number of students (max 10): 2
Enter student ID: 1
Enter student name: John Doe
Enter student grade: 85.5
Enter student ID: 2
Enter student name: Jane Doe
Enter student grade: 90.0
```
Output:
```
Student Records:
ID: 1, Name: John Doe, Grade: 85.5
ID: 2, Name: Jane Doe, Grade: 90.0
```
Display specific student (ID: 1):
```
Student ID: 1, Name: John Doe, Grade: 85.5
```

### CONSTRAINTS
- Must use a `struct` to represent the student data entity.
- Logic for displaying the details of ONE specific entity must be in a function called `displayStudent`.
- The solution must be implemented with a single function besides `main()` to handle all the input and output operations, including menu display and navigation.
- The program must include a menu with the following options:
  1. Input student records
  2. Display all student records
  3. Display a specific student record
  4. EXIT the program

Note: The program must exit when the user selects the EXIT option (option 4).

---

## Problem 36 - llama-3.3-70b-versatile - Iteration 41
# STEP 1: PROBLEM
You are a curator at a local museum, and you have been tasked with creating a program to manage the museum's collection of artifacts. The museum has a vast collection of items, each with its own unique identifier, name, and description. As the curator, you want to be able to store, retrieve, and display information about these artifacts efficiently.

The program should be able to store the artifacts in a dynamically allocated array, where each artifact is represented by a struct. The program should also be able to perform pointer arithmetic operations to navigate through the array and access the artifacts.

Here are the requirements for the program's functionality:
1. The program should prompt the user to enter the number of artifacts they want to store.
2. The program should dynamically allocate an array of structs to store the artifacts.
3. The program should prompt the user to enter the details of each artifact (id, name, and description).
4. The program should store the artifacts in the dynamically allocated array.
5. The program should provide a menu-driven interface to display the details of all artifacts, display the details of a specific artifact, and exit the program.

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the artifact, with members for id, name, and description.
- The logic for displaying the details of all artifacts must be in a function called 'displayAllArtifacts'.
- The logic for displaying the details of a specific artifact must be in a function called 'displayArtifact'.
- The program must use pointer arithmetic to navigate through the array of artifacts.
- The program must include a menu option to EXIT the program, which should be option 4.

### EXAMPLE INPUT/OUTPUT
```
Enter the number of artifacts: 2
Enter id of artifact 1: 1
Enter name of artifact 1: Artifact 1
Enter description of artifact 1: This is artifact 1
Enter id of artifact 2: 2
Enter name of artifact 2: Artifact 2
Enter description of artifact 2: This is artifact 2

Menu:
1. Display all artifacts
2. Display a specific artifact
3. Add a new artifact
4. EXIT

Enter your choice: 1
Artifact 1:
Id: 1
Name: Artifact 1
Description: This is artifact 1
Artifact 2:
Id: 2
Name: Artifact 2
Description: This is artifact 2
```

---

## Problem 37 - llama-3.3-70b-versatile - Iteration 42
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their student ID, name, and GPA. You want to create a program that can efficiently store and manage this data using pointers and pointer arithmetic.

Background:
The university has a large number of students, and the system needs to be able to handle this data efficiently. You have decided to use an array of structures to store the student information, where each structure represents a single student.

Requirements:
1. The program should be able to store information about a maximum of 100 students.
2. The program should have a menu-driven interface that allows the user to:
   - Add a new student to the database
   - Display the details of all students in the database
   - Display the details of a specific student by their student ID
   - Update the GPA of a specific student
3. The program should use pointers and pointer arithmetic to manage the student data.

Example Input/Output:
If the user chooses to add a new student, the program should prompt them to enter the student's ID, name, and GPA. For example:
```
Enter student ID: 1234
Enter student name: John Doe
Enter student GPA: 3.5
```
If the user chooses to display the details of all students, the program should output something like:
```
Student ID: 1234, Name: John Doe, GPA: 3.5
Student ID: 5678, Name: Jane Smith, GPA: 3.8
```
If the user chooses to display the details of a specific student, the program should output something like:
```
Student ID: 1234, Name: John Doe, GPA: 3.5
```
### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the student data.
- The logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The program must use a single array to store all student data, and pointers and pointer arithmetic to manage this data.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.
- The menu options should be as follows:
  1. Add a new student to the database
  2. Display the details of all students in the database
  3. Display the details of a specific student by their student ID
  4. Update the GPA of a specific student
  5. EXIT the program

---

## Problem 38 - llama-3.3-70b-versatile - Iteration 43
# STEP 1: PROBLEM
In a simple library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. To efficiently manage the collection, the library uses a computer program to keep track of the books. The program utilizes pointers and pointer arithmetic to navigate through the collection of books.

The program should allow users to add books to the collection, display the details of all books, and search for a specific book by its identifier. The collection of books is represented as an array of structures, where each structure contains information about a book.

### REQUIREMENTS
1. The program should store the collection of books in an array of structures, where each structure represents a book with its identifier, title, author, and publication year.
2. The program should have a function to add a new book to the collection.
3. The program should have a function to display the details of all books in the collection.
4. The program should have a function to search for a specific book by its identifier and display its details.

### EXAMPLE
Input:
```
Add a book with id: 1, title: "Book1", author: "Author1", year: 2020
Add a book with id: 2, title: "Book2", author: "Author2", year: 2021
Display all books
Search for book with id: 1
```
Output:
```
Book 1: 
  Id: 1
  Title: Book1
  Author: Author1
  Year: 2020
Book 2: 
  Id: 2
  Title: Book2
  Author: Author2
  Year: 2021
Book with id 1:
  Id: 1
  Title: Book1
  Author: Author1
  Year: 2020
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for searching for a specific book by its identifier and displaying its details must be in a function called `searchBook`.
- The program must use a menu to allow users to interact with the system. The menu options are:
  1. Add a book
  2. Display all books
  3. Search for a book
  4. EXIT
- The program must use pointer arithmetic to navigate through the array of books.

Note: The program should handle invalid inputs and errors, such as attempting to add a book with an existing identifier or searching for a non-existent book.

---

## Problem 39 - llama-3.3-70b-versatile - Iteration 44
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their student ID, name, and GPA. You want to create a program that can efficiently store and manage this data using pointers and pointer arithmetic.

The program should be able to perform the following operations:
1. Add a new student to the database
2. Display the details of all students in the database
3. Display the details of a specific student by their student ID
4. Update the GPA of a specific student
5. Remove a student from the database

The program should use a struct to represent a student, with the following fields: student ID (integer), name (character array), and GPA (float).

### EXAMPLE
Input:
```
Add student with ID 1, name "John Doe", and GPA 3.5
Add student with ID 2, name "Jane Doe", and GPA 3.8
Display all students
Display student with ID 1
Update GPA of student with ID 1 to 3.6
Remove student with ID 2
Display all students
```
Output:
```
Student 1: John Doe, GPA 3.5
Student 2: Jane Doe, GPA 3.8
Student 1: John Doe, GPA 3.6
No student with ID 2 found
Student 1: John Doe, GPA 3.6
```
### CONSTRAINTS
- The solution must be implemented using pointers and pointer arithmetic.
- The program must use a struct to represent a student.
- Logic for displaying the details of all students must be in a function called `displayAllStudents`.
- Logic for displaying the details of a specific student must be in a function called `displayStudent`.
- The program must include a menu with the following options:
  1. Add student
  2. Display all students
  3. Display student by ID
  4. Update GPA
  5. Remove student
  6. EXIT
- The program must exit when the user selects the EXIT option (option 6).

---

## Problem 40 - llama-3.3-70b-versatile - Iteration 45
# STEP 1: PROBLEM
You are the curator of a museum with a vast collection of artifacts from different historical periods. Each artifact has a unique identifier, name, description, and acquisition date. To efficiently manage the collection, you want to create a program that stores the artifacts' information and allows you to navigate through the collection using pointers and pointer arithmetic.

The program should store the artifact information in an array of structures, where each structure represents an artifact. The program should have the following functionality:
1. Initialize an array of artifact structures with a specified number of elements.
2. Populate the array with artifact information.
3. Display the details of all artifacts in the collection.
4. Display the details of a specific artifact based on its index in the array.
5. Calculate and display the average number of characters in the names of all artifacts.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to perform the calculations and display the results, named `processArtifacts`.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Number of artifacts: 3
Artifact 1:
  ID: 1
  Name: Ancient Vase
  Description: A vase from ancient Greece
  Acquisition Date: 2020-01-01
Artifact 2:
  ID: 2
  Name: Medieval Sword
  Description: A sword from medieval Europe
  Acquisition Date: 2020-02-01
Artifact 3:
  ID: 3
  Name: Modern Painting
  Description: A painting from modern times
  Acquisition Date: 2020-03-01
```
Example Output:
```
All Artifacts:
  ID: 1, Name: Ancient Vase, Description: A vase from ancient Greece, Acquisition Date: 2020-01-01
  ID: 2, Name: Medieval Sword, Description: A sword from medieval Europe, Acquisition Date: 2020-02-01
  ID: 3, Name: Modern Painting, Description: A painting from modern times, Acquisition Date: 2020-03-01
Average name length: 15.33
Display specific artifact (enter index, -1 to return): 1
  ID: 1, Name: Ancient Vase, Description: A vase from ancient Greece, Acquisition Date: 2020-01-01
```
### MENU CONSTRAINTS
If a menu is implemented, it must include the following options:
1. Display all artifacts
2. Display a specific artifact
3. Calculate and display the average name length
4. EXIT the program (option 4 or keyword 'exit')

Note: The program should handle invalid inputs and edge cases, such as an empty array or an out-of-range index.

---

## Problem 41 - llama-3.3-70b-versatile - Iteration 16
# STEP 1: PROBLEM
In a small library, the librarian wants to manage a collection of books using a simple computer program. The program should store information about each book, including its title, author, and publication year. The librarian wants to be able to add new books, display the details of all books, and display the details of a specific book.

The program will use an array to store the book information, and the librarian wants to use pointers and pointer arithmetic to manage the array.

The requirements for the program are as follows:
1. The program must store the book information in an array of structs, where each struct represents a book with title, author, and publication year.
2. The program must have a function to add a new book to the array.
3. The program must have a function to display the details of all books in the array.
4. The program must have a function to display the details of a specific book, given its index in the array.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to add a new book to the array.
- The program must include a menu with the following options:
  - Option 1: Add a new book
  - Option 2: Display all books
  - Option 3: Display a specific book
  - Option 4: EXIT the program

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book
2. Display all books
3. Display a specific book
4. EXIT

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Choose an option: 2
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Choose an option: 3
Enter book index: 1
Book:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Choose an option: 4
Exiting program...
```

---

## Problem 42 - llama-3.3-70b-versatile - Iteration 17
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a system to keep track of the books in the library. Each book has a title, author, publication year, and a unique identifier. You want to store the information of all the books in an array and perform certain operations on it.

Background:
The library currently has a collection of books, and you want to create a program that can store the information of these books, display the details of a specific book, and update the publication year of a book.

Requirements:
1. The program should store the information of all the books in an array.
2. The program should have a function to display the details of a specific book.
3. The program should have a function to update the publication year of a book.
4. The program should have a menu-driven interface to perform these operations.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with two functions besides main(): 'displayBook' and 'updatePublicationYear'.
- The program must include a menu with the following options:
  1. Display all books
  2. Display a specific book
  3. Update the publication year of a book
  4. EXIT (to exit the program)

Example of expected Input/Output:
If the library has the following books:
| Title | Author | Publication Year | Unique Identifier |
| --- | --- | --- | --- |
| Book1 | Author1 | 2010 | 1 |
| Book2 | Author2 | 2015 | 2 |
| Book3 | Author3 | 2020 | 3 |

When the user selects option 2 to display a specific book and enters the unique identifier of Book2, the program should display:
"Title: Book2, Author: Author2, Publication Year: 2015"

When the user selects option 3 to update the publication year of a book and enters the unique identifier of Book2 and the new publication year 2022, the program should update the publication year of Book2 to 2022.

---

## Problem 43 - llama-3.3-70b-versatile - Iteration 18
# STEP 1: PROBLEM
In a university setting, student records are crucial for tracking academic progress. To manage these records efficiently, you have been tasked with designing a simple console-based application. The application should utilize pointers and pointer arithmetic to store and manipulate student information.

Background: 
The university wants to maintain a list of students with their IDs, names, and GPAs. The list should be dynamically allocated, and the application should allow users to add, remove, and display student records.

Requirements:
1. The program should start by allocating space for a specified number of students.
2. The user should be able to add a new student record, which includes the student's ID, name, and GPA.
3. The user should be able to remove a student record by ID.
4. The user should be able to display all student records.
5. The user should be able to display the details of a specific student by ID.

Example of expected Input/Output:
- When the user chooses to add a student, the program should prompt for the ID, name, and GPA, then store this information.
- When the user chooses to display all students, the program should show the ID, name, and GPA of each student.

### CONSTRAINTS
- Must use a `struct` to represent the student data entity.
- Logic for displaying the details of ONE specific student must be in a function called `displayStudent`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input.
- If a menu is implemented, it must include the following options:
  1. Add a new student
  2. Remove a student by ID
  3. Display all students
  4. Display a specific student by ID
  5. EXIT the program
- The program should validate user input to prevent crashes or unexpected behavior.

Example Menu:
```
1. Add a new student
2. Remove a student by ID
3. Display all students
4. Display a specific student by ID
5. EXIT
Choose an option:
```

---

## Problem 44 - llama-3.3-70b-versatile - Iteration 19
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. To efficiently manage the books, the library uses a pointer-based system to keep track of the books on each shelf. Your task is to design a program that can store and display the details of the books on a shelf using pointers and pointer arithmetic.

The program should allow users to add books to the shelf, display the details of all books on the shelf, and display the details of a specific book. 

### REQUIREMENTS
1. The program must store the details of each book in a struct, which includes the book's identifier, title, author, and publication year.
2. The program must use dynamic memory allocation to store the books on the shelf.
3. The program must provide the following functionalities:
   - Add a book to the shelf.
   - Display the details of all books on the shelf.
   - Display the details of a specific book.
4. The program must handle invalid inputs and exceptions.

### EXAMPLE
If the user adds two books with the following details:
- Book 1: Identifier = 1, Title = "Book1", Author = "Author1", Publication Year = 2020
- Book 2: Identifier = 2, Title = "Book2", Author = "Author2", Publication Year = 2021

The program should display the following output when the user chooses to display all books:
```
Book 1:
Identifier: 1
Title: Book1
Author: Author1
Publication Year: 2020

Book 2:
Identifier: 2
Title: Book2
Author: Author2
Publication Year: 2021
```

### CONSTRAINTS
- The solution must be implemented using a single function besides main(), called `manageLibrary()`.
- The program must use a struct to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayBook()`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4.

### MENU CONSTRAINTS
If a menu is implemented, it must have the following options:
1. Add a book to the shelf.
2. Display the details of all books on the shelf.
3. Display the details of a specific book.
4. EXIT the program.

---

## Problem 45 - llama-3.3-70b-versatile - Iteration 20
# STEP 1: PROBLEM
Topic: Pointers and Pointer Arithmetic

Background:
A university library wants to create a simple system to manage the books in its catalog. The library has a large collection of books, and the librarian needs a program that can efficiently store and retrieve information about each book.

Problem Statement:
Create a program that uses pointers and pointer arithmetic to manage a collection of books. Each book has a title, author, and publication year. The program should allow the user to add books to the catalog, display the details of all books, and display the details of a specific book.

Requirements:
1. The program should store the book information in an array of structures, where each structure represents a book.
2. The program should have a function to add a new book to the catalog.
3. The program should have a function to display the details of all books in the catalog.
4. The program should have a function to display the details of a specific book, given its index in the array.
5. The program should have a menu-driven interface to interact with the user.

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the Book entity.
- Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
- The program must have a single array to store all the books, and pointer arithmetic must be used to traverse and access the elements of this array.
- The menu options must include:
  1. Add a new book
  2. Display all books
  3. Display a specific book
  4. EXIT (to exit the program)

Example Input/Output:
```
Menu:
1. Add a new book
2. Display all books
3. Display a specific book
4. EXIT

Enter your choice: 1
Enter book title: Introduction to CS
Enter book author: John Smith
Enter book publication year: 2020

Menu:
1. Add a new book
2. Display all books
3. Display a specific book
4. EXIT

Enter your choice: 2
Book 1:
Title: Introduction to CS
Author: John Smith
Year: 2020

Menu:
1. Add a new book
2. Display all books
3. Display a specific book
4. EXIT

Enter your choice: 3
Enter book index: 1
Book:
Title: Introduction to CS
Author: John Smith
Year: 2020
```

---

## Problem 46 - llama-3.3-70b-versatile - Iteration 21
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. To manage the books efficiently, the library uses a pointer-based system to keep track of the books on each shelf. Your task is to design a program that simulates this system.

The program should allow users to add books to the system, display the details of all books, and search for a specific book by its identifier. The system should use pointer arithmetic to navigate through the array of books.

### REQUIREMENTS
1. The program should have a function to add a new book to the system.
2. The program should have a function to display the details of all books in the system.
3. The program should have a function to search for a specific book by its identifier and display its details.
4. The program should use pointer arithmetic to navigate through the array of books.

### EXAMPLE
Input:
```
Add book with id: 1, title: "Book1", author: "Author1", year: 2020
Add book with id: 2, title: "Book2", author: "Author2", year: 2021
Display all books
Search for book with id: 1
```
Output:
```
Book 1: Title - Book1, Author - Author1, Year - 2020
Book 2: Title - Book2, Author - Author2, Year - 2021
Book with id 1: Title - Book1, Author - Author1, Year - 2020
```

### CONSTRAINTS
- Must use a `struct` to represent a book with fields for id, title, author, and year.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for searching for a specific book must be in a function called `searchBook`.
- The solution must be implemented with a single array to store all books.
- The program must have a menu-driven interface with the following options:
  1. Add a new book
  2. Display all books
  3. Search for a book
  4. EXIT
- The program must exit when the user chooses the EXIT option (option 4).

---

## Problem 47 - llama-3.3-70b-versatile - Iteration 22
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, and you need to manage the records of students enrolled in various courses. Each student has a unique ID, name, and grade point average (GPA). You want to create a program to store and display the information of these students.

The program should store the information of 10 students. The program must allow the user to input the details of the students, display the details of all students, and display the details of a specific student.

### REQUIREMENTS
1. The program must store the information of 10 students.
2. The program must allow the user to input the details of the students.
3. The program must display the details of all students.
4. The program must display the details of a specific student.
5. The program must have a menu-driven interface.

### EXAMPLE
If the user inputs the following details:
- Student 1: ID = 1, Name = John, GPA = 3.5
- Student 2: ID = 2, Name = Alice, GPA = 3.8
- Student 3: ID = 3, Name = Bob, GPA = 3.2

The program should display the details of all students as follows:
- Student 1: ID = 1, Name = John, GPA = 3.5
- Student 2: ID = 2, Name = Alice, GPA = 3.8
- Student 3: ID = 3, Name = Bob, GPA = 3.2

If the user wants to display the details of a specific student with ID = 2, the program should display:
- Student 2: ID = 2, Name = Alice, GPA = 3.8

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu and user input.
- The menu must have the following options:
  1. Input student details
  2. Display all students
  3. Display specific student
  4. EXIT

Note: The program will exit when the user chooses the 'EXIT' option (option 4).

---

## Problem 48 - llama-3.3-70b-versatile - Iteration 23
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining accurate information about each student's performance and personal details. As a Computer Science professor, you want to design a program that utilizes pointers and pointer arithmetic to manage student records efficiently.

Background:
The program aims to store student information, including their ID, name, and grade point average (GPA). The records will be stored in a dynamically allocated array, and the program will provide options to add, display, and update student records.

Requirements:
1. The program must dynamically allocate memory for an array of student records.
2. The program must provide a menu with the following options:
   - Add a new student record
   - Display all student records
   - Update a student record by ID
   - Display a specific student record by ID
3. The program must handle invalid inputs and provide error messages accordingly.

Example Input/Output:
If the user chooses to add a new student record, the program will prompt for the student's ID, name, and GPA. For example:
```
Enter student ID: 12345
Enter student name: John Doe
Enter student GPA: 3.5
```
If the user chooses to display all student records, the program will display the ID, name, and GPA of each student.

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student record.
- The logic for displaying the details of ONE specific student record must be in a function called `displayStudent`.
- The program must include a menu option to EXIT the program. The EXIT option must be numbered as 5.
- If a menu is implemented, it must include the following options:
  1. Add a new student record
  2. Display all student records
  3. Update a student record by ID
  4. Display a specific student record by ID
  5. EXIT the program

Example Menu:
```
Student Record Management System
-------------------------------
1. Add a new student record
2. Display all student records
3. Update a student record by ID
4. Display a specific student record by ID
5. EXIT
```
Note: The program should handle memory deallocation to prevent memory leaks.

---

## Problem 49 - llama-3.3-70b-versatile - Iteration 24
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, tasked with managing student records. Each student has a unique ID, name, and GPA. You want to create a program that stores student information in an array and allows users to navigate through the records using pointers and pointer arithmetic.

The program should have the following functionality:
1. Initialize an array of student records with a fixed size (e.g., 10).
2. Populate the array with sample student data.
3. Provide a menu for users to navigate through the records:
   - Option 1: Display the current student record.
   - Option 2: Move to the next student record.
   - Option 3: Move to the previous student record.
   - Option 4: Display all student records.
   - Option 5: EXIT the program.

### CONSTRAINTS
- Must use a `struct` to represent the student data entity.
- Logic for displaying the details of ONE specific student record must be in a function called `displayStudent`.
- The solution must be implemented with a single function besides `main()`, which will handle the menu and user input.

### EXAMPLE INPUT/OUTPUT
If the array has the following student records:
```
Student 1: ID = 1, Name = John, GPA = 3.5
Student 2: ID = 2, Name = Alice, GPA = 3.8
Student 3: ID = 3, Name = Bob, GPA = 3.2
```
The program should display the current student record when the user selects Option 1. For example:
```
Current Student:
ID: 1
Name: John
GPA: 3.5
```
When the user selects Option 2, the program should move to the next student record and display its details:
```
Current Student:
ID: 2
Name: Alice
GPA: 3.8
```
To exit the program, the user should select Option 5.

---

## Problem 50 - llama-3.3-70b-versatile - Iteration 25
# STEP 1: PROBLEM
In a university setting, student records are crucial for administrative purposes. As a Computer Science professor, you want to create a simple program to manage student information using pointers and pointer arithmetic. The program should store student details such as student ID, name, and grade point average (GPA). 

The program should allow users to add new student records, display all student records, and search for a specific student by ID. The program will store student records in a dynamically allocated array.

Here is a precise list of requirements for the program's functionality:
1. The program should start by asking the user for the initial number of student records they want to store.
2. The program should then dynamically allocate memory for the specified number of student records.
3. The program should have a menu with the following options:
   - Add a new student record
   - Display all student records
   - Search for a student by ID
   - Exit the program
4. When adding a new student record, the program should ask for the student's ID, name, and GPA, and then store this information in the next available slot in the array.
5. If the array is full, the program should dynamically reallocate memory to double the size of the array before adding the new student record.
6. When displaying all student records, the program should print out the ID, name, and GPA of each student.
7. When searching for a student by ID, the program should print out the details of the student with the matching ID, or a message indicating that no student with that ID was found.

### CONSTRAINTS
- The solution must be implemented using a single function besides main(), called `manageStudentRecords`.
- The program must use a `struct` to represent the student data entity.
- The program must include a specific menu option to EXIT the program, which is option 4.

### EXAMPLE
Example Input/Output:
```
Enter the initial number of student records: 2
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Exit the program
Choose an option: 1
Enter student ID: 123
Enter student name: John Doe
Enter student GPA: 3.5
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Exit the program
Choose an option: 1
Enter student ID: 456
Enter student name: Jane Doe
Enter student GPA: 3.8
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Exit the program
Choose an option: 2
Student ID: 123, Name: John Doe, GPA: 3.5
Student ID: 456, Name: Jane Doe, GPA: 3.8
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Exit the program
Choose an option: 4
```
Note: The program should continue to run and prompt the user for input until the user chooses to exit.

---

## Problem 51 - llama-3.3-70b-versatile - Iteration 26
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The library wants to create a program to manage the books on the shelves. The program should be able to store book information, display the details of a specific book, and calculate the total number of books on the shelves.

Background:
The library has multiple shelves, and each shelf can hold a maximum of 100 books. The librarian wants to create a program to manage the books on the shelves efficiently.

Requirements:
1. The program should store book information (identifier, title, author, and publication year) in an array of structs.
2. The program should have a function to display the details of a specific book.
3. The program should calculate the total number of books on the shelves.
4. The program should have a menu-driven interface to interact with the user.

Example Input/Output:
If the user adds three books with identifiers 1, 2, and 3, and then displays the details of book 2, the output should be:
```
Book ID: 2
Title: Book Title 2
Author: Author 2
Publication Year: 2020
```

### CONSTRAINTS
1. The program must use a `struct` to represent the book entity.
2. The logic for displaying the details of one specific book must be in a function called `displayBook`.
3. The solution must be implemented with a single function besides `main()` to handle user input and interactions.
4. If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5, labeled as "EXIT".

Menu Options:
1. Add a book
2. Display book details
3. Calculate total number of books
4. Display all books
5. EXIT

Note: The program should handle invalid user input and provide clear error messages. The program should also handle the case where the user tries to display a book that does not exist.

---

## Problem 52 - llama-3.3-70b-versatile - Iteration 27
# STEP 1: PROBLEM
In a small bookstore, the owner wants to keep track of the books in stock using a simple computer program. The program should store information about each book, including its title, author, publication year, and price. The bookstore owner wants to be able to add new books, display all books, and find a specific book by its title.

The program should use pointers and pointer arithmetic to manage the memory for the book structures.

### REQUIREMENTS
1. The program should allow the user to add a new book with its title, author, publication year, and price.
2. The program should display all the books in stock, showing their title, author, publication year, and price.
3. The program should allow the user to find a specific book by its title and display its details if found.
4. The program should handle memory allocation and deallocation for the book structures.

### EXAMPLE
If the user adds the following books:
- Title: "Book1", Author: "Author1", Year: 2020, Price: 10.99
- Title: "Book2", Author: "Author2", Year: 2021, Price: 12.99
- Title: "Book3", Author: "Author3", Year: 2022, Price: 14.99

And then searches for "Book2", the program should display:
Title: Book2, Author: Author2, Year: 2021, Price: 12.99

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for finding a specific book by its title must be in a function called `findBook`.
- The program must include a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Find a book by title
  4. EXIT the program
- The program must use pointers and pointer arithmetic to manage memory for the book structures.
- The `EXIT` option should be selected by entering the number 4.

---

## Problem 53 - llama-3.3-70b-versatile - Iteration 28
# STEP 1: PROBLEM
You are the curator of a museum with a vast collection of artifacts. To manage the collection, you want to create a simple program that stores information about each artifact, including its name, year of origin, and type (e.g., painting, sculpture, relic). Since the collection is large and you need to efficiently manage the data, you decide to use pointers and pointer arithmetic to store and manipulate the information.

The program should allow users to add new artifacts, display all artifacts, and search for a specific artifact by name. The program should also have a menu-driven interface to make it easy for users to interact with the collection.

### REQUIREMENTS
1. The program should store information about each artifact in a struct that includes the name, year of origin, and type of the artifact.
2. The program should have a menu-driven interface with the following options:
   - Add a new artifact
   - Display all artifacts
   - Search for an artifact by name
   - Exit the program
3. When adding a new artifact, the program should prompt the user to enter the name, year of origin, and type of the artifact.
4. When displaying all artifacts, the program should print the name, year of origin, and type of each artifact.
5. When searching for an artifact by name, the program should print the name, year of origin, and type of the artifact if it is found.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new artifact
2. Display all artifacts
3. Search for an artifact by name
4. Exit the program
Choose an option: 1
Enter name: Mona Lisa
Enter year of origin: 1503
Enter type: Painting
Menu:
1. Add a new artifact
2. Display all artifacts
3. Search for an artifact by name
4. Exit the program
Choose an option: 2
Mona Lisa, 1503, Painting
Menu:
1. Add a new artifact
2. Display all artifacts
3. Search for an artifact by name
4. Exit the program
Choose an option: 3
Enter name: Mona Lisa
Mona Lisa, 1503, Painting
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (i.e., an artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle all menu options.
- To exit the program, the user must choose option 4 from the menu.
- The program must dynamically allocate memory for each new artifact using pointers.
- The program must use pointer arithmetic to access and manipulate the artifact data.

---

## Problem 54 - llama-3.3-70b-versatile - Iteration 29
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The library wants to implement a simple system to manage their book collection using pointers and pointer arithmetic.

Background:
The library has a collection of books, and each book is represented by a struct containing the book's identifier, title, author, and publication year. The library wants to create a program that allows them to add books, display book details, and navigate through the collection using pointer arithmetic.

Requirements:
1. The program must allow users to add books to the collection.
2. The program must display the details of all books in the collection.
3. The program must allow users to navigate through the collection using pointer arithmetic (i.e., move to the next book, previous book, or a specific book).
4. The program must display the details of a specific book.

Example Input/Output:
```
Add a book:
Enter book ID: 1
Enter book title: Book Title 1
Enter book author: Author 1
Enter publication year: 2020

Add a book:
Enter book ID: 2
Enter book title: Book Title 2
Enter book author: Author 2
Enter publication year: 2021

Display all books:
Book ID: 1, Title: Book Title 1, Author: Author 1, Year: 2020
Book ID: 2, Title: Book Title 2, Author: Author 2, Year: 2021

Navigate to next book:
Book ID: 2, Title: Book Title 2, Author: Author 2, Year: 2021

Navigate to previous book:
Book ID: 1, Title: Book Title 1, Author: Author 1, Year: 2020
```

### CONSTRAINTS
1. The solution must be implemented using a `struct` to represent the book entity.
2. The logic for displaying the details of a specific book must be in a function called `displayBook`.
3. The program must use a single array to store all books, and pointer arithmetic to navigate through the collection.
4. The program must have a menu with the following options:
   - Add a book (option 1)
   - Display all books (option 2)
   - Navigate to next book (option 3)
   - Navigate to previous book (option 4)
   - Display a specific book (option 5)
   - EXIT the program (option 6)

Note: The program should handle invalid inputs and edge cases, such as navigating to a non-existent book or displaying a book that is not in the collection.

---

## Problem 55 - llama-3.3-70b-versatile - Iteration 30
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their ID, name, and GPA. You want to create a program that can efficiently store and manage this data using pointers and pointer arithmetic.

The program should allow users to add new students, display all students, and search for a specific student by ID. The program should also calculate and display the average GPA of all students.

### REQUIREMENTS
1. The program should store student data in a dynamically allocated array of structures, where each structure represents a student.
2. The program should have a function to add a new student to the database.
3. The program should have a function to display all students in the database.
4. The program should have a function to search for a specific student by ID and display their details.
5. The program should calculate and display the average GPA of all students.

### EXAMPLE INPUT/OUTPUT
Example input:
```
Add student with ID 1, name John, GPA 3.5
Add student with ID 2, name Alice, GPA 3.8
Display all students
Search for student with ID 1
Calculate average GPA
```
Example output:
```
Student 1: ID 1, Name John, GPA 3.5
Student 2: ID 2, Name Alice, GPA 3.8
Student found: ID 1, Name John, GPA 3.5
Average GPA: 3.65
```

### CONSTRAINTS
1. Must use a `struct` to represent the student data entity.
2. Logic for displaying the details of ONE specific entity must be in a function called `displayStudent`.
3. The solution must be implemented with a single function besides `main()` to handle all menu options.
4. The program must include a menu with the following options:
   - Option 1: Add new student
   - Option 2: Display all students
   - Option 3: Search for student by ID
   - Option 4: Calculate average GPA
   - Option 5: EXIT the program
   The program should continue to run and prompt the user for input until the user chooses to EXIT (Option 5).

---

## Problem 56 - openai/gpt-oss-120b - Iteration 1
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and tracks how many copies are currently on the shelf. The library wants a small console program that lets a librarian **add** new books, **update** the number of copies for an existing book, **display** the details of a specific book, and **list** all books. Because the librarians are learning C, the instructor wants them to practice **pointers**, **pointer arithmetic**, and the use of a **struct** to store each book’s data.

## Requirements  

1. Define a `struct Book` that contains:  
   - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
   - `char title[101];` // up to 100 characters plus null  
   - `int copies;`  

2. The program must maintain the collection in a **dynamically allocated array** of `struct Book`.  
   - The array should start with capacity for 5 books and grow (using `realloc`) when more space is needed.  

3. Implement a **menu‑driven** interface that repeatedly prompts the user until they choose to exit. The menu must contain the following options (exact wording is not required, but the numbers must match):  

   1. **Add a new book** – read ISBN, title, and initial copy count, then store it at the end of the array.  
   2. **Update copies** – ask for an ISBN, locate the matching book using pointer arithmetic, and change its `copies` field.  
   3. **Display a book** – ask for an ISBN and print the book’s details. The logic for displaying a single book **must be placed in a function called `displayBook`** that receives a pointer to a `struct Book`.  
   4. **List all books** – iterate through the array (using pointer arithmetic) and print every book’s information.  
   5. **Exit** – terminate the program.  

4. Input validation:  
   - If the user tries to update or display a book that does not exist, print an appropriate message.  
   - The number of copies must never be negative; reject such input with a warning and re‑prompt.  

5. Memory management:  
   - Free any allocated memory before the program terminates.  

## Example Interaction  

```
=== Library Inventory Menu ===
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. Exit
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added.

=== Library Inventory Menu ===
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. Exit
Enter choice: 1
Enter ISBN: 9780262033848
Enter title: Introduction to Algorithms
Enter number of copies: 2
Book added.

=== Library Inventory Menu ===
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. Exit
Enter choice: 3
Enter ISBN to display: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

=== Library Inventory Menu ===
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. Exit
Enter choice: 4
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4
ISBN: 9780262033848 | Title: Introduction to Algorithms | Copies: 2

=== Library Inventory Menu ===
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Usage:** The primary data entity must be represented by a `struct Book`.  
- **Function Requirement:** The logic for displaying the details of **ONE specific book** must be implemented in a function named `displayBook` that takes a pointer to a `struct Book` as its sole argument.  
- **Pointer Arithmetic:** Traversal of the dynamic array (for searching, updating, and listing) must be performed using pointer arithmetic; indexing (`array[i]`) is not allowed for those operations.  
- **Menu Exit Option:** The menu must include an explicit option (number **5**) to **EXIT** the program, and selecting it must cause the program to terminate gracefully.  
- **Single‑File Implementation:** All code must reside in a single `.c` source file; only the `displayBook` helper function may be added besides `main`.  

*Note: Students are free to create additional static helper functions if they wish, but the mandatory `displayBook` function is required.*

---

## Problem 57 - openai/gpt-oss-120b - Iteration 2
# STEP 1: PROBLEM  

## Background  
The kingdom of **Algoria** maintains a registry of its magical artifacts. Each artifact is stored in a **Chest** that contains:  

* an integer `id` (unique identifier)  
* a string `name` (max 30 characters)  
* a double `value` (the monetary worth in gold pieces)  

The royal archivist wants a small console program that lets a junior scribe add chests, view a specific chest, and compute the total value of all chests currently recorded. The archivist insists that the program use raw pointers and pointer arithmetic to navigate the array of chests, rather than higher‑level abstractions.

## Requirements  

1. **Data Structure**  
   * Define a `struct Chest` with the three fields described above.  

2. **Storage**  
   * Allocate a dynamic array capable of holding up to **100** chests using `new` (or `malloc` if you prefer C).  
   * Keep track of the current number of stored chests (`count`).  

3. **Menu** (the program must present a text menu and repeat until the user chooses to exit)  
   * `1` – **Add a Chest**  
        * Prompt for `id`, `name`, and `value`.  
        * Store the new chest at the first free position in the array using pointer arithmetic (`*(chests + count) = newChest`).  
        * Increment `count`.  
        * If the array is full, display an error message.  
   * `2` – **Display a Chest**  
        * Prompt for the `id` of the chest to view.  
        * Search the array (using pointer arithmetic) for a chest with that `id`.  
        * If found, call a function `displayChest` (see constraint) to print its details; otherwise, print “Chest not found.”  
   * `3` – **Total Value**  
        * Compute and display the sum of the `value` fields of all stored chests, again iterating with pointer arithmetic.  
   * `4` – **EXIT**  
        * Terminate the program gracefully, releasing any allocated memory.  

4. **Functions**  
   * Implement **exactly one** helper function besides `main` named `void displayChest(const Chest *c)`.  
        * It receives a pointer to a `Chest` and prints the chest’s `id`, `name`, and `value` in a readable format.  

5. **Input / Output**  
   * All interaction is via `stdin`/`stdout`.  
   * The program should be robust to invalid menu choices (print “Invalid option.” and re‑display the menu).  

## Example  

```
=== Algoria Chest Registry ===
1. Add a Chest
2. Display a Chest
3. Total Value
4. EXIT
Choose an option: 1
Enter id: 101
Enter name: Dragon Scale
Enter value: 1250.75
Chest added.

=== Algoria Chest Registry ===
1. Add a Chest
2. Display a Chest
3. Total Value
4. EXIT
Choose an option: 1
Enter id: 202
Enter name: Phoenix Feather
Enter value: 980.00
Chest added.

=== Algoria Chest Registry ===
1. Add a Chest
2. Display a Chest
3. Total Value
4. EXIT
Choose an option: 2
Enter id to display: 101
Chest ID: 101
Name   : Dragon Scale
Value  : 1250.75 gold

=== Algoria Chest Registry ===
1. Add a Chest
2. Display a Chest
3. Total Value
4. EXIT
Choose an option: 3
Total value of all chests: 2230.75 gold

=== Algoria Chest Registry ===
1. Add a Chest
2. Display a Chest
3. Total Value
4. EXIT
Choose an option: 4
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Chest`.  
* **Function Requirement** – The logic for displaying the details of ONE specific chest must be placed in a function called `displayChest`.  
* **Pointer Arithmetic** – All traversals of the chest array (adding, searching, summing) must use raw pointers and pointer arithmetic; array indexing (`chests[i]`) is not allowed.  
* **Menu Requirement** – The menu must include an explicit option `4` (or the keyword “EXIT”) that terminates the program.  
* **Memory Management** – Dynamically allocated memory must be released before program exit.  

---

## Problem 58 - openai/gpt-oss-120b - Iteration 3
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, an author, and a count of how many copies are currently on the shelf. The library wants a small console program that lets a librarian browse the catalog, look up a single book, and update the number of copies using only pointer operations (no array indexing with `[]`).  

## Requirements  
Write a C program that:

1. **Stores** up to **20** books in an array of `struct Book`.  
2. **Initialises** the array with at least five hard‑coded books of your choice.  
3. **Presents** a text‑based menu with the following options:  
   1. **List all books** – print every book’s ISBN, title, author, and copy count.  
   2. **Find a book by ISBN** – prompt for an ISBN, locate the matching book, and display its details using a function called `displayBook`.  
   3. **Update copy count** – prompt for an ISBN and a new integer value, then modify the copy count of the matching book.  
   4. **Exit** – terminate the program. *(The exit option must be clearly numbered, e.g., “4. Exit”.)*
4. **All traversals and element accesses** must be performed with **pointer arithmetic** only (e.g., `*(books + i)`, `books + i`, etc.). Direct indexing such as `books[i]` is **not allowed**.  
5. **The function `displayBook`** must take a pointer to a `struct Book` and print its fields in a readable format. No other helper functions are required, but you may add them if you wish.  

## Example Interaction  

```
=== Library Catalog Menu ===
1. List all books
2. Find a book by ISBN
3. Update copy count
4. Exit
Enter choice: 1

ISBN: 978-0131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 4

ISBN: 978-0201633610
Title: Design Patterns
Author: Gamma et al.
Copies: 2

...

=== Library Catalog Menu ===
1. List all books
2. Find a book by ISBN
3. Update copy count
4. Exit
Enter choice: 2
Enter ISBN to search: 978-0201633610

ISBN: 978-0201633610
Title: Design Patterns
Author: Gamma et al.
Copies: 2

=== Library Catalog Menu ===
1. List all books
2. Find a book by ISBN
3. Update copy count
4. Exit
Enter choice: 3
Enter ISBN to update: 978-0201633610
Enter new copy count: 5
Copy count updated.

=== Library Catalog Menu ===
1. List all books
2. Find a book by ISBN
3. Update copy count
4. Exit
Enter choice: 4
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct Book` containing at least the fields: `char isbn[20]; char title[100]; char author[100]; int copies;`.  
- **Function Requirement** – The logic for displaying the details of a single book **must be in a function named `displayBook`** that receives a pointer to `struct Book`.  
- **Pointer‑Only Access** – You may **not** use the array subscript operator (`[]`) anywhere in the program; all accesses to the `books` array must be performed with pointer arithmetic.  
- **Menu Requirement** – If you implement a menu (as strongly recommended), it **must** include a distinct option to **EXIT** the program, clearly numbered (e.g., option 4).  

Design the problem so that students practice declaring structs, passing pointers to functions, and navigating an array with pointer arithmetic.

---

## Problem 59 - openai/gpt-oss-120b - Iteration 4
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Club maintains a small “Lost‑and‑Found” inventory of items that students leave in classrooms. Each item is described by three pieces of information: a **name** (string, up to 30 characters), a **room number** (integer), and a **day‑of‑the‑year** when it was found (integer 1‑365).  

You have been asked to write a C program that stores a collection of these items using dynamic memory and lets the user query the list. The emphasis of the assignment is to practice **pointers**, **pointer arithmetic**, and the use of **structures**.

## Requirements  

1. Define a `struct Item` that holds the three fields described above.  
2. At program start, dynamically allocate an array capable of holding **exactly 10** `Item` objects.  
3. Prompt the user to enter the data for each of the 10 items (name, room, day).  
4. After the data entry phase, present a **menu** that repeats until the user chooses to exit. The menu must contain the following options:  

   1. **Display all items** – print the complete list in the order entered.  
   2. **Search by room** – ask for a room number and display every item stored for that room.  
   3. **Search by day** – ask for a day‑of‑the‑year and display every item found on that day.  
   4. **Exit** – terminate the program.  

5. All display operations (printing a single `Item`) must be performed by a function named `displayItem` that receives a pointer to an `Item`.  
6. The menu handling may be placed in `main`, but any other helper functions must be **separate** from `main`.  
7. Use **pointer arithmetic** (e.g., `ptr + i`, `*(ptr + i)`) when iterating over the dynamically allocated array; do **not** use array indexing (`items[i]`).  

## Example Input / Output  

```
Enter data for 10 lost‑and‑found items:
Item 1 name: Umbrella
Item 1 room #: 203
Item 1 day found (1‑365): 45

Item 2 name: Calculator
Item 2 room #: 101
Item 2 day found (1‑365): 45
...
[continue until Item 10]

--- MENU ---
1) Display all items
2) Search by room
3) Search by day
4) Exit
Choose an option: 2
Enter room number to search: 101

Item found:
Name: Calculator
Room: 101
Day: 45

--- MENU ---
1) Display all items
2) Search by room
3) Search by day
4) Exit
Choose an option: 4
Goodbye!
```

*Note:* The exact formatting is not critical, but the program must correctly read the data, perform the requested searches, and display matching items using `displayItem`.

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented with a `struct Item`.  
- **Function Requirement:** The logic for displaying the details of **one** specific entity must be in a function called `displayItem`. Its prototype should be `void displayItem(const struct Item *p);`.  
- **Pointer Arithmetic Requirement:** When traversing the array of items, you must use pointer arithmetic (`ptr`, `ptr + i`, `*(ptr + i)`, etc.) and **must not** use the array subscript operator (`[]`).  
- **Menu Exit Requirement:** The menu must include an explicit option to **EXIT** the program (option 4 in the example).  

*All other aspects of the implementation are left to the student.*

---

## Problem 60 - openai/gpt-oss-120b - Iteration 5
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Lab maintains a small inventory of **lab workstations**. Each workstation has a unique identifier, a CPU speed (in GHz), and the amount of RAM (in GB). The lab manager wants a simple console program that lets a user browse the inventory, add new workstations, and look up a workstation by its identifier. Because the lab’s software is written in C, the manager insists that the program demonstrate proper use of **pointers**, **pointer arithmetic**, and **structures**.

## Requirements  
Write a C program that fulfills the following specifications:

1. **Data representation**  
   * Define a `struct Workstation` containing:  
     ```c
     int id;          // unique identifier, positive integer
     float cpuGHz;    // CPU speed, e.g., 3.2
     int ramGB;       // RAM size, e.g., 16
     ```  
   * Store the workstations in a dynamically‑allocated array (allocated with `malloc`/`realloc`).  
   * All accesses to the array must be performed via pointers and pointer arithmetic – **do not use the subscript operator `[]`** for reading or writing workstation data.

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new workstation** – prompt for `id`, `cpuGHz`, and `ramGB`, then append it to the array (re‑allocating if necessary). |
   | 2      | **Display a workstation** – ask for an `id`; locate the matching workstation and print its details. |
   | 3      | **List all workstations** – iterate through the array and print each workstation’s data. |
   | 0      | **Exit** – terminate the program. |

3. **Functional details**  
   * When adding a workstation, ensure the `id` does not already exist; if it does, print an error and do not add a duplicate.  
   * When displaying a specific workstation (option 2), if the `id` is not found, print “Workstation not found.”  
   * All output must be neatly formatted, e.g.:  
     ```
     ID: 101   CPU: 3.4 GHz   RAM: 16 GB
     ```

4. **Modular design**  
   * Implement a function `void displayWorkstation(const struct Workstation *ws);` that prints the details of **one** workstation.  
   * All other logic (adding, searching, listing) may be placed in `main()` or additional helper functions, but the display of a single workstation **must** be performed by `displayWorkstation`.

## Example Interaction  

```
=== Lab Workstation Inventory ===
1. Add workstation
2. Display workstation by ID
3. List all workstations
0. Exit
Enter choice: 1
Enter ID: 101
Enter CPU speed (GHz): 3.4
Enter RAM (GB): 16
Workstation added.

=== Lab Workstation Inventory ===
1. Add workstation
2. Display workstation by ID
3. List all workstations
0. Exit
Enter choice: 1
Enter ID: 102
Enter CPU speed (GHz): 2.8
Enter RAM (GB): 8
Workstation added.

=== Lab Workstation Inventory ===
1. Add workstation
2. Display workstation by ID
3. List all workstations
0. Exit
Enter choice: 2
Enter ID to display: 101
ID: 101   CPU: 3.4 GHz   RAM: 16 GB

=== Lab Workstation Inventory ===
1. Add workstation
2. Display workstation by ID
3. List all workstations
0. Exit
Enter choice: 3
ID: 101   CPU: 3.4 GHz   RAM: 16 GB
ID: 102   CPU: 2.8 GHz   RAM: 8 GB

=== Lab Workstation Inventory ===
1. Add workstation
2. Display workstation by ID
3. List all workstations
0. Exit
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Structure usage** – the primary data entity must be represented by a `struct Workstation`.  
* **Display function** – the logic for printing the details of a single workstation must reside in a function named `displayWorkstation`.  
* **Pointer‑only array access** – after the array is allocated, you may **only** read or write elements using pointers and pointer arithmetic (`*(ptr + i)`, `ptr[i]` is *not* allowed).  
* **Menu requirement** – the program must present a menu as described, and option **0** must be the explicit command to **EXIT** the program.  

Design the solution so that a student who has just learned pointers and pointer arithmetic can implement it without needing advanced C features.

---

## Problem 61 - llama-3.3-70b-versatile - Iteration 1
# STEP 1: PROBLEM
In a university's computer science department, student records are stored in a large database. To efficiently manage these records, the department wants a program that can store, display, and manipulate student information using pointers and pointer arithmetic. The program should be able to store student details such as student ID, name, and grade point average (GPA). 

The program's functionality should include:
1. Dynamically allocating memory for a specified number of students.
2. Allowing users to input student details.
3. Displaying all student records.
4. Finding and displaying the details of a specific student by their ID.
5. Calculating and displaying the average GPA of all students.

A simple example of expected input/output is:
- Input: Number of students = 2, Student 1 details: ID = 1, Name = John, GPA = 3.5, Student 2 details: ID = 2, Name = Alice, GPA = 3.8
- Output: All students' details, followed by the average GPA, and then the details of a specific student when searched by ID.

### CONSTRAINTS
- Must use a 'struct' to represent a student, containing fields for student ID, name, and GPA.
- Logic for displaying the details of all students must be in a function called 'displayAllStudents'.
- The solution must include a menu-driven interface with the following options:
  1. Add student records
  2. Display all student records
  3. Search for a student by ID
  4. Calculate and display the average GPA
  5. EXIT the program
- The program must handle invalid inputs, such as negative numbers for student IDs or GPAs, and provide appropriate error messages.
- If a menu is implemented, the program must exit when the user selects the 'EXIT' option (option 5).

---

## Problem 62 - llama-3.3-70b-versatile - Iteration 2
# STEP 1: PROBLEM
You are the curator of a local library, and you want to create a program to manage the books in your collection. The program should store information about each book, including its title, author, and publication year. You have decided to use pointers and pointer arithmetic to efficiently manage the memory used by the program.

The program should have the following functionality:
1. Allow the user to add a new book to the collection.
2. Display all the books in the collection.
3. Allow the user to search for a specific book by its title.
4. Allow the user to delete a book from the collection.

### CONSTRAINTS
* The solution must be implemented using a single function besides main(), called `manageLibrary`.
* Must use a `struct` to represent the primary data entity (Book).
* Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
* The program must use pointers and pointer arithmetic to manage the memory used by the collection of books.
* If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a new book
Title: "Introduction to Computer Science"
Author: "John Doe"
Publication Year: 2020
2. Display all books
3. Search for a book
Title: "Introduction to Computer Science"
4. Delete a book
Title: "Introduction to Computer Science"
5. Exit
```
Example Output:
```
Book added successfully!
All books:
Title: "Introduction to Computer Science"
Author: "John Doe"
Publication Year: 2020
Book found:
Title: "Introduction to Computer Science"
Author: "John Doe"
Publication Year: 2020
Book deleted successfully!
```

---

## Problem 63 - llama-3.3-70b-versatile - Iteration 3
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books on the shelves using a simple computer program. The librarian has a list of books with their titles, authors, and publication years. The librarian wants to be able to display the details of each book and also calculate the total number of books and the average publication year.

The program should be able to store the book details in an array of structures, where each structure represents a book. The program should also be able to perform pointer arithmetic to access and manipulate the book details.

### REQUIREMENTS
1. Define a structure `Book` to represent a book with title, author, and publication year.
2. Create an array of `Book` structures to store the book details.
3. Write a function `displayBookDetails` to display the details of all books.
4. Write a function `calculateStatistics` to calculate the total number of books and the average publication year.
5. The program should have a menu with options to:
   - Display book details
   - Calculate statistics
   - Add a new book
   - Exit the program

### EXAMPLE INPUT/OUTPUT
Example input:
```
Enter the number of books: 2
Enter title of book 1: Book1
Enter author of book 1: Author1
Enter publication year of book 1: 2010
Enter title of book 2: Book2
Enter author of book 2: Author2
Enter publication year of book 2: 2015
```
Example output:
```
Book details:
Title: Book1, Author: Author1, Publication year: 2010
Title: Book2, Author: Author2, Publication year: 2015
Total number of books: 2
Average publication year: 2012.5
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of all books must be in a function called `displayBookDetails`.
- Logic for calculating the statistics must be in a function called `calculateStatistics`.
- The solution must be implemented with a single array of structures to store the book details.
- The program must have a menu with a specific option to EXIT the program (option 4).

### MENU OPTIONS
1. Display book details
2. Calculate statistics
3. Add a new book
4. Exit the program (type '4' to exit)

---

## Problem 64 - llama-3.3-70b-versatile - Iteration 4
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The library wants to implement a simple system to manage the books using an array of structures, where each structure represents a book. The system should allow users to add books, display all books, and search for a specific book by its identifier.

The library has a limited number of shelves, and each shelf can hold a maximum of 100 books. The system should also keep track of the number of books on each shelf.

### REQUIREMENTS
1. The program should use an array of structures to represent the books, where each structure has the following members: `id` (unique identifier), `title`, `author`, and `publicationYear`.
2. The program should have a function to add a new book to the system.
3. The program should have a function to display all books in the system.
4. The program should have a function to search for a specific book by its identifier.
5. The program should keep track of the number of books on each shelf.

### EXAMPLE INPUT/OUTPUT
```
Add a book:
Enter book id: 1
Enter book title: Introduction to Computer Science
Enter book author: John Smith
Enter book publication year: 2020

Display all books:
Book 1: Introduction to Computer Science by John Smith (2020)

Search for a book:
Enter book id: 1
Book found: Introduction to Computer Science by John Smith (2020)
```

### CONSTRAINTS
* The solution must be implemented using a single function besides `main()`, called `manageLibrary()`, which will handle all the operations.
* The program must use a `struct` to represent the primary data entity, which is the book.
* The `struct` must have the following members: `id`, `title`, `author`, and `publicationYear`.
* The program must use pointer arithmetic to access and manipulate the array of structures.
* The program must have a menu with the following options:
	1. Add a book
	2. Display all books
	3. Search for a book
	4. EXIT (to exit the program)
* The program must validate user input to ensure that the book id is unique and the publication year is valid (between 1900 and 2024).
* The program must handle the case where the library is full (i.e., all shelves are full).

---

## Problem 65 - llama-3.3-70b-versatile - Iteration 5
# STEP 1: PROBLEM
In a college setting, student records are maintained using a system that stores information such as student ID, name, and GPA. As the system administrator, you are tasked with designing a simple console-based application to manage these student records. The application should allow users to add, remove, and display student records. Since memory management is crucial for efficient storage, the application will utilize pointers and pointer arithmetic to handle student records.

The application should have the following functionality:
1. Add a new student record: The user should be able to input the student ID, name, and GPA, and the record should be added to the existing list of records.
2. Remove a student record: The user should be able to input a student ID, and the corresponding record should be removed from the list if it exists.
3. Display all student records: The application should display the details of all student records.
4. Display a specific student record: The user should be able to input a student ID, and the application should display the details of the corresponding record if it exists.

### Example
Input:
```
1. Add a new student record
Student ID: 12345
Name: John Doe
GPA: 3.5

2. Add a new student record
Student ID: 67890
Name: Jane Doe
GPA: 3.8

3. Display all student records
```
Output:
```
Student ID: 12345
Name: John Doe
GPA: 3.5

Student ID: 67890
Name: Jane Doe
GPA: 3.8
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student record.
- Logic for displaying the details of all student records must be in a function called `displayAllRecords`.
- The solution must be implemented with a single array to store all student records.
- The application must have a menu-driven interface with the following options:
  1. Add a new student record
  2. Remove a student record
  3. Display all student records
  4. Display a specific student record
  5. EXIT the program
- The EXIT option should be selected by entering '5' or typing 'EXIT'. 

Note: The application should handle memory allocation and deallocation dynamically using pointers and pointer arithmetic.

---

## Problem 66 - llama-3.3-70b-versatile - Iteration 6
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a simple program to manage the books in your library. Each book has a title, author, and publication year. You want to store the books in an array and use pointers to manipulate the data.

Background:
The library has a collection of books, and you need to keep track of the title, author, and publication year of each book. You want to create a program that allows you to add, remove, and display books from the collection.

Requirements:
1. The program must store the books in an array of structures, where each structure represents a book with its title, author, and publication year.
2. The program must have a function to add a new book to the collection.
3. The program must have a function to remove a book from the collection by its title.
4. The program must have a function to display all the books in the collection.
5. The program must have a function to display the details of a specific book by its title.

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must include a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- The program must use pointer arithmetic to manipulate the array of structures.

Example Input/Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 3
Book1 by Author1, published in 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 4
Enter book title: Book1
Book1 by Author1, published in 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 5
Exiting the program...
```

---

## Problem 67 - llama-3.3-70b-versatile - Iteration 7
# STEP 1: PROBLEM
In a university setting, a student's information is crucial for administrative purposes. To efficiently manage student records, you are tasked with designing a program that utilizes pointers and pointer arithmetic to store and manipulate student data.

Background:
The university wants to keep track of student information, including their names, student IDs, and GPAs. The program should allow administrators to add new students, display all students, and find a specific student by their ID.

Requirements:
1. The program must store student information in a dynamically allocated array of structures, where each structure represents a student.
2. The program must provide a menu-driven interface with the following options:
   - Add a new student
   - Display all students
   - Find a student by ID
   - Exit the program
3. When adding a new student, the program must dynamically allocate memory for the new student structure and add it to the array.
4. When displaying all students, the program must iterate through the array and print out the details of each student.
5. When finding a student by ID, the program must iterate through the array and print out the details of the student with the matching ID.

Example Input/Output:
```
Menu:
1. Add a new student
2. Display all students
3. Find a student by ID
4. Exit
Choose an option: 1
Enter student name: John Doe
Enter student ID: 12345
Enter student GPA: 3.5

Menu:
1. Add a new student
2. Display all students
3. Find a student by ID
4. Exit
Choose an option: 2
Student 1:
Name: John Doe
ID: 12345
GPA: 3.5

Menu:
1. Add a new student
2. Display all students
3. Find a student by ID
4. Exit
Choose an option: 3
Enter student ID: 12345
Student found:
Name: John Doe
ID: 12345
GPA: 3.5
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student data entity.
- The logic for displaying the details of all students must be in a function called `displayAllStudents`.
- The logic for finding a student by ID must be in a function called `findStudentByID`.
- The program must use pointer arithmetic to iterate through the array of student structures.
- The menu option to exit the program is option 4, labeled "Exit".

---

## Problem 68 - llama-3.3-70b-versatile - Iteration 8
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their student ID, name, and grade point average (GPA). You need to design a program that can store, display, and manage student information using pointers and pointer arithmetic.

Background: 
The university has a large number of students, and the system needs to efficiently store and retrieve student information. The program should be able to add new students, display the details of all students, and display the details of a specific student.

Requirements:
1. The program should have a menu-driven interface with the following options:
   - Add a new student
   - Display all students
   - Display a specific student
   - Exit the program
2. The program should store student information in a dynamically allocated array of structures.
3. The program should use pointer arithmetic to traverse the array of structures.

Example of expected Input/Output:
If the user chooses to add a new student, the program should prompt the user to enter the student's ID, name, and GPA. If the user chooses to display all students, the program should display the details of all students in the database.

Example:
```
Menu:
1. Add a new student
2. Display all students
3. Display a specific student
4. Exit

Enter your choice: 1
Enter student ID: 1234
Enter student name: John Doe
Enter student GPA: 3.5

Menu:
1. Add a new student
2. Display all students
3. Display a specific student
4. Exit

Enter your choice: 2
Student ID: 1234, Name: John Doe, GPA: 3.5
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu-driven interface and the logic for adding, displaying, and exiting the program.
- If a menu is implemented, it must include a specific menu option to EXIT the program (option 4).

---

## Problem 69 - llama-3.3-70b-versatile - Iteration 9
# STEP 1: PROBLEM
In a library management system, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. To efficiently manage the books, the library uses a pointer-based system to keep track of the books on each shelf. As a programmer, your task is to design a program that simulates this system.

The program should allow users to add books to the system, display the details of all books, and search for a specific book by its identifier. The system should also be able to display the details of a specific book.

Here is a precise list of requirements for the program's functionality:
1. The program should be able to store a maximum of 100 books.
2. Each book should have a unique identifier, title, author, and publication year.
3. The program should have an option to add a new book to the system.
4. The program should have an option to display the details of all books in the system.
5. The program should have an option to search for a specific book by its identifier and display its details.
6. The program should have an option to exit the program.

Here is a simple example of expected input/output:
```
Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit

Choose an option: 1
Enter book id: 1
Enter book title: Book Title
Enter book author: Book Author
Enter book publication year: 2020

Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit

Choose an option: 2
Book 1:
Id: 1
Title: Book Title
Author: Book Author
Publication Year: 2020

Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit

Choose an option: 3
Enter book id to search: 1
Book 1:
Id: 1
Title: Book Title
Author: Book Author
Publication Year: 2020
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program by choosing option 4. 
- The program must use pointer arithmetic to manage the books in the system.

---

## Problem 70 - llama-3.3-70b-versatile - Iteration 10
# STEP 1: PROBLEM
In a university setting, student records are maintained using a student information system. The system stores student details such as student ID, name, and GPA. To efficiently manage these records, pointers and pointer arithmetic can be utilized. Your task is to design a program that can store, display, and update student records using pointers and pointer arithmetic.

The program should have the following functionality:
1. Initialize an array of student structures with a specified size.
2. Allow users to input student details (ID, name, GPA) and store them in the array.
3. Display all student records.
4. Update a specific student record based on the student ID.
5. Display the details of a specific student record based on the student ID.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all menu options.
- If a menu is implemented, it must include the following options:
  1. Add Student Record
  2. Display All Student Records
  3. Update Student Record
  4. Display Specific Student Record
  5. EXIT (to exit the program)
- The program should handle invalid inputs and display error messages accordingly.

### EXAMPLE
Example Input:
```
Enter student ID: 1
Enter student name: John Doe
Enter student GPA: 3.5
```
Example Output:
```
Student ID: 1
Student Name: John Doe
Student GPA: 3.5
```
Note: The actual implementation may vary based on the chosen programming language and the specific requirements of the assignment.

---

## Problem 71 - llama-3.3-70b-versatile - Iteration 11
# STEP 1: PROBLEM
You are the manager of a library, and you need to manage the books in your library. You have decided to write a program to store and display the details of the books. You want to use an array of structures to store the book details, where each structure represents a book with its title, author, and publication year. You also want to use pointers and pointer arithmetic to navigate through the array and display the details of the books.

The program should have the following functionality:
1. Store the details of up to 10 books in an array of structures.
2. Display the details of all the books in the array.
3. Display the details of a specific book based on its index in the array.
4. Allow the user to add a new book to the array.

### CONSTRAINTS
- The solution must be implemented with a single function besides main(), called `manageLibrary()`.
- Must use a `struct` to represent the primary data entity (i.e., a book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayBook()`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Display all books
2. Display a specific book
3. Add a new book
4. Display menu
5. Exit

Enter your choice: 1
Book 1:
Title: Book1
Author: Author1
Year: 2000

Book 2:
Title: Book2
Author: Author2
Year: 2001

...

Enter your choice: 2
Enter the index of the book: 1
Book 1:
Title: Book1
Author: Author1
Year: 2000
```

Note: The program should handle invalid inputs and edge cases, such as trying to access a book at an index that is out of range.

---

## Problem 72 - llama-3.3-70b-versatile - Iteration 12
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a university library. Each book has a unique identifier, title, author, and publication year. To efficiently store and manage this information, you decide to use an array of structures to represent the books. Your task is to create a program that allows users to add, remove, and display books in the library.

The program should have the following functionality:
1. Initialize an empty array of structures to represent the books.
2. Provide a menu-driven interface for users to interact with the program.
3. Allow users to add a new book to the library by inputting its identifier, title, author, and publication year.
4. Allow users to remove a book from the library by inputting its identifier.
5. Allow users to display all books in the library.
6. Allow users to search for a specific book by its identifier and display its details.

### CONSTRAINTS
- The solution must be implemented using a single function besides `main()`, called `manageLibrary()`.
- Must use a `struct` to represent the primary data entity (Book).
- The program must use pointer arithmetic to manipulate the array of structures.
- The menu options should be numbered, and the option to EXIT the program should be option 6.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. Display menu
6. EXIT

Choose an option: 1
Enter book identifier: 1
Enter book title: Introduction to Programming
Enter book author: John Smith
Enter publication year: 2020

Choose an option: 3
Book 1:
Identifier: 1
Title: Introduction to Programming
Author: John Smith
Publication Year: 2020

Choose an option: 6
Exiting the program...
```
Note: The above example is a simplified representation of the expected input/output. The actual output may vary based on the implementation details.

---

## Problem 73 - llama-3.3-70b-versatile - Iteration 13
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a Computer Science professor, you want to develop a simple console-based application to manage student records using pointers and pointer arithmetic. The application should allow users to add, display, and update student records.

Background:
The university wants to keep track of student names, student IDs, and grades. The application should store this information in memory and provide basic operations to manipulate the data.

Requirements:
1. The program should dynamically allocate memory for each student record.
2. The program should provide options to add a new student record, display all student records, and update a specific student record.
3. The program should use pointers and pointer arithmetic to navigate and manipulate the student records.
4. The program should validate user input for student IDs and grades.

Example Input/Output:
```
Menu:
1. Add Student Record
2. Display All Student Records
3. Update Student Record
4. Exit

Choose an option: 1
Enter student name: John Doe
Enter student ID: 12345
Enter grade: 90

Choose an option: 2
Student Records:
Name: John Doe, ID: 12345, Grade: 90

Choose an option: 3
Enter student ID to update: 12345
Enter new grade: 95

Choose an option: 2
Student Records:
Name: John Doe, ID: 12345, Grade: 95
```

### CONSTRAINTS
* The solution must be implemented using a `struct` to represent the student record, which should contain fields for name, student ID, and grade.
* The logic for displaying the details of all student records must be in a function called `displayRecords`.
* The solution must include a menu with options to add, display, and update student records, as well as an option to exit the program. The exit option should be clearly labeled as "4. Exit".
* The program must validate user input for student IDs (must be a 5-digit integer) and grades (must be between 0 and 100).
* The program must use dynamic memory allocation to store student records.
* The menu option to exit the program is "4. Exit".

---

## Problem 74 - llama-3.3-70b-versatile - Iteration 14
# STEP 1: PROBLEM
In a small library, books are organized on shelves according to their genres. Each book has a unique identifier, title, author, and publication year. The librarian wants to create a simple program to manage the books on the shelves. The program should allow the librarian to add new books, display all books, and search for a specific book by its identifier.

The program will use an array to store the books, where each book is represented by a struct. The librarian can interact with the program through a simple menu.

### REQUIREMENTS
- The program must store books in an array of structs, where each struct represents a book with its identifier, title, author, and publication year.
- The program must provide a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Search for a book by its identifier
  4. Exit the program
- When adding a new book, the program must prompt the user to enter the book's details (identifier, title, author, and publication year).
- When displaying all books, the program must show the details of each book in the array.
- When searching for a book, the program must prompt the user to enter the book's identifier and then display the book's details if found.

### EXAMPLE
Input:
```
Choose an option:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit
1
Enter book's identifier: 1
Enter book's title: Introduction to Programming
Enter book's author: John Doe
Enter book's publication year: 2020
Choose an option:
2
```
Output:
```
Book 1:
Identifier: 1
Title: Introduction to Programming
Author: John Doe
Publication Year: 2020
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The solution must be implemented with a single function besides `main()` for each menu option.
- The program must use pointer arithmetic to access and manipulate the array of structs.
- To exit the program, the user must choose option 4 from the menu.

---

## Problem 75 - llama-3.3-70b-versatile - Iteration 15
# STEP 1: PROBLEM
As a curator of a local museum, you are tasked with organizing an exhibition of ancient artifacts. Each artifact has a unique identifier, name, description, and age. You want to create a program that allows you to manage these artifacts by storing their information in memory and performing various operations.

The program should be able to store information about multiple artifacts, display the details of all artifacts, and display the details of a specific artifact given its identifier.

### REQUIREMENTS
1. The program must store information about multiple artifacts in memory using pointers and pointer arithmetic.
2. The program must display the details of all artifacts when requested.
3. The program must display the details of a specific artifact given its identifier when requested.
4. The program must have a menu that allows the user to interact with the program.

### EXAMPLE INPUT/OUTPUT
If the user adds three artifacts with the following information:
- Artifact 1: ID = 1, Name = "Vase", Description = "Ancient Greek vase", Age = 2000
- Artifact 2: ID = 2, Name = "Sculpture", Description = "Roman sculpture", Age = 1500
- Artifact 3: ID = 3, Name = "Coin", Description = "Ancient coin", Age = 1000

When the user requests to display all artifacts, the program should output:
```
Artifact 1:
ID: 1
Name: Vase
Description: Ancient Greek vase
Age: 2000

Artifact 2:
ID: 2
Name: Sculpture
Description: Roman sculpture
Age: 1500

Artifact 3:
ID: 3
Name: Coin
Description: Ancient coin
Age: 1000
```

When the user requests to display the details of artifact with ID 2, the program should output:
```
Artifact 2:
ID: 2
Name: Sculpture
Description: Roman sculpture
Age: 1500
```

### CONSTRAINTS
- Must use a 'struct' to represent an artifact.
- Logic for displaying the details of ONE specific artifact must be in a function called 'displayArtifact'.
- The solution must be implemented with a single function besides main() to handle the menu operations.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5. The menu should look like this:
```
Menu:
1. Add an artifact
2. Display all artifacts
3. Display a specific artifact
4. Delete an artifact
5. EXIT
```
Note: The program should handle invalid inputs and errors, such as trying to display or delete a non-existent artifact.

---

## Problem 76 - openai/gpt-oss-120b - Iteration 6
# STEP 1: PROBLEM  

## Background  
Captain Aria is cataloguing the loot recovered from a recent expedition. Each piece of loot is described by a **Treasure** record that stores:  

* an integer `id` (unique identifier)  
* a string `type` (e.g., “Gold”, “Gem”, “Artifact”) – maximum 20 characters  
* a floating‑point `value` (in gold pieces)  

The captain wants a small console program that lets a junior officer **add**, **list**, **search**, and **remove** treasures while practicing pointer arithmetic. The officer must manipulate the collection through raw pointers, not through array indexing (`[]`).  

## Requirements  

1. **Data Structure**  
   * Define a `struct Treasure` that holds the three fields described above.  

2. **Storage**  
   * Dynamically allocate an array capable of holding up to **100** treasures.  
   * Keep track of the current number of stored treasures (`size`).  

3. **Menu** (displayed repeatedly until the user chooses to quit)  
   * `1` – **Add a treasure**  
        * Prompt for `id`, `type`, and `value`.  
        * Store the new treasure at the first free position using pointer arithmetic.  
        * If the array is full, display an error message.  
   * `2` – **List all treasures**  
        * Traverse the array with a pointer, printing each treasure on its own line.  
   * `3` – **Search by ID**  
        * Prompt for an `id`.  
        * Scan the collection using pointer arithmetic.  
        * If found, call `displayTreasure` (see constraint) to show its details; otherwise print “Not found”.  
   * `4` – **Remove a treasure**  
        * Prompt for an `id`.  
        * Locate the treasure using pointer arithmetic.  
        * If found, shift all subsequent elements left (again using pointers) to fill the gap and decrement `size`.  
        * If not found, print “Not found”.  
   * `5` – **EXIT** – terminate the program.  

4. **Functions**  
   * Implement a function `void displayTreasure(const struct Treasure *t)` that prints a single treasure in the format:  
     ```
     ID: <id>, Type: <type>, Value: <value>
     ```  
   * All other logic must be placed in `main()` (i.e., only one additional function besides `main`).  

5. **Pointer Usage**  
   * **Never** use the subscript operator `[]` to access elements of the treasure array.  
   * All traversals, insertions, deletions, and searches must be performed with pointer arithmetic (`*ptr`, `ptr + i`, etc.).  

## Example Interaction  

```
--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 1
Enter ID: 101
Enter type: Gold
Enter value: 2500.75
Treasure added.

--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 1
Enter ID: 202
Enter type: Gem
Enter value: 1800.00
Treasure added.

--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 2
ID: 101, Type: Gold, Value: 2500.75
ID: 202, Type: Gem, Value: 1800.00

--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 3
Enter ID to search: 202
ID: 202, Type: Gem, Value: 1800.00

--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 4
Enter ID to remove: 101
Treasure removed.

--- Treasure Catalog ---
1) Add a treasure
2) List all treasures
3) Search by ID
4) Remove a treasure
5) EXIT
Choose an option: 5
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Treasure`.  
* **Display Function** – Details of a single treasure must be shown by a function named `displayTreasure`.  
* **Function Count** – Apart from `main`, only the `displayTreasure` function may be defined.  
* **Pointer‑Only Access** – No array indexing (`[]`) is allowed when working with the dynamically allocated treasure array.  
* **Menu Exit Option** – The menu must include an explicit option (`5` in the example) labeled **EXIT** that terminates the program.  

---

## Problem 77 - openai/gpt-oss-120b - Iteration 7
# STEP 1: PROBLEM  

## Background  
The university’s **Campus Navigation System** stores the locations of all campus buildings in a dynamically allocated array. Each building is represented by a `struct Building` that holds the building’s name (a short string) and its coordinates on the campus map (two integers, `x` and `y`).  

Your task is to write a small program that lets a user query the distance between two buildings. Because the array of buildings is allocated at run‑time, you must use **pointers and pointer arithmetic** to walk through the collection, locate the requested buildings, and compute the Euclidean distance between them (rounded to two decimal places).

## Requirements  

1. **Data structure**  
   * Define a `struct Building` with the following members:  
     ```c
     char name[32];   // null‑terminated building name
     int  x;          // x‑coordinate
     int  y;          // y‑coordinate
     ```  

2. **Input**  
   * First read an integer `N` (1 ≤ N ≤ 100) – the number of buildings.  
   * For each building, read a line containing the name (a single word, no spaces) followed by two integers `x` and `y`.  
   * After the list, the program enters a **menu loop** (see requirement 5).  

3. **Distance query**  
   * When the user selects the “Find distance” option, prompt for two building names (`A` and `B`).  
   * Locate the two structures in the dynamically allocated array using **pointer arithmetic only** (no array indexing `[]`).  
   * If either name is not found, display `Error: building not found.`  
   * Otherwise compute the Euclidean distance:  

     \[
     d = \sqrt{(x_A - x_B)^2 + (y_A - y_B)^2}
     \]

   * Print the distance rounded to two decimal places:  

     `Distance between <A> and <B> is <d>`  

4. **Display a building**  
   * Implement a function `void displayBuilding(const struct Building *b)` that prints a single building in the format:  

     `<name>: (<x>, <y>)`  

   * This function must be used whenever a building’s details need to be shown (e.g., after a successful lookup).  

5. **Menu** (must be implemented)  

   ```
   1. List all buildings
   2. Find distance between two buildings
   3. Exit
   Enter choice: 
   ```

   * **Option 1** – iterate through the array using pointer arithmetic and call `displayBuilding` for each entry.  
   * **Option 2** – perform the distance query described above.  
   * **Option 3** – terminate the program.  

6. **Memory management**  
   * Allocate the array of `struct Building` with `malloc` (or `calloc`).  
   * Release the allocated memory before exiting.  

## Example  

**Input** (user input shown in bold)  

```
5
Library 10 20
Gym 15 25
Cafeteria 30 10
Lab 5 5
Admin 0 0
1
2
Library Gym
3
```

**Program Output**  

```
--- Campus Buildings ---
Library: (10, 20)
Gym: (15, 25)
Cafeteria: (30, 10)
Lab: (5, 5)
Admin: (0, 0)

--- Menu ---
1. List all buildings
2. Find distance between two buildings
3. Exit
Enter choice: 2
Enter first building name: Library
Enter second building name: Gym
Library: (10, 20)
Gym: (15, 25)
Distance between Library and Gym is 7.07

--- Menu ---
1. List all buildings
2. Find distance between two buildings
3. Exit
Enter choice: 3
Goodbye!
```

If a name is miss‑spelled:

```
Enter first building name: Library
Enter second building name: Dorm
Error: building not found.
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be a `struct Building` as defined above.  
2. **Function requirement** – The logic for displaying a single building must be placed in a function named `displayBuilding`.  
3. **Pointer arithmetic only** – When traversing the dynamic array (listing, searching, etc.) you may **not** use the subscript operator `[]`. Access elements solely via pointers (`ptr`, `ptr + i`, `*(ptr + i)`, etc.).  
4. **Menu** – The program must present a menu with the three options listed, and **option 3 must be the explicit “Exit” command**.  
5. **Single‑file implementation** – All code must reside in one source file (e.g., `main.c`). Apart from `main`, you may create additional helper functions, but the only required extra function is `displayBuilding`.  

Write the program in C (C99 or later). The solution should compile without warnings using `gcc -Wall -Wextra -std=c99`.

---

## Problem 78 - openai/gpt-oss-120b - Iteration 8
# STEP 1: PROBLEM  

## Background  
The campus library is digitizing its collection of **reference books**. Each book has a unique identifier, a title, and the number of pages. The library wants a small console program that stores a fixed‑size array of books, lets the user add books, view a specific book, and compute the total number of pages in the collection. The assignment is meant to give students practice with **structures, pointers, and pointer arithmetic**.

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` containing:  
     - `int id;`            // unique identifier (positive integer)  
     - `char title[51];`    // title string (max 50 characters, null‑terminated)  
     - `int pages;`         // number of pages (positive integer)  

2. **Program Functionality**  
   * The program must maintain an array capable of storing **up to 20** `Book` records.  
   * Present a **menu** (repeated until the user chooses to exit) with the following options:  
     1. **Add a new book** – Prompt for `id`, `title`, and `pages`. Store the record at the first free slot. If the array is full, display an appropriate message.  
     2. **Display a book** – Prompt for a book `id`. Locate the book using pointer arithmetic (do **not** use array indexing `[]`) and call a helper function `displayBook` to print its details. If the `id` does not exist, inform the user.  
     3. **Total pages** – Compute and print the sum of the `pages` field of all stored books using pointer arithmetic.  
     4. **Exit** – Terminate the program. (This option must be explicitly listed in the menu.)  

3. **User Interaction**  
   * After completing any option (except Exit), the menu should be shown again.  
   * Input validation is not required beyond what is described above.

## Example Input / Output  

```
=== Library Book Manager ===
1. Add a new book
2. Display a book
3. Total pages
4. Exit
Choose an option: 1

Enter book id: 101
Enter title: Introduction to Algorithms
Enter pages: 1312
Book added successfully.

=== Library Book Manager ===
1. Add a new book
2. Display a book
3. Total pages
4. Exit
Choose an option: 1

Enter book id: 205
Enter title: C Programming Language
Enter pages: 274
Book added successfully.

=== Library Book Manager ===
1. Add a new book
2. Display a book
3. Total pages
4. Exit
Choose an option: 2

Enter book id to display: 101
--- Book Details ---
ID: 101
Title: Introduction to Algorithms
Pages: 1312

=== Library Book Manager ===
1. Add a new book
2. Display a book
3. Total pages
4. Exit
Choose an option: 3

Total pages in collection: 1586

=== Library Book Manager ===
1. Add a new book
2. Display a book
3. Total pages
4. Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Function Requirement** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```

* **Pointer Arithmetic Only** – When searching the array (e.g., for a given `id`) and when summing pages, you must use pointer arithmetic (`ptr = ptr + 1`, `*(ptr)`, etc.) **without** using the array subscript operator `[]`.  

* **Menu Implementation** – The program must present a menu as described, and **option 4 must be the explicit “Exit” choice** that terminates the program.  

* **Single‑File Solution** – All code must reside in one source file (e.g., `main.c`). Apart from `main`, only the `displayBook` helper function is required; any additional helper functions are optional but must not duplicate the required functionality.  

* **No Dynamic Allocation** – Use a static array of 20 `Book` objects; dynamic memory allocation (`malloc`, `new`, etc.) is not allowed.  

---

## Problem 79 - openai/gpt-oss-120b - Iteration 9
# STEP 1: PROBLEM  

## Background  
The campus library has just digitized its collection of **reference books**. Each book is stored in an array of `struct Book` objects. The library’s checkout terminal must allow a librarian to **search for a book by its ISBN**, **display the details of a single book**, and **list a range of books** (e.g., from the 3‑rd to the 8‑th entry). Because the array lives in memory, the program must use **pointers and pointer arithmetic** to move through the collection instead of array indexing.

## Requirements  

Write a C program that:

1. **Defines** a `struct Book` containing at least the following fields:  
   - `char title[50];`  
   - `char author[30];`  
   - `unsigned long isbn;`   (a 13‑digit identifier)  
   - `int year;`  

2. **Creates** an array of exactly **10** `Book` objects, initialized with sample data of your choice.

3. **Presents** a simple text menu that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
   1. **Search by ISBN** – the user enters an ISBN; the program searches the array using pointer arithmetic and reports whether the book was found. If found, it calls a helper function to display the book’s details.  
   2. **Display a range** – the user enters two integers `a` and `b` (1 ≤ a ≤ b ≤ 10). The program uses pointer arithmetic to iterate from the `a`‑th to the `b`‑th book (inclusive) and prints each book’s title on a separate line.  
   3. **Exit** – terminates the program.  

4. **Implements** the display of a single book’s full information (title, author, ISBN, year) in a separate function named `void displayBook(const struct Book *p)`.

5. **Uses only pointer arithmetic** (e.g., `p = p + 1;`, `*(p + i)`) to traverse the array. Direct array indexing (`books[i]`) is **not allowed** for any traversal or search logic.

6. **Handles invalid input** gracefully (e.g., ISBN not found, range out of bounds) by printing an appropriate message and returning to the menu.

## Example Input / Output  

```
--- Library Book Manager ---
1. Search by ISBN
2. Display a range of books
3. Exit
Enter option: 1
Enter ISBN to search: 9780131103627
Book found:
Title : The C Programming Language
Author: Kernighan & Ritchie
ISBN  : 9780131103627
Year  : 1988

--- Library Book Manager ---
1. Search by ISBN
2. Display a range of books
3. Exit
Enter option: 2
Enter start index (1‑10): 3
Enter end index (1‑10): 5
Books 3 to 5:
The Mythical Man‑Month
Clean Code
Design Patterns

--- Library Book Manager ---
1. Search by ISBN
2. Display a range of books
3. Exit
Enter option: 3
Goodbye!
```

*(The titles above correspond to the sample data you initialized.)*

### CONSTRAINTS  

- The primary data entity **must** be represented by a `struct Book`.  
- The function that prints the details of a single book **must** be named `displayBook` and accept a pointer to `const struct Book`.  
- All traversal of the `Book` array **must** be performed with **pointer arithmetic**; using the subscript operator `[]` for that purpose is prohibited.  
- The program **must** present a menu that includes an explicit **Exit** option (option 3 in the example).  

Your solution should compile with a standard C compiler (e.g., `gcc -std=c11`).

---

## Problem 80 - openai/gpt-oss-120b - Iteration 10
# STEP 1: PROBLEM  

## Background  
The university’s **Campus Navigation System** stores the locations of all campus buildings in a dynamically allocated array. Each building is represented by a `struct Building` that contains the building’s name (a short string), its building‑code (an integer), and its distance in meters from the main gate.  

Your task is to write a program that lets a user **search** for a building by its building‑code and then displays the building’s details. The search must be performed using **pointer arithmetic**—no array indexing (`[]`) is allowed when scanning the array.

---

## Requirements  

1. **Data structure**  
   - Define a `struct Building` with the following members:  
     ```c
     char name[32];      // e.g., "Science Hall"
     int  code;          // unique building code, e.g., 101
     double distance;   // distance from main gate in meters
     ```  

2. **Input**  
   - The program first reads an integer **N** (1 ≤ N ≤ 100), the number of buildings.  
   - For each building, read three values on a single line: `name` (a single word, no spaces), `code`, and `distance`.  
   - After the list, the program repeatedly reads a building‑code to look up until the user chooses to exit (see the menu below).

3. **Menu** (must be presented after the initial data load)  

   ```
   ==== Campus Navigation Menu ====
   1. Search for a building by code
   2. List all buildings (in the order they were entered)
   3. EXIT
   Enter your choice: 
   ```

   - **Option 1**: Prompt the user for a building‑code, search the array using pointer arithmetic, and display the building’s details (see function requirement).  
   - **Option 2**: Print the complete list of buildings, one per line, using pointer arithmetic.  
   - **Option 3**: Terminate the program.

4. **Output**  
   - When a building is found, print:  
     ```
     Building: <name>, Code: <code>, Distance: <distance> meters
     ```  
   - If the code does not exist, print:  
     ```
     No building with code <code> found.
     ```
   - For option 2, print each building on its own line using the same format as above.

5. **Error handling**  
   - If the user enters a menu choice other than 1‑3, display “Invalid choice. Try again.” and re‑show the menu.

---

## Example Input / Output  

```
Enter number of buildings: 3
ScienceHall 101 250.5
Library      202 400.0
Gymnasium    303 150.2

==== Campus Navigation Menu ====
1. Search for a building by code
2. List all buildings
3. EXIT
Enter your choice: 1
Enter building code to search: 202
Building: Library, Code: 202, Distance: 400.0 meters

==== Campus Navigation Menu ====
1. Search for a building by code
2. List all buildings
3. EXIT
Enter your choice: 1
Enter building code to search: 999
No building with code 999 found.

==== Campus Navigation Menu ====
1. Search for a building by code
2. List all buildings
3. EXIT
Enter your choice: 2
Building: ScienceHall, Code: 101, Distance: 250.5 meters
Building: Library, Code: 202, Distance: 400.0 meters
Building: Gymnasium, Code: 303, Distance: 150.2 meters

==== Campus Navigation Menu ====
1. Search for a building by code
2. List all buildings
3. EXIT
Enter your choice: 3
```

---

### CONSTRAINTS  

1. **Struct usage** – The primary data entity **must** be a `struct Building` as described.  
2. **Function requirement** – The logic for displaying the details of **one specific building** must be placed in a function with the exact prototype:  
   ```c
   void displayBuilding(const struct Building *b);
   ```  
3. **Pointer arithmetic only** – When iterating over the array (both for searching and listing), you **may not** use the subscript operator `[]`. Access elements exclusively via pointers and pointer arithmetic (e.g., `ptr + i`, `*(ptr + i)`).  
4. **Single extra function** – Apart from `main()` and `displayBuilding`, no additional functions are required (though you may create helper functions if you wish, they are not mandatory).  
5. **Menu exit option** – The menu must contain an explicit option to **EXIT** the program (option 3 in the example).  

---  

*Design your solution to be clear, well‑commented, and to demonstrate proper use of pointers, structs, and modular code.*

---

## Problem 81 - openai/gpt-oss-120b - Iteration 11
# STEP 1: PROBLEM  

## Background  
The kingdom’s archivist has digitised the map of an ancient underground **dungeon**.  
Each chamber of the dungeon is described by three pieces of information:  

1. **room number** – an integer that uniquely identifies the chamber.  
2. **treasure** – the amount of gold (in pieces) stored in that chamber.  
3. **danger level** – an integer from 1 (safe) to 5 (very dangerous).  

The archivist wants a small C program that stores the chambers in a dynamically‑allocated array and lets a user explore the map using only pointers and pointer arithmetic (no array indexing `[]`).  

Your task is to write that program.

## Requirements  

1. **Data representation**  
   * Define a `struct` called `Room` that holds the three fields described above.  

2. **Dynamic allocation**  
   * At program start, read an integer `N` ( 1 ≤ N ≤ 100 ) – the number of chambers.  
   * Allocate memory for `N` `Room` objects in a single block using `malloc`.  

3. **Input of chamber data**  
   * For each chamber `i` (1 … N) read three integers: `room_number treasure danger`.  
   * Store the values in the allocated array **using only pointers** (no `[]`).  

4. **Menu‑driven interaction**  
   * After the data are read, repeatedly present the following menu until the user chooses to exit:  

        ```
        1) Show details of a specific room
        2) Add treasure to a room
        3) Show total treasure in the dungeon
        4) EXIT
        Enter choice: 
        ```  

   * **Option 1** – Prompt for a `room_number`. Locate the corresponding `Room` by scanning the array with pointer arithmetic and call a function `displayRoom` (see constraint) to print its details in the format:  

        ```
        Room <room_number>: Treasure = <treasure>, Danger = <danger>
        ```  

   * **Option 2** – Prompt for a `room_number` and an integer `delta`. Locate the room (pointer arithmetic) and increase its `treasure` by `delta`. Print a confirmation line:  

        ```
        Added <delta> gold to room <room_number>.
        ```  

   * **Option 3** – Compute the sum of the `treasure` fields of **all** rooms using pointer arithmetic and display:  

        ```
        Total treasure in dungeon: <sum>
        ```  

   * **Option 4** – Exit the program gracefully, freeing any allocated memory.  

5. **Error handling**  
   * If the user requests a `room_number` that does not exist, print:  

        ```
        Error: room <room_number> not found.
        ```  

   * If the menu choice is not 1‑4, re‑display the menu.  

## Example Input / Output  

```
Enter number of rooms: 3
Room 101 50 2
Room 102 20 3
Room 103 0 5

--- MENU ---
1) Show details of a specific room
2) Add treasure to a room
3) Show total treasure in the dungeon
4) EXIT
Enter choice: 1
Enter room number: 102
Room 102: Treasure = 20, Danger = 3

--- MENU ---
1) Show details of a specific room
2) Add treasure to a room
3) Show total treasure in the dungeon
4) EXIT
Enter choice: 2
Enter room number: 103
Enter gold to add: 15
Added 15 gold to room 103.

--- MENU ---
1) Show details of a specific room
2) Add treasure to a room
3) Show total treasure in the dungeon
4) EXIT
Enter choice: 3
Total treasure in dungeon: 85

--- MENU ---
1) Show details of a specific room
2) Add treasure to a room
3) Show total treasure in the dungeon
4) EXIT
Enter choice: 4
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity **must** be represented by a `struct` named `Room`.  
2. **Function requirement** – The logic that prints the details of **one** specific room **must** be placed in a function with the exact prototype:  

   ```c
   void displayRoom(const Room *r);
   ```  

3. **Pointer arithmetic only** – All traversals of the `Room` array (searching, summing, updating) must be performed with pointer arithmetic (`*p`, `p++`, `p + i`, etc.). **Array indexing (`[]`) is not allowed** anywhere except for the single allocation line (`malloc(N * sizeof(Room))`).  
4. **Menu exit** – The menu **must** include an option labelled `4) EXIT` (or the exact keyword “EXIT”) that terminates the program.  

Feel free to add any auxiliary helper functions you need, but the three constraints above are mandatory.

---

## Problem 82 - openai/gpt-oss-120b - Iteration 12
# STEP 1: PROBLEM  

## Background  
The university’s Computer Lab wants a tiny “inventory” program to keep track of **lab computers**.  
Each computer has a **serial number** (integer), a **CPU speed** in GHz (float), and a **status flag** indicating whether the machine is **available** (`1`) or **in use** (`0`).  

You have just finished the lecture on pointers and pointer arithmetic. Your task is to write a C program that stores a collection of these computers in a **dynamically‑allocated array**, lets the user manipulate the collection through a menu, and performs all traversals **only with pointer arithmetic** (no array indexing `[]`).  

## Requirements  

1. **Data representation**  
   * Define a `struct Computer` that holds the three fields described above.  

2. **Dynamic storage**  
   * At program start, ask the user for the maximum number of computers `MAX`.  
   * Allocate a contiguous block of memory large enough to hold `MAX` `struct Computer` objects using `malloc`.  

3. **Menu‑driven interface** (the program must present a menu and repeat until the user chooses to exit)  
   * **1 – Add a computer**  
     * Prompt for serial number, CPU speed, and status.  
     * Store the new computer at the first free slot (use a pointer that walks the array with pointer arithmetic).  
     * If the array is full, display an error message.  
   * **2 – List all computers**  
     * Walk the array with a pointer and print each stored computer on its own line.  
   * **3 – Find a computer by serial number**  
     * Prompt for a serial number, search the array using pointer arithmetic, and if found call the function `displayEntity` (see constraints) to show its details; otherwise print “Not found”.  
   * **4 – Remove a computer by serial number**  
     * Prompt for a serial number, locate the matching element, shift all subsequent elements **left** using pointer arithmetic so that the array remains compact, and decrease the logical count.  
   * **5 – EXIT** – terminate the program (free the allocated memory first).  

4. **Program flow**  
   * After each operation (except EXIT) the menu should be shown again.  
   * All input should be read from `stdin`; all output to `stdout`.  

## Example Input / Output  

```
Enter maximum number of computers: 3

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 1
Enter serial number: 1001
Enter CPU speed (GHz): 3.2
Enter status (1=available, 0=in use): 1
Computer added.

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 1
Enter serial number: 1002
Enter CPU speed (GHz): 2.8
Enter status (1=available, 0=in use): 0
Computer added.

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 2
Serial: 1001 | CPU: 3.20 GHz | Status: AVAILABLE
Serial: 1002 | CPU: 2.80 GHz | Status: IN USE

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 3
Enter serial number to find: 1002
Serial: 1002 | CPU: 2.80 GHz | Status: IN USE

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 4
Enter serial number to remove: 1001
Computer removed.

--- Lab Computer Manager ---
1) Add a computer
2) List all computers
3) Find a computer by serial number
4) Remove a computer by serial number
5) EXIT
Choose an option: 5
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Computer`.  
* **Function requirement** – The logic for displaying the details of **ONE specific computer** must be placed in a function with the exact prototype:  

  ```c
  void displayEntity(const struct Computer *c);
  ```  

* **Pointer arithmetic only** – All traversals, searches, insertions, and deletions must use pointer arithmetic (`*ptr`, `ptr++`, `ptr + n`, etc.). **Do not use the subscript operator `[]` anywhere in the program**.  
* **Single‑function restriction** – Apart from `main()` and `displayEntity()`, you may not create additional functions. (All menu handling, allocation, and manipulation must be inside `main`.)  
* **Menu exit option** – The menu must contain an explicit option `5) EXIT` (or the keyword `EXIT`) that terminates the program.  

---  

*Design the program so that a student who has just learned pointers and pointer arithmetic can implement it while respecting all the constraints above.*

---

## Problem 83 - openai/gpt-oss-120b - Iteration 13
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is stored as a record that contains the book’s **ISBN**, **title**, and **number of copies available**. The library wants a small C program that lets a user:

1. Add new books to the inventory.  
2. Update the number of copies for an existing book.  
3. Print the details of a specific book.  
4. List all books currently stored.  

The program must manage the array of book records **using only pointers and pointer arithmetic** (no array indexing `[]`). This will give students practice with pointer manipulation, `malloc`/`free`, and the relationship between pointers and structures.

## Requirements  

1. **Data structure**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating `\0`  
     - `char title[64];`  
     - `int copies;`  

2. **Dynamic storage**  
   * The program should allocate memory for an array of `struct Book` objects using `malloc`.  
   * The initial capacity is **5** books. When the array becomes full, double its capacity with `realloc`.  

3. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | Add a new book |
   | 2 | Update copies of an existing book (search by ISBN) |
   | 3 | Display details of ONE specific book (search by ISBN) |
   | 4 | List all books |
   | 5 | **EXIT** the program |

4. **Functionality**  

   * **Add a new book** – Prompt for ISBN, title, and copies; store the record at the first free slot.  
   * **Update copies** – Prompt for ISBN; if the book exists, ask for the new copy count and update the `copies` field.  
   * **Display ONE book** – Prompt for ISBN; if found, call a helper function `displayBook` (see constraints) to print the book’s information.  
   * **List all books** – Iterate through the array and print each book’s details (use `displayBook` for each entry).  

5. **Memory management** – Before exiting, free any dynamically allocated memory.

## Example Input / Output  

```
=== Library Inventory ===
1. Add a new book
2. Update copies of a book
3. Display a book
4. List all books
5. EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter copies: 3
Book added successfully!

=== Library Inventory ===
1. Add a new book
2. Update copies of a book
3. Display a book
4. List all books
5. EXIT
Choose an option: 3

Enter ISBN to display: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Copies: 3

=== Library Inventory ===
1. Add a new book
2. Update copies of a book
3. Display a book
4. List all books
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be represented by the `struct Book` defined above.  
* **Pointer arithmetic only** – When traversing or accessing the dynamic array, you may **only** use pointers (`*`, `->`, `+`, `-`) and **must not** use the subscript operator `[]`.  
* **Helper function** – The logic for displaying the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```

  `displayBook` should print the ISBN, title, and copies exactly as shown in the example.  

* **Menu exit option** – The menu must include option **5** (or the keyword `EXIT`) that terminates the program.  

* **Single‑file program** – All code must reside in one source file (`.c`). Apart from `main`, you may create additional functions, but the only required extra function is `displayBook`.  

* **Standard library only** – You may use `<stdio.h>`, `<stdlib.h>`, and `<string.h>`. No other libraries are permitted.  

---

## Problem 84 - openai/gpt-oss-120b - Iteration 14
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Department maintains a small inventory of laboratory equipment (e.g., oscilloscopes, multimeters, power supplies). Each item is identified by a **serial number**, has a **type name**, and a **quantity** indicating how many of that item are currently available.  

You have been asked to write a C program that stores this inventory in a dynamically‑allocated array and lets the user query the inventory by serial number. The goal of the assignment is to practice **pointers**, **pointer arithmetic**, and basic **dynamic memory management**.

## Requirements  

1. **Data representation**  
   * Define a `struct Equipment` that contains:  
     ```c
     int serial;          // unique serial number (positive integer)
     char type[32];       // null‑terminated string describing the equipment type
     int quantity;        // number of units in stock (non‑negative)
     ```  

2. **Reading the inventory**  
   * At program start, read an integer `N` (1 ≤ N ≤ 100) – the number of equipment records.  
   * Allocate memory for an array of `N` `Equipment` structs using `malloc`.  
   * Read the next `N` lines, each containing: `serial type quantity` (separated by whitespace).  
   * Store each record in the allocated array.

3. **Query loop**  
   * Repeatedly present a menu:  
     ```
     1) Find equipment by serial number
     2) List all equipment
     3) Exit
     ```  
   * The user selects an option by entering the corresponding number.  

   * **Option 1** – Prompt for a serial number, search the array using **pointer arithmetic only** (no array indexing `[]`). If the serial number exists, call a function `displayEquipment` (see Constraint) to print the record; otherwise print `Serial not found.`  

   * **Option 2** – Iterate through the array (again using only pointer arithmetic) and print every record, one per line, using `displayEquipment`.  

   * **Option 3** – Terminate the program after freeing all dynamically allocated memory.

4. **Output format**  
   * The `displayEquipment` function must output a single record in the exact format:  
     ```
     Serial: <serial>, Type: <type>, Quantity: <quantity>
     ```
   * For the *list all* option, each record appears on its own line in the order they were read.

5. **Error handling**  
   * If the user enters an invalid menu choice, print `Invalid option.` and redisplay the menu.  

## Example Input / Output  

```
Enter number of equipment records: 3
101 Oscilloscope 5
202 Multimeter 12
303 PowerSupply 3

--- Menu ---
1) Find equipment by serial number
2) List all equipment
3) Exit
Choice: 1
Enter serial number to search: 202
Serial: 202, Type: Multimeter, Quantity: 12

--- Menu ---
1) Find equipment by serial number
2) List all equipment
3) Exit
Choice: 2
Serial: 101, Type: Oscilloscope, Quantity: 5
Serial: 202, Type: Multimeter, Quantity: 12
Serial: 303, Type: PowerSupply, Quantity: 3

--- Menu ---
1) Find equipment by serial number
2) List all equipment
3) Exit
Choice: 3
```

*(Program exits after freeing memory.)*

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Equipment` as described.  
2. **Display function** – The logic for printing the details of **ONE** equipment record must be placed in a separate function with the exact prototype:  
   ```c
   void displayEquipment(const struct Equipment *e);
   ```  
3. **Pointer arithmetic only** – When traversing or searching the dynamically allocated array, you may **not** use the subscript operator `[]`. All navigation must be performed with pointers (`ptr`, `ptr + i`, `ptr++`, etc.).  
4. **Menu requirement** – If a menu is implemented (as required), the menu must include an explicit option to **EXIT** the program (option 3 in the example).  

*All other aspects of the program (e.g., variable names, additional helper functions) are left to the student’s discretion.*

---

## Problem 85 - openai/gpt-oss-120b - Iteration 15
# STEP 1: PROBLEM  

## Background  
The campus library has just been upgraded with a new **Automated Shelf Management System**.  Each book on a shelf is represented by a C `struct` that stores the book’s ISBN (a 13‑digit integer), the number of copies currently on the shelf, and a pointer to the next book on the same shelf (forming a singly‑linked list).  

Your task is to write a small program that lets a librarian **navigate the shelves using only pointer arithmetic** (no array indexing) and perform basic queries.  The program will be exercised with a pre‑populated list of books; you do **not** have to implement dynamic insertion or deletion – only traversal and reporting.

## Requirements  

1. **Data representation**  
   * Define a `struct Book` containing:  
     ```c
     unsigned long long isbn;   // 13‑digit ISBN
     int copies;                // number of copies on the shelf
     struct Book *next;         // pointer to next book (NULL for end of shelf)
     ```  
   * The program will be given a pointer `head` that points to the first `Book` in the list.  

2. **Menu‑driven interface** (the menu must be presented repeatedly until the user chooses to exit)  
   * **1. Show first book** – display the details of the book pointed to by `head`.  
   * **2. Show last book** – traverse the list using only pointer arithmetic to locate the final node and display its details.  
   * **3. Show book at position *k*** – the user enters a positive integer `k` (1‑based).  Starting from `head`, move `k‑1` steps forward using pointer arithmetic and display that book’s details. If `k` exceeds the length of the list, print an error message.  
   * **4. Show total copies on the shelf** – compute the sum of the `copies` field for all books by traversing the list with pointers only, then print the total.  
   * **5. EXIT** – terminate the program.  

3. **Output format**  
   * For any “show” operation, print the book’s data on a single line as:  
     ```
     ISBN: <isbn>, Copies: <copies>
     ```  
   * For the total‑copies operation, print:  
     ```
     Total copies on shelf: <sum>
     ```  
   * For an invalid position, print:  
     ```
     Error: position out of range.
     ```

4. **Implementation rules**  
   * **All traversal must be performed with pointer arithmetic only** – you may not use array subscripting (`[]`) or integer indexing on the list.  
   * The logic that prints a single book’s details **must be placed in a separate function** named `displayBook` that receives a pointer to a `Book`.  
   * Apart from `main`, you may create additional helper functions, but the core traversal for each menu option must be written directly in the corresponding case block (i.e., do not delegate the whole traversal to another helper).  

## Example Interaction  

```
--- Library Shelf Manager ---
1. Show first book
2. Show last book
3. Show book at position k
4. Show total copies on the shelf
5. EXIT
Enter choice: 1
ISBN: 9780306406157, Copies: 4

--- Library Shelf Manager ---
1. Show first book
2. Show last book
3. Show book at position k
4. Show total copies on the shelf
5. EXIT
Enter choice: 3
Enter position k: 2
ISBN: 9780131103627, Copies: 2

--- Library Shelf Manager ---
1. Show first book
2. Show last book
3. Show book at position k
4. Show total copies on the shelf
5. EXIT
Enter choice: 4
Total copies on shelf: 11

--- Library Shelf Manager ---
1. Show first book
2. Show last book
3. Show book at position k
4. Show total copies on the shelf
5. EXIT
Enter choice: 5
Goodbye!
```

*(Assume the pre‑populated list contains three books with the shown ISBNs and copy counts.)*  

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be a `struct Book` as described.  
2. **Display function** – The details of a single book must be printed by a function named `displayBook(Book *b)`.  
3. **Menu requirement** – The menu must include an explicit option **5. EXIT** that terminates the program.  
4. **Pointer‑only traversal** – No array indexing (`[]`) or integer‑based access to list elements; only `ptr = ptr->next` (or equivalent pointer arithmetic) may be used to move through the list.  

Design the problem so that students can practice pointer dereferencing, linked‑list traversal, and modular code organization.

---

## Problem 86 - openai/gpt-oss-120b - Iteration 16
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is stored as a record containing the title, the number of copies available, and a unique integer ID. The library wants a simple command‑line utility that lets a librarian **add**, **list**, and **search** for books. Because the system will later be expanded to handle thousands of entries, the assignment focuses on using **pointers** and **pointer arithmetic** to manage a dynamically allocated array of book records.

## Requirements  

Write a C program that:

1. **Defines** a `struct Book` with the following fields:  
   * `int id;` – unique identifier (positive integer)  
   * `char title[51];` – null‑terminated string, maximum 50 characters  
   * `int copies;` – number of copies currently in the library (non‑negative)

2. **Allocates** an array of `struct Book` on the heap. The initial capacity is 5 books; if the librarian adds more than the current capacity, the program must **reallocate** the array to double its previous size using `realloc`.

3. **Provides a menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
   1. **Add a new book** – prompt for `id`, `title`, and `copies`. If a book with the same `id` already exists, display an error and do not add a duplicate.  
   2. **List all books** – display each book’s `id`, `title`, and `copies` on a separate line.  
   3. **Search by ID** – prompt for an `id` and display the matching book’s details, or a “not found” message.  
   4. **EXIT** – terminate the program gracefully, freeing all allocated memory.

4. **Uses pointer arithmetic** (e.g., `*(books + i)`, `books + i`) instead of array indexing (`books[i]`) for **all** traversals and element accesses.

5. **Implements** the logic for displaying a single book’s details in a separate function named `void displayBook(const struct Book *b);`. This function must be called whenever a single book’s information needs to be printed (options 2 and 3).

6. **Handles invalid input** gracefully (e.g., non‑numeric menu choices, negative numbers for copies, etc.) without crashing.

## Example Interaction  

```
=== Library Inventory System ===
1. Add a new book
2. List all books
3. Search by ID
4. EXIT
Choose an option: 1

Enter book ID: 101
Enter title (max 50 chars): The C Programming Language
Enter number of copies: 3
Book added successfully!

=== Library Inventory System ===
1. Add a new book
2. List all books
3. Search by ID
4. EXIT
Choose an option: 1

Enter book ID: 102
Enter title (max 50 chars): Algorithms Unlocked
Enter number of copies: 5
Book added successfully!

=== Library Inventory System ===
1. Add a new book
2. List all books
3. Search by ID
4. EXIT
Choose an option: 2

ID: 101 | Title: The C Programming Language | Copies: 3
ID: 102 | Title: Algorithms Unlocked          | Copies: 5

=== Library Inventory System ===
1. Add a new book
2. List all books
3. Search by ID
4. EXIT
Choose an option: 3

Enter ID to search: 101
ID: 101 | Title: The C Programming Language | Copies: 3

=== Library Inventory System ===
1. Add a new book
2. List all books
3. Search by ID
4. EXIT
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented with a `struct Book`.  
* The function `displayBook` **must** be used for printing a single book’s details.  
* **All** accesses to the dynamic array of books must be performed with **pointer arithmetic**; using the subscript operator (`[]`) for the array is prohibited.  
* The program must include a menu option **exactly** as shown (`4. EXIT`) to terminate execution.  
* Memory allocated with `malloc`/`realloc` must be freed before the program exits.  

---

## Problem 87 - openai/gpt-oss-120b - Iteration 17
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernising its inventory system. Each book in the collection is identified by a **call‑number** (an integer), has a **title** (a short string), and stores the **number of copies** currently on the shelf.  

The library wants a tiny console program that lets a librarian:

1. Add new books to the inventory.  
2. Look up a book by its call‑number and display its details.  
3. Increase or decrease the number of copies for a given book.  
4. List all books currently stored.  

The assignment is meant to practise **pointers**, **pointer arithmetic**, and the use of **structures** in C (or C++).  

---

## Requirements  

Write a program that:

1. Defines a `struct Book` containing three members:  
   * `int callNumber;`  
   * `char title[51];`   // up to 50 characters plus the terminating `'\0'`  
   * `int copies;`  

2. Stores the collection in a **dynamically allocated array** of `struct Book`.  
   * The array may grow when new books are added (you may use `realloc`).  

3. Presents a **text‑based menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   ```
   1. Add a new book
   2. Display a book by call‑number
   3. Update copies of a book
   4. List all books
   5. EXIT
   ```

4. Implements the following functionality for each menu option:  

   * **Add a new book** – Prompt for call‑number, title, and initial copies.  
     * If a book with the same call‑number already exists, print an error and do **not** add a duplicate.  

   * **Display a book by call‑number** – Prompt for the call‑number, locate the book, and **call a function named `displayBook`** (see constraints) to print its details in the format:  

     ```
     Call Number: 12345
     Title      : The Art of Pointers
     Copies     : 4
     ```

   * **Update copies of a book** – Prompt for the call‑number and the *delta* (positive to add copies, negative to remove).  
     * If the resulting number of copies would become negative, print an error and leave the value unchanged.  

   * **List all books** – Iterate through the array using **pointer arithmetic** (no index variables) and print each book using `displayBook`.  

   * **EXIT** – Terminate the program gracefully, freeing any allocated memory.  

5. Handles all input errors gracefully (e.g., non‑numeric input where a number is expected).  

---

## Example Input / Output  

```
--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 1

Enter call number: 1001
Enter title (max 50 chars): C Programming Basics
Enter number of copies: 3
Book added successfully.

--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 1

Enter call number: 1002
Enter title (max 50 chars): Pointer Adventures
Enter number of copies: 5
Book added successfully.

--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 2

Enter call number to display: 1002
Call Number: 1002
Title      : Pointer Adventures
Copies     : 5

--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 3

Enter call number to update: 1001
Enter change in copies (e.g., -1 to remove, 2 to add): -2
Copies updated. New total: 1

--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 4

Call Number: 1001
Title      : C Programming Basics
Copies     : 1

Call Number: 1002
Title      : Pointer Adventures
Copies     : 5

--- Library Inventory System ---
1. Add a new book
2. Display a book by call-number
3. Update copies of a book
4. List all books
5. EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Book` as described above.  

2. **Display Function** – All printing of a single book’s details must be performed by a **separate function** with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```  

   The function receives a pointer to a `Book` and prints the three fields in the format shown in the example.  

3. **Pointer Arithmetic** – When iterating over the dynamic array (e.g., in the “List all books” option), you **must** use pointer arithmetic (`ptr = ptr + 1;`) rather than array indexing (`array[i]`).  

4. **Single‑responsibility Functions** – Apart from `main`, you may create additional helper functions, but the **only** function that directly prints a book’s information is `displayBook`.  

5. **Menu Exit Option** – The menu **must** include the option numbered **5** labeled `EXIT`. Selecting this option ends the program.  

6. **Memory Management** – All memory allocated with `malloc`/`realloc` must be released before program termination.  

---  

*Deliver a complete, compilable program (C or C++) that satisfies the above specifications.*

---

## Problem 88 - openai/gpt-oss-120b - Iteration 18
# STEP 1: PROBLEM  

## Background  
The kingdom’s archivist has just digitised the royal treasure register.  
Each entry in the register records the **name** of a treasure, its **value** in gold coins, and the **room number** where it is kept.  
Your task is to write a small C program that lets a user explore this register.  
The program must manipulate the data **exclusively with pointers and pointer arithmetic** – no array‑subscript (`[]`) notation is allowed.

## Requirements  

1. **Data representation**  
   * Define a `struct Treasure` containing three fields:  
     ```c
     char name[32];   // null‑terminated string, max 31 chars
     int  value;      // in gold coins
     int  room;       // room number in the palace
     ```  
   * The program should contain a **static array** of exactly **7** `Treasure` objects, pre‑initialised with any data you like.

2. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Action |
   |--------|--------|
   | 1      | **List all treasures** – print each treasure on its own line (name, value, room). |
   | 2      | **Show the most valuable treasure** – locate the treasure with the highest `value` and display it. |
   | 3      | **Display a treasure by index** – ask the user for an index `i` (0‑based) and show the `i`‑th treasure. If the index is out of range, print an error message. |
   | 4      | **EXIT** – terminate the program. *(The exit option **must** be option 4.)* |

3. **Pointer usage**  
   * All traversals of the treasure array must be performed with a pointer that is incremented/decremented using pointer arithmetic (`ptr++`, `ptr + n`, etc.).  
   * Direct indexing (`treasures[i]`) is **not** allowed anywhere in the code except when initializing the static array.

4. **Function requirement**  
   * Implement a function `void displayTreasure(const struct Treasure *t)` that prints a single treasure in the format:  
     ```
     Name: <name>, Value: <value> gold, Room: <room>
     ```
   * All menu actions that need to show a treasure must call `displayTreasure`.

5. **User interaction**  
   * After completing any menu action (except EXIT), the program should redisplay the menu and wait for the next choice.  
   * Input may be assumed to be well‑formed integers.

## Example Input / Output  

```
=== Royal Treasure Register ===
1) List all treasures
2) Show most valuable treasure
3) Display treasure by index
4) EXIT
Enter choice: 1

Name: Golden Crown, Value: 1500 gold, Room: 101
Name: Emerald Scepter, Value: 2300 gold, Room: 102
Name: Sapphire Chalice, Value: 1800 gold, Room: 103
Name: Ruby Necklace, Value: 2100 gold, Room: 104
Name: Silver Sword, Value: 900 gold, Room: 105
Name: Ivory Statue, Value: 1200 gold, Room: 106
Name: Bronze Shield, Value: 750 gold, Room: 107

=== Royal Treasure Register ===
1) List all treasures
2) Show most valuable treasure
3) Display treasure by index
4) EXIT
Enter choice: 2

Most valuable treasure:
Name: Emerald Scepter, Value: 2300 gold, Room: 102

=== Royal Treasure Register ===
1) List all treasures
2) Show most valuable treasure
3) Display treasure by index
4) EXIT
Enter choice: 3
Enter index (0‑6): 4

Name: Silver Sword, Value: 900 gold, Room: 105

=== Royal Treasure Register ===
1) List all treasures
2) Show most valuable treasure
3) Display treasure by index
4) EXIT
Enter choice: 4
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be a `struct Treasure`.  
* **Function name** – The routine that prints a single treasure must be exactly `displayTreasure`.  
* **Pointer arithmetic only** – No use of the subscript operator `[]` for accessing the array after its definition.  
* **Menu requirement** – The menu must contain the four options listed above, with option **4** being the explicit “EXIT” command.  

*Optional (for extra credit)*: implement the search for the most valuable treasure using a single pass pointer loop without auxiliary index variables.  

---

## Problem 89 - openai/gpt-oss-120b - Iteration 19
# STEP 1: PROBLEM  

## Background  
The university’s campus library maintains a tiny “in‑memory” catalogue of books.  
Each book record stores the book’s **ISBN**, **title**, **author**, and **number of copies**.  
The catalogue is kept in a dynamically allocated array of `struct Book`.  
Because the array size can change at run‑time, you must use pointers and pointer arithmetic to navigate the records.

Your task is to write a small menu‑driven program that lets a user **add**, **search**, **list**, and **remove** books from this catalogue. All operations must be performed by manipulating pointers directly (no array indexing `[]`).

## Requirements  

1. **Data structure**  
   * Define a `struct Book` containing:  
     ```c
     char isbn[14];      // 13‑digit ISBN + terminating '\0'
     char title[51];     // up to 50 characters + '\0'
     char author[51];    // up to 50 characters + '\0'
     int  copies;        // number of copies available
     ```  

2. **Menu** (displayed repeatedly until the user chooses to exit)  

   | Option | Description                              |
   |--------|------------------------------------------|
   | 1      | **Add a new book** – prompt for all fields and append the record to the end of the array (reallocate as needed). |
   | 2      | **Search by ISBN** – ask for an ISBN, locate the matching book using pointer arithmetic, and display its details. |
   | 3      | **List all books** – traverse the array with a pointer and print each record. |
   | 4      | **Remove a book** – ask for an ISBN, delete the matching record, shift subsequent records left (again using pointers), and shrink the array. |
   | 5      | **EXIT** – terminate the program.        |

3. **Memory management**  
   * The array must be created with `malloc` (or `calloc`) and resized with `realloc`.  
   * When the program ends, free all allocated memory.

4. **Pointer usage**  
   * **Never** use the subscript operator `[]` to access the array elements; always use a pointer variable and advance it with `ptr = ptr + 1` (or `ptr++`).  
   * The same rule applies when scanning the array for search, list, or removal.

5. **User interaction**  
   * All prompts and messages should be clear and user‑friendly.  
   * If an ISBN is not found for search or removal, display an appropriate message.

## Example Input / Output  

```
===== Library Catalogue =====
1) Add a new book
2) Search by ISBN
3) List all books
4) Remove a book
5) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter copies: 3
Book added successfully!

===== Library Catalogue =====
1) Add a new book
2) Search by ISBN
3) List all books
4) Remove a book
5) EXIT
Choose an option: 3

--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 3
--- End of List ---

===== Library Catalogue =====
1) Add a new book
2) Search by ISBN
3) List all books
4) Remove a book
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct requirement** – The primary data entity must be represented by a `struct Book` as described above.  
2. **Display function** – The logic that prints the details of a *single* book must be placed in a function with the exact prototype:  
   ```c
   void displayBook(const struct Book *b);
   ```  
3. **Single helper function** – Apart from `main` and `displayBook`, you may create at most **one** additional user‑defined function (e.g., for searching).  
4. **Menu exit** – The menu must contain the option **5) EXIT** (or the keyword `EXIT`) that cleanly terminates the program.  
5. **No array indexing** – All accesses to the dynamic array of books must be performed via pointer arithmetic; the `[]` operator is prohibited for this array.  

Write a program that satisfies all of the above specifications.

---

## Problem 90 - openai/gpt-oss-120b - Iteration 20
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its catalogue system. Each book in the collection is stored as a record that contains the title, the author’s name, the year of publication, and the number of copies currently on the shelf. The library wants a small console program that lets a librarian **navigate the array of books using only pointers and pointer arithmetic** (no array indexing `[]`).  

## Requirements  
Write a C program that performs the following tasks:

1. **Data Definition**  
   * Define a `struct Book` that holds:
     - `char title[51];`   (maximum 50 characters + terminating null)  
     - `char author[51];`  
     - `int  year;`  
     - `int  copies;`  

2. **Initialisation**  
   * In `main`, create an array of **exactly five** `struct Book` objects and initialise them with data of your choice.

3. **Menu‑Driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1 – List all books** – Print the details of every book in the catalogue.  
   * **2 – Find a book by title** – Prompt the user for a title (case‑sensitive, full match). Search the array using only pointer arithmetic; if found, display the book’s details, otherwise print “Book not found.”  
   * **3 – Update copies** – Prompt for a title and a new integer value for `copies`. Locate the book (again using only pointers) and modify its `copies` field. Confirm the update with a message.  
   * **4 – EXIT** – Terminate the program.  

4. **Display Function**  
   * Implement a function `void displayBook(const struct Book *b);` that receives a pointer to a `Book` and prints its fields in a readable format. This function must be used for every display operation (listing, searching, confirming an update).

5. **Pointer‑Only Traversal**  
   * **Never** use the subscript operator `[]` to access elements of the book array. All navigation must be done with a pointer variable that is incremented/decremented using `+` or `-` (or `++`/`--`).  

## Example Input / Output  

```
--- Library Catalogue ---
1. List all books
2. Find a book by title
3. Update copies
4. EXIT
Choose an option: 1

Title : The C Programming Language
Author: Brian Kernighan
Year  : 1978
Copies: 3

Title : Clean Code
Author: Robert Martin
Year  : 2008
Copies: 5

... (three more books displayed) ...

--- Library Catalogue ---
1. List all books
2. Find a book by title
3. Update copies
4. EXIT
Choose an option: 2
Enter title: Clean Code

Title : Clean Code
Author: Robert Martin
Year  : 2008
Copies: 5

--- Library Catalogue ---
1. List all books
2. Find a book by title
3. Update copies
4. EXIT
Choose an option: 3
Enter title: Clean Code
Enter new number of copies: 7
Copies for "Clean Code" updated to 7.

--- Library Catalogue ---
1. List all books
2. Find a book by title
3. Update copies
4. EXIT
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Display Function** – All printing of a book’s information must be performed by the function `displayBook`.  
* **Pointer Arithmetic Only** – Access to the book array must be performed exclusively with pointers; the `[]` operator is prohibited for any array element access.  
* **Menu Exit Option** – The menu must contain an explicit option (number **4**) labelled **EXIT** that ends the program.  

*Optional extra credit:*  
Implement the search (option 2) using a **binary search** after sorting the array by title (still using only pointer arithmetic).

---

## Problem 91 - openai/gpt-oss-120b - Iteration 21
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library wants a tiny C program that can load a list of books, let the user query a specific ISBN, and then display the information for that book. Because the course has just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of books through pointers rather than using array indexing.

## Requirements  
Write a C program that:

1. **Defines a `struct Book`** containing three members:  
   * `char isbn[14];`   // 13‑digit ISBN plus terminating null character  
   * `char title[51];`  // up to 50 characters plus terminating null character  
   * `int copies;`      // number of copies on the shelf  

2. **Reads the inventory** from standard input:  
   * The first line contains an integer `N` (1 ≤ N ≤ 100), the number of books.  
   * The next `N` lines each contain an ISBN, a title (single‑word or multi‑word, terminated by a newline), and an integer `copies`, separated by a single space.  
   * Example line: `9780131103627 The_C_Programming_Language 4` (underscores may be used to represent spaces in the title for input simplicity).

3. **Prompts the user** to enter an ISBN to look up.  

4. **Searches** the array of `Book` structures for a matching ISBN using **pointer arithmetic only** (no `[]` indexing).  

5. **If a match is found**, calls a function `void displayEntity(const struct Book *b)` that prints the book’s details in the format:  
   ```
   ISBN: <isbn>
   Title: <title>
   Copies: <copies>
   ```  

6. **If no match is found**, prints the line:  
   ```
   Book not found.
   ```

7. The program then terminates.

## Example Input / Output  

**Input (stdin)**  
```
3
9780131103627 The_C_Programming_Language 4
9780201633610 Design_Patterns 2
9780131101630 Introduction_to_Algorithms 5
9780201633610
```

**Output (stdout)**  
```
ISBN: 9780201633610
Title: Design_Patterns
Copies: 2
```

*If the user entered `1234567890123` instead, the output would be:*  
```
Book not found.
```

## Additional Constraints  

### CONSTRAINTS  

* The primary data entity **must be represented with a `struct`** named `Book`.  
* The logic that prints the details of **one specific book** must be placed in a **function called `displayEntity`** with the exact prototype `void displayEntity(const struct Book *b);`.  
* The search for the ISBN **must use pointer arithmetic** (e.g., incrementing a `struct Book *` pointer) and **must not use the array subscript operator (`[]`)**.  
* Apart from `main` and `displayEntity`, no other functions are required (but you may add helper functions if you wish, provided the above constraints are satisfied).  

---  

Write the program so that it compiles with a standard C compiler (C99 or later) and adheres strictly to the constraints above.

---

## Problem 92 - openai/gpt-oss-120b - Iteration 22
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its software to keep track of **book copies** that are currently on loan. Each loan record stores the ISBN of the book, the ID of the borrower, and the number of days remaining until the book must be returned. The library wants a tiny command‑line utility that can store a **fixed‑size array** of loan records, let the user add, remove, and query records, and demonstrate the use of pointers and pointer arithmetic for navigating the array.

## Requirements  

Write a C program that:

1. **Defines** a `struct Loan` containing:
   * `char isbn[14];`   // 13‑character ISBN plus terminating `\0`
   * `int borrowerId;`
   * `int daysLeft;`

2. **Allocates** a static array `Loan loans[MAX]` where `MAX` is a constant (e.g., 20).  
   The program must **manage the array only with pointers** – no array indexing (`loans[i]`) is allowed anywhere except in the initial declaration.

3. Presents a **menu** that repeats until the user chooses to exit:
   1. **Add a loan** – Prompt for ISBN, borrower ID, and days left; store the record in the first free slot.  
   2. **Remove a loan** – Prompt for an ISBN; locate the record and remove it by shifting subsequent records left so that there are no gaps.  
   3. **Display a loan** – Prompt for an ISBN; locate the record and call a function `void displayLoan(const Loan *p)` that prints the three fields in a readable format.  
   4. **List all loans** – Walk through the array with pointer arithmetic and print every stored record (you may reuse `displayLoan`).  
   5. **Exit** – Terminate the program.  

4. **Validates** input where reasonable (e.g., do not add a loan if the array is full; report “Not found” when searching for an ISBN that does not exist).

5. **Uses pointer arithmetic** for all traversals, insertions, deletions, and searches. Direct indexing (`loans[i]`) is prohibited in the functional code.

## Example Interaction  

```
=== Library Loan Manager ===
1) Add a loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 1

Enter ISBN (13 chars): 9780131103627
Enter borrower ID: 1024
Enter days left: 12
Loan added.

=== Library Loan Manager ===
1) Add a loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 4

--- All Active Loans ---
ISBN: 9780131103627 | Borrower ID: 1024 | Days left: 12

=== Library Loan Manager ===
1) Add a loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 3

Enter ISBN to display: 9780131103627
ISBN: 9780131103627 | Borrower ID: 1024 | Days left: 12

=== Library Loan Manager ===
1) Add a loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Loan` as described.  
* **Display Function** – The logic for showing the details of a single loan **must** be placed in a function with the exact prototype:  

  ```c
  void displayLoan(const Loan *p);
  ```

* **Pointer‑Only Traversal** – All operations that walk through the `loans` array (search, insert, delete, list) must use **pointer arithmetic** (`ptr = ptr + 1`, `ptr++`, etc.). The use of the subscript operator `[]` is not allowed outside the initial array declaration.  

* **Menu Exit Option** – The menu must contain an explicit option to **EXIT** the program; in the example it is option `5`. The program must terminate only when the user selects this option.  

* **Single‑File Implementation** – Apart from `main()`, you may define additional helper functions, but the total number of source files must be one (i.e., a single `.c` file).  

* **No Dynamic Allocation** – Use only the static array; `malloc`/`free` are not permitted.  

---

## Problem 93 - openai/gpt-oss-120b - Iteration 23
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library’s junior programmers have been asked to write a small console program that lets a librarian **add**, **search**, and **display** books using only pointer arithmetic (no array indexing `[]`).  

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[51];` // up to 50 characters plus null  
     - `int copies;`  

2. **Program Functionality**  
   * The program maintains a dynamic array of `Book` objects (allocated with `malloc`/`realloc`).  
   * The user interacts through a simple text menu with the following options:  
     1. **Add a new book** – Prompt for ISBN, title, and copies, then store it at the end of the array.  
     2. **Search by ISBN** – Prompt for an ISBN, locate the matching book using pointer arithmetic, and display its details.  
     3. **Display all books** – List every stored book in the order they were added.  
     4. **Exit** – Terminate the program.  

3. **Implementation Rules**  
   * All traversal of the dynamic array must be performed with pointer arithmetic (`ptr`, `ptr + i`, `*(ptr + i)`, etc.). Direct indexing (`array[i]`) is prohibited.  
   * The program must not leak memory; all allocated memory should be freed before exiting.  

4. **User Interaction**  
   * After completing any operation (except Exit), the menu should be shown again.  
   * Input validation is not required beyond ensuring the menu choice is one of the listed options.  

## Example Input / Output  

```
=== Library Inventory Menu ===
1. Add a new book
2. Search by ISBN
3. Display all books
4. Exit
Enter choice: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added successfully!

=== Library Inventory Menu ===
1. Add a new book
2. Search by ISBN
3. Display all books
4. Exit
Enter choice: 2

Enter ISBN to search: 9780131103627
Book found:
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

=== Library Inventory Menu ===
1. Add a new book
2. Search by ISBN
3. Display all books
4. Exit
Enter choice: 3

--- All Books ---
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

=== Library Inventory Menu ===
1. Add a new book
2. Search by ISBN
3. Display all books
4. Exit
Enter choice: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Function Requirement** – The logic for displaying the details of **one specific book** (used by both the search and the “display all” options) must be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Pointer‑Only Traversal** – Inside `displayBook` and any loop that walks through the dynamic array, you must use only pointer arithmetic; the `[]` operator is not allowed.  
* **Menu Exit Option** – The menu must include option **4** (or the keyword “Exit”) that cleanly terminates the program.  

*Optional (but recommended for grading):*  
- Use a separate helper function for adding a book (`addBook`) and for searching (`searchBook`). Each helper must receive a pointer to the dynamic array and its current size.  

---  

*Write the program in C, adhering strictly to the constraints above.*

---

## Problem 94 - openai/gpt-oss-120b - Iteration 24
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Archaeology Exploration Agency (AEA)** to write a small utility that keeps track of discovered treasure chests during an excavation. Each chest has a unique identifier, a weight (in kilograms), and a flag indicating whether it is **sealed** or **opened**. The field agents will enter data for up to **20** chests, and later they may request to view the details of a particular chest.

The agency wants the program to demonstrate proper use of **pointers**, **pointer arithmetic**, and **structures** – concepts you have just learned.

## Program Requirements  

1. **Data Structure**  
   - Define a `struct Chest` that contains:  
     - `int id;`                // unique identifier (positive integer)  
     - `float weight;`          // weight in kilograms (positive)  
     - `int sealed;`            // 1 = sealed, 0 = opened  

2. **Menu‑Driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   - **1. Add a new chest**  
     - Prompt for `id`, `weight`, and `sealed` (enter 1 or 0).  
     - Store the new chest in the next free slot of an array of `struct Chest`.  
     - Do not allow more than 20 chests; display an error if the limit is reached.  
   - **2. Display a chest**  
     - Prompt for a chest `id`.  
     - Locate the chest with that `id` using **pointer arithmetic** (do **not** use array indexing `[]`).  
     - If found, call a function `displayChest` (see constraint) to print its details; otherwise print “Chest not found.”  
   - **3. List all chests**  
     - Iterate through the stored chests using a pointer and pointer arithmetic, printing each chest’s data.  
   - **4. Exit**  
     - Terminate the program gracefully.  

3. **Input Validation**  
   - All numeric inputs must be checked for validity (positive where required, 0/1 for the sealed flag).  
   - If the user enters an invalid choice in the menu, display “Invalid option, try again.” and re‑show the menu.

4. **Output Format**  
   - When displaying a single chest (option 2) or listing all chests (option 3), use the exact format:  

     ```
     Chest ID: <id>
     Weight : <weight> kg
     Status : <"Sealed" or "Opened">
     ```

## Example Interaction  

```
--- Treasure Chest Manager ---
1. Add a new chest
2. Display a chest
3. List all chests
4. Exit
Enter option: 1
Enter chest ID: 101
Enter weight (kg): 12.5
Is the chest sealed? (1=Yes, 0=No): 1
Chest added successfully.

--- Treasure Chest Manager ---
1. Add a new chest
2. Display a chest
3. List all chests
4. Exit
Enter option: 2
Enter chest ID to display: 101

Chest ID: 101
Weight : 12.5 kg
Status : Sealed

--- Treasure Chest Manager ---
1. Add a new chest
2. Display a chest
3. List all chests
4. Exit
Enter option: 4
Goodbye!
```

## ### CONSTRAINTS  

1. **Structure Usage** – The primary data entity must be represented with a `struct Chest`.  
2. **Display Function** – The logic for showing the details of **ONE** specific chest must reside in a function named `void displayChest(const struct Chest *c);`.  
3. **Pointer Arithmetic Only** – When searching for a chest by ID (menu option 2) and when iterating over the array for listing (menu option 3), you must use pointer arithmetic (`ptr = ptr + 1`, `*(ptr + i)`, etc.) and **must not** use the array subscript operator `[]`.  
4. **Menu Requirement** – The program must present a menu and **must include a menu option to EXIT the program** (option 4 in the specification above).  
5. **Single Additional Function** – Apart from `main` and the required `displayChest`, you may not introduce extra functions; all other logic must be placed directly in `main`.  

Design your solution to satisfy all the above requirements and constraints.

---

## Problem 95 - openai/gpt-oss-120b - Iteration 25
# STEP 1: PROBLEM  

## Background  
The university’s Computer Lab maintains a small inventory of **lab workstations**. Each workstation is identified by a unique integer `id`, has a short description (e.g., “Linux‑C Development”), and stores the number of **available USB ports**. The lab manager wants a simple console program that lets a user browse the inventory, add new workstations, and query details of a specific workstation.  

The assignment’s learning goal is to practice **pointers**, **dynamic memory allocation**, and **pointer arithmetic** on an array of structures.

## Requirements  

1. **Data Representation**  
   * Define a `struct Workstation` containing:  
     - `int id;`  
     - `char description[50];`  
     - `int usb_ports;`  

2. **Dynamic Array**  
   * The program must allocate an array of `Workstation` objects on the heap using `malloc` (or `new` if C++ is used).  
   * The size of the array can grow when the user adds a new workstation; re‑allocate the array with `realloc` (or `std::vector` is **not** allowed).  

3. **Menu‑driven Interface** (optional but recommended)  
   * Present a menu with the following options:  
     1. **Add a workstation** – ask for `id`, `description`, and `usb_ports`; store it at the end of the dynamic array.  
     2. **Show a workstation** – ask for an `id` and display the matching workstation’s details.  
     3. **List all workstations** – iterate through the array and print each entry.  
     4. **Exit** – terminate the program.  
   * The “Exit” option must be clearly numbered (e.g., `4`) and documented in the menu.  

4. **Pointer Arithmetic**  
   * All traversals of the workstation array must be performed using pointer arithmetic (e.g., `ptr + i`) rather than array indexing (`array[i]`).  

5. **Function Requirements**  
   * Implement a function `void displayWorkstation(const struct Workstation *ws);` that prints the fields of a single workstation. This function must be used whenever a workstation’s details are shown (both for a single query and while listing all).  

6. **Input Validation**  
   * If the user requests a workstation `id` that does not exist, print an informative message and return to the menu.  

## Example Input / Output  

```
=== Lab Workstation Inventory ===
1) Add a workstation
2) Show a workstation
3) List all workstations
4) Exit
Choose an option: 1

Enter workstation id: 101
Enter description: Linux-C Development
Enter number of USB ports: 4
Workstation added.

=== Lab Workstation Inventory ===
1) Add a workstation
2) Show a workstation
3) List all workstations
4) Exit
Choose an option: 1

Enter workstation id: 202
Enter description: Windows-Testing
Enter number of USB ports: 2
Workstation added.

=== Lab Workstation Inventory ===
1) Add a workstation
2) Show a workstation
3) List all workstations
4) Exit
Choose an option: 2

Enter workstation id to display: 101
--- Workstation Details ---
ID: 101
Description: Linux-C Development
USB Ports: 4

=== Lab Workstation Inventory ===
1) Add a workstation
2) Show a workstation
3) List all workstations
4) Exit
Choose an option: 3

--- All Workstations ---
ID: 101 | Description: Linux-C Development | USB Ports: 4
ID: 202 | Description: Windows-Testing      | USB Ports: 2

=== Lab Workstation Inventory ===
1) Add a workstation
2) Show a workstation
3) List all workstations
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must** be represented by a `struct Workstation`.  
- The function that prints the details of **one** workstation **must** be named `displayWorkstation` and accept a pointer to a `Workstation`.  
- All array traversals **must** use pointer arithmetic; direct indexing (`array[i]`) is prohibited.  
- If a menu is implemented, it **must** include an explicit “Exit” option (number 4 in the example) that terminates the program.  

*Note: The problem is language‑agnostic but assumes a C‑style language (C or C++) where pointers and manual memory management are explicit.*

---

## Problem 96 - openai/gpt-oss-120b - Iteration 26
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is stored in a **struct** that holds the title, the number of copies available, and a unique integer ID. The library wants a small console program that can **add** books, **search** for a book by its ID, and **list** all stored books.  

Because the students have just finished the unit on *pointers and pointer arithmetic*, the implementation must manipulate an array of `Book` structures **only through pointers** – no direct array indexing (`books[i]`) is allowed.

## Requirements  

1. Define a `struct Book` with the following members:  
   * `int id;` – unique identifier (positive integer)  
   * `char title[51];` – null‑terminated string (max 50 characters)  
   * `int copies;` – number of copies currently in the library  

2. In `main()` dynamically allocate an array that can hold up to **20** books.  

3. Implement a **menu‑driven** interface with the following options (the user selects a number):  
   1. **Add a new book** – prompt for `id`, `title`, and `copies`. Store the new record at the first free slot.  
   2. **Find a book by ID** – ask for an `id`, locate the matching record, and display its details.  
   3. **List all books** – display the information for every stored book in the order they were added.  
   4. **Exit** – terminate the program (this option **must** be present).  

4. All traversals of the book array must be performed **using pointer arithmetic** (`ptr`, `ptr+1`, `*(ptr+1)`, etc.). Direct indexing such as `books[i]` is prohibited.  

5. The logic that prints the details of a **single** `Book` must be placed in a function with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```

   This function should be called wherever a single book’s information needs to be shown (options 2 and 3).  

6. The program should gracefully handle the following error conditions:  
   * Trying to add a book when the array is already full.  
   * Searching for an ID that does not exist.  

7. Before exiting, free any dynamically allocated memory.

## Example Interaction  

```
=== Library Inventory ===
1. Add a new book
2. Find a book by ID
3. List all books
4. Exit
Choose an option: 1

Enter book ID: 101
Enter title (max 50 chars): The C Programming Language
Enter number of copies: 3
Book added successfully!

=== Library Inventory ===
1. Add a new book
2. Find a book by ID
3. List all books
4. Exit
Choose an option: 1

Enter book ID: 202
Enter title (max 50 chars): Algorithms Unlocked
Enter number of copies: 5
Book added successfully!

=== Library Inventory ===
1. Add a new book
2. Find a book by ID
3. List all books
4. Exit
Choose an option: 2

Enter ID to search: 202
Book ID: 202
Title : Algorithms Unlocked
Copies: 5

=== Library Inventory ===
1. Add a new book
2. Find a book by ID
3. List all books
4. Exit
Choose an option: 3

Book ID: 101
Title : The C Programming Language
Copies: 3

Book ID: 202
Title : Algorithms Unlocked
Copies: 5

=== Library Inventory ===
1. Add a new book
2. Find a book by ID
3. List all books
4. Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented by a `struct` named `Book`.  
* The function that displays a single book **must** be exactly `void displayBook(const struct Book *b);`.  
* All array traversals and element accesses **must** use pointer arithmetic; direct indexing (`books[i]`) is not allowed.  
* The menu must contain an explicit **Exit** option (option 4 in the example).  
* The program may contain additional helper functions, but the only required user‑visible functions are `main` and `displayBook`.  

---  

*Note: The problem is intentionally designed to reinforce the use of pointers, pointer arithmetic, dynamic memory, and struct handling for students who have just completed the corresponding lecture.*

---

## Problem 97 - openai/gpt-oss-120b - Iteration 27
# STEP 1: PROBLEM  

## Background  
The museum of **ChronoTech** is digitizing its collection of ancient devices. Each device is described by three pieces of information:  

1. **ID** – a unique integer identifier.  
2. **Name** – a short string (max 30 characters).  
3. **Year** – the year the device was created (integer, may be negative for BCE).  

The museum’s software must store the devices in a dynamically‑allocated array and allow the curator to query and modify the collection using pointer arithmetic.  

## Requirements  

Write a C program that performs the following actions:

1. **Read the initial collection**  
   * Prompt the user for the number of devices `N` (1 ≤ N ≤ 100).  
   * Dynamically allocate an array of `N` `struct Device` objects.  
   * For each device, read its `ID`, `Name`, and `Year` from the user.  

2. **Present a menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   1. **Display a device** – ask for an `ID` and print the full information of the matching device.  
   2. **Update a device’s year** – ask for an `ID` and a new `Year`; modify the stored year.  
   3. **List all devices** – print the information of every device in the order they are stored.  
   4. **Exit** – terminate the program.  

3. **Implement pointer arithmetic**  
   * All traversals of the device array (searching, listing, updating) must be performed using pointers and pointer arithmetic only; array indexing (`[]`) is **not** allowed in those parts.  

4. **Memory management**  
   * Before exiting, free any dynamically allocated memory.  

## Example Input / Output  

```
Enter number of devices: 3
Device 1 ID: 101
Device 1 Name: Sun Dial
Device 1 Year: -500
Device 2 ID: 202
Device 2 Name: Astrolabe
Device 2 Year: 900
Device 3 ID: 303
Device 3 Name: Mechanical Clock
Device 3 Year: 1350

--- Museum Device Manager ---
1. Display a device
2. Update a device's year
3. List all devices
4. Exit
Choose an option: 1
Enter device ID: 202
Device ID: 202
Name: Astrolabe
Year: 900

--- Museum Device Manager ---
1. Display a device
2. Update a device's year
3. List all devices
4. Exit
Choose an option: 2
Enter device ID: 101
Enter new year: -480
Year updated.

--- Museum Device Manager ---
1. Display a device
2. Update a device's year
3. List all devices
4. Exit
Choose an option: 3
Device ID: 101, Name: Sun Dial, Year: -480
Device ID: 202, Name: Astrolabe, Year: 900
Device ID: 303, Name: Mechanical Clock, Year: 1350

--- Museum Device Manager ---
1. Display a device
2. Update a device's year
3. List all devices
4. Exit
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be defined as  

   ```c
   struct Device {
       int id;
       char name[31];
       int year;
   };
   ```  

2. **Function requirement** – The logic for displaying the details of **ONE** specific device (option 1) must be placed in a function named  

   ```c
   void displayDevice(const struct Device *dev);
   ```  

3. **Pointer arithmetic only** – When searching for a device by ID, listing all devices, or updating a device’s year, you must use pointers (`struct Device *p`) and pointer arithmetic (`p++`, `p + i`, etc.). Direct array indexing (`devices[i]`) is prohibited in those sections.  

4. **Menu implementation** – The menu must be presented exactly as shown, and option 4 must be the explicit “Exit” command that terminates the loop and ends the program.  

5. **Single‑function restriction** – Apart from `main()` and `displayDevice()`, you may create additional helper functions **only if** they also operate exclusively with pointers (no array indexing).  

---  

*Your task is to design the complete program meeting all the above specifications.*

---

## Problem 98 - openai/gpt-oss-120b - Iteration 28
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Department maintains a small inventory of **lab equipment** (e.g., microscopes, oscilloscopes, 3‑D printers). Each piece of equipment is identified by a unique serial number, has a descriptive name, and a count of how many units are currently available for checkout.  

You have been asked to write a **C** program that lets a user browse the inventory, add new items, and update the quantity of existing items. The program must demonstrate correct use of **pointers** and **pointer arithmetic** to manipulate an array of equipment records stored in dynamic memory.

## Requirements  

1. **Data Representation**  
   - Define a `struct Equipment` containing:  
     ```c
     char name[31];      // up to 30 characters + null terminator
     int  serial;        // unique positive integer
     int  quantity;      // number of units in stock (≥ 0)
     ```  

2. **Dynamic Storage**  
   - At program start, allocate space for **N** equipment records (`N` is a constant you may define, e.g., 10).  
   - Use a pointer to the first element of the array (`struct Equipment *inventory`) and **only** pointer arithmetic (no array indexing `[]`) to traverse or modify the array.

3. **Menu‑Driven Interface**  
   The program must present the user with a menu repeatedly until the user chooses to exit. The menu options are:  

   1. **Add a new equipment record** – Prompt for `serial`, `name`, and `quantity`. Insert the record into the first free slot (where `serial` is 0). If the inventory is full, display an appropriate message.  
   2. **Update quantity of an existing item** – Prompt for a `serial` number and the new `quantity`. Locate the record using pointer arithmetic and modify its `quantity`. If the serial does not exist, inform the user.  
   3. **Display details of ONE specific equipment** – Prompt for a `serial` number and call a function `void displayEntity(const struct Equipment *e)` that prints the name, serial, and quantity. If the serial is not found, print “Equipment not found.”  
   4. **List all equipment** – Walk through the array with pointer arithmetic and print every record whose `serial` is non‑zero.  
   5. **EXIT** – Terminate the program.  

4. **Input Validation**  
   - All numeric inputs must be positive integers.  
   - The `name` may contain spaces; read it with `fgets` or an equivalent safe method.

5. **Memory Management**  
   - Before program termination, free any dynamically allocated memory.

## Example Interaction  

```
=== Lab Equipment Inventory ===
1) Add new equipment
2) Update quantity
3) Display equipment
4) List all equipment
5) EXIT
Choose an option: 1

Enter serial number: 1001
Enter name: 3D Printer
Enter quantity: 2
Equipment added.

=== Lab Equipment Inventory ===
1) Add new equipment
2) Update quantity
3) Display equipment
4) List all equipment
5) EXIT
Choose an option: 3

Enter serial number to display: 1001
--- Equipment Details ---
Name    : 3D Printer
Serial  : 1001
Quantity: 2

=== Lab Equipment Inventory ===
1) Add new equipment
2) Update quantity
3) Display equipment
4) List all equipment
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct Equipment`.  
- **Function Requirement** – The logic for displaying the details of ONE specific entity must be encapsulated in a function named `displayEntity` with the prototype `void displayEntity(const struct Equipment *e);`.  
- **Pointer‑Only Traversal** – All accesses to the `inventory` array must use pointer arithmetic (`*(inventory + i)`, `inventory + i`, etc.). The use of the subscript operator `[]` is prohibited for array traversal or element modification.  
- **Menu Exit Option** – The menu must include an explicit option (number **5**) labelled **EXIT** that terminates the program.  

*Note: The problem is intentionally designed for students who have just learned pointers and pointer arithmetic, so the emphasis is on correct pointer usage, dynamic memory handling, and modular code organization.*

---

## Problem 99 - openai/gpt-oss-120b - Iteration 29
# STEP 1: PROBLEM  

## Background  
The ancient kingdom of **Codeland** stores its priceless artifacts in a line of treasure chests.  
Each chest is identified by a unique **ID** (an integer) and holds a quantity of gold coins (also an integer).  
The royal archivist has asked you to write a small C program that will keep the chests in memory, allow the king to inspect a single chest, and compute the total wealth stored in all chests.  

You have just learned about **pointers** and **pointer arithmetic**, and you must use these concepts to manipulate the dynamically‑allocated array of chests.

## Requirements  

1. **Data representation**  
   * Define a `struct Chest` that contains two members:  
     ```c
     int id;      // chest identifier
     int gold;    // number of gold coins in the chest
     ```
2. **Dynamic allocation**  
   * Prompt the user for the number of chests `N` ( `N > 0` ).  
   * Allocate an array of `N` `Chest` objects on the heap using `malloc`.  
   * Populate the array: for each chest, read its `id` and `gold` from standard input.  
3. **Menu‑driven interface** (the program must present a menu after the data are read)  
   * The menu must contain the following options (the user selects by entering the option number):  
     1. **Display a chest** – ask for a chest `id` and print the `id` and `gold` of the matching chest.  
     2. **Total gold** – compute and print the sum of `gold` values of **all** chests.  
     3. **Exit** – terminate the program.  
   * The menu must repeat after each operation until the user chooses **Exit**.  
4. **Pointer arithmetic usage**  
   * All traversals of the chest array (e.g., searching for an `id`, summing gold) must be performed with pointer arithmetic (`*ptr`, `ptr++`, `ptr + i`, etc.) – **do not** use array indexing (`array[i]`).  
5. **Function requirement**  
   * The logic for displaying the details of ONE specific chest must be placed in a function with the exact prototype:  
     ```c
     void displayChest(const struct Chest *c);
     ```
   * This function receives a pointer to the chest to be displayed and prints the information in the format shown in the example.  

## Example Input / Output  

```
Enter number of chests: 3
Chest 1 - enter id and gold: 101 250
Chest 2 - enter id and gold: 102 400
Chest 3 - enter id and gold: 103 150

--- MENU ---
1) Display a chest
2) Total gold
3) Exit
Choose an option: 1
Enter chest id to display: 102
Chest ID: 102, Gold: 400

--- MENU ---
1) Display a chest
2) Total gold
3) Exit
Choose an option: 2
Total gold in all chests: 800

--- MENU ---
1) Display a chest
2) Total gold
3) Exit
Choose an option: 3
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – the primary data entity must be represented by a `struct Chest`.  
* **Display function** – the details of a single chest must be shown by a function named `displayChest` with the prototype shown above.  
* **Pointer arithmetic only** – you may not use the subscript operator `[]` when accessing the dynamically‑allocated chest array.  
* **Menu requirement** – the program must provide a menu as described, and the menu must include an explicit **Exit** option (option 3 in the example).  

*The problem is intentionally scoped for students who have just completed the “Pointers and Pointer Arithmetic” unit.*

---

## Problem 100 - openai/gpt-oss-120b - Iteration 30
# STEP 1: PROBLEM  

## Background  
The kingdom’s archivist has been tasked with keeping track of a collection of **ancient relics** stored in a series of sealed wooden boxes. Each box contains a single relic, and the archivist wants a small C program that can store information about each relic, allow the user to add new boxes, view the contents of a specific box, and finally clean up all allocated memory before exiting.  

Because the relics are stored in a contiguous block of memory, the archivist insists that the program manipulate the collection **only with pointers and pointer arithmetic** – no array indexing (`[]`) may be used for accessing the relics after the initial allocation.

## Requirements  

1. **Data representation**  
   * Define a `struct Relic` that holds:  
     - `char name[31]` – the name of the relic (max 30 characters, null‑terminated).  
     - `int age` – how many centuries old the relic is.  
   * The collection of relics must be stored in a **dynamically allocated contiguous block** (i.e., a single `malloc`/`realloc` call).  

2. **Menu‑driven interface** (the program must present a text menu and loop until the user chooses to exit). The menu must contain the following options (the numbers are mandatory):  
   1. **Add a new relic** – prompt for the relic’s name and age, enlarge the block if necessary, and store the new relic at the end.  
   2. **Display a relic** – ask for the 0‑based index of the relic to view and print its details. The actual printing must be performed by a function named `void displayRelic(const struct Relic *r)`.  
   3. **List all relics** – iterate through the collection and display each relic using `displayRelic`.  
   4. **EXIT** – terminate the program gracefully, freeing all allocated memory.  

3. **Pointer arithmetic only**  
   * After the initial allocation, **no** array subscript operator (`[]`) may be used to read or write a `Relic`. All accesses must be performed with pointers (`*`, `+`, `-`).  
   * Example: to obtain a pointer to the *i*‑th relic, use `struct Relic *p = basePtr + i;`.  

4. **Robustness**  
   * The program must validate user input for menu choices and indices (e.g., reject negative indices or indices ≥ current count).  
   * If the user requests to display a non‑existent relic, print an appropriate error message and return to the menu.  

5. **Memory management**  
   * Use `realloc` to grow the array when a new relic is added.  
   * Before exiting, free the allocated block exactly once.  

## Example Interaction  

```
=== Relic Archive ===
1. Add a new relic
2. Display a relic
3. List all relics
4. EXIT
Choose an option: 1

Enter relic name: Golden Scepter
Enter relic age (centuries): 12
Relic added successfully!

=== Relic Archive ===
1. Add a new relic
2. Display a relic
3. List all relics
4. EXIT
Choose an option: 1

Enter relic name: Crystal Orb
Enter relic age (centuries): 8
Relic added successfully!

=== Relic Archive ===
1. Add a new relic
2. Display a relic
3. List all relics
4. EXIT
Choose an option: 2

Enter relic index (0‑based): 1
Relic #1:
Name: Crystal Orb
Age: 8 centuries

=== Relic Archive ===
1. Add a new relic
2. Display a relic
3. List all relics
4. EXIT
Choose an option: 3

Relic #0:
Name: Golden Scepter
Age: 12 centuries

Relic #1:
Name: Crystal Orb
Age: 8 centuries

=== Relic Archive ===
1. Add a new relic
2. Display a relic
3. List all relics
4. EXIT
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Relic`.  
2. **Display function** – The logic for printing the details of a single relic must reside in a function with the exact prototype:  
   ```c
   void displayRelic(const struct Relic *r);
   ```  
3. **Pointer‑only access** – After the initial allocation, you may **not** use the subscript operator (`[]`) to read or write any element of the relic collection. All element accesses must be performed with pointer arithmetic.  
4. **Menu requirement** – The program must present a menu as described, and option **4** (or the keyword `EXIT`) must be the explicit way to terminate the program.  

*All other aspects of the implementation (e.g., helper functions, variable names) are left to the student.*

---

