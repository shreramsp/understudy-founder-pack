# Risk matrix

> **What this is** — the top risks as a table: likelihood, impact, leading indicator, mitigation, and **residual** level after mitigation.
> **Why it exists** — a matrix where everything mitigates to "low" is fiction, and it is the most common failure of this artifact. Four rows below stay **high** after mitigation, and one has no mitigation at all.
> **How to read it** — the Residual column. A skeptic should check that no residual has been talked down by a mitigation that is itself unbuilt.
> **Depends on / feeds** — inherits [../validation/riskiest_assumptions.md](../validation/riskiest_assumptions.md), [../research/](../research/), [../tech/](../tech/); feeds `narrative/vc_memo.md` §6, `startup-audit`.

| # | Risk | Likelihood | Impact | Leading indicator | Mitigation | **Residual** |
|---|---|---|---|---|---|---|
| **1** | **Core mechanism fails** — skills do not transfer across environments | Medium | **Fatal** | E1 interim scores below 60% after two approaches | Harness before clusterer; 3 iterations; kill criterion declared; publish either way | **High.** No mitigation makes an unevidenced mechanism work. The mitigation buys an *honest, early* answer, not a better one |
| **2** | **Disuse** — engineers quietly stop cooperating with capture | Medium-high | **Severe, and invisible** | Pause rate >25%, narration <30% (E6); endorsement rate falling | Attribution, correction rights, rejection without justification; E6 instruments it | **High.** It is a social failure with no technical fix, and every other metric looks fine while it happens [S36] |
| **3** | **Market too small** at achievable pricing | Medium-high | Severe | E3 acceptance below 5/10; banded schedule forced down | Two-part tariff; wedge-to-expansion story | **High.** SAM is ~$179M after two successive fee corrections, and the justification has failed arithmetic twice. This is a ceiling, not a bug |
| **4** | **Channel closed** — vendor founder not admissible to peer/buying groups | Medium | Severe | E4 | Open sources first; marketplace as fallback | **Medium.** The fallback exists but is 18–24 months out and changes the raise |
| **5** | **Envelope re-identification succeeds** | Medium | Severe | E5/X25 | m≥3 MSPs, whitelist construction, schema versioning | **Medium-high.** The guarantee is heuristic — minimum support does not address compositional linkage, and no l-diversity, t-closeness or DP is implemented. **X25 is unbuilt** |
| **6** | **A confident wrong action at a client** (the 14:20 class) | **High — it will happen** | Moderate per incident, severe if mishandled | Reversal rate (X23) | Reversibility, agent identity, same-day disclosure (X24), destructive gating | **Medium.** Not eliminable, only survivable — and the pack says so rather than promising prevention |
| **7** | **Incumbent adds discovery** — Ravenna, Atomicwork, or Automation Anywhere on FortressIQ's footprint | Medium | Severe | A competitor shipping recording-based onboarding | Variance envelope; MSP-specific motion; 41 environments per customer | **Medium-high.** They can build it; the constraint is environment coverage, and a funded incumbent is ahead on raw count today |
| **8** | **API displacement** — vendors ship good APIs and the UI surface shrinks | **High, and continuous** | Moderate now, severe over 5 years | Share of target procedures with a usable API | Prefer APIs where they exist; concentrate on surfaces that lack them | **Medium-high.** This is structural erosion, not an event, and D10 requires it stated publicly |
| **9** | **Schedule** — 40-week floor, month 12 only at optimistic bounds | **High** | Moderate | Any Now-tier item exceeding its band | Reserve block; DD1 time-boxed | **High.** Solo founder, sequential critical path, no slack |
| **10** | **Node fleet operations** — version skew, silent node failure | Medium | Moderate | Stale-skill age, buffer depth | S13 fleet health, HALT-and-page, schema versioning | **Medium.** One node per MSP is tractable; the on-call obligation arrives with deployment one |
| **11** | **Key person** — solo founder | Medium | **Fatal** | — | **None.** No co-founder, no bus factor | **High.** Stated rather than mitigated |
| **12** | Regulatory — EU capture constraints | Low (US-first) | Moderate | EU expansion attempt | US-first (D3) | **Low.** Deferred, not solved [S29] |

## What the residual column says

**Four risks stay High and one has no mitigation at all.** That is the correct shape for a pre-build company with one unmeasured mechanism, a solo founder and a ceiling on its market — and a matrix that showed anything else would be describing a different company.

**Risk 2 deserves more attention than it will get.** It is the only severe risk whose realisation is *invisible in every dashboard*: capture volume keeps rising, the library keeps growing, and what degrades is the quality of what is captured. E6 exists solely to see it, and it runs for free inside E1.

**Risk 8 is the one that gets worse with time regardless of execution.** Every other risk is retired by evidence or by building; API displacement is a structural trend we can position against but not affect.

**Recommended next 3:** (1) build X25 before the first security review so risk 5's residual is measured rather than asserted; (2) instrument E6's three metrics from the first captured session, because risk 2 is otherwise undetectable; (3) do not present this matrix with anything talked down — the four High residuals are the reason the pre-seed is sized to fund a question rather than a company.
