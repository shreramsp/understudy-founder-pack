# Competitor teardown

> **What this is** — a teardown of every system competing for the budget Understudy wants, including the two that are not products: doing nothing, and the dominant manual workaround.
> **Why it exists** — positioning is chosen against a map, and the founder's map had three names on it. This file replaces it with a sourced one, and locates the axes that actually divide the space so `strategy/positioning.md` picks a quadrant rather than a slogan.
> **How to read it** — the table is the evidence; the positioning read below it is the argument. A skeptic should attack the claim that the two axes named here are the ones buyers actually decide on.
> **Depends on / feeds** — cites [sources.md](sources.md) and [landscape.md](landscape.md); feeds `strategy/positioning.md`, `strategy/petal_diagram.md`, `narrative/vc_memo.md`, `financials/comps_exits.md`.

## The teardown

| Competitor | Segment | Mechanism | Pricing | Funding / stage | Traction signal | Where it wins | Where it fails *mechanistically* |
|---|---|---|---|---|---|---|---|
| **Ravenna** [S1][S2][S3] | Mid-market internal IT, Slack-first | Agentic ITSM; customer-authored visual workflows executing across connected tools | Not public (quote) | $15M pre-seed+seed, Apr 2025 (Madrona, Khosla) | Design partners Futureverse, Homebase, Zapier | Genuinely agentic execution; adoption where work already lives | **The environment is still described to it.** A workflow builder is configuration with a nicer surface — the knowledge must already be explicit in someone's head |
| **Atomicwork** [S12] | Enterprise + mid-market IT | "No ticket" agentic resolution in Slack/Teams | Not public | $25M Series A Jan 2025; $40.3M total | Khosla-backed, enterprise logos | Funding depth, enterprise motion | Same: configured, not taught |
| **Moveworks / ServiceNow** [S26] | Enterprise (5k+) | AI assistant + enterprise search, now inside the platform of record | Enterprise contract | Acquired **$2.85B**, closed Dec 2025 | ~5M employee users; ~250 mutual customers | Distribution through the incumbent; the category's exit proof | Enterprise-shaped; **consolidation vacated the independent mid-market**, and ServiceNow's economics depend on configuration revenue |
| **Aisera / Espressive** [S13] | Enterprise ITSM/ESM | Conversational deflection + workflow automation | Not public | $164.5M / $53M raised | Long customer lists | Incumbency in the prior generation | Deflection-era architecture; heavy services to deploy |
| **ServiceNow (direct)** [S3][S20] | Enterprise | Platform of record; configuration is the product | $150–300+/fulfiller/mo; implementation **3–5× license** | ~$160B public co. | Category default | **Deployment friction is its revenue, not its defect.** Structurally cannot attack its own services economics — and per its own lead investor, "completely inappropriate" below enterprise [S3] |
| **UiPath Task Mining / Celonis** [S8][S9] | Enterprise process teams | Record desktop or mine logs → process maps → automation candidates | Enterprise | Public / late-stage | Enterprise-proven discovery | **Output is a diagram.** The executor it feeds is RPA, which fails 30–50% of projects with maintenance at up to 60% of cost [S10][S11] |
| **FortressIQ** [S5][S6][S7] | — (absorbed) | Computer vision over employee work → process intelligence | — | Acquired Dec 2021 | — | Proved recording knowledge work is feasible at enterprise scale | **The historical warning.** Same input, no executor available in 2021; the output was analysis, and it ended as a feature inside an RPA vendor |
| **Strawberry** [S25] | Prosumer / SMB knowledge work | Agentic browser companions that learn workflows by use | Not public | $6M, Oct 2025 (General Catalyst, EQT) | Launched product | Learns from the user, executes directly | **Browser-only** — most IT work is RMM consoles, AD, terminals, MDM, native admin UIs |
| **"Do nothing"** [S21] | — | Engineers absorb onboarding as billable project work | 40–80 engineer-hours/client | — | Universal | Zero adoption risk; already budgeted | Cost recurs per client forever; knowledge stays in heads and leaves with them |
| **Documentation + scripts (IT Glue/Hudu + RMM)** | The real workaround | Humans write the environment down; engineers script the top tasks | Bundled in MSP stack | — | Near-universal at MSPs | Cheap, familiar, no procurement | **Passive artifacts.** Documentation does not execute, and is stale the week after it is written |

## Positioning read

**The two axes that actually divide this space are not price and quality.** From the teardown, every system takes a position on:

1. **How the system acquires environment knowledge** — *configured by a human* (Ravenna, Atomicwork, Aisera, ServiceNow) vs. *observed from work being done* (FortressIQ, UiPath Task Mining, Strawberry, Understudy).
2. **What the system does with that knowledge** — *produces an artifact for a human* (task mining, documentation platforms) vs. *executes it directly* (AI service desks, agentic browsers).

Placing everything on those axes:

```
                      EXECUTES DIRECTLY
                              |
   Ravenna · Atomicwork       |        [ open quadrant ]
   Aisera · ServiceNow        |         Understudy
   Moveworks                  |         (Strawberry, browser-only,
                              |          sits at the boundary)
  CONFIGURED ────────────────-+──────────────── OBSERVED
   BY A HUMAN                 |                 FROM WORK
                              |
   IT Glue · Hudu             |        FortressIQ
   runbooks                   |        UiPath Task Mining · Celonis
                              |
                    PRODUCES AN ARTIFACT
```

**The white space is the observed × executes quadrant, and it is empty for a reason that has expired.** Three of the four quadrants are crowded. The fourth required an executor reliable enough to act on an observed procedure, which did not exist until computer-use agents crossed their threshold [S14][S15] and skills got a portable format [S24]. Strawberry is the only company approaching it, from the browser, at $6M.

**Positioning statement (draft, for `strategy/positioning.md` to sharpen):** *For MSPs onboarding client environments, Understudy is the only service desk that learns the environment by watching engineers work — because a recorded session becomes an executable skill, not a diagram someone still has to implement.*

## What the incumbents do about it

- **ServiceNow** buys rather than builds in this category and has just spent $2.85B doing so [S26]. It could add discovery — but its services economics run on configuration [S20], and a serious self-onboarding capability cannibalizes the implementation revenue that is 3–5× its license line. That is a real structural inhibition, not wishful thinking, though it is not permanent.
- **Ravenna and Atomicwork** are the genuine threat: same buyer instinct, real funding, and adding recording-based discovery is a product decision rather than a business-model conflict. **Understudy's defensibility cannot be the idea; it has to be the skill library that compounds** (A8) and the MSP-specific motion the internal-IT-focused players are not running.
- **UiPath** owns discovery and has every reason to point it at a modern executor. Its constraint is that its executor is RPA and its buyer is the enterprise process team, not IT service delivery.
