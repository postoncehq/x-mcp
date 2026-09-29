---
name: x-content-calendar
description: Plan 1–4 weeks of X (Twitter) posts from the user's goals and content pillars, or by repurposing a blog URL, video or transcript, draft every tweet, and schedule them with the PostOnce X MCP. Use when the user asks for an X or Twitter content calendar, a tweet schedule, tweet ideas for the week, or to turn one piece of content into a month of tweets.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# X (Twitter) content calendar

Plan a run of tweets, write every one, and schedule them once the user approves.

## Inputs to get first

- The X account and its voice (a few past tweets help).
- The goal: followers in a niche, clicks to a product, launch awareness, hiring.
- 2–4 content pillars (topics the account owns), or a source to repurpose: a blog URL, video, transcript, newsletter or notes.
- How many weeks (1–4), how many posts per week, the timezone, and preferred posting times.
- Whether the account had X Premium when it was connected (sets the 280 or 4,000 limit).

## Build the plan

- Pick a cadence the user can keep. Consistency matters more than volume; 3–7 posts a week is a realistic range for most accounts.
- Rotate formats across the week so the feed doesn't repeat itself:

| Format | What it is |
| --- | --- |
| Insight | One opinion or lesson, stated plainly |
| Proof | A result, screenshot or before/after |
| List | 3–5 short points |
| Story | A specific moment and what it taught |
| Resource | A link to the user's own post, video or product, with the reason to click |
| Thread lead | A post that could open a thread (see `x-thread-generator` for how to ship it) |

- Repurposing: pull 5–10 distinct ideas from the source, one per tweet. Each tweet must stand alone; don't write "part 2".
- Keep links to about one post in four.
- Vary posting times a little if the user has no data; weekday mornings and lunchtimes in the audience's timezone are common starting points.

## Write every slot

Draft each tweet with the `x-tweet-generator` rules: line 1 carries it, one idea, 0–1 hashtags, within the limit (count emoji as 2). Text over the limit is cut off at publish. Note any media each slot needs: up to 4 images, or 1 GIF (by public URL), or 1 video (up to 2 minutes without Premium).

This server can't publish threads, replies, quote posts or polls, so don't put those in the calendar as scheduled items. A thread slot becomes a lead post plus a note for the user to add replies by hand.

## Output

Return a table: date, time (with timezone), format, the full tweet, character count, media needed. Then ask for approval. On approval, for each slot call `create_post` with the X account and `publish_at`, or `create_draft` if the user wants to review in PostOnce first. Upload media with `create_upload_url` before scheduling slots that need it. Report each scheduled post's ID and time, and follow the `postonce` skill for confirming account and times before any call.
