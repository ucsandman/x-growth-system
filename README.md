# x-growth-system

The pipeline is source, extract, draft. Nothing else.

## The rule

Every draft traces to wes's real published work, cited inline. If a number is not in the source, it does not exist.

The test: "could anyone else have posted this?" If yes, it dies.

## Sources

- https://www.practicalsystems.io/blog — the Building in Public posts. Primary material.
- https://github.com/ucsandman — repos, READMEs, releases. Secondary material for shipped facts.

Material from anywhere else (memory files, conversation, the wes-voice stories file) is not usable in a draft until it is published at one of the two sources above. The stories file is a voice reference, not a source.

## Sourcing rules

1. Every factual claim in a draft must appear in the cited source. Quote or paraphrase. Never embellish, round up, or merge two stories into one.
2. Every thread cites its source URL at the end, on its own line.
3. No invented events, numbers, stories, or follow-ups.
4. No quotas. Drafts are written when there is new source material, not to fill a calendar.
5. No hook formulas, no engagement-bait question endings, no motivational sign-offs.
6. Drafts are distillations: X-native threads that deliver the useful content standalone (a real technique, lesson, or measured result), ending with the source link.
7. Voice: ~/workspace/skills/wes-voice/SKILL.md is mandatory for every draft. Before drafting, also read its references/samples.md and references/stories.md. Apply the X section of references/platforms.md for shape.
8. First person singular. The account is personal (@ucsandman). Drafts say I, never we.

## How a draft gets made

1. Read the source post in full.
2. Extract: the event, the real numbers with units, the technique or lesson, what was verified live vs what was not.
3. Draft the thread per templates.md.
4. Check every claim against the source. If it is not there, cut it.

## Files

- drafts/<slug>.md — one thread per source. Nothing else goes in drafts/.
- templates.md — the one template.
- SOURCES.md — the X algorithm mechanics (tagged VERIFIED/REPORTED/SPECULATION) plus the content-sourcing rules.
- metrics.md — weekly log.
- references/hooks-archive.md — the retired hook library. Archived, not for generation.

## Weekly run

Sundays 08:00 America/New_York (cron `x-growth-weekly`): scan the blog and GitHub for material published since the last run. Draft only from what is new, following the sourcing rules above. If nothing new was published, stay quiet: no draft, no commit.

## What killed v1 and v2

v1 was built on thin research: specific ranker numbers presented as fact with no verified basis. v2 fixed the algorithm research but kept the content factory: hook formulas, templates, and a quota of 12 posts a week, which produced synthetic posts with engagement-bait endings and fortune-cookie takes. v3 deletes the factory. The input is published work; the output is its distillation.
