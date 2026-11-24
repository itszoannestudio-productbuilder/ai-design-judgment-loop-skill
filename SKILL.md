---
name: ai-design-judgment-loop
description: "Run a lightweight design judgment exercise: capture a first instinct, compare options, eliminate with a reason, and save a useful decision story. Use when the user asks to practice this method or to build its interaction; use ordinary critique unless they opt in."
---

# AI Design Judgment Loop

Help the user practice and show how they make design decisions. Success means they leave with their first instinct preserved, a choice or honest open decision, and a concise record they can use. Finishing three rounds is not required.

## Core rules

1. Ask one easy question at a time; use context the user already gave.
2. Capture the user's first instinct before showing options. One sentence or “I don't know yet” is enough. Treat it as a snapshot they can compare with their later thinking, not an immutable lock. If they have already seen options, note that and don't pretend otherwise.
3. Keep the elimination choice separate from the reason question. In a text chat, say choices are not clickable and ask for letters; use a native multi-select if one is actually available. Never render fake checkboxes.
4. The user decides. AI-generated options and observations are suggestions; don't steer toward a winner or invent the user's reasons.
5. Make the exercise easy to leave: allow skip, pause, edit, and stop. Preserve unanswered items as unknown.
6. Put every question that needs a user response in a fenced plain-text block. Keep explanations and observations outside the block. The block visually separates the prompt; its choices are not clickable unless a real interactive control is provided.

## Short flow

### Start

Begin with the easiest missing context, usually:

```text
What are you designing, and who is it for?
```

Then ask for the first instinct, unless it is already known:

```text
Before looking at options, what's your first instinct?
One rough sentence is enough. “I don't know yet” is fine.
```

Don't front-load a time estimate or a list of rules. Mention that the user can skip or change an answer only when it becomes relevant.

### What matters

Suggest up to three plain-language criteria grounded in the user's stated goal. Make clear they are a starting suggestion, not facts about the user's priorities. Ask the user to choose, edit, or replace them. If the user just says “okay,” ask which one matters most before using the criteria to interpret their choices. If priorities conflict, ask which should lead for this decision. Record later changes briefly so earlier rounds aren't silently rejudged.

Example:

```text
I can think of three things that might matter: whether reading feels smooth, whether the transition is noticeable, and whether it feels natural on mobile.
Which matters most to you? You can change or replace any of them.
```

### Show options

Ask which presentation format would help the user judge the options. Define the choices clearly:

- `Text`: concise written descriptions of each direction.
- `Static mockups`: still images for comparing visual direction; they are not interactive.
- `Interactive prototype`: a clickable or otherwise operable experience for trying the flow or transition. Offer this only when you can actually provide one. If not, say that static mockups are available instead.

Ask in a fenced plain-text block:

```text
How would you like to compare the options?

Text
Static mockups
Interactive prototype

Reply with one choice.
```

Use a real choice control if the host provides one. In text-only chat, request a reply by name; never imply that the listed choices are clickable. If the user has no preference, choose the most useful available format. For visual design, prefer a visual comparison when possible; if only text is available, say briefly that they are judging descriptions rather than visuals.

Use two or three options by default. If the user provides more, preserve their choices and offer to compare them in manageable groups; don't silently discard options to fit the default. Make options meaningfully different, plausible, and comparable. Use the same compact format and order for each:

```text
Option A — name
Direction: ...
Upside: ...
Risk: ...
```

Treat AI-created options as proposals. Avoid straw men and invented performance claims. Reorder options when practical to reduce order bias; don't add a disclaimer every round unless order could reasonably be mistaken for ranking.

### Eliminate and reflect

Ask only the multi-select deletion question first, inside a fenced plain-text block:

```text
Which option(s) would you remove? Reply with the letters, such as A and C.
You can also say “not sure” or “skip.”
```

Keep three user-facing outcomes: eliminated, still considering, or want to change. Distinguish “still considering” from “not sure”; ask a short clarification only when needed. Silence or skip is not a decision.

After the user eliminates, ask one low-effort follow-up for the group, inside its own block:

```text
What's the main reason? A few words are enough, or skip.
```

Offer quick reason choices only if useful, such as “too complex,” “misses the main need,” or “other.” Ask what they noticed or when the option might fit only when it adds value; these are optional. If the user says “I just don't like it,” accept that as their preference and optionally ask once what the dislike relates to. If they don't know, record the reason as unclear—don't invalidate the choice.

If everything is eliminated, pause and ask what was missing from all of them. If they skip, record the gap as unknown and ask whether they'd like another round anyway.

### Compare and close

After each round, give a short progress cue. Offer one observation only when there is enough evidence; phrase it tentatively and invite correction. If a stated priority seems at odds with a choice, neutrally reflect both and ask whether the priority is relevant. For example:

> 你說最在意手機上的清楚度；B 的描述是字比較小。這點有影響你的選擇嗎？

When several options remain, summarize the differences against the user's priorities without selecting for them. Ask whether they want to choose, keep considering, change an option, or pause. Put this question in a fenced plain-text block. An option that survives elimination is not automatically the winner.

If they want to change an option, ask what to change and make a revised version labelled, for example, `B revised`. This is an iteration within the current round unless the user is comparing a newly generated set; count that as a new round. Preserve the earlier version in the record.

After three rounds without a decision, show a two- or three-sentence preview of what the user's path currently says, then offer to save it now or continue. Don't pressure them to finish. Save a short checkpoint at a round boundary or whenever they pause or change direction.

## Privacy and visual material

If the user is about to paste or upload confidential client or workplace material, briefly suggest removing identifying or sensitive details first. Don't interrupt ordinary abstract discussion with a privacy disclaimer. Be accurate about whether the current tool stores or uploads material; if unknown, don't promise local-only handling.

## Thinking record

Use the user's language. Make the export read like a short story of a decision, not an audit form. Keep the user's own words and distinguish them from AI suggestions. Leave unknowns blank or label them as not explored.

Example:

```markdown
# How I made this design decision

My first thought was…

What mattered most to me was… because…

I compared a few directions. I removed… mainly because…
This direction might still work when… (optional)

For now, I chose / am still considering / want to change…
It fits… better, though I accept the trade-off of…

Looking back, my thinking changed from… to…
```

Include only claims the user made or confirmed. If no final choice was made, end with the open question rather than manufacturing closure. Translate headings and the record to the user's language; English headings are not mandatory.

## Optional enhancements

Use these only when they materially help: a visual sketch or mockup, criteria priority ranking, an observation about a repeated pattern, randomized option order, a “when could this rejected idea work?” reflection, or a polished portfolio-ready layout. Keep the core flow above even if optional enhancements are skipped.

## If building the interaction as a product

Use accessible real multi-select controls for elimination, with a separate follow-up for reasons. Support edit/back and visible round history. Keep the same three user-facing outcomes and preserve revisions. Explain storage/upload behavior at the point where users add material.
