# Introduction to Graphs
## Graph Data Structure
A **Graph** is a **~={yellow}non-linear data structure=~** consisting of:
- **Vertices (V)** — a finite non-empty set of nodes.
- **Edges (E)** — pairs of vertices that connect them.
## Definitions and Terminologies
- Degree of a Vertex - it is the **number of edges incident to it**. (num of edges)
- Adjacent Vertices - When an edge connects two vertices, they are **adjacent** to each other. 
- In-Degree of Vertex -- no of edges **pointing to the head of vertex.**
- Out - Degree of Vertex -- no of edges **pointing to the tail of vertex.**
- Path - it is a sequence of adjacent vertices
- Simple path - a path in which all the vertices expect the first and last are distinct
- Cycle - A cycle is a **simple path** in which the **first and last vertices** are the same.
## Types of Graphs
### Directed Graph
- A graph where **edges have direction.**
- **each edges goes from one vertex to another vertex.**
- Edge is represented as **u --> v**
- **Direction matters that is U --> V not V --> U.**
### Undirected Graph
- A graph where **edges have no direction.**
- **The connection is Bi directional**.
-  Edge is represented as **u --> v**
- **Direction does not matter that is U --> V not V --> U.**

## Breadth First Search BFS
- Is a **graph traversal algorithm that**
	- **Explores all vertices reachable from a source vertex**.
	- then computes the **~={cyan}short distance from the source vertex to each reachable vertex=~**
	- then it produces the **Breadth-First Tree BFT** with source vertex as root.
	- then visit each vertices level by level.

### BFS Algorithm
```
BFS(Graph G, int source):
1. Create a visited array of size n (all false)
2. Create an empty Queue Q
3. Mark source as visited
4. Insert source into Q
5. While Q is not empty:
     a. Dequeue a vertex v1
     b. Print v1
     c. For each unvisited adjacent vertex v2 of v1:
          - Mark v2 as visited
          - Insert v2 into Q
```
### Example
```
        A
       / \
      B   C
     / \   \
    D   E   F
         \
          G
```
```

Adjacency list:

A → B, C
B → A, D, E
C → A, F
D → B
E → B, G
F → C
G → E
```

```
### Step-by-Step BFS (Source = A)

|Step|Dequeued|Queue After|Visited            |Output             |
|--- |--     -|-        --|--                -|   -             --|
|0   |—       |[A]        |A                  |     —             |
|1   |A       |[B, C]     |A, B, C            |A                  |
|2   |B       |[C, D, E]  |A, B, C, D, E      |A, B               |
|3   |C       |[D, E, F]  |A, B, C, D, E, F   |A, B, C            |
|4   |D       |[E, F]     |A, B, C, D, E, F   |A, B, C, D         |
|5   |E       |[F, G]     |A, B, C, D, E, F, G|A, B, C, D, E      |
|6   |F       |[G]        |A, B, C, D, E, F, G|A, B, C, D, E, F   |
|7   |G       |[]         |A, B, C, D, E, F, G|A, B, C, D, E, F, G|
```