#Oct 24

##Data Structure Basic

---linear
    --Static
        -Array
    -Dynamic
        -Queue
        -Stack
        -Linked List
*Static memory has a fixed memory size, easy to access.
*Dynamic size not fix, could be update.

---Non-Linear
    --Tree
    --Graph
*Non-Linear we can not traverse all the elements in a single run only.

###Array

An array is a collection of items stored at contiguous memory locations. 
The idea is to store multiple items of the [same type] together.
* easier to calculate the position of each element (offset)

Applications:
--bubble sort, merge sort, and quicksort
--linear search and binary search.

A:

--Efficient 
    -Accessing an element in an array is an O(1) operation
--Fast data retrieval, Memory efficiency

DA:
--Fixed Size
--Insertion & Deletion

###Linked List
A linked list is a linear data structure, in which the elements are not stored at contiguous memory locations. 
The elements in a linked list are linked using pointers.

Node consists DATA & NEXT POINTER.
Head(First) and Tail(Last)

A:
Dynamic Data structure(SIZE)
Ease of Insertion/Deletion
Efficient Memory Utilization

DA:
Random Access
Extra Memory

Operations on Linked Lists:
Insertion, Deletion, Searching

###Stack
order with Stack -> LIFO, FILO

Basic Stack operation:
Push,Pop,top(return the top element), isEmpty,size

Type of Stack:
Register Stack: This type of stack is also a memory element present in the memory unit and can handle a small amount of data only. 
The height of the register stack is always limited as the size of the register stack is very small compared to the memory.

Memory Stack: This type of stack can handle a large amount of memory data. 
The height of the memory stack is flexible as it occupies a large amount of memory data.

A:
Easy implementation
Efficient memory utilization
Fast access time 
Supports backtracking

DA:
Limited capacity
No random access

###Queue

We define a queue to be a list in which all additions to the list are made at one end, 
and all deletions from the list are made at the other end.

-> FIFO like a real queue.

We can access both ends for Queue.

Basic queue operation:
enqueue,dequeue,peek,rear,isFull,isNull


###Tree
A tree data structure is a hierarchical structure 
that is used to represent and organize data in a way that is easy to navigate and search.

Basic Terminologies:
Parent Node, Child node, Root node, Leaf Node, Ancestor of a Node,
Descendant, Sibling, Level of Node, Neighbour of a Node, SubTree

Basic Operation:
Create, Insert, Search

3-Traversal:
Pre order, In order, Post-order.

Application:
File System, Data Compression, Compiler Design, Database Index

A:
Efficient Searching: Normal O(log n)
Easy Organize & Navigate
Traverse & Manipulate(Recursive nature)

DA:
Unbalanced Tree would cost search using more time.
More memory

##Tree Traversal
1. Depth First Search:
    in-order -> Left, Root, Right    4 5 2 1 6 3 7
    pre-order -> Root, Left, Right   1 2 4 5 3 6 7
    post-order -> Left, Righ, Root   4 5 2 6 7 3 1
    
2. Level Order Treversal(BFS):
   
   
   
###Heap
A Heap is a special Tree-based data structure in which the tree is a complete binary tree.
min-head/max-heap

*Operations:
Heapify: a process of creating a heap from an array.
Insertion: process to insert an element in existing heap time complexity O(log N).
Deletion: deleting the top element of the heap or the highest priority element, and then organizing the heap and returning the element with time complexity O(log N).
Peek: to check or find the first (or can say the top) element of the heap.

Application:
Priority queues
Heapsort Algorithm
Memory management
Graph algorithms

A:
Efficient insertion and deletion
Efficient priority queue
Guaranteed access to the maximum or minimum element
Space efficiency
Heap-sort algorithm

DA:
Lack of flexibility
Not ideal for searching
Not a stable data structure