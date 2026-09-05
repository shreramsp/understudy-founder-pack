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

## E3 · Willingness to pay for environment 2

**Hypothesis.** **≥5 of 10** MSP owners accept the banded onboarding fee at the median band, framed "first environment free", after seeing their own hour counts.
**Design.** 10 discovery conversations. Ask for their onboarding hours *before* showing any price. Present the banded schedule. Record acceptance, objection, and counter-anchor.
**Threshold.** ≥5 accept → pricing holds. ≤2 accept, **or the median hour count comes back below 25**, → the fee has no basis and the revenue model returns to per-ticket, which `strategy/channel_plan.md` shows closes every channel.
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

**Recommended next 3:** (1) run E3, E4 and E5 in the first month — three phone calls, ten conversations and one afternoon of attacking our own schema; (2) build the harness before the clusterer so E1 and E2 share it; (3) re-rank this board after the first five results, and record what changed in [pivot_log.md](pivot_log.md).
