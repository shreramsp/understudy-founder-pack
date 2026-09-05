# Customer discovery guide

> **What this is** — the interview kit: screening criteria per persona, non-leading problem-interview questions, a solution-interview script, and the synthesis template.
> **Why it exists** — the pack's single most valuable unknown (MSP ticket mix, onboarding hours by client size) is answerable in ten conversations and by nothing else. This file exists so those conversations produce data rather than encouragement.
> **How to read it** — the question set is Mom-Test disciplined: every question asks about the **past**, never about a hypothetical future. A skeptic should check that no question below could be answered "yes, that sounds useful".
> **Depends on / feeds** — inherits [../strategy/personas.md](../strategy/personas.md), [experiment_board.md](experiment_board.md) E3/E8; feeds [pivot_log.md](pivot_log.md), `strategy/market_sizing.md` (rows 6, 8, 13).

## Screening

| Persona | Include if | Exclude if |
|---|---|---|
| **Marcus** — MSP owner/COO | 10–100 staff · ≥8 client environments · US · owner is reachable | Single-client MSP; pure staff-aug; >200 staff (different buying process) |
| **Dana** — service delivery manager | Owns the queue and the onboarding checklist | Title only, no queue ownership |
| **Ray** — principal/escalation engineer | ≥10 years · holds environment knowledge for named clients | Generalist without deep client-specific knowledge |
| **Sonia** — client-side IT director | Approves what their MSP deploys in their environment | No approval authority |

## Problem interview — 14 questions, all about the past

**Never describe the product before question 12.**

**Onboarding**
1. Walk me through the last client you onboarded. What happened in week one?
2. How many engineer-hours did it take? Who tracked that?
3. Was that typical? What made it more or less than usual?
4. What did you have at the end that you didn't have at the start? *(listening for: documentation, or knowledge in someone's head)*
5. When did that client's documentation last get updated? By whom?

**The knowledge problem**
6. Tell me about the last time someone on your team escalated something a colleague had already solved elsewhere.
7. Who on your team knows the most about your hardest client? What happens when they're on holiday?
8. Has anyone left in the last two years who took environment knowledge with them? What did that cost?

**Volume and mix**
9. Roughly how many tickets a month across the book? *(E8)*
10. If you sorted last month's tickets by category, what would the top five be, and roughly what share? *(E8 — the pack's single highest-value unknown)*
11. What share arrive from RMM alerts rather than from a person?

**Constraint**
12. Have you turned down a client in the last year? Why?
13. What would you have to be true to take on 20% more clients without hiring?
14. What have you already tried to fix this? What happened?

## Solution interview — only after the problem is confirmed unprompted

15. *(Show the positioning statement, once.)* What do you think this does?
16. What would have to be true for you to try it?
17. *(Show the banded fee, framed "first environment free".)* What's your reaction to that number? *(E3)*
18. Who else would have to agree before you could sign?
19. What would your client's IT contact ask you about it? *(E7 — the veto persona, surfaced through the buyer)*
20. What would make you stop using it after three months?

## Questions we deliberately do not ask

- *"Would you use a system that learns your environment by watching engineers?"* — hypothetical, and everyone says yes.
- *"How much would you pay for this?"* — invites an invented number. Ask what they pay for the thing today (Q2) and put a price in front of them (Q17) instead.
- *"Does documentation going stale bother you?"* — leading. Q5 gets the same information from behaviour.
- Anything that pitches. **If the interviewer is talking for more than a quarter of the call, the data is contaminated.**

## Synthesis template — filled after each interview, within the hour

```
Interview #  · Persona · Firm size · Environments · Date
Top 3 pains, in their words (verbatim quotes, not paraphrase):
Current workaround:
Trigger that would make them act:
Onboarding hours quoted:            (Q2)  → feeds market_sizing row 13
Ticket volume + top 5 categories:   (Q10) → feeds market_sizing rows 6, 8
Price reaction:                     (Q17) → feeds E3
Objection that must be overcome:
Surprise finding (anything that contradicted the pack):
Did they mention onboarding cost unprompted before Q12?   Y / N
```

**That last line is the pack's exit criterion.** [../strategy/gtm.md](../strategy/gtm.md) requires ≥6 of 10 to rank onboarding in their top three pains *unprompted*. Recording it per interview is what keeps that from being decided retrospectively by whoever wants the answer to be yes.

**Recommended next 3:** (1) run all ten before writing a line of marketing copy; (2) treat Q10 as the priority question — it is worth more to the model than any other single answer; (3) log every surprise finding in [pivot_log.md](pivot_log.md) the same day, because contradictory evidence decays fastest.
