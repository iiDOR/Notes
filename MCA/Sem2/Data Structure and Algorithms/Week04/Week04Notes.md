# Circular Linked List (CLI)
## What is CLI
- A **Circular Linked List** is like a regular Linked List, BUT the **last node points back to the first node** instead of pointing to `null`. 
- This creates a **circle/loop**!
```text
CIRCULAR LINKED LIST: 
HEAD → [10|→] → [20|→] → [30|→] 
       ↑                        |
       |________________________| 
       (Last node points back to first)
```

### Insert Operation
```java
void insert_to_list(int item, int pos) {
	//validation posi
	if(pos < 0 || pos > size) {
		system.out.println("Inv position");
		return;
	}
	
	//create a new node
	Node newNode = new Node(item);  
	
	//insert to empty list
	if(head == null) {
		newNode.next = newNode;
		head = newNode;
		size++
		return;
	}
	
	//insert at begining (pos == 0)
	if(pos == 0) {
		Node last = head;
		while (last.next != head) {
			last = last.next
		}
		
		newNode.next = head;
		last.next = newNode;
		head = newNode;
		size++
		return;
	}
	
	Node temp = head;
	for (int i = 0; i<pos -1; i++) {
		
	}
	
}
```

# Doubly Linked List
## What is a Doubly Linked List (DLL)?

A **Doubly Linked List** is like a regular Linked List, BUT each node has **TWO pointers** instead of one:

1. **Next pointer** → Points to the next node (like regular LL)
2. **Previous pointer** → Points to the previous node (NEW!)

This allows you to traverse in **BOTH directions** - forward AND backward! 🔄

## Doubly Linked List: Operations 
Insertion: 
- Insert at the beginning of the list. 
- Insert at the end of the list. 
- Insert item into a particular position of list. 
Deletion: 
- Deleting the first node. 
- Deleting the last node. 
- Deleting an intermediate node. 
Traverse() 
- Forward traversal. 
- Backward traversal.

# Trees
## Tree
- Tree is a non linear Data structure.
- Set of nodes - One node is distinguished as root and other nodes are partitioned into disjoint set called as sub trees of root.
```text
        ROOT           (Level 0)
		   A
          /  \
         /    \
       B        C      (Level 1)
      / \        \
     D   E        F    (Level 2)
```

**Components:**
- **Root** = Top node (B's parent, shown at top which is A)
- **Parent** = Node with children
- **Child** = Node connected below parent
- **Leaf** = Node with no children (D, E, F)
- **Edge** = Connection between nodes
- **Level** = Distance from root
- **Height** = Number of levels
- **Depth** = Distance of node from root

### Skewed Tree
- Every node has only one child, expect the leaf code.
	- Right Skewed Tree
	- Left Skewed Tree

## Tree - Application
- File system in OS is represent in the form of Tree.
- Indexing in Databases for better searching in the database. B-Tree B+ - Tree
- Syntax Tree -- in compliers
- Document Object model (DOM) in html.
## Binary Tree
- A **Binary Tree** is a tree where each node has **at most 2 children** - a **left child** and a **right child**.
```text
         1          (Root)
        / \
       2   3        (Level 1)
      / \   \
     4   5   6      (Level 2)
    /
   7                (Level 3)

Nodes: 1, 2, 3, 4, 5, 6, 7
Edges: 1-2, 1-3, 2-4, 2-5, 3-6, 4-7
Left child of 1: 2
Right child of 1: 3
Leaf nodes: 5, 6, 7
Height: 3 (levels 0, 1, 2, 3)
```
- Each Node in the tree has exactly two children and all the leaves at the same level

## Types of Binary Tree
### Binary Tree –Full Binary Tree
- Each node in the tree has exactly two children and all the leaves at the same level. 
### Binary Tree –Complete Binary Tree
- All the levels are completely filled except possibly the lowest one which is filled from the left.
## Binary Tree Properties
1. Num of nodes at level h is 2^h  so level - 0 is 2^0 nodes.
2. Total Nodes in Full Binary Tree = 2^(h+1) - 1.