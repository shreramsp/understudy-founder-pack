# Product requirements — Understudy · v0.1 · 2026-09-04

> **What this is** — the product definition: the closed core loop, the principles every feature must obey, the superset feature set organised by loop phase, and the metrics that say whether it works.
> **Why it exists** — this product's failure mode is not missing features, it is building a recorder that produces plausible skills nobody trusts enough to run. The first-principles section (§5) exists to make that failure structurally hard: a feature that maps to no principle gets cut, and the principles are drawn from why forty years of prior attempts failed rather than from what would be nice to have.
> **How to read it** — §5 then §6; the principle tags in §5 are the argument that this is engineering rather than a wish list. A skeptic should attack principle P5, which concedes the product cannot do the thing the category is excited about.
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

1. Reduce engineer-hours to onboard a client environment, measurably, **against that client's own size band** — 15–25 hours small, 25–40 median, 40–80 complex (D7; [strategy/market_sizing.md](../strategy/market_sizing.md)). A single book-average baseline overstates the gain on small clients and understates it on large ones.
2. Produce skills a principal engineer will read and endorse — trust is the adoption gate, not accuracy alone.
3. Make each environment onboard faster than the last (the variance envelope compounding, A8).
4. Execute tier-1 repetitive work under supervision with a verified success criterion on every action.

## 3. Target users — one system, no separate tracks

Full cards in [strategy/personas.md](../strategy/personas.md); this section states them as **requirements**, because `tech/` builds from this file.

| Seat | Role in the system | What the product must do for them | Spectrum position |
|---|---|---|---|
| **Priya** — tier-1 technician | Consumes skills | Surface *this client's* procedure and its deviations inline in the ticket; never present a generic runbook as if it were specific | **Edge-low** |
| **Dana** — service delivery manager | Judges skills | Make most days require no action; make the exceptions unambiguous | **Beachhead core** |
| **Ray** — principal engineer | Authors skills by working; can veto by not cooperating | Readable text he can inspect, correct and reject without justification | **Edge-high** |
| **Marcus** — MSP owner | **Payer, not user** | One number, weekly, true including when it is bad | Buyer |
| **Sonia** — client-side IT director | **Veto, one per client environment** | One boring export, twice a year, plus a structural answer to *what leaves my environment* | External gate |

**Requirement — one adaptive system, no stigmatizing tiers.** There is no "lite" edition for Priya and no "pro" edition for Ray. The same skill library serves all three spectrum positions; what differs is **whether a person is consuming a skill, authoring one by working, or judging one**. Any design that forks the product by user sophistication violates this requirement.

**Requirement — payer ≠ user.** Marcus signs and barely uses it; Ray never signs and can kill it. The product must therefore be independently defensible to a buyer who sees a dashboard and to an expert who sees the internals, and those two surfaces must not contradict each other.

## 4. Non-goals — real renunciations

- **Not unattended autonomous resolution.** Binding claim boundary (D1). Long-horizon completion is 20.6% [S16]; supervision is not a stepping stone we remove, it is the architecture.
- **Not a ticketing system.** We sit beside the PSA/ITSM, we do not replace it. Displacing the desk is a year-two fight [strategy/petal_diagram.md](../strategy/petal_diagram.md).
- **Not a documentation product.** The library is executable or it is nothing; a skill that cannot run is a failed skill, not a document.
- **Not browser-only.** The surface is RMM consoles, AD, terminals, MDM and native admin tools — this is precisely where Strawberry's approach stops [S25].
- **Not model training.** Skills are text under an open format [S24]; no customer data enters a training loop, which is also what makes the security answer sayable.
- **Not EU at launch.** Continuous screen recording faces disproportionality findings and works-council co-determination [S29] (A12/D3).

## 5. First-principles grounding — non-negotiable

Every major feature must map to one or more of these. **A feature that maps to none gets cut, or the principle list was wrong.** Drawn from [research/survey.md](../research/survey.md).

| # | Principle | Why it is true | Source |
|---|---|---|---|
| **P1** | **A demonstration underdetermines intent.** What was essential and what was incidental to that run cannot be recovered from actions alone | The failure that sank forty years of programming-by-demonstration | survey §1 |
| **P2** | **Happy paths are not procedures.** Recovery behaviour, aborted attempts and failure branches are exactly what a successful recording does not contain | survey §7 | survey §7 |
| **P3** | **An assertion about the UI can detect a break; only a goal can re-ground against one.** RPA *does* offer success checks — UiPath's Verify/Check App State, Blue Prism's Wait stages with Application Modeller conditions — but they are optional per-step assertions about the interface, not a declaration of what the procedure is trying to achieve. So a broken selector either **halts loudly or proceeds wrongly**, and neither outcome can recover. A skill's criterion is a *goal state*, which a re-grounding search can aim at | Selector contracts break on application upgrades, unstable dynamic ids, timing, config drift, unhappy paths | survey §1, §6.3; D5 |
| **P4** | **Environments drift continuously.** A skill library is a maintenance liability from the day it is written | RPA maintenance reaches 60% of total implementation cost | [S11] |
| **P5** | **Long-horizon autonomy is not available.** Best frontier completion on long-horizon tasks is 20.6%, and agents at ~85% on standard benchmarks still fail ~80% of real workflows | Benchmarks are curated; client environments are not | [S15][S16] |
| **P6** | **Trust must be calibrated, not maximised — which requires the system to be inspectable and its limits legible.** An engineer will not endorse what they cannot inspect and correct, and a system trusted beyond its capability fails worse than one distrusted | Lee & See: appropriate reliance comes from transparency about capability *and* limits. Parasuraman & Riley: **disuse** — rejection by the expert — is this product's likeliest failure mode | [S35][S36]; survey §6b; [S24] |
| **P7** | **The variance envelope is the asset.** The happy-path procedure is in vendor documentation; how it differs across real environments is not | Cross-environment transfer is survey §8's first open question — the envelope is the pack's answer to it. *(Weakest-grounded of the nine: this is a hypothesis the literature has not settled, and `strategy/lean_canvas.md` treats it as assumption A8, not a finding.)* | survey §8 Q1 |
| **P8** | **Recording is a consent relationship, not a data pipeline.** The person being recorded must benefit, visibly, or capture quietly degrades | The champion and the edge-high persona are the data source | personas §3, §4 |
| **P9** | **Destructive actions are irreversible; verification precedes action — and approval habituates.** IT operations delete mailboxes and disable accounts, and an approver who has cleared 200 correct proposals reads the 201st less carefully | Silent wrongness is worse than loud failure, and **automation bias makes a reliable system more dangerous at the margin, not less** | survey §7, §6b; [S35][S36] |

## 6. Core feature set by loop phase

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

## 7. Data and the learning flywheel

**Three layers, not two:**

| Layer | Lives | Holds | Crosses out |
|---|---|---|---|
| **Per environment** | MSP's node | skills specific to that client, their variance, their drift history — client names, domains, policy ids | never |
| **Per MSP** | MSP's node | procedure shapes clustered across that MSP's 41 environments; this is what makes compounding work for the customer | never, in raw form |
| **Global** | central | abstracted envelopes from many MSPs: `{procedure_shape, precondition_pattern, deviation_class, observation_count}` | — |

The middle layer is the one the first version omitted, and it is where the customer's own compounding actually happens.

### Where distillation runs — the two-stage boundary (D6, corrected)

The first statement of D6 said clustering runs "inside the client boundary". **Critic review established that this is not implementable as written**, for three reasons that are worth recording because they shape the architecture:

1. **Cross-environment clustering needs more than one environment's sessions co-located.** In-client execution guarantees exactly one. The two clauses were mutually exclusive.
2. **Raw capture does not originate inside the client boundary.** It is recorded on an *MSP engineer's workstation* that covers 41 clients. Raw sessions would have to be shipped *into* each client perimeter to be kept from leaving it.
3. **Most clients have no perimeter to host a node in.** For a 22-person dental practice on Okta and M365, the "environment" is a set of SaaS tenants the MSP administers — there is no network to place compute inside.

**The corrected design preserves the founder's intent exactly — raw recordings never reach us — by putting stage 1 at the boundary where capture actually lives:**

| Stage | Runs | Operates on | Crosses out |
|---|---|---|---|
| **1 · Distil + abstract** | **Inside the MSP's own tenant** — one node per MSP, not one per client | That MSP's raw sessions across all its client environments. The MSP already administers all of them, so no new trust boundary is crossed | Nothing raw. Emits **abstracted envelopes only** |
| **2 · Global clustering** | Central | Abstracted envelopes from many MSPs | Procedure shapes and deviation patterns |

**Consequences, all of them improvements:**

- **Cross-environment clustering is legal and local.** An MSP's 41 environments cluster together inside that MSP's own boundary — which is what makes the beachhead's compounding possible at all. Only the *cross-MSP* layer is central, and it never sees raw anything.
- **One node per MSP, not 41.** Three design partners means three nodes, not ~123. This is the difference between a fleet a solo founder can operate and one they cannot.
- **The client-facing claim gets stronger, not weaker:** *your session recordings never leave your MSP's control, and nothing identifying your tenant ever reaches the vendor.*

**The envelope schema, defined well enough to check.** An envelope entry is `{procedure_shape, precondition_pattern, deviation_class, observation_count}` — for example *"MFA re-enrolment blocked by a network-zone-scoped authentication policy; observed in 6 tenants; resolved by time-boxed exclusion, not policy disablement."* It carries **no tenant name, no domain, no user, no policy id and no configuration values** — only that a pattern was seen, its shape, and how often.

**What this means for the two examples the critique caught:** a record reading "conditional-access bypass (Brightwater)" is a **stage-1 artifact and stays in the MSP's tenant** — it is not envelope content. Likewise Ray's cross-environment query ("which of my 41 environments show this pattern?") resolves **entirely within his own MSP's node**; it is his data about his own clients, and it never touches the global layer.

**It constrains the build from day one.** Stage-1 distillation is materially harder to retrofit than to assume, so it binds N6/N9 in [features_prioritized.md](features_prioritized.md) rather than sitting in a later tier — and it adds **N15 node fleet lifecycle**, because a distributed component inside customer tenants has to be deployed, patched, upgraded, rolled back and monitored by whoever operates this company.

**Environment velocity is gated by two things, not one:** the client-side security review [strategy/sales_roadmap.md](../strategy/sales_roadmap.md), and node fleet operations. The second is new and is the one a solo founder feels first.

**Edge inference is a unit-economics line.** The compute-heavy half of the loop runs on hardware we do not own; `financials/unit_economics.md` must model it, including the per-node hardware floor an MSP has to provide.

## 8. Oversight, safety, privacy, compliance

- **Capture consent surface** — engineers see what is captured, can pause, and review before distillation (P8).
- **Client-side transparency** — the MSP's client can be shown what is recorded in their environment and what leaves it; this is Sonia's question and it is a product feature, not a sales document.
- **Destructive-action gating** — always on, not configurable to off.
- **Audit trail** — agent identity, skill version, verification result per action.
- **Retention policy** — raw sessions expire; distilled skills persist. Raw admin-plane recording is the highest-sensitivity artifact in the system and should have the shortest life.
- **Geography** — US-first; EU capture is constrained by disproportionality findings and works-council rights [S29].

## 9. Success metrics

**Outcome metrics first — the domain's real "did it work":**
1. **Engineer-hours to onboard an environment**, against that client's size band (D7). The number the buyer feels — and it must be defined: it counts engineer time spent *reaching a maintained runbook and a working tier-1 floor*, which is not the same as time spent onboarding the client at all. See [journeys/beachhead.md](journeys/beachhead.md).
2. **Time-to-first-verified-skill** in a new environment — the category yardstick nobody publishes [research/survey.md §4].
3. **Cross-environment skill reuse rate** — A8 made measurable, and the earliest read on whether the moat exists.
4. **Verified-action accuracy** — actions whose success criterion passed *and* were correct on human review. Silent wrongness is the metric that matters, not throughput.

**Engagement:** sessions captured per engineer per week; skills endorsed by their authoring engineer (P8 working or not); shadow-to-gated promotion rate.

**Business:** environments onboarded per MSP (the expansion metric on which the revenue ramp depends); **resolved tickets per environment — where "resolved" needs a definition the customer has agreed, including the case where the agent acted, verification passed, and a human then intervened** (the 14:20 case in [journeys/day_in_life.md](journeys/day_in_life.md); `strategy/sales_roadmap.md` step 6b names this as where outcome pricing dies in month three); revenue per MSP against the ~$8,600 year-1 model [strategy/market_sizing.md](../strategy/market_sizing.md).

**Recommended next 3:** (1) build Watch and Distil only, and prove clustering on lab environments before any Act surface exists; (2) specify the envelope schema in `tech/architecture/` precisely enough to be audited — D6's claim is only as good as the guarantee that an envelope entry carries no tenant identity; (3) instrument reuse rate and variance-envelope growth from environment #2, since together they are the only early evidence for A8.
