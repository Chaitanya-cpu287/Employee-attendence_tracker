# Employee Attendance Management System (C — Doubly Linked List)

A high-performance, console-based Employee Attendance Management System implemented in **C**. Designed to demonstrate practical applications of dynamic data structures, manual heap memory management (`malloc` / `free`), and pointer manipulation using a **Doubly Linked List (DLL)**.

---

## Key Features

- **Dynamic Record Management:** Add and deregister employee records dynamically at runtime without static array boundaries.
- **Attendance Verification:** Mark employee status (`Present` / `Absent`) with date stamping and status toggles.
- **Fast Search & In-Place Updates:** Lookup employee details by unique ID with instant update capabilities.
- **Data Integrity & Validation:** Prevents duplicate ID assignments and safely handles boundary conditions (empty list, single node, deletion of head/tail nodes).
- **Statistical Summaries:** Generates aggregated attendance ratios (Present vs. Absent counts) for shift management.
- **Bidirectional Traversal:** Leverages forward (`next`) and backward (`prev`) pointers for intuitive traversal.

---

## Algorithmic Complexity

| Operation | Time Complexity | Space Complexity | Description |
| :--- | :--- | :--- | :--- |
| **Insert Employee (Tail)** | O(n) | O(1) | Appends a new dynamically allocated node to the list |
| **Search by ID** | O(n) | O(1) | Linear traversal comparing unique employee identifiers |
| **Delete by ID** | O(n) | O(1) | Locates node and safely updates adjacent `prev` and `next` pointers |
| **Mark Attendance** | O(n) | O(1) | Searches for ID and updates attendance state flag |
| **Generate Report** | O(n) | O(1) | Traverses full list to compute aggregate counts |

---

## Data Structure Architecture

```
         +-------------------------------------------------------+
         |                     DLL Node                          |
         |  [prev*] <--> [ID | Name | Attendance] <--> [next*]   |
         +-------------------------------------------------------+
            ^                                             ^
            |                                             |
   Head Node (Employee 1)                       Tail Node (Employee N)
```

Each employee is represented by a dynamically allocated `struct Node`:
```c
struct Node {
    int id;
    char name[50];
    int is_present;
    struct Node* prev;
    struct Node* next;
};
```

---

## Build and Execution

### Prerequisites
- C compiler (`gcc`, `clang`, or MSVC).

### Compilation

```bash
# Compile with GCC and standard warnings enabled
gcc -Wall -Wextra -std=c99 project.c -o attendance_tracker

# Execute on Linux/macOS
./attendance_tracker

# Execute on Windows
attendance_tracker.exe
```

---

## Memory Safety & Cleanup

- Every inserted node is allocated via `malloc(sizeof(struct Node))`.
- On record deletion and system exit, nodes are systematically traversed and deallocated using `free()` to prevent heap memory leaks.
