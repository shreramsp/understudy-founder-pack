# Market sizing — bottom-up

> **What this is** — TAM, SAM and SOM built from users × frequency × price, with the endpoint→user conversion made explicit, penetration modelled as a ramp rather than assumed complete, and every factor sourced or flagged.
> **Why it exists** — assumption A5 flagged market size as one of three claims that could kill this pack. The first version of this file got the arithmetic wrong in the direction that flattered the story (see §Corrections). This version is the honest one, and its answer reshapes the pricing model: **at per-ticket pricing alone the MSP market is roughly $107M, which is not a business — the onboarding fee is not an optional second tariff, it is where the revenue is.**
> **How to read it** — §2 is the build, §3 the ramp, §5 the conclusion that matters. A skeptic should attack the 0.8 tickets/user/month and the 25% automatable share; both are flagged, both are unsourced for MSPs specifically, and §4 shows what happens across their plausible range.
> **Depends on / feeds** — cites [research/sources.md](../research/sources.md); feeds [gtm.md](gtm.md), [channel_plan.md](channel_plan.md), [petal_diagram.md](petal_diagram.md), `financials/pricing.md`, `financials/revenue_build.md`.

## 1. Corrections applied after critic round 1

Three errors in the first version, all found independently and all in the same flattering direction. Recorded rather than quietly fixed, because the corrected numbers are the argument now:

| Error | Was | Now |
|---|---|---|
| **Normaliser re-based.** MetricNet's tickets-per-user-per-month is per served *human* [S34]; it was applied to a managed-*endpoint* count. Endpoints include servers, network gear and second devices | 1,247 endpoints × 0.9 = 1,122 tickets/mo | 1,247 endpoints ÷ 2.0 = **~620 users** × 0.8 = **~496 tickets/mo**, which reconciles with S34's independent "~492 tickets/month" |
| **Penetration double-counted.** Revenue per MSP was computed across the MSP's entire client book, then an expansion assumption was added on top | $28,300/yr per MSP, treated as year-1 | Full-book figure stated separately from a **year-by-year environment ramp** (§3) |
| **Automatable share imported from the wrong population.** Ravenna's 35–60% is internal-IT Slack deflection [S1]; an MSP queue carries break-fix, RMM alert tickets, hardware and on-site work | 35%, "conservative floor" | **25%** `(assumption)` derived from ticket-category mix, with Ravenna cited only as an upper bound |

## 2. Bottom-up build — revenue per MSP at full book penetration

| # | Factor | Value | Basis |
|---|---|---|---|
| 1 | US MSPs | 45,000 | [S31] — no universal registry; estimates 40–50k |
| 2 | Serviceable band (10–100 employees) | ~12,000 | `(assumption: 70% of US MSPs have <50 employees [S31]; this band has multiple clients and no automation staff)` |
| 3 | Endpoints per MSP | 1,247 | [S18] |
| 4 | **Endpoint : user ratio** | **2.0** | `(assumption: endpoints include servers, network devices and second devices; practitioner range 1.5–2.5. No sourced figure found)` |
| 5 | Served users per MSP | ~620 | 3 ÷ 4 |
| 6 | Tickets per user per month | 0.8 | `(assumption: MetricNet defines the metric [S34] but publishes no free benchmark value)` — **cross-check: 620 × 0.8 = 496/mo, against S34's independently reported ~492/mo. The two agree, which is the only validation available** |
| 7 | Tickets per MSP per month | ~496 | 5 × 6 |
| 8 | Automatable share within the claim boundary (D1: governed, supervised, tier-1 repetitive) | **25%** | `(assumption: the "same twenty procedures" category — password/MFA, mailbox and permissions, provisioning, printer/queue. No sourced MSP ticket-mix data exists; see §Gap. Ravenna's 35–60% [S1] is internal-IT deflection and is treated as an upper bound, not a floor)` |
| 9 | Resolved tickets per MSP per month | ~124 | 7 × 8 |
| 10 | Price per resolved ticket | $6 | Below buyer's blended cost of $22.50 [S27]; far below $45 agent-handled [S28] |
| 11 | **Ticket revenue per MSP per year, whole book** | **~$8,900** | 9 × 10 × 12 |
| 12 | Environments (clients) per MSP | ~41 | `(assumption: consistent with a 34-person MSP at $4.6M revenue — see personas.md)` |
| 13 | **Onboarding fee per environment** | **$1,500** | `(assumption)` — against a buyer cost today of 40–80 engineer-hours [S21] at `(assumption: $75/hr loaded)` = $3,000–6,000. Prices at roughly a third of the cost displaced |
| 14 | New/replaced clients per MSP per year | ~6 | `(assumption: ~15% annual client turnover + growth)` |
| 15 | **Steady-state onboarding revenue per MSP per year** | **~$9,000** | 13 × 14 |
| 16 | **Blended annual revenue per MSP, steady state** | **~$17,900** | 11 + 15 |

**The onboarding fee is not a second tariff bolted on — it is half the revenue and the half that arrives first.** Ticket revenue accrues only after an environment is live; the onboarding fee is billed at the moment of the work the buyer already pays 40–80 hours for.

## 3. The ramp — what a customer is actually worth in year 1

An MSP does not onboard 41 environments on signature. Modelling the ramp is what the first version missed:

| Year | Environments live | Onboarding revenue | Ticket revenue | **Total** |
|---|---|---|---|---|
| 1 | 5 (backfill of existing clients) | $7,500 | ~$1,090 | **~$8,600** |
| 2 | 15 cumulative | $15,000 | ~$3,250 | **~$18,250** |
| 3 | 30 cumulative | $22,500 | ~$6,500 | **~$29,000** |
| Steady state (~41 + turnover) | 41 | ~$9,000/yr | ~$8,900/yr | **~$17,900/yr recurring** |

**3-year revenue per MSP ≈ $55,850; at 70% gross margin `(assumption, owed to financials/unit_economics.md)`, 3-year gross profit ≈ $39,100.** This is the number [gtm.md](gtm.md) derives its CAC ceiling from, and it is materially lower than the $65,000 the first version claimed.

## 4. Market size and sensitivity

| Measure | Value | Build |
|---|---|---|
| **SAM** — US, 10–100 employee band, steady state | **~$215M/yr** | 12,000 × $17,900 |
| **SAM at per-ticket pricing alone** | **~$107M/yr** | 12,000 × $8,900 — *the business without the onboarding fee* |
| **TAM** — all 45,000 US MSPs | **~$800M/yr** | 45,000 × $17,900 |
| **SOM** — 3 years, 2% of SAM | **~$4.3M ARR** | 240 MSPs |

SAM in $M/yr across the two softest assumptions:

| Tickets/user/mo → | 0.5 | **0.8** | 1.2 |
|---|---|---|---|
| **15% automatable** | $173 | $185 | $201 |
| **25% automatable** | $193 | **$215** | $244 |
| **35% automatable** | $213 | $245 | $287 |

The band is **$173M–$287M**, and it is narrow because the onboarding fee — the larger half — does not vary with ticket volume at all. That is a structural argument for the two-part tariff independent of its size: it makes revenue robust to the assumption we are least sure of.

**Top-down check.** US MSP revenue is $120–140B [S31]. A $215M SAM is ~0.16% of it — comfortably conservative for a tool automating a slice of service-delivery labour, and built bottom-up rather than reasoned down from a headline.

## 5. What this means — the uncomfortable part, kept

**The MSP market is not, by itself, venture-scale, and the corrected arithmetic makes that clearer than the first version did.** A $215M SAM supports a real company; it does not support a generational one. Three responses; the pack takes the first two and names the third as unproven:

1. **The MSP is the wedge, not the market.** It is where onboarding pain is recurring rather than one-time, and where the global skill layer reaches density fastest because one customer brings 41 environments. It is how the product gets good.
2. **Price the environment, not only the ticket.** Founder-confirmed pricing was per-resolved-ticket; the corrected arithmetic says that alone yields ~$107M and a year-1 customer worth ~$1,100. **This is a change to a founder decision and is flagged as such** — see the open decision in the checkpoint.
3. **The internal-IT expansion market, sized honestly and still unproven.** US firms of 100–2,000 employees: `(assumption: ~200,000 firms; 20% addressable = 40,000)`, ~500 users each × 0.8 × 25% × $6 × 12 ≈ **$7,200/yr each → ~$288M**. Combined with MSPs that is roughly **$500M**, against competitors funded at $164.5M [S13] and an incumbent that paid $2.85B for the category [S26]. **Entering it means competing on resolution quality, the axis [positioning.md](positioning.md) commits to avoiding.** It is the expansion story, and this pack does not claim it is won.

**The honest summary a VC should be handed:** this is a ~$500M-SAM opportunity at current pricing, whose path to more runs through capturing a larger share of the labour cost it displaces — agent labour is 70–80% of the $22.50 blended cost per ticket [S28], and $6 captures roughly a quarter of it.

## Gap — stated, not guessed

**No sourced MSP ticket-category mix exists.** Row 8 is the second-most load-bearing number in the pack and it rests on a category argument, not data. Every free source found describes internal IT desks, whose mix excludes RMM-generated alert tickets, hardware and on-site work. **This is the single highest-value question in the first ten discovery interviews**, and until it is answered the SAM carries a ±40% honest uncertainty that no sensitivity table can remove.

**Recommended next 3 moves:** (1) get real ticket-category mix and per-client ticket volume from the first 5 MSP interviews — rows 6 and 8 are worth more than any other research; (2) test the $1,500 onboarding fee against the 40–80-hour incumbent cost in the same conversations; (3) size internal IT properly before the seed raise rather than carrying §5.3's assumption chain into a deck.
