# Sliding-Tiles-Game
Silding Tiles Game using Python and JSON

A sliding-tile puzzle is a rectangular grid of tile with one empty space. You can slide a tile into an adjacent empty space. The object of the puzzle is to rearrange the tiles into a given goal state.

![tile](https://user-images.githubusercontent.com/38886899/73072756-d45f5980-3edb-11ea-8a81-2dcd34997a64.jpg)

## Part 1 – Reading and Validating Sliding-Puzzle Problems ##

We will use JSON, which is described below, to define specific sliding-tile puzzle instances for the programs to solve. An example JSON corresponding to the instance of the 8-puzzle in Figure is:

{

"n" : 3,

"start" : [[7,2,4], [5,0,6], [8,3,1]],

"goal" : [[0,1,2], [3,4,5], [6,7,8]]

}

This is an 8-puzzle problem with a grid size of n = 3 and the specified 3 x 3 matrices for the start state and the goal state. Each state is a 3 x 3 matrix of non-negative integers and the empty space is denoted by the integer 0.

### Specifics ###

* Reading a sliding-tile puzzle problem using a JSON parser. The form of the internal data varies from language to language and even from parser to parser.
* Checking that the sliding-tile puzzle problem is valid. Specifically, there must be fields named n, start, and goal. The n field must be a positive integer greater than 1. The start and goal fields must be n x n matrices containing the integers 0 (for the empty space) to n<sup>2</sup>-1.

## Part 2 – Sliding-Tile Puzzle Rules ##

A rule has three parts:

* name – a simple name for the rule (e.g., up, left, down, right)
* precondition function – a Boolean function that accepts a state and returns true if the rule is applicable to state
* action function – a function that accepts a state and returns the successor state obtained by applying the rule

Using these rules to implement functions such as applicable-rule, which returns a list of the rules applicable to a given state, and successor-state, which returns the successor state for a given state and rule.

### Specifics ###
Encoding the rules for the sliding-tile puzzle. It is easiest to consider moving the empty space up, left, down, or right. Using these rules, writing routines to determine the rules applicable to a state and the successor state given a state and rule to apply.

## Part 3 – Backtracking Control Strategy ##

The simplest problem-solving strategy is a depth-first search implemented using a backtracking control strategy.Two backtracking algorithms – BACKTRACK(DATA) and BACKTRACK1(DATALIST). We will be using BACKTRACK1(DATALIST), which avoids cycles, for this programming assignment.

The BACKTRACK1(DATALIST) algorithm implements a recursive depth-first search through a state space. The DATALIST argument is a list of the states in the current search path. The algorithm returns either a list of the rules to reach the goal state or failure if no goal was found.

### Specifics ###

* Implementing the BACKTRACK1(DATALIST) algorithm to solve instances of the sliding-puzzle problem. The depth bound may be a global variable or passed as an argument.
* Implementing a main program to accept a sliding-tile puzzle problem and solve it using the BACKTRACK1(DATALIST) algorithm. Print the start state and the goal state; the solution and solution length; and the number of states that were examined.
* Implementing a main program to accept a sliding-tile puzzle problem and solve it using an iterative depth-first search using the BACKTRACK1(DATALIST) algorithm. Printing the cumulative number of states examined and the final (optimal) solution.

**Implementing a main program to accept a sliding-tile puzzle and solve it using our implementation. Print the start and goal state; the solution and solution length; and the number of states generated and explored.**
