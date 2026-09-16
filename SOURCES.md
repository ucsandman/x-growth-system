# SOURCES.md

Every mechanistic claim in this repo, tagged. Read 2026-09-16.

- **VERIFIED**: read directly in X's published code or official documentation.
- **REPORTED**: a credible named secondary source. Believed, but not primary.
- **SPECULATION**: guru or influencer claim with no verified basis. Not used for strategy.

Primary source: the scoring defaults at https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs, synced from production feature-switch defaults at 2026-09-15T16:25:02Z (per the file's own comment).

## VERIFIED: weights multiply predicted probabilities, not counts

The code comments in param.rs state the scoring formula explicitly: each weight multiplies the *predicted probability* of an action for a specific viewer and candidate post. The comments name and reject the count-equivalence reading, calling "one report cancels 468 likes" incorrect. The comment on negative weights explains the sizing: "the baseline probability of a Report is more than 1000x lower than a Like, so it's weighted more to allow the prediction to affect the final ranking at all."

This kills every "X likes equals one Y" claim. Weight ratios are real numbers in the formula. Count equivalences are not.

## VERIFIED: positive weights (current defaults)

From param.rs, read 2026-09-16:

| Action | Weight |
|---|---|
| Share via copy link | 20.0 |
| Reply | 5.0 |
| Quote | 5.0 |
| Share via DM | 5.0 |
| Follow author | 4.0 |
| Repost | 1.0 |
| Favorite (like) | 0.5 |
| Click | 0.4 |
| Open link | 0.2 |
| Video open | 0.07 |
| Dwell | 0.05 |
| Photo expand | 0.05 |
| Quoted click | 0.05 |
| Post unexplored | 0.02 |
| Continuous dwell time | 0.004 |
| Profile click | 0.0 |
| Video quality view | 0.0 |
| Quoted video quality view | 0.0 |
| Click dwell time | 0.0 |

Copy-link share is the highest positive weight. DM share and reply/quote are the next tier. Like is 0.5.

## VERIFIED: negative weights (current defaults)

From param.rs, read 2026-09-16:

| Action | Weight |
|---|---|
| Not interested | -43.2 |
| Block author | -31.2 |
| Mute author | -58.8 |
| Report | -234.0 |
| Not dwelled | -0.02 |

The code's own framing: rare negative actions are weighted heavily so their tiny predicted probabilities can move the final score at all. Reports are personalized per the code comments: reports from bad actors mostly affect recommendations for users similar to them.

## VERIFIED: out-of-network discount

param.rs: OonWeightFactor 0.75. Posts from accounts the viewer does not follow are scored normally, then multiplied by 0.75. Topic out-of-network candidates get 0.5. In-network replies and reposts to out-of-network posts get the same rescore treatment. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: author diversity decay

param.rs: AuthorDiversity enabled, decay 0.5, floor 0.25. Repeated posts from one author in a window are decayed toward the floor. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: mutual-follow reply boost

param.rs: BidirectionalFollowReplyWeightBoost 15.0. Replies inside conversations where both sides follow each other get this boost. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: cold start for new posts

param.rs: EnableViewerColdStart true. Posts under ColdStartImpressionThreshold (1000 impressions) are lifted toward slots 15 to 16. Only posts under 24 hours old qualify (ColdStartMaxPostAgeSecs 86400). Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: diversity re-ranking

param.rs: EnableVMRanker true, DPP theta 0.65. After scoring, a determinantal-point-process ranker re-ranks for diversity. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: only Home Timeline actions count

param.rs code comments: for an account to count in the recommendation system, the action must take place on a post served in the Home Timeline. Directly navigating to a post, e.g. coordinated via groupchat, has no ranking impact. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## VERIFIED: long dwell matters in retrieval aggregation

param.rs: PhoenixAggregationType "DENSE_WITH_LONG_DWELL". Retrieval aggregation weights long dwell. Source: https://github.com/xai-org/x-algorithm/blob/main/home-mixer/params/param.rs

## REPORTED: pipeline shape and visibility filtering

The community explainer at https://github.com/mihhhir08/x-algorithm-explained (cross-checked against the official repo's file layout) describes a seven-stage Post Pipeline: sourcing, candidate generation, feature hydration, 17 pre-scoring filters, Phoenix scoring, heuristic post-scoring, visibility filtering, and serving. Ranking and visibility filtering are separate systems; visibility outcomes are ALLOW, INTERSTITIAL, or DROP, and labels that feed those rules accrue continuously in the background. The explainer names AgeFilter as dropping posts older than 48 hours. This is a secondary source, not official documentation, so it is REPORTED, not VERIFIED.

## REPORTED: Phoenix is a Grok-based transformer

Daniel An's paper "An Overview of the Phoenix Recommendation System" (verified against repo commit aaa167b, January 2026): Phoenix is a Grok-based transformer that models roughly 19 engagement signals with candidate isolation, meaning candidates are scored independently rather than ranked against each other. https://zenodo.org/records/18318223/files/phoenix_paper_FINAL.pdf

## REPORTED: what the August 2026 release added

MediaNama, August 2026: the August 13 release added config parameters, explicit ranking weights, and visibility-filtering code, alongside an "Under the Hood" transparency pilot explaining individual post outcomes. https://www.medianama.com/2026/08/223-x-open-sources-algorithm-post-reach/

## REPORTED: May 2026 update added content understanding

opentweet.io: the May 15, 2026 update touched 187 files and added Grox, a content-understanding system for classifying post content. Secondary source; treated as REPORTED. https://opentweet.io/blog/x-algorithm-open-source-github-2026

## REPORTED: researchers on the probability shift

Engadget, August 2026, quoting researchers including Ruggero Lazzaroni (University of Graz): the current code is a genuine shift from raw engagement counts to predicted-probability scoring, but training data and model behavior remain opaque, which limits what the open weights can actually explain. https://www.engadget.com/social-media/xs-open-source-algorithm-isnt-a-win-for-transparency-researchers-say-181836233.html

## SPECULATION: not used in this repo

- "One report cancels N likes" and every other count equivalence. Explicitly rejected by X's own code comments.
- Exact "reply quality is scored 0 to 3." Not found in the published code.
- "Video earns its weight only above a minimum duration." Not found in the published code. (Current code: video open 0.07, video quality view 0.0.)
- "Grok compares post text to attached media." Not verified in the published code.
- Optimal posting times, "first 30 minutes" velocity windows, reply-within-the-hour rules, daily comment quotas. No verified basis in the published code.
- Hashtag rules, link-placement rules, native-media preference as ranker mechanics. No verified basis in the published code.
- Bookmark as an explicit scoring signal. No bookmark weight appears in the published scoring params. wes's own data shows demos earn bookmarks; that is an audience observation, not a ranker claim.

## Older history, superseded

The 2023-era twitter/the-algorithm repository is the older system and is not used for any claim here. The current primary source is the xai-org/x-algorithm repository.

## Content sourcing rules (2026-09-16)

Drafts are distillations of wes's published work. The rules:

- Usable sources: https://www.practicalsystems.io/blog (primary) and https://github.com/ucsandman repos, READMEs, releases (secondary, for shipped facts).
- Every factual claim in a draft must appear in the cited source. Never embellish, round up, or merge two stories into one.
- Material from memory files, conversation, or the wes-voice stories file is not usable until published at one of the two sources above. The stories file is a voice reference, not a source.
- Every thread cites its source URL at the end, on its own line.

## The 2026-09-16 fabrication incident

The v2 drafts used specific numbers (for example "$227.72 in 8 days, 16,561 compression calls, 732 session summaries") presented as things that happened to wes. Those figures exist in the wes-voice stories file as sourced true stories, but they appear in no published source this repo can cite, so per the rules above they are excluded until published. The one v2 number that is published is $27.72: the model cost of the Packomania run, from https://www.practicalsystems.io/blog/ai-agent-broke-10-math-records-overnight-for-28-dollars. Note how close $27.72 and $227.72 look on a screen. That is exactly why the sourcing rules exist.
