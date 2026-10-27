---
name: tee-up
description: Present a decision as a fully self-contained world the user can settle on taste alone — the situation grounded, each option given by what they'd notice from outside and what could surprise them, closing with a plain-language tradeoff and an honest lean. Written in lay English, assuming zero loaded context. Use for a single pending decision or fork ("what should I do here", "give me the call", "lay out the options", "set the stage", "make this a decision I can just make"), and for several accumulated decisions served strictly one at a time, easy wins first and the hardest last ("tee up the decisions", "one question at a time", "serve the open threads", "don't overwhelm me", "silver platter", "walk me through the choices"), or when another skill (closeout, audit-planes) needs its surfaced loose ends presented for taste input.
license: MIT
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

**One unresolved user choice at a time, not one procedural operation per conversational turn.** The request to serve several decisions stays active across replies. The agent owns the work between user decisions; a user need not request the next item or confirm that a resolved item is resolved.

### Agent turn — prepare and present the first real choice

Take the thread list from `closeout`, `audit-planes`, an explicit list, or the current conversation. For each item identify the decision, real options, tradeoff, lean, what it unblocks, reversibility, and cost-to-clear. Reuse an `advisory` verdict's default, challenger, and flip condition where available.

Resolve research and factual gaps yourself. Apply existing user preferences and authorization; remove questions they already answer. Order the remaining genuine choices easy-first, hardest-last, subject to dependencies (see [references/ordering.md](references/ordering.md)). Present the first unresolved choice in the complete situation/options/tradeoff/lean shape. Yield only because the user has a real preference left to supply.

### User turn — choose, clarify, correct, or redirect

Read the whole reply for what it settles or changes. A choice can be expressed through a constraint or correction rather than an option label. A question may leave the choice open, or its answer may establish that the apparent fork has no remaining preference dimension. A request to stop or change scope governs the sequence.

### Agent turn — answer, incorporate, and advance in one response

Answer any direct question first. Incorporate the user's choice or constraint, do any already-authorized work needed to apply it (or retain it as a decision when this is discussion only), update affected items, and re-rank the remainder. **All of that belongs to this agent turn, including the complete next unresolved choice.** Acknowledgment, explanation, execution, and re-ranking are parts of the turn, not separate occasions to wait for another user message.

If the reply or your answer resolves the current fork under the user's existing constraints, state the consequence briefly and present the next genuine choice in the same response. Do not insert a confirmation round or wait for the user to say "that's solved" or "next." Your own lean alone does not settle an unresolved preference: when a real choice remains, answer the question and keep that choice open rather than moving past it.

End the response at one of these boundaries:

- **A genuine user decision remains:** present that one complete choice, then wait. It may be the current choice after clarification or the next choice after resolution. Keep the rest of the queue private beyond an optional count; a brief disposition of the resolved item plus one new choice is not stacking.
- **No decisions remain:** give one compact account of the outcomes and what they set in motion. Do not manufacture another fork to sustain the sequence.
- **An actual blocker or user-directed stop prevents continuation:** identify it directly; retain the remaining work without asking for generic permission to continue.

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
