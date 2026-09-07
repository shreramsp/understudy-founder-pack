# Pricing — the banded schedule, and where its basis runs out

> **What this is** — the value metric and why it was chosen, the anchor analysis, the competitor price table, the banded tier design D7 requires, willingness-to-pay logic per persona, and the pricing-power argument.
> **Why it exists** — this pack's pricing has failed a critique once already: the fee was justified against onboarding hours the corrected journeys showed it did not displace. This file rebuilds it band by band and states, explicitly, the band where the justification still does not hold.
> **How to read it** — §4 is the uncomfortable section and the one that matters. A skeptic should attack the small-client band, where the fee exceeds the value it displaces.
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

## 2 · Anchor analysis — what budget this comes out of

| Anchor | Figure | Source |
|---|---|---|
| MSP's own onboarding labour | 25–40 engineer-hours, median client | [S21] |
| Loaded engineer rate | `(assumption: $75/hr)` | — |
| **The budget being displaced** | **$1,875–3,000 per median client** | derived |
| Buyer's blended cost per ticket | $22.50 | [S27] |
| Agent-handled cost per ticket | $45 | [S28] |
| Agent labour as share of ticket cost | 70–80% | [S28] |

**The onboarding budget is not a line item.** It is unbilled engineer time [../strategy/petal_diagram.md](../strategy/petal_diagram.md) petal 1 — which makes it the easiest budget to justify against and the hardest to find, because there is no code to charge it to. The ROI calculator exists to convert it into one.

## 3 · Competitor price table

| Vendor | Public price | Model |
|---|---|---|
| Ravenna | **Not public** — quote only | Per-seat, believed |
| Atomicwork | Not public | Enterprise contract |
| Moveworks / ServiceNow | Not public | Enterprise contract |
| ServiceNow ITSM | $150–300+/fulfiller/month, plus implementation at 3–5× licence [S20] | Seat + services |
| IT Glue / documentation class | ~$30–50/technician/month `(assumption)` | Per technician |

**No AI-ITSM vendor publishes a price**, which `research/sources.md` records as a marked gap. That is why the anchor above is the buyer's own cost structure rather than a competitor's list price — the only honest anchor available.

## 4 · The banded schedule (D7) — and the band where the basis fails

Charged **from environment 2**. Basis is the compression the library produces, not the full onboarding cost.

| Band | Share of a book `(assumption)` | Baseline hours | With Understudy | Hours displaced | Value displaced | **Fee** | Fee as % of value |
|---|---|---|---|---|---|---|---|
| **Small** ≤10 users | ~45% | 15–25 | ~11–18 | **0–7** | **$0–525** | **$400** | **76%–∞** ⚠ |
| **Typical** 10–30 users | ~40% | 25–40 | 18–28 | 0–22 | $0–1,650 | **$1,500** | 91%–∞ ⚠ |
| **Complex** 30+ users | ~15% | 40–80 | 28–56 | 12–24 | $900–1,800 | **$3,000** | **167%–333%** ⚠⚠ |

**Every band is uncomfortable, and the honest reading is worse than the D9 correction implied.**

**The compression basis does not survive at any band's lower bound**, and at the complex band it does not survive at all — a $3,000 fee against $900–1,800 of displaced hours is priced above the value it claims. Three responses:

1. **Price the complex band down to $1,500**, matching typical, and accept that large environments subsidise nothing. Simplest, and it makes the schedule nearly flat — which is what D7 was trying to escape.
2. **Re-base the fee on the library rather than the compression.** What environment 2 buys is not only fewer hours; it is a maintained runbook for that client and a tier-1 floor at it. Those are real and are not hours-denominated — but abandoning the hours denomination discards the ROI calculator that `petal_diagram.md` identifies as the instrument that creates the budget line at all.
3. **Fold the onboarding fee into a per-MSP platform fee** and keep per-ticket as the only usage metric. This is D9's rejected alternative 2 returning by a different road, and it changes the revenue model in three strategy files.

**Recommendation: option 1 for the schedule, and treat option 3 as live.** The compression basis is defensible for the typical band at its upper half and nowhere else. **This is the second time the fee's justification has failed under arithmetic, and that pattern is itself information: the value this product creates may simply not be hours-shaped.** E3 is the experiment that settles it, and it costs ten conversations.

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
