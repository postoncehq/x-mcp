---
name: x-thread-generator
description: Turn a topic, blog URL or transcript into a 5–15 post X (Twitter) thread, then ship it in a way the PostOnce X MCP supports (lead tweet plus replies to paste, one Premium long post, or standalone tweets over several days). Use when the user asks for a Twitter thread, an X thread, a thread generator, or to turn an article, video or notes into a thread.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# X (Twitter) thread generator

Write a thread that people read to the end. Be clear up front: the PostOnce MCP publishes single posts. It can't publish a thread as a reply chain, so every thread ends with a publishing choice (below).

## Before writing

Get: the source (topic, blog URL, transcript or notes), the account and its voice, who the thread is for, and the one promise the thread makes. If the source is a URL you can read, pull the specific steps, numbers and examples from it. Never invent numbers, results or quotes.

## Structure

| Post | Job |
| --- | --- |
| 1. Hook | The promise and why to keep reading: a result, a list count or a strong claim. Must work alone. |
| 2 | Context or proof: why you're worth listening to on this, in one or two lines. |
| 3 to N-1 | One point per post. Numbered if it's a list. Each post makes sense if read alone. |
| Last | The takeaway in one line, plus one ask: follow, read the full post, or reply. |

- 5–15 posts. Cut any post that repeats another.
- Every post under 280 characters (count emoji as 2). Aim for 150–260.
- Short lines, concrete examples, one screenshot or chart where it proves a point.
- No "1/" filler in the hook; numbering like "1/9" is optional and only if the user likes it.
- Links go in the last post. Hashtags: none, or one in the last post.

## Publishing choices

Offer these, in this order, and let the user pick:

1. **Lead post now, rest by hand.** Publish or schedule post 1 with `create_post`. Give the user the remaining posts, numbered, to paste as replies in the X app right after it goes live. Use `get_post` to hand them the live URL.
2. **One long post (X Premium only).** If the account had X Premium when it was connected, collapse the thread into a single post of up to 4,000 characters: keep the hook as the first lines, turn each post into a short paragraph or list item. Text over 4,000 is cut off, so count it.
3. **Standalone tweets over several days.** Rewrite each strong point so it stands alone without "as I said above", then schedule them as separate posts (for example one a day) with `publish_at`. Good for evergreen material.

Don't tell the user the thread was posted as a thread. It wasn't.

## Output

Return the thread as a numbered list with each post's character count, then the recommended publishing choice and why. On approval, follow the `postonce` skill: confirm the X account and times (with timezone) before calling `create_post`, then report each post's status with `get_post`.
