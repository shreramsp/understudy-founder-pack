# Not vaporware — what is buildable this quarter, what is research risk

> **What this is** — the concrete engineering position: stack choices, how quality is measured continuously, the cost model at current prices, and an honest split between what a competent team ships this quarter and what is genuinely research.
> **Why it exists** — every claim in this pack is conditional on a system that does not exist yet. This file states what building it actually requires, so a technical evaluator can judge the schedule rather than the ambition — and so the one genuinely uncertain component is named rather than hidden inside a roadmap.
> **How to read it** — §4 is the honest part. A skeptic should attack the cost model in §3, whose volume assumptions are unmeasured.
> **Depends on / feeds** — inherits [deep_dives.md](deep_dives.md), [architecture/00_INDEX.md](architecture/00_INDEX.md), [../product/features_prioritized.md](../product/features_prioritized.md); feeds `financials/unit_economics.md`, `narrative/vc_memo.md`, `validation/experiment_board.md`.

## 1 · Stack

| Layer | Choice | Why |
|---|---|---|
| Capture agent | Native Windows (C#/Rust) using UI Automation; macOS secondary | MSP engineer workstations are overwhelmingly Windows; UIA gives structured control roles that vision has to infer |
| Transport | mTLS to the MSP's own stage-1 node, never to us | D6: the vendor is not on the raw-data path at all |
| Stage-1 node | Containerised, deployable to an MSP's existing virtualisation or a small cloud tenant they own | It must live where the MSP already operates, not where we would prefer |
| Action typing | Mid-tier multimodal model, batch | High volume, latency-tolerant, and the cost line that scales with capture |
| Clustering | Classical sequence alignment + profile HMMs over typed actions — **not** an LLM | Deterministic, inspectable, debuggable. An LLM here would make the core bet unfalsifiable |
| Skill synthesis | Frontier model, low volume | Quality matters more than cost; runs once per cluster |
| Executor | Deterministic step runner + frontier model only for re-grounding | Most execution should not involve a model at all |
| Skill format | `SKILL.md`, Apache-2.0 open standard [S24] | Readable by the engineer it came from (`P6`); no lock-in from the format, which is a feature not a concession |
| Evaluation harness | Standalone, built **before** clustering is tuned | Otherwise the system grades its own homework |

**The deliberate non-choice:** no model fine-tuning anywhere. Skills are text. This keeps customer data out of a training loop, which is what makes the security answer sayable, and it means improvement comes from better clustering rather than from accumulating a weights advantage nobody can audit.

## 2 · How quality is measured continuously

| Metric | Method | Where it runs |
|---|---|---|
| Clustering correctness | Held-out environment scoring against a hand-labelled procedure set (4.1, 4.4) | Offline harness (N8) |
| Skill robustness | **E2**: altered-UI perturbation vs a selector-based RPA baseline (4.2, 4.3) | Offline harness |
| Verified-action accuracy | Criterion pass rate, plus human review of a sample of passes | Production |
| Silent-wrongness rate | Reversals within ticket life (X23) — the only detector for the 14:20 class | Production |
| Envelope safety | Adversarial re-identification attempts (X25) | Offline, pre-review |
| Drift | CUSUM on per-skill verification (6.1) | Production |

**No public benchmark exists for any of this** [../research/survey.md](../research/survey.md) §4. That is a credibility problem and an opportunity: the harness is a moat component as well as an engineering necessity, and publishing its method — not just its numbers — is what would make the category's first yardstick ours.

## 3 · Cost model at current prices

Per environment, per month, at the median 16-user client `(all volumes assumption-based; no pilot exists)`:

| Line | Volume assumption | Unit cost basis | Monthly |
|---|---|---|---|
| Action typing | ~40 sessions × ~15 min, batch mid-tier | falling ~10×/yr for fixed capability [S30] | `(assumption: $8–20)` |
| Clustering | classical, CPU only | MSP's own hardware | ~$0 marginal |
| Skill synthesis | ~10 skills/month, frontier | low volume | `(assumption: $3–8)` |
| Execution | ~12 tickets × mostly deterministic | model only on re-grounding | `(assumption: $2–6)` |
| **Total** | | | **`(assumption: $13–34)`** |

Against ~$216/month of ticket revenue per environment plus the amortised onboarding fee, this leaves gross margin comfortably above the 70% the strategy assumes — **but the number that matters is not in this table.** D6 moved clustering onto the MSP's hardware, so the real cost is a **per-node hardware floor the MSP must provide**, which is a commercial term in the contract rather than a line in our P&L. `financials/unit_economics.md` owes both sides.

## 4 · Buildable this quarter vs research risk

**Buildable by a competent engineer, low uncertainty:**
capture agent (F1) · redaction (N4) · session segmentation (N2) · skill viewer and correction UI (N12, X19) · action-class policy and approval flow (X5, X6) · agent identity (X7) · audit export (X21) · onboarding meter (N14) · drift detection (6.1) · node lifecycle (N15, tedious rather than uncertain).

**Hard engineering, meaningful uncertainty, still engineering:**
semantic action typing (DD2) — degrades on custom-drawn UIs and terminals · goal-directed re-grounding (DD5) — the failure mode is subtle and the mitigation (demote to gated) is known · envelope abstraction with k-anonymity (DD4) — the design is settled, the threshold is not.

**Genuine research risk — one item:**
**DD1, cross-session procedure clustering.** No benchmark, no named prior system, no literature to inherit [../research/capability_table.md](../research/capability_table.md) row 5. ALLOY [S22] demonstrates the adjacent claim at user-study scale; nothing demonstrates it across environments, which is A8.

**The honest position:** this is one research bet wrapped in about nine months of ordinary engineering. That is a better risk profile than a system with five uncertain components — but it is a *concentrated* risk, and there is no partial credit. If DD1 clusters into skills that do not transfer, M2's maintenance multiplier survives and M1 does not, and the company is materially smaller.

**What would falsify the whole thing, stated plainly:** skills synthesized from environment A execute correctly in environment B less often than a competent engineer would accept — call it below 70% on the held-out set. That number is measurable in the harness, before a customer, and it is the first thing the build should produce.

**Recommended next 3:** (1) build the harness before the clusterer, so the answer arrives as evidence; (2) implement clustering classically and resist making it a model call — an unfalsifiable core bet is worse than a negative result; (3) publish the evaluation method early, since no yardstick exists and the first credible one becomes the category's.
