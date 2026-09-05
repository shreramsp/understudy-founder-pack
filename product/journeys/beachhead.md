# Journey — beachhead: Dana onboards Brightwater Dental, first session to habitual use

> **What this is** — the core paying use case end to end: a service delivery manager taking a brand-new client environment from signed contract to a working skill library, then to habit, with the component and durable record named at each beat.
> **Why it exists** — this is the journey the entire go-to-market is priced against. The onboarding fee (D4/D7) is charged for exactly this sequence, and the number it produces — engineer-hours consumed — is the claim every marketing artifact makes.
> **How to read it** — the timeline is the argument; the baseline column is what the buyer is comparing against. A skeptic should attack week 1, where the product still needs a human to do the work it is learning from.
> **Depends on / feeds** — inherits [PRD.md](../PRD.md), personas §2; feeds `strategy/gtm.md`, `financials/pricing.md`, `narrative/one_pager.md`, [ux_spec.md](../ux_spec.md).

**Persona.** Dana Ortiz, service delivery manager, 20 technicians, 41 client environments.
**Session goal.** Onboard Brightwater Dental (22 users) to full SLA coverage.
**Baseline today.** 25–40 engineer-hours for a client this size — the median band, not the 40–80 complex band [S21] — spread over 3–4 weeks, producing documentation that is stale within a month.

**All operating figures in this journey are `(illustrative: targets, not measured — no pilot exists)`.** They are what the product must achieve to be worth its fee, and they belong in `validation/experiment_board.md` as declared thresholds, not in marketing copy.

---

## Week 0 — the boundary, before any recording

**Monday.** Contract signed. Brightwater is added as an environment on the MSP's **existing** stage-1 node — the node lives in the MSP's own tenant and was provisioned once, when the MSP onboarded, not per client (D6 corrected). The three engineers covering Brightwater already run the capture agent.
→ *Component:* **N1 capture**, **N6 stage-1 distillation** on the MSP node, **N15 node lifecycle**.
→ *Record:* environment `brightwater` registered; envelope egress filter confirmed active.
**This is why the corrected boundary matters operationally:** onboarding a client is a registration, not a deployment. Under the original per-client framing this beat would have been a distributed-node install inside a 22-person dental practice that has no perimeter to host one.

**Monday — the review opens, and it does not close this week.** Brightwater's IT contact receives the tenant-isolation document. Her question — *what leaves my environment?* — has a structural answer: **raw recordings never leave the MSP's control, and nothing identifying her tenant reaches the vendor.**
→ *Component:* **N9 + egress filter**, **X21 audit export**.
→ *Record:* boundary attestation, retained for her review file.
**But the document opens a ~6-week review, it does not end one** [strategy/sales_roadmap.md](../../strategy/sales_roadmap.md) — and there is one of her per client environment. Capture may proceed under the MSP's existing administrative agreement; **gated execution in her tenant waits for her sign-off.** The first version of this journey had her clear it in the same hour, which contradicted the file it cited.

## Week 1 — watch, and do the work anyway

**The honest part of this journey.** In week 1 Understudy produces nothing. Engineers onboard Brightwater the way they always have — mapping the tenant, setting up monitoring, fixing what they find — while capture runs.
→ *Component:* **N1**, **N2 session segmentation**, **N4 sensitive-value redaction** (credentials dropped at capture, before storage), **N10 decision-point narration** prompting ~10 seconds of voice at branch points, **N11 engineer capture controls** (indicator, pause).
→ *Record:* ~30 segmented sessions; zero skills.
**A skeptic should attack here, and the answer is that the fee is not charged for week 1.** The buyer pays for the outcome at week 3, and the first environment is the one that pays back least — the compounding is across environments, not within one.

**Thursday.** An engineer hits a printer-mapping problem, tries two approaches, abandons the first. The system keeps both.
→ *Component:* **N5 failure/abort labelling** (`P2`).
→ *Record:* a labelled failure session — the kind successful runs never contain.

## Week 2 — distil, and let the engineers judge it

**Monday.** Stage-1 distillation runs on the MSP's node. ~30 sessions collapse into ~11 candidate skills `(illustrative)`.
→ *Component:* **N3 action extraction**, **N6 clustering**, **N7 skill synthesis** (goal, preconditions, steps, **success criterion**, escalation envelope).
→ *Record:* 11 skills v1, each naming its contributing sessions and authors (**N13**).

**Monday afternoon — the beat that decides adoption.** Each engineer sees the skills built from their own sessions and is asked to confirm or correct, not informed.
→ *Component:* **N12 skill viewer**, **X19 skill correction UI** (`P6 P8`).
→ *Record:* 8 endorsed as-is, 2 corrected, 1 rejected as "that was a one-off, don't generalise it".
**The rejection matters more than the endorsements.** A system that cannot be told *no* by the person it learned from will not be fed honestly next time.

**Wednesday.** Skills go to shadow. They run against live Brightwater tickets without acting, and their intended actions are compared with what the engineer actually did.
→ *Component:* **X2 shadow mode** (`P5`).
→ *Record:* per-skill agreement rate.

**Friday.** Dana's first weekly digest: *would have matched you on 27 of 34 tickets `(illustrative)`. Here are the 7 disagreements, most interesting first.*
→ *Component:* **X3 deviation report**.
→ *Record:* 7 deviations routed to authoring engineers as questions, not metrics. Four produce corrections; three reveal the engineer was inconsistent, which Dana finds more useful than the four.

## Week 3 — promote, and count

**Tuesday.** Six skills clear their thresholds and promote from shadow to gated. Destructive actions stay gated permanently — not configurable.
→ *Component:* **X10 promotion ladder**, **X5 action-class policy** (`P9`).
→ *Record:* promotion events with the evidence that justified each.

**Thursday.** The onboarding meter closes the environment: **38 engineer-hours consumed against a 25–40 median-band baseline, 9 skills live, time-to-first-verified-skill 8 days.** The meter reports the overrun rather than hiding it — the first environment costs more, and a buyer who discovers that themselves stops believing every other number.
→ *Component:* **N14 onboarding meter**, **X20 environment dashboard**.
→ *Record:* the number the go-to-market is built on [strategy/gtm.md](../../strategy/gtm.md) — against a 25–40-hour baseline for a client this size.

## Week 6 — habit, and the thing Dana actually bought

**The runbook stopped being a document.** Dana no longer maintains Brightwater's documentation; she reviews deviations for ten minutes on Friday. When a tech asks how Brightwater does something, the answer is in the desk rather than in Ray's head.
→ *Component:* **X20**, **X3**, **X13 envelope widening**.

**Week 9 — the compounding shows up, partially.** Dana onboards the next client, a 30-person accountancy on the same M365/Entra stack. Onboarding takes **21 engineer-hours against a 25–40 baseline** — the mechanical setup is unchanged, but the *figure out how this client differs* portion is largely pre-solved because the procedure shapes transferred even though Brightwater's data did not. A second ~6-week client-side review runs in parallel; it gates gated execution, not capture.
→ *Component:* **X17 global stack layer** fed by **N9**'s abstracted envelopes (D6).
→ *Record:* environment 2 onboarded; reuse rate — the A8 measurement — recorded for the first time.
**This is the beat the moat lives or dies on**, and it is the first point in the whole journey where evidence for A8 exists.

---

## Timeline against baseline — stated so it survives a timesheet

The first version of this table claimed environment 1 took **11 hours against a 25–40 baseline**. That was wrong, and wrong in the direction that flattered us: week 1 *is* a normal onboarding — the engineers map the tenant, set up monitoring and fix what they find exactly as before — so the product removed none of it. It then *added* review and endorsement work.

| | Today | With Understudy | |
|---|---|---|---|
| **Hours to onboard environment 1** | 25–40 [S21] | **31–46** | **worse** — baseline unchanged, plus ~6 hrs of skill review, deviation answers and promotion decisions |
| **Hours to onboard environment 2** (same stack) | 25–40 | **18–28** | the *knowledge* portion shrinks; the mechanical setup does not |
| **Hours to a maintained runbook** | ~8 hrs/month, forever, and it is stale anyway | **~40 min/month** of deviation review | the thing Dana actually bought |
| **Tier-1 floor at an unfamiliar client** | none | client-specific procedures from day one | not measurable in hours; it is why escalations fall |
| Knowledge on attrition | leaves with the engineer | stays as endorsed skills | |

`(illustrative: targets, not measured)`

**What the fee is charged for, restated honestly.** Not hours saved on the first environment — there are none. It is charged for **a maintained runbook the MSP never has to write, a tier-1 floor at clients nobody knows, and compression that begins at environment 2.** An ROI calculator built on the first-environment number would be falsified by the first design partner's timesheet [strategy/gtm.md](../../strategy/gtm.md).

## What Dana bought, stated honestly

Not ticket deflection — six gated skills do not empty her queue. **She bought the end of maintaining a runbook nobody kept current, and a floor under her tier-1 team at clients they do not know.** The deflection comes later and is smaller than the category advertises; the onboarding compression begins at environment 2, not environment 1, and the fee is charged against the runbook and the tier-1 floor rather than against first-environment hours.

**Recommended next:** instrument the week-9 beat before anything else in the product — reuse rate on environment 2 is the earliest real evidence for A8, and it arrives roughly two months into a customer relationship rather than at the end of one.
