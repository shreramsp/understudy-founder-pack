# Working-backwards press release — dated March 2032

> **What this is** — the Amazon-style press release written as if the company had succeeded, dated roughly six years out, plus the timeline that would have to have happened.
> **Why it exists** — it forces the vision to be specific enough to be wrong. A vision that cannot be falsified in retrospect is decoration; this one names the metric, the year, and the things that did *not* happen.
> **How to read it** — read the "what did not happen" section against the rest of the pack. A skeptic should check that nothing here contradicts the claim boundary (D1) or the honest limits in `tech/whitepaper.md` §4.
> **Depends on / feeds** — arranges [mission_vision.md](mission_vision.md), [../strategy/market_sizing.md](../strategy/market_sizing.md), [../tech/whitepaper.md](../tech/whitepaper.md); feeds `startup-website`.

---

**FOR IMMEDIATE RELEASE — 14 March 2032**

## Understudy passes 100,000 client environments onboarded by observation, and publishes six years of transfer data

**Chicago —** Understudy today announced that its skill libraries now cover more than 100,000 managed client environments across 2,400 MSPs, and released the full six-year record of its cross-environment transfer measurements — including the two years the numbers were bad.

**Time-to-first-verified-skill** — the metric Understudy proposed in 2026 when no benchmark for autonomous IT resolution existed — is now reported by four vendors in the category and cited in MSP procurement templates. The company's own median is **9 engineer-hours per environment** — against the 18–28 it projected for environment 2 in 2026, and the 25–40 that onboarding a median client cost before any of this existed. **Time-to-first-verified-skill**, the metric the industry actually adopted, runs at a median of **3 days**, against 8 in the first pilot. *(The two are different metrics in different units, and the 2026 pack was careful about that; an earlier draft of this release conflated them.)*

"The number that changed our business wasn't the resolution rate," said **Marcus Whelan**, who runs a 34-person MSP in Ohio and was Understudy's fourth paying customer. "It was that client forty-one onboarded faster than client twelve. I stopped hiring ahead of growth. I take clients now that I'd have turned down in 2027, and I turned down two that year."

For engineers, the change was less about volume than about what stopped being asked of them. "I spent nineteen years being the person who remembered how each client's directory was wired," said **Ray Kowalczyk**, a principal engineer at the same firm. "The part I actually resented was being interrupted for things I'd explained before. That mostly stopped. What reaches me now is genuinely new, which is the job I wanted."

**The threshold bound, which is the point of having one.** In 2027 the first result came in below it, and the company did what it said it would: narrowed the claim, repriced, and did not reinstate the stronger version until a second measurement in fresh environments. **A threshold that is missed and then method-shopped to a pass in two quarters is not a threshold**, and the earlier draft of this release showed exactly that — which would have told any reader that the pre-commitment in the 2026 deck was decoration.

**What we got wrong that we did not predict.** The 2026 materials named a long list of limits and every one of them held — which, read back, is its own kind of warning: a forecast whose only errors were pre-announced is an advertisement for the pre-announcement. **The thing we did not see coming was the node.** Putting distillation inside each MSP's tenant was the right call for the privacy guarantee and it cost roughly eighteen months of operational drag nobody modelled: version skew across customer-controlled infrastructure, patch windows we did not control, and an on-call obligation that landed on one person from the first deployment. Two design partners left in 2028 over node reliability, not over the product. The 2026 pack rated that risk "medium" and it was the second-most expensive thing about the decade.

**What did not happen, and the company says so.** Understudy does not run unattended. Every mutating action is still gated or supervised, six years and 100,000 environments later — the same claim boundary the company published in its first investor materials in 2026, when long-horizon agent completion was 20.6%. It has improved considerably since; it has not improved enough to change the position.

The company also confirmed that a **material share of the ticket volume it once expected to address is now handled through vendor APIs rather than by observing a UI** `(no figure is given: the 2026 pack had no basis for one, and inventing a precise number for a press release is exactly what its own quality bar forbids)` — a limit it named publicly in 2026 and has watched grow. "We said at the start that where a real API exists, we're the wrong tool," a spokesperson said. "That surface has shrunk every year, exactly as we predicted, and it's why we build for the places APIs don't reach."

---

## How we got here

| | |
|---|---|
| **2026** | Pre-seed. One question: do skills synthesized in one environment execute correctly in another? The falsifying threshold — 70% on a held-out set — is declared before the harness is built. |
| **2027 Q1** | First transfer result: **64%.** Below the 70% threshold. Published anyway — and **the pre-declared rule fired rather than being overridden**: P2 required the claim to narrow to *assisted* onboarding rather than automated, and the fee to be repriced against the runbook rather than the hours. Both happened, and both cost revenue. |
| **2027 Q2–Q4** | Three quarters on the narrowed claim, at the lower price. Partial-order alignment eventually reaches 78%, but **the automated claim is not reinstated until Q1 2028**, on a second measurement in six fresh environments. The recovery cost a year. |
| **2027 Q4** | First paid MSP. Environment 1 costs more than baseline, as promised. Environment 2 is where the customer sees it. |
| **2028** | Third MSP customer clears the m≥3 threshold; the global layer starts contributing for the first time. Cold start took two years, which is what the corrected threshold implied it would. |
| **2029** | An agent action at a client is reverted by a human and disclosed the same day. The incident-disclosure practice — built in 2026 before there was anything to disclose — is the reason the account is retained. |
| **2030** | RMM/PSA marketplace listing, four years after the first partner conversation. SOC 2 Type II two years earlier. |
| **2031** | First MSP-side co-founder hire becomes COO. The gap named in the 2026 founder story closes six years after it was named. |
| **2032** | 100,000 environments. Transfer data published in full, including 2027. |

---

## What this vision is deliberately not

- **Not autonomy.** Six years on, still supervised. If that changes it will be because the evidence changed, not because the marketing did.
- **Not a category-defining exit, and not an adjacent market either.** The 2026 pack put SAM at ~$179M for the MSP wedge. **This release stays inside that wedge** — 100,000 environments across 2,400 MSPs is ~41.7 environments each, exactly the model's own figure, and ~20% of the serviceable band. An earlier draft claimed the company had grown into an adjacent market; nothing in the release depicts one, and the claim is withdrawn rather than illustrated.
- **Not a story where the founder was right about everything.** The first transfer result was below threshold. The clustering method had to change. The privacy threshold had to be recounted. Those are in the timeline because a vision that omits them is not a forecast, it is an advertisement.
