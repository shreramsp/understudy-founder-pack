# Pivot log — what has already been killed, and what would kill what remains

> **What this is** — the decision journal: options considered and rejected during this run with the reason, plus the standing pivot-or-persevere criteria in the form "we pivot if X by date Y".
> **Why it exists** — a company that cannot say what it has already rejected has not made any decisions. This log also preserves *why* something was killed, which is the thing that gets lost first and re-litigated most.
> **How to read it** — the rejections are more informative than the criteria. A skeptic should check that each rejection has a reason that would still hold if the founder changed their mind.
> **Depends on / feeds** — inherits [../ASSUMPTIONS.md](../ASSUMPTIONS.md) D1–D10 and the critic rounds; feeds [stage_gate.md](stage_gate.md), `narrative/vc_memo.md`.

## Already killed — during the grill and the build of this pack

| # | Option | Killed because | When |
|---|---|---|---|
| K1 | **Internal IT as the beachhead** | It is where every funded competitor is fighting, on resolution quality — the axis we cannot win. One internal-IT customer also contributes one environment where an MSP contributes ~41 | Grill, round 1 |
| K2 | **Per-tenant-only skill library** | No cross-customer compounding; the moat becomes workflow lock-in only, which is weaker than the mechanism deserves | Grill, round 1 |
| K3 | **Claiming unattended autonomy** | Long-horizon agent completion is 20.6% [S16]. A pack promising it fails its first technical diligence call | D1, phase 1 |
| K4 | **Per-resolved-ticket pricing alone** | Yields ~$107M SAM and a year-1 customer worth ~$1,100, at which no acquisition channel is viable | D4, phase 2 |
| K5 | **Flat $1,500 onboarding fee** | Approaches 100% of displaced cost at the small end of a book whose median client is 16 users | D7, phase 2 |
| K6 | **Charging for environment 1** | It displaces *negative* hours — charging for it is charging for a loss, and a design partner's timesheet finds that in an afternoon | D9, phase 3 |
| K7 | **Clustering inside the *client* boundary** | Not implementable: capture originates on MSP workstations, cross-environment clustering needs environments co-located, and SaaS-only clients have no perimeter | D6 correction, phase 3 |
| K8 | **Hosted inference for action typing** | Frames of a client's admin console reaching a third party breaks D6's guarantee outright. Moved on-node at the cost of a GPU | Phase 4 critique |
| K9 | **"RPA has no success criterion"** as the differentiation | Falsifiable in one sentence — UiPath Verify App State, Blue Prism Wait stages. Narrowed three times to the claim that survives | D5, then phase 4 critique |
| K10 | **The 10× maintenance multiplier** | Its baseline is hours the pack itself calls "largely unperformed", and the strategy layer had already refused to price against it | Phase 4 critique |
| K11 | **k≥3 counting client tenants** | Three observations could sit inside one MSP's book, identifying that MSP with certainty at its first security review. Now counts distinct MSPs | Phase 4 critique |
| K12 | **Deleting process mining from the technique catalogue** | Reversed: DD1 must tolerate reordering, which order-preserving alignment cannot represent; partial-order methods are exactly those rows | Phase 4 critique |

**Note what K8–K12 have in common.** They were all killed by adversarial review *after* being written into the pack as settled. **Five load-bearing claims survived authorship and did not survive scrutiny** — which is the argument for the critic loop, and the reason the run's honest completion state matters more than its artifact count.

## Standing pivot-or-persevere criteria

Each states a date and a number. A criterion without both is an intention.

| # | We pivot if… | By | To what |
|---|---|---|---|
| **P1** | Cross-environment transfer is **<50%** after three clustering approaches (E1) | Month 11 | **Stop and return remaining capital, unless E1's failure teaches something specific that makes K1 viable.** The earlier version pivoted to a single-environment product sold to internal IT — which is **K1, the option this same log killed** as "where every funded competitor is fighting, on the axis we cannot win". A pivot into a market you rejected, on a mechanism that just failed, is not a pivot. **This is the one criterion that stops the company, and the log previously had none** |
| **P2** | Transfer lands **50–70%** | Month 11 | Persevere with a narrowed claim: assisted onboarding rather than automated, priced against the runbook rather than the hours |
| **P3** | **Neither E3 arm reaches 3 of 5 signed LOIs** (branch 3) | Month 3 | The per-environment fee has no basis at any price. Move to the **D12 per-MSP platform fee** and accept the revenue-model change it forces. *(If Arm A fails but Arm B clears, that is branch 2 — rebuild on the ~$241 schedule at ~$124M SAM, not a platform-fee pivot. The earlier version conflated the two.)* |
| **P4** | **Zero of three** peer/buying groups admit a vendor founder (E4) | Month 2 | The primary and best-economics channels are closed. Reshape around the RMM/PSA marketplace at 18–24 months, which changes the raise size and timing |
| **P5** | Envelope re-identification **succeeds** (E5/X25) | Month 3 | Raise *m*, add a linkage budget or a noise floor — and if none suffices, **the global layer is abandoned** and the company is per-tenant only, which is K2 arriving by a different road |
| **P6** | Capture pause rate **>25%** or narration **<30%** (**E6b**, at a design partner with employed engineers — not E1's contractors) | **First pilot + 90 days** | `P8` is failing. The product needs to change, not the messaging — and if it cannot, the input dries up and there is no company |
| **P7** | Median client-side security review **>10 weeks** (E7) | Month 4 | Expansion velocity caps below the ramp. Re-time the revenue model and reconsider whether in-boundary distillation can be simplified further |

## What we will not pivot on

- **Supervised execution.** If the market demands unattended autonomy before the evidence supports it, we lose those deals. That is a cost we accept (D1).
- **Publishing negative results.** Including E1. A quiet re-scope after a bad number is how a company keeps its story and loses its credibility.
- **The environment-1 overrun staying visible** (D8).

**Recommended next 3:** (1) date-stamp every row above at the start of the run, since criteria without dates get renegotiated; (2) review this log at each gate rather than at each setback — its value is in the rejections, and rejections get re-litigated when things are going badly; (3) add a row every time the critic loop kills a claim, because K8–K12 are the most useful entries here and they exist only because someone wrote them down.
