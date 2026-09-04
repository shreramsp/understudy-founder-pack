# Understudy — Founder Brief

> **What this is** — the single source of truth every other artifact in this pack reads: who bleeds, the mechanism, the beachhead, and the one assumption that can kill the company.
> **Why it exists** — every downstream artifact inherits its beachhead (MSPs), its per-resolved-ticket pricing, and its riskiest assumption from this page. If recorded engineer sessions do not cluster into skills an agent can execute reliably, the rest of this pack argues for a screen recorder with extra steps — and the two-week test at the bottom is the cheapest way to find that out.
> **How to read it** — start at "Riskiest assumption" and "Mechanism & moat"; a skeptic should attack the clustering step and the claim that a global stack library transfers between clients.
> **Depends on / feeds** — pairs with [ASSUMPTIONS.md](ASSUMPTIONS.md); feeds `research/`, `strategy/positioning.md`, `validation/riskiest_assumptions.md`, `financials/pricing.md`.

one-line: **Understudy is the AI service desk that onboards itself — it records IT engineers doing real work, clusters those recordings into an executable skill library, and takes over tickets stack by stack, deploying in days instead of months of manual configuration.**
domain: ITSM · AI agents · managed services
stage: design (nothing implemented; no code, no pilot)

## Problem

Every AI service desk on the market can resolve a ticket. None can learn an unfamiliar IT environment without months of manual configuration — mapping the stack, writing runbooks, wiring integrations, encoding the local conventions that live in three engineers' heads. **Deployment friction, not resolution capability, is the bottleneck.**

For an MSP this is not an inconvenience, it is cost of goods. Every new client is a fresh configuration project priced in engineer-weeks, paid before a single ticket is deflected. The knowledge that would make automation work is being performed daily and captured nowhere.

## Users & spectrum

- **Edge-low:** tier-1 helpdesk technician — runs the same twenty procedures all day, is the first whose queue the agent absorbs, and gains escalation-grade backup on the twenty-first.
- **Beachhead:** MSP service delivery engineers across a book of client environments. They are the *source* of the skill library (their recorded sessions) and its first consumers. User ≠ payer.
- **Edge-high:** senior/principal escalation engineer — never automated, but freed from repetition and served the agent's simulation traces on the hard cases.
- **Payer:** MSP owner/COO (carries the P&L, buys margin per client). **Champion:** service delivery manager. **Veto:** whoever owns client security review.

## Why now

1. **Agents crossed the computer-use threshold in roughly the last 18 months** — models can watch a screen, execute a multi-step UI workflow and recover from a wrong click. This is the capability that converts a recording into an executable skill, and it did not exist in 2023. *(primary)*
2. Portable skill formats (`SKILL.md` / agent-skills) gave procedural knowledge somewhere to land that is not fine-tuning — the reason "no model training" is a design choice rather than a limitation.
3. Long-context and falling inference cost made hours of screen, click and narration tractable to deduplicate for dollars rather than thousands.

## Wedge & 10-year vision

**Wedge:** onboarding, done 10x better. Not "resolves more tickets" — *arrives already knowing this environment.* One MSP, one client stack, from recording to first autonomously resolved ticket in days.
**Vision (10 yr):** MSPs run 10x the clients per engineer. The economics of managed services are permanently restructured, and software that learns its environment by watching is the default expectation rather than a feature.

## Mechanism & moat

**Core loop:** record (screen · clicks · spoken reasoning) → cluster → deduplicate → synthesize `SKILL.md` → simulate in parallel with a human → govern with approval gates on destructive actions → execute under supervision, escalating anything outside the skill's envelope. No model training anywhere in the loop; skills are text, readable and auditable by the engineer they came from.

**Supporting design:** the agent holds its own identity for attribution, and self-explores with a test account to learn the environment beyond what was recorded.

**Moat — hybrid library.** Global skills for the stacks every client shares (Okta, M365, Active Directory, Jira) compound across every deployment, so each new environment starts warmer than the last; environment-specific skills stay in a private tenant layer that never crosses the boundary. The compounding half never touches customer data — which is what makes the flywheel survive security review. Secondary moat: workflow lock-in once the library is the runbook of record.

## Competition & failed alternatives (as stated by founder — to be verified in `research/`)

| Alternative | Why it falls short |
|---|---|
| Ravenna | AI-native ITSM, Slack-first, but no discovery — the environment is still configured by hand |
| Strawberry | Records workflows, browser-only — most IT work is not in a browser |
| ServiceNow (+ Moveworks) | Platform of record; configuration is the product's premise, not its problem |
| Do nothing | Tribal knowledge stays in three engineers' heads and leaves with them |

## Business model

**Two-part tariff** (founder-confirmed, D4): **~$6 per resolved ticket** — outcome pricing, comparable to the $5–13/ticket figures the category publishes and well under the buyer's own $22.50 blended cost [S27] — **plus $1,500 per environment onboarded**, priced against the 40–80 engineer-hours that onboarding costs today [S21].

The onboarding fee is not a second-order add-on: it is roughly 87% of year-1 revenue, it arrives at the moment of the work the buyer already resents paying for, and without it no acquisition channel is economically viable [strategy/channel_plan.md](strategy/channel_plan.md). Signed by the MSP owner/COO.

## Founder edge

AI/agents engineering depth. The clustering-and-skill-synthesis core is the hard technical bet in this company, and it is the founder's ground — founder-market fit argued on the mechanism rather than on years in managed services. *(The market-side gap is named honestly in ASSUMPTIONS.md A6 rather than papered over.)*

## Claim boundary — binding on every artifact in this pack

Founder decision, 2026-09-04, taken against the capability evidence in [research/capability_table.md](research/capability_table.md).

**What this pack claims:** environment discovery, and **governed, supervised execution with human escalation.**
**What it does not claim:** unattended autonomous resolution. Phase 4 of the original ladder is stated as *direction*, never as a deliverable, a roadmap date, or a number in the revenue build.

*Basis:* the best frontier system completes 20.6% of long-horizon OSWorld 2.0 tasks, where the median task takes a human 1.6 hours — the shape of a real ticket [S16]; agents scoring ~85% on standard OSWorld still fail ~80% of real workflows [S15]. A pack promising autonomy against that evidence fails its first technical diligence call. **Any artifact implying unattended autonomy is a defect, not a stretch goal.**

**Geography:** US-first. EU capture is constrained by data-protection practice treating continuous screen recording as disproportionate, and by works-council co-determination in DE/NL/AT/SE [S29] (A12).

## The RPA differentiation argument — required, not optional

Founder directive, 2026-09-04. **`tech/whitepaper.md` and `narrative/vc_memo.md` must each carry this argument explicitly**, because it is the single objection this company will be asked in every technical diligence conversation, and the base rate is against us: automation derived from observed work has failed in 30–50% of projects, with maintenance reaching 60% of total cost [S10][S11].

**The claim to make and defend:** a narrated procedural skill **degrades gracefully under UI change, where an RPA automation breaks.**

*Stated correctly — the first framing was technically wrong and would have lost the argument.* Enterprise RPA has not primarily encoded screen **coordinates** for over a decade: UiPath uses attribute-based selectors over the accessibility tree with anchor and CV fallbacks, Blue Prism uses application-modeller attribute matching. Saying "not coordinates" to a practitioner falsifies the pitch in one sentence. RPA brittleness actually comes from **selector contracts breaking on application upgrades, unstable dynamic identifiers, timing and synchronisation, configuration drift, and unhandled unhappy paths** [research/survey.md §6].

**The real mechanical difference is contract vs. goal.** An RPA step is a *contract* — perform this action, on this element, in this application build — carrying **no statement of what success looks like**, so a break either halts the run or proceeds wrongly. A narrated skill carries the **goal state and a verification step**, so a broken assumption becomes a re-grounding search against an intact success criterion. That is arguable as a mechanism and testable as an experiment. "We use an LLM" is not the argument.

**It must be tested against a fair baseline.** E2's RPA comparison must be a **selector-based** automation of the same procedure — not a coordinate-clicking toy, which would rig the result and prove nothing to the one persona (Ray) the argument exists to convince.

**The experiment:** `validation/experiment_board.md` carries E2 — synthesized skills executed against a **deliberately altered UI** (moved, renamed and re-ordered elements, plus a version upgrade that changes selectors), measuring skill success rate against the selector-based baseline on the identical alteration. Falsifiable, threshold declared in advance.

## Riskiest assumption

**That recorded sessions cluster into reliable, reusable skills** — rather than brittle transcripts of one engineer's happy path on one good day. If clustering yields procedures that break on the second client, there is no product; every environment becomes a cold start and the manual-configuration problem returns with extra steps.

*Cheapest decisive test:* record 3 engineers doing the same 5 procedures across 2 client environments; synthesize skills from environment A only; measure unattended success rate in environment B. Threshold declared in advance in `validation/experiment_board.md`.

## Vocabulary

- **core loop:** record → cluster → synthesize → simulate → govern → execute
- **skill:** one `SKILL.md` procedure, human-readable and auditable
- **skill library:** the per-role set of skills; global layer + private tenant layer
- **environment:** one client's IT stack
- **discovery:** the onboarding phase that produces the initial library
- **session:** one recorded engineer work period
- **unit of value:** a resolved ticket
- **outcome metrics:** autonomous resolution rate per environment · time-to-first-autonomous-skill · engineer-hours per client onboarded
