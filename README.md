# AlgoStep

Step through an algorithm line by line and watch its variables change, entirely in the browser.

AlgoStep runs real Python 3.12 ([Pyodide](https://pyodide.org), compiled to WebAssembly) inside a single HTML page. Pick a problem and a solution, or write your own code. The page records every executed line with `sys.settrace`, then lets you replay the run step by step.

## Features

- **Problems with several solutions:** Contains Duplicate, Valid Anagram, Two Sum, Best Time to Buy and Sell Stock, Valid Parentheses, Binary Search, Climbing Stairs and Reverse Linked List. Each solution shows its time and space complexity.
- **Line by line:** the line about to run is highlighted, the previous line is shaded, and each line shows how many times it has run so far.
- **Explanations:** each step lists what the last line changed (`seen gained 3`, `nums[2]: 5 → 1`, `stack popped '('`) and the value of `if` and `while` conditions.
- **Visual state:** lists and strings as indexed cells with pointer variables (`i`, `j`, `l`, `r`, `mid`…) under them, sets as chips, dicts as key/value pairs, 2D lists as grids, linked lists as chains of nodes, and objects field by field. Changed values are highlighted.
- **Recursion:** the call stack is shown, and each call and return is a step.
- **Free code:** pick *Free code* in the problem menu to write any Python with no problem attached. Type the program's input in the **Input** box and read it with `input()` or `sys.stdin`. Leave the Run line empty to trace the whole script, or write a call to trace one function.
- **Your own code:** edit any solution. `print` output is captured. Edits and input are saved in the browser.
- **Playback:** Play, Previous / Next, a scrubber, keyboard arrows, Home / End and adjustable speed.

## Usage

Open `index.html` in a modern browser. The first visit downloads the Pyodide runtime from jsDelivr (about 10 MB, cached afterwards).

1. Pick a problem, then a solution tab.
2. Adjust the code or the **Run** line, for example `Solution().hasDuplicate([1, 2, 3, 3])`.
3. Press **Ctrl + Enter** and step through.

The Run line's arguments are evaluated before tracing starts, so only your solution's own lines become steps. `linked([1, 2, 3])` builds a linked list from your `ListNode` class. `List`, `Optional`, `collections`, `heapq`, `math`, `defaultdict`, `Counter` and `deque` are already imported, as on LeetCode.

## Limitations

- Traces stop after 3,000 steps, which also catches infinite loops.
- Conditions are only evaluated when they have no side effects (no calls except built-ins such as `len` or `min`).
- Containers show their first 200 elements, and linked lists their first 50 nodes.
- Python only.

## License

MIT. Pyodide is licensed under MPL 2.0.
