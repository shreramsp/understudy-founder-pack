# Survey: learning executable procedures from observed work — 2026-09-04

> **What this is** — a dated mini survey of the science and engineering behind turning observed human work into machine-executable procedure, from 1980s programming-by-demonstration to 2026 computer-use agents.
> **Why it exists** — the whitepaper, the PRD and the VC memo all rest on one scientific claim: that watching work is a sufficient basis for doing it. This is the file those artifacts cite, and it is where the evidence *against* that claim is recorded so the pack argues with the objection rather than around it.
> **How to read it** — §5 (evidence for) and §6 (evidence against) are the load-bearing sections; read them as a pair. A skeptic should attack §5's reliance on a single user study.
> **Depends on / feeds** — cites [sources.md](sources.md); feeds `tech/whitepaper.md`, `tech/deep_dives.md`, `product/PRD.md`, `narrative/vc_memo.md`.

## Abstract

Converting observed human work into executable automation is a forty-year-old research programme with a poor industrial record. Programming by demonstration produced compelling laboratory systems that generalized badly; process and task mining industrialized the *observation* half at enterprise scale but terminated in documents; robotic process automation industrialized the *execution* half but on brittle, hand-authored scripts that fail in 30–50% of projects and consume up to 60% of their cost in maintenance [S10][S11]. Since 2024 three capabilities have arrived together — multimodal agents that operate real UIs, methods that synthesize reusable workflows from demonstrations, and an open portable format for procedural knowledge — which for the first time permit an observation-to-execution loop with no human transcription step. The evidence that this loop works is real but thin: one peer-reviewed system (ALLOY) validated at user-study scale [S22], against a benchmark record showing that the same agents scoring 85% on standard tasks fail approximately 80% of real workflows [S15] and complete 20.6% of long-horizon ones [S16]. The open question is not whether a procedure can be learned from a demonstration, but whether procedures learned in one environment transfer to another — which is unaddressed in the literature and is the commercial crux.

## 1. Classical foundations

**Programming by demonstration (PbD).** The founding idea: a user performs a task once and the system infers a general program. The persistent failure is generalization — inferring which parts of the demonstration are essential and which are incidental to that run. Systems worked in constrained domains and degraded sharply outside them. Understudy inherits this problem exactly, with one modern advantage: a language model can be asked *why* a step was taken, and the brief's spoken-reasoning capture is a direct attack on the incidental-vs-essential problem that sank classical PbD.

**Process mining.** Reconstructs the real process from system event logs rather than from what anyone believes happens. Mature, enterprise-standard, and structurally limited: it sees what systems record. IT support work is thinly logged and happens largely *between* transactions [S8].

**Task mining.** The desktop-level answer to that limit — capture clicks, keystrokes and screens directly [S8][S9]. FortressIQ built a company on it with computer vision from 2017 and was acquired into an RPA vendor in December 2021 [S5][S6][S7]. This is the closest historical analogue to Understudy and its most instructive one.

**RPA.** The executor that discovery fed for a decade. Its measured record is the strongest available evidence about what happens to automation derived from observed work: **30–50% of projects fail to meet expectations** [S10]; bots break on UI change; **maintenance reaches 60% of total implementation cost** [S11]. Any claim that Understudy's skills will be durable must explain why they are not RPA scripts with a language model in front.

## 2. Taxonomy of approaches

| Class | Acquires knowledge by | Produces | Representative |
|---|---|---|---|
| Log-based mining | System event logs | Process model | Celonis |
| Desktop task mining | Screen/click capture | Task diagram, automation candidates | UiPath Task Mining, FortressIQ |
| Hand-authored automation | Human encoding | Executable script/bot | RPA, RMM scripts |
| Configured agentic | Human encoding in a builder | Executing agent | Ravenna, Atomicwork, Moveworks |
| **Demonstration-to-workflow** | **Observed work** | **Executable, reusable workflow** | **ALLOY [S22]; Understudy** |
| Instructed agentic | Natural-language instruction at run time | Ephemeral execution | Frontier computer-use agents |

The last-but-one row is the only one that closes observation to execution without a human transcription step, and until 2024 it had no viable executor.

## 3. Enabling technology (see [capability_table.md](capability_table.md))

Three arrivals define the window: computer-use agents moving 12% → 85% on OSWorld between April 2024 and June 2026 [S14][S15]; demonstration-to-workflow synthesis demonstrated in ALLOY [S22] and screen-video pretraining in VideoAgentTrek [S23]; and `SKILL.md` becoming an open, cross-vendor standard for procedural knowledge, Apache 2.0, adopted by 26+ platforms [S24]. Inference cost for fixed capability continues to fall roughly 10× per year [S30], making bulk processing of recorded sessions economically trivial relative to the engineer-hours it replaces.

## 4. Evaluation methods and benchmarks

- **OSWorld / OSWorld-Verified** — the standard computer-use benchmark; leaderboard at 86.1% as of 2026-09-02 [S14].
- **OSWorld 2.0** — long-horizon variant, median task 1.6 human-hours; best system 20.6% [S16]. The more honest proxy for a real IT ticket.
- **No benchmark exists** for procedure clustering, for cross-environment skill transfer, or for autonomous IT ticket resolution. Every resolution-rate figure in this market is vendor-published [S1][S2]. **A company whose core claim has no benchmark should build one** — an internal, published evaluation harness is both a credibility asset and a genuine moat component.

## 5. Evidence *for* the core mechanism

1. **ALLOY** demonstrates the exact loop — demonstration in, reusable generalizable workflow out — and beat both prompt-based agents and manual workflow construction on intent capture and generalization [S22].
2. **VideoAgentTrek** shows unlabeled screen recordings carry enough signal to improve computer-use capability without manual annotation [S23], supporting the economics of bulk capture.
3. **Task mining's commercial history** proves the organizational half: enterprises do permit recording of employee work at scale, and FortressIQ's claimed ~90% reduction in discovery time [S7] indicates the observation step genuinely compresses.
4. **The executor is real now.** 85% on OSWorld is not nothing, and the specific class of IT work Understudy starts with — repetitive tier-1 procedures on familiar consoles — sits at the easy end of that distribution.
5. **A portable landing format exists** [S24], so a learned procedure is inspectable text an engineer can read, correct and own — which is also the answer to RPA's opacity problem.

## 6. Evidence *against* — read this before believing §5

1. **Benchmark-to-reality gap.** Agents at 85% on OSWorld fail ~80% of real workflows [S15]. Benchmarks are curated; client environments are not.
2. **Long-horizon collapse.** 20.6% on OSWorld 2.0 [S16]. Real tickets are long-horizon.
3. **RPA's record is the base rate.** Automation derived from observed work has failed 30–50% of the time with maintenance at 60% of cost [S10][S11]. The burden is on Understudy to explain what is structurally different, and "we use an LLM" is not that explanation — brittleness came from environment drift, which LLMs mitigate but do not eliminate.
4. **PbD's generalization problem is unsolved, not bypassed.** Fifty years of it.
5. **No published evidence of cross-environment transfer** — the single most load-bearing commercial assumption (A8) has no support in the literature either way.
6. **The historical analogue was absorbed.** FortressIQ's outcome was a $ ​trade sale into an RPA vendor and product invisibility [S5][S6], not an independent category win.

## 6b. Human–automation trust — the literature the adoption argument rests on

The product's adoption case (readable skills, correction rights, gated actions) is a **trust-calibration** argument, and that field has forty years of results the pack must not reinvent:

- **Lee & See (2004), "Trust in Automation: Designing for Appropriate Reliance."** The goal is not maximal trust but *calibrated* trust — reliance matched to actual capability. Both over-trust and under-trust are failures. Transparency about how a system works, and about its limits, is the primary calibration mechanism. [S35]
- **Parasuraman & Riley (1997), "Humans and Automation: Use, Misuse, Disuse, Abuse."** Names the failure modes directly: **misuse** (over-reliance on an unreliable system), **disuse** (rejecting a system that would have helped — which is what Ray does if beat 12 goes wrong), and **abuse** (deploying automation without regard to the human's resulting role). [S36]
- **Automation bias and complacency.** Operators under-verify automated recommendations, especially when the system is usually right — which is precisely the condition a skill library with a high success rate creates. Verification that a human performs *because the system asked* degrades over time.

**What this implies for the product, beyond what the pack already says:**

1. **A high success rate is a hazard as well as an asset.** The 14:20-class error (verified action, wrong decision) is exactly where automation bias bites: an approver who has clicked through 200 correct proposals reads the 201st less carefully. Approval-surface design must fight the habituation it creates.
2. **Disuse is the more likely failure here than misuse**, because the expert whose cooperation the capture programme needs is the one most equipped to reject it (`P8`).
3. **Calibration, not confidence.** This is the research reason the product shows an envelope ("seen in 6 tenants, 3 variants") rather than a confidence score: a number invites reliance it cannot justify.

## 7. Risks the science implies

- **Happy-path capture.** A recording captures what one engineer did once; failure branches, aborted attempts and recovery behaviour are exactly what is *not* demonstrated, and exactly what production requires.
- **Silent wrongness.** A skill that executes cleanly and does the wrong thing is worse than one that fails loudly. IT actions are frequently destructive and often irreversible. **Automation bias makes this worse over time**, not better: the more reliable the system, the less carefully each approval is read [S35][S36].
- **Drift.** Client environments change continuously; a skill library is a maintenance liability from the day it is written — the precise mechanism that made RPA maintenance 60% of cost [S11].
- **Regulatory.** Continuous screen recording of employees is treated as disproportionate under EU data-protection practice, consent is a weak legal basis given the employer–employee power imbalance, and works councils hold co-determination rights in Germany, the Netherlands, Austria and Sweden [S29]. This constrains the capture step in the EU specifically and belongs in the risk matrix, not in a footnote.

## 8. Open questions

1. **Does a skill learned in environment A execute correctly in environment B?** No literature. The commercial crux (A8).
2. **How many demonstrations does one reliable skill require?** Unknown; determines the cost and duration of onboarding, and therefore the entire unit-economics model.
3. **Can failure branches be learned from happy-path recordings**, or must they be elicited separately?
4. **What is the decay rate of a skill** as an environment drifts, and can drift be detected before an action goes wrong?
5. **Is there a defensible evaluation of autonomous IT resolution** that a buyer would accept — and does building it constitute the moat?
