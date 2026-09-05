# Deep dives — the six systems that have to work

> **What this is** — the tier-1 algorithmic problems behind the mechanisms, each stated as the one question it answers, the real methods that answer it, its inputs and outputs, the design choice that matters, and how it fails.
> **Why it exists** — the whitepaper argues that mechanisms remove frictions; this file is where those mechanisms stop being nouns. It is also where the pack is most exposed: **DD1 is the company's core bet and has no benchmark, no named prior system, and no literature to inherit** [../research/capability_table.md](../research/capability_table.md) row 5.
> **How to read it** — DD1 first; everything downstream is conditional on it. A skeptic should attack DD1's evaluation strategy, since a system with no benchmark can grade its own homework.
> **Depends on / feeds** — inherits [whitepaper.md](whitepaper.md), [../research/capability_table.md](../research/capability_table.md), [../product/PRD.md](../product/PRD.md); feeds [architecture/00_INDEX.md](architecture/00_INDEX.md), [not_vaporware.md](not_vaporware.md), `narrative/vc_memo.md`.

---

## DD1 · Cross-session procedure clustering

**The one question:** given many recordings of engineers doing work, which of them are the *same procedure*, and what is invariant across them?

**Approach.** Three stages, none novel individually; the combination is the bet.
1. **Episode representation.** Each session segment becomes a typed action sequence — `(app, ui_role, action_kind, value_class)` — deliberately *not* raw pixels or coordinates. Value classes (`email_address`, `group_name`, `guid`) rather than values, so that redaction (N4) and abstraction are the same operation rather than two.
2. **Alignment.** Sequence alignment adapted from bioinformatics (Needleman–Wunsch / profile HMMs) over action types, tolerant of insertions, deletions and reordering — because two engineers doing the same job take different routes through the same UI.
3. **Consensus + variance.** The aligned set yields a modal path (the procedure) and a **distribution over deviations** (the variance envelope, `P7`). The envelope is not a by-product; it is the asset.

**Inputs:** typed action streams + optional narration transcripts. **Outputs:** procedure clusters with per-step variance and per-cluster support counts.

**Key design choice and why.** *Cluster on action semantics, not on UI trajectory.* Trajectory clustering makes two engineers reaching the same end by different routes look like two procedures, which is precisely the failure that makes the library grow without getting better. The cost is that semantic typing must be inferred, which is DD2's problem.

**Failure modes.** Over-merging (two genuinely different procedures collapse into one skill with an incoherent envelope — the dangerous one, because it produces a confident wrong skill). Under-merging (the library grows without generalising). Narration-absent branches, where the *why* was never spoken and the alignment cannot tell essential from incidental (`P1`).
**Fallback:** under-merge by default. A library with duplicate skills is inefficient; a library with over-merged skills is unsafe.

---

## DD2 · Semantic action typing from screen capture

**The one question:** what did this click *mean*?

**Approach.** Multimodal frame understanding plus accessibility-tree extraction where available, producing `ui_role` (the control's function, not its label) and `action_kind`. Prefer structured signal over pixels: on Windows admin tooling UIA gives roles directly, and browser admin consoles expose the DOM. Vision is the fallback for terminals and native tools that expose nothing. VideoAgentTrek [S23] establishes that unlabelled screen video carries enough signal to be useful without manual annotation.

**Inputs:** frames, input events, accessibility tree / DOM where present. **Outputs:** typed actions with confidence.

**Key design choice.** *Structured-first, vision-fallback* — the inverse of the demo-friendly choice. Vision-first looks more impressive and degrades badly on exactly the dense admin UIs this product lives in.

**Failure modes.** Custom-drawn UIs exposing no tree; terminal work where semantics live in text rather than controls; confidently wrong typing, which is worse than abstention. **Fallback:** abstain and mark the step opaque; an opaque step blocks promotion of the whole skill rather than being guessed.

---

## DD3 · Skill synthesis with a declared success criterion

**The one question:** what is this procedure *for*, and how would we know it worked?

**Approach.** From a cluster and its narration, generate `SKILL.md`: goal, preconditions, steps, **success criterion**, escalation envelope. The criterion is the hard part and the whole point (`P3`) — it must be a **goal-state predicate that is checkable independently of the steps that produced it**. "The user can complete an MFA challenge from a new device" is checkable; "the TAP was issued" merely restates step 4.

**Key design choice.** *Reject the skill if no independently checkable criterion can be derived.* An unverifiable skill is not a weak skill — it is the RPA failure mode with better prose, and admitting it would collapse the §5 argument the whole pack rests on.

**Failure modes.** Circular criteria (restating the last step). Criteria that are expensive or intrusive to check. Criteria that pass while the outcome is wrong — the 14:20 class [../product/journeys/day_in_life.md](../product/journeys/day_in_life.md), which no verification design eliminates.

---

## DD4 · Envelope abstraction and egress filtering

**The one question:** what can cross the MSP boundary without carrying tenant identity? (D6)

**Approach.** A whitelist-shaped transform, not a redaction pass. An envelope entry emits only `{procedure_shape, precondition_pattern, deviation_class, observation_count}` — constructed from a closed vocabulary rather than by removing identifiers from free text. **Anything not expressible in that vocabulary does not leave.**

**Key design choice.** *Whitelist construction over blacklist scrubbing.* Scrubbing fails open — one unanticipated identifier format and tenant data crosses. Whitelisting fails closed: an unrepresentable pattern is simply not shared, and the cost is a less complete global layer rather than a breach.

**Failure modes.** Vocabulary too narrow (the global layer starves and A8's compounding never materialises). Vocabulary too broad (a `deviation_class` that is effectively a fingerprint — e.g. a policy pattern unique enough to identify one tenant). **Mitigation, corrected after critic round 1 — the first version was decorative on three counts:**

1. **It is not k-anonymity.** Sweeney's k-anonymity is a property of equivalence classes over quasi-identifiers in a released table. This is a **minimum-support threshold on a released pattern** (k-map-shaped). A privacy reviewer will make that distinction immediately, so the pack makes it first.
2. **The threshold was counting the wrong thing.** It counted distinct *client tenants*. One MSP brings ~41 of them — so at cold start all three observations can sit inside a single design partner's book, and the envelope **identifies that MSP with certainty at exactly the moment of its first security review.** The threshold now counts **distinct MSPs** `(assumption: m≥3 MSPs, and ≥3 tenants within each)`. This lengthens the cold start considerably and is the correct trade.
3. **The attack is compositional, and per-entry thresholds do not address it.** A set of `deviation_class` values each cleared individually can jointly identify one tenant — the standard sparse-high-dimensional linkage result (Narayanan & Shmatikov 2008). Nothing in the released set is currently budgeted across entries.

**Honest status:** the guarantee is **heuristic, not formal.** l-diversity (Machanavajjhala 2007), t-closeness (Li 2007) and differential privacy all exist precisely because minimum-support alone is insufficient, and none is implemented here. **D6's promise is contingent on X25 — adversarial re-identification testing — which wave 2 concedes is unbuilt.** Until X25 runs, the correct statement to a security reviewer is "threshold plus adversarial testing", not "anonymised".

---

## DD5 · Goal-directed re-grounding

**The one question:** the interface changed — where is the thing I need now?

**Approach.** On precondition failure, search the current UI for a state satisfying the skill's goal predicate, using the semantic role that was recorded rather than the identifier that broke. Bounded: a fixed search budget, read-only probing, and escalation on exhaustion. **This is the D5 mechanism made operational** — it works only because DD3 guaranteed a goal exists to aim at.

**Key design choice.** *Read-only during re-grounding, always.* A search that mutates while exploring is how a re-grounding attempt becomes an incident.

**Failure modes.** Re-grounding onto a *similar but wrong* control — the highest-severity failure in the system, since it produces a confident wrong action. **Mitigation:** re-grounded steps demote the run to gated regardless of the skill's rung, so a human sees the first execution after any drift.

---

## DD7 · Blast-radius classification

**The one question:** is this synthesized step destructive?

**Why it is a deep dive and not a config table.** The entire safety ordering in [techniques/decision_tree.md](techniques/decision_tree.md) fires on this label, and the first version of this layer never said how a step acquires it. Wave 1 lists "action-class policy enforcement · standard privileged-access practice · borrowed" — but PAM classification is a **curated policy over named operations**, not a label inferred over arbitrary observed UI actions on admin surfaces. That gap *is* the adaptation, and it was unwritten.

**Approach.** A mapping from `(app, ui_role, action_kind)` to a blast-radius class, built from three sources: an explicit operation catalogue for the common stacks (Entra, M365, AD, Jira), the semantics available from the accessibility tree, and the engineer's own classification during skill endorsement.

**Key design choice — default-destructive on anything unmapped.** An operation the catalogue does not recognise is treated as destructive, and **an unmapped step blocks promotion of the whole skill** rather than being guessed. This is DD2's discipline (abstain rather than assert) applied to safety instead of semantics, and it is deliberately the annoying default: it produces friction proportional to coverage gaps, which is exactly where friction belongs.

**Failure modes.** Misclassifying a destructive operation as reversible — the highest-severity failure in the system, since it routes past rule 1 of the decision tree. A catalogue that drifts as vendors add operations. Engineers over-classifying to avoid gates, or under-classifying to reduce approvals.

**Note the second failure this exposes.** "Read" is not a single class. A mailbox export, a full directory enumeration and an MFA-state dump are all reads with real consequence, and the decision tree's original rule 7 said reads have "no blast radius" and execute freely. **That is the line a founder widens the week before a demo**, and the taxonomy is corrected accordingly.

## DD6 · Drift detection

**The one question:** is this skill still true?

**Approach.** Monitor per-skill verification pass rates and re-grounding frequency; a CUSUM-style change detector flags degradation before it becomes failure. Pause on threshold breach (`P4 P9`).

**Key design choice.** *Pause first, ask second — but tune for specificity.* The two asymmetries genuinely point opposite ways and the first version stated both without resolving them. Resolution: **pause is cheap, alerting is not.** A skill pauses on a low threshold (a missed drift can cause a client incident), but the *human-facing alert* fires on a high one — a spurious alert costs more trust than a silent pause, because a paused skill degrades throughput while a false alarm degrades belief. `(assumption: pause at a 2-sigma shift, alert at 3-sigma or on a second consecutive pause; both owed to the first pilot's data)`.

**Failure modes.** Slow drift under the detector's threshold. Seasonal patterns misread as drift. Too few executions to establish a baseline — which is the normal case for a rare skill, and is why drift detection cannot be the only safety mechanism.

---

## What this list concedes

**Six of seven are engineering.** DD2–DD7 are hard, but they are recombinations of known methods with known failure modes, and a competent team ships them.

**DD1 is research with a product schedule attached.** It has no benchmark to beat, no prior system to compare against, and the honest position is that a negative result is possible. The mitigation is not confidence — it is **DD1's evaluation harness (N8) existing before DD1 is optimised**, so the answer arrives as evidence rather than as an opinion held by the person who built it.

**Recommended next 3:** (1) build N8's harness against a hand-labelled procedure set before tuning DD1, or the system grades its own homework; (2) settle DD4's k-anonymity threshold early — it is the guarantee D6's security story rests on and it constrains DD1's output format; (3) treat DD1 over-merging as the priority failure mode, since it is the one that produces confident wrong skills rather than merely inefficient ones.
