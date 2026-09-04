# Market type

> **What this is** — Steve Blank's market-type declaration for Understudy: existing, re-segmented, new, or clone — chosen once, with evidence, because every other strategic decision inherits it.
> **Why it exists** — market type determines sales cycle, capital needs, positioning approach and the dominant risk, and teams that skip it default to *existing-market* behaviour (feature comparison, competitive displacement) in markets that do not reward it. Choosing wrong here misallocates the entire seed round.
> **How to read it** — the declaration is one line; the evidence and the consequences table are the argument. A skeptic should attack whether this is genuinely re-segmentation rather than a feature of the existing AI-ITSM market.
> **Depends on / feeds** — cites [research/competitors.md](../research/competitors.md), [research/landscape.md](../research/landscape.md); feeds [positioning.md](positioning.md), [gtm.md](gtm.md), [market_sizing.md](market_sizing.md), `validation/stage_gate.md`.

## Declaration

**Hybrid: re-segmented by buyer, new-market by budget.**

Re-segmentation of IT service management by buyer (MSPs) and by capability (self-onboarding) — but the budget it is paid from does not exist as a line item, which is Blank's diagnostic for a **new market**. Both halves are true and the pack must carry both consequences rather than picking the more comfortable one. [petal_diagram.md](petal_diagram.md) shows why: the primary budget is unbilled engineer time, not a software spend, so the first sale *creates* a budget code rather than switching one.

## Evidence

**It is not a new market.** MSPs already buy service-desk software, already run ticket queues, and already have a budget line for it. Nobody has to be convinced that AI ticket resolution is a category: Moveworks sold for $2.85B [S26], Aisera has raised $164.5M [S13], and ServiceNow is a ~$160B company [S3]. Demand exists and is funded.

**It is not a straight existing-market play either.** Winning an existing market means beating incumbents on the axis they already compete on — resolution quality — against companies with $164.5M and a $2.85B exit behind them. That is a losing fight for a pre-seed company, and it is not where the evidence says the pain is.

**The re-segmentation is on two axes at once:**

1. **By buyer.** The AI-ITSM field is aimed at internal IT: Ravenna and Atomicwork both pitch mid-market internal teams [S2][S12], and ServiceNow's own lead investor says the platform is "completely inappropriate" below enterprise [S3]. **MSPs are structurally different customers** — they onboard a new environment every few weeks rather than once, so deployment cost is recurring cost of goods rather than a one-time project. No AI-ITSM vendor is running an MSP-specific motion.
2. **By capability.** Every competitor acquires environment knowledge by human configuration. Understudy acquires it by observation [research/competitors.md]. That is a different product category — discovery — grafted onto the service-desk category.

**Corroborating signal that the segment feels the pain:** 26% of MSPs report lacking enough staff to service more clients and 22% cannot find skilled technicians [S33]. The constraint on MSP growth is engineer-hours, which is exactly what onboarding consumes at 40–80 hours per client [S21].

## Strategic consequences of re-segmentation

| Dimension | Consequence for Understudy |
|---|---|
| **Positioning approach** | Must make the *segment* the story, not the feature. "The service desk for MSPs that learns each client environment" beats "better AI resolution". The buyer must recognise themselves in the first sentence |
| **Sales cycle** | Shorter than enterprise ITSM (owner-operator buyers, 70% of US MSPs have <50 employees [S31]) but requires proving a new claim rather than a better number — expect 30–90 days with a pilot, not a 6–12 month enterprise cycle [S20] |
| **Capital needs** | Moderate. Re-segmentation does not require market creation spend, but does require enough runway to prove the discovery claim before competing on resolution. The evidence burden, not the demand generation, is the cost centre |
| **Dominant risk** | **Market risk, in two forms.** (a) *Re-segmentation risk:* buyers reject the new segment boundary and default to comparing us with the category leader on the category's existing axis — resolution rate — where we lose. (b) *New-market risk:* the sale has to create a budget line that does not exist, which is slower and costlier than a switch. **Technical risk (clustering, A8) is real but lives in `validation/riskiest_assumptions.md`, not in this cell** — the first version wrote execution risk here and thereby hid the market risk this declaration exists to surface |
| **What the new-market half costs** | Buyer education on a cost they do not currently measure. The engineer-hours ROI calculator is not a marketing nicety — it is the instrument that turns an unmeasured leak into a number, and without it there is no budget to move |
| **Competitive response** | Incumbents can add discovery as a feature. ServiceNow is structurally inhibited (implementation is 3–5× licence revenue [S20]); Ravenna and Atomicwork are not. Speed to a defensible skill library matters more than speed to first customer |
| **Metric that matters** | Time-to-first-autonomously-resolved-ticket in a *new* environment. It is the segment's own pain expressed as a number, and no competitor publishes it |

## The decision

**Play re-segmentation, not displacement.** Understudy does not enter conversations by comparing resolution rates with Ravenna. It enters by asking an MSP owner what onboarding a new client costs them in engineer-hours — a question no incumbent's positioning invites — and answers it with discovery. Resolution quality must be *sufficient*, not superior; onboarding cost must be *transformed*.

**Recommended next 3 moves:** (1) validate the *positioning*, not only the pain — ask five owners to place us against Ravenna unprompted; if they compare on resolution rate, the re-segmentation has not landed and the messaging, not the product, is the problem; (2) instrument the onboarding-hours claim with the same five interviews, since the new-market half needs a measured number to create a budget; (3) hold resolution-rate claims to the evidence in `research/capability_table.md` and never compete on that axis in year one.
