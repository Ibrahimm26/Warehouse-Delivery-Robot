Warehouse Delivery Robot — Intelligent Systems

📌 Project Overview

This project implements a pathfinding system for a warehouse delivery robot. The robot must find a path from a starting position ("S") to a goal position ("G") in a grid-based warehouse while avoiding walls and minimizing the total movement cost.

The project compares two search algorithms:

- Uniform Cost Search (UCS) — an uninformed search algorithm.
- A* Search — an informed search algorithm that uses a heuristic to guide the search toward the goal.

The warehouse contains different types of terrain, so finding the path with the fewest steps does not always mean finding the cheapest path.

🎯 Project Objectives

- Implement UCS and A* without using external pathfinding libraries.
- Find the start and goal positions automatically.
- Avoid blocked cells and find valid paths through the grid.
- Calculate the total cost of each path.
- Count the number of expanded nodes.
- Measure the maximum frontier size and execution time.
- Display the final path on the warehouse map.
- Compare the performance of UCS and A* across different maps.

🗺️ Warehouse Map Representation

The warehouse is represented as a two-dimensional grid.

Symbol| Meaning| Movement Cost
"S"| Starting position| Not counted
"G"| Goal position| 1
"."| Normal floor| 1
"~"| Rough floor| 3
"#"| Wall / blocked cell| Impassable
"*"| Cell included in the discovered path| Depends on the original cell

The robot can move in four directions only:

- Up
- Down
- Left
- Right

Diagonal movement is not allowed.

🧠 Algorithms Used

1. Uniform Cost Search (UCS)

UCS expands the node with the lowest accumulated path cost.

It uses:

[
f(n)=g(n)
]

Where:

- (g(n)) is the total cost from the start to the current node.

Why UCS?

The warehouse contains different movement costs. UCS considers these costs and finds the minimum-cost path when a path exists.

2. A* Search

A* combines the actual cost of reaching a node with an estimate of the remaining cost to the goal.

[
f(n)=g(n)+h(n)
]

Where:

- (g(n)) is the actual cost from the start to the current node.
- (h(n)) is the estimated cost from the current node to the goal.

The project uses Manhattan Distance as the heuristic:

[
h(n)=|r_n-r_g|+|c_n-c_g|
]

Where:

- (r_n,c_n) are the current cell coordinates.
- (r_g,c_g) are the goal coordinates.

Manhattan Distance is suitable because the robot moves only horizontally and vertically. Since every traversable move costs at least 1, this heuristic does not overestimate the remaining cost.

Why A?*

A* considers both the cost already paid and the estimated remaining cost. With this heuristic and the implemented search conditions, it can find an optimal-cost path while guiding the search toward the goal.

⚖️ Why UCS and A*?

UCS and A* provide a useful comparison between uninformed and informed search.

- UCS finds the lowest-cost path without using a heuristic.
- A* uses a heuristic to guide the search while considering the accumulated cost.
- BFS focuses on the number of moves and is not guaranteed to find the lowest-cost path when movement costs differ.
- DFS does not guarantee an optimal path.
- Greedy Best-First Search prioritizes the estimated distance to the goal but does not fully account for the cost already paid.

🧪 Test Maps

The project evaluates the algorithms on three different warehouse maps:

- Map A: Contains walls and rough-floor cells.
- Map B: Contains a long rough-floor route, demonstrating the importance of movement costs.
- Map C: Contains obstacles that prevent a valid path from the start to the goal.

Each algorithm is executed on all three maps.

📊 Performance Evaluation

The algorithms are evaluated using the following metrics:

Metric| Description
Path Length| Number of movements in the discovered path
Path Cost| Total movement cost of the path
Nodes Expanded| Number of nodes explored by the algorithm
Maximum Frontier Size| Largest number of nodes stored in the frontier during the search
Execution Time| Time required to execute the search

The results help compare solution quality and search performance. Execution time may vary depending on the computer and runtime environment.

🖥️ Output

For each map and algorithm, the program displays:

- Algorithm name.
- Path as a list of "(row, column)" coordinates.
- Total path cost.
- Number of expanded nodes.
- Warehouse map with the path marked using "*".
- Performance comparison table.

If no valid path exists, the program displays:

"No path found"

🛠️ Technologies Used

- Python 3
- "heapq" for priority queues
- "time" for execution-time measurement
- Jupyter Notebook

No external pathfinding libraries are used.

▶️ How to Run the Project

1. Clone or download this repository.
2. Open the project folder.
3. Open the Jupyter Notebook containing the implementation.
4. Run all cells in order.
5. Review the displayed paths and performance comparison table.

Alternatively, run the Python implementation in a Python environment that supports the required standard-library modules.

📁 Project Structure

Warehouse-Delivery-Robot/
│
├── IntelligentSys_Task_1_Warehouse_Robot.ipynb
└── README.md

📌 Conclusion

This project demonstrates how uninformed and informed search algorithms can solve a weighted pathfinding problem.

UCS provides a minimum-cost solution without heuristic guidance, while A* uses Manhattan Distance to guide its exploration toward the goal. Comparing their path costs, expanded nodes, frontier sizes, and execution times provides insight into their behavior in different warehouse environments.

The project highlights the importance of considering terrain costs rather than simply choosing the path with the fewest movements.

👨‍🎓 Academic Project

Course: Intelligent Systems
Project: Task 1 — Warehouse Delivery Robot
Algorithms: Uniform Cost Search (UCS) and A* Search
