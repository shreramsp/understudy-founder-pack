# Product requirements — Understudy · v0.1 · 2026-09-04

> **What this is** — the product definition: the closed core loop, the principles every feature must obey, the superset feature set organised by loop phase, and the metrics that say whether it works.
> **Why it exists** — this product's failure mode is not missing features, it is building a recorder that produces plausible skills nobody trusts enough to run. The first-principles section (§4) exists to make that failure structurally hard: a feature that maps to no principle gets cut, and the principles are drawn from why forty years of prior attempts failed rather than from what would be nice to have.
> **How to read it** — §4 then §5; the principle tags in §5 are the argument that this is engineering rather than a wish list. A skeptic should attack principle P5, which concedes the product cannot do the thing the category is excited about.
> **Depends on / feeds** — inherits [BRIEF.md](../BRIEF.md) (incl. the binding claim boundary D1 and pricing D4), [research/survey.md](../research/survey.md), [research/capability_table.md](../research/capability_table.md), [strategy/personas.md](../strategy/personas.md); feeds [features_flagship.md](features_flagship.md), [features_prioritized.md](features_prioritized.md), [journeys/](journeys/), [ux_spec.md](ux_spec.md), `tech/`.

## 1. Executive summary & vision

Understudy learns an unfamiliar IT environment by watching engineers work in it, and then does the repetitive part of that work under supervision. It closes a loop the market has left open in two halves: discovery tools observe and emit documents, resolution tools execute but must be configured [research/landscape.md](../research/landscape.md).

**The core loop, in this domain's own verbs:**

```
   WATCH ──→ DISTIL ──→ REHEARSE ──→ GATE ──→ ACT ──→ VERIFY
     ↑                                                    │
     └──────────────── LEARN ←────────────────────────────┘
```

| Phase | What happens | The unit that moves |
|---|---|---|
| **Watch** | Passive capture of an engineer's session: screen, actions, and optional spoken reasoning | a *session* |
| **Distil** | Cluster sessions of the same procedure across engineers and environments; synthesize one readable `SKILL.md` with a goal, steps, and a **verification step** | a *skill* |
| **Rehearse** | Run the skill in shadow against real tickets, in parallel with the human, comparing outcomes without acting | a *rehearsal* |
| **Gate** | Approval policy per skill and per action class; destructive actions always gated | a *gate decision* |
| **Act** | Execute under the agent's own identity, within the skill's declared envelope, escalating anything outside it | an *action* |
| **Verify** | Check the declared success criterion; on failure, re-ground rather than halt, and record the deviation | a *verification* |
| **Learn** | Every deviation, escalation and correction widens the skill's **variance envelope** | an *envelope update* |

**Vision.** MSPs run many more clients per engineer because environment knowledge stops being something a person holds and becomes something the business owns — observed, readable, and executable.

## 2. Goals

1. Reduce engineer-hours to onboard a client environment, measurably, against the 40–80 hours it costs today [S21].
2. Produce skills a principal engineer will read and endorse — trust is the adoption gate, not accuracy alone.
3. Make each environment onboard faster than the last (the variance envelope compounding, A8).
4. Execute tier-1 repetitive work under supervision with a verified success criterion on every action.

## 3. Non-goals — real renunciations

- **Not unattended autonomous resolution.** Binding claim boundary (D1). Long-horizon completion is 20.6% [S16]; supervision is not a stepping stone we remove, it is the architecture.
- **Not a ticketing system.** We sit beside the PSA/ITSM, we do not replace it. Displacing the desk is a year-two fight [strategy/petal_diagram.md](../strategy/petal_diagram.md).
- **Not a documentation product.** The library is executable or it is nothing; a skill that cannot run is a failed skill, not a document.
- **Not browser-only.** The surface is RMM consoles, AD, terminals, MDM and native admin tools — this is precisely where Strawberry's approach stops [S25].
- **Not model training.** Skills are text under an open format [S24]; no customer data enters a training loop, which is also what makes the security answer sayable.
- **Not EU at launch.** Continuous screen recording faces disproportionality findings and works-council co-determination [S29] (A12/D3).

## 4. First-principles grounding — non-negotiable

Every major feature must map to one or more of these. **A feature that maps to none gets cut, or the principle list was wrong.** Drawn from [research/survey.md](../research/survey.md).

| # | Principle | Why it is true | Source |
|---|---|---|---|
| **P1** | **A demonstration underdetermines intent.** What was essential and what was incidental to that run cannot be recovered from actions alone | The failure that sank forty years of programming-by-demonstration | survey §1 |
| **P2** | **Happy paths are not procedures.** Recovery behaviour, aborted attempts and failure branches are exactly what a successful recording does not contain | survey §7 | survey §7 |
| **P3** | **A contract without a success criterion fails silently.** An RPA step says what to do, not what "done correctly" looks like, so a broken assumption produces a wrong outcome rather than an error | Selector contracts break on upgrades, dynamic ids, timing, drift, unhappy paths | survey §1, §6.3; D5 |
| **P4** | **Environments drift continuously.** A skill library is a maintenance liability from the day it is written | RPA maintenance reaches 60% of total implementation cost | [S11] |
| **P5** | **Long-horizon autonomy is not available.** Best frontier completion on long-horizon tasks is 20.6%, and agents at ~85% on standard benchmarks still fail ~80% of real workflows | Benchmarks are curated; client environments are not | [S15][S16] |
| **P6** | **Procedural knowledge must be readable to be trusted.** An engineer will not endorse what they cannot inspect and correct | The open `SKILL.md` format makes this structural rather than a UI choice | [S24]; personas §4 |
| **P7** | **The variance envelope is the asset.** The happy-path procedure is in vendor documentation; how it differs across real environments is not | The moat, restated after critic round 1 | [strategy/lean_canvas.md](../strategy/lean_canvas.md) |
| **P8** | **Recording is a consent relationship, not a data pipeline.** The person being recorded must benefit, visibly, or capture quietly degrades | The champion and the edge-high persona are the data source | personas §3, §4 |
| **P9** | **Destructive actions are irreversible; verification precedes action.** IT operations delete mailboxes and disable accounts | Silent wrongness is worse than loud failure | survey §7 |

## 5. Core feature set by loop phase

Each feature tagged with the principles it serves.

### Watch
- **Multi-surface session capture** — screen, input events and window/application context across RMM consoles, AD, terminals, MDM and native admin UIs, not just the browser. `P1`
- **Narration capture** — optional voice, prompted at decision points rather than continuously; the direct attack on P1's underdetermination. `P1 P8`
- **Engineer-controlled capture** — visible indicator, pause, and post-session review before anything is distilled. `P8`
- **Escalation and abort capture** — sessions that *failed* are retained deliberately, because they contain what successes do not. `P2`

### Distil
- **Cross-session clustering** — group recordings of the same procedure across engineers and environments; the company's core technical bet, with no benchmark to inherit [capability_table row 5]. `P1 P7`
- **Skill synthesis to `SKILL.md`** — goal, preconditions, steps, **declared success criterion**, and escalation envelope. `P3 P6`
- **Variance envelope extraction** — record how the same procedure differed across environments; this is the asset, not a by-product. `P7`
- **Authorship attribution** — every skill names the engineers whose sessions produced it. `P8`

### Rehearse
- **Shadow mode** — the skill runs against live tickets without acting, and outcomes are compared with the human's. `P5 P9`
- **Deviation report** — where the skill would have diverged, surfaced to the authoring engineer for correction. `P2 P6`

### Gate
- **Action-class policy** — read / reversible-write / destructive, with destructive always gated regardless of confidence. `P9`
- **Envelope enforcement** — an action outside the skill's declared preconditions escalates rather than improvising. `P5`

### Act
- **Agent identity** — its own principal, so every action is attributable in the client's audit log. `P8 P9`
- **Test-account self-exploration** — bounded discovery of the environment beyond what was recorded, read-only by default. `P1 P4`

### Verify
- **Success-criterion check** — every action ends by testing the declared criterion; this is what P3 says RPA lacks. `P3 P9`
- **Re-grounding on failure** — a changed UI triggers a search against the intact goal, not a halt. `P3 P4`

### Learn
- **Envelope widening** — deviations, escalations and corrections update the skill's variance envelope. `P4 P7`
- **Drift detection** — a skill whose verification starts failing flags before it acts wrongly. `P4 P9`

## 6. Data and the learning flywheel

**Per environment (private tenant layer):** the skills specific to that client, their variance, their drift history. Never leaves the tenant boundary.
**Global layer:** procedure shapes and variance patterns for common stacks, carrying no client data. This is the half that compounds and the half a security review must be able to reason about.

**The open architecture question with direct revenue consequence:** where clustering runs. If it can execute inside the client boundary, or on redacted derivatives that never leave it, the ~6-week per-environment security review shortens dramatically and expansion velocity — which gates the revenue ramp — improves materially [strategy/sales_roadmap.md](../strategy/sales_roadmap.md). **Owed to `tech/architecture/`. It is a product requirement, not an implementation detail.**

## 7. Oversight, safety, privacy, compliance

- **Capture consent surface** — engineers see what is captured, can pause, and review before distillation (P8).
- **Client-side transparency** — the MSP's client can be shown what is recorded in their environment and what leaves it; this is Sonia's question and it is a product feature, not a sales document.
- **Destructive-action gating** — always on, not configurable to off.
- **Audit trail** — agent identity, skill version, verification result per action.
- **Retention policy** — raw sessions expire; distilled skills persist. Raw admin-plane recording is the highest-sensitivity artifact in the system and should have the shortest life.
- **Geography** — US-first; EU capture is constrained by disproportionality findings and works-council rights [S29].

## 8. Success metrics

**Outcome metrics first — the domain's real "did it work":**
1. **Engineer-hours to onboard an environment**, against the 40–80-hour baseline [S21]. The number the buyer feels.
2. **Time-to-first-verified-skill** in a new environment — the category yardstick nobody publishes [research/survey.md §4].
3. **Cross-environment skill reuse rate** — A8 made measurable, and the earliest read on whether the moat exists.
4. **Verified-action accuracy** — actions whose success criterion passed *and* were correct on human review. Silent wrongness is the metric that matters, not throughput.

**Engagement:** sessions captured per engineer per week; skills endorsed by their authoring engineer (P8 working or not); shadow-to-gated promotion rate.

**Business:** environments onboarded per MSP (the expansion metric on which the revenue ramp depends); resolved tickets per environment; revenue per MSP against the ~$8,600 year-1 model [strategy/market_sizing.md](../strategy/market_sizing.md).

**Recommended next 3:** (1) build Watch and Distil only, and prove clustering on lab environments before any Act surface exists; (2) settle the clustering-location question in `tech/architecture/` — it gates security review length and therefore the whole ramp; (3) instrument reuse rate and variance-envelope growth from environment #2, since together they are the only early evidence for A8.
