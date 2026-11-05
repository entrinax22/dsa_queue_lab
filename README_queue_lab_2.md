# Hands-On Laboratory Activity 2: Customer Service Queue Management System

**Course:** Data Structures and Algorithms  
**Topic:** Queue (FIFO – First In, First Out)  
**Programming Language:** JavaScript  
**Total:** 50 Points

## Learning Objectives

After completing this laboratory, students should be able to:
1. Implement a Queue using a JavaScript class and an array.
2. Explain and demonstrate FIFO behavior.
3. Use Queue methods to manage customers waiting for service.
4. Test Queue operations, including empty-queue conditions.

## Scenario

A customer service center assists customers in the order they arrive. The first customer to join the waiting line must be served first. Create a simple console-based **Customer Service Queue Management System** using JavaScript.

This is a **new activity**, separate from the previous student enrollment and school cashier queue examples.

## General Instructions

1. Create a file named `customer_queue.js`.
2. Write your own `Queue` class. Use an array named `items` to store customers.
3. Implement the methods described below. You may use `push()` and `shift()` to demonstrate FIFO.
4. Write the main program to perform the required operations in the exact order given.
5. Use `console.log()` to display results. A browser interface, database, and external libraries are not required.
6. Handle an empty queue safely: do not crash when there are no customers.
7. Do not submit a copy of the instructor's earlier queue demonstration without implementing the requirements of this activity.

## Part A – Queue Class (25 Points)

Create a class named `Queue` with these methods:

| Requirement | Description | Points |
|---|---|---:|
| `constructor()` | Initialize an empty `items` array | 5 |
| `enqueue(name)` | Add a customer to the rear of the queue | 5 |
| `dequeue()` | Remove and return the front customer; return `null` when empty | 5 |
| `front()` | Return the next customer without removing them; return `null` when empty | 5 |
| `isEmpty()` and `size()` | Check if the queue is empty and return the number of customers | 5 |
| **Subtotal** | | **25** |

## Part B – Customer Service Simulation (15 Points)

Write a main program that performs the following steps **in order**:

1. Create a Queue object named `customers`.
2. Add these customers: **Maria**, **Jose**, **Liza**, and **Paolo**, in that order.
3. Display the customer at the front of the queue.
4. Serve two customers using `dequeue()` and display each served customer's name.
5. Add a new customer named **Nina**.
6. Display the next customer, the remaining queue in FIFO order, and the queue size.

**Expected Output:**

```text
Next Customer: Maria
Served: Maria
Served: Jose
Next Customer: Liza
Waiting Customers: Liza, Paolo, Nina
Total Waiting: 3
```

**Part B scoring:** correct initial enqueue order (3), front display (2), serving two customers (4), adding Nina (2), final queue and count (4) = **15 points**.

## Part C – Empty Queue Test (10 Points)

After Part B, continue using the **same** `customers` Queue object:

1. Serve all remaining customers until the queue is empty.
2. Display whether the queue is empty.
3. Attempt to serve one more customer and display a clear message if no customer is waiting.
4. Display the final queue size.

**Expected Output for Part C:**

```text
Queue Empty: true
No customers waiting.
Total Waiting: 0
```

**Part C scoring:** removes all remaining customers (4), correct empty check (2), safe extra dequeue with message (2), correct final size (2) = **10 points**.

## Grading Summary

| Component | Points |
|---|---:|
| Part A – Queue Class | 25 |
| Part B – Customer Service Simulation | 15 |
| Part C – Empty Queue Test | 10 |
| **TOTAL** | **50** |

## Submission Requirements

Submit the following through the learning management system:

1. JavaScript source file: `customer_queue.js`.
2. Screenshot(s) showing the complete console output for Parts B and C.
3. Link to a GitHub repository containing your source code and this README or your own short project description.

**Reminder:** Your program must demonstrate **FIFO**: the customer who enters first must be served first. The required output is an example of correct behavior; do not print it as hard-coded text without implementing the Queue operations.
