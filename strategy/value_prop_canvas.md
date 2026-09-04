# Value proposition canvas

> **What this is** — Osterwalder's customer-profile (jobs, pains, gains) mapped against the value map (pain relievers, gain creators, products) for the three personas who decide: the payer, the champion, and the veto.
> **Why it exists** — it is the artifact that catches a product solving a problem nobody ranks highly. Mapping per persona also exposes where a single feature relieves one persona's pain while creating another's — which, for a product built on recording people, is the central design tension.
> **How to read it** — read Ray's column last and treat it as the adoption gate. A skeptic should check whether every gain creator traces to a real product capability rather than an aspiration.
> **Depends on / feeds** — cites [personas.md](personas.md), [positioning.md](positioning.md); feeds `product/PRD.md`, `narrative/one_pager.md`, `startup-website`.

## Marcus (MSP owner — payer)

| Customer profile | Value map |
|---|---|
| **Jobs** — win clients he can staff; keep revenue/technician above $150k [S32]; protect margin on new logos | **Products** — discovery run on a new client environment, priced at **$1,500 against the ~25–40 engineer-hours it displaces** (D4); plus ~$6 per resolved ticket thereafter |
| **Pains** — 25–40 unbilled engineer-hours per median onboarding, 40–80 for complex ones [S21]; turning away business (26% of MSPs [S33]); knowledge loss on attrition | **Pain relievers** — onboarding cost falls per client *and* falls further with each client as the global layer compounds (A8); knowledge captured as an asset the business owns rather than a person does |
| **Gains** — take the next client without hiring; a diligence-friendly asset if he ever sells | **Gain creators** — the skill library is transferable business value; time-to-first-skill becomes a number he can quote to prospects |

**Top mapping (ranked):** 1. unbilled onboarding hours → discovery, priced directly against those hours. 2. staffing ceiling → per-client leverage. 3. attrition risk → library as owned asset.

**Note the pricing tension:** at $1,500 flat the fee captures 57–80% of the median client's displaced cost and approaches 100% for the smallest, where Marcus would rationally decline. The value proposition holds at the median and needs banding at the edges [market_sizing.md](market_sizing.md).

## Dana (service delivery manager — champion)

| Customer profile | Value map |
|---|---|
| **Jobs** — hold SLAs across 41 clients; keep the runbook true; get tier-1 self-sufficient | **Products** — the skill library as the runbook of record; client-specific procedures surfaced in the queue |
| **Pains** — documentation stale on arrival; the same problem re-solved at three clients; escalations that should not have been | **Pain relievers** — documentation maintained by observation instead of by nagging; a procedure solved once at any client becomes available at all of them (within the global layer) |
| **Gains** — fewer escalations; onboarding a new engineer takes days | **Gain creators** — reuse rate visible as a metric she can show Marcus |

**Top mapping:** 1. stale documentation → observed capture. 2. repeated escalations → library reuse.

## Ray (principal engineer — edge-high, the veto from below)

| Customer profile | Value map |
|---|---|
| **Jobs** — solve what nobody else can; not be interrupted 14×/day; not clean up after another failed automation | **Products** — readable `SKILL.md` text he can inspect and correct; governed execution with approval gates; escalation routing |
| **Pains** — constant interruption; two RPA cleanups behind him; **fear that a black box will act wrongly in production with his name on it** | **Pain relievers** — a skill states the **goal and its success test**, where an RPA step sequence states a **contract against a specific application build**; agent identity gives attribution [BRIEF]; approval gates on destructive actions; **the E2 experiment is the evidence, not a promise** (D2) |
| **Gains** — his expertise scales without him repeating it; he works on the genuinely hard 10% | **Gain creators** — his sessions become the highest-value skills in the library; he becomes the reviewer, which is a role, not a redundancy |

**Top mapping:** 1. black-box fear → readable skills + gates. 2. RPA scepticism → the contract-vs-goal mechanism + E2. 3. interruption load → library absorbs the repeat questions.

**Get the RPA argument technically right, or Ray ends the meeting.** Enterprise RPA has not primarily encoded screen coordinates for over a decade — UiPath uses attribute-based selectors over the accessibility tree with anchor and CV fallbacks; Blue Prism uses application-modeller attribute matching. Brittleness comes from **selector contracts breaking on application upgrades, unstable dynamic identifiers, timing and synchronisation, configuration drift, and unhandled unhappy paths** — which is what `research/survey.md` §6 actually says. Saying "not coordinates" to a practitioner falsifies the whole pitch in one sentence.

**The defensible claim:** an RPA step is a *contract* — do this, to this element, in this build — with no statement of what success looks like, so a break halts the run or, worse, proceeds wrongly. A narrated skill carries the **goal state and a verification step**, so a break becomes a re-grounding search against an intact success criterion. That is a real mechanical difference and it is testable. **It also constrains E2: the baseline must be a selector-based RPA script, not a coordinate-clicking toy, or the experiment is rigged and proves nothing.**

## The tension this canvas exposes

**The same capability that creates Marcus's gain creates Priya's and Ray's pain.** Capturing engineer work is an asset to the business and a threat to the person being captured. No amount of copy resolves that; only product decisions do — passive capture with visible controls, skills attributed to the engineer who authored them, and the absorbed work being the repetitive tier-1 layer rather than the interesting work. **If the pack ever pitches "replace your engineers", the champion and the edge-high persona both become blockers, and they are the ones the data comes from.**

**Recommended next:** design the engineer-facing side of the product — attribution, review, correction — as a first-class surface in `product/ux_spec.md`, not an admin afterthought. It is the difference between a data source that cooperates and one that quietly doesn't.
