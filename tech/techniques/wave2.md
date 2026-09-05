# Technique wave 2 — advanced and theory-grounded

> **What this is** — the second wave: methods that are established in their home fields but not yet standard practice in IT automation, and that this system depends on more heavily than wave 1.
> **Why it exists** — wave 1 shows the system is mostly assembly. This wave shows where the assembly requires judgement: which theoretical apparatus to point at the clustering problem, and how to keep an abstraction honest enough to cross a trust boundary.
> **How to read it** — cluster 2 (privacy-preserving abstraction) is the one carrying commercial weight, because D6's entire guarantee rests on it. A skeptic should attack 2.3's k-anonymity threshold.
> **Depends on / feeds** — inherits [wave1.md](wave1.md), [../deep_dives.md](../deep_dives.md); feeds [wave3.md](wave3.md), [decision_tree.md](decision_tree.md), [technique_feature_matrix.md](technique_feature_matrix.md).

**24 techniques across 5 clusters.** Fewer than wave 1 because the field is genuinely thinner here — this is stated rather than padded.

## 1 · Structure learning and consensus (6)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 1.1 | Multiple sequence alignment | Align *n* sequences simultaneously rather than pairwise, yielding a true consensus | Bioinformatics standard |
| 1.2 | Grammar induction from traces | Infer a grammar whose language is the set of valid runs of a procedure | Formal-languages literature |
| 1.3 | Automaton learning (L*/passive) | Learn a state machine from observed traces | Angluin-style active learning; passive variants suit recorded data |
| 1.4 | Hierarchical clustering with a stability criterion | Choose the cut by cluster stability rather than a fixed *k* — **the guard against DD1 over-merging** | Consensus-clustering literature |
| 1.5 | Minimum description length as a merge criterion | Merge two clusters only when it shortens the total description | MDL principle |
| 1.6 | Silhouette / stability validation | Quantify whether a clustering is real or an artefact of the metric | Standard cluster validation |

## 2 · Privacy-preserving abstraction (5) — the commercially load-bearing cluster

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 2.1 | Whitelist-constructed serialisation | Emit only fields from a closed vocabulary, rather than removing identifiers from free text | Fails closed rather than open — DD4 |
| 2.2 | Structural anonymisation | Preserve the *shape* of a pattern while discarding every value | Standard in telemetry design |
| 2.3 | k-anonymity thresholding | A pattern crosses only once observed in ≥k distinct tenants `(assumption: k=3)` | Sweeney's k-anonymity — **the actual guarantee behind D6** |
| 2.4 | Federated aggregation | Compute cross-tenant statistics without centralising the underlying records | Federated-analytics practice |
| 2.5 | Re-identification testing | Actively attempt to fingerprint a tenant from its published envelope entries | Adversarial privacy evaluation — **owed to the security pack, and currently unbuilt** |

## 3 · Goal-directed recovery (5)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 3.1 | Goal-state predicates | Express success as a checkable property of the world, not of the steps | Planning literature — the basis of `P3` |
| 3.2 | Hierarchical task networks | Decompose a goal into methods, allowing an alternative method when one fails | HTN planning |
| 3.3 | Bounded search under a budget | Cap exploration so recovery cannot become an incident | Standard anytime-algorithm practice |
| 3.4 | Read-only probing | Interrogate state without mutating during recovery | Safety constraint, DD5 |
| 3.5 | Semantic control matching | Locate a control by inferred function when its identifier has changed | The re-grounding mechanism; adapted from retrieval |

## 4 · Evaluation under scarcity (4)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 4.1 | Held-out environment evaluation | Score a skill in an environment it was never recorded in — **the A8 measurement** | Standard generalisation testing |
| 4.2 | Adversarial perturbation testing | Deliberately alter the UI and measure degradation — **this is E2** | Robustness literature; D5 |
| 4.3 | Paired-baseline comparison | Measure against a selector-based RPA implementation of the same procedure on the identical perturbation | Controlled comparison; the non-rigged baseline D5 requires |
| 4.4 | Inter-rater agreement on labels | Establish that the hand-labelled procedure set is itself reliable before scoring against it | Standard; the harness's own validity |

## 5 · Human–automation interaction (4)

| # | Technique | Mechanism | Anchor |
|---|---|---|---|
| 5.1 | Trust calibration through transparency | Expose capability *and* limits so reliance matches reality | Lee & See [S35] |
| 5.2 | Disuse mitigation | Design against expert rejection, the documented failure mode for this product | Parasuraman & Riley [S36] |
| 5.3 | Automation-bias countermeasures | Structure approvals so habituation does not erode scrutiny — vary presentation, surface the unusual | Automation-bias literature, survey §6b |
| 5.4 | Attribution and credit | Name the contributing human, converting capture from surveillance into authorship | `P8`; no formal literature anchor — an assertion this pack makes |

## What wave 2 concedes

**The field is thinner than wave 1 and this wave stops at 24 rather than padding to 50.** Two entries are honest gaps rather than capabilities: **2.5 re-identification testing is unbuilt**, and it is the test that would actually validate D6 rather than assert it; **5.4 has no literature anchor** and rests on a claim about human motivation that the pack has not evidenced.

**Recommended next 3:** (1) build 2.5 before the first security review, because a founder who has attacked their own envelope has an answer no competitor's policy statement can match; (2) settle 1.4's stability criterion early — it is the guard against DD1's dangerous failure mode; (3) implement 4.3's paired baseline before E2 runs, since an unfair baseline makes the whole §5 argument worthless.
