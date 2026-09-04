# Go-to-market

> **What this is** — the channel strategy by segment, the acquisition loop meant to compound, a CAC hypothesis per channel with payback logic, and the 90-day motion from first customer to first ten.
> **Why it exists** — at ~$8,600 year-1 revenue per MSP and ~$17,900 at steady state [market_sizing.md](market_sizing.md), most enterprise go-to-market motions are arithmetically impossible: a $40k acquisition cost never pays back, and even the primary channel has no slack. This file exists to make that constraint explicit before the seed round is spent discovering it.
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

1. **MSP peer communities and mastermind groups** *(primary)*. MSP owners buy what other MSP owners run, and these groups exist specifically to exchange that. Trust is inherited, so the sales cycle collapses once you are inside. **CAC, entry cost and time-to-first-close are computed in [channel_plan.md](channel_plan.md) and are not restated here** — the two files drifted apart once already. Summary: not cheap ($4,000–9,000) and not fast (6–9 months to first close, including membership approval).
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

**Access precondition, stated because the engineering one was not enough.** [channel_plan.md](channel_plan.md) §Entry cost establishes that peer communities take 3–9 months to enter and may not admit a vendor at all. **The first ten conversations therefore cannot come from that channel** — it is the channel being built, not the one being used. Day-1 sources are open ones: r/msp and the MSP Discord/Slack communities, LinkedIn outreach to owners of 10–100-person MSPs, MSP-podcast host audiences, and warm paths through any RMM/PSA vendor contact. Lower trust, higher volume, available immediately.

**Days 1–30 — ten conversations, no product pitch, plus the access test in parallel.** Marcus-profile owners from the open sources above. Ask what onboarding costs in hours; do not describe the product until the pain is stated unprompted. **Run channel_plan.md's fortnight admissibility test alongside it:** name three specific peer/buying groups, establish membership rules, vendor terms and whether the founder can join at all. **Exit:** ≥6 of 10 rank onboarding in their top 3 pains, *and* a yes/no on admissibility to three named groups.

**Days 31–60 — build the minimum pipeline; days 61–120 — the A8 transfer test.** Correcting the first revision, which said the lab test needed "no product". It does not need security review, a pilot agreement or tenant isolation; it *does* need capture, clustering, skill synthesis, an executor and an evaluation harness — the core loop minus governance. Name that as a build window rather than hiding it inside a 30-day slot.

The test itself — three engineers × five procedures × two environments, per BRIEF's decisive test — also needs **three engineers who can perform real Okta/M365/AD procedures competently**, which a solo founder does not have on hand. Sources, in order of preference: a design partner lending two engineers for a day, paid contract MSP technicians `(assumption: ~$100/hr, ~16 hours total, ~$1,600)`, or moonlighting tier-2 techs. **The honest schedule is days 31–120, not 31–60**, and the plan already accepts that discipline for the paid pilot. **Exit:** a measured cross-environment skill success rate.

**Days 121–150 — recorded walkthrough to three design partners, and publish the *method*.** Show a synthesized skill executing against a lab environment; secure design-partner commitments contingent on a build milestone. Publish the evaluation method and the first data point — not a yardstick claim, which needs ≥3 environments across ≥2 MSPs before it means anything. **Exit:** three signed design-partner LOIs and one published method.

**Days 180–240 — first paid pilot**, gated on a shipping capture-and-execute path and the tenant-isolation document Sonia's review opens with.

**First 10 customers by type:** 3 design partners (converted), 4 from the peer group of those 3, 2 from newsletter/podcast attribution, 1 inbound from the published number. **First 100:** requires the marketplace channel. Two distinct partner events, conflated in the first version: an **intelligence call in month 2** to price the revenue share, and a **listing application** gated on a shipping integration, SOC 2 and reference customers — realistically month 18–24. First-100 is a two-year horizon, not a year-one one, and no artifact should imply otherwise.

## 5. What would falsify this GTM

- The founder is not admissible to peer or buying groups as a vendor → the primary and best-economics channels are both closed, and the plan reshapes around the marketplace at 18–24 months. **This is the fastest and cheapest thing to find out, and it is now a day 1–30 exit criterion.**
- Peer-community introductions convert below 20% to a booked call → trust is not inheritable here, and CAC assumptions collapse.
- Design partners will not permit even **anonymised** publication ("a 34-person Midwest MSP") → the compounding loop has no fuel and this becomes a conventional, more expensive motion. Note the pilot agreement no longer asks for named-client numbers [sales_roadmap.md](sales_roadmap.md) step 6.
- Environment #2 at the same MSP requires a sales conversation → land-and-expand is false, and revenue per MSP is capped at the single-environment figure.

**Recommended next 3 moves:** (1) join two MSP peer communities as a participant before selling anything — the channel is the relationship; (2) build the engineer-hours ROI calculator as the first marketing artifact, per [petal_diagram.md](petal_diagram.md); (3) run the 100-email cold test once, early, to price the floor honestly.
