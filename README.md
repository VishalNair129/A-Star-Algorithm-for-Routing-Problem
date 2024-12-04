# Summary and Implementation of the A*-Algorithm

This repository contains the implementation of the A*-algorithm, a widely used pathfinding and graph traversal algorithm. The A* algorithm is employed to find the shortest path between a start node and a goal node, combining the strengths of Dijkstra’s algorithm and Greedy Best-First-Search. This implementation uses the Haversine distance as a heuristic for geospatial routing problems.

## Project Overview

### Key Components of the A*-Algorithm
- **Open Set:** A priority queue that holds nodes to be explored. Nodes are expanded based on the smallest f value.
- **g(n):** The exact cost from the start node to node n.
- **h(n):** The heuristic cost estimate from node n to the goal node, using the Haversine distance.
- **f(n):** The estimated total cost of the cheapest solution through node n, defined as f(n) = g(n) + h(n).

### The Routing Problem
The implementation addresses geospatial routing problems using the Haversine distance, which calculates the distance between two points on a spherical surface. The heuristic ensures admissibility, consistency, and monotonicity, guiding the search efficiently.

### Documentation of Implementational Framework
The implementation is divided into three files:
1. **binfile.c:** Preprocesses map data from a CSV file and generates a binary file for faster access.
2. **AStar.c:** Implements the A*-algorithm, reading the preprocessed binary file to find the shortest path.
3. **Map_Plot.py:** Visualizes the solution found by the A*-algorithm.

---

## File Descriptions

### binfile.c
This file preprocesses map data from a CSV file and generates a binary file.

#### Functions
- **main():** Extracts and formats nodes and edges from a CSV file, writes the information into a binary file.
- **searchNode():** Performs a binary search to find a node by its ID.
- **ExitError():** Handles errors by printing a message and exiting the program.

### AStar.c
This file contains the implementation of the A* algorithm, reading the preprocessed binary file to find the shortest path.

#### Functions
- **main():** Reads the binary file, defines start and goal nodes, executes the A*-algorithm, and prints the results.
- **searchNode():** Identical to the implementation in `binfile.c`.
- **ExitError():** Identical to the implementation in `binfile.c`.
- **haversine_distance():** Calculates the Haversine distance between two points.
- **Oenqueue():** Adds a vertex to a priority queue.
- **Odequeue():** Removes the first element from a priority queue.
- **Orequeue():** Adjusts the position of a vertex within a priority queue.
- **astar():** The core function implementing the A* algorithm.

### Map_Plot.py
This script visualizes the path found by the A* algorithm.

#### Usage
- The path obtained from the A* algorithm is stored in `Astarpath.txt`.
- Run the script to generate a plot of the path.

---

## Compilation Instructions
To compile the provided code files, use the following commands:

```sh
gcc -o binfile binfile.c
gcc -o AStar AStar.c
```
## Execution Instructions

## Preprocessing the Map Data
Run the binfile executable to preprocess the map data:

```sh
./binfile <map_file>
```
Example:

```sh
./binfile spain.csv
This will produce a binary file named spain.csv.bin.
```

## Running the A* Algorithm
Run the AStar executable to find the shortest path using the A* algorithm:

```sh
./AStar <start_id> <goal_id> <map_file>
```
Example:

```sh
./AStar 240949599 195977239 spain.csv.bin
```
The results will be printed to the console and saved to a file named Astarpath.txt.

## Visualizing the Path
Ensure that you have the necessary Python environment set up with the required dependencies. Run the Map_Plot.py script:

```sh
python Map_Plot.py Astarpath.txt
```
The output will be saved as an Astarpath.html file, which contains the plot of the path.

## Conclusion
This implementation efficiently preprocesses map data for use with the A* algorithm. The binary format allows for quick access and manipulation of nodes and their successors. By using the Haversine distance as a heuristic, the A* algorithm effectively finds the shortest path on a spherical surface, making it suitable for geographic data. The provided compilation and execution instructions ensure that users can easily preprocess their map data and run the A* algorithm on it.

