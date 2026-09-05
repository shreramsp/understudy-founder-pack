# Technique × feature matrix

> **What this is** — which techniques power which flagship features, with orphan techniques and unsupported features flagged as findings rather than tidied away.
> **Why it exists** — a catalogue and a feature list can both look complete while being disconnected. This matrix is the reconciliation, and its two failure columns are the point: a technique powering nothing is either research indulgence or a missing feature, and a feature resting on no technique is a promise with no mechanism behind it.
> **How to read it** — skip to §3 and §4; the matrix itself is bookkeeping. A skeptic should check that no flagship feature appears in §4.
> **Depends on / feeds** — inherits [wave1.md](wave1.md), [wave2.md](wave2.md), [wave3.md](wave3.md), [../../product/features_flagship.md](../../product/features_flagship.md); feeds `visuals/` (heat table), `startup-audit`.

**73 techniques across three waves · 20 flagship features.** Wave 3 is excluded from the support analysis — it is a research pipeline, not a build plan, so every wave-3 row is expected to be an orphan.

## 1 · The matrix (waves 1–2 vs flagship features)

| Feature | Primary techniques | Supporting |
|---|---|---|
| **F1** Multi-surface capture | 1.1 UIA, 1.2 DOM, 1.3 input hooking | 1.4 change-detected sampling |
| **F2** Decision-point narration | 1.6 push-to-talk, 3.3 intent elicitation | 5.4 attribution (w2) |
| **F3** Failure/abort retention | 3.5 negative demonstration | 1.3 |
| **F4** Capture controls | 1.5 field-level redaction | 5.4 (w2) |
| **F5** Cross-session clustering | 2.1 alignment, 2.2 profile HMM, 1.1–1.6 structure learning (w2) | 2.5 trace clustering, 1.4/1.5 stability + MDL (w2) |
| **F6** Skill synthesis w/ criterion | 3.4 demonstration-to-workflow, 3.1 goal-state predicates (w2) | 3.1 version-space, 3.2 generalisation |
| **F7** Variance envelope | 2.7 edit-distance variance, 2.2 structural anonymisation (w2) | 2.6 LCS |
| **F8** Authorship attribution | 5.4 attribution (w2) | 3.5 legal versioning (w3, aspirational) |
| **F9** Shadow mode | 4.1 held-out evaluation (w2) | 6.2 canary |
| **F10** Deviation report | 4.4 inter-rater agreement (w2) | 2.7 |
| **F11** Promotion ladder | 5.2 action-class policy, 5.1 trust calibration (w2) | 6.2 |
| **F12** Action-class policy | 5.2, 5.3 JIT elevation | 4.4 idempotence |
| **F13** Agent identity | 5.1 non-human principals, 5.4 immutable audit | 5.3 |
| **F14** Envelope enforcement | 4.6 preflight checks, 2.5 uncertainty abstention (w3, aspirational) | 3.1 (w2) |
| **F15** Test-account exploration | 3.4 read-only probing (w2) | 4.6 |
| **F16** Success-criterion verification | 3.1 goal-state predicates (w2), 4.3 app-state assertion | 4.4 |
| **F17** Re-grounding | 3.2 HTN, 3.3 bounded search, 3.5 semantic matching (all w2) | 4.2 anchors |
| **F18** Drift detection | 6.1 CUSUM | 6.3 golden-path regression |
| **F19** Envelope widening | 2.7, 1.4 stability criterion (w2) | 3.2 |
| **F20** Onboarding meter | — | — |

## 2 · Density read

| Feature | Technique support | Read |
|---|---|---|
| F5, F17 | 5–6 techniques each | Correct: these are the two hardest problems |
| F1, F6, F12, F13, F16 | 3–4 each | Healthy |
| F3, F8, F10, F15 | 1–2 each | Thin, and honestly so — these are straightforward once the substrate exists |
| **F20** | **0** | See §4 |

**A matrix where every technique powered every feature would be a sign nobody checked.** The concentration on F5 and F17 is the correct shape: those are DD1 and DD5, the two places where the system is doing something that has not been done in this domain.

## 3 · Orphan techniques — powering nothing

| Technique | Wave | Verdict |
|---|---|---|
| **2.3 process mining (alpha/heuristic miners)** | 1 | **No longer an orphan — the earlier verdict is withdrawn.** DD1 needs to tolerate two engineers taking different routes through the same UI, which is transposition, which order-preserving alignment cannot represent. **Partial-order discovery is the family that can**, so this powers F5 and is on the build path |
| **2.4 task mining** | 1 | Retained for the same reason: its conformance-alignment machinery is what handles reordering in F5 |
| **2.5 re-identification testing** | 2 | **Orphan that should not be — this is a missing feature.** Nothing in the flagship list attacks our own envelope to see whether a tenant can be fingerprinted, and D6's whole guarantee rests on the answer. See §4 |
| **2.4 federated aggregation** | 2 | Premature: relevant only once the global layer spans many MSPs (L1) |
| **5.3 automation-bias countermeasures** | 2 | **Orphan that should not be.** `P9` says approval habituates and UX7 (the approval prompt) specifies a static prompt. Nothing varies presentation or surfaces the unusual |
| Wave-3 rows **other than 2.5 and 3.5** | 3 | Expected — research pipeline, not build plan |

## 4 · Unsupported features — promises with no mechanism

| Feature | Gap | Resolution |
|---|---|---|
| **F20 Onboarding meter** | No technique. It is instrumentation — counting engineer-hours and time-to-first-verified-skill | **Acceptable, and declared.** It is a measurement surface, not a mechanism, which is also why it carries the sole `—` in the PRD's principle mapping. It does not require a technique; it requires a definition, which [../../product/PRD.md](../../product/PRD.md) §9 now supplies |

**Two flagship features lean partly on aspirational rows, which §3 previously called "expected orphans" while §1 cited them as support.** F14 (envelope enforcement) lists wave-3 2.5 uncertainty-aware abstention, and F8 (authorship attribution) lists wave-3 3.5 legal versioning. Both are marked *aspirational* in §1 and neither is load-bearing — F14 works on preflight checks and goal predicates alone, F8 on attribution alone — but a flagship feature partly supported by a speculative row should say so where the support is listed, not only in a footnote. Both now do.

**One genuine finding, in the other direction.** Two techniques (2.5 re-identification testing, 5.3 automation-bias countermeasures) power nothing **because two features are missing**, and both are safety-adjacent:

1. **An envelope adversarial-testing capability.** D6's promise is that an envelope entry cannot identify a tenant. Nobody has tried to break it. A founder who has attacked their own boundary has an answer no competitor's policy statement matches — and if the attack succeeds, the k-anonymity threshold (`k=3`) is wrong and needs raising before the first security review, not after.
2. **Approval-surface countermeasures.** `P9` states that approval habituates and that automation bias makes a reliable system more dangerous at the margin. The product's response is a static prompt that looks identical the 201st time. The 14:20 incident is exactly this failure.

**Both are added to `features_prioritized.md` as X25 and X26 rather than left as a matrix observation** — an orphan technique that identifies a missing feature is the most useful thing this matrix produces, and leaving it as a note would waste it.

**Recommended next 3:** (1) build X25 (envelope adversarial testing) before the first security review; (2) build X26 (approval-surface countermeasures) before the first supervised promotion, since that is when habituation starts; (3) **the earlier recommendation to delete 2.3 and 2.4 is withdrawn** — DD1's reordering requirement needs partial-order methods, and those are the rows that supply them.
