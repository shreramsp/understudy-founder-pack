# Get / Keep / Grow

> **What this is** — the funnel per segment: how a customer is acquired, what keeps them, and what makes them expand, with the metric and the lever at each stage.
> **Why it exists** — this business's growth mechanism is unusual and easy to get wrong: expansion is per *environment*, and its throttle is a security review rather than a sales conversation. A conventional funnel would optimise the wrong stage.
> **How to read it** — the Keep and Grow stages matter more here than Get, because the land is small and the expansion is where the revenue is. A skeptic should attack the Grow lever, which depends on an unproven assumption (A8).
> **Depends on / feeds** — inherits [../strategy/gtm.md](../strategy/gtm.md), [../strategy/channel_plan.md](../strategy/channel_plan.md), [decision_making_unit.md](decision_making_unit.md); feeds [metrics_by_stage.md](metrics_by_stage.md), `financials/revenue_build.md`.

## GET

| Stage | Mechanism | Metric | Current / target | Lever |
|---|---|---|---|---|
| Reach | Open sources first (r/msp, MSP Slack/Discord, LinkedIn owner outreach, podcast audiences); peer and buying groups **once admissible** (E4) | Conversations booked/month | 0 / 8 | The hours ROI calculator as the opener, not a demo |
| Qualify | Five earlyvangelist criteria [mvp_definition.md](mvp_definition.md) | % of prospects meeting all five | — / ≥30% | Criterion 4 (has a real workaround) is the discriminator |
| Convert | Design-partner pilot → paid | Pilot → paid conversion | — / ≥50% | The published time-to-first-verified-skill number |

**Activation moment: the first verified skill in the customer's own environment.** Not signup, not capture starting — the first time Dana sees a procedure the system learned from her own team and she agrees it is right.

## KEEP

| Stage | Mechanism | Metric | Target | Lever |
|---|---|---|---|---|
| Habit | Friday deviation review | Weekly active reviewers | ≥1 per MSP | Keep it to ~40 min/month; a queue that manufactures urgency gets muted |
| Trust | Skills endorsed by their authoring engineer | Endorsement rate | ≥70% | Attribution and rejection-without-justification (`P8`) |
| Value proof | Onboarding meter | Environments where hours beat the client's size band | ≥60% from environment 2 | Honest reporting of the environment-1 overrun (D8) |

**The retention-predicting metric is endorsement rate, not usage.** A library nobody has endorsed is one the engineers do not trust, and that state precedes churn without showing up in logins. It is also the earliest visible signal of Ray's silent veto.

## GROW

| Stage | Mechanism | Metric | Target | Lever |
|---|---|---|---|---|
| Expand | Additional client environments onboarded | Environments per MSP per quarter | ≥2 | **Security review throughput, not sales** |
| Compound | Skill reuse across environments | Cross-environment reuse rate | measurable from environment 2 | This is A8 made observable |
| Refer | Owner-to-owner in peer groups | Referrals per customer per year | ≥0.5 | The published number, not a case study |

**The growth loop, and where it can break:**

```
   environment onboarded → variance envelope thickens → next environment onboards faster
            ↓                                                      ↓
   security review passed                            a number worth repeating in a peer group
            ↓                                                      ↓
   throughput permits the next one  ←──────────────  next MSP
```

**Two honest weaknesses in this loop.** It depends on A8 — if procedures do not transfer, "onboards faster" is false and the loop degrades to ordinary word of mouth. And its throttle is the security review, which no amount of sales effort accelerates. **The lever that actually raises expansion velocity is architectural** — shortening the review by making the boundary easier to reason about — which is why D6 was worth treating as a constraint rather than a preference.

**Net revenue retention is below 100% after backfill completes** [../strategy/market_sizing.md](../strategy/market_sizing.md): an MSP that has onboarded all 41 environments drops from the backfill run-rate to ~$14,930/yr (D11). **Growth after that point depends on the customer's own client growth**, which is coherent — petal 2 says we help them win clients — but it must be said rather than assumed.

**Recommended next 3:** (1) instrument endorsement rate from the first pilot, since it predicts churn earlier than any usage metric; (2) measure review cycle time as a first-class funnel stage, because it caps Grow and nothing else does; (3) do not build referral mechanics until the published number exists — the referral is the number, not a programme.
