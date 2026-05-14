# Development Log – The Torchbearer

**Student Name:** Gilad Bitton
**Student ID:** 130621085

> Instructions: Write at least four dated entries. Required entry types are marked below.
> Two to five sentences per entry is sufficient. Write entries as you go, not all in one
> sitting. Graders check that entries reflect genuine work across multiple sessions.
> Delete all blockquotes before submitting.

---

## Entry 1 – [5/13/2026]: Initial Plan

Since the assignment was laid out step by step, I will go through each step on the ASSIGNMENT.md and fill out the written answer before then filling out the corresponding code. I expect the recursion steps to be difficult to wrap my head around the logic of. I plan to test it with the premade test function as its good at covering different edge cases.

---

## Entry 2 – [5/13/2026]: Backtracking Mutation Bug

> Required. At least one entry must describe a bug, wrong assumption, or design change
> you encountered. Describe what went wrong and how you resolved it.

While implementing the _explore() function, I initially tried to directly loop through the remaining relics, while also removing them from that same list. This was a problem as it ended up skipping items and causing various other unpredictable behavior. I fixed this bug by iterating over a list copy of the relics_remaining set. Then I removed relics before the recursive call and added them back during backtracking.

---

## Entry 4 – [5/13/2026]: Post-Implementation Reflection

After finishing this I would have liked, given more time, to implement this algorithm to tackle different edge cases. For example, the aforementioned negative edge cases. Is there a way to implement this algorithm given nonnegative edge cases without risking O(k!)? I would have liked to delve into it.

---

## Final Entry – [5/13/2026]: Time Estimate

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | 10M |
| Part 2: Precomputation Design | 10M |
| Part 3: Algorithm Correctness | 20M |
| Part 4: Search Design | 10M |
| Part 5: State and Search Space | 10M |
| Part 6: Pruning | 10M |
| Part 7: Implementation | 2H |
| README and DEVLOG writing | 20M |
| **Total** | 3H 30M |
