# Six-by-six-maze
Implement two search algorithms (Uniform  Cost Search and A*) for finding the shortest path in a six-by-six maze


# 🔍 Pathfinding Algorithms in a 6x6 Maze: UCS vs A*

This project implements and analyzes two classic pathfinding algorithms—**Uniform Cost Search (UCS)** and **A\* Search**—on a randomly generated 6×6 maze. The goal is to find the optimal path from a random start node to a goal node while avoiding barriers.

---

## 🧠 Objective

To compare the performance of UCS and A* search in terms of:
- **Completeness**
- **Optimality**
- **Time Complexity**
- **Path Quality** (mean and variance of path length and solution time)

---

## 🧪 Methodology

### 🔧 Maze Setup
- The maze is a 6×6 grid (36 nodes), each with `(x, y)` coordinates and a unique node ID.
- A custom `MazeNode` class encapsulates node attributes (coordinates, type: start/goal/barrier/normal).
- A `Maze` class manages initialization and configuration of the grid.

### 🎲 Random Setup
- **Start Node**: Randomly chosen from top-left quadrant (nodes 0–11)
- **Goal Node**: Randomly chosen from bottom-right quadrant (nodes 24–35)
- **Barriers**: 4 random nodes (excluding start and goal)
- **Valid Moves**: 8 directions (horizontal, vertical, and diagonal)
- **Edge Costs**:
  - Horizontal/Vertical: `1`
  - Diagonal: `√2 ≈ 1.414`
- **Visualization**:
  - Start: 🟩 Green
  - Goal: 🟥 Red
  - Barriers: ⬛ Black
  - Visited: 🟨 Yellow
  - Final Path: 🔵 Blue

---

## 🚀 Algorithms

### 🔄 Uniform Cost Search (UCS)
- Explores nodes based on cumulative path cost using a priority queue (`heapq`)
- Processes neighbors in ascending order of node ID
- **Exploration Time**: 1 minute per node
- **Output**:
  - List of visited nodes
  - Time to goal
  - Final path
- Visualized via `matplotlib`

### ✨ A* Search with Chebyshev Heuristic
- Prioritizes nodes using `f(n) = g(n) + h(n)` where:
  - `g(n)`: Actual path cost from start
  - `h(n)`: Chebyshev distance to goal →  
    `h(n) = max(|nx - gx|, |ny - gy|)`
- Avoids suboptimal paths using a dictionary to track best-known `g` costs
- Neighbor processing follows node ID order
- Visual output similar to UCS

---

## 💻 Technologies Used

- **Python**
- **Google Colab**
- `numpy` – numerical operations  
- `heapq` – priority queue management  
- `matplotlib` – maze visualization  
- `pandas` – data analysis & statistical metrics

---

## 📊 Output & Analysis

- Ran multiple trials with randomized mazes
- Collected data on:
  - Number of nodes visited
  - Total time taken (in node explorations)
  - Path length
- Statistical metrics:
  - **Mean** and **Variance** of solution times and path lengths
- Compared UCS and A* in:
  - Performance
  - Efficiency
  - Optimality

---

## ✅ Conclusion

A\* demonstrated superior efficiency, exploring fewer nodes compared to UCS, due to the use of the Chebyshev Distance heuristic.  
The statistical and theoretical analysis confirmed these findings, with A\* showing lower variability in exploration time and a more focused search strategy.
