# Journey — edge-low: Priya's first ticket at a client she has never touched

> **What this is** — the least-supported user on the spectrum succeeding at work she could not do unaided, narrated beat by beat with the component acting and the durable record written at each step.
> **Why it exists** — the edge-low case is where a product either serves the whole spectrum or quietly serves only the confident. It is also where this product's adoption risk concentrates: Priya is the person most plausibly threatened by it, and if her journey reads as replacement rather than support, the capture programme fails from inside [strategy/personas.md](../../strategy/personas.md) §3.
> **How to read it** — the component column is the test. A skeptic should be able to list which components fired in what order without reading the prose. Attack beat 7, where the system declines to act.
> **Depends on / feeds** — inherits [PRD.md](../PRD.md), [features_flagship.md](../features_flagship.md), personas §3; feeds `visuals/`, `narrative/vc_memo.md`, [ux_spec.md](../ux_spec.md).

**Persona.** Priya Raman, 14 months' experience, tier-1 technician. Handles first-line for 41 client environments, each configured slightly differently.
**Session goal.** Resolve an MFA re-enrolment for a user at Brightwater Dental — a 22-person client on Microsoft Entra ID that Priya has never worked in — without escalating.

*Vocabulary note: this journey is Entra/M365 throughout. The first version mixed Okta and Entra terms in the same scenario, which is the kind of error a practitioner spots immediately.*
**Baseline today.** She reads a generic runbook, finds Brightwater's Okta configured unlike the others, burns 25 minutes, escalates to Ray. The escalation counts against her.

---

**08:41 · Ticket lands.** "Can't get into email on my new phone." Priya opens it in the PSA.
→ *Component:* **X14 ticket-system integration (read)** pulls ticket context and the client identity.
→ *Record:* ticket bound to environment `brightwater`.

**08:41 · The desk offers what it knows.** Alongside the ticket, a panel: *MFA re-enrolment — Brightwater Dental. 3 skills available. This client differs from your other Entra tenants in 2 ways.*
→ *Component:* **X17 global stack layer** matched the ticket to a known procedure shape; **N9 variance envelope** supplied the two deviations specific to this tenant.
→ *Record:* a skill-match event, and which envelope variant was selected.

**08:42 · She reads before she acts.** The skill opens with its goal and its success test — *Succeeds when: the user completes an MFA challenge from the new device* — then the steps, then a flagged line: *Brightwater has a Conditional Access policy requiring a compliant device for registration, which blocks enrolment from a new personal phone. Two engineers hit this; both resolved it with a **Temporary Access Pass**, not by weakening the policy.*
→ *Component:* **F6 skill synthesis** (goal + success criterion), **N9** (the deviation), **N13 authorship attribution** — the note carries Ray's and a colleague's names.
→ *Record:* skill view, by whom, which version.
**This beat is the product.** Nobody told Priya about Brightwater's conditional access. Two engineers hit it months apart, and the system kept what they did.

**08:44 · She chooses supervised execution.** Priya clicks *run with me* rather than doing it by hand. The agent proposes step 1 — verify the user's identity against the ticket's originating address — and waits.
→ *Component:* **X10 promotion ladder** has this skill at *gated* for this environment; **X6 approval queue** surfaces each action inline.
→ *Record:* run started, mode `gated`, operator Priya.

**08:45 · Read steps proceed; she watches.** The agent reads the user's enrolment state and reports it. No approval needed — reads are unrestricted.
→ *Component:* **X5 action-class policy** classified these as read; **X1 read-only executor** ran them.
→ *Record:* two read actions, attributed to the **agent's own principal** (**X7**), visible in Brightwater's audit log as a named non-human identity.

**08:47 · The first mutating step stops for her.** *Issue a Temporary Access Pass for j.mbeki@ — single-use, valid 60 minutes. Approve?* With one line of effect: *this user only; expires on its own; does not alter any policy.*

*A TAP is a real Entra primitive built for exactly this case — time-boxed, per-user, and it leaves the Conditional Access policy untouched. The first version invented an "auto-expiring conditional-access bypass", which does not exist in either Entra or Okta.*
→ *Component:* **X5** classified it reversible-write; **X6** requires human approval at this ladder rung; **X8 reversible-write execution** has the undo path recorded before the action runs.
→ *Record:* approval by Priya, undo path stored.

**08:48 · The system declines to guess.** The user's device shows an enrolment already in progress from an unrecognised location. The skill's preconditions do not cover it. The agent stops: *This doesn't match what I've seen in 14 environments. Routing to Ray with what I found.*
→ *Component:* **X9 envelope enforcement** — outside the declared envelope, escalate rather than improvise (`P5`).
→ *Record:* escalation with the full action trace attached.
**This is the beat a skeptic should attack, and it is the one that makes the product safe.** A system that improvised here might have cancelled a legitimate enrolment or approved a hostile one. Priya's queue metric is unharmed: an escalation the system initiated is not an escalation she failed.

**08:52 · Ray resolves it in four minutes**, because the trace told him what had already been checked. His session is captured.
→ *Component:* **N1 capture**, **N5 failure/abort labelling** marks this as an escalation-resolution session — the kind that contains what successful runs never do (`P2`).
→ *Record:* a labelled session against `brightwater`, queued for distillation.

**09:20 · A variant is *proposed*, not shipped.** Stage-1 distillation runs on the MSP's node (D6). The unrecognised-registration branch becomes a **candidate** third variant, queued for Ray's endorsement — the same governance the beachhead journey applies, because a library that self-modifies without the authoring engineer's sign-off breaks `P8` and the first version of this journey quietly did exactly that.
→ *Component:* **N6 stage-1 distillation**, **N9 + egress filter**, **X19 skill correction**, **X13 envelope widening** (pending).
→ *Record:* candidate variant awaiting endorsement.

**Next morning.** Ray endorses it with one edit. Skill v4, variants 3, contributors now including him.
→ *Record:* endorsed variant; the abstracted pattern — *"registration blocked by compliant-device policy; resolved by time-boxed pass"* — becomes eligible for the global layer. **Brightwater's name, domain and policy id do not travel with it.**

**Next week.** The same situation arises at a different client. Priya sees the branch, follows it, and does not escalate.
→ *Component:* **X17 global stack layer** — the *pattern* transferred; Brightwater's data did not.

---

## What the durable record holds after this session

| Artifact | Content |
|---|---|
| Skill `okta-mfa-reenrolment` | v4 · 3 variants · success criterion · contributors: Ray, 2 others |
| Stage-1 record (**stays in the MSP's tenant**) | compliant-device policy blocks registration (Brightwater); registration-in-progress-from-unknown-location |
| Envelope entry (**eligible to cross**) | `{registration blocked by device-compliance precondition; resolved by time-boxed pass; observed in 6 tenants}` — no tenant name, domain, user or policy id |
| Action log (client-visible) | 2 reads, 1 approved reversible write, 1 escalation — all under the agent's named principal |
| Session store (in-boundary) | Ray's escalation session, labelled, expiring per retention policy (**X22**) |
| Priya's record | one ticket resolved with assistance, one system-initiated escalation — **not** counted as her failure |

## Why this is dignity rather than replacement

Priya did not become a button-pusher: she read the procedure, approved the consequential step, and learned Brightwater's conditional-access quirk in the process. The system absorbed the part she found demoralising — not knowing what she could not have known — and left her the judgement. **Had beat 8 improvised instead of escalating, or had beat 3 shown her a black box instead of readable text, this journey would read as replacement and `P8` would fail.** The design choices that prevent that are `P6` (readable) and `P9` (verification before action), not the copy.

**Recommended next:** validate beat 3 in discovery — ask five tier-1 technicians whether "here is how *this client* does it" is what they actually want, or whether they want the ticket simply gone. If it is the latter, this journey is the wrong shape and the edge-low proposition needs rethinking.
