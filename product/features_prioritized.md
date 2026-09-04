# Prioritized feature list — 50 features, Now / Next / Later

> **What this is** — fifty features in strict priority order across three tiers, each with its mechanism, the user value it produces, its dependencies, and a size.
> **Why it exists** — [features_flagship.md](features_flagship.md) argues what matters; this file decides what gets built first and what is deliberately deferred. Priority here is **risk-ordered, not chronological**: the earliest items are the ones that retire the assumption that kills the company, not the ones a user sees first.
> **How to read it** — the Now tier is the whole bet. If N1–N8 fail, nothing below them matters and the Next tier should never be started. A skeptic should check that no Later item is secretly a dependency of a Now item.
> **Depends on / feeds** — inherits [PRD.md](PRD.md) §4–§5, [features_flagship.md](features_flagship.md); feeds `tech/`, [journeys/](journeys/), `validation/experiment_board.md`.

Effort: **S** ≤2 weeks · **M** 2–6 weeks · **L** >6 weeks, solo-founder baseline. Principle tags refer to [PRD.md](PRD.md) §4.

## NOW — retire the core assumption (F5 clustering) or stop

Nothing in this tier is user-facing polish. It exists to answer whether recorded sessions become reliable skills.

**D6 binds this tier.** In-boundary distillation was previously an L-tier item; it is now an architecture constraint on N6 and N9, because retrofitting a boundary into a pipeline built without one is far more expensive than assuming it. The N-tier is therefore designed edge-first from the start.

| # | Feature | Mechanism | User value | Depends on | Effort |
|---|---|---|---|---|---|
| N1 | Screen + input capture agent | OS-level capture of screen, input events, window/app context | Nothing yet — the substrate | — | M |
| N2 | Session segmentation | Split a shift into discrete task episodes by idle gaps, app focus and ticket context | Recordings become units that can be compared | N1 | M |
| N3 | Action extraction | Convert raw capture into a typed action stream (clicked X in app Y, entered value class Z) | The representation clustering operates on | N2 | L |
| N4 | Sensitive-value redaction | Detect and drop credentials, tokens, PII at capture time, before storage | The precondition for any security conversation | N1 | M |
| N5 | Failure/abort labelling | Retain and mark sessions ending in escalation or rollback | Recovery behaviour becomes learnable (`P2`) | N2 | S |
| N6 | Cross-session clustering, **in-boundary** | Group episodes of the same procedure across engineers and environments — **executing inside the client perimeter (D6)** | **The core bet** (`P1 P7`) | N3 | L |
| N7 | Skill synthesis to `SKILL.md` | Emit goal, preconditions, steps, **success criterion**, escalation envelope | A readable, executable artifact (`P3 P6`) | N6 | L |
| N8 | Evaluation harness | Run a synthesized skill against a held-out environment and score it | **The only way to know if N6 works**; also the E2/A8 instrument | N7 | M |
| N9 | Variance envelope extraction **+ boundary egress filter** | Keep the distribution of how a procedure differed; the envelope is the **only** artifact permitted to cross the client boundary, and the filter is what enforces it (D6) | The moat, made into data — and the security answer, made structural (`P7`) | N6 | M |
| N10 | Decision-point narration | Prompt for ~10s of voice at detected branch points | Attacks demonstration underdetermination (`P1`) | N2 | M |
| N11 | Engineer capture controls | Indicator, pause, post-session review before distillation | Consent is structural, not promised (`P8`) | N1 | S |
| N12 | Skill viewer | Read a skill as text, with the sessions and authors it came from | Ray's "show me what it learned" — the demo that converts | N7 | S |
| N13 | Authorship attribution | Name the contributing engineers on every skill | `P8`; the capture programme survives | N6 | S |
| N14 | Onboarding meter | Engineer-hours and time-to-first-verified-skill per environment | **The GTM number** [strategy/gtm.md](../strategy/gtm.md) | N8 | S |

## NEXT — earn the right to act

Only after N6–N8 show cross-environment transfer. Shadow before gate, gate before act — no exceptions.

| # | Feature | Mechanism | User value | Depends on | Effort |
|---|---|---|---|---|---|
| X1 | Read-only executor | Execute non-mutating steps against a real environment | The first live action, with nothing at risk | N7 | L |
| X2 | Shadow mode | Skill runs against live tickets without acting; outcomes compared to the human's | Trust bought before risk taken (`P5`) | X1 | M |
| X3 | Deviation report | Route each divergence to the authoring engineer as a question | Corrections flow back (`P2 P6`) | X2 | M |
| X4 | Success-criterion verification | Test the declared criterion after every action | What RPA structurally lacks (`P3`) | X1 | M |
| X5 | Action-class policy | read / reversible-write / destructive, destructive always gated | `P9`; the security conversation becomes concrete | X1 | S |
| X6 | Approval queue | Human approves gated actions with a one-line summary of effect | Dana and Ray stay in control | X5 | M |
| X7 | Agent identity integration | Own principal in the client IdP; every action attributable | Sonia's audit answer (`P8 P9`) | X1 | M |
| X8 | Reversible-write execution | Mutating actions that can be undone, with the undo path recorded | Real work, bounded risk | X4 X5 | L |
| X9 | Envelope enforcement | Preconditions unmet → escalate rather than improvise | `P5`; no silent overreach | X4 | M |
| X10 | Promotion ladder | shadow → gated → supervised, on thresholds declared in advance | Adoption at the customer's pace | X2 X6 | M |
| X11 | Re-grounding on UI change | Search against the intact goal when a step breaks | **The D5 claim, shipped** (`P3 P4`) | X4 | L |
| X12 | Drift detection | Falling verification rates pause a skill before it acts wrongly | `P4 P9` | X4 | M |
| X13 | Envelope widening | Deviations and corrections update the variance envelope | The library hardens rather than just grows (`P7`) | X3 N9 | M |
| X14 | Ticket-system integration (read) | Pull ticket context from the PSA/ITSM | Skills fire against real work, not synthetic prompts | X1 | M |
| X15 | Ticket-system integration (write) | Write resolution notes and status back | Closes the loop the MSP is measured on | X14 X8 | M |
| X16 | Tenant isolation architecture | Private per-client layer; global layer provably carries no client data | **Gates every deal** [strategy/sales_roadmap.md](../strategy/sales_roadmap.md) | N7 | L |
| X17 | Global stack layer | Shared procedure shapes for Okta/M365/AD/Jira | New environments start warm (A8) | X16 N9 | L |
| X18 | Test-account self-exploration | Bounded read-only discovery beyond what was recorded | Coverage without more recording (`P1 P4`) | X1 | M |
| X19 | Skill correction UI | Engineer edits a skill; the edit is versioned and credited | `P6 P8`; the library stays theirs | N12 | M |
| X20 | Environment dashboard | Per-client view: skills live, coverage, hours saved | What Dana opens each morning | N14 | S |
| X21 | Audit export | Action log with skill version and verification result | Sonia's recurring review, answered with a file | X7 X4 | S |
| X22 | Retention policy engine | Raw sessions expire on schedule; skills persist | The highest-sensitivity artifact has the shortest life | N4 | S |

## LATER — scale, expand, and the things that look urgent but are not

| # | Feature | Mechanism | User value | Depends on | Effort |
|---|---|---|---|---|---|
| L1 | Multi-MSP global layer | Variance patterns pooled across customers, no client data | The flywheel at scale (A8) | X17 | L |
| L2 | Skill marketplace | MSPs publish and consume skill packs | Network effect on top of the library | L1 | L |
| L3 | RMM/PSA marketplace listing | Distribution through where MSPs already shop | The only path to 100 customers — 18–24 months [strategy/channel_plan.md](../strategy/channel_plan.md) | X15 | L |
| L4 | SOC 2 Type II evidence | Controls, monitoring, audit | Gates enterprise-adjacent clients *and* L3 — **start the clock early** | X16 X21 | L |
| L5 | Alert-ticket remediation | Skills triggered by RMM alerts rather than users | Possibly the most mechanisable queue segment [strategy/market_sizing.md](../strategy/market_sizing.md) row 8 | X14 | M |
| L6 | Banded onboarding pricing | Fee scaled by client size | Fixes the flat-$1,500 structure the sizing shows fails at small clients | N14 | S |
| L7 | Client-facing transparency portal | The MSP's client sees what is captured and what leaves | Shortens the recurring 6-week review | X21 | M |
| L9 | Skill test generation | Auto-generate regression tests per skill | Drift caught before production | X12 | M |
| L10 | Multi-engineer consensus | Reconcile conflicting procedures from different engineers | Resolves "whose way is right" at scale | X3 | M |
| L11 | Escalation routing intelligence | Route by who authored the relevant skills | Ray gets fewer, better interruptions | X9 N13 | M |
| L12 | Onboarding simulator | Replay a new environment against the library before going live | Quotes onboarding time before the contract | X17 | M |
| L13 | Engineer contribution dashboard | Skills authored, reuse, hours saved by their work | `P8` made rewarding, not just visible | N13 | S |
| L14 | Natural-language skill authoring | Write a skill without a recording | Covers the long tail recording misses | N7 | M |
| L15 | Mobile approval | Approve gated actions from a phone | Removes the after-hours bottleneck | X6 | S |
| L16 | Internal-IT deployment mode | Single-environment packaging | The expansion market, deliberately deferred | X17 | M |
| L17 | Cost/usage analytics | Inference cost per skill and per resolved ticket | Protects gross margin as volume grows | X4 | S |
| L18 | Skill deprecation workflow | Retire skills whose environment is gone | The library stays true rather than accumulating | X12 | S |
| L19 | Multi-language capture | Non-English narration | International, post-US | N10 | M |
| L20 | On-prem/air-gapped deployment | For clients that will not permit cloud processing | Unlocks regulated MSP clients | L8 | L |

## What is deliberately not on this list

- **Unattended autonomous execution.** Not deferred — excluded by the binding claim boundary (D1). It is not an L-tier item; it is a non-goal.
- **A ticketing system of our own.** We integrate (X14/X15); we do not replace.
- **EU deployment.** Blocked on legal analysis, not engineering (A12/D3).
- **Model fine-tuning.** Skills are text; no customer data enters a training loop (`P6`, and it is the sayable security answer).

**Recommended next 3:** (1) build N1–N8 and nothing else — the evaluation harness (N8) is what turns opinion into evidence and it is the item most likely to be skipped for looking un-shippable; (2) put N12 in front of a principal engineer the week it works, because that demo converts the persona that can veto adoption; (3) start L4's SOC 2 clock while N-tier is still in progress — it gates the marketplace and cannot be compressed later.
