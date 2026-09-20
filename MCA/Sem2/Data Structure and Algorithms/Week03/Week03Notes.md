# Linked List
## What is Linked List
A **linear data structure** that stores items in **non-sequential memory locations** (unlike arrays which are sequential). Each item knows where the **next item** is located!
### Node Structure 
```text
┌─────────────┬──────────────┐
│   DATA      │  NEXT (Ptr)  │
└─────────────┴──────────────┘
```
### Main Parts
- Head/Start Pointer
- Node
- Data
- Next Pointer
### Properties of Linked List
1. Accessed using Head / Start.
2. Successive elements connected by pointers
3. Next of last node = NULL
4. Dynamic growth/shrink
5. Sequential access only
6. No random access.
## Linked List -ADT
### Three Core Operations
#### 1. Insert_to_list(item, pos)
**Purpose:** Add an item at a specific position in the list.
**Cases:**
- **pos == 0**: Insert at the **beginning** (new node becomes HEAD)
- **pos == n** (where n = number of nodes): Insert at the **end**
- **0 < pos < n**: Insert **in the middle**
```text
Before
	HEAD ---> 10 | NULL
	
After: (insert 5 at pos=0)
	HEAD ---> 5 | 10 ---> 10 | NULL
```
#### 2. Del_from_list(pos)
**Purpose:** Delete a node at position `pos` and return the deleted value.
**Cases:**
- **pos == 0**: Delete HEAD (update HEAD to next node)
- **pos > 0**: Find node at pos, adjust pointers, delete.
```text
Before
	HEAD ---> 10 | 20 ---> 20 | NULL
	
After: (delete pos=0 then return 5)
	HEAD ---> 10 | NULL
```
#### 1. Traverse()
- Visit each node and do some action say, print the value

#### Linked List Implementation in the simplest way possible
##### Step 1: Understanding the Node Class
- Node is like a Box, it holds data:
	- Data --> **actual value** (10,20,30,etc)
	- Next --> **addr of the next box.**

```java
class Node {
	private int data;
	private Node next;
	
	//Constructor -- create a new empty node
	public Node() {
		data = 0
		next = null;
	}
	
	//Constructor -- create a node with data and next pointer.
	public Node(int d, Node n) {
		data = d;
		next = n
	}
	
	//Setters (change values)
	public void setData(int d)  { data = d; }
	public void setNext(Node p) { next = p; }
	
	//Getters (get values)
	public int  getData()  { return data; }
	public void getNext()  { return next; }
	
	//print this node's data
	public void print() { System.out.println(data); }
}
```

##### Step 2: Understanding the LList Class
```java
class LList {
	private Node head;
	
	//Constructor - emp list starts with null HEAD
	public LList() {
		head = null;
	}
}
```

##### Step 3: INSERT Operation (Simplified)
```java
public void insert_to_list(int item, int pos) {
	if(pos==0) {
		Node temp = new Node(item, null);
		temp.setNext(head);
		head = temp;
	}
}
```

##### Step 3: DELETE Operation (Simplified)
```java
public void del_from_list(int p) {
	
	//check if position is valid
	if(head == null) {
		system.out.println("list empty");
		return -1;
	}
	else if(pos == 0) {
		// Save the value to return 
		int val = head.getData();
		
		// Make HEAD point to next node 
		head = head.getNext();
		
		return val;
	}
}
```

##### Step 3: DELETE Operation (Simplified)
```java
void print() {
	Node temp = head;
	
	while(temp != null) {
		System.out.println(temp.getData());
		temp = temp.getNext();
	}
}
```