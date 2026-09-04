# UX specification — the twelve screens that carry the product

> **What this is** — the key screens: purpose, primary action, information hierarchy, empty/loading/error states, and the micro-interactions that carry the product's feel. Text spec only; visual collages belong to `visuals/`.
> **Why it exists** — this product asks people to be recorded, and asks a sceptical expert to endorse what was learned from them. Those are interface problems before they are model problems: S4 and S5 decide whether capture keeps flowing, and no amount of clustering quality compensates if they are wrong. The spec exists so the consent and inspection surfaces get designed rather than inherited from an admin template.
> **How to read it** — S4 and S5 first; they are the adoption gates. A skeptic should attack the empty states, which is where a product that has learned nothing yet has to still be worth opening.
> **Depends on / feeds** — inherits [PRD.md](PRD.md), [features_flagship.md](features_flagship.md), [journeys/](journeys/); feeds `visuals/` (UX collages), `tech/`, `startup-website`.

**Cross-cutting rules.** Skills render as **text, never as flowcharts** (`P6`). Every number is monospaced and traceable to the session or action that produced it. Destructive actions are visually distinct everywhere they appear and can never be bulk-approved. Nothing in the product manufactures urgency: most days the correct action is none.

---

## S1 · Environment dashboard — Dana's ten minutes

**Purpose.** One client environment's state at a glance. **Primary action:** review what changed since yesterday.
**Hierarchy:** skills live / in shadow / paused → deviations awaiting judgement → onboarding meter → recent actions.
**States.** *Empty (week 1):* "Capture running. 14 sessions recorded, no skills yet — distillation runs at the end of week 1." **This is the honest empty state the beachhead journey requires**, and it must say what happens next and when, not "no data". *Loading:* skeleton rows, never a spinner over the whole page. *Error:* if the in-boundary node is unreachable, say which node and since when — silence here reads as data loss.
**Micro-interactions.** Paused skills sort to the top and stay until acknowledged. Counts animate only when they change during the session, so a changed number is noticed without the page feeling busy.

## S2 · Owner summary — Marcus's 90 seconds a week

**Purpose.** Is the number still true? **Primary action:** none — this screen is read, not operated.
**Hierarchy:** hours saved this month → environments onboarded → **the two worst-performing environments, shown before the best**.
**States.** *Empty:* "First environment onboards in ~3 weeks. This screen fills then." *Error:* never show a partial total; show nothing and say why.
**Micro-interactions.** Every figure expands one level to the environments composing it, and no further — an owner who wants the third level should be talking to Dana.
**Rule:** if a month is worse than baseline, this screen leads with it. A dashboard that only reports wins is distrusted permanently the first time a client reports a problem first.

## S3 · Ticket-side skill panel — Priya's ambient surface

**Purpose.** Offer what is known about *this* client for *this* ticket. **Primary action:** read the procedure, then optionally *run with me*.
**Hierarchy:** matched skill + confidence → **the deviations specific to this environment** → steps → run controls.
**States.** *Empty:* "No skill for this yet — your session will be captured and may become one." *Ambiguous match:* offer up to three, never auto-select. *Error:* fall back to showing nothing rather than a generic runbook; a wrong-client procedure is worse than none.
**Micro-interactions.** The panel never steals focus or blocks the ticket. Deviations are the visually loudest element, because they are the part no runbook would have told her.

## S4 · Capture control and session review — the consent surface `P8`

**Purpose.** The engineer sees, controls and reviews what was captured. **Primary action:** pause, or approve a session for distillation.
**Hierarchy:** capture state → today's segmented sessions → what was redacted → pause.
**States.** *Paused:* unmistakable, persistent, with no nagging to resume. *Redaction summary:* "3 credential fields dropped at capture" — shown routinely, because trust is built by visible refusals rather than by a policy page.
**Micro-interactions.** One click to pause; **resuming is also one click and is never automatic**. A session can be deleted before distillation with no justification required and no notification to a manager.
**This screen is load-bearing.** If it feels like surveillance, capture degrades quietly and the failure looks like slow adoption — the most likely way this product dies inside a paying customer [journeys/edge_high.md](journeys/edge_high.md).

## S5 · Skill viewer — the demo that converts Ray

**Purpose.** Show exactly what the system believes it learned. **Primary action:** endorse, or correct.
**Hierarchy:** goal → **success criterion** → preconditions → steps → variants observed → contributing sessions and authors.
**States.** *Low-confidence skill:* labelled as a draft with the number of sessions behind it. *Single-session skill:* explicitly marked — one demonstration is an anecdote, not a procedure (`P2`).
**Micro-interactions.** Every step links to the session moment it came from, playable. Narration appears as quoted text beside the branch it explains, attributed. **Nothing on this screen is a black box, and nothing renders as a flowchart** — text is the format an expert can argue with (`P6`).

## S6 · Skill correction — being told no

**Purpose.** The authoring engineer changes what is wrong. **Primary action:** edit and commit, or reject the skill outright.
**Hierarchy:** the edit → what it affects → who else authored this.
**States.** *Conflicting edits:* both are shown to both engineers; the system does not adjudicate whose method is right (`L10` handles this at scale).
**Micro-interactions.** **Rejection requires no justification.** A system that argues with the expert it learned from will not be fed honestly next time — and the rejection is recorded as a finding, not as an error.

## S7 · Approval prompt — the gated action

**Purpose.** A human decides on a mutating action. **Primary action:** approve or decline.
**Hierarchy:** **one line of plain-language effect** → reversibility → scope → the skill and its version.
**States.** *Destructive:* distinct treatment, never batchable, never remembered as a default. *Timeout:* expires rather than proceeding.
**Micro-interactions.** The effect line names the actual object — *"removes forwarding from j.okafor@ to an external address"* — not the operation class. **The 14:20 incident in [journeys/day_in_life.md](journeys/day_in_life.md) turned on whether a human could evaluate that sentence in two seconds.** No "approve all".

## S8 · Deviation review — where the library learns

**Purpose.** Turn disagreements into corrections. **Primary action:** answer the question.
**Hierarchy:** what the skill would have done vs. what the human did → the ticket → *which is right?*
**States.** *Empty:* "No disagreements this week" — a legitimately good outcome, not a barren screen.
**Micro-interactions.** Framed as a question to the engineer, never as an accuracy score against them. Three outcomes, all first-class: the skill was wrong, the human was wrong, or both were valid and the envelope widens.

## S9 · Onboarding progress — what the fee is charged for

**Purpose.** Track a new environment from capture to live skills. **Primary action:** none; it reports.
**Hierarchy:** engineer-hours consumed → time-to-first-verified-skill → skills by stage → **hours against this client's size band** (D7).
**States.** *Week 1:* explicitly "watching — no skills yet by design", so silence is not read as failure.
**Micro-interactions.** The baseline comparison uses *this client's size band*, not the book average — the pricing correction that critic round 2 forced applies to the UI too.

## S10 · Boundary and egress attestation — Sonia's screen

**Purpose.** Show what leaves the environment. **Primary action:** export.
**Hierarchy:** raw recordings — **never leave, stated first** → what the envelope contains → what crossed, itemised → retention state.
**States.** *Error:* if egress filtering is degraded, the system stops distillation rather than continuing and reporting later.
**Micro-interactions.** One export, complete, no configuration. She needs one file, twice a year, and for it to be boring [journeys/day_in_life.md](journeys/day_in_life.md).

## S11 · Promotion ladder — adoption at the customer's pace

**Purpose.** Move a skill shadow → gated → supervised, on declared evidence. **Primary action:** promote, or leave it.
**Hierarchy:** current rung → evidence for the next → what promotion changes in practice.
**Micro-interactions.** Thresholds are declared before results exist and are visible. **A skill can sit at gated forever with no nagging** — the product does not lobby for its own autonomy.

## S12 · Drift alert — the trust-building interruption

**Purpose.** Surface a skill whose verification is degrading, before it acts wrongly. **Primary action:** review and pause, or accept the change.
**Hierarchy:** what changed → since when → which environments → what has been paused already.
**Micro-interactions.** The system pauses first and asks second. **This is the screen that converts a sceptic into a user** — it told Ray about a production change before a user did [journeys/edge_high.md](journeys/edge_high.md) — so it must never fire spuriously; a false drift alert costs more trust than a missed one.

---

## Screens deliberately not built

- **A chat interface.** The product's surface is the ticket and the skill, not a conversation. A chat box invites the unbounded requests `P5` says we cannot serve.
- **A confidence score on every action.** A number implies calibration we cannot demonstrate; the envelope either covers the situation or it does not (`X9`).
- **An autonomy toggle.** Excluded by the claim boundary (D1) — not a setting we have chosen to withhold.
- **A leaderboard of engineer contributions.** `P8` requires attribution, not competition; ranking the people being recorded is the fastest route to gamed capture.

**Recommended next 3:** (1) prototype S5 and S6 before any dashboard — they are the adoption gates and they can be tested on lab-generated skills with no customer; (2) write S7's effect-line generator as a first-class component, since the 14:20 incident turns on one sentence being readable in two seconds; (3) design the S1 and S9 empty states properly — the product spends its entire first week having produced nothing, and that week is when the buyer decides whether they were sold something real.
