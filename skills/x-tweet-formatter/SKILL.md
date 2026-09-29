---
name: x-tweet-formatter
description: Format X (Twitter) posts for readability: line breaks, lists, Unicode bold and italic (with their accessibility and search costs), and splitting text that's over the tweet character limit before publishing with the PostOnce X MCP. Use when the user asks for a tweet formatter, to add line breaks or bold text to a tweet, or to shorten or split a tweet that's too long.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# X (Twitter) tweet formatter

Take tweet text the user already has and make it read well on X without changing what it says. Then check it fits.

## Line breaks and lists

- Line breaks survive publishing. Use them to separate the hook from the body and to give each point its own line.
- One blank line between blocks. Don't double-space every line of a short tweet.
- Lists: one item per line with a simple marker (`-`, `→`, or `1.`). Keep markers consistent.
- Keep the hook on line 1 by itself when the tweet has more than two lines.

## Unicode bold and italic

X has no native bold or italic in regular posts. "Bold" text is made of Unicode math letters (𝗯𝗼𝗹𝗱, 𝘪𝘵𝘢𝘭𝘪𝘤). Tell the user the costs before using them:

- Screen readers often read these characters letter by letter or as symbol names, so people using them can't follow the text.
- Search, including X search, usually doesn't match them to normal letters, so those words don't help the tweet get found.
- Each styled letter may count as 2 characters against the limit.

If the user still wants it, style 1–3 words at most, never a whole sentence, never hashtags or names. Offer caps or a line break for emphasis instead.

## Counting and the limit

The limit is 280 characters, or 4,000 if the account had X Premium when it was connected to PostOnce. Text over the limit is cut off at publish, not rejected, so the ending is lost silently. When counting:

- Count emoji, CJK characters and Unicode-styled letters as 2.
- Count every character of a link to be safe, even though X shortens links.

## Splitting over-limit text

When the text is over the limit, offer the choices in this order:

1. **Tighten.** Cut filler words, repeated ideas and throat-clearing openers. Show what was removed.
2. **Split into standalone tweets.** Each one must make sense alone; schedule them separately.
3. **Thread.** Use `x-thread-generator`. The MCP can't publish reply chains, so that skill explains the ways to ship it.
4. **Long post.** Only for X Premium accounts, up to 4,000.

Never split mid-sentence or mid-list, and never add "(1/2)" to text that will be posted as separate standalone tweets.

## Output

Return the formatted tweet exactly as it will appear, its character count, and a one-line note on what changed. If it was split, number the parts with their counts. Offer to publish or schedule with the `postonce` skill; confirm the account and time before `create_post`.
