# Problem Batch Preview: Pointers and Pointer Arithmetic
**Batch Number:** 2 | **Total Problems:** 100

---

## Problem 1 - llama-3.3-70b-versatile - Iteration 81
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, tasked with managing the details of various computer labs on campus. Each lab has a unique identifier, name, capacity (number of computers), and a pointer to the next lab in the list. To efficiently manage these labs, you need to create a program that can store, display, and manipulate the lab details using pointers and pointer arithmetic.

### BACKGROUND
The university has multiple computer labs, and the department needs a simple system to keep track of the lab details. The system should allow for adding new labs, displaying the details of all labs, and finding a specific lab by its unique identifier.

### REQUIREMENTS
1. The program should store the lab details in a dynamically allocated linked list.
2. The program should have the following functionalities:
   - Add a new lab to the end of the list.
   - Display the details of all labs in the list.
   - Find and display the details of a specific lab by its unique identifier.
3. The program should handle memory allocation and deallocation for the linked list.

### EXAMPLE
If we have two labs with the following details:
- Lab 1: ID = 1, Name = "Lab A", Capacity = 20
- Lab 2: ID = 2, Name = "Lab B", Capacity = 30

The program should be able to display the details of all labs:
```
Lab ID: 1, Name: Lab A, Capacity: 20
Lab ID: 2, Name: Lab B, Capacity: 30
```
And find a specific lab by its ID:
```
Enter Lab ID to find: 1
Lab ID: 1, Name: Lab A, Capacity: 20
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (Lab).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input.
- If a menu is implemented, it must include a specific menu option to EXIT the program (option 4: "EXIT").

### MENU CONSTRAINTS (IF IMPLEMENTED)
The menu should have the following options:
1. Add a new lab
2. Display all labs
3. Find a lab by ID
4. EXIT

Example Menu:
```
1. Add a new lab
2. Display all labs
3. Find a lab by ID
4. EXIT
Choose an option:
```

---

## Problem 2 - llama-3.3-70b-versatile - Iteration 82
# STEP 1: PROBLEM
You are the curator of a large museum with an extensive collection of artifacts. To keep track of these artifacts, you want to create a simple program that can store and display their details. Each artifact has a unique identifier, name, and description. You have decided to use C programming to implement this system, utilizing pointers and pointer arithmetic to efficiently manage the data.

The program should be able to store information about multiple artifacts and display the details of a specific artifact when requested. To achieve this, you will implement a system that uses a struct to represent each artifact and dynamically allocates memory for these structs as needed.

### REQUIREMENTS
1. The program must allow users to add new artifacts to the collection.
2. The program must be able to display the details of all artifacts in the collection.
3. The program must be able to display the details of a specific artifact based on its unique identifier.
4. The program must handle memory allocation and deallocation properly to prevent memory leaks.

### EXAMPLE
If the user adds two artifacts with the following details:
- Artifact 1: ID = 1, Name = "Vase", Description = "Ancient Greek vase"
- Artifact 2: ID = 2, Name = "Painting", Description = "Modern art painting"

The program should be able to display all artifacts or a specific artifact based on its ID. For example, displaying the details of the artifact with ID 1 should output:
```
Artifact ID: 1
Name: Vase
Description: Ancient Greek vase
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (in this case, an artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle all operations related to adding and displaying artifacts.
- The program must include a simple menu with options to add an artifact, display all artifacts, display a specific artifact, and exit the program. The exit option must be clearly labeled as "4. Exit".

### MENU CONSTRAINTS
The menu must include the following options:
1. Add an artifact
2. Display all artifacts
3. Display a specific artifact
4. Exit

The program must exit when the user selects the "4. Exit" option.

---

## Problem 3 - llama-3.3-70b-versatile - Iteration 83
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As the Computer Science professor, you have decided to design a simple program that utilizes pointers and pointer arithmetic to manage student records. The program should store student information such as student ID, name, and GPA.

The program's background context is to provide a simple console-based application where users can add, display, and search for student records.

The program's functionality requirements are as follows:
1. Allow users to add new student records.
2. Display all student records.
3. Search for a specific student record by student ID.
4. Update a student's GPA given their student ID.

Here's a simple example of expected input/output:
- Add a new student record: `Student ID: 123, Name: John Doe, GPA: 3.5`
- Display all student records: `Student ID: 123, Name: John Doe, GPA: 3.5`
- Search for a student record: `Enter Student ID: 123, Output: Student ID: 123, Name: John Doe, GPA: 3.5`
- Update a student's GPA: `Enter Student ID: 123, New GPA: 3.8, Output: Student ID: 123, Name: John Doe, GPA: 3.8`

### CONSTRAINTS
- Must use a `struct` to represent the student record.
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle the menu and user input.
- If a menu is implemented:
  - Must include a specific menu option to EXIT the program, which is option `5` or the keyword `EXIT`.
  - Must have the following menu options:
    1. Add a new student record
    2. Display all student records
    3. Search for a student record
    4. Update a student's GPA
    5. EXIT the program

Example menu:
```
Student Record Management System
1. Add a new student record
2. Display all student records
3. Search for a student record
4. Update a student's GPA
5. EXIT
Choose an option:
```

---

## Problem 4 - llama-3.3-70b-versatile - Iteration 84
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, and you need to manage the student records. Each student has a unique ID, name, and grade point average (GPA). You want to create a program that allows you to store, display, and update student records using pointers and pointer arithmetic.

Background:
The university has a limited number of student records that can be stored in memory. You need to efficiently manage the memory to store and retrieve student records.

Requirements:
1. The program should dynamically allocate memory to store student records.
2. The program should allow the user to add a new student record.
3. The program should allow the user to display all student records.
4. The program should allow the user to update a student record by ID.
5. The program should allow the user to delete a student record by ID.

Example of expected Input/Output:
```
Add a new student record:
Enter student ID: 1
Enter student name: John Doe
Enter student GPA: 3.5

Display all student records:
ID: 1, Name: John Doe, GPA: 3.5

Update student record:
Enter student ID: 1
Enter new student name: Jane Doe
Enter new student GPA: 3.8

Display all student records:
ID: 1, Name: Jane Doe, GPA: 3.8
```

### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student record.
- The logic for displaying the details of all student records must be in a function called `displayRecords`.
- The program must include a menu with the following options:
  1. Add a new student record
  2. Display all student records
  3. Update a student record
  4. Delete a student record
  5. EXIT the program
- The program must use pointer arithmetic to manage the student records.
- The `EXIT` option must be chosen by entering the number `5`. 

Note: The program should handle memory allocation and deallocation efficiently to avoid memory leaks.

---

## Problem 5 - llama-3.3-70b-versatile - Iteration 85
# STEP 1: PROBLEM
In a university setting, student records are crucial for managing and tracking student information. As a Computer Science professor, you want to design a simple program to store and display student records using pointers and pointer arithmetic. The program should allow users to add student records, display all records, and search for a specific student by their ID.

Background:
The university wants to keep track of student information, including their ID, name, and GPA. The student records are stored in a dynamically allocated array, and the program should use pointers and pointer arithmetic to manage the records.

Requirements:
1. The program should allow users to add student records dynamically.
2. The program should display all student records.
3. The program should allow users to search for a specific student by their ID.
4. The program should handle memory allocation and deallocation for the student records.

Example:
Input: 
```
Add student with ID: 1, Name: John, GPA: 3.5
Add student with ID: 2, Name: Jane, GPA: 3.8
Display all students:
Student 1: ID: 1, Name: John, GPA: 3.5
Student 2: ID: 2, Name: Jane, GPA: 3.8
Search for student with ID: 1
Student found: ID: 1, Name: John, GPA: 3.5
```

### CONSTRAINTS
- Must use a `struct` to represent the student record.
- Logic for displaying the details of all student records must be in a function called `displayAllStudents`.
- The solution must be implemented with a single function besides `main()` to handle user input and program logic.
- If a menu is implemented, it must include the following options:
  1. Add student record
  2. Display all student records
  3. Search for a student by ID
  4. EXIT (to exit the program)

Note: The program should be well-structured, readable, and follow standard professional guidelines for coding. The use of pointers and pointer arithmetic is mandatory to manage the student records.

---

## Problem 6 - llama-3.3-70b-versatile - Iteration 86
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. As a computer science professor, you want to design a simple program to manage student records using pointers and pointer arithmetic.

Background:
The university wants to keep track of student information, including their names, student IDs, and GPAs. The program should allow users to add, display, and search for student records.

Requirements:
1. The program should be able to store student records in a dynamic array.
2. The program should provide a menu for users to add, display, and search for student records.
3. The program should use pointers and pointer arithmetic to manage the dynamic array.
4. The program should validate user input to ensure that student IDs are unique and GPAs are within the range of 0.0 to 4.0.

Example:
Input:
```
1. Add Student
2. Display Students
3. Search Student
4. Exit
```
User chooses option 1:
```
Enter student name: John Doe
Enter student ID: 12345
Enter GPA: 3.5
```
User chooses option 2:
```
Student Name: John Doe
Student ID: 12345
GPA: 3.5
```
User chooses option 3:
```
Enter student ID to search: 12345
Student Name: John Doe
Student ID: 12345
GPA: 3.5
```
### CONSTRAINTS
- The solution must be implemented using a `struct` to represent the student record.
- The logic for displaying the details of all student records must be in a function called `displayStudents`.
- The logic for searching for a specific student record must be in a function called `searchStudent`.
- The program must include a menu option to EXIT the program, which is option 4.
- The program must use a single dynamic array to store all student records.
- The program must use pointers and pointer arithmetic to manage the dynamic array.

---

## Problem 7 - llama-3.3-70b-versatile - Iteration 87
# STEP 1: PROBLEM
In a library management system, books are stored on shelves. Each book has a unique identifier, title, author, and publication year. The system uses an array to store information about the books and pointers to navigate through this array. Your task is to write a program that allows users to interact with the library's book collection by displaying book details, adding new books, and removing existing books.

### BACKGROUND
The library currently has a collection of books stored in an array, and the system uses pointers to manage this array. The program should provide a menu for users to perform various operations on the book collection.

### REQUIREMENTS
1. The program should display a menu with options to:
   - Display all books
   - Add a new book
   - Remove a book by its identifier
   - Display details of a specific book
   - Exit the program
2. The program should use a struct to represent each book, containing the unique identifier, title, author, and publication year.
3. The program should use pointer arithmetic to navigate through the array of books.
4. When displaying book details, the program should show the unique identifier, title, author, and publication year of the book.

### EXAMPLE
Input:
```
Choose an option:
1. Display all books
2. Add a new book
3. Remove a book
4. Display book details
5. Exit
```
User chooses option 2:
```
Enter book identifier: 1
Enter book title: Introduction to CS
Enter book author: John Doe
Enter book publication year: 2020
```
Output (after adding the book and choosing option 1):
```
Book 1:
   Identifier: 1
   Title: Introduction to CS
   Author: John Doe
   Publication Year: 2020
```

### CONSTRAINTS
- Must use a `struct` to represent each book.
- Logic for displaying the details of all books must be in a function called `displayAllBooks`.
- Logic for displaying the details of one specific book must be in a function called `displayBookDetails`.
- The solution must be implemented using a menu with a specific option to exit the program (option 5: Exit).
- The program should handle a maximum of 100 books in the collection.
- The program should use pointer arithmetic to add new books and remove existing books from the collection.

---

## Problem 8 - llama-3.3-70b-versatile - Iteration 88
# STEP 1: PROBLEM
In a university setting, students often need to manage their grades and course information. To simplify this process, you've been tasked with designing a program that utilizes pointers and pointer arithmetic to store and display student records. The program should allow users to add new students, display all students, and search for a specific student by their ID.

The program will store student information, including their ID, name, and GPA. The background story is that the university wants to create a simple console-based application to manage student records efficiently.

The requirements for the program's functionality are:
1. The program must store student records in a dynamically allocated array.
2. The program must provide options to add a new student, display all students, and search for a student by ID.
3. The program must use pointer arithmetic to navigate through the array of student records.
4. The program must handle memory deallocation to prevent memory leaks.

### CONSTRAINTS
- Must use a `struct` to represent the student data entity.
- Logic for displaying the details of all students must be in a function called `displayStudents`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which will be option 4, labeled as "Exit Program".

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add Student
2. Display Students
3. Search Student
4. Exit Program
```
User chooses option 1:
```
Enter student ID: 123
Enter student name: John Doe
Enter student GPA: 3.5
```
User chooses option 2:
```
Student ID: 123, Name: John Doe, GPA: 3.5
```
User chooses option 3:
```
Enter student ID to search: 123
Student ID: 123, Name: John Doe, GPA: 3.5
```
User chooses option 4:
```
Exiting program...
```

---

## Problem 9 - llama-3.3-70b-versatile - Iteration 89
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The librarian has a large collection of books and wants to store the details of each book, such as the title, author, and publication year. The librarian also wants to be able to display the details of each book and calculate the total number of books.

The program should use pointers and pointer arithmetic to store and manage the book details. The program should also have a simple menu that allows the librarian to add a new book, display the details of all books, and exit the program.

The background story is that the librarian has a small budget and cannot afford a commercial library management system. Therefore, the librarian needs a simple and efficient program to manage the book collection.

The requirements for the program's functionality are as follows:
1. The program should be able to store the details of each book, including the title, author, and publication year.
2. The program should have a function to add a new book to the collection.
3. The program should have a function to display the details of all books in the collection.
4. The program should have a simple menu that allows the librarian to add a new book, display the details of all books, and exit the program.

Here is a simple example of expected input/output:
```
Menu:
1. Add a new book
2. Display all books
3. Exit

Enter your choice: 1
Enter book title: Harry Potter
Enter book author: J.K. Rowling
Enter book publication year: 1997

Menu:
1. Add a new book
2. Display all books
3. Exit

Enter your choice: 2
Book 1:
Title: Harry Potter
Author: J.K. Rowling
Publication Year: 1997

Menu:
1. Add a new book
2. Display all books
3. Exit

Enter your choice: 3
Exiting the program...
```

### CONSTRAINTS
1. The solution must be implemented using a 'struct' to represent the book entity.
2. The logic for displaying the details of all books must be in a function called 'displayBooks'.
3. The program must use pointers and pointer arithmetic to store and manage the book details.
4. If a menu is implemented, it must include a specific menu option to EXIT the program, which is option 3.

Note: The program should be able to handle a maximum of 100 books. If the user tries to add more than 100 books, the program should display an error message and not add the new book.

---

## Problem 10 - llama-3.3-70b-versatile - Iteration 90
# STEP 1: PROBLEM
You are the manager of a bookstore, and you want to create a simple inventory management system to keep track of the books in your store. Each book has a unique identifier (ID), title, author, and price. You want to use pointers and pointer arithmetic to store and manage the book inventory.

The program should allow users to add new books to the inventory, display all books, and search for a specific book by its ID.

### REQUIREMENTS
1. The program should store the book inventory in an array of structures, where each structure represents a book with its ID, title, author, and price.
2. The program should have a function to add a new book to the inventory.
3. The program should have a function to display all books in the inventory.
4. The program should have a function to search for a specific book by its ID and display its details.

### EXAMPLE
If the user adds the following books to the inventory:
- Book 1: ID = 1, Title = "Book 1", Author = "Author 1", Price = 10.99
- Book 2: ID = 2, Title = "Book 2", Author = "Author 2", Price = 20.99
- Book 3: ID = 3, Title = "Book 3", Author = "Author 3", Price = 30.99

The program should display the following output when the user chooses to display all books:
```
Book 1: ID = 1, Title = "Book 1", Author = "Author 1", Price = 10.99
Book 2: ID = 2, Title = "Book 2", Author = "Author 2", Price = 20.99
Book 3: ID = 3, Title = "Book 3", Author = "Author 3", Price = 30.99
```

### CONSTRAINTS
1. Must use a `struct` to represent a book.
2. Must use pointers and pointer arithmetic to store and manage the book inventory.
3. Logic for displaying the details of all books must be in a function called `displayAllBooks`.
4. Logic for searching for a specific book by its ID and displaying its details must be in a function called `searchBook`.
5. The program must have a menu with the following options:
   - Add a new book (option 1)
   - Display all books (option 2)
   - Search for a book by ID (option 3)
   - EXIT the program (option 4)

Note: The user should be able to choose the EXIT option (option 4) to terminate the program.

---

## Problem 11 - llama-3.3-70b-versatile - Iteration 91
# STEP 1: PROBLEM
You are the curator of a university museum, and you want to create a simple program to manage the artifacts in the museum's collection. The museum has various types of artifacts, but for this program, you will focus on ancient statues. Each statue has a unique identifier, a name, a creation year, and a material (e.g., marble, bronze). You want to store the statues in an array and perform operations on them.

The program should allow you to:
1. Add a new statue to the collection.
2. Display all statues in the collection.
3. Display the details of a specific statue.
4. Update the material of a specific statue.
5. Remove a statue from the collection.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (i.e., the statue).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle all menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program. The exit option should be option 6, labeled as "EXIT".

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add statue
Name: Statue1
Creation Year: 1000
Material: Marble

2. Display all statues
3. Display specific statue
ID: 0
4. Update material
ID: 0
New Material: Granite
5. Remove statue
ID: 0
6. EXIT
```
Example Output:
```
After adding Statue1:
ID: 0, Name: Statue1, Creation Year: 1000, Material: Marble

After displaying all statues:
ID: 0, Name: Statue1, Creation Year: 1000, Material: Marble

After updating material:
ID: 0, Name: Statue1, Creation Year: 1000, Material: Granite

After removing statue:
Statue with ID 0 removed.
```
Note: The ID of each statue will be assigned automatically based on the order of addition. The `displayEntity` function should take a pointer to the statue `struct` as an argument. The `main` function will handle user input and call the required functions to perform the operations.

---

## Problem 12 - llama-3.3-70b-versatile - Iteration 92
# STEP 1: PROBLEM
You are the administrator of a university's computer science department, and you need to manage the student records. Each student has a unique ID, name, and GPA. You want to create a program that stores the student records in an array and allows users to perform various operations on the records.

The program should be able to:
1. Add a new student record to the array.
2. Display all student records.
3. Search for a student by ID and display their record.
4. Update a student's GPA.
5. Delete a student record.

### CONSTRAINTS
* The student records must be stored in a struct called `Student`.
* The program must use pointer arithmetic to access and manipulate the student records.
* The solution must be implemented with two functions besides `main()`: `displayStudent` and `updateStudent`.
* A menu must be implemented to allow users to choose the operation they want to perform. The menu options are:
	1. Add a new student record
	2. Display all student records
	3. Search for a student by ID
	4. Update a student's GPA
	5. Delete a student record
	6. EXIT the program

Example of expected Input/Output:
```
Menu:
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Update a student's GPA
5. Delete a student record
6. EXIT

Choose an option: 1
Enter student ID: 1234
Enter student name: John Doe
Enter student GPA: 3.5

Menu:
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Update a student's GPA
5. Delete a student record
6. EXIT

Choose an option: 2
Student ID: 1234, Name: John Doe, GPA: 3.5

Menu:
1. Add a new student record
2. Display all student records
3. Search for a student by ID
4. Update a student's GPA
5. Delete a student record
6. EXIT

Choose an option: 6
Exiting the program...
```
Note: The `displayStudent` function should take a `Student*` pointer as an argument and display the student's record. The `updateStudent` function should take a `Student*` pointer and a new GPA as arguments and update the student's GPA.

---

## Problem 13 - llama-3.3-70b-versatile - Iteration 93
# STEP 1: PROBLEM
In a small library, the librarian wants to manage the books using a computer program. The program should be able to store the details of each book and display them as needed. The details of each book include the title, author, and publication year.

### BACKGROUND
The librarian has a collection of books and wants to create a digital catalog. The catalog should allow the librarian to add new books, display the details of all books, and display the details of a specific book.

### REQUIREMENTS
The program should have the following functionality:
1. Store the details of each book in a struct.
2. Allow the user to add a new book to the catalog.
3. Display the details of all books in the catalog.
4. Display the details of a specific book.
5. The program should use pointer arithmetic to traverse the array of book structs.

### EXAMPLE
If the user adds two books with the following details:
- Book 1: Title = "Book1", Author = "Author1", Year = 2020
- Book 2: Title = "Book2", Author = "Author2", Year = 2021
The program should display the details of all books as:
- Book 1: Title = "Book1", Author = "Author1", Year = 2020
- Book 2: Title = "Book2", Author = "Author2", Year = 2021
If the user wants to display the details of a specific book (e.g., the first book), the program should display:
- Book 1: Title = "Book1", Author = "Author1", Year = 2020

### CONSTRAINTS
- The solution must be implemented using a single array of structs to represent all books.
- The logic for displaying the details of all books must be in a function called `displayAllBooks`.
- The logic for displaying the details of a specific book must be in a function called `displayBook`.
- The program must use pointer arithmetic to traverse the array of book structs.
- The program must include a menu with the following options:
  1. Add a new book
  2. Display all books
  3. Display a specific book
  4. EXIT the program
- The program must exit when the user chooses the EXIT option (option 4). 

Note: The program should be able to handle a maximum of 100 books. If the user tries to add more than 100 books, the program should display an error message.

---

## Problem 14 - llama-3.3-70b-versatile - Iteration 94
# STEP 1: PROBLEM
You are the administrator of a library management system, and you want to create a program to manage the catalog of books. The program should store information about each book, including its title, author, publication year, and price. You have decided to use pointers and pointer arithmetic to efficiently manage the memory allocated for the books.

The program should allow users to add new books to the catalog, display the details of all books, and search for a specific book by its title. The program should also include a menu-driven interface to make it easy for users to interact with the system.

### REQUIREMENTS
1. The program should store the book information in a dynamically allocated array of structures, where each structure represents a book.
2. The program should have a menu-driven interface with the following options:
   - Add a new book to the catalog
   - Display the details of all books
   - Search for a specific book by its title
   - Exit the program
3. The program should use pointers and pointer arithmetic to manage the memory allocated for the books.
4. The program should validate user input to ensure that the publication year is a positive integer and the price is a non-negative floating-point number.

### EXAMPLE INPUT/OUTPUT
```
Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit

Enter your choice: 1
Enter book title: Introduction to Computer Science
Enter author: John Smith
Enter publication year: 2020
Enter price: 50.00

Menu:
1. Add a new book
2. Display all books
3. Search for a book
4. Exit

Enter your choice: 2
Book 1:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020
Price: 50.00
```

### CONSTRAINTS
- The solution must be implemented using a single function called `manageLibrary` besides the `main` function.
- The `manageLibrary` function should use pointers and pointer arithmetic to manage the memory allocated for the books.
- The program must include a specific menu option to EXIT the program, which is option 4.
- The program must use a `struct` to represent the primary data entity, which is the book.
- The logic for displaying the details of all books must be in a loop within the `manageLibrary` function.

---

## Problem 15 - llama-3.3-70b-versatile - Iteration 95
# STEP 1: PROBLEM
You are a librarian in charge of managing the inventory of books in a library. Each book has a unique identifier, title, author, and publication year. You want to create a program that allows you to store and manage the book collection using pointers and pointer arithmetic.

The program should be able to store information about multiple books and display the details of each book. The program should also be able to calculate the total number of books and the average publication year of all the books.

Here is a precise list of requirements for the program's functionality:
1. Store information about multiple books, including the unique identifier, title, author, and publication year.
2. Display the details of each book.
3. Calculate the total number of books.
4. Calculate the average publication year of all the books.

Here is a simple example of expected input/output:
Input:
```
Enter the number of books: 2
Enter book 1 details:
Enter unique identifier: 1
Enter title: Book1
Enter author: Author1
Enter publication year: 2010
Enter book 2 details:
Enter unique identifier: 2
Enter title: Book2
Enter author: Author2
Enter publication year: 2015
```
Output:
```
Book 1:
Unique Identifier: 1
Title: Book1
Author: Author1
Publication Year: 2010
Book 2:
Unique Identifier: 2
Title: Book2
Author: Author2
Publication Year: 2015
Total number of books: 2
Average publication year: 2012.5
```
### CONSTRAINTS
* The solution must be implemented using a `struct` to represent a book.
* The logic for displaying the details of all books must be in a function called `displayBooks`.
* The solution must include a menu with the following options:
	1. Add a new book
	2. Display all books
	3. Calculate total number of books
	4. Calculate average publication year
	5. EXIT (to exit the program)
* The menu must be implemented in the `main` function, and the program must use a loop to continuously display the menu until the user chooses to exit.

---

## Problem 16 - llama-3.3-70b-versatile - Iteration 96
# STEP 1: PROBLEM
In a university setting, student records are crucial for tracking academic performance. To efficiently manage these records, a system that utilizes pointers and pointer arithmetic can be beneficial. The goal is to design a program that can store, display, and manipulate student records.

Background:
A student record consists of a name, student ID, and grade point average (GPA). The university wants to create a simple system to store and display these records.

Requirements:
1. The program must be able to store up to 100 student records.
2. The program must display all stored student records.
3. The program must allow the user to add a new student record.
4. The program must allow the user to search for a student record by student ID and display the details of the found record.
5. The program must allow the user to update the GPA of a student record by student ID.

Example Input/Output:
- When the user chooses to display all records, the program should print out each student's name, ID, and GPA.
- When the user chooses to add a new record, the program should prompt for the name, ID, and GPA, then store the new record.
- When the user searches for a record by ID, the program should display the name, ID, and GPA of the matching record if found.

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of all student records must be in a function called 'displayRecords'.
- Logic for searching for a student record by ID must be in a function called 'searchRecord'.
- The program must implement a menu-driven interface with the following options:
  1. Display all records
  2. Add a new record
  3. Search for a record by ID
  4. Update GPA of a record by ID
  5. EXIT the program
- The program must use pointer arithmetic to manipulate the student records.

Note: The program should handle cases where the user attempts to add more than 100 records or searches for a non-existent record. In such cases, appropriate error messages should be displayed.

---

## Problem 17 - llama-3.3-70b-versatile - Iteration 97
# STEP 1: PROBLEM
You are the curator of a university library, and you want to create a simple program to manage the books in the library. The library has a collection of books, each with a title, author, and publication year. You want to store the books in an array and perform various operations on the array using pointers and pointer arithmetic.

The program should allow users to add a new book, display all books, and search for a specific book by title. The program should also keep track of the number of books in the library.

### REQUIREMENTS
1. The program should store the books in an array of structures, where each structure represents a book with title, author, and publication year.
2. The program should have a function to add a new book to the array.
3. The program should have a function to display all books in the array.
4. The program should have a function to search for a specific book by title.
5. The program should keep track of the number of books in the library.

### EXAMPLE
If the user adds the following books:
- Title: "Introduction to Computer Science", Author: "John Smith", Year: 2020
- Title: "Data Structures and Algorithms", Author: "Jane Doe", Year: 2019
- Title: "Computer Networks", Author: "Bob Johnson", Year: 2021

The program should display the following output when the user chooses to display all books:
```
Book 1:
Title: Introduction to Computer Science
Author: John Smith
Year: 2020

Book 2:
Title: Data Structures and Algorithms
Author: Jane Doe
Year: 2019

Book 3:
Title: Computer Networks
Author: Bob Johnson
Year: 2021
```

### CONSTRAINTS
- The solution must be implemented using a single function besides main(), which will be responsible for handling the menu and user input.
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The program must include a menu with the following options:
  - Add a new book
  - Display all books
  - Search for a book by title
  - EXIT the program (option 4)

Note: The program should use pointers and pointer arithmetic to perform operations on the array of books.

---

## Problem 18 - llama-3.3-70b-versatile - Iteration 98
# STEP 1: PROBLEM
Imagine you are the curator of a museum with a collection of unique artifacts, each with its own set of attributes such as name, year of creation, and the artist who created it. To efficiently manage this collection, you decide to create a program that utilizes pointers and pointer arithmetic to store and manipulate the data of these artifacts.

Your program should be able to perform the following functionalities:
1. Dynamically allocate memory for a specified number of artifacts.
2. Allow users to input the details of each artifact (name, year of creation, artist).
3. Display the details of all artifacts.
4. Given the index of an artifact, display the details of that specific artifact.
5. Update the details of a specific artifact given its index.

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (in this case, an artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` for handling user interactions and operations.
- If a menu is implemented, it must include a specific menu option to EXIT the program. The exit option should be clearly labeled as "5. Exit".

### EXAMPLE INPUT/OUTPUT
Example Input:
- Number of artifacts: 2
- Artifact 1 details: Name = "Mona Lisa", Year = 1503, Artist = "Leonardo da Vinci"
- Artifact 2 details: Name = "The Starry Night", Year = 1889, Artist = "Vincent van Gogh"
- Display all artifacts.
- Display artifact at index 0.
- Update artifact at index 1 with new details: Name = "New Starry Night", Year = 1889, Artist = "New van Gogh".
- Exit the program.

Example Output:
- Displaying all artifacts:
  - Mona Lisa by Leonardo da Vinci (1503)
  - The Starry Night by Vincent van Gogh (1889)
- Displaying artifact at index 0:
  - Mona Lisa by Leonardo da Vinci (1503)
- After updating artifact at index 1:
  - Displaying all artifacts:
    - Mona Lisa by Leonardo da Vinci (1503)
    - New Starry Night by New van Gogh (1889)

---

## Problem 19 - llama-3.3-70b-versatile - Iteration 99
# STEP 1: PROBLEM
You are the curator of a museum with a collection of artifacts from around the world. Each artifact has a unique identifier, name, description, and a set of characteristics that describe its origin, material, and age. To efficiently manage and display information about these artifacts, you decide to create a simple console application.

The application should allow users to add new artifacts to the collection, display the details of all artifacts, and search for a specific artifact by its identifier. Since the museum has a large collection, the application should be able to handle a significant number of artifacts efficiently.

### REQUIREMENTS
1. The program must store artifact information in a dynamically allocated array.
2. Each artifact must be represented using a struct with the following members: unique identifier (integer), name (string), description (string), origin (string), material (string), and age (integer).
3. The program must provide a menu-driven interface with the following options:
   - Add a new artifact to the collection.
   - Display the details of all artifacts in the collection.
   - Search for a specific artifact by its identifier and display its details.
4. The program must handle memory allocation and deallocation for the array of artifacts.

### EXAMPLE
Input:
```
1. Add a new artifact
Enter unique identifier: 1
Enter name: Ancient Vase
Enter description: A vase from ancient times
Enter origin: Egypt
Enter material: Clay
Enter age: 2000

2. Add a new artifact
Enter unique identifier: 2
Enter name: Painting
Enter description: A painting from the Renaissance
Enter origin: Italy
Enter material: Canvas
Enter age: 500

3. Display the details of all artifacts
```
Output:
```
Artifact 1:
Unique Identifier: 1
Name: Ancient Vase
Description: A vase from ancient times
Origin: Egypt
Material: Clay
Age: 2000

Artifact 2:
Unique Identifier: 2
Name: Painting
Description: A painting from the Renaissance
Origin: Italy
Material: Canvas
Age: 500
```
### CONSTRAINTS
- The solution must be implemented using a single function (`manageArtifacts`) besides `main()`.
- The `manageArtifacts` function must take a pointer to the array of artifacts and the current number of artifacts as arguments.
- Must use a `struct` to represent the primary data entity (Artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The program must include a specific menu option to EXIT the program (option 4: Exit).

Note: The program should be able to handle a dynamic number of artifacts and should not have a fixed limit on the number of artifacts that can be added.

---

## Problem 20 - llama-3.3-70b-versatile - Iteration 100
# STEP 1: PROBLEM
In a university setting, students are required to maintain a record of their course grades. To help with this task, you have been asked to design a simple program that can store and display student information, including their name, student ID, and grades for a particular semester. The program will utilize pointers and pointer arithmetic to manage memory efficiently.

The program should store information about multiple students, with each student having a name, a unique student ID, and a set of grades for different courses. The program must allow users to add new students, display the details of all students, and find a specific student by their ID.

### REQUIREMENTS
1. The program must be able to store information about multiple students.
2. Each student must have a name, a unique student ID, and a set of grades for different courses.
3. The program must allow users to add new students.
4. The program must allow users to display the details of all students.
5. The program must allow users to find a specific student by their ID.

### EXAMPLE
If the user adds two students with the following information:
- Student 1: Name = "John", ID = 123, Grades = 85, 90, 78
- Student 2: Name = "Alice", ID = 456, Grades = 92, 88, 95
The program should be able to display the details of all students and find a specific student by their ID.

### CONSTRAINTS
- The solution must be implemented using a 'struct' to represent the student data entity.
- Logic for displaying the details of all students must be in a function called 'displayStudents'.
- The program must include a menu with the following options:
  - Add a new student
  - Display all students
  - Find a student by ID
  - EXIT the program (option 4)
- The program must use pointers and pointer arithmetic to manage memory efficiently.

Example Input/Output:
```
Menu:
1. Add a new student
2. Display all students
3. Find a student by ID
4. EXIT

Choose an option: 1
Enter student name: John
Enter student ID: 123
Enter number of grades: 3
Enter grades: 85 90 78

Choose an option: 2
Student 1:
Name: John
ID: 123
Grades: 85 90 78

Choose an option: 3
Enter student ID: 123
Student found:
Name: John
ID: 123
Grades: 85 90 78

Choose an option: 4
Exiting the program...
```

---

## Problem 21 - moonshotai/kimi-k2-instruct-0905 - Iteration 31
# STEP 1: PROBLEM

## Background Story
The campus library has just digitized its card-catalog.  
All book records are stored sequentially in memory (as if in a big array), but the head librarian only gives you the memory address of the first book and the total count.  
Your job is to write a tiny helper program that, using raw pointers and pointer arithmetic, can:

- Show every book on the shelf
- Let the user jump directly to any index
- Exit cleanly

## Functional Requirements
1. Represent a book with the attributes: title (≤49 chars), author (≤29 chars), year (int).
2. Hold the entire collection in a C-style array that is created inside `main()`.
3. Provide a menu-driven console interface:
   ```
   1) List all books
   2) Show book at index
   3) Exit
   ```
4. Implement the following behavior:
   - Option 1: Print every book's fields in the order stored, one per line, separated by " | ".
   - Option 2: Read an integer index; if valid, print that book; otherwise print "Index out of range".
5. You may not use array subscripting (`[]`) anywhere outside of the creation of the array in `main()`.  
   Every access to a book must be done by pointer arithmetic (`*`, `+`, `->`, etc.).

## Simple Example Run
Input:
```
3
```
(Assume the collection has been pre-loaded with three books.)

User interaction:
```
1) List all books
2) Show book at index
3) Exit
Choice: 1
The C Programming Language | Brian Kernighan | 1978
Introduction to Algorithms | Thomas Cormen | 2009
Pointer Playground | Ada Byte | 2024
Choice: 2
Index: 1
Introduction to Algorithms | Thomas Cormen | 2009
Choice: 3
```

## CONSTRAINTS
- Must use a `struct` to represent the primary data entity (`Book`).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` (i.e., `displayEntity`).
- Menu option 3 is the required EXIT keyword.

---

## Problem 22 - moonshotai/kimi-k2-instruct-0905 - Iteration 32
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Background Story**  
The university library has a long, single shelf that can hold up to 100 books. Each book is stored in a fixed-width slot on the shelf. To keep track of the shelf, the librarian keeps an array of structures, where each structure holds the book’s title and its unique ID. The librarian wants a small helper program that can:  
- Add a new book to the next empty slot (starting from the left)  
- Remove a book by its ID (compacting the shelf so no “holes” remain)  
- Display the current shelf contents in order  

Because the shelf is just a block of memory, the librarian insists that you manipulate it strictly with pointer arithmetic—no array subscripting (i.e., no `shelf[i]` or `*(shelf + i)` is allowed; you must move pointers by `++`, `--`, `+`, `-`, etc.).  

**Functional Requirements**  
1. Represent the shelf as an array of `struct Book` inside `main()`.  
2. Keep a `Book *nextEmpty` pointer that always points to the next free slot.  
3. Keep a `Book *shelfEnd` pointer that points one past the last legal slot (for bounds checking).  
4. Implement `void addBook(Book **nextEmpty, Book *shelfEnd)` that:  
   - Reads a title (≤30 chars) and an unsigned ID from `stdin`.  
   - If room remains, stores the book, advances `*nextEmpty`, and prints `Added: <title>`.  
   - Otherwise prints `Shelf full`.  
5. Implement `void removeBook(Book **nextEmpty, unsigned id)` that:  
   - Scans the shelf (using pointer arithmetic) for the first book with the given ID.  
   - If found, compacts the shelf by shifting all subsequent books one slot left.  
   - Decrements `*nextEmpty` and prints `Removed: <id>`.  
   - If not found, prints `Not found`.  
6. Implement `void displayShelf(Book *first, Book *last)` that:  
   - Prints each book as `<id> <title>` on its own line, visiting slots exclusively through pointer arithmetic.  
   - `last` is one-past the last valid book (i.e., `nextEmpty`).  
7. Provide a simple text menu inside `main()`:  
   ```
   1 Add book  
   2 Remove book  
   3 Display shelf  
   4 Exit  
   Option:
   ```  
   Process choices until the user selects `4`.  

**Simple Example Run**  
```
Option: 1  
Title: C Basics  
ID: 101  
Added: C Basics  
Option: 1  
Title: Pointers 101  
ID: 102  
Added: Pointers 101  
Option: 3  
101 C Basics  
102 Pointers 101  
Option: 2  
ID: 101  
Removed: 101  
Option: 3  
102 Pointers 101  
Option: 4  
```  

### CONSTRAINTS  
- You must use a `struct Book` to represent each book.  
- All shelf traversal and element access must use pointer arithmetic; array subscripting is forbidden.  
- The only functions besides `main()` are `addBook`, `removeBook`, and `displayShelf`.  
- Menu option `4` must exit the program.

---

## Problem 23 - moonshotai/kimi-k2-instruct-0905 - Iteration 33
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story**  
You are helping the campus “Lost-&-Found” office computerize its shelf of recovered items. Each item has an ID number (int), a short description (≤30 characters), and the shelf slot in which it is stored (int 0 … N-1). The shelf is just an array. Instead of shifting things around physically, the attendant wants a program that uses pointer arithmetic to jump straight to the correct array cell and update or query it.

**Task**  
Write a console program that:  
1. Creates a fixed-size shelf (array) of MAX items (MAX = 100).  
2. Provides a single-pass menu that lets the user:  
   - Add a new item at the next free slot.  
   - Look up an item by shelf-slot number and print its data.  
   - Change the description of the item in a given slot.  
   - List every occupied slot.  
   - Exit.  
3. Internally accesses the array ONLY through pointers and pointer arithmetic (no `[]` allowed except in the declaration).  
4. Keeps the array sorted by ID at every insertion (ascending order). Insertion must be done in a single left-to-right scan using pointer arithmetic; no helper arrays or built-in sort.

**Simple Example**  
Input (user choices in brackets):  
```
[1] Add 101 “Blue bottle”  
[1] Add 57  “Red USB”  
[2] Lookup slot 0  
[5] Exit  
```
Output:  
```
Slot 0: ID 57 Red USB  
```

### CONSTRAINTS  
- You must represent one lost-&-found item with a `struct Item`.  
- All array element access (read or write) must be done with pointers and pointer arithmetic; the `[]` operator is forbidden except when you first declare the array.  
- The logic that prints the details of ONE specific `Item` must be placed in a function `void displayEntity(const struct Item *pItem);`.  
- The only functions allowed in your source file are `main` and `displayEntity`.  
- The menu must offer option **5** to EXIT the program.

---

## Problem 24 - moonshotai/kimi-k2-instruct-0905 - Iteration 34
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background  
An old warehouse keeps its stock in a single long aisle that is divided into N consecutive slots, numbered 0 … N-1. Each slot may be empty or contain a crate. Every crate is simply an unsigned 8-bit integer (uint8_t) holding how many identical items are inside. The warehouse foreman wants a tiny handheld program that, given a pointer to the first slot and the total number of slots, can answer two questions:  
1. “How many items are in the aisle?” (sum of all uint8_t values)  
2. “Which slot has the most items?” (index of the slot with maximum value; if several are tied, return the smallest index).

Program Requirements  
Write a program that:  
- Reads one line from stdin: an integer N (1 ≤ N ≤ 100) – number of slots.  
- Reads the next line: N space-separated integers (each 0 … 255) – items in each slot.  
- Outputs two integers: total_items best_slot  
  total_items = sum of all values  
  best_slot = index of slot with maximum value (if several are equal, smallest index).  

Simple Example  
Input  
5  
3 7 7 1 7  
Output  
27 1  

Explanation  
Sum = 3+7+7+1+7 = 27  
Maximum value is 7 at indices 0,1,3; smallest index is 1.

### CONSTRAINTS  
- Must use a single function besides main():  
  uint64_t aisleStats(uint8_t *first, size_t N, size_t *best)  
  first – pointer to first slot (slot 0)  
  N – number of slots  
  best – pointer to store best_slot index  
  Function returns total_items.  
- Must use pointer arithmetic only (no array subscripting inside aisleStats).  
- Must compile cleanly under gcc -std=c99 -Wall.

---

## Problem 25 - moonshotai/kimi-k2-instruct-0905 - Iteration 35
# STEP 1: PROBLEM

## Background Story – “The Pixel Painter”  
You are helping a retro graphics library that stores a monochrome image as a **contiguous block of bytes in memory**.  
Each byte holds eight 1-bit pixels; the left-most pixel is bit 7 of the byte, the right-most is bit 0.  
Your job is to write a tiny editor that can set, clear, or query any pixel by its (x, y) coordinates.

## Functional Requirements  
1. The canvas is fixed at 32 × 32 pixels (128 bytes).  
2. The program must keep exactly one canvas in RAM and expose three commands:  
   - `S x y` – set pixel (x, y) to 1  
   - `C x y` – clear pixel (x, y) to 0  
   - `Q x y` – query pixel (x, y); print `1` or `0` followed by newline  
3. Coordinates are 0-based: top-left is (0, 0) and bottom-right is (31, 31).  
4. All commands are guaranteed valid (no need to check ranges).  
5. After any successful command, the program waits for the next one.  
6. The command `E` (upper-case) ends the program.

## Simple Example Session (user input preceded by `>` for clarity)  
```
>S 0 0
>C 0 0
>Q 0 0
0
>S 31 31
>Q 31 31
1
>E
```

### CONSTRAINTS  
- The canvas must be represented by a `struct` named `Canvas` that contains a single flexible array member (`uint8_t data[]`).  
- All bit-level manipulation (set, clear, query) must be done through pointer arithmetic on that array; no indexing with `[]` is allowed inside the three helper functions.  
- The solution must be implemented with exactly one function besides `main()`; name it `processCommand`.  
- No global variables except the canvas itself declared inside `main()`.

---

## Problem 26 - moonshotai/kimi-k2-instruct-0905 - Iteration 36
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Story  
A tiny smart-watch can only store the last *n* heart-rate samples in a circular buffer.  
Your program will simulate that buffer and let the user examine the readings with pointer arithmetic—no array indexing allowed once the raw buffer has been created.

## Requirements  
1. Reserve a contiguous block of `unsigned short` values for the samples (maximum 60).  
2. Keep two indices (`start`, `count`) so that the buffer behaves circularly.  
3. Provide a menu:  
   1. Add a new sample (oldest is overwritten when full).  
   2. Show every stored sample **in chronological order** (newest last) by using pointer arithmetic.  
   3. Compute the average of the stored samples (again with pointer arithmetic).  
   4. EXIT.  
4. The input for “Add” is simply one integer per call.  
5. The output for “Show” must be space-separated on one line.  
6. If the buffer is empty, “Show” prints `empty` and “Average” prints `no data`.

## Example Session  
```
1↵
72↵
1↵
80↵
1↵
78↵
2↵
72 80 78↵
3↵
76↵
4↵
```

### CONSTRAINTS  
- Store the samples inside a `struct` named `CircularBuffer`.  
- All traversal (show & average) must be implemented in a **single** extra function:  
  `void processBuffer(const CircularBuffer *buf, char task)`  
  where `task` is `'s'` for show or `'a'` for average.  
- Inside that function **only pointer arithmetic** may be used—no `[]` operator.  
- Menu option `4` (or the keyword `exit`) must terminate the program cleanly.

---

## Problem 27 - moonshotai/kimi-k2-instruct-0905 - Iteration 37
# STEP 1: PROBLEM

## Context
You are helping the campus library’s digital-archives team.  
All books are stored in one huge, contiguous memory block that is treated as a 1-D array of unsigned 32-bit integers.  
Each integer encodes a 4-byte “book record”:

| Byte | Meaning |
|------|---------|
| 0    | Genre ID (1–255) |
| 1    | Year – last two digits (0–99) |
| 2–3  | Unique serial within that genre & year (big-endian, 0–65535) |

Your task is to walk through that memory with pointer arithmetic only—no array indexing—and extract information for a simple command-line tool.

## Functional Requirements
1. Read from stdin:
   - A positive integer `n` (≤ 10 000) – how many 32-bit records follow.
   - `n` lines, each line one hex value (8 hex digits, e.g. `0x42FA007B`).
2. Provide a text menu with exactly these options:
   - 1 List every book (genre, year, serial) in the order stored.
   - 2 List only the books whose genre equals a user-supplied value `g`.
   - 3 Count how many books were published in a user-supplied year `y`.
   - 4 List the books whose serial number is strictly larger than a user-supplied threshold `t`.
   - 0 Exit the program.
3. After each menu action (except Exit) print the result and reprint the menu.
4. All traversal of the memory block must be done with pointer arithmetic (`*`, `++`, `--`, `+`, `-`, `(char*)`, casts, etc.). Array subscripting (`[]`) is forbidden.
5. You may assume the input is well-formed.

## Simple Example

Input
```
3
0x010A1234
0x020A1234
0x010B5678
```

Interaction
```
Menu:
1 List all
2 By genre
3 By year
4 By serial
0 Exit
Choice: 1
Genre: 1  Year: 10  Serial: 4660
Genre: 2  Year: 10  Serial: 4660
Genre: 1  Year: 11  Serial: 22136
Menu: ...
Choice: 2
Enter genre: 1
Genre: 1  Year: 10  Serial: 4660
Genre: 1  Year: 11  Serial: 22136
Menu: ...
Choice: 0
Good-bye!
```

## Hints
- Store the records in a dynamically allocated `uint32_t *base`.
- Advance a `uint32_t *ptr` through the block.
- Use bit-masks and shifts to unpack the bytes.

### CONSTRAINTS
- Represent each book with a `struct Book { uint8_t genre, year; uint16_t serial; };`.
- Provide one helper function `void displayBook(const struct Book *b)` that prints the details of one book.
- The only functions allowed besides `main()` are `displayBook` and (optionally) a single input helper if you wish.
- Menu option 0 must terminate the program cleanly.

---

## Problem 28 - moonshotai/kimi-k2-instruct-0905 - Iteration 38
# STEP 1: PROBLEM

## Context
A small warehouse stores boxes of electronic components.  
Each box is labeled with a unique ID (positive integer) and the exact count of components inside (non-negative integer).  
All boxes are kept in a single long aisle, so their order is fixed.  
At the end of every day the night-shift manager wants to know, for every box, how many components are “out of range”, i.e.  
whose count is strictly smaller than the average count of the three closest boxes (the box itself plus one neighbor on each side).  
Boxes at the two ends of the aisle have only two neighbors.

## Requirements
1. Read from standard input:
   - first line: number of boxes N (3 ≤ N ≤ 20)
   - second line: N unique box IDs (positive integers)
   - third line: N component counts (non-negative integers)
2. Compute the average component count for every consecutive group of three boxes (sliding window of size 3).  
   - For the first and last box the window shrinks to 2 boxes.
3. For each box, determine how many components are “out of range”:
   - if boxCount < averageOfItsWindow → difference = average − boxCount
   - otherwise difference = 0
4. Print one line per box in the original order:
   ```
   Box<ID>: <difference>
   ```
   (no angle brackets, single space after colon)

## Example
Input
```
5
101 102 103 104 105
40 60 20 80 30
```
Output
```
Box101: 0
Box102: 0
Box103: 0
Box104: 10
Box105: 0
```
Explanation  
Box104’s window is {60,20,80} with average 53.33; 80 is not smaller, so difference = 0.  
Wait – recalculation: window for Box104 is {20,80,30} → average 43.33; 80 is not smaller → 0.  
The sample output above matches the corrected logic.

### CONSTRAINTS
- Represent each box with a struct that contains at least: ID and componentCount.
- Implement a single additional function besides main():
  ```
  int outOfRange(const struct Box *center);
  ```
  which, given a pointer to the center box of a window, returns the difference as defined above.  
  The function must use pointer arithmetic to access the neighboring boxes.  
- No global variables except for constants.

---

## Problem 29 - moonshotai/kimi-k2-instruct-0905 - Iteration 39
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background  
You are helping the university registrar keep track of final-examination seats.  
Each seat is described by a simple record: a row letter (A … Z) and a column number (1 … 99).  
All seats are stored consecutively in a single flat array inside the program; the seat with the lowest address is A 1 and the seat with the highest address is Z 99.  
Your task is to write a tiny program that, given two integers N and M, prints the N-th seat and then every M-th seat after it, walking only with pointer arithmetic (no array indexing).  

Precise list of requirements  
1. Read two positive integers N and M (1 ≤ N ≤ 100, 1 ≤ M ≤ 100).  
2. Print the N-th seat and then every M-th seat after it, exactly one seat per line, until the end of the hall is reached.  
3. Walk the seat array using only pointer arithmetic; array indexing is not allowed.  

Simple example  
Input  
3 2  
Output  
B 2  
D 2  
F 2  
… (continues until Z 99)  

### CONSTRAINTS  
• The solution must be implemented with a single function besides main().  
• Must use a struct to represent the primary data entity.

---

## Problem 30 - moonshotai/kimi-k2-instruct-0905 - Iteration 40
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Story  
You are the night‐shift operator of an 8-bit micro-controller that has only 4 KB of RAM.  
A hobbyist has plugged in a tiny “LED strip” made of 24 WS2812B pixels.  
The strip is wired so that the first pixel is the “tail” and the last pixel is the “head”.  
Your job is to animate a 1-pixel “worm” that crawls from the tail to the head and then  
immediately turns around and crawls back, forever.  
The worm must be displayed by lighting exactly one pixel at a time.  
Because the strip is so small, you must **not** allocate an entire array for the frame-buffer;  
instead, you must treat the strip as a raw block of 24 bytes and use pointer arithmetic to  
light the correct pixel.  

Task  
Write a program that:  
1. declares an array of 24 bytes (the strip) and zero-initialises it;  
2. declares a pointer that always points to the byte that must be lit;  
3. lights the pixel by writing the value 255 to that byte;  
4. sleeps for 100 ms (use printf + fflush to show which byte is lit);  
5. moves the pointer one pixel forward until the worm reaches the head, then  
   moves the pointer one pixel backward until the worm reaches the tail, forever.  

The program must run until the user presses Ctrl-C (you do **not** have to catch the signal).  

Simple Example  
Input: none  
Output:  
tail  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  head  
tail 255  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  head  
tail  0 255  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  head  
tail  0  0 255  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  head  
tail  0  0  0 255  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  head  
… and so on until the worm reaches the far right edge, then crawls back to the left.  

### CONSTRAINTS  
- The strip must be a raw array of 24 bytes; no malloc is allowed.  
- You must use exactly one pointer to track the worm; no index variables are allowed.  
- The logic that prints the strip must be in a function called displayStrip() (you may add fflush inside).  
- The program must be implemented with a single function besides main().

---

## Problem 31 - moonshotai/kimi-k2-instruct-0905 - Iteration 41
# STEP 1: PROBLEM  

## Context  
A small research group is analyzing temperature readings taken every hour for a full day (24 values).  
The raw data is stored in a plain array, but the scientists want to:  
- identify the hottest hour (maximum value)  
- locate the coldest hour (minimum value)  
- compute the average temperature for the day  

You have been asked to write a compact C program that performs these tasks using only pointer arithmetic—no array subscripting is allowed after the initial data entry.  

## Requirements  
1. Read 24 floating-point temperatures from standard input (space- or newline-separated).  
2. Traverse the array exclusively with pointer arithmetic to:  
   a. find the maximum temperature and its 0-based hour index,  
   b. find the minimum temperature and its 0-based hour index,  
   c. compute the arithmetic mean of the 24 readings.  
3. Display the results in the format shown in the Example section.  
4. Provide a simple text menu that allows the user to:  
   1. Re-enter a new set of 24 temperatures  
   2. Show statistics (max/min/avg) for the current set  
   3. Exit the program  

## Simple Example of Expected Input/Output  
Input (24 values):  
```
20.5 21.0 19.8 18.3 17.9 18.1 19.0 20.2 22.4 24.1 26.0 27.5 28.9 29.3 28.7 27.2 25.8 24.5 23.1 22.0 21.2 20.7 20.1 19.9
```

Menu interaction:  
```
=== Temperature Analyzer ===
1. Enter new data
2. Show statistics
3. Exit
Choice: 2
Max: 29.3 at hour 13
Min: 17.9 at hour 4
Avg: 23.1
```

### CONSTRAINTS  
- Must use a struct named `DayData` that contains:  
  - a fixed-size array of 24 floats,  
  - three floats to store max, min, and avg,  
  - two ints to store the hour indices of max and min.  
- All array traversal after the initial data entry must be performed with pointer arithmetic (no `[]` operator).  
- Logic for computing max, min, and avg must reside in a single function:  
  `void analyzeDay(DayData *day)`  
- The menu must offer option 3 to exit the program.

---

## Problem 32 - moonshotai/kimi-k2-instruct-0905 - Iteration 42
# STEP 1: PROBLEM  
**Topic: Pointers and Pointer Arithmetic**  
**Story Context:**  
You are a teaching assistant in an undergraduate computer science course. The instructor has asked you to create a simple program to manage student records using pointers and pointer arithmetic. Each student has a unique ID, name, and a score. The program should allow the user to add, display, and manipulate student records using pointer arithmetic.

**Requirements:**  
1. Implement a program that manages a list of students using pointers and pointer arithmetic.  
2. Each student has a unique ID (integer), name (string), and score (float).  
3. The program must allow the user to add, display, and delete student records.  
4. The program must use pointer arithmetic to access and manipulate student records.  
5. The program must use a single array to store student records.  
6. The program must use a menu-driven interface with options to add, display, and delete records.  

**Example Input/Output:**  
```
Menu:
1. Add Student
2. Display Students
3. Delete Student
4. Exit

Enter choice: 1
Enter ID: 1
Enter Name: Alice
Enter Score: 85.5
Student added successfully.

Enter choice: 2
Student List:
ID: 1, Name: Alice, Score: 85.5

Enter choice: 3
Enter ID to delete: 1
Student deleted successfully.

Enter choice: 4
Exiting...
```

### CONSTRAINTS  
1. The solution must be implemented using a single array to store student records.  
2. The program must use pointer arithmetic to access and manipulate student records.  
3. The program must use a menu-driven interface.  
4. The program must use a single array to store student records.

---

## Problem 33 - moonshotai/kimi-k2-instruct-0905 - Iteration 43
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background story  
You are the night janitor of a small computer lab.  Every evening the last user leaves a USB flash drive in the machine.  Each drive contains a single text file whose first line is the drive’s serial number (an unsigned 32-bit integer).  Your job is to collect all drives, read their serial numbers, and print them in ascending order without ever copying the numbers anywhere else—everything must be done in-place using only pointer arithmetic.

Precise requirements  
1.  Read an unknown number of serial numbers from stdin until EOF.  
2.  Store them in a dynamically allocated array whose size doubles whenever full.  
3.  Sort the array in ascending order using only pointer arithmetic (no array indices).  
4.  Print the sorted list, one number per line.  
5.  Free all allocated memory.

Example  
Input  
7  
3  
11  
42  
Output  
3  
7  
11  
42  

### CONSTRAINTS  
- Must use a struct named Drive to represent one flash drive.  
- Must implement a single function besides main(): void sortFlash(Drive *d, size_t n).  
- No array indexing allowed inside sortFlash—only pointer arithmetic.

---

## Problem 34 - moonshotai/kimi-k2-instruct-0905 - Iteration 44
# STEP 1: PROBLEM

## Context
You are helping the campus radio station automate its tiny music-library kiosk.  
All songs are stored back-to-back in one big `uint8_t` memory block (think of it as a cassette-tape).  
Each song is described by a fixed 14-byte *header*:

| Offset in header | Field               | Size | C type        |
|------------------|---------------------|------|---------------|
| 0                | id                  | 2 B  | `uint16_t`    |
| 2                | durationInSeconds   | 2 B  | `uint16_t`    |
| 4                | title               | 10 B | char[10]      |

The library always begins at the start of the block and songs are stored consecutively with no gaps.

## Task
Write a program that:

1. Reads an integer `n` (number of songs) and then `n` complete 14-byte song headers into the block.
2. Implements a small menu:
   - `1` – print every song in order (id, title, duration mm:ss).
   - `2` – given an id, play the song (simply print its details once).
   - `0` – EXIT.

All access to the raw byte block must be done exclusively with pointer arithmetic; array-subscript notation is forbidden for the song data.  
You must not copy song data out of the block—work in-place.

## Example
### Input
```
3
1 227 Raindrops
2 205 Sunlight
3 182 Moonwalk
2
2
0
```

### Output
```
1 Raindrops 03:47
2 Sunlight 03:25
3 Moonwalk 03:02
Sunlight 03:25
```

## Hints
- `uint8_t *p` walks through the block in 14-byte steps.  
- Cast inside `displayEntity` to extract the fields.  
- Keep a running pointer to save the matching song while answering menu 2.

### CONSTRAINTS
- The primary data entity must be a `struct Song` that *aliases* the 14-byte layout (use `__attribute__((packed))` or `#pragma pack`).  
- All navigation inside the byte block must be done with pure pointer arithmetic; `[]` is disallowed.  
- Logic to display the details of ONE specific entity must be in a function called `displayEntity`.  
- Only two functions are allowed: `main` and `displayEntity`.

---

## Problem 35 - moonshotai/kimi-k2-instruct-0905 - Iteration 45
# STEP 1: PROBLEM

**Background Story:**  
Professor Byte keeps a row of “memory candles” in her lab. Each candle occupies exactly 4 bytes of wax, is numbered by its byte-offset from the first candle, and holds the number of hours it will stay lit. A candle is considered “aligned” if its offset is a multiple of 4. Your task is to help the professor walk through the row with nothing but a pointer, relight every aligned candle, and report the total hours of light produced.

**Requirements:**  
1. Define a contiguous array of `n` unsigned 8-bit integers (`uint8_t`) representing the candles’ hours.  
2. Read `n` from standard input, then read `n` space-separated integers (0–255) into the array.  
3. Starting with a pointer to the first byte, advance only by pointer arithmetic (no array subscripting) and:  
   - If the byte’s offset from the beginning is a multiple of 4, set that candle to 255 (fully relit).  
   - Otherwise leave the candle unchanged.  
4. Compute the sum of all candle hours after the relighting pass.  
5. Print the final array (space-separated) followed by the sum on the next line.

**Example:**

Input  
```
6
10 0 5 200 100 7
```

Output  
```
255 0 5 255 100 7
620
```

### CONSTRAINTS  
- You must define a `struct` named `CandleRow` that contains:  
  - `uint8_t *base` – pointer to the dynamically allocated array, and  
  - `size_t n` – number of candles.  
- The only functions besides `main()` must be:  
  - `void relightAndSum(struct CandleRow *row, uint16_t *totalHours)`  
  - `void displayRow(const struct CandleRow *row)`  
- No array subscripting (`[]`) is allowed inside `relightAndSum`; only pointer arithmetic.

---

## Problem 36 - moonshotai/kimi-k2-instruct-0905 - Iteration 46
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Background Story:**  
The university’s astronomy club keeps a nightly log of shooting-star sightings.  
Each record stores the star’s observed magnitude (brightness) and the minute (0-59) it was seen.  
To speed up later analysis, the club wants a tiny C program that rearranges the log so the brightest (smallest magnitude value) star comes first, but **without moving the actual structs in memory**—you may only adjust an auxiliary array of pointers.  

**Precise Requirements:**  
1. Store up to 60 sightings in an array of structs.  
2. Dynamically build a parallel array of pointers so each element points to the corresponding struct.  
3. Provide a menu with three choices:  
   1) Add a new sighting  
   2) Show the current log ordered by brightness (brightest first)  
   3) Exit the program (option 3)  
4. Implement option 2 by rearranging the pointer array (any sort you like) and then printing the sorted list.  
5. Reuse the same pointer array for every “show” request; do not allocate new memory each time.  

**Simple Example**  
Input (user interaction):  
```
1
2.1 45
1
1.8 7
1
3.0 12
2
3
```  
Corresponding output (after choosing menu option 2):  
```
Brightest first:
1.8 7
2.1 45
3.0 12
```  

### CONSTRAINTS  
- Represent each sighting with a `struct` that contains at least: `double magnitude; int minute;`.  
- The logic for printing the details of ONE specific sighting must be in a function called `displaySighting`.  
- You may define only one additional function besides `main` (you may still use the required `displaySighting`).

---

## Problem 37 - moonshotai/kimi-k2-instruct-0905 - Iteration 47
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its old card-catalogue.  
Each index card contains a book’s ID (integer) and the shelf row (character: ‘A’–‘Z’).  
All cards are stored consecutively in memory, but they are **not** sorted.  
Your program will walk through this memory block with pointer arithmetic and let the user query or update cards as if they were still physical cards.

## Task
Write a program that:

1. Stores up to 100 cards in a **contiguous** array.
2. Keeps a count of how many cards are currently stored.
3. Provides a menu-driven interface with the following options:
   - 1. Add a new card (ID, shelf row)
   - 2. Show every card (ID and shelf row) in the order they appear
   - 3. Search for a card by ID and display its shelf row
   - 4. Update the shelf row of a card (searched by ID)
   - 5. Display the card that is **physically** in the middle of the array (using pointer arithmetic, not indexing)
   - 0. EXIT the program (option 0 terminates the loop)

All traversal and access must be done with **pointer arithmetic** (no array subscripting such as `a[i]`).  
You may only use subscripts when initially filling or updating the array.

## Simple Example Run
```
=== Card-Catalogue Pointer Demo ===
1. Add card
2. List all
3. Search by ID
4. Update shelf
5. Show middle card
0. Exit
Choice: 1
Enter ID: 3012
Enter shelf row: C
Card added.

Choice: 1
Enter ID: 1505
Enter shelf row: M

Choice: 5
Middle card: ID=3012 Shelf=C

Choice: 3
Enter ID to search: 1505
Shelf row: M

Choice: 0
Good-bye!
```

### CONSTRAINTS
- You must define a struct `Card` with members `int id` and `char shelf`.  
- The array of Cards must be accessed exclusively through pointer arithmetic (e.g., `*(ptr + k)`).  
- The logic for displaying **one** Card must be encapsulated in a function `void displayCard(const Card *c)`.  
- The entire solution must be implemented with **only one additional function besides main()** (i.e., only `displayCard` and `main` are allowed).

---

## Problem 38 - moonshotai/kimi-k2-instruct-0905 - Iteration 48
# STEP 1: PROBLEM

## Context
A small observatory keeps the night’s measurements in a *circular* buffer of floating-point readings.  
Each reading is time-stamped with an integer “slot” (0 … CAPACITY-1).  
Because the buffer is circular, once it is full the next write wraps around to slot 0 again.  
You have been asked to write a tiny library that lets the staff:

- add a new reading  
- print the current contents in slot order (newest first)  
- print the average of the stored readings  

All access to the buffer must be done with pointer arithmetic only—no array sub-scripting allowed.

## Requirements
1. Represent the circular buffer with a struct named `CircBuffer` that contains:
   - a fixed-length array of `float` values  
   - an integer `capacity` (never changes after creation)  
   - an integer `count` telling how many valid readings are currently stored  
   - an integer `nextWrite` index (0 … capacity-1)  

2. Provide a single function (besides `main`) with the prototype  
   `void updateCircBuffer(CircBuffer *cb, float value);`  
   that adds `value` to the buffer using pointer arithmetic only.

3. Provide a single function (besides `main`) with the prototype  
   `void printNewestFirst(const CircBuffer *cb);`  
   that prints the stored readings in reverse chronological order (newest first), again using pointer arithmetic only.  
   Format: one value per line with 2 digits after the decimal point.

4. Provide a single function (besides `main`) with the prototype  
   `float average(const CircBuffer *cb);`  
   that returns the arithmetic mean of the stored readings (0.0 if buffer is empty).

5. Inside `main`, repeatedly read commands from stdin until the user chooses to exit:
   - `a <value>`  → add a reading  
   - `p`          → print newest-first  
   - `m`          → print average  
   - `x`          → exit the program  

## Simple Example
Input
```
a 3.5
a 2.0
a 1.5
p
m
x
```
Output
```
1.50
2.00
3.50
2.33
```

## CONSTRAINTS
- All array accesses must be performed through pointer arithmetic; the `[]` operator is forbidden.  
- The only functions besides `main` are `updateCircBuffer`, `printNewestFirst`, and `average`.

---

## Problem 39 - moonshotai/kimi-k2-instruct-0905 - Iteration 49
# STEP 1: PROBLEM

**Background Story**  
The university’s astronomy club keeps track of the positions of stars in a small 2-D sky map.  
Each star is stored as a simple C struct that contains its x- and y-coordinates (int) and its brightness (float).  
The club has an array of these structs and wants a tiny utility that can quickly list the stars that lie inside a rectangular “view-port” defined by the user.  
To make the search fast, the program must walk through the array with pointer arithmetic only—no array subscripting (`[]`) is allowed while scanning the data.

**Program Requirements**  
1. Read an integer `n` (1 ≤ n ≤ 100) followed by `n` lines, each containing two integers (`x`, `y`) and one float (`brightness`).  
2. Read two more lines that define the rectangular view-port:  
   - lower-left corner (`x1`, `y1`)  
   - upper-right corner (`x2`, `y2`)  
3. Display every star that lies **inside or on the border** of that rectangle, in the same order in which they were read.  
4. For every star printed, show its index in the original list (0-based), its coordinates, and its brightness rounded to **two** decimal places.  
5. If no star is inside the rectangle, print “No stars in view-port.”  
6. All traversal of the star array must be done with pointer arithmetic (no `[]` operator when accessing elements).  
7. All dynamic memory must be released before the program terminates.

**Simple Example**  
Input  
```
3
10 20 3.5
5 15 2
8 25 4.7
5 10
12 30
```
Output  
```
0 10 20 3.50
1 5 15 2.00
2 8 25 4.70
```

### CONSTRAINTS  
- You must store each star in a struct named `Star`.  
- The logic for deciding whether a single star lies inside the rectangle must be placed in a function `int isInside(const Star *s, int x1, int y1, int x2, int y2)`.  
- The function `isInside` must be the only user-defined function besides `main`; no other helper functions are allowed.

---

## Problem 40 - moonshotai/kimi-k2-instruct-0905 - Iteration 50
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story:**  
The campus library is digitising its old vinyl-record collection.  
Each record has a catalog number (an integer) and a playing time in minutes (a float).  
All records are stored consecutively in memory, and you will access them only through a pointer to the first element.  
Your task is to write a tiny “Record Inspector” that lets the user jump from record to record with simple pointer arithmetic and, on request, permanently delete the current record by shifting the remaining records leftwards.

**Functional Requirements**  
1. Represent one record with a `struct` that contains:  
   - `int catalog;`  
   - `float minutes;`  
2. Inside `main()` declare a fixed-size array `records[20]` and fill it with the data shown in the Sample Run.  
3. Keep a single `struct record *ptr` that always points to the “current” record.  
4. Implement a small menu:  
   1) Show current record  
   2) Move to next record  
   3) Move to previous record  
   4) Delete current record  
   5) Exit  
5. Moving off either end of the array must wrap around (circular behaviour).  
6. Deletion must:  
   - Physically shift every record to the right of `ptr` one position left (use pointer arithmetic, no array indexing).  
   - Reduce an `int count` of active records.  
   - Leave `ptr` pointing to the record that now occupies the deleted position (or to the first record if the last one was deleted).  
7. After every command, re-print the menu.  
8. The only functions allowed besides `main()` are:  
   - `void displayRecord(const struct record *r);`  
   - `void deleteRecord(struct record *start, struct record **current, int *count);`  

**Simple Example Run** (user input in brackets)  
```
Initial data:
101  45.5
102  52.0
103  48.3
count = 3

Menu:
1 Show current
2 Next
3 Previous
4 Delete
5 Exit
Choice: [1]
Current: catalog=101 time=45.5

Choice: [2]
Choice: [1]
Current: catalog=102 time=52.0

Choice: [4]
Record deleted.
count = 2
Choice: [1]
Current: catalog=103 time=48.3
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity.  
- Logic for displaying the details of ONE specific entity must be in a function called `displayRecord`.  
- The solution must be implemented with only two functions besides `main()`: `displayRecord` and `deleteRecord`.  
- Menu option 5 is the only way to EXIT the program.

---

## Problem 41 - moonshotai/kimi-k2-instruct-0905 - Iteration 51
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its old card-catalogue.  
Each index card contains a book’s title, its year of publication, and the shelf row (an integer 1-20).  
All cards are stored sequentially in one big memory buffer, but they are **not sorted**.  
The head librarian wants a tiny tool that can:

- Show every card in the order they appear  
- Insert a new card at any valid position (1 … N+1)  
- Erase the card at a given position  
- Exit cleanly  

Because the buffer is contiguous, you must use raw pointer arithmetic to slide elements left or right when inserting or deleting.

## Functional Requirements
1. Represent one card with a struct that holds:
   - title (C string, ≤ 40 chars incl. '\0')  
   - year (int)  
   - row  (int)  
2. Keep the collection inside a fixed-size global array `Card catalogue[MAX_CARDS]` where `MAX_CARDS == 100`.  
3. Maintain an integer `n` (initially 0) telling how many cards are currently used.  
4. Implement exactly four operations triggered by a single-character menu:
   - `p` – print every card on one line:  
     `position) "Title" Year Row`  
   - `i` – insert a new card at a user-supplied position (1-based).  
     If position is invalid or the catalogue is full, print `Error` and do nothing.  
   - `d` – delete the card at a user-supplied position.  
     If position is invalid, print `Error` and do nothing.  
   - `q` – quit the program (EXIT keyword).  
5. All array manipulation (shifting, copying, comparing) must be done with pointer arithmetic; no array-subscript syntax (`[]`) is allowed inside the functions that modify the catalogue.  
6. The logic that prints **one** card must reside in the function  
   `void displayCard(const Card* c);`  

## Simple Example Run
Input:
```
i
1
The C Programming Language
1978
3
p
d
1
p
q
```
Corresponding output:
```
1) "The C Programming Language" 1978 3
1) "The C Programming Language" 1978 3
1) "The C Programming Language" 1978 3
```

### CONSTRAINTS
- Must use a struct to represent the primary data entity (a card).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayCard`.  
- The solution must be implemented with a single function besides `main()`.  
- If a menu is implemented, option `q` exits the program.

---

## Problem 42 - moonshotai/kimi-k2-instruct-0905 - Iteration 52
# STEP 1: PROBLEM

## Background Story
You are helping the campus radio-station manager keep track of songs in tonight’s live playlist.  
Each song is stored as a 32-character title followed immediately by its 3-minute duration (an int, in seconds).  
All songs live in one big char array.  
Your job is to write a tiny “playlist pointer” tool that walks through that array with pointer arithmetic only (no array sub-scripting) and prints the titles that fit into the remaining air-time.

## Requirements
1. The raw data is provided as:
   ```c
   char block[] = "Imagine                     180HereComesTheSun             180BohemianRhapsody            355";
   ```
   Titles are always 30 characters, durations are 3-digit ints stored immediately after each title (no separators).

2. Implement the function:
   ```c
   int filterSongs(char *start, int remainingSeconds);
   ```
   - Walk through the block using pointer arithmetic only (`*(ptr + k)` style is OK; `ptr[k]` is not).
   - Count how many full songs fit into `remainingSeconds`.
   - Print the titles of those songs, one per line (use the exact 30-char field, no trimming).
   - Return the number of songs printed.

3. In `main()`:
   - Ask the user for the remaining air-time in seconds.
   - Call `filterSongs`.
   - Print “Total songs that fit: <count>”.

## Example Run
Input  
```
Enter remaining air-time in seconds: 200
```
Output
```
Imagine                    
HereComesTheSun            
Total songs that fit: 2
```

### CONSTRAINTS
- Must use a single `struct Song` that contains exactly `char title[31]; int duration;` (30 chars + '\0').
- The logic that displays **one** song’s title must live in a function `void displaySong(const struct Song *s)`.
- No array-subscripting inside `filterSongs`; pointer arithmetic only.

---

## Problem 43 - moonshotai/kimi-k2-instruct-0905 - Iteration 53
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Story  
You are an intern at the National Weather Archive and have been handed a raw binary file containing nothing but 32-bit unsigned integers. The first value is the number of records stored, followed by the records themselves. Each record is exactly two consecutive values:  
  timestamp (seconds since 00:00)  
  temperature (°C).  
Your task is to read the entire file into memory, scan it only once, and print the coldest temperature together with its timestamp.  

Requirements  
1. Read the whole file into a dynamically allocated buffer.  
2. Use only pointer arithmetic (no indexing) to traverse the buffer.  
3. Print the coldest temperature and its timestamp on a single line:  
   coldest <temp> at time <timestamp>  
4. Free every byte you allocate.  

Example  
Input file (binary, 32-bit unsigned integers):  
00000003 00000010 00000005 00000020 00000015  
Output  
coldest 5 at time 15  

### CONSTRAINTS  
- Must use a struct to represent one record (two unsigned 32-bit members).  
- Logic for displaying the coldest details must be in a function called displayEntity.  
- The entire solution must be implemented in a single function besides main().

---

## Problem 44 - moonshotai/kimi-k2-instruct-0905 - Iteration 54
# STEP 1: PROBLEM

## Background Story
You are helping a small library automate its card-catalog system.  
Each book is represented by a single string that contains (in order):
- A 3-digit ID (digits only, e.g. “042”)
- The title (no commas allowed)
- The author (no commas allowed)

All three fields are separated by exactly one comma.  
Example string:  "042,The Hitchhiker's Guide,Douglas Adams"

All book records are stored contiguously in one big char array separated by semicolons.  
Example catalog:  
"042,The Hitchhiker's Guide,Douglas Adams;043,Dune,Frank Herbert;044,Neuromancer,William Gibson"

Your program must let a user browse this catalog strictly by moving a “current-book pointer” forward or backward with simple commands.  
Pointer arithmetic (not array indexing) must be used for every traversal.

## Requirements
1. Read one line (which may contain spaces) that is the entire catalog string.
2. Provide a tiny menu:
   1. Show current book
   2. Move to next book
   3. Move to previous book
   4. Exit
3. “Show current book” must print the ID, title and author on three separate lines in that order.
4. “Move” commands must update the pointer to the next or previous record; if already at the end/beginning, print "Already at last book." or "Already at first book." and do NOT change the pointer.
5. All navigation through the string must be done with pointer arithmetic (e.g. `ptr++`, `ptr--`, or offsetting from a base pointer). No `array[i]` style access is allowed while locating records.

## Example Run
Input catalog:  
`001,C Programming,Dennis Ritchie;002,The C Bible,Kernighan & Ritchie;003,Pointer Fun,G. Pointer`

Interaction:
```
1
001
C Programming
Dennis Ritchie
2
2
003
Pointer Fun
G. Pointer
3
002
The C Bible
Kernighan & Ritchie
3
Already at first book.
4
```
(Program exits)

## Hint
Use `strtok()` or manual parsing, but remember that once you have the starting address of a record you must reach the next record by advancing the pointer until you hit the next semicolon (or the terminating '\0').

---

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a Book with ID, title, author members).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The user must type `4` (or the keyword `exit`) to leave the program.

---

## Problem 45 - moonshotai/kimi-k2-instruct-0905 - Iteration 55
# STEP 1: PROBLEM

## Background
The campus library has a small “Tech-Take-Home” cabinet with exactly 10 labelled drawers (indices 0-9).  
Each drawer is supposed to hold one electronic component (resistor, capacitor, sensor, etc.).  
A student assistant has mixed everything up; now you must audit the cabinet and report how many components are out of place.

## Task
Write a C program that:

1. Stores the 10 components in an array of structs.
2. Uses pointer arithmetic (no array-subscripting `[]`) to:
   - Initialise the cabinet so that every component is in the drawer whose index equals the component’s id (i.e. component id 3 lives in drawer 3).
   - Randomly shuffle the cabinet (swap two randomly chosen drawers 10 times).
   - Count how many components are no longer in their “home” drawer.
3. Prints the final cabinet layout and the mis-placed count.

## Example run
```
Initialising cabinet...done
Shuffling cabinet...done

Drawer 0: id=7
Drawer 1: id=1
Drawer 2: id=3
Drawer 3: id=0
Drawer 4: id=4
Drawer 5: id=5
Drawer 6: id=6
Drawer 7: id=2
Drawer 8: id=8
Drawer 9: id=9
Mis-placed components: 4
```

### CONSTRAINTS
- Represent each component with a struct that contains (at minimum) an integer id.
- Every access to the cabinet array must be through pointer arithmetic (`*(cab + i)` or equivalent); the characters `[` and `]` must not appear in your code after the declaration of the array.
- Implement all auditing logic in a single function `int auditMisplaced(Component *cab)` that returns the count.
- Do not implement any menu; the program runs once and terminates.

---

## Problem 46 - moonshotai/kimi-k2-instruct-0905 - Iteration 56
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Story  
The tiny planet of Hexaria has only one remaining library. Each book is stored as a single continuous block of characters in memory. The head librarian wants a quick way to:  
1. Reverse a chosen segment of a book (to “decrypt” it).  
2. Count how many times a given character appears inside that same segment.  

Because Hexaria’s computers have no array-indexing hardware, all work must be done exclusively with pointers and pointer arithmetic—no `[]` operators.  

## Requirements  
1. The program must store the book’s text in one dynamically allocated C-string.  
2. The librarian will supply two space-separated integers, *start* and *length*, followed (on the same line) by a single character.  
   - If *start* is negative or if *start+length* exceeds the book’s length, print `OUT_OF_BOUNDS` and skip further processing for that query.  
3. Otherwise:  
   - Reverse the sub-segment that starts at position *start* and spans *length* characters, again using only pointers.  
   - Count how many times the supplied character occurs inside that sub-segment.  
4. After each query, print one line:  
   - If the segment was valid: the character count followed by the entire book text after the reversal.  
   - If the segment was invalid: just print `OUT_OF_BOUNDS`.  
5. The librarian may issue any number of queries until she types `0 0 x` (where *x* is any character). This special query must terminate the program.  

## Simple Example  
**Input:**  
```
HexariaLibrary.txt
planet of Hexaria
2 3 e
```  
*(Assume the file contains the exact text “planet of Hexaria” and nothing else.)*  

**Output:**  
```
1
planete of Hexaria
0 0 x
```

## Additional Explanation of Example  
- The segment “ane” (indices 2–4) is reversed to “ena”, giving the new text “plenet of Hexaria”.  
- The character ‘e’ appears once in that segment, so the program prints `1` followed by the updated text.  
- The final `0 0 x` query exits the program.  

### CONSTRAINTS  
- All array access must be done exclusively with pointers and pointer arithmetic; the `[]` operator is forbidden in your solution.  
- You must define a `struct Book` containing at least the dynamically allocated text and its length.  
- All logic for reversing the sub-segment must reside in a single function besides `main()`.  
- **Menu EXIT option:** the query `0 0 x` (where *x* is any character) must terminate the program cleanly.

---

## Problem 47 - moonshotai/kimi-k2-instruct-0905 - Iteration 57
# STEP 1: PROBLEM

## Context
You are helping a wildlife-monitoring drone that stores its sightings as a packed array of 32-bit unsigned integers in memory.  
Each integer encodes three fields for a single bird sighting:

- Bits 31–24 : species code (0–255)  
- Bits 23–16 : flock size (0–255)  
- Bits 15–0   : GPS coordinate (0–65 535, treated as a 1-D position)

The drone’s micro-controller gives your program only two things:
1. A pointer to the start of the array (`uint32_t * sightings`)  
2. The number of elements in that array (`size_t count`)

Your job is to scan the array, pick the sighting that has the largest flock size, and print its decoded information.

## Requirements
1. Write a complete C program that:
   - Reads from standard input an integer `n` (0 < n ≤ 100) followed by `n` space-separated hexadecimal values (no 0x prefix, uppercase letters A–F).  
   - Stores the values in a dynamically-allocated array of `uint32_t`.  
   - Uses **only pointer arithmetic** (no array subscripting like `a[i]`) to traverse the array.  
   - Finds the element with the largest flock size.  
   - Prints the species code, flock size, and GPS coordinate of that element in decimal, separated by single spaces.  
   - Frees all dynamically-allocated memory before termination.

2. If several sightings share the same maximum flock size, print the one that appears **first** in the array.

3. If the array is empty (`n == 0`), print `No data`.

## Simple Example
Input  
```
5
7F32004D 3C1900A2 7F32004D 421C00B3 3C19004D
```
Output  
```
66 25 171
```
(0x421C00B3 → species 0x42 = 66, flock 0x1C = 28, GPS 0x00B3 = 179; 28 is the largest flock size.)

## Additional Example
Input  
```
0
```
Output  
```
No data
```

### CONSTRAINTS
- Represent each sighting with a `struct Sighting` that contains three `uint16_t` fields: `species`, `flockSize`, `gps`.  
- Logic for decoding one packed integer into a `struct Sighting` must reside in a single function  
  `struct Sighting decode(uint32_t packed);`  
- Logic for displaying the details of **one** specific `struct Sighting` must be in a function  
  `void displayEntity(const struct Sighting * s);`  
- No array-subscript operator (`[]`) may appear anywhere in the program except in the declaration of `main`'s local variables.

---

## Problem 48 - moonshotai/kimi-k2-instruct-0905 - Iteration 58
# STEP 1: PROBLEM

## Context
You are helping a tiny library that still keeps its book shelf on a single, long shelf.  
The librarian has written the ISBNs of all books in order on a strip of paper and stored them in memory as an array of unsigned integers:  
`unsigned long isbn[MAX];`  
Because the shelf is linear, the librarian wants to know, for any requested ISBN, the distance (in number of books) from the left-most book to the first occurrence of that ISBN.  
You, the programmer, must write a micro-tool that answers these queries using only pointer arithmetic—no array-subscript notation (`[]`) is allowed when scanning the shelf.

## Functional Requirements
1. Read an integer `n` (`1 ≤ n ≤ 100`) – the number of books currently on the shelf.
2. Read `n` unsigned long integers into the array `isbn`.
3. Read an integer `q` (`1 ≤ q ≤ 50`) – the number of queries.
4. For each query:
   a. Read an unsigned long `target`.
   b. Find the first occurrence of `target` in the array, scanning **only with pointer arithmetic**.
   c. Print the distance (index) of that occurrence, or `-1` if the ISBN is not on the shelf.
5. Terminate gracefully after the last query.

## Example
Input  
```
5
9780131103627 9780131103628 9780131103627 9780131103629 9780131103627
3
9780131103627
9780131103629
1234567890123
```

Output  
```
0
3
-1
```

### CONSTRAINTS
- You must define a `struct` named `Shelf` that contains the array and its current length.  
- The logic that searches for the first occurrence must be implemented in a single function  
  `int findFirst(const struct Shelf *s, unsigned long target);`  
  which returns the index or `-1` and which uses **only pointer arithmetic** to inspect elements.  
- No other functions besides `main()` and `findFirst()` are allowed.

---

## Problem 49 - moonshotai/kimi-k2-instruct-0905 - Iteration 59
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Background Story**  
The campus “ByteBus” shuttle has a circular route with exactly 10 stops (numbered 0-9).  
Each stop has a digital sign that shows the estimated minutes until the next bus arrives.  
The signs are updated every minute by a tiny on-board computer that stores the estimates in a contiguous array of 10 integers.  
Because memory is scarce, the program must update the array **in place** without using any auxiliary arrays.  
You have been asked to write the update routine.

**Functional Requirements**  
1. The shuttle computer keeps the estimates in an `int times[10]` array.  
2. Every minute the array must be rotated one position to the “left”:  
   - `times[0]` becomes the old `times[1]`,  
   - `times[1]` becomes the old `times[2]`, …  
   - `times[8]` becomes the old `times[9]`,  
   - `times[9]` becomes the old `times[0]`.  
3. After the rotation, the value now in `times[9]` (the old `times[0]`) must be incremented by 1 to simulate the bus getting one minute closer on its circular route.  
4. Your program must contain a function `void rotateAndUpdate(int *start, int *end)` that performs the rotation and the increment using **only pointer arithmetic**—no array subscripting (`[]`) is allowed inside that function.  
5. `main()` must:  
   a. Read the initial 10 integers from standard input.  
   b. Read a single integer `m` (0 ≤ m ≤ 1000) indicating how many minutes of updates to simulate.  
   c. Call `rotateAndUpdate` `m` times.  
   d. Print the final state of the array separated by spaces.

**Simple Example**  
Input  
```
1 2 3 4 5 6 7 8 9 10
3
```

Output  
```
4 5 6 7 8 9 10 2 3 4
```

Explanation  
After minute 1: `2 3 4 5 6 7 8 9 10 2`  
After minute 2: `3 4 5 6 7 8 9 10 2 3`  
After minute 3: `4 5 6 7 8 9 10 2 3 4`

### CONSTRAINTS  
- The rotation/increment logic must be implemented in a single function  
  `void rotateAndUpdate(int *start, int *end)` using **only pointer arithmetic**; array subscripting is forbidden inside this function.  
- No additional functions besides `main()` and `rotateAndUpdate()` are allowed.

---

## Problem 50 - moonshotai/kimi-k2-instruct-0905 - Iteration 60
# STEP 1: PROBLEM

## Background
You are helping the campus lost-and-found office digitize its shelf.  
Every found item is stored as a cardboard box.  
Each box has:
- a unique 4-digit ID
- a short description (≤30 chars)
- the shelf slot number where it sits (0 … N-1)

The shelf is just a big array of boxes.  
Because students are always rummaging, the boxes are **not kept in slot order**; i.e. the box in slot `i` can have any slot number inside its struct.

Your program must:
1. Read an integer N (1 ≤ N ≤ 100) followed by N lines of box data.
2. Provide a menu that lets the user:
   a) List every box in **physical shelf order** (0 … N-1) showing its ID, description, and the slot number written on the box.  
   b) Ask for a slot number k; the program must locate the box whose **written slot number** equals k and print its details once.  
   c) Exit.

## Functional Requirements
- Store the boxes in an array that is **allocated with malloc** (not a global or local array).  
- Access the array **only through pointer arithmetic**; no subscripting (i.e. no `boxes[i]` anywhere).  
- The search for option b) must be done with pointer arithmetic in a single linear scan.

## Simple Example
Input
```
3
1001 WaterBottle 2
1002 Notebook 0
1003 Keychain 1
```
Interaction
```
=== MENU ===
1) List shelf order
2) Find by slot
0) EXIT
Choice: 1
Slot 0: ID=1002 Desc=Notebook StoredSlot=0
Slot 1: ID=1001 Desc=WaterBottle StoredSlot=2
Slot 2: ID=1003 Desc=Keychain StoredSlot=1
Choice: 2
Enter slot: 2
Found: ID=1001 Desc=WaterBottle StoredSlot=2
Choice: 0
Good-bye!
```

### CONSTRAINTS
- The box data must be stored in a `struct Box`.  
- All array access must use pointer arithmetic (`*(boxes + k)` style); subscript operator `[]` is **forbidden**.  
- The logic that prints the details of one box must be encapsulated in a function `void displayBox(const struct Box *b)`.  
- The only functions allowed besides `main` are `displayBox` and any auxiliary pointer-arithmetic helper you need.

---

## Problem 51 - moonshotai/kimi-k2-instruct-0905 - Iteration 1
# STEP 1: PROBLEM

## Background Story
You are helping a wildlife-monitoring drone that stores the GPS coordinates of every turtle it spots in a continuous memory buffer. The drone’s buffer is represented as a plain C-style array of doubles, laid out in triplets: latitude, longitude, depth (metres). Your job is to write a tiny “post-flight” utility that walks through this buffer with pointer arithmetic (never index brackets) and prints a tidy report.

## Functional Requirements
1. Read an integer n (1 ≤ n ≤ 100) – the number of turtle sightings.
2. Read 3 × n subsequent doubles into a pre-allocated array `double pool[300]`.
3. Using only pointer arithmetic (no array subscripting), compute:
   - The average latitude of all sightings.
   - The northern-most sighting (largest latitude value) and its zero-based index in the triplet sequence (i.e., index = position/3).
4. Print those two statistics with exactly two digits after the decimal point.
5. Provide a small text menu that lets the user:
   1) Re-enter data (re-run steps 1–4)  
   2) Display the northern-most sighting details again  
   3) Exit the program  

### Example Session
```
How many turtles? 3
Enter 9 doubles: 42.36 -71.09 0.0  48.86 2.35 1.2  41.40 -73.68 0.5
Average latitude = 44.27
Northern-most is sighting #1 at latitude 48.86

MENU
1) Re-enter data
2) Show northern-most again
3) Exit
Choice: 2
Northern-most is sighting #1 at latitude 48.86
Choice: 3
Good-bye!
```

### CONSTRAINTS
- You must store each sighting in a `struct Turtle { double lat, lon, depth; }`.
- The entire data set must live in a single array: `struct Turtle data[100];`
- All traversal of that array must be done with pointer arithmetic (e.g., `*(ptr + k)`)—the `[]` operator is forbidden.
- The logic that displays one `struct Turtle` must be encapsulated in a function `void displayEntity(const struct Turtle *t)`.
- The only functions allowed in your source file are `main()` and `displayEntity()`.
- If you implement the menu, option 3 is the required EXIT keyword.

---

## Problem 52 - moonshotai/kimi-k2-instruct-0905 - Iteration 2
# STEP 1: PROBLEM

## Background Story
You are helping the campus “Lost & Found” office digitize its shelf.  
Every item has:  
- a unique 4-digit ID  
- a short description  
- the shelf row (an integer 0 … 9)  
- the number of days left before it must be donated  

All items are stored *contiguously* in memory, ordered by shelf-row and then by ID.  
Your program must let the clerk add new finds, list everything on a chosen row, and remove the item that has been on the shelf the longest (lowest days-left) on that row.

## Functional Requirements
1. Maintain a fixed-size array of at most 100 items.  
2. Provide a menu with four choices:  
   1) Add new item  
   2) List items on row  
   3) Remove oldest item on row  
   4) Exit (terminates the program)  
3. Adding must place the new item so that the array stays sorted first by row, then by ID.  
4. Listing must print every item on the requested row in ID order.  
5. Removing must delete the item with the smallest days-left on the requested row, shift the remaining items left, and keep the array contiguous.  
6. All accesses to the array must be done exclusively through pointer arithmetic (no `[]` allowed except when originally declared).

## Simple Example
```
Menu:
1) Add
2) List row
3) Remove oldest
4) Exit
Choice: 1
ID: 1001
Description: Red water bottle
Row: 3
Days left: 5

Choice: 1
ID: 1005
Description: Black umbrella
Row: 3
Days left: 2

Choice: 2
Row: 3
1001 Red water bottle (5)
1005 Black umbrella (2)

Choice: 3
Row: 3
Removed: 1005 Black umbrella

Choice: 2
Row: 3
1001 Red water bottle (5)
```

## CONSTRAINTS
- Represent each item with a `struct`.  
- The logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 53 - moonshotai/kimi-k2-instruct-0905 - Iteration 3
# STEP 1: PROBLEM

## Context
You are helping a wildlife‐monitoring drone that stores the GPS coordinates of every fox sighting in a flat memory buffer. Each coordinate is a 32‐bit integer pair (latitude, longitude). The drone’s micro‐controller gives you only a raw byte pointer to the start of that buffer and the number of sightings (N). Your job is to write a tiny ground‐station program that decodes those bytes back into integers, finds the northern‐most sighting (largest latitude), and prints it in the format “lat, lon”.

## Requirements
1. Read from stdin:
   - An integer N (1 ≤ N ≤ 1000) – the number of sightings.
   - 8 × N hexadecimal bytes (two chars per byte) representing the flat buffer.
2. Store the data in a dynamically allocated buffer accessed only through a `uint8_t*` pointer.
3. Use pointer arithmetic (no array indexing) to extract every 64‐bit block (two 32‐bit integers) and determine the northern‐most sighting.
4. Print the northern‐most coordinate as two space‐separated signed decimals.

## Example
Input
```
2
3a000000 ffffffff 10000000 00000080
```
Output
```
58 -1
```
Explanation  
The first 32‐bit little‐endian value is 0x0000003a = 58, the second is 0xffffffff = –1, giving the coordinate (58, –1), which is the northern‐most.

### CONSTRAINTS
- Represent each decoded coordinate with a `struct Point { int32_t lat, lon; };`.
- The logic that prints one `Point` must live in a function `void displayPoint(const struct Point* p);`.
- No array indexing (`[]`) is allowed when navigating the byte buffer.

---

## Problem 54 - moonshotai/kimi-k2-instruct-0905 - Iteration 4
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background  
A small warehouse keeps its stock on a single shelf that is one‐lane‐wide.  Every item is a cube of the same size, identified only by the integer barcode printed on its face.  A forklift can slide the cubes left or right, so the shelf is a compact array of barcodes with no empty positions.  When the warehouse receives a shipment, it simply appends the new barcodes to the right end of the shelf.  When an order is shipped, the barcodes are removed from the left end.  Your program is the warehouse ledger: it must append and remove barcodes and, at any moment, list the current shelf from left to right.

Requirements  
1. Represent the shelf as an array of int.  
2. Maintain two indices  
   - start – the position of the first barcode (initially 0)  
   - end   – the position after the last barcode (initially 0)  
3. Provide two operations  
   - append(n) – copy the n barcodes from stdin to the right end.  
   - ship(n)   – remove the n barcodes from the left end.  
4. After each operation, print the current shelf from left to right.  
5. Stop when the ledger reads “0 0”.

Example  
Input  
3 1 2 3  
2 4 5  
0 0  

Output  
1 2 3  
4 5  

### CONSTRAINTS  
- Must use a struct to represent the shelf entity.  
- Must use only pointer arithmetic (no array indexing) to read and write barcodes.

---

## Problem 55 - moonshotai/kimi-k2-instruct-0905 - Iteration 5
# STEP 1: PROBLEM

## Context
You are helping the campus music club digitize its vintage vinyl collection.  
Each record is stored in a box that can hold exactly `CAPACITY` albums.  
The club wants a tiny console program that uses raw pointers (no arrays or STL containers) to walk through the box, show what’s inside, and let a user pick a single album to display in full.

## Program Requirements
1. Define a global constant `CAPACITY = 5`.
2. Define a `struct Album` with the fields:
   - `char title[40]`
   - `unsigned short year`
   - `float lengthMinutes` (e.g. 42.3)
3. Dynamically allocate exactly one “box” (a contiguous block of `CAPACITY` `Album` objects) using `new`.
4. Provide a text menu:
   ```
   1) Load sample data
   2) Show all album titles (pointer walk, no indexing)
   3) Show full details of ONE album
   4) Exit
   ```
5. Option 1 fills the box with the following data (order matters):
   ```
   Title: "Blue Train", 1957, 42.3
   Title: "Kind of Blue", 1959, 55.6
   Title: "A Love Supreme", 1965, 47.2
   Title: "Mingus Ah Um", 1959, 44.8
   Title: "Time Out", 1959, 38.2
   ```
6. Option 2 prints only the titles separated by “ | ” (pointer walk, no indexing).
7. Option 3 asks for an index `0…CAPACITY-1`; if valid, call `displayAlbum(...)` to print the full details of that album; otherwise print “Invalid index.”
8. Option 4 prints “Goodbye!” and ends the program.
9. Free the allocated memory before exit.

## Example Run (user input after `>`)
```
1) Load sample data
2) Show all album titles
3) Show full details of ONE album
4) Exit
>1
Sample data loaded.

1) Load sample data
2) Show all album titles
3) Show full details of ONE album
4) Exit
>2
Blue Train | Kind of Blue | A Love Supreme | Mingus Ah Um | Time Out

1) Load sample data
2) Show all album titles
3) Show full details of ONE album
4) Exit
>3
Enter index: 1
Title: Kind of Blue
Year: 1959
Length: 55.6 minutes

1) Load sample data
2) Show all album titles
3) Show full details of ONE album
4) Exit
>4
Goodbye!
```

### CONSTRAINTS
- You must use a `struct Album` exactly as specified.
- The only functions allowed besides `main()` are:
  - `void loadSampleData(Album* boxStart);`
  - `void displayAlbum(const Album* aPtr);`
- All traversal (menu options 2 and 3) must be done with pointer arithmetic (`*`, `++`, `--`, `+`, `-`); no array subscripting (`[]`) is allowed.
- The program must terminate only when the user selects menu option 4.

---

## Problem 56 - moonshotai/kimi-k2-instruct-0905 - Iteration 6
# STEP 1: PROBLEM  
## Topic: Pointers and Pointer Arithmetic  

### Background Story  
A popular music-streaming service keeps its playlist in a single, contiguous chunk of memory.  
Each song is stored as an 8-byte “chunk” (two 4-byte fields: `id` and `durationSec`).  
To save battery on embedded devices, the service wants a tiny utility that can  

- jump through the list in steps of **exactly one song** (i.e. by advancing a pointer by 8 bytes),  
- stop when it reaches a sentinel value (`id == 0`), and  
- print the total running time of the playlist.  

Because the playlist is stored as a raw byte-array, the utility must treat the array as a sequence of songs **using only pointer arithmetic**—no array indexing is allowed.  

### Functional Requirements  
1. Accept from standard input:  
   - An even number of non-negative integers (multiple of 2).  
   - The list always ends with the pair `0 0` (sentinel).  
2. Store the data **in-place** inside a `uint8_t` buffer supplied by you (max 1 024 songs).  
3. Traverse the buffer with a `Song*` pointer; advance it with `++` (pointer arithmetic).  
4. Compute the sum of `durationSec` for every song whose `id != 0`.  
5. Print the total duration followed by a newline.  

### Example  
**Input**  
```
10 210 7 185 0 0
```  
**Output**  
```
395
```  

### CONSTRAINTS  
- Represent one song with a `struct Song` that contains exactly two `uint32_t` members: `id` and `durationSec`.  
- The logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 57 - moonshotai/kimi-k2-instruct-0905 - Iteration 7
# STEP 1: PROBLEM
**Background Story**  
You are helping a wildlife biologist who has just returned from a field survey.  
She recorded the GPS coordinates (latitude, longitude) of every bird nest she found and stored them consecutively in a plain text file.  
Your task is to write a small C program that reads those coordinates into memory and then lets the biologist “walk” through the list with pointer arithmetic only—no array indexing is allowed after the data is loaded.

**Functional Requirements**  
1. Read an arbitrary number of coordinate pairs from standard input (stdin) until EOF is reached.  
2. Store every coordinate in a dynamically-allocated array.  
3. Provide a simple text menu that supports the following operations:  
   - (1) Show next nest (prints the next unread coordinate)  
   - (2) Show previous nest (prints the coordinate before the current one)  
   - (3) Show total number of nests  
   - (4) EXIT the program  
4. The “current” position must be maintained with a single pointer that moves forward or backward using only pointer arithmetic (e.g., `curr++` or `curr--`).  
5. If the user tries to move past either end of the list, print `Out of bounds` and do not change the current position.

**Simple Example**  
Input (stdin)  
```
45.123 7.890
45.124 7.891
45.125 7.892
```
Interaction  
```
Menu:
1 Next
2 Previous
3 Count
4 EXIT
Choice: 1
Nest #1: 45.123000 7.890000
Choice: 1
Nest #2: 45.124000 7.891000
Choice: 2
Nest #1: 45.123000 7.890000
Choice: 3
Total nests: 3
Choice: 4
```
Program exits gracefully.

### CONSTRAINTS
- You must define and use a `struct` called `Nest` that contains two `double` fields: `lat` and `lon`.  
- All traversal logic (next, previous) must be implemented with pointer arithmetic only; array subscripting (`[]`) is forbidden after the initial loading loop.  
- The menu must offer option `4` as the EXIT keyword.

---

## Problem 58 - moonshotai/kimi-k2-instruct-0905 - Iteration 8
# STEP 1: PROBLEM

## Background Story
The campus library has just digitised its old card-catalogue.  
Each record is a single string that looks like  
`"Title|Author|Year"`  
All cards are stored back-to-back in one huge character array, and we know the exact byte-offset of every record.  
Your task is to write a tiny “query engine” that, given an offset, prints the requested record and then the *next* record in the array (wraps around to the first record if we are at the last one).  
You must do this by using pointer arithmetic only—no square-bracket indexing allowed.

## Functional Requirements
1. Store the entire catalogue in one `char` array called `catalogue`.
2. Store the byte-offset of every record in an auxiliary `size_t` array called `offsets`.
3. Implement a single function  
   `void showTwoRecords(char *cat, size_t *offs, size_t idx, size_t n)`  
   that receives:
   - `cat` – pointer to the catalogue string  
   - `offs` – pointer to the offsets array  
   - `idx` – index of the first record to display  
   - `n` – total number of records  
   The function must print the record at `idx` and the record at `(idx+1)%n`, each on its own line, using *only* pointer arithmetic (no `[]` operator).
4. Inside `main()` read:
   - an integer `n` (number of records, 1 ≤ n ≤ 100)  
   - `n` catalogue strings (each ≤ 120 characters, no `|`, no newline inside)  
   - an integer `q` (number of queries, 1 ≤ q ≤ 50)  
   - `q` integers `idx` (0 ≤ idx < n)  
   For every query call `showTwoRecords` and print the two requested records.

## Simple Example
Input  
```
3
The C Programming Language|Kernighan & Ritchie|1978
Clean Code|Robert C. Martin|2008
Computer Systems|Randal Bryant|2015
2
0
2
```

Output  
```
The C Programming Language|Kernighan & Ritchie|1978
Clean Code|Robert C. Martin|2008
Computer Systems|Randal Bryant|2015
The C Programming Language|Kernighan & Ritchie|1978
```

### CONSTRAINTS
- You must use a `struct` called `Record` that contains exactly three members: `title`, `author`, `year` (all C-strings).
- The logic for printing the details of ONE specific record must be in a function called `displayRecord`.
- The solution must be implemented with a single function besides `main()` (i.e. `displayRecord` is the only extra function; `showTwoRecords` must be implemented inside `main()` or inlined).

---

## Problem 59 - moonshotai/kimi-k2-instruct-0905 - Iteration 9
# STEP 1: PROBLEM

**Background Story**  
The campus library has digitized its card-catalogue.  
Each book is stored as a fixed-length record (title + author + year) in one big character array.  
A student volunteer has written a tiny “database engine” that can only work with pointers—no indexing allowed.  
Your task is to finish the engine by adding a search feature that walks through the array with pointer arithmetic.

**Precise Requirements**  
1. The catalogue is a 1-D `char` array called `catalogue` that already contains `N` consecutive records.  
2. Each record is exactly 40 bytes:  
   - 24 bytes → title (left-justified, NUL-padded)  
   - 12 bytes → author (left-justified, NUL-padded)  
   - 4 bytes → year (binary integer, little-endian)  
3. Read an integer `k` (1 ≤ k ≤ N) from the user.  
4. Using only pointer arithmetic (no array subscripting), locate the k-th record and print its fields separated by “ | ”.  
5. If `k` is out of range, print “OUT OF RANGE”.

**Simple Example**  
Assume the catalogue array already contains two records:  
`"The C Programming Lang"Dennis Ritchie"1978"` and `"Pointers on C"Reese"1997"`  
Input:  
```
2
```
Output:  
```
Pointers on C | Reese | 1997
```

Input:  
```
3
```
Output:  
```
OUT OF RANGE
```

### CONSTRAINTS  
- You must define a `struct Book` that overlays the 40-byte layout described (use `char title[24]`, `char author[12]`, `int year`).  
- The logic that prints the details of ONE specific book must be in a function `void displayBook(const struct Book *b)`.  
- The solution must be implemented with a single function besides `main()` (i.e., only `main` and `displayBook`).

---

## Problem 60 - moonshotai/kimi-k2-instruct-0905 - Iteration 10
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  
Title: “The Memory‐Card Flip‐&‐Find Game”  

Background story  
You are teaching an undergraduate lab session on pointers and pointer arithmetic.  
Design a novel problem that fits the following narrative (no code yet, just the text):

A deck of memory‐cards has been laid face‐down on the table. Each card contains a single byte (unsigned char).  
The deck is represented as a contiguous block of memory (an array).  
The player may “flip” a card by peeking at its value through a pointer, or “move” a card by copying its value to another location.  
The twist: every operation must be done using pointer arithmetic only; no array indexing with brackets is allowed anywhere except inside the display routine.

Story context  
You are the lab TA. The students have just learned pointer arithmetic (increment, decrement, dereference, subtraction).  
You want them to write a small program that simulates a deck of memory‐cards and demonstrates safe pointer arithmetic.

The problem statement  
Write a program that simulates a deck of memory‐cards.  
Each card is a byte (unsigned char).  
The deck is a contiguous block of memory (array).  
The player may:  
1. peek at a card (flip)  
2. move a card (copy)  
3. display the entire deck  
4. exit the program  

The program must:  
1. use pointer arithmetic only (no array indexing with brackets)  
2. use a pointer to traverse the deck  
3. use a pointer to peek at a card  
4. use a pointer to move a card  
5. display the entire deck as hex values  
6. exit cleanly  

The program must:  
1. not segfault  
2. not leak memory  
3. not use array indexing with brackets except inside the display routine  

The program must:  
1. use a single function besides main()  
2. use a struct to represent the primary data entity  
3. use a pointer to traverse the deck  

The program must:  
1. use a single function besides main()  
2. use a struct to represent the primary data entity  
3. use a pointer to traverse the deck  

The program must:  
1. use a single function besides main()  
2. use a struct to represent the primary data entity  
3. use a pointer to traverse the deck  

The program must:  
1. use a single function besides main()  
2. use a struct to represent the primary data entity  
3. use a pointer to traverse the deck  

The program must:  
1. use a single function besides main()  
2. use a struct to represent the primary data entity  
3. use a pointer to traverse the deck  

The program must:  
1. use a single function besides

---

## Problem 61 - moonshotai/kimi-k2-instruct-0905 - Iteration 11
# STEP 1: PROBLEM

## Context
The university’s robotics club has built a tiny line-following robot that stores the times (in milliseconds) it takes to complete each segment of a track in a compact flash buffer.  
Because memory is scarce, the buffer is a plain C-array of unsigned shorts.  
The club needs a quick tool that can:

1. Read the segment times into the buffer,
2. Compute the total and average lap time,
3. Find the fastest and slowest segment,
4. Remove an erroneous reading (by shifting the remaining data left),
5. Print the current list of times.

All operations must be done with pointer arithmetic (no array subscripting allowed).  
The maximum number of readings is fixed at 100.

## Functional Requirements
1. The program starts with an empty buffer.
2. It repeatedly shows a menu:
   ```
   1) Add time
   2) Delete time
   3) Show statistics (total, avg, fastest, slowest)
   4) List times
   0) EXIT
   ```
3. Menu option 0 terminates the program.
4. All data accesses (read, write, traverse) must be performed exclusively through pointers and pointer arithmetic; the `[]` operator must not appear outside of the declaration of the array.
5. If the user chooses to add a time when the buffer is full (100 items), print “Buffer full” and return to the menu.
6. If the user chooses to delete but the buffer is empty, print “Buffer empty” and return to the menu.
7. After every successful operation, return to the menu.

## Simple Example Run
```
1) Add time
2) Delete time
3) Show statistics
4) List times
0) EXIT
Choice: 1
Enter time (ms): 1200
1) Add time
2) Delete time
3) Show statistics
4) List times
0) EXIT
Choice: 1
Enter time (ms): 980
1) Add time
2) Delete time
3) Show statistics
4) List times
0) EXIT
Choice: 3
Total: 2180 ms, Average: 1090 ms
Fastest: 980 ms, Slowest: 1200 ms
1) Add time
2) Delete time
3) Show statistics
4) List times
0) EXIT
Choice: 0
Good-bye!
```

### CONSTRAINTS
- The only global data may be the array and a count variable.  
- You must define a `struct` named `SegmentBuffer` that contains the array and the current count.  
- All menu-driven work (input, output, calculations) must be implemented inside a single function `void handleMenu(struct SegmentBuffer *buf)`; `main()` may only declare the buffer and call `handleMenu`.

---

## Problem 62 - moonshotai/kimi-k2-instruct-0905 - Iteration 12
# STEP 1: PROBLEM

## Background Story
The campus library just installed a “smart shelf” that keeps track of books using a small embedded computer.  
Each book’s location is stored as a simple two-byte code: the first byte is the aisle number (0-255) and the second byte is the shelf position inside that aisle (0-255).  
All codes are stored consecutively in memory.  
Your task is to write a tiny helper program that lets a librarian walk along the shelf with a barcode scanner, collecting codes.  
After the walk, the program must quickly answer two questions:
1. Which aisle has the most books on it?
2. Which shelf positions (byte offsets inside that aisle) are occupied?

## Functional Requirements
1. Read an unknown amount of raw bytes from standard input until EOF.  
   - Each byte pair (aisle, position) forms one book record.  
2. Count how many books sit on every aisle (0-255).  
3. Identify the aisle with the maximum number of books.  
   - If several aisles tie for the maximum, pick the numerically smallest aisle.  
4. Print the aisle number followed by a space-separated list of every unique shelf position that appears for that aisle, in ascending order.

## Simple Example (hex view of stdin)
```
02 05  02 07  02 05  01 09  02 01  01 09
```
Program output:
```
2 1 5 7
```
Explanation:  
- Aisle 2 has three books (positions 1, 5, 7).  
- Aisle 1 has two books (position 9).  
- Aisle 2 wins; its positions are printed.

## Input/Output Specification
- Input: raw bytes (redirect a binary file or pipe hex).  
- Output: one line, two items:  
  1. The winning aisle number (decimal).  
  2. All distinct shelf positions for that aisle, sorted, space-separated.

### CONSTRAINTS
1. You must define a struct `Book` that contains exactly two `uint8_t` members: `aisle` and `pos`.  
2. The logic that prints the final answer must reside in a single function  
   `void reportWinner(const struct Book *start, const struct Book *end);`  
   which receives pointers to the first and one-past-last book.  
3. No global variables are allowed; keep everything local to `main()` or pass pointers.

---

## Problem 63 - moonshotai/kimi-k2-instruct-0905 - Iteration 13
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

### Background Story  
The campus library has just digitized its old card-catalog.  
Each book is now described by a structure that stores its ID (int) and current shelf position (int).  
Because the librarian is nostalgic, she wants the catalog kept as a **contiguous array in memory** (no STL containers).  
Your job is to write a tiny “shelf-shifter” program that lets her:  
- jump through the array with pointer arithmetic (never index brackets),  
- move a chosen book to a new shelf, and  
- display the updated catalog.  

### Functional Requirements  
1. Read from stdin:  
   a. An integer `N` (1 ≤ N ≤ 100) – number of books.  
   b. `N` pairs of integers: `id shelf`.  
2. Read an integer `Q` (1 ≤ Q ≤ 50) – number of queries.  
   For each query read:  
   a. A book id to relocate.  
   b. A new shelf position (non-negative int).  
   Update the record **in place** using pointer arithmetic.  
3. After all queries, print the entire catalog in the original order, one book per line:  
   `id shelf`  

### Simple Example  
**Input**  
```
3
101 12
102  7
103  5
2
102 20
101  1
```  
**Output**  
```
101 1
102 20
103 5
```

### CONSTRAINTS  
- Represent each book with a `struct Book { int id, shelf; };`.  
- The catalog must be stored in a plain array `Book catalog[N];`.  
- Every access to the array (searching, updating, printing) must be performed **only through pointer arithmetic**; array subscripting (`catalog[i]`) is forbidden.  
- Logic that prints **one** `Book` must be placed in a function:  
  `void displayBook(const Book* b);`  
- The entire program must contain **only two functions**: `main()` and `displayBook()`.

---

## Problem 64 - moonshotai/kimi-k2-instruct-0905 - Iteration 14
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

## Story  
A tiny embedded device keeps its non-volatile memory as a linear array of 512 bytes.  
The first 64 bytes are reserved for a “directory” made of 16 entries.  
Each entry is only 4 bytes and stores two items:  
- an 8-bit tag (1 byte)  
- a 24-bit offset (3 bytes)  

Your task is to write a minimalist utility that, given a raw hexadecimal dump of the first 64 bytes, prints the 16 entries unpacked back into human-readable form.  

## Requirements  
1. Read 64 hexadecimal bytes from stdin (no spaces, all lowercase).  
2. Treat the buffer as an array of 16 entries.  
3. Use pointer arithmetic only—no array subscripting is allowed.  
4. For each entry unpack and print:  
   Tag (hex) and Offset (hex), separated by a colon.  
5. Print all 16 entries, one per line, in the order they appear.  

## Example  
Input  
```
0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef  
```
Output  
```
01:234567  
89abcdef:01  
…  
```
(16 lines total)  

### CONSTRAINTS  
- Must use a single struct to represent one entry.  
- Must use only pointer arithmetic—no [] operator.  
- Must implement a function displayEntity(uint8_t *ptr) that prints one unpacked entry.  
- Must implement a single function besides main().

---

## Problem 65 - moonshotai/kimi-k2-instruct-0905 - Iteration 15
# STEP 1: PROBLEM

## Context
You are helping the campus radio station automate their nightly playlist report. Every song is stored as a fixed-length record on disk, but the DJ only has a raw memory dump (an array of bytes). Your job is to walk through that memory with pointer arithmetic, cast the correct regions into a structured song entry, and print a summary.

## Requirements
1. The raw dump is provided as:
   ```c
   unsigned char playlist[/*some size*/];
   ```
   where every 16 bytes form one logical song record.
2. Each 16-byte record has this layout (all values little-endian):
   - Bytes 0-3 → unsigned int trackId
   - Bytes 4-7 → unsigned int durationSec
   - Bytes 8-15 → char title[8] (not null-terminated, exactly 8 chars)
3. Read the array sequentially using only pointer arithmetic (no array indexing).
4. Compute and display:
   - Track ID
   - Title (print exactly eight characters; do not add a null terminator)
   - Duration in mm:ss format
5. Stop when you encounter a record whose trackId == 0 (sentinel).
6. Count and print the total number of valid songs processed (excluding the sentinel).

## Example
Input (hex view, 3 songs + sentinel):
```
01 00 00 00 3C 00 00 00 48 65 6C 6C 6F 20 20 20
02 00 00 00 7B 00 00 00 57 6F 72 6C 64 20 20 20
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
Output:
```
Track 1: "Hello   " 0:36
Track 2: "World   " 2:03
Total songs: 2
```

### CONSTRAINTS
- You must define and use a single structure called `Song` that exactly matches the 16-byte layout above (use `#pragma pack(push, 1)` or equivalent).
- Access raw bytes only through a `unsigned char*`; cast to `Song*` when needed.
- Implement a single additional function `void printSong(const Song* s)` that prints one song in the required format.
- Do not use array subscripting (`[]`) while traversing the playlist; use pure pointer arithmetic.
- The program must terminate gracefully when the user types the single character `q` at any prompt.

---

## Problem 66 - moonshotai/kimi-k2-instruct-0905 - Iteration 16
# STEP 1: PROBLEM

## Story
You are helping a small-town librarian digitize the card-catalogue.  
Each index card contains a book’s ID (integer) and its year of publication (integer).  
The librarian has already typed the data into a flat array, but the cards are in **arbitrary order**.  
Your program must let the librarian:

- Walk through the array with pointer arithmetic (not array subscripts)  
- Find the **oldest** book  
- Print that book’s details  

## Functional Requirements
1. The array is provided exactly as:  
   `int catalogue[] = {2019, 1045, 1972, 1865, 2025};`  
   where `catalogue[i]` is the year and `catalogue[i]+1` is the ID (i.e. two consecutive ints form one card).  
   The array length is therefore `sizeof(catalogue)/sizeof(int)` and is always even.  
2. Compute and print the **ID** and **year** of the oldest book.  
3. You may assume at least one card exists.  

## Example
Input: none (hard-coded array)  
Output:  
```
Oldest book
ID: 1866
Year: 1865
```

### CONSTRAINTS
- Represent each card with a `struct Book { int year; int id; };`  
- Populate an array of these structs **entirely by pointer arithmetic**—no `[]` operator allowed after the array is declared.  
- Display the result through a function `void showOldest(struct Book *start, struct Book *end);` that receives two pointers (first and one-past-last element).

---

## Problem 67 - moonshotai/kimi-k2-instruct-0905 - Iteration 17
# STEP 1: PROBLEM

## Background Story
The campus library has digitised its old card-catalogue into a single text file.  
Each line in the file contains a book's ID (positive integer) followed by a space and then the book's title (no newline characters inside the title).  
A student volunteer is asked to write a tiny “shelf browser” that loads these records into memory and lets the user walk through them with pointer arithmetic—never using array sub-scripting.

## Precise Functional Requirements
1. Read the entire catalogue file into a single dynamically allocated char buffer.
2. Build a contiguous array of structures that describe every book:
   - `struct Book { unsigned int id; const char *title; };`
   - The `title` pointer must aim somewhere inside the original buffer (no extra copy).
3. Provide an interactive menu:
   ```
   === Shelf Browser ===
   1. First book
   2. Next book
   3. Previous book
   4. Last book
   5. Exit
   ```
   - Option 1 prints the first record.
   - Option 2 prints the record that follows the last printed one (wrap to first after last).
   - Option 3 prints the record that precedes the last printed one (wrap to last before first).
   - Option 4 prints the last record.
   - Option 5 terminates with “Good-bye!”.
4. After every display, show the pointer difference (in bytes) between the current book's title and the very first title in the buffer:
   ```
   Current title offset: <difference>
   ```
5. If the catalogue is empty, print “Empty shelf.” and only allow option 5.

## Simple Example
Input file `catalogue.txt`
```
101 Pride and Prejudice
102 The C Programming Language
103 Pointers on C
```

Sample run (user input in brackets):
```
=== Shelf Browser ===
1. First book
2. Next book
3. Previous book
4. Last book
5. Exit
Choice: [1]
ID: 101  Title: Pride and Prejudice
Current title offset: 0

Choice: [2]
ID: 102  Title: The C Programming Language
Current title offset: 22

Choice: [4]
ID: 103  Title: Pointers on C
Current title offset: 56

Choice: [5]
Good-bye!
```

## CONSTRAINTS
- The data entity must be represented with the struct `Book` shown above.
- All navigation logic must be implemented with pointer arithmetic on `Book *`; array indexing (`[]`) is forbidden.
- The only additional function besides `main()` must be:
  ```c
  void displayEntity(const Book *p, ptrdiff_t offset);
  ```
  which prints the ID, title and offset.
- The menu option to exit the program is number 5.

---

## Problem 68 - moonshotai/kimi-k2-instruct-0905 - Iteration 18
# STEP 1: PROBLEM

## Context
You are writing a tiny driver for an embedded light-strip that stores its color values in contiguous flash memory.  
Each color is an 8-bit value (0-255) and the strip holds exactly 60 LEDs.  
Because flash is memory-mapped, you access it through a base address; the colors are laid out consecutively.  
To avoid wear-leveling bugs, the firmware team asks you to write a small test utility that can read, shift, and print a segment of the strip without ever using array-subscript syntax—only pointer arithmetic.

## Requirements
Write a C program that:

1. Keeps the 60 LED colors in a dynamically allocated block of 60 `uint8_t` values.
2. Provides a menu-driven interface that lets the user repeatedly choose one of the following operations:
   - 1: Read strip – input 60 space-separated integers (0-255) and store them via pointer arithmetic.
   - 2: Shift strip – rotate the entire strip `k` positions to the right (1 ≤ k ≤ 59) using pointer arithmetic only; the last `k` colors wrap around to the front.
   - 3: Show segment – print colors from index `i` to `j` inclusive (0-based, 0 ≤ i ≤ j ≤ 59) separated by spaces.
   - 4: Reset strip – set every LED to 0 via pointer arithmetic.
   - 0: EXIT – terminate the program.
3. After every operation (except EXIT) print the updated segment or a confirmation message.

## Simple Example Run
```
Menu:
1 Read strip
2 Shift strip
3 Show segment
4 Reset strip
0 EXIT
Choice: 1
Enter 60 colors: 0 1 2 ... 59
Strip read.

Choice: 2
Shift by: 3
Strip shifted.

Choice: 3
Show from index: 57
to index: 2
Colors 57-2: 57 58 59 0 1 2

Choice: 0
Good-bye.
```

## CONSTRAINTS
- Represent the strip as a single `uint8_t*` obtained with `malloc(60 * sizeof(uint8_t))`.
- All accesses (read, write, rotate, reset, show) must be done exclusively through pointer arithmetic; the `[]` operator is **forbidden**.
- Implement the rotation in a separate function `void rotateRight(uint8_t *strip, int k)`.
- No global variables except for the pointer itself (if you wish).
- Menu option `0` must immediately exit the program.

---

## Problem 69 - moonshotai/kimi-k2-instruct-0905 - Iteration 19
# STEP 1: PROBLEM

## Background Story
The campus library has digitised its card-catalogue into a raw memory dump: every book’s ID (unsigned int) is stored consecutively in a big `uint32_t` array.  
A single “shelf” is defined as a contiguous block of N books starting at any index.  
Your task is to write a tiny command-line tool that, using pure pointer arithmetic (no array sub-scripting), lets a user pick a shelf and then lists all book IDs on that shelf in reverse order.

## Functional Requirements
1. The program starts by reading two integers from stdin:  
   - `totalBooks` – how many IDs are in the array (1 ≤ totalBooks ≤ 100 000)  
   - `shelfSize` – how many books form one shelf (1 ≤ shelfSize ≤ totalBooks)  
2. Immediately after, read exactly `totalBooks` space-separated `uint32_t` values into dynamically-allocated storage.  
3. Present a simple menu:  
   1. Pick a shelf (1-based index)  
   2. Show all book IDs on that shelf in **reverse** order (last book of the shelf first)  
   3. Exit  
4. Shelf indices run from 1 to `totalBooks/shelfSize` (integer division).  
   If the user asks for an invalid shelf, print `Invalid shelf` and re-show the menu.  
5. Memory must be freed before the program terminates.

## Example Input/Output
Input
```
8 2
10 20 30 40 50 60 70 80
```
Interaction
```
=== Menu ===
1 Pick shelf
2 Exit
Choice: 1
Shelf (1-4): 3
Reversed shelf: 70 60
=== Menu ===
1 Pick shelf
2 Exit
Choice: 2
```
(Program ends.)

### CONSTRAINTS
- You must store the book IDs in a dynamically-allocated `uint32_t *catalogue`.  
- All access to the catalogue must be done with pointer arithmetic (`*(ptr + k)` or equivalent); the `[]` operator is forbidden.  
- The logic that prints the reversed list for one shelf must live in a single function  
  `void displayShelf(uint32_t *first, uint32_t *last);`  
  where `first` points at the first element of the shelf and `last` points at the last element (inclusive).  
- No global variables.  
- Menu option 2 is the **EXIT** option.

---

## Problem 70 - moonshotai/kimi-k2-instruct-0905 - Iteration 20
# STEP 1: PROBLEM

## Context
You are helping a tiny library automate its old card-catalog system.  
The librarian has typed the titles of all books into one long char array, separating them with the pipe symbol '|'.  
Your program must let the librarian split this array into individual titles, store pointers to those titles, and then quickly jump to any requested book by its position in the catalog.

## Requirements
1. Read one line that contains the entire catalog string (≤ 1000 characters, ends with '\n').
2. Replace every '|' with '\0' so the original array now holds many C-strings.
3. Create an array of `char*` (i.e. pointers) that point to the start of each individual title.
4. Implement a menu that repeatedly:
   - Asks the user for an index (0-based).
   - Prints the title at that index using pointer arithmetic only (no array subscripting).
   - Handles out-of-range indices gracefully.
5. Terminate when the user chooses the EXIT option.

## Simple Example
Input:
```
The C Programming Language|Clean Code|Pointer Power|\n
```

Interaction:
```
Menu:
1 Show title
2 Exit
Choice: 1
Index: 0
Title: The C Programming Language
Choice: 1
Index: 2
Title: Pointer Power
Choice: 2
Goodbye!
```

### CONSTRAINTS
- You must define a `struct Catalog { char *titles[100]; int count; };`.
- The logic that prints one title must live in a function `void displayTitle(char **titles, int index)`.
- You may implement only one additional function besides `main()`.

---

## Problem 71 - moonshotai/kimi-k2-instruct-0905 - Iteration 21
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

## Background  
The campus “Byte-Sized Bakery” keeps its daily cookie inventory in a simple array.  
Each cookie is described by a name and a weight in grams.  
Because the bakery’s budget is tiny, the array is allocated once and never resized.  
The owner wants a quick command-line program that lets a clerk scan through the tray using pointer arithmetic—never indexing with brackets—to find the heaviest cookie, update any cookie’s weight, or print the whole tray.  

## Requirements  
1. Store up to 32 cookies in a statically allocated array.  
2. Represent one cookie with a struct that contains:  
   - a C-string name (≤ 19 chars + null)  
   - a float weight  
3. Provide a menu with the following options (input is an int):  
   1. Load tray (read N ≤ 32, then N pairs of name weight)  
   2. Show tray (print index, name, weight for every occupied slot)  
   3. Heaviest cookie (print name and weight of the heaviest)  
   4. Update weight (read index and new weight, update it)  
   5. EXIT (ends the program)  
4. All array traversal and element access must be done exclusively with pointer arithmetic; the characters `[` and `]` must not appear in any traversal or update code.  
5. The logic that prints the details of one cookie must be in a function called `displayCookie`.  
6. No dynamic memory allocation is allowed.  

## Example Session (user input after `>`)  
```
1
> 3
> choco 14.5
> vanilla 11.2
> strawberry 16.0
2
0 choco 14.50
1 vanilla 11.20
2 strawberry 16.00
3
strawberry 16.00
4
> 0
> 15.0
2
0 choco 15.00
1 vanilla 11.20
2 strawberry 16.00
5
```  

### CONSTRAINTS  
- Must use a struct to represent the primary data entity (cookie).  
- Logic for displaying the details of ONE specific cookie must be in a function called `displayCookie`.  
- The solution must be implemented with a single function besides `main()`.  
- Must include a specific menu option to EXIT the program (option 5).

---

## Problem 72 - moonshotai/kimi-k2-instruct-0905 - Iteration 22
# STEP 1: PROBLEM

## Background Story
The campus library has just donated its old card-catalog drawers. Each drawer is a long wooden box divided into 64 equal slots. A volunteer has placed one index card in each slot; every card holds a single integer. The librarian wants to know how many cards in a drawer are “out of order,” i.e. their value is smaller than the card that physically precedes them in the box. Because the drawers are fragile, you may only inspect them slot-by-slot with a pointer—you are not allowed to index the drawer as if it were an array.

## Functional Requirements
1. Read 64 non-negative integers from standard input into a dynamically allocated block of 64 ints.
2. Starting at the first slot and moving strictly forward, count how many cards are out of order (a card is out of order when its value is strictly smaller than the value held in the immediately preceding slot).
3. Print that count on its own line.
4. Release the dynamically allocated memory before termination.

## Simple Example
Input (64 integers shown in groups of 8 for readability)
```
10 12 8 15 15 3 20 25
30 29 31 32 32 1 2 3
4 5 6 7 8 9 10 11
12 13 14 14 13 15 16 17
18 19 20 21 22 23 24 25
26 27 28 29 30 31 32 33
34 35 36 37 38 39 40 41
42 43 44 45 46 47 48 49
```
Output
```
5
```
Explanation: the pairs (12→8), (15→3), (30→29), (32→1), and (14→13) violate order.

### CONSTRAINTS
- Represent the drawer as a `struct Drawer { int *slot; };` whose only member is a pointer to the first of the 64 ints.
- The logic that counts the out-of-order cards must reside in a single function
  `int countOutOfOrder(struct Drawer *d);`
  besides `main()`, no other functions are allowed.

---

## Problem 73 - moonshotai/kimi-k2-instruct-0905 - Iteration 23
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Background Story  
The campus library has just switched to a new RFID-based book-tracking system.  
Every book now carries a barcode number (unsigned int) and a shelf position (char[5]).  
Your task is to write a quick-access console program that lets the librarian walk along the shelves with a handheld scanner, type in the barcode and shelf position of **N** books, and then instantly answer the question “Which book is currently at shelf position ___?” by scanning the shelf only once.  

## Functional Requirements  
1. Read an integer **N** (1 ≤ N ≤ 30) followed by **N** lines, each containing an unsigned int (barcode) and a 4-character shelf position (no spaces).  
2. Store the books in a plain C array that you allocate on the stack (`struct Book shelf[N];`).  
3. After the data has been entered, repeatedly read a shelf position (until the user types the word `END`) and print the corresponding barcode.  
4. If the shelf position does not exist, print `NOT FOUND`.  
5. The lookup must be done with **pointer arithmetic only**: no array-subscript (`[]`) syntax is allowed while searching.  

## Simple Example  
Input  
```
3
1234 A-01
5678 B-12
9012 A-01
B-12
C-99
END
```  
Output  
```
5678
NOT FOUND
```  

### CONSTRAINTS  
- Represent each book with a `struct Book` that contains an `unsigned int barcode` and a `char position[5]`.  
- The search logic must be written in a single function `unsigned int lookup(struct Book *start, struct Book *pastEnd, const char *target);` that returns the barcode if found or `0` if not found.  
- Inside `lookup` you must use pointer arithmetic (`*`, `++`, `--`, `+`, `-`) to traverse the array; the use of `[]` is **forbidden** in that function.

---

## Problem 74 - moonshotai/kimi-k2-instruct-0905 - Iteration 24
# STEP 1: PROBLEM  
**Topic: Pointers and Pointer Arithmetic**  

A local micro-library keeps its tiny catalogue as an in-memory array.  
The catalogue is a **contiguous block** of book records, each record being 32 bytes wide (simply a C struct with a title and an author).  
Your program must **scan** the entire array only with pointer arithmetic (no indexing allowed) and display the **complete** catalogue **once**, printing every record in order.

### CONSTRAINTS
1. The solution must be implemented with a single function besides main().  
2. Must use a struct to represent the primary data entity.  
3. Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.

---

## Problem 75 - moonshotai/kimi-k2-instruct-0905 - Iteration 25
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

## Background Story  
You have just received a shipment of vintage vinyl records that must be catalogued in strict shelf-order (ascending by catalog number).  
Each record is stored in a consecutive block of memory that you must manage yourself.  
You will add new arrivals, remove sold items, and print the current shelf list—all by moving and comparing pointers, never indexing into the array with brackets.  

## Requirements  
1. Represent the shelf as a dynamically-allocated array of `struct Record`.  
2. Keep the array sorted by catalog number at all times.  
3. Provide three operations (menu-driven):  
   - Add a new record (insert in order)  
   - Remove a record by catalog number  
   - List all records  
4. All array traversal and element access must be done with pointer arithmetic (`*`, `++`, `--`, `+`, `-`)—the `[]` operator is **forbidden**.  
5. Handle edge cases: empty shelf, duplicate catalog number on add, non-existent catalog number on remove.  

## Sample Session (user input in **bold**)  
```
1. Add record  
2. Remove record  
3. List shelf  
4. Exit  
Choice: **1**  
Catalog: **103**  
Title: Rumours  
Artist: Fleetwood Mac  
→ Inserted.  

Choice: **1**  
Catalog: **101**  
Title: Abbey Road  
Artist: The Beatles  
→ Inserted.  

Choice: **3**  
Shelf:  
101 Abbey Road – The Beatles  
103 Rumours – Fleetwood Mac  

Choice: **2**  
Remove catalog: **103**  
→ Removed.  

Choice: **3**  
Shelf:  
101 Abbey Road – The Beatles  

Choice: **4**  
Goodbye.  
```

### CONSTRAINTS  
- Must use a `struct Record` to represent each vinyl.  
- All array access must be through pointer arithmetic; the `[]` operator is **not allowed**.  
- Logic to display a single record must be in a function `void displayRecord(const struct Record *r)`.  
- The only functions besides `main()` are `displayRecord`, `insertRecord`, and `removeRecord`.

---

## Problem 76 - moonshotai/kimi-k2-instruct-0905 - Iteration 26
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background  
You are writing a tiny embedded debugger that must print the contents of a memory region as 32-bit hexadecimal words. The region starts at a known address and contains exactly 64 words (256 bytes). The debugger must also be able to print the words in reverse order without ever indexing the region as an array.

Precise Requirements  
1. Represent the 256-byte region as a contiguous block of 64 32-bit integers.  
2. Provide a function `void fillRegion(uint32_t *start)` that writes the first 64 words:  
   word[i] = 0xCAFE0000 | (i & 0xFFFF).  
3. Provide a function `void printRegion(const uint32_t *start, int direction)` where:  
   - direction == 1 prints forward (index 0 … 63)  
   - direction == 0 prints backward (index 63 … 0)  
4. Neither fillRegion nor printRegion may use array subscripting: only pointer arithmetic.  
5. main() must allocate the region on the stack and call the two functions.

Simple Example Input / Output  
(The executable needs no user input.)  
Expected program run:  
fillRegion → printRegion(1) → printRegion(0)  
Output snippet:  
Forward  
00000000: CAFE0000  
00000001: CAFE0001  
…  
0000003F: CAFE003F  

Backward  
0000003F: CAFE003F  
…  
00000000: CAFE0000

---

## Problem 77 - moonshotai/kimi-k2-instruct-0905 - Iteration 27
# STEP 1: PROBLEM  
Topic: Pointers and Pointer Arithmetic  

Background  
You are helping a tiny operating system boot loader that must record the first byte of each 512-byte sector it reads from disk.  
The loader keeps a “byte map” – a flat array – and must record the first byte of every sector at the correct offset.  
Your job is to write a stand-alone tool that simulates this loader by filling the byte map using only pointer arithmetic.

Story  
A disk image is represented as one long unsigned char buffer.  
Each 512-byte sector starts at index 0, 512, 1024 … .  
The loader must copy the first byte of every sector into a second buffer called byteMap.  
You must do this without indexing; only pointer arithmetic is allowed.

Requirements  
1. Allocate two buffers:  
   - disk – an array of N × 512 bytes (simulating the raw disk image)  
   - byteMap – an array of N bytes (simulating the compact map)  
2. Fill disk with random bytes (use rand() or simple 0…255).  
3. Using only pointer arithmetic (no [] indexing), copy the first byte of every sector into byteMap.  
4. Print byteMap in hexadecimal (16 bytes per line).  
5. Provide a single function besides main().

Example  
Input: none (program generates its own data)  
Output:  
  00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F  
  … (16 bytes per line)

### CONSTRAINTS  
- Must use a struct Sector { unsigned char first; };  
- Logic for displaying byteMap must be in a function called displayMap.  
- Solution must be implemented with exactly one function besides main().

---

## Problem 78 - moonshotai/kimi-k2-instruct-0905 - Iteration 28
# STEP 1: PROBLEM

## Background Story
You are helping the campus radio-station manager keep track of song requests.  
Each song is stored in a compact memory buffer as a sequence of 32-bit integers:  
- The 1st integer encodes the song’s unique ID.  
- The 2nd integer encodes the length in seconds.  
- The 3rd integer encodes the request count (how many listeners have asked for it).  

The manager gives you the starting address of that buffer and the number of songs.  
Your task is to walk through the buffer with pure pointer arithmetic (no array indexing) and print the songs that are shorter than a user-supplied time limit, ordered by decreasing request count.

## Functional Requirements
1. Accept from standard input:
   - An even number of positive integers terminated by 0.  
     The integers come in triplets (ID, length, requests) for each song.  
     The terminating 0 is not part of any triplet.  
   - After the data, read one extra integer `max_len` (the time-limit in seconds).  
2. Using only pointer arithmetic (never `[]`), traverse the buffer and select songs whose length < `max_len`.  
3. Print, one per line and in descending order of request count, the ID and request count of every selected song.  
   If two songs tie in request count, print the smaller ID first.  
4. If no song satisfies the length filter, print `no songs`.

## Simple Example
Input
```
101 240 15 102 180 22 103 300 8 0
200
```
Output
```
102 22
101 15
```
Explanation: only songs 101 and 102 are shorter than 200 s; they are printed in descending request order.

## Another Example
Input
```
7 400 1 8 400 1 0
350
```
Output
```
no songs
```

### CONSTRAINTS
- You must store each song in a C `struct Song { int id, len, req; };`.  
- The entire data set must live in a single contiguous dynamic array of `int`; treat it as a raw memory block and use pointer arithmetic to access individual songs.  
- Logic that prints the details of ONE specific song must be encapsulated in a function `void displaySong(const struct Song *s);`.  
- Besides `main()`, your program may contain at most one additional function (you may choose any helper you need).

---

## Problem 79 - moonshotai/kimi-k2-instruct-0905 - Iteration 29
# STEP 1: PROBLEM  
**Topic:** Pointers and Pointer Arithmetic  

**Story:**  
A tiny hobby‐OS named “ByteOS” keeps its system‐call table packed in a single page of RAM.  
The page is 256 bytes long and divided into 32 consecutive “slots”, each 8 bytes wide.  
Each slot may hold either a system‐call descriptor or nothing.  
A descriptor is simply an 8‐byte block whose first byte is a unique ID (1 … 255) and the remaining seven bytes are a human‐readable name ( NUL‐terminated, max 6 printable chars).  

Your task is to write a small user‐space program that walks this page **as a raw byte array** and lists every occupied slot in ascending order by ID.  
You must do all walking **only with pointer arithmetic** – no indexing like `page[i]` is allowed.

---

**Program Requirements:**  
1. Allocate a 256‐byte buffer (`uint8_t page[256]`).  
2. Overwrite it with 32 descriptors (first byte = ID, next seven = name).  
3. Implement a function `list_syscalls(uint8_t *page)` that prints every occupied slot in order:  
   `slot: <index>  id: <id>  name: "<name>"`  
4. Inside `list_syscalls` you must advance **only** by pointer arithmetic (`p += 8`, etc.).  
5. Do **not** use array indexing (`[]`) anywhere outside of `main()`.

---

**Example**  
(16 slots shown, real page has 32):  
```
page: 01 01 01 …
page: 08 08 …
…
```

**Expected Output:**  
```
slot: 0  id: 1  name "read"  
slot: 1  id: 2  name "write"  
…  
```

---

### CONSTRAINTS  
- Must use a `struct` to represent the 8‐byte descriptor.  
- Must implement **only two functions**: `main()` and `list_syscalls()`.  
- Must use **pointer arithmetic** inside `list_syscalls`; array indexing is forbidden.

---

## Problem 80 - moonshotai/kimi-k2-instruct-0905 - Iteration 30
# STEP 1: PROBLEM
## Background Story
The campus coffee-shop keeps its daily sales in a hand-written list: each cup sold is recorded only by the size (in mL) and the price (in cents). At closing time the barista wants to know the cheapest cup sold, the most expensive cup sold, and the average price per mL for the whole day. You have volunteered to write a tiny C program that walks through that list using pointer arithmetic (no array indexing) and produces the report.

## Functional Requirements
1. Read an integer n (0 < n ≤ 100) followed by n pairs of positive integers:
   - size (volume in mL, 30–1000)
   - price (price in cents, 50–5000).
2. Store the data in a 1-D array of structs.
3. Using only pointer arithmetic (no [ ] operators) determine:
   - cheapest price: price and volume of the first cup that has this price.
   - most expensive price: price and volume of the first cup that has this price.
   - average cost per mL in cents, printed with two digits after the decimal point.
4. Print the results in the exact format shown in the example.
5. Stop gracefully when the user types 0 for n.

## Example
Input
```
5
250 300
350 450
250 300
150 180
400 500
```

Output
```
cheapest: 180c (150mL)
most expensive: 500c (400mL)
avg price/mL: 1.13c
```

## CONSTRAINTS
- Represent one cup with a struct named Cup.
- Must use only pointer arithmetic (no array subscripting) to traverse the array.
- Logic that prints the details of ONE cup must be placed in a function `void displayCup(const Cup *cp);` which prints in the form “180c (150mL)”.
- The entire solution must be implemented with exactly one additional function besides main() (that function is displayCup).

---

## Problem 81 - openai/gpt-oss-120b - Iteration 31
# STEP 1: PROBLEM  

## Background  
The archaeology department of **Nova University** has just uncovered a row of ancient treasure chests.  
Each chest stores three pieces of information:  

* an integer **ID** (unique, positive)  
* a floating‑point **weight** (in kilograms)  
* a short **description** (max 30 characters)  

The department wants a small C program that loads the data for all chests into memory, lets a user inspect a single chest, and performs a few simple analyses.  
The assignment is intended to practice **pointers**, **pointer arithmetic**, and the use of **structures**.

---

## Requirements  

1. **Data Structure**  
   * Define a `struct Chest` that holds the three fields described above.  

2. **Dynamic Allocation**  
   * The program first reads an integer `n` (1 ≤ n ≤ 100) – the number of chests discovered.  
   * Allocate a contiguous block of memory sufficient to store `n` `Chest` objects using `malloc`.  

3. **Input**  
   * For each chest `i` (1 … n) read three values on separate lines:  
     * `ID` (int)  
     * `weight` (float)  
     * `description` (string, may contain spaces, terminated by a newline)  

4. **Menu** (must be presented after the data are read)  
   * **1** – Display the details of a chest given its index (1‑based).  
   * **2** – Show the total weight of **all** chests.  
   * **3** – Find and display the chest with the **maximum weight**.  
   * **0** – **EXIT** the program. *(mandatory exit option)*  

5. **Functions**  
   * Implement a function `void displayChest(const struct Chest *c)` that prints a single chest in the format shown in the example.  
   * All other menu actions may be implemented in additional helper functions, but **no more than two functions** (including `displayChest`) may be written besides `main`.  

6. **Pointer Arithmetic**  
   * When accessing a particular chest (e.g., the *k*‑th chest), you **must** compute its address using pointer arithmetic on the base pointer returned by `malloc` (e.g., `basePtr + (k‑1)`). Direct array indexing (`chests[k]`) is **not allowed** for these accesses.  

7. **Output Formatting**  
   * For option 1, use `displayChest`.  
   * For option 2, print:  
     `Total weight: <value>` (value printed with two decimal places).  
   * For option 3, print the line `Heaviest chest:` followed by the chest details using `displayChest`.  

8. **Cleanup**  
   * Before exiting, free the allocated memory.  

---

## Example  

**Input (entered by the user)**  
```
3
101
12.5
Golden Crown
102
8.3
Silver Sword
103
15.0
Emerald Statue
```

**Program Interaction**  
```
--- Treasure Chest Menu ---
1. Display chest by index
2. Show total weight
3. Show heaviest chest
0. EXIT
Enter option: 1
Enter chest index (1-3): 2
Chest ID: 102
Weight: 8.30 kg
Description: Silver Sword

--- Treasure Chest Menu ---
1. Display chest by index
2. Show total weight
3. Show heaviest chest
0. EXIT
Enter option: 2
Total weight: 35.80

--- Treasure Chest Menu ---
1. Display chest by index
2. Show total weight
3. Show heaviest chest
0. EXIT
Enter option: 3
Heaviest chest:
Chest ID: 103
Weight: 15.00 kg
Description: Emerald Statue

--- Treasure Chest Menu ---
1. Display chest by index
2. Show total weight
3. Show heaviest chest
0. EXIT
Enter option: 0
Goodbye!
```

---

### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Chest`.  
* **Function Requirement** – The logic for displaying the details of ONE specific chest must be placed in a function named `displayChest`.  
* **Pointer‑Arithmetic Requirement** – Access to individual chests must be performed with pointer arithmetic; array‑style indexing (`chests[i]`) is prohibited for those accesses.  
* **Menu Requirement** – The menu must include an explicit option `0` (or the word `EXIT`) that terminates the program.  
* **Function Count** – Apart from `main`, you may implement **at most two** additional functions (one of them is `displayChest`).  

Write the program in standard C (C99 or later).

---

## Problem 82 - openai/gpt-oss-120b - Iteration 32
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is modernising its bus‑stop information system. Each bus stop is identified by a unique integer ID, stores the name of the stop (a short string), and keeps a **dynamic** array of the next three arrival times (in minutes) for the buses that serve that stop.  

Your task is to write a small C program that lets a user **add**, **view**, and **remove** bus‑stop records using only pointer arithmetic (no array indexing `[]`). The program should manage the memory for the dynamic array of arrival times manually, demonstrating correct use of pointers, `malloc`/`free`, and pointer arithmetic.

## Requirements  

1. **Data representation**  
   * Define a `struct BusStop` that contains:  
     - `int id;`                // unique identifier  
     - `char name[31];`         // stop name (max 30 characters + null terminator)  
     - `int *times;`            // pointer to a dynamically allocated array of three `int` values  

2. **Program functionality** (menu‑driven)  
   * **(1) Add a new bus stop**  
     - Prompt for `id`, `name`, and three arrival times.  
     - Allocate memory for the `times` array using `malloc`.  
     - Store the new `BusStop` in a **linked list** that is built using pointers only (no array of structs).  
   * **(2) Display a bus stop**  
     - Prompt for an `id`.  
     - Locate the matching `BusStop` in the list.  
     - Call a function `void displayStop(const struct BusStop *s);` that prints the stop’s details (id, name, and the three times).  
   * **(3) Delete a bus stop**  
     - Prompt for an `id`.  
     - Remove the corresponding node from the linked list, free the `times` array, and free the node itself.  
   * **(4) List all bus stops**  
     - Traverse the linked list and display each stop using `displayStop`.  
   * **(5) EXIT** – terminate the program, freeing all remaining allocated memory.  

3. **Implementation rules**  
   * **All array accesses must be performed with pointer arithmetic** (e.g., `*(ptr + i)`), never with the subscript operator `[]`.  
   * The linked list must be built manually using `struct Node { struct BusStop data; struct Node *next; };`.  
   * The program must not leak memory; all allocated memory must be released before termination.  

## Example Interaction  

```
=== Bus‑Stop Manager ===
1) Add a bus stop
2) Display a bus stop
3) Delete a bus stop
4) List all bus stops
5) EXIT
Choose an option: 1

Enter stop ID: 101
Enter stop name: Main Street
Enter arrival time #1 (minutes): 5
Enter arrival time #2 (minutes): 12
Enter arrival time #3 (minutes): 19
Bus stop added.

=== Bus‑Stop Manager ===
1) Add a bus stop
2) Display a bus stop
3) Delete a bus stop
4) List all bus stops
5) EXIT
Choose an option: 2

Enter stop ID to display: 101
--- Bus Stop 101 ---
Name : Main Street
Next arrivals (min): 5 12 19

=== Bus‑Stop Manager ===
1) Add a bus stop
2) Display a bus stop
3) Delete a bus stop
4) List all bus stops
5) EXIT
Choose an option: 4

--- Bus Stop 101 ---
Name : Main Street
Next arrivals (min): 5 12 19

=== Bus‑Stop Manager ===
1) Add a bus stop
2) Display a bus stop
3) Delete a bus stop
4) List all bus stops
5) EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct BusStop` as described.  
* **Display Function** – The logic for printing the details of a single bus stop **must** be placed in a function named `void displayStop(const struct BusStop *s);`.  
* **Pointer‑Only Access** – All accesses to the `times` array and to the linked‑list nodes must use pointer arithmetic; the `[]` operator is prohibited for those structures.  
* **Menu Exit Option** – The menu must contain an explicit option (number **5**) labelled **EXIT** that ends the program.  
* **Memory Management** – No memory leaks are allowed; every `malloc`/`calloc` must have a matching `free` before program termination.  

---

## Problem 83 - openai/gpt-oss-120b - Iteration 33
# STEP 1: PROBLEM  

## Background  
You have been hired by **EcoTrack**, a small startup that monitors the health of a garden using a network of sensor nodes. Each sensor node records three measurements: **soil moisture**, **temperature**, and **light intensity**. The data from each node is stored in an array of `Sensor` structures. Your task is to write a program that lets a user explore the collected data using only pointer arithmetic—no array indexing (`[]`) is allowed.

## Requirements  
1. **Data Structure**  
   - Define a `struct Sensor` that contains three `float` members: `moisture`, `temperature`, and `light`.  

2. **Data Initialization**  
   - In `main`, create an array of **5** `Sensor` objects and initialize them with the following values (in the given order):  
     1. 23.5, 18.2, 350.0  
     2. 30.1, 19.0, 400.5  
     3. 18.7, 17.5, 280.3  
     4. 25.0, 20.1, 500.0  
     5. 22.3, 18.8, 320.7  

3. **Menu‑Driven Interface** (optional but encouraged)  
   - Present a menu that repeats until the user chooses to exit. The menu must include the following options:  
     1. **Display all sensor readings** – print each sensor’s three measurements on a separate line.  
     2. **Display a single sensor** – prompt the user for a sensor index (1‑5) and show that sensor’s data.  
     3. **Update a sensor** – prompt for an index (1‑5) and new values for moisture, temperature, and light, then store them.  
     4. **Exit** – terminate the program. (The exit option must be clearly numbered, e.g., “4. Exit”.)  

4. **Pointer Arithmetic Only**  
   - All accesses to the sensor array must be performed using pointers and pointer arithmetic (`*`, `+`, `-`). The use of the subscript operator `[]` is prohibited for reading or writing sensor data.  

5. **Helper Function**  
   - Implement a function `void displaySensor(const Sensor *p)` that receives a pointer to a `Sensor` and prints its three fields in the format:  
     `Moisture: <value>  Temperature: <value>  Light: <value>`  

6. **Input Validation**  
   - If the user enters an index outside the range 1‑5, display an error message and return to the menu without crashing.  

## Example Input/Output  

```
--- EcoTrack Sensor Menu ---
1. Display all sensor readings
2. Display a single sensor
3. Update a sensor
4. Exit
Choose an option: 1

Sensor 1: Moisture: 23.5  Temperature: 18.2  Light: 350.0
Sensor 2: Moisture: 30.1  Temperature: 19.0  Light: 400.5
Sensor 3: Moisture: 18.7  Temperature: 17.5  Light: 280.3
Sensor 4: Moisture: 25.0  Temperature: 20.1  Light: 500.0
Sensor 5: Moisture: 22.3  Temperature: 18.8  Light: 320.7

--- EcoTrack Sensor Menu ---
1. Display all sensor readings
2. Display a single sensor
3. Update a sensor
4. Exit
Choose an option: 2
Enter sensor number (1‑5): 3
Sensor 3: Moisture: 18.7  Temperature: 17.5  Light: 280.3

--- EcoTrack Sensor Menu ---
1. Display all sensor readings
2. Display a single sensor
3. Update a sensor
4. Exit
Choose an option: 3
Enter sensor number (1‑5): 4
Enter new moisture: 26.2
Enter new temperature: 21.0
Enter new light: 510.5
Sensor 4 updated.

--- EcoTrack Sensor Menu ---
1. Display all sensor readings
2. Display a single sensor
3. Update a sensor
4. Exit
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  
- **Struct Requirement** – The primary data entity must be represented by a `struct Sensor`.  
- **Function Requirement** – The logic for displaying the details of ONE specific sensor must be encapsulated in a function named `displaySensor`.  
- **Pointer‑Only Access** – All reads and writes to the sensor array must use pointer arithmetic; the `[]` operator is not allowed for those operations.  
- **Menu Exit Option** – If a menu is provided, it must contain a clearly numbered option (e.g., “4. Exit”) that terminates the program.  

---

## Problem 84 - openai/gpt-oss-120b - Iteration 34
# STEP 1: PROBLEM  

## Background  
The city’s public‑transport authority is upgrading its fleet of electric scooters. Each scooter is identified by a unique serial number, stores its current battery level (percentage), and records the mileage it has travelled. The maintenance team wants a small console program that lets them **add**, **view**, **update**, and **remove** scooter records while practicing pointer arithmetic.

## Requirements  

1. **Data Representation**  
   * Define a `struct Scooter` containing:  
     * `int id;`               – unique serial number (positive integer)  
     * `float battery;`        – battery level as a percentage (0.0 – 100.0)  
     * `float mileage;`        – total kilometres travelled  

2. **Dynamic Storage**  
   * The program must allocate an array of `Scooter` objects on the **heap** using `malloc` (or `new` in C++).  
   * The array size can grow or shrink as scooters are added or removed.  
   * All navigation through the array **must use pointer arithmetic** (e.g., `*(scooters + i)`) – indexing (`scooters[i]`) is not allowed.

3. **Menu‑driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Action |
   |--------|--------|
   | 1 | **Add a scooter** – ask for `id`, `battery`, `mileage`; store it at the end of the array. |
   | 2 | **Display a scooter** – ask for an `id` and print the matching scooter’s details. The display logic must be in a function called `displayScooter`. |
   | 3 | **Update battery** – ask for an `id` and a new battery percentage; modify the corresponding record. |
   | 4 | **Remove a scooter** – ask for an `id`; delete that record and shift the remaining elements to keep the array contiguous. |
   | 5 | **List all scooters** – print every scooter in the order they are stored. |
   | 0 | **EXIT** – terminate the program, freeing all allocated memory. |

4. **Input validation** – If the user requests an operation on an `id` that does not exist, print an informative message and return to the menu.

5. **Memory management** – Every time the array size changes, reallocate it appropriately; on program termination, free the memory.

## Example Interaction  

```
=== Scooter Management System ===
1) Add scooter
2) Display scooter
3) Update battery
4) Remove scooter
5) List all scooters
0) EXIT
Choose an option: 1
Enter ID: 101
Enter battery (%): 78.5
Enter mileage (km): 1200.0
Scooter added.

Choose an option: 1
Enter ID: 202
Enter battery (%): 55.0
Enter mileage (km): 850.2
Scooter added.

Choose an option: 5
ID: 101 | Battery: 78.5% | Mileage: 1200.00 km
ID: 202 | Battery: 55.0% | Mileage: 850.20 km

Choose an option: 2
Enter ID to display: 202
ID: 202 | Battery: 55.0% | Mileage: 850.20 km

Choose an option: 3
Enter ID to update battery: 101
Enter new battery (%): 90
Battery updated.

Choose an option: 4
Enter ID to remove: 202
Scooter removed.

Choose an option: 5
ID: 101 | Battery: 90.0% | Mileage: 1200.00 km

Choose an option: 0
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented by the `struct Scooter`.  
* **Display function** – The logic that prints a single scooter’s details must be placed in a function named `displayScooter` with the prototype `void displayScooter(const Scooter *s);`.  
* **Pointer arithmetic only** – Access to the dynamic array must be performed exclusively with pointers and pointer arithmetic; array‑index notation (`scooters[i]`) is prohibited.  
* **Menu requirement** – The program must implement the menu shown above, and **option 0 must be the explicit EXIT command**.  
* **Single‑function restriction** – Apart from `main` and the required `displayScooter`, no other helper functions are allowed (all other logic must be written directly inside `main`).  

Design and implement the program adhering to these specifications.

---

## Problem 85 - openai/gpt-oss-120b - Iteration 35
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Campus IT Department** to write a tiny “Student Registry” utility that runs in a terminal. The registry will keep a short list of students in memory while the program is running. Because the department wants to demonstrate low‑level memory handling to new interns, **all access to the student records must be performed with pointers and pointer arithmetic** – no array‑index syntax (`students[i]`) is allowed.

## Program Requirements  

1. **Data Representation**  
   * Define a `struct` named `Student` containing three fields:  
     * `char name[31];`   – the student’s name (max 30 characters, plus the terminating `'\0'`).  
     * `int  age;`        – the student’s age.  
     * `float gpa;`       – the student’s grade point average.  

2. **Dynamic Storage**  
   * At program start, allocate memory for **up to 20** `Student` objects using `malloc`.  
   * Keep a separate integer variable that tracks how many students have actually been stored.

3. **Menu‑Driven Interface** (the program must present a menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | **1**  | **Add a new student** – prompt for name, age, and GPA, store the data in the next free slot. If the list is already full, display an error message. |
   | **2**  | **Display a student by index** – ask for an index (0‑based). If the index is valid, call the function `displayStudent` (see Constraints) to print that student’s details; otherwise print “Invalid index”. |
   | **3**  | **List all students** – iterate through the array using only pointers and pointer arithmetic, printing each student’s data on its own line. |
   | **4**  | **Exit** – terminate the program gracefully, freeing any allocated memory. |

4. **Input / Output**  
   * All prompts and messages should be clear and user‑friendly.  
   * When displaying a student, use the exact format:  

     ```
     Name: <name>, Age: <age>, GPA: <gpa>
     ```

5. **Error Handling**  
   * If the user selects an undefined menu option, print “Unknown option, please try again.” and redisplay the menu.  
   * When reading numeric values, assume the user enters a valid integer or float (no need for robust validation beyond range checks for the index).

## Simple Example  

```
--- Student Registry ---
1) Add a new student
2) Display a student by index
3) List all students
4) Exit
Choose an option: 1
Enter name: Alice
Enter age: 20
Enter GPA: 3.7
Student added.

--- Student Registry ---
1) Add a new student
2) Display a student by index
3) List all students
4) Exit
Choose an option: 1
Enter name: Bob
Enter age: 22
Enter GPA: 3.4
Student added.

--- Student Registry ---
1) Add a new student
2) Display a student by index
3) List all students
4) Exit
Choose an option: 3
Name: Alice, Age: 20, GPA: 3.70
Name: Bob, Age: 22, GPA: 3.40

--- Student Registry ---
1) Add a new student
2) Display a student by index
3) List all students
4) Exit
Choose an option: 2
Enter index (0‑based): 0
Name: Alice, Age: 20, GPA: 3.70

--- Student Registry ---
1) Add a new student
2) Display a student by index
3) List all students
4) Exit
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Student` as described above.  
* **Display Function** – The logic for showing the details of **one** specific student must be placed in a function with the exact prototype:  

  ```c
  void displayStudent(const Student *p);
  ```

  The function receives a pointer to a `Student` and prints the student using the format shown in the example.  

* **Pointer‑Only Traversal** – When iterating over the array (e.g., for options 3 and 2), you **must not** use the subscript operator (`[]`). Access each element solely with pointer arithmetic (`*(ptr + i)` or `ptr[i]` is prohibited).  

* **Single‑Function Aside from `main`** – Apart from `main`, you may only create the following additional functions:  
  * `void displayStudent(const Student *p);` (required)  
  * Any helper you deem necessary **must be declared as `static`** and placed in the same source file. No separate compilation units are allowed.  

* **Menu Exit Option** – The menu **must** include option **4** (or the keyword “EXIT”) that terminates the program, as shown in the example.  

* **Memory Management** – All dynamically allocated memory must be freed before the program exits.  

* **Compilation** – The program must compile without warnings using the command  

  ```bash
  gcc -Wall -Wextra -std=c11 student_registry.c -o student_registry
  ```

---  

Design the problem so that students practice declaring structs, allocating memory, passing pointers to functions, and using pointer arithmetic to navigate an array of structures.

---

## Problem 86 - openai/gpt-oss-120b - Iteration 36
# STEP 1: PROBLEM  

## Background  
The campus library is upgrading its inventory system. Every book in the collection is stored in an array of **`struct Book`** objects. The library wants a small console program that can **add**, **search**, and **list** books by directly manipulating the array with pointers and pointer arithmetic – no index‑based subscripting allowed inside the core logic.  

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` containing:  
     * `char title[51];`   // up to 50 characters + null terminator  
     * `char author[31];`  // up to 30 characters + null terminator  
     * `int  year;`  

2. **Program Functionality**  
   The program must present a text menu with the following options:  
   1. **Add a new book** – Prompt the user for title, author, and year, then store the new book at the next free position in the array.  
   2. **Search by title** – Ask for a title string, locate the first book whose title matches exactly, and display its details.  
   3. **List all books** – Display the details of every stored book in the order they were entered.  
   4. **Exit** – Terminate the program.  

   *The search and list operations must be implemented **using only pointers** (e.g., `Book *p = books; p < books + count; ++p`). No array indexing (`books[i]`) is allowed inside those functions.*  

3. **Functions**  
   * `void displayBook(const Book *b);` – prints the title, author, and year of the book pointed to by `b`. This function must be used for both the search result and the list operation.  
   * Any additional helper functions are allowed, but the core pointer arithmetic must reside in the search and list routines.  

4. **Capacity**  
   * The array can hold a maximum of **100** books. If the user attempts to add more, display an error message and return to the menu.  

5. **User Interaction** – All prompts and messages should be clear and user‑friendly.  

## Example Input / Output  

```
=== Library Inventory ===
1) Add a new book
2) Search by title
3) List all books
4) Exit
Choose an option: 1

Enter title : The C Programming Language
Enter author: Brian Kernighan and Dennis Ritchie
Enter year  : 1978
Book added successfully!

=== Library Inventory ===
1) Add a new book
2) Search by title
3) List all books
4) Exit
Choose an option: 1

Enter title : Clean Code
Enter author: Robert C. Martin
Enter year  : 2008
Book added successfully!

=== Library Inventory ===
1) Add a new book
2) Search by title
3) List all books
4) Exit
Choose an option: 2

Enter title to search: Clean Code
--- Book Found ---
Title : Clean Code
Author: Robert C. Martin
Year  : 2008

=== Library Inventory ===
1) Add a new book
2) Search by title
3) List all books
4) Exit
Choose an option: 3

--- Book List ---
Title : The C Programming Language
Author: Brian Kernighan and Dennis Ritchie
Year  : 1978

Title : Clean Code
Author: Robert C. Martin
Year  : 2008

=== Library Inventory ===
1) Add a new book
2) Search by title
3) List all books
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Book`.  
* **Display Function** – The logic for displaying the details of **ONE** specific book must be in a function named `displayBook`.  
* **Pointer‑Only Traversal** – Inside the search and list functionalities, you **must not** use array indexing (`books[i]`). Use pointer arithmetic (`*p`, `p++`, `p + n`, etc.) instead.  
* **Menu Exit Option** – The menu must include option **4** (or the keyword `Exit`) that cleanly terminates the program.  

*Optional*: You may add additional helper functions, but the above constraints are mandatory.

---

## Problem 87 - openai/gpt-oss-120b - Iteration 37
# STEP 1: PROBLEM  

## Background  
The archaeology department of **Nova University** has just uncovered a cache of ancient treasure chests. Each chest is described by three pieces of information:  

* **ID** – a unique integer identifier.  
* **Weight** – the weight of the chest in kilograms (a `float`).  
* **Material** – a short string (max 20 characters) describing the material of the chest (e.g., “gold”, “bronze”, “silver”).  

You have been asked to write a small C program that stores information about up to **10** chests, lets the user add new chests, view the details of a specific chest, and list all stored chests. The program must make heavy use of **pointers** and **pointer arithmetic** to manipulate the collection of chests.

---

## Requirements  

1. **Data Representation**  
   * Define a `struct Chest` containing the three fields described above.  

2. **Storage**  
   * Allocate a static array of 10 `struct Chest` objects.  
   * Use a pointer (`struct Chest *`) to refer to the first element of the array and **only** pointer arithmetic (e.g., `ptr + i`) to access individual elements. Direct array indexing (`chests[i]`) is **not** allowed.  

3. **Menu‑Driven Interface** (displayed repeatedly until the user chooses to exit)  
   * **1. Add a new chest** – Prompt for ID, weight, and material, then store the chest in the first free slot. If the array is full, display an appropriate message.  
   * **2. Display a chest by ID** – Prompt for an ID, locate the chest with that ID using pointer arithmetic, and call a function `displayChest` (see constraints) to print its details. If no chest with the given ID exists, inform the user.  
   * **3. List all chests** – Traverse the entire array with pointer arithmetic and print the details of every stored chest.  
   * **4. EXIT** – Terminates the program.  

4. **Input Validation**  
   * IDs must be positive integers and unique.  
   * Weight must be a positive floating‑point number.  
   * Material must be a non‑empty string not exceeding 20 characters.  

5. **Program Output**  
   * All output should be clear and user‑friendly, indicating what the program expects and what it is doing.

---

## Example Interaction  

```
=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest by ID
3. List all chests
4. EXIT
Choose an option: 1

Enter Chest ID: 101
Enter Weight (kg): 12.5
Enter Material (max 20 chars): gold
Chest added successfully!

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest by ID
3. List all chests
4. EXIT
Choose an option: 1

Enter Chest ID: 202
Enter Weight (kg): 8.3
Enter Material (max 20 chars): bronze
Chest added successfully!

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest by ID
3. List all chests
4. EXIT
Choose an option: 2

Enter Chest ID to display: 101
--- Chest Details ---
ID: 101
Weight: 12.50 kg
Material: gold

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest by ID
3. List all chests
4. EXIT
Choose an option: 3

--- All Stored Chests ---
ID: 101, Weight: 12.50 kg, Material: gold
ID: 202, Weight: 8.30 kg, Material: bronze

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest by ID
3. List all chests
4. EXIT
Choose an option: 4

Goodbye!
```

---

### CONSTRAINTS  

1. **Struct Usage** – The primary data entity **must** be represented by a `struct Chest`.  
2. **Display Function** – The logic for printing the details of a single chest **must** be placed in a function with the exact prototype:  

   ```c
   void displayChest(const struct Chest *c);
   ```  

3. **Pointer Arithmetic Only** – Access to the chest array **must** be performed exclusively via a pointer and pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.). Direct array indexing (`chests[i]`) is prohibited.  
4. **Menu Requirement** – The program must present a menu as described above, and **option 4 must be the EXIT choice**.  
5. **Single‑File Implementation** – All code (including `struct` definition, `displayChest`, `main`, and any helper functions) must reside in a single source file.  
6. **No Global Variables** – Apart from the static chest array, all other variables must be defined inside functions.  

*Optional extra challenge (not required for credit):* implement dynamic memory allocation for the chest array and resize it when the user attempts to add more than the current capacity.

---

## Problem 88 - openai/gpt-oss-120b - Iteration 38
# STEP 1: PROBLEM  

## Background  
You have been hired by **EcoTrack**, a small startup that monitors the health of trees in an urban park. Each tree is identified by a unique ID, its species name, and the current height (in centimeters). The park’s maintenance software stores an array of tree records and frequently needs to retrieve or update information about a single tree based on its ID.  

Your task is to write a C program that manages a **fixed‑size collection** of trees using pointers and pointer arithmetic. The program must demonstrate correct use of `struct`, pointer dereferencing, and pointer indexing without resorting to array‑style subscripting (`[]`) for the main data manipulation.

## Requirements  

1. **Data Representation**  
   - Define a `struct Tree` containing:  
     ```c
     int id;               // unique identifier (positive integer)
     char species[31];     // null‑terminated string, max 30 characters
     int height_cm;        // current height in centimeters
     ```  
   - Declare an array of **10** `struct Tree` objects in `main`.  

2. **Menu‑Driven Interface** (the program must present a menu repeatedly until the user chooses to exit)  
   - **1. Add / Update a tree** – Prompt for `id`, `species`, and `height_cm`.  
     - If a tree with the given `id` already exists, update its `species` and `height_cm`.  
     - If the `id` is new and there is still free space, store it in the first unused slot.  
   - **2. Display a tree** – Prompt for an `id` and print the tree’s details using the required function `displayTree`.  
   - **3. List all trees** – Print the details of every stored tree in the order they appear in memory.  
   - **4. EXIT** – Terminate the program.  

3. **Pointer Arithmetic**  
   - All accesses to the tree array **must** be performed with pointers (`Tree *p = trees;`) and pointer arithmetic (`p + i`, `*(p + i)`, etc.).  
   - Do **not** use the subscript operator `[]` for reading or writing tree fields, except when initializing the `species` string with `scanf("%30s", ...)` (which is acceptable).  

4. **Function Requirements**  
   - Implement a function `void displayTree(const struct Tree *t)` that prints a single tree in the format:  
     ```
     ID: <id>, Species: <species>, Height: <height_cm> cm
     ```  
   - This function must be the **only** place where a tree’s fields are printed.  

5. **Error Handling**  
   - If the user tries to add a tree when the array is full, print:  
     ```
     Error: Tree storage is full.
     ```  
   - If the user requests to display a tree that does not exist, print:  
     ```
     Error: No tree with ID <id> found.
     ```

## Example Input / Output  

```
=== EcoTrack Tree Manager ===
1. Add / Update a tree
2. Display a tree
3. List all trees
4. EXIT
Choose an option: 1
Enter tree ID: 101
Enter species (max 30 chars): Oak
Enter height (cm): 550
Tree added/updated successfully.

=== EcoTrack Tree Manager ===
1. Add / Update a tree
2. Display a tree
3. List all trees
4. EXIT
Choose an option: 1
Enter tree ID: 202
Enter species (max 30 chars): Maple
Enter height (cm): 430
Tree added/updated successfully.

=== EcoTrack Tree Manager ===
1. Add / Update a tree
2. Display a tree
3. List all trees
4. EXIT
Choose an option: 2
Enter tree ID to display: 101
ID: 101, Species: Oak, Height: 550 cm

=== EcoTrack Tree Manager ===
1. Add / Update a tree
2. Display a tree
3. List all trees
4. EXIT
Choose an option: 3
ID: 101, Species: Oak, Height: 550 cm
ID: 202, Species: Maple, Height: 430 cm

=== EcoTrack Tree Manager ===
1. Add / Update a tree
2. Display a tree
3. List all trees
4. EXIT
Choose an option: 4
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Usage:** The primary data entity must be represented by a `struct Tree`.  
- **Function Requirement:** The details of ONE specific tree must be displayed by a function named `displayTree`. No other function may print tree information.  
- **Pointer Arithmetic Only:** All manipulations of the tree array inside `main` (searching, adding, listing) must use pointers and pointer arithmetic; the `[]` operator is prohibited for these operations.  
- **Menu Exit Option:** The menu must include a distinct option (`4` in the example) labeled **EXIT** that terminates the program.  

*Feel free to add any auxiliary helper functions you deem necessary, provided the above constraints are respected.*

---

## Problem 89 - openai/gpt-oss-120b - Iteration 39
# STEP 1: PROBLEM  

## Background  
The university’s campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, an author, and a count of how many copies are currently on the shelf. The library staff wants a tiny command‑line utility written in C that lets them **add**, **search**, **remove**, and **list** books using only pointer arithmetic (no array indexing `[]`).  

## Requirements  

Your program must:

1. **Define a `struct Book`** that stores  
   - `char isbn[14]`   (13‑digit ISBN plus terminating `'\0'`)  
   - `char title[51]`  (max 50 characters + `'\0'`)  
   - `char author[31]` (max 30 characters + `'\0'`)  
   - `int copies`      (number of copies on the shelf)  

2. **Maintain a dynamically allocated array of `struct Book`**.  
   - The array starts empty.  
   - When a new book is added, the array grows with `realloc`.  

3. **Present a text menu** (shown repeatedly until the user chooses to exit) with the following options:  

   | Option | Description |
   |--------|-------------|
   | 1      | Add a new book |
   | 2      | Search for a book by ISBN and display its details |
   | 3      | Remove a book by ISBN (decrease `copies` by 1; if `copies` becomes 0, delete the record and shrink the array) |
   | 4      | List all books in the order they are stored |
   | 5      | **EXIT** the program |

4. **All traversals of the book array must use pointer arithmetic only** (e.g., `ptr = books; ptr < books + count; ++ptr`). Direct indexing (`books[i]`) is **not allowed**.

5. **The logic that prints the details of a single book** (ISBN, title, author, copies) **must be placed in a function named `displayBook`** that receives a pointer to a `struct Book`.

6. The program should gracefully handle invalid input (e.g., searching for a non‑existent ISBN) by printing an informative message and returning to the menu.

## Example Interaction  

```
--- Library Inventory Menu ---
1) Add a new book
2) Search by ISBN
3) Remove a copy
4) List all books
5) EXIT
Enter choice: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter number of copies: 3
Book added successfully!

--- Library Inventory Menu ---
1) Add a new book
2) Search by ISBN
3) Remove a copy
4) List all books
5) EXIT
Enter choice: 2

Enter ISBN to search: 9780131103627
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 3

--- Library Inventory Menu ---
1) Add a new book
2) Search by ISBN
3) Remove a copy
4) List all books
5) EXIT
Enter choice: 4

Listing all books (2 records):
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie
Copies: 3

ISBN: 9780201633610
Title: Design Patterns
Author: Gamma et al.
Copies: 1

--- Library Inventory Menu ---
1) Add a new book
2) Search by ISBN
3) Remove a copy
4) List all books
5) EXIT
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement:** The primary data entity must be represented by a `struct Book`.  
- **Function Requirement:** The routine that displays a single book’s details **must be named `displayBook`** and accept a `struct Book *` parameter. No other function may directly print book fields.  
- **Pointer‑Only Traversal:** All loops that walk through the dynamic array must use pointer arithmetic; the `[]` subscript operator is prohibited for array access.  
- **Menu Exit Option:** The menu must include option **5 – EXIT** (or the exact keyword “EXIT”) that terminates the program.  

*Note: You may create additional helper functions, but the core display logic must remain in `displayBook` and the array must always be accessed via pointers.*

---

## Problem 90 - openai/gpt-oss-120b - Iteration 40
# STEP 1: PROBLEM  

## Background  
You have been hired by the **Archaeology Exploration Agency (AEA)** to write a small utility that keeps track of discovered ancient treasure chests during an excavation. Each chest has a unique identifier, a weight (in kilograms), and a flag indicating whether it has been opened. The field team will input data for up to **10** chests, and later they need to query the information stored for any particular chest.  

Because the program will run on a low‑level embedded device used in the field, you must manage the collection of chests with raw pointers and pointer arithmetic rather than higher‑level containers.

## Requirements  
Write a C program that fulfills the following:

1. **Data Representation**  
   * Define a `struct Chest` containing:  
     - `int id;`                // unique identifier (positive integer)  
     - `float weight;`          // weight in kilograms (positive)  
     - `int opened;`            // 0 = closed, 1 = opened  

2. **Storage**  
   * Allocate an array of **10** `struct Chest` objects **statically** (i.e., on the stack).  
   * Use a pointer (`struct Chest *p`) to refer to the first element of the array and access other elements **exclusively** with pointer arithmetic (`p + i`, `*(p + i)`, etc.). Do **not** use the subscript operator `[]` anywhere in the program except in the `printf` format strings.

3. **Menu‑Driven Interface** (the program must present a menu; see mandatory constraint below)  
   * **1 – Add a new chest**  
     - Prompt for `id`, `weight`, and initial `opened` status (0 or 1).  
     - Store the data in the first free slot of the array. If the array is full, display an error message.  
   * **2 – Display a chest**  
     - Prompt for the chest `id`.  
     - Locate the chest with that `id` using pointer arithmetic.  
     - Call a function `void displayChest(const struct Chest *c)` that prints the chest’s details in the format shown in the example.  
     - If no chest with the given `id` exists, print “Chest not found.”  
   * **3 – List all chests**  
     - Iterate over the array using pointer arithmetic and call `displayChest` for every occupied slot.  
   * **4 – Mark a chest as opened**  
     - Prompt for the chest `id`.  
     - Locate the chest and set its `opened` field to `1`.  
     - Confirm the action with a message.  
   * **5 – EXIT** – terminate the program.  

4. **Input Validation**  
   * All numeric inputs must be validated to be within the sensible ranges (e.g., `id > 0`, `weight > 0`).  
   * If the user enters an invalid menu option, display “Invalid choice, try again.” and re‑show the menu.

5. **Program Flow**  
   * The menu should repeat after each operation until the user selects the EXIT option.

## Example Input / Output  

```
=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 1

Enter chest id: 101
Enter weight (kg): 12.5
Is the chest already opened? (0 = no, 1 = yes): 0
Chest added successfully.

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 1

Enter chest id: 202
Enter weight (kg): 8.3
Is the chest already opened? (0 = no, 1 = yes): 1
Chest added successfully.

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 2

Enter chest id to display: 101
Chest ID: 101
Weight : 12.50 kg
Status : CLOSED

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 4

Enter chest id to mark as opened: 101
Chest 101 marked as opened.

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 3

Chest ID: 101
Weight : 12.50 kg
Status : OPENED

Chest ID: 202
Weight : 8.30 kg
Status : OPENED

=== Treasure Chest Manager ===
1. Add a new chest
2. Display a chest
3. List all chests
4. Mark a chest as opened
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct Chest`.  
2. **Function Requirement** – The logic for displaying the details of **ONE** specific chest must be placed in a function named `void displayChest(const struct Chest *c)`.  
3. **Pointer‑Only Access** – All accesses to the array of chests must be performed using a pointer and pointer arithmetic. The array‑subscript operator `[]` is prohibited outside of `printf` format strings.  
4. **Menu Exit Option** – Because a menu is used, the program **must** provide a distinct menu option (number **5**) labelled “EXIT” that cleanly terminates the program.  

*Optional extra credit*: Implement the “Mark a chest as opened” operation without using any additional helper functions (i.e., perform the pointer arithmetic directly inside `main`).  

---  

*Your task*: Write the full C source code that satisfies all of the above specifications. Remember to keep the code readable, comment the pointer‑arithmetic sections, and handle erroneous input gracefully.

---

## Problem 91 - openai/gpt-oss-120b - Iteration 41
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its inventory system. Each book in the collection is stored in an array of **`Book`** structures. The library wants a small console program that lets a librarian **add new books**, **list all books**, and **display the details of a single book** by its position in the array. Because the library’s database will eventually be huge, the assignment emphasizes the use of **pointers and pointer arithmetic** to navigate the array instead of the usual index notation.

## Requirements  

1. **Define a `struct Book`** containing the following fields:  
   * `char title[51];`   // up to 50 characters + null terminator  
   * `char author[51];`  
   * `int  year;`  

2. **Allocate an array** capable of holding up to **100** `Book` objects **statically** (i.e., `Book library[100];`).  

3. The program must present a **menu** with the following options (the exact numbers are required):  
   * `1` – Add a new book (prompt for title, author, and year).  
   * `2` – List all books currently stored (display index, title, author, year).  
   * `3` – Display the details of ONE specific book (ask for the index).  
   * `4` – EXIT the program.  

4. **Adding a book** should store the data in the next free slot of the array. If the array is full, display an appropriate message and return to the menu.  

5. **Listing books** must traverse the array **using a pointer** that is incremented with pointer arithmetic (`ptr = ptr + 1`) rather than using the subscript operator `[]`.  

6. **Displaying a single book** must be performed by a **function named `displayBook`** that receives a pointer to a `Book` and prints its fields in a readable format.  

7. The program should continue to show the menu after each operation until the user selects the **EXIT** option (`4`).  

8. Input validation:  
   * For menu selection, reject any number outside 1‑4 and re‑prompt.  
   * For the index in option 3, ensure it is within the range of currently stored books; otherwise, print an error and return to the menu.  

## Example Input / Output  

```
=== Library Inventory ===
1. Add a new book
2. List all books
3. Display a book by index
4. EXIT
Select an option: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Book added successfully!

=== Library Inventory ===
1. Add a new book
2. List all books
3. Display a book by index
4. EXIT
Select an option: 1

Enter title: Clean Code
Enter author: Robert C. Martin
Enter year: 2008
Book added successfully!

=== Library Inventory ===
1. Add a new book
2. List all books
3. Display a book by index
4. EXIT
Select an option: 2

Index  Title                         Author               Year
0      The C Programming Language    Kernighan & Ritchie  1978
1      Clean Code                     Robert C. Martin     2008

=== Library Inventory ===
1. Add a new book
2. List all books
3. Display a book by index
4. EXIT
Select an option: 3

Enter index of the book to display: 0
--- Book Details ---
Title : The C Programming Language
Author: Kernighan & Ritchie
Year  : 1978

=== Library Inventory ===
1. Add a new book
2. List all books
3. Display a book by index
4. EXIT
Select an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **`struct Book`** must be used to represent each book.  
* The traversal for listing books **must use pointer arithmetic**; direct array indexing (`library[i]`) is not allowed in that part of the code.  
* The logic for displaying the details of ONE specific book **must be encapsulated in a function named `displayBook`** with the prototype `void displayBook(const Book *b);`.  
* The program **must implement a menu** and **must include option `4` to EXIT the program** as shown above.  
* Apart from `main`, you may create additional helper functions, but the core requirements (adding, listing, displaying) should each be clearly separated.  

*Optional (for extra credit):* Dynamically allocate the array with `malloc` and release it before exiting, still using pointer arithmetic for traversal.  

---

## Problem 92 - openai/gpt-oss-120b - Iteration 42
# STEP 1: PROBLEM  

## Background  
The city’s “Smart‑Parcel” service uses a small fleet of autonomous delivery drones. Each drone stores a handful of telemetry values (ID, current battery level, and distance travelled). The control center needs a simple console program that can **add**, **remove**, **list**, and **query** drones while practicing pointer arithmetic.  

You have just finished the lecture on pointers, pointer arithmetic, and `struct`s in C. Write a program that manages the fleet in a **statically‑allocated array** of drones, using only pointer operations (no array indexing `[]`) to walk through the collection.

## Requirements  

1. **Data representation**  
   * Define a `struct Drone` containing:  
     - `int id;`                // unique identifier (positive)  
     - `float battery;`        // percentage (0.0 – 100.0)  
     - `float distance;`       // total kilometres travelled  

2. **Program functionality** (menu‑driven)  
   1. **Add a drone** – Prompt for `id`, `battery`, and `distance`.  
      - If the fleet is full (maximum 20 drones) display an error.  
      - If a drone with the same `id` already exists, display an error.  
   2. **Remove a drone** – Prompt for an `id`.  
      - If the drone exists, delete it by shifting the subsequent drones left using pointer arithmetic.  
      - If it does not exist, display an error.  
   3. **List all drones** – Print a table of every drone currently stored, in the order they appear in the array.  
   4. **Show details of a single drone** – Prompt for an `id` and display that drone’s data.  
   5. **Exit** – Terminate the program.  

3. **Implementation rules**  
   * The fleet must be stored in a **single static array**: `struct Drone fleet[20];`.  
   * All traversal of the array **must use pointers** (`Drone *p;` and pointer arithmetic). Direct indexing (`fleet[i]`) is **not allowed** except when the array is passed to a function as a pointer argument.  
   * The logic that prints the details of **one specific drone** must be placed in a function named  

     ```c
     void displayDrone(const struct Drone *d);
     ```  

   * Apart from `main()`, you may create additional helper functions, but the core pointer‑walking code should be isolated in its own function(s).  

## Example Input / Output  

```
=== Smart‑Parcel Drone Manager ===
1) Add a drone
2) Remove a drone
3) List all drones
4) Show drone details
5) Exit
Select option: 1
Enter Drone ID: 101
Enter Battery (%): 87.5
Enter Distance (km): 12.3
Drone added successfully.

1) Add a drone
2) Remove a drone
3) List all drones
4) Show drone details
5) Exit
Select option: 1
Enter Drone ID: 202
Enter Battery (%): 45.0
Enter Distance (km): 5.7
Drone added successfully.

1) Add a drone
2) Remove a drone
3) List all drones
4) Show drone details
5) Exit
Select option: 3
ID   Battery%   Distance(km)
101   87.50        12.30
202   45.00         5.70

1) Add a drone
2) Remove a drone
3) List all drones
4) Show drone details
5) Exit
Select option: 4
Enter Drone ID to view: 202
--- Drone 202 ---
Battery : 45.00%
Distance: 5.70 km

1) Add a drone
2) Remove a drone
3) List all drones
4) Show drone details
5) Exit
Select option: 5
Good‑bye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity **must** be a `struct Drone`.  
2. **Display function** – The details of a single drone must be printed by a function named `displayDrone`.  
3. **Pointer arithmetic only** – Inside the program (including any helper functions that walk the fleet) you **must not** use array subscript notation `[]`. Use a pointer (`Drone *p`) and increment/decrement it to move through the array.  
4. **Menu exit option** – The menu **must** contain an explicit option to EXIT the program (option 5 in the example). Selecting this option ends the program.  

*Feel free to add any additional helper functions you deem necessary, as long as the above constraints are respected.*

---

## Problem 93 - openai/gpt-oss-120b - Iteration 43
# STEP 1: PROBLEM  

## Background  
The university’s campus navigation system stores the locations of all campus buildings in a dynamically‑allocated array. Each building is represented by a `struct` containing its name, a short description, and its (x, y) coordinates on the campus map. The navigation program must allow a user to:

1. Load a list of buildings from a file.  
2. Browse the list, add new buildings, or delete an existing one.  
3. Find the building that is **closest** to a user‑provided coordinate using pointer arithmetic (i.e., by walking through the array with a pointer, not by using array indexing).  

The goal of the assignment is to practice dynamic memory management, `struct`s, and pointer arithmetic.

## Requirements  

Write a C program that implements the following functionality:

1. **Load Buildings**  
   - Prompt the user for a file name.  
   - The file contains one building per line in the format:  
     `name;description;x;y`  
     Example line: `Library;Main study area;12.5;8.3`  
   - Allocate a dynamic array of `struct Building` objects to hold all entries.  
   - Store the data read from the file into the array.

2. **Menu‑Driven Interface** (displayed after loading)  
   - **1. List all buildings** – print each building’s index, name, and coordinates.  
   - **2. Add a building** – ask for name, description, x, y; reallocate the array to accommodate the new entry.  
   - **3. Delete a building** – ask for the index of the building to remove; shift the remaining elements and shrink the array.  
   - **4. Find nearest building** – ask the user for a pair of coordinates (x₀, y₀) and display the building whose Euclidean distance to (x₀, y₀) is minimal. The search **must** be performed using pointer arithmetic (e.g., a `struct Building *p = array; p < array + count; ++p`).  
   - **5. EXIT** – terminate the program, freeing all allocated memory.  

3. **Display Function**  
   - Implement a function `void displayBuilding(const struct Building *b);` that prints a single building’s full details (name, description, coordinates). All menu options that need to show a building must call this function.

4. **Memory Management**  
   - All memory allocated with `malloc`/`realloc` must be released before program termination.

## Example Input / Output  

Assume the file *campus.txt* contains:

```
Library;Main study area;12.5;8.3
Gym;Fitness center;5.0;3.2
Cafeteria;Food services;9.1;11.4
```

Sample interaction (user input shown after `>`):

```
Enter the name of the building file: > campus.txt
Loaded 3 buildings.

--- Campus Navigation Menu ---
1. List all buildings
2. Add a building
3. Delete a building
4. Find nearest building
5. EXIT
Choose an option: > 1

[0] Library      (12.5, 8.3)
[1] Gym          (5.0, 3.2)
[2] Cafeteria    (9.1, 11.4)

--- Campus Navigation Menu ---
Choose an option: > 4
Enter your location (x y): > 6 4
Nearest building:
Name: Gym
Description: Fitness center
Coordinates: (5.0, 3.2)

--- Campus Navigation Menu ---
Choose an option: > 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be a `struct Building` with at least the following members:  
   ```c
   char name[64];
   char description[128];
   double x;
   double y;
   ```
2. **Display Function** – All printing of a single building’s details must be done through the function `displayBuilding`. No `printf` of a building’s fields may appear outside this function.  
3. **Pointer Arithmetic** – The search for the nearest building (menu option 4) must be implemented using pointer arithmetic only; array indexing (`array[i]`) is **not** allowed inside the search loop.  
4. **Menu Exit** – The menu must contain an explicit option labeled **5. EXIT** (or the keyword `EXIT`) that terminates the program.  

*The problem is intentionally designed for students who have just learned pointers, dynamic allocation, and basic struct usage.*

---

## Problem 94 - openai/gpt-oss-120b - Iteration 44
# STEP 1: PROBLEM  

## Background  
The Royal Archive stores a collection of ancient scrolls. Each scroll is described by three pieces of information:  

* **ID** – a unique integer identifier.  
* **Title** – a short string (max 30 characters).  
* **Pages** – the number of pages in the scroll.  

The archivist wants a small C program that can keep the scrolls in memory, allow the user to add new scrolls, list all stored scrolls, and look up a single scroll by its ID. Because the archivist is learning low‑level programming, the implementation must make explicit use of pointers and pointer arithmetic to traverse the collection.

## Requirements  

1. **Data Representation**  
   * Define a `struct Scroll` that holds the three fields described above.  

2. **Dynamic Storage**  
   * The program must allocate an array of `struct Scroll` dynamically (using `malloc` or `calloc`).  
   * The maximum number of scrolls is **20**.  

3. **Menu‑Driven Interface** (optional but recommended)  
   * Present a menu with the following options:  
     1. **Add a new scroll** – prompt for ID, Title, and Pages; store it at the next free position.  
     2. **List all scrolls** – display every stored scroll in the order they were added.  
     3. **Find a scroll by ID** – ask for an ID, locate the matching scroll, and display its details.  
     4. **Exit** – terminate the program.  

4. **Pointer Arithmetic**  
   * When iterating over the array (for listing or searching), you must use pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.) rather than array indexing (`arr[i]`).  

5. **Functions**  
   * Implement a function `void displayScroll(const struct Scroll *s);` that prints the details of a single scroll. This function must be used whenever a scroll’s information is shown (both in the list and in the search).  

6. **Input Validation**  
   * Do not allow more than 20 scrolls to be added; display an appropriate message if the user tries to exceed the limit.  
   * If a search is performed for an ID that does not exist, print “Scroll not found.”  

## Example  

```
--- Royal Archive Menu ---
1) Add a new scroll
2) List all scrolls
3) Find a scroll by ID
4) Exit
Choose an option: 1

Enter Scroll ID: 101
Enter Title: The Art of War
Enter number of pages: 120
Scroll added successfully!

--- Royal Archive Menu ---
1) Add a new scroll
2) List all scrolls
3) Find a scroll by ID
4) Exit
Choose an option: 1

Enter Scroll ID: 202
Enter Title: Chronicles of Narnia
Enter number of pages: 350
Scroll added successfully!

--- Royal Archive Menu ---
1) Add a new scroll
2) List all scrolls
3) Find a scroll by ID
4) Exit
Choose an option: 2

ID: 101 | Title: The Art of War | Pages: 120
ID: 202 | Title: Chronicles of Narnia | Pages: 350

--- Royal Archive Menu ---
1) Add a new scroll
2) List all scrolls
3) Find a scroll by ID
4) Exit
Choose an option: 3

Enter ID to search: 202
ID: 202 | Title: Chronicles of Narnia | Pages: 350

--- Royal Archive Menu ---
1) Add a new scroll
2) List all scrolls
3) Find a scroll by ID
4) Exit
Choose an option: 4

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity must be represented by a `struct Scroll`.  
* **Display Function** – The logic for displaying the details of ONE specific scroll must reside in a function named `displayScroll`.  
* **Pointer Arithmetic Only** – Traversal of the scroll array must be performed using pointer arithmetic; array‑subscript notation (`arr[i]`) is prohibited for those loops.  
* **Menu Exit Option** – If a menu is implemented, option **4** (or the keyword “Exit”) must be provided to terminate the program.  

*Optional*: The program may contain additional helper functions, but the only mandatory function besides `main` is `displayScroll`.

---

## Problem 95 - openai/gpt-oss-120b - Iteration 45
# STEP 1: PROBLEM  

## Background  
The interplanetary logistics company **StarShip Logistics** needs a tiny command‑line tool to keep track of the cargo ships that are currently docked at its orbital hub. Each ship is identified by a name (a short string) and the amount of fuel (in kilograms) remaining in its tanks. The engineers have just learned about pointers and pointer arithmetic and would like a program that stores the ships in a dynamically allocated array and manipulates that array using only pointers (no array indexing `[]`).

## Program Requirements  

1. **Data representation**  
   * Define a `struct Ship` that contains:  
     - `char name[31];`   // up to 30 characters + terminating null  
     - `int fuel;`        // fuel in kilograms  

2. **Dynamic storage**  
   * At program start, allocate memory for **up to 10** `Ship` objects using `malloc`.  
   * Use a pointer (`Ship *ships`) to refer to the first element of the array.  

3. **Menu‑driven interface** (the program must present a menu and loop until the user chooses to exit)  
   * **1 – Add a ship** – Prompt for the ship’s name and fuel, store the data in the next free slot.  
   * **2 – List all ships** – Traverse the array with pointer arithmetic and print the details of every ship that has been added.  
   * **3 – Show a ship** – Prompt for a ship index (starting at 0). Use a function `displayShip` (see below) to print the details of that single ship. If the index is out of range, display an error message.  
   * **4 – Exit** – Terminate the program gracefully, freeing any allocated memory.  

4. **Pointer arithmetic only**  
   * When iterating over the array (for listing or accessing a specific element), you must use pointer arithmetic (`ptr = ptr + 1`, `ptr + i`, etc.). **Do not use the subscript operator `[]` anywhere except when reading a string into `name`.**

5. **Error handling**  
   * If the user tries to add more than 10 ships, display “Maximum capacity reached.” and ignore the request.  
   * If the user selects an invalid menu option, display “Invalid choice, try again.”  

## Example Interaction  

```
--- StarShip Logistics ---
1. Add a ship
2. List all ships
3. Show a ship
4. Exit
Enter choice: 1
Enter ship name: Aurora
Enter fuel (kg): 1250
Ship added.

--- StarShip Logistics ---
1. Add a ship
2. List all ships
3. Show a ship
4. Exit
Enter choice: 1
Enter ship name: Nebula
Enter fuel (kg): 980
Ship added.

--- StarShip Logistics ---
1. Add a ship
2. List all ships
3. Show a ship
4. Exit
Enter choice: 2
Ship 0: Aurora, Fuel = 1250 kg
Ship 1: Nebula, Fuel = 980 kg

--- StarShip Logistics ---
1. Add a ship
2. List all ships
3. Show a ship
4. Exit
Enter choice: 3
Enter ship index: 0
Ship 0: Aurora, Fuel = 1250 kg

--- StarShip Logistics ---
1. Add a ship
2. List all ships
3. Show a ship
4. Exit
Enter choice: 4
Good‑bye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity must be represented with a `struct Ship`.  
* **Display function** – The logic for displaying the details of **ONE specific ship** must be placed in a function with the exact prototype:  

  ```c
  void displayShip(const Ship *p);
  ```

* **Menu exit option** – The menu must include a distinct option (number **4**) that exits the program.  

* **Pointer‑only traversal** – All traversals of the ship array must be performed using pointer arithmetic; the subscript operator `[]` is prohibited for accessing `Ship` elements.  

* **Single additional function** – Apart from `main` and the required `displayShip` function, no other user‑defined functions are necessary (but you may create helper functions if you wish, provided the above constraints are satisfied).  

---

## Problem 96 - openai/gpt-oss-120b - Iteration 46
# STEP 1: PROBLEM  

## Background  
The kingdom’s archivist keeps a **record of ancient treasure chests** discovered by explorers.  
Each chest is described by three pieces of information:

* `id` – a unique integer identifier  
* `weight` – the weight of the chest in kilograms (a `float`)  
* `value` – the monetary value of the chest in gold coins (an `int`)  

Your task is to write a small C program that stores a collection of these chests, lets the user query the data, and performs a few simple calculations. The program must make explicit use of **pointers and pointer arithmetic** to navigate the collection.

---

## Requirements  

1. **Data representation**  
   * Define a `struct Chest` that holds the three fields listed above.  

2. **Dynamic allocation**  
   * Prompt the user for the number of chests `N` (1 ≤ N ≤ 100).  
   * Allocate an array of `N` `Chest` structures on the **heap** using `malloc`.  

3. **Input**  
   * For each chest, read its `id`, `weight`, and `value` from standard input.  

4. **Menu‑driven interface** (the program must present a menu after the data are entered)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Display a chest** – ask for a chest `id` and print all its fields. |
   | 2      | **Average weight** – compute and print the average weight of all chests. |
   | 3      | **Total value** – compute and print the sum of the `value` fields. |
   | 4      | **Exit** – terminate the program. |

   * The menu must be displayed repeatedly until the user selects the **Exit** option.  

5. **Pointer arithmetic**  
   * All traversals of the chest array (searching, averaging, summing) must be performed with **pointer arithmetic only** (e.g., `ptr = base; ptr++;`) – no array‑indexing (`arr[i]`) is allowed.  

6. **Function requirement**  
   * The logic that prints the details of a single chest must be placed in a function with the exact prototype:  

     ```c
     void displayChest(const struct Chest *c);
     ```

7. **Cleanup**  
   * Before exiting, free any memory allocated with `malloc`.  

---

## Example Input / Output  

```
Enter number of chests: 3
Chest 1 – id weight value: 101 12.5 2500
Chest 2 – id weight value: 102 8.0 1800
Chest 3 – id weight value: 103 15.2 3200

--- MENU ---
1) Display a chest
2) Average weight
3) Total value
4) Exit
Choose an option: 1
Enter chest id: 102
Chest ID: 102
Weight : 8.00 kg
Value  : 1800 gold

--- MENU ---
1) Display a chest
2) Average weight
3) Total value
4) Exit
Choose an option: 2
Average weight of 3 chests: 11.90 kg

--- MENU ---
1) Display a chest
2) Average weight
3) Total value
4) Exit
Choose an option: 3
Total value of all chests: 7500 gold

--- MENU ---
1) Display a chest
2) Average weight
3) Total value
4) Exit
Choose an option: 4
Goodbye!
```

*Note*: The exact formatting of prompts is not graded, only that the required information appears and the program behaves as described.*

---

### CONSTRAINTS  

* **Struct usage** – the primary data entity must be a `struct Chest`.  
* **Function name** – the routine that prints a single chest’s details must be named `displayChest` and accept a pointer to `const struct Chest`.  
* **Pointer‑only traversal** – you may **not** use the subscript operator (`[]`) to access elements of the dynamically allocated array; use only pointer arithmetic.  
* **Menu exit** – option **4** (or the keyword “Exit”) must be provided and must terminate the program.  
* **Single additional function** – besides `main`, only `displayChest` may be defined; helper logic must be placed inside `main` or inside `displayChest`.  

---  

Write the program that satisfies all of the above. Good luck!

---

## Problem 97 - openai/gpt-oss-120b - Iteration 47
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by an ISBN, has a title, and stores the number of copies currently on the shelf. The library wants a small C program that lets a librarian **add**, **remove**, **search**, and **list** books using only pointer arithmetic (no array indexing `[]`). The program must demonstrate a solid grasp of pointers, pointer arithmetic, and dynamic memory management.

## Requirements  

1. **Data Representation**  
   * Define a `struct Book` that contains:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[101];` // up to 100 characters plus terminating null  
     - `int copies;`      // number of copies on the shelf  

2. **Dynamic Storage**  
   * The program must allocate a contiguous block of memory to hold up to **N** books, where **N** is entered by the user at program start.  
   * Use `malloc` (or `calloc`) once; **do not** re‑allocate or use a fixed‑size array.  

3. **Menu‑Driven Interface** (the menu must contain an explicit **EXIT** option)  
   * **1 – Add a Book** – Prompt for ISBN, title, and copies, then store the new book at the first unused slot.  
   * **2 – Remove a Book** – Prompt for an ISBN; if found, shift all subsequent books left (using pointer arithmetic) to fill the gap and decrement the logical count.  
   * **3 – Search by ISBN** – Prompt for an ISBN; if the book exists, call the required function `displayBook` (see Constraints) to print its details.  
   * **4 – List All Books** – Iterate through the stored books and print each one (reuse `displayBook`).  
   * **5 – EXIT** – Free all allocated memory and terminate the program.  

4. **Pointer Arithmetic Only**  
   * When traversing the collection (adding, searching, shifting, listing), **do not** use the subscript operator `[]`. All navigation must be performed with pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.).  

5. **Input Validation**  
   * The program should gracefully handle attempts to add a book when the storage is full, remove/search for a non‑existent ISBN, or enter invalid menu choices.  

## Example Interaction  

```
Enter maximum number of books to manage: 3

--- Library Menu ---
1) Add a Book
2) Remove a Book
3) Search by ISBN
4) List All Books
5) EXIT
Choice: 1
Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter copies: 4
Book added.

--- Library Menu ---
1) Add a Book
2) Remove a Book
3) Search by ISBN
4) List All Books
5) EXIT
Choice: 1
Enter ISBN: 9780201633610
Enter Title: Design Patterns
Enter copies: 2
Book added.

--- Library Menu ---
1) Add a Book
2) Remove a Book
3) Search by ISBN
4) List All Books
5) EXIT
Choice: 4
ISBN: 9780131103627 | Title: The C Programming Language | Copies: 4
ISBN: 9780201633610 | Title: Design Patterns | Copies: 2

--- Library Menu ---
1) Add a Book
2) Remove a Book
3) Search by ISBN
4) List All Books
5) EXIT
Choice: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described.  
2. **Display Function** – The logic for printing the details of **one** book **must** be placed in a function with the exact prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```  

   All menu options that show book information (search and list) must call `displayBook`.  
3. **Pointer‑Only Traversal** – Inside `main` (and any helper functions) you **may not** use the array subscript operator `[]`. Every access to a `Book` inside the dynamically allocated block must be performed via pointer arithmetic.  
4. **Single Additional Function** – Apart from `main` and `displayBook`, you may **not** create extra functions. (All menu handling, shifting, etc., must be written inside `main`.)  
5. **Menu Exit Option** – The menu must include an explicit option labeled **5) EXIT** (or the keyword `EXIT`) that terminates the program after freeing the allocated memory.  

---

## Problem 98 - openai/gpt-oss-120b - Iteration 48
# STEP 1: PROBLEM  

## Background  
The university’s **Campus Navigation System** stores the locations of all campus buildings in a dynamically allocated array. Each building is described by its name (a short string) and its distance in meters from the main gate. The system must allow a user to query, add, and remove buildings while demonstrating correct use of pointers, pointer arithmetic, and dynamic memory management.

## Requirements  

1. **Data Structure**  
   - Define a `struct Building` that contains:  
     ```c
     char name[32];   // building name (max 31 characters + '\0')
     int  distance;   // distance from the main gate in meters
     ```  

2. **Program Functionality**  
   - The program starts with **no buildings** stored.  
   - Present a **menu** that repeats until the user chooses to exit. The menu must contain the following options (the numbers are mandatory):  
     1. **Add a building** – Prompt for the building’s name and distance, then append it to the end of the dynamic array.  
     2. **Remove a building** – Prompt for the building’s name; if found, delete that entry and shift the remaining elements so that the array stays contiguous.  
     3. **Display a building** – Prompt for the building’s name; if found, call a function `displayBuilding` (see Constraint) to print its details.  
     4. **List all buildings** – Print the name and distance of every stored building in the order they were added.  
     5. **Exit** – Terminate the program.  

   - All dynamic memory allocation must be performed with `malloc`/`realloc` and freed appropriately before program termination.  

3. **Pointer Arithmetic**  
   - When accessing or shifting elements in the array, you **must** use pointer arithmetic (e.g., `*(array + i)`) rather than array indexing (`array[i]`).  

4. **Error Handling**  
   - If the user tries to remove or display a building that does not exist, print a friendly message and return to the menu.  
   - If memory allocation fails, print an error message and exit gracefully.  

## Example Interaction  

```
=== Campus Navigation System ===
1. Add a building
2. Remove a building
3. Display a building
4. List all buildings
5. Exit
Choose an option: 1
Enter building name: Library
Enter distance from main gate (m): 250
Building added.

1. Add a building
2. Remove a building
3. Display a building
4. List all buildings
5. Exit
Choose an option: 1
Enter building name: Gym
Enter distance from main gate (m): 180
Building added.

1. Add a building
2. Remove a building
3. Display a building
4. List all buildings
5. Exit
Choose an option: 3
Enter building name to display: Gym
--- Building Details ---
Name: Gym
Distance: 180 m

1. Add a building
2. Remove a building
3. Display a building
4. List all buildings
5. Exit
Choose an option: 4
--- All Buildings ---
1. Library – 250 m
2. Gym – 180 m

1. Add a building
2. Remove a building
3. Display a building
4. List all buildings
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented by a `struct Building` as described above.  
- **Display Function** – The logic for printing the details of **one specific building** must reside in a separate function with the exact prototype:  

  ```c
  void displayBuilding(const struct Building *b);
  ```  

- **Pointer‑Only Access** – Inside the main program (except inside `displayBuilding`), you may **not** use the `[]` subscript operator to access array elements; you must use pointer arithmetic.  
- **Menu Exit Option** – The menu must include option **5** (or the keyword `EXIT`) that terminates the program.  

These constraints are mandatory; solutions that violate any of them will be considered incomplete.

---

## Problem 99 - openai/gpt-oss-120b - Iteration 49
# STEP 1: PROBLEM  

## Background  
The campus library has just upgraded its inventory system. Each book in the collection is stored as a record that contains the book’s ISBN (a 13‑digit integer), the title (a short string), and the number of copies currently on the shelf. The library software must keep these records in a **contiguous array** allocated dynamically at runtime.  

Your task is to write a small C program that lets a user **search for a book by its ISBN** and then displays the details of that book. The search must be performed using **pointer arithmetic** (no array indexing `[]`).  

## Requirements  

1. **Data Structure**  
   - Define a `struct Book` that holds:  
     ```c
     long long isbn;   // 13‑digit ISBN
     char title[64];   // title, null‑terminated
     int copies;       // number of copies on the shelf
     ```  

2. **Dynamic Allocation**  
   - At program start, read an integer `n` (the number of books, 1 ≤ n ≤ 100).  
   - Dynamically allocate an array of `n` `struct Book` objects using `malloc`.  

3. **Input**  
   - For each of the `n` books, read three values on separate lines:  
     1. ISBN (as a 64‑bit integer)  
     2. Title (a line of text, may contain spaces)  
     3. Number of copies (integer)  

4. **Search**  
   - Prompt the user to enter an ISBN to look up.  
   - Scan the dynamically allocated array **using only pointer arithmetic** (i.e., increment a `struct Book *` pointer) to find a matching ISBN.  

5. **Output**  
   - If a matching book is found, call a function `displayBook` (see constraints) to print:  
     ```
     ISBN: <isbn>
     Title: <title>
     Copies: <copies>
     ```  
   - If no book matches, print:  
     ```
     Book not found.
     ```  

6. **Program Termination**  
   - After the search result is displayed, the program should end (no loop required).  

## Example  

**Input**  
```
3
9780306406157
The C Programming Language
5
9780131103627
Introduction to Algorithms
2
9780262033848
Artificial Intelligence: A Modern Approach
4
9780131103627
```

**Output**  
```
ISBN: 9780131103627
Title: Introduction to Algorithms
Copies: 2
```

(If the last line had been `1234567890123`, the output would be `Book not found.`)

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct Book`.  
2. **Display Function** – The logic for printing a book’s details **must be placed in a separate function** with the exact prototype:  
   ```c
   void displayBook(const struct Book *b);
   ```  
3. **Pointer Arithmetic Only** – While traversing the array to locate the ISBN, you **may not use the subscript operator `[]`**. Access each element exclusively through pointer arithmetic (e.g., `ptr + i`, `*(ptr + i)`).  
4. **Dynamic Memory Management** – Allocate the array with `malloc` (or `calloc`) and free it before program exit.  
5. **No Global Variables** – All data must be passed via parameters or local variables.  

*If you decide to extend the program with a menu (optional), you must include an explicit “Exit” option (e.g., entering `0` or the word `EXIT`) that terminates the program.*

---

## Problem 100 - openai/gpt-oss-120b - Iteration 50
# STEP 1: PROBLEM  

## Background  
You have been hired by **EcoTrack**, a small environmental‑monitoring startup, to write a utility that keeps a short list of sensor stations deployed in a city park. Each station records the current temperature (in Celsius) and the number of minutes since the last maintenance check. The stations are stored in a **fixed‑size array**, and the program must manipulate this array **exclusively with pointers and pointer arithmetic** – no array indexing (`[]`) is allowed.

## Program Requirements  

1. **Data representation**  
   * Define a `struct Station` that contains:  
     ```c
     float temperature;      // current temperature in °C
     int   minutesSinceCheck; // minutes since last maintenance
     ```
2. **Menu‑driven interface** (the program runs until the user selects the exit option)  
   * **1. Add a station** – Prompt the user for temperature and minutes‑since‑check, then store the new station in the first free slot of the array. If the array is full, display an error message.  
   * **2. Update a station** – Ask for the index (0‑based) of the station to modify, then request the new temperature and minutes‑since‑check, and overwrite the data at that position. If the index is invalid, display an error.  
   * **3. Display a station** – Ask for the index of the station and print its contents in the format shown below. If the index is invalid, display an error. The display logic **must be implemented in a separate function named `displayStation`**.  
   * **4. List all stations** – Iterate through the array and print every stored station (skip unused slots).  
   * **5. EXIT** – Terminates the program.  

3. **Pointer‑only manipulation**  
   * All accesses to the `Station` array must be performed using pointers (`Station *`) and pointer arithmetic (`ptr + i`, `*(ptr + i)`, etc.). Direct array indexing (`stations[i]`) is prohibited.  

4. **Program flow**  
   * The program should continue to display the menu after completing any option except EXIT.  

## Example Interaction  

```
=== EcoTrack Station Manager ===
1) Add a station
2) Update a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 1
Enter temperature (°C): 23.5
Enter minutes since last check: 45
Station added at index 0.

=== EcoTrack Station Manager ===
1) Add a station
2) Update a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 1
Enter temperature (°C): 19.2
Enter minutes since last check: 12
Station added at index 1.

=== EcoTrack Station Manager ===
1) Add a station
2) Update a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 3
Enter station index to display: 0
Station 0 -> Temperature: 23.50°C, Minutes Since Check: 45

=== EcoTrack Station Manager ===
1) Add a station
2) Update a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 4
Station 0 -> Temperature: 23.50°C, Minutes Since Check: 45
Station 1 -> Temperature: 19.20°C, Minutes Since Check: 12

=== EcoTrack Station Manager ===
1) Add a station
2) Update a station
3) Display a station
4) List all stations
5) EXIT
Choose an option: 5
Goodbye!
```

*If the user tries to add a station when the array is full, the program should print:*  

```
Error: station list is full.
```

*If an invalid index is supplied:*  

```
Error: invalid station index.
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented with a `struct Station`.  
2. **Display function** – The logic for showing the details of **one specific station** must reside in a function with the exact prototype:  
   ```c
   void displayStation(const Station *s, int index);
   ```  
3. **Pointer‑only array handling** – No use of the subscript operator (`[]`) anywhere in the program; all reads/writes to the station array must be via pointers and pointer arithmetic.  
4. **Menu exit option** – The menu must contain a distinct option (number **5**) labeled **EXIT** that terminates the program.  

*Note:* The maximum number of stations can be a constant such as `#define MAX_STATIONS 10`. The solution should compile with a standard C compiler (C99 or later).

---

