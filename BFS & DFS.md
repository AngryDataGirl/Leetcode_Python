#Concepts 
`Breadth First Search` (BFS) and `Depth First Search` (DFS) are two of the most common strategies employed in problems given during an interview. Proficiency in these two algorithms will allow you to solve (in our estimation) at least two-thirds of `tree` and [`graph` problems](https://algodaily.com/sections/draw-a-graph) that you may encounter in an interview.

## Breadth First Search Theory

In `Breadth First Search (BFS)`, the key is that it is a **level-based**, or **row-based** movement. At each level or row, the nodes of a tree are visited/traversed horizontally from left to right or right to left.

The horizontal direction chosen will depend on the problem statement. For instance, a problem that is looking for the sum of all nodes on the **right-hand side** may necessitate **right-to-left** traversal. This would allow you to just grab the first node, and immediately move on to the next level, without wasting cycles visiting the others.