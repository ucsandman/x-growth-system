# A one-line edit cost me 77,000 tokens

Source: https://www.practicalsystems.io/blog/measure-your-subagent-token-cost (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

I delegated a one-line edit to a helper agent. It cost 77,000 tokens. The edit itself was maybe 40 tokens of actual change. Everything else was the helper arriving: its system prompt, its tool schemas, every skill it might want, every other agent it could call. All loaded before it read a single file.

## Post 2

The number is almost entirely a function of what you have installed. On my machine it costs 29,553 tokens to say hello. Two weeks ago it was over 40,000. A lean scout with a short tool list costs 15,746 tokens for the same nothing. A general-purpose agent costs 38,401. That is 22,655 tokens of pure arrival cost, decided by one field in the dispatch.

## Post 3

Three plugins off and nine unused skills archived took a fresh session from 73,600 tokens to 43,000. If you only do one thing here, audit what is installed before you edit a single prompt. Every plugin, skill, and MCP server is a line item on every spawn, forever, whether it fires once a month or never.

## Post 4

My rule now: under about ten tool calls or eighty lines of edits, I do it inline. Delegation earns its arrival cost when the work is genuinely large, the pieces run in parallel, or the output is long and would otherwise sit in main context being re-read every turn. Measure yours first. One command, thirty seconds, and you will know whether you have a problem.

https://www.practicalsystems.io/blog/measure-your-subagent-token-cost
