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

###Hashing
Hashing is a technique or process of mapping keys, and values into the hash table by using a hash function. 
It is done for faster access to elements.

*Components of Hashing
Key, Hash Function, Hash Table

*Properties of Good hash function
A hash function that maps every item into its own unique slot is known as a perfect hash function.
Increase the size of the Hash Table(it is not practical when the number of possibilities is large.)

1.Efficiently computable.  
2.Should uniformly distribute the keys (Each table position is equally likely for each.
3.Should minimize collisions.
4.Should have a low load factor(number of items in the table divided by the size of the table).


*How to handle Hash Collisions?
Separate Chaining
Open Addressing
 --Linear Probing(next available slot)
 --Quadratic Probing(H + k^2)
 --Double Hashing(Two hash function)
 
Load Factor = Total elements in hash table/ Size of hash table

Rehashing:when the load factor increases to more than its predefined value (the default value of the load factor is 0.75), the complexity increases. So to overcome this, the size of the array is increased (doubled) and all the values are hashed again and stored in the new double-sized array to 
maintain a low load factor and low complexity.

A:
Hash provides better synchronization than other data structures.
Hash tables are more efficient than search trees or other data structures
Hash provides constant time for searching, insertion, and deletion operations on average.

D/A:
Hash is inefficient when there are many collisions.
Hash collisions are practically not avoided for a large set of possible keys.
Hash does not allow null values. 


###Graph Data Structure And Algorithms

*Components of Graph
Vertices: Vertices are the fundamental units of the graph. Sometimes, vertices are also known as vertex or nodes. 
Every node/vertex can be labeled or unlabelled.

Edges: Edges are drawn or used to connect two nodes of the graph. It can be ordered pair of nodes in a directed graph. Edges can connect any two nodes in any possible way. There are no rules. 
Sometimes, edges are also known as arcs. Every edge can be labeled/unlabelled.

*Types of Graph
1.Null Graph - no edge
2.Trivial Graph - one single vertex
3.Undirected Graph
4.Directed Graph
5.Connected Graph
6.Disconnected Graph
11.Directed Acyclic Graph
13.Weighted Graph

*Representation of Graphs
    *Adjacency Matrix
    *Adjacency List
When the graph contains a large number of edges then it is good to store it as a matrix

*Basic Operations on Graphs
Insertion
Deletion
Searching
Traversal

*When to use Graph
When you need to represent and analyze the relationships between different objects or entities. 

A:
Graphs are a versatile data structure that can be used to represent a wide range of relationships and data structures.
They can be used to model and solve a wide range of problems, including pathfinding, data clustering, network analysis, and machine learning.
Graph algorithms are often very efficient and can be used to solve complex problems quickly and effectively.
Graphs can be used to represent complex data structures in a simple and intuitive way, making them easier to understand and analyze.

D/A:
Graphs can be complex and difficult to understand, especially for people who are not familiar with graph theory or related algorithms.
Creating and manipulating graphs can be computationally expensive, especially for very large or complex graphs.
Graph algorithms can be difficult to design and implement correctly, and can be prone to bugs and errors.
Graphs can be difficult to visualize and analyze, especially for very large or complex graphs, which can make it challenging to extract meaningful insights from the data.

<<<<<<< HEAD
###Breadth First Search:
It starts at the root of the graph and visits all nodes at the current depth level before moving on to the nodes at the next depth level.
using queue

###Depth First Search:
using stack
*Applications of DFS
Detecting cycle in a graph[Finding back edge]
Path Finding
Topological Sorting

A:
Memory requirement is only linear with respect to the search graph.

DA:
The disadvantage of Depth-First Search is that there is a possibility that it may down the left-most path forever.
Depth-First Search is not guaranteed to find the solution.
And there is no guarantee to find a minimal solution, if more than one solution.
=======
### Set
Unique Value with operation like "union,intersection,difference"
>>>>>>> 85bd07c0a93f86d9a95ea7bfc63481076fa1976f

Hash-Based Set & Tree-Based Set

<<<<<<< HEAD
###Matrix
A matrix represents a collection of numbers arranged in an order of rows and columns. It is necessary to enclose the elements of a matrix in parentheses or brackets.
2-D:
int arr[number_of_rows][number_of_columns]; 

*Traversing
Row Major Order[row by row]
Column Major Order[column by column]
=======
Set data structures are commonly used in a variety of computer science applications, 
including algorithms, data analysis, and databases. The main advantage of using a set data structure is that it allows you to perform operations on a collection of elements in an efficient and organized way.

*Unordered Set & Ordered Set

Set is different from array and map.

### Map
(also known as a dictionary, associative array, or hash map)
is a collection of key[unique identifier]-value pair
>>>>>>> 85bd07c0a93f86d9a95ea7bfc63481076fa1976f
