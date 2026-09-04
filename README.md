# Understudy — founder artifact pack

**Understudy is the AI service desk that onboards itself.** It records IT engineers doing real work, clusters those recordings into an executable skill library, and takes over tickets stack by stack — deploying into an unfamiliar client environment in days rather than the months of manual configuration every other AI service desk requires. Beachhead: MSPs, where onboarding a new client environment is cost of goods rather than a one-time project.

**Status:** `PARTIAL` · generated 2026-09-04 · run slug `self-onboarding-desk` · **18/61 required artifacts · 0 visuals** · phases 0–1 complete; phase 2 written and revised through critic round 1, **gate not yet passed**.

## Start here

1. [BRIEF.md](BRIEF.md) — the single source of truth: problem, beachhead, mechanism, moat, riskiest assumption.
2. [research/landscape.md](research/landscape.md) — why the wedge is narrower and better than the brief claimed: everyone records, nobody executes.
3. [research/capability_table.md](research/capability_table.md) — the nine capabilities the loop needs, and the two that are not yet strong enough.
4. [ASSUMPTIONS.md](ASSUMPTIONS.md) — what the founder confirmed vs. what was decided for them, and which decisions are load-bearing.

## Artifact map

| Path | What it holds | Files | Owning skill |
|---|---|---|---|
| `BRIEF.md` | founder brief | 1 | grill-me |
| `ASSUMPTIONS.md` | assumptions log | 1 | grill-me |
| [`research/`](research/) | evidence layer — landscape, competitors, capability table, survey, 30 sources | 5 | startup-research |
| [`strategy/`](strategy/) | market type, positioning, bottom-up sizing, personas, canvases, GTM, petal, channel economics, sales roadmap | 11 | startup-strategy |
| `product/` | PRD, features, journeys, UX spec | 0 | startup-product |
| `tech/` | whitepaper, deep dives, architecture, technique waves | 0 | startup-tech |
| `narrative/` | one-pager, VC memo, deck, press release, founder story | 0 | startup-narrative |
| `validation/` | Blank board set | 0 | startup-validation |
| `financials/` | pricing, revenue build, unit economics, risks, comps | 0 | startup-financials |
| `visuals/` | manifest, infographics, image prompts | 0 | startup-visuals |
| `audit/` | coverage audit | 0 | startup-audit |

## Sharpest claims so far

1. **The market has split the loop in half and left the join manual.** Discovery tools record work and hand a human a diagram; resolution tools execute but must be configured by hand. Both halves are mature; the handoff is where the months go. [S5][S8][S10] — [landscape.md](research/landscape.md)
2. **Deployment friction is the incumbent's revenue, not its defect.** ServiceNow implementation runs 3–5× the annual licence and 6–12 months for an enterprise rollout, which is a structural inhibition on it ever self-onboarding. [S20] — [competitors.md](research/competitors.md)
3. **The executor is newly good enough to be interesting and not yet good enough to be trusted.** 86.1% on OSWorld-Verified, but ~80% of real workflows still fail and long-horizon completion is 20.6%. [S14][S15][S16] — [capability_table.md](research/capability_table.md)
4. **The clustering step — the company's core bet — has no benchmark and no named prior system.** That is the risk and the opportunity in one line. [capability_table.md](research/capability_table.md) row 5
5. **This was tried before, at the wrong time.** FortressIQ recorded employees with computer vision from 2017 and was acquired into an RPA vendor in Dec 2021 — it could observe, but had no executor to send the result to. [S5][S6][S7]

## Completeness

`PARTIAL` — phases 0–1 of 10. The brief and the full evidence layer exist: 30 sources, 18 live searches, and four marked gaps where the search found nothing (no global MSP census, no independent deflection benchmark, no public competitor pricing, no post-acquisition record for FortressIQ). Eight product, nine tech, six narrative, nine validation and six financial artifacts remain, plus visuals, audit and site. Next: critic round 2 on the strategy layer, then `startup-product`. Row-by-row status will live in `audit/COVERAGE.md` once the audit phase runs.
