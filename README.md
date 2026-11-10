# AlgoStep

Step through an algorithm line by line and watch its variables change, entirely in the browser.

AlgoStep runs real Python 3.12 ([Pyodide](https://pyodide.org), compiled to WebAssembly) inside a single HTML page. Pick a problem and a solution, or write your own code. The page records every executed line with `sys.settrace`, then lets you replay the run step by step.

## Features

- **Example problems with several solutions:** Contains Duplicate, Valid Anagram, Two Sum, Best Time to Buy and Sell Stock, Valid Parentheses, Binary Search, Climbing Stairs, Reverse Linked List and Maximum Depth of Binary Tree. Each solution shows its time and space complexity.
- **Line by line:** the line about to run is highlighted, the previous line is shaded, and each line shows how many times it has run so far.
- **Explanations:** each step lists what the last line changed (`seen gained 3`, `nums[2]: 5 → 1`, `stack popped '('`) and the value of `if` and `while` conditions.
- **Visual state:** lists and strings as indexed cells with pointer variables (`i`, `j`, `l`, `r`, `mid`…) under them, sets as chips, dicts as key/value pairs, 2D lists as grids, linked lists as chains of nodes, and objects field by field. Changed values are highlighted.
- **Recursion:** the call stack is shown, and each call and return is a step.
- **LeetCode-style test cases:** paste a solution under *My code* (the default view). The function to run is detected from the code: the public method of `class Solution`, or a top-level function. Each parameter gets its own field. Add, remove and switch cases with the *Case 1, Case 2, +* tabs. An optional **Expected** value marks each case *Accepted* or *Wrong answer*.
- **LeetCode input syntax:** values accept `null`, `true` and `false`. A list becomes a `ListNode` chain or a `TreeNode` tree (level order) when the parameter is annotated that way, and results compare against the same list form. Pasting `nums = [1,2,3], k = 2` into a field fills every field; pasting several lines, one per parameter, creates several cases.
- **Trees:** binary trees are drawn as trees, with the variables that point into them shown under their nodes.
- **Your own code:** edit any solution. `print` output is captured. Code and test cases are saved in the browser.
- **Playback:** Play, Previous / Next, a scrubber, keyboard arrows, Home / End and adjustable speed.

## Usage

Open `index.html` in a modern browser. The first visit downloads the Pyodide runtime from jsDelivr (about 10 MB, cached afterwards).

1. Paste your solution in the editor (*My code*), or pick an example problem.
2. Fill in the test case fields, and optionally the expected output. Use **+** to add cases.
3. Press **Ctrl + Enter** (or Enter in a field). Every case runs; click a case tab to step through that case.

`List`, `Optional`, `ListNode`, `TreeNode`, `collections`, `heapq`, `math`, `defaultdict`, `Counter` and `deque` are predefined, as on LeetCode. If the code defines no function, Run traces the whole script.

## Limitations

- Traces stop after 3,000 steps, which also catches infinite loops.
- Conditions are only evaluated when they have no side effects (no calls except built-ins such as `len` or `min`).
- Containers show their first 200 elements, and linked lists their first 50 nodes.
- Design problems (a class with several methods called in sequence) aren't supported yet.
- Python only.

## License

MIT. Pyodide is licensed under MPL 2.0.
