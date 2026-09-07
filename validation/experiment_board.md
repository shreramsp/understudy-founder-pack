# Experiment board

> **What this is** — the Blank-style learning log for the top assumptions: falsifiable hypothesis with a number, experiment design, **pass/fail threshold declared in advance**, result, learning, decision.
> **Why it exists** — thresholds declared after results are not thresholds. This board exists so that a negative result is a finding rather than an occasion for reinterpretation, and every row here is `planned` because nothing has been run.
> **How to read it** — the Threshold column is the discipline; if a row's threshold could be satisfied by any plausible outcome, the row is decoration. A skeptic should attack E2's fairness bar, which has been raised twice.
> **Depends on / feeds** — inherits [riskiest_assumptions.md](riskiest_assumptions.md), [../tech/not_vaporware.md](../tech/not_vaporware.md) §2; feeds [stage_gate.md](stage_gate.md), [pivot_log.md](pivot_log.md), `financials/use_of_funds.md`.

---

## E1 · Cross-environment skill transfer — the company's one question

**Hypothesis.** Skills synthesized from recordings in environment A execute correctly, unattended, in a held-out environment B **≥70% of the time** across 5 common procedures.
**Design.** 3 engineers × 5 procedures (password reset, MFA re-enrolment, mailbox permission grant, user provisioning, printer queue) × 2 lab tenants on the same stack. Synthesize from A only. Score in B with the harness, blind to which recordings produced which skill.
**Threshold, declared in advance.** **≥70% pass.** 50–70% = method problem, one more iteration. **<50% after three approaches = R1 is false; the company is materially smaller and we say so publicly.**
**Why this number.** Below 70% a technician must check every action, which reproduces the labour the product exists to remove.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E2 · Graceful degradation vs a fair RPA baseline

**Hypothesis.** Under a deliberate interface change, synthesized skills retain **≥2× the success rate** of an equivalently-capable RPA automation of the same procedures.
**Design.** Same 5 procedures. Perturbations: elements moved, renamed, re-ordered, plus a version upgrade that changes selectors. Baseline is a **Unified-Target-equivalent implementation with fuzzy, anchor, image and OCR fallbacks ENABLED**.
**Threshold.** **≥2× the baseline's post-change success rate.** Below 1.5× the differentiation claim is not supportable and `tech/whitepaper.md` §5 must be rewritten or withdrawn.
**The fairness bar has been raised twice and that is the point.** The original design compared against a coordinate-clicking script — a strawman. The second required only "selector-based", which permits fallbacks disabled. **An experiment worth running is one that can lose**, and this one now can.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E3 · Basis test — do they pay for the library, or only for the hours? (D17)

**Reframed after the financials critique.** The original hypothesis asked whether owners would pay $1,500. That is the wrong question, because `financials/pricing.md` §4 now shows the fee is priced **above** the hours it displaces at every band — 99–174% small, 216–466% typical, 108–272% complex. An hours-defensible schedule would be roughly **$241 blended against the $1,005 we charge.** So the price question is downstream of a prior one.

**Hypothesis.** MSP owners will pay a per-environment fee **materially above the engineer-hours it displaces**, because what they are buying is the maintained runbook, the tier-1 floor at unfamiliar clients, and knowledge that survives attrition — none of which is hours-denominated.

**Design.** 10 owner conversations, in this order and no other:
1. Get their onboarding hours by client size, before any price. *(Also feeds `market_sizing.md` row 13 and E8.)*
2. Show the **hours arithmetic honestly** — including that we charge above it.
3. Present the schedule and ask what they would pay for, in their words.
4. Present the **~$241 hours-defensible alternative** and ask which they would rather buy.

**Threshold, declared in advance.**
- **≥5 of 10 accept the banded schedule after seeing the gap** → the library has value independent of hours; the schedule stands and the ROI calculator is re-based on library value.
- **≥5 prefer the ~$241 schedule** → the value *is* hours-shaped, revenue per MSP falls to ~$10,350 and SAM to ~$124M, and the model must be rebuilt on it.
- **≤2 accept either** → the per-environment fee has no basis at all and the **D12 per-MSP platform fee** becomes the model.

**Why this is the highest-value ten conversations in the pack.** It costs nothing, needs no product, and it is the only thing that can distinguish three futures the model cannot: a $179M SAM, a $124M SAM, or a different revenue architecture entirely.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E4 · Channel admissibility

**Hypothesis.** A pre-revenue vendor founder can join **≥1 of 3** named MSP peer or buying groups on terms that permit participation before selling.
**Design.** Identify three specific groups. Establish membership rules, vendor terms, fees, and whether a vendor may join at all.
**Threshold.** ≥1 yes → the primary channel is real. **Zero → the primary and best-economics channels are both closed and the GTM reshapes around the marketplace at 18–24 months**, which changes the raise.
**Cost: two weeks and three phone calls.** It is the cheapest company-shaping result available and it needs no product.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E5 · Envelope re-identification (X25)

**Hypothesis.** Given the full published envelope set from *m* MSPs, an attacker with knowledge of the stack **cannot identify a contributing MSP or tenant** above chance.
**Design.** Generate a realistic envelope set from lab environments. Attack it ourselves: single-entry fingerprinting, and **compositional linkage across entries** — the failure minimum-support thresholds do not address.
**Threshold.** Any successful identification → raise *m*, add a linkage budget, or adopt a noise floor **before the first security review**, not after.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E6 · Do engineers actually cooperate with capture?

**Hypothesis.** Across E1's capture window, engineers pause capture on **<10%** of sessions, provide narration when prompted **>60%** of the time, and delete **<5%** of sessions pre-distillation.
**Design.** Instrument N11's controls during E1. No incentive to cooperate beyond the product's own attribution surface.
**Threshold.** Pause >25% or narration <30% → `P8` is failing and the capture programme needs product changes, not messaging.
**Why this matters more than it looks.** Disuse is invisible in every other metric [S36]. **This is the only instrument that sees it**, and it runs for free inside E1.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E7 · Client-side security review duration

**Hypothesis.** With the tenant-isolation document presented up front, a client-side IT director's review completes in **≤6 weeks**.
**Design.** Present to 3 client-side directors cold, through an MSP contact. Measure elapsed time and what they ask for beyond the document.
**Threshold.** >10 weeks median → expansion velocity is capped below the ramp in `strategy/market_sizing.md` §3 and the revenue model needs re-timing.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

## E8 · MSP ticket-category mix

**Hypothesis.** Tier-1 repetitive plus RMM-alert remediation together account for **≥25%** of an MSP's ticket volume.
**Design.** Ticket-category exports from 5 MSPs, 3 months each.
**Threshold.** <15% → SAM falls roughly 40% and the per-ticket half of the tariff is close to immaterial.
**Result.** — · **Learning.** — · **Decision.** — · **Status: planned.**

---

## Board discipline

- **Every threshold above was written before any data exists.** That is the only property that makes this a board rather than a plan.
- **No `(assumption)` figure from any layer may enter `financials/` until the experiment that tests it returns a number** — the standing rule adopted in `tech/whitepaper.md` §2.
- **Order is by cost, not by importance.** E3, E4 and E5 need no product and run first; E1 and E2 wait on the harness. A company that runs its expensive experiment first learns the same thing later and poorer.
- **A negative result is published.** E1 in particular: forty years of literature has assumed procedure transfer works without measuring it, and a clean negative is the most useful thing this company could contribute if the positive does not arrive.

**Recommended next 3:** (1) run E3, E4 and E5 in the first month — three phone calls, ten conversations and one afternoon of attacking our own schema; (2) run E3 as a *basis* test rather than a price test — it is the only experiment that can distinguish three different companies; (3) re-rank this board after the first five results, and record what changed in [pivot_log.md](pivot_log.md).
