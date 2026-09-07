# Unit economics — per MSP, both node cases

> **What this is** — the per-unit P&L: CAC by channel with its basis, gross margin including inference at current prices, payback, LTV under stated retention, and the cost-curve argument.
> **Why it exists** — D6 moved the compute-heavy half of the system onto hardware we do not own. That either removes the dominant cost from our P&L or it does not, depending on a commercial term nobody has negotiated — and the margin conclusion is completely different in the two cases. `not_vaporware.md` promised this file would model both. It does.
> **How to read it** — §3 is the fork. A skeptic should attack the retention assumption in §4, which is known to be below 100% and is not yet measured.
> **Depends on / feeds** — inherits [pricing.md](pricing.md), [revenue_build.md](revenue_build.md), [../tech/not_vaporware.md](../tech/not_vaporware.md) §3b, [../strategy/channel_plan.md](../strategy/channel_plan.md); feeds [use_of_funds.md](use_of_funds.md), `narrative/vc_memo.md`.

**Conditional on E1, E3 and E8.** Figures are flat-basis with the banded scenario in brackets, per `revenue_build.md` §1.

## 1 · Revenue per MSP

| | Year 1 | Steady state |
|---|---|---|
| Ticket revenue (124 resolved/mo × $6 × 12) | ~$1,090 | ~$8,900 |
| Onboarding fees | ~$6,000 [~$4,020] | ~$9,000 [~$6,030] |
| **Total** | **~$7,100 [~$5,110]** | **~$17,900 [~$14,930]** |

## 2 · Marginal cost per MSP per month

| Line | Basis | Monthly |
|---|---|---|
| Action typing | **On-node** (D6) — no API cost | $0 |
| Clustering / alignment | Classical, CPU, on-node | $0 |
| Skill synthesis | ~20–40 skills/mo, frontier, on abstracted clusters — the only outbound call | `(assumption: $10–30)` |
| Execution | mostly deterministic; model only on re-grounding | `(assumption: $5–15)` |
| **Total marginal API** | | **`(assumption: $15–45)`** |

Against ~$1,494/month [~$1,244] of revenue, **marginal API is 1–3% of revenue.** Falling inference prices [S30] make this line progressively irrelevant. **It is not the number that decides this business.**

## 3 · The fork — who owns the node

The reference node is 1×24GB GPU, 8 vCPU / 32GB, ~2TB `(assumption)` [../tech/not_vaporware.md](../tech/not_vaporware.md) §3b.

| | **Case A — MSP provides the node** | **Case B — we provide it** |
|---|---|---|
| Capital per customer | $0 to us | `(assumption: $2,000–4,000 hardware, or ~$150–250/mo hosted)` |
| Gross margin, steady state | **~96%** | **~76% [~72%]** — hosted, amortised |
| Effect on the sale | A procurement conversation before value is proven. **Loses deals at the small end**, where a GPU box is not a thing the MSP owns | Removes the objection; converts a capex conversation into our balance sheet |
| Effect on CAC | Raises it — more touches, longer cycle | Lowers it |
| Effect on payback | Unchanged | Year-1 revenue of $7,100 [$5,110] against $2,000–4,000 of capital means **payback slips past year 1 in the banded scenario** |

**Decided (D13) — a hybrid, and a real commercial design rather than a hedge.** Offer the node as a **hardware credit against onboarding fees** — the MSP owns it, we fund it out of revenue we would otherwise book. Case A's margin, Case B's sales motion, and the credit is self-liquidating across the first 3–4 environments.

**With D13 taken, the operative margin is Case A's (~96% marginal) with a working-capital line rather than a margin line**: the credit is `(assumption: $2,000–4,000 per customer)` recovered across the first 3–4 environments' onboarding fees. It appears in the cash plan, not in gross margin.

**The file still refuses to publish a single blended gross-margin number externally**, because the credit's recovery period is untested and a headline margin quoted before the first customer would be a forecast dressed as a fact.

## 4 · CAC, payback and LTV

| Channel | CAC | Basis | Payback vs year-1 revenue |
|---|---|---|---|
| Peer communities *(primary)* | $4,000–9,000 | Entry cost + participation amortised + 15–25 hrs/close | **0.6–1.3 years [0.8–1.8]** |
| Buying groups | $500–2,000 + 10–20% referral | Best available | 0.1–0.4 years |
| Newsletters / podcasts | $4,000–8,000 | Placement cost ÷ 1–2 customers | 0.6–1.1 years [0.8–1.6] |
| Marketplace | $1,000–3,000 + 15–25% share | 18–24 months away | 0.2–0.6 years |
| Outbound / field | $15,000–40,000 | Excluded | **Never** |

**LTV.** 3-year gross profit ~$38,000 [~$28,000]. **LTV:CAC at the primary channel's midpoint (~$6,500): 5.8:1 [4.3:1]** — healthy on paper, and resting on a retention assumption that is known to be wrong in a specific direction.

**Retention, honestly.** NRR falls below 100% after backfill completes — a customer steps down from the year-4 peak to the steady-state run rate. **The 3-year window flatters this** by sitting entirely inside the backfill period. A 5-year LTV would be materially lower per year, and no churn figure exists because no customer does.

## 5 · The cost curve

Inference for fixed capability falls ~10×/yr [S30], so §2's marginal line trends toward zero and **§3's hardware fork is the durable cost question, not the API line.** Two consequences: the on-node constraint (D6) gets cheaper to honour every year as quantised models improve, which is a tailwind for the privacy architecture rather than a tax on it; and **margin improvement will come from the node, not from the model** — which means the commercial design in §3 is the lever, not vendor negotiation.

**Recommended next 3:** (1) price the hardware-credit hybrid explicitly and test it in E3's conversations — it is a pricing question disguised as an infrastructure one; (2) do not quote a single gross margin externally until the node question is settled; (3) model a 5-year LTV alongside the 3-year one before any raise, since the 3-year window sits entirely inside the flattering period.
