# Problem Batch Preview: Implementing Data Structures (e.g., Singly Linked Lists)
**Batch Number:** 3 | **Total Problems:** 100

---

## Problem 1 - openai/gpt-oss-120b - Iteration 51
# STEP 1: PROBLEM  

## Background  
The campus library is transitioning from paper‑based catalog cards to a simple digital system that runs on a command‑line interface. Each book in the collection is represented by a **record** containing its ISBN, title, and the number of copies currently available. Because the library’s collection is constantly changing—books are added, removed, or have their copy counts updated—the data must be stored in a structure that can grow and shrink efficiently.  

Your task is to implement this catalog using a **singly linked list**. The program will allow a librarian to perform basic operations through a text‑based menu.

## Requirements  
Write a C (or C++) program that provides the following functionality:

1. **Add a new book** to the front of the list.  
   - Prompt for ISBN (string, up to 13 characters), title (string, up to 100 characters), and copies (non‑negative integer).  
   - If a book with the same ISBN already exists, reject the insertion and display an error message.

2. **Remove a book** given its ISBN.  
   - Search the list; if the book is found, unlink it and free its memory.  
   - If the ISBN does not exist, display a “Book not found” message.

3. **Update the copy count** of an existing book.  
   - Prompt for ISBN and the new copy count.  
   - If the ISBN is not in the list, display an error.

4. **Display the details of a single book** identified by ISBN.  
   - The display logic **must** be encapsulated in a function named `displayBook`.

5. **List all books** in the order they appear in the linked list (from head to tail), showing ISBN, title, and copies for each entry.

6. **Exit** the program gracefully, releasing all allocated memory.

The program should repeatedly present the menu until the user chooses the exit option.

## Example Interaction  

```
=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Update copy count
4. Show a book by ISBN
5. List all books
6. Exit
Enter choice: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added successfully.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Update copy count
4. Show a book by ISBN
5. List all books
6. Exit
Enter choice: 5

Catalog contents:
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Update copy count
4. Show a book by ISBN
5. List all books
6. Exit
Enter choice: 6

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary data entity (a book) **must** be defined using a `struct` named `BookNode` that contains the ISBN, title, copy count, and a pointer to the next node.  
- **Display Function**: The logic for printing the details of a single book **must** be placed in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
- **Menu Implementation**: The menu must include an explicit option to **EXIT** the program (option `6` in the example). Selecting this option terminates the loop and frees all allocated memory.  
- **Memory Management**: Every node allocated with `malloc`/`new` must be freed before program termination; no memory leaks are permitted.  
- **Single‑Purpose Helper Functions**: Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the **only** function that directly prints a book’s details is `displayBook`.  

Follow these constraints closely; the grader will inspect the source code for compliance.

---

## Problem 2 - openai/gpt-oss-120b - Iteration 52
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple command‑line inventory manager for its **newly‑acquired collection of textbooks**.  Each textbook is identified by an ISBN, has a title, an author, and a quantity on hand.  The store’s IT intern has learned how a **singly linked list** works and has been asked to implement the inventory using that data structure.

## Requirements  
Write a C (or C++) program that manages the textbook inventory with a **menu‑driven interface**. The program must support the following operations:

1. **Add a new textbook** – Prompt the user for ISBN (string), title, author, and quantity, then insert the new node at the **head** of the list. If a textbook with the same ISBN already exists, update its quantity instead of adding a duplicate node.  
2. **Remove a textbook** – Prompt for an ISBN and delete the corresponding node from the list. If the ISBN is not found, display an appropriate message.  
3. **Search for a textbook** – Prompt for an ISBN and display the details of that textbook (ISBN, title, author, quantity). If not found, report it.  
4. **Display all textbooks** – Traverse the list and print the details of every node in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.

The menu must be displayed after each operation until the user chooses the **Exit** option.

## Example Input / Output  

```
=== Textbook Inventory Menu ===
1. Add textbook
2. Remove textbook
3. Search textbook
4. Display all textbooks
5. Exit
Enter choice: 1
Enter ISBN: 978-0131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter quantity: 3
Textbook added.

=== Textbook Inventory Menu ===
1. Add textbook
2. Remove textbook
3. Search textbook
4. Display all textbooks
5. Exit
Enter choice: 1
Enter ISBN: 978-0201633610
Enter title: Design Patterns
Enter author: Gamma et al.
Enter quantity: 5
Textbook added.

=== Textbook Inventory Menu ===
1. Add textbook
2. Remove textbook
3. Search textbook
4. Display all textbooks
5. Exit
Enter choice: 3
Enter ISBN to search: 978-0131103627
ISBN: 978-0131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Quantity: 3

=== Textbook Inventory Menu ===
1. Add textbook
2. Remove textbook
3. Search textbook
4. Display all textbooks
5. Exit
Enter choice: 4
--- Inventory List ---
ISBN: 978-0201633610 | Title: Design Patterns | Author: Gamma et al. | Qty: 5
ISBN: 978-0131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Qty: 3

=== Textbook Inventory Menu ===
1. Add textbook
2. Remove textbook
3. Search textbook
4. Display all textbooks
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary entity (textbook) **must be defined with a `struct`** (or `class` if using C++) containing at least the fields `isbn`, `title`, `author`, `quantity`, and a pointer to the next node.  
* **Display Function** – The logic that prints the details of **one specific textbook** (used by the Search operation) **must reside in a function named `displayBook`** (signature may be `void displayBook(const Book *b)` or equivalent).  
* **Menu Requirement** – The program **must present a menu** as shown above and **must include an explicit option to EXIT** (choice number 5 in the example). Selecting this option ends the program.  
* **Memory Management** – All dynamically allocated nodes must be freed before the program terminates.  
* **Single‑File Implementation** – Apart from `main`, you may create additional helper functions (e.g., `addBook`, `removeBook`, `searchBook`, `displayAll`, `displayBook`), but the entire solution must reside in a **single source file**.  

---  

Implement the described program, adhering to all constraints. Good luck!

---

## Problem 3 - openai/gpt-oss-120b - Iteration 53
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalogue system.  Each book in the catalogue is identified by a **ISBN**, has a **title**, and stores the **year of publication**.  The library wants a simple console‑based program that lets a clerk add new books, remove books, and look up a book by its ISBN.  Because the catalogue will be constantly edited, the clerk has asked that the underlying data structure be a **singly linked list** – the list should grow and shrink dynamically as books are inserted or deleted.

## Requirements  

Write a C (or C++) program that implements the catalogue using a singly linked list. The program must support the following operations, presented through a text menu:

1. **Add a Book** – Prompt the user for ISBN (string, up to 13 characters), title (string, up to 100 characters), and publication year (integer). Insert the new node at the **head** of the list.
2. **Delete a Book** – Prompt for an ISBN. Search the list; if a node with that ISBN exists, remove it and free its memory. If the ISBN is not found, display an appropriate message.
3. **Find a Book** – Prompt for an ISBN. If a node with that ISBN exists, display its details (ISBN, title, year). If not, inform the user that the book is not in the catalogue.
4. **Print All Books** – Traverse the list from head to tail and print the details of every book in the order they appear in the list.
5. **Exit** – Terminate the program gracefully, releasing any allocated memory.

All user prompts and output should be clear and self‑explanatory.

## Example Input / Output  

```
=== Library Catalogue Menu ===
1) Add a Book
2) Delete a Book
3) Find a Book
4) Print All Books
5) EXIT
Select an option: 1

Enter ISBN (max 13 chars): 9780131103627
Enter Title: The C Programming Language
Enter Publication Year: 1978
Book added successfully!

=== Library Catalogue Menu ===
1) Add a Book
2) Delete a Book
3) Find a Book
4) Print All Books
5) EXIT
Select an option: 3

Enter ISBN to find: 9780131103627
Book found:
ISBN: 9780131103627
Title: The C Programming Language
Year: 1978

=== Library Catalogue Menu ===
1) Add a Book
2) Delete a Book
3) Find a Book
4) Print All Books
5) EXIT
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity (a book) **must be represented with a `struct`** named `BookNode` (or equivalent) containing at least the fields `isbn`, `title`, `year`, and a pointer to the next node.  
2. **Display Function** – The logic for showing the details of **one specific book** (used by the “Find a Book” operation) **must be placed in a function called `displayBook`** that takes a pointer to a `BookNode` as its only argument.  
3. **Modular Design** – Apart from `main`, you may create additional helper functions, but **the menu handling loop must reside entirely inside `main`**.  
4. **Memory Management** – Every node allocated with `malloc`/`new` must be freed exactly once before program termination.  
5. **Menu Exit Requirement** – The menu **must include an explicit option to EXIT the program** (option 5 in the example) and selecting it must cause the program to stop after cleaning up resources.  

*All other aspects of the implementation are left to the student’s discretion.*

---

## Problem 4 - openai/gpt-oss-120b - Iteration 54
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple command‑line tool to keep track of the books that are currently on loan to students. Each book is identified by an ISBN (a 13‑digit number), has a title, and records the name of the student who borrowed it. The store’s IT intern has learned how to build a **singly linked list** and is asked to write a program that stores the loan records in the order they are entered.

## Requirements  
Write a C (or C++) program that implements a singly linked list to manage the loan records. The program must provide a **menu‑driven interface** with the following options:

1. **Add a new loan record** – Prompt the user for ISBN, title, and borrower’s name, then insert the new record at the **tail** of the list.  
2. **Remove a loan record** – Prompt for an ISBN and delete the first node whose ISBN matches. If no such record exists, display an appropriate message.  
3. **Display all loan records** – Traverse the list from head to tail and print each record on a separate line.  
4. **Search for a loan record** – Prompt for an ISBN and display the corresponding record (title and borrower) if found; otherwise, indicate that the record is absent.  
5. **EXIT** – Terminate the program.

The program should continue to display the menu after completing any operation until the user selects the **EXIT** option.

## Example Input / Output  

```
=== Book Loan Manager ===
1. Add loan
2. Remove loan
3. Display all loans
4. Search loan
5. EXIT
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter borrower name: Alice Johnson
Loan added.

=== Book Loan Manager ===
1. Add loan
2. Remove loan
3. Display all loans
4. Search loan
5. EXIT
Choose an option: 1

Enter ISBN (13 digits): 9780262033848
Enter title: Introduction to Algorithms
Enter borrower name: Bob Smith
Loan added.

=== Book Loan Manager ===
1. Add loan
2. Remove loan
3. Display all loans
4. Search loan
5. EXIT
Choose an option: 3

Current loan records:
ISBN: 9780131103627 | Title: The C Programming Language | Borrower: Alice Johnson
ISBN: 9780262033848 | Title: Introduction to Algorithms | Borrower: Bob Smith

=== Book Loan Manager ===
1. Add loan
2. Remove loan
3. Display all loans
4. Search loan
5. EXIT
Choose an option: 4

Enter ISBN to search: 9780131103627
Record found:
ISBN: 9780131103627 | Title: The C Programming Language | Borrower: Alice Johnson

=== Book Loan Manager ===
1. Add loan
2. Remove loan
3. Display all loans
4. Search loan
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: Use a `struct` named `LoanNode` (or equivalent) to represent each node in the singly linked list. The struct must contain fields for ISBN, title, borrower name, and a pointer to the next node.  
- **Function Requirement**: The logic for displaying the details of **ONE specific loan record** (used by the search operation) must be placed in a function with the exact prototype:  

  ```c
  void displayLoan(const LoanNode *node);
  ```

- **Menu Exit Option**: The menu must contain an explicit option labeled **EXIT** (option number 5 in the example) that terminates the program. Selecting any other number should re‑display the menu after the operation completes.  
- **Memory Management**: All dynamically allocated nodes must be freed appropriately before program termination to avoid memory leaks.  
- **No Global Variables**: All list manipulation should be performed via pointers passed to functions; do not use global variables to store the head or tail of the list.  

Implement the program meeting all the above specifications.

---

## Problem 5 - openai/gpt-oss-120b - Iteration 55
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑tracking system. Each bus that is currently on the road must be stored in a dynamic list so that new buses can be added as they start their routes and buses can be removed as soon as they finish. Because the number of active buses changes constantly, a **singly linked list** is the most appropriate data structure.

You have been hired to write a small console application that maintains this list of active buses. The program will allow the user (a dispatcher) to add a bus, remove a bus, search for a bus, and display the entire list.  

## Requirements  

Your program must support the following operations, presented through a text‑based menu:

1. **Add a bus** – Prompt for the bus’s unique integer ID and its route name (a single word, e.g., `RouteA`). Insert the new bus at the **end** of the linked list.  
2. **Remove a bus** – Prompt for a bus ID. If a bus with that ID exists, delete it from the list; otherwise, print “Bus not found.”  
3. **Search for a bus** – Prompt for a bus ID. If found, display the bus’s details; otherwise, print “Bus not found.”  
4. **Display all buses** – Traverse the list from head to tail and print each bus’s ID and route name on its own line.  
5. **Exit** – Terminate the program. (The menu option for this must be clearly identified, e.g., `5`.)

The program should loop, repeatedly showing the menu after each operation until the user chooses to exit.

### Input / Output Example  

```
=== Bus Tracker Menu ===
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 1
Enter bus ID: 101
Enter route name: RouteA
Bus added.

=== Bus Tracker Menu ===
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 1
Enter bus ID: 202
Enter route name: RouteB
Bus added.

=== Bus Tracker Menu ===
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 4
Active buses:
ID: 101, Route: RouteA
ID: 202, Route: RouteB

=== Bus Tracker Menu ===
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 3
Enter bus ID to search: 202
Bus found – ID: 202, Route: RouteB

=== Bus Tracker Menu ===
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 5
Goodbye!
```

## Functional Details  

- Bus IDs are guaranteed to be positive integers and unique within the list.  
- Route names contain no spaces.  
- When adding a bus, if the entered ID already exists, print “Error: Bus ID already in use.” and do not insert.  
- Removing the head, tail, or a middle node must correctly update list links to avoid memory leaks (if using a language with manual memory management).  
- Searching must **not** modify the list.  

### CONSTRAINTS  

- **Data Representation**: You **must** define a `struct` (or equivalent record type) named `BusNode` that contains at least the fields `int id`, `char route[...]/string route`, and a pointer to the next node.  
- **Display Function**: The logic for showing the details of a **single** bus (used by both the “Search” operation and the “Display all buses” traversal) must reside in a function called `displayBus`. Its prototype should be `void displayBus(const BusNode *node);`.  
- **Menu Implementation**: The program must present a menu as described, and **option 5 must be the explicit EXIT choice**. Selecting this option ends the program gracefully.  
- **Single‑purpose Helper**: Apart from `main`, you may create additional helper functions, but **the insertion logic must be encapsulated in a function named `appendBus`** with prototype `void appendBus(BusNode **head, int id, const char *route);`.  
- **No Global Variables**: All list pointers must be passed explicitly to functions; do not use global variables to store the head of the list.  

*Feel free to choose any programming language that supports structs (e.g., C, C++, or a language with similar constructs).*  

---  

*Your task is to write the complete program that satisfies the above specifications and constraints.*

---

## Problem 6 - openai/gpt-oss-120b - Iteration 56
# STEP 1: PROBLEM  

## Background  
The campus “Eco‑Bike” program rents bicycles to students. Each rental is recorded with the student’s ID, the bike’s serial number, and the number of days the bike is borrowed. The program must keep these rental records in the order they are entered, because the staff processes returns in a first‑in‑first‑out fashion.  

Your task is to write a console application that **stores, manipulates, and displays** the rental records using a **singly linked list**.

---

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Rental` that contains:  
     - `int studentID` – the unique identifier of the student.  
     - `int bikeSerial` – the bike’s serial number.  
     - `int days` – number of days the bike is borrowed.  
     - `Rental *next` – pointer to the next record.  

2. **Menu‑driven interface** (the program must present a menu after each operation)  
   * **1 – Add a new rental** – Prompt the user for the three fields and append the new node to the **tail** of the list.  
   * **2 – Remove the earliest rental** – Delete the node at the **head** of the list (if the list is not empty) and display the removed record.  
   * **3 – Find a rental by student ID** – Prompt for a `studentID`, search the list, and display the matching record (if any).  
   * **4 – List all rentals** – Traverse the list from head to tail and display every record.  
   * **5 – EXIT** – Terminate the program.  

3. **Display logic**  
   * All code that prints the details of **exactly one** `Rental` node must be placed in a function with the exact prototype:  
     ```c
     void displayRental(const Rental *r);
     ```  

4. **Memory management**  
   * Allocate each new node dynamically (`malloc`/`new`).  
   * Free memory appropriately when a node is removed or when the program exits.  

5. **Input validation**  
   * The menu choice must be an integer between 1 and 5.  
   * If the user selects an operation that cannot be performed (e.g., removing from an empty list), print a friendly message and return to the menu.  

---

## Example Interaction  

```
--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 1
Enter student ID: 10234
Enter bike serial #: 5871
Enter number of days: 3
Rental added.

--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 1
Enter student ID: 10456
Enter bike serial #: 6023
Enter number of days: 1
Rental added.

--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 4
Current rentals:
Student ID: 10234, Bike Serial: 5871, Days: 3
Student ID: 10456, Bike Serial: 6023, Days: 1

--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 3
Enter student ID to search: 10456
Student ID: 10456, Bike Serial: 6023, Days: 1

--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 2
Removed rental:
Student ID: 10234, Bike Serial: 5871, Days: 3

--- Eco‑Bike Rental System ---
1) Add a new rental
2) Remove earliest rental
3) Find rental by student ID
4) List all rentals
5) EXIT
Enter choice: 5
Goodbye!
```

---

### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be a `struct` named `Rental` (as described above).  
2. **Display function** – The logic for displaying the details of **one** rental must reside **exclusively** in a function called `displayRental`. No other function may directly `printf`/`cout` a single rental’s fields.  
3. **Menu requirement** – The program must present a menu and **must include** an explicit option to **EXIT** the program (option 5 in the specification).  
4. **Single‑function rule** – Apart from `main` and `displayRental`, you may create additional helper functions **only if they are for list manipulation** (e.g., `addTail`, `removeHead`, `searchByID`). No extra I/O functions are allowed.  

*The problem is intended for students who have just learned how to implement a singly linked list, dynamic memory allocation, and basic menu‑driven programs.*

---

## Problem 7 - openai/gpt-oss-120b - Iteration 57
# STEP 1: PROBLEM  

**Background**  
The university is launching a small‑scale bike‑sharing program on campus. Each bike is identified by a unique integer **BikeID**, has a **model name** (string, up to 30 characters), and a **current mileage** (integer). The system that tracks the bikes will be implemented as a **singly linked list** – the head of the list always points to the bike that was added first, and new bikes are appended to the end of the list.

You are asked to write a console program that allows the operator to manage the fleet of bikes through a simple text menu.

**Program Requirements**  

Your program must provide the following functionality:

1. **Add a new bike** – Prompt the user for BikeID, model name, and mileage, then create a node and append it to the end of the list. BikeIDs are guaranteed to be unique.  
2. **Remove a bike** – Prompt for a BikeID; if a bike with that ID exists, delete its node and free any allocated memory; otherwise, display “Bike not found.”  
3. **Search for a bike** – Prompt for a BikeID; if found, display all its details using the required display function; otherwise, display “Bike not found.”  
4. **Display all bikes** – Traverse the list from head to tail and print each bike’s details on its own line.  
5. **Update mileage** – Prompt for a BikeID and a new mileage value; if the bike exists, replace its mileage with the new value; otherwise, display “Bike not found.”  
6. **Exit** – Terminate the program gracefully, freeing any remaining dynamic memory.

The program should continue to show the menu after each operation until the user selects the exit option.

**Example Interaction**  

```
=== Campus Bike Sharing Menu ===
1. Add Bike
2. Remove Bike
3. Search Bike
4. Display All Bikes
5. Update Mileage
6. Exit
Enter choice: 1
Enter BikeID: 101
Enter model name: TrekFX3
Enter mileage: 120
Bike added.

Enter choice: 1
Enter BikeID: 202
Enter model name: GiantEscape
Enter mileage: 85
Bike added.

Enter choice: 4
BikeID: 101 | Model: TrekFX3      | Mileage: 120
BikeID: 202 | Model: GiantEscape | Mileage: 85

Enter choice: 5
Enter BikeID to update: 101
Enter new mileage: 130
Mileage updated.

Enter choice: 3
Enter BikeID to search: 202
BikeID: 202 | Model: GiantEscape | Mileage: 85

Enter choice: 2
Enter BikeID to remove: 101
Bike removed.

Enter choice: 4
BikeID: 202 | Model: GiantEscape | Mileage: 85

Enter choice: 6
Goodbye!
```

**Note:** The exact wording of prompts and messages can vary, but the overall flow must match the description above.

### CONSTRAINTS  

- The primary data entity **must be represented with a `struct`** named `Bike`. It must contain at least the fields `int id; char model[31]; int mileage; struct Bike *next;`.
- The logic for displaying the details of **one specific bike** must be placed in a function with the exact prototype:  
  ```c
  void displayBike(const struct Bike *b);
  ```
- Apart from `main`, you may create **no more than two additional functions** (e.g., for adding or removing nodes). All other code must reside in `main` or the required `displayBike` function.
- The program **must be menu‑driven** and **must include a menu option to EXIT** the program. The exit option must be clearly identified (e.g., option `6` in the example) and must cause the program to terminate after freeing any allocated memory.  

Follow these constraints strictly; the grading script will check for the presence of the `Bike` struct, the `displayBike` function, and the exit menu option.

---

## Problem 8 - openai/gpt-oss-120b - Iteration 58
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by a **ISBN**, has a **title**, an **author**, and a **shelf number** where it is stored. The library wants a simple console application that lets a librarian add new books, remove books that are no longer in the collection, and look up a book’s details by its ISBN.  

Because the librarian will be using the program repeatedly during a shift, the interface should be menu‑driven. The underlying data structure must be a **singly linked list** that stores each book as a node.

## Requirements  

1. **Data Representation**  
   - Define a `struct` called `Book` that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[101];` // up to 100 characters  
     - `char author[51];` // up to 50 characters  
     - `int shelf;`       // shelf number  
     - `struct Book *next;`  

2. **Core Operations (menu options)**  
   - **1. Add a Book** – Prompt the user for ISBN, title, author, and shelf number, then insert the new node at the **head** of the list.  
   - **2. Remove a Book** – Prompt for an ISBN. If a node with that ISBN exists, unlink it from the list and free its memory; otherwise, display “Book not found.”  
   - **3. Find a Book** – Prompt for an ISBN and, if found, display all its details using the required function `displayBook`. If not found, display “Book not found.”  
   - **4. List All Books** – Traverse the list and print the details of every stored book, one per line.  
   - **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **User Interaction**  
   - After completing any operation (except EXIT), the menu should be shown again.  
   - Input validation is not required beyond what is described; you may assume the user follows prompts.

## Example Input / Output  

```
--- Library Book Manager ---
1) Add a Book
2) Remove a Book
3) Find a Book
4) List All Books
5) EXIT
Enter choice: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Shelf Number: 12
Book added.

--- Library Book Manager ---
1) Add a Book
2) Remove a Book
3) Find a Book
4) List All Books
5) EXIT
Enter choice: 3

Enter ISBN to find: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Shelf: 12

--- Library Book Manager ---
1) Add a Book
2) Remove a Book
3) Find a Book
4) List All Books
5) EXIT
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented with a `struct` named `Book` as described above.  
- **Display Function:** The logic for printing the details of a single book **must** reside in a function with the exact prototype:  
  ```c
  void displayBook(const Book *b);
  ```  
- **Menu Exit Option:** The menu must include option **5) EXIT** (or the keyword `EXIT`) that ends the program.  
- **Memory Management:** All dynamically allocated nodes must be freed before program termination.  
- **Single‑File Implementation:** Apart from `main`, you may define additional helper functions, but the entire solution must be contained in a single source file.  

---

## Problem 9 - openai/gpt-oss-120b - Iteration 59
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book is identified by an ISBN, has a title, an author, and a count of how many copies are currently on the shelf. The library staff wants a simple console‑based program that lets them **add**, **remove**, **search**, and **list** books while the system is running. Because the staff will be entering and deleting books frequently, the professor has asked you to implement the collection as a **singly linked list**.

## Requirements  
Write a C (or C++) program that provides the following functionality through a text‑based menu:

1. **Add a new book** – Prompt the user for ISBN (string, no spaces), title, author, and copy count, then insert the new node at the **head** of the list.  
2. **Delete a book** – Prompt for an ISBN. If a node with that ISBN exists, remove it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN and display all information of the matching book (use the required function `displayBook`). If not found, print “Book not found.”  
4. **List all books** – Traverse the list and display the details of every stored book in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully (free any remaining allocated memory).  

The menu must be displayed after each operation until the user chooses the exit option.

## Example Input / Output  

```
--- Library Book Manager ---
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Copies: 3
Book added.

--- Library Book Manager ---
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) EXIT
Choose an option: 4

Books in inventory:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Copies: 3

--- Library Book Manager ---
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity (a book) must be represented with a `struct` named `BookNode` that contains at least the fields `isbn`, `title`, `author`, `copies`, and a pointer to the next node.  
2. **Display Function** – The logic for displaying the details of **one** specific book must be placed in a function with the exact prototype:  

   ```c
   void displayBook(const BookNode *node);
   ```  

3. **Memory Management** – All nodes must be allocated dynamically (e.g., using `malloc`/`new`) and freed appropriately when deleted or when the program exits.  
4. **Menu Requirement** – The menu must include a distinct option to **EXIT** the program; in the example it is option `5`. Selecting this option must end the program after releasing all allocated memory.  
5. **Single‑File Implementation** – The entire solution must reside in a single source file. Apart from `main()`, you may create additional helper functions, but the `displayBook` function is mandatory.  

Follow these constraints closely; the grading rubric will check for compliance.

---

## Problem 10 - openai/gpt-oss-120b - Iteration 60
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalog system.  The catalog stores information about each **book** in the order it is received.  Because the library frequently adds new acquisitions and occasionally discards old copies, the staff has decided to keep the books in a **singly linked list** – a simple structure that allows constant‑time insertion at the front and linear‑time traversal for reporting.

You have been hired to write a small console program that lets a librarian manage this list.  The program should be menu‑driven, allowing the librarian to add books, delete a book by its unique ISBN, display the whole catalog, and view the details of a single book.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   - Define a `struct` named `Book` that holds the following fields:  
     - `char title[101]` – title of the book (max 100 characters).  
     - `char author[51]` – author name (max 50 characters).  
     - `unsigned long isbn` – unique International Standard Book Number.  
     - `struct Book *next` – pointer to the next node in the list.  

2. **Menu (displayed repeatedly until the user chooses to exit)**  
   - **1. Add a new book** – Prompt for title, author, and ISBN, then insert the new node at the **front** of the linked list.  
   - **2. Remove a book** – Prompt for an ISBN; locate the node with that ISBN and remove it from the list (free its memory). If the ISBN is not found, print an appropriate message.  
   - **3. List all books** – Traverse the list from head to tail and print each book’s ISBN, title, and author on a separate line.  
   - **4. Show details of a book** – Prompt for an ISBN and display the full information for that single book. The display logic **must** be placed in a function called `displayBook`.  
   - **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **Input / Output**  
   - All interactions occur via `stdin` / `stdout`.  
   - The menu should be printed exactly as shown in the example.  
   - After completing an operation (except EXIT), the menu is shown again.  

4. **Memory Management**  
   - Dynamically allocate each `Book` node using `malloc` (or `new`).  
   - Ensure there are no memory leaks when the program ends.

## Example Interaction  

```
=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. List all books
4. Show details of a book
5. EXIT
Enter your choice: 1
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN: 9780131103627
Book added.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. List all books
4. Show details of a book
5. EXIT
Enter your choice: 1
Enter title: Introduction to Algorithms
Enter author: Cormen, Leiserson, Rivest, Stein
Enter ISBN: 9780262033848
Book added.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. List all books
4. Show details of a book
5. EXIT
Enter your choice: 3
ISBN: 9780262033848 | Title: Introduction to Algorithms | Author: Cormen, Leiserson, Rivest, Stein
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. List all books
4. Show details of a book
5. EXIT
Enter your choice: 4
Enter ISBN to view: 9780131103627
--- Book Details ---
ISBN : 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. List all books
4. Show details of a book
5. EXIT
Enter your choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct` named `Book` as described above.  
- **Function Naming** – The logic for displaying the details of ONE specific book **must** be implemented in a function called `displayBook`. Its prototype should be `void displayBook(const Book *b);`.  
- **Menu Exit Option** – The menu must contain an explicit option labeled **5. EXIT** (or the keyword `EXIT`) that terminates the program.  
- **Single‑purpose Functions** – Apart from `main`, you may create additional helper functions (e.g., `addBook`, `removeBook`, `listBooks`), but the only mandatory function name is `displayBook`.  

*Design your solution to be clear, well‑structured, and to respect the constraints above.*

---

## Problem 11 - openai/gpt-oss-120b - Iteration 1
# STEP 1: PROBLEM  

## Background  
The campus library is transitioning from a paper‑based catalogue to a simple digital system that runs on a single‑board computer in the reading room. The librarian wants a tiny console program that can store information about each book, allow her to add new titles, remove old ones, and look up details quickly. Because the library’s inventory is modest, a **singly linked list** is sufficient for the task, and the professor has just taught you how to build and manipulate such a list in C (or C++ with `struct`).  

## Requirements  

Write a console application that manages a collection of books using a **singly linked list**. The program must provide a text‑based menu that repeatedly prompts the user until they choose to exit. Implement the following operations:

1. **Add a Book** – Prompt for the book’s **ISBN** (string, no spaces), **title** (string, may contain spaces), and **author** (string, may contain spaces). Insert the new book at the **head** of the list.  
2. **Delete a Book** – Prompt for an ISBN. Remove the first node whose ISBN matches; if none is found, display “Book not found.”  
3. **Search for a Book** – Prompt for an ISBN and display the details of the matching book (see constraint on the display function). If not found, display “Book not found.”  
4. **List All Books** – Traverse the list and print the ISBN, title, and author of every stored book in the order they appear in the list. If the list is empty, print “No books in the catalogue.”  
5. **Exit** – Terminate the program gracefully.  

All input should be read from `stdin`; all output should be written to `stdout`. The menu must be displayed after each operation (except when exiting).  

## Example Input / Output  

```
=== Library Catalogue ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan and Ritchie
Book added.

=== Library Catalogue ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 4
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan and Ritchie

=== Library Catalogue ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 3
Enter ISBN to search: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan and Ritchie

=== Library Catalogue ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary data entity must be a `struct` named `Book` (or equivalent) containing at least the fields `char isbn[20]`, `char title[100]`, `char author[100]`, and a pointer to the next node.  
- **Display Function**: The logic for displaying the details of **ONE specific book** (used by the “Search for a Book” operation) must reside in a function with the exact prototype:  
  ```c
  void displayBook(const Book *b);
  ```  
- **Menu Requirement**: The program must present a menu as described above, and the menu must include a distinct option to **EXIT** the program (option number 5 in the example). Selecting this option should end the program.  
- **Memory Management**: All dynamically allocated nodes must be freed before program termination (no memory leaks).  
- **Single‑File Implementation**: Apart from `main()`, you may define additional helper functions, but the entire solution must be contained in a single source file.  

Design your solution to be clear, modular, and easy for a peer to read. Good luck!

---

## Problem 12 - openai/gpt-oss-120b - Iteration 2
# STEP 1: PROBLEM  

## Background  
The campus library has decided to modernize its “Book‑on‑the‑Shelf” system.  Each book is identified by a unique ISBN, has a title, an author, and a year of publication.  The library wants a simple command‑line program that stores the books in the order they are received (i.e., a **singly linked list**).  The program will be used by student volunteers who will add new books, remove books that are checked out, and look up information about a particular book.

## Requirements  

Write a console application that implements a singly linked list to manage the library’s collection. The program must support the following operations, presented through a text‑based menu:

1. **Add a new book** – Prompt the user for ISBN (string), title, author, and year (integer) and insert the new node at the **tail** of the list.  
2. **Remove a book** – Prompt for an ISBN and delete the first node whose ISBN matches. If the ISBN is not found, display an appropriate message.  
3. **Display a book’s details** – Prompt for an ISBN and show all stored information for that book. If the ISBN does not exist, inform the user.  
4. **List all books** – Traverse the list from head to tail and print each book’s data on a separate line.  
5. **Exit** – Terminate the program.

The program should continue to display the menu after completing any operation until the user chooses the Exit option.

## Example Input / Output  

```
=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Display a book's details
4. List all books
5. Exit
Select an option: 1

Enter ISBN: 978-0131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1988
Book added successfully!

=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Display a book's details
4. List all books
5. Exit
Select an option: 4

ISBN: 978-0131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1988

=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Display a book's details
4. List all books
5. Exit
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must** be represented by a `struct` (or equivalent record type) named `BookNode` that contains the fields: `isbn` (string/char array), `title`, `author`, `year`, and a pointer to the next node.  
- The logic for displaying the details of **ONE specific book** must be encapsulated in a function called `displayBook`. The function signature should accept a pointer to a `BookNode` (or `nullptr`/`NULL` if not found) and handle all output for that single book.  
- Apart from `main()`, you may create additional helper functions, but the core list manipulation (insertion, deletion, traversal) should each be implemented in **separate** functions.  
- If a menu is implemented (as required), the menu must include an explicit option to **EXIT** the program (e.g., option 5 shown above).  

*The problem is intended for students who have just learned how to build and manipulate singly linked lists.*

---

## Problem 13 - openai/gpt-oss-120b - Iteration 3
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a tiny inventory‑tracking utility that runs in a console.  Each book in the inventory is identified only by a **title** (a string of up to 50 characters) and a **quantity on hand** (a non‑negative integer).  The store clerk will add new titles, remove titles that are no longer sold, update the quantity of an existing title, and request a listing of the entire inventory.  

You have just learned how to implement a **singly linked list** in C (or C‑like language) using `struct`s.  Write a program that stores the bookstore’s inventory in a singly linked list and provides a simple text‑based menu for the clerk to manipulate the list.

## Requirements  

Your program must support the following operations, selectable from a menu:

1. **Add a new book** – Prompt for the title and the initial quantity, then insert a new node at the **head** of the list. If a book with the same title already exists, display an error and do not insert.
2. **Delete a book** – Prompt for the title, locate the node, remove it from the list, and free its memory. If the title is not found, display an appropriate message.
3. **Update quantity** – Prompt for the title and the new quantity, locate the node and replace its stored quantity. If the title is not found, display an appropriate message.
4. **Display inventory** – Traverse the list and print each book’s title and quantity, one per line, in the order they appear in the list.
5. **Search for a book** – Prompt for a title and display the quantity of that book using the function `displayEntity`. If the title is not found, inform the user.
6. **EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.

All user prompts and messages should be clear and self‑explanatory.

## Example Input / Output  

```
--- Bookstore Inventory Menu ---
1) Add a new book
2) Delete a book
3) Update quantity
4) Display inventory
5) Search for a book
6) EXIT
Enter your choice: 1
Enter title: The C Programming Language
Enter quantity: 12
Book added.

--- Bookstore Inventory Menu ---
1) Add a new book
2) Delete a book
3) Update quantity
4) Display inventory
5) Search for a book
6) EXIT
Enter your choice: 1
Enter title: Introduction to Algorithms
Enter quantity: 5
Book added.

--- Bookstore Inventory Menu ---
1) Add a new book
2) Delete a book
3) Update quantity
4) Display inventory
5) Search for a book
6) EXIT
Enter your choice: 4
Inventory:
The C Programming Language - 12 copies
Introduction to Algorithms - 5 copies

--- Bookstore Inventory Menu ---
1) Add a new book
2) Delete a book
3) Update quantity
4) Display inventory
5) Search for a book
6) EXIT
Enter your choice: 5
Enter title to search: The C Programming Language
The C Programming Language - 12 copies

--- Bookstore Inventory Menu ---
1) Add a new book
2) Delete a book
3) Update quantity
4) Display inventory
5) Search for a book
6) EXIT
Enter your choice: 6
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary data entity (a book) **must** be represented with a `struct` named `Node` (or equivalent) containing at least the fields `title`, `quantity`, and a pointer to the next node.  
* **Function Requirement** – The logic for displaying the details of **one specific book** (used in the “Search for a book” operation) **must** be placed in a function called `displayEntity`. Its prototype should be something like `void displayEntity(const Node *node);`.  
* **Menu Implementation** – The menu must include a distinct option to **EXIT** the program (as shown in the example, option 6). Selecting this option must cause the program to terminate after freeing all dynamically allocated memory.  
* **Memory Management** – Every node that is created with `malloc`/`new` must be freed exactly once when it is removed or when the program exits.  
* **Single‑File Solution** – Apart from `main`, you may define additional helper functions (e.g., for insertion, deletion, searching, displaying the whole list), but the entire solution must reside in a single source file.  

Write the program according to the above specification.

---

## Problem 14 - openai/gpt-oss-120b - Iteration 4
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants to keep a simple, in‑memory inventory of the textbooks it sells each semester. Because the inventory changes frequently (new arrivals, books being sold out, and occasional returns), the store’s software engineer has decided to use a **singly linked list** to store each book’s information.  

You are tasked with writing a small console program that lets a user manage this inventory through a text‑based menu. The program must build, modify, and query the linked list according to the user’s commands.

## Requirements  

Your program must provide the following functionality:

1. **Add a new book** – Prompt the user for the book’s ISBN (string, up to 13 characters), title (string, up to 50 characters), and quantity in stock (non‑negative integer). Insert the new node at the **end** of the list.  
2. **Remove a book** – Prompt for an ISBN. If a node with that ISBN exists, delete it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN and display the details of that single book (ISBN, title, quantity). If the ISBN does not exist, print “Book not found.”  
4. **Display the entire inventory** – Walk the list from head to tail and print each book on its own line in the format:  
   `ISBN | Title | Quantity`  
5. **Update quantity** – Prompt for an ISBN and a new quantity. If the ISBN exists, replace the stored quantity with the new value; otherwise print “Book not found.”  
6. **Exit** – Terminate the program gracefully, releasing all allocated memory.

The program should repeatedly show the menu until the user selects the exit option.

## Example Interaction  

```
=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter quantity: 5
Book added.

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Choose an option: 4

Inventory:
9780131103627 | The C Programming Language | 5

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Choose an option: 6

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation** – The primary data entity **must** be represented by a `struct` named `BookNode` containing at least the fields `char isbn[14];`, `char title[51];`, `int quantity;`, and a pointer `struct BookNode *next;`.  
- **Display Function** – The logic that prints the details of **one** specific book (used by the Search operation) **must** be placed in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
- **Menu Implementation** – The program must present a textual menu as shown in the example. The menu **must** include an explicit option to **EXIT** the program (option number 6 in the example). Selecting this option must cause the program to terminate after freeing all dynamically allocated nodes.  
- **Memory Management** – Every node created with `malloc`/`new` must be freed exactly once before program termination.  
- **Single‑File Solution** – All code (including `struct` definition, helper functions, and `main`) must reside in a single source file.  
- **Standard Library Only** – You may only use the standard I/O and memory‑allocation libraries of your language (e.g., `<stdio.h>`, `<stdlib.h>` for C; `<iostream>`, `<cstring>` for C++). No external containers or libraries are permitted.  

Implement the program according to the above specifications.

---

## Problem 15 - openai/gpt-oss-120b - Iteration 5
# STEP 1: PROBLEM  

## Background  
The campus computer lab maintains a **simple equipment checkout system**.  Each piece of equipment (e.g., a laptop, projector, or tablet) is identified by a unique integer ID, a short name, and a status flag indicating whether it is currently **available** or **checked‑out**.  

The lab manager wants a small console program that stores the equipment records in a **singly linked list**.  The list must support adding new equipment, removing equipment that is retired, updating the status of a piece of equipment, and printing the entire inventory.  

You have just finished the lecture on singly linked lists and are now asked to implement this system.

## Requirements  
Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   - Define a `struct` named `Equipment` that contains:  
     - `int id;`            // unique identifier  
     - `char name[32];`     // short name (no spaces)  
     - `int available;`    // 1 = available, 0 = checked‑out  

   - Define a `struct` named `Node` that holds an `Equipment` and a pointer to the next node.

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add Equipment** – Prompt for `id`, `name`, and initial availability, then insert the new node at the **end** of the list. If an item with the same `id` already exists, print an error and do not insert. |
   | 2 | **Remove Equipment** – Prompt for `id`; delete the node with that `id` from the list. If not found, print a message. |
   | 3 | **Update Status** – Prompt for `id` and the new availability (1 or 0); modify the matching node. If not found, print a message. |
   | 4 | **Display All** – Print a table of all equipment records in the order they appear in the list. |
   | 5 | **Display One** – Prompt for `id` and print the details of that single piece of equipment (use the required helper function, see Constraints). |
   | 6 | **EXIT** – Terminate the program. |

3. **Input / Output**  
   - All input is read from `stdin`; all output is written to `stdout`.  
   - The menu should be redisplayed after each operation (except after EXIT).  

4. **Memory Management**  
   - Allocate nodes dynamically (`malloc`/`new`).  
   - Free memory for a node when it is removed.  
   - Before program termination, free any remaining nodes.

## Example Interaction  

```
=== Equipment Checkout System ===
1) Add Equipment
2) Remove Equipment
3) Update Status
4) Display All
5) Display One
6) EXIT
Enter choice: 1
Enter ID: 101
Enter name: LaptopA
Is available? (1/0): 1
Equipment added.

1) Add Equipment
2) Remove Equipment
3) Update Status
4) Display All
5) Display One
6) EXIT
Enter choice: 1
Enter ID: 102
Enter name: ProjectorB
Is available? (1/0): 0
Equipment added.

1) Add Equipment
2) Remove Equipment
3) Update Status
4) Display All
5) Display One
6) EXIT
Enter choice: 4
ID   Name        Status
101  LaptopA     Available
102  ProjectorB  Checked‑out

1) Add Equipment
2) Remove Equipment
3) Update Status
4) Display All
5) Display One
6) EXIT
Enter choice: 5
Enter ID to display: 102
ID: 102
Name: ProjectorB
Status: Checked‑out

1) Add Equipment
2) Remove Equipment
3) Update Status
4) Display All
5) Display One
6) EXIT
Enter choice: 6
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Usage** – The primary data entity must be represented with a `struct Equipment`. The linked‑list node must be a separate `struct Node` that contains an `Equipment` and a `Node *next`.  

2. **Helper Function** – The logic for displaying the details of **ONE specific equipment record** must be placed in a function with the exact prototype:  

   ```c
   void displayEquipment(const Equipment *e);
   ```

   The menu option **5 – Display One** must call this function.  

3. **Single‑purpose Functions** – Apart from `main`, you must implement at least the following separate functions (each performing a single logical task):  
   - `Node* createNode(const Equipment *e);` – allocate and initialise a node.  
   - `void addEquipment(Node **head);` – handle option 1.  
   - `void removeEquipment(Node **head);` – handle option 2.  
   - `void updateStatus(Node *head);` – handle option 3.  
   - `void displayAll(const Node *head);` – handle option 4.  

   (You may add more helper functions if you wish, but the above are required.)  

4. **Menu Exit** – The menu must include an explicit option **6) EXIT** that ends the program.  

5. **No Global Variables** – All data structures must be passed to functions via parameters; do not use global variables for the list head or any other data.  

6. **Error Handling** – All user‑provided IDs must be validated for existence where appropriate; print clear error messages without crashing.  

---  

Implement the program according to the specifications above. The solution will be evaluated on correctness, adherence to the constraints, proper memory management, and code clarity.

---

## Problem 16 - openai/gpt-oss-120b - Iteration 6
# STEP 1: PROBLEM  

## Background  
The campus “TechTree” club maintains a simple roster of its members. Each member is identified by a **Student ID** (an integer), a **name** (a string of at most 30 characters), and the **year** they are in (e.g., 1‑4). The club’s executive board wants a tiny console program that can store this roster in memory, allow the board to add new members, remove members who have left, look up a particular member, and print the whole list.  

You have just finished the unit on **singly linked lists** and are asked to implement this roster using a singly linked list.

## Requirements  

Write a C (or C‑compatible) program that provides the following functionality through a text‑based menu:

1. **Add a member** – Prompt for Student ID, name, and year, then insert the new member at the **end** of the linked list.  
2. **Remove a member** – Prompt for a Student ID and delete the first node whose ID matches. If the ID is not found, display a suitable message.  
3. **Find a member** – Prompt for a Student ID and display that member’s details (ID, name, year). If the ID is not present, report it.  
4. **Display all members** – Traverse the list and print each member on its own line in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.

The program should continue to show the menu after each operation until the user chooses the **Exit** option.

## Example Input / Output  

```
=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 1
Enter Student ID: 1024
Enter name: Alice Johnson
Enter year (1-4): 2
Member added.

=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 1
Enter Student ID: 2048
Enter name: Bob Lee
Enter year (1-4): 3
Member added.

=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 4
Roster:
ID: 1024 | Name: Alice Johnson | Year: 2
ID: 2048 | Name: Bob Lee      | Year: 3

=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 3
Enter Student ID to find: 2048
Member found:
ID: 2048 | Name: Bob Lee | Year: 3

=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 2
Enter Student ID to remove: 1024
Member removed.

=== TechTree Roster Menu ===
1. Add member
2. Remove member
3. Find member
4. Display all members
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data representation** – The primary data entity must be represented with a `struct` named `MemberNode` (or similar) that contains the three fields (ID, name, year) and a pointer to the next node.  
2. **Display function** – The logic for showing the details of **one specific member** (used in the “Find member” operation) must be placed in a function with the exact prototype:  

   ```c
   void displayMember(const MemberNode *node);
   ```  

3. **Menu implementation** – The program must present a menu as described above and **must include an explicit “Exit” option** (choice number 5) that ends the program.  
4. **Memory management** – All dynamically allocated nodes must be freed before the program terminates.  
5. **Single‑responsibility functions** – Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching, printing the whole list), but each helper must perform **one logical task** and be clearly named.  

Follow these constraints; any solution that violates them will be considered incomplete.

---

## Problem 17 - openai/gpt-oss-120b - Iteration 7
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its “quick‑checkout” system.  When a patron scans a book, the system records the book’s **ISBN**, **title**, and **author** in the order they are scanned.  The library wants a simple console program that stores these records in a **singly linked list** so that the most recently scanned book can be retrieved quickly, and the entire list can be displayed or cleared at the end of the day.

## Requirements  

Write a C (or C++) program that implements a singly linked list to manage the scanned‑book records. The program must provide a **menu‑driven interface** with the following options:

1. **Add a new book** – Prompt the user for ISBN (string, up to 13 characters), title, and author, then insert the new record at the **head** of the list.  
2. **Remove the most recent book** – Delete the node at the head of the list and display the removed book’s details. If the list is empty, print an appropriate message.  
3. **Display all books** – Traverse the list from head to tail and print each book’s ISBN, title, and author on a separate line. If the list is empty, indicate that there are no records.  
4. **Search by ISBN** – Prompt for an ISBN, locate the first node whose ISBN matches, and display that book’s details using the required display function. If not found, inform the user.  
5. **Clear all records** – Delete every node in the list and confirm that the list is now empty.  
6. **Exit** – Terminate the program gracefully (this option must be present as the explicit “Exit” menu item).

The program should continue to display the menu after completing any operation until the user chooses **Exit**.

## Example Input / Output  

```
--- Library Quick‑Checkout ---
1) Add a new book
2) Remove most recent book
3) Display all books
4) Search by ISBN
5) Clear all records
6) Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie

Book added successfully.

--- Library Quick‑Checkout ---
1) Add a new book
2) Remove most recent book
3) Display all books
4) Search by ISBN
5) Clear all records
6) Exit
Choose an option: 3

Current scanned books:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- Library Quick‑checkout ---
...
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must** be represented with a `struct` named `BookNode` (or equivalent) that contains fields for `isbn`, `title`, `author`, and a pointer to the next node.  
- The logic for displaying the details of **ONE** specific book **must** be placed in a function with the exact signature `void displayBook(const BookNode *node);`.  
- Apart from `main`, the solution must contain **at most two** additional user‑defined functions (e.g., for insertion, deletion, searching, or clearing).  
- If a menu is implemented (as required), the menu must include an explicit option to **EXIT** the program; the option number or keyword for exiting must be clearly indicated (see option 6 above).  

*Note: Use only standard libraries (`stdio.h`, `stdlib.h`, `string.h`, etc.). Do not use any container classes from C++ STL.*

---

## Problem 18 - openai/gpt-oss-120b - Iteration 8
# STEP 1: PROBLEM  

## Background  
The campus library wants a tiny command‑line tool that keeps track of the books currently on loan. Each loan record contains a **book ID** (an integer), the **title** of the book (a string without spaces), and the **student’s name** (a string without spaces). The library staff will add new loan records, remove them when a book is returned, look up a particular loan, and print the whole list of active loans.  

You have just finished the unit on **singly linked lists** and are asked to implement this tool using a linked list as the underlying data structure.

## Requirements  

Write a program that provides the following functionality through a simple text menu:

1. **Add a loan record** – Prompt for `book ID`, `title`, and `student name`, then insert the new record at the **head** of the list.  
2. **Return a book** – Prompt for a `book ID` and delete the first node whose ID matches. If the ID is not found, display an appropriate message.  
3. **Find a loan** – Prompt for a `book ID` and display the details of that loan (use the required `displayEntity` function). If the ID is not found, inform the user.  
4. **List all loans** – Traverse the list and display every active loan in the order they are stored (head to tail).  
5. **Exit** – Terminate the program.  

All input and output should be performed via the console.

### Example Interaction  

```
--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 1
Enter Book ID: 101
Enter Title: Algorithms
Enter Student Name: Alice

--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 1
Enter Book ID: 202
Enter Title: DataStructures
Enter Student Name: Bob

--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 4
Loan List:
[ID: 202] Title: DataStructures, Borrower: Bob
[ID: 101] Title: Algorithms,    Borrower: Alice

--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 3
Enter Book ID to find: 101
[ID: 101] Title: Algorithms, Borrower: Alice

--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 2
Enter Book ID to return: 202
Book ID 202 returned successfully.

--- Library Loan Tracker ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The loan record must be represented with a `struct` (or equivalent language‑specific record type) named `Loan`. The struct must contain at least the three fields: `int id; char title[...]; char student[...];` and a pointer to the next node.  
2. **Function Requirement** – The logic that prints the details of **one specific loan** (used by the “Find loan” option) must reside in a function called `displayEntity`. Its prototype should be something like `void displayEntity(const Loan *node);`.  
3. **Menu Implementation** – The program must present a menu as shown in the example. The menu must include a distinct option to **EXIT** the program (option 5 in the example). Selecting this option ends the program gracefully.  
4. **Memory Management** – Every node that is removed (e.g., when a book is returned) must be freed/deallocated appropriately to avoid memory leaks.  
5. **Single‑File Solution** – Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, traversal), but the core logic for displaying a single loan must be isolated in `displayEntity`.  

*Note: The problem is language‑agnostic; you may choose C, C++, Java, or any language that supports explicit struct‑like types and manual memory handling.*

---

## Problem 19 - openai/gpt-oss-120b - Iteration 9
# STEP 1: PROBLEM  

## Background  
The campus library wants a simple command‑line tool to keep track of the books that are currently on the “New Arrivals” shelf.  The shelf can hold an arbitrary number of books, and the librarian will be adding and removing books throughout the day.  Because the list of books changes frequently, a **singly linked list** is the most appropriate data structure – it allows constant‑time insertion and removal at the front of the list and linear‑time traversal for displaying the contents.

You are asked to write a small C (or C‑like) program that implements this “New Arrivals” manager using a singly linked list.

## Requirements  

Your program must provide a **menu‑driven interface** that allows the user to perform the following actions:

1. **Add a book to the front of the list** – Prompt for the book’s ISBN (string, up to 13 characters), title (string, up to 50 characters), and author (string, up to 30 characters). Insert the new book node at the head of the linked list.  
2. **Remove the first book** – Delete the node at the head of the list and free its memory. If the list is empty, display an appropriate message.  
3. **Search for a book by ISBN** – Prompt for an ISBN, traverse the list, and if a matching node is found, display the book’s details (ISBN, title, author). If not found, inform the user.  
4. **Display all books** – Traverse the list from head to tail and print the details of every book in the order they appear in the list. If the list is empty, state that there are no books.  
5. **Exit the program** – Clean up any allocated memory and terminate gracefully.

The menu must be displayed after each operation (except after exiting).

## Example Input / Output  

```
--- New Arrivals Manager ---
1) Add book to front
2) Remove first book
3) Search by ISBN
4) Display all books
5) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added successfully.

--- New Arrivals Manager ---
1) Add book to front
2) Remove first book
3) Search by ISBN
4) Display all books
5) EXIT
Choose an option: 1

Enter ISBN: 9780262033848
Enter Title: Introduction to Algorithms
Enter Author: Cormen et al.
Book added successfully.

--- New Arrivals Manager ---
1) Add book to front
2) Remove first book
3) Search by ISBN
4) Display all books
5) EXIT
Choose an option: 4

Books on the New Arrivals shelf:
ISBN: 9780262033848 | Title: Introduction to Algorithms | Author: Cormen et al.
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- New Arrivals Manager ---
1) Add book to front
2) Remove first book
3) Search by ISBN
4) Display all books
5) EXIT
Choose an option: 3

Enter ISBN to search: 9780131103627
Book found:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- New Arrivals Manager ---
1) Add book to front
2) Remove first book
3) Search by ISBN
4) Display all books
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary data entity (a book) must be represented with a `struct` named `BookNode` that contains:
  * `char isbn[14];`   // space for 13‑character ISBN plus terminating null
  * `char title[51];`
  * `char author[31];`
  * `struct BookNode *next;`
* **Function Requirements** –  
  * The logic for displaying the details of **one specific book** (used by the search operation) **must be placed in a function called `displayBook`** with the prototype `void displayBook(const BookNode *node);`.  
  * All other list operations (insert, delete, display all, search) should each be implemented in their own separate functions (e.g., `insertFront`, `removeFront`, `searchByISBN`, `displayAll`).  
* **Memory Management** – Every node allocated with `malloc`/`new` must be freed before program termination.  
* **Menu Exit Option** – The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option must cause the program to terminate after releasing all resources.  
* **No Global Variables** – All list pointers must be passed to functions as parameters; do not use global variables to store the head pointer.  

These constraints are mandatory; solutions that do not obey them will be considered incomplete.

---

## Problem 20 - openai/gpt-oss-120b - Iteration 10
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple command‑line application to keep track of the books it receives each week. Because the inventory changes frequently, the store owner has asked you to store the books in a **singly linked list** that grows and shrinks as books are added or removed. Each book is identified by an ISBN, has a title, and a price.

Your task is to write a program that lets a user manage this list through a text‑based menu.

## Requirements  

Your program must provide the following functionality:

1. **Add a new book** – Prompt the user for ISBN (string, no spaces), title (string, may contain spaces), and price (floating‑point). Insert the new node at the **head** of the list.  
2. **Remove a book** – Prompt for an ISBN. If a node with that ISBN exists, remove it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN and, if found, display the book’s details using the required display function (see constraints). If not found, print “Book not found.”  
4. **Display all books** – Traverse the list and print the details of every book, one per line, in the order they appear in the list.  
5. **Exit** – Clean up any allocated memory and terminate the program.

The menu should be displayed after each operation until the user chooses to exit.

## Example Input / Output  

```
--- Book Inventory Menu ---
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter price: 45.99
Book added.

--- Book Inventory Menu ---
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Choose an option: 1
Enter ISBN: 9780262033848
Enter title: Introduction to Algorithms
Enter price: 89.50
Book added.

--- Book Inventory Menu ---
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Choose an option: 4
ISBN: 9780262033848 | Title: Introduction to Algorithms | Price: $89.50
ISBN: 9780131103627 | Title: The C Programming Language | Price: $45.99

--- Book Inventory Menu ---
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Choose an option: 3
Enter ISBN to search: 9780131103627
ISBN: 9780131103627 | Title: The C Programming Language | Price: $45.99

--- Book Inventory Menu ---
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – You **must** define a `struct` named `BookNode` (or equivalent) to represent each node in the singly linked list. The struct should contain fields for ISBN, title, price, and a pointer to the next node.  
* **Display Function** – The logic for printing the details of **one specific book** (used in the “Search” operation) **must be placed in a function called `displayBook`** that takes a pointer to a `BookNode` as its sole argument and prints the book in the format shown in the example.  
* **Menu Requirement** – The program must present a text‑based menu as described above, and **option 5 must be the explicit “Exit” choice** that terminates the program.  
* **Memory Management** – All dynamically allocated nodes must be freed before the program exits.  
* **Standard Libraries Only** – You may only use the standard C library headers (`stdio.h`, `stdlib.h`, `string.h`, etc.). No external libraries are allowed.  

Write the program in C (or C++) adhering to the constraints above.

---

## Problem 21 - openai/gpt-oss-120b - Iteration 11
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernising its catalogue system.  Each book is identified by a unique **ISBN**, has a **title**, an **author**, and a **year of publication**.  The library wants a simple console‑based prototype that stores the books in a **singly linked list**.  The prototype will be used by a junior librarian who will add new books, remove books that are withdrawn, look up a specific book, and print the whole catalogue.  

Your task is to implement this prototype.  The program should present a text‑based menu, perform the requested operation, and loop until the librarian chooses to exit.  

## Requirements  

1. **Data Representation**  
   * Define a `struct` called `BookNode` that stores:  
     - `char isbn[20];`  
     - `char title[100];`  
     - `char author[100];`  
     - `int year;`  
     - a pointer to the next node.  

2. **Menu‑driven Operations** (displayed repeatedly until exit)  
   1. **Add a book** – Prompt for ISBN, title, author, and year; insert the new node at the **end** of the list.  
   2. **Remove a book** – Prompt for an ISBN; delete the first node whose ISBN matches. If the ISBN is not found, print a message.  
   3. **Search for a book** – Prompt for an ISBN; locate the node and display its details (use the required function, see below). If not found, report it.  
   4. **Display all books** – Traverse the list from head to tail, printing each book’s information on a separate line.  
   5. **Exit** – Terminate the program.  

3. **Input / Output**  
   * All interaction occurs via `stdin`/`stdout`.  
   * The menu should be clear, e.g.:  

```
--- Library Catalogue ---
1) Add a book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 
```  

   * After each operation (except EXIT) the menu is shown again.  

4. **Error handling**  
   * If the user selects an invalid menu option, display “Invalid choice, try again.” and re‑show the menu.  
   * When removing or searching, if the ISBN does not exist, display “Book not found.”  

## Example  

```
--- Library Catalogue ---
1) Add a book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 1
Enter ISBN: 978-0131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1988
Book added.

--- Library Catalogue ---
1) Add a book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 4
ISBN: 978-0131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1988

--- Library Catalogue ---
1) Add a book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 5
Goodbye!
```  

## ### CONSTRAINTS  

* **Data Structure** – The primary data entity **must** be a `struct` named `BookNode`.  
* **Display Function** – The logic for printing the details of **one** specific book **must** be placed in a function with the exact prototype:  

```c
void displayBook(const BookNode *node);
```  

* **Modularity** – Apart from `main`, you must implement **exactly three** additional functions:  
  1. `void addBook(BookNode **head);`  
  2. `void removeBook(BookNode **head);`  
  3. `void searchBook(const BookNode *head);`  

  (The `displayBook` function counts toward the total; you may create helper functions only if they are declared `static` inside the same source file.)  

* **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option ends the loop and terminates the program.  

* **Memory Management** – All dynamically allocated nodes must be freed before the program exits.  

* **Language** – The solution must be written in **C** (C99 or later).  

---  

Design your solution so that a student who has just learned how to build and manipulate singly linked lists can implement it confidently while respecting the constraints above.

---

## Problem 22 - openai/gpt-oss-120b - Iteration 12
# STEP 1: PROBLEM  

## Background  
The campus museum is expanding its collection of historical artifacts. The curatorial staff wants a simple command‑line tool to keep track of each artifact as it arrives, leaves, or is queried. Because the collection is expected to change frequently, a **singly linked list** is the most appropriate structure – it allows constant‑time insertion and removal at the head and linear‑time traversal for searches.

You are asked to write this tool. The program will run in a loop, presenting a menu to the user and performing the requested operation on the linked list of artifacts.

---

## Requirements  

1. **Data Entity**  
   - Each artifact must be represented by a `struct` named `Artifact` containing the following fields:  
     - `int id` – a unique positive identifier (no two artifacts share the same id).  
     - `char name[50]` – the name of the artifact (single‑word or space‑separated, up to 49 characters).  
     - `int year` – the year the artifact was created (e.g., 1845).  
     - `struct Artifact *next` – pointer to the next node in the list.

2. **Menu Options** (displayed each iteration)  
   1. **Add Artifact** – Prompt for `id`, `name`, and `year`; insert the new artifact at the **head** of the list. If an artifact with the same `id` already exists, print an error and do not insert.  
   2. **Remove Artifact** – Prompt for an `id`; delete the node with that `id` from the list. If the `id` is not found, print an appropriate message.  
   3. **Display All Artifacts** – Traverse the list from head to tail and print each artifact’s details on its own line, using the format shown in the example.  
   4. **Find Artifact by ID** – Prompt for an `id`; locate the artifact and display its details using the dedicated display function. If not found, inform the user.  
   5. **EXIT** – Terminate the program. (The menu must clearly label this option with the word “EXIT”.)

3. **Program Flow**  
   - The program starts with an empty list.  
   - After completing any operation (except EXIT), the menu is shown again.  
   - All input is read from `stdin`; all output is written to `stdout`.  

4. **Error Handling**  
   - Non‑numeric input for numeric fields may be considered undefined behavior (the instructor will supply correct input).  
   - Duplicate `id` on insertion, or attempts to delete/find a non‑existent `id`, must be reported with a clear message.

---

## Example Input / Output  

```
--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 1
Enter ID: 101
Enter name: GoldenMask
Enter year: 1500
Artifact added.

--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 1
Enter ID: 202
Enter name: SilverSword
Enter year: 1320
Artifact added.

--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 3
ID: 202 | Name: SilverSword | Year: 1320
ID: 101 | Name: GoldenMask | Year: 1500

--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 4
Enter ID to find: 101
ID: 101 | Name: GoldenMask | Year: 1500

--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 2
Enter ID to remove: 202
Artifact removed.

--- Artifact Management Menu ---
1. Add Artifact
2. Remove Artifact
3. Display All Artifacts
4. Find Artifact by ID
5. EXIT
Enter choice: 5
Goodbye!
```

---

### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be a `struct` named `Artifact` as described above.  
- **Display Function** – The logic for printing the details of **one** artifact must reside in a function with the exact prototype:  
  ```c
  void displayArtifact(const Artifact *a);
  ```  
  This function is to be used both by the “Display All” and “Find by ID” options.  
- **Menu Implementation** – The program must present a textual menu and **must** include an explicit option labeled `EXIT` (as option 5 in the example) that terminates the loop.  
- **Single‑File Solution** – All code must be placed in a single source file; you may define additional helper functions, but the only global variables permitted are the head pointer of the list.  
- **Standard Library Only** – Use only the C standard library headers (`stdio.h`, `stdlib.h`, `string.h`). No external libraries are allowed.  

---

## Problem 23 - openai/gpt-oss-120b - Iteration 13
# STEP 1: PROBLEM  

## Background  
The campus library is transitioning from a paper‑based catalogue to a simple digital system that runs on a command‑line interface.  Each book in the catalogue is identified by a **title**, an **author**, and a **unique integer ID**.  The library staff wants a lightweight program that lets them:

* add new books to the catalogue,  
* remove a book when it is withdrawn,  
* search for a book by its ID, and  
* display the entire list of books in the order they were entered.

Because the catalogue will be stored only for the duration of a single session, the data can be kept in memory using a **singly linked list**.

## Requirements  

Write a C (or C‑like) program that implements the library catalogue using a singly linked list. The program must provide a **menu‑driven interface** with the following options:

1. **Add Book** – Prompt the user for `ID`, `Title`, and `Author`, then insert a new node at the **end** of the list.  
2. **Remove Book** – Prompt for an `ID`; if a node with that ID exists, delete it and free its memory; otherwise print “Book not found.”  
3. **Find Book** – Prompt for an `ID`; if found, display the book’s details; otherwise print “Book not found.”  
4. **List All Books** – Traverse the list from head to tail and print each book’s `ID`, `Title`, and `Author` on a separate line.  
5. **Exit** – Terminate the program gracefully, freeing any remaining allocated memory.

The program should continue to display the menu after completing an operation until the user selects **Exit**.

## Example Input / Output  

```
--- Library Catalogue Menu ---
1) Add Book
2) Remove Book
3) Find Book
4) List All Books
5) Exit
Enter choice: 1
Enter ID: 101
Enter Title: The Art of Algorithms
Enter Author: Jane Doe
Book added.

--- Library Catalogue Menu ---
1) Add Book
2) Remove Book
3) Find Book
4) List All Books
5) Exit
Enter choice: 1
Enter ID: 202
Enter Title: Data Structures in Practice
Enter Author: John Smith
Book added.

--- Library Catalogue Menu ---
1) Add Book
2) Remove Book
3) Find Book
4) List All Books
5) Exit
Enter choice: 4
ID: 101 | Title: The Art of Algorithms | Author: Jane Doe
ID: 202 | Title: Data Structures in Practice | Author: John Smith

--- Library Catalogue Menu ---
1) Add Book
2) Remove Book
3) Find Book
4) List All Books
5) Exit
Enter choice: 3
Enter ID to find: 202
ID: 202 | Title: Data Structures in Practice | Author: John Smith

--- Library Catalogue Menu ---
1) Add Book
2) Remove Book
3) Find Book
4) List All Books
5) Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a book) **must be defined using a `struct`** that contains at least the fields `int id; char title[100]; char author[100]; struct Book *next;`.  
2. **Function Requirements** –  
   * The logic for displaying the details of **one specific book** (used by the *Find Book* option) **must be placed in a function named `displayBook`** that takes a pointer to a `Book` struct and prints its fields in the format shown in the example.  
   * All list‑manipulation operations (add, remove, list) may be implemented in separate helper functions, but **no more than two functions besides `main`** may be defined.  
3. **Menu Constraint** – The menu must include a distinct option to **EXIT** the program (option 5 in the example). Selecting this option must end the loop and free any allocated memory.  
4. **Memory Management** – Every node allocated with `malloc`/`new` must be freed before the program terminates (including when a book is removed).  

*Note:* The problem is intentionally limited to a singly linked list; using arrays, vectors, or other containers to store the books is not allowed.

---

## Problem 24 - openai/gpt-oss-120b - Iteration 14
# STEP 1: PROBLEM  

## Background  
The university’s student services office wants a simple **digital “Help‑Desk Ticket” manager** that runs in a console. Each ticket records the student’s name, the ID of the course they need help with, and a short description of the problem. The office clerk will add new tickets as they arrive, view the next ticket to be handled (the one at the front of the list), remove tickets that have been resolved, and list all pending tickets.  

You have just finished the unit on **singly linked lists** and are asked to implement this manager using a singly linked list as the underlying data structure.

## Requirements  
Write a C (or C++) program that provides the following functionality through a text‑based menu:

1. **Add a ticket** – Prompt the user for the student’s name (single word, max 30 chars), course ID (integer), and problem description (single line, max 100 chars). Insert the new ticket at the **tail** of the list (i.e., tickets are processed in FIFO order).  
2. **Show next ticket** – Display the details of the ticket at the **head** of the list without removing it. If the list is empty, print an appropriate message.  
3. **Resolve next ticket** – Remove the ticket at the head of the list and free its memory. Print a confirmation message showing the removed ticket’s details. If the list is empty, inform the user.  
4. **List all tickets** – Traverse the list from head to tail and display each ticket’s details, numbered in order of arrival. If the list is empty, state that there are no pending tickets.  
5. **Exit** – Terminate the program, ensuring that any dynamically allocated memory is released.  

The menu must be displayed after each operation until the user chooses to exit.

## Example Input / Output  

```
=== Help‑Desk Ticket Manager ===
1) Add ticket
2) Show next ticket
3) Resolve next ticket
4) List all tickets
5) EXIT
Choose an option: 1

Enter student name: alice
Enter course ID: CS101
Enter problem description: cannot compile project

Ticket added successfully!

=== Help‑Desk Ticket Manager ===
1) Add ticket
2) Show next ticket
3) Resolve next ticket
4) List all tickets
5) EXIT
Choose an option: 2

--- Next Ticket ---
Name: alice
Course ID: CS101
Problem: cannot compile project
--------------------

=== Help‑Desk Ticket Manager ===
1) Add ticket
2) Show next ticket
3) Resolve next ticket
4) List all tickets
5) EXIT
Choose an option: 4

Pending tickets (1):
1) Name: alice | Course ID: CS101 | Problem: cannot compile project

=== Help‑Desk Ticket Manager ===
1) Add ticket
2) Show next ticket
3) Resolve next ticket
4) List all tickets
5) EXIT
Choose an option: 3

Resolved ticket:
Name: alice
Course ID: CS101
Problem: cannot compile project

=== Help‑Desk Ticket Manager ===
1) Add ticket
2) Show next ticket
3) Resolve next ticket
4) List all tickets
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: The ticket must be represented by a `struct` named `Ticket` containing at least the fields `name`, `courseID`, `description`, and a pointer to the next ticket.  
- **Function Requirements**:  
  - The logic for displaying the details of **one specific ticket** must be placed in a function with the exact prototype: `void displayTicket(const Ticket *t);`  
  - All list‑manipulation operations (add, show, resolve, list) must be implemented as separate functions **outside of `main`**. You may create additional helper functions as needed.  
- **Memory Management**: Every ticket added to the list must be allocated dynamically (e.g., using `malloc`/`new`). All allocated memory must be freed before program termination.  
- **Menu Exit Option**: The menu must include a clearly numbered option **5) EXIT** (or the keyword `EXIT`) that terminates the program. Selecting this option must cause the program to free any remaining tickets and then end.  

*Note: The problem is intentionally scoped for students who have just learned singly linked lists, dynamic memory allocation, and basic modular programming.*

---

## Problem 25 - openai/gpt-oss-120b - Iteration 15
# STEP 1: PROBLEM  

## Background  
The campus bookstore needs a simple command‑line application to keep track of the books that are currently on the shelves. Each book is identified by an ISBN (a 13‑digit integer), has a title, and a quantity indicating how many copies are available. The store manager has asked you to write a program that stores the books in a **singly linked list** and lets the manager perform basic operations through a text menu.

## Requirements  

Your program must implement the following functionality:

1. **Add a new book** – Prompt the user for ISBN, title, and quantity, then insert the new node at the **end** of the linked list. If a book with the same ISBN already exists, reject the insertion and display an error message.  
2. **Remove a book** – Prompt for an ISBN and delete the node that contains that ISBN. If the ISBN is not found, display an appropriate message.  
3. **Search for a book** – Prompt for an ISBN and display the details of that book (ISBN, title, quantity). If the ISBN is not present, inform the user.  
4. **Display all books** – Traverse the list and print the details of every stored book in the order they appear in the list. If the list is empty, print “No books in inventory.”  
5. **Update quantity** – Prompt for an ISBN and a new quantity, then modify the quantity field of the matching node. If the ISBN does not exist, display an error.  
6. **Exit** – End the program gracefully.

All interactions must occur through a **menu** that repeatedly prompts the user for a choice until the exit option is selected.

## Example Interaction  

```
=== Book Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Enter your choice: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter quantity: 4
Book added successfully.

=== Book Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Enter your choice: 4

ISBN: 9780131103627 | Title: The C Programming Language | Qty: 4

=== Book Inventory Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Update quantity
6. EXIT
Enter your choice: 6

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: You **must** define a `struct` named `Book` (or equivalent) to represent each node in the singly linked list. The struct should contain at least the fields `isbn`, `title`, `quantity`, and a pointer to the next node.  
- **Display Function**: The logic for showing the details of **one specific book** (used in the Search operation) **must** be placed in a function named `displayBook`. This function should take a pointer to a `Book` node as its sole argument and print the ISBN, title, and quantity.  
- **Function Count**: Apart from `main`, you may implement **only one additional function** (i.e., `displayBook`). All other list manipulations (insert, delete, search, update, traversal) must be coded directly inside `main` or inside helper code that does **not** constitute a separate named function.  
- **Menu Requirement**: The menu must include a distinct option to **EXIT** the program. The option number (or keyword) for exiting must be clearly indicated in the menu (as shown in the example).  

*Note: The problem is intended for students who have just learned how to build and manipulate singly linked lists. No advanced data structures or libraries beyond standard I/O are required.*

---

## Problem 26 - openai/gpt-oss-120b - Iteration 16
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, an author, and a current stock count (how many copies are on the shelf). The library wants a simple command‑line tool that a junior developer can use to add new books, remove books, update the stock of an existing title, and display information about a particular book. The tool must store the books in a **singly linked list**, because the total number of titles is unknown at compile time and insertions/removals happen frequently.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   - Define a `struct Book` (or `struct book`) that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus null terminator  
     - `char title[101];` // up to 100 characters + null terminator  
     - `char author[51];` // up to 50 characters + null terminator  
     - `int stock;`       // number of copies currently available  
     - A pointer to the next `Book` node.  

2. **Menu‑driven Interface** (displayed repeatedly until the user chooses to exit)  
   - **1. Add a new book** – Prompt for ISBN, title, author, and initial stock, then insert the new node at the **head** of the list. If a book with the same ISBN already exists, print an error and do not insert.  
   - **2. Remove a book** – Prompt for an ISBN; locate the node and remove it from the list, freeing its memory. If the ISBN is not found, display a message.  
   - **3. Update stock** – Prompt for an ISBN and a signed integer `delta`. Add `delta` to the book’s current stock (the stock may become zero but never negative; if the operation would make it negative, reject it with an error).  
   - **4. Display a book** – Prompt for an ISBN and print all fields of the matching book. The printing logic **must** be placed in a function named `displayBook`. If the ISBN is not found, inform the user.  
   - **5. List all books** – Traverse the list and print each book’s details in the order they appear (head to tail).  
   - **0. EXIT** – Terminate the program, freeing any remaining allocated memory.  

3. **Input / Output**  
   - All prompts and messages should be clear and user‑friendly.  
   - After completing an operation (except EXIT), the menu should be shown again.  

## Example Interaction  

```
--- Library Inventory System ---
1) Add a new book
2) Remove a book
3) Update stock
4) Display a book
5) List all books
0) EXIT
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter initial stock: 3
Book added successfully.

--- Library Inventory System ---
1) Add a new book
2) Remove a book
3) Update stock
4) Display a book
5) List all books
0) EXIT
Enter choice: 4
Enter ISBN to display: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Stock: 3

--- Library Inventory System ---
1) Add a new book
2) Remove a book
3) Update stock
4) Display a book
5) List all books
0) EXIT
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must** be represented with a `struct` named `Book` (or `book`).  
- The logic for displaying the details of ONE specific book **must** be encapsulated in a function called `displayBook`. Its prototype should be `void displayBook(const Book *b);`.  
- Apart from `main`, you may create additional helper functions, but the menu handling should be performed inside `main` (i.e., no separate `runMenu()` function).  
- The program **must** use a **singly linked list**; using arrays, vectors, or other containers for storing the books is not allowed.  
- If a menu is implemented (as required), the option to **EXIT** the program **must** be present and clearly labeled (option `0` in this specification).  

---  

*Design your solution so that it compiles without warnings and runs correctly on a standard C (or C++) compiler.*

---

## Problem 27 - openai/gpt-oss-120b - Iteration 17
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a tiny command‑line utility to keep track of the books that are currently on a “quick‑checkout” shelf.  Because the shelf can be rearranged at any moment, the store manager prefers a **singly linked list** – new books are always added to the front, and books can be removed from anywhere in the list without having to shift other elements.  

Your task is to write a C (or C++) program that models this shelf and lets the user manipulate it through a simple text menu.

## Requirements  

Your program must support the following operations:

1. **Add a book** – Prompt the user for the book’s ISBN (string, up to 13 characters), title (string, up to 50 characters), and price (floating‑point). Insert the new book **at the head** of the linked list.  
2. **Remove a book** – Prompt for an ISBN. Search the list; if a node with that ISBN exists, unlink it and free its memory. If the ISBN is not found, display an appropriate message.  
3. **Search for a book** – Prompt for an ISBN and, if found, display the book’s details (ISBN, title, price). If not found, report that the book is absent.  
4. **Display all books** – Traverse the list from head to tail and print the details of every stored book in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully, freeing any remaining allocated memory.

All user interaction should be performed through a **menu** that repeatedly asks the user to choose one of the options above.

## Example Input / Output  

```
=== Quick‑Checkout Shelf Manager ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter price: 45.99
Book added.

=== Quick‑Checkout Shelf Manager ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 4

Books on the shelf:
ISBN: 9780131103627 | Title: The C Programming Language | Price: $45.99

=== Quick‑Checkout Shelf Manager ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 5

Goodbye!
```

*(The exact formatting of prompts and messages is not graded; only the functional behaviour matters.)*  

## ### CONSTRAINTS  

- **Data representation**: You **must** define a `struct` (in C) or a `struct`‑type (in C++) named `Book` that stores the ISBN, title, price, and a pointer to the next node.  
- **Display function**: The logic for printing the details of **one** specific book (used by the “Search” operation) **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const Book *b);
  ```

- **Menu implementation**: The program must present a textual menu as shown in the example. The menu **must** include an option explicitly labeled “EXIT” (or the number 5) that terminates the program.  

- **Memory management**: Every node that is removed or the program terminates must be freed; no memory leaks are allowed.  

- **Single‑source file**: All code must reside in one source file (e.g., `main.c` or `main.cpp`). Apart from `main`, you may create additional helper functions, but the primary linked‑list operations (add, remove, search, display all) should each be encapsulated in their own function.  

- **Standard library only**: Use only the C (or C++) standard library; no third‑party containers or utilities.  

---  

*Write a program that satisfies the above specifications. Your solution will be evaluated on correctness, adherence to the constraints, and clean handling of dynamic memory.*

---

## Problem 28 - openai/gpt-oss-120b - Iteration 18
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its software to keep track of the books that are currently on the “quick‑checkout” shelf. The shelf can hold an arbitrary number of books, and the library staff wants a simple console program that lets them **add**, **remove**, **search**, and **list** the books in the order they were placed on the shelf.  

Because the shelf is conceptually a “first‑in, first‑out” line, a **singly linked list** is the most natural way to store the collection. Your task is to implement this list and the operations required by the staff.

## Requirements  
Write a C (or C++) program that provides a text‑based menu with the following options:

1. **Add a new book** – Prompt the user for the book’s title (a single line, up to 100 characters) and its ISBN (a 13‑digit number). Insert the new node at the **end** of the linked list.  
2. **Remove a book** – Prompt for a title. If a node with that title exists, delete the first occurrence from the list and report success; otherwise, report that the book was not found.  
3. **Search for a book** – Prompt for a title. If the book is present, display its details (title and ISBN); otherwise, inform the user that the book is not on the shelf.  
4. **Display all books** – Traverse the list from head to tail and print each book’s title and ISBN on its own line. If the list is empty, print “The shelf is empty.”  
5. **Exit** – Terminate the program.  

The program should repeatedly display the menu after completing an operation until the user chooses the Exit option.

## Example Input / Output  

```
=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 1
Enter title: Introduction to Algorithms
Enter ISBN: 9780262033848
Book added.

=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 1
Enter title: Clean Code
Enter ISBN: 9780132350884
Book added.

=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 4
Books on the shelf:
Title: Introduction to Algorithms, ISBN: 9780262033848
Title: Clean Code, ISBN: 9780132350884

=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 3
Enter title to search: Clean Code
Title: Clean Code, ISBN: 9780132350884

=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 2
Enter title to remove: Introduction to Algorithms
Book removed.

=== Quick‑Checkout Shelf Menu ===
1. Add a book
2. Remove a book
3. Search for a book
4. Display all books
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary entity (a book) **must** be represented with a `struct` named `BookNode` (or equivalent) that contains at least the fields `title`, `isbn`, and a pointer to the next node.  
- **Display Function**: The logic for displaying the details of **ONE specific book** must be placed in a function with the exact prototype:  

  ```c
  void displayBook(const BookNode *node);
  ```  

  This function should print the title and ISBN in the format shown in the example.  
- **Menu Requirement**: The program **must** include a menu option to **EXIT** the program. The exit option must be clearly numbered (as shown) and must cause the program to terminate cleanly.  
- **Memory Management**: All dynamically allocated memory for nodes must be freed before the program exits.  
- **Single‑File Implementation**: Apart from `main()`, you may define additional helper functions (e.g., for insertion, deletion, searching, displaying all books), but the entire solution must reside in a single source file.  

*Deliver a program that satisfies all of the above.*

---

## Problem 29 - openai/gpt-oss-120b - Iteration 19
# STEP 1: PROBLEM  

## Background  
The campus “Book‑Buddy” club maintains a tiny digital catalogue of the most‑requested books on a single‑room bookshelf. Because the collection is constantly changing—books are donated, borrowed, or removed—the club has decided to store the catalogue in a **singly linked list** that can grow and shrink at runtime.  

Your task is to write a console program that lets a user manage this catalogue. The program should be written in C (or C‑like pseudocode) and must use a `struct` to represent each book node.

## Requirements  

1. **Data Entity**  
   - Each book is represented by a `struct BookNode` containing:  
     - `int id` – a unique identifier (positive integer).  
     - `char title[51]` – the book title (max 50 characters, may contain spaces).  
     - `char author[31]` – the author name (max 30 characters).  
     - `struct BookNode *next` – pointer to the next node.  

2. **Program Functionality** (menu‑driven)  
   - **1. Add a Book** – Prompt for `id`, `title`, and `author`. Insert the new node at the **end** of the list. If an existing node already uses the given `id`, print an error and do not insert.  
   - **2. Remove a Book** – Prompt for an `id`. Delete the node with that `id` (anywhere in the list). If the `id` does not exist, print an error.  
   - **3. Display All Books** – Traverse the list from head to tail and print each book’s details on a separate line, using the format:  
     ```
     [id] Title by Author
     ```  
   - **4. Find a Book** – Prompt for an `id`. If found, call a dedicated function `displayBook` (see constraint) to print that single book’s details; otherwise, print “Book not found.”  
   - **5. EXIT** – Terminate the program gracefully, freeing any allocated memory.  

3. **User Interaction**  
   - After completing any operation (except EXIT), the menu should be shown again.  
   - Input may be assumed to be well‑formed (integers where integers are expected, strings without newline issues).  

## Example Input / Output  

```
--- Book‑Buddy Catalogue ---
1) Add a Book
2) Remove a Book
3) Display All Books
4) Find a Book
5) EXIT
Choose an option: 1
Enter Book ID: 101
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added.

--- Book‑Buddy Catalogue ---
1) Add a Book
2) Remove a Book
3) Display All Books
4) Find a Book
5) EXIT
Choose an option: 1
Enter Book ID: 202
Enter Title: Introduction to Algorithms
Enter Author: Cormen et al.
Book added.

--- Book‑Buddy Catalogue ---
1) Add a Book
2) Remove a Book
3) Display All Books
4) Find a Book
5) EXIT
Choose an option: 3
[101] The C Programming Language by Kernighan & Ritchie
[202] Introduction to Algorithms by Cormen et al.

--- Book‑Buddy Catalogue ---
1) Add a Book
2) Remove a Book
3) Display All Books
4) Find a Book
5) EXIT
Choose an option: 4
Enter Book ID to find: 202
[202] Introduction to Algorithms by Cormen et al.

--- Book‑Buddy Catalogue ---
1) Add a Book
2) Remove a Book
3) Display All Books
4) Find a Book
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity **must** be defined as a `struct` named `BookNode` (or equivalent) containing the fields listed above.  
- **Display Function:** The logic for showing the details of **ONE** specific book **must** reside in a function with the exact signature:  
  ```c
  void displayBook(const BookNode *node);
  ```  
  This function should print the book in the format `[id] Title by Author` followed by a newline.  
- **Menu Exit Option:** The menu **must** contain an explicit option to EXIT the program. In the example it is option `5`. The program must terminate only when this option is chosen.  
- **Memory Management:** All dynamically allocated nodes must be freed before program termination.  
- **Single‑File Implementation:** Apart from `main()` and `displayBook()`, you may create additional helper functions (e.g., `addBook`, `removeBook`, `findBook`), but the entire solution must reside in a single source file.  

---  

Design your solution to satisfy all the above requirements and constraints. Good luck!

---

## Problem 30 - openai/gpt-oss-120b - Iteration 20
# STEP 1: PROBLEM  

**Background**  
The campus wildlife club maintains a tiny “virtual zoo” where each animal is stored in a singly‑linked list.  
Every animal has a unique integer **ID**, a name (max 30 characters), and its species (max 30 characters).  
The club wants a simple console program that lets a user add new animals, remove them, look them up, and display the whole roster.

**Program Requirements**  

1. **Data representation** – Define a `struct` called `Animal` that contains the fields described above **and** a pointer to the next node in the list.  
2. **Menu‑driven interface** – When the program starts, repeatedly present the user with a menu containing the following options (the exact numbers are up to you, but they must be shown to the user):  
   - Add a new animal to the **end** of the list.  
   - Delete an animal given its ID.  
   - Search for an animal by ID and display its details.  
   - Display **all** animals currently stored.  
   - **EXIT** the program.  
3. **Adding** – Prompt for ID, name, and species. If the ID already exists in the list, print an error message and do **not** insert.  
4. **Deleting** – Prompt for the ID to delete. If the ID is not found, print a message indicating so. Otherwise remove the node and free its memory.  
5. **Searching** – Prompt for the ID, locate the node, and display its details using a dedicated function `displayAnimal`. If not found, report that.  
6. **Displaying all** – Traverse the list from head to tail and print each animal on its own line in the format:  
   `ID: <id>, Name: <name>, Species: <species>`  
7. The program must continue looping until the user selects the **EXIT** option.  

**Example Interaction** (user input is bolded)

```
=== Virtual Zoo Menu ===
1. Add Animal
2. Delete Animal
3. Search Animal
4. Display All Animals
5. EXIT
Choose an option: **1**
Enter ID: **101**
Enter name: **Leo**
Enter species: **Lion
Animal added.

=== Virtual Zoo Menu ===
1. Add Animal
2. Delete Animal
3. Search Animal
4. Display All Animals
5. EXIT
Choose an option: **1**
Enter ID: **102**
Enter name: **Molly**
Enter species: **Elephant
Animal added.

=== Virtual Zoo Menu ===
1. Add Animal
2. Delete Animal
3. Search Animal
4. Display All Animals
5. EXIT
Choose an option: **3**
Enter ID to search: **101**
ID: 101, Name: Leo, Species: Lion

=== Virtual Zoo Menu ===
1. Add Animal
2. Delete Animal
3. Search Animal
4. Display All Animals
5. EXIT
Choose an option: **4**
ID: 101, Name: Leo, Species: Lion
ID: 102, Name: Molly, Species: Elephant

=== Virtual Zoo Menu ===
1. Add Animal
2. Delete Animal
3. Search Animal
4. Display All Animals
5. EXIT
Choose an option: **5**
Good‑bye!
```

### CONSTRAINTS  

- **Struct usage** – The primary data entity **must** be a `struct` named `Animal`.  
- **Display function** – The logic for showing the details of **one** specific animal **must** be placed in a function with the exact signature `void displayAnimal(const Animal *a);`.  
- **Menu requirement** – The menu must contain an explicit option to **EXIT** the program (e.g., option number 5 as shown). Selecting this option terminates the loop and ends the program.  
- **Memory management** – All dynamically allocated nodes must be freed before program termination.  
- **Single‑source file** – The entire solution should be written in one source file (e.g., `zoo.c` or `zoo.cpp`).  

*Your task is to write a program that satisfies all of the above.*

---

## Problem 31 - openai/gpt-oss-120b - Iteration 21
# STEP 1: PROBLEM  

## Background  
The city’s public transportation department is modernizing its bus‑stop information system. Each bus stop is identified by a unique stop number and stores the name of the stop and the average daily passenger count. The department wants a simple console application that lets a clerk **add**, **remove**, **search**, and **list** bus stops. Internally the stops must be stored in a **singly linked list** because stops are frequently inserted and deleted while the program is running.

## Program Requirements  
Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   * Define a `struct` named `BusStop` that contains:  
     - `int stopID` – unique identifier (positive integer)  
     - `char name[50]` – name of the stop (no spaces, e.g., `MainSt`)  
     - `int dailyPassengers` – average daily passengers (non‑negative)  
     - `struct BusStop *next` – pointer to the next node in the list  

2. **Menu‑Driven Interface** (the program must present a menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new bus stop** – prompt for `stopID`, `name`, and `dailyPassengers`. Insert the new node at the **end** of the list. If a stop with the same `stopID` already exists, display an error and do not insert. |
   | 2 | **Delete a bus stop** – prompt for a `stopID`. Remove the node with that ID from the list. If the ID is not found, display an appropriate message. |
   | 3 | **Search for a bus stop** – prompt for a `stopID`. If found, display the stop’s details using the function `displayEntity`. If not found, inform the user. |
   | 4 | **List all bus stops** – traverse the list from head to tail and display each stop’s details (again using `displayEntity`). |
   | 5 | **EXIT** – terminate the program. |

3. **Functions**  
   * Implement a function `void displayEntity(const BusStop *node);` that prints a single bus stop in the format:  
     ```
     Stop ID: <stopID>, Name: <name>, Daily Passengers: <dailyPassengers>
     ```
   * All other list operations (add, delete, search, list) should be implemented in separate helper functions of your choosing. Apart from `main`, at least one additional function must be present (the required `displayEntity`).  

4. **Input Validation**  
   * `stopID` must be a positive integer.  
   * `dailyPassengers` must be a non‑negative integer.  
   * The program should not crash on malformed input; instead, display an error and re‑show the menu.

5. **Memory Management**  
   * Allocate nodes dynamically using `malloc` (or `new` in C++).  
   * Free memory for removed nodes and before program termination to avoid leaks.

## Example Interaction  

```
=== Bus Stop Management ===
1. Add a new bus stop
2. Delete a bus stop
3. Search for a bus stop
4. List all bus stops
5. EXIT
Choose an option: 1
Enter Stop ID: 101
Enter Name: CentralStation
Enter Daily Passengers: 3500
Bus stop added.

=== Bus Stop Management ===
1. Add a new bus stop
2. Delete a bus stop
3. Search for a bus stop
4. List all bus stops
5. EXIT
Choose an option: 1
Enter Stop ID: 102
Enter Name: OakStreet
Enter Daily Passengers: 1200
Bus stop added.

=== Bus Stop Management ===
1. Add a new bus stop
2. Delete a bus stop
3. Search for a bus stop
4. List all bus stops
5. EXIT
Choose an option: 3
Enter Stop ID to search: 101
Stop ID: 101, Name: CentralStation, Daily Passengers: 3500

=== Bus Stop Management ===
1. Add a new bus stop
2. Delete a bus stop
3. Search for a bus stop
4. List all bus stops
5. EXIT
Choose an option: 4
Stop ID: 101, Name: CentralStation, Daily Passengers: 3500
Stop ID: 102, Name: OakStreet, Daily Passengers: 1200

=== Bus Stop Management ===
1. Add a new bus stop
2. Delete a bus stop
3. Search for a bus stop
4. List all bus stops
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  
- **Struct Requirement:** The primary data entity must be represented with a `struct` named `BusStop`.  
- **Display Function:** The logic for printing the details of **one** bus stop must reside in a function called `displayEntity`.  
- **Menu Exit Option:** The menu must include a distinct option (number **5**) labeled **EXIT** that ends the program.  
- **Dynamic Allocation:** All nodes must be created with dynamic memory allocation; no static or global arrays of nodes are allowed.  
- **Single‑File Implementation:** The entire solution should be contained in a single source file.  

*Note:* The problem is intentionally scoped for students who have just learned singly linked lists, dynamic memory, and basic modular programming.

---

## Problem 32 - openai/gpt-oss-120b - Iteration 22
# STEP 1: PROBLEM  

**Background**  
The campus library is modernizing its inventory system. The librarian wants a simple console program that keeps track of the books currently on the shelves. Because the collection is constantly changing (books are added, removed, or looked up), a *singly linked list* is the most appropriate data structure for this assignment.  

**Task**  
Write a C (or C++) program that maintains a singly linked list of books. Each book is represented by a `struct` containing the following fields:  

| Field | Type | Description |
|-------|------|-------------|
| `id`   | `int` | A unique identification number for the book (positive integer). |
| `title`| `char[51]` | The title of the book (max 50 characters, null‑terminated). |
| `author`| `char[31]` | The author’s name (max 30 characters, null‑terminated). |
| `next` | pointer to the next node | Used internally by the linked list. |

Your program must present a **menu‑driven interface** that allows the user to perform the following operations:

1. **Add a new book** – Append the new book to the end of the list.  
2. **Remove a book by ID** – Search for the node whose `id` matches the supplied value and delete it, preserving list integrity.  
3. **Search for a book by ID** – Locate the node and display its details.  
4. **Display all books** – Print the information of every node in the list, from head to tail.  
5. **Exit** – Terminate the program gracefully.

**Program Requirements**  

1. **Data Representation** – Use a `struct` named `Book` (or equivalent) to store each book’s data and the link to the next node.  
2. **Functionality** – Implement **exactly one** helper function (besides `main`) named `displayBook` that takes a pointer to a `Book` node and prints its `id`, `title`, and `author` in a readable format. All other operations (insert, delete, search, display‑all) may be coded directly in `main` or in additional static helper functions, but the *display of a single entity* **must** be performed by `displayBook`.  
3. **Menu** – The menu must be displayed after each completed operation, and option **5** (or the keyword `EXIT`) must cleanly end the program.  
4. **Input Validation** – If the user attempts to delete or search for a non‑existent `id`, print an informative message and return to the menu.  
5. **Memory Management** – Allocate nodes dynamically and free them when they are removed or when the program exits.  

**Example Interaction**  

```
--- Library Book Manager ---
1. Add a new book
2. Remove a book by ID
3. Search for a book by ID
4. Display all books
5. EXIT
Choose an option: 1

Enter book ID: 101
Enter title (max 50 chars): The C Programming Language
Enter author (max 30 chars): Kernighan & Ritchie
Book added successfully!

--- Library Book Manager ---
1. Add a new book
2. Remove a book by ID
3. Search for a book by ID
4. Display all books
5. EXIT
Choose an option: 4

ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- Library Book Manager ---
1. Add a new book
2. Remove a book by ID
3. Search for a book by ID
4. Display all books
5. EXIT
Choose an option: 3

Enter book ID to search: 999
No book with ID 999 found.

--- Library Book Manager ---
1. Add a new book
2. Remove a book by ID
3. Search for a book by ID
4. Display all books
5. EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

- **Data Entity** – Must use a `struct` (named `Book` or similar) to represent each node.  
- **Display Function** – The logic for displaying the details of **ONE** specific book must be encapsulated in a function called `displayBook`.  
- **Menu Requirement** – The program must present a menu and include a distinct option (number **5** or the keyword `EXIT`) that terminates the program.  
- **Memory** – All dynamically allocated memory must be freed before program termination.  

*Feel free to add any minor helper functions you deem useful, but the above constraints are mandatory.*

---

## Problem 33 - openai/gpt-oss-120b - Iteration 23
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its digital catalog system.  Each book in the collection is identified by an **ISBN**, has a **title**, an **author**, and a **year of publication**.  The library wants a simple command‑line utility that stores the books in a **singly linked list** so that librarians can add new entries, remove old ones, and look up a book by its ISBN while the program is running.

You are asked to implement this utility from scratch, using only the standard C library (or C++ if you prefer, but the same concepts apply).  The focus of the assignment is the correct implementation of a singly linked list and basic list operations.

---

## Requirements  

Your program must provide the following functionality through a text‑based menu:

1. **Add a new book** – Prompt the user for ISBN (string, up to 13 characters), title, author, and year, then insert the new node at the **head** of the list.  
2. **Delete a book** – Prompt for an ISBN; if a node with that ISBN exists, remove it from the list and free its memory; otherwise display “Book not found”.  
3. **Search for a book** – Prompt for an ISBN; if found, display all details of that book; otherwise display “Book not found”.  
4. **List all books** – Traverse the list from head to tail and print the details of every stored book in the order they appear.  
5. **Exit** – Terminate the program gracefully, freeing all allocated memory.

All input should be read from `stdin`; all output should be written to `stdout`. The program should continue to show the menu after completing any operation until the user selects the **Exit** option.

---

## Example Input / Output  

```
=== Library Catalog Menu ===
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) Exit
Choose an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Year: 1988
Book added.

=== Library Catalog Menu ===
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) Exit
Choose an option: 1

Enter ISBN: 9780201616224
Enter Title: The Pragmatic Programmer
Enter Author: Andrew Hunt
Enter Year: 1999
Book added.

=== Library Catalog Menu ===
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) Exit
Choose an option: 4

--- Book List ---
ISBN: 9780201616224
Title: The Pragmatic Programmer
Author: Andrew Hunt
Year: 1999

ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1988
-----------------

=== Library Catalog Menu ===
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) Exit
Choose an option: 3

Enter ISBN to search: 9780131103627
--- Book Details ---
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1988
---------------------

=== Library Catalog Menu ===
1) Add Book
2) Delete Book
3) Search Book
4) List All Books
5) Exit
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

* **Data Representation** – The primary data entity (a book) must be represented with a `struct` named `BookNode` that contains the fields `isbn`, `title`, `author`, `year`, and a pointer to the next node.  
* **Display Function** – The logic for showing the details of **one specific book** (used by both “Search Book” and the individual entries while listing) must be placed in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
* **Modular Design** – Apart from `main()`, you may create additional helper functions, but the **menu handling loop** must be implemented inside `main()`; all other operations (add, delete, search, list) should be delegated to separate functions.  
* **Memory Management** – Every node allocated with `malloc`/`new` must be freed before program termination.  
* **Menu Exit Requirement** – The menu must include an option explicitly labeled “5) Exit” (or the keyword `EXIT`) that terminates the program.  

*Optional (for extra credit)*: Implement the list insertion so that the list remains **sorted in ascending order by ISBN** instead of always inserting at the head.  

---  

*Submit a single source file that compiles without warnings and meets all the constraints above.*

---

## Problem 34 - openai/gpt-oss-120b - Iteration 24
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, an author, and a year of publication. The library wants a simple console program that lets a librarian **add**, **remove**, **search**, and **list** books while the program is running. The librarian will interact with the program through a text‑based menu.

You have just finished the unit on **singly linked lists** and are asked to implement the underlying data structure for this task.

## Requirements  
Write a C (or C++) program that fulfills the following specifications:

1. **Data Representation**  
   - Define a `struct Book` that contains:
     - `char isbn[14];`   // 13‑character ISBN plus terminating null  
     - `char title[101];` // up to 100 characters + null  
     - `char author[51];` // up to 50 characters + null  
     - `int  year;`  
   - Implement a **singly linked list** where each node stores a `Book` and a pointer to the next node.

2. **Menu‑driven Interface** (displayed repeatedly until the user chooses to exit)  
   - **1. Add a new book** – Prompt for the book’s fields and insert the new node at the **head** of the list.  
   - **2. Remove a book** – Prompt for an ISBN; if a node with that ISBN exists, delete it and free its memory; otherwise print “Book not found.”  
   - **3. Search for a book** – Prompt for an ISBN; if found, display the book’s details (see function requirement below); otherwise print “Book not found.”  
   - **4. List all books** – Traverse the list and display every stored book in the order they appear in the list.  
   - **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.

3. **Functionality Requirements**  
   - All input should be read from `stdin`; all output to `stdout`.  
   - The program must **not** leak memory (every allocated node is freed before program termination).  
   - The program should handle an empty list gracefully (e.g., searching or listing when no books have been added).

4. **Error Handling**  
   - If the user selects an invalid menu option, print “Invalid choice, please try again.” and redisplay the menu.  
   - If the user attempts to add a book whose ISBN already exists in the list, print “Duplicate ISBN – book not added.” and do not insert a new node.

## Example Input / Output  

```
=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 1

Enter ISBN (13 chars): 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1988
Book added.

=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 4

--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1988
--- End of List ---

=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 3

Enter ISBN to search: 9780131103627

ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1988

=== Library Book Manager ===
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented with a `struct Book` as described above.  
- **Display Function** – The logic for showing the details of **one specific book** (used by both the “Search” and “List” operations) must be placed in a function with the exact prototype:  
  ```c
  void displayBook(const struct Book *b);
  ```  
- **Modular Design** – Apart from `main()`, you may create any number of helper functions **but** the program must contain **exactly one** function whose purpose is to free the entire list; its prototype must be:  
  ```c
  void freeList(struct BookNode *head);
  ```  
- **Menu Exit Option** – The menu must contain the option **5. EXIT** (or the keyword `EXIT`) that terminates the program.  

*Note: The problem is intentionally scoped for students who have just learned singly linked lists, so avoid using library containers (e.g., `std::list`).*

---

## Problem 35 - openai/gpt-oss-120b - Iteration 25
# STEP 1: PROBLEM  

## Background  
The kingdom of **Algoria** maintains a magical inventory of enchanted artifacts that adventurers discover during their quests.  
Because the number of artifacts is unknown in advance and items are frequently added or removed as quests progress, the royal archivist has decided to store the inventory in a **singly linked list**.  

Your task is to write a small console program that lets a user manage this inventory. The program will be used by first‑year CS students to demonstrate that they understand how to implement a singly linked list, how to manipulate nodes, and how to separate concerns into functions.

---

## Requirements  

1. **Data representation**  
   - Each artifact is described by three fields:  
     - `int id` – a unique positive identifier.  
     - `char name[31]` – the artifact’s name (max 30 characters, no spaces required).  
     - `int power` – an integer representing the artifact’s magical power level.  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   - **1. Insert artifact** – Prompt for `id`, `name`, and `power`; insert the new node at the **head** of the list.  
   - **2. Delete artifact** – Prompt for an `id`; locate the node with that id and remove it from the list. If the id does not exist, print “Artifact not found.”  
   - **3. Search artifact** – Prompt for an `id`; if found, display the artifact’s details using the required `displayArtifact` function; otherwise print “Artifact not found.”  
   - **4. List all artifacts** – Traverse the list from head to tail and display each artifact’s details (again using `displayArtifact`). If the list is empty, print “Inventory is empty.”  
   - **0. EXIT** – Terminate the program.  

3. **Input validation** – The program should handle non‑numeric menu choices gracefully by re‑displaying the menu.  

4. **Memory management** – All allocated nodes must be freed before the program exits.

---

## Example Interaction  

```
=== Algoria Artifact Inventory ===
1) Insert artifact
2) Delete artifact
3) Search artifact
4) List all artifacts
0) EXIT
Choose an option: 1
Enter id: 101
Enter name: PhoenixFeather
Enter power: 250
Artifact inserted.

=== Algoria Artifact Inventory ===
1) Insert artifact
2) Delete artifact
3) Search artifact
4) List all artifacts
0) EXIT
Choose an option: 4
--- Artifact List ---
ID: 101 | Name: PhoenixFeather | Power: 250

=== Algoria Artifact Inventory ===
1) Insert artifact
2) Delete artifact
3) Search artifact
4) List all artifacts
0) EXIT
Choose an option: 3
Enter id to search: 999
Artifact not found.

=== Algoria Artifact Inventory ===
1) Insert artifact
2) Delete artifact
3) Search artifact
4) List all artifacts
0) EXIT
Choose an option: 0
Goodbye!
```

---

### CONSTRAINTS  

- The primary data entity **must** be represented with a `struct` named `Artifact`.  
- The logic for displaying the details of **one** artifact **must** be placed in a function with the exact prototype:  

  ```c
  void displayArtifact(const Artifact *a);
  ```  

- The program must contain **exactly one** additional user‑defined function besides `main()` (i.e., `displayArtifact`). All other operations (insert, delete, search, list) must be performed directly inside `main()` or within helper code that is **not** a separate function.  
- Because a menu is required, the menu **must** include an explicit option to **EXIT** the program, numbered `0`.  

*Note: The constraint about a single extra function is intentional to force students to manage list operations inline, reinforcing their understanding of pointer manipulation.*

---

## Problem 36 - openai/gpt-oss-120b - Iteration 26
# STEP 1: PROBLEM  

**Background**  
The campus library is upgrading its software and needs a simple command‑line tool to keep track of the books that are currently on the shelves. Because the number of books changes frequently (new acquisitions, lost or withdrawn copies), the library wants the data stored in a dynamic structure that can grow and shrink at runtime. Your task is to write a small program that manages the collection of books using a **singly linked list**.

**Program Requirements**  

Implement a menu‑driven application that supports the following operations:

1. **Add a new book** – Prompt the user for the book’s ISBN (string, max 13 characters), title, and author, then insert the new book at the **head** of the list.  
2. **Remove a book** – Ask for an ISBN and delete the first node whose ISBN matches. If no such book exists, print an appropriate message.  
3. **Search for a book** – Ask for an ISBN and display the details of the matching book (title and author). If the book is not found, report it.  
4. **List all books** – Traverse the list and display every stored book in the order they appear in the linked list (i.e., from head to tail).  
5. **Exit** – Terminate the program gracefully.

All input should be read from `stdin`; all output should be written to `stdout`. The program must continue to display the menu after completing an operation, until the user chooses the **Exit** option.

**Simple Example**  

```
--- Library Book Manager ---
1. Add a book
2. Remove a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added.

--- Library Book Manager ---
1. Add a book
2. Remove a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 4
Books in the library:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- Library Book Manager ---
1. Add a book
2. Remove a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 5
Goodbye!
```

**### CONSTRAINTS**  

- The primary data entity **must** be represented by a `struct` named `BookNode` that contains at least the fields `isbn`, `title`, `author`, and a pointer to the next node.  
- The logic for displaying the details of **one specific book** must be placed in a function with the exact prototype:  

  ```c
  void displayBook(const BookNode *node);
  ```  

- Apart from `main`, you may create **exactly two additional functions**: one for displaying a single book (`displayBook`) and one helper function of your choice (e.g., for freeing the list). No other functions are allowed.  
- The program **must** present a textual menu and **must** include a menu option to **EXIT** the program (option 5 in the example). Selecting this option ends the program.  

Follow good coding style: check for `NULL` pointers, avoid memory leaks, and keep user prompts clear.

---

## Problem 37 - openai/gpt-oss-120b - Iteration 27
# STEP 1: PROBLEM  

## Background  
The campus library is transitioning from a paper‑based catalog to a simple digital system that runs on a single‑board computer in the student lounge. The librarian, Maya, wants a tiny program that can store, retrieve, and delete information about books while the computer is powered on. Because the memory is limited and the data set is expected to be modest, a **singly linked list** is the most appropriate structure.

Your task is to write that program. It will let the user add new books, list all stored books, search for a book by its ISBN, and remove a book. The program should run until the user chooses to quit.

## Requirements  

1. **Data representation**  
   * Define a `struct Book` that holds the following fields:  
     - `char title[101]` – the title of the book (max 100 characters, null‑terminated).  
     - `char author[51]` – the author's name (max 50 characters).  
     - `unsigned long isbn` – a 13‑digit ISBN number (you may treat it as an unsigned long).  
     - `struct Book *next` – pointer to the next node in the list.  

2. **Menu‑driven interface** (displayed repeatedly until the user exits)  
   * **1. Add a book** – Prompt for title, author, and ISBN, then insert the new node at the **end** of the list.  
   * **2. List all books** – Traverse the list and print each book’s details in the order they were added.  
   * **3. Find a book by ISBN** – Ask for an ISBN, search the list, and display the matching book (or a “not found” message).  
   * **4. Delete a book by ISBN** – Ask for an ISBN, remove the first node whose ISBN matches, and free its memory. If the ISBN is not present, report it.  
   * **5. EXIT** – Terminate the program gracefully, freeing any remaining nodes.  

3. **Functionality**  
   * The logic for displaying the details of **ONE** specific book must be encapsulated in a function named `void displayBook(const struct Book *b);`.  
   * All other operations (add, list, find, delete) may be implemented as separate functions, but **no more than three** additional functions may be created besides `main` and `displayBook`.  

4. **Robustness**  
   * The program must not crash on empty input or when the list is empty.  
   * All dynamically allocated memory must be released before the program ends.  

## Example Input / Output  

```
=== Library Catalog ===
1) Add a book
2) List all books
3) Find a book by ISBN
4) Delete a book by ISBN
5) EXIT
Choose an option: 1

Enter title: The Pragmatic Programmer
Enter author: Andrew Hunt and David Thomas
Enter ISBN (13 digits): 9780135957059
Book added successfully!

=== Library Catalog ===
1) Add a book
2) List all books
3) Find a book by ISBN
4) Delete a book by ISBN
5) EXIT
Choose an option: 2

--- Book List ---
ISBN: 9780135957059
Title: The Pragmatic Programmer
Author: Andrew Hunt and David Thomas
-----------------

=== Library Catalog ===
1) Add a book
2) List all books
3) Find a book by ISBN
4) Delete a book by ISBN
5) EXIT
Choose an option: 3

Enter ISBN to search: 9780135957059
ISBN: 9780135957059
Title: The Pragmatic Programmer
Author: Andrew Hunt and David Thomas

=== Library Catalog ===
1) Add a book
2) List all books
3) Find a book by ISBN
4) Delete a book by ISBN
5) EXIT
Choose an option: 4

Enter ISBN to delete: 9780135957059
Book with ISBN 9780135957059 deleted.

=== Library Catalog ===
1) Add a book
2) List all books
3) Find a book by ISBN
4) Delete a book by ISBN
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described above.  
- **Display Function** – The details of a single book must be printed by a function exactly named `displayBook`. No other function may perform this printing.  
- **Function Count** – Apart from `main` and `displayBook`, you may create **at most three** additional functions (e.g., `addBook`, `listBooks`, `findBook`, `deleteBook`). Exceeding this limit will be considered a violation.  
- **Menu Exit Option** – The menu must contain an explicit option labeled **5) EXIT** (or the word “EXIT”) that terminates the program.  

*All requirements and constraints are mandatory; failure to satisfy any will result in a loss of points.*

---

## Problem 38 - openai/gpt-oss-120b - Iteration 28
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its catalogue system.  The librarian wants a tiny command‑line utility that can keep track of **books** while the program is running.  Each book has a **title**, an **author**, and a **unique integer ID**.  The utility will let a user add new books, delete a book by its ID, search for a book by its ID, and display the whole collection.  The data must be stored in a **singly linked list** that the student implements from scratch.

## Requirements  
Write a C (or C++) program that provides the following functionality through a simple text menu:

1. **Add a Book** – Prompt the user for an integer ID, a title (single‑line string, up to 100 characters), and an author (single‑line string, up to 100 characters). Insert the new book at the **head** of the linked list.  
2. **Delete a Book** – Prompt for an integer ID and remove the node whose ID matches. If no such book exists, print an informative message.  
3. **Search for a Book** – Prompt for an integer ID and display the book’s details (ID, title, author) if found; otherwise, indicate that the book is not in the list.  
4. **Display All Books** – Traverse the list from head to tail and print each book’s details on a separate line. If the list is empty, print “No books stored.”  
5. **Exit** – Terminate the program gracefully.

All menu options must be numbered, and the menu must be displayed after each operation until the user chooses the exit option.

## Example Input / Output  

```
=== Library Book Manager ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. Exit
Choose an option: 1

Enter Book ID: 101
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added.

=== Library Book Manager ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. Exit
Choose an option: 1

Enter Book ID: 202
Enter Title: Introduction to Algorithms
Enter Author: Cormen et al.
Book added.

=== Library Book Manager ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. Exit
Choose an option: 4

ID: 202 | Title: Introduction to Algorithms | Author: Cormen et al.
ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Book Manager ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. Exit
Choose an option: 3

Enter Book ID to search: 101
ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Book Manager ===
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a book) **must be defined using a `struct`** named `BookNode` that contains the fields `int id; char title[101]; char author[101]; struct BookNode *next;`.  
2. **Display Function** – The logic for showing the details of **ONE specific book** (used by the Search operation) **must be placed in a function called `void displayBook(const BookNode *node);`**.  
3. **Modularity** – Apart from `main()`, you may create **no more than two additional functions** (e.g., `addBook`, `deleteBook`, `searchBook`, `displayAll`). Any extra helper functions will be considered a violation.  
4. **Menu Exit Option** – The menu **must include an explicit option to EXIT the program** (option number 5 in the example). Selecting this option ends the program.  

*All other aspects of the program (input handling, memory management, etc.) are left to the student’s discretion.*

---

## Problem 39 - openai/gpt-oss-120b - Iteration 29
# STEP 1: PROBLEM  

## Background  
The city of **Byteville** runs a small bike‑sharing service. Each bike is identified by a unique integer ID and stores the total number of kilometers it has been ridden. The service wants a simple console program that can keep track of the bikes as they are added, removed, and queried throughout the day. Because the fleet is constantly changing, a **singly linked list** is the most appropriate structure for the task.

## Requirements  
Write a C (or C++) program that implements the bike‑fleet manager using a singly linked list. The program must provide a text‑based menu that allows the user to perform the following operations:

1. **Add a bike** – Prompt for the bike’s ID (integer) and its initial mileage (float). Insert the new bike at the **head** of the list. If a bike with the same ID already exists, display an error and do not insert.  
2. **Remove a bike** – Prompt for a bike ID and delete the node containing that bike. If the ID is not found, display an appropriate message.  
3. **Update mileage** – Prompt for a bike ID and the additional kilometers ridden (float). Add the value to the bike’s existing mileage. If the bike is not found, report it.  
4. **Display a bike** – Prompt for a bike ID and show its ID and current mileage. If the bike does not exist, inform the user.  
5. **List all bikes** – Traverse the list and print the ID and mileage of every bike in the order they are stored (head to tail).  
6. **Exit** – Terminate the program gracefully.

The program should continue to display the menu after each operation until the user chooses the **Exit** option.

## Example Input / Output  

```
--- Bike Fleet Manager ---
1) Add a bike
2) Remove a bike
3) Update mileage
4) Display a bike
5) List all bikes
6) Exit
Choose an option: 1
Enter bike ID: 101
Enter initial mileage: 12.5
Bike added.

--- Bike Fleet Manager ---
1) Add a bike
2) Remove a bike
3) Update mileage
4) Display a bike
5) List all bikes
6) Exit
Choose an option: 1
Enter bike ID: 102
Enter initial mileage: 0
Bike added.

--- Bike Fleet Manager ---
1) Add a bike
2) Remove a bike
3) Update mileage
4) Display a bike
5) List all bikes
6) Exit
Choose an option: 4
Enter bike ID to display: 101
Bike ID: 101, Mileage: 12.50 km

--- Bike Fleet Manager ---
1) Add a bike
2) Remove a bike
3) Update mileage
4) Display a bike
5) List all bikes
6) Exit
Choose an option: 5
Bike ID: 102, Mileage: 0.00 km
Bike ID: 101, Mileage: 12.50 km

--- Bike Fleet Manager ---
1) Add a bike
2) Remove a bike
3) Update mileage
4) Display a bike
5) List all bikes
6) Exit
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity (a bike) **must be represented with a `struct`** (or `class` in C++) containing at least the fields `int id; float mileage;` and a pointer to the next node.  
2. **Display Function** – The logic for showing the details of **one specific bike** must be placed in a function named `void displayBike(struct Bike *b);` (or an equivalent signature in C++).  
3. **Modular Design** – Apart from `main()`, the solution may contain **no more than three additional functions** (e.g., for insertion, deletion, and the required `displayBike`).  
4. **Menu Requirement** – The program **must include a menu option to EXIT** the program; in this specification it is option **6**. Selecting this option must cause the program to terminate cleanly.  

*All other implementation details (memory management, input validation, etc.) are left to the student, but the above constraints must be satisfied.*

---

## Problem 40 - openai/gpt-oss-120b - Iteration 30
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its software and needs a simple command‑line tool that allows a librarian to keep track of the books currently on a single shelf. Each book is identified by an ISBN, has a title, and records how many copies are presently placed on that shelf. The librarian will add books to the front of the shelf, remove the first book, and request a display of any single book’s details.  

Your task is to implement this tool using a **singly linked list**. The list will represent the order of books on the shelf, with the head of the list being the book closest to the door.  

## Requirements  

Write a program that provides a **menu‑driven interface** with the following options:

1. **Add a book to the front of the shelf**  
   - Prompt the user for ISBN (string), title (string, may contain spaces), and number of copies (integer).  
   - Insert a new node at the head of the linked list.

2. **Remove the book at the front of the shelf**  
   - Delete the head node and free its memory.  
   - If the list is empty, print a friendly message.

3. **Display details of a specific book**  
   - Prompt the user for an ISBN.  
   - Search the list for a node whose ISBN matches exactly.  
   - If found, call a function named `displayEntity` to print the book’s ISBN, title, and copies.  
   - If not found, inform the user.

4. **List all books on the shelf**  
   - Traverse the list from head to tail, printing each book’s details on its own line.

5. **Exit the program**  
   - Clean up all allocated memory and terminate.

The program should continue to display the menu after completing any operation until the user selects the **Exit** option.

## Example Input / Output  

```
=== Library Shelf Manager ===
1. Add book to front
2. Remove front book
3. Display a book
4. List all books
5. Exit
Choose an option: 1
Enter ISBN: 978-0131103627
Enter title: The C Programming Language
Enter copies: 3
Book added.

=== Library Shelf Manager ===
1. Add book to front
2. Remove front book
3. Display a book
4. List all books
5. Exit
Choose an option: 1
Enter ISBN: 978-0201616224
Enter title: The Pragmatic Programmer
Enter copies: 2
Book added.

=== Library Shelf Manager ===
1. Add book to front
2. Remove front book
3. Display a book
4. List all books
5. Exit
Choose an option: 4
Shelf contents:
ISBN: 978-0201616224 | Title: The Pragmatic Programmer | Copies: 2
ISBN: 978-0131103627 | Title: The C Programming Language | Copies: 3

=== Library Shelf Manager ===
1. Add book to front
2. Remove front book
3. Display a book
4. List all books
5. Exit
Choose an option: 3
Enter ISBN to search: 978-0131103627
--- Book Details ---
ISBN: 978-0131103627
Title: The C Programming Language
Copies: 3

=== Library Shelf Manager ===
1. Add book to front
2. Remove front book
3. Display a book
4. List all books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation:** You **must** use a `struct` (or equivalent language construct) to represent a book node. The struct should contain fields for ISBN, title, copies, and a pointer to the next node.  
- **Display Function:** The logic for printing the details of a single book **must** reside in a function named `displayEntity`. This function receives a pointer/reference to a node and prints its contents in the format shown above.  
- **Menu Requirement:** Because the program is menu‑driven, you **must** include a menu option that **exits** the program (option 5 in the example). Selecting this option should terminate the loop and free any remaining dynamic memory.  
- **Memory Management:** All nodes created with dynamic allocation must be properly freed either when removed or when the program exits.  
- **Single‑File Implementation:** The entire solution should be placed in a single source file (e.g., `main.c`, `program.cpp`, `list.py`, etc.). Apart from `main`, you may create additional helper functions, but the core display logic must be in `displayEntity`.  

Feel free to choose any programming language that supports structs/classes and dynamic memory (C, C++, Java, Python, etc.), but adhere to the constraints above.

---

## Problem 41 - llama-3.3-70b-versatile - Iteration 16
# STEP 1: PROBLEM
In a university setting, student records are crucial for efficient management. To keep track of student information, we can utilize a data structure like a Singly Linked List. The goal is to design a program that implements a Singly Linked List to store student records, allowing for the addition, deletion, and display of student information.

The program's context is a simple student record management system where each student has a unique ID, name, and GPA. The system should be able to add new students, remove existing students by their ID, and display all student records or the details of a specific student.

### REQUIREMENTS
1. The program must allow users to add new student records to the Singly Linked List.
2. The program must enable the removal of a student record by their unique ID from the Singly Linked List.
3. The program must provide the functionality to display all student records in the Singly Linked List.
4. The program must have the option to display the details of a specific student by their ID.

### EXAMPLE
Input:
- Add a student with ID = 1, Name = "John Doe", GPA = 3.5
- Add a student with ID = 2, Name = "Jane Doe", GPA = 3.8
- Display all students
- Remove the student with ID = 1
- Display all students

Output (after adding students and before removal):
1. ID: 1, Name: John Doe, GPA: 3.5
2. ID: 2, Name: Jane Doe, GPA: 3.8

Output (after removing the student with ID = 1):
1. ID: 2, Name: Jane Doe, GPA: 3.8

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of all students must be in a function called 'displayAllStudents'.
- The solution must be implemented with a menu-driven approach.
- The menu must include options to add a student, remove a student, display all students, display a specific student, and exit the program.
- The option to exit the program must be clearly labeled as '5. Exit'.

### MENU CONSTRAINTS
The menu must be as follows:
1. Add a student
2. Remove a student
3. Display all students
4. Display a specific student
5. Exit

The program should continue to run and display the menu until the user chooses the 'Exit' option (option 5).

---

## Problem 42 - llama-3.3-70b-versatile - Iteration 17
# STEP 1: PROBLEM
You are a librarian at a university, and you need to manage a collection of books in a library. The library uses a singly linked list to store information about each book, including the book's title, author, publication year, and the number of copies available. You want to create a program that allows you to add, remove, and search for books in the library, as well as display the details of all books or a specific book.

The program should have the following functionality:
1. Add a new book to the library.
2. Remove a book from the library by its title.
3. Search for a book by its title or author.
4. Display the details of all books in the library.
5. Display the details of a specific book.

### EXAMPLE
If the library has the following books:
- Book 1: Title = "Introduction to Computer Science", Author = "John Smith", Publication Year = 2010, Copies = 5
- Book 2: Title = "Data Structures and Algorithms", Author = "Jane Doe", Publication Year = 2015, Copies = 3

The program should be able to add a new book, remove "Introduction to Computer Science", search for books by "John Smith", display all books, and display the details of "Data Structures and Algorithms".

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle all the menu options.
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book
  3. Search for a book
  4. Display all books
  5. Display a specific book
  6. EXIT (to exit the program)
- The program should handle cases where the library is empty or a book is not found.

### INPUT/OUTPUT EXAMPLE
Input:
```
1. Add a new book
Title: Introduction to Programming
Author: Bob Johnson
Publication Year: 2020
Copies: 2
```
Output:
```
Book added successfully!
```
Input:
```
4. Display all books
```
Output:
```
Book 1:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2010
Copies: 5

Book 2:
Title: Data Structures and Algorithms
Author: Jane Doe
Publication Year: 2015
Copies: 3

Book 3:
Title: Introduction to Programming
Author: Bob Johnson
Publication Year: 2020
Copies: 2
```

---

## Problem 43 - llama-3.3-70b-versatile - Iteration 18
# STEP 1: PROBLEM
You are the administrator of a university library, and you want to create a simple system to manage the borrowing and returning of books. The system should store the details of each book in a singly linked list, where each node represents a book with its title, author, and status (available or borrowed).

The library has a large collection of books, and the system should be able to efficiently add, remove, and search for books. The system should also be able to display the details of all books or a specific book.

Here is a precise list of requirements for the program's functionality:
1. The program should allow users to add a new book to the library.
2. The program should allow users to remove a book from the library by its title.
3. The program should allow users to search for a book by its title or author.
4. The program should allow users to display the details of all books in the library.
5. The program should allow users to display the details of a specific book.
6. The program should allow users to borrow a book by its title.
7. The program should allow users to return a book by its title.

Simple Example of expected Input/Output:
- Add a new book: "Introduction to Computer Science" by "John Doe"
- Display all books: 
  - "Introduction to Computer Science" by "John Doe" (available)
  - "Data Structures" by "Jane Smith" (available)
- Search for a book by title: "Introduction to Computer Science"
  - "Introduction to Computer Science" by "John Doe" (available)
- Borrow a book: "Introduction to Computer Science"
  - "Introduction to Computer Science" by "John Doe" (borrowed)

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a menu-driven approach.
- The menu should include the following options:
  1. Add a new book
  2. Remove a book
  3. Search for a book
  4. Display all books
  5. Display a specific book
  6. Borrow a book
  7. Return a book
  8. EXIT (to exit the program)
- If a menu is implemented, the program must include a specific menu option to EXIT the program (option 8).

---

## Problem 44 - llama-3.3-70b-versatile - Iteration 19
# STEP 1: PROBLEM
You are the administrator of a university library, and you want to create a system to manage the borrowing and returning of books. The system should store information about each book, including its title, author, and whether it is currently borrowed or not. To implement this system, you will use a singly linked list, where each node represents a book.

The library has the following requirements for the system:
1. The system should allow users to add new books to the library.
2. The system should allow users to remove books from the library.
3. The system should allow users to borrow a book.
4. The system should allow users to return a book.
5. The system should display all the books in the library.
6. The system should display the details of a specific book.

Here's a simple example of how the system could work:
- If the library has two books, "Book1" by "Author1" and "Book2" by "Author2", and both are available, the system should display both books when the user chooses to display all books.
- If the user chooses to borrow "Book1", the system should update the status of "Book1" to "borrowed" and display a message confirming the borrowing.
- If the user then chooses to return "Book1", the system should update the status of "Book1" to "available" and display a message confirming the return.

### CONSTRAINTS
- Must use a 'struct' to represent a book, which should include the title, author, and a boolean indicating whether the book is borrowed or not.
- The logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must be implemented using a menu-driven approach.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book
  3. Borrow a book
  4. Return a book
  5. Display all books
  6. Display a specific book
  7. EXIT
- The program should exit when the user chooses the EXIT option (option 7).

---

## Problem 45 - llama-3.3-70b-versatile - Iteration 20
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a small library. The library uses a simple system to keep track of its books, and you want to implement this system using a singly linked list. Each book has a unique title, author, and publication year.

The library's system should be able to perform the following operations:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all the books in the collection.
4. Search for a book by its title and display its details if found.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit the program
- The program should exit when the user chooses the 'Exit the program' option (option 5).

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
3
Book1 by Author1 (2020)
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
4
Enter book title to search: Book1
Book1 by Author1 (2020)
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
5
```
Example Output:
```
The program will display the menu and perform the chosen operations.
```

---

## Problem 46 - llama-3.3-70b-versatile - Iteration 21
# STEP 1: PROBLEM
You are the curator of a local library, and you want to create a simple system to manage the borrowing and returning of books. The system should use a singly linked list to store information about the books. Each book has a unique title, author, and status (available or borrowed).

Background:
The library has a collection of books, and users can borrow and return books. You need to keep track of which books are available and which are borrowed.

Requirements:
1. Create a singly linked list to store book information.
2. Implement functions to add a new book to the list, remove a book from the list, and display all books in the list.
3. Implement a function to borrow a book (change its status to "borrowed") and another function to return a book (change its status to "available").
4. Display the details of all books in the list.

Example of expected Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Borrow a book
4. Return a book
5. Display all books
6. EXIT

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling

Choose an option: 5
Book Title: Harry Potter, Author: J.K. Rowling, Status: available

Choose an option: 3
Enter book title: Harry Potter

Choose an option: 5
Book Title: Harry Potter, Author: J.K. Rowling, Status: borrowed
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented with a single linked list.
- To exit the program, the user must choose the 'EXIT' option (option 6).
- If a menu is implemented, it must include options to add, remove, borrow, and return a book, as well as display all books, and exit the program. 

Note: The program should handle cases where a user tries to borrow a book that is already borrowed or return a book that is not borrowed. It should also handle cases where a user tries to remove a book that does not exist in the list.

---

## Problem 47 - llama-3.3-70b-versatile - Iteration 22
# STEP 1: PROBLEM
In a university setting, it's common for students to enroll in various courses. To manage the courses and their respective students efficiently, the university wants to develop a system that utilizes a singly linked list data structure. The system should allow for adding courses, displaying all courses, and finding a specific course by its name.

Background:
The university offers a wide range of courses, and each course has a unique name and a list of enrolled students. The system should enable the university administrators to manage these courses and their enrolled students.

Requirements:
1. The program should allow administrators to add a new course to the system.
2. The program should display all the courses in the system.
3. The program should enable administrators to find a specific course by its name and display its details.
4. The program should have a menu-driven interface for easy navigation.

Example:
If we have two courses, "Data Structures" and "Algorithms", with "John" and "Alice" enrolled in "Data Structures" respectively, the program should be able to display all courses, add a new course, and find a specific course by its name.

Input:
- Add course: "Machine Learning"
- Enrolled students: "Bob", "Charlie"
- Find course: "Data Structures"

Output:
- All courses: "Data Structures", "Algorithms", "Machine Learning"
- Course details: "Data Structures" - "John", "Alice"

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Course).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu-driven interface.
- The menu-driven interface must include the following options:
  1. Add a new course
  2. Display all courses
  3. Find a specific course
  4. EXIT the program (Option 4 or 'exit' keyword) 

Note: The 'struct' to represent the Course entity should have the following members: course_name and enrolled_students (as a linked list). The linked list for enrolled students should be implemented using a separate 'struct' to represent each student node.

---

## Problem 48 - llama-3.3-70b-versatile - Iteration 23
# STEP 1: PROBLEM
Imagine that you are the administrator of a university's library system. The library has a collection of books, and you want to create a simple program to manage these books. You decide to use a singly linked list to store the book information. Each book has a unique title, author, and publication year.

The program should allow users to perform the following operations:
1. Add a new book to the list.
2. Remove a book from the list by its title.
3. Display all the books in the list.
4. Search for a book by its title and display its details.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book, with fields for title, author, and publication year.
- The solution must be implemented with a single linked list.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The program must have a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit the program
- To exit the program, the user must select option 5.

### EXAMPLE INPUT/OUTPUT
Example input:
```
1. Add a new book
Enter book title: Introduction to CS
Enter book author: John Smith
Enter book publication year: 2020
2. Add a new book
Enter book title: Data Structures
Enter book author: Jane Doe
Enter book publication year: 2019
3. Display all books
```
Example output:
```
Book 1:
Title: Introduction to CS
Author: John Smith
Publication Year: 2020
Book 2:
Title: Data Structures
Author: Jane Doe
Publication Year: 2019
```
Note: The program should handle cases where the user tries to remove or search for a book that does not exist in the list.

---

## Problem 49 - llama-3.3-70b-versatile - Iteration 24
# STEP 1: PROBLEM
In a library management system, books are organized using a singly linked list. Each book has a unique identifier (ID), title, author, and publication year. The system should allow users to add new books, remove existing books, display all books, and search for a book by ID.

Background:
The library management system currently uses a manual method to track books, which is time-consuming and prone to errors. To improve efficiency, the library wants to implement a computerized system using a singly linked list to store and manage book information.

Requirements:
1. The program should allow users to add new books to the linked list.
2. The program should allow users to remove existing books from the linked list by ID.
3. The program should display all books in the linked list.
4. The program should allow users to search for a book by ID and display its details.

Example:
Input: 
- Add book with ID: 1, title: "Book1", author: "Author1", publication year: 2020
- Add book with ID: 2, title: "Book2", author: "Author2", publication year: 2021
- Display all books
- Search for book with ID: 1

Output: 
- Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020
- Book ID: 2, Title: Book2, Author: Author2, Publication Year: 2021
- Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020

### CONSTRAINTS
1. Must use a 'struct' to represent the Book entity.
2. Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
3. The solution must be implemented with a menu-driven approach.
4. The menu should have the following options:
   - Option 1: Add a new book
   - Option 2: Remove a book by ID
   - Option 3: Display all books
   - Option 4: Search for a book by ID
   - Option 5: EXIT the program

Note: The program should exit when the user selects Option 5.

---

## Problem 50 - llama-3.3-70b-versatile - Iteration 25
# STEP 1: PROBLEM
In a university setting, it's common to manage student records efficiently. To practice implementing data structures, you will create a simple student record management system using a Singly Linked List. The system should allow users to add, remove, and display student records.

The background story is that the university wants to automate its student record-keeping process. Each student record consists of a unique student ID, name, and GPA. The system should be able to handle a dynamic number of student records.

The requirements for the program's functionality are as follows:
1. The program should allow users to add a new student record to the system.
2. The program should allow users to remove a student record by student ID.
3. The program should allow users to display all student records.
4. The program should allow users to search for a student record by student ID and display the details of the student.

An example of expected input/output is:
- Add a student record: Enter student ID, name, and GPA (e.g., 12345, John Doe, 3.5).
- Remove a student record: Enter student ID (e.g., 12345).
- Display all student records: The program displays a list of all student records in the system (e.g., 12345 John Doe 3.5, 67890 Jane Doe 3.8).
- Search for a student record: Enter student ID (e.g., 12345), and the program displays the details of the student (e.g., Student ID: 12345, Name: John Doe, GPA: 3.5).

### CONSTRAINTS
- The solution must be implemented using a Singly Linked List.
- Must use a 'struct' to represent the primary data entity (student record).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The program must include a menu with the following options:
  1. Add a student record
  2. Remove a student record
  3. Display all student records
  4. Search for a student record
  5. EXIT the program
- The EXIT option must be clearly labeled as option 5, and the program should terminate when this option is selected.

Example menu:
```
Student Record Management System
1. Add a student record
2. Remove a student record
3. Display all student records
4. Search for a student record
5. EXIT
Enter your choice:
```

---

## Problem 51 - llama-3.3-70b-versatile - Iteration 26
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a simple system to keep track of books, and you've been asked to implement a data structure to store and manage the books. You decide to use a Singly Linked List to store the books, where each node in the list represents a book.

The background story is that the library has a large collection of books, and the current system is inefficient. The librarian wants to be able to add, remove, and search for books in the collection. The librarian also wants to be able to display the details of all the books in the collection.

The requirements for the program's functionality are:
1. The program must allow the user to add a new book to the collection.
2. The program must allow the user to remove a book from the collection.
3. The program must allow the user to search for a book in the collection by title or author.
4. The program must allow the user to display the details of all the books in the collection.
5. The program must allow the user to display the details of a specific book in the collection.

Here is a simple example of expected input/output:
```
Add a book:
Title: Harry Potter
Author: J.K. Rowling
Year: 1997

Add a book:
Title: The Lord of the Rings
Author: J.R.R. Tolkien
Year: 1954

Display all books:
Harry Potter by J.K. Rowling (1997)
The Lord of the Rings by J.R.R. Tolkien (1954)

Search for a book:
Title: Harry Potter
Found: Harry Potter by J.K. Rowling (1997)

Remove a book:
Title: The Lord of the Rings
Book removed: The Lord of the Rings by J.R.R. Tolkien (1954)

Display all books:
Harry Potter by J.K. Rowling (1997)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book, with fields for title, author, and year.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a Singly Linked List.
- If a menu is implemented, it must include a specific menu option to EXIT the program (option 6).
- The menu options must be:
  1. Add a book
  2. Remove a book
  3. Search for a book
  4. Display all books
  5. Display a specific book
  6. EXIT the program

Note: The program should handle invalid inputs and edge cases, such as attempting to remove a book that does not exist in the collection.

---

## Problem 52 - llama-3.3-70b-versatile - Iteration 27
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a small library. The library uses a simple system to keep track of the books, and you want to implement this system using a Singly Linked List. Each book has a unique ID, title, author, and publication year.

The library system should allow users to perform the following operations:
1. Add a new book to the collection.
2. Remove a book by its ID.
3. Display the details of all books in the collection.
4. Search for a book by its title or author.
5. Display the details of a specific book by its ID.

The system should have a simple menu-driven interface where users can choose the operation they want to perform.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented using a Singly Linked List.
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Search for a book
  5. Display a specific book
  6. EXIT the program (option 6)

### EXAMPLE INPUT/OUTPUT
Example input:
```
1. Add a new book
Enter book ID: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020

2. Add a new book
Enter book ID: 2
Enter book title: Book2
Enter book author: Author2
Enter book publication year: 2021

3. Display all books
Book ID: 1, Title: Book1, Author: Author1, Year: 2020
Book ID: 2, Title: Book2, Author: Author2, Year: 2021

4. Display a specific book
Enter book ID: 1
Book ID: 1, Title: Book1, Author: Author1, Year: 2020
```
Note: The actual implementation may vary based on the programming language used. The above example is a simplified representation of the expected input/output.

---

## Problem 53 - llama-3.3-70b-versatile - Iteration 28
# STEP 1: PROBLEM
You are the administrator of a university library, responsible for managing the catalog of books. The library uses a simple system to keep track of books, and you want to implement this system using a Singly Linked List data structure. Each book has a unique title, author, and publication year. You need to design a program that allows you to add books to the catalog, remove books, display all books, and search for a specific book by title.

The program should have the following functionality:
1. Add a book to the catalog: The user should be able to input the title, author, and publication year of a book, and the program should add this book to the catalog.
2. Remove a book from the catalog: The user should be able to input the title of a book, and the program should remove this book from the catalog if it exists.
3. Display all books in the catalog: The program should display the details of all books in the catalog.
4. Search for a book by title: The user should be able to input the title of a book, and the program should display the details of this book if it exists in the catalog.

### EXAMPLE
Input:
```
Add book: "Introduction to Computer Science", "Author1", 2020
Add book: "Data Structures", "Author2", 2019
Display all books:
Remove book: "Introduction to Computer Science"
Display all books:
Search book: "Data Structures"
```
Output:
```
Book added successfully: "Introduction to Computer Science" by Author1 (2020)
Book added successfully: "Data Structures" by Author2 (2019)
All books:
- "Introduction to Computer Science" by Author1 (2020)
- "Data Structures" by Author2 (2019)
Book removed successfully: "Introduction to Computer Science"
All books:
- "Data Structures" by Author2 (2019)
Book found: "Data Structures" by Author2 (2019)
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of a specific book must be in a function called `displayBook`.
- The solution must be implemented using a Singly Linked List.
- If a menu is implemented, it must include the following options:
  1. Add book
  2. Remove book
  3. Display all books
  4. Search book
  5. EXIT (to exit the program)
- If a menu is implemented, the program should continue to run and display the menu until the user chooses the EXIT option.

---

## Problem 54 - llama-3.3-70b-versatile - Iteration 29
# STEP 1: PROBLEM
Imagine you are the administrator of a university library, and you want to manage the books in the library using a singly linked list data structure. Each book has a unique identifier (ID), title, author, and publication year. You want to create a program that allows you to add, remove, and display books in the library.

The program should have the following functionality:
1. Add a new book to the library.
2. Remove a book from the library by its ID.
3. Display all books in the library.
4. Display the details of a specific book by its ID.

Here is a simple example of expected input/output:
- Add a new book: ID = 1, Title = "Introduction to CS", Author = "John Doe", Publication Year = 2020
- Add a new book: ID = 2, Title = "Data Structures", Author = "Jane Smith", Publication Year = 2019
- Display all books:
  - ID = 1, Title = "Introduction to CS", Author = "John Doe", Publication Year = 2020
  - ID = 2, Title = "Data Structures", Author = "Jane Smith", Publication Year = 2019
- Remove a book by ID = 1
- Display all books:
  - ID = 2, Title = "Data Structures", Author = "Jane Smith", Publication Year = 2019

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The solution must be implemented with a menu-driven approach.
- The menu options are:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Display a specific book by ID
  5. EXIT the program
- The program must exit when the user chooses the 'EXIT' option (option 5). 

### ADDITIONAL NOTES
- The program should handle cases where a book with the same ID already exists in the library when adding a new book.
- The program should handle cases where a book with the specified ID does not exist in the library when removing or displaying a book.

---

## Problem 55 - llama-3.3-70b-versatile - Iteration 30
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the collection of books using a singly linked list. Each book in the collection has a unique identifier (ID), title, author, and publication year. The librarian needs a program to efficiently add, remove, and display books in the collection.

## BACKGROUND
The librarian currently uses a manual system to keep track of the books, which is time-consuming and prone to errors. The program should allow the librarian to easily manage the collection and perform common operations.

## REQUIREMENTS
The program must have the following functionality:
1. Add a new book to the collection.
2. Remove a book from the collection by its ID.
3. Display all books in the collection.
4. Display the details of a specific book by its ID.

## EXAMPLE
Input: 
- Add book with ID 1, title "Book1", author "Author1", and publication year 2020.
- Add book with ID 2, title "Book2", author "Author2", and publication year 2021.
- Display all books.
- Remove book with ID 1.
- Display all books.

Output:
- After adding two books and displaying all books: 
  Book 1: ID 1, Title: Book1, Author: Author1, Year: 2020
  Book 2: ID 2, Title: Book2, Author: Author2, Year: 2021
- After removing book with ID 1 and displaying all books:
  Book 1: ID 2, Title: Book2, Author: Author2, Year: 2021

### CONSTRAINTS
- The solution must be implemented using a singly linked list.
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The solution must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- To exit the program, the user must select option 5 (EXIT). 

Note: The program should handle invalid inputs and edge cases, such as attempting to remove a non-existent book or displaying a book that does not exist.

---

## Problem 56 - llama-3.3-70b-versatile - Iteration 31
# STEP 1: PROBLEM
In a small library, the librarian wants to maintain a catalog of books using a singly linked list. Each book in the catalog has a unique identifier (ID), title, author, and publication year. The librarian needs a program to manage the catalog, including adding new books, removing existing books, and displaying the details of all books or a specific book.

## BACKGROUND
The librarian currently uses a manual system to keep track of the books, which is time-consuming and prone to errors. The proposed program will help the librarian to efficiently manage the catalog and provide quick access to book information.

## REQUIREMENTS
The program must have the following functionalities:
1. Add a new book to the catalog.
2. Remove a book from the catalog by its ID.
3. Display the details of all books in the catalog.
4. Display the details of a specific book by its ID.
5. Search for books by author or title.

## EXAMPLE
For example, if the catalog contains the following books:
- Book 1: ID = 1, Title = "Introduction to Programming", Author = "John Smith", Year = 2010
- Book 2: ID = 2, Title = "Data Structures", Author = "Jane Doe", Year = 2015
- Book 3: ID = 3, Title = "Algorithms", Author = "John Smith", Year = 2018

The program should be able to add a new book, remove a book by its ID, display all books, display a specific book by its ID, and search for books by author or title.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- The logic for displaying the details of all books must be in a function called 'displayCatalog'.
- The logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The program must implement a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Display a specific book by ID
  5. Search for books by author or title
  6. EXIT (to exit the program)
- The solution must be implemented using a singly linked list.

---

## Problem 57 - llama-3.3-70b-versatile - Iteration 32
# STEP 1: PROBLEM
In a library management system, books are stored in a catalog for easy access and management. To efficiently manage the catalog, the library wants to implement a singly linked list data structure to store information about each book. The system should allow users to add, remove, and display books in the catalog.

The library management system should have the following functionality:
1. Add a new book to the catalog.
2. Remove a book from the catalog by its title.
3. Display all books in the catalog.
4. Display the details of a specific book.

### CONSTRAINTS
- Must use a 'struct' to represent a book, which should include the title, author, and publication year.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle user input and menu options.
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT the program (option 5)

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a new book:
Title: "Introduction to CS"
Author: "John Doe"
Publication Year: 2020

Add another book:
Title: "Data Structures"
Author: "Jane Smith"
Publication Year: 2019

Display all books:
1. Introduction to CS by John Doe (2020)
2. Data Structures by Jane Smith (2019)

Display a specific book:
Title: "Introduction to CS"
Book details: Introduction to CS by John Doe (2020)

Remove a book:
Title: "Data Structures"

Display all books:
1. Introduction to CS by John Doe (2020)
```
To exit the program, the user should select option 5 from the menu. The system should handle invalid inputs and provide clear error messages.

---

## Problem 58 - llama-3.3-70b-versatile - Iteration 33
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books borrowed by the students. The librarian needs a system to store and manage the borrowing records. The system should allow the librarian to add, remove, and display the borrowing records. The borrowing record includes the student's name, book title, and the date of borrowing.

## BACKGROUND
The librarian currently uses a manual system to keep track of the borrowing records, which is time-consuming and prone to errors. The librarian wants a computerized system that can efficiently manage the borrowing records.

## REQUIREMENTS
The program should have the following functionality:
1. Add a new borrowing record to the system.
2. Remove a borrowing record from the system based on the student's name.
3. Display all the borrowing records in the system.
4. Display the borrowing records of a specific student.

## EXAMPLE
Input:
```
Add: John, Book1, 2022-01-01
Add: Alice, Book2, 2022-01-05
Display All
Display John
Remove: John
Display All
```
Output:
```
Borrowing Records:
John, Book1, 2022-01-01
Alice, Book2, 2022-01-05

John, Book1, 2022-01-01

Borrowing Records:
Alice, Book2, 2022-01-05
```

### CONSTRAINTS
- Must use a singly linked list to store the borrowing records.
- Must use a 'struct' to represent the borrowing record.
- Logic for displaying the details of all borrowing records must be in a function called 'displayAllRecords'.
- Logic for displaying the details of a specific student's borrowing records must be in a function called 'displayStudentRecords'.
- The solution must be implemented with a single linked list.
- If a menu is implemented, it must include the following options:
  1. Add a new borrowing record
  2. Remove a borrowing record
  3. Display all borrowing records
  4. Display a specific student's borrowing records
  5. EXIT the program (option 5)
- The program must handle invalid inputs and edge cases.

---

## Problem 59 - llama-3.3-70b-versatile - Iteration 34
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a small library. The library uses a simple system to keep track of the books, and you have been asked to create a program to help with this task. The program will use a singly linked list to store information about each book, including the title, author, and publication year.

The program should allow users to add new books to the collection, remove books that are no longer in the collection, and display information about all the books in the collection. The program should also allow users to search for a specific book by title or author.

Here is a precise list of requirements for the program's functionality:
1. The program should create a new node for each book added to the collection.
2. The program should allow users to add new books to the collection.
3. The program should allow users to remove books from the collection.
4. The program should display information about all the books in the collection.
5. The program should allow users to search for a specific book by title or author.

Here is a simple example of expected Input/Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

User selects option 1:
Enter title: "To Kill a Mockingbird"
Enter author: "Harper Lee"
Enter publication year: 1960

User selects option 3:
Title: "To Kill a Mockingbird", Author: "Harper Lee", Publication Year: 1960
```

### CONSTRAINTS
* The solution must be implemented using a singly linked list.
* Must use a 'struct' to represent the primary data entity (Book).
* Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
* If a menu is implemented, it must include a specific menu option to EXIT the program (option 5).
* The program should handle invalid user input (e.g., attempting to remove a book that does not exist).

---

## Problem 60 - llama-3.3-70b-versatile - Iteration 35
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a singly linked list to keep track of the books, where each node represents a book with its title, author, and publication year. You need to design a program to manage this collection.

The program should allow users to perform the following operations:
1. Insert a new book at the beginning of the list.
2. Insert a new book at the end of the list.
3. Delete a book by its title.
4. Search for a book by its title and display its details.
5. Display all books in the collection.
6. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented with a menu-driven approach.
- The program must have a menu option to EXIT the program, which should be option 6.

## Example Input/Output
If the user chooses to insert two books, "Book1" by "Author1" (2020) and "Book2" by "Author2" (2021), and then displays all books, the output should be:
```
Title: Book1
Author: Author1
Year: 2020

Title: Book2
Author: Author2
Year: 2021
```
If the user searches for "Book1", the output should be:
```
Title: Book1
Author: Author1
Year: 2020
```
The menu should look something like this:
```
1. Insert a new book at the beginning of the list.
2. Insert a new book at the end of the list.
3. Delete a book by its title.
4. Search for a book by its title.
5. Display all books.
6. EXIT
```

---

## Problem 61 - llama-3.3-70b-versatile - Iteration 36
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a singly linked list to store information about each book, including its title, author, publication year, and a unique identifier (ID). Your task is to design a program that allows the librarian to manage the collection of books by adding new books, removing existing books, displaying all books, and searching for a specific book by its ID.

The program should provide a menu-driven interface to perform the following operations:
1. Add a new book to the collection.
2. Remove a book from the collection by its ID.
3. Display all books in the collection.
4. Search for a specific book by its ID and display its details.
5. EXIT the program.

### CONSTRAINTS
- The program must use a 'struct' to represent a book, which includes the title, author, publication year, and a unique identifier (ID).
- The logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented using a singly linked list.
- The program must include a menu option to EXIT the program, which is option 5.
- When adding a new book, the program must assign a unique ID to the book, which is one more than the ID of the last added book.

### EXAMPLE
If the program is run with the following input:
- Add a new book with title "Book1", author "Author1", and publication year 2020.
- Add a new book with title "Book2", author "Author2", and publication year 2021.
- Display all books.
- Search for a book with ID 1 and display its details.
- EXIT the program.

The expected output would be:
- Book 1: Book1 by Author1 (2020)
- Book 2: Book2 by Author2 (2021)
- Book details: Book1 by Author1 (2020)

Note: The ID of the first book added is 1, the ID of the second book added is 2, and so on.

---

## Problem 62 - llama-3.3-70b-versatile - Iteration 37
# STEP 1: PROBLEM
In a university setting, student records are crucial for efficient management. To streamline this process, you have been tasked with designing a simple student record system using a singly linked list. The system should allow for adding, deleting, and displaying student records.

Background: 
The student record system will store information about each student, including their unique student ID, name, and grade point average (GPA). The system should be able to handle a dynamic number of student records.

Requirements:
1. The system should allow users to add new student records to the list.
2. The system should allow users to delete a student record by their unique student ID.
3. The system should display all student records.
4. The system should display the details of a specific student record by their unique student ID.

Example of expected Input/Output:
- Add a new student record: If the user chooses to add a new student, the system should prompt for the student's ID, name, and GPA, and then add this record to the list.
- Delete a student record: If the user chooses to delete a student record, the system should prompt for the student's ID and remove the corresponding record from the list if it exists.
- Display all student records: The system should display the ID, name, and GPA of all students in the list.
- Display a specific student record: The system should prompt for a student ID and display the corresponding student's details if the record exists.

### CONSTRAINTS
- Must use a 'struct' to represent a student record.
- Logic for displaying the details of ONE specific student record must be in a function called 'displayStudent'.
- The solution must implement a menu-driven system with the following options:
  1. Add a new student record
  2. Delete a student record
  3. Display all student records
  4. Display a specific student record
  5. EXIT the program
- The program must use a singly linked list to store student records.
- To EXIT the program, the user must choose option 5. 

Note: The menu options and the 'displayStudent' function are mandatory. The program should handle invalid inputs and edge cases appropriately, such as attempting to delete a non-existent record or displaying a record that does not exist.

---

## Problem 63 - llama-3.3-70b-versatile - Iteration 38
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a small library. The library uses a simple system to keep track of the books, where each book has a unique ID, title, author, and publication year. To efficiently manage the collection, you decide to implement a singly linked list data structure to store and manipulate the book records.

The library needs a program that allows users to interact with the book collection. The program should provide the following functionalities:
1. Add a new book to the collection.
2. Remove a book from the collection by its ID.
3. Display all books in the collection.
4. Search for a book by its ID and display its details.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book, containing fields for ID, title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

## Example Input/Output
When the user chooses to add a new book:
```
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Smith
Enter book publication year: 2020
```
The program should then display the added book details:
```
Book ID: 1
Title: Introduction to CS
Author: John Smith
Publication Year: 2020
```
When the user chooses to display all books, the program should list all the books in the collection:
```
Book ID: 1
Title: Introduction to CS
Author: John Smith
Publication Year: 2020

Book ID: 2
Title: Data Structures
Author: Jane Doe
Publication Year: 2019
```
When the user chooses to search for a book by ID:
```
Enter book ID to search: 1
```
The program should display the details of the book with the matching ID:
```
Book ID: 1
Title: Introduction to CS
Author: John Smith
Publication Year: 2020
```
When the user chooses to exit the program (option 5), the program should terminate.

---

## Problem 64 - llama-3.3-70b-versatile - Iteration 39
# STEP 1: PROBLEM
In a library management system, books are organized using a singly linked list. Each book has a unique identifier (ID), title, author, and publication year. The library wants to implement a simple program to manage their book collection. The program should allow users to add books, remove books, display all books, and search for a specific book by ID.

The program will be used by library staff to efficiently manage the book collection. The staff will interact with the program using a menu-driven interface.

## REQUIREMENTS
1. The program must allow users to add a new book to the collection.
2. The program must allow users to remove a book from the collection by ID.
3. The program must display all books in the collection.
4. The program must allow users to search for a specific book by ID and display its details.
5. The program must have a menu-driven interface with the following options:
   - Add a book
   - Remove a book
   - Display all books
   - Search for a book
   - Exit the program

## EXAMPLE INPUT/OUTPUT
Example input:
- Add a book with ID 1, title "Book1", author "Author1", and publication year 2020.
- Add a book with ID 2, title "Book2", author "Author2", and publication year 2021.
- Display all books.
- Search for a book with ID 1.

Example output:
- After adding two books, the program displays:
  Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020
  Book ID: 2, Title: Book2, Author: Author2, Publication Year: 2021
- After searching for a book with ID 1, the program displays:
  Book ID: 1, Title: Book1, Author: Author1, Publication Year: 2020

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The program must be implemented with a single linked list.
- The menu option to EXIT the program is option 5.

Note: The program should be implemented in a programming language such as C or C++. The solution should be efficient, readable, and well-structured.

---

## Problem 65 - llama-3.3-70b-versatile - Iteration 40
# STEP 1: PROBLEM
You are the curator of a local library, and you want to create a system to manage the books in your library. The system should allow you to add, remove, and display books. You have decided to use a singly linked list to store the book information.

Background:
The library has a collection of books, and each book has a unique title, author, and publication year. You want to create a system that can efficiently manage these books.

Functional Requirements:
1. The system should allow users to add a new book to the library.
2. The system should allow users to remove a book from the library by its title.
3. The system should allow users to display all the books in the library.
4. The system should allow users to search for a book by its title and display its details.
5. The system should have a menu-driven interface.

### CONSTRAINTS
1. Must use a 'struct' to represent a book, which has attributes for title, author, and publication year.
2. Logic for displaying the details of one specific book must be in a function called 'displayBook'.
3. The solution must be implemented with a minimum number of functions, including 'main', 'addBook', 'removeBook', 'displayAllBooks', 'searchBook', and 'displayBook'.
4. The system should have a menu with the following options:
   - Option 1: Add a new book
   - Option 2: Remove a book
   - Option 3: Display all books
   - Option 4: Search for a book
   - Option 5: EXIT the program

Example Input/Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 1
Enter book title: Book1
Enter author: Author1
Enter publication year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 3
Book1 by Author1 (2020)

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 5
Exiting the program...
```

---

## Problem 66 - llama-3.3-70b-versatile - Iteration 41
# STEP 1: PROBLEM
In a university setting, it's essential to keep track of student records efficiently. To manage these records, you've been tasked with designing a system that utilizes a Singly Linked List to store student information. Each student record will contain the student's ID, name, and GPA. Your program should allow users to add, remove, and display student records.

## BACKGROUND
The university currently has a manual system for managing student records, which is time-consuming and prone to errors. The new system should be able to store student records in a Singly Linked List and provide options to add, remove, and display records.

## FUNCTIONAL REQUIREMENTS
1. The program should allow users to add a new student record to the Singly Linked List.
2. The program should allow users to remove a student record from the Singly Linked List based on the student's ID.
3. The program should allow users to display all student records in the Singly Linked List.
4. The program should allow users to display a specific student record based on the student's ID.

## EXAMPLE INPUT/OUTPUT
Example Input:
- Add student with ID: 1, Name: John, GPA: 3.5
- Add student with ID: 2, Name: Alice, GPA: 3.8
- Display all students
- Remove student with ID: 1
- Display all students

Example Output:
- After adding students: 
  - Student ID: 1, Name: John, GPA: 3.5
  - Student ID: 2, Name: Alice, GPA: 3.8
- After removing student with ID 1:
  - Student ID: 2, Name: Alice, GPA: 3.8

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (student record).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
3. The solution must be implemented with a single function besides main() to handle the menu and user input.
4. If a menu is implemented:
   - Must include a specific menu option to EXIT the program. The exit option should be '5' or the keyword 'EXIT'.
   - The menu options should be:
     1. Add student
     2. Remove student
     3. Display all students
     4. Display specific student
     5. EXIT 

Note: The program should handle invalid inputs and edge cases, such as removing a non-existent student or displaying a non-existent student record.

---

## Problem 67 - llama-3.3-70b-versatile - Iteration 42
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books borrowed by students. To achieve this, the librarian needs a simple system to store and manage the borrowing records. The system should be able to add new borrowing records, delete existing records, and display all the records. The records should be stored in a singly linked list, where each node represents a borrowing record.

The borrowing record includes the following information:
- Student ID (a unique identifier for each student)
- Book Title
- Borrow Date
- Return Date (initially set to "Not Returned" and updated when the book is returned)

### REQUIREMENTS
1. The program should allow the user to add a new borrowing record.
2. The program should allow the user to delete a borrowing record by Student ID.
3. The program should allow the user to display all borrowing records.
4. The program should allow the user to update the Return Date of a borrowing record by Student ID.
5. The program should display a menu with the above options and an option to exit the program.

### EXAMPLE
Input:
```
Add a new record with Student ID: S001, Book Title: "Introduction to CS", Borrow Date: "2022-01-01"
Add a new record with Student ID: S002, Book Title: "Data Structures", Borrow Date: "2022-01-15"
Display all records
Update Return Date for Student ID: S001, Return Date: "2022-02-01"
Display all records
```
Output:
```
Borrowing Records:
S001 - "Introduction to CS" - Borrowed on: 2022-01-01 - Returned on: Not Returned
S002 - "Data Structures" - Borrowed on: 2022-01-15 - Returned on: Not Returned
Borrowing Records:
S001 - "Introduction to CS" - Borrowed on: 2022-01-01 - Returned on: 2022-02-01
S002 - "Data Structures" - Borrowed on: 2022-01-15 - Returned on: Not Returned
```

### CONSTRAINTS
- Must use a `struct` to represent the borrowing record.
- Must implement the logic for displaying all borrowing records in a function called `displayRecords`.
- Must use a singly linked list to store the borrowing records.
- The menu should have the following options:
  1. Add a new borrowing record
  2. Delete a borrowing record
  3. Display all borrowing records
  4. Update Return Date of a borrowing record
  5. EXIT the program
- To exit the program, the user should select option 5.

---

## Problem 68 - llama-3.3-70b-versatile - Iteration 43
# STEP 1: PROBLEM
In a university setting, it's essential to manage student records efficiently. To achieve this, you are tasked with designing a simple system that utilizes a singly linked list to store and manipulate student data. The system should allow users to add, delete, and display student records.

Background: 
The university wants to create a basic system to manage student information. Each student record consists of a unique student ID, name, and GPA. The system should provide the following functionalities:
- Add a new student record to the list.
- Delete a student record based on the student ID.
- Display all student records in the list.
- Display the details of a specific student record based on the student ID.

Requirements:
1. The program should create a singly linked list to store student records.
2. The program should provide options to add, delete, and display student records.
3. The program should handle invalid inputs and edge cases, such as attempting to delete a non-existent student record.
4. The program should display an error message if the user attempts to add a duplicate student record (i.e., a record with an existing student ID).

Example:
Input: 
- Add student with ID 1, name "John Doe", and GPA 3.5
- Add student with ID 2, name "Jane Doe", and GPA 3.8
- Display all student records
- Delete student with ID 1
- Display all student records

Output:
- After adding the first two students and displaying all records:
  Student ID: 1, Name: John Doe, GPA: 3.5
  Student ID: 2, Name: Jane Doe, GPA: 3.8
- After deleting the student with ID 1 and displaying all records:
  Student ID: 2, Name: Jane Doe, GPA: 3.8

### CONSTRAINTS
1. The solution must be implemented using a singly linked list.
2. Must use a 'struct' to represent the student record.
3. Logic for displaying the details of all student records must be in a function called 'displayAllRecords'.
4. The solution must include a menu-driven interface with the following options:
   - Option 1: Add a new student record
   - Option 2: Delete a student record
   - Option 3: Display all student records
   - Option 4: Display a specific student record
   - Option 5: EXIT the program
5. The program must validate user inputs to prevent crashes or unexpected behavior.

Note: The program should be designed with readability, maintainability, and efficiency in mind. Proper error handling and input validation are crucial to ensure a robust system.

---

## Problem 69 - llama-3.3-70b-versatile - Iteration 44
# STEP 1: PROBLEM
You are the administrator of a university library, responsible for managing the catalog of books. The library uses a simple system to keep track of the books, and you want to implement a Singly Linked List to store the book records. Each book record contains the book's title, author, and publication year.

The library wants to be able to perform the following operations:
1. Add a new book to the catalog.
2. Remove a book from the catalog by its title.
3. Display all the books in the catalog.
4. Search for a book by its title and display its details.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayCatalog'.
- The solution must be implemented with a menu-driven approach.
- The menu must include the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit the program
- The program must exit when the user chooses the 'Exit the program' option (option 5).

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
1
Enter book title: Introduction to Computer Science
Enter book author: John Smith
Enter book publication year: 2020
Choose an option:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit the program
3
```
Example Output:
```
Book Title: Introduction to Computer Science
Book Author: John Smith
Book Publication Year: 2020
```
Note: The program should continue to run and prompt the user for input until the user chooses to exit.

---

## Problem 70 - llama-3.3-70b-versatile - Iteration 45
# STEP 1: PROBLEM
You are the curator of a local library, and you want to create a simple system to manage the books in your collection. The system should allow you to add, remove, and display books. Since the library is small, a singly linked list is sufficient for storing the book information.

The library has various types of books, including fiction, non-fiction, and biographies. Each book has a unique title, author, publication year, and genre.

### REQUIREMENTS
The program must have the following functionality:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all the books in the collection.
4. Display the details of a specific book by its title.

### EXAMPLE
Example Input:
```
Add a book with the following details:
Title: "To Kill a Mockingbird"
Author: "Harper Lee"
Publication Year: 1960
Genre: "Fiction"

Add another book with the following details:
Title: "The Great Gatsby"
Author: "F. Scott Fitzgerald"
Publication Year: 1925
Genre: "Fiction"

Remove the book with the title: "To Kill a Mockingbird"

Display all the books in the collection:
```
Example Output:
```
Book Title: The Great Gatsby
Author: F. Scott Fitzgerald
Publication Year: 1925
Genre: Fiction
```
### CONSTRAINTS
* Must use a 'struct' to represent a book.
* Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
* The solution must be implemented with a menu-driven approach.
* The menu options are as follows:
	1. Add a book
	2. Remove a book
	3. Display all books
	4. Display a specific book
	5. EXIT the program
* The program must exit when the user chooses the 'EXIT' option (option 5).

---

## Problem 71 - llama-3.3-70b-versatile - Iteration 46
# STEP 1: PROBLEM
In a library management system, books are organized and tracked using a singly linked list. Each book has a unique title, author, and publication year. The librarian needs a program to efficiently manage the collection of books.

## BACKGROUND
The library management system requires a program that can store and retrieve information about books. The program should allow the librarian to add new books, remove existing books, and display details of specific books or the entire collection.

## REQUIREMENTS
The program must have the following functionalities:
1. **Add Book**: Add a new book to the collection with its title, author, and publication year.
2. **Remove Book**: Remove a book from the collection by its title.
3. **Display Book**: Display the details of a specific book by its title.
4. **Display All Books**: Display the details of all books in the collection.
5. **Search Book**: Search for books by author or publication year.

## EXAMPLE
Input:
```
Add Book: "Introduction to CS" by "John Doe" (2020)
Add Book: "Data Structures" by "Jane Smith" (2019)
Display Book: "Introduction to CS"
```
Output:
```
Book Title: Introduction to CS
Author: John Doe
Publication Year: 2020
```

### CONSTRAINTS
1. Must use a `struct` to represent a book.
2. Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
3. The program must implement a menu-driven interface with the following options:
   - Option 1: Add Book
   - Option 2: Remove Book
   - Option 3: Display Book
   - Option 4: Display All Books
   - Option 5: Search Book
   - Option 6: EXIT
4. The solution must be implemented using a singly linked list to store the collection of books.
5. The program must handle cases where a book is not found in the collection.

Note: The program should be implemented in C or C++ programming language, and the `struct` should be used to represent a book with its title, author, and publication year. The `displayBook` function should take the title of the book as input and display its details. The menu-driven interface should be implemented using a loop that continues until the user chooses to EXIT (Option 6).

---

## Problem 72 - llama-3.3-70b-versatile - Iteration 47
# STEP 1: PROBLEM
Imagine you are a librarian tasked with managing a collection of books in a library. You want to create a simple system to keep track of the books, allowing you to add, remove, and display book information. To implement this system, you will use a singly linked list data structure.

Background:
The library has a vast collection of books, and you need to manage the inventory efficiently. Each book has a unique title, author, publication year, and a unique identifier (ID). The system should allow you to perform basic operations such as adding a new book, removing a book, and displaying the details of all books or a specific book.

Requirements:
1. Create a singly linked list to store book information.
2. Implement functions to add a new book to the list.
3. Implement a function to remove a book by its ID.
4. Implement a function to display the details of all books in the list.
5. Implement a function to display the details of a specific book by its ID.

Example:
Input:
- Add book: "Book1" by "Author1" (2020) with ID 1
- Add book: "Book2" by "Author2" (2019) with ID 2
- Display all books
- Remove book with ID 1
- Display all books

Output:
- After adding books: 
  Book1 by Author1 (2020) - ID: 1
  Book2 by Author2 (2019) - ID: 2
- After removing book with ID 1:
  Book2 by Author2 (2019) - ID: 2

### CONSTRAINTS
- Must use a 'struct' to represent the Book entity with fields for title, author, publication year, and ID.
- The solution must be implemented with a menu-driven approach.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The menu must include the following options:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Display a specific book by ID
  5. EXIT the program
- The program must exit when the user chooses option 5 (EXIT).

---

## Problem 73 - llama-3.3-70b-versatile - Iteration 48
# STEP 1: PROBLEM
In a small library, books are organized using a singly linked list data structure. Each book has a unique title, author, and publication year. The librarian wants to manage the collection of books efficiently, so they need a program to add, remove, and display books in the library.

The program should have the following functionality:
1. Add a new book to the library.
2. Remove a book from the library by its title.
3. Display all books in the library.
4. Display the details of a specific book by its title.

### EXAMPLE
Input:
```
Add: Book1, Author1, 2020
Add: Book2, Author2, 2019
Display All
Display Book1
Remove: Book1
Display All
```
Output:
```
Book1, Author1, 2020
Book2, Author2, 2019
Book1, Author1, 2020
Book2, Author2, 2019
```

### CONSTRAINTS
* Must use a `struct` to represent a book.
* Logic for displaying the details of one specific book must be in a function called `displayBook`.
* The solution must be implemented using a menu-driven approach.
* Must include a menu option to EXIT the program. The program will exit when the user chooses option 5.

### MENU OPTIONS
1. Add a new book to the library.
2. Remove a book from the library.
3. Display all books in the library.
4. Display the details of a specific book.
5. EXIT the program.

The program should be able to handle a large number of books and perform operations efficiently. The librarian should be able to easily manage the collection of books using the menu-driven interface.

---

## Problem 74 - llama-3.3-70b-versatile - Iteration 49
# STEP 1: PROBLEM
In a simple library management system, books are stored in a catalog. To efficiently manage the catalog, the library wants to implement a system that utilizes a singly linked list to store and retrieve book information. The system should allow users to add, remove, and display books in the catalog.

The library has the following requirements for the system:
1. The system should store the title, author, and publication year of each book.
2. The system should allow users to add a new book to the catalog.
3. The system should allow users to remove a book from the catalog by its title.
4. The system should display all the books in the catalog.
5. The system should display the details of a specific book by its title.

Here's a simple example of the expected input/output:
- Add a book: "Introduction to Computer Science" by "John Smith" published in 2020.
- Add a book: "Data Structures" by "Jane Doe" published in 2019.
- Display all books:
  - Introduction to Computer Science by John Smith (2020)
  - Data Structures by Jane Doe (2019)
- Remove a book: "Introduction to Computer Science"
- Display all books:
  - Data Structures by Jane Doe (2019)
- Display book details: "Data Structures"
  - Title: Data Structures
  - Author: Jane Doe
  - Publication Year: 2019

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display book details
  5. EXIT (to exit the program)
- If a user tries to remove or display a book that does not exist, the system should display an error message.

---

## Problem 75 - llama-3.3-70b-versatile - Iteration 50
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a singly linked list data structure. Each book has a unique ID, title, author, and publication year. The librarian wants to perform basic operations like inserting a new book, deleting a book, and displaying all the books in the list.

The program should provide a menu to the user to interact with the singly linked list. The menu options should include:

1. Insert a new book
2. Delete a book by ID
3. Display all books
4. EXIT the program

The librarian should be able to insert new books, delete existing books, and display all the books in the list.

### EXAMPLE
If the user inserts three books with the following details:
- Book 1: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
- Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021
- Book 3: ID = 3, Title = "Book3", Author = "Author3", Year = 2022

The display all books option should output:
```
Book ID: 1, Title: Book1, Author: Author1, Year: 2020
Book ID: 2, Title: Book2, Author: Author2, Year: 2021
Book ID: 3, Title: Book3, Author: Author3, Year: 2022
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayBooks`.
- Must use a singly linked list to store the books.
- The solution must be implemented with a single function besides `main()` to handle the menu options.
- The program should have a menu option to EXIT the program. The EXIT option should be option 4.
- If a user tries to delete a book that does not exist, the program should print an error message "Book not found". 

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks.

---

## Problem 76 - llama-3.3-70b-versatile - Iteration 51
# STEP 1: PROBLEM
You are the curator of a museum, and you want to create a program to manage the artifacts in your collection. The museum has a vast array of artifacts, each with its own unique characteristics, such as name, description, and date of origin. You want to store these artifacts in a singly linked list and provide a simple menu-driven interface to add, remove, and display artifacts.

The program should have the following functionality:
1. Add an artifact to the collection: The program should prompt the user to enter the name, description, and date of origin of the artifact.
2. Remove an artifact from the collection: The program should prompt the user to enter the name of the artifact to be removed.
3. Display all artifacts in the collection: The program should display the name, description, and date of origin of each artifact in the collection.
4. Display the details of a specific artifact: The program should prompt the user to enter the name of the artifact and then display its details.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (i.e., the artifact).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu options.
- If a menu is implemented, it must include the following options:
  - Option 1: Add an artifact to the collection
  - Option 2: Remove an artifact from the collection
  - Option 3: Display all artifacts in the collection
  - Option 4: Display the details of a specific artifact
  - Option 5: EXIT the program

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Enter your choice:
1. Add an artifact
2. Remove an artifact
3. Display all artifacts
4. Display a specific artifact
5. EXIT
1
Enter name: Ancient Vase
Enter description: A beautiful ancient vase
Enter date of origin: 1000 BC
```
Example Output:
```
Artifact added successfully!
```
Then, if the user chooses to display all artifacts:
```
1. Add an artifact
2. Remove an artifact
3. Display all artifacts
4. Display a specific artifact
5. EXIT
3
```
Example Output:
```
Name: Ancient Vase
Description: A beautiful ancient vase
Date of origin: 1000 BC
```

---

## Problem 77 - llama-3.3-70b-versatile - Iteration 52
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a singly linked list data structure. The librarian needs to perform various operations such as adding a book, removing a book, displaying all books, and searching for a specific book. The librarian also wants to keep track of the total number of books in the library.

The background story is that the library has a limited number of shelves, and the librarian wants to automate the process of managing the books to make it more efficient. The librarian has asked you to design a program that can help with this task.

The program's functionality should include the following requirements:
1. Add a book to the library: The program should allow the user to add a new book to the library by providing the book's title, author, and publication year.
2. Remove a book from the library: The program should allow the user to remove a book from the library by providing the book's title.
3. Display all books in the library: The program should display all the books in the library, including their title, author, and publication year.
4. Search for a specific book: The program should allow the user to search for a book by providing the book's title.
5. Display the total number of books in the library: The program should display the total number of books in the library.

Here's a simple example of expected input/output:
```
Add a book:
Title: "Introduction to Computer Science"
Author: "John Smith"
Publication Year: 2020

Display all books:
1. "Introduction to Computer Science" by John Smith (2020)

Remove a book:
Title: "Introduction to Computer Science"

Display all books:
No books in the library.

Search for a book:
Title: "Introduction to Computer Science"
Book not found.

Add a book:
Title: "Data Structures and Algorithms"
Author: "Jane Doe"
Publication Year: 2019

Display all books:
1. "Data Structures and Algorithms" by Jane Doe (2019)

Total number of books: 1
```

### CONSTRAINTS
1. Must use a `struct` to represent a book, which should include the title, author, and publication year.
2. Logic for displaying the details of all books must be in a function called `displayBooks`.
3. The solution must be implemented with a single linked list.
4. The program must include a menu with the following options:
   - 1: Add a book
   - 2: Remove a book
   - 3: Display all books
   - 4: Search for a book
   - 5: Display total number of books
   - 6: EXIT the program (by selecting option 6, the program should terminate)

Note: The menu option to EXIT the program is option 6.

---

## Problem 78 - llama-3.3-70b-versatile - Iteration 53
# STEP 1: PROBLEM
You are the curator of a museum, and you want to create a system to manage the artifacts in your collection. The museum has a wide variety of artifacts, each with its own unique characteristics. To efficiently manage these artifacts, you decide to implement a singly linked list data structure. The linked list will store nodes, each representing an artifact with its name, description, and acquisition year.

The program should allow users to interact with the museum's collection by performing the following operations:
1. Insert a new artifact at the end of the list.
2. Delete an artifact by its name.
3. Display all artifacts in the collection.
4. Search for an artifact by its name and display its details.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Artifact).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle user input and menu operations, named 'menuOperations'.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which will be option 5.

### EXAMPLE
Input:
```
1. Insert a new artifact: 
Name: Ancient Vase
Description: A vase from ancient Greece
Acquisition Year: 2000
2. Insert a new artifact: 
Name: Painting
Description: A painting from the Renaissance
Acquisition Year: 2010
3. Display all artifacts
4. Search for an artifact: Ancient Vase
5. Exit
```
Output:
```
All Artifacts:
- Ancient Vase, A vase from ancient Greece, 2000
- Painting, A painting from the Renaissance, 2010
Artifact Details:
- Name: Ancient Vase
- Description: A vase from ancient Greece
- Acquisition Year: 2000
```
Note: The actual implementation of the menu and input/output operations is left to the student's discretion, as long as the requirements and constraints are met.

---

## Problem 79 - llama-3.3-70b-versatile - Iteration 54
# STEP 1: PROBLEM
You are a curator at a museum, and you want to create a system to manage the artifacts in the museum's collection. The collection includes various items such as paintings, sculptures, and historical objects. You want to use a singly linked list to store the information about these artifacts.

The museum has a large collection, and you want to be able to efficiently add, remove, and display information about the artifacts. You also want to be able to search for specific artifacts by their name or ID.

Here is the background story and context for the problem:

The museum's collection is currently stored in a large database, but the database is becoming outdated and difficult to manage. You want to create a new system that uses a singly linked list to store the information about the artifacts. The system should be able to perform the following operations:

* Add a new artifact to the collection
* Remove an artifact from the collection
* Display all the artifacts in the collection
* Search for a specific artifact by name or ID
* Display the details of a specific artifact

The requirements for the program's functionality are:

1. The program should use a singly linked list to store the information about the artifacts.
2. The program should have a menu that allows the user to add, remove, display, search, and exit the program.
3. The program should have a function to display the details of a specific artifact.
4. The program should be able to handle a large number of artifacts.

Here is a simple example of expected input/output:

```
Menu:
1. Add artifact
2. Remove artifact
3. Display all artifacts
4. Search for artifact
5. Display artifact details
6. Exit

Enter your choice: 1

Enter artifact name: Painting 1
Enter artifact ID: 1
Enter artifact description: This is a painting

Menu:
1. Add artifact
2. Remove artifact
3. Display all artifacts
4. Search for artifact
5. Display artifact details
6. Exit

Enter your choice: 3

Artifact 1: Painting 1, ID: 1, Description: This is a painting

Menu:
1. Add artifact
2. Remove artifact
3. Display all artifacts
4. Search for artifact
5. Display artifact details
6. Exit

Enter your choice: 5

Enter artifact ID: 1

Artifact name: Painting 1
Artifact ID: 1
Artifact description: This is a painting
```

### CONSTRAINTS
* Must use a `struct` to represent the primary data entity (the artifact).
* Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
* The solution must be implemented with a single linked list.
* The menu option to EXIT the program is option 6.
* The program must handle invalid user input and provide clear error messages.
* The program must be able to handle a large number of artifacts (at least 100).

---

## Problem 80 - llama-3.3-70b-versatile - Iteration 55
# STEP 1: PROBLEM
In a small university, the registrar's office is responsible for maintaining the records of all students. To efficiently manage these records, the registrar's office wants to implement a system that utilizes a singly linked list to store and retrieve student information. Each student record contains the student's ID, name, and GPA.

The registrar's office needs a program that can perform the following operations:
1. Insert a new student record at the end of the list.
2. Delete a student record by ID.
3. Display all student records.
4. Search for a student record by ID and display the details.
5. Calculate and display the average GPA of all students.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all the operations.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 6.

### EXAMPLE
Example Input:
```
1. Insert a new student record: ID = 1, Name = John, GPA = 3.5
2. Insert a new student record: ID = 2, Name = Alice, GPA = 3.8
3. Display all student records.
```
Example Output:
```
Student ID: 1, Name: John, GPA: 3.5
Student ID: 2, Name: Alice, GPA: 3.8
```
To run the program, the user will be presented with a menu:
```
1. Insert a new student record
2. Delete a student record by ID
3. Display all student records
4. Search for a student record by ID
5. Calculate and display the average GPA of all students
6. EXIT
```
The user can choose an option by entering the corresponding number. The program will continue to run until the user chooses option 6 to EXIT.

---

## Problem 81 - llama-3.3-70b-versatile - Iteration 56
# STEP 1: PROBLEM
As the curator of a local library, you want to create a system to manage the borrowing and returning of books. The system should allow users to add, remove, and display books in the library. Since the number of books can be large, you decide to use a Singly Linked List data structure to efficiently store and retrieve the book information.

The library has the following requirements for the system:
1. The system should be able to add a new book to the library.
2. The system should be able to remove a book from the library by its title.
3. The system should be able to display all the books in the library.
4. The system should be able to search for a book by its title and display its details.

Here is a simple example of the expected input/output:
```
Add a book: 
Title: "Introduction to CS"
Author: "John Doe"
Year: 2020

Display all books:
1. "Introduction to CS" by John Doe (2020)

Remove a book: 
Title: "Introduction to CS"

Display all books:
No books in the library.
```

### CONSTRAINTS
* Must use a 'struct' to represent a book with attributes: title, author, and year.
* Logic for displaying the details of all books must be in a function called 'displayBooks'.
* The solution must be implemented with a menu-driven approach.
* The menu should have the following options:
	1. Add a book
	2. Remove a book
	3. Display all books
	4. Search for a book
	5. EXIT (to exit the program)
* The menu option to EXIT the program is option 5. 

Note: The system should handle cases where a book is not found in the library, and it should not allow duplicate books to be added. The system should also handle cases where the user tries to remove a book that does not exist in the library.

---

## Problem 82 - llama-3.3-70b-versatile - Iteration 57
# STEP 1: PROBLEM
In a university setting, it's common for students to enroll in various courses throughout their academic journey. To manage student course enrollment efficiently, the university wants to implement a system that utilizes a singly linked list to store and manipulate student enrollment data. Each student's enrollment information includes their unique student ID, name, and the course they are enrolled in.

The system should allow users to perform the following operations:
1. Add a new student enrollment to the list.
2. Remove a student enrollment from the list based on their student ID.
3. Display all student enrollments in the list.
4. Search for a specific student enrollment by student ID and display their details.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent each student's enrollment information, which includes student ID, name, and course.
- Logic for displaying the details of all student enrollments must be in a function called 'displayEnrollments'.
- The solution must be implemented with a menu-driven approach, where each option corresponds to one of the required operations.
- The menu must include a specific option to EXIT the program, which is option 5.
- If a menu is implemented, the program must continue to run and display the menu until the user chooses to exit.

### EXAMPLE
Example Input/Output:
```
Menu:
1. Add Enrollment
2. Remove Enrollment
3. Display Enrollments
4. Search Enrollment
5. Exit

Choose an option: 1
Enter Student ID: S001
Enter Student Name: John Doe
Enter Course: CS101

Choose an option: 3
Student ID: S001, Name: John Doe, Course: CS101

Choose an option: 5
Exiting program...
```
In this example, the user adds a new enrollment, displays all enrollments, and then exits the program. The system should handle various operations and provide the expected output based on the user's input.

---

## Problem 83 - llama-3.3-70b-versatile - Iteration 58
# STEP 1: PROBLEM
In a simple library management system, books are stored in a catalog. The catalog is implemented as a singly linked list where each node represents a book with its title, author, and publication year. The system should allow users to add books to the catalog, remove books, and display the details of all books or a specific book.

**Background Story:**
A small local library wants to implement a basic management system to keep track of its books. The librarian needs a program that can store book information, add new books, remove existing ones, and display book details.

**Requirements:**
1. The program should create a singly linked list to store book information.
2. The program should have options to add a new book, remove a book, and display all books or a specific book.
3. Each book should have a title, author, and publication year.
4. The program should display a menu for the user to interact with the catalog.

**Example Input/Output:**
- When adding a book: 
    - Input: Title = "Introduction to CS", Author = "John Doe", Year = 2020
    - Output: Book added successfully.
- When displaying all books:
    - Output: A list of all books with their title, author, and publication year.
- When removing a book:
    - Input: Title of the book to remove = "Introduction to CS"
    - Output: Book removed successfully or Book not found.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must be implemented with a main function and additional functions for each operation (e.g., addBook, removeBook).
- Must include a menu with the following options:
    1. Add a book
    2. Remove a book
    3. Display all books
    4. Display a specific book
    5. EXIT the program
- The program must exit when the user chooses the EXIT option (option 5).

---

## Problem 84 - llama-3.3-70b-versatile - Iteration 59
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a simple system. The system should allow the librarian to add, remove, and display books. Each book has a unique title, author, and publication year. The librarian wants to store the books in a singly linked list, where each node represents a book.

The librarian provides the following requirements for the program's functionality:
1. The program should allow the librarian to add a new book to the list.
2. The program should allow the librarian to remove a book from the list by its title.
3. The program should display all the books in the list.
4. The program should display the details of a specific book by its title.

Here is a simple example of expected input/output:
```
Add a book: Title - "Introduction to CS", Author - "John Doe", Year - 2020
Add a book: Title - "Data Structures", Author - "Jane Smith", Year - 2019
Display all books:
  Introduction to CS by John Doe (2020)
  Data Structures by Jane Smith (2019)
Display book by title: "Introduction to CS"
  Title: Introduction to CS
  Author: John Doe
  Year: 2020
Remove book by title: "Data Structures"
Display all books:
  Introduction to CS by John Doe (2020)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book, with members for title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a book
  2. Remove a book by title
  3. Display all books
  4. Display a book by title
  5. EXIT the program
- To exit the program, the librarian should select option 5 or type 'EXIT'. 

Note: The program should handle invalid inputs and exceptions, such as attempting to remove a non-existent book or displaying a book that does not exist in the list.

---

## Problem 85 - llama-3.3-70b-versatile - Iteration 60
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books borrowed by the students. The librarian needs a simple system to add, remove, and display the details of the borrowed books. The system should use a Singly Linked List to store the book details. 

The background story is that the librarian has a manual system of maintaining a register for borrowed books, but it is becoming cumbersome and prone to errors. The librarian wants a computerized system that can efficiently manage the borrowed books.

The requirements for the program's functionality are:
1. Add a new book to the list with details such as book ID, book name, student ID, and student name.
2. Remove a book from the list by book ID.
3. Display all the books in the list.
4. Display the details of a specific book by book ID.
5. The program should have a menu-driven interface to perform the above operations.

An example of expected input/output is:
- When adding a new book: 
    - Input: Book ID: 1, Book Name: "Introduction to CS", Student ID: 101, Student Name: "John Doe"
    - Output: Book added successfully.
- When removing a book:
    - Input: Book ID: 1
    - Output: Book removed successfully.
- When displaying all books:
    - Output: A list of all books with their details.
- When displaying a specific book:
    - Input: Book ID: 1
    - Output: Details of the book with ID 1.

### CONSTRAINTS
- Must use a 'struct' to represent the book details.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu operations.
- If a menu is implemented, it must include the following options:
    1. Add a new book
    2. Remove a book
    3. Display all books
    4. Display a specific book
    5. EXIT the program (option 5)
- The menu option to EXIT the program is option 5. When this option is chosen, the program should terminate. 

Example menu:
```
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
```

---

## Problem 86 - llama-3.3-70b-versatile - Iteration 1
# STEP 1: PROBLEM
You are the curator of a library that uses a singly linked list to keep track of books. Each book has a title, author, and publication year. The linked list is used to manage the books in the order they were added to the library. Your task is to design a program that allows the librarian to add, remove, and display books in the library.

The program should have the following functionality:
1. Add a new book to the end of the linked list.
2. Remove a book by its title.
3. Display all books in the library.
4. Display the details of a specific book.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The program must have the following menu options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (this option should exit the program)

### EXAMPLE
If the library has the following books:
- Book 1: Title = "To Kill a Mockingbird", Author = "Harper Lee", Year = 1960
- Book 2: Title = "1984", Author = "George Orwell", Year = 1949
- Book 3: Title = "Pride and Prejudice", Author = "Jane Austen", Year = 1813

The program should be able to display all books, add a new book, remove a book by its title, and display the details of a specific book.

Example Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Choose an option: 3
To Kill a Mockingbird by Harper Lee (1960)
1984 by George Orwell (1949)
Pride and Prejudice by Jane Austen (1813)

Choose an option: 1
Enter book title: The Great Gatsby
Enter book author: F. Scott Fitzgerald
Enter book year: 1925

Choose an option: 3
To Kill a Mockingbird by Harper Lee (1960)
1984 by George Orwell (1949)
Pride and Prejudice by Jane Austen (1813)
The Great Gatsby by F. Scott Fitzgerald (1925)

Choose an option: 5
Exiting the program...
```

---

## Problem 87 - llama-3.3-70b-versatile - Iteration 2
# STEP 1: PROBLEM
In a university setting, it's common for students to borrow books from the library. To manage the borrowing process efficiently, the library wants to implement a system that keeps track of borrowed books using a Singly Linked List. The system should allow students to borrow books, return books, and display the list of borrowed books.

The library has a collection of books, each identified by a unique title and author. When a student borrows a book, the system should add the book to the list of borrowed books. If a student returns a book, the system should remove the book from the list. The system should also be able to display the list of borrowed books.

### REQUIREMENTS
1. Implement a Singly Linked List to store the borrowed books.
2. The system should have the following functionalities:
   - Borrow a book: Add a book to the list of borrowed books.
   - Return a book: Remove a book from the list of borrowed books.
   - Display borrowed books: Display the list of borrowed books.
3. Each book should have a title and an author.

### EXAMPLE
Input:
- Borrow "Introduction to Algorithms" by "Thomas H. Cormen"
- Borrow "Data Structures and Algorithms" by "Robert Sedgewick"
- Return "Introduction to Algorithms" by "Thomas H. Cormen"
- Display borrowed books

Output:
- "Data Structures and Algorithms" by "Robert Sedgewick"

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all borrowed books must be in a function called 'displayBorrowedBooks'.
- The solution must be implemented with a menu-driven approach.
- The menu options should include:
  1. Borrow a book
  2. Return a book
  3. Display borrowed books
  4. EXIT (to exit the program)

Note: The program should continue to run until the user chooses the EXIT option. If a user tries to return a book that is not borrowed, the program should display an error message. If a user tries to borrow a book that is already borrowed, the program should display an error message.

---

## Problem 88 - llama-3.3-70b-versatile - Iteration 3
# STEP 1: PROBLEM
In a university library, books are organized and tracked using a catalog system. The catalog system currently uses a simple text-based interface to manage its collection. As part of a library automation project, you have been tasked with designing a program that utilizes a singly linked list to store and manage book information. Each book in the catalog has a unique identifier (ID), title, author, and publication year.

The program should allow users to perform the following operations:
1. Add a new book to the catalog.
2. Remove a book by its ID from the catalog.
3. Display all books in the catalog.
4. Search for a book by its title or author.
5. Display the details of a specific book given its ID.

### CONSTRAINTS
- Must use a 'struct' to represent a book, containing fields for ID, title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must include a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Display book details
  6. EXIT (to exit the program)
- The program must handle invalid inputs and exceptions gracefully.

### EXAMPLE
Example Input:
- Add a new book with ID = 1, title = "Introduction to CS", author = "John Doe", publication year = 2020.
- Add another book with ID = 2, title = "Data Structures", author = "Jane Smith", publication year = 2022.
- Display all books.
- Search for books by author "John Doe".
- Display the details of the book with ID = 1.

Example Output:
- After adding the books, the catalog will contain:
  - Book 1: Introduction to CS by John Doe (2020)
  - Book 2: Data Structures by Jane Smith (2022)
- Displaying all books will list both books.
- Searching for books by "John Doe" will display "Introduction to CS".
- Displaying the details of the book with ID = 1 will show "Introduction to CS by John Doe (2020)".

By following these requirements and constraints, you will create a functional program for managing a library's book catalog using a singly linked list.

---

## Problem 89 - llama-3.3-70b-versatile - Iteration 4
# STEP 1: PROBLEM
You are the administrator of a university library, and you want to create a simple system to manage the borrowing and returning of books. The system should store information about each book, including its title, author, and borrower (if any). The system should also allow you to add, remove, and search for books.

The system will use a singly linked list to store the book information. Each node in the list will represent a book, and it will contain the title, author, and borrower of the book.

## REQUIREMENTS:
1. The system should be able to add a new book to the list.
2. The system should be able to remove a book from the list.
3. The system should be able to search for a book by title or author.
4. The system should be able to display all the books in the list.
5. The system should be able to display the details of a specific book.

## EXAMPLE:
If we have a list of books with the following information:
- Book 1: Title - "Introduction to CS", Author - "John Smith", Borrower - "None"
- Book 2: Title - "Data Structures", Author - "Jane Doe", Borrower - "John Doe"

The system should be able to add a new book, remove a book, search for a book, display all the books, and display the details of a specific book.

### CONSTRAINTS:
- Must use a 'struct' to represent the book entity.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book
  3. Search for a book
  4. Display all books
  5. Display a specific book
  6. EXIT the program
- The program should exit when the user selects the 'EXIT' option (option 6).

Example Input/Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Display a specific book
6. EXIT

Enter your choice: 1
Enter book title: Introduction to CS
Enter book author: John Smith
Enter book borrower: None

Menu:
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. Display a specific book
6. EXIT

Enter your choice: 4
Book 1: Title - "Introduction to CS", Author - "John Smith", Borrower - "None"
```

---

## Problem 90 - llama-3.3-70b-versatile - Iteration 5
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the borrowing and returning of books using a simple system. The system should allow the librarian to add a book to the collection, remove a book from the collection, display all the books in the collection, and search for a specific book by its title. The librarian wants to store the book's title, author, and status (available or borrowed).

The system will use a Singly Linked List to store the book collection. Each node in the list will represent a book, and the node will contain the book's title, author, and status.

## REQUIREMENTS
1. The system must allow the librarian to add a book to the collection.
2. The system must allow the librarian to remove a book from the collection.
3. The system must allow the librarian to display all the books in the collection.
4. The system must allow the librarian to search for a specific book by its title.
5. The system must update the status of a book when it is borrowed or returned.

## EXAMPLE
Input:
```
Add book: "Harry Potter" by "J.K. Rowling"
Add book: "The Lord of the Rings" by "J.R.R. Tolkien"
Display all books:
  Harry Potter by J.K. Rowling (available)
  The Lord of the Rings by J.R.R. Tolkien (available)
Borrow book: "Harry Potter"
Display all books:
  Harry Potter by J.K. Rowling (borrowed)
  The Lord of the Rings by J.R.R. Tolkien (available)
Return book: "Harry Potter"
Display all books:
  Harry Potter by J.K. Rowling (available)
  The Lord of the Rings by J.R.R. Tolkien (available)
```
### CONSTRAINTS
* Must use a `struct` to represent a book.
* Must implement a Singly Linked List to store the book collection.
* The solution must include a menu with the following options:
  1. Add a book to the collection
  2. Remove a book from the collection
  3. Display all books in the collection
  4. Search for a specific book by its title
  5. Borrow a book
  6. Return a book
  7. EXIT the program (option 8)
* Logic for displaying the details of all books must be in a function called `displayAllBooks`.
* Logic for displaying the details of a specific book must be in a function called `displayBook`.
* The program must use a single loop to handle the menu options.

---

## Problem 91 - llama-3.3-70b-versatile - Iteration 6
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a singly linked list data structure. The librarian needs a program that can add, remove, and display books in the library. Each book has a unique title, author, and publication year.

The program should have the following functionality:
1. Add a new book to the library: The program should prompt the user to enter the title, author, and publication year of the book.
2. Remove a book from the library: The program should prompt the user to enter the title of the book to be removed.
3. Display all books in the library: The program should display the title, author, and publication year of all books in the library.
4. Display a specific book: The program should prompt the user to enter the title of the book and then display the details of that book.

Here's a simple example of the expected input/output:
```
Library Management System
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter publication year: 2020
Book added successfully!

Library Management System
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 3
Book1 by Author1 (2020)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single linked list data structure.
- The program should have a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- The program should exit when the user selects option 5 (EXIT).

---

## Problem 92 - llama-3.3-70b-versatile - Iteration 7
# STEP 1: PROBLEM
In a small library, books are managed using a simple catalog system. The catalog is implemented as a singly linked list, where each node represents a book with its title, author, and publication year. The library staff needs a program to manage this catalog efficiently. Your task is to design and implement this program.

### BACKGROUND
The library staff wants to be able to add new books to the catalog, remove existing books, display all books in the catalog, and search for a specific book by its title or author.

### REQUIREMENTS
1. The program must allow the user to add a new book to the catalog.
2. The program must allow the user to remove a book from the catalog by its title.
3. The program must display all books in the catalog.
4. The program must allow the user to search for a book by its title or author.
5. The program must have a menu-driven interface for the user to interact with the catalog.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a new book:
Title: Introduction to Algorithms
Author: Thomas H. Cormen
Year: 2009

Remove a book:
Title: Introduction to Algorithms

Display all books:
Introduction to Algorithms by Thomas H. Cormen (2009)
Data Structures and Algorithms by Robert Sedgewick (2011)

Search for a book by title:
Title: Data Structures and Algorithms
Result: Data Structures and Algorithms by Robert Sedgewick (2011)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayCatalog'.
- The solution must be implemented with a single linked list to store the books.
- The program must have a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. EXIT the program
- The user can exit the program by selecting the 'EXIT' option (option 5).

---

## Problem 93 - llama-3.3-70b-versatile - Iteration 8
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. To efficiently store and manage these records, we can utilize a singly linked list data structure. The goal of this assignment is to design a program that implements a singly linked list to store student records, allowing users to perform various operations such as adding, deleting, and displaying student records.

The program should simulate a simple student record management system. Each student record should contain the student's ID, name, and GPA. The program should provide a menu-driven interface for users to interact with the system.

### REQUIREMENTS
1. The program should allow users to add new student records to the linked list.
2. The program should allow users to delete a student record by ID from the linked list.
3. The program should allow users to display all student records in the linked list.
4. The program should allow users to search for a student record by ID and display the corresponding record.
5. The program should handle cases where the linked list is empty or a student record is not found.

### EXAMPLE
Input: 
```
1. Add student record
Enter student ID: 1234
Enter student name: John Doe
Enter student GPA: 3.8

2. Add student record
Enter student ID: 5678
Enter student name: Jane Doe
Enter student GPA: 3.9

3. Display all records
```
Output:
```
Student ID: 1234, Name: John Doe, GPA: 3.8
Student ID: 5678, Name: Jane Doe, GPA: 3.9
```

### CONSTRAINTS
1. Must use a `struct` to represent the student record.
2. Logic for displaying the details of all student records must be in a function called `displayRecords`.
3. The solution must be implemented with a single linked list data structure.
4. The program must include a menu option to EXIT the program. The EXIT option should be numbered as 6.

### MENU OPTIONS
1. Add student record
2. Delete student record
3. Display all records
4. Search for a student record
5. Clear all records
6. EXIT the program

Note: The program should handle invalid inputs and provide user-friendly error messages. The menu options should be clearly displayed, and the program should continue to run until the user chooses to EXIT.

---

## Problem 94 - llama-3.3-70b-versatile - Iteration 9
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a singly linked list to keep track of the books, where each book is represented by a node containing the book's title, author, and publication year. Your task is to design a program that allows the librarian to manage the collection of books by inserting new books, deleting existing books, and displaying the details of all books or a specific book.

### BACKGROUND
The library has a large collection of books, and the librarian needs a program to efficiently manage the collection. The program should allow the librarian to insert new books, delete existing books, and display the details of all books or a specific book.

### REQUIREMENTS
1. The program should have the following functionalities:
   - Insert a new book at the beginning of the list.
   - Insert a new book at the end of the list.
   - Delete a book by its title.
   - Display the details of all books.
   - Display the details of a specific book by its title.
2. The program should use a singly linked list to store the books.
3. The program should have a menu-driven interface to allow the librarian to choose the desired operation.

### EXAMPLE
Input:
```
1. Insert book at beginning
Title: Book1
Author: Author1
Year: 2020
2. Insert book at end
Title: Book2
Author: Author2
Year: 2021
3. Display all books
```
Output:
```
Book1 by Author1 (2020)
Book2 by Author2 (2021)
```
### CONSTRAINTS
1. Must use a 'struct' to represent a book.
2. Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
3. Logic for displaying the details of a specific book must be in a function called 'displayBook'.
4. The program must have a menu-driven interface with the following options:
   - 1. Insert book at beginning
   - 2. Insert book at end
   - 3. Delete book by title
   - 4. Display all books
   - 5. Display book by title
   - 6. EXIT (to exit the program)

Note: The program should handle invalid inputs and edge cases, such as inserting a book with an empty title or author, or deleting a book that does not exist.

---

## Problem 95 - llama-3.3-70b-versatile - Iteration 10
# STEP 1: PROBLEM
In a small library, books are organized using a singly linked list. Each book has a unique title, author, and publication year. The librarian wants to create a simple program to manage the book collection. The program should allow the librarian to add new books, remove existing books, display all books, and search for a specific book by title.

The program will be used by the librarian to keep track of the books in the library. The librarian will interact with the program through a menu-driven interface.

## Requirements:
1. Implement a singly linked list to store the books.
2. The program should have the following menu options:
   - Add a new book to the collection
   - Remove a book from the collection by title
   - Display all books in the collection
   - Search for a book by title
   - Exit the program
3. Each book should have a title, author, and publication year.
4. The program should handle cases where a book is not found in the collection.

## Example:
If the librarian adds the following books:
- Title: "To Kill a Mockingbird", Author: "Harper Lee", Year: 1960
- Title: "1984", Author: "George Orwell", Year: 1949
- Title: "Pride and Prejudice", Author: "Jane Austen", Year: 1813

The output for the "Display all books" option should be:
```
To Kill a Mockingbird by Harper Lee (1960)
1984 by George Orwell (1949)
Pride and Prejudice by Jane Austen (1813)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented with a single linked list.
- The program must have a menu option to EXIT the program, which will be option 5.
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. EXIT the program (by selecting option 5)

---

## Problem 96 - llama-3.3-70b-versatile - Iteration 11
# STEP 1: PROBLEM
In a library management system, books are organized using a singly linked list. Each book has a unique identifier (ID), title, author, and publication year. The system should allow users to add, remove, and display books.

Background:
The library wants to implement a simple system to manage its collection of books. The system should be able to store information about each book and provide basic operations to manipulate the data.

Requirements:
1. The program should create a singly linked list to store book information.
2. The program should allow users to add a new book to the list.
3. The program should allow users to remove a book from the list by its ID.
4. The program should display all books in the list.
5. The program should display the details of a specific book by its ID.

Example:
Input:
- Add book with ID 1, title "Book1", author "Author1", publication year 2020
- Add book with ID 2, title "Book2", author "Author2", publication year 2021
- Display all books
- Remove book with ID 1
- Display all books

Output:
- Book 1: Book1 by Author1 (2020)
- Book 2: Book2 by Author2 (2021)
- Book 2: Book2 by Author2 (2021)

### CONSTRAINTS
- Must use a 'struct' to represent the Book entity.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Display a book by ID
  5. EXIT the program
- The program should continue to run and display the menu until the user chooses to EXIT (option 5).

---

## Problem 97 - llama-3.3-70b-versatile - Iteration 12
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. To efficiently manage these records, the university wants to implement a system using a singly linked list data structure. The system should allow for adding, removing, and displaying student records.

The background story is that the university currently uses a manual system, which is time-consuming and prone to errors. By implementing a singly linked list, the university aims to automate the process, making it more efficient and reducing the likelihood of errors.

The system should have the following functionality:
1. Add a new student record to the list.
2. Remove a student record from the list based on the student's ID.
3. Display all student records in the list.
4. Display a specific student record based on the student's ID.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all the operations on the linked list.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which will be option 5, labeled as "EXIT".

### EXAMPLE INPUT/OUTPUT
Example input:
- Add student record: ID = 1, Name = John, GPA = 3.5
- Add student record: ID = 2, Name = Alice, GPA = 3.8
- Display all student records
- Remove student record: ID = 1
- Display all student records

Example output:
- After adding student records:
  ID: 1, Name: John, GPA: 3.5
  ID: 2, Name: Alice, GPA: 3.8
- After removing student record with ID = 1:
  ID: 2, Name: Alice, GPA: 3.8

Note: The student struct should have the following members: ID (integer), Name (string), and GPA (float). The displayEntity function should take a pointer to the student struct as an argument and print the student's details. The main function should handle the menu and call the necessary functions to perform the operations.

---

## Problem 98 - llama-3.3-70b-versatile - Iteration 13
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a simple system to keep track of books, with each book having a unique identifier, title, author, and publication year. To efficiently manage the collection, you decide to implement a singly linked list to store and manipulate the book records.

The library's system should allow users to perform the following operations:
1. Add a new book to the collection.
2. Remove a book from the collection by its unique identifier.
3. Display all books in the collection.
4. Search for a book by its title or author.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book, containing fields for the unique identifier, title, author, and publication year.
- The solution must be implemented using a singly linked list.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

### EXAMPLE
Example input:
```
1. Add a new book:
   Unique Identifier: 1
   Title: Introduction to Computer Science
   Author: John Smith
   Publication Year: 2020

2. Add another book:
   Unique Identifier: 2
   Title: Data Structures and Algorithms
   Author: Jane Doe
   Publication Year: 2019

3. Display all books:
   Expected output:
   Book 1:
     Unique Identifier: 1
     Title: Introduction to Computer Science
     Author: John Smith
     Publication Year: 2020
   Book 2:
     Unique Identifier: 2
     Title: Data Structures and Algorithms
     Author: Jane Doe
     Publication Year: 2019
```
The program should handle these operations and display the results accordingly. The menu option to EXIT the program should be clearly labeled as option 5.

---

## Problem 99 - llama-3.3-70b-versatile - Iteration 14
# STEP 1: PROBLEM
In a library management system, books are organized using a singly linked list. Each book has a unique ISBN number, title, author, and publication year. The librarian wants to implement a simple system to manage the books, including adding, removing, and displaying book information.

The system should allow users to:
1. Add a new book to the list.
2. Remove a book by its ISBN number.
3. Display all books in the list.
4. Display the details of a specific book by its ISBN number.
5. Exit the program.

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented with a menu-driven approach.
- The menu options should be numbered from 1 to 5.
- The option to EXIT the program should be numbered as 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a new book
Enter ISBN: 1234567890
Enter title: Introduction to CS
Enter author: John Smith
Enter publication year: 2020

2. Add a new book
Enter ISBN: 9876543210
Enter title: Data Structures
Enter author: Jane Doe
Enter publication year: 2019

3. Display all books
Book 1:
ISBN: 1234567890
Title: Introduction to CS
Author: John Smith
Publication Year: 2020

Book 2:
ISBN: 9876543210
Title: Data Structures
Author: Jane Doe
Publication Year: 2019

4. Display book details
Enter ISBN: 1234567890
Book Details:
ISBN: 1234567890
Title: Introduction to CS
Author: John Smith
Publication Year: 2020

5. Exit
```
Example Output:
```
Library Management System
------------------------
1. Add a new book
2. Remove a book
3. Display all books
4. Display book details
5. Exit

Choose an option: 
```

---

## Problem 100 - llama-3.3-70b-versatile - Iteration 15
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books using a singly linked list. Each book has a unique ID, title, author, and publication year. The librarian needs a program to manage the collection of books.

The program should allow the librarian to perform the following operations:
- Add a new book to the collection
- Remove a book by its ID
- Display all the books in the collection
- Search for a book by its title or author
- Display the details of a specific book by its ID

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The program must have a menu-driven interface with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Display a specific book
  6. EXIT (to exit the program)

## Example Input/Output
When the librarian adds a new book with ID 1, title "Introduction to CS", author "John Doe", and publication year 2020, the program should display a confirmation message. If the librarian chooses to display all books, the program should print the details of all the books in the collection.

Example:
```
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter publication year: 2020
Book added successfully!

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. Display a specific book
6. EXIT

Choose an option: 3

Book ID: 1
Title: Introduction to CS
Author: John Doe
Publication Year: 2020
```

The librarian can continue to interact with the program using the menu options until they choose to EXIT.

---

