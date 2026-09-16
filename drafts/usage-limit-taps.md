# Where coding agents hide their usage limits

Source: https://www.practicalsystems.io/blog/where-coding-agents-hide-usage-limits (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

Someone asked on X for a harness that hands work between coding agents when one hits its limit. 1,024 bookmarks, 340 replies. Nobody answered the actual question, so I built it in four days. The hard part is not the handoff. It is knowing the limit is coming, and every agent reports it differently. One of them does not report it at all.

## Post 2

Claude Code: the number lives at GET api.anthropic.com/api/oauth/usage, using the OAuth token it already stored on your machine. You get a 5-hour window and a 7-day window, each with a utilization percentage and a reset timestamp. Codex: it writes its whole thread to a rollout JSONL file, and event_msg.token_count.rate_limits carries both windows. Observed live on codex-cli 0.153.4.

## Post 3

Antigravity: there is no number. Closed Go binary, nothing on disk. You get --log-file and string matching on RESOURCE_EXHAUSTED. And the reset text reads "Resets in 71h19m42s", which computes as 71 seconds if you grab the first unit. Three days versus seventy-one seconds is the kind of bug that looks fine in a test and wastes your evening.

## Post 4

Put the agents that can warn you first and the blind one last. You can plan around a number. You cannot plan around a wall. And a limit handler you have never seen fire is a guess with good syntax. I am straight in the post about which paths I verified live and which I did not.

https://www.practicalsystems.io/blog/where-coding-agents-hide-usage-limits
