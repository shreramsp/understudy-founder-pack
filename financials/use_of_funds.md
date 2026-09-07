# Use of funds

> **What this is** — the raise: amount, an 18–24 month milestone-linked spend plan where each block buys a named de-risking result, hires in order, the capital-efficiency metric to report, and what the next round's story requires this one to prove.
> **Why it exists** — this company has one question and a long build. A use-of-funds that spreads money evenly across a roadmap would fund the wrong thing first; this one is ordered by what each dollar retires, and the cheapest experiments come before the expensive one.
> **How to read it** — the sequencing in §2 is the argument. A skeptic should check that no block funds work that a cheaper experiment could have made unnecessary.
> **Depends on / feeds** — inherits [../validation/experiment_board.md](../validation/experiment_board.md), [../product/features_prioritized.md](../product/features_prioritized.md) Build math, [unit_economics.md](unit_economics.md); feeds `narrative/pitch_deck.md` slide 14, [comps_exits.md](comps_exits.md).

## 1 · The raise

**Pre-seed, `(assumption: $750k–1.2M)`** — sized to reach one measured result plus a first paid pilot, with runway past it rather than up to it.

**Why not more.** A larger round funds hiring and channel spend before E1 returns a number, and E1 can return a negative. **A company that has raised $3M against an unmeasured core mechanism has to keep going; one that has raised $1M can publish the negative and stop.** That optionality is worth the dilution difference.

**Why not less.** The build floor to the harness plus the transfer test is ~40 weeks solo [../product/features_prioritized.md](../product/features_prioritized.md), and month 12 for a first paid pilot holds only at every item's optimistic bound. A round that ends at month 12 ends exactly when the evidence arrives.

## 2 · Milestone-linked spend

Each block names what it retires. **Ordered by cost, not by importance** — three company-killing assumptions cost under $2,000 to test and none of them needs code.

| # | Block | Spend | Months | What it retires |
|---|---|---|---|---|
| **B1** | **Discovery + cheap experiments** | ~$5k | 1–2 | **E3** (does the fee have a basis), **E4** (is the channel even open), **E5/X25** (can our own envelope be re-identified), **E8** (ticket mix, ±40% of SAM). Any one negative reshapes the company before a line of code |
| **B2** | Founder salary + the Now-tier build | ~$420k | 2–10 | The pipeline: capture, typing, clustering, synthesis, the stub executor, the **harness first** |
| **B3** | **E1 + E2** | ~$15k | 10–12 | **The core mechanism, measured.** Contract engineers for the transfer test; the fallback-enabled RPA baseline for E2 |
| **B4** | Security and compliance groundwork | ~$60k | 6–18 | SOC 2 Type II — a 6–12 month clock that gates enterprise-adjacent clients *and* the marketplace, and cannot be compressed later |
| **B5** | First pilots + node hardware credits | ~$40k | 12–18 | E7 (review cycle time), the hardware-credit hybrid tested commercially |
| **B6** | First hire — **MSP-side operator** | ~$180k | 14–24 | Closes the gap A6 names. **Not an engineer** |
| **B7** | Reserve | ~$100k | — | The 40-week floor is a floor |

**B1 costs 0.5% of the round and can invalidate the other 99.5%.** That is the whole sequencing argument.

## 3 · Hires, in order

1. **MSP-side operator / founding GTM** (month ~14). The founder story names this gap explicitly; it does not close by reading.
2. **Systems engineer** (month ~18), for the node fleet — D09's on-call obligation arrives with the first deployment and lands on one person until this hire.
3. **Nobody before E1 returns a number.** Hiring against an unmeasured mechanism converts optionality into obligation.

## 4 · Capital-efficiency metric to report

**Dollars per assumption retired**, not burn multiple or ARR per dollar — neither of which means anything pre-revenue.

| Assumption | Cost to retire |
|---|---|
| R3 pricing basis | ~$0 |
| R4 channel admissibility | ~$0 |
| R5 envelope re-identification | ~$8k |
| R8 ticket mix | ~$0 |
| **R1 core mechanism** | **~$435k** (the build is the cost) |

**This table is the fundraising argument.** Four of five company-killing assumptions retire for under $10k; the fifth is the company. A round that funds them in that order is efficient regardless of what it discovers.

## 5 · What the next round needs this one to prove

A seed requires **three** things, and only one is a number:

1. **E1 ≥70%** — cross-environment transfer measured, published, and honest either way.
2. **A repeatable acquisition motion** — 3 paying MSPs through the same channel, with CAC inside the ceiling `unit_economics.md` computes.
3. **Expansion without a sales conversation** — environment 2 onward at ≤6 weeks review cycle, because that is what makes the revenue model work and it is gated by throughput rather than selling.

**What it explicitly does not require: autonomy, a large logo, or a blended 10× claim.** All three are excluded by decisions this pack has already made, and a seed story that reintroduced them would contradict the pre-seed story that raised on their absence.

**Recommended next 3:** (1) run B1 in month one — it is 0.5% of the round and it gates the rest; (2) start B4's SOC 2 clock in month six even though it feels early, because it gates two channels and cannot be compressed; (3) report dollars-per-assumption-retired to investors monthly — it is the only efficiency metric that is meaningful before revenue.
