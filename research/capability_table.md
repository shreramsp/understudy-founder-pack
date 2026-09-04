# Enabling-technology capability table — as of 2026-09-04

> **What this is** — the state of the art in each capability Understudy's core loop depends on, with measured performance, cost direction, and the gap between what is published and what the product needs.
> **Why it exists** — "why now" is the claim investors check hardest, and it is only defensible if each link in the loop is independently at or above threshold today. This table is also where the product's honest ceiling is set: two links are not yet strong enough for the autonomy the brief's phase 4 describes.
> **How to read it** — the Gap column is the important one. A skeptic should go straight to rows 2 and 3, where the benchmark headline and the real-workflow number diverge sharply.
> **Depends on / feeds** — cites [sources.md](sources.md); feeds `tech/whitepaper.md`, `tech/not_vaporware.md`, `strategy/market_type.md`, `validation/riskiest_assumptions.md`.

| # | Capability | Best current system | Measured performance | Cost trend | Fit to the loop | **Gap** |
|---|---|---|---|---|---|---|
| 1 | **UI understanding from screen capture** | Frontier multimodal models; VideoAgentTrek shows unlabeled screen video as a usable training signal [S23] | Sufficient to parse app state and actions from recordings; no standard benchmark for IT-admin surfaces specifically | Falling with general inference (~10×/yr for fixed capability) [S30] | Feeds `record` | No published accuracy figures on RMM/AD/MDM consoles — every number here is from general-purpose benchmarks, not IT tooling |
| 2 | **Multi-step UI execution** | Qwen3.8 Max 86.1%; Claude Fable 5 / Mythos 5 at 85% on OSWorld-Verified (2026-09-02) [S14] | 12% (Apr 2024) → 85% (Jun 2026) [S15] | Falling | Feeds `execute` | **The headline is not the operating number.** The same analysis reports these agents still **fail ~80% of real workflows** [S15] |
| 3 | **Long-horizon task completion** | Best frontier system on OSWorld 2.0: **20.6%**, median task = 1.6 human-hours [S16] | Four-fifths of long tasks incomplete | Improving, rate unclear | Governs how much of a ticket runs unattended | **This is the binding constraint on the whole product.** Phase-4 autonomy is not supportable at 20.6%; the ladder must stop at governed execution for now |
| 4 | **Demonstration → reusable workflow** | ALLOY [S22] | Beat prompt-based agents and manual workflows on intent capture, cognitive load and generalization in a user study | n/a (research) | **The core mechanism** | Validated at user-study scale only. No published evidence of cross-*environment* transfer — which is assumption A8, the moat |
| 5 | **Procedure clustering / deduplication** | No named system or benchmark found | — | — | `cluster` step | **Unevidenced.** The riskiest assumption sits precisely where the literature is thinnest; this is the founder's to prove, not to cite |
| 6 | **Portable skill representation** | `SKILL.md` / Agent Skills, Apache 2.0, 26+ platforms [S24] | Progressive disclosure: discovery → activation → execution | Free, open | Where a clustered procedure lands | Solved, and genuinely new — it did not exist for FortressIQ in 2019. Also means no lock-in from the format itself |
| 7 | **Spoken-reasoning capture** | Commodity ASR | High accuracy, cents per hour | Falling | Captures the *why* a screen recording misses | Mature; not a differentiator, and the weakest-value part of the capture stack |
| 8 | **Agent identity & governed action** | Enterprise IdP support for non-human principals; approval-gate patterns | No benchmark; a compliance surface rather than a capability | — | Attribution, destructive-action gates | Table stakes for the security review that gates every MSP deal; not a moat |
| 9 | **Inference economics** | — | GPT-4-class $30/M (2023) → <$1/M (2026); ~10×/yr for fixed capability, median 50× per Epoch [S30] | Falling hard | Makes hours of recording tractable to process | Favourable, and it favours competitors equally |

## What the table actually says

**Three of nine links are new since 2023, and they are the right three.** Execution (2), demonstration-to-workflow (4) and a portable skill format (6) are what FortressIQ lacked in 2019 — it could record, and had nowhere to send the result but a human. The why-now is real and it is specific.

**But the loop is gated by row 3, not row 2.** The brief's four-phase ladder ends in autonomous resolution; long-horizon completion at 20.6% [S16] does not support that within a credible roadmap window. The pack should claim what rows 2–3 support — **discovery and governed, supervised execution with human escalation** — and treat full autonomy as a direction, not a deliverable. Claiming otherwise is the fastest way to fail the critic panel and, later, a technical diligence call.

**Row 5 is the company.** The clustering step — turning many messy recordings of the same procedure into one reliable, reusable skill — has no benchmark, no named system, and no published evidence. That is simultaneously the risk (nothing to cite) and the opportunity (nothing to copy). It is correctly identified in the brief as the assumption that kills the company if wrong.
