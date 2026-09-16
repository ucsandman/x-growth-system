# Markdown is all you need (agent memory)

Source: https://www.practicalsystems.io/blog/markdown-is-all-you-need (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

A memory startup DM'd me and asked me to break their product. Their test: give an agent three versions of the same decision, then check whether it returns the current one. REST in January, GraphQL in April, tRPC in August. It answered GraphQL. The superseded one. All three versions came back tied at a relevance score of 1.000.

## Post 2

The schema knew about time. The write path and the read path did not. Nothing wrote to the temporal fields and nothing ranked by them. Three versions of a decision are just three equal facts, and an agent asking for the best answer gets a coin flip weighted toward wrong. The install pulled 382 packages to get there.

## Post 3

My own agent keeps its memory in markdown files in a git repo. Same class of question, and it returns the current decision, dated, with the superseded versions struck through above it, each line carrying where it came from. That is not computed at query time. It is just what the file says, because the editing rules require it. git log is the validity window. blame is per-line provenance.

## Post 4

The reliability was never in the storage. It is in four write rules: every fact gets a provenance tag, inferred lessons need three independent signals across two sessions before they become rules, supersession is an edit not an append, and memory only stores what cannot be recomputed. Seven months in production, three models, two vendors. The folder is the product. The discipline is the moat.

https://www.practicalsystems.io/blog/markdown-is-all-you-need
