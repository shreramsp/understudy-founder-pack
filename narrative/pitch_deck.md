# Pitch deck — 15 slides

> **What this is** — the deck as markdown: one section per slide, each title stating the takeaway as a full sentence, a 3–5 bullet payload, and a `visual:` line naming the supporting visual.
> **Why it exists** — a deck is the pack compressed to fourteen claims. This file is also what seeds `visuals/visual_manifest.md`: every `visual:` line below becomes a manifest row, so the visual layer is derived from what the story needs rather than from what is easy to draw.
> **How to read it** — the titles alone should carry the argument; if they do not, the deck has failed. A skeptic should attack slide 10, where the pack admits it has no traction, and slides 11–12, which give away the two limits most decks hide.
> **Depends on / feeds** — arranges [one_pager.md](one_pager.md), [vc_memo.md](vc_memo.md) and the layers beneath them; feeds `visuals/visual_manifest.md`, `startup-website`.

---

### 1 · Every AI service desk can resolve a ticket. None can learn where it is.
- Deployment friction, not resolution capability, is the category's real bottleneck.
- For an MSP this is not setup cost — it is cost of goods, paid again for every client.
- 25–40 engineer-hours to onboard a median client, before a ticket is billed [S21].
- 26% of MSPs say they cannot staff clients they could otherwise win [S33].
`visual: V01 — the knowledge cycle: acquire → decay → lose → re-acquire, with hours attached`

### 2 · The market split the problem in half and left the join manual.
- **Discovery tools record work and emit a diagram** a human must implement (UiPath, Celonis, FortressIQ).
- **Resolution tools execute but must be told how** (Ravenna, Atomicwork, Moveworks).
- Both halves are mature. The handoff between them is where the hours go.
`visual: V02 — the two-axis map: knowledge acquired by configuration vs observation × produces artifact vs executes`

### 3 · FortressIQ had the right input in 2017 and no executor to send it to.
- Computer vision over employee work; claimed ~90% reduction in discovery time [S7].
- Acquired into an RPA vendor, December 2021 [S5].
- The automation discovery fed was RPA: 30–50% of projects fail, maintenance reaches 60% of cost [S10][S11].
- **Discovery was never the weak link. The executor was.**
`visual: V03 — timeline: FortressIQ 2017–2021 against the computer-use capability curve 2024–2026`

### 4 · A recording can now become an executable skill, which was impossible eighteen months ago.
- Computer-use agents: 12% (Apr 2024) → ~86% on OSWorld-Verified (Sep 2026) [S14][S15].
- `SKILL.md` became an open cross-vendor standard, 26+ platforms [S24].
- A recorded procedure finally has both an executor and a portable place to live.
`visual: V04 — OSWorld capability curve with the SKILL.md standard marked, and the honest ceiling annotated`

### 5 · Understudy learns each client environment by watching engineers work.
- Record: screen, actions, and 10 seconds of spoken reasoning at decision points.
- Distil: cluster recordings into a readable `SKILL.md` library, inside the MSP's own tenant.
- Execute: under approval gates, verifying every action against a goal-state criterion.
- **Supervised throughout. Never unattended.**
`visual: V05 — the closed loop: Watch → Distil → Rehearse → Gate → Act → Verify → Learn`

### 6 · The demo is a technician resolving a ticket at a client she has never touched.
- The desk surfaces the procedure *and the two ways this tenant differs*.
- The difference came from two engineers who hit it months apart. Nobody wrote it down.
- When the situation leaves the skill's envelope, the agent stops and escalates rather than improvising.
`visual: V06 — the ticket-side panel: matched skill, tenant deviations, one gated approval`

### 7 · A skill states the goal; an RPA step states the interface. That is why one recovers and one does not.
- RPA does have success checks — but they assert that *a control exists in a state*.
- A broken selector halts loudly or proceeds wrongly. Neither recovers.
- A skill's criterion is the **goal**, so a changed UI becomes a re-grounding search against an intact target.
- Tested against a **selector-based** baseline, not a strawman: `validation/` E2.
`visual: V07 — contract-vs-goal: the same procedure under a UI change, side by side`

### 8 · Each environment makes the next one cheaper — and one MSP customer brings forty-one.
- The happy-path procedure is in vendor docs. **That half is copyable and we say so.**
- What compounds: how procedures *differ* across real tenants, how they fail, how engineers verify them.
- One MSP customer contributes ~41 environments; one internal-IT customer contributes one.
- Only abstracted patterns cross the boundary — raw recordings never leave the MSP's control.
`visual: V08 — the variance envelope: one procedure, many tenants, the distribution as the asset`

### 9 · ~12,000 US MSPs in the serviceable band, a $179M SAM, and it is a wedge rather than a category.
- ~45,000 US MSPs; ~12,000 at 10–100 employees [S31].
- Two-part tariff: ~$6/resolved ticket plus a banded per-environment fee ($400/$1,500/$1,500), first environment free. ~$14,930/yr per MSP at steady state.
- **SAM ≈ $179M.** Internal IT is ~$288M more and this deck does not claim it.
- Roughly 73% of three-year revenue is one-time onboarding — a services shape during land, and we price it as such.
`visual: V09 — bottom-up SAM build, arithmetic shown, with the sensitivity band`

### 10 · We have no traction, and every number in this deck is a declared target.
- No pilot, no customer, no measured result, no code.
- The mechanism is validated at user-study scale in the literature; nothing is validated across environments.
- Every operating figure carries its source or an `(assumption)` tag.
- **The one number that matters: do skills from environment A work in environment B? Below ~70%, we say so.**
`visual: V10 — the evidence ledger: what is sourced, what is assumed, what is unknown`

### 11 · The first environment costs more, not less — and we do not charge for it.
- Environment 1: 31–46 hours against a 25–40 baseline. The work is unchanged; review is added.
- Environment 2: 18–28 hours. **Compression begins at the second client, not the first.**
- So environment 1 is waived. Charging for it would be charging for a loss.
- A design partner's timesheet should confirm our number, not falsify it.
`visual: V11 — hours per environment, 1 through 5, against baseline, with the waiver marked`

### 11b · We are not cheaper per ticket. We are throughput at a capacity ceiling.
- The tickets we automate are the cheapest quartile of an MSP queue — resets, permissions, provisioning, alert remediation.
- A junior tech clears those at roughly $2–6. **At $6 we are at or above their marginal cost.**
- So the pitch is not savings. **26% of MSPs cannot staff the clients they could win** [S33]; the alternative to us is a hire they already failed to make.
- We say this on a slide rather than have a buyer find it in their own numbers.
`visual: V33 — cost per ticket: their marginal cost vs our price, with the capacity ceiling marked`

### 12 · Where a real API exists, we are the wrong tool — and that bounds the mechanism.
- Driving an API beats driving a UI on speed, cost and stability.
- Capture's durable value concentrates where APIs are poor: native admin consoles, terminals, legacy tooling.
- As vendors ship better APIs, that surface shrinks.
- **We prefer APIs wherever they exist rather than defend UI automation on principle.**
`visual: V12 — the admin surface map: API-covered vs UI-only, with the addressable slice highlighted`

### 13 · The founder's edge is the clustering problem, and the market gap is stated rather than papered over.
- Solo founder, AI/agents engineering background. The synthesis core is the hard bet and it is the founder's ground.
- **No managed-services operating history** — a named gap (A6), to be closed with design partners rather than claimed.
- First hire is an MSP-side operator, not an engineer.
`visual: V13 — founder-market fit: what is covered, what is missing, and how it gets closed`

### 14 · Pre-seed to answer one question, with the falsifying number declared in advance.
- ~40-week build floor to the evaluation harness and the transfer test.
- First paid pilot at month 12 — **only if every item lands at its optimistic bound.** That is the single point of failure.
- Use of funds: the harness before the clusterer, so the answer is evidence rather than opinion.
- **Ask: pre-seed. Milestone: cross-environment skill transfer measured, published, and honest either way.**
`visual: V14 — use of funds against the one milestone, with the go/no-go threshold marked`

---

## What this deck deliberately does not do

- **No autonomy slide.** Excluded by the claim boundary (D1), not withheld for modesty.
- **No logo wall, no testimonials, no invented metrics.** There are no customers.
- **No cost-savings claim on the ticket half.** We are at or above the buyer's marginal cost there, and slide 11b says so (D18).
- **No blended 10× claim.** The whitepaper locates the leverage precisely: ~8× on the maintenance line, ~1.3× on repeat onboarding. A single headline multiplier would misuse its own table.
- **No slide titled "Market" or "Team".** Titles are claims; a label is a wasted slide.

**Recommended next 3:** (1) build V07 first — the contract-vs-goal visual carries the argument that converts technical evaluators; (2) treat slides 10, 11 and 12 as non-negotiable, since a deck whose limits are visible is the one that survives diligence; (3) seed `visuals/visual_manifest.md` directly from the 14 `visual:` lines above.
