# Positioning

> **What this is** — the two axes that actually divide this market, where every competitor sits on them, the open quadrant, and the one-sentence positioning statement everything customer-facing inherits.
> **Why it exists** — positioning chosen badly sends a pre-seed company to fight $164.5M-funded incumbents on resolution quality, an axis it cannot win. This file commits to the axis where the competition is empty and explains why it stayed empty.
> **How to read it** — the axes are the argument; the statement is the output. A skeptic should attack whether buyers actually decide on these axes rather than on price, brand or integration breadth.
> **Depends on / feeds** — cites [research/competitors.md](../research/competitors.md), [market_type.md](market_type.md); feeds [value_prop_canvas.md](value_prop_canvas.md), [gtm.md](gtm.md), `narrative/one_pager.md`, `startup-website`.

## The axes — discovered, not defaulted

Price × quality is not the map here. Every system in the teardown differs on two structural questions:

**Axis 1 — How does the system acquire knowledge of the environment?** *Configured by a human* ⟷ *Observed from work being done.*
**Axis 2 — What does it do with that knowledge?** *Produces an artifact a human must act on* ⟷ *Executes it directly.*

These are the axes because they predict the buyer's actual cost. Axis 1 sets what onboarding costs — 40–80 engineer-hours per client today [S21], 3–5× licence at enterprise scale [S20]. Axis 2 sets whether that cost ever converts into resolved work or stops at a document.

## The map

| | **Produces an artifact** | **Executes directly** |
|---|---|---|
| **Configured by a human** | IT Glue / Hudu, runbooks, RMM scripts | Ravenna, Atomicwork, Aisera, Espressive, Moveworks/ServiceNow |
| **Observed from work** | FortressIQ, UiPath Task Mining, Celonis | **← empty. Understudy.** (Strawberry at the boundary, browser-only) |

**Three quadrants are crowded; the fourth is empty for a reason that expired in 2024.** Acting on an observed procedure required an executor that could work a real UI reliably. Computer-use agents went from 12% to ~85% on OSWorld between April 2024 and June 2026 [S14][S15], and `SKILL.md` became a portable cross-vendor format for the result [S24]. FortressIQ recorded employees from 2017 with no executor to send the output to, and ended as a feature inside an RPA vendor [S5][S6]. Same input, wrong decade.

## Positioning statement

> **For MSPs onboarding client environments, Understudy is the only service desk that learns the environment by watching engineers work — because a recorded session becomes an executable skill, not a diagram someone still has to implement.**

Decomposed, so every downstream artifact uses the same load-bearing parts:

- **For MSPs onboarding client environments** — the segment and the moment. Not "IT teams"; not "companies with tickets".
- **the only service desk that learns the environment by watching** — the category we join, and the claim that separates us within it.
- **because a recorded session becomes an executable skill** — the mechanism. This clause is why the claim is credible; it must never be dropped for brevity.
- **not a diagram someone still has to implement** — the teardown of the adjacent category, in six words.

## What we deliberately do not claim

- **Not "resolves more tickets than X".** Resolution quality must be sufficient, not superior (see [market_type.md](market_type.md)). Competing on that axis is competing with Moveworks' distribution and Aisera's balance sheet.
- **Not autonomy.** Per the binding claim boundary in BRIEF.md (D1): discovery plus governed, supervised execution. Any copy implying unattended resolution is a defect.
- **Not "AI-powered".** Every competitor is. The differentiator is the acquisition axis, not the model.

## The wedge sentence for a 30-second conversation

*"What does it cost you in engineer-hours to onboard a new client? We watch your engineers do the work once and turn it into skills the desk can run — so client three onboards faster than client one."*

That question is the positioning working: no incumbent's messaging invites it, and 26% of MSPs are already staff-constrained on exactly this [S33].

## Decision

**Commit to the observed × executes quadrant and defend it with the variance envelope, not the skill list.** The idea is visible to anyone reading ALLOY [S22], and the happy-path skills for Okta, M365, AD and Jira are authorable from vendor documentation — that half of the library is copyable in a quarter and claiming otherwise invites the obvious rebuttal. What is not copyable is the observed distribution of how those procedures actually differ across dozens of real environments, how they fail, and how engineers verify them; that accrues only from deployments. See [lean_canvas.md](lean_canvas.md) ⚠. **It remains an assumption (A8), not a finding.**

**Recommended next 3 moves:** (1) put the wedge sentence in front of 10 MSP owners and measure whether the onboarding-hours question lands cold; (2) do not publish a resolution-rate number until an independent one exists; (3) name and instrument time-to-first-skill as the category yardstick before a competitor names their own.
