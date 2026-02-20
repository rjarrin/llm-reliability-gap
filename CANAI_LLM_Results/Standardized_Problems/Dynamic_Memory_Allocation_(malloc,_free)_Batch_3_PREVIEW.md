# Problem Batch Preview: Dynamic Memory Allocation (malloc, free)
**Batch Number:** 3 | **Total Problems:** 100

---

## Problem 1 - openai/gpt-oss-120b - Iteration 36
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small command‑line inventory manager for a **toy library**.  
Each toy in the library has a name (a string of up to 30 characters) and a weight in grams (an integer).  
The library staff wants to be able to add new toys, remove toys, and view the details of a specific toy while the program is running.  
Because the number of toys is not known in advance, you must allocate memory dynamically.

## Requirements  

Write a C program that implements the following functionality:

1. **Add a Toy**  
   * Prompt the user for the toy’s name and weight.  
   * Dynamically allocate a new `Toy` structure, store the information, and insert it at the end of the current collection.

2. **Remove a Toy**  
   * Prompt the user for the **index** (starting at 0) of the toy to delete.  
   * If the index is valid, free the memory for that toy and shift any subsequent toys so that the collection remains contiguous.  
   * If the index is invalid, display an error message and leave the collection unchanged.

3. **Display a Toy**  
   * Prompt the user for the **index** of the toy to view.  
   * If the index is valid, call a function `displayToy` (see Constraints) to print the toy’s name and weight.  
   * If the index is invalid, display an error message.

4. **List All Toys**  
   * Print the index, name, and weight of every toy currently stored, one per line.

5. **Exit**  
   * Gracefully terminate the program, freeing all allocated memory.

The program should present a simple text menu that repeats after each operation until the user chooses to exit.

## Example Input / Output  

```
=== Toy Library Manager ===
1) Add Toy
2) Remove Toy
3) Display Toy
4) List All Toys
5) Exit
Select an option: 1
Enter toy name: Teddy Bear
Enter weight (g): 350
Toy added.

=== Toy Library Manager ===
1) Add Toy
2) Remove Toy
3) Display Toy
4) List All Toys
5) Exit
Select an option: 1
Enter toy name: Rubber Duck
Enter weight (g): 120
Toy added.

=== Toy Library Manager ===
1) Add Toy
2) Remove Toy
3) Display Toy
4) List All Toys
5) Exit
Select an option: 4
[0] Teddy Bear – 350g
[1] Rubber Duck – 120g

=== Toy Library Manager ===
1) Add Toy
2) Remove Toy
3) Display Toy
4) List All Toys
5) Exit
Select an option: 3
Enter index to display: 0
Toy #0:
  Name : Teddy Bear
  Weight: 350 g

=== Toy Library Manager ===
1) Add Toy
2) Remove Toy
3) Display Toy
4) List All Toys
5) Exit
Select an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Toy` containing at least:
  ```c
  typedef struct {
      char name[31];   // up to 30 characters + terminating null
      int  weight;     // in grams
  } Toy;
  ```

* **Dynamic Allocation** – All toys must be stored in dynamically allocated memory (using `malloc`, `realloc`, and `free`). No static or fixed‑size arrays may be used for the collection.

* **Display Function** – The logic for printing the details of **one specific toy** must reside in a separate function with the exact prototype:
  ```c
  void displayToy(const Toy *t, int index);
  ```

* **Menu Structure** – The program must present a menu as shown in the example.  
  * The menu must contain an explicit option to **EXIT** the program; in the example this is option 5.  

* **Memory Safety** – Before the program terminates (via the Exit option), every block of memory obtained with `malloc`/`realloc` must be released with `free`.  

* **Error Handling** – If the user enters an invalid menu choice or an out‑of‑range index, the program should print a clear error message and re‑display the menu without crashing.  

* **Single‑File Implementation** – All code must reside in a single `.c` source file, but you may define as many helper functions as you need (aside from `main`).  

---  

*Your task is to write the described program, respecting all the constraints above.*

---

## Problem 2 - openai/gpt-oss-120b - Iteration 37
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for the campus library. The library keeps a **dynamic** collection of books that can grow or shrink while the program runs. Each book has a title, an author, and the year it was published. Because the number of books is not known ahead of time, you must allocate and release memory at runtime using `malloc`/`calloc` and `free`.  

Your task is to implement a **menu‑driven** program that lets the user add new books, remove a book by its position in the list, list all stored books, and display the details of a single book. All memory that is allocated must be properly released before the program terminates.

## Requirements  

1. Define a `struct Book` that contains:  
   * `char *title;`   (dynamically allocated string)  
   * `char *author;`  (dynamically allocated string)  
   * `int year;`  

2. The program must maintain a **dynamic array** (or linked list) of `struct Book` objects. The container itself must be allocated with `malloc`/`realloc` as the number of books changes.  

3. Provide a **text menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   ```
   1) Add a new book
   2) Remove a book by index
   3) List all books
   4) Show details of a specific book
   5) EXIT
   ```  

4. **Option 1 – Add a new book**  
   * Prompt the user for the title, author, and year.  
   * Allocate memory for the new `Book` and for the two strings, copy the input, and store the book in the dynamic collection.  

5. **Option 2 – Remove a book by index**  
   * Ask for the zero‑based index of the book to delete.  
   * Validate the index; if it is out of range, print an error message and return to the menu.  
   * Free the memory used by the book’s title, author, and the `Book` structure itself, then shrink the collection accordingly (use `realloc`).  

6. **Option 3 – List all books**  
   * Print each book’s index, title, and author on a separate line.  

7. **Option 4 – Show details of a specific book**  
   * Ask for the index of the book.  
   * Validate the index.  
   * Call a function `void displayBook(const struct Book *b);` that prints the title, author, and year in a readable format.  

8. **Option 5 – EXIT**  
   * Before terminating, free **all** memory that was allocated for every book and for the container itself.  

9. The program must handle input errors gracefully (non‑numeric menu choices, negative indices, etc.) without crashing.

## Example Interaction  

```
--- Library Book Manager ---
1) Add a new book
2) Remove a book by index
3) List all books
4) Show details of a specific book
5) EXIT
Choice: 1
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978

Book added successfully!

--- Library Book Manager ---
1) Add a new book
2) Remove a book by index
3) List all books
4) Show details of a specific book
5) EXIT
Choice: 3

[0] The C Programming Language by Kernighan & Ritchie

--- Library Book Manager ---
1) Add a new book
2) Remove a book by index
3) List all books
4) Show details of a specific book
5) EXIT
Choice: 4
Enter index: 0

Title : The C Programming Language
Author: Kernighan & Ritchie
Year  : 1978

--- Library Book Manager ---
1) Add a new book
2) Remove a book by index
3) List all books
4) Show details of a specific book
5) EXIT
Choice: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be a `struct Book` as described.  
* **Function requirement** – The logic for displaying the details of ONE specific book must be placed in a function named `void displayBook(const struct Book *b);`.  
* **Memory management** – All memory allocated with `malloc`/`calloc`/`realloc` must be released with `free` before the program ends.  
* **Menu exit** – The menu must contain the option `5) EXIT` (or the exact keyword `EXIT`) and selecting it terminates the program after cleaning up.  

Feel free to choose between a dynamic array (using `realloc`) or a singly‑linked list, as long as the above constraints are satisfied.

---

## Problem 3 - openai/gpt-oss-120b - Iteration 38
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny inventory‑management tool for a start‑up that ships custom‑made gadgets.  
Each gadget (an **Item**) has a name, a unit price, and a quantity in stock.  
The number of different items is not known in advance – the program must allocate memory for the list of items at run‑time and be able to grow or shrink this list as the user adds or removes entries.

Your task is to implement this tool using **dynamic memory allocation** (`malloc`, `realloc`, `free`). The program will be driven by a simple text menu.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Item` that contains:  
     * `char *name` – a dynamically allocated string (maximum length 100 characters).  
     * `int quantity` – number of units in stock (≥ 0).  
     * `double price` – unit price in dollars (≥ 0.0).  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | `1` | **Add a new item** – prompt for name, quantity, and price; allocate space for the new `Item` and store it at the end of the list. |
   | `2` | **Remove an item** – ask for the exact name; if the item exists, delete it, shift remaining items, and shrink the allocated array accordingly. |
   | `3` | **Display an item** – ask for the exact name; if found, call `displayItem` (see Constraints) to print its details. |
   | `4` | **List all items** – print the details of every stored item in the order they were added. |
   | `5` | **EXIT** – terminate the program after releasing all allocated memory. |

3. **Dynamic storage**  
   * The list of items must be stored in a **dynamically allocated array** (`Item *items`).  
   * When a new item is added, use `realloc` to enlarge the array by one element.  
   * When an item is removed, shrink the array with `realloc` (or free it completely if it becomes empty).  

4. **Memory management**  
   * Every string stored in `name` must be allocated with `malloc` (or `strdup`).  
   * All allocated memory (the array and each `name` string) must be released with `free` before the program exits.  

5. **Error handling**  
   * If memory allocation fails, print an error message and exit.  
   * If the user tries to remove or display a non‑existent item, print “Item not found.”  

---

## Example Interaction  

```
=== Inventory Manager ===
1. Add item
2. Remove item
3. Display item
4. List all items
5. EXIT
Choose an option: 1
Enter name: Widget
Enter quantity: 12
Enter price: 3.75
Item added.

=== Inventory Manager ===
1. Add item
2. Remove item
3. Display item
4. List all items
5. EXIT
Choose an option: 1
Enter name: Gizmo
Enter quantity: 5
Enter price: 9.99
Item added.

=== Inventory Manager ===
1. Add item
2. Remove item
3. Display item
4. List all items
5. EXIT
Choose an option: 4
--- Inventory List ---
Name: Widget, Quantity: 12, Price: $3.75
Name: Gizmo,  Quantity: 5,  Price: $9.99

=== Inventory Manager ===
1. Add item
2. Remove item
3. Display item
4. List all items
5. EXIT
Choose an option: 3
Enter name to display: Gizmo
Name: Gizmo
Quantity: 5
Price: $9.99

=== Inventory Manager ===
1. Add item
2. Remove item
3. Display item
4. List all items
5. EXIT
Choose an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Item` as described above.  
* **Function requirement** – The logic for displaying the details of **ONE specific item** must be placed in a function with the exact prototype:  

  ```c
  void displayItem(const struct Item *it);
  ```

* **Memory‑only functions** – Apart from `main`, you may create any helper functions you need (e.g., for adding, removing, freeing), but **no additional global variables** are allowed.  
* **Menu exit** – The menu must contain the option `5` (or the keyword `EXIT`) that cleanly terminates the program after all memory has been freed.  

---  

Your solution should compile with a standard C compiler (`gcc -std=c11`) and run on a typical Unix‑like terminal. Good luck!

---

## Problem 4 - openai/gpt-oss-120b - Iteration 39
# STEP 1: PROBLEM  

## Background  
A small community library wants to keep a **runtime‑only** catalogue of the books that are currently on loan. Because the number of loans changes while the program is running, the catalogue must be built with dynamic memory allocation (`malloc`/`free`). Each loan record stores the **ISBN**, the **borrower’s name**, and the **number of days** the book has been borrowed.

You are to write a C program that lets a librarian add new loan records, remove them when a book is returned, and display the details of a particular loan. All data must reside in dynamically allocated memory; no static arrays of fixed size are allowed.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Loan` that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char borrower[51];` // up to 50 characters + null  
     - `int daysBorrowed;`  

2. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1** – Add a new loan record  
   * **2** – Return a book (remove a loan record by ISBN)  
   * **3** – Display a loan record (show the details of ONE specific loan identified by ISBN)  
   * **4** – List all current loans (in the order they were added)  
   * **0** – **EXIT** the program  

3. **Adding a loan**  
   * Prompt the user for ISBN, borrower name, and days borrowed.  
   * Allocate a new `struct Loan` with `malloc`, fill it, and insert it at the end of a singly‑linked list of loans.  

4. **Returning a book**  
   * Prompt for the ISBN to remove.  
   * Search the linked list, unlink the matching node, `free` its memory, and report success or “not found”.  

5. **Displaying a loan**  
   * Prompt for the ISBN.  
   * Locate the matching node and **call a function named `displayLoan`** to print the record in the format shown in the example.  
   * If the ISBN is not present, print an appropriate message.  

6. **Listing all loans**  
   * Traverse the list and print each record using `displayLoan`.  

7. **Program termination**  
   * When the user selects **0**, free **all** remaining allocated memory before exiting.  

---

## Example Interaction  

```
=== Library Loan Manager ===
1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 1
Enter ISBN: 9780131103627
Enter borrower name: Alice Johnson
Enter days borrowed: 5
Loan added.

1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 1
Enter ISBN: 9780262033848
Enter borrower name: Bob Smith
Enter days borrowed: 2
Loan added.

1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 3
Enter ISBN to display: 9780131103627
--- Loan Details ---
ISBN: 9780131103627
Borrower: Alice Johnson
Days Borrowed: 5

1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 2
Enter ISBN to return: 9780262033848
Loan with ISBN 9780262033848 returned.

1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 4
--- All Current Loans ---
ISBN: 9780131103627
Borrower: Alice Johnson
Days Borrowed: 5

1) Add loan
2) Return book
3) Display loan
4) List all loans
0) EXIT
Choice: 0
Cleaning up memory... Goodbye!
```

---

## ### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented by a `struct Loan` as described.  
* **Function Requirement** – The logic for printing the details of a single loan **must** be placed in a function with the exact prototype:  

  ```c
  void displayLoan(const struct Loan *l);
  ```  

* **Memory Management** – Every loan added with `malloc` must be released with `free` exactly once (either when the loan is returned or when the program exits).  
* **Menu Exit Option** – The menu must contain an option **0** that cleanly terminates the program (as shown in the example).  
* **No Global Variables** – All pointers to the head (and optionally tail) of the linked list must be declared inside `main` and passed to helper functions as needed.  
* **Single Source File** – The entire solution should be written in one `.c` file; you may define additional helper functions, but the `main` function must contain the menu loop.  

---  

*Your task*: Implement the described program in C, respecting all requirements and constraints.

---

## Problem 5 - openai/gpt-oss-120b - Iteration 40
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “Student Registry” utility for a university department.  
The registry must keep information about each student **only while the program is running**; when the program terminates all data is lost.  
Because the number of students is not known in advance, you must allocate and release memory dynamically using `malloc` and `free`.

## Program Requirements  

1. **Data representation**  
   - Define a `struct Student` that contains the following fields:  
     - `int id` – a unique positive integer identifier.  
     - `char *name` – a dynamically‑allocated string (maximum length 100 characters, not counting the terminating `'\0'`).  
     - `float gpa` – the student’s grade point average.  

2. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new student** – Prompt for `id`, `name`, and `gpa`. Allocate a new `Student` structure, store the data, and add it to the end of a dynamically‑grown array (or linked list). If a student with the same `id` already exists, print an error and do not add a duplicate. |
   | 2 | **Display a student** – Prompt for an `id` and print the corresponding student’s details. If the `id` is not found, print “Student not found.” |
   | 3 | **Delete a student** – Prompt for an `id`. Remove the matching student from the collection, free all memory associated with that student, and shift the remaining elements so that no gaps remain. If the `id` does not exist, print “Student not found.” |
   | 4 | **List all students** – Print the details of every stored student in the order they were added. If no students are stored, print “No students registered.” |
   | 5 | **Exit** – Terminate the program after freeing all allocated memory. |

3. **Input validation** – The program should handle non‑numeric input for menu choices gracefully (i.e., re‑prompt). For the student fields, you may assume the user enters data of the correct type.

4. **Memory management** – Every allocation performed with `malloc` (or `calloc`) must have a matching `free` before the program ends or when a student is deleted.

## Example Interaction  

```
--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 1
Enter ID: 101
Enter name: Alice Johnson
Enter GPA: 3.8
Student added.

--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 1
Enter ID: 102
Enter name: Bob Smith
Enter GPA: 3.5
Student added.

--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 4
ID: 101, Name: Alice Johnson, GPA: 3.80
ID: 102, Name: Bob Smith, GPA: 3.50

--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 2
Enter ID to display: 101
ID: 101, Name: Alice Johnson, GPA: 3.80

--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 3
Enter ID to delete: 101
Student deleted.

--- Student Registry ---
1) Add student
2) Display student
3) Delete student
4) List all students
5) Exit
Choice: 5
Good‑bye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity **must** be represented with a `struct Student` as described above.  
2. **Display function** – The logic for showing the details of **one** specific student **must** be placed in a function named  

   ```c
   void displayStudent(const struct Student *s);
   ```

3. **Function count** – Apart from `main`, you may create **at most two** additional functions (e.g., `displayStudent` and a helper for freeing memory). Any extra helper functions will cause the solution to be marked incorrect.  
4. **Menu requirement** – The menu must include an explicit option to **EXIT** the program (option 5 in the example). Selecting this option must cause the program to free all allocated memory and terminate cleanly.  

---  

*Design the program so that it compiles with a standard C compiler (`gcc -std=c11`).*

---

## Problem 6 - openai/gpt-oss-120b - Iteration 41
# STEP 1: PROBLEM  

## Background  
You have been hired as a software developer for **CampusConnect**, a small startup that maintains an in‑memory registry of “Club Members” for university student organizations. The registry is transient – it only lives while the program runs – and the number of members is not known ahead of time. Your task is to write a console program that lets the user add members, remove members, and view details of a particular member. All member records must be allocated dynamically using `malloc` (or `calloc`) and released with `free` when they are no longer needed.

## Requirements  

1. **Data representation**  
   * Define a `struct Member` that stores:  
     - an integer `id` (unique identifier)  
     - a string `name` (maximum 50 characters)  
     - an integer `age`  

2. **Program functionality**  
   The program must present a text‑based menu with the following options:  

   1. **Add a new member** – Prompt for `id`, `name`, and `age`. Allocate a new `Member` on the heap and store it in a dynamically‑grown array (or linked list).  
   2. **Delete a member** – Prompt for an `id`. Locate the corresponding `Member`, remove it from the collection, and `free` its memory. If the `id` does not exist, display an appropriate message.  
   3. **Display a member** – Prompt for an `id`. Locate the `Member` and print its details using the function `displayMember`. If the `id` is not found, inform the user.  
   4. **List all members** – Print the `id`, `name`, and `age` of every stored member in the order they were added.  
   5. **EXIT** – Terminate the program, freeing any remaining allocated memory.  

3. **User interaction**  
   * After completing any operation (except EXIT), the menu should be shown again.  
   * Input validation is not required beyond checking whether an `id` exists for delete/display operations.

## Example Input / Output  

```
=== CampusConnect Member Registry ===
1) Add member
2) Delete member
3) Display member
4) List all members
5) EXIT
Choose an option: 1
Enter ID: 101
Enter name: Alice Johnson
Enter age: 20
Member added.

=== CampusConnect Member Registry ===
1) Add member
2) Delete member
3) Display member
4) List all members
5) EXIT
Choose an option: 1
Enter ID: 102
Enter name: Bob Smith
Enter age: 22
Member added.

=== CampusConnect Member Registry ===
1) Add member
2) Delete member
3) Display member
4) List all members
5) EXIT
Choose an option: 4
ID: 101, Name: Alice Johnson, Age: 20
ID: 102, Name: Bob Smith, Age: 22

=== CampusConnect Member Registry ===
1) Add member
2) Delete member
3) Display member
4) List all members
5) EXIT
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice Johnson, Age: 20

=== CampusConnect Member Registry ===
1) Add member
2) Delete member
3) Display member
4) List all members
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Member`.  
* **Display function** – The logic for printing the details of a single member must reside in a function with the exact prototype:  

  ```c
  void displayMember(const struct Member *m);
  ```  

* **Dynamic allocation** – All `Member` objects must be obtained with `malloc`/`calloc` and released with `free`. No static or global arrays of `Member` may be used.  
* **Menu requirement** – The program must include a menu option to **EXIT** the program (option number 5 in the example). Selecting this option must cause the program to terminate after freeing any still‑allocated members.  

*Optional (for extra credit)*: Implement the collection as a singly‑linked list instead of an array. The extra‑credit implementation must still obey all constraints above.  

---

## Problem 7 - openai/gpt-oss-120b - Iteration 42
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny inventory‑management tool for a small outdoor‑gear shop. The shop sells **backpacks**, each of which has a name, a capacity (in liters), and a price (in dollars). Because the shop’s inventory changes daily, the program must allocate memory for each backpack dynamically as it is entered and release that memory when the backpack is removed from the list.

## Requirements  

1. **Data representation**  
   * Define a `struct Backpack` that stores the three fields mentioned above (`char *name`, `int capacity`, `double price`).  

2. **Menu‑driven interface** (the program must present a text menu repeatedly until the user chooses to exit). The menu must contain the following options (the numbers are mandatory):  
   1. **Add a new backpack** – Prompt the user for the name (a single word, maximum 30 characters), capacity, and price. Allocate memory for a new `Backpack` structure and store it in a dynamically‑grown array (you may re‑allocate the array as needed).  
   2. **Remove a backpack** – Ask for the index (starting at 1) of the backpack to delete. Free the memory for that backpack and shift the remaining entries so that the array stays contiguous.  
   3. **Display a backpack** – Ask for the index (starting at 1) of the backpack to view. The details must be printed by calling a function named `displayBackpack`.  
   4. **List all backpacks** – Print a numbered list of every backpack currently stored.  
   5. **EXIT** – Terminate the program, freeing any remaining allocated memory.  

3. **Dynamic memory management**  
   * Use `malloc` (or `calloc`) to allocate each new `Backpack`.  
   * Use `realloc` to grow/shrink the array that holds the pointers to the backpacks.  
   * Use `free` for every allocation before the program ends or when a backpack is removed.  

4. **Input validation**  
   * If the user selects an invalid menu option or an out‑of‑range index, print an error message and redisplay the menu.  

5. **Program termination**  
   * Before exiting, ensure that **all** memory allocated during the run is properly released.  

## Example Interaction  

```
===== Backpack Inventory =====
1) Add a new backpack
2) Remove a backpack
3) Display a backpack
4) List all backpacks
5) EXIT
Choose an option: 1
Enter name: TrailBlazer
Enter capacity (liters): 45
Enter price ($): 129.99
Backpack added.

===== Backpack Inventory =====
1) Add a new backpack
2) Remove a backpack
3) Display a backpack
4) List all backpacks
5) EXIT
Choose an option: 1
Enter name: AlpinePro
Enter capacity (liters): 60
Enter price ($): 199.50
Backpack added.

===== Backpack Inventory =====
1) Add a new backpack
2) Remove a backpack
3) Display a backpack
4) List all backpacks
5) EXIT
Choose an option: 4
1) TrailBlazer – 45 L – $129.99
2) AlpinePro   – 60 L – $199.50

===== Backpack Inventory =====
1) Add a new backpack
2) Remove a backpack
3) Display a backpack
4) List all backpacks
5) EXIT
Choose an option: 3
Enter backpack number to display: 2
--- Backpack #2 ---
Name    : AlpinePro
Capacity: 60 L
Price   : $199.50

===== Backpack Inventory =====
1) Add a new backpack
2) Remove a backpack
3) Display a backpack
4) List all backpacks
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Backpack`.  
* **Display function** – The logic for printing the details of a single backpack must reside in a function with the exact prototype:  
  ```c
  void displayBackpack(const struct Backpack *b, int index);
  ```  
* **Menu implementation** – The menu must include the option **5) EXIT** as shown above. Selecting this option ends the program.  
* **Memory discipline** – No memory leak is allowed; every allocation performed with `malloc`/`calloc`/`realloc` must be matched with a corresponding `free` before program termination.  
* **Single extra function** – Apart from `main`, you may only define the required `displayBackpack` function; any helper functions you write must be declared `static` inside the same source file.  

---  

*Deliverable*: A single C source file (`inventory.c`) that compiles without warnings (e.g., with `-Wall -Wextra -pedantic`) and fulfills all the requirements and constraints above.

---

## Problem 8 - openai/gpt-oss-120b - Iteration 43
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Track**, a startup that monitors the growth of trees in a city park. Each tree is recorded with three pieces of information:  

* **ID** – an integer that uniquely identifies the tree.  
* **Species** – a short string (maximum 30 characters) describing the tree type (e.g., “Oak”, “Maple”).  
* **Height** – a floating‑point value representing the current height of the tree in meters.  

Because the number of trees changes over time (new saplings are planted and old trees are removed), the program must allocate memory dynamically for each tree record.  

## Requirements  
Write a C program that allows the user to manage the collection of trees using a **menu‑driven interface**. The program must support the following operations:

1. **Add a new tree**  
   * Prompt the user for the tree’s ID, species, and height.  
   * Allocate memory for a new `Tree` structure with `malloc`.  
   * Store the information and insert the new node at the end of a singly‑linked list.

2. **Delete a tree**  
   * Ask for the ID of the tree to remove.  
   * Search the list; if the tree is found, unlink it, `free` its memory, and report success.  
   * If the ID does not exist, print an appropriate message.

3. **Display a tree’s details**  
   * Ask for the ID of the tree to view.  
   * Locate the tree in the list and call a function `displayTree` (see constraints) to print its data in the format:  
     `Tree ID: <id>, Species: <species>, Height: <height> m`  
   * If the tree is not found, inform the user.

4. **List all trees**  
   * Traverse the entire list and print each tree’s information using `displayTree`.

5. **Exit the program**  
   * Choose the menu option **0** to terminate the program. Before exiting, free any remaining allocated memory.

The program should continue to display the menu after each operation until the user selects the exit option.

## Example Interaction  

```
=== Eco‑Track Tree Manager ===
1. Add a new tree
2. Delete a tree
3. Display a tree
4. List all trees
0. Exit
Enter choice: 1
Enter Tree ID: 101
Enter Species (max 30 chars): Oak
Enter Height (m): 4.2
Tree added.

=== Eco‑Track Tree Manager ===
1. Add a new tree
2. Delete a tree
3. Display a tree
4. List all trees
0. Exit
Enter choice: 1
Enter Tree ID: 102
Enter Species (max 30 chars): Maple
Enter Height (m): 3.7
Tree added.

=== Eco‑Track Tree Manager ===
1. Add a new tree
2. Delete a tree
3. Display a tree
4. List all trees
0. Exit
Enter choice: 3
Enter Tree ID to display: 101
Tree ID: 101, Species: Oak, Height: 4.20 m

=== Eco‑Track Tree Manager ===
1. Add a new tree
2. Delete a tree
3. Display a tree
4. List all trees
0. Exit
Enter choice: 4
Tree ID: 101, Species: Oak, Height: 4.20 m
Tree ID: 102, Species: Maple, Height: 3.70 m

=== Eco‑Track Tree Manager ===
1. Add a new tree
2. Delete a tree
3. Display a tree
4. List all trees
0. Exit
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be defined as a `struct` named `Tree` containing the fields `int id; char species[31]; float height; struct Tree *next;`.  
* **Display Function** – The logic for printing the details of a single tree **must** be placed in a separate function with the exact prototype:  

  ```c
  void displayTree(const struct Tree *t);
  ```  

* **Memory Management** – Every tree added with `malloc` must eventually be released with `free`. No memory leaks are permitted.  
* **Menu Exit Option** – The menu must include option **0** (zero) labeled “Exit” that terminates the program after freeing all allocated memory.  

*Optional (but recommended for grading):*  
- Use defensive programming: validate that the ID entered for a new tree does not already exist in the list.  
- Limit the species string to 30 characters; excess input should be truncated safely.  

---  

Implement the program according to the above specifications and constraints.

---

## Problem 9 - openai/gpt-oss-120b - Iteration 44
# STEP 1: PROBLEM  

## Background  
You have been hired as the software developer for **Eco‑Garden**, a small startup that sells custom‑designed garden beds. Each garden bed consists of a variable‑length list of plant slots, and each slot can hold a single plant type (e.g., “Tomato”, “Basil”, “Lettuce”). The number of slots for a bed is not known until the user creates the bed, so the program must allocate memory dynamically.

Your task is to write a C program that lets the user **create**, **view**, **add plants to**, and **delete** garden beds. All memory that is allocated with `malloc` (or related functions) must be released with `free` before the program terminates.

## Requirements  

1. **Data representation**  
   * Define a `struct PlantSlot` that stores the name of the plant (a null‑terminated string, maximum length 31 characters).  
   * Define a `struct GardenBed` that stores:  
     - an integer `id` (unique identifier for the bed)  
     - an integer `slotCount` (the number of plant slots)  
     - a pointer `PlantSlot *slots` that points to a dynamically allocated array of `PlantSlot` objects.  

2. **Menu‑driven interface** (the program must present a text menu after each operation)  
   * **1. Create a new garden bed**  
     - Prompt for the bed’s `id` (must be positive and not already used).  
     - Prompt for the number of slots `N` (positive integer).  
     - Allocate memory for the `GardenBed` and for its `slots` array (`N` elements).  
     - Initialise every slot’s plant name to the string `"empty"`.  
   * **2. Add a plant to a slot**  
     - Prompt for the bed `id`.  
     - Prompt for the slot index (0‑based).  
     - Prompt for the plant name (max 31 characters, no spaces).  
     - If the index is valid, store the name in the corresponding `PlantSlot`.  
   * **3. Display a garden bed**  
     - Prompt for the bed `id`.  
     - Show the bed’s `id`, total number of slots, and for each slot its index and stored plant name.  
     - The logic that prints a single bed must be placed in a function called `void displayBed(const GardenBed *bed);`.  
   * **4. Delete a garden bed**  
     - Prompt for the bed `id`.  
     - Free the memory used for its `slots` array and then free the `GardenBed` itself.  
   * **5. List all existing garden beds**  
     - Print the `id` of every currently allocated bed.  
   * **0. EXIT** – terminate the program. The program must free any remaining allocated memory before exiting.  

3. **Error handling**  
   * If the user requests an operation on a non‑existent bed, print an appropriate error message.  
   * If the user provides an out‑of‑range slot index, print an error message.  
   * If memory allocation fails, print an error and terminate gracefully.  

## Example Interaction  

```
=== Eco‑Garden Management ===
1) Create a new garden bed
2) Add a plant to a slot
3) Display a garden bed
4) Delete a garden bed
5) List all garden beds
0) EXIT
Select option: 1
Enter bed id: 101
Enter number of slots: 3
Garden bed 101 created with 3 slots.

=== Eco‑Garden Management ===
1) Create a new garden bed
2) Add a plant to a slot
3) Display a garden bed
4) Delete a garden bed
5) List all garden beds
0) EXIT
Select option: 2
Enter bed id: 101
Enter slot index (0‑2): 1
Enter plant name: Tomato
Plant added.

=== Eco‑Garden Management ===
1) Create a new garden bed
2) Add a plant to a slot
3) Display a garden bed
4) Delete a garden bed
5) List all garden beds
0) EXIT
Select option: 3
Enter bed id: 101

--- Garden Bed 101 ---
Slots: 3
[0] empty
[1] Tomato
[2] empty
-------------------------

=== Eco‑Garden Management ===
1) Create a new garden bed
2) Add a plant to a slot
3) Display a garden bed
4) Delete a garden bed
5) List all garden beds
0) EXIT
Select option: 0
Cleaning up… all memory freed. Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with the `struct GardenBed` (as described above).  
* **Display function** – The logic for displaying the details of ONE specific garden bed must be implemented in a function named `void displayBed(const GardenBed *bed);`. No other function may perform the same task.  
* **Menu requirement** – The menu must include the option **0) EXIT** to terminate the program. Selecting this option must free any still‑allocated memory before ending.  
* **Dynamic allocation only** – All arrays (`slots`) and the garden‑bed objects themselves must be allocated with `malloc`/`calloc` (or `realloc` if you choose) and released with `free`. No static or global fixed‑size arrays may be used to store the beds.  

*Optional (for extra credit)*: Implement the collection of garden beds using a singly‑linked list, also allocated dynamically. The list management functions (insert, delete, search) must be separate from `main`.  

---  

*Write the program in C, compile with `gcc -Wall -Wextra -std=c11`. The solution will be evaluated for correctness, proper memory management (no leaks), and adherence to the constraints above.*

---

## Problem 10 - openai/gpt-oss-120b - Iteration 45
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior software developer for **EcoLog**, a small startup that monitors the growth of plants in a greenhouse.  
Each plant is identified by a **Plant ID**, a **species name**, and a **current height in centimeters**.  
The greenhouse can hold an arbitrary number of plants, but the exact number is not known until the program runs.  
Your task is to write a C program that lets the user **add**, **remove**, **list**, and **query** plants.  
Because the number of plants changes at runtime, you must allocate and free memory dynamically using `malloc` and `free`.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Plant` that contains:  
     * `int id;` – unique identifier (positive integer)  
     * `char *species;` – dynamically allocated string (max length 50 characters)  
     * `float height;` – current height in centimeters  

2. **Menu‑driven Interface** (the program must present a menu after each operation)  
   * **1. Add a plant** – Prompt for ID, species name, and height, allocate a new `Plant`, store it in a dynamic array that grows as needed.  
   * **2. Remove a plant** – Prompt for an ID, locate the plant, free its `species` string and the `Plant` structure, and shrink the dynamic array accordingly.  
   * **3. List all plants** – Print a table showing ID, species, and height for every plant currently stored.  
   * **4. Show plant details** – Prompt for an ID and display the information of that single plant. The display logic **must** be in a function named `displayPlant`.  
   * **5. EXIT** – Terminate the program, freeing all remaining allocated memory.  

3. **Dynamic Array Management**  
   * The array of `Plant*` pointers should start empty.  
   * When a new plant is added, enlarge the array with `realloc`.  
   * When a plant is removed, shrink the array with `realloc` (or shift elements and `realloc` at the end).  

4. **Error Handling**  
   * If the user tries to add a plant with an ID that already exists, print an error and do **not** add a duplicate.  
   * If the user requests removal or display of a non‑existent ID, print an appropriate message.  
   * All memory allocation failures must be detected and reported, then the program should exit gracefully.  

5. **Program Termination**  
   * Before exiting (via the menu option 5), free every `species` string, every `Plant` structure, and the array that holds the pointers.  

## Example Interaction  

```
=== EcoLog Plant Manager ===
1) Add a plant
2) Remove a plant
3) List all plants
4) Show plant details
5) EXIT
Choose an option: 1

Enter Plant ID: 101
Enter species name: Basil
Enter height (cm): 12.5
Plant added successfully.

=== EcoLog Plant Manager ===
1) Add a plant
2) Remove a plant
3) List all plants
4) Show plant details
5) EXIT
Choose an option: 1

Enter Plant ID: 102
Enter species name: Tomato
Enter height (cm): 25.0
Plant added successfully.

=== EcoLog Plant Manager ===
1) Add a plant
2) Remove a plant
3) List all plants
4) Show plant details
5) EXIT
Choose an option: 3

ID   Species   Height(cm)
101  Basil     12.5
102  Tomato    25.0

=== EcoLog Plant Manager ===
1) Add a plant
2) Remove a plant
3) List all plants
4) Show plant details
5) EXIT
Choose an option: 4

Enter Plant ID to view: 101
--- Plant Details ---
ID: 101
Species: Basil
Height: 12.5 cm

=== EcoLog Plant Manager ===
1) Add a plant
2) Remove a plant
3) List all plants
4) Show plant details
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented by a `struct Plant` as described above.  
* **Display Function** – The logic for displaying the details of ONE specific plant must be implemented in a function with the exact prototype:  

  ```c
  void displayPlant(const struct Plant *p);
  ```  

* **Menu Requirement** – The program **must** include a menu option to **EXIT** the program (option 5 in the example). Selecting this option must cause the program to free all allocated memory and terminate.  
* **Dynamic Allocation Only** – All plant data (including the species string) must be allocated with `malloc`/`calloc`/`realloc` and released with `free`. No static or global arrays of fixed size are allowed for storing plants.  
* **Single Source File** – The entire solution should be contained in one `.c` file, using only the standard C library (`stdio.h`, `stdlib.h`, `string.h`).  

---  

*Write a program that fulfills the specifications above, demonstrating correct use of `malloc`, `free`, and dynamic array management.*

---

## Problem 11 - openai/gpt-oss-120b - Iteration 46
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “Student Registry” program for a small community college. The college wants a command‑line tool that can store an arbitrary number of student records while the program runs, and release all memory when the user decides to quit. Each student record contains the student’s ID (an integer), full name (a string of up to 50 characters), and GPA (a floating‑point number).  

Because the number of students is not known in advance, you must allocate memory dynamically with `malloc`/`calloc` and free it with `free`. The program will present a simple text menu that lets the user add new students, list all stored students, and look up a single student by ID.

## Requirements  

1. **Data representation**  
   * Define a `struct Student` that holds the three fields described above.  
   * The program must keep the student records in a dynamically allocated array that can grow as new students are added.  

2. **Menu** (displayed repeatedly until the user chooses to exit)  
   1. **Add a student** – Prompt for ID, name, and GPA, allocate space for a new `Student`, store it, and expand the array as needed.  
   2. **List all students** – Print a table of every stored student (ID, name, GPA).  
   3. **Find a student by ID** – Ask for an ID, search the array, and display that student’s details (or a “not found” message).  
   4. **Exit** – Free all allocated memory and terminate the program.  

3. **Input validation**  
   * IDs must be positive integers; if a duplicate ID is entered, print an error and do not add the student.  
   * GPA must be a number between 0.0 and 4.0 inclusive; otherwise print an error and discard the input.  

4. **Memory management**  
   * Use `malloc`/`realloc` to grow the array; never allocate a fixed‑size array larger than needed.  
   * Every allocated block must be released with `free` before the program exits.  

5. **User interaction** – All prompts and messages should be clear and user‑friendly.

## Example Interaction  

```
--- Student Registry ---
1) Add a student
2) List all students
3) Find a student by ID
4) Exit
Choose an option: 1

Enter student ID: 1024
Enter full name: Alice Johnson
Enter GPA (0.0 - 4.0): 3.7
Student added successfully.

--- Student Registry ---
1) Add a student
2) List all students
3) Find a student by ID
4) Exit
Choose an option: 1

Enter student ID: 2048
Enter full name: Bob Smith
Enter GPA (0.0 - 4.0): 4.1
Error: GPA must be between 0.0 and 4.0.

--- Student Registry ---
1) Add a student
2) List all students
3) Find a student by ID
4) Exit
Choose an option: 2

ID    Name           GPA
1024  Alice Johnson  3.70

--- Student Registry ---
1) Add a student
2) List all students
3) Find a student by ID
4) Exit
Choose an option: 3

Enter ID to search: 1024
Student found:
ID: 1024
Name: Alice Johnson
GPA: 3.70

--- Student Registry ---
1) Add a student
2) List all students
3) Find a student by ID
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Student`.  
* **Function requirement** – The logic that displays the details of **one specific student** (used by the “Find a student by ID” option) must be placed in a function named `void displayStudent(const struct Student *s);`.  
* **Menu exit option** – The menu must contain an explicit option to **EXIT** the program; in the example it is option `4`.  
* **Single‑responsibility functions** – Apart from `main`, you may create additional helper functions, but the dynamic‑array resizing logic must be isolated in a function called `Student* resizeArray(Student *arr, size_t newSize);`.  
* **No global variables** – All data structures must be allocated and passed explicitly; do not use global variables for the student array or its size.  

Your task is to write the complete C program that satisfies all of the above specifications.

---

## Problem 12 - openai/gpt-oss-120b - Iteration 47
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for the campus library’s “Book‑Swap” program.  The program must keep track of **book requests** submitted by students.  
Each request contains the student’s ID, the title of the book they would like to borrow, and the number of days they need the book.  
Because the number of requests is not known in advance and can change while the program runs, you must store the requests in dynamically allocated memory.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Request` that holds:  
     * `int studentId` – a positive integer.  
     * `char *title` – a dynamically allocated string (maximum length 100 characters).  
     * `int days` – number of days the book is needed (1 – 30).  

2. **Menu‑driven Interface** (the program must present a text menu repeatedly until the user chooses to exit)  
   * **1 – Add a new request**  
     * Prompt for the three fields, allocate memory for a new `Request`, and store it in a dynamically‑grown array (use `malloc`/`realloc`).  
   * **2 – List all requests**  
     * Print each stored request on its own line in the order they were added.  
   * **3 – Delete a request**  
     * Prompt for a `studentId`. If a request with that ID exists, remove it from the array, free the memory used for its title, and shrink the array accordingly. If not found, display “Request not found.”  
   * **4 – Show a specific request**  
     * Prompt for a `studentId`. If found, call a function `displayRequest` (see constraints) to print the details; otherwise print “Request not found.”  
   * **5 – EXIT** – terminate the program, freeing all allocated memory.  

3. **Memory Management**  
   * Every allocation performed with `malloc`/`realloc` must have a matching `free` before the program terminates.  
   * The program must not leak memory when requests are deleted or when the program ends.

4. **Error Handling**  
   * If memory allocation fails, print “Memory allocation error.” and return to the menu.  
   * Validate user input for the numeric fields; if an invalid value is entered, display an appropriate message and re‑prompt.

## Example Interaction  

```
=== Book‑Swap Request Manager ===
1) Add request
2) List all requests
3) Delete request
4) Show request
5) EXIT
Choose an option: 1

Enter student ID: 12345
Enter book title: The C Programming Language
Enter number of days (1‑30): 14
Request added.

=== Book‑Swap Request Manager ===
1) Add request
2) List all requests
3) Delete request
4) Show request
5) EXIT
Choose an option: 2

Requests:
[1] ID: 12345 | Title: The C Programming Language | Days: 14

=== Book‑Swap Request Manager ===
1) Add request
2) List all requests
3) Delete request
4) Show request
5) EXIT
Choose an option: 4

Enter student ID to view: 12345
--- Request Details ---
Student ID : 12345
Title      : The C Programming Language
Days       : 14

=== Book‑Swap Request Manager ===
1) Add request
2) List all requests
3) Delete request
4) Show request
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented by a `struct Request`.  
* **Display Function** – The logic for displaying the details of a single request must be placed in a function with the exact prototype:  

  ```c
  void displayRequest(const struct Request *req);
  ```  

* **Single‑File Implementation** – Apart from `main`, you may define helper functions, but the entire solution must be contained in one source file.  
* **Menu Exit Option** – The menu must include an explicit option labeled **5) EXIT** (or the keyword `EXIT`) that terminates the program.  

---  

*Note: The problem is intended for students who have just learned `malloc`, `free`, `realloc`, and basic struct handling in C.*

---

## Problem 13 - openai/gpt-oss-120b - Iteration 48
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “student roster” utility for a university department. The program must keep information about an arbitrary number of students entered at runtime. Because the number of students is not known beforehand, you must allocate and release memory dynamically using `malloc` and `free`.  

Each student record contains:  

* an integer **ID** (a positive number)  
* a string **name** (maximum 30 characters, no spaces)  
* a floating‑point **GPA** (0.0 – 4.0)  

The program will run in a loop presenting a text menu, allowing the user to add new students, list all stored students, remove a student by ID, and finally exit.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Student` that holds the three fields described above.  

2. **Dynamic storage**  
   * All student records must be stored in a dynamically allocated array that can grow as new students are added.  
   * When a student is removed, the memory for that specific record must be released and the remaining records shifted so that the array stays contiguous.  

3. **Menu‑driven interface** (the program must loop until the user chooses to exit)  
   * **1 – Add a student**  
        * Prompt for ID, name, and GPA.  
        * Allocate space for the new record, copy the data, and expand the array.  
        * If the entered ID already exists, print an error and do **not** add a duplicate.  
   * **2 – List all students**  
        * Print a table showing ID, name, and GPA for every stored student, in the order they were entered.  
        * The printing of a single student’s details must be performed by a function named `displayStudent`.  
   * **3 – Delete a student**  
        * Prompt for the ID of the student to delete.  
        * If the ID exists, remove that student, free its memory, and shrink the array.  
        * If the ID does not exist, print an appropriate message.  
   * **4 – EXIT**  
        * Terminate the program after freeing all allocated memory.  

4. **Input validation**  
   * The program should handle non‑numeric input for menu choices gracefully (you may assume the user enters correct types for ID, name, and GPA).  

5. **Memory management**  
   * No memory leak is allowed: every block obtained with `malloc`/`realloc` must eventually be released with `free`.  

---

## Example Interaction  

```
--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 1
Enter ID: 1024
Enter name: Alice
Enter GPA: 3.8
Student added.

--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 1
Enter ID: 2048
Enter name: Bob
Enter GPA: 3.2
Student added.

--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 2
ID     Name                           GPA
------------------------------------------------
1024   Alice                          3.80
2048   Bob                            3.20

--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 3
Enter ID to delete: 1024
Student removed.

--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 2
ID     Name                           GPA
------------------------------------------------
2048   Bob                            3.20

--- Student Roster Menu ---
1) Add a student
2) List all students
3) Delete a student
4) EXIT
Enter choice: 4
Goodbye!
```

---

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Student`.  
* **Display function** – The logic for printing the details of a single student must be placed in a function with the exact prototype:  
  ```c
  void displayStudent(const struct Student *s);
  ```  
* **Menu requirement** – The program must present a menu as described above and **must include option 4 (EXIT)** to terminate the program.  
* **Single‑responsibility functions** – Apart from `main`, you may create additional helper functions, but the core operations (add, list, delete) should each be encapsulated in their own function.  
* **Dynamic allocation only** – Do **not** use static or global arrays to store the students; the array must be created with `malloc`/`realloc` and resized as needed.  

---  

*Your task is to write a complete C program that satisfies all of the above.*

---

## Problem 14 - openai/gpt-oss-120b - Iteration 49
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Garden**, a small startup that sells custom‑built garden planters. Each planter can hold a variable number of plants, and the company wants a simple console program that lets a store clerk add new planters, record the plants that go inside each one, and later view or delete a specific planter. Because the number of planters and the number of plants per planter are not known ahead of time, you must allocate memory dynamically with `malloc`/`free`.

## Requirements  

Write a C program that implements the following functionality:

1. **Data representation**  
   * Define a `struct Plant` that stores the plant’s **name** (max 30 characters) and **height** in centimeters (integer).  
   * Define a `struct Planter` that stores:  
     - an **ID** (integer, unique for each planter, assigned automatically starting from 1)  
     - a **capacity** – maximum number of plants it can hold (integer)  
     - a **count** – current number of plants stored (integer)  
     - a **dynamic array** of `Plant` objects (`Plant *plants`).  

2. **Menu‑driven interface** (the program must present a menu after each operation). The menu must contain the following options (the numbers are mandatory):  

   ```
   1. Add a new planter
   2. Insert a plant into a planter
   3. Display a planter’s details
   4. Delete a planter
   5. EXIT
   ```

3. **Option 1 – Add a new planter**  
   * Prompt the user for the planter’s capacity (positive integer).  
   * Allocate a `Planter` structure and its internal `plants` array using `malloc`.  
   * Initialise `count` to 0, assign the next available ID, and store the new planter in a dynamic list of all planters.  

4. **Option 2 – Insert a plant into a planter**  
   * Ask for the planter ID.  
   * If the ID does not exist, print an error message.  
   * If the planter is already full, print “Planter is full.”  
   * Otherwise, prompt for the plant’s name and height, allocate a `Plant` (or copy the data into the next slot of the array), and increment the planter’s `count`.  

5. **Option 3 – Display a planter’s details**  
   * Ask for the planter ID.  
   * If the ID does not exist, print an error message.  
   * Otherwise, call a function `void displayPlanter(const Planter *p)` that prints:  
     - Planter ID  
     - Capacity and current count  
     - For each plant stored, its index (starting at 1), name, and height.  

6. **Option 4 – Delete a planter**  
   * Ask for the planter ID.  
   * If the ID does not exist, print an error message.  
   * Otherwise, free the planter’s internal `plants` array, remove the planter from the list, and free the `Planter` structure itself.  

7. **Option 5 – EXIT**  
   * Before terminating, free **all** memory that is still allocated (any remaining planters and their plant arrays).  

8. The program must handle invalid menu choices gracefully (print a short message and redisplay the menu).

## Example Interaction  

```
=== Eco‑Garden Planter Manager ===
1. Add a new planter
2. Insert a plant into a planter
3. Display a planter’s details
4. Delete a planter
5. EXIT
Enter choice: 1
Enter capacity of new planter: 3
Planter created with ID 1.

1. Add a new planter
2. Insert a plant into a planter
3. Display a planter’s details
4. Delete a planter
5. EXIT
Enter choice: 2
Enter planter ID: 1
Enter plant name: Tomato
Enter plant height (cm): 45
Plant added.

1. Add a new planter
2. Insert a plant into a planter
3. Display a planter’s details
4. Delete a planter
5. EXIT
Enter choice: 3
Enter planter ID: 1
--- Planter 1 ---
Capacity: 3, Plants stored: 1
1) Tomato, 45 cm

1. Add a new planter
2. Insert a plant into a planter
3. Display a planter’s details
4. Delete a planter
5. EXIT
Enter choice: 5
Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entities **must** be represented with the `struct Plant` and `struct Planter` definitions described above.  
* **Display function** – The logic for showing the details of **one specific planter** **must** reside in a function named `void displayPlanter(const Planter *p)`.  
* **Dynamic list of planters** – You may store the collection of planters in a dynamically‑resized array (using `realloc`) or a linked list, but **all memory must be obtained with `malloc`/`realloc` and released with `free`.**  
* **Menu requirement** – The program **must** include the menu option `5. EXIT` as shown, and selecting it must cause the program to free all allocated memory before terminating.  
* **No global variables** – All data structures should be allocated and passed via pointers; do not rely on global variables for storing the planter list.  

Your solution will be evaluated on correctness, proper use of dynamic memory functions, clean deallocation of all resources, and adherence to the constraints above.

---

## Problem 15 - openai/gpt-oss-120b - Iteration 50
# STEP 1: PROBLEM  

## Background  
You have been hired as a software developer for **CampusConnect**, a small startup that maintains a simple in‑memory registry of students for a campus‑wide event. The registry must be built from scratch using dynamic memory allocation (`malloc`, `free`). The program will run only while the organizer is entering data; once the program exits, all allocated memory must be released.

## Requirements  

Write a C program that implements a **menu‑driven** student registry with the following capabilities:

1. **Add a student**  
   - Prompt the user for the student’s **full name** (a string of up to 100 characters, may contain spaces), **age** (positive integer), and **GPA** (floating‑point number between 0.0 and 4.0).  
   - Allocate a new `Student` structure on the heap and store the information.  
   - Insert the new student at the **end** of the current list.

2. **Display all students**  
   - Print a table showing the index (starting from 1), name, age, and GPA of every student currently stored.

3. **Search for a student by name**  
   - Prompt for a name (exact match, case‑sensitive).  
   - If a matching student exists, display that student’s details using the dedicated display function (see constraints).  
   - If no match is found, print “Student not found.”

4. **Delete a student by index**  
   - Prompt for the index shown in the “display all” list.  
   - Remove the corresponding student from the list, free the associated memory, and shift the remaining entries so that indices stay contiguous.

5. **Exit**  
   - Free **all** dynamically allocated memory and terminate the program.

The program must continue to show the menu after each operation until the user selects the **Exit** option.

## Example Interaction  

```
=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 1

Enter name: Alice Johnson
Enter age: 20
Enter GPA: 3.75
Student added.

=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 1

Enter name: Bob Lee
Enter age: 22
Enter GPA: 3.42
Student added.

=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 2

Index  Name            Age  GPA
1      Alice Johnson   20   3.75
2      Bob Lee         22   3.42

=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 3

Enter name to search: Bob Lee
--- Student Details ---
Name: Bob Lee
Age : 22
GPA : 3.42

=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 4

Enter index to delete: 1
Student removed.

=== CampusConnect Student Registry ===
1) Add student
2) Display all students
3) Search student by name
4) Delete student by index
5) Exit
Choose an option: 5
All memory freed. Goodbye!
```

## ### CONSTRAINTS  

1. **Data structure** – The primary entity must be represented by a `struct` named `Student` containing at least the fields `char *name; int age; float gpa;`.  
2. **Dynamic allocation** – Every `Student` instance must be allocated with `malloc` (or `calloc`) and released with `free`. The list of pointers to students must also be managed dynamically (e.g., an array that grows with `realloc`).  
3. **Display function** – The logic for printing the details of **one** specific student must reside in a function with the exact prototype:  

   ```c
   void displayStudent(const Student *s);
   ```

4. **Menu implementation** – The program must present a textual menu as shown in the example.  
   - The menu must include an explicit option to **EXIT** the program (option 5 in the example). Selecting this option must cause the program to free all allocated memory and terminate.  

5. **No global variables** – All data structures must be created and passed explicitly; global variables are not allowed.  

6. **Error handling** – The program should handle invalid menu choices, non‑numeric input for age/index, and out‑of‑range indices gracefully, prompting the user again without crashing.  

---  

*Deliver a single C source file that compiles with `gcc -Wall -Wextra -std=c11` and fulfills all the above requirements.*

---

## Problem 16 - openai/gpt-oss-120b - Iteration 51
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Library Automation Team** to write a small utility that lets a librarian keep track of the books currently on loan.  
Because the number of borrowed books changes constantly, the program must allocate memory dynamically as books are added and release it when they are returned.  

The librarian will interact with the program through a simple text‑based menu.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Book` that stores:  
     - an integer `id` (unique identifier)  
     - a string `title` (maximum 100 characters)  
     - a string `borrower` (maximum 50 characters)  

2. **Menu Options** (the program must display a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new loan** – Prompt for `id`, `title`, and `borrower`. Allocate a new `Book` with `malloc` and store it in a dynamic array that grows as needed. |
   | 2 | **Return a book** – Prompt for the `id` of the book being returned. Locate the matching `Book` in the array, free its memory, and shift the remaining entries so that there are no gaps. |
   | 3 | **List all current loans** – Print the details of every `Book` still stored. |
   | 4 | **Display a specific loan** – Prompt for an `id` and show the details of that single `Book`. The logic for this must be placed in a function named `displayEntity`. |
   | 5 | **Exit** – Terminate the program cleanly, freeing any memory that is still allocated. |

3. **Dynamic Array Management**  
   * Start with a capacity for 2 books.  
   * When the array becomes full, double its capacity using `realloc`.  
   * When the number of stored books falls below one‑quarter of the capacity after a return, shrink the array to half its current size (but never shrink below the initial capacity of 2).  

4. **Input Validation**  
   * If the user tries to add a book whose `id` already exists, print an error and do not add a duplicate.  
   * If the user attempts to return or display a book with an `id` that does not exist, print an appropriate message.  

5. **Program Termination**  
   * Before exiting, free **all** memory that was allocated for `Book` structures and for the dynamic array itself.

## Example Interaction  

```
=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 1

Enter Book ID: 101
Enter Title: Introduction to Algorithms
Enter Borrower Name: Alice

Book added successfully.

=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 1

Enter Book ID: 102
Enter Title: Clean Code
Enter Borrower Name: Bob

Book added successfully.

=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 3

Current loans:
ID: 101 | Title: Introduction to Algorithms | Borrower: Alice
ID: 102 | Title: Clean Code                | Borrower: Bob

=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 4

Enter Book ID to display: 101
ID: 101
Title: Introduction to Algorithms
Borrower: Alice

=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 2

Enter Book ID to return: 101
Book returned and memory freed.

=== Library Loan Manager ===
1) Add a new loan
2) Return a book
3) List all current loans
4) Display a specific loan
5) Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Book`.  
* **Function Requirement** – The logic that prints the details of a single book must be implemented in a function named `displayEntity`. Its prototype should be:  

  ```c
  void displayEntity(const struct Book *b);
  ```  

* **Memory Management** – Every `malloc`/`realloc` must have a matching `free`. No memory leaks are allowed.  
* **Menu Exit** – The menu must include an explicit option (option **5**) to **EXIT** the program. Selecting this option must cause the program to terminate after freeing all allocated memory.  

*You may create additional helper functions (e.g., for searching, resizing the array), but the two constraints above are mandatory.*

---

## Problem 17 - openai/gpt-oss-120b - Iteration 52
# STEP 1: PROBLEM  

## Background  
A small community library wants to keep a simple in‑memory roster of its members.  
Each member record stores the member’s **ID number**, **full name**, and the **number of books currently borrowed**.  
The library staff will interact with the program through a text‑based menu that allows them to add new members, remove members, update the number of borrowed books, and view a member’s details.  

You have just learned how to allocate and free memory dynamically with `malloc` and `free`.  
Write a program that stores the roster in a dynamically‑allocated array that can grow or shrink as members are added or removed.

## Requirements  

1. Define a `struct` named `Member` that contains  
   * `int id;` – unique identifier (positive integer)  
   * `char *name;` – dynamically allocated string (maximum length 100 characters)  
   * `int booksBorrowed;` – number of books the member currently has  

2. The program must present a menu with the following options (the user selects the option by entering the shown number):  

   1. **Add a new member** – Prompt for `id`, `name`, and `booksBorrowed`.  
      * If the `id` already exists, print an error and do not add.  
      * Expand the dynamic array to accommodate the new entry.  

   2. **Remove a member** – Prompt for `id`.  
      * If the `id` is found, remove that member, shrink the array, and free all memory associated with the member’s name.  
      * If the `id` does not exist, print an error.  

   3. **Update books borrowed** – Prompt for `id` and the new `booksBorrowed` value.  
      * If the `id` exists, update the field; otherwise, print an error.  

   4. **Display a member’s details** – Prompt for `id`.  
      * If found, call a function `displayMember` (see Constraints) to print the member’s information.  
      * If not found, print an error.  

   5. **List all members** – Print the details of every member currently stored, in the order they were added.  

   6. **Exit** – Terminate the program, freeing all allocated memory.  

3. All input should be read from `stdin`; all output should be written to `stdout`.  

4. The program must never leak memory: every allocation performed with `malloc` (or `calloc`/`realloc`) must eventually be released with `free` before the program terminates.  

## Example Interaction  

```
--- Library Member Roster ---
1) Add a new member
2) Remove a member
3) Update books borrowed
4) Display a member’s details
5) List all members
6) Exit
Enter option: 1
Enter ID: 101
Enter name: Alice Johnson
Enter books borrowed: 2
Member added.

Enter option: 1
Enter ID: 102
Enter name: Bob Smith
Enter books borrowed: 0
Member added.

Enter option: 4
Enter ID to display: 101
Member ID: 101
Name: Alice Johnson
Books borrowed: 2

Enter option: 5
Member ID: 101, Name: Alice Johnson, Books borrowed: 2
Member ID: 102, Name: Bob Smith, Books borrowed: 0

Enter option: 3
Enter ID: 102
Enter new number of books borrowed: 3
Books borrowed updated.

Enter option: 2
Enter ID to remove: 101
Member removed.

Enter option: 5
Member ID: 102, Name: Bob Smith, Books borrowed: 3

Enter option: 6
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Member` as described above.  
* **Display Function** – The logic for showing the details of a single member must be placed in a function with the exact prototype:  

  ```c
  void displayMember(const Member *m);
  ```  

* **Single‑responsibility Functions** – Apart from `main`, you may create additional helper functions, but the menu handling (reading the option and dispatching) must remain in `main`.  
* **Dynamic Array Management** – Use `malloc`/`realloc` to manage the array of `Member` objects; do **not** use a fixed‑size array.  
* **Memory Clean‑up** – Before exiting (option 6), free every piece of memory that was allocated, including each member’s `name` string and the array that holds the `Member` structs.  
* **Menu Exit Option** – The menu must include option **6) Exit** (as shown) that cleanly terminates the program.  

Your solution should compile with a standard C compiler (`gcc -std=c11`) and run without warnings when compiled with `-Wall -Wextra -pedantic`.

---

## Problem 18 - openai/gpt-oss-120b - Iteration 53
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small “Student Registry” utility for the university’s computer‑lab. The program must keep a collection of student records in memory while the program runs. Because the number of students is not known ahead of time, you must allocate and release memory dynamically using `malloc` and `free`.  

Each student record consists of:  

* an integer **ID** (positive, unique)  
* a string **name** (maximum 30 characters, no spaces)  
* a floating‑point **GPA** (0.0 – 4.0)  

The utility should allow the user to add new students, remove a student by ID, display a particular student’s details, and list all stored students. The program terminates when the user selects the “Exit” option.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Student` that holds the three fields listed above.  

2. **Dynamic Storage**  
   * The collection of students must be stored in a dynamically allocated array (or linked list) that can grow and shrink as records are added or removed.  
   * Use `malloc`/`realloc` (or `malloc` for each node in a linked list) to obtain memory and `free` to release it when a student is deleted or when the program ends.  

3. **Menu‑driven Interface** (displayed repeatedly until the user exits)  
   1. **Add a student** – Prompt for ID, name, and GPA, allocate space for a new record, and insert it.  
   2. **Remove a student** – Prompt for an ID, locate the matching record, remove it, and free its memory. If the ID does not exist, print an error message.  
   3. **Display a student** – Prompt for an ID and show the student’s information using the required function `displayStudent`. If the ID is not found, print an error message.  
   4. **List all students** – Print the details of every stored student in the order they were added.  
   5. **Exit** – Clean up all allocated memory and terminate the program.  

4. **Input / Output**  
   * All interaction is via `stdin`/`stdout`.  
   * The menu should be clear and numbered (e.g., “1 – Add student”, …, “5 – Exit”).  

5. **Error Handling**  
   * If memory allocation fails, print “Memory allocation failed.” and exit.  
   * Validate that GPA is within the allowed range; otherwise, ask for the value again.  

---

## Example Interaction  

```
--- Student Registry ---
1) Add student
2) Remove student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter ID: 1023
Enter name: Alice
Enter GPA: 3.8
Student added.

--- Student Registry ---
1) Add student
2) Remove student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter ID: 2045
Enter name: Bob
Enter GPA: 2.9
Student added.

--- Student Registry ---
1) Add student
2) Remove student
3) Display student
4) List all students
5) Exit
Choose an option: 4
ID: 1023, Name: Alice, GPA: 3.80
ID: 2045, Name: Bob,   GPA: 2.90

--- Student Registry ---
1) Add student
2) Remove student
3) Display student
4) List all students
5) Exit
Choose an option: 3
Enter ID to display: 2045
ID: 2045, Name: Bob, GPA: 2.90

--- Student Registry ---
1) Add student
2) Remove student
3) Display student
4) List all students
5) Exit
Choose an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Student`.  
* **Display Function** – The logic for showing the details of ONE specific student must reside in a function with the exact prototype:  
  ```c
  void displayStudent(const struct Student *s);
  ```  
* **Menu Exit Option** – The menu must contain a distinct option (number 5 in the example) that terminates the program. Selecting this option must free **all** dynamically allocated memory before exiting.  
* **Memory Management** – Every `malloc`/`realloc` call must have a matching `free` at the appropriate point; no memory leaks are permitted.  
* **Single‑file Implementation** – Apart from `main`, you may define additional helper functions, but the entire solution must be contained in one source file.  

---  

*Deliver a program that satisfies all the above specifications and compiles without warnings using a standard C compiler (e.g., `gcc -Wall -Wextra`).*

---

## Problem 19 - openai/gpt-oss-120b - Iteration 54
# STEP 1: PROBLEM  

## Background  
The Inter‑planetary Shipping Agency (ISA) needs a small command‑line tool to keep track of cargo containers that are loaded onto a shuttle before launch.  
Each container has a **unique ID**, a **weight** (in kilograms), and a short **description** (max 30 characters).  
Because the number of containers varies from mission to mission, the program must allocate memory dynamically at run‑time and release it when containers are removed or when the program ends.

## Requirements  

Write a C program that provides a **menu‑driven** interface for managing the list of cargo containers. The program must:

1. **Create a new list** – ask the user for the initial number of containers `n` (may be zero). Allocate an array of `n` containers using `malloc`.  
2. **Populate the list** – for each of the `n` containers, read:  
   * integer `id` (must be positive)  
   * floating‑point `weight` (kg)  
   * string `description` (no spaces, up to 30 characters)  
3. **Menu options** (repeat until the user chooses to exit):  
   1. **Add a container** – enlarge the array by one element (`realloc`), read its fields, and store it at the end.  
   2. **Remove a container** – ask for an `id`. If a container with that `id` exists, remove it by shifting the later elements left and shrinking the array with `realloc`. If the `id` is not found, display an appropriate message.  
   3. **Display a container** – ask for an `id` and print all its fields using the function `displayContainer`. If the `id` does not exist, print a message.  
   4. **Display all containers** – print the details of every container currently stored.  
   5. **EXIT** – terminate the program, freeing all allocated memory.  

4. All input should be read from `stdin`; all output should be written to `stdout`.  
5. The program must **never leak memory** – every block obtained with `malloc`/`realloc` must eventually be released with `free`.  

## Example Interaction  

```
Enter initial number of containers: 2
Container 1 ID: 101
Container 1 weight (kg): 45.5
Container 1 description: FoodSupplies
Container 2 ID: 202
Container 2 weight (kg): 120.0
Container 2 description: ScientificGear

--- MENU ---
1) Add container
2) Remove container
3) Display container
4) Display all containers
5) EXIT
Choose an option: 4

ID: 101 | Weight: 45.5 kg | Description: FoodSupplies
ID: 202 | Weight: 120.0 kg | Description: ScientificGear

--- MENU ---
1) Add container
2) Remove container
3) Display container
4) Display all containers
5) EXIT
Choose an option: 1
New container ID: 303
Weight (kg): 78.2
Description: HabitatParts
Container added.

--- MENU ---
1) Add container
2) Remove container
3) Display container
4) Display all containers
5) EXIT
Choose an option: 3
Enter ID to display: 303
ID: 303 | Weight: 78.2 kg | Description: HabitatParts

--- MENU ---
1) Add container
2) Remove container
3) Display container
4) Display all containers
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Container` with members `int id; double weight; char description[31];`.  
* **Function Requirement** – The logic for displaying the details of **ONE** specific container must be placed in a function with the exact prototype:  

  ```c
  void displayContainer(const Container *c);
  ```  

* **Menu Requirement** – The program must present a textual menu as shown above and **must include a specific menu option to EXIT the program** (option number 5).  
* **Dynamic Allocation Only** – You may only use `malloc`, `realloc`, and `free` for managing the container array; static or global arrays are not allowed.  
* **Single‑File Implementation** – All code must reside in a single `.c` source file. Apart from `main`, you may define additional helper functions, but the only required extra function is `displayContainer`.  

Design the program so that a student who has just learned `malloc`, `realloc`, and `free` can implement it correctly while respecting the constraints.

---

## Problem 20 - openai/gpt-oss-120b - Iteration 55
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for the campus library. The library needs a program that can keep track of **book reservations** made by students. Each reservation consists of a student’s ID, the title of the book, and the number of days the student intends to keep the book.  
The library staff will run the program interactively: they will add new reservations, list all current reservations, view the details of a particular reservation, and delete reservations when they are fulfilled. Because the number of reservations is not known in advance and can change while the program runs, you must allocate and free memory dynamically.

## Requirements  
Write a C program that implements the following functionality:

1. **Add a reservation** – Prompt the user for the student ID (an integer), the book title (a string of up to 100 characters, may contain spaces), and the number of days (integer). Store the information in a dynamically allocated `struct Reservation` and keep it in a dynamically allocated array (or linked list) that can grow as needed.  

2. **List all reservations** – Display a numbered list of every reservation currently stored, showing the student ID, book title, and days.  

3. **Display a reservation** – Given a reservation number (as shown by the list operation), print the details of that single reservation. This operation **must** be performed by a function named `void displayReservation(const struct Reservation *r);`.  

4. **Delete a reservation** – Remove a reservation identified by its number from the collection, freeing any memory associated with it, and compact the collection so that subsequent numbers remain consecutive.  

5. **Exit** – Terminate the program, freeing all remaining dynamically allocated memory.  

The program should present a simple text menu that repeats until the user chooses to exit.

## Example Input / Output  

```
=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 1

Enter student ID: 12345
Enter book title: Introduction to Algorithms
Enter number of days: 14
Reservation added.

=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 1

Enter student ID: 9876
Enter book title: Clean Code
Enter number of days: 7
Reservation added.

=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 2

Current reservations:
1) Student ID: 12345, Title: Introduction to Algorithms, Days: 14
2) Student ID: 9876,  Title: Clean Code,                Days: 7

=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 3

Enter reservation number to view: 2
--- Reservation Details ---
Student ID: 9876
Book Title: Clean Code
Days: 7

=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 4

Enter reservation number to delete: 1
Reservation deleted.

=== Library Reservation System ===
1) Add reservation
2) List reservations
3) Show reservation details
4) Delete reservation
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct requirement:** The primary data entity must be represented by a `struct Reservation` containing at least the fields `int studentId; char title[101]; int days;`.  

- **Function requirement:** The logic for displaying the details of ONE specific reservation must be placed in a function with the exact prototype  
  ```c
  void displayReservation(const struct Reservation *r);
  ```  

- **Dynamic allocation:** All reservations must be stored using memory obtained with `malloc`/`calloc` (or `realloc` when the collection grows). No static or global arrays of fixed size may be used to hold the reservations.  

- **Memory safety:** Every block of memory obtained with `malloc`/`calloc`/`realloc` must be released exactly once with `free` before the program terminates or when a reservation is deleted.  

- **Menu requirement (mandatory):** The program must present a menu and must include a distinct option to **EXIT** the program (option number 5 in the example). Selecting this option ends the loop and triggers cleanup of all allocated memory.  

- **Standard library only:** You may only use headers from the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are allowed.  

---

## Problem 21 - openai/gpt-oss-120b - Iteration 56
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for the **Museum of Ancient Artifacts**. The museum keeps a catalog of *artifact containers* (e.g., display cases, boxes, or vaults). Each container stores a short description, the year the artifact was discovered, and its estimated value in dollars.  

The museum wants a simple command‑line program that lets a curator add new containers, view the details of a specific container, and finally discard the entire catalog when the program ends. Because the number of containers is not known ahead of time, you must allocate memory dynamically.

---

## Requirements  

Write a C program that fulfills the following specifications:

1. **Data Representation**  
   * Define a `struct Container` that holds:  
     - `char *name` – a dynamically allocated string (max 100 characters).  
     - `int year` – the year the artifact was discovered.  
     - `double value` – estimated monetary value.  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1 – Add a new container**  
     - Prompt the user for the container’s name, year, and value.  
     - Allocate a new `Container` object on the heap and store it in a dynamically‑sized array (the array itself must also be allocated with `malloc`/`realloc`).  
   * **2 – Display a container**  
     - Ask the user for the index (starting at 1) of the container to view.  
     - Call a function `void displayContainer(const Container *c)` that prints the container’s information in a readable format.  
   * **3 – List all containers**  
     - Print a numbered list of all stored containers using `displayContainer` for each entry.  
   * **4 – Exit**  
     - Free *all* memory that was allocated (both the array and each container’s name string) and terminate the program.  

3. **Error handling**  
   * If the user selects an invalid menu option or requests a container index that does not exist, print an appropriate error message and redisplay the menu.  

4. **Program termination**  
   * Before exiting, ensure that there are no memory leaks (all `malloc`/`realloc` calls must have matching `free` calls).  

---

## Example Interaction  

```
=== Museum Container Manager ===
1) Add a new container
2) Display a container
3) List all containers
4) Exit
Choose an option: 1

Enter container name: Golden Mask
Enter discovery year: 1922
Enter estimated value: 2500000

Container added successfully!

=== Museum Container Manager ===
1) Add a new container
2) Display a container
3) List all containers
4) Exit
Choose an option: 1

Enter container name: Ancient Vase
Enter discovery year: 1785
Enter estimated value: 750000

Container added successfully!

=== Museum Container Manager ===
1) Add a new container
2) Display a container
3) List all containers
4) Exit
Choose an option: 3

1) Golden Mask (Year: 1922, Value: $2500000.00)
2) Ancient Vase (Year: 1785, Value: $750000.00)

=== Museum Container Manager ===
1) Add a new container
2) Display a container
3) List all containers
4) Exit
Choose an option: 2

Enter container number to display: 2
Ancient Vase (Year: 1785, Value: $750000.00)

=== Museum Container Manager ===
1) Add a new container
2) Display a container
3) List all containers
4) Exit
Choose an option: 4

Goodbye!
```

---

### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Container` as described above.  
2. **Display Function** – The logic for showing the details of a single container must be placed in a function with the exact prototype:  
   ```c
   void displayContainer(const Container *c);
   ```  
3. **Dynamic Array** – The collection of containers must be stored in a dynamically allocated array that grows with `realloc` each time a new container is added.  
4. **Menu Exit Option** – The menu must include a dedicated option **4 – Exit** (or the exact keyword “Exit”) that terminates the program after freeing all allocated memory.  
5. **Memory Management** – Every allocation performed with `malloc`/`realloc` must have a corresponding `free` before the program ends.  

*Note: The solution may contain additional helper functions, but the two constraints above are mandatory.*

---

## Problem 22 - openai/gpt-oss-120b - Iteration 57
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its computer‑based catalog system. Each book record must be stored dynamically because the number of books changes at run‑time (books are added and removed while the program is running). Your task is to write a small console application that lets a librarian **add**, **remove**, **list**, and **search** for books using dynamic memory allocation (`malloc`, `realloc`, `free`).  

## Requirements  

Your program must provide a text‑based menu with the following options (the exact numbers are mandatory):  

1. **Add a new book** – Prompt the user for the book’s title (a string up to 100 characters), author (up to 100 characters), and the year of publication (integer). Allocate a new `struct Book` on the heap and store it in a dynamic array that grows as needed.  
2. **Delete a book by title** – Prompt for a title, locate the first matching book, remove it from the array, free its memory, and shrink the array accordingly. If the title is not found, display an appropriate message.  
3. **List all books** – Display every stored book in the order they were added. The display of a single book must be performed by a function called `displayBook`.  
4. **Search for a book by year** – Prompt for a publication year and print all books that were published in that year (again using `displayBook`). If none are found, inform the user.  
5. **Exit** – Terminate the program cleanly, freeing all allocated memory.  

Additional functional details:  

- The program must continue to show the menu after completing any operation, until the user selects **Exit**.  
- Input validation is not the focus; you may assume the user enters data of the correct type.  
- The dynamic array of pointers to `struct Book` must be managed manually (i.e., using `malloc`/`realloc`/`free`). Do **not** use C++ containers or library functions that hide the allocation.  

## Example Interaction  

```
=== Library Catalog ===
1. Add a new book
2. Delete a book by title
3. List all books
4. Search for books by year
5. Exit
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Book added.

=== Library Catalog ===
1. Add a new book
2. Delete a book by title
3. List all books
4. Search for books by year
5. Exit
Choose an option: 3

--- Book List ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Year  : 1978
-----------------

=== Library Catalog ===
1. Add a new book
2. Delete a book by title
3. List all books
4. Search for books by year
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Book` containing at least the fields `title`, `author`, and `year`.  
2. **Display Function** – The logic for displaying the details of **one** specific book must reside in a function with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```  

3. **Memory Management** – All memory allocated with `malloc`/`realloc` must be released with `free` before the program terminates. No memory leaks are allowed.  
4. **Menu Exit Option** – The menu must include an explicit option **5. Exit** (or the keyword `EXIT`) that ends the program. Selecting this option must trigger the cleanup of all dynamic memory.  

*Optional hint for students:* you may keep a separate variable `size_t count` for the current number of books and `size_t capacity` for the allocated size of the pointer array. Use `realloc` to grow/shrink the array as books are added or removed.  

---

## Problem 23 - openai/gpt-oss-120b - Iteration 58
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Bookstore** to write a small console‑based inventory manager.  
Each book in the store is described by three pieces of information:

* **ISBN** – a 13‑digit integer (use `unsigned long long`).
* **Title** – a string of up to 100 characters (including spaces).
* **Quantity** – how many copies are currently on the shelf (non‑negative integer).

The store wants a program that can **create**, **display**, **add**, and **remove** books while the program is running. Because the number of books is not known in advance, you must allocate memory dynamically with `malloc`/`realloc` and release it with `free` when it is no longer needed.

## Requirements  

Your program must:

1. **Read the initial number of books** `N` (0 ≤ N ≤ 100) from standard input.  
2. **Allocate** an array of `N` `Book` structures using `malloc`.  
3. **Populate** the array by reading `N` lines, each containing:  
   `ISBN Title Quantity`  
   (the title may contain spaces; you may read the whole line after the ISBN and split it).  
4. **Present a menu** that repeats until the user chooses to exit. The menu must contain the following options (the exact numbers are mandatory):  

   ```
   1) Display all books
   2) Add a new book
   3) Remove a book by ISBN
   4) EXIT
   ```
5. **Option 1 – Display all books**  
   * Calls a function `displayBook(const Book *b)` that prints a single book in the format:  
     `ISBN: <isbn>, Title: "<title>", Quantity: <qty>`  
   * The program should iterate over the current array and invoke `displayBook` for each entry.  

6. **Option 2 – Add a new book**  
   * Prompt the user for the new book’s data (`ISBN Title Quantity`).  
   * Resize the dynamic array to hold one more element using `realloc`.  
   * Store the new book at the end of the array.  

7. **Option 3 – Remove a book by ISBN**  
   * Prompt the user for the ISBN to delete.  
   * Search the array; if the ISBN is found, remove that entry by shifting subsequent elements left, then shrink the array with `realloc`.  
   * If the ISBN does not exist, print `Book not found.`  

8. **Option 4 – EXIT**  
   * Free all dynamically allocated memory and terminate the program.  

9. The program must **never leak memory**: every block obtained with `malloc`/`realloc` must be released exactly once before the program ends.

## Example Input / Output  

```
Enter initial number of books: 2
Enter book 1 (ISBN Title Quantity): 9780131103627 The C Programming Language 5
Enter book 2 (ISBN Title Quantity): 9780201633610 Design Patterns 3

--- Bookstore Menu ---
1) Display all books
2) Add a new book
3) Remove a book by ISBN
4) EXIT
Choose an option: 1

ISBN: 9780131103627, Title: "The C Programming Language", Quantity: 5
ISBN: 9780201633610, Title: "Design Patterns", Quantity: 3

--- Bookstore Menu ---
1) Display all books
2) Add a new book
3) Remove a book by ISBN
4) EXIT
Choose an option: 2
Enter new book (ISBN Title Quantity): 9780262033848 Introduction to Algorithms 4

--- Bookstore Menu ---
1) Display all books
2) Add a new book
3) Remove a book by ISBN
4) EXIT
Choose an option: 3
Enter ISBN to remove: 9780201633610
Book removed.

--- Bookstore Menu ---
1) Display all books
2) Add a new book
3) Remove a book by ISBN
4) EXIT
Choose an option: 1

ISBN: 9780131103627, Title: "The C Programming Language", Quantity: 5
ISBN: 9780262033848, Title: "Introduction to Algorithms", Quantity: 4

--- Bookstore Menu ---
1) Display all books
2) Add a new book
3) Remove a book by ISBN
4) EXIT
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Book` with the three fields described above.  
* **Display Function** – The logic for printing a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const Book *b);
  ```  

* **Menu Implementation** – The menu must be presented exactly as shown, and option **4** must be the explicit command to exit the program.  
* **Dynamic Allocation Only** – All storage for the collection of books must be obtained with `malloc`/`realloc` and released with `free`. No static‑size arrays (e.g., `Book books[100];`) are allowed.  
* **Single‑File Program** – The entire solution should be written in one source file (e.g., `bookstore.c`). Apart from `main`, you may define additional helper functions, but no additional source files.  

---  

Design and implement the program according to the specifications above, demonstrating correct use of dynamic memory allocation, struct handling, and clean resource management.

---

## Problem 24 - openai/gpt-oss-120b - Iteration 59
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Event Planning Committee** to write a small utility that keeps track of “Event Booths” that will be set up at the upcoming university fair.  
Each booth has a name, a contact phone number, and an estimated budget (in dollars).  
The committee does not know in advance how many booths will be registered, so the program must allocate memory dynamically as booths are added and release it when booths are removed.

Your task is to implement a console‑based program that lets the user **add**, **remove**, **list**, and **search** for a booth. All booth records must be stored in dynamically allocated memory using `malloc`/`free`.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Booth` containing:  
     * `char *name` – a dynamically allocated string (maximum length 100 characters).  
     * `char *phone` – a dynamically allocated string (maximum length 20 characters).  
     * `int budget` – the estimated budget.  

2. **Menu‑driven Interface** (the program must present a menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new booth** – Prompt for name, phone, and budget, allocate a new `Booth`, store it, and keep it in a dynamically‑grown array. |
   | 2      | **Remove a booth** – Prompt for the booth name; if found, delete that booth, free all associated memory, and shrink the array accordingly. |
   | 3      | **List all booths** – Display the details of every stored booth in the order they were added. |
   | 4      | **Search for a booth** – Prompt for a name and display the details of the matching booth (if any). |
   | 5      | **EXIT** – Terminate the program after freeing all remaining allocated memory. |

3. **Dynamic Array Management**  
   * The collection of pointers to `Booth` objects must be kept in a dynamically allocated array that grows (`realloc`) when a booth is added and shrinks when a booth is removed.  
   * No fixed‑size limits (other than the maximum string lengths) may be assumed.

4. **Memory Safety**  
   * Every `malloc`/`realloc` must be checked for failure.  
   * All allocated memory (both the array and the strings inside each `Booth`) must be freed before the program exits.

5. **User Interaction**  
   * Input should be read using `scanf`/`fgets` (or equivalent) and must not cause buffer overruns.  
   * After completing an operation, the menu should be shown again until the user selects **EXIT**.

---

## Example  

```
===== Campus Fair Booth Manager =====
1) Add a new booth
2) Remove a booth
3) List all booths
4) Search for a booth
5) EXIT
Enter option: 1

Enter booth name: Tech Club
Enter contact phone: 555-1234
Enter budget: 2500
Booth added successfully!

===== Campus Fair Booth Manager =====
1) Add a new booth
2) Remove a booth
3) List all booths
4) Search for a booth
5) EXIT
Enter option: 3

--- List of Booths ---
1) Name: Tech Club
   Phone: 555-1234
   Budget: $2500
---------------------

===== Campus Fair Booth Manager =====
1) Add a new booth
2) Remove a booth
3) List all booths
4) Search for a booth
5) EXIT
Enter option: 5
Goodbye!
```

---

### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity **must** be represented by a `struct Booth` as described above.  
2. **Display Function** – The logic for displaying the details of **one** specific booth (used by both “List all booths” and “Search for a booth”) **must** be placed in a function with the exact prototype:  

   ```c
   void displayBooth(const struct Booth *b);
   ```

3. **Single‑responsibility Helper** – All memory‑deallocation for a single booth (freeing its strings and the struct itself) **must** be performed inside a function with the prototype:  

   ```c
   void destroyBooth(struct Booth *b);
   ```

4. **Menu Exit Option** – The menu must include option **5** (or the keyword `EXIT`) that terminates the program after freeing all allocated memory.  

5. **No Global Variables** – All data structures must be created and manipulated inside `main` or functions called from `main`; global variables are not allowed.  

---  

*Design the program so that a student who has just learned `malloc`, `free`, `realloc`, and basic `struct` usage can implement it confidently.*

---

## Problem 25 - openai/gpt-oss-120b - Iteration 60
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Book‑Exchange** to write a small console program that keeps track of the books currently offered for trade. The program must store each book’s information dynamically, because the number of books is not known in advance and can change while the program is running.  

Your task is to implement the core data‑management part of the system using **`malloc`** and **`free`** only (no C++ containers, no global static arrays).  

---

## Requirements  

1. **Data entity** – each book is represented by a `struct Book` that contains:  
   * an integer `id` (unique, assigned sequentially starting at 1)  
   * a dynamically allocated string `title`  
   * a dynamically allocated string `author`  
   * an integer `year` (publication year)  

2. **Menu‑driven interface** (the program repeatedly shows a menu until the user chooses to exit). The menu must contain the following options (the numbers are mandatory):  

   | Option | Description |
   |--------|-------------|
   | **1** | **Add a new book** – ask the user for title, author, and year; allocate a new `Book`, store it, and assign it the next free `id`. |
   | **2** | **Remove a book** – ask for the `id`; if a book with that `id` exists, delete it and free all associated memory; otherwise print “Book not found”. |
   | **3** | **Display a book** – ask for the `id`; if found, call the required function `displayBook` (see Constraints) to show its details; otherwise print “Book not found”. |
   | **4** | **List all books** – print the details of every stored book in order of insertion. |
   | **0** | **Exit** – before terminating, free *all* memory that was allocated for books. |

3. The program must keep the collection of books in a **singly‑linked list** (each node points to the next book). New books are appended to the end of the list.  

4. All strings entered by the user must be copied into newly allocated memory (do **not** keep the pointer returned by `scanf`/`gets`).  

5. The program must be robust against invalid input (e.g., non‑numeric menu choice) – you may simply redisplay the menu in such cases.  

---

## Example Interaction  

```
--- Campus Book‑Exchange ---
1) Add a new book
2) Remove a book
3) Display a book
4) List all books
0) Exit
Choice: 1
Enter title : The C Programming Language
Enter author: Kernighan & Ritchie
Enter year  : 1978
Book added with id 1.

1) Add a new book
2) Remove a book
3) Display a book
4) List all books
0) Exit
Choice: 1
Enter title : Introduction to Algorithms
Enter author: Cormen, Leiserson, Rivest, Stein
Enter year  : 2009
Book added with id 2.

1) Add a new book
2) Remove a book
3) Display a book
4) List all books
0) Exit
Choice: 4
ID: 1 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1978
ID: 2 | Title: Introduction to Algorithms | Author: Cormen, Leiserson, Rivest, Stein | Year: 2009

1) Add a new book
2) Remove a book
3) Display a book
4) List all books
0) Exit
Choice: 3
Enter id to display: 2
ID: 2
Title : Introduction to Algorithms
Author: Cormen, Leiserson, Rivest, Stein
Year  : 2009

1) Add a new book
2) Remove a book
3) Display a book
4) List all books
0) Exit
Choice: 0
Good‑bye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct Book` as described above.  
* **Display Function** – The logic that prints the details of **one** specific book must reside in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Memory Management** – Every call to `malloc` (or `calloc`) must have a matching `free`. No memory leaks are permitted.  
* **Menu Exit** – The menu must contain the option **0) Exit** (as shown) and the program must terminate only after the user selects this option.  
* **Single Source File** – The entire solution must be written in one `.c` file; you may define helper functions besides `main`, but the only *required* helper is `displayBook`.  

---  

*Deliverable*: a complete C program that fulfills the specifications above, compiles with `gcc -Wall -Wextra -std=c11`, and runs as illustrated.

---

## Problem 26 - llama-3.3-70b-versatile - Iteration 46
# STEP 1: PROBLEM
You are a curator at a local art museum, tasked with managing the museum's collection of paintings. The museum has a diverse collection, and you need to keep track of each painting's details, including its title, artist, year of creation, and price. To efficiently manage this information, you decide to create a program that utilizes dynamic memory allocation to store and manipulate the collection.

The program should allow users to add new paintings, display all paintings, and search for a specific painting by title. When a painting is added, its details should be stored in memory. The program should also allow users to free the memory allocated to a painting when it is removed from the collection.

### REQUIREMENTS
1. The program must allow users to add new paintings to the collection.
2. The program must display all paintings in the collection.
3. The program must allow users to search for a specific painting by title.
4. The program must free the memory allocated to a painting when it is removed from the collection.

### EXAMPLE
Example Input:
```
Add Painting
Title: Starry Night
Artist: Vincent van Gogh
Year: 1889
Price: 1000000
Add Painting
Title: Mona Lisa
Artist: Leonardo da Vinci
Year: 1503
Price: 800000
Display All Paintings
Search Painting
Title: Starry Night
```
Example Output:
```
Painting Added: Starry Night
Painting Added: Mona Lisa
All Paintings:
- Starry Night by Vincent van Gogh (1889) - $1000000
- Mona Lisa by Leonardo da Vinci (1503) - $800000
Painting Found: Starry Night by Vincent van Gogh (1889) - $1000000
```

### CONSTRAINTS
1. Must use a `struct` to represent a painting, containing fields for title, artist, year, and price.
2. The solution must be implemented with a single function besides `main()`, called `managePaintings()`, which will handle all the program's logic.
3. The program must include a menu with the following options:
   - Add Painting (option 1)
   - Display All Paintings (option 2)
   - Search Painting (option 3)
   - Remove Painting (option 4)
   - EXIT (option 5)
4. The program must free all allocated memory before exiting.

Note: The `managePaintings()` function will be responsible for handling the program's logic, including displaying the menu, processing user input, and managing the collection of paintings.

---

## Problem 27 - llama-3.3-70b-versatile - Iteration 47
# STEP 1: PROBLEM
You are the administrator of a university's library system. The library has a collection of books, and you want to create a program to manage these books. The program should allow users to add, remove, and display information about the books. Since the number of books can vary, you will use dynamic memory allocation to store the book information.

The program should have the following functionality:
1. Add a new book: The program should ask for the book's title, author, and publication year, and then store this information in a dynamically allocated memory location.
2. Remove a book: The program should ask for the title of the book to be removed and then free the memory allocated for that book.
3. Display all books: The program should display the information of all the books currently in the system.
4. Display a specific book: The program should ask for the title of the book and then display its information.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu options.
- If a menu is implemented:
  - Must include a specific menu option to EXIT the program (option 5: "Exit").
  - The menu should be displayed at the start of the program and after each operation.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter publication year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 3
Book 1:
Title: Introduction to CS
Author: John Doe
Year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 4
Enter book title: Introduction to CS
Title: Introduction to CS
Author: John Doe
Year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 5
Exiting the program...
```

---

## Problem 28 - llama-3.3-70b-versatile - Iteration 48
# STEP 1: PROBLEM
You are the administrator of a library management system. The library has a collection of books, and you want to create a program to manage these books. The program should be able to add, remove, and display books. Since the number of books is not fixed, you will use dynamic memory allocation to store the book information.

The program should maintain a list of books, where each book has a title, author, and year of publication. The user should be able to interact with the program through a menu, where they can choose to add a book, remove a book, display all books, or exit the program.

### REQUIREMENTS
1. The program should allocate memory dynamically for each book.
2. The program should have a menu-driven interface with the following options:
   - Add a book
   - Remove a book
   - Display all books
   - Exit the program
3. When adding a book, the program should prompt the user to enter the title, author, and year of publication.
4. When removing a book, the program should prompt the user to enter the title of the book to be removed.
5. When displaying all books, the program should print the title, author, and year of publication of each book.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 1
Enter title: Book1
Enter author: Author1
Enter year: 2020

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 3
Book1 by Author1 (2020)

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 2
Enter title of book to remove: Book1

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 3
No books in the library.

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 4
Exiting the program...
```

### CONSTRAINTS
- Must use a `struct` to represent a book, with members for title, author, and year of publication.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- The program must have a function called `displayBook` to display the details of a single book.
- The program must have a menu option to exit the program, which is option 4. When this option is chosen, the program should free all allocated memory and exit.

---

## Problem 29 - llama-3.3-70b-versatile - Iteration 49
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books using a computer program. The librarian can add, remove, and display books. Each book has a title, author, and publication year. The program should use dynamic memory allocation to store the books.

The librarian wants the program to have the following functionality:
1. Add a new book: The program should ask for the title, author, and publication year of the book and store it in memory.
2. Remove a book: The program should ask for the title of the book and remove it from memory if it exists.
3. Display all books: The program should display the details of all the books in memory.
4. Display a specific book: The program should ask for the title of the book and display its details if it exists.

### EXAMPLE
If the user adds the following books:
- Title: "Book1", Author: "Author1", Year: 2000
- Title: "Book2", Author: "Author2", Year: 2001
The program should display:
- When displaying all books:
  - Book1 by Author1 (2000)
  - Book2 by Author2 (2001)
- When displaying a specific book (e.g., "Book1"):
  - Book1 by Author1 (2000)

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- A menu must be implemented with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- The program must use dynamic memory allocation (`malloc`, `free`) to store the books.

Note: The program should handle memory allocation and deallocation correctly to prevent memory leaks.

---

## Problem 30 - llama-3.3-70b-versatile - Iteration 50
# STEP 1: PROBLEM
In a university setting, students often need to manage their book collections. As a Computer Science student, you have been tasked with creating a program to help with this task. The program should allow students to add, remove, and display books in their collection.

Background:
The university library has decided to create a digital catalog of all the books in the students' collections. The catalog will store information about each book, including the title, author, and publication year.

Requirements:
1. The program should dynamically allocate memory for each book added to the collection.
2. The program should allow students to add a new book to their collection by providing the title, author, and publication year.
3. The program should allow students to remove a book from their collection by providing the title of the book.
4. The program should display all the books in the collection.
5. The program should display the details of a specific book if the title is provided.

Example Input/Output:
```
Add a book:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020

Collection:
1. Introduction to Computer Science by John Smith (2020)

Remove a book:
Title: Introduction to Computer Science

Collection:
(no books)

Display a book:
Title: Introduction to Computer Science

Book not found.

Add a book:
Title: Data Structures
Author: Jane Doe
Publication Year: 2019

Collection:
1. Data Structures by Jane Doe (2019)

Display a book:
Title: Data Structures

Title: Data Structures
Author: Jane Doe
Publication Year: 2019
```

### CONSTRAINTS
- The program must use a `struct` to represent each book.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented with a menu-driven approach.
- The menu must include the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- The program must handle memory allocation and deallocation using `malloc` and `free` respectively.
- The program must check for memory allocation errors and handle them accordingly.

---

## Problem 31 - llama-3.3-70b-versatile - Iteration 51
# STEP 1: PROBLEM
In a simple library management system, books are the primary entities that need to be managed. Each book has a title, author, and publication year. The system should dynamically allocate memory for each book and allow users to add, display, and remove books.

Background: 
The library management system is designed to manage a collection of books. The system should be able to handle a dynamic number of books, and users should be able to interact with the system through a menu-driven interface.

Requirements:
1. The program should dynamically allocate memory for each book using malloc.
2. The program should have a menu-driven interface with the following options:
   - Add a book
   - Display all books
   - Remove a book
   - Exit the program
3. When adding a book, the program should prompt the user to enter the title, author, and publication year.
4. When displaying all books, the program should display the title, author, and publication year of each book.
5. When removing a book, the program should prompt the user to enter the title of the book to be removed and then free the memory allocated for that book.

Example Input/Output:
```
Menu:
1. Add a book
2. Display all books
3. Remove a book
4. Exit the program
Enter your choice: 1
Enter title: Book1
Enter author: Author1
Enter publication year: 2020
Menu:
1. Add a book
2. Display all books
3. Remove a book
4. Exit the program
Enter your choice: 2
Book1 by Author1 (2020)
Menu:
1. Add a book
2. Display all books
3. Remove a book
4. Exit the program
Enter your choice: 3
Enter title of book to remove: Book1
Book removed successfully.
Menu:
1. Add a book
2. Display all books
3. Remove a book
4. Exit the program
Enter your choice: 4
Exiting the program.
```

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
3. The solution must be implemented with a single function besides main() to handle the menu-driven interface, called 'handleMenu'.
4. The program must include a specific menu option to EXIT the program (option 4).

---

## Problem 32 - llama-3.3-70b-versatile - Iteration 52
# STEP 1: PROBLEM
You are the administrator of a library management system. The library has a collection of books, and you want to create a program to manage the catalog. The program should allow users to add, remove, and display books in the catalog.

The program should maintain a dynamic array of books, where each book is represented by its title, author, and publication year. The program should allocate memory for each book dynamically using `malloc` and free the memory when a book is removed from the catalog.

### REQUIREMENTS
1. The program should have a menu-driven interface with the following options:
   - Add a book to the catalog
   - Remove a book from the catalog
   - Display all books in the catalog
   - Display the details of a specific book
   - Exit the program
2. The program should validate user input to ensure that the publication year is a positive integer and the title and author are non-empty strings.
3. The program should handle memory allocation and deallocation correctly to prevent memory leaks.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter publication year: 2020

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 3
Book 1:
Title: Introduction to CS
Author: John Doe
Publication Year: 2020

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 5
Exiting the program...
```

### CONSTRAINTS
- Must use a `struct` to represent a book, with fields for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayCatalog`.
- The logic for adding a book to the catalog must be in a function called `addBook`.
- The solution must include a menu option to exit the program, which is option 5.
- The program must validate user input and handle errors accordingly.
- The program must use `malloc` and `free` to manage memory dynamically.

---

## Problem 33 - llama-3.3-70b-versatile - Iteration 53
# STEP 1: PROBLEM
You are the administrator of a university library system, and you need to manage the collection of books in the library. The library has a vast collection of books, and you want to create a program that can efficiently manage the books. You have decided to use dynamic memory allocation to store the book details.

The program should allow users to add, delete, and display books in the library. Each book has a unique title, author, and publication year.

### REQUIREMENTS
1. The program should dynamically allocate memory to store the book details.
2. The program should have the following menu options:
   - Add a book
   - Delete a book
   - Display all books
   - Display a specific book
   - Exit the program
3. When adding a book, the program should prompt the user to enter the title, author, and publication year of the book.
4. When deleting a book, the program should prompt the user to enter the title of the book to be deleted.
5. When displaying all books, the program should display the details of all the books in the library.
6. When displaying a specific book, the program should prompt the user to enter the title of the book and then display its details.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a book
Title: Computer Science
Author: John Smith
Publication Year: 2020
```
Example Output:
```
Book Details:
Title: Computer Science
Author: John Smith
Publication Year: 2020
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle all the menu options.
- If a menu is implemented, the program must include a specific menu option to EXIT the program. The exit option should be numbered as 5, and it should be labeled as "Exit the program".
- The program should handle memory leaks by freeing the allocated memory when a book is deleted or when the program exits.

Example Menu:
```
1. Add a book
2. Delete a book
3. Display all books
4. Display a specific book
5. Exit the program
```

---

## Problem 34 - llama-3.3-70b-versatile - Iteration 54
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books in the library using a dynamic memory allocation system. The librarian wants to be able to add, remove, and display books in the library.

Background:
The library has a collection of books, and each book has a title, author, and publication year. The librarian wants to be able to dynamically add or remove books from the collection.

Requirements:
1. The program must allow the user to add a new book to the library.
2. The program must allow the user to remove a book from the library by its title.
3. The program must allow the user to display all the books in the library.
4. The program must allow the user to display the details of a specific book.

Example of expected Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 1
Enter title: Book1
Enter author: Author1
Enter publication year: 2020

Enter your choice: 3
Title: Book1, Author: Author1, Publication Year: 2020

Enter your choice: 2
Enter title: Book1

Enter your choice: 3
No books in the library

Enter your choice: 5
Exiting the program...
```

### CONSTRAINTS
- The solution must be implemented using dynamic memory allocation (malloc, free) to store the books.
- Must use a 'struct' to represent a book, with fields for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The logic for displaying the details of a specific book must be in a function called 'displayBook'.
- If a menu is implemented, it must include a specific menu option to EXIT the program by entering '5'.

---

## Problem 35 - llama-3.3-70b-versatile - Iteration 55
# STEP 1: PROBLEM
In a university setting, the management wants to keep track of the books in the library using a dynamic memory allocation system. The system should be able to add, remove, and display books. Each book has a unique ID, title, author, and publication year.

The program should allow the user to interact with the library system through a menu-driven interface. The menu options should include adding a book, removing a book, displaying all books, and exiting the program.

### REQUIREMENTS
1. The program should be able to dynamically allocate memory for each book.
2. The program should be able to add a book with a unique ID, title, author, and publication year.
3. The program should be able to remove a book by its ID.
4. The program should be able to display all books in the system.
5. The program should have a menu-driven interface with options to add, remove, display, and exit.

### EXAMPLE
Input:
```
Choose an option:
1. Add a book
2. Remove a book
3. Display all books
4. Exit
```
User chooses option 1 and enters the book details:
```
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter book publication year: 2020
```
Then, the user chooses option 3 to display all books:
```
Book ID: 1
Book Title: Introduction to CS
Book Author: John Doe
Book Publication Year: 2020
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. The solution must be implemented with a single function besides `main()` to handle the menu options.
3. Must include a specific menu option to EXIT the program (option 4).

Note: The program should handle memory deallocation using `free()` when a book is removed or when the program exits.

---

## Problem 36 - llama-3.3-70b-versatile - Iteration 56
# STEP 1: PROBLEM
You are the administrator of a university's library system, responsible for managing the catalog of books. The library wants to create a simple program to keep track of its books, including their titles, authors, publication years, and whether they are currently borrowed or available. The program should utilize dynamic memory allocation to store the book information.

The program's functionality should include the following requirements:
1. Allow users to add new books to the catalog.
2. Display the details of all books in the catalog.
3. Display the details of a specific book by its title.
4. Remove a book from the catalog by its title.
5. Indicate whether a book is available or borrowed.

### EXAMPLE
If the user adds two books: "Book1" by "Author1" published in 2020, and "Book2" by "Author2" published in 2021, the program should display the details of both books when the user chooses to view all books.

### CONSTRAINTS
- Must use a `struct` to represent a book, containing fields for title, author, publication year, and availability.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The solution must include a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Display a specific book
  4. Remove a book
  5. Borrow a book
  6. Return a book
  7. EXIT (to exit the program)
- The menu should be implemented in the `main` function, and each menu option should call a separate function to perform the corresponding action.

Example Input/Output:
```
Menu:
1. Add a new book
2. Display all books
3. Display a specific book
4. Remove a book
5. Borrow a book
6. Return a book
7. EXIT

Choose an option: 1
Enter book title: Book1
Enter book author: Author1
Enter publication year: 2020

Choose an option: 2
Book1 by Author1 (2020) - Available

Choose an option: 5
Enter book title to borrow: Book1

Choose an option: 2
Book1 by Author1 (2020) - Borrowed
```

---

## Problem 37 - llama-3.3-70b-versatile - Iteration 57
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. To efficiently manage the collection, you need to develop a program that utilizes dynamic memory allocation to store and retrieve book information.

The program should be able to store the title, author, and publication year of each book. The librarian should be able to add new books, remove existing books, and display the details of all books or a specific book.

### REQUIREMENTS
1. The program should allow the user to add a new book by providing its title, author, and publication year.
2. The program should allow the user to remove a book by its title.
3. The program should display the details of all books in the collection.
4. The program should display the details of a specific book by its title.

### EXAMPLE
Input:
```
Add book: "Introduction to CS" by "John Doe" (2020)
Add book: "Data Structures" by "Jane Smith" (2019)
Display all books:
  Introduction to CS by John Doe (2020)
  Data Structures by Jane Smith (2019)
Remove book: "Introduction to CS"
Display all books:
  Data Structures by Jane Smith (2019)
```

### CONSTRAINTS
* Must use a `struct` to represent a book, containing its title, author, and publication year.
* The logic for displaying the details of all books must be in a function called `displayAllBooks`.
* The logic for displaying the details of a specific book must be in a function called `displayBook`.
* The solution must be implemented with a menu-driven interface.
* The menu options must include:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT the program

Note: The EXIT option (option 5) will terminate the program. The program should handle memory deallocation properly when exiting.

---

## Problem 38 - llama-3.3-70b-versatile - Iteration 58
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books it has, including their titles, authors, and publication years. The library's catalog system should be able to dynamically add and remove books as they are acquired or removed from the collection.

The program should be able to perform the following functions:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all the books in the collection.
4. Display the details of a specific book by its title.

### CONSTRAINTS
- The solution must use a `struct` to represent a book, containing fields for title, author, and publication year.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The program must implement a menu-driven interface with the following options:
  - Option 1: Add a new book
  - Option 2: Remove a book
  - Option 3: Display all books
  - Option 4: Display a specific book
  - Option 5: EXIT the program
- The program must use dynamic memory allocation (`malloc`, `free`) to manage the collection of books.

### EXAMPLE
Example Input:
```
1
Book Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
2
Book Title: The Lord of the Rings
Author: J.R.R. Tolkien
Publication Year: 1954
3
```
Example Output:
```
Book Collection:
1. Harry Potter by J.K. Rowling (1997)
2. The Lord of the Rings by J.R.R. Tolkien (1954)
```
Then, if the user chooses to display a specific book:
```
4
Book Title: Harry Potter
```
Example Output:
```
Book Details:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```

---

## Problem 39 - llama-3.3-70b-versatile - Iteration 59
# STEP 1: PROBLEM
In a university setting, the administration wants to manage the details of its faculty members using a dynamic memory allocation system. The system should be able to add, remove, and display faculty member details.

Background: 
The university wants a simple console-based application to manage its faculty members. Each faculty member has a unique ID, name, department, and contact number. The application should be able to dynamically allocate memory for each faculty member and deallocate the memory when a faculty member is removed.

Requirements:
1. The program should be able to add faculty members with their details (ID, name, department, contact number).
2. The program should be able to remove a faculty member by their ID.
3. The program should be able to display all faculty member details.
4. The program should have a menu-driven interface to perform the above operations.

Example:
If the user adds two faculty members with the following details:
- ID: 1, Name: John Doe, Department: CS, Contact Number: 1234567890
- ID: 2, Name: Jane Doe, Department: Math, Contact Number: 9876543210

The program should display the details as follows:
- Faculty Member 1: ID - 1, Name - John Doe, Department - CS, Contact Number - 1234567890
- Faculty Member 2: ID - 2, Name - Jane Doe, Department - Math, Contact Number - 9876543210

### CONSTRAINTS
- Must use a 'struct' to represent the faculty member details.
- Logic for displaying the details of ALL faculty members must be in a function called 'displayAllEntities'.
- The program must have a menu-driven interface with the following options:
  1. Add Faculty Member
  2. Remove Faculty Member
  3. Display All Faculty Members
  4. EXIT
- The program must free the allocated memory when a faculty member is removed or when the program exits.

Note: The program should handle invalid inputs and display appropriate error messages. The menu option to EXIT the program is option 4.

---

## Problem 40 - llama-3.3-70b-versatile - Iteration 60
# STEP 1: PROBLEM
In a small university, the administration wants to manage the information of its students using a dynamic memory allocation system. The system should allow the administrators to add, remove, and display student information. Each student has a unique ID, name, and GPA.

The program should provide a menu-driven interface to perform the following operations:
1. Add a new student: Allocate memory for a new student and store the student's ID, name, and GPA.
2. Remove a student: Free the memory allocated for a specific student based on the student's ID.
3. Display all students: Display the information of all students.
4. Display a specific student: Display the information of a specific student based on the student's ID.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu operations.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1
1 John 3.5
2
3
1 Jane 3.8
4
1
5
```
Example Output:
```
Student ID: 1, Name: John, GPA: 3.5
Student ID: 1, Name: John, GPA: 3.5
Student ID: 1, Name: John, GPA: 3.5
Student ID: 2, Name: Jane, GPA: 3.8
Student ID: 1, Name: John, GPA: 3.5
Student ID: 2, Name: Jane, GPA: 3.8
```
Note: The input and output may vary based on the actual implementation of the program. The above example is a simple representation of the expected input/output. 

Menu Options:
1. Add a new student
2. Remove a student
3. Display all students
4. Display a specific student
5. EXIT the program

---

## Problem 41 - llama-3.3-70b-versatile - Iteration 1
# STEP 1: PROBLEM
You are the administrator of a university's library system, tasked with managing the records of books in the library. The library has a dynamic collection of books, and you need to develop a program to keep track of these books. The program should be able to add new books, remove existing books, and display the details of all books or a specific book.

The program will use dynamic memory allocation to store the book records. Each book record will consist of the book's title, author, and publication year.

## REQUIREMENTS:
1. The program must allow users to add new books to the library's collection.
2. The program must allow users to remove a book from the library's collection by its title.
3. The program must display the details of all books in the library's collection.
4. The program must display the details of a specific book by its title.
5. The program must handle memory allocation and deallocation properly to prevent memory leaks.

## EXAMPLE INPUT/OUTPUT:
Example Input:
```
Add a book: "Introduction to Computer Science" by "John Smith" published in 2020
Add a book: "Data Structures and Algorithms" by "Jane Doe" published in 2019
Display all books:
  Introduction to Computer Science by John Smith (2020)
  Data Structures and Algorithms by Jane Doe (2019)
Remove a book: "Introduction to Computer Science"
Display all books:
  Data Structures and Algorithms by Jane Doe (2019)
```

### CONSTRAINTS:
* The solution must be implemented using a `struct` to represent the book records.
* The logic for displaying the details of all books must be in a function called `displayAllBooks`.
* The logic for displaying the details of a specific book must be in a function called `displayBook`.
* The program must implement a menu-driven interface with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (type '5' to exit the program)
* The program must use dynamic memory allocation (`malloc` and `free`) to manage the book records.

---

## Problem 42 - llama-3.3-70b-versatile - Iteration 2
# STEP 1: PROBLEM
In a small library, the librarian wants to keep track of the books borrowed by students. The librarian needs a program that can dynamically manage the list of borrowed books. The program should be able to add, remove, and display the details of the borrowed books.

The program will use a simple text-based menu to interact with the user. The user can add a new book, remove a book, display all books, or exit the program.

### REQUIREMENTS
1. The program must use dynamic memory allocation (malloc, free) to store the list of borrowed books.
2. The program must be able to add a new book with the following details: book title, author, and borrower's name.
3. The program must be able to remove a book by its title.
4. The program must be able to display all the borrowed books.
5. The program must have a menu-driven interface with the following options:
   - Add a new book
   - Remove a book
   - Display all books
   - Exit the program

### EXAMPLE
Input:
```
1. Add a new book
Book title: Harry Potter
Author: J.K. Rowling
Borrower's name: John Doe

2. Add a new book
Book title: The Lord of the Rings
Author: J.R.R. Tolkien
Borrower's name: Jane Doe

3. Display all books
```
Output:
```
Borrowed Books:
1. Harry Potter by J.K. Rowling (borrowed by John Doe)
2. The Lord of the Rings by J.R.R. Tolkien (borrowed by Jane Doe)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book with the following members: title, author, and borrower's name.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must include a menu option to EXIT the program, which is option 4.
- If the user chooses to remove a book, the program must ask for the book title and then remove the book with the matching title.
- The program must free the allocated memory when a book is removed or when the program exits.

---

## Problem 43 - llama-3.3-70b-versatile - Iteration 3
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. To efficiently manage the collection, you need to create a program that utilizes dynamic memory allocation to store and display information about each book.

The program should store the title, author, publication year, and the number of copies of each book. The program should allow users to add new books, remove existing books, and display information about all books or a specific book.

### REQUIREMENTS
1. The program should dynamically allocate memory to store information about each book.
2. The program should have options to add a new book, remove an existing book, and display information about all books or a specific book.
3. The program should handle memory deallocation when a book is removed to prevent memory leaks.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a new book:
Title: "To Kill a Mockingbird"
Author: "Harper Lee"
Publication Year: 1960
Number of Copies: 5

Display all books:
Title: "To Kill a Mockingbird", Author: "Harper Lee", Publication Year: 1960, Number of Copies: 5

Remove a book:
Title: "To Kill a Mockingbird"

Display all books:
No books available.
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
3. The solution must be implemented with a single function besides `main()` to handle user input and interactions.
4. Must include a menu with the following options:
   - Option 1: Add a new book
   - Option 2: Remove an existing book
   - Option 3: Display all books
   - Option 4: Display a specific book
   - Option 5: EXIT the program
   The program should exit when the user selects Option 5.

Note: The program should handle invalid inputs and memory allocation errors. The `struct` definition and function prototypes should be included in the implementation.

---

## Problem 44 - llama-3.3-70b-versatile - Iteration 4
# STEP 1: PROBLEM
In a small university, the management wants to keep track of the books in its library using a simple program. The program should allow the librarian to add, remove, and display books. Each book has a title, author, and publication year.

The librarian should be able to interact with the program through a menu-driven interface. The menu options should include:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

The program should use dynamic memory allocation to store the book details. The memory should be freed when a book is removed or when the program exits.

### REQUIREMENTS
- The program should allow the user to add a book with title, author, and publication year.
- The program should allow the user to remove a book by its title.
- The program should display all the books in the library.
- The program should display a specific book by its title.
- The program should free the memory allocated for a book when it is removed.
- The program should free all the memory allocated for the books when the program exits.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 3
Book1 by Author1 (2020)
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 2
Enter book title to remove: Book1
Book removed successfully.
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT
Enter your choice: 5
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` to handle the menu options.
- The program must use dynamic memory allocation (`malloc`, `free`) to store the book details.
- The program must have a menu option to EXIT the program (option 5). When this option is chosen, the program should free all the allocated memory and exit.

---

## Problem 45 - llama-3.3-70b-versatile - Iteration 5
# STEP 1: PROBLEM
In a library management system, books are the primary entities that need to be managed. Each book has a title, author, publication year, and a unique identifier (ID). The system should allow users to add, remove, and display books dynamically. The system should utilize dynamic memory allocation to store book information.

Background: 
The library management system is designed to help librarians keep track of the books in their collection. The system should be able to handle a variable number of books, and it should be efficient in terms of memory usage.

Requirements:
1. The program should allow users to add a new book to the system.
2. The program should allow users to remove a book from the system by its ID.
3. The program should allow users to display all the books in the system.
4. The program should allow users to display the details of a specific book by its ID.

Example of expected Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a book
5. Exit

Choose an option: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
Enter book ID: 1

Choose an option: 3
Book 1: Book1 by Author1 (2020)

Choose an option: 4
Enter book ID: 1
Book 1: Book1 by Author1 (2020)

Choose an option: 5
Exiting the program...
```

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
3. The system must free the dynamically allocated memory when a book is removed or when the program exits.
4. If a menu is implemented, it must include a specific menu option to EXIT the program (option 5). The program should exit when the user chooses this option. 

Note: The solution should be implemented in C programming language.

---

## Problem 46 - llama-3.3-70b-versatile - Iteration 6
# STEP 1: PROBLEM
In a simple library management system, books are stored with their titles, authors, and publication years. The system needs to dynamically manage the memory for storing these books as they are added or removed from the library. 

The library management system should be able to perform the following operations:
1. Add a new book to the library.
2. Remove a book from the library by its title.
3. Display all the books in the library.
4. Display the details of a specific book by its title.

The system will start with an empty library, and users will interact with it through a menu-driven interface.

### EXAMPLE INPUT/OUTPUT
Example Input:
- Add a book: "Introduction to CS" by "John Doe" published in 2020.
- Add another book: "Data Structures" by "Jane Smith" published in 2019.
- Display all books.
- Remove a book by title: "Introduction to CS".
- Display all books again.

Example Output:
- After adding the first two books and displaying all:
  - Introduction to CS by John Doe (2020)
  - Data Structures by Jane Smith (2019)
- After removing "Introduction to CS" and displaying all:
  - Data Structures by Jane Smith (2019)

### CONSTRAINTS
- Must use a `struct` to represent a book, containing fields for title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called `displayBook`.
- The program must include a menu with the following options:
  1. Add a book.
  2. Remove a book by title.
  3. Display all books.
  4. Display a book by title.
  5. EXIT the program.
- The menu option to EXIT the program is option 5.

### ADDITIONAL NOTES
- The program should handle memory allocation and deallocation properly using `malloc` and `free`.
- It should also handle cases where a book with the given title does not exist when trying to remove or display it.
- The program should be able to handle a variable number of books, limited only by available memory.

---

## Problem 47 - llama-3.3-70b-versatile - Iteration 7
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books it has, including their titles, authors, and publication years. Since the number of books can vary, you need to use dynamic memory allocation to store the information about each book.

The program should allow users to add, remove, and display books in the library. 

The requirements for the program's functionality are as follows:
1. The program should start with an empty library.
2. The user should be able to add a book to the library by providing the title, author, and publication year.
3. The user should be able to remove a book from the library by providing the title of the book.
4. The user should be able to display all the books in the library.
5. The user should be able to display the details of a specific book by providing the title of the book.

Here's a simple example of expected input/output:
```
Library Management System
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit
Enter your choice: 1
Enter title: Book1
Enter author: Author1
Enter publication year: 2020
Book added successfully.

Library Management System
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit
Enter your choice: 3
Book1 by Author1 (2020)

Library Management System
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit
Enter your choice: 4
Enter title: Book1
Book1 by Author1 (2020)
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for displaying the details of a specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5. 
- The program should handle memory leaks by freeing the allocated memory when a book is removed or when the program exits.

---

## Problem 48 - llama-3.3-70b-versatile - Iteration 8
# STEP 1: PROBLEM
You are the manager of a small library that lends books to its members. The library has a collection of books, and you want to create a program to manage the catalog. The program should allow you to add, remove, and display books. Since the number of books can vary, you will use dynamic memory allocation to store the book information.

The library has the following requirements for the program:
1. The program should be able to store information about each book, including the title, author, and publication year.
2. The program should allow the user to add a new book to the catalog.
3. The program should allow the user to remove a book from the catalog by title.
4. The program should allow the user to display all the books in the catalog.
5. The program should allow the user to display the details of a specific book by title.

### CONSTRAINTS
* Must use a 'struct' to represent a book.
* Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
* The program must have a menu-driven interface with the following options:
    1. Add a book
    2. Remove a book
    3. Display all books
    4. Display a specific book
    5. EXIT (to exit the program)

### EXAMPLE INPUT/OUTPUT
When the user runs the program, they should see a menu with the options listed above. If the user chooses to add a book, they should be prompted to enter the title, author, and publication year of the book. If the user chooses to display all books, the program should display the title, author, and publication year of each book in the catalog.

Example:
```
Library Catalog Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 1
Enter title: Harry Potter
Enter author: J.K. Rowling
Enter publication year: 1997

Library Catalog Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 3
Harry Potter by J.K. Rowling (1997)
```

---

## Problem 49 - llama-3.3-70b-versatile - Iteration 9
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. The library wants to keep track of the books it has, including their titles, authors, and the number of copies available. The library also wants to be able to add new books, remove existing books, and display the details of all the books it has. To achieve this, you will design a program that uses dynamic memory allocation to store the book details.

The program should have the following functionality:
1. Allocate memory for a new book when the user chooses to add a new book.
2. Store the title, author, and number of copies of the new book in the allocated memory.
3. Display the details of all the books when the user chooses to display the books.
4. Remove a book from the list when the user chooses to remove a book.
5. Free the allocated memory when the program exits.

Here is a simple example of the expected input/output:
```
Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit
Enter your choice: 1
Enter the title of the book: "Harry Potter"
Enter the author of the book: "J.K. Rowling"
Enter the number of copies: 5
Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit
Enter your choice: 2
Title: "Harry Potter", Author: "J.K. Rowling", Copies: 5
Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit
Enter your choice: 4
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- The logic for displaying the details of all the books must be in a function called `displayBooks`.
- The program must include a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Remove a book
  4. Exit
- The program must exit when the user chooses option 4 (Exit). 
- The program must free all the allocated memory before exiting.

---

## Problem 50 - llama-3.3-70b-versatile - Iteration 10
# STEP 1: PROBLEM
In a simple library management system, books are the primary entities that need to be tracked. The system should allow users to add books, display all books, and remove books. Since the number of books is not fixed, dynamic memory allocation will be used to manage the collection of books.

**Background and Context:**
A small library wants to implement a basic management system for its collection of books. The system should allow library staff to add new books, view all existing books, and remove books that are no longer in the collection.

**Requirements:**
1. The program should allow users to add a new book by providing its title, author, and publication year.
2. The program should display all the books in the collection, showing their title, author, and publication year.
3. The program should allow users to remove a book by its title.
4. The program should handle memory allocation and deallocation properly to avoid memory leaks.

**Example Input/Output:**
```
Welcome to the Library Management System!
1. Add a book
2. Display all books
3. Remove a book
4. Exit

Choose an option: 1
Enter book title: Introduction to Algorithms
Enter book author: Thomas H. Cormen
Enter publication year: 2009

Choose an option: 2
Book 1:
Title: Introduction to Algorithms
Author: Thomas H. Cormen
Year: 2009

Choose an option: 3
Enter title of book to remove: Introduction to Algorithms
Book removed successfully!

Choose an option: 4
Exiting the program...
```

### CONSTRAINTS
- The solution must use a `struct` to represent a book, which should include fields for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The program must include a menu with the options to add a book, display all books, remove a book, and exit the program. The exit option should be clearly labeled as "4. Exit" or by entering "exit".
- The menu should be implemented in a loop that continues until the user chooses the exit option.
- Memory must be allocated and deallocated dynamically using `malloc` and `free` to manage the collection of books.

---

## Problem 51 - llama-3.3-70b-versatile - Iteration 11
# STEP 1: PROBLEM
You are the curator of a museum, and you want to create a simple system to manage the artifacts in your collection. Each artifact has a unique identifier, name, and description. You need to write a program that allows you to add, remove, and display artifacts.

The program should have the following functionality:
1. Add an artifact: dynamically allocate memory for a new artifact, and prompt the user to input the artifact's unique identifier, name, and description.
2. Remove an artifact: free the memory allocated for a specific artifact based on its unique identifier.
3. Display all artifacts: print out the details of all artifacts in the collection.
4. Display a specific artifact: print out the details of a specific artifact based on its unique identifier.

Here's a simple example of expected input/output:
```
Add an artifact:
Enter unique identifier: 1
Enter name: Ancient Vase
Enter description: A vase from ancient civilization
Artifacts:
1 - Ancient Vase - A vase from ancient civilization

Remove an artifact:
Enter unique identifier: 1
Artifacts:
(no artifacts)

Add an artifact:
Enter unique identifier: 2
Enter name: Painting
Enter description: A beautiful painting
Add an artifact:
Enter unique identifier: 3
Enter name: Sculpture
Enter description: A sculpture from the Renaissance
Artifacts:
2 - Painting - A beautiful painting
3 - Sculpture - A sculpture from the Renaissance

Display a specific artifact:
Enter unique identifier: 2
2 - Painting - A beautiful painting
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent an artifact, with members for the unique identifier, name, and description.
- The program must have a menu with the following options:
  1. Add an artifact
  2. Remove an artifact
  3. Display all artifacts
  4. Display a specific artifact
  5. EXIT
- The logic for displaying the details of all artifacts must be in a function called `displayAllArtifacts`.
- The logic for displaying the details of a specific artifact must be in a function called `displaySpecificArtifact`.
- The program must use dynamic memory allocation (`malloc`, `free`) to manage the artifacts.
- The user can exit the program by selecting the "EXIT" option (option 5).

---

## Problem 52 - llama-3.3-70b-versatile - Iteration 12
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a simple system to manage the books in your library. The system should be able to store information about each book, including its title, author, and publication year. Since the number of books in the library can change over time, you want to use dynamic memory allocation to store the book information.

The system should have the following functionality:
1. Add a new book to the library.
2. Display all the books in the library.
3. Search for a book by its title and display its details.
4. Remove a book from the library.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book, with fields for title, author, and publication year.
- The logic for displaying the details of a book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu and user input.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a new book
Enter book title: Introduction to CS
Enter book author: John Doe
Enter book publication year: 2020

2. Display all books
Book 1:
Title: Introduction to CS
Author: John Doe
Year: 2020

3. Search for a book
Enter book title to search: Introduction to CS
Book found:
Title: Introduction to CS
Author: John Doe
Year: 2020
```
Note: The input/output can vary based on the actual implementation, but it should be similar to the example provided. 

To exit the program, the user should select option 5 from the menu.

---

## Problem 53 - llama-3.3-70b-versatile - Iteration 13
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. Each book has a unique title, author, and publication year. The library wants to implement a simple system to keep track of its books using dynamic memory allocation. Your task is to design a program that allows the librarian to add, remove, and display books in the library's collection.

### REQUIREMENTS
1. The program should start with an empty collection of books.
2. The program should allow the librarian to add a new book to the collection by providing the title, author, and publication year.
3. The program should allow the librarian to remove a book from the collection by providing the title of the book to be removed.
4. The program should allow the librarian to display all books in the collection.
5. The program should allow the librarian to display the details of a specific book by providing the title of the book.

### EXAMPLE
Input:
```
Add a book: Title - "Introduction to CS", Author - "John Doe", Year - 2020
Add a book: Title - "Data Structures", Author - "Jane Smith", Year - 2019
Display all books:
Book 1: Title - "Introduction to CS", Author - "John Doe", Year - 2020
Book 2: Title - "Data Structures", Author - "Jane Smith", Year - 2019
Remove a book: Title - "Introduction to CS"
Display all books:
Book 1: Title - "Data Structures", Author - "Jane Smith", Year - 2019
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- The program must have a menu-driven interface with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks. The `EXIT` option should be used to terminate the program.

---

## Problem 54 - llama-3.3-70b-versatile - Iteration 14
# STEP 1: PROBLEM
In a library management system, books are the primary entities that need to be tracked. The system should allow users to add, remove, and display book details dynamically. The library wants to implement a simple console-based application to manage their book inventory.

Background:
The library has a collection of books with unique ISBN numbers, titles, authors, and publication years. The library staff needs to manage this collection efficiently, and the system should be able to handle a variable number of books.

Requirements:
1. The program should allow users to add a new book to the collection.
2. The program should allow users to remove a book from the collection by its ISBN number.
3. The program should display all the books in the collection.
4. The program should have a menu-driven interface to interact with the user.

Example Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Exit

Choose an option: 1
Enter ISBN: 1234567890
Enter title: Book Title
Enter author: Book Author
Enter publication year: 2020

Choose an option: 3
ISBN: 1234567890, Title: Book Title, Author: Book Author, Publication Year: 2020

Choose an option: 2
Enter ISBN to remove: 1234567890

Choose an option: 3
No books in the collection.

Choose an option: 4
Exiting the program...
```

### CONSTRAINTS
- Must use a 'struct' to represent a book entity.
- The solution must be implemented with a single function besides main(), which will handle the menu and all operations.
- The menu option to EXIT the program is option 4.

---

## Problem 55 - llama-3.3-70b-versatile - Iteration 15
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books using a computer program. The program should allow the librarian to add, remove, and display books. Each book has a title, author, and publication year.

The program's functionality should include the following:
1. Dynamically allocate memory for each book when it is added.
2. Store the details of each book in a struct.
3. Provide a menu-driven interface to add, remove, and display books.
4. When displaying books, the program should show the title, author, and publication year of each book.

Here's a simple example of expected input/output:
```
Menu:
1. Add book
2. Remove book
3. Display books
4. Exit

Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020

Menu:
1. Add book
2. Remove book
3. Display books
4. Exit

Enter your choice: 3
Book1 by Author1 (2020)

Menu:
1. Add book
2. Remove book
3. Display books
4. Exit

Enter your choice: 4
```

### CONSTRAINTS
- The solution must be implemented using a struct to represent a book.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The program must use dynamic memory allocation (malloc, free) to manage the memory for the books.
- The menu must include a specific option to EXIT the program (option 4).
- The program must free the allocated memory when a book is removed or when the program exits. 

### ADDITIONAL NOTES
- The program should handle invalid menu choices by displaying an error message and prompting the user to enter a valid choice.
- The program should handle memory allocation failures by displaying an error message and exiting the program.

---

## Problem 56 - openai/gpt-oss-120b - Iteration 1
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “student‑registry” utility for the campus computer lab. The lab administrator wants a command‑line program that can store an arbitrary number of student records while the program is running. Because the number of students is not known beforehand, you must allocate memory dynamically using `malloc` (or `calloc`) and release it with `free` when a record is removed or when the program terminates.

Each student record consists of:
* a **student ID** (positive integer),
* a **full name** (string, maximum 100 characters, may contain spaces),
* a **GPA** (floating‑point number between 0.0 and 4.0).

The administrator will interact with the program through a simple text menu.

## Requirements  
Write a C program that fulfills the following functionality:

1. **Menu Loop** – Continuously display a menu and process the user’s choice until the user selects the *Exit* option.  
2. **Add a Student** – Prompt for ID, name, and GPA, allocate a new `struct` to hold the data, and store the pointer in a dynamically‑grown array (you may re‑allocate the array as needed).  
3. **Delete a Student** – Prompt for a student ID, locate the matching record, free its memory, and remove the pointer from the array, shifting remaining pointers to keep the array compact. If the ID does not exist, print an informative message.  
4. **Display a Student** – Prompt for a student ID and display the details of that student using a helper function `displayStudent`. If the ID is not found, print an appropriate message.  
5. **Display All Students** – List every stored student in the order they were added, one per line.  
6. **Exit** – Before terminating, free **all** allocated memory (both the individual student structs and the array that holds their pointers).  

The program must **not** leak memory; every allocation performed with `malloc`/`calloc` must eventually be released with `free`.

## Example Interaction  

```
=== Student Registry Menu ===
1. Add student
2. Delete student
3. Display a student
4. Display all students
5. Exit
Enter choice: 1
Enter ID: 1024
Enter name: Alice Johnson
Enter GPA: 3.85
Student added.

Enter choice: 1
Enter ID: 2048
Enter name: Bob Lee
Enter GPA: 2.97
Student added.

Enter choice: 4
ID: 1024, Name: Alice Johnson, GPA: 3.85
ID: 2048, Name: Bob Lee, GPA: 2.97

Enter choice: 3
Enter ID to display: 1024
ID: 1024, Name: Alice Johnson, GPA: 3.85

Enter choice: 2
Enter ID to delete: 2048
Student removed.

Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct` named `Student` containing the three fields described above.  
* **Display Function** – The logic for showing the details of a single student must be placed in a function with the exact prototype:  
  ```c
  void displayStudent(const Student *s);
  ```  
* **Menu Implementation** – The menu must include an explicit option to **EXIT** the program; in the example this is option `5`. The program must terminate only after the user selects this option.  
* **Single‑File Solution** – All code (including `displayStudent` and any helper functions) must reside in one source file.  
* **Dynamic Allocation Only** – You may **not** use static or global arrays to store the student records; the collection must be built entirely with dynamic memory (`malloc`, `realloc`, `free`).  

Your solution will be evaluated for correct use of `malloc`/`free`, proper handling of the menu loop, and adherence to the constraints above.

---

## Problem 57 - openai/gpt-oss-120b - Iteration 2
# STEP 1: PROBLEM  

## Background  
You have been hired by the **City Library** to write a small utility that keeps track of **book reservations** made by patrons. Each reservation records the patron’s name, the title of the book, and the number of days the patron intends to keep the book. The library wants a command‑line program that can add new reservations, list all current reservations, and delete a reservation when it is fulfilled. Because the number of reservations is not known in advance, the program must allocate memory dynamically.

## Requirements  

Your program must:

1. **Define a `struct Reservation`** that contains  
   * `char *patronName;` – a dynamically allocated string for the patron’s name.  
   * `char *bookTitle;` – a dynamically allocated string for the book title.  
   * `int days;` – number of days the patron will keep the book.  

2. **Maintain a dynamic array** (or linked list) of `Reservation` objects. The array should grow or shrink using `malloc`, `realloc`, and `free` as reservations are added or removed.

3. **Present a text menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   ```
   1. Add a new reservation
   2. List all reservations
   3. Cancel a reservation
   4. EXIT
   ```

4. **Option 1 – Add a new reservation**  
   * Prompt the user for the patron’s name, the book title, and the number of days.  
   * Allocate memory for the strings and store the data in a new `Reservation`.  
   * Append the new reservation to the dynamic collection.

5. **Option 2 – List all reservations**  
   * For each reservation, display its index (starting at 1) and all fields.  
   * The logic that prints a **single** reservation must be placed in a function named `void displayReservation(const Reservation *r, int index);`.

6. **Option 3 – Cancel a reservation**  
   * Prompt the user for the index of the reservation to cancel (as shown by option 2).  
   * Remove that reservation from the collection, freeing all memory associated with it, and shift the remaining entries so that indices stay contiguous.

7. **Option 4 – EXIT**  
   * Free **all** memory that is still allocated and terminate the program.

8. The program must **not leak memory**; every allocation performed with `malloc`/`realloc` must eventually be released with `free`.

## Example Interaction  

```
--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 1

Enter patron name: Alice
Enter book title:  The C Programming Language
Enter number of days: 14
Reservation added.

--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 1

Enter patron name: Bob
Enter book title:  Introduction to Algorithms
Enter number of days: 7
Reservation added.

--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 2

1) Patron: Alice
   Book: The C Programming Language
   Days: 14
2) Patron: Bob
   Book: Introduction to Algorithms
   Days: 7

--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 3

Enter reservation number to cancel: 1
Reservation cancelled.

--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 2

1) Patron: Bob
   Book: Introduction to Algorithms
   Days: 7

--- Library Reservation System ---
1. Add a new reservation
2. List all reservations
3. Cancel a reservation
4. EXIT
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct Reservation` as described above.  
* **Display Function** – The code that prints the details of a single reservation must be encapsulated in a function named `displayReservation`. No other function may perform that printing.  
* **Menu Exit** – The menu must contain the explicit option `4. EXIT` (or the keyword `EXIT`) that terminates the program.  
* **Memory Management** – Use only the C standard library functions `malloc`, `realloc`, and `free` for dynamic memory handling. Do **not** use global variables to store the collection; it should be managed within `main` (or functions called from `main`).  

Your solution should compile with a standard C compiler (e.g., `gcc -Wall -Wextra -std=c11`).

---

## Problem 58 - openai/gpt-oss-120b - Iteration 3
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Logistics**, a small startup that manages a fleet of delivery drones.  
Each drone can carry a variable number of packages on a single trip. The company wants a simple command‑line tool that allows an operator to **create**, **inspect**, and **remove** drones while the program is running. Because the number of drones and the number of packages per drone are not known ahead of time, the program must allocate memory dynamically using `malloc` (or `calloc`) and release it with `free` when a drone is deleted.

## Requirements  

Write a C program that supports the following operations through a text menu:

1. **Add a new drone**  
   * Prompt the user for the drone’s **ID** (an integer) and the **number of packages** it will carry (a positive integer).  
   * Dynamically allocate a `struct Drone` to store the ID, the package count, and a dynamically allocated array of `float` values representing the weight (in kilograms) of each package.  
   * Prompt the user to enter the weight for each package and store them in the allocated array.  
   * Store a pointer to the newly created `Drone` in a dynamically resized list of drones.

2. **Display a drone’s details**  
   * Prompt for a drone ID.  
   * Locate the corresponding drone in the list.  
   * Call a function `void displayDrone(const struct Drone *d)` that prints the drone’s ID, the number of packages, and the weight of each package (to two decimal places).  

3. **Remove a drone**  
   * Prompt for a drone ID.  
   * Locate the drone, free the memory used for its package‑weight array, free the `Drone` structure itself, and remove its pointer from the list (shifting later entries forward).  

4. **List all drones**  
   * Print a compact table showing every stored drone’s ID and package count.

5. **Exit**  
   * Terminate the program after freeing **all** remaining dynamically allocated memory.

The menu must be displayed after each completed operation until the user chooses the exit option.

## Example Interaction  

```
=== Drone Management System ===
1) Add a new drone
2) Display drone details
3) Remove a drone
4) List all drones
5) EXIT
Select an option: 1

Enter Drone ID: 101
Enter number of packages: 3
Enter weight of package 1 (kg): 2.5
Enter weight of package 2 (kg): 1.75
Enter weight of package 3 (kg): 4.0
Drone added successfully.

=== Drone Management System ===
1) Add a new drone
2) Display drone details
3) Remove a drone
4) List all drones
5) EXIT
Select an option: 1

Enter Drone ID: 202
Enter number of packages: 2
Enter weight of package 1 (kg): 3.3
Enter weight of package 2 (kg): 2.2
Drone added successfully.

=== Drone Management System ===
1) Add a new drone
2) Display drone details
3) Remove a drone
4) List all drones
5) EXIT
Select an option: 4

ID   Packages
101        3
202        2

=== Drone Management System ===
1) Add a new drone
2) Display drone details
3) Remove a drone
4) List all drones
5) EXIT
Select an option: 2

Enter Drone ID to display: 101
--- Drone 101 ---
Packages: 3
Package 1: 2.50 kg
Package 2: 1.75 kg
Package 3: 4.00 kg

=== Drone Management System ===
1) Add a new drone
2) Display drone details
3) Remove a drone
4) List all drones
5) EXIT
Select an option: 5
Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct Drone` containing at least the following members:  
  ```c
  struct Drone {
      int id;
      int packageCount;
      float *packageWeights;   // dynamically allocated array
  };
  ```
* **Display Function** – The logic for showing the details of a single drone **must** be placed in a function named exactly `void displayDrone(const struct Drone *d);`.  
* **Dynamic List Management** – The collection of drone pointers must be stored in a dynamically allocated array that grows (or shrinks) with `realloc` as drones are added or removed.  
* **Memory Discipline** – Every block of memory obtained with `malloc`/`calloc`/`realloc` must be released exactly once with `free`. No memory leaks are permitted (the program will be tested with tools such as Valgrind).  
* **Menu Exit Option** – The menu must contain an option labeled **5) EXIT** (or the word `EXIT`) that terminates the program after all allocated memory has been freed.  

*Optional (for extra credit)*: implement input validation so that non‑numeric or out‑of‑range entries do not crash the program.  

---  

Write clean, well‑commented code that follows these constraints and demonstrates correct use of dynamic memory allocation in C.

---

## Problem 59 - openai/gpt-oss-120b - Iteration 4
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Tracker**, a startup that builds simple command‑line tools for field biologists.  
Biologists collect data about **tree specimens** during a survey: each tree has an ID number, a species name (max 30 characters), and a measured trunk diameter (in centimeters).  
Because the number of trees encountered is not known ahead of time, the program must allocate memory dynamically as the survey progresses. When the survey ends, all allocated memory must be released.

## Program Requirements  
Write a C program that allows the user to manage a collection of tree records. The program must support the following operations through a text‑based menu:

1. **Add a new tree** – Prompt the user for the tree’s ID (integer), species name (string, up to 30 characters, no spaces), and trunk diameter (floating‑point). Allocate a new `struct Tree` on the heap, store the data, and add the pointer to a dynamic array that grows as needed.  
2. **List all trees** – Print a table showing the ID, species, and diameter of every tree currently stored, in the order they were added.  
3. **Find a tree by ID** – Prompt for an integer ID, search the collection, and display the matching tree’s details. If no tree with that ID exists, print “Tree not found.”  
4. **Delete a tree by ID** – Prompt for an integer ID, locate the tree, free its memory, and remove its pointer from the dynamic array, shifting later elements forward to keep the array compact. If the ID is not present, print “Tree not found.”  
5. **Exit** – Release **all** remaining dynamically allocated memory and terminate the program.

The menu must be displayed after each completed operation until the user selects the Exit option.

## Example Interaction  

```
=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 1
Enter tree ID: 101
Enter species (max 30 chars, no spaces): Oak
Enter trunk diameter (cm): 45.2
Tree added.

=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 1
Enter tree ID: 202
Enter species (max 30 chars, no spaces): Pine
Enter trunk diameter (cm): 38.7
Tree added.

=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 2
ID   Species   Diameter(cm)
101  Oak       45.20
202  Pine      38.70

=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 3
Enter tree ID to find: 202
ID: 202, Species: Pine, Diameter: 38.70 cm

=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 4
Enter tree ID to delete: 101
Tree with ID 101 deleted.

=== Eco‑Tracker Menu ===
1) Add a new tree
2) List all trees
3) Find a tree by ID
4) Delete a tree by ID
5) EXIT
Select an option: 5
All memory freed. Goodbye!
```

## ### CONSTRAINTS  

1. **Structure Requirement** – The primary data entity must be represented by a `struct` named `Tree` containing at least the following members:  
   ```c
   typedef struct {
       int id;
       char species[31];   // space for 30 chars + terminating null
       float diameter;
   } Tree;
   ```
2. **Dynamic Array Management** – The collection of pointers to `Tree` objects must be stored in a dynamically allocated array (e.g., `Tree **forest`). The array must grow (using `realloc`) when a new tree is added and shrink (optional) when a tree is deleted.  
3. **Function Decomposition** –  
   * The logic that displays the details of **one specific tree** (used by both “Find” and “Delete” operations) must be placed in a function with the exact prototype:  
     ```c
     void displayTree(const Tree *t);
     ```  
   * All other menu‑handling code may be placed in `main`, but you may create additional helper functions if you wish.  
4. **Memory Discipline** – Every call to `malloc`/`calloc`/`realloc` must have a matching `free`. No memory leaks are permitted (you can verify with tools such as Valgrind).  
5. **Menu Exit Option** – The menu must include a clearly labeled option to exit the program; in the example it is option **5** labeled `EXIT`. Selecting this option must trigger the final cleanup of all allocated memory before the program terminates.  

*Feel free to add minor input validation (e.g., ensure the ID entered is positive), but the core of the assignment is to demonstrate correct use of `malloc`, `realloc`, `free`, and struct handling.*

---

## Problem 60 - openai/gpt-oss-120b - Iteration 5
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Club maintains a small inventory of **project kits** (each kit contains a micro‑controller, a set of sensors, and a brief description). The inventory changes frequently: kits are added when new equipment arrives, and removed when a kit is loaned out permanently.  

Your task is to write a **menu‑driven C program** that lets the user manage this inventory using dynamic memory allocation (`malloc`, `free`). Each kit must be stored in a dynamically allocated structure, and the list of kits must grow or shrink as kits are added or removed.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Kit` that contains:  
     * `int id` – a unique identifier (positive integer).  
     * `char *name` – a dynamically allocated string for the kit’s name (max 50 characters).  
     * `char *description` – a dynamically allocated string for a short description (max 200 characters).  

2. **Menu** (displayed repeatedly until the user chooses to exit)  
   1. **Add a new kit** – Prompt for `id`, `name`, and `description`. Allocate memory for a new `Kit` and store it in the inventory.  
   2. **Remove a kit** – Prompt for the `id` of the kit to delete. Locate the kit, free all memory associated with it, and remove it from the inventory list.  
   3. **Display a kit** – Prompt for the `id` and call a function `displayKit` (see Constraint) to print all fields of the requested kit.  
   4. **List all kits** – Print the `id` and `name` of every kit currently stored.  
   5. **Exit** – Terminate the program, freeing any remaining allocated memory.  

3. **Dynamic storage**  
   * The inventory must be kept in a **dynamically allocated array** (or linked list) that can expand when a new kit is added and shrink when a kit is removed.  
   * Use `malloc`/`realloc` (or `malloc`/`free` for a linked list) appropriately; never allocate a fixed‑size array of kits.  

4. **Error handling**  
   * If the user tries to add a kit with an `id` that already exists, display an error and do not insert.  
   * If the user requests to remove or display a non‑existent `id`, display an appropriate message.  

5. **Program termination**  
   * Before exiting, ensure **all** dynamically allocated memory (kits, their name/description strings, and the container) is freed.  

---

## Example Interaction  

```
=== Kit Inventory Menu ===
1. Add a new kit
2. Remove a kit
3. Display a kit
4. List all kits
5. Exit
Enter choice: 1

Enter kit id: 101
Enter kit name: SensorPack
Enter kit description: Arduino + temperature & humidity sensors
Kit added successfully.

=== Kit Inventory Menu ===
1. Add a new kit
2. Remove a kit
3. Display a kit
4. List all kits
5. Exit
Enter choice: 4

Current kits:
ID: 101   Name: SensorPack

=== Kit Inventory Menu ===
1. Add a new kit
2. Remove a kit
3. Display a kit
4. List all kits
5. Exit
Enter choice: 3

Enter kit id to display: 101
--- Kit Details ---
ID          : 101
Name        : SensorPack
Description : Arduino + temperature & humidity sensors

=== Kit Inventory Menu ===
1. Add a new kit
2. Remove a kit
3. Display a kit
4. List all kits
5. Exit
Enter choice: 5

Goodbye!
```

---

### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be represented by a `struct Kit`.  
* **Display function** – The logic for printing the details of **one** specific kit must reside in a function with the exact prototype:  
  ```c
  void displayKit(const struct Kit *k);
  ```  
* **Single‑responsibility functions** – Apart from `main`, you may create helper functions (e.g., for adding, removing, listing), but the *only* function that directly prints a kit’s full information is `displayKit`.  
* **Menu exit option** – The menu must contain an explicit option **5. Exit** (or the keyword `EXIT`) that terminates the program.  

*Optional but recommended*: Use `typedef` for the struct if you prefer, but the `displayKit` signature must still accept a pointer to the original struct type.  

---

## Problem 61 - openai/gpt-oss-120b - Iteration 6
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for a local community library. The library wants a simple command‑line program that lets the staff keep a **dynamic list** of books currently on the shelves. Because the number of books can change at any time, the program must allocate and release memory at runtime using `malloc` and `free`.  

Each book is described by three pieces of information:  

* **Title** – a string (maximum 100 characters)  
* **Author** – a string (maximum 100 characters)  
* **Number of pages** – an integer  

The staff will interact with the program through a text menu.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct` named `Book` that holds the three fields listed above.  

2. **Menu‑driven Interface** (displayed repeatedly until the user chooses to exit)  
   * **1 – Add a new book**  
     * Prompt the user for title, author, and page count.  
     * Allocate memory for a new `Book` instance with `malloc`.  
     * Store the pointer in a dynamically‑grown array (you may re‑allocate the array as needed).  
   * **2 – List all books**  
     * Print a numbered list of every stored book showing title, author, and page count.  
   * **3 – Show details of a specific book**  
     * Ask for the book number (as shown in the list).  
     * Call a function `void displayBook(const Book *b)` that prints the selected book’s information.  
   * **4 – Remove a book**  
     * Ask for the book number to delete.  
     * Free the memory occupied by that `Book`.  
     * Shift the remaining pointers in the array so that the list stays contiguous.  
   * **5 – EXIT**  
     * Free **all** remaining allocated memory and terminate the program.  

3. **Error handling**  
   * If the user selects an invalid menu option or a non‑existent book number, print an informative message and redisplay the menu.  

4. **Memory management**  
   * Every `malloc` must have a matching `free`. No memory leaks are allowed.  

---

## Example Interaction  

```
=== Library Book Manager ===
1) Add a new book
2) List all books
3) Show details of a specific book
4) Remove a book
5) EXIT
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter number of pages: 274
Book added successfully!

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Show details of a specific book
4) Remove a book
5) EXIT
Choose an option: 2

Current books:
1) The C Programming Language by Kernighan & Ritchie (274 pages)

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Show details of a specific book
4) Remove a book
5) EXIT
Choose an option: 3

Enter book number to view: 1
--- Book Details ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Pages : 274

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Show details of a specific book
4) Remove a book
5) EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct` named `Book`.  
* **Display Function** – The logic for showing the details of ONE specific book must be placed in a function with the exact prototype:  
  ```c
  void displayBook(const Book *b);
  ```  
* **Menu Exit** – The menu must contain an explicit option **5 – EXIT** (or the keyword “EXIT”) that terminates the program after freeing all allocated memory.  
* **Memory Discipline** – No memory allocated with `malloc` may be left unreleased at program termination.  

Feel free to add any helper functions you deem necessary, but the two constraints above are mandatory.

---

## Problem 62 - openai/gpt-oss-120b - Iteration 7
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “personal library” manager for a small reading club. The club members will enter information about the books they own, look up a book by its ISBN, list all stored books, and remove a book when it is donated away. Because the number of books is not known in advance, the program must allocate memory dynamically as books are added and release it when they are removed or when the program terminates.

## Requirements  
Write a C program that implements the following functionality:

1. **Data representation**  
   * Define a `struct Book` that stores:  
     - `char title[101]` – the title (max 100 characters, null‑terminated)  
     - `char author[51]` – the author (max 50 characters)  
     - `unsigned long isbn` – a 13‑digit ISBN (store as an unsigned long)  
     - `int year` – year of publication  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   1. **Add a new book** – Prompt the user for the book’s fields, allocate a new `struct Book` with `malloc`, store the data, and keep a pointer to it in a dynamically‑grown array (or linked list).  
   2. **List all books** – Print the details of every stored book in the order they were added.  
   3. **Find a book by ISBN** – Ask for an ISBN, search the collection, and if found call a function `displayBook` (see constraints) to show the book’s details; otherwise print “Book not found.”  
   4. **Remove a book by ISBN** – Ask for an ISBN, locate the matching book, free its memory, and remove its pointer from the collection so that the list stays compact. Print a success or failure message.  
   5. **Exit** – Free *all* remaining allocated memory and terminate the program.  

3. **Input validation** – The program should handle non‑numeric input for menu choices and ISBN gracefully (e.g., re‑prompt).

4. **Memory management** – Every `malloc` must have a corresponding `free`. No memory leaks are permitted (you may use tools like Valgrind to verify).

## Example Interaction  

```
=== Personal Library Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Enter choice: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN (13 digits): 9780131103627
Enter year: 1988
Book added successfully!

=== Personal Library Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Enter choice: 2

--- Library Contents ---
1. Title : The C Programming Language
   Author: Kernighan & Ritchie
   ISBN  : 9780131103627
   Year  : 1988

=== Personal Library Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Enter choice: 3

Enter ISBN to search: 9780131103627
--- Book Found ---
Title : The C Programming Language
Author: Kernighan & Ritchie
ISBN  : 9780131103627
Year  : 1988

=== Personal Library Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Remove a book by ISBN
5) Exit
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be represented by a `struct Book`.  
* **Display function** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Menu requirement** – The menu must contain an explicit option to **EXIT** the program (as shown in the example, option 5). Selecting this option must free every allocated `struct Book` before termination.  
* **Single‑responsibility functions** – Apart from `main`, you may create additional helper functions (e.g., for adding, searching, removing), but the *only* function that directly prints a book’s fields is `displayBook`.  
* **Dynamic collection** – You may implement the collection as a dynamically resized array (using `realloc`) **or** as a singly linked list; in either case, memory for each `struct Book` must be obtained with `malloc` and released with `free`.  
* **No global variables** – All data structures should be passed to functions via parameters or returned values; avoid using global variables for the book collection.  

---  

Your task is to write the complete C program that satisfies the above specifications and constraints. Remember to test your program thoroughly for memory leaks and correct handling of edge cases (e.g., attempting to remove a non‑existent ISBN).

---

## Problem 63 - openai/gpt-oss-120b - Iteration 8
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **EcoTrack**, a startup that monitors the water usage of households. Each household reports a series of daily water‑consumption readings. The data for each household is not known at compile‑time; the program must allocate memory dynamically as households are added and release it when they are removed.

Your task is to write a small console application that lets the user **add**, **remove**, and **display** households and their readings using `malloc`/`free`. The program should continue to run until the user explicitly chooses to exit.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Household` that contains:  
     * an integer `id` (unique identifier)  
     * an integer `numDays` (how many daily readings are stored)  
     * a pointer `int *readings` that points to an array of `numDays` integers (the daily water‑consumption values).  

2. **Menu‑driven interface** (displayed repeatedly until the user exits)  
   * **1. Add a household**  
     * Prompt for the household `id`.  
     * Prompt for `numDays` (must be > 0).  
     * Allocate memory for the `Household` structure and for its `readings` array using `malloc`.  
     * Prompt the user to enter `numDays` integer readings, storing each in the allocated array.  
     * Store the pointer to the new `Household` in a dynamically‑grown list of households (you may use a simple array that you re‑allocate each time a new household is added).  
   * **2. Remove a household**  
     * Prompt for the `id` of the household to delete.  
     * Locate the household in the list.  
     * Free the `readings` array, then free the `Household` structure itself.  
     * Remove the pointer from the list and shrink the list accordingly.  
     * If the `id` does not exist, print an error message.  
   * **3. Display a household**  
     * Prompt for the `id` of the household to show.  
     * Locate the household and call a function `displayEntity` (see constraints) to print:  
       * `Household ID: <id>`  
       * `Number of days: <numDays>`  
       * `Readings: <r1> <r2> … <rN>` (space‑separated)  
     * If the `id` does not exist, print an error message.  
   * **4. List all households**  
     * For every household currently stored, invoke `displayEntity` to show its data.  
   * **5. EXIT** – terminates the program.  

3. **Memory management**  
   * Every allocation performed with `malloc` must eventually be released with `free`.  
   * When the program exits, all remaining allocated memory must be freed.

4. **Error handling**  
   * If any `malloc` call returns `NULL`, print “Memory allocation failed.” and safely return to the menu without leaking memory.  
   * Validate user input where reasonable (e.g., `numDays` > 0).

---

## Example Interaction  

```
=== EcoTrack Menu ===
1) Add a household
2) Remove a household
3) Display a household
4) List all households
5) EXIT
Choose an option: 1

Enter household ID: 101
Enter number of days: 3
Enter reading for day 1: 120
Enter reading for day 2: 135
Enter reading for day 3: 110
Household added successfully.

=== EcoTrack Menu ===
1) Add a household
2) Remove a household
3) Display a household
4) List all households
5) EXIT
Choose an option: 3

Enter household ID to display: 101
Household ID: 101
Number of days: 3
Readings: 120 135 110

=== EcoTrack Menu ===
1) Add a household
2) Remove a household
3) Display a household
4) List all households
5) EXIT
Choose an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct Household` as described above.  
* **Display function** – The logic that prints the details of **one** household must be placed in a function with the exact prototype:  

  ```c
  void displayEntity(const struct Household *h);
  ```  

* **Menu requirement** – The menu must contain an explicit option labeled **5) EXIT** (or the keyword “EXIT”) that terminates the program.  
* **Single‑source file** – All code (including `displayEntity`) must be written in a single `.c` source file.  
* **Dynamic list handling** – You may not use a fixed‑size array with a hard‑coded maximum number of households; the list of household pointers must grow/shrink using `realloc` (or repeated `malloc`/`free`).  

---  

*Design your solution so that a student who has just learned `malloc`, `free`, and basic `struct` handling can implement it confidently.*

---

## Problem 64 - openai/gpt-oss-120b - Iteration 9
# STEP 1: PROBLEM  

## Background  
You have been hired by the campus IT department to write a tiny “Student Registry” utility that runs in a terminal. The program must keep track of an arbitrary number of students entered by the user during a single execution. Because the number of students is not known beforehand, you must allocate and free memory dynamically using `malloc`/`calloc` and `free`.  

Each student record contains:  

* an integer **ID** (positive, unique for the session)  
* a string **name** (maximum 30 characters, no spaces)  
* a floating‑point **GPA** (0.0 – 4.0)  

The program should present a simple text menu that lets the user add new students, delete a student by ID, display the details of a particular student, and list all stored students. When the program terminates, all allocated memory must be released.

---

## Requirements  

1. **Data Representation** – Define a `struct Student` that holds the three fields listed above.  
2. **Dynamic Storage** – Store the collection of students in a dynamically‑allocated array that can grow or shrink as students are added or removed.  
3. **Menu** – Repeatedly display a menu with the following options (the numbers are mandatory):  
   * `1` – Add a new student  
   * `2` – Delete a student (by ID)  
   * `3` – Display a student’s details (by ID)  
   * `4` – List all students (in the order they were added)  
   * `5` – **EXIT** the program (this option must terminate the loop)  
4. **Adding** – Prompt for ID, name, and GPA, allocate space for the new `Student`, and expand the array accordingly. If the entered ID already exists, print an error and do not add a duplicate.  
5. **Deleting** – Locate the student with the given ID, free its memory, shift remaining elements to keep the array contiguous, and shrink the array. If the ID does not exist, print an error message.  
6. **Displaying One Student** – Implement a function `void displayStudent(const struct Student *s)` that prints a single student in the format:  
   ```
   ID: <id>, Name: <name>, GPA: <gpa>
   ```  
   The menu option **3** must call this function.  
7. **Listing All** – Iterate over the array and call `displayStudent` for each stored student.  
8. **Memory Management** – Every call to `malloc`/`calloc` must have a matching `free`. No memory leaks are allowed.  
9. **Input Validation** – The program should handle non‑numeric input for menu choices gracefully (i.e., re‑prompt). GPA must be within the valid range; otherwise, reject the entry.  

---

## Example Interaction  

```
=== Student Registry ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 101
Enter name: Alice
Enter GPA: 3.7
Student added.

=== Student Registry ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) EXIT
Choose an option: 1
Enter ID: 102
Enter name: Bob
Enter GPA: 3.2
Student added.

=== Student Registry ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) EXIT
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice, GPA: 3.70

=== Student Registry ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) EXIT
Choose an option: 4
ID: 101, Name: Alice, GPA: 3.70
ID: 102, Name: Bob, GPA: 3.20

=== Student Registry ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) EXIT
Choose an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented by a `struct Student`.  
* **Display Function** – The logic for displaying the details of ONE specific entity must be in a function named `displayStudent`.  
* **Menu Requirement** – The menu must contain an explicit option `5` (or the keyword `EXIT`) that terminates the program.  
* **Single‑File Implementation** – All code must reside in one source file; only `main` and the required helper functions (e.g., `displayStudent`, any array‑management helpers) are allowed.  
* **Dynamic Allocation Only** – Do **not** use fixed‑size global arrays; every addition/removal must involve `malloc`/`realloc`/`free`.  

---  

*Your task is to write the complete C program that satisfies the description above.*

---

## Problem 65 - openai/gpt-oss-120b - Iteration 10
# STEP 1: PROBLEM  

## Background  
You have been hired as the software engineer for **EcoGarden**, a startup that sells customizable garden kits. Each kit contains a variable‑length list of plant species that the customer selects at runtime. The program must store the information for each plant (its name, the number of seeds to plant, and the recommended spacing in centimeters) using dynamic memory allocation, because the number of plants in a kit is not known until the user enters it.

Your task is to write a C program that lets the user:

1. Create a new garden kit by specifying how many different plant species it will contain.  
2. Enter the data for each species.  
3. Display the complete list of species in the kit.  
4. Delete the kit and release all allocated memory before the program terminates (or when the user chooses to start a new kit).

The program should demonstrate correct use of `malloc`, `free`, and pointer handling.

---

## Requirements  

1. **Data Structure**  
   - Define a `struct Plant` that holds:  
     - `char *name` – a dynamically allocated string (maximum length 50 characters).  
     - `int seeds` – number of seeds to plant.  
     - `float spacing` – recommended spacing in centimeters.  

2. **Dynamic Allocation**  
   - Allocate an array of `Plant` structures of size *n* (the number of species) using `malloc`.  
   - For each plant, allocate just enough memory to store its name (including the terminating `'\0'`).  

3. **Menu‑Driven Interface** (optional but recommended)  
   - Present a menu with the following options:  
     1. **Create New Kit** – prompts for *n* and then reads the data for each plant.  
     2. **Display Kit** – prints all stored plants in the order entered.  
     3. **Delete Kit** – frees all memory associated with the current kit and resets the internal state so a new kit can be created.  
     4. **Exit** – terminates the program.  
   - The program must **include a specific menu option to EXIT the program** (option 4 in the list above).  

4. **Functions**  
   - Implement a function `void displayPlant(const Plant *p);` that prints the details of a single plant.  
   - The logic for displaying the whole kit must call `displayPlant` for each element.  

5. **Error Handling**  
   - If memory allocation fails, print an error message and gracefully terminate the program.  
   - If the user selects “Display Kit” or “Delete Kit” before a kit has been created, print an informative message.

6. **Program Termination**  
   - Before exiting (whether via the menu or an error), ensure that **all dynamically allocated memory is freed**.

---

## Example Interaction  

```
=== EcoGarden Kit Manager ===
1) Create New Kit
2) Display Kit
3) Delete Kit
4) Exit
Select an option: 1

Enter number of plant species: 3

--- Plant 1 ---
Name: Tomato
Seeds to plant: 12
Spacing (cm): 45.5

--- Plant 2 ---
Name: Basil
Seeds to plant: 5
Spacing (cm): 20.0

--- Plant 3 ---
Name: Marigold
Seeds to plant: 8
Spacing (cm): 30.0

Kit created successfully!

=== EcoGarden Kit Manager ===
1) Create New Kit
2) Display Kit
3) Delete Kit
4) Exit
Select an option: 2

Garden Kit Contents:
1) Name: Tomato   Seeds: 12   Spacing: 45.5 cm
2) Name: Basil    Seeds: 5    Spacing: 20.0 cm
3) Name: Marigold Seeds: 8    Spacing: 30.0 cm

=== EcoGarden Kit Manager ===
1) Create New Kit
2) Display Kit
3) Delete Kit
4) Exit
Select an option: 3

Kit deleted. All memory freed.

=== EcoGarden Kit Manager ===
1) Create New Kit
2) Display Kit
3) Delete Kit
4) Exit
Select an option: 4

Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Plant` as described above.  
* **Display Function** – The details of ONE specific plant must be printed by a function named `displayPlant`.  
* **Memory Management** – Every `malloc` (or related allocation) must have a matching `free`. No memory leaks are permitted.  
* **Menu Exit Option** – The program must include a menu option to EXIT the program (option 4 in the example).  

*Optional additional constraint for extra credit*:  
* Implement the menu handling in a separate function `int showMenu(void);` that returns the selected option.  

---  

**Deliverable:** Submit a single C source file (`eco_garden.c`) that compiles without warnings using `gcc -Wall -Wextra -std=c11` and fulfills all the requirements and constraints listed above.

---

## Problem 66 - openai/gpt-oss-120b - Iteration 11
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its catalogue system.  Each book record must be stored in memory only while the program runs, and the number of books is not known beforehand.  You are asked to write a small C program that lets a librarian **add**, **remove**, **list**, and **search** for books using dynamic memory allocation (`malloc`, `free`).  The program should keep the records in a singly‑linked list that grows and shrinks as the librarian performs operations.

## Requirements  

1. **Data representation**  
   * Define a `struct Book` that contains:  
     - an integer `id` (unique identifier)  
     - a character array `title[101]` (null‑terminated string, max 100 characters)  
     - a character array `author[51]` (null‑terminated string, max 50 characters)  
     - a pointer `struct Book *next` for the linked list.  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   * **1 – Add a new book**  
     - Prompt for `id`, `title`, and `author`.  
     - Allocate a new `struct Book` with `malloc`.  
     - Insert the new node at the **end** of the list.  
   * **2 – Delete a book by id**  
     - Prompt for the `id`.  
     - Search the list; if the book exists, unlink it and `free` its memory.  
     - If the `id` is not found, print `Book not found.`  
   * **3 – List all books**  
     - Traverse the list and print each book’s `id`, `title`, and `author` on a separate line.  
   * **4 – Search for a book by id**  
     - Prompt for the `id`.  
     - If found, display the book’s details using the required function `displayBook`.  
     - If not found, print `Book not found.`  
   * **0 – Exit**  
     - Before terminating, free any remaining allocated nodes.  

3. **Functionality constraints**  
   * The logic that prints the details of **one** specific book must be placed in a function with the exact prototype:  
     ```c
     void displayBook(const struct Book *b);
     ```  
   * All other list manipulations (add, delete, list, search) may be implemented in `main` or helper functions of your choice, but `displayBook` must be used wherever a single book’s information is shown.  

4. **Robustness**  
   * The program must not leak memory; every `malloc` must eventually be paired with a `free`.  
   * Input can be assumed to be well‑formed (correct data types), but the program should handle the case where the requested `id` does not exist.  

## Example Interaction  

```
=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 1
Enter book id: 101
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added.

=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 1
Enter book id: 202
Enter title: Introduction to Algorithms
Enter author: Cormen et al.
Book added.

=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 3
ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie
ID: 202 | Title: Introduction to Algorithms | Author: Cormen et al.

=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 4
Enter book id to search: 202
ID: 202 | Title: Introduction to Algorithms | Author: Cormen et al.

=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 2
Enter book id to delete: 101
Book deleted.

=== Library Catalogue ===
1. Add a new book
2. Delete a book by id
3. List all books
4. Search for a book by id
0. Exit
Choose an option: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be represented by a `struct Book` as described above.  
* **Display function** – The details of a single book must be printed by a function named `displayBook` with the exact prototype shown.  
* **Menu exit option** – The menu must contain an explicit option `0` (or the word `EXIT`) that terminates the program.  
* **Dynamic memory** – All book records must be allocated with `malloc` (or `calloc`) and released with `free`. No static arrays of `struct Book` are allowed.  

---  

*Write the program in C, adhering to the constraints and using good coding style (proper error checking for allocation, clear comments, and freeing all memory before exit).*

---

## Problem 67 - openai/gpt-oss-120b - Iteration 12
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Track**, a startup that monitors the growth of small indoor plants for hobbyists. Each plant is identified by a unique *Plant ID* and has three pieces of information that change over time:

1. **Current height** (in centimeters, a `float`).  
2. **Number of leaves** (an `int`).  
3. **Health rating** (a character: `A`, `B`, `C`, or `D`).  

The number of plants the system must handle is not known at compile‑time; the user will add and remove plants while the program runs. Therefore, you must allocate and de‑allocate memory dynamically using `malloc` and `free`.

## Program Requirements  

Write a C program that provides a simple text‑based menu allowing the user to manage the plant collection. The program must support the following operations:

1. **Add a new plant**  
   * Prompt for Plant ID (string, max 20 characters), height, leaf count, and health rating.  
   * Dynamically allocate a `struct Plant` to store the data and store a pointer to it in an array that also grows dynamically as needed.  

2. **Remove an existing plant**  
   * Prompt for the Plant ID to delete.  
   * Find the matching plant, free its memory, and shift the remaining pointers in the array to keep it compact.  

3. **Update a plant’s data**  
   * Prompt for the Plant ID.  
   * If found, allow the user to change any of the three attributes (height, leaf count, health rating).  

4. **Display a plant’s details**  
   * Prompt for the Plant ID.  
   * If the plant exists, call a function `displayPlant` (see constraints) to print all its fields in a readable format.  

5. **List all plants**  
   * Iterate over the dynamic array and print the details of every stored plant.  

6. **Exit**  
   * Terminate the program after freeing **all** allocated memory.  

The menu should repeat until the user selects the exit option.

## Example Interaction  

```
=== Eco‑Track Plant Manager ===
1) Add plant
2) Remove plant
3) Update plant
4) Display plant
5) List all plants
6) EXIT
Select an option: 1

Enter Plant ID: basil01
Enter height (cm): 12.5
Enter number of leaves: 8
Enter health rating (A/B/C/D): B
Plant added successfully!

=== Eco‑Track Plant Manager ===
1) Add plant
2) Remove plant
3) Update plant
4) Display plant
5) List all plants
6) EXIT
Select an option: 4

Enter Plant ID to display: basil01
Plant ID: basil01
Height: 12.5 cm
Leaves: 8
Health: B

=== Eco‑Track Plant Manager ===
1) Add plant
2) Remove plant
3) Update plant
4) Display plant
5) List all plants
6) EXIT
Select an option: 6

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Plant` containing at least the following members:  
   ```c
   typedef struct {
       char id[21];   // up to 20 characters + terminating '\0'
       float height;
       int leaves;
       char health;   // 'A'..'D'
   } Plant;
   ```

2. **Display Function** – The logic for showing the details of **one** specific plant must be encapsulated in a function with the exact prototype:  
   ```c
   void displayPlant(const Plant *p);
   ```

3. **Dynamic Array Management** – The collection of plant pointers must be stored in a dynamically allocated array that expands (using `realloc` or a similar technique) when new plants are added and contracts when plants are removed.

4. **Memory Discipline** – Every call to `malloc`/`realloc` must have a matching `free`. No memory leaks are permitted; the program must free all allocated memory before exiting.

5. **Menu Exit Option** – The menu must include an explicit option labeled **6) EXIT** (or the keyword `EXIT`) that terminates the program after all cleanup.  

6. **Standard Library Only** – You may only use headers from the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are allowed.  

---  

*Design your solution to be clear, modular, and robust against invalid input (e.g., non‑existent Plant IDs). The emphasis of this assignment is correct use of dynamic memory allocation and proper de‑allocation.*

---

## Problem 68 - openai/gpt-oss-120b - Iteration 13
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior software engineer for **EcoLogistics**, a company that manages a fleet of delivery drones. Each drone can carry a variable‑size list of packages for a single delivery run. The number of packages is not known until the user (the dispatcher) enters it at run‑time.  

Your task is to write a C program that lets the dispatcher **create**, **display**, and **delete** a delivery run. Because the number of packages varies, you must allocate memory dynamically with `malloc` (or `calloc`) and release it with `free` when the run is no longer needed.

## Requirements  

1. **Define a `struct Package`** that stores:  
   * an integer `id` (unique identifier of the package)  
   * a floating‑point `weight` (in kilograms)  

2. **Define a `struct DeliveryRun`** that stores:  
   * an integer `runId` (identifier of the delivery run)  
   * an integer `packageCount` (how many packages are in this run)  
   * a pointer `Package *packages` that points to a dynamically allocated array of `Package` objects  

3. The program must present a **menu** with the following options (the user selects a number):  
   1. **Create a new delivery run** –  
      * Prompt for `runId` and `packageCount`.  
      * Allocate memory for the `packages` array using `malloc`.  
      * For each package, ask for its `id` and `weight`.  
   2. **Display the current delivery run** –  
      * If a run exists, print `runId`, `packageCount`, and a table of all packages (`id` and `weight`).  
      * The printing logic must be encapsulated in a function named `displayRun`.  
   3. **Delete the current delivery run** –  
      * Release the memory allocated for the `packages` array using `free`.  
      * Reset the stored run information so that a new run can be created later.  
   4. **Exit** – terminate the program.  

4. The program must handle the case where the user tries to display or delete a run before one has been created, printing an appropriate message.

5. The program must **not leak memory**: every allocation performed with `malloc` must be paired with a corresponding `free` before the program terminates or before a new run overwrites the old one.

## Example Input / Output  

```
=== EcoLogistics Delivery Manager ===
1) Create a new delivery run
2) Display the current delivery run
3) Delete the current delivery run
4) Exit
Select an option: 2
No delivery run exists. Please create one first.

1) Create a new delivery run
2) Display the current delivery run
3) Delete the current delivery run
4) Exit
Select an option: 1
Enter run ID: 101
Enter number of packages: 3
Package #1 ID: 5001
Package #1 weight (kg): 2.4
Package #2 ID: 5002
Package #2 weight (kg): 1.1
Package #3 ID: 5003
Package #3 weight (kg): 3.7

Delivery run created successfully.

1) Create a new delivery run
2) Display the current delivery run
3) Delete the current delivery run
4) Exit
Select an option: 2

--- Delivery Run 101 ---
Number of packages: 3
ID      Weight(kg)
5001    2.40
5002    1.10
5003    3.70

1) Create a new delivery run
2) Display the current delivery run
3) Delete the current delivery run
4) Exit
Select an option: 3
Delivery run deleted and memory freed.

1) Create a new delivery run
2) Display the current delivery run
3) Delete the current delivery run
4) Exit
Select an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct DeliveryRun` (and a nested `struct Package`).  
* **Function requirement** – The logic that prints the details of a delivery run must be placed in a function with the exact prototype:  

  ```c
  void displayRun(const struct DeliveryRun *run);
  ```  

* **Menu exit** – The menu must contain an explicit option to **Exit** the program (option 4 in the example). Selecting this option ends the program.  
* **Single‑source file** – All code must be written in one `.c` file. Apart from `main`, you may define additional helper functions, but the core display logic must be in `displayRun`.  
* **No global variables** – All data should be stored in local variables (or passed via parameters).  

---  

*Your students should now implement the described program, demonstrating correct use of `malloc`, `free`, and struct handling.*

---

## Problem 69 - openai/gpt-oss-120b - Iteration 14
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Track**, a small startup that builds simple inventory‑tracking tools for community gardens. Each garden keeps a list of **plant beds**. A plant bed stores the name of the vegetable being grown, the number of rows in the bed, and the current number of plants planted.  

Because the number of beds varies from garden to garden and may change while the program is running (the gardener can add or remove beds), you must allocate memory dynamically. The program will let the user add new beds, delete existing ones, and view the details of a specific bed.

## Requirements  

Write a C program that:

1. **Defines a `struct Bed`** containing  
   * `char *name;`     // vegetable name (dynamically allocated string)  
   * `int rows;`     // number of rows in the bed  
   * `int plants;`    // total plants currently planted  

2. **Keeps a dynamic array of `struct Bed` objects** (the array itself must be allocated with `malloc`/`realloc`). The array may grow or shrink as beds are added or removed.

3. Presents the user with a **menu** (see “Menu Options” below). The menu must include an explicit option to **EXIT** the program.

4. Implements the following menu actions:  

   | Option | Description |
   |--------|-------------|
   | `1`    | **Add a new bed** – Prompt for vegetable name, rows, and plants. Allocate space for the new `struct Bed`, copy the name into a newly allocated string, and append the bed to the dynamic array. |
   | `2`    | **Delete a bed** – Prompt for the index (0‑based) of the bed to remove. Free the name string, shift later elements left, and shrink the array with `realloc`. If the index is invalid, display an error and return to the menu. |
   | `3`    | **Display a bed** – Prompt for the index of the bed to view. The details must be printed by calling a **function named `displayBed`** (see Constraints). If the index is invalid, display an error. |
   | `4`    | **List all beds** – Print the index and vegetable name of every bed currently stored. |
   | `5`    | **EXIT** – Terminate the program, freeing all allocated memory. |

5. Performs **proper error checking** for all user input (non‑numeric input, out‑of‑range indices, allocation failures, etc.).

6. Before terminating (whether via the EXIT option or an unrecoverable error), **frees every piece of memory** that was allocated during execution.

## Simple Example  

```
=== Eco‑Track Plant Bed Manager ===
1. Add a new bed
2. Delete a bed
3. Display a bed
4. List all beds
5. EXIT
Choose an option: 1

Enter vegetable name: Tomato
Enter number of rows: 3
Enter number of plants: 12
Bed added successfully!

=== Eco‑Track Plant Bed Manager ===
1. Add a new bed
2. Delete a bed
3. Display a bed
4. List all beds
5. EXIT
Choose an option: 1

Enter vegetable name: Lettuce
Enter number of rows: 2
Enter number of plants: 8
Bed added successfully!

=== Eco‑Track Plant Bed Manager ===
1. Add a new bed
2. Delete a bed
3. Display a bed
4. List all beds
5. EXIT
Choose an option: 4

[0] Tomato
[1] Lettuce

=== Eco‑Track Plant Bed Manager ===
1. Add a new bed
2. Delete a bed
3. Display a bed
4. List all beds
5. EXIT
Choose an option: 3

Enter index of bed to display: 0
--- Bed 0 ---
Vegetable: Tomato
Rows: 3
Plants: 12

=== Eco‑Track Plant Bed Manager ===
1. Add a new bed
2. Delete a bed
3. Display a bed
4. List all beds
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Bed` as described above.  
* **Display Function** – The logic that prints the details of a single bed must be placed in a function with the exact prototype:  
  ```c
  void displayBed(const struct Bed *b, int index);
  ```  
* **Single‑responsibility Functions** – Apart from `main`, you may create helper functions (e.g., for adding, deleting, listing), but the *only* function that directly prints the full contents of a bed is `displayBed`.  
* **Menu Exit Option** – The menu must contain an option labeled **`5. EXIT`** (or the keyword `EXIT`) that terminates the program. Selecting this option must cause the program to free all allocated memory before ending.  
* **Dynamic Allocation Only** – All memory for the array of beds and for each vegetable name must be obtained with `malloc`, `calloc`, or `realloc`. No static or fixed‑size arrays may be used to store the beds.  

---  

*Your task is to write the complete program that satisfies the above specification.*

---

## Problem 70 - openai/gpt-oss-120b - Iteration 15
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for the campus library’s “quick‑lookup” kiosk. The kiosk stores information about **books** that are currently on the shelves. Because the number of books can change at runtime (books are added when new copies arrive and removed when they are withdrawn), you must manage the collection with **dynamic memory allocation** (`malloc` / `free`).  

Your program will allow a librarian to:  

1. **Add** a new book to the collection.  
2. **Remove** a book by its ISBN.  
3. **Display** the details of a single book (chosen by ISBN).  
4. **List** all books currently stored.  
5. **Exit** the program.  

The librarian interacts with the program through a simple text‑based menu.

## Requirements  

1. Define a `struct` named `Book` that contains at least the following fields:  
   - `char *title`   – dynamically allocated string (maximum length 100 characters).  
   - `char *author`  – dynamically allocated string (maximum length 100 characters).  
   - `char isbn[14]` – fixed‑size array to hold a 13‑digit ISBN plus the terminating null character.  
   - `int year`      – year of publication.  

2. The collection of books must be stored in a **dynamically allocated array** of `Book` structures.  
   - When a new book is added, the array should be resized with `realloc`.  
   - When a book is removed, the array should shrink accordingly and the memory used by the removed book’s `title` and `author` strings must be freed.  

3. Implement the following menu (displayed repeatedly until the user chooses to exit):  

   ```
   1) Add a new book
   2) Remove a book by ISBN
   3) Display a book by ISBN
   4) List all books
   5) EXIT
   Enter your choice: 
   ```

   - **Option 1**: Prompt for title, author, ISBN, and year, allocate the necessary memory, and insert the new `Book` into the array.  
   - **Option 2**: Prompt for an ISBN, locate the matching book, free its `title` and `author` strings, remove it from the array, and shrink the array. If the ISBN is not found, print an informative message.  
   - **Option 3**: Prompt for an ISBN and display the full details of the matching book. If the ISBN is not found, print an informative message.  
   - **Option 4**: Print a table of all books currently stored (ISBN, title, author, year).  
   - **Option 5**: Terminate the program after freeing **all** allocated memory.  

4. All input should be read from `stdin`; all output should be written to `stdout`.  

5. The program must **not leak memory** – every allocation performed with `malloc`/`realloc` must eventually be released with `free` before the program exits.  

## Example Interaction  

```
--- Library Quick‑Lookup ---
1) Add a new book
2) Remove a book by ISBN
3) Display a book by ISBN
4) List all books
5) EXIT
Enter your choice: 1
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN (13 digits): 0131103628
Enter year: 1988
Book added successfully.

Enter your choice: 1
Enter title: Clean Code
Enter author: Robert C. Martin
Enter ISBN (13 digits): 0132350882
Enter year: 2008
Book added successfully.

Enter your choice: 4
ISBN          Title                     Author                Year
0131103628    The C Programming Language Kernighan & Ritchie 1988
0132350882    Clean Code                Robert C. Martin      2008

Enter your choice: 3
Enter ISBN to display: 0132350882
ISBN: 0132350882
Title: Clean Code
Author: Robert C. Martin
Year: 2008

Enter your choice: 2
Enter ISBN to remove: 0131103628
Book removed.

Enter your choice: 4
ISBN          Title        Author          Year
0132350882    Clean Code   Robert C. Martin 2008

Enter your choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct` named `Book`.  
2. **Display Function** – The logic for showing the details of **one specific book** must be placed in a function with the exact prototype:  

   ```c
   void displayBook(const Book *b);
   ```  

3. **Single Helper Function** – Apart from `main`, you may create **no more than two additional functions** (the required `displayBook` plus optionally one helper for menu handling or array resizing).  
4. **Menu Exit Option** – The menu must include the option `5) EXIT` (or the exact keyword “EXIT”) that terminates the program.  
5. **Dynamic Allocation Only** – All strings for titles and authors must be allocated dynamically; using fixed‑size character arrays inside the struct for these fields is **not allowed**.  
6. **Error Handling** – If memory allocation fails at any point, the program should print an error message and exit gracefully, freeing any memory that was already allocated.  

Design your solution to satisfy all the above requirements and constraints. Happy coding!

---

## Problem 71 - openai/gpt-oss-120b - Iteration 16
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior software developer for **CampusConnect**, a small startup that maintains a simple in‑memory directory of students for a campus event. The directory must be built at run‑time; the number of participants is not known beforehand, so you need to allocate memory dynamically as students are added and release it when they are removed.  

Your task is to write a C program that lets the user manage this directory through a text‑based menu.

## Requirements  

1. **Data representation**  
   * Define a `struct Student` that contains:  
     * `int id` – a unique positive identifier (assume the user never repeats an existing id).  
     * `char *name` – a dynamically allocated string that can hold up to 100 characters (including the terminating null).  
     * `float gpa` – the student's grade point average.  

2. **Menu‑driven operations** (the program should loop until the user chooses to exit)  
   * **1 – Add a student**  
     * Prompt for `id`, `name`, and `gpa`.  
     * Allocate a new `Student` object with `malloc`.  
     * Allocate space for the `name` field with `malloc` (or `strdup`).  
     * Store the new student in a dynamically‑grown array (you may reallocate the array each time a new student is added).  
   * **2 – Remove a student**  
     * Prompt for the `id` of the student to delete.  
     * Locate the student in the array, `free` the memory used for the `name`, `free` the `Student` structure itself, and shift the remaining elements to keep the array compact.  
   * **3 – Display a student**  
     * Prompt for the `id` of the student to view.  
     * Locate the student and call a function `displayStudent` (see constraints) to print the student's details in the format shown below.  
   * **4 – List all students**  
     * Iterate over the array and call `displayStudent` for each entry.  
   * **0 – Exit**  
     * Before terminating, free all memory that is still allocated (both the name strings and the array of pointers).  

3. **Error handling**  
   * If the user tries to remove or display a student that does not exist, print an informative message and return to the menu.  
   * If any `malloc`/`realloc` call fails, print an error message and gracefully exit after freeing any memory that was already allocated.  

## Example Interaction  

```
=== CampusConnect Student Directory ===
1) Add a student
2) Remove a student
3) Display a student
4) List all students
0) Exit
Choose an option: 1
Enter ID: 101
Enter name: Alice Johnson
Enter GPA: 3.8
Student added.

1) Add a student
2) Remove a student
3) Display a student
4) List all students
0) Exit
Choose an option: 1
Enter ID: 202
Enter name: Bob Lee
Enter GPA: 3.5
Student added.

1) Add a student
2) Remove a student
3) Display a student
4) List all students
0) Exit
Choose an option: 3
Enter ID to display: 101
--- Student Details ---
ID   : 101
Name : Alice Johnson
GPA  : 3.80

1) Add a student
2) Remove a student
3) Display a student
4) List all students
0) Exit
Choose an option: 4
--- Student Details ---
ID   : 101
Name : Alice Johnson
GPA  : 3.80
--- Student Details ---
ID   : 202
Name : Bob Lee
GPA  : 3.50

1) Add a student
2) Remove a student
3) Display a student
4) List all students
0) Exit
Choose an option: 0
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Student`.  
* **Display function** – The logic for printing the details of a single student must be placed in a function with the exact prototype:  

  ```c
  void displayStudent(const struct Student *s);
  ```  

* **Memory management** – Every piece of memory obtained with `malloc`/`realloc` must be released with `free` before the program terminates.  
* **Menu requirement** – The program must present a text menu as described above, and the menu must include the explicit option **0 – Exit** to terminate the program.  
* **Single‑source file** – All code must reside in a single `.c` file; you may define additional static helper functions, but the only public entry point besides `main` may be `displayStudent`.  

---  

Design and implement the program according to the specifications and constraints above.

---

## Problem 72 - openai/gpt-oss-120b - Iteration 17
# STEP 1: PROBLEM  

## Background  
You have been hired as a software developer for **EcoGarden**, a startup that sells custom‑made garden planters.  Each planter can contain a variable number of different plant species, and the information about each species (its name, the number of seeds planted, and the average water requirement per day in milliliters) must be stored dynamically because the user does not know in advance how many species will be entered.

Your task is to write a small C program that lets the user **add**, **list**, **search**, and **remove** plant species from a single planter.  All plant records must be allocated on the heap using `malloc` (or `calloc`) and released with `free` when they are no longer needed.

## Requirements  

1. Define a `struct Plant` that contains:  
   * `char *name;`          – a dynamically allocated string (maximum length 50 characters).  
   * `int seeds;`           – number of seeds planted (positive integer).  
   * `float waterPerDay;`   – average water needed per day in milliliters (positive float).  
   * `struct Plant *next;`  – pointer to the next plant in the singly‑linked list.  

2. The program must maintain a **singly‑linked list** of `Plant` nodes representing the current contents of the planter.

3. Implement a **text‑based menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   ```
   1. Add a new plant
   2. List all plants
   3. Find a plant by name
   4. Remove a plant by name
   5. EXIT
   ```

4. For each menu option:  

   * **Add a new plant** – Prompt the user for the plant’s name, number of seeds, and water requirement. Allocate a new `Plant` node, copy the name into a heap‑allocated buffer, and insert the node at the **end** of the list.  

   * **List all plants** – Traverse the list and print each plant’s details on a separate line in the format:  
     `Name: <name>, Seeds: <seeds>, Water/day: <waterPerDay> ml`  

   * **Find a plant by name** – Prompt for a name, search the list, and if found call the required display function (see constraints) to show its details; otherwise print `Plant not found.`  

   * **Remove a plant by name** – Prompt for a name, locate the node, unlink it from the list, free **both** the name string and the node itself, and print `Plant removed.`; if the plant does not exist, print `Plant not found.`  

   * **EXIT** – Before terminating, free **all** remaining dynamically allocated memory (both name strings and list nodes) and then end the program.

5. The program must **validate input** where reasonable (e.g., seeds > 0, water > 0). If invalid data is entered, display an error message and return to the menu without modifying the list.

## Example Input / Output  

```
=== EcoGarden Planter Manager ===
1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 1

Enter plant name: Basil
Enter number of seeds: 12
Enter water per day (ml): 30.5
Plant added.

1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 1

Enter plant name: Tomato
Enter number of seeds: 5
Enter water per day (ml): 80
Plant added.

1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 2

Name: Basil, Seeds: 12, Water/day: 30.50 ml
Name: Tomato, Seeds: 5, Water/day: 80.00 ml

1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 3

Enter plant name to search: Tomato
Name: Tomato, Seeds: 5, Water/day: 80.00 ml

1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 4

Enter plant name to remove: Basil
Plant removed.

1. Add a new plant
2. List all plants
3. Find a plant by name
4. Remove a plant by name
5. EXIT
Choose an option: 5
All memory freed. Goodbye!
```

## ### CONSTRAINTS  

1. **Structure Requirement** – The primary data entity must be represented by a `struct Plant` as described above.  

2. **Display Function** – The logic for displaying the details of **one specific plant** must be placed in a function with the exact prototype:  

   ```c
   void displayPlant(const struct Plant *p);
   ```

   This function must be used both in the “List all plants” option (called for each node) and in the “Find a plant by name” option.

3. **Modular Design** – Apart from `main`, you may create **no more than three additional functions**. One of them must be `displayPlant`. The remaining functions (if any) should be clearly named and serve distinct purposes (e.g., adding, searching, or freeing the list).

4. **Memory Management** – Every allocation performed with `malloc`/`calloc` must have a corresponding `free`. Leaking memory will be considered a failure.

5. **Menu Exit** – The menu must include option **5. EXIT** (as shown) and selecting it must terminate the program after freeing all allocated memory.

---  

*Design the program to satisfy all the above requirements and constraints. Good luck!*

---

## Problem 73 - openai/gpt-oss-120b - Iteration 18
# STEP 1: PROBLEM  

## Background  
The university’s **Student Records Office** is moving from a paper‑based system to a simple C‑program that stores student information only while the program is running. Each student record consists of a name (maximum 30 characters), an integer ID, and a floating‑point GPA. Because the number of students entered each session is not known in advance, the program must allocate memory dynamically as records are added and release it when they are removed or when the program ends.

## Requirements  
Write a C program that implements the following functionality:

1. **Add a student** – Prompt the user for the name, ID, and GPA, allocate a new `Student` structure with `malloc`, store the data, and keep a pointer to the structure in a dynamically‑grown array (the array itself must also be allocated/re‑allocated with `malloc`/`realloc` as needed).  
2. **Delete a student** – Prompt for a student ID, locate the matching record, free the memory for that `Student` structure, and shrink the array accordingly (by moving the last element into the freed slot and resizing the array). If the ID does not exist, print an informative message.  
3. **Display a student** – Prompt for a student ID and print the stored name, ID, and GPA. The printing logic **must** be placed in a function named `displayStudent`.  
4. **List all students** – Print the details of every student currently stored, in the order they appear in the internal array.  
5. **Exit** – Before terminating, free all memory that was allocated for student records and for the array that holds their pointers.

The program should repeatedly present a menu until the user chooses the exit option.

## Example Interaction  

```
=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter name: Alice Johnson
Enter ID: 1001
Enter GPA: 3.75
Student added.

=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter name: Bob Lee
Enter ID: 1002
Enter GPA: 3.42
Student added.

=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 4
ID: 1001 | Name: Alice Johnson | GPA: 3.75
ID: 1002 | Name: Bob Lee      | GPA: 3.42

=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 3
Enter ID to display: 1002
ID: 1002 | Name: Bob Lee | GPA: 3.42

=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 2
Enter ID to delete: 1001
Student with ID 1001 deleted.

=== Student Record System ===
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Data Structure** – The primary entity must be represented with a `struct` named `Student` containing at least the fields `char name[31]; int id; float gpa;`.  
* **Display Function** – The logic for showing the details of **one** specific student must be encapsulated in a function with the exact prototype:  
  ```c
  void displayStudent(const Student *s);
  ```  
* **Memory Management** – Every allocation performed with `malloc`/`realloc` must have a corresponding `free` before the program terminates. No memory leaks are allowed.  
* **Menu Requirement** – The program must present a textual menu as shown in the example. The menu must include an option to **EXIT** the program; this option must be number **5** (or the keyword `exit`). Selecting this option ends the loop and triggers the final cleanup.  

*Optional but recommended*: Use `realloc` to grow/shrink the array of pointers to `Student` structures, rather than allocating a new array and copying manually.  

---  

*Your task is to write the complete C source file that satisfies all of the above.*

---

## Problem 74 - openai/gpt-oss-120b - Iteration 19
# STEP 1: PROBLEM  

## Background  
You have been hired as a software engineer for **EcoLog**, a startup that builds a simple inventory system for a community garden. The garden keeps track of **plant beds** – each bed holds a variable number of different vegetable types that are planted each season. Because the number of beds and the number of vegetables per bed change from season to season, the program must allocate memory dynamically.

Your task is to write a C program that lets the user **create**, **inspect**, and **delete** plant‑bed records at runtime using `malloc` and `free`. The program should continue to accept commands until the user chooses to exit.

## Requirements  

1. **Data representation**  
   * Define a `struct PlantBed` that contains:  
     * an integer `id` – a unique identifier for the bed (positive, non‑zero).  
     * an integer `vegCount` – how many vegetable types are currently planted in the bed.  
     * a pointer `char **vegNames` – an array of C‑strings, each string holding the name of a vegetable (e.g., `"Tomato"`).  

2. **Menu‑driven interface** (the program must present a text menu after each operation)  
   * **1. Add a new bed** – Prompt for the bed `id`, the number of vegetables, and then each vegetable name. Allocate all needed memory dynamically and store the new `PlantBed` in a dynamically‑grown list.  
   * **2. Display a bed** – Prompt for a bed `id` and print the bed’s information (id, number of vegetables, and the list of names). The printing logic must be placed in a function called `displayBed`.  
   * **3. Remove a bed** – Prompt for a bed `id`, free all memory associated with that bed (including each vegetable name and the `vegNames` array), and remove the bed from the list.  
   * **4. List all beds** – Print a summary line for every stored bed (id and vegCount).  
   * **5. EXIT** – Terminate the program after freeing any remaining allocated memory.  

3. **Error handling**  
   * If the user tries to add a bed with an `id` that already exists, print an error and do not add a duplicate.  
   * If the user requests to display or remove a non‑existent `id`, print an appropriate message.  
   * All input strings (vegetable names) may be assumed to be at most 31 characters long.

4. **Memory management**  
   * Every allocation performed with `malloc` (or `calloc`) must have a matching `free` at the appropriate time.  
   * No memory leak may remain when the program exits.

## Example Interaction  

```
=== EcoLog Plant‑Bed Manager ===
1) Add a new bed
2) Display a bed
3) Remove a bed
4) List all beds
5) EXIT
Choose an option: 1

Enter bed id: 101
How many vegetables in this bed? 3
Enter name of vegetable #1: Tomato
Enter name of vegetable #2: Lettuce
Enter name of vegetable #3: Carrot
Bed 101 added successfully.

=== EcoLog Plant‑Bed Manager ===
1) Add a new bed
2) Display a bed
3) Remove a bed
4) List all beds
5) EXIT
Choose an option: 2

Enter bed id to display: 101
--- Bed 101 ---
Vegetable count: 3
1) Tomato
2) Lettuce
3) Carrot

=== EcoLog Plant‑Bed Manager ===
1) Add a new bed
2) Display a bed
3) Remove a bed
4) List all beds
5) EXIT
Choose an option: 4

Current beds:
* Bed 101 – 3 vegetables

=== EcoLog Plant‑Bed Manager ===
1) Add a new bed
2) Display a bed
3) Remove a bed
4) List all beds
5) EXIT
Choose an option: 5

Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be represented by a `struct PlantBed` as described above.  
* **Display function** – The logic for printing the details of **one specific bed** must be encapsulated in a function with the exact prototype:  

  ```c
  void displayBed(const struct PlantBed *bed);
  ```  

* **Single‑responsibility helper** – All memory‑freeing for a single bed must be performed by a separate function named `void freeBed(struct PlantBed *bed);`.  
* **Menu requirement** – The program **must** include a menu option numbered **5** (or the keyword `EXIT`) that terminates the program. Selecting this option must first free any remaining allocated memory.  
* **Standard library only** – You may only use headers from the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are allowed.  

---  

Design your solution so that a student who has just learned `malloc`, `free`, and basic `struct` handling can implement it correctly.

---

## Problem 75 - openai/gpt-oss-120b - Iteration 20
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Events Office** to write a small utility that keeps track of upcoming campus events.  
Each event has a title, a day‑of‑the‑month (1‑31), and an expected number of attendees.  
Because the number of events is not known in advance and can change while the program is running, you must store the events in dynamically allocated memory using `malloc`/`free`.

## Requirements  

Write a C program that provides a **menu‑driven interface** with the following options:

1. **Add a new event** – Prompt the user for the title (a single word, max 31 characters), the day, and the expected attendance. Allocate a new `struct Event` on the heap and store it in a dynamically‑grown array (or linked list).  
2. **Remove an event** – Ask for the day of the event to delete. If an event with that day exists, remove it from the collection and free its memory. If multiple events share the same day, remove the first one found.  
3. **Display an event** – Ask for the day and print the details of the event that occurs on that day using a dedicated function `displayEvent`. If no event exists for the given day, print an appropriate message.  
4. **List all events** – Print the details of every stored event in the order they were added.  
5. **Exit** – Terminate the program, freeing all allocated memory.

Additional functional details:

- The program must continue to display the menu after completing an operation, until the user selects **Exit**.  
- Input validation is required: the day must be between 1 and 31, and the attendance must be a non‑negative integer.  
- The program should handle the situation where the user tries to remove or display an event that does not exist gracefully.  

## Example Interaction  

```
=== Campus Events Manager ===
1) Add event
2) Remove event
3) Display event
4) List all events
5) Exit
Choose an option: 1
Enter title: Picnic
Enter day (1-31): 12
Enter expected attendance: 150
Event added.

=== Campus Events Manager ===
1) Add event
2) Remove event
3) Display event
4) List all events
5) Exit
Choose an option: 1
Enter title: Hackathon
Enter day (1-31): 20
Enter expected attendance: 80
Event added.

=== Campus Events Manager ===
1) Add event
2) Remove event
3) Display event
4) List all events
5) Exit
Choose an option: 4
Day 12: Picnic (150 attendees)
Day 20: Hackathon (80 attendees)

=== Campus Events Manager ===
1) Add event
2) Remove event
3) Display event
4) List all events
5) Exit
Choose an option: 3
Enter day to display: 12
Day 12: Picnic (150 attendees)

=== Campus Events Manager ===
1) Add event
2) Remove event
3) Display event
4) List all events
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Event` containing at least the fields `char title[32]`, `int day`, and `int attendance`.  
2. **Display Function** – The logic for printing the details of a single event must be placed in a function with the exact prototype:  

   ```c
   void displayEvent(const struct Event *e);
   ```  

3. **Memory Management** – Every `malloc`/`calloc` call must have a matching `free` before the program terminates. No memory leaks are permitted.  
4. **Menu Exit Option** – The menu must include an explicit option (number **5**) labelled **Exit** that ends the program.  

*Feel free to choose any dynamic container (resizable array, singly linked list, etc.) as long as it respects the constraints above.*

---

## Problem 76 - openai/gpt-oss-120b - Iteration 21
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **CampusConnect**, a small campus‑wide service that keeps a temporary list of “study‑group” participants while the program is running. The list is not stored on disk; it exists only in memory while the user interacts with the program. Because the number of participants is not known in advance, you must allocate and release memory dynamically using `malloc` and `free`.

## Requirements  
Write a C program that allows the user to manage a collection of **participants**. Each participant is described by the following data:

| Field          | Type               | Description                         |
|----------------|--------------------|-------------------------------------|
| `id`           | `int`              | A unique positive integer identifier |
| `name`         | `char[51]`         | Participant’s name (max 50 chars)   |
| `age`          | `int`              | Age in years (positive)             |
| `gpa`          | `float`            | Grade Point Average (0.0 – 4.0)      |

Your program must present a **menu‑driven interface** with the following options:

1. **Add a participant** – Prompt for the fields above, allocate a new struct, and store it in a dynamically‑grown array (or linked list).  
2. **Remove a participant** – Ask for the participant’s `id`. If found, delete the struct, free its memory, and compact the collection so that no “holes” remain.  
3. **Display a participant** – Ask for an `id` and print all information for that participant. The display logic must be placed in a function called `displayParticipant`.  
4. **List all participants** – Print the details of every participant currently stored, in the order they were added.  
5. **Exit** – Terminate the program after freeing all allocated memory.  

The program should continue to show the menu after each operation until the user selects **Exit**.

## Example Input / Output  

```
=== CampusConnect Menu ===
1. Add participant
2. Remove participant
3. Display participant
4. List all participants
5. Exit
Choose an option: 1

Enter ID: 101
Enter name: Alice Johnson
Enter age: 20
Enter GPA: 3.75
Participant added.

=== CampusConnect Menu ===
1. Add participant
2. Remove participant
3. Display participant
4. List all participants
5. Exit
Choose an option: 1

Enter ID: 102
Enter name: Bob Smith
Enter age: 22
Enter GPA: 3.42
Participant added.

=== CampusConnect Menu ===
1. Add participant
2. Remove participant
3. Display participant
4. List all participants
5. Exit
Choose an option: 4

ID: 101 | Name: Alice Johnson | Age: 20 | GPA: 3.75
ID: 102 | Name: Bob Smith     | Age: 22 | GPA: 3.42

=== CampusConnect Menu ===
1. Add participant
2. Remove participant
3. Display participant
4. List all participants
5. Exit
Choose an option: 3

Enter ID to display: 101
ID: 101 | Name: Alice Johnson | Age: 20 | GPA: 3.75

=== CampusConnect Menu ===
1. Add participant
2. Remove participant
3. Display participant
4. List all participants
5. Exit
Choose an option: 5

Goodbye!
```

*(If the user tries to remove or display an `id` that does not exist, print an appropriate “Participant not found.” message.)*

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity must be defined as a `struct` named `Participant`.  
2. **Dynamic Allocation** – All participants must be created with `malloc` (or `calloc`) and released with `free`. No static or global arrays of fixed size may be used to store the participants.  
3. **Display Function** – The logic for printing the details of **one** participant must reside in a function with the exact prototype:  

   ```c
   void displayParticipant(const Participant *p);
   ```  

4. **Menu Requirement** – The menu must include an explicit option to **Exit** the program (option 5 in the example). Selecting this option must cause the program to free every allocated block before terminating.  

5. **Single‑responsibility Functions** – Apart from `main`, you must implement at least the following helper functions (you may add more if you wish):  

   - `Participant* createParticipant();` – reads input, allocates, and returns a pointer.  
   - `int removeParticipant(Participant **arr, int *size, int id);` – removes the participant with the given `id`, frees its memory, and updates the collection; returns 1 on success, 0 if not found.  
   - `Participant* findParticipant(const Participant *arr, int size, int id);` – returns a pointer to the participant with the given `id` or `NULL` if absent.  

6. **Robustness** – The program should handle invalid menu choices gracefully (e.g., print “Invalid option, try again.” and redisplay the menu).  

7. **Compilation** – The solution must compile with a standard C compiler (`gcc -Wall -Wextra -std=c11`).  

Deliver a single C source file that fulfills all the above requirements.

---

## Problem 77 - openai/gpt-oss-120b - Iteration 22
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Interstellar Logistics Agency (ILA)** to write a small command‑line tool that helps a space‑station crew keep track of the cargo containers they receive and unload.  
Each container has an identifier, a weight (in kilograms), and a short textual description.  
Because the number of containers is not known in advance and changes during the mission, the program must allocate and release memory dynamically using `malloc`, `realloc`, and `free`.

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Cargo` that stores:  
     - `int id;`      // unique container identifier  
     - `float weight;`  // weight in kilograms  
     - `char *desc;`  // dynamically allocated description string  

2. **Program functionality**  
   The program presents a **menu‑driven** interface (see the mandatory constraint about the exit option). The user can:  

   1. **Add a new cargo container**  
      * Prompt for `id`, `weight`, and a description (maximum 100 characters).  
      * Allocate a new `Cargo` element, store the data, and insert it into a dynamically‑sized array (use `realloc` to grow the array).  

   2. **Remove a cargo container**  
      * Prompt for the `id` of the container to delete.  
      * Locate the container in the array, free the memory used for its description, shift the remaining elements to fill the gap, and shrink the array with `realloc`.  
      * If the `id` does not exist, display an appropriate message.  

   3. **Display a specific container**  
      * Prompt for an `id`.  
      * Locate the container and invoke a function called `displayCargo` (see constraints) to print its details.  

   4. **List all containers**  
      * Print a table of every stored container, using `displayCargo` for each entry.  

   5. **Exit the program**  
      * Free all allocated memory (both the description strings and the array itself) and terminate.  

3. **User interaction**  
   * The menu must be displayed after each completed operation (except after exiting).  
   * Input should be read using standard I/O functions (`scanf`, `fgets`, etc.).  

## Example Input / Output  

```
=== ILA Cargo Manager ===
1) Add container
2) Remove container
3) Show container
4) List all containers
5) EXIT
Select an option: 1

Enter container ID: 101
Enter weight (kg): 250.5
Enter description: Oxygen tanks
Container added.

=== ILA Cargo Manager ===
1) Add container
2) Remove container
3) Show container
4) List all containers
5) EXIT
Select an option: 1

Enter container ID: 202
Enter weight (kg): 1200
Enter description: Food supplies
Container added.

=== ILA Cargo Manager ===
1) Add container
2) Remove container
3) Show container
4) List all containers
5) EXIT
Select an option: 4

ID: 101 | Weight: 250.50 kg | Description: Oxygen tanks
ID: 202 | Weight: 1200.00 kg | Description: Food supplies

=== ILA Cargo Manager ===
1) Add container
2) Remove container
3) Show container
4) List all containers
5) EXIT
Select an option: 3

Enter container ID to view: 101
ID: 101 | Weight: 250.50 kg | Description: Oxygen tanks

=== ILA Cargo Manager ===
1) Add container
2) Remove container
3) Show container
4) List all containers
5) EXIT
Select an option: 5

Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Cargo` as described above.  
2. **Display function** – The logic for printing the details of a single container must reside in a function with the exact prototype:  

   ```c
   void displayCargo(const Cargo *c);
   ```  

3. **Dynamic allocation only** – All memory for containers and their description strings must be obtained with `malloc`/`realloc` and released with `free`. No static or global arrays for the cargo list are allowed.  
4. **Menu requirement** – The program must present a menu and **option 5 must be the EXIT command** (as shown in the example). Selecting this option must free all allocated memory before terminating.  

---  

*Feel free to add minor usability enhancements (input validation, clear screen, etc.) as long as the mandatory constraints above are respected.*

---

## Problem 78 - openai/gpt-oss-120b - Iteration 23
# STEP 1: PROBLEM  

## Background  
You have been hired by **EcoTrack**, a startup that builds simple inventory‑tracking tools for small‑scale urban farms. Each farm keeps a list of **plant beds**. A plant bed has a *name* (e.g., “Tomato Bed”), a *capacity* (maximum number of plants it can hold), and the *current number of plants* that have been planted.  

Because farms may add or remove beds during the season, the program must allocate memory for each bed dynamically. When a bed is removed, its memory must be released.  

Your task is to write a console program that lets the user manage the collection of plant beds using a menu‑driven interface.

---

## Requirements  

1. **Data Representation**  
   - Define a `struct Bed` that contains:
     - `char *name;`   (dynamically allocated string)
     - `int capacity;`
     - `int planted;`

2. **Menu Options** (displayed repeatedly until the user chooses to exit)  
   1. **Add a new bed**  
      - Prompt for the bed name (a single word, up to 30 characters).  
      - Prompt for the capacity (positive integer).  
      - Initialise `planted` to `0`.  
      - Allocate memory for the `Bed` structure **and** for the name string, then store the new bed in a dynamically‑grown array of pointers to `Bed`.  
   2. **Remove a bed**  
      - Prompt for the bed name.  
      - Locate the bed, free the memory used for its name and for the `Bed` itself, and shrink the array accordingly.  
      - If the name does not exist, print an informative message.  
   3. **Plant in a bed**  
      - Prompt for the bed name and the number of plants to add.  
      - If the bed exists and the addition would not exceed `capacity`, update `planted`.  
      - Otherwise, print an error (e.g., “Not enough space”).  
   4. **Harvest from a bed**  
      - Prompt for the bed name and the number of plants to remove.  
      - If the bed exists and the removal does not make `planted` negative, update `planted`.  
      - Otherwise, print an error.  
   5. **Display a specific bed**  
      - Prompt for the bed name.  
      - Call a function `void displayBed(const Bed *b);` that prints the bed’s name, capacity, and current planted count.  
   6. **List all beds**  
      - Iterate over the array and call `displayBed` for each stored bed.  
   7. **EXIT**  
      - Terminate the program after freeing **all** remaining dynamically allocated memory.  

3. **Memory Management**  
   - Every `malloc`/`calloc` must have a matching `free`.  
   - The program must not leak memory when beds are removed or when the program exits.  

4. **Error Handling**  
   - Invalid menu choices should result in a polite “Invalid option” message and re‑display the menu.  
   - All numeric inputs must be validated to be positive integers where appropriate.  

---

## Example Interaction  

```
--- EcoTrack Plant Bed Manager ---
1) Add Bed
2) Remove Bed
3) Plant
4) Harvest
5) Display Bed
6) List All Beds
7) EXIT
Choose an option: 1
Enter bed name: Tomato
Enter capacity: 50
Bed "Tomato" added.

--- EcoTrack Plant Bed Manager ---
1) Add Bed
2) Remove Bed
3) Plant
4) Harvest
5) Display Bed
6) List All Beds
7) EXIT
Choose an option: 3
Enter bed name: Tomato
Plants to add: 20
20 plants added to "Tomato".

--- EcoTrack Plant Bed Manager ---
1) Add Bed
2) Remove Bed
3) Plant
4) Harvest
5) Display Bed
6) List All Beds
7) EXIT
Choose an option: 5
Enter bed name: Tomato
Bed: Tomato
Capacity: 50
Planted: 20

--- EcoTrack Plant Bed Manager ---
1) Add Bed
2) Remove Bed
3) Plant
4) Harvest
5) Display Bed
6) List All Beds
7) EXIT
Choose an option: 7
Goodbye!
```

---

### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented by a `struct Bed` as described.  
- **Display Function** – The logic for showing the details of a single bed **must** be encapsulated in a function named `void displayBed(const Bed *b);`.  
- **Menu Exit Option** – The menu **must** contain an explicit option (number 7) labeled `EXIT` that terminates the program.  
- **Single‑File Implementation** – All code must reside in one `.c` source file; you may define additional helper functions, but the `main` function should only coordinate the menu loop.  
- **Dynamic Array Management** – You may not use a fixed‑size array for the collection of beds; the array itself must be resized with `realloc` as beds are added or removed.  

---  

*Deliverables*: Source code (`.c` file) that compiles with a standard C compiler (e.g., `gcc -std=c11`) and conforms to the requirements and constraints above.

---

## Problem 79 - openai/gpt-oss-120b - Iteration 24
# STEP 1: PROBLEM  

## Background  
The university’s Student Services office maintains a simple in‑memory registry of **Club Memberships**. Each club has a name and a list of its members. The registry is rebuilt every time the program starts, so all data must be allocated dynamically (using `malloc`/`calloc`) and released before the program terminates.  

Your task is to implement a console program that lets a user **add clubs**, **add members to a club**, **display the members of a specific club**, and **remove a club** (which also frees all memory associated with its members).  

## Requirements  

1. **Data structures**  
   - Define a `struct Member` containing:  
     - `char *name` (dynamically allocated string)  
     - `int id` (unique within the club)  
   - Define a `struct Club` containing:  
     - `char *name` (dynamically allocated string)  
     - `Member *members` (dynamically allocated array of members)  
     - `size_t memberCount` (current number of members)  
     - `size_t capacity` (current allocated capacity of the members array)  

2. **Program functionality** (menu‑driven)  
   1. **Create a new club** – ask for the club name, allocate a `Club` object, and store it in a dynamic array of clubs.  
   2. **Add a member to a club** – ask for the club name, then for the member’s name and id. Expand the club’s members array as needed (use `realloc`).  
   3. **Display a club’s members** – ask for the club name and print all members (id and name). The printing logic must be inside a function called `displayClub`.  
   4. **Delete a club** – ask for the club name, free all memory belonging to that club (including each member’s name, the members array, and the club name), and remove the club from the clubs array (shifting later elements left).  
   5. **Exit** – free every remaining allocation and terminate the program.  

3. **User interaction** – The menu must be displayed after each operation until the user chooses the exit option.  

4. **Error handling** – If the user requests an operation on a non‑existent club, print an informative message and return to the menu.  

## Example Input / Output  

```
=== Club Registry Menu ===
1. Create a new club
2. Add a member to a club
3. Display members of a club
4. Delete a club
5. Exit
Enter choice: 1
Enter club name: ChessClub
Club 'ChessClub' created.

=== Club Registry Menu ===
1. Create a new club
2. Add a member to a club
3. Display members of a club
4. Delete a club
5. Exit
Enter choice: 2
Enter club name: ChessClub
Enter member name: Alice
Enter member id: 101
Member added to 'ChessClub'.

=== Club Registry Menu ===
1. Create a new club
2. Add a member to a club
3. Display members of a club
4. Delete a club
5. Exit
Enter choice: 3
Enter club name: ChessClub

Members of 'ChessClub':
ID: 101, Name: Alice

=== Club Registry Menu ===
1. Create a new club
2. Add a member to a club
3. Display members of a club
4. Delete a club
5. Exit
Enter choice: 5
Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

- **Struct usage** – The primary data entities must be represented with the `struct Member` and `struct Club` definitions as described.  
- **Display function** – The logic for printing the details of **ONE specific club** must be encapsulated in a function with the exact prototype:  

  ```c
  void displayClub(const Club *c);
  ```  

- **Memory management** – Every allocation performed with `malloc`, `calloc`, or `realloc` must have a matching `free` before the program terminates or when the associated club is deleted.  
- **Menu requirement** – The program must present a textual menu and **must include a specific menu option to EXIT the program** (option number 5 in the example). Selecting this option must trigger the final cleanup of all allocated memory.  

*Note: You may assume that input strings will not exceed 100 characters.*

---

## Problem 80 - openai/gpt-oss-120b - Iteration 25
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “student roster” utility for the campus computer lab.  
The lab administrator wants a command‑line program that can **add**, **remove**, **list**, and **search** for students while the program is running.  
Because the number of students is not known in advance, the program must allocate and release memory dynamically using `malloc` and `free`.  

## Program Requirements  

1. **Data representation**  
   * Define a `struct Student` that contains:  
     * an integer `id` (unique identifier)  
     * a dynamically allocated string `name` (maximum length 100 characters)  
     * a float `gpa`  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  

| Option | Description |
|--------|-------------|
| 1      | Add a new student |
| 2      | Delete a student by `id` |
| 3      | Display information of a student by `id` |
| 4      | List all stored students (in the order they were added) |
| 5      | Exit the program |

3. **Functional details**  

   * **Add** – Prompt for `id`, `name`, and `gpa`. Allocate a new `Student` object and store a copy of the name using `malloc`. Reject the addition if an existing student already has the same `id`.  
   * **Delete** – Locate the student with the given `id`. If found, free the memory used for the name and the `Student` structure itself, then remove the entry from the internal collection. If not found, print an appropriate message.  
   * **Display** – Locate the student with the given `id` and print all of its fields. The printing logic must be placed in a function called `displayStudent(const Student *s)`.  
   * **List** – Iterate over all stored students and invoke `displayStudent` for each.  
   * **Exit** – Before terminating, free **all** memory that has been allocated during the program’s execution.  

4. **Internal storage** – Use a dynamically resizable array (e.g., an array of `Student*` that grows with `realloc`) or a linked list; the exact data structure is up to you, but it must be built with dynamic allocation only (no static arrays of fixed size).

## Example Interaction  

```
=== Student Roster Menu ===
1. Add student
2. Delete student
3. Show student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 101
Enter name: Alice Johnson
Enter GPA: 3.85
Student added.

=== Student Roster Menu ===
1. Add student
2. Delete student
3. Show student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 102
Enter name: Bob Smith
Enter GPA: 3.42
Student added.

=== Student Roster Menu ===
1. Add student
2. Delete student
3. Show student
4. List all students
5. Exit
Choose an option: 4
ID: 101, Name: Alice Johnson, GPA: 3.85
ID: 102, Name: Bob Smith, GPA: 3.42

=== Student Roster Menu ===
1. Add student
2. Delete student
3. Show student
4. List all students
5. Exit
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice Johnson, GPA: 3.85

=== Student Roster Menu ===
1. Add student
2. Delete student
3. Show student
4. List all students
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Student` as described above.  
* **Display function** – The logic for printing a single student's details must be isolated in a function with the exact prototype:  
  ```c
  void displayStudent(const Student *s);
  ```  
* **Dynamic allocation only** – All memory for students and their names must be obtained with `malloc`/`realloc` and released with `free`. No global or static arrays of fixed size are permitted.  
* **Menu requirement** – The program must present a menu as shown, and **option 5 must be the explicit “Exit” choice** that terminates the program.  
* **Memory cleanup** – Before exiting, the program must free every block of memory it allocated (including names, student structures, and any auxiliary containers).  

---  

*Your task is to write a complete C program that satisfies the above specifications.*

---

## Problem 81 - openai/gpt-oss-120b - Iteration 26
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science department wants a simple command‑line tool to keep track of **lab equipment** that is loaned to students. Each piece of equipment has a unique identifier, a description, and the name of the student who currently has it (or “None” if it is in the storage room). The department’s teaching assistants have just learned how to allocate and free memory with `malloc`/`free`, and they need to write a program that stores an arbitrary number of equipment records at run‑time.

## Requirements  

Your program must:

1. **Maintain a collection of equipment records** that can grow or shrink while the program runs.  
2. **Present a menu** to the user with the following options (the numbers are mandatory):  
   1. **Add a new equipment record** – the user supplies the identifier (integer), description (string, up to 50 characters), and the borrower’s name (string, up to 30 characters; type “None” if the item is not borrowed).  
   2. **Remove an equipment record** – the user supplies the identifier; the program deletes that record and frees its memory.  
   3. **Display a specific equipment record** – the user supplies the identifier; the program prints all fields of that record.  
   4. **List all equipment records** – the program prints every stored record in the order they were added.  
   5. **Exit** – terminates the program (this option **must** be present).  

3. **Validate input**:  
   * If the user tries to add a record with an identifier that already exists, print an error and do not add a duplicate.  
   * If the user tries to remove or display a record that does not exist, print an appropriate message.  

4. **Use dynamic memory** (`malloc`/`realloc`/`free`) to store the collection; the program must not impose a fixed upper limit on the number of records.  

5. **Free all allocated memory** before exiting.

## Example Interaction  

```
=== Lab Equipment Manager ===
1) Add equipment
2) Remove equipment
3) Display equipment
4) List all equipment
5) Exit
Choose an option: 1
Enter ID: 101
Enter description: Arduino Uno
Enter borrower name (or None): Alice
Equipment added.

=== Lab Equipment Manager ===
1) Add equipment
2) Remove equipment
3) Display equipment
4) List all equipment
5) Exit
Choose an option: 1
Enter ID: 202
Enter description: Raspberry Pi 4
Enter borrower name (or None): None
Equipment added.

=== Lab Equipment Manager ===
1) Add equipment
2) Remove equipment
3) Display equipment
4) List all equipment
5) Exit
Choose an option: 3
Enter ID to display: 101
ID: 101
Description: Arduino Uno
Borrower: Alice

=== Lab Equipment Manager ===
1) Add equipment
2) Remove equipment
3) Display equipment
4) List all equipment
5) Exit
Choose an option: 4
--- All Equipment ---
ID: 101 | Description: Arduino Uno | Borrower: Alice
ID: 202 | Description: Raspberry Pi 4 | Borrower: None

=== Lab Equipment Manager ===
1) Add equipment
2) Remove equipment
3) Display equipment
4) List all equipment
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct` named `Equipment` containing at least the fields `int id; char description[51]; char borrower[31];`.  
* **Function Requirement** – The logic for displaying the details of **one specific** equipment record **must** be placed in a function with the exact prototype:  

  ```c
  void displayEquipment(const Equipment *e);
  ```  

* **Modular Design** – Apart from `main`, you must implement **exactly three additional functions**:  
  1. `void addEquipment(Equipment **list, size_t *count);`  
  2. `void removeEquipment(Equipment **list, size_t *count);`  
  3. `void displayEquipment(const Equipment *e);`  

  (You may create static helper functions inside those files, but the public interface must consist of only these four functions.)  

* **Menu Exit Option** – The menu **must** include option **5) Exit** (or the keyword `EXIT`) and selecting it ends the program after freeing all memory.  

* **No Global Variables** – All data must be passed explicitly via parameters; global variables are not allowed.  

* **Standard Library Only** – You may only include `<stdio.h>`, `<stdlib.h>`, and `<string.h>`. No third‑party libraries.  

---  

Write the program in C, adhering to the above specifications. The assessment will check for correct dynamic allocation, proper freeing of memory, correct handling of the menu, and compliance with the listed constraints.

---

## Problem 82 - openai/gpt-oss-120b - Iteration 27
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Track**, a startup that monitors the growth of trees in a city park. Each tree is identified by a unique **Tree ID** and has two associated measurements: the **height** (in centimeters) and the **diameter** of its trunk (in millimetres).  

The park’s sensors send data to the program one tree at a time. Because the number of trees is not known in advance and can change while the program runs (trees may be added or removed), the program must allocate and release memory dynamically.

## Requirements  

Write a C program that lets the user manage a collection of trees using a **menu‑driven interface**. The program must support the following operations:

1. **Add a new tree**  
   - Prompt the user for the Tree ID (an integer), height, and trunk diameter.  
   - Allocate memory for a new `struct Tree` and store the information.  
   - Insert the new tree at the end of the current list.

2. **Remove a tree**  
   - Prompt the user for a Tree ID.  
   - Search the list; if the tree exists, remove it from the list and `free` its memory.  
   - If the Tree ID is not found, display an appropriate message.

3. **Display a tree’s data**  
   - Prompt the user for a Tree ID.  
   - Locate the tree and print its ID, height, and diameter.  
   - If the tree does not exist, inform the user.

4. **Display all trees**  
   - Print the data of every tree currently stored, in the order they were added.  
   - If the list is empty, print a message indicating that.

5. **Exit**  
   - Terminate the program after freeing any memory that is still allocated.

The menu must be displayed after each operation (except after the user selects **Exit**).

## Example Interaction  

```
=== Eco‑Track Tree Manager ===
1) Add a tree
2) Remove a tree
3) Display a tree
4) Display all trees
5) Exit
Select an option: 1
Enter Tree ID: 101
Enter height (cm): 215
Enter trunk diameter (mm): 45
Tree added.

=== Eco‑Track Tree Manager ===
1) Add a tree
2) Remove a tree
3) Display a tree
4) Display all trees
5) Exit
Select an option: 1
Enter Tree ID: 102
Enter height (cm): 180
Enter trunk diameter (mm): 38
Tree added.

=== Eco‑Track Tree Manager ===
1) Add a tree
2) Remove a tree
3) Display a tree
4) Display all trees
5) Exit
Select an option: 3
Enter Tree ID to display: 101
Tree ID: 101, Height: 215 cm, Diameter: 45 mm

=== Eco‑Track Tree Manager ===
1) Add a tree
2) Remove a tree
3) Display a tree
4) Display all trees
5) Exit
Select an option: 4
Tree ID: 101, Height: 215 cm, Diameter: 45 mm
Tree ID: 102, Height: 180 cm, Diameter: 38 mm

=== Eco‑Track Tree Manager ===
1) Add a tree
2) Remove a tree
3) Display a tree
4) Display all trees
5) Exit
Select an option: 5
Good‑bye!
```

## ### CONSTRAINTS  

1. **Data Structure** – The primary entity must be represented with a `struct` named `Tree` containing at least the fields `id`, `height`, and `diameter`.  

2. **Dynamic Allocation** – All `Tree` objects must be allocated with `malloc` (or `calloc`) and released with `free`. No static or global arrays of fixed size may be used to store the trees.  

3. **Modular Design** –  
   - The logic for displaying the details of **one specific tree** must be placed in a function with the exact prototype:  
     ```c
     void displayTree(const struct Tree *t);
     ```  
   - The logic for removing a tree must be placed in a function with the prototype:  
     ```c
     int removeTree(struct Tree **head, int id);
     ```  
     (return `1` on success, `0` if the ID was not found).  

4. **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option number `5` as shown in the example). Selecting this option must cause the program to free any remaining allocated memory before terminating.  

5. **Memory Safety** – The program must not leak memory; every `malloc`/`calloc` must have a matching `free` before the program ends.  

6. **Standard Library Only** – Only headers from the C Standard Library may be used (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are allowed.  

---

## Problem 83 - openai/gpt-oss-120b - Iteration 28
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “library catalog” program for a small community library. The library keeps information about each book in memory only while the program runs. Because the number of books is not known ahead of time, you must allocate and free memory dynamically as books are added or removed.

Each book is described by three fields:

* **ISBN** – a 13‑character string (e.g., `"9780131103627"`).  
* **Title** – a string of up to 100 characters.  
* **Year** – the year of publication (integer).

Your task is to implement a menu‑driven application that lets the user add books, list all books, search for a book by ISBN, delete a book, and finally exit the program. All book records must be stored in dynamically allocated memory, and any memory that is no longer needed must be released with `free`.

## Requirements  

1. **Menu** – Upon start, display a menu with the following options (the numbers are mandatory):  
   1. Add a new book  
   2. List all books  
   3. Find a book by ISBN  
   4. Delete a book by ISBN  
   5. EXIT  

2. **Add a new book**  
   * Prompt the user for ISBN, Title, and Year.  
   * Allocate a `struct Book` dynamically with `malloc`.  
   * Store the data in the newly allocated struct and add a pointer to it at the end of a dynamic array (the array itself must also be managed with `malloc`/`realloc`).  

3. **List all books**  
   * Iterate over the dynamic array and print the details of every stored book, one per line.  

4. **Find a book by ISBN**  
   * Ask the user for an ISBN.  
   * Search the array; if a matching book is found, display its details using the required function `displayEntity`.  
   * If not found, print “Book not found.”  

5. **Delete a book by ISBN**  
   * Ask the user for an ISBN.  
   * Locate the matching book. If found, free the memory for that `struct Book`, remove its pointer from the array (shift later elements left), and shrink the array with `realloc`.  
   * If the ISBN does not exist, print “Book not found.”  

6. **EXIT**  
   * Before terminating, free **all** remaining dynamically allocated memory (both the individual `struct Book`s and the array that holds their pointers).  

7. The program must continue to display the menu after each operation until the user selects the EXIT option.

## Example Input / Output  

```
=== Library Catalog ===
1. Add a new book
2. List all books
3. Find a book by ISBN
4. Delete a book by ISBN
5. EXIT
Choose an option: 1

Enter ISBN (13 chars): 9780131103627
Enter Title: The C Programming Language
Enter Year: 1978
Book added successfully!

=== Library Catalog ===
1. Add a new book
2. List all books
3. Find a book by ISBN
4. Delete a book by ISBN
5. EXIT
Choose an option: 2

--- Book List ---
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1978

=== Library Catalog ===
1. Add a new book
2. List all books
3. Find a book by ISBN
4. Delete a book by ISBN
5. EXIT
Choose an option: 3

Enter ISBN to search: 9780131103627
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1978

=== Library Catalog ===
1. Add a new book
2. List all books
3. Find a book by ISBN
4. Delete a book by ISBN
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Book` containing the three fields described above.  
* **Display Function** – The logic for displaying the details of **one** specific book must be placed in a function with the exact prototype:  
  ```c
  void displayEntity(const struct Book *b);
  ```  
* **Memory Management** – Every allocation performed with `malloc`/`realloc` must have a corresponding `free` before the program terminates.  
* **Menu Exit Option** – The menu must include the option **5. EXIT** (or the keyword `EXIT`) that terminates the program, as shown in the required menu list.  

*Optional (but recommended for style)*: Keep all other helper functions (e.g., for adding, searching, deleting) separate from `main`. The only mandatory extra function is `displayEntity`.

---

## Problem 84 - openai/gpt-oss-120b - Iteration 29
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small command‑line utility for the university’s **Student Records Office**.  
The office keeps a list of currently enrolled students in memory while the program runs.  
Because the number of students is not known in advance, the list must be created using **dynamic memory allocation** (`malloc`, `realloc`, `free`).  

Each student record contains:  

* a unique integer **ID**  
* a **name** (maximum 30 characters, no spaces)  
* a **GPA** (floating‑point number between 0.0 and 4.0)  

The program should allow the user to add new students, remove a student by ID, view the details of a single student, and list all stored students.  

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Student` that stores the three fields listed above.  

2. **Dynamic List**  
   * Maintain the collection of students in a **dynamically allocated array** that can grow or shrink as students are added or removed.  
   * Use `malloc`/`realloc` to adjust the array size and `free` to release memory before the program terminates.  

3. **Menu‑Driven Interface** (the program must present a textual menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a student** – Prompt for ID, name, and GPA, then store the new record. |
   | 2 | **Remove a student** – Prompt for an ID; if a student with that ID exists, delete the record and shrink the array. |
   | 3 | **Display a student** – Prompt for an ID; if found, show the student’s details. |
   | 4 | **List all students** – Print the details of every stored student in the order they were added. |
   | 5 | **Exit** – Terminate the program (this option must be present). |

4. **Input Validation**  
   * IDs must be positive integers and unique; if a duplicate ID is entered, print an error and reject the insertion.  
   * GPA must be in the range `[0.0, 4.0]`; otherwise, print an error and reject the insertion.  

5. **Memory Management**  
   * When a student is removed, shift the remaining elements so that the array stays contiguous.  
   * After the user selects **Exit**, free all allocated memory before returning from `main`.  

6. **Function Requirements**  
   * Implement a function `void displayStudent(const struct Student *s);` that prints a single student’s information in the format shown in the example.  
   * All other logic may be placed in `main` or additional helper functions, but the `displayStudent` function **must** be used whenever a single student’s details are shown.  

---

## Example Interaction  

```
--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 101
Enter name: Alice
Enter GPA: 3.7
Student added.

--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 102
Enter name: Bob
Enter GPA: 3.2
Student added.

--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 3
Enter ID to display: 101
ID: 101, Name: Alice, GPA: 3.70

--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 4
ID: 101, Name: Alice, GPA: 3.70
ID: 102, Name: Bob,   GPA: 3.20

--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 2
Enter ID to remove: 101
Student removed.

--- Student Records Menu ---
1. Add a student
2. Remove a student
3. Display a student
4. List all students
5. Exit
Choose an option: 5
Goodbye!
```

*Note:* The exact wording of prompts is not graded; only the required functionality and correct use of dynamic memory matter.

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Student`.  
* **Display Function** – The details of a single student must be printed by a function named `displayStudent`.  
* **Menu Exit** – The menu must contain an explicit option (number **5**) to exit the program.  
* **Dynamic Allocation Only** – The student list must be stored in a dynamically allocated array; using a fixed‑size static array is not allowed.  
* **Memory Clean‑up** – All memory allocated with `malloc`/`realloc` must be released with `free` before the program ends.  

---

## Problem 85 - openai/gpt-oss-120b - Iteration 30
# STEP 1: PROBLEM  

## Background  
A small community library wants a simple console program to keep track of the books it owns while the semester is in session.  
The library staff will manually enter information about each book, view the details of a particular book, and remove a book when it is retired.  
Because the number of books is not known in advance and can change during execution, the program must allocate and free memory dynamically.

## Requirements  

Write a **menu‑driven** C program that manages a collection of books. Each book has the following attributes:  

| Field | Type | Description |
|-------|------|-------------|
| `title` | string (max 100 characters) | The title of the book |
| `author` | string (max 100 characters) | Author’s name |
| `year` | `int` | Publication year |
| `pages` | `int` | Number of pages |

The program must support the following operations (selected by the user from a menu):  

1. **Add a new book** – Prompt the user for the four fields, allocate memory for a new `Book` structure with `malloc`, store the data, and insert the book at the end of the current collection.  
2. **Display a book** – Ask the user for the *title* of the book to view. Search the collection; if the book exists, call a function `displayBook` to print all its fields in a readable format. If the book is not found, print an appropriate message.  
3. **Remove a book** – Ask the user for the *title* of the book to delete. Locate the book, remove it from the collection, free the memory that was allocated for that `Book`, and shift the remaining pointers so that the collection stays contiguous. If the book does not exist, inform the user.  
4. **List all books** – Print the details of every book currently stored, using `displayBook` for each entry.  
5. **Exit** – Terminate the program after freeing all remaining allocated memory.

The program should continue to display the menu after completing any operation until the user chooses the **Exit** option.

## Example Interaction  

```
=== Library Book Manager ===
1) Add a new book
2) Display a book
3) Remove a book
4) List all books
5) Exit
Select an option: 1

Enter title: The C Programming Language
Enter author: Brian Kernighan and Dennis Ritchie
Enter year: 1988
Enter pages: 274
Book added successfully.

=== Library Book Manager ===
1) Add a new book
2) Display a book
3) Remove a book
4) List all books
5) Exit
Select an option: 2

Enter title to display: The C Programming Language
--- Book Details ---
Title : The C Programming Language
Author: Brian Kernighan and Dennis Ritchie
Year  : 1988
Pages : 274

=== Library Book Manager ===
1) Add a new book
2) Display a book
3) Remove a book
4) List all books
5) Exit
Select an option: 5
Goodbye!
```

If the user tries to display or remove a title that is not in the collection, the program should output, e.g.:

```
Book with title "Unknown Title" not found.
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity must be a `struct` named `Book` that contains the four fields listed above.  
2. **Dynamic Allocation** – Every time a new book is added, memory for that `Book` must be obtained with `malloc`. When a book is removed, its memory must be released with `free`. All remaining allocated memory must be freed before the program terminates.  
3. **Display Function** – The logic for printing the details of **one** book must reside in a separate function with the exact prototype:  

   ```c
   void displayBook(const Book *b);
   ```  

4. **Menu Requirement** – The program must present a menu as shown in the example. The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option ends the program after cleaning up all allocated resources.  
5. **Single Source File** – The entire solution must be placed in one `.c` file; you may define additional helper functions, but the `main` function must contain the menu loop.  
6. **No Global Dynamic Arrays** – The collection of books must be stored as a dynamically‑allocated array of pointers (`Book **catalog`) that can grow as books are added. You may use `realloc` to resize the array, but you must never access memory that has not been allocated.  

Follow these constraints closely; they are part of the grading rubric.

---

## Problem 86 - llama-3.3-70b-versatile - Iteration 31
# STEP 1: PROBLEM
You are a curator of a museum, and you want to manage the collection of artifacts using a dynamic memory allocation system. The museum has a variety of artifacts, each with a unique name, description, and acquisition year. Your task is to design a program that allows you to add, remove, and display artifacts.

The program should have the following functionality:
1. Add an artifact to the collection: The program should prompt the user to enter the name, description, and acquisition year of the artifact.
2. Remove an artifact from the collection: The program should prompt the user to enter the name of the artifact to be removed.
3. Display all artifacts in the collection: The program should display the name, description, and acquisition year of each artifact.
4. Display the details of a specific artifact: The program should prompt the user to enter the name of the artifact and then display its details.

### CONSTRAINTS
- The solution must use a `struct` to represent an artifact, with members for name, description, and acquisition year.
- The logic for displaying the details of one specific artifact must be in a function called `displayArtifact`.
- The program must have a menu-driven interface with the following options:
  1. Add an artifact
  2. Remove an artifact
  3. Display all artifacts
  4. Display a specific artifact
  5. EXIT the program
- The program must use dynamic memory allocation (`malloc` and `free`) to manage the collection of artifacts.

### EXAMPLE INPUT/OUTPUT
```
Museum Artifact Management System
1. Add an artifact
2. Remove an artifact
3. Display all artifacts
4. Display a specific artifact
5. EXIT

Enter your choice: 1
Enter artifact name: Ancient Vase
Enter artifact description: A vase from ancient Greece
Enter artifact acquisition year: 2010

Museum Artifact Management System
1. Add an artifact
2. Remove an artifact
3. Display all artifacts
4. Display a specific artifact
5. EXIT

Enter your choice: 3
Artifact 1:
Name: Ancient Vase
Description: A vase from ancient Greece
Acquisition Year: 2010

Museum Artifact Management System
1. Add an artifact
2. Remove an artifact
3. Display all artifacts
4. Display a specific artifact
5. EXIT

Enter your choice: 4
Enter artifact name: Ancient Vase
Name: Ancient Vase
Description: A vase from ancient Greece
Acquisition Year: 2010
```

---

## Problem 87 - llama-3.3-70b-versatile - Iteration 32
# STEP 1: PROBLEM
You are the manager of a small library that lends books to its members. The library has a collection of books, and you want to create a program to manage the book collection. The program should allow you to add, remove, and display books. Since the number of books is not fixed, you will use dynamic memory allocation to store the book information.

The program should have the following functionality:
1. Add a book to the collection: The program should prompt the user to enter the book's title, author, and publication year.
2. Remove a book from the collection: The program should prompt the user to enter the title of the book to be removed.
3. Display all books in the collection: The program should display the title, author, and publication year of each book in the collection.
4. Display the details of a specific book: The program should prompt the user to enter the title of the book and then display the book's details.

### CONSTRAINTS
- Must use a 'struct' to represent a book, which should have members for title, author, and publication year.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu options should be:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 3
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 4
Enter book title: Harry Potter
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT

Enter your choice: 5
Exiting the program...
```

---

## Problem 88 - llama-3.3-70b-versatile - Iteration 33
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a simple program. The program should allow the librarian to add, remove, and display books. Each book has a title, author, and publication year. The program should use dynamic memory allocation to store the books.

The librarian wants the program to have the following functionalities:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all the books in the collection.
4. Display the details of a specific book by its title.

Here's a simple example of expected input/output:
- Add a book: "Harry Potter" by "J.K. Rowling" (2000)
- Add a book: "The Lord of the Rings" by "J.R.R. Tolkien" (1954)
- Display all books:
  - "Harry Potter" by "J.K. Rowling" (2000)
  - "The Lord of the Rings" by "J.R.R. Tolkien" (1954)
- Display book "Harry Potter":
  - Title: Harry Potter
  - Author: J.K. Rowling
  - Year: 2000
- Remove book "The Lord of the Rings"
- Display all books:
  - "Harry Potter" by "J.K. Rowling" (2000)

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The program must have a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT the program
- The program must free all the allocated memory before exiting.

Note: The menu option to EXIT the program is option 5.

---

## Problem 89 - llama-3.3-70b-versatile - Iteration 34
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The program should be able to dynamically allocate memory for each book as it is added to the library. The librarian wants to store information such as the book's title, author, and publication year.

The program should allow the librarian to add books, display all books, and search for a specific book by title. The librarian also wants to be able to remove a book from the library, which should deallocate the memory used by that book.

### REQUIREMENTS
1. The program should use dynamic memory allocation (malloc, free) to store the books.
2. The program should have a menu with the following options:
   - Add a book
   - Display all books
   - Search for a book by title
   - Remove a book
   - Exit the program
3. The program should validate user input to ensure that the publication year is a valid integer and the title and author are not empty.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a book
2. Display all books
3. Search for a book by title
4. Remove a book
5. Exit the program
Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter publication year: 1997
Book added successfully!

Menu:
1. Add a book
2. Display all books
3. Search for a book by title
4. Remove a book
5. Exit the program
Choose an option: 2
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```

### CONSTRAINTS
- The solution must use a `struct` to represent a book, which should have members for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for searching for a specific book by title must be in a function called `searchBookByTitle`.
- The program must include a menu option to EXIT the program, which should be option 5.
- If a menu is implemented, the program should continue to run and display the menu until the user chooses to exit (option 5).

---

## Problem 90 - llama-3.3-70b-versatile - Iteration 35
# STEP 1: PROBLEM
You are the manager of a library, and you need to create a system to manage the books in the library. The system should allow you to dynamically add and remove books from the library. Each book has a unique title, author, and publication year.

The system should have the following functionality:
1. Add a new book to the library: The system should prompt the user for the title, author, and publication year of the book, and then add the book to the library.
2. Remove a book from the library: The system should prompt the user for the title of the book to remove, and then remove the book from the library if it exists.
3. Display all books in the library: The system should display the title, author, and publication year of all books in the library.
4. Display the details of a specific book: The system should prompt the user for the title of the book, and then display the title, author, and publication year of the book if it exists.

Here is a simple example of expected input/output:
```
Library Management System
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

Choose an option: 1
Enter book title: Book1
Enter book author: Author1
Enter publication year: 2020

Choose an option: 3
Book1 by Author1 (2020)

Choose an option: 4
Enter book title: Book1
Book1 by Author1 (2020)
```

### CONSTRAINTS
- The solution must be implemented using dynamic memory allocation (malloc, free) to store the books.
- Must use a 'struct' to represent a book, with members for title, author, and publication year.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The system should have a menu with the above options, and the user should be able to exit the program by choosing option 5 (EXIT).
- The system should handle memory leaks by freeing the memory allocated for each book when it is removed from the library.

---

## Problem 91 - llama-3.3-70b-versatile - Iteration 36
# STEP 1: PROBLEM
You are the administrator of a university's library system, responsible for managing the catalog of books. The library has a large collection, and the catalog is constantly being updated with new books being added and old ones being removed. To efficiently manage this catalog, you decide to create a program that utilizes dynamic memory allocation to store and manipulate the book records.

The program should allow users to add new books, remove existing books, and display the details of all books or a specific book. Each book record consists of a unique book ID, title, author, and publication year.

### REQUIREMENTS
1. The program must be able to dynamically allocate memory for each new book record added by the user.
2. The program must allow users to add new book records.
3. The program must allow users to remove existing book records by book ID.
4. The program must be able to display the details of all book records.
5. The program must be able to display the details of a specific book record by book ID.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add Book
2. Remove Book
3. Display All Books
4. Display Book by ID
5. EXIT

Choose an option: 1
Enter Book ID: 1
Enter Book Title: Introduction to CS
Enter Author: John Doe
Enter Publication Year: 2020

Choose an option: 3
Book ID: 1, Title: Introduction to CS, Author: John Doe, Year: 2020

Choose an option: 2
Enter Book ID to remove: 1

Choose an option: 3
No books in the catalog.

Choose an option: 5
Exiting the program...
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called `displayBook`.
3. The solution must be implemented with a single function besides `main()` to handle the menu and user input, called `handleMenu`.
4. The program must include a specific menu option to EXIT the program, which is option 5 (EXIT).

---

## Problem 92 - llama-3.3-70b-versatile - Iteration 37
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. The library has a collection of books, and each book has a unique title, author, and publication year. You want to create a program to manage the library's collection of books using dynamic memory allocation.

The program should allow you to add books to the collection, remove books from the collection, and display the details of all books in the collection. The program should also allow you to search for a book by its title and display its details.

Here is a precise list of requirements for the program's functionality:
1. The program should allow the user to add a book to the collection by providing the title, author, and publication year.
2. The program should allow the user to remove a book from the collection by providing the title of the book.
3. The program should allow the user to display the details of all books in the collection.
4. The program should allow the user to search for a book by its title and display its details.

Here is a simple example of expected input/output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 1
Enter title: Book1
Enter author: Author1
Enter publication year: 2020

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 3
Book1 by Author1 (2020)

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 4
Enter title: Book1
Book1 by Author1 (2020)
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input, called `handleMenu`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.
- All dynamically allocated memory must be freed before the program exits to prevent memory leaks.

---

## Problem 93 - llama-3.3-70b-versatile - Iteration 38
# STEP 1: PROBLEM
You are the manager of a small bookstore, and you want to create a simple inventory management system to keep track of the books in your store. The system should allow you to add, remove, and display book details.

Background:
The bookstore has a limited amount of memory to store information about the books. You want to use dynamic memory allocation to efficiently manage the memory usage. Each book has a title, author, and price.

Requirements:
1. The program should allow users to add a new book to the inventory.
2. The program should allow users to remove a book from the inventory by its title.
3. The program should display the details of all books in the inventory.
4. The program should have a menu-driven interface to interact with the user.

### CONSTRAINTS
* Must use a 'struct' to represent a book, with members 'title', 'author', and 'price'.
* Logic for displaying the details of all books must be in a function called 'displayBooks'.
* The solution must be implemented with a single function besides main() to handle the memory management and menu options.
* If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

Example:
Input:
```
1. Add Book
2. Remove Book
3. Display Books
4. Search Book
5. Exit
Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book price: 15.99

Choose an option: 3
```
Output:
```
Book Title: Harry Potter
Book Author: J.K. Rowling
Book Price: $15.99
```
Note: The program should handle memory allocation and deallocation correctly to avoid memory leaks. The menu options should be displayed to the user, and the user's input should be handled accordingly.

---

## Problem 94 - llama-3.3-70b-versatile - Iteration 39
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. To efficiently manage the collection, you want to create a program that uses dynamic memory allocation to store and retrieve book information.

The program should allow users to add, remove, and display books in the collection. Each book has a title, author, and publication year.

## REQUIREMENTS:
1. The program should allow users to add a new book to the collection.
2. The program should allow users to remove a book from the collection by its title.
3. The program should display all books in the collection.
4. The program should display the details of a specific book by its title.

## EXAMPLE INPUT/OUTPUT:
```
Add a book:
Title: "To Kill a Mockingbird"
Author: "Harper Lee"
Publication Year: 1960

Remove a book:
Title: "To Kill a Mockingbird"

Display all books:
Title: "1984", Author: "George Orwell", Publication Year: 1949
Title: "Pride and Prejudice", Author: "Jane Austen", Publication Year: 1813

Display a specific book:
Title: "1984"
Title: "1984", Author: "George Orwell", Publication Year: 1949
```

### CONSTRAINTS:
1. Must use a `struct` to represent a book, with members for title, author, and publication year.
2. Logic for displaying the details of one specific book must be in a function called `displayBook`.
3. The solution must implement a menu-driven interface with the following options:
   - Add a book (Option 1)
   - Remove a book (Option 2)
   - Display all books (Option 3)
   - Display a specific book (Option 4)
   - EXIT the program (Option 5)
4. The program must use dynamic memory allocation (`malloc` and `free`) to manage the collection of books.

Note: The program should handle memory deallocation when a book is removed or when the program exits.

---

## Problem 95 - llama-3.3-70b-versatile - Iteration 40
# STEP 1: PROBLEM
You are the administrator of a university's library system, tasked with managing the inventory of books. The library has a large collection of books, and you need to develop a program to efficiently manage the catalog. The program should utilize dynamic memory allocation to store and retrieve information about each book.

The program should allow users to add, remove, and display books in the catalog. Each book has a unique title, author, publication year, and ISBN (International Standard Book Number).

### REQUIREMENTS
1. The program should dynamically allocate memory for each book added to the catalog.
2. The program should allow users to add a new book by providing its title, author, publication year, and ISBN.
3. The program should allow users to remove a book by its ISBN.
4. The program should allow users to display all books in the catalog.
5. The program should allow users to search for a book by its title or author.

### EXAMPLE
Input:
```
Add a book:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020
ISBN: 1234567890

Add a book:
Title: Data Structures and Algorithms
Author: Jane Doe
Publication Year: 2019
ISBN: 9876543210

Display all books:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020
ISBN: 1234567890

Title: Data Structures and Algorithms
Author: Jane Doe
Publication Year: 2019
ISBN: 9876543210
```
Output:
```
Books in the catalog:
1. Introduction to Computer Science by John Smith (2020) - 1234567890
2. Data Structures and Algorithms by Jane Doe (2019) - 9876543210
```

### CONSTRAINTS
1. Must use a `struct` to represent a book, containing its title, author, publication year, and ISBN.
2. The logic for displaying the details of a book must be in a function called `displayBook`.
3. The solution must be implemented with a menu-driven interface.
4. The menu should include the following options:
   - Add a book (option 1)
   - Remove a book (option 2)
   - Display all books (option 3)
   - Search for a book (option 4)
   - Exit the program (option 5)
5. The program must free all dynamically allocated memory before exiting.

### MANDATORY CONSTRAINTS FOR MENU
- The program must include a specific menu option to EXIT the program (option 5).
- The program should continue to run and display the menu until the user chooses to exit (option 5).

---

## Problem 96 - llama-3.3-70b-versatile - Iteration 41
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a simple program. The program should allow the librarian to add, remove, and display books. Each book has a title, author, and publication year. The librarian wants to be able to dynamically allocate memory for each book and free the memory when a book is removed.

The program should have the following functionality:
1. Add a new book: The program should prompt the user to enter the title, author, and publication year of the book. It should then dynamically allocate memory for the new book and store the information.
2. Remove a book: The program should prompt the user to enter the title of the book to be removed. It should then find the book in the list, free the memory allocated for the book, and remove it from the list.
3. Display all books: The program should display the title, author, and publication year of all books in the list.
4. Display a specific book: The program should prompt the user to enter the title of the book and then display the title, author, and publication year of the book.

### EXAMPLE
Input:
```
Add a new book
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
Add a new book
Title: The Lord of the Rings
Author: J.R.R. Tolkien
Publication Year: 1954
Display all books
```
Output:
```
Harry Potter by J.K. Rowling (1997)
The Lord of the Rings by J.R.R. Tolkien (1954)
```
### CONSTRAINTS
- Must use a `struct` to represent a book.
- The solution must be implemented with a menu-driven approach.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- The logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The program should handle memory allocation and deallocation using `malloc` and `free` respectively. 

Note: The program should be able to handle a variable number of books and should not have a predefined limit on the number of books.

---

## Problem 97 - llama-3.3-70b-versatile - Iteration 42
# STEP 1: PROBLEM
In a library management system, books are the primary entities that need to be tracked. Each book has a title, author, publication year, and a unique identifier (ISBN). The library wants to create a simple program to manage its book collection using dynamic memory allocation. 

The program should allow users to add books, display all books, search for a book by ISBN, and remove a book by ISBN. The library also wants to ensure that the program handles memory efficiently by freeing unused memory when a book is removed.

### REQUIREMENTS
1. The program should have a menu-driven interface.
2. The user should be able to add a new book with its details (title, author, publication year, and ISBN).
3. The user should be able to display all the books in the collection.
4. The user should be able to search for a book by its ISBN and display its details if found.
5. The user should be able to remove a book by its ISBN.
6. The program should handle memory deallocation when a book is removed.

### EXAMPLE
If the user adds two books:
- Book 1: Title = "Book1", Author = "Author1", Year = 2020, ISBN = "12345"
- Book 2: Title = "Book2", Author = "Author2", Year = 2021, ISBN = "67890"

The program should display both books when the user chooses to display all books. If the user searches for a book with ISBN "12345", it should display the details of "Book1". If the user removes the book with ISBN "12345", it should deallocate the memory used by "Book1" and only display "Book2" when the user chooses to display all books.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The program must implement a menu with the following options:
  1. Add a book
  2. Display all books
  3. Search for a book by ISBN
  4. Remove a book by ISBN
  5. EXIT the program
- The program must use dynamic memory allocation (malloc, free) to manage the book collection.
- The EXIT option should be clearly labeled as "5. EXIT" in the menu, and it should free all allocated memory before terminating the program.

---

## Problem 98 - llama-3.3-70b-versatile - Iteration 43
# STEP 1: PROBLEM
In a university setting, a simple library management system is needed to track the books available for students. The system should be able to dynamically add or remove books as they are borrowed or returned. The details of each book include its title, author, and availability status.

The system should provide the following functionalities:
1. Add a new book to the library.
2. Remove a book from the library.
3. Display all the books in the library.
4. Display the details of a specific book.
5. Exit the program.

### CONSTRAINTS
- Must use a `struct` to represent a book, which includes the title, author, and availability status.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation (`malloc`, `free`) to manage the books.
- If a menu is implemented, it must include the following options:
  - Option 1: Add a new book.
  - Option 2: Remove a book.
  - Option 3: Display all books.
  - Option 4: Display a specific book.
  - Option 5: Exit the program. The program exits when the user chooses Option 5.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book.
2. Remove a book.
3. Display all books.
4. Display a specific book.
5. Exit the program.

Choose an option: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Book added successfully.

Choose an option: 3
Book 1:
Title: Introduction to CS
Author: John Doe
Available: Yes

Choose an option: 4
Enter book title to display: Introduction to CS
Book:
Title: Introduction to CS
Author: John Doe
Available: Yes

Choose an option: 5
Exiting the program.
```
This problem requires students to apply their understanding of dynamic memory allocation to manage a collection of books in a simple library management system.

---

## Problem 99 - llama-3.3-70b-versatile - Iteration 44
# STEP 1: PROBLEM
You are the administrator of a library, and you want to manage the collection of books using a C program. The library has a large number of books, and you want to store the details of each book in memory dynamically. You will use dynamic memory allocation to store the book details.

The library has the following requirements for the program:
1. The program should allow you to add a new book to the collection.
2. The program should allow you to display the details of all books in the collection.
3. The program should allow you to search for a specific book by its title.
4. The program should allow you to remove a book from the collection.

Here's a simple example of the expected input/output:
```
Enter your choice:
1. Add a book
2. Display all books
3. Search for a book
4. Remove a book
5. Exit

You choose: 1
Enter book title: Harry Potter
Enter author: J.K. Rowling
Enter year: 1997

You choose: 2
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Year: 1997
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
- The program must have a menu with the following options:
  1. Add a book
  2. Display all books
  3. Search for a book
  4. Remove a book
  5. Exit
- The menu option to exit the program is option 5. 
- The solution must implement dynamic memory allocation using malloc and free to manage the book collection.

---

## Problem 100 - llama-3.3-70b-versatile - Iteration 45
# STEP 1: PROBLEM
You are the manager of a bookstore, and you want to create a simple inventory management system to keep track of the books in your store. The system should allow you to add, remove, and display books.

Background:
The bookstore sells books of various genres, and each book has a title, author, price, and quantity in stock. You want to create a program that can efficiently manage the inventory of books.

Requirements:
1. The program should allow users to add a new book to the inventory.
2. The program should allow users to remove a book from the inventory if it exists.
3. The program should allow users to display all the books in the inventory.
4. The program should allow users to search for a book by title or author.

### CONSTRAINTS
* Must use a 'struct' to represent a book with fields for title, author, price, and quantity.
* Logic for displaying the details of all books must be in a function called 'displayBooks'.
* The solution must be implemented with a menu-driven approach.
* The menu should have the following options:
	1. Add a new book
	2. Remove a book
	3. Display all books
	4. Search for a book
	5. EXIT (to exit the program)
* The program should use dynamic memory allocation (malloc, free) to manage the memory for the books.

Example Input/Output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book price: 20.00
Enter book quantity: 10

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 3

Book Title: Harry Potter
Book Author: J.K. Rowling
Book Price: $20.00
Book Quantity: 10

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Search for a book
5. EXIT

Enter your choice: 5
```
Note: The program should handle memory allocation and deallocation properly to avoid memory leaks.

---

