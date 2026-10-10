# Anti-patterns

Each is a wrong→right pair with the single feature that flips it. Drawn from real failure modes this skill exists to prevent.

### Boxing a complex choice into a widget
❌ Wrong:    Fire `AskUserQuestion` with four canned options for a nuanced fork.
✅ Right:    Write the fork in prose — options, one-line tradeoffs, your lean — and let the user answer in their own words.
Why it flips: a fixed-option widget forces a rich decision through a narrow slot and reads as patronizing for anything non-trivial; prose lets the user pick, hedge, amend, or reject the frame.
Prevents:    the single most-hated interaction — a complex judgment reduced to multiple-choice. This skill never uses `AskUserQuestion`.

### Queue-dumping
❌ Wrong:    "Open items: (1) dedup the folders, (2) fix config refs, (3) decide familiars. After these, next is the capture build…"
✅ Right:    Present decision 1 only. Say nothing about 2+ beyond a bare "1 of 4". After the pick, reveal the next.
Why it flips: a visible queue forces the user to hold and manage state; one-at-a-time offloads it. The whole point is *not* seeing the pile.
Prevents:    overwhelm — the reason the user reached for this skill.

### One operation mistaken for one conversational turn
❌ Wrong:    User picks an option. Agent replies "Confirmed" and stops; execution, re-ranking, and presenting the next choice each wait for another prompt.
✅ Right:    In the same agent turn, incorporate the choice, perform any authorized follow-through, re-rank, and present the next complete unresolved choice. If none remain, close the sequence.
Why it flips: the human boundary is a genuine decision, not each node in the agent's procedure; the whole response between decisions belongs to the agent.

### Requiring confirmation after the fork has dissolved
❌ Wrong:    User asks whether partial results offer any benefit for their stated workflow. Agent determines there is no remaining reason to require them, recommends one finished result, and waits for "okay, that's solved" before advancing.
✅ Right:    "For your workflow, use one finished result with progress visible. [Present the next genuine choice in full.]"
Why it flips: the answer has already resolved the apparent fork under the user's constraints. Asking whether it is resolved adds no information and forces the user to operate the sequence.

### Treating a recommendation as the user's decision
❌ Wrong:    User asks why the agent prefers one option. Agent explains its preference and immediately moves on even though both options still express different user priorities.
✅ Right:    Explain the preference and keep the current choice open when the user's constraints do not resolve it.
Why it flips: advancing automatically after resolution does not authorize inventing assent; a real unresolved preference still belongs to the user.

### Non-self-contained question
❌ Wrong:    "So — keep or delete the duplicate folder?"
✅ Right:    "Two folders hold byte-identical files: `claude.ai/` (cleaner name) and `claude.ai-export-pipeline/` (has a description file). Keep one, delete the other — which?"
Why it flips: the right version embeds every fact needed to decide *in the prompt*; the wrong one requires reconstructing context from earlier messages.
Prevents:    forcing the user back through scrollback to answer.

### Options without a grounded situation
❌ Wrong:    "Option A: bounded slice of the typed-metadata issue. Option B: the login bundle issue. I lean A."
✅ Right:    "You need a first PR that gets reviewed by the people whose trust matters. Reviews route by subsystem, and the reliability lane is where two of the three actually read code. Given that: [options]."
Why it flips: the right version establishes when and why the question bites before offering answers; without it the options are a quiz on reasoning the user never saw.
Prevents:    the user having to reverse-engineer the stakes to evaluate the choice.

### Internals tour instead of lived consequence
❌ Wrong:    "Option A refactors the error DTO and threads typed cause objects through the gateway boundary."
✅ Right:    "Option A means a failed model call can finally say *why* it failed instead of a generic string — so the UI can tell a billing problem from an outage. New risk: every layer that reads errors has to be updated, and one missed reader silently degrades."
Why it flips: the right version gives what you'd notice from outside plus what could surprise you later; mechanism appears only where it changes the consequence.
Prevents:    a decision presented as an architecture lecture, which the user cannot weigh on taste.

### Carried-over shorthand
❌ Wrong:    "This is the H2 lane, so it favors the co-primary over the entry move."
✅ Right:    "This favors starting where the reliability work lives — the typed-errors issue — over the faster-looking login one."
Why it flips: the wrong version uses labels coined during the investigation; the user was not present for their coinage and would have to look them up.
Prevents:    private vocabulary leaking into a prompt that must stand alone.

### Patronizing scaffolding
❌ Wrong:    "Should I keep the cleaner-named one? **Yes or no.**"  /  "…delete the duplicate (a duplicate is an identical copy)…"
✅ Right:    "Keep `claude.ai/` or `claude.ai-export-pipeline/`? I lean `claude.ai/` — cleaner name."
Why it flips: the wrong version tacks on a decision-format instruction and defines a word the user obviously knows — presuming incapacity. The right one states the choice and the lean, then stops.
Prevents:    reading as condescension; eroding the user's trust that they're treated as competent.

### Handing labor instead of taste
❌ Wrong:    "Should we dedup? If so which do we keep, and where should it live, and want me to first check they're actually identical?"
✅ Right:    (First: verify identical, determine canonical name, confirm where archives live.) Then: "They're identical; I'd keep `claude.ai/` and move it under `recollection/`. Keep-and-move, or delete both since it's a dead export?"
Why it flips: the wrong version outsources the groundskeeping to the user; the right one does that work and presents only the residual preference.
Prevents:    the "teed-up" promise collapsing into a research assignment.

### Wall-of-text context
❌ Wrong:    Five paragraphs of history and mechanism, then the question buried at the bottom.
✅ Right:    Options + one-line tradeoff each + lean. Offer the deep detail *if asked*.
Why it flips: compressed context still fully specifies the choice; the wall re-creates the overwhelm the skill removes (Hick's Law / progressive disclosure).
Prevents:    the user skimming, missing the ask, disengaging.

### Ordering by arrival, not by design
❌ Wrong:    Present decisions in the order they happened to come up during the session.
✅ Right:    Order deliberately — easiest-to-clear first (Fisher-information breaking ties among easy items), re-ranked after each answer.
Why it flips: arrival order is noise; the deliberate order front-loads quick decluttering wins and shapes the sequence toward the intended finish.
Prevents:    spending early focus on whatever surfaced first instead of what clears the deck fastest.

### Ending on trivia instead of the hard thing
❌ Wrong:    Save a quick low-stakes pick for last so the run "ends easy"; scatter the hard decision somewhere in the middle.
✅ Right:    Defer the single hardest, highest-stakes decision to the end; clear all the easy ones before it so it gets a cleared mind and full attention.
Why it flips: the user wants to *converge on* one hard thing with undivided focus, not trail off on filler. The finale is the point, not an afterthought.
Prevents:    spending peak attention mid-run and meeting the weightiest choice while still cluttered.

### Importance ≠ information
❌ Wrong:    Treat "big topic" as "serve early" — rank by subject gravity.
✅ Right:    Weight by ease first; use information (how much the answer *changes* the remaining state) as the secondary tiebreak. A weighty but 90%-settled thread is neither easy-urgent nor informative.
Why it flips: information is a property of the answer's *effect*, not the subject's importance; conflating them corrupts both weights.
Prevents:    the ordering degenerating into priority-by-topic.

### Static list vs adaptive re-rank
❌ Wrong:    Compute the order once, then march down it regardless of what answers reveal.
✅ Right:    After each pick, drop threads it dissolved, re-score the rest for ease and information, serve the new top.
Why it flips: answers routinely merge, moot, or reframe later threads; a fixed list serves stale or pointless questions. Re-ranking is the adaptive-testing move that makes the ordering real.
Prevents:    presenting a decision the previous answer already made — or one whose framing just changed.
