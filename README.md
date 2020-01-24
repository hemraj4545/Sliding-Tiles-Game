# Sliding-Tiles-Game
Silding Tiles Game using Python and JSON

Sliding-Tile Puzzle

A sliding-tile puzzle is a rectangular grid of tile with one empty space. You can slide a tile into an adjacent empty space. The object of the puzzle is to rearrange the tiles into a given goal state. Figure 1 shows a typical instance of the 8-puzzle, which uses a 3 x 3 grid.

















Figure 1. Typical instance of the 8-puzzle.

For this assignment, we will limit ourselves to n x n sliding-tile puzzles, where n > 1. Such a puzzle has tiles numbered 1 to n2-1 plus the empty tile. For specific values of n, such puzzles are known as <n2-1>-puzzles. The most common are 8-puzzles and 15-puzzles.

In this assignment you will write a series of programs to solve sliding-tile puzzles using various uninformed and informed (heuristic) methods.

You may use whatever operating system and programming language you like.

Part 1 – Reading and Validating Sliding-Puzzle Problems

We will use JSON, which is described below, to define specific sliding-tile puzzle instances for your programs to solve. An example JSON corresponding to the instance of the 8-puzzle in Figure 1 is:

{"n" : 3,
"start" : [[7,2,4],
[5,0,6],
[8,3,1]],
"goal" : [[0,1,2],

[3,4,5],
[6,7,8]]}

This is an 8-puzzle problem with a grid size of n = 3 and the specified 3 x 3 matrices for the start state and the goal state. Each state is a 3 x 3 matrix of non-negative integers and the empty space is denoted by the integer 0.










1
 
JSON

JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.

A description of the JSON format as well as links to parsers for various languages is available on the JSON web site at http://www.json.org.

Specifics

Find a JSON parser for the programming language you have chosen to use – there are generally several JSON parsers available for all major programming languages. There are links to such parsers at the site given above.

Read a sliding-tile puzzle problem using a JSON parser. The form of the internal data varies from language to language and even from parser to parser. Consult the documentation for your selected parser.

Check that the sliding-tile puzzle problem is valid. Specifically, there must be fields named n, start, and goal. The n field must be a positive integer greater than 1. The start and goal fields must be n x n matrices containing the integers 0 (for the empty space) to n2-1.

You do not have to check that the problem is solvable – that is, that there is a series of moves that will transform the start state into the goal state.

Part 2 – Sliding-Tile Puzzle Rules

Given a sliding-tile puzzle state, you must be able to determine the rules that are applicable to that state that can be used to generate its successor states.

A rule has three parts:

•	name – a simple name for the rule (e.g., up, left, down, right)

•	precondition function – a Boolean function that accepts a state and returns true if the rule is applicable to state

•	action function – a function that accepts a state and returns the successor state obtained by applying the rule

You can use these rules to implement functions such as applicable-rule, which returns a list of the rules applicable to a given state, and successor-state, which returns the successor state for a given state and rule.

Specifics
Encode the rules for the sliding-tile puzzle. Remember that it is easiest to consider moving the empty space up, left, down, or right. Using these rules, write routines to determine the rules applicable to a state and the successor state given a state and rule to apply.

Note that you could implement these as iterators or have them return lists (or vectors) or rules and states.

Part 3 – Backtracking Control Strategy

The simplest problem-solving strategy is a depth-first search implemented using a backtracking control strategy. See the paper Backtracking.pdf on the Canvas web site for the class. This paper gives two backtracking algorithms – BACKTRACK(DATA) and BACKTRACK1(DATALIST). We will be using BACKTRACK1(DATALIST), which avoids cycles, for this programming assignment.

The BACKTRACK1(DATALIST) algorithm implements a recursive depth-first search through a state space. The DATALIST argument is a list of the states in the current search path. The algorithm returns either a list of the rules to reach the goal state or failure if no goal was found. [You will have to decide how to represent failure in your implementation. Note that returning an empty list for failure is not a good idea because an empty list actually represents success when you are at the goal.]

Specifics

Implement the BACKTRACK1(DATALIST) algorithm to solve instances of the sliding-puzzle problem. The depth bound may be a global variable or passed as an argument.

Implement a main program to accept a sliding-tile puzzle problem and solve it using the BACKTRACK1(DATALIST) algorithm. Print the start state and the goal state; the solution and solution length; and the number of states that were examined.

Implement a main program to accept a sliding-tile puzzle problem and solve it using an iterative depth-first search using the BACKTRACK1(DATALIST) algorithm. Print the cumulative number of states examined and the final (optimal) solution.

Part 4 – Graph Search

Graph search is a general purpose algorithm for searching graphs and state space problems are a prime example of problems that are represented as graphs. Depending on the specific data structure used to store the list of unexplored nodes, you can get a breadth-first search (using a queue), a depth-first search (using a stack), or any of a number of best-first searches (using priority queues – or sorted lists – with various cost or heuristic functions).

You may either use the function Uniform-Cost-Search (problem) (from p. 84 in the text) or the GRAPHSEARCH algorithm from the Graph Search.pdf document on the Canvas web site for the course. The function Uniform-Cost-Search (problem) is probably the easier of the two to implement. But, it is not a true graph search algorithm (as noted in footnote 9 on page 95 in the text “… A* requires some extra bookkeeping to ensure optimality.”). The GRAPHSEARCH algorithm has that “extra bookkeeping” by providing a true graph search.

<b>Specifics</b>
Implement either the Uniform-Cost-Search or GRAPHSEARCH algorithm and use it to perform a breadth-first search of sliding-tile problems.

Implement a main program to accept a sliding-tile puzzle and solve it using your implementation. Print the start and goal state; the solution and solution length; and the number of states generated and explored.
