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
| 6 | Tickets per user per month | 0.8 | `(assumption: MetricNet defines the metric [S34] but publishes no free benchmark value)` — **consistency check: 620 × 0.8 = 496/mo against S34's ~492/mo. This is a *fit, not a validation* — two unsourced free parameters (row 4's ratio, this rate) whose product lands on the anchor; any pair on ratio × rate ≈ 0.4 does the same, and S34's own population (a support team of unstated size) is itself an assumed match. It rules out an order-of-magnitude error and nothing more** |
| 7 | Tickets per MSP per month | ~496 | 5 × 6 |
| 8 | Automatable share within the claim boundary (D1: governed, supervised, tier-1 repetitive) | **25%** | `(assumption)` — two sub-populations, not one: **(a) user-initiated tier-1 procedures** (password/MFA, mailbox and permissions, provisioning, printer/queue) and **(b) RMM-generated alert remediation** (patch failure, agent offline, disk space, backup job failed, certificate expiry). (b) was originally cited as a reason MSP rates differ from internal IT — but alert tickets have deterministic triggers, documented remediation and no end user to interview, which makes them among the *most* mechanisable items in the queue. They belong in the numerator, not the excuse. **25% may therefore be conservative in an unexamined way rather than a well-chosen floor.** No sourced MSP ticket-mix data exists; see §Gap. Ravenna's 35–60% [S1] is internal-IT deflection, treated as an upper bound only |
| 9 | Resolved tickets per MSP per month | ~124 | 7 × 8 |
| 10 | Price per resolved ticket | $6 | Below buyer's blended cost of $22.50 [S27]; far below $45 agent-handled [S28] |
| 11 | **Ticket revenue per MSP per year, whole book** | **~$8,900** | 9 × 10 × 12 |
| 12 | Environments (clients) per MSP | ~41 | `(assumption)` — consistent with [personas.md](personas.md): a 34-person, **$2.9M** MSP whose 41 clients average ~16 users. Cross-check: 620 users × $185/user/mo [S19] ≈ $1.4M of managed-services revenue, with the balance in projects, hardware and licence resale — a normal MSP revenue mix |
| 13 | **Onboarding fee per environment** | **$1,500** | `(assumption)` — **priced against the median client of this book, not the outlier.** See the size distribution below; the median 16-user client displaces `(assumption: ~25–35 hours at $75/hr loaded = $1,875–2,625)`, so the fee captures **57–80% of the cost displaced**. Thin headroom, stated plainly — see §Pricing headroom |
| 14 | New/replaced clients per MSP per year | ~6 | `(assumption: ~15% annual client turnover + growth)` |
| 15 | **Steady-state onboarding revenue per MSP per year** | **~$9,000** | 13 × 14 |
| 16 | **Blended annual revenue per MSP, steady state** | **~$17,900** | 11 + 15 |

### Onboarding hours by client size — the correction that matters most

S21's "40–80 hours" is the typical-to-complex band ("2–3 weeks small, 8–12 weeks complex"), and the 60-hour case in [personas.md](personas.md) is an 80-seat client that the same file calls large for this book. Pricing the fee against that client while the ramp counts 16-user clients repeats round 1's error class in the half that now carries the revenue.

| Client size | Share of a typical book `(assumption)` | Onboarding hours `(assumption)` | Cost displaced at $75/hr |
|---|---|---|---|
| Small (≤10 users) | ~45% | 15–25 | $1,125–1,875 |
| **Typical (10–30 users) — the median** | ~40% | **25–40** | **$1,875–3,000** |
| Complex (30+ users, multi-site, compliance) | ~15% | 40–80 [S21] | $3,000–6,000 |

**Pricing headroom.** At $1,500 flat, the fee is 57–80% of the median client's displaced cost and **at or above 100% for the smallest clients** — where an MSP would rationally decline it. Two consequences the pack must carry: the fee should almost certainly be **banded by client size rather than flat**, and the flat-$1,500 model used throughout this build is therefore conservative for large clients and optimistic for small ones. **The blended figure survives; the flat structure does not.** `financials/pricing.md` owes the banded schedule.

**The onboarding fee is not a second tariff bolted on — it is half the revenue and the half that arrives first.** Ticket revenue accrues only after an environment is live; the onboarding fee is billed at the moment of the work the buyer already pays 40–80 hours for.

## 3. The ramp — what a customer is actually worth in year 1

An MSP does not onboard 41 environments on signature. Modelling the ramp is what the first version missed:

| Year | Environments live | Onboarding fee — **one-time backfill** | Onboarding fee — **recurring** (new clients) | Ticket revenue — **recurring** | **Total** |
|---|---|---|---|---|---|
| 1 | 5 (backfill) | $7,500 | — | ~$1,090 | **~$8,600** |
| 2 | 15 cumulative | $15,000 | — | ~$3,250 | **~$18,250** |
| 3 | 30 cumulative | $22,500 | — | ~$6,500 | **~$29,000** |
| 4 | 41 (backfill complete) | $16,500 | ~$9,000 | ~$8,900 | **~$34,400** |
| **Steady state** | 41 + turnover | — | ~$9,000 | ~$8,900 | **~$17,900/yr** |

**3-year revenue per MSP ≈ $55,850; at 70% gross margin `(assumption, owed to financials/unit_economics.md)`, 3-year gross profit ≈ $39,100** — the number [gtm.md](gtm.md) derives its CAC ceiling from.

### Revenue quality — say this before a diligence call computes it

**Roughly 81% of three-year revenue ($45,000 of $55,850) is one-time backfill onboarding**, billed once per existing client and never again. Two consequences a sophisticated reader will price, so the pack states them first:

1. **This is implementation-shaped revenue during the land phase**, which earns a services multiple, not a SaaS one. It is the same revenue quality this pack criticises ServiceNow for [market_type.md](market_type.md); the difference is that ours *decays by design* as backfill completes, rather than being the permanent business model.
2. **Net revenue retention falls below 100% after backfill.** An MSP goes from ~$34,400 in year 4 to ~$17,900 at steady state — a 48% step down — unless its own client base grows. **Expansion revenue therefore depends on the MSP winning clients, which is exactly what [petal_diagram.md](petal_diagram.md) petal 2 says we help them do.** That is a coherent story, but it must be told: the growth case rests on customers' growth, not on seat expansion.

The durable recurring line is **~$17,900/yr per MSP**, and that — not the year-3 peak — is what a valuation should be built on.

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
3. **The internal-IT expansion market — an option, not a number in the headline.** `(assumption: ~200,000 US firms of 100–2,000 employees; 20% addressable = 40,000)` × `(assumption: ~500 users each)` × 0.8 × 25% × $6 × 12 ≈ **$7,200/yr each → ~$288M**. Three reasons it is **not added to SAM**: entering means competing on resolution quality, the axis [positioning.md](positioning.md) explicitly commits to avoiding, against competitors funded at $164.5M [S13] and an incumbent that paid $2.85B [S26]; an internal-IT customer has **one** environment, so the onboarding fee is a single event and the shape reverts to the ~$107M per-ticket-only model this file already calls insufficient; and the estimate rests on three stacked assumptions with no source. It is an option worth naming and not a market this pack claims.

**The honest summary a VC should be handed: a defended ~$215M SAM**, with a per-customer recurring line of ~$17,900 and a front-loaded backfill phase. The path beyond it runs through capturing more of the labour cost displaced — agent labour is 70–80% of the $22.50 blended cost per ticket [S28] and $6 captures roughly a quarter of it — and, optionally, through internal IT on terms this pack has not defended. **Summing the two into a $500M headline is the move a skeptical reader is looking for; it is not made here.**

## Gap — stated, not guessed

**No sourced MSP ticket-category mix exists.** Row 8 is the second-most load-bearing number in the pack and it rests on a category argument, not data. Every free source found describes internal IT desks, whose mix excludes RMM-generated alert tickets, hardware and on-site work. **Two questions, both cheap to ask and both moving the SAM: the ticket-category mix, and specifically the RMM-alert share of volume. These are the single highest-value questions in the first ten discovery interviews**, and until it is answered the SAM carries a ±40% honest uncertainty that no sensitivity table can remove.

**Recommended next 3 moves:** (1) get real ticket-category mix and per-client ticket volume from the first 5 MSP interviews — rows 6 and 8 are worth more than any other research; (2) test the $1,500 onboarding fee against the 40–80-hour incumbent cost in the same conversations; (3) size internal IT properly before the seed raise rather than carrying §5.3's assumption chain into a deck.
