# Revenue build — $1M → $10M → $50M ARR, and what each jump requires

> **What this is** — the bottom-up path to scale: units × conversion × price per stage, the expansion layers, the milestone each jump depends on, and which GTM motion carries it.
> **Why it exists** — a revenue build is where a pack either inherits its own corrected numbers or quietly reverts to the flattering ones. **This file also carries a cascade the pricing work created: the banded schedule `pricing.md` recommends lowers the blended fee from $1,500 to ~$1,005, which moves SAM, the CAC ceiling and every channel verdict.** That is surfaced here, not absorbed.
> **How to read it** — §1 first: two scenarios, because the schedule is not yet decided. A skeptic should note that every row waits on E1.
> **Depends on / feeds** — inherits [pricing.md](pricing.md), [../strategy/market_sizing.md](../strategy/market_sizing.md), [../strategy/gtm.md](../strategy/gtm.md); feeds [unit_economics.md](unit_economics.md), [use_of_funds.md](use_of_funds.md), `narrative/pitch_deck.md`.

**Conditional on E1.** If cross-environment transfer lands below ~70%, M1 collapses, the onboarding fee loses its compression basis entirely, and every figure below is void. Nothing here is a forecast.

## 1 · The pricing cascade — two scenarios, undecided

`market_sizing.md` was built on a **flat $1,500** per-environment fee. [pricing.md](pricing.md) §4 shows that flat fee is priced *above* displaced value at the complex band and recommends banding down. The blended effect:

| | Flat $1,500 (current strategy basis) | **Banded per pricing.md §4 rec.** ($400 / $1,500 / $1,500) |
|---|---|---|
| Blended fee per environment | $1,500 | **~$1,005** (0.45×400 + 0.40×1,500 + 0.15×1,500) |
| Steady-state fee revenue/MSP/yr (6 new clients) | $9,000 | **~$6,030** |
| Ticket revenue/MSP/yr | $8,900 | $8,900 |
| **Steady-state revenue/MSP/yr** | **$17,900** | **~$14,930** |
| Year-1 revenue/MSP (5 envs, 1 waived) | ~$7,100 | **~$5,110** |
| 3-year revenue/MSP | ~$54,350 | **~$40,000** |
| 3-year gross profit @70% | ~$38,000 | **~$28,000** |
| **CAC ceiling at 3:1** | ~$12,700 | **~$9,300** |
| **SAM** (12,000 MSPs) | ~$215M | **~$179M** |

**The consequence that matters is not SAM.** It is the CAC ceiling: at ~$9,300, the primary channel's $4,000–9,000 range [../strategy/channel_plan.md](../strategy/channel_plan.md) **touches the ceiling at its top end**, and the newsletter channel at $4,000–8,000 does too. **Under the banded schedule there is no channel with a comfortable margin, and one that was viable becomes marginal.** This is a founder decision and it is escalated rather than chosen here.

**Both scenarios are carried below.** Figures are given flat-basis first, banded in brackets.

## 2 · The path

| Stage | ARR | MSPs | Environments live | What has to be true | Motion |
|---|---|---|---|---|---|
| **First revenue** | ~$7k [~$5k] | 1 | 5 | E1 ≥70%; E3 accepts the fee; one MSP admits us | Design partner converted |
| **$100k** | $100k | ~14 [~20] | ~70 [~100] | Channel admissibility confirmed (E4); the published time-to-first-verified-skill number exists | Peer/buying groups |
| **$1M** | $1M | ~56 [~67] at steady state | ~2,300 [~2,750] | Expansion works without a sales conversation; security review ≤6 weeks median (E7) | Groups + newsletters |
| **$10M** | $10M | ~560 [~670] | ~23,000 [~27,000] | **Marketplace listing live** — requires SOC 2, a shipping integration and references; 18–24 months minimum | RMM/PSA marketplace |
| **$50M** | $50M | ~2,800 [~3,350] | — | **Exceeds the MSP wedge.** 2,800 MSPs is ~23% of the serviceable band — a share no early-stage company should assume. Requires internal IT, which this pack does not claim | Undefined, honestly |

**The $50M row is where the pack stops claiming.** `market_sizing.md` puts SAM at $215M [$179M]; $50M ARR is 23–28% of the entire serviceable market. **A build that runs to $100M without naming a new market is arithmetic laundering**, and this one names the wall instead.

## 3 · Expansion layers, in order of confidence

| Layer | Mechanism | Confidence |
|---|---|---|
| **Environments per MSP** | Backfill the existing book, then ~6 new clients/yr | Highest — it is the model's core motion |
| **Ticket volume growth** | The MSP's own client growth | Medium — depends on the customer, and petal 2 says we help |
| **Band mix shift** | More complex clients as trust grows | Low, and small |
| **Global-layer premium** | Price rises as the envelope thickens | **Lowest — this is A8, and it is a year-two mechanism at best** [../tech/whitepaper.md](../tech/whitepaper.md) M5 |

## 4 · The revenue-quality problem, restated because it survives both scenarios

**~80% of three-year revenue per MSP is one-time backfill onboarding.** It bills once per existing client and never again. Two consequences:

- During land, this is **implementation-shaped revenue earning a services multiple**, not a SaaS one — the same revenue quality this pack criticises ServiceNow for [S20].
- **NRR falls below 100% once backfill completes**: from the year-4 peak to the steady-state run rate, a step down of roughly 45%. Growth past that point depends on the customer winning clients.

**The durable line is ~$17,900 [$14,930] per MSP per year, and that — not the peak — is what a valuation should rest on.**

**Recommended next 3:** (1) settle the banded schedule before this build is shown to anyone, since the two scenarios differ by ~$36M of SAM and by whether any channel has slack; (2) do not model past $10M without naming the market that carries it; (3) re-run this file the day E1 returns a number, because every row above is void if it comes back low.
