---
layout: project
type: project
image: img/200px-Sudoku06u.png
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
  <img width="400px" src="../img/Sudoku_image_2.png" class="img-thumbnail">
</div>

The Sudoku Solver is a Java-based application that solves a given Sudoku puzzle. It uses a backtracking algorithm to fill in the empty cells of a 9x9 grid while following the Sudoku rules. The solver ensures that each number appears only once per row, column, and 3x3 subgrid. The project was implemented for the ICS 211 course assignment, with the goal of enhancing problem-solving and algorithm design skills.

### Code Overview

The core functionality of the Sudoku solver is implemented in the `Sudoku` class. The `checkSudoku` method ensures that the rules of Sudoku are adhered to, while the `fillSudoku` method uses backtracking to find a solution for the puzzle.

```java
public class Sudoku {

  /* check that the sudoku rules hold in this sudoku puzzle.
   * cells that contain 0 are not checked.
   * @param the sudoku to be checked
   * @param whether to print the error found, if any
   * @return true if this sudoku obeys all of the sudoku rules, otherwise false
   */
  public static boolean checkSudoku (int [] [] sudoku, boolean printErrors)
  {
    if (sudoku.length != 9) {
      if (printErrors) {
        System.out.println ("sudoku has " + sudoku.length +
                            " rows, should have 9");
      }
      return false;
    }
    for (int i = 0; i < sudoku.length; i++) {
      if (sudoku [i].length != 9) {
        if (printErrors) {
          System.out.println ("sudoku row " + i + " has " +
                              sudoku [i].length + " cells, should have 9");
        }
        return false;
      }
    }
    /* check each cell for conflicts */
    for (int i = 0; i < sudoku.length; i++) {
      for (int j = 0; j < sudoku.length; j++) {
        int cell = sudoku [i] [j];
        if (cell == 0) {
          continue;   /* blanks are always OK */
        }
        if ((cell < 1) || (cell > 9)) {
          if (printErrors) {
            System.out.println ("sudoku row " + i + " column " + j +
                                " has illegal value " + cell);
          }
          return false;
        }
        /* does it match any other value in the same row? */
        for (int m = 0; m < sudoku.length; m++) {
          if ((j != m) && (cell == sudoku [i] [m])) {
            if (printErrors) {
              System.out.println ("sudoku row " + i + " has " + cell +
                                  " at both positions " + j + " and " + m);
            }
            return false;
          }
        }
        /* does it match any other value it in the same column? */
        for (int k = 0; k < sudoku.length; k++) {
          if ((i != k) && (cell == sudoku [k] [j])) {
            if (printErrors) {
              System.out.println ("sudoku column " + j + " has " + cell +
                                  " at both positions " + i + " and " + k);
            }
            return false;
          }
        }
        /* does it match any other value in the 3x3? */
        for (int k = 0; k < 3; k++) {
          for (int m = 0; m < 3; m++) {
            int testRow = (i / 3 * 3) + k;   /* test this row */
            int testCol = (j / 3 * 3) + m;   /* test this col */
            if ((i != testRow) && (j != testCol) &&
                (cell == sudoku [testRow] [testCol])) {
              if (printErrors) {
                System.out.println ("sudoku character " + cell + " at row " +
                                    i + ", column " + j + 
                                    " matches character at row " + testRow +
                                    ", column " + testCol);
              }
              return false;
            }
          }
        }
      }
    }
    return true;
  }

  /* convert the sudoku to a printable string
   * @param the sudoku to be converted
   * @param whether to check for errors
   * @return the printable version of the sudoku
   */
  public static String toString (int [] [] sudoku, boolean debug) {
    if ((! debug) || (checkSudoku (sudoku, true))) {
      String result = "";
      for (int i = 0; i < sudoku.length; i++) {
        if (i % 3 == 0) {
          result = result + "+-------+-------+-------+\n";
        }
        for (int j = 0; j < sudoku.length; j++) {
          if (j % 3 == 0) {
            result = result + "| ";
          }
          if (sudoku [i] [j] == 0) {
            result = result + "  ";
          } else {
            result = result + sudoku [i] [j] + " ";
          }
        }
        result = result + "|\n";
      }
      result = result + "+-------+-------+-------+\n";
      return result;
    }
    return "illegal sudoku";
  }

  /* find an assignment of values to sudoku cells that makes the sudoku valid
   * @param the sudoku to be filled
   * @return whether a solution was found 
   *    if a solution was found, the sudoku is filled in with the solution
   *    if no solution was found, restores the sudoku to its original value
   */
  public static boolean fillSudoku (int [] [] sudoku)
  {
	boolean allFilled = true;
	int row = -1;
	int col = -1;
	
	for (int i = 0; i < 9; i++) {
		for (int j = 0; j < 9; j++) {
			if (sudoku[i][j] == 0) {
				row = i;
				col = j;
				allFilled = false;
				break;
			}
		}
		if (!allFilled) {
			break;
		}
	}
	if (allFilled) {
		return true;
	}
	for (int num = 1; num <= 9; num++) {
    	sudoku[row][col] = num;
    	if (checkSudoku(sudoku, false)) {
    		if (fillSudoku(sudoku)) {
    			return true;
    		}
    	}
    }
	sudoku[row][col] = 0;
	return false;
  }
}
```
