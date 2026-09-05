# Technique wave 3 — frontier and cross-domain imports

> **What this is** — the third wave: methods drawn from current AI research and from fields outside IT operations, applicable to this system but not yet proven in it.
> **Why it exists** — waves 1 and 2 describe what gets built. This wave is the research pipeline: what becomes possible if the core bet lands, and where the ceiling moves. It is explicitly speculative, and each row says so.
> **How to read it** — treat every row as a hypothesis. A skeptic should note that nothing here is on the Now or Next tier of [../../product/features_prioritized.md](../../product/features_prioritized.md) and none of it rescues the pack if DD1 fails.
> **Depends on / feeds** — inherits [wave2.md](wave2.md), [../../research/capability_table.md](../../research/capability_table.md); feeds [technique_feature_matrix.md](technique_feature_matrix.md), `financials/use_of_funds.md` (what research money would buy).

**18 techniques across 4 clusters. The wave stops early and the field is not exhausted** — it is that most frontier work in this space is aimed at *executing* better, and this system's binding constraint is *learning* better. That asymmetry is itself a finding.

## 1 · Learning from unlabelled interaction (5)

| # | Technique | Mechanism | Status |
|---|---|---|---|
| 1.1 | Screen-video pretraining | Use unlabelled screen recordings as a training signal without manual annotation | VideoAgentTrek [S23] — published, unreplicated here |
| 1.2 | Self-supervised action representation | Learn the action embedding from interaction rather than hand-designing the schema | Speculative; would replace DD2's typed schema |
| 1.3 | Contrastive procedure embedding | Learn a metric where two runs of the same procedure are near and different procedures are far — **would directly attack DD1** | Speculative, and the highest-value row here |
| 1.4 | Curriculum from escalation data | Order learning by difficulty using which tickets humans escalated | Speculative |
| 1.5 | Counterfactual trace generation | Synthesise plausible failure branches rather than waiting to observe them — attacks `P2` directly | Speculative, and dangerous if wrong: a synthesised branch that never occurs is a confident fiction |

## 2 · Agentic execution frontier (5)

| # | Technique | Mechanism | Status |
|---|---|---|---|
| 2.1 | Long-horizon planning with subgoal decomposition | Extend beyond the short-horizon segment this pack claims | Best long-horizon completion is 20.6% [S16] — **why D1 exists** |
| 2.2 | Compositional generalist-specialist agents | A generalist plans, specialists execute domain steps | Agent S2 architecture, research-stage |
| 2.3 | Tool-use over API rather than UI | Bypass the interface where an API exists — faster and far more stable | Available today; **the honest note is that this reduces the value of UI capture wherever it applies** |
| 2.4 | Self-verification via independent re-derivation | Confirm an outcome by a second, unrelated route | Speculative; would strengthen DD3 |
| 2.5 | Uncertainty-aware abstention | Decline to act when the model's own uncertainty is high | Calibration research; complements envelope enforcement |

## 3 · Cross-domain imports (5)

| # | Technique | Mechanism | Source field |
|---|---|---|---|
| 3.1 | Clinical-pathway variance analysis | Model how a standard protocol is actually deviated from across institutions | Healthcare ops — **the closest structural analogue to the variance envelope in any field** |
| 3.2 | Aviation checklist design | Design procedures for reliable execution under distraction and fatigue | Human factors |
| 3.3 | Manufacturing SPC | Control-chart methods for detecting process drift | Industrial engineering — generalises DD6 |
| 3.4 | Apprenticeship / cognitive task analysis | Elicit expert knowledge that experts cannot articulate unprompted | Knowledge engineering — the formal version of F2 narration |
| 3.5 | Legal document versioning and provenance | Track authorship, amendment and derivation of a living text | Records management — applies directly to skill governance |

## 4 · Economics and scale (3)

| # | Technique | Mechanism | Status |
|---|---|---|---|
| 4.1 | Model cascade routing | Route each step to the cheapest model that can do it | Standard practice; matters because inference runs on MSP hardware (D05) |
| 4.2 | Distillation to small local models | Move high-volume typing to a small model at the edge | Feasible; directly reduces the per-node hardware floor |
| 4.3 | Speculative execution of likely next steps | Pre-compute probable next actions to cut latency | Speculative, and dangerous on mutating paths |

## What wave 3 concedes

**Nothing here rescues the company if DD1 fails.** Row 1.3 (contrastive procedure embedding) is the only entry that would materially attack the core bet, and it is speculative.

**Row 2.3 is the uncomfortable one.** Where a real API exists, using it is faster, cheaper and more stable than driving a UI — so the long-run value of UI capture is concentrated in the surfaces that *lack* good APIs: native admin tools, terminals, legacy consoles. That is a real limit on the mechanism, it argues the product should prefer APIs wherever they exist rather than defend UI automation on principle, and it is better stated here than discovered by an investor.

**Recommended next:** none of this is fundable yet. Wave 3 exists so that `financials/use_of_funds.md` can name what research money would buy *after* DD1 returns a positive result — and so the pack does not pretend a research pipeline is a product roadmap.
