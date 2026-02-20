# Problem Batch Preview: Dynamic Memory Allocation (malloc, free)
**Batch Number:** 1 | **Total Problems:** 100

---

## Problem 1 - moonshotai/kimi-k2-instruct-0905 - Iteration 61
# STEP 1: PROBLEM

## Background Story
The university library is digitizing its card-catalogue.  
Your task is to write a tiny, throw-away program that lets the librarian type in book records one-by-one.  
Each record is kept only while the program is running; when the librarian chooses to exit, every record must be released and the program must terminate cleanly.

## Functional Requirements
1. The program repeatedly shows a menu:
   1) Add a new book  
   2) List all books  
   3) Delete the last added book (LIFO)  
   4) Exit  
2. “Add” prompts for: title (≤80 chars), author (≤50 chars), year (integer).  
3. “List” prints every book currently stored, in the order they were added.  
4. “Delete” removes the most recently added book and frees its memory.  
5. Choosing “Exit” (menu option 4) frees every remaining book and ends the program.

## Example Session
```
1) Add  2) List  3) Delete-last  4) Exit
Choice: 1
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1978
Book added.

1) Add  2) List  3) Delete-last  4) Exit
Choice: 2
1. The C Programming Language - Kernighan & Ritchie (1978)

1) Add  2) List  3) Delete-last  4) Exit
Choice: 3
Last book removed.

1) Add  2) List  3) Delete-last  4) Exit
Choice: 4
Good-bye.
```

### CONSTRAINTS
- You must use a single struct to represent a book.  
- All dynamic allocations (malloc) and de-allocations (free) must be explicit—no memory leaks.  
- The only additional function allowed besides main() is displayBook(struct Book *b), which prints a single book in the format shown in the example.

---

## Problem 2 - moonshotai/kimi-k2-instruct-0905 - Iteration 62
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)  

## Background  
The university library has bought a huge box of index cards for a “mini‐catalogue.”  
Instead of throwing the cards away, the librarian wants you to digitize them.  
Each card contains exactly three strings: title, author, and ISBN.  
Because the librarian does not know how many cards will be in the box, your program must allocate exactly the amount of memory needed, no more, no less.

## Functional Requirements  
1. The program starts by asking for the number of cards (n).  
2. Allocate a contiguous block of memory for n cards.  
3. For each card, read the title, author, and ISBN (all single‐line strings, max 100 chars each).  
4. Implement a menu loop with the following options:  
   1) Display all cards  
   2) Search for a card by ISBN  
   3) Exit  
5. Option 1 prints every card, one per line, in the order stored.  
6. Option 2 reads an ISBN. If a card with that ISBN exists, print its details; otherwise print “ISBN not found.”  
7. Option 3 frees all memory and terminates the program with “Good‐bye!”  
8. If the user enters an invalid menu choice, print “Invalid choice.” and re‐show the menu.

## Example Session (user input in bold)  
```
How many cards? 2
Card 1
  Title: Clean Code
  Author: Robert C. Martin
  ISBN: 9780132350884
Card 2
  Title: The C Programming Language
  Author: Kernighan & Ritchie
  ISBN: 9780131103627

Menu:
1) Display all
2) Search by ISBN
3) Exit
Choice: 2
Enter ISBN: 9780132350884
Title: Clean Code, Author: Robert C. Martin, ISBN: 9780132350884

Menu:
1) Display all
2) Search by ISBN
3) Exit
Choice: 1
1. Clean Code | Robert C. Martin | 9780132350884
2. The C Programming Language | Kernighan & Ritchie | 9780131103627

Menu:
1) Display all
2) Search by ISBN
3) Exit
Choice: 3
Good-bye!
```

### CONSTRAINTS  
- Must use a single `struct` to represent a single card.  
- Must allocate the array of cards with one call to `malloc` and free it with one call to `free`.  
- The logic for displaying the details of ONE specific card must be in a function called `displayCard`.  
- The only functions allowed besides `main` are `displayCard` and any helper functions strictly necessary for the menu loop.  
- Menu option **3** is the only way to exit the program; typing **3** must free memory and terminate.

---

## Problem 3 - moonshotai/kimi-k2-instruct-0905 - Iteration 63
# STEP 1: PROBLEM

## Background Story  
The campus library has just gone “fine-free,” but they still need a way to keep track of who has which book.  
You volunteer to write a tiny, memory-only checkout system that starts empty, grows as books are checked out, and shrinks as they are returned.  
All data must live on the heap so the program can run for the entire semester without ever knowing in advance how many books will pass through.

## Functional Requirements  
1. Represent a book with:  
   - 13-digit ISBN (string, exactly 13 chars + null terminator)  
   - Title (dynamically allocated string of any length)  
   - Borrower’s student ID (unsigned int)  
2. Store every *currently* checked-out book in a single, contiguous, dynamically allocated array.  
3. Provide a menu-driven interface:  
   1. Check-out (add) a book  
   2. Return (remove) a book by ISBN  
   3. List all checked-out books  
   4. Exit  
4. After every add or remove operation, the array must be resized *exactly* to the current number of books (no slack, no fragmentation).  
5. If the user tries to remove a non-existent ISBN, print `Not found.` and leave the array unchanged.  
6. On exit, free every byte of heap memory (array and every title string).

## Simple Example Session  
(user input shown after `>`)

```
1
>9781234567890
>The C Programming Language
>12345
2
>9781234567890
1
>9781111111111
>Python Crash Course
>12345
3
4
```

Expected Output

```
1
Title: The C Programming Language, ISBN: 9781234567890, Student: 12345
Title: Python Crash Course, ISBN: 9781111111111, Student: 12345
Good-bye!
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (a Book).  
- Logic for displaying the details of ONE specific Book must be in a function called `displayBook`.  
- The solution must be implemented with a single function besides `main()` (you may add `displayBook`; everything else lives in that one helper).  
- Menu option 4 is the EXIT keyword.

---

## Problem 4 - moonshotai/kimi-k2-instruct-0905 - Iteration 64
# STEP 1: PROBLEM

## Background Story
The campus library has just gone “digital-only” for its CD collection.  
Staff members are typing the titles into a simple terminal program, but they have no idea how many discs will arrive.  
Your job is to write a tiny inventory tool that grows the list as each CD is scanned and shrinks it when a CD is withdrawn.

## Requirements
1. The program starts with an empty list of CDs.
2. The user repeatedly chooses one of three actions:
   - `1` – Add a new CD  
     *Prompt for:* title (≤30 characters), artist (≤30 characters), and an integer year.  
     *Store the data in dynamically allocated memory* and append it to the list.
   - `2` – Remove a CD by its exact title (case-sensitive).  
     If the title is found, free its memory and compact the list; otherwise print `CD not found.`
   - `3` – List all CDs in the order they were added.  
     Format: `Title — Artist (year)`
   - `0` – Exit the program (free all remaining memory before terminating).
3. Handle an arbitrary number of CDs; do not declare a fixed-size array.
4. After every command, re-display the menu unless the user chose `0`.

## Simple Example Run
```
1
Title: Nevermind
Artist: Nirvana
Year: 1991
1
Title: Back in Black
Artist: AC/DC
Year: 1980
3
Nevermind — Nirvana (1991)
Back in Black — AC/DC (1980)
2
Title to remove: Nevermind
3
Back in Black — AC/DC (1980)
0
```
(Program ends; all memory freed.)

### CONSTRAINTS
- Must use a `struct` to represent one CD.
- All dynamic allocation must be done with `malloc`; every successful `malloc` must eventually be matched by `free`.
- Logic for displaying the details of ONE specific CD must be in a function called `displayCD`.
- The entire solution must be implemented with **only one** additional function besides `main()` (you may choose any name for that function).
- Menu option `0` must be the EXIT option.

---

## Problem 5 - moonshotai/kimi-k2-instruct-0905 - Iteration 65
# STEP 1: PROBLEM

## Context
The campus library is testing a new self–service kiosk that lets students borrow books without staff help.  
Every time a student borrows a book, the kiosk must remember the book’s title, the student’s ID, and the due‐date.  
Because the number of simultaneous checkouts is unpredictable, the system must store this data in dynamically-allocated memory.

## Requirements
Write a C program that behaves like the kiosk’s back-end.  
The program must:

1. Keep an expandable array of pointers (`Book **catalog`) that point to individually allocated `Book` structures.
2. Support two commands entered by the user:
   - `add <title> <student_id> <days>`  
     Allocate a new `Book`, store the title, student ID, and a due-date computed as “today + days”, append its address to the catalog, and print the catalog index at which it was stored.
   - `return <catalog_index>`  
     Free the `Book` at that index, set its pointer to `NULL`, and print `Returned`.  
     If the index is invalid or the slot is already empty, print `Invalid`.
3. Stop accepting commands when the user types `exit`.
4. Just before terminating, print the total number of books currently checked-out (non-NULL entries).

## Example Session
```
Input
add C_Programming 12345 14
add Data_Structures 12345 7
return 0
exit

Output
0
1
Returned
1
```

## Explanation
- First `add` stores the book at catalog[0] and prints `0`.  
- Second `add` stores the next book at catalog[1] and prints `1`.  
- `return 0` frees catalog[0] and prints `Returned`.  
- `exit` prints the final count of outstanding books: `1`.

### CONSTRAINTS
- You must represent a book with a `struct Book` containing at least `char *title`, `int student_id`, and `int due_days`.
- All dynamic allocations (`malloc`) must be matched by exactly one `free`.  
- The logic that displays the final count must reside in a function `void showOutstanding(Book **catalog, int size)`.  
- The only functions allowed besides `main()` are `showOutstanding` and any helper you need for string duplication.  
- If you implement an interactive menu, option `3` must be “Exit the program”.

---

## Problem 6 - moonshotai/kimi-k2-instruct-0905 - Iteration 66
# STEP 1: PROBLEM

**Background Story**  
The campus library has just bought a small, unnamed server that only supports plain C.  
They need a tiny “checkout-log” program that can remember, at runtime, which books a patron has borrowed.  
Because the server has very little RAM, the program must allocate memory only when a new book is added, and free it immediately when the book is returned.

**Functional Requirements**  
1. The program keeps a dynamic array of structures, one structure per currently-checked-out book.  
2. At start-up the array is empty (size 0).  
3. The user can repeatedly choose one of three actions:  
   - **1** Add a newly-borrowed book (title, author, year).  
   - **2** Return (delete) the newest book in the log.  
   - **3** Exit the program.  
4. After every action the program must print the current number of books still checked out.  
5. If the user tries to delete when the log is empty, print “Nothing to return.” and leave the count at 0.

**Simple Example**  
Input
```
1
C_Programming_Language
Kernighan
1978
1
Introduction_to_Algorithms
Cormen
2009
2
3
```
Output
```
Books in log: 1
Books in log: 2
Books in log: 1
Good-bye.
```

### CONSTRAINTS  
- Represent each book with a `struct Book`.  
- Store the dynamic array itself as `struct Book *log`.  
- You may have only one function besides `main()`: `void displayCount(int n);` that prints “Books in log: n”.  
- Menu option **3** is the required EXIT keyword.

---

## Problem 7 - moonshotai/kimi-k2-instruct-0905 - Iteration 67
# STEP 1: PROBLEM

## Context (Story)
You are helping the campus library build a tiny, self-contained catalog system for its new “Pop-Up Reading Corner.”  
Because the corner only exists for the weekend, the librarian wants the catalog to live entirely in RAM and disappear when the program ends.  
All book records must therefore be allocated dynamically with malloc and freed with free when they are no longer needed.

## Functional Requirements
1. The program starts with an empty catalog (no books).
2. It supports a single-character menu loop:
   - `A` – Add a new book  
   - `L` – List all books currently in the catalog  
   - `D` – Delete (remove & free) the most recently added book  
   - `X` – Exit the program (and free any remaining memory before quitting)
3. Adding a book prompts the user for:
   - Title (one line, up to 99 characters, may contain spaces)
   - Author (one line, up to 99 characters)
   - Year (positive integer)
4. Listing prints every book in the order they were added, one per line, in the exact format:
   ```
   Year: <year>, Title: "<title>", Author: <author>
   ```
5. Deleting removes the last-added book from memory; if the catalog is empty, print `Nothing to delete.` and return to the menu.

## Simple Example Run
```
=== Pop-Up Reading Corner Catalog ===
A) Add book
L) List books
D) Delete last book
X) Exit
Choice: A
Title: The Little Prince
Author: Antoine de Saint-Exupéry
Year: 1943
Choice: A
Title: Dune
Author: Frank Herbert
Year: 1965
Choice: L
Year: 1943, Title: "The Little Prince", Author: Antoine de Saint-Exupéry
Year: 1965, Title: "Dune", Author: Frank Herbert
Choice: D
Choice: L
Year: 1943, Title: "The Little Prince", Author: Antoine de Saint-Exupéry
Choice: X
Goodbye!
```

## CONSTRAINTS
- Each book must be represented by a struct named `Book`.
- The catalog must be implemented as a dynamically-sized array of pointers to `Book`, resized with `realloc` as books are added.
- All dynamic memory (every `Book` struct and the array itself) must be freed before the program exits.
- The menu option to exit the program is `X`.
- No global variables are allowed; keep all data inside `main()` or pass it as parameters.

---

## Problem 8 - moonshotai/kimi-k2-instruct-0905 - Iteration 68
# STEP 1: PROBLEM

## Context
You are helping the university library build a tiny “digital shelf” for new arrivals.  
Each book has: title, author, and year.  
Because the collection grows and shrinks every day, the program must keep its data on the heap, not in fixed-size arrays.

## Requirements
1. The program starts with an empty collection.
2. It repeatedly shows this menu:
   ```
   1) Add a new book
   2) Remove the last added book
   3) List all books
   4) Exit
   ```
3. Choosing 1 prompts for title, author, and year, then stores the book on the heap.
4. Choosing 2 deletes the most recently added book (like popping a stack) and frees its memory.
5. Choosing 3 prints every book in the order they were added, one per line, with a single space between fields:
   ```
   C_Programming_Language Kernighan 1978
   ```
6. After each operation the menu re-appears until the user chooses 4.
7. On Exit the program must free every remaining book before terminating.

## Example Run
```
1) Add a new book
2) Remove the last added book
3) List all books
4) Exit
Choice: 1
Title: C_Programming_Language
Author: Kernighan
Year: 1978
Choice: 1
Title: Clean_Code
Author: Martin
Year: 2008
Choice: 3
C_Programming_Language Kernighan 1978
Clean_Code Martin 2008
Choice: 2
Choice: 3
C_Programming_Language Kernighan 1978
Choice: 4
```

### CONSTRAINTS
- You must store each book in a struct named Book allocated with malloc.
- You must implement exactly one extra function besides main(): void displayBook(const struct Book *b) which prints one book in the required format.
- The user must type 4 to exit the program.

---

## Problem 9 - moonshotai/kimi-k2-instruct-0905 - Iteration 69
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)  

## Background Story  
The campus library is throwing away its old card-catalog drawers. Each drawer contains a variable number of index cards that list a book’s call number and title.  
You volunteer to digitize one drawer at a time. Your program will let the user type in as many cards as they like, store them in dynamic memory, and then re-print the whole catalog on request. When the user is done, the program must release every byte it allocated before exiting.

## Functional Requirements  
1. Read an arbitrary number of book entries from standard input until the user types the single word `END` as the call number.  
   - Each entry is two lines:  
     a. Call number (string, max 19 characters, may contain spaces).  
     b. Title (string, max 79 characters, may contain spaces).  
2. Store every entry in dynamically allocated memory; do **not** use global or fixed-size arrays.  
3. After input is complete, print the entire drawer back to the user in the same order, numbered starting at 1.  
4. After printing, free every block you allocated and exit gracefully.

## Simple Example  
**Input**  
```
PQ2678.I44 A16 1990  
L'Étranger  
END  
```

**Output**  
```
1. PQ2678.I44 A16 1990 - L'Étranger  
```

## CONSTRAINTS  
- You must represent each book with a `struct` that contains at least two members: the call number and the title.  
- You must allocate the `struct` itself and the two strings inside it with separate `malloc` calls (three allocations per book).  
- The only functions besides `main()` allowed are:  
  - `struct Book *readBook(void)` – reads one book from stdin, allocates memory, returns pointer or `NULL` if `END` is entered.  
  - `void displayCatalog(struct Book **catalog, int count)` – prints the entire catalog.  
- You are not allowed to use `realloc`; grow the catalog manually.  
- If a menu is implemented (not required here), it must contain an option to EXIT the program (type `0` to exit).

---

## Problem 10 - moonshotai/kimi-k2-instruct-0905 - Iteration 70
# STEP 1: PROBLEM

## Context  
The university’s robotics club keeps its spare parts in an old storage room. Every week the treasurer buys a few new items and writes down their cost and quantity on sticky notes. At the end of the month the club wants to see how much money is tied up in each part and in total. You have volunteered to write a tiny inventory tracker that can grow as new parts arrive.

## Requirements  
1. The program must start by asking how many *different* parts were bought this month (0 ≤ n ≤ 100).  
2. It must then allocate exactly enough dynamic memory to store information for those n parts.  
3. For every part the program must read:  
   - an integer ID (positive, unique within this run)  
   - a string of up to 29 printable characters for the part name (no spaces)  
   - an integer quantity (≥ 0)  
   - a double unit price (≥ 0)  
4. After all parts are stored, the program must print:  
   - a neat table listing ID, name, quantity, unit price, and total cost (=quantity×price) for every part  
   - the grand total money tied up in inventory (sum of all total costs)  
5. Before exiting the program must free every byte of dynamically allocated memory.

## Example run  
```
How many parts? 3
Part 1: id name qty unitPrice
101 wheels 4 2.50
Part 2: id name qty unitPrice
102 servo 10 5.00
Part 3: id name qty unitPrice
103 frame 1 12.00
ID   Name     Qty  Price  Total
101  wheels   4    2.50   10.00
102  servo   10    5.00   50.00
103  frame    1   12.00   12.00
Grand total: 72.00
```

### CONSTRAINTS  
- You must define a single `struct` called `Part` that contains the four data fields described above.  
- All parts must be stored in a single dynamically allocated array obtained with one call to `malloc`.  
- You must provide a function `void displayPart(const struct Part *p)` that prints the details of one part in the format shown in the example (one line of the table).  
- The only other function allowed besides `main` is `displayPart`.

---

## Problem 11 - moonshotai/kimi-k2-instruct-0905 - Iteration 71
# STEP 1: PROBLEM

**Background Story**  
You are the night-shift manager of the campus “Print-Anywhere” shop.  
Students bring USB sticks with PDFs; each PDF must be stored in memory until the printer is free.  
Because RAM is tight, you will dynamically allocate exactly the number of bytes each PDF needs and free them as soon as the job is printed.  
Your supervisor has asked for a tiny C program that keeps track of the current print queue.

**Task**  
Write a program that:

1. Keeps a linked list of pending print jobs.  
2. Each job holds:  
   - an `id` (positive int, unique inside one run)  
   - a `name` (one-word string ≤30 chars)  
   - the PDF’s `size` in bytes (positive int)  
   - a pointer to the next job.  
3. Provides a text menu with the following choices:  
   1. Add new job  
   2. Print (remove) the first job  
   3. Display queue  
   4. Exit (terminates the program)  

4. On “Add new job” the program must:  
   - read id, name, size  
   - allocate a new struct node (`malloc`)  
   - append it to the tail of the list.  

5. On “Print” the program must:  
   - remove the head job, print its id & name  
   - free its memory (`free`)  
   - if the queue is empty, print “Queue empty”.  

6. On “Display queue” print the id, name and size of every job in order, one per line.  

**Simple Example Session (user input after ‘> ’)**  
```
1
> 101 report.pdf 24000
1
> 102 slides.pdf 1500000
3
101 report.pdf 24000
102 slides.pdf 1500000
2
Printing: 101 report.pdf
2
Queue empty
4
```
The program terminates.

### CONSTRAINTS  
- The primary data entity must be represented by a `struct`.  
- All dynamic allocations (`malloc`) and de-allocations (`free`) must be explicit; no global arrays.  
- The logic that prints the details of exactly one job must be placed in a function called `displayJob`.  
- The menu option to EXIT the program is `4`.

---

## Problem 12 - moonshotai/kimi-k2-instruct-0905 - Iteration 72
# STEP 1: PROBLEM

**Topic:** Dynamic Memory Allocation (malloc, free)

**Background Story**  
You are a volunteer inventory keeper for a small neighborhood food‐bank.  
Every week, donors drop off bags of non‐perishable food.  
Each bag is labeled with a unique ID (positive integer) and the net weight (in kilograms).  
You need a simple program that keeps track of these bags in memory, allowing you to add new bags, delete a bag by ID, and list the current inventory.  
Because the number of bags changes every week, you must store them in dynamically‐allocated memory.

**Program Requirements**  
1. On startup, the program must start with an empty inventory.  
2. Implement a text menu with the following options:  
   1) Add a new bag  
   2) Delete a bag by ID  
   3) List all bags  
   4) Exit  
3. “Add a new bag” must prompt for a unique ID (positive int) and a weight (positive double).  
   - Reject duplicate IDs and ask again.  
4. “Delete a bag by ID” must free the memory of that bag and compact the array.  
5. “List all bags” must print each bag’s ID and weight on its own line, in the order stored.  
6. The program must release all dynamically‐allocated memory before exiting.

**Simple Example Run**  
```
=== Food-Bank Inventory ===
1) Add bag
2) Delete bag
3) List bags
4) Exit
Choice: 1
Enter bag ID: 101
Enter weight (kg): 3.5
Bag added.

Choice: 1
Enter bag ID: 102
Enter weight (kg): 2.0
Bag added.

Choice: 3
Bag ID: 101, Weight: 3.5 kg
Bag ID: 102, Weight: 2.0 kg

Choice: 2
Enter bag ID to delete: 101
Bag deleted.

Choice: 3
Bag ID: 102, Weight: 2.0 kg

Choice: 4
Good-bye!
```

### CONSTRAINTS
1. Must use a `struct` to represent each bag.  
2. Logic for displaying the details of ONE specific bag must be in a function called `displayBag`.  
3. The solution must be implemented with a single function besides `main()` (that one function may do all operations or you may call it with different flags; `displayBag` is allowed as a separate tiny helper).  
4. Menu option 4 is the required EXIT keyword.

---

## Problem 13 - moonshotai/kimi-k2-instruct-0905 - Iteration 73
# STEP 1: PROBLEM

## Background Story
The campus library has just upgraded its old card-catalogue to a tiny C program that lets students “check-out” and “return” e-books.  
Each book is represented only by its title (≤80 chars) and a flag telling whether it is currently borrowed.  
The librarian types commands into a menu-driven console.  
All book records must live in dynamic memory (malloc/free) so the catalogue can grow or shrink while the program runs.

## Functional Requirements
1. On start-up the program has an empty catalogue (no books).
2. The program repeatedly shows a menu:
   1. Add new book
   2. Borrow book
   3. Return book
   4. List all books
   5. Remove book
   6. Exit
3. “Add new book” reads a title and stores the book as *not borrowed*.
4. “Borrow book” reads a title and marks that book borrowed **only if it exists and is not already borrowed**.
5. “Return book” reads a title and marks it *not borrowed* **only if it exists and is currently borrowed**.
6. “List all books” prints every book’s title and status (AVAILABLE / BORROWED).
7. “Remove book” deletes a book record from memory (free its heap block) **only if it exists and is not currently borrowed**.
8. After every command the menu re-appears until the user chooses “Exit”.
9. Choosing “Exit” frees every remaining book record and terminates the program.

## Simple Example Run
(“>” denotes user input; program output is unmarked)

```
1. Add new book
2. Borrow book
3. Return book
4. List all books
5. Remove book
6. Exit
> 1
Enter title: C Programming
1. Add new book
2. Borrow book
3. Return book
4. List all books
5. Remove book
6. Exit
> 4
C Programming - AVAILABLE
1. Add new book
2. Borrow book
3. Return book
4. List all books
5. Remove book
6. Exit
> 2
Enter title: C Programming
Book borrowed.
1. Add new book
2. Borrow book
3. Return book
4. List all books
5. Remove book
6. Exit
> 6
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a book).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.  
- Must include menu option 6 to EXIT the program.

---

## Problem 14 - moonshotai/kimi-k2-instruct-0905 - Iteration 74
# STEP 1: PROBLEM

## Context
The campus library has just gone “book-return” digital.  
Every time a student returns a book, the system must store the book’s title, the student’s ID, and the due-date.  
Because the number of returns is unknown in advance, the records must be kept in dynamically-allocated memory that grows on demand.

## Requirements
1. On start-up the program allocates space for exactly one return record.
2. Repeatedly read commands from stdin:
   - `ADD` *title* *studentID* *dueDate*  
     (add a new return record; if the current array is full, double its capacity using `realloc`)
   - `LIST`  
     (print every record on a single line in the order: title,studentID,dueDate)
   - `EXIT`  
     (free all heap memory and terminate)
3. Assume no line will exceed 100 characters, studentID is an integer, and dueDate is a string in the form DD-MM-YYYY.
4. If `ADD` is called after `EXIT`, the program must ignore it (it has already ended).

## Simple Example
Input
```
ADD Introduction_to_C 12345 15-05-2024
ADD Data_Structures 12346 16-05-2024
LIST
EXIT
```
Output
```
Introduction_to_C,12345,15-05-2024
Data_Structures,12346,16-05-2024
```

### CONSTRAINTS
- Represent each return record with a `struct`.
- The logic that prints a single record must be encapsulated in a function called `displayRecord`.
- The only functions allowed besides `main()` are: `displayRecord`, plus any memory-management helpers you need (but no extra menu-related functions).
- Menu option to EXIT the program is the keyword `EXIT`.

---

## Problem 15 - moonshotai/kimi-k2-instruct-0905 - Iteration 75
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a new “Tech-for-Rent” kiosk that lets students borrow electronic devices (graphing calculators, phone chargers, VR viewers, etc.).  
All gadgets are stored in a single locked case.  
At opening time the librarian places every device into numbered slots (slot 1 … slot *n*).  
Students take an available device from the lowest-numbered slot, and when they return it the device is always placed back into the *highest-numbered empty* slot.  
Your task is to write a tiny “device-desk” program that keeps track of which slots are occupied and which are free.

## Functional Requirements
1. At start-up the program reads one positive integer *n* (≤ 1000) that tells how many slots the case contains.  
2. It then repeatedly reads single-character commands from standard input:
   - `B` → **Borrow** the lowest-numbered free slot.  
     - If at least one slot is free, print the borrowed slot number and mark it occupied.  
     - If every slot is full, print `No free slots`.
   - `R` → **Return** a device.  
     - The next integer on the same line is the slot number that is being returned.  
     - If that slot was actually occupied, mark it free and print `Slot #k returned`.  
     - If the slot was already free or is out of range, print `Invalid return`.
   - `E` → **Exit** the program immediately.

3. All memory that describes the slots must be allocated dynamically with `malloc`/`free`.  
4. No global variables may be used; every piece of data lives on the heap.

## Simple Example
### Input
```
5
B
B
R 1
B
E
```

### Output
```
1
2
Slot #1 returned
2
```

## Explanation
- Initial capacity is 5 (slots 1–5).  
- First two `B` commands borrow slots 1 and 2.  
- `R 1` returns slot 1; the next `B` again finds slot 1 the lowest free, so it is re-issued.

### CONSTRAINTS
- You must store the slots using a dynamically allocated array (via `malloc`).  
- You must free that array before the program exits.  
- You must use a `struct` named `SlotCase` that contains at least the pointer to the array and its size.  
- All command processing must be done in a single function `processCommand(struct SlotCase *, char cmd, int param)`; `main` is the only other function allowed.

---

## Problem 16 - moonshotai/kimi-k2-instruct-0905 - Iteration 76
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old magazine collection.  
Your task is to write a tiny “Magazine Manager” that lets a librarian type-in new magazine issues, list them, or remove an issue when it is donated elsewhere.  
All data must live in dynamic memory (the librarian may stop entering at any moment), and everything must be released before the program ends.

## Functional Requirements
1. The program starts with an empty collection of magazine issues.
2. Present a menu with four options:
   1. Add Issue
   2. List All Issues
   3. Remove Issue
   4. Exit
3. “Add Issue” prompts for title (one word, ≤30 chars), issue number (positive int), and year (positive int).  
   Store the new issue in dynamically allocated memory; keep it in a linked list.
4. “List All Issues” prints every magazine currently stored, one per line, in the order they were added.  
   If the collection is empty, print “Collection is empty.”
5. “Remove Issue” asks for the issue number.  
   If found, free its memory and splice it out of the list; otherwise print “Issue not found.”
6. “Exit” frees every remaining node and terminates the program.

## Simple Example Run
```
1. Add Issue
2. List All Issues
3. Remove Issue
4. Exit
Choice: 1
Title: BYTE
Issue #: 12
Year: 1984
Choice: 1
Title: Wired
Issue #: 7
Year: 1995
Choice: 2
BYTE #12 (1984)
Wired #7 (1995)
Choice: 3
Issue #: 12
Choice: 2
Wired #7 (1995)
Choice: 4
```

### CONSTRAINTS
- Must use a struct to represent a Magazine issue.  
- All list nodes must be dynamically allocated with malloc and released with free.  
- Logic for displaying the details of ONE specific Magazine must be in a function called displayMagazine.  
- The menu option to EXIT the program is 4.

---

## Problem 17 - moonshotai/kimi-k2-instruct-0905 - Iteration 77
# STEP 1: PROBLEM

## Background Story
The campus library has just replaced its old index-card checkout system with a tiny computer that only runs C programs.  
Because memory is tight, the librarian wants a program that keeps track of who has borrowed which book, but allocates space only when a book is actually checked out and immediately frees it when the book is returned.

## Functional Requirements
1. The program must keep a dynamic list of currently checked-out books.
2. Each record must store:
   - an integer catalog number (unique within the list)
   - the book title (≤60 characters)
   - the borrower’s name (≤30 characters)
3. The user can repeatedly enter one of the following commands:
   - `checkout <catalog#> "<title>" "<borrower>"`  
     – add a new checkout to the list (malloc a new record)
   - `return <catalog#>`  
     – remove that checkout and free its memory
   - `list`  
     – print every current checkout, one per line, in the order they were added
   - `exit`  
     – free all remaining memory and terminate the program
4. If a command is malformed or a catalog number is not found for `return`, the program must print `error` and continue.

## Simple Example
Input
```
checkout 42 "C Programming" "Alice"
checkout 7 "Operating Systems" "Bob"
list
return 7
list
return 42
list
exit
```

Output
```
42 "C Programming" Alice
7 "Operating Systems" Bob
42 "C Programming" Alice
error
```

### CONSTRAINTS
- You must use a `struct` to represent each checkout record.
- All memory for records must be allocated with `malloc` and released with `free`.
- The logic that prints a single record must be implemented in a function called `displayEntity`.
- The only functions allowed in your source file are `main` and `displayEntity`.
- The menu option to exit the program is the keyword `exit`.

---

## Problem 18 - moonshotai/kimi-k2-instruct-0905 - Iteration 78
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (`malloc`, `free`)

## Background Story  
You have just been hired as the volunteer “Ticket Librarian” for the town’s annual Book & Bake Festival.  
Your only tool is a simple C program that keeps track of the numbered tickets people purchase at the entrance.  
Because the total number of visitors is unknown in advance, you must store the tickets in dynamically-allocated memory and release that memory when it is no longer needed.

## Program Requirements  
1. On startup the program shows a tiny menu:  
   1. Issue new ticket  
   2. Return (delete) a ticket  
   3. Show all remaining tickets  
   4. Exit  
2. Choosing “Issue new ticket” prompts for the visitor’s name (one word, ≤30 chars) and automatically assigns the next available positive integer as the ticket number (start at 1).  
3. Choosing “Return a ticket” asks for the ticket number. If the ticket exists it is removed and its memory is freed; otherwise print “Ticket not found.”  
4. Choosing “Show all” prints every ticket in ascending numerical order, one per line, in the format  
   `Ticket #<number>: <name>`  
5. After every action (except Exit) redisplay the menu.  
6. On Exit, free all remaining dynamically-allocated memory and terminate.

## Simple Example Run  
```
1. Issue new ticket
2. Return a ticket
3. Show all tickets
4. Exit
Choice: 1
Name: Alice
Ticket #1 issued for Alice.

1. Issue new ticket
2. Return a ticket
3. Show all tickets
4. Exit
Choice: 1
Name: Bob
Ticket #2 issued for Bob.

1. Issue new ticket
2. Return a ticket
3. Show all tickets
4. Exit
Choice: 3
Ticket #1: Alice
Ticket #2: Bob

1. Issue new ticket
2. Return a ticket
3. Show all tickets
4. Exit
Choice: 2
Ticket number: 1
Ticket #1 returned.

1. Issue new ticket
2. Return a ticket
3. Show all tickets
4. Exit
Choice 4
Good-bye!
```

## CONSTRAINTS  
- You must use a `struct` to represent a ticket (at minimum: ticket number and owner name).  
- The logic for displaying a single ticket must be placed in a function called `displayTicket`.  
- The only functions allowed besides `main()` are:  
  - `displayTicket` (required)  
  - plus any helper functions you create for allocation/deallocation.

---

## Problem 19 - moonshotai/kimi-k2-instruct-0905 - Iteration 79
# STEP 1: PROBLEM

## Background Story
The campus library has a tiny “Memory-Only” shelf that can physically hold exactly N books.
When a student checks a book out, the librarian removes it from the shelf and gives it to the student.
When the book is returned, the librarian puts it back in the first empty slot.
Because the shelf is so small, the librarian keeps no paper records; the only record is an in-memory list of which slots are occupied and by which book.
Your task is to write a program that acts as the librarian’s assistant, dynamically allocating and freeing the slots.

## Requirements
1. The shelf capacity N (1 ≤ N ≤ 100) is read first.
2. The program then repeatedly reads commands from stdin:
   - `CHECKOUT <title>`  
     If at least one slot is free, the book is added to the first free slot and the program prints `Checked out: <title>`
     If the shelf is full, print `Shelf full - cannot checkout`
   - `RETURN <title>`  
     If the book is currently on the shelf, it is removed and the program prints `Returned: <title>`  
     If the book is not found, print `Book not found`
   - `LIST`  
     Print one line per occupied slot in the form  
     `Slot <k>: <title>`  
     slots are numbered 1..N.  If the shelf is empty, print `Shelf empty`
3. The program must stop when the command `EXIT` is read.

## Simple Example
Input
```
3
CHECKOUT Dune
CHECKOUT 1984
LIST
CHECKOUT Neuromancer
CHECKOUT SnowCrash
RETURN 1984
LIST
EXIT
```

Output
```
Checked out: Dune
Checked out: 1984
Slot 1: Dune
Slot 2: 1984
Checked out: Neuromancer
Shelf full - cannot checkout
Returned: 1984
Slot 1: Dune
Slot 3: Neuromancer
```

### CONSTRAINTS
- You must store each book in a `struct` called `Book` that contains at least the fields `char* title` and `int slot`.
- You must allocate and free all memory with `malloc`/`free`; no global or static arrays of books are allowed.
- All logic for displaying the shelf contents must be implemented in a single function `void displayShelf()`; `main()` is not allowed to contain any `printf` calls for the `LIST` command.
- The only additional function besides `main()` permitted is `displayShelf()`.

---

## Problem 20 - moonshotai/kimi-k2-instruct-0905 - Iteration 80
# STEP 1: PROBLEM

## Context
You are helping the campus library manage its small collection of e-books.  
Each e-book has a title (≤40 characters) and a size in MB (a positive double).  
The librarian wants a tiny console program that stores these e-books in dynamic memory and lets the user add, list, or delete them one at a time.

## Required Functionality
1. On start-up the program has room for 0 e-books; all memory is obtained with `malloc`/`realloc`.
2. Implement a menu that always appears after every action (except when the user exits):
   ```
   1 Add e-book
   2 List e-books
   3 Delete last e-book
   4 Exit
   ```
3. **Add** – read title and size; append the new e-book to the collection.
4. **List** – print the index, title and size of every stored e-book (indices start at 0).
5. **Delete last** – remove the last e-book and immediately `free` its memory; do nothing if the collection is empty.
6. **Exit** – free all remaining memory and terminate gracefully.

## Simple Example
Input
```
1
Algorithms_Cormen
5.5
1
Data_Structures_Tenenbaum
3.2
2
3
2
4
```
Output
```
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 1
Title: Algorithms_Cormen
Size in MB: 5.5
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 1
Title: Data_Structures_Tenenbaum
Size in MB: 3.2
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 2
0 Algorithms_Cormen 5.5
1 Data_Structures_Tenenbaum 3.2
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 3
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 2
0 Algorithms_Cormen 5.5
1 Add e-book
2 List e-books
3 Delete last e-book
4 Exit

Choice> 4
```
(program ends)

### CONSTRAINTS
- You must use a `struct` to represent an e-book.
- The solution must be implemented with a single function besides `main()`.

---

## Problem 21 - moonshotai/kimi-k2-instruct-0905 - Iteration 81
# STEP 1: PROBLEM
## Background Story
The campus library has just switched to a new self-service kiosk that stores e-book checkouts in memory while the kiosk is running.  
Your task is to write a tiny “checkout server” that keeps track of which student has borrowed which e-book.  
All data must live in dynamically allocated memory; when the kiosk is turned off, everything disappears.

## Functional Requirements
1. On startup the program holds **no records**.
2. The user is shown a menu:
   1) Add a new checkout  
   2) Return (delete) a checkout  
   3) List all active checkouts  
   4) Exit
3. “Add” prompts for: student ID (int), book ID (int), and book title (≤30 chars, no spaces).  
   Store the record in a **new** malloc’ed structure and link it into a simple **singly-linked list**.
4. “Return” prompts for a book ID; find and remove that record, freeing its memory.
5. “List” prints every active checkout in the order they were added (one per line):
   ```
   Student 12345: "CProgramming" (Book 6789)
   ```
6. After each operation, re-display the menu until the user chooses **4) Exit**.  
   On exit, free **all** remaining nodes and terminate gracefully.

## Simple Example Run
```
=== Mini-Kiosk ===
1) Add
2) Return
3) List
4) Exit
Choice: 1
Student ID: 12345
Book ID: 6789
Title: CProgramming
Added.
1) Add
2) Return
3) List
4) Exit
Choice: 3
Student 12345: "CProgramming" (Book 6789)
1) Add
2) Return
3) List
4) Exit
Choice: 2
Book ID to return: 6789
Returned.
1) Add
2) Return
3) List
4) Exit
Choice: 4
Good-bye.
```

### CONSTRAINTS
- Must use a `struct Checkout` to represent each record.  
- Logic for displaying a **single** checkout must be in a function `void displayCheckout(const struct Checkout *c)`.  
- The entire solution must be implemented with **only one** additional function besides `main()` (you may reuse `displayCheckout` for listing).

---

## Problem 22 - moonshotai/kimi-k2-instruct-0905 - Iteration 82
# STEP 1: PROBLEM

## Background Story
You are helping the campus “Ride-Share Hub” keep track of carpools for weekend trips.  
Each carpool has a driver (name), a destination, and a dynamically-allocated array of passenger names.  
Students can add carpools, add passengers to an existing carpool, list all carpools, or delete a carpool (which must also free every passenger name and the passenger array itself).

## Functional Requirements
1. The program starts with an empty collection of carpools.
2. Implement a menu with the following choices:
   1. Add a new carpool  
   2. Add a passenger to an existing carpool  
   3. List all carpools  
   4. Delete a carpool (and all its memory)  
   5. Exit  
3. After every operation, re-display the menu until the user chooses “Exit”.
4. All strings (names, destinations) may be assumed ≤ 49 characters.
5. Memory for every carpool, its driver name, destination, and passenger list must be dynamically allocated with malloc.  
   Memory must be freed with free as soon as the data is no longer needed.
6. If an allocation fails, print “Memory allocation failed” and terminate the program with EXIT_FAILURE.

## Simple Example Run
(user input shown after »)
```
1. Add carpool
2. Add passenger
3. List carpools
4. Delete carpool
5. Exit
» 1
Driver name: Alice
Destination: Beach
Carpool added.

1. Add carpool
2. Add passenger
3. List carpools
4. Delete carpool
5. Exit
» 2
Carpool index: 0
Passenger name: Bob
Passenger added.

1. Add carpool
2. Add passenger
3. List carpools
4. Delete carpool
5. Exit
» 3
Carpool 0: Alice -> Beach (1 passengers: Bob)

1. Add carpool
2. Add passenger
3. List carpools
4. Delete carpool
5. Exit
» 5
Goodbye!
```

### CONSTRAINTS
- Must use a struct to represent a carpool.
- The logic for displaying the details of ONE specific carpool must be in a function called displayCarpool.
- The solution must be implemented with a single function besides main().
- Menu option 5 must exit the program.

---

## Problem 23 - moonshotai/kimi-k2-instruct-0905 - Iteration 83
# STEP 1: PROBLEM

## Context
You have been hired by the campus library to write a tiny checkout-tracking program.  
All of the data (book titles, authors, and current borrower IDs) must be stored only in dynamically-allocated memory so that the program can grow or shrink as books are added or removed during the day.

## Functional Requirements
1. The program displays a menu with four choices:  
   1) Add a new book  
   2) Remove a book (by its unique integer ID)  
   3) List every book currently in the catalogue  
   4) Exit (terminates the program)  
2. Adding a book: the user supplies an ID, title, and author.  
   - If the ID already exists, print “Duplicate ID—ignored.” and do nothing.  
   - Otherwise store the book in a dynamically-allocated array of structures.  
3. Removing a book: the user supplies an ID.  
   - If the ID is found, free its memory and compact the catalogue.  
   - Otherwise print “Book not found.”  
4. Listing: print ID, title, and author for every book, one per line, in the order they are stored.  
5. Before termination (option 4) the program must free every remaining allocation.

## Simple Example Run
```
1) Add
2) Remove
3) List
4) Exit
Choice: 1
ID: 7
Title: Dune
Author: Frank Herbert
Choice: 1
ID: 3
Title: 1984
Author: George Orwell
Choice: 3
7 Dune Frank Herbert
3 1984 George Orwell
Choice: 2
ID: 7
Choice: 3
3 1984 George Orwell
Choice: 4
```

### CONSTRAINTS
- The primary data entity must be a struct Book.  
- The catalogue must be held in a single contiguous block obtained with malloc/realloc.  
- All logic for displaying one Book must be inside void displayBook(const struct Book *b).  
- The only functions besides main() are displayBook and any helper you need for memory resizing.

---

## Problem 24 - moonshotai/kimi-k2-instruct-0905 - Iteration 84
# STEP 1: PROBLEM

## Context
You are helping a small library keep track of the books that patrons borrow.  
Each book has a unique ISBN (string, max 15 chars), a title (string, max 30 chars), and the number of pages (positive int).  
The librarian wants a tiny console program that can:

- Add a new book to a dynamically-growing collection
- Show every book currently stored
- Delete a book by its ISBN
- Exit the program and release all allocated memory

The collection must start empty and grow or shrink as books are added or removed.

## Functional Requirements
1. On start-up the program shows a menu:
   1) Add book  
   2) List books  
   3) Delete book  
   4) Exit  

2. Choosing “Add book” prompts for ISBN, title, and pages; the program then allocates memory for one book, stores the data, and appends it to the collection.

3. “List books” prints every book in the order they were added, one line per book:  
   `<ISBN> - <Title> (<pages> pages)`

4. “Delete book” asks for an ISBN.  
   - If that ISBN exists, the corresponding memory is freed and the book is removed from the collection.  
   - If it does not exist, print “Book not found.”

5. On “Exit” the program must free every remaining allocated book before terminating.

## Simple Example Run
```
1) Add book
2) List books
3) Delete book
4) Exit
Choice: 1
ISBN: 9780131103627
Title: The C Programming Language
Pages: 272
Book added.

Choice: 2
9780131103627 - The C Programming Language (272 pages)

Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must represent each book with a struct named Book.
- The collection itself must also be dynamically allocated (array of pointers to Book) and resized with realloc as books are added or removed.
- All logic that prints the details of a single book must be placed in a function:  
  void displayBook(const Book *b);
- The only functions allowed besides main() are:  
  - displayBook  
  - Any helper you need for memory (re)allocation  
  No other functions are permitted.
- Menu option 4 is the only valid way to exit; the program must keep running until the user selects it.

---

## Problem 25 - moonshotai/kimi-k2-instruct-0905 - Iteration 85
# STEP 1: PROBLEM

## Background Story
You are helping the campus library re-organise its “book request” list.  
Students can ask the library to reserve copies of new titles.  
Each request contains: a unique ID (positive int), the book title (≤49 chars), and the number of copies requested (positive int).  
All requests must be stored dynamically (i.e. with malloc) while the program is running.  
When the librarian is done, the program must release every byte it allocated and exit cleanly.

## Functional Requirements
1. The program starts with an empty collection of requests.
2. Repeatedly show a menu:
   ```
   1. Add request  
   2. Delete request by ID  
   3. Show all requests  
   4. Exit
   ```
3. On “Add”:
   - Read an ID, title, and copies.
   - If that ID already exists, print “Duplicate ID – ignored.” and do nothing.
   - Otherwise allocate space for the new request, store it, and print “Request <ID> added.”
4. On “Delete”:
   - Read an ID.
   - If found, free its memory, remove it, and print “Request <ID> deleted.”
   - Otherwise print “ID not found.”
5. On “Show all”:
   - Print every request in the order added, one per line, formatted as
     ```
     ID: <id>, Title: <title>, Copies: <copies>
     ```
   - If none, print “No requests.”
6. On “Exit”:
   - Free every remaining request.
   - Print “Good-bye.” and terminate with status 0.

## Simple Example Run
Input:
```
1
101
C Primer Plus
3
1
102
Python Crash Course
2
1
3
4
```
Output:
```
Request 101 added.
Request 102 added.
ID: 101, Title: C Primer Plus, Copies: 3
ID: 102, Title: Python Crash Course, Copies: 2
Good-bye.
```

### CONSTRAINTS
- The primary data entity must be a struct named `BookRequest`.
- All requests must be kept in a singly-linked list whose nodes are also allocated with malloc.
- The only additional functions allowed besides `main()` are:
  - `void pushRequest(int id, const char *title, int copies);`
  - `int deleteRequest(int id); // returns 1 if found & deleted, else 0`
  - `void displayAll();`
- The menu option to EXIT the program is number 4.

---

## Problem 26 - moonshotai/kimi-k2-instruct-0905 - Iteration 86
# STEP 1: PROBLEM

## Context
You are helping the university library build a tiny, self-contained digital index for its collection of classic novels.  
Each book is described by:  
- a unique integer ID (1 … N)  
- a title (≤ 80 printable characters, no commas)  
- the year it was first published (positive integer)  

Because the collection keeps growing, the index must be stored in dynamically-allocated memory.  
The librarian will interact with the program through a simple text menu.

## Functional Requirements
1. Start by asking how many books will be entered (call this value `n`).  
2. Dynamically allocate an array of exactly `n` structures to hold the book data.  
3. Prompt for and store the ID, title, and publication year of each book.  
4. After all books are stored, repeatedly show a menu with the following options:  
   1) Display the full index (ID, title, year) in the order they were entered  
   2) Display the details of the book with the smallest ID  
   3) Exit the program  
5. After the user chooses “Exit”, free every dynamically-allocated byte and terminate gracefully.

## Simple Example
Input
```
3
101
Pride and Prejudice
1813
102
The Great Gatsby
1925
103
Crime and Punishment
1866
2
3
```

Output
```
1) Display full index
2) Display book with smallest ID
3) Exit
Choice: 101,"Pride and Prejudice",1813
1) Display full index
2) Display book with smallest ID
3) Exit
Choice: Goodbye!
```

### CONSTRAINTS
- You must define and use a single `struct Book` to represent each entity.  
- The logic for printing the details of exactly one book must be encapsulated in a function called `displayBook`.  
- Only two functions are allowed in your source file: `main` and `displayBook`.

---

## Problem 27 - moonshotai/kimi-k2-instruct-0905 - Iteration 87
# STEP 1: PROBLEM

**Context**  
A campus library is digitising its old catalogue cards and wants a quick-and-dirty program to add, list, and delete book records while the real system is being built.  
The program will run in a loop, keep every book in **dynamic memory only**, and release that memory when the book record is removed or when the program ends.

**What the program must do**  
1. Maintain a dynamic array of pointers to individual book records.  
2. Provide a text menu with these choices (case-insensitive single letter is fine):  
   - A – Add a new book  
   - L – List all books  
   - D – Delete a book by its unique library-id (integer)  
   - Q – Quit and free all remaining memory before exiting  
3. On “Add”, prompt for:  
   - library-id (int, unique, duplicates rejected)  
   - title (one line, up to 99 chars)  
   - author (one line, up to 99 chars)  
   and allocate exactly one `struct Book` to hold the data.  
4. On “List”, print every book in the order they were added, one per line, formatted as:  
   `id: <id>, Title: "<title>", Author: "<author>"`  
   If no books exist, print `No books in catalogue.`  
5. On “Delete”, prompt for the library-id. If found, remove that book, free its memory, compact the pointer array, and print `Book <id> removed.` If not found, print `Book <id> not found.`  
6. On “Quit”, free every book and the pointer array itself, then exit gracefully.

**Simple Example Run**  
(user input after prompt `> `)

> A  
id: 101  
title: The Art of Code  
author: J. Programmer  
Book added.  
> A  
id: 102  
title: Memory Matters  
author: A. Malloc  
Book added.  
> L  
id: 101, Title: "The Art of Code", Author: "J. Programmer"  
id: 102, Title: "Memory Matters", Author: "A. Malloc"  
> D  
id: 101  
Book 101 removed.  
> Q  

### CONSTRAINTS  
- Must use `struct Book` to represent a book entity.  
- All book storage must be allocated with `malloc` and released with `free`; no global/static arrays of fixed size.  
- The logic that prints the details of ONE specific book must be in a function called `displayBook`.  
- The program must offer option Q to quit.

---

## Problem 28 - moonshotai/kimi-k2-instruct-0905 - Iteration 88
# STEP 1: PROBLEM  
**Topic:** Dynamic Memory Allocation (malloc, free)

## Background Story  
You are helping the campus library write a tiny “Digital Post-it” system.  
A student can walk up, request a new Post-it, type a short note, and pin it to an on-screen board.  
Later they can delete a specific Post-it (by number) or wipe the whole board.  
All Post-its must live in dynamic memory so that the program never reserves more space than it actually needs.

## Requirements  
1. Keep an array of *pointers* to `struct PostIt` objects.  
2. The struct must contain:  
   - an `int id` (1-based, assigned automatically)  
   - a `char *text` (dynamically allocated)  
3. Implement the following actions via a simple text menu:  
   1) Create new Post-it  
   2) Delete one Post-it (by id)  
   3) Display all Post-its  
   4) Wipe the board (free everything)  
   5) Exit  
4. After “Exit” the program must free every remaining Post-it before terminating.  
5. Do **not** pre-allocate any array—resize the pointer array with `realloc` only when a Post-it is added or deleted.

## Example Session (user input shown after `>`)  
```
1) New 2) Delete 3) List 4) Wipe 5) Exit
> 1
Enter note: Buy milk
1) New 2) Delete 3) List 4) Wipe 5) Exit
> 3
#1: Buy milk
1) New 2) Delete 3) List 4) Wipe 5) Exit
> 2
Delete id: 1
Deleted.
1) New 2) Delete 3) List 4) Wipe 5) Exit
> 5
Good-bye!
```

## CONSTRAINTS  
- You must store Post-its in a dynamically-resized array of pointers (`struct PostIt **board`).  
- The logic that prints a single Post-it must be in a function called `displayPostIt`.  
- The only functions besides `main` may be: `displayPostIt`, `createPostIt`, `deletePostIt`, `wipeBoard`.

---

## Problem 29 - moonshotai/kimi-k2-instruct-0905 - Iteration 89
# STEP 1: PROBLEM

## Context
You are helping the campus bookstore manage its inventory of used textbooks.  
Each book has:  
- a unique 13-digit ISBN (string, exactly 13 chars plus null terminator)  
- a title (one word, ≤30 chars)  
- an integer quantity in stock  

The store clerk will interact with a simple console program that can add books, update stock, and list everything currently in the inventory.  
All data must be kept in dynamic memory so that the array can grow or shrink while the program is running.

## Functional Requirements
1. On startup the inventory is empty.
2. The program repeatedly shows a menu:
   1. Add a new book  
   2. Update stock for an existing ISBN  
   3. Show complete inventory  
   4. Exit  
3. Choosing 1:  
   - Read ISBN, title, initial quantity.  
   - If ISBN already exists, print “ISBN already in inventory.” and do nothing.  
   - Otherwise allocate space for the new book, expand the inventory array, and store it.  
4. Choosing 2:  
   - Read an ISBN and a signed integer delta.  
   - If the ISBN is found, adjust its quantity by delta (even if negative).  
   - If the ISBN is not found, print “ISBN not found.”  
5. Choosing 3:  
   - Print one line per book: `ISBN title quantity`  
   - If inventory is empty print “Inventory empty.”  
6. Choosing 4:  
   - Free all dynamically allocated memory and terminate the program.  
7. The program must handle any non-negative number of books (0 → as many as memory allows).

## Simple Example Run
```
1
9780131103627 K&R 15
1
9780131103627 K&R 5
ISBN already in inventory.
2
9780131103627 -3
3
9780131103627 K&R 12
4
```
(Program ends.)

### CONSTRAINTS
- You must store each book in a `struct Book`.  
- All books must be kept in a dynamically-allocated array of `struct Book`.  
- The logic that prints the details of ONE specific book must be in a function `void displayBook(const struct Book *b)`.  
- The only functions besides `main()` allowed are:  
  - `displayBook`  
  - one optional helper that resizes the array (if you wish).

---

## Problem 30 - moonshotai/kimi-k2-instruct-0905 - Iteration 90
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its small magazine stand.  
Each magazine is represented only by a title (≤30 chars) and its monthly price.  
You will write a tiny terminal program that lets the librarian:

- Add a new magazine (dynamically allocate it and store it in an array of pointers)
- Show every magazine currently stored
- Delete a magazine by its 1-based index (free its memory)
- Exit the program

All memory must be managed with malloc/free.

## Functional Requirements
1. On start-up the program should allocate space for up to 50 magazine pointers (but no magazines yet).
2. Present a numbered menu:
   ```
   1) Add magazine
   2) List magazines
   3) Delete magazine
   4) Exit
   ```
3. "Add magazine" reads a title and a price, allocates one magazine record, and stores its address in the next free slot.
4. "List magazines" prints the index, title, and price of every valid magazine.
5. "Delete magazine" reads an index; if valid it frees that magazine's memory and sets the pointer to NULL so it can be reused later.
6. The program must not leak memory: every malloc'ed block must eventually be freed (either during deletion or when the program ends).
7. After every command except Exit, re-display the menu.
8. On Exit the program frees any remaining magazines and terminates.

## Simple Example Run
```
1) Add magazine
2) List magazines
3) Delete magazine
4) Exit
Choice: 1
Title: CS Weekly
Price: 4.99
Magazine added.

1) Add magazine
2) List magazines
3) Delete magazine
4) Exit
Choice: 2
1: CS Weekly $4.99

1) Add magazine
2) List magazines
3) Delete magazine
4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Represent a magazine with a struct containing at least `title` and `price`.
- The logic that prints details of a single magazine must be placed in a function called `displayMagazine(const struct Magazine*)`.
- The only functions allowed in your submission are `main()` and `displayMagazine()`.
- Menu option 4 is the mandatory EXIT command.

---

## Problem 31 - moonshotai/kimi-k2-instruct-0905 - Iteration 91
# STEP 1: PROBLEM

**Background Story**  
The campus library is digitising its old card-catalogue.  
Each card contains: title (≤80 chars), author (≤50 chars), and year (int).  
Your program will act as a tiny in-memory catalogue: the user can add new cards, list all of them, or delete a card by its position in the list.  
All data must be kept in dynamically allocated memory and freed before the program ends.

**Functional Requirements**  
1. Present a simple text menu with four options:  
   1. Add a new card  
   2. List all cards  
   3. Delete a card (by 1-based index)  
   4. Exit (menu option 4)  
2. “Add” must allocate a new structure, read title, author and year, and append it to the catalogue.  
3. “List” must print every card in order, one per line, formatted exactly as:  
   `idx: "Title" by Author (year)`  
   If the catalogue is empty print `Catalogue empty.`  
4. “Delete” must free the memory of the chosen card and compact the array of pointers so that no gaps remain.  
5. After option 4 (“Exit”) the program must free all remaining memory and terminate.

**Simple Example**  
Input:
```
1
The C Programming Language
Kernighan & Ritchie
1978
1
Clean Code
Robert C. Martin
2008
2
3
1
4
```
Output:
```
1: "The C Programming Language" by Kernighan & Ritchie (1978)
2: "Clean Code" by Robert C. Martin (2008)
1: "Clean Code" by Robert C. Martin (2008)
```

### CONSTRAINTS  
- Must use a struct to represent each catalogue card.  
- All cards must be stored in a dynamically resizing array of pointers (double when full).  
- Logic for displaying the details of ONE specific card must be in a function called `displayCard`.  
- The only functions allowed besides `main()` are: `displayCard`, `addCard`, `listCards`, `deleteCard`, `freeCatalogue`.

---

## Problem 32 - moonshotai/kimi-k2-instruct-0905 - Iteration 92
# STEP 1: PROBLEM

**Background Story**  
You are the night-shift keeper at the university library.  
Every time a student returns a textbook you must shelve it, but the shelf only has room for one book of each course-number.  
If a second copy of the same course-number arrives you must recycle (free) the older copy and store the newer one.  
At closing time you need to print the current shelf contents and release all dynamically allocated memory.

**Program Requirements**  
1. Read from standard input an unknown number of lines (until EOF).  
   Each line contains:
   ```
   course_number  book_title
   ```
   Both fields are single words with no spaces (course_number is an int, book_title ≤ 30 chars).

2. Maintain a collection of currently shelved books.  
   - If the course_number is new, allocate memory for the book and add it.  
   - If the course_number already exists, replace the older book with the new one (free the old memory, allocate the new).

3. After the last line is read, print the shelf contents in ascending order of course_number, one per line:
   ```
   CS101  IntroToCS
   CS202  DataStructures
   ```

4. Immediately after printing, free every remaining dynamically allocated block and exit.

**Simple Example**  
Input
```
CS101  IntroToCS
CS202  DataStructures
CS101  BetterIntro
CS303  OS
```

Output
```
CS101  BetterIntro
CS202  DataStructures
CS303  OS
```

### CONSTRAINTS  
- Must store each book in a dynamically allocated struct.  
- Must implement exactly one user-defined function besides main():  
  `void displayShelf(const struct Book **shelf, int n);`  
  which prints the shelf as specified.  
- No global variables except for the constant `MAX_TITLE_LEN 30`.

---

## Problem 33 - moonshotai/kimi-k2-instruct-0905 - Iteration 93
# STEP 1: PROBLEM

**Context – The Library-Box Project**  
The university library is digitising its “book boxes.” Each box can hold a variable number of books that arrive over the week. You have been asked to write a small C program that keeps track of the books currently in one such box. Because the number of books changes daily, all storage must be allocated dynamically on the heap.

**Task**  
Write a program that starts with an empty box and supports the following operations:

1. Add a new book (you will be given the title and year).  
2. Remove the last book that was added (LIFO order).  
3. List every book currently in the box (print index, title, year).  
4. Exit the program.

The program must keep its data in dynamic memory and free that memory before termination.

**Simple Example Run**  
User input is shown after the prompt `>`.  

```
=== Library-Box Menu ===
1 Add book
2 Remove last book
3 List books
4 Exit
> 1
Title: The Pragmatic Programmer
Year: 1999
> 1
Title: C Programming Language
Year: 1988
> 3
0) The Pragmatic Programmer (1999)
1) C Programming Language (1988)
> 2
Removed "C Programming Language"
> 4
Good-bye!
```

### CONSTRAINTS  
- A single `struct` called `Book` must represent the primary data entity.  
- All books must be stored in a dynamically-allocated array that grows/shrinks as needed (realloc).  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The only functions allowed besides `main()` are:  
  - `displayBook(const struct Book *b)`  
  - Any helper you need for resizing the array (keep helpers minimal).  
- Menu option 4 must exit the program.

---

## Problem 34 - moonshotai/kimi-k2-instruct-0905 - Iteration 94
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a new “Tech-Loan” window where students can borrow electronic gadgets (calculators, phone chargers, mini-speakers, etc.) for a few hours.  
To keep track of what is currently on loan, you are to write a tiny, memory-aware inventory program that records each gadget’s ID, name, and the borrower’s student card number.  
Because the collection changes every semester, the program must grow or shrink its records dynamically—no compile-time arrays allowed.

## Functional Requirements
1. The program starts with an empty collection.  
2. It repeatedly presents a menu:
   1) Add a new gadget (ID, name, borrower card)  
   2) Delete a gadget by ID  
   3) List every gadget currently stored  
   4) Exit  
3. Adding must allocate exactly the memory needed for one gadget; listing must print all gadgets in the order they were added; deleting must free the memory of the chosen gadget and keep the list contiguous.  
4. After every operation the menu reappears until the user chooses the EXIT option.  
5. All heap memory must be released before the program ends.

## Simple Example Run
( user input after » )
```
1) Add
2) Delete
3) List
4) Exit
Choice: » 1
Gadget ID: » 101
Name: » Calculator
Card: » 12345
1) Add
2) Delete
3) List
4) Exit
Choice: » 1
Gadget ID: » 202
Name: » Charger
Card: » 67890
1) Add
2) Delete
3) List
4) Exit
Choice: » 3
101 Calculator 12345
202 Charger 67890
1) Add
2) Delete
3) List
4) Exit
Choice: » 2
Delete ID: » 101
Deleted.
1) Add
2) Delete
3) List
4) Exit
Choice: » 3
202 Charger 67890
1) Add
2) Delete
3) List
4) Exit
Choice: » 4
Good-bye!
```

### CONSTRAINTS
- A single structure named `Gadget` must represent each entity.  
- All list logic (add, delete, list) must be implemented in **one** user-defined function besides `main()`; use a switch inside that function or another disciplined approach, but keep the count of custom functions to one.  
- The EXIT menu option is number 4.

---

## Problem 35 - moonshotai/kimi-k2-instruct-0905 - Iteration 95
# STEP 1: PROBLEM

## Background Story
The campus library is digitising its old “book card” system.  
Each card contains a title, author, and a unique accession number.  
You have been hired to write a tiny replacement program that stores these cards in dynamic memory while the librarian is working.  
When the librarian is finished, the program must release every byte it allocated before terminating.

## Functional Requirements
1. On startup the program has NO books stored.
2. The program must support three commands entered by the user:
   - `add` – read a book’s accession number, title, and author (in that order) and store the information.
   - `list` – print every book currently stored, one per line, in the order they were added.  
     Format: `#<accession> "<title>" by <author>`
   - `exit` – free all memory and terminate the program (see menu constraint below).
3. All book data must be kept only in dynamic memory (i.e., use `malloc`/`realloc`); no global or fixed-size arrays.
4. After each `add`, the program must be able to store an unlimited number of books.

## Simple Example
Input
```
add
1001
Pride and Prejudice
Jane Austen
add
1002
1984
George Orwell
list
exit
```

Output
```
#1001 "Pride and Prejudice" by Jane Austen
#1002 "1984" by George Orwell
```

## Menu Constraint
The keyword `exit` is the only way to leave the program; typing it must free all previously allocated memory and then terminate.

### CONSTRAINTS
- You must define a single `struct` called `Book` that contains the accession number, title, and author.
- All printing of a single book must be done by a function called `displayBook` that takes a pointer to a `Book`.
- Only two functions are allowed besides `main`: `displayBook` and any function you need for releasing memory.

---

## Problem 36 - moonshotai/kimi-k2-instruct-0905 - Iteration 96
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its small collection of classic novels.  
Each book is stored as a variable-length string (its full text), and the librarian wants a tiny program that can:

1. Add a new book to the collection.  
2. Remove a book by its unique ID.  
3. List every book currently stored.  
4. Quit the program.

Because the collection grows and shrinks while the program runs, you must allocate and free memory dynamically.

## Functional Requirements
1. Represent each book with:
   - A unique integer ID (assigned sequentially, starting at 1).  
   - A dynamically-allocated C-string that holds the book’s entire text (may contain spaces).

2. Implement the following user commands (menu-driven):
   ```
   1. Add book
   2. Remove book
   3. List books
   4. Exit
   ```

3. Add book:  
   Prompt for the book’s text (up to 4095 readable characters, including spaces).  
   Store the text in freshly allocated memory and assign the next available ID.

4. Remove book:  
   Prompt for an ID.  
   Free the memory used by that book and mark the slot as empty.  
   If the ID does not exist, print `Not found.`

5. List books:  
   Print every existing book in the order of ascending IDs:
   ```
   ID: <id>
   Text: <text>
   ```
   If the collection is empty, print `Collection empty.`

6. Exit:  
   Free all remaining dynamically-allocated memory and terminate the program gracefully.

## Example Session (user input after `>`)
```
1. Add book
2. Remove book
3. List books
4. Exit
> 1
Enter book text:
> It was the best of times, it was the worst of times.

1. Add book
2. Remove book
3. List books
4. Exit
> 1
Enter book text:
> Call me Ishmael.

1. Add book
2. Remove book
3. List books
4. Exit
> 3
ID: 1
Text: It was the best of times, it was the worst of times.
ID: 2
Text: Call me Ishmael.

1. Add book
2. Remove book
3. List books
4. Exit
> 2
Enter ID to remove:
> 1
Removed.

1. Add book
2. Remove book
3. List books
4. Exit
> 3
ID: 2
Text: Call me Ishmael.

1. Add book
2. Remove book
3. List books
4. Exit
> 4
Good-bye.
```

### CONSTRAINTS
- You must use a `struct` to represent a book.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The user must be able to EXIT the program by choosing menu option 4.

---

## Problem 37 - moonshotai/kimi-k2-instruct-0905 - Iteration 97
# STEP 1: PROBLEM

## Context
You are helping the campus bookstore manage its second-hand textbook inventory.  
Each book has a title (≤40 characters), an ISBN-13 (string of 13 digits), and a price in dollars (double).  
The number of books changes every semester, so the list must grow or shrink at run-time.  
You will write a small console program that keeps the list in dynamic memory using malloc/realloc/free.

## Functional Requirements
1. On startup the program starts with an empty list.
2. The user is repeatedly shown a menu with the following choices:
   1. Add a new book
   2. Remove a book by ISBN-13
   3. Show all books (title, ISBN-13, price)
   4. EXIT
3. Adding a book:
   - Dynamically resize the array to hold one more book.
   - Read title, ISBN-13, price.
4. Removing a book:
   - Read the ISBN-13 to delete.
   - If found, shift remaining books left and shrink the array.
   - If not found, print “Book not found.”
5. Showing all books:
   - Print one line per book in the format:  
     Title: <title>, ISBN: <isbn>, Price: $<price>  
     (If there are no books, print “No books in stock.”)

## Simple Example Run
Input:
```
1
Computer Networks
9780132126953
89.99
1
Calculus
9781285740621
120.50
3
2
9781285740621
3
4
```
Output:
```
Title: Computer Networks, ISBN: 9780132126953, Price: $89.99
Book not found
Title: Computer Networks, ISBN: 9780132126953, Price: $89.99
```

### CONSTRAINTS
- The primary data entity must be a struct called Book.
- All logic for displaying a single book must be in a function void displayBook(const Book *b).
- The solution must be implemented with only one additional function besides main().
- Menu option 4 is EXIT; typing 4 must free all dynamically allocated memory and terminate the program.

---

## Problem 38 - moonshotai/kimi-k2-instruct-0905 - Iteration 98
# STEP 1: PROBLEM

## Background Story  
The campus library is tired of losing track of which books are on loan.  
They hire you to write a tiny, temporary digital ledger that keeps a list of currently borrowed books.  
All data must live only in RAM and must be created with malloc(); when the librarian chooses to quit, every record must be released with free().

## Requirements  
1. Represent each book with a struct that stores:  
   - a unique integer ID (1 … 9999)  
   - the book’s title (≤ 30 characters, no spaces)  
   - the borrower’s name (≤ 30 characters, no spaces)  
2. Keep an expandable array of pointers to these structs (double the capacity when full).  
3. Provide a menu driven interface:  
   1) Add a new loan record (ID, title, borrower)  
   2) Delete a record by ID  
   3) Display all loans  
   4) Exit the program (releases all memory and terminates)  
4. After every operation, print the current number of active loans.  
5. If the user tries to add a duplicate ID, print “Duplicate ID!” and do nothing.

## Simple Example Run  
```
1) Add  2) Delete  3) Show  4) Exit
Choice: 1
ID: 7
Title: ThePragProgrammer
Borrower: Alice
Loans: 1

1) Add  2) Delete  3) Show  4) Exit
Choice: 3
ID 7: ThePragProgrammer borrowed by Alice
Loans: 1

1) Add  2) Delete  3) Show  4) Exit
Choice: 4
Good-bye!
```

## CONSTRAINTS  
- Must use a struct to represent the primary data entity (a book loan).  
- Logic for displaying the details of ONE specific entity must be in a function called displayEntity.  
- The entire solution must be implemented with a single function besides main().

---

## Problem 39 - moonshotai/kimi-k2-instruct-0905 - Iteration 99
# STEP 1: PROBLEM

## Background Story
The campus library has just upgraded to a digital “check-out” system.  
Instead of keeping a fixed-size array for book records, the head librarian wants you to write a tiny demo that stores book information in dynamically allocated memory so that the collection can grow and shrink as books are added or returned.

## Functional Requirements
1. Represent each book with three fields:  
   - a unique integer id (1 … 2 147 483 647)  
   - title (at most 99 printable characters, no newline)  
   - a boolean flag checkedOut (0 = available, 1 = on loan)  
2. Keep every book in its own heap-allocated structure.  
3. Provide a text menu that lets the user repeatedly:  
   1) Add a new book (read id, title, checkedOut).  
   2) Search for a book by id and print its details.  
   3) Toggle the checked-out status of a book (find by id).  
   4) Delete a book (find by id and free its memory).  
   5) Show every book currently in memory.  
   6) **EXIT** the program (menu option 6).  
4. After every command, re-display the menu (except when exiting).  
5. If the user chooses an invalid menu option, print “Invalid choice.” and re-display the menu.  
6. Do not leak memory: every malloc’d book must be free’d before the program ends.

## Simple Example Run
```
=== Digital Library Demo ===
1) Add book
2) Search book
3) Toggle checkout
4) Delete book
5) List all books
6) EXIT
Choice: 1
Enter id: 101
Enter title: C Programming Language
Is checked out (0/1): 0
Book added.

1) Add book
2) Search book
3) Toggle checkout
4) Delete book
5) List all books
6) EXIT
Choice: 2
Enter id: 101
Id: 101
Title: C Programming Language
Status: Available

1) Add book
2) Search book
3) Toggle checkout
4) Delete book
5) List all books
6) EXIT
Choice: 6
Goodbye!
```

### CONSTRAINTS
- You MUST use a struct to represent each book entity.  
- All printing of a single book’s details (whether from search or list) must be done by a function named `displayBook`.  
- You may implement any number of helper functions, but the core logic for each menu action must be handled by exactly **one** additional function besides `main()` (i.e., only two functions total: `main` and the extra function).

---

## Problem 40 - moonshotai/kimi-k2-instruct-0905 - Iteration 100
# STEP 1: PROBLEM

## Background Story
The tiny village of Bitville has just discovered that its beloved “Memory Lane” is full of potholes—each hole is the size of one `int`.  
The mayor asks you, the newly-appointed “Chief Allocation Officer,” to keep a ledger that records which holes have been patched (`malloc`) and which have been reopened (`free`).  
Because the village budget is tight, you must never patch the same hole twice and you must never reopen a hole that isn’t currently patched.  
Your program will process a list of daily work orders and then print the final status of every hole.

## Program Requirements
1. Read an integer `n` (1 ≤ n ≤ 100) that tells how many holes exist on Memory Lane.  
2. Read an integer `q` (1 ≤ q ≤ 100) followed by `q` work orders.  
   - Each work order is either  
     `patch i`  – allocate memory for hole number `i` (0-based index)  
     `reopen i` – free the memory for hole number `i`  
3. After every order, silently enforce the rules:  
   - Ignore a `patch` request if the hole is already patched.  
   - Ignore a `reopen` request if the hole is already open (or never patched).  
4. After all orders, print the final status of the `n` holes on a single line:  
   - `1` if the hole is currently patched (allocated)  
   - `0` if the hole is open (freed)  
5. You must actually allocate and free the memory with `malloc`/`free`; a static array is not allowed for the status storage.

## Simple Example
Input
```
5
6
patch 0
patch 2
reopen 0
patch 0
reopen 3
patch 4
```
Output
```
1 0 1 0 1
```

### CONSTRAINTS
- The primary data entity must be a `struct` named `Hole` that contains at least an `int status` field.  
- Logic for displaying the details of ONE specific `Hole` must be in a function called `displayHole`.  
- The only functions allowed are `main` and `displayHole`.

---

## Problem 41 - llama-3.3-70b-versatile - Iteration 61
# STEP 1: PROBLEM
You are the administrator of a university's student records system. The system needs to efficiently manage student information, including their names, student IDs, and grades. The system should be able to dynamically allocate memory for new students and deallocate memory when a student's record is deleted. 

The program should provide a menu-driven interface for the user to interact with the system. The menu options should include adding a new student, deleting a student, displaying all students, and exiting the program.

### REQUIREMENTS
1. The program should use dynamic memory allocation to store student records.
2. The program should provide a menu-driven interface with the following options:
   - Add a new student
   - Delete a student
   - Display all students
   - Exit the program
3. When adding a new student, the program should prompt the user for the student's name, student ID, and grade.
4. When deleting a student, the program should prompt the user for the student ID of the student to be deleted.
5. When displaying all students, the program should display the name, student ID, and grade of each student.

### EXAMPLE
If the user adds two students with the following information:
- Student 1: Name = John, Student ID = 123, Grade = 90
- Student 2: Name = Alice, Student ID = 456, Grade = 85

The program should display the following information when the "Display all students" option is chosen:
- John, 123, 90
- Alice, 456, 85

### CONSTRAINTS
- Must use a 'struct' to represent a student, with members for name, student ID, and grade.
- The solution must be implemented with a single function besides main() to handle the menu options and student record management.
- The program must include a specific menu option to EXIT the program, which should be option 4.
- The program should handle memory deallocation when a student's record is deleted to prevent memory leaks.

Example Menu:
1. Add a new student
2. Delete a student
3. Display all students
4. Exit the program

Choose an option:

---

## Problem 42 - llama-3.3-70b-versatile - Iteration 62
# STEP 1: PROBLEM
You are a curator at a local art museum, tasked with managing the collection of art pieces. The museum has a diverse collection of paintings, sculptures, and installations, each with its own unique characteristics. To efficiently manage the collection, you need to create a program that utilizes dynamic memory allocation to store and display information about each art piece.

The program should allow users to add new art pieces, display the details of all art pieces, and remove art pieces from the collection. The art pieces will be represented by their title, artist, year of creation, and type (painting, sculpture, or installation).

### REQUIREMENTS
1. The program must allow users to add new art pieces to the collection.
2. The program must display the details of all art pieces in the collection.
3. The program must allow users to remove art pieces from the collection by title.
4. The program must handle cases where the collection is empty or the user attempts to remove a non-existent art piece.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Add art piece: 
Title: "Mona Lisa"
Artist: "Leonardo da Vinci"
Year: 1503
Type: "painting"

Add art piece: 
Title: "The Thinker"
Artist: "Auguste Rodin"
Year: 1880
Type: "sculpture"

Display all art pieces:
Title: "Mona Lisa", Artist: "Leonardo da Vinci", Year: 1503, Type: "painting"
Title: "The Thinker", Artist: "Auguste Rodin", Year: 1880, Type: "sculpture"

Remove art piece by title: "Mona Lisa"

Display all art pieces:
Title: "The Thinker", Artist: "Auguste Rodin", Year: 1880, Type: "sculpture"
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (art piece).
2. Logic for displaying the details of all art pieces must be in a function called `displayArtPieces`.
3. The solution must be implemented with a menu-driven interface.
4. The menu must include the following options:
   - Option 1: Add art piece
   - Option 2: Display all art pieces
   - Option 3: Remove art piece by title
   - Option 4: EXIT the program

Note: The program must handle dynamic memory allocation using `malloc` and `free` to store and remove art pieces from the collection. The `EXIT` option (Option 4) will terminate the program.

---

## Problem 43 - llama-3.3-70b-versatile - Iteration 63
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books it has, including the title, author, publication year, and the number of copies available. Since the number of books can vary, you need to use dynamic memory allocation to store the information about each book.

The program should allow users to add new books, remove existing books, display all books, and display the details of a specific book.

### REQUIREMENTS
1. The program should allow users to add new books with title, author, publication year, and the number of copies.
2. The program should allow users to remove existing books by title.
3. The program should display all books in the collection.
4. The program should display the details of a specific book by title.
5. The program should handle cases where a book is not found or when there are no books in the collection.

### EXAMPLE
Input:
```
Add a book: "Introduction to CS" by "John Doe" published in 2020 with 5 copies.
Add a book: "Data Structures" by "Jane Smith" published in 2019 with 3 copies.
Display all books:
  Title: Introduction to CS, Author: John Doe, Year: 2020, Copies: 5
  Title: Data Structures, Author: Jane Smith, Year: 2019, Copies: 3
Display book details: "Introduction to CS"
  Title: Introduction to CS, Author: John Doe, Year: 2020, Copies: 5
Remove book: "Data Structures"
Display all books:
  Title: Introduction to CS, Author: John Doe, Year: 2020, Copies: 5
```

### CONSTRAINTS
1. Must use a `struct` to represent a book with title, author, publication year, and the number of copies.
2. Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
3. The solution must be implemented with a menu-driven approach.
4. Must include a menu option to EXIT the program (option 6: "Exit").

Example Menu:
```
1. Add a book
2. Remove a book
3. Display all books
4. Display book details
5. Search for a book by author
6. Exit
```

---

## Problem 44 - llama-3.3-70b-versatile - Iteration 64
# STEP 1: PROBLEM
In a university setting, it's common for students to borrow books from the library. To manage the borrowing process efficiently, the library wants to create a system that keeps track of the books that are currently borrowed and the students who borrowed them. The system should allow for dynamic memory allocation to accommodate any number of books and students.

Background:
The library has a collection of books with unique titles and IDs. Each book can be borrowed by one student at a time. The system should be able to store information about the books, including their titles, IDs, and the IDs of the students who borrowed them.

Requirements:
1. The program should allow users to add new books to the system.
2. The program should allow users to borrow a book by specifying the book's ID and the student's ID.
3. The program should allow users to return a book by specifying the book's ID.
4. The program should display the details of all books in the system, including their titles, IDs, and the IDs of the students who borrowed them.
5. The program should handle cases where a book is not found in the system or is already borrowed.

Example of expected Input/Output:
```
Menu:
1. Add a new book
2. Borrow a book
3. Return a book
4. Display all books
5. EXIT

User input: 1
Book title: Introduction to Computer Science
Book ID: 12345
Student ID: (leave blank for now)

User input: 2
Book ID: 12345
Student ID: 11111

User input: 4
Book title: Introduction to Computer Science, Book ID: 12345, Student ID: 11111

User input: 5
Exiting the program...
```

### CONSTRAINTS
- The solution must use a `struct` to represent a book, which should include the book's title, ID, and the ID of the student who borrowed it.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The program must include a menu with the following options: Add a new book, Borrow a book, Return a book, Display all books, and EXIT (option 5).
- The menu option to EXIT the program is option 5.
- The program must use dynamic memory allocation (`malloc` and `free`) to manage the books in the system.

---

## Problem 45 - llama-3.3-70b-versatile - Iteration 65
# STEP 1: PROBLEM
You are the administrator of a university's library system, responsible for managing the inventory of books. The library has a large collection of books, and you need to develop a program to keep track of the books, including their titles, authors, publication years, and availability status.

The program should allow users to add new books, remove existing books, and display the details of all books or a specific book. Since the number of books is dynamic and can change frequently, you will use dynamic memory allocation to store the book information.

## REQUIREMENTS
1. The program should allow users to add new books with their titles, authors, publication years, and availability status.
2. The program should allow users to remove existing books by their titles.
3. The program should display the details of all books or a specific book by its title.
4. The program should handle cases where a book is not found or the memory allocation fails.

## EXAMPLE
Input:
```
Add book: "Introduction to CS" by "John Smith" (2020) - Available
Add book: "Data Structures" by "Jane Doe" (2019) - Available
Display all books:
  Introduction to CS by John Smith (2020) - Available
  Data Structures by Jane Doe (2019) - Available
Remove book: "Introduction to CS"
Display all books:
  Data Structures by Jane Doe (2019) - Available
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called `displayBook`.
3. The program must be implemented with a single function besides `main()` to handle the menu and user interactions, called `libraryMenu`.
4. The solution must include a menu with the following options:
   - Add a new book (Option 1)
   - Remove a book (Option 2)
   - Display all books (Option 3)
   - Display a specific book (Option 4)
   - EXIT the program (Option 5)
   The menu must be displayed repeatedly until the user chooses to EXIT the program by selecting Option 5.

---

## Problem 46 - llama-3.3-70b-versatile - Iteration 66
# STEP 1: PROBLEM
You are the curator of a library, and you need to manage the books in your collection. You want to create a program to keep track of the books, including their titles, authors, and publication years. Since the number of books can vary, you will use dynamic memory allocation to store the book information.

The program should allow you to add a new book, display all books, and search for a specific book by title or author. You should also be able to remove a book from the collection.

Here are the requirements for the program's functionality:
1. The program should dynamically allocate memory for each book.
2. The program should allow the user to add a new book to the collection.
3. The program should display all books in the collection, including their titles, authors, and publication years.
4. The program should allow the user to search for a specific book by title or author.
5. The program should allow the user to remove a book from the collection.

### EXAMPLE
Example Input:
```
Add a new book
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```
Example Output:
```
Book Collection:
1. Harry Potter by J.K. Rowling (1997)
```
### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayBooks`.
- The solution must be implemented with a menu-driven approach.
- The menu options should include:
  1. Add a new book
  2. Display all books
  3. Search for a book
  4. Remove a book
  5. EXIT (to exit the program)
- The program should free all dynamically allocated memory before exiting.

Note: The program should handle invalid inputs and edge cases, such as attempting to remove a non-existent book or searching for a book that does not exist.

---

## Problem 47 - llama-3.3-70b-versatile - Iteration 67
# STEP 1: PROBLEM
You are the administrator of a library management system. The library has a collection of books, and you want to manage the catalog using dynamic memory allocation. You need to create a program that can store book details, display them, and free the allocated memory when the program exits.

The program should have the following functionality:
1. Allocate memory dynamically for each book.
2. Store the book details, including the title, author, publication year, and price.
3. Display the details of all the books in the catalog.
4. Allow the user to search for a book by title and display its details.
5. Allow the user to add a new book to the catalog.
6. Allow the user to remove a book from the catalog and free the allocated memory.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user interactions.
- If a menu is implemented, it must include the following options:
  1. Display all books
  2. Search for a book
  3. Add a new book
  4. Remove a book
  5. EXIT the program (option 5)

### EXAMPLE INPUT/OUTPUT
Example input:
```
Choose an option:
1. Display all books
2. Search for a book
3. Add a new book
4. Remove a book
5. EXIT
```
User chooses option 3:
```
Enter book title: Introduction to CS
Enter author: John Smith
Enter publication year: 2020
Enter price: 50.00
```
Example output (after adding a new book):
```
Book title: Introduction to CS
Author: John Smith
Publication year: 2020
Price: 50.00
```
Note: The program should handle memory allocation and deallocation correctly to avoid memory leaks. The menu should be implemented in a way that allows the user to interact with the program until they choose to EXIT (option 5).

---

## Problem 48 - llama-3.3-70b-versatile - Iteration 68
# STEP 1: PROBLEM
In a simple library management system, books are the primary entities. Each book has a unique identifier (ID), title, author, and publication year. The library wants to manage its collection of books dynamically, allowing for the addition and removal of books as needed. The system should be able to store, display, and manage the details of these books efficiently.

The program should provide a menu-driven interface for the user to interact with the library system. The requirements for the program's functionality are as follows:
1. The program should allow users to add new books to the library.
2. The program should display all the books currently in the library.
3. The program should allow users to remove a book by its ID.
4. The program should display the details of a specific book by its ID.

### EXAMPLE
If the user adds two books with the following details:
- Book 1: ID = 1, Title = "Introduction to CS", Author = "John Doe", Year = 2020
- Book 2: ID = 2, Title = "Data Structures", Author = "Jane Smith", Year = 2022

The program should display these books when the user chooses to view all books. If the user then removes Book 1, only Book 2 should be displayed when the user chooses to view all books again.

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must implement a menu-driven interface with the following options:
  1. Add a new book
  2. Display all books
  3. Remove a book by ID
  4. Display a book by ID
  5. EXIT the program
- The program must dynamically allocate memory for each book when added and free the memory when a book is removed or when the program exits.

### ADDITIONAL NOTES
The program should handle memory allocation and deallocation efficiently to prevent memory leaks. The `struct` for representing a book should include the ID, title, author, and publication year. The program should validate user inputs for book details and menu options.

---

## Problem 49 - llama-3.3-70b-versatile - Iteration 69
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a simple system to manage the books in your library. The system should allow you to add, remove, and display books. Each book has a title, author, and publication year.

The program should use dynamic memory allocation to store the books. The system should start with no books and allow the user to add books dynamically.

## REQUIREMENTS
1. The program should have a menu with the following options:
   - Add a book
   - Remove a book
   - Display all books
   - Display a specific book
   - Exit the program
2. When adding a book, the program should ask for the title, author, and publication year.
3. When removing a book, the program should ask for the title of the book to remove.
4. When displaying all books, the program should show the title, author, and publication year of each book.
5. When displaying a specific book, the program should ask for the title of the book to display and show its details.

## EXAMPLE
Input:
```
1. Add a book
Title: Book1
Author: Author1
Publication Year: 2020
2. Add a book
Title: Book2
Author: Author2
Publication Year: 2021
3. Display all books
```
Output:
```
Book1 by Author1 (2020)
Book2 by Author2 (2021)
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- The menu option to EXIT the program is option 5.
- If a menu is implemented, it must include the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. Exit the program (type '5' to exit) 

Note: The program should handle memory deallocation properly to prevent memory leaks.

---

## Problem 50 - llama-3.3-70b-versatile - Iteration 70
# STEP 1: PROBLEM
You are the administrator of a university's computer lab, and you need to manage the inventory of computers in the lab. Each computer has a unique identifier, processor type, and amount of RAM. You want to create a program that allows you to dynamically add, remove, and display computers in the inventory.

The program should have the following functionality:
1. Allow the user to add a new computer to the inventory by providing its unique identifier, processor type, and amount of RAM.
2. Allow the user to remove a computer from the inventory by providing its unique identifier.
3. Allow the user to display the details of all computers in the inventory.
4. Allow the user to display the details of a specific computer by providing its unique identifier.

### EXAMPLE
Input:
```
Add computer with ID: C001, Processor: Intel, RAM: 16GB
Add computer with ID: C002, Processor: AMD, RAM: 8GB
Display all computers
Display computer with ID: C001
Remove computer with ID: C002
Display all computers
```
Output:
```
Added computer with ID: C001, Processor: Intel, RAM: 16GB
Added computer with ID: C002, Processor: AMD, RAM: 8GB
All computers:
  - ID: C001, Processor: Intel, RAM: 16GB
  - ID: C002, Processor: AMD, RAM: 8GB
Computer with ID: C001, Processor: Intel, RAM: 16GB
Removed computer with ID: C002
All computers:
  - ID: C001, Processor: Intel, RAM: 16GB
```

### CONSTRAINTS
* Must use a `struct` to represent a computer.
* Logic for displaying the details of all computers must be in a function called `displayAllComputers`.
* Logic for displaying the details of a specific computer must be in a function called `displayComputer`.
* Must use dynamic memory allocation (`malloc` and `free`) to manage the computers in the inventory.
* The solution must be implemented with a `main` function and the above-mentioned functions.
* If a menu is implemented, it must include the following options:
  1. Add computer
  2. Remove computer
  3. Display all computers
  4. Display specific computer
  5. EXIT (to exit the program)
  Note: The program should exit when the user chooses the EXIT option (option 5).

---

## Problem 51 - llama-3.3-70b-versatile - Iteration 71
# STEP 1: PROBLEM
You are the manager of a bookstore, and you want to keep track of the books in your store using a computer program. The program should allow you to add, remove, and display books. Each book has a title, author, and price.

The program should dynamically allocate memory for each book when it is added, and free the memory when the book is removed. The program should also display the details of all the books in the store.

### REQUIREMENTS
1. The program should allow the user to add a book with a title, author, and price.
2. The program should allow the user to remove a book by its title.
3. The program should display the details of all the books in the store.
4. The program should handle memory allocation and deallocation correctly to avoid memory leaks.

### EXAMPLE
Input:
```
Add book: "Book1" by "Author1" with price $10.99
Add book: "Book2" by "Author2" with price $9.99
Display all books
Remove book: "Book1"
Display all books
```
Output:
```
Book1 by Author1, price: $10.99
Book2 by Author2, price: $9.99
Book2 by Author2, price: $9.99
```

### CONSTRAINTS
1. Must use a `struct` to represent a book.
2. Logic for displaying the details of all books must be in a function called `displayBooks`.
3. The solution must be implemented with a menu-driven approach.
4. Must include a menu option to EXIT the program (option 5).

### MENU OPTIONS
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book by title
5. EXIT the program

Note: The program should handle invalid inputs and edge cases correctly.

---

## Problem 52 - llama-3.3-70b-versatile - Iteration 72
# STEP 1: PROBLEM
In a simple library management system, books are the primary entities that need to be managed. The library wants to keep track of the books it has, including their titles, authors, and the year they were published. To efficiently manage memory, the system should utilize dynamic memory allocation. Your task is to design a program that can add, display, and remove books from the library's catalog.

The program should have the following functionality:
1. Allow users to add new books to the catalog by providing the title, author, and publication year.
2. Display all the books in the catalog.
3. Remove a book from the catalog by its title.
4. The program should continue to run and prompt the user for actions until the user chooses to exit.

### CONSTRAINTS
- Must use a `struct` to represent a book, which includes the title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayCatalog`.
- The solution must include a menu-driven interface with the following options:
  1. Add a new book
  2. Display all books
  3. Remove a book
  4. Exit the program
- The program must use dynamic memory allocation (`malloc`, `free`) to manage the memory for the books.
- The "Exit the program" option must be clearly labeled as option 4.

### EXAMPLE
Example Input/Output:
```
Library Catalog Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit the program

Choose an option: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter book publication year: 2020

Library Catalog Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit the program

Choose an option: 2
Book Title: Introduction to CS
Book Author: John Doe
Book Publication Year: 2020

Library Catalog Menu:
1. Add a new book
2. Display all books
3. Remove a book
4. Exit the program

Choose an option: 4
Exiting the program...
```

---

## Problem 53 - llama-3.3-70b-versatile - Iteration 73
# STEP 1: PROBLEM
You are the manager of a university's computer lab, and you need to keep track of the computers in the lab. Each computer has a unique ID, a type (laptop or desktop), and a status (available or in use). You want to create a program that allows you to manage the computers in the lab.

The program should be able to perform the following functions:
1. Add a new computer to the lab.
2. Remove a computer from the lab.
3. Display the details of all computers in the lab.
4. Display the details of a specific computer.
5. Exit the program.

Here's a simple example of how the program should work:
```
Input:
1. Add computer with ID 1, type laptop, and status available.
2. Add computer with ID 2, type desktop, and status in use.
3. Display all computers.
Output:
Computer 1: laptop, available
Computer 2: desktop, in use
```

### CONSTRAINTS
- Must use a `struct` to represent a computer.
- The solution must be implemented with two functions besides `main()`: `addComputer` and `displayComputers`.
- Logic for displaying the details of ONE specific entity must be in a function called `displayComputer`.
- The program must use dynamic memory allocation (`malloc`, `free`) to store the computers.
- If a menu is implemented, it must include a specific menu option to EXIT the program (option 5).
- The menu options must be:
  1. Add computer
  2. Remove computer
  3. Display all computers
  4. Display specific computer
  5. Exit program

Note: The program should handle memory deallocation when a computer is removed or when the program exits.

---

## Problem 54 - llama-3.3-70b-versatile - Iteration 74
# STEP 1: PROBLEM
You are the manager of a library where books are borrowed and returned by students. To manage the inventory of books efficiently, you want to create a simple program that allows you to add, remove, and display books. Since the number of books is dynamic and can change over time, you need to use dynamic memory allocation to store the book information.

Background: 
The library has a collection of books, each with a unique title, author, and status (available or borrowed). You want to create a program that can store this information and perform basic operations like adding a new book, removing a book, and displaying the details of all books or a specific book.

Requirements:
1. The program should allow users to add a new book with title, author, and initial status (available).
2. The program should allow users to remove a book by title.
3. The program should allow users to display all books.
4. The program should allow users to display the details of a specific book by title.
5. The program should handle cases where a book is not found.

Example:
Input: 
- Add book: "Harry Potter" by "J.K. Rowling"
- Add book: "The Lord of the Rings" by "J.R.R. Tolkien"
- Display all books
- Remove book: "Harry Potter"
- Display all books

Output:
- After adding "Harry Potter" and "The Lord of the Rings":
  - "Harry Potter" by J.K. Rowling (available)
  - "The Lord of the Rings" by J.R.R. Tolkien (available)
- After removing "Harry Potter":
  - "The Lord of the Rings" by J.R.R. Tolkien (available)

### CONSTRAINTS
- Must use a 'struct' to represent a book with title, author, and status.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must implement a menu with the following options:
  - 1: Add book
  - 2: Remove book
  - 3: Display all books
  - 4: Display a specific book
  - 5: EXIT the program
- The program must handle memory allocation and deallocation using malloc and free.

---

## Problem 55 - llama-3.3-70b-versatile - Iteration 75
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library wants to keep track of the books it has, including the title, author, publication year, and whether the book is currently borrowed or not. To efficiently manage the collection, you need to create a program that can dynamically add, remove, and display books.

The program should allow users to interact with the library's collection through a simple menu-driven interface. The menu options should include adding a new book, removing a book, displaying all books, displaying a specific book, and exiting the program.

## REQUIREMENTS
1. The program must be able to dynamically allocate memory for new books.
2. The program must allow users to add new books to the collection.
3. The program must allow users to remove books from the collection.
4. The program must display all books in the collection.
5. The program must allow users to search for and display a specific book by its title.

## EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

User choice: 1
Enter book title: "Introduction to Computer Science"
Enter book author: "Professor Smith"
Enter publication year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

User choice: 3
Book 1:
Title: "Introduction to Computer Science"
Author: "Professor Smith"
Publication Year: 2020
Borrowed: No
```

### CONSTRAINTS
- Must use a `struct` to represent a book, containing fields for title, author, publication year, and whether the book is borrowed.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must include a menu option to EXIT the program, which is option 5.
- When removing a book, the program must check if the book exists in the collection before attempting to remove it.
- When displaying all books or a specific book, the program must handle the case where the collection is empty or the specific book is not found.

---

## Problem 56 - llama-3.3-70b-versatile - Iteration 76
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. You want to create a program that can efficiently manage the collection by allocating memory for each book as it is added and deallocating memory when a book is removed.

The program should maintain a list of books, where each book has a title, author, and publication year. The program should provide options to add a book, remove a book, display all books, and exit the program.

### REQUIREMENTS
1. The program should allocate memory for each book using dynamic memory allocation (malloc).
2. The program should deallocate memory for a book when it is removed (free).
3. The program should display the details of all books in the collection.
4. The program should provide a menu-driven interface to interact with the collection.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add Book
2. Remove Book
3. Display Books
4. Exit
Enter your choice: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997
```
Example Output:
```
Book added successfully!
```
Then, if the user chooses to display all books:
```
1. Add Book
2. Remove Book
3. Display Books
4. Exit
Enter your choice: 3
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. Logic for displaying the details of all books must be in a function called `displayBooks`.
3. The solution must be implemented with a single function besides `main()` to handle the menu operations, called `handleMenu`.
4. If a menu is implemented, must include a specific menu option to EXIT the program, which is option 4.

Note: The program should handle memory allocation and deallocation correctly to avoid memory leaks.

---

## Problem 57 - llama-3.3-70b-versatile - Iteration 77
# STEP 1: PROBLEM
In a university setting, it's common for students to borrow books from the library. To manage the borrowing process efficiently, the library wants to implement a simple system using dynamic memory allocation. The system should allow students to borrow and return books, and it should keep track of the books that are currently borrowed.

Background:
The library has a collection of books, and each book has a unique title, author, and status (available or borrowed). The library wants to create a program that can manage the borrowing and returning of books.

Requirements:
1. The program should allow users to add new books to the system.
2. The program should allow users to borrow a book by its title.
3. The program should allow users to return a book by its title.
4. The program should display the status of all books in the system.
5. The program should handle cases where a user tries to borrow a book that is already borrowed or return a book that is not borrowed.

Example:
Input: 
- Add book "Introduction to CS" by "John Doe"
- Add book "Data Structures" by "Jane Smith"
- Borrow book "Introduction to CS"
- Display all books
- Return book "Introduction to CS"
- Display all books

Output:
- After adding books: 
  - Introduction to CS by John Doe (available)
  - Data Structures by Jane Smith (available)
- After borrowing "Introduction to CS": 
  - Introduction to CS by John Doe (borrowed)
  - Data Structures by Jane Smith (available)
- After returning "Introduction to CS": 
  - Introduction to CS by John Doe (available)
  - Data Structures by Jane Smith (available)

### CONSTRAINTS
- The program must use a `struct` to represent a book, which should have fields for title, author, and status.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The program must implement a menu-driven system with the following options:
  1. Add a new book
  2. Borrow a book
  3. Return a book
  4. Display all books
  5. EXIT (to exit the program)
- The program must use dynamic memory allocation (`malloc` and `free`) to manage the books.
- The program must handle memory leaks by freeing allocated memory when it is no longer needed.

---

## Problem 58 - llama-3.3-70b-versatile - Iteration 78
# STEP 1: PROBLEM
You are the owner of a small library that lends books to its members. To manage the books and their respective authors, you want to create a simple console-based application. The application should store information about each book, including its title, author, and the year it was published.

### BACKGROUND
The library currently has a small collection of books, and you want to be able to add, remove, and display information about the books. Since the number of books is expected to grow, you want to use dynamic memory allocation to store the book information.

### FUNCTIONALITY REQUIREMENTS
The program must be able to:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all the books in the collection.
4. Display the details of a specific book by its title.

### EXAMPLE INPUT/OUTPUT
Example input:
```
Add a book: Title - "Book1", Author - "Author1", Year - 2020
Add a book: Title - "Book2", Author - "Author2", Year - 2021
Display all books:
Book1 by Author1 (2020)
Book2 by Author2 (2021)
Remove book: Book1
Display all books:
Book2 by Author2 (2021)
```

### CONSTRAINTS
- Must use a `struct` to represent a book with its title, author, and year.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for displaying the details of a specific book must be in a function called `displayBook`.
- The solution must be implemented with dynamic memory allocation using `malloc` and `free`.
- The program must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- The program must exit when the user selects the EXIT option (option 5).

Note: The program should handle memory allocation and deallocation properly to avoid memory leaks. The user input for the book title, author, and year should be handled using `scanf` or `fgets` functions. The program should also handle cases where a book with the given title does not exist in the collection.

---

## Problem 59 - llama-3.3-70b-versatile - Iteration 79
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The librarian can add, remove, and display books. Each book has a title, author, and publication year. The program should use dynamic memory allocation to store the books.

The librarian wants the program to have the following functionality:
1. Add a new book: The program should allocate memory for a new book and store the title, author, and publication year.
2. Remove a book: The program should free the memory allocated for the book and remove it from the list.
3. Display all books: The program should display the title, author, and publication year of all books.
4. Display a specific book: The program should display the title, author, and publication year of a specific book.

Here's an example of the expected input/output:
```
Add a new book:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
Book added successfully!

Display all books:
1. Harry Potter by J.K. Rowling (1997)
2. The Lord of the Rings by J.R.R. Tolkien (1954)

Remove a book:
Title: Harry Potter
Book removed successfully!

Display all books:
1. The Lord of the Rings by J.R.R. Tolkien (1954)
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the primary data entity (Book).
- The logic for displaying the details of ONE specific entity must be in a function called `displayBook`.
- The program must include a menu with the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- The program must use dynamic memory allocation (`malloc` and `free`) to store the books.

---

## Problem 60 - llama-3.3-70b-versatile - Iteration 80
# STEP 1: PROBLEM
You are the administrator of a library management system. The library has a collection of books, and you want to manage the books using a dynamic memory allocation system. You will create a program that can add, remove, and display books.

Background:
The library management system needs to store information about each book, including the title, author, publication year, and status (available or borrowed). The system should be able to handle a dynamic number of books.

Requirements:
1. The program should allocate memory for each book using malloc.
2. The program should store the book's information in a struct.
3. The program should have a menu-driven interface with the following options:
   - Add a book
   - Remove a book
   - Display all books
   - Display a specific book
4. The program should free the allocated memory when a book is removed.

Example:
Input:
```
1. Add a book
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
Status: available
2. Add a book
Title: The Lord of the Rings
Author: J.R.R. Tolkien
Publication Year: 1954
Status: available
3. Display all books
```
Output:
```
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
Status: available

Book 2:
Title: The Lord of the Rings
Author: J.R.R. Tolkien
Publication Year: 1954
Status: available
```
### CONSTRAINTS
- Must use a 'struct' to represent the book entity.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.

Menu Options:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. EXIT the program

Note: The program should handle invalid inputs and memory allocation failures.

---

## Problem 61 - llama-3.3-70b-versatile - Iteration 81
# STEP 1: PROBLEM
You are the manager of a library that lends books to its members. The library has a collection of books, and each book has a unique title, author, and publication year. You want to create a program to manage the library's collection of books using dynamic memory allocation.

Background:
The library's collection of books is constantly changing, with new books being added and old books being removed. The library wants to keep track of its collection using a program that can handle a dynamic number of books.

Requirements:
1. The program must allow the user to add a new book to the collection.
2. The program must allow the user to remove a book from the collection by its title.
3. The program must allow the user to display all the books in the collection.
4. The program must allow the user to search for a book by its title or author.

Example Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit

Enter your choice: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit

Enter your choice: 3
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```

### CONSTRAINTS
1. The program must use a `struct` to represent a book, with members for the title, author, and publication year.
2. The logic for displaying the details of all books must be in a function called `displayBooks`.
3. The solution must be implemented with a single function besides `main()` to handle the menu options, called `handleMenuOption`.
4. The program must include a specific menu option to EXIT the program, which is option 5.

Note: The program must use dynamic memory allocation (`malloc` and `free`) to manage the collection of books. The program must also handle memory leaks by freeing the allocated memory when it is no longer needed.

---

## Problem 62 - llama-3.3-70b-versatile - Iteration 82
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a dynamic system to store information about each book, including its title, author, and publication year. Your task is to design a program that allows the librarian to add, remove, and display books in the collection.

The program should have the following functionality:
1. **Add a Book**: The user should be able to add a new book to the collection by providing its title, author, and publication year.
2. **Remove a Book**: The user should be able to remove a book from the collection by providing its title.
3. **Display All Books**: The user should be able to view all the books in the collection.
4. **Display a Specific Book**: The user should be able to view the details of a specific book by providing its title.

### EXAMPLE
Input:
```
Add a book with title "Book1", author "Author1", and publication year 2020.
Add a book with title "Book2", author "Author2", and publication year 2021.
Display all books.
Remove the book with title "Book1".
Display all books.
```
Output:
```
Book1 by Author1, published in 2020
Book2 by Author2, published in 2021
Book2 by Author2, published in 2021
```

### CONSTRAINTS
* The solution must use a `struct` to represent a book, with members for title, author, and publication year.
* The logic for displaying the details of all books must be in a function called `displayAllBooks`.
* The logic for displaying the details of a specific book must be in a function called `displayBook`.
* The program must use dynamic memory allocation (`malloc` and `free`) to store and manage the collection of books.
* A menu must be implemented with the following options:
	1. Add a book
	2. Remove a book
	3. Display all books
	4. Display a specific book
	5. EXIT (to exit the program)
* The program must handle invalid inputs and memory allocation errors.

Note: The program should be implemented in C, and the `struct` definition, function prototypes, and main function should be clearly defined.

---

## Problem 63 - llama-3.3-70b-versatile - Iteration 83
# STEP 1: PROBLEM
You are the administrator of a library management system. The library has a collection of books, and you need to manage the inventory using dynamic memory allocation. The program should allow users to add, remove, and display book details.

The library has the following requirements for the program's functionality:
1. The program should be able to store and manage a dynamic list of books.
2. Each book should have a unique ID, title, author, and publication year.
3. Users should be able to add a new book to the inventory by providing the required details.
4. Users should be able to remove a book from the inventory by providing the book's ID.
5. Users should be able to display all the books in the inventory.
6. Users should be able to search for a book by its ID and display its details.

Here is a simple example of expected input/output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Search for a book
5. Exit

User chooses option 1:
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter publication year: 2020

User chooses option 3:
Book 1:
ID: 1
Title: Introduction to CS
Author: John Doe
Publication Year: 2020

User chooses option 5:
Exiting the program...
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The solution must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit
- The program must exit when the user chooses option 5 (Exit).
- The `displayBookDetails` function should be used to display the details of a single book.
- The program should handle memory allocation and deallocation using `malloc` and `free` functions.

---

## Problem 64 - llama-3.3-70b-versatile - Iteration 84
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. To efficiently manage the collection, you need to create a program that utilizes dynamic memory allocation to store and manage book information.

The program should allow users to add, remove, and display books in the collection. Each book is represented by its title, author, and publication year.

## REQUIREMENTS
1. The program should dynamically allocate memory for each book added to the collection.
2. The program should allow users to add books to the collection.
3. The program should allow users to remove books from the collection by title.
4. The program should allow users to display all books in the collection.
5. The program should display the details of each book, including title, author, and publication year.

## EXAMPLE INPUT/OUTPUT
Example Input:
```
Add a book: 
Title: "Introduction to Computer Science"
Author: "John Doe"
Publication Year: 2020

Add another book: 
Title: "Data Structures and Algorithms"
Author: "Jane Smith"
Publication Year: 2019

Display all books:
1. Introduction to Computer Science by John Doe (2020)
2. Data Structures and Algorithms by Jane Smith (2019)

Remove a book: 
Title: "Introduction to Computer Science"

Display all books:
1. Data Structures and Algorithms by Jane Smith (2019)
```

### CONSTRAINTS
- Must use a `struct` to represent each book in the collection.
- The solution must be implemented with a single function besides `main()`, called `manageLibrary()`, which will contain the logic for the entire program.
- Must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. EXIT the program
- The program must free any dynamically allocated memory before exiting to prevent memory leaks. 

Note that the menu option to EXIT the program is option 4.

---

## Problem 65 - llama-3.3-70b-versatile - Iteration 85
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a program to manage the books in your library. The program should be able to add, remove, and display books. Each book has a title, author, and publication year.

Background:
The library has a limited budget, and it can only afford to store information about a certain number of books at a time. Therefore, the program should use dynamic memory allocation to store the book information.

Requirements:
1. The program should be able to add a new book to the library.
2. The program should be able to remove a book from the library.
3. The program should be able to display all the books in the library.
4. The program should be able to display the details of a specific book.

Example:
If the user adds the following books:
- Title: "Book1", Author: "Author1", Year: 2000
- Title: "Book2", Author: "Author2", Year: 2001
- Title: "Book3", Author: "Author3", Year: 2002

And then the user chooses to display all books, the output should be:
- Book1 by Author1 (2000)
- Book2 by Author2 (2001)
- Book3 by Author3 (2002)

If the user chooses to display the details of "Book2", the output should be:
Title: Book2
Author: Author2
Year: 2001

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- The logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- The program must free all allocated memory before exiting.

Note: The user should be able to specify the title of the book when choosing to display a specific book or remove a book. The program should handle cases where the book is not found.

---

## Problem 66 - llama-3.3-70b-versatile - Iteration 86
# STEP 1: PROBLEM
In a library management system, books are stored on shelves. Each book has a title, author, publication year, and a unique identifier (ID). The system needs to efficiently manage the books using dynamic memory allocation. The goal is to create a program that allows users to add, remove, and display books, while also demonstrating the proper use of `malloc` and `free` for memory management.

### BACKGROUND
The library management system starts with no books. Users can add books, and each book is assigned a unique ID starting from 1. When a book is removed, its ID is not reused. The system must be able to display all books or a specific book by its ID.

### REQUIREMENTS
1. The program must allow users to add a new book with a title, author, and publication year.
2. The program must allow users to remove a book by its ID.
3. The program must be able to display all books or a specific book by its ID.
4. The program must handle memory allocation and deallocation properly using `malloc` and `free`.
5. The program must have a menu-driven interface.

### EXAMPLE
If the user adds three books:
- Book 1: "Book1", "Author1", 2000
- Book 2: "Book2", "Author2", 2001
- Book 3: "Book3", "Author3", 2002

And then displays all books, the output should show the details of all three books.

### CONSTRAINTS
- Must use a `struct` to represent a book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
- The solution must implement a menu with the following options:
  1. Add a book
  2. Remove a book by ID
  3. Display all books
  4. Display a book by ID
  5. EXIT the program

Note: The menu option to EXIT the program is option 5. When this option is chosen, the program must free all allocated memory before terminating.

---

## Problem 67 - llama-3.3-70b-versatile - Iteration 87
# STEP 1: PROBLEM
You are the administrator of a university's parking system. The university has a limited number of parking spots, and you need to keep track of which spots are occupied and by whom. To efficiently manage the parking system, you decide to create a program that uses dynamic memory allocation to store information about the parked vehicles.

The program should allow users to add, remove, and display information about the parked vehicles. Each vehicle is represented by its license plate number, the owner's name, and the parking spot number.

### REQUIREMENTS
1. The program must allow users to add a new vehicle to the parking system.
2. The program must allow users to remove a vehicle from the parking system by its license plate number.
3. The program must display all the vehicles currently parked in the system.
4. The program must handle cases where a user tries to add a vehicle to a non-existent parking spot or remove a vehicle that is not in the system.

### EXAMPLE
If the user adds two vehicles with the following information:
- License plate number: ABC123, Owner's name: John Doe, Parking spot number: 1
- License plate number: DEF456, Owner's name: Jane Doe, Parking spot number: 2

The program should display:
- License plate number: ABC123, Owner's name: John Doe, Parking spot number: 1
- License plate number: DEF456, Owner's name: Jane Doe, Parking spot number: 2

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Vehicle).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayVehicle'.
3. The program must implement a menu-driven system with the following options:
   - Add a vehicle (Option 1)
   - Remove a vehicle (Option 2)
   - Display all vehicles (Option 3)
   - Display a specific vehicle (Option 4)
   - EXIT the program (Option 5)

Note: The program should exit when the user selects Option 5. If the user enters an invalid option, the program should display an error message and prompt the user to enter a valid option.

---

## Problem 68 - llama-3.3-70b-versatile - Iteration 88
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library's catalog system is currently being updated, and you need to create a program to manage the books. The program should utilize dynamic memory allocation to efficiently store and manage the books.

The program's background is to create a simple library management system where you can add, remove, and display books. The library has a limited amount of memory, so you need to ensure that you are allocating and deallocating memory efficiently.

### REQUIREMENTS
The program must have the following functionalities:
1. Add a book to the library: The program should prompt the user for the book's title, author, and publication year.
2. Remove a book from the library: The program should prompt the user for the title of the book to be removed.
3. Display all books in the library: The program should display the title, author, and publication year of all books in the library.
4. Display the details of a specific book: The program should prompt the user for the title of the book and display its details.

### EXAMPLE
Example Input:
```
Add a book
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```
Example Output:
```
Book added successfully!
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997
```

### CONSTRAINTS
- Must use a `struct` to represent a book, containing the title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input.
- If a menu is implemented, it must include the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- The program should handle memory allocation and deallocation using `malloc` and `free` to ensure efficient memory management.

Note: The program should be able to handle a dynamic number of books and should not have a fixed limit on the number of books that can be added.

---

## Problem 69 - llama-3.3-70b-versatile - Iteration 89
# STEP 1: PROBLEM
You are the manager of a library, and you want to create a system to manage the books in your library. The system should be able to store information about each book, including its title, author, and publication year. The system should also be able to add new books, remove existing books, and display information about all the books in the library.

The system will use dynamic memory allocation to store the book information, and you want to make sure that the memory is properly managed to avoid memory leaks.

### REQUIREMENTS
The program should have the following functionality:
1. Add a new book to the library: The program should ask for the title, author, and publication year of the new book, and then add the book to the library.
2. Remove a book from the library: The program should ask for the title of the book to be removed, and then remove the book from the library if it exists.
3. Display all books in the library: The program should display the title, author, and publication year of all the books in the library.
4. Display the details of a specific book: The program should ask for the title of the book, and then display the title, author, and publication year of the book if it exists in the library.

### EXAMPLE
Input:
```
1. Add a new book
Title: "Introduction to Computer Science"
Author: "John Smith"
Publication Year: 2020
2. Display all books
3. Display the details of a specific book
Title: "Introduction to Computer Science"
```
Output:
```
Book added successfully!
All books:
Title: "Introduction to Computer Science", Author: "John Smith", Publication Year: 2020
Book details:
Title: "Introduction to Computer Science", Author: "John Smith", Publication Year: 2020
```

### CONSTRAINTS
* The solution must be implemented in C.
* The program must use a `struct` to represent a book, with members for title, author, and publication year.
* The logic for displaying the details of a specific book must be in a function called `displayBook`.
* The program must use dynamic memory allocation (`malloc` and `free`) to store the book information.
* The program must include a menu with the following options:
	1. Add a new book
	2. Remove a book
	3. Display all books
	4. Display the details of a specific book
	5. EXIT (to exit the program)
* The program must handle invalid user input and memory allocation errors.

---

## Problem 70 - llama-3.3-70b-versatile - Iteration 90
# STEP 1: PROBLEM
In a simple library management system, we want to manage a collection of books using dynamic memory allocation. Each book has a title, author, and publication year. The system should allow users to add new books, display all books, and remove a book by its title.

Background:
The library management system is designed to efficiently manage a collection of books. The system should be able to handle a varying number of books, and the user should be able to interact with the system through a simple menu.

Requirements:
1. The program should allocate memory for each book dynamically using `malloc`.
2. The program should store the books in a linked list.
3. The program should provide a menu with options to:
   - Add a new book
   - Display all books
   - Remove a book by its title
   - Exit the program
4. The program should free the allocated memory when a book is removed or when the program exits.

Example:
Input:
```
1. Add a new book
Title: Book1
Author: Author1
Year: 2020
2. Add a new book
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
- Must use a `struct` to represent a book, with members `title`, `author`, and `year`.
- The solution must be implemented with a single function besides `main()` to handle the menu options, called `handleMenuOption`.
- The `handleMenuOption` function should take an integer representing the chosen menu option as a parameter.
- The program should include a specific menu option to EXIT the program, which is option 5.
- When removing a book, the program should prompt the user to enter the title of the book to be removed.
- The program should handle cases where the user tries to remove a book that does not exist in the system. 

Example Menu:
```
1. Add a new book
2. Display all books
3. Remove a book
4. Display the details of a specific book
5. Exit the program
```

---

## Problem 71 - llama-3.3-70b-versatile - Iteration 91
# STEP 1: PROBLEM
In a university setting, it's common for students to borrow books from the library. To manage the borrowing process efficiently, the library wants to create a simple system to track borrowed books. The system should allow users to add, remove, and display books.

The system will use a simple text-based interface where users can interact with the system using a menu. The menu will have the following options:
- Add a book to the system
- Remove a book from the system
- Display all books in the system
- Display details of a specific book
- Exit the program

### REQUIREMENTS
The program must meet the following requirements:
1. The program must use dynamic memory allocation to store book information.
2. Each book must have a unique ID, title, and author.
3. The program must allow users to add books to the system.
4. The program must allow users to remove books from the system by ID.
5. The program must display all books in the system when the user chooses to do so.
6. The program must display the details of a specific book when the user chooses to do so.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a book
Enter book ID: 1
Enter book title: Introduction to CS
Enter book author: John Doe
2. Add a book
Enter book ID: 2
Enter book title: Data Structures
Enter book author: Jane Doe
3. Display all books
```
Example Output:
```
Book 1:
ID: 1
Title: Introduction to CS
Author: John Doe

Book 2:
ID: 2
Title: Data Structures
Author: Jane Doe
```

### CONSTRAINTS
- Must use a `struct` to represent a book.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of a specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which will be option 5. When the user chooses option 5, the program must free all dynamically allocated memory before exiting.

---

## Problem 72 - llama-3.3-70b-versatile - Iteration 92
# STEP 1: PROBLEM
In a university setting, a simple student information system is required to manage student records. The system should be able to dynamically allocate memory for each student record and free the memory when a record is deleted. 

The background story is that the university wants to create a simple console-based application that allows administrators to add, delete, and display student records. Each student record consists of a unique student ID, name, and age.

The requirements for the program's functionality are as follows:
1. The program should allow administrators to add a new student record.
2. The program should allow administrators to delete a student record by student ID.
3. The program should allow administrators to display all student records.
4. The program should allow administrators to display a specific student record by student ID.

Here's a simple example of expected input/output:
```
Menu:
1. Add student
2. Delete student
3. Display all students
4. Display student by ID
5. Exit

Choose an option: 1
Enter student ID: S001
Enter name: John Doe
Enter age: 20

Choose an option: 3
Student ID: S001, Name: John Doe, Age: 20

Choose an option: 2
Enter student ID to delete: S001

Choose an option: 3
No students found.
```

### CONSTRAINTS
- The solution must use a `struct` to represent the student record.
- Logic for displaying the details of one specific student must be in a function called `displayStudent`.
- The program must implement a menu-driven interface.
- Must include a specific menu option to EXIT the program, which is option 5.
- The `displayAllStudents` function must be implemented to display all student records.
- Memory for each student record must be dynamically allocated using `malloc` and freed using `free` when a record is deleted.

---

## Problem 73 - llama-3.3-70b-versatile - Iteration 93
# STEP 1: PROBLEM
**Dynamic Memory Allocation for Student Records**

You are a system administrator at a university, tasked with designing a simple program to manage student records. The program should allow users to add, display, and delete student records dynamically. Each student record consists of a unique ID, name, and grade point average (GPA).

**Background Story:**
The university currently uses a manual system to manage student records, which is time-consuming and prone to errors. The goal is to create a program that can efficiently store and manage student records using dynamic memory allocation.

**Requirements:**

1. The program should allow users to add new student records.
2. The program should display all student records.
3. The program should allow users to delete a specific student record by ID.
4. The program should handle memory allocation and deallocation dynamically using `malloc` and `free`.

**Example Input/Output:**

```
Menu:
1. Add Student Record
2. Display All Student Records
3. Delete Student Record
4. EXIT

Choose an option: 1
Enter Student ID: 123
Enter Student Name: John Doe
Enter Student GPA: 3.5

Choose an option: 2
Student ID: 123, Name: John Doe, GPA: 3.5

Choose an option: 3
Enter Student ID to delete: 123

Choose an option: 2
No student records found.
```

### CONSTRAINTS

* Must use a `struct` to represent the primary data entity (Student Record).
* Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
* The solution must be implemented with a single function besides `main()`, which will handle all menu options and operations.
* If a menu is implemented, it must include a specific menu option to EXIT the program (option 4: EXIT).

---

## Problem 74 - llama-3.3-70b-versatile - Iteration 94
# STEP 1: PROBLEM
In a university setting, the management wants to create a simple system to manage the allocation of rooms for various events. The system should be able to dynamically allocate memory for new rooms and deallocate memory when a room is no longer needed. The system should be able to store the room number, capacity, and a brief description of the event.

The background story is that the university has a limited number of rooms available, and the management wants to ensure that the rooms are allocated efficiently. The system should be able to handle a large number of rooms and events.

The program's functionality should include the following requirements:
1. The program should be able to dynamically allocate memory for new rooms.
2. The program should be able to store the room number, capacity, and a brief description of the event.
3. The program should be able to display the details of all rooms.
4. The program should be able to deallocate memory for a room when it is no longer needed.
5. The program should have a menu-driven interface to perform the above operations.

Here is a simple example of expected Input/Output:
```
Menu:
1. Add Room
2. Display Rooms
3. Remove Room
4. EXIT
Enter your choice: 1
Enter room number: 101
Enter capacity: 50
Enter description: Meeting
Menu:
1. Add Room
2. Display Rooms
3. Remove Room
4. EXIT
Enter your choice: 2
Room Number: 101
Capacity: 50
Description: Meeting
Menu:
1. Add Room
2. Display Rooms
3. Remove Room
4. EXIT
Enter your choice: 3
Enter room number to remove: 101
Room removed successfully
Menu:
1. Add Room
2. Display Rooms
3. Remove Room
4. EXIT
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Room).
- Logic for displaying the details of all rooms must be in a function called `displayRooms`.
- The solution must be implemented with a single function besides `main()` to handle the menu-driven interface, called `handleMenu`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4 or the keyword "EXIT". 
- The program should handle memory leaks by deallocating memory for rooms when they are no longer needed.

---

## Problem 75 - llama-3.3-70b-versatile - Iteration 95
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library has a dynamic collection, with books being added and removed regularly. To efficiently manage the collection, you want to create a program that uses dynamic memory allocation to store and manage the books.

The program should allow users to add, remove, and display books in the collection. Each book has a title, author, and publication year.

The requirements for the program's functionality are:
1. The program should allow users to add a new book to the collection.
2. The program should allow users to remove a book from the collection by title.
3. The program should display all books in the collection.
4. The program should display the details of a specific book by title.

Here's a simple example of expected input/output:
- Add a book: "To Kill a Mockingbird" by Harper Lee, published in 1960.
- Add a book: "1984" by George Orwell, published in 1949.
- Display all books:
  - "To Kill a Mockingbird" by Harper Lee, published in 1960.
  - "1984" by George Orwell, published in 1949.
- Remove a book: "1984"
- Display all books:
  - "To Kill a Mockingbird" by Harper Lee, published in 1960.

### CONSTRAINTS
- The solution must be implemented using dynamic memory allocation (malloc, free).
- Must use a 'struct' to represent a book, which includes title, author, and publication year.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The program must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT
- If a menu is implemented, the program must exit when the user selects the 'EXIT' option (option 5).

---

## Problem 76 - llama-3.3-70b-versatile - Iteration 96
# STEP 1: PROBLEM
In a simple library management system, books are the primary entities that need to be managed. The system should allow users to add, remove, and display book details dynamically. The details of each book include its title, author, and publication year.

The program should start with an empty list of books and provide a menu-driven interface to perform the following operations:
1. Add a new book to the system.
2. Remove a book from the system by its title.
3. Display all books in the system.
4. Display the details of a specific book by its title.
5. Exit the program.

### EXAMPLE
If the user adds two books: "Book1" by "Author1" published in 2020, and "Book2" by "Author2" published in 2021, and then chooses to display all books, the output should be:
```
Book1 by Author1 (2020)
Book2 by Author2 (2021)
```
If the user then removes "Book1" and displays all books again, the output should be:
```
Book2 by Author2 (2021)
```

### CONSTRAINTS
- Must use a `struct` to represent a book, with members for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free` to manage the list of books.
- If a menu is implemented, it must include a specific option to exit the program, which is option 5 or the keyword 'EXIT'. 

### MENU SPECIFICATION
If a menu is implemented, it should look something like this:
```
1. Add a new book
2. Remove a book by title
3. Display all books
4. Display a specific book by title
5. EXIT
```
Choose an option: 

Note: The program should handle memory leaks by freeing allocated memory when a book is removed or when the program exits.

---

## Problem 77 - llama-3.3-70b-versatile - Iteration 97
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The librarian needs to store the book's title, author, and publication year. The librarian also wants to be able to add, remove, and display books.

Here is the background story and context for the problem:
The librarian has a limited amount of space to store the books, so the program needs to dynamically allocate memory to store the books.

The program must meet the following requirements:
1. The program must allow the librarian to add a book by entering the title, author, and publication year.
2. The program must allow the librarian to remove a book by entering the title of the book.
3. The program must allow the librarian to display all the books in the library.
4. The program must allow the librarian to search for a book by title and display its details.

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
3. The solution must be implemented using dynamic memory allocation (malloc, free) to store the books.
4. The program must have a menu with the following options:
   - Add a book (Option 1)
   - Remove a book (Option 2)
   - Display all books (Option 3)
   - Search for a book (Option 4)
   - EXIT the program (Option 5)

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020
```
Example Output:
```
Book added successfully!
```
Then, if the librarian chooses to display all books:
```
Enter your choice: 3
Book1 by Author1, published in 2020
```
The librarian can also search for a book:
```
Enter your choice: 4
Enter book title to search: Book1
Book1 by Author1, published in 2020
```
If the librarian chooses to exit the program:
```
Enter your choice: 5
Exiting the program...
```

---

## Problem 78 - llama-3.3-70b-versatile - Iteration 98
# STEP 1: PROBLEM
Imagine you are a librarian responsible for managing a collection of books in a library. You want to create a program that allows you to add, remove, and display books from the collection. The program should use dynamic memory allocation to store the book information.

The library has the following requirements for the program:
1. The program should allow users to add a new book to the collection by providing the book's title, author, and publication year.
2. The program should allow users to remove a book from the collection by providing the book's title.
3. The program should allow users to display all the books in the collection.
4. The program should allow users to display the details of a specific book.

Here's a simple example of the expected input/output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a specific book
5. Exit

User input: 1
Enter book title: "Introduction to CS"
Enter book author: "John Doe"
Enter publication year: 2020

User input: 3
Book 1:
Title: "Introduction to CS"
Author: "John Doe"
Year: 2020

User input: 5
Exiting program...
```

### CONSTRAINTS
- Must use a `struct` to represent a book, with members for title, author, and publication year.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of a specific book must be in a function called `displayBook`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu navigation, called `handleMenu`.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 5.
- The program must use `malloc` and `free` to dynamically allocate and deallocate memory for the books.

---

## Problem 79 - llama-3.3-70b-versatile - Iteration 99
# STEP 1: PROBLEM
In a university setting, the management wants to keep track of the books in the library using a dynamic memory allocation system. The system should be able to add, remove, and display book details. Each book has a unique ID, title, author, and publication year.

The program should be designed to handle the dynamic allocation and deallocation of memory for the books. The system starts with no books and provides options to add a new book, remove a book, display all books, and exit the program.

### REQUIREMENTS
1. The program should be able to dynamically allocate memory for new books.
2. The program should be able to deallocate memory for removed books.
3. The program should display a menu with the following options:
   - Add a new book
   - Remove a book
   - Display all books
   - Exit the program
4. When adding a new book, the program should prompt for the book's ID, title, author, and publication year.
5. When removing a book, the program should prompt for the book's ID and remove the corresponding book from the system.
6. When displaying all books, the program should show the details of all the books in the system.

### EXAMPLE
If the user adds two books with the following details:
- Book 1: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
- Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021

The output of the "Display all books" option should be:
```
Book 1:
ID: 1
Title: Book1
Author: Author1
Year: 2020

Book 2:
ID: 2
Title: Book2
Author: Author2
Year: 2021
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle the menu and the operations.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4.

### MENU IMPLEMENTATION
If a menu is implemented, the options should be numbered as follows:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit the program

To exit the program, the user must select option 4.

---

## Problem 80 - llama-3.3-70b-versatile - Iteration 100
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a small library. The library has a limited budget and can only store a certain number of books at a time. To efficiently manage the collection, you decide to create a program to keep track of the books. The program will allow you to add, remove, and display books.

Background:
The library wants to keep track of the title, author, and publication year of each book. The program should be able to handle a dynamic number of books, as the library's collection is constantly changing.

Requirements:
1. The program must be able to add a new book to the collection.
2. The program must be able to remove a book from the collection by its title.
3. The program must be able to display all the books in the collection.
4. The program must be able to display the details of a specific book by its title.

Example Input/Output:
```
Menu:
1. Add a book
2. Remove a book
3. Display all books
4. Display a book
5. EXIT

Choose an option: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Choose an option: 3
Title: Harry Potter, Author: J.K. Rowling, Year: 1997

Choose an option: 4
Enter book title: Harry Potter
Title: Harry Potter, Author: J.K. Rowling, Year: 1997
```

### CONSTRAINTS
- The program must use a `struct` to represent a book, containing the title, author, and publication year.
- The logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented using dynamic memory allocation with `malloc` and `free`.
- The program must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a book
  5. EXIT (to exit the program)
- The program must handle memory allocation and deallocation correctly to prevent memory leaks.

---

## Problem 81 - openai/gpt-oss-120b - Iteration 61
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “Student Registry” program for a small tutoring centre. The centre keeps a **dynamic** list of students that can grow or shrink while the program is running. Each student record stores the student’s **ID number**, **full name**, and the **average grade** (a floating‑point value). Because the number of students is not known in advance, you must allocate and free memory at runtime using `malloc` and `free`.

## Requirements  

Write a C program that implements the following functionality:

1. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit). The menu must contain at least the following options, each identified by a distinct number:  
   1. **Add a new student** – Prompt the user for ID, name, and average grade, allocate a new `struct` for the student, and store it in the dynamic list.  
   2. **Delete a student** – Prompt for a student ID, locate the matching record, remove it from the list, and free the associated memory. If the ID is not found, display an appropriate message.  
   3. **Display a student** – Prompt for a student ID and print the stored information for that student. If the ID does not exist, report it.  
   4. **List all students** – Print the details of every student currently stored, in the order they were added.  
   5. **Exit** – Terminate the program after freeing all allocated memory.  

2. The program must maintain the list of students in a **dynamic array** that expands as needed (you may re‑allocate the array with `realloc` or maintain a linked structure – either is acceptable, but you must use `malloc`/`free` explicitly).  

3. All input is entered via `stdin`; all output is written to `stdout`.  

4. The program must **not leak memory**: every block obtained with `malloc` (or `realloc`) must eventually be released with `free` before the program ends.

## Example Input / Output  

```
=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 101
Enter name: Alice Johnson
Enter average grade: 88.5
Student added.

=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 1
Enter ID: 102
Enter name: Bob Smith
Enter average grade: 91.0
Student added.

=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 4
ID: 101 | Name: Alice Johnson | Avg: 88.50
ID: 102 | Name: Bob Smith     | Avg: 91.00

=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 3
Enter ID to display: 101
ID: 101 | Name: Alice Johnson | Avg: 88.50

=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 2
Enter ID to delete: 101
Student removed.

=== Student Registry ===
1. Add student
2. Delete student
3. Display student
4. List all students
5. Exit
Choose an option: 5
Goodbye!
```

*(The exact wording of prompts is not mandatory, but the interaction flow must follow the described options.)*  

## ### CONSTRAINTS  

1. **Data structure** – The primary entity must be represented by a `struct` named `Student` containing at least the fields `int id; char *name; float avg;`.  
2. **Display function** – The logic for showing the details of **one specific student** must reside in a function with the exact prototype:  

   ```c
   void displayStudent(const Student *s);
   ```  

3. **Memory handling** –  
   * The `name` field must be stored in dynamically allocated memory (e.g., using `malloc`/`strdup`).  
   * When a student is deleted, both the `Student` struct and its `name` buffer must be freed.  
   * Upon exiting, all remaining student structs and their name buffers must be freed.  

4. **Menu requirement** – The menu must include an explicit option to **EXIT** the program, identified by the number **5** (as shown in the example). Selecting this option ends the loop and triggers the final cleanup.  

5. **Single‑responsibility functions** – Apart from `main`, you must implement at least the following helper functions (you may add more if you wish):  
   * `Student *createStudent(int id, const char *name, float avg);` – allocates and returns a new student.  
   * `void displayStudent(const Student *s);` – prints a single student.  
   * `int findStudentIndex(const Student *list, size_t count, int id);` – returns the index of the student with the given ID or `-1` if not found.  

6. **Standard library only** – Use only the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries are permitted.  

Your solution will be evaluated on correctness, proper use of dynamic memory (`malloc`/`free`), adherence to the constraints, and clean, readable code.

---

## Problem 82 - openai/gpt-oss-120b - Iteration 62
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its computer‑based catalogue.  Each book record consists of a title (up to 100 characters), an author name (up to 50 characters), the year of publication, and the number of copies currently owned.  The catalogue will be stored in memory while the program runs; records are added and removed dynamically as the librarian works.  

Your task is to write a small C program that lets the librarian manage this catalogue using **dynamic memory allocation** (`malloc`, `realloc`, `free`).  The program must keep the collection in a **single dynamically‑allocated array of structs** that can grow or shrink as books are inserted or deleted.

## Requirements  

1. **Data structure**  
   * Define a `struct Book` that holds the four fields described above.  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   * **1 – Add a book**  
     * Prompt for title, author, year, and copies.  
     * Append the new book to the end of the dynamic array, expanding it with `realloc` as needed.  
   * **2 – Remove a book**  
     * Prompt for the *index* (starting at 0) of the book to delete.  
     * If the index is valid, remove that entry by shifting later elements left and shrinking the array with `realloc`.  
   * **3 – List all books**  
     * Print each stored book on a separate line, showing its index and all fields.  
   * **4 – Show a single book**  
     * Prompt for an index and display only that book’s details.  
     * The display logic **must be implemented in a function called `displayBook`** that receives a pointer to a `struct Book`.  
   * **5 – EXIT** – terminate the program (must be option 5).  

3. **Memory management**  
   * All memory allocated for the array must be released before the program exits.  
   * No memory leaks are tolerated; each successful `malloc`/`realloc` must have a matching `free`.  

4. **Input validation**  
   * If the user selects an invalid menu option or provides an out‑of‑range index, print an error message and redisplay the menu.  

## Example Interaction  

```
=== Library Catalogue ===
1. Add a book
2. Remove a book
3. List all books
4. Show a single book
5. EXIT
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Enter copies: 3
Book added.

=== Library Catalogue ===
1. Add a book
2. Remove a book
3. List all books
4. Show a single book
5. EXIT
Choose an option: 3

[0] Title: The C Programming Language
    Author: Kernighan & Ritchie
    Year: 1978
    Copies: 3

=== Library Catalogue ===
1. Add a book
2. Remove a book
3. List all books
4. Show a single book
5. EXIT
Choose an option: 4

Enter index of book to display: 0
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1978
Copies: 3

=== Library Catalogue ===
1. Add a book
2. Remove a book
3. List all books
4. Show a single book
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Book`.  
* **Display function** – The logic for displaying the details of ONE specific book must be placed in a function named `displayBook` with the prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Single additional function** – Apart from `main` and `displayBook`, you may define helper functions, but the core dynamic‑array manipulation (add, remove, list) should be performed directly in `main` to keep the program simple.  
* **Menu exit option** – The menu must include option **5 – EXIT** (or the exact keyword “EXIT”) that terminates the program.  

*The program must compile with a standard C compiler (`gcc -std=c99`) and run without memory‑leak warnings when checked with tools such as Valgrind.*

---

## Problem 83 - openai/gpt-oss-120b - Iteration 63
# STEP 1: PROBLEM  

## Background  
You have been hired by the **City Library** to develop a small command‑line utility that keeps track of **book reservations** made by patrons.  
Each reservation records the patron’s name, the title of the book, and the number of days the patron intends to keep the book.  
Because the library does not know in advance how many reservations will be entered each day, the program must allocate memory dynamically for each reservation and release it when the reservation is cancelled.

## Program Requirements  

Your program must:

1. **Maintain a list of reservations** in memory using dynamic allocation (`malloc`/`calloc`/`realloc`).  
2. **Support the following operations**, presented to the user through a text menu:  
   - **(1) Add a reservation** – Prompt for patron name, book title, and loan length (in days). Create a new reservation record and store it in the list.  
   - **(2) Cancel a reservation** – Prompt for the patron name. If a reservation with that name exists, remove it from the list and free the associated memory. If multiple reservations share the same name, cancel the *first* one found.  
   - **(3) List all reservations** – Display every stored reservation in the order they were added.  
   - **(4) Find a reservation** – Prompt for a patron name and display the details of that reservation (or a “not found” message).  
   - **(5) EXIT** – Terminate the program, freeing any remaining allocated memory.  

3. **Validate input** where reasonable (e.g., loan length must be a positive integer).  

4. **Use a `struct`** named `Reservation` to represent a single reservation. The struct must contain at least the three fields mentioned above (name, title, days).  

5. **Implement the display logic** for a single reservation in a separate function with the exact prototype:  

   ```c
   void displayReservation(const Reservation *r);
   ```

6. **All dynamic memory operations** (allocation, reallocation, deallocation) must be performed explicitly; you may not use global or static arrays to store the reservations.

## Example Interaction  

```
--- Library Reservation System ---
1) Add reservation
2) Cancel reservation
3) List all reservations
4) Find reservation
5) EXIT
Choose an option: 1

Enter patron name: Alice
Enter book title:  The C Programming Language
Enter loan length (days): 14
Reservation added.

--- Library Reservation System ---
1) Add reservation
2) Cancel reservation
3) List all reservations
4) Find reservation
5) EXIT
Choose an option: 1

Enter patron name: Bob
Enter book title:  Introduction to Algorithms
Enter loan length (days): 21
Reservation added.

--- Library Reservation System ---
1) Add reservation
2) Cancel reservation
3) List all reservations
4) Find reservation
5) EXIT
Choose an option: 3

Current reservations:
Patron: Alice
Book:   The C Programming Language
Days:   14

Patron: Bob
Book:   Introduction to Algorithms
Days:   21

--- Library Reservation System ---
1) Add reservation
2) Cancel reservation
3) List all reservations
4) Find reservation
5) EXIT
Choose an option: 4

Enter patron name to find: Bob
Patron: Bob
Book:   Introduction to Algorithms
Days:   21

--- Library Reservation System ---
1) Add reservation
2) Cancel reservation
3) List all reservations
4) Find reservation
5) EXIT
Choose an option: 5
Goodbye!
```

*(The exact formatting of prompts and output is not critical, but the information shown must match the example.)*  

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be a `struct Reservation` containing at least the fields `char *name; char *title; int days;`.  
- **Display Function** – The details of a single reservation must be printed by a function named `displayReservation` with the prototype shown above.  
- **Menu Exit** – The menu must include an explicit option (number **5** in the example) labelled **EXIT** that terminates the program.  
- **Memory Management** – Every call to `malloc`/`calloc`/`realloc` must have a matching `free` before the program ends or when a reservation is removed.  
- **No Global Arrays** – You may not declare a fixed‑size array to hold the reservations; the list must grow/shrink dynamically (e.g., using a pointer to an array that is reallocated).  

*Feel free to add minor user‑interface niceties, but all functional requirements and constraints above must be satisfied.*

---

## Problem 84 - openai/gpt-oss-120b - Iteration 64
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small command‑line utility for the “Campus Library” that keeps track of the books currently on loan.  
Each loan record stores the **title** of the book (a string of up to 100 characters), the **borrower’s name** (up to 50 characters), and the **number of days** the book has been borrowed.  

Because the number of active loans changes at run‑time, you must allocate and free memory dynamically. The program will let the librarian add new loan records, remove records that have been returned, and view the details of a particular loan.

## Requirements  
Write a C program that:

1. Defines a `struct Loan` that holds the three fields described above.  
2. Uses `malloc` (or `calloc`) to create a new `Loan` each time the librarian adds a loan record.  
3. Stores pointers to the created `Loan` objects in a **dynamic array** (i.e., an array whose size grows with `realloc`).  
4. Provides a text‑based menu with the following options (the numbers are mandatory):  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new loan** – Prompt for title, borrower name, and days borrowed; allocate a new `Loan` and append it to the array. |
   | 2      | **Remove a loan** – Prompt for the index (starting at 0) of the loan to delete; free its memory and shrink the array accordingly. |
   | 3      | **Display a loan** – Prompt for the index of the loan; call a function `displayLoan` (see below) to print its details. |
   | 4      | **List all loans** – Iterate over the array and print each loan’s index and title. |
   | 5      | **Exit** – Terminate the program, freeing any remaining allocated memory. |

5. Implements a function `void displayLoan(const struct Loan *p)` that prints a single loan in the exact format shown in the example.  
6. Frees **all** dynamically allocated memory before the program terminates.  

## Example Interaction  

```
=== Campus Library Loan Manager ===
1) Add a new loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 1
Enter book title: The C Programming Language
Enter borrower name: Alice Johnson
Enter days borrowed: 12
Loan added successfully.

1) Add a new loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 1
Enter book title: Introduction to Algorithms
Enter borrower name: Bob Smith
Enter days borrowed: 7
Loan added successfully.

1) Add a new loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 4
[0] The C Programming Language
[1] Introduction to Algorithms

1) Add a new loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 3
Enter loan index to display: 0
--- Loan Details ---
Title          : The C Programming Language
Borrower       : Alice Johnson
Days Borrowed  : 12

1) Add a new loan
2) Remove a loan
3) Display a loan
4) List all loans
5) Exit
Select an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Loan`.  
* **Display Function** – The logic for showing the details of **one** specific loan must reside in a function named `displayLoan`.  
* **Menu Exit** – The menu must contain the option **5) Exit** (or the keyword `EXIT`) that terminates the program.  
* **Dynamic Allocation Only** – All loan records must be created with `malloc`/`calloc` and released with `free`. No static or global arrays of `struct Loan` are allowed.  
* **Single‑File Implementation** – The entire solution must be placed in one source file (e.g., `loan_manager.c`). Apart from `main`, you may define additional helper functions, but the core functionality must obey the constraints above.  

---

## Problem 85 - openai/gpt-oss-120b - Iteration 65
# STEP 1: PROBLEM  

## Background  
A small community library wants to keep a **runtime‑only** catalogue of its books while the program is running. The catalogue should be able to grow and shrink as the librarian adds new titles or removes old ones. Because the number of books is not known in advance, the program must allocate and free memory dynamically.

Your task is to write a C program that lets the user manage this catalogue through a simple text‑based menu.

## Requirements  

1. **Data representation**  
   * Define a `struct Book` that stores:  
     * an integer `id` (unique identifier),  
     * a string `title` (maximum 100 characters),  
     * a string `author` (maximum 100 characters).  

2. **Menu** – The program repeatedly displays the following options and performs the chosen action:  

   | Choice | Action |
   |--------|--------|
   | 1 | **Add a new book** – Prompt for `id`, `title`, and `author`. Allocate a new `Book` with `malloc` and store its pointer in a dynamic array that grows as needed. |
   | 2 | **Remove a book** – Prompt for the `id` of the book to delete. Find the matching `Book`, free its memory, and compact the array so that there are no gaps. |
   | 3 | **Display a book** – Prompt for the `id`. Locate the book and print all its fields using a dedicated function `displayBook`. |
   | 4 | **List all books** – Print the details of every book currently stored, in the order they were added. |
   | 5 | **Exit** – Terminate the program gracefully, freeing any remaining allocated memory. *(This option **must** be present as the exit command.)* |

3. **Dynamic array management**  
   * The array that holds the pointers to `Book` structures must itself be allocated with `malloc` (or `realloc`) and resized whenever a book is added or removed. Do **not** use a fixed‑size array.

4. **Error handling**  
   * If the user tries to add a book with an `id` that already exists, print an error and do not insert a duplicate.  
   * If the user requests removal or display of a non‑existent `id`, print an appropriate message.  

5. **Program termination**  
   * Before exiting, free every `Book` that is still allocated and also free the dynamic array that holds the pointers.

## Example Input / Output  

```
--- Library Catalogue ---
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Enter choice: 1
Enter book id: 101
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added.

--- Library Catalogue ---
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Enter choice: 1
Enter book id: 102
Enter title: Clean Code
Enter author: Robert C. Martin
Book added.

--- Library Catalogue ---
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Enter choice: 3
Enter book id to display: 101
Book ID: 101
Title : The C Programming Language
Author: Kernighan & Ritchie

--- Library Catalogue ---
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Enter choice: 4
Book ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie
Book ID: 102 | Title: Clean Code | Author: Robert C. Martin

--- Library Catalogue ---
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be represented by a `struct Book`.  
* **Display function** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```

* **Dynamic allocation only** – All memory for `Book` instances and the array of pointers must be obtained with `malloc`/`realloc` and released with `free`. No static or global arrays of fixed size are allowed.  
* **Menu exit option** – The menu must contain an explicit option (choice 5 in the example) that terminates the program. Selecting this option must cause the program to free all allocated memory before exiting.  

Feel free to add any helper functions you need, but the above constraints must be respected.

---

## Problem 86 - openai/gpt-oss-120b - Iteration 66
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **EcoTrack**, a small startup that maintains a dynamic list of sensor devices deployed in a forest to monitor environmental conditions. Each sensor reports its **ID**, **type** (e.g., temperature, humidity, light), and the **last measured value**. The number of sensors is not known at compile‑time; they can be added or removed while the program is running.  

Your task is to write a C program that lets a user manage this list using dynamic memory allocation (`malloc`, `realloc`, `free`). The program will be used in a command‑line interface and must present a simple text menu.

## Requirements  

1. **Data representation**  
   * Define a `struct Sensor` that holds:
     * an integer `id`
     * a string `type` (maximum 20 characters)
     * a `float` `value`
2. **Menu‑driven operations** (the program should loop until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new sensor** – Prompt for `id`, `type`, and `value`. Allocate space for the new sensor and store it at the end of the current list. |
   | 2 | **Remove a sensor** – Prompt for an `id`. If a sensor with that `id` exists, delete it, shift the remaining elements to fill the gap, and shrink the allocated array. If it does not exist, print an informative message. |
   | 3 | **Update a sensor’s value** – Prompt for an `id` and a new `value`. If the sensor exists, change its `value`; otherwise, report that the sensor was not found. |
   | 4 | **Display a sensor** – Prompt for an `id` and show all fields of that sensor. The actual printing must be performed by a function named `displaySensor`. |
   | 5 | **List all sensors** – Print the details of every sensor in the order they are stored. |
   | 0 | **Exit** – Free all allocated memory and terminate the program. |

3. **Memory handling**  
   * The array of `struct Sensor` must be allocated with `malloc` (or `calloc`) and resized with `realloc` whenever sensors are added or removed.  
   * When the program terminates (option 0), every block obtained from `malloc`/`realloc` must be released with `free`.  

4. **User interaction**  
   * All prompts and messages should be clear and user‑friendly.  
   * Input validation is not required beyond what is described (e.g., you may assume the user enters an integer when an integer is requested).  

## Example Input / Output  

```
=== EcoTrack Sensor Manager ===
1) Add sensor
2) Remove sensor
3) Update sensor value
4) Display sensor
5) List all sensors
0) Exit
Choose an option: 1
Enter sensor ID: 101
Enter sensor type: temperature
Enter sensor value: 23.5
Sensor added.

1) Add sensor
2) Remove sensor
3) Update sensor value
4) Display sensor
5) List all sensors
0) Exit
Choose an option: 1
Enter sensor ID: 202
Enter sensor type: humidity
Enter sensor value: 48.2
Sensor added.

1) Add sensor
2) Remove sensor
3) Update sensor value
4) Display sensor
5) List all sensors
0) Exit
Choose an option: 5
ID: 101 | Type: temperature | Value: 23.50
ID: 202 | Type: humidity    | Value: 48.20

1) Add sensor
2) Remove sensor
3) Update sensor value
4) Display sensor
5) List all sensors
0) Exit
Choose an option: 4
Enter sensor ID to display: 101
ID: 101 | Type: temperature | Value: 23.50

1) Add sensor
2) Remove sensor
3) Update sensor value
4) Display sensor
5) List all sensors
0) Exit
Choose an option: 0
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Sensor`.  
* **Function requirement** – The logic for printing the details of a single sensor must reside in a function with the exact prototype:  

  ```c
  void displaySensor(const struct Sensor *s);
  ```  

* **Memory allocation** – Only `malloc`, `realloc`, and `free` may be used for managing the dynamic array. No global or static arrays of sensors are allowed.  
* **Menu exit** – The menu must contain an option **0) Exit** that terminates the program after releasing all allocated memory.  

Feel free to add any helper functions you deem necessary, but the above constraints must be satisfied. Good luck!

---

## Problem 87 - openai/gpt-oss-120b - Iteration 67
# STEP 1: PROBLEM  

## Background  
The campus IT department is building a tiny “Student Registry” that runs as a console program.  
Each student record consists of a **name** (a string of up to 30 characters) and an **ID number** (an integer).  
Because the number of students is not known in advance, the program must allocate memory for each record dynamically as the user adds them, and release the memory when a record is removed or when the program terminates.

## Requirements  

Write a C program that implements the following functionality:

1. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit).  
2. **Add a student** – prompt for the name and ID, allocate a `struct Student` with `malloc`, store the data, and keep the pointer in a dynamic array (the array itself may also be resized with `realloc`).  
3. **Delete a student** – ask for an ID, locate the matching record, free its memory, and compact the dynamic array so that no “holes” remain.  
4. **Display a student** – ask for an ID and print the corresponding name and ID. The printing logic must be placed in a function named `displayStudent`.  
5. **List all students** – print every stored record in the order they were added.  
6. **Exit** – before terminating, free **all** memory that was allocated during the program’s execution.  

The program should handle invalid inputs gracefully (e.g., trying to delete or display a non‑existent ID).

## Example Input / Output  

```
--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter name: Alice
Enter ID: 1001
Student added.

--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 1
Enter name: Bob
Enter ID: 1002
Student added.

--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 4
ID: 1001, Name: Alice
ID: 1002, Name: Bob

--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 3
Enter ID to display: 1002
ID: 1002, Name: Bob

--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 2
Enter ID to delete: 1001
Student removed.

--- Student Registry ---
1) Add student
2) Delete student
3) Display student
4) List all students
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be defined as  

  ```c
  typedef struct {
      int id;
      char *name;   // dynamically allocated string
  } Student;
  ```

* **Function Requirement** – The logic that prints a single student’s details must be placed in a function with the exact prototype  

  ```c
  void displayStudent(const Student *s);
  ```

* **Memory Management** –  
  * Every `malloc`/`realloc` call must have a matching `free`.  
  * The program must not leak memory; all allocated memory must be released before exiting.

* **Menu Requirement** – The menu must contain an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option terminates the loop and triggers the final cleanup.

* **Single‑source file** – The entire solution must be written in one `.c` file, but you may define as many helper functions as you need (aside from `main`).  

* **No global dynamic arrays** – The dynamic array that holds the pointers to `Student` structures must be created inside `main` (or a function called from `main`) and passed to helper functions as needed; do not use global variables for this purpose.  

* **String handling** – The student’s name must be stored in a separate dynamically allocated block (use `malloc`/`strdup`), not as a fixed‑size array inside the struct.  

* **Error messages** – When an operation cannot be performed (e.g., ID not found), print a clear message and return to the menu.  

---  

Implement the program according to the above description and constraints. Your solution will be evaluated on correctness, proper use of `malloc`/`free`, adherence to the required function signatures, and clean handling of edge cases.

---

## Problem 88 - openai/gpt-oss-120b - Iteration 68
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Library** to write a small C program that keeps track of the books currently on loan. The library does not want a permanent database – it only needs a temporary list that lives while the program runs. Each book record should contain the title, the author’s name, and the number of days the book has been borrowed. Because the number of books on loan can change during the execution (students may borrow or return books), you must allocate and free memory dynamically.

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that holds:  
     - `char *title` – dynamically allocated string (maximum length 100 characters).  
     - `char *author` – dynamically allocated string (maximum length 100 characters).  
     - `int daysBorrowed` – number of days the book has been on loan.  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new book** – Prompt the user for title, author, and days borrowed, allocate a new `Book`, store it in a dynamic array that grows as needed, and confirm the addition. |
   | 2      | **Remove a book** – Ask for the title of the book to remove. If the title exists, free all memory associated with that `Book`, shift the remaining elements in the array to fill the gap, shrink the array, and confirm removal. If the title is not found, print an appropriate message. |
   | 3      | **Display a book** – Ask for the title, locate the matching `Book`, and call the function `displayEntity` to print its details (title, author, days borrowed). If the title is not found, inform the user. |
   | 4      | **List all books** – Iterate over the dynamic array and call `displayEntity` for each stored book. If no books are stored, print “No books on loan.” |
   | 5      | **Exit** – Terminate the program after freeing **all** allocated memory. |

3. **Memory Management**  
   * Use `malloc` (or `calloc`) to allocate memory for each new `Book` and for the strings inside it.  
   * Use `realloc` to grow or shrink the array that holds pointers to `Book` structures.  
   * Every allocation must have a matching `free` before the program ends or when a book is removed.  

4. **Program Flow**  
   * The program starts with an empty list (no books).  
   * After each operation (except Exit), the menu is shown again.  

## Example Input / Output  

```
=== Library Loan Tracker ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter days borrowed: 12
Book added successfully!

=== Library Loan Tracker ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 1

Enter title: Introduction to Algorithms
Enter author: Cormen, Leiserson, Rivest, Stein
Enter days borrowed: 5
Book added successfully!

=== Library Loan Tracker ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 4

--- Book 1 ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Days Borrowed: 12

--- Book 2 ---
Title : Introduction to Algorithms
Author: Cormen, Leiserson, Rivest, Stein
Days Borrowed: 5

=== Library Loan Tracker ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 3

Enter title to display: Introduction to Algorithms
--- Book Details ---
Title : Introduction to Algorithms
Author: Cormen, Leiserson, Rivest, Stein
Days Borrowed: 5

=== Library Loan Tracker ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct Book` as described above.  
2. **Display Function** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

   ```c
   void displayEntity(const struct Book *b);
   ```  

3. **Menu Implementation** – The program must present a menu (options 1‑5) and **must** include option **5** to EXIT the program, freeing all allocated memory before termination.  
4. **Dynamic Allocation Only** – No static arrays of fixed size may be used to store the collection of books; you must manage the collection with `malloc`/`realloc`/`free`.  
5. **Single‑File Solution** – All code must reside in one source file (`.c`). Apart from `main`, you may create additional helper functions, but the only required extra function is `displayEntity`.  

*Feel free to add any minor helper functions (e.g., for input handling) as long as the above constraints are satisfied.*

---

## Problem 89 - openai/gpt-oss-120b - Iteration 69
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus Events Office** to write a small utility that keeps track of **event volunteers**.  
Each volunteer has a name (maximum 30 characters), an integer ID, and the number of hours they have pledged to work.  
The office wants a simple console program that lets a user **add**, **remove**, **list**, and **query** volunteers while the program is running.  
Because the number of volunteers is not known in advance and can change during execution, you must allocate and free memory dynamically.

## Requirements  

Write a C program that provides the following functionality through a text‑based menu:

1. **Add a volunteer**  
   * Prompt for the volunteer’s name, ID, and pledged hours.  
   * Allocate a new `struct Volunteer` on the heap and store the data.  
   * Insert the new volunteer at the end of the current list.

2. **Remove a volunteer**  
   * Prompt for the volunteer’s ID.  
   * Search the list; if the ID exists, remove that volunteer, free the associated memory, and close the gap in the list (i.e., shift later elements forward).  
   * If the ID is not found, display an appropriate message.

3. **List all volunteers**  
   * Print a table showing the ID, name, and pledged hours of every volunteer currently stored, in the order they were added.

4. **Show a volunteer’s details**  
   * Prompt for an ID, locate the volunteer, and display the information using a dedicated function called `displayVolunteer`.  
   * If the ID does not exist, inform the user.

5. **Exit**  
   * Before terminating, free any memory that remains allocated.

The program should continue to display the menu after each operation until the user selects the **Exit** option.

## Example Interaction  

```
=== Volunteer Management System ===
1) Add volunteer
2) Remove volunteer
3) List all volunteers
4) Show volunteer details
5) Exit
Choose an option: 1

Enter name: Alice Johnson
Enter ID: 101
Enter pledged hours: 12

Volunteer added successfully.

=== Volunteer Management System ===
1) Add volunteer
2) Remove volunteer
3) List all volunteers
4) Show volunteer details
5) Exit
Choose an option: 1

Enter name: Bob Lee
Enter ID: 102
Enter pledged hours: 8

Volunteer added successfully.

=== Volunteer Management System ===
1) Add volunteer
2) Remove volunteer
3) List all volunteers
4) Show volunteer details
5) Exit
Choose an option: 3

ID   Name           Hours
101  Alice Johnson  12
102  Bob Lee        8

=== Volunteer Management System ===
1) Add volunteer
2) Remove volunteer
3) List all volunteers
4) Show volunteer details
5) Exit
Choose an option: 4

Enter ID to display: 102
Volunteer Details:
ID: 102
Name: Bob Lee
Pledged Hours: 8

=== Volunteer Management System ===
1) Add volunteer
2) Remove volunteer
3) List all volunteers
4) Show volunteer details
5) Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Volunteer` containing at least the fields `char name[31]; int id; int hours;`.  
* **Display Function** – The logic for displaying the details of a single volunteer must reside in a function with the exact prototype:  
  ```c
  void displayVolunteer(const struct Volunteer *v);
  ```  
* **Dynamic Allocation** – All volunteers must be stored in dynamically allocated memory (using `malloc`/`realloc`/`free`). No static or global arrays of fixed size are allowed.  
* **Menu Implementation** – The program must present a menu as shown above. The menu must include a distinct option to **Exit** the program (option number 5 in the example). Selecting this option must cause the program to free any remaining allocated memory and terminate gracefully.  
* **Single‑File Solution** – All code must be placed in a single source file (`.c`). Apart from `main`, you may define additional helper functions, but the only required extra function is `displayVolunteer`.  

---  

*Note:* The problem is designed for students who have just learned `malloc`, `free`, and basic struct handling. Focus on correct allocation, deallocation, and pointer manipulation rather than on sophisticated data structures.

---

## Problem 90 - openai/gpt-oss-120b - Iteration 70
# STEP 1: PROBLEM  

## Background  
A small wildlife sanctuary is building a simple console‑based database to keep track of the animals it cares for. Each animal has a name, a species, and an age (in years). The sanctuary staff will run the program, add new animals as they arrive, remove animals that are transferred out, and view the details of any animal on demand. Because the number of animals is not known in advance and changes over time, the program must allocate and free memory dynamically.

## Requirements  

Write a C program that implements the following functionality:

1. **Data Representation**  
   * Define a `struct Animal` that stores:  
     * `char *name` – a dynamically allocated string (maximum length 100 characters).  
     * `char *species` – a dynamically allocated string (maximum length 100 characters).  
     * `int age` – the animal’s age.  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   * **1 – Add a new animal**  
     * Prompt the user for name, species, and age.  
     * Allocate memory for a new `struct Animal` and for the two strings, copy the input, and store the pointer in a dynamically growing array (or linked list).  
   * **2 – Remove an animal**  
     * Prompt for the **index** (starting at 0) of the animal to delete.  
     * Free the memory for the two strings and the `struct Animal` itself, then shift remaining entries so that the array stays compact (or adjust links if you use a list).  
     * If the index is invalid, display an error message and return to the menu.  
   * **3 – Display an animal’s details**  
     * Prompt for the **index** of the animal to view.  
     * Call a function `void displayAnimal(const struct Animal *a, int index)` that prints the animal’s index, name, species, and age in a readable format.  
   * **4 – List all animals**  
     * Iterate over the collection and call `displayAnimal` for each entry.  
   * **5 – EXIT**  
     * Terminate the program after freeing **all** remaining dynamically allocated memory.  

3. **Program Flow**  
   * After completing any operation (except EXIT), the menu is shown again.  
   * The program must never leak memory: every `malloc`/`calloc`/`realloc` must have a matching `free` before the program ends or an element is removed.  

## Example Interaction  

```
=== Wildlife Sanctuary Database ===
1. Add a new animal
2. Remove an animal
3. Display an animal's details
4. List all animals
5. EXIT
Choose an option: 1
Enter name: Luna
Enter species: Red Panda
Enter age: 3
Animal added successfully.

=== Wildlife Sanctuary Database ===
1. Add a new animal
2. Remove an animal
3. Display an animal's details
4. List all animals
5. EXIT
Choose an option: 1
Enter name: Max
Enter species: African Elephant
Enter age: 12
Animal added successfully.

=== Wildlife Sanctuary Database ===
1. Add a new animal
2. Remove an animal
3. Display an animal's details
4. List all animals
5. EXIT
Choose an option: 4
[0] Name: Luna, Species: Red Panda, Age: 3
[1] Name: Max, Species: African Elephant, Age: 12

=== Wildlife Sanctuary Database ===
1. Add a new animal
2. Remove an animal
3. Display an animal's details
4. List all animals
5. EXIT
Choose an option: 3
Enter index to display: 0
[0] Name: Luna, Species: Red Panda, Age: 3

=== Wildlife Sanctuary Database ===
1. Add a new animal
2. Remove an animal
3. Display an animal's details
4. List all animals
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented by a `struct Animal` as described above.  
* **Display Function** – The logic for showing the details of **ONE** specific animal must reside in a function with the exact prototype:  
  ```c
  void displayAnimal(const struct Animal *a, int index);
  ```  
* **Menu Requirement** – Because a menu is part of the specification, the program **must** include an explicit menu option to **EXIT** the program (option 5 in the example).  
* **Dynamic Allocation Only** – All storage for animals and their name/species strings must be obtained with `malloc`/`calloc`/`realloc`. No static or global arrays of fixed size may be used to hold the animals.  
* **Memory Management** – Every allocated block must be freed exactly once. Failure to do so will be considered a compilation‑time or run‑time penalty.  

*Optional (but recommended for students):* you may implement the collection as a resizable array using `realloc`, or as a singly‑linked list. Either approach satisfies the constraints as long as dynamic allocation is used throughout.

---

## Problem 91 - openai/gpt-oss-120b - Iteration 71
# STEP 1: PROBLEM  

## Background  
You have been hired by the campus “Student Housing Office” to write a tiny command‑line utility that keeps track of the rooms currently occupied in a dormitory.  
Each occupied room is described by three pieces of information:

* **Room number** – an integer (e.g., 101, 202).  
* **Student name** – a string of up to 30 characters (no spaces).  
* **Number of occupants** – an integer (1‑4).  

The program must store these records dynamically because the number of occupied rooms changes while the program runs. When the user decides to stop using the program, all allocated memory must be released.

## Requirements  

1. **Data representation** – Define a `struct` called `Room` that holds the three fields above.  
2. **Dynamic storage** – The program must maintain a **dynamic array** of `Room` objects that can grow or shrink as rooms are added or removed. Use `malloc`, `realloc`, and `free` only (no global static arrays).  
3. **Menu‑driven interface** – Present the user with a menu that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   1. **Add a room** – Prompt for room number, student name, and occupants; insert the new record at the end of the dynamic array.  
   2. **Remove a room** – Prompt for a room number; if a room with that number exists, delete it from the array, shifting later elements forward to fill the gap. If the room does not exist, print “Room not found”.  
   3. **Display a room** – Prompt for a room number; if found, call a function `displayRoom` (see constraint) to print the details; otherwise print “Room not found”.  
   4. **List all rooms** – Print the details of every stored room in the order they were added, using `displayRoom` for each entry.  
   5. **Exit** – Free all allocated memory and terminate the program.  

4. **Input validation** – The program should not crash on invalid numeric input; you may assume the user follows the prompts for strings.  

5. **Memory cleanup** – Before exiting, all memory obtained with `malloc`/`realloc` must be released with `free`.  

## Example Interaction  

```
--- Dormitory Occupancy Manager ---
1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 1
Enter room number: 101
Enter student name: Alice
Enter number of occupants: 2
Room added.

1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 1
Enter room number: 202
Enter student name: Bob
Enter number of occupants: 1
Room added.

1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 4
Room 101 – Alice – 2 occupants
Room 202 – Bob – 1 occupant

1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 3
Enter room number to display: 101
Room 101 – Alice – 2 occupants

1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 2
Enter room number to remove: 202
Room removed.

1) Add a room
2) Remove a room
3) Display a room
4) List all rooms
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be a `struct` named `Room`.  
* **Display function** – The logic that prints the details of **one** room must be encapsulated in a function with the exact prototype:  

  ```c
  void displayRoom(const Room *r);
  ```  

* **Menu exit option** – The menu must include an explicit “Exit” choice (option 5 in the example). Selecting this option must cause the program to free all allocated memory and terminate.  
* **Single‑source file** – The entire solution must be written in one `.c` file, but you may define as many helper functions as you like (the only required helper is `displayRoom`).  

---  

*Write a program that satisfies the above specifications.*

---

## Problem 92 - openai/gpt-oss-120b - Iteration 72
# STEP 1: PROBLEM  

## Background  
You have been hired to write a tiny “library inventory” program for a small community library that keeps track of the books currently on its shelves. The library does **not** have a database; instead, it stores all information in memory while the program runs. Because the number of books can change at runtime (books are added and removed), you must allocate and free memory dynamically using `malloc` and `free`.

## Requirements  

Write a C program that allows the user to manage a collection of books. Each book has the following attributes:

| Field | Type | Description |
|-------|------|-------------|
| `title` | `char *` | The title of the book (maximum 100 characters). |
| `author` | `char *` | The author’s name (maximum 100 characters). |
| `year` | `int` | Publication year. |
| `id` | `int` | A unique integer identifier assigned by the program (starting from 1). |

The program must provide a **menu‑driven** interface with the following options:

1. **Add a new book** – Prompt the user for title, author, and year, allocate a new `Book` structure, store the data, and append it to the dynamic collection.  
2. **Remove a book by ID** – Ask for the book’s ID, locate the corresponding structure, remove it from the collection, and free its memory. If the ID does not exist, display an error message.  
3. **Display details of a book by ID** – Ask for the ID and print all fields of that book. The printing logic **must** be placed in a function called `displayBook`.  
4. **List all books** – Print the details of every book currently stored, in the order they were added.  
5. **Exit** – Terminate the program after freeing all allocated memory.

Additional functional details:

* The collection must be stored as a **dynamic array of pointers** (`Book **books`). The array itself should grow or shrink with `realloc` as books are added or removed.
* IDs are never reused; each newly added book receives the next integer (1, 2, 3, …) even if earlier books have been deleted.
* Input validation is required only for the menu choice and the book ID (must be a positive integer).  

## Example Interaction  

```
=== Library Inventory ===
1) Add a new book
2) Remove a book by ID
3) Display a book by ID
4) List all books
5) Exit
Enter choice: 1
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Book added with ID 1.

=== Library Inventory ===
1) Add a new book
2) Remove a book by ID
3) Display a book by ID
4) List all books
5) Exit
Enter choice: 1
Enter title: Clean Code
Enter author: Robert C. Martin
Enter year: 2008
Book added with ID 2.

=== Library Inventory ===
1) Add a new book
2) Remove a book by ID
3) Display a book by ID
4) List all books
5) Exit
Enter choice: 4
ID: 1 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1978
ID: 2 | Title: Clean Code | Author: Robert C. Martin | Year: 2008

=== Library Inventory ===
1) Add a new book
2) Remove a book by ID
3) Display a book by ID
4) List all books
5) Exit
Enter choice: 3
Enter ID to display: 2
ID: 2
Title: Clean Code
Author: Robert C. Martin
Year: 2008

=== Library Inventory ===
1) Add a new book
2) Remove a book by ID
3) Display a book by ID
4) List all books
5) Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity **must** be represented by a `struct` named `Book`.  
2. **Function Requirement** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

   ```c
   void displayBook(const Book *b);
   ```  

3. **Dynamic Allocation** – All memory for `Book` objects and the array that holds their pointers must be obtained with `malloc`/`realloc` and released with `free`. No static or global arrays of fixed size are allowed.  
4. **Menu Implementation** – Because a menu is required, the program **must** include an explicit menu option to **EXIT** the program (option 5 in the example). Selecting this option must cause the program to free any remaining allocated memory before terminating.  
5. **Single‑File Solution** – All code must reside in a single source file (`.c`). Apart from `main`, you may define additional helper functions (e.g., for adding, removing, resizing the array), but the `displayBook` function is mandatory.  

Your task is to write the complete program that satisfies the above specifications and constraints.

---

## Problem 93 - openai/gpt-oss-120b - Iteration 73
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **Eco‑Logistics**, a company that tracks the daily deliveries of reusable containers (e.g., water bottles, food trays). Each delivery is recorded as a *ContainerBatch* that stores:

* a unique batch ID (integer)  
* the number of containers in the batch (integer)  
* the total weight of the batch in kilograms (floating‑point)  

Because the number of batches is not known in advance and can change while the program is running, you must allocate memory dynamically for each batch record. The program will allow the user to add new batches, remove existing ones, and view details of a specific batch.

## Requirements  

Write a C program that implements a **menu‑driven** interface with the following options:

1. **Add a new batch** – Prompt the user for the batch ID, number of containers, and total weight. Allocate memory for a new `struct ContainerBatch` using `malloc` and store the data. The batch IDs must be unique; if the user enters an ID that already exists, display an error and do not add a duplicate.  
2. **Delete a batch** – Prompt for a batch ID. If a batch with that ID exists, free the memory associated with it and remove it from the list; otherwise, display “Batch not found.”  
3. **Display a batch** – Prompt for a batch ID and print all its fields in a readable format. The logic for displaying the details must be placed in a function called `displayBatch`.  
4. **List all batches** – Print the information of every batch currently stored, in the order they were added.  
5. **Exit** – Terminate the program. (This option must be present and clearly labeled as the exit choice.)

The program should keep the batches in a **singly‑linked list** (each node contains a pointer to a `ContainerBatch` and a pointer to the next node). All memory allocated for batches and list nodes must be released before the program exits.

## Example Interaction  

```
=== Eco‑Logistics Batch Manager ===
1. Add a new batch
2. Delete a batch
3. Display a batch
4. List all batches
5. Exit
Choose an option: 1

Enter batch ID: 101
Enter number of containers: 25
Enter total weight (kg): 312.5
Batch 101 added.

=== Eco‑Logistics Batch Manager ===
1. Add a new batch
2. Delete a batch
3. Display a batch
4. List all batches
5. Exit
Choose an option: 1

Enter batch ID: 102
Enter number of containers: 40
Enter total weight (kg): 480.0
Batch 102 added.

=== Eco‑Logistics Batch Manager ===
1. Add a new batch
2. Delete a batch
3. Display a batch
4. List all batches
5. Exit
Choose an option: 3

Enter batch ID to display: 101
Batch ID: 101
Containers: 25
Total weight: 312.50 kg

=== Eco‑Logistics Batch Manager ===
1. Add a new batch
2. Delete a batch
3. Display a batch
4. List all batches
5. Exit
Choose an option: 4

Batch ID: 101 | Containers: 25 | Weight: 312.50 kg
Batch ID: 102 | Containers: 40 | Weight: 480.00 kg

=== Eco‑Logistics Batch Manager ===
1. Add a new batch
2. Delete a batch
3. Display a batch
4. List all batches
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct` named `ContainerBatch`.  
* **Display Function** – The logic that prints a single batch’s details must be encapsulated in a function with the exact prototype:  
  ```c
  void displayBatch(const struct ContainerBatch *batch);
  ```  
* **Dynamic Allocation** – All `ContainerBatch` objects and list nodes must be created with `malloc` (or `calloc`) and released with `free`. No static or global arrays may be used to store batches.  
* **Menu Exit Option** – The menu must contain an explicit option (number **5** in the example) that terminates the program. Selecting this option must cause the program to free any remaining allocated memory before exiting.  
* **No Memory Leaks** – The program will be tested with tools such as Valgrind; any leaked memory will result in a loss of points.  

Feel free to add helpful prompts or error messages, but the core functionality and constraints must be respected. Good luck!

---

## Problem 94 - openai/gpt-oss-120b - Iteration 74
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior developer for **Eco‑Cart**, a small e‑commerce startup that sells reusable household items. The product catalog is stored only while the program runs; each time the application starts it must build the catalog from user input. Because the number of products is not known in advance, you must allocate memory dynamically.

Your task is to write a C program that lets the user **add**, **remove**, **list**, and **search** products in the catalog. Each product is represented by a `struct` containing an identifier, a name, a price, and a quantity in stock. All memory that is allocated with `malloc` (or `calloc`) must be released with `free` before the program terminates.

## Requirements  

1. **Data representation**  
   * Define a `struct Product` with the following fields:  
     - `int id;`       // unique product identifier (positive integer)  
     - `char *name;`   // dynamically allocated string (maximum length 100 characters)  
     - `float price;`   // price in dollars (e.g., 12.99)  
     - `int quantity;`  // units currently in stock  

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | **1**  | **Add a new product** – Prompt for id, name, price, and quantity. Allocate memory for the new `Product` and for the name string. The id must be unique; if a duplicate id is entered, print an error and discard the entry. |
   | **2**  | **Remove a product** – Prompt for an id, locate the product, free its name string and the `Product` structure, and remove it from the catalog. If the id does not exist, print a message. |
   | **3**  | **List all products** – Print a table containing id, name, price, and quantity for every product currently stored. |
   | **4**  | **Search by id** – Prompt for an id and display the details of that single product using a helper function `displayProduct`. If not found, report it. |
   | **5**  | **EXIT** – Terminate the program after freeing all remaining allocated memory. |

3. **Dynamic storage**  
   * The catalog must be stored as a **dynamically allocated array of pointers to `Product`**. The array should expand (using `realloc`) when a new product is added and shrink when a product is removed.  
   * No fixed‑size global arrays are allowed.

4. **Helper function**  
   * Implement a function `void displayProduct(const struct Product *p);` that prints a single product in the same format used by the “List all products” option.

5. **Program termination**  
   * Before exiting (whether via the menu option or an error), the program must free **all** memory that was allocated during execution.

## Example Interaction  

```
=== Eco‑Cart Product Catalog ===
1) Add product
2) Remove product
3) List all products
4) Search by id
5) EXIT
Choose an option: 1
Enter product id: 101
Enter product name: Bamboo Toothbrush
Enter price: 3.49
Enter quantity: 250
Product added.

1) Add product
2) Remove product
3) List all products
4) Search by id
5) EXIT
Choose an option: 1
Enter product id: 102
Enter product name: Reusable Water Bottle
Enter price: 15.00
Enter quantity: 80
Product added.

1) Add product
2) Remove product
3) List all products
4) Search by id
5) EXIT
Choose an option: 3

ID   Name                 Price   Qty
101  Bamboo Toothbrush    3.49    250
102  Reusable Water Bottle15.00   80

1) Add product
2) Remove product
3) List all products
4) Search by id
5) EXIT
Choose an option: 4
Enter product id to search: 101
ID: 101
Name: Bamboo Toothbrush
Price: $3.49
Quantity: 250

1) Add product
2) Remove product
3) List all products
4) Search by id
5) EXIT
Choose an option: 5
Cleaning up memory... Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be a `struct Product` as described.  
* **Function requirement** – The logic for displaying the details of ONE specific entity **must** be placed in a function named `displayProduct`.  
* **Menu exit** – The menu **must** contain an option labeled **5) EXIT** (or the keyword `EXIT`) that terminates the program.  
* **Dynamic allocation only** – All memory for products and their name strings must be obtained with `malloc`/`calloc` (or `realloc`) and released with `free`. No static or stack‑allocated arrays for the catalog are permitted.  
* **Single source file** – The entire solution should be written in one `.c` file, but you may define as many helper functions as you like (the only mandatory helper is `displayProduct`).  

---  

Write the program that satisfies the above specification, demonstrating correct use of `malloc`, `realloc`, and `free`, as well as proper handling of user input and dynamic data structures.

---

## Problem 95 - openai/gpt-oss-120b - Iteration 75
# STEP 1: PROBLEM  

## Background  
You have been hired to write a small utility for a university’s registration office. The office needs a program that can keep a **dynamic list of courses** that are being offered for the upcoming semester.  
Each course has a *course code* (a string of up to 8 characters, e.g., `CS101`), a *title* (up to 40 characters), and the *number of enrolled students* (an integer).  
Because the number of courses is not known in advance and may change during the execution of the program, you must allocate memory on the heap using `malloc`/`realloc` and release it with `free` when it is no longer needed.

## Requirements  

Write a C program that provides a **text‑based menu** with the following options:

1. **Add a new course** – Prompt the user for the course code, title, and initial enrollment, then store the information in a dynamically‑allocated array.  
2. **Remove a course** – Prompt for a course code. If a course with that code exists, delete it from the array, shifting the remaining elements as necessary, and shrink the allocated memory accordingly.  
3. **Display a course** – Prompt for a course code and, if found, show all its fields. The logic for displaying a single course **must** be placed in a function called `displayCourse`.  
4. **List all courses** – Print the details of every stored course in the order they were added.  
5. **Exit** – Terminate the program after freeing all allocated memory.  

Additional functional details:

* The program must continue to show the menu after completing any option except **Exit**.  
* If the user tries to add a course whose code already exists, print an error message and do **not** add a duplicate.  
* If the user requests to remove or display a course that does not exist, print an appropriate “not found” message.  
* All input should be read safely (e.g., using `scanf` with width limits or `fgets` followed by parsing) to avoid buffer overflows.  

## Example Interaction  

```
=== Course Management System ===
1) Add a new course
2) Remove a course
3) Display a course
4) List all courses
5) Exit
Enter choice: 1
Enter course code: CS101
Enter title: Introduction to Programming
Enter enrollment: 45
Course added.

=== Course Management System ===
1) Add a new course
2) Remove a course
3) Display a course
4) List all courses
5) Exit
Enter choice: 1
Enter course code: MATH220
Enter title: Linear Algebra
Enter enrollment: 30
Course added.

=== Course Management System ===
1) Add a new course
2) Remove a course
3) Display a course
4) List all courses
5) Exit
Enter choice: 3
Enter course code to display: CS101
Course Code: CS101
Title      : Introduction to Programming
Enrollment : 45

=== Course Management System ===
1) Add a new course
2) Remove a course
3) Display a course
4) List all courses
5) Exit
Enter choice: 4
Course Code: CS101   Title: Introduction to Programming   Enrollment: 45
Course Code: MATH220 Title: Linear Algebra                Enrollment: 30

=== Course Management System ===
1) Add a new course
2) Remove a course
3) Display a course
4) List all courses
5) Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct` named `Course` containing at least the fields `code`, `title`, and `enrollment`.  
* **Display Function** – The logic that prints the details of **one** specific course must be implemented in a function with the exact prototype:  

  ```c
  void displayCourse(const Course *c);
  ```  

* **Memory Management** – Use `malloc`/`realloc` to grow the array when a new course is added and `free` (or `realloc` to shrink) when a course is removed or when the program exits. No memory leaks are allowed.  
* **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option 5 in the example). Selecting this option must cause the program to terminate after all allocated memory has been released.  
* **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but the entire solution must reside in a single source file (e.g., `course_manager.c`).  

---  

*Your task is to write the complete program that satisfies all of the above.*

---

## Problem 96 - openai/gpt-oss-120b - Iteration 76
# STEP 1: PROBLEM  

## Background  
The campus IT department is building a tiny “Student Record Manager” that runs in a terminal.  
Each student record contains a **student ID**, **full name**, **age**, and **GPA**.  
Because the number of students is not known in advance, the program must allocate memory for each record at run‑time and release it when the record is removed or when the program terminates.

You are to implement this manager using only the C standard library functions `malloc`, `realloc`, and `free`.  

## Requirements  

Your program must present a simple text menu and perform the following operations:

1. **Add a new student**  
   - Prompt the user for the student’s ID (integer), name (string up to 50 characters, may contain spaces), age (integer), and GPA (float).  
   - Dynamically allocate a `struct Student` to hold the data and store a pointer to it in a dynamically‑grown array (use `realloc` as needed).  

2. **List all students**  
   - Print a table showing the ID, name, age, and GPA of every student currently stored.  

3. **Find a student by ID**  
   - Ask for an ID, locate the matching student (if any), and display the details using the required display function.  

4. **Delete a student by ID**  
   - Ask for an ID, locate the matching student, free the memory for that student, remove the pointer from the array, and shrink the array appropriately.  

5. **Exit the program**  
   - Before terminating, free *all* memory that was allocated for student records and for the array that holds the pointers.  

The menu must be displayed after each completed operation until the user chooses the **Exit** option.

## Example Input / Output  

```
=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 1

Enter student ID: 1001
Enter name: Alice Johnson
Enter age: 20
Enter GPA: 3.75
Student added.

=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 1

Enter student ID: 1002
Enter name: Bob Lee
Enter age: 22
Enter GPA: 3.42
Student added.

=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 2

ID     Name               Age  GPA
---------------------------------------
1001   Alice Johnson      20   3.75
1002   Bob Lee            22   3.42

=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 3

Enter ID to search: 1002
Student details:
ID: 1002
Name: Bob Lee
Age: 22
GPA: 3.42

=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 4

Enter ID to delete: 1001
Student with ID 1001 deleted.

=== Student Record Manager ===
1) Add student
2) List all students
3) Find student by ID
4) Delete student by ID
5) Exit
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data structure** – You must define a `struct Student` that holds the four fields (ID, name, age, GPA).  
2. **Dynamic allocation** – Every student record must be allocated with `malloc` (or `calloc`). The array that stores the pointers to the records must also be allocated dynamically and resized with `realloc`.  
3. **Memory deallocation** – When a student is deleted, or when the program exits, the corresponding memory must be released with `free`. No memory leaks are allowed.  
4. **Display function** – The logic that prints the details of a *single* student must be placed in a function with the exact prototype:  

   ```c
   void displayStudent(const struct Student *s);
   ```  

   This function will be used by both the “Find student by ID” and “List all students” options.  
5. **Menu requirement** – The menu must contain an explicit option to **Exit** the program; it should be numbered (as in the example) and selecting it must cause the program to terminate after freeing all allocated memory.  
6. **Standard library only** – Apart from `stdio.h`, `stdlib.h`, and `string.h`, no other libraries may be used.  

---

*Design your solution so that a student who has just learned how `malloc`, `realloc`, and `free` work can implement it without needing any advanced data‑structure knowledge.*

---

## Problem 97 - openai/gpt-oss-120b - Iteration 77
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Park**, a small wildlife sanctuary that keeps a dynamic list of animals that are currently in the park. The number of animals changes every day as new ones are rescued and others are released back to the wild. The park’s computer system must be able to **add**, **remove**, and **display** information about the animals while using memory efficiently – i.e., allocating memory only when needed and releasing it when it is no longer required.

Your task is to write a C program that implements this animal‑tracking system using **dynamic memory allocation** (`malloc`, `realloc`, `free`).  

---

## Program Requirements  

1. **Data representation**  
   * Define a `struct Animal` that contains at least the following fields:  
     - `char *name` – the animal’s name (a string of arbitrary length).  
     - `int age` – age in years.  
     - `char species[30]` – species name (e.g., “Red Panda”).  

2. **Menu‑driven interface** (the program must present a textual menu repeatedly until the user chooses to exit). The menu must contain the following options (the numbers are mandatory):  
   1. **Add a new animal** – prompt for name, age, and species, allocate memory for a new `Animal`, store it in the dynamic list, and expand the list as needed.  
   2. **Remove an animal by name** – search the list for the first animal whose name matches the user‑provided string, remove it, free all memory associated with that animal, and shrink the list accordingly. If the name is not found, display an appropriate message.  
   3. **Display all animals** – list every animal currently stored, showing name, age, and species.  
   4. **Display details of ONE specific animal** – ask for a name, locate that animal, and call a helper function `displayAnimal` (see Constraints) to print its details. If the animal does not exist, inform the user.  
   5. **EXIT** – terminate the program gracefully, freeing all allocated memory.  

3. **Memory management**  
   * Use `malloc` (or `calloc`) to allocate each new `Animal`.  
   * Use `realloc` to grow/shrink the array (or linked list) that holds the pointers to the animals.  
   * Every allocated block must be released with `free` before the program ends or when an animal is removed.  

4. **Robustness**  
   * Validate user input where reasonable (e.g., non‑negative age).  
   * Do not leak memory; tools such as Valgrind should report zero leaks.  

---

## Example Interaction  

```
=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 1

Enter animal name: Luna
Enter age (years): 3
Enter species: Red Panda
Animal added successfully!

=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 1

Enter animal name: Milo
Enter age (years): 5
Enter species: Capybara
Animal added successfully!

=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 3

Current animals in the park:
1) Name: Luna, Age: 3, Species: Red Panda
2) Name: Milo, Age: 5, Species: Capybara

=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 4

Enter name of animal to display: Milo
--- Animal Details ---
Name   : Milo
Age    : 5
Species: Capybara

=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 2

Enter name of animal to remove: Luna
Animal 'Luna' removed.

=== Eco‑Park Animal Tracker ===
1. Add a new animal
2. Remove an animal by name
3. Display all animals
4. Display details of ONE specific animal
5. EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Animal` as described above.  
2. **Display function** – The logic for displaying the details of ONE specific animal **must** be placed in a separate function with the exact prototype:  

   ```c
   void displayAnimal(const struct Animal *a);
   ```  

3. **Single‑responsibility helper** – Any memory‑deallocation for a removed animal must be performed by a helper function named `freeAnimal` with prototype:  

   ```c
   void freeAnimal(struct Animal *a);
   ```  

4. **Menu requirement** – The program **must** implement the menu shown in the requirements. Option **5** must be the explicit “EXIT” choice that ends the program.  

5. **No global variables** – All data structures must be allocated dynamically and passed to functions via parameters; global variables are not allowed.  

6. **Standard library only** – You may only include headers from the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries.  

---  

*Write the program so that it compiles with `gcc -Wall -Wextra -std=c11` without warnings.*

---

## Problem 98 - openai/gpt-oss-120b - Iteration 78
# STEP 1: PROBLEM  

## Background  
You have been hired by **Eco‑Park**, a small wildlife sanctuary that tracks the animals it rescues.  Each animal record consists of a **name**, a **species**, and its **age in years**.  The sanctuary’s staff will be entering records at run‑time, and because the number of rescued animals is not known in advance, the program must allocate memory dynamically.  When an animal is released back into the wild, its record must be removed and the memory reclaimed.

Your task is to write a C program that lets the user **add**, **remove**, **list**, and **search** animal records using dynamic memory allocation (`malloc`, `free`).  

## Requirements  

1. **Data structure**  
   * Define a `struct Animal` that holds:  
     ```c
     char *name;      // dynamically allocated string
     char *species;   // dynamically allocated string
     int   age;       // age in years
     ```  

2. **Menu‑driven interface** (the program must present a menu after each operation)  
   * **1 – Add a new animal**  
     - Prompt for the animal’s name, species, and age.  
     - Allocate a new `struct Animal` and store it in a dynamically‑grown array (or linked list).  
   * **2 – Remove an animal**  
     - Prompt for the animal’s name.  
     - Find the first record whose name matches exactly (case‑sensitive).  
     - Remove that record, free all memory associated with it, and shrink the container appropriately.  
   * **3 – List all animals**  
     - Display every stored animal in the order they were added.  
   * **4 – Search by species**  
     - Prompt for a species string.  
     - Print all animals whose `species` field matches the input (exact match).  
   * **5 – EXIT** – terminate the program (must be the exact option to end the loop).  

3. **Memory management**  
   * Every string entered by the user must be stored in its own dynamically allocated buffer (use `malloc`/`realloc`).  
   * When an animal is removed, all memory belonging to that animal must be released.  
   * When the program exits, any remaining allocated memory must be freed.  

4. **Functionality decomposition**  
   * Implement a function `void displayAnimal(const struct Animal *a);` that prints a single animal in the format:  
     ```
     Name: <name>, Species: <species>, Age: <age>
     ```  
   * All other operations (add, remove, search, list) may be implemented in additional helper functions, but **no more than two functions besides `main`** are allowed.  

## Example Interaction  

```
=== Eco‑Park Animal Tracker ===
1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 1
Enter name: Luna
Enter species: Wolf
Enter age: 4
Animal added.

1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 1
Enter name: Toby
Enter species: Turtle
Enter age: 12
Animal added.

1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 3
--- Animal List ---
Name: Luna, Species: Wolf, Age: 4
Name: Toby, Species: Turtle, Age: 12

1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 4
Enter species to search: Wolf
--- Search Results ---
Name: Luna, Species: Wolf, Age: 4

1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 2
Enter name of animal to remove: Luna
Animal removed.

1. Add animal
2. Remove animal
3. List all animals
4. Search by species
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented by a `struct Animal`.  
* The function that prints a single animal **must** be named `displayAnimal`.  
* The program **must** present a menu and include the explicit option **5 – EXIT** to end execution.  
* Only **two** helper functions (in addition to `main`) are permitted; one of them must be `displayAnimal`.  
* All memory for names, species strings, and animal structures must be obtained with `malloc`/`realloc` and released with `free`.  
* No global variables may be used; all data must be passed via parameters or returned from functions.  

---

## Problem 99 - openai/gpt-oss-120b - Iteration 79
# STEP 1: PROBLEM  

## Background  
You have been hired as the software engineer for **Eco‑Park**, a small wildlife sanctuary that keeps track of the animals it rescues. The sanctuary’s database is extremely lightweight and runs on a single‑board computer with very limited RAM. For each animal the system must store a **dynamic list of health‑check records** (date and a short note). Because the number of records for any animal is not known in advance, you must allocate and free memory at run‑time using `malloc` and `free`.

Your task is to write a console program that lets a park ranger **add animals**, **append health‑check records**, **display the information for a particular animal**, and **remove an animal** (releasing all memory associated with it). The program should continue to run until the ranger chooses to exit.

## Requirements  

1. Define a `struct Animal` that contains:  
   * an integer `id` (unique identifier supplied by the user)  
   * a string `name` (max 30 characters)  
   * a pointer to an array of `struct Record` (the health‑check records)  
   * an integer `recordCount` (current number of records)  
   * an integer `recordCapacity` (size of the allocated array).  

2. Define a `struct Record` that contains:  
   * a string `date` (format `YYYY-MM-DD`, max 10 characters)  
   * a string `note` (max 100 characters).  

3. The program must present a **menu** with the following options (the numbers are mandatory):  

   1. **Add a new animal** – prompt for `id` and `name`. Allocate an `Animal` dynamically and store it in a dynamically‑grown array of animals.  
   2. **Add a health‑check record to an animal** – ask for the animal’s `id`. If the animal exists, prompt for `date` and `note`, then append the new record, expanding the record array with `realloc` when necessary.  
   3. **Display an animal’s information** – ask for the animal’s `id`. If found, call a function `displayAnimal` (see constraints) that prints the animal’s `id`, `name`, and all its records, one per line.  
   4. **Remove an animal** – ask for the animal’s `id`. If found, free all memory belonging to that animal (its records array and the `Animal` struct itself) and remove it from the animals array, shifting later entries forward.  
   5. **Exit** – terminate the program after freeing any remaining allocated memory.  

4. The menu must repeat after each operation until the user selects **Exit**.

5. All input should be read from `stdin`; all output should be written to `stdout`. The program must handle invalid menu choices and non‑existent animal IDs gracefully, printing an appropriate error message and returning to the menu.

## Example Input / Output  

```
--- Eco‑Park Animal Tracker ---
1) Add a new animal
2) Add a health‑check record
3) Display an animal
4) Remove an animal
5) Exit
Enter choice: 1
Enter animal ID: 101
Enter animal name: Leo
Animal added.

--- Eco‑Park Animal Tracker ---
1) Add a new animal
2) Add a health‑check record
3) Display an animal
4) Remove an animal
5) Exit
Enter choice: 2
Enter animal ID: 101
Enter record date (YYYY-MM-DD): 2024-11-02
Enter note: Annual dental check
Record added.

--- Eco‑Park Animal Tracker ---
1) Add a new animal
2) Add a health‑check record
3) Display an animal
4) Remove an animal
5) Exit
Enter choice: 3
Enter animal ID: 101
--- Animal 101: Leo ---
Record 1: 2024-11-02 - Annual dental check

--- Eco‑Park Animal Tracker ---
1) Add a new animal
2) Add a health‑check record
3) Display an animal
4) Remove an animal
5) Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct Animal` (as described above).  
* **Display function** – The logic for printing the details of ONE specific animal must be placed in a function with the exact prototype:  

  ```c
  void displayAnimal(const struct Animal *a);
  ```  

* **Memory management** – Every block of memory obtained with `malloc`/`realloc` must eventually be released with `free`. No memory leaks are permitted.  
* **Single‑function rule for animal list handling** – All operations that modify the dynamic array of animals (adding, removing, shifting) must be performed inside **one** helper function besides `main()` and `displayAnimal`. You may name it as you wish (e.g., `manageAnimals`).  
* **Menu exit option** – Option **5** must be labeled “Exit” and must terminate the program after freeing all remaining allocated memory.  

---  

*Note:* The problem is intended for students who have just learned `malloc`, `realloc`, `free`, and basic `struct` manipulation in C. The focus is on correct dynamic allocation, resizing, and cleanup, as well as clean modular code.*

---

## Problem 100 - openai/gpt-oss-120b - Iteration 80
# STEP 1: PROBLEM  

## Background  
You have been hired by a small library that keeps a catalog of its books only in memory while the program runs.  
Each book record contains a title, the author’s name, the year of publication, and the number of copies the library owns.  
Because the library does not know in advance how many books will be entered, you must allocate memory dynamically as books are added and release it when they are removed.

## Requirements  

Write a C program that implements a **menu‑driven** system to manage the in‑memory book catalog. The program must support the following operations:

1. **Add a new book**  
   - Prompt the user for the title (max 100 characters), author (max 100 characters), year (integer), and copies (integer).  
   - Dynamically allocate a new `Book` structure, store the data, and insert it at the end of the current list.

2. **Remove a book**  
   - Prompt the user for the title of the book to delete.  
   - Search the list for a book whose title matches exactly (case‑sensitive).  
   - If found, remove it from the list, free the memory associated with that `Book`, and shift the remaining elements so that the list stays contiguous.  
   - If not found, print “Book not found.”

3. **Display a specific book**  
   - Prompt the user for a title.  
   - Locate the book and call a function `displayBook` (see constraints) to print all its fields in a readable format.  
   - If the book does not exist, print “Book not found.”

4. **List all books**  
   - Iterate over the entire catalog and, for each book, call `displayBook` to show its details.  
   - If the catalog is empty, print “No books in the catalog.”

5. **Exit**  
   - Choose the menu option that terminates the program.  
   - Before exiting, free all memory that was allocated for the books.

The menu should be displayed after each operation until the user selects the exit option.

## Example Input / Output  

```
=== Library Catalog ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Enter copies: 3
Book added.

=== Library Catalog ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 1

Enter title: Clean Code
Enter author: Robert C. Martin
Enter year: 2008
Enter copies: 2
Book added.

=== Library Catalog ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 4

--- Book 1 ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Year  : 1978
Copies: 3

--- Book 2 ---
Title : Clean Code
Author: Robert C. Martin
Year  : 2008
Copies: 2

=== Library Catalog ===
1. Add a new book
2. Remove a book
3. Display a book
4. List all books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Structure definition** – The primary data entity must be represented by a `struct` named `Book` containing at least the fields `title`, `author`, `year`, and `copies`.  

2. **Dynamic allocation** – All `Book` instances must be allocated with `malloc` (or `calloc`) when added and released with `free` when removed or when the program exits. No static or global arrays of `Book` may be used to store the catalog.  

3. **Display function** – The logic for printing the details of **one** specific book must reside in a function with the exact prototype:  

   ```c
   void displayBook(const Book *b);
   ```  

   This function must be called both by the “Display a book” and “List all books” options.  

4. **Menu requirement** – The program must present a textual menu as shown in the example. The menu must contain an explicit option to **EXIT** the program; in the example this is option `5`. The exit option must terminate the loop, free all remaining allocated memory, and then end the program.  

5. **Single‑source file** – The entire solution must be written in one `.c` source file. Apart from `main`, you may create additional helper functions (e.g., for adding, removing, searching), but the program must compile with a standard C compiler (C99 or later) without requiring external libraries beyond `<stdio.h>`, `<stdlib.h>`, and `<string.h>`.  

6. **Robustness** – The program should handle invalid menu choices gracefully by printing “Invalid option, try again.” and re‑displaying the menu.  

---  

*Your task is to design the problem statement above; you do **not** need to provide a solution.*

---

