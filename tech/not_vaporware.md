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
| Action typing | **On-node multimodal model — not a hosted API** | **This is forced by D6, and the first version got it wrong.** A hosted model on the frame path means screenshots of a client's Entra and AD consoles leave the MSP tenant for an unnamed third party, which contradicts D6's guarantee and is the first question in any MSP security review. Typing runs on the node or the guarantee is not true |
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

## 2b · The inference boundary — corrected

**The first version of this file put a hosted multimodal model on the frame path and no diagram showed the hop.** That is not a costing detail; it breaks D6. If typed actions are derived by sending frames to an inference provider, then raw client-console screenshots leave the MSP tenant, and D06's claim that "raw sessions exist in exactly one place" is false.

**Two ways to resolve it, and the pack takes the first:**

1. **Typing runs on the node.** A quantised open-weights multimodal model, sized for batch throughput rather than latency. Costs a GPU in the reference node (§3b) and some accuracy against a frontier model. **Preserves D6 exactly as stated, which is the point — it is an architecture constraint, not a preference.**
2. *(Rejected)* Hosted inference on redacted crops under a zero-retention DPA. Cheaper, more accurate, and it weakens the claim from *nothing leaves* to *we have contractual assurances about what leaves*. A security reviewer will notice the difference, and the compounding-half-is-defensible-by-construction argument becomes a policy argument instead.

**Skill synthesis is the exception and it is a narrow one.** Synthesis operates on the *already-abstracted* cluster — procedure shapes and typed action sequences, no frames, no values — so a frontier API call there carries no client data by construction. **That is the only outbound inference call in the system, and it is drawn in D05.**

## 3 · Cost model at current prices

**Corrected after critic round 1.** The first version priced revenue at "~$216/month per environment" against costs stated per environment per month. **$216 is the *annual* figure** — row 9 of [../strategy/market_sizing.md](../strategy/market_sizing.md) gives ~124 resolved tickets per MSP per month across 41 environments, i.e. ~3 tickets/environment/month at $6 ≈ **$18/environment/month, ~$216/year**. Compared against a monthly cost line that was a 12× error in the flattering direction, and it falsified by one division.

**It is also the wrong granularity.** Clustering and synthesis operate across an MSP's environments, not within one, so the costs do not decompose per environment. The model belongs at the MSP level:

Per **MSP**, per month `(all volumes assumption-based; no pilot exists)`:

| Line | Volume assumption | Cost basis | Monthly |
|---|---|---|---|
| Action typing | ~1,600 session-minutes across the book | **On-node (§2b) — no API cost** | **$0 marginal** |
| Clustering + alignment | classical, CPU, off-peak | On-node | $0 marginal |
| Skill synthesis | ~20–40 new or revised skills/month, frontier, on abstracted clusters only | the sole outbound inference call | `(assumption: $10–30)` |
| Execution | ~124 resolved tickets, mostly deterministic; model only on re-grounding | mid-tier, rare | `(assumption: $5–15)` |
| **Total marginal API** | | | **`(assumption: $15–45)`** |

**Revenue per MSP per month:** ~$744 in ticket revenue (124 × $6) plus ~$503 of amortised onboarding fees at the banded blended fee (D11) ≈ **~$1,247/month, ~$14,930/yr** — which reconciles with the steady-state figure the strategy layer carries.

**Marginal gross margin is therefore ~97%**, and that is not the interesting number. Falling inference prices [S30] make the API line nearly irrelevant here. **The cost that decides this business is the node**, which D6 moved onto hardware we do not own — so it leaves our P&L and arrives in the customer's procurement conversation instead.

### 3b · The reference node — the number an MSP owner asks for in the first call

The dominant cost is not in the table above, so the table's margin conclusion cannot be stated before this is:

| Resource | Reference spec `(assumption)` | Driver |
|---|---|---|
| GPU | 1 × 24GB (e.g. L4-class or a consumer 3090/4090) | On-node typing (§2b option 1) at batch throughput |
| vCPU / RAM | 8 vCPU / 32GB | Alignment and clustering are CPU-bound and run off-peak |
| Disk | ~2TB | Raw sessions for ~41 environments at the stated capture volumes, held to the retention window. **X22's retention engine is Next tier, so until it ships this number only grows** — which makes retention a capacity requirement, not just a privacy one |
| Network | Outbound to the vendor only: envelopes and health | No inbound requirement |

**Commercial fallback, because "provide a GPU box" loses deals:** offer a hardware credit against the onboarding fee, or a hosted node the vendor operates *inside a tenant the MSP owns* — which preserves the boundary while removing the procurement conversation. `financials/unit_economics.md` owes both sides, but the reference spec is ours to state and it is stated here.

**Only now the margin claim:** at ~$1,247/month per MSP against $15–45 of marginal API, gross margin clears the 70% the strategy assumes with wide room — **provided the node sits with the MSP or is credited against the onboarding fee.** If the vendor absorbs the hardware, roughly $2,000–4,000 of amortised capital lands per customer and the margin conclusion does not survive. `financials/unit_economics.md` must model both cases; this file states the reference spec so it can.

## 4 · Buildable this quarter vs research risk

**Buildable by a competent engineer, low uncertainty:**
capture agent (F1) · redaction (N4) · session segmentation (N2) · skill viewer and correction UI (N12, X19) · action-class policy and approval flow (X5, X6) · agent identity (X7) · audit export (X21) · onboarding meter (N14) · drift detection (6.1) · — **but not node lifecycle.** N15 is moved out of this bucket: the product layer calls it "the item most likely to be underestimated", it is rated L, and D09 now carries the on-call obligation, buffering thresholds and schema-version rule that make it an operational commitment rather than a build task. It belongs with the hard-engineering group below.

**Hard engineering, meaningful uncertainty, still engineering:**
**node lifecycle (N15)** — distributed components inside customer infrastructure, with version skew that corrupts the m≥3 count if unmanaged, and a paging obligation from the first deployment · semantic action typing (DD2) — degrades on custom-drawn UIs and terminals · goal-directed re-grounding (DD5) — the failure mode is subtle and the mitigation (demote to gated) is known · envelope abstraction with k-anonymity (DD4) — the design is settled, the threshold is not.

**Genuine research risk — one item:**
**DD1, cross-session procedure clustering.** No benchmark, no named prior system, no literature to inherit [../research/capability_table.md](../research/capability_table.md) row 5. ALLOY [S22] demonstrates the adjacent claim at user-study scale; nothing demonstrates it across environments, which is A8.

**The honest position, corrected.** The first version said "one research bet wrapped in about nine months of ordinary engineering" — which was roughly the *Now-tier floor alone*, applied to a list about twice that size, and which excluded every governance item the month-12 pilot is gated on. The product layer's own key prices the buildable list above at **~24 weeks at every optimistic bound and ~43 at midpoints**, and the Now tier at **~40 weeks floor, midpoints past 55** [../product/features_prioritized.md](../product/features_prioritized.md). This file inherits those numbers rather than publishing a third set.

**"Buildable by a competent engineer" and "shippable by this founder by month N" are not the same sentence**, and the first version wrote them as one. The first is defensible; the second is what the schedule actually depends on.

**DD1 gets its own line, because absorbing a research bet into an engineering estimate is the accounting move that makes it look like a sprint:**

| | |
|---|---|
| **Time-box** | 10 weeks from the harness being ready |
| **Iteration budget** | 3 substantive approaches (representation, alignment method, merge criterion) |
| **Kill criterion** | held-out cross-environment success below ~70% after the third approach |
| **On kill** | M1 collapses; the maintenance and risk-reduction claims survive; the company is materially smaller and the pack says so rather than re-scoping quietly |

That is a *concentrated* risk with a date attached, and there is no partial credit. If DD1 clusters into skills that do not transfer, M2's maintenance multiplier survives and M1 does not, and the company is materially smaller.

**What would falsify the whole thing, stated plainly:** skills synthesized from environment A execute correctly in environment B less often than a competent engineer would accept — call it below 70% on the held-out set. That number is measurable in the harness, before a customer, and it is the first thing the build should produce.

**Recommended next 3:** (1) build the harness before the clusterer, so the answer arrives as evidence; (2) implement clustering classically and resist making it a model call — an unfalsifiable core bet is worse than a negative result; (3) publish the evaluation method early, since no yardstick exists and the first credible one becomes the category's.
