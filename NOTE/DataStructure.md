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