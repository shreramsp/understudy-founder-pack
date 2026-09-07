# Understudy — one page

> **What this is** — the single page an investor or design partner reads first: problem, mechanism, why now, evidence, market, team, ask.
> **Why it exists** — every longer artifact in this pack assumes a reader who already wants to know more. This is the page that decides whether they do. It also carries the pack's two binding honesty constraints (D8, D10) rather than deferring them to a memo nobody reaches.
> **How to read it** — every sentence is load-bearing; nothing here is unsupported by an artifact elsewhere in the pack. A skeptic should attack "Evidence", which is the shortest section because the company is pre-build.
> **Depends on / feeds** — arranges [../strategy/positioning.md](../strategy/positioning.md), [../research/](../research/), [../tech/whitepaper.md](../tech/whitepaper.md), [../strategy/market_sizing.md](../strategy/market_sizing.md); feeds [pitch_deck.md](pitch_deck.md), `startup-website`.

**Understudy is the AI service desk that learns each client environment by watching engineers work.** For MSPs, where onboarding a new client is recurring cost of goods rather than a one-time project.

---

**The problem.** Every AI service desk can resolve a ticket. None can learn an unfamiliar environment without being configured by hand. For an MSP that configuration is not a setup cost — it is cost of goods, paid again for every client. Onboarding a median client runs **25–40 engineer-hours** before a ticket is billed [S21], and **26% of MSPs say they cannot staff the clients they could otherwise win** [S33]. The knowledge that would make automation work is performed daily and captured nowhere.

**Why nobody has closed this.** The market split the problem in half. Discovery tools — task mining, FortressIQ, UiPath — **record work and emit a diagram a human must implement**. Resolution tools — Ravenna, Atomicwork, Moveworks — **execute, but must be told how**. Both halves are mature. The handoff between them is manual, and that is where the hours go. It stayed open for a structural reason: until agents could act on a real UI, a recording had nowhere to go but someone's to-do list. FortressIQ was recording employees with computer vision in 2017 and was acquired into an RPA vendor in December 2021 — right input, wrong decade.

**The mechanism.** Record engineers working (screen, actions, spoken reasoning at decision points). Cluster the recordings into a readable `SKILL.md` library, each skill carrying a **goal-state success criterion**. Rehearse in shadow against live tickets. Execute under approval gates, verifying every action against its criterion. **Supervised throughout — never unattended.**

**Why now.** Computer-use agents moved from 12% to ~86% on OSWorld between April 2024 and September 2026 [S14][S15], and `SKILL.md` became an open cross-vendor standard adopted by 26+ platforms [S24]. A recorded procedure now has both an executor and a portable place to live. Neither existed in 2019.

**Why it is not RPA.** RPA's checks assert things about **the interface** — that a control exists in a state. So a broken selector halts loudly or proceeds wrongly, and neither recovers. A skill's criterion states the **goal**, so a changed interface becomes a re-grounding search against an intact target. That is a difference in failure mode, and it is tested in `validation/experiment_board.md` E2 against a **selector-based** RPA baseline, not a strawman.

**Evidence.** Pre-build, and the pack says so. What exists: the mechanism is validated at user-study scale in the literature (ALLOY, arXiv 2510.10049), the enabling capability is measured [S14][S16], and the market pain is sourced [S21][S33]. **What does not exist: any pilot, any customer, any measured result.** Every operating figure in this pack is a declared target, not a measurement.

**What we are actually selling on the ticket half — and it is not savings.** The tickets we automate are the cheapest quartile of an MSP's queue by construction: password and MFA resets, mailbox permissions, provisioning, printer queues, RMM-alert remediation with documented fixes. A junior technician clears those at `(assumption: $2–6 each)`. **At $6 per resolved ticket we are at or above their marginal cost.** What we sell is not a cheaper ticket — it is **throughput at a capacity ceiling**: 26% of MSPs say they cannot staff the clients they could otherwise win [S33], and the alternative to us is a hire they have already failed to make. We would rather state that than have a buyer work it out from their own numbers.

**What we deliberately do not claim.**
- **Not unattended autonomy.** Long-horizon agent completion is 20.6% [S16]; supervision is architecture, not a phase we remove.
- **Not faster first onboarding — it is slower.** Environment 1 costs 31–46 hours against a 25–40 baseline, because the work is unchanged and review is added. Compression begins at environment 2 (18–28 hours). **We waive the fee on environment 1** rather than charge for a loss.
- **Not a universal mechanism.** Where a real API exists, using it beats driving a UI on speed, cost and stability. The durable value of capture concentrates in surfaces that *lack* good APIs — native admin consoles, terminals, legacy tooling — and we would rather name that than have a reviewer find it.

**Market.** ~45,000 US MSPs, ~12,000 in the serviceable 10–100-employee band [S31]. **SAM ≈ $179M/yr** at a two-part tariff (~$6/resolved ticket plus a banded per-environment fee of $400/$1,500/$1,500), against a US managed-services market of $120–140B [S31]. Steady-state ~$14,930/yr per MSP. **This is a wedge, not the whole market** — internal IT is roughly $288M more and this pack does not claim it, because entering it means competing on resolution quality, the axis we have chosen to avoid.

**Team.** Solo founder, AI/agents engineering background. Founder-market fit is argued on the mechanism — the clustering-and-synthesis core is the hard bet and it is the founder's ground — not on managed-services operating history, which is a stated gap (A6).

**The ask.** Pre-seed to reach one number: **do skills synthesized in environment A execute correctly in environment B?** Below ~70% on a held-out set, the company is materially smaller and we will say so. The evaluation harness is built before the clusterer, so the answer arrives as evidence rather than as the opinion of the person who built it.
