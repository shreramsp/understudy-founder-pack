# Revenue build — $1M → $10M → $50M ARR, and what each jump requires

> **What this is** — the bottom-up path to scale: units × conversion × price per stage, the expansion layers, the milestone each jump depends on, and which GTM motion carries it.
> **Why it exists** — a revenue build is where a pack either inherits its own corrected numbers or quietly reverts to the flattering ones. **This file also carries a cascade the pricing work created: the banded schedule `pricing.md` recommends lowers the blended fee from $1,500 to ~$1,005, which moves SAM, the CAC ceiling and every channel verdict.** That is surfaced here, not absorbed.
> **How to read it** — §1 first: two scenarios, because the schedule is not yet decided. A skeptic should note that every row waits on E1.
> **Depends on / feeds** — inherits [pricing.md](pricing.md), [../strategy/market_sizing.md](../strategy/market_sizing.md), [../strategy/gtm.md](../strategy/gtm.md); feeds [unit_economics.md](unit_economics.md), [use_of_funds.md](use_of_funds.md), `narrative/pitch_deck.md`.

**Conditional on E1.** If cross-environment transfer lands below ~70%, M1 collapses, the onboarding fee loses its compression basis entirely, and every figure below is void. Nothing here is a forecast.

## 1 · The pricing cascade — decided (D11), and what it moved

The banded schedule is **decided**, not undecided. The earlier version of this section carried two live columns and an escalation sentence after D11 had already settled it, and the superseded flat figures then leaked into `unit_economics.md`'s headline row — where an investor skimming the top line read $7,100 and $17,900, the two numbers D11 retired. **Banded is now the sole primary basis across this layer; flat survives only as the footnote below.**

| Operative figure | Value |
|---|---|
| Blended fee per environment (45/40/15 at $400/$1,500/$1,500) | **~$1,005** |
| Year-1 revenue per MSP (5 environments, first waived per D9) | **~$5,110** |
| Steady-state revenue per MSP | **~$14,930** |
| 3-year revenue per MSP | **~$40,000** |
| Fully loaded gross margin (bridged in `unit_economics.md` §3b) | **~76%** |
| 3-year gross profit | **~$30,400** |
| **CAC ceiling at 3:1** | **~$10,100** |
| SAM (12,000 MSPs) | **~$179M** |

*Footnote — what the flat $1,500 schedule gave, for anyone reconciling against an earlier draft: $17,900 steady state, $7,100 year 1, $54,350 over three years, a $12,700 ceiling and a $215M SAM. D11 banded the complex tier down and the cascade moved every one of them.*

**A correction that arrived after D11 and does not change these figures but does change their standing:** `pricing.md` §4 now computes hours displaced by one consistent method across all three bands, and under it **the fee is priced above displaced value at every band** — with *typical* the worst offender, not complex. D11's arithmetic propagated correctly; its rationale was an artifact of an inconsistency. **The schedule stands pending E3 on the founder's instruction, and E3 is now a test of whether the fee has any hours basis at all.**

## 2 · The path

| Stage | ARR | MSPs | Environments live | What has to be true | Motion |
|---|---|---|---|---|---|
| **First revenue** | ~$7k [~$5k] | 1 | 5 | E1 ≥70%; E3 accepts the fee; one MSP admits us | Design partner converted |
| **$100k** | $100k | ~14 [~20] | ~70 [~100] | Channel admissibility confirmed (E4); the published time-to-first-verified-skill number exists | Peer/buying groups |
| **$1M** | $1M | ~56 [~67] at steady state | ~2,300 [~2,750] | Expansion works without a sales conversation; security review ≤6 weeks median (E7) | Groups + newsletters |
| **$10M** | $10M | ~560 [~670] | ~23,000 [~27,000] | **Marketplace listing live** — requires SOC 2, a shipping integration and references; 18–24 months minimum | RMM/PSA marketplace |
| **$50M** | $50M | ~2,800 [~3,350] | — | **Exceeds the MSP wedge.** 2,800 MSPs is ~23% of the serviceable band — a share no early-stage company should assume. Requires internal IT, which this pack does not claim | Undefined, honestly |

**The $50M row is where the pack stops claiming.** `market_sizing.md` puts SAM at ~$179M; $50M ARR is 23–28% of the entire serviceable market. **A build that runs to $100M without naming a new market is arithmetic laundering**, and this one names the wall instead.

## 3 · Expansion layers, in order of confidence

| Layer | Mechanism | Confidence |
|---|---|---|
| **Environments per MSP** | Backfill the existing book, then ~6 new clients/yr | Highest — it is the model's core motion |
| **Ticket volume growth** | The MSP's own client growth | Medium — depends on the customer, and petal 2 says we help |
| **Band mix shift** | More complex clients as trust grows | Low, and small |
| **Global-layer premium** | Price rises as the envelope thickens | **Lowest — this is A8, and it is a year-two mechanism at best** [../tech/whitepaper.md](../tech/whitepaper.md) M5 |

## 4 · The revenue-quality problem, restated because it survives both scenarios

**~73% of three-year revenue per MSP is one-time backfill onboarding.** It bills once per existing client and never again.

**The earlier version called this an NRR decline, and that was wrong.** Every diligence definition of net revenue retention excludes one-time implementation revenue from both numerator and denominator. On the recurring line alone the ramp runs **$1,090 → $8,900**, so NRR is well above 100% throughout — **the "45% step down" is the exhaustion of a one-time backfill balance, not churn.** A reader taking the old sentence literally would conclude the subscription contracts, which this pack's own ramp says it does not.

**Reported correctly, there are three lines and they should never be summed into one "recurring" figure:**

| Line | Annual, steady state | Character |
|---|---|---|
| **Ticket revenue** | **~$8,900** | genuinely recurring — the subscription line a valuation should rest on |
| Turnover-driven onboarding fees | ~$6,030 | recurs only as a function of **the customer's own client churn**, not ours. Not recurring by any standard definition |
| Backfill onboarding | declining to zero by ~year 4 | a one-time implementation backlog, and it should be carried as one |

**So the durable subscription line is ~$8,900 per MSP per year — roughly 60% of the ~$14,930 figure the rest of this pack quotes**, and `comps_exits.md` values on the smaller number with the turnover line argued separately. During the land phase this is implementation-shaped revenue earning a services multiple, the same quality this pack criticises ServiceNow for [S20]; the difference is that ours decays by design.

**Recommended next 3:** (1) run E3 before this build is shown to anyone — the fee is priced above displaced value at every band and E3 is the only thing that establishes whether it has a basis; (2) do not model past $10M without naming the market that carries it; (3) re-run this file the day E1 returns a number, because every row above is void if it comes back low.
