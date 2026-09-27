# harness-arena draft

Post 1
I built an LMSYS-style arena for AI coding-agent harnesses. Two setups run the same task on the same commit, fresh git worktrees, identical prompt, hooks disabled, and a deterministic verdict comes out with a battle report.

Post 2
Correctness gates everything. A broken run never beats a correct one, no matter how fast it was. Between equally correct sides, the tie-break is weighted tokens, cost, and wall time at 40/35/25, and they have to be at least 5% apart or it is a tie.

Post 3
Battles run on your machine through the CLIs you already pay for, so no model costs for anyone but you. Arena never reads, copies, proxies, or uploads those credentials.

Post 4
Telemetry is never fabricated. Every metric carries observed, calculated, estimated, or unavailable. A CLI that does not report cost shows n/a, never 0. That one matters to me more than most of the features.

Post 5
Your harness is everything around the model: CLAUDE.md, hooks, skills, subagents. Now it can fight someone else's instead of you arguing about it.

https://github.com/ucsandman/harness-arena
