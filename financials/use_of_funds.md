# Use of funds

> **What this is** — the raise: amount, an 18–24 month milestone-linked spend plan where each block buys a named de-risking result, hires in order, the capital-efficiency metric to report, and what the next round's story requires this one to prove.
> **Why it exists** — this company has one question and a long build. A use-of-funds that spreads money evenly across a roadmap would fund the wrong thing first; this one is ordered by what each dollar retires, and the cheapest experiments come before the expensive one.
> **How to read it** — the sequencing in §2 is the argument. A skeptic should check that no block funds work that a cheaper experiment could have made unnecessary.
> **Depends on / feeds** — inherits [../validation/experiment_board.md](../validation/experiment_board.md), [../product/features_prioritized.md](../product/features_prioritized.md) Build math, [unit_economics.md](unit_economics.md); feeds `narrative/pitch_deck.md` slide 14, [comps_exits.md](comps_exits.md).

## 1 · The raise

**Pre-seed, $900k–1.2M.** The earlier version said $750k–1.2M and its own blocks summed to $820k — **$70k underwater at the floor before anything slipped**, with the reserve then covering under a month of burn. The floor is raised and the plan below now totals to a stated figure.

**Two structural holes the earlier version also had, both fixed:** there was **no founder compensation for months 11–24** in an 18–24 month plan (B2 ended at month 10), and the reserve was a round number rather than sized against the slip it insures — `product/features_prioritized.md` puts midpoints "past 55 weeks", a ~3.5-month overrun costing ~$165k at B2's rate.

**Why not more.** A larger round funds hiring and channel spend before E1 returns a number, and E1 can return a negative. **A company that has raised $3M against an unmeasured core mechanism has to keep going; one that has raised $1M can publish the negative and stop.**

**Why not less.** The build floor to the harness plus the transfer test is ~40 weeks solo, and month 12 for a first paid pilot holds only at every item's optimistic bound. A round ending at month 12 ends exactly when the evidence arrives.

## 2 · Milestone-linked spend

Ordered by cost, not importance. **Three company-killing assumptions cost under $2,000 to test and none needs code.**

| # | Block | Spend | Months | What it retires |
|---|---|---|---|---|
| **B1** | Discovery + cheap experiments | **$5k** | 1–2 | **E3** (does the fee have any basis), **E4** (is the channel open at all), **E5/X25** (envelope re-identification), **E8** (ticket mix and the automatable subset's real cost) |
| **B2** | Founder comp + Now-tier build | **$420k** | 2–10 | The pipeline, harness first. `(assumption: $150k founder comp + ~$270k contract engineering and infra = $420k. **The contract line is deliberate and it qualifies the solo framing**: it buys specialist help on DD2 typing and the harness without a hire, and it does NOT compress the ~40-week floor, which is why B7 is unchanged)` |
| **B2b** | **Founder comp, months 11–24** | **$175k** | 11–24 | Nothing — it is the cost of existing while the evidence arrives. **The earlier version simply omitted it** |
| **B3** | E1 + E2 | $15k | 10–12 | **The core mechanism, measured** |
| **B4** | Security groundwork | **$60k**, of which ~$15k at month 6 | 6–18 | Policy and platform first; the **Type II audit spend waits for X16 (tenant isolation) to ship** — a Type II requires controls operating over a real production system, and at month 6 there is none |
| **B5** | First pilots + node + **contracted on-call backstop** | **$70k** | 12–18 | E7 review cycle time; the hosted-node option; and **six months of 24/7 cover on customer infrastructure before the month-18 systems hire** — asserted in §3 and previously unfunded. The $800/yr node-ops line in `unit_economics.md` is per-MSP COGS at scale, not the fixed cost of first cover |
| **B6** | First hire — **MSP-side operator** | $180k | **on E1 ≥70%, not before month 14** | Closes the A6 gap. **Milestone-gated, not date-gated** — the earlier version fired the largest discretionary commitment before E1 returned, breaking this file's own rule |
| **B7** | Reserve | **$165k** | — | Sized to the 55-week midpoint slip, not to a round number |
| | **Plan case total** | **$1,090k** | | |
| | **Reduced-scope case** (B6 deferred) | **$910k** | | Reaches E1 and a first pilot; defers the hire to a seed |

**B1 is 0.5% of the plan-case round and can invalidate the other 99.5%.** *(E5's ~$8k adversarial testing is funded from B3 rather than B1, which covers the four conversation-based experiments.)*

## 3 · Hires, in order

1. **MSP-side operator / founding GTM** (month ~14). The founder story names this gap explicitly; it does not close by reading.
2. **Systems engineer** (month ~18), for the node fleet — the on-call obligation (D6/N15, drawn in `tech/architecture/D09.md`) arrives with the **first deployment**, not with this hire, so months 12–18 need a contracted on-call backstop priced into B5 rather than one person's phone.
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

**Recommended next 3:** (1) run B1 in month one — it is 0.5% of the round and it gates the rest; (2) start B4's **policy and platform work** at month six — the Type II audit spend itself waits for X16 to ship, per the split above, so the clock that cannot be compressed is the controls-operating window, not the whole programme; (3) report dollars-per-assumption-retired to investors monthly — it is the only efficiency metric that is meaningful before revenue.
