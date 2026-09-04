# Journey — one ordinary Tuesday across every touchpoint

> **What this is** — a single day at one MSP seen from all four seats: the tier-1 technician, the delivery manager, the principal engineer, and the owner who signs the invoice — plus the client-side IT director who can stop everything.
> **Why it exists** — the other three journeys each follow one person through an arc. This one tests whether the product coheres when four people touch it in the same eight hours with different goals, and whether the payer ever sees anything at all. A product the buyer never opens is a renewal risk regardless of how well it works.
> **How to read it** — watch what each seat sees at the same moment. A skeptic should attack 14:20, where the system's mistake reaches a real client.
> **Depends on / feeds** — inherits [PRD.md](../PRD.md), all three sibling journeys, personas §1–§5; feeds `visuals/`, `narrative/pitch_deck.md`, [ux_spec.md](../ux_spec.md).

**Setting.** Tuesday — per [S34] the week's heaviest ticket day. 20 staff, 41 environments.

**Ticket volume, derived rather than asserted.** ~620 served users across the book × 0.8 tickets/user/month ≈ **~496 tickets/month** [strategy/market_sizing.md](../../strategy/market_sizing.md). Of 20 staff, ~8 are on the ticket queue full-time (the rest are projects, dispatch, vCIO, admin), so **~62 tickets/technician/month, ~3/day**, with Tuesday running roughly double. The first version had Priya alone closing 11 in a morning — ~400/month, or 80% of the whole book from one of twenty people.

---

## 07:50 — Marcus (owner, the payer) · 90 seconds, once a week

He opens one screen before his first meeting: **Client 38 onboarded — 22 engineer-hours against a 25–40 median-band baseline.** `(illustrative: target, not measured)` Below it, the month: 4 environments onboarded, ~46 engineer-hours saved `(illustrative)`, and the two clients where the number was **worse** than baseline — including the one where it always is, the first.
→ *Component:* **N14 onboarding meter**, **X20 environment dashboard**.
**The two bad ones are shown first, deliberately.** A dashboard that only reports wins gets distrusted the first time the owner hears about a problem from a client instead.
→ *This is the payer's entire product surface.* He is not a user; he is a buyer who needs the number to still be true, and 90 seconds a week is the right amount of his attention to ask for.

## 08:41 — Priya (tier-1) · the ticket from [edge_low.md](edge_low.md)

MFA re-enrolment at a client she has never touched. Skill matched, variance surfaced, one gated approval, one system-initiated escalation when the situation left the envelope.
→ *Component:* **X14 → X17 → N12 → X6 → X9**.
→ *Record:* resolved with assistance; the escalation is not counted against her.

## 09:15 — Dana (delivery manager) · triage, ten minutes

Her queue view shows four skills in shadow at two clients, one skill paused by drift, and three deviations waiting for engineer judgement.
→ *Component:* **X20**, **X12 drift detection**, **X3 deviation report**.
She promotes nothing today. Two of the shadow skills are one clean week away; she leaves them.
**The product's job here is to be ignorable.** Most days the correct action is none, and a queue that manufactures urgency to seem valuable will be muted within a month.

## 11:30 — Ray (principal) · a cross-environment question

*Which of my environments have this conditional-access pattern?* Six, three of which he did not expect.
→ *Component:* **X17** + **N9 variance envelope**, patterns only — no client data crosses a boundary (D6).

## 13:05 — Priya · the unglamorous majority

Eleven tickets between 09:00 and 13:00. Six matched a skill and ran gated; three were novel and she did them by hand while capture ran; two were the kind of request no automation should touch — a user wanting a policy exception — and she just talked to the person.
→ *Component:* **N1 capture** on the two novel ones; nothing at all on the human one.
**The one the system stayed out of matters.** A product that tries to intermediate a conversation about a policy exception makes the day worse, and `P9` plus envelope enforcement are what keep it out.

## 14:20 — The mistake · and how far it gets

A gated skill proposes disabling a mailbox forwarding rule at a 60-person client. The approval line says *removes forwarding from j.okafor@ to an external address*. The technician approves it. It was legitimate — an executive's deliberate forward to a personal account, set up by Ray eight months ago and documented nowhere.

**What contained it:**
→ **X4 success-criterion verification** confirmed the action did what it said — the action was executed correctly. **The system was not wrong about what it did; it was wrong about whether to do it.** No verification step catches that.
→ **X8 reversible-write execution** had recorded the undo path before acting. Restored in 40 seconds once the executive called.
→ **X7 agent identity** meant the client's audit log showed exactly which principal made the change, at what time, under whose approval — so the post-mortem took four minutes rather than an afternoon.
→ **X3 deviation report** routed it to Ray, who added the exception to the skill's envelope. **N9/X13** widened it.

**What genuinely failed:** the skill's preconditions did not encode "check for documented exceptions", because no captured session had ever encountered one. **This is `P2` — happy paths are not procedures — arriving in production.** The library learns the exception only by meeting it, and the first meeting is a live client.

**14:45 — somebody has to tell the client, and it is not the product.** Dana calls Sonia before Sonia hears it from the executive. The MSP discloses: what the agent did, under which principal, that it was reverted in 40 seconds, and what changed in the skill so it cannot recur. **The pack assigns this to Dana explicitly**, because a veto-holder who learns about an agent's mistake secondhand reopens a review that took six weeks to close [strategy/sales_roadmap.md](../../strategy/sales_roadmap.md) — and there is one of her per environment.
→ *Component:* **X21 audit export**, run same-day rather than quarterly.
→ *The product's job here is narrow and real:* make the disclosure take four minutes and be complete. It cannot make the call.

**And somebody has to decide whether this ticket is billable.** The agent acted, **X4** verification passed, and a human then undid the work. Under per-resolved-ticket pricing (D4), is that a resolution?
**The pack's answer, owed to the pilot agreement:** no. **A resolution is billable when the declared success criterion passed *and* no human reversed the action within the ticket's life.** Reversal within the ticket voids the charge. This is the clause `strategy/sales_roadmap.md` step 6b names as where outcome pricing dies in month three, and it is settled here rather than discovered in an invoice dispute.
→ *Component:* **X4** result plus reversal state feed the billing record — a **Next-tier requirement**, not an afterthought.
**A skeptic should attack exactly here, and the honest answer is that this class of error is not eliminable, only survivable.** Reversibility, attribution and gating are what make it a 40-second incident instead of a lost client. **A product that promised this could not happen would be lying, and the pack does not claim it** [BRIEF.md](../../BRIEF.md) claim boundary.

## 16:00 — Sonia (client-side IT director) · the quarterly review

She exports the action log for her environment: every action, its skill version, its verification result, the approving human, under the agent's named principal. She also confirms what she was told at onboarding — no raw recording has left her boundary.
→ *Component:* **X21 audit export**, egress attestation (D6).
→ She is not a user either. **She needs one file, twice a year, and for it to be boring.**

## 17:30 — Dana · Friday's work, started early

Three deviations resolved, one skill promoted, one rejected outright — a technician's idiosyncratic shortcut that should not become the house method.
→ *Component:* **X19 skill correction UI**, **X10 promotion ladder**.
→ *Record:* the rejection, with its reason, which is as valuable as the promotion.

---

## The day, by seat

| Seat | Time in product | What they need it to be |
|---|---|---|
| **Marcus** (payer) | ~90 seconds/week | A number that is still true, including when it is bad |
| **Dana** (champion) | ~20 minutes/day | Ignorable most days; unambiguous when it is not |
| **Priya** (edge-low) | continuous, ambient | A colleague who knows this client, not a supervisor |
| **Ray** (edge-high) | ~15 minutes/day | Inspectable, correctable, and occasionally an instrument |
| **Sonia** (veto) | one file, twice a year — **plus a same-day call when something goes wrong** | Boring, and never surprised |
| **Dana** (again) | owns the disclosure conversation | Fast, complete, and not defensive |

**One system, four relationships, no separate tiers.** Nobody was served by a "lite" version and nobody hit a wall meant for someone else — the difference between the seats is whether a person is consuming a skill, authoring one by working, judging one, or auditing one.

**Recommended next:** design the 14:20 path before the 08:41 path. **The incident journey is the one that decides whether a customer keeps the product**, and reversibility, attribution and a fast post-mortem are the features that make an inevitable error survivable rather than terminal.
