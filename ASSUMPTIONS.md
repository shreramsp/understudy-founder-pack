# Understudy — Assumptions Log

> **What this is** — every choice made without founder confirmation during the grill, with its basis and whether the pack collapses if it is wrong.
> **Why it exists** — a brief reads as settled fact, and six weeks later nobody remembers which lines the founder said and which the agent decided. This file keeps that boundary visible, so a skeptic attacks the assumption rather than the artifact built on it.
> **How to read it** — scan the `kills-pack-if-wrong: yes` rows first; those are the ones that propagate. A1 is cosmetic, A2–A4 are structural.
> **Depends on / feeds** — derived from [BRIEF.md](BRIEF.md); feeds `validation/riskiest_assumptions.md`, which ranks these alongside the lean-canvas ⚠ cells and tests them.

Confirmed by the founder in the grill (**not** assumptions): MSP beachhead · hybrid global+tenant skill library · per-resolved-ticket pricing · riskiest assumption is skill-clustering reliability · why-now is the computer-use threshold · founder edge is AI/agents engineering · MSP owner/COO signs · 10-year vision is 10x clients per engineer.

| # | Assumption | Basis | Kills pack if wrong |
|---|---|---|---|
| A1 | Working name **"Understudy"** | The idea had no name. An understudy watches the performer, rehearses, goes on under supervision, then takes the role — which is the four-phase ladder exactly. Cosmetic; overrule in one word. | no |
| A2 | Edge-low is the tier-1 helpdesk technician; edge-high is the senior escalation engineer | Quality-bar property 4 requires all three spectrum edges; the founder named only the beachhead. Derived from standard MSP service-delivery tiering. | no |
| A3 | The three why-now factors are ranked with computer-use as primary and the other two as supporting | Founder selected computer-use; the skill format and inference-cost points follow from the material's "no model training" and clustering design. | no |
| A4 | ~~Competitor failure modes are founder-asserted and unverified~~ **RESOLVED by research, and it reframed the wedge** | Discovery-by-recording is **not** unattempted: task mining is a mature category (UiPath, Celonis) and FortressIQ built and sold a company on it [S5][S7]. But no one closes recording → execution; the handoff is manual. See [research/landscape.md](research/landscape.md). | resolved — the sharper claim ("nobody closes the loop") replaces the false one ("nobody does discovery") |
| A5 | The MSP market is large enough to carry a venture-scale outcome at per-ticket pricing | Not yet sized. Bottom-up build owed in `strategy/market_sizing.md`; MSPs are numerous but individually small, and this is the likeliest place the story breaks. | **yes** |
| A6 | Founder-market fit is argued on the mechanism, with no MSP operating history | Founder selected "AI/agents engineering depth" over MSP experience. The pack must compensate with design-partner evidence rather than claimed domain authority. | no |
| A7 | Engineer consent to recording is tractable at MSPs | MSPs already record sessions for QA and training, and engineers are employees rather than customers. Weaker at in-house IT, which is a reason the beachhead is what it is. | no |
| A8 | Global-layer skills transfer between client environments without carrying client-specific data | The moat depends on it and the privacy story depends on it. Untested; second only to the clustering assumption in load-bearing weight. | **yes** |
| A9 | Per-ticket pricing is acceptable to MSP buyers who bill their own clients per seat or per device | Outcome pricing is where the category is converging, but MSP revenue is not per-ticket, so the metrics may mismatch at the margin. Owed a check in `financials/pricing.md`. | no |
| A10 | "Generic across IT stacks" means broad coverage of the common stack, not literally any stack | Founder wrote "not ServiceNow-specific". Scoped to Okta / M365 / Active Directory / Jira as the global layer's first targets. | no |

## Resolved during the run

- **A4** closed by phase 1 (see row above). The correction strengthens the pitch: the gap is narrower, better evidenced, and explains *why* it persisted.
- **A5** (MSP market size) now has inputs: managed services ≈ $424–437B in 2026 [S17], 88% of SMBs use an MSP, average MSP manages 1,247 endpoints [S18]. Still owed a bottom-up build in `strategy/market_sizing.md`.
- **New, promoted to pack-killing — A11:** the brief's phase-4 autonomy is not supportable by current long-horizon agent performance (20.6% on OSWorld 2.0 [S16]). The pack will claim discovery + governed execution and treat full autonomy as direction, not deliverable.
- **New — A12:** EU deployments face a real constraint on the capture step: continuous screen recording is generally treated as disproportionate, consent is a weak legal basis, and works councils hold co-determination rights in DE/NL/AT/SE [S29]. US-first is now an implicit assumption.

## Founder decisions taken during the run

| # | Decision | Date | Consequence |
|---|---|---|---|
| D1 | **A11 accepted.** Scope is discovery + governed supervised execution; autonomy is direction, not deliverable | 2026-09-04 | Binding claim boundary in [BRIEF.md](BRIEF.md). No artifact may imply unattended autonomy; the revenue build may not price it |
| D2 | **RPA differentiation is a required argument**, not an optional one — narrated skills degrade gracefully under UI change where scripted bots break | 2026-09-04 | Mandatory explicit section in `tech/whitepaper.md` and `narrative/vc_memo.md`; tested as **E2** in `validation/experiment_board.md` against a deliberately altered UI, with an RPA-style scripted baseline |
| D3 | **A12 stands. US-first** | 2026-09-04 | EU is a later-market question with a named legal constraint, not a launch geography. `strategy/market_sizing.md` sizes US SAM |
| D4 | **Two-part tariff confirmed** — per resolved ticket (~$6) **plus $1,500 per environment onboarded** | 2026-09-04 | Supersedes the round-1 per-ticket-only answer. Per-ticket alone yields ~$107M SAM and a year-1 customer worth ~$1,100, at which no channel in `strategy/channel_plan.md` is viable. The onboarding fee is ~87% of year-1 revenue and prices against the 40–80 engineer-hours it displaces [S21]. Binding on `financials/pricing.md` and `financials/revenue_build.md` |
| D5 | **D2's mechanism restated: contract vs. goal, not coordinates** | 2026-09-04 | Enterprise RPA uses attribute-based selectors, not screen coordinates; the original framing would have been falsified by any practitioner. The claim is that an RPA step is a contract against a specific application build with no success criterion, while a narrated skill carries a goal state and verification step. **E2's baseline must be selector-based** or the experiment is rigged. Binding on `tech/whitepaper.md`, `narrative/vc_memo.md`, `validation/experiment_board.md` |

| D6 | **In-boundary distillation is an architecture constraint, not a preference.** Raw recordings never reach the vendor; only the abstracted variance envelope crosses | 2026-09-04 | Binding on `tech/architecture/`. **Corrected the same day after critic review:** the boundary is the **MSP's tenant**, not each client's. Stage 1 (cluster + abstract) runs on one node per MSP across that MSP's environments; stage 2 (global clustering) runs centrally on abstracted envelopes only. The original "inside the client boundary" wording was not implementable — capture originates on MSP workstations, cross-environment clustering needs environments co-located, and SaaS-only clients have no perimeter. **The founder's intent is preserved and the fleet drops from ~41 nodes per customer to 1.** Relocation confirmed by the founder 2026-09-04 — **D6 is settled.** The envelope schema is binding and auditable: `{procedure_shape, precondition_pattern, deviation_class, observation_count}`, carrying no tenant name, domain, user, policy id or configuration value |
| D7 | **Banded onboarding fee, scaled to client size** | 2026-09-04 | Supersedes the flat $1,500 in D4's first form. `financials/pricing.md` owes the schedule; bands follow the client-size distribution in `strategy/market_sizing.md` (small ≤10 users / typical 10–30 / complex 30+). The blended revenue figure is unchanged; the structure is not |

| D8 | **The environment-1-costs-more finding stays visible** — in [journeys/beachhead.md](product/journeys/beachhead.md), in the onboarding meter (F20/S9), and in every ROI artifact | 2026-09-04 | Founder directive: *"we'd rather a design partner's timesheet confirm our number than falsify it."* Binding on `strategy/gtm.md`'s engineer-hours ROI calculator, on `narrative/` (no artifact may quote a first-environment saving), and on `startup-website` — the quantified proof block must lead with compression at environment 2, never with environment 1 |

## Open questions for the founder

1. Is there any existing recording corpus, design partner MSP, or prior pilot — or is this genuinely zero-evidence today?
2. Team: solo, or co-founders with the MSP-side experience A6 says is missing?
3. Is a raise being planned, and roughly at what size? `financials/use_of_funds.md` needs a number to build against, and will otherwise assume a pre-seed.
