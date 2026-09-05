# Technique wave 1 — established practice

> **What this is** — the first wave of the technique arsenal: methods that are established, documented and in production use somewhere today. Per technique: name, one-line mechanism, evidence anchor.
> **Why it exists** — a deep-tech pack that lists only frontier methods is claiming novelty it does not have. Most of what this system does is well-understood engineering; naming that honestly is what makes the two genuinely uncertain steps (DD1 clustering, A8 transfer) legible as the actual bet rather than lost in a list.
> **How to read it** — the cluster counts are the argument: 31 techniques, of which 27 are borrowed and 4 are adapted. A skeptic should check that nothing here is claimed as novel.
> **Depends on / feeds** — inherits [../deep_dives.md](../deep_dives.md), [../../research/survey.md](../../research/survey.md); feeds [wave2.md](wave2.md), [decision_tree.md](decision_tree.md), [technique_feature_matrix.md](technique_feature_matrix.md).

**31 techniques across 6 clusters.** Status: `borrowed` (used as documented) · `adapted` (modified for this domain).

## 1 · Capture and instrumentation (6)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 1.1 | UI Automation / accessibility-tree extraction | Read control roles and states from the OS accessibility layer rather than pixels | Windows UIA, standard in RPA tooling · `borrowed` |
| 1.2 | DOM-level event capture | Structured action capture in browser-based admin consoles | Standard web instrumentation · `borrowed` |
| 1.3 | Input-event hooking | Timestamped keyboard and pointer events correlated with window focus | OS-level, standard · `borrowed` |
| 1.4 | Screen-frame sampling with change detection | Capture frames on state change rather than at fixed rate, cutting volume by an order of magnitude | Standard video encoding practice · `borrowed` |
| 1.5 | Field-level redaction at capture | Drop credential and secret fields before they reach storage | [S29] makes this a legal requirement, not a nicety · `adapted` |
| 1.6 | Push-to-talk narration capture | Short voice segments bound to a UI event rather than continuous audio | Commodity ASR · `adapted` — the binding to a *branch point* is the adaptation |

## 2 · Sequence and process analysis (7)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 2.1 | Sequence alignment (Needleman–Wunsch) | Align two action sequences tolerating insertions and deletions | Bioinformatics, 1970 · `borrowed` |
| 2.2 | Profile HMMs | Model a family of sequences as a probabilistic consensus with per-position variation | Standard in sequence families · `adapted` — positions are UI actions |
| 2.3 | Process mining (alpha / heuristic miners) | Reconstruct a process model from event logs | Celonis-class tooling [S8] · `borrowed` |
| 2.4 | Task mining | Desktop-level capture to task-flow diagrams | UiPath Task Mining, FortressIQ [S7][S8] · `borrowed` — this is the category we are extending |
| 2.5 | Trace clustering | Group process traces by structural similarity | Process-mining literature · `borrowed` |
| 2.6 | Longest-common-subsequence extraction | Find the invariant spine across many runs | Classic · `borrowed` |
| 2.7 | Edit-distance variance measurement | Quantify how far a run deviates from the consensus — **the numeric basis of the variance envelope** | Classic, applied to a new object · `adapted` |

## 3 · Programming by demonstration (5)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 3.1 | Version-space algebra for PbD | Maintain the set of programs consistent with the demonstrations seen | PbD literature, survey §1 · `borrowed` |
| 3.2 | Generalisation from multiple traces | Use disagreement between demonstrations to locate what is incidental | survey §1 — the core PbD insight · `borrowed` |
| 3.3 | Intent elicitation at branch points | Ask the demonstrator *why* rather than inferring it | survey §1's unsolved problem; ALLOY [S22] · `adapted` |
| 3.4 | Demonstration-to-workflow synthesis | Emit a reusable workflow from computer-use demonstrations | ALLOY [S22] — validated at user-study scale · `borrowed` |
| 3.5 | Negative demonstration | Learn from what the operator *did not* do, or abandoned | survey §7; F3 retains abort sessions · `adapted` |

## 4 · Execution and verification (6)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 4.1 | Attribute-based UI selectors | Address controls by role and attributes rather than position | UiPath, Blue Prism · `borrowed` — **the baseline E2 measures against** |
| 4.2 | Anchor-based element location | Locate a control relative to a stable neighbour | RPA standard · `borrowed` |
| 4.3 | Application-state assertion | Check the interface is in an expected state before proceeding | UiPath Verify/Check App State · `borrowed` — and the thing §5 distinguishes a *goal* criterion from |
| 4.4 | Idempotent operation design | Structure actions so repetition is harmless | Distributed-systems practice · `borrowed` |
| 4.5 | Compensating transactions | Record an explicit undo path before mutating | Saga pattern · `adapted` — recorded *before* execution, which is what made 14:20 recoverable |
| 4.6 | Preflight precondition checks | Verify assumptions before acting rather than discovering them mid-run | Standard ops practice · `borrowed` |

## 5 · Safety, identity and governance (4)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 5.1 | Non-human principals / workload identity | The agent holds its own directory identity | Entra workload identities, Okta service apps · `borrowed` |
| 5.2 | Action-class policy enforcement | Classify by blast radius, gate accordingly | Standard privileged-access practice · `borrowed` |
| 5.3 | Just-in-time elevation | Grant the minimum privilege for the minimum window | PIM/PAM practice · `borrowed` |
| 5.4 | Immutable audit logging | Attributable, tamper-evident action records | Compliance standard · `borrowed` |

## 6 · Monitoring and drift (3)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 6.1 | CUSUM / change-point detection | Detect a shift in a metric before it becomes a failure | Classical SPC · `borrowed` |
| 6.2 | Canary execution | Run a changed skill on a small slice first | Deployment standard · `borrowed` |
| 6.3 | Golden-path regression testing | Re-run known-good procedures against a reference environment | Test practice · `adapted` |

## What wave 1 concedes

**27 of 31 are borrowed outright.** This system is mostly an assembly of well-understood parts, and saying so is the point: it means the schedule risk is low everywhere except the two places it is not. **Nothing in wave 1 is a differentiator.** The differentiation is the *circuit* [../../product/features_flagship.md](../../product/features_flagship.md), and specifically the four `adapted` rows — 1.6, 2.7, 3.5 and 4.5 — which are where an ordinary technique is pointed at an unusual object.

**Recommended next:** implement 2.1, 2.2 and 2.7 first. They are the numeric core of DD1, they are decades old and well-characterised, and if the variance envelope cannot be extracted with methods this mature the problem is the representation (DD2) rather than the algorithm.
