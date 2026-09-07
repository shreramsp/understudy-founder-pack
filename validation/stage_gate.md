# Stage gate — where the company sits, and what passing the next gate requires

> **What this is** — placement in Blank's four steps (Discovery → Validation → Creation → Building), the evidence supporting that placement, and the numbered exit criteria for the next gate.
> **Why it exists** — a founder under pressure describes the company one stage ahead of where it is, which causes money and hiring to be spent on the wrong stage. This file states the placement against evidence and makes the exit numeric.
> **How to read it** — the placement is deliberately unflattering. A skeptic should check that no exit criterion below could be satisfied by an opinion.
> **Depends on / feeds** — inherits [riskiest_assumptions.md](riskiest_assumptions.md), [experiment_board.md](experiment_board.md); feeds [metrics_by_stage.md](metrics_by_stage.md), `financials/use_of_funds.md`.

## Placement: **Customer Discovery, early.** Not Validation.

**Evidence for the placement, not against it:**

- No customer has seen a price. No discovery interview has been conducted.
- No code exists. `BRIEF.md` records stage as *design*.
- Every row of [riskiest_assumptions.md](riskiest_assumptions.md) reads `untested`, including all four that kill the company.
- The problem hypothesis is sourced [S21][S33] but **unvalidated with a single MSP owner**.

**What the pack has that an early-Discovery company usually does not:** a sourced research layer, a falsifiable core hypothesis with a pre-declared threshold, and an architecture whose privacy claim is stated tightly enough to be attacked. **That is preparation, not traction**, and the distinction is the whole point of this file.

## Exit criteria — Discovery → Validation

All seven must hold. Each is a number or a binary, none is a judgement.

**Criterion 7 was added after critic review, which found the original six contained no commitment.** All of them could pass with nobody having agreed to anything — a weaker bar than `strategy/gtm.md` §4 already sets for itself at months 9–10. **A gate the GTM plan outruns is not gating.**

| # | Criterion | Threshold | Source |
|---|---|---|---|
| **1** | Problem confirmed **genuinely unprompted** | **≥6 of 10** owners name onboarding cost in the answer to **Q0** — *"the three biggest constraints on your delivery capacity last quarter"* — asked before the topic is raised by either party | discovery_guide Q0 |
| **2** | Ticket mix known | **Graded evidence ladder**: ≥2 PSA exports **+** 8 memory estimates **+** one PSA-vendor or community benchmark. (±10pp was unreachable at 5 convenience exports — with a between-MSP SD near 10pp the half-width is ~12pp before selection bias) | E8 |
| **3** | Channel is real | **≥1 of 3** named peer or buying groups admits a pre-revenue vendor founder | E4 |
| **4** | Price has a basis | **Arm A ≥3 of 5 sign an LOI at the banded price, with the hours gap disclosed** — split-sample per E3's branch table, not a verbal reaction | E3 |
| **5** | Core mechanism supported | Cross-environment skill transfer **≥70%** on the held-out set | E1 |
| **6** | Differentiation supported | Skills retain **≥2×** the post-change success rate of a fallback-enabled RPA baseline | E2 |
| **7** | **Somebody has committed something** | **≥3 signed design-partner LOIs** | `strategy/gtm.md` §4 |

**Criteria 1–4 need no product and cost under $2,000 in total.** Criteria 5–6 need the harness. **A company that passes 1–4 and fails 5 is not in Validation; it is in Discovery with a better-understood market and a dead mechanism** — and the honest response is to say so publicly rather than re-scope quietly.

## What we do *not* do before this gate passes

- **No hiring.** Not an engineer, not the MSP-side operator the founder story names as the first hire.
- **No marketplace integration work.** It is 18–24 months out and gated on SOC 2 and references [../strategy/channel_plan.md](../strategy/channel_plan.md).
- **No *seed* raise on the strength of the pack.** Stated honestly rather than as a technicality: criteria 5 and 6 are unreachable without the **pre-seed** `financials/use_of_funds.md` raises precisely to fund them. **The pre-seed is raised to fund the gate; the seed is raised on the gate having returned.** Claiming the gate before it returns is the thing prohibited here.
- **No paid pilot before month 12**, which holds only if every build item lands at its optimistic bound.

## The next two gates, stated so the current one is not mistaken for the finish

**Validation → Creation** requires a repeatable sale: 3 paying MSPs acquired through the same channel motion, ≥2 environments each expanded without a sales conversation, and review cycle time measured at ≤6 weeks median (E7).

**Creation → Building** requires the cross-customer mechanism to exist: **≥3 distinct MSPs contributing to the global layer** (the m≥3 threshold), with measured contribution to a new customer's first environment. That is a year-two milestone at the earliest, and the corrected threshold is the reason.

**Recommended next 3:** (1) run criteria 1–4 in the first month; (2) do not describe the company as being in Validation until criterion 5 returns a number — the language leaks into hiring and fundraising decisions faster than the evidence does; (3) if criterion 5 fails, publish it, because a clean negative on a forty-year-old assumption is a real contribution and a quiet pivot is not.
