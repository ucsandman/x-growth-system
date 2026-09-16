# I turned my AI company back on after 8 weeks

Source: https://www.practicalsystems.io/blog/we-turned-our-ai-company-back-on-after-8-weeks (read in full 2026-09-16). wes reviews, edits, posts. Nothing here is scheduled or published.

## Post 1

I shut down my autonomous AI systems for 8 weeks. When I turned them back on it took a full day of debugging. First punchline: every hosting service was on a free tier, so the shutdown saved me exactly $0.

## Post 2

The website told visitors the dashboard was running right now. Both production services were suspended. My Stripe API key had expired 194 days before restart. The $49 report product was archived in Stripe. The $299/month "Start Free Trial" button was secretly a mailto link to me. I was not selling software. I was selling an email address.

## Post 3

The dashboard login was broken in four stacked ways, each one hiding behind the last: missing env vars, wrong auth instance, a missing Python crypto package, a missing email claim. The CEO agent picked a product I had already built in June, because nobody told it the company had moved on. Three cycle records showed "running" for 55+ days. Nothing in the system reaps dead runs.

## Post 4

Nothing that broke was a model problem. Expired keys, uncommitted fixes, stale status flags, a website that lied. Dormancy is code drift, not model rust. And a status page that cannot verify what it is displaying is not a status page. It is a press release. Total compute for the whole restart: $2.34.

https://www.practicalsystems.io/blog/we-turned-our-ai-company-back-on-after-8-weeks
