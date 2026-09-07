# Comparables and exit landscape

> **What this is** — sourced comparable companies and transactions, what the market rewarded and punished in each, realistic acquirer profiles with the reason each would pay, IPO-path conditions, and a closing assessment of whether this can be a standalone generational company.
> **Why it exists** — the exit section is where a pack usually stops being honest, because the closing paragraph is expected to be bullish. This one runs the sober comps first and then answers the question the arithmetic actually supports, which is not the answer a founder would prefer.
> **How to read it** — §4 is the honest assessment. A skeptic should note that no revenue multiple appears in this file, because none was findable.
> **Depends on / feeds** — inherits [../research/sources.md](../research/sources.md), [revenue_build.md](revenue_build.md), [../strategy/market_sizing.md](../strategy/market_sizing.md); feeds `narrative/vc_memo.md`, `narrative/pitch_deck.md`.

## 1 · Transactions and rounds in this space

| Company | Event | Amount | What the market rewarded / punished |
|---|---|---|---|
| **Moveworks** | Acquired by ServiceNow, announced Mar 2025, closed Dec 2025 [S26] | **$2.85B** — ServiceNow's largest acquisition | **Rewarded:** enterprise distribution at scale (~5M employee users, ~250 mutual customers) and a front-end the incumbent lacked. The category's defining proof that AI service desks are strategically valuable |
| **FortressIQ** | Acquired by Automation Anywhere, Dec 2021 [S5][S6] | Undisclosed | **Punished:** discovery without an executor. Claimed ~90% reduction in discovery time [S7] and still ended as a feature inside an RPA vendor, no longer independently visible. **The closest historical analogue to this company, and its cautionary case** |
| **Aisera** | Raised $164.5M total [S13] | — | Rewarded: enterprise ESM breadth |
| **Espressive** | Raised $53M total [S13] | — | — |
| **Atomicwork** | Series A $25M, Jan 2025; $40.3M total [S12] | — | Rewarded: the anti-ServiceNow mid-market thesis, Khosla-backed |
| **Ravenna** | Pre-seed + seed $15M, Apr 2025 [S2][S3] | — | Rewarded: Slack-native agentic ITSM, the same mid-market gap read |
| **Strawberry** | $6M, Oct 2025 [S25] | — | Rewarded: agentic execution that learns from the user — browser-only |
| **ServiceNow** | Public | ~$160B [S3] | The incumbent whose implementation revenue is 3–5× licence [S20] |

**Marked gap: no revenue multiples are stated in this file because none was findable.** Moveworks' $2.85B was disclosed without revenue; the private rounds disclose no ARR. **A pack that invented a multiple here would be fabricating the single number an investor most wants**, and `research/sources.md` records the absence rather than filling it.

## 2 · Realistic acquirer profiles

| Acquirer | Why they would pay | Why they might not |
|---|---|---|
| **ConnectWise / Kaseya / N-able** — MSP platform vendors | **The most natural fit by some distance: our buyer is already their buyer.** They own the PSA/RMM surface an MSP runs its day in, they have the distribution the channel plan says takes 18–24 months to reach, and self-onboarding is a capability they cannot build without a capture footprint | Consolidators buy on revenue multiples, not capability. At $179–215M SAM they would price this as a feature acquisition |
| **Automation Anywhere** | Already owns FortressIQ's capture footprint [S5] and the discovery-plus-execution thesis. We are the executor their discovery never had | They could build it. They have the input and the customers; what they lack is the MSP motion, which is a new market rather than an extension |
| **ServiceNow** | Bought Moveworks for $2.85B; buys rather than builds in this category | **Structurally inhibited** — implementation at 3–5× licence [S20] means self-onboarding cannibalises the larger half of its own deal. And its lead investor calls the platform inappropriate below enterprise [S3] |
| **UiPath** | Owns discovery, and its executor is the one whose failure record stalled the category | Its buyer is the enterprise process team, not IT service delivery |
| **Ravenna / Atomicwork** | Adding recording-based discovery is a product decision for them, not a business-model conflict | At their stage they build rather than buy |

**The strategic read:** the MSP platform vendors are the natural home and the likeliest outcome. That is a **good** trade-sale profile and a **poor** independence profile — the same distribution advantage that makes them a buyer is the one we would need decades to build.

## 3 · IPO-path conditions

An IPO requires roughly $100M+ ARR with durable growth. Against `revenue_build.md`: $50M ARR already needs ~23–28% of the entire serviceable MSP band, and $100M exceeds the band outright. **The IPO path therefore does not exist on the wedge.** It requires the internal-IT expansion — a market this pack explicitly declines to claim, on an axis (resolution quality) it has chosen not to compete on, against competitors funded at $164.5M and an incumbent that paid $2.85B for the category.

**Stating the condition plainly:** an IPO story for this company is a story about winning internal IT, and nothing in this pack argues that we can.

## 4 · Can this be a standalone generational company?

**On the MSP wedge alone: no, and the arithmetic says so rather than the mood.**

SAM is ~$179M (D11; $215M under the superseded flat fee). A generational outcome requires either capturing a share of it no early-stage company should assume, or entering a market this pack has declined to claim. **The honest ceiling on the wedge is an excellent business — durable recurring revenue at ~$15k per MSP, a defensible mechanism, and a natural acquirer set — and not a generational one.**

**What would change that answer**, in descending order of credibility:

1. **Price capture.** $6 captures roughly a quarter of the $22.50 blended cost per ticket, and agent labour is 70–80% of it [S27][S28]. Capturing half the labour value rather than a quarter roughly doubles SAM without a new market. **This is the most credible path and it is a pricing question, not a product one.**
2. **The variance envelope becoming an asset others pay for.** If procedure-variance data across thousands of environments is valuable to platform vendors or to the vendors whose products are being administered, that is a second business — speculative, and it depends entirely on A8.
3. **Internal IT.** Real, large, and a fight on the wrong axis. Available if the MSP-proven library gives a genuine cold-start advantage, which is M5, which is a year-two mechanism at best.

**The honest close, and it is the one this pack has earned:** this is a company whose realistic good outcome is a strong trade sale to an MSP platform vendor within five to seven years, whose upside case runs through pricing rather than through market expansion, and whose downside is a clean, publishable negative on a forty-year-old assumption. **A memo claiming a generational outcome from a $200M SAM would be the strongest evidence against everything else in this pack.**

**Recommended next 3:** (1) test price capture in E3 — ask what they would pay per *resolved ticket* against their own $22.50 blended cost, not just for onboarding; (2) open a relationship with one MSP platform vendor early, as an intelligence channel rather than a partnership; (3) do not present an IPO path in any investor material, since the arithmetic above makes it checkable in one division.
