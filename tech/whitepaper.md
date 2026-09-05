# Whitepaper — where the leverage actually is

> **What this is** — the mechanism argument: which frictions consume an MSP's engineering capacity, which mechanisms remove each, what multiplier each produces, and — stated first because it is what a skeptic checks — **which friction this system does not touch.**
> **Why it exists** — every "10x" claim in this category is asserted on a total, and falls apart when a customer measures the total. This paper locates the leverage precisely: it is on **knowledge maintenance and reuse**, not on first-environment onboarding, where the system is measurably *worse* than doing nothing. A paper that claimed the headline number would be falsified by the first design partner's timesheet (D8).
> **How to read it** — §1 then §4. A skeptic should attack §2's multiplier bands, all of which are targets rather than measurements, and §3's honest ceiling.
> **Depends on / feeds** — inherits [../research/survey.md](../research/survey.md), [../research/capability_table.md](../research/capability_table.md), [../product/PRD.md](../product/PRD.md), the claim boundary D1 and the ROI-honesty directive D8; feeds [deep_dives.md](deep_dives.md), [architecture/00_INDEX.md](architecture/00_INDEX.md), `narrative/vc_memo.md`.

## Executive summary

An MSP's engineering capacity is consumed by a knowledge cycle, not by a knowledge cost: environment knowledge is **acquired** per client, **decays** continuously, is **lost** on attrition, and is then **re-acquired**. The cycle repeats 41 times per MSP and never terminates.

Understudy does not make acquisition cheaper. **It makes acquisition happen once.**

**There is no 10×, and the first version of this paper claimed one it could not support.** It located the multiplier on documentation-maintenance hours — against a baseline this paper's own §1 describes as "largely unperformed". An 8× on hours nobody spends displaces no cost, and the strategy layer had already rejected charging for that line on precisely those grounds. The claim is withdrawn.

What survives is smaller, measurable, and stated as four separate things because they do not combine into one:

| | Effect | **Absolute, per MSP per year** | Kind |
|---|---|---|---|
| **M1** repeat-environment onboarding | **~1.4×** (25–40 hrs → 18–28) | **~42–72 hrs saved** (6 new clients/yr) | a real hours multiplier, derived below |
| **M2** documentation that is *true* rather than cheaper | risk reduction | **unquantified until measured** | re-baselined; see §2 |
| **M3** knowledge survives attrition | structural | unquantified, bounded by capture coverage | not a multiplier |
| **M4** tier-1 repetitive execution | ~25% of ticket volume, supervised | ~124 tickets/month addressed | a capacity shift, not hours |
| **M5** global layer | ~10–12% of a *new customer's* first onboarding | **year-two mechanism**, see §2 | cross-customer, and the only one |

**Every ratio in this paper is shown beside its absolute magnitude**, because the first version's headline multiplier was large only because its base was tiny — and that is the specific way a mechanism paper misleads without stating anything false.

And first-environment onboarding gets *worse* by about 20%. That is why this paper is credible: the system's cost falls exactly where the category's marketing puts its gains.

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

**A note on tags.** The first version marked every multiplier `(target)`, which is not one of the two tags quality-bar property 2 permits. Each is now either sourced or carries `(assumption: <basis>)`. **Standing rule adopted here: no figure below may be used as an input to `financials/` until E1 or E2 returns a measurement.**

### M1 · Observation replaces re-derivation → attacks F1, at environment *n+1*

Procedure shapes learned at one environment transfer to the next on the same stack; only the deviations are new.

**Derived rather than asserted.** `(assumption: ~30% of a median onboarding is environment discovery — mapping the tenant, finding its deviations, writing them down; the remaining ~70% is mechanical setup — RMM deployment, monitoring, backup verification — that observation does not touch)`. Applying that to the 25–40-hour median band gives **17.5–28 hours, i.e. 18–28**, and a multiplier of **25/18 = 1.39 to 40/28 = 1.43 → ~1.4×**. The first version quoted "1.3–1.6×", a band neither of whose endpoints its own figures reach.

**Not 10×, and the reason is structural:** most of an onboarding is mechanical setup — RMM deployment, monitoring, backup verification — that observation does not touch. Only the *figure out how this client differs* portion compresses. A paper claiming otherwise is claiming to automate work it never sees.

### M2 · Documentation that is true, not documentation that is cheaper → attacks F2

Documentation decays because keeping it current is a separate act from doing the work. Capture makes them the same act.

**The multiplier claimed here has been withdrawn.** The first version claimed 8–12× on maintenance hours. But §1's own F2 row says the ~8 hrs/month baseline is *"largely unperformed — most MSPs pay this in wrong documentation rather than in hours"*, and [../strategy/market_sizing.md](../strategy/market_sizing.md) formally rejected pricing against this line because the saving is roughly 12 minutes per environment per month. **A multiplier on hours nobody spends displaces no cost, and the two statements could not both stand.**

**Re-baselined on what the wrongness actually costs**, which is measurable and is not hours of upkeep:

- **Repeat escalations** — the same problem re-solved at a second client because the first solution reached nobody. Measurable as escalation rate per procedure per environment, from day one of shadow mode.
- **Rework** — a technician following stale documentation, doing the wrong thing, and redoing it.
- **Time-to-competence** — how long a new engineer takes to work safely in an unfamiliar client.

**M2 is therefore a risk-reduction claim, not a productivity multiplier**, and no figure is quoted for it until the escalation-rate baseline is measured in the first pilot. That is a weaker claim than the one it replaces, and it is the one the evidence supports.

### M3 · Capture converts individual knowledge into an owned asset → attacks F3

When an engineer leaves, procedures they authored remain, attributed and endorsed. **Effect: F3's re-acquisition cost approaches zero for captured procedures.** Not a multiplier — a risk that is removed rather than a cost that shrinks. `(assumption: unmeasured; bounded by capture coverage, below)`

**Honest limit:** only for procedures that were *performed during the capture window*. A procedure exercised once a year at one client is not in the library when the engineer leaves. Coverage, not mechanism, bounds this.

### M4 · Supervised execution on the repetitive class → attacks F4

Skills execute the tier-1 repetitive segment under gates, with verification. **Multiplier: ~25% of ticket volume addressable** `(assumption)`, at supervised — not unattended — throughput.

**Bounded by evidence, not ambition** (D1): long-horizon agent completion is 20.6% [S16] and agents at ~85% on OSWorld still fail ~80% of real workflows [S15]. This paper claims the repetitive, short-horizon, verifiable segment and nothing else.

### M5 · The global layer → the only cross-customer mechanism, and it was missing

M1–M4 are all **intra-MSP**: they improve a customer's own book using that customer's own data, which is the customer's asset, not ours. The first version of this paper never gave the global layer a mechanism of its own — which meant the moat existed in the strategy deck and nowhere in the engineering.

**What it contributes.** A procedure shape that has cleared the k≥3 threshold tells a *new* customer's first environment which patterns to expect on a given stack — it pre-solves shape identification, though never the tenant-specific deviation, which by construction is not in the envelope. `(assumption: shape identification is ~30–40% of the discovery portion of an onboarding; discovery is ~30% of the total, so the global layer removes ~10–12% of a first onboarding)`.

**This reconciles two statements that previously contradicted each other.** [architecture/D01.md](architecture/D01.md) says global shapes make environment *n+1* start warmer; §4.1 says first-environment onboarding is *slower*. Both hold, because they describe different indices: **environment 1 of customer 10 is cheaper than environment 1 of customer 1** — and both are still worse than doing nothing, because the mechanical setup is unchanged and review work is added. The global layer shortens the penalty; it does not remove it.

**The cold start is long, and an earlier draft of this section got it backwards.** It argued that because the threshold counted distinct *tenants* and one MSP brings ~41, a single customer could populate the global layer alone — and called that the paper's most encouraging finding. **It was a privacy hole described as a feature.** If three observations of a pattern can all sit inside one design partner's book, the envelope identifies that MSP with certainty, at exactly the moment of its first security review.

**The threshold now counts distinct MSPs** (`m≥3`, see [deep_dives.md](deep_dives.md) DD4). The consequence is that **the global layer contributes nothing until customer 3, and little until customer 5–10** — so M5 is a year-two mechanism, not a year-one one. Every M1–M4 effect is intra-MSP and available from customer 1; the cross-customer moat arrives later than the strategy layer's compounding story implies, and `strategy/lean_canvas.md`'s time-to-parity estimate should be read against this, not against the earlier version.

**Why the incumbent does not already have this.** Automation Anywhere bought FortressIQ [S5] and therefore owns a capture footprint and years of recorded enterprise work. **They could build this, and nothing here prevents it.** Two things stand in the way and neither is permanent: their executor is RPA, whose failure record is the reason discovery stalled at documents [S10][S11]; and their buyer is the enterprise process team, not IT service delivery, so an MSP-shaped motion is a new market for them rather than an extension. **Publishing our evaluation method — which §2 of `not_vaporware.md` recommends — hands them the yardstick too.** That is a deliberate trade: a category with a public benchmark is one where our result is checkable, and we would rather compete on a measured axis than on marketing claims we cannot verify either.

### Conservative × conservative

Taking the low end of every band, for an MSP at steady state:

| Line | Before | After | Effect |
|---|---|---|---|
| Repeat-environment onboarding (6 new clients/yr) | 150–240 hrs | 108–168 hrs | **~1.4×** — the only hours multiplier in the paper |
| First-environment onboarding | 25–40 hrs | 31–46 hrs | **0.8× — worse** |
| Documentation correctness | stale, unquantified | maintained by observation | **risk reduction, unquantified until measured** |
| Re-acquisition after attrition | full F1 cost, unpredictable | near zero for captured procedures | **structural** |
| Tier-1 repetitive execution | manual | ~25% supervised | **capacity, not hours** |

**The honest aggregate is one multiplier of ~1.4×, one negative, and three effects that are not multipliers at all.** Anyone quoting a blended figure from this table is misusing it, and the first version of this paper invited that by claiming a 10× on the maintenance line.

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

**Two more absolutes have been withdrawn here — this argument has now been corrected three times, which is itself worth knowing.** The earlier version claimed RPA asserts only about the interface and that a broken selector leaves "nothing to aim at". A UiPath practitioner falsifies both in one sentence: bots routinely assert on **world state** (create an AD object, then query AD or an API to confirm it), the REFramework's BusinessRuleException/SystemException split exists precisely to separate *the outcome is wrong* from *the interface broke*, and **Unified Target already recovers from broken selectors** through fuzzy, anchor, image and OCR fallbacks tried in sequence. Our own wave-1 catalogue lists those fallbacks, so the earlier version argued against a technique list we wrote ourselves.

**The narrower claim survives, and it still wins.** The difference is not whether RPA can check a goal or recover from a break — it can do both. It is that **the goal is not carried in the RPA artifact in a form the runtime can re-plan against.** Recovery is therefore confined to fallbacks a developer enumerated in advance; when the change falls outside that enumeration, the run stops. A skill carries the goal as a **predicate the runtime holds at execution time**, so recovery is a search over a space nobody had to anticipate.

That is a smaller claim than "RPA cannot recover", and it is the one that survives the room.

**It is tested, not asserted — and the fairness bar has been raised.** `validation/experiment_board.md` E2 executes synthesized skills against a deliberately altered UI — moved, renamed and re-ordered elements plus a version upgrade that changes selectors — against an RPA baseline on the identical alteration. **D5 originally required only that the baseline be "selector-based", which would permit one with its fallbacks disabled. That is no longer sufficient: the baseline must be a Unified-Target-equivalent implementation with fuzzy, anchor and image fallbacks enabled**, or a practitioner falsifies the result on sight. The experiment is worth running only if it can lose.

**What this does not claim.** Re-grounding is not immunity. Environment drift still degrades skills (`P4`), which is why drift detection pauses a skill before it acts wrongly rather than trusting re-grounding to always succeed. The claim is a difference in *failure mode*, not the elimination of failure.

**Recommended next 3:** (1) run E2 before any customer conversation — §5 is the section that converts technical evaluators and it is currently an argument, not a result; (2) instrument M2's maintenance line first, since it carries the only genuine 10× and does not depend on the executor working; (3) publish §4 unedited in the investor materials — a paper whose limits section is longer than its claims section is the one that survives diligence.
