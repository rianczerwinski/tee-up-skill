---
name: tee-up
description: Present a decision as a fully self-contained world the user can settle on taste alone — the situation grounded, each option given by what they'd notice from outside and what could surprise them, closing with a plain-language tradeoff and an honest lean. Written in lay English, assuming zero loaded context. Use for a single pending decision or fork ("what should I do here", "give me the call", "lay out the options", "set the stage", "make this a decision I can just make"), and for several accumulated decisions served strictly one at a time, easy wins first and the hardest last ("tee up the decisions", "one question at a time", "serve the open threads", "don't overwhelm me", "silver platter", "walk me through the choices"), or when another skill (closeout, audit-planes) needs its surfaced loose ends presented for taste input.
---

# tee-up

Tee up a decision: place it so the swing is easy. **One fully-worked choice, self-contained, answerable on taste alone.** The user supplies preference; the skill has already done the labor.

The primitive is a single decision. Serving several is the same move repeated with an ordering discipline (see "Serving several"). Both cases share one distinctive property: **a presented decision is never a request for work.** By the time it reaches the user it is resolved down to a preference fork — the options are real, the tradeoff is named, a lean is stated. If a thread still needs research, verification, or computation to reach that state, do that first. Handing over a half-baked question is the primary failure this skill exists to prevent.

## Hard constraint: plain prose, never AskUserQuestion

**Present every decision as plain conversational text — an inline fork the user answers in their own words. Never use the `AskUserQuestion` tool (or any rigid multiple-choice widget) in this skill.** It boxes a nuanced choice into canned options and reads as patronizing for anything of real complexity — exactly the decisions this skill handles. Write the options as prose; let the user respond with the full nuance of natural language (pick, hedge, amend, reject the frame, ask a question back). This is non-negotiable and load-bearing — a defining property of the skill, not a style preference.

## The shape of one teed-up decision

Three movements, in order:

1. **Ground the situation.** When — or whether — the issue actually bites. What is true right now that makes this a live question. Never open on the options; an option list without a grounded situation is a quiz.
2. **Give each option functionally.** What the user would *notice from the outside* if they took it, and what new failure could *surprise* them later. Not an internals tour: name a component only where it changes the lived consequence.
3. **Close with the meta-tradeoff and an honest lean.** The plain-language shape of what's really being traded, then where you'd land and why — stated as yours. Never neutral fence-sitting.

Bound by five properties:

- **Self-contained.** Every fact needed to decide lives *in this prompt*. Never lean on "the folders we discussed", earlier turns, or shorthand you coined along the way. Name things; state their identifying details inline. Assume the user was not watching you work — because they weren't.
- **Lay English.** Spell out the terms. No jargon carried over from the investigation, no invented labels the user would have to look up, no arrow chains. If a term is genuinely theirs, use it; if it's yours, define it in passing or drop it.
- **Compressed, not a wall.** Situation, options with one-line consequences, lean. Complete but tight — full landscape, no padding. Overwhelm defeats the whole skill.
- **Taste, not labor.** The ask is the swing, never the groundskeeping. If you're asking the user to gather facts or make a call you could have made, you skipped the work step.
- **No scaffolding.** Do not append "Yes or no?", do not explain a term the user plainly knows, do not narrate your process. Treat the user as able to decide.

## Work it to a home run first

Before a decision is ever shown, close every gap *you* can close. Verify the facts, run the check, resolve the dependency, determine the canonical answer. What remains must be only what *this person alone* can supply — their preference. A knowledge gap routed to the user as a preference fork is unfinished work wearing a question mark. If you cannot make it taste-only, say what's blocking and resolve that first.

## Serving several

When decisions have accumulated, the move is the same — repeated with sequencing:

```
intake threads → work each to a home run → order (easy wins first, one hard finale) →
  present the top one → WAIT for pick → execute/park → re-rank remainder → present next → …
```

1. **Intake.** Take the thread list — from `closeout`, `audit-planes`, an explicit list, or the decisions accumulated this session. Normalize each to: the decision, the real options, the tradeoff, current lean, what it unblocks, reversibility, and cost-to-clear. Threads arriving from an `advisory` axis-verdict are already in this form — a `default / runner-up / flip-when` triple maps onto lean / real option / tradeoff; take them as-is rather than re-deriving.
2. **Order: clear the decks, hard thing last.** Strip the easy wins first to declutter mental space, converging on the single hardest decision so it lands last, met with a cleared mind. Ease-weighted, with Fisher-information as secondary weight (full method in [references/ordering.md](references/ordering.md)).
3. **Present exactly one.** Never reveal that others are queued beyond a bare count ("1 of 5"). No "and next…". No stacking.
4. **Wait, then re-rank.** An answer can change, merge, or dissolve later threads, so re-rank the remainder before presenting the next — adaptive, the way computerized adaptive testing re-selects its next item after each response.
5. **Close.** When the list is empty, summarize what was decided and what each decision set in motion — once, compactly.

This is progressive disclosure applied to decision-making (the GOV.UK "one thing per page" pattern, grounded in Hick's Law: fewer simultaneous choices → faster, un-fatigued decisions).

## When NOT to use

- **The answer is inferable.** If context, code, or logs already decide it, decide it and say so — don't manufacture a question (see `elicit`'s "when NOT to interview").
- **It's one coupled decision wearing several hats.** Don't atomize a single choice into fake sub-questions; present it once with its facets.
- **The user wants the map, not the route.** `§equip` asks for a decision landscape *without* collapsing to a recommendation. Tee-up always lands on a lean; if they asked to be equipped, don't steer.

## Anti-patterns

See [antipatterns.md](antipatterns.md) — wrong→right pairs drawn from real failures (using a multiple-choice widget for a complex fork, queue-dumping, non-self-contained questions, patronizing scaffolding, handing labor instead of taste, ordering by arrival, saving easy instead of hard for last), each with the discriminating feature that flips it.

## Additional resources

- [references/ordering.md](references/ordering.md) — the clear-the-decks ordering method and its alternates. Read when serving several.
- [antipatterns.md](antipatterns.md) — the negative-examples core.
- [examples/session-threads.md](examples/session-threads.md) — a worked run: raw thread list → ease-ordered, one-at-a-time platter.
