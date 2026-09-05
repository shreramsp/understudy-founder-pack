# Metrics by stage — and the vanity metrics to ignore at each

> **What this is** — the three to five metrics that matter at each stage, and — equally important — the ones that will look good and mean nothing at that stage.
> **Why it exists** — the vanity metrics for this company are unusually seductive, because a capture product generates impressive-looking volume numbers from day one that are entirely uncorrelated with whether it works.
> **How to read it** — read the Ignore column first. A skeptic should check that no metric in the left column can be improved without the product actually working.
> **Depends on / feeds** — inherits [stage_gate.md](stage_gate.md), [get_keep_grow.md](get_keep_grow.md); feeds `financials/revenue_build.md`, `startup-website` (the quantified proof block).

## Discovery — where we are

| Track | Why | **Ignore, and why** |
|---|---|---|
| Unprompted problem mentions (÷10 interviews) | The gate-1 criterion, and the only unbiased read on whether the pain is top-three | **Number of interviews conducted.** Twenty flattering conversations beat none, and mean less than six unprompted mentions |
| Onboarding hours quoted, by client size | Feeds `market_sizing` row 13 — the most load-bearing unknown | **Positive sentiment.** Everyone likes the idea; nobody's sentiment predicts a purchase |
| Ticket-category mix from real exports | Moves SAM ±40% (E8) | **Estimated ticket volume from memory.** Owners systematically misremember mix |
| Earlyvangelist criteria met, per prospect (of 5) | Predicts who will actually pilot | **Pipeline size.** A pipeline of interested parties failing criterion 4 is the most flattering and least predictive artifact a founder can build |

## Validation — after the gate

| Track | Why | **Ignore, and why** |
|---|---|---|
| **Cross-environment skill transfer rate** | The company, expressed as one number | **Sessions captured.** Grows automatically with headcount and tells you nothing |
| **Skills endorsed by their authoring engineer** | Predicts retention and detects Ray's silent veto before churn does | **Skills generated.** A library can grow while getting worse — over-merging produces more skills, not fewer |
| Engineer-hours per environment, vs that client's size band | The buyer's own number, honestly reported including overruns (D8) | **Aggregate hours saved.** Sums the environment-1 overrun into a positive figure and hides it |
| Verified-action accuracy, human-reviewed sample | Catches silent wrongness, which verification alone cannot | **Actions executed.** Volume without correctness is the 14:20 failure at scale |
| Security review cycle time | The throttle on expansion, and nothing else raises it | **Deals in security review.** A count that grows when reviews stall |

## Creation

| Track | Why | **Ignore, and why** |
|---|---|---|
| Environments per MSP per quarter | The expansion metric the revenue ramp depends on | **Logo count.** One MSP with 41 environments outweighs four with three |
| Reuse rate across environments | A8 made observable — the moat or its absence | **Library size.** See above |
| Net revenue retention post-backfill | Known to fall below 100%; the question is how far | **Gross revenue growth during backfill.** It is one-time revenue and reads like a trend |
| Reversal rate (X23) | The only detector for verified-but-wrong actions | **Resolution rate.** Uncorrected, it counts the 14:20 case as a success |

## Building

| Track | Why | **Ignore, and why** |
|---|---|---|
| Distinct MSPs contributing to the global layer | The m≥3 threshold is the cross-customer mechanism's precondition | **Envelope entries published.** Entries below threshold are not shared and count for nothing |
| Global-layer contribution to a new customer's first environment | M5's claim, measured | **Total environments covered.** Impressive, and not the mechanism |
| Time-to-first-verified-skill, published | The category yardstick, and the referral engine | **Internal benchmark scores.** A number nobody else can reproduce is marketing |

## The two metrics that would be dangerous at every stage

**1. Automation rate.** It rises when the envelope is widened carelessly and when gates are loosened — both of which make the product worse. It is the number the category advertises and the one most likely to be optimised against the customer's interest.

**2. Capture volume.** It grows with the customer's headcount, is uncorrelated with whether clustering works, and — because it looks like traction — is the metric most likely to be reported to investors during the period when nothing is actually being learned.

**Recommended next 3:** (1) instrument endorsement rate and reversal rate from the first pilot, since both detect failures no other metric sees; (2) never report aggregate hours saved without the environment-1 overrun beside it (D8); (3) publish time-to-first-verified-skill early — a metric nobody else reports becomes the category's yardstick by default, and a yardstick we defined and can meet is worth more than a benchmark we win.
