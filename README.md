# The Torchbearer

**Student Name:** Gilad Bitton
**Student ID:** 130621085
**Course:** CS 460 – Algorithms | Spring 2026

---

## Part 1: Problem Analysis

- **Why a single shortest-path run from S is not enough:**
  The shortest path from S only gives the cheapest distances from the entrance to each node, but does not take ordering into account. Thus, the torchbearer won't know which relic to visit first, second, and so on.

- **What decision remains after all inter-location costs are known:**
  The decision that remains is the order in which the torchbearer will take the paths to all the relics before exiting. Different orders can have different fuel costs.

- **Why this requires a search over orders (one sentence):**
  This requires a search over orders because this task requires making a decision between different relic visit sequences by lowest fuel cost.

---

## Part 2: Precomputation Design

### Part 2a: Source Selection

| Source Node Type | Why it is a source |
|---|---|
| Entrance node S | The route starts at S, thus the planner needs cheapest distances from entrance to each relic.|
| Relic chambers in M | After collecting a relic from a chamber m, the planner may need to travel to other relics or the exit. |

### Part 2b: Distance Storage

| Property | Your answer |
|---|---|
| Data structure name | Nested python dict |
| What the keys represent | Outer keys are source nodes, inner are destination |
| What the values represent | The shortest distance from current source node to corresponding destination node |
| Lookup time complexity | O(1) |
| Why O(1) lookup is possible | Each destination node has only one shortest distance associated with it so hashing should be O(1) for lookup |

### Part 2c: Precomputation Complexity

> State the total complexity and show the arithmetic. Two to three lines max.

- **Number of Dijkstra runs:** k + 1
- **Cost per run:** O(m log n)
- **Total complexity:** O((k+1)m log n)
- **Justification (one line):** For each dijkstra run from a source node to all destination nodes, the cost is m*log(n).
If there are k relic chambers plus the single end node, then dijkstra will run k + 1 times. Thus O((k+1)m log n).

---

## Part 3: Algorithm Correctness

### Part 3a: What the Invariant Means

- **For nodes already finalized (in S):**
  Since the nodes have been finalized, we can assume that the path cost from x to any v in S is the shortest possible path cost.

- **For nodes not yet finalized (not in S):**
  Since the nodes have not yet been finalized, that may mean that there could be a shorter path from x to any v not yet in S that has just not been found yet.

### Part 3b: Why Each Phase Holds

- **Initialization : why the invariant holds before iteration 1:**
  - S = {}
  - Since the algorithm has not yet started, S is empty, so the finalized part of the invariant is true. 
  - The source starts with dist[x] = 0, and every other node starts with infinity until a path is discovered, so the not yet finalized part is true.

- **Maintenance : why finalizing the min-dist node is always correct:**
  - S = {(x, 0), (v_1, dist[v_1]), ...} for all v that have been finalized
  - Since all edge weights are nonnegative, we can safely add unfinalized node with lowest current distance since later nodes will only add distance.

- **Termination : what the invariant guarantees when the algorithm ends:**
  - S = {(x, 0), (v_n, dist[v_n])} for all v destination nodes.
  - Since the algorithm has finished, all destination nodes are finalized with minimum distance. Thus the invariant holds.

### Part 3c: Why This Matters for the Route Planner

Correct shortest route distances matter because the algorithm uses them when comparing relic visit orders. 
Since we need to find the shortest path that connects the source to all relics and the end.

---

## Part 4: Search Design

### Why Greedy Fails

- **The failure mode:** The local shortest distance to relic may force a more expensive path later.
- **Counter-example setup:** 

    | From \ To | B   | C   | D   | T   |
    |-----------|-----|-----|-----|-----|
    | S         | 1   | 2   | 2   | --  |
    | B         | --  | 100 | 1   | 1   |
    | C         | 1   | --  | 100 | 100 |
    | D         | 1   | 1   | --  | 100 |
- **What greedy picks:** Route: S -> B -> D -> C -> T = 103 fuel cost
- **What optimal picks:** Route: S -> D -> C -> B -> T = 5 fuel cost
- **Why greedy loses:** Greedy chooses B since it's best immediate choice at start, but it forces it onto a very costly edge from C to T.

### What the Algorithm Must Explore

The algorithm must explore the order in which these relics are visited, we want to have the shortest distance possible from start to finish.

---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---|---|---|---|
| Current location | current_loc | node | |
| Relics already collected | | | |
| Fuel cost so far | | | |

### Part 5b: Data Structure for Visited Relics

> Fill in the table.

| Property | Your answer |
|---|---|
| Data structure chosen | |
| Operation: check if relic already collected | Time complexity: |
| Operation: mark a relic as collected | Time complexity: |
| Operation: unmark a relic (backtrack) | Time complexity: |
| Why this structure fits | |

### Part 5c: Worst-Case Search Space

> Two bullets.

- **Worst-case number of orders considered:** _Your answer (in terms of k)._
- **Why:** _One-line justification._

---

## Part 6: Pruning

### Part 6a: Best-So-Far Tracking

> Three bullets.

- **What is tracked:** _Your answer here._
- **When it is used:** _Your answer here._
- **What it allows the algorithm to skip:** _Your answer here._

### Part 6b: Lower Bound Estimation

> Three bullets.

- **What information is available at the current state:** _Your answer here._
- **What the lower bound accounts for:** _Your answer here._
- **Why it never overestimates:** _Your answer here._

### Part 6c: Pruning Correctness

> One to two bullets. Explain why pruning is safe.

- _Your answer here._

---

## References

> Bullet list. If none beyond lecture notes, write that.

- _Your references here._
