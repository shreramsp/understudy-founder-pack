# Journey — edge-high: Ray is convinced, then genuinely stretched

> **What this is** — the elite user's journey: a 19-year principal engineer who has cleaned up after two failed RPA programmes, moving from active scepticism to authorship, and then to work he could not do before.
> **Why it exists** — Ray can veto adoption without attending a single meeting, by quietly not cooperating with capture [strategy/sales_roadmap.md](../../strategy/sales_roadmap.md). He is also the source of the highest-value skills in the library. A product that bores or threatens him fails twice: no data in, and a credible internal voice saying it is RPA again.
> **How to read it** — beats 1–4 are conversion, 5–8 are the stretch. A skeptic should attack beat 3, where a single wrong skill would have ended the deployment.
> **Depends on / feeds** — inherits [PRD.md](../PRD.md) `P3 P6 P7 P8`, personas §4, the D5 contract-vs-goal argument; feeds `tech/whitepaper.md`, `narrative/vc_memo.md`.

**Persona.** Ray Kowalczyk, 19 years, principal escalation engineer. Holds environment knowledge for the 8 most complex clients. Interrupted ~14 times a day.
**Session goal (his, not ours).** Establish whether this system is going to make production worse.

---

## Conversion

**Day 1 — he does not attend the kickoff.** He reads the capture agent's docs instead, and checks two things: whether it captures keystrokes into password fields (it does not — **N4 sensitive-value redaction** drops them at capture, before storage) and whether he can stop it (he can — **N11**, indicator and pause).
→ *Record:* nothing. **That is the point: he verified before contributing.**

**Day 3 — the narration prompt earns its place.** Mid-session he picks the second of two AD groups. A prompt: *why that one?* He says: *"Because the first one syncs to their billing system and finance owns that."* Nine seconds.
→ *Component:* **N10 decision-point narration** (`P1`).
→ *Record:* the rationale attached to that branch — **the piece of information no amount of screen capture would have recovered.**

**Day 12 — the beat that converts him.** He opens a skill built from his own session. Not a flowchart: text, with a goal, a success test, and his reasoning quoted where the branch happens. He finds one thing wrong — a precondition too broad — and fixes it in place.
→ *Component:* **N12 skill viewer**, **X19 skill correction UI**, **N13 authorship attribution** (`P6 P8`).
→ *Record:* skill v2, edit credited to Ray.
**A skeptic should attack here.** If that first skill had been subtly wrong in a way he could not see, or presented as a black box he could not edit, this deployment ends on day 12 and no later feature recovers it. **`P6` is not a UI preference; it is the adoption gate.**

**Day 20 — the RPA objection, answered by mechanism.** He asks the question he has been saving: *"What happens when Okta redesigns their admin console? Because that's what killed the last two."*
The answer he is shown is not a promise. It is the E2 result: skills executed against a deliberately altered UI — moved, renamed, re-ordered elements plus a version upgrade that changed selectors — beside a **selector-based** RPA baseline on the identical alteration.
→ *Component:* **N8 evaluation harness**, **X11 re-grounding on change** (`P3 P4`, D5).
→ *The mechanism, stated as he would state it:* an RPA step is a contract against a specific build with no success criterion, so a break halts or proceeds wrongly. A skill carries a goal and a verification step, so a break becomes a re-grounding search against an intact criterion.
**He is not convinced by the argument. He is convinced that the argument is testable, and that the baseline was not rigged.**

## The stretch

**Week 5 — interruptions fall, and the ones remaining are better.** Tier-1 stops asking him things the library now answers. What reaches him is genuinely novel.
→ *Component:* **X17 global stack layer**, **L11 escalation routing** (routes by who authored the relevant skills).
→ *Record:* his interruption count and its composition — the metric he judges the product on.

**Week 7 — he starts using it as an instrument.** A client's intermittent authentication failure. Ray asks the library a question it was not designed for: *which of my 41 environments have this conditional-access pattern?*
→ *Component:* **X17** + **N9 variance envelope** queried across environments — patterns only, no client data crossing boundaries (D6).
→ *Record:* a cross-environment query. **This is Ray using the variance envelope as a diagnostic, which is not a feature anyone specified.** It is what having the distribution rather than the modal path makes possible (`P7`).

**Week 9 — he authors deliberately.** He performs a gnarly Exchange hybrid migration procedure *knowing* it will be captured, and narrates as he goes. He is no longer a subject; he is writing the manual by doing his job.
→ *Component:* **N1**, **N10**, **N6**, **N13**.
→ *Record:* the most valuable skill in the library, attributed to him.
**`P8` has flipped.** Capture stopped being surveillance and became authorship, and the mechanism was attribution plus the ability to correct — not messaging.

**Week 14 — drift catches something he would have missed.** A skill's verification rate degrades over three days. The system pauses it and flags a change in a client's tenant that nobody had announced.
→ *Component:* **X12 drift detection**, **X4 success-criterion verification** (`P4 P9`).
→ *Record:* paused skill, drift signal, the tenant change identified.
**This is the beat where he stops testing it and starts relying on it:** it told him about a production change before a user did.

---

## What Ray got, and what the company got

| | Ray | The company |
|---|---|---|
| Week 1 | verified it could not harm him | nothing — correctly |
| Week 3 | his reasoning captured in 9-second increments | the rationale screen capture cannot recover (`P1`) |
| Week 12 | a skill he corrected and owns | the endorsement that makes capture sustainable (`P8`) |
| Week 20 | an evidence-backed answer to his RPA objection | the argument that survives diligence (D5) |
| Week 5–14 | fewer, better interruptions; a cross-environment diagnostic | the highest-value skills in the library, and the variance envelope proven useful to a human |

## The failure mode this journey exists to prevent

Reverse beats 3 and 4 — show him a black box, answer his RPA question with a slogan — and Ray tells the team channel it is RPA with a chatbot on it. He would be listened to, because he cleaned up the last two. **Capture then degrades quietly: sessions get paused, narration stops, and the library learns only the easy procedures.** No dashboard shows this failure; it looks like slow adoption. It is the single most likely way this product dies inside a customer that has already paid.

**Recommended next:** run beat 4 before the first pilot, not during it. The E2 result and a selector-based baseline are cheap to produce on lab environments and they are the artifact that converts this persona — [strategy/sales_roadmap.md](../../strategy/sales_roadmap.md) step 4 already gates the deal on it.
