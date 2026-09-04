# Personas

> **What this is** — five persona cards spanning the full user spectrum plus the economic buyer, each with the pain moment, the current workaround, the switch trigger, the language they would actually use, and the objection that must be overcome.
> **Why it exists** — a pack that says "MSPs" as its customer will produce copy nobody recognises themselves in. These cards are what `product/journeys/`, `narrative/`, the sales roadmap and the website's "who it's for" section all draw from, so a vague card here becomes vague everything.
> **How to read it** — Marcus is the payer and Dana is the champion; those two decide whether this company exists. Priya is the edge-low case the product must serve with dignity, and Ray is the objection with a keyboard. A skeptic should attack whether Ray's objection is actually surmountable.
> **Depends on / feeds** — cites [market_type.md](market_type.md), [research/sources.md](../research/sources.md); feeds `product/journeys/`, [value_prop_canvas.md](value_prop_canvas.md), [sales_roadmap.md](sales_roadmap.md), `validation/decision_making_unit.md`.

---

## 1. Marcus Whelan — MSP owner / COO · **the payer** · 34-person MSP, 41 clients

**Context.** Runs a **$2.9M-revenue** MSP in the US Midwest: 34 people, of whom **20 are billable technicians** (the rest are sales, dispatch, admin and a part-time vCIO). Revenue per technician is **$145k, below the healthy $150–200k band**, and revenue per employee is **$85k against a $142k average** [S32] — he is not a top-quartile operator, which is the whole reason he is a buyer. He has turned down two clients this quarter because he could not staff them: he is in the 26% [S33].
**Pain moment.** An 80-seat manufacturer signs on Monday — a large client by his book's standards, where the 41 clients average ~16 users each. Onboarding is 60 engineer-hours [S21] pulled from billable work, and the client expects SLA coverage from day one. He is paying twice: once in unbilled hours, once in the tickets his team fumbles because nobody knows the environment yet.
**Current workaround.** Assign his best engineer to shadow-document the environment for three weeks, and eat the margin.
**Trigger to switch.** A client win he cannot staff. Not a demo — a signed contract he is afraid of.
**Language he'd actually use.** *"I can't hire my way out of this. Every new logo costs me a month of my best guy before it makes a dollar."*
**Objection to overcome.** *"So I record my engineers, and in two years you sell what they know back to me — or to the MSP down the road."* Answer must be architectural (tenant isolation, A8), not reassuring.

---

## 2. Dana Ortiz — Service delivery manager · **the champion** · owns the queue and the onboarding runbook

**Context.** 20 technicians, **~500 tickets/month across the whole book** — consistent with S34's independently reported ~492/month and with the users-based build in [market_sizing.md](market_sizing.md) §2. Owns SLAs and the onboarding checklist nobody keeps current.
**Pain moment.** Third time this month an engineer escalates a ticket that a colleague solved last week at a different client — the procedure existed, in someone's head, and never reached her runbook.
**Current workaround.** IT Glue documentation she nags people to update, plus Slack archaeology.
**Trigger to switch.** Losing a senior engineer. Two weeks' notice, and eleven years of environment knowledge walking out with them.
**Language she'd actually use.** *"Our documentation is a museum. It describes an environment we stopped having a year ago."*
**Objection to overcome.** *"My engineers will tell me they don't have time to narrate what they're doing."* Answer: capture must be passive by default, narration optional and rewarded.

---

## 3. Priya Raman — Tier-1 technician · **edge-low** · 14 months' experience

**Context.** Runs the same twenty procedures all day: password resets, mailbox permissions, MFA re-enrolment, printer queues. First line for 41 clients, each slightly different.
**Pain moment.** A ticket for a client she has never touched. The runbook is generic; the client's Okta is configured unlike the others; she burns 25 minutes and escalates, which counts against her.
**Current workaround.** Ask in the team Slack channel and wait.
**Trigger to switch.** The first time the agent hands her a client-specific procedure instead of a generic one — she stops feeling like the newest person in the room.
**Language she'd actually use.** *"I don't need it to do my job. I need it to tell me how this client does this thing."*
**Objection to overcome.** *"Am I training my replacement?"* This is the honest one. Answer: her queue is the repetitive twenty; what the agent absorbs is the part she does not want, and the escalation path is where her career is. **If this answer is not true in the product, the recording programme fails from the inside.**

---

## 4. Ray Kowalczyk — Principal escalation engineer · **edge-high** · 19 years, the person everything ends up with

**Context.** Handles what tier 1 and 2 cannot. Holds the environment knowledge for the 8 most complex clients. Deeply sceptical of automation, with earned reason: he has cleaned up after two RPA projects.
**Pain moment.** Interrupted 14 times a day for things he has explained before. He is the bottleneck and he knows it, and the interruptions are why the genuinely hard work slips.
**Current workaround.** Answers in Slack, occasionally writes it down.
**Trigger to switch.** Seeing a skill derived from *his* session, in text he can read and correct, and finding it right. Not a demo — his own work, played back accurately.
**Language he'd actually use.** *"Show me the thing it thinks it learned. If it's a black box, we're done."*
**Objection to overcome.** *"This is RPA with a chatbot on it, and I've watched that fail twice."* This is D2's argument, and it must be delivered as mechanism plus the E2 altered-UI experiment, not as reassurance. **Ray is the single most important persona in this pack: he can veto adoption from below without ever attending a meeting.**

---

## 5. Sonia Achebe — Client-side IT director · **the veto** · at the MSP's customer

**Context.** Signs off on what the MSP may deploy inside her environment. Not the buyer; entirely able to stop the deal.
**Pain moment.** Her MSP proposes software that records administrative sessions inside her network. Her security review has one question: what leaves my environment?
**Current workaround.** Blanket refusal, or a 6-week review.
**Trigger to approve.** A tenant-isolation architecture she can read, plus a clear statement that the compounding global library carries no client data (A8).
**Language she'd actually use.** *"I'm not approving a recorder in my admin plane without knowing exactly what it keeps and where it goes."*
**Objection to overcome.** All of it. **She is why the hybrid library architecture is a security document before it is a moat.**

---

## Spectrum coverage — one system, no separate tiers

| Edge | Persona | Served by the same system how |
|---|---|---|
| Low support | Priya | Receives client-specific procedures instead of generic runbooks; the agent's library is her onboarding |
| Beachhead core | Dana | The library *is* the runbook of record, maintained by observation instead of by nagging |
| High / power | Ray | His sessions become the highest-value skills; he reviews and corrects them as readable text, and is interrupted less |

No "lite" fork and no separate product tier: the same skill library serves all three, differing only in whether a person is consuming a skill or authoring one by working.

**Recommended next 3 moves:** (1) validate Priya's and Ray's objections in discovery interviews before writing a line of product copy — both are adoption-fatal and neither is a buyer objection; (2) build Sonia's security one-pager before the first pilot, not after her review starts; (3) make Ray's "show me what it learned" the core demo, since it converts the hardest persona.
