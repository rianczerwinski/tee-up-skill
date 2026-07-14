---
name: tee-up
description: Serve accumulated open threads or pending decisions to the user one at a time — each a fully self-contained, teed-up choice (options, the tradeoff, and a recommended lean) that asks for taste, not labor. Presents strictly one decision at a time in plain prose, waits for the pick, then reveals the next; never stacks questions, never dumps a queue, never uses a rigid multiple-choice widget. Default order clears the easy wins first and saves the single hardest decision for last (an ease-weighted blend of cost-to-clear and Fisher-information), re-ranked after each answer. Use when several pending decisions, loose ends, or forks need resolving and the user wants them served one-at-a-time without being overwhelmed — "tee up the decisions", "one question at a time", "serve the open threads", "don't overwhelm me", "give me the choices on a silver platter", "walk me through the pending choices" — or when another skill (e.g. closeout, audit-planes) needs to present its surfaced loose ends for taste input.
---

# tee-up

Serialize a pile of pending decisions into a silver-platter interview: **one fully-worked choice at a time, easy wins first, waiting for each pick before the next appears.** The user supplies taste; the skill has already done the labor. This is the opposite of a status dump — it is progressive disclosure applied to decision-making (the GOV.UK "one thing per page" pattern, grounded in Hick's Law: fewer simultaneous choices → faster, un-fatigued decisions).

The distinctive move: **a presented decision is never a request for work.** By the time it reaches the user it is resolved down to a preference fork — the options are real, the tradeoff is named, a lean is stated. If a thread still needs research, verification, or computation to reach that state, do that first (see "Work it to a home run"). Handing over a half-baked question is the primary failure this skill exists to prevent.

## Hard constraint: plain prose, never AskUserQuestion

**Present every decision as plain conversational text — an inline fork the user answers in their own words. Never use the `AskUserQuestion` tool (or any rigid multiple-choice widget) in this skill.** It boxes a nuanced choice into canned options and reads as patronizing for anything of real complexity — exactly the decisions this skill handles. Write the options as prose; let the user respond with the full nuance of natural language (pick, hedge, amend, reject the frame, ask a question back). This is non-negotiable and load-bearing — it is a defining property of the skill, not a style preference.

## When to use

- Multiple pending decisions / loose ends / forks have accumulated and need the user's preference.
- Another skill (closeout, audit-planes, documentation) has surfaced a list of open items and needs them presented for taste input.
- The user says any of: "tee up the decisions", "one at a time", "serve the open threads", "don't overwhelm me", "silver platter", "walk me through the choices".

## When NOT to use

- **One decision only.** Present it directly — serializing a single item is theater. Use `elicit`'s fork directly.
- **The answer is inferable.** If context, code, or logs already decide it, decide it and log the choice — don't manufacture a question (see `elicit`'s "when NOT to interview").
- **It's genuinely one coupled decision wearing several hats.** Don't atomize a single choice into fake sub-questions; present it once with its facets.

## The loop

```
intake threads → work each to a home run → order (easy wins first, one hard finale) →
  present the top one in prose (self-contained, one only) → WAIT for pick →
  execute/park that choice → re-rank the remainder → present next → …
```

1. **Intake.** Take the thread list — from `closeout`, `audit-planes`, an explicit list, or the decisions accumulated this session. Normalize each to: the decision, the real options, the tradeoff, current lean, what it unblocks, how reversible it is, and how hard it is to clear.
2. **Work it to a home run.** For each thread, close every gap *you* can close before it is ever shown. Verify the facts, run the check, resolve the dependency, determine the canonical answer. What remains presented must be only what *this person alone* can supply — their preference. If you cannot make it taste-only, say what's blocking and resolve that first.
3. **Order: clear the decks, hard thing last.** Default order strips the easy wins first to declutter mental space, converging on the single hardest decision so it lands last — to be met with a cleared mind and undivided attention. The sort is ease-weighted, with Fisher-information as the secondary weight (full method in [references/ordering.md](references/ordering.md)).
4. **Present exactly one, in prose.** Write a single decision as a self-contained inline fork (see below). Never reveal that others are queued beyond a bare count (e.g. "1 of 5"). No "and next…". No stacking. No `AskUserQuestion`.
5. **Wait, then re-rank.** After the pick, execute or park that decision. Because an answer can change, merge, or dissolve later threads, **re-rank the remainder** before presenting the next — adaptive, the way computerized adaptive testing re-selects its next item after each response. Then serve the new top.
6. **Close.** When the list is empty, summarize what was decided and what each decision set in motion — once, compactly.

## Presenting one decision (the platter)

Compose `elicit` — fork-based, strawman-first — but bound tighter, and always in plain text:

- **Self-contained.** Every fact needed to decide lives *in this prompt*. Never lean on "the folders we discussed" or session memory. Name the things; state their identifying details inline.
- **Compressed, not a wall.** Options + a one-line tradeoff each + your lean. Not five paragraphs of preamble. Overwhelm here defeats the whole skill.
- **Lean stated as yours.** Recommend, and say it's your recommendation — don't hide the steer, don't pretend neutrality.
- **Prose, open response.** Lay the options out as text and stop. Let the user answer however they like. Do not force a widget; do not append "Yes or no?"; do not explain a term unless asked; do not narrate the process. Treat the user as able to decide.
- **Taste, not labor.** The ask is the swing, never the groundskeeping. If you're asking the user to gather facts or make a call you could have made, you skipped step 2.

## Ordering

Default is the **clear-the-decks** order: easiest-to-clear first, hardest single decision last, re-ranked adaptively after each answer. The full method — the ease/Fisher-information blend and its honest scope, the one-hard-finale rationale, dependency overrides, and the alternate orders the user can request — is in [references/ordering.md](references/ordering.md).

## Anti-patterns

See [antipatterns.md](antipatterns.md) — wrong→right pairs drawn from real failures (using a multiple-choice widget for a complex fork, queue-dumping, non-self-contained questions, patronizing scaffolding, handing labor instead of taste, ordering by arrival, saving easy instead of hard for last), each with the discriminating feature that flips it.

## Additional resources

- [references/ordering.md](references/ordering.md) — the clear-the-decks ordering method and its alternates.
- [antipatterns.md](antipatterns.md) — the negative-examples core.
- [examples/session-threads.md](examples/session-threads.md) — a worked run: raw thread list → ease-ordered, one-at-a-time platter.
