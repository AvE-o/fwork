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



#2.0[FEB 19]

####################################
1.数组(Array)
- 相同元素(Element)
- 连续内存
- 元素索引(index)访问对用储存地址
特点: 提供随机访问 容量有限
访问O(1) 插入O(n) 删除O(n)

2.链表(LinkedList)
- 不是连续的内存空间来存储数据
- 链表结构可以克服数组需要预先知道数据大小的缺点
- 相比于数组会占用更多的空间 
- 不能随机读取
单链表: 访问O(n) 删除插入O(1)[知道插入元素位置的情况下]

链表 vs 数组
如果需要支持随机访问的话，链表没办法做到。
如果需要存储的数据元素的个数不确定，并且需要经常添加和删除数据的话，使用链表比较合适。
如果需要存储的数据元素的个数确定，并且不需要经常添加和删除数据的话，使用数组比较合适。
    -数组的大小固定，而链表则天然支持动态扩容。如果声明的数组过小，需要另外申请一个更大的内存空间存放数组元素，
    然后将原数组拷贝进去，这个操作是比较耗时的！
数组使用的是连续内存空间对 CPU 的缓存机制友好，链表则相反。

3.栈(Stack)
- 后进先出（LIFO, Last In First Out）
- 在栈中，push 和 pop 的操作都发生在栈顶
访问O(n) 插入删除O(1)[顶端]
应用: 
当我们我们要处理的数据只涉及在一端插入和删除数据，并且满足 后进先出（LIFO, Last In First Out）
实现浏览器的回退和前进功能
反转字符串

4.队列(Queue)
- 先进先出 (FIFO，First In, First Out)
访问O(n) 插入删除O(1)
应用:
阻塞队列： 阻塞队列可以看成在队列基础上加了阻塞操作的队列。当队列为空的时候，出队操作阻塞，当队列满的时候，入队操作阻塞。
使用阻塞队列我们可以很容易实现“生产者 - 消费者“模型。
一切队列....
####################################
图
G(V,E)，其中，G 表示一个图，V[vertex] 表示顶点的集合，E 表示边的集合
图的储存
- 邻接矩阵存储[优点: 直接 缺点: 占用空间]
    邻接矩阵将图用二维矩阵存储，是一种较为直观的表示方式
    如果第 i 个顶点和第 j 个顶点之间有关系，且关系权值为 n，则 A[i][j]=n 
    在无向图中，我们只关心关系的有无
    所以当顶点 i 和顶点 j 有关系时，A[i][j]=1，当顶点 i 和顶点 j 没有关系时，A[i][j]=0
- 邻接表存储
    邻接链表使用一个链表来存储某个顶点的所有后继相邻顶点。对于图中每个顶点 Vi，
    把所有邻接于 Vi 的顶点 Vj 链成一个单链表，这个单链表称为顶点 Vi 的 邻接表

图的搜索
广度优先搜索(BFS)
    广度优先搜索的具体实现方式用到了之前所学过的线性数据结构——队列
深度优先搜索(DFS)
    深度优先搜索的具体实现用到了另一种线性数据结构——栈
    深度优先搜索就是“一条路走到黑”，从源顶点开始，一直走到没有后继节点，才回溯到上一顶点，
    然后继续“一条路走到黑”
####################################
堆(Heap)
堆是一种满足以下条件的树 
    堆中的每一个节点值都大于等于（或小于等于）子树中所有节点的值
    或者说，任意一个节点的值都大于等于（或小于等于）所有子节点的值
堆的用途
    当我们只关心所有数据中的最大值或者最小值，存在多次获取最大值或者最小值，多次插入或删除数据时，就可以使用堆
    相对于有序数组而言，堆的主要优势在于插入和删除数据效率较高 插入删除O(log(n))
    Heap 初始化的时间复杂度为 O(n)
堆的分类
    最大堆：堆中的每一个节点的值都大于等于子树中所有节点的值
    最小堆：堆中的每一个节点的值都小于等于子树中所有节点的值
堆的储存
    利用数组存储二叉树即节省空间，又方便索引
堆的操作
    插入元素
        将要插入的元素放到最后
        从底向上，如果父结点比该元素小，则该节点和父结点交换，直到无法交换
    删除堆顶元素
        删除堆顶元素后，为了保持堆的性质，需要对堆的结构进行调整，我们将这个过程称之为"堆化"
        自底向上的堆化[会有空出的一个气泡]
            首先删除堆顶元素，使得数组中下标为 1 的位置空出
            比较根结点的左子节点和右子节点，也就是下标为 2,3 的数组元素，将较大的元素填充到根结点(下标为 1)的位置
            一直循环比较空出位置的左右子节点，并将较大者移至空位，直到堆的最底部
        自顶向下堆化   
            我们将最后一个元素移动到堆顶
            然后开始将这个石头沉入海底，不停与左右子节点的值进行比较，和较大的子节点交换位置，直到无法交换位置
    堆的操作总结
        插入元素：先将元素放至数组末尾，再自底向上堆化，将末尾元素上浮
        删除堆顶元素：删除堆顶元素，将末尾元素放至堆顶，再自顶向下堆化，将堆顶元素下沉。
            也可以自底向上堆化，只是会产生“气泡”，浪费存储空间。最好采用自顶向下堆化的方式。
堆排序
    建堆
        建堆的过程就是一个对所有非叶节点的自顶向下堆化过程
        首先要了解哪些是非叶节点，最后一个节点的父结点及它之前的元素，都是非叶节点。也就是说，
        如果节点个数为 n，那么我们需要对 n/2 到 1 的节点进行自顶向下（沉底）堆化
        叶节点 顺序是从后往前堆化
    排序 
        由于堆顶元素是所有元素中最大的，所以我们重复取出堆顶元素，将这个最大的堆顶元素放至数组末尾，并对剩下的元素进行堆化即可(?)
        我们需要执行自顶向下（沉底）堆化，这个堆化一开始要将末尾元素移动至堆顶，这个时候末尾的位置就空出来了，由于堆中元素已经减小，这个位置不会再被使用，所以我们可以将取出的元素放在末尾
        机智的小伙伴已经发现了，这其实是做了一次交换操作，将堆顶和末尾元素调换位置，
        从而将取出堆顶元素和堆化的第一步(将末尾元素放至根结点位置)进行合并
####################################
     
树(Tree)
    红黑树(Red Black Tree)
    由于其自平衡的特性，保证了最坏情形下在 O(logn) 时间复杂度内完成查找、增加、删除等操作，性能表现稳定
    TreeMap,TreeSet,HashMap底层
    如果节点是按照升序或降序的方式插入的，那么二叉查找树就会退化成一个线性结构，也就是一个链表。这样的情况下，
    二叉查找树的性能就会大大降低，时间复杂度就会从 O(logn) 变为 O(n)
    public class Node {
        public Class<?> clazz;
        public Integer value;
        public Node parent;
        public Node left;
        public Node right;
        //AVL
        public int height;
        //
        public Color color = Color.RED;
    }