# Investor memo — Understudy

> **What this is** — the technical investor memo: thesis, why existing approaches are structurally insufficient, the architecture, concrete operating examples, why this can win, and honest risks.
> **Why it exists** — a deck compresses; this is where a technical investor checks whether the compression hid anything. It is written to be read adversarially, which is why the risks section is the longest and the traction section is one paragraph admitting there is none.
> **How to read it** — §6 first if you are deciding; §2 first if you are curious. A skeptic should attack §5, the recombination argument, which is where a pack of this kind usually overreaches.
> **Depends on / feeds** — arranges [../research/](../research/), [../strategy/](../strategy/), [../product/](../product/), [../tech/](../tech/); no number here originates in this file. Feeds [pitch_deck.md](pitch_deck.md), `financials/comps_exits.md`.

## 1 · Thesis

Everyone building AI service desks is competing on resolution quality. That is the wrong axis: resolution is nearly commoditised, and the binding constraint on deployment is that the system must be **told** what the environment is. For an MSP with 41 client environments, that telling costs 25–40 engineer-hours per client [S21] and recurs forever.

Understudy acquires environment knowledge by **observation** rather than configuration. The claim is not that it resolves tickets better. It is that it **arrives already knowing**, and that each environment it learns makes the next one cheaper — which turns a per-client cost into a compounding asset.

The bet is one research problem: whether recorded sessions cluster into skills that transfer between environments. Everything else is engineering.

## 2 · Why existing approaches are structurally insufficient

**Task mining and process discovery** — UiPath, Celonis, and FortressIQ before its acquisition. These record employee work at enterprise scale and it works: FortressIQ claimed ~90% reduction in discovery time [S7]. **Their output is a document.** A human then builds the automation, and the automation they built was RPA, whose measured record is 30–50% of projects failing to meet expectations with maintenance reaching **60% of total implementation cost** [S10][S11]. Discovery was never the weak link; the executor was.

**AI-native service desks** — Ravenna ($15M, Apr 2025), Atomicwork ($25M Series A, Jan 2025), Aisera ($164.5M), Espressive ($53M) [S2][S12][S13]. Genuinely agentic execution, and the right instinct about the mid-market. **But the environment is still described to them** — a visual workflow builder is configuration with a better surface, and it requires the knowledge to already be explicit in someone's head. Their resolution claims (35–60% deflection, −70% ticket volume) are vendor-published and independently unverified; no third-party benchmark of autonomous IT resolution exists.

**ServiceNow** — ~$160B, and it bought Moveworks for **$2.85B** in the category's defining transaction [S26]. It cannot attack this problem without attacking itself: implementation runs **3–5× the annual licence** [S20]. Self-onboarding cannibalises the services revenue that is the larger half of the deal. Its own lead investor in this space describes the platform as "completely inappropriate" below enterprise [S3].

**Agentic browsers** — Strawberry ($6M, Oct 2025) [S25] learns workflows by use and executes directly. Browser-only, and most IT administration is not in a browser.

**The structural reading:** three of four quadrants of the market are crowded. The fourth — *knowledge acquired by observation, executed directly* — was empty because acting on an observed procedure required an executor that could work a real UI. That arrived within the last eighteen months.

## 3 · Architecture

Six components, in the order they run. Full diagrams in [../tech/architecture/](../tech/architecture/).

1. **Capture** — screen, input and application context across RMM consoles, AD, terminals and MDM, with credentials dropped at capture before storage, and 10-second narration prompts at detected branch points. Narration is the direct attack on the problem that sank fifty years of programming-by-demonstration: a demonstration underdetermines intent.
2. **Stage-1 distillation, inside the MSP's own tenant** — clustering across that MSP's 41 environments using sequence alignment over typed actions, not an LLM. Deterministic and inspectable, so the core bet is falsifiable.
3. **Skill synthesis** — emits `SKILL.md` with a **goal-state success criterion**. A skill for which no independently checkable criterion can be derived is rejected rather than shipped.
4. **Envelope abstraction** — the only artifact that reaches us: `{procedure_shape, precondition_pattern, deviation_class, observation_count}`, whitelist-constructed, released only once a pattern is observed in **≥3 distinct tenants**. Raw recordings never leave the MSP's control.
5. **Governed execution** — action classified by blast radius; destructive always gated, non-negotiably; every action under the agent's own directory principal so the client's audit log attributes it without our help.
6. **Verify and re-ground** — every action checked against its criterion; a changed interface triggers a bounded, read-only search against the intact goal, and any re-grounded run is demoted to gated so a human sees it.

## 4 · Concrete operating examples

**A ticket at a client the technician has never touched.** MFA re-enrolment at a 22-person client. The desk surfaces the procedure *and the two ways this tenant differs* — including that a Conditional Access policy requiring a compliant device blocks registration, which two engineers previously resolved with a Temporary Access Pass rather than by weakening the policy. Nobody told her that. Two engineers hit it months apart and the system kept what they did. When the situation then leaves the skill's envelope, the agent stops and escalates rather than improvising.

**An incident, because they happen.** A gated skill correctly removes a mailbox forwarding rule that turns out to be a deliberate executive exception documented nowhere. Verification passed — **the system was not wrong about what it did, only about whether to do it, and no success criterion catches that.** It was reverted in 40 seconds because the undo path was recorded before the mutation; the client's IT owner was told the same day; the ticket was not billed, because a resolution a human reverses within the ticket's life does not bill. **This class of error is not eliminable, only survivable**, and a memo claiming otherwise would be lying.

## 5 · Why this can win

**The recombination.** Capture that keeps failures, feeding clustering that keeps variance, producing skills that declare success, which makes verification possible, which makes re-grounding possible, which makes deviations widen the envelope. Every component exists somewhere. **No one has the circuit**, and breaking any link degrades it to something that already exists.

**The moat, stated narrowly enough to survive.** The happy-path procedure for Entra or M365 is authorable from vendor documentation — **that half of the library is copyable in a quarter, and we say so.** What is not copyable is the observed distribution of how those procedures differ across dozens of real tenants, how they fail, and how engineers verify them. Vendors document the intended path, not the forty ways a real tenant deviates from it. That accrues only from deployments — and one MSP customer contributes 41 environments where an internal-IT customer contributes one. **It remains an assumption (A8), not a finding.**

**Why not Ravenna in a quarter.** They can add recording; it is a product decision, not a business-model conflict. What they cannot compress is environment coverage, and their customer shape yields one environment each. On our own corrected schedule a funded incumbent is **ahead on raw environment count today** — we overtake on density, not on speed, at roughly quarters 8–10.

## 6 · Honest risks

*The full twelve-row matrix with likelihoods, leading indicators and residual levels is in [../financials/risk_matrix.md](../financials/risk_matrix.md). Five below; four residuals there stay **high** and one has no mitigation at all.*

1. **The core mechanism is unevidenced.** Cross-session clustering into reliable skills has no benchmark and no named prior system. ALLOY demonstrates the adjacent claim at user-study scale; nothing demonstrates it across environments. **A negative result is possible and there is no partial credit.** *Mitigation: the evaluation harness is built before the clusterer, and the falsifying number — below ~70% on a held-out environment — is declared in advance.*
2. **Where a real API exists, we are the wrong tool.** Driving an API beats driving a UI on speed, cost and stability. The durable value of capture concentrates in surfaces that lack good APIs — native admin consoles, terminals, legacy tooling — and as vendors ship better APIs that surface shrinks. *Mitigation: prefer APIs wherever they exist rather than defend UI automation on principle. This is a real limit on the mechanism and we would rather state it than have it found.*
3. **The market is a wedge, not a category.** SAM is ~$179M at current pricing, after a banding correction that cut it from $215M. Venture scale requires either capturing more of the labour value we displace — $6 captures about a quarter of the $22.50 blended cost per ticket [S27][S28] — or the internal-IT expansion, which is a fight on an axis we have chosen to avoid. *Mitigation: none yet. This is the honest ceiling.*
4. **Adoption fails from inside, quietly.** The expert whose cooperation capture requires is the one best equipped to reject it — **disuse**, in the human-factors taxonomy [S36], is a documented failure mode. It looks like slow adoption and no dashboard shows it. *Mitigation: attribution, correction rights and rejection without justification, designed in rather than messaged.*
5. **Schedule.** ~40-week build floor for a solo founder; first paid pilot at month 12 **only if every item lands at its optimistic bound**. *Mitigation: none. It is the single point of failure and it is named.*

## 6b · What the ticket half actually sells

**This is stated here rather than left for a buyer to derive, because it is derivable in one conversation.**

Our per-ticket price is $6. The tickets we address are the cheapest quartile of an MSP queue by construction, and a junior technician clears them at `(assumption: $2–6 each)` — a figure `validation/experiment_board.md` E8 exists to establish. **So on the ticket half we are plausibly at or above the customer's own marginal cost, and the savings argument is not available.**

The argument that *is* available is capacity. An MSP at its staffing ceiling cannot convert marginal cost into marginal output — **26% of them report being unable to staff clients they could otherwise win** [S33], and the alternative to us is a hire they have already failed to make. What we sell on that half is throughput and coverage at the ceiling, not a cheaper unit.

**Three consequences we accept rather than argue around:**
1. The per-ticket line will not survive a buyer who has spare capacity. Those are not our customers.
2. It caps price capture: `financials/comps_exits.md`'s "capture more of the labour value" path is weaker than it first appears, because the labour value on this subset is small.
3. **The onboarding half carries the economics**, and its own basis is unresolved — the fee is priced above the hours it displaces at every band, and E3 is reframed to test whether the library has value independent of hours at all (D17).

## 7 · Traction

**There is none.** No pilot, no customer, no measured result, no code. Design partners are not yet signed. Every operating figure in this pack is a declared target with its source or `(assumption)` tag attached, and the artifacts state where the numbers would be falsified. **A memo that manufactured traction here would be the strongest evidence against everything else in it.**
