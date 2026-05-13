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

> Document your understanding of why Dijkstra produces correct distances.
> Bullet points and short sentences throughout. No paragraphs.

### Part 3a: What the Invariant Means

> Two bullets: one for finalized nodes, one for non-finalized nodes.
> Do not copy the invariant text from the spec.

- **For nodes already finalized (in S):**
  _Your answer here._

- **For nodes not yet finalized (not in S):**
  _Your answer here._

### Part 3b: Why Each Phase Holds

> One to two bullets per phase. Maintenance must mention nonnegative edge weights.

- **Initialization : why the invariant holds before iteration 1:**
  _Your answer here._

- **Maintenance : why finalizing the min-dist node is always correct:**
  _Your answer here._

- **Termination : what the invariant guarantees when the algorithm ends:**
  _Your answer here._

### Part 3c: Why This Matters for the Route Planner

> One sentence connecting correct distances to correct routing decisions.

_Your answer here._

---

## Part 4: Search Design

### Why Greedy Fails

> State the failure mode. Then give a concrete counter-example using specific node names
> or costs (you may use the illustration example from the spec). Three to five bullets.

- **The failure mode:** _Your answer here._
- **Counter-example setup:** _Your answer here._
- **What greedy picks:** _Your answer here._
- **What optimal picks:** _Your answer here._
- **Why greedy loses:** _Your answer here._

### What the Algorithm Must Explore

> One bullet. Must use the word "order."

- _Your answer here._

---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---|---|---|---|
| Current location | | | |
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
