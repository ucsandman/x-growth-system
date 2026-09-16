# Your coding agent pays to relearn your repo every morning

Source: https://www.practicalsystems.io/blog/your-coding-agent-pays-to-relearn-your-repo-every-morning (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

Every AI coding session burns 20k to 60k tokens re-reading the repo before it does anything new. The README, the config, the files it touched yesterday, the tests. Two sessions a day, five days a week, and you are paying frontier-model prices for the agent to remember what it already knew.

## Post 2

So I built Context Handoff Bundle and open-sourced it. It saves a session's working state as a durable bundle: the findings, the open questions, the decisions, and evidence anchors pointing at the exact files and commits those findings came from. The next session loads the bundle instead of re-reading the repo. About 640 tokens to resume instead of about 23,000 to rebuild from source.

## Post 3

The part that matters: it knows when it is stale. On load the bundle checks its evidence anchors against the live repo. If a file a finding depended on changed, that finding gets flagged. If most anchors drifted, the recommendations get flagged. A saved summary you cannot trust is worse than no summary.

## Post 4

Shipped three releases in two days, each one fixing a failure hit on a real repo. Someone on Reddit asked about renames within an hour of launch, and the fix was live that afternoon. pip install context-handoff-bundle. Source at github.com/ucsandman/context-handoff-bundle.

https://www.practicalsystems.io/blog/your-coding-agent-pays-to-relearn-your-repo-every-morning
