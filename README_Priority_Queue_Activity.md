# Laboratory Activity: Customer Service Priority Queue System

**Subject:** Data Structures and Algorithms (JavaScript)  
**Module:** 5 — Priority Queue  
**Total:** 50 points  
**Environment:** Node.js (terminal)

## Objective
Create a menu-driven customer service program that uses a **Priority Queue** and accepts keyboard input using Node.js **`readline`**. Use **`findIndex()`** to insert each customer in the correct priority order.

## Scenario
A customer service office handles three kinds of requests:

| Priority | Request type |
|---|---|
| 1 | Urgent |
| 2 | Normal |
| 3 | Low |

**Priority 1 is served first.** Customers with the same priority must be served in the order they arrived (FIFO).

## Requirements
1. Create a `PriorityQueue` class with an `items` array.
2. Implement `enqueue(name, priority)` using `findIndex()` to locate the correct insertion position. Use `push()` when no position is found and `splice()` otherwise.
3. Implement `dequeue()` to remove and return the next customer. Handle an empty queue.
4. Implement `front()` and `display()` to show the next customer and the current queue. Handle an empty queue.
5. Use `readline` to show a repeating menu and accept user input:
   - **1** — Add customer (ask for name and priority 1–3)
   - **2** — Serve next customer
   - **3** — View queue
   - **4** — View next customer
   - **5** — Exit
6. Reject blank customer names and invalid priorities. Display an appropriate message when the queue is empty.

## Starter Code
Complete the sections marked `TODO`. Do not replace `findIndex()` with `sort()`.

```javascript
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

class PriorityQueue {
    constructor() {
        this.items = [];
    }

    enqueue(name, priority) {
        // TODO: Create an object containing name and priority.
        // TODO: Use findIndex() to find the insertion position.
        // TODO: Use push() or splice() to insert the object.
    }

    dequeue() {
        // TODO: Return null if empty; otherwise remove the first item.
    }

    front() {
        // TODO: Return null if empty; otherwise return the first item.
    }

    display() {
        // TODO: Print the queue in priority order.
    }
}

const queue = new PriorityQueue();

function showMenu() {
    console.log("\n=== CUSTOMER SERVICE PRIORITY QUEUE ===");
    console.log("1. Add customer");
    console.log("2. Serve next customer");
    console.log("3. View queue");
    console.log("4. View next customer");
    console.log("5. Exit");

    rl.question("Choose an option: ", (choice) => {
        switch (choice.trim()) {
            case "1":
                rl.question("Customer name: ", (name) => {
                    rl.question("Priority (1=Urgent, 2=Normal, 3=Low): ", (input) => {
                        const priority = Number(input);
                        // TODO: Validate name and input (must be exactly 1, 2, or 3).
                        // TODO: Enqueue valid customers and print confirmation.
                        showMenu();
                    });
                });
                break;
            case "2":
                // TODO: Serve the next customer or print an empty-queue message.
                showMenu();
                break;
            case "3":
                queue.display();
                showMenu();
                break;
            case "4":
                // TODO: Display the next customer or an empty-queue message.
                showMenu();
                break;
            case "5":
                console.log("Goodbye!");
                rl.close();
                break;
            default:
                console.log("Invalid menu option.");
                showMenu();
        }
    });
}

showMenu();
```

### Hint: `findIndex()`

```javascript
let index = this.items.findIndex(
    current => priority < current.priority
);
```

This finds the first existing customer whose priority number is **greater** than the new customer's number. Use `<`, not `<=`, to preserve arrival order for equal priorities.

## Sample Run

```text
=== CUSTOMER SERVICE PRIORITY QUEUE ===
1. Add customer
2. Serve next customer
3. View queue
4. View next customer
5. Exit
Choose an option: 1
Customer name: Ana
Priority (1=Urgent, 2=Normal, 3=Low): 3
Customer added: Ana (Priority 3)

Choose an option: 1
Customer name: Ben
Priority (1=Urgent, 2=Normal, 3=Low): 1
Customer added: Ben (Priority 1)

Choose an option: 1
Customer name: Carl
Priority (1=Urgent, 2=Normal, 3=Low): 2
Customer added: Carl (Priority 2)

Choose an option: 3
Current queue:
1. Ben - Priority 1
2. Carl - Priority 2
3. Ana - Priority 3

Choose an option: 2
Serving: Ben (Priority 1)

Choose an option: 4
Next customer: Carl (Priority 2)

Choose an option: 5
Goodbye!
```

*The menu should reappear after each operation; it is shortened in the sample run.*

## Test Cases

1. Add **Ana (3)**, **Ben (1)**, **Carl (2)**. Expected order: **Ben → Carl → Ana**.
2. Add **David (2)** after Carl. Expected order: **Ben → Carl → David → Ana** (same priority uses FIFO).
3. Serve one customer. Expected: **Ben** is removed first.
4. Try adding a blank name or priority `4`. Expected: **input rejected**.
5. Serve customers until empty, then serve once more. Expected: **empty-queue message**, no crash.

## Submission
Submit:
- `priority_queue.js` — your completed JavaScript program.
- `README.md` — brief instructions on how to run your program and your name/section.
- A screenshot showing your program running in the terminal.
- Your GitHub repository link (if required by your instructor).

**Run command:** `node priority_queue.js`

## Grading Rubric (50 Points)

| Criteria | Points |
|---|---:|
| Priority Queue class and `enqueue()` with `findIndex()` | 15 |
| `dequeue()`, `front()`, and `display()` | 10 |
| Working `readline` menu and user input | 10 |
| Priority validation, empty-queue handling, and FIFO ties | 10 |
| Code readability and successful demonstration | 5 |
| **Total** | **50** |

**Reminder:** Submit your own work and be ready to explain how `findIndex()` and `splice()` determine the queue order.
