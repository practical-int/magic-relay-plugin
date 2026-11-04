---
name: publish-flow
description: Draft, review, schedule, publish and confirm social posts with Magic Relay. Use whenever a post is going to be written, changed, scheduled, published or deleted on the person's accounts.
---

# Publishing

1. **Pick the accounts** with `list_accounts`. Note each account's limits and `required_post_options`, such as TikTok's privacy or YouTube's visibility. Ask for any required choice rather than choosing for them.
2. **Write it** with the brand-voice skill. Use `text_overrides` when accounts need different text.
3. **Add media** with `add_media` when there is any, and use the `media_id` it returns. Give photos alt text.
4. **Check it** with `check_post`. Fix what it reports, or tell the person what it found. Nothing is posted by this step.
5. **Save a draft** with `create_post` and `action: "draft"`. Where the app shows Magic Relay's card, the person sees the post with its time field, **Schedule** and **Post now**. Elsewhere, show them the exact text for each account.
6. **Get their OK on the exact text** before it goes out, and again if the text changes. Someone who gave you the exact text and told you to publish it has already given that OK.
7. **Schedule or publish** with `update_post`, using `action: "schedule"` with `scheduled_at`, or `action: "publish"`. Give `scheduled_at` a UTC offset; without one it's read in the brandspace's timezone. Say the time back in the person's words.
8. **Confirm** with `get_post`: report each account's status and link, not just that the call returned. Report any account that failed with the reason given, and offer to try again.

Use a fresh `idempotency_key` for each new action. To retry the same action after an unclear result, send the same key, so it can't happen twice.

## Good to know

- One account can fail while others succeed, so read every account's result.
- A status of `sent` means the platform has the post but it isn't live yet.
- Moving a scheduled post back with `action: "draft"`, or **Move back to drafts** on the card, stops it going out.
- Editing a published post works only where the account's capabilities allow it. Where they don't, pass on the reason given, which usually offers another way.
- `delete_post` on a published post removes it from the platform for good, so confirm first.
- Don't claim a time is the person's "best time" unless you've worked it out from numbers you read, and say what you based it on.
- If a refusal mentions the person's plan, tell them plans are handled on the Magic Relay website. Never offer to take payment in the conversation.
