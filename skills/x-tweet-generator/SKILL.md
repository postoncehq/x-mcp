---
name: x-tweet-generator
description: Write single X (Twitter) posts in the user's voice, within 280 characters or 4,000 for X Premium accounts, ready to publish with the PostOnce X MCP. Use when the user asks for a tweet, a tweet generator, a Twitter post generator or an X post, or to write, rewrite or turn an update, article, video or idea into a tweet.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# X (Twitter) tweet generator

Write one tweet that earns a stop in the timeline, then hand it to the `postonce` skill if the user wants it published or scheduled.

## Before writing

Get or infer: the account and its voice (paste 3–5 of the user's past tweets if they have them), who they want to reach, the one idea, and any fact, number or example that proves it. From a long source, pick the single sharpest idea. Never invent numbers, results, customers or quotes.

Check the limit. It's 280 characters, or 4,000 if the account had X Premium (blue check) when it was connected to PostOnce. If you don't know, write for 280. Text over the limit is cut off at publish, not rejected, so never hand over a tweet that's over.

## What makes a tweet work

- Line 1 carries the whole tweet. Lead with the claim, the result or the specific moment, not the setup.
- One idea. If there are two, that's two tweets or a thread (`x-thread-generator`).
- Specific beats clever: a number, a name, a before/after, a short list.
- Take a side. Neutral tips read as filler.
- Write like a person talking. Plain words, contractions, no corporate voice.
- Short lines with line breaks help longer tweets scan; see `x-tweet-formatter`.

Openers that tend to work:

| Pattern | Template |
| --- | --- |
| Result first | "[Result] in [time]. Here's what changed:" |
| Contrarian | "[Common advice] is wrong for [who]." |
| Specific moment | "You [did the thing]. It's [later] and [problem]." |
| List | "[N] things I'd do if I started [X] today:" |
| Lesson | "[Mistake] cost me [cost]. The fix was [fix]." |

## Anti-patterns

- Hashtags: 0–1, only if it's a real tag people follow. Never a hashtag wall.
- "Thread 🧵" or "1/" on a single tweet.
- Opening with "We're excited to announce", "Just a reminder" or a vague question.
- "Game-changer", "unlock", "let's dive in", emoji bullet walls.
- Tagging accounts only to borrow reach.

## Premium long posts

For a 4,000-character account, only go long when the idea needs it. The timeline shows the start and hides the rest behind "Show more", so the first 280 characters still have to stand alone.

## Media

Suggest one visual when it helps: a screenshot, chart or short clip. X takes up to 4 images (JPEG, PNG or WEBP, 5 MB each), or 1 GIF (up to 15 MB), or 1 video (MP4, up to 512 MB; up to 2 minutes unless the account has Premium). Don't mix types. GIFs can't go through `create_upload_url`; pass a public GIF URL instead.

## Output

Give 2–3 versions with different openers, each with its character count, and mark the one you'd post. Offer to publish or schedule it with the `postonce` skill; confirm the X account and the time (with timezone) before calling `create_post`.
