# Understudy — founder artifact pack

> **Masters coursework.** This founder-artifact pack was generated with the **startup-skills** pipeline ([dlmastery/startup-skills](https://github.com/dlmastery/startup-skills), MIT licensed) — the pipeline supplied the method; the idea, the 18 founder decisions and the resulting analysis are this project's own.
> **Not a funded company.** No customers, no code, no traction. Every figure here is a declared target carrying its source or an `(assumption)` tag.


**Understudy is the AI service desk that learns each client environment by watching engineers work.** It records IT engineers doing real work, clusters those recordings into a readable, executable skill library, and takes over tier-1 tickets under supervision — for MSPs, where onboarding a new client environment is recurring cost of goods rather than a one-time project. Every AI service desk can resolve a ticket; none can learn where it is.

**Status:** `PARTIAL` · generated 2026-09-04 · run slug `self-onboarding-desk` · **59/61 required artifacts · 20 HTML infographics · a 5-page site and a 70-document reader · 0 rendered images** · 103 files. Two manifest rows are open and **four of eight generated layers have never been through the critic loop** — see [Completeness](#completeness).

---

## Open this first

**[`pack.html`](pack.html)** — the whole pack as a browsable reader. All 70 documents, sidebar-navigable and searchable, Mermaid diagrams drawn, every cross-reference clickable. **Every document is embedded, so it opens from a double-click with no server.**

**[`index.html`](index.html)** — the five-page site built from the pack: [product](product.html), [evidence](evidence.html), [pricing](pricing.html), [about](about.html).

## Start here — 60 seconds

1. **[narrative/one_pager.md](narrative/one_pager.md)** — the whole company on one page, including the three things it deliberately does not claim.
2. **[narrative/pitch_deck.md](narrative/pitch_deck.md)** — fourteen slides. Slides 10, 11 and 12 are the limits, and they are not optional.
3. **[tech/whitepaper.md](tech/whitepaper.md)** — where the leverage actually is, and why there is no 10×.

## Reading paths by audience

**Investor** — [one_pager](narrative/one_pager.md) → [vc_memo](narrative/vc_memo.md) (the risks section is the longest, deliberately) → [market_sizing](strategy/market_sizing.md) (the arithmetic, corrected three times, with the corrections kept visible) → [revenue_build](financials/revenue_build.md) (73% of three-year revenue is one-time) → [comps_exits](financials/comps_exits.md) (this is not a generational company on the wedge alone, and the file says so).

**Engineer** — [whitepaper](tech/whitepaper.md) §5 (the RPA argument, corrected three times) → [deep_dives](tech/deep_dives.md) (DD1 is the only research bet) → [architecture/D06](tech/architecture/D06.md) (the privacy boundary the security review is about) → [not_vaporware](tech/not_vaporware.md) (what ships this quarter and what does not).

**Operator** — [PRD](product/PRD.md) → [features_prioritized](product/features_prioritized.md) (the build math that does not close, stated) → [journeys/day_in_life](product/journeys/day_in_life.md) (an incident at 14:20 that verification cannot catch) → [ux_spec](product/ux_spec.md).

**Practitioner / MSP** — [journeys/edge_low](product/journeys/edge_low.md) (a technician at a client she has never touched) → [journeys/beachhead](product/journeys/beachhead.md) (week 1 produces nothing, honestly) → [pricing](financials/pricing.md) (the first environment is free because it costs you more).

**Skeptic** — [audit/COVERAGE.md](audit/COVERAGE.md) → [validation/pivot_log.md](validation/pivot_log.md) (five load-bearing claims that survived authorship and did not survive review) → [validation/riskiest_assumptions.md](validation/riskiest_assumptions.md) (every row untested).

## Artifact map

| Path | What it holds | Files | Owning skill |
|---|---|---|---|
| [BRIEF.md](BRIEF.md) · [ASSUMPTIONS.md](ASSUMPTIONS.md) | Founder brief · 13 decisions and 12 assumptions | 2 | grill-me |
| [research/](research/) | Landscape, competitor teardown, capability table, dated survey, 36 sources | 5 | startup-research |
| [strategy/](strategy/) | Market type, positioning, bottom-up sizing, personas, canvases, GTM, petal, channel economics, sales roadmap | 11 | startup-strategy |
| [product/](product/) | PRD with nine first-principles, 20 flagship features, 61 prioritized, four journeys, thirteen-screen UX spec | 8 | startup-product |
| [tech/](tech/) | Whitepaper, seven deep dives, 11 Mermaid architecture diagrams, 73 techniques, decision tree, technique×feature matrix, not-vaporware | 19 | startup-tech |
| [narrative/](narrative/) | One-pager, technical VC memo, 14-slide deck, working-backwards press release, founder story, mission/vision | 6 | startup-narrative |
| [validation/](validation/) | Riskiest assumptions, 8-experiment board, discovery guide, get/keep/grow, stage gate, metrics by stage, pivot log, dual MVP, decision-making unit | 9 | startup-validation |
| [financials/](financials/) | Banded pricing, revenue build, unit economics (both node cases), use of funds, 12-row risk matrix, comps and exits | 6 | startup-financials |
| [visuals/](visuals/) | 69-row manifest, 20 rendered HTML infographics, 46 image prompts | 2 md + 26 | startup-visuals |
| [audit/](audit/) | Coverage audit against the manifest | 1 | startup-audit |

## Visual index

**No raster images are rendered** — no text-to-image tool existed in this run, so the 46 prompts in [visuals/image_prompts.md](visuals/image_prompts.md) are pending. The pack's visual layer is 20 self-contained HTML infographics, each carrying real figures from the artifact it cites:

| | Takeaway |
|---|---|
| [V02 · Positioning map](visuals/infographics/V02_positioning-map.html) | Three quadrants are crowded; the fourth was empty for a reason that expired in 2024 |
| [V09 · Bottom-up SAM](visuals/infographics/V09_sam-build.html) | A defended $179M SAM, with its two softest assumptions named |
| [V10 · Evidence ledger](visuals/infographics/V10_evidence-ledger.html) | Every company-killing assumption untested; three of four cost under $2,000 |
| [V11 · Hours per environment](visuals/infographics/V11_hours-per-environment.html) | The first environment costs more, not less. We do not charge for it |
| [V14 · Use of funds](visuals/infographics/V14_use-of-funds.html) | 0.5% of the round can invalidate the other 99.5% |
| [V15 · Risk matrix](visuals/infographics/V15_risk-matrix.html) | Four residuals stay high; one has no mitigation at all |
| [V16 · Revenue quality](visuals/infographics/V16_revenue-quality.html) | 73% of three-year revenue is one-time |
| [V18 · Banded pricing](visuals/infographics/V18_banded-pricing.html) | The fee's justification has failed arithmetic twice |
| [V19 · Decision-making unit](visuals/infographics/V19_decision-unit.html) | A deal signed by the owner can still fail three times over |
| [V20](visuals/infographics/V20_journey-edge-low.html) · [V21](visuals/infographics/V21_journey-beachhead.html) · [V22](visuals/infographics/V22_journey-edge-high.html) · [V23](visuals/infographics/V23_day-in-life.html) | The four journeys, component by component |
| [V24 · Thirteen screens](visuals/infographics/V24_thirteen-screens.html) | Two screens decide adoption, and neither is a dashboard |
| [V25 · Feature tiers](visuals/infographics/V25_feature-tiers.html) | The Now tier is the whole bet, and its floor is ~40 weeks |
| [V26 · Technique matrix](visuals/infographics/V26_technique-matrix.html) | Two orphan techniques turned out to be missing safety features |
| [V28](visuals/infographics/V28_experiment-board.html) · [V29](visuals/infographics/V29_stage-gate.html) · [V30](visuals/infographics/V30_metrics-by-stage.html) · [V31](visuals/infographics/V31_pivot-log.html) | Experiments, gate, metrics, and what has already been killed |

Three further rows render live from their source: [D01](tech/architecture/D01.md), [D06](tech/architecture/D06.md) and the [decision tree](tech/techniques/decision_tree.md) ship Mermaid.

## Top 5 sharpest claims

1. **The market split the problem in half and left the join manual.** Discovery tools record work and emit a diagram a human must implement; resolution tools execute but must be configured. Both halves are mature. [S5] [S8] [S10] — [research/landscape.md](research/landscape.md)
2. **Deployment friction is the incumbent's revenue, not its defect.** ServiceNow implementation runs 3–5× the annual licence, so self-onboarding cannibalises the larger half of its own deal. [S20] — [research/competitors.md](research/competitors.md)
3. **The first environment costs more than doing nothing** — 31–46 hours against a 25–40 baseline — so we waive it. Compression begins at environment 2. [S21] — [product/journeys/beachhead.md](product/journeys/beachhead.md)
4. **There is no 10×.** The claim was withdrawn when its baseline turned out to be hours nobody spends. What survives is one ~1.4× multiplier, one negative, and three effects that are not multipliers. — [tech/whitepaper.md](tech/whitepaper.md)
5. **The core mechanism has no benchmark and no named prior system**, and the falsifying number is declared in advance: below ~70% cross-environment transfer, the company is materially smaller and says so. — [research/capability_table.md](research/capability_table.md) row 5

## Completeness

`PARTIAL`. 59 of 61 required artifacts are present with no stubs, and property 0 passes on all 68 — after this audit found and fixed eleven failures. **Two manifest rows are open: dossier illustration coverage (37 of 58 artifacts have prompts but no rendered image) and the website phase, which has not been run.** More importantly, **only one of eight generated layers has passed its critic gate**; narrative, validation, financials and visuals have never been reviewed at all. The critic loop is where this pack found its real errors — five load-bearing claims survived authorship and did not survive scrutiny — so the unreviewed layers should be read as drafts. Row-by-row status, the property-0 result and the priority draw order are in [audit/COVERAGE.md](audit/COVERAGE.md).
