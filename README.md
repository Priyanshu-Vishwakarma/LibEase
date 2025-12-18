# LibEase - C++ Library Management System

![C++](https://img.shields.io/badge/Language-C++-blue) ![CMake](https://img.shields.io/badge/Build-CMake-green) ![Storage](https://img.shields.io/badge/Data-CSV-orange)

**LibEase** is a lightweight, command-line interface (CLI) application designed to streamline library operations. It manages books and members efficiently using **Object-Oriented Programming (OOP)** principles and persistent **CSV file handling**. 

It removes the need for manual notebooks by automating book issuing, returning, and searching processes.

---

## Key Features

### Book Management
* **Add Books:** Auto-generates unique IDs for every new book.
* **Search:** Find books instantly by title.
* **Display:** View all available books in a formatted table.
* **Issue & Return:** Tracks book status (Borrowed/Available) and updates records in real-time.

### User Management & Security
* **Registration & Login:** Secure member access.
* **Profile Management:** Edit usernames and passwords.
* **Encryption:** Passwords are encoded using the **ROT13 algorithm** before storage.

### System Architecture
* **Persistence:** Data is saved in `books.csv` and `members.csv`, ensuring data survives after the program closes.
* **Robust Updates:** Uses temporary files to safely update records without data corruption.
* **Formatting:** Includes helper functions for clean UI (banners, spacing, menus).

---

## Project Structure

The project follows a clean separation of concerns:

```text
LibEase/
├── bin/                 # Contains the compiled executable (created after build)
├── build/               # Temporary CMake build files
├── data/                # Persistent storage
│   ├── books.csv        # Stores: id, title, author, year, status
│   └── members.csv      # Stores: username, encoded_password
├── include/             # Header files (Declarations)
│   ├── Auth.hpp         # Auth class
│   ├── Book.hpp         # Book class
│   ├── User.hpp         # User class
│   └── Utils.hpp        # Helper functions
├── src/                 # Source code (Implementations)
│   ├── main.cpp         # Entry point
│   ├── add_book.cpp     # Logic to add books
│   ├── auth.cpp         # Logic for login/register
│   ├── utils.cpp        # UI and helper logic
│   └── ...              # Other feature implementations
├── CMakeLists.txt       # CMake build configuration
└── README.md            # Project documentation


---

### How to Build and Run
This project uses CMake for easy cross-platform compilation.
Prerequisites
C++ Compiler (GCC/Clang/MSVC)
CMake (Version 3.10 or higher)

Installation Steps
Clone the repository (or download source):
Bash
git clone [https://github.com/your-username/LibEase.git](https://github.com/your-username/LibEase.git)
cd LibEase
Create a build directory:
Bash
mkdir build
cd build
Generate build files with CMake:
Bash
cmake ..
Compile the project:
Bash
make
(On Windows with MinGW, use mingw32-make)
Run the application:
Bash
./bin/libraryx

#Technical Highlights
OOP Design: Uses Encapsulation to protect data within Book and User classes and Abstraction to hide complex file I/O logic from the main menu.
File Handling: Implements std::fstream for reading/writing. Updates are handled by writing to a temp.csv, deleting the old file, and renaming the temp file to prevent data loss.
String Manipulation: Custom utilities to handle CSV parsing (replacing spaces with dashes) and table formatting.

# Future Improvements
xImplement a visual GUI.
Add an Admin role for managing users.
Migrate from CSV to SQL Database (SQLite/MySQL).
Add "Due Date" calculation for issued books.
