# Binary Search Tree
- Ordered Binary Tree
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

- **Pre-order Traversal** (Root, Left, Right)
	- Visit the root
	- Visit Left sub Tree in pre order
	- Visit Right sub Tree in pre order**
- **Post-order Traversal** (Left, Right, Root)
	- Visit Left sub Tree in post order
	- Visit Right sub Tree in post order
	- Visit Root
- **In-order Traversal** (Left, Root, Right)
	- Visit Left sub Tree in order
	- Visit the Root.
	- Visit Right sub Tree in order
- **level-order Traversal** (All)
	- Visit order vise.