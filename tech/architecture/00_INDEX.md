# Architecture index

> **What this is** — the ten diagrams that define Understudy's system design, each a Mermaid source document with a caption saying what a reviewer should notice.
> **Why it exists** — the pack's central architectural claim (D6: raw recordings never reach the vendor) is only checkable if the boundary is drawn explicitly in every view. These diagrams exist so a security reviewer and an engineer can disagree with the same picture.
> **How to read it** — D06 first if you are evaluating the privacy claim; D01 first if you are evaluating the mechanism. A skeptic should attack D04, where the three-layer schema either does or does not keep tenant identity out of the global layer.
> **Depends on / feeds** — inherits [../whitepaper.md](../whitepaper.md), [../deep_dives.md](../deep_dives.md), [../../product/PRD.md](../../product/PRD.md) §7 and the settled D6; feeds [../not_vaporware.md](../not_vaporware.md), `visuals/`, `narrative/vc_memo.md`.

| # | Diagram | What it settles |
|---|---|---|
| [D01](D01.md) | Capture-to-skill pipeline | How a recording becomes an executable skill, and where each stage runs |
| [D02](D02.md) | The closed loop | Watch → Distil → Rehearse → Gate → Act → Verify → Learn as a circuit, with what breaks if a link is cut |
| [D03](D03.md) | Execution orchestration | What actually runs when a skill fires against a ticket |
| [D04](D04.md) | Three-layer library schema | What each layer holds and what may cross between them |
| [D05](D05.md) | Inference routing and cost control | Which model runs where, and why the expensive half runs at the edge |
| [D06](D06.md) | The two-stage boundary | **The privacy architecture. The diagram the security review is about** |
| [D07](D07.md) | Integration surface | PSA, RMM, IdP and admin-plane touchpoints |
| [D08](D08.md) | Verification, drift and evaluation | How the system knows it is still right |
| [D09](D09.md) | Node fleet across MSPs | Multi-tenant scale, and the operational obligation D6 creates |
| [D10](D10.md) | Human-in-the-loop and escalation | Every path by which a decision reaches a person |

**One convention across all ten:** anything inside a `MSP tenant` boundary never leaves it in raw form. If a diagram shows an arrow crossing that line, the arrow is labelled with exactly what it carries.
