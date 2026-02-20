# Problem Batch Preview: Implementing Data Structures (e.g., Singly Linked Lists)
**Batch Number:** 2 | **Total Problems:** 100

---

## Problem 1 - moonshotai/kimi-k2-instruct-0905 - Iteration 81
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech Help Window.” Students can borrow small gadgets (USB cables, adapters, etc.) for 30-minute slots.  
A Raspberry Pi at the window only runs C, so you must build a tiny inventory manager that keeps the gadget queue in memory using a **singly linked list**.  
Each time a student checks out an item, it is appended to the end of the list; when the item is returned, it is removed from the front.  
The manager must also be able to show the current waiting list on request.

## Functional Requirements
1. Represent every gadget with a unique ID (positive integer) and a short name (≤20 characters).
2. Maintain the queue strictly in FIFO order.
3. Provide an interactive menu with the following choices:
   1. Check out (enqueue) a gadget  
   2. Return (dequeue) a gadget  
   3. Display current queue  
   4. Exit program  
4. On enqueue, read ID and name from stdin; silently ignore duplicate IDs.  
5. On dequeue, print the ID and name of the gadget that was removed; if the queue is empty, print `Queue empty`.  
6. On display, print one line per gadget in the format `ID: name`; if the queue is empty, print `Queue empty`.

## Simple Input/Output Example
```
1
101 powerbank
1
102 usbc_cable
3
2
4
```
Expected output
```
Queue empty
101: powerbank
102: usbc_cable
101 powerbank
```

### CONSTRAINTS
- Must use a `struct` to represent each gadget node.  
- All queue operations (enqueue, dequeue, display) must be implemented in **one** user-defined function each (three functions total besides `main`).  
- The program must terminate when the user chooses menu option **4**.

---

## Problem 2 - moonshotai/kimi-k2-instruct-0905 - Iteration 82
# STEP 1: PROBLEM

## Context
A local library is digitizing its card-catalog system.  
Each “card” will be stored as a node in a singly linked list, and the only information kept is the book’s unique ID (an integer).  
The head librarian wants a tiny demo program that can add books to the front of the list, remove a book by ID, and print the current catalog.

## Requirements
1. Represent each book with a node that stores:
   - an integer ID
   - a pointer to the next node
2. Provide three user commands:
   - `add <id>` – insert a new book with the given ID at the head of the list
   - `remove <id>` – delete the first node whose ID matches the given value; do nothing if the ID is absent
   - `print` – display every ID in the list from head to tail, separated by a single space and followed by a newline
3. The program must read commands until the user types `exit`, at which point it should free all remaining nodes and terminate
4. Assume IDs are non-negative integers and that no two books share the same ID

## Simple Example
Input
```
add 5
add 3
print
remove 5
print
exit
```
Output
```
3 5
3
```

### CONSTRAINTS
- You must use a `struct` to represent the primary data entity (the book node).  
- All dynamic memory must be freed before the program exits.

---

## Problem 3 - moonshotai/kimi-k2-instruct-0905 - Iteration 83
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its magazine rack.  
Each magazine is stored as a single stapled issue, and students can only add new issues to the front of the rack or remove the most recent issue (LIFO style).  
Your task is to model this rack as a **singly linked list** and provide a tiny terminal interface so the librarian can keep track of the magazines.

## Requirements
1. A magazine has two pieces of data:  
   - `title` – a single-word string (≤30 chars)  
   - `issue` – an integer (≥1)  
2. Represent each magazine node with a `struct`.  
3. Provide the following operations in a menu loop:  
   1. **Push** a new magazine to the front of the list.  
   2. **Pop** the magazine at the front and print its details.  
   3. **Display** the entire rack from most-recent to oldest.  
   4. **EXIT** the program (option 4).  
4. After every operation, re-display the menu (except when exiting).  
5. Handle empty-list cases gracefully with the message `"Rack is empty"`.

## Example Run
```
1. Push
2. Pop
3. Display
4. Exit
Choice: 1
Title: Wired
Issue: 202304
1. Push
2. Pop
3. Display
4. Exit
Choice: 1
Title: Nature
Issue: 202312
1. Push
2. Pop
3. Display
4. Exit
Choice: 3
Nature 202312
Wired 202304
1. Push
2. Pop
3. Display
4. Exit
Choice: 2
Removed: Nature 202312
1. Push
2. Pop
3. Display
4. Exit
Choice: 4
```

### CONSTRAINTS
- You **must** use a `struct` to represent the magazine node.  
- The logic that prints the details of **one** magazine must be encapsulated in a function named `displayMagazine`.  
- The solution must be implemented with **only one** additional function besides `main()`—i.e., all list operations (push, pop, display list) must be handled inline inside `main()` or via the single extra function.

---

## Problem 4 - moonshotai/kimi-k2-instruct-0905 - Iteration 84
# STEP 1: PROBLEM
## Background Story
The campus library has a “Take-a-Book, Leave-a-Book” shelf that is literally a single line of books.  
Students may only add a book to the front of the line or borrow the book at the front.  
To keep track of what is on the shelf, the librarian has asked you to write a tiny inventory system that models the shelf as a **singly linked list** of book nodes.

## Task
Implement a console program that maintains the shelf.  
Each book has:
- a unique 5-digit ID (int)
- a title string (up to 50 characters, no spaces)

The program must support the following commands in a loop:

1. `ADD id title` – insert the new book at the **front** of the list.  
   If an ID already exists anywhere on the shelf, print `ID already exists` and do nothing.
2. `BORROW` – remove the book at the **front** of the list and print `Borrowed: id title`.  
   If the shelf is empty, print `Shelf is empty`.
3. `LIST` – print every book currently on the shelf, **one per line**, in order from front to back.  
   If the shelf is empty, print `Shelf is empty`.
4. `EXIT` – terminate the program.

## Simple Example
### Input
```
ADD 10001 Pride
ADD 10002 Prejudice
BORROW
LIST
ADD 10001 Pride
EXIT
```

### Output
```
Borrowed: 10001 Pride
Shelf is empty
ID already exists
```

### CONSTRAINTS
1. You **must** use a `struct` to represent a book node (it must contain at least the fields `id`, `title`, and a pointer to the next node).
2. All list operations (insert at front, remove from front, traversal) must be implemented **manually**; you may **not** use STL containers such as `list` or `forward_list`.
3. The only functions allowed besides `main()` are:
   - `void displayEntity(const Book* b)` – prints the ID and title of the single book passed to it.
   - One helper function of your choice (e.g., `bool idExists(Book* head, int id)`).
4. Memory allocated with `new` must be freed before the program exits; no leaks.
5. The menu option to EXIT the program is the keyword `EXIT`.

---

## Problem 5 - moonshotai/kimi-k2-instruct-0905 - Iteration 85
# STEP 1: PROBLEM

## Background Story
You are helping a small music-streaming startup called “BeatChain” keep track of the songs queued by users.  
Each user has a personal playlist that is stored as a singly linked list.  
A node in the list holds the song title (≤100 characters) and a play-count (≥0).  
The playlist is always built in “append-to-end” order; the newest song is always added at the tail.

## Precise Requirements
1. Define a structure `SongNode` that contains:
   - a character array for the title
   - an integer for play-count
   - a pointer to the next node
2. Provide exactly four operations (menu driven):
   1. Add Song – read a title and a play-count, append a new node to the tail of the list
   2. Play Next – remove the node at the head, print its title and play-count, and free it
   3. Show Playlist – print every song in order, one per line, as `title (playCount)`
   4. Exit – free every remaining node and terminate the program
3. After every operation (except Exit), re-display the menu and wait for the next choice
4. If the user tries to Play Next when the list is empty, print `Playlist empty` and continue

## Simple Example
Input
```
1
Bohemian Rhapsody
42
1
Imagine
7
3
2
3
4
```

Output
```
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 1
Title: Bohemian Rhapsody
Play count: 42
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 1
Title: Imagine
Play count: 7
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 3
Bohemian Rhapsody (42)
Imagine (7)
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 2
Playing: Bohemian Rhapsody (42)
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 3
Imagine (7)
Menu:
1. Add Song
2. Play Next
3. Show Playlist
4. Exit
Choice: 4
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (`SongNode`)
- Logic for displaying the details of ONE specific entity must be in a function called `displaySong`
- The program must terminate only when the user chooses menu option 4 (Exit)

---

## Problem 6 - moonshotai/kimi-k2-instruct-0905 - Iteration 86
# STEP 1: PROBLEM

## Context
You’ve been hired by the campus music club to build a tiny, self-contained “Now-Playing” playlist manager.  
The club DJ keeps adding songs to the end of the playlist and sometimes needs to remove the song that just finished playing (always at the front).  
Your job is to implement the playlist as a **singly linked list** that can grow and shrink from opposite ends.

## Requirements
1. Each song is stored in a node that contains:
   - an integer id (unique within a session)  
   - a string title  
   - a string artist  
   - a pointer to the next node  
2. Maintain only two external pointers:
   - `head` – points to the song that will play next  
   - `tail` – points to the most-recently added song  
3. Support exactly three user commands (menu driven):
   1. **Add Song** – append a new song to the end of the list  
   2. **Play Next** – remove and display the song at the front (id, title, artist)  
   3. **Exit** – free all remaining nodes and terminate (menu option 3)  
4. After every command, print the count of songs currently in the playlist.

## Example Session (user input after prompt `>`)
```
1
> Please enter song id, title, artist: 101 Bohemian Rhapsody Queen
Songs in playlist: 1

1
> Please enter song id, title, artist: 102 Imagine Dragons
Songs in playlist: 2

2
Now playing: 101 Bohemian Rhapsody Queen
Songs in playlist: 1

3
Goodbye!
```

## Deliverables
Your program must present the menu in a loop until the user chooses 3.

### CONSTRAINTS
- Must use a `struct` to represent each song node.  
- All list operations (insert at tail, remove from head, memory cleanup) must be implemented **inside a single user-defined function** besides `main()` (call it `playlistManager`).  
- Menu option 3 is the only way to exit; it must also free every remaining node.

---

## Problem 7 - moonshotai/kimi-k2-instruct-0905 - Iteration 87
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Help” desk where students can donate spare USB flash drives.  
To keep track of the drives, the student assistant needs a tiny inventory system that stores the drives in the exact order they were donated.  
Because the number of drives changes constantly, a singly linked list is the perfect structure.

## Requirements
Implement a console program that maintains a singly linked list of donated USB flash drives.  
Each drive stores:
- `id` – a unique positive integer (the library labels them sequentially)
- `capacityGB` – an integer ≥ 1
- `brand` – a string without spaces (e.g., SanDisk, Kingston)

The program must support the following operations:
1. Insert a new drive (always appended to the tail of the list)
2. Remove the drive with a given id
3. Display the entire inventory in order from head to tail
4. Display full details of the drive with a given id
5. Exit the program

## Simple Example
Input (user choices shown after the menu prompt):

```
1
101 64 Kingston
1
102 32 SanDisk
3
4
101
5
```

Corresponding output:

```
=== USB Inventory ===
ID:101 GB:64 Brand:Kingston
ID:102 GB:32 Brand:SanDisk
=== Details ===
ID:101 GB:64 Brand:Kingston
Good-bye!
```

## Menu Layout
```
USB Drive Inventory
1) Donate (insert)
2) Remove by id
3) Show all
4) Show one
5) Exit
Choice:
```

### CONSTRAINTS
- Must use a `struct` to represent each USB drive node.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 8 - moonshotai/kimi-k2-instruct-0905 - Iteration 88
# STEP 1: PROBLEM

## Background Story
The campus library is digitising its “reservation queue” for study rooms.  
Students can join the queue, cancel their reservation, or check their current position.  
Your task is to implement the queue as a singly linked list that the librarian will control from a simple text menu.

## Requirements
1. Each queue node stores a student’s first name (≤ 30 characters) and a 6-digit student ID.
2. The list must be kept in strictly increasing order of student ID at all times (no separate sorting step after every insertion).
3. Provide a menu with the following choices:
   1. Add a new reservation (insert student in sorted order)  
   2. Cancel a reservation (remove by student ID)  
   3. Show the current queue (print ID and name, one per line)  
   4. EXIT (terminates the program)
4. After every successful insert or delete, print the current length of the queue.
5. If the user tries to add a duplicate ID, print “ID already in queue” and leave the queue unchanged.
6. If the user tries to cancel a non-existent ID, print “ID not found”.

## Simple Example of Expected Input/Output
```
1
Alice 123456
Length: 1
1
Bob 100001
Length: 2
3
100001 Bob
123456 Alice
2
123456
Length: 1
4
```
(The program terminates.)

## CONSTRAINTS
- Must use a struct to represent the primary data entity (the node).  
- Logic for displaying the details of ONE specific node must be in a function called displayEntity.  
- The entire solution must be implemented with a single function besides main().

---

## Problem 9 - moonshotai/kimi-k2-instruct-0905 - Iteration 89
# STEP 1: PROBLEM

## Context
The campus bookstore needs a tiny inventory system to keep track of textbooks.  
Each book has:  
- a unique ISBN (string, 13 digits)  
- a title (string, up to 50 characters)  
- a quantity in stock (integer ≥ 0)

Because the system will run on an embedded board with very little RAM, you are asked to store the collection as a **singly linked list** that you implement yourself.  
No arrays, no STL containers.

## Requirements
1. Represent each book with a `struct Book` that contains the three fields above and a `next` pointer.
2. Maintain the list in **ascending alphabetical order by title** (A→Z).
3. Support the following operations shown in a simple text menu:
   1. Add a new book (insert in the correct position; if the ISBN already exists, just update the quantity).
   2. Sell a book (decrease its quantity by 1; if quantity reaches 0, remove the node).
   3. Display the full inventory in order (one line per book: `ISBN title qty`).
   4. Exit the program (option 4).
4. After every operation, re-display the menu until the user chooses 4.
5. You may assume that all inputs are well-formed (no need to validate ISBN length, etc.).

## Simple Example Run
```
1. Add
2. Sell
3. Display
4. Exit
Choice: 1
ISBN: 9780131103627
Title: The C Programming Language
Quantity: 3
1. Add
2. Sell
3. Display
4. Exit
Choice: 1
ISBN: 9780201310092
Title: Advanced Programming in the UNIX Environment
Quantity: 2
1. Add
2. Sell
3. Display
4. Exit
Choice: 3
9780201310092 Advanced Programming in the UNIX Environment 2
9780131103627 The C Programming Language 3
1. Add
2. Sell
3. Display
4. Exit
Choice: 2
Title to sell: The C Programming Language
1. Add
2. Sell
3. Display
4. Exit
Choice: 3
9780201310092 Advanced Programming in the UNIX Environment 2
9780131103627 The C Programming Language 2
1. Add
2. Sell
3. Display
4. Exit
Choice: 4
Goodbye!
```

### CONSTRAINTS
- Must use a `struct Book` to represent the primary data entity.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with **only one additional function besides `main()`** (you may overload this function if you wish, but only one user-defined name other than `main`).

---

## Problem 10 - moonshotai/kimi-k2-instruct-0905 - Iteration 90
# STEP 1: PROBLEM

## BACKGROUND STORY  
The campus library has replaced its paper card catalog with a tiny, battery-powered “book finder” gadget that only stores book titles in the order they were added. Because memory is precious, the gadget must keep the list as a **singly linked list** and never allocate more nodes than strictly necessary.  
Your task is to write the firmware that lets a librarian add new titles to the back of the list and, on request, print the full current catalog.

## PRECISE REQUIREMENTS  
1. Represent each book as a node that stores one `std::string` title.  
2. Maintain a singly linked list that always appends new books at the tail.  
3. Provide two user commands:  
   - `ADD <title>` – insert the given title at the end of the list (case-sensitive, may contain spaces).  
   - `PRINT` – output the entire list, one title per line, in the same order the books were added.  
4. Stop the program only when the user types `EXIT` (case-insensitive).  
5. You may assume every command is on a single line and input is well-formed.

## SIMPLE EXAMPLE  
**Input**  
ADD The Great Gatsby  
ADD To Kill a Mockingbird  
PRINT  
EXIT  

**Output**  
The Great Gatsby  
To Kill a Mockingbird  

## NOTE  
No dynamic arrays, vectors, or STL containers are allowed—only raw pointers and your own linked-list logic.

### CONSTRAINTS  
- Must use a `struct` named `BookNode` to represent each list element.  
- All list manipulation (add, traverse) must be implemented in **one** user-defined function besides `main()`.  
- The menu option to EXIT the program must be the keyword `EXIT`.

---

## Problem 11 - moonshotai/kimi-k2-instruct-0905 - Iteration 91
# STEP 1: PROBLEM

## Background Story
You are helping the campus music club manage its vinyl-record collection.  
Each record has a catalog number (unique integer), album title, and artist name.  
Because the collection keeps growing, the club wants a tiny terminal program that stores the records in a singly linked list and lets them add or search records quickly.

## Required Functionality
1. When the program starts, the list is empty.
2. The program repeatedly shows a menu:
   1) Add a new record  
   2) Search for a record by catalog number  
   3) Show every record (in the order they were added)  
   4) Exit  
3. Option 1: Prompt user for catalog number, album title, and artist name; insert the new record at the **head** of the list.  
4. Option 2: Prompt for a catalog number; if it exists, print the record’s details; otherwise print “Not found”.  
5. Option 3: Print every record, one per line, in the same order they were added (i.e., reverse of insertion order).  
6. Option 4: Print “Goodbye!” and terminate.

## Simple Example Run
```
1) Add
2) Search
3) Show All
4) Exit
Choice: 1
Catalog #: 101
Title: Rumours
Artist: Fleetwood Mac
Added.

1) Add
2) Search
3) Show All
4) Exit
Choice: 1
Catalog #: 102
Title: Abbey Road
Artist: The Beatles
Added.

1) Add
2) Search
3) Show All
4) Exit
Choice: 2
Enter catalog #: 101
101 | Rumours | Fleetwood Mac

1) Add
2) Search
3) Show All
4) Exit
Choice: 3
102 | Abbey Road | The Beatles
101 | Rumours | Fleetwood Mac

1) Add
2) Search
3) Show All
4) Exit
Choice: 4
Goodbye!
```

### CONSTRAINTS
- You must define a `struct` to represent a record (node).  
- All list operations (add, search, display) must be implemented in **one** user-defined function besides `main()`.  
- Menu option 4 is the only way to exit; typing 4 must terminate the program.

---

## Problem 12 - moonshotai/kimi-k2-instruct-0905 - Iteration 92
# STEP 1: PROBLEM

**Background Story**  
The campus library has a “Fast-Return” box where students drop returned books.  
A student volunteer robot can only pick up one book at a time from the top of the pile and  
store it on a cart.  
Your task is to write a tiny “cart-tracker” that records the titles in the exact order the  
robot stores them. Because the robot can only access the most recently added book,  
you must model the cart as a **singly linked list** that always grows at the head (LIFO style).

**Requirements**  
1. Represent each book with a struct that contains at least:  
   – a unique title (C-string, ≤80 chars)  
   – a pointer to the next book in the cart  
2. Provide an interactive menu with the following choices:  
   1) Add a new book (push onto the head)  
   2) Remove the last added book (pop from the head)  
   3) Display the current cart from newest to oldest  
   4) Exit the program (must be option 4)  
3. After every operation, print the updated size of the cart.  
4. If the cart is empty and the user tries to pop or display, print “Cart is empty.”

**Simple Example**  
Input (user responses in brackets)
```
Welcome to Cart-Tracker
1) Add book
2) Remove last book
3) Display cart
4) Exit
[1]
Enter title: Introduction to Algorithms
Size: 1
[1]
Enter title: Clean Code
Size: 2
[3]
Cart (newest → oldest):
Clean Code
Introduction to Algorithms
[2]
Removed: Clean Code
Size: 1
[4]
Goodbye!
```

### CONSTRAINTS
- Must use a struct named Book to represent the primary data entity.  
- All list operations (push, pop, display) must be implemented in a **single function** besides main().  
- Menu option 4 must immediately terminate the program.

---

## Problem 13 - moonshotai/kimi-k2-instruct-0905 - Iteration 93
# STEP 1: PROBLEM

## Context  
The campus library has just reopened and is still using paper cards to keep track of who has borrowed which book.  
To modernise the process, you decide to build a tiny, single-session console program that stores the waiting list for one popular textbook.  
The list must be a **singly linked list** of students, each holding:  
- a unique 6-digit student ID  
- the student’s first name (≤ 20 characters)  
- the day of the month (1-31) on which the book was reserved  

## Requirements  
1. Represent every student node with a `struct` that contains the three data fields above.  
2. Provide a text menu that lets the user repeatedly choose among the following actions:  
   1. Add a new student to the **end** of the list.  
   2. Display the full waiting list in order (one student per line: ID, name, day).  
   3. Remove the student at the **front** of the list (the next person to receive the book).  
   4. Search for a student by ID and print their details if found.  
   5. **EXIT** the program.  
3. After every successful operation print a short confirmation message.  
4. All list operations must run in O(1) or O(n) time as appropriate; no auxiliary arrays or STL containers are allowed.  
5. Free all dynamically allocated memory before exit.

## Simple Example Run  
```
Welcome to Library Waiting List Manager
1. Add student
2. Display list
3. Serve first student
4. Search by ID
5. EXIT
Choice: 1
Enter ID: 123456
Enter first name: Ada
Enter reservation day: 12
Student added.

Choice: 1
Enter ID: 654321
Enter first name: Alan
Enter reservation day: 13
Student added.

Choice: 2
Waiting list:
123456 Ada 12
654321 Alan 13

Choice: 3
123456 Ada has been served and removed.

Choice: 5
Good-bye!
```

### CONSTRAINTS  
- You must use a `struct` to represent each student node.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The only functions besides `main()` are:  
  - `displayEntity` (as specified)  
  - plus any utility functions you need for list operations (add, remove, search, free).

---

## Problem 14 - moonshotai/kimi-k2-instruct-0905 - Iteration 94
# STEP 1: PROBLEM

## Background Story
The campus library is modernizing its card-catalogue system.  
Instead of physical drawers, they want a tiny terminal program that keeps track of book records in a **singly linked list**.  
Each record stores the book’s title, author, and year of publication.  
Students can add new books, remove the oldest book, or print the catalogue in the order the books were added.

---

## Required Functionality
1. Maintain the catalogue as a singly linked list.
2. Support three user commands:
   - `add <title> "<author>" <year>`  
      (title and author strings may contain spaces; author is always wrapped in double quotes)
   - `remove`  
      (always removes the first book that was added, i.e. head of the list)
   - `print`  
      (prints the entire catalogue, one book per line, in the format shown below)
3. After every command, print the number of books currently in the catalogue.
4. The program must loop until the user types `exit`.

---

## Simple Example Session (user input is preceded by `>`)

```
> add "The Pragmatic Programmer" "Andrew Hunt" 1999
1
> add Clean Code "Robert C. Martin" 2008
2
> print
"The Pragmatic Programmer" by Andrew Hunt (1999)
"Clean Code" by Robert C. Martin (2008)
2
> remove
1
> exit
```

---

### CONSTRAINTS
- You must use a `struct` named `Book` to represent each record and a `struct` named `Node` for the list nodes.  
- All list manipulation logic (insert, delete, print) must be implemented in **one user-defined function** besides `main()`; you may choose any signature for that function.  
- No global variables are allowed.

---

## Problem 15 - moonshotai/kimi-k2-instruct-0905 - Iteration 95
# STEP 1: PROBLEM
## Background Story
The campus library has replaced its old card-catalogue with a tiny computer that can only remember one thing at a time.  To help it keep track of which books are on the shelf, you will build an in-memory “shelf list” using a **singly linked list**.  Each node represents one book.  When a book is returned you add it to the front of the list; when a book is borrowed you remove it by title.  The librarian should also be able to print the current shelf (in order from front to back) and, of course, finish the work day.

## Functional Requirements
1. Represent a book with at least the following data:  
   - title (a single word, ≤30 characters)  
   - author (a single word, ≤30 characters)  
   - year (int)  

2. Maintain the shelf as a singly linked list whose head pointer is kept in `main`.

3. Provide a **console menu** with four choices:
   ```
   1  Return a book (insert at front)
   2  Borrow a book (remove by exact title match, case-sensitive)
   3  Show shelf
   4  Exit
   ```
4. For menu option 1, prompt the user for title, author, and year, then insert a new node at the **front** of the list.

5. For menu option 2, prompt for the title; if the book is on the shelf, delete **only the first matching node** and print `Borrowed.`, otherwise print `Not found.`.

6. For menu option 3, print the shelf contents one book per line in the format  
   `title (year) by author`  
   or print `Shelf is empty.` if nothing is stored.

7. After every operation, redisplay the menu until the user chooses option 4.

## Simple Example Run
```
1
Moby_Dick Melville 1851
1
1984 Orwell 1949
3
1984 (1949) by Orwell
Moby_Dick (1851) by Melville
2
1984
Borrowed.
3
Moby_Dick (1851) by Melville
4
```
(Program ends.)

### CONSTRAINTS
- Must use a `struct` called `Book` to represent the primary data entity.  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with a single function besides `main()` (i.e., only one additional function definition is permitted, and `displayBook` must be that function).

---

## Problem 16 - moonshotai/kimi-k2-instruct-0905 - Iteration 96
# STEP 1: PROBLEM

**Background Story**  
The campus bookstore has run out of shelf space. To keep track of which books are stored in which sealed box, the clerk wants a tiny “inventory” program that remembers the order in which boxes were stacked. Each box is labelled with a unique ID (positive integer) and a short description (one word, ≤30 characters). Because boxes are stacked on top of one another, the most recently added box must be the first one removed (LIFO). You will implement this behaviour with a **singly linked list** that only allows insertions and deletions at the head.

**Functional Requirements**  
1. Represent every box as a node that stores:
   - an integer id (the label)  
   - a C-string description (≤30 characters)  
   - a pointer to the next node  
2. Provide a text menu that repeatedly offers the following choices:  
   1. Push a new box onto the stack  
   2. Pop the top box from the stack  
   3. Display the current stack (from top to bottom)  
   4. Exit  
3. Push: read an id and a description from stdin; prepend the node to the list.  
4. Pop: remove the head node, print its id and description, and free its memory.  
   - If the stack is empty, print “Stack underflow” and do nothing.  
5. Display: print one line per box in the format  
   `id description`  
   starting from the top. If the stack is empty, print “Empty stack”.  

**Simple Example**  
Input  
```
1 42 physics
2 17 chemistry
3
1
4
```
Output  
```
17 chemistry
42 physics
Empty stack
```

**Explanation of Example**  
- 42 physics is pushed.  
- 17 chemistry is pushed.  
- Pop prints “17 chemistry”.  
- Display prints “42 physics”.  
- Another pop prints “42 physics”.  
- Final display prints “Empty stack”.  

### CONSTRAINTS  
- You **must** use a single `struct` named `Box` to represent each node.  
- The logic that prints the details of **one** box must be placed in a function called `displayBox`.  
- The entire solution must be implemented with **only one additional function besides main()** (you may choose which one).  
- The menu option to **Exit the program** is number **4**.

---

## Problem 17 - moonshotai/kimi-k2-instruct-0905 - Iteration 97
# STEP 1: PROBLEM

## Context
You are helping the campus music club manage their vinyl-record queue.  
Each record has a catalog number (positive integer) and a title.  
Club members can add a new record to the **front** of the queue, remove the **front** record after it is played, or print the entire queue from front to back.  
All operations must run in O(1) time for add/remove and O(n) time for printing.

## Requirements
1. Represent each record with a node that stores catalog number, title, and a pointer to the next node.
2. Provide the user with a text menu:
   ```
   1) Add record to front
   2) Play (remove) front record
   3) Show queue
   4) Exit
   ```
3. After every operation print one brief status line:
   - "Added: <title>"
   - "Played: <title>"
   - "Queue empty" (if removal attempted on empty list)
   - (No extra text when merely showing the queue.)

4. The queue must be implemented as a **singly linked list** you build yourself; no STL/Collections containers allowed.

## Simple Example
Input (user choices):
```
1
1801
Abbey Road
1
2105
Rumours
3
2
4
```

Corresponding console output:
```
Added: Abbey Road
Added: Rumours
(1801) Abbey Road
(2105) Rumours
Played: Abbey Road
```

### CONSTRAINTS
- The primary data entity (a record node) must be defined with a C/C++ `struct`.
- All list operations must be performed through a single user-defined function besides `main()` (e.g., `void listManager(int choice, ...)`).
- Menu option 4 is the only way to exit the program.

---

## Problem 18 - moonshotai/kimi-k2-instruct-0905 - Iteration 98
# STEP 1: PROBLEM  
## Background Story  
The campus music club keeps its vinyl-record playlist as a **singly linked list**. Each record stores the album title, the band name, and the year of release. The club hires you to write a tiny console program that lets a DJ quickly grow, shrink, and review the playlist between shows.

## Requirements  
1. The playlist is stored only as a singly linked list whose nodes are dynamically allocated.  
2. The user is shown a menu with the following choices:  
   1) Add a new record to the **front** of the list  
   2) Remove the **first** record that matches a supplied album title  
   3) Display the entire playlist (one record per line)  
   4) Count how many records in the list are **older than a given year**  
   5) Exit the program (terminates)  
3. All inputs are from `stdin`; all outputs go to `stdout`.  
4. If an operation is requested on an empty list, print `Playlist empty.` and redisplay the menu.  
5. After every successful operation (except Exit), redisplay the menu.  

## Simple Example Run (user input shown after `>`)  
```
1
>Album: Pet Sounds
>Band: The Beach Boys
>Year: 1966
1
>Album: Rumours
>Band: Fleetwood Mac
>Year: 1977
3
Pet Sounds (The Beach Boys, 1966)
Rumours (Fleetwood Mac, 1977)
4
>Year: 1970
Records older than 1970: 1
2
>Album: Pet Sounds
Removed.
3
Rumours (Fleetwood Mac, 1977)
5
```
Program terminates.

### CONSTRAINTS  
- You **must** define a `struct Record` containing the three data fields and a pointer to the next node.  
- The logic for displaying a single record must be placed in a function called `displayEntity`.  
- Apart from `main`, your solution may contain **only one additional function** that performs all list operations (add, remove, print, count); use a switch or similar inside that function to dispatch work.  
- Menu option **5** is the only way to exit the program.

---

## Problem 19 - moonshotai/kimi-k2-instruct-0905 - Iteration 99
# STEP 1: PROBLEM  
**Story:**  
The campus library is digitizing its small “Book-Swap” shelf. Every time a student donates a book, the title is written on an index card and placed at the **front** of the shelf (a LIFO pile). When another student borrows a book, they always take the **top** card. Your task is to write a tiny program that keeps track of the current order of books on this shelf using a **singly linked list**.  

**Precise Requirements:**  
1. Represent each book with a node that stores the title (a single string of ≤ 50 characters) and a next-pointer.  
2. Provide a menu with three operations:  
   - `1` – Donate a book (add to the front of the list).  
   - `2` – Borrow a book (remove and print the title of the front book).  
   - `3` – Show all books currently on the shelf (from front to back).  
   - `4` – EXIT the program.  
3. If the shelf is empty and a borrow or show is attempted, print `Shelf is empty`.  
4. All list operations must be implemented **manually** (no `STL`/`Collections`).  

**Simple Example Run:**  
```
1
Donate title: Clean Code
1
Donate title: Algorithms Unlocked
3
Shelf: Algorithms Unlocked -> Clean Code -> END
2
Borrowed: Algorithms Unlocked
3
Shelf: Clean Code -> END
4
Goodbye!
```

### CONSTRAINTS  
- Must use a `struct` called `BookNode` to represent the primary data entity.  
- All list manipulation must be done with **one single user-defined function** besides `main()` (e.g., a helper that performs insert, delete, and display).  
- Menu option `4` must EXIT the program.

---

## Problem 20 - moonshotai/kimi-k2-instruct-0905 - Iteration 100
# STEP 1: PROBLEM

**Background Story**  
You are the keeper of the “Scroll of Tasks,” a magical parchment that can only hold one quest at a time.  
Each quest is written on a tiny slip that is linked to the next slip by a silver thread, forming a chain.  
When an adventurer completes the current quest, the slip vanishes and the next quest slides to the front.  
Your job is to write the spells (code) that let the guild add new quests, complete (remove) the current quest, peek at the current quest, display the entire chain, and dissolve the guild (exit).

**Precise Requirements**  
1. Represent each quest with a struct that stores:  
   - a unique id (positive integer)  
   - a short title (string, ≤30 chars)  
   - a pointer to the next quest (or NULL if last).  
2. Maintain the quests as a **singly linked list** whose head is the **current active quest**.  
3. Provide a console menu with the following options:  
   1. Add new quest (insert at the tail)  
   2. Complete current quest (remove head)  
   3. Peek at current quest  
   4. Display entire quest chain  
   5. Exit (dissolve guild)  
4. After every operation, re-display the menu until the user chooses 5.  
5. Handle edge cases gracefully:  
   - Completing or peeking when the list is empty should print “No active quests.”  
   - Adding the first quest should make it the new head.  

**Simple Example Run**  
```
Menu:
1. Add quest
2. Complete quest
3. Peek current quest
4. Display chain
5. Exit
Choice: 1
Enter quest id: 101
Enter quest title: RescueCat
Choice: 1
Enter quest id: 102
Enter quest title: FetchWater
Choice: 3
Current quest: [101] RescueCat
Choice: 2
Quest 101 completed!
Choice: 4
Quest chain:
[102] FetchWater
Choice: 5
Good-bye!
```

### CONSTRAINTS  
- You must use a struct named Quest to represent each node.  
- All list operations (insert, remove, peek, display) must be implemented in **one user-defined function** besides main(); name that function listManager().  
- The program must terminate only when the user selects menu option 5.

---

## Problem 21 - moonshotai/kimi-k2-instruct-0905 - Iteration 1
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old card-catalog.  
Each drawer is a singly linked list of cards; each card stores a book’s call-number (a unique string) and title.  
Your job is to write a mini-catalog program that keeps the list alphabetically sorted by call-number while letting the librarian add and search cards.

## Functional Requirements
1. Represent each card as a node in a singly linked list.
2. Provide an interactive menu with the following choices:
   1. Add a new card (insert in ascending alphabetical order by call-number; reject duplicates).
   2. Search for a card by call-number and display its title.
   3. Display the entire catalog in order.
   4. Exit the program.
3. If the catalog is empty, any display operation must print `Catalog is empty.`
4. All dynamic memory must be freed before the program exits.

## Example Session (user input after `>`)
```
1
> 1
Enter call-number: QA76.73.C15
Enter title: The C Programming Language
Card added.
> 1
Enter call-number: QA76.6.B67
Enter title: Algorithms to Live By
Card added.
> 3
QA76.6.B67 : Algorithms to Live By
QA76.73.C15 : The C Programming Language
> 2
Enter call-number: QA76.73.C15
Title: The C Programming Language
> 4
Good-bye!
```

## Technical Details
- Use C or C++.
- All list operations must be implemented “by hand” (no STL or built-in containers).

### CONSTRAINTS
- Must use a `struct` named `Card` to represent each node (call-number string, title string, next pointer).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- Menu option `4` is the only way to exit the program.

---

## Problem 22 - moonshotai/kimi-k2-instruct-0905 - Iteration 2
# STEP 1: PROBLEM  
**Topic:** Implementing Data Structures (Singly Linked Lists)

## Background Story  
The tiny town of Bitville has only one bus route, but the stops change every week.  
To keep riders informed, the mayor wants a console program that can:  
- Add a new stop anywhere on the route  
- Remove the stop that is farthest from the depot (largest distance value)  
- Print the entire route from first to last  

Because the route changes so often, a singly linked list is perfect: cheap insertions and deletions.

## Requirements  
1. Represent each bus stop with:  
   - `id` (positive integer)  
   - `name` (single-word string, ≤20 chars)  
   - `distance` (integer kilometres from the depot, >0)  
2. Maintain stops in a singly linked list in the exact order they are inserted (unless repositioned).  
3. Support three user commands:  
   - `ADD_AFTER id_new name distance prev_id`  
     – Insert the new stop immediately after the stop whose id equals `prev_id`.  
     – If `prev_id` is 0, insert at the front.  
     – Print `Added` on success.  
     – If `prev_id` does not exist, print `Invalid prev_id`.  
   - `REMOVE_FARTHEST`  
     – Delete the single stop with the largest `distance`.  
     – If several stops tie for largest distance, remove the first one that appears in the list.  
     – Print `Removed id name distance`.  
     – If the list is empty, print `Empty route`.  
   - `PRINT_ROUTE`  
     – Print all stops in order, one per line: `id name distance`  
     – If the list is empty, print `Route is empty`.  
4. The program must loop until the user chooses option `0 EXIT`.

## Simple Example (user input after `>`)  
```
> ADD_AFTER 1 Depot 0
Added
> ADD_AFTER 2 Square 5 1
Added
> ADD_AFTER 3 Beach 12 2
Added
> ADD_AFTER 4 Park 7 2
Added
> PRINT_ROUTE
1 Depot 0
2 Square 5
4 Park 7
3 Beach 12
> REMOVE_FARTHEST
Removed 3 Beach 12
> PRINT_ROUTE
1 Depot 0
2 Square 5
4 Park 7
> 0
```  
Program terminates.

## CONSTRAINTS  
- Must use a `struct` to represent each bus stop (node).  
- All list operations (insert, find, delete) must be implemented manually; STL containers are forbidden.  
- The only functions allowed besides `main()` are:  
  - `void addAfter(...)`  
  - `void removeFarthest()`  
  - `void printRoute()`

---

## Problem 23 - moonshotai/kimi-k2-instruct-0905 - Iteration 3
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its card-catalogue system.  
Each “card” is now a small record that contains a book’s ID (a positive integer) and its title.  
All cards are kept in a singly linked list in **increasing order of ID**.  
The head librarian has hired you to write a tiny maintenance program that lets a clerk add a new card, remove an old one, or print the entire catalogue.  
Because the catalogue must always stay sorted by ID, every insertion has to preserve the order.

## Precise Requirements
1. Represent a card with two fields: `int id` and `string title`.
2. Maintain the cards in a **singly linked list** whose nodes are always arranged in **strictly increasing order of ID**.
3. Implement exactly three operations:
   - `1` – Insert a new card (ID and title are supplied by the user).  
     If an ID already exists, print `Duplicate ID` and leave the list unchanged.
   - `2` – Remove the card with a given ID.  
     If the ID is not found, print `ID not found`.
   - `3` – Print the whole catalogue, one card per line in the format `ID: title`.
4. Operation `0` exits the program (see CONSTRAINTS).

## Simple Example
Input
```
1 7 "The Pragmatic Programmer"
1 3 "Clean Code"
1 5 "Design Patterns"
3
2 7
3
0
```
Output
```
3: Clean Code
5: Design Patterns
7: The Pragmatic Programmer
ID not found
3: Clean Code
5: Design Patterns
```

## CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a card/node).  
- All list operations (insert, remove, print) must be implemented inside **one single user-defined function** besides `main()`; `main()` is only allowed to handle the menu loop and call that function.

---

## Problem 24 - moonshotai/kimi-k2-instruct-0905 - Iteration 4
# STEP 1: PROBLEM

Background Story  
The campus bookstore keeps its bargain-bin inventory in a hand-written notebook. To modernize, the manager wants a tiny console program that records the titles in the exact order they arrive, but still allows “first-in, first-out” removal when books are sold. You will implement this simple inventory as a **singly linked list** where each node stores one book title.

Program Requirements  
1. Represent every book with a node that has a title (C-string, ≤ 80 chars) and a *next* pointer.  
2. Keep an external pointer to the **front** of the list.  
3. Provide three operations that the user may repeat until they choose to quit:  
   a. **enqueue** (add a book title to the **tail** of the list).  
   b. **dequeue** (remove the book title from the **head** of the list and print it).  
   c. **display** (print all titles from head to tail, one per line).  
4. If the user tries to dequeue or display when the list is empty, print the exact message:  
   `List is empty.`  
5. All list operations must be implemented **manually** (no STL containers or built-in lists).  
6. Free every allocated node before the program exits.

Example Session (user input after prompt `>`)  
```
1
> Learning C
1
> Data Structures
2
Learning C
3
Data Structures
4
```
Output produced by the program:
```
1. Enqueue book
2. Dequeue book
3. Display books
4. Exit
1
Title: Learning C
1. Enqueue book
2. Dequeue book
3. Display books
4. Exit
1
Title: Data Structures
1. Enqueue book
2. Dequeue book
3. Display books
4. Exit
2
Sold: Learning C
1. Enqueue book
2. Dequeue book
3. Display books
4. Exit
3
Data Structures
1. Enqueue book
2. Dequeue book
3. Display books
4. Exit
4
```

### CONSTRAINTS  
- Must use a `struct` named `Book` (or `Node`) to represent each list element.  
- The logic for displaying the **entire** list must be placed in a function called `displayList`.  
- The solution must be implemented with **only one additional function besides main()** (choose wisely).  
- Menu option `4` is the **only** way to exit the program.

---

## Problem 25 - moonshotai/kimi-k2-instruct-0905 - Iteration 5
# STEP 1: PROBLEM

## Story  
The campus library’s reference desk keeps its “most-asked-for” bookmarks in a paper chain.  
Each link in the chain contains a bookmark title and a reference count (how many times it was asked for).  
To stay within the desk’s limited space, the librarian only wants the bookmarks that have been requested at least k times.  
Your task is to model this paper chain with a singly linked list and then remove the “unpopular” bookmarks (those whose count < k).  
The popular ones must remain in their original relative order.

## Requirements  
1. Represent each link (node) with:  
   - `title` – a C-style string (≤ 100 characters)  
   - `count` – an integer  
   - `next` – a pointer to the next node  
2. Provide the following operations:  
   a. Insert a new bookmark at the **head** of the list.  
   b. Remove all bookmarks whose `count` is **strictly less than** a user-supplied integer `k`.  
   c. Display the current list from head to tail (one line per bookmark: `title,count`).  
   d. Exit the program.  
3. All operations must run on the same list instance that is created at start-up and modified in-place.  
4. Memory allocated with `malloc()` must be freed before the program exits.

## Example Session (user input shown after `>`)  
```
1> CS101,15
1> Python,8
1> C,4
1> Java,12
2> 10
3>
Python,8
Java,12
CS101,15
4>
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (a node).  
- The logic for displaying the details of ONE specific node must be in a function called `displayNode`.  
- The solution must be implemented with a single function besides `main()`.  
- If a menu is implemented, option `4` must EXIT the program.

---

## Problem 26 - moonshotai/kimi-k2-instruct-0905 - Iteration 6
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Checkout Station” where students can borrow one of 20 identical Wi-Fi hotspots.  
To keep track of which hotspot is currently checked-out to which student, the station needs a tiny inventory system that stores the hotspot-ID and the borrower’s name in the order they were borrowed.  
You will build this inventory as a **singly linked list** that grows when hotspots are loaned out and shrinks when they are returned.

## Requirements
1. Each hotspot record holds:
   - a unique 4-digit ID (int)
   - the borrower’s first name (≤20 characters, no spaces)
2. The program keeps the records in a **singly linked list** whose head pointer is always the most-recently borrowed item.
3. The program must support exactly three commands from a menu:
   ```
   1 Borrow
   2 Return
   3 Exit
   ```
4. “Borrow” (`1`):
   - Read an ID and a name.
   - If the ID is already in the list, print “ID already borrowed.” and do nothing.
   - Otherwise add a new node at the **head** of the list and print “Borrowed.”
5. “Return” (`2`):
   - Read an ID.
   - If the ID exists, remove that node (keep the others in the same order) and print “Returned.”
   - Otherwise print “ID not found.”
6. After every command, print the current list in order from most-recently borrowed to least-recently borrowed, one record per line: `ID name`
7. The program must terminate **only** when the user chooses menu option `3`.

## Simple Example
Input
```
1 1001 Alice
1 1002 Bob
2 1001
3
```
Output
```
Borrowed.
1002 Bob
1001 Alice
Borrowed.
1002 Bob
1001 Alice
Returned.
1002 Bob
```
(Program exits after the final “3”.)

### CONSTRAINTS
- You **must** use a `struct` to represent each list node.
- All list operations (insert, delete, display) must be implemented **recursively**; no loops are allowed in any function that touches the nodes.
- The entire solution must be written with **only two user-defined functions** besides `main()`:  
  – one that performs **all** recursive insert/delete operations, and  
  – one that performs the **recursive** display of the list.

---

## Problem 27 - moonshotai/kimi-k2-instruct-0905 - Iteration 7
# STEP 1: PROBLEM

## Context
The campus library is digitizing its card-catalog system.  
Each book is represented by an old-fashioned “catalog card” that contains only three pieces of information:  
- a unique call-number (an integer)  
- the book’s title (a string, ≤100 chars)  
- a pointer to the next card in the drawer  

The librarian wants a tiny demo that keeps the cards in call-number order and supports a few quick operations.  
You will implement the drawer as a **singly linked list** of catalog cards.

## Functional Requirements
1. Insert a new catalog card **in ascending order** by call-number.  
2. Search for a book by call-number and display its title (or “Not found”).  
3. Remove a catalog card by call-number.  
4. Display the entire drawer in order, one card per line:  
   `call-number: title`  
5. Provide a menu-driven interface with the following choices:  
   1. Insert  
   2. Search  
   3. Remove  
   4. Display  
   5. Exit  

## Simple Example Run
```
=== Library Catalog Demo ===
1. Insert
2. Search
3. Remove
4. Display
5. Exit
Choice: 1
Call-number: 42
Title: Hitchhiker's Guide
Choice: 1
Call-number: 7
Title: Harry Potter
Choice: 4
7: Harry Potter
42: Hitchhiker's Guide
Choice: 2
Call-number: 7
Found: Harry Potter
Choice: 5
Goodbye!
```

### CONSTRAINTS
- Must use a `struct` named `CatalogCard` to represent the primary data entity.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayCard`.  
- The only functions allowed are `main()` and `displayCard()`; all list operations must be handled inline inside `main()`.  
- Menu option `5` must EXIT the program.

---

## Problem 28 - moonshotai/kimi-k2-instruct-0905 - Iteration 8
# STEP 1: PROBLEM

## Context
The campus library has a tiny help–desk bell that rings every time a book is returned.  
To keep track of the order in which books are returned (and therefore who is next in the “first-come, first-served” hold queue), the librarian asks you to build an electronic log.  
You decide to model the log as a singly linked list where each node stores one book ID (a positive integer).  
Books are always added to the tail of the list (they arrive in time order) and removed from the head (the next book to be processed).

## Requirements
1. Represent the log as a singly linked list of book IDs.
2. Provide a console menu with exactly four choices:
   1. Ring bell & return book (adds a new ID to the tail)  
   2. Process next hold (removes and displays the ID at the head)  
   3. Display current queue (prints every ID from head to tail, space-separated on one line)  
   4. Exit  
3. If the user tries to process a hold when the queue is empty, print `Queue empty` instead of a book ID.
4. All dynamic memory must be freed before the program exits.

## Simple Example Run
```
1
101
1
102
1
103
3
101 102 103
2
Processed: 101
3
102 103
4
```

### CONSTRAINTS
- You must use a `struct` to represent each node of the linked list.  
- All list operations (insert at tail, delete from head, display queue) must be performed by a **single helper function** besides `main()`.  
- The menu option to EXIT the program is number **4**.

---

## Problem 29 - moonshotai/kimi-k2-instruct-0905 - Iteration 9
# STEP 1: PROBLEM

**Background Story**  
The campus library has installed a new book-drop slot that only works in “last-in, first-out” order.  
To keep things fair, the head librarian wants a tiny piece of software that records the exact order in which books are dropped and can tell her, at any moment, which book is currently on the top of the stack (the one that will be picked up first).  
Your task is to model this book-drop slot as a singly linked list that always grows at the front (like a stack) and never has to delete anything—only insert and inspect.

**Functional Requirements**  
1. Represent each book with two data members:  
   - a unique integer ID (1–1000)  
   - a title string (up to 50 characters, no spaces)  
2. Provide an interactive menu with the following choices:  
   1) Drop a new book (insert at the front)  
   2) See the top book (display the head node only)  
   3) List every book currently in the slot (from most-recent to oldest)  
   4) Exit  
3. After every successful operation, print a short confirmation message.  
4. If the user tries to see the top book or list books when the slot is empty, print “Slot is empty.”

**Simple Example Run**  
```
1) Drop 2) Top 3) List 4) Exit
Choice: 1
Enter ID: 42
Title: CleanCode
Book 42 dropped.

1) Drop 2) Top 3) List 4) Exit
Choice: 1
Enter ID: 7
Title: PragProg
Book 7 dropped.

1) Drop 2) Top 3) List 4) Exit
Choice: 2
Top book: 7 PragProg

1) Drop 2) Top 3) List 4) Exit
Choice: 3
7 PragProg
42 CleanCode

1) Drop 2) Top 3) List 4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a book node).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.  
- Menu option 4 is the required EXIT keyword.

---

## Problem 30 - moonshotai/kimi-k2-instruct-0905 - Iteration 10
# STEP 1: PROBLEM

## Background Story
You are helping the campus music club manage their vinyl-record lending shelf.  
Each record is stored in a sleeve that has a unique catalog number (an integer) and the album’s title (a string).  
All sleeves are kept in a single chain—like a singly linked list—hung on a wall.  
Members can:  
- add a new record to the front of the chain,  
- remove a record by catalog number,  
- search for a record by catalog number, and  
- print the entire chain in order.  

Your task is to write the tiny library system that the club volunteers will run from a simple text menu.

## Functional Requirements
1. Represent each record with a catalog number (int) and album title (string).  
2. Store the collection as a singly linked list whose nodes are dynamically allocated.  
3. Provide a text menu with four numbered operations:  
   1) Add a record  
   2) Remove a record  
   3) Search for a record  
   4) Print all records  
   5) Exit  
4. “Add” inserts at the head of the list.  
5. “Remove” deletes the first node with the given catalog number; if none exists, print “Not found.”  
6. “Search” prints the catalog number and title if found; otherwise print “Not found.”  
7. “Print all” displays every record in the list, one per line, in the format  
   `<catalog #>: <album title>`  
   or print “Empty shelf.” if the list is empty.  
8. After every operation (except Exit), re-display the menu.  
9. No global variables except for the head pointer, which must be declared in main().  

## Simple Example Run (user input after `>`)
```
1
> 12345
> Kind of Blue
1
> 12346
> A Love Supreme
4
12346: A Love Supreme
12345: Kind of Blue
3
> 12345
12345: Kind of Blue
2
> 12346
4
12345: Kind of Blue
5
```

### CONSTRAINTS
- You must define a `struct` to represent each node (record).  
- All list operations (add, remove, search, print) must be implemented as exactly four standalone functions besides `main()`.  
- The only functions allowed in your source file are: `main()`, `addRecord()`, `removeRecord()`, `searchRecord()`, `printRecords()`.  
- Menu option 5 is the only way to exit; the program must terminate cleanly with return code 0.

---

## Problem 31 - moonshotai/kimi-k2-instruct-0905 - Iteration 11
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a 24-hour self-service kiosk where students can borrow and return books without staff present.  
To keep track of which books are currently on the shelf, the kiosk needs a tiny in-memory inventory system that uses a **singly linked list**.  
Each book is identified only by its (unique) ISBN string.  
Your task is to write the kiosk’s brain: a console program that lets a student add a book (when it is returned) and remove a book (when it is borrowed) in O(1) time at the head of the list.

## Requirements
1. Represent the inventory as a singly linked list of books.
2. Support two commands:
   - `ADD <ISBN>` – insert the book at the head of the list.
   - `BORROW <ISBN>` – remove the first occurrence of that ISBN (starting from the head) and print `Removed <ISBN>`; if the ISBN is not found, print `Not found`.
3. After every command, print the current inventory in order from head to tail, one ISBN per line, followed by a line containing only `---`.
4. The program terminates when the user enters the keyword `EXIT`.

## Simple Example
### Input
```
ADD 9780131103627
ADD 9780201633610
BORROW 9780131103627
BORROW 9780000000000
EXIT
```

### Expected Output
```
9780131103627
---
9780201633610
9780131103627
---
Removed 9780131103627
9780201633610
---
Not found
9780201633610
---
```

### CONSTRAINTS
- You must use a `struct` to represent a book node.  
- All list operations (add, remove, display) must be implemented in a single user-defined function called `processCommand` besides `main()`.

---

## Problem 32 - moonshotai/kimi-k2-instruct-0905 - Iteration 12
# STEP 1: PROBLEM

## Topic: Implementing Data Structures (e.g., Singly Linked Lists)

### Background Story
You are helping a local library digitise its small‐ magazine collection. Each magazine has a unique 4‐digit ID and a title. The librarian wants a tiny console program that can add a new magazine to the front of the list, show the whole list, and exit.

### Requirements
1. Represent each magazine as a node in a singly linked list.  
2. Provide a console menu with two options:  
   1) Add new magazine  
   2) Exit  
3. When the user chooses “Add”, the program must insert the new magazine at the **head** of the list and print the updated list.  
4. When the user chooses “Exit”, the program must print the full list once more and terminate.

### Example Input/Output
```
1
1234
New Yorker
1
5678
Time
2
5678 Time 1234 New Yorker
```

### CONSTRAINTS
- The magazine must be stored as a struct with two fields: an integer id and a string title.  
- The list must be implemented as a singly linked list.  
- The program must use a menu option 2 to exit.

---

## Problem 33 - moonshotai/kimi-k2-instruct-0905 - Iteration 13
# STEP 1: PROBLEM

Context  
You are the last‑minute substitute TA for “CSC 152: Intro to Machine Org.” The instructor left a flash drive containing every student’s grade history as a plain text log of integer scores. Your task is to write a tiny emergency tool that rebuilds the log as a singly linked list so the registrar can append or query grades even if the drive is unplugged.

Problem  
Write a console program that

 1. starts with an empty singes‑linked list whose nodes hold one int (the grade);
 2. supports three commands:
      insert  <grade>     → append grade to tail  
      print               → display entire list  
      exit                → quit

The program must keep the list alive until exit.

Input / Output  
Sample session  
insert 73  
insert 81  
print  
81  
73  
insert 90  
print  
90  
81  
exit  

### CONSTRAINTS  
1. You must define a struct GradeNode.  
2. Logic for displaying the list must be in a function displayEntity().  
3. You must implement only one function besides main().

---

## Problem 34 - moonshotai/kimi-k2-instruct-0905 - Iteration 14
# STEP 1: PROBLEM

## Context
The campus library is digitising its CD-audio collection.  
Each CD has a unique 6-digit ID, a title, and the number of tracks.  
Your task is to write a tiny cataloguing system that keeps these CDs in **the exact order they were inserted** (i.e. a singly linked list with *append-only* behaviour).  
Librarians should be able to add a new CD, list every CD currently stored, or exit the program.

## Functional Requirements
1. Represent a CD with the attributes:
   - `id` (positive 6-digit integer)
   - `title` (single-word string, ≤30 characters)
   - `tracks` (positive integer)
2. Maintain a singly linked list that always appends new CDs at the end.
3. Implement a console menu with the following options:
   1. Add a new CD  
   2. List all CDs  
   3. Exit  
4. If the user tries to add a CD whose ID already exists anywhere in the list, refuse the insertion and print `Duplicate ID`.
5. Listing must show every CD on a single line in the format:  
   `<id>: <title> (<tracks> tracks)`  
   (one CD per line, in insertion order).

## Simple Example
Input
```
1
123456
Mozart25
8
1
123457
Beethoven5
4
2
3
```
Output
```
123456: Mozart25 (8 tracks)
123457: Beethoven5 (4 tracks)
```

## CONSTRAINTS
- You must define a `struct` called `CD` to represent the primary data entity.  
- All code (except `main`) must be encapsulated in **exactly one additional function**; that function must be named `menu`.  
- Menu option `3` must immediately terminate the program.

---

## Problem 35 - moonshotai/kimi-k2-instruct-0905 - Iteration 15
# STEP 1: PROBLEM

## Context
You are helping the campus music club manage the queue for their weekly open-mic night. Musicians add their names to a waiting list that is processed in strict first-come-first-served order. To keep things digital, the club wants a tiny command-line program that uses a **singly linked list** to maintain the waiting list and lets them add performers, call the next performer to the stage, and print the current queue at any moment.

## Requirements
1. Provide a text menu with three choices:
   1) Add performer  
   2) Call next performer  
   3) Exit  
2. "Add performer" reads a single name (no spaces) and appends it to the end of the queue.  
3. "Call next performer" removes the front node and prints "Now on stage: <name>".  
4. If the queue is empty and the user tries to call the next performer, print "Queue is empty - no performers waiting."  
5. After every operation (except exit) re-display the menu.  
6. On exit, release all dynamically allocated memory.

## Example Session
```
1) Add performer
2) Call next performer
3) Exit
Choice: 1
Name: Alice
1) Add performer
2) Call next performer
3) Exit
Choice: 1
Name: Bob
1) Add performer
2) Call next performer
3) Exit
Choice: 2
Now on stage: Alice
1) Add performer
2) Call next performer
3) Exit
Choice: 3
Goodbye!
```

### CONSTRAINTS
- Use a `struct` to represent each performer (node).  
- All list operations (insert at tail, delete from head, and printing) must be implemented in functions other than `main()`.  
- The menu option to EXIT the program is option `3`.

---

## Problem 36 - moonshotai/kimi-k2-instruct-0905 - Iteration 16
# STEP 1: PROBLEM

**Background Story**  
The campus library is digitizing its help-desk ticket system. Every time a student has a question, a new “ticket” is created. The tickets must be kept in the exact order they arrive, but staff need to be able to:  
- add a ticket to the end of the queue,  
- remove the first ticket when it is answered, and  
- display the current queue at any moment.  

You will implement the queue as a **singly linked list** whose nodes hold the ticket ID (a positive integer) and the student’s question (a short string).

**Precise Functional Requirements**  
1. Represent each ticket with a node that stores:  
   - an `int ticketID`  
   - a `char question[60]`  
   - a pointer to the next node.  
2. Maintain two global pointers:  
   - `front` – points to the head of the list (oldest unanswered ticket).  
   - `rear` – points to the tail of the list (newest ticket).  
3. Provide exactly three user operations triggered by a console menu:  
   1. Add a new ticket (read ID and question; append to rear).  
   2. Answer the next ticket (remove from front and print its details).  
   3. Display the current queue (print every ticket ID and question in order).  
   4. Exit the program.  
4. After every operation, re-display the menu unless the user chose Exit.  
5. Handle underflow gracefully: if the queue is empty and the user chooses “Answer,” print `Queue empty` and redisplay the menu.  
6. Do **not** use arrays or any STL containers; the queue must be managed with your linked-list nodes.

**Simple Example Run**  
```
=== Library Help-Desk Ticket System ===
1. Add ticket
2. Answer ticket
3. Display queue
4. Exit
Choice: 1
Enter ticket ID: 101
Enter question: How do I print double-sided?
Ticket added.

1. Add ticket
2. Answer ticket
3. Display queue
4. Exit
Choice: 1
Enter ticket ID: 102
Enter question: Where is the quiet zone?
Ticket added.

1. Add ticket
2. Answer ticket
3. Display queue
4. Exit
Choice: 3
Queue:
101 How do I print double-sided?
102 Where is the quiet zone?

1. Add ticket
2. Answer ticket
3. Display queue
4. Exit
Choice: 2
Answered ticket 101: How do I print double-sided?

1. Add ticket
2. Answer ticket
3. Display queue
4. Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (the ticket node).  
- Logic for displaying the details of ONE specific ticket must be in a function called `displayTicket`.  
- The solution must be implemented with a single function besides `main()` (you may have as many helper functions as you like, but only one additional “major” function besides `main`).  
- Menu option 4 is the only way to exit the program.

---

## Problem 37 - moonshotai/kimi-k2-instruct-0905 - Iteration 17
# STEP 1: PROBLEM  
## Background  
The campus library has installed a new self-checkout kiosk. Instead of scanning bar-codes, the kiosk keeps a running list of book IDs (positive integers) in the order they are checked out. After each checkout, the kiosk must:  
1. Print the complete current list (in order) so the patron can verify it.  
2. Be able to remove the most-recently-added book if the patron changes their mind.  

## Requirements  
Your task is to implement the kiosk’s memory as a singly linked list of book IDs.  
Provide these operations:  
- `addBook(id)` – append a new book ID to the end of the list.  
- `removeLast()` – delete the last added ID (if the list is empty, do nothing).  
- `displayList()` – print the entire list in the order the books were added, one ID per line.  

## Input/Output Format  
The program reads commands from standard input until the user types `exit`.  
Commands:  
- `add <id>` – call `addBook` with the given positive integer `<id>`.  
- `remove` – call `removeLast`.  
- `display` – call `displayList`.  
- `exit` – terminate the program (must be option 0 if a menu is used).  

### Simple Example  
Input  
```
add 101
display
add 102
add 103
remove
display
exit
```  
Output  
```
101
101
102
```

### CONSTRAINTS  
1. Must use a `struct` named `BookNode` to represent each node.  
2. Logic for printing the entire list must be in a function called `displayList`.  
3. The solution must be implemented with **only one** function besides `main()` (i.e., `displayList` is that function; all other logic may be placed inline in `main`).

---

## Problem 38 - moonshotai/kimi-k2-instruct-0905 - Iteration 18
# STEP 1: PROBLEM

## Background Story
The campus library has a small “Take-One-Leave-One” book crate that works only through a *last-in, first-out* rule: when a student donates a book, it is placed on the *top* of the pile; the next student who wants a free book must take the one that is currently on top.  
To keep track of the crate without arrays (because the crate can grow or shrink unpredictably), the librarian asks you to build a tiny digital ledger that remembers the titles in the exact order they were donated.

## Requirements
Your program must:
1. Represent every donated book as a node in a **singly linked list**.
2. Provide a menu-driven interface that lets the librarian repeatedly choose one of the following actions:
   - `1` Donate a book (push title on the top of the pile)
   - `2` Lend a book (pop title from the top of the pile and show it)
   - `3` Peek at the top book (show its title without removing it)
   - `4` Print the entire pile from top to bottom (one title per line)
   - `0` Exit the program
3. After every operation, automatically return to the menu until the user chooses `0`.
4. If the crate is empty and the librarian tries to lend or peek, print:
   ```
   Crate is empty!
   ```

## Simple Example of Expected Input/Output
```
=== Book-Crate Ledger ===
1 Donate
2 Lend
3 Peek
4 Show all
0 Exit
Choice: 1
Title: Clean Code
Choice: 1
Title: The Pragmatic Programmer
Choice: 3
Top book: The Pragmatic Programmer
Choice: 2
Lent: The Pragmatic Programmer
Choice: 4
Clean Code
Choice: 0
Good-bye!
```

### CONSTRAINTS
- You must define a `struct` named `Book` to represent each node (it needs at least a title and a pointer to the next book).
- All list manipulation (push, pop, peek, print) must be performed by **a single helper function** you write yourself, called `listOp()`, which takes an integer operation code and any other parameters it needs.  
  *No other user-defined function besides* `main()` *and* `listOp()` *is allowed.*

---

## Problem 39 - moonshotai/kimi-k2-instruct-0905 - Iteration 19
# STEP 1: PROBLEM

## Story
The tiny town of Byteville has only one public library, and it still keeps its book inventory on paper cards.  
The head librarian, Ms. Ada, has hired you to digitize the card catalogue.  
For now she only wants to keep the books in the order they were added, but she must be able to:

- add a new book to the end of the catalogue,  
- remove a book by its unique shelf-id (a positive integer),  
- list every book currently on file, and  
- quit the program when she is done for the day.

Because the collection is small, a singly-linked list is perfect for the job.

## Requirements
1. Represent each book with a struct that contains:
   - shelf-id (positive int, unique across the catalogue)  
   - title (string, no commas)  
   - author (string, no commas)  
   - pointer to next book (or NULL if last)
2. Maintain the list in “arrival order” (new books appended at the tail).
3. Implement exactly four user commands:
   - `add` – read one line “shelf-id title author” and append the book.  
   - `remove` – read one integer (shelf-id) and delete that book if it exists; print “Removed” or “Not found”.  
   - `list` – print the entire catalogue, one book per line, in the format “shelf-id) Title by Author”.  
   - `exit` – free all dynamically allocated memory and terminate the program.
4. All list operations must be performed by manipulating the linked nodes; no arrays or STL containers.
5. The program must keep running until the user types `exit`.

## Simple Example
**Input**
```
add 42 HitchhikersGuide DouglasAdams
add 7 GEB Hofstadter
list
remove 42
remove 99
exit
```

**Expected Output**
```
42) HitchhikersGuide by DouglasAdams
7) GEB by Hofstadter
Removed
Not found
```

### CONSTRAINTS
- You must use a single struct called `Book` to represent each node.  
- All dynamic memory (malloc/new) must be released before the program exits.

---

## Problem 40 - moonshotai/kimi-k2-instruct-0905 - Iteration 20
# STEP 1: PROBLEM  
**Topic:** Implementing a Singly Linked List  

**Background Story**  
You are helping the campus library automate its waiting list for newly–arrived books. Every time a student wants a book that is still “in transit”, the student is added to a queue. When the book arrives, the first student in the queue is notified and removed. You will implement this queue as a singly linked list.

**Requirements**  
1. Each node stores a student ID (integer) and a next pointer.  
2. Provide the following operations:  
   - `enqueue(id)` – add a new student to the tail of the list.  
   - `dequeue()` – remove the student at the head and return the ID.  
   - `display()` – print the entire list from head to tail, space-separated.  
3. A menu must keep running until the user chooses to exit.  
4. All memory must be dynamically allocated and freed before the program ends.

**Example Interaction**  
Input  
```
1 101
1 102
1 103
2
3
4
```
Output  
```
101 102 103  
102  
102 103  
```
### CONSTRAINTS  
- Implement queue logic only with a singly linked list.  
- Must use a struct to represent each node.  
- No global variables allowed.  
- The menu must offer option 4 to EXIT.

---

## Problem 41 - moonshotai/kimi-k2-instruct-0905 - Iteration 21
# STEP 1: PROBLEM  
Topic: Implementing a Singly Linked List  

Story  
You are the TA for a course whose professor keeps losing the grade sheet.  The professor wants a tiny “Grade Sheet” program that stores nothing more than the student’s ID (an int) and the grade (a char: A … F).  The program must be able to insert a new grade at the head, delete one grade, print the entire list, and exit.

Requirements  
1. Represent one grade as a struct with two members: int id; char grade;  
2. Keep all grades in a singly linked list.  
3. Provide exactly four menu choices:  
   1 insert  2 delete  3 print  4 exit  
4. insert must add the new grade at the head of the list.  
5. delete must remove the first node with a matching id (if any).  
6. print must display every node as “id grade” on one line.  
7. After every command the program returns to the menu; choice 4 ends the program.

Example Input / Output  
Input  
1 101 A  3  1 102 B  3  4  

Output  
1 A  3  
1 A  3  

CONSTRAINTS  
The solution must be implemented with a single function besides main().

---

## Problem 42 - moonshotai/kimi-k2-instruct-0905 - Iteration 22
# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Singly Linked Lists)

You are a Computer Science professor designing an undergraduate curriculum.  
Generate a novel programming problem on Implementing Data Structures (e.g., Singly Linked Lists). Your response must begin with the header # STEP 1: PROBLEM.  
The problem statement must be clear, unambiguous, and suitable for a student who has just learned this topic.  
Requirements:  
1. Clear background story or context.  
2. A precise list of requirements for the program's functionality.  
3. Simple Example of expected Input/Output.  
4. Additional constraints such as 'Must use a 'struct' to represent the primary data entity.', 'Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.' or 'The solution must be implemented with a single function besides main()'. The constraint(s) should be listed under the header ### CONSTRAINTS.  
4. MANDATORY CONSTRAINTS IF A MENU IS IMPLEMENTED:  
   - Must include a specific menu option to EXIT the program (clearly state the number or keyword).

---

# STEP 1: PROBLEM

Context  
You are a teaching assistant helping a student who has just learned about singly linked lists.  
Write a small program that stores a list of positive integers and allows the user to insert, delete, and display the elements.

Background story  
A local bakery wants to record the temperature (in °C) of its ovens every minute.  
The temperatures are always positive integers and are stored in a sing singly linked list.

Precise requirements  
1. Define a struct Node containing an integer value and a pointer to the next node.  
2. Implement the following menu options:  
   - insert at the end  
   - delete a value  
   - display the list  
   - exit  
3. The program must keep the list in ascending order at all times.  
4. After each operation, display the updated list.  
5. The program must be implemented using only one function besides main().

Simple Example Input/Output  
Input:  
1 10  
1 20  
1 30  
2 25  
3  
4  

Output:  
10 20 30  
25 30  

### CONSTRAINTS  
- Must use a struct to represent the primary data entity.  
- Logic for displaying the details of ONE specific entity must be in a function called displayEntity.  
- The solution must be implemented with a single function besides main().

---

## Problem 43 - moonshotai/kimi-k2-instruct-0905 - Iteration 23
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old card-catalog.  
Each card contains a book’s ID (a positive integer) and its title.  
Your task is to write a tiny catalog that keeps the cards in **ascending order of ID** and supports quick insertions, deletions, and look-ups.

## Requirements
1. Represent each card with a struct named `Card` that stores:
   - `int id`
   - `char title[60]`
   - `Card *next`
2. Maintain the cards in a **singly linked list** sorted by `id`.
3. Implement exactly **one helper function** (besides `main`):
   - `Card *insertCard(Card *head, int id, const char *title)`  
     - If `id` already exists, update the title and return the head unchanged.
     - Otherwise insert the new card in the correct position and return the new head.
4. Inside `main`, repeatedly read commands from standard input until the user chooses to exit:
   - `1 id title` : insert/update a card
   - `2 id`      : delete the card with that id (ignore if not found)
   - `3`         : print the entire catalog, one card per line in the format `id: title`
   - `0`         : EXIT the program (guaranteed to be called at least once)

## Simple Example
Input
```
1 7 PrideAndPrejudice
1 3 Hamlet
1 5 Odyssey
3
2 5
3
0
```
Output
```
3: Hamlet
5: Odyssey
7: PrideAndPrejudice
3: Hamlet
7: PrideAndPrejudice
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (`Card`).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.

---

## Problem 44 - moonshotai/kimi-k2-instruct-0905 - Iteration 24
# STEP 1: PROBLEM  
**Topic:** Implementing a Singly Linked List  

**Background Story:**  
The campus library has asked you to write a tiny program that keeps track of the next book they will process for digitization. Each book is added to a “queue” (really a list) and is removed from the front when the librarian clicks “process.” Because the collection is small, the library wants the simplest possible structure—no arrays, no STL containers—just a classic hand-rolled singly linked list.

**Requirements (what your program must do):**  
1. Represent each book with a node that stores:  
   - an integer id (unique, > 0)  
   - a string title  
   - a pointer to the next node  
2. Maintain the list in **strict ascending order by id**.  
3. Support exactly three user commands from a console menu:  
   1. `add` – read an id and title, insert a new node in the correct ordered position.  
   2. `process` – remove and print the *smallest-id* node (the head).  
   3. `exit` – free all remaining nodes and terminate the program.  
4. After every successful `add` or `process`, print the updated list as a single space-separated sequence of ids (or “empty” if none).  
5. Reject duplicate ids with the message “duplicate id” and leave the list unchanged.

**Simple Example Run (user input shown after the prompt `>`):**  
```
> add 5 Pride
5
> add 2 Sense
2 5
> add 7 Magic
2 5 7
> process
processing 2
5 7
> add 5
duplicate id
5 7
> exit
```

### CONSTRAINTS  
- You must define the node with a `struct`.  
- All list operations (insert ordered, remove head) must be implemented in **one single function** besides `main()`.  
- The menu option to EXIT the program is the number `3`.

---

## Problem 45 - moonshotai/kimi-k2-instruct-0905 - Iteration 25
# STEP 1: PROBLEM  
## Background  
The campus library is digitising its old card-catalogue. Each index card contains a single book title and the next card’s drawer number (a non-negative int). Your job is to write a tiny program that lets the librarian keep the catalogue in memory as a **singly linked list** of these cards.  

## Requirements  
1. Represent each “card” with a node that stores:  
   - a string (the book title)  
   - an integer (the drawer number of the next card, –1 if this card is the last one)  
2. Maintain the list in **ascending order of drawer numbers** (ties keep insertion order).  
3. Provide an interactive menu with the following choices:  
   1. Add a new card  
   2. Remove the card with a given drawer number  
   3. Display the full catalogue (one card per line: `title drawer#`)  
   4. Count how many cards are currently stored  
   5. Exit  
4. After every successful Add or Remove, print the updated count.  
5. All list operations must be performed **in-place**; no arrays or STL containers.  

## Simple Example  
Input  
```
1
Pride and Prejudice
7
1
The Hobbit
3
1
Dune
5
3
2
3
5
```  
Output  
```
Added. Total cards: 1
Added. Total cards: 2
Added. Total cards: 3
Dune 3
Pride and Prejudice 5
The Hobbit 7
Removed. Total cards: 2
```  

### CONSTRAINTS  
- Must use a `struct Card` to represent each node.  
- The only functions allowed besides `main()` are:  
  - `void addCard(string title, int drawer)`  
  - `void removeCard(int drawer)`  
  - `void displayCatalogue()`  
  - `int cardCount()`  
- Menu option **5** must terminate the program.

---

## Problem 46 - moonshotai/kimi-k2-instruct-0905 - Iteration 26
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a new “Tech-to-Lend” kiosk that loans out small electronic gadgets (e.g., noise-canceling headphones, phone chargers, tablets) to students for up to 24 h.  
To keep the inventory simple, the librarian keeps all gadgets in a single chain (a singly-linked list) in the order they were donated.  
Your task is to write a tiny inventory program that lets the librarian add a new gadget, show the full current list, or search for a gadget by its ID number.

## Requirements
1. Represent each gadget with:  
   - `int id` – unique 4-digit identifier (1000–9999)  
   - `char name[32]` – short description (e.g., “Headphones-Sony”)  
   - `int qty` – how many identical units are available  
2. Maintain the gadgets in a singly-linked list in the order they were added.  
3. Implement a text menu with three options (and a fourth to exit):  
   1. Add new gadget  
   2. Display entire inventory  
   3. Search gadget by ID  
   4. Exit  
4. On “Search”, print the first matching gadget’s details or “Not found.”  
5. Do not use any STL or Java collections; implement your own nodes.

## Example Session
```
1. Add new gadget
2. Display inventory
3. Search gadget by ID
4. Exit
Choice: 1
Enter ID: 1001
Enter name: Headphones-Sony
Enter quantity: 5
Gadget added.

Choice: 1
Enter ID: 1005
Enter name: Charger-USB-C
Enter quantity: 3
Gadget added.

Choice: 3
Enter ID to search: 1005
ID: 1005  Name: Charger-USB-C  Qty: 3

Choice: 3
Enter ID to search: 9999
Not found.

Choice: 4
Good-bye!
```

### CONSTRAINTS
- You must define a `struct Node` that contains the gadget data and a pointer to the next node.  
- The logic that prints the details of exactly one gadget must be placed in a function called `displayEntity()`.  
- The entire solution must be implemented with only one additional function besides `main()` (you may use `displayEntity()` and any helper functions you need, but the core list operations must be handled inside `main()`).  
- The menu option to exit the program is option number 4.

---

## Problem 47 - moonshotai/kimi-k2-instruct-0905 - Iteration 27
# STEP 1: PROBLEM

**Context**  
The campus library has replaced its old card–catalog drawers with a tiny Raspberry Pi-powered kiosk that only understands text commands. The head librarian has hired you to write the backend that stores the current list of “overnight-loan” books. Because the kiosk has very little memory, the library wants the list stored as a singly linked list that is kept in alphabetical order by title at all times (i.e., inserts must maintain order). No arrays or STL/Boost containers may be used.

**Required Functionality**  
1. Start with an empty list.  
2. Repeatedly read single-letter commands from `cin` until the user types `X` (uppercase) to exit.  
3. Command “A” (Add): read one book title (possibly containing spaces) and insert it into the list so that titles stay in strictly ascending alphabetical order.  
   - If the title is already present, silently ignore the request (no duplicates).  
4. Command “R” (Remove): read one book title and delete the first matching node if it exists; if the title is not found, do nothing.  
5. Command “P” (Print): output every title in order, one per line, preceded by “Catalog:”. If the catalog is empty, output only the line “Catalog: empty”.  
6. Command “C” (Count): print the total number of distinct titles currently stored.  
7. All dynamic memory must be released before the program exits.

**Simple Example Run**  
Input  
```
A The Great Gatsby
A Animal Farm
P
R The Great Gatsby
C
X
```
Output  
```
Catalog:
Animal Farm
The Great Gatsby
1
```

### CONSTRAINTS  
- You must use a `struct` called `BookNode` to represent each node of the list.  
- All list operations (insert, delete, print, count) must be implemented inside **one single user-defined function** besides `main()`; give that function the prototype  
  `void processCommand(char cmd, std::istream& in, BookNode*& head);`  
- The program must terminate when the user enters the menu option `X`.

---

## Problem 48 - moonshotai/kimi-k2-instruct-0905 - Iteration 28
# STEP 1: PROBLEM

## Topic: Implementing Data Structures – Singly Linked Lists

### Background Story
You are helping the campus library build a tiny‐text archive of old book‐borrowing histories. Each history entry is just a (year, month) pair plus a short sentence describing what happened that month. The archive must support two operations: (1) add a new history entry at the **front** of the list, and (2) display every entry in the exact order it was added. The library wants the whole archive kept in memory as a singly linked list.

### Requirements
1. Define a struct that represents one history entry.
2. Maintain a singly linked list in the order entries were added.
3. Provide two functions:
   - `addEntry()` – insert a new history entry at the front of the list.
   - `displayArchive()` – print every entry in the list, one per line.
4. The program must never add duplicate entries (same year and month).
5. The program must be able to handle multiple operations until the user exits.

### Example Input/Output
```
Enter 1 to add, 2 to display, 3 to exit.
1
Enter year and month: 2021 5
Enter description: "Borrowing history for May 2021"
Enter 1 to add, 2 to display, 3 to exit.
1
Enter year and description: 2021 5
"Borrowing history for May 2021"
Entry already exists.
Enter 1 to add, 2 to display, 3 to exit.
2
2021 5: Borrowing history for May 2021
Enter 1 to add, 2 to display, 3 to exit.
3
```

### CONSTRAINTS
- You must define a struct to represent the history entry.
- You must implement a function `displayArchive()` to print the entire list.
- You must not use any dynamic arrays or standard containers.
- You must not use any global variables.

---

## Problem 49 - moonshotai/kimi-k2-instruct-0905 - Iteration 29
# STEP 1: PROBLEM

**Background Story**  
The campus library has hired you to write a tiny catalog system that keeps track of the next book to be shelved.  
Each book is represented by its call-number (a positive integer).  
All books waiting to be shelved form a queue that must behave like a **singly linked list**; only the first book may be removed, and every new book is always added at the end of the queue.

**Precise Functional Requirements**  
1. Represent every book with a node that stores:  
   - `callNo` – an `unsigned int`  
   - `next` – a pointer to the next node (or `nullptr` if it is the last book).  
2. Maintain two external pointers:  
   - `head` – always points to the front of the queue (the next book to shelve).  
   - `tail` – always points to the last node in the list (where the next book will be appended).  
3. Provide exactly three operations (case-insensitive single-letter commands):  
   - `A <callNo>` – append a book with the given call-number to the tail of the queue.  
   - `S` – shelve (remove) the book at the head of the queue and print its call-number.  
     If the queue is empty, print `Queue empty`.  
   - `P` – print the entire queue from head to tail, space-separated on one line.  
     If the queue is empty, print `Queue empty`.  
4. The program must terminate only when the user chooses menu option `X`.  
5. You may assume every input line is syntactically correct.

**Simple Example**  
Input  
```
A 101
A 202
P
S
P
X
```
Output  
```
101 202
101
202
```

### CONSTRAINTS  
- You must use a `struct` called `Book` to represent each node.  
- All list manipulation logic (append, remove, print) must be implemented in **one single function** besides `main()`.  
- The menu option to EXIT the program is the single uppercase letter `X`.

---

## Problem 50 - moonshotai/kimi-k2-instruct-0905 - Iteration 30
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech Lending Locker.”  
Students can borrow one of 20 identical Arduino kits for up to 7 days.  
To keep things fair, the librarian wants a tiny console program that records who has which kit and when it is due—using nothing more advanced than a singly linked list.

## Requirements
1. Each kit is represented by a node that stores:
   - kit ID (unique integer 1-20)
   - borrower name (single-word string, ≤20 chars)
   - due day (integer 1-31, inclusive)
2. The list is initially empty.
3. The program repeatedly presents a menu with four choices:
   1. Check-out a kit
   2. Return a kit
   3. Show all currently borrowed kits
   4. Exit (ends the program)
4. Check-out (option 1):
   - Read kit ID, borrower name, due day.
   - Reject if kit ID is not in range or already borrowed.
   - Insert at the **front** of the list.
5. Return (option 2):
   - Read kit ID.
   - If found, remove that node; print “Kit <id> returned.”
   - Else print “Kit <id> not found.”
6. Show all (option 3):
   - Print one line per borrowed kit in the exact format:
     ```
     Kit <id>: <name> due day <day>
     ```
   - If the list is empty, print “No kits currently borrowed.”
7. All list operations must be performed on your own singly linked list; no STL/Collection libraries allowed.

## Simple Example Run
```
1. Check-out
2. Return
3. Show all
4. Exit
Choice: 1
Kit ID: 7
Borrower: Alice
Due day: 12
1. Check-out
2. Return
3. Show all
4. Exit
Choice: 3
Kit 7: Alice due day 12
1. Check-out
2. Return
3. Show all
4. Exit
Choice: 2
Kit ID: 7
Kit 7 returned.
1. Check-out
2. Return
3. Show all
4. Exit
Choice: 3
No kits currently borrowed.
1. Check-out
2. Return
3. Show all
4. Exit
Choice: 4
```

### CONSTRAINTS
- Must use a `struct` to represent each kit node.
- All list manipulation (insert, delete, traverse) must be coded in **one user-defined function** besides `main()`.

---

## Problem 51 - moonshotai/kimi-k2-instruct-0905 - Iteration 31
# STEP 1: PROBLEM

## Background Story
You are helping the university registrar’s office build a tiny in-memory waiting list for an over-enrolled course. Students are added to the list in the order they request a seat, but the registrar also needs to remove a student when they withdraw or when a seat opens and the first student in line is admitted. You will implement this “waiting list” as a **singly linked list** where each node stores a student’s ID (integer) and last name (≤20 letters).

## Requirements
1. Represent each list node with a student’s ID and last name.
2. Provide the following operations:
   - **1** – Add a new student to the **back** of the list.  
   - **2** – Remove the student from the **front** of the list (they got a seat).  
   - **3** – Display the entire waiting list in order, one line per student:  
     ```
     ID lastName
     ```
   - **4** – Exit the program.
3. After every operation, print the updated list length.  
   Format: `List now holds N student(s).`  
   (If the list is empty, print `List is empty.`)
4. All operations must run in O(1) time except Display, which is O(n).

## Simple Example
Input
```
1 101 Smith
1 102 Jones
3
2
4
```

Output
```
List now holds 1 student(s).
List now holds 2 student(s).
101 Smith
102 Jones
List now holds 2 student(s).
Admitted: 101 Smith
List now holds 1 student(s).
```

### CONSTRAINTS
- You must use a `struct` to represent each list node.
- The logic that prints the details of a **single** node must be encapsulated in a function called `displayEntity`.
- The entire solution must be implemented with only **one** user-defined function besides `main()`.  
- Menu option **4** is the required EXIT option.

---

## Problem 52 - moonshotai/kimi-k2-instruct-0905 - Iteration 32
# STEP 1: PROBLEM
Background Story  
You have just been hired as the “Night Shift Librarian” for the city’s oldest library.  
The previous librarian kept all book records on paper cards.  
Your first task is to digitize the card catalog.  
Each card holds only three things: a unique ID number, the book’s title, and a pointer to the next card.  
Your job is to write a tiny program that lets you add new cards, list every card in order, and then lock up for the night.

Program Requirements  
1. Represent each card with a struct named Card that contains  
   - an int id  
   - a string title (≤100 characters)  
   - a pointer to the next Card.  
2. Maintain the cards as a singly linked list in ascending order of id.  
3. Provide a text menu with exactly three choices:  
   1) Add a new card  
   2) List all cards  
   3) Exit  
4. On “Add”, read an id and title from stdin.  
   - Reject duplicate ids with the message “Duplicate ID.”  
   - Insert the new card so the list stays sorted.  
5. On “List”, print every card in order, one per line, in the exact format  
   ID: <id>, Title: <title>  
6. On “Exit”, free every allocated node and terminate the program.  
7. You may assume every input line is well-formed and within length limits.

Simple Example  
Input  
1  
103  
Pride and Prejudice  
1  
101  
The Great Gatsby  
2  
3  

Output  
ID: 101, Title: The Great Gatsby  
ID: 103, Title: Pride and Prejudice  

### CONSTRAINTS  
- Must use a struct named Card to represent each card.  
- The logic for inserting a new Card into the list must be implemented in a single function named insertCard.  
- The logic for displaying the details of ONE specific Card must be in a function named displayCard.  
- The only functions allowed besides main() are insertCard and displayCard.

---

## Problem 53 - moonshotai/kimi-k2-instruct-0905 - Iteration 33
# STEP 1: PROBLEM
## Background
You are helping a music-streaming startup build an ultra-light “Now-Playing” history.  
Each song played is stored in a singly linked list so that the most recent song is always at the head.  
When the user quits the app, the history is printed from newest to oldest.

## Requirements
1. Define a `struct Song` that stores:
   - a unique integer id (0–10 000),
   - title (≤30 chars, no spaces),
   - artist (≤30 chars, no spaces).
2. Maintain a global pointer `head` that always points at the most-recently played song.
3. Implement exactly one function besides `main()`:
   ```c
   void pushSong(int id, const char* title, const char* artist);
   ```
   - It inserts a new song at the head of the list.
   - If an id already exists anywhere in the list, print `Duplicate id` and do nothing.
4. Inside `main()`:
   - Repeatedly read commands from standard input until the user types `0`.
   - Commands:
     - `1 id title artist` → call `pushSong`.
     - `0` → print the entire history (one line per song, fields separated by space) and exit.

## Example
Input
```
1 7 BlindingLights TheWeeknd
1 3 Levitating DuaLipa
1 7 BlindingLights TheWeeknd
0
```
Output
```
Duplicate id
3 Levitating DuaLipa
7 BlindingLights TheWeeknd
```

## CONSTRAINTS
- Must use a `struct` to represent the primary data entity (`Song`).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.

---

## Problem 54 - moonshotai/kimi-k2-instruct-0905 - Iteration 34
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Help” window staffed entirely by robots.  
Each robot is represented by a unique ID string and a battery level (0-100).  
When a robot’s battery drops below 10 % it must leave the line to recharge.  
Your task is to model the queue of robots **as a singly linked list** so that the head of the list is always the robot currently at the window.

## Requirements
1. Represent every robot with a node that stores:
   - `id` (C-string, ≤ 20 characters)  
   - `battery` (integer 0-100)  
   - `next` pointer
2. Maintain the list in FIFO order; new robots are always appended to the tail.
3. Implement a text menu that lets the user:
   - `1` Add a robot (read id and battery, append).  
   - `2` Remove the robot at the window (head) **only if** its battery < 10; otherwise print “Robot still has juice, cannot remove.”  
   - `3` Display the complete queue from head to tail, one robot per line:  
     `ID: R2D2 Battery: 45`
   - `4` Exit the program.
4. All list operations must be done **in place** (no auxiliary arrays or STL containers).

## Simple Example
Input (user choices in brackets):
```
[1] R2D2 45
[1] BB8 7
[3]
[2]
[3]
[4]
```

Output:
```
ID: R2D2 Battery: 45
ID: BB8 Battery: 7
Robot still has juice, cannot remove.
ID: R2D2 Battery: 45
ID: BB8 Battery: 7
```

### CONSTRAINTS
- Must use a `struct Node` to represent the primary data entity.  
- Logic for displaying the details of ONE specific robot must be in a function called `displayRobot`.  
- The solution must be implemented with a single function besides `main()` (you may have helper functions, but all list manipulation must be done inside that one function).  
- Menu option `4` must immediately terminate the program.

---

## Problem 55 - moonshotai/kimi-k2-instruct-0905 - Iteration 35
# STEP 1: PROBLEM  
Topic: Implementing a Singly Linked List

Story  
You are a teaching assistant helping freshmen register their ID cards.  
Each card contains only two fields: an integer ID (unique) and a 3-letter name.  
All cards are stored in a single box that behaves like a stack:  
new cards are inserted at the top; when a student leaves, the top card is removed.  
Your job is to maintain this box entirely in C without arrays or STL containers.

Task  
Implement a minimal “card box” as a singly linked list that supports the following commands:

1 insert <id> <name>  
   Add a new card to the top.  
2 remove  
   Remove the top card.  
3 list  
   Print every card from top to bottom, one per line:  
   <id> <name>  
4 exit  
   Release all memory and terminate.

Input/Output Example  
insert 101 bob  
insert 102 ana  
list  
102 ana  
101 bob  
remove  
list  
101 bob  
exit  

### CONSTRAINTS  
- Must use a struct Node {int id; char name[4]; Node *next;}.  
- Must use only one function besides main().  
- No global variables.

---

## Problem 56 - moonshotai/kimi-k2-instruct-0905 - Iteration 36
# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Singly Linked Lists)

You are a Computer Science professor designing an undergraduate curriculum.  
Generate a novel programming problem on Implementing Data Structures (e.g., Singly Linked Lists). Your response must begin with the header # STEP 1: PROBLEM.  
The problem statement must be clear, unambiguous, and suitable for a student who has just learned this topic.  
Requirements:  
1. Clear background story or context.  
2. A precise list of requirements for the program's functionality.  
3. Simple Example of expected Input/Output.  
4. Additional constraints, such as 'Must use a 'struct' to represent the primary data entity.', 'Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.' or 'The solution must be implemented with a single function besides main()'. The constraint(s) should be listed under the ### CONSTRAINTS.  
4. MANDATORY CONSTRAINTS IF A MENU IS IMPLEMENTED:  
   - Must include a specific menu option to EXIT the program (clearly state the number or keyword).

# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Sing Singly Linked Lists)

You are a Computer Science professor designing an undergraduate curriculum.  
Generate a novel programming problem on Implementing Data Structures (e.g., Sing Singly Linked Lists). Your response must begin with the header # STEP 1: PROBLEM.  
The problem statement must be clear, unambiguous, and suitable for a student who has just learned this topic.  
Requirements:  
1. Clear background story or context.  
2. A precise list of requirements for the program's functionality.  
3. Simple Example of expected Input/Output.  
4. Additional constraints, such as 'Must use a 'struct' to represent the primary data entity.', 'Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.' or 'The solution must be implemented with a single function besides main()'. The constraint(s) should be listed under the ### CONSTRAINTS.  
4. MANDATORY CONSTRAINTS IF A MENU IS IMPLEMENTED:  
   - Must include a specific menu option to EXIT the program (clearly state the number or keyword).

# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Sing Singly Linked Lists)

You are a Computer Science professor designing an undergraduate curriculum.  
Generate a novel programming problem on Implementing Data Structures (e.g., Sing Singly Linked Lists). Your response must begin with the header # STEP 1: PROBLEM.  
The problem statement must be clear, unambiguous, and suitable for a student who has just learned this topic.  
Requirements:  
1. Clear background story or context.  
2. A precise list of requirements for the program's functionality.  
3. Simple Example of expected Input/Output.  
4. Additional constraints, such as 'Must use a 'struct' to represent the primary data entity.', 'Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.' or 'The solution must be implemented with a single function besides main()'. The constraint(s) should be listed under the ### CONSTRAINTS.  
4. MANDATORY CONSTRAINTS IF A MENU IS IMPLEMENTED:  
   - Must include a specific menu option to EXIT the program (clearly state the number or keyword).

# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Sing Singly Linked Lists)

You are a Computer Science professor designing an undergraduate curriculum.  
Generate a novel programming problem on Implementing Data Structures (e.g., Sing Singly Linked Lists).

---

## Problem 57 - moonshotai/kimi-k2-instruct-0905 - Iteration 37
# STEP 1: PROBLEM  
Topic: Implementing Singly Linked Lists  

Background  
A small town library has hired you to replace its old card‐catalog system with a tiny digital one.  Each book is represented only by its ISBN (a positive integer).  The librarian will type commands to add a new book to the front of the shelf, remove the first book, or display the entire shelf in order.

Requirements  
1. Represent the shelf as a singly linked list whose nodes store one ISBN.  
2. Implement the following commands:  
   - `add <ISBN>` – insert a new node at the head of the list.  
   - `remove` – delete the head node and print its ISBN; if the list is empty, print `empty`.  
   - `display` – print the list contents in order, one ISBN per line; if empty, print `empty`.  
3. Stop when the user types `exit`.

Example  
Input  
```
add 101  
add 102  
display  
remove  
display  
exit  
```

Output  
```
102  
101  
102  
101  
```

### CONSTRAINTS  
- Must use a `struct` to represent a node.  
- Must have exactly one function besides `main()`; all list operations must be inside that function.  
- Menu option `exit` must terminate the program.

---

## Problem 58 - moonshotai/kimi-k2-instruct-0905 - Iteration 38
# STEP 1: PROBLEM

**Background Story**  
The campus library has just opened a “Fast-Return” desk that only accepts books in the exact order they were borrowed. To keep track of the waiting list, you decide to build a tiny terminal program that models the queue of books using a **singly linked list**. Each book is identified only by its unique accession number (a positive integer).  

**Task**  
Implement an interactive system that lets the librarian:  
1. **Add** a new book to the *back* of the queue.  
2. **Return** the book at the *front* of the queue (i.e., remove and display it).  
3. **Display** the entire current queue from front to back.  
4. **Exit** the program.  

The program must keep the queue in the correct order at all times.

**Simple Example (user input shown after `>`)**  
```
1> 123
1> 124
1> 125
2
Returned book 123
3
Queue: 124 125
0
Good-bye!
```

### CONSTRAINTS  
- You must use a `struct` called `Book` to represent each node (it holds at least the accession number and a next-pointer).  
- All list operations (insert at tail, delete from head, display) must be implemented **manually**—do **not** use `std::list`, `vector`, etc.  
- The logic that prints the accession number of **one** book must be placed in a function called `displayEntity`.  
- The only functions allowed besides `main()` are:  
  – `void enqueue(Book*&, int)`  
  – `int dequeue(Book*&, Book*&)` (returns accession # or -1 if empty)  
  – `void displayQueue(Book*)`  
  – `void displayEntity(Book*)`  
- The menu must offer option **0** to EXIT the program.

---

## Problem 59 - moonshotai/kimi-k2-instruct-0905 - Iteration 39
# STEP 1: PROBLEM

## Background Story
The campus library has asked your CS class to build a “mini-catalog” system that keeps track of books currently on a single shelf.  
Each book has a unique call-number (an integer), a title, and an author.  
Because the shelf is narrow, books are physically stored in a singly-linked list so they can be easily inserted or removed without shifting the entire row.  
Your job is to implement the core data structure and the basic operations the librarian needs.

## Requirements
1. Represent a book as a node in a singly-linked list.  
2. Provide the following operations (menu-driven):
   1) Add a new book to the front of the list.  
   2) Remove a book by call-number.  
   3) Search for a book by call-number and display its title & author.  
   4) Display the full shelf (all books, in order).  
   5) Exit the program.  
3. After every operation, show the updated shelf contents (except for the search operation, which only shows the requested book).  
4. If an operation cannot be performed (e.g., removing a non-existent book), print an appropriate error message.

## Example Session (user input in **bold**)
```
1) Add
2) Remove
3) Search
4) Display
5) Exit
Choice: **1**
Call-number: **101**
Title: **The Pragmatic Programmer**
Author: **Andrew Hunt**
Shelf: [101:The Pragmatic Programmer by Andrew Hunt]

Choice: **1**
Call-number: **102**
Title: **Clean Code**
Author: **Robert Martin**
Shelf: [102:Clean Code by Robert Martin] -> [101:The Pragmatic Programmer by Andrew Hunt]

Choice: **3**
Call-number: **101**
Found: 101:The Pragmatic Programmer by Andrew Hunt

Choice: **2**
Call-number: **101**
Removed. Shelf: [102:Clean Code by Robert Martin]

Choice: **5**
Goodbye!
```

### CONSTRAINTS
- Must use a struct named `Book` to represent the primary data entity.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The entire solution must be implemented with only one additional function besides `main()` (you may use helper functions internally, but only one user-defined function prototype besides main is allowed).

---

## Problem 60 - moonshotai/kimi-k2-instruct-0905 - Iteration 40
# STEP 1: PROBLEM

**Background Story**  
The campus library is modernizing its manual “hold request” list. Each student can place only one hold on a book, and the system must keep the requests in the order they arrive. You have been asked to build a tiny prototype that records, cancels, and prints the queue of waiting students using a **singly linked list**.  

**Requirements**  
1. Represent each hold request with a node that stores the student’s full name (≤30 characters).  
2. Maintain the queue strictly as a singly linked list.  
3. Provide a menu-driven interface with the following options:  
   1. Add a new hold request (enqueue at the tail).  
   2. Cancel the oldest hold request (dequeue from the head).  
   3. Display the current queue.  
   4. Exit the program.  
4. After every operation, print the updated queue or the cancelled student’s name.  
5. Handle empty-queue cancellations gracefully with the message “Queue is empty.”  

**Simple Example of Expected I/O**  
```
===== Library Hold Queue =====
1. Add Request
2. Cancel Oldest
3. Display Queue
4. Exit
Choice: 1
Enter student name: Alice
Queue: Alice

Choice: 1
Enter student name: Bob
Queue: Alice -> Bob

Choice: 3
Queue: Alice -> Bob

Choice: 2
Cancelled: Alice
Queue: Bob

Choice: 4
Goodbye!
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (the node).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.  
- If a menu is implemented (as required above), option 4 must EXIT the program.

---

## Problem 61 - moonshotai/kimi-k2-instruct-0905 - Iteration 41
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Takeaway” window where students can borrow small gadgets (portable chargers, calculators, adapters) for a short period. Each gadget is stored in a numbered cubby, and the window is so narrow that the attendant can only add or remove items from the front of the shelf. To keep track of what’s available, you will write a tiny inventory manager that stores the gadgets in a **singly linked list**. Each node represents one cubby and holds the gadget’s name and a checkout flag.

## Functional Requirements
1. Represent every cubby as a node in a singly linked list.
2. Provide a menu-driven console program with the following options:
   - 1 Add a new gadget (insert at the front of the list)
   - 2 Check-out a gadget (remove the first node whose checkout flag is false, mark it as checked-out, and print its name)
   - 3 Return a gadget (append it back to the front of the list as “available” again)
   - 4 List all cubbies (print each gadget’s name and its current status: “available” or “checked-out”)
   - 5 Exit the program
3. After every successful operation, print a short confirmation message (e.g., “Added power-bank”, “Checked-out calculator”, “Returned adapter”).

## Simple Example Run
```
=== Tech-Takeaway Inventory ===
1 Add gadget
2 Check-out gadget
3 Return gadget
4 List cubbies
5 Exit
Choice: 1
Gadget name: power-bank
Added power-bank

Choice: 1
Gadget name: calculator
Added calculator

Choice: 2
Checked-out calculator

Choice: 4
cubby 0: calculator (checked-out)
cubby 1: power-bank (available)

Choice: 3
Returned calculator

Choice: 4
cubby 0: calculator (available)
cubby 1: power-bank (available)

Choice: 5
Good-bye!
```

### CONSTRAINTS
- You must define a struct named `Cubby` that represents a node (gadget name, checkout flag, next pointer).
- All list operations must be implemented in a single function besides `main()`; name that function `processMenu`.
- The menu option to EXIT the program is `5`.

---

## Problem 62 - moonshotai/kimi-k2-instruct-0905 - Iteration 42
# STEP 1: PROBLEM

**Background Story**  
The campus library has just digitised its old card-catalogue. Each catalogue card contains a book’s ID (a positive integer) and its title (a single word with no spaces).  
All cards arrived in a box in **strictly increasing order of ID**, but some cards are **duplicates** (same ID and title).  
Your task is to write a program that stores the cards in a **singly linked list**, removes every duplicate while preserving the order, and then lets the librarian query the list.

**Functional Requirements**  
1. Read an unknown number of catalogue cards from standard input until the word “END” is encountered.  
2. Each non-END line contains:  
   `<ID> <title>`  
   where ID is a positive int and title is a single word.  
3. Build a singly linked list in the exact order the cards arrive.  
4. Remove **all duplicate cards** (two cards are equal when both ID and title match).  
   - Keep the **first** occurrence of every duplicate.  
5. After all input is read, repeatedly display a menu with the following options:  
   1. Display the entire list (one card per line: ID and title).  
   2. Search for a book by ID; display the first matching card or “Not found”.  
   3. Exit the program.  

**Simple Example**  
Input  
```
101 Algorithms
102 Biology
101 Algorithms
103 Chemistry
102 Biology
END
```
Menu interaction (user choices shown after prompt)  
```
1. Display list
2. Search by ID
3. Exit
Choice: 1
101 Algorithms
102 Biology
103 Chemistry
Choice: 2
Enter ID: 102
102 Biology
Choice: 3
```
Program terminates.

### CONSTRAINTS  
- Must use a `struct` to represent a catalogue card (node).  
- Logic for displaying the details of ONE specific card must be in a function called `displayCard`.  
- The solution must be implemented with **only one function besides main()** (you may choose which single helper function to write; all other logic must be inside main).  
- If the menu is implemented, option **3** is the required EXIT option.

---

## Problem 63 - moonshotai/kimi-k2-instruct-0905 - Iteration 43
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech Lending Locker” that loans out gadgets (calculators, phone chargers, tablets, etc.) to students for 24-hour periods.  
To keep track of what is in stock, the student tech-clerk needs a tiny inventory system that remembers which items are currently available and which have been checked out.  
You will build a **singly-linked list** that stores each gadget as a node and lets the clerk add, delete, search, display, and exit.

## Functional Requirements
1. Each gadget has:
   - an integer ID (unique in the list)  
   - a string name (e.g., “TI-84 Calculator”)  
   - a bool available (true = in locker, false = checked-out)

2. The program must start with an empty list (no dummy head node).

3. The program must repeatedly show a menu:
   ```
   1 Add gadget
   2 Delete gadget by ID
   3 Search gadget by ID
   4 Display all gadgets
   5 Exit
   ```

4. Menu actions:
   - **Add**: Read ID, name, available; insert at the **head** of the list; silently ignore (do nothing) if that ID already exists.
   - **Delete**: Read an ID; if found, remove that node and print `<ID> removed.`; otherwise print `<ID> not found.`
   - **Search**: Read an ID; if found, print the gadget’s name and availability on one line separated by space; otherwise print `Not found.`
   - **Display**: Print one line per node in the exact format `ID name status` where status is `available` or `checked-out`.

5. No global variables except possibly a head pointer.

6. You may assume all inputs are well-formed (no type errors).

## Simple Example Run
Input:
```
1
101
PowerBank-Anker
1
1
102
Calculator-TI84
0
3
101
2
103
4
5
```

Corresponding Output:
```
101 PowerBank-Anker available
103 not found.
101 PowerBank-Anker available
102 Calculator-TI84 checked-out
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (the gadget node).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- Menu option 5 is the only way to EXIT the program.

---

## Problem 64 - moonshotai/kimi-k2-instruct-0905 - Iteration 44
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-Help” desk where students can borrow basic electronics (e.g., calculators, phone chargers, Arduinos).  
To keep track of who has what, you will build a tiny inventory system that stores the items in memory as a **singly linked list**.  
Each node represents one item; the list grows when items are donated and shrinks when items are checked out.

## Requirements
1. Represent every item with at least these fields:  
   - `id` (unique integer ≥ 1)  
   - `name` (string, ≤ 30 characters)  
   - `quantity` (integer ≥ 0)  
2. Maintain the items in a singly linked list that is always **sorted in ascending order by id**.  
3. Provide a text menu with these choices:  
   1) Add new item (insert in the correct sorted position; reject duplicate ids)  
   2) Remove item by id (print “Item not found.” if it does not exist)  
   3) Display all items (one per line: `id name quantity`)  
   4) Exit program  
4. After every successful insertion or removal, immediately display the updated list.  
5. The program must keep running until the user chooses option 4.

## Simple Example Run
```
1) Add
2) Remove
3) Display
4) Exit
Choice: 1
Enter id name quantity: 102 Arduino 5
Current inventory:
102 Arduino 5
1) Add
2) Remove
3) Display
4) Exit
Choice: 1
Enter id name quantity: 101 Calculator 12
Current inventory:
101 Calculator 12
102 Arduino 5
1) Add
2) Remove
3) Display
4) Exit
Choice: 2
Enter id to remove: 102
Current inventory:
101 Calculator 12
1) Add
2) Remove
3) Display
4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Must use a `struct` to represent each node/item.  
- Logic for displaying the details of ONE specific node must be in a function called `displayEntity`.  
- The entire solution must be implemented with **only one additional function besides `main()`** (you may use helper macros or inline code inside main, but only one standalone function).

---

## Problem 65 - moonshotai/kimi-k2-instruct-0905 - Iteration 45
# STEP 1: PROBLEM

## Story
You are the keeper of the Great Library of Alexandria, reborn as a tiny kiosk in the campus bookstore.  
Students slide scrolls (really, titles of books) through a slot.  
Your job is to store them in the exact order they arrive, but you may later be asked to “lose” a scroll by title (someone bought the last copy).  
At any moment the curator can ask you to recite the current catalog from oldest to newest.  
To stay historically accurate, you must store the scrolls in a chain—exactly like the ancient scroll racks—implemented as a singly linked list.

## Requirements
1. Represent each scroll with a node that stores:
   - A unique title (C-string, ≤ 100 characters, no spaces).  
   - A pointer to the next node.  
2. Provide a text menu that loops until the user chooses to exit:
   1. Add a scroll (append to the tail of the list).  
   2. Remove a scroll by title (delete first exact match).  
   3. Display the full catalog (print titles in order, one per line).  
   4. Exit the program (terminates the loop).  
3. After every operation, the program must return to the menu.  
4. If the list is empty and a display or remove is requested, print `Collection is empty.`  

## Example Session (user input after `>`)
```
1
> Learn C Pointers
1
> Mythical Man-Month
3
Learn C Pointers
Mythical Man-Month
2
> Learn C Pointers
3
Mythical Man-Month
4
```
The program ends.

### CONSTRAINTS
- You must use a `struct` named `Scroll` to represent each node.  
- All list operations (add, remove, display) must be implemented inside a single user-defined function called `manageLibrary()`; `main()` may only handle the menu loop and call `manageLibrary()`.

---

## Problem 66 - moonshotai/kimi-k2-instruct-0905 - Iteration 46
# STEP 1: PROBLEM

## Background Story
The tiny village of Nodelia keeps its history in a chain of carved wooden plaques.  
Each plaque stores a single year (an int) and a pointer to the next plaque.  
The village scribe has asked you to write a program that lets her:
- add a new plaque to the front of the chain,
- remove the front plaque,
- print the whole chain from oldest to newest,
- count how many plaques are currently stored, and
- exit when she is done.

## Requirements
1. Represent one plaque with a struct that contains:
   - an integer field `year`
   - a pointer to the next plaque (or NULL if it is the last one).
2. Maintain a global head pointer that always points to the first plaque.
3. Provide a text menu with the following options:
   - 1 – Add a new plaque (ask for the year and push it to the front).
   - 2 – Remove the front plaque.
   - 3 – Display the chain from oldest to newest, one year per line.
   - 4 – Report the current number of plaques.
   - 5 – Exit the program.
4. After every operation (except Exit) re-display the menu.
5. If the user chooses an invalid option, print “Invalid choice.” and re-display the menu.
6. If the user tries to remove or display when the chain is empty, print “Empty chain.”

## Example Session
```
1
Enter year: 2020
1
Enter year: 2021
3
2020
2021
2
3
2020
5
```

### CONSTRAINTS
- You must use a struct to represent each plaque.
- All list operations (insert, remove, display, count) must be implemented in a single user-defined function besides main().
- Menu option 5 is the only way to exit the program.

---

## Problem 67 - moonshotai/kimi-k2-instruct-0905 - Iteration 47
# STEP 1: PROBLEM

## Background Story  
A local music-streaming startup keeps the playlist for each user as a singly linked list of songs.  
Each song node stores the song title (≤30 characters) and its duration in seconds.  
Your task is to build the core linked-list engine that lets the user insert new songs, delete songs, and display the current playlist.

## Requirements  
1. Start with an **empty** playlist (head = NULL).  
2. Support the following menu choices (loop until the user chooses EXIT):  
   1. Insert a song at the **end** of the playlist.  
   2. Delete a song by its exact title (case-sensitive).  
   3. Show the current playlist (one song per line: `title (duration s)`).  
   4. EXIT the program with the keyword `4`.  
3. If a delete operation fails (title not found), print:  
   `Song not found.`  
4. After every insert or delete, the playlist must remain a valid singly linked list.

## Example Session (user input in **bold**)  
```
1
**Midnight City 240**
1
**Daylight 195**
3
Midnight City (240 s)
Daylight (195 s)
2
**Midnight City**
3
Daylight (195 s)
4
```

### CONSTRAINTS  
- Must use a single `struct` called `Song` to represent a node (title, duration, next pointer).  
- All list operations (insert, delete, display) must be implemented in **one** user-defined function besides `main()`.  
- The menu option to EXIT the program is `4`.

---

## Problem 68 - moonshotai/kimi-k2-instruct-0905 - Iteration 48
# STEP 1: PROBLEM
Background  
The campus library has a tiny help-desk called “QuickShelf” that stores the names of books students ask for in the order they are requested. Because the desk is so small, only the oldest request can be served (FIFO). To keep the software simple, the desk clerk insists that the program must run in a single loop and that the entire queue is always printed after each operation so she can see the current waiting list.

Precise Requirements  
1. Represent each book request with a struct containing an integer id and a string title.  
2. Maintain a singly-linked list that models the queue.  
3. Implement exactly four operations (menu options):  
   1. Enqueue a new request (read id and title from stdin).  
   2. Dequeue the oldest request.  
   3. Print the current queue from front to back.  
   4. Exit the program (option 4).  
4. After every enqueue or dequeue, automatically print the queue content on one line, space-separated, in the format  
   id:title id:title …  
   or print “empty” if the queue is empty.  
5. All list manipulations must be done with pointer operations; no STL containers or Java collections allowed.

Simple Example  
Input  
1 100 HarryPotter  
1 101 Hobbit  
2  
4  

Output  
100:HarryPotter  
100:HarryPotter 101:Hobbit  
101:Hobbit  
(empty line, program ends)

### CONSTRAINTS  
- Must use a struct to represent the primary data entity (the book request).  
- The queue logic (enqueue, dequeue, print) must be implemented with a single function besides main().  
- Menu option 4 must exit the program.

---

## Problem 69 - moonshotai/kimi-k2-instruct-0905 - Iteration 49
# STEP 1: PROBLEM

## Background Story
The campus library has installed a new “smart” book return bin.  
Every time a student drops a book in the slot, the bin stores its ISBN in the order it arrived.  
Your task is to write the tiny embedded program that records the returns and, on request, prints the list in the exact order they were received so the librarian can check them back in.

## Requirements
1. Represent the queue of returned ISBNs with a **singly linked list**.
2. Provide a console menu with exactly three choices:
   1. Return a book (read an ISBN and append it to the list)  
   2. Display the current return queue (print ISBNs one per line, oldest first)  
   3. Exit the program (clearly numbered as option 3)
3. After every operation the menu must re-appear until the user chooses 3.
4. Assume ISBNs are strings of at most 20 characters with no spaces.

## Simple Example
Input  
```
1
9780131103627
1
9780131103634
2
3
```

Output  
```
Menu:
1 Return book
2 Show queue
3 Exit
Choice: 1
ISBN: 9780131103627
Menu:
1 Return book
2 Show queue
3 Exit
Choice: 1
ISBN: 9780131103634
Menu:
1 Return book
2 Show queue
3 Exit
Choice: 2
Queue:
9780131103627
9780131103634
Menu:
1 Return book
2 Show queue
3 Exit
Choice: 3
Goodbye!
```

### CONSTRAINTS
- Must use a `struct` to represent each node of the linked list.  
- Logic for displaying the queue must be encapsulated in a single function named `displayQueue`.

---

## Problem 70 - moonshotai/kimi-k2-instruct-0905 - Iteration 50
# STEP 1: PROBLEM

### Background Story
The campus library has a “Fast-Return” box where students drop books without lining up at the desk.  
To keep track of what comes in, the librarian wants a tiny terminal program that remembers the **order** of returned books.  
Your task is to simulate this with a **singly linked list** that stores book IDs (positive integers).  
Every time a student drops a book, the ID is appended to the list; when the librarian is ready to process returns, she removes the **oldest** ID (FIFO).  
She also needs to peek at the next book to be processed and to see the whole queue at any moment.

### Functional Requirements
1. Read commands from standard input until the user chooses to exit.
2. Support four commands (case-insensitive):
   - `ADD <id>`  – append the book ID (positive int) to the tail of the list.  
   - `PROCESS`   – remove the ID from the head and print `Processing book <id>`.  
     If the list is empty, print `Box is empty`.  
   - `PEEK`      – print the ID at the head without removing it.  
     If the list is empty, print `Box is empty`.  
   - `LIST`      – print the IDs in order from head to tail, space-separated on one line.  
     If the list is empty, print `Box is empty`.  
3. The program must terminate **only** when the user selects the EXIT option.

### Simple Example Input/Output
Input
```
ADD 101
ADD 102
PEEK
LIST
PROCESS
LIST
EXIT
```

Output
```
101
101 102
Processing book 101
102
```

### CONSTRAINTS
- You **must** use a `struct` to represent each node of the singly linked list.  
- All list operations (add, remove, peek, display) must be implemented in **one single function** besides `main()`.  
- The menu option to EXIT is the integer `0`.

---

## Problem 71 - moonshotai/kimi-k2-instruct-0905 - Iteration 51
# STEP 1: PROBLEM

## Background Story
The campus library has asked your CS class to build a tiny, self-contained system that keeps track of the next book to be shelved.  
Instead of an array (which shifts are expensive), you decide to model the “to-shelve” list as a **singly linked list** where every node stores a book’s ID (an int) and a string with the book’s title.  
The librarian can add new books to the **front** (they’re the most urgent) and, once a book is shelved, remove it from the **front**.  
At any moment the librarian may also ask to see the current list in order.

## Precise Requirements
1. Represent each book with a node that contains:
   - `id` (positive int)
   - `title` (C-string, ≤ 80 chars, no spaces)
2. Maintain a singly linked list whose **head pointer is a global variable**.
3. Implement exactly three operations (choose via a simple text menu):
   - `1` Add a book to the **front** of the list  
     (read id and title from stdin; if id already exists, ignore the request and print `Duplicate ID`)
   - `2` Remove the book at the **front**  
     (print `Removed: <id> <title>` or `Empty` if nothing to remove)
   - `3` Print the entire list from head to tail, one line per book:  
     `<id> <title>`
   - `4` Exit the program
4. No memory leaks: every removed node must be freed.

## Simple Example Run
```
1
101 AtlasShrugged
1
202 AnimalFarm
3
202 AnimalFarm
101 AtlasShrugged
2
Removed: 202 AnimalFarm
3
101 AtlasShrugged
4
```
(Program ends.)

### CONSTRAINTS
- Must use a `struct Node` to represent each list element.  
- All list operations (insert, delete, print) must be implemented in **a single function** besides `main()`.  
- Menu option `4` must immediately terminate the program.

---

## Problem 72 - moonshotai/kimi-k2-instruct-0905 - Iteration 52
# STEP 1: PROBLEM

## Context
The campus library is digitising its card-catalogue system.  
For every book they store only three things (in this order):
1. a unique integer ID
2. the book’s title
3. the author’s name

Because the collection is small, the librarian insists on keeping the books in **alphabetical order by title** (A→Z) so that visitors can browse the list quickly.  
Your job is to write a tiny command-line program that lets the staff insert new books while maintaining that order, and to list all books whenever asked.

## Requirements
1. Represent each book with a `struct` containing the three fields above.
2. Keep the collection as a **singly linked list** whose nodes are ordered by `title` (case-sensitive, lexicographic).
3. Support exactly two user commands (plus exit):
   - `insert id title author`  
     Insert a new book with the given id, title, and author.  
     If a book with the same id already exists, print `Duplicate ID` and do nothing.
   - `list`  
     Print every book in order, one per line, in the exact format  
     `id) Title by Author`  
     If the collection is empty, print `Empty catalogue`.
   - `0` (the number zero)  
     Exit the program.
4. After each command (except exit) the program must return to the prompt and wait for the next command.
5. All dynamic memory you allocate must be freed before the program exits.

## Simple Example
Input
```
insert 7 ThePragmaticProgrammer AndrewHunt
insert 3 CleanCode RobertMartin
list
insert 7 Refactoring MartinFowler
0
```

Output
```
3) CleanCode by RobertMartin
7) ThePragmaticProgrammer by AndrewHunt
Duplicate ID
```

## CONSTRAINTS
- You must use a `struct` to represent each book node.
- The only functions you may write besides `main()` are:
  - `insertBook()` – inserts a book in the correct position
  - `displayCatalogue()` – prints the entire list
- No global variables are allowed; pass the head pointer around explicitly.
- The menu option to EXIT the program is the number `0`.

---

## Problem 73 - moonshotai/kimi-k2-instruct-0905 - Iteration 53
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old card-catalogue system.  
Each index card contains a book’s call-number (a unique string) and its title.  
Your task is to write a tiny in-memory catalogue that keeps the cards in the same order they were entered (like a stack on the librarian’s desk) and lets the librarian add, inspect, and discard cards.

## Requirements
1. Represent each card with two fields:  
   - `callNumber` (C-string, max 19 chars + terminating null)  
   - `title` (C-string, max 99 chars + terminating null)  
2. Store the cards in a **singly linked list** whose nodes are created with dynamic memory (`malloc`).  
3. Provide a **text menu** with exactly these choices:  
   1) Add a new card to the **front** of the list  
   2) Display every card in order (one per line: `callNumber: title`)  
   3) Remove the **first** card (the one most recently added)  
   4) Exit the program  
4. After every operation, re-display the menu (loop until the user chooses 4).  
5. Handle empty-list cases gracefully (print nothing for “Display” and “Cannot remove from empty catalogue” for “Remove”).  
6. No global variables except possibly the head pointer inside `main`.

## Simple Example Run
```
1) Add  2) Display  3) Remove  4) Exit
Choice: 1
Call number: QA76.6  Title: Introduction to Algorithms
1) Add  2) Display  3) Remove  4) Exit
Choice: 1
Call number: TK7895  Title: Computer Architecture
1) Add  2) Display  3) Remove  4) Exit
Choice: 2
TK7895: Computer Architecture
QA76.6: Introduction to Algorithms
1) Add  2) Display  3) Remove  4) Exit
Choice: 3
Removed TK7895
1) Add  2) Display  3) Remove  4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Must use a `struct` to represent each list node (the card plus `next` pointer).  
- Logic for displaying the details of ONE specific card must be in a function called `displayCard`.  
- The solution must be implemented with a single function besides `main()` (you may reuse `displayCard` for the whole list).  
- Menu option 4 is the **only** way to exit; the program must terminate cleanly with `return 0;`.

---

## Problem 74 - moonshotai/kimi-k2-instruct-0905 - Iteration 54
# STEP 1: PROBLEM

## Background Story
The campus library has a “Take-a-Book, Leave-a-Book” shelf that works like a tiny, ever-changing library.  
To keep track of which paperbacks are currently on the shelf, the student volunteers want a program that remembers the order in which books were added (so the oldest can be given away first).  
You will build a tiny inventory manager that keeps the titles in a **singly linked list**.

## Requirements
1. Define a singly linked list where each node stores:
   - a unique ID (positive integer)
   - the book title (single-line string, max 100 characters)
2. Provide a text menu with the following options:
   1. Add a new book (oldest to the front, newest to the back)
   2. Display the entire shelf (one book per line, in order from oldest to newest)
   3. Remove the oldest book (head of the list)
   4. Exit the program (keyword `4`)
3. After every successful operation print a short confirmation message.
4. If the list is empty and the user tries to remove or display, print “Shelf is empty.”
5. All dynamic memory must be freed before the program exits.

## Example Run
```
1. Add book
2. Display shelf
3. Remove oldest
4. Exit
Choice: 1
Enter ID: 101
Enter title: Dune
Book added.

1. Add book
2. Display shelf
3. Remove oldest
4. Exit
Choice: 1
Enter ID: 102
Enter title: Neuromancer
Book added.

1. Add book
2. Display shelf
3. Remove oldest
4. Exit
Choice: 2
101 | Dune
102 | Neuromancer

1. Add book
2. Display shelf
3. Remove oldest
4. Exit
Choice: 3
Removed 101 | Dune

1. Add book
2. Display shelf
3. Remove oldest
4. Exit
Choice: 4
Goodbye!
```

### CONSTRAINTS
- Must use a `struct` to represent each node.
- The logic for displaying the details of ONE specific book must be in a function called `displayEntity`.
- No global variables; use only local variables and parameters.
- The menu option to exit the program is `4`.

---

## Problem 75 - moonshotai/kimi-k2-instruct-0905 - Iteration 55
# STEP 1: PROBLEM  
## Topic: Implementing a Singly Linked List

### Background Story  
The campus library has just digitised its catalogue of textbooks. Each book is stored as a node in a singly linked list so that new arrivals can be inserted quickly at the head of the list, while keeping memory usage low. You are asked to write a tiny demo program that librarians can run to add books and display the current shelf.

### Functional Requirements  
1. Represent a book with at least the following data:  
   - `id` (unique positive integer)  
   - `title` (string, no commas)  
   - `author` (string, no commas)  

2. Maintain the books in a singly linked list.

3. Provide a text menu with two options (and an exit):  
   1. Insert a new book (adds at the head of the list)  
   2. Display all books in the order they were inserted (head → tail)  
   3. Exit the program  

4. After every insertion or display request, re-show the menu.

5. Handle invalid menu choices by re-printing the menu.

### Simple Example  
Input (user responses in **bold**):
```
1
101
Introduction to Algorithms
Cormen
2
3
```
Output:
```
1) Insert book
2) Display books
3) Exit
Choice: 1
Enter id: 101
Enter title: Introduction to Algorithms
Enter author: Cormen
1) Insert book
2) Display books
3) Exit
Choice: 2
ID: 101, Title: Introduction to Algorithms, Author: Cormen
1) Insert book
2) Display books
3) Exit
Choice: 3
Goodbye!
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (a book node).  
- The logic for displaying the details of **one specific book** must be in a function called `displayBook`.  
- The entire solution must be implemented with **only one additional function besides `main()`** (you may choose which one).  
- If a menu is implemented (which it is), the exit option must be option number **3**.

---

## Problem 76 - moonshotai/kimi-k2-instruct-0905 - Iteration 56
# STEP 1: PROBLEM

## Background Story
You are helping the campus music club build a playlist manager for their Thursday-night open-mic sessions.  
The songs must be played in the exact order they are submitted, but the host needs the ability to drop the last submission if it is inappropriate or to review the entire list before showtime.  
Your task is to write a tiny console app that keeps the submissions in a singly linked list and lets the host add, remove, or display songs.

## Functional Requirements
1. Represent each song with an integer ID (the submission order) and a string title.
2. Maintain the songs in a singly linked list that always appends new songs to the **tail** (end).
3. Implement exactly three user commands:
   - `add <ID> "<Title>"` – append the song (assume ID is unique).
   - `remove` – delete the last song in the list (print `Nothing to remove` if empty).
   - `show` – print the full playlist, one song per line, in the format `ID: Title`.
4. Commands are entered by the user in any order until the host types `exit`, which terminates the program.
5. After every `add` or `remove`, print `Added` or `Removed` respectively (lower-case exactly).

## Simple Example Run
```
> add 1 "Blinding Lights"
Added
> add 2 "Levitating"
Added
> show
1: Blinding Lights
2: Levitating
> remove
Removed
> show
1: Blinding Lights
> exit
```

## CONSTRAINTS
- Must use a `struct` named `Song` to represent the primary data entity.
- All list operations (append, delete-last, display) must be implemented in a single function `managePlaylist()`; `main()` is only allowed to handle user input and call this function.
- The program must support the command `exit` (case-insensitive) to terminate.

---

## Problem 77 - moonshotai/kimi-k2-instruct-0905 - Iteration 57
# STEP 1: PROBLEM

## Background Story
The campus library has just switched to a fully digital check-out system.  
Every time a student borrows a book, the system must record the book’s unique call-number (an integer) and the student’s ID (also an integer).  
Because the traffic is light, the head librarian has asked you to implement a **minimal, memory-efficient** system that keeps these records in the exact order they arrive, and must be able to:

- add a new loan record,
- display all current loans, and
- delete the **oldest** loan (the one at the front of the list) when the book is returned.

To keep the code short and easy to audit, the librarian insists that **only one programmer-defined function besides `main()`** is used.

---

## Functional Requirements
1. Represent each loan as a node in a **singly linked list**.
2. Provide a **text menu** that repeats until the user chooses to exit.
3. Menu options:
   - `1` Add a new loan (read call-number and student ID).
   - `2` Display every loan in order from oldest to newest (one line per loan: `call-number student-ID`).
   - `3` Delete the oldest loan (the head node).
   - `4` Exit the program.
4. If the user tries to delete or display when the list is empty, print the exact message: `List is empty.`
5. All dynamic memory must be properly freed before the program exits.

---

## Simple Example Run
```
1
101 90001
1
102 90002
2
101 90001
102 90002
3
2
102 90002
4
```
(Program ends.)

---

### CONSTRAINTS
- You **must** define a `struct` to represent each loan node.  
- The **entire solution** must be implemented with **only one programmer-defined function besides `main()`**.  
- Menu option `4` is the **EXIT** option.

---

## Problem 78 - moonshotai/kimi-k2-instruct-0905 - Iteration 58
# STEP 1: PROBLEM  
Topic: Implementing Data Structures (e.g., Singly Linked Lists)

Story  
You are a teaching assistant for the first–year biology lab.  Every afternoon, students drop in to borrow a microscope, and the lab keeps a waiting list.  Today, the waiting list is handled electronically: each student is added at the tail of a singly linked list when they arrive, and is removed from the head when a microscope becomes free.

Problem  
Write a small console program that records the waiting list for the biology microscopes.  The program must support the following operations:

1. Add a student to the tail of the list.  
2. Remove the student at the head of the list.  
3. Display the entire waiting list (head → tail).  
4. Exit the program.

Input/Output  
Each operation is selected from a menu.  The only data stored per student is a unique string (student ID).

 nothing else.

Simple Example  
Menu  
1. Add student  
2. Remove student  
3. Display list  
4. Exit  
Select: 1  
Enter student ID: Alice  
Select: 1  
Enter student ID: Bob  
Select: 3  
Waiting list:  
Alice → Bob  
Select: 2  
Removed Alice  
Select: 3  
Waiting list:  
Bob →

### CONSTRAINTS  
1. Represent each student as a struct Node containing a string studentID and a pointer next.  
2. The waiting list must be a singly linked list.  
3. The program must be implemented with exactly one function besides main(): the menu driver.  
4. The menu must include option 4 Exit; selecting it terminates the program.

---

## Problem 79 - moonshotai/kimi-k2-instruct-0905 - Iteration 59
# STEP 1: PROBLEM

## Context
The campus library is digitizing its old card-catalog.  
Each catalog card contains a book’s call-number (a unique string) and title.  
Your job is to write a tiny "live catalog" program that keeps these cards in **call-number order** using a **singly linked list**.  
Users can add a new card, remove one by call-number, or print the whole catalog.

## Requirements
1. Represent each catalog card with two fields:
   - `callNumber` (C-string, ≤ 20 chars, unique)
   - `title` (C-string, ≤ 100 chars)
2. Store the cards in **ascending lexicographic order of call-number** at all times.
3. Provide a text menu with exactly these choices:
   1. Add card
   2. Remove card
   3. Show catalog
   4. Exit
4. Adding:
   - Reject duplicates (print `"Duplicate call-number."`)
   - Insert in the correct sorted position without rebuilding the list.
5. Removing:
   - Delete by call-number; if not found print `"Card not found."`
6. Showing:
   - Print one line per card in the exact format  
     `call-number: title`  
     (If the catalog is empty, print `"Catalog is empty."`)

## Simple Example (user input after `>`)
```
1
> A123.4
> Introduction to Algorithms
1
> B56
> Operating Systems
3
A123.4: Introduction to Algorithms
B56: Operating Systems
2
> A123.4
Card removed.
3
B56: Operating Systems
4
```
(Program ends)

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a catalog card).
- The logic for displaying the details of ONE specific card must be in a function called `displayCard`.
- The menu option to EXIT the program is option 4.

---

## Problem 80 - moonshotai/kimi-k2-instruct-0905 - Iteration 60
# STEP 1: PROBLEM

## Context
The campus library has a tiny “Take-a-Book, Leave-a-Book” shelf that only holds one copy of each title.  
To keep track of which books are on the shelf, the librarian asks you to build a very small inventory system.  
Because the shelf is so small, the librarian wants to be able to insert a new book at any chosen position in the list, remove a book by title, and instantly see the current list of books in order.  
You decide that a singly linked list is perfect for this job.

## Requirements
1. Represent each book with a struct that stores:
   - a unique title (string, ≤100 chars, no spaces)  
   - a struct pointer to the next book.

2. Maintain the inventory as a singly linked list whose head is a global pointer (or returned/updated through parameters—your choice).

3. Provide three operations (menu driven):
   1. Insert a new title at a 1-based position.  
      If position ≤ 0 or greater than current length+1, print “Invalid position” and do nothing.  
   2. Remove a title.  
      If the title is not found, print “Title not found”.  
   3. Display the current list from first to last, one title per line.  
   4. Exit the program.

4. All dynamic memory (malloc/free) must be handled explicitly; no memory leaks.

## Simple Example
Input
```
1
Pride
1
2
Prejudice
2
1
Pride
3
4
```
Output
```
Invalid position
Prejudice
Title not found
Pride
Prejudice
```
(The first “Invalid position” appears because the second insertion tries position 2 when only one book exists.)

### CONSTRAINTS
- You must use a struct to represent the primary data entity (the book node).  
- All list-modifying logic (insert, remove) must be implemented in a single function besides main().  
- The menu option to EXIT the program is 4.

---

## Problem 81 - openai/gpt-oss-120b - Iteration 31
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its inventory system.  Each book is identified by a **unique ISBN**, has a **title**, an **author**, and a **year of publication**.  The library wants a simple console program that lets a clerk add new books, remove books that are withdrawn, and look up a book by its ISBN.  Because the clerk will be entering and deleting books frequently, the data should be stored in a **singly linked list** that grows and shrinks dynamically.

## Requirements  

Write a C (or C‑like) program that provides the following functionality through a text‑based menu:

1. **Add a Book** – Prompt the user for ISBN (string, no spaces), title, author, and year, then insert the new book at the **head** of the linked list.  
2. **Remove a Book** – Prompt for an ISBN and delete the first node whose ISBN matches. If the ISBN is not found, display a message.  
3. **Find a Book** – Prompt for an ISBN and display all details of the matching book. If not found, display a message.  
4. **List All Books** – Traverse the list from head to tail and print the details of every stored book in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.

All input should be read from standard input, and all output written to standard output. The program should continue to display the menu after completing an operation (except when the user chooses **Exit**).

## Example Input / Output  

```
===== Library Book Manager =====
1. Add a Book
2. Remove a Book
3. Find a Book
4. List All Books
5. Exit
Choose an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Year: 1988
Book added successfully!

===== Library Book Manager =====
1. Add a Book
2. Remove a Book
3. Find a Book
4. List All Books
5. Exit
Choose an option: 4

Current books in inventory:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1988

===== Library Book Manager =====
1. Add a Book
2. Remove a Book
3. Find a Book
4. List All Books
5. Exit
Choose an option: 5

Goodbye!
```

*If the user tries to remove or find a book that does not exist, the program should output:*  

```
Book with ISBN <ISBN> not found.
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a book) **must be defined using a `struct`** named `BookNode` that contains the ISBN, title, author, year, and a pointer to the next node.  
2. **Display Function** – The logic for printing the details of **one specific book** must be placed in a function with the exact prototype:  

   ```c
   void displayBook(const BookNode *node);
   ```  

3. **Memory Management** – Every node allocated with `malloc`/`new` must be freed exactly once before program termination.  
4. **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option ends the loop and frees all resources.  

*No additional libraries beyond the standard I/O and memory‑management libraries may be used.*

---

## Problem 82 - openai/gpt-oss-120b - Iteration 32
# STEP 1: PROBLEM  

## Background  
The ancient kingdom of **Algoria** maintains a **registry of heroic quests**. Each quest is recorded with a unique ID, the name of the hero who undertook it, and the number of days the quest lasted. The kingdom’s archivist wants a simple console program to keep this registry up‑to‑date while the students of the Royal Academy learn how singly linked lists work.

## Requirements  
Write a C (or C++) program that implements a **singly linked list** to store the quest records. The program must present a text‑based menu that allows the user to perform the following operations:

1. **Add a new quest** – Prompt for the quest ID (integer), hero name (single‑word string, max 31 characters), and duration in days (integer). Insert the new node at the **head** of the list.  
2. **Delete a quest by ID** – Prompt for a quest ID and remove the first node whose ID matches. If no such quest exists, display an appropriate message.  
3. **Search and display a quest by ID** – Prompt for a quest ID and show all its fields using the required display function (see constraints). If the quest is not found, inform the user.  
4. **Display all quests** – Traverse the list from head to tail, printing each quest on its own line.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.

The menu should repeat after each operation until the user chooses the **Exit** option.

## Example Input / Output  

```
=== Quest Registry Menu ===
1. Add Quest
2. Delete Quest
3. Search Quest
4. List All Quests
5. Exit
Choose an option: 1

Enter Quest ID: 101
Enter Hero Name: Aria
Enter Duration (days): 7
Quest added.

=== Quest Registry Menu ===
1. Add Quest
2. Delete Quest
3. Search Quest
4. List All Quests
5. Exit
Choose an option: 1

Enter Quest ID: 202
Enter Hero Name: Boren
Enter Duration (days): 12
Quest added.

=== Quest Registry Menu ===
1. Add Quest
2. Delete Quest
3. Search Quest
4. List All Quests
5. Exit
Choose an option: 4

Quest ID: 202 | Hero: Boren | Days: 12
Quest ID: 101 | Hero: Aria  | Days: 7

=== Quest Registry Menu ===
1. Add Quest
2. Delete Quest
3. Search Quest
4. List All Quests
5. Exit
Choose an option: 3

Enter Quest ID to search: 101
Quest ID: 101 | Hero: Aria | Days: 7

=== Quest Registry Menu ===
1. Add Quest
2. Delete Quest
3. Search Quest
4. List All Quests
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Structure**: The primary entity (a quest) **must be represented with a `struct`** named `QuestNode` (or equivalent) containing at least the fields `id`, `heroName`, `duration`, and a pointer to the next node.  
- **Display Function**: The logic for showing the details of **one specific quest** must reside in a **function called `displayQuest`** that takes a pointer to a `QuestNode` and prints the fields in the format shown in the example.  
- **Memory Management**: All nodes allocated on the heap must be freed before the program terminates (e.g., when exiting).  
- **Menu Requirement**: The program **must include a menu option to EXIT the program** (option 5 in the example). Selecting this option ends the loop and frees any remaining list memory.  
- **Single‑Responsibility Functions**: Apart from `main`, you may create additional helper functions (e.g., `addQuest`, `deleteQuest`, `searchQuest`, `listQuests`), but each should perform a clearly defined sub‑task.  

*The problem is intended for students who have just learned how to build and manipulate singly linked lists. The specifications are deliberately straightforward to focus on correct list operations, struct usage, and basic I/O.*

---

## Problem 83 - openai/gpt-oss-120b - Iteration 33
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑tracking system. Each bus that is currently on the road is represented by a **BusRecord** that stores the bus’s unique identifier, its current route number, and the number of passengers on board. The authority wants a simple console program that lets an operator add new buses, remove buses that have completed their routes, and query the list of active buses.  

Your task is to implement this system using a **singly linked list**. The list will hold the `BusRecord` structures in the order they are entered (i.e., insertion at the tail). The operator will interact with the program through a text‑based menu.

## Requirements  

1. **Data Entity**  
   * Define a `struct` named `BusRecord` with the following fields:  
     - `int id` – unique bus identifier (positive integer)  
     - `int route` – route number (positive integer)  
     - `int passengers` – number of passengers currently on board (non‑negative integer)  

2. **Menu‑driven Operations** (the program must display a menu and process the user’s choice)  
   * **1. Add a bus** – Prompt for `id`, `route`, and `passengers`; create a new node and append it to the tail of the list.  
   * **2. Remove a bus** – Prompt for a bus `id`; locate the node with that `id` and delete it from the list. If the `id` is not found, display an appropriate message.  
   * **3. Display all buses** – Traverse the list and print each bus’s details on a separate line in the format:  
     `Bus <id>: Route <route>, Passengers <passengers>`  
   * **4. Display a specific bus** – Prompt for a bus `id` and invoke a dedicated function `displayBus` to print the details of that single bus in the same format as above. If the `id` does not exist, inform the user.  
   * **5. EXIT** – Terminate the program gracefully.  

3. **Memory Management**  
   * Allocate nodes dynamically (e.g., using `malloc`/`new`).  
   * Free memory for a node when it is removed and also free the entire list before program exit.  

4. **Input Validation**  
   * The menu choice must be an integer between 1 and 5.  
   * Bus `id` values must be positive and unique when adding a new bus. If a duplicate `id` is entered, reject the addition with an explanatory message.  

## Example Interaction  

```
=== Bus Tracking System ===
1) Add a bus
2) Remove a bus
3) Display all buses
4) Display a specific bus
5) EXIT
Enter choice: 1
Enter bus id: 101
Enter route number: 12
Enter passenger count: 35
Bus added.

=== Bus Tracking System ===
1) Add a bus
2) Remove a bus
3) Display all buses
4) Display a specific bus
5) EXIT
Enter choice: 1
Enter bus id: 202
Enter route number: 7
Enter passenger count: 20
Bus added.

=== Bus Tracking System ===
1) Add a bus
2) Remove a bus
3) Display all buses
4) Display a specific bus
5) EXIT
Enter choice: 3
Bus 101: Route 12, Passengers 35
Bus 202: Route 7, Passengers 20

=== Bus Tracking System ===
1) Add a bus
2) Remove a bus
3) Display all buses
4) Display a specific bus
5) EXIT
Enter choice: 4
Enter bus id to display: 202
Bus 202: Route 7, Passengers 20

=== Bus Tracking System ===
1) Add a bus
2) Remove a bus
3) Display all buses
4) Display a specific bus
5) EXIT
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Structure Requirement** – The primary data entity must be represented with a `struct` named `BusRecord`.  
2. **Function Requirement** – The logic that prints the details of **one** specific bus must reside in a function with the exact prototype:  

   ```c
   void displayBus(const BusRecord *bus);
   ```

   (or the equivalent in C++/Java/Python with the same name).  
3. **Single‑purpose Helper Functions** – Apart from `main`, you may create additional helper functions, but each distinct operation (add, remove, display all, display one) must be encapsulated in its own function.  
4. **Menu Exit Option** – The menu must include the option **5) EXIT** (or the keyword `EXIT`) that ends the program.  

*The problem is intended for students who have just learned how to implement a singly linked list, dynamic memory allocation, and basic modular programming.*

---

## Problem 84 - openai/gpt-oss-120b - Iteration 34
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by a **call number** (an integer) and has a **title** (a short string). The library wants a simple console application that stores the books in the order they are received, allows staff to add new books, remove the oldest book, and look up a book by its call number. Because the number of books can change dynamically, the data must be kept in a **singly linked list**.

## Requirements  
Write a program that implements the following functionality:

1. **Add a book** – Prompt the user for a call number and a title, then insert the new book at the **tail** of the list (i.e., after all existing books).  
2. **Remove the oldest book** – Delete the node at the **head** of the list and display the removed book’s details. If the list is empty, print an appropriate message.  
3. **Find a book** – Prompt for a call number, search the list, and display the title of the matching book. If the call number is not present, inform the user.  
4. **Display all books** – Traverse the list from head to tail and print each book’s call number and title in the order they were added.  
5. **Exit** – Terminate the program gracefully.

The program should present a text‑based menu that repeatedly asks the user to choose one of the actions above.

## Example Input / Output  

```
=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 1

Enter call number: 1023
Enter title: Introduction to Algorithms
Book added.

=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 1

Enter call number: 2045
Enter title: Data Structures in C
Book added.

=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 4

Current collection:
[1023] Introduction to Algorithms
[2045] Data Structures in C

=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 3

Enter call number to find: 2045
Title: Data Structures in C

=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 2

Removed book: [1023] Introduction to Algorithms

=== Library Book Manager ===
1. Add a book
2. Remove the oldest book
3. Find a book by call number
4. Display all books
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  
- The primary data entity **must be represented with a `struct`** named `BookNode` containing at least:
  - `int callNumber;`
  - `char title[101];` (titles are limited to 100 characters plus the null terminator)
  - `struct BookNode *next;`
- The logic for displaying the details of **ONE specific book** (used when a book is found or removed) **must be placed in a function called `displayBook(const BookNode *node)`**.
- All list manipulation (insertion, deletion, search, traversal) should be performed in functions separate from `main()`. You may create as many helper functions as needed, but **no more than one additional function besides `main()` may be used for each distinct operation** (e.g., `addBook`, `removeHead`, `findBook`, `printAll`).
- **If a menu is implemented (as required), the menu must include an explicit option to EXIT the program**. In the example above this is option `5`. The exit option must be clearly labeled and must cause the program to terminate without further prompts.

*Note: The problem is intended for students who have just learned singly linked lists, structs, and basic modular programming.*

---

## Problem 85 - openai/gpt-oss-120b - Iteration 35
# STEP 1: PROBLEM  

## Background  
The campus library wants a tiny command‑line utility to keep track of the books that are currently on a single shelf.  Each book is identified by an **ISBN**, has a **title**, and a **year of publication**.  The librarian will manually add books to the shelf, remove them when they are taken off, and occasionally request a listing of all books or the details of a specific ISBN.  

Your task is to implement this utility using a **singly linked list**.  The list must be built from scratch (no STL containers, no `vector`, etc.) and must reflect the order in which books are added – new books are appended to the tail of the list.

## Requirements  

Write a program that provides a **menu‑driven** interface with the following options:

1. **Add a new book** – Prompt for ISBN (string, no spaces), title (string, may contain spaces), and year (integer).  Append the new book to the end of the list.  
2. **Remove a book** – Prompt for an ISBN.  If a node with that ISBN exists, delete it from the list and free its memory; otherwise, print “Book not found.”  
3. **Display all books** – Traverse the list from head to tail and print each book on its own line in the format:  
   `ISBN | Title | Year`  
   If the list is empty, print “No books on the shelf.”  
4. **Search for a book by ISBN** – Prompt for an ISBN and, if found, display that single book’s details using the required helper function (see Constraints). If not found, print “Book not found.”  
5. **Exit** – Terminate the program gracefully.

The program should loop until the user selects the **Exit** option.

## Example Interaction  

```
--- Library Shelf Manager ---
1) Add book
2) Remove book
3) Display all books
4) Search by ISBN
5) Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter year: 1978
Book added.

--- Library Shelf Manager ---
1) Add book
2) Remove book
3) Display all books
4) Search by ISBN
5) Exit
Choose an option: 1
Enter ISBN: 9780201633610
Enter title: Design Patterns
Enter year: 1994
Book added.

--- Library Shelf Manager ---
1) Add book
2) Remove book
3) Display all books
4) Search by ISBN
5) Exit
Choose an option: 3
9780131103627 | The C Programming Language | 1978
9780201633610 | Design Patterns | 1994

--- Library Shelf Manager ---
1) Add book
2) Remove book
3) Display all books
4) Search by ISBN
5) Exit
Choose an option: 4
Enter ISBN to search: 9780201633610
9780201633610 | Design Patterns | 1994

--- Library Shelf Manager ---
1) Add book
2) Remove book
3) Display all books
4) Search by ISBN
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary entity (a book) must be stored in a `struct` named `BookNode` that contains the ISBN, title, year, and a pointer to the next node.  
* **Helper Function** – The logic for displaying the details of **ONE specific book** must reside in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
  This function should print the book in the format `ISBN | Title | Year` followed by a newline.  
* **Menu Implementation** – The menu must include an explicit option to **EXIT** the program (option 5 in the example). Selecting this option must end the program without memory leaks.  
* **Memory Management** – Every `malloc`/`new` (depending on language) must have a corresponding `free`/`delete` when a node is removed or when the program terminates.  
* **Single‑File Requirement** – All code must reside in a single source file; you may define additional static/helper functions, but no separate compilation units.  

Feel free to choose C, C++, or any language that lets you manually manage a singly linked list and satisfy the constraints above.

---

## Problem 86 - openai/gpt-oss-120b - Iteration 36
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  The librarian wants a simple console program that can keep track of **books** as they are added, removed, or searched.  Each book is identified by a unique integer **ISBN**, has a **title**, and a **year of publication**.  Because the library’s collection is constantly changing, a **singly linked list** is an appropriate data structure: new books are appended to the end of the list, and deletions can occur anywhere in the list.

You have just finished a unit on singly linked lists.  Write a program that implements the required operations using a linked list.

## Requirements  

Your program must provide a **menu‑driven interface** with the following options (the numbers are mandatory):

1. **Add a new book** – Prompt for ISBN, title, and year, then insert the new node at the **end** of the list.  
2. **Delete a book** – Prompt for an ISBN; if a node with that ISBN exists, remove it from the list and free its memory; otherwise display “Book not found.”  
3. **Search for a book** – Prompt for an ISBN; if found, display the book’s details; otherwise display “Book not found.”  
4. **Display all books** – Traverse the list from head to tail, printing each book on a separate line in the order they were added.  
5. **EXIT** – Terminate the program gracefully.

Additional functional requirements:

- The list must be **initially empty**.
- ISBN values are guaranteed to be positive integers and unique for each insertion.
- Title may contain spaces; read it as a whole line.
- Year is a four‑digit integer.
- All user prompts and messages should be clear but need not follow an exact wording beyond the required output shown in the example.

## Example Input / Output  

```
--- Library Book Manager ---
1. Add a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter year: 1978
Book added.

--- Library Book Manager ---
1. Add a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 1
Enter ISBN: 9780201616224
Enter title: The Pragmatic Programmer
Enter year: 1999
Book added.

--- Library Book Manager ---
1. Add a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 4
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1978
ISBN: 9780201616224 | Title: The Pragmatic Programmer | Year: 1999

--- Library Book Manager ---
1. Add a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 3
Enter ISBN to search: 9780201616224
ISBN: 9780201616224 | Title: The Pragmatic Programmer | Year: 1999

--- Library Book Manager ---
1. Add a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a book) must be represented with a `struct` named `BookNode` (or equivalent) containing at least the fields `int isbn; char title[100]; int year; struct BookNode *next;`.  
2. **Display Function** – The logic for showing the details of **one specific book** (used in the “Search” option) must reside in a function with the exact prototype:  

   ```c
   void displayBook(const BookNode *node);
   ```  

3. **Function Count** – Apart from `int main(void)`, the entire solution may contain **only one additional user‑defined function** (i.e., `displayBook`). All list manipulation (add, delete, traverse, search) must be performed directly inside `main` or helper code placed inside `main`’s body.  
4. **Menu Exit Option** – The menu must include the option **5. EXIT** (or the keyword “EXIT”) that terminates the program. Selecting this option must end the program without memory leaks.  

*Note:* The problem is deliberately restrictive to encourage careful organization of code within `main`.

---

## Problem 87 - openai/gpt-oss-120b - Iteration 37
# STEP 1: PROBLEM  

## Background  
The local **Community Wildlife Sanctuary** wants a simple console‑based system to keep track of the animals that are currently in its care.  Each animal has a name, species, and an integer identifier (ID).  The sanctuary staff are not programmers, so the program must be easy to use: a text menu that lets them **add**, **remove**, **search**, and **list** animals.  

You have just finished the lecture on **singly linked lists**.  Implement the required functionality using a singly linked list to store the animal records.

---

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Animal` that stores:  
     - `int id` – a unique identifier (positive integer)  
     - `char name[50]` – the animal’s name (no spaces)  
     - `char species[30]` – the species name (no spaces)  
   * The linked‑list node must contain an `Animal` object and a pointer to the next node.

2. **Menu‑driven program** (displayed repeatedly until the user chooses to exit)  
   * **1. Add a new animal** – prompt for `id`, `name`, and `species`; insert the new node at the **head** of the list.  
   * **2. Remove an animal by ID** – prompt for an `id`; delete the first node whose `id` matches. If no such animal exists, print a suitable message.  
   * **3. Search for an animal by name** – prompt for a `name`; traverse the list and display the details of the first matching animal (use the required display function). If not found, report it.  
   * **4. List all animals** – traverse the list from head to tail and display each animal’s details (use the required display function). If the list is empty, print “No animals recorded.”  
   * **5. EXIT** – terminate the program.  

3. **Display function**  
   * Implement a function `void displayAnimal(const Animal *a)` that prints an animal’s details in the format:  
     ```
     ID: <id>, Name: <name>, Species: <species>
     ```

4. **Memory management**  
   * Allocate nodes dynamically (`malloc`/`new` depending on language).  
   * Free memory for a node when it is removed and also before program termination.

5. **Input validation**  
   * Assume the user enters data of the correct type; you do not need to handle malformed input beyond the menu choice.

---

## Example Interaction  

```
=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 1
Enter ID: 101
Enter name: Leo
Enter species: Lion
Animal added.

=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 1
Enter ID: 202
Enter name: Maya
Enter species: Meerkat
Animal added.

=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 4
ID: 202, Name: Maya, Species: Meerkat
ID: 101, Name: Leo, Species: Lion

=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 3
Enter name to search: Leo
ID: 101, Name: Leo, Species: Lion

=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 2
Enter ID to remove: 202
Animal removed.

=== Sanctuary Animal Tracker ===
1. Add a new animal
2. Remove an animal by ID
3. Search for an animal by name
4. List all animals
5. EXIT
Choose an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct` named `Animal`.  
* **Display function** – All printing of an animal’s details must be performed by a function called `displayAnimal`.  
* **Menu requirement** – The program must present a menu as described above and **must include an explicit EXIT option (option 5)** that terminates the program.  
* **Single‑responsibility functions** – Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the only function that directly prints an animal’s fields is `displayAnimal`.  

*Optional language note*: The problem can be solved in C, C++, or any language that supports structs/classes and manual dynamic memory allocation. The essential constraints remain the same.

---

## Problem 88 - openai/gpt-oss-120b - Iteration 38
# STEP 1: PROBLEM  

## Background  
The city of **Algoria** is preparing for the annual **Treasure Hunt Festival**.  Contest organizers need a simple computer program to keep track of the **magical artifacts** that participants discover during the event.  Each artifact has a unique identifier, a name, and a point value.  Because the list of artifacts can grow and shrink throughout the day, a **singly linked list** is the most appropriate data structure.

You have just finished the lecture on singly linked lists and are asked to write the program that the organizers will run on a laptop at the registration desk.

## Requirements  

Write a C (or C‑like) program that provides the following functionality through a text‑based menu:

1. **Add a new artifact** to the **end** of the list.  
   - Prompt the user for the artifact’s **ID** (integer), **name** (single‑word string, up to 31 characters), and **point value** (integer).  
2. **Remove an artifact** by its ID.  
   - If the ID is not found, display an appropriate message.  
3. **Display all artifacts** in the order they appear in the list, one per line, showing ID, name, and points.  
4. **Search for an artifact** by ID and display its details.  
   - The logic that prints the details of a single artifact **must** be placed in a function named `displayArtifact`.  
5. **Exit** the program.  

The menu must be displayed after each operation until the user chooses to exit.

## Example Input / Output  

```
=== Algoria Treasure Hunt Inventory ===
1) Add artifact
2) Remove artifact
3) List all artifacts
4) Find artifact by ID
5) EXIT
Choose an option: 1
Enter artifact ID: 101
Enter artifact name: GoldenCup
Enter point value: 250
Artifact added.

=== Algoria Treasure Hunt Inventory ===
1) Add artifact
2) Remove artifact
3) List all artifacts
4) Find artifact by ID
5) EXIT
Choose an option: 1
Enter artifact ID: 102
Enter artifact name: SilverSword
Enter point value: 180
Artifact added.

=== Algoria Treasure Hunt Inventory ===
1) Add artifact
2) Remove artifact
3) List all artifacts
4) Find artifact by ID
5) EXIT
Choose an option: 3
Current artifacts:
[101] GoldenCup – 250 points
[102] SilverSword – 180 points

=== Algoria Treasure Hunt Inventory ===
1) Add artifact
2) Remove artifact
3) List all artifacts
4) Find artifact by ID
5) EXIT
Choose an option: 4
Enter artifact ID to search: 102
[102] SilverSword – 180 points

=== Algoria Treasure Hunt Inventory ===
1) Add artifact
2) Remove artifact
3) List all artifacts
4) Find artifact by ID
5) EXIT
Choose an option: 5
Good‑bye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary entity **must** be represented by a `struct` named `Artifact` containing at least the fields `id` (int), `name` (char array of length 32), `points` (int), and a pointer to the next node.  
- **Function Requirement**: The code that prints the details of a single artifact **must** reside in a function with the exact prototype `void displayArtifact(const Artifact *a);`.  
- **Menu Implementation**: The program must present a textual menu as shown above and **must include** an explicit option to **EXIT** the program (option 5 in the example). Selecting this option terminates the program gracefully.  
- **Memory Management**: All dynamically allocated nodes must be freed before program termination.  
- **Single‑File Submission**: The entire solution should be contained in one source file (e.g., `main.c`). Apart from `main`, you may create additional helper functions, but the core list operations (add, remove, search, display) should each be encapsulated in their own functions.  

---  

*Design the program so that a student who has just completed the lecture on singly linked lists can implement it correctly, respecting all constraints.*

---

## Problem 89 - openai/gpt-oss-120b - Iteration 39
# STEP 1: PROBLEM  

**Background**  
The campus bookstore wants a simple console‑based system to keep track of the books that are currently on the shelves. Each book is identified by a unique ISBN, has a title, and a quantity indicating how many copies are available. The store manager has asked you to write a program that stores the books in a **singly linked list** and provides a small menu‑driven interface for common operations.

**Program Requirements**  

1. **Data Representation**  
   * Define a `struct` called `BookNode` that stores:  
     - `char isbn[20]` – the book’s ISBN (no spaces).  
     - `char title[100]` – the book’s title (may contain spaces).  
     - `int quantity` – number of copies on the shelf.  
     - `BookNode *next` – pointer to the next node.  

2. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new book** – Prompt for ISBN, title, and quantity, then insert the new node at the **end** of the list. If a book with the same ISBN already exists, increase its `quantity` by the entered amount instead of adding a new node. |
   | 2 | **Remove a book** – Prompt for an ISBN. If the book exists, delete its node from the list and free the memory. If it does not exist, print “Book not found.” |
   | 3 | **Search for a book** – Prompt for an ISBN and, if found, display its details using a function named `displayBook`. If not found, print “Book not found.” |
   | 4 | **List all books** – Traverse the list and display every book’s details (ISBN, title, quantity) using `displayBook`. If the list is empty, print “No books in inventory.” |
   | 5 | **EXIT** – Terminate the program. *(This option must be present as the explicit way to end the program.)* |

3. **Functional Details**  
   * All input should be read from `stdin`; all output should be written to `stdout`.  
   * The program must **not** leak memory – every allocated node must be freed before the program terminates.  
   * The function `void displayBook(const BookNode *node);` must be responsible for printing a single book in the format:  
     ```
     ISBN: <isbn>, Title: <title>, Quantity: <quantity>
     ```
   * The main menu loop should be implemented in `main()`; all other operations (add, remove, search, list) must be performed in separate helper functions of your choice.

**Example Interaction**  

```
--- Book Inventory Menu ---
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter quantity: 3
Book added.

--- Book Inventory Menu ---
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter quantity: 2
Book already exists; quantity updated.

--- Book Inventory Menu ---
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 4
ISBN: 9780131103627, Title: The C Programming Language, Quantity: 5

--- Book Inventory Menu ---
1. Add a new book
2. Remove a book
3. Search for a book
4. List all books
5. EXIT
Enter choice: 5
Goodbye!
```

### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented by a `struct` named `BookNode`.  
- **Display Function:** The logic for displaying the details of **ONE** specific book must reside in a function called `displayBook`.  
- **Menu Exit Option:** The menu must contain an explicit option (number 5) labeled **EXIT** that terminates the program.  
- **Memory Management:** No memory leaks are allowed; every node created with `malloc`/`new` must be freed before program termination.  
- **Language:** The solution must be written in C (or C++ if you prefer, but the struct and function signatures must match the description above).  

*Write a complete program that satisfies all of the above requirements.*

---

## Problem 90 - openai/gpt-oss-120b - Iteration 40
# STEP 1: PROBLEM  

## Background  
The city’s public transportation department is modernizing its bus‑tracking system. Each bus is identified by a unique integer **BusID** and carries a short textual **RouteName** (e.g., “Downtown‑Airport”). The department wants a simple console program that lets an operator add, remove, and view buses in the order they are reported to the system. Because the order of arrival matters, the operator must store the buses in a **singly linked list**.

## Requirements  
Write a C (or C++) program that implements the bus list with the following capabilities:

1. **Add a bus** – Append a new bus node to the end of the list. The operator supplies the `BusID` (positive integer) and `RouteName` (a single word, max 30 characters).  
2. **Delete a bus** – Remove the first node whose `BusID` matches a value supplied by the operator. If no such bus exists, print an informative message.  
3. **Display all buses** – Traverse the list from head to tail, printing each bus’s `BusID` and `RouteName` on its own line.  
4. **Display a specific bus** – Given a `BusID`, locate that node and print its details using a dedicated function `displayBus`. If the bus is not found, print an appropriate message.  
5. **Count buses** – Show the total number of buses currently stored.  
6. **Exit** – Terminate the program gracefully.

The program should present a text‑based menu that repeatedly prompts the user for one of the actions above until the **Exit** option is chosen.

## Example Interaction  

```
=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 1
Enter BusID: 101
Enter RouteName: DowntownAirport

Bus added successfully.

=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 1
Enter BusID: 202
Enter RouteName: MidtownLoop

Bus added successfully.

=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 3

Current buses:
BusID: 101, RouteName: DowntownAirport
BusID: 202, RouteName: MidtownLoop

=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 4
Enter BusID to display: 202
BusID: 202, RouteName: MidtownLoop

=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 5
Total buses: 2

=== Bus Management System ===
1. Add a bus
2. Delete a bus
3. Display all buses
4. Display a specific bus
5. Count buses
6. Exit
Select an option: 6

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: Use a `struct` named `Bus` to represent each node. The struct must contain at least:
  - `int busID;`
  - `char routeName[31];` (enough space for a 30‑character name plus the terminating null)
  - `struct Bus *next;`
- **Function Requirement**: The logic for printing the details of **one** bus must reside in a function with the exact prototype:
  ```c
  void displayBus(const struct Bus *b);
  ```
- **Program Structure**: Apart from `main()`, you may create **only one additional function** (the required `displayBus`). All other list operations (add, delete, traverse, count) must be implemented directly inside `main()` or as static inline code blocks.
- **Menu**: The program must present a menu as shown in the example, and **option 6 must be the explicit “Exit” command** that ends the program.
- **Memory Management**: Every node allocated with `malloc` (or `new` if using C++) must be freed appropriately when deleted or when the program terminates. No memory leaks are allowed.  

---  

*Deliver a complete, compilable source file that satisfies all the above constraints.*

---

## Problem 91 - openai/gpt-oss-120b - Iteration 41
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its “quick‑checkout” system.  When a patron arrives, the librarian scans the patron’s ID and then repeatedly adds the titles of the books the patron wishes to borrow.  The books are stored in the order they are scanned, and the librarian can at any time:

* view the current list of books,  
* remove the most recently scanned book (e.g., if the patron changes their mind), or  
* clear the entire list when the transaction is finished.

Your task is to implement this “checkout list” as a **singly linked list**.  The program must be menu‑driven so that the librarian can interact with it from the console.

---

## Requirements  

1. **Data Entity**  
   * Define a `struct` (or equivalent) named `BookNode` that stores:  
     - `char title[101]` – the book title (maximum 100 characters, null‑terminated).  
     - `BookNode *next` – pointer to the next node.  

2. **Core Operations (menu options)**  
   * **1 – Add Book** – Prompt the user for a title and insert a new node at the **tail** of the list.  
   * **2 – Remove Last Book** – Delete the node at the tail (if the list is not empty) and display the title that was removed.  
   * **3 – Show All Books** – Traverse the list from head to tail and print each title on its own line, preceded by its position in the list (starting at 1).  
   * **4 – Clear List** – Delete **all** nodes, freeing memory, and report how many books were removed.  
   * **5 – EXIT** – Terminate the program gracefully (see mandatory constraint).  

3. **Helper Function**  
   * Implement a function `void displayBook(const BookNode *node);` that prints a single book title in the format `Title: <title>`.  
   * This function **must** be used by the “Show All Books” and “Remove Last Book” options when they need to display a title.

4. **Memory Management**  
   * Every allocated node must be freed exactly once.  
   * The program must not leak memory, even when the user exits without clearing the list.

5. **User Interaction**  
   * After completing any operation (except EXIT), the menu should be displayed again.  
   * Input errors (e.g., selecting a non‑existent menu number) should be handled with an informative message and a redisplay of the menu.

---

## Example Input / Output  

```
--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 1
Enter book title: The C Programming Language
Book added.

--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 1
Enter book title: Introduction to Algorithms
Book added.

--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 3
1. Title: The C Programming Language
2. Title: Introduction to Algorithms

--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 2
Removed book: Introduction to Algorithms

--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 4
Cleared 1 book(s) from the list.

--- Library Checkout System ---
1) Add Book
2) Remove Last Book
3) Show All Books
4) Clear List
5) EXIT
Select an option: 5
Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct` named `BookNode`.  
* **Display Function** – The function `void displayBook(const BookNode *node);` must contain the logic for printing a single book’s details and must be called wherever a single book title needs to be shown.  
* **Menu Exit** – The menu must include option **5 – EXIT** (or the exact keyword “EXIT”) that terminates the program.  
* **Single‑File Implementation** – All code must reside in a single source file; only `main()` and the required helper functions (`displayBook` and any internal list‑management helpers) are permitted.  
* **No Global Variables** – All list pointers must be managed within `main()` (or passed as parameters); global variables are not allowed.  

---  

*Design your solution to be clear, modular, and memory‑safe. Good luck!*

---

## Problem 92 - openai/gpt-oss-120b - Iteration 42
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple command‑line tool to keep track of the books that are currently on the shelves. Each book is identified by a unique integer **ID**, has a **title**, and a **price** (in dollars). The store clerk will run the program each day, adding new arrivals, removing books that have been sold, and looking up information about specific titles.  

Your task is to implement this tool using a **singly linked list**. The list will store the books in the order they are added (i.e., new books are appended to the tail of the list).

## Program Requirements  

Your program must provide a text‑based menu with the following options:

1. **Add a new book** – Prompt for `ID`, `title`, and `price`. Append the new book to the end of the list. If a book with the same `ID` already exists, display an error and do not insert.
2. **Remove a book by ID** – Prompt for an `ID`. Delete the node containing that `ID`. If the `ID` is not found, display an appropriate message.
3. **Search for a book by title** – Prompt for a `title` (case‑insensitive exact match). If found, display the book’s details using the required `displayBook` function; otherwise, report that the book does not exist.
4. **Display all books** – Traverse the list from head to tail and display each book’s details (one per line) using `displayBook`.
5. **Exit** – Terminate the program. *(The menu must include this option as the explicit way to quit.)*

Additional functional details:

- The list must be **singly linked**; you may not use arrays or library containers (e.g., `std::vector`).
- All input validation (e.g., non‑negative price, unique ID) must be performed.
- After completing any operation (except Exit), the menu should be shown again.

## Example Interaction  

```
=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ID
3. Search for a book by title
4. Display all books
5. Exit
Choose an option: 1

Enter Book ID: 101
Enter Title: Data Structures in C
Enter Price: 59.99
Book added successfully.

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ID
3. Search for a book by title
4. Display all books
5. Exit
Choose an option: 1

Enter Book ID: 102
Enter Title: Algorithms Unlocked
Enter Price: 45.00
Book added successfully.

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ID
3. Search for a book by title
4. Display all books
5. Exit
Choose an option: 4

ID: 101 | Title: Data Structures in C | Price: $59.99
ID: 102 | Title: Algorithms Unlocked   | Price: $45.00

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ID
3. Search for a book by title
4. Display all books
5. Exit
Choose an option: 3

Enter Title to search: algorithms unlocked
ID: 102 | Title: Algorithms Unlocked | Price: $45.00

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ID
3. Search for a book by title
4. Display all books
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: You **must** define a `struct` (or equivalent language construct) named `BookNode` that contains the book’s `ID`, `title`, `price`, and a pointer to the next node.
- **Display Function**: The logic for printing a single book’s details **must** be placed in a function with the exact signature `void displayBook(const BookNode* node);`. All menu options that show a book (search and display‑all) must call this function.
- **Menu Implementation**: The program must present a menu as described above and must include an explicit option to **Exit** (option 5 in the example). Selecting this option ends the program.
- **Single‑File Requirement**: The entire solution should be contained in one source file. Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the core display logic must reside in `displayBook`.
- **No Global Variables**: All list manipulation should be performed via pointers passed to functions; do not use global variables to store the head of the list.  

*These constraints are mandatory; violating any of them will cause the solution to be considered incomplete.*

---

## Problem 93 - openai/gpt-oss-120b - Iteration 43
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑tracking system. Each bus on a route is identified by a unique **bus ID** and reports its **current passenger count** every few minutes. The authority wants a simple console program that stores the buses that are currently active on a given route using a **singly linked list**.  

Your task is to implement this list and provide a small interactive menu so that a user (e.g., a dispatcher) can add, remove, query, and display buses while the program is running.

## Requirements  

Write a C (or C++) program that:

1. **Defines a `struct Bus`** containing at least:  
   * `int id` – the unique bus identifier.  
   * `int passengers` – number of passengers currently on board.  
   * `struct Bus *next` – pointer to the next node in the list.  

2. **Maintains a singly linked list** of all active buses. The list must be kept in the order in which buses are added (i.e., insertion at the tail).

3. **Provides a text‑based menu** with the following options (the user selects a number):  
   1. **Add a bus** – Prompt for `id` and `passengers`, then append a new node to the list. If a bus with the same `id` already exists, display an error and do not add it.  
   2. **Remove a bus** – Prompt for `id`. If a bus with that `id` exists, delete its node and free the memory; otherwise, display “Bus not found.”  
   3. **Search for a bus** – Prompt for `id`. If found, display the bus’s details; otherwise, display “Bus not found.”  
   4. **Display all buses** – Traverse the list and print each bus’s `id` and `passengers` on a separate line. If the list is empty, print “No active buses.”  
   5. **EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

4. **Implements the following helper functions** (you may add more if you wish, but at least these must exist):  
   * `void displayBus(const struct Bus *b);` – prints a single bus’s details in the format `Bus ID: <id>, Passengers: <passengers>`.  
   * `void addBus(struct Bus **head, int id, int passengers);`  
   * `void removeBus(struct Bus **head, int id);`  
   * `struct Bus* findBus(struct Bus *head, int id);`  
   * `void displayAll(const struct Bus *head);`  

5. **Handles all input errors gracefully** (e.g., non‑numeric input for menu choices or IDs) by prompting the user again.

## Example Interaction  

```
--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 1
Enter bus ID: 42
Enter passenger count: 15
Bus added.

--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 1
Enter bus ID: 7
Enter passenger count: 30
Bus added.

--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 4
Bus ID: 42, Passengers: 15
Bus ID: 7, Passengers: 30

--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 3
Enter bus ID to search: 7
Bus ID: 7, Passengers: 30

--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 2
Enter bus ID to remove: 42
Bus removed.

--- Bus Tracking System ---
1. Add a bus
2. Remove a bus
3. Search for a bus
4. Display all buses
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Must use a `struct`** to represent each bus (as described above).  
* The logic for displaying the details of **ONE specific bus** must reside **exclusively** in the function `displayBus`.  
* The program **must provide a menu** and **must include an option numbered 5 (or the keyword “EXIT”) that terminates the program**.  
* All dynamic memory allocated for bus nodes must be freed before the program exits.  
* Only one additional helper function (besides `main`) is **not** allowed; you must implement at least the four functions listed in the requirements.  

Feel free to add any auxiliary functions you need, but respect the constraints above. Good luck!

---

## Problem 94 - openai/gpt-oss-120b - Iteration 44
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  Each book in the collection is identified by a **unique ISBN**, has a **title**, and stores the **number of copies** currently available.  The library wants a simple console application that lets a librarian add new books, remove books, update the copy count, and view the details of a particular book.  Because the inventory can grow and shrink dynamically, the librarian has been instructed to use a **singly linked list** to store the books.

## Requirements  
Write a C (or C++) program that implements the described inventory system using a singly linked list. The program must provide a **menu‑driven interface** with the following options:

1. **Add a new book** – Prompt for ISBN (string without spaces), title (string possibly containing spaces), and initial copy count (non‑negative integer). Insert the new node at the **end** of the list. If a book with the same ISBN already exists, display an error and do not insert.
2. **Remove a book** – Prompt for an ISBN. Locate the node with that ISBN, remove it from the list, and free its memory. If the ISBN is not found, display an appropriate message.
3. **Update copy count** – Prompt for an ISBN and a new copy count. If the book exists, replace its copy count with the new value; otherwise, report that the ISBN was not found.
4. **Display a book’s details** – Prompt for an ISBN and show the ISBN, title, and copy count of that book. If the ISBN does not exist, inform the user.
5. **List all books** – Traverse the list and print the details of every stored book in the order they were added.
6. **EXIT** – Terminate the program gracefully, releasing all allocated memory.

The program should continue to display the menu after completing any operation until the user selects **EXIT**.

## Example Input / Output  

```
=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Update copy count
4) Display a book’s details
5) List all books
6) EXIT
Choose an option: 1
Enter ISBN: 978-0131103627
Enter title: The C Programming Language
Enter copy count: 4
Book added successfully.

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Update copy count
4) Display a book’s details
5) List all books
6) EXIT
Choose an option: 1
Enter ISBN: 978-0201616224
Enter title: The Pragmatic Programmer
Enter copy count: 2
Book added successfully.

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Update copy count
4) Display a book’s details
5) List all books
6) EXIT
Choose an option: 5

Current inventory:
ISBN: 978-0131103627 | Title: The C Programming Language | Copies: 4
ISBN: 978-0201616224 | Title: The Pragmatic Programmer   | Copies: 2

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Update copy count
4) Display a book’s details
5) List all books
6) EXIT
Choose an option: 4
Enter ISBN to display: 978-0201616224
ISBN: 978-0201616224
Title: The Pragmatic Programmer
Copies: 2

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Update copy count
4) Display a book’s details
5) List all books
6) EXIT
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary data entity (a book) **must be represented with a `struct`** named `BookNode` (or equivalent) that contains at least the fields `isbn`, `title`, `copies`, and a pointer to the next node.  
* **Function Requirements** – The logic for displaying the details of **ONE specific book** (requirement #4) **must be placed in a function called `displayBook`**. This function should accept a pointer to the node to be displayed (or the ISBN to locate it) and handle all output formatting.  
* **Modular Design** – Apart from `main()`, the solution must contain **no more than three additional functions** (e.g., `addBook`, `removeBook`, `updateCopies`, `displayBook`, `listAll`). Any extra helper functions are not permitted.  
* **Menu Exit** – The menu must include an explicit option labeled **`6) EXIT`** (or the keyword `EXIT`) that terminates the program. Selecting this option must free all dynamically allocated memory before exiting.  

*Optional (for extra credit):*  
- Ensure that the program does not suffer from memory leaks (use tools such as Valgrind to verify).  
- Validate that the copy count entered is a non‑negative integer; otherwise, prompt the user again.  

---

## Problem 95 - openai/gpt-oss-120b - Iteration 45
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  The library wants a simple console‑based program that can store information about each book and allow the librarian to perform basic operations while the program is running.  The librarian has just been introduced to **singly linked lists**, so the solution must use a linked list to keep the collection of books in memory.

## Requirements  
Write a C (or C++) program that implements a **singly linked list** of books.  Each book record must contain the following fields:  

1. **ISBN** – a string of up to 13 characters (no spaces).  
2. **Title** – a string of up to 50 characters (may contain spaces).  
3. **Author** – a string of up to 30 characters (may contain spaces).  
4. **Year** – an integer (e.g., 2023).  

The program must present a text‑based menu that allows the user to:

1. **Add a new book** – insert the new node at the **end** of the list.  
2. **Delete a book by ISBN** – remove the first node whose ISBN matches the supplied value.  
3. **Search for a book by ISBN** – locate the node and display its details.  
4. **Display all books** – traverse the list and print every stored book in the order they were added.  
5. **Exit** – terminate the program gracefully.  

All input is read from `stdin`; all output is written to `stdout`.  The program should continue to display the menu after each operation until the user selects the Exit option.

## Example  

```
=== Library Book Manager ===
1) Add Book
2) Delete Book
3) Search Book
4) Display All Books
5) Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Year: 1988
Book added successfully!

=== Library Book Manager ===
1) Add Book
2) Delete Book
3) Search Book
4) Display All Books
5) Exit
Choose an option: 4
--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Year: 1988
--- End of List ---

=== Library Book Manager ===
1) Add Book
2) Delete Book
3) Search Book
4) Display All Books
5) Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary data entity (a book) **must be defined using a `struct`** (or `class` with public members if using C++).  
* **Display Function** – The logic for displaying the details of **ONE specific book** (used in the Search operation) **must be placed in a function named `displayBook`** that takes a pointer/reference to a book node as its only parameter.  
* **Menu Requirement** – The menu must include an explicit option to **EXIT the program** (option `5` in the example). Selecting this option must cause the program to terminate without memory leaks.  
* **Memory Management** – All dynamically allocated nodes must be freed appropriately when they are removed or when the program exits.  
* **Single‑File Implementation** – The entire solution should be contained in one source file; only `main` and the required helper functions (`displayBook`, and any others you create) are permitted.  

Your task is to design and implement this program following the specifications above.

---

## Problem 96 - openai/gpt-oss-120b - Iteration 46
# STEP 1: PROBLEM  

## Background  
The city’s **Urban Wildlife Rescue** maintains a simple database of rescued animals that are waiting to be adopted.  Because the number of arrivals and adoptions changes every day, the staff wants a lightweight program that can **dynamically add** new animals, **remove** the animal that has been in the shelter the longest, and **display** information about any single animal on demand.  

You have just learned how to implement a **singly linked list** in C (or C‑like language).  Write a console program that models the rescue’s animal list using a singly linked list.

## Requirements  

1. **Data Representation**  
   - Each animal is represented by a `struct` (or equivalent) containing:  
     - `int id` – a unique identifier (positive integer).  
     - `char name[30]` – the animal’s name (no spaces).  
     - `char species[20]` – e.g., “fox”, “raccoon”, “eagle”.  
     - `int age` – age in years.  

2. **Supported Operations (menu‑driven)**  
   - **1. Add Animal** – Prompt the user for the fields above and insert the new node at the **tail** of the list (i.e., the newest arrival is at the end).  
   - **2. Adopt Animal** – Remove the **head** node (the animal that has been in the shelter the longest) and display its details before deletion. If the list is empty, print an appropriate message.  
   - **3. Display Animal by ID** – Ask for an `id`, search the list, and display that animal’s details. If not found, inform the user.  
   - **4. List All Animals** – Traverse the list from head to tail and print each animal’s information on its own line. If the list is empty, state that there are no animals.  
   - **5. EXIT** – Terminate the program.  

3. **User Interaction**  
   - After completing any operation (except EXIT), the menu should be shown again.  
   - Input should be read from standard input; output written to standard output.  

4. **Memory Management**  
   - Dynamically allocate memory for each new node.  
   - Free memory when a node is removed or when the program exits.  

## Example Input / Output  

```
--- Urban Wildlife Rescue ---
1. Add Animal
2. Adopt Animal
3. Display Animal by ID
4. List All Animals
5. EXIT
Choose an option: 1
Enter ID: 101
Enter name: Bella
Enter species: fox
Enter age: 3
Animal added.

--- Urban Wildlife Rescue ---
1. Add Animal
2. Adopt Animal
3. Display Animal by ID
4. List All Animals
5. EXIT
Choose an option: 1
Enter ID: 102
Enter name: Rocky
Enter species: raccoon
Enter age: 2
Animal added.

--- Urban Wildlife Rescue ---
1. Add Animal
2. Adopt Animal
3. Display Animal by ID
4. List All Animals
5. EXIT
Choose an option: 4
ID: 101, Name: Bella, Species: fox, Age: 3
ID: 102, Name: Rocky, Species: raccoon, Age: 2

--- Urban Wildlife Rescue ---
1. Add Animal
2. Adopt Animal
3. Display Animal by ID
4. List All Animals
5. EXIT
Choose an option: 2
Adopted animal:
ID: 101, Name: Bella, Species: fox, Age: 3

--- Urban Wildlife Rescue ---
1. Add Animal
2. Adopt Animal
3. Display Animal by ID
4. List All Animals
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be defined as a `struct` named `AnimalNode` (or equivalent) that contains the animal fields **and** a pointer to the next node.  
- **Display Function:** The logic for printing the details of **one specific animal** (used in options 2 and 3) must reside in a function called `displayAnimal(const AnimalNode *node)`.  
- **Menu Implementation:** The program must present a textual menu as described above and **must include a specific menu option to EXIT the program (option 5)**.  
- **Single‑purpose Helper Functions:** Apart from `main()`, you may create additional helper functions (e.g., `addAnimal`, `adoptAnimal`, `findAnimal`, `listAll`, `displayAnimal`). No global variables other than the head pointer are allowed.  

*Your solution should compile without warnings and behave exactly as specified.*

---

## Problem 97 - openai/gpt-oss-120b - Iteration 47
# STEP 1: PROBLEM  

## Background  
The ancient library of **Algoria** stores its scrolls in a single‑file chain of wooden boxes. Each box knows only the box that follows it; there is no backward link. The librarian wants a simple console program to manage this chain: adding new scrolls, removing them, and inspecting the contents of any box.  

You have just learned how to implement a **singly linked list** in C (or C‑like language) using `struct`s and pointer manipulation. Your task is to write a program that models the library’s chain of boxes.

## Requirements  

Your program must support the following operations, presented to the user through a text menu:

1. **Insert a new box at the end of the chain**  
   - Prompt for the scroll’s *title* (a string without spaces, max 30 characters) and its *page count* (positive integer).  
   - Allocate a new node and attach it as the last element.

2. **Delete the first box that contains a scroll with a given title**  
   - Prompt for the title to delete.  
   - If the title is found, remove that node and free its memory; otherwise report “Not found”.

3. **Display the details of a specific box**  
   - Prompt for a title.  
   - Locate the first node whose title matches and call a function `displayEntity` to print its contents in the format:  
     `Title: <title>, Pages: <pages>`  
   - If the title does not exist, print “Not found”.

4. **Print the entire chain**  
   - Starting from the first box, print each node on its own line using the same format as above.

5. **Exit the program**  
   - Selecting this option terminates the program gracefully.

The menu must be displayed after each operation (except after exiting). All input and output should be done via `stdin`/`stdout`.

## Example Input / Output  

```
--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 1
Enter title: TheHobbit
Enter pages: 310
Box inserted.

--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 1
Enter title: Dune
Enter pages: 412
Box inserted.

--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 4
Title: TheHobbit, Pages: 310
Title: Dune, Pages: 412

--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 3
Enter title to display: Dune
Title: Dune, Pages: 412

--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 2
Enter title to delete: TheHobbit
Box deleted.

--- Algoria Library Menu ---
1) Insert box
2) Delete box by title
3) Display box by title
4) Print all boxes
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must** be represented with a `struct` named `Box` (or equivalent) containing at least a `char title[31]`, an `int pages`, and a pointer to the next node.  
- The logic for displaying the details of **ONE specific entity** must reside in a function exactly named `displayEntity`. Its prototype should be:  
  ```c
  void displayEntity(const Box *node);
  ```  
- Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, printing the list), but the program must **not** contain more than **five** user‑defined functions total (including `displayEntity`).  
- All dynamic memory allocations must be checked for success; if `malloc` fails, print “Memory allocation error” and exit.  
- The menu **must** include a distinct option to **EXIT** the program (as shown in the example, option 5). Selecting this option should end the program without memory leaks.  

*Write clean, well‑commented code that follows these constraints.*

---

## Problem 98 - openai/gpt-oss-120b - Iteration 48
# STEP 1: PROBLEM  

## Background  
The campus **Student Activities Office** maintains a simple digital register of club events.  
Each event is identified by a unique **Event ID** (integer), has a **title** (string, up to 30 characters), and a **date** (string in the form `YYYY‑MM‑DD`).  
Because events are added and removed frequently, the office has decided to store them in a **singly linked list** that preserves the order in which events are entered (i.e., new events are appended to the tail of the list).

You are asked to write a small console program that lets a user manage this list through a menu‑driven interface.

## Requirements  
Your program must provide the following functionality:

1. **Add a new event** – Prompt the user for Event ID, title, and date, then insert the event at the end of the list.  
2. **Remove an event by ID** – Prompt for an Event ID and delete the first node whose ID matches. If the ID does not exist, display an appropriate message.  
3. **Search for an event by ID** – Prompt for an Event ID and display the details of the matching event. If not found, inform the user.  
4. **Display all events** – Traverse the list from head to tail and print each event’s ID, title, and date on a separate line.  
5. **Exit** – Terminate the program gracefully.

All interactions are performed through a text menu displayed after each operation.

## Example Input / Output  

```
--- Student Activities Event Manager ---
1. Add Event
2. Remove Event
3. Search Event
4. List All Events
5. Exit
Choose an option: 1

Enter Event ID: 101
Enter Title: Hackathon
Enter Date (YYYY-MM-DD): 2024-03-15
Event added.

--- Student Activities Event Manager ---
1. Add Event
2. Remove Event
3. Search Event
4. List All Events
5. Exit
Choose an option: 1

Enter Event ID: 102
Enter Title: Poetry Night
Enter Date (YYYY-MM-DD): 2024-04-02
Event added.

--- Student Activities Event Manager ---
1. Add Event
2. Remove Event
3. Search Event
4. List All Events
5. Exit
Choose an option: 4

Event ID: 101 | Title: Hackathon   | Date: 2024-03-15
Event ID: 102 | Title: Poetry Night| Date: 2024-04-02

--- Student Activities Event Manager ---
1. Add Event
2. Remove Event
3. Search Event
4. List All Events
5. Exit
Choose an option: 3

Enter Event ID to search: 102
Event ID: 102 | Title: Poetry Night | Date: 2024-04-02

--- Student Activities Event Manager ---
1. Add Event
2. Remove Event
3. Search Event
4. List All Events
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (an event) must be represented with a `struct` (or equivalent language‑specific record) containing at least the three fields: `id` (int), `title` (char array / string), and `date` (char array / string).  

2. **Linked List Node** – The linked‑list node must contain the event `struct` and a pointer to the next node.  

3. **Display Function** – The logic for showing the details of **one specific event** (used by the *Search* operation) must reside in a function named `displayEvent`. Its signature should accept a pointer/reference to an event and print the formatted line shown in the example.  

4. **Menu Implementation** – The menu must be presented in a loop and must include a distinct option to **EXIT** the program (option number 5 in the example). Selecting this option ends the loop and terminates the program.  

5. **Memory Management** – If the chosen language requires explicit memory handling (e.g., C/C++), you must allocate nodes dynamically when adding events and free the memory of removed nodes (and all remaining nodes before program termination).  

6. **Single‑File Solution** – All code must reside in a single source file. Apart from `main`, you may create additional helper functions, but the total number of user‑defined functions (including `displayEvent`) must not exceed **six**.  

7. **No Standard Library Containers** – You may **not** use built‑in list, vector, or similar container classes; the linked list must be implemented manually.  

Follow these constraints closely; they are part of the grading rubric.

---

## Problem 99 - openai/gpt-oss-120b - Iteration 49
# STEP 1: PROBLEM  

**Background**  
The campus library wants a simple command‑line tool to keep track of the books that are currently on loan. Each book record contains a unique identifier, the title, and the name of the borrower. The library staff will use this tool to add new loans, remove returned books, and view the list of outstanding loans.  

Your task is to implement this tool using a **singly linked list**. The list should store the loan records in the order they are entered (i.e., new records are appended to the tail of the list).  

---

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Book` (or equivalent in your language) that stores:  
     - `int id` – unique loan identifier  
     - `char title[101]` – book title (max 100 characters)  
     - `char borrower[51]` – borrower’s name (max 50 characters)  
     - `struct Book *next` – pointer to the next node  

2. **Menu‑driven program** (the program must present a text menu and loop until the user chooses to exit)  
   * **1. Add a new loan** – Prompt for `id`, `title`, and `borrower`; create a new node and append it to the tail of the list. If a node with the same `id` already exists, print an error and do not insert.  
   * **2. Return a book** – Prompt for `id`; locate the node with that `id` and remove it from the list, freeing its memory. If the `id` is not found, print an appropriate message.  
   * **3. Display all outstanding loans** – Traverse the list from head to tail and print each record on its own line in the format:  
     `ID: <id>, Title: "<title>", Borrower: <borrower>`  
   * **4. Display a specific loan** – Prompt for `id`; locate the node and display its details using a dedicated function called `displayBook`. If not found, inform the user.  
   * **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **Input validation** – The program should handle non‑numeric menu choices gracefully and re‑prompt the user.  

4. **Memory management** – All dynamically allocated nodes must be freed before the program ends.  

---

## Example Interaction  

```
=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Display all outstanding loans
4. Display a specific loan
5. EXIT
Choose an option: 1

Enter loan ID: 101
Enter book title: The C Programming Language
Enter borrower name: Alice
Loan added successfully.

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Display all outstanding loans
4. Display a specific loan
5. EXIT
Choose an option: 1

Enter loan ID: 102
Enter book title: Introduction to Algorithms
Enter borrower name: Bob
Loan added successfully.

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Display all outstanding loans
4. Display a specific loan
5. EXIT
Choose an option: 3

ID: 101, Title: "The C Programming Language", Borrower: Alice
ID: 102, Title: "Introduction to Algorithms", Borrower: Bob

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Display all outstanding loans
4. Display a specific loan
5. EXIT
Choose an option: 4

Enter loan ID to view: 102
ID: 102, Title: "Introduction to Algorithms", Borrower: Bob

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Display all outstanding loans
4. Display a specific loan
5. EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

* **Struct requirement** – The primary data entity must be represented by a `struct` named `Book`.  
* **Display function** – The logic for showing the details of ONE specific loan must reside in a function with the exact prototype:  
  ```c
  void displayBook(const Book *b);
  ```  
* **Menu exit** – The menu must contain an option labelled **5. EXIT** (or the word “EXIT”) that terminates the program.  
* **Single‑function rule** – Apart from `main()` you may create as many helper functions as needed, but the core list operations (insert, delete, traverse) must each be encapsulated in their own separate functions (e.g., `addLoan`, `removeLoan`, `printAll`, `displayBook`).  
* **No global variables** – All list pointers must be passed to functions via parameters; do not use global variables to store the head or tail of the list.  

---  

Implement the program according to the above specifications.

---

## Problem 100 - openai/gpt-oss-120b - Iteration 50
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants to keep a simple in‑memory record of the **first‑edition textbooks** it receives each day. Each textbook is identified by a unique ISBN, has a title, and a price. Because the store receives books continuously throughout the day, the list of books must support **insertion at the end** (the order of arrival matters) and **removal of the first book** when it is sold.  

Your task is to write a console program that maintains this list using a **singly linked list**. The program will present a small menu that allows the user (the store clerk) to add new books, sell the oldest book, view the whole inventory, and look up a single book by its ISBN.

## Requirements  

1. **Data representation**  
   * Define a `struct` called `Book` that stores:  
     - `char isbn[14]` (13‑digit ISBN plus terminating null)  
     - `char title[101]` (up to 100 characters)  
     - `double price`  

2. **Linked‑list node**  
   * Define a `struct` called `Node` that contains a `Book` and a pointer to the next node.

3. **Menu‑driven program** (displayed repeatedly until the user chooses to exit)  
   * **1. Add a new textbook** – Prompt for ISBN, title, and price, then append a new node at the **tail** of the list.  
   * **2. Sell the oldest textbook** – Remove the node at the **head** of the list and display its details. If the list is empty, print an appropriate message.  
   * **3. Show all textbooks** – Traverse the list from head to tail, printing each book’s ISBN, title, and price on its own line. If the list is empty, indicate that the inventory is empty.  
   * **4. Find a textbook by ISBN** – Prompt for an ISBN, search the list, and if found call a function `displayBook` (see Constraint) to show its details; otherwise report “Book not found”.  
   * **5. EXIT** – Terminate the program.  

4. **Input validation** – The program should not crash on malformed input; if a numeric value cannot be read, ask the user to re‑enter it.

5. **Memory management** – All dynamically allocated nodes must be freed before the program exits.

## Example Interaction  

```
=== Bookstore Inventory Menu ===
1. Add a new textbook
2. Sell the oldest textbook
3. Show all textbooks
4. Find a textbook by ISBN
5. EXIT
Enter choice: 1
Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter price: 59.99
Textbook added.

=== Bookstore Inventory Menu ===
1. Add a new textbook
2. Sell the oldest textbook
3. Show all textbooks
4. Find a textbook by ISBN
5. EXIT
Enter choice: 1
Enter ISBN (13 digits): 9780262033848
Enter title: Introduction to Algorithms
Enter price: 89.50
Textbook added.

=== Bookstore Inventory Menu ===
1. Add a new textbook
2. Sell the oldest textbook
3. Show all textbooks
4. Find a textbook by ISBN
5. EXIT
Enter choice: 3
Inventory:
ISBN: 9780131103627 | Title: The C Programming Language | Price: $59.99
ISBN: 9780262033848 | Title: Introduction to Algorithms | Price: $89.50

=== Bookstore Inventory Menu ===
1. Add a new textbook
2. Sell the oldest textbook
3. Show all textbooks
4. Find a textbook by ISBN
5. EXIT
Enter choice: 2
Sold textbook:
ISBN: 9780131103627 | Title: The C Programming Language | Price: $59.99

=== Bookstore Inventory Menu ===
1. Add a new textbook
2. Sell the oldest textbook
3. Show all textbooks
4. Find a textbook by ISBN
5. EXIT
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct` named `Book`.  
* **Display function** – The logic for displaying the details of **ONE** specific book must reside in a function with the exact prototype:  
  ```c
  void displayBook(const Book *b);
  ```  
* **Single‑purpose helper functions** – Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the program must contain **no more than three** user‑defined functions besides `main` and `displayBook`.  
* **Menu requirement** – The menu must include an explicit option **5. EXIT** that terminates the program, as shown in the example.  

---  

Implement the program in C (or C++) following the above specifications. The solution will be evaluated on correctness, adherence to the constraints, proper memory handling, and code clarity.

---

