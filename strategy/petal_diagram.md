# Petal diagram — the adjacent markets we draw customers from

> **What this is** — Blank's petal diagram: Understudy at the centre, and the six adjacent budget pools whose budgets and habits it displaces, with the incumbents in each petal and what customers currently spend there.
> **Why it exists** — a 2×2 asks where rivals sit; the petal asks a harder and more useful question — **which existing budget does this get paid out of?** For a company selling a category that does not yet have a line item, that question decides whether the sale is a swap or a net-new ask, and net-new asks stall.
> **How to read it** — the "what they spend today" column is the point. A skeptic should attack whether these budgets are genuinely reachable or merely adjacent.
> **Depends on / feeds** — cites [research/competitors.md](../research/competitors.md), [market_sizing.md](market_sizing.md); feeds [gtm.md](gtm.md), [channel_plan.md](channel_plan.md), `financials/pricing.md`.

```
                    Service desk / ITSM software
                    (Ravenna, Atomicwork, ConnectWise)
                              $  per seat/mo
                                   |
   Documentation & IT              |              Onboarding as
   knowledge mgmt                  |              billable project work
   (IT Glue, Hudu)          ┌──────┴──────┐       (own engineers)
   $ per tech/mo    ────────┤ UNDERSTUDY  ├────── $ 40–80 hrs per client
                            └──────┬──────┘
   Process discovery /             |              Headcount
   task mining                     |              (hire another technician)
   (UiPath, Celonis)               |              $ ~$95–120k loaded
   $ enterprise licence     Automation tooling
                            (RPA, RMM scripting)
```

| Petal | Incumbents | What the customer spends there today | Why that budget moves to us | Difficulty |
|---|---|---|---|---|
| **1. Onboarding as project work** *(displaced internal cost, not a vendor market)* | The MSP's own engineers — **no incumbent vendor** | **40–80 engineer-hours per client** [S21] at `(assumption: $75/hr loaded)` = $3,000–6,000 per client; at ~6 new clients/yr that is **$18–36k/yr per MSP, ~$216–432M across the band** | The budget we are actually taking. Easiest sale because it is already being spent and already resented. Not a line item — a leak | **Lowest** |
| **2. Headcount** *(displaced internal cost, not a vendor market)* | The labour market — **no incumbent vendor** | `(assumption: a technician at ~$95–120k loaded)`; revenue/tech benchmark $150–200k [S32] | 26% of MSPs cannot staff clients they could win [S33]; we are a partial substitute for the hire they cannot make | Low — but framing matters enormously (see below) |
| **3. Service desk / ITSM software** | ConnectWise, Ravenna, Atomicwork | `(assumption: $50–100/tech/mo → ~$20–40k/yr per MSP; ~$240–480M across the 12,000-MSP band)` | Only if we replace the desk, which we do not initially. Early on we sit beside it | Medium — displacement, not addition, is a later fight |
| **4. Documentation & knowledge management** | IT Glue, Hudu | `(assumption: $30–50/tech/mo → ~$12–20k/yr per MSP; ~$144–240M across the band)` | Our library makes their documentation partly redundant — but the budgets are small and the switch is emotional (years of accumulated content) | Medium |
| **5. Process discovery / task mining** | UiPath, Celonis, FortressIQ's heirs | **$0 at MSPs** — enterprise licences, not an MSP line item at all | We do their job for a segment they do not serve, at a price the segment can pay | **Not a petal.** A pool you cannot draw a budget from is a competitor, not a source market — retained here only to record that it was considered and rejected |
| **6. Automation tooling** | RPA vendors, RMM scripting | Bundled in the RMM stack — **no discrete budget**; the real spend is engineer time writing scripts `(assumption: 2–5 hrs/week/MSP)` | We displace the scripting effort, not the RMM licence | Medium |

## Honest labelling

Petals 1 and 2 have **no incumbent vendor** — they are displaced internal cost pools, not markets with a defender. Petal 5 has **no MSP budget at all** and is retained only as a considered-and-rejected row. Blank's petal asks which adjacent markets supply customers; for this company the honest answer is that the two largest pools are internal costs, which is unusual and worth stating plainly rather than dressing as markets.

**Sized total of the genuinely addressable pools:** petals 1 + 3 + 4 ≈ **$600M–$1.15B/yr** across the 12,000-MSP serviceable band `(assumption-heavy — every figure above except the engineer-hours [S21] and the revenue/tech benchmark [S32] is an assumption)`. That is the ceiling on what could ever be redirected to us in this segment, and it brackets the $215M SAM in [market_sizing.md](market_sizing.md) sensibly: we are claiming roughly a fifth to a third of the displaceable pool, not all of it.

## What the petal says that the 2×2 did not

**The primary budget is petal 1, and it is not a software budget at all** — it is unbilled engineer time. That is unusually good news: no incumbent vendor loses a renewal when we win, so there is no defender, and the buyer feels the cost monthly without having chosen to spend it. It is also a warning: **a leak is not a line item.** Marcus has no "onboarding software" budget code, so the first sale is a *creation* of budget, justified against hours, which is exactly why the ROI arithmetic must be on the first slide and denominated in engineer-hours rather than in tickets.

**Petal 2 is the most dangerous to name out loud.** "Cheaper than a technician" is true, converts well with owners, and poisons the well with Dana, Priya and Ray — the three people whose cooperation the recording programme requires ([value_prop_canvas.md](value_prop_canvas.md)). **Positioning must draw from petal 2's budget while telling petal 1's story.** That is not spin: the honest claim is that we let an MSP take the client they could not staff, which is additive, not substitutive.

**Recommended next 3 moves:** (1) build the ROI calculator in engineer-hours, not tickets, and lead with it; (2) never write "replaces a technician" in customer-facing copy, while modelling petal 2 internally in `financials/`; (3) treat petals 3 and 4 as year-two displacement, not year-one positioning.
