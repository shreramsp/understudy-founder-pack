# Sales roadmap — organisation, influence, access

> **What this is** — Blank's Customer Validation Phase 1 set: the organisation map of the buyer, the influence map of who actually sways the decision, the access map of how a stranger reaches them, and the sales process with the artifact required at each step.
> **Why it exists** — "we'll sell to MSPs" hides the fact that nobody has established who signs, who can quietly kill it, and how a founder with no relationship reaches either. For this product the veto sits in two places most maps miss: the engineers being recorded, and the MSP's own client.
> **How to read it** — the influence map is the important one; the organisation map is conventional and the access map is tactics. A skeptic should attack whether the client-side veto (Sonia) can be handled without lengthening every deal.
> **Depends on / feeds** — cites [personas.md](personas.md), [gtm.md](gtm.md); feeds `validation/decision_making_unit.md`, `validation/discovery_guide.md`, `narrative/one_pager.md`.

## 1. Organisation map — a 34-person MSP

```
   Owner / COO  (Marcus)  ── signs, owns P&L
        │
   Service delivery mgr (Dana) ── owns queue, SLAs, onboarding runbook
        │
   ├── Tier 1 techs (Priya ×5)      ── highest ticket volume
   ├── Tier 2 techs (×4)
   └── Principal engineer (Ray)     ── escalation, deepest env. knowledge
   
   [outside the org]  Client IT director (Sonia) ── approves what runs in their environment
```

70% of US MSPs have fewer than 50 employees [S31], so this chain is short and the owner is reachable — the structural advantage of this segment over enterprise ITSM.

## 2. Influence map — who actually decides

| Role | Formal power | Real influence | What moves them | What they kill it with |
|---|---|---|---|---|
| **Marcus** (owner) | **Signs** | High | Engineer-hours saved per client, in dollars | "Not this quarter" |
| **Dana** (delivery mgr) | Recommends | **Highest** — Marcus asks her before signing | Fewer escalations; a runbook that stays true | "My team won't use it" |
| **Ray** (principal) | None | **Veto from below** | Reading a skill derived from his own session and finding it correct | Quiet non-cooperation; one credible "this is RPA again" in the team channel |
| **Priya** (tier 1) | None | Low individually, decisive in aggregate | Client-specific procedures when she is stuck | Not narrating; working around the capture |
| **Sonia** (client IT) | **Veto** | Absolute, **and there is one of her per client environment** | A tenant-isolation architecture she can read, plus a clear answer to where raw capture is processed | Security review that never ends |

**The two non-obvious vetoes are both about the recording.** Ray and Priya are the data source; Sonia owns the environment being recorded. **A deal can be signed by Marcus and still fail three times over.** This is why `validation/decision_making_unit.md` treats the engineers as a buying-unit role rather than as users.

### Sonia recurs, and that is the expansion constraint

The first version treated the client-side security review as a one-time gate cleared by a one-pager. Both halves were wrong, and the second is expensive:

- **A one-pager does not end a review; it opens one.** What actually arrives is a CAIQ or SIG-lite, a SOC 2 Type II report, a pen-test summary, a sub-processor list, a cyber-insurance certificate and a DPA. A design-stage company has none of these, and no artifact in this pack has budgeted for them. **SOC 2 is a 6–12 month prerequisite, and it gates the marketplace channel as well** [channel_plan.md](channel_plan.md).
- **There is one Sonia per client environment, and this business expands per environment.** Removing the *sales* conversation from expansion (step 7) does not remove the *security review*, which is the longer pole at ~6 weeks per environment [personas.md](personas.md) §5. Environment velocity is therefore gated by review throughput, not by selling capacity — which is what makes the ramp in [market_sizing.md](market_sizing.md) §3 conservative rather than pessimistic.
- **The question was not the skill library, it was the raw capture — and it is now answered (D6).** Sonia's actual question is *what leaves my environment?* **Distillation is two-stage (D6, corrected): clustering and abstraction run inside the *MSP's own* tenant — the boundary where capture actually originates — and only abstracted variance envelopes carrying no tenant identity reach the vendor. Her recordings never leave her MSP's control, and nothing identifying her tenant reaches us.** That converts her review from a data-transfer assessment — the kind that stalls for months — into a boundary-and-egress assessment, which is the kind that closes. It does not remove the review, and the ~6-week figure should be held until measured, but it removes the objection most likely to end it in refusal. **This is an architecture constraint on `tech/architecture/`, not a preference.**

## 3. Access map — how a stranger reaches them

| Target | Best route | Second route | Does not work |
|---|---|---|---|
| Marcus | Peer group / mastermind introduction from another owner | MSP-focused podcast appearance | Cold email (test the floor once, expect <5% [gtm.md](gtm.md)) |
| Dana | Through Marcus, or MSP delivery-operations communities | Conference session on onboarding cost | Vendor webinars |
| Ray | **Never sold to — convinced.** Through a technical write-up of the graceful-degradation mechanism and the E2 experiment (D2) | Open evaluation harness he can run himself | Any pitch framed as automation replacing expertise |
| Sonia | Through Marcus, with the architecture document attached before her review opens | — | Reaching her directly; it is the MSP's relationship |

## 4. Sales process and the artifact each step requires

| # | Step | Artifact required | Exit criterion |
|---|---|---|---|
| 1 | Peer-group introduction | — | Booked 30-min call |
| 2 | Pain conversation (no pitch) | Discovery script `validation/discovery_guide.md` | Onboarding cost named unprompted, in hours |
| 3 | ROI framing | **Engineer-hours ROI calculator** (their numbers, not ours) | Marcus states a dollar figure back |
| 4 | Technical credibility | **RPA differentiation write-up + E2 results** (D2) | Ray does not object in the room |
| 5 | Security clearance *(recurs per environment, ~6 weeks)* | **Tenant-isolation architecture document** + a stated answer on where raw capture is processed. Full evidence pack (SOC 2, pen test, DPA) is a 6–12 month prerequisite, not a document | Sonia's review opens with a document rather than a questionnaire, and closes in weeks rather than months |
| 6 | Design-partner pilot, one environment | **Pilot agreement** — a named artifact that does not yet exist. Three clauses: (a) *anonymised* publication rights ("a 34-person Midwest MSP", never a named client, since the sessions sit under the MSP's own client-confidentiality terms and the number is not purely theirs to give); (b) a **definition of "resolved ticket" with an arbitration rule** — outcome pricing dies in month three on who adjudicates a ticket the agent touched and a human finished; (c) capture scope and retention | One environment onboarded, hours measured |
| 7 | Convert + expand | Measured time-to-first-skill | Environment #2 without a sales conversation |

**Steps 4, 5 and 6 are the ones a conventional SaaS process omits**, and they are the three most likely to lose the deal. Two are documents that can be written before the first call and do not exist yet; one (the SOC 2 evidence pack) is a 6–12 month programme that has to start long before it is asked for.

**Recommended next 3 moves:** (1) write the tenant-isolation document, the RPA differentiation write-up and the pilot agreement before the first pilot conversation — all three gate early steps and none requires product; (2) specify the envelope schema precisely enough for a security reviewer to audit — D6's promise is only as strong as the guarantee that an envelope entry carries no tenant identity, and that guarantee is what shortens every review; (3) start the SOC 2 clock early — it gates both the enterprise-adjacent clients and the marketplace channel, and it cannot be compressed later.
