---
name: x-bio-generator
description: Write an X (Twitter) bio of up to 160 characters, plus a display name and a pinned tweet idea, for the user to paste into their profile. Use when the user asks for a Twitter bio, an X bio, a bio generator, or help with their X profile.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# X (Twitter) bio generator

Write a bio that tells a visitor in one read who this is and why to follow. The PostOnce MCP can't edit profiles; the user pastes the result into X under Edit profile.

## Before writing

Get: who the account is (person, founder, brand), what they post about, who they want to follow them, one proof point (role, company, result, audience), and the link they want in the profile. Paste the current bio if there is one. Never invent credentials, employers, numbers or awards.

## Limits

| Field | Limit |
| --- | --- |
| Bio | 160 characters |
| Display name | 50 characters |
| Location | 30 characters |
| Website | One link, in its own field, so it doesn't need to go in the bio |

Count emoji as 2 characters to be safe.

## What makes a bio work

- Answer "what will I get if I follow?" Topics and angle beat job titles alone.
- One proof point: "Built [X] to [result]", "[Role] at [company]", "Writing about [topic] since [year]".
- Specific nouns over adjectives. "Posts about pricing for SaaS founders" beats "Passionate entrepreneur".
- Separators (`·`, `|`, line breaks) are fine; keep it to 2–3 short parts.
- Mentions of a company handle (`@acme`) link to it; use one if it helps.
- Hashtags and emoji: 0–1 each. They rarely help.

Patterns:
- "[What I do] for [who]. [Proof point]. [What I post about]."
- "[Role] at @[company]. Posting about [topic 1], [topic 2] and [topic 3]."
- "[Result]. Now sharing how I [did it]."

## Display name and pinned tweet

- Display name: the real name, optionally plus a short topic ("Sam Lee | SaaS pricing"). Don't keyword-stuff.
- Pinned tweet: suggest one post that shows the account at its best (a strong thread lead, an intro post or a proof post). If the user wants to publish it, draft it with `x-tweet-generator`. Pinning happens in the X app; the MCP can't pin.

## Output

Give 3 bio options with character counts, one display name suggestion and one pinned tweet idea. Remind the user to paste the bio into X themselves. Offer to publish the pinned tweet through the `postonce` skill (confirm account and time before `create_post`).
