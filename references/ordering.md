# Ordering: clear the decks, hard thing last

The default order **strips the easy wins first to declutter, converging on the single hardest decision so it lands last** — met with a cleared mind and undivided attention. The sort is ease-weighted, with Fisher-information as the secondary weight, and it is re-computed after every answer.

## The telos (what the order is *for*)

The user's stated preference: clear easy wins to free mental space of what remains, "leaving me at the end with one final hard thing to devote unrestrainedly my entire attention towards." So the sequence is a **burn-down**: each early pick is quick and removes an item, the remaining set shrinks and simplifies, and the ordering deliberately defers the one heavy, high-stakes, needs-real-thought decision to the very end where it gets the whole runway.

This inverts naive max-information-first. Pure information ordering would front-load the pivotal/hard choice; the user explicitly wants the opposite arrival — easy → hard — because the *experience* of deciding matters, not just the theoretical bits-per-question.

## The two weights

Score each open thread on two axes, then order by a blend that **weights ease more heavily** (the user's call; keep the weighting tunable):

- **Cost-to-clear (primary, heavier weight).** How little effort/attention the decision takes the user to settle — a snap preference vs. a choice needing deliberation. Low cost → served early. This is what does the decluttering.
- **Fisher-information (secondary weight).** How much the answer collapses remaining uncertainty and unblocks other threads (see "the analogy" below). Used mainly to *break ties among comparably-easy items* — a quick decision that also moots two others is the ideal opener.

Resulting shape:

- **First:** easy **and** high-information — quick wins that also clear other threads. Maximum declutter per second.
- **Middle:** the remaining easy/moderate items, high-info before low-info.
- **Last:** the hardest single decision — highest cost-to-clear, usually also highest stakes. The finale, alone, with full attention.

Keep it judgment, not arithmetic — you are not computing a real score to three decimals. If the user ever says information matters more than ease for a given batch, flip the weighting and lead with the pivotal one instead.

## The Fisher-information analogy, stated honestly

Proper Fisher information is the expected curvature of a log-likelihood — how sharply an observation pins a parameter. There is no literal likelihood model over "which folder to keep," so this is an **analogy, not a computation** — and the apt one: it is how **computerized adaptive testing (CAT)** and item-response theory pick the next item, administering the one with maximum information given what's already known, then re-estimating. Here it's the secondary weight: among easy items, prefer the more *discriminating* one. Don't oversell it as a metric.

The classic trap: collapsing information into "importance." A weighty but already-90%-decided thread carries little marginal information — its answer barely moves the state — so it does not earn an early slot on information grounds. Information is about what the answer *changes*, not the topic's gravity. See `antipatterns.md` → "Importance ≠ information."

## Adaptive re-ranking (load-bearing)

Ordering is **not a static sort computed once.** After each answer:

1. Apply the answer — some remaining threads are now decided-by-implication, merged, or dissolved. Drop those (and say so in one line).
2. Re-score the survivors — an answer often changes how easy or how informative the rest are.
3. Serve the new easiest/most-decluttering item; keep the hardest deferred toward the end.

This is the adaptive-testing move (re-estimate, re-select after each response). A fixed list is the non-adaptive special case; prefer it only when the threads are truly independent.

## Dependency comes before ease

One hard override: if thread B is **unanswerable until A is decided** (a true prerequisite, not merely correlated), A precedes B regardless of ease. Resolve genuine dependencies in prerequisite order; apply the ease/information blend *within* what's currently answerable. Never present a thread whose framing a pending earlier answer would rewrite — that produces a non-self-contained or soon-stale question.

Note the tension the user should know about: dependency-first can conflict with hard-thing-last (a hard prerequisite may unblock several easy items). When they collide, dependency wins for *correctness*, but flag it — "clearing this hard one first unlocks three quick ones; want it first, or should I hold the easy ones that don't depend on it and still finish on this?" — and let taste settle it.

## Alternate orders (on request)

The user can override the default. Offer these when asked, or when the situation obviously calls for one:

- **Highest-information-first** — the pivotal/hard decision leads (pure Fisher). Good when the user wants the big fork settled while attention is freshest and doesn't care about decluttering.
- **Dependency-topological** — strict prerequisite order, ignoring ease and information.
- **By workframe / theme** — batch decisions about the same subtree together to preserve context. Good when switching contexts is the dominant cost.
- **Reversibility-first** — irreversible decisions first.

State which order is active if it isn't the default, so the user knows the logic behind the sequence.
