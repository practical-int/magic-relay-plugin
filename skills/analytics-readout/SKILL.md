---
name: analytics-readout
description: Tell the person how their social posts and accounts are doing with Magic Relay. Use for questions like "how did my post do", "how are my accounts doing", or a review of recent results.
---

# Reading out analytics

- **An account:** `get_analytics`, with `account_id` for one account or none for all. Where the app shows Magic Relay's card, it draws the numbers, so add what they mean rather than repeating them.
- **One post:** `get_analytics` with `post_id` from `get_posts` or `create_post`.
- **A review of recent posts:** `get_posts` for the account, then `get_analytics` for the few that matter. Say which ones you looked at.

## Stay honest with the numbers

- Report only what the result contains. Each platform gives different metrics, and some are missing or cover only a recent period, so say so rather than filling a gap.
- Never add or compare one platform's numbers with another's unless the metric plainly means the same thing. Say which platform each number came from.
- Compare only numbers you actually read in this conversation. Magic Relay doesn't return an average or a past period, so don't claim a post beat "your usual" unless you read the posts you're comparing it with, and name how many.
- A new post may read zero because no one has seen it yet. Say how long it has been out, and when it's worth checking again.
- Say when the numbers are from, using `captured_at`.

## Keep reads few

Each `get_analytics` call reads the platform. X reads are billed and count against a monthly budget, and once it's used up X reads fail until the next month. Read what the question needs, and ask before reading many X posts.

## How to answer

Lead with one or two findings in plain words, then the numbers behind them. End with one thing to try next, based on what you read or the person's saved profile, and be clear when it's only a suggestion from a few posts.
