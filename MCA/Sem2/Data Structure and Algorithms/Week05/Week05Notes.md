# Binary Search Tree
- Also **Ordered Binary Tree**
- A Binary Search Tree (BST) is a tree in **which all the nodes follow the below-mentioned properties**:
	- The **left sub-tree of a node** has a **~={green}key less than or equal=~** to its parent node's key.
	- The **right sub-tree of a node** has a **~={green}key greater than or equal=~** to its parent node's key.
	
- BST is used in search applications, where data is updated frequently

- **With the help of BST how does it help in fast search ?**
	- lets say u want to search node 25 from the entire tree.
		- we know that **Left of the node has lower value** and **Right of the node has higher value.**
	```text
	                         10
	                       /    \
	                      6      20
	                    /  \    /   \
	                   3    8  12   25
	```
	- in this case we know that we only have to look at right side since all nodes in left the smaller that 25. 
	- so when compare 25 to 10 we get 20 and then we compare 25 to 20 and we get 12 and 25 now we don't compare 12 since it is smaller than 25 so then we compare 25 to 25 and we got that number we where looking for. 
	- So time complexity of search is **O(logn)**

	- For binary tree is **0(n)**

## Binary Search Tree Operations
- Visit each node of the tree and perform operations, say print the content.

```text
                      10
                    /    \
                   6      20
                 /  \    /   \
                3    8  12   25
```

- ~={yellow}**Pre-order Traversal**=~ (Root, Left, Right)

	1. Visit **10** (root).
	2. Go left that **is 6.**
		1. Visit **6.**
		2. Go left to 3:
			1. Visit **3**
			2. No left and no right --> done
		3. Go right to 8:
			1. Visit **8.**
			2. No left and no right --> done
	3. Go right to 20:
		1. Visit **20**
		2. Got left 12:
			1. Visit **12.**
			2. No left and right --> done
		3. Got right to 25:
			1. Visit **25.**

- ~={yellow}**Post-order Traversal**=~ (Left, Right, Root)

	1. **Start at 10**
	2.  Go left to 6:
		1. Go left to 3:
			1. No left and right --> **Visit 3**
		2. Go right to 8:
			1. No left and right --> **Visit 8**
		3. **Visit 6**

	3. Go right to 20:
		1. Go left to 12:
			1. No left and right --> **Visit 12**
		2. Go right to 25:
			1. No left and right --> **Visit 25**
		3. **Visit 20**

	 4. **Visit 10**

```
3, 8, 6, 12, 25, 20, 10
```

	> Root always printed **last**. Children before parents.


- ~={yellow} **In-order Traversal**=~ (Left, Root, Right)

	1. **Start at 10**
	2. Go left 6:
		1. **Visit 6.**
		2. Go left 3:
			1. **Visit 3.**
		3. **Visit 6.**
		4. Go right 8:
			1. **Visit 8.**
		5. **Visit 10.**

	3. Go right 20:
		1. Go left 12:
			1. **Visit 12**
		2. **Visit 20.**
		3. Go right 25:
			1. **Visit 25.**

- ~={yellow} **level-order Traversal**=~ (All)
	- Visit order vise.

## Binary Search Tree 0 -- Node

```
----------------
    Data
left | Right
----------------
getData()
setData()
TreeNode getLeft()
setLeft(TreeNode)
TreeNode getRight()
setRight(TreeNode)
----------------
```

## Syntax for BST -- Insertion

```java
TreeNode insertNode(TreeNode n, int d){          ## TreeNode n is the root value
	if (n == null) {return new TreeNode(d);}
	else{
		if (d < n.getData()) {
			TreeNode newn = insertNode(n.getLeft().d);
			n.setLeft(newn);
		} else {
			TreeNode newn = insertNode(n.getRight().d);
			n.setRight(newn)
		}
	}
	return n;
}
```

### Example -- How to insert following keys in BST -- 10 , 20 ,30 , 12, 5, 7

```

		            10
		          /   \             
		         5     20           
		          \    /  \        
		           7  12    30 
```

## Syntax for BST -- Search

 - ~={purple} **BST search property used:**=~
	- ~={blue} **If key < current node --> go left**=~
	- ~={blue}**If key > current node --> go right**=~
	- ~={blue}**If key == current node --> found**=~

```java
public boolean search(int key){
	TreeNode temp = root;
		while(temp!=null){
			if (temp.getData() == key) {return true;}
			else if (key < temp.getData()) {
				temp = temp.getLeft();
			} else {
				temp = temp.getRight();
			}
		}
return false;
}
```

### BST Search Questions

1. How many comparisons are required for searching key **28** from this tree?
	1. How many comparisons for searching a key from a complete binary search tree with 'n' nodes ?
```
        20
       /  \
      10   25
     / \   / \
    8  15 22 28
```

- ### Total Comparisons = **3**

For a **complete binary search tree** (which is perfectly balanced or close to it), the height of the tree is:

$$ h=[\log_2 n] $$

- Maximum number of comparisons = Height of tree + 1

$$ Max Comparisons = [\log_2 n] + 1 $$

## Syntax for BST -- Deletion

|Case|Situation|Solution|
|---|---|---|
|**Case 1**|Node is a **leaf** (no children)|Simply remove it|
|**Case 2**|Node has **one child**|Replace node with its child|
|**Case 3**|Node has **two children**|Replace with **inorder successor** (or predecessor), then delete that successor|

#### Case 1 -- Delete Leaf Node

```java
TreeNode deleteNode(TreeNode n, int d) {
	if (n == null) return null;
	
	if (d < n.getData()) {
		n.setLeft(deleteNode(n.getLeft(), d));
	} else if (d > n.getData()) {
		n.setRight(deleteNode(n.getRight(), d));
	} else {
		if (n.getleft() == null && n.getRight() == null) {
			return null
		}
	}
}

// EXAMPLE

        20
       /  \
      10   25
     / \   / \
    8  15 22 28
    
// **Delete 8** (leaf):

        20
       /  \
      10   25
       \   / \
       15 22 28
```

#### Case 2 -- Delete Node with 1 child

```java
TreeNode deleteNode(TreeNode n, int d) {
    if (n == null) return null;

    if (d < n.getData()) {
        n.setLeft(deleteNode(n.getLeft(), d));
    } else if (d > n.getData()) {
        n.setRight(deleteNode(n.getRight(), d));
    } else {
        // Node found → one child
        if (n.getLeft() == null) return n.getRight();
        if (n.getRight() == null) return n.getLeft();
    }
    return n;
}

// EXAMPLE

        20
       /  \
      10   25
       \   / \
       15 22 28
       
 // **Delete 10** (one right child = 15):      
       
         20
       /  \
      15   25
          / \
         22 28             
```

#### Case 3: Delete Node with Two Children

```java
TreeNode deleteNode(TreeNode n, int d) {
    if (n == null) return null;

    if (d < n.getData()) {
        n.setLeft(deleteNode(n.getLeft(), d));
    } else if (d > n.getData()) {
        n.setRight(deleteNode(n.getRight(), d));
    } else {
        // Node found → two children
        TreeNode successor = findMin(n.getRight());
        n.setData(successor.getData());
        n.setRight(deleteNode(n.getRight(), successor.getData()));
    }
    return n;
}

TreeNode findMin(TreeNode n) {
    while (n.getLeft() != null) n = n.getLeft();
    return n;

// EXAMPLE
        20
       /  \
      10   25
     / \   / \
    8  15 22 28    
    
// **Delete 20** (two children: 10 and 25):

1. Find the inorder successor of 20
    - Go to **right subtree** (25)
	- Then go **left as far as possible** → 22
	- So **22 is the inorder successor**
	  
2. Step 2: Replace 20 with 22
        22
       /  \
      10   25
     / \     \
    8  15    28	  
    
}
```

## AVL Tree

### What is AVL tree 
- **it is a self balancing binary** search tree where the balance factor of every node is **-1, 0, +1.**
	- Named after Adelson-Velsky and Landis (1962.)

- So with that balancing effect it guarantees a `O(log n)` time for search, insert, delete.

$$BF(node)= \text{Height of left subtree} - \text{Height of Right subtree}$$
#### Find AVL tree 
```
        20
       /  \
      15   30
     /       \
    5        35
```

- Find bf for all levels
	- Node 20:  2 - 2 = 0
	- Node  15:   1 - 0 = +1
	- Node   30:  0 - 1 = -1
	- Node  5:     0 - 0 = 0
	- Node 35:    0 - 0 = 0

```
        20
       /  \
      15   30
     /  \    \
    5   18   35
```

- Find bf for all levels:
	- Node 20: 0
	- Node 15:  0
	- Node 30: -1
	- Node 5: 0
	- Node 18: 0
	- Node 35: 0 

```
        20
       /  \
      15   30
       \     \
        18   35
          \
           19
```

- Find bf for all levels
	- Node 20: 0
	- Node 15:  -2
	- Node 30: -1
	- Node 18:  0
	- Node 35: 0
	- Node 19: 0

### 4 insertion cases for AVL trees. (MAIN IDEA IS BALANCING)
#### Case 1  Left to left --> Right Rotation.
- **Insert:** `30, 20, 10`
- 1. Insert 30
```
    30
```
- Insert 20
```
    30
   /
  20
```
- Insert 10
```
      30      ← BF = +2 (unbalanced)
     /
    20      ← BF = +1
   /
  10
```
- Rotation: Right rotation at 30.
```
      20
     /  \
    10   30
```
#### Case 2  Right to Right --> Left Rotation.
- **Insert:** `10, 20, 30`
- 1. Insert 20
```
    10
```
- Insert 20
```
    10
     \ 
      20
```
- Insert 30
```
    10        ← BF = -2 (unbalanced)
      \
       20     ← BF = -1
         \
          30
```
- Rotation: Right rotation at 30.
```
      20
     /  \
    10   30
```
#### Case 3  Left to Right --> Left Rotate then Right Rotate.
- **Insert:** `30, 20, 10`
- 1. Insert 30
```
    30
```
- Insert 20
```
    30
   /
  20
```
- Insert 10
```
      30      ← BF = +2 (unbalanced)
     /
    10      ← BF = -1
      \
       20
```
- Rotation: **1. Left Rotate at 10.**
```
      30
     /
    20
   /
  10
```
- Rotation: **2. Right Rotate at 30.**
```
      20
     /  \
    10   30
```