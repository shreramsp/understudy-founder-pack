# Pitch deck — 17 slides

> **What this is** — the deck as markdown: one section per slide, each title stating the takeaway as a full sentence, a 3–5 bullet payload, and a `visual:` line naming the supporting visual.
> **Why it exists** — a deck is the pack compressed to fourteen claims. This file is also what seeds `visuals/visual_manifest.md`: every `visual:` line below becomes a manifest row, so the visual layer is derived from what the story needs rather than from what is easy to draw.
> **How to read it** — the titles alone should carry the argument; if they do not, the deck has failed. A skeptic should attack the traction slide, where the pack admits it has none, and the two limit slides that give away what most decks hide.
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

### 4 · A recording can now become an executable skill — and the same benchmark says why we don't claim autonomy.
- Computer-use agents: 12% (Apr 2024) → ~86% on OSWorld-Verified (Sep 2026) [S14][S15].
- **The counterweight, on the same slide: those agents still fail ~80% of real workflows, and long-horizon completion is 20.6%** [S15][S16]. That is the binding constraint on the whole product.
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

### 7 · RPA can recover. It just can't re-plan — the goal isn't in the artifact.
- RPA asserts on world state, and Unified Target recovers from broken selectors via fuzzy, anchor, image and OCR fallbacks. **Anyone who says otherwise gets corrected in the room.**
- The narrower difference: **recovery is confined to fallbacks a developer enumerated in advance.**
- A skill carries the goal as a predicate the runtime holds at execution time — so it searches a space nobody anticipated.
- Tested against a **Unified-Target-equivalent baseline with fallbacks enabled**, built by a contracted certified practitioner and published: `validation/` E2.
`visual: V07 — contract-vs-goal: the same procedure under a UI change, side by side`

### 8 · Each environment makes the next one cheaper — and one MSP customer brings forty-one.
- The happy-path procedure is in vendor docs. **That half is copyable and we say so.**
- What compounds: how procedures *differ* across real tenants, how they fail, how engineers verify them.
- One MSP customer contributes ~41 environments; one internal-IT customer contributes one.
- Only abstracted patterns cross the boundary — raw recordings never leave the MSP's control.
`visual: V08 — the variance envelope: one procedure, many tenants, the distribution as the asset`

### 9 · ~12,000 US MSPs in the serviceable band, a $179M SAM, and it is a wedge rather than a category.
- ~45,000 US MSPs [S31]; **~12,000 in the 10–100-employee band `(assumption: derived from S31's "70% have fewer than 50 employees" — S31 defines no such band)`**.
- Two-part tariff: ~$6/resolved ticket plus a banded per-environment fee ($400/$1,500/$1,500), first environment free. ~$14,930/yr per MSP at steady state.
- **SAM ≈ $179M.** Internal IT is ~$288M more and this deck does not claim it.
- Roughly 73% of three-year revenue is one-time onboarding — a services shape during land, and we price it as such.
`visual: V09 — bottom-up SAM build, arithmetic shown, with the sensitivity band`

### 10 · We have no traction, and every number in this deck is a declared target.
- No pilot, no customer, no measured result, no code.
- The mechanism is validated at user-study scale in the literature; nothing is validated across environments.
- Every operating figure carries its source or an `(assumption)` tag.
- **The one number that matters: do skills from environment A work in environment B?** Pass bar ~70% across ≥30 scored pairs; **kill line below 50%** with the CI excluding it. **≥30 pairs cannot separate 70% from 60%, and we say so on this slide rather than in a footnote.**
`visual: V10 — the evidence ledger: what is sourced, what is assumed, what is unknown`

### 11 · The first environment costs more, not less — and we do not charge for it.
- Environment 1: 31–46 hours against a 25–40 baseline. The work is unchanged; review is added.
- Environment 2: 18–28 hours. **Compression begins at the second client, not the first.**
- So environment 1 is waived. Charging for it would be charging for a loss.
- **And on the ticket half we are not cheaper either** — the automatable subset costs an MSP roughly $2–6 and we charge $6. What we sell there is **throughput at a capacity ceiling**: 26% cannot staff the clients they could win [S33].
- A design partner's timesheet should confirm our numbers, not falsify them.
`visual: V11 — hours per environment, 1 through 5, against baseline, with the waiver marked`

### 12 · The channel is the constraint, not the product — and its margin is thin.
- Best economics: MSP buying groups. Primary: peer communities, **$4,000–9,000 CAC against a $10,100 ceiling — 3.4:1 at the top end.**
- **No channel has a comfortable margin.** The plan is viable only if CAC lands at the bottom of its range.
- **E4 — two weeks, three phone calls — establishes whether a vendor founder can join these groups at all.** It is the round's real gate.
- Marketplace is the only route to 100 customers and it is 18–24 months out behind SOC 2.
`visual: V34 — six channels against one ceiling, with the primary channel's top end marked`

### 13 · Ravenna can add recording. What they can't add is forty-one environments per customer.
- Adding discovery is a product decision for them, not a business-model conflict. **We say that rather than claim a moat we don't have.**
- The happy-path skill for Entra or M365 is authorable from vendor docs. **That half is copyable in a quarter.**
- What compounds is the **variance envelope** — how procedures differ across real tenants, how they fail, how engineers verify them.
- **One MSP customer contributes ~41 environments; one internal-IT customer contributes one.** We overtake on density, not speed — roughly quarters 8–10.
- ServiceNow is structurally inhibited: implementation is 3–5× its licence revenue [S20].
`visual: V35 — environment accumulation: MSP customers vs internal-IT customers over time`

### 14 · Where a real API exists, we are the wrong tool — and that bounds the mechanism.
- Driving an API beats driving a UI on speed, cost and stability.
- Capture's durable value concentrates where APIs are poor: native admin consoles, terminals, legacy tooling.
- As vendors ship better APIs, that surface shrinks.
- **We prefer APIs wherever they exist rather than defend UI automation on principle.**
`visual: V12 — the admin surface map: API-covered vs UI-only, with the addressable slice highlighted`

### 15 · The founder's edge is the clustering problem, and the market gap is stated rather than papered over.
- Solo founder, AI/agents engineering background. The synthesis core is the hard bet and it is the founder's ground.
- **No managed-services operating history** — a named gap (A6), to be closed with design partners rather than claimed.
- First hire is an MSP-side operator, not an engineer.
`visual: V13 — founder-market fit: what is covered, what is missing, and how it gets closed`

### 16 · $900k–1.2M to retire four company-killing assumptions, three of them for under $10k.
- **Ask: $900k–1.2M. Plan case $1,060k. 18–24 months.**
- **Four of five company-killing assumptions retire for under $10,000. The fifth is the company.** That is the whole sequencing argument.
- B1 discovery + cheap experiments **$5k** · B2 build to the harness **$420k** · B2b founder comp to month 24 **$175k** · B3 E1+E2 **$15k** · B4 security **$60k** · B5 pilots **$40k** · B6 MSP-side hire **$180k**, gated on E1 ≥70% · B7 reserve **$165k**, sized to the 55-week midpoint slip.
- **Reduced-scope case $880k** defers the hire and still reaches the measurement.
`visual: V14 — use of funds against dollars-per-assumption-retired`

### 17 · What this round has to prove before the next one, stated as three gates not one.
- **E1 ≥70%** — cross-environment transfer measured, published, honest either way.
- **3 paying MSPs through the same channel motion**, at a CAC inside the ~$10,100 ceiling.
- **Expansion without a sales conversation** — environment 2 onward at ≤6 weeks review cycle.
- The earlier version of this deck promised only the first. **A round that reaches one of three gates does not reach a seed**, and saying so is cheaper than discovering it at month 18.
`visual: V15 — the three seed gates, with what each costs to reach`

---

## What this deck deliberately does not do

- **No autonomy slide.** Excluded by the claim boundary (D1), not withheld for modesty.
- **No logo wall, no testimonials, no invented metrics.** There are no customers.
- **No cost-savings claim on the ticket half.** We are at or above the buyer's marginal cost there, and the hours slide says so (D18).
- **No blended 10× claim, and no maintenance multiplier either.** The whitepaper locates the leverage precisely: **~1.4× on repeat-environment onboarding, 0.8× — worse — on the first, and three effects that are not multipliers at all.** The maintenance-line multiplier was withdrawn when its baseline turned out to be hours nobody actually spends.
- **No slide titled "Market" or "Team".** Titles are claims; a label is a wasted slide.

**Recommended next 3:** (1) build V07 first — the contract-vs-goal visual carries the argument that converts technical evaluators; (2) treat the traction, hours and API-limit slides as non-negotiable — but note the limits are now **three slides, not four**, with the fourth replaced by the channel and incumbent-response beats the contract's arc requires and the earlier version omitted; (3) seed `visuals/visual_manifest.md` directly from the 14 `visual:` lines above.
