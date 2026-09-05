# Whitepaper — where the leverage actually is

> **What this is** — the mechanism argument: which frictions consume an MSP's engineering capacity, which mechanisms remove each, what multiplier each produces, and — stated first because it is what a skeptic checks — **which friction this system does not touch.**
> **Why it exists** — every "10x" claim in this category is asserted on a total, and falls apart when a customer measures the total. This paper locates the leverage precisely: it is on **knowledge maintenance and reuse**, not on first-environment onboarding, where the system is measurably *worse* than doing nothing. A paper that claimed the headline number would be falsified by the first design partner's timesheet (D8).
> **How to read it** — §1 then §4. A skeptic should attack §2's multiplier bands, all of which are targets rather than measurements, and §3's honest ceiling.
> **Depends on / feeds** — inherits [../research/survey.md](../research/survey.md), [../research/capability_table.md](../research/capability_table.md), [../product/PRD.md](../product/PRD.md), the claim boundary D1 and the ROI-honesty directive D8; feeds [deep_dives.md](deep_dives.md), [architecture/00_INDEX.md](architecture/00_INDEX.md), `narrative/vc_memo.md`.

## Executive summary

An MSP's engineering capacity is consumed by a knowledge cycle, not by a knowledge cost: environment knowledge is **acquired** per client, **decays** continuously, is **lost** on attrition, and is then **re-acquired**. The cycle repeats 41 times per MSP and never terminates.

Understudy does not make acquisition cheaper. **It makes acquisition happen once.** The leverage is in breaking the decay-and-reacquire loop, and in transferring what was acquired at client *n* to client *n+1*. Conservative estimates put the compounded effect at **6–11× on the knowledge-maintenance line** and **roughly 30% on repeat-environment onboarding** — while first-environment onboarding gets *worse* by about 20%.

That last clause is why this paper is credible. The system's cost falls exactly where the category's marketing puts its gains.

## §1 The current inefficiency — four frictions that compound

| # | Friction | Magnitude | Source |
|---|---|---|---|
| **F1** | **Acquisition.** Every new client environment is re-derived from scratch: mapping the tenant, discovering its deviations, writing it down | **25–40 engineer-hours** for a median (≈16-user) client; 40–80 for a complex one | [S21], banded per D7 |
| **F2** | **Decay.** Documentation is stale on arrival and needs continuous upkeep that nobody does | `(assumption: ~8 hrs/month per MSP of nominal upkeep, largely unperformed)` — the honest figure is that most MSPs pay this in *wrong* documentation rather than in hours | — |
| **F3** | **Loss.** Environment knowledge lives in individuals; attrition removes it entirely | A departing senior engineer takes years of tenant-specific knowledge. 22% of MSPs cannot find replacement technical talent | [S33] |
| **F4** | **Repetition without leverage.** The same ~20 procedures execute across 41 environments, manually, forever | ~496 tickets/month/MSP; ~25% within the tier-1 repetitive class | [S34], `(assumption)` per `strategy/market_sizing.md` |

**Why they compound rather than add.** F3 resets F1: when the engineer holding an environment leaves, its acquisition cost is paid again, at full price. F2 guarantees F3's damage is unmitigated — the documentation that should have preserved the knowledge does not describe the current environment. F4 pays a small tax on every ticket that F1's knowledge would have removed. The cycle is:

```
   acquire (F1) ──→ decays (F2) ──→ lost on attrition (F3) ──→ re-acquire (F1) ──→ …
                          │
                          └──→ every ticket pays the gap (F4)
```

**An MSP is not paying an onboarding cost. It is servicing a knowledge debt with no principal repayment.**

## §2 Mechanisms and their multipliers

Each mechanism, the evidence for it, and the multiplier with a confidence band. **Bands are targets, not measurements — no pilot exists** [../research/capability_table.md](../research/capability_table.md) row 5 records that the core mechanism has no benchmark to inherit.

### M1 · Observation replaces re-derivation → attacks F1, at environment *n+1*

Procedure shapes learned at one environment transfer to the next on the same stack; only the deviations are new. **Multiplier: 1.3–1.6× on repeat-environment onboarding** (25–40 hrs → 18–28). `(target)`

**Not 10×, and the reason is structural:** most of an onboarding is mechanical setup — RMM deployment, monitoring, backup verification — that observation does not touch. Only the *figure out how this client differs* portion compresses. A paper claiming otherwise is claiming to automate work it never sees.

### M2 · Maintenance by observation replaces maintenance by discipline → attacks F2

Documentation decays because keeping it current is a separate act from doing the work. Capture makes them the same act. **Multiplier: 8–12× on the knowledge-maintenance line** (~8 hrs/month → ~40 min/month of deviation review). `(target)`

**This is where the 10× actually lives**, and it is the least glamorous line in the business. It is also the most defensible, because it does not depend on the agent executing anything — only on distillation working.

### M3 · Capture converts individual knowledge into an owned asset → attacks F3

When an engineer leaves, procedures they authored remain, attributed and endorsed. **Multiplier: F3's re-acquisition cost approaches zero for captured procedures.** `(target)`

**Honest limit:** only for procedures that were *performed during the capture window*. A procedure exercised once a year at one client is not in the library when the engineer leaves. Coverage, not mechanism, bounds this.

### M4 · Supervised execution on the repetitive class → attacks F4

Skills execute the tier-1 repetitive segment under gates, with verification. **Multiplier: ~25% of ticket volume addressable** `(assumption)`, at supervised — not unattended — throughput.

**Bounded by evidence, not ambition** (D1): long-horizon agent completion is 20.6% [S16] and agents at ~85% on OSWorld still fail ~80% of real workflows [S15]. This paper claims the repetitive, short-horizon, verifiable segment and nothing else.

### Conservative × conservative

Taking the low end of every band, for an MSP at steady state:

| Line | Before | After | Effect |
|---|---|---|---|
| Repeat-environment onboarding (6 new clients/yr) | 150–240 hrs | 108–168 hrs | **~1.3×** |
| Knowledge maintenance | ~96 hrs/yr | ~8–12 hrs/yr | **~8×** |
| Re-acquisition after attrition | full F1 cost, unpredictable | near zero for captured procedures | **structural** |
| Tier-1 repetitive execution | manual | ~25% supervised | **capacity, not hours** |

**The honest aggregate is not a single number.** It is: *one line improves ~8×, one improves ~1.3×, one risk is largely removed, and one is a capacity shift.* Anyone quoting a blended "10x" from this table is misusing it.

## §3 Full-spectrum applicability

**Edge-low (tier-1).** Gains most in *capability*, not hours: a client-specific procedure where previously there was a generic runbook and an escalation. Measured as escalation-rate reduction, not time saved.
**Beachhead (delivery manager).** Gains the M2 multiplier directly — the maintenance line is hers.
**Edge-high (principal).** Gains from F3 and F4 removal: fewer repeat interruptions, and the variance envelope as a cross-environment diagnostic. **Loses nothing**, which is the necessary condition for the capture programme to survive (`P8`, and disuse is the documented failure mode [S36]).

The gains hold at both edges because they come from different mechanisms at each — not because one mechanism is claimed to scale across all users.

## §4 What this is not

Read this section before §2 if you are evaluating rather than reading.

1. **It is not faster first-environment onboarding. It is slower.** Environment 1 costs **31–46 hours against a 25–40 baseline** — the work is unchanged and review overhead is added [../product/journeys/beachhead.md](../product/journeys/beachhead.md). Compression begins at environment 2. This is stated in every ROI artifact by founder directive (D8).
2. **It is not unattended automation.** Supervised execution with human escalation, per the binding claim boundary (D1). Not a roadmap position — an architectural one.
3. **It is not a 10× productivity claim.** The 10× is on one line (M2). The headline number moves far less.
4. **The core mechanism is unevidenced.** Cross-session clustering into reliable skills has no benchmark and no named prior system [../research/capability_table.md](../research/capability_table.md) row 5. Everything above is conditional on it.
5. **Cross-environment transfer is an assumption**, not a finding (A8). If procedures do not transfer, M1 collapses to zero and M2 survives — the business would be smaller but not dead.
6. **Coverage bounds M3.** Rare procedures are not in the library when the engineer holding them leaves.
7. **The gains are conditional on capture continuing.** If engineers quietly stop cooperating, input stops and every mechanism degrades. This is a social failure with no technical mitigation [../product/journeys/edge_high.md](../product/journeys/edge_high.md).

## §5 The RPA question — required, and answered as mechanism (D2/D5)

Every technical evaluation asks it, and the base rate is against us: automation derived from observed work fails in 30–50% of projects, with maintenance reaching 60% of total cost [S10][S11].

**State the opposing case accurately first, because a strawman loses the room.** Enterprise RPA does not encode screen coordinates and has not for a decade — UiPath uses attribute-based selectors over the accessibility tree with anchor and CV fallbacks; Blue Prism uses application-modeller matching. It *does* offer success checks: Verify Application State, Check App State, Wait stages with modelled conditions. Anyone claiming RPA has no verification is falsified in one sentence.

**The real difference is what the check is *about*.** An RPA assertion is a statement about **the interface**: *this element exists in this state*. It can detect that something broke; it cannot say what the procedure was trying to achieve. So a broken selector either halts loudly or proceeds wrongly — and neither outcome can recover, because there is nothing left to aim at.

A skill's success criterion is a statement about **the goal**: *the user can complete an MFA challenge from a new device*. When the interface changes, the criterion is still valid, so a break becomes a **re-grounding search against an intact target** rather than a failure. That is the mechanism, and it is the whole claim.

**It is tested, not asserted.** `validation/experiment_board.md` E2 executes synthesized skills against a deliberately altered UI — moved, renamed and re-ordered elements plus a version upgrade that changes selectors — against a **selector-based** RPA baseline on the identical alteration. A coordinate-clicking baseline would rig the result and prove nothing to the only person who matters here.

**What this does not claim.** Re-grounding is not immunity. Environment drift still degrades skills (`P4`), which is why drift detection pauses a skill before it acts wrongly rather than trusting re-grounding to always succeed. The claim is a difference in *failure mode*, not the elimination of failure.

**Recommended next 3:** (1) run E2 before any customer conversation — §5 is the section that converts technical evaluators and it is currently an argument, not a result; (2) instrument M2's maintenance line first, since it carries the only genuine 10× and does not depend on the executor working; (3) publish §4 unedited in the investor materials — a paper whose limits section is longer than its claims section is the one that survives diligence.
