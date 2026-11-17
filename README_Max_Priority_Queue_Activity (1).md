# Laboratory Activity: Max Priority Queue in JavaScript

## Hospital Emergency Room Management System

**Language:** JavaScript (Node.js)\
**Topic:** Max Priority Queue using Arrays, `findIndex()`, and
`readline`\
**Total Points:** 50\
**Suggested Time:** 45--60 minutes

------------------------------------------------------------------------

## 1. Activity Overview

A hospital emergency room needs a simple system to organize patients
based on the seriousness of their medical conditions.

In this activity, you will create a **Max Priority Queue**. Patients
with higher priority numbers must be served before patients with lower
priority numbers.

You will implement a `PriorityQueue` class and create a menu-driven
program that allows users to add, serve, and view patients.

## 2. Priority Rules

    Priority Description
  ---------- ------------------------------
           3 Critical -- Highest priority
           2 Serious -- Medium priority
           1 Minor -- Lowest priority

### Important Rules

-   The patient with the **highest priority number** must be served
    first.
-   If two or more patients have the same priority, the patient who
    arrived first must be served first (FIFO).
-   A priority of `3` is higher than `2`, and `2` is higher than `1`.

## 3. Learning Objectives

After completing this activity, you should be able to:

1.  Implement a Max Priority Queue using a JavaScript array.
2.  Use `findIndex()` to locate the correct insertion position.
3.  Use `splice()` and `push()` to insert elements.
4.  Implement basic Priority Queue operations.
5.  Use Node.js `readline` to accept user input.
6.  Create a menu-driven JavaScript program.

## 4. Program Requirements

Create a class named `PriorityQueue` with the following methods:

  ---------------------------------------------------------------------
  Method                             Description
  ---------------------------------- ----------------------------------
  `enqueue(name, priority)`          Adds a patient in the correct
                                     priority position.

  `dequeue()`                        Removes and returns the patient
                                     with the highest priority.

  `front()`                          Returns the next patient without
                                     removing them.

  `isEmpty()`                        Checks whether the queue has no
                                     patients.

  `size()`                           Returns the number of patients.

  `display()`                        Displays all patients in priority
                                     order.
  ---------------------------------------------------------------------

### Required Implementation

For the `enqueue()` method, use:

``` javascript
let index = this.items.findIndex(
    current => priority > current.priority
);
```

This checks for the first existing patient whose priority is lower than
the new patient's priority.

-   If `index === -1`, add the new patient at the end using `push()`.
-   Otherwise, insert the new patient at the found position using
    `splice(index, 0, item)`.
-   Use `>` and not `>=` so patients with equal priority remain in
    arrival order.

## 5. Menu Requirements

Your program must display this menu:

``` text
===== HOSPITAL EMERGENCY ROOM =====
1. Add Patient
2. Serve Patient
3. View Next Patient
4. Display All Patients
5. Display Queue Size
6. Exit
```

The program must use Node.js `readline` to receive the user's menu
choice, patient name, and priority.

### Menu Operations

1.  **Add Patient** -- Ask for the patient's name and priority. Accept
    only whole-number priorities from 1 to 3.
2.  **Serve Patient** -- Remove and display the patient with the highest
    priority. If the queue is empty, display an appropriate message.
3.  **View Next Patient** -- Display the next patient without removing
    them.
4.  **Display All Patients** -- Show all patients from highest to lowest
    priority.
5.  **Display Queue Size** -- Show the number of patients currently
    waiting.
6.  **Exit** -- End the program.

## 6. Initial Test Records

Use these records to test your program. Add them in the exact order
shown:

  Patient     Priority
  --------- ----------
  Mark               1
  Ana                3
  John               2
  Peter              3
  Sarah              1

### Expected Queue Order

After adding all five patients, the queue should be:

``` text
Ana - Priority 3
Peter - Priority 3
John - Priority 2
Mark - Priority 1
Sarah - Priority 1
```

### Expected Serving Order

If all patients are served one by one, the order should be:

``` text
Ana
Peter
John
Mark
Sarah
```

Notice that Ana is served before Peter because both have priority 3, but
Ana arrived first.

## 7. Student Tasks

Complete the starter code provided by your instructor.

1.  Complete all sections marked `TODO`.
2.  Implement `enqueue()` using `findIndex()`.
3.  Implement `dequeue()` and `front()`.
4.  Implement `isEmpty()` and `size()`.
5.  Complete the `display()` method.
6.  Complete the menu operations using `readline`.
7.  Validate all required patient information before inserting a record into the queue.
   **Expected behavior:**
    1. Empty patient name → Reject.
    2. Empty patient ID → Reject.
    3. Duplicate patient record → Reject.
    4. Invalid priority → Reject.
    5. Valid, unique patient record → Accept and enqueue.

Dequeue or front when the queue is empty → Display an appropriate message instead of causing an error.
8.  Validate the priority input so only `1`, `2`, or `3` is accepted.
9.  Run and test your program using the initial test records.
10.  Test what happens when you try to serve or view a patient while the
    queue is empty.

## 8. Submission Requirements

Submit your completed JavaScript source file.

Your submission must:

-   Contain the completed `PriorityQueue` class.
-   Include the menu-driven program using `readline`.
-   Run without syntax or runtime errors.
-   Correctly follow the Max Priority Queue rules.
-   Display the correct patient order and serving order.

## 9. Rubric

  Criteria                                    Points
  ----------------------------------------- --------
  Correct `enqueue()` using `findIndex()`         15
  Correct `dequeue()` and `front()`               10
  Correct `isEmpty()` and `size()`                 5
  Correct `display()`                              5
  Correct `readline` menu and operations          10
  Correct output and program execution             5
  **Total**                                   **50**

## 10. Important Reminders

-   This activity uses a **Max Priority Queue**.
-   Higher priority numbers are served first.
-   Priority `3` is the highest; priority `1` is the lowest.
-   Equal priorities must follow FIFO order.
-   Do not use `>=` in the `findIndex()` condition because it would
    place a new patient ahead of an existing patient with the same
    priority.
-   Test your program before submitting.

**Good luck!**

## 11. Overall Starter Code Template

Copy the following template into a JavaScript file named
`priority_queue.js`. Complete every section marked `TODO`.

``` javascript
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

class PriorityQueue {
    constructor() {
        this.items = [];
    }

    // Add a patient according to priority
    enqueue(name, priority) {
        let item = {
            name: name,
            priority: priority
        };

        // TODO 1: Find the correct insertion position using findIndex()
        let index = ______________________________;

        // TODO 2: Insert the patient in the correct position
        if (index === -1) {
            ______________________________;
        } else {
            ______________________________;
        }
    }

    // Remove and return the patient with the highest priority
    dequeue() {
        if (this.isEmpty()) {
            return null;
        }

        // TODO 3: Remove and return the first patient
        return ______________________________;
    }

    // Return the next patient without removing them
    front() {
        if (this.isEmpty()) {
            return null;
        }

        // TODO 4: Return the first patient
        return ______________________________;
    }

    // Check whether the queue is empty
    isEmpty() {
        // TODO 5
        return ______________________________;
    }

    // Return the number of patients
    size() {
        // TODO 6
        return ______________________________;
    }

    // Display all patients
    display() {
        if (this.isEmpty()) {
            console.log("No patients in the queue.");
            return;
        }

        console.log("\\n--- PATIENT QUEUE ---");

        // TODO 7: Display each patient's name and priority
        for (let i = 0; i < this.items.length; i++) {
            // Your code here
        }
    }
}

let queue = new PriorityQueue();

function showMenu() {
    console.log("\\n===== HOSPITAL EMERGENCY ROOM =====");
    console.log("1. Add Patient");
    console.log("2. Serve Patient");
    console.log("3. View Next Patient");
    console.log("4. Display All Patients");
    console.log("5. Display Queue Size");
    console.log("6. Exit");

    rl.question("Choose an option: ", function(choice) {
        switch (choice) {
            case "1":
                addPatient();
                break;

            case "2":
                servePatient();
                break;

            case "3":
                viewNextPatient();
                break;

            case "4":
                queue.display();
                showMenu();
                break;

            case "5":
                console.log("Total patients:", queue.size());
                showMenu();
                break;

            case "6":
                console.log("Program terminated.");
                rl.close();
                break;

            default:
                console.log("Invalid choice.");
                showMenu();
        }
    });
}

// Add a patient
function addPatient() {
    rl.question("Enter patient name: ", function(name) {
        rl.question(
            "Enter priority (1=Minor, 2=Serious, 3=Critical): ",
            function(input) {
                let priority = Number(input);

                if (
                    !Number.isInteger(priority) ||
                    priority < 1 ||
                    priority > 3
                ) {
                    console.log("Invalid priority! Enter 1, 2, or 3.");
                    showMenu();
                    return;
                }

                // TODO 8: Add the patient to the queue
                ______________________________;

                console.log("Patient added successfully!");
                showMenu();
            }
        );
    });
}

// Serve the patient with the highest priority
function servePatient() {
    // TODO 9: Remove a patient from the queue
    let patient = ______________________________;

    if (patient === null) {
        console.log("No patients to serve.");
    } else {
        console.log("Now serving:", patient.name);
        console.log("Priority:", patient.priority);
    }

    showMenu();
}

// View the next patient
function viewNextPatient() {
    // TODO 10: Get the next patient without removing them
    let patient = ______________________________;

    if (patient === null) {
        console.log("No patients in the queue.");
    } else {
        console.log("Next patient:", patient.name);
        console.log("Priority:", patient.priority);
    }

    showMenu();
}

// Start the program
showMenu();
```

### Test Your Completed Program

Add these patients in this exact order:

  Patient     Priority
  --------- ----------
  Mark               1
  Ana                3
  John               2
  Peter              3
  Sarah              1

The expected queue order is:

``` text
Ana - Priority 3
Peter - Priority 3
John - Priority 2
Mark - Priority 1
Sarah - Priority 1
```

The expected serving order is:

``` text
Ana
Peter
John
Mark
Sarah
```

### Important Coding Hint

For a **Max Priority Queue**, the `findIndex()` condition must check
whether the new patient's priority is greater than the existing
patient's priority:

``` javascript
current => priority > current.priority
```

Use `>` instead of `>=` so patients with equal priority remain in their
original arrival order (FIFO).

**Do not remove the TODO comments until you have completed and tested
each section.**
