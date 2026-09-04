# Business model canvas — Osterwalder nine blocks

> **What this is** — Blank's Customer Discovery Phase 1 artifact: all nine blocks, each carrying **one falsifiable hypothesis and the cheapest test that would kill it**.
> **Why it exists** — the Lean Canvas [lean_canvas.md](lean_canvas.md) is Maurya's variant and drops Key Partners, Key Activities and Customer Relationships — precisely the blocks Blank insists on testing, and precisely where a channel-dependent MSP business can quietly fail. Both are kept and cross-linked deliberately.
> **How to read it** — read the Test column, not the Hypothesis column; the hypotheses are ordinary, and the discipline is that each has a kill condition. A skeptic should check that no test costs more than the learning is worth.
> **Depends on / feeds** — cites [lean_canvas.md](lean_canvas.md), [market_sizing.md](market_sizing.md), [personas.md](personas.md); feeds `validation/experiment_board.md`, `validation/riskiest_assumptions.md`.

| Block | Content | Falsifiable hypothesis | Cheapest killing test |
|---|---|---|---|
| **Customer segments** | US MSPs, 10–100 employees, multi-client, no automation staff (~12,000 [S31]); expansion to internal IT | ≥6 of 10 MSP owners rank onboarding cost in their top 3 operational pains, unprompted | 10 discovery interviews, unprompted pain ranking. 1 week, ~$0 |
| **Value propositions** | Learns each client environment by watching engineers; onboarding cost falls per client and compounds | ≥5 of 10 can restate the value prop accurately after one reading, and name onboarding (not resolution) as the differentiator | Read the positioning statement cold to 10 owners; ask them to explain it back. 1 week |
| **Channels** | MSP peer communities → podcasts/newsletters → RMM/PSA marketplace [channel_plan.md](channel_plan.md) | A peer-community introduction converts to a booked call ≥20% of the time; cold outbound converts <5% | 30 warm intros vs. 100 cold emails, same offer, 3 weeks |
| **Customer relationships** | High-touch pilot → self-serve expansion to further client environments | An MSP that onboards environment #1 with us onboards #2 within 60 days without a sales conversation | Track first 5 pilots; expansion is the metric, not renewal |
| **Revenue streams** | Per resolved ticket (~$6) + per environment onboarded (two-part tariff, to test) | MSP buyers accept per-resolved-ticket billing despite billing their own clients per seat (A9) | Price conversation in the same 10 interviews; offer both tariffs and see which is chosen and why |
| **Key resources** | The compounding global skill library (A8); clustering quality; the evaluation harness | A skill synthesized in environment A executes correctly in environment B ≥70% of the time | **The BRIEF's decisive test** — 3 engineers × 5 procedures × 2 environments. Weeks, not months |
| **Key activities** | Clustering/dedup research; skill evaluation; security architecture for tenant isolation | Clustering quality is improvable by engineering rather than bounded by model capability | Ablation: same recordings, three clustering approaches, measured on the same held-out environment |
| **Key partners** | RMM/PSA vendors (distribution); IdP vendors (identity/attribution); MSP peer groups | At least one RMM/PSA vendor will list an AI service-desk integration without an exclusivity demand | Partner conversations with 3 vendors before building any integration |
| **Cost structure** | Inference (falling ~10×/yr [S30]); engineering; per-client security review | Gross margin at $6/ticket exceeds 70% including inference at current prices | Model the per-ticket inference cost against real recorded sessions — owed to `financials/unit_economics.md` |

## The three blocks the Lean Canvas would have hidden

- **Key partners.** This business plausibly reaches scale through RMM/PSA marketplaces rather than direct sales, which makes a partner the channel and therefore a dependency, not a nicety. Untested here, and it is the block most likely to change the GTM shape.
- **Key activities.** Naming *clustering quality* as the key activity — rather than "building the product" — is what keeps engineering pointed at the riskiest assumption instead of at surface area.
- **Customer relationships.** The land-and-expand motion is per *environment*, not per seat. That is unusual, it is the reason the two-part tariff is worth testing, and it does not appear anywhere on a Lean Canvas.

**Recommended next 3 moves:** (1) run the 10 discovery interviews once — four blocks are tested by the same conversation; (2) run the key-resources test before any GTM spend, since a negative result reshapes the company; (3) open partner conversations early, because channel economics take months to learn and cannot be compressed later.
