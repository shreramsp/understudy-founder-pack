# Flagship features — the 20 that carry the product

> **What this is** — the twenty highest-leverage features, each stated as name → mechanism → the principle it obeys → **the visible product moment**, meaning what a user literally sees.
> **Why it exists** — feature lists drift into adjectives, and adjectives cannot be built or falsified. The "visible moment" column is the discipline: if a feature has no moment, it is infrastructure, and if it maps to no principle in [PRD.md](PRD.md) §4 it should not exist.
> **How to read it** — F1–F4 are the company; F13–F16 are the trust surface that decides adoption. A skeptic should attack F2, which has no benchmark in the literature to inherit.
> **Depends on / feeds** — inherits [PRD.md](PRD.md); feeds [features_prioritized.md](features_prioritized.md), [journeys/](journeys/), [ux_spec.md](ux_spec.md), `tech/deep_dives.md`, `visuals/`.

## Watch — capture what is actually happening

**F1 · Multi-surface session capture** · *Mechanism:* OS-level capture of screen, input events and application/window context across RMM consoles, AD, terminals, MDM and native admin tools. · `P1` · **Moment:** Priya starts her shift, sees a small capture indicator in the tray, and works normally. Nothing else changes about her day.

**F2 · Decision-point narration** · *Mechanism:* detects branch points — a choice between two paths, an unusual value entered, a step skipped — and prompts for ten seconds of voice at that moment rather than asking for continuous commentary. · `P1 P8` · **Moment:** Ray picks the second of two AD groups; a quiet prompt asks "why that one?"; he says nine words and keeps going.

**F3 · Failure and abort retention** · *Mechanism:* sessions that ended in escalation or rollback are retained and labelled, because recovery behaviour appears nowhere in successful runs. · `P2` · **Moment:** a ticket Priya escalates is marked "kept — this is the useful kind", which is also the first time failing has felt productive.

**F4 · Engineer capture controls** · *Mechanism:* visible indicator, one-click pause, and a post-session review screen before anything is distilled. · `P8` · **Moment:** Ray pauses capture to open his password manager, and the timeline shows a gap he does not have to explain.

## Distil — turn sessions into skills

**F5 · Cross-session clustering** · *Mechanism:* groups recordings of the same procedure across engineers and environments, separating the invariant procedure from environment-specific detail. · `P1 P7` · **Moment:** twelve recordings of MFA re-enrolment collapse into one skill with three named variants. **This is the company's core bet and has no benchmark in the literature to inherit [capability_table row 5].**

**F6 · Skill synthesis with a declared success criterion** · *Mechanism:* emits `SKILL.md` carrying goal, preconditions, steps, **a test for "done correctly"**, and an escalation envelope. · `P3 P6` · **Moment:** the skill opens with "Succeeds when: the user can complete an MFA challenge from a new device" — the line an RPA script never had.

**F7 · Variance envelope extraction** · *Mechanism:* records how the same procedure differed across environments and keeps the distribution, not just the modal path. · `P7` · **Moment:** a skill shows "observed in 14 environments · 3 variants · 2 known deviations" — the asset made visible.

**F8 · Authorship attribution** · *Mechanism:* every skill names the engineers whose sessions produced it, and shows them their contribution. · `P8` · **Moment:** Ray's name is on the escalation skill the whole team now uses, which is the difference between being mined and being credited.

## Rehearse — earn trust before acting

**F9 · Shadow mode** · *Mechanism:* the skill runs against live tickets without acting; its intended actions are compared with what the human actually did. · `P5 P9` · **Moment:** a weekly digest: "would have matched you on 34 of 40 tickets" — with the six disagreements listed first.

**F10 · Deviation report** · *Mechanism:* every divergence is routed to the authoring engineer as a specific question, not a metric. · `P2 P6` · **Moment:** "On ticket 8812 I would have reset the token; you rebuilt the profile. Which is right?" — and the answer becomes part of the skill.

**F11 · Promotion ladder** · *Mechanism:* a skill moves shadow → gated → **supervised** only on evidence thresholds declared in advance, per action class. Naming matters: there is no autonomous rung, per the binding claim boundary (D1). · `P5 P9` · **Moment:** Dana sees a skill at "gated — 2 more clean weeks to promote", and can hold it there indefinitely.

## Gate and Act — do the work, safely

**F12 · Action-class policy** · *Mechanism:* read / reversible-write / destructive, with destructive gated regardless of confidence and **not configurable to off**. · `P9` · **Moment:** a mailbox deletion stops with "needs your approval" and a one-line summary of exactly what will happen.

**F13 · Agent identity** · *Mechanism:* the agent holds its own principal in the client's IdP, so every action is attributable in the client's own audit log. · `P8 P9` · **Moment:** Sonia opens her audit log and sees a named non-human principal, not a shared admin account.

**F14 · Envelope enforcement** · *Mechanism:* an action outside the skill's declared preconditions escalates instead of improvising. · `P5` · **Moment:** "This tenant has conditional access I haven't seen before — routing to Ray."

**F15 · Test-account self-exploration** · *Mechanism:* bounded, read-only-by-default discovery of the environment beyond what was recorded. · `P1 P4` · **Moment:** the agent maps a tenant's group structure overnight and reports what differs from the twelve it already knows.

## Verify and Learn — the part RPA never had

**F16 · Success-criterion verification** · *Mechanism:* every action ends by testing its declared criterion; a passing action is one that was *checked*, not one that did not error. · `P3 P9` · **Moment:** "Reset complete — verified by signing in as the test principal."

**F17 · Re-grounding on change** · *Mechanism:* when the interface moves, the agent searches against the intact goal rather than halting on a broken step. · `P3 P4` · **Moment:** an Okta redesign ships overnight; the skill logs "control moved, re-grounded, verified" instead of a queue of failures. **This is the D5 claim made visible, and E2 is its test.**

**F18 · Drift detection** · *Mechanism:* a skill whose verification rate degrades flags before it acts wrongly. · `P4 P9` · **Moment:** "This skill's checks have failed twice this week — paused pending review."

**F19 · Envelope widening** · *Mechanism:* every deviation, escalation and correction updates the variance envelope, so the library gets more robust rather than merely larger. · `P4 P7` · **Moment:** a skill's variant count goes from 3 to 4 after an unusual tenant, and the fourth is credited to the engineer who handled it.

**F20 · Onboarding meter** · *Mechanism:* measures engineer-hours consumed and time-to-first-verified-skill per environment, compared against **that client's own size band** (15–25 / 25–40 / 40–80 hours, D7) rather than a book average. · `P4` — the metric exists because a library's value decays and has to be re-evidenced · **Moment:** Marcus opens one screen: *"Client 42 (median band, baseline 25–40): 14 hours to a maintained runbook."* `(illustrative: target, not measured — no pilot exists)` **The number the entire go-to-market is built on** [strategy/gtm.md](../strategy/gtm.md).

## Why the power is the loop, not any feature

Every one of these exists elsewhere in some form. Task mining has F1 [S8]. Agentic desks have F12 and F13 [S1]. RPA has a weak F17. **What no one has is the circuit:** capture that keeps failures (F3) feeding clustering that keeps variance (F5, F7), producing skills that declare success (F6) so that verification (F16) is possible, so that re-grounding (F17) is possible, so that deviations (F10) widen the envelope (F19) and the next environment starts warmer.

Break any link and it degrades to something that already exists. Without F6's success criterion, F16 cannot verify and F17 cannot re-ground — and the product is RPA with better parsing, which is the exact objection Ray raises and D5 answers. Without F3 and F10, the library learns only happy paths and P2 kills it in month three. Without F8's attribution, P8 fails, capture quietly degrades, and there is no input at all.

**The integration is the product. The features are how it is built.**

**Recommended next 3:** (1) F1, F3, F5, F6 — capture with failures, clustering, skills that declare success. Nothing else matters until F5 works; (2) F9 shadow mode before any Act feature, because it is how trust is bought and it cannot hurt anything; (3) F20 early, because the metric it produces is the go-to-market.
