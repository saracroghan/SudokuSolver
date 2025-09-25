# AI Sudoku Solver

This project explores and implements a variety of artificial intelligence algorithms to solve Sudoku puzzles. It serves as a powerful demonstration and comparison of classic **Constraint Satisfaction Problem (CSP)** techniques versus modern **heuristic** and **local search** methods. Created with Jada Zorn.

---

## Features

* **Multi-Algorithm Implementation**: Solves Sudoku puzzles using five distinct AI approaches.
* **Easy Configuration**: Switch between different algorithms and puzzles by changing a single variable.
* **File I/O**: Reads puzzles from `.txt` files and exports the solved boards to new files.
* **Performance Comparison**: Allows for the direct comparison of the efficiency and effectiveness of different solving strategies.

---

## Algorithms Implemented

This solver is built around two main categories of AI algorithms.

### 1. Constraint Satisfaction (Backtracking)

These algorithms treat the Sudoku as a classic Constraint Satisfaction Problem. They work by intelligently exploring the search space of possible number placements, ensuring that no constraints (row, column, or 3x3 box rules) are violated.

* **Simple Backtracking**: The fundamental approach. It places a valid number in an empty cell and recursively moves to the next. If it hits a dead end, it backtracks to the previous cell and tries a different number.
* **Backtracking with Forward Checking**: An improvement where placing a number in a cell prunes the possible valid numbers for all other cells in the same row, column, and box. This reduces the search space more quickly.
* **Backtracking with Arc Consistency (AC-3)**: The most advanced CSP method here. It propagates constraints across the entire board, not just from the most recent move. This makes the domain of possible values for each cell consistent with its neighbors, significantly optimizing the search.

### 2. Heuristic and Local Search Methods

These algorithms start with a complete (but incorrect) board and iteratively improve it by reducing the number of "conflicts" (i.e., repeated numbers in a row, column, or box) until a solution is found.

* **Simulated Annealing**: This algorithm starts with a randomly filled board and makes small changes. It always accepts changes that reduce conflicts. Crucially, it sometimes accepts changes that *increase* conflicts, allowing it to escape "local optimums" where it might get stuck. The probability of accepting a bad move decreases over time.
* **Genetic Algorithm**: This method uses principles of natural selection. It creates a "population" of randomly filled boards. The "fittest" boards (those with the fewest conflicts) are selected to "reproduce," combining their rows to create a new generation of "child" boards. Random mutations are introduced to maintain genetic diversity, gradually evolving the population toward a perfect solution.

---

## Getting Started

Follow these steps to run the solver on your local machine.

### Prerequisites

* Python 3.x
* NumPy
* Jupyter Notebook or JupyterLab

### Installation

1.  **Clone the repository:**
    ```sh
    git clone [https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git)
    cd your-repository-name
    ```

2.  **Install dependencies:**
    ```sh
    pip install numpy notebook
    ```

### Execution

1.  **Launch Jupyter:**
    ```sh
    jupyter notebook
    ```

2.  **Configure the Solver**: Open the `SudokuSolver.ipynb` file. In the first code cell, set the following variables to choose your desired algorithm and puzzle file:
    ```python
    # Choose the algorithm: 'bt', 'fc', 'ac3', 'sa', 'ga'
    ALGORITHM = 'ac3'

    # Set the path to your puzzle file
    PUZZLE_PATH = '/path/to/your/Puzzles/Easy-P1.txt'
    ```

3.  **Run the Notebook**: Run all the cells in the notebook to solve the puzzle. The solved puzzle will be printed in the output and saved to a new `.txt` file in your project directory.

---

## Puzzle Format

The input puzzle files should be comma-separated values (`.csv` or `.txt`) representing the 9x9 grid. Use a question mark `?` for empty, unsolved cells.

**Example (`Easy-P1.txt`):**
