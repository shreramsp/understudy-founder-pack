# Founder story

> **What this is** — the founder-market-fit narrative in first person, usable verbatim in applications, warm intros and the site's about page.
> **Why it exists** — the pack's honest position is that the founder has deep AI/agents engineering background and **no managed-services operating history** (A6). A founder story that obscured that would be discovered in the first reference call; one that states it and shows what is being done about it is a stronger artifact than a manufactured origin.
> **How to read it** — the third section is the one an investor is actually testing. A skeptic should ask whether the gap named there is genuinely being closed or merely acknowledged.
> **Depends on / feeds** — inherits [../BRIEF.md](../BRIEF.md) §Founder edge and assumption A6; feeds [one_pager.md](one_pager.md), [pitch_deck.md](pitch_deck.md) slide 13, `startup-website`.

---

## Why this problem

I kept meeting the same failure from the other side of it.

Agents got genuinely good at doing multi-step work in real interfaces over the last eighteen months — not perfect, but past a threshold that did not exist in 2023. And every time I looked at where that capability was being pointed, it was pointed at *execution*: better resolution, better deflection, better throughput. Meanwhile the thing actually stopping deployment was that somebody still had to sit down and tell the system what the environment was.

That is a strange place for the industry's attention to be. The hard part was never the doing. It was the knowing.

## What I know that most people working on this do not

**The clustering problem is the company, and it is not an LLM problem.**

The instinct — mine included, at first — is to hand a pile of recordings to a frontier model and ask it to produce a procedure. That works well enough to demo and badly enough to be unfalsifiable: when it fails you cannot tell whether the representation was wrong, the alignment was wrong, or the model simply had a bad day.

So the design does the opposite. Actions are typed into a semantic representation; clustering runs on classical sequence alignment and profile HMMs — methods that are decades old, deterministic and debuggable. The model is used where it is genuinely better than an algorithm: understanding what a click *meant*, and synthesising readable prose. **That choice makes the core bet falsifiable, which is worth more to me than making it look impressive.**

The second thing: what accumulates is not the procedure. Any competent engineer can write the Entra MFA re-enrolment procedure from Microsoft's own documentation. What nobody has written down is how that procedure *differs* across forty real tenants — which conditional access policy blocks it where, what the failure looks like, how an engineer confirms it actually worked. That distribution is the asset, and it exists only where someone watched.

## The gap, and what I am doing about it

**I have not run a managed services business.** I have not felt the specific pain of onboarding a client at 2am because the contract starts Monday, and I am not going to pretend otherwise in a room with someone who has.

That gap is real and it is the reason the plan starts with ten conversations and no product pitch, why the first hire is an MSP-side operator rather than an engineer, and why the design partners are being asked for their timesheets rather than their enthusiasm. The mechanism is my ground. The market is not yet, and the fastest way to make it so is to be corrected early and often by people who live in it.

I would rather present a pack whose weakest assumption is labelled than one whose weakest assumption is load-bearing and hidden.

## Why I will still be here in ten years

Because the honest version of this problem is a long one. The literature has been circling *learning a procedure by watching someone perform it* for forty years and has not closed it; task mining industrialised the watching and stopped at a document; RPA industrialised the doing and stopped at a script that breaks. The piece that was missing arrived recently enough that almost nobody has built on it yet.

If the transfer result comes back negative, I will publish that too. It is the most useful thing I could contribute to a field that has been assuming this works for four decades without measuring it.
