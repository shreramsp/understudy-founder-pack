# Go-to-market

> **What this is** — the channel strategy by segment, the acquisition loop meant to compound, a CAC hypothesis per channel with payback logic, and the 90-day motion from first customer to first ten.
> **Why it exists** — at ~$28.3k annual revenue per MSP [market_sizing.md](market_sizing.md), most enterprise go-to-market motions are arithmetically impossible: a $40k enterprise-style acquisition cost never pays back. This file exists to make that constraint explicit before the seed round is spent discovering it.
> **How to read it** — the CAC ceiling in §2 is the governing constraint; every channel below is judged against it. A skeptic should attack the assumption that MSP peer communities convert at the rate claimed.
> **Depends on / feeds** — cites [market_sizing.md](market_sizing.md), [petal_diagram.md](petal_diagram.md), [personas.md](personas.md); feeds [channel_plan.md](channel_plan.md), [sales_roadmap.md](sales_roadmap.md), `financials/unit_economics.md`, `validation/get_keep_grow.md`.

## 1. The governing arithmetic

| Quantity | Value | Source |
|---|---|---|
| **Year-1** revenue per MSP (5 environments live) | **~$8,600** | [market_sizing.md](market_sizing.md) §3 ramp |
| 3-year revenue per MSP | ~$55,850 | ramp, years 1–3 |
| Target gross margin | 70% `(assumption: owed to financials/unit_economics.md)` | — |
| **3-year gross profit per MSP** | **~$39,100** | derived |
| **CAC ceiling at 3:1 LTV:CAC** | **~$13,000** | derived |
| **CAC target for a healthy seed-stage motion** | **≤$5,000** | `(assumption: 3:1 is the floor, not the goal; year-1 revenue of $8,600 means anything above ~$5k has a payback longer than the first renewal decision)` |

**Corrected after critic round 1.** The first version computed revenue across an MSP's entire client book and then added expansion on top, producing a $21,000 ceiling that flattered every channel. Revenue arrives one environment at a time; the ceiling is $13,000 and the year-1 constraint is tighter still.

**What this rules out immediately:** field sales, enterprise-style multi-threaded pursuit, conference booths as a primary channel, and any motion requiring more than roughly two sales touches plus a pilot. **What it demands:** channels where trust is inherited rather than purchased.

**And it makes the onboarding fee load-bearing for distribution, not just for revenue.** Year-1 value is ~$8,600 and roughly 87% of it is the per-environment fee [market_sizing.md](market_sizing.md) §3. A pure per-ticket model yields a year-1 customer worth ~$1,100, at which point no channel in [channel_plan.md](channel_plan.md) is viable — including the primary one.

## 2. Channel strategy by segment

**Beachhead — US MSPs, 10–100 employees.**

1. **MSP peer communities and mastermind groups** *(primary)*. MSP owners buy what other MSP owners run, and these groups exist specifically to exchange that. Trust is inherited, so the sales cycle collapses. Estimated CAC **$2,000–5,000** `(assumption: based on time cost of community participation rather than media spend)`. Slow to start, compounds hard.
2. **MSP-focused newsletters and podcasts** *(secondary)*. Narrow, cheap, and read by exactly Marcus. Works only with a concrete artifact — the engineer-hours ROI calculator, not a brand ad. CAC **$4,000–8,000** `(assumption)`.
3. **RMM/PSA marketplace listing** *(scale channel, year 2)*. Where MSPs already shop. Requires a partner relationship and carries a margin stack — see [channel_plan.md](channel_plan.md).
4. **Direct outbound** *(disqualifying test, not a channel)*. Run 100 cold emails once to measure the floor. If it converts below 5% to a call, it is confirmation the trust-inherited channels are the only viable ones, which is itself worth knowing cheaply.

**Expansion — internal IT.** Deliberately deferred. It is where every funded competitor is fighting [research/competitors.md], and entering it before the skill library compounds means competing on resolution quality, the one axis [positioning.md](positioning.md) commits to avoiding.

## 3. The compounding acquisition loop

```
   MSP onboards client environment
              ↓
   Global skill layer gets denser (A8)
              ↓
   Next MSP's first environment onboards measurably faster
              ↓
   "Time to first skill" becomes a number worth repeating
              ↓
   Owner tells peer group  ──────────→  next MSP
```

**This loop is the company's only real distribution advantage**, and it is the same asset as the moat: the product literally gets faster to deploy with each customer, which is a referenceable claim rather than a marketing one. It compounds only if skill reuse across environments is real (A8, ⚠ in [lean_canvas.md](lean_canvas.md)). **If A8 fails, this loop degrades to ordinary word of mouth and the CAC assumptions above are optimistic.**

## 4. The 90-day motion

**Engineering precondition, stated because the first version omitted it.** BRIEF.md records stage as *design — nothing implemented*. Multi-surface capture, clustering, skill synthesis, a governed executor and tenant isolation do not exist. The 90 days below are therefore an **evidence motion, not a deployment motion**: no step requires running in a customer's production environment, and the paid pilot sits at day 120–180 behind a stated build milestone. A plan that puts a live client onboarding at day 31 is a plan written as if engineering capacity were free.

**Days 1–30 — ten conversations, no product pitch.** Marcus-profile owners from peer communities. Ask what onboarding costs in hours; do not describe the product until the pain is stated unprompted. Simultaneously tests four business-model-canvas blocks. **Exit:** ≥6 of 10 rank onboarding in their top 3 pains.

**Days 31–60 — the A8 transfer test, on our own lab environments.** Three engineers × five procedures × two environments, per BRIEF's decisive test. Run in lab tenants we control, not in a client's admin plane — this needs no security review, no pilot agreement and no product, and it answers the assumption that decides the shape of the company. **Exit:** a measured cross-environment skill success rate.

**Days 61–90 — recorded walkthrough to three design partners, and publish the *method*.** Show a synthesized skill executing against a lab environment; secure design-partner commitments contingent on a build milestone. Publish the evaluation method and the first data point — not a yardstick claim, which needs ≥3 environments across ≥2 MSPs before it means anything. **Exit:** three signed design-partner LOIs and one published method.

**Days 120–180 — first paid pilot**, gated on a shipping capture-and-execute path and the tenant-isolation document Sonia's review opens with.

**First 10 customers by type:** 3 design partners (converted), 4 from the peer group of those 3, 2 from newsletter/podcast attribution, 1 inbound from the published number. **First 100:** requires the marketplace channel. Two distinct partner events, conflated in the first version: an **intelligence call in month 2** to price the revenue share, and a **listing application** gated on a shipping integration, SOC 2 and reference customers — realistically month 18–24. First-100 is a two-year horizon, not a year-one one, and no artifact should imply otherwise.

## 5. What would falsify this GTM

- Peer-community introductions convert below 20% to a booked call → trust is not inheritable here, and CAC assumptions collapse.
- Design partners will not permit publication of their numbers → the compounding loop has no fuel and this becomes a conventional, more expensive motion.
- Environment #2 at the same MSP requires a sales conversation → land-and-expand is false, and revenue per MSP is capped at the single-environment figure.

**Recommended next 3 moves:** (1) join two MSP peer communities as a participant before selling anything — the channel is the relationship; (2) build the engineer-hours ROI calculator as the first marketing artifact, per [petal_diagram.md](petal_diagram.md); (3) run the 100-email cold test once, early, to price the floor honestly.
