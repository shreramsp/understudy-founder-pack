# Unit economics — per MSP, both node cases

> **What this is** — the per-unit P&L: CAC by channel with its basis, gross margin including inference at current prices, payback, LTV under stated retention, and the cost-curve argument.
> **Why it exists** — D6 moved the compute-heavy half of the system onto hardware we do not own. That either removes the dominant cost from our P&L or it does not, depending on a commercial term nobody has negotiated — and the margin conclusion is completely different in the two cases. `not_vaporware.md` promised this file would model both. It does.
> **How to read it** — §3 records why the hardware credit was withdrawn (D14) and §3b bridges the two margins that were previously unreconciled. A skeptic should attack the year-1 margin in §4, which is ~56% against a 76% steady state, and the retention assumption behind LTV.
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
| **$0** | $5,110 | $39,985 | $30,625 | **$10,208** |
| $2,000 | $3,110 | $37,985 | $28,869 | $9,623 |
| $3,000 (mid) | **$2,110** | $36,985 | $28,314 | **$9,438** |
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

**Built by driver, not as a steady-state stack applied to a ramp.** The earlier version applied one annual cost line across a three-year window in which no driver is at steady state — delivery scales with environments *onboarded* (30 over three years, not the 18 a flat line implies), support with environments *live* (5→15→30 against a steady-state 41, so a flat line overstates it), and inference with tickets. The errors ran opposite ways and did not cancel.

| Driver | 3-year cost | Scales with |
|---|---|---|
| Onboarding delivery | **$4,950** | 30 environments onboarded × ~3 hrs × $55 |
| Support / customer success | **$1,829** | environments live (5→15→30 against a 41 steady state) |
| Node fleet ops + on-call | **$2,400** | **fixed from deployment one** — not per-customer |
| Inference API | **$181** | tickets, ramping |
| **3-year COGS** | **$9,360** | |
| 3-year revenue | $39,985 | |
| **3-year gross profit** | **$30,625 (~77%)** | range **68–80%** on the assumption spread |
| **CAC ceiling at 3:1** | **~$10,200** | range **$9,100–10,700** |

**The range matters more than the point.** At the low end the primary channel's $9,000 top gives **3.0:1 — exactly the floor**, not comfortably inside it. D15's claim that the bridge "keeps the primary channel inside the floor" survives only in the favourable half of the range, and that is stated rather than rounded away.

**96% was marginal-on-API-only; 76% is the operating number**, and it is the one the CAC ceiling should be derived from. The 70% the strategy layer assumed was close enough to be harmless, and is now replaced by a figure with its cost stack shown. **The human lines — onboarding delivery, support, node ops — are where channel products actually lose margin, and the earlier version costed the compute meticulously and omitted them entirely.**

## 4 · CAC, payback and LTV

| Channel | CAC | Basis | **Payback vs year-1 gross profit** |
|---|---|---|---|
| Peer communities *(primary)* | $4,000–9,000 | Entry cost + participation amortised + 15–25 hrs/close | **1.4–3.1 years** on year-1 gross profit |
| Buying groups | $500–2,000 + 10–20% referral | Best available | 0.2–0.7 years |
| Newsletters / podcasts | $4,000–8,000 | Placement cost ÷ 1–2 customers | 1.4–2.8 years |
| Marketplace | $1,000–3,000 + 15–25% share | 18–24 months away | 0.2–0.6 years |
| Outbound / field | $15,000–40,000 | Excluded | **Never** |

**Year-1 margin is materially below steady state, and the earlier version computed payback against revenue rather than gross profit.** Two costs land in year 1 that the 6-environment steady-state bridge never sees: **node fleet ops (~$800) is fixed from deployment one**, and **onboarding delivery is incurred on all five environments including the one D9 waives** — which carries cost and zero revenue.

| Year-1 line | Amount |
|---|---|
| Revenue | ~$5,110 |
| Onboarding delivery, 5 environments incl. the waived one | ~$825 |
| Node ops (fixed from deployment one) | ~$800 |
| Support + inference | ~$620 |
| **Year-1 gross profit** | **~$2,865 (≈56% margin)** |

**So the honest primary-channel payback is ~2.3 years at the midpoint and ~3.1 at the top**, not the 0.8–1.8 the earlier table published. **That tightens this file's own conclusion rather than loosening it: E4 — whether the founder can enter the channel at all — is the round's real gate, because only a bottom-of-range CAC works.**

**LTV.** 3-year gross profit **~$30,400** at the 76% steady-state loaded margin, no credit. LTV:CAC at the primary channel:

| CAC | LTV:CAC | Read |
|---|---|---|
| $4,000 (bottom) | **7.6:1** | healthy |
| $6,500 (mid) | **4.7:1** | workable |
| **$9,000 (top)** | **3.4:1** | **at the floor the ceiling was defined by** |

**Stated plainly, because `channel_plan.md` says it and this file previously softened it to "healthy on paper":** a business whose best channel's top end sits at its 3:1 floor is fundable **only if CAC lands at the bottom of its range** — which makes **E4, the two-week channel-admissibility test, the round's real gate, not E1.**

**Retention.** The earlier version said "NRR falls below 100% after backfill completes" — **`revenue_build.md` §4 now establishes that was wrong.** NRR excludes one-time implementation revenue by every diligence definition; on the recurring line the ramp runs $1,090 → $8,900, so NRR is well above 100% throughout and the step-down is **backlog exhaustion, not churn**.

**What does qualify the LTV: ~73% of the 3-year gross profit this ratio rests on is one-time.** The durable subscription line is ~$8,900/yr, not $14,930 — see `revenue_build.md` §4's three-line split, which should never be re-summed into a single "recurring" figure. No churn figure exists because no customer does.

## 5 · The cost curve

Inference for fixed capability falls ~10×/yr [S30], so §2's marginal line trends toward zero and **§3's hardware fork is the durable cost question, not the API line.** Two consequences: the on-node constraint (D6) gets cheaper to honour every year as quantised models improve, which is a tailwind for the privacy architecture rather than a tax on it; and **margin improvement will come from operating leverage on the human lines — support, onboarding delivery, node ops — not from the model.** The node itself is now the customer's opex (D14), so it is a pricing question rather than a margin lever.

**Recommended next 3:** (1) settle whether the hosted node is bundled into the fee or passed through, and put the **all-in** number in both E3 arms — `pricing.md` §4b shows the buyer sees ~$6,900–8,100 in year 1, not $5,110; (2) quote the margin as the **68–80% range with its cost stack**, not a point — the top-end channel verdict flips inside it; (3) model a 5-year LTV alongside the 3-year one before any raise, since the 3-year window sits entirely inside the backfill period.
