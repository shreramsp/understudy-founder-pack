# Understudy — a self-onboarding AI service desk for MSPs

> **Masters coursework.** The artifact pipeline that structured this pack is [dlmastery/startup-skills](https://github.com/dlmastery/startup-skills) (MIT). **The pipeline supplied the method. The idea, the 18 recorded decisions, the arithmetic, and everything the review process broke and rebuilt are this project's own.**
> **This is not a company.** No customers, no code, no traction, no revenue. Every figure carries a source tag or an `(assumption)` tag, and the pack names the number that would falsify its central claim.

**The idea in one line:** every AI service desk can resolve a ticket; none can *learn where it is*. Understudy records IT engineers working, clusters those recordings into a readable executable skill library, and takes over tier-1 work under supervision — sold to MSPs, for whom onboarding each new client environment is recurring cost of goods rather than a one-time setup.

**→ [Read the pack](https://shreramsp.github.io/understudy-founder-pack/pack.html)** · **[the site](https://shreramsp.github.io/understudy-founder-pack/)** · **[the visuals](https://shreramsp.github.io/understudy-founder-pack/visuals.html)**

---

## What this project actually demonstrates

Not that an idea can be written up at length. **That a structured adversarial process finds things the author cannot.**

Each layer was reviewed by three independent critics — a skeptical VC, a domain PhD, and an operator-founder — reading in isolation from the author. **Twelve load-bearing claims were written into this pack as settled fact and did not survive that review.** They are logged, with reasons, in [`validation/pivot_log.md`](validation/pivot_log.md):

| Claim as written | Why it died |
|---|---|
| Clustering runs inside the **client's** boundary | Not implementable — capture originates on MSP workstations, and a 22-person SaaS client has no perimeter to host a node in |
| The maintenance line delivers a **10×** | Its baseline was hours the pack itself calls "largely unperformed". A multiplier on hours nobody spends displaces no cost |
| "RPA has **no success criterion**" | Falsifiable in one sentence by any practitioner. Corrected three times before it survived |
| The privacy threshold counts **3 tenants** | One MSP brings ~41 tenants, so all three observations could sit inside one customer's book and identify them with certainty |
| Hosted inference for action typing | Frames of a client's admin console reaching a third party breaks the architecture's central guarantee outright |

**Three arithmetic errors were also caught, each in the direction that flattered the business:** a per-*endpoint* benchmark applied as per-*user* (2× inflation), revenue counted across a customer's whole client book and then given expansion on top (~40× on year-one value), and an annual figure compared against a monthly cost line (12×).

## What it cost to be honest

The pack states things a pitch would normally hide, and each one has a price recorded in the model:

- **The first client environment costs the customer *more* than doing nothing** — 31–46 engineer-hours against a 25–40 baseline. So it is given away free, which cut year-one revenue per customer from $8,600 to $5,110.
- **There is no 10×.** One real multiplier (~1.4× on repeat onboarding), one negative, and three effects that are not multipliers at all.
- **The pricing has no defensible basis on hours.** The fee is 99–466% of the time it saves. Both the charged schedule and the ~4× cheaper hours-justified one are published side by side, and the experiment that resolves it is designed as a split sample so it cannot be gamed.
- **On tickets we are at or above the buyer's own marginal cost**, so the pitch is capacity, not savings.
- **This is not a generational company** on the market it targets — ~$179M SAM — and the artifact says so instead of summing in an adjacent market it has not earned.

## Reading paths

**If you have five minutes** — [the one-pager](narrative/one_pager.md), then [what would falsify it](validation/riskiest_assumptions.md).

**If you want the argument** — [landscape](research/landscape.md) (why the gap exists) → [positioning](strategy/positioning.md) (the two axes) → [whitepaper](tech/whitepaper.md) (where the leverage actually is) → [VC memo](narrative/vc_memo.md).

**If you want the engineering** — [deep dives](tech/deep_dives.md) (seven systems, one genuine research bet) → [the privacy architecture](tech/architecture/D06.md) → [what ships and what does not](tech/not_vaporware.md).

**If you are checking the work** — [the coverage audit](audit/COVERAGE.md) (what is still open, and why one row is deliberately not closed) → [the decision log](ASSUMPTIONS.md) (18 decisions, each with its cost) → [the pivot log](validation/pivot_log.md).

## What is in here

| | |
|---|---|
| [`research/`](research/) | Landscape, competitor teardown, capability table, a dated survey, 36 cited sources |
| [`strategy/`](strategy/) | Market type, positioning, bottom-up sizing, personas, canvases, channel economics |
| [`product/`](product/) | PRD on nine first-principles, 61 prioritised features, four journeys, 13 screens |
| [`tech/`](tech/) | Whitepaper, seven deep dives, 11 architecture diagrams, 73 techniques |
| [`narrative/`](narrative/) | One-pager, VC memo, 17-slide deck, working-backwards press release |
| [`validation/`](validation/) | Ten experiments with thresholds declared before any data exists |
| [`financials/`](financials/) | Banded pricing, revenue build, unit economics, risk matrix, exit landscape |
| [`visuals/`](visuals/) | 20 rendered infographics, 46 further figures as prompts |
| [`audit/`](audit/) | Row-by-row completeness against the pipeline's own manifest |

**70 documents · 20 infographics · 30 commits · 60 of 61 required artifacts.**

## What is not finished, stated plainly

**One row is open and stays open.** 37 substantive documents have production-ready image prompts but no rendered image, because this run had no text-to-image tool. The audit records that rather than redefining coverage to make it disappear.

**Four review rounds were owed and deliberately stopped.** They would have found propagation debt — corrections reaching the file where an argument is made but not the files where it is restated, which is where roughly half the defects in this pack lived. That matters for investment diligence. It does not matter for coursework, and stopping was a judgement call, recorded in [`audit/COVERAGE.md`](audit/COVERAGE.md) rather than left implicit.

**No claim here has been tested against a real MSP.** Every row of the assumption board reads `untested`. Four of them would end the company, and three cost under $10,000 to check — which is the point the pack makes about its own sequencing.
