# Problem Batch Preview: Pointers and Pointer Arithmetic
**Batch Number:** 1 | **Total Problems:** 100

---

## Problem 1 - moonshotai/kimi-k2-instruct-0905 - Iteration 61
# STEP 1: PROBLEM

## Context
A small astronomy club keeps track of the altitudes (in degrees above the horizon) of five bright stars that are visible tonight.  
Because the sky is constantly changing, the club wants to update each altitude by adding the same “drift” value (positive or negative) to every star.  
They ask you to write a tiny C program that lets them:
1. Enter the five altitudes.
2. Enter the drift value.
3. Display the updated altitudes in the same order.

## Requirements
1. Store the five altitudes in an array of double.
2. Read the five altitudes from standard input (space-separated on one line).
3. Read one double that represents the drift.
4. Add the drift to every altitude using pointer arithmetic—no array-subscript syntax (i.e. no `a[i]`) inside the updating loop.
5. Print the updated altitudes on one line, separated by a single space and with two digits after the decimal point.
6. Do all updating in a single pass through the array.

## Simple Example
Input
```
30.5 45.0 10.25 90.0 5.75
-2.5
```

Output
```
28.00 42.50 7.75 87.50 3.25
```

### CONSTRAINTS
- You must define and use a `struct` named `StarData` that contains exactly one member: a fixed-length array of five `double`s called `alt`.
- All updating logic must be done in a function `void applyDrift(struct StarData *data, double drift)`.  
- No other functions besides `main` and `applyDrift` may be defined.

---

## Problem 2 - moonshotai/kimi-k2-instruct-0905 - Iteration 62
# STEP 1: PROBLEM

## Background
A small library keeps the titles of its books in one long, contiguous `char` array (a “shelf”).  
Each title ends with the newline character `\n`.  
A second array of pointers (`char *index[]`) points to the beginning of every title.  
When a book is borrowed, its entry is removed from the index by shifting the later pointers one position to the left; the characters of the title remain physically on the shelf (we are only updating the index).

## Task
Write a program that:

1. Reads a single line containing an integer `n` (`1 ≤ n ≤ 100`) – the number of books initially on the shelf.
2. Reads the next `n` lines; each line is a book title (at most 80 characters, including the terminating `\n`).
3. Stores all titles **contiguously** in one `char shelf[8192]` buffer.
4. Builds an index of pointers so that `index[i]` points to the first character of the `i`-th title.
5. Reads an integer `m` (`0 ≤ m ≤ n`) – how many books will be borrowed.
6. For each of the next `m` lines:
   - Read an integer `k` (`0 ≤ k < current number of books`) – the position of the book to borrow.
   - Remove the `k`-th entry from the index by shifting the remaining pointers left.
7. Prints the remaining titles in their **current** order, one per line, exactly as they appear on the shelf.

## Simple Example
Input
```
3
The C Programming Language
Introduction to Algorithms
Computer Organization and Design
2
0
1
```
Output
```
Introduction to Algorithms
```

## Explanation
After borrowing the book at position 0 (`The C Programming Language`), the index becomes  
`index[0] → "Introduction to Algorithms"`  
`index[1] → "Computer Organization and Design"`  
Borrowing position 1 removes the second title, leaving only the first one in the index.

### CONSTRAINTS
- You **must** store the titles in a single `char` array (`shelf`) and manipulate only the index of pointers; no second copy of the strings is allowed.  
- The logic that **prints one title** given a `char *` to its first character must be implemented in a function  
  `void displayTitle(const char *title);`  
- Apart from `main`, `displayTitle` is the **only** function you may define.

---

## Problem 3 - moonshotai/kimi-k2-instruct-0905 - Iteration 63
# STEP 1: PROBLEM

## Background Story
The campus library has just switched to a tiny “key-tag” system: every book’s 13-digit ISBN is stored in a single 64-byte NFC tag that also keeps the number of available copies.  
The librarian plugs the tag into your Arduino-like terminal, which presents the memory as a plain byte array.  
Your task is to write a micro-service (in C) that walks through that array with pointer arithmetic, decodes the ISBNs, and tells the librarian which book has the most copies on the shelf.

## Functional Requirements
1. The memory region is given as a `uint8_t*` called `tag` and its byte-length `n` is always a multiple of 8.
2. Every 8-byte block is laid out as:
   - Bytes 0-6: printable ASCII characters of the ISBN (13 digits are packed left-justified, right-padded with spaces, **no null-terminator**).
   - Byte 7: an unsigned count of available copies (0-255).
3. Scan the entire region **using only pointer arithmetic** (no array sub-scripting like `tag[i]`).
4. Return a pointer to the first byte of the block that currently holds the largest stock.  
   If several blocks tie for the same maximum, return the pointer to the **first** one encountered.
5. Provide a small `main()` that:
   - hard-codes one tag image,
   - calls your function,
   - prints the winning ISBN and its stock count.

## Example
Input (hard-coded in `main`):  
```
uint8_t tag[] = {
    '9','7','8','0','1','3','4','5',   // ISBN "9780134 ", 5 copies
    '9','7','8','0','1','3','5','9',   // ISBN "9780135 ", 9 copies
    '9','7','8','0','1','3','6','9'    // ISBN "9780136 ", 9 copies
};
```

Output:
```
Most stocked: ISBN 9780135, copies 9
```

### CONSTRAINTS
- You must define a `struct Book` that contains exactly two members:  
  `char isbn[7];`  // not null-terminated  
  `uint8_t copies;`
- The only additional function besides `main()` must be:  
  `uint8_t* mostStocked(uint8_t *tag, size_t n);`  
  All decoding and pointer arithmetic belongs inside this function.
- Array indexing (`[]`) is forbidden inside `mostStocked`; use pure pointer arithmetic.
- Menu is **not** required; therefore the EXIT rule is waived.

---

## Problem 4 - moonshotai/kimi-k2-instruct-0905 - Iteration 64
# STEP 1: PROBLEM

**Background Story**  
You are helping a small-town librarian digitize the card-catalog.  
Each book is stored in memory as a continuous block of 3 unsigned integers:  
`id`, `year`, `timesBorrowed`.  
All books sit back-to-back in one big array.  
Your job is to write a tiny tool that walks through that array with pointer arithmetic (no array sub-scripting) and reports the required information.

**Functional Requirements**  
1. Read from stdin an initial sequence of triplets `id year timesBorrowed` until the triplet `0 0 0` is entered.  
2. Store the triplets consecutively in an `unsigned int` array.  
3. After the input ends, read one extra integer `K` (the librarian’s query).  
4. Using only pointer arithmetic (never `array[i]`) implement:  
   - A function `unsigned int* mostPopular(unsigned int* start, unsigned int* end)`  
     that returns the address of the book with the largest `timesBorrowed` value.  
   - A function `void displayBook(const unsigned int* p)`  
     that prints the three fields of the book pointed to by `p` in the format  
     `id year loans` separated by single spaces and followed by newline.  
5. In `main()` print the most popular book by calling the two functions above.  
6. If several books share the same maximum `timesBorrowed`, return the first one encountered.

**Simple Example**  
Input  
```
101 1977 34
102 2001 12
103 1999 34
0 0 0
```
Output  
```
101 1977 34
```

### CONSTRAINTS  
- You must define `struct Book { unsigned int id, year, timesBorrowed; };` and store the data as an array of this struct (not as a flat `unsigned int` array).  
- The only additional function you may write besides `main()` is the pair `mostPopular` and `displayBook` (two functions total).  
- Pointer arithmetic must be used instead of array indexing when walking through the collection inside `mostPopular`.

---

## Problem 5 - moonshotai/kimi-k2-instruct-0905 - Iteration 65
# STEP 1: PROBLEM

## Background
You are helping the campus radio station automate its tiny vinyl-record library.  
Each record is stored in a single contiguous block of memory that is treated as an array of 30-second “sides.”  
A pointer to the first side of a record is passed around the studio, and DJs navigate the disk by moving that pointer forward or backward with classic pointer arithmetic only—no array indexing allowed.

## Requirements
1. Represent one vinyl record as a dynamically allocated array of `n` 30-second sides (each side is a C-string containing the song title on that side).  
2. Provide a function  
   `void rotate(char **ptr, int steps, int n)`  
   that moves the pointer `ptr` `steps` positions forward (positive steps) or backward (negative steps).  
   - After rotation, `*ptr` must still point somewhere inside the original block; if the requested rotation would move it outside, “wrap around” (circular buffer style).  
   - The function must perform the movement using pointer arithmetic only (`*ptr + k` or `*ptr - k`); array-subscript notation is forbidden inside `rotate`.  
3. In `main()`, read:  
   - an integer `n` (number of sides, 1 ≤ n ≤ 100),  
   - `n` song titles (each ≤ 80 chars, newline-terminated),  
   - an integer `q` (number of DJ commands, 1 ≤ q ≤ 50),  
   - `q` commands: each command is a single integer `s` (−1000 ≤ s ≤ 1000) that tells you how many 30-second steps to rotate.  
4. After every command, print the title currently pointed to by the rotated pointer.

## Example
Input  
```
4
Here Comes The Sun
Something
Octopus's Garden
Come Together
3
1
-2
5
```

Output  
```
Something
Octopus's Garden
Here Comes The Sun
```

Explanation  
- Start pointing at “Here Comes The Sun.”  
- +1 → “Something”  
- −2 → “Octopus’s Garden”  
- +5 wraps twice → “Here Comes The Sun” again

### CONSTRAINTS
- You must define `struct Record { char **sides; int n; };` to represent the vinyl.  
- The only functions allowed are `main` and `rotate`; no other helper functions.  
- Inside `rotate`, pointer arithmetic is mandatory; array indexing is prohibited.

---

## Problem 6 - moonshotai/kimi-k2-instruct-0905 - Iteration 66
# STEP 1: PROBLEM

## Background Story
You are helping the campus radio station “WOLF-FM” catalogue its vinyl records.  
Each 12-inch LP is stored flat in a long, contiguous shelf that behaves like a giant array.  
The station intern has measured the offset (in centimetres) from the start of the shelf to the first groove of every record.  
Your task is to write a tiny “record locator” that uses pointer arithmetic to jump straight to the requested album and display its details.

## Functional Requirements
1. Store up to 100 records.
2. Each record has: catalog number (int), artist name (≤30 chars), album title (≤30 chars), and offset (double, cm from shelf start).
3. Provide the following menu loop:
   1) Add a new record  
   2) List all records (offset ascending)  
   3) Find a record by catalog number  
   4) Exit  
4. Option 1 must refuse to add if the shelf is full.  
5. Option 3 must use pointer arithmetic (not array indexing) to scan the contiguous block and return the first matching record or “not found”.

## Simple Example Run (user input after ‘>’)
```
WOLF-FM Record Locator
1) Add  2) List  3) Find  4) Exit
> 1
Catalog #: 2101
Artist: Fleetwood Mac
Album: Rumours
Offset (cm): 42.5
Added!

1) Add  2) List  3) Find  4) Exit
> 3
Search catalog #: 2101
Found at offset 42.50 cm: Fleetwood Mac - Rumours

1) Add  2) List  3) Find  4) Exit
> 4
Good-bye!
```

### CONSTRAINTS
- Must use a struct to represent a record.  
- All shelf traversal (list & find) must be done with pointer arithmetic; no `[]` operator allowed outside of `main()`.  
- Logic to display one record must live in a function called `displayRecord`.  
- Only one additional function besides `main()` is permitted.

---

## Problem 7 - moonshotai/kimi-k2-instruct-0905 - Iteration 67
# STEP 1: PROBLEM

## Context
A small pet shelter keeps all of its animals in one long row of cages.  
Each cage is represented by a structure that stores the pet’s name (≤19 characters) and its age in months.  
The shelter manager wants a quick way to print the list of pets in reverse order (from the last cage back to the first) without ever moving the pets or allocating extra arrays—only using pointer arithmetic.

## Requirements
1. Write a program that:
   - Reads an integer `n` (1 ≤ n ≤ 50) followed by `n` pairs of lines:  
     – pet name (single-word, no spaces)  
     – age in months (positive integer)
   - Stores the data in a statically-allocated array of `struct Pet`.
   - Uses pointer arithmetic (no array subscripting) to traverse the array backwards.
   - Prints the pets in reverse order, one per line, in the format:  
     `<name> is <age> months old.`
2. The program must terminate gracefully after printing the list.

## Example
Input
```
3
Luna
8
Milo
12
Nala
5
```
Output
```
Nala is 5 months old.
Milo is 12 months old.
Luna is 8 months old.
```

### CONSTRAINTS
- You must define and use a `struct Pet` to represent each animal.
- The logic that prints one pet must be placed in a function `void displayPet(const struct Pet *p)` that receives a pointer to the pet.
- Inside `displayPet`, you may NOT use array indexing; you must use the pointer `p` to access members.

---

## Problem 8 - moonshotai/kimi-k2-instruct-0905 - Iteration 68
# STEP 1: PROBLEM

**Background Story**  
While cleaning the attic you discover an old “digital treasure‐chest”: a chunk of memory that used to belong to a retro game.  
The chest contains a long tape of 64 consecutive integers (representing jewels) and a set of “magic keys” that are just offsets from the start of the tape.  
Your task is to write a tiny explorer that walks through that tape with pointer arithmetic, finds the jewel pointed at by each key, and finally returns the *sum of all keys that point to positive jewels*.

**Precise Requirements**  
1. Inside `main`, reserve a contiguous block of 64 `int`s on the stack (the tape).  
2. Read 64 space-separated integers from standard input into that block, using pointer arithmetic only (`*(base+i)` or `*ptr++` style—no array subscripting).  
3. Read an integer `k` (1 ≤ k ≤ 32) followed by `k` magic keys.  
   Each key is an integer offset `o` such that `0 ≤ o < 64`.  
4. Compute the sum of all keys whose corresponding jewel (value at `*(tape + key)`) is strictly positive.  
5. Print that sum on its own line.

**Simple Example**  
Input  
```
1 2 -3 4 5 6 -7 8 9 -10 11 12 -13 14 15 16 -17 18 19 20 -21 22 23 24 -25 26 27 28 -29 30 31 32 -33 34 35 36 -37 38 39 40 -41 42 43 44 -45 46 47 48 -49 50 51 52 -53 54 55 56 -57 58 59 60 -61 62 63
3
0 3 5
```
Output  
```
8
```
Explanation: keys 0, 3, 5 point to values 1, 4, 6; all are positive → sum = 0+3+5 = 8.

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.

---

## Problem 9 - moonshotai/kimi-k2-instruct-0905 - Iteration 69
# STEP 1: PROBLEM

## Context
A small library keeps a compact record of its books in memory as a single chunk.  
Each book is represented by its (unique) ISBN, the number of pages, and the shelf row it sits on.  
The librarian wants a command-line tool that can:

1. Add a run of consecutive books (the data are already in memory right after the current collection).  
2. Display every stored book in ascending order of memory address (i.e. the order in which they were added).  
3. Show the average page-count of all books currently stored.  
4. Exit cleanly.

The program must work only with pointer arithmetic—no array indexing is allowed after the initial setup.

## Requirements
- Represent a book with a struct that stores:
  - unsigned long isbn
  - unsigned pages
  - unsigned row
- Maintain a contiguous memory block that can grow up to a fixed maximum (MAX_BOOKS 100).
- Implement exactly four user commands:
  - 1 → addBooks
  - 2 → listBooks
  - 3 → avgPages
  - 0 → EXIT
- addBooks(n): the user supplies n (1 ≤ n and current+n ≤ MAX_BOOKS).  
  After the call, the n books are already placed in memory immediately after the last stored book; your code must advance the “logical end” of the collection accordingly.
- listBooks(): print the three fields of every stored book, one per line, in the order they sit in memory. Use the function displayBook described below.
- avgPages(): print the integer average of pages over the collection (truncate fractional part).
- All traversal of the collection must be done with pure pointer arithmetic (no [] operator).
- The only functions besides main() are:
  - void displayBook(const Book *b) – prints one book in the format “ISBN pages row”
  - double averagePages(const Book *start, const Book *end) – returns the average pages between two pointers (end points one past last element).

## Example
Input
```
1 3
123456789 320 5
987654321 456 2
111111111 200 3
2
3
0
```

Output
```
123456789 320 5
987654321 456 2
111111111 200 3
325
```

### CONSTRAINTS
- Must use a struct to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific book must be in a function called displayBook.
- The solution must be implemented with exactly two functions besides main(): displayBook and averagePages.
- All scanning of the collection must use pointer arithmetic; array subscripting is forbidden after the initial declaration.
- Menu option 0 must exit the program.

---

## Problem 10 - moonshotai/kimi-k2-instruct-0905 - Iteration 70
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its card-catalogue.  
Each index card contains a book’s title, its 13-digit ISBN, and the shelf row (an integer 1-100).  
All cards are stored consecutively in memory, and you are asked to write a small tool that walks through this array using pointer arithmetic only (no array sub-scripting) to list, search and update books.

## Requirements
1. Store the collection of cards in a dynamically allocated array.
2. Provide a menu with the following options (implement exactly as numbered):
   1. Add a new book  
   2. List all books  
   3. Search for a book by ISBN  
   4. Update the shelf row of a book (found by ISBN)  
   5. Exit the program  
3. All traversal of the array (printing, searching, updating) must be done with pointer arithmetic; the `[]` operator is **not allowed** after the array is created.
4. Memory must be released before the program terminates.

## Simple Example Run
```
Campus Catalogue
1 Add | 2 List | 3 Search | 4 Update | 5 Exit
Choice: 1
Title: Pointers 101
ISBN: 9780131103627
Row: 42

Choice: 3
ISBN to search: 9780131103627
Found: Pointers 101, row 42

Choice: 5
Good-bye!
```

### CONSTRAINTS
- A single `struct Book` must represent one catalogue card.  
- All printing of a single book (whether in List or Search) must be done by a function `void displayBook(const struct Book *bPtr)`.  
- The only functions allowed besides `main` are:  
  – `displayBook` (described above)  
  – Any helper you need for memory reallocation (but no extra “logic” functions).

---

## Problem 11 - moonshotai/kimi-k2-instruct-0905 - Iteration 71
# STEP 1: PROBLEM

## Context
A small library keeps every book’s “card” in one long shelf of contiguous memory.  
Each card is a fixed-size record that stores the book’s unique ID, its current due-day (0 = Sunday … 6 = Saturday), and a pointer that can be used to jump to the next book that is due on the **same** weekday.  
All cards for Sunday-due books are threaded together in a linked list, all Monday-due books in another list, and so on—seven circular lists total, one per weekday.

## Task
You will receive a single line of input that describes the cards exactly as they sit in memory:  
`id0 day0 id1 day1 … idN−1 dayN−1`  
where every `idX` is a non-negative integer and every `dayX` is 0–6.  
Using **pointer arithmetic only** (no array indexing allowed) you must:

1. Build the seven circular linked lists in place inside that memory block.
2. Starting with the list that corresponds to **today’s day** (given as the last value on the line), print the IDs of every book that is due on that weekday, in the order they appear in the list.
3. After the list is printed, output the total number of books due today.

## Example
### Input
```
10 1 20 3 30 1 40 2 50 1 1
```
(today is day 1 = Monday)

### Output
```
10 30 50
3
```

### Explanation
- Books due on Monday: 10 → 30 → 50 (circular, but we stop when we loop back to 10).  
- Count printed last: 3.

## Input/Output Rules
- Input is one single line of even length ≥ 2.  
- IDs are unique within a test case.  
- If no book is due today, output an empty line followed by 0.

### CONSTRAINTS
1. Must store each book in a `struct Book` containing:  
   `unsigned id; unsigned day; struct Book *next;`  
2. The entire collection must live in one contiguous block obtained by a single `malloc()` call; afterwards you may **only** use pointer arithmetic (never `[]`) to navigate it.  
3. Logic that prints the IDs for **one** weekday must be encapsulated in a function  
   `void printDue(struct Book *head, unsigned today)`  
   that is called exactly once from `main()`.  
4. No global variables; `main()` plus at most one helper function only.

---

## Problem 12 - moonshotai/kimi-k2-instruct-0905 - Iteration 72
# STEP 1: PROBLEM

## Background Story
You are helping the campus radio-station manager catalog vinyl records.  
Each record has a catalog number (integer) and a playing time in seconds.  
All records are stored consecutively in memory as an array of structs.  
The manager wants to be able to jump through the catalog in strides (pointer arithmetic) rather than using array indices, because “it feels more rock-and-roll.”

## Functional Requirements
1. Read an integer `n` (number of records, 1 ≤ n ≤ 100).
2. Read `n` lines, each containing:
   - catalog number (int)
   - playing time in seconds (int)
   Store these in an array of structs.
3. Read an integer `stride` (1 ≤ stride ≤ n).
4. Starting from the first record, print the catalog number and playing time of every `stride`-th record, using pointer arithmetic (not array indexing) to move between elements.
5. After printing the sequence, print the total playing time of those selected records.

## Example
Input
```
5
101 2400
102 2100
103 2700
104 2300
105 2500
2
```
Output
```
101 2400
103 2700
105 2500
Total: 7600
```

### CONSTRAINTS
- Represent each record with a `struct Record`.
- Must use pointer arithmetic (e.g., `ptr += stride`) to traverse the array; no array-subscript syntax inside the traversal loop.
- Logic for displaying one `Record` must be encapsulated in a function `void displayRecord(const struct Record *r)`.
- The only additional function besides `main()` is `displayRecord`.

---

## Problem 13 - moonshotai/kimi-k2-instruct-0905 - Iteration 73
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story:**  
A new community garden has planted 30 tomato seedlings in a single straight row. Every day the gardener records the height of each plant. She wants a tiny C program that, by scanning along that row with pointer arithmetic, can quickly tell her which plant is the tallest, which is the shortest, and how many plants are taller than a given threshold.

**Requirements:**  
1. Store the 30 heights (positive doubles) in a plain array.  
2. Provide exactly four menu choices:  
   1. Enter/Update all 30 heights  
   2. Show tallest and shortest plant (index + height)  
   3. Count how many plants are strictly taller than a user-supplied threshold  
   4. Exit  
3. All array work (scanning, comparison, counting) must be done with pointer arithmetic—no `[]` operator allowed.  
4. After each operation (except Exit), re-display the menu.  
5. Handle the “Exit” choice cleanly.

**Simple Example Run (user input after »):**  
```
Tomato Row Tracker
1.Enter heights
2.Show tallest & shortest
3.Count above threshold
4.Exit
Choice » 1
Enter 30 heights: 12.3 11.9 13.2 … (28 more) … 10.7
1.Enter heights
2.Show tallest & shortest
3.Count above threshold
4.Exit
Choice » 2
Tallest: plant 27, 13.2 cm
Shortest: plant 14, 9.8 cm
1.Enter heights
2.Show tallest & shortest
3.Count above threshold
4.Exit
Choice » 3
Threshold » 12
6 plants above 12 cm
1.Enter heights
2.Show tallest & shortest
3.Count above threshold
4.Exit
Choice » 4
Goodbye!
```

### CONSTRAINTS  
- You must represent the row of plants with a `struct Garden { double plants[30]; };`.  
- All array accesses must be performed by pure pointer arithmetic (no `[]`).  
- The logic for menu choices 2 and 3 must reside in a single function:  
  `void analyzePlants(const struct Garden *g, int choice)`  
  (You may add helper functions, but the analysis triggered by menu choices 2 and 3 must ultimately be invoked through this function.)

---

## Problem 14 - moonshotai/kimi-k2-instruct-0905 - Iteration 74
# STEP 1: PROBLEM

## Background Story
You are helping a small-town library that still keeps its card-catalogue information in a flat text file.  
Each “catalogue card” contains a book title, the year it was acquired, and the number of times it has been checked out.  
To modernise access, you will read this data into memory and let the librarian jump quickly to any card by its index, update the checkout counter, and immediately see the updated record—all using raw pointers and pointer arithmetic.

## Functional Requirements
1. Read an integer `n` (`1 ≤ n ≤ 100`) followed by `n` lines of catalogue data.  
   Each line contains:  
   - a string (the book title, no longer than 80 characters)  
   - an integer (acquisition year)  
   - an integer (current checkout count)  
2. After reading the data, repeatedly read single-letter commands until the command `X` is entered:  
   - `S i`  – Show the `i`-th card (`0 ≤ i < n`) in the exact format shown in the example.  
   - `U i`  – Update (increment by 1) the checkout count of the `i`-th card and then display that card.  
   - `X`    – Exit the program.  
3. All access to the catalogue must be done with pointer arithmetic; no array subscripting (bracket `[]`) is allowed after the initial storage is created.

## Simple Example
Input
```
3
The Little Prince 1943 42
Dune 1965 18
1984 1949 27
S 0
U 2
X
```
Output
```
The Little Prince (1943) -> 42
1984 (1949) -> 28
```

### CONSTRAINTS
- The catalogue record must be stored in a user-defined `struct`.  
- The logic that prints one catalogue entry (given a pointer to it) must reside in a function `void displayEntity(const struct Card *c)`.  
- The entire solution must be implemented with only **one** additional function besides `main` (i.e., `displayEntity`).

---

## Problem 15 - moonshotai/kimi-k2-instruct-0905 - Iteration 75
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story**  
You are helping a small library automate its card-catalog.  
Each book is stored as a contiguous block in a statically-allocated array.  
Because memory is tight, you may NOT use any indexing operator (`[]`)—every access must be done with pointer arithmetic.  

**Task**  
Write a program that:  
1. Keeps an array of at most 100 `Book` records.  
2. Lets the user repeatedly choose one of the following actions:  
   1) Add a new book (stop if the array is full).  
   2) Search for a book by ISBN and display its details.  
   3) Exit the program.  
3. Validates that an ISBN is exactly 10 characters long and unique inside the collection.  
4. When displaying, show: title, author, year, ISBN.  

**Simple Example**  
Input  
```
1
C Programming
King
1978
1234567890
2
1234567890
3
```  
Output  
```
C Programming
King
1978
1234567890
```  

### CONSTRAINTS  
- You must represent a book with a `struct Book`.  
- You must NOT use the `[]` operator anywhere in your code; all array accesses must be through pointers and pointer arithmetic.  
- The logic for displaying a single book must be encapsulated in a function `void displayBook(const struct Book *)`.  
- Only one additional function besides `main()` is allowed (i.e., `displayBook`).  
- Menu option 3 is EXIT; entering 3 must terminate the program cleanly.

---

## Problem 16 - moonshotai/kimi-k2-instruct-0905 - Iteration 76
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story:**  
The campus library has digitised its card-catalogue for classic novels. Each record is stored in memory as a contiguous block (an “array of structs”). Unfortunately, the head-librarian only remembers the *title* of a book, not its index. Your task is to write a tiny search engine that walks through the catalogue **using pointer arithmetic only**—no array indexing allowed—and returns the full details of the requested title.  

---

### Requirements  
1. Define a struct `Book` with members:  
   - `title` (string, ≤30 chars)  
   - `author` (string, ≤30 chars)  
   - `year` (int)  

2. Populate a **hard-coded** catalogue of exactly 5 classic novels.  

3. Present a menu:  
   ```
   1) Search by title
   2) Show all books
   3) Exit
   ```
   Option 3 must terminate the program.  

4. When the user chooses option 1, read a title and locate the book by scanning the array with **pure pointer arithmetic** (i.e. `*(catPtr + k)`).  
   - If found, display the full record.  
   - If not found, print `“Title not found.”`  

5. Option 2 simply prints the entire catalogue (again, no `[]` operators).  

---

### Example Run  
```
1) Search by title
2) Show all books
3) Exit
Choice: 1
Enter title: Pride and Prejudice
Author: Jane Austen, Year: 1813
```
```
Choice: 2
Title: Pride and Prejudice, Author: Jane Austen, Year: 1813
Title: 1984, Author: George Orwell, Year: 1949
Title: The Hobbit, Author: J.R.R. Tolkien, Year: 1937
Title: To Kill a Mockingbird, Author: Harper Lee, Year: 1960
Title: Crime and Punishment, Author: Fyodor Dostoevsky, Year: 1866
```
```
Choice: 3
Good-bye!
```

---

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (`Book`).  
- The logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 17 - moonshotai/kimi-k2-instruct-0905 - Iteration 77
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story**  
The tiny town of Byteville has just opened its first “Memory-Museum.”  
Every exhibit is a single byte, stored in a long corridor of memory.  
The curator keeps track of exhibits by their **distance from the front door**—i.e. their **offset**—using only pointer arithmetic.  
You have volunteered to write the software that lets visitors query the value stored at any offset and, if they wish, **rotate** (left-rotate) a contiguous block of exhibits starting at that offset.  

**Your Task**  
Implement a console program that:  
1. Creates an array of 16 `unsigned char` exhibits (values 0–255).  
2. Lets the user repeatedly:  
   a. **peek** at the value stored at a given offset (0 ≤ offset ≤ 15), or  
   b. **left-rotate** a block of k exhibits starting at that offset (k ≥ 2), or  
   c. **exit** the program.  
3. After every successful peek or rotation, prints the new full corridor (16 space-separated values in hex).  

**Simple I/O Example**  
User input shown after the `>` prompt.  
```
Initial corridor:
00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
> p 5
Peek at offset 5: 05
00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
> r 5 3
Rotated 3 exhibits starting at offset 5
00 01 02 03 04 06 07 05 08 09 0A 0B 0C 0D 0E 0F
> x
Good-bye!
```

### CONSTRAINTS  
1. You **must** represent the corridor with a single `unsigned char corridor[16]`.  
2. All access (peek and rotation) must be done **exclusively through pointer arithmetic**; no index notation (`[]`) is allowed inside the functions that manipulate the corridor.  
3. The logic for displaying the corridor must be in a function called `displayCorridor` that takes a `const unsigned char *` (the start of the corridor) and returns nothing.  
4. The peek and rotation logic must be handled by **one additional function** besides `main()` (i.e. only two functions total: `main` and `displayCorridor`).  
5. If you implement a menu, option `x` (lower-case) must exit the program.

---

## Problem 18 - moonshotai/kimi-k2-instruct-0905 - Iteration 78
# STEP 1: PROBLEM

## Background Story
The campus library has just replaced its old card-catalogue with a tiny in-memory database stored in an array of book records. You have been asked to write a console tool that lets a librarian walk through the shelf (array) using pointer arithmetic instead of ordinary indexing, locate a book, and optionally mark it as loaned out. All navigation must be done with pointers, never with subscript operators.

## Functional Requirements
1. Store at most 50 books in a statically allocated array.
2. Each book contains:
   - `int id` – unique identifier
   - `char title[40]` – up to 39 printable characters plus NUL terminator
   - `int available` – 1 if the copy is on the shelf, 0 if already loaned out
3. Provide a menu with the following options (the first letter is sufficient):
   - `a` Add a new book (append at the end; refuse if shelf is full)
   - `l` List all books (show id, title, status: "available" or "loaned")
   - `f` Find a book by id (use pointer arithmetic to walk the array)
   - `t` Toggle availability of a book (find it by id, flip the flag)
   - `x` Exit the program
4. All traversal of the array must be performed with pointer arithmetic (`*(ptr + k)` or `ptr++`, never `array[i]`).
5. If a book is not found, print `Book <id> not found.`

## Example Session
```
a
ID: 101
Title: C Programming
a
ID: 102
Title: Pointers 101
f
ID to find: 101
Found: C Programming (available)
t
ID to toggle: 101
C Programming is now loaned.
l
101 C Programming loaned
102 Pointers 101 available
x
```

## CONSTRAINTS
- Represent each book with a `struct Book`.
- The logic that prints the details of ONE book must be placed in a function `void displayBook(const struct Book *bptr)`.
- Implement only one additional helper function besides `main`; all other code must be inline in `main`.
- Menu option `x` exits the program.

---

## Problem 19 - moonshotai/kimi-k2-instruct-0905 - Iteration 79
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its old card-catalogue for classic novels.  
Each card contains a title, the year of first publication, and the number of copies currently on the shelf.  
All cards are stored consecutively in memory as an array of structures.  
Your task is to write a small “shelf scanner” that walks through this array with pointer arithmetic (no index notation) and produces a simple report.

## Functional Requirements
1. Read up to 100 cards from stdin.  
   – First comes an integer *n* (0 ≤ *n* ≤ 100).  
   – Then *n* lines follow, each containing:  
     `title` (single-word, ≤ 30 chars), `year` (int), `copies` (int).  
2. Using only pointer arithmetic (not `[]`), scan the array and:  
   a. Print the **average publication year** (rounded down to an integer).  
   b. Print the **title of the newest book** (largest `year`).  
   c. Print how many cards still have **at least one copy** (`copies > 0`).  
3. Stop processing as soon as the array ends; do not read beyond *n* elements.

## Simple Example
Input
```
4
Pride 1813 2
Emma 1815 0
Oz 1900 5
Mockingbird 1960 1
```
Output
```
Average year: 1842
Newest: Mockingbird
Cards in stock: 3
```

### CONSTRAINTS
- You must store each card in a `struct Book`.  
- The logic that prints the details of ONE specific book must be in a function `void displayBook(const struct Book *b)`.  
- The entire report (parts a–c) must be produced by a single additional function `void produceReport(struct Book *start, int n)`; `main()` is only allowed to read input and call this function.

---

## Problem 20 - moonshotai/kimi-k2-instruct-0905 - Iteration 80
# STEP 1: PROBLEM

## Background Story
The campus library has digitised its old card-catalogue into a single chunk of memory that looks like a long shelf of books.  
Each “book” is represented by a fixed-size record.  
Because the original catalogue was written in the 1970s, the entire collection is stored as one big byte array and the only way to reach a particular record is to jump through it with pointer arithmetic.  
Your task is to write a mini search engine that can locate a book by its unique ID and display its details.

## Requirements
1. The collection is stored in a statically allocated `unsigned char catalogue[]` whose length is always a multiple of the record size (see below).
2. Every record has exactly 24 bytes, laid out as:
   - `unsigned int id` (4 bytes, little-endian)
   - `char title[16]` (16 bytes, NUL-terminated if shorter)
   - `unsigned short year` (2 bytes)
   - `unsigned short shelf` (2 bytes)
3. The user enters an integer ID.  
   If the ID exists, print (in this order):  
   `Title`, `Year`, `Shelf` separated by a single space and followed by a newline.  
   If the ID does not exist, print `NOT FOUND\n`.
4. You may assume the catalogue contains ≤ 100 000 records and the IDs are unique.

## Simple Example
Input
```
3
```
Assuming the catalogue contains a record with id=3, title="Coraline", year=2002, shelf=42, the output is:
```
Coraline 2002 42
```
If no record has id=3, the output is:
```
NOT FOUND
```

### CONSTRAINTS
- You must define a `struct Book` that exactly matches the 24-byte layout described above.  
- The logic for printing the details of ONE specific book must be in a function `void displayBook(const struct Book *b)`.  
- No global variables except the catalogue array itself.  
- The only functions allowed besides `main()` are `displayBook` and any helper you need for searching.

---

## Problem 21 - moonshotai/kimi-k2-instruct-0905 - Iteration 81
# STEP 1: PROBLEM

## Context
You are helping the campus “Lost-&-Found” office digitize its shelf of unidentified items.  
Each item has: a sequential ID (starting at 1000), a short description, and the shelf slot it is stored in.  
All IDs are packed consecutively in memory, but the office intern keeps removing items, leaving “holes”.  
Your task is to write a small C program that, using raw pointers and pointer arithmetic, can:

- Show every item currently on the shelf  
- Shift the remaining items to the left so there are no gaps  
- Look up an item by ID and tell the user its details  

## Requirements
1. Store up to 50 items in a single **contiguous** array.  
2. Represent each item with a `struct` that contains:  
   - `unsigned int id`  
   - `char desc[32]` (description)  
   - `unsigned char slot` (shelf slot number)  
3. Keep track of how many items are **currently** stored (`size_t count`).  
4. Implement the three operations above by moving *only* through the array with pointer arithmetic (`++`, `--`, `+`, `-`, `[ ]`, etc.).  
   - No array subscripts such as `item[i]` are allowed *inside* the helper functions (subscripts are fine in `main` if you wish).  
5. After compaction, the order of the remaining items must stay the same.  

## Simple Example Run
```
=== Lost-&-Found Shelf ===
1) Show all items
2) Compact shelf
3) Find by ID
4) Exit
Choice: 1
1001  blue umbrella   shelf-7
1002  red水壶         shelf-9
1004  black jacket    shelf-12
Choice: 2
Compaction done. 3 items left.
Choice: 1
1001  blue umbrella   shelf-7
1002  red水壶         shelf-9
1004  black jacket    shelf-12
Choice: 3
Enter ID: 1002
Item 1002: red水壶 at shelf-9
Choice: 4
Good-bye!
```

### CONSTRAINTS
- You **must** use a `struct` to represent the primary data entity.  
- All traversal and compaction logic must be implemented with pointer arithmetic, not array indexing, inside the helper functions.  
- The only functions besides `main()` are:  
  - `void displayAll(Item *start, Item *end)`  
  - `Item *findById(Item *start, Item *end, unsigned int id)`  
  - `size_t compactShelf(Item *start, Item *end)`  
- If you implement an interactive menu, option `4` (or the keyword `exit`) must terminate the program.

---

## Problem 22 - moonshotai/kimi-k2-instruct-0905 - Iteration 82
# STEP 1: PROBLEM  
## Topic: Pointers and Pointer Arithmetic  

**Background Story**  
The campus “Byte-Swap” club is building a tiny database of its members.  
Each member record contains only two fields: an integer id and a float fee.  
All records are stored consecutively in an array.  
To keep the system trivial, the club wants every operation to be done with pointer arithmetic—no array subscripting allowed.  

**Precise Requirements**  
1. Declare a global constant `MAX 100`.  
2. Define a struct `Member` with two members: `int id`, `float fee`.  
3. Inside `main()` declare an array `Member roster[MAX];` and an integer `count` (initially 0).  
4. Implement a single additional function  
   ```c
   Member* findMember(Member* start, Member* end, int targetId);
   ```  
   that returns a pointer to the first element whose `id == targetId`, or `NULL` if not found.  
   The search must be performed using pure pointer arithmetic; no array indexing allowed.  
5. The program repeatedly reads commands from `stdin`:  
   - `A id fee` – append a new member (if room left).  
   - `F id` – find and print the fee of the member with the given id.  
   - `X` – exit the program.  
6. For command `F`, output either  
   ```
   fee = <value>
   ```  
   or  
   ```
   not found
   ```  
   exactly as shown.  
7. All traversal and access must use pointer arithmetic; the only place the identifier `roster` may appear is when passing its address to functions.  

**Simple Example Input/Output**  
Input:  
```
A 10 3.50
A 20 1.25
F 10
F 99
X
```  
Output:  
```
fee = 3.50
not found
```  

### CONSTRAINTS  
- You must use a struct to represent the primary data entity (`Member`).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`. (Here it will simply print the fee.)  
- The solution must be implemented with a single function besides `main()` (`findMember`).

---

## Problem 23 - moonshotai/kimi-k2-instruct-0905 - Iteration 83
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Context  
You are helping the campus radio-station manager catalog vinyl records.  
Each record has a catalog number (a 6-digit integer) and a title (≤40 characters).  
All records are stored contiguously in memory (an array of structs).  
The manager wants a tiny tool that, given a catalog number, can **instantly** compute how many “slots” away that record is from the beginning of the shelf (array) **without ever using array subscripting (i.e. no [] )**—only pointer arithmetic.  

## Requirements  
1. Define a struct `Vinyl` with members:  
   - `unsigned int catNum;`   // 6-digit catalog number  
   - `char title[41];`         // NUL-terminated string  

2. Read up to 100 records into a global array `shelf[100]`.  
   Input ends with catalog number 0 (sentinel).  

3. After reading, repeatedly read an integer `q`.  
   - If `q` is 0, exit the program.  
   - Otherwise, locate the first record whose catalog number equals `q`.  
   - Print the zero-based index of that record (first record → 0) **using only pointer arithmetic** (no array indexing).  
   - If not found, print `Not found`.  

4. You may assume every catalog number is unique.  

## Example  
**Input**  
```
123456 DarkSideOfTheMoon  
234567 Thriller  
345678 BackInBlack  
0  
234567  
999999  
0  
```  

**Output**  
```
1  
Not found  
```  

### CONSTRAINTS  
- You **must** use a struct to represent each vinyl record.  
- The logic that determines the zero-based index must reside in a function  
  `int findIndex(Vinyl *start, Vinyl *end, unsigned int target);`  
  which returns the index (via pointer subtraction) or −1 if not found.  
- Inside `findIndex` you **may not** use the `[]` operator; only pointer arithmetic.  
- The program must offer menu option `0` to exit.

---

## Problem 24 - moonshotai/kimi-k2-instruct-0905 - Iteration 84
# STEP 1: PROBLEM

## Background
You are helping the campus music club digitize its old cassette mixtapes.  
Each tape is stored as a continuous chunk of 16-bit audio samples in memory.  
The club wants a tiny tool that can “fast-forward” or “rewind” the tape by a user-supplied number of seconds, using pointer arithmetic only—no array indexing.

## Task
Write a program that:

1. Holds one mixtape in a dynamically-allocated array of `int16_t` samples.
2. Keeps track of the current play position with a single `int16_t*` pointer.
3. Provides a menu with three choices:
   - 1) Advance the play position forward by N seconds.
   - 2) Move the play position backward by N seconds.
   - 3) EXIT (choice 0) the program.
4. After every move, print the first four samples starting at the new position (or fewer if near the ends).  
   (Assume a sampling rate of 8 000 samples/second.)

## Example
Input (user interaction)
```
Tape length in seconds: 5
Initial samples (40 000 values) are filled automatically.
Menu:
1) Fast-forward
2) Rewind
0) EXIT
Choice: 1
Seconds to advance: 2
New position: 16000
First 4 samples at new position: 42 43 44 45
```
(The exact sample values are not important; only the pointer movement is checked.)

### CONSTRAINTS
- The mixtape must be represented by a `struct MixTape` that contains the pointer to the samples, the total number of samples, and the current position pointer.
- All logic for displaying the four samples must reside in a function `void displayEntity(const struct MixTape* tape)`.
- The solution must be implemented with only one additional function besides `main()` (i.e. `displayEntity`).

---

## Problem 25 - moonshotai/kimi-k2-instruct-0905 - Iteration 85
# STEP 1: PROBLEM

## Topic: Pointers and Pointer Arithmetic

### Background Story
You are writing firmware for a tiny “smart-parking” device that keeps track of parking-meter payments.  
The device has a fixed-size circular buffer (an array) that can hold up to 24 hourly payment records.  
Each record is a single 32-bit unsigned integer that encodes the number of cents paid during that hour.  
Because the microcontroller has almost no RAM, you must access every record **exclusively through pointer arithmetic**—no array subscripting is allowed anywhere in the user-defined functions.

### Requirements
1. The buffer is declared in `main()` as  
   `uint32_t payments[24];`  
   and is *pre-initialised* with 24 zeroes.
2. Provide a function  
   `void recordPayment(uint32_t *base, uint32_t offset, uint32_t cents)`  
   that deposits `cents` into the slot `(base + offset) % 24`.  
   `offset` may be larger than 23; the modulo operation keeps it inside the circular buffer.
3. Provide a function  
   `uint32_t totalCollected(uint32_t *base)`  
   that returns the sum of all 24 payments, again using **only pointer arithmetic** to traverse the buffer.
4. `main()` must repeatedly read commands from standard input:
   - `p offset cents`  (record a payment)  
   - `t`              (print total collected)  
   - `q`              (quit the program)  
   All inputs are valid; no error checking is required.

### Simple Example
Input
```
p 25 150
p 1 275
t
q
```
Output
```
425
```

### CONSTRAINTS
- The solution must be implemented with **exactly two** user-defined functions besides `main()`:  
  `recordPayment` and `totalCollected`.  
- Inside those functions **you may not use the `[]` operator**; only pointer arithmetic is allowed.

---

## Problem 26 - moonshotai/kimi-k2-instruct-0905 - Iteration 86
# STEP 1: PROBLEM
## Topic: Pointers and Pointer Arithmetic

### Background Story
You are helping the campus music club digitize its vinyl-collection archive. Each vinyl record is stored in a box that is exactly 3 inches wide. All boxes are placed consecutively on a long shelf. The club president gives you the starting memory address of the first box (as a pointer to the first structure) and the total number of records. Using pointer arithmetic (no array indexing allowed), you must compute the memory address of any requested box and display its contents.

### Requirements
1. Represent a vinyl record with a structure that contains:
   a. catalog number (positive int)  
   b. title (string up to 40 chars)  
   c. artist (string up to 40 chars)  
2. Read an integer N (1 ≤ N ≤ 100) followed by N triples of data (catalog, title, artist) and store them contiguously in dynamically allocated memory.  
3. Read an integer Q (1 ≤ Q ≤ 100) followed by Q queries.  
   Each query is a single integer k (1-based position on shelf).  
4. For each query use pointer arithmetic to locate the k-th structure and print its catalog number, title, and artist on one line, separated by “ | ”.  
5. If k is out of range (k < 1 or k > N) print “Query out of range.”  
6. Free all dynamically allocated memory before exiting.

### Simple Example
Input  
```
3
101 Rumours Fleetwood Mac
102 Back in Black AC/DC
103 Thriller Michael Jackson
4
1
3
4
2
```
Output  
```
101 | Rumours | Fleetwood Mac
103 | Thriller | Michael Jackson
Query out of range.
102 | Back in Black | AC/DC
```

### CONSTRAINTS
- Must use a struct to represent the primary data entity (a vinyl record).  
- Logic for displaying the details of ONE specific entity must be in a function called displayEntity.  
- Pointer arithmetic (not array subscripting) must be used to reach any requested record.

---

## Problem 27 - moonshotai/kimi-k2-instruct-0905 - Iteration 87
# STEP 1: PROBLEM

## Context
You are helping a wildlife‐tracking team that stores animal sightings in a simple array‐based logbook.  
Each log entry contains a species name (≤29 chars), the exact GPS latitude and longitude (both doubles), and the sighting’s UTC time expressed as seconds‐since‐epoch (long).  
Your program must let the user browse and inspect these entries exclusively through pointer arithmetic—never by normal array‐subscripting such as `logbook[i]`.

## Functional Requirements
1. Read from standard input an integer N (0 < N ≤ 100) followed by N complete log entries.  
2. Store the entries in a plain C array.  
3. Provide a menu with exactly these three choices (the numbers shown are required):
   - 1 – Show earliest sighting (smallest time stamp)  
   - 2 – Show northern‐most sighting (largest latitude)  
   - 3 – Exit program  
4. After the user chooses option 1 or 2, print the requested entry’s species, lat, lon, and time stamp on a single line, separated by single spaces.  
5. After printing, re-display the menu until the user chooses option 3.

## Simple Example
Input
```
3
Lion 2.152 -1.674 1584230400
Elephant 0.543 35.293 1584316800
Zebra -2.333 34.567 1584403200
```
Sample interaction
```
1
Lion 2.152 -1.674 1584230400
2
Elephant 0.543 35.293 1584316800
3
```
(The program terminates immediately after the user types 3.)

### CONSTRAINTS
- The primary data entity must be represented by a struct named `LogEntry`.  
- All access to array elements must be done with pointer arithmetic; using the `[]` operator on the array is forbidden outside of the original read loop.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()` (that function is `displayEntity`).

---

## Problem 28 - moonshotai/kimi-k2-instruct-0905 - Iteration 88
# STEP 1: PROBLEM

## Background Story
You are helping a wildlife-rescue team that has set up motion-triggered cameras in a forest.  
Each camera stores its photos in a contiguous memory block, and every photo is represented by an integer “size-in-KB”.  
At the end of the week the rangers want to know, for every camera, how many photos are larger than a user-supplied threshold and what the average size of those “big” photos is.  
Because the micro-controller has very little RAM, you must not copy the photos—work entirely with pointer arithmetic.

## Functional Requirements
1. Read an integer `n` (number of photos) followed by `n` integers that represent the photo sizes (in KB) stored contiguously in memory.
2. Read an integer `threshold` (in KB).
3. Using only pointer arithmetic (no array subscripting) compute:
   - `countBig` – how many photos are strictly larger than `threshold`
   - `avgBig` – the arithmetic mean size of those “big” photos (print 0.0 if there are none).  
   Print `countBig` and `avgBig` with 1 decimal place for the average.
4. The rangers may inspect several cameras in one run; after each camera’s data are processed, ask whether they want to process another camera (`y`/`n`).  
   The program must terminate cleanly when the user answers anything other than case-insensitive `y`.

## Simple Example
Input
```
8
1200 560 3000 890 3100 560 1200 2990
1000
```
Output
```
4 2572.5
Process another camera? (y/n): n
```
(Explanation: four photos exceed 1000 KB; their average size is (3000+3100+1200+2990)/4 = 2572.5.)

### CONSTRAINTS
- Represent a camera with a `struct Camera` that contains:
  - an `int *photos` pointer to the dynamically allocated block of photo sizes,
  - an `int n` storing how many photos it holds.
- The only functions allowed are `main()` and one additional function:
  - `void processCamera(struct Camera *cam, int threshold)`  
    which, using pointer arithmetic, updates `countBig` and `avgBig` and prints them as specified.
- The program must offer the EXIT option “n” (or any input other than “y”) to quit.

---

## Problem 29 - moonshotai/kimi-k2-instruct-0905 - Iteration 89
# STEP 1: PROBLEM

## Background Story
The university’s robotics club is building a line-following robot that stores the sequence of turns in a circular buffer kept in flash memory.  
Each turn is recorded as a single character:  
- ‘L’ for a 90° left turn  
- ‘R’ for a 90° right turn  
- ‘S’ for straight  

Because flash memory is limited, the club wants a tiny C program that can:  
1. Store the most recent 20 moves in a circular buffer.  
2. Replay the moves from the oldest to the newest on demand.  
3. Tell the robot how many moves are currently stored.  

All access to the buffer must be done with pointers and pointer arithmetic—no array indexing allowed.

## Requirements
Write a C program that:

1. Keeps a global circular buffer (array) named `history` of exactly 20 `char` values.  
2. Provides three user commands (menu-driven):  
   - `A <move>` → append one move (L, R, or S)  
   - `P` → print the entire sequence from oldest to newest, separated by spaces  
   - `Q` → quit the program (EXIT option)  
3. Uses two size_t variables, `start` and `count`, to track where the oldest element is and how many elements are stored.  
4. Implements **only one additional function** besides `main()`:  
   `void appendMove(char **pNext, char move);`  
   - `pNext` is the address of the pointer that always points to the slot where the next move will be written.  
   - The function updates the circular buffer and wraps the pointer when necessary.  
5. All array accesses inside `appendMove` must be done purely by pointer arithmetic; no `history[i]` notation is allowed.  
6. Printing inside `main()` must also use pointer arithmetic to walk through the buffer.

## Simple Example Run
Input:
```
A L
A R
A S
P
Q
```
Output:
```
L R S
```

## Additional Clarifications
- Upper/lower case is ignored; store everything in uppercase.  
- If more than 20 moves are entered, the oldest move is silently overwritten.  
- After the `P` command, output a single newline.

### CONSTRAINTS
- Must use a `struct` to represent the **primary data entity** (the circular buffer metadata).  
  Example skeleton (you may rename):  
  ```c
  typedef struct {
      char buffer[20];
      char *next;   // points to next write position
      size_t count; // number of valid elements
  } Log;
  ```
- Logic for displaying the details of ONE specific move (a single character) must be in a function called `displayMove`.  
- The solution must be implemented with a single function besides `main()` (i.e., only `displayMove` and `main` are allowed).

---

## Problem 30 - moonshotai/kimi-k2-instruct-0905 - Iteration 90
# STEP 1: PROBLEM

**Topic:** Pointers and Pointer Arithmetic  
**Story:**  
This year the Computer Science Department is hosting a “Treasure-Hunt in Memory.”  
Each student team is given a “map” that is actually one big contiguous block of 1024 bytes.  
At the start of the block sits a header that tells how many treasure chests are hidden in the rest of the block.  
Each chest is described by a fixed-size struct that contains:  
- an id (unsigned 32-bit)  
- a latitude (float)  
- a longitude (float)  
- loot value in gold coins (unsigned 32-bit)  

All chests are stored back-to-back immediately after the header.  
Your task is to write a small inspection tool that, given only the raw memory block, uses pointer arithmetic (no array subscripting) to:  
1. Print how many chests exist.  
2. Show the details of the chest located at a user-chosen index.  
3. Show the details of the very last chest (highest loot chest).  
4. Exit the program.  

**Functional Requirements**  
1. Read the memory block from standard input as one 1024-byte chunk (you may read it with fread).  
2. Treat the first 4 bytes as an unsigned 32-bit integer that equals the number of chests (N).  
3. Treat the next N*sizeof(Chest) bytes as a sequence of Chest structs.  
4. Provide an interactive text menu with exactly four options:  
   - 1) Display total number of chests  
   - 2) Display chest at index (user supplies 0-based index)  
   - 3) Display the last chest  
   - 4) EXIT (terminates the program)  
5. If the user chooses option 2, validate the index; if it is out of range print “Invalid index” and redisplay the menu.  
6. All chest inspection logic must be implemented without using the [] operator—only pointer arithmetic on the base address of the block.  
7. All printing of a single chest must be done through a helper function called displayEntity.  

**Simple Example Run**  
(assume the binary input contains 3 chests; sizes are illustrative)  
Input (binary, 1024 bytes)  
```
03 00 00 00          // little-endian 32-bit 3
01 00 00 00 00 00 80 3F 00 00 00 3F 0A 00 00 00
02 00 00 00 00 00 00 40 00 00 80 3F 14 00 00 00
03 00 00 00 00 00 40 40 00 00 40 40 1E 00 00 00
```
User session (stdin/stdout):  
```
MENU
1) Display total number of chests
2) Display chest at index
3) Display the last chest
4) EXIT
Choice: 1
Number of chests: 3

MENU
...
Choice: 2
Enter index: 1
Chest 1: lat=2.000000 lon=1.000000 loot=20

MENU
...
Choice: 3
Chest 2: lat=3.000000 lon=3.000000 loot=30

MENU
...
Choice: 4
(Program ends)
```

### CONSTRAINTS  
- Must define a struct named Chest with the exact layout described.  
- Must use a function called displayEntity that takes a single const Chest* and prints its details.  
- Must implement the entire inspection logic with pointer arithmetic—no array indexing allowed.  
- Must implement only one additional function besides main() (displayEntity).  
- Menu option 4 is the only way to exit; the program must terminate cleanly when chosen.

---

## Problem 31 - moonshotai/kimi-k2-instruct-0905 - Iteration 91
# STEP 1: PROBLEM

## Background Story
You are helping a librarian organize a shelf of classic novels.  
Each book has a unique position on the shelf (1-based index) and a fixed-length title (≤30 characters).  
Instead of moving the books physically, the librarian wants a small C program that can “scan” the shelf with pointer arithmetic and report which books are in a requested range of positions.

## Requirements
1. Store exactly 10 book titles in a 1-D array of fixed-size char buffers (30 chars each).  
2. Read a start and end position (both inclusive) from standard input.  
3. Using only pointer arithmetic—no array subscripting (i.e., no `books[i]` after the initial load)—print the titles that lie between the two positions, one per line.  
4. If the user enters an invalid range (start < 1, end > 10, or start > end), print `Invalid range` and nothing else.  
5. Stop the program when the user enters 0 for either the start or end position (this acts as the EXIT condition).

## Example I/O
Input
```
3 5
```
Output
```
Pride and Prejudice
1984
Jane Eyre
```
Next Input
```
0 0
```
Program terminates.

## Initial Shelf Contents (pre-loaded)
1  “The Great Gatsby”  
2  “To Kill a Mockingbird”  
3  “Pride and Prejudice”  
4  “1984”  
5  “Jane Eyre”  
6  “Wuthering Heights”  
7  “The Catcher in the Rye”  
8  “Brave New World”  
9  “Moby Dick”  
10 “War and Peace”

### CONSTRAINTS
- All shelf access after the initial load must be done with pointer arithmetic (no `[]`).  
- Logic for displaying the details of ONE specific book must be in a function called `displayBook`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 32 - moonshotai/kimi-k2-instruct-0905 - Iteration 92
# STEP 1: PROBLEM

## Story
You are helping the campus library digitize its card-catalog system.  
Each book is represented only by its starting memory address (a pointer to the first of four consecutive integers that hold: ID, year, edition, shelf-number).  
Your task is to write a tiny “shelf-shifter” program that walks along this contiguous memory with pointer arithmetic and reports which books need to be moved because their shelf-number is out of the legal 1-to-99 range.

## Functional Requirements
1. Read an integer `n (1 ≤ n ≤ 20)` followed by `4×n` space-separated integers stored in one contiguous block of memory.
2. Treat the block as an array of `n` books, each book occupying four consecutive ints:  
   `[id, year, edition, shelf]`.
3. Using only pointer arithmetic (no array subscripting like `a[i]`) traverse the block and collect every book whose shelf-number is **not** between 1 and 99 inclusive.
4. Print the IDs of the invalid books in one line, space-separated, in the same order they appeared. If none are invalid, print `OK`.

## Example
Input  
```
3
101 2010 2  5
102 1999 1  0
103 2022 3 100
```
Output  
```
102 103
```

### CONSTRAINTS
- Represent each book with a `struct Book` containing the four integers.  
- Logic that prints the details of **one** book must be placed in `void displayBook(const struct Book *b)`.  
- You may add at most one helper function besides `main()`.

---

## Problem 33 - moonshotai/kimi-k2-instruct-0905 - Iteration 93
# STEP 1: PROBLEM

## Background Story
You are helping the registrar’s office of a small college that keeps course‐enrollment data in plain C arrays.  
Each course is identified by a 4-digit code (e.g. 1021) and has room for exactly CAPACITY students.  
The registrar needs a quick way to see which seats are still free, assign a seat to a new student (if one is open), and remove a student.  
All access to the underlying arrays must be done with pointers and pointer arithmetic—array-indexing with [] is **not allowed** except in the one place explicitly permitted below.

## Functional Requirements
1. Represent a course as a `struct Course` containing:
   - `int code;`          // 4-digit course code  
   - `int capacity;`       // maximum seats (fixed when the course is created)  
   - `int size;`          // how many seats are currently occupied  
   - `int *seats;`        // dynamically allocated array of student IDs (0 means empty)  

2. Write a function  
   `int menu(Course *c);`  
   that displays the following text and returns the user’s choice as an int:

   ```
   1) Show free seats
   2) Assign seat
   3) Remove student
   4) Exit
   Choice:
   ```

3. Implement the three operations (1–3) **entirely with pointer arithmetic**:
   - Show free seats: print every index that currently contains 0.  
   - Assign seat: read a student ID and the desired seat index; if that seat is free (0), store the ID there and increment `size`.  
   - Remove student: read a seat index; if it is occupied (non-zero), set it back to 0 and decrement `size`.

4. `main()` must:
   - create one `Course` with a code and capacity of your choice (e.g. 1021, 5);  
   - zero-initialise the seats;  
   - loop on the menu until the user chooses 4;  
   - free all dynamically allocated memory before exiting.

## Simple Example Run
(Note: user input follows `>`)

```
1) Show free seats
2) Assign seat
3) Remove student
4) Exit
Choice: >1
Free seats: 0 1 2 3 4

Choice: >2
Enter student ID and seat index: >1234 2
Seat 2 assigned to student 1234.

Choice: >1
Free seats: 0 1 3 4

Choice: >4
```

### CONSTRAINTS
- `struct Course` must be used to represent the primary data entity.  
- Logic for displaying the list of free seats (option 1) must be placed in a separate function `void showFreeSeats(const Course *c);` which is called from the menu handler.  
- The solution must be implemented with **only two functions besides main**: `menu()` and `showFreeSeats()`.

---

## Problem 34 - moonshotai/kimi-k2-instruct-0905 - Iteration 94
# STEP 1: PROBLEM

## Background Story
The campus library has a “Book-Stacker” robot that stores books in a single long corridor.  
Each book is identified only by its (unique) shelf position: an integer address like 1000, 1004, 1008 …  
The robot keeps the books in ascending address order, but students keep returning books, so empty slots appear.  
Your job is to write a tiny, low-level helper program that, given the current shelf layout, can compact the books so the empty slots are at the high-address end and the books remain in their original relative order.

## Task
You will receive two lines of input:
1. An even integer `N` (2 ≤ N ≤ 20) telling how many shelf slots exist.  
2. `N` hexadecimal addresses separated by spaces.  Each address is a multiple of 4 and lies between 0x1000 and 0x2000 inclusive.  A value `0x0000` marks an empty slot; every other value is a book.

Write a program that:
- Reads the data into an array.  
- Uses pointer arithmetic (not array subscripts) to scan the array exactly once and compact the books toward the low-address end.  
- Prints the compacted shelf, still in hexadecimal, with one space between values and no trailing space.

## Simple Example
Input  
```
8
0x1000 0x0000 0x1008 0x0000 0x1010 0x1014 0x0000 0x1018
```
Output  
```
0x1000 0x1008 0x1010 0x1014 0x1018 0x0000 0x0000 0x0000
```

### CONSTRAINTS
1. Represent each shelf slot with a `struct Slot { unsigned int addr; };`  
2. The only functions besides `main()` must be:  
   - `void compact(struct Slot *start, struct Slot *stop)`  
     (using pointer arithmetic to perform the in-place compaction)  
   - `void displayShelf(struct Slot *start, struct Slot *stop)`  
     (prints the final shelf contents)  
3. No auxiliary arrays or dynamic allocation; the original array must be modified in place.

---

## Problem 35 - moonshotai/kimi-k2-instruct-0905 - Iteration 95
# STEP 1: PROBLEM

## Background Story
The campus library has just upgraded its card-catalogue system.  
Each book is now represented by a small memory block that stores its ID, title, and shelf row.  
To speed up searches, the librarian wants a tiny tool that can “slide” along the shelf (array) using pointer arithmetic and show the details of any requested book.

## Functional Requirements
1. Define a constant `MAX_BOOKS = 5`.
2. Define a `struct Book` with three members:
   - `unsigned int id`
   - `char title[40]` (max 39 printable characters + terminating `\0`)
   - `unsigned char row` (shelf row number, 1–255)
3. In `main()`:
   - Declare a static array `catalogue[MAX_BOOKS]` and fill it with the data supplied by the user (one book per line: id, title, row).
   - After reading the catalogue, repeatedly read an integer index `i` (0 ≤ i < MAX_BOOKS).
   - For every valid index, call the function `displayBook` (see constraints) to print the book’s information.
   - If the index is –1, terminate the program.
   - Any other out-of-range index must print `Invalid index` and prompt again.

## Simple Example
Input
```
101 C_Programming 3
102 Pointers_101 1
103 Fun_With_Memory 5
104 Algorithm_Notes 2
105 OS_Concepts 4
2
0
-1
```
Output
```
103 Fun_With_Memory 5
101 C_Programming 3
```

## CONSTRAINTS
- You must use the `struct Book` described above.
- The only function you may write besides `main()` is `void displayBook(const struct Book *bPtr)`; it must receive a pointer and use only pointer/arrow notation inside.
- Pointer-arithmetic traversal is required: inside `main()` you must locate the requested book by adding the index to the base pointer of the array (no square-bracket subscripting allowed when accessing the element).
- No global variables.
- The program must exit when the user enters the integer –1.

---

## Problem 36 - moonshotai/kimi-k2-instruct-0905 - Iteration 96
# STEP 1: PROBLEM

## Background Story
You are helping a small music venue called “The Pointer Stage” manage its nightly set list.  
Every song is stored as a 32-byte title (max 31 printable characters plus the terminator).  
All songs are kept back-to-back in one big character array called `setList`.  
A second integer array, `idx`, holds the byte-offset of the first character of every title.  
Thus the *n-th* song starts at `setList + idx[n]` and is a normal C-string.

## Task
Write a program that lets the user:
1. Append a new song title (stop if the arena is full).
2. Remove the last song.
3. Print the current running order (one song per line).
4. Exit.

All work must be done with raw pointers and pointer arithmetic; no array subscripting (`[]`) is allowed while accessing `setList` or `idx`.

## Example Run
```
=== The Pointer Stage ===
1 Add song
2 Remove last
3 Show set list
4 Exit
Choice: 1
Title: Midnight Blues
Choice: 1
Title: Neon Lights
Choice: 3
1. Midnight Blues
2. Neon Lights
Choice: 2
Removed "Neon Lights"
Choice: 4
Good show!
```

### CONSTRAINTS
- Represent the data with one `struct` named `SetList`.
- The only functions besides `main()` must be:
  - `int addSong(SetList *sl, const char *title);`  
  - `void removeLast(SetList *sl);`  
  - `void displaySet(const SetList *sl);`  
- The solution must be implemented with these three functions only (plus `main`).

---

## Problem 37 - moonshotai/kimi-k2-instruct-0905 - Iteration 97
# STEP 1: PROBLEM

## Story
A small company keeps track of its inventory in a simple file that stores the names of products and their quantities.  
Your task is to write a small command-line utility that lets the user browse through the inventory using only pointer arithmetic—no array subscripting allowed after the initial load.

## Requirements
1. Read up to 100 product records from standard input.  
   Each record is on one line and has the form:  
   `<name> <quantity>`  
   where `<name>` is a single word (≤30 characters) and `<quantity>` is a non-negative integer.
2. After reading, print a short prompt `cmd>`` and repeatedly accept single-character commands:
   - `n` – move the “current” pointer to the next product (wraps to the first product after the last).  
   - `p` – move the “current” pointer to the previous product (wraps to the last product if already at the first).  
   - `d` – display the product currently pointed to, using the exact format shown below.  
   - `q` – exit the program.
3. All navigation must be done with pointer arithmetic (e.g., `++`, `--`, or `+`/`-` on pointers); array indexing (`[]`) is forbidden once the initial data is loaded.
4. If no data was read, any command except `q` must print `Inventory empty.` and re-prompt.

## Example Session
Input (redirected from a file or typed):
```
apple 12
banana 5
carrot 8
```

Interaction:
```
cmd> d
apple : 12
cmd> n
cmd> d
banana : 5
cmd> n
cmd> n
cmd> d
apple : 12
cmd> q
```

### CONSTRAINTS
- Represent each product with a `struct` that contains a `char name[31]` and an `int quantity`.
- The logic that prints one product must be in a function `void displayProduct(const struct Product *p)`.
- The solution may contain only two functions: `main()` and `displayProduct()`.
- The menu option to exit is the single character `q`.

---

## Problem 38 - moonshotai/kimi-k2-instruct-0905 - Iteration 98
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old card-catalog.  
Each card contains a book’s ID (int) and its shelf position (char row, int column).  
Your program will act as a tiny “shelf navigator” that walks through an in-memory array of these cards using only pointer arithmetic—no array subscripting.

## Functional Requirements
1. Read up to 100 cards into a contiguous array.  
2. After each card is entered, immediately display the card’s information.  
3. When the user finishes entry, print the entire catalog in the exact order it was typed.  
4. Provide a menu with exactly three choices:  
   1) Add a new card  
   2) Re-print the whole catalog  
   3) Exit  
   (Option 3 must terminate the program.)

## Simple Example Run
```
1) Add  2) List  3) Exit
Choice: 1
Book ID: 101
Shelf row: A
Shelf column: 12
Card #1: ID=101, Position=A-12

1) Add  2) List  3) Exit
Choice: 1
Book ID: 102
Shelf row: C
Shelf column: 5
Card #2: ID=102, Position=C-5

1) Add  2) List  3) Exit
Choice: 2
Catalog:
101 A-12
102 C-5

1) Add  2) List  3) Exit
Choice: 3
Good-bye!
```

## CONSTRAINTS
- Must store each card in a struct named `Card`.  
- Must keep the collection in a plain C array (not std::vector).  
- Must use pointer arithmetic (++, *, ->, etc.) for every array access—no `[]` operator.  
- All printing of a single card must be done by a function `void displayCard(const Card *c)`.  
- The entire solution must be implemented with **one additional function besides main()** (i.e., only `main` and `displayCard`).

---

## Problem 39 - moonshotai/kimi-k2-instruct-0905 - Iteration 99
# STEP 1: PROBLEM

## Context
You are helping the campus library automate its small magazine rack.  
Each magazine is represented only by its **ISSN** (a 9-digit integer) and the **number of copies** currently on the shelf.  
All magazines are stored **in increasing order of ISSN** in a fixed-size array.  
Instead of moving large chunks of memory when a new magazine arrives, the librarian simply places it in the first free cell and later runs a “compact-and-sort” routine.  
Your task is to write the routine that performs this in-place compaction and sorting using only pointer arithmetic—no array-index syntax (`[]`) is allowed after the initial load.

## Requirements
1. Store the magazines in an array of `struct Magazine { long issn; int copies; };`.
2. Keep a `size_t count` of how many slots are currently occupied.
3. Implement a single operation (triggered by menu option 1):
   - **Add Magazine**  
     - If the ISSN already exists, just add the incoming copies to the existing entry.  
     - If the ISSN is new, place it in the first empty cell (even if this breaks the order).  
4. Implement a second operation (triggered by menu option 2):
   - **Compact & Sort**  
     - Move all valid magazines to the front of the array, eliminating any unused holes.  
     - Sort the magazines in ascending ISSN order **using only pointers** (no `[]`).  
5. Implement a third operation (triggered by menu option 3):
   - **Display Shelf**  
     - Print the magazines in the current order, one per line:  
       `ISSN copies`  
6. Implement a fourth operation (triggered by menu option 0):
   - **EXIT** the program.

## Simple Example
### Input
```
3
1 123456789 5
1 987654321 2
1 123456789 3
2
3
0
```

### Output
```
123456789 8
987654321 2
```

### Explanation
- Three magazines are added; the second arrival for ISSN `123456789` simply increases its copies.  
- Option 2 compacts and sorts the shelf.  
- Option 3 prints the final shelf state.  
- Option 0 terminates the program.

### CONSTRAINTS
- You must represent each magazine with the provided `struct Magazine`.
- All array accesses after the initial load must be performed through pointer arithmetic; the `[]` operator is **not** allowed in `compactAndSort`, `addMagazine`, or `displayShelf`.
- The only functions besides `main()` are:
  - `void addMagazine(struct Magazine *shelf, size_t *count, size_t capacity, long issn, int copies);`
  - `void compactAndSort(struct Magazine *shelf, size_t count);`
  - `void displayShelf(const struct Magazine *shelf, size_t count);`
- Menu option **0** must exit the program cleanly.

---

## Problem 40 - moonshotai/kimi-k2-instruct-0905 - Iteration 100
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Background Story  
The campus library has just gone “digital-first.” Instead of stamping due-dates inside books, the librarian now stores each book’s info in one big contiguous array inside the program’s memory. To speed up shelving, the librarian wants a tiny tool that can walk through that array with pointer arithmetic (no array subscripts!) and show the books that are currently overdue.

## Functional Requirements  
1. The program keeps up to 100 books in a **contiguous** array.  
2. Each book has:  
   - ID (positive int)  
   - Title (single-word string, ≤30 chars)  
   - Due year, month, day (ints)  
3. The user first enters how many books (`n`, 0 < n ≤ 100).  
4. For each book the user enters the data above, in the order listed.  
5. The current date (year, month, day) is entered next.  
6. Using **only pointer arithmetic** (no `[]` operator) you must:  
   - Find every book whose due date is **strictly earlier** than the current date.  
   - Display the book’s ID and Title in the order they appear in the array.  
7. If none are overdue, print `All books are on time.`  
8. The program must terminate cleanly after displaying results.

## Simple Example  
**Input:**  
```
3
101 Novel 2024 5 10
102 Poems 2024 4 25
103 Java 2024 5 9
2024 5 9
```

**Output:**  
```
102 Poems
```

### CONSTRAINTS  
- You must define a `struct Book` to represent a book.  
- Logic that prints the details of **one** book must live in a function `void displayBook(const struct Book *b)`.  
- You may **not** use array subscripting (`[]`) inside `main` or inside `displayBook`; traversal must be done exclusively with pointer arithmetic.

---

## Problem 41 - openai/gpt-oss-120b - Iteration 61
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is represented by a small record containing the ISBN, the title, and the number of copies currently on the shelf. The library wants a simple command‑line utility that stores a **fixed‑size** array of book records in memory and lets a librarian browse, add, and query the data using only pointer arithmetic (no array indexing `[]`).  

## Requirements  
Write a C program that:  

1. **Defines** a `struct Book` with the following members:  
   * `char isbn[14];`   // 13‑digit ISBN plus terminating null  
   * `char title[51];`  // up to 50 characters plus terminating null  
   * `int copies;`  

2. **Creates** an array capable of holding **up to 20** `Book` objects. The array must be allocated on the stack (e.g., `struct Book books[20];`).  

3. **Presents** a text menu that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
   * `1` – Add a new book (if there is free space).  
   * `2` – List all books currently stored.  
   * `3` – Find a book by ISBN and display its details.  
   * `4` – Exit the program.  

4. **Implements** all traversals of the `books` array **exclusively with pointer arithmetic** (e.g., using `struct Book *p = books; p < books + count; ++p`). Direct indexing such as `books[i]` is **not allowed** anywhere except when initializing the array size.  

5. **Uses** a separate function called `void displayBook(const struct Book *b);` that prints the ISBN, title, and copy count of a single `Book`. This function must be called whenever a single book’s information needs to be shown (options 2 and 3).  

6. **Handles** input errors gracefully (e.g., trying to add a book when the array is full, or searching for a non‑existent ISBN).  

## Example Input / Output  

```
=== Library Book Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added successfully!

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 2

--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 3

Enter ISBN to search: 9780131103627

--- Book Found ---
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

=== Library Book Manager ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 4

Goodbye!
```

If the user searches for an ISBN that does not exist:

```
Enter ISBN to search: 1234567890123
No book with ISBN 1234567890123 found.
```

If the array is full and the user selects option 1:

```
Cannot add more books; the inventory is full (20 entries).
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented by a `struct Book`.  
* The function `displayBook` **must** be used to print the details of a single book.  
* All iteration over the `books` array **must** use pointer arithmetic; the `[]` operator is prohibited for traversal.  
* The program must contain **only two functions** besides `main`: `displayBook` and optionally a helper for menu input (if you choose to create one). No additional helper functions are allowed.  
* The menu must include the explicit option `4` to **EXIT** the program, as shown in the requirements.  

---

## Problem 42 - openai/gpt-oss-120b - Iteration 62
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book on the shelves is identified by a **Book ID** (an integer) and has a **shelf position** measured as the number of centimeters from the left end of the shelf. The library wants a small C program that stores a collection of books in a dynamically allocated array and allows the librarian to query and update the positions using pointer arithmetic only (no array indexing `[]`).  

## Requirements  
Write a program that:  

1. **Creates** a dynamic array of `N` books (the value of `N` is entered by the user).  
2. Each book is represented by a `struct Book` containing:  
   * `int id;`            // unique Book ID  
   * `float position;`   // distance in centimeters from the left end of the shelf  
3. **Populates** the array: for each book the user enters the `id` and the initial `position`.  
4. **Provides a menu** (displayed after the initial input) with the following options:  
   1. **Display a book** – the user enters a Book ID, and the program prints the ID and its current position.  
   2. **Shift a range** – the user enters three values: `startID`, `endID`, and `delta`.  
      * All books whose IDs are **between** `startID` and `endID` inclusive must have their `position` increased by `delta` centimeters.  
      * The update must be performed by traversing the array with pointer arithmetic (i.e., using `*ptr`, `ptr++`, `ptr + k`, etc.).  
   3. **Exit** – terminates the program.  

The menu must repeat after each operation until the user selects **Exit**.  

## Example Input / Output  

```
Enter number of books: 3
Book 1 – ID: 101  Position: 12.5
Book 2 – ID: 205  Position: 45.0
Book 3 – ID: 150  Position: 30.2

--- MENU ---
1) Display a book
2) Shift a range
3) Exit
Choose an option: 1
Enter Book ID to display: 150
Book ID: 150, Position: 30.20 cm

--- MENU ---
1) Display a book
2) Shift a range
3) Exit
Choose an option: 2
Enter start ID: 100
Enter end ID: 200
Enter shift amount (cm): 5.0
Positions updated.

--- MENU ---
1) Display a book
2) Shift a range
3) Exit
Choose an option: 1
Enter Book ID to display: 150
Book ID: 150, Position: 35.20 cm

--- MENU ---
1) Display a book
2) Shift a range
3) Exit
Choose an option: 3
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct Book` as described above.  
* **Function Requirement** – The logic for displaying the details of **ONE** specific book must reside in a function named `void displayBook(struct Book *books, int count, int targetID);`. This function must use pointer arithmetic to locate the requested book.  
* **Pointer‑Only Traversal** – All traversals of the dynamic array (both in `displayBook` and in the range‑shift operation) must use pointer arithmetic; the subscript operator `[]` is **not** allowed anywhere in the program.  
* **Menu Exit Option** – The menu must include an explicit option to **Exit** the program, numbered `3` in the example above.  

*Optional but recommended*: Validate user input (e.g., ensure the entered Book ID exists) and handle the case where no books fall within the specified shift range.

---

## Problem 43 - openai/gpt-oss-120b - Iteration 63
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is described by a small record containing the book’s ISBN (as a 13‑digit integer), the number of copies currently on the shelf, and a short title (max 30 characters). The library wants a simple console program that can store up to **N** books (where *N* is entered by the user at run‑time) and allow the librarian to perform basic operations using **pointers and pointer arithmetic** only (no index‑based array access).

## Requirements  
Write a C program that fulfills the following functionality:

1. **Initialisation** – Prompt the user for the maximum number of books `N`. Dynamically allocate an array of `N` `Book` structures using `malloc`.  
2. **Menu‑driven interface** – Repeatedly present the librarian with a menu that includes the following options:  
   1. **Add a new book** – Prompt for ISBN, title, and number of copies, then store the information in the first free slot of the array. If the array is full, display an appropriate message.  
   2. **Update copies** – Ask for an ISBN; locate the matching book using pointer arithmetic (do **not** use `[]`). If found, ask for the new number of copies and update the record; otherwise report “Book not found”.  
   3. **Display a book** – Ask for an ISBN and display all fields of the matching book by calling a helper function `displayBook`. If the ISBN does not exist, report “Book not found”.  
   4. **List all books** – Walk through the entire array using pointer arithmetic and print each stored book’s details.  
   5. **EXIT** – Terminate the program, freeing any allocated memory.  

3. **Error handling** – The program must gracefully handle invalid menu choices, duplicate ISBNs on insertion, and attempts to update or display a non‑existent book.

## Example Input / Output  

```
Enter maximum number of books: 3

--- Library Menu ---
1) Add a new book
2) Update copies
3) Display a book
4) List all books
5) EXIT
Choose an option: 1
Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies on shelf: 4
Book added successfully.

--- Library Menu ---
1) Add a new book
2) Update copies
3) Display a book
4) List all books
5) EXIT
Choose an option: 1
Enter ISBN (13 digits): 9780262033848
Enter title: Introduction to Algorithms
Enter copies on shelf: 2
Book added successfully.

--- Library Menu ---
1) Add a new book
2) Update copies
3) Display a book
4) List all books
5) EXIT
Choose an option: 3
Enter ISBN to display: 9780131103627

ISBN: 9780131103627
Title: The C Programming Language
Copies: 4

--- Library Menu ---
1) Add a new book
2) Update copies
3) Display a book
4) List all books
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct` named `Book` with the fields `unsigned long long isbn; char title[31]; int copies;`.  
- **Function Requirement** – The logic for displaying the details of **ONE specific book** must be placed in a separate function with the exact prototype:  

  ```c
  void displayBook(const Book *b);
  ```  

- **Pointer‑Only Traversal** – All traversals of the dynamically allocated array must use **pointer arithmetic** (`ptr`, `ptr + 1`, etc.). Direct indexing with `array[i]` is **not allowed**.  
- **Menu Requirement** – The program must present a textual menu as described above, and **option 5 must be the EXIT command** (the number “5” is mandatory).  
- **Memory Management** – The program must free the dynamically allocated array before terminating.  

*All other design decisions are left to the student.*

---

## Problem 44 - openai/gpt-oss-120b - Iteration 64
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑tracking system. Each bus is equipped with a GPS device that periodically records its current location (latitude and longitude) and the distance (in meters) it has traveled since the last report. The authority wants a simple console program that stores a collection of bus records, lets the user add new reports, and can display the details of any single bus on demand.

## Requirements  
Write a C program that:

1. **Defines a `struct`** called `BusReport` containing:  
   - `int id;`               // unique bus identifier  
   - `double latitude;`  
   - `double longitude;`  
   - `int distance;`         // meters travelled since previous report  

2. **Stores up to 100 `BusReport` objects** in a dynamically allocated array (use `malloc`).  

3. **Provides a text‑based menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
   1. **Add a new bus report** – Prompt for the bus id, latitude, longitude, and distance, then store the record at the next free slot.  
   2. **Display a bus report** – Prompt for a bus id, locate the first record with that id, and invoke a function `displayEntity` to print its contents. If the id is not found, print “Bus not found.”  
   3. **Show total distance** – Compute and print the sum of the `distance` fields of all stored reports.  
   4. **EXIT** – Terminate the program gracefully, freeing any allocated memory.  

4. **Implements the display logic** in a separate function with the exact prototype:  

   ```c
   void displayEntity(const BusReport *b);
   ```

   This function must print the bus report in the format:  

   ```
   Bus ID: <id>
   Location: (<latitude>, <longitude>)
   Distance since last report: <distance> meters
   ```

5. **Uses pointer arithmetic** (not array indexing) to traverse the dynamically allocated array when adding, searching, and summing distances.

6. **Validates input** minimally: if the user tries to add more than 100 reports, display “Report storage full.” and return to the menu.

## Example Interaction  

```
=== Bus Tracking System ===
1. Add a new bus report
2. Display a bus report
3. Show total distance
4. EXIT
Choose an option: 1

Enter Bus ID: 42
Enter latitude: 37.7749
Enter longitude: -122.4194
Enter distance (m): 150
Report added.

=== Bus Tracking System ===
1. Add a new bus report
2. Display a bus report
3. Show total distance
4. EXIT
Choose an option: 1

Enter Bus ID: 7
Enter latitude: 34.0522
Enter longitude: -118.2437
Enter distance (m): 200
Report added.

=== Bus Tracking System ===
1. Add a new bus report
2. Display a bus report
3. Show total distance
4. EXIT
Choose an option: 2

Enter Bus ID to display: 42
Bus ID: 42
Location: (37.7749, -122.4194)
Distance since last report: 150 meters

=== Bus Tracking System ===
1. Add a new bus report
2. Display a bus report
3. Show total distance
4. EXIT
Choose an option: 3

Total distance reported by all buses: 350 meters

=== Bus Tracking System ===
1. Add a new bus report
2. Display a bus report
3. Show total distance
4. EXIT
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  
- The primary data entity **must be represented with a `struct`** named `BusReport`.  
- The function that prints a single bus’s details **must be named `displayEntity`** and accept a pointer to a `const BusReport`.  
- The program **must use pointer arithmetic** (e.g., `ptr + i`, `*(ptr + i)`) for all array traversals; direct indexing (`array[i]`) is not allowed.  
- The menu must include the **EXIT option numbered 4** as shown, and selecting it must end the program.  
- Only one additional helper function (`displayEntity`) is required; all other logic may reside in `main`.  

*Design the solution so that a student who has just learned pointers and pointer arithmetic can implement it without needing advanced language features.*

---

## Problem 45 - openai/gpt-oss-120b - Iteration 65
# STEP 1: PROBLEM  

## Background  
The campus library has just digitised its catalogue. Each book is stored as a record that contains the book’s **ISBN**, **title**, and **number of copies** available. The catalogue is kept in a dynamically‑allocated array of these records.  

Your task is to write a small console program that lets a librarian **add**, **search**, and **list** books by manipulating the array only through pointers and pointer arithmetic. The program must demonstrate that you understand how to work with pointers, pointer arithmetic, and `struct`s in C (or C++).

---

## Requirements  

1. **Data structure**  
   * Define a `struct Book` with the following members:  
     ```c
     char isbn[14];   // 13‑digit ISBN plus terminating '\0'
     char title[51];  // up to 50 characters + '\0'
     int  copies;
     ```  

2. **Dynamic storage**  
   * At program start, allocate space for **10** `Book` records using `malloc` (or `new` in C++).  
   * Keep track of the *current* number of books stored (`size`).  

3. **Menu‑driven interface** (the program must present a menu and repeat until the user chooses to exit)  

   | Option | Action |
   |--------|--------|
   | 1      | **Add a new book** – read ISBN, title, and copies, store the data at the first free slot using pointer arithmetic (`*(books + i)`). If the array is full, display a message and refuse the addition. |
   | 2      | **Search by ISBN** – prompt for an ISBN, scan the array with a pointer, and if a matching book is found, call `displayBook` (see Constraint) to show its details; otherwise print “Book not found”. |
   | 3      | **List all books** – traverse the array with a pointer and print each stored record. |
   | 4      | **EXIT** – terminate the program (must be the exact keyword/number shown in the menu). |

4. **Functions**  
   * Implement a function `void displayBook(const struct Book *b)` that receives a pointer to a single `Book` and prints its ISBN, title, and number of copies in a readable format.  
   * No other helper functions are required, but you may add them if you wish; the only *mandatory* extra function besides `main` is `displayBook`.  

5. **Input validation**  
   * Assume the user enters data of the correct type; you do not need to handle malformed input beyond checking for a full array when adding a book.  

6. **Memory cleanup**  
   * Before exiting, free the dynamically allocated array.

---

## Example Interaction  

```
=== Library Catalogue ===
1. Add a new book
2. Search by ISBN
3. List all books
4. EXIT
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added successfully.

=== Library Catalogue ===
1. Add a new book
2. Search by ISBN
3. List all books
4. EXIT
Choose an option: 2

Enter ISBN to search: 9780131103627
--- Book Details ---
ISBN   : 9780131103627
Title  : The C Programming Language
Copies : 4

=== Library Catalogue ===
1. Add a new book
2. Search by ISBN
3. List all books
4. EXIT
Choose an option: 3

--- All Books ---
[0] ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Catalogue ===
1. Add a new book
2. Search by ISBN
3. List all books
4. EXIT
Choose an option: 4

Goodbye!
```

---

### CONSTRAINTS  

* **Must use a `struct`** named `Book` to represent each catalogue entry.  
* The logic for displaying the details of **ONE specific book** must be placed in a function called **`displayBook`** that receives a pointer to `Book`.  
* The program must be **menu‑driven** and **must include an option to EXIT** the program (option 4 in the example).  
* All accesses to the dynamic array of books must be performed using **pointer arithmetic** (e.g., `*(books + i)`, `books + i`, `ptr++`, etc.). No array‑indexing syntax (`books[i]`) is allowed for reading or writing book records.  

Feel free to add any additional helper functions, but the above constraints are mandatory. Good luck!

---

## Problem 46 - openai/gpt-oss-120b - Iteration 66
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernising its catalogue system.  Each book in the catalogue is represented by a small record containing the book’s ISBN, title, number of copies owned, and the price per copy.  The library wants a simple console program that lets a librarian **add new books**, **update the number of copies**, **look up a single book**, and **list every book** currently stored.  

You have just finished the unit on *Pointers and Pointer Arithmetic*.  The librarian’s program must store the book records in a dynamically‑allocated array and must manipulate that array **exclusively with pointer arithmetic** (i.e., you may not use the subscript operator `[]` to walk through the array).  

## Requirements  

1. **Data structure**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating `\0`  
     - `char title[51];`  // up to 50 characters + `\0`  
     - `int copies;`  
     - `float price;`  

2. **Dynamic storage**  
   * At program start, ask the user for the maximum number of books the catalogue will hold (`capacity`).  
   * Allocate a single block of memory large enough to hold `capacity` `struct Book` objects using `malloc`.  

3. **Menu (repeated until the user chooses to exit)**  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a new book** – Prompt for ISBN, title, copies, and price. Store the new record at the first unused slot. If the catalogue is full, print an error message. |
   | 2 | **Update copies** – Prompt for an ISBN, locate the matching book, then ask for the new number of copies and store it. If the ISBN is not found, print “Book not found”. |
   | 3 | **Display a book** – Prompt for an ISBN and show all fields of that book (use the function `displayBook`). If the ISBN is not found, print “Book not found”. |
   | 4 | **List all books** – Walk through the whole array and display every stored book (again using `displayBook`). |
   | 5 | **EXIT** – Terminate the program. |

4. **Pointer‑only traversal**  
   * When adding, searching, updating, or listing books, you must move through the array using pointer arithmetic (`ptr = ptr + 1;`, `ptr = base + i;`, etc.). **Do not use the array subscript operator (`[]`) for any traversal or element access.** Direct field access through a pointer (e.g., `ptr->copies`) is allowed.  

5. **Function requirement**  
   * Implement a function  

     ```c
     void displayBook(const struct Book *b);
     ```  

     that prints a single book in the format shown in the example below. All menu options that need to show a book must call this function.  

6. **Graceful termination**  
   * Before exiting, free any memory allocated with `malloc`.  

## Example Interaction  

```
Enter maximum number of books the catalogue can hold: 3

--- Library Catalogue Menu ---
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. EXIT
Choose an option: 1
Enter ISBN (13 chars): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 5
Enter price: 45.99
Book added successfully.

--- Library Catalogue Menu ---
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. EXIT
Choose an option: 1
Enter ISBN (13 chars): 9780201633610
Enter title: Design Patterns
Enter number of copies: 2
Enter price: 54.50
Book added successfully.

--- Library Catalogue Menu ---
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. EXIT
Choose an option: 3
Enter ISBN to display: 9780131103627

ISBN : 9780131103627
Title: The C Programming Language
Copies: 5
Price : $45.99

--- Library Catalogue Menu ---
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. EXIT
Choose an option: 4

ISBN : 9780131103627
Title: The C Programming Language
Copies: 5
Price : $45.99

ISBN : 9780201633610
Title: Design Patterns
Copies: 2
Price : $54.50

--- Library Catalogue Menu ---
1. Add a new book
2. Update copies
3. Display a book
4. List all books
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Book`.  
* **Function name** – The routine that prints a single book must be named `displayBook` and have the prototype shown above.  
* **Pointer arithmetic only** – Traversal of the dynamically allocated array must be performed with pointer arithmetic; the `[]` operator is prohibited for any loop that walks the array.  
* **Menu exit** – The menu must include option **5. EXIT** (or the keyword “EXIT”) that terminates the program.  
* **Single additional function** – Apart from `main`, the only other user‑defined function may be `displayBook`. (All other logic must remain in `main`.)  

Design the problem so that students can demonstrate their understanding of dynamic memory allocation, structs, pointer arithmetic, and modular code organization.

---

## Problem 47 - openai/gpt-oss-120b - Iteration 67
# STEP 1: PROBLEM  

## Background  
The campus library is digitising its catalogue. Each book is stored as a record containing its ISBN, title, and the number of copies available. The library staff wants a small console program that can **add**, **search**, and **list** books. Because the staff is learning C, the assignment must demonstrate the use of pointers, pointer arithmetic, and structures.

## Requirements  

Write a C program that fulfills the following specifications:

1. **Data Representation**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[51];` // up to 50 characters plus terminating null  
     - `int copies;`  

2. **Dynamic Storage**  
   * Allocate an array of `struct Book` dynamically (using `malloc`).  
   * The maximum number of books the program can hold is **100**.  

3. **Menu‑driven Interface** (the program must present a menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new book** – prompt for ISBN, title, and copies, then store it at the first free slot. |
   | 2      | **Search by ISBN** – ask for an ISBN, locate the matching record, and display its details. |
   | 3      | **List all books** – display every stored book in the order they were added. |
   | 4      | **Exit** – terminate the program. *(MANDATORY EXIT OPTION)* |

4. **Pointer Arithmetic**  
   * All traversals of the book array (adding, searching, listing) **must be performed using pointer arithmetic** (e.g., `ptr = base + i;`), **not** by indexing (`array[i]`).  

5. **Display Function**  
   * Implement a function `void displayBook(const struct Book *b);` that prints a single book in the format:  
     ```
     ISBN: <isbn>, Title: "<title>", Copies: <copies>
     ```
   * The search option (2) must call `displayBook` to show the found record.  

6. **Input Validation**  
   * If the user attempts to add a book when the array is full, print an informative message and return to the menu.  
   * If a search yields no result, print “Book not found.”  

7. **Program Termination**  
   * Before exiting, free any dynamically allocated memory.

## Example Interaction  

```
--- Library Catalogue ---
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added successfully!

--- Library Catalogue ---
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780201633610
Enter title: Design Patterns
Enter copies: 2
Book added successfully!

--- Library Catalogue ---
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 2

Enter ISBN to search: 9780201633610
ISBN: 9780201633610, Title: "Design Patterns", Copies: 2

--- Library Catalogue ---
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 3

ISBN: 9780131103627, Title: "The C Programming Language", Copies: 4
ISBN: 9780201633610, Title: "Design Patterns", Copies: 2

--- Library Catalogue ---
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

1. **Structure Requirement** – The primary data entity must be represented by a `struct Book`.  
2. **Function Requirement** – The details of a single book must be displayed by a function named `displayBook`.  
3. **Pointer‑Arithmetic Requirement** – All array traversals must use pointer arithmetic; direct indexing (`books[i]`) is prohibited.  
4. **Menu Requirement** – The program must present a menu and **must include an explicit “Exit” option (option 4)** that terminates the program.  

*All other aspects of the program (e.g., variable names, helper functions) are left to the student’s design.*

---

## Problem 48 - openai/gpt-oss-120b - Iteration 68
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science department wants a tiny console‑based “Student Registry” that stores information about a limited number of students in memory while the program runs.  
Each student record contains a **student ID** (an integer), a **name** (a string of up to 30 characters), and a **GPA** (a `float`).  
The instructor has just taught you how to work with pointers, pointer arithmetic, and `struct`s, and asks you to implement the registry using only dynamic memory allocation (no global arrays).

## Requirements  

Write a C program that performs the following actions, selectable through a simple text menu:

1. **Add a student** – Prompt the user for ID, name, and GPA, allocate a new `Student` structure on the heap, and store the pointer in a dynamically‑managed array of pointers.  
2. **List all students** – Walk through the array using pointer arithmetic (i.e., increment a `Student **` pointer) and print each student’s data.  
3. **Find a student by ID** – Search the array (again using pointer arithmetic) for a matching ID and, if found, display that student’s details.  
4. **Delete a student by ID** – Locate the student, free its memory, and shift the remaining pointers so that the array stays compact.  
5. **Exit** – Terminate the program gracefully, freeing any remaining allocated memory.

The program should continue to display the menu after each operation until the user chooses the **Exit** option.

### Detailed functional specifications  

- The maximum number of students that can be stored at any time is **100**.  
- The array that holds the pointers to `Student` structures must be allocated dynamically (e.g., `Student **registry = malloc(100 * sizeof(Student *));`).  
- All traversal of the registry must be performed with pointer arithmetic; **do not** use array indexing (`registry[i]`) for the core loops.  
- Input validation:  
  * Student IDs must be positive integers and unique; if a duplicate ID is entered, print an error and discard the entry.  
  * GPA must be in the range `0.0` – `4.0`; otherwise, print an error and discard the entry.  
- When the user selects “Find a student by ID”, the program must call a function `displayEntity` that receives a pointer to a `Student` and prints its fields.  

## Example Input / Output  

```
=== Student Registry Menu ===
1. Add student
2. List all students
3. Find student by ID
4. Delete student by ID
5. Exit
Choose an option: 1

Enter student ID: 1024
Enter name (max 30 chars): Alice Johnson
Enter GPA (0.0 - 4.0): 3.7
Student added successfully.

=== Student Registry Menu ===
1. Add student
2. List all students
3. Find student by ID
4. Delete student by ID
5. Exit
Choose an option: 1

Enter student ID: 2048
Enter name (max 30 chars): Bob Smith
Enter GPA (0.0 - 4.0): 2.9
Student added successfully.

=== Student Registry Menu ===
1. Add student
2. List all students
3. Find student by ID
4. Delete student by ID
5. Exit
Choose an option: 2

--- All Students ---
ID: 1024 | Name: Alice Johnson | GPA: 3.70
ID: 2048 | Name: Bob Smith     | GPA: 2.90

=== Student Registry Menu ===
1. Add student
2. List all students
3. Find student by ID
4. Delete student by ID
5. Exit
Choose an option: 3

Enter ID to search: 1024
--- Student Details ---
ID: 1024
Name: Alice Johnson
GPA: 3.70

=== Student Registry Menu ===
1. Add student
2. List all students
3. Find student by ID
4. Delete student by ID
5. Exit
Choose an option: 5

Exiting program. Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented by a `struct Student` containing the three fields (ID, name, GPA).  
2. **Display function** – The logic for showing the details of a single student must be placed in a function with the exact prototype:  

   ```c
   void displayEntity(const struct Student *s);
   ```  

3. **Pointer arithmetic only** – When iterating over the registry (adding, listing, searching, deleting), you must use a `Student **` pointer and increment it (`ptr++`) rather than array indexing.  
4. **Menu requirement** – The program must present a textual menu as shown above, and **option 5 must be the explicit “Exit” command** that ends the loop and frees all allocated memory.  
5. **Single‑function restriction** – Apart from `main()` and `displayEntity()`, you may create additional helper functions **only if they are static and not used for the core traversal logic** (e.g., input validation). The traversal itself must stay within `main()` or a dedicated “registry management” function.  

Your solution should compile with a standard C compiler (`gcc -std=c11`) and run without memory leaks (use tools like `valgrind` to verify).

---

## Problem 49 - openai/gpt-oss-120b - Iteration 69
# STEP 1: PROBLEM  

## Background  
The coastal kingdom of **C‑Bay** maintains a linear list of islands that are connected by a narrow sea‑lane.  
Each island has a name and a hidden amount of treasure (in gold coins).  
The kingdom’s archivist stores the islands in a contiguous block of memory (an array) so that a sailor can “walk” from one island to the next simply by incrementing a pointer.

Your task is to write a small console program that lets a user explore this island list using **pointers and pointer arithmetic**. The program must demonstrate how a pointer can be moved forward and backward through an array, and how the data behind the pointer can be accessed.

## Requirements  

1. **Data Representation**  
   * Define a `struct Island` that contains:  
     ```c
     char name[32];   // null‑terminated name of the island
     int  treasure;   // amount of gold coins hidden on the island
     ```  

2. **Program Functionality**  
   * At start‑up, the program should create (statically or dynamically) an array of **exactly 7** `Island` objects with any names and treasure values you like.  
   * The program presents a **menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

     1. **Show current island** – display the name and treasure of the island that the *current pointer* is pointing to.  
     2. **Move forward _k_ islands** – ask the user for a positive integer `k` and advance the pointer by `k` positions using pointer arithmetic. If the movement would go past the last island, wrap around to the beginning of the array (circular navigation).  
     3. **Move backward _k_ islands** – similar to (2) but move the pointer backward; wrap around to the end if necessary.  
     4. **Show total treasure from current to end** – compute and display the sum of `treasure` values for all islands starting at the current pointer and continuing to the last island in the array (do **not** wrap). Use pointer arithmetic to traverse the range.  
     5. **EXIT** – terminate the program.  

   * All navigation must be performed **exclusively with pointers** (no array indexing `[]` inside the navigation logic).  

3. **Helper Function**  
   * Implement a function `void displayIsland(const Island *p)` that receives a pointer to an `Island` and prints its `name` and `treasure` in a readable format. This function must be used for menu option 1.  

4. **Robustness**  
   * The program should validate menu choices and the integer `k` entered for movement (reject non‑positive values).  
   * If the user enters an invalid menu option, display an error message and re‑show the menu.  

## Example Interaction  

```
=== C‑Bay Island Explorer ===
Current island: Island 0 (Treasure: 120)

Menu:
1) Show current island
2) Move forward k islands
3) Move backward k islands
4) Show total treasure from current to end
5) EXIT
Enter choice: 2
Enter k (positive integer): 3
Moved forward 3 islands.

Menu:
1) Show current island
2) Move forward k islands
3) Move backward k islands
4) Show total treasure from current to end
5) EXIT
Enter choice: 1
Island: Coral Reef
Treasure: 85 gold coins

Menu:
1) Show current island
2) Move forward k islands
3) Move backward k islands
4) Show total treasure from current to end
5) EXIT
Enter choice: 4
Total treasure from "Coral Reef" to the last island: 342 gold coins

Menu:
1) Show current island
2) Move forward k islands
3) Move backward k islands
4) Show total treasure from current to end
5) EXIT
Enter choice: 5
Good‑bye!
```

*(The exact island names and treasure amounts may differ; the example only illustrates the flow.)*  

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Island`.  
* **Display Function** – The details of a single island must be printed by a function named `displayIsland`.  
* **Pointer‑Only Navigation** – Inside the navigation and summation logic you may **not** use the subscript operator `[]`; you must use pointer arithmetic (`p + i`, `p - i`, `*(p + i)`, etc.).  
* **Menu Structure** – Because a menu is used, the program **must** include an explicit option to **EXIT** (option 5 in the example).  

---  

Design and implement the program according to the specifications above. The focus is on correct use of pointers, pointer arithmetic, and struct handling in C (or C‑compatible C++). Good luck!

---

## Problem 50 - openai/gpt-oss-120b - Iteration 70
# STEP 1: PROBLEM  

## Background  
The university’s archaeology department maintains a small digital catalogue of artifacts that have been loaned to the campus museum. Each artifact is described by an identification number, a short name, the year it was created, and its estimated monetary value.  

You have been asked to write a C program that stores this catalogue in memory using **dynamic allocation** and **pointer arithmetic**. The program will later be extended to support more sophisticated queries, so it must be written in a clean, modular way.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Artifact` that holds the following fields:  
     - `int id;`      // unique identifier  
     - `char name[31];` // up to 30 characters + terminating null  
     - `int year;`    // year of creation (e.g., 1845)  
     - `float value;`  // estimated value in dollars  

2. **Input**  
   * At program start, read an integer `n` (1 ≤ n ≤ 100) – the number of artifacts to store.  
   * For each artifact, read the four fields in the order **id name year value**, separated by whitespace.  
   * Example line: `1023 "BronzeStatue" 1500 12500.50` (the name will be a single word, no spaces).

3. **Dynamic storage**  
   * Allocate a contiguous block of memory sufficient to hold `n` `struct Artifact` objects using `malloc`.  
   * Use **pointer arithmetic** (e.g., `ptr + i`) to access individual elements; do **not** use array‑subscript notation (`arr[i]`).

4. **Menu‑driven interface** (the program must present a menu after the data are loaded)  
   * The menu must contain the following options (the user selects by entering the shown number):  

     ```
     1) Display an artifact by ID
     2) List all artifacts created before a given year
     3) Compute and display the average value of all artifacts
     4) EXIT
     ```  

   * The program must loop until the user chooses option **4** (EXIT).  

5. **Option details**  

   * **1) Display an artifact by ID**  
     - Prompt: `Enter artifact ID:`  
     - Search the dynamically‑allocated array using pointer arithmetic.  
     - If the artifact is found, call a function `void displayArtifact(const struct Artifact *p)` to print its details in the format:  

       ```
       ID: 1023, Name: BronzeStatue, Year: 1500, Value: $12500.50
       ```  

     - If not found, print `Artifact with ID <id> not found.`  

   * **2) List all artifacts created before a given year**  
     - Prompt: `Enter year:`  
     - Traverse the array with pointer arithmetic and print each matching artifact using `displayArtifact`.  
     - If none match, print `No artifacts found before <year>.`  

   * **3) Compute and display the average value**  
     - Compute the arithmetic mean of the `value` field of all stored artifacts.  
     - Print `Average value: $<average>` with two digits after the decimal point.  

6. **Cleanup**  
   * Before terminating, free the memory allocated for the artifact array.

---

## Example Input / Output  

```
Enter number of artifacts: 3
1023 BronzeStatue 1500 12500.50
2045 SilverCoin   1800  850.75
3078 ClayVase     1705  430.00

--- MENU ---
1) Display an artifact by ID
2) List all artifacts created before a given year
3) Compute and display the average value of all artifacts
4) EXIT
Choose an option: 1
Enter artifact ID: 2045
ID: 2045, Name: SilverCoin, Year: 1800, Value: $850.75

--- MENU ---
1) Display an artifact by ID
2) List all artifacts created before a given year
3) Compute and display the average value of all artifacts
4) EXIT
Choose an option: 2
Enter year: 1750
ID: 1023, Name: BronzeStatue, Year: 1500, Value: $12500.50
ID: 3078, Name: ClayVase, Year: 1705, Value: $430.00

--- MENU ---
1) Display an artifact by ID
2) List all artifacts created before a given year
3) Compute and display the average value of all artifacts
4) EXIT
Choose an option: 3
Average value: $4593.08

--- MENU ---
1) Display an artifact by ID
2) List all artifacts created before a given year
3) Compute and display the average value of all artifacts
4) EXIT
Choose an option: 4
Goodbye!
```

---

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Artifact`.  
* **Function requirement** – The logic for displaying the details of **ONE** specific artifact must reside in a function named `void displayArtifact(const struct Artifact *p)`.  
* **Pointer arithmetic only** – Access to the dynamically allocated array must be performed with pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.). Do **not** use the array subscript operator (`[]`).  
* **Menu exit option** – The menu must include a distinct option (`4`) that terminates the program.  

---  

*Write the program fulfilling all the above specifications.*

---

## Problem 51 - openai/gpt-oss-120b - Iteration 71
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book is stored in memory as a record that contains the ISBN, the title, and the number of copies currently on the shelf. The library’s junior programmer has been asked to write a small C program that lets a librarian **add**, **remove**, **search**, and **display** books using only pointer arithmetic (no array indexing `[]`). The program must manipulate the collection of books directly through pointers, demonstrating the students’ recent lessons on pointer arithmetic and `struct` handling.

## Requirements  
Write a console‑based C program that fulfills the following functional requirements:

1. **Data Representation**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating `\0`  
     - `char title[51];`  // up to 50 characters plus `\0`  
     - `int  copies;`  

2. **Dynamic Collection**  
   * The program must allocate a contiguous block of memory large enough to hold **up to 100** `struct Book` objects using `malloc`.  
   * Keep track of the current number of books stored (`size`).  

3. **Menu‑Driven Interface** (the menu must include an explicit “Exit” option)  
   * **1 – Add a Book**  
     - Prompt for ISBN, title, and copies.  
     - Store the new record at the end of the current collection using only pointer arithmetic (`*(ptr + i)`).  
     - Do not allow more than 100 books; display an error if the collection is full.  
   * **2 – Remove a Book**  
     - Prompt for an ISBN.  
     - Locate the matching record using pointer arithmetic.  
     - If found, shift all subsequent records left to fill the gap (again, only pointer arithmetic).  
     - Decrease `size`. If not found, display “Book not found.”  
   * **3 – Search for a Book**  
     - Prompt for an ISBN.  
     - Locate the record using pointer arithmetic.  
     - If found, call `displayEntity` (see Constraint) to show its details; otherwise print “Book not found.”  
   * **4 – List All Books**  
     - Iterate through the collection using pointer arithmetic and print each book’s details on a separate line.  
   * **5 – Exit**  
     - Free any allocated memory and terminate the program.  

4. **Input Validation**  
   * ISBN must be exactly 13 characters (ignore hyphens).  
   * Number of copies must be a non‑negative integer.  

5. **Program Structure**  
   * Aside from `main`, the solution must contain **exactly one additional function** named `displayEntity` that receives a pointer to a `struct Book` and prints the ISBN, title, and copies in a readable format.  

## Example Interaction  

```
=== Library Inventory System ===
1. Add a Book
2. Remove a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added successfully.

=== Library Inventory System ===
1. Add a Book
2. Remove a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 4

ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Inventory System ===
1. Add a Book
2. Remove a Book
3. Search for a Book
4. List All Books
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Function Requirement** – All logic for displaying the details of **one** specific book must reside in a function named `displayEntity`. Its prototype must be:  

  ```c
  void displayEntity(const struct Book *b);
  ```  

* **Pointer‑Only Access** – Inside the program (including `displayEntity`), you may **not** use the array subscript operator `[]`. Access every `struct Book` element exclusively with pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.).  
* **Single Auxiliary Function** – Apart from `main`, only the `displayEntity` function may be defined. No other helper functions are permitted.  
* **Menu Exit Option** – The menu must contain a clearly labeled option (number **5**) to **Exit** the program, as shown in the example.  

Your task is to write the full problem description above; the actual implementation will be completed by the students.

---

## Problem 52 - openai/gpt-oss-120b - Iteration 72
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book in the collection is stored in an array of **`Book`** structures. The library wants a small console program that lets a librarian **add**, **list**, and **search** for books using only pointer arithmetic (no array indexing `[]`). This will give students practice with pointers, pointer arithmetic, and the use of `struct`s.

## Requirements  

1. **Data structure**  
   * Define a `struct Book` that contains:  
     - `char title[51];`   // up to 50 characters + terminating null  
     - `char author[51];`  
     - `int  year;`  

2. **Program functionality** (menu‑driven)  
   * **1 – Add a book**  
     - Prompt the user for title, author, and publication year.  
     - Store the new book at the next free position in the array (maximum 100 books).  
   * **2 – List all books**  
     - Traverse the array using only pointer arithmetic and print each book’s details on a separate line.  
   * **3 – Find a book by title**  
     - Prompt for a title string.  
     - Search the array (pointer arithmetic only) for the first book whose title matches exactly (case‑sensitive).  
     - If found, display the book’s details; otherwise print “Book not found.”  
   * **0 – Exit**  
     - Terminates the program.  

3. **User interaction**  
   * After completing any operation (except Exit), the menu should be shown again.  
   * Input validation is not required beyond the constraints described.  

## Example Input / Output  

```
--- Library Inventory ---
1) Add a book
2) List all books
3) Find a book by title
0) EXIT
Choose an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Book added.

--- Library Inventory ---
1) Add a book
2) List all books
3) Find a book by title
0) EXIT
Choose an option: 1

Enter title: Clean Code
Enter author: Robert Martin
Enter year: 2008
Book added.

--- Library Inventory ---
1) Add a book
2) List all books
3) Find a book by title
0) EXIT
Choose an option: 2

0: Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1978
1: Title: Clean Code               | Author: Robert Martin          | Year: 2008

--- Library Inventory ---
1) Add a book
2) List all books
3) Find a book by title
0) EXIT
Choose an option: 3

Enter title to search: Clean Code
Found:
Title: Clean Code | Author: Robert Martin | Year: 2008

--- Library Inventory ---
1) Add a book
2) List all books
3) Find a book by title
0) EXIT
Choose an option: 0

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented with a `struct Book`.  
2. **Pointer arithmetic only** – When accessing or iterating through the array of `Book`s, you **must not** use the subscript operator `[]`. Use pointers (`Book *p = books;`, `p++`, `*(p + i)`, etc.).  
3. **Display function** – The logic for printing the details of a **single** `Book` must reside in a function with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```

   This function may be called from the listing and searching options.  
4. **Menu requirement** – The program must present a menu as described, and option **0** must be the explicit “EXIT” choice that terminates the program.  

*All other helper functions are optional, but the above constraints are mandatory.*

---

## Problem 53 - openai/gpt-oss-120b - Iteration 73
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science Lab maintains a small inventory of **lab equipment** (e.g., microscopes, oscilloscopes, soldering stations). Each item has a unique **ID**, a **name**, and a **quantity** currently available. The lab manager wants a simple console program that stores the inventory in an array of structures and allows the manager to query the inventory using pointer arithmetic.

## Requirements  
Write a C program that:

1. **Defines** a `struct Equipment` containing:  
   * `int id;` – unique identifier (positive integer)  
   * `char name[30];` – null‑terminated string (no spaces)  
   * `int qty;` – number of units available  

2. **Creates** an array of `struct Equipment` with a maximum capacity of **10** items.  
   * The program should first read an integer `n` ( 1 ≤ n ≤ 10 ) – the number of equipment records to store.  
   * For each record, read the three fields (`id`, `name`, `qty`) from standard input.

3. **Displays a menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  

   ```
   1) List all equipment
   2) Find equipment by ID
   3) Exit
   ```

4. **Option 1 – List all equipment**  
   * Print each equipment record on its own line in the format:  
     `ID: <id>, Name: <name>, Qty: <qty>`  

5. **Option 2 – Find equipment by ID**  
   * Prompt the user for an integer `search_id`.  
   * Use **pointer arithmetic** (no array indexing `[]`) to scan the array and locate the record whose `id` matches `search_id`.  
   * If found, display the record using the function `displayEquipment` (see constraints).  
   * If not found, print `Equipment with ID <search_id> not found.`  

6. **Option 3 – Exit**  
   * Terminate the program gracefully.

## Example Input / Output  

```
Enter number of equipment items (max 10): 3
Enter ID, Name, Qty for item 1: 101 Microscope 5
Enter ID, Name, Qty for item 2: 202 Oscilloscope 2
Enter ID, Name, Qty for item 3: 303 SolderingStation 7

--- Menu ---
1) List all equipment
2) Find equipment by ID
3) Exit
Choose an option: 1

ID: 101, Name: Microscope, Qty: 5
ID: 202, Name: Oscilloscope, Qty: 2
ID: 303, Name: SolderingStation, Qty: 7

--- Menu ---
1) List all equipment
2) Find equipment by ID
3) Exit
Choose an option: 2
Enter ID to search: 202

ID: 202, Name: Oscilloscope, Qty: 2

--- Menu ---
1) List all equipment
2) Find equipment by ID
3) Exit
Choose an option: 2
Enter ID to search: 999
Equipment with ID 999 not found.

--- Menu ---
1) List all equipment
2) Find equipment by ID
3) Exit
Choose an option: 3
Goodbye!
```

### CONSTRAINTS  
1. **Struct Requirement** – The primary data entity must be represented by a `struct Equipment`.  
2. **Function Requirement** – The logic that displays the details of a single equipment record must be placed in a function with the exact prototype:  

   ```c
   void displayEquipment(const struct Equipment *e);
   ```

3. **Pointer‑Arithmetic Requirement** – In the search routine (Option 2), you **must not** use the subscript operator `[]`. Access array elements only via pointers and arithmetic (e.g., `ptr + i`).  
4. **Menu Requirement** – The menu must include the explicit “Exit” option numbered **3** as shown above. Selecting this option ends the program.  

---

## Problem 54 - openai/gpt-oss-120b - Iteration 74
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its bus‑stop information system. Each bus stop is identified by a numeric **stop ID**, has a **name** (up to 30 characters), and stores the **distance in meters** to the next stop on the route. The authority wants a small C program that can load a list of stops into memory, let the user query or modify the data, and demonstrate the use of pointers and pointer arithmetic to traverse the list.

## Requirements  

1. **Data representation**  
   * Define a `struct Stop` containing:  
     ```c
     int   id;                // unique stop identifier
     char  name[31];          // null‑terminated name (max 30 chars)
     int   distance_to_next; // meters to the next stop
     ```  
   * The program must allocate an array of `struct Stop` dynamically on the heap (using `malloc`).  

2. **Program functionality** (presented as a simple text menu)  
   * **(1) Load stops** – Prompt the user for the number of stops *n* (1 ≤ n ≤ 100) and then read *n* records (id, name, distance). Store them in the dynamically allocated array.  
   * **(2) Display a stop** – Ask for a stop ID and display the corresponding stop’s details. The lookup must be performed by iterating through the array using **pointer arithmetic only** (no array indexing `[]`).  
   * **(3) Update distance** – Ask for a stop ID and a new distance value, then modify the `distance_to_next` field of that stop, again using pointer arithmetic.  
   * **(4) List all stops** – Print the entire list in the order stored, traversing the array with pointer arithmetic.  
   * **(5) EXIT** – Terminate the program, freeing any allocated memory.  

3. **Input / Output**  
   * All prompts and messages should be clear and user‑friendly.  
   * If a requested stop ID does not exist, print an informative error message.  

### Example Interaction  

```
=== Bus Stop Manager ===
1. Load stops
2. Display a stop
3. Update distance
4. List all stops
5. EXIT
Choose an option: 1
Enter number of stops: 3
Stop 1 – ID: 101, Name: MainStreet, Distance to next: 250
Stop 2 – ID: 102, Name: OakAvenue, Distance to next: 180
Stop 3 – ID: 103, Name: PineLane, Distance to next: 0

=== Bus Stop Manager ===
1. Load stops
2. Display a stop
3. Update distance
4. List all stops
5. EXIT
Choose an option: 2
Enter stop ID to display: 102
Stop ID: 102
Name: OakAvenue
Distance to next: 180 meters

=== Bus Stop Manager ===
1. Load stops
2. Display a stop
3. Update distance
4. List all stops
5. EXIT
Choose an option: 3
Enter stop ID to update: 101
Enter new distance to next: 300
Distance updated.

=== Bus Stop Manager ===
1. Load stops
2. Display a stop
3. Update distance
4. List all stops
5. EXIT
Choose an option: 4
[0] ID:101 Name:MainStreet Distance:300
[1] ID:102 Name:OakAvenue Distance:180
[2] ID:103 Name:PineLane  Distance:0

=== Bus Stop Manager ===
1. Load stops
2. Display a stop
3. Update distance
4. List all stops
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by a `struct Stop` as described above.  
* **Pointer‑only traversal** – All array traversals (search, update, listing) must be performed using pointers and pointer arithmetic (`*ptr`, `ptr + i`, etc.). Direct indexing with `[]` is **not allowed** for these operations.  
* **Modular design** – The logic for displaying the details of ONE specific stop must be placed in a function with the exact prototype:  
  ```c
  void displayStop(const struct Stop *p);
  ```  
  This function will be called by the menu option “Display a stop”.  
* **Menu exit** – The menu must include option **5. EXIT** (or the keyword `EXIT`) that cleanly terminates the program.  

*Optional (but recommended for grading):*  
- Use a separate function to locate a stop by its ID, returning a pointer to the matching `struct Stop` (or `NULL` if not found).  

---  

Design the program to satisfy all the above requirements and constraints, demonstrating correct use of pointers, pointer arithmetic, dynamic memory management, and modular coding practices.

---

## Problem 55 - openai/gpt-oss-120b - Iteration 75
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library wants a tiny C program that lets a librarian **add**, **remove**, **search**, and **list** books using only pointer arithmetic (no array indexing `[]`). The program must keep the books in a dynamically‑allocated array that can grow as new titles are entered.

## Requirements  

Write a C program that fulfills the following functional specifications:

1. **Data Representation**  
   * Define a `struct Book` that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating `\0`  
     - `char title[101];` // up to 100 characters + `\0`  
     - `int copies;`  

2. **Dynamic Storage**  
   * Allocate an initial block of memory capable of holding **5** `Book` records.  
   * When the array becomes full, double its capacity with `realloc`. All pointer arithmetic must be performed with `Book *` pointers (no `[]`).

3. **Menu‑Driven Interface** (the program must present a menu and repeat until the user chooses to exit)  

   | Option | Action |
   |--------|--------|
   | 1      | **Add a new book** – read ISBN, title, and copies; store it at the first free slot. |
   | 2      | **Remove a book** – ask for an ISBN; if found, delete the record by shifting the later elements left (using pointer arithmetic). |
   | 3      | **Search for a book** – ask for an ISBN; if found, display the book’s details. |
   | 4      | **List all books** – display every stored book in the order they appear in the array. |
   | 5      | **EXIT** – terminate the program. |

4. **Display Function**  
   * Implement a function `void displayBook(const struct Book *b);` that prints a single book in the format:  
     `ISBN: <isbn>, Title: <title>, Copies: <copies>`  

5. **Input Validation**  
   * If the user tries to remove or search for a non‑existent ISBN, print an informative message.  

6. **Memory Management**  
   * Before exiting, free any memory allocated with `malloc`/`realloc`.

## Example Input / Output  

```
=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter copies: 3
Book added.

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 4
ISBN: 9780131103627, Title: The C Programming Language, Copies: 3

=== Library Inventory Menu ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be a `struct Book` as described.  
* **Function Requirement** – All logic that prints a single book’s details must be inside the function `displayBook`. No other function may directly use `printf` for a book.  
* **Pointer‑Only Access** – Access the dynamic array exclusively with pointer arithmetic (`*(ptr + i)`, `ptr++`, etc.). The use of the subscript operator `[]` on the book array is prohibited.  
* **Menu Exit** – The menu must contain option **5** labeled `EXIT`, which ends the program.  

Your solution should compile with a standard C compiler (e.g., `gcc -std=c11`).

---

## Problem 56 - openai/gpt-oss-120b - Iteration 76
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernizing its fleet of electric scooters. Each scooter is identified by a unique ID, has a current battery level (percentage), and stores the total distance it has travelled (in kilometers). The authority wants a small console program that lets a technician query and update the scooters while practicing pointer arithmetic.

## Requirements  

1. **Data Representation**  
   * Define a `struct Scooter` that contains:  
     * `int id;`      // unique identifier  
     * `float battery;`  // battery percentage (0.0 – 100.0)  
     * `float distance;` // total kilometres travelled  

2. **Program Functionality**  
   * The program must create an array of **exactly 5** `Scooter` objects, whose initial values are hard‑coded in the source code.  
   * The program presents a **menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
     1. **Display a scooter** – ask for a scooter ID and show all its fields.  
     2. **Charge a scooter** – ask for a scooter ID and a charge amount (percentage). Increase the battery, but never let it exceed 100 %.  
     3. **Ride a scooter** – ask for a scooter ID, a distance to ride (km), and the consumption rate (percentage per kilometre). Decrease the battery accordingly (if there is enough charge) and increase the travelled distance. If the battery would drop below 0 %, reject the ride and display an error.  
     4. **List all scooters** – print a table with the ID, battery, and distance of every scooter.  
     5. **EXIT** – terminate the program.  

3. **Pointer Arithmetic**  
   * All accesses to the scooter array **must be performed using pointer arithmetic** (e.g., `*(scooters + i)` or `scooters[i]` is acceptable, but you may not use the subscript operator on the array name alone).  
   * When searching for a scooter by ID, walk through the array using a pointer that you increment manually.

4. **Modular Design**  
   * The logic for displaying the details of **one** scooter must be placed in a function with the exact prototype:  
     ```c
     void displayScooter(const Scooter *p);
     ```  
   * All other menu actions may be implemented in additional helper functions if desired, but the program must contain **exactly one** function besides `main` that performs the display task described above.

## Example Interaction  

```
--- Scooter Management System ---
1. Display a scooter
2. Charge a scooter
3. Ride a scooter
4. List all scooters
5. EXIT
Choose an option: 4

ID   Battery%   Distance(km)
--------------------------------
101     85.0          120.5
102     40.0           78.2
103    100.0            0.0
104     60.5          210.3
105     30.0           55.0

--- Scooter Management System ---
1. Display a scooter
2. Charge a scooter
3. Ride a scooter
4. List all scooters
5. EXIT
Choose an option: 3
Enter scooter ID: 102
Enter distance to ride (km): 10
Enter consumption rate (% per km): 2.5
Ride accepted. New battery: 15.0%

--- Scooter Management System ---
1. Display a scooter
2. Charge a scooter
3. Ride a scooter
4. List all scooters
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Usage** – The primary data entity must be represented with a `struct Scooter`.  
* **Display Function** – The details of a single scooter must be printed by the function `void displayScooter(const Scooter *p);`.  
* **Pointer Arithmetic Only** – Direct array indexing (e.g., `scooters[i]`) is **not allowed** for traversing or locating scooters; you must use pointer arithmetic (`*(ptr + i)`, `ptr++`, etc.).  
* **Menu Requirement** – The menu must include option **5. EXIT** (or the word “EXIT”) that cleanly ends the program.  

---  

*Design the problem so that students can practice defining structs, passing pointers to functions, and navigating an array with pointer arithmetic while writing clear, modular code.*

---

## Problem 57 - openai/gpt-oss-120b - Iteration 77
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its inventory system. Every book in the collection is identified by an ISBN, has a title, and a count of how many copies are currently on the shelf. The library wants a small C program that stores the books in a dynamically‑allocated array and lets the user query the collection using pointer arithmetic only (no array indexing `[]`).  

## Requirements  
Write a program that:

1. **Defines a `struct Book`** containing  
   * `char isbn[14]`  – a null‑terminated string (13 characters plus the terminating `'\0'`).  
   * `char title[51]` – a null‑terminated string (max 50 characters).  
   * `int copies` – number of copies on the shelf.  

2. **Reads the initial inventory** from standard input:  
   * The first line contains an integer `N` (1 ≤ N ≤ 100) – the number of books.  
   * The next `N` lines each contain three fields separated by a single space: `ISBN TITLE COPIES`.  
   * `TITLE` will not contain spaces (use underscores `_` to represent spaces if needed).  

3. **Stores the books** in a single dynamically‑allocated block of memory (`malloc`/`calloc`). The pointer returned by the allocation must be used for all later accesses.  

4. **Provides a menu** that repeats until the user chooses to exit. The menu must contain the following options (the user enters the option number):  
   1. **Search by ISBN** – Prompt for an ISBN, locate the matching `Book` using pointer arithmetic, and display its details.  
   2. **List all books** – Traverse the array with pointer arithmetic and print every book.  
   3. **Update copies** – Prompt for an ISBN and a new integer value, locate the book, and replace its `copies` field.  
   4. **EXIT** – Terminate the program.  

5. **All traversals and look‑ups** must be performed with pointer arithmetic only (e.g., `ptr = base + i;` and `ptr->field`). Direct array indexing (`books[i]`) is **not allowed** anywhere in the program.  

6. **Graceful handling**:  
   * If a searched ISBN is not found, print `Book not found.`  
   * All inputs are assumed to be well‑formed; no need for extra validation.  

## Example Input / Output  

```
Enter number of books: 3
Enter book 1 (ISBN TITLE COPIES): 9780131103627 The_C_Programming_Language 4
Enter book 2 (ISBN TITLE COPIES): 9780201633610 Design_Patterns 2
Enter book 3 (ISBN TITLE COPIES): 9780262033848 Introduction_to_Algorithms 5

--- Library Menu ---
1. Search by ISBN
2. List all books
3. Update copies
4. EXIT
Choose an option: 2

ISBN: 9780131103627 | Title: The_C_Programming_Language | Copies: 4
ISBN: 9780201633610 | Title: Design_Patterns | Copies: 2
ISBN: 9780262033848 | Title: Introduction_to_Algorithms | Copies: 5

--- Library Menu ---
1. Search by ISBN
2. List all books
3. Update copies
4. EXIT
Choose an option: 1
Enter ISBN to search: 9780201633610

ISBN: 9780201633610 | Title: Design_Patterns | Copies: 2

--- Library Menu ---
1. Search by ISBN
2. List all books
3. Update copies
4. EXIT
Choose an option: 3
Enter ISBN to update: 9780131103627
Enter new number of copies: 6
Copies updated.

--- Library Menu ---
1. Search by ISBN
2. List all books
3. Update copies
4. EXIT
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Function Requirement** – The logic that displays the details of **one** specific book (used by the search option) must be placed in a function with the exact prototype:  
  ```c
  void displayBook(const struct Book *b);
  ```  
* **Menu Requirement** – The menu must include an explicit option to **EXIT** the program (option number 4 in the example).  
* **Pointer‑Only Access** – No use of the subscript operator `[]` is permitted for accessing the dynamically allocated array; only pointer arithmetic may be used.  
* **Single‑File Implementation** – Apart from `main`, you may define additional helper functions, but the program must reside in a single source file.  

---

## Problem 58 - openai/gpt-oss-120b - Iteration 78
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its inventory system. Each book in the collection is stored in a **linked list** of records that lives entirely in memory while the program runs. A record contains the book’s ISBN, title, and the number of copies currently available.  

Your task is to write a small C program that lets a librarian **add**, **search**, **update**, and **display** books using only pointer arithmetic (no array indexing `[]`). The program should demonstrate a solid grasp of pointers, `struct`s, and dynamic memory management.

---

## Requirements  

1. **Data Structure**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN + terminating null  
     - `char title[101];` // up to 100 characters + terminating null  
     - `int copies;`  
     - `struct Book *next;`  

2. **Core Operations (menu‑driven)**  
   * **1 – Add a new book**  
     - Prompt for ISBN, title, and copies.  
     - Allocate a new `struct Book` with `malloc`.  
     - Insert the new node at the **head** of the linked list.  
   * **2 – Find a book by ISBN**  
     - Prompt for an ISBN.  
     - Traverse the list using only pointer arithmetic (`ptr = ptr->next`).  
     - If found, call `displayBook` (see constraint) to show its details; otherwise print “Book not found.”  
   * **3 – Update copies**  
     - Prompt for an ISBN and the new number of copies.  
     - Locate the node (same traversal as above) and modify its `copies` field.  
   * **4 – List all books**  
     - Walk the list from head to tail, printing each book’s data on its own line.  
   * **5 – EXIT**  
     - Free all dynamically allocated nodes and terminate the program.  

3. **User Interaction**  
   * After completing any operation (except EXIT), the menu should be shown again.  
   * Input may be assumed to be well‑formed; no need for extensive validation.  

---

## Example Input / Output  

```
=== Library Inventory Menu ===
1) Add a new book
2) Find a book by ISBN
3) Update copies
4) List all books
5) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added.

=== Library Inventory Menu ===
1) Add a new book
2) Find a book by ISBN
3) Update copies
4) List all books
5) EXIT
Choose an option: 2

Enter ISBN to search: 9780131103627
--- Book Details ---
ISBN   : 9780131103627
Title  : The C Programming Language
Copies : 4

=== Library Inventory Menu ===
1) Add a new book
2) Find a book by ISBN
3) Update copies
4) List all books
5) EXIT
Choose an option: 4

--- All Books ---
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4

=== Library Inventory Menu ===
1) Add a new book
2) Find a book by ISBN
3) Update copies
4) List all books
5) EXIT
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described above.  
* **Display Function** – The logic that prints the details of a single book **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Pointer‑Only Traversal** – When walking the linked list, you may **only** use the `next` pointer; **no** array‑style indexing (`[]`) or pointer‑to‑array tricks are allowed.  
* **Menu Exit** – The menu must include option **5** (or the keyword `EXIT`) that cleanly terminates the program, freeing all allocated memory.  

---  

*Note: The problem is intentionally designed to let students practice dynamic allocation, pointer navigation, and modular code organization while keeping the overall logic straightforward.*

---

## Problem 59 - openai/gpt-oss-120b - Iteration 79
# STEP 1: PROBLEM  

## Background  
You have been hired as a junior software engineer for **ByteBound Library**, a small community library that keeps its inventory in a simple in‑memory database. Each book record contains an ISBN, a title, and the number of copies currently on the shelf. The library’s legacy code base stores the collection as a contiguous block of memory (an array) and all navigation through the collection must be performed with **pointers and pointer arithmetic** – no indexing (`[]`) is allowed.

Your task is to write a small C program that lets a librarian:

* add new books to the collection,
* look up a book by its ISBN,
* list all books currently stored,
* and exit the program.

The program must demonstrate correct use of pointers, pointer arithmetic, and `struct`s.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[51];`  // up to 50 characters plus null terminator  
     - `int copies;`  

2. **Dynamic Storage**  
   * Allocate an array of `struct Book` dynamically (using `malloc`).  
   * The initial capacity is 5 books.  
   * When the array becomes full, double its capacity with `realloc`.  

3. **Menu‑Driven Interface** (displayed repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a Book** – prompt for ISBN, title, and copies, then store it at the first free slot. |
   | 2      | **Find a Book** – prompt for an ISBN, search the collection using pointer arithmetic, and display the matching book (or “Not found”). |
   | 3      | **List All Books** – traverse the array with pointers and print every stored book. |
   | 4      | **Exit** – terminate the program gracefully, freeing any allocated memory. |

4. **Functions**  
   * Implement a function `void displayBook(const struct Book *b);` that prints a single book’s details in the format:  
     `ISBN: <isbn>, Title: <title>, Copies: <copies>`  
   * All other functionality (adding, searching, listing) may be placed in separate helper functions, but **no additional function may be named `displayBook`**.

5. **Pointer‑Only Traversal**  
   * When iterating over the array (for add, search, or list), you must use only pointer expressions (`*p`, `p+1`, etc.). Direct array indexing (`books[i]`) is **not** permitted.

6. **Input Validation**  
   * The number of copies must be a non‑negative integer. If the user enters a negative value, re‑prompt until a valid number is supplied.

---

## Example Interaction  

```
=== ByteBound Library ===
1) Add a Book
2) Find a Book
3) List All Books
4) Exit
Choose an option: 1

Enter ISBN (13 chars): 9780131103627
Enter Title: The C Programming Language
Enter number of copies: 3
Book added successfully!

=== ByteBound Library ===
1) Add a Book
2) Find a Book
3) List All Books
4) Exit
Choose an option: 2

Enter ISBN to search: 9780131103627
ISBN: 9780131103627, Title: The C Programming Language, Copies: 3

=== ByteBound Library ===
1) Add a Book
2) Find a Book
3) List All Books
4) Exit
Choose an option: 3

--- Book List ---
ISBN: 9780131103627, Title: The C Programming Language, Copies: 3
--- End of List ---

=== ByteBound Library ===
1) Add a Book
2) Find a Book
3) List All Books
4) Exit
Choose an option: 4

Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Display Function** – The logic for showing the details of a single book must reside in a function named `displayBook`.  
* **Pointer‑Only Traversal** – No use of the subscript operator (`[]`) when accessing the dynamically allocated array.  
* **Menu Exit Option** – The menu must contain an explicit option (number 4) that terminates the program.  
* **Memory Management** – All dynamically allocated memory must be freed before program termination.  

---  

*Note: The problem is intended for students who have just completed a unit on pointers and pointer arithmetic; therefore, the solution should emphasize correct pointer manipulation, dynamic memory handling, and struct usage.*

---

## Problem 60 - openai/gpt-oss-120b - Iteration 80
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book in the collection is identified by an ISBN, has a title, an author, and a count of how many copies are currently on the shelf. The library’s IT intern has been asked to write a small C program that lets a librarian **add**, **search**, **display**, and **remove** books using only pointer arithmetic (no array indexing `[]`).  

## Requirements  
Write a console program that supports the following operations through a simple text‑based menu:

1. **Add a new book**  
   * Prompt the user for ISBN (string, up to 13 characters), title (string, up to 50 characters), author (string, up to 30 characters), and number of copies (integer).  
   * Store the information in a dynamically allocated array of `Book` structures. The array should grow with `realloc` as new books are added.  

2. **Search for a book by ISBN**  
   * Prompt for an ISBN.  
   * Using only pointer arithmetic, locate the book in the array.  
   * If found, call `displayBook` (see Constraints) to show all its details; otherwise print “Book not found.”  

3. **Display all books**  
   * Iterate through the array with pointer arithmetic and print each book’s details on a separate line.  

4. **Remove a book by ISBN**  
   * Prompt for an ISBN.  
   * Locate the book using pointer arithmetic.  
   * If found, remove it by shifting the later elements left (again, only pointer arithmetic) and shrink the array with `realloc`. Print “Book removed.”; otherwise print “Book not found.”  

5. **Exit**  
   * Selecting this option terminates the program.  

The menu must be displayed after each operation until the user chooses to exit.

## Example Input / Output  

```
=== Library Inventory Menu ===
1) Add Book
2) Search Book by ISBN
3) Display All Books
4) Remove Book by ISBN
5) EXIT
Enter choice: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Copies: 4
Book added.

=== Library Inventory Menu ===
1) Add Book
2) Search Book by ISBN
3) Display All Books
4) Remove Book by ISBN
5) EXIT
Enter choice: 3

ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Copies: 4

=== Library Inventory Menu ===
1) Add Book
2) Search Book by ISBN
3) Display All Books
4) Remove Book by ISBN
5) EXIT
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct` named `Book` containing the fields:  
   ```c
   typedef struct {
       char isbn[14];      // 13 characters + null terminator
       char title[51];
       char author[31];
       int  copies;
   } Book;
   ```
2. **Function Requirement** – The logic that prints the details of a single `Book` must reside in a function with the exact prototype:  
   ```c
   void displayBook(const Book *b);
   ```
3. **Pointer‑Only Traversal** – All traversals of the dynamic array must use pointer arithmetic (`*ptr`, `ptr + i`, etc.). The subscript operator `[]` is **not** allowed for accessing array elements.  
4. **Single‑File Implementation** – Apart from `main()`, you may define additional helper functions, but the entire program must be contained in a single source file.  
5. **Menu Exit Option** – The menu must include an explicit option numbered **5** (or the keyword `EXIT`) that terminates the program. Selecting this option must cleanly free any dynamically allocated memory before exiting.  

---

## Problem 61 - openai/gpt-oss-120b - Iteration 81
# STEP 1: PROBLEM  

## Background  
The city’s historic museum is digitizing its collection of ancient artifacts. Each artifact is described by a **name**, a **year of discovery**, and a **value in thousands of dollars**. The museum wants a small console program that stores a list of artifacts in an array and lets a curator browse, add, and remove entries using only pointer arithmetic (no array indexing `[]`).  

## Requirements  

1. **Data representation**  
   * Define a `struct Artifact` that contains:  
     ```c
     char name[40];        // null‑terminated string
     int  year;            // year of discovery
     double value;        // value in thousands of dollars
     ```  
2. **Program functionality** (menu‑driven)  
   * **1 – Add an artifact**  
     * Prompt for the name, year, and value.  
     * Store the new artifact at the end of the current list.  
   * **2 – List all artifacts**  
     * Print each stored artifact on a separate line in the order they were entered.  
   * **3 – Display an artifact by index**  
     * Ask for an index (0‑based).  
     * Call a function `void displayArtifact(const Artifact *p)` that prints the details of the requested artifact.  
   * **4 – Delete the last artifact**  
     * Remove the most recently added artifact (if any).  
   * **5 – EXIT**  
     * Terminates the program.  

3. **Technical constraints**  
   * The program must **never use the subscript operator (`[]`)** to access the array of `Artifact`. All traversals and element accesses must be performed with **pointer arithmetic** (e.g., `p + i`, `*(p + i)`).  
   * The maximum number of artifacts the program can hold is **100**.  
   * The list of artifacts should be stored in a **single static array** defined in `main`.  

4. **Input / Output Example**  

```
--- Artifact Manager ---
1) Add an artifact
2) List all artifacts
3) Display an artifact by index
4) Delete the last artifact
5) EXIT
Choose an option: 1
Enter name: Golden Scepter
Enter year of discovery: 1842
Enter value (in $1000s): 125.5

--- Artifact Manager ---
1) Add an artifact
2) List all artifacts
3) Display an artifact by index
4) Delete the last artifact
5) EXIT
Choose an option: 1
Enter name: Bronze Helmet
Enter year of discovery: 1901
Enter value (in $1000s): 78.0

--- Artifact Manager ---
1) Add an artifact
2) List all artifacts
3) Display an artifact by index
4) Delete the last artifact
5) EXIT
Choose an option: 2
[0] Golden Scepter   1842   $125.50k
[1] Bronze Helmet    1901   $78.00k

--- Artifact Manager ---
1) Add an artifact
2) List all artifacts
3) Display an artifact by index
4) Delete the last artifact
5) EXIT
Choose an option: 3
Enter index: 0
Name: Golden Scepter
Year: 1842
Value: $125.50k

--- Artifact Manager ---
1) Add an artifact
2) List all artifacts
3) Display an artifact by index
4) Delete the last artifact
5) EXIT
Choose an option: 5
Goodbye!
```

### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by the `struct Artifact` defined above.  
* **Display function** – The logic for showing the details of a single artifact **must** reside in a function named `displayArtifact` with the prototype `void displayArtifact(const Artifact *p);`.  
* **Pointer‑only access** – No array indexing (`[]`) is allowed anywhere in the program; all element access must be done with pointers and pointer arithmetic.  
* **Menu requirement** – The menu must include an explicit option labeled **5) EXIT** (or the word “EXIT”) that terminates the program.  

*Optional (for extra credit):*  
* Implement input validation for the menu choice and the index entered for option 3.  
* Ensure that adding an artifact when the array is full prints an informative error message.  

---

## Problem 62 - openai/gpt-oss-120b - Iteration 82
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalog system. Each book in the collection is stored in an array of records, and the library software must manipulate this array using **pointers and pointer arithmetic** (no array indexing `[]`). Your task is to write a small program that loads a list of books, allows the user to query a specific book by its position, and prints the details of the book that has the largest number of copies available.

## Requirements  
1. Define a `struct Book` that contains the following fields:  
   * `char title[51]` – the title of the book (max 50 characters, null‑terminated).  
   * `char author[31]` – the author’s name (max 30 characters, null‑terminated).  
   * `int copies` – number of copies the library owns.  

2. The program must:  
   * Read an integer **N** (1 ≤ N ≤ 100) – the number of books.  
   * For each of the **N** books, read three lines: title, author, and copies.  
   * After the data is loaded, present a **menu** with the following options:  

        1. **Display a book** – ask the user for a 1‑based position *p* (1 ≤ p ≤ N) and display that book’s details.  
        2. **Show the most abundant book** – find the book with the greatest `copies` value and display its details. If several books tie, display the first one encountered.  
        3. **Exit** – terminate the program.  

   * The menu must repeat after each operation until the user selects **Exit**.  

3. All traversals of the book array must be performed **exclusively with pointers** (e.g., incrementing a `Book *` variable). Direct array indexing (`books[i]`) is **not allowed**.

4. The logic for displaying the details of **one specific book** (used by both menu options) must be placed in a separate function with the exact prototype:  

```c
void displayEntity(const struct Book *b);
```  

The function should print the title, author, and copies on separate lines, prefixed by labels as shown in the example.

## Example Input / Output  

```
Enter number of books: 3
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 4
Title: Clean Code
Author: Robert Martin
Copies: 7
Title: Introduction to Algorithms
Author: Cormen et al.
Copies: 5

--- MENU ---
1) Display a book
2) Show the most abundant book
3) Exit
Choose an option: 1
Enter position (1‑3): 2
Title: Clean Code
Author: Robert Martin
Copies: 7

--- MENU ---
1) Display a book
2) Show the most abundant book
3) Exit
Choose an option: 2
Title: Clean Code
Author: Robert Martin
Copies: 7

--- MENU ---
1) Display a book
2) Show the most abundant book
3) Exit
Choose an option: 3
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Book`.  
* **Display Function** – The details‑displaying logic must be implemented in a function named `displayEntity` with the prototype shown above.  
* **Pointer‑Only Traversal** – All iteration over the array of books must use pointer arithmetic; the `[]` operator is prohibited for accessing elements.  
* **Menu Exit Option** – The menu must include an explicit option to **Exit** the program (option 3 in the example).  

Your solution should compile with a standard C compiler (C99 or later) and adhere strictly to the constraints. Good luck!

---

## Problem 63 - openai/gpt-oss-120b - Iteration 83
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science department maintains a tiny in‑memory roster of **lab assistants** that help with weekly programming labs. Each assistant is described by a name (maximum 30 characters) and the number of labs they have already assisted.  

Your task is to write a C program that stores a fixed‑size array of these assistants and lets the user query or modify the data using **pointers and pointer arithmetic** only (no array indexing `[]`). This will give you practice navigating memory manually, a skill that is essential when working with low‑level data structures.

## Requirements  

1. **Data Representation**  
   * Define a `struct Assistant` containing:  
     - `char name[31];` (null‑terminated string)  
     - `int labs;` (number of labs assisted)  

2. **Program Flow**  
   * The program should present a **menu** that repeats until the user chooses to exit.  
   * Menu options (choose one):  
     1. **Add / Update an assistant** – Prompt for a name and a new labs count. If the name already exists in the array, update its `labs` field; otherwise, store it in the first free slot.  
     2. **Display an assistant** – Prompt for a name and print the assistant’s details (name and labs). If the name is not found, print “Assistant not found.”  
     3. **List all assistants** – Print the details of every stored assistant in the order they appear in memory.  
     4. **Exit** – Terminate the program. *(This option must be present as required by the mandatory constraints.)*  

3. **Implementation Rules**  
   * The array of `struct Assistant` must have a capacity of **10** elements and be allocated statically (e.g., `struct Assistant roster[10];`).  
   * **All traversal of the array must be performed using pointers and pointer arithmetic** (`*ptr`, `ptr + 1`, etc.). Direct indexing (`roster[i]`) is not allowed.  
   * The logic that prints the details of **one** specific assistant (requirement 2‑b) must be placed in a separate function named `void displayAssistant(const struct Assistant *a);`.  

4. **Input / Output**  
   * All prompts and messages should be printed to `stdout`.  
   * All user responses are read from `stdin`.  

## Example Interaction  

```
--- Lab Assistant Roster ---
1) Add / Update an assistant
2) Display an assistant
3) List all assistants
4) Exit
Enter choice: 1
Enter assistant name: Alice
Enter labs assisted: 3
Assistant added.

--- Lab Assistant Roster ---
1) Add / Update an assistant
2) Display an assistant
3) List all assistants
4) Exit
Enter choice: 1
Enter assistant name: Bob
Enter labs assisted: 5
Assistant added.

--- Lab Assistant Roster ---
1) Add / Update an assistant
2) Display an assistant
3) List all assistants
4) Exit
Enter choice: 2
Enter assistant name: Alice
Name: Alice, Labs Assisted: 3

--- Lab Assistant Roster ---
1) Add / Update an assistant
2) Display an assistant
3) List all assistants
4) Exit
Enter choice: 3
Name: Alice, Labs Assisted: 3
Name: Bob,   Labs Assisted: 5

--- Lab Assistant Roster ---
1) Add / Update an assistant
2) Display an assistant
3) List all assistants
4) Exit
Enter choice: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Assistant`.  
* **Function Requirement** – The function that prints the details of a single assistant must be named `displayAssistant` and accept a pointer to a `const struct Assistant`.  
* **Pointer‑Only Traversal** – No use of the subscript operator `[]` when accessing the roster array; use only pointers and pointer arithmetic.  
* **Menu Exit Option** – The menu must contain an explicit option (number 4 in the example) that exits the program.  

*Optional (for extra credit):* implement the “Add / Update” operation so that it also reports whether the entry was added **or** updated.  

---  

Write the program to satisfy all the above requirements and constraints. Good luck!

---

## Problem 64 - openai/gpt-oss-120b - Iteration 84
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book in the collection is represented by a small record containing the book’s ISBN (a 13‑digit integer), the title (a string of up to 50 characters), and the number of copies currently on the shelf.  

You have been asked to write a **C** program that stores a fixed‑size array of books and lets the librarian perform a few basic operations using **pointers and pointer arithmetic** only (no array indexing `[]`).  

## Requirements  

1. **Data Structure**  
   - Define a `struct Book` with the three fields described above.  

2. **Program Functionality**  
   The program must present a **menu‑driven** interface with the following options:  
   1. **Add a new book** – Prompt for ISBN, title, and copy count, then store the record in the next free slot of the array.  
   2. **Search by ISBN** – Prompt for an ISBN, locate the matching book, and display its details.  
   3. **List all books** – Display the details of every stored book in the order they were entered.  
   4. **Exit** – Terminate the program.  

3. **Implementation Rules**  
   - The array can hold **at most 20 books**.  
   - All traversal of the array must be performed **exclusively with pointers and pointer arithmetic** (e.g., `ptr = ptr + 1`, `*(ptr + i)`, etc.). Direct indexing like `books[i]` is **not allowed**.  
   - The logic that prints the details of a **single** `struct Book` must reside in a function named `void displayBook(const struct Book *b);`.  
   - The main menu loop may call other helper functions, but the only additional function you are required to implement is `displayBook`.  

4. **User Interaction**  
   - The menu should be redisplayed after each operation until the user selects the **Exit** option.  
   - Input validation is not required beyond ensuring the array does not overflow when adding a new book.  

## Example Input / Output  

```
=== Library Book Manager ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added successfully!

=== Library Book Manager ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780201633610
Enter title: Design Patterns
Enter number of copies: 2
Book added successfully!

=== Library Book Manager ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 2

Enter ISBN to search: 9780201633610
--- Book Details ---
ISBN : 9780201633610
Title: Design Patterns
Copies: 2

=== Library Book Manager ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 3

--- All Books ---
ISBN : 9780131103627  Title: The C Programming Language   Copies: 4
ISBN : 9780201633610  Title: Design Patterns               Copies: 2

=== Library Book Manager ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
- **Display Function** – The details of a single book must be printed by a function named `displayBook`. Its prototype must be exactly: `void displayBook(const struct Book *b);`.  
- **Pointer‑Only Traversal** – All navigation through the book array must use pointers and pointer arithmetic; the `[]` operator is prohibited for this purpose.  
- **Menu Exit Option** – The menu must include a clearly labeled option to **Exit** the program (option 4 in the example).  

*Note: The problem is intentionally scoped for students who have just learned pointers and pointer arithmetic, so dynamic memory allocation is **not** required.*

---

## Problem 65 - openai/gpt-oss-120b - Iteration 85
# STEP 1: PROBLEM  

## Background  
The university’s campus *Map* department stores the coordinates of every building on a 2‑D grid. Each building is identified by a short **code** (e.g., “LIB”, “ENG”, “SCI”) and its **(x, y)** location. The department wants a tiny console program that lets a user load a list of buildings, then query the distance between any two of them.  

Because the course just covered **pointers and pointer arithmetic**, the implementation must manipulate the array of buildings through pointers rather than using array indexing directly.

---

## Requirements  

Write a C program that performs the following steps:

1. **Read input**  
   * The first line contains an integer `N` (1 ≤ N ≤ 100) – the number of buildings.  
   * The next `N` lines each contain:  
     ```
     CODE X Y
     ```  
     where `CODE` is a three‑character string (no spaces), and `X` and `Y` are integers representing the building’s coordinates.  

2. **Process queries**  
   * After the building list, the program reads an integer `Q` – the number of distance queries.  
   * Each of the next `Q` lines contains two building codes:  
     ```
     CODE1 CODE2
     ```  
   * For each query the program must:  
     * Locate the two buildings in the stored array (using pointer arithmetic).  
     * Compute the Euclidean distance between them:  

       \[
       d = \sqrt{(x_1-x_2)^2 + (y_1-y_2)^2}
       \]

     * Print the distance rounded to **two** decimal places.  
     * If either code does not exist, print `ERROR: building not found`.

3. **Output**  
   * For each query, output a single line with either the distance or the error message.

---

## Example  

**Input**  
```
5
LIB 10 20
ENG 15 25
SCI 30 35
MED 5 10
ART 12 22
3
LIB ENG
SCI MED
HIS LIB
```

**Output**  
```
7.07
31.62
ERROR: building not found
```

*Explanation*:  
- Distance between LIB (10,20) and ENG (15,25) ≈ 7.07.  
- Distance between SCI (30,35) and MED (5,10) ≈ 31.62.  
- “HIS” is not in the list, so an error is reported.

---

### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be a `struct` named `Building` containing:
   * a character array `code[4]` (to store the three‑letter code plus the terminating `\0`),
   * two integers `x` and `y`.

2. **Function requirement** – The logic that prints the details of **one** specific building (its code and coordinates) must be placed in a function called `displayBuilding`. (The function does not need to be used by the main program for this problem, but it must be present and correctly implemented.)

3. **Pointer arithmetic only** – When searching for a building in the array, you **must not** use the subscript operator `[]`. Access the array exclusively via pointers and pointer arithmetic (e.g., `ptr + i`, `*(ptr + i)`).

4. **Single helper function** – Apart from `main` and `displayBuilding`, you may not add additional functions.

5. **Standard libraries only** – You may include `<stdio.h>`, `<stdlib.h>`, `<string.h>`, and `<math.h>`; no other libraries are allowed.

---

*The problem is self‑contained and ready to be used in an undergraduate assignment on pointers and pointer arithmetic.*

---

## Problem 66 - openai/gpt-oss-120b - Iteration 86
# STEP 1: PROBLEM  

## Background  
The university’s archaeology department has digitized a small collection of **ancient pottery shards**.  
Each shard is described by three pieces of information:  

1. **ID** – a unique integer identifier.  
2. **Weight** – a floating‑point value (grams).  
3. **Age** – an integer representing the estimated number of years old.  

The department wants a simple console program that lets a user **browse, add, and query** the collection.  
Because the data will later be stored in a binary file, the instructor wants students to practice **dynamic memory allocation, structs, pointer arithmetic, and function decomposition**.

## Requirements  
Write a C program that performs the following tasks:

1. **Create** an initially empty dynamic array of `Shard` structs.  
2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit):  

   | Option | Description |
   |--------|-------------|
   | 1 | Add a new shard to the collection. Prompt for ID, weight, and age, allocate space for the new element, and store it at the end of the array (use pointer arithmetic to place it). |
   | 2 | List **all** shards in the order they were entered. Print each shard on its own line in the format `ID: <id>, Weight: <weight>g, Age: <age> years`. |
   | 3 | Search for a shard by **ID** and display its details. If the ID does not exist, print `Shard not found.` |
   | 4 | Delete a shard by **ID**. The array must stay contiguous (move later elements forward using pointer arithmetic). If the ID does not exist, print `Shard not found.` |
   | 5 | **EXIT** the program (the mandatory exit option). |

3. **Memory management** – every time a shard is added or removed, the program must reallocate the dynamic array appropriately (use `malloc`, `realloc`, and `free`). No memory leaks are allowed.  

4. **Error handling** – if allocation fails, print `Memory allocation error.` and return to the menu.  

5. The program terminates only when the user selects the EXIT option; before terminating, it must free all allocated memory.

## Example Interaction  

```
--- Pottery Shard Manager ---
1) Add shard
2) List all shards
3) Find shard by ID
4) Delete shard by ID
5) EXIT
Choose an option: 1
Enter ID: 101
Enter weight (g): 23.5
Enter age (years): 1500
Shard added.

--- Pottery Shard Manager ---
1) Add shard
2) List all shards
3) Find shard by ID
4) Delete shard by ID
5) EXIT
Choose an option: 1
Enter ID: 202
Enter weight (g): 19.2
Enter age (years): 1200
Shard added.

--- Pottery Shard Manager ---
1) Add shard
2) List all shards
3) Find shard by ID
4) Delete shard by ID
5) EXIT
Choose an option: 2
ID: 101, Weight: 23.5g, Age: 1500 years
ID: 202, Weight: 19.2g, Age: 1200 years

--- Pottery Shard Manager ---
1) Add shard
2) List all shards
3) Find shard by ID
4) Delete shard by ID
5) EXIT
Choose an option: 3
Enter ID to search: 202
ID: 202, Weight: 19.2g, Age: 1200 years

--- Pottery Shard Manager ---
1) Add shard
2) List all shards
3) Find shard by ID
4) Delete shard by ID
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct` named `Shard` containing exactly the three fields described (ID, weight, age).  

2. **Function Decomposition** –  
   * The logic for displaying the details of **one specific shard** (used by options 2 and 3) must be placed in a function with the exact prototype:  

     ```c
     void displayShard(const Shard *s);
     ```  

   * All other operations (add, search, delete, menu handling) may be implemented in additional helper functions, but **no more than three functions** (including `displayShard`) may be defined besides `main`.  

3. **Pointer Arithmetic** – When inserting a new shard or shifting elements after deletion, you must use explicit pointer arithmetic (e.g., `*(array + i) = *(array + i + 1);`) rather than array indexing (`array[i]`).  

4. **Menu Exit Option** – The menu must contain an option labeled **5) EXIT** (or the keyword `EXIT`) that cleanly terminates the program.  

5. **Standard Library Only** – You may only include `<stdio.h>`, `<stdlib.h>`, and `<string.h>`; no other libraries are permitted.  

Deliver a complete, compilable C source file that satisfies all the above requirements and constraints.

---

## Problem 67 - openai/gpt-oss-120b - Iteration 87
# STEP 1: PROBLEM  

## Background  
The island of **C‑Isle** is famous for its buried treasures.  The island’s archivist stores each treasure’s information (name, estimated value, and the (x, y) coordinates where it was found) in a dynamically‑allocated list.  Your task is to write a small C program that lets a user explore this list using only pointers and pointer arithmetic – no array‑indexing (`[]`) is allowed.

## Program Requirements  

1. **Data representation**  
   * Define a `struct Treasure` that contains:  
     - `char name[32];`  
     - `int value;`          // in gold coins  
     - `int x, y;`           // map coordinates  

2. **Dynamic storage**  
   * At program start, allocate space for **N** treasures (`N` is a constant you may set to 5).  
   * Populate the array with the data given in the *Sample Input* (or any hard‑coded values you prefer).  

3. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Action |
   |--------|--------|
   | 1      | **List all treasures** – walk through the list using pointer arithmetic and print each treasure’s details. |
   | 2      | **Show a specific treasure** – ask the user for an index (0‑based) and display that treasure’s details. |
   | 3      | **Add a new treasure** – ask the user for name, value, x, and y; re‑allocate the array to hold one more element and store the new treasure at the end (again using only pointers). |
   | 4      | **EXIT** – terminate the program. |

4. **Display routine**  
   * All printing of a single treasure’s information must be performed by a function named `void displayTreasure(const struct Treasure *t)`.  
   * The function receives a pointer to a `Treasure` and prints the fields in a readable format.

5. **Pointer‑only access**  
   * Inside the menu handling code you **must not** use the subscript operator (`[]`).  
   * Access each element by moving a pointer (`ptr = ptr + i;` or `ptr++`) and dereferencing (`ptr->field` or `(*ptr).field`).  

6. **Clean‑up**  
   * Before exiting, free any memory allocated with `malloc`/`realloc`.

## Example Input / Output  

```
=== Treasure Explorer ===
1) List all treasures
2) Show a specific treasure
3) Add a new treasure
4) EXIT
Choose an option: 1

Treasure #0: Gold Crown, Value: 1500, Location: (12, 8)
Treasure #1: Silver Sword, Value: 800, Location: (5, 13)
Treasure #2: Pearl Necklace, Value: 1200, Location: (20, 4)

=== Treasure Explorer ===
1) List all treasures
2) Show a specific treasure
3) Add a new treasure
4) EXIT
Choose an option: 2
Enter treasure index (0‑4): 1

Treasure #1: Silver Sword, Value: 800, Location: (5, 13)

=== Treasure Explorer ===
1) List all treasures
2) Show a specific treasure
3) Add a new treasure
4) EXIT
Choose an option: 3
Enter name: Ruby Ring
Enter value: 950
Enter x coordinate: 7
Enter y coordinate: 9
Treasure added.

=== Treasure Explorer ===
1) List all treasures
2) Show a specific treasure
3) Add a new treasure
4) EXIT
Choose an option: 1

Treasure #0: Gold Crown, Value: 1500, Location: (12, 8)
Treasure #1: Silver Sword, Value: 800, Location: (5, 13)
Treasure #2: Pearl Necklace, Value: 1200, Location: (20, 4)
Treasure #3: Ruby Ring, Value: 950, Location: (7, 9)

=== Treasure Explorer ===
1) List all treasures
2) Show a specific treasure
3) Add a new treasure
4) EXIT
Choose an option: 4
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be a `struct Treasure`.  
* **Display function** – All single‑treasure output must be performed by a function named `displayTreasure`.  
* **Pointer arithmetic only** – No array indexing (`[]`) may appear in the code that traverses or accesses the treasure list.  
* **Menu requirement** – The menu must include an explicit option **4) EXIT** that terminates the program.  

(Feel free to add any additional helper functions, but the above constraints must be satisfied.)

---

## Problem 68 - openai/gpt-oss-120b - Iteration 88
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library wants a small C program that lets a librarian **add new books**, **list all books**, and **search for a book by its ISBN**. Because the system will later be expanded to handle thousands of entries, the professor wants the students to practice **dynamic memory allocation** and **pointer arithmetic** while keeping the code simple.

## Requirements  

1. **Data Representation**  
   - Define a `struct Book` that contains:  
     ```c
     char isbn[14];      // 13‑digit ISBN + terminating '\0'
     char title[101];    // up to 100 characters + '\0'
     int  copies;        // number of copies on the shelf
     ```  

2. **Dynamic Array of Books**  
   - The program must maintain a **dynamic array** of `struct Book` objects that grows as new books are added.  
   - Use `malloc`/`realloc` and **pointer arithmetic** (e.g., `*(books + i)`) to access individual elements; **do not** use the array subscript operator `[]` for accessing the books after allocation.

3. **Menu‑Driven Interface**  
   - Present a text menu with the following options (the user enters the number):  
     1. **Add a new book** – prompt for ISBN, title, and copies; append the book to the dynamic array.  
     2. **List all books** – display every stored book in the order they were added.  
     3. **Find a book by ISBN** – ask for an ISBN, search the array, and display the matching book (or a “not found” message).  
     4. **Exit** – terminate the program gracefully, freeing all allocated memory.  

4. **Display Function**  
   - Implement a function `void displayBook(const struct Book *b);` that prints a single book’s details in the format:  
     ```
     ISBN: <isbn>, Title: <title>, Copies: <copies>
     ```  
   - All places where a book’s details are shown (listing and searching) must call this function.

5. **Input Validation** *(basic)*  
   - The number of copies must be a non‑negative integer.  
   - The ISBN must be exactly 13 characters long (the program may assume the user enters a correct length).

## Example Interaction  

```
=== Library Inventory System ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 1

Enter ISBN (13 chars): 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added!

=== Library Inventory System ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 2

ISBN: 9780131103627, Title: The C Programming Language, Copies: 4

=== Library Inventory System ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 3

Enter ISBN to search: 9780131103627
ISBN: 9780131103627, Title: The C Programming Language, Copies: 4

=== Library Inventory System ===
1) Add a new book
2) List all books
3) Find a book by ISBN
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

- **Must use a `struct`** (`struct Book`) to represent each book.  
- **All accesses to the dynamic array after allocation must be performed with pointer arithmetic**; the `[]` operator is prohibited for that purpose.  
- **The function `displayBook` must be used** whenever a book’s information is printed.  
- The program must contain **exactly one additional user‑defined function** besides `main` (i.e., `displayBook`). All other logic must reside in `main`.  
- The menu **must include an explicit “Exit” option** (option 4) that ends the program and releases any allocated memory.  

---

## Problem 69 - openai/gpt-oss-120b - Iteration 89
# STEP 1: PROBLEM  

## Background  
The university’s Computer Science department maintains a small inventory of laboratory equipment (e.g., microscopes, oscilloscopes, and 3‑D printers). Each item has a **name**, a **serial number**, and a **quantity** currently available in the lab. The inventory system is to be written in C and must make heavy use of pointers and pointer arithmetic because the students have just finished the “Pointers and Pointer Arithmetic” unit.

## Task  
Write a program that stores up to **20** inventory items in a dynamically allocated array. The program must allow the user to:

1. **Add** a new equipment record (if there is still space).  
2. **Remove** an equipment record by its serial number (shifting the remaining records so that the array stays contiguous).  
3. **Update** the quantity of a specific item identified by its serial number.  
4. **Display** the details of **one** specific item (by serial number).  
5. **List** all items currently stored.  
6. **Exit** the program.

All operations that modify the collection must be performed by manipulating pointers directly (no array‑index notation `[]` is allowed in the implementation of those operations).  

## Requirements  

- Define a `struct Equipment` containing:
  - `char name[30];`
  - `int serial;`
  - `int quantity;`
- Allocate the array of `struct Equipment` with `malloc` (size = 20).  
- Implement the following functions (each must use pointer arithmetic internally):
  1. `void addItem(struct Equipment *base, int *size);`
  2. `void removeItem(struct Equipment *base, int *size);`
  3. `void updateQuantity(struct Equipment *base, int size);`
  4. `void displayItem(struct Equipment *base, int size);`   ← **must be named exactly this**
  5. `void listAll(const struct Equipment *base, int size);`
- The `main` function should present a **menu** and repeatedly prompt the user until the **Exit** option is chosen.  

## Example Interaction  

```
--- Lab Equipment Inventory ---
1) Add item
2) Remove item
3) Update quantity
4) Display item
5) List all items
6) Exit
Choose an option: 1
Enter name: Oscilloscope
Enter serial number: 1024
Enter quantity: 3
Item added.

--- Lab Equipment Inventory ---
1) Add item
2) Remove item
3) Update quantity
4) Display item
5) List all items
6) Exit
Choose an option: 5
Serial   Name          Quantity
1024     Oscilloscope  3

--- Lab Equipment Inventory ---
1) Add item
2) Remove item
3) Update quantity
4) Display item
5) List all items
6) Exit
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented by a `struct Equipment` as described above.  
- **Function Naming:** The logic for displaying the details of ONE specific entity must be in a function called **`displayItem`** with the exact prototype shown.  
- **Pointer‑Only Access:** Inside `addItem`, `removeItem`, `updateQuantity`, `displayItem`, and `listAll`, you **may not** use the subscript operator `[]`. All traversal and element access must be done with pointer arithmetic (`*`, `+`, `-`).  
- **Menu Exit:** The menu must include an explicit option to **Exit** the program (option number **6** in the example). Selecting this option terminates the loop and ends the program.  

*Note:* The program should handle invalid inputs gracefully (e.g., trying to remove a non‑existent serial number) by printing an appropriate message and returning to the menu.

---

## Problem 70 - openai/gpt-oss-120b - Iteration 90
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernising its inventory system. Each book in the collection is stored in a **singly‑linked list** that lives entirely in dynamic memory. The list nodes contain the book’s ISBN, title, and the number of copies currently on the shelf.  

Your task is to write a small console program that lets a librarian **add**, **remove**, **search**, and **display** books using only pointer operations (no array indexing). The program must demonstrate that you understand pointer arithmetic, dynamic allocation, and the use of `struct` to model data.

## Requirements  

1. **Data representation**  
   * Define a `struct BookNode` that holds:  
     - `char isbn[14]` (13‑digit ISBN plus terminating `'\0'`)  
     - `char title[51]` (up to 50 characters plus `'\0'`)  
     - `int copies` (non‑negative)  
     - `struct BookNode *next` (pointer to the next node)  

2. **Menu‑driven interface** (the program repeatedly shows a menu until the user chooses to exit)  
   * **1. Add a new book** – Prompt for ISBN, title, and copies. Allocate a new node with `malloc`, fill the fields, and insert the node **at the end of the list** using only pointer arithmetic.  
   * **2. Remove a book** – Prompt for an ISBN. Locate the node with that ISBN, unlink it from the list, free its memory, and report success or “not found”.  
   * **3. Search for a book** – Prompt for an ISBN and display the book’s details if it exists, otherwise print “Book not found”.  
   * **4. List all books** – Walk the list and print the ISBN, title, and copies for every stored book.  
   * **5. EXIT** – Terminate the program, freeing any remaining allocated nodes.  

3. **Pointer arithmetic rule**  
   * When traversing the list, you may **only** use the `next` pointer and the `*` (dereference) operator. Do **not** use array‑style indexing (`list[i]`) or the `->` operator; instead, use `(*ptr).field` syntax to access members.  

4. **Functions**  
   * Implement a function `void displayBook(const struct BookNode *node);` that prints a single book’s information in the format:  
     `ISBN: <isbn>, Title: "<title>", Copies: <copies>`  
   * All other logic (adding, removing, searching, listing) must be placed in separate helper functions of your choice, but **no more than three additional functions** may be written besides `main` and `displayBook`.  

5. **Robustness**  
   * Validate input where reasonable (e.g., copies must be ≥ 0).  
   * Ensure there are no memory leaks (every `malloc` must have a matching `free`).  

## Example Interaction  

```
=== Library Inventory System ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter number of copies: 4
Book added successfully.

=== Library Inventory System ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 4

ISBN: 9780131103627, Title: "The C Programming Language", Copies: 4

=== Library Inventory System ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 3

Enter ISBN to search: 9780131103627
ISBN: 9780131103627, Title: "The C Programming Language", Copies: 4

=== Library Inventory System ===
1) Add a new book
2) Remove a book
3) Search for a book
4) List all books
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity **must** be represented by a `struct BookNode`.  
* **Display function** – The details of a single book **must** be printed by a function named `displayBook`.  
* **Pointer access** – Inside traversal loops you **must** use `(*ptr).field` syntax (no `ptr->field`).  
* **Menu requirement** – The menu **must** include an explicit option to **EXIT** (option 5 in the example).  
* **Function count** – Apart from `main` and `displayBook`, you may create **at most three** additional helper functions.  

Write the program in C, adhering strictly to the constraints above.

---

## Problem 71 - openai/gpt-oss-120b - Iteration 91
# STEP 1: PROBLEM  

## Background  
The ancient kingdom of **Codelandia** stores its priceless artifacts in a series of **Treasure Chests**. Each chest holds a unique ID, the name of the artifact, and its estimated value in gold coins. The royal archivist wants a small console program that lets a junior scribe add new chests, view the details of a specific chest, and list all chests currently recorded. Because the scribe is just learning C, the program must manipulate the collection of chests using **pointers and pointer arithmetic only** – no array‑index (`[]`) notation is allowed.

## Requirements  

1. Define a `struct` named `Chest` that contains:  
   * `int id;` – a positive integer identifier (unique for each chest).  
   * `char name[31];` – a null‑terminated string (max 30 characters) describing the artifact.  
   * `double value;` – the estimated value in gold coins.  

2. The program must maintain a **dynamic array** of `Chest` objects, allocated with `malloc`/`realloc`. The maximum number of chests is not known in advance.

3. Provide a **menu‑driven interface** with the following options (the exact numbers are required):  
   1. **Add a new chest** – prompt for `id`, `name`, and `value`; store the new chest at the end of the dynamic array.  
   2. **Display a chest** – ask for an `id` and print the details of the chest whose `id` matches. If no such chest exists, print `Chest not found.`  
   3. **List all chests** – print the details of every chest in the order they were added.  
   4. **EXIT** – terminate the program.  

4. All traversal of the dynamic array must be performed **exclusively with pointer arithmetic** (`*ptr`, `ptr + i`, etc.). Direct indexing (`array[i]`) is prohibited.

5. The logic that prints the details of a single chest must be placed in a **function called `displayChest`** with the prototype:  
   ```c
   void displayChest(const Chest *c);
   ```

6. The program should gracefully handle memory allocation failures by printing an error message and exiting.

## Example Input / Output  

```
--- Treasure Chest Manager ---
1) Add a new chest
2) Display a chest
3) List all chests
4) EXIT
Choose an option: 1
Enter chest ID: 101
Enter artifact name: Golden Crown
Enter value in gold coins: 1250.75
Chest added successfully.

--- Treasure Chest Manager ---
1) Add a new chest
2) Display a chest
3) List all chests
4) EXIT
Choose an option: 1
Enter chest ID: 202
Enter artifact name: Sapphire Scepter
Enter value in gold coins: 980.00
Chest added successfully.

--- Treasure Chest Manager ---
1) Add a new chest
2) Display a chest
3) List all chests
4) EXIT
Choose an option: 2
Enter chest ID to display: 101
Chest ID: 101
Artifact: Golden Crown
Value: 1250.75 gold coins

--- Treasure Chest Manager ---
1) Add a new chest
2) Display a chest
3) List all chests
4) EXIT
Choose an option: 3
Chest ID: 101, Artifact: Golden Crown, Value: 1250.75 gold coins
Chest ID: 202, Artifact: Sapphire Scepter, Value: 980.00 gold coins

--- Treasure Chest Manager ---
1) Add a new chest
2) Display a chest
3) List all chests
4) EXIT
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct` named `Chest`.  
* **Function Requirement** – The details of ONE specific chest must be displayed by a function called `displayChest`.  
* **Pointer‑Arithmetic Requirement** – All access to the dynamic array of chests must use pointer arithmetic; the `[]` operator is not allowed.  
* **Menu Requirement** – The program must present a menu and **must include an EXIT option (option 4)** that cleanly terminates the program.  

*Optional (but encouraged for extra credit):*  
- Implement a function `void listAllChests(const Chest *base, size_t count);` that uses pointer arithmetic to iterate through the array.  
- Validate that entered IDs are unique; if a duplicate ID is entered, display `Error: ID already exists.` and do not add the chest.  

---

## Problem 72 - openai/gpt-oss-120b - Iteration 92
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its inventory system. Each book in the collection is stored in a dynamically allocated array of **Book** structures. The library wants a simple console program that lets a librarian:  

1. Add new books to the inventory.  
2. List all books currently stored.  
3. Search for a book by its ISBN and display its details.  
4. Remove a book by its ISBN.  

All operations must be performed by manipulating pointers and using pointer arithmetic—no array indexing (`[]`) is allowed except when printing a string stored inside the structure.

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that contains:  
     - `char title[64];`  
     - `char author[48];`  
     - `unsigned long isbn;` (unique identifier)  
     - `int copies;` (number of copies owned)  

2. **Dynamic Storage**  
   * The program must maintain a **dynamic array** of `Book` objects that can grow or shrink as books are added or removed.  
   * Memory for the array must be allocated with `malloc`/`realloc` and freed appropriately.  

3. **Menu‑Driven Interface** (the program must present a menu; see **MANDATORY CONSTRAINTS** below)  
   * **1 – Add a Book** – Prompt for title, author, ISBN, and copies, then append the new `Book` to the array.  
   * **2 – List All Books** – Traverse the array using only pointer arithmetic and print each book’s information.  
   * **3 – Find Book by ISBN** – Prompt for an ISBN, locate the matching `Book`, and call the required function `displayBook` to show its details.  
   * **4 – Remove Book by ISBN** – Prompt for an ISBN, delete the matching entry, shift the remaining elements using pointer arithmetic, and shrink the allocated memory.  
   * **0 – Exit** – Terminate the program, freeing all allocated memory.  

4. **Functionality Restrictions**  
   * No use of the subscript operator (`[]`) for traversing the dynamic array; only pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.).  
   * The logic for displaying the details of **ONE specific book** must be encapsulated in a function with the exact prototype:  

     ```c
     void displayBook(const struct Book *b);
     ```

   * All other helper functions (e.g., for adding, searching, removing) may be added at the programmer’s discretion, but the program must contain **exactly one** additional function besides `main` and `displayBook`.  

## Example Input / Output  

```
--- Library Inventory System ---
1) Add a Book
2) List All Books
3) Find Book by ISBN
4) Remove Book by ISBN
0) Exit
Enter choice: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN: 9780131103627
Enter copies: 3
Book added successfully!

--- Library Inventory System ---
1) Add a Book
2) List All Books
3) Find Book by ISBN
4) Remove Book by ISBN
0) Exit
Enter choice: 2

Book #0
  Title : The C Programming Language
  Author: Kernighan & Ritchie
  ISBN  : 9780131103627
  Copies: 3

--- Library Inventory System ---
1) Add a Book
2) List All Books
3) Find Book by ISBN
4) Remove Book by ISBN
0) Exit
Enter choice: 3

Enter ISBN to search: 9780131103627
--- Book Details ---
Title : The C Programming Language
Author: Kernighan & Ritchie
ISBN  : 9780131103627
Copies: 3

--- Library Inventory System ---
1) Add a Book
2) List All Books
3) Find Book by ISBN
4) Remove Book by ISBN
0) Exit
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
2. **Display Function** – The details of a single book must be printed by a function named `displayBook` with the prototype shown above.  
3. **Function Count** – Apart from `main` and `displayBook`, the solution may contain **only one** additional user‑defined function.  
4. **Pointer‑Only Traversal** – When iterating over the dynamic array (listing, searching, shifting after removal), you must use pointer arithmetic; array indexing (`[]`) is prohibited for those operations.  
5. **Menu Exit Option** – The menu must include an explicit option **0) Exit** that terminates the program and releases all allocated memory.  

---

## Problem 73 - openai/gpt-oss-120b - Iteration 93
# STEP 1: PROBLEM  

## Background  
The campus IT department is building a tiny “Student Directory” that runs in a console.  
Each student record consists of a **name** (up to 30 characters) and a **grade point average** (a `float`).  
The directory must store an arbitrary number of students that can be added or removed while the program is running.  

You are to write this directory using **pointers and pointer arithmetic only** – no array‑subscript (`[]`) notation may be used to access the student data.

---

## Program Requirements  

1. **Data Representation**  
   * Define a `struct Student` containing:  
     * `char name[31];`  (null‑terminated string)  
     * `float gpa;`  

2. **Dynamic Storage**  
   * Allocate memory for the student list on the heap using `malloc`/`realloc`.  
   * The program must keep track of the current number of stored students (`size`) and the allocated capacity (`capacity`).  

3. **Supported Operations** (the program may present a simple menu, but a menu is **optional** – if you include one, see the mandatory EXIT rule in the constraints)  
   * **Add a student** – read a name and a GPA, store the new record at the end of the list.  
   * **Remove a student** – given a zero‑based index, delete that record and shift all later records forward so that the list remains contiguous.  
   * **Display a student** – given a zero‑based index, print that student’s name and GPA. The printing logic **must** be placed in a function named `void displayStudent(const Student *p)` that receives a pointer to a single `Student`.  
   * **Display all students** – iterate through the list and print each record (you may reuse `displayStudent`).  

4. **Pointer Arithmetic Only**  
   * Access any element of the dynamic array **exclusively** with pointer arithmetic (`*(ptr + i)`, `ptr[i]` is **not allowed**).  
   * All pointer increments/decrements used for traversing or shifting must be explicit arithmetic on `Student*` pointers.  

5. **Program Termination**  
   * When the user chooses to quit (or after a predefined sequence of commands in an automated test), free all allocated memory and exit cleanly.  

---

## Example Interaction  

```
Welcome to the Student Directory!
Choose an option:
1) Add student
2) Remove student
3) Display a student
4) Display all students
5) Exit
> 1
Enter name: Alice
Enter GPA: 3.8
Student added.

> 1
Enter name: Bob
Enter GPA: 3.2
Student added.

> 4
[0] Alice - GPA: 3.80
[1] Bob   - GPA: 3.20

> 3
Enter index to display: 0
Alice - GPA: 3.80

> 2
Enter index to remove: 0
Student removed.

> 4
[0] Bob - GPA: 3.20

> 5
Goodbye!
```

*Note:* The exact wording of prompts is not graded; only the functional behavior matters.

---

### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented by a `struct Student` as described above.  
- **Display Function:** The logic for showing the details of **one** specific student must reside in a function named `void displayStudent(const Student *p)`.  
- **Pointer‑Only Access:** No use of the array subscript operator (`[]`) is permitted when working with the dynamic list of students. All traversals, insertions, deletions, and reads must employ pointer arithmetic.  
- **Memory Management:** All memory allocated with `malloc`/`realloc` must be released with `free` before program termination.  
- **Menu (if implemented):** Must contain an option explicitly labeled “5) Exit” (or the keyword `EXIT`) that terminates the program.  

---  

*Write the program in C (C99 or later).*

---

## Problem 74 - openai/gpt-oss-120b - Iteration 94
# STEP 1: PROBLEM  

## Background  
The campus library has decided to modernize its inventory system. Every book is stored in a **shelf array** that holds the titles, the number of copies currently on the shelf, and a unique identifier (ISBN). The library’s IT intern has been asked to write a small C program that lets a librarian:

1. Add new books to the inventory.  
2. Remove a book (by ISBN) from the inventory.  
3. Search for a book by ISBN and display its details.  

The intern has just learned about **pointers** and **pointer arithmetic**, and the professor wants the assignment to force the student to manipulate an array of structures through pointers rather than using array indexing.

## Requirements  

1. **Data Representation**  
   - Define a `struct Book` containing:  
     ```c
     char title[51];      // up to 50 characters + null terminator
     unsigned int isbn;  // unique identifier
     int copies;          // number of copies on the shelf
     ```  
2. **Dynamic Storage**  
   - The program must allocate a dynamic array of `struct Book` using `malloc`.  
   - The initial capacity is 10 books. If the array becomes full, double its capacity with `realloc`.  
3. **Menu‑Driven Interface** (the program must present a text menu after each operation)  
   - `1` – Add a new book. Prompt for title, ISBN, and copies.  
   - `2` – Remove a book by ISBN. If the ISBN does not exist, print an error message.  
   - `3` – Search and display a book by ISBN.  
   - `4` – List **all** books currently stored (in the order they were added).  
   - `0` – **EXIT** the program. *(mandatory exit option)*  
4. **Pointer Arithmetic**  
   - All traversals of the book array (search, list, removal, etc.) must be performed using pointers and pointer arithmetic **only**; the use of the subscript operator `[]` is prohibited for accessing the array elements.  
5. **Function Requirements**  
   - Implement a function `void displayBook(const struct Book *b);` that prints the details of a single book in the format:  
     ```
     ISBN: <isbn>, Title: "<title>", Copies: <copies>
     ```  
   - All other logic may be placed in additional helper functions, but the program must contain **exactly one** function besides `main` that performs any pointer‑based traversal (e.g., a search function).  

## Example Interaction  

```
=== Library Inventory ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
0) EXIT
Choice: 1
Enter title: The C Programming Language
Enter ISBN: 9780131103627
Enter copies: 3
Book added.

=== Library Inventory ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
0) EXIT
Choice: 1
Enter title: Introduction to Algorithms
Enter ISBN: 9780262033848
Enter copies: 5
Book added.

=== Library Inventory ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
0) EXIT
Choice: 3
Enter ISBN to search: 9780131103627
ISBN: 9780131103627, Title: "The C Programming Language", Copies: 3

=== Library Inventory ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
0) EXIT
Choice: 4
ISBN: 9780131103627, Title: "The C Programming Language", Copies: 3
ISBN: 9780262033848, Title: "Introduction to Algorithms", Copies: 5

=== Library Inventory ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
0) EXIT
Choice: 0
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity must be represented with a `struct Book`.  
- The function `displayBook` **must** be used for printing a single book’s details.  
- All array traversals must use **only** pointer arithmetic; the `[]` operator is not allowed for accessing elements of the dynamic array.  
- The menu must include option `0` to **EXIT** the program.  
- Apart from `main`, the program may contain **exactly one** additional function that performs a pointer‑based traversal (e.g., a search routine). All other helper functions must not iterate over the array.  

*Design the program to satisfy all the above specifications.*

---

## Problem 75 - openai/gpt-oss-120b - Iteration 95
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its catalogue system. Each book in the collection is stored as a record that contains the book’s ISBN, title, author, and the number of copies currently on the shelf. The library wants a small console program that allows a librarian to **add**, **search**, and **list** books using pointers and pointer arithmetic. The program will be the first practical assignment for students who have just finished the “Pointers and Pointer Arithmetic” lecture.

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that holds:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[51];`  // up to 50 characters + null  
     - `char author[31];` // up to 30 characters + null  
     - `int copies;`  

2. **Dynamic Storage**  
   * Allocate an array of `Book` records dynamically on the heap using `malloc`.  
   * The program starts with capacity for **10** books.  
   * If the array becomes full, double its capacity with `realloc`.  

3. **Menu‑driven Interface** (the program must present a menu each iteration)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new book** – Prompt for ISBN, title, author, and copies, then store the record at the end of the array. |
   | 2      | **Search by ISBN** – Prompt for an ISBN, locate the matching book, and display its details. |
   | 3      | **List all books** – Print the information of every stored book in the order they were added. |
   | 4      | **Exit** – Terminate the program. |

   *The “Exit” option **must** be option **4**.*

4. **Pointer Arithmetic**  
   * All accesses to the `Book` array (reading, writing, searching) must be performed using pointer arithmetic (e.g., `*(books + i)`, `books[i]` is *not* allowed).  

5. **Display Function**  
   * Implement a function `void displayBook(const struct Book *b);` that receives a pointer to a `Book` and prints its fields in a readable format.  
   * The search option (2) must call `displayBook` to show the found record.  

6. **Input Validation**  
   * The program should reject a duplicate ISBN when adding a new book and print an appropriate message.  

7. **Memory Clean‑up**  
   * Before exiting, free any dynamically allocated memory.

## Example Interaction  

```
=== Library Catalogue ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 1

Enter ISBN (13 chars): 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter number of copies: 4
Book added successfully!

=== Library Catalogue ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 2

Enter ISBN to search: 9780131103627
--- Book Details ---
ISBN   : 9780131103627
Title  : The C Programming Language
Author : Kernighan & Ritchie
Copies : 4

=== Library Catalogue ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 3

--- All Books ---
1) ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie | Copies: 4

=== Library Catalogue ===
1) Add a new book
2) Search by ISBN
3) List all books
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described.  
2. **Display Function** – The logic for showing the details of a single book **must** be encapsulated in a function named `displayBook`.  
3. **Pointer‑Only Access** – Direct array indexing (`books[i]`) is prohibited; use pointer arithmetic for every array operation.  
4. **Menu Exit Option** – The menu must contain the explicit option **4** to exit the program.  
5. **Single‑File Implementation** – All code (including `displayBook`) must reside in a single source file; no additional headers or source files are allowed.  

*The problem is intended for students who have just learned about pointers, `malloc`/`realloc`, and basic struct handling. The solution should demonstrate correct use of pointer arithmetic, dynamic memory management, and modular design via the required function.*

---

## Problem 76 - openai/gpt-oss-120b - Iteration 96
# STEP 1: PROBLEM  

## Background  
The university’s Computer Lab wants a tiny command‑line utility to keep track of **lab stations** that are currently in use. Each station has a numeric ID, the name of the student occupying it, and the number of minutes the student has been logged in. The lab manager will run the program each shift and perform simple operations such as adding a new occupied station, removing a station when a student leaves, and displaying the details of a particular station.  

The assignment is meant to reinforce **pointers**, **pointer arithmetic**, and the use of **structures** in C.

## Requirements  

Write a C program that:

1. **Defines** a `struct Station` containing:  
   * `int id;` – unique station identifier (positive integer).  
   * `char name[31];` – student’s name (max 30 characters, null‑terminated).  
   * `int minutes;` – minutes the student has been logged in.  

2. **Stores** up to **20** stations in a **single dynamically allocated array** of `struct Station`. The array must be allocated with `malloc` (or `calloc`) and accessed only through pointers and pointer arithmetic – **no array indexing (`[]`)** may be used for the main data structure.

3. **Provides** a text menu with the following options (the user selects the option number):  
   1. **Add a station** – Prompt for `id`, `name`, and `minutes`. Insert the new station at the *first free slot* in the array. If the array is full, print an error message.  
   2. **Remove a station** – Prompt for a station `id`. Locate the matching station and remove it by shifting the subsequent elements left (using pointer arithmetic). If the `id` is not found, print an error message.  
   3. **Display a station** – Prompt for a station `id` and call a function `displayStation` (see Constraints) to print the station’s details. If the `id` is not found, print an error message.  
   4. **List all stations** – Print the details of every occupied station in the order they appear in the array.  
   5. **EXIT** – Terminate the program gracefully, freeing any allocated memory.  

4. The program must **repeat** the menu after completing an operation until the user chooses **EXIT**.

5. All input should be read from `stdin`; all output should be written to `stdout`.  

## Example Input / Output  

```
=== Lab Station Manager ===
1) Add a station
2) Remove a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 1
Enter station ID: 101
Enter student name: Alice
Enter minutes logged in: 45
Station added.

=== Lab Station Manager ===
1) Add a station
2) Remove a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 1
Enter station ID: 102
Enter student name: Bob
Enter minutes logged in: 12
Station added.

=== Lab Station Manager ===
1) Add a station
2) Remove a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 3
Enter station ID to display: 101
Station ID: 101
Student: Alice
Minutes: 45

=== Lab Station Manager ===
1) Add a station
2) Remove a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 4
Station ID: 101, Student: Alice, Minutes: 45
Station ID: 102, Student: Bob,   Minutes: 12

=== Lab Station Manager ===
1) Add a station
2) Remove a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Station`.  
* **Function Requirement** – The logic for displaying the details of **ONE specific station** must be placed in a function with the exact prototype:  

  ```c
  void displayStation(const struct Station *p);
  ```  

* **Pointer‑Only Access** – Inside the main program (except for the `displayStation` function) you may **not** use the array subscript operator `[]`. All traversal, insertion, removal, and searching must be performed with pointers and pointer arithmetic (`*`, `->`, `+`, `-`).  
* **Dynamic Allocation** – The array of stations must be allocated at runtime using `malloc`/`calloc`.  
* **Menu Exit Option** – The menu must include a distinct option (number **5**) labelled **EXIT** that terminates the program.  

*Optional (for extra credit):*  
- Validate that station IDs are unique when adding a new station.  
- Implement the list‑all operation using a single loop that prints each station via pointer arithmetic.  

---

## Problem 77 - openai/gpt-oss-120b - Iteration 97
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is described by a small record containing its ISBN, title, and the number of copies currently on the shelf. The library’s IT intern has been asked to write a **C** program that stores a fixed‑size array of these book records and allows the user to query information about a particular book using pointer arithmetic only (no array indexing `[]`).  

## Requirements  

Write a program that:

1. **Defines** a `struct Book` with the following members:  
   * `char isbn[14];`   // 13‑digit ISBN plus terminating null  
   * `char title[51];`  // up to 50 characters plus terminating null  
   * `int copies;`  

2. **Creates** an array of **exactly 5** `Book` objects, initialized with data of your choice (hard‑coded in the source).  

3. **Displays** a simple text menu repeatedly until the user chooses to exit:  

   ```
   1) List all books (show ISBN, title, copies)
   2) Find a book by ISBN
   3) Exit
   Enter choice: 
   ```

4. If the user selects **option 2**, the program prompts for an ISBN string, searches the array using **pointer arithmetic only** (no `[]` operator), and:

   * If a matching book is found, calls a function `displayBook` to print the book’s details.  
   * If no match is found, prints “Book not found.”  

5. The program must **return to the menu** after completing an operation (except when exiting).  

## Example Input / Output  

```
--- Library Inventory ---
1) List all books
2) Find a book by ISBN
3) Exit
Enter choice: 1

ISBN: 9780131103627   Title: The C Programming Language   Copies: 4
ISBN: 9780201633610   Title: Design Patterns               Copies: 2
ISBN: 9780131101630   Title: Introduction to Algorithms    Copies: 5
ISBN: 9780262033848   Title: Computer Systems: A Programmer's Perspective   Copies: 3
ISBN: 9780132350884   Title: Clean Code                     Copies: 1

--- Library Inventory ---
1) List all books
2) Find a book by ISBN
3) Exit
Enter choice: 2
Enter ISBN to search: 9780132350884

ISBN: 9780132350884   Title: Clean Code   Copies: 1

--- Library Inventory ---
1) List all books
2) Find a book by ISBN
3) Exit
Enter choice: 3
Goodbye!
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented with a `struct` named `Book`.  
* The logic that prints the details of **one** specific book **must** reside in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* All traversal of the `Book` array **must** be performed using **pointer arithmetic** (`*ptr`, `ptr + i`, etc.). The subscript operator `[]` is **not allowed** for accessing the array elements.  
* The program must contain **exactly two user‑defined functions** besides `main`: `displayBook` and a helper `searchByISBN` (optional) – no additional functions are permitted.  
* The menu must include an explicit **Exit** option (option 3 in the example) that terminates the program.  

---  

*Write the program so that it compiles with a standard C99 compiler and runs correctly on any platform.*

---

## Problem 78 - openai/gpt-oss-120b - Iteration 98
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernizing its catalog system. Each book in the collection is stored as a record containing the book’s **ISBN**, **title**, **author**, and the **number of copies** currently on the shelf. The library wants a small C program that lets a librarian browse the catalog, add new books, and look up a book by its ISBN.  

The librarian is comfortable with a simple text‑based menu, but the implementation must demonstrate the use of **pointers** and **pointer arithmetic** to traverse an array of book records.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` with the following members:  
     ```c
     char isbn[14];      // 13‑digit ISBN + terminating '\0'
     char title[51];     // up to 50 characters + '\0'
     char author[31];    // up to 30 characters + '\0'
     int  copies;        // number of copies on the shelf
     ```
2. **Program Functionality**  
   * The program maintains a dynamically allocated array of `struct Book`. The maximum number of books is **100**.  
   * Present a menu with the following options (the user selects by entering the number):  
     1. **Add a new book** – Prompt for ISBN, title, author, and copies, then store the record at the next free position.  
     2. **Find a book by ISBN** – Ask for an ISBN, search the array using pointer arithmetic, and if found display the book’s details; otherwise print “Book not found.”  
     3. **List all books** – Traverse the array with a pointer and print every stored record.  
     4. **Exit** – Terminate the program.  
   * Input validation is not required beyond the menu choice; you may assume the user enters data in the correct format.  

3. **Functions**  
   * Implement a function `void displayBook(const struct Book *b);` that prints a single book’s information in a readable format. This function must be used for both the “Find” and “List” options.  

4. **Memory Management**  
   * Allocate the array of `struct Book` once at program start (e.g., using `malloc`).  
   * Free the allocated memory before exiting.  

---

## Example Input / Output  

```
--- Library Catalog Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Enter choice: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter copies: 4
Book added successfully!

--- Library Catalog Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Enter choice: 2

Enter ISBN to search: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 4

--- Library Catalog Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Enter choice: 3

ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 4

--- Library Catalog Menu ---
1) Add a new book
2) Find a book by ISBN
3) List all books
4) Exit
Enter choice: 4

Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented with a `struct Book` as described.  
* **Display Function** – All printing of a book’s details must be performed by the function `displayBook`. Direct `printf` of book fields inside `main` or other functions is not allowed.  
* **Pointer Arithmetic** – When searching or listing the books, you must use pointer arithmetic (e.g., `ptr = books + i;`) rather than array indexing (`books[i]`).  
* **Menu Exit Option** – The menu must include option **4) Exit** (or the keyword `EXIT`) that cleanly terminates the program.  

*Optional (for extra credit):*  
- Implement the “Add a new book” option so that it refuses to add a book when the catalog already contains 100 entries, printing an appropriate message.  

---  

*Your task is to write the complete C program that satisfies all of the above specifications.*

---

## Problem 79 - openai/gpt-oss-120b - Iteration 99
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library’s junior programmer has been asked to write a small C program that keeps a **fixed‑size** list of books in memory and allows a librarian to view, add, and remove books while practicing pointer arithmetic.

## Requirements  

Write a C program that:

1. **Defines** a `struct Book` containing  
   * `char isbn[14];`   // 13‑digit ISBN plus terminating `'\0'`  
   * `char title[51];` // up to 50 characters plus terminating `'\0'`  
   * `int copies;`     // number of copies on the shelf  

2. **Allocates** an array of **10** `struct Book` objects **statically** (i.e., `struct Book books[10];`).  

3. **Keeps** track of how many slots are currently occupied (`int count`).  

4. **Provides** a text‑based menu with the following options (the exit option must be present as required):  
   1. **Add a new book** – Prompt for ISBN, title, and copies. Store the new record in the first free slot. If the array is full, display an appropriate message.  
   2. **Remove a book** – Prompt for an ISBN. Find the matching book, shift all later elements left using pointer arithmetic, and decrement `count`. If the ISBN is not found, inform the user.  
   3. **Display a book** – Prompt for an ISBN and show its details. The logic for displaying a single book **must be placed in a function called `displayBook`** that receives a pointer to a `struct Book`.  
   4. **List all books** – Print the details of every stored book in the order they appear in the array.  
   5. **Exit** – Terminates the program.  

5. All traversals of the `books` array **must be performed using pointer arithmetic** (e.g., `for (struct Book *p = books; p < books + count; ++p)`), not by indexing (`books[i]`).  

6. The program should be robust against invalid input (e.g., non‑numeric menu choices) and should not cause buffer overflows when reading strings.

## Example Input / Output  

```
=== Library Book Manager ===
1) Add a new book
2) Remove a book
3) Display a book
4) List all books
5) Exit
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter copies: 4
Book added successfully.

=== Library Book Manager ===
1) Add a new book
2) Remove a book
3) Display a book
4) List all books
5) Exit
Choose an option: 4

--- Book List ---
ISBN: 9780131103627
Title: The C Programming Language
Copies: 4
--- End of List ---

=== Library Book Manager ===
1) Add a new book
2) Remove a book
3) Display a book
4) List all books
5) Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book` as described above.  
* **Display Function** – The details of ONE specific book must be displayed by a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Pointer Arithmetic Only** – All loops that walk through the `books` array must use pointers; array indexing (`books[i]`) is not permitted for those traversals.  
* **Menu Exit Option** – The menu must include an explicit “5) Exit” choice (or a clearly labeled keyword) that terminates the program.  

*Optional (but recommended for grading):*  
- Use `fgets` (or `scanf` with width limits) to read strings safely.  
- Separate the menu handling into its own function `void showMenu(void);`.  

---

## Problem 80 - openai/gpt-oss-120b - Iteration 100
# STEP 1: PROBLEM  

## Background  
The campus library is modernising its catalog system. Each book in the collection is stored as a record containing the book’s **ISBN**, **title**, **author**, and the **number of copies** currently on the shelf. The library wants a small command‑line utility that lets a librarian add new books, look up a book by its ISBN, and display the details of a specific book.  

Because the library’s database is kept in a simple array that may grow while the program runs, you must manage the array with pointers and pointer arithmetic rather than using high‑level containers.

## Requirements  

1. **Data representation**  
   - Define a `struct Book` that holds:  
     ```c
     char isbn[14];      // 13‑digit ISBN + terminating '\0'
     char title[64];
     char author[48];
     int  copies;
     ```
2. **Dynamic array**  
   - At program start allocate space for **10** `Book` records using `malloc`.  
   - Keep track of the current number of stored books (`size`) and the current capacity (`capacity`).  
   - When the array becomes full, double its capacity with `realloc`. All pointer arithmetic must be performed manually (e.g., `bookPtr = basePtr + i;`).

3. **Menu‑driven interface** (the program must present a menu and loop until the user chooses to exit)  
   - **1. Add a new book** – Prompt for ISBN, title, author, and copies, then store the record at the end of the array.  
   - **2. Find a book by ISBN** – Prompt for an ISBN, search the array using pointer arithmetic, and print “Found” or “Not found”.  
   - **3. Display a book** – Prompt for an ISBN, locate the matching record, and call a function `displayBook` (see Constraints) to print all its fields.  
   - **4. EXIT** – Terminate the program gracefully, freeing any allocated memory.  

4. **Input validation** – If the user selects an invalid menu option, print an error message and redisplay the menu.

## Example Input / Output  

```
=== Library Catalog ===
1) Add a new book
2) Find a book by ISBN
3) Display a book
4) EXIT
Choose an option: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter copies: 3
Book added successfully!

=== Library Catalog ===
1) Add a new book
2) Find a book by ISBN
3) Display a book
4) EXIT
Choose an option: 2

Enter ISBN to search: 9780131103627
Found!

=== Library Catalog ===
1) Add a new book
2) Find a book by ISBN
3) Display a book
4) EXIT
Choose an option: 3

Enter ISBN to display: 9780131103627
--- Book Details ---
ISBN   : 9780131103627
Title  : The C Programming Language
Author : Kernighan & Ritchie
Copies : 3

=== Library Catalog ===
1) Add a new book
2) Find a book by ISBN
3) Display a book
4) EXIT
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described above.  
2. **Display Function** – The logic for printing the details of ONE specific book **must** be placed in a function with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```  

3. **Pointer Arithmetic Only** – All traversals of the dynamic array must use pointer arithmetic (e.g., `*(basePtr + i)`) rather than array indexing (`array[i]`).  
4. **Single Additional Function** – Apart from `main` and `displayBook`, no other user‑defined functions are required (but you may create helper static functions if you wish, provided they are clearly documented).  
5. **Menu Exit Option** – The menu **must** include an option labelled exactly `4) EXIT` (or the keyword `EXIT`) that ends the program.  

*The problem is intended for students who have just learned pointers, pointer arithmetic, dynamic memory allocation, and basic `struct` usage.*

---

## Problem 81 - llama-3.3-70b-versatile - Iteration 61
# STEP 1: PROBLEM
In a university setting, you are tasked with managing a list of students enrolled in a course. Each student has a unique identifier, name, and grade point average (GPA). The list of students is stored in an array, and you need to write a program that allows you to navigate through the list using pointers and perform various operations.

You are the administrator of the student database, and you want to create a simple program that can display the details of each student, calculate the average GPA of all students, and allow the user to search for a specific student by their unique identifier.

The program should have the following functionality:
1. Display the details of all students in the list.
2. Calculate and display the average GPA of all students.
3. Search for a specific student by their unique identifier and display their details.
4. Allow the user to add a new student to the list.

### CONSTRAINTS
* The solution must be implemented using pointers and pointer arithmetic.
* Must use a `struct` to represent the primary data entity (Student).
* Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
* The program must have a menu-driven interface with the following options:
    1. Display all students
    2. Calculate average GPA
    3. Search for a student
    4. Add a new student
    5. EXIT (to exit the program)

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Display all students
2. Calculate average GPA
3. Search for a student
4. Add a new student
5. EXIT

Choose an option: 1
Student 1: ID = 101, Name = John, GPA = 3.5
Student 2: ID = 102, Name = Alice, GPA = 3.8

Choose an option: 2
Average GPA: 3.65

Choose an option: 3
Enter student ID: 101
Student 1: ID = 101, Name = John, GPA = 3.5

Choose an option: 5
Exiting program...
```
Note: The program should handle invalid inputs and edge cases, such as an empty list of students or a non-existent student ID.

---

## Problem 82 - llama-3.3-70b-versatile - Iteration 62
# STEP 1: PROBLEM
In a university setting, student records are essential for maintaining and tracking student information. To efficiently manage these records, you have been tasked with designing a program that utilizes pointers and pointer arithmetic to store and display student details.

The program should store student records, each containing a student ID, name, and grade point average (GPA). The student records should be stored in a dynamically allocated array, and the program should provide options to add a new student record, display all student records, and display the details of a specific student record.

### REQUIREMENTS
- The program must dynamically allocate memory for the student records array.
- The program must provide the following functionalities:
  1. Add a new student record.
  2. Display all student records.
  3. Display the details of a specific student record.
- The program must handle invalid inputs and memory allocation failures.

### EXAMPLE
Example Input:
```
Enter the number of students: 2
Enter student ID: 1
Enter student name: John Doe
Enter student GPA: 3.5
Enter student ID: 2
Enter student name: Jane Doe
Enter student GPA: 3.8
```
Example Output (after adding students and choosing to display all student records):
```
Student Records:
ID: 1, Name: John Doe, GPA: 3.5
ID: 2, Name: Jane Doe, GPA: 3.8
```

### CONSTRAINTS
- Must use a `struct` to represent the student record.
- Logic for displaying the details of all student records must be in a function called `displayAllRecords`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input.
- If a menu is implemented:
  - Must include a specific menu option to EXIT the program (option 4: 'EXIT').
  - Menu options:
    1. Add a new student record
    2. Display all student records
    3. Display a specific student record
    4. EXIT

Note: The program should be written in C, and the use of pointers and pointer arithmetic is mandatory.

---

## Problem 83 - llama-3.3-70b-versatile - Iteration 63
# STEP 1: PROBLEM
In a university setting, students often need to manage their grades across different courses. To help with this, you have been tasked with designing a simple program that uses pointers and pointer arithmetic to store and display student information. The program should allow users to add students, display student details, and calculate the average grade of all students.

The program's background story is that it will be used by a student union to keep track of member GPAs. The union wants a simple command-line interface where they can add new students, view student details, and see the average GPA of all members.

## REQUIREMENTS
1. The program must store student information, including name and GPA.
2. The program must allow users to add new students.
3. The program must display the details of all students.
4. The program must calculate and display the average GPA of all students.
5. The program must have a menu-driven interface.

## EXAMPLE
If the user adds two students, "John" with a GPA of 3.5 and "Alice" with a GPA of 3.8, the program should display the details of both students and calculate the average GPA as (3.5 + 3.8) / 2 = 3.65.

### CONSTRAINTS
- Must use a 'struct' to represent the student data entity.
- Logic for displaying the details of all students must be in a function called 'displayStudents'.
- The solution must be implemented with a single function besides main() to handle the menu and user input.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which will be option 4.

Example Input/Output:
```
1. Add Student
2. Display Students
3. Calculate Average GPA
4. Exit
Choose an option: 1
Enter student name: John
Enter student GPA: 3.5
1. Add Student
2. Display Students
3. Calculate Average GPA
4. Exit
Choose an option: 1
Enter student name: Alice
Enter student GPA: 3.8
1. Add Student
2. Display Students
3. Calculate Average GPA
4. Exit
Choose an option: 2
Student 1: John, GPA: 3.5
Student 2: Alice, GPA: 3.8
1. Add Student
2. Display Students
3. Calculate Average GPA
4. Exit
Choose an option: 3
Average GPA: 3.65
1. Add Student
2. Display Students
3. Calculate Average GPA
4. Exit
Choose an option: 4
Exiting program...
```

---

## Problem 84 - llama-3.3-70b-versatile - Iteration 64
# STEP 1: PROBLEM
In a university setting, students' records are maintained using a database system. To improve the efficiency of the system, you are tasked with designing a program that utilizes pointers and pointer arithmetic to manage student records. The program should be able to store, display, and update student information.

The background story is that the university wants to keep track of its students' names, IDs, and GPAs. The program should be able to handle a dynamic number of students and perform operations such as adding a new student, displaying all students, and updating a student's GPA.

### REQUIREMENTS
The program must meet the following requirements:
1. Store student records in a dynamically allocated array of structs, where each struct represents a student with attributes: name, ID, and GPA.
2. Implement a function to add a new student to the array, allocating memory as needed.
3. Implement a function to display all students in the array.
4. Implement a function to update a student's GPA given their ID.
5. The program must handle memory deallocation when the program exits.

### EXAMPLE
Example input:
```
Add a new student with name "John Doe", ID "S123", and GPA 3.5
Add a new student with name "Jane Doe", ID "S456", and GPA 3.8
Display all students
Update GPA of student with ID "S123" to 3.6
Display all students
```
Example output:
```
Student 1: John Doe, S123, GPA: 3.5
Student 2: Jane Doe, S456, GPA: 3.8
Student 1: John Doe, S123, GPA: 3.6
Student 2: Jane Doe, S456, GPA: 3.8
```
### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Student).
- Logic for displaying the details of ALL students must be in a function called `displayStudents`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu options.
- If a menu is implemented, it must include the following options:
  1. Add a new student
  2. Display all students
  3. Update a student's GPA
  4. EXIT the program (option 4)

Note: The program should be designed to handle a dynamic number of students, and the menu should be user-friendly and easy to navigate. The `EXIT` option should be clearly labeled as option 4.

---

## Problem 85 - llama-3.3-70b-versatile - Iteration 65
# STEP 1: PROBLEM
In a university setting, a professor wants to keep track of student records, specifically their names, student IDs, and grades. To efficiently manage this data, the professor decides to use an array of structures, where each structure represents a student. The professor needs a program that can perform basic operations such as adding a new student, displaying all students, and finding a student by their ID.

The program should have the following functionalities:
1. Add a new student to the array.
2. Display all students in the array.
3. Find a student by their ID and display their details.
4. Exit the program.

### CONSTRAINTS
- The program must use a `struct` to represent the student data entity.
- The logic for displaying the details of all students must be in a function called `displayAllStudents`.
- The logic for finding a student by their ID and displaying their details must be in a function called `findStudent`.
- The program must be implemented with a single loop in the `main` function to continuously prompt the user for input until they choose to exit.
- If a menu is implemented, it must include a specific option to EXIT the program, which should be option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Enter your choice:
1. Add a new student
2. Display all students
3. Find a student by ID
4. Display menu
5. Exit
```
User chooses option 1:
```
Enter student name: John Doe
Enter student ID: S1234
Enter grade: 85
```
User chooses option 2:
```
Student Name: John Doe
Student ID: S1234
Grade: 85
```
User chooses option 3:
```
Enter student ID to find: S1234
Student Name: John Doe
Student ID: S1234
Grade: 85
```
User chooses option 5:
```
Exiting the program...
```

---

## Problem 86 - llama-3.3-70b-versatile - Iteration 66
# STEP 1: PROBLEM
You are the administrator of a university's student database system. The system stores information about each student, including their student ID, name, and GPA. You need to design a program that can efficiently store and manage this data using pointers and pointer arithmetic.

The program should be able to perform the following operations:
1. Initialize an array of student structures with a specified size.
2. Allow users to add new students to the database.
3. Display the details of all students in the database.
4. Search for a student by their student ID and display their details.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu options.
- If a menu is implemented, it must include the following options:
  - Option 1: Add a new student
  - Option 2: Display all students
  - Option 3: Search for a student by ID
  - Option 4: EXIT the program

### EXAMPLE
Example Input:
```
Enter the size of the student database: 5
Enter student ID: S001
Enter student name: John Doe
Enter student GPA: 3.5
```
Example Output:
```
Student ID: S001
Student Name: John Doe
Student GPA: 3.5
```
Note: The program should handle invalid inputs and edge cases, such as attempting to add more students than the specified size or searching for a non-existent student ID.

---

## Problem 87 - llama-3.3-70b-versatile - Iteration 67
# STEP 1: PROBLEM
In a simple library management system, books are stored on shelves. Each book has a unique identifier (ID), title, and author. The system needs to efficiently manage and display information about these books. The library uses an array to store the books, and the system administrator wants to implement a program that uses pointers and pointer arithmetic to navigate through the array and display book details.

The program should have the following functionality:
1. Initialize an array of books with some sample data.
2. Display a menu to the user with the following options:
   - Display all books
   - Display a specific book by ID
   - Exit the program
3. Based on the user's choice, perform the corresponding action.

Simple Example of expected Input/Output:
```
Initial Book List:
Book ID: 1, Title: "Book1", Author: "Author1"
Book ID: 2, Title: "Book2", Author: "Author2"
Book ID: 3, Title: "Book3", Author: "Author3"

Menu:
1. Display all books
2. Display a specific book by ID
3. Exit

User Input: 2
Enter Book ID: 2
Book ID: 2, Title: "Book2", Author: "Author2"

Menu:
1. Display all books
2. Display a specific book by ID
3. Exit

User Input: 3
Exiting the program...
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBookByID'.
- The solution must be implemented using pointers and pointer arithmetic to navigate through the array of books.
- The program must have a menu with options to display all books, display a specific book by ID, and exit the program. The exit option must be option 3, and the user must enter '3' to exit the program.

---

## Problem 88 - llama-3.3-70b-versatile - Iteration 68
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a Computer Science professor, you want to create a simple program that utilizes pointers and pointer arithmetic to manage student records. The program should be able to store student details, display them, and allow the user to navigate through the records.

The background story is that the university has just started a new semester, and the administration wants to digitalize the student records. The task is to design a program that can efficiently store and display student information.

The program's functionality requirements are as follows:
1. The program should be able to store student records, where each record consists of a student ID (integer), name (string), and grade (float).
2. The program should display a menu with options to add a new student record, display all student records, display a specific student record, and exit the program.
3. When adding a new student record, the program should prompt the user to enter the student ID, name, and grade.
4. When displaying all student records, the program should print out the details of each student in a formatted manner.
5. When displaying a specific student record, the program should prompt the user to enter the student ID and then print out the details of the corresponding student.

Here's a simple example of expected input/output:
```
Menu:
1. Add a new student record
2. Display all student records
3. Display a specific student record
4. Exit the program
Enter your choice: 1
Enter student ID: 123
Enter student name: John Doe
Enter student grade: 85.5
Menu:
1. Add a new student record
2. Display all student records
3. Display a specific student record
4. Exit the program
Enter your choice: 2
Student ID: 123, Name: John Doe, Grade: 85.5
```

### CONSTRAINTS
* The program must use a `struct` to represent the student record.
* The logic for displaying the details of all student records must be in a function called `displayAllRecords`.
* The logic for displaying the details of a specific student record must be in a function called `displaySpecificRecord`.
* The program must use pointer arithmetic to navigate through the student records.
* If a menu is implemented, it must include a specific menu option to exit the program, which is option 4 or the keyword "EXIT".
* The maximum number of student records that can be stored is 100. If the user tries to add more than 100 records, the program should display an error message and not add the new record.

---

## Problem 89 - llama-3.3-70b-versatile - Iteration 69
# STEP 1: PROBLEM
You are the curator of a museum with a vast collection of artifacts from different historical periods. To efficiently manage and display the artifacts, you want to create a program that stores the details of each artifact and allows users to navigate through the collection. The program should utilize pointers and pointer arithmetic to manage the collection.

The museum has a collection of artifacts, each with a unique identifier, name, and historical period. You want to create a program that can store the details of these artifacts and perform basic operations such as displaying the details of a specific artifact and navigating through the collection.

### REQUIREMENTS
The program must have the following functionality:
1. Store the details of each artifact in a struct.
2. Allow users to navigate through the collection using pointer arithmetic.
3. Display the details of a specific artifact.
4. Provide a menu for users to interact with the program.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Enter the number of artifacts: 3
Enter the details of artifact 1:
Enter unique identifier: 1
Enter name: Artifact 1
Enter historical period: Ancient
Enter the details of artifact 2:
Enter unique identifier: 2
Enter name: Artifact 2
Enter historical period: Medieval
Enter the details of artifact 3:
Enter unique identifier: 3
Enter name: Artifact 3
Enter historical period: Modern
```
Example Output:
```
Menu:
1. Display artifact details
2. Navigate through collection
3. EXIT
Enter your choice: 1
Enter the unique identifier of the artifact: 2
Artifact 2, Ancient is not correct, it is actually from Medieval
```
### CONSTRAINTS
* The solution must be implemented using a `struct` to represent the primary data entity (i.e., the artifact).
* The logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
* The program must include a menu with the following options:
	+ Display artifact details (option 1)
	+ Navigate through collection (option 2)
	+ EXIT the program (option 3)
* The program must use pointer arithmetic to navigate through the collection.

Note: The program should be able to handle a variable number of artifacts, and the user should be able to add or remove artifacts as needed. However, for simplicity, this example assumes a fixed number of artifacts.

---

## Problem 90 - llama-3.3-70b-versatile - Iteration 70
# STEP 1: PROBLEM
In a small library, books are stored on shelves, and each book has a unique identifier, title, author, and publication year. The library wants to create a simple system to manage its book collection using pointers and pointer arithmetic. The system should be able to store book information, display details of all books, and display details of a specific book by its identifier.

Background: The library has a limited number of books, and the system should be able to handle a maximum of 100 books.

Requirements:
1. The program should ask the user to input the number of books they want to add to the system.
2. For each book, the program should ask the user to input the book's identifier, title, author, and publication year.
3. The program should store the book information in an array of structures, where each structure represents a book.
4. The program should display a menu with the following options:
   - Add a book
   - Display all books
   - Display a specific book by its identifier
   - EXIT

Simple Example of expected Input/Output:
```
Enter the number of books: 2
Enter book 1 details:
Identifier: 1
Title: Book1
Author: Author1
Publication Year: 2020
Enter book 2 details:
Identifier: 2
Title: Book2
Author: Author2
Publication Year: 2021

Menu:
1. Add a book
2. Display all books
3. Display a specific book
4. EXIT

Choose an option: 2
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
- The solution must be implemented using a 'struct' to represent a book.
- The logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The program must use pointer arithmetic to access and manipulate the book information stored in the array of structures.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 4.
- The program must handle invalid inputs, such as a user entering a non-integer value when asked for a number.

---

## Problem 91 - llama-3.3-70b-versatile - Iteration 71
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a Computer Science professor, you want to create a simple program that stores and manages student records using pointers and pointer arithmetic. The program should be able to store student names and grades, and perform basic operations such as displaying student records and calculating the average grade.

The program should have the following functionality:
1. Store student records in an array of structures, where each structure represents a student with a name and a grade.
2. Allow the user to add new student records.
3. Display all student records.
4. Calculate and display the average grade of all students.
5. Allow the user to search for a specific student by name and display their record.

### CONSTRAINTS
- The solution must be implemented using a single function besides main(), called `manageStudentRecords`.
- Must use a `struct` to represent the primary data entity (student record).
- The program must include a menu with the following options:
  1. Add new student record
  2. Display all student records
  3. Calculate and display the average grade
  4. Search for a specific student
  5. EXIT the program
- The menu option to EXIT the program is option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add new student record
Enter student name: John Doe
Enter student grade: 85
2. Display all student records
```
Example Output:
```
Student Records:
Name: John Doe, Grade: 85
```
Note: The program should be able to handle multiple student records and perform the specified operations correctly.

---

## Problem 92 - llama-3.3-70b-versatile - Iteration 72
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a programmer, you are tasked with designing a simple program to manage student records using pointers and pointer arithmetic. The program should be able to store student details, display specific student records, and provide basic navigation through a menu.

The background story is that the university wants to automate its student record-keeping process. The records include the student's ID, name, and grade point average (GPA). The university wants a simple console-based application to manage these records.

The program's functionality requirements are as follows:
1. The program should be able to store up to 100 student records.
2. It should allow users to add new student records.
3. It should display all student records.
4. It should allow users to search for a specific student record by ID and display the details.
5. It should have a menu-driven interface for easy navigation.

Here's a simple example of expected input/output:
- When adding a new student record, the user should be prompted to enter the student's ID, name, and GPA. For example:
    - Enter Student ID: 1234
    - Enter Student Name: John Doe
    - Enter Student GPA: 3.5
- When displaying all student records, the program should list each student's ID, name, and GPA in a formatted manner.

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle the menu and user interactions.
- If a menu is implemented, it must include the following options:
    1. Add New Student Record
    2. Display All Student Records
    3. Search for Student Record by ID
    4. EXIT the program
- The EXIT option should be clearly labeled as "4. EXIT" in the menu, and entering '4' should terminate the program.

Example Menu:
```
Student Record Management System
1. Add New Student Record
2. Display All Student Records
3. Search for Student Record by ID
4. EXIT
Choose an option:
```

---

## Problem 93 - llama-3.3-70b-versatile - Iteration 73
# STEP 1: PROBLEM
You are the curator of a museum with a collection of artifacts from around the world. To manage the collection, you want to create a simple program that stores information about each artifact, including its name, description, and storage location. Since the museum has a vast collection, you want to use pointers and pointer arithmetic to efficiently manage the data.

The program should store the artifact information in a struct, with each struct representing an artifact. The program should allow users to add new artifacts, display the details of all artifacts, and display the details of a specific artifact.

### REQUIREMENTS
1. The program should define a struct to represent an artifact, with fields for name, description, and storage location.
2. The program should have a function to add a new artifact to the collection.
3. The program should have a function to display the details of all artifacts in the collection.
4. The program should have a function to display the details of a specific artifact, given its index in the collection.
5. The program should have a menu-driven interface to allow users to interact with the program.

### EXAMPLE
If the user adds three artifacts with the following information:
- Artifact 1: Name = "Vase", Description = "Ancient Greek vase", Storage Location = "Gallery 1"
- Artifact 2: Name = "Painting", Description = "Modern art painting", Storage Location = "Gallery 2"
- Artifact 3: Name = "Sculpture", Description = "Ancient Roman sculpture", Storage Location = "Gallery 3"

The program should display the following output when the user chooses to display all artifacts:
```
Artifact 1:
Name: Vase
Description: Ancient Greek vase
Storage Location: Gallery 1

Artifact 2:
Name: Painting
Description: Modern art painting
Storage Location: Gallery 2

Artifact 3:
Name: Sculpture
Description: Ancient Roman sculpture
Storage Location: Gallery 3
```

### CONSTRAINTS
1. The solution must be implemented using a struct to represent the artifact.
2. The logic for displaying the details of all artifacts must be in a function called `displayAllArtifacts`.
3. The logic for displaying the details of a specific artifact must be in a function called `displayArtifact`.
4. The program must use pointers and pointer arithmetic to manage the artifact data.
5. The program must have a menu-driven interface with the following options:
   - Option 1: Add a new artifact
   - Option 2: Display all artifacts
   - Option 3: Display a specific artifact
   - Option 4: EXIT the program

Note: The user can exit the program by choosing Option 4.

---

## Problem 94 - llama-3.3-70b-versatile - Iteration 74
# STEP 1: PROBLEM
In a simple library management system, books are stored on shelves. Each book has a unique identifier (ISBN), title, author, and publication year. To efficiently manage the books, the library uses a pointer-based system to keep track of the books on each shelf.

The library has decided to implement a simple console-based application to manage the books. The application should be able to store information about the books, display the details of a specific book, and allow users to navigate through the collection.

### REQUIREMENTS
The program must:
1. Store information about the books in an array of structures, where each structure represents a book with its ISBN, title, author, and publication year.
2. Implement pointer arithmetic to navigate through the array of books.
3. Provide a menu-driven interface to interact with the application.
4. Allow users to display the details of a specific book by its ISBN.
5. Allow users to exit the program.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
Enter the number of books: 2
Enter ISBN of book 1: 1234567890
Enter title of book 1: Book1
Enter author of book 1: Author1
Enter publication year of book 1: 2020
Enter ISBN of book 2: 2345678901
Enter title of book 2: Book2
Enter author of book 2: Author2
Enter publication year of book 2: 2021
```
Example Output (after selecting the option to display a book's details):
```
Enter the ISBN of the book to display its details: 1234567890
ISBN: 1234567890
Title: Book1
Author: Author1
Publication Year: 2020
```
### CONSTRAINTS
* The solution must be implemented using a `struct` to represent a book.
* The logic for displaying the details of a specific book must be in a function called `displayBook`.
* The program must use pointer arithmetic to navigate through the array of books.
* The menu must include the following options:
	+ Option 1: Add a new book
	+ Option 2: Display a book's details
	+ Option 3: Exit the program
* To exit the program, the user must select Option 3.

Note: The program should handle invalid inputs and errors, such as attempting to display a book's details with an invalid ISBN.

---

## Problem 95 - llama-3.3-70b-versatile - Iteration 75
# STEP 1: PROBLEM
You are the administrator of a library management system. The system needs to maintain information about books, including title, author, publication year, and the shelf where the book is located. The system should be able to store, display, and update book information. To optimize memory usage, the system will utilize pointers and pointer arithmetic.

Background:
The library has a large collection of books, and the management system should be efficient in terms of memory usage. The system will store information about each book in a struct, and pointers will be used to navigate and manipulate the data.

Requirements:
1. The program should define a struct to represent a book with the following members: title (character array), author (character array), publication year (integer), and shelf (character array).
2. The program should dynamically allocate memory for an array of books.
3. The program should have a function to add a new book to the system.
4. The program should have a function to display the details of all books in the system.
5. The program should have a function to update the shelf of a specific book.

Example of expected Input/Output:
```
Enter the number of books: 2
Enter title of book 1: Book1
Enter author of book 1: Author1
Enter publication year of book 1: 2020
Enter shelf of book 1: Shelf1
Enter title of book 2: Book2
Enter author of book 2: Author2
Enter publication year of book 2: 2021
Enter shelf of book 2: Shelf2

Book List:
Title: Book1, Author: Author1, Publication Year: 2020, Shelf: Shelf1
Title: Book2, Author: Author2, Publication Year: 2021, Shelf: Shelf2

Update shelf of book 1 to Shelf3

Book List:
Title: Book1, Author: Author1, Publication Year: 2020, Shelf: Shelf3
Title: Book2, Author: Author2, Publication Year: 2021, Shelf: Shelf2
```

### CONSTRAINTS
- Must use a struct to represent a book.
- The logic for displaying the details of all books must be in a function called `displayBooks`.
- The logic for updating the shelf of a book must be in a function called `updateShelf`.
- The solution must implement a menu-driven system with the following options:
  1. Add a new book
  2. Display all books
  3. Update shelf of a book
  4. EXIT the program (option 4)
- The program must use pointer arithmetic to navigate and manipulate the array of books.

---

## Problem 96 - llama-3.3-70b-versatile - Iteration 76
# STEP 1: PROBLEM
In a university setting, student records are crucial for tracking academic progress. To efficiently manage these records, you have been tasked with designing a simple program that utilizes pointers and pointer arithmetic to store and display student information.

Background:
The student records consist of a student's ID, name, and GPA. The program should allow users to add new student records, display all existing records, and search for a specific student by ID.

Requirements:
1. The program must be able to dynamically allocate memory for new student records.
2. It should provide options to add a new student record, display all student records, and search for a specific student record by ID.
3. The program must use pointer arithmetic to navigate through the allocated memory.

Example:
Input:
- Add a new student with ID = 1, name = "John Doe", GPA = 3.5
- Add a new student with ID = 2, name = "Jane Doe", GPA = 3.8
- Display all student records
- Search for a student with ID = 1

Output:
- When displaying all student records:
  - ID: 1, Name: John Doe, GPA: 3.5
  - ID: 2, Name: Jane Doe, GPA: 3.8
- When searching for a student with ID = 1:
  - ID: 1, Name: John Doe, GPA: 3.5

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of ONE specific student record must be in a function called 'displayStudent'.
- The solution must implement a menu-driven interface with the following options:
  1. Add a new student record
  2. Display all student records
  3. Search for a student record by ID
  4. EXIT the program (option 4)
- The program must handle memory deallocation when the user chooses to exit. 

Note: The program should be able to handle a variable number of student records, and it should not have any memory leaks.

---

## Problem 97 - llama-3.3-70b-versatile - Iteration 77
# STEP 1: PROBLEM
In a library management system, books are stored on shelves with unique identifiers. To manage the books efficiently, the system needs to keep track of the books' titles, authors, publication years, and their positions on the shelves. The library uses a pointer-based system to keep track of the books.

The background story is that the library has just introduced a new system to manage its books, and the librarian needs a program to store and display the details of the books.

The program's functionality should include the following requirements:
1. Store the details of the books in an array of structures.
2. Display the details of all the books.
3. Display the details of a specific book based on its position on the shelf.
4. Update the details of a specific book.

### CONSTRAINTS
- Must use a 'struct' to represent a book, which should include the title, author, publication year, and position on the shelf.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single function besides main() to handle the menu and user input.
- If a menu is implemented, it must include the following options:
  1. Display all books
  2. Display a specific book
  3. Update a book
  4. EXIT the program (option 4)

Example of expected Input/Output:
Input:
```
Enter the number of books: 3
Enter the title of book 1: Book1
Enter the author of book 1: Author1
Enter the publication year of book 1: 2020
Enter the position of book 1: 1
Enter the title of book 2: Book2
Enter the author of book 2: Author2
Enter the publication year of book 2: 2021
Enter the position of book 2: 2
Enter the title of book 3: Book3
Enter the author of book 3: Author3
Enter the publication year of book 3: 2022
Enter the position of book 3: 3
```
Output (after selecting option 2 to display a specific book):
```
Enter the position of the book to display: 2
Title: Book2
Author: Author2
Publication Year: 2021
Position: 2
```

---

## Problem 98 - llama-3.3-70b-versatile - Iteration 78
# STEP 1: PROBLEM
You are the curator of a library, and you want to create a simple program to manage the books in your collection. You have decided to use pointers and pointer arithmetic to efficiently store and retrieve book information.

Background:
The library has a vast collection of books, and you want to create a program that allows you to add, remove, and display book information. Each book has a title, author, and publication year.

Requirements:
1. The program must allow the user to add a new book to the collection.
2. The program must allow the user to remove a book from the collection by its title.
3. The program must allow the user to display all books in the collection.
4. The program must allow the user to display the details of a specific book by its title.

Example Input/Output:
```
Add a book:
Title: "Introduction to Computer Science"
Author: "John Doe"
Publication Year: 2020

Remove a book:
Title: "Introduction to Computer Science"

Display all books:
Title: "Introduction to Data Structures"
Author: "Jane Smith"
Publication Year: 2019
Title: "Introduction to Algorithms"
Author: "Bob Johnson"
Publication Year: 2021

Display a specific book:
Title: "Introduction to Data Structures"
Author: "Jane Smith"
Publication Year: 2019
```

### CONSTRAINTS
1. Must use a `struct` to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called `displayBook`.
3. The solution must be implemented with a single function besides `main()` to handle the menu and user input.
4. If a menu is implemented, it must include the following options:
   - Option 1: Add a book
   - Option 2: Remove a book
   - Option 3: Display all books
   - Option 4: Display a specific book
   - Option 5: EXIT the program

Note: The program must use pointers and pointer arithmetic to manage the book collection. The `struct` representing the Book entity must contain the title, author, and publication year as separate fields. The `displayBook` function must take a pointer to the Book `struct` as an argument.

---

## Problem 99 - llama-3.3-70b-versatile - Iteration 79
# STEP 1: PROBLEM
In a university setting, student records are crucial for management and organization. To efficiently manage these records, a system that utilizes pointers and pointer arithmetic can be beneficial. The goal of this assignment is to design a program that can store, display, and manage student records using pointers and pointer arithmetic.

Background:
The university wants to develop a simple console-based application to store and display student information. Each student record consists of a student ID, name, and GPA. The program should allow users to add new student records, display all student records, and search for a specific student record by ID.

Requirements:
1. The program should store student records in a dynamically allocated array.
2. The program should provide a menu-driven interface to add, display, and search for student records.
3. When adding a new student record, the program should prompt the user to enter the student ID, name, and GPA.
4. When displaying all student records, the program should print the student ID, name, and GPA for each record.
5. When searching for a specific student record, the program should prompt the user to enter the student ID and then display the corresponding record if found.

Example Input/Output:
```
Menu:
1. Add Student Record
2. Display All Student Records
3. Search for Student Record
4. Exit

Choose an option: 1
Enter Student ID: 1234
Enter Name: John Doe
Enter GPA: 3.5

Menu:
1. Add Student Record
2. Display All Student Records
3. Search for Student Record
4. Exit

Choose an option: 2
Student ID: 1234, Name: John Doe, GPA: 3.5

Menu:
1. Add Student Record
2. Display All Student Records
3. Search for Student Record
4. Exit

Choose an option: 3
Enter Student ID: 1234
Student ID: 1234, Name: John Doe, GPA: 3.5
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student record.
- The logic for displaying the details of one specific student record must be in a function called `displayStudentRecord`.
- The program must use pointer arithmetic to traverse the array of student records.
- The menu option to exit the program is option 4, labeled as "Exit".
- If a menu is implemented, it must include a specific menu option to exit the program, which is option 4 in this case.

---

## Problem 100 - llama-3.3-70b-versatile - Iteration 80
# STEP 1: PROBLEM
In a university setting, students often need to manage their grades and course information. To help with this, you have been tasked with creating a simple program that stores and displays student information using pointers and pointer arithmetic.

Background:
The university wants to keep track of each student's name, student ID, and GPA. The information for each student is stored in a struct, and the university wants to be able to display the information for all students, as well as the information for a specific student.

Requirements:
1. The program must store student information in a struct with the following fields: name (a character array of maximum length 50), student ID (an integer), and GPA (a floating-point number).
2. The program must allow the user to add new students to the system.
3. The program must allow the user to display the information for all students.
4. The program must allow the user to display the information for a specific student by student ID.
5. The program must handle memory allocation and deallocation using pointers and pointer arithmetic.

Example:
Input:
- Add a student with name "John Doe", student ID 12345, and GPA 3.5.
- Add a student with name "Jane Doe", student ID 67890, and GPA 3.8.
- Display all students.
- Display the student with ID 12345.

Output:
- When displaying all students:
  - John Doe, 12345, 3.5
  - Jane Doe, 67890, 3.8
- When displaying the student with ID 12345:
  - John Doe, 12345, 3.5

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Student).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all menu options.
- If a menu is implemented, it must include the following options:
  1. Add a new student
  2. Display all students
  3. Display a specific student
  4. EXIT the program
- The program must dynamically allocate memory for each new student added to the system.

Note: The program should be implemented in C, as it is the most suitable language for demonstrating pointers and pointer arithmetic.

---

