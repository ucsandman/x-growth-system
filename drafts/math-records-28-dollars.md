# An AI agent broke 10 math records overnight for $28

Source: https://www.practicalsystems.io/blog/ai-agent-broke-10-math-records-overnight-for-28-dollars (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

An agent broke 10 math records overnight for $28. I pointed an LLM-driven evolution loop at Packomania's circle packing benchmark. By morning it had beaten 10 listed records, margins of 2.5% to 5.4% above the prior best. Total model cost: $27.72.

## Post 2

The loop is three parts. A seed solver produces a mediocre packing. An LLM reads the champion solver, the scoreboard of my results against the listed records, and the history of ideas already tried, then writes a complete replacement solver. A zero-tolerance verifier checks every circle placement in float64. The model cannot influence the checker.

## Post 3

The cost curve is the real story. The first $14 bought 99.9% of the total improvement. The second $14 bought 0.1%. The last 5 iterations spent $13.76 for a total gain of 0.006. I added a plateau detector that stops the loop when improvement flattens. Backtested on this run, it would have stopped after iteration 9, saved half the spend, and given up 0.01% of final quality.

## Post 4

The system that knows when to stop is more valuable than the system that runs. Automated research is a cost-optimization problem as much as a search problem. The code is public at github.com/ucsandman/discovery-loop. Paper: https://arxiv.org/abs/2609.05093

https://www.practicalsystems.io/blog/ai-agent-broke-10-math-records-overnight-for-28-dollars
