# Problem Batch Preview: Dynamic Memory Allocation (malloc, free)
**Batch Number:** 2 | **Total Problems:** 100

---

## Problem 1 - openai/gpt-oss-120b - Iteration 81
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **CampusConnect**, a small campus‑wide service that keeps a live list of active study‑group sessions. Each session has a **title**, a **maximum number of participants**, and the **current number of participants** that have already joined. The program must allow the user (the campus administrator) to create new sessions, join participants, display session information, and delete sessions that are no longer needed.  

All session records must be stored in **dynamic memory** because the number of sessions is not known at compile time and can change while the program runs.

## Requirements  

Write a C program that implements the following functionality:

1. **Create a new session**  
   * Prompt the user for the session title (a string of up to 50 characters) and the maximum number of participants (positive integer).  
   * Allocate a `struct Session` on the heap with `malloc`.  
   * Initialise the current participant count to 0 and add the new session to the end of a dynamically‑managed list.

2. **Add participants to a session**  
   * Ask the user for the session title and the number of participants to add.  
   * If the session exists and the addition would not exceed the maximum, increment the current participant count.  
   * If the session does not exist or the addition would overflow, print an appropriate error message.

3. **Display a specific session**  
   * Prompt for a session title.  
   * Locate the session and print its title, maximum capacity, and current participant count.  
   * This display logic must be placed in a function named `void displaySession(const struct Session *s);`.

4. **Delete a session**  
   * Prompt for a session title.  
   * If the session exists, remove it from the list, free its memory with `free`, and shift remaining list elements as needed.  
   * If the session does not exist, print an error message.

5. **List all sessions**  
   * Print a table of every session currently stored, showing title, maximum capacity, and current participants.

6. **Exit**  
   * The program must terminate cleanly, freeing any remaining allocated memory before exiting.

The program should repeatedly present a **menu** that lets the user choose one of the actions above until the “Exit” option is selected.

## Example Input / Output  

```
=== CampusConnect Menu ===
1. Create new session
2. Add participants
3. Display a session
4. Delete a session
5. List all sessions
6. Exit
Enter choice: 1
Enter session title: Algorithms Study Group
Enter maximum participants: 12
Session created.

=== CampusConnect Menu ===
1. Create new session
2. Add participants
3. Display a session
4. Delete a session
5. List all sessions
6. Exit
Enter choice: 2
Enter session title: Algorithms Study Group
Enter participants to add: 5
5 participants added.

=== CampusConnect Menu ===
1. Create new session
2. Add participants
3. Display a session
4. Delete a session
5. List all sessions
6. Exit
Enter choice: 3
Enter session title: Algorithms Study Group
--- Session Details ---
Title: Algorithms Study Group
Maximum participants: 12
Current participants: 5

=== CampusConnect Menu ===
1. Create new session
2. Add participants
3. Display a session
4. Delete a session
5. List all sessions
6. Exit
Enter choice: 5
--- All Sessions ---
Title                     Max   Current
Algorithms Study Group    12    5

=== CampusConnect Menu ===
1. Create new session
2. Add participants
3. Display a session
4. Delete a session
5. List all sessions
6. Exit
Enter choice: 6
Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

1. **Data structure** – The primary entity must be represented with a `struct Session` containing at least the fields `char title[51]; int maxParticipants; int currentParticipants;`.  

2. **Display function** – The logic that prints the details of a single session must be encapsulated in a function named `void displaySession(const struct Session *s);`.  

3. **Dynamic allocation** – All sessions must be allocated with `malloc` (or `calloc`) and released with `free`. No static or global arrays of fixed size may be used to store the sessions.  

4. **Menu requirement** – The program must present a menu as shown in the example and **must include an explicit “Exit” option (choice 6)** that terminates the program.  

5. **Memory safety** – Before the program ends, every block of memory obtained via `malloc`/`calloc` must be freed exactly once.  

Feel free to add any helper functions you deem necessary, but the above constraints must be satisfied.

---

## Problem 2 - openai/gpt-oss-120b - Iteration 82
# STEP 1: PROBLEM  

## Background  
You have been hired by the **City Library** to write a small C program that keeps track of the books currently borrowed by patrons. The library does not have a database; instead, it stores the information only while the program is running. Because the number of active loans changes constantly, you must allocate and release memory dynamically using `malloc` and `free`.  

Each loan (a **BorrowRecord**) contains:  

* the patron’s name (a string, up to 50 characters),  
* the title of the book (a string, up to 100 characters),  
* the number of days the book is borrowed (an integer).  

The program should allow the librarian to add new loans, remove a loan when a book is returned, and display the details of a specific loan.

---

## Requirements  

Your program must implement the following functionality:

1. **Add a new loan**  
   * Prompt the user for the patron’s name, book title, and number of days.  
   * Dynamically allocate a `BorrowRecord` and store the entered data.  
   * Store the pointer in a dynamically‑growing array (you may re‑allocate the array each time a new record is added).

2. **Return a loan (remove a record)**  
   * Ask the user for the patron’s name and the book title.  
   * Search the array for a matching record (both fields must match exactly).  
   * If found, free the memory used by that `BorrowRecord`, remove its pointer from the array, and shrink the array accordingly.  
   * If not found, print “Record not found.”

3. **Display a specific loan**  
   * Ask the user for the patron’s name and the book title.  
   * Locate the matching record and call a function `displayRecord` (see constraints) to print the three fields in a readable format.  
   * If the record does not exist, print “Record not found.”

4. **List all active loans**  
   * Iterate over the array and print every stored loan using `displayRecord`.

5. **Exit**  
   * Before terminating, free **all** memory that was allocated (both the individual `BorrowRecord`s and the array that holds their pointers).

The program should present a simple text menu that repeatedly asks the user to choose an option until the *Exit* option is selected.

---

## Example Interaction  

```
=== Library Loan Manager ===
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
5. Exit
Choose an option: 1

Patron name: Alice Johnson
Book title : The C Programming Language
Days borrowed: 14
Loan added successfully.

=== Library Loan Manager ===
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
5. Exit
Choose an option: 4

--- Active Loans ---
Patron: Alice Johnson
Book  : The C Programming Language
Days  : 14
--------------------

=== Library Loan Manager ===
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
5. Exit
Choose an option: 5

Goodbye!
```

---

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct` named `BorrowRecord`.  
* **Display Function** – The logic for printing the details of a single loan must be placed in a function with the exact prototype:  

  ```c
  void displayRecord(const BorrowRecord *rec);
  ```

* **Menu Requirement** – The program must present a menu as shown in the example.  
  * The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option terminates the loop and triggers the final cleanup.  

* **Dynamic Allocation Only** – All storage for loan records and the array of pointers must be obtained with `malloc`/`calloc`/`realloc` and released with `free`. No static or global arrays of fixed size are allowed for storing the records.  

* **Single‑File Implementation** – All code must reside in one source file (`.c`). Apart from `main`, you may create additional helper functions, but the only required extra function is `displayRecord`.  

* **Error Handling** – If any `malloc`/`realloc` call fails, the program should print an error message and exit gracefully, freeing any memory that was already allocated.  

---

## Problem 3 - openai/gpt-oss-120b - Iteration 83
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “personal library” manager for a small community reading club.  
The club wants a console program that can keep track of the books currently owned by the club.  
Because the number of books is not known in advance and can change while the program runs, the
data for each book must be allocated dynamically on the heap using `malloc` (or `calloc`) and released
with `free` when the book is removed or when the program terminates.

## Requirements  

Write a C program that provides the following functionality through a simple text‑based menu:

1. **Add a new book**  
   * Prompt the user for the book’s **ISBN** (a positive integer), **title** (a single line, up to 100 characters), and **author** (a single line, up to 100 characters).  
   * Dynamically allocate a `struct Book` to store the information and insert it into an internal list.  
   * If a book with the same ISBN already exists, print an error message and do **not** add a duplicate.

2. **Delete a book**  
   * Prompt for an ISBN.  
   * Locate the matching book, remove it from the list, and free the memory that was allocated for it.  
   * If the ISBN is not found, print a suitable message.

3. **Display details of ONE specific book**  
   * Prompt for an ISBN.  
   * Locate the book and **call a function named `displayBook`** to print its details in the format:  
     ```
     ISBN: <isbn>
     Title: <title>
     Author: <author>
     ```  
   * If the ISBN does not exist, print a suitable message.

4. **List all books**  
   * Print the details of every book currently stored, using `displayBook` for each entry.  
   * If the list is empty, print “No books in the library.”

5. **Exit**  
   * Choose the menu option to terminate the program.  
   * Before exiting, free **all** memory that was allocated for books.

The program should continue to display the menu after each operation until the user selects the
exit option.

## Example Interaction  

```
=== Library Manager ===
1. Add a book
2. Delete a book
3. Show a book
4. List all books
0. Exit
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added.

=== Library Manager ===
1. Add a book
2. Delete a book
3. Show a book
4. List all books
0. Exit
Enter choice: 1
Enter ISBN: 9780201633610
Enter title: Design Patterns
Enter author: Gamma et al.
Book added.

=== Library Manager ===
1. Add a book
2. Delete a book
3. Show a book
4. List all books
0. Exit
Enter choice: 3
Enter ISBN to display: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Library Manager ===
1. Add a book
2. Delete a book
3. Show a book
4. List all books
0. Exit
Enter choice: 4
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

ISBN: 9780201633610
Title: Design Patterns
Author: Gamma et al.

=== Library Manager ===
1. Add a book
2. Delete a book
3. Show a book
4. List all books
0. Exit
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Data structure** – The primary entity must be represented by a `struct` named `Book` containing at least the fields `int isbn; char title[101]; char author[101];` and a pointer to the next `Book` (i.e., a singly‑linked list).  
* **Dynamic allocation** – Every time a new book is added, allocate memory with `malloc`/`calloc`.  
  Every removal must free the exact block that was allocated for that book.  
* **Function requirement** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Menu** – The program must present a menu as shown above and **must** include the option `0` (or the word `EXIT`) that terminates the program. Selecting this option must cause the program to free all remaining allocated memory before exiting.  

* **Single‑source file** – The entire solution should be written in one `.c` file; you may define helper functions, but the `main` function must contain the menu loop.  

* **No global variables** – All data structures should be created and manipulated via pointers passed to functions; avoid using global variables for the book list.  

---  

*Note to students*: Focus on correct use of `malloc`, `free`, pointer manipulation, and keeping the program free of memory leaks. Use tools such as `valgrind` (or your IDE’s memory‑checking facilities) to verify that every allocated block is released.

---

## Problem 4 - openai/gpt-oss-120b - Iteration 84
# STEP 1: PROBLEM  

## Background  
The city museum is digitizing its collection of artifacts. Each artifact has a name, a year of origin, and a short description. The museum’s software must be able to **create**, **store**, **display**, and **remove** artifacts while the program is running. Because the number of artifacts is not known ahead of time, the program must allocate memory dynamically using `malloc`/`calloc` and release it with `free` when an artifact is deleted or when the program terminates.

## Requirements  

Write a C program that implements a simple **menu‑driven** artifact manager. The program must support the following operations:

1. **Add a new artifact**  
   - Prompt the user for the artifact’s *name* (string, max 50 characters), *year* (integer), and *description* (string, max 200 characters).  
   - Allocate memory for a new `struct Artifact` and store the entered data.  
   - Append the new artifact to the end of the current collection.

2. **Delete an artifact**  
   - Prompt the user for the *index* (1‑based) of the artifact to delete.  
   - Remove the artifact from the collection, free its memory, and shift any following artifacts so that indices remain contiguous.  
   - If the index is invalid, display an error message and return to the menu.

3. **Display a specific artifact**  
   - Prompt the user for the *index* (1‑based) of the artifact to view.  
   - Call a function `displayArtifact` (see constraints) that prints the artifact’s details in a readable format.  
   - If the index is invalid, display an error message.

4. **List all artifacts**  
   - Print a numbered list of all stored artifacts, showing only the *index* and *name* for each entry.  
   - If the collection is empty, print “No artifacts stored.”

5. **Exit the program**  
   - Before terminating, free **all** dynamically allocated memory.  
   - The menu must contain a clearly labeled option (e.g., `0. Exit`) that ends the program.

The menu should be displayed after each operation until the user chooses to exit.

## Example Input / Output  

```
=== Museum Artifact Manager ===
1. Add artifact
2. Delete artifact
3. Display artifact
4. List all artifacts
0. Exit
Choose an option: 1

Enter name (max 50 chars): Golden Mask
Enter year of origin: 1325
Enter description (max 200 chars): A ceremonial mask made of gold, discovered in the Andes.

Artifact added successfully!

=== Museum Artifact Manager ===
1. Add artifact
2. Delete artifact
3. Display artifact
4. List all artifacts
0. Exit
Choose an option: 4

Current artifacts:
1. Golden Mask

=== Museum Artifact Manager ===
1. Add artifact
2. Delete artifact
3. Display artifact
4. List all artifacts
0. Exit
Choose an option: 3

Enter artifact index to display: 1

--- Artifact #1 ---
Name       : Golden Mask
Year       : 1325
Description: A ceremonial mask made of gold, discovered in the Andes.
--------------------

=== Museum Artifact Manager ===
1. Add artifact
2. Delete artifact
3. Display artifact
4. List all artifacts
0. Exit
Choose an option: 0

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Structure** – The primary entity must be represented by a `struct Artifact` containing at least the following members:  
   ```c
   char name[51];        // 50 chars + terminating null
   int  year;
   char description[201]; // 200 chars + terminating null
   ```
2. **Dynamic Allocation** – Every artifact must be allocated on the heap using `malloc` (or `calloc`). No static or global arrays of artifacts are allowed.
3. **Display Function** – The logic for printing the details of a single artifact **must** reside in a function with the exact prototype:  
   ```c
   void displayArtifact(const struct Artifact *a, int index);
   ```
4. **Memory Management** – All memory obtained with `malloc`/`calloc` must be released with `free` before the program exits, and also when an artifact is deleted.
5. **Menu Requirement** – The program must present a menu as shown in the example and **must** include an explicit option to **EXIT** the program (option `0` in the example). Selecting this option terminates the loop and ends the program after freeing memory.
6. **Single‑File Implementation** – The entire solution must be written in a single source file (`.c`). Apart from `main`, you may define additional helper functions, but the core menu handling should remain in `main`.  

*Note: The problem is intended for students who have just learned `malloc`, `free`, structs, and basic I/O. No advanced data structures (linked lists, etc.) are required; a simple dynamically‑resized array (reallocating as needed) is sufficient.*

---

## Problem 5 - openai/gpt-oss-120b - Iteration 85
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “personal library” manager for a university student who wants to keep track of the books he/she owns. The program must store each book’s information dynamically because the number of books is not known at compile‑time and can change while the program runs (books can be added or removed).  

## Requirements  
Write a C program that allows the user to manage a collection of books using **dynamic memory allocation** (`malloc`, `realloc`, `free`). The program must provide a **menu‑driven interface** with the following options:

1. **Add a new book** – Prompt the user for the book’s title (string, up to 100 characters), author (string, up to 100 characters), and number of pages (positive integer). Allocate memory for the new book and store it in the collection.  
2. **Remove a book** – Ask for the **index** (starting at 1) of the book to delete. Remove the book from the collection, free its memory, and shift the remaining entries so that there are no gaps.  
3. **List all books** – Display the index, title, author, and page count for every book currently stored.  
4. **Display details of a specific book** – Ask for the index of a book and show its full information. The logic for this operation **must be placed in a function called `displayBook`**.  
5. **Exit** – Terminate the program, freeing any memory that is still allocated. (The menu option to exit must be clearly numbered, e.g., `0. Exit`.)

### Functional Details
- The collection should be stored as a **dynamic array of `struct Book`**. The array may grow or shrink as books are added or removed, using `realloc` as needed.  
- Input validation: if the user selects an invalid menu option or provides an out‑of‑range index, display an error message and re‑show the menu.  
- When the program terminates (option “Exit”), all memory that was allocated for books **must be freed**.  

## Example Interaction  

```
=== Personal Library Manager ===
1. Add a new book
2. Remove a book
3. List all books
4. Display a specific book
0. Exit
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter number of pages: 274
Book added successfully!

=== Personal Library Manager ===
1. Add a new book
2. Remove a book
3. List all books
4. Display a specific book
0. Exit
Choose an option: 3

Current books:
1) Title: The C Programming Language | Author: Kernighan & Ritchie | Pages: 274

=== Personal Library Manager ===
1. Add a new book
2. Remove a book
3. List all books
4. Display a specific book
0. Exit
Choose an option: 4

Enter book index to display: 1
--- Book Details ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Pages : 274
--------------------

=== Personal Library Manager ===
1. Add a new book
2. Remove a book
3. List all books
4. Display a specific book
0. Exit
Choose an option: 0

Goodbye!
```

## ### CONSTRAINTS  
- **Struct Requirement** – The primary data entity must be defined as  

  ```c
  typedef struct {
      char title[101];
      char author[101];
      int  pages;
  } Book;
  ```

- **Function Requirement** – The logic for displaying the details of ONE specific book **must be implemented in a function named** `void displayBook(const Book *b);`. No other function may perform this exact task.  

- **Menu Exit Requirement** – The menu must contain an option explicitly labeled (e.g., `0. Exit`) that terminates the program. Selecting this option must cause the program to free all allocated memory before exiting.  

- **Dynamic Allocation Only** – All storage for books must be obtained with `malloc`/`realloc` and released with `free`. No static or global arrays of books are allowed.  

- **Single Source File** – The entire solution must be placed in a single `.c` file (aside from standard library headers).  

- **No Memory Leaks** – The program will be tested with tools such as Valgrind; any leaked memory will result in a failed submission.  

---  

Write the program fulfilling the above specifications. Good luck!

---

## Problem 6 - openai/gpt-oss-120b - Iteration 86
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Logistics**, a small company that ships reusable containers across a city. Each container is tracked by three pieces of information:  

* **ID** – a positive integer that uniquely identifies the container.  
* **Weight** – the current load in kilograms (a `float`).  
* **Destination** – a short string (max 30 characters) describing the delivery address.  

The company’s software must be able to add new containers, remove containers that have been delivered, and display information about a particular container on demand. Because the number of active containers changes at runtime, the program must allocate and free memory dynamically.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Container` that holds the three fields described above.  

2. **Dynamic Storage**  
   * Maintain a dynamic array (or linked list) of `Container` objects.  
   * The array must grow when a new container is added (using `malloc`/`realloc`) and shrink when a container is removed (using `free`).  

3. **Menu‑Driven Interface** (the program must present a text menu to the user)  
   * **1 – Add a container**  
     * Prompt for ID, weight, and destination.  
     * Insert the new container at the end of the dynamic collection.  
   * **2 – Remove a container**  
     * Prompt for an ID.  
     * If a container with that ID exists, delete it and free its memory; otherwise, print “Container not found.”  
   * **3 – Display a container**  
     * Prompt for an ID.  
     * If found, call a function `displayContainer` (see constraints) to print the container’s details; otherwise, print “Container not found.”  
   * **4 – List all containers**  
     * Print the ID, weight, and destination of every stored container, one per line.  
   * **0 – Exit**  
     * Terminate the program after releasing all allocated memory.  

4. **Input Validation**  
   * IDs are unique; if the user tries to add a container with an existing ID, print “ID already in use.” and do not add it.  

5. **Memory Management**  
   * No memory leaks: every allocation must eventually be freed before program termination.  

## Example Interaction  

```
=== Eco‑Logistics Container Manager ===
1) Add a container
2) Remove a container
3) Display a container
4) List all containers
0) Exit
Choice: 1
Enter ID: 101
Enter weight (kg): 12.5
Enter destination: 12 Oak St.
Container added.

1) Add a container
2) Remove a container
3) Display a container
4) List all containers
0) Exit
Choice: 1
Enter ID: 202
Enter weight (kg): 8.0
Enter destination: 45 Pine Ave.
Container added.

1) Add a container
2) Remove a container
3) Display a container
4) List all containers
0) Exit
Choice: 3
Enter ID to display: 101
--- Container 101 ---
Weight: 12.5 kg
Destination: 12 Oak St.

1) Add a container
2) Remove a container
3) Display a container
4) List all containers
0) Exit
Choice: 4
ID   Weight   Destination
101  12.5     12 Oak St.
202  8.0      45 Pine Ave.

1) Add a container
2) Remove a container
3) Display a container
4) List all containers
0) Exit
Choice: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct Container`.  
* **Display Function** – The logic for showing the details of a **single** container **must** be placed in a function with the exact prototype:  

  ```c
  void displayContainer(const struct Container *c);
  ```  

* **Menu Exit Option** – The menu **must** contain an option numbered **0** (or the keyword `EXIT`) that cleanly terminates the program.  
* **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but the entire solution must reside in one source file.  
* **Dynamic Allocation Only** – You are **not** allowed to use static or global arrays to store the containers; all storage must come from `malloc`/`realloc` and be released with `free`.  

---  

*Write a C program that satisfies the above specifications.*

---

## Problem 7 - openai/gpt-oss-120b - Iteration 87
# STEP 1: PROBLEM  

## Background  
You have been hired as a software engineer for **PixelPet**, a startup that creates simple “virtual pet” toys that run on tiny embedded systems. Each pet has a name, an age (in days), and a happiness level (0‑100). Because the device has very limited RAM, pets must be created and destroyed dynamically as the user interacts with the system.  

Your task is to write a C program that lets the user **add**, **remove**, **list**, and **view details** of pets using dynamic memory allocation (`malloc` / `free`). The program must store each pet in a dynamically allocated `struct` and keep a list of pointers to those structs.

## Requirements  

1. **Data structure**  
   * Define a `struct Pet` containing:  
     - `char *name` – a dynamically allocated string (maximum length 50 characters).  
     - `int age` – age in days.  
     - `int happiness` – value from 0 to 100.  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   * **1. Add a new pet** – Prompt for name, age, and happiness; allocate memory for a new `Pet` and store its pointer in the list.  
   * **2. Remove a pet** – Prompt for the pet’s name; locate the matching pet, free its `name` string, free the `Pet` struct, and remove its pointer from the list. If the pet does not exist, print an error message.  
   * **3. List all pets** – Print each pet’s name on a separate line. If no pets exist, print “No pets available.”  
   * **4. Show pet details** – Prompt for a pet’s name and display its age and happiness in the format shown in the example. Use a separate function named `displayPet` for this output. If the pet is not found, print an error message.  
   * **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **Dynamic list management**  
   * The list of pet pointers must be stored in a dynamically allocated array that grows as needed (you may reallocate with `realloc`).  
   * Keep track of the current number of pets and the allocated capacity.  

4. **Input validation**  
   * Age must be a non‑negative integer.  
   * Happiness must be an integer between 0 and 100 inclusive.  
   * If the user enters invalid data, display a brief error message and return to the menu.  

5. **Program termination**  
   * Before exiting, ensure that **all** memory allocated for pet names, pet structs, and the pointer array is freed.  

## Example Interaction  

```
--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 1
Enter pet name: Fluffy
Enter age (days): 12
Enter happiness (0-100): 85
Pet added successfully.

--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 1
Enter pet name: Bubbles
Enter age (days): 5
Enter happiness (0-100): 60
Pet added successfully.

--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 3
Current pets:
Fluffy
Bubbles

--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 4
Enter pet name to view: Fluffy
Pet Details:
Name: Fluffy
Age: 12 days
Happiness: 85

--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 2
Enter pet name to remove: Bubbles
Pet removed.

--- PixelPet Management ---
1) Add a new pet
2) Remove a pet
3) List all pets
4) Show pet details
5) EXIT
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity **must** be represented by a `struct Pet` as described.  
2. **Function requirement** – The logic that displays the details of a single pet **must** be implemented in a function with the exact prototype:  

   ```c
   void displayPet(const struct Pet *p);
   ```  

3. **Dynamic allocation only** – All memory for pet names, pet structs, and the pointer array must be obtained with `malloc`, `calloc`, or `realloc`. No static or global arrays of fixed size are allowed.  
4. **Menu exit option** – The menu must contain an explicit option labeled **5) EXIT** (or the keyword `EXIT`) that terminates the program. Selecting this option must trigger the clean‑up of all allocated memory before the program ends.  

*Optional hint for students:* consider keeping a variable `size_t capacity` and double it whenever the pointer array is full.  

---  

*Your solution will be evaluated on correctness of dynamic memory handling, adherence to the constraints, and proper freeing of all resources.*

---

## Problem 8 - openai/gpt-oss-120b - Iteration 88
# STEP 1: PROBLEM  

## Background  
You have been hired by a small wildlife‑conservation NGO to develop a simple C program that keeps track of rescued **turtles** awaiting release back into the wild. Each turtle has a unique tag number, its species name, and the number of days it has been in the care facility. The NGO’s field volunteers will enter data for an arbitrary number of turtles during a single run of the program. Because the number of turtles is not known in advance, you must allocate memory dynamically.

## Requirements  

Your program must:

1. **Store each turtle’s data** in a dynamically allocated array of structures (use `malloc`/`realloc` as needed).  
2. **Provide a text‑based menu** with the following options:  
   1. **Add a new turtle** – Prompt the user for tag number (int), species (string ≤ 30 characters), and days in care (int). Append the new record to the dynamic array.  
   2. **List all turtles** – Print a table showing all stored turtles in the order they were entered.  
   3. **Search by tag** – Prompt for a tag number and display the matching turtle’s details (or a “not found” message).  
   4. **Remove a turtle** – Prompt for a tag number, delete that turtle from the array, and shrink the allocated memory accordingly.  
   5. **Exit** – Clean up all allocated memory and terminate the program.  

3. All input should be read from `stdin`; all output should be written to `stdout`.  
4. The program must **not leak memory**: every block obtained with `malloc`/`realloc` must eventually be released with `free`.  

## Example Interaction  

```
=== Turtle Rescue Tracker ===
1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 1
Enter tag number: 101
Enter species (max 30 chars): Loggerhead
Enter days in care: 12
Turtle added.

1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 1
Enter tag number: 202
Enter species (max 30 chars): Green
Enter days in care: 7
Turtle added.

1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 2
Tag   Species          Days
101   Loggerhead       12
202   Green            7

1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 3
Enter tag number to search: 202
Tag: 202, Species: Green, Days in care: 7

1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 4
Enter tag number to remove: 101
Turtle removed.

1) Add a new turtle
2) List all turtles
3) Search by tag
4) Remove a turtle
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct` named `Turtle` containing at least the fields `int tag; char species[31]; int days;`.  
* **Function decomposition** –  
  * The logic that **displays the details of ONE specific turtle** (used by the “Search by tag” option) **must be placed in a function called `displayTurtle`** with prototype `void displayTurtle(const Turtle *t);`.  
  * All other menu actions may be implemented in additional helper functions, but the program must contain **no more than three user‑defined functions besides `main`**.  
* **Dynamic array management** – Use `malloc` for the initial allocation and `realloc` when expanding or shrinking the array. Do **not** use a fixed‑size array.  
* **Menu exit requirement** – The menu must include an option explicitly labeled “5) Exit” (or the word `EXIT`) that terminates the program after freeing all allocated memory.  

These constraints are mandatory; solutions that violate any of them will be considered incomplete.

---

## Problem 9 - openai/gpt-oss-120b - Iteration 89
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “student‑record manager” for a university’s registration office.  
The office keeps a **dynamic** list of students that can grow and shrink while the program runs.  
Each student is represented by a `struct` that holds the student's **ID number**, **full name**, **age**, and **GPA**.  

Your task is to write a menu‑driven C program that lets the user add new students, view a particular student’s data, delete a student, and list all stored students. All memory for student records must be obtained with `malloc` (or `calloc`) and released with `free` when a record is removed or when the program terminates.

## Requirements  

1. **Data structure**  
   * Define a `struct Student` containing:  
     ```c
     int    id;          // unique positive identifier
     char  *name;        // dynamically allocated string (max 100 characters)
     int    age;
     float  gpa;
     ```  
   * The `name` field itself must be allocated dynamically (e.g., with `malloc`).

2. **Menu** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new student** – ask for ID, name, age, GPA; allocate memory for the struct and for the name string, then store the pointer in the list. |
   | 2      | **Display a student** – ask for an ID and print all fields of the matching student. If the ID does not exist, print an appropriate message. |
   | 3      | **Delete a student** – ask for an ID, free the memory for that student (including the name string), and remove the pointer from the list. |
   | 4      | **List all students** – print the data of every stored student in the order they were added. |
   | 5      | **Exit** – free **all** remaining allocated memory and terminate the program. *(This option **must** be present.)* |

3. **Dynamic list management**  
   * The program must not assume a fixed maximum number of students.  
   * Use a dynamically allocated array of `Student *` (e.g., start with capacity 2 and `realloc` as needed) to store the pointers to each student record.  

4. **Functions**  
   * Implement a function `void displayStudent(const Student *s);` that prints a single student’s information in a readable format. This function must be used by menu options 2 and 4.  
   * All other logic may reside in `main` or additional helper functions, but **no other function may directly perform printing of a student’s fields** (the printing must go through `displayStudent`).  

5. **Input validation**  
   * IDs must be positive integers and unique; if the user tries to add a student with an existing ID, print an error and discard the input.  
   * Age must be a positive integer; GPA must be a floating‑point number between `0.0` and `4.0`. If any value is invalid, request the input again.  

6. **Memory safety**  
   * Every block obtained with `malloc`/`calloc`/`realloc` must eventually be released with `free`.  
   * The program must not leak memory when the user selects “Exit”.  

## Example Interaction  

```
=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 1

Enter ID: 101
Enter name: Alice Johnson
Enter age: 20
Enter GPA: 3.7
Student added successfully.

=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 1

Enter ID: 102
Enter name: Bob Smith
Enter age: 22
Enter GPA: 3.2
Student added successfully.

=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 2

Enter ID to display: 101
--- Student 101 ---
Name : Alice Johnson
Age  : 20
GPA  : 3.70

=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 4

--- All Students ---
--- Student 101 ---
Name : Alice Johnson
Age  : 20
GPA  : 3.70
--- Student 102 ---
Name : Bob Smith
Age  : 22
GPA  : 3.20

=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 3

Enter ID to delete: 101
Student 101 deleted.

=== Student Record Manager ===
1) Add a new student
2) Display a student
3) Delete a student
4) List all students
5) Exit
Choose an option: 5
Goodbye!
```

*(The exact wording of prompts is not important, only the overall flow and required functionality.)*

---

### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be a `struct Student` as described.  
2. **Display function** – The function `void displayStudent(const Student *s);` must be used for any output of a single student’s details.  
3. **Menu requirement** – The program must present a menu and **must** include an explicit “Exit” option (option 5 in the example). Selecting this option must free all allocated memory before terminating.  
4. **Dynamic allocation only** – No static arrays of fixed size may be used to store the student records; the list must grow/shrink with `malloc`/`realloc`/`free`.  

*Feel free to add any minor helper functions you need, but the above constraints are mandatory.*

---

## Problem 10 - openai/gpt-oss-120b - Iteration 90
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “Student Registry” program for the campus IT department. The registry must keep track of an arbitrary number of students entered during a single execution of the program. Because the number of students is not known in advance, you must allocate and release memory dynamically using `malloc` and `free`.  

## Requirements  
1. **Data representation**  
   * Define a `struct Student` that stores:  
     - an integer `id` (unique identifier)  
     - a string `name` (maximum 50 characters)  
     - a floating‑point `gpa`  

2. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1. Add a student** – Prompt for `id`, `name`, and `gpa`. Allocate a new `Student` object with `malloc` and store it in a dynamically‑grown array (or linked list).  
   * **2. Remove a student** – Prompt for an `id`. Locate the matching student, remove it from the collection, and `free` its memory. If the `id` does not exist, print an appropriate message.  
   * **3. Display a student** – Prompt for an `id`. Locate the student and display all of its fields using a dedicated function (see Constraints). If the `id` is not found, inform the user.  
   * **4. List all students** – Print the details of every student currently stored, in the order they were added.  
   * **5. EXIT** – Terminate the program. Before exiting, free any memory that remains allocated.  

3. **Input validation** – The program should handle non‑numeric input for menu choices gracefully (you may assume the user enters valid data for `id`, `name`, and `gpa`).  

4. **Memory management** – No memory leak is allowed. Every block obtained with `malloc` must be released exactly once.  

## Example Interaction  

```
=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 101
Enter name: Alice
Enter GPA: 3.8
Student added.

=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 102
Enter name: Bob
Enter GPA: 3.5
Student added.

=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 4
ID: 101, Name: Alice, GPA: 3.80
ID: 102, Name: Bob, GPA: 3.50

=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice, GPA: 3.80

=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 2
Enter ID to remove: 102
Student removed.

=== Student Registry ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  
- **Struct usage**: The primary data entity must be represented by a `struct Student`.  
- **Display function**: The logic for showing the details of **one** specific student must be placed in a function named `void displayStudent(const struct Student *s);`.  
- **Menu requirement**: The menu must contain an explicit option numbered **5** (or the keyword `EXIT`) that terminates the program.  
- **Memory discipline**: Every `malloc` call must have a matching `free`. The program must not leak memory, even when the user exits without removing all students.  

*Note: You may implement the collection as a dynamic array that is resized with `realloc`, or as a singly‑linked list; either approach is acceptable as long as dynamic allocation (`malloc`/`realloc`) and deallocation (`free`) are used correctly.*

---

## Problem 11 - openai/gpt-oss-120b - Iteration 91
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for the campus “Lost‑and‑Found” office.  Items that are turned in are recorded in a computer system so that owners can later retrieve them.  Each item has a **type** (e.g., “Wallet”, “Backpack”, “Phone”), a **description** (a short text entered by the staff member), and the **room number** where it was found.  

The office wants a simple console program that lets a user **add**, **list**, **search**, and **remove** items while the program is running.  Because the number of items is not known in advance, the program must allocate memory dynamically using `malloc`/`free`.

## Requirements  

1. Define a `struct Item` that holds the three fields mentioned above (`type`, `description`, `room`).  
2. The program must maintain a **dynamic array** (i.e., a pointer that can be re‑allocated) of `Item` objects.  
3. Implement a **menu‑driven** interface with the following options (the user enters the number shown):  
   1. **Add a new item** – Prompt for type, description, and room; store the new item at the end of the array (grow the array with `realloc`).  
   2. **List all items** – Print every stored item, one per line, showing its index (starting at 0) and all fields.  
   3. **Search by room** – Prompt for a room number and display all items that were found in that room.  
   4. **Remove an item** – Prompt for the index of the item to delete; remove it by shifting later elements left and shrinking the array with `realloc`.  
   5. **EXIT** – Terminate the program (must be option 5).  

4. All memory allocated for the array (and any strings inside the struct, if you allocate them separately) must be released before the program exits.  

## Example Input / Output  

```
=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 1
Enter item type: Phone
Enter description: Black iPhone 12, cracked screen
Enter room number: 210

Item added successfully.

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 1
Enter item type: Wallet
Enter description: Brown leather, contains ID and cash
Enter room number: 210

Item added successfully.

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 2

[0] Type: Phone   Room: 210   Description: Black iPhone 12, cracked screen
[1] Type: Wallet  Room: 210   Description: Brown leather, contains ID and cash

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 3
Enter room number to search: 210

[0] Type: Phone   Description: Black iPhone 12, cracked screen
[1] Type: Wallet  Description: Brown leather, contains ID and cash

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 4
Enter index of item to remove: 0

Item removed.

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 2

[0] Type: Wallet  Room: 210   Description: Brown leather, contains ID and cash

=== Lost‑and‑Found Management ===
1) Add a new item
2) List all items
3) Search by room
4) Remove an item
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Item`.  
* **Function Requirement** – The logic for displaying the details of **one specific item** must be placed in a function named `void displayItem(const struct Item *p);`. This function should be used by both the “List all items” and the “Search by room” options.  
* **Menu Exit** – The menu must contain the explicit option **5) EXIT** (or the keyword `EXIT`) that terminates the program.  
* **Dynamic Allocation Only** – The array of items must be created with `malloc`/`realloc` and freed with `free`. No static or fixed‑size arrays are allowed.  
* **Single‑File Implementation** – All code must reside in a single source file (e.g., `lost_and_found.c`). Apart from `main`, you may create additional helper functions, but the only required extra function is `displayItem`.  

---  

*Feel free to add any harmless user‑interface niceties (such as clearing the screen or pausing), as long as the core requirements and constraints above are satisfied.*

---

## Problem 12 - openai/gpt-oss-120b - Iteration 92
# STEP 1: PROBLEM  

## Background  
You have been hired as the software developer for **“Campus Café”**, a small coffee shop on a university campus.  
The café wants a simple command‑line inventory system to keep track of the drinks it sells during the day.  
Each drink has a name, a price (in dollars, to two decimal places), and the quantity currently in stock.  

Because the number of different drinks can change from day to day (new seasonal drinks may be added, old ones removed), the program must allocate memory dynamically for the list of drinks.

## Requirements  

Write a **menu‑driven** C program that allows the user to manage the drink inventory. The program must support the following operations:

1. **Add a new drink**  
   - Prompt for the drink’s name (a string of up to 30 characters, no spaces), price, and initial quantity.  
   - Allocate memory for the new drink and store it in the dynamic array, expanding the array as necessary with `realloc`.  

2. **Remove a drink**  
   - Prompt for the name of the drink to delete.  
   - If the drink exists, remove it from the array, free the memory associated with that drink, and shrink the array with `realloc`.  
   - If the drink does not exist, display an appropriate message.  

3. **Update the quantity of a drink**  
   - Prompt for the drink’s name and the amount to add (positive integer) or subtract (negative integer).  
   - Adjust the quantity accordingly; the quantity must never become negative.  
   - If the drink is not found, display an appropriate message.  

4. **Display a drink’s details**  
   - Prompt for the drink’s name.  
   - Show the name, price, and current quantity of that drink.  
   - The logic for displaying a single drink must be placed in a function called `displayEntity`.  

5. **List all drinks**  
   - Print a table containing the name, price, and quantity of every drink currently stored.  

6. **Exit**  
   - Terminate the program, freeing **all** dynamically allocated memory before exiting.  

The menu must be displayed after each operation and must contain a clearly labeled option to **EXIT** the program (e.g., “0 – Exit”).

## Example Interaction  

```
=== Campus Café Inventory ===
1) Add a new drink
2) Remove a drink
3) Update drink quantity
4) Display a drink
5) List all drinks
0) Exit
Choose an option: 1
Enter drink name: Latte
Enter price: 3.50
Enter quantity: 10
Drink added.

=== Campus Café Inventory ===
1) Add a new drink
2) Remove a drink
3) Update drink quantity
4) Display a drink
5) List all drinks
0) Exit
Choose an option: 1
Enter drink name: Espresso
Enter price: 2.25
Enter quantity: 5
Drink added.

=== Campus Café Inventory ===
1) Add a new drink
2) Remove a drink
3) Update drink quantity
4) Display a drink
5) List all drinks
0) Exit
Choose an option: 4
Enter drink name to display: Latte
--- Drink Details ---
Name    : Latte
Price   : $3.50
Quantity: 10

=== Campus Café Inventory ===
1) Add a new drink
2) Remove a drink
3) Update drink quantity
4) Display a drink
5) List all drinks
0) Exit
Choose an option: 5
--- All Drinks ---
Name       Price   Quantity
Latte      3.50    10
Espresso   2.25    5

=== Campus Café Inventory ===
1) Add a new drink
2) Remove a drink
3) Update drink quantity
4) Display a drink
5) List all drinks
0) Exit
Choose an option: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity (a drink) must be represented by a `struct` named `Drink` containing at least the fields `name`, `price`, and `quantity`.  
* **Function Requirement** – The code that prints the details of a single drink **must** be placed in a function with the exact prototype:  

  ```c
  void displayEntity(const Drink *d);
  ```  

* **Dynamic Allocation** – The array that holds the pointers to `Drink` objects must be allocated with `malloc`/`realloc` and each individual `Drink` must also be allocated with `malloc`. No static (fixed‑size) arrays are allowed for storing the drinks.  
* **Memory Management** – Every call to `malloc`/`realloc` must have a matching `free` before the program terminates.  
* **Menu Exit Option** – The menu must include an explicit option to exit the program (e.g., option `0 – Exit`). Selecting this option must cause the program to free all allocated memory and then terminate.  

*Optional (for extra credit):*  
- Validate all numeric input (price must be non‑negative, quantity must be an integer).  
- Keep the drink list sorted alphabetically after each insertion.  

---

## Problem 13 - openai/gpt-oss-120b - Iteration 93
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny command‑line “personal library” program for a university reading club. The club members will add information about the books they own, query the collection, and remove books when they are donated away. Because the number of books is not known in advance and can change while the program runs, you must allocate and free memory dynamically using `malloc` and `free`.

## Requirements  

Write a C program that implements a **menu‑driven** interface with the following options (the user selects an option by typing its number and pressing **Enter**):

1. **Add a new book** – Prompt the user for the book’s ISBN (string, up to 13 characters), title (string, up to 100 characters), and number of pages (positive integer). Allocate a new `struct Book` on the heap and store the data.  
2. **List all books** – Print the details of every book currently stored, in the order they were added.  
3. **Find a book by ISBN** – Prompt for an ISBN, search the collection, and display the matching book’s details (or a “not found” message).  
4. **Remove a book by ISBN** – Prompt for an ISBN, locate the book, free its memory, and remove it from the list so that subsequent listings no longer show it. If the ISBN is not present, display an appropriate message.  
5. **Exit** – Terminate the program, freeing any remaining allocated memory.

The program should continue to display the menu after completing any option except **Exit**.

## Example Input / Output  

```
=== Personal Library Menu ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Select an option: 1

Enter ISBN (max 13 chars): 9780131103627
Enter title: The C Programming Language
Enter number of pages: 274
Book added successfully!

=== Personal Library Menu ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Select an option: 2

--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Pages: 274
--- End of List ---

=== Personal Library Menu ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Select an option: 5

Goodbye!
```

(Any reasonable formatting of the output is acceptable as long as the required information is present.)

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Book` containing at least the following members:  
   ```c
   typedef struct Book {
       char isbn[14];      // space for 13 characters + null terminator
       char title[101];    // space for 100 characters + null terminator
       int  pages;
       struct Book *next; // pointer for linked‑list chaining
   } Book;
   ```
2. **Function Requirement** – The logic that prints the details of **exactly one** `Book` must be placed in a function with the exact prototype:  
   ```c
   void displayBook(const Book *b);
   ```
   This function may be called from other parts of the program (e.g., when listing all books or showing a search result).  
3. **Memory Management** – Every `malloc` call must have a corresponding `free` when a book is removed or when the program exits. No memory leaks are permitted.  
4. **Menu Requirement** – The menu must include an option to **EXIT** the program; it must be clearly identified as option **5** (or the keyword “exit”) and must cause the program to terminate after freeing all allocated memory.  

*No additional libraries beyond `<stdio.h>`, `<stdlib.h>`, and `<string.h>` may be used.*  

---  

**Your task** is to design the problem statement above; you do **not** need to provide a solution. The problem should be clear enough for a student who has just learned about `malloc`, `free`, and basic struct handling to implement.

---

## Problem 14 - openai/gpt-oss-120b - Iteration 94
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “inventory” program for a local hobby‑shop that sells model kits.  
Each model kit has a **name**, a **price**, and a **quantity in stock**.  
The shop owner wants to be able to add new kits, remove kits that are discontinued, and view the details of a single kit on demand.  
Because the number of different kits changes over time, the program must allocate memory dynamically for each kit as it is entered.

## Requirements  
Write a C program that fulfills the following functional specifications:

1. **Data Representation**  
   * Define a `struct Kit` that stores the name (a string of up to 50 characters), price (a `double`), and quantity (an `int`).  

2. **Menu‑driven Interface** (the program must present a text menu repeatedly until the user chooses to exit)  
   * **1 – Add a new kit**  
     * Prompt the user for the name, price, and quantity.  
     * Allocate memory for a new `struct Kit` using `malloc` and store the entered data.  
     * Store the pointer in a dynamic array that grows as needed (you may re‑allocate the array with `realloc`).  
   * **2 – Delete a kit**  
     * Prompt for the name of the kit to delete.  
     * Search the dynamic array for a kit with that exact name.  
     * If found, free the memory for that `struct Kit`, remove the pointer from the array, and shrink the array accordingly.  
     * If not found, print “Kit not found.”  
   * **3 – Display a kit**  
     * Prompt for the name of the kit to display.  
     * Locate the kit and call a function `displayKit` (see Constraints) to print its details in the format shown in the example.  
     * If the kit does not exist, print “Kit not found.”  
   * **4 – List all kits**  
     * Iterate over the dynamic array and print the details of every kit, one per line.  
   * **5 – EXIT**  
     * Terminate the program after freeing **all** allocated memory.  

3. **Input Validation**  
   * The program should handle non‑numeric input for price and quantity gracefully (you may assume the user follows the prompts).  

4. **Memory Management**  
   * Every `malloc`/`realloc` must have a matching `free`.  
   * No memory leaks should remain when the program exits.

## Example Interaction  

```
=== Model Kit Inventory ===
1) Add a new kit
2) Delete a kit
3) Display a kit
4) List all kits
5) EXIT
Choose an option: 1
Enter kit name: Starfighter
Enter price: 34.99
Enter quantity: 12
Kit added.

=== Model Kit Inventory ===
1) Add a new kit
2) Delete a kit
3) Display a kit
4) List all kits
5) EXIT
Choose an option: 1
Enter kit name: Space Rover
Enter price: 27.50
Enter quantity: 5
Kit added.

=== Model Kit Inventory ===
1) Add a new kit
2) Delete a kit
3) Display a kit
4) List all kits
5) EXIT
Choose an option: 3
Enter kit name to display: Starfighter
Name: Starfighter, Price: $34.99, Quantity: 12

=== Model Kit Inventory ===
1) Add a new kit
2) Delete a kit
3) Display a kit
4) List all kits
5) EXIT
Choose an option: 4
Name: Starfighter, Price: $34.99, Quantity: 12
Name: Space Rover, Price: $27.50, Quantity: 5

=== Model Kit Inventory ===
1) Add a new kit
2) Delete a kit
3) Display a kit
4) List all kits
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Usage** – The primary data entity must be represented by a `struct Kit`.  
2. **Display Function** – The logic for printing the details of a single kit must be placed in a function with the exact prototype:  

   ```c
   void displayKit(const struct Kit *k);
   ```  

3. **Menu Requirement** – The program must present a menu as described above and **must include option 5 (or the keyword EXIT) to terminate the program**.  
4. **Single‑source File** – All code must reside in a single `.c` file; you may define additional helper functions, but the `main` function must orchestrate the menu loop.  
5. **Dynamic Array Management** – You must manage the collection of kit pointers with a dynamically allocated array (using `malloc`/`realloc`). Static arrays or fixed‑size limits are not allowed.  

*Feel free to add any auxiliary helper functions you need, but respect the constraints above.*

---

## Problem 15 - openai/gpt-oss-120b - Iteration 95
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Event Planning Office** to write a small utility that keeps track of **event volunteers**.  
Each volunteer has a name (up to 30 characters) and the number of hours they have pledged to work.  
The office does not know in advance how many volunteers will sign up, so the program must allocate memory dynamically as volunteers are added and release it when they are removed.

## Requirements  

Write a C program that provides a **menu‑driven interface** to manage the volunteer list. The program must support the following operations:

1. **Add a volunteer**  
   - Prompt the user for the volunteer’s name and pledged hours.  
   - Dynamically allocate (or re‑allocate) space to store the new volunteer record.  

2. **Remove a volunteer**  
   - Prompt for the volunteer’s name.  
   - If a volunteer with that name exists, remove the record, shrink the allocated array accordingly, and free the memory that is no longer needed.  
   - If the name is not found, display an appropriate message.  

3. **Display all volunteers**  
   - List every stored volunteer in the order they were added, showing the name and pledged hours.  

4. **Display a specific volunteer**  
   - Prompt for a name and, if found, display that volunteer’s details.  
   - The logic for this operation must be placed in a function named `displayVolunteer`.  

5. **Exit**  
   - Terminate the program, freeing all allocated memory.  

The menu must be displayed after each completed operation until the user chooses to exit.

## Example Input / Output  

```
=== Volunteer Management Menu ===
1) Add volunteer
2) Remove volunteer
3) Display all volunteers
4) Display a specific volunteer
5) Exit
Enter choice: 1
Enter name: Alice
Enter pledged hours: 12

Volunteer added.

=== Volunteer Management Menu ===
1) Add volunteer
2) Remove volunteer
3) Display all volunteers
4) Display a specific volunteer
5) Exit
Enter choice: 1
Enter name: Bob
Enter pledged hours: 8

Volunteer added.

=== Volunteer Management Menu ===
1) Add volunteer
2) Remove volunteer
3) Display all volunteers
4) Display a specific volunteer
5) Exit
Enter choice: 3

Current volunteers:
1. Alice – 12 hours
2. Bob – 8 hours

=== Volunteer Management Menu ===
1) Add volunteer
2) Remove volunteer
3) Display all volunteers
4) Display a specific volunteer
5) Exit
Enter choice: 4
Enter name to view: Bob

Volunteer details:
Name: Bob
Hours pledged: 8

=== Volunteer Management Menu ===
1) Add volunteer
2) Remove volunteer
3) Display all volunteers
4) Display a specific volunteer
5) Exit
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct` named `Volunteer` containing at least the fields `char name[31];` and `int hours;`.  
* **Dynamic allocation** – Use `malloc`, `realloc`, and `free` to manage the array of `Volunteer` records. No fixed‑size arrays are allowed.  
* **Function requirement** – The logic for displaying the details of ONE specific volunteer must be implemented in a function with the exact prototype:  
  ```c
  void displayVolunteer(const Volunteer *v);
  ```  
* **Menu exit option** – The menu must include an option (clearly numbered or keyworded) that allows the user to exit the program; choosing this option must free all allocated memory before terminating.  

Your solution should compile with a standard C compiler (e.g., `gcc -std=c11`).

---

## Problem 16 - openai/gpt-oss-120b - Iteration 96
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for a **community garden**. The garden keeps a list of *plot reservations*. Each reservation stores the gardener’s name, the size of the plot (in square meters), and the number of weeks the plot will be used. The garden manager wants a simple command‑line program that can add new reservations, remove an existing reservation, and display the details of any reservation on demand. Because the number of reservations is not known in advance and can change while the program runs, you must allocate and free memory dynamically.

## Requirements  

1. **Data Structure**  
   * Define a `struct Reservation` that contains:  
     - `char *name` – a dynamically allocated string for the gardener’s name (max length 100 characters).  
     - `int size` – plot size in square meters.  
     - `int weeks` – number of weeks the reservation lasts.  
   * Store each reservation in a dynamically allocated node of a singly‑linked list.

2. **Program Functionality**  
   The program must present a **menu** with the following options (the user selects by entering the number):  
   1. **Add a reservation** – Prompt for name, size, and weeks, allocate memory for a new `Reservation`, and insert it at the end of the list.  
   2. **Remove a reservation** – Prompt for the gardener’s name, locate the first node whose `name` matches exactly, remove it from the list, and free all associated memory. If no such reservation exists, print an informative message.  
   3. **Display a reservation** – Prompt for the gardener’s name and call a function `displayReservation` (see Constraints) to print the reservation’s details. If the name is not found, print an informative message.  
   4. **List all reservations** – Traverse the list and print each reservation’s details in the order they were added.  
   5. **EXIT** – Terminate the program after freeing all allocated memory.  

3. **User Interaction**  
   - After completing any operation (except EXIT), the menu should be shown again.  
   - Input validation is not required beyond what is described; you may assume the user enters data of the correct type.

4. **Memory Management**  
   - Every `malloc`/`calloc`/`realloc` must have a matching `free`.  
   - When a reservation is removed or the program exits, all memory belonging to that reservation (including the name string) must be released.

## Example Input / Output  

```
=== Garden Plot Reservation System ===
1) Add a reservation
2) Remove a reservation
3) Display a reservation
4) List all reservations
5) EXIT
Select an option: 1

Enter gardener's name: Alice
Enter plot size (m^2): 12
Enter number of weeks: 8
Reservation added.

=== Garden Plot Reservation System ===
1) Add a reservation
2) Remove a reservation
3) Display a reservation
4) List all reservations
5) EXIT
Select an option: 1

Enter gardener's name: Bob
Enter plot size (m^2): 20
Enter number of weeks: 4
Reservation added.

=== Garden Plot Reservation System ===
1) Add a reservation
2) Remove a reservation
3) Display a reservation
4) List all reservations
5) EXIT
Select an option: 3

Enter gardener's name to display: Alice
Reservation for Alice:
  Plot size: 12 m^2
  Duration : 8 weeks

=== Garden Plot Reservation System ===
1) Add a reservation
2) Remove a reservation
3) Display a reservation
4) List all reservations
5) EXIT
Select an option: 4

All reservations:
1) Alice – 12 m^2, 8 weeks
2) Bob   – 20 m^2, 4 weeks

=== Garden Plot Reservation System ===
1) Add a reservation
2) Remove a reservation
3) Display a reservation
4) List all reservations
5) EXIT
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct Reservation` as described.  
2. **Display Function** – The logic for showing the details of a single reservation must be placed in a function with the exact prototype:  

   ```c
   void displayReservation(const struct Reservation *r);
   ```

3. **Menu Exit Option** – The menu must contain an option labelled **EXIT** (option number 5 in the example) that terminates the program. Selecting this option must first free **all** dynamically allocated memory.  

4. **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but the entire solution must be contained in a single source file (e.g., `garden.c`).  

5. **Standard Library Only** – Use only the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are allowed.  

---

## Problem 17 - openai/gpt-oss-120b - Iteration 97
# STEP 1: PROBLEM  

## Background  
You have been hired by the campus IT department to write a small utility that keeps track of **temporary study‑group sessions** for a single course.  
Each session is created at run‑time, stores a few pieces of information, and can be removed when the group finishes.  
Because the number of sessions is not known in advance, the program must allocate and free memory dynamically using `malloc` and `free`.

## Program Requirements  

1. **Data representation**  
   * Define a `struct Session` that contains:  
     - an integer `id` (unique identifier, assigned sequentially starting from 1)  
     - a string `topic` (maximum 50 characters)  
     - an integer `participants` (number of students in the group)  

2. **Menu‑driven interface** (the program must present a text menu after each operation)  
   * **1 – Add a new session**  
     - Prompt the user for `topic` and `participants`.  
     - Allocate memory for a new `struct Session`, fill the fields, assign the next `id`, and store the pointer in a dynamic array that grows as needed.  
   * **2 – List all sessions**  
     - Print a table showing `id`, `topic`, and `participants` for every session currently stored.  
   * **3 – Display a session**  
     - Ask for a session `id` and call a function `displaySession` (see constraints) to print the details of that single session.  
   * **4 – Delete a session**  
     - Ask for a session `id`. Remove the corresponding `struct Session` from the dynamic array, free its memory, and shift the remaining pointers so that the array stays compact.  
   * **5 – EXIT**  
     - Terminate the program after freeing **all** remaining allocated memory.  

3. The program must continue to show the menu until the user selects the **EXIT** option.

## Example Interaction  

```
=== Study‑Group Manager ===
1) Add a new session
2) List all sessions
3) Display a session
4) Delete a session
5) EXIT
Choose an option: 1
Enter topic: Operating Systems Review
Enter number of participants: 4
Session added with id 1.

=== Study‑Group Manager ===
1) Add a new session
2) List all sessions
3) Display a session
4) Delete a session
5) EXIT
Choose an option: 1
Enter topic: Compiler Design Basics
Enter number of participants: 3
Session added with id 2.

=== Study‑Group Manager ===
1) Add a new session
2) List all sessions
3) Display a session
4) Delete a session
5) EXIT
Choose an option: 2
ID   Topic                     Participants
1    Operating Systems Review  4
2    Compiler Design Basics    3

=== Study‑Group Manager ===
1) Add a new session
2) List all sessions
3) Display a session
4) Delete a session
5) EXIT
Choose an option: 3
Enter session id to display: 2
--- Session 2 ---
Topic: Compiler Design Basics
Participants: 3

=== Study‑Group Manager ===
1) Add a new session
2) List all sessions
3) Display a session
4) Delete a session
5) EXIT
Choose an option: 5
Cleaning up… All memory freed. Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented with a `struct Session`.  
2. **Display function** – The logic for showing the details of a **single** session must reside in a function with the exact prototype:  

   ```c
   void displaySession(const struct Session *s);
   ```  

3. **Dynamic array management** – The collection of session pointers must be stored in a dynamically allocated array that grows (e.g., using `realloc`) when new sessions are added and shrinks when sessions are removed.  
4. **Memory safety** – Every `malloc`/`realloc` must have a corresponding `free`. No memory leaks are allowed; all allocated memory must be released before program termination.  
5. **Menu requirement** – The menu must include an explicit option **5 – EXIT** (or the word “EXIT”) that ends the program. Selecting this option must trigger the cleanup described above.  

*Note:* Use only the standard C library (`stdio.h`, `stdlib.h`, `string.h`). Do **not** use global variables; all data structures should be managed through pointers passed between functions.

---

## Problem 18 - openai/gpt-oss-120b - Iteration 98
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Bookstore** to write a small C program that keeps track of the books currently on loan to students.  
Each loan record contains the student’s ID, the title of the book, and the number of days the book is borrowed for.  
The bookstore wants a simple console application that can add new loan records, remove a record when a book is returned, and display the details of a particular loan.  

Because the number of active loans changes over the semester, the program must allocate memory dynamically for each record and release it when the record is removed.

## Requirements  

Write a C program that fulfills the following functionality:

1. **Data representation**  
   * Define a `struct Loan` that stores:  
     - `int studentID;`  
     - `char *title;`   (dynamically allocated string)  
     - `int days;`  

2. **Menu‑driven interface** (the program must present a text menu and repeat until the user chooses to exit)  
   * **1 – Add a new loan**  
     - Prompt for `studentID`, the book `title` (a line of text up to 100 characters), and `days`.  
     - Allocate a new `struct Loan` with `malloc`.  
     - Allocate just‑enough memory for the title string, copy it, and store the pointer in the struct.  
     - Insert the new loan at the end of a dynamically‑grown array (or linked list) of loans.  
   * **2 – Return a loan (remove)**  
     - Prompt for a `studentID`.  
     - Search for the first loan with that `studentID`.  
     - If found, free the memory used for the title string and the `struct Loan` itself, then remove it from the collection, shifting remaining elements if you use an array.  
     - If not found, print “Loan not found.”  
   * **3 – Display a loan**  
     - Prompt for a `studentID`.  
     - Locate the loan with that `studentID` and call a function `displayLoan` (see Constraint) to print its contents in the format shown in the example.  
     - If the loan does not exist, print “Loan not found.”  
   * **4 – List all loans**  
     - Iterate over the collection and print each loan using `displayLoan`.  
   * **0 – Exit**  
     - Terminate the program after freeing **all** dynamically allocated memory.  

3. **Error handling**  
   * If any `malloc` call fails, print “Memory allocation failed.” and exit the program.  

4. **Program termination**  
   * Before exiting (via the menu option), ensure that every block of memory obtained with `malloc`/`calloc`/`realloc` is released with `free`.

## Example Input / Output  

```
--- Campus Bookstore Loan System ---
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
0. Exit
Choose an option: 1

Enter student ID: 12345
Enter book title: Introduction to Algorithms
Enter number of days: 14
Loan added.

--- Campus Bookstore Loan System ---
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
0. Exit
Choose an option: 1

Enter student ID: 67890
Enter book title: Clean Code
Enter number of days: 7
Loan added.

--- Campus Bookstore Loan System ---
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
0. Exit
Choose an option: 3

Enter student ID to display: 12345
Student ID: 12345
Title     : Introduction to Algorithms
Days      : 14

--- Campus Bookstore Loan System ---
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
0. Exit
Choose an option: 4

Student ID: 12345
Title     : Introduction to Algorithms
Days      : 14

Student ID: 67890
Title     : Clean Code
Days      : 7

--- Campus Bookstore Loan System ---
1. Add a new loan
2. Return a loan
3. Display a loan
4. List all loans
0. Exit
Choose an option: 0

All memory freed. Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Loan` as described above.  
2. **Display function** – The logic for printing the details of a single loan must be placed in a function with the exact prototype:  

   ```c
   void displayLoan(const struct Loan *loan);
   ```  

3. **Single additional function** – Apart from `main` and `displayLoan`, you may create helper functions **only if** they are used for memory management (e.g., `createLoan`, `freeLoan`). No other functionality should be placed in extra functions.  
4. **Menu requirement** – The program must provide a menu and **must** include an explicit option `0` (or the word “EXIT”) that terminates the program, as shown in the example.  
5. **Dynamic allocation** – All loan records and their title strings must be allocated with `malloc` (or `calloc`/`realloc`). No static or global arrays of fixed size are allowed for storing the loans.  

*Note: The problem is deliberately open to either an array that is resized with `realloc` or a linked‑list implementation; both satisfy the constraints as long as the above rules are respected.*

---

## Problem 19 - openai/gpt-oss-120b - Iteration 99
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **“PixelPet”,** a simple console‑based virtual‑pet game. Each pet has a name, an age (in days), and a “hunger level” that ranges from 0 (full) to 10 (starving). The game must allow the user to create any number of pets while the program runs, inspect a single pet’s details, feed a pet (decrease its hunger level), and finally release all pets before exiting.

The focus of this assignment is to practice **dynamic memory allocation** with `malloc` and `free`. All pets must be stored on the heap, and the program must correctly clean up every allocation before terminating.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Pet` that contains:  
     - `char *name;`   (dynamically allocated string)  
     - `int age;`  
     - `int hunger;`  

2. **Menu‑driven Interface** (displayed repeatedly until the user chooses to quit)  
   * **1. Add a new pet** – Prompt for the pet’s name (single word, up to 31 characters) and its age.  
     - Allocate memory for a new `Pet`.  
     - Allocate exactly enough memory to store the entered name (including the terminating `'\0'`).  
     - Initialise `hunger` to `5`.  
   * **2. List all pets** – Print each pet’s index (starting at 0) and name.  
   * **3. Show pet details** – Ask for a pet index, then call a function `displayPet` that prints the pet’s name, age, and hunger level.  
   * **4. Feed a pet** – Ask for a pet index, then decrease its `hunger` by 1 (minimum 0).  
   * **5. Remove a pet** – Ask for a pet index, free the memory for that pet’s name and the `Pet` structure itself, and shift the remaining pets in the array so that indices stay contiguous.  
   * **6. EXIT** – Terminate the program after freeing **all** remaining allocated memory.  

3. **Dynamic Storage of the Pet List**  
   * The collection of pets must be stored in a dynamically allocated array of pointers (`Pet **petList`).  
   * When a new pet is added, the array should be resized with `realloc` to accommodate the extra pointer.  
   * When a pet is removed, shrink the array accordingly.

4. **Error Handling**  
   * If the user enters an invalid index, print an informative message and return to the menu.  
   * If any `malloc`/`realloc` call fails, print an error and exit gracefully after freeing any memory already obtained.

5. **Program Termination**  
   * Before exiting (whether via the menu or an error), ensure that every block of memory allocated with `malloc`/`realloc` is released with `free`.

## Example Interaction  

```
--- PixelPet ---
1) Add a new pet
2) List all pets
3) Show pet details
4) Feed a pet
5) Remove a pet
6) EXIT
Choose an option: 1
Enter pet name: Fluffy
Enter pet age (days): 12
Pet added.

--- PixelPet ---
1) Add a new pet
2) List all pets
3) Show pet details
4) Feed a pet
5) Remove a pet
6) EXIT
Choose an option: 2
[0] Fluffy

--- PixelPet ---
1) Add a new pet
2) List all pets
3) Show pet details
4) Feed a pet
5) Remove a pet
6) EXIT
Choose an option: 3
Enter pet index: 0
Name   : Fluffy
Age    : 12 days
Hunger : 5

--- PixelPet ---
1) Add a new pet
2) List all pets
3) Show pet details
4) Feed a pet
5) Remove a pet
6) EXIT
Choose an option: 4
Enter pet index to feed: 0
Fluffy has been fed. Hunger is now 4.

--- PixelPet ---
1) Add a new pet
2) List all pets
3) Show pet details
4) Feed a pet
5) Remove a pet
6) EXIT
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Pet` as described above.  
* **Display Function** – The logic for displaying the details of ONE specific pet **must** be placed in a function with the exact prototype:  
  ```c
  void displayPet(const struct Pet *p);
  ```  
* **Menu Exit Option** – The menu must include a distinct option labelled **“6) EXIT”** (or the exact keyword `EXIT`) that terminates the program.  
* **Memory Management** – Every allocation performed with `malloc`, `calloc`, or `realloc` must have a matching `free` before program termination. No memory leaks are allowed.  
* **Single‑source File** – The entire solution should be written in one `.c` file and may contain only `main` plus the required helper functions (e.g., `displayPet`). No additional libraries beyond `<stdio.h>`, `<stdlib.h>`, and `<string.h>` may be used.  

---  

*Write a program that satisfies all the requirements above, demonstrating correct use of dynamic memory allocation, pointer arithmetic, and proper resource cleanup.*

---

## Problem 20 - openai/gpt-oss-120b - Iteration 100
# STEP 1: PROBLEM  

## Background  
A small wildlife sanctuary maintains a list of rescued animals that are adopted out to families.  Each animal record contains the animal’s **ID number**, **species name**, **age in months**, and a **short description** entered by the caretaker.  The sanctuary’s computer system must be able to add new animals, remove animals that have been adopted, and display the information of a particular animal on demand.  

Because the number of rescued animals changes over time, the program must allocate memory dynamically for each animal record and release it when the record is deleted.

## Requirements  

Write a C program that implements the following functionality:

1. **Add an animal** – Prompt the user for the animal’s ID (integer), species (string, max 30 characters), age (integer), and description (string, max 100 characters).  
   - Dynamically allocate a `struct Animal` to store this information using `malloc`.  
   - Store a pointer to the newly created struct in an array that can grow as needed (you may also use a linked list if you prefer).  

2. **Remove an animal** – Prompt the user for an animal ID.  
   - Search for the animal with that ID.  
   - If found, free the memory occupied by that animal’s struct and remove its pointer from the collection.  
   - If not found, display an appropriate message.  

3. **Display an animal** – Prompt the user for an animal ID.  
   - Locate the animal and print all its fields in a readable format.  
   - The printing logic must be placed in a function named `displayAnimal`.  

4. **List all animals** – Print a summary line for every animal currently stored (ID and species only).  

5. **Exit** – Terminate the program, freeing any memory that remains allocated.  

The program should repeatedly present a menu that allows the user to choose one of the actions above until the “Exit” option is selected.

## Example Interaction  

```
=== Sanctuary Animal Tracker ===
1. Add animal
2. Remove animal
3. Display animal
4. List all animals
5. Exit
Choose an option: 1

Enter ID: 101
Enter species: Red Panda
Enter age (months): 18
Enter description: Small, shy, loves climbing.
Animal added.

=== Sanctuary Animal Tracker ===
1. Add animal
2. Remove animal
3. Display animal
4. List all animals
5. Exit
Choose an option: 1

Enter ID: 202
Enter species: African Grey Parrot
Enter age (months): 36
Enter description: Very talkative, enjoys puzzles.
Animal added.

=== Sanctuary Animal Tracker ===
1. Add animal
2. Remove animal
3. Display animal
4. List all animals
5. Exit
Choose an option: 4

Current animals:
ID: 101   Species: Red Panda
ID: 202   Species: African Grey Parrot

=== Sanctuary Animal Tracker ===
1. Add animal
2. Remove animal
3. Display animal
4. List all animals
5. Exit
Choose an option: 3

Enter ID to display: 101
--- Animal Details ---
ID: 101
Species: Red Panda
Age (months): 18
Description: Small, shy, loves climbing.

=== Sanctuary Animal Tracker ===
1. Add animal
2. Remove animal
3. Display animal
4. List all animals
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data structure** – The primary entity must be represented by a `struct` named `Animal` containing at least the fields `id`, `species`, `age`, and `description`.  

2. **Dynamic allocation** – Every `Animal` instance must be created with `malloc` (or `calloc`) and released with `free` when the animal is removed or when the program exits.  

3. **Display function** – The logic that prints the full details of a single animal must be encapsulated in a function with the exact prototype:  

   ```c
   void displayAnimal(const struct Animal *a);
   ```  

4. **Menu requirement** – The program must present a textual menu as shown in the example.  
   - The menu must include an explicit option to **EXIT** the program (option number 5 in the example).  

5. **Memory safety** – No memory leaks are permitted. All allocated memory must be freed before the program terminates.  

6. **Standard library only** – Use only the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries.  

Feel free to choose an array that resizes with `realloc` or a singly‑linked list to store the pointers to `Animal` structs; either approach satisfies the requirements as long as the dynamic allocation rules are obeyed.

---

## Problem 21 - moonshotai/kimi-k2-instruct-0905 - Iteration 31
# STEP 1: PROBLEM

## Context
You are helping the campus library manage its collection of e-books.  
Each e-book record contains a title (≤60 chars), an author (≤40 chars), and a file-size in MB (positive double).  
All records are stored in memory only while the program is running.  
The librarian should be able to add new books, delete a book by its zero-based index, list every book, or safely quit.

## Functional Requirements
1. The program keeps an expandable array of e-book records in dynamic memory.
2. Provide a simple text menu:
   ```
   1) Add book
   2) Delete book
   3) List books
   4) Exit
   ```
3. “Add book” reads title, author, and size; appends the record; reallocates memory as needed.
4. “Delete book” reads an integer index; if valid, removes that book and shrinks the array; otherwise print “Invalid index.”
5. “List books” prints every book in the order stored, one per line, in the exact format:
   ```
   <index>. "<title>" by <author> (<size> MB)
   ```
   If no books exist, print “Collection empty.”
6. On “Exit” the program frees all heap memory and terminates.

## Simple Example Run
```
1) Add book
2) Delete book
3) List books
4) Exit
Choice: 1
Title: C Traps and Pitfalls
Author: Andrew Koenig
Size: 1.2
Book added.

Choice: 1
Title: The C Programming Language
Author: Kernighan & Ritchie
Size: 2.3
Book added.

Choice: 3
0. "C Traps and Pitfalls" by Andrew Koenig (1.2 MB)
1. "The C Programming Language" by Kernighan & Ritchie (2.3 MB)

Choice: 2
Index to delete: 0
Book deleted.

Choice: 3
0. "The C Programming Language" by Kernighan & Ritchie (2.3 MB)

Choice: 4
Good-bye.
```

### CONSTRAINTS
- Must use a `struct` to represent one e-book record.
- The logic that prints a single book must live in a function called `displayBook`.
- Only two functions are allowed: `main` and `displayBook`.
- Menu option 4 is the required EXIT keyword.

---

## Problem 22 - moonshotai/kimi-k2-instruct-0905 - Iteration 32
# STEP 1: PROBLEM

## Background Story
The campus library has just started a “Late-Night Laptop Lending” program.  
Students can borrow a laptop for up to 4 hours, but only while supplies last.  
You have been asked to write a tiny console app that keeps track of which laptops are currently checked-out and which are available.  
All data must live only in dynamic memory (`malloc`/`free`) while the program runs; when the program ends, the list disappears.

## Functional Requirements
1. Start with an empty inventory (no laptops).
2. Support the following commands (menu-driven):
   - `1` Add a new laptop to the pool (enter ID and battery %).
   - `2` Check-out a laptop by ID (only if it is not already checked-out).
   - `3` Return a laptop by ID (mark it available again).
   - `4` Show the full current inventory (ID, battery, status).
   - `5` Completely remove a laptop from the pool (free its memory).
   - `6` EXIT the program and free all remaining memory.
3. After every command, re-display the menu.
4. If an operation is illegal (e.g., duplicate ID, check-out of non-existent laptop), print a short error message and continue.

## Simple Example Run
```
=== Laptop Lending ===
1) Add laptop
2) Check-out
3) Return
4) Show inventory
5) Remove laptop
6) EXIT
Choice: 1
Enter laptop ID: 101
Battery %: 85
Laptop added.

Choice: 2
Enter laptop ID to check-out: 101
Laptop 101 checked out.

Choice: 4
ID: 101 | Battery: 85% | Status: OUT

Choice: 6
Good-bye.
```

### CONSTRAINTS
- Must use a `struct` to represent each laptop.
- All laptop structs must be stored in a linked list that is built with `malloc`.
- Every `malloc` must eventually be matched by a `free` (no leaks).
- The only functions allowed besides `main()` are:
  - `void displayInventory(struct Laptop *head)` – prints the list.
  - `void freeAll(struct Laptop *head)` – frees every node.
- Menu option `6` must be the only way to exit the program.

---

## Problem 23 - moonshotai/kimi-k2-instruct-0905 - Iteration 33
# STEP 1: PROBLEM

## Story
Professor Byte has just opened the campus **USB Memory Bank**.  
Students can deposit ("check-in") any number of USB sticks, each with a unique ID and a capacity in GB.  
They can also withdraw ("check-out") a stick by giving its ID.  
Because the bank never knows how many sticks will arrive, it must store them in dynamically-allocated memory.  
Your task is to write the program that acts as the bank’s front-desk clerk.

## Program Requirements
1. Keep track of every USB stick currently in the bank.  
2. Support three operations (presented in a menu that repeats until the user chooses to quit):
   - 1  Check-in a new stick  
     – Ask for an ID string (max 15 chars, no spaces) and capacity (positive integer ≤ 1024 GB).  
     – Reject duplicate IDs.  
   - 2  Check-out a stick  
     – Ask for the ID; remove it and free its memory; if the ID is not found, say so.  
   - 3  List all sticks currently in the bank (ID and capacity)  
   - 4  Exit the program  
3. Use dynamic memory allocation (`malloc`/`free`) for every stick.  
4. After every operation (except Exit) re-display the menu.

## Example Run
```
USB Memory Bank
1 Check-in  2 Check-out  3 List  4 Exit
Choice: 1
ID: blue32
Capacity (GB): 64
Stick blue32 checked in.

1 Check-in  2 Check-out  3 List  4 Exit
Choice: 1
ID: red11
Capacity (GB): 128
Stick red11 checked in.

1 Check-in  2 Check-out  3 List  4 Exit
Choice: 3
blue32 64GB
red11 128GB

1 Check-in  2 Check-out  3 List  4 Exit
Choice: 2
ID: blue32
Stick blue32 checked out.

1 Check-in  2 Check-out  3 List  4 Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must use a `struct` to represent each USB stick.  
- All stick data must be stored in dynamically-allocated memory; no fixed-size arrays.  
- The logic that prints the details of ONE stick must be placed in a function called `displayStick`.  
- The entire solution must be implemented with only one additional function besides `main` (you may still use `displayStick`).

---

## Problem 24 - moonshotai/kimi-k2-instruct-0905 - Iteration 34
# STEP 1: PROBLEM

## Story
You are helping the campus library move from a card-catalog to a tiny digital archive.  
The head librarian asks for a console program that can store (and later discard) book records in **heap memory only**.  
No global arrays are allowed; every record must be created with `malloc` and released with `free`.

## Requirements
1. The user can repeatedly choose one of four actions from a menu:
   - 1) Add a new book  
   - 2) Delete the most recently added book (LIFO)  
   - 3) Show the current catalog (print every book, one per line)  
   - 4) Exit (the program must free every remaining record before termination)

2. Each book stores:
   - a unique integer id (auto-incremented, starting at 1)
   - title (max 80 characters, no spaces)
   - year of publication (positive integer)

3. After every command the menu must re-appear until the user chooses Exit.

4. If the catalog is empty, deletion or display must print:  
   `Catalog is empty.`

## Simple Example Run
```
1) Add
2) Delete-last
3) Show
4) Exit
Choice: 1
Title: KandR
Year: 1988
1) Add
2) Delete-last
3) Show
4) Exit
Choice: 1
Title: DragonBook
Year: 1986
1) Add
2) Delete-last
3) Show
4) Exit
Choice: 3
1 KandR 1988
2 DragonBook 1986
1) Add
2) Delete-last
3) Show
4) Exit
Choice: 2
1) Add
2) Delete-last
3) Show
4) Exit
Choice: 4
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- All book records must live in dynamically allocated memory (`malloc`/`free`).
- Logic that prints a single book must be placed in a function called `displayBook`.
- The only functions allowed besides `main` are `displayBook` and any helper functions you need for memory management.
- Menu option 4 is the **only** valid way to exit; the program must free every remaining book before terminating.

---

## Problem 25 - moonshotai/kimi-k2-instruct-0905 - Iteration 35
# STEP 1: PROBLEM

## Context
You are helping the campus library build a tiny, self-service kiosk that keeps track of which books are currently on the shelf.  
Because the kiosk only runs while a patron is using it, the list of books must be built on-the-fly with dynamic memory.  
When the patron is done, the list is freed and the program exits, releasing all memory back to the system.

## Requirements
1. The program starts with an empty collection (no books).
2. The program repeatedly shows this menu:

   ```
   1 Add a book
   2 List all books
   3 Remove a book by ISBN
   4 Exit
   ```

3. “Add a book” reads from stdin: title (may contain spaces), author (may contain spaces), and a positive integer ISBN.  
   The book is appended to the current collection.
4. “List all books” prints every book in the order added, one per line, in the exact format:

   ```
   ISBN: 1234567890 | Title: Alice in Wonderland | Author: Lewis Carroll
   ```

   (If the collection is empty, print nothing.)
5. “Remove a book by ISBN” reads an integer ISBN.  
   Only the first matching book is removed; memory for that book is freed.  
   If no book matches, do nothing.
6. The program must not leak memory: every malloc’d block must be freed before the program ends.

## Simple Example
Input
```
1
Alice in Wonderland
Lewis Carroll
1234567890
1
The Hobbit
J. R. R. Tolkien
1234567891
2
3
1234567890
2
4
```

Output
```
ISBN: 1234567890 | Title: Alice in Wonderland | Author: Lewis Carroll
ISBN: 1234567891 | Title: The Hobbit | Author: J. R. R. Tolkien
ISBN: 1234567891 | Title: The Hobbit | Author: J. R. R. Tolkien
```

### CONSTRAINTS
- Must use a struct to represent a Book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` (you may declare other helper functions, but only one additional function may contain substantial logic; `displayBook` counts as that one).
- Menu option 4 is the EXIT keyword.

---

## Problem 26 - moonshotai/kimi-k2-instruct-0905 - Iteration 36
# STEP 1: PROBLEM

## Topic  
Dynamic Memory Allocation (malloc, free)

## Background Story  
The campus library has just opened a new “Tech-Loan” desk that lets students borrow electronic gadgets (e.g., tablets, VR headsets, drones).  
You are asked to write a quick, light-weight console program to keep track of which gadgets are currently checked-out.  
All data must live only while the program is running (no files), so you will use dynamic memory.

## Functional Requirements  
1. The program starts with an empty list of gadgets.  
2. It repeatedly shows a menu:  
   1) Add a gadget  
   2) Return (delete) a gadget by ID  
   3) List all gadgets  
   4) EXIT  
3. Adding a gadget allocates a new structure, stores its data, and appends it to the list.  
4. Returning a gadget finds the gadget with the given ID, removes it from the list, frees its memory, and compacts the list.  
5. Listing displays one line per gadget in the order they were added.  
6. After every operation the menu re-appears until the user chooses EXIT (option 4).

## Input/Output Example  
(“> ” is the prompt; user input is in italics)

```
1) Add
2) Return
3) List
4) EXIT
> *1*
Enter gadget ID: *T123*
Enter gadget name: *Tablet Pro*
Enter borrower name: *Alice*
1) Add
2) Return
3) List
4) EXIT
> *1*
Enter gadget ID: *V007*
Enter gadget name: *VR Headset*
Enter borrower name: *Bob*
1) Add
2) Return
3) List
4) EXIT
> *3*
T123 Tablet Pro Alice
V007 VR Headset Bob
1) Add
2) Return
3) List
4) EXIT
> *2*
Enter gadget ID to return: *T123*
Gadget T123 returned.
1) Add
2) Return
3) List
4) EXIT
> *4*
Good-bye!
```

## CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (a gadget).  
- The list must be maintained as a dynamically-allocated array of pointers (`struct gadget **list`).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The only functions allowed are `main` and `displayEntity`; no other helper functions.

---

## Problem 27 - moonshotai/kimi-k2-instruct-0905 - Iteration 37
# STEP 1: PROBLEM  
**Memory Mailbox**  

A local post office has hired you to write a small program that keeps track of physical mailboxes currently in storage. Each mailbox is represented only by a 32-byte description string (e.g., “rusty red mailbox on post”). The warehouse can add or remove mailboxes at runtime, so you must store the descriptions in heap memory using `malloc` and `free`.  

Your program must provide a console menu with the following options:  
1. Add a mailbox  
2. Remove a mailbox  
3. List all mailboxes  
4. Exit (free all remaining mailboxes and quit)  

The program starts with an empty warehouse (no mailboxes).

---

## Problem 28 - moonshotai/kimi-k2-instruct-0905 - Iteration 38
# STEP 1: PROBLEM

## Background Story  
The university library is modernizing its old card-catalog system. You have been hired to write a tiny proof-of-concept that keeps the catalogue only in memory while the program is running. All data must be allocated dynamically with `malloc`/`free`, because the final embedded device will have no standard C++ containers available.

## Functional Requirements  
1. The program stores exactly three pieces of information for each book:  
   - an integer id (unique inside the catalogue)  
   - the title (≤80 printable characters)  
   - the author (≤80 printable characters)  
2. The catalogue is initially empty.  
3. The user must be able to perform the following operations through a simple text menu:  
   1) Add a new book  
   2) List all books (one per line: id, title, author)  
   3) Remove a book given its id  
   4) EXIT the program  
4. Every dynamically created structure must be released before the program terminates (no memory leaks).  
5. If the user tries to add a book with an id that already exists, print `"Duplicate id"` and do nothing else; otherwise print `"Book added"`.  
6. If the user tries to remove a non-existing id, print `"Not found"`; otherwise print `"Book removed"`.

## Simple Example Run  
(Everything after “> ” is user input.)

```
1
> 17
> The C Programming Language
> Kernighan & Ritchie
Book added
1
> 42
> Dynamic Memory For Dummies
> Malloc Mallory
Book added
2
17, The C Programming Language, Kernighan & Ritchie
42, Dynamic Memory For Dummies, Malloc Mallory
3
> 17
Book removed
4
```

Program terminates and Valgrind reports: `All heap blocks were freed -- no leaks are possible`.

### CONSTRAINTS  
- Must use a single `struct` called `Book` to represent the primary data entity.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The program must be implemented with exactly one function besides `main()` (i.e. `displayBook` is the only additional function).  
- If a menu is implemented, option 4 must be the EXIT option.

---

## Problem 29 - moonshotai/kimi-k2-instruct-0905 - Iteration 39
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Context  
You are writing a tiny guest-book for the console.  
The user can add, list, and delete guest records.  
Each record is just a name (≤ 30 characters) and a message (≤ 100 characters).

Requirements  
1. Store all records in dynamically allocated memory.  
2. The program must support three commands:  
   - ADD followed by a name and a message → store one record  
   - LIST → print every stored record  
   - EXIT → free memory and terminate  
3. After each ADD the program must allocate a new struct and append it to the collection.  
4. After LIST the program must print every stored record.  
5. After EXIT the program must free all allocated memory and exit cleanly.

Example  
Input  
ADD Alice Hello  
ADD Bob Hello  
LIST  
EXIT  

Output  
Name: Alice Message: Hello  
Name: Bob Message:

---

## Problem 30 - moonshotai/kimi-k2-instruct-0905 - Iteration 40
# STEP 1: PROBLEM

## Background Story
The campus bookstore is running a “Student-Authored Titles” promotion.  
Authors (students) may add their books to a shared catalogue and later remove them if they change their minds.  
Because the number of books is unknown in advance, the catalogue must grow and shrink at run-time using dynamic memory allocation.

## Precise Functional Requirements
1. Represent each book with a struct that stores:
   - a unique integer id (positive, supplied by the user)
   - the book’s title (one word, ≤30 chars)
   - the author’s name (one word, ≤30 chars)
2. Maintain the collection as a dynamically-allocated array of pointers to these structs.
3. Provide an interactive menu with the following choices:
   1. Add a new book
   2. Remove a book by id
   3. Display catalogue (print id, title, author for every book)
   4. Exit (this choice must be numbered 4)
4. Adding must:
   - check that the id is not already present
   - allocate a new struct and resize the array with realloc
5. Removing must:
   - find the book, free its struct, compact the array, and realloc to shrink it
   - print “Book <id> removed.” or “Book <id> not found.”
6. Display must be implemented in a function called `displayEntity` that receives one struct pointer and prints its data on a single line in the format:
   ```
   [<id>] "<title>" by <author>
   ```
7. After every successful add or remove, print the current number of books in the catalogue.
8. On Exit, free all remaining memory and print “Good-bye!”

## Simple Example Run
```
===== Student Book Catalogue =====
1. Add book
2. Remove book
3. Display catalogue
4. Exit
Choice: 1
Enter id title author: 42 Algorithms Alice
Added. Total books: 1
Choice: 1
Enter id title author: 7 Poems Bob
Added. Total books: 2
Choice: 3
[42] "Algorithms" by Alice
[7] "Poems" by Bob
Choice: 2
Enter id to remove: 42
Book 42 removed. Total books: 1
Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must use a struct to represent each book entity.
- The logic that prints the details of a single book must be placed in a function called `displayEntity` which receives a pointer to that struct.
- The only functions allowed are `main` and `displayEntity`.
- Menu option 4 is the required EXIT choice.

---

## Problem 31 - moonshotai/kimi-k2-instruct-0905 - Iteration 41
# STEP 1: PROBLEM

## Background Story
The campus library is digitising its small “Reference-Only” book shelf.  
Each book is so fragile that it cannot be moved; instead, every student request is answered by *creating a temporary digital bookmark* that records the student’s name and the page they want to revisit.  
The librarian has hired you to write a short-lived tool that keeps track of these bookmarks in memory while the program is running and releases the memory when the student leaves the terminal.

## Functional Requirements
1. The program starts with an initially empty collection of bookmarks.
2. It repeatedly presents a menu with the following options:
   1. Add a bookmark (student’s name ≤30 chars, page number ≥1)  
   2. Delete the *last* bookmark that was added (LIFO)  
   3. Display *all* current bookmarks in the order they were added  
   4. Exit (this option must be numbered 4)
3. After every successful operation (add or delete) the program must print the total number of bookmarks currently stored.
4. If the user tries to delete when no bookmarks exist, print “Stack-empty” and redisplay the menu.
5. Before the program terminates it must free every allocated structure.

## Example Session (user input after prompt ›)
```
1. Add bookmark
2. Delete last bookmark
3. Show all
4. Exit
Choice › 1
Student name › Alice
Page › 77
Total bookmarks: 1

1. Add bookmark
2. Delete last bookmark
3. Show all
4. Exit
Choice › 1
Student name › Bob
Page › 42
Total bookmarks: 2

1. Add bookmark
2. Delete last bookmark
3. Show all
4. Exit
Choice › 3
1. Alice, page 77
2. Bob, page 42

1. Add bookmark
2. Delete last bookmark
3. Show all
4. Exit
Choice › 2
Removed Bob, page 42
Total bookmarks: 1

1. Add bookmark
2. Delete last bookmark
3. Show all
4. Exit
Choice › 4
Good-bye!
```

### CONSTRAINTS
- You must use a `struct` called `Bookmark` to represent one bookmarked request.
- The logic that prints the details of a *single* bookmark must be placed in a function called `displayBookmark(const struct Bookmark *b)`.
- You may implement only **one** additional function besides `main()` (you may still use library functions such as `malloc`, `free`, `printf`, etc.).
- Menu option 4 is the only valid way to exit the program.

---

## Problem 32 - moonshotai/kimi-k2-instruct-0905 - Iteration 42
# STEP 1: PROBLEM

## Context
You are helping the campus library build a tiny, self-service kiosk that keeps track of who is currently reading which book.  
Because the kiosk has very little permanent storage, the list of “who-has-which-book” must live only in RAM while the program is running.  
All records must therefore be created, updated, and destroyed with explicit dynamic memory calls (`malloc`, `free`).

## Functional Requirements
1. The program starts with an empty list.
2. It repeatedly presents a menu:
   ```
   1. Register new loan
   2. Return book (remove record)
   3. Show all active loans
   4. Exit
   ```
3. **Register new loan**  
   - Read a reader name (single word, ≤30 chars), an ISBN string (≤20 chars), and a title string (≤50 chars).  
   - Dynamically create one record, add it to the list.
4. **Return book**  
   - Read an ISBN.  
   - Remove the corresponding record and free its memory; print `Not found` if the ISBN is absent.
5. **Show all active loans**  
   - Print every record on one line in this exact format:  
     ```
     Reader: <name>, ISBN: <isbn>, Title: <title>
     ```
   - Print `No active loans` when the list is empty.
6. **Exit**  
   - Free any remaining memory and terminate.

## Example Run
```
1. Register new loan
2. Return book
3. Show all active loans
4. Exit
Choice: 1
Reader: Alice
ISBN: 9780131103627
Title: The C Programming Language
Choice: 1
Reader: Bob
ISBN: 9780201633610
Title: Design Patterns
Choice: 3
Reader: Alice, ISBN: 9780131103627, Title: The C Programming Language
Reader: Bob, ISBN: 9780201633610, Title: Design Patterns
Choice: 2
ISBN: 9780131103627
Choice: 3
Reader: Bob, ISBN: 9780201633610, Title: Design Patterns
Choice: 4
<program ends>
```

### CONSTRAINTS
- You must store each loan in a `struct Loan` allocated with `malloc`.  
- All list manipulation (insert, delete, traverse) must use explicit pointer logic; you may not use global arrays.  
- The only additional function besides `main()` must be `displayLoan(struct Loan* node)`, which prints one record in the required format.

---

## Problem 33 - moonshotai/kimi-k2-instruct-0905 - Iteration 43
# STEP 1: PROBLEM

You are helping a tiny library automate its book-tracking system.  
The librarian can add new books, remove old ones, and list every book currently stored.  
Each book has a unique (positive) ID, a title (no spaces, ≤30 chars), and the number of copies on the shelf.  
All data must be kept only in dynamic memory (i.e., you must use malloc/realloc and free; no global arrays).

Program behaviour
1. The program starts with an empty collection.
2. It repeatedly shows a menu:
   1. Add book
   2. Remove book
   3. List books
   0. Exit  ← mandatory exit option
3. “Add book” asks for ID, title, copies. If the ID is already taken the request is ignored.
4. “Remove book” asks for an ID; if it exists the book is erased and its memory freed.
5. “List books” prints every book on a single line in the order they were added:
   ID title copies
6. After every command (except Exit) the menu re-appears. Choosing 0 ends the program and frees every remaining allocation.

Example run (user input after >)
1
>101 C_Programming 4
2
>101
3
101 C_Programming 4
0

### CONSTRAINTS
- You must store each book in a struct Book { int id; char title[31]; int copies; };  
- You must keep the collection as a dynamically-sized array of struct Book * (i.e., struct Book **library).  
- The logic that prints the details of ONE specific book must be in a function void displayBook(const struct Book *b).

---

## Problem 34 - moonshotai/kimi-k2-instruct-0905 - Iteration 44
# STEP 1: PROBLEM

## Background Story
You are helping the campus “RideShare” office manage their fleet of electric scooters.  
Each scooter stores only three pieces of information: an integer ID (1–9999), its current battery percentage (0–100), and whether it is currently rented (1 = yes, 0 = no).  
Because the fleet size changes every semester, the office wants a program that stores the scooters in dynamic memory and lets the user add, remove, and display scooters on demand.

## Functional Requirements
1. The program must keep all scooters in dynamically allocated memory (i.e., use `malloc`/`realloc`/`free`; no statically sized arrays).
2. When the program starts it has **zero** scooters.
3. The user is presented with a menu:
    1. Add a new scooter  
    2. Remove a scooter by ID  
    3. Display all scooters  
    4. Exit  
   (Choosing option 4 must cleanly free all allocated memory and terminate the program.)
4. Adding a scooter:
   - Prompt for ID, battery, rented status.  
   - Reject duplicate IDs (print `ID already exists.` and leave memory unchanged).  
   - Dynamically expand the collection to hold the new scooter.
5. Removing a scooter:
   - Prompt for an ID.  
   - If the ID exists, delete that scooter and shrink the dynamic memory; otherwise print `ID not found.`
6. Displaying scooters:
   - Print one line per scooter in the format `ID: <id>, Battery: <bat>%, Rented: <Yes/No>`  
   - If the fleet is empty, print `Fleet empty.`

## Simple Example Run
```
1. Add a new scooter
2. Remove a scooter
3. Display all scooters
4. Exit
Choice: 1
Enter ID: 101
Enter battery: 85
Is rented (1=yes, 0=no): 0
Scooter added.

Choice: 1
Enter ID: 202
Enter battery: 42
Is rented (1=yes, 0=no): 1
Scooter added.

Choice: 3
ID: 101, Battery: 85%, Rented: No
ID: 202, Battery: 42%, Rented: Yes

Choice: 2
Enter ID to remove: 101
Scooter removed.

Choice: 3
ID: 202, Battery: 42%, Rented: Yes

Choice: 4
Goodbye.
```

### CONSTRAINTS
- You must define a `struct Scooter` to represent a single scooter.
- The logic that prints the details of exactly one scooter must be placed in a function called `displayScooter(const struct Scooter *s)`.
- The entire solution must be implemented with only two functions: `main()` and `displayScooter()`.

---

## Problem 35 - moonshotai/kimi-k2-instruct-0905 - Iteration 45
# STEP 1: PROBLEM

## Context
You have been hired by the campus bookstore to write a tiny inventory system that keeps track of how many copies of each textbook are in stock. The program must store the records in dynamic memory (heap) so that the array can grow or shrink while the program is running. All memory you allocate with malloc must later be released with free before the program ends.

## Functional Requirements
1. The program starts by asking how many different titles will be entered initially (≥0).
2. For each title it reads: ISBN (long), title (one–line string, max 80 chars), quantity (int).
3. After the initial load the program shows a menu with four choices:
   - 1 – Add a new book (append to the current list)
   - 2 – Update quantity of an existing book (search by ISBN)
   - 3 – Display complete inventory (one line per book)
   - 4 – Exit (must free all heap memory and terminate)
4. Every dynamic array expansion must use realloc; no fixed upper limits are allowed.

## Example Session (user input in italics)
```
How many initial titles? *2*
ISBN: *9780131103627*
Title: *The C Programming Language*
Quantity: *2*
ISBN: *9780134190440*
Title: *Computer Systems: A Programmer's Perspective*
Quantity: *5*

Menu
1 Add
2 Update
3 Display
4 Exit
Choice: *3*
9780131103627 "The C Programming Language" 2
9780134190440 "Computer Systems: A Programmer's Perspective" 5
Choice: *1*
ISBN: *9780201616224*
Title: *Effective C++*
Quantity: *4*
Choice: *3*
9780131103627 "The C Programming Language" 2
9780134190440 "Computer Systems: A Programmer's Perspective" 5
9780201616224 "Effective C++" 4
Choice: *4*
Good-bye.
```

## CONSTRAINTS
- You must define and use a struct Book that contains the three fields.
- All list operations (add, update, display) must be implemented in a single function called manageInventory; main is only allowed to call this one function after the initial load.
- Option 4 must be the explicit EXIT keyword.

---

## Problem 36 - moonshotai/kimi-k2-instruct-0905 - Iteration 46
# STEP 1: PROBLEM
## Background Story
The campus library has just opened a “Tech-Loan” corner where students can borrow small electronic gadgets (Arduino kits, power banks, cables, etc.). To keep track of what is currently on loan, you are asked to write a tiny inventory system that only remembers the gadgets that are **checked-out**.  All data must live in dynamic memory; when the program ends the list disappears (that is fine).

## Program Requirements
1. On startup the list is empty.
2. Repeatedly show a menu:
   ```
   1. Check-out gadget
   2. Return gadget
   3. Show current loans
   4. Exit
   ```
3. “Check-out gadget” asks for:
   - student ID (positive integer)
   - gadget name (single word, ≤30 chars)
   - estimated return day (1-31)
   The new loan is appended to the list.  
   (Do **not** worry about duplicates; every call creates a new record.)
4. “Return gadget” asks for a student ID.  
   - If the student has **any** loan, remove the **first** one found (free its memory) and print:
     ```
     <gadget name> returned by student <student ID>
     ```
   - If the student has no loans, print:
     ```
     No loan found for student <student ID>
     ```
5. “Show current loans” prints one line per record in the order they were added:
   ```
   Student 12345: power-bank (due day 15)
   Student 14022: cable (due day 20)
   ```
   If the list is empty, print:
   ```
   No gadgets currently on loan
   ```
6. After every menu action (except Exit) re-display the menu.
7. Choose menu option 4 to terminate the program gracefully (free all remaining memory before exit).

## Simple Example Run
```
1. Check-out gadget
2. Return gadget
3. Show current loans
4. Exit
Choice: 1
Student ID: 12345
Gadget name: power-bank
Return day: 15
1. Check-out gadget
2. Return gadget
3. Show current loans
4. Exit
Choice: 3
Student 12345: power-bank (due day 15)
1. Check-out gadget
2. Return gadget
3. Show current loans
4. Exit
Choice: 2
Student ID: 12345
power-bank returned by student 12345
1. Check-out gadget
2. Return gadget
3. Show current loans
4. Exit
Choice: 3
No gadgets currently on loan
1. Check-out gadget
2. Return gadget
3. Show current loans
4. Exit
Choice: 4
```

### CONSTRAINTS
- Must use a `struct` to represent one loan record.
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` (you may add `displayEntity` and still satisfy this).
- Must include a specific menu option to EXIT the program: choose `4` to exit.

---

## Problem 37 - moonshotai/kimi-k2-instruct-0905 - Iteration 47
# STEP 1: PROBLEM

**Background Story**  
You are helping a small-town library computerise its book-loan records.  
Each book is stored as a dynamic record containing its title and the number of free copies.  
Readers can borrow or return copies, and the librarian can add new titles to the catalogue.  
When the librarian chooses to shut the program, every dynamically allocated record must be released.

**Program Requirements**  
1. Maintain a catalogue of books (title + available-copy count).  
2. Provide a simple text menu with the following options:  
   1. Add new book title (initial copies ≥ 1)  
   2. Borrow a copy (decrease count by 1, refuse if none left)  
   3. Return a copy (increase count by 1)  
   4. Show entire catalogue (title and current copies)  
   5. Exit (free all memory and terminate)  
3. The catalogue must grow on demand; do not pre-allocate a fixed-size array.  
4. Duplicate titles are not allowed; when “adding” a title that already exists, just increase its copy count instead of creating a second record.

**Example Session**  
Input:
```
1
Pride and Prejudice
3
1
1984
5
2
1984
2
1984
4
5
```

Output:
```
Catalogue:
1984 - 4 copies
```

### CONSTRAINTS
- You must represent each book with a struct that contains at least title (string) and copies (int).  
- All dynamic allocation must be done with malloc; every malloc must have a matching free before the program exits.  
- The menu option to EXIT the program is option 5.

---

## Problem 38 - moonshotai/kimi-k2-instruct-0905 - Iteration 48
# STEP 1: PROBLEM

You have just volunteered to help the campus library digitise its old card-catalogue.  
Each book card contains: title (≤80 chars), author (≤50 chars), and year of publication.  
Your task is to write a tiny, interactive catalogue program that keeps these cards in dynamic memory only while the program is running.  
The librarian should be able to add new cards, list every card, delete a card by position, and cleanly exit.

## Functional Requirements
1. On start-up the program holds **zero** cards; all storage must be obtained with `malloc`/`realloc`.
2. The program presents a menu:
   1) Add a new card  
   2) List all cards  
   3) Delete a card by index (1-based)  
   4) Exit  
3. Adding a card must `realloc` the internal array to hold one more `struct Card`.
4. Deleting a card must shift later elements left and `realloc` the array one element smaller; freeing unused memory is mandatory.
5. After every operation the menu re-appears; choosing option 4 must free **all** remaining memory and terminate gracefully with the message `Good-bye!`

## Simple Example Session
```
1) Add
2) List
3) Delete
4) Exit
Choice: 1
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1978

1) Add
2) List
3) Delete
4) Exit
Choice: 2
#1 "The C Programming Language" by Kernighan & Ritchie (1978)

1) Add
2) List
3) Delete
4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must represent each card with a `struct Card`.
- You must implement the operation “display details of ONE specific card” inside a function called `displayCard`.
- The solution must be implemented with **a single function besides `main()`** (i.e. only `main` and `displayCard`).
- Menu option `4` is the required EXIT keyword.

---

## Problem 39 - moonshotai/kimi-k2-instruct-0905 - Iteration 49
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Background  
The university library is digitising its card catalogue.  
Each card contains a title, author and year.  
All cards are stored in a single “drawer” that can grow or shrink on demand.

Task  
Write a program that sim this drawer using dynamic memory.  
The user can add, list or remove cards.  
All cards reside in one contiguous block allocated with malloc.

Requirements  
1. Represent one card as a struct Card { … }.  
2. Keep the entire drawer in one pointer: struct * drawer = malloc(…).  
3. When the user adds a card, realloc the drawer to size+1.  
4. When the user lists, print every card.  
5. When the user deletes, shift the remaining cards and realloc to size–1.  
6. Provide a menu: 1=add, 2=list, 3=delete, 0=exit.  
7. free everything before exit.

Example  
Input  
1  
1984 Orwell 1949  
1  
Animal Farm Orwell 1945  
2  
3 1984  
2  
0  

Output  
1 1984 Orwell 1949  
2 Animal Farm Orwell 1945  
1 1984 Orwell 1949  
2 Animal Farm Orwell 1945  
1 Animal Farm Orwell 1945  

### CONSTRAINTS  
- Must use a struct Card to represent one entity.  
- Must use malloc/realloc/free only for the drawer.  
- Must include a menu option 0 to EXIT.

---

## Problem 40 - moonshotai/kimi-k2-instruct-0905 - Iteration 50
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

### BACKGROUND  
You are the sole librarian of a tiny, one-room public library that has just gone digital. Every book is now represented only by its title and nothing else. When a patron walks in, they hand you a title and you either add it to the collection or remove it. The collection starts empty and you must store every title in dynamically allocated memory.

### TASK  
Write a program that keeps the live collection of titles in memory while the librarian is working. At any moment the librarian must be able to:  
1. Add a title (malloc)  
2. Remove a title (free)  
3. List every title currently present  
4. Exit the program  

The program must start with an empty collection and finish by freeing every byte it ever allocated.

### INPUT/OUTPUT  
Each command is a single line:

```
add <title>  
remove <title>  
list  
exit  
```

Example session:

```
add Moby Dick  
add Les Misérables  
list  
Moby Dick  
Les Misérables  
remove Moby Dick  
list  
Les Misérables  
exit  
```

### CONSTRAINTS  
- Must use a struct to represent the primary data entity.  
- Must use malloc to add and free to remove.  
- Must include a specific menu option to EXIT the program.

---

## Problem 41 - moonshotai/kimi-k2-instruct-0905 - Iteration 51
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

A small campus library has just acquired its first computer and wants a tiny digital‐only checkout system.  
The librarian will type a list of ISBNs (as 13-digit strings) into the terminal.  
When the librarian finishes, the program must print the exact same list back out, one ISBN per line, and then free every byte it allocated.

### CONSTRAINTS  
1. You may NOT store any data statically; everything must live on the heap.  
2. You may NOT use any global variables.  
3. You may NOT use any arrays (no `[]` anywhere).  
4. You may NOT use any libraries besides `<stdio.h>`, `<stdlib.h>`, and `<string.h>`.  
5. You must use a single function besides `main()`.  
6. You must use `malloc` and `free` only.  

### INPUT  
The first line is a single integer `n` (0 ≤ n ≤ 100).  
The next `n` lines are 13-digit ISBN strings (no spaces).

### OUTPUT  
The exact same `n` lines, one ISBN per line, in the same order.

### EXAMPLE  
Input  
3  
9781234567890  
9791234567890  
9781234567890  

Output  
9781234567890  
9791234567890  
9781234567890

---

## Problem 42 - moonshotai/kimi-k2-instruct-0905 - Iteration 52
# STEP 1: PROBLEM

## Context
The campus library has replaced its old card-catalog with a tiny, memory-constrained computer that can only keep one “bookshelf” in RAM at a time.  
Each shelf holds up to 100 books, but the exact number is not known until run-time.  
Your task is to write a console program that lets the librarian:

1. Create a new shelf (allocate just enough memory for the books that will be placed on it).
2. Fill the shelf with book titles (stop early if the librarian types “END”).
3. List every book currently on the shelf.
4. Discard the entire shelf (free its memory) and exit.

## Functional Requirements
1. Ask the librarian how many books will be placed on the shelf (`n`, 1 ≤ n ≤ 100).
2. Dynamically allocate an array of exactly `n` book titles (each title ≤ 80 characters).
3. Read up to `n` titles from stdin; stop reading if the librarian types the sentinel word `END`.  If fewer than `n` titles are entered, shrink the array to the actual number of titles entered.
4. Print the list of titles in the order they were entered, one per line.
5. After printing, release all dynamically allocated memory and terminate.

## Simple Example
Input
```
5
The C Programming Language
END
```
Output
```
Shelf contents:
The C Programming Language
```
(Only one title was typed before the sentinel, so memory for 1 book is used and then freed.)

### CONSTRAINTS
- Must use a single `struct` named `Shelf` that contains a pointer to the dynamic array of titles and an integer `count` of how many books are currently stored.
- All allocation and re-allocation must be done with `malloc`/`realloc`; no variable-length arrays.
- The logic for printing the shelf must be in a function `void displayShelf(const struct Shelf *s)`.
- The program must offer a menu with two options:  
  1. Create and fill shelf  
  2. Exit (choose 2 to terminate)

---

## Problem 43 - moonshotai/kimi-k2-instruct-0905 - Iteration 53
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its old card catalogue.  
Each card contains a book’s title, author, and year of publication.  
Your task is to write a tiny “digital catalogue” program that can:

- add new cards (allocate them dynamically),
- list every card currently in memory,
- delete a card by its running index,
- free all cards and exit.

The librarian will interact with the program through a simple text menu.

## Functional Requirements
1. On startup the catalogue is empty.
2. Menu options (cycle until the user chooses to quit):
   1) Add Card
   2) List Cards
   3) Delete Card
   4) Exit
3. “Add Card” reads title, author, and year from stdin (see example).
4. “List Cards” prints every card in insertion order, numbering them 0,1,2…
5. “Delete Card” reads an integer index; if valid, frees that card and compacts the array of pointers so there are no gaps.
6. After each command the menu re-appears.
7. Choosing “Exit” must free every remaining card before terminating.

## Simple Input/Output Example
```
1
The Pragmatic Programmer
Andrew Hunt
1999
1
Clean Code
Robert C. Martin
2008
2
0) "The Pragmatic Programmer" by Andrew Hunt (1999)
1) "Clean Code" by Robert C. Martin (2008)
3
0
2
0) "Clean Code" by Robert C. Martin (2008)
4
```
(program exits)

### CONSTRAINTS
- You must store cards in a dynamically-resizing array (`Card **catalogue`).
- Each card must be represented by a `struct Card`.
- The logic that prints a single card must live in a function `void displayCard(const struct Card *c)`.
- The only functions besides `main()` allowed are: `displayCard`, `addCard`, `listCards`, `deleteCard`, and `freeAll`.
- Menu option 4 is the required EXIT keyword.

---

## Problem 44 - moonshotai/kimi-k2-instruct-0905 - Iteration 54
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Loan” counter where students can borrow small electronic items (calculators, phone chargers, etc.).  
Each item is stored in a sealed box labeled with an ID, a description, and the number of units currently available.  
To keep the inventory flexible, the librarian has asked you to write a tiny C program that stores the catalog in dynamic memory and lets her add new items on-the-fly.

## Functional Requirements
1. At start-up the program knows **no items**; everything is entered at run-time.
2. The user can repeatedly:
   - Add a new item (ID, description, quantity).  
   - Show the entire catalog.  
   - Exit.
3. All items must be stored in a dynamically-allocated array that grows by exactly one `struct` each time the user adds an item.
4. When the user chooses **Exit**, the program must:
   - Print every item once more (identical to “Show catalog”).  
   - Release every byte of dynamically-allocated memory.  
   - Terminate gracefully.

## Example Session (user input in `[]`)
```
===== MENU =====
1. Add item
2. Show catalog
3. Exit
Choice: [1]
Enter item ID: [PWRBANK-07]
Enter description: [10 000 mAh power bank]
Enter quantity: [12]

===== MENU =====
1. Add item
2. Show catalog
3. Exit
Choice: [1]
Enter item ID: [CALC-TI30]
Enter description: [Scientific calculator TI-30]
Enter quantity: [5]

===== MENU =====
1. Add item
2. Show catalog
3. Exit
Choice: [2]
Catalog:
PWRBANK-07 | 10 000 mAh power bank | 12
CALC-TI30 | Scientific calculator TI-30 | 5

===== MENU =====
1. Add item
2. Show catalog
3. Exit
Choice: [3]
Final catalog:
PWRBANK-07 | 10 000 mAh power bank | 12
CALC-TI30 | Scientific calculator TI-30 | 5
<program ends>
```

### CONSTRAINTS
- You must define a `struct` named `Item` that contains at least: `char id[32]`, `char desc[64]`, `int qty`.  
- You may implement **only one** additional function besides `main()`; that function must be named `displayItem` and must print a single `Item` in the exact format shown in the example.  
- The menu option to exit the program is **3**.

---

## Problem 45 - moonshotai/kimi-k2-instruct-0905 - Iteration 55
# STEP 1: PROBLEM

**Background Story**  
The campus library has just upgraded to an electronic checkout system.  
Each book is represented by its title, author, and a unique integer ID.  
You are asked to write a tiny “checkout manager” that allows the librarian to add new books, list every book currently in memory, and delete a book by ID. All data must be stored in dynamically allocated structures so that the collection can grow and shrink at runtime.

**Program Requirements**  
1. On startup the program contains zero books.  
2. Present a menu with four options:  
   1. Add a new book  
   2. List all books (ID, title, author)  
   3. Delete book by ID  
   4. Exit  
3. “Add” must prompt for title (≤80 chars), author (≤50 chars), and automatically assign the next free ID (start at 1).  
4. “List” must print the books in the order they were added; if the collection is empty, print “No books.”  
5. “Delete” must free the memory of the chosen book and compact the internal array so there are no gaps.  
6. Choosing “Exit” must free every remaining book before terminating.

**Simple Example Run**  
```
1. Add book
2. List books
3. Delete book
4. Exit
Choice: 1
Title: The C Programming Language
Author: Kernighan & Ritchie
Book added with ID 1.

Choice: 1
Title: Introduction to Algorithms
Author: Cormen
Book added with ID 2.

Choice: 2
ID: 1, Title: The C Programming Language, Author: Kernighan & Ritchie
ID: 2, Title: Introduction to Algorithms, Author: Cormen

Choice: 3
Enter ID to delete: 1
Book deleted.

Choice: 2
ID: 2, Title: Introduction to Algorithms, Author: Cormen

Choice: 4
Good-bye.
```

### CONSTRAINTS  
- The primary data entity must be represented by a `struct Book`.  
- All books must be stored in a single dynamically allocated array that grows/shrinks with `realloc`.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with only two functions besides `main`: `displayBook` and one other helper of your choice.  
- Menu option 4 is the required EXIT keyword.

---

## Problem 46 - moonshotai/kimi-k2-instruct-0905 - Iteration 56
# STEP 1: PROBLEM

## Background Story
The campus library has just upgraded its old card-catalogue to a tiny C program running on the librarian’s PC.  
Every time a student returns a book, the librarian types the book’s ID and the day it is returned.  
Your task is to keep track of these returns in memory (using dynamic allocation) and to let the librarian:
- add a return record,
- list all current records, and
- delete (free) a record once the book is placed back on the shelf.

## Program Requirements
1. The program must display a simple text menu:
   1. Add return record  
   2. List all returns  
   3. Remove a return  
   4. Exit  
2. “Add” allocates one new record, stores the book ID (positive integer) and return day (1-31), and keeps it in a linked list.  
3. “List” prints every record in the order they were added, one per line:  
   `ID=<id> Day=<day>`  
4. “Remove” reads an ID; if that ID exists, the corresponding node is freed and removed from the list.  
5. After each command the menu re-appears until the user chooses Exit.  
6. No global variables; use dynamic memory (malloc/free) for every node.  
7. Before exiting, free every remaining node.

## Simple Example Run
```
1
101 12
1
102 15
2
ID=101 Day=12
ID=102 Day=15
3
101
2
ID=102 Day=15
4
```
(Program ends.)

### CONSTRAINTS
- You must store each return in a struct called `ReturnRecord`.  
- All list operations (add, remove, list) must be implemented in a **single** function called `listOps` besides `main()`.

---

## Problem 47 - moonshotai/kimi-k2-instruct-0905 - Iteration 57
# STEP 1: PROBLEM

## Background Story
The campus library has just switched to a fully digital check-out system.  
Every time a student borrows a book, a “loan record” must be created on-the-fly.  
Because the number of daily loans is unknown in advance, you must manage the records in dynamic memory.  
At closing time the librarian wants to see a summary of every open loan and then free all memory before the program quits.

## Functional Requirements
1. Store an arbitrary number of loan records.
2. Each record contains: student ID (positive int), book ID (string of up to 20 chars), daysBorrowed (int).
3. Provide an interactive menu with at least these options:
   - 1 Add a new loan (allocate one record)
   - 2 Display all current loans
   - 3 Return (delete) a loan by student ID
   - 0 Exit the program
4. After the user chooses “Exit”, the program must release every allocated byte and then terminate.

## Simple Example Run
```
=== Digital Loan Manager ===
1 Add loan
2 List loans
3 Return loan
0 Exit
Choice: 1
Student ID: 101
Book ID: C_Prog_Lang
Days borrowed: 7
Loan added.

Choice: 1
Student ID: 202
Book ID: Algo_Design
Days borrowed: 14

Choice: 2
Loan 0: Student 101, Book C_Prog_Lang, 7 days
Loan 1: Student 202, Book Algo_Design, 14 days

Choice: 3
Student ID to return: 101
Loan removed.

Choice: 0
Releasing memory… Good-bye!
```

### CONSTRAINTS
- You must represent one loan with a `struct` called `Loan`.
- All loans must be kept in a dynamically resizing 1-D array (use `malloc`/`realloc`).
- Logic that prints the details of a **single** loan must be encapsulated in a function named `displayLoan`.
- The only functions allowed besides `main()` are `displayLoan` and any memory-management helpers you need.
- Menu option `0` must immediately exit the program after freeing memory.

---

## Problem 48 - moonshotai/kimi-k2-instruct-0905 - Iteration 58
# STEP 1: PROBLEM

## Background
A small library wants a tiny, self-contained program to keep track of the books that are currently on a single display table.  
Each book has a title (≤ 80 characters), an author (≤ 50 characters), and a year of publication.  
The head librarian will enter new books one-by-one until she types “END” as the title.  
After all books are entered, the program must print the full list in the order they were typed.

## Functional Requirements
1. The program starts with an empty collection.
2. Repeatedly read:
   - Title (stop if the user enters exactly “END”)
   - Author
   - Year
3. Store every book in dynamically allocated memory (you may NOT use a fixed-size array).
4. After the sentinel “END” is entered, print every book on its own line in the exact format:
   ```
   Title by Author (Year)
   ```
5. Before terminating, free every byte of dynamically allocated memory.

## Simple Example
Input
```
The Pragmatic Programmer
Andrew Hunt
1999
Clean Code
Robert C. Martin
2008
END
```
Output
```
The Pragmatic Programmer by Andrew Hunt (1999)
Clean Code by Robert C. Martin (2008)
```

### CONSTRAINTS
- You must define a single `struct` called `Book` that represents one book.
- All dynamic allocations must be done with `malloc`; every `malloc`ed block must be `free`d exactly once.
- The only functions allowed besides `main` are:
  - `struct Book *createBook(const char *title, const char *author, int year);`  
  - `void printBook(const struct Book *b);`  
  - `void freeBook(struct Book *b);`  
- You may NOT use global variables; keep all data inside `main` or pass it through parameters.

---

## Problem 49 - moonshotai/kimi-k2-instruct-0905 - Iteration 59
# STEP 1: PROBLEM  
## Background Story  
You are helping the campus library build a tiny “book-tracker” for its new mini-collection of e-textbooks.  
Each time a student downloads a copy of a book, the program must create a new record in memory (hint: malloc).  
When the student returns the copy, the record must be released (hint: free).  
All records must be kept in a single chained list; no global arrays are allowed.

## Functional Requirements  
1. The program must present a menu with these exact options:  
   1) Add a new book download  
   2) Return (delete) a book  
   3) Show all active downloads  
   4) Exit  
2. “Add” must prompt for: ISBN (string of at most 12 chars), title (string of at most 30 chars), and student ID (integer).  
3. “Return” must prompt for the same ISBN and remove the matching record; if no match, print “ISBN not found.”  
4. “Show all” must print one line per active record with ISBN, title, and student ID separated by spaces.  
5. All dynamic memory must be released before the program terminates.

## Simple Example Run  
```
1
123456789012
Algorithms
101
3
123456789012 Algorithms 101
2
123456789012
4
```
(The program exits without leaks.)

### CONSTRAINTS  
- You must use a struct called `Book` to represent each record.  
- All list operations must be performed inside a single function besides `main()`.  
- Menu option 4 is EXIT and must terminate the program cleanly.

---

## Problem 50 - moonshotai/kimi-k2-instruct-0905 - Iteration 60
# STEP 1: PROBLEM

## Background Story
You are helping a local animal shelter manage its foster-home records.  
Each foster home can temporarily house several cats.  The shelter keeps only the homes that are currently in use, so the list must grow and shrink dynamically as homes are added or removed.

## Requirements
Write a program that keeps a dynamic array of foster-home records.  
Each record contains:
- a unique positive integer ID (used as the key)
- the caregiver’s last name (≤30 characters, no spaces)
- the number of cats currently housed there

The program must support the following commands in a loop:
1. Add a new foster home (allocate space, store the data, expand the array if needed).  
2. Remove a foster home given its ID (free its memory and compact the array).  
3. Show the current list of homes (ID, last name, cat count).  
4. Exit the program and release **all** remaining dynamically allocated memory.

The array itself must be dynamically allocated and resized with `realloc`.  
No global variables are allowed; carry any necessary state through pointers.

## Simple Example
Input
```
1 101 Smith 3
1 102 Lee 1
3
2 101
3
4
```
Output
```
ID: 101 Last: Smith Cats: 3
ID: 102 Last: Lee Cats: 1
ID: 102 Last: Lee Cats: 1
```
(Program terminates after the final `4`.)

### CONSTRAINTS
- Represent each foster home with a `struct FosterHome`.  
- The logic that prints a **single** home must be in a function `void displayHome(const struct FosterHome *home)`.  
- The only functions allowed besides `main()` are `displayHome`, plus at most one helper function for resizing the array.

---

## Problem 51 - moonshotai/kimi-k2-instruct-0905 - Iteration 1
# STEP 1: PROBLEM

## Topic: Dynamic Memory Allocation (malloc, free)

### Context
You are helping a small-town library computerise its catalogue. The librarian can only add or remove books one at a time, but the program must remember every title currently on the shelf. The titles are stored only in memory, not in files, and you must not waste space for books that do not exist.

### Requirements
Write a program that:

1. keeps an expandable list of book titles currently in the library;
2. lets the librarian:
   - add one new title;
   - remove one title;
   - list every title currently stored;
   - exit the program;
3. stores each title as a dynamically allocated string;
4. frees every string before the program ends.

### Example session
```
1 add
2 remove
3 list
4 exit
Choice: 1
Enter title: The Hobbit
Choice: 1
Enter title: Dune
Choice: 3
Current titles:
The Hobbit
Dune
Choice: 2
Enter title: The Hobbit
Choice: 3
Current titles:
Dune
Choice: 1
Enter title: The Hobbit
Choice: 4
Goodbye.
```

### CONSTRAINTS
- Must use a single struct to represent the catalogue.
- Must implement only one function besides main().
- Must free all allocated memory before exit.

---

## Problem 52 - moonshotai/kimi-k2-instruct-0905 - Iteration 2
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Loan” kiosk where students can borrow small electronic items (phone chargers, ear buds, calculators, etc.).  
Each item is tagged with a unique ID and a loan period in days.  
You have volunteered to write the tiny inventory system that keeps track of what is currently checked out.  
All data must live in dynamically-allocated memory so that the kiosk can run for weeks without rebooting.

## Functional Requirements
1. On start-up the program has an empty inventory.
2. The program repeatedly shows a menu:
   1) Add a new item  
   2) Delete an item by ID  
   3) Display all items  
   4) Exit
3. “Add” reads an ID (positive int) and loan period (positive int, in days).  
   - If the ID already exists, print “ID already exists.” and do nothing.  
   - Otherwise store the new item in dynamically-allocated memory.
4. “Delete” reads an ID.  
   - If the ID exists, free its memory and remove it.  
   - Otherwise print “ID not found.”
5. “Display” prints one line per item in the order they were added:  
   ID:<id>, Loan:<days> days
6. “Exit” frees all remaining memory and terminates the program.

## Simple Example Run
```
1) Add
2) Delete
3) Display
4) Exit
Choice: 1
Enter ID: 101
Enter loan days: 7
1) Add
2) Delete
3) Display
4) Exit
Choice: 1
Enter ID: 102
Enter loan days: 3
1) Add
2) Delete
3) Display
4) Exit
Choice: 3
ID:101, Loan:7 days
ID:102, Loan:3 days
1) Add
2) Delete
3) Display
4) Exit
Choice: 2
Enter ID: 101
1) Add
2) Delete
3) Display
4) Exit
Choice: 3
ID:102, Loan:3 days
1) Add
2) Delete
3) Display
4) Exit
Choice: 4
```

### CONSTRAINTS
- Must use a struct to represent each item.  
- All items must be stored in a singly-linked list of dynamically allocated nodes.  
- The only functions besides main() are:  
  – void displayEntity(const struct Item *item)  
  – struct Node *deleteByID(struct Node *head, int id)  
- Menu option 4 is the only way to exit; typing 4 must free every remaining node before terminating.

---

## Problem 53 - moonshotai/kimi-k2-instruct-0905 - Iteration 3
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)

## Background Story  
The campus library has just switched to a fully digital check-out system.  
Every time a student borrows a book, a new record must be created on-the-fly and stored until the book is returned.  
Your task is to write a tiny, self-contained “Digital Check-Out” program that keeps these records in dynamic memory and frees them as soon as the book is returned.

## Functional Requirements  
1. The program starts with an empty collection (no books checked out).  
2. It repeatedly presents a menu:  
   1. Check-out book  
   2. Return book  
   3. Show all currently checked-out books  
   4. Exit program  
3. **Check-out book:**  
   - Prompt for title (≤50 characters) and student ID (positive integer).  
   - Dynamically allocate one structure to store the pair.  
   - Append it to an in-memory array of pointers (also dynamically allocated).  
4. **Return book:**  
   - Prompt for the title.  
   - Remove the corresponding record, free its memory, and compact the array.  
   - If the title is not found, print “Book not found.”  
5. **Show all:** print title and student ID, one per line.  
6. **Exit:** free every remaining record before termination.

## Simple Example Session (user input after `>`)  
```
1
> Quantum Gravity
> 12345
1
> Advanced C
> 67890
3
Quantum Gravity 12345
Advanced C 67890
2
> Quantum Gravity
3
Advanced C 67890
4
```
(Program ends.)

### CONSTRAINTS  
- The primary data entity must be a `struct Book`.  
- All dynamic allocations must use `malloc`/`realloc`/`free`; no global arrays.  
- Logic that prints the details of ONE specific book must be in a function `void displayBook(const struct Book *b)`.  
- The solution must be implemented with a single function besides `main()`.  
- Menu option 4 is the only way to exit; the program must free all remaining memory before terminating.

---

## Problem 54 - moonshotai/kimi-k2-instruct-0905 - Iteration 4
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)  

Background  
A tiny convenience store has just bought a second-hand cash register that can only run console programs. The owner wants a simple stock-control program that keeps a list of products in memory while the program is running. Each product has a name, a price and a quantity. The list must grow and shrink on demand; no fixed-size arrays are allowed.  

Requirements  
1. The program must start with an empty list (pointer initially NULL).  
2. It must support:  
   1) add a new product (malloc)  
   2) delete a product (free)  
   3) list all products  
3. Every add or delete must update the list correctly and never leak memory.  
4. The program must terminate only when the user chooses the EXIT option.  

Example  
Input  
```
1
Apple 2.50 30
1
Banana 1.20 40
2
Apple
3
0
```

Output  
```
Apple 2.50 30
Banana 1.20 40
```

### CONSTRAINTS  
- Must use a struct to represent the product.  
- Must use a single function besides main() (e.g. displayEntity).  
- Must include a menu option 0 to EXIT the program.

---

## Problem 55 - moonshotai/kimi-k2-instruct-0905 - Iteration 5
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)  

### Background Story  
A university residence-hall manager keeps track of which rooms are occupied.  
At the start of the term the manager only knows the total number of rooms; no names are stored yet.  
During check-in day students arrive one-by-one, give their name, and are assigned the lowest-numbered free room.  
If a student wants to check out, the manager deletes that record so the room becomes free again.  
You will write a tiny “front-desk” program that lets the manager type simple commands to: record a check-in, record a check-out, list the current occupants, or exit.

### Functional Requirements  
1. On start-up read one integer N (1 ≤ N ≤ 100 000) – the total number of rooms.  
2. Then repeatedly read a single-line command until the EXIT command is given.  
   Commands are:  
   - `CHECKIN name` – allocate the lowest free room for this student.  
     - Print `OK <name> <room>` on success.  
     - If every room is full print `FULL`.  
   - `CHECKOUT name` – delete that student.  
     - Print `OK` if the name was found and removed.  
     - Print `NOTFOUND` if the name does not exist.  
   - `LIST` – print every occupied room in ascending room-number order, one per line: `<room> <name>`.  
     - If no rooms are occupied print `EMPTY`.  
   - `EXIT` – free all dynamically allocated memory and terminate.  

### Simple Example  
**Input**  
```
5
CHECKIN Alice
CHECKIN Bob
CHECKOUT Alice
LIST
CHECKIN Carol
LIST
EXIT
```

**Output**  
```
OK Alice 1
OK Bob 2
OK
EMPTY
OK Carol 1
1 Carol
2 Bob
```

### CONSTRAINTS  
- You must store each occupant in a dynamically allocated `struct` that contains at least the student’s name (C-string) and room number.  
- You must keep an array of *pointers* to these structs; the array itself must be dynamically allocated with `malloc` and released with `free`.  
- You may **not** use `realloc`; the array size is fixed after the first input.  
- The logic that prints the details of a single occupant must be placed in a function `void displayEntity(const struct Student *s)`.  
- The only functions allowed besides `main` are `displayEntity` and, if you wish, string-duplication helper(s).

---

## Problem 56 - moonshotai/kimi-k2-instruct-0905 - Iteration 6
# STEP 1: PROBLEM  
**Story**  
The town of Byteville has just opened its first public library. You are the volunteer programmer who must write the tiny “checkout register” that keeps track of which books are on the shelves. Because the library may buy more books at any time, the list must grow and shrink while the program is running, so you will use dynamic memory (`malloc`, `free`).

**What the program must do**  
1. Maintain a catalogue of up to 1000 books.  
2. Each book has:  
   - a unique integer ID (1 … 1000)  
   - a title string (≤ 40 characters, no spaces)  
   - an integer quantity (how many physical copies are on the shelf)  
3. Offer the user a menu with the following four choices:  
   1. Add a new book (or increase quantity if ID already exists).  
   2. Remove one copy of a book (if quantity reaches 0 the entry is deleted and its memory freed).  
   3. Display the full catalogue sorted by ID (ascending).  
   4. EXIT the program (free all remaining memory before quitting).  
4. After every operation print the updated total number of distinct titles stored.

**Simple example**  
Input  
```
1 101 C_Programming 5
1 102 Algorithms 3
3
2 101
3
4
```  
Output  
```
Total titles: 1
Total titles: 2
ID 101 C_Programming 5
ID 102 Algorithms 3
Total titles: 2
ID 101 C_Programming 4
ID 102 Algorithms 3
Total titles: 2
Good-bye!
```

### CONSTRAINTS  
- You must store each book in a dynamically allocated `struct Book`.  
- All catalogue operations (add, remove, display) must be performed through a **single user-defined function** besides `main()`.  
- Menu option **4** is the only way to EXIT; the program must free every remaining `struct Book` before terminating.

---

## Problem 57 - moonshotai/kimi-k2-instruct-0905 - Iteration 7
# STEP 1: PROBLEM

## Background
You are helping the campus library manage its small collection of daily-use laptops.  
Each laptop is identified by a unique integer ID, its brand name, and whether it is currently checked out.  
Because the collection grows or shrinks during the semester, you must store the records in dynamically allocated memory and free them before the program ends.

## Requirements
1. Represent one laptop with a `struct` containing:
   - `int id` (unique, positive)
   - `char *brand` (dynamically allocated string)
   - `int isCheckedOut` (0 = available, 1 = checked-out)

2. Provide an interactive menu with the following options:
   - `1` Add a new laptop
   - `2` Display all laptops
   - `3` Check-out a laptop (by ID)
   - `4` Return a laptop (by ID)
   - `5` Remove a laptop record (by ID)
   - `6` Exit the program

3. For options 2–5, if the requested ID does not exist, print `Laptop <id> not found.`

4. Before the program terminates, free **every** dynamically allocated object (both structs and their brand strings).

5. You may assume no more than 100 laptops will ever exist simultaneously.

## Simple Example Run
```
=== Laptop Manager ===
1 Add laptop
2 Display all
3 Check-out
4 Return
5 Remove
6 Exit
Choice: 1
Enter ID: 101
Enter brand: DellXPS
Added laptop 101.

Choice: 1
Enter ID: 102
Enter brand: MacAir
Added laptop 102.

Choice: 3
Enter ID: 101
Laptop 101 checked out.

Choice: 2
ID  Brand     Status
101 DellXPS   OUT
102 MacAir    IN

Choice: 6
Good-bye!
```

### CONSTRAINTS
- You **must** use a `struct` to represent a laptop.
- The logic that prints the details of **one** laptop must be placed in a function called `displayEntity`.
- The solution must be implemented with **only one** additional function besides `main()` (i.e., `displayEntity` is that function; all other code resides in `main`).
- Menu option `6` is the required EXIT keyword.

---

## Problem 58 - moonshotai/kimi-k2-instruct-0905 - Iteration 8
# STEP 1: PROBLEM

## Background Story
You are helping the university library’s “Book-Tracker” project.  
Every time a student checks out a book, the librarian types the book’s ISBN (a 13-digit string) and the student’s ID number (an int).  
All check-outs must be kept until the librarian explicitly deletes them; the data must therefore be stored in dynamically allocated memory so that it can grow and shrink while the program is running.

## Program Requirements
1. The program must repeatedly show a menu:
   1. Add a new check-out  
   2. Delete the oldest check-out (FIFO)  
   3. List all current check-outs  
   4. Exit  
2. “Add” must read an ISBN (13 chars, no spaces) and a student ID, store them in dynamically allocated memory, and append the record to the list.  
3. “Delete” must free the memory of the oldest check-out; if none exist, print “Nothing to delete.”  
4. “List” must print every check-out in order, one per line:  
   ISBN studentID  
5. “Exit” must free all remaining memory and quit.

## Simple Example
Input (user choices and data):
1  
9780131103627 12345  
1  
9780136097042 67890  
3  
2  
3  
4  

Corresponding output:
1. Add  
2. Delete oldest  
3. List  
4. Exit  
Choice: ISBN: Student ID:  
1. Add  
2. Delete oldest  
3. List  
4. Exit  
Choice: ISBN: Student ID:  
1. Add  
2. Delete oldest  
3. List  
4. Exit  
Choice: 9780131103627 12345  
9780136097042 67890  
1. Add  
2. Delete oldest  
3. List  
4. Exit  
Choice: Deleted oldest check-out.  
1. Add  
2. Delete oldest  
3. List  
4. Exit  
Choice: 9780136097042 67890  

### CONSTRAINTS
- Must use a struct to represent one check-out record.  
- The logic for displaying a single record must be in a function called displayEntity.  
- The entire solution must be implemented with only one additional function besides main().

---

## Problem 59 - moonshotai/kimi-k2-instruct-0905 - Iteration 9
# STEP 1: PROBLEM

## Background Story
You have just been hired as the “Memory Librarian” for the city of Heapville.  
Citizens can donate books (titles only) to the library at any time, but because shelf space is precious, every donated book must be stored in dynamically-allocated memory.  
When a citizen is done reading, they may return a book by giving its title; the librarian then frees the memory so it can be reused.  
Your job is to write the program that keeps track of which books are currently checked in.

## Functional Requirements
1. The program starts with an empty collection.
2. Repeatedly present the user with a menu:
   1) Donate book  
   2) Return book  
   3) List all books currently in the library  
   4) Exit
3. Donating a book:
   - Read one line (may contain spaces) that is the book’s title.  
   - Dynamically allocate exactly enough bytes to store the title plus the terminating '\0'.  
   - Store the pointer in your collection.  
   - If the title is already present, print “Book already donated.” and do **not** allocate anything.
4. Returning a book:
   - Read one line (the title).  
   - If the title exists, free its memory and remove it from the collection.  
   - If the title is not found, print “No such book in the library.”
5. Listing books:
   - Print every title currently stored, one per line, in the order they were donated.  
   - If the library is empty, print “Library is empty.”
6. After every command (except Exit), re-display the menu.

## Simple Example Run
(Underlined text is user input)

1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 1  
Title: The C Programming Language  
1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 1  
Title: Dynamic Memory for Dummies  
1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 3  
The C Programming Language  
Dynamic Memory for Dummies  
1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 2  
Title: The C Programming Language  
1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 3  
Dynamic Memory for Dummies  
1) Donate book  
2) Return book  
3) List all books  
4) Exit  
Choice: 4  

### CONSTRAINTS
- You must use a single `struct` named `Book` to represent each book; the struct must contain *only* a dynamically-allocated C-string (`char *title`).  
- All allocation (`malloc`) and deallocation (`free`) must be performed explicitly; you may not use global arrays or fixed-size buffers for the titles.  
- The logic that prints the details of **one** specific book must be in a function called `displayBook()`.  
- You may implement additional helper functions, but the core book-handling logic must reside in **one** additional function besides `main()` (i.e., `displayBook()` counts toward this limit; any others are forbidden).

---

## Problem 60 - moonshotai/kimi-k2-instruct-0905 - Iteration 10
# STEP 1: PROBLEM

## Background Story
The campus library is experimenting with a tiny “book‐tracker” for its new study‐room shelves.  
Each shelf can hold at most `N` books, but the librarian does **not** know `N` in advance.  
Students keep donating books, so the shelf must grow on demand.  
Your task is to write a C program that simulates this shelf: it starts empty, grows with `malloc`/`realloc`, and shrinks when books are removed (using `free`).

## Functional Requirements
1. The program starts by asking for the **initial capacity** of the shelf (a positive integer).
2. It then repeatedly presents a menu:
   ```
   1. Add book
   2. Remove last book
   3. List shelf
   0. EXIT
   ```
3. **Add book**: Prompt for a single‐word title (≤30 chars).  
   - If the shelf is full, double its capacity with `realloc`.  
   - Insert the title at the next free slot.
4. **Remove last book**: Delete the last title (do nothing if shelf is empty).  
   - If after removal the **used** portion is ≤25 % of the current capacity **and** the capacity is > 4, shrink the array to half its current size (never < 4).  
   - `free` the old block after a successful shrink.
5. **List shelf**: Print the current titles, one per line, preceded by `1)` `2)` …  
   - Print `(empty)` if none.
6. On choosing `0` (EXIT), release **all** dynamically allocated memory and terminate gracefully.

## Example Run
```
Initial capacity> 2
1. Add book
2. Remove last book
3. List shelf
0. EXIT
Choice> 1
Title> Alice
Choice> 1
Title> Bob
Choice> 3
1) Alice
2) Bob
Choice> 1
Title> Carol
Choice> 3
1) Alice
2) Bob
3) Carol
Choice> 2
Choice> 3
1) Alice
2) Bob
Choice> 0
```
(Program frees memory and exits.)

### CONSTRAINTS
- You must represent the shelf with a `struct Shelf` that contains at least:  
  `char **titles`, `size_t used`, `size_t capacity`.
- Implement exactly one additional function besides `main()`:  
  `void displayShelf(const struct Shelf *s);`  
  This function prints the list exactly as required for menu option 3.
- No global variables except possibly for constants.

---

## Problem 61 - moonshotai/kimi-k2-instruct-0905 - Iteration 11
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)  

Background  
A tiny campus library owns exactly 100 physical books.  At the start of term every book is either “Available” or “Borrowed”.  The librarian wants a small terminal program that records only two things for each book:  
1. its unique 1-based index (1 … 100)  
2. its status (Available / Borrowed).  

The program must keep this information entirely in RAM, never store anything on disk, and never use fixed-size arrays.  You must allocate / re-allocate / free memory as the user inserts or deletes records.

Functional Requirements  
1. Provide a console menu:  
   1. Add a book  
   2. Delete a book  
   3. List all books  
   4. Exit  
2. “Add” allocates memory for one new book and stores its index and status.  
3. “Delete” frees the memory of the book with the given index.  
4. “List” prints every book index and its status, one per line.  
5. After every command the menu re-appears.  
6. No global variables, no fixed arrays, no memory leaks.  

Input / Output Example  
( > is user input)  
> 1  
> 3  
1 Available  
2 Borrowed  
3 Available  
> 4  

### CONSTRAINTS  
- You must represent a book with a struct Book { int index; char status; }.  
- All books must be stored in a dynamically allocated linked list.  
- You must provide a single function void displayBook(Book *b) that prints one book.  
- You must implement only one additional function besides main().

---

## Problem 62 - moonshotai/kimi-k2-instruct-0905 - Iteration 12
# STEP 1: PROBLEM

## Background Story
You are helping the campus “Lost & Found” office computerize its logbook.  
Every item that is turned in gets an ID number, a short description, and the contact e-mail of the person who found it.  
Because the number of items changes constantly, the office wants a small C program that keeps the list in dynamic memory and lets the clerk add or delete entries during the day.  
At closing time the clerk will print the complete list and exit the program.

## Functional Requirements
1. On start-up the program holds **zero** items and displays a simple text menu:
    ```
    1. Add new item
    2. Remove an item (by ID)
    3. Show all items
    4. Exit
    ```
2. Choosing “Add” prompts for:
    - ID (positive integer, unique in the current list)
    - description (single line, ≤80 characters)
    - finder’s e-mail (single line, ≤40 characters)  
    The program stores this new item in dynamically allocated memory.
3. Choosing “Remove” prompts for an ID.  
    If the ID exists, the corresponding memory is freed and the item disappears; otherwise print `ID not found.`
4. Choosing “Show all” prints every item, one per line, in the order they were added:
    ```
    ID: 102   Desc: Black umbrella   Found-by: alice@univ.edu
    ID: 105   Desc: Blue water bottle Found-by: bob@univ.edu
    ```
    If the list is empty, print `No items.`
5. Choosing “Exit” (option 4) frees all remaining dynamic memory and terminates the program.
6. All dynamic allocations must use `malloc`/`realloc`/`free`; no global arrays are allowed.

## Example Session (user input after prompt)
```
1. Add new item
2. Remove an item
3. Show all items
4. Exit
Choice: 1
Enter ID: 102
Description: Black umbrella
E-mail: alice@univ.edu
1. Add new item
2. Remove an item
3. Show all items
4. Exit
Choice: 3
ID: 102   Desc: Black umbrella   Found-by: alice@univ.edu
1. Add new item
2. Remove an item
3. Show all items
4. Exit
Choice: 4
```
(program ends)

### CONSTRAINTS
- You must define a `struct` to represent one lost-and-found item.  
- All list operations (add, remove, show) must be implemented in **one** user-defined function besides `main()`; `main()` itself should only handle the menu loop and call that helper function with appropriate arguments.  
- Menu option **4** is the required EXIT keyword.

---

## Problem 63 - moonshotai/kimi-k2-instruct-0905 - Iteration 13
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)  

**Background Story**  
The campus library is replacing its old card‐catalog with a tiny digital system for storing book records.  
You volunteer to write a demo program that keeps an *expandable* collection of books in **heap memory**.  
Each book has a unique accession number, title, and author.  
The librarian must be able to add books, list all of them, delete a book by accession number, and quit.

**Precise Functional Requirements**  
1. On startup the program holds **zero** books.  
2. Present a simple numbered menu:  
   1) Add Book  
   2) List Books  
   3) Delete Book  
   4) Exit  
3. Choosing **1** prompts for:  
   - accession number (positive int, unique)  
   - title (single‐line string ≤80 chars)  
   - author (single‐line string ≤50 chars)  
   Then dynamically allocate a new book record and append it to the collection.  
4. Choosing **2** prints every book in the order added, one per line:  
   `<AccNo> — <Title> by <Author>`  
   (If none exist, print “Collection empty.”)  
5. Choosing **3** prompts for an accession number.  
   - If it exists, free its memory, shrink the collection logically, and print “Deleted.”  
   - Otherwise print “Not found.”  
6. Choosing **4** frees *all* remaining heap blocks and terminates with “Good-bye.”  
7. After any operation, re-display the menu unless the user chose 4.  

**Simple Example Run**  
( user input after `>` )  

```
1) Add Book
2) List Books
3) Delete Book
4) Exit
> 1
Accession number> 1001
Title> The C Programming Language
Author> Kernighan & Ritchie
1) Add Book
2) List Books
3) Delete Book
4) Exit
> 2
1001 — The C Programming Language by Kernighan & Ritchie
1) Add Book
2) List Books
3) Delete Book
4) Exit
> 4
Good-bye.
```

### CONSTRAINTS  
- You **must** define a `struct Book` to represent each book entity.  
- You **must** store the collection as a dynamically‐allocated *array* of pointers to `struct Book` (i.e., `struct Book **library`).  
- The only functions besides `main()` allowed are:  
  – `void displayLibrary(struct Book **lib, int count)`  
  – `void freeLibrary(struct Book **lib, int count)`  
- Menu option **4** is the *sole* way to exit; typing 4 must free every allocated block before termination.

---

## Problem 64 - moonshotai/kimi-k2-instruct-0905 - Iteration 14
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)  

Story  
You are helping a tiny village library that still checks books out by hand.  
Every afternoon the librarian types the day’s new titles into your program.  
Your program must store the list in memory only while it is running; the librarian will NOT save anything to disk.  
When the librarian closes the program every byte must be freed again.

Task  
Write a small console program that:

1. keeps a list of books  
2. lets the librarian add one book at a time  
3. prints the whole catalogue on request  
4. exits when finished and frees every malloc’ed byte

Input / Output  
Each line is either  
   add <title>  
or  
   list  

Example  
add Alice in Wonderland  
add Through the Looking-Glass  
list  
Alice in Wonderland  
Through the Looking-Glass  
add  
list  
Alice in Wonderland  
Through the Looking-Glass  
exit  

Constraints  
- Must use a struct to represent a book.  
- Must use malloc/free; no global arrays.  
- Must display one book via displayEntity().  
- Must implement only one function besides main().

---

## Problem 65 - moonshotai/kimi-k2-instruct-0905 - Iteration 15
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Background  
A tiny campus library has just donated its old card-catalogue to the CS department. Each drawer is full of blank 3 × 5 index cards. You are to write a console program that lets the librarian create an arbitrary number of “drawers” (dynamic arrays) of cards on the fly. The only fields stored on each card are an integer card‐ID and a 3-character string title (title fits exactly on the card). The program must keep track of how many cards are currently in each drawer and must be able to add, delete, or list cards.

Requirements  
1. The program must start with an empty library (no drawers).  
2. The user can type commands:  
   - `add <card-ID> <3-char-title>` – add a new card  
   - `list` – print every card currently stored  
   - `exit` – quit and free everything  
3. The program must allocate exactly the space needed for each card (no fixed arrays).  
4. No global variables allowed.

Example  
Input  
```
add 107 cat  
add 105 dog  
list  
exit
```
Output  
```
107 cat  
105 dog
```

### CONSTRAINTS  
- Must use a `struct` to represent a single card.  
- Must implement a function `displayEntity(int cardID, char title[3])` that prints one card.  
- Must implement only one function besides `main()` (displayEntity).

---

## Problem 66 - moonshotai/kimi-k2-instruct-0905 - Iteration 16
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

You are the owner of a tiny student library that keeps every book on a single shelf.  
When a student brings a new book, you place it on the first free slot you find.  
When a student returns a book, you erase its title and mark the slot as empty.  
All memory must be managed manually with malloc and free.

Write a program that simulates this shelf.

### CONSTRAINTS  
1. Must use a struct Book { char title[50]; } to represent one slot.  
2. Must use a single function besides main(): void displayEntity(int index).  
3. Must implement a menu with options 0-3 and option 0 must EXIT the program.

---

## Problem 67 - moonshotai/kimi-k2-instruct-0905 - Iteration 17
# STEP 1: PROBLEM

**Background Story**  
The campus library just bought a crate of second-hand books.  
Each book has three attributes: title (≤50 chars), author (≤30 chars), and year of publication (int).  
Because the librarian does not know how many books are inside the crate, your program must keep the records in dynamically-allocated memory (malloc) and be able to release that memory (free) when the user closes the program.

**Required Behaviour**  
1. The program starts with an empty catalogue.  
2. A simple text menu repeats until the user chooses to exit:  
   1. Add a new book (read title, author, and year).  
   2. List all books in the order they were added.  
   3. Remove the last added book (LIFO discard).  
   4. Exit.  
3. After every operation the menu is re-displayed.  
4. On exit, every dynamically-allocated byte must be freed.

**Simple Example Run**  
(“>” is the prompt, user input is shown after the number)

```
1. Add book
2. List books
3. Remove last book
4. Exit
> 1
Title: The Pragmatic Programmer
Author: Hunt & Thomas
Year: 1999
1. Add book
2. List books
3. Remove last book
4. Exit
> 1
Title: Clean Code
Author: Robert C. Martin
Year: 2008
1. Add book
2. List books
3. Remove last book
4. Exit
> 2
1. The Pragmatic Programmer, Hunt & Thomas, 1999
2. Clean Code, Robert C. Martin, 2008
1. Add book
2. List books
3. Remove last book
4. Exit
> 3
Removed Clean Code
1. Add book
2. List books
3. Remove last book
4. Exit
> 4
Good-bye!
```

### CONSTRAINTS
- Must use a struct to represent a single book entity.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with a single function besides `main()`.  
- Menu option 4 is EXIT.

---

## Problem 68 - moonshotai/kimi-k2-instruct-0905 - Iteration 18
# STEP 1: PROBLEM  
**Topic: Dynamic Memory Allocation (malloc, free)**  

**Story**  
You are running a tiny pop-up coffee cart that only sells one item: a “cup” whose size is measured in millilitres. Customers can place an order (`add`), cancel an order (`remove`), or see what is currently in the cart (`list`). Every order is stored in a dynamically-allocated array that grows and shrinks as needed.

**Task**  
Write a console program that keeps an expandable array of orders, each order being a single integer (millilitres). The program must respond to three commands:  

- `add <mL>` → append one order to the cart  
- `remove` → delete the last order (LIFO)  
- `list` → print the current cart contents  

The cart starts empty. Every `add` must enlarge the array by one element; every `remove` must shrink it by one element. The array must be built entirely with `malloc`/`realloc` and released with `free`.

**Example**  
Input  
```
add 200
add 150
remove
add 100
list
```
Output  
```
200 100
```

### CONSTRAINTS  
1. Must use a single `struct` to represent the entire cart (e.g. `struct Cart`).  
2. Must implement exactly one helper function besides `main()`: `displayEntity` prints the millilitres of one order.  
3. No menu; commands are typed directly.

---

## Problem 69 - moonshotai/kimi-k2-instruct-0905 - Iteration 19
# STEP 1: PROBLEM

## Story
The tiny town of Stackville has just opened a public library.  
To keep track of its book collection, the head librarian has hired you to write a console program that stores book records in **dynamic memory**.  
Each book has a unique ID (positive integer), a title, and the number of copies on the shelf.  
All records must be kept only while the program is running; nothing is saved to disk.

## Functional Requirements
1. The program must start with an empty collection (i.e. no books are pre-loaded).  
2. The user is shown a menu with four options:  
   1. Add a new book  
   2. Remove a book by ID  
   3. List every book currently stored  
   4. Exit  
3. “Add” must prompt for ID, title, and copies, then store the new record in dynamically allocated memory.  
4. “Remove” must release the memory occupied by the chosen book.  
5. “List” must print ID, title, and copies for every book in the order they were added.  
6. The program must free **all** remaining memory before terminating.  
7. Handle invalid menu choices gracefully by re-printing the menu.

## Example Session (user input in bold)
```
=== Stackville Library ===
1. Add book
2. Remove book
3. List books
4. Exit
Choice: **1**
Enter ID: **101**
Enter title: **The C Programming Language**
Enter copies: **3**
Book added.

1. Add book
2. Remove book
3. List books
4. Exit
Choice: **3**
ID: 101, Title: The C Programming Language, Copies: 3

1. Add book
2. Remove book
3. List books
4. Exit
Choice: **4**
Good-bye!
```

### CONSTRAINTS
- You must define a `struct Book` to represent the primary data entity.  
- Add and Remove must be handled by a single helper function  
  `void updateCollection(struct Book **collection, int *size, int choice)`;  
  no other functions besides `main()` are allowed.  
- The EXIT option is number **4** and must be clearly listed in the menu.

---

## Problem 70 - moonshotai/kimi-k2-instruct-0905 - Iteration 20
# STEP 1: PROBLEM

## Context
A small public library has just received a donation of old computers and wants to catalogue them while they are being refurbished. Each computer is identified by a unique integer ID, the year it was built, and the amount of RAM (in GB). The librarian needs a simple console program that can add a new computer, show the current catalogue, or exit. Because the number of computers is unknown at compile time, you must allocate and free memory dynamically.

## Requirements
1. The program must keep all computer records in dynamic memory.
2. The program must provide a text menu with the following options:
   - 1) Add Computer
   - 2) Show Catalogue
   - 3) Exit
3. Choosing “Add Computer” prompts the user for ID, year, and RAM, then stores the information.
4. Choosing “Show Catalogue” prints every stored computer in the order they were added, one per line, with the format:
   ```
   ID=123 Year=2015 RAM=8GB
   ```
   If no computers exist, print “No computers in catalogue.”
5. Choosing “Exit” frees all dynamically allocated memory and terminates the program.
6. Handle invalid menu choices with the message “Invalid option.” and re-display the menu.

## Example Run
```
1) Add Computer
2) Show Catalogue
3) Exit
Choice: 1
Enter ID: 101
Enter year: 2019
Enter RAM (GB): 16

1) Add Computer
2) Show Catalogue
3) Exit
Choice: 2
ID=101 Year=2019 RAM=16GB

1) Add Computer
2) Show Catalogue
3) Exit
Choice: 3
```

### CONSTRAINTS
- You must define a struct named `Computer` to represent each computer.
- All computer structs must be stored in a dynamically resizing array allocated with `malloc`/`realloc` and freed with `free`.
- Only two functions are allowed: `main` and `addComputer`.
- The menu option to exit the program is 3.

---

## Problem 71 - moonshotai/kimi-k2-instruct-0905 - Iteration 21
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

You have just been hired as the night-shift manager of a tiny, 24-hour underground parking garage.  
The garage contains exactly 100 parking spaces, numbered 1 … 100.  
Each space is either free or occupied by a single car.  
When a car arrives, the driver types a 4-digit year (e.g. 2023) and a 1 … 100 space number.  
When a car leaves, the system must erase that space and reclaim its memory.

Your job is to write a small C program that keeps an in-memory record of which spaces are occupied and by which year.  
The parking lot never grows beyond 100 spaces, so you must store only the occupied spaces and nothing else.

Requirements  
1. Represent one occupied space as a struct { int year; }.  
2. Use malloc to allocate one struct when a car arrives, and free to de-allocate when it leaves.  
3. Implement a single function void displayEntity(int space) that prints  
   “Space 42 occupied by car from 2023.”  
   or  
   “Space 42 is free.”  
4. main() must only call displayEntity; no other functions allowed.

Simple Example  
Input  
1 42 2023  
1 42 2023  
2 42  
3  

Output  
Space 42 occupied by car from 2023.  
Space 42 is free.  

### CONSTRAINTS  
- The solution must be implemented with exactly one function besides main().  
- Must use a struct to represent the primary data entity.  
- Menu option 3 is EXIT the program.

---

## Problem 72 - moonshotai/kimi-k2-instruct-0905 - Iteration 22
# STEP 1: PROBLEM  
“Memory-Mart” is a tiny convenience store that keeps its entire stock in the heap rather than on shelves. Every night the owner dynamically records what has just arrived and every morning throws away what has not been sold. Your job is to model this nightly inventory with nothing more than malloc, free and simple console I/O.

### Specification  
The program must:  
1. Keep a linked list of structs describing one product (name, quantity, price).  
2. Present a menu:  
   1. Add new product  
   2. Delete product by name  
   3. Display all products  
   4. EXIT  
3. After each “Add” the user enters: name, quantity, price.  
4. After each “Delete” the user enters a name; if it exists, remove the node and free its heap memory.  
5. Display must print every product in the list.  
6. EXIT immediately ends the program.

### Example Session  
(typed exactly as the student would see it)  
1  
apple 10 1.50  
1  
banana 5 0.75  
3  
apple 10 1.50  
banana 5 0.75  
2  
banana  
3  
apple 10 1.50  
4  
→ program ends

### CONSTRAINTS  
- Must include a menu option 4 to EXIT.  
- Use a struct to represent one product.  
- Logic for displaying the entire list must be in a function called displayList.

---

## Problem 73 - moonshotai/kimi-k2-instruct-0905 - Iteration 23
# STEP 1: PROBLEM

## Background Story
You have just been hired as the “Memory Keeper” for the campus library.  
Instead of shelves, the library stores its electronic books (e-books) in dynamically allocated memory.  
Every time a new e-book is donated, you must allocate space for its metadata (title, author, file-size in KiB).  
When an e-book is withdrawn, you must reclaim that memory.  
Your job is to write a tiny, menu-driven console program that lets student volunteers add, list, and withdraw e-books while correctly using malloc and free.

## Functional Requirements
1. The program starts with an empty collection of e-books.
2. Implement a menu with the following choices:
   1) Add e-book
   2) List all e-books
   3) Withdraw e-book (by array index, 0-based)
   4) Exit program (keyword `4`)
3. “Add e-book” reads title (≤30 chars, no spaces), author (≤30 chars, no spaces), and file-size (positive integer).  
   Dynamically allocate one struct for the new e-book and append its pointer to a dynamically allocated array of pointers.
4. “List all e-books” prints every e-book in insertion order, showing index, title, author, and size.  
   If the collection is empty, print `Collection empty.`
5. “Withdraw e-book” removes the e-book at the given index, frees its memory, compacts the pointer array, and updates counters.  
   If the index is invalid, print `Invalid index.`
6. On Exit, free every remaining allocated object (no memory leaks).

## Example Input/Output
```
=== E-Book Memory Keeper ===
1) Add e-book
2) List e-books
3) Withdraw e-book
4) Exit
Choice: 1
Title: C_Programming
Author: King
Size: 2048
Choice: 1
Title: Python_Crash
Author: Matthes
Size: 1536
Choice: 2
0: C_Programming by King (2048 KiB)
1: Python_Crash by Matthes (1536 KiB)
Choice: 3
Index to withdraw: 0
Choice: 2
0: Python_Crash by Matthes (1536 KiB)
Choice: 4
Goodbye!
```

### CONSTRAINTS
- Must use a `struct` to represent each e-book.
- The logic for listing a single e-book must be in a function called `displayEntity`.
- The only functions allowed are `main` and `displayEntity`.
- Menu option 4 must exit the program.

---

## Problem 74 - moonshotai/kimi-k2-instruct-0905 - Iteration 24
# STEP 1: PROBLEM  
Dynamic Memory Allocation (malloc, free) – “Library‐of‐Everything”

Background  
Imagine a tiny public library that has only ONE shelf.  Every book is identified by its title (a single word, no spaces, ≤ 30 characters).  When a new book arrives the librarian places it on the shelf; when a book is borrowed the librarian removes it from the shelf and frees the memory.  The librarian never keeps more than one copy of any title.

Task  
Write a program that simulates this ultra‐minimal library.  The program must keep the shelf in dynamic memory and must be able to:  
1. Add a new book (malloc).  
2. Borrow a book (free).  
3. Print the current shelf.  

Requirements  
1. The shelf is represented as a dynamically allocated array of strings (titles).  
2. The program must add and remove books only by malloc/free.  
3. The program must print the current shelf.  
4. The program must exit when the user chooses EXIT.

Example  
Input  
```
1 add Harry  
1 add Potter  
1 add  
2 borrow Harry  
3 shelf  
4 exit  
```
Output  
```
Current shelf:  
Potter  
```

### CONSTRAINTS  
1. Must use a struct to represent the library.  
2. Logic for displaying the details of ONE specific entity must be in a function called displayEntity.  
3. The solution must be implemented with a single function besides main().

---

## Problem 75 - moonshotai/kimi-k2-instruct-0905 - Iteration 25
# STEP 1: PROBLEM

## Background Story
You are helping the campus library move from paper cards to a tiny digital index.  
They only care about one thing right now: keeping track of how many copies of each book are currently on the shelf.  
Because the librarian is never sure how many titles will be entered on a given day, the list must grow on demand.

## Requirements
1. The program starts with an empty list of books.
2. It repeatedly asks the user to choose one of the following actions:
   1. Add a new book title (allocate space, store the title string and an initial copy-count).
   2. Increase the copy-count of an existing title by 1.
   3. Decrease the copy-count of an existing title by 1 (never let it go below 0).
   4. Display the current list of all titles and their copy-counts.
   5. Exit the program (and free every malloc’d block before termination).
3. All dynamically allocated memory must be released before the program ends.
4. Assume titles are unique; case-sensitive matching is fine.

## Simple Example of Expected Input/Output
```
1
Introduction to Algorithms
3
1
Operating Systems
2
2
Operating Systems
4
5
```
Output (after the last command):
```
Introduction to Algorithms : 3
Operating Systems        : 3
```
Program terminates cleanly.

### CONSTRAINTS
- Every book must be represented by a `struct Book` containing at least the fields `title` (char *) and `copies` (int).
- All dynamic allocation must be done with `malloc`/`realloc`; every block must be freed before the program exits.
- Logic that prints the details of ONE specific book must be placed in a separate function called `displayBook`.
- The menu option to exit the program is number 5.

---

## Problem 76 - moonshotai/kimi-k2-instruct-0905 - Iteration 26
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Background  
A small library wants to keep track of the books that are currently on the shelf. Each book has a title (≤30 characters) and an integer ID. The librarian will type commands into a console program that must keep an up-to-date list of books, storing the data only in dynamically allocated memory.

Requirements  
1. Implement a tiny “shelf” that can grow or shrink at run-time.  
2. The program must support three commands:  
   - `add <title> <id>` – append a new book to the shelf.  
   - `remove <id>` – delete the book with the given ID (if it exists).  
   - `exit` – free everything and terminate.  
3. After every command the program prints the current list of books in order of insertion (one per line: `<id> <title>`).  
4. All data must be stored in dynamically allocated memory; no fixed-size arrays.

Simple Example  
Input  
```
add Moby_Dick 42  
add Hamlet 17  
remove 42  
exit  
```
Output  
```
42 Moby_Dick  
17 Hamlet  
```
Input  
```
remove 99  
exit  
```
Output  
```
```

### CONSTRAINTS  
- Must use a struct to represent a book.  
- Must use a single function besides main().  
- Must free all memory before exiting.

---

## Problem 77 - moonshotai/kimi-k2-instruct-0905 - Iteration 27
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Story  
A small campus library has just bought a handful of identical books each week.  
You are the volunteer who records how many identical copies arrived that week and stores the week’s data in a simple catalogue.  
Each week you also decide whether to keep the catalogue or throw it away.

Precise Requirements  
1. Allocate space for one week’s worth of identical books at a time.  
2. Keep a list of weeks that are still in the catalogue.  
3. Free any week that is removed from the catalogue.  
4. At the end, free everything that is still in the catalogue.

Input/Output  
Each line is either  
   + <week> <copies>  
or  
   − <week>  

+ means “add week to catalogue” (allocate)  
− means “remove week from catalogue” (free)  

Example  
Input  
+ 1 5  
+ 2 4  
− 2  
+ 3 6  

Output  
1 5  
3 6  

### CONSTRAINTS  
1. A single struct must represent a week.  
2. The catalogue must be an array of pointers to these structs.  
3. You may not use any STL containers.  
4. You must use malloc and free only.

---

## Problem 78 - moonshotai/kimi-k2-instruct-0905 - Iteration 28
# STEP 1: PROBLEM  
Topic: Dynamic Memory Allocation (malloc, free)

Background  
A tiny library has just hired you to automate their catalogue.  
Each book is described by three strings: title, author, and ISBN.  
The librarian will type the details of any number of books (until she decides to stop).  
Your program must store these books in memory and print them back in the same order.

Requirements  
1. Allocate space for each book dynamically (malloc).  
2. Store all books in a contiguous block (array).  
3. When the librarian finishes, print the list in the order received.  
4. Free all allocated memory before the program ends.

Example  
Input  
How many books? 2  
Book 1:  
Title: The Catcher  
Author: John  
ISBN: 001  
Book 2:  
Title: The Catcher  
Author: Jane  
ISBN: 002  

Output  
Book 1  
Title: The Catcher  
Author: John  
ISBN: 001  
Book 2  
Title: The Catcher  
Author: Jane  
ISBN: 002  

### CONSTRAINTS  
- Must use a struct Book.  
- Must allocate space for each book dynamically.  
- Must print each book in the order received.  
- Must free all allocated memory.

---

## Problem 79 - moonshotai/kimi-k2-instruct-0905 - Iteration 29
# STEP 1: PROBLEM

## Context
You have just joined the university’s “Retro Game Preservation Club.”  
The club keeps a small, hand-curated collection of classic 8-bit games.  
Each game is stored as a cartridge that has only three fields:  
- a unique ID number (int)  
- the year it was released (int)  
- the number of hours the club has logged playing it (double)

Because the collection grows and shrinks as new donations arrive and old ones are traded away, the club needs a tiny inventory manager that uses dynamic memory allocation (`malloc`, `free`) to store the cartridges. No static arrays are allowed.

## Requirements
1. On startup the collection is empty.
2. The program repeatedly offers a menu:
   1) Add a new cartridge  
   2) Remove a cartridge by ID  
   3) Show every cartridge (one per line: ID, year, hours)  
   4) EXIT  
3. After every successful operation the menu re-appears.  
4. All cartridge data must live in dynamically allocated memory.  
5. When the user chooses EXIT every allocated byte must be released.

## Simple Example Run
```
=== Retro Cartridge Manager ===
1) Add cartridge
2) Remove cartridge
3) List cartridges
4) EXIT
Choice: 1
Enter ID: 101
Enter year: 1985
Enter hours played: 12.5
Cartridge added.

1) Add cartridge
2) Remove cartridge
3) List cartridges
4) EXIT
Choice: 3
ID: 101  Year: 1985  Hours: 12.50

1) Add cartridge
2) Remove cartridge
3) List cartridges
4) EXIT
Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must represent each cartridge with a `struct` named `Cartridge`.  
- The only functions besides `main()` you may write are:  
  – `void displayCartridge(const struct Cartridge *c)` which prints one cartridge in the exact format shown above.  
  – Any helper you need for memory management (but no other “logic” functions).

---

## Problem 80 - moonshotai/kimi-k2-instruct-0905 - Iteration 30
# STEP 1: PROBLEM

## Background Story
You are helping the campus library build a tiny, self-service kiosk that lets students register the books they are donating.  
Because the number of donations is unknown in advance, the program must keep the registry in dynamically-allocated memory.  
Each book is recorded only once; if the same ISBN appears again the kiosk simply ignores the duplicate.

## Functional Requirements
1. On startup the registry is empty.
2. The program repeatedly shows a menu:
   1) Add a donated book  
   2) List all donated books  
   3) Remove a book by ISBN  
   4) Exit
3. Adding a book stores:
   - title (single string, ≤80 characters)  
   - author (single string, ≤50 characters)  
   - ISBN  (13-digit string, no spaces)  
   - year  (positive integer)  
   Duplicate ISBNs must be rejected with the message “Book already registered.”
4. Listing prints the books in the order they were added, one line per book with a single space between fields:
   `title author ISBN year`
5. Removing deletes the first book with the given ISBN and compacts the array.  
   If no such ISBN exists, print “Book not found.”
6. Before terminating, all dynamically allocated memory must be released.

## Example Session (user input after ">")
```
1) Add  2) List  3) Remove  4) Exit
> 1
Title: Clean Code
Author: Robert C. Martin
ISBN: 9780132350884
Year: 2008
Book added.

1) Add  2) List  3) Remove  4) Exit
> 1
Title: Clean Code
Author: Robert C. Martin
ISBN: 9780132350884
Year: 2008
Book already registered.

1) Add  2) List  3) Remove  4) Exit
> 2
Clean Code Robert C. Martin 9780132350884 2008

1) Add  2) List  3) Remove  4) Exit
> 3
ISBN: 9780132350884
Book removed.

1) Add  2) List  3) Remove  4) Exit
> 2
(nothing printed – registry is empty)

1) Add  2) List  3) Remove  4) Exit
> 4
Goodbye.
```

### CONSTRAINTS
- A single `struct` must represent a book.
- All book data must be kept in one dynamically-allocated array of `struct`.
- The only functions allowed besides `main()` are:
  - `addBook(...)`
  - `listBooks(...)`
  - `removeBook(...)`
  - `freeRegistry(...)`
- Menu option 4 is the only way to exit; typing 4 must terminate the program cleanly.

---

## Problem 81 - llama-3.3-70b-versatile - Iteration 16
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library's catalog system needs to be updated to efficiently store and manage book information. The system should utilize dynamic memory allocation to store book details.

## BACKGROUND
The library has a diverse collection of books, and the catalog system needs to store information such as the book's title, author, publication year, and genre. The system should allow users to add new books, display all books, and search for specific books by title or author.

## REQUIREMENTS
The program should have the following functionality:
1. Add a new book to the catalog.
2. Display all books in the catalog.
3. Search for a book by title or author.
4. Remove a book from the catalog.

## EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a new book:
Title: "To Kill a Mockingbird"
Author: "Harper Lee"
Publication Year: 1960
Genre: "Fiction"

Display all books:
Title: "To Kill a Mockingbird", Author: "Harper Lee", Publication Year: 1960, Genre: "Fiction"

Search for a book by title: "To Kill a Mockingbird"
Title: "To Kill a Mockingbird", Author: "Harper Lee", Publication Year: 1960, Genre: "Fiction"

Remove a book:
Title: "To Kill a Mockingbird"
Book removed successfully.
```

### CONSTRAINTS
1. The solution must use a `struct` to represent a book, containing fields for title, author, publication year, and genre.
2. The logic for displaying the details of all books must be in a function called `displayCatalog`.
3. The program must include a menu with the following options:
   - Option 1: Add a new book
   - Option 2: Display all books
   - Option 3: Search for a book
   - Option 4: Remove a book
   - Option 5: EXIT the program
   The menu should be displayed repeatedly until the user chooses to EXIT the program by selecting Option 5.

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks.

---

## Problem 82 - llama-3.3-70b-versatile - Iteration 17
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a simple program to manage the books in your library. The library has a limited amount of memory to store information about the books, so you will use dynamic memory allocation to store the book details.

The program should allow you to add, remove, and display books in the library. Each book has a title, author, and publication year.

### REQUIREMENTS
1. The program should allow the user to add a new book to the library.
2. The program should allow the user to remove a book from the library by its title.
3. The program should allow the user to display all the books in the library.
4. The program should allow the user to display the details of a specific book by its title.

### EXAMPLE
If the user adds the following books:
- Title: "Book1", Author: "Author1", Year: 2000
- Title: "Book2", Author: "Author2", Year: 2001
- Title: "Book3", Author: "Author3", Year: 2002

The program should display:
- When displaying all books: 
  - "Book1" by Author1 (2000)
  - "Book2" by Author2 (2001)
  - "Book3" by Author3 (2002)
- When displaying a specific book (e.g., "Book2"): 
  - "Book2" by Author2 (2001)

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven program.
- The program must have the following menu options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- If a menu is implemented, the program must include a specific menu option to EXIT the program, which is option 5.

---

## Problem 83 - llama-3.3-70b-versatile - Iteration 18
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The librarian needs to store the title, author, and publication year of each book. Since the number of books is not fixed, the program should dynamically allocate memory for each book. The program should also allow the librarian to add, remove, and display books.

### BACKGROUND
The librarian has a collection of books and wants to use a computer program to manage the collection. The program should store the title, author, and publication year of each book.

### REQUIREMENTS
The program should have the following functionality:
1. Dynamically allocate memory for each book.
2. Allow the librarian to add a new book to the collection.
3. Allow the librarian to remove a book from the collection.
4. Allow the librarian to display all books in the collection.
5. Allow the librarian to display the details of a specific book.

### EXAMPLE
Example Input:
```
Add a book: Title - "Book1", Author - "Author1", Year - 2020
Add a book: Title - "Book2", Author - "Author2", Year - 2021
Display all books:
Book1 by Author1 (2020)
Book2 by Author2 (2021)
Remove a book: Title - "Book1"
Display all books:
Book2 by Author2 (2021)
```
Example Output:
```
Book added successfully!
Book added successfully!
Book1 by Author1 (2020)
Book2 by Author2 (2021)
Book removed successfully!
Book2 by Author2 (2021)
```

### CONSTRAINTS
* Must use a `struct` to represent a book.
* Logic for displaying the details of all books must be in a function called `displayAllBooks`.
* Logic for displaying the details of a specific book must be in a function called `displayBook`.
* The solution must be implemented with two functions besides `main()`: `addBook` and `removeBook`.
* The program must have a menu with the following options:
	1. Add a book
	2. Remove a book
	3. Display all books
	4. Display a specific book
	5. EXIT the program
* The program must free the dynamically allocated memory when a book is removed or when the program exits.

Note: The `EXIT` option should be clearly stated as option 5. When the user chooses option 5, the program should free all dynamically allocated memory and exit.

---

## Problem 84 - llama-3.3-70b-versatile - Iteration 19
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a system to manage the books in your library. You want to store the title, author, and year of publication for each book. Since the number of books is not fixed, you will use dynamic memory allocation to store the books.

The program should allow users to add, remove, and display books. When a user adds a book, the program should allocate memory for the new book and store its details. When a user removes a book, the program should free the memory allocated for that book.

### REQUIREMENTS
1. The program should allow users to add books with their title, author, and year of publication.
2. The program should allow users to remove books by their title.
3. The program should allow users to display all the books in the library.
4. The program should display a menu with options to add, remove, display books, and exit the program.

### EXAMPLE
If the user adds two books: "Book1" by "Author1" published in 2020, and "Book2" by "Author2" published in 2021, and then displays all books, the output should be:
```
Title: Book1
Author: Author1
Year: 2020
Title: Book2
Author: Author2
Year: 2021
```
If the user then removes "Book1" and displays all books again, the output should be:
```
Title: Book2
Author: Author2
Year: 2021
```

### CONSTRAINTS
1. Must use a `struct` to represent a book with its title, author, and year of publication.
2. Logic for displaying the details of all books must be in a function called `displayBooks`.
3. The solution must be implemented with a single function besides `main()` to handle the menu and user input, called `handleMenu`.
4. If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4.

### MENU CONSTRAINTS
If a menu is implemented, it should have the following options:
1. Add a book
2. Remove a book
3. Display all books
4. EXIT the program (by selecting option 4)

---

## Problem 85 - llama-3.3-70b-versatile - Iteration 20
# STEP 1: PROBLEM
In a library management system, books are the primary entities that need to be managed. The system should allow users to add, delete, and display book details. The details of each book include the title, author, and publication year. Since the number of books is not fixed and can vary dynamically, dynamic memory allocation using `malloc` and `free` should be utilized.

The system should provide a simple menu-driven interface for users to interact with the library management system. The requirements for the system's functionality are as follows:
1. Initialize an empty library.
2. Allow users to add new books to the library.
3. Allow users to delete a book by its title.
4. Display all books in the library.
5. Display the details of a specific book by its title.

### CONSTRAINTS
- Must use a `struct` to represent a book, containing fields for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for adding a new book must be in a function called `addBook`.
- The solution must include a menu with the following options:
  1. Add a new book
  2. Delete a book
  3. Display all books
  4. Display a specific book
  5. EXIT the program
- The program must handle memory allocation and deallocation properly to avoid memory leaks.

### EXAMPLE
Example Input/Output:
```
Menu:
1. Add a new book
2. Delete a book
3. Display all books
4. Display a specific book
5. EXIT

Choose an option: 1
Enter title: Harry Potter
Enter author: J.K. Rowling
Enter publication year: 1997

Choose an option: 3
Title: Harry Potter, Author: J.K. Rowling, Year: 1997

Choose an option: 5
```
Note: The above example illustrates a simple interaction with the system. The actual implementation should handle user inputs, validate data, and manage memory efficiently.

---

## Problem 86 - llama-3.3-70b-versatile - Iteration 21
# STEP 1: PROBLEM
You are the administrator of a university's student records system. The system needs to store information about each student, including their name, student ID, and GPA. Since the number of students is not fixed and can change dynamically, you want to use dynamic memory allocation to store the student records. 

The program should allow users to add, remove, and display student records. When adding a student record, the program should prompt the user for the student's name, ID, and GPA. When removing a student record, the program should prompt the user for the student's ID. When displaying student records, the program should display all the records or a specific record based on the user's choice.

### REQUIREMENTS
1. The program should have a menu-driven interface to add, remove, and display student records.
2. The program should use dynamic memory allocation to store student records.
3. The program should handle memory deallocation when removing a student record.
4. The program should validate user input for student ID and GPA.

### EXAMPLE
If the user chooses to add a student record with name "John Doe", ID "12345", and GPA "3.5", the program should store this information and display a confirmation message. If the user chooses to display all student records, the program should display the name, ID, and GPA of each student.

Example Input/Output:
```
Menu:
1. Add Student Record
2. Remove Student Record
3. Display All Student Records
4. Display Specific Student Record
5. EXIT

Choose an option: 1
Enter student name: John Doe
Enter student ID: 12345
Enter student GPA: 3.5
Student record added successfully.

Choose an option: 3
Student Records:
Name: John Doe, ID: 12345, GPA: 3.5

Choose an option: 5
Exiting the program...
```

### CONSTRAINTS
1. Must use a `struct` to represent the student record.
2. Logic for displaying the details of one specific student record must be in a function called `displayStudent`.
3. The program must use dynamic memory allocation to store student records.
4. If a menu is implemented, the program must include a specific menu option to EXIT the program, which is option 5.

Note: The `struct` should have fields for student name, ID, and GPA. The `displayStudent` function should take a pointer to the student record as an argument and display the details of the student. The program should handle memory deallocation when removing a student record to prevent memory leaks.

---

## Problem 87 - llama-3.3-70b-versatile - Iteration 22
# STEP 1: PROBLEM
You are a librarian tasked with managing the inventory of books in a library. The library has a limited budget and can only store a certain number of books at a time. You need to create a program to manage the book inventory, allowing you to add, remove, and display books.

**Background Story:**
The library has a unique system where each book is represented by its title, author, and publication year. The librarian wants to be able to add new books to the inventory, remove books that are no longer needed, and display the details of all the books in the inventory.

**Requirements:**
1. The program must be able to dynamically allocate memory for each book.
2. The program must allow the user to add a new book to the inventory.
3. The program must allow the user to remove a book from the inventory by its title.
4. The program must display the details of all the books in the inventory.
5. The program must handle memory deallocation when a book is removed from the inventory.

**Example Input/Output:**
```
Menu:
1. Add Book
2. Remove Book
3. Display Books
4. Exit

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Choose an option: 3
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Choose an option: 2
Enter book title to remove: Harry Potter

Choose an option: 3
No books in inventory.

Choose an option: 4
Exiting program...
```

### CONSTRAINTS
* The solution must be implemented using a `struct` to represent each book.
* The logic for displaying the details of all books must be in a function called `displayBooks`.
* The program must have a menu with the following options:
	+ 1: Add Book
	+ 2: Remove Book
	+ 3: Display Books
	+ 4: Exit
* The program must exit when the user chooses option 4 (Exit).
* The program must use `malloc` and `free` for dynamic memory allocation and deallocation.

---

## Problem 88 - llama-3.3-70b-versatile - Iteration 23
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. To efficiently manage the books and their corresponding borrowers, you decide to create a program that utilizes dynamic memory allocation. The program will store information about the books and their borrowers, and perform operations to add, remove, and display this information.

The library has a collection of books with unique IDs, titles, authors, and the names of the borrowers. The program should be able to handle the following operations:
1. Add a new book to the collection, along with its details (ID, title, author, and borrower).
2. Remove a book from the collection by its ID.
3. Display the details of all the books in the collection.
4. Display the details of a specific book by its ID.

### CONSTRAINTS
- The program must use a `struct` to represent a book, which includes the ID, title, author, and borrower.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented with at least two functions besides `main()`.
- If a menu is implemented, it must include the following options:
  - Option 1: Add a new book
  - Option 2: Remove a book
  - Option 3: Display all books
  - Option 4: Display a specific book
  - Option 5: EXIT the program
  To exit the program, the user must select Option 5.

### EXAMPLE
Example Input:
```
1. Add a new book with ID: 1, title: "Book1", author: "Author1", borrower: "Borrower1"
2. Add a new book with ID: 2, title: "Book2", author: "Author2", borrower: "Borrower2"
3. Display all books
```
Example Output:
```
Book 1:
ID: 1
Title: Book1
Author: Author1
Borrower: Borrower1

Book 2:
ID: 2
Title: Book2
Author: Author2
Borrower: Borrower2
```
This program will help the library to efficiently manage its collection of books and borrowers, and provide a simple and user-friendly interface for the library manager to perform various operations.

---

## Problem 89 - llama-3.3-70b-versatile - Iteration 24
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. The library has a collection of books, and each book has a title, author, and status (available or borrowed). The library wants to create a system to manage its book collection using dynamic memory allocation.

The system should allow the librarian to add new books, remove existing books, display all books, and search for a specific book by title or author.

### REQUIREMENTS
1. The system should store the book collection in a dynamically allocated array of structures, where each structure represents a book with its title, author, and status.
2. The system should have the following functionalities:
   - Add a new book to the collection
   - Remove a book from the collection
   - Display all books in the collection
   - Search for a book by title or author
3. The system should handle memory allocation and deallocation properly to avoid memory leaks.

### EXAMPLE
Input:
```
Add book: "Harry Potter" by "J.K. Rowling"
Add book: "The Lord of the Rings" by "J.R.R. Tolkien"
Display all books
Search for book by title: "Harry Potter"
Remove book: "The Lord of the Rings"
Display all books
```
Output:
```
Book 1: "Harry Potter" by "J.K. Rowling" (available)
Book 2: "The Lord of the Rings" by "J.R.R. Tolkien" (available)
Book found: "Harry Potter" by "J.K. Rowling" (available)
Book removed: "The Lord of the Rings"
Book 1: "Harry Potter" by "J.K. Rowling" (available)
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The solution must include a menu with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. EXIT (to exit the program)
- The menu option to exit the program is option 5 (EXIT). 

Note: The program should handle invalid inputs and memory allocation errors properly.

---

## Problem 90 - llama-3.3-70b-versatile - Iteration 25
# STEP 1: PROBLEM
In a university setting, the management wants to keep track of the books in its library using a dynamic memory allocation system. The system should be able to add, remove, and display books. Each book has a unique ID, title, author, and publication year.

The program should be designed to manage the library's book collection efficiently. The following requirements must be met:
1. The program should allow users to add a new book to the collection.
2. The program should allow users to remove a book from the collection by its ID.
3. The program should allow users to display all the books in the collection.
4. The program should allow users to search for a book by its ID and display its details.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle all the menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a new book
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter publication year: 2020

2. Add a new book
Enter book ID: 2
Enter book title: Data Structures
Enter book author: Jane Smith
Enter publication year: 2019

3. Display all books
Book ID: 1, Title: Introduction to CS, Author: John Doe, Year: 2020
Book ID: 2, Title: Data Structures, Author: Jane Smith, Year: 2019

4. Search for a book by ID
Enter book ID: 1
Book ID: 1, Title: Introduction to CS, Author: John Doe, Year: 2020

5. Exit
```
Example Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book by ID
5. Exit

Choose an option: 
```

---

## Problem 91 - llama-3.3-70b-versatile - Iteration 26
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. To keep track of the books and their borrowers, you need to develop a program that utilizes dynamic memory allocation. The program should store information about each book, including its title, author, and borrower's name (if the book is borrowed).

## BACKGROUND
The library has a collection of books, and each book can be borrowed by a member. When a book is borrowed, the program should record the borrower's name. If a book is returned, the borrower's name should be removed from the record.

## REQUIREMENTS
The program's functionality should include the following:
1. Add a new book to the collection with its title, author, and initially, no borrower.
2. Borrow a book by specifying the book's title and the borrower's name.
3. Return a book by specifying the book's title.
4. Display all books in the collection, including their titles, authors, and borrowers (if any).
5. Display the details of a specific book by its title.

## EXAMPLE INPUT/OUTPUT
Example input:
- Add book: "Introduction to CS" by "John Doe"
- Borrow book: "Introduction to CS" by "Jane Smith"
- Return book: "Introduction to CS"
- Display all books
- Display book: "Introduction to CS"

Example output:
- After adding the book: "Book added successfully: Introduction to CS by John Doe"
- After borrowing the book: "Book borrowed successfully: Introduction to CS by Jane Smith"
- After returning the book: "Book returned successfully: Introduction to CS"
- Display all books: A list of all books with their titles, authors, and borrowers (if any).
- Display book: Details of the specified book, including title, author, and borrower (if any).

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book, which includes the title, author, and borrower's name.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The program must include a menu with the following options:
  1. Add a new book
  2. Borrow a book
  3. Return a book
  4. Display all books
  5. Display a specific book
  6. EXIT (to exit the program)
- The program must use dynamic memory allocation (`malloc`, `free`) to manage the collection of books.

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks.

---

## Problem 92 - llama-3.3-70b-versatile - Iteration 27
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. The library has a collection of books, and you want to create a program to manage the catalog. The program should allow you to add, remove, and display the details of books in the catalog.

The background story is that the library has just started, and you need to create a system to manage the books. You have decided to use dynamic memory allocation to store the book details, as the number of books can vary.

Here are the requirements for the program's functionality:
1. The program should allow you to add a new book to the catalog. Each book has a title, author, and publication year.
2. The program should allow you to remove a book from the catalog by its title.
3. The program should allow you to display the details of all books in the catalog.
4. The program should allow you to search for a book by its title and display its details.

Here is a simple example of expected Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Choose an option: 3
Title: Harry Potter, Author: J.K. Rowling, Year: 1997

Choose an option: 5
Exiting the program...
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for adding a new book must be in a function called 'addBook'.
- The program must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit
- The program must exit when the user chooses option 5.
- The solution must be implemented using dynamic memory allocation (malloc, free) to store the book details.

---

## Problem 93 - llama-3.3-70b-versatile - Iteration 28
# STEP 1: PROBLEM
In a university setting, the management wants to create a simple system to manage the details of its faculty members. The system should be able to dynamically allocate memory for each faculty member and store their details such as name, age, department, and years of experience. The system should also be able to display the details of all faculty members and free the allocated memory when the program terminates.

The background story is that the university has a growing number of faculty members, and the management wants a system that can efficiently store and manage their details without wasting memory.

The program's functionality requirements are as follows:
1. The program should dynamically allocate memory for each faculty member using malloc.
2. The program should store the details of each faculty member, including name, age, department, and years of experience.
3. The program should display the details of all faculty members.
4. The program should free the allocated memory when the program terminates.

Here is a simple example of expected input/output:
```
Enter the number of faculty members: 2
Enter name: John Doe
Enter age: 30
Enter department: Computer Science
Enter years of experience: 5
Enter name: Jane Doe
Enter age: 25
Enter department: Mathematics
Enter years of experience: 3
Faculty Member 1:
Name: John Doe
Age: 30
Department: Computer Science
Years of Experience: 5
Faculty Member 2:
Name: Jane Doe
Age: 25
Department: Mathematics
Years of Experience: 3
```

### CONSTRAINTS
- The solution must be implemented using a struct to represent the faculty member.
- The logic for displaying the details of all faculty members must be in a function called `displayFaculty`.
- The solution must include a menu with the following options:
  1. Add Faculty Member
  2. Display Faculty Members
  3. Exit
- The program must exit when the user selects the "Exit" option (option 3).
- The program must free the allocated memory when the program terminates.

---

## Problem 94 - llama-3.3-70b-versatile - Iteration 29
# STEP 1: PROBLEM
In a small library, books are stored on shelves. Each book has a unique title, author, and publication year. The librarian wants a program to manage the library's book collection. The program should allow the librarian to add, remove, and display books. Since the number of books is dynamic, the program will use dynamic memory allocation to store the book collection.

The program's functionality should include:
1. Adding a new book to the collection: The librarian will input the title, author, and publication year of the new book.
2. Removing a book from the collection: The librarian will input the title of the book to be removed.
3. Displaying all books in the collection: The program will display the title, author, and publication year of each book.
4. Displaying a specific book's details: The librarian will input the title of the book, and the program will display its details.

### EXAMPLE
If the librarian adds two books: "Book1" by "Author1" published in 2020, and "Book2" by "Author2" published in 2021, the program should display the following when the librarian chooses to display all books:
```
Book1 by Author1 (2020)
Book2 by Author2 (2021)
```
If the librarian chooses to display the details of "Book1", the program should display:
```
Book1 by Author1 (2020)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- The logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book's details
  5. EXIT (to exit the program)
- The menu option to EXIT the program is option 5. 

Note: The program should handle cases where the librarian tries to remove or display a book that does not exist in the collection. In such cases, the program should display an error message.

---

## Problem 95 - llama-3.3-70b-versatile - Iteration 30
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books using a dynamic memory allocation system. The system should allow the librarian to add, remove, and display books.

Background:
The library has a large collection of books, and the number of books can vary. The librarian needs a system that can dynamically allocate memory to store the book details.

Requirements:
1. The program should allow the librarian to add a new book to the collection.
2. The program should allow the librarian to remove a book from the collection.
3. The program should allow the librarian to display all the books in the collection.
4. The program should allow the librarian to search for a specific book by its title.

Example Input/Output:
```
Menu:
1. Add Book
2. Remove Book
3. Display Books
4. Search Book
5. Exit

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling

Choose an option: 3
Book 1:
Title: Harry Potter
Author: J.K. Rowling

Choose an option: 4
Enter book title to search: Harry Potter
Book found:
Title: Harry Potter
Author: J.K. Rowling
```

### CONSTRAINTS
1. Must use a `struct` to represent the book entity with fields for `title`, `author`, and `next` (a pointer to the next book in the collection).
2. The solution must be implemented with a single linked list.
3. The `addBook` function should dynamically allocate memory for the new book and add it to the end of the linked list.
4. The `removeBook` function should free the memory allocated for the book being removed.
5. The logic for displaying the details of all books must be in a function called `displayBooks`.
6. The program must include a menu with options to add, remove, display, search, and exit the program.
7. The menu option to exit the program must be option 5, labeled as "Exit".

### ADDITIONAL CONSTRAINTS IF MENU IS IMPLEMENTED
- The program must include a specific menu option to exit the program, which is option 5, labeled as "Exit". When this option is chosen, the program should free all the dynamically allocated memory and exit.

---

## Problem 96 - openai/gpt-oss-120b - Iteration 31
# STEP 1: PROBLEM  

## Background  
The city museum is modernising its catalogue system.  Each exhibit is described by a **name**, the **year** it was created, and its **estimated monetary value**.  The museum wants a small console program that can store an arbitrary number of exhibits while the program runs, allow the curator to add new entries, view the whole list, look up a single exhibit, and finally release all memory before the program ends.

You have just learned how to allocate and release memory with `malloc`/`free`, and how to bundle related data in a `struct`.  Write the required program using those tools.

## Requirements  

1. Define a `struct Exhibit` that contains:  
   * `char *name` – a dynamically allocated string (maximum length 100 characters).  
   * `int year` – the year the artifact was created.  
   * `double value` – estimated monetary value in dollars.  

2. When the program starts, it should present the user with a **menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   1. **Add a new exhibit** – Prompt for the name, year, and value, allocate a new `Exhibit`, and store it in a dynamically‑allocated array that grows as needed.  
   2. **List all exhibits** – Print the index (starting at 0) and all fields of every stored exhibit.  
   3. **Display a specific exhibit** – Ask for an index, then call a function `displayEntity` to print that exhibit’s details.  
   4. **Delete an exhibit** – Ask for an index, free the memory used for that exhibit’s name, shift the remaining elements left, and shrink the array accordingly.  
   5. **Exit** – Free **all** memory allocated for the array and for every exhibit’s name, then terminate the program.  

3. The program must **never leak memory**: every block obtained with `malloc` (or `realloc`) must be released with `free` before the program ends or when an exhibit is deleted.

4. Input validation is not required beyond ensuring the entered index is within the current range of stored exhibits.

## Example Interaction  

```
=== Museum Exhibit Manager ===
1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 1
Enter exhibit name: Ancient Vase
Enter year created: 1845
Enter estimated value: 1250.75
Exhibit added.

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 1
Enter exhibit name: Bronze Sword
Enter year created: 1020
Enter estimated value: 3400.00
Exhibit added.

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 2
[0] Name: Ancient Vase, Year: 1845, Value: $1250.75
[1] Name: Bronze Sword, Year: 1020, Value: $3400.00

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 3
Enter exhibit index: 1
--- Exhibit Details ---
Name : Bronze Sword
Year : 1020
Value: $3400.00

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 4
Enter exhibit index to delete: 0
Exhibit deleted.

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 2
[0] Name: Bronze Sword, Year: 1020, Value: $3400.00

1) Add a new exhibit
2) List all exhibits
3) Display a specific exhibit
4) Delete an exhibit
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct Exhibit` as described above.  
* **Function Requirement** – The logic for displaying the details of ONE specific exhibit must be placed in a function named `void displayEntity(const struct Exhibit *e);`.  
* **Menu Requirement** – The program must present a textual menu that includes a distinct option to **EXIT** the program (option 5 in the example).  
* **Memory Management** – All memory allocated with `malloc`/`realloc` must be released with `free` before the program terminates, and also when an exhibit is removed.  
* **Single‑File Implementation** – Apart from `main`, you may create additional helper functions, but the overall solution should be contained in a single source file.  

Write the program in C, adhering to the above specifications.

---

## Problem 97 - openai/gpt-oss-120b - Iteration 32
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “library‑catalog” program for a small community library.  
Each book in the catalog is described by three pieces of information:

* **ISBN** – a 13‑digit number (store as a string to keep leading zeros).  
* **Title** – up to 100 characters.  
* **Year** – the year of publication (integer).  

The library wants a command‑line, menu‑driven application that can add books, remove books, and display information about a single book on demand. Because the number of books is not known beforehand, you must allocate memory dynamically for each book record and for the list that holds the pointers to those records.

## Requirements  

Write a C program that satisfies the following functional specifications:

1. **Menu** – When the program starts, display a menu with the options:  
   1. Add a new book  
   2. Delete a book by ISBN  
   3. Show details of a book by ISBN  
   4. List all books (in the order they were added)  
   5. EXIT  

   The user selects an option by entering the corresponding number.

2. **Add a new book**  
   * Prompt the user for ISBN, Title, and Year.  
   * Allocate a `struct Book` dynamically (`malloc`).  
   * Store the data in the newly allocated structure.  
   * Store the pointer to this structure in a dynamically‑sized array (you may use a simple array that you `realloc` each time a book is added).  

3. **Delete a book by ISBN**  
   * Search the array for a book whose ISBN matches the user‑supplied ISBN.  
   * If found, free the memory that holds that `struct Book`.  
   * Remove the pointer from the array, shifting later elements forward, and shrink the array with `realloc`.  
   * If the ISBN is not present, print an informative message.

4. **Show details of a book by ISBN**  
   * Locate the book with the given ISBN.  
   * If found, call a function `displayBook` (see constraints) to print the book’s data.  
   * If not found, print an appropriate message.

5. **List all books**  
   * Iterate over the array and call `displayBook` for each stored book.

6. **EXIT**  
   * Before terminating, free every dynamically allocated `struct Book` and the array that holds the pointers.

## Example Interaction  

```
=== Library Catalog ===
1. Add a new book
2. Delete a book by ISBN
3. Show details of a book by ISBN
4. List all books
5. EXIT
Enter choice: 1
Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Year: 1978
Book added.

=== Library Catalog ===
1. Add a new book
2. Delete a book by ISBN
3. Show details of a book by ISBN
4. List all books
5. EXIT
Enter choice: 1
Enter ISBN: 9780262033848
Enter Title: Introduction to Algorithms
Enter Year: 2009
Book added.

=== Library Catalog ===
1. Add a new book
2. Delete a book by ISBN
3. Show details of a book by ISBN
4. List all books
5. EXIT
Enter choice: 4
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1978
ISBN: 9780262033848 | Title: Introduction to Algorithms | Year: 2009

=== Library Catalog ===
1. Add a new book
2. Delete a book by ISBN
3. Show details of a book by ISBN
4. List all books
5. EXIT
Enter choice: 3
Enter ISBN to display: 9780131103627
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1978

=== Library Catalog ===
1. Add a new book
2. Delete a book by ISBN
3. Show details of a book by ISBN
4. List all books
5. EXIT
Enter choice: 5
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be represented by a `struct` named `Book` containing the fields `char isbn[14];`, `char title[101];`, and `int year;`.  

* **Display function** – The logic for printing the details of **ONE** book must reside in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Memory management** – Every call to `malloc`/`realloc` must have a matching `free` before program termination. No memory leaks are permitted.  

* **Menu exit option** – The menu must include the option **5. EXIT** (as shown above). Selecting this option must cause the program to free all allocated memory and then terminate.  

* **Single‑source file** – The entire solution must be placed in one `.c` file and compile with a standard C compiler (C99 or later).  

* **Error handling** – The program should handle invalid menu choices and failed allocations gracefully, printing an error message and returning to the menu.  

---

## Problem 98 - openai/gpt-oss-120b - Iteration 33
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “student registry” utility for the campus computer lab.  
The lab’s computer must keep track of an arbitrary number of students that are entered during a single execution of the program. Because the number of students is not known beforehand, you must allocate and free memory dynamically using `malloc` and `free`.  

## Requirements  

Write a C program that implements the following functionality:

1. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit):
   * `1` – **Add a student**  
        * Prompt for the student’s **ID** (integer), **name** (string without spaces, max 30 characters), and **GPA** (float).  
        * Allocate a new `struct Student` on the heap, store the data, and insert it at the end of the current list.
   * `2` – **Display a student**  
        * Prompt for a student **ID**.  
        * Search the list; if the student exists, call the function `displayEntity` to print the student’s details (see below).  
        * If the ID is not found, print `Student not found.`  
   * `3` – **Remove a student**  
        * Prompt for a student **ID**.  
        * If the student exists, remove it from the list and `free` the associated memory.  
        * If the ID is not found, print `Student not found.`  
   * `4` – **List all students**  
        * Print the details of every student currently stored, in the order they were added.  
   * `5` – **Exit**  
        * Terminate the program after freeing **all** dynamically allocated memory.  

2. The program must **not** impose any fixed limit on the number of students; it should grow the list only as needed.

3. All allocated memory must be released before the program terminates (including when a student is removed).

4. The program should be robust against invalid menu choices (print `Invalid option.` and redisplay the menu).

## Example Interaction  

```
=== Student Registry ===
1) Add student
2) Display student
3) Remove student
4) List all students
5) Exit
Choose an option: 1
Enter ID: 101
Enter name: Alice
Enter GPA: 3.7
Student added.

=== Student Registry ===
1) Add student
2) Display student
3) Remove student
4) List all students
5) Exit
Choose an option: 1
Enter ID: 202
Enter name: Bob
Enter GPA: 3.2
Student added.

=== Student Registry ===
1) Add student
2) Display student
3) Remove student
4) List all students
5) Exit
Choose an option: 2
Enter ID to display: 101
--- Student Details ---
ID   : 101
Name : Alice
GPA  : 3.70

=== Student Registry ===
1) Add student
2) Display student
3) Remove student
4) List all students
5) Exit
Choose an option: 4
--- All Students ---
ID   : 101  Name : Alice  GPA : 3.70
ID   : 202  Name : Bob    GPA : 3.20

=== Student Registry ===
1) Add student
2) Display student
3) Remove student
4) List all students
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Student` containing at least the fields `int id; char name[31]; float gpa;`.  
* **Display Function** – The logic for printing the details of a single student must reside in a function with the exact prototype:  

  ```c
  void displayEntity(const struct Student *s);
  ```  

* **Memory Management** – Use only `malloc` (or `calloc`) and `free` for dynamic allocation; do **not** use global/static arrays to store the students.  
* **Menu Exit Option** – The menu must include an explicit option `5` (or the keyword `EXIT`) that terminates the program, satisfying the mandatory exit‑option constraint.  

*Optional (for extra credit):* Implement the list as a singly‑linked list; however, any dynamic container that respects the above constraints is acceptable.  

---

## Problem 99 - openai/gpt-oss-120b - Iteration 34
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “student registry” for the campus computer‑lab. The lab technician will run the program each day to add new students, remove students who have left, and view the details of a particular student. Because the number of students changes at run‑time, you must allocate and free memory dynamically.

## Program Requirements  

1. **Data Representation**  
   - Define a `struct Student` that stores:  
     - an integer `id` (unique identifier)  
     - a string `name` (maximum 30 characters)  
     - a floating‑point `gpa`  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   - **1. Add a student** – Prompt for `id`, `name`, and `gpa`. Allocate memory for a new `Student` and store it in a dynamically‑grown array (or linked list).  
   - **2. Remove a student** – Prompt for an `id`. Locate the matching `Student`, free its memory, and shrink the collection accordingly. If the `id` does not exist, print an appropriate message.  
   - **3. Display a student** – Prompt for an `id`. Locate the matching `Student` and call a function `displayStudent` (see Constraint) to print its details in the format shown below. If the `id` does not exist, print an appropriate message.  
   - **4. List all students** – Print the details of every stored student, one per line, in the order they were added.  
   - **5. EXIT** – Terminate the program, freeing any remaining allocated memory.  

3. **Input / Output**  
   - All interaction is via standard input and output.  
   - The program should be robust to invalid menu choices (print “Invalid option, try again.” and re‑display the menu).  

### Example Interaction  

```
--- Student Registry ---
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 101
Enter name: Alice
Enter GPA: 3.8
Student added.

--- Student Registry ---
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 102
Enter name: Bob
Enter GPA: 3.2
Student added.

--- Student Registry ---
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice, GPA: 3.80

--- Student Registry ---
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 4
ID: 101, Name: Alice, GPA: 3.80
ID: 102, Name: Bob, GPA: 3.20

--- Student Registry ---
1) Add a student
2) Remove a student
3) Display a student
4) List all students
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented with a `struct Student`.  
- **Display Function** – The logic for printing the details of a single student must reside in a function with the exact prototype:  

  ```c
  void displayStudent(const struct Student *s);
  ```  

- **Dynamic Allocation Only** – All `Student` objects must be created with `malloc` (or `calloc`) and released with `free`. No static or global arrays of fixed size may be used to store the students.  
- **Menu Exit Option** – The menu must contain an explicit option labeled **5) EXIT** (or the keyword “EXIT”) that ends the program after freeing any remaining allocated memory.  

*Optional:* You may implement the collection as a dynamically resized array (using `realloc`) or as a singly‑linked list; either approach satisfies the dynamic‑memory requirement.

---

## Problem 100 - openai/gpt-oss-120b - Iteration 35
# STEP 1: PROBLEM  

## Background  
The university library is modernizing its catalogue system. Each book record must be stored in dynamically allocated memory because the number of books is not known at compile‑time and can change while the program runs (books may be added or removed). Your task is to write a small console application that lets a librarian add new books, list all books, search for a book by its ISBN, and delete a book. All book information must be kept in a singly‑linked list that you build yourself using `malloc` and `free`.

## Requirements  

1. **Data Representation**  
   *Define a `struct Book` that contains the following fields:*  
   - `char title[101]` – title of the book (maximum 100 characters).  
   - `char author[51]` – author name (maximum 50 characters).  
   - `char isbn[14]` – ISBN‑13 string (13 characters + terminating null).  
   - `int copies` – number of copies available.  
   - `struct Book *next` – pointer to the next book in the list.  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   1. **Add a new book** – Prompt for title, author, ISBN, and number of copies; allocate a new `Book` node with `malloc` and insert it at the end of the list.  
   2. **List all books** – Traverse the list and print each book’s details on a separate line.  
   3. **Search by ISBN** – Ask for an ISBN, locate the matching node, and display its details using a dedicated function `displayBook`. If the ISBN is not found, print “Book not found.”  
   4. **Delete a book** – Ask for an ISBN, locate the node, remove it from the list, free its memory, and confirm deletion. If the ISBN does not exist, print “Book not found.”  
   5. **Exit** – Terminate the program, freeing any remaining allocated memory.  

3. **Input Validation**  
   - The program should not crash on malformed input; if a numeric entry is invalid, re‑prompt the user.  
   - ISBN strings must be exactly 13 characters long (you may assume the user follows this rule).  

4. **Memory Management**  
   - Every `malloc` must have a corresponding `free`.  
   - Before exiting, the program must free all nodes that are still allocated.  

## Example Interaction  

```
=== Library Catalogue ===
1. Add a new book
2. List all books
3. Search by ISBN
4. Delete a book
5. Exit
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN (13 chars): 9780131103627
Enter number of copies: 3
Book added successfully!

=== Library Catalogue ===
1. Add a new book
2. List all books
3. Search by ISBN
4. Delete a book
5. Exit
Choose an option: 2

Title: The C Programming Language | Author: Kernighan & Ritchie | ISBN: 9780131103627 | Copies: 3

=== Library Catalogue ===
1. Add a new book
2. List all books
3. Search by ISBN
4. Delete a book
5. Exit
Choose an option: 3

Enter ISBN to search: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
ISBN: 9780131103627
Copies: 3

=== Library Catalogue ===
1. Add a new book
2. List all books
3. Search by ISBN
4. Delete a book
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct Book` as described above.  
- **Function Requirement** – The logic for displaying the details of a single book must be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

- **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option must cause the program to terminate after freeing all allocated memory.  

- **Dynamic Allocation Only** – No static or global arrays may be used to store the books; all nodes must be obtained with `malloc` and released with `free`.  

- **Single‑File Implementation** – The entire solution must be contained in a single `.c` source file.  

- **Standard Library Only** – You may only use headers from the C standard library (`<stdio.h>`, `<stdlib.h>`, `<string.h>`, etc.). No third‑party libraries are allowed.  

---

