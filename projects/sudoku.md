---
layout: project
type: project
image: /assets/images/electrocat.png
title: "Sudoku Solver"
date: 2024
published: true
labels:
  - Java
  - Algorithms
  - Puzzle Solving
summary: "This project implements a Sudoku solver in Java. It validates the grid and finds a solution using backtracking."
---

<div class="text-center p-4">
  <img width="200px" src="/assets/images/electrocat.png" class="img-thumbnail">
  <img width="200px" src="/assets/images/electrocat.png" class="img-thumbnail">
</div>

The Sudoku Solver is a Java-based application that solves a given Sudoku puzzle. It uses a backtracking algorithm to fill in the empty cells of a 9x9 grid while following the Sudoku rules. The solver ensures that each number appears only once per row, column, and 3x3 subgrid. The project was implemented for the ICS 211 course assignment, with the goal of enhancing problem-solving and algorithm design skills.

### Code Overview

The core functionality of the Sudoku solver is implemented in the `Sudoku` class. The `checkSudoku` method ensures that the rules of Sudoku are adhered to, while the `fillSudoku` method uses backtracking to find a solution for the puzzle.

```java
public class Sudoku {

  public static boolean checkSudoku (int [][] sudoku, boolean printErrors) {
    // Implementation that checks rows, columns, and 3x3 grids for conflicts
  }

  public static boolean fillSudoku (int [][] sudoku) {
    // Backtracking algorithm to solve the Sudoku puzzle
  }

  public static String toString (int [][] sudoku, boolean debug) {
    // Converts the sudoku grid to a printable string
  }
}
