# Example: raw thread list → clear-the-decks, one-at-a-time platter

A worked run showing intake, working-to-home-run, ease-weighted ordering (easy wins first, one hard finale), and single-item **plain-prose** presentation. No widget is used anywhere.

## Input: accumulated open threads (unworked, as they surfaced)

```
- claude.ai dedup: two identical folders, keep one?
- fix stale config refs (.claude/rules/adrs.md etc. point at old path)
- familiars/ fate: vestigial folder, keep/fold/retire?
- habits/ seeding: folder is thin, add docs?
- build claude.ai Project-doc capture in Octopus? (feasibility just confirmed)
```

## Step: work each to a home run (labor done BEFORE any question)

- **config refs** → exact edits known (`jarvis/decisions/` → `axis/psyche/superego/decisions/`), 3 files, user already leaned yes. Residual = a quick go-ahead. *Easiest.*
- **habits seeding** → two candidate docs identified. Residual = whether to bother now. Easy, low stakes, unblocks nothing.
- **familiars** → confirmed the live agent loads from `.claude/agents/`, so the folder is a non-loaded copy. Residual = keep-as-design-home vs fold vs retire. Easy-moderate, self-contained.
- **dedup** → verified byte-identical; canonical name `claude.ai/`; archives live in `recollection/`. **But mooted by the capture decision** — if capture gets built, both export folders retire regardless of which you'd keep.
- **Project capture** → feasibility proven; a real build (hours), high stakes. The taste-question is a go/no-go on the plan — legit preference — but it's the *hard* one. *Hardest.*

## Step: order — clear the decks, hard thing last

1. **config refs** — easiest, near-settled, quick win. Clears an item in one word.
2. **habits seeding** — easy, optional.
3. **familiars fate** — easy-moderate, self-contained.
4. **Project capture (finale)** — hardest, highest-stakes. Deferred to last for full attention.
   - **dedup is folded in as a rider on the finale, not served early.** It's dominated by capture: serving it first would risk asking a question capture's answer erases (the "static list serves a soon-mooted question" trap). So capture's outcome resolves it — see re-rank.

*Note the tension (per `references/ordering.md`): dedup depends on capture, and capture is the hard finale. Rather than pull the hard one early (which dependency-first would do), the mooted item rides on the finale's answer. Flag-and-let-taste-settle would also be valid; here dominance makes the rider clean.*

## Step: present ONE — plain prose, item 1 of 4

> **Fix the stale config references?** Three files (`​.claude/rules/adrs.md` and two agent files) still point ADR placement at the old `jarvis/decisions/` path; the ADRs now live at `axis/psyche/superego/decisions/`. It's a mechanical find-replace — the misdirection is the only cost of leaving it.
> I'd just fix all three. Any reason to hold off?

*(Then stop. Nothing about items 2–4 beyond "1 of 4". Wait for the answer in whatever form it comes.)*

## Step: re-rank after each answer

- Clear config refs → serve **habits seeding**, then **familiars**.
- Reaching the finale, present **capture** as the last decision, with dedup as its rider:

> **Build Claude.ai Project-doc capture into Octopus?** *(the last one — take your time)*
> Feasibility is proven from your existing captures: Projects are bulk-listable and pull with the same poll that grabbed your 5k conversations. A few hours of work.
> — **Build it** → the two manual export folders become redundant and retire themselves; the dedup question disappears with them.
> — **Not now** → I keep one copy (`claude.ai/`, moved under `recollection/`) and delete the duplicate; revisit capture later.
> I lean *build it* — it dissolves the folder cleanup underneath and makes the docs self-maintaining.

Why this shape: the run burns down three quick items so the user meets the one genuinely hard decision with a cleared deck — and the whole dedup thread never had to be asked on its own, because the finale's answer settles it.
