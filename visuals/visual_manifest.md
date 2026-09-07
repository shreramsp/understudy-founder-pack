# Visual manifest

> **What this is** — the complete ranked list of visuals this pack needs, grouped by audience, each with its source artifact, its form (HTML / Mermaid / image prompt) and its status.
> **Why it exists** — visuals generated ad hoc illustrate whatever was easiest to draw. This manifest is derived from what the pack actually argues: every `visual:` line in the pitch deck, every architecture diagram, and a dossier-coverage pass over artifacts that are walls of prose.
> **How to read it** — the Form column is a technical classification, not a style choice (A50): rows whose content is text a reader must read *exactly* get HTML; chart-shaped and schematic rows get image prompts. A skeptic should check the Status column against the glob, not against this sentence.
> **Depends on / feeds** — derived from [../narrative/pitch_deck.md](../narrative/pitch_deck.md), [../tech/architecture/](../tech/architecture/), and the dossier pass below; feeds `pack.html`, `startup-website`, `audit/COVERAGE.md`.

**Palette and type, declared once so the set is consistent:** ink `#0B0B12` · muted `#5A5A6B` · line `#E4E4EB` · accent `#4338CA` · accent-soft `#EEEDFB` · signal `#0D7A70` · warn `#B45309` · white ground. Inter for text, JetBrains Mono for **every number, threshold and identifier**. Orientation: 16:9 for deck rows, A4 portrait for dossier rows.

**No text-to-image tool is available in this run.** Every image-form row is therefore `pending-image` with a production-ready prompt in [image_prompts.md](image_prompts.md); HTML rows are generated and are the pack's actual visual layer. This is stated rather than left for the audit to discover.

## Investors

| ID | Title | Audience | Source | Form | Status |
|---|---|---|---|---|---|
| V01 | The knowledge cycle: acquire → decay → lose → re-acquire | investors | tech/whitepaper.md | image | pending-image |
| V02 | The two-axis map: configured vs observed × artifact vs executes | investors | strategy/positioning.md | html | **rendered** |
| V03 | FortressIQ 2017–2021 against the computer-use capability curve | investors | research/landscape.md | image | pending-image |
| V04 | OSWorld capability curve with the honest ceiling annotated | investors | research/capability_table.md | image | pending-image |
| V09 | Bottom-up SAM build, arithmetic shown | investors | strategy/market_sizing.md | html | **rendered** |
| V10 | The evidence ledger: sourced / assumed / unknown | investors | validation/riskiest_assumptions.md | html | **rendered** |
| V11 | Hours per environment 1–5 against baseline, waiver marked | investors | product/journeys/beachhead.md | html | **rendered** |
| V14 | Use of funds against the one milestone | investors | financials/use_of_funds.md | html | **rendered** |
| V15 | Risk matrix with residuals | investors | financials/risk_matrix.md | html | **rendered** |
| V16 | Revenue quality: one-time vs recurring across the ramp | investors | financials/revenue_build.md | html | **rendered** |

## Buyers and partners

| ID | Title | Audience | Source | Form | Status |
|---|---|---|---|---|---|
| V05 | The closed loop: Watch → Distil → Rehearse → Gate → Act → Verify → Learn | buyers | product/PRD.md | image | pending-image |
| V07 | Contract vs goal: the same procedure under a UI change | buyers | tech/whitepaper.md | image | pending-image |
| V12 | Admin surface map: API-covered vs UI-only | buyers | tech/techniques/wave3.md | image | pending-image |
| V33 | Cost per ticket: their marginal cost vs our price, capacity ceiling marked | buyers | narrative/pitch_deck.md | image | pending-image |
| V17 | The two-stage boundary: what leaves your environment, what leaves your MSP | buyers | tech/architecture/D06.md | mermaid | **source renders** |
| V18 | Banded pricing against hours displaced, by client size | buyers | financials/pricing.md | html | **rendered** |
| V19 | Decision-making unit: who can say no | buyers | validation/decision_making_unit.md | html | **rendered** |

## Users and operators

| ID | Title | Audience | Source | Form | Status |
|---|---|---|---|---|---|
| V06 | The ticket-side panel: matched skill, deviations, one approval | users | product/ux_spec.md | image | pending-image |
| V08 | The variance envelope: one procedure, many tenants | users | tech/deep_dives.md | image | pending-image |
| V20 | Journey: Priya at an unfamiliar client | users | product/journeys/edge_low.md | html | **rendered** |
| V21 | Journey: Dana onboards an environment | users | product/journeys/beachhead.md | html | **rendered** |
| V22 | Journey: Ray converted, then stretched | users | product/journeys/edge_high.md | html | **rendered** |
| V23 | One Tuesday, four seats | users | product/journeys/day_in_life.md | html | **rendered** |
| V24 | The thirteen screens | users | product/ux_spec.md | html | **rendered** |

## Team and roadmap

| ID | Title | Audience | Source | Form | Status |
|---|---|---|---|---|---|
| V13 | Founder-market fit: covered, missing, how it closes | investors | narrative/founder_story.md | image | pending-image |
| V25 | Feature tiers with the build-math floor | operators | product/features_prioritized.md | html | **rendered** |
| V26 | Technique × feature matrix heat table | operators | tech/techniques/technique_feature_matrix.md | html | **rendered** |
| V27 | The runtime decision tree | operators | tech/techniques/decision_tree.md | mermaid | **source renders** |
| V28 | Experiment board: thresholds declared in advance | operators | validation/experiment_board.md | html | **rendered** |
| V29 | Stage gate: where we are and what passing requires | operators | validation/stage_gate.md | html | **rendered** |
| V30 | Metrics by stage, and the vanity metrics to ignore | operators | validation/metrics_by_stage.md | html | **rendered** |
| V31 | Pivot log: what has already been killed | operators | validation/pivot_log.md | html | **rendered** |
| V32 | The capture-to-skill pipeline | operators | tech/architecture/D01.md | mermaid | **source renders** |

## Dossier coverage — one row per substantive artifact with no visual

The coverage pass found **58 artifacts over ~400 words, of which 21 are covered** by the rows above. The remaining **37 are listed here**, one row each, sourced to the artifact. Every one is schematic and label-only by design: these are dossier illustrations, and a diffusion model garbles sentences.

| ID | Title | Audience | Source | Form | Status |
|---|---|---|---|---|---|
| V40 | Decisions vs assumptions | dossier | ASSUMPTIONS.md | image | pending-image |
| V41 | Founder brief spine | dossier | BRIEF.md | image | pending-image |
| V42 | Acquirer landscape | dossier | financials/comps_exits.md | image | pending-image |
| V43 | Two node cases | dossier | financials/unit_economics.md | image | pending-image |
| V44 | Founder edge and gap | dossier | narrative/founder_story.md | image | pending-image |
| V45 | 2026 to 2032 | dossier | narrative/future_press.md | image | pending-image |
| V46 | Five values as trade-offs | dossier | narrative/mission_vision.md | image | pending-image |
| V47 | One page, seven claims | dossier | narrative/one_pager.md | image | pending-image |
| V48 | Fourteen slides, three limits | dossier | narrative/pitch_deck.md | image | pending-image |
| V49 | Memo structure, risks longest | dossier | narrative/vc_memo.md | image | pending-image |
| V50 | Nine principles to features | dossier | product/PRD.md | image | pending-image |
| V51 | Twenty features, one circuit | dossier | product/features_flagship.md | image | pending-image |
| V52 | Nine capabilities, three gaps | dossier | research/capability_table.md | image | pending-image |
| V53 | Ten competitors on two axes | dossier | research/competitors.md | image | pending-image |
| V54 | Six tiers, nearest to farthest | dossier | research/landscape.md | image | pending-image |
| V55 | Source authority mix | dossier | research/sources.md | image | pending-image |
| V56 | Forty years, four dead ends | dossier | research/survey.md | image | pending-image |
| V57 | Nine blocks, one test each | dossier | strategy/business_model_canvas.md | image | pending-image |
| V58 | Six channels against one ceiling | dossier | strategy/channel_plan.md | image | pending-image |
| V59 | Twelve-month motion | dossier | strategy/gtm.md | image | pending-image |
| V60 | Lean canvas, riskiest cell marked | dossier | strategy/lean_canvas.md | image | pending-image |
| V61 | Hybrid market type | dossier | strategy/market_type.md | image | pending-image |
| V62 | Five seats, one system | dossier | strategy/personas.md | image | pending-image |
| V63 | Six budget pools | dossier | strategy/petal_diagram.md | image | pending-image |
| V64 | Seven-step sale, two vetoes | dossier | strategy/sales_roadmap.md | image | pending-image |
| V65 | Jobs, pains, gains vs relievers | dossier | strategy/value_prop_canvas.md | image | pending-image |
| V66 | Three trust zones | dossier | tech/architecture/00_INDEX.md | image | pending-image |
| V67 | One node per MSP | dossier | tech/architecture/D09.md | image | pending-image |
| V68 | Seven deep dives, one research bet | dossier | tech/deep_dives.md | image | pending-image |
| V69 | Buildable vs research risk | dossier | tech/not_vaporware.md | image | pending-image |
| V70 | Wave 1 borrowed vs adapted | dossier | tech/techniques/wave1.md | image | pending-image |
| V71 | Wave 2 clusters | dossier | tech/techniques/wave2.md | image | pending-image |
| V72 | Wave 3 is a pipeline, not a plan | dossier | tech/techniques/wave3.md | image | pending-image |
| V73 | Four frictions, five mechanisms | dossier | tech/whitepaper.md | image | pending-image |
| V74 | Twenty questions, all past-tense | dossier | validation/discovery_guide.md | image | pending-image |
| V75 | Funnel with a review throttle | dossier | validation/get_keep_grow.md | image | pending-image |
| V76 | Two MVPs, one is not software | dossier | validation/mvp_definition.md | image | pending-image |

**All 37 are `pending-image` because no renderer exists in this run.** Their prompts are in [image_prompts.md](image_prompts.md) §Dossier, written to be usable unchanged. **Stated plainly: this run does not satisfy A52b's "no substantive artifact left unillustrated" contract**, and `audit/COVERAGE.md` should record it as an open row rather than a closed one.

## Form classification (A50) — why each row is what it is

**HTML, because the words are the content:** every table, matrix and board above. A reader must be able to transcribe the numbers — a SAM build whose figures cannot be copied cannot be checked, and an experiment board whose thresholds are approximate is not a board.

**Mermaid, because the source already renders it:** V17, V27, V32. The architecture and decision-tree documents ship live Mermaid; an HTML poster would duplicate them, so the manifest cites the source instead.

**Image prompt, because the picture is the content:** V01, V03–V08, V12, V13 — curves, timelines, loops and schematic illustrations that carry structure rather than sentences.

**Recommended next 3:** (1) render V02, V07 and V11 first — the positioning map, the contract-vs-goal mechanism and the honest hours chart carry the three arguments that convert; (2) run `build_docimages.js` after every batch, since it is the reconciliation step and prints what is still unillustrated; (3) treat the `pending-image` rows as genuinely pending — the prompts are production-ready and a founder with an image tool can render the set in an afternoon.
