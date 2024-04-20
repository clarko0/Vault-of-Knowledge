### Overview
A linked list is a linear collection of data elements whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which together represent a sequence.

### Singly linked list
Singly linked lists contain nodes which have a 'value' field as well as 'next' field, which points to the next node in line of nodes. Operations that can be performed on singly linked lists include insertion, deletion and traversal.

In c++ the struct would look something like:
```cpp
struct Node {
	int value;
	Node* next;
}
```

### Doubly linked list
In a 'doubly linked list', each node contains, besides the next-node link, a second link field pointing to the 'previous' node in the sequence. The two links may be called 'forward('s') and 'backwards', or 'next' and 'prev'('previous').

In c++ the struct would look like:
```cpp
struct Node {
	int value;
	Node* next;
	Node* prev;
}
```

### Circular linked list
In the last node of a linked list, the link field often contains a null reference, a special value is used to indicate the lack of further nodes. A less common convention is to make it point to the first node of the list; in that case, the list is said to be 'circular' or 'circularly linked'; otherwise, it is said to be 'open' or 'linear'. It is a list where the last node pointer points to the first node (i.e., the "next link" pointer of the last node has the memory address of the first node).