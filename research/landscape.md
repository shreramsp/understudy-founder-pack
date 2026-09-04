# Landscape — every approach to learning an IT environment

> **What this is** — a survey of every existing way a system comes to know how work is done in an unfamiliar IT environment, ordered from nearest to Understudy's mechanism (record → cluster → execute) to farthest.
> **Why it exists** — the brief claims deployment friction is an unsolved bottleneck. That claim is only worth building on if nobody has solved it, and *"nobody does discovery"* turns out to be wrong: an entire category has recorded employees since 2017. This file establishes what the real, narrower gap is, so the wedge is defended rather than assumed.
> **How to read it** — read tier 1 first; it is the uncomfortable one. A skeptic should attack the claim that the record→execute handoff is genuinely open rather than merely unbranded.
> **Depends on / feeds** — cites [sources.md](sources.md); feeds [competitors.md](competitors.md), `strategy/positioning.md`, `tech/whitepaper.md`, `narrative/vc_memo.md`.

## The finding that reframes the wedge

The founder brief states that no AI service desk can learn an environment without months of configuration, implying discovery is unattempted. **It is not.** Recording employees at work to discover their processes is a mature category — *task mining* / *process discovery* — with a decade of products and at least one acquisition of a company built on exactly this premise.

What no one has done is **close the loop.** The market has cleanly split Understudy's mechanism in half:

- **Discovery tools record work and hand a diagram to a human**, who then builds the automation by hand. The output is a document.
- **Resolution tools execute work but must be told how**, by a human configuring them. The input is a document.

Both halves exist. The handoff between them is manual, and it is where the months go. That — not "nobody does discovery" — is the defensible gap, and it is a stronger claim because it explains *why* the gap persisted: until agents could execute a UI workflow directly, a recording had nowhere to go but a human's to-do list.

## Tier 1 — Process discovery by recording (nearest mechanism, different output)

| System | Mechanism | Strengths | Measured limits | Gap it leaves |
|---|---|---|---|---|
| **FortressIQ** (2017; acquired by Automation Anywhere Dec 2021 [S5][S6]) | Computer vision over employee screen activity → "Virtual Process Analyst" process maps | The original proof that recording knowledge work at scale is technically and organizationally possible; claimed ~90% reduction in discovery time [S7] | Output was *analysis*, not execution — a map for humans to act on. Absorbed into an RPA platform and no longer independently visible [S5] | The recording was never converted into something that could run |
| **UiPath Task Mining** [S8][S9] | Desktop capture of clicks and keystrokes → task-flow diagrams → candidates for RPA | Native path from discovery into UiPath Studio; enterprise-proven | Produces automation *candidates*; a human still builds each bot. Scoped as time-boxed projects, not continuous | Same handoff — diagram to human to bot |
| **Celonis** [S8] | Process mining from system transaction logs rather than the desktop | Sees the whole cross-system process; strong where ERP logs are rich | Blind to work that happens *between* system transactions — which is where IT support lives | Log-shaped, not screen-shaped; IT ticket work leaves thin logs |

**Why this tier's output could not become execution.** The automation these tools fed was RPA, and RPA's record is poor on exactly this axis: **30–50% of projects fail to meet expectations** [S10], bots are brittle against UI change, and **maintenance runs up to 60% of total implementation cost** [S11]. Discovery worked; the executor it fed was the weak link. That is the specific thing that changed.

## Tier 2 — AI-native service desks (same buyer, opposite half of the loop)

| System | Mechanism | Strengths | Measured limits | Gap it leaves |
|---|---|---|---|---|
| **Ravenna** ($15M seed, Apr 2025) [S1][S2][S3] | Slack-native agentic ITSM; visual workflow builder; agents execute across connected tools | Genuinely agentic execution (e.g. Okta password reset end to end); fast to adopt where Slack is the workplace | Workflows are **authored by the customer** in a builder. Resolution claims (35–60%, −70% tickets) are vendor-published and unverified [S1][S2] | Someone still has to know and encode the environment |
| **Atomicwork** ($25M Series A, Jan 2025; $40.3M total) [S12] | "No ticket" agentic model — resolve in Slack/Teams, create a record only on escalation | Well-funded, enterprise-credible, same anti-ServiceNow thesis | Same premise: the agent is configured, not taught | Same |
| **Moveworks** (acquired by ServiceNow $2.85B, closed Dec 2025) [S26] | Enterprise AI assistant over IT/HR, now inside the incumbent | ~5M employee users; the category's proof of value and its exit comp | Enterprise-scale deployment; now bound to ServiceNow's motion | Consolidation removes the independent mid-market option |
| **Aisera** ($164.5M), **Espressive** ($53M) [S13] | AI service management across IT/HR/support | Deep funding, long customer lists | Prior-generation conversational deflection; heavy configuration | Same |
| **ServiceNow** [S3][S20] | Platform of record; configuration *is* the product | Owns the enterprise; ~$160B company | Implementation costs **3–5× annual license**, 6–12 months for enterprise rollout, $150k–450k services even for SMB ITSM [S20] | Deployment friction is not a bug here — it is the business model |

## Tier 3 — Agentic executors that learn from the user

| System | Mechanism | Limits | Gap |
|---|---|---|---|
| **Strawberry** ($6M, Oct 2025, General Catalyst + EQT) [S25] | Agentic browser; "companions" perform multi-step tasks by clicking and typing, learning user workflows over time | **Browser-only.** IT work spans RMM consoles, AD, terminals, MDM, native admin tools | Confirms the founder's read; the surface is the constraint |
| Generic computer-use agents (frontier models) | Execute UI workflows from natural-language instruction | No persistence of what was learned; no library; no attribution | Execution without accumulation |

## Tier 4 — Research systems (the mechanism, unproductized)

- **ALLOY** (arXiv 2510.10049) [S22] — generates **reusable agent workflows from demonstrations of computer use**, letting users externalize procedural knowledge by doing it once and generalizing it via natural language. In a user study it beat prompt-based agents and manual workflows on intent capture and generalization. This is Understudy's core loop, demonstrated in a lab.
- **VideoAgentTrek** (arXiv 2510.19488) [S23] — treats unlabeled screen video as a training signal for computer-use agents, removing the manual-annotation bottleneck in turning recordings into capability.

**Read:** the mechanism is academically live and validated at study scale, and not yet owned by a product. That is the most encouraging finding in this layer — and also a warning that the idea is visible to everyone reading the same papers.

## Tier 5 — Classical and manual (what MSPs actually do today)

| Approach | Why it persists | Where it fails |
|---|---|---|
| Documentation platforms (IT Glue, Hudu-class) | Structured home for client environment knowledge | Written by hand, stale on arrival, and **passive** — nothing executes them |
| RMM/PSA scripting | Real automation for known, repetitive tasks | Written per client per task; the long tail is never worth the engineer-hours |
| Runbooks and tribal knowledge | Free, immediate, matches reality | Lives in 3 engineers' heads; leaves when they do; **the direct competitor for this company's budget** |
| Onboarding as a services project | Billable, understood | **4–6 weeks and 40–80 engineer-hours per client** [S21], paid before a ticket is deflected |

## Tier 6 — Emerging hybrid (the opening)

Two things landed within roughly 18 months of each other: computer-use agents crossed from 12% to ~85% on OSWorld [S14][S15], and `SKILL.md` became a **cross-vendor open standard** adopted by 26+ platforms [S24]. Together they mean a recorded procedure now has both an executor and a portable, auditable place to live. Neither existed when FortressIQ was recording employees in 2019.

**The honest counterweight, stated here rather than buried:** the same source reporting 85% on OSWorld also reports that these agents **fail roughly 80% of real workflows** [S15], and on the long-horizon OSWorld 2.0 the best frontier system completes **20.6%** [S16]. The executor is newly good enough to be interesting and not yet good enough to be trusted unattended — which is precisely why the brief's four-phase ladder (simulate → govern → autonomous) is the right shape and why phase 4 cannot be promised on a near-term roadmap.
