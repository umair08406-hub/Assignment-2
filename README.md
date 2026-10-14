# Assignment-2

1. What is a data structure? Differentiate
between linear and non-linear data structures.

Data Structure: A way of organizing and storing data so that it can be used efficiently.
Linear Non-linear
Data is arranged sequentially. Data is arranged hierarchically or as a network.
Example: Array, Stack, Queue. Example: Tree, Graph.

3. What is an array? Write two advantages
and two disadvantages.

Array: An array is a collection of elements of the same data type stored in contiguous memory locations.
Advantages:
Fast access to elements.
Easy to traverse.
Disadvantages:
Usually has a fixed size.
Insertion and deletion can be costly.

3.Why is random access in an array O(1)?
Array random access is O(1) because an element can be accessed directly using its index without traversing other elements.
4. What are row-major and column-major order?
Row-major: Array elements are stored row by row in memory.
Column-major: Array elements are stored column by column in memory.
5. What is a stack? Explain the LIFO principle.
Stack: A linear data structure in which insertion and deletion take place at the same end, called the TOP.
LIFO: Last In, First Out — the last element inserted is the first one removed.
Example: A stack of plates.

6. What are stack overflow and stack underflow?

Stack Overflow: When we try to insert an element into a full stack.
Stack Underflow: When we try to remove an element from an empty stack.

7. What is a queue? Explain the FIFO principle.

Queue: A linear data structure in which insertion takes place at the REAR and deletion takes place at the FRONT.
FIFO: First In, First Out — the first element inserted is the first one removed.
Example: People standing in a line.

8. Write the four types of queues.

Linear Queue
Circular Queue
Priority Queue
Double-Ended Queue (Deque)

9. What is a priority queue?

A priority queue is a queue in which elements are processed according to their priority rather than simply their arrival order.

10. What is a deque?

Deque (Double-Ended Queue): A queue in which insertion and deletion can take place at both the front and rear ends.
Quick revision for exams:
Array → Indexed access
Stack → LIFO
Queue → FIFO
Overflow → Full stack
Underflow → Empty stack
Deque → Both ends
Row-major → Row by row
Column-major → Column by column

11. What is a call stack?

A call stack is a stack that stores information about function calls in a program. It follows the LIFO principle.

12. Write three real-life applications of a stack.

Stack of plates.
Undo/Redo operation.
Browser back button.

13. Write three real-life applications of a queue.

People standing in a ticket line.
Printer job scheduling.
CPU task scheduling.

14. What are time complexity and space
complexity?

Time Complexity: Measures how the running time of an algorithm grows with input size.
Space Complexity: Measures how much memory an algorithm requires.

15. Explain Big-O, Omega and Theta notation.

Big-O : Represents an asymptotic upper bound on an algorithm's growth.
Omega : Represents an asymptotic lower bound.
Theta : Represents a tight asymptotic bound (both upper and lower).
Stop.

             section B.

1.Algorithm to Insert an Element at a
 Given Position

Algorithm: INSERT(A, N, POS, ITEM)            
Start.
Set i = N.
Repeat while i >= POS:
A[i+1] = A[i]
i = i - 1
Set A[POS] = ITEM.
Set N = N + 1.
Stop.
Example:
Original array: [10, 20, 30, 40]
Insert 25 at position 3.
After shifting: [10, 20, 30, 30, 40]
Final array: [10, 20, 25, 30, 40]
Time Complexity:  in the worst case.


 2. Algorithm to Delete an Element at a        Given Position

Algorithm: DELETE(A, N, POS)
Start.
Set i = POS.
Repeat while i < N:
A[i] = A[i+1]
i = i + 1
Set N = N - 1.
Stop.
Example:
Original array: [10, 20, 30, 40, 50]
Delete the element at position 3.
Final array: [10, 20, 40, 50]
Time Complexity:  in the worst case.     

3. Linear Search and Binary Search

Algorithm: LINEAR_SEARCH(A, N, ITEM)
Start from the first element.
Compare each element with ITEM.
If matched, return its position.
If no match is found, return -1.
Stop.
Time Complexity: 
B. Binary Search
Condition: The array must be sorted.
Algorithm: BINARY_SEARCH(A, N, ITEM)
Set LOW = 0, HIGH = N - 1.
Repeat while LOW <= HIGH:
MID = (LOW + HIGH) / 2 (integer division).
If A[MID] == ITEM, return MID.
If ITEM < A[MID], set HIGH = MID - 1.
Otherwise, set LOW = MID + 1.
Return -1 if not found.
Stop.

Time Complexity: 
Comparison
Linear Search Binary Search
Works on unsorted arrays Requires a sorted array
Checks elements one by one Divides the search range in half
Worst case: Worst case: 

4. Reverse an Array In-Place

Algorithm: REVERSE(A, N)
1.Set START = 0, END = N - 1.
2.Repeat while START < END:
Swap A[START] and A[END].
START = START + 1.
END = END - 1.
Stop.

Example:

Original: [1, 2, 3, 4, 5]
Reversed: [5, 4, 3, 2, 1]
Time Complexity: 
Space Complexity: , because no extra array is used.

5. Rotate an Array by K Positions
Algorithm: Right Rotation
Find K = K % N.
Reverse the entire array.
Reverse the first K elements.
Reverse the remaining N-K elements.

Stop.Example:

Array: [1, 2, 3, 4, 5]
Rotate right by K = 2.
Final array: [4, 5, 1, 2, 3]
Time Complexity: 
Space Complexity: 
Space Complexity: 

6. Address Calculation Formula for a 2D Array

A. Row-Major Order
Elements are stored row by row.
B. Column-Major Order
Elements are stored column by column.
Where:
BA = Base address
w = Size of each element in bytes
N = Number of columns
M = Number of rows
LR = Lower row index
LC = Lower column index
i, j = Required element 

Numerical Example

Given:
Array size = 3×4
Base address = 1000
Element size = 4 bytes
Find the address of A[2][3]
Lower row and column indices = 0

          stack 

7. Implement a Stack Using an Array           Stack: Stack follows LIFO (Last In,        First Out).

#define MAX 5
int stack[MAX], top = -1;

void push(int x) {
    if (top == MAX - 1)
        printf("Stack Overflow");
    else
        stack[++top] = x;
}

void pop() {
    if (top == -1)
        printf("Stack Underflow");
    else
        top--;
}

void peek() {
    if (top == -1)
        printf("Stack Empty");
    else
        printf("%d", stack[top]);
}

int isEmpty() {
    return top == -1;
}

int isFull() {
    return top == MAX - 1;
}


8. Push and Pop Using a Linked List

struct Node {
    int data;
    struct Node *next;
};

struct Node *top = NULL;

void push(int x) {
    struct Node *newNode = malloc(sizeof(struct Node));
    newNode->data = x;
    newNode->next = top;
    top = newNode;
}

void pop() {
    if (top == NULL)
        printf("Stack Underflow");
    else {
        struct Node *temp = top;
        top = top->next;
        free(temp);
    }
}
   
   Pop characters one by one.
The popped characters form the reversed string.
Example: HELLO → OLLEH
Time Complexity: O(n)

10. Next Greater Element Using a Stack

Meaning: Find the first greater element on the right of each array element.
Example:
Array: [4, 5, 2, 10]
Output: [5, 10, 10, -1]
Algorithm:
1.Traverse the array from right to left.
2.Remove stack elements smaller than or equal to the current element.
3.If the stack is empty, answer is -1; otherwise, the top is the answer.
4.Push the current element onto the stack.
Time Complexity: O(n)

11. Min Stack – Implement getMin() in O(1)
Meaning: A Min Stack returns the minimum element in constant time.

Algorithm:

1.Maintain two stacks: stack and minStack.
2.On push(x), push x onto the main stack. Also push it onto minStack if it is less than or equal to the current minimum.
3.On pop(), remove the top element and also remove it from minStack if both top elements are equal.
4.getMin() returns the top of minStack.
Example: Push 5, 3, 7
getMin() → 3
Pop 7
getMin() → 3
Time Complexity: Push O(1), Pop O(1), getMin() O(1).
Exam tip: Remember these three points: Stack = LIFO, Push = Insert, Pop = Delete.


               Queue 

12. Queue Using Array (Enqueue & Dequeue)


 #include <stdio.h>
#define SIZE 5
int q[SIZE], front = -1, rear = -1;

void enqueue(int x) {
    if (rear == SIZE - 1)
        printf("Queue Overflow\n");
    else {
        if (front == -1) front = 0;
        q[++rear] = x;
    }
}

void dequeue() {
    if (front == -1 || front > rear)
        printf("Queue Underflow\n");
    else
        printf("Deleted: %d\n", q[front++]);
}

int main() {
    enqueue(10);
    enqueue(20);
    dequeue();
    return 0;
}


13. Queue Using Linked List


#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

struct Node *front = NULL, *rear = NULL;

void enqueue(int x) {
    struct Node *n = malloc(sizeof(struct Node));
    n->data = x;
    n->next = NULL;

    if (rear == NULL)
        front = rear = n;
    else {
        rear->next = n;
        rear = n;
    }
}

void dequeue() {
    if (front == NULL)
        printf("Queue is Empty\n");
    else {
        struct Node *temp = front;
        printf("Deleted: %d\n", temp->data);
        front = front->next;
        if (front == NULL) rear = NULL;
        free(temp);
    }
}

int main() {
    enqueue(10);
    enqueue(20);
    dequeue();
    return 0;
}


14. Deque Operations (Insert/Delete Both Ends)



#include <stdio.h>
#define SIZE 5

int dq[SIZE], front = -1, rear = -1;

void insertFront(int x) {
    if (front == 0)
        printf("Cannot insert at front\n");
    else {
        if (front == -1)
            front = rear = 0;
        else
            front--;
        dq[front] = x;
    }
}

void insertRear(int x) {
    if (rear == SIZE - 1)
        printf("Deque is Full\n");
    else {
        if (front == -1) front = 0;
        dq[++rear] = x;
    }
}

void deleteFront() {
    if (front == -1)
        printf("Deque is Empty\n");
    else if (front == rear)
        front = rear = -1;
    else
        front++;
}

void deleteRear() {
    if (front == -1)
        printf("Deque is Empty\n");
    else if (front == rear)
        front = rear = -1;
    else
        rear--;
}

int main() {
    insertRear(10);
    insertFront(5);
    deleteFront();
    deleteRear();
    return 0;
}

15. Reverse a Queue Using a Stack


#include <stdio.h>

int main() {
    int q[] = {10, 20, 30, 40};
    int stack[4], top = -1, i;

    for (i = 0; i < 4; i++)
        stack[++top] = q[i];

    for (i = 0; i < 4; i++)
        q[i] = stack[top--];

    for (i = 0; i < 4; i++)
        printf("%d ", q[i]);

    return 0;
}

 16. Generate Binary Numbers from 1 to n       Using a Queue


#include <stdio.h>
#include <string.h>

int main() {
    char q[100][20];
    int front = 0, rear = 0, n, i;

    printf("Enter n: ");
    scanf("%d", &n);

    strcpy(q[rear++], "1");

    for (i = 1; i <= n; i++) {
        char s[20];
        strcpy(s, q[front++]);

        printf("%s ", s);

        strcpy(q[rear], s);
        strcat(q[rear++], "0");

        strcpy(q[rear], s);
        strcat(q[rear++], "1");
    }

    return 0;
}


             SECTION-C
1. Infix to Postfix Conversion Using Stack

Expression: A + B * (C - D) / E
Answer: A B C D - * E / +
Stack table
Symbol Stack Postfix
(  + * ( AB
C + * ( ABC
- + * ( - ABC
D + * ( - ABCD
) + * ABCD-
/ + / ABCD-*
E + / ABCD-*E
End Empty ABCD-*E/+
Spaces are added for readability: A B C D - * E / +
Algorithm
1. Create an empty stack and postfix string.
2. Scan the infix expression from left to right.
3. If the symbol is an operand, add it to postfix.
4. If ( occurs, push it onto the stack.
5. If an operator occurs, pop operators of higher or equal precedence, stopping at (.
6.If ) occurs, pop until ( is found and discard the parentheses.
7. Pop all remaining operators at the end.

2. Postfix Evaluation Using Stack
Expression: 5 3 2 * + 4 -

Rule: When an operator appears, pop t

 Rule: When an operator appears, pop the top two values, perform the operation, and push the result.
Symbol Operation Stack (bottom → top)
5 Push 5 5
3 Push 3 5, 3
2 Push 2 5, 3, 2
* 3 × 2 = 6 5, 6
+ 5 + 6 = 11 11
4 Push 4 11, 4
- 11 − 4 = 7 7
Final answer: 7
Algorithm:
1. Scan the postfix expression from left to right.
2. Push each operand onto the stack.
3.For each operator, pop the second operand b, then the first operand a.
4. Calculate a operator b and push the result.
5. The final stack value is the answer.


            

