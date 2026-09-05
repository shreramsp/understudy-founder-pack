# MVP definition — two of them, kept distinct

> **What this is** — the low-fidelity MVP that tests whether the *problem* is real, the high-fidelity MVP that tests whether the *solution* is bought, and the earlyvangelist definition that says who counts as a real early customer.
> **Why it exists** — conflating these two is how a pre-build company spends ten months building the wrong thing carefully. A PRD is neither of them: it describes the product, not the cheapest artifact that could falsify it.
> **How to read it** — the low-fidelity MVP is not software, and that is deliberate. A skeptic should check that each MVP names what it *omits* as clearly as what it includes.
> **Depends on / feeds** — inherits [experiment_board.md](experiment_board.md), [../product/features_prioritized.md](../product/features_prioritized.md); feeds [stage_gate.md](stage_gate.md), `financials/use_of_funds.md`.

## Low-fidelity MVP — tests whether the problem is real

**It is not software.** It is: **the engineer-hours ROI calculator, plus a two-page tenant-isolation document.**

| | |
|---|---|
| **What it does** | Takes an MSP owner's own onboarding hours and client mix, and returns what the knowledge cycle costs them per year in their own numbers |
| **What it deliberately omits** | Any product. Any demo. Any claim about what we would save them |
| **The question it answers** | Does an MSP owner recognise onboarding cost as a top-three pain when shown their own arithmetic — *before* being shown a solution? |
| **What would falsify it** | Fewer than 6 of 10 rank it top-three unprompted (E3's exit criterion). Or: owners cannot produce an hours figure at all, which would mean the cost is real but unmeasured, and the sale becomes a measurement sale first |
| **Cost** | A spreadsheet and a document. Days |

**Why the isolation document is part of the low-fidelity MVP.** It looks like a compliance artifact. It is actually the test of whether D6's architecture is *sayable* — whether a client-side director reads it and asks two questions or twenty (E7). That is a problem-space finding, and it costs nothing to run early.

## High-fidelity MVP — tests whether the solution is bought

**The thinnest thing that could earn money: capture → distil → a readable skill library, with no execution at all.**

| | |
|---|---|
| **What it includes** | N1–N4, N6, N7, N11, plus the skill viewer (N12) and the onboarding meter (N14) |
| **What it deliberately omits** | **Execution.** No executor, no gating, no agent identity, no approval queue, no tenant isolation beyond the boundary itself |
| **The question it answers** | Will an MSP pay for a **library that is true** — a runbook maintained by observation — before it does any work? |
| **Why omitting execution is the right cut** | Execution is where the risk, the security review and most of the build sit. If the library alone is worth paying for, the company has revenue while it builds the executor. **If it is not, the executor was never going to rescue it** |
| **What would falsify it** | Owners say "so it's documentation" and decline. That is a real possible outcome and it would mean the value is in execution after all — which is a longer, more expensive company |
| **Cost** | The Now tier minus N0/N8/N15: roughly 20–26 weeks solo |

**Note what this does to the schedule.** The high-fidelity MVP is *smaller* than the transfer test's requirements, because E1 needs the harness and an executor stub while a paying library does not. **Those are two different first products and the pack should not pretend they are one** — `strategy/gtm.md` builds toward E1 because the evidence question outranks the revenue question at this stage, but a founder who needed revenue sooner would build this instead.

## Earlyvangelist definition — five things that must already be true

A prospect counts as an earlyvangelist only if **all five** hold. Anything less is an interested party.

1. **They have the problem** — they onboard client environments regularly, not once a year.
2. **They know they have it** — they can name it without being prompted (the discovery guide's exit criterion).
3. **They have been actively looking for a solution** — they have tried documentation platforms, scripting, a hiring push, or an internal process fix.
4. **They have cobbled together an interim workaround** — a shared runbook, a shadowing ritual, an onboarding checklist someone maintains by hand. **This is the highest-signal criterion**: a workaround is proof the pain is worth spending time on.
5. **They can commit budget** — the owner is in the room, or one step away.

**The MSP-specific reading of criterion 4:** almost every MSP has an onboarding checklist. That is not a workaround; it is table stakes. The workaround that qualifies is one built *because the checklist failed* — a senior engineer assigned to shadow-document, a Slack channel that functions as the real runbook, a rule that one person must be on every new client.

**Recommended next 3:** (1) run the low-fidelity MVP before writing any code — it is days of work and it gates everything; (2) hold the high-fidelity MVP's omission of execution deliberately, and be prepared to hear that the library alone is not enough; (3) score every discovery prospect against all five earlyvangelist criteria and record the count — a pipeline of interested parties who fail criterion 4 is the most flattering and least predictive thing a founder can accumulate.
