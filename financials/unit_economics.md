# Unit economics — per MSP, both node cases

> **What this is** — the per-unit P&L: CAC by channel with its basis, gross margin including inference at current prices, payback, LTV under stated retention, and the cost-curve argument.
> **Why it exists** — D6 moved the compute-heavy half of the system onto hardware we do not own. That either removes the dominant cost from our P&L or it does not, depending on a commercial term nobody has negotiated — and the margin conclusion is completely different in the two cases. `not_vaporware.md` promised this file would model both. It does.
> **How to read it** — §3 is the fork. A skeptic should attack the retention assumption in §4, which is known to be below 100% and is not yet measured.
> **Depends on / feeds** — inherits [pricing.md](pricing.md), [revenue_build.md](revenue_build.md), [../tech/not_vaporware.md](../tech/not_vaporware.md) §3b, [../strategy/channel_plan.md](../strategy/channel_plan.md); feeds [use_of_funds.md](use_of_funds.md), `narrative/vc_memo.md`.

**Conditional on E1, E3 and E8.** All figures are the banded schedule (D11); the superseded flat basis is a footnote in `revenue_build.md` §1, not a parallel column here.

## 1 · Revenue per MSP

| | Year 1 | Steady state |
|---|---|---|
| Ticket revenue (124 resolved/mo × $6 × 12) | ~$1,090 | ~$8,900 |
| Onboarding fees | ~$4,020 | ~$6,030 |
| **Total** | **~$5,110** | **~$14,930** |

## 2 · Marginal cost per MSP per month

| Line | Basis | Monthly |
|---|---|---|
| Action typing | **On-node** (D6) — no API cost | $0 |
| Clustering / alignment | Classical, CPU, on-node | $0 |
| Skill synthesis | ~20–40 skills/mo, frontier, on abstracted clusters — the only outbound call | `(assumption: $10–30)` |
| Execution | mostly deterministic; model only on re-grounding | `(assumption: $5–15)` |
| **Total marginal API** | | **`(assumption: $15–45)`** |

Against ~$1,244/month of revenue, **marginal API is 1–3% of revenue.** Falling inference prices [S30] make this line progressively irrelevant. **It is not the number that decides this business.**

## 3 · The node, and why the credit is being withdrawn

The reference node is 1×24GB GPU, 8 vCPU / 32GB, ~2TB `(assumption)` [../tech/not_vaporware.md](../tech/not_vaporware.md) §3b.

**D13 approved a hardware credit against onboarding fees. Modelled properly, it does not survive, and the recommendation is to drop it.**

**It is contra-revenue, not a cash-plan line.** A credit denominated as a reduction of the customer's own fees is consideration payable to a customer. The earlier version placed it "in the cash plan, not in gross margin" — it appeared in neither, and the payback table below was computed as though it did not exist.

**Netted correctly.** D9 waives environment 1, so year 1 has **four** chargeable environments at the ~$1,005 blend = **$4,020 of fee revenue**. A $2,000–4,000 credit consumes **50–100% of it**:

| Credit | Year-1 net revenue | 3-year revenue | Gross profit @76% | CAC ceiling |
|---|---|---|---|---|
| **$0** | $5,110 | $39,985 | $30,389 | **$10,130** |
| $2,000 | $3,110 | $37,985 | $28,869 | $9,623 |
| $3,000 (mid) | **$2,110** | $36,985 | $28,109 | **$9,370** |
| $4,000 | $1,110 | $35,985 | $27,349 | $9,116 |

**And it breaks payback**, which is the test that settles it:

| CAC | Credit | Cash out | Year-1 cash in | Payback |
|---|---|---|---|---|
| $6,500 (primary, mid) | $0 | $6,500 | $5,110 | **1.3 yrs** |
| $6,500 | $3,000 | $9,500 | $2,110 | **4.5 yrs** |
| $9,000 (primary, top) | $3,000 | $12,000 | $2,110 | **5.7 yrs** |

**Recommendation: drop the blanket credit.** A 4.5-year payback on a company whose retention is unmeasured, whose customer may stall at environment 2 — which is `strategy/gtm.md` §5's own falsification test — and which has $900k–1.2M of runway, is not a pricing instrument. It is vendor-financed capex with the risk on the wrong side.

**What replaces it, in order of preference:**

1. **A hosted node the vendor operates inside a tenant the MSP owns** — `(assumption: $150–250/month)` billed to the MSP as opex. Preserves the D6 boundary exactly, removes the procurement conversation, and costs us no capital. **This is the recommended default.**
2. **The MSP provides the node.** Best margin, loses deals at the small end.
3. **The credit, reserved for design partners only** — where it is an acquisition cost knowingly spent on evidence, not a term offered at scale.

**If the credit is used at all, it needs the three terms it did not have:** **title** remains with us until recovered; a **24-month term**; and **pro-rata clawback on churn**. Without them an owner takes a free GPU box and keeps it — and `risk_matrix.md` now carries that exposure as its own row, which it previously did not.

## 3b · Margin bridge — reconciling 96% marginal with the 70% the strategy assumes

The layer carried two unreconciled margins, and every channel verdict turns on which is operative. Neither was derived. Here is the bridge:

| Line | Annual, per MSP | Basis |
|---|---|---|
| Revenue | $14,930 | steady state, banded (D11) |
| Inference API | $360 | §2, ~$30/month |
| Onboarding delivery (human) | $990 | `(assumption: 2–4 hrs × 6 environments × $55)` |
| Support / customer success | $1,500 | `(assumption)` |
| Node fleet ops + on-call, amortised | $800 | `(assumption)` — D09's obligation, arriving at deployment one |
| **Total COGS** | **$3,650** | |
| **Fully loaded gross margin** | **~76%** | |

**96% was marginal-on-API-only; 76% is the operating number**, and it is the one the CAC ceiling should be derived from. The 70% the strategy layer assumed was close enough to be harmless, and is now replaced by a figure with its cost stack shown. **The human lines — onboarding delivery, support, node ops — are where channel products actually lose margin, and the earlier version costed the compute meticulously and omitted them entirely.**

## 4 · CAC, payback and LTV

| Channel | CAC | Basis | Payback vs year-1 revenue (no credit) |
|---|---|---|---|
| Peer communities *(primary)* | $4,000–9,000 | Entry cost + participation amortised + 15–25 hrs/close | **0.6–1.3 years [0.8–1.8]** |
| Buying groups | $500–2,000 + 10–20% referral | Best available | 0.1–0.4 years |
| Newsletters / podcasts | $4,000–8,000 | Placement cost ÷ 1–2 customers | 0.6–1.1 years [0.8–1.6] |
| Marketplace | $1,000–3,000 + 15–25% share | 18–24 months away | 0.2–0.6 years |
| Outbound / field | $15,000–40,000 | Excluded | **Never** |

**LTV.** 3-year gross profit **~$30,400** at 76% loaded margin, no credit. LTV:CAC at the primary channel:

| CAC | LTV:CAC | Read |
|---|---|---|
| $4,000 (bottom) | **7.6:1** | healthy |
| $6,500 (mid) | **4.7:1** | workable |
| **$9,000 (top)** | **3.4:1** | **at the floor the ceiling was defined by** |

**Stated plainly, because `channel_plan.md` says it and this file previously softened it to "healthy on paper":** a business whose best channel's top end sits at its 3:1 floor is fundable **only if CAC lands at the bottom of its range** — which makes **E4, the two-week channel-admissibility test, the round's real gate, not E1.**

**Retention, honestly.** NRR falls below 100% after backfill completes — a customer steps down from the year-4 peak to the steady-state run rate. **The 3-year window flatters this** by sitting entirely inside the backfill period. A 5-year LTV would be materially lower per year, and no churn figure exists because no customer does.

## 5 · The cost curve

Inference for fixed capability falls ~10×/yr [S30], so §2's marginal line trends toward zero and **§3's hardware fork is the durable cost question, not the API line.** Two consequences: the on-node constraint (D6) gets cheaper to honour every year as quantised models improve, which is a tailwind for the privacy architecture rather than a tax on it; and **margin improvement will come from the node, not from the model** — which means the commercial design in §3 is the lever, not vendor negotiation.

**Recommended next 3:** (1) price the hardware-credit hybrid explicitly and test it in E3's conversations — it is a pricing question disguised as an infrastructure one; (2) do not quote a single gross margin externally until the node question is settled; (3) model a 5-year LTV alongside the 3-year one before any raise, since the 3-year window sits entirely inside the flattering period.
