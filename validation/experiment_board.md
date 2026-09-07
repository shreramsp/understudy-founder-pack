# Experiment board

> **What this is** — the Blank-style learning log for the top assumptions: falsifiable hypothesis with a number, experiment design, **pass/fail threshold declared in advance**, result, learning, decision.
> **Why it exists** — thresholds declared after results are not thresholds. This board exists so that a negative result is a finding rather than an occasion for reinterpretation, and every row here is `planned` because nothing has been run.
> **How to read it** — the Threshold column is the discipline; if a row's threshold could be satisfied by any plausible outcome, the row is decoration. A skeptic should attack E2's fairness bar, which has been raised twice.
> **Depends on / feeds** — inherits [riskiest_assumptions.md](riskiest_assumptions.md), [../tech/not_vaporware.md](../tech/not_vaporware.md) §2; feeds [stage_gate.md](stage_gate.md), [pivot_log.md](pivot_log.md), `financials/use_of_funds.md`.

---

## E0 · The recruiting funnel — the constraint every other experiment sits on

**Added after critic round 1, which found the layer's fatal flaw: four of six Discovery exit criteria consume MSP owner attention, and nothing modelled how a founder with no MSP relationships (A6) obtains it.** "Costs nothing" was true of the transcript and false of the founder-weeks, and it was the only unsourced cost in a file whose contract requires a Cost column.

**The chain, tagged rather than assumed away:**

| Stage | Rate `(assumption)` | To get 10 completed E3 conversations |
|---|---|---|
| Cold touches (r/msp, MSP Discord/Slack, LinkedIn owner outreach, podcast audiences) | — | **200–400 touches** |
| → reply | 8–15% | 20–45 replies |
| → booked call | 40–50% of replies | 10–20 booked |
| → **completed 45–60 min substantive call** (owner produces hours by client size, ticket mix, price reaction) | 60–75% | **7–14 completed** |

**Anchored on the pack's own floor:** `strategy/gtm.md` §2.4 prices cold outbound at *"below 5% to a call"* as its disqualifying test. That 5% is to a *call*, not to a substantive one — so the pessimistic case is ~400 touches for 10 completed conversations.

**Founder-hours: `(assumption: 60–100 hours across 6–10 weeks)`** — outreach, follow-up, scheduling, the calls, and same-hour synthesis. **That is the real cost of E3, E7 and E8, and it was previously recorded as "~$0 · 2 weeks".**

**This is also the layer's first instrumented metric**, and `get_keep_grow.md` now carries the stage it previously omitted: touches → reply → booked → completed. A pre-revenue company can instrument nothing else.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E1 · Cross-environment skill transfer — the company's one question

**Redesigned after critic review established the original could not produce the estimate it named.** Three defects, all fatal to the inference:

- **The unit of analysis and the sample size were never stated.** At 5 skills scored once, observing 4/5 gives a Wilson 95% CI of **[38%, 96%]**; at 15, observing 11/15 gives **[48%, 89%]**. Neither separates 70% from 60%, and **neither excludes the 50% kill line.** Distinguishing 70 from 60 at 80% power needs ~142 independent trials; 70 from 50 needs ~37.
- **Two environments have zero degrees of freedom on between-environment variance — which is literally what R1 is asking about.** Two lab tenants on the same stack is a near-best case, and a 70% result there licenses nothing about the ~41 drifted client environments per MSP the ramp is built on.
- **Three iterations against B destroys B's held-out status.** After approach 3, B is a training set.

### Design

**Unit of analysis: the *(skill, held-out environment)* pair.** Repeated runs of one skill in one fixed tenant are near-deterministic and do not add information.

| | |
|---|---|
| Procedures | 5 |
| Environments | **≥6 held-out**, plus A for synthesis and **C reserved untouched for the final scored run** |
| **Scored pairs** | **≥30** — enough to exclude the 50% kill line, not enough to separate 70 from 60, and that limit is stated rather than hidden |
| Environment sampling | Pre-registered **dissimilarity metric** (tenant policy count, non-default configuration ratio, stack version spread), with environments chosen to span it |
| Primary endpoint | Transfer rate **as a function of dissimilarity**, not one scalar |
| Every rate reported | with a **Wilson 95% CI** beside it |

**Method selection freezes on A.** All three clustering approaches are chosen and tuned against environment A. **C is opened once, for the final scored run**, and never iterated against.

**The harness's own false-positive mode is measured, not assumed away.** DD3 generates the success criterion the harness then scores against, and `tech/deep_dives.md` names *"criteria that pass while the outcome is wrong"* as a failure verification design cannot eliminate. **A human adjudicates a random 20% sample of harness "passes"**, and the adjudicated rate is what the threshold applies to.

**Threshold, re-derived — the earlier 70% did not follow from its own justification.** The old reasoning was *"below 70% a technician must check every action"*, which argues for ~100%: at 70% a technician still checks every action, because you cannot know which 3 in 10 failed without looking. And **DD7's default-destructive gating requires human review of destructive steps at any success rate**, so 70% is not the point where checking stops.

**The decision-relevant variable is review time against do-it-yourself time.** A skill is worth running when *(review time + failure-fix time) < (time to do it by hand)*. For a tier-1 procedure at ~8 minutes by hand and ~2 minutes to review `(assumption, to be measured in the first pilot)`, the crossover sits near a **25–30% failure rate**.

**Threshold: ≥70% adjudicated-correct across ≥30 scored pairs, with the Wilson CI reported.** 50–70% = method problem, one iteration. **<50% with the CI excluding 50% = R1 is false.**
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E2 · Graceful degradation vs a fair RPA baseline

**Hypothesis.** Under a deliberate interface change, synthesized skills retain **≥2× the success rate** of an equivalently-capable RPA automation of the same procedures.
**Design.** Same 5 procedures. Perturbations: elements moved, renamed, re-ordered, plus a version upgrade that changes selectors. Baseline is a **Unified-Target-equivalent implementation with fuzzy, anchor, image and OCR fallbacks ENABLED**.
**Threshold — a ratio alone can pass on two failures.** 20% vs 8% is 2.5× and clears any ratio bar while neither arm is deployable. So the threshold is **both**: skills retain **≥2× the baseline's post-change success rate AND ≥50% in absolute terms.** Below either, the differentiation claim is not supportable and `tech/whitepaper.md` §5 must be rewritten or withdrawn.

**Two design defects the earlier version had, both about who controls the comparator:**

- **Nobody was named as the baseline's builder**, and A6 records the founder's edge as AI/agents engineering with **no declared RPA competence**. A sponsor building the active comparator arm is not a control. **A certified UiPath or Blue Prism practitioner is contracted to build it, and the implementation is published for replication.**
- **Perturbation selection was the experiment's largest undeclared degree of freedom.** "Moved, renamed, re-ordered" are precisely the classes where selector fallbacks are weakest and goal re-grounding strongest. **The perturbation set is now pre-registered and sealed before either arm is built**, and drawn from the failure classes `tech/whitepaper.md` §5 already sources: upgrade-broken selector contracts, unstable dynamic identifiers, timing and synchronisation, configuration drift.
**The fairness bar has been raised twice and that is the point.** The original design compared against a coordinate-clicking script — a strawman. The second required only "selector-based", which permits fallbacks disabled. **An experiment worth running is one that can lose**, and this one now can.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E3 · Basis test — do they pay for the library, or only for the hours? (D17)

**Reframed after the financials critique, then redesigned after the validation critique.** The first reframe put both schedules in front of the *same* owner and asked which they preferred. **That measures discount preference, not basis** — no owner prefers to pay 4× more, so it was structurally biased toward the answer that the value is hours-shaped, which is the very thing under test.

**Hypothesis.** An MSP owner will commit to a per-environment fee **materially above the engineer-hours it displaces**, because what they are buying is the maintained runbook, the tier-1 floor at unfamiliar clients, and knowledge that survives attrition — none of which is hours-denominated.

**Design — split sample, not a menu.** 10 owners from E0's funnel, **randomly assigned**, and neither arm sees the other's price:

| Arm | n | Sees | Asked for |
|---|---|---|---|
| **A** | 5 | The banded schedule **with the hours gap disclosed** — we charge $1,005 blended against ~$241 of displaced hours, and we say so | A countersigned design-partner LOI at the banded price |
| **B** | 5 | The ~$241 hours-defensible schedule **only** | The same LOI at that price |

**Acceptance has to cost the owner something.** A verbal reaction to a product twelve months from existing is not evidence. **The instrument is a countersigned design-partner LOI** — non-binding on delivery, binding on price and intent — because that is the cheapest signal that separates politeness from willingness.

**Both arms are asked their onboarding hours by client size before any price is shown**, which also feeds `strategy/market_sizing.md` row 13 and E8.

**Thresholds, with precedence stated so two branches cannot both fire:**

1. **Arm A ≥3 of 5 sign** → the library has value independent of hours. The schedule stands; the ROI calculator is re-based on library value. *(This branch is checked first.)*
2. **Arm A ≤1 signs and Arm B ≥3 sign** → the value is hours-shaped. Revenue per MSP falls to ~$10,350, SAM to ~$124M, and the model is rebuilt on the lower schedule.
3. **Neither arm reaches 3** → the per-environment fee has no basis at any price, and the **D12 per-MSP platform fee** becomes the model.
4. *Ambiguous (Arm A = 2)* → inconclusive, and it is reported as inconclusive rather than resolved in whichever direction is convenient. Re-run with 10 more.

**What n=10 cannot do, stated rather than glossed.** Five of ten carries a 95% CI of roughly [24%, 76%]. **This experiment can distinguish "clearly yes" from "clearly no"; it cannot resolve anything in between**, which is why branch 4 exists and why an ambiguous result is reported as ambiguous rather than resolved in whichever direction is convenient. Presentation order within each arm is counterbalanced so the split is not a property of the script.

**Why this is the highest-value ten conversations in the pack.** It needs no product, and it is the only instrument that can distinguish three different companies — a $179M SAM, a $124M SAM, or a different revenue architecture — which no amount of modelling can.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E4 · Channel admissibility

**Hypothesis, restated against the rule rather than against admission.** ≥1 of 3 named groups' **stated terms permit** a non-MSP vendor founder to participate before selling.

**Why the distinction matters.** The earlier version's threshold was written against *being admitted*, and `strategy/channel_plan.md` says approval takes **3–6 months**. At month 2 the realistic state is three applications in progress — which scored as "zero admitted" and fired a pivot that "changes the raise" **on absence of evidence rather than evidence of absence.**

**Design.** Identify three specific groups. Establish membership rules, vendor terms, fees, and whether a vendor may join at all. That is discoverable in a fortnight; admission is not.
**Threshold.** ≥1 group's terms permit it → the primary channel is real, and **admission becomes a separate, later criterion dated to the first committee cycle.** All three exclude vendors outright → the primary and best-economics channels are closed and the GTM reshapes around the marketplace at 18–24 months.
**Cost: two weeks and three phone calls.** It is the cheapest company-shaping result available and it needs no product.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E5 · Envelope re-identification (X25)

**Hypothesis.** Given the full published envelope set from *m* MSPs, an attacker with knowledge of the stack **cannot identify a contributing MSP or tenant** above chance.
**Design.** Generate a realistic envelope set from lab environments. Attack it ourselves: single-entry fingerprinting, and **compositional linkage across entries** — the failure minimum-support thresholds do not address.
**Threshold, and what a null result does *not* license.** The earlier version fired only on success — on synthetic data we generate and attack ourselves — so the most plausible outcome (we didn't break it) passed by default. That fails the board's own test: a threshold no plausible outcome violates is decoration.

**Declared attack budget:** methods (single-entry fingerprinting, compositional linkage across entries, auxiliary-data join against public tenant characteristics), **40 person-hours**, and **one external red-team pass**. Any successful identification → raise *m*, add a linkage budget, or adopt a noise floor **before the first security review**.

**A null licenses exactly one sentence: "no attack was found within budget B."** It does not license "anonymised". DD4 concedes the guarantee is **heuristic, not formal** — the shippable privacy claim needs l-diversity, t-closeness or differential privacy, none of which is implemented — and E5 cannot substitute for that.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E6 · Do engineers actually cooperate with capture?

**Hypothesis.** Across E1's capture window, engineers pause capture on **<10%** of sessions, provide narration when prompted **>60%** of the time, and delete **<5%** of sessions pre-distillation.
**Split in two, because the population could not support the inference.** E1 runs **paid contractors on lab tenants**. Disuse [S36] is a reliance decision by an operator whose *role* is affected — a contractor has no employment exposure, no client-specific expertise being expropriated, no peer channel, and is **paid by the person measuring them**. That is a demand-characteristics setup that manufactures a cooperative result, and at n=3 one engineer pausing on 75% of sessions crosses the kill line alone.

**E6a — instrumentation smoke test, inside E1.** Does N11 emit the events at all? **No thresholds, no inference about willingness.**

**E6b — the real experiment, at a design partner.** ≥8–10 **employed** engineers capturing real client work, stratified by tenure, over a pre-declared window with a pre-declared baseline period. This is the persona the experiment exists for — the guide screens Ray as "≥10 years, holds environment knowledge for named clients", and E1's contractors are by construction not Rays.
**Threshold (E6b only).** Pause >25% or narration <30% → `P8` is failing and the capture programme needs product changes, not messaging. **P6's date moves to first-pilot + 90 days**, since that is the earliest this is measurable.
**Why this matters more than it looks.** Disuse is invisible in every other metric [S36]. **This is the only instrument that sees it**, and it runs for free inside E1.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E7 · Client-side security review duration

**Split into two, because the earlier version was contradictory and unfalsifiable.** It said "cold, through an MSP contact" — those are opposites — and neither contact exists at month 3. Worse, the ask inverts the introducer's incentive: an owner would be introducing a product-less stranger to *his own client* so that client can be prompted to think about an AI with write access in their tenant, **before the owner has decided to buy.** That is the introduction an owner is least likely to make.

**E7a · Pre-customer — measures what is observable.**
**Hypothesis.** A client-side IT director raises **≤8 questions beyond the tenant-isolation document**, and none of them is a blocker the architecture cannot answer.
**Design.** Source directors through security communities, vCISO networks, or **paid expert-network calls** — not a borrowed MSP relationship. Measure the count and category of questions, not elapsed time.
**Threshold.** Any question the architecture cannot answer → a design gap, surfaced before a customer meets it.

**E7b · Cycle time — deferred to the design-partner phase.**
Elapsed time on a hypothetical review with no contract, no purchase and no deadline measures **how long a favour takes, not how long a review takes**, so R7's ">10 weeks" threshold could not be falsified honestly. It moves to where `stage_gate.md` already needs it: the first real pilot.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E8 · MSP ticket-category mix

**Hypothesis.** Tier-1 repetitive plus RMM-alert remediation together account for **≥25%** of an MSP's ticket volume.
**Design, corrected. Target ≥8–10 exports, not 5** — at 5 convenience-recruited exports with a plausible between-MSP SD of ~10pp, the t-based half-width is ~12pp before selection bias, so the stage gate's "±10pp" was unreachable by construction. A PSA export is the MSP's book of business — client count, volume, service mix, effectively their revenue shape. **No owner gives that to a stranger with no product, no NDA and no reference**, and the earlier version named no instrument that would change that.

**What buys it:** an **anonymised cross-MSP category benchmark returned to every contributor** — the thing none of them can build alone and all of them want. Plus a **one-page mutual NDA** and a **scoped export spec** (category and count only; no client names, no revenue, no identifiers).

**And the layer contradicted itself here.** `discovery_guide.md` Q10 asks owners to recall their top five categories from memory and calls it "the pack's single highest-value unknown", while `metrics_by_stage.md` files exactly that under **Ignore** — *"owners systematically misremember mix"*. Both cannot be right. **Resolution: memory estimates are a screening signal, exports are the evidence**, and the gate accepts a graded ladder rather than a binary.
**Threshold, graded rather than binary.** The evidence ladder: **2 exports + 8 memory estimates + one PSA-vendor or community benchmark** clears it. <15% automatable → SAM falls roughly 40% and the per-ticket half is close to immaterial.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E9 · Demonstrations per stable skill

**Promoted from a dangling reference.** R9 cited "E9 — included in E1" and no such row existed; E1 as designed collects one demonstration count (3 per procedure), which is a single point on a curve.
**Hypothesis.** A procedure reaches a stable skill — one whose synthesis no longer changes materially with additional demonstrations — within **≤6 demonstrations**.
**Design.** Synthesize at 1, 2, 3, 4, 6 and 8 demonstrations and measure edit distance between successive syntheses. **This sizes E1's contractor hours**, which the earlier version priced before knowing the answer.
**Threshold.** >8 demonstrations → capture economics change materially and onboarding duration with them.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E10 · On-node typing accuracy

**Also promoted from a dangling reference** (R10). D6 forces action typing onto a quantised on-node model, and no published accuracy exists for RMM/AD/MDM surfaces.
**Hypothesis.** On-node typing reaches **≥90% of frontier-model accuracy** on 200 hand-labelled admin actions.
**Threshold.** <80% → the D6 boundary costs more accuracy than assumed, and either the reference node's GPU grows or the boundary needs re-examining.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**
---

## Board discipline

- **Every threshold above was written before any data exists.** That is the only property that makes this a board rather than a plan.
- **No `(assumption)` figure from any layer may enter `financials/` until the experiment that tests it returns a number** — the standing rule adopted in `tech/whitepaper.md` §2.
- **Order is by cost, not by importance.** E3, E4 and E5 need no product and run first; E1 and E2 wait on the harness. A company that runs its expensive experiment first learns the same thing later and poorer.
- **A negative result is published.** E1 in particular: forty years of literature has assumed procedure transfer works without measuring it, and a clean negative is the most useful thing this company could contribute if the positive does not arrive.

**Recommended next 3:** (1) run E3, E4 and E5 in the first month — three phone calls, ten conversations and one afternoon of attacking our own schema; (2) run E3 as a *basis* test rather than a price test — it is the only experiment that can distinguish three different companies; (3) re-rank this board after the first five results, and record what changed in [pivot_log.md](pivot_log.md).