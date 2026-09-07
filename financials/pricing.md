# Pricing — the banded schedule, and where its basis runs out

> **What this is** — the value metric and why it was chosen, the anchor analysis, the competitor price table, the banded tier design D7 requires, willingness-to-pay logic per persona, and the pricing-power argument.
> **Why it exists** — this pack's pricing has failed a critique once already: the fee was justified against onboarding hours the corrected journeys showed it did not displace. This file rebuilds it band by band and states, explicitly, the band where the justification still does not hold.
> **How to read it** — §4 is the uncomfortable section and the one that matters: it shows **what we charge ($1,005 blended) beside what the hours justify (~$241 blended)**, and names E3 as the test that resolves the gap (D16, D17). A skeptic should attack whether the library has value independent of hours at all.
> **Depends on / feeds** — inherits [../strategy/market_sizing.md](../strategy/market_sizing.md) (D4, D7, D9), [../product/journeys/beachhead.md](../product/journeys/beachhead.md); feeds [revenue_build.md](revenue_build.md), [unit_economics.md](unit_economics.md), `startup-website` (pricing page).

**Standing rule inherited from `tech/whitepaper.md` §2, and it governs this entire layer:** no `(assumption)` figure may be treated as an input to a financial forecast until the experiment that tests it returns a number. **Everything below is a scenario conditional on E1, E2, E3 and E8**, not a forecast, and every table says which experiment it waits on.

## 1 · Value metric

**Two parts, and they measure different things deliberately:**

| Part | Metric | What it scales with | Founder decision |
|---|---|---|---|
| **Resolution** | ~$6 per resolved ticket | Work the system does | D4 |
| **Onboarding** | Banded fee per environment, **from environment 2** | Environments the library covers | D4, banded D7, waiver D9 |

**Why not per seat or per endpoint** — the two metrics MSPs are used to. Both scale with the *client's* size rather than with anything we do, which means we would be paid most where we help least (a large client onboarded once) and least where the compounding actually lands (many small environments). Per-environment tracks the mechanism.

**Why environment 1 is free (D9).** It costs the customer *more* than doing nothing — 31–46 engineer-hours against a 25–40 baseline, because the work is unchanged and review is added. Charging for it is charging for a loss, and a design partner's timesheet establishes that in one afternoon.

## 2 · Anchor analysis — corrected twice, and one anchor withdrawn

| Anchor | Figure | Basis |
|---|---|---|
| MSP onboarding labour, **complex client** | 40–80 engineer-hours | **[S21] — this is what the source actually says** |
| MSP onboarding labour, **median client** | 25–40 engineer-hours | `(assumption — no source)`. **The earlier version cited [S21] for this figure and [S21] does not contain it.** See below |
| Loaded engineer rate | **$46–58/hr** | Derived from §5's own $95–120k loaded technician cost ÷ 2,080 hrs. The earlier `$75/hr` implied $156k loaded — above the top of this file's own range |
| **The budget displaced, median client** | **$322–696** | 7–12 hours × $46–58, matched-pair method (§4) |
| Buyer's blended cost per ticket | $22.50 | [S27] — **and it is the wrong anchor. See below** |
| Agent labour as share of ticket cost | 70–80% | [S28] |

**Two anchors were wrong, and both are the same error class this pack has now committed three times.**

**The `[S21]` mis-citation.** The 25–40-hour median figure carried a source tag for a source that says 40–80. `strategy/market_sizing.md` states this correctly — *"S21's 40–80 hours is the typical-to-complex band"* — and this file cited it for the median anyway. **An unsourced assumption wearing a citation is worse than an untagged one**, because it defeats the check the tag exists to enable, and this number sits under roughly 40–60% of revenue. It is now marked as an assumption with no citation, which is what it always was.

**The $22.50 blended anchor is the wrong population.** [S27] is a blended *internal IT help-desk* cost across the whole queue — including the expensive escalations this product explicitly does not touch. The tickets we address are the cheapest quartile by construction: password/MFA resets, mailbox permissions, provisioning, printer queues, and RMM-alert remediation with documented fixes. **A junior technician at $22–30/hr loaded clearing 6–10 of those an hour costs the MSP roughly `(assumption: $2–6 per ticket)`** — and a material share of the alert half is already scripted inside the RMM they pay for.

**The consequence is uncomfortable and is stated rather than buried: at $6, our per-ticket price may sit at or above the MSP's own marginal cost for exactly the tickets we automate.** What we would actually be selling on that half is capacity rather than savings — the tech is at capacity and the alternative is a hire [S33]. That is a real argument, but it is not the arithmetic argument this file was making. **E8 must establish the cost of the automatable subset, not the blend**, and until it does, the per-ticket price has no verified basis either.

## 3 · Competitor price table

| Vendor | Public price | Model |
|---|---|---|
| Ravenna | **Not public** — quote only | Per-seat, believed |
| Atomicwork | Not public | Enterprise contract |
| Moveworks / ServiceNow | Not public | Enterprise contract |
| ServiceNow ITSM | $150–300+/fulfiller/month, plus implementation at 3–5× licence [S20] | Seat + services |
| IT Glue / documentation class | ~$30–50/technician/month `(assumption)` | Per technician |

**No AI-ITSM vendor publishes a price**, which `research/sources.md` records as a marked gap. That is why the anchor above is the buyer's own cost structure rather than a competitor's list price — the only honest anchor available.

## 4 · The banded schedule (D7/D11) — one method, and the fee fails at every band

**The earlier version of this table computed "hours displaced" three different ways** — crossed extremes for the small and typical rows, matched pairs for complex. That inconsistency is not cosmetic: **it is what produced D11's entire cascade.** The complex row looked worst (167–333%) only because it was the one row using the stricter convention.

**Matched pairs is the correct method, and it is now used for all three rows.** A low-complexity client has a low baseline *and* a low post-Understudy figure; crossing the extremes compares one client's baseline against a different client's outcome, which is not a real client. "With Understudy" is baseline × 0.70, per M1's derivation that ~30% of an onboarding is environment discovery and ~70% is mechanical setup observation does not touch.

| Band | Share `(assumption)` | Baseline hrs | With Understudy | **Displaced (matched)** | Value @ $46–58 | Fee | **Fee as % of value** |
|---|---|---|---|---|---|---|---|
| **Small** ≤10 users | ~45% | 15–25 | 10–18 | **5–7** | $230–406 | $400 | **99%–174%** |
| **Typical** 10–30 | ~40% | 25–40 | 18–28 | **7–12** | $322–696 | $1,500 | **216%–466%** ⚠⚠ |
| **Complex** 30+ | ~15% | 40–80 | 28–56 | **12–24** | $552–1,392 | $1,500 | **108%–272%** |
| **Blended** | | | | | | **~$1,005** | |

### What the consistent method changes

**1. The fee fails at every band, at every point in every range.** The lowest ratio anywhere in the table is 99%. There is no point at which the banded schedule is priced below the hours it displaces.

**2. D11 cut the wrong band.** Under the corrected method **typical (216–466%) is the worst band and complex (108–272%) is the best of the three** — the reverse of what D11 acted on. D11's *arithmetic* propagated correctly and every downstream figure in the pack is internally consistent with it; **its rationale was an artifact of the inconsistency it was correcting for.** That is recorded here rather than quietly fixed, because the cascade it triggered moved SAM by $36M and the CAC ceiling by $3,400.

**3. An hours-defensible schedule would be roughly a quarter of this one.** At ~50% of midpoint displaced value: **~$159 small, ~$254 typical, ~$486 complex — blended ~$241.** That would put steady-state onboarding revenue at ~$1,446/yr per MSP instead of $6,030, revenue per MSP at ~$10,350, and **SAM at ~$124M**.

**The schedule is held at $400/$1,500/$1,500 pending E3, on the founder's instruction** — a structure should not be abandoned on the strength of numbers that were computed three inconsistent ways. But the finding is now unambiguous: **the hours basis cannot support this fee at any band.** Either the fee is justified on something other than hours — the maintained runbook, the tier-1 floor, knowledge retention, none of which are hours-denominated — or it moves to the D12 per-MSP platform fee, or it drops by roughly 4×.

**E3 is therefore no longer a price test. It is a *basis* test:** does an MSP owner pay for the library, or only for the hours? Ten conversations settle it, and no model can.

## 5 · Willingness to pay, by persona

| Persona | Pays for | Ceiling `(assumption, untested until E3)` |
|---|---|---|
| **Marcus** (owner) | Taking a client he cannot staff | Anchored on a technician's loaded cost, ~$95–120k — so a four-figure per-environment fee is small *if* the leverage story lands |
| **Dana** (delivery manager) | A runbook that stays true | Would not authorise a purchase; would block one |
| **Ray** (principal) | Nothing. He is not a buyer | — |

**The buyer's real comparison is not our fee against our value. It is our fee against a hire he cannot make** [S33]. That framing supports a much higher price than the compression arithmetic does — and it is exactly the framing `petal_diagram.md` warns is dangerous to say out loud, because it poisons the personas whose cooperation capture requires.

## 6 · Pricing power over time

Price should rise as the variance envelope thickens, because what the buyer receives at environment 20 is materially better than at environment 2. **But that argument is A8** — untested, and the whole pricing-power case collapses with it. There is no pricing-power claim in this pack that does not reduce to the transfer assumption.

**Recommended next 3:** (1) run E3 before committing to any schedule — the fee has now failed two arithmetic checks and a tenth conversation is worth more than an eleventh model; (2) price the complex band at $1,500 pending E3 rather than defending $3,000; (3) build the ROI calculator on the *library* value as well as the hours, so that if option 2 becomes necessary the instrument survives the change.
