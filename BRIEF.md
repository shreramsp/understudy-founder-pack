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

**Core loop:** record (screen · clicks · spoken reasoning) → cluster → deduplicate → synthesize `SKILL.md` → simulate in parallel with a human → govern with approval gates on destructive actions → execute autonomously, escalating the hardest cases. No model training anywhere in the loop; skills are text, readable and auditable by the engineer they came from.

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

**Per resolved ticket** — outcome pricing, directly comparable to the $5–13/ticket figures the category publishes. Recurring, expands per client environment onboarded. Signed by the MSP owner/COO.

## Founder edge

AI/agents engineering depth. The clustering-and-skill-synthesis core is the hard technical bet in this company, and it is the founder's ground — founder-market fit argued on the mechanism rather than on years in managed services. *(The market-side gap is named honestly in ASSUMPTIONS.md A6 rather than papered over.)*

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
