# Problem Batch Preview: Implementing Data Structures (e.g., Singly Linked Lists)
**Batch Number:** 1 | **Total Problems:** 100

---

## Problem 1 - llama-3.3-70b-versatile - Iteration 61
# STEP 1: PROBLEM
You are a software developer tasked with creating a simple library management system to keep track of books. The system should be able to store information about each book, including its title, author, publication year, and status (available or borrowed). The system should be able to add new books, remove existing books, display all books, and display the details of a specific book.

The library management system will use a singly linked list to store the book information. Each node in the linked list will represent a book, and the nodes will be linked together in the order they are added to the system.

### REQUIREMENTS
1. The program must be able to add new books to the system.
2. The program must be able to remove existing books from the system.
3. The program must be able to display all books in the system.
4. The program must be able to display the details of a specific book.
5. The program must be able to update the status of a book (from available to borrowed or vice versa).

### EXAMPLE
If the system has the following books:
- Book 1: Title = "Book1", Author = "Author1", Year = 2020, Status = "available"
- Book 2: Title = "Book2", Author = "Author2", Year = 2021, Status = "available"

The output of displaying all books should be:
```
Book1 by Author1 (2020) - available
Book2 by Author2 (2021) - available
```

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Must use a singly linked list to store the books.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must include a menu to interact with the system.
- If a menu is implemented:
  - Must include a specific menu option to EXIT the program (option 6: "Exit").

Example menu:
```
1. Add a new book
2. Remove a book
3. Display all books
4. Display a specific book
5. Update book status
6. Exit
```

---

## Problem 2 - llama-3.3-70b-versatile - Iteration 62
# STEP 1: PROBLEM
In a university setting, it's essential to manage student records efficiently. To achieve this, we can utilize a Singly Linked List to store and manipulate student data. Your task is to design a program that implements a Singly Linked List to manage student records.

The program should allow users to add, delete, and display student records. Each student record should contain the student's ID, name, and GPA.

### REQUIREMENTS
1. The program should have the ability to add a new student record to the end of the list.
2. The program should have the ability to delete a student record based on the student's ID.
3. The program should have the ability to display all student records.
4. The program should have the ability to display the details of a specific student record based on the student's ID.

### EXAMPLE
Input:
```
Add student with ID: 1, Name: John, GPA: 3.5
Add student with ID: 2, Name: Alice, GPA: 3.8
Display all students
Display student with ID: 1
Delete student with ID: 1
Display all students
```
Output:
```
Student 1: John, GPA: 3.5
Student 2: Alice, GPA: 3.8
Student 1: John, GPA: 3.5
Student 1: Alice, GPA: 3.8
```

### CONSTRAINTS
1. Must use a 'struct' to represent the student record.
2. Logic for displaying the details of one specific student record must be in a function called 'displayStudent'.
3. The program must be implemented with a menu-driven interface.
4. The menu should have the following options:
   - Option 1: Add a new student record
   - Option 2: Delete a student record
   - Option 3: Display all student records
   - Option 4: Display a specific student record
   - Option 5: EXIT the program

Note: The user can exit the program by selecting Option 5.

---

## Problem 3 - llama-3.3-70b-versatile - Iteration 63
# STEP 1: PROBLEM
In a university setting, it's common for students to enroll in various courses. To manage student enrollment efficiently, you've been tasked with designing a system that utilizes a singly linked list to store and manage course enrollment data. Each course has a unique identifier, name, and the number of students enrolled.

The system should allow users to perform the following operations:
1. Add a new course to the system.
2. Remove a course from the system based on its unique identifier.
3. Display all courses in the system.
4. Display the details of a specific course.
5. Enroll a student in a course (increment the enrollment count).
6. Drop a student from a course (decrement the enrollment count if the course has students enrolled).

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Course).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a menu-driven approach.
- The menu options should include:
  1. Add Course
  2. Remove Course
  3. Display All Courses
  4. Display Course Details
  5. Enroll Student
  6. Drop Student
  7. EXIT

### EXAMPLE INPUT/OUTPUT
Example Input:
- Adding a course: Course ID = "CS101", Name = "Introduction to Computer Science"
- Removing a course: Course ID = "CS101"
- Displaying all courses: List all courses in the system.
- Displaying course details: Course ID = "CS101"
- Enrolling a student: Course ID = "CS101"
- Dropping a student: Course ID = "CS101"

Example Output:
- After adding "CS101": Course CS101 added successfully.
- After removing "CS101": Course CS101 removed successfully.
- Displaying all courses: List of courses with their IDs, names, and enrollment counts.
- Displaying course details: Course ID: CS101, Name: Introduction to Computer Science, Enrollment Count: 5
- After enrolling a student in "CS101": Student enrolled in CS101 successfully.
- After dropping a student from "CS101": Student dropped from CS101 successfully.

The system should be designed to handle invalid inputs (e.g., attempting to remove a non-existent course, enrolling in a non-existent course) and provide meaningful error messages. The program should continue to run until the user chooses the EXIT option (option 7).

---

## Problem 4 - llama-3.3-70b-versatile - Iteration 64
# STEP 1: PROBLEM
In a university setting, it is essential to keep track of student records efficiently. To achieve this, we can utilize a singly linked list data structure. The problem is to design and implement a program that manages student records using a singly linked list.

Background:
The university wants to create a simple system to store and manage student information, including student ID, name, and GPA. The system should allow administrators to add new student records, delete existing records, display all records, and search for a specific student by ID.

Requirements:
1. The program should create a singly linked list to store student records.
2. The program should have the following functionalities:
   - Add a new student record to the list.
   - Delete a student record by ID.
   - Display all student records in the list.
   - Search for a student record by ID and display the details if found.
3. The program should handle cases where the list is empty or the student record is not found.

Example:
Input:
- Add student with ID 1, name "John Doe", and GPA 3.5.
- Add student with ID 2, name "Jane Doe", and GPA 3.8.
- Display all student records.
- Search for student with ID 1.

Output:
- Student records:
  - ID: 1, Name: John Doe, GPA: 3.5
  - ID: 2, Name: Jane Doe, GPA: 3.8
- Student with ID 1: John Doe, GPA: 3.5

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of ONE specific student record must be in a function called 'displayStudent'.
- The program should have a menu-driven interface with the following options:
  1. Add a new student record.
  2. Delete a student record by ID.
  3. Display all student records.
  4. Search for a student record by ID.
  5. EXIT the program.
- To exit the program, the user must select option 5.

Note: The program should be implemented in a way that is easy to understand and maintain, with proper comments and error handling.

---

## Problem 5 - llama-3.3-70b-versatile - Iteration 65
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a singly linked list to keep track of the books, where each node in the list represents a book with its title, author, and publication year. Your task is to design a program that allows the librarian to manage the collection of books.

The program should allow the librarian to:
1. Add a new book to the collection.
2. Remove a book from the collection by title.
3. Display all the books in the collection.
4. Search for a book by title or author.
5. Exit the program.

The librarian should be able to interact with the program through a menu-driven interface.

### CONSTRAINTS
- Must use a 'struct' to represent a book with its title, author, and publication year.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented using a singly linked list.
- The menu option to EXIT the program is option 5, labeled as "Exit".
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. Exit

### EXAMPLE INPUT/OUTPUT
If the librarian adds the following books:
- Title: "Book1", Author: "Author1", Year: 2000
- Title: "Book2", Author: "Author2", Year: 2001
- Title: "Book3", Author: "Author3", Year: 2002

The output of displaying all books should be:
```
Book1 by Author1 (2000)
Book2 by Author2 (2001)
Book3 by Author3 (2002)
```

If the librarian searches for a book by title "Book2", the output should be:
```
Book2 by Author2 (2001)
```

If the librarian removes a book by title "Book2", the output of displaying all books should be:
```
Book1 by Author1 (2000)
Book3 by Author3 (2002)
```

---

## Problem 6 - llama-3.3-70b-versatile - Iteration 66
# STEP 1: PROBLEM
You are the curator of a local library, and you want to create a simple system to manage the books in your collection. You decide to implement a singly linked list to store information about each book, including its title, author, and publication year.

The system should allow you to add new books to the collection, remove existing books, and display the details of all books or a specific book.

### REQUIREMENTS
1. The system must be able to add a new book to the collection with its title, author, and publication year.
2. The system must be able to remove a book from the collection by its title.
3. The system must be able to display the details of all books in the collection.
4. The system must be able to display the details of a specific book by its title.
5. The system must have a menu-driven interface to interact with the user.

### EXAMPLE
If the user adds the following books:
- Title: "To Kill a Mockingbird", Author: "Harper Lee", Publication Year: 1960
- Title: "1984", Author: "George Orwell", Publication Year: 1949

The system should be able to display the details of all books:
- "To Kill a Mockingbird" by Harper Lee (1960)
- "1984" by George Orwell (1949)

If the user searches for a specific book by title, e.g., "To Kill a Mockingbird", the system should display:
- "To Kill a Mockingbird" by Harper Lee (1960)

### CONSTRAINTS
1. Must use a 'struct' to represent a book.
2. Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
3. Logic for displaying the details of a specific book must be in a function called 'displayBook'.
4. The solution must be implemented with a menu-driven interface.
5. The menu must have the following options:
   - Option 1: Add a new book
   - Option 2: Remove a book by title
   - Option 3: Display all books
   - Option 4: Search for a book by title
   - Option 5: EXIT the program

Note: The EXIT option is clearly stated as Option 5.

---

## Problem 7 - llama-3.3-70b-versatile - Iteration 67
# STEP 1: PROBLEM
In a university setting, it's common to manage student records using various data structures. One such application is a Singly Linked List, where each node represents a student with their unique ID, name, and GPA. The goal is to design a program that utilizes a Singly Linked List to store and manage student records efficiently.

Background:
The university's administration wants to create a simple console-based application to manage student records. The application should allow administrators to add new students, delete existing students, display all students, and search for a specific student by their ID.

Requirements:
1. The program should have a menu-driven interface with options to add a new student, delete a student, display all students, search for a student by ID, and exit the program.
2. When adding a new student, the program should prompt the user to input the student's ID, name, and GPA.
3. When deleting a student, the program should prompt the user to input the student's ID and then remove the corresponding student from the list if found.
4. When displaying all students, the program should print out the details of each student in the list.
5. When searching for a student by ID, the program should print out the details of the student with the matching ID if found.

Example Input/Output:
```
Menu:
1. Add Student
2. Delete Student
3. Display All Students
4. Search Student by ID
5. Exit

Choose an option: 1
Enter Student ID: S001
Enter Student Name: John Doe
Enter Student GPA: 3.5

Menu:
1. Add Student
2. Delete Student
3. Display All Students
4. Search Student by ID
5. Exit

Choose an option: 3
Student ID: S001, Name: John Doe, GPA: 3.5
```

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Student).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
3. The Singly Linked List must be implemented using a separate function for each operation (e.g., addNode, deleteNode, displayList, searchNode).
4. The solution must be implemented with a single main function to handle the menu-driven interface.

Note: To exit the program, choose option 5 from the menu. The program should terminate cleanly and release any allocated memory.

---

## Problem 8 - llama-3.3-70b-versatile - Iteration 68
# STEP 1: PROBLEM
In a university setting, it's crucial to manage student records efficiently. As the administrator of a computer science department, you need to implement a system that can store and display student information using a Singly Linked List. The system should allow you to add students, remove students, and display the details of all students or a specific student.

### BACKGROUND
The system will store student records, each containing the student's ID, name, and GPA. You will implement a Singly Linked List to store these records, providing functions to add, remove, and display student information.

### REQUIREMENTS
1. Implement a Singly Linked List to store student records.
2. Provide a function to add a new student to the list.
3. Provide a function to remove a student by their ID.
4. Provide a function to display the details of all students in the list.
5. Provide a function to display the details of a specific student by their ID.

### EXAMPLE
Input:
- Add student with ID 1, name "John Doe", and GPA 3.5
- Add student with ID 2, name "Jane Doe", and GPA 3.8
- Display all students
- Remove student with ID 1
- Display all students

Output:
- After adding both students and displaying all:
  - Student ID: 1, Name: John Doe, GPA: 3.5
  - Student ID: 2, Name: Jane Doe, GPA: 3.8
- After removing the student with ID 1 and displaying all:
  - Student ID: 2, Name: Jane Doe, GPA: 3.8

### CONSTRAINTS
- Must use a 'struct' to represent a student.
- Logic for displaying the details of all students must be in a function called 'displayAllStudents'.
- The solution must include a menu with the following options:
  1. Add a student
  2. Remove a student
  3. Display all students
  4. Display a specific student
  5. EXIT
- The program must exit when the user chooses option 5 (EXIT). 

Note: The menu options and their corresponding numbers can be modified based on specific requirements, but the EXIT option must be clearly stated as in this example.

---

## Problem 9 - llama-3.3-70b-versatile - Iteration 69
# STEP 1: PROBLEM
In a university setting, student records are crucial for tracking academic progress, attendance, and other important details. To efficiently manage these records, a system based on a singly linked list can be implemented. The goal is to create a program that can store, retrieve, and manipulate student records in a user-friendly manner.

Background:
The university wants a simple console-based application that allows administrators to manage student records. Each record should contain the student's ID, name, and GPA. The system should enable administrators to add new records, delete existing ones, display all records, and search for a specific student by ID.

Requirements:
1. The program should allow administrators to add new student records to the system.
2. Administrators should be able to delete a student record by ID.
3. The system must display all student records.
4. It should be possible to search for a student by ID and display their record.
5. The program should handle cases where a student record is not found.

Example:
Input: 
- Add student with ID 123, name "John Doe", GPA 3.5
- Add student with ID 456, name "Jane Doe", GPA 3.8
- Display all records
- Search for student with ID 123

Output:
- When displaying all records:
  - ID: 123, Name: John Doe, GPA: 3.5
  - ID: 456, Name: Jane Doe, GPA: 3.8
- When searching for student with ID 123:
  - ID: 123, Name: John Doe, GPA: 3.5

### CONSTRAINTS
- Must use a 'struct' to represent a student record.
- Logic for displaying the details of all student records must be in a function called 'displayRecords'.
- The solution must include a menu-driven interface.
- Must include a menu option to EXIT the program. The exit option should be '5. Exit'.
- The menu options should be as follows:
  1. Add a new student record
  2. Delete a student record by ID
  3. Display all student records
  4. Search for a student by ID
  5. Exit

Note: The program should be implemented in a way that it can handle a variable number of student records and should be able to handle cases where the list is empty.

---

## Problem 10 - llama-3.3-70b-versatile - Iteration 70
# STEP 1: PROBLEM
You are a librarian tasked with creating a system to manage book rentals in a small library. The library has a collection of books, and you want to implement a singly linked list to store the book information. Each book has a unique ID, title, author, and rental status (available or rented).

The system should allow users to add new books, remove existing books, display all books, and search for a specific book by ID. The system should also display the details of a specific book when searched.

### REQUIREMENTS
1. Implement a singly linked list to store book information.
2. The system should have the following functionalities:
   - Add a new book to the list.
   - Remove a book from the list by ID.
   - Display all books in the list.
   - Search for a book by ID and display its details.
3. The system should handle cases where a book is not found in the list.

### EXAMPLE
Input:
- Add book with ID 1, title "Book1", author "Author1", and status "available".
- Add book with ID 2, title "Book2", author "Author2", and status "rented".
- Display all books.
- Search for book with ID 1.

Output:
- When displaying all books:
  - Book ID: 1, Title: Book1, Author: Author1, Status: available
  - Book ID: 2, Title: Book2, Author: Author2, Status: rented
- When searching for book with ID 1:
  - Book ID: 1, Title: Book1, Author: Author1, Status: available

### CONSTRAINTS
- Must use a 'struct' to represent the book information.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu options are:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Search for a book by ID
  5. EXIT

Note: The EXIT option is used to terminate the program. When the user selects this option, the program should end and return control to the operating system.

---

## Problem 11 - llama-3.3-70b-versatile - Iteration 71
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a simple system to keep track of the books, and you have been asked to implement this system using a singly linked list. The system should be able to store the title, author, and publication year of each book.

The library's system has the following requirements:
1. The system should be able to add a new book to the collection.
2. The system should be able to display all the books in the collection.
3. The system should be able to search for a book by its title and display its details.
4. The system should be able to delete a book from the collection by its title.

Here is a simple example of the expected input/output:
```
Input: 
Add book: "Book1" by "Author1" (2020)
Add book: "Book2" by "Author2" (2021)
Display all books:
Book1 by Author1 (2020)
Book2 by Author2 (2021)
Search for book: "Book1"
Book1 by Author1 (2020)
Delete book: "Book1"
Display all books:
Book2 by Author2 (2021)
```

### CONSTRAINTS
- Must use a 'struct' to represent a book, containing the title, author, and publication year.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- The solution must include a menu-driven interface with the following options:
  1. Add a new book
  2. Display all books
  3. Search for a book
  4. Delete a book
  5. EXIT the program
- The program must exit when the user selects the 'EXIT' option (option 5).

---

## Problem 12 - llama-3.3-70b-versatile - Iteration 72
# STEP 1: PROBLEM
Imagine you are a librarian tasked with managing a collection of books in a library. You want to create a program to keep track of the books, allowing you to add, remove, and display information about each book. To achieve this, you will implement a singly linked list data structure.

Background:
The library has a vast collection of books, and manually keeping track of each book is becoming increasingly difficult. The librarian needs a program that can efficiently store and manage book information. The program should allow the librarian to add new books, remove existing books, and display details about specific books.

Requirements:
1. The program should allow the librarian to add a new book to the collection.
2. The program should allow the librarian to remove a book from the collection by its unique identifier (book ID).
3. The program should display the details of all books in the collection.
4. The program should display the details of a specific book by its unique identifier (book ID).

Example Input/Output:
- Add a new book: Book ID = 1, Title = "Introduction to Computer Science", Author = "John Doe"
- Remove a book: Book ID = 1
- Display all books:
  - Book ID = 2, Title = "Data Structures", Author = "Jane Smith"
  - Book ID = 3, Title = "Algorithms", Author = "Bob Johnson"
- Display a specific book: Book ID = 2
  - Book ID = 2, Title = "Data Structures", Author = "Jane Smith"

### CONSTRAINTS
- Must use a 'struct' to represent a book, containing the book ID, title, and author.
- The solution must be implemented with a single linked list data structure.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- If a menu is implemented, it must include the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (type '5' to exit the program)
- The program should handle cases where a book with the specified ID does not exist.

---

## Problem 13 - llama-3.3-70b-versatile - Iteration 73
# STEP 1: PROBLEM
You are a curator at a local museum, and you have been tasked with creating a digital catalog of the museum's collection. The catalog will store information about each artifact, including its name, description, and acquisition date. To efficiently manage the catalog, you decide to implement a singly linked list data structure.

The museum has a large collection, and the catalog needs to support the following operations:
1. Add a new artifact to the catalog.
2. Remove an artifact from the catalog by its name.
3. Display all artifacts in the catalog.
4. Display the details of a specific artifact.
5. Update the description of an artifact.

The catalog will be used by multiple staff members, so it's essential to ensure that the program is user-friendly and easy to navigate.

Here's a simple example of expected input/output:
```
Add artifact: 
Name: Ancient Vase
Description: A vase from ancient Greece
Acquisition Date: 2020-01-01

Display all artifacts:
1. Ancient Vase - A vase from ancient Greece - 2020-01-01

Display artifact details:
Name: Ancient Vase
Description: A vase from ancient Greece
Acquisition Date: 2020-01-01

Update artifact description:
Name: Ancient Vase
New Description: A vase from ancient Greece, recently restored

Display all artifacts:
1. Ancient Vase - A vase from ancient Greece, recently restored - 2020-01-01
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (i.e., the artifact).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a single function besides `main()` to handle user input and menu navigation.
- If a menu is implemented:
  - Must include a specific menu option to EXIT the program (option 6: "Exit Program").
  - The menu options must be clearly numbered, starting from 1. 

Example menu:
```
Museum Catalog Menu:
1. Add artifact
2. Remove artifact
3. Display all artifacts
4. Display artifact details
5. Update artifact description
6. Exit Program
```

---

## Problem 14 - llama-3.3-70b-versatile - Iteration 74
# STEP 1: PROBLEM
In a library management system, books are arranged in a shelf in a particular order. To manage the books efficiently, the librarian wants to implement a system that uses a singly linked list to store the book details. Each book has a unique book ID, title, author, and publication year.

The librarian wants a program that can perform the following operations:
1. Insert a new book at the beginning of the list.
2. Insert a new book at the end of the list.
3. Delete a book by its ID.
4. Display all the books in the list.
5. Search for a book by its ID and display its details.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must be implemented with a menu-driven approach.
- Must include a menu option to EXIT the program (option 6).

### EXAMPLE
If the input is:
```
1. Insert book at beginning: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
2. Insert book at end: ID = 2, Title = "Book2", Author = "Author2", Year = 2021
3. Display all books:
   Book ID: 1, Title: Book1, Author: Author1, Year: 2020
   Book ID: 2, Title: Book2, Author: Author2, Year: 2021
4. Search book by ID: 1
   Book ID: 1, Title: Book1, Author: Author1, Year: 2020
5. Delete book by ID: 1
6. Display all books:
   Book ID: 2, Title: Book2, Author: Author2, Year: 2021
7. Exit the program (option 6)
```
The program should be able to handle the above operations and display the results accordingly. 

The menu options should be:
1. Insert book at beginning
2. Insert book at end
3. Display all books
4. Search book by ID
5. Delete book by ID
6. EXIT

---

## Problem 15 - llama-3.3-70b-versatile - Iteration 75
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining academic history and facilitating administrative tasks. To efficiently manage these records, a data structure that allows for easy insertion, deletion, and display of student information is necessary. A Singly Linked List can be an ideal choice for this purpose, given its dynamic nature and ability to grow or shrink as records are added or removed.

Imagine you are tasked with designing a simple student record management system using a Singly Linked List. Each student record should contain the student's ID, name, and GPA. The system should allow for adding new student records, deleting existing ones, and displaying all or specific student records.

### REQUIREMENTS
1. The program should create a Singly Linked List to store student records.
2. It should have the capability to add a new student record at the end of the list.
3. It should be able to delete a student record based on the student's ID.
4. It should be able to display all student records in the list.
5. It should be able to display the details of a specific student record based on the student's ID.

### EXAMPLE
- Input: Add student records for John (ID: 1, GPA: 3.5), Alice (ID: 2, GPA: 3.8), and Bob (ID: 3, GPA: 3.2).
- Output (after displaying all records): 
  - ID: 1, Name: John, GPA: 3.5
  - ID: 2, Name: Alice, GPA: 3.8
  - ID: 3, Name: Bob, GPA: 3.2
- Input: Display the record for ID: 2.
- Output: ID: 2, Name: Alice, GPA: 3.8

### CONSTRAINTS
- Must use a 'struct' to represent the student record.
- Logic for displaying the details of all student records must be in a function called 'displayAllRecords'.
- Logic for displaying the details of a specific student record must be in a function called 'displayRecord'.
- The solution must implement a menu-driven system with the following options:
  1. Add a new student record.
  2. Delete a student record by ID.
  3. Display all student records.
  4. Display a specific student record by ID.
  5. EXIT the program.
- The program must exit when the user chooses the 'EXIT' option (option 5).

---

## Problem 16 - llama-3.3-70b-versatile - Iteration 76
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a simple cataloging system where each book is represented by its title, author, and publication year. To efficiently manage the catalog, you decide to implement a singly linked list data structure to store and manipulate the book records.

The library wants a program that can perform the following operations:
1. Add a new book to the catalog.
2. Remove a book from the catalog by its title.
3. Display all the books in the catalog.
4. Search for a book by its title and display its details if found.
5. Exit the program.

Here's a simple example of the expected input/output:
- When you add a book titled "Introduction to CS" by "John Doe" published in 2020, the program should store this information.
- When you choose to display all books, the program should output the details of all the books in the catalog, including the one you just added.
- If you search for a book titled "Introduction to CS", the program should display its details.

### CONSTRAINTS
- Must use a `struct` to represent a book, containing the title, author, and publication year.
- Logic for displaying the details of all books must be in a function called `displayCatalog`.
- The solution must be implemented with a menu-driven approach.
- The menu options must include:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. EXIT (to exit the program)
- The program must handle invalid inputs and edge cases, such as attempting to remove a non-existent book or searching for a book that does not exist in the catalog.

---

## Problem 17 - llama-3.3-70b-versatile - Iteration 77
# STEP 1: PROBLEM
You are the curator of a library that uses a singly linked list to keep track of its book collection. Each book in the collection has a unique identifier (ID), title, author, and publication year. Your task is to design a program that allows the librarian to manage the book collection by performing various operations such as adding a new book, removing a book, searching for a book, and displaying all books in the collection.

## BACKGROUND
The library has a large collection of books, and the current system for managing the collection is manual and prone to errors. The librarian wants a program that can efficiently manage the collection and provide accurate information about the books.

## REQUIREMENTS
The program must have the following functionality:
1. Add a new book to the collection.
2. Remove a book from the collection by its ID.
3. Search for a book by its ID, title, or author.
4. Display all books in the collection.
5. Display the details of a specific book.

## EXAMPLE
Input:
```
Add book with ID: 1, title: "Book1", author: "Author1", publication year: 2020
Add book with ID: 2, title: "Book2", author: "Author2", publication year: 2021
Display all books
Search for book with title: "Book1"
```
Output:
```
Book with ID: 1, title: "Book1", author: "Author1", publication year: 2020
Book with ID: 2, title: "Book2", author: "Author2", publication year: 2021
Book with ID: 1, title: "Book1", author: "Author1", publication year: 2020
```

### CONSTRAINTS
1. Must use a 'struct' to represent a book.
2. Logic for displaying the details of a specific book must be in a function called 'displayBook'.
3. The program must be implemented using a singly linked list.
4. The program must have a menu with the following options:
   - Add a new book (option 1)
   - Remove a book (option 2)
   - Search for a book (option 3)
   - Display all books (option 4)
   - Display the details of a specific book (option 5)
   - EXIT the program (option 6)

Note: The program will exit when the user chooses option 6.

---

## Problem 18 - llama-3.3-70b-versatile - Iteration 78
# STEP 1: PROBLEM
You are a librarian tasked with managing a collection of books in a library. The library uses a singly linked list to keep track of the books, where each book has a unique identifier (ID), title, author, and publication year. Your task is to create a program that allows the librarian to manage the collection of books.

The background story is that the library has recently acquired a new set of books and needs to update its catalog. The librarian wants to be able to add new books, remove existing books, display all books, and search for a specific book by its ID or title.

The requirements for the program's functionality are:
1. The program must allow the librarian to add a new book to the collection.
2. The program must allow the librarian to remove a book from the collection by its ID.
3. The program must allow the librarian to display all books in the collection.
4. The program must allow the librarian to search for a book by its ID or title.

An example of expected input/output is:
```
Input:
Add book with ID: 1, title: "Book1", author: "Author1", publication year: 2020
Add book with ID: 2, title: "Book2", author: "Author2", publication year: 2021
Display all books:
Book ID: 1, title: "Book1", author: "Author1", publication year: 2020
Book ID: 2, title: "Book2", author: "Author2", publication year: 2021
Search for book by ID: 1
Book ID: 1, title: "Book1", author: "Author1", publication year: 2020
Remove book with ID: 1
Display all books:
Book ID: 2, title: "Book2", author: "Author2", publication year: 2021
```

### CONSTRAINTS
* The solution must be implemented using a singly linked list.
* Must use a 'struct' to represent a book.
* Logic for displaying the details of all books must be in a function called 'displayBooks'.
* The solution must include a menu with the following options:
  1. Add book
  2. Remove book
  3. Display all books
  4. Search for book
  5. EXIT
* The program must exit when the user selects the 'EXIT' option (option 5).

---

## Problem 19 - llama-3.3-70b-versatile - Iteration 79
# STEP 1: PROBLEM
You are the curator of a museum with a vast collection of artifacts from around the world. Each artifact has a unique identifier, name, description, and acquisition year. To efficiently manage and display the artifacts, you want to create a program that utilizes a singly linked list data structure. The program should allow you to add, remove, and display artifacts, as well as search for specific artifacts by their identifier or name.

The program's functionality should include the following requirements:
1. The ability to add a new artifact to the collection.
2. The ability to remove an artifact by its identifier.
3. The ability to display all artifacts in the collection.
4. The ability to search for an artifact by its identifier or name.
5. The ability to display the details of a specific artifact.

### CONSTRAINTS
* Must use a 'struct' to represent the primary data entity (i.e., the artifact).
* Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
* The solution must be implemented with a single function besides main() to handle all menu operations.
* If a menu is implemented, it must include the following options:
  - Option 1: Add a new artifact
  - Option 2: Remove an artifact by identifier
  - Option 3: Display all artifacts
  - Option 4: Search for an artifact by identifier or name
  - Option 5: Display the details of a specific artifact
  - Option 6: EXIT the program

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add a new artifact
Enter artifact identifier: A001
Enter artifact name: Ancient Vase
Enter artifact description: A vase from ancient Greece
Enter acquisition year: 2010

2. Display all artifacts
Artifact Identifier: A001
Artifact Name: Ancient Vase
Artifact Description: A vase from ancient Greece
Acquisition Year: 2010

3. Search for an artifact by identifier
Enter artifact identifier: A001
Artifact Identifier: A001
Artifact Name: Ancient Vase
Artifact Description: A vase from ancient Greece
Acquisition Year: 2010
```
Example Output:
```
Menu:
1. Add a new artifact
2. Remove an artifact by identifier
3. Display all artifacts
4. Search for an artifact by identifier or name
5. Display the details of a specific artifact
6. EXIT

Choose an option: 
```

---

## Problem 20 - llama-3.3-70b-versatile - Iteration 80
# STEP 1: PROBLEM
In a university setting, student records are crucial for tracking academic progress, grades, and other relevant information. To efficiently manage these records, a data structure like a Singly Linked List can be utilized. Your task is to create a program that implements a Singly Linked List to store and manage student records.

Background:
The registrar's office wants a simple program to store and display student information. Each student record consists of a student ID, name, and GPA. The program should allow the registrar to add new student records, display all student records, and search for a specific student record by ID.

Requirements:
1. The program must allow the user to add a new student record with a unique ID, name, and GPA.
2. The program must display all student records in the list.
3. The program must allow the user to search for a specific student record by ID and display the details if found.
4. The program must handle cases where a student record with the given ID does not exist.

Example of expected Input/Output:
```
Menu:
1. Add Student Record
2. Display All Student Records
3. Search for Student Record
4. EXIT

Choose an option: 1
Enter Student ID: 1234
Enter Name: John Doe
Enter GPA: 3.5

Choose an option: 2
Student ID: 1234, Name: John Doe, GPA: 3.5

Choose an option: 3
Enter Student ID to search: 1234
Student ID: 1234, Name: John Doe, GPA: 3.5

Choose an option: 4
Exiting the program...
```

### CONSTRAINTS
- Must use a `struct` to represent the student record.
- Logic for displaying the details of ONE specific student record must be in a function called `displayStudent`.
- The solution must be implemented with a single Singly Linked List.
- The menu option to EXIT the program is option 4, labeled as "EXIT".
- If a menu is implemented, it must include options to add a student record, display all student records, search for a student record, and exit the program.

---

## Problem 21 - llama-3.3-70b-versatile - Iteration 81
# STEP 1: PROBLEM
You are the curator of a museum, and you want to create a system to keep track of the artifacts in your collection. You decide to use a singly linked list to store the information about each artifact. Each artifact has a unique identifier, a name, and a description.

The museum has a large collection of artifacts, and you want to be able to add, remove, and display information about each artifact. You also want to be able to search for artifacts by their identifier or name.

Here are the requirements for the program's functionality:
1. Create a new artifact with a unique identifier, name, and description.
2. Add the new artifact to the end of the linked list.
3. Remove an artifact from the linked list by its identifier.
4. Display all the artifacts in the linked list.
5. Search for an artifact by its identifier or name.

### EXAMPLE
Input:
```
Add artifact with id 1, name "Vase", and description "Ancient Greek vase".
Add artifact with id 2, name "Painting", and description "Modern art painting".
Display all artifacts.
Search for artifact with id 1.
```
Output:
```
Artifact 1: Vase - Ancient Greek vase
Artifact 2: Painting - Modern art painting
Artifact 1: Vase - Ancient Greek vase
```
### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Artifact).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all the operations on the linked list.
- If a menu is implemented, it must include the following options:
  1. Add artifact
  2. Remove artifact
  3. Display all artifacts
  4. Search for artifact
  5. EXIT (to exit the program)
- The program must handle invalid inputs and errors, such as attempting to remove an artifact that does not exist.

---

## Problem 22 - llama-3.3-70b-versatile - Iteration 82
# STEP 1: PROBLEM
You are the curator of a museum that specializes in showcasing a collection of rare and unique artifacts from around the world. To efficiently manage and display information about these artifacts, you decide to implement a system using a Singly Linked List data structure. Each artifact has a unique identifier, name, description, and acquisition year. 

The system should allow users to add new artifacts, display all artifacts, and search for a specific artifact by its identifier. 

Here are the requirements for the program's functionality:
1. The program should allow users to add new artifacts to the collection.
2. The program should display all artifacts in the collection.
3. The program should allow users to search for a specific artifact by its identifier and display its details.
4. The program should have a menu-driven interface with options to add an artifact, display all artifacts, search for an artifact, and exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent an artifact, containing fields for the unique identifier, name, description, and acquisition year.
- Logic for displaying the details of one specific artifact must be in a function called 'displayArtifact'.
- The solution must be implemented with a single function besides main() to handle the menu and user interactions.
- If a menu is implemented, it must include a specific menu option to EXIT the program, which should be option 5.

### EXAMPLE INPUT/OUTPUT
Example Input:
```
1. Add Artifact
2. Display All Artifacts
3. Search Artifact
4. Display Menu
5. Exit
```
User chooses option 1:
```
Enter unique identifier: 1
Enter name: Ancient Vase
Enter description: A 2000-year-old vase from ancient civilization
Enter acquisition year: 2010
```
User chooses option 2:
```
Artifact 1: 
  Unique Identifier: 1
  Name: Ancient Vase
  Description: A 2000-year-old vase from ancient civilization
  Acquisition Year: 2010
```
User chooses option 3:
```
Enter unique identifier to search: 1
Artifact 1: 
  Unique Identifier: 1
  Name: Ancient Vase
  Description: A 2000-year-old vase from ancient civilization
  Acquisition Year: 2010
```

---

## Problem 23 - llama-3.3-70b-versatile - Iteration 83
# STEP 1: PROBLEM
In a library management system, books are arranged in a shelf and each book has a title, author, and publication year. The librarian wants to create a program to manage the books in the shelf. The program should allow the librarian to add a new book, remove a book, and display all the books in the shelf.

The background story is that the library has a single shelf where books are added and removed frequently. The librarian needs a simple program to keep track of the books in the shelf.

The requirements for the program's functionality are:
1. The program should allow the librarian to add a new book to the shelf.
2. The program should allow the librarian to remove a book from the shelf.
3. The program should display all the books in the shelf.
4. The program should have a menu-driven interface to perform the above operations.

Here's a simple example of the expected input/output:
```
Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 1
Enter book title: Book1
Enter book author: Author1
Enter book publication year: 2020

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 3
Book1 by Author1 (2020)

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 2
Enter book title: Book1

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 3
No books in the shelf

Menu:
1. Add a new book
2. Remove a book
3. Display all books
4. Exit

Enter your choice: 4
Exiting the program...
```

### CONSTRAINTS
1. The program must use a singly linked list to store the books in the shelf.
2. The program must use a 'struct' to represent a book, which should have fields for title, author, and publication year.
3. The logic for displaying the details of all books must be in a function called 'displayBooks'.
4. The program must have a menu-driven interface with the following options:
   - 1: Add a new book
   - 2: Remove a book
   - 3: Display all books
   - 4: Exit
   The program should exit when the user chooses option 4. 

Note: The menu options and the 'displayBooks' function are mandatory. The program should handle invalid inputs and edge cases, such as removing a book that does not exist in the shelf.

---

## Problem 24 - llama-3.3-70b-versatile - Iteration 84
# STEP 1: PROBLEM
You are a librarian tasked with creating a system to manage a collection of books in a library. The system should utilize a singly linked list to store the books, where each book is represented by its title, author, and publication year. Your task is to design a program that allows users to interact with the library's collection by adding, removing, and searching for books.

## BACKGROUND
The library currently has a small collection of books, but it is expected to grow rapidly. The librarian needs a system that can efficiently manage the collection and provide users with an easy way to find specific books.

## REQUIREMENTS
The program should have the following functionality:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Search for a book by its title or author.
4. Display all books in the collection.
5. Display the details of a specific book.

## EXAMPLE
Input:
```
Add Book: "Introduction to Computer Science" by John Smith, 2020
Add Book: "Data Structures" by Jane Doe, 2019
Search Book by Title: "Introduction to Computer Science"
```
Output:
```
Book Found:
Title: Introduction to Computer Science
Author: John Smith
Publication Year: 2020
```

### CONSTRAINTS
1. Must use a `struct` to represent a book.
2. Logic for displaying the details of ONE specific book must be in a function called `displayBook`.
3. The solution must be implemented with a menu-driven interface.
4. The menu should have the following options:
   - Option 1: Add a new book to the collection.
   - Option 2: Remove a book from the collection.
   - Option 3: Search for a book.
   - Option 4: Display all books.
   - Option 5: Display the details of a specific book.
   - Option 6: EXIT the program.

Note: To exit the program, the user must select Option 6.

---

## Problem 25 - llama-3.3-70b-versatile - Iteration 85
# STEP 1: PROBLEM
In a library management system, it's essential to keep track of books and their authors efficiently. To achieve this, we can utilize a singly linked list data structure. The system should allow users to add books, remove books, display all books, and search for a specific book by its title.

Background:
The library manager wants to automate the process of managing books in the library. The manager needs a system that can store information about each book, including its title, author, and publication year. The system should be able to perform basic operations like adding, removing, and searching for books.

Requirements:
1. The program should have the ability to add a new book to the linked list.
2. The program should be able to remove a book from the linked list by its title.
3. The program should be able to display all the books in the linked list.
4. The program should be able to search for a specific book by its title and display its details.

Example:
Input: 
- Add a book with title "Introduction to CS", author "John Doe", and publication year 2020.
- Add a book with title "Data Structures", author "Jane Smith", and publication year 2019.
- Display all books.
- Search for a book with title "Introduction to CS".

Output:
- When displaying all books:
  - Introduction to CS by John Doe (2020)
  - Data Structures by Jane Smith (2019)
- When searching for a book with title "Introduction to CS":
  - Introduction to CS by John Doe (2020)

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayBooks'.
- The solution must include a menu with the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Search for a book
  5. EXIT
- The program should exit when the user chooses the 'EXIT' option (option 5).

Note: The menu option to EXIT the program is clearly option 5, labeled 'EXIT'.

---

## Problem 26 - llama-3.3-70b-versatile - Iteration 86
# STEP 1: PROBLEM
In a university's student information system, a singly linked list can be used to efficiently manage and retrieve student records. Each student has a unique ID, name, and GPA. The system needs to support adding new students, deleting existing students, and displaying student information.

The background story is that the university's current system is outdated and does not support efficient data retrieval. By implementing a singly linked list, the system can quickly add, remove, and display student records.

The program's functionality requirements are as follows:
1. Create a new node for each student with attributes: ID, name, and GPA.
2. Implement an `addStudent` function to add a new student to the end of the linked list.
3. Implement a `deleteStudent` function to remove a student by their ID from the linked list.
4. Implement a `displayStudents` function to display all students' information in the linked list.
5. Implement a `displayStudent` function to display a specific student's information by their ID.

Here is a simple example of expected input/output:
```
Input:
Add student with ID: 1, name: John, GPA: 3.5
Add student with ID: 2, name: Jane, GPA: 3.8
Display all students:
Student ID: 1, Name: John, GPA: 3.5
Student ID: 2, Name: Jane, GPA: 3.8
Delete student with ID: 1
Display all students:
Student ID: 2, Name: Jane, GPA: 3.8
Display student with ID: 2:
Student ID: 2, Name: Jane, GPA: 3.8
```

### CONSTRAINTS
- Must use a `struct` to represent the student entity.
- Logic for displaying the details of all students must be in a function called `displayStudents`.
- Logic for displaying the details of one specific student must be in a function called `displayStudent`.
- The program must have a menu with the following options:
  1. Add a new student
  2. Delete a student
  3. Display all students
  4. Display a specific student
  5. EXIT the program
- The program must exit when the user chooses option 5 (EXIT). 

Note that the program should handle cases where a student with the specified ID does not exist in the linked list.

---

## Problem 27 - llama-3.3-70b-versatile - Iteration 87
# STEP 1: PROBLEM
In a small library, the librarian wants to manage a collection of books using a singly linked list. Each book has a unique title, author, and publication year. The librarian needs a program to efficiently add, remove, and display books in the collection.

The program should allow the librarian to perform the following operations:
1. Add a new book to the collection.
2. Remove a book from the collection by its title.
3. Display all books in the collection.
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
Expected Output:
```
Book1, Author1, 2020
Book2, Author2, 2019
Book1, Author1, 2020
Book2, Author2, 2019
```

### CONSTRAINTS
- Must use a `struct` to represent a book with attributes: title, author, and publication year.
- Logic for displaying the details of one specific book must be in a function called `displayBook`.
- The solution must be implemented with a menu-driven approach.
- The menu options are:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- The program must handle cases where a book is not found in the collection.

Note: The program should be implemented in a way that is easy to understand and follow, using proper variable names, comments, and functions. The menu option to EXIT the program is option 5.

---

## Problem 28 - llama-3.3-70b-versatile - Iteration 88
# STEP 1: PROBLEM
In a university's student information system, a singly linked list can be used to store and manage student records. Each student record contains the student's ID, name, and GPA. The system should allow users to add new student records, delete existing records, and display all records. To make the system more user-friendly, a menu-driven interface will be implemented.

The background story is that the university wants to develop a simple student information system to manage student records efficiently. The system will be used by the university's administrative staff to add, delete, and view student records.

The requirements for the program's functionality are as follows:
1. The program should create a singly linked list to store student records.
2. The program should have a menu-driven interface with the following options:
   - Add a new student record
   - Delete a student record by ID
   - Display all student records
   - Exit the program
3. When adding a new student record, the program should prompt the user to enter the student's ID, name, and GPA.
4. When deleting a student record, the program should prompt the user to enter the ID of the student to be deleted.
5. When displaying all student records, the program should display the ID, name, and GPA of each student.

Here is a simple example of expected input/output:
```
Menu:
1. Add a new student record
2. Delete a student record
3. Display all student records
4. Exit the program
Enter your choice: 1
Enter student ID: S001
Enter student name: John Doe
Enter student GPA: 3.5
Menu:
1. Add a new student record
2. Delete a student record
3. Display all student records
4. Exit the program
Enter your choice: 3
Student Records:
ID: S001, Name: John Doe, GPA: 3.5
```

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (student record).
- Logic for displaying the details of all student records must be in a function called 'displayRecords'.
- The solution must be implemented with a single function besides main() to handle the menu options.
- The program must include a specific menu option to EXIT the program, which is option 4. When this option is chosen, the program should terminate and display a farewell message.

---

## Problem 29 - llama-3.3-70b-versatile - Iteration 89
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. To efficiently manage these records, we can utilize a singly linked list data structure. The problem requires designing a program that implements a singly linked list to store student records, allowing for easy insertion, deletion, and display of student information.

The background story is that the university registrar's office needs a simple system to manage student records. Each student record consists of a unique student ID, name, and GPA. The registrar's office wants to be able to insert new student records, delete existing records, and display all student records or the details of a specific student.

The requirements for the program's functionality are as follows:
1. The program should allow users to insert new student records into the linked list.
2. The program should allow users to delete a student record by student ID.
3. The program should display all student records in the linked list.
4. The program should display the details of a specific student record by student ID.

A simple example of expected input/output is:
- Inserting a new student record: `insert 12345 John 3.8`
- Deleting a student record: `delete 12345`
- Displaying all student records: `display all`
- Displaying a specific student record: `display 12345`

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (student record).
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.
- The solution must be implemented with a menu-driven interface.
- The menu options should include:
  1. Insert a new student record
  2. Delete a student record
  3. Display all student records
  4. Display a specific student record
  5. EXIT the program

To exit the program, the user must select the `EXIT` option (option 5). The program should continue to run and prompt the user for input until the `EXIT` option is chosen.

---

## Problem 30 - llama-3.3-70b-versatile - Iteration 90
# STEP 1: PROBLEM
In a library management system, books are stored in a shelf and each book has a unique title, author, and publication year. To efficiently manage these books, the library wants to implement a singly linked list data structure to store and retrieve information about the books. Your task is to design a program that can create a singly linked list of books, insert new books, delete existing books, display all books, and search for a specific book.

The library manager wants the program to have the following functionalities:
1. Create a new singly linked list of books.
2. Insert a new book into the list.
3. Delete a book from the list by its title.
4. Display all books in the list.
5. Search for a book by its title and display its details.

Here is a simple example of the expected input/output:
- Input: Insert book "Book1" by "Author1" published in 2020.
- Output: Book "Book1" by "Author1" published in 2020 has been inserted.
- Input: Display all books.
- Output: 
    Book "Book1" by "Author1" published in 2020
    Book "Book2" by "Author2" published in 2021

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (Book).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach, where the user can choose to:
  1. Insert a new book
  2. Delete a book
  3. Display all books
  4. Search for a book
  5. EXIT the program
- The program must include a specific menu option to EXIT the program, which is option 5. When the user chooses option 5, the program should terminate and display a message saying "Thank you for using the library management system."

---

## Problem 31 - llama-3.3-70b-versatile - Iteration 91
# STEP 1: PROBLEM
In a library management system, books are often organized and tracked using a catalog. To efficiently manage this catalog, a singly linked list can be used, where each node represents a book with its details. Your task is to design and implement a simplified library catalog system using a singly linked list.

Background: 
A library wants to create a digital catalog of its books. Each book has a unique identifier (ID), title, author, and publication year. The library staff should be able to add new books to the catalog, remove existing books, display all books, and search for a specific book by its ID.

Requirements:
1. The program should allow users to add a new book to the catalog.
2. The program should allow users to remove a book from the catalog by its ID.
3. The program should display all books in the catalog.
4. The program should be able to search for a specific book by its ID and display its details.

Example Input/Output:
- Adding a book: If a user adds a book with ID "B001", title "Introduction to CS", author "John Doe", and publication year "2020", the system should successfully add this book to the catalog.
- Displaying all books: The system should list all added books with their details.
- Searching for a book: If a user searches for a book by ID "B001", the system should display the book's title, author, and publication year.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of one specific book must be in a function called 'displayBook'.
- The solution must include a menu-driven interface.
- The menu should have the following options:
  1. Add a new book
  2. Remove a book
  3. Display all books
  4. Search for a book by ID
  5. EXIT the program
- To exit the program, the user must choose option 5.

For the menu-driven interface, ensure that the program continuously prompts the user for input until the user chooses to exit. Validate user inputs appropriately to handle potential errors, such as attempting to remove a non-existent book or searching for a book that does not exist in the catalog.

---

## Problem 32 - llama-3.3-70b-versatile - Iteration 92
# STEP 1: PROBLEM
In a university setting, student records are crucial for maintaining and tracking student information. To efficiently manage these records, implementing a data structure such as a Singly Linked List can be beneficial. The goal of this assignment is to design a program that utilizes a Singly Linked List to store and manipulate student records.

Background:
The university wants to create a system that allows for the addition, deletion, and display of student records. Each student record consists of a unique student ID, name, and GPA. The system should be able to handle a dynamic number of student records.

Requirements:
1. The program should allow users to add new student records to the Singly Linked List.
2. The program should allow users to delete a student record by student ID.
3. The program should display all student records in the Singly Linked List.
4. The program should have a menu-driven interface for users to interact with the system.

Example Input/Output:
If the user adds three student records with IDs 1, 2, and 3, the program should display the records as follows:
```
Student ID: 1, Name: John Doe, GPA: 3.5
Student ID: 2, Name: Jane Doe, GPA: 3.8
Student ID: 3, Name: Bob Smith, GPA: 3.2
```
If the user deletes the student record with ID 2, the program should display the updated records as follows:
```
Student ID: 1, Name: John Doe, GPA: 3.5
Student ID: 3, Name: Bob Smith, GPA: 3.2
```

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (student record).
2. Logic for displaying the details of ALL student records must be in a function called 'displayRecords'.
3. The solution must be implemented with a single function besides main() to handle the menu-driven interface and user input.
4. The menu-driven interface must include the following options:
   - Option 1: Add a new student record
   - Option 2: Delete a student record by ID
   - Option 3: Display all student records
   - Option 4: EXIT the program
   The program should exit when the user selects Option 4.

---

## Problem 33 - llama-3.3-70b-versatile - Iteration 93
# STEP 1: PROBLEM
You are a curator at a local museum, and you have been tasked with creating a digital catalog of the museum's collection. The catalog should store information about each artifact, including its name, description, year of creation, and the name of the artist or creator. You have decided to use a singly linked list to store the catalog, where each node represents an artifact.

The museum has a large collection, and the catalog needs to be efficient and easy to use. You want to create a program that allows you to add, remove, and display artifacts in the catalog.

## REQUIREMENTS
The program should have the following functionality:
1. Add an artifact to the catalog: The program should prompt the user to enter the name, description, year of creation, and the name of the artist or creator of the artifact.
2. Remove an artifact from the catalog: The program should prompt the user to enter the name of the artifact to be removed.
3. Display all artifacts in the catalog: The program should display the details of all artifacts in the catalog.
4. Display the details of a specific artifact: The program should prompt the user to enter the name of the artifact and display its details.

## EXAMPLE
Input:
```
Add artifact
Name: Painting
Description: A beautiful painting
Year: 2020
Artist: John Doe
```
Output:
```
Artifact added successfully
```
Input:
```
Display all artifacts
```
Output:
```
Name: Painting
Description: A beautiful painting
Year: 2020
Artist: John Doe
```
### CONSTRAINTS
* The solution must be implemented using a singly linked list.
* The logic for displaying the details of all artifacts must be in a function called `displayAllArtifacts`.
* The logic for displaying the details of a specific artifact must be in a function called `displayArtifact`.
* The program must include a menu with the following options:
	1. Add artifact
	2. Remove artifact
	3. Display all artifacts
	4. Display artifact
	5. EXIT (to exit the program)
* The program must use a `struct` to represent an artifact.

Note: The program should handle invalid inputs and edge cases, such as adding a duplicate artifact or removing an artifact that does not exist.

---

## Problem 34 - llama-3.3-70b-versatile - Iteration 94
# STEP 1: PROBLEM
In a library management system, books are arranged on shelves in a particular order. To efficiently manage the books, the librarian wants to implement a system that uses a singly linked list to store the book details. Each book has a unique identifier (ID), title, author, and publication year. The librarian wants to perform various operations on the list, such as adding a new book, deleting a book, and displaying the details of all books or a specific book.

The library management system should have the following functionalities:
1. Add a new book to the end of the list.
2. Delete a book by its ID.
3. Display all books in the list.
4. Display the details of a specific book by its ID.
5. Exit the program.

### CONSTRAINTS
- Must use a 'struct' to represent a book, with members for ID, title, author, and publication year.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven approach.
- The menu options should be as follows:
  1. Add a new book
  2. Delete a book
  3. Display all books
  4. Display a specific book
  5. Exit the program
- To exit the program, the user should select option 5.

### EXAMPLE
If the user adds the following books:
- Book 1: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
- Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021
- Book 3: ID = 3, Title = "Book3", Author = "Author3", Year = 2022

The output for "Display all books" should be:
Book 1: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021
Book 3: ID = 3, Title = "Book3", Author = "Author3", Year = 2022

The output for "Display a specific book" with ID = 2 should be:
Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021

---

## Problem 35 - llama-3.3-70b-versatile - Iteration 95
# STEP 1: PROBLEM
You are a curator at a local museum, and you need to manage the collection of artifacts. Each artifact has a unique identifier, name, description, and acquisition date. To efficiently store and retrieve information about these artifacts, you decide to implement a singly linked list data structure.

The museum has a large number of artifacts, and the curator wants to be able to add new artifacts, remove existing ones, display the details of a specific artifact, and list all artifacts in the collection. The curator also wants to be able to search for artifacts by name or identifier.

Here are the requirements for the program's functionality:

1. The program must allow the user to add a new artifact to the collection.
2. The program must allow the user to remove an artifact from the collection by its identifier.
3. The program must allow the user to display the details of a specific artifact by its identifier.
4. The program must allow the user to list all artifacts in the collection.
5. The program must allow the user to search for artifacts by name or identifier.

### CONSTRAINTS
- Must use a 'struct' to represent the primary data entity (i.e., the artifact).
- Logic for displaying the details of ONE specific entity must be in a function called 'displayEntity'.
- The solution must be implemented with a single function besides main() to handle all menu options.
- If a menu is implemented, it must include a specific menu option to EXIT the program. The EXIT option must be numbered as '5'.

### EXAMPLE
If the user adds two artifacts with the following details:
- Artifact 1: id = 1, name = "Vase", description = "Ancient Greek vase", acquisition_date = "2020-01-01"
- Artifact 2: id = 2, name = "Painting", description = "Modern art painting", acquisition_date = "2022-01-01"

And then lists all artifacts, the output should be:
```
Artifact 1:
  id: 1
  name: Vase
  description: Ancient Greek vase
  acquisition_date: 2020-01-01

Artifact 2:
  id: 2
  name: Painting
  description: Modern art painting
  acquisition_date: 2022-01-01
```

If the user searches for artifacts by name "Vase", the output should be:
```
Artifact 1:
  id: 1
  name: Vase
  description: Ancient Greek vase
  acquisition_date: 2020-01-01
```

---

## Problem 36 - llama-3.3-70b-versatile - Iteration 96
# STEP 1: PROBLEM
In a library management system, books are arranged on shelves in a particular order. To efficiently manage the collection, the librarian wants to implement a system that uses a singly linked list to store and retrieve book information. Each book has a unique title, author, publication year, and a rating from 1 to 5.

The system should allow the librarian to perform the following operations:
1. Add a new book to the end of the list.
2. Display all books in the list.
3. Search for a book by title and display its details.
4. Remove a book by title from the list.
5. Update the rating of a book.

The librarian wants a simple text-based interface to interact with the system.

### EXAMPLE
If the input is:
```
Add: Book1, Author1, 2020, 4
Add: Book2, Author2, 2019, 3
Display All
Search: Book1
Update: Book1, 5
Display All
Remove: Book1
Display All
```
The output should be:
```
Book1, Author1, 2020, 4
Book2, Author2, 2019, 3
Book1, Author1, 2020, 4
Book1, Author1, 2020, 5
Book2, Author2, 2019, 3
Book2, Author2, 2019, 3
```
### CONSTRAINTS
- Must use a 'struct' to represent the Book entity.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The solution must be implemented with a single linked list.
- The program should have a menu-driven interface with the following options:
  1. Add Book
  2. Display All Books
  3. Search Book
  4. Remove Book
  5. Update Book
  6. EXIT
- The program should exit when the user chooses the 'EXIT' option (option 6).

---

## Problem 37 - llama-3.3-70b-versatile - Iteration 97
# STEP 1: PROBLEM
You are a software engineer at a library, tasked with designing a system to manage the catalog of books. The system should utilize a singly linked list to store information about each book, including the title, author, publication year, and genre. The system should allow users to add new books, remove existing books, display all books, and search for a specific book by title.

## Background and Context
The library currently uses a manual system to keep track of its catalog, which is time-consuming and prone to errors. The new system should improve efficiency and reduce the likelihood of mistakes.

## Requirements
1. The system should store information about each book in a singly linked list.
2. The system should allow users to add new books to the catalog.
3. The system should allow users to remove existing books from the catalog.
4. The system should display all books in the catalog.
5. The system should allow users to search for a specific book by title.

## Example Input/Output
Example Input:
- Add a new book: "To Kill a Mockingbird" by Harper Lee, published in 1960, genre: Classic
- Remove a book: "1984" by George Orwell
- Display all books
- Search for a book: "Pride and Prejudice"

Example Output:
- The book "To Kill a Mockingbird" has been added to the catalog.
- The book "1984" has been removed from the catalog.
- Displaying all books:
  - "To Kill a Mockingbird" by Harper Lee, published in 1960, genre: Classic
  - "Pride and Prejudice" by Jane Austen, published in 1813, genre: Romance
- The book "Pride and Prejudice" is found in the catalog.

### CONSTRAINTS
1. Must use a 'struct' to represent the primary data entity (Book).
2. Logic for displaying the details of ONE specific entity must be in a function called 'displayBook'.
3. The solution must be implemented with a single function besides main() to handle user input and interactions.
4. If a menu is implemented:
   - Must include a specific menu option to EXIT the program, which is option 6, labeled as "EXIT".
   - The menu should be as follows:
     1. Add a new book
     2. Remove a book
     3. Display all books
     4. Search for a book
     5. Display book details
     6. EXIT

---

## Problem 38 - llama-3.3-70b-versatile - Iteration 98
# STEP 1: PROBLEM
As a librarian, you want to create a simple system to manage books in your library. You have decided to use a Singly Linked List to store the book information. Each book has a unique identifier (ID), title, author, and publication year. 

You need to design a program that allows you to add, remove, and display books in the library. The program should also have a menu-driven interface to make it user-friendly.

Here are the requirements for the program's functionality:
1. The program should allow users to add a new book to the library.
2. The program should allow users to remove a book from the library by its ID.
3. The program should allow users to display all books in the library.
4. The program should allow users to search for a book by its ID and display its details.
5. The program should have a menu-driven interface with options to add, remove, display all books, search for a book, and exit the program.

### EXAMPLE
If the library has the following books:
- Book 1: ID = 1, Title = "Book1", Author = "Author1", Year = 2020
- Book 2: ID = 2, Title = "Book2", Author = "Author2", Year = 2021
- Book 3: ID = 3, Title = "Book3", Author = "Author3", Year = 2022

The program should be able to add a new book, remove a book by its ID, display all books, and search for a book by its ID.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The program must be implemented using a Singly Linked List.
- The menu-driven interface should have the following options:
  1. Add a new book
  2. Remove a book by ID
  3. Display all books
  4. Search for a book by ID
  5. EXIT the program

Note: The program should exit when the user chooses option 5 (EXIT).

---

## Problem 39 - llama-3.3-70b-versatile - Iteration 99
# STEP 1: PROBLEM
In a small library, the librarian wants to manage a collection of books using a singly linked list. Each book has a unique title, author, and publication year. The librarian needs a program to add, remove, and display books in the collection.

Background:
The library has a growing collection of books, and the current system for tracking them is becoming cumbersome. The librarian wants a simple program to manage the collection, allowing for easy addition and removal of books, as well as the ability to display the details of all books or a specific book.

Requirements:
1. The program must allow the user to add a new book to the collection.
2. The program must allow the user to remove a book from the collection by title.
3. The program must display the details of all books in the collection.
4. The program must display the details of a specific book by title.

Example:
Input: 
- Add book: "To Kill a Mockingbird" by Harper Lee, published in 1960
- Add book: "1984" by George Orwell, published in 1949
- Display all books
- Remove book: "To Kill a Mockingbird"
- Display all books

Output:
- After adding books: 
  - "To Kill a Mockingbird" by Harper Lee, published in 1960
  - "1984" by George Orwell, published in 1949
- After removing "To Kill a Mockingbird": 
  - "1984" by George Orwell, published in 1949

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of all books must be in a function called 'displayAllBooks'.
- Logic for displaying the details of a specific book must be in a function called 'displayBook'.
- The solution must be implemented with a menu-driven interface.
- The menu must include the following options:
  1. Add a book
  2. Remove a book
  3. Display all books
  4. Display a specific book
  5. EXIT (to exit the program)
- If a menu is implemented, the program must exit when the user chooses option 5 (EXIT).

---

## Problem 40 - llama-3.3-70b-versatile - Iteration 100
# STEP 1: PROBLEM
You are the curator of a university's library, and you want to implement a system to keep track of the books in the library. The system should be able to store the title, author, publication year, and the status (available or borrowed) of each book. You decide to use a singly linked list to store the book information.

The library currently has a collection of books, and you want to create a program that can add, remove, and display the details of the books in the library. The program should also be able to change the status of a book from available to borrowed and vice versa.

### REQUIREMENTS
The program should have the following functionality:
1. Add a new book to the library.
2. Remove a book from the library.
3. Display the details of all the books in the library.
4. Display the details of a specific book.
5. Change the status of a book from available to borrowed or vice versa.

### EXAMPLE
If the library has the following books:
- Book 1: Title - "Introduction to CS", Author - "John Smith", Publication Year - 2010, Status - Available
- Book 2: Title - "Data Structures", Author - "Jane Doe", Publication Year - 2015, Status - Borrowed

The program should be able to add a new book, remove an existing book, display all the books, display a specific book, and change the status of a book.

### CONSTRAINTS
- Must use a 'struct' to represent a book.
- Logic for displaying the details of ONE specific book must be in a function called 'displayBook'.
- The program should have a menu-driven interface with the following options:
  - 1: Add a new book
  - 2: Remove a book
  - 3: Display all books
  - 4: Display a specific book
  - 5: Change the status of a book
  - 6: EXIT the program
- The solution must be implemented using a singly linked list.

Note: The program should handle cases where a book is not found in the library, and it should also handle cases where the library is empty.

---

## Problem 41 - openai/gpt-oss-120b - Iteration 61
# STEP 1: PROBLEM  

## Background  
Captain Ada has just discovered a series of ancient treasure chests scattered along a deserted island. Each chest is identified by a **unique integer ID**, contains a **description** (a short string, max 30 characters), and holds a **value** measured in gold coins (an integer).  

Because the island is constantly shifting, the order in which the chests are found matters – the first chest discovered should be the first one examined, the second chest the next, and so on.  
You have been hired to write a small program that lets the crew **record**, **inspect**, and **remove** chests using a **singly linked list**.

## Requirements  

Write a console program that provides a menu‑driven interface with the following options:

1. **Add a new chest** – Prompt the user for the chest’s ID, description, and value, then insert the chest at the **end** of the linked list.  
2. **Display all chests** – Traverse the list and print each chest’s ID, description, and value in the order they were added.  
3. **Search for a chest by ID** – Ask for an ID, locate the first chest with that ID, and display its details using a dedicated function `displayChest`. If the ID is not found, print “Chest not found.”  
4. **Remove a chest by ID** – Ask for an ID, delete the first node whose ID matches the given ID, and free its memory. If the ID does not exist, print “Chest not found; nothing removed.”  
5. **Exit** – Terminate the program gracefully.

The program should continue to show the menu after completing any operation until the user selects **Exit**.

## Example Input / Output  

```
=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 1

Enter chest ID: 101
Enter description: Emerald Crown
Enter value (gold coins): 2500
Chest added.

=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 1

Enter chest ID: 202
Enter description: Silver Sword
Enter value (gold coins): 1500
Chest added.

=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 2

Chest ID: 101 | Description: Emerald Crown | Value: 2500
Chest ID: 202 | Description: Silver Sword   | Value: 1500

=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 3

Enter ID to search: 202
Chest ID: 202 | Description: Silver Sword | Value: 1500

=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 4

Enter ID to remove: 101
Chest with ID 101 removed.

=== Treasure Chest Manager ===
1. Add chest
2. Display all chests
3. Search chest by ID
4. Remove chest by ID
5. Exit
Choose an option: 5

Good‑bye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary data entity (a treasure chest) **must be represented with a `struct`** (or equivalent record type in the chosen language) containing at least the fields `id` (int), `description` (char array / string), and `value` (int).  
- **Linked List**: The collection of chests **must be stored as a singly linked list**; using arrays, vectors, or other container classes for the main storage is not allowed.  
- **Display Function**: The logic for showing the details of **ONE specific chest** must reside in a function named `displayChest` (or `display_entity` if your language does not allow that exact name). This function takes a pointer/reference to a chest node and prints its fields in the format shown in the example.  
- **Menu Option for Exit**: The menu **must include a dedicated option to EXIT the program** (option 5 in the example). Selecting this option must terminate the program without performing any further list operations.  
- **Memory Management**: All dynamically allocated nodes must be freed appropriately when removed or when the program exits.  
- **No Global Variables**: All list pointers (e.g., head) must be passed to functions or managed within `main`; using global variables for the list is prohibited.  

*Feel free to implement the solution in C, C++, Java, or any language that supports explicit struct/record definitions and manual memory handling.*

---

## Problem 42 - openai/gpt-oss-120b - Iteration 62
# STEP 1: PROBLEM  

## Background  
The campus library wants a simple command‑line tool that lets a student assistant keep track of the books that are currently on loan. Because the assistant is only learning the basics of dynamic data structures, the program must use a **singly linked list** to store the information for each book.  

## Requirements  

Write a C (or C++) program that implements a singly linked list to manage a collection of books. The program must provide a text‑based menu that allows the user to perform the following operations:

1. **Add a new book** – Prompt for the book’s ISBN (string, up to 13 characters), title, and author, then insert the new node at the **end** of the list.  
2. **Remove a book** – Prompt for an ISBN and delete the first node whose ISBN matches. If the ISBN is not found, display an appropriate message.  
3. **Search for a book** – Prompt for an ISBN and display the details of the matching book (title and author). If the ISBN is not found, inform the user.  
4. **Display all books** – Traverse the list and print the ISBN, title, and author of every stored book in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully.  

The program should continue to display the menu after each operation until the user chooses the exit option.

## Example Input / Output  

```
=== Library Loan Tracker ===
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) Exit
Select an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added successfully.

=== Library Loan Tracker ===
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) Exit
Select an option: 4

Current books on loan:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Loan Tracker ===
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) Exit
Select an option: 3

Enter ISBN to search: 9780131103627
Book found:
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Library Loan Tracker ===
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) Exit
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Data Representation** – The primary entity (a book) must be represented with a `struct` (or `class` if using C++) named `BookNode` that contains at least the fields `isbn`, `title`, `author`, and a pointer to the next node.  
* **Function Naming** – The logic for displaying the details of **one specific book** (used by the search operation) must be placed in a function called `displayBook(const BookNode *node)`.  
* **Menu Requirement** – The menu must include an explicit option to **EXIT** the program; in the example it is option `5`. The program must not terminate until this option is chosen.  
* **Memory Management** – All dynamically allocated nodes must be freed before program termination (i.e., when exiting).  
* **Single‑File Implementation** – Apart from `main()`, you may create additional helper functions, but the core linked‑list operations (insert, delete, search, display) should each be encapsulated in their own function for clarity.  

Your solution should compile without warnings and behave exactly as described above.

---

## Problem 43 - openai/gpt-oss-120b - Iteration 63
# STEP 1: PROBLEM  

## Background  
The campus library wants a very lightweight command‑line tool to keep track of the books that are currently on loan.  
Each book is identified by its **ISBN** (a 13‑digit number) and also stores the **title** and the **author’s name**.  
The library staff will run the program, repeatedly choosing actions from a menu (add a new loan, return a book, look up a book, list all loans, or quit).  

You are to implement this tool using a **singly linked list** where each node represents one loaned book.

## Requirements  

Your program must provide the following functionality:

1. **Add a new loan** – Prompt the user for ISBN, title, and author, then insert a new node at the **end** of the list.  
2. **Return a book** – Prompt for an ISBN and remove the corresponding node from the list. If the ISBN is not found, display an appropriate message.  
3. **Search for a book** – Prompt for an ISBN and display the details of that book using the dedicated display function (see constraints). If the ISBN is not present, inform the user.  
4. **List all current loans** – Traverse the list and display every stored book in the order they were added.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.  

All interactions must occur through a simple numeric menu displayed after each completed operation.

## Example Input / Output  

```
=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Search for a book
4. List all loans
0. EXIT
Choose an option: 1

Enter ISBN (13 digits): 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added successfully!

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Search for a book
4. List all loans
0. EXIT
Choose an option: 4

Current loans:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Search for a book
4. List all loans
0. EXIT
Choose an option: 2

Enter ISBN to return: 9780131103627
Book returned successfully!

=== Library Loan Tracker ===
1. Add a new loan
2. Return a book
3. Search for a book
4. List all loans
0. EXIT
Choose an option: 0

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity must be represented with a `struct` named `Book`. It must contain at least the following members:  
   ```c
   typedef struct Book {
       char isbn[14];      // 13 digits + terminating null
       char title[100];
       char author[100];
       struct Book *next;
   } Book;
   ```
2. **Display Function** – The logic for showing the details of **one specific book** must reside in a function with the exact prototype:  
   ```c
   void displayBook(const Book *b);
   ```
   This function should print the ISBN, title, and author on a single line as shown in the example.  

3. **Modular Operations** – Apart from `main`, you must implement **exactly three** additional functions with the following prototypes (no more, no fewer):  
   ```c
   void insertBook(Book **head);
   void deleteBook(Book **head);
   void searchBook(const Book *head);
   ```
   Each function must handle the user prompts, input validation, and the required list manipulation for its operation.  

4. **Memory Management** – All nodes must be allocated with `malloc` (or `new` if using C++) and freed appropriately when a book is returned or when the program exits.  

5. **Menu Requirement** – The program must present a menu that includes a clearly labeled option to **EXIT** the program. The exit option must be either `0` or the keyword `EXIT` (state which you choose). Selecting this option ends the loop and frees any remaining list nodes before termination.  

6. **Language** – The solution must be written in **C** (or C++ if you prefer, but the `struct` and function signatures above must be preserved).  

7. **No Global Variables** – All list pointers must be passed to functions; do not use global variables to store the head of the list.  

Follow these constraints exactly; the grading rubric will check for compliance before evaluating correctness.

---

## Problem 44 - openai/gpt-oss-120b - Iteration 64
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  Each book in the collection is identified by an ISBN (a 13‑digit integer), has a title (a single‑word string for simplicity), and a number of copies currently on the shelf.  The library staff wants a small console application that lets them **add**, **remove**, **search**, and **list** books while the program is running.  Because the list of books can grow and shrink dynamically, the staff has been told to store the collection in a **singly linked list**.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data representation**  
   * Define a `struct` named `Book` that contains:  
     - `long long isbn;`   // 13‑digit ISBN (use `long long` to hold it)  
     - `char title[51];`   // title, up to 50 characters, no spaces (single word)  
     - `int copies;`       // number of copies on the shelf  
   * Define a `struct` named `Node` that holds a `Book` and a pointer to the next `Node`.

2. **Menu‑driven interface** (displayed repeatedly until the user chooses to exit)  
   1. **Add a new book** – Prompt for ISBN, title, and copies, then insert the new node at the **head** of the list.  
   2. **Delete a book** – Prompt for an ISBN; if a node with that ISBN exists, remove it from the list and free its memory. If not found, print “Book not found.”  
   3. **Search for a book** – Prompt for an ISBN; if found, display its details using the function `displayBook`. If not, print “Book not found.”  
   4. **List all books** – Traverse the list from head to tail and display each book’s details (again using `displayBook`). If the list is empty, print “No books in the system.”  
   5. **Exit** – Terminate the program gracefully.  

3. **Helper function**  
   * Implement a function `void displayBook(const Book *b);` that prints a single book in the format:  
     `ISBN: <isbn>, Title: <title>, Copies: <copies>`  

4. **Memory management**  
   * All nodes must be allocated with `malloc` (or `new` in C++) and freed when removed or when the program exits.

5. **User interaction**  
   * After each operation (except Exit), the menu should be shown again.  
   * Input may be assumed to be well‑formed (e.g., the user enters an integer where required).

## Example  

```
=== Library Book Manager ===
1. Add a book
2. Delete a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: CProgramming
Enter copies: 3
Book added.

=== Library Book Manager ===
1. Add a book
2. Delete a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 4
ISBN: 9780131103627, Title: CProgramming, Copies: 3

=== Library Book Manager ===
1. Add a book
2. Delete a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 3
Enter ISBN to search: 9780131103627
ISBN: 9780131103627, Title: CProgramming, Copies: 3

=== Library Book Manager ===
1. Add a book
2. Delete a book
3. Search for a book
4. List all books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

* The primary data entity **must** be represented with a `struct` named `Book`.  
* The linked‑list node **must** be a separate `struct` named `Node` that contains a `Book` and a `Node* next`.  
* The logic for displaying the details of **one** specific book **must** be placed in a function called `displayBook`.  
* The program **must** be menu‑driven and **must** include an explicit menu option to **EXIT** the program (option 5 in the example).  
* No global variables may be used to store the head of the list; the head pointer should be passed to functions as needed (or kept static inside `main`).  

*Optional additional constraint for extra credit:* implement the list insertion such that the list remains **sorted in ascending order of ISBN** instead of always inserting at the head. (The basic requirement does not require sorting.)  

---

## Problem 45 - openai/gpt-oss-120b - Iteration 65
# STEP 1: PROBLEM  

**Background**  
The campus bookstore wants a simple command‑line inventory system to keep track of the titles it has on hand for the current semester. Because the list of titles changes frequently (new arrivals, removed out‑of‑stock books, etc.), the store’s manager has asked you to implement the inventory using a **singly linked list**. Each node will store information about a single book.

**Program Requirements**  

Write a C (or C++) program that provides a menu‑driven interface for the following operations:

1. **Add a new book** – Insert the new book at the **head** of the list.  
2. **Remove a book by ISBN** – Search the list for a node whose ISBN matches the user‑supplied value and delete that node (if found).  
3. **Search for a book by title** – Print the details of the first book whose title contains the exact search string (case‑sensitive).  
4. **Display the entire inventory** – Traverse the list and print the details of every book in order from head to tail.  
5. **Exit** – Terminate the program.

Each book must store the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `title` | string (max 100 chars) | The title of the book |
| `author` | string (max 50 chars) | Author’s name |
| `isbn` | string (13 characters, may include hyphens) | Unique identifier |
| `price` | float | Retail price in dollars |

**Input / Output Example**

```
=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 1

Enter title: Data Structures in C
Enter author: Jane Doe
Enter ISBN: 978-0134093413
Enter price: 59.99
Book added successfully!

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 4

--- Inventory ---
Title : Data Structures in C
Author: Jane Doe
ISBN  : 978-0134093413
Price : $59.99
-----------------

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 5

Goodbye!
```

**Additional Constraints**

### CONSTRAINTS
- The primary data entity **must be defined as a `struct`** named `BookNode` (or equivalent) that contains the book fields *and* a pointer to the next node.
- The logic for displaying the details of **ONE specific book** (used by the search operation) **must be placed in a function called `displayBook`** that takes a pointer to a `BookNode` as its only argument.
- The program must be **menu‑driven** and **must include an explicit EXIT option** (option number 5 in the example) that cleanly terminates the program.
- All dynamic memory allocations must be checked for success; any failure should result in an error message and program termination.
- No global variables may be used to store the head of the list; the head pointer should be passed to functions as needed (or managed within `main`).  

Implement the program according to the specifications above.

---

## Problem 46 - openai/gpt-oss-120b - Iteration 66
# STEP 1: PROBLEM  

**Background**  
The local history museum is digitizing its collection of artifacts. Each artifact has a unique integer **ID**, a short **name**, and the **year** it was created. The museum staff wants a tiny console program that lets them maintain a **singly‑linked list** of artifacts while they are entering data, correcting mistakes, or looking up a particular piece.

Your task is to write that program.

---

## Requirements  

Your program must provide a **menu‑driven interface** (text only) that allows the user to perform the following operations:

1. **Add a new artifact to the end of the list**  
   - Prompt for `ID`, `name`, and `year`.  
   - Insert the new node as the last element.

2. **Insert an artifact at a specific position**  
   - Prompt for the 1‑based position (e.g., `1` = beginning).  
   - Prompt for `ID`, `name`, and `year`.  
   - If the position is larger than the current length + 1, print an error and return to the menu.

3. **Delete an artifact by its ID**  
   - Prompt for the `ID`.  
   - Remove the first node whose `ID` matches.  
   - If no such node exists, print a message indicating that the artifact was not found.

4. **Display all artifacts**  
   - Print each artifact on a separate line in the order they appear in the list, showing `ID`, `name`, and `year`.

5. **Display the details of ONE specific artifact**  
   - Prompt for the `ID`.  
   - Locate the node and print its information.  
   - If the artifact is not in the list, inform the user.

6. **Exit the program**  
   - Selecting this option terminates the program gracefully.

The menu must be displayed after each operation (except when exiting).  

All input is entered via `stdin`; all output must be written to `stdout`.

---

## Example Interaction  

```
===== Museum Artifact Tracker =====
1. Add artifact at end
2. Insert artifact at position
3. Delete artifact by ID
4. Display all artifacts
5. Display artifact by ID
6. Exit
Choose an option: 1
Enter ID: 101
Enter name: Bronze Statue
Enter year: 1500
Artifact added.

===== Museum Artifact Tracker =====
1. Add artifact at end
2. Insert artifact at position
3. Delete artifact by ID
4. Display all artifacts
5. Display artifact by ID
6. Exit
Choose an option: 1
Enter ID: 202
Enter name: Ceramic Vase
Enter year: 1802
Artifact added.

===== Museum Artifact Tracker =====
1. Add artifact at end
2. Insert artifact at position
3. Delete artifact by ID
4. Display all artifacts
5. Display artifact by ID
6. Exit
Choose an option: 4
Artifacts in collection:
ID: 101 | Name: Bronze Statue | Year: 1500
ID: 202 | Name: Ceramic Vase   | Year: 1802

===== Museum Artifact Tracker =====
1. Add artifact at end
2. Insert artifact at position
3. Delete artifact by ID
4. Display all artifacts
5. Display artifact by ID
6. Exit
Choose an option: 5
Enter ID to display: 202
ID: 202 | Name: Ceramic Vase | Year: 1802

===== Museum Artifact Tracker =====
1. Add artifact at end
2. Insert artifact at position
3. Delete artifact by ID
4. Display all artifacts
5. Display artifact by ID
6. Exit
Choose an option: 6
Goodbye!
```

---

### CONSTRAINTS  

1. **Data Representation** – The artifact must be represented with a `struct` (or equivalent record type) containing at least the fields `int id; char name[64]; int year; struct Node *next;`.  

2. **Function Requirement** – The logic for displaying the details of ONE specific artifact **must** be placed in a function named `displayArtifact`. This function takes the head pointer of the list and the target `ID` as parameters and prints the artifact or an appropriate “not found” message.  

3. **Menu Implementation** – The program must present a textual menu as described, and **must include a menu option to EXIT the program** (option 6 in the example). Selecting this option ends the program.  

4. **Memory Management** – All nodes that are removed must be freed, and any allocated memory must be released before program termination.  

5. **Standard Library Only** – You may only use the language’s standard library (e.g., `<stdio.h>`, `<stdlib.h>`, `<string.h>` for C). No third‑party containers or list implementations are allowed.  

---  

*Write a program that satisfies the above specifications. The focus is on correctly implementing a singly‑linked list and exercising basic dynamic‑memory operations.*

---

## Problem 47 - openai/gpt-oss-120b - Iteration 67
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  The librarian wants a tiny command‑line tool that can keep track of **books** while the students are learning how to implement a singly linked list.  Each book has a **title**, an **author**, and a **unique integer ID**.  The tool will allow the user to add new books, remove a book by its ID, search for a book, and list all books currently stored.

## Requirements  
Write a C program that implements a **singly linked list** to store the books.  The program must provide the following functionality:

1. **Add a Book** – Prompt the user for the book’s ID (int), title (string, up to 50 characters), and author (string, up to 50 characters).  Insert the new node at the **end** of the list.  
2. **Delete a Book** – Prompt for a book ID and remove the node with that ID.  If the ID does not exist, print a friendly message.  
3. **Search for a Book** – Prompt for a book ID and display the book’s details if found; otherwise report that the book is not in the list.  
4. **Display All Books** – Traverse the list from head to tail and print each book’s ID, title, and author on a separate line.  
5. **Exit** – End the program gracefully, freeing any allocated memory.

The program should present a **menu** after each operation, allowing the user to choose the next action.

## Example Input / Output  

```
--- Library Book Manager ---
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. EXIT
Choose an option: 1

Enter Book ID: 101
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added.

--- Library Book Manager ---
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. EXIT
Choose an option: 1

Enter Book ID: 202
Enter Title: Introduction to Algorithms
Enter Author: Cormen et al.
Book added.

--- Library Book Manager ---
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. EXIT
Choose an option: 4

ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie
ID: 202 | Title: Introduction to Algorithms | Author: Cormen et al.

--- Library Book Manager ---
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. EXIT
Choose an option: 3

Enter Book ID to search: 202
ID: 202 | Title: Introduction to Algorithms | Author: Cormen et al.

--- Library Book Manager ---
1. Add a Book
2. Delete a Book
3. Search for a Book
4. Display All Books
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Data Structure** – The primary entity must be represented with a `struct` named `BookNode` containing:
  * `int id;`
  * `char title[51];`   // space for null terminator  
  * `char author[51];`  
  * `struct BookNode *next;`

* **Function Naming** –  
  * The logic for displaying the details of **one specific book** (used by both *Search* and *Display All*) **must** be placed in a function with the exact prototype:  
    ```c
    void displayBook(const BookNode *node);
    ```
  * All other list operations (add, delete, search, free) should each be implemented in their own separate functions (you may choose appropriate names).

* **Menu Requirement** – If a menu is implemented (as required above), it **must** include an explicit option to **EXIT** the program. The option number must be `5` (as shown in the example) and selecting it should terminate the program after freeing all allocated memory.

* **Memory Management** – No memory leaks are allowed. Every node allocated with `malloc`/`calloc` must be freed before program termination.

* **Standard Library Only** – You may only use headers from the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No third‑party libraries.

* **Compilation** – The program must compile without warnings using `gcc -Wall -Wextra -pedantic`.

---  

*Write the program according to the specifications above.*

---

## Problem 48 - openai/gpt-oss-120b - Iteration 68
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its book‑tracking system.  Each book is identified by an ISBN, has a title, and a flag indicating whether it is currently checked out.  The library wants a simple console program that stores the collection of books in a **singly linked list** so that librarians can add new books, remove books that are withdrawn, and query the status of a particular book.

## Requirements  
Write a C (or C++) program that implements the following functionality:

1. **Add a Book** – Prompt the user for ISBN (string, up to 13 characters), title (string, up to 50 characters), and status (`0` = available, `1` = checked‑out). Insert the new book at the **head** of the linked list.  
2. **Remove a Book** – Prompt for an ISBN. If a node with that ISBN exists, delete it from the list and free its memory; otherwise display “Book not found”.  
3. **Search a Book** – Prompt for an ISBN and display all details of the matching book. If the book does not exist, display “Book not found”.  
4. **List All Books** – Traverse the list and print the ISBN, title, and status of every stored book in the order they appear in the list.  
5. **Exit** – Terminate the program gracefully.

The program must present a **menu** that repeats until the user chooses the Exit option.

## Example Input / Output  

```
=== Library Book Manager ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
5) Exit
Select an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Status (0=available, 1=checked-out): 0
Book added.

=== Library Book Manager ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
5) Exit
Select an option: 4

Books in collection:
ISBN: 9780131103627 | Title: The C Programming Language | Status: Available

=== Library Book Manager ===
1) Add Book
2) Remove Book
3) Search Book
4) List All Books
5) Exit
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must be represented with a `struct`** named `BookNode` that contains the ISBN, title, status, and a pointer to the next node.  
- The logic for displaying the details of **one specific book** (used by the Search operation) **must be placed in a function called `displayBook`** with the prototype `void displayBook(const BookNode *node);`.  
- The program **must include a menu option to EXIT the program**; option **5** (or the keyword `EXIT`) is reserved for this purpose.  
- No global variables may be used to store the head of the list; the head pointer must be passed to functions as needed.  

Implement the program according to the above specifications.

---

## Problem 49 - openai/gpt-oss-120b - Iteration 69
# STEP 1: PROBLEM  

## Background  
The campus computer lab maintains a simple inventory of **borrowable equipment** (e.g., laptops, tablets, projectors).  The inventory is small enough that a dynamic, linear data structure is sufficient, but it must support frequent additions and removals as equipment is checked in and out.  

You have just learned how to implement a **singly linked list** in C (or C‑like pseudocode).  Your task is to write a program that stores each piece of equipment as a node in a singly linked list and provides a menu‑driven interface for the lab manager to manipulate the list.

## Requirements  

Your program must implement the following functionality:

1. **Add Equipment** – Prompt the user for the equipment’s *ID* (integer), *type* (string, max 30 characters), and *status* (`available` or `checked‑out`). Insert the new node at the **end** of the list.  
2. **Remove Equipment** – Prompt for an *ID* and delete the node with that ID, if it exists. If the ID is not found, display an appropriate message.  
3. **Search Equipment** – Prompt for an *ID* and display the details of that equipment (using the required `displayEquipment` function). If not found, inform the user.  
4. **List All Equipment** – Traverse the list and display every equipment record in the order they were added.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.  

The program must present a **menu** that repeatedly asks the user to choose one of the above actions.

## Example Input / Output  

```
=== Equipment Inventory Menu ===
1. Add Equipment
2. Remove Equipment
3. Search Equipment
4. List All Equipment
5. Exit
Enter choice: 1

Enter Equipment ID: 101
Enter Type (max 30 chars): Laptop
Enter Status (available/checked-out): available
Equipment added.

=== Equipment Inventory Menu ===
1. Add Equipment
2. Remove Equipment
3. Search Equipment
4. List All Equipment
5. Exit
Enter choice: 1

Enter Equipment ID: 202
Enter Type (max 30 chars): Projector
Enter Status (available/checked-out): checked-out
Equipment added.

=== Equipment Inventory Menu ===
1. Add Equipment
2. Remove Equipment
3. Search Equipment
4. List All Equipment
5. Exit
Enter choice: 4

--- All Equipment ---
ID: 101 | Type: Laptop      | Status: available
ID: 202 | Type: Projector   | Status: checked-out

=== Equipment Inventory Menu ===
1. Add Equipment
2. Remove Equipment
3. Search Equipment
4. List All Equipment
5. Exit
Enter choice: 3

Enter Equipment ID to search: 202
ID: 202 | Type: Projector | Status: checked-out

=== Equipment Inventory Menu ===
1. Add Equipment
2. Remove Equipment
3. Search Equipment
4. List All Equipment
5. Exit
Enter choice: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**:  
  - You **must** define a `struct` named `Equipment` (or equivalent) that contains at least the fields `id` (int), `type` (char array), `status` (char array), and a pointer to the next node.  

- **Function Requirement**:  
  - The logic for displaying the details of **ONE specific equipment record** must be placed in a function with the exact prototype:  
    ```c
    void displayEquipment(const Equipment *node);
    ```  

- **Menu Implementation**:  
  - The menu must include an option to **EXIT** the program. The exit option must be clearly numbered (as shown in the example) and selecting it should terminate the loop and free all allocated memory.  

- **Memory Management**:  
  - All nodes must be allocated dynamically (e.g., using `malloc`/`new`). Before program termination, every allocated node must be freed to avoid memory leaks.  

- **Single‑File Restriction** *(optional but recommended for this assignment)*:  
  - All code should reside in a single source file (e.g., `inventory.c`). Apart from `main()`, you may create additional helper functions, but the core list operations (insert, delete, search, display) should each be encapsulated in their own functions.  

- **Input Validation**:  
  - The program should handle invalid menu choices gracefully by re‑displaying the menu.  
  - When prompting for the status, accept only the exact strings `available` or `checked-out`; otherwise, re‑prompt the user.  

---  

*Deliverables*: Submit the complete source code file that compiles without warnings and behaves as described above.

---

## Problem 50 - openai/gpt-oss-120b - Iteration 70
# STEP 1: PROBLEM  

**Background**  
The campus bookstore wants a simple command‑line tool to keep track of the books that are currently on loan to students. Each book record contains a unique ISBN, the title, and the name of the student who borrowed it. The store’s IT intern has just learned how to build a **singly linked list** and has been asked to implement a small program that can add, remove, and query these loan records.

**Program Requirements**  

1. **Data Representation**  
   - Define a `struct` named `BookNode` that stores the following fields:  
     - `char isbn[14];`   // 13‑digit ISBN plus terminating null  
     - `char title[101];` // up to 100 characters + null  
     - `char borrower[51];` // up to 50 characters + null  
     - `BookNode *next;`   // pointer to the next node  

2. **Menu‑Driven Interface** (the program must present a menu after each operation)  
   - **1. Add a new loan record** – Prompt for ISBN, title, and borrower name, then insert the new node at the **head** of the list.  
   - **2. Return a book** – Prompt for an ISBN; if a node with that ISBN exists, remove it from the list and free its memory. If not found, display an appropriate message.  
   - **3. Find a loan record** – Prompt for an ISBN; if found, display the full details of that book using a function called `displayBook`. If not found, inform the user.  
   - **4. List all current loans** – Traverse the list and display each record (use `displayBook` for each node).  
   - **0. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **Input/Output**  
   - All input is read from `stdin`; all output is written to `stdout`.  
   - The menu should be clear and repeat after each completed operation (except after choosing EXIT).  

4. **Error Handling**  
   - The program must handle attempts to add a record with an ISBN that already exists by rejecting the insertion and notifying the user.  
   - Removing or searching for a non‑existent ISBN must not crash the program.  

**Example Interaction**  

```
--- Library Loan Manager ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
0) EXIT
Choose an option: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter borrower name: Alice Johnson
Loan added.

--- Library Loan Manager ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
0) EXIT
Choose an option: 4
ISBN: 9780131103627
Title: The C Programming Language
Borrower: Alice Johnson

--- Library Loan Manager ---
1) Add loan
2) Return book
3) Find loan
4) List all loans
0) EXIT
Choose an option: 0
Goodbye!
```

### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented with a `struct` named `BookNode` as described above.  
- **Display Function** – The logic for printing the details of **ONE** specific book record must reside in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
- **Function Count** – Apart from `main()`, the solution may contain **only two** additional functions: `displayBook` and a helper function of your choice (e.g., for node deletion). No other user‑defined functions are allowed.  
- **Menu Exit Option** – The menu must include an explicit option `0` (or the keyword `EXIT`) that terminates the program, as shown in the example.  

Implement the program in C (or C++) adhering to the constraints above.

---

## Problem 51 - openai/gpt-oss-120b - Iteration 71
# STEP 1: PROBLEM  

**Background**  
The campus radio station keeps a running log of every song it plays during the day. Each entry in the log records the **song title**, the **artist name**, and the **duration in seconds**. The station wants a simple console program that allows a student volunteer to maintain this log while the station is on‑air. Because the number of songs played is not known in advance and songs are constantly added or removed, a **singly linked list** is the most appropriate data structure.

**Your task** is to write a menu‑driven C (or C++) program that implements the song log using a singly linked list. The program must let the user insert new songs, delete songs, search for a song, and display the whole list.  

---

## Requirements  

1. **Data representation**  
   - Define a `struct Song` (or `class Song` with public members) that contains:  
     - `char title[64];`  
     - `char artist[64];`  
     - `int duration;`   // in seconds  
     - a pointer to the next `Song` node.  

2. **Menu options** (displayed repeatedly until the user chooses to quit)  
   1. **Add a song to the end of the log** – Prompt for title, artist, and duration, then append a new node.  
   2. **Remove a song by title** – Prompt for a title; delete the first node whose title matches (case‑sensitive). If no such song exists, print a message.  
   3. **Search for a song by title** – Prompt for a title; if found, display the song’s details using the required `displaySong` function (see Constraints). If not found, report it.  
   4. **Display the entire log** – Traverse the list from head to tail, printing each song’s details on its own line.  
   5. **Exit** – Terminate the program. *(This option must be explicitly numbered as “5. Exit”.)*  

3. **Input validation**  
   - The program should handle an empty list gracefully (e.g., trying to delete or display when the list is empty should not crash).  
   - Duration must be a positive integer; if the user enters a non‑positive value, re‑prompt.  

4. **Memory management**  
   - Allocate each new node dynamically.  
   - Free the memory of a node when it is removed.  
   - Before program termination, free any remaining nodes to avoid leaks.  

---

## Example Interaction  

```
=== Radio Song Log ===
1. Add a song
2. Remove a song by title
3. Search for a song by title
4. Display the entire log
5. Exit
Choose an option: 1

Enter song title: Yesterday
Enter artist name: The Beatles
Enter duration (seconds): 125
Song added.

=== Radio Song Log ===
1. Add a song
2. Remove a song by title
3. Search for a song by title
4. Display the entire log
5. Exit
Choose an option: 1

Enter song title: Imagine
Enter artist name: John Lennon
Enter duration (seconds): 183
Song added.

=== Radio Song Log ===
1. Add a song
2. Remove a song by title
3. Search for a song by title
4. Display the entire log
5. Exit
Choose an option: 4

Log contents:
1) Title: Yesterday | Artist: The Beatles | Duration: 125s
2) Title: Imagine  | Artist: John Lennon | Duration: 183s

=== Radio Song Log ===
1. Add a song
2. Remove a song by title
3. Search for a song by title
4. Display the entire log
5. Exit
Choose an option: 3

Enter title to search: Imagine
--- Song Found ---
Title: Imagine
Artist: John Lennon
Duration: 183 seconds

=== Radio Song Log ===
1. Add a song
2. Remove a song by title
3. Search for a song by title
4. Display the entire log
5. Exit
Choose an option: 5

Goodbye!
```

---

### CONSTRAINTS  

- **Struct usage** – The primary data entity **must** be a `struct Song` (or equivalent) that contains the fields listed above and a pointer to the next node.  
- **Display function** – The logic for printing the details of **one** specific song **must** reside in a function with the exact prototype:  

  ```c
  void displaySong(const struct Song *s);
  ```  

  (or the C++ equivalent). All other output may call this function.  
- **Menu implementation** – The program **must** present a textual menu as described, and **option 5 must be “Exit”** to satisfy the mandatory exit‑option rule.  
- **Single‑responsibility functions** – Apart from `main`, you must implement at least the following separate functions (you may add more if you wish):  
  - `void addSong(struct Song **head);`  
  - `void removeSong(struct Song **head);`  
  - `void searchSong(struct Song *head);`  
  - `void displayLog(struct Song *head);`  
- **No global variables** – All list pointers must be passed to functions; do not use global variables to store the head of the list.  

Deliver a complete, compilable program that meets all the requirements and constraints.

---

## Problem 52 - openai/gpt-oss-120b - Iteration 72
# STEP 1: PROBLEM  

## Background  
The campus bookstore maintains a simple inventory of textbooks for each semester.  Because the inventory changes frequently (books are added, removed, or looked up by their ISBN), the store wants a lightweight program that stores the books in a **singly linked list**.  Your task is to implement this inventory manager.  The program will be run from a console and will present a text‑based menu to the user.

## Requirements  

Write a C (or C‑like) program that implements the following functionality:

1. **Data Representation**  
   - Define a `struct Book` that contains at least the following fields:  
     - `int isbn;`            // unique identifier (positive integer)  
     - `char title[64];`      // book title (no spaces needed, but you may allow them)  
     - `char author[32];`     // author name  
     - `struct Book *next;`   // pointer to the next node in the list  

2. **Menu‑Driven Operations** (the program must display a menu and repeatedly ask the user for a choice until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | 1 | **Add a book at the beginning** of the list. Prompt for `isbn`, `title`, and `author`. |
   | 2 | **Add a book at the end** of the list. Prompt for `isbn`, `title`, and `author`. |
   | 3 | **Delete a book** given its `isbn`. If the book is not found, display an appropriate message. |
   | 4 | **Search for a book** by `isbn` and display its details. |
   | 5 | **Display all books** in the order they appear in the list. |
   | 6 | **Exit** the program. *(This option must be present and clearly labelled.)* |

3. **Functional Details**  
   - When adding a book, the program must ensure that the `isbn` does not already exist in the list. If it does, reject the insertion with a warning.  
   - Deleting the head, a middle node, or the tail must all be handled correctly.  
   - The **search** operation must locate the node with the matching `isbn` and then **display its details** using a dedicated function (see Constraints).  
   - The **display all** operation should iterate through the list and print each book on its own line, showing all fields.  

4. **User Interaction**  
   - After completing any operation (except Exit), the menu should be shown again.  
   - Input validation is not required beyond what is specified (e.g., you may assume the user enters an integer for menu choices).  

## Example Input / Output  

```
=== Book Inventory Manager ===
1) Add book at beginning
2) Add book at end
3) Delete book by ISBN
4) Search book by ISBN
5) Display all books
6) Exit
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: CProgramming
Enter author: Kernighan
Book added at the beginning.

=== Book Inventory Manager ===
1) Add book at beginning
2) Add book at end
3) Delete book by ISBN
4) Search book by ISBN
5) Display all books
6) Exit
Enter choice: 2
Enter ISBN: 9780201633610
Enter title: DesignPatterns
Enter author: Gamma
Book added at the end.

=== Book Inventory Manager ===
1) Add book at beginning
2) Add book at end
3) Delete book by ISBN
4) Search book by ISBN
5) Display all books
6) Exit
Enter choice: 5
Current inventory:
ISBN: 9780131103627 | Title: CProgramming | Author: Kernighan
ISBN: 9780201633610 | Title: DesignPatterns | Author: Gamma

=== Book Inventory Manager ===
1) Add book at beginning
2) Add book at end
3) Delete book by ISBN
4) Search book by ISBN
5) Display all books
6) Exit
Enter choice: 4
Enter ISBN to search: 9780201633610
--- Book Found ---
ISBN: 9780201633610
Title: DesignPatterns
Author: Gamma

=== Book Inventory Manager ===
1) Add book at beginning
2) Add book at end
3) Delete book by ISBN
4) Search book by ISBN
5) Display all books
6) Exit
Enter choice: 6
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct Requirement** – The primary data entity must be represented with a `struct` named `Book` (or an equivalent name you choose) as described above.  

2. **Dedicated Display Function** – The logic that prints the details of **one specific book** (used by the search operation) **must be placed in a function called `displayBook`** with the prototype:  

   ```c
   void displayBook(const struct Book *b);
   ```  

   This function should print the ISBN, title, and author in a readable format.  

3. **Menu Exit Option** – The menu must contain an explicit option (number **6** in the example) that terminates the program. The wording “Exit” must be used in the menu text.  

4. **No Global Variables for the List Head** – The head pointer of the linked list must be declared inside `main` (or passed as a parameter) and not as a global variable.  

5. **Memory Management** – Every node that is removed from the list must be freed to avoid memory leaks.  

6. **Single‑File Implementation** – All code must reside in a single source file; you may define helper functions (e.g., `addAtHead`, `addAtTail`, `deleteByISBN`, `searchByISBN`, `displayAll`) but the program must compile as a single translation unit.  

---  

*Design the program so that a student who has just finished a lecture on singly linked lists can implement it without needing any additional data structures or advanced language features.*

---

## Problem 53 - openai/gpt-oss-120b - Iteration 73
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its software. The librarian wants a simple command‑line tool that keeps a **singly linked list** of the books currently on the shelf. Each book record stores the title, author, and a 4‑digit year of publication. The tool will be used by volunteers who are just learning how linked lists work, so the program must be straightforward, menu‑driven, and must demonstrate the core operations on a singly linked list.

## Requirements  

Your program must:

1. **Define a `struct`** called `Book` that holds:
   - `char title[101]`   – the book title (max 100 characters, may contain spaces)  
   - `char author[51]`   – the author name (max 50 characters)  
   - `int  year`         – year of publication (four‑digit integer)  
   - `struct Book *next` – pointer to the next node in the list  

2. **Maintain a singly linked list** of `Book` nodes. The list is initially empty.

3. **Provide a menu** (displayed after each operation) with the following options:  

   1. **Add a new book** – Prompt for title, author, and year; insert the new node at the **end** of the list.  
   2. **Remove a book by title** – Prompt for a title; delete the first node whose title matches exactly (case‑sensitive). If no such book exists, display an appropriate message.  
   3. **Search for a book by title** – Prompt for a title; locate the first matching node and display its details using the required function (see constraint). If not found, inform the user.  
   4. **Display all books** – Traverse the list and print the details of every stored book in the order they appear.  
   5. **EXIT** – Terminate the program.  

   *The EXIT option must be clearly indicated (e.g., “5. EXIT”).*

4. **Input validation** – For the year, ensure the entered value is a positive four‑digit integer; otherwise, re‑prompt.

5. **Memory management** – Allocate nodes dynamically (`malloc`/`new`) and free them when a book is removed or when the program exits.

## Example Interaction  

```
--- Library Book Manager ---
1. Add a new book
2. Remove a book by title
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 1

Enter title : The C Programming Language
Enter author: Brian Kernighan and Dennis Ritchie
Enter year  : 1978
Book added successfully.

--- Library Book Manager ---
1. Add a new book
2. Remove a book by title
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 1

Enter title : Introduction to Algorithms
Enter author: Thomas H. Cormen
Enter year  : 2009
Book added successfully.

--- Library Book Manager ---
1. Add a new book
2. Remove a book by title
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 4

Books in the catalog:
1. Title: The C Programming Language
   Author: Brian Kernighan and Dennis Ritchie
   Year: 1978
2. Title: Introduction to Algorithms
   Author: Thomas H. Cormen
   Year: 2009

--- Library Book Manager ---
1. Add a new book
2. Remove a book by title
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 3

Enter title to search: Introduction to Algorithms
--- Book Found ---
Title : Introduction to Algorithms
Author: Thomas H. Cormen
Year  : 2009

--- Library Book Manager ---
1. Add a new book
2. Remove a book by title
3. Search for a book by title
4. Display all books
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity must be represented with a `struct` named `Book` as described above.  
- **Display Function** – The logic that prints the details of a *single* book (title, author, year) **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const Book *b);
  ```

  All places where a single book’s information is shown (search result, deletion confirmation, etc.) must call this function.  

- **Single‑Responsibility Functions** – Apart from `main`, you may create additional helper functions, but the program **must not** contain more than **four** user‑defined functions (including `displayBook`).  

- **Menu Exit Option** – The menu must include a clearly labeled option to EXIT the program (as shown in the example, option 5). Selecting this option should cause the program to terminate gracefully after freeing any allocated memory.  

- **Dynamic Allocation Only** – Nodes must be created using dynamic memory allocation; static or global arrays for storing the books are not allowed.  

- **No Global Variables** – All list pointers should be passed to functions as arguments; do not use global variables to hold the head of the list.  

---  

*Design and implement the program according to the above specifications. The solution should compile and run on a standard C (or C++) compiler.*

---

## Problem 54 - openai/gpt-oss-120b - Iteration 74
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple command‑line tool to keep track of the books it has on hand for a special “Pop‑Up” sale. Each book is identified by an ISBN, has a title, and a quantity indicating how many copies are available. The store manager will run the program, add new titles, remove titles that are sold out, look up a particular book, and print the whole inventory.  

Your task is to implement this tool using a **singly linked list**. The list should store the books in the order they are entered (no sorting is required).  

## Requirements  

Write a C (or C++) program that provides the following functionality through a text‑based menu:  

1. **Add a new book** – Prompt for ISBN (string, up to 13 characters), title (string, up to 50 characters), and quantity (non‑negative integer). Insert the new node at the **tail** of the linked list.  
2. **Delete a book** – Prompt for an ISBN. If a node with that ISBN exists, remove it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN and display the book’s details (ISBN, title, quantity) if it exists; otherwise print “Book not found.”  
4. **Display all books** – Traverse the list and print each book on its own line in the format:  
   `ISBN: <isbn>, Title: <title>, Qty: <quantity>`  
5. **Display a specific book** – Prompt for an ISBN and invoke a dedicated function `displayBook` to print the details of that single book (or “Book not found.” if absent).  
6. **Exit** – Terminate the program cleanly, freeing all allocated memory.  

The program should continue to show the menu after each operation until the user selects the exit option.  

## Example Interaction  

```
--- Book Inventory Menu ---
1) Add book
2) Delete book
3) Search book
4) Display all books
5) Display specific book
6) Exit
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter quantity: 4
Book added.

--- Book Inventory Menu ---
1) Add book
2) Delete book
3) Search book
4) Display all books
5) Display specific book
6) Exit
Enter choice: 4
ISBN: 9780131103627, Title: The C Programming Language, Qty: 4

--- Book Inventory Menu ---
1) Add book
2) Delete book
3) Search book
4) Display all books
5) Display specific book
6) Exit
Enter choice: 5
Enter ISBN: 9780131103627
ISBN: 9780131103627, Title: The C Programming Language, Qty: 4

--- Book Inventory Menu ---
1) Add book
2) Delete book
3) Search book
4) Display all books
5) Display specific book
6) Exit
Enter choice: 6
Goodbye!
```  

## ### CONSTRAINTS  

- **Data Representation**: You **must** define a `struct` (or `class` in C++) named `BookNode` (or `Book`) that contains the ISBN, title, quantity, and a pointer to the next node.  
- **Display Function**: The logic for showing the details of a single book **must** reside in a function with the exact prototype:  
  ```c
  void displayBook(const BookNode *node);
  ```  
  (or the equivalent in C++).  
- **Menu Requirement**: The menu must include an explicit option to **EXIT** the program (option 6 in the example). Selecting this option must end the loop and free all dynamically allocated nodes.  
- **Memory Management**: All nodes created with `malloc`/`new` must be freed/deleted before program termination.  
- **No Global Variables**: All list manipulation should be performed via pointers passed to functions; do not use global variables to hold the head of the list.  

Feel free to add minor helper functions (e.g., `addBook`, `deleteBook`, `searchBook`) as needed, but the two constraints above are mandatory.

---

## Problem 55 - openai/gpt-oss-120b - Iteration 75
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalog system. Each book in the collection is identified by a unique **ISBN**, has a **title**, an **author**, and a **year of publication**. The library wants a simple console program that lets a librarian add, remove, and view books while the program is running. Because the collection can grow and shrink dynamically, the librarian has been asked to store the books in a **singly linked list**.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data Structure**  
   * Define a `struct Book` that holds the ISBN (string of up to 13 characters), title (string up to 50 characters), author (string up to 30 characters), year (integer), and a pointer to the next `Book`.  

2. **Menu‑Driven Interface** (the program must display a menu after each operation)  
   * **1 – Add a new book** – Prompt the user for ISBN, title, author, and year, then insert the new book **at the end** of the linked list.  
   * **2 – Remove a book** – Prompt for an ISBN; if a book with that ISBN exists, remove it from the list and free its memory; otherwise display “Book not found.”  
   * **3 – Display all books** – Traverse the list and print each book’s details on a separate line in the order they appear in the list.  
   * **4 – Find a book by ISBN** – Prompt for an ISBN and display the details of that single book using a dedicated function called `displayBook`. If the book is not found, print “Book not found.”  
   * **5 – EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.  

3. **Helper Functions**  
   * Implement a function `void displayBook(const struct Book *b)` that prints a single book in the format:  
     `ISBN: <isbn>, Title: <title>, Author: <author>, Year: <year>`  
   * All other list operations (add, remove, traverse) should be implemented in separate functions of your own design; **no list logic may be placed directly inside `main()`**.

4. **Robustness**  
   * The program must handle an empty list gracefully (e.g., attempting to display or remove a book when the list is empty should not crash).  
   * Input should be read safely (you may assume the user enters data of the correct type).  

## Example Interaction  

```
=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Display all books
4. Find a book by ISBN
5. EXIT
Select an option: 1

Enter ISBN (13 chars max): 9780131103627
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1988
Book added.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Display all books
4. Find a book by ISBN
5. EXIT
Select an option: 3

ISBN: 9780131103627, Title: The C Programming Language, Author: Kernighan & Ritchie, Year: 1988

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Display all books
4. Find a book by ISBN
5. EXIT
Select an option: 4

Enter ISBN to find: 9780131103627
ISBN: 9780131103627, Title: The C Programming Language, Author: Kernighan & Ritchie, Year: 1988

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Display all books
4. Find a book by ISBN
5. EXIT
Select an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented by a `struct Book` as described above.  
* **Display Function** – The details of a **single** book must be printed by a function named `displayBook`.  
* **Menu Exit Option** – The menu must contain an explicit option `5. EXIT` (or the keyword `EXIT`) that terminates the program.  
* **Separation of Concerns** – No list manipulation code (insertion, deletion, traversal) may appear inside `main()`. All such logic must reside in separate helper functions.  

Your solution should compile without warnings and run correctly on a standard C (or C++) compiler.

---

## Problem 56 - openai/gpt-oss-120b - Iteration 76
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. The librarians want a tiny command‑line tool that can store information about each book in a **singly linked list** while the program is running. The list must support adding new books, removing a book by its ISBN, searching for a book, and printing the whole collection.  

You are to write this tool from scratch, using only the standard C library. The program will be menu‑driven, so the user can repeatedly choose an operation until they decide to quit.

## Requirements  

1. **Data representation**  
   * Each book is represented by a `struct` containing:  
     - `char title[101]` – the book’s title (max 100 characters).  
     - `char author[51]` – the author’s name (max 50 characters).  
     - `unsigned long isbn` – a 13‑digit ISBN (treated as an unsigned long).  
     - `struct Book *next` – pointer to the next node in the list.  

2. **Supported operations (menu options)**  
   1. **Insert a new book at the front of the list** – Prompt for title, author, and ISBN, then create a node and link it as the new head.  
   2. **Delete a book by ISBN** – Prompt for an ISBN, locate the first node with that ISBN, remove it from the list, and free its memory. If the ISBN is not found, display an appropriate message.  
   3. **Search for a book by ISBN** – Prompt for an ISBN, locate the node, and display its details using the required `displayBook` function. If not found, inform the user.  
   4. **Print the entire catalog** – Traverse the list from head to tail, printing each book’s details on a separate line.  
   5. **EXIT** – Terminate the program gracefully, freeing any remaining nodes.  

3. **User interaction**  
   * After completing an operation, the menu should be shown again.  
   * Input should be read safely (e.g., using `fgets` for strings, checking the return value of `scanf` for numbers).  

4. **Memory management**  
   * Every node allocated with `malloc` must be released exactly once, either when it is deleted or when the program exits.  

## Example Input / Output  

```
--- Library Catalog Menu ---
1) Insert new book
2) Delete book by ISBN
3) Search book by ISBN
4) Print catalog
5) EXIT
Enter choice: 1

Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter ISBN (13 digits): 9780131103627
Book inserted.

--- Library Catalog Menu ---
1) Insert new book
2) Delete book by ISBN
3) Search book by ISBN
4) Print catalog
5) EXIT
Enter choice: 4

Catalog:
ISBN: 9780131103627 | Title: The C Programming Language | Author: Kernighan & Ritchie

--- Library Catalog Menu ---
1) Insert new book
2) Delete book by ISBN
3) Search book by ISBN
4) Print catalog
5) EXIT
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

* **Struct usage** – The primary data entity *must* be defined as a `struct Book` (as described above).  
* **Display function** – The logic for printing the details of **one** specific book must reside in a function with the exact prototype:  

  ```c
  void displayBook(const struct Book *b);
  ```  

* **Function count** – Apart from `int main(void)`, you may create **no more than three** additional functions. (The required `displayBook` counts as one of them.) Typical acceptable helpers are `insertFront`, `deleteByISBN`, `searchByISBN`, or a combined helper, but the total must stay ≤ 3.  
* **Menu exit option** – The menu must contain an explicit option to **EXIT** the program; in the example it is option `5`. The program must terminate only after the user selects this option.  
* **No global variables** – All list pointers must be passed to functions via parameters or returned values; do not use global variables to store the head of the list.  

---  

*Write a complete, compilable C program that satisfies all of the above.*

---

## Problem 57 - openai/gpt-oss-120b - Iteration 77
# STEP 1: PROBLEM  

**Background**  
The campus newspaper “The Byte Gazette” maintains a simple online archive of its articles. Each article is stored with a unique ID, a title, and the name of the author. The archive is small enough that a *singly linked list* is sufficient, but the newspaper staff wants a tiny console program to let a student editor add new articles, delete old ones, and look up information while the program is running.

**Program Requirements**  

Write a C (or C++) program that implements the article archive as a **singly linked list**. The program must provide a text‑based menu that allows the user to perform the following actions:

1. **Add a new article** – Prompt for the article’s ID (integer), title (string, max 100 characters), and author (string, max 50 characters). Insert the new node at the **head** of the list.
2. **Delete an article** – Prompt for an article ID and remove the node with that ID from the list. If the ID does not exist, display an appropriate message.
3. **Search for an article** – Prompt for an article ID and display the details of that article. If the ID is not found, inform the user.
4. **Display all articles** – Traverse the list and print the ID, title, and author of every stored article in the order they appear in the list.
5. **Exit** – Terminate the program gracefully. *(This option must be present as required by the mandatory constraints.)*

**Simple Example (sample interaction)**  

```
=== Article Archive Menu ===
1. Add article
2. Delete article
3. Search article
4. Display all articles
5. Exit
Choose an option: 1
Enter article ID: 101
Enter title: Linked Lists in Practice
Enter author: Alice Smith
Article added.

=== Article Archive Menu ===
1. Add article
2. Delete article
3. Search article
4. Display all articles
5. Exit
Choose an option: 1
Enter article ID: 202
Enter title: Memory Management Basics
Enter author: Bob Lee
Article added.

=== Article Archive Menu ===
1. Add article
2. Delete article
3. Search article
4. Display all articles
5. Exit
Choose an option: 4
ID: 202 | Title: Memory Management Basics | Author: Bob Lee
ID: 101 | Title: Linked Lists in Practice | Author: Alice Smith

=== Article Archive Menu ===
1. Add article
2. Delete article
3. Search article
4. Display all articles
5. Exit
Choose an option: 3
Enter article ID to search: 101
ID: 101 | Title: Linked Lists in Practice | Author: Alice Smith

=== Article Archive Menu ===
1. Add article
2. Delete article
3. Search article
4. Display all articles
5. Exit
Choose an option: 5
Goodbye!
```

### CONSTRAINTS  

- **Data Representation**: You **must** define a `struct` named `Article` (or equivalent) to represent each node in the linked list. The struct must contain at least the fields `int id; char title[101]; char author[51]; struct Article *next;`.
- **Display Function**: The logic for showing the details of **one specific article** (used by the search operation) **must be placed in a function called `displayArticle`** that takes a pointer to an `Article` as its sole argument and prints the article in the format shown in the example.
- **Menu Exit Option**: The menu must include a clearly labeled option (number **5** in the example) that exits the program. Selecting this option must end the program without memory leaks.
- **Memory Management**: All dynamically allocated nodes must be freed before program termination (e.g., when deleting a node or when exiting).  

*No other constraints are imposed; you may add helper functions as needed, but the above must be satisfied.*

---

## Problem 58 - openai/gpt-oss-120b - Iteration 78
# STEP 1: PROBLEM  

## Background  
The city of **Algoria** has just launched a pilot program that uses a fleet of autonomous delivery drones.  The operations team needs a simple console‑based tool to keep track of the drones that are currently active.  Each drone is identified by a unique integer ID, has a model name (a short string), and stores the number of packages it is currently carrying.  

Your task is to implement this tool using a **singly linked list**.  The list will hold the drones in the order they are added (new drones are appended to the end of the list).  The program must allow the user to add new drones, remove a drone by its ID, display the whole fleet, search for a specific drone, and report how many drones are currently stored.

## Requirements  

1. **Data Representation**  
   - Define a `struct` named `Drone` that contains:  
     - `int id;`                     // unique identifier  
     - `char model[32];`             // model name (max 31 characters + null)  
     - `int packages;`               // number of packages on board  

2. **Linked List Node**  
   - Define a `struct` named `Node` that contains:  
     - `Drone data;`  
     - `Node *next;`  

3. **Menu‑driven Program** (displayed repeatedly until the user chooses to exit)  
   - **1. Add a Drone** – Prompt for `id`, `model`, and `packages`; create a new node and append it to the list.  
   - **2. Remove a Drone** – Prompt for an `id`; locate the node with that `id` and delete it (maintaining list integrity). If the `id` is not found, print an appropriate message.  
   - **3. Display All Drones** – Traverse the list and print each drone’s details on its own line.  
   - **4. Search for a Drone** – Prompt for an `id`; if a drone with that `id` exists, display its details using the required function (see below); otherwise, report that it was not found.  
   - **5. Count Drones** – Print the total number of drones currently stored.  
   - **0. EXIT** – Terminate the program.  

4. **Input / Output**  
   - All interaction occurs via `stdin`/`stdout`.  
   - The menu should be shown exactly as shown in the example.  
   - After completing an operation, the menu is shown again (except when exiting).  

5. **Error Handling**  
   - If the user attempts to add a drone whose `id` already exists, reject the insertion and display a warning.  
   - All numeric inputs should be validated; if a non‑numeric value is entered where an integer is expected, print an error and re‑prompt.  

## Example  

```
=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 1

Enter Drone ID: 101
Enter Model name: SkyHawk
Enter Packages on board: 3
Drone added successfully.

=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 1

Enter Drone ID: 102
Enter Model name: CloudRunner
Enter Packages on board: 0
Drone added successfully.

=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 3

Fleet:
ID: 101 | Model: SkyHawk | Packages: 3
ID: 102 | Model: CloudRunner | Packages: 0

=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 4

Enter Drone ID to search: 101
ID: 101 | Model: SkyHawk | Packages: 3

=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 5
Total drones in fleet: 2

=== Drone Fleet Manager ===
1. Add a Drone
2. Remove a Drone
3. Display All Drones
4. Search for a Drone
5. Count Drones
0. EXIT
Choose an option: 0
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Usage** – The primary data entity **must** be represented with a `struct` named `Drone`.  
- **Display Function** – The logic that prints the details of a **single** drone **must** be placed in a function with the exact prototype:  

  ```c
  void displayDrone(const Drone *d);
  ```

- **Single Helper Function** – Apart from `main()`, you may only create **one additional function** (`displayDrone`). All other list manipulation (insertion, deletion, search, counting) must be performed directly inside `main()` or within the menu handling code.  
- **Menu Requirement** – The program **must** present a menu as described and must include the option `0. EXIT` to terminate the program.  

*Your solution should compile with a standard C compiler (C99 or later) and run correctly on a typical command‑line environment.*

---

## Problem 59 - openai/gpt-oss-120b - Iteration 79
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system.  Each book in the collection is identified by a **call number** (an integer), has a **title** (a string of up to 50 characters), and a **year of publication** (an integer).  The library wants a simple console program that lets a librarian add new books, remove a book, search for a book, and display the entire catalogue.  Because the catalogue size changes frequently, the librarian has asked you to store the books in a **singly linked list**.

## Requirements  
Write a C (or C++) program that implements the following functionality:

1. **Add a book** – Prompt the user for call number, title, and year, then insert the new book **at the end** of the linked list.  
2. **Delete a book** – Prompt for a call number and remove the first node whose call number matches. If no such book exists, display an appropriate message.  
3. **Search for a book** – Prompt for a call number and display the details of the matching book (call number, title, year). If the book is not found, inform the user.  
4. **Display catalogue** – Print every book in the list in the order they appear, one per line, using the format:  
   `CallNumber | Title | Year`  
5. **Exit** – End the program gracefully.

The program must present a **menu** that repeats after each operation until the user chooses the exit option.

## Example Input / Output  

```
=== Library Catalogue Menu ===
1. Add a book
2. Delete a book
3. Search for a book
4. Display catalogue
5. EXIT
Enter your choice: 1
Enter call number: 1023
Enter title: The Art of Algorithms
Enter year: 2020
Book added.

=== Library Catalogue Menu ===
1. Add a book
2. Delete a book
3. Search for a book
4. Display catalogue
5. EXIT
Enter your choice: 1
Enter call number: 2045
Enter title: Data Structures in Practice
Enter year: 2018
Book added.

=== Library Catalogue Menu ===
1. Add a book
2. Delete a book
3. Search for a book
4. Display catalogue
5. EXIT
Enter your choice: 4
Catalogue:
1023 | The Art of Algorithms | 2020
2045 | Data Structures in Practice | 2018

=== Library Catalogue Menu ===
1. Add a book
2. Delete a book
3. Search for a book
4. Display catalogue
5. EXIT
Enter your choice: 3
Enter call number to search: 2045
Book found: 2045 | Data Structures in Practice | 2018

=== Library Catalogue Menu ===
1. Add a book
2. Delete a book
3. Search for a book
4. Display catalogue
5. EXIT
Enter your choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data representation**: Use a `struct` named `BookNode` (or equivalent) to represent each node in the singly linked list. The struct must contain fields for `callNumber`, `title`, `year`, and a pointer to the next node.  
- **Display function**: The logic that prints the details of a **single** book must be placed in a function with the exact prototype `void displayBook(const BookNode *node);`.  
- **Menu requirement**: The menu must include an explicit option to **EXIT** the program (as shown in the example, option 5). Selecting this option should terminate the loop and end the program.  
- **Memory management**: All dynamically allocated nodes must be freed before the program terminates.  
- **Standard libraries only**: You may only use headers from the C (or C++) standard library (e.g., `<stdio.h>`, `<stdlib.h>`, `<string.h>`). No third‑party libraries are allowed.  

Your solution should be clear, well‑commented, and demonstrate proper use of a singly linked list.

---

## Problem 60 - openai/gpt-oss-120b - Iteration 80
# STEP 1: PROBLEM  

## Background  
The campus “Eco‑Club” keeps a simple electronic list of its members. Because the club’s membership changes frequently—students join, graduate, or drop out—the list must support fast insertion and deletion at any position. Your task is to implement this member list using a **singly linked list**.  

## Requirements  

Write a C (or C++) program that provides a **menu‑driven interface** for managing the Eco‑Club member list. The program must support the following operations:

1. **Add a new member at the end of the list**  
   - Prompt for the member’s **ID** (integer) and **full name** (string, up to 50 characters).  
   - Insert the new member as the last node of the linked list.

2. **Insert a member after a given ID**  
   - Prompt for an existing member’s ID after which the new member will be placed.  
   - Prompt for the new member’s ID and name.  
   - If the specified existing ID is not found, display an error message and return to the menu.

3. **Delete a member by ID**  
   - Prompt for the ID of the member to remove.  
   - If the ID exists, remove that node and free its memory; otherwise, display an error message.

4. **Display all members**  
   - Traverse the list from head to tail and print each member’s ID and name on a separate line.

5. **Search for a member by ID and display its details**  
   - Prompt for the ID to search.  
   - If found, call a dedicated function `displayMember` to print the member’s information; otherwise, report “Member not found”.

6. **Exit the program**  
   - Selecting this option terminates the program gracefully, releasing any allocated memory.

The menu must be displayed after each operation (except when exiting) and should clearly label the option numbers, e.g., `1) Add member`, `2) Insert after ID`, …, `6) Exit`.

## Example Input / Output  

```
=== Eco‑Club Member Management ===
1) Add member
2) Insert after ID
3) Delete member
4) Display all members
5) Search member by ID
6) Exit
Choose an option: 1
Enter member ID: 101
Enter member name: Alice Johnson
Member added.

=== Eco‑Club Member Management ===
1) Add member
2) Insert after ID
3) Delete member
4) Display all members
5) Search member by ID
6) Exit
Choose an option: 1
Enter member ID: 102
Enter member name: Bob Lee
Member added.

=== Eco‑Club Member Management ===
1) Add member
2) Insert after ID
3) Delete member
4) Display all members
5) Search member by ID
6) Exit
Choose an option: 4
Current members:
ID: 101   Name: Alice Johnson
ID: 102   Name: Bob Lee

=== Eco‑Club Member Management ===
1) Add member
2) Insert after ID
3) Delete member
4) Display all members
5) Search member by ID
6) Exit
Choose an option: 5
Enter ID to search: 102
--- Member Details ---
ID: 102
Name: Bob Lee

=== Eco‑Club Member Management ===
1) Add member
2) Insert after ID
3) Delete member
4) Display all members
5) Search member by ID
6) Exit
Choose an option: 6
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must be represented with a `struct`** named `MemberNode` (or equivalent) containing at least:
  - `int id;`
  - `char name[51];`  // space for the null terminator
  - `struct MemberNode *next;`
- The logic that prints the details of a **single** member **must reside in a function called `displayMember`** with the prototype `void displayMember(const MemberNode *node);`.
- The program must be **menu‑driven** and **must include an explicit “Exit” option** (option 6 in the example) that terminates the program.
- All dynamically allocated nodes must be freed before the program terminates to avoid memory leaks.
- Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the **only function that directly prints a member’s information is `displayMember`**.  

Your solution should compile without warnings and work correctly for any sequence of menu operations that obey the input format described above.

---

## Problem 61 - openai/gpt-oss-120b - Iteration 81
# STEP 1: PROBLEM  

**Background**  
The campus library wants a lightweight command‑line tool to keep track of the books that are currently on the shelves. Because the library’s inventory changes frequently (books are added, removed, or relocated), the staff has asked you to implement a **singly linked list** that stores each book’s information. Your program will be used by a single librarian at a time, so a simple text‑based menu is sufficient.

**Task**  
Write a C (or C‑compatible) program that maintains a singly linked list of books. Each book is identified by an ISBN (a string of up to 13 characters) and also stores a title and the year of publication. The program must allow the librarian to:

1. **Add a new book** to the *front* of the list.  
2. **Remove a book** given its ISBN (the first occurrence only).  
3. **Search for a book** by ISBN and display its details.  
4. **Display all books** in the order they appear in the list.  
5. **Exit** the program.

All operations should be performed in‑place on the linked list; no arrays or other containers may be used to store the books.

**Input / Output**  
The program presents a menu, reads the user’s choice, and then prompts for any additional data required by that choice. Below is a short interaction illustrating the required behaviour (user input is shown after `>`).

```
=== Library Book Manager ===
1) Add book
2) Remove book
3) Search book
4) Display all books
5) EXIT
Select an option: > 1
Enter ISBN (max 13 chars): > 9780131103627
Enter title: > The C Programming Language
Enter year: > 1988
Book added.

=== Library Book Manager ===
1) Add book
2) Remove book
3) Search book
4) Display all books
5) EXIT
Select an option: > 4
--- Book List ---
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1988
--- End of List ---

=== Library Book Manager ===
1) Add book
2) Remove book
3) Search book
4) Display all books
5) EXIT
Select an option: > 3
Enter ISBN to search: > 9780131103627
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1988

=== Library Book Manager ===
1) Add book
2) Remove book
3) Search book
4) Display all books
5) EXIT
Select an option: > 5
Goodbye!
```

If an operation cannot be completed (e.g., trying to remove or search for a non‑existent ISBN), print an appropriate message such as “Book not found.” and return to the menu.

### CONSTRAINTS  

1. **Data structure** – The primary entity must be represented with a `struct` named `BookNode` that contains at least the following members:  
   ```c
   char isbn[14];   // 13 characters + null terminator
   char title[101]; // up to 100 characters + null terminator
   int  year;
   struct BookNode *next;
   ```
2. **Function requirement** – The logic for displaying the details of **one specific book** (used by the search operation) must be placed in a function with the exact prototype:  
   ```c
   void displayBook(const BookNode *node);
   ```
3. **Menu** – The program must present a menu as shown in the example and **must include a menu option to EXIT** the program. The exit option must be numbered `5` (or any clearly stated keyword) and cause the program to terminate gracefully.  
4. **Memory management** – Every node that is removed from the list must be freed; the program must not leak memory.  
5. **Single‑source file** – All code (including the `displayBook` function) must reside in a single `.c` file compiled with a standard C compiler. No additional libraries beyond `<stdio.h>`, `<stdlib.h>`, and `<string.h>` may be used.  

Deliver a program that satisfies the above functional requirements and constraints.

---

## Problem 62 - openai/gpt-oss-120b - Iteration 82
# STEP 1: PROBLEM  

## Background  
The university’s Student Services Office wants to keep a simple in‑memory roster of students who have signed up for a new extracurricular workshop. Because the list of participants changes frequently (students can be added, removed, or moved to a different position), the office has decided to store the roster as a **singly linked list**.  

Your task is to write a console program that implements this roster. The program will be used by a teaching assistant who will interact with it through a text‑based menu.

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Student` that stores:  
     - an integer `id` (unique student identifier)  
     - a string `name` (max 30 characters)  
     - a pointer to the next `Student` in the list.  

2. **Core operations (menu‑driven)**  
   * **1 – Add student at the end** – Prompt for `id` and `name`, create a new node, and append it to the tail of the list.  
   * **2 – Insert student at a given position** – Prompt for `id`, `name`, and a 1‑based position `pos`. Insert the new node so that it becomes the `pos`‑th element (if `pos` is larger than the current length + 1, append at the end).  
   * **3 – Delete student by ID** – Prompt for an `id`. Remove the first node whose `id` matches; if no such node exists, display a message.  
   * **4 – Display the entire roster** – Traverse the list from head to tail and print each student’s `id` and `name`.  
   * **5 – Display details of ONE specific student** – Prompt for an `id` and print that student’s information using a dedicated function `displayStudent`. If the `id` is not found, report it.  
   * **0 – EXIT** – Terminate the program.  

3. **User interaction**  
   * After completing any operation (except EXIT), the menu should be shown again.  
   * All prompts and messages must be clear and user‑friendly.  

4. **Memory management**  
   * Allocate nodes dynamically and free them appropriately when they are removed or when the program exits.

## Example Input / Output  

```
=== Workshop Roster Menu ===
1. Add student at end
2. Insert student at position
3. Delete student by ID
4. Display all students
5. Display a student by ID
0. EXIT
Choose an option: 1
Enter student ID: 101
Enter student name: Alice
Student added.

=== Workshop Roster Menu ===
1. Add student at end
2. Insert student at position
3. Delete student by ID
4. Display all students
5. Display a student by ID
0. EXIT
Choose an option: 2
Enter student ID: 102
Enter student name: Bob
Enter position (1‑based): 1
Student inserted.

=== Workshop Roster Menu ===
1. Add student at end
2. Insert student at position
3. Delete student by ID
4. Display all students
5. Display a student by ID
0. EXIT
Choose an option: 4
Roster:
1) ID: 102, Name: Bob
2) ID: 101, Name: Alice

=== Workshop Roster Menu ===
1. Add student at end
2. Insert student at position
3. Delete student by ID
4. Display all students
5. Display a student by ID
0. EXIT
Choose an option: 5
Enter student ID to view: 101
--- Student Details ---
ID: 101
Name: Alice

=== Workshop Roster Menu ===
1. Add student at end
2. Insert student at position
3. Delete student by ID
4. Display all students
5. Display a student by ID
0. EXIT
Choose an option: 0
Goodbye!
```

## ### CONSTRAINTS  

1. **Struct usage** – The primary data entity must be represented with a `struct` called `Student` (or equivalent in the chosen language).  
2. **Dedicated display function** – The logic for showing the details of a single student must reside in a function named `displayStudent` (signature may vary by language, but the name is mandatory).  
3. **Menu requirement** – The program must present a menu as described, and **option 0 must be the explicit EXIT choice**.  
4. **Single‑function rule for list manipulation** – All list‑modifying operations (add, insert, delete) must be implemented in separate helper functions; `main` may only contain the menu loop and calls to these helpers.  
5. **No use of library containers** – You may not use built‑in list, vector, or similar collection types; the linked list must be built manually using pointers (or references) and dynamic allocation.  

*The problem is intended for students who have just learned how to implement a singly linked list and basic dynamic memory handling.*

---

## Problem 63 - openai/gpt-oss-120b - Iteration 83
# STEP 1: PROBLEM  

## Background  
The municipal library of **Codelandia** is modernizing its catalog system. The library keeps a simple linear list of books that are currently on the “New Arrivals” shelf. Because the shelf is constantly refreshed, the staff needs a lightweight program that can add books to the front of the list, remove the first book when it is checked out, and display information about any book when the patron asks for it.  

You have just learned how to implement a **singly linked list** in C (or C‑like pseudocode). Your task is to write a console application that models the “New Arrivals” shelf using a singly linked list.

## Requirements  

Your program must support the following operations, presented through a text‑based menu:

1. **Add a Book** – Prompt the user for the book’s ISBN (string, up to 13 characters), title (string, up to 50 characters), and author (string, up to 30 characters). Insert the new book node at the **head** of the linked list.  
2. **Remove the First Book** – Delete the node at the head of the list (the book that has been on the shelf the longest). If the list is empty, display an appropriate message.  
3. **Display a Book by ISBN** – Prompt the user for an ISBN, search the list, and if a matching node is found, show its details (ISBN, title, author). If no match is found, inform the user.  
4. **List All Books** – Traverse the list from head to tail and print the details of every book in order of insertion (most recent first).  
5. **Exit** – Terminate the program.

The program should continue to show the menu after each operation until the user selects **Exit**.

## Example Input / Output  

```
=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 1

Enter ISBN: 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Book added successfully!

=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 1

Enter ISBN: 9780201633610
Enter Title: Design Patterns
Enter Author: Gamma et al.
Book added successfully!

=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 4

--- Books on New Arrivals ---
ISBN: 9780201633610
Title: Design Patterns
Author: Gamma et al.

ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 3

Enter ISBN to search: 9780131103627
Book found:
ISBN: 9780131103627
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 2
First book removed (Design Patterns).

=== Codelandia Library – New Arrivals ===
1. Add a Book
2. Remove the First Book
3. Display a Book by ISBN
4. List All Books
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a book) **must be represented with a `struct`** (or equivalent record type) containing at least the fields `isbn`, `title`, `author`, and a pointer to the next node.  
2. **Display Function** – The logic for showing the details of **one specific book** (used in option 3) **must be placed in a function named `displayBook`** that receives a pointer/reference to a book node and prints its fields.  
3. **Modular Design** – Apart from `main`, you may create additional helper functions, but **the menu handling loop must reside entirely within `main`**.  
4. **Menu Exit Requirement** – The menu **must include an explicit option to EXIT the program** (option 5 in the example). Selecting this option ends the program gracefully.  

*Note:* You may assume that user input will not exceed the maximum lengths specified for each string field.

---

## Problem 64 - openai/gpt-oss-120b - Iteration 84
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book is identified by a **call number** (a string of letters and digits) and has a **title**. The library wants a simple console program that stores the collection of books in the order they are received. Because the collection can grow and shrink throughout the semester, the faculty has decided to use a **singly linked list** to manage the books.

You are to write this program. It should let the user add books, remove a book by its call number, search for a book, and display the entire list. The program must be menu‑driven and must terminate only when the user selects the explicit **EXIT** option.

## Requirements  

1. **Data representation**  
   * Define a `struct` named `Book` that holds:  
     - `char callNumber[20];`   // unique identifier  
     - `char title[100];`  
     - `struct Book *next;`  

2. **Menu options** (displayed repeatedly until the user exits)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new book** – Prompt for call number and title, then insert the new node at the **end** of the list. |
   | 2      | **Remove a book** – Prompt for a call number; delete the first node whose call number matches. If not found, print a message. |
   | 3      | **Search for a book** – Prompt for a call number; if found, display the book’s details using a function `displayBook`. If not found, inform the user. |
   | 4      | **Display all books** – Traverse the list from head to tail, printing each book’s call number and title (again using `displayBook`). |
   | 5      | **EXIT** – End the program. |

3. **Program behavior**  
   * The list is initially empty.  
   * All dynamic memory allocations must be checked for success.  
   * After each operation (except EXIT) the menu should be shown again.  
   * The program must free all allocated memory before terminating.  

## Example Interaction  

```
--- Library Book Manager ---
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 1

Enter call number: QA76.73C15
Enter title: Introduction to C Programming
Book added.

--- Library Book Manager ---
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 1

Enter call number: QA76.73J38
Enter title: Java for Beginners
Book added.

--- Library Book Manager ---
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 4

Book List:
Call #: QA76.73C15 | Title: Introduction to C Programming
Call #: QA76.73J38 | Title: Java for Beginners

--- Library Book Manager ---
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 3

Enter call number to search: QA76.73J38
Call #: QA76.73J38 | Title: Java for Beginners

--- Library Book Manager ---
1) Add a new book
2) Remove a book
3) Search for a book
4) Display all books
5) EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented with a `struct` named `Book` as described above.  
* **Display Function** – The logic that prints a single book’s details **must** be placed in a function with the exact prototype:  

  ```c
  void displayBook(const Book *b);
  ```

* **Menu Exit** – The menu **must** contain an option labeled **EXIT** (option number 5 in the example) that terminates the program.  
* **Single‑function rule** – Apart from `main`, you may create **only** the following helper functions:  
  * `displayBook` (required)  
  * any one additional function of your choice (e.g., for inserting at the tail). No other functions are permitted.  

* **Memory Management** – All nodes allocated with `malloc`/`calloc` must be released before the program ends.  

---  

Write the program in C (or C++) adhering to the constraints above. The solution will be evaluated on correctness, proper use of a singly linked list, compliance with the listed constraints, and clean memory handling.

---

## Problem 65 - openai/gpt-oss-120b - Iteration 85
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. The librarian wants a simple console program that keeps track of the books currently on the shelves. Each book has a **title**, an **author**, and a **unique integer ID**. Because the collection changes frequently (books are added, removed, or looked up), the librarian has asked you to store the books in a **singly linked list**.

Your task is to write a C (or C‑like) program that lets a user manage this list through a text‑based menu.

---

## Requirements  

1. **Data Representation**  
   - Define a `struct` named `Book` that holds the three fields: `int id`, `char title[51]`, `char author[51]`.  
   - Define a `struct` named `Node` that contains a `Book` and a pointer to the next `Node`.

2. **Menu‑driven Operations** (the program must display a menu repeatedly until the user chooses to exit)  
   - **1. Add a new book** – Prompt for `id`, `title`, and `author`. Insert the new node at the **head** of the list. If a book with the same `id` already exists, print an error and do not insert.  
   - **2. Remove a book** – Prompt for an `id`. Delete the node with that `id` from the list. If the `id` is not found, print a message.  
   - **3. Search for a book** – Prompt for an `id`. If found, display the book’s details; otherwise, report “Book not found”.  
   - **4. Display all books** – Traverse the list from head to tail and print each book’s `id`, `title`, and `author` on a separate line. If the list is empty, print “No books in the catalog”.  
   - **5. EXIT** – Terminate the program gracefully, freeing any allocated memory.

3. **Functionality**  
   - The logic for displaying the details of **one** specific book (used by the Search operation) must be placed in a function named `void displayBook(const Book *b);`.  
   - All other list manipulations (insert, delete, traversal) may be implemented in separate helper functions, but **no more than three functions** besides `main` may be defined.  

4. **Input / Output**  
   - All prompts and messages should be clear and user‑friendly.  
   - The program should not crash on invalid input; it may re‑prompt or ignore the offending line.

---

## Example Interaction  

```
=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 1

Enter book ID: 101
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Book added successfully.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 1

Enter book ID: 102
Enter title: Introduction to Algorithms
Enter author: Cormen et al.
Book added successfully.

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 3

Enter book ID to search: 101
Book found:
ID: 101
Title: The C Programming Language
Author: Kernighan & Ritchie

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 4

Catalog contents:
ID: 102 | Title: Introduction to Algorithms | Author: Cormen et al.
ID: 101 | Title: The C Programming Language | Author: Kernighan & Ritchie

=== Library Catalog Menu ===
1. Add a new book
2. Remove a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 5

Goodbye!
```

---

### CONSTRAINTS  

- **Struct Usage** – The primary data entity (`Book`) must be represented with a `struct`.  
- **Display Function** – The function `displayBook` must be used **exactly** for showing the details of a single book (e.g., in the Search operation).  
- **Menu Requirement** – The menu must include an explicit option **5. EXIT** that terminates the program.  
- **Function Limit** – Apart from `main`, you may define **no more than three** additional functions (e.g., `displayBook`, `insertHead`, `deleteNode`).  

*Feel free to add any helper functions you need, as long as the total number of user‑defined functions (excluding library functions) does not exceed the limit.*

---

## Problem 66 - openai/gpt-oss-120b - Iteration 86
# STEP 1: PROBLEM  

## Background  
The campus library is transitioning from a paper‑based catalogue to a simple digital system that runs on a command‑line interface.  Each book in the catalogue is identified by a **ISBN**, has a **title**, and stores the **year of publication**.  The library staff wants a tiny program that can add books, remove a book by ISBN, and list all books currently stored.  Because the collection may grow and shrink frequently, the staff has asked you to implement the catalogue as a **singly linked list**.

## Requirements  
Write a C (or C++) program that provides the following functionality through a text‑based menu:

1. **Insert a new book** – Prompt the user for ISBN (string, up to 13 characters), title (string, up to 50 characters), and year (integer). Insert the new node at the **head** of the list.  
2. **Delete a book** – Prompt for an ISBN. If a node with that ISBN exists, remove it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN and, if found, display the book’s details; otherwise print “Book not found.”  
4. **Display all books** – Traverse the list from head to tail and print each book’s ISBN, title, and year on a separate line.  
5. **Exit** – Terminate the program gracefully, freeing any remaining allocated memory.

The program must continue to show the menu after completing any operation until the user selects the **Exit** option.

## Example Interaction  

```
===== Library Catalogue Menu =====
1. Insert a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter year: 1988
Book inserted.

===== Library Catalogue Menu =====
1. Insert a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 4
ISBN: 9780131103627 | Title: The C Programming Language | Year: 1988

===== Library Catalogue Menu =====
1. Insert a new book
2. Delete a book
3. Search for a book
4. Display all books
5. EXIT
Enter your choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: The primary data entity (a book) **must be represented using a `struct`** named `BookNode` that contains the ISBN, title, year, and a pointer to the next node.  
- **Display Function**: The logic for displaying the details of **one specific book** (used by the Search operation) **must be placed in a function called `displayBook(const BookNode *node)`**.  
- **Memory Management**: All dynamically allocated memory must be freed before the program terminates.  
- **Menu Requirement**: The menu must include an explicit option to **EXIT** the program (option number 5 in the example). Selecting this option ends the loop and prints a farewell message.  

*Optional (but recommended for style):* Keep all list‑manipulation code (insert, delete, search) in separate functions besides `main`.  

---  

Implement the program according to the specifications above. Good luck!

---

## Problem 67 - openai/gpt-oss-120b - Iteration 87
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalogue system. Each book in the catalogue is identified by a unique **ISBN** (a 13‑digit number) and has a **title** and a **shelf number** (an integer indicating where the book is stored). The library wants a simple console application that lets a librarian add new books, remove books, search for a book by ISBN, and display the entire catalogue in the order the books were entered.  

Because the catalogue will be built incrementally and may change frequently, the librarian has requested that the underlying data structure be a **singly linked list**.

## Requirements  
Write a C (or C++) program that implements the catalogue using a singly linked list. The program must provide the following functionality through a text‑based menu:

1. **Add a new book** – Prompt for ISBN, title, and shelf number, then insert the new node at the **end** of the list.  
2. **Remove a book** – Prompt for an ISBN; if a node with that ISBN exists, remove it from the list and free its memory; otherwise print “Book not found.”  
3. **Search for a book** – Prompt for an ISBN; if found, display the book’s details (ISBN, title, shelf); otherwise print “Book not found.”  
4. **Display catalogue** – Print all books in the list from head to tail, one per line, in the format:  
   `ISBN: <isbn>, Title: <title>, Shelf: <shelf>`  
5. **Exit** – Terminate the program gracefully, freeing any remaining allocated memory.

The menu must be displayed after each operation until the user selects the exit option.

## Example Input / Output  

```
--- Library Catalogue Menu ---
1. Add book
2. Remove book
3. Search book
4. Display catalogue
5. Exit
Enter choice: 1
Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter shelf number: 42
Book added.

--- Library Catalogue Menu ---
1. Add book
2. Remove book
3. Search book
4. Display catalogue
5. Exit
Enter choice: 1
Enter ISBN: 9780201633610
Enter title: Design Patterns
Enter shelf number: 7
Book added.

--- Library Catalogue Menu ---
1. Add book
2. Remove book
3. Search book
4. Display catalogue
5. Exit
Enter choice: 4
ISBN: 9780131103627, Title: The C Programming Language, Shelf: 42
ISBN: 9780201633610, Title: Design Patterns, Shelf: 7

--- Library Catalogue Menu ---
1. Add book
2. Remove book
3. Search book
4. Display catalogue
5. Exit
Enter choice: 3
Enter ISBN to search: 9780201633610
ISBN: 9780201633610, Title: Design Patterns, Shelf: 7

--- Library Catalogue Menu ---
1. Add book
2. Remove book
3. Search book
4. Display catalogue
5. Exit
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must be represented with a `struct`** named `BookNode` (or equivalent) containing at least the fields `isbn` (string or unsigned long long), `title` (string), `shelf` (int), and a pointer to the next node.  
- The logic for displaying the details of **one specific book** (used by the search operation) **must be placed in a function called `displayBook(const BookNode *node)`**.  
- Apart from `main`, you may create additional helper functions, but **the menu handling loop must reside entirely inside `main`**.  
- If you choose to implement the menu, **option 5 must be the explicit “Exit” choice**, and selecting it must cause the program to terminate after freeing all dynamically allocated memory.  
- All dynamic memory allocations must be checked for success; on failure, print an error message and exit.  

Your solution should compile without warnings and run correctly on a standard C (or C++) compiler.

---

## Problem 68 - openai/gpt-oss-120b - Iteration 88
# STEP 1: PROBLEM  

## Background  
The campus library has decided to digitize its “Featured Book” display. Each day a single book is highlighted on the front page of the library website. The library staff wants a tiny command‑line tool that lets a student librarian maintain a **singly linked list** of the upcoming featured books. The list must preserve the order in which the books will be shown (first node = the book that will be featured tomorrow, second node = the book for the day after, etc.).  

Your task is to write the program that lets the user add, remove, and view books in this schedule. The program will be used only during the semester, so efficiency is not a primary concern—correctness and clean use of a singly linked list are.

## Requirements  

1. **Data representation**  
   * Each book is represented by a `struct` (or equivalent language construct) containing:  
     - `title` (string, up to 100 characters)  
     - `author` (string, up to 100 characters)  
     - `isbn` (string, exactly 13 characters)  

2. **Menu‑driven interface** (the program must present a menu repeatedly until the user chooses to exit)  

   | Option | Description |
   |--------|-------------|
   | `1` | **Add Book to End** – Prompt for title, author, ISBN and append a new node to the tail of the list. |
   | `2` | **Insert Book at Position** – Prompt for position (1‑based index), then for the book data, and insert the node at that position. If the position is greater than the current length + 1, display an error and do nothing. |
   | `3` | **Remove Book by ISBN** – Prompt for an ISBN; locate the first node with that ISBN and delete it. If not found, report “Book not found.” |
   | `4` | **Display All Books** – Traverse the list from head to tail and print each book on its own line in the format: `Title | Author | ISBN`. |
   | `5` | **Display Book at Position** – Prompt for a position and print the book at that position using the function `displayEntity`. If the position is invalid, report an error. |
   | `6` | **EXIT** – Terminate the program. |

3. **Functionality constraints**  
   * The logic for displaying the details of **ONE specific book** must be encapsulated in a function named `displayEntity` (or the language‑appropriate equivalent).  
   * All list manipulation (insert, delete, traversal) must be performed using a singly linked list; no array‑based containers (e.g., `vector`, `ArrayList`) may be used to store the books.  
   * The program should handle an empty list gracefully (e.g., “No books scheduled.” when displaying all books).  

4. **User interaction**  
   * After completing any operation (except EXIT), the menu should be shown again.  
   * Input errors (non‑numeric menu choice, out‑of‑range positions, duplicate ISBNs, etc.) should be detected and reported, but the program may simply re‑prompt for the next menu choice.  

## Example  

```
=== Featured Book Scheduler ===
1. Add Book to End
2. Insert Book at Position
3. Remove Book by ISBN
4. Display All Books
5. Display Book at Position
6. EXIT
Choose an option: 1

Enter title: The Time Machine
Enter author: H. G. Wells
Enter ISBN (13 chars): 9780141439976
Book added to the end.

=== Featured Book Scheduler ===
1. Add Book to End
2. Insert Book at Position
3. Remove Book by ISBN
4. Display All Books
5. Display Book at Position
6. EXIT
Choose an option: 4

Scheduled Featured Books:
The Time Machine | H. G. Wells | 9780141439976

=== Featured Book Scheduler ===
1. Add Book to End
2. Insert Book at Position
3. Remove Book by ISBN
4. Display All Books
5. Display Book at Position
6. EXIT
Choose an option: 6

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity (the book) **must** be represented with a `struct` (or the language’s equivalent record type).  
* **Display Function** – The details of a single book must be printed by a function named `displayEntity`. No direct `printf`/`cout`/`System.out.println` of book fields is allowed outside this function.  
* **Menu Exit** – The menu **must** include an explicit option (`6` in the example) to EXIT the program; selecting this option ends the program immediately.  
* **Single‑linked list only** – You may not use built‑in dynamic array or list containers; only a manually‑implemented singly linked list is permitted.  

*Optional (for extra credit):*  
- Detect and reject insertion of a book whose ISBN already exists in the list, printing “Duplicate ISBN not allowed.”  
- Implement a function `countBooks` that returns the current number of scheduled books and display this count each time the menu is shown.  

---

## Problem 69 - openai/gpt-oss-120b - Iteration 89
# STEP 1: PROBLEM  

## Background  
The city’s public library is modernizing its catalog system.  Each book in the collection is identified by a unique **ISBN**, has a **title**, an **author**, and a **year of publication**.  The library wants a simple console‑based program that stores the books in the order they are added, using a **singly linked list**.  Librarians will be able to add new books, remove a book by ISBN, search for a book, and display the entire catalog.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   * Define a `struct` named `Book` that stores the ISBN (string of up to 13 characters), title, author, and year (integer).  
   * Define a `struct` named `Node` that contains a `Book` and a pointer to the next `Node`.

2. **Menu‑Driven Interface** (the program must present a menu and loop until the user chooses to exit)  
   * **1. Add Book** – Prompt for the book’s details and append a new node to the **end** of the list.  
   * **2. Remove Book** – Prompt for an ISBN; locate the node with that ISBN and remove it, freeing its memory. If the ISBN is not found, display an appropriate message.  
   * **3. Search Book** – Prompt for an ISBN; if a matching book exists, display its details using the function `displayBook`. Otherwise, indicate that the book is not in the catalog.  
   * **4. List All Books** – Traverse the list from head to tail, displaying each book’s details (again via `displayBook`). If the list is empty, print “Catalog is empty.”  
   * **5. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.

3. **Helper Functions**  
   * Implement a function `void displayBook(const Book *b)` that prints a single book in the format:  
     `ISBN: <isbn>, Title: "<title>", Author: <author>, Year: <year>`  
   * All other list operations (add, remove, search, list) must be implemented as separate functions (you may create as many as you need, but **no more than one function besides `main` may perform I/O**; all user prompts and reads must be done in `main`).

4. **Robustness**  
   * Validate that the year entered is a positive integer.  
   * Ensure that memory is never leaked (every allocated node must eventually be freed).

## Example Interaction  

```
--- Library Catalog Menu ---
1. Add Book
2. Remove Book
3. Search Book
4. List All Books
5. EXIT
Choose an option: 1

Enter ISBN (max 13 chars): 9780131103627
Enter Title: The C Programming Language
Enter Author: Kernighan & Ritchie
Enter Year: 1988
Book added successfully.

--- Library Catalog Menu ---
1. Add Book
2. Remove Book
3. Search Book
4. List All Books
5. EXIT
Choose an option: 4

Catalog:
ISBN: 9780131103627, Title: "The C Programming Language", Author: Kernighan & Ritchie, Year: 1988

--- Library Catalog Menu ---
1. Add Book
2. Remove Book
3. Search Book
4. List All Books
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

* **Struct Requirement** – The primary data entity **must** be represented with a `struct` named `Book`.  
* **Display Function** – The logic for displaying the details of **ONE specific book** must be in a function called `displayBook`.  
* **Menu Exit** – The menu must contain a distinct option (number **5**) labeled **EXIT** that terminates the program.  
* **I/O Limitation** – Apart from `main`, no other function may read from `stdin` or write to `stdout`. All user interaction must occur in `main`.  
* **Memory Management** – Use dynamic memory (`malloc`/`free` or `new`/`delete`) for list nodes; static or global arrays are not permitted.  

Your program should compile without warnings and behave exactly as described above.

---

## Problem 70 - openai/gpt-oss-120b - Iteration 90
# STEP 1: PROBLEM  

## Background  
The campus library is launching a **“Reading‑Buddy”** program that pairs each freshman with a senior student who recommends a book each week. The library staff needs a simple console application to keep track of the current list of reading‑buddies. Each buddy record contains the freshman’s name, the senior’s name, and the title of the recommended book. Because the list will be constantly updated (students join, leave, or change their recommendation), the staff has decided to store the data in a **singly linked list**.

## Requirements  

Write a **menu‑driven** C program that allows the user to manage the reading‑buddy list. The program must support the following operations:

1. **Add a new buddy** – Prompt for freshman name, senior name, and book title, then insert the new record at the **end** of the linked list.  
2. **Remove a buddy** – Prompt for the freshman’s name and delete the first node whose freshman name matches (if any).  
3. **Search for a buddy** – Prompt for a freshman’s name and display the corresponding senior’s name and book title.  
4. **Display all buddies** – Print the entire list in the order stored, one buddy per line.  
5. **Exit** – Terminate the program gracefully.

All input should be read from `stdin`; all output should be written to `stdout`. The program should continue to display the menu after completing any operation until the user selects the **Exit** option.

## Example  

```
=== Reading‑Buddy Manager ===
1. Add Buddy
2. Remove Buddy
3. Search Buddy
4. Display All
5. Exit
Choose an option: 1
Enter freshman name: Alice
Enter senior name: Dr. Rivera
Enter book title: "Introduction to Algorithms"

Buddy added successfully.

=== Reading‑Buddy Manager ===
1. Add Buddy
2. Remove Buddy
3. Search Buddy
4. Display All
5. Exit
Choose an option: 4

List of Reading‑Buddies:
1. Freshman: Alice, Senior: Dr. Rivera, Book: "Introduction to Algorithms"

=== Reading‑Buddy Manager ===
1. Add Buddy
2. Remove Buddy
3. Search Buddy
4. Display All
5. Exit
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation** – The primary entity (a buddy record) **must be defined using a `struct`** named `Buddy`. The struct must contain at least three character arrays (or pointers) for the freshman name, senior name, and book title, and a pointer to the next `Buddy`.  
- **Modular Design** – The logic for **displaying the details of ONE specific buddy** (used by the Search operation) **must be placed in a function called `displayBuddy`** that takes a pointer to a `Buddy` as its sole argument.  
- **Menu Requirement** – The program must present a menu as described above, and **option 5 must be the explicit “Exit” choice** that terminates the program.  
- **Memory Management** – All dynamically allocated memory for nodes must be freed before the program exits.  
- **Standard Library Only** – Use only the C standard library (`stdio.h`, `stdlib.h`, `string.h`, etc.). No external libraries are permitted.  

Your solution should compile with a standard C compiler (e.g., `gcc -std=c11`).

---

## Problem 71 - openai/gpt-oss-120b - Iteration 91
# STEP 1: PROBLEM  

## Background  
The city’s public transportation authority is modernizing its bus‑stop information system. Each bus stop is identified by a unique integer ID and stores the name of the stop (a short string, up to 30 characters) and the average daily passenger count (an integer). The authority wants a simple console program that lets a clerk add new stops, remove stops that are no longer in service, and query information about a particular stop. Internally the stops must be kept in a **singly linked list** in the order they are entered.

## Requirements  

Write a C (or C++) program that implements the following functionality:

1. **Data Structure**  
   - Define a `struct` named `BusStop` that contains:
     - `int id;`               // unique identifier  
     - `char name[31];`        // stop name (null‑terminated)  
     - `int dailyPassengers;` // average daily passengers  
     - `BusStop *next;`        // pointer to the next node  

2. **Menu‑driven Interface** (the program must present a text menu after each operation)  

   | Option | Description |
   |--------|-------------|
   | 1      | **Add a new stop** – Prompt for `id`, `name`, and `dailyPassengers`. Insert the new node at the **end** of the list. If a stop with the same `id` already exists, print an error and do not insert. |
   | 2      | **Delete a stop** – Prompt for an `id`. Remove the node with that `id` from the list. If the `id` is not found, print an appropriate message. |
   | 3      | **Display a stop** – Prompt for an `id`. Use a function called `displayStop` (see Constraints) to print the stop’s details in the format shown in the example. If the `id` does not exist, inform the user. |
   | 4      | **List all stops** – Traverse the list from head to tail and print each stop on its own line (use the same format as option 3). If the list is empty, print “No stops recorded.” |
   | 5      | **EXIT** – Terminate the program gracefully, freeing any allocated memory. |

3. **Memory Management**  
   - Dynamically allocate each `BusStop` node using `malloc`/`new`.  
   - Ensure that all allocated memory is released before the program exits.

4. **Input Validation**  
   - The program should handle non‑numeric input for menu choices and IDs without crashing (you may assume the user eventually enters a valid integer).

## Example Interaction  

```
--- Bus Stop Management System ---
1) Add a new stop
2) Delete a stop
3) Display a stop
4) List all stops
5) EXIT
Enter choice: 1
Enter stop ID: 101
Enter stop name: Main Street
Enter daily passengers: 2350
Stop added.

--- Bus Stop Management System ---
1) Add a new stop
2) Delete a stop
3) Display a stop
4) List all stops
5) EXIT
Enter choice: 1
Enter stop ID: 205
Enter stop name: River Park
Enter daily passengers: 1240
Stop added.

--- Bus Stop Management System ---
1) Add a new stop
2) Delete a stop
3) Display a stop
4) List all stops
5) EXIT
Enter choice: 3
Enter stop ID to display: 101
Stop ID: 101 | Name: Main Street | Daily Passengers: 2350

--- Bus Stop Management System ---
1) Add a new stop
2) Delete a stop
3) Display a stop
4) List all stops
5) EXIT
Enter choice: 4
Stop ID: 101 | Name: Main Street | Daily Passengers: 2350
Stop ID: 205 | Name: River Park | Daily Passengers: 1240

--- Bus Stop Management System ---
1) Add a new stop
2) Delete a stop
3) Display a stop
4) List all stops
5) EXIT
Enter choice: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented by a `struct` named `BusStop`.  
- **Display Function** – The logic for printing the details of a single stop **must** reside in a function with the exact prototype:  

  ```c
  void displayStop(const BusStop *stop);
  ```

- **Menu Exit** – The menu **must** include an explicit option (number 5) labeled **EXIT** that terminates the program.  
- **Single‑purpose Functions** – Apart from `main`, you may create additional helper functions (e.g., for insertion, deletion, searching), but the `displayStop` function must be used for any single‑stop output.  
- **No Global Variables** – All list pointers should be managed locally (e.g., passed to functions) or via static variables inside functions; do not use global variables for the head of the list.  

Implement the program according to these specifications.

---

## Problem 72 - openai/gpt-oss-120b - Iteration 92
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Every book in the collection is identified by a **call number** (a string), has a **title**, an **author**, and a **year of publication**. The library wants a simple console‑based application that stores the books in the order they are entered, using a **singly linked list**.  

You have just finished the unit on singly linked lists and are asked to write the program that will let a librarian add, remove, search, and list books.

## Requirements  

Write a C (or C++) program that provides the following functionality through a text‑based menu:

1. **Add a new book** – Prompt for call number, title, author, and year; insert the new node at the **end** of the list.  
2. **Delete a book** – Prompt for a call number; remove the first node whose call number matches. If no such book exists, display an appropriate message.  
3. **Search for a book** – Prompt for a call number; if a matching node is found, display all its details; otherwise report that the book is not found.  
4. **List all books** – Traverse the list from head to tail and display each book’s details on a separate line.  
5. **Exit** – Terminate the program gracefully, freeing any allocated memory.

The program must continue to show the menu after completing any operation (except Exit).

## Example Input / Output  

```
--- Library Book Manager ---
1. Add Book
2. Delete Book
3. Search Book
4. List All Books
5. Exit
Choose an option: 1

Enter call number: QA76.73.C15
Enter title: The C Programming Language
Enter author: Kernighan & Ritchie
Enter year: 1978
Book added successfully!

--- Library Book Manager ---
1. Add Book
2. Delete Book
3. Search Book
4. List All Books
5. Exit
Choose an option: 4

Books in inventory:
Call: QA76.73.C15 | Title: The C Programming Language | Author: Kernighan & Ritchie | Year: 1978

--- Library Book Manager ---
1. Add Book
2. Delete Book
3. Search Book
4. List All Books
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- The primary data entity **must be represented with a `struct`** named `BookNode` containing the fields: `char callNumber[20]; char title[100]; char author[100]; int year; struct BookNode *next;`.  
- All list‑manipulation logic (insert, delete, search, traverse) must be placed in **separate functions**; the `main` function may only handle the menu loop and call those functions.  
- The logic for displaying the details of **one specific book** must be implemented in a function with the exact prototype:  

  ```c
  void displayBook(const BookNode *node);
  ```  

- The program must **free all dynamically allocated memory** before exiting.  
- **Menu Requirement** (mandatory): option **5** must be the “Exit” choice, and selecting it ends the program.  

*Note: You may assume that input strings will not exceed the allocated array sizes.*

---

## Problem 73 - openai/gpt-oss-120b - Iteration 93
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by a unique ISBN, has a title, and stores the number of copies currently on the shelf. The library wants a simple command‑line tool that allows a librarian to add new books, remove books, and view the current list of books. Because the collection will be constantly changing, the librarian prefers a **singly linked list** to store the books in the order they were entered.

## Requirements  
Write a program that implements the book inventory using a singly linked list. The program must provide a **menu‑driven interface** with the following options:

1. **Add a Book** – Prompt for ISBN (string), title (string), and copy count (integer). Insert the new book at the **end** of the list.  
2. **Remove a Book** – Prompt for an ISBN. If a node with that ISBN exists, delete it from the list and free its memory; otherwise print “Book not found.”  
3. **Display All Books** – Traverse the list and print each book’s details on a separate line in the order they appear in the list.  
4. **Display One Book** – Prompt for an ISBN and, if found, display that book’s details using a dedicated function called `displayBook`. If the ISBN is not present, print “Book not found.”  
5. **Exit** – Terminate the program. *(This option must be explicitly listed in the menu as “5. Exit”.)*  

Additional functional details:

- The list must be **empty** when the program starts.
- ISBNs are unique; attempting to add a book with an ISBN that already exists should result in the message “ISBN already in inventory.” and the book should not be added.
- All user prompts and messages should be clear and self‑explanatory.
- The program should not leak memory; every removed node must be freed, and all nodes must be freed before exiting.

## Example Interaction  

```
=== Library Inventory Menu ===
1. Add a Book
2. Remove a Book
3. Display All Books
4. Display One Book
5. Exit
Choose an option: 1

Enter ISBN: 978-0131103627
Enter Title: The C Programming Language
Enter Copies: 3
Book added.

=== Library Inventory Menu ===
1. Add a Book
2. Remove a Book
3. Display All Books
4. Display One Book
5. Exit
Choose an option: 1

Enter ISBN: 978-0201616224
Enter Title: The Pragmatic Programmer
Enter Copies: 5
Book added.

=== Library Inventory Menu ===
1. Add a Book
2. Remove a Book
3. Display All Books
4. Display One Book
5. Exit
Choose an option: 3

ISBN: 978-0131103627 | Title: The C Programming Language | Copies: 3
ISBN: 978-0201616224 | Title: The Pragmatic Programmer | Copies: 5

=== Library Inventory Menu ===
1. Add a Book
2. Remove a Book
3. Display All Books
4. Display One Book
5. Exit
Choose an option: 4

Enter ISBN to view: 978-0201616224
ISBN: 978-0201616224 | Title: The Pragmatic Programmer | Copies: 5

=== Library Inventory Menu ===
1. Add a Book
2. Remove a Book
3. Display All Books
4. Display One Book
5. Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: Use a `struct` named `BookNode` (or similar) to represent each node in the singly linked list. The struct must contain fields for ISBN, title, copy count, and a pointer to the next node.  
- **Function Requirement**: The logic for displaying the details of ONE specific book must be placed in a function named `displayBook`. Its prototype should be `void displayBook(const BookNode *node);`.  
- **Menu Exit**: The menu must include the explicit option “5. Exit” that terminates the program.  
- **Single‑File Implementation**: All code must reside in a single source file (e.g., `inventory.c`). Apart from `main()`, you may create additional helper functions, but the core list operations (add, remove, display all, display one) should each be encapsulated in their own functions.  
- **Memory Management**: No memory leaks are allowed; every allocated node must be freed when removed or when the program ends.  

*Design your solution to be clear, modular, and easy for a fellow student to read.*

---

## Problem 74 - openai/gpt-oss-120b - Iteration 94
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a simple console‑based inventory system to keep track of the books that are currently on the shelves. Because the inventory changes frequently (books are added, sold, or moved), the store manager has asked you to implement the list of books as a **singly linked list**. Each node in the list will store the information for one book.

Your task is to write a program that lets a user (the manager) interact with this list through a text menu.

---

## Requirements  

Your program must provide the following functionality:

1. **Add a new book** to the **front** of the list.  
   - Prompt the user for the book’s ISBN (string, up to 13 characters), title (string, up to 50 characters), and price (floating‑point).  
2. **Remove a book** given its ISBN.  
   - If the ISBN is not found, display an appropriate message.  
3. **Search for a book** by ISBN and display its details.  
4. **Display the entire inventory** in the order stored in the linked list (i.e., from the most recently added to the oldest).  
5. **Exit** the program.

The program should repeatedly show the menu until the user chooses the exit option.

---

## Example Interaction  

```
=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by ISBN
4. Display all books
5. EXIT
Enter choice: 1

Enter ISBN: 9780131103627
Enter title: The C Programming Language
Enter price: 45.99
Book added successfully.

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by ISBN
4. Display all books
5. EXIT
Enter choice: 4

Inventory:
ISBN: 9780131103627 | Title: The C Programming Language | Price: $45.99

=== Bookstore Inventory Menu ===
1. Add a new book
2. Remove a book by ISBN
3. Search for a book by ISBN
4. Display all books
5. EXIT
Enter choice: 5

Goodbye!
```

---

## ### CONSTRAINTS  

1. **Data representation** – The primary data entity (a book) **must be defined using a `struct`** named `Book`. The struct must contain at least the following fields:  
   ```c
   typedef struct Book {
       char isbn[14];      // 13 characters + null terminator
       char title[51];     // up to 50 characters + null terminator
       double price;
       struct Book *next; // pointer to the next node
   } Book;
   ```

2. **Display function** – The logic that prints the details of **one** book must be encapsulated in a function with the exact prototype:  
   ```c
   void displayBook(const Book *b);
   ```

3. **Menu implementation** – The menu must be presented in a loop and **must include a distinct option to EXIT the program** (e.g., option `5` as shown above). Selecting this option terminates the loop and ends the program.

4. **Memory management** – Every node allocated with `malloc` (or `new` if using C++) must be freed appropriately when the program exits or when a book is removed.

5. **Single‑source file** – The entire solution must reside in one source file (e.g., `inventory.c`).

Feel free to add any helper functions you need, but the two constraints above are mandatory.

---

## Problem 75 - openai/gpt-oss-120b - Iteration 95
# STEP 1: PROBLEM  

## Background  
The campus library has decided to modernize its “Lost‑and‑Found” system. Every item that is turned in by a student is recorded with three pieces of information:  

1. **Item ID** – a unique integer assigned by the system.  
2. **Description** – a short string (max 30 characters) describing the item (e.g., “Blue backpack”).  
3. **Location** – the name of the building where the item was found.  

Because items are constantly being added and occasionally removed (once the owner claims the item), the library wants the data stored in a **singly linked list** that preserves the order in which items were received (new items are appended to the tail).  

You are to write a console program that allows a library assistant to manage this list through a simple text‑based menu.

## Requirements  
Your program must provide the following functionality:

1. **Add a new item** – Prompt the user for Item ID, Description, and Location, then append a new node to the end of the list.  
2. **Remove an item** – Prompt for an Item ID and delete the node with that ID (if it exists).  
3. **Search for an item** – Prompt for an Item ID and display the details of that item.  
4. **Display all items** – Traverse the list from head to tail and print each node’s information.  
5. **Exit** – Terminate the program gracefully.  

All menu choices must be numeric (e.g., `1` for Add, `2` for Remove, etc.). The program should continue to display the menu after completing an operation until the user selects the Exit option.

## Example Input / Output  

```
=== Lost‑and‑Found Management ===
1. Add item
2. Remove item
3. Search item
4. Display all items
5. EXIT
Choose an option: 1

Enter Item ID: 101
Enter Description: Blue backpack
Enter Location: Library Lobby
Item added successfully.

=== Lost‑and‑Found Management ===
1. Add item
2. Remove item
3. Search item
4. Display all items
5. EXIT
Choose an option: 4

Current items:
[101] Blue backpack – Library Lobby

=== Lost‑and‑Found Management ===
1. Add item
2. Remove item
3. Search item
4. Display all items
5. EXIT
Choose an option: 3

Enter Item ID to search: 101
Item found: [101] Blue backpack – Library Lobby

=== Lost‑and‑Found Management ===
1. Add item
2. Remove item
3. Search item
4. Display all items
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary entity (a lost‑and‑found item) **must be represented with a `struct`** (or equivalent record type in the chosen language) containing the three fields listed above and a pointer to the next node.  
2. **Function Naming** – The logic for displaying the details of **ONE specific item** (used by the Search operation) **must be placed in a function named `displayItem`** (signature appropriate to the language).  
3. **Modular Design** – Apart from `main`, you may create additional helper functions, but the **menu handling must be performed inside `main`**; no separate “menu driver” function is allowed.  
4. **Menu Exit Requirement** – The menu **must include an option explicitly labeled “EXIT”** (numeric choice `5` in the example) that terminates the program.  

*All other implementation details (memory management, input validation, etc.) are left to the student.*

---

## Problem 76 - openai/gpt-oss-120b - Iteration 96
# STEP 1: PROBLEM  

## Background  
The city’s new **Urban Wildlife Tracker** needs a lightweight console application that keeps a dynamic list of animals that have been spotted in the downtown park. Because the number of sightings varies day‑to‑day, the program must store the animals in a data structure that can grow and shrink without a fixed size limit.  

You have just learned how to implement a **singly linked list** in C (or C‑like pseudocode). Your task is to write a program that lets a park ranger add new sightings, remove the most recent sighting, and display information about any animal in the list.

## Requirements  

1. **Data Entity** – Each animal sighting must be stored in a `struct` named `Animal` with the following fields:  
   - `int id` – a unique integer identifier (assigned automatically, starting at 1).  
   - `char name[30]` – common name of the animal (e.g., “Raccoon”).  
   - `char species[30]` – scientific name (e.g., “Procyon lotor”).  
   - `int age` – estimated age in months.  

2. **Linked List** – Implement a singly linked list where each node contains an `Animal` and a pointer to the next node.

3. **Menu‑driven interface** (displayed after each operation) with the following options:  
   1. **Add a new sighting** – Prompt the user for `name`, `species`, and `age`; assign the next available `id` and insert the new node at the **head** of the list.  
   2. **Remove the most recent sighting** – Delete the node at the head of the list and free its memory. If the list is empty, print a warning.  
   3. **Display a sighting** – Ask for an `id` and print the details of the matching animal. If the `id` does not exist, report “Not found”.  
   4. **List all sightings** – Traverse the list from head to tail, printing each animal’s details on a separate line.  
   5. **EXIT** – Terminate the program. (The menu must clearly label this option, e.g., “5. EXIT”.)

4. **Input/Output** – All interaction occurs through `stdin`/`stdout`. Prompt messages should be user‑friendly but concise.

5. **Error handling** – The program must not crash on invalid input; it should display an appropriate message and re‑show the menu.

## Example  

```
=== Urban Wildlife Tracker ===
1. Add a new sighting
2. Remove the most recent sighting
3. Display a sighting
4. List all sightings
5. EXIT
Choose an option: 1

Enter animal name: Raccoon
Enter scientific name: Procyon lotor
Enter age (months): 24
Sighting added with ID 1.

=== Urban Wildlife Tracker ===
1. Add a new sighting
2. Remove the most recent sighting
3. Display a sighting
4. List all sightings
5. EXIT
Choose an option: 1

Enter animal name: Red Fox
Enter scientific name: Vulpes vulpes
Enter age (months): 12
Sighting added with ID 2.

=== Urban Wildlife Tracker ===
1. Add a new sighting
2. Remove the most recent sighting
3. Display a sighting
4. List all sightings
5. EXIT
Choose an option: 4

ID: 2 | Name: Red Fox | Species: Vulpes vulpes | Age: 12 months
ID: 1 | Name: Raccoon | Species: Procyon lotor | Age: 24 months

=== Urban Wildlife Tracker ===
1. Add a new sighting
2. Remove the most recent sighting
3. Display a sighting
4. List all sightings
5. EXIT
Choose an option: 3

Enter ID to display: 1
ID: 1 | Name: Raccoon | Species: Procyon lotor | Age: 24 months

=== Urban Wildlife Tracker ===
1. Add a new sighting
2. Remove the most recent sighting
3. Display a sighting
4. List all sightings
5. EXIT
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Struct Usage** – The primary data entity **must** be defined as a `struct` named `Animal`.  
- **Display Function** – The logic that prints the details of **ONE** specific animal (requirement 3‑3) **must** reside in a function called `void displayAnimal(const Animal *a);`.  
- **Function Count** – Apart from `main`, you may implement **exactly one additional helper function** (`displayAnimal`). All other list operations (add, remove, list) must be written directly inside `main` or as inline code blocks.  
- **Menu Exit** – The menu must contain an explicit option labeled **“5. EXIT”** (or the chosen numeric value) that ends the program.  

*All other design choices (e.g., memory allocation method, input parsing) are left to the student.*  

---

## Problem 77 - openai/gpt-oss-120b - Iteration 97
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its inventory system. Each book in the collection is identified by a **call number** (a string of up to 8 characters) and has a **title** (a string of up to 50 characters). The library wants a simple console program that lets a librarian add new books, remove books, and view the current list of books. Because the collection can grow and shrink frequently, the data must be stored in a **singly linked list**.

## Requirements  
Write a C (or C++) program that implements the following functionality:

1. **Data Representation**  
   - Define a `struct` (or `class` if you prefer C++) named `Book` that holds the call number and title.  
   - Define a singly linked list node that contains a `Book` and a pointer to the next node.

2. **Menu‑driven Interface** (the program must present a menu after each operation)  
   - **1. Add a book** – Prompt the user for the call number and title, then insert the new book **at the end** of the list.  
   - **2. Remove a book** – Prompt for a call number; if a node with that call number exists, remove it from the list and free its memory; otherwise print “Book not found.”  
   - **3. Display all books** – Traverse the list and print each book’s call number and title on its own line.  
   - **4. Find a book** – Prompt for a call number and, if found, display that single book’s details; otherwise print “Book not found.”  
   - **0. EXIT** – Terminate the program gracefully, freeing any remaining allocated memory.

3. **Input Validation**  
   - The call number must be unique; if the user tries to add a book whose call number already exists, print “Duplicate call number – book not added.”  
   - The menu choice must be an integer from the set {0,1,2,3,4}; any other input should cause the menu to be shown again.

4. **Memory Management**  
   - All nodes must be allocated dynamically.  
   - Before exiting, the program must release every allocated node.

## Example Interaction  

```
--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 1
Enter call number: CS101
Enter title: Introduction to Algorithms
Book added.

--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 1
Enter call number: MA202
Enter title: Linear Algebra
Book added.

--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 3
Books in the list:
CS101  Introduction to Algorithms
MA202  Linear Algebra

--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 4
Enter call number to find: MA202
MA202  Linear Algebra

--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 2
Enter call number to remove: CS101
Book removed.

--- Library Book List ---
1. Add a book
2. Remove a book
3. Display all books
4. Find a book
0. EXIT
Enter choice: 0
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented with a `struct` named `Book`.  
- **Display Function** – The logic for showing the details of **one specific book** (used in menu option 4) **must** be placed in a function called `displayBook(const Book *b)`.  
- **Single‑purpose Helper** – Any other helper functions (e.g., for insertion, deletion, freeing the list) are allowed, but the program must contain **exactly one** additional function besides `main()` **if you choose to implement the entire menu handling inside `main()`**. (If you create more helpers, you must still keep the total number of user‑defined functions ≤ 4.)  
- **Menu Exit Option** – The menu **must** include the option `0` labeled “EXIT” that terminates the program as described above.  

*Note: The problem is intended for students who have just learned singly linked lists, dynamic memory allocation, and basic struct usage.*

---

## Problem 78 - openai/gpt-oss-120b - Iteration 98
# STEP 1: PROBLEM  

## Background  
The campus café wants to keep a simple digital roster of the daily special drinks it offers. Each drink has a **name** (a string of up to 30 characters) and a **price** (a floating‑point number). The café staff will run a console program that lets them add new drinks, remove a drink by name, look up the price of a specific drink, and list all drinks currently on the menu. Because the list of specials changes frequently, a **singly linked list** is the most appropriate data structure.

## Requirements  
Write a C (or C++) program that implements the drink roster using a singly linked list. The program must provide a text‑based menu with the following options:

1. **Add a new drink** – Prompt for the drink’s name and price, then insert the new node at the **head** of the list.  
2. **Remove a drink** – Prompt for a drink name; delete the first node whose name matches (case‑sensitive). If the drink is not found, display a suitable message.  
3. **Find a drink** – Prompt for a drink name; if the drink exists, display its price; otherwise, indicate that the drink is not on the list.  
4. **Display all drinks** – Print each drink’s name and price in the order they appear in the linked list (head to tail).  
5. **Exit** – Terminate the program.  

The program should continue to display the menu after completing any operation until the user selects **Exit**.

## Example Input / Output  

```
=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 1
Enter drink name: Mocha
Enter price: 3.75
Drink added.

=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 1
Enter drink name: Latte
Enter price: 3.25
Drink added.

=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 4
Current Specials:
- Latte : $3.25
- Mocha : $3.75

=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 3
Enter drink name: Mocha
Price of Mocha: $3.75

=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 2
Enter drink name: Latte
Drink removed.

=== Café Specials Manager ===
1. Add a new drink
2. Remove a drink
3. Find a drink
4. Display all drinks
5. Exit
Select an option: 5
Goodbye!
```

## ### CONSTRAINTS  

1. **Data Representation** – The primary data entity (a drink) must be represented with a `struct` named `DrinkNode` containing at least the fields `char name[31];`, `float price;`, and `struct DrinkNode *next;`.  

2. **Function Requirement** – The logic for displaying the details of **one specific drink** (used in the “Find a drink” option) must be placed in a function with the exact prototype:  

   ```c
   void displayDrink(const DrinkNode *node);
   ```

3. **Modular Design** – Apart from `main()`, you may define any number of helper functions, but **the insertion operation must be implemented in a separate function named `insertAtHead`**, and the deletion operation must be implemented in a separate function named `deleteByName`.  

4. **Menu Exit Option** – The menu must include an explicit option to **EXIT** the program; in this problem it is option **5** as shown in the example. Selecting this option must cause the program to terminate gracefully.  

5. **Memory Management** – All dynamically allocated nodes must be freed before the program exits (i.e., no memory leaks).  

6. **No Global Variables** – All data structures must be passed to functions via parameters; do not use global variables to store the head pointer.  

---  

*Deliver a complete, compilable program that satisfies all of the above requirements and constraints.*

---

## Problem 79 - openai/gpt-oss-120b - Iteration 99
# STEP 1: PROBLEM  

## Background  
The campus bookstore wants a lightweight command‑line tool to keep track of the books that are currently on loan. Because the number of loans changes frequently and the data set is modest, a **singly linked list** is a good fit. Your task is to implement this tool so that the store clerk can add new loans, return books, look up a loan by its ISBN, and view the whole loan list.

## Requirements  

Write a program that provides the following functionality through a simple text menu:

1. **Add a loan** – Prompt the user for the book’s ISBN (string), title (string), and the borrower’s name (string). Insert the new loan at the **end** of the linked list.  
2. **Return a book** – Prompt for an ISBN and remove the corresponding node from the list. If the ISBN is not found, display an appropriate message.  
3. **Search for a loan** – Prompt for an ISBN and display the details of that loan (ISBN, title, borrower). If the ISBN does not exist, inform the user.  
4. **Display all loans** – Traverse the list and print every loan in the order they were added.  
5. **Exit** – Terminate the program.

The program must continue to display the menu after each operation until the user selects the **Exit** option.

## Example Input / Output  

```
--- Library Loan Manager ---
1) Add a loan
2) Return a book
3) Search for a loan
4) Display all loans
5) Exit
Choose an option: 1

Enter ISBN: 978-0131103627
Enter Title: The C Programming Language
Enter Borrower: Alice
Loan added.

--- Library Loan Manager ---
1) Add a loan
2) Return a book
3) Search for a loan
4) Display all loans
5) Exit
Choose an option: 1

Enter ISBN: 978-0201633610
Enter Title: Design Patterns
Enter Borrower: Bob
Loan added.

--- Library Loan Manager ---
1) Add a loan
2) Return a book
3) Search for a loan
4) Display all loans
5) Exit
Choose an option: 3

Enter ISBN to search: 978-0131103627
ISBN: 978-0131103627
Title: The C Programming Language
Borrower: Alice

--- Library Loan Manager ---
1) Add a loan
2) Return a book
3) Search for a loan
4) Display all loans
5) Exit
Choose an option: 4

Loan List:
1) ISBN: 978-0131103627 | Title: The C Programming Language | Borrower: Alice
2) ISBN: 978-0201633610 | Title: Design Patterns | Borrower: Bob

--- Library Loan Manager ---
1) Add a loan
2) Return a book
3) Search for a loan
4) Display all loans
5) Exit
Choose an option: 5

Goodbye!
```

## ### CONSTRAINTS  

- **Data Representation**: Use a `struct` named `Loan` (or equivalent in your language) to represent each loan, containing at least the fields `isbn`, `title`, `borrower`, and a pointer to the next node.  
- **Display Function**: The logic for showing the details of **ONE specific loan** must reside in a function called `displayLoan` (signature may vary by language, e.g., `void displayLoan(const Loan *node)` in C).  
- **Menu Requirement**: The program must present a menu as shown above, and **option 5 must be the explicit “Exit” choice** that terminates the program.  
- **Memory Management**: All dynamically allocated nodes must be freed appropriately before program termination (no memory leaks).  
- **Single‑File Implementation**: Apart from `main`, you may create additional helper functions, but the core linked‑list operations (insert, delete, search, display) must each be implemented in separate functions.  

Your solution should compile and run on a standard C (or C++, Java, Python, etc.) environment without external libraries beyond the language’s standard library.

---

## Problem 80 - openai/gpt-oss-120b - Iteration 100
# STEP 1: PROBLEM  

## Background  
The campus library is modernizing its catalog system.  Each book in the collection is identified by a **call number** (a string such as `"QA76.73.J38"`), has a **title**, and a **year of publication**.  The library wants a simple console program that lets a librarian add new books, remove the oldest book, and look up a book by its call number.  Internally the librarian has decided to keep the books in a **singly linked list**, ordered by the year of publication from newest (head) to oldest (tail).

## Requirements  

Write a C (or C‑compatible) program that implements the following functionality:

1. **Data Structure**  
   - Define a `struct Book` that stores the call number, title, year, and a pointer to the next `Book`.  

2. **Menu‑driven Interface** (the program must present a menu after each operation)  
   - `1` – **Add a Book**  
     * Prompt the user for call number, title, and year.  
     * Insert the new book into the list so that the list remains sorted **descending by year** (newest first).  
   - `2` – **Remove Oldest Book**  
     * Delete the book at the tail of the list (the oldest).  
     * Print the removed book’s details; if the list is empty, display a suitable message.  
   - `3` – **Find Book by Call Number**  
     * Prompt for a call number, search the list, and display the matching book’s details.  
     * If not found, inform the user.  
   - `4` – **Print All Books**  
     * Traverse the list from head to tail, printing each book on a separate line in the format:  
       `CallNumber | Title | Year`  
   - `5` – **EXIT**  
     * Terminate the program gracefully, freeing any allocated memory.  

3. **Input Validation**  
   - The year must be a positive integer.  
   - The call number and title may contain spaces; read them using a method that captures whole lines.

4. **Memory Management**  
   - Allocate memory dynamically for each new `Book`.  
   - Ensure no memory leaks (free nodes when removed or at program exit).

## Example Interaction  

```
--- Library Catalog Menu ---
1. Add a Book
2. Remove Oldest Book
3. Find Book by Call Number
4. Print All Books
5. EXIT
Choose an option: 1

Enter call number: QA76.73.J38
Enter title: The C Programming Language
Enter year: 1978
Book added.

--- Library Catalog Menu ---
1. Add a Book
2. Remove Oldest Book
3. Find Book by Call Number
4. Print All Books
5. EXIT
Choose an option: 1

Enter call number: CS101.5
Enter title: Introduction to Algorithms
Enter year: 1990
Book added.

--- Library Catalog Menu ---
1. Add a Book
2. Remove Oldest Book
3. Find Book by Call Number
4. Print All Books
5. EXIT
Choose an option: 4

CS101.5 | Introduction to Algorithms | 1990
QA76.73.J38 | The C Programming Language | 1978

--- Library Catalog Menu ---
1. Add a Book
2. Remove Oldest Book
3. Find Book by Call Number
4. Print All Books
5. EXIT
Choose an option: 2
Removed oldest book:
QA76.73.J38 | The C Programming Language | 1978

--- Library Catalog Menu ---
1. Add a Book
2. Remove Oldest Book
3. Find Book by Call Number
4. Print All Books
5. EXIT
Choose an option: 5
Goodbye!
```

## ### CONSTRAINTS  

- **Struct Requirement** – The primary data entity **must** be represented with a `struct Book` as described above.  
- **Function Naming** –  
  - The logic that **displays the details of ONE specific book** (used by options 2, 3, and 4) **must be placed in a function named** `void displayBook(const struct Book *b);`.  
  - All other list operations (insertion, deletion, search) should each be implemented in their own separate functions (e.g., `insertBook`, `removeOldest`, `findBook`).  
- **Menu Exit** – The menu must contain the option `5` (or the keyword `EXIT`) that cleanly terminates the program.  
- **Single‑source File** – The entire solution must be contained in a single source file (`.c` or `.cpp`).  
- **No Global Variables** – All list pointers must be passed to functions; do not use global variables to store the head of the list.  

Your program will be evaluated on correctness, adherence to the constraints, proper memory handling, and clarity of code.

---

## Problem 81 - moonshotai/kimi-k2-instruct-0905 - Iteration 61
# STEP 1: PROBLEM

## Background Story
You are helping the campus library automate its “book queue” for the checkout counter.  
Each arriving book is represented by its ID (a positive integer) and is served in strict FIFO order.  
The librarian needs a small console tool that lets her add books to the queue, serve (remove) the next book, and quickly inspect the whole queue so she knows how many patrons are still waiting.

## Functional Requirements
1. Represent a book with a single unsigned int id.
2. Implement a **singly linked list** to store the queue.
3. Provide a menu with four options:
   - 1 – Enqueue a new book (read an id from stdin; ignore duplicates)
   - 2 – Dequeue the next book (print the id of the served book or “Queue empty”)
   - 3 – Display the entire queue in order from front to rear (space-separated ids on one line, or “Queue empty”)
   - 4 – Exit the program
4. After every operation the menu must re-appear until option 4 is chosen.

## Simple Example Run
Input:
```
1 101
1 102
3
2
3
4
```
Output:
```
101 102
101
102
```
(The program terminates after the last menu choice.)

### CONSTRAINTS
- You must use a `struct` called `BookNode` to represent each linked-list node.  
- All queue logic (enqueue, dequeue, display) must be implemented inside **a single user-defined function** besides `main()`.  
- Menu option 4 must cleanly exit the program.

---

## Problem 82 - moonshotai/kimi-k2-instruct-0905 - Iteration 62
# STEP 1: PROBLEM

**Background Story**  
The campus library has a small “Book Swap” shelf where students can donate or borrow books. To keep track of what is available, the student librarian wants a tiny console program that remembers the titles in the exact order they were donated. Because the shelf is narrow, books are always added to the front (newest on the left) and removed from the front whenever someone borrows the “most-recently-donated” book (LIFO style). Your job is to implement the inventory system as a **singly linked list** that models this behavior.

---

**Program Requirements**  
1. Represent each book with a node that stores a unique title (C-string, ≤ 100 chars) and a pointer to the next node.  
2. Provide an interactive menu with the following choices:  
   1) Donate (insert a book at the head)  
   2) Borrow (remove the head book)  
   3) Show Shelf (print the current list from head to tail, one title per line)  
   4) Exit (terminate the program)  
3. After every operation, print the updated count of books on the shelf.  
4. If the user tries to borrow when the shelf is empty, print “Shelf empty – nothing to borrow.” and do not crash.  
5. No global variables for the list state; manage everything through pointers inside main().  

---

**Simple Example I/O**  
User input is shown after the prompt “Choice: ”.

```
=== Book Swap Menu ===
1) Donate
2) Borrow
3) Show Shelf
4) Exit
Choice: 1
Enter title: Clean Code
Books on shelf: 1
Choice: 1
Enter title: C Primer
Books on shelf: 2
Choice: 3
C Primer
Clean Code
Choice: 2
Borrowed: C Primer
Books on shelf: 1
Choice: 4
Goodbye!
```

---

### CONSTRAINTS  
- You must define a `struct BookNode` that contains a title array and a single forward pointer.  
- All list operations (insert at head, delete head, display) must be implemented inside **one user-defined function** besides `main()` (call it `listManager`).  
- No use of the STL containers (`std::list`, `std::vector`, etc.).  
- If a menu is implemented (and it must be), option `4` is the required EXIT keyword.

---

## Problem 83 - moonshotai/kimi-k2-instruct-0905 - Iteration 63
# STEP 1: PROBLEM

## Context
The campus library is digitizing its old card-catalogue system.  
Each catalogue card is stored as a node in a singly linked list.  
Your task is to rebuild the catalogue as a program that librarians can run at the reference desk.

## Requirements
1. Represent a catalogue card with:  
   – a unique integer ID (used as the primary key)  
   – the book’s title (single–word, ≤30 characters)  
   – the author’s last name (single–word, ≤20 characters)  
2. Maintain the cards in **ascending order of ID** inside a singly linked list.  
3. Support the following operations:  
   a. **Add** a new card (insert in sorted order; reject duplicate IDs).  
   b. **Remove** a card by ID.  
   c. **Search** for a card by ID and display its fields.  
   d. **Display** the full catalogue in order.  
4. Provide a text menu:  
   ```
   1 Add card
   2 Remove card
   3 Search card
   4 Display catalogue
   0 Exit
   ```
   The program must terminate **only** when the user chooses option 0.

## Simple Example
Input (user responses after the prompt `> `):
```
1
> 17 PridePrejudice Austen
1
> 42 Hobbit Tolkien
4
2
> 17
3
> 42
0
```
Corresponding output:
```
1 Add card
2 Remove card
3 Search card
4 Display catalogue
0 Exit
Choice: Card added.
Choice: Card added.
Choice:
ID: 17  Title: PridePrejudice  Author: Austen
ID: 42  Title: Hobbit  Author: Tolkien
Choice: Card removed.
Choice:
ID: 42  Title: Hobbit  Author: Tolkien
Choice:
```
(The menu is reprinted before each new choice.)

### CONSTRAINTS
- You **must** use a `struct` to represent each catalogue card (node).  
- The logic that prints the fields of **one** card must be placed in a function called `displayEntity`.  
- The linked-list operations (insert, delete, search, display) must be implemented in **one additional function** besides `main()`; `main()` handles the menu loop.

---

## Problem 84 - moonshotai/kimi-k2-instruct-0905 - Iteration 64
# STEP 1: PROBLEM

## Background
The campus library has an old card-catalog that is being digitised.  
Each card contains only two pieces of information:  
- a unique accession number (int)  
- the title of the book (string, no spaces)  

Because the budget is tiny, the only tool available is a command-line program that keeps these cards in memory as a **singly linked list**.  
Your task is to write that program.

## Requirements
1. The list starts empty.  
2. The program repeatedly shows a menu:  
   1. Add a new card (to the front of the list).  
   2. Remove a card by accession number.  
   3. Display every card in the order they were added (one per line: `#1234 "Moby Dick"`).  
   4. **EXIT** the program.  
3. After every operation the menu reappears until the user chooses EXIT.  
4. If the user tries to remove a non-existent accession number, print `Card not found.`  
5. All memory must be freed before the program terminates.

## Example Session
```
1
1234
Moby Dick
1
1235
Pride and Prejudice
2
1234
3
0
```
Expected output:
```
Card removed.
#1235 "Pride and Prejudice"
```
(Program ends.)

### CONSTRAINTS
- Must use a `struct` to represent each card (node).  
- The only functions allowed besides `main()` are:  
  - `void pushFront(int accNum, const char* title)`  
  - `bool removeByAccession(int accNum)`  
  - `void displayCatalog()`

---

## Problem 85 - moonshotai/kimi-k2-instruct-0905 - Iteration 65
# STEP 1: PROBLEM

## Background Story
The campus library is digitizing its old card-catalogue system.  
Each catalogue card contains a book’s accession number (a unique positive integer) and title.  
Your task is to write a tiny program that lets the librarian type in the cards in any order, then print them back in the exact same order they were entered (the librarian wants to verify that the scanner is working).

## Requirements
1. Represent each card with an accession number and a title.
2. Store the cards in the order they are read.
3. Support two commands from the keyboard:
   - `add <accession-number> "<title>"`  
     (quotes are only around the title; the accession-number is an int)
   - `print`  
     (outputs every card in the exact order they were added, one per line)
4. Stop when the keyword `exit` is entered.
5. You may assume:
   - accession-numbers are unique inside one run.
   - titles contain no more than 100 characters and may include spaces.
   - no more than 100 cards will be added.

## Simple Example
### Input
```
add 42 "The Art of Computer Programming"
add 7 "Clean Code"
print
exit
```

### Output
```
42 "The Art of Computer Programming"
7 "Clean Code"
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a catalogue card).  
- The logic for displaying the details of ONE specific card must be in a function called `displayCard`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 86 - moonshotai/kimi-k2-instruct-0905 - Iteration 66
# STEP 1: PROBLEM

## Context  
The campus library is digitizing its old card-catalogue system. Each catalogue card contains a book’s call-number, title, and author. All cards are currently stored in a shoe box in **reverse** order of insertion (the last card inserted is the first one you see). The head librarian wants a tiny program that will let a student worker rebuild the correct “front-to-back” order by only ever picking the **visible** (i.e., last-inserted) card and moving it to a second box. After every move the worker should be able to print the current contents of the second box. Once all cards are in the second box they will be in the original chronological order.

## Task  
Model the shoe box as a **singly linked stack** (LIFO) and the second box as a **singly linked queue** (FIFO).  
Implement the following operations:

1. `push <call-number> "<title>" "<author>"`  
   Add a new card to the top of the stack (box 1).  
2. `pop`  
   Remove the top card from the stack and enqueue it at the rear of the queue (box 2).  
   If the stack is empty, print `EMPTY` and do nothing.  
3. `print`  
   Display the queue from front to rear, one card per line, in the exact format shown below.  
   If the queue is empty, print `EMPTY`.  
4. `exit`  
   Terminate the program. (Option 4 in the menu.)

The program must keep processing commands until the user types `exit`.

## Example Session  
Input  
```
push 123.45 "The Art of Computer Programming" "Knuth"
push 678.90 "Introduction to Algorithms" "CLRS"
pop
print
pop
print
pop
print
exit
```

Output  
```
678.90 "Introduction to Algorithms" "CLRS"
123.45 "The Art of Computer Programming" "Knuth"
EMPTY
```

### CONSTRAINTS  
- You must use a `struct` named `Card` to represent each catalogue card.  
- All list manipulation (push, pop, enqueue, dequeue, print) must be implemented with **singly linked nodes**; no arrays or STL containers.  
- The only functions besides `main()` allowed are:  
  – `void push(...)`, `Card* pop()`, `void enqueue(Card*)`, `void printQueue()`, and `int main()`.

---

## Problem 87 - moonshotai/kimi-k2-instruct-0905 - Iteration 67
# STEP 1: PROBLEM  
**Topic:** Implementing Data Structures – Singly Linked Lists  

### Background Story  
The campus library has a “Fast-Return” box where students drop books after hours. A student volunteer must log each returned book into a digital ledger so the librarians can process them the next morning. The only tool available is a tiny Raspberry Pi that can run a single C program with no dynamic arrays (because of memory limits). Your task is to build a minimalist ledger that keeps the books in the order they arrived and lets the volunteer:  
1. Record a new returned book.  
2. Check how many books are currently in the box.  
3. Remove the first book from the ledger (it has just been processed by a librarian).  
4. Display the full current list of waiting books.  
5. Exit the program.  

### Requirements (what the program must do)  
1. Represent each book with at least:  
   - A unique ID (positive integer)  
   - Title (single string, ≤ 50 characters, no spaces)  
2. Maintain the books in a singly linked list in the order they were recorded.  
3. Provide a console menu with the five options above.  
4. After every successful operation, print a short confirmation (see example).  
5. Handle the empty-list case gracefully with the message “Ledger is empty.” when needed.  

### Example Session (user input after `>`)  
```
1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 1
Enter ID: 101
Enter title: C_Programming
Recorded: 101 C_Programming

1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 1
Enter ID: 102
Enter title: Data_Structures
Recorded: 102 Data_Structures

1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 2
Total books: 2

1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 4
101 C_Programming
102 Data_Structures

1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 3
Processed: 101 C_Programming

1. Record new book
2. Show total books
3. Process first book
4. List all books
5. Exit
> 5
Good-bye!
```

### CONSTRAINTS  
1. Must use a `struct` to represent the primary data entity (a book node).  
2. Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
3. The solution must be implemented with a single function besides `main()`.  
4. Menu option 5 must EXIT the program.

---

## Problem 88 - moonshotai/kimi-k2-instruct-0905 - Iteration 68
# STEP 1: PROBLEM

## Background Story
The university’s “Lost & Found” office is overwhelmed with unclaimed items.  
They have asked the CS department to build a tiny console app that keeps track of items as they arrive and as they are claimed.  
Each item has only three pieces of information: a unique integer ID (assigned by the system), a short description (one word, ≤ 20 characters), and the date it was found (dd-mm-yyyy).

You will implement this tracker as a **singly linked list** that grows when items are added and shrinks when items are claimed (deleted).

---

## Functional Requirements
1. When the program starts, the list is empty.
2. The program repeatedly prints a menu:
   ```
   1) Add new found item
   2) Claim (delete) an item by ID
   3) Show all items currently stored
   4) Exit
   ```
3. Option 1: Prompt for description and date, create a node, assign the next free ID (start at 1000 and increment), insert at the **tail** of the list, and print `Item added with ID <id>`.
4. Option 2: Prompt for an ID; if that ID exists, remove the corresponding node and print `Item <id> claimed.`; otherwise print `ID not found.`
5. Option 3: Print one line per item in the order they were added:
   ```
   ID: <id>, Desc: <description>, Date: <date>
   ```
   If the list is empty, print `No items.`
6. Option 4: Print `Good-bye.` and terminate.

---

## Simple Example Run
```
1) Add new found item
2) Claim (delete) an item by ID
3) Show all items currently stored
4) Exit
Choice: 1
Description: Umbrella
Date: 12-04-2024
Item added with ID 1000

Choice: 1
Description: WaterBottle
Date: 13-04-2024
Item added with ID 1001

Choice: 3
ID: 1000, Desc: Umbrella, Date: 12-04-2024
ID: 1001, Desc: WaterBottle, Date: 13-04-2024

Choice: 2
ID to claim: 1000
Item 1000 claimed.

Choice: 3
ID: 1001, Desc: WaterBottle, Date: 13-04-2024

Choice: 4
Good-bye.
```

---

### CONSTRAINTS
- You **must** use a `struct` to represent each node (item).  
- All list operations (add, delete, display) must be implemented with **exactly one user-defined function besides `main()`**; you may choose its signature.

---

## Problem 89 - moonshotai/kimi-k2-instruct-0905 - Iteration 69
# STEP 1: PROBLEM

**Background Story**  
The campus library is digitizing its old card-catalog. Each card contains a book’s title and its accession number (a unique integer). Your task is to write a mini-catalog program that stores these cards in memory as a singly linked list and lets the librarian add, delete, and search cards. Because the cards are fragile, the librarian must be able to reconstruct the exact order in which they were added (so the list is always append-only at the tail).

**Precise Requirements**  
1. Represent each catalog card as a node with two data fields:  
   - `int accession` – unique across the catalog.  
   - `char title[41]` – at most 40 printable characters plus terminating `\0`.  
2. Maintain a singly linked list that always appends new cards at the tail.  
3. Provide a text menu that repeatedly offers:  
   1. Add a new card (read accession number and title).  
   2. Delete a card by accession number (if present).  
   3. Search for a card by accession number and display its title.  
   4. Display the entire catalog in order (one line per card: `accession: title`).  
   5. Exit the program.  
4. After every successful add, delete, or search, print the updated count of cards currently in the catalog.  
5. If the user tries to add a duplicate accession number, print `Duplicate accession ignored.` and do **not** modify the list.

**Simple Example Run**  
Input:
```
1
101
Pride and Prejudice
1
102
The Hobbit
3
101
5
```
Output:
```
1 card(s) in catalog
2 card(s) in catalog
101: Pride and Prejudice
Goodbye!
```

### CONSTRAINTS  
- Must use a `struct` to represent each catalog card (node).  
- All list operations (add, delete, search, display) must be implemented in **one user-defined function** besides `main()`.  
- Menu option `5` (or the keyword `exit`) must terminate the program cleanly.

---

## Problem 90 - moonshotai/kimi-k2-instruct-0905 - Iteration 70
# STEP 1: PROBLEM

## Context
The campus library is tired of its paper-and-pencil waiting list for study rooms.  
They have hired you to build a tiny, stand-alone console program that keeps the queue strictly in memory (no files).  
A student may only request the next available room; when a room is freed, the first student in line is automatically assigned that room and removed from the queue.  
You must implement this “room-waiting list” with a **singly linked list** that stores the students’ names.

## Functional Requirements
1. The program must display a numbered menu:
   1. Join waiting list  
   2. Serve next student (remove head & print name)  
   3. Show current waiting list  
   4. Exit program  
2. Option 1 reads a single name and appends it to the **tail** of the list, printing confirmation.  
3. Option 2 removes the **head** (earliest arrival) and prints the served student’s name.  
4. Option 3 prints the names in order, one per line, or prints “List is empty.”  
5. All dynamic memory must be freed before program termination.

## Simple Example Run
```
1. Join waiting list  
2. Serve next student  
3. Show current waiting list  
4. Exit  
Enter choice: 1  
Enter student name: Ada  
Ada joined the queue.  

Enter choice: 1  
Enter student name: Grace  
Grace joined the queue.  

Enter choice: 3  
Current queue:  
Ada  
Grace  

Enter choice: 2  
Ada has been served.  

Enter choice: 4  
Good-bye!
```

## CONSTRAINTS
- Must use a `struct Node` to represent each list element.  
- All list operations (append, serve, display) must be implemented in **one single function** besides `main()`; that function must take a `char` command character and perform the requested action.  
- The menu option to EXIT is number 4.

---

## Problem 91 - moonshotai/kimi-k2-instruct-0905 - Iteration 71
# STEP 1: PROBLEM

## Background Story
The university’s Music Library is outdated: every time a student wants to know which songs are available, the librarian has to flip through a paper notebook.  
Your task is to digitise the notebook by writing a tiny catalog that keeps the songs in the order they were added (a singly linked list).  
Each song stores its title and the artist’s name.

## Functional Requirements
1. The program must keep the songs in a singly linked list.
2. It must support the following menu-driven operations:
   1. Add a new song (append to the end).  
   2. Remove the first song that matches a given title (exact, case-sensitive).  
   3. Display the entire catalog in order (one line per song: “Title – Artist”).  
   4. EXIT the program.  
3. After every operation (except EXIT) the menu must re-appear.
4. If an operation cannot be completed (e.g., remove on an empty list), print the exact message:  
   `Cannot perform operation: list is empty.`

## Simple Example Run
```
1. Add song
2. Remove song by title
3. Show catalog
4. EXIT
Choice: 1
Title: Bohemian Rhapsody
Artist: Queen
1. Add song
2. Remove song by title
3. Show catalog
4. EXIT
Choice: 3
Bohemian Rhapsody – Queen
1. Add song
2. Remove song by title
3. Show catalog
4. EXIT
Choice: 4
Goodbye!
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (a song node).  
- Logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.

---

## Problem 92 - moonshotai/kimi-k2-instruct-0905 - Iteration 72
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a “Tech-for-Checkout” kiosk where students can borrow one of 20 identical Wi-Fi hotspots.  
Instead of a database, the kiosk uses a tiny embedded board that only supports standard C.  
Your task is to write the checkout/return system for the kiosk using a **singly linked list** that stores the student ID of each person who currently has a device.

## Functional Requirements
1. Maintain a singly linked list of currently-checked-out hotspots.
2. Provide a menu with these four options:
   - 1) Borrow – add the caller’s 8-digit student ID to the list **only if** the list has < 20 nodes; otherwise print “All hotspots in use.”
   - 2) Return – remove the node that contains the caller’s student ID; if ID not found print “No record found.”
   - 3) Display – print every currently borrowed ID in the order they were borrowed (one ID per line).
   - 4) Exit – terminate the program immediately (use option 4).

## Simple Example Run
```
1) Borrow
2) Return
3) Display
4) Exit
Choice: 1
Enter student ID: 87654321
1) Borrow
2) Return
3) Display
4) Exit
Choice: 3
87654321
1) Borrow
2) Return
3) Display
4) Exit
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Must use a `struct` to represent the primary data entity (the list node).
- The only functions allowed besides `main()` are:
  - `borrowNode(unsigned int id)`
  - `returnNode(unsigned int id)`
  - `displayList()`
- No global variables except a single pointer to the head of the list.

---

## Problem 93 - moonshotai/kimi-k2-instruct-0905 - Iteration 73
# STEP 1: PROBLEM  
**Background:** A local music festival uses a “Song Queue” that visitors can edit in real-time on a kiosk. The queue is a singly linked list where each node stores the song title (a single string of ≤30 characters) and the requester’s name (a single string of ≤20 characters). Visitors can add songs, remove the currently playing song (always at the head), or print the entire queue.  

**Requirements:**  
1. Represent each song request as a node in a singly linked list.  
2. Provide a menu with the following options:  
   1) Add song to the tail of the queue  
   2) Play current song (remove head node and display its info)  
   3) Print the full queue (from head to tail)  
   4) Exit  
3. After every operation, re-display the menu until the user chooses Exit.  
4. If the queue is empty and the user chooses option 2 or 3, print “Queue is empty.”  

**Simple Example (user input shown after ">"):**  
```
1) Add  2) Play  3) Print  4) Exit
Choice > 1
Song title > Bohemian Rhapsody
Requester  > Alice
1) Add  2) Play  3) Print  4) Exit
Choice > 1
Song title > Imagine
Requester  > Bob
1) Add  2) Play  3) Print  4) Exit
Choice > 3
Queue:
Bohemian Rhapsody (Alice)
Imagine (Bob)
1) Add  2) Play  3) Print  4) Exit
Choice > 2
Now playing: Bohemian Rhapsody (Alice)
1) Add  2) Play  3) Print  4) Exit
Choice > 4
Goodbye!
```

### CONSTRAINTS  
- Must use a `struct` to represent the primary data entity (the node).  
- The logic for displaying the details of ONE specific entity must be in a function called `displayEntity`.  
- The solution must be implemented with a single function besides `main()`.  
- The menu option to EXIT the program is option 4.

---

## Problem 94 - moonshotai/kimi-k2-instruct-0905 - Iteration 74
# STEP 1: PROBLEM

**Background Story**  
The campus library is digitizing its old card-catalog. Each card contains a book’s call-number, title, and year. The student-jobs team has decided to store these cards in a singly linked list so new cards can be inserted while preserving lexicographic order of call-numbers. Your program will simulate this tiny catalog by letting the user add books, list them, and—because the head-librarian is impatient—immediately quit when requested.

**Functional Requirements**  
1. Represent a book with three fields:  
   - call-number (string, unique key)  
   - title (string)  
   - year (positive int)  
2. Maintain the books in strictly increasing lexicographic order of call-number.  
3. Support two user commands:  
   - `ADD` – read one book’s data and insert it into the correct position; if the call-number already exists, silently ignore the request.  
   - `LIST` – print every book in order, one line per book, with a single space separating call-number, title, and year.  
4. Provide a clean way to terminate the program.  
5. Implement everything with a singly linked list you create from scratch—no STL/Java collections/Python lists.

**Simple Example**  
Input  
```
ADD
QA76.73.C26S37
C++ Primer 5th ed
2012
ADD
QA76.73.P224L77
Learning Python 5th ed
2013
LIST
EXIT
```
Output  
```
QA76.73.C26S37 C++ Primer 5th ed 2012
QA76.73.P224L77 Learning Python 5th ed 2013
```

### CONSTRAINTS  
- Must use a `struct` (or `class`) named `BookNode` to represent each list node.  
- All list operations (insert, print) must be implemented in exactly one user-defined function besides `main()`; `main()` should only handle the menu loop.  
- The menu option to EXIT the program is the integer `0`.

---

## Problem 95 - moonshotai/kimi-k2-instruct-0905 - Iteration 75
# STEP 1: PROBLEM

## Background Story
The campus library has just opened a 24-hour “Tech Help Window” where students can drop-off USB drives that need to be scanned for viruses. Each USB drive is tagged with a unique serial number and the owner’s e-mail. To keep things fair, the drives must be serviced in the exact order they arrive. You volunteer to write a tiny management system that keeps track of this queue.

## Required Functionality
1. Represent the queue of USB drives with a **singly linked list**.
2. Provide a text menu with the following choices:
   - 1) Drop-off a new USB drive (enqueue)
   - 2) Service the next USB drive (dequeue)
   - 3) Display the current queue
   - 4) Exit the program
3. On enqueue, read a serial number (positive integer) and an owner e-mail (string without spaces).
4. On dequeue, print the serial number and e-mail of the drive being removed; if the queue is empty, print “Queue empty”.
5. Display the queue from front to back in a single line, each element as `(serial#:email)` separated by `->` and ending with `NULL`.

## Simple Example Run
Input:
```
1
101 alice@uni.edu
1
102 bob@uni.edu
3
2
3
4
```
Expected Output:
```
Menu:
1) Drop-off
2) Service
3) Display
4) Exit
Choice: 1
Enter serial# email: 101 alice@uni.edu
Menu...
Choice: 1
Enter serial# email: 102 bob@uni.edu
Menu...
Choice: 3
Queue: (101:alice@uni.edu)->(102:bob@uni.edu)->NULL
Menu...
Choice: 2
Serviced: 101 alice@uni.edu
Menu...
Choice: 3
Queue: (102:bob@uni.edu)->NULL
Menu...
Choice: 4
Good-bye!
```

### CONSTRAINTS
- Represent each USB drive with a `struct` called `USBDrive`.
- The logic that prints a single node (serial and email) must be in a function called `displayEntity`.
- The entire solution must implement the linked-list operations in only one additional function besides `main()` (i.e., one helper function total).
- Menu option `4` is the only way to exit the program.

---

## Problem 96 - moonshotai/kimi-k2-instruct-0905 - Iteration 76
# STEP 1: PROBLEM  
**Story:**  
The campus library has a “Take-a-Book, Leave-a-Book” shelf. To keep track of which paperbacks are currently available, the student volunteer on duty needs a tiny console program that remembers the titles in the exact order they were added. Because the shelf is just a row of books, the program must behave like a queue: new books are always placed at the back, and when a patron borrows one, the book at the front is removed.  

Your task is to implement this queue with a singly linked list. Each book is represented only by its title (one word, ≤30 characters, no spaces).  

**Requirements:**  
1. Start with an empty shelf.  
2. Support three commands:  
   - `ADD <title>` – enqueue a new book (add at rear).  
   - `BORROW` – dequeue the oldest book (remove from front) and print `Borrowed: <title>`.  
   - `SHELF` – print the current queue from oldest to newest, one title per line.  
3. If `BORROW` is attempted when the shelf is empty, print `Nothing to borrow.`  
4. Stop the program only when the command `EXIT` is entered.  

**Example session (user input after `>`):**  
```
> ADD Dune  
> ADD Neuromancer  
> SHELF  
Dune  
Neuromancer  
> BORROW  
Borrowed: Dune  
> ADD SnowCrash  
> SHELF  
Neuromancer  
SnowCrash  
> EXIT  
```

### CONSTRAINTS  
- Must use a `struct` called `Book` to represent each node (data + next pointer).  
- The entire queue logic (add, remove, display) must be implemented in a **single function** besides `main()`.  
- `EXIT` is option `0` in the menu and must terminate the program cleanly.

---

## Problem 97 - moonshotai/kimi-k2-instruct-0905 - Iteration 77
# STEP 1: PROBLEM

## Context
The campus library is tired of losing track of which books are currently checked out.  
They hire you to build a tiny, text-based inventory system that records the title of each book and keeps them in the exact order they were added.  
Because the collection is small, the library wants you to store the data in a **singly linked list** that you implement yourself.

## Requirements
1. Represent each book with a node that stores:
   - A unique title (one string, no spaces, ≤ 30 characters)
   - A pointer to the next node
2. Provide a menu with exactly four choices:
   1. Add a new book (appends to the end of the list)
   2. Display all books in order, one per line
   3. Remove the first book that matches a given title (exact match, case-sensitive)
   4. Exit the program
3. After every operation, re-show the menu unless the user chose Exit.
4. Handle an empty list gracefully (print nothing for display, print “Not found” for removal).

## Simple Example Run
```
1
Neuromancer
2
1
SnowCrash
2
3
Neuromancer
2
4
```
Expected output:
```
Neuromancer
SnowCrash
SnowCrash
```
(The last blank line is the program terminating.)

### CONSTRAINTS
- You must use a `struct` to represent the primary data entity (the book node).  
- All pointer manipulations (creation, insertion, deletion) must be done manually—no STL or Java Collections.  
- The only functions allowed besides `main()` are:  
  - `void addBook(const string& title)`  
  - `void displayBooks()`  
  - `void removeBook(const string& title)`  
- Menu option 4 is the **only** way to exit the program.

---

## Problem 98 - moonshotai/kimi-k2-instruct-0905 - Iteration 78
# STEP 1: PROBLEM  
**Topic:** Implementing a Singly Linked List  

**Background Story**  
The campus library has asked the CS department for help. They lend e-book readers to students, but keeping track of who has which device—and in what order they were checked out—has become chaotic. Your task is to write a miniature “e-reader check-out system” that records each reader’s 4-digit ID and the time (in whole minutes since midnight) it was checked out. The system must keep the list in the exact order in which the readers were borrowed. Because new readers are checked out all day, you must implement a **singly linked list** so that insertions are always O(1) at the front and traversals are O(n).

**Functional Requirements**  
1. Represent each e-reader checkout with two integers: `id` (4-digit, 0000-9999) and `time` (0-1439).  
2. Provide a text menu with exactly these four options:  
   - `1` Add a checkout (insert at head, rejecting any `id` that is already in the list).  
   - `2` Display all checkouts in the order they were added (newest first).  
   - `3` Return (delete) a checkout given its `id`; print “Not found” if it does not exist.  
   - `4` Exit the program.  
3. After every successful operation, print the count of currently checked-out readers.  
4. All list manipulation must be done **only** through pointer manipulation; no arrays or STL containers.

**Simple Example Run**  
```
1
1010 720
Added, total 1

1
2020 800
Added, total 2

2
1010 720
2020 800

3
1010
Returned, total 1

2
2020 800

4
Good-bye!
```

### CONSTRAINTS  
- Must use a `struct` named `Node` to represent each checkout.  
- All list operations (insert, delete, display) must be implemented in a **single function** besides `main()`.  
- Menu option `4` is the **only** way to terminate the program.

---

## Problem 99 - moonshotai/kimi-k2-instruct-0905 - Iteration 79
# STEP 1: PROBLEM

## Background Story
You are interning at the campus library, which has just started a “read-one, donate-one” program.  
Every time a student finishes a book, they can donate it to the library by adding it to a *donation shelf*.  
The shelf is really just a linked chain of books hanging on strings, so the only practical way to add or remove a book is at the *front* of the chain.  
Your job is to write the tiny inventory system that keeps track of these donated books.

## Requirements
1. Represent each book with at least the following information:
   - a unique ID (positive integer)
   - title (single string, no spaces)
   - genre (single string, no spaces)

2. Maintain the donation shelf as a **singly linked list** whose head pointer always points at the most-recently donated book.

3. Implement exactly three operations:
   - **Add**: create a new book and insert it **at the front** of the list.
   - **Remove**: delete the book **at the front** of the list (the one that was most-recently donated).  
     If the shelf is empty, print `Shelf is empty`.
   - **Display**: print the inventory from most-recent to oldest, one book per line in the exact format  
     `ID title (genre)`

4. The program must present a menu to the user with the following choices:
   1. Add a book  
   2. Remove a book  
   3. Display shelf  
   4. Exit  

5. After every operation (except Exit), re-display the menu.

## Simple Example Run
```
1. Add a book
2. Remove a book  
3. Display shelf
4. Exit
Choice: 1
Enter ID title genre: 101 Algorithms CS  
1. Add a book
2. Remove a book
3. Display shelf
4. Exit
Choice: 1
Enter ID title genre: 102 PythonIntro CS  
1. Add a book
2. Remove a book
3. Display shelf
4. Exit
Choice: 3
102 PythonIntro (CS)
101 Algorithms (CS)
1. Add a book
2. Remove a book
3. Display shelf
4. Exit
Choice: 2
1. Add a book
2. Remove a book
3. Display shelf
4. Exit
Choice: 3
101 Algorithms (CS)
1. Add a book
2. Remove a book
3. Display shelf
4. Exit
Choice: 4
```

### CONSTRAINTS
- You must use a `struct` to represent each book node.  
- All list operations (add, remove, display) must be implemented in *one* user-defined function called `manageShelf()`; `main()` is allowed only to handle user interaction.

---

## Problem 100 - moonshotai/kimi-k2-instruct-0905 - Iteration 80
# STEP 1: PROBLEM

## Context
The campus library has just digitised its old card-catalogue system.  
Each catalogue card contains a single book’s information: a unique ID (integer) and its title (string).  
All cards are stored in a box in **no particular order**; they are chained together with pieces of string in the exact order they were added.  
Your task is to write a tiny program that mimics this box of cards using a **singly linked list** so that the librarian can:
- add a new card to the front of the box (fastest place to reach),
- search for a card by its ID,
- remove a card by its ID, and
- print every card currently in the box (in the same order they were added).

## Functional Requirements
1. Represent each card as a node that stores an integer ID and a string title.
2. Maintain the nodes as a singly linked list.
3. Provide a text menu with the following four options (and nothing else):
   1. Add card  
   2. Search card  
   3. Remove card  
   4. Print catalogue  
   5. Exit  
4. For **Add card**, read an ID and title from stdin and insert the node at the **head** of the list.  
5. For **Search card**, read an ID and print either  
   `Found: <title>` or `Not found`.  
6. For **Remove card**, read an ID.  
   - If the ID exists, delete that node and print `Removed`.  
   - Otherwise print `ID not found`.  
7. For **Print catalogue**, print every card in the list in **one line** in the format  
   `[ID] Title; [ID] Title; ...`  
   (no trailing semicolon).  
   If the list is empty, print `Empty catalogue`.

## Simple Example Run
Input  
```
1
7
The Little Prince
2
7
3
7
4
5
```
Output  
```
Added
Found: The Little Prince
Removed
Empty catalogue
```
(The program then terminates because the user chose option 5.)

### CONSTRAINTS
- You **must** use a `struct` to represent the primary data entity (the card/node).  
- All list operations (add, search, remove, print) must be implemented in **one single function** besides `main()`.  
- The menu option to **Exit the program** is number **5**.

---

