# Image prompts

> **What this is** — one production-grade text-to-image prompt per image-form manifest row, each fully self-contained: subject, every label to embed verbatim, composition zones, orientation, and the pack's shared style block.
> **Why it exists** — no text-to-image tool is available in this run, so these rows are `pending-image`. The prompts are written to be usable unchanged by a human with an image tool or by a later session with one, which is the difference between a gap and a deferral.
> **How to read it** — the label lists are verbatim and closed. A skeptic should check that no prompt asks a diffusion model to render a sentence, which is the failure mode that garbles.
> **Depends on / feeds** — inherits [visual_manifest.md](visual_manifest.md); feeds `visuals/images/` when a renderer exists.

## Rules every prompt below obeys

Image models garble dense text. Each prompt therefore: uses **short labels only** (a code plus two or three words), **states element counts as numbers** ("exactly THREE bars"), **binds every label inside the shape it describes** rather than floating beside it, and **forbids additions**. Anything needing a paragraph is an HTML infographic instead, and is already rendered.

**Shared style block — prepend to every prompt:**
> *Extremely information-dense professional infographic, white background, elite systems-architect quality, clean modern typography with clear hierarchy, one bold headline takeaway, 3–5 labeled information zones, consistent accent palette (indigo #4338CA accent, teal #0D7A70 for positive signal, amber #B45309 for caveats, near-black #0B0B12 ink, #E4E4EB hairlines), refined iconography, print-grade, no watermark, no lorem ipsum. Render ONLY the labels quoted in the prompt — add no other text.*

---

### P01 · The knowledge cycle
**Orientation:** 16:9. **Subject:** a closed four-node cycle with a leak arrow.
**Exactly FOUR nodes in a ring**, each label inside its node: `ACQUIRE`, `DECAY`, `LOSE`, `RE-ACQUIRE`. **One arrow leaving the ring downward**, labelled inside a small tag: `EVERY TICKET PAYS THE GAP`. Headline across the top: `A knowledge debt with no principal repayment`. One figure in a corner tag: `25–40 HRS PER CLIENT`.
**Forbid:** any additional text, any human figures.

### P03 · Right input, wrong decade
**Orientation:** 16:9. **Subject:** two horizontal timelines stacked, sharing one time axis.
**Upper track, exactly TWO markers**, labels inside the markers: `FORTRESSIQ 2017`, `ACQUIRED 2021`. **Lower track, exactly THREE markers**: `12% 2024`, `85% 2026`, `SKILL.MD STANDARD`. A vertical dashed band spanning both tracks labelled inside a tag: `THE GAP`. Headline: `Recording worked. There was nothing to send it to.`
**Forbid:** curves on the upper track, any prose.

### P04 · The capability curve and its ceiling
**Orientation:** 16:9. **Subject:** one rising curve with a hard annotation.
**Exactly ONE curve** rising left to right. **Exactly THREE point labels bound to the curve**: `12%`, `85%`, `86.1%`. **One horizontal dashed line below the curve's right end**, labelled inside its own tag: `20.6% LONG-HORIZON`. Headline: `Good enough to be interesting. Not good enough to trust.`
**Forbid:** a second curve, gridline numbers, any sentence.

### P05 · The closed loop
**Orientation:** square. **Subject:** a seven-stage ring.
**Exactly SEVEN nodes**, labels inside: `WATCH`, `DISTIL`, `REHEARSE`, `GATE`, `ACT`, `VERIFY`, `LEARN`. One node (`DISTIL`) filled in the indigo accent; the rest outlined. **One inward arrow from `LEARN` to `DISTIL`.** Headline above the ring: `Break any link and it becomes something that already exists.`
**Forbid:** icons inside nodes, extra arrows, any caption text.

### P06 · The ticket-side panel
**Orientation:** 16:9. **Subject:** a clean product UI mock, three stacked zones in a single panel.
**Exactly THREE zones**, each with its label bound inside: top `MATCHED SKILL`, middle `2 DEVIATIONS AT THIS TENANT` (rendered as exactly TWO short rows), bottom `RUN WITH ME`. A small monospace tag in the panel header: `GATED`.
**Forbid:** realistic body text, browser chrome, any additional UI element.

### P07 · Contract vs goal
**Orientation:** 16:9. **Subject:** a two-column before/after ledger showing the same procedure under a UI change.
**Exactly TWO columns.** Left column header inside its band: `RPA · ASSERTS THE INTERFACE`; below it exactly THREE step blocks, the third filled amber and labelled inside: `HALTS OR PROCEEDS WRONGLY`. Right column header: `SKILL · ASSERTS THE GOAL`; exactly THREE step blocks, the third filled teal and labelled inside: `RE-GROUNDS`. Headline: `The difference is what the check is about.`
**Forbid:** any explanatory sentence, arrows between columns.

### P08 · The variance envelope
**Orientation:** 16:9. **Subject:** one modal path with a distribution around it.
**One central bold path left to right** labelled inside a tag: `MODAL PROCEDURE`. **Exactly SIX faint parallel paths** around it, three above and three below, one of which is labelled inside: `OBSERVED IN 14 TENANTS`. A corner tag: `3 VARIANTS · 2 DEVIATIONS`. Headline: `The distribution is the asset. The procedure is in the vendor's docs.`
**Forbid:** more than six variant paths, any legend.

### P12 · The admin surface map
**Orientation:** 16:9. **Subject:** a horizontal stacked band split into two regions.
**Exactly TWO regions.** Left region filled light, label bound inside: `API-COVERED · WE ARE THE WRONG TOOL`. Right region filled indigo, label bound inside: `UI-ONLY · TERMINALS, NATIVE ADMIN, LEGACY`. **One arrow above the band pointing right-to-left**, labelled inside a tag: `SHRINKS EVERY YEAR`. Headline: `We would rather name the limit than have it found.`
**Forbid:** percentages, any third region, prose.

### P13 · Founder-market fit
**Orientation:** 16:9. **Subject:** a three-cell horizontal ledger.
**Exactly THREE cells**, labels bound inside each: cell 1 filled teal `COVERED · AI/AGENTS ENGINEERING`, cell 2 filled amber `MISSING · MSP OPERATING HISTORY`, cell 3 outlined `CLOSES · FIRST HIRE, MONTH 14`. Headline: `The weakest assumption is labelled, not hidden.`
**Forbid:** portraits, any additional cell, any sentence.

---

## Verification required before any row is marked `rendered`

Two stages, both mandatory, per the visuals contract:

1. **The file exists** — nonzero size >10KB, PNG header bytes `89504e47`. Never trust "the image has been generated".
2. **The file is *this* visual** — open it and read it. Confirm the headline matches the prompt's headline line. A file of the right size in the right place can still be the wrong picture, and a raster that passes stage 1 and fails stage 2 is worse than a missing one because the audit will never catch it again.

**Three failure modes and what catches each:** clipping (automated edge-brightness check), garbling (only by reading it), and **mis-binding** — perfect spelling, clean margins, labels attached to the wrong element. The third passes every automated gate. Every prompt above states element counts as numbers and binds labels inside shapes specifically to make mis-binding detectable by counting.

**Recommended next 3:** (1) render P07 first — the contract-vs-goal visual carries the argument that converts technical evaluators; (2) prove the byte-transfer path on one image before generating the batch; (3) re-run `build_docimages.js` after every batch, since it is the reconciliation step and prints what remains unillustrated.

### P33 · Cost per ticket vs price
**Orientation:** 16:9. **Subject:** two bars and a ceiling line.
**Exactly TWO bars** side by side, labels bound inside: `THEIR MARGINAL COST $2–6`, `OUR PRICE $6`. **One horizontal dashed line above both**, labelled inside a tag: `CAPACITY CEILING`. One corner tag: `26% CANNOT STAFF`. Headline: `Not cheaper. More throughput.`
**Forbid:** a third bar, axis numbers, any sentence.

---

## Dossier prompts (V40–V76)

Each uses the shared style block above plus this frame: **A4 portrait, one headline takeaway, the stated element count, every label bound inside its shape, no prose, no additional text.** The Composition column states the element count as a number precisely so mis-binding is detectable by counting — the failure mode that passes every automated gate.

| ID | Source artifact | Subject | Labels (verbatim, closed set) | Composition |
|---|---|---|---|---|
| P40 | `ASSUMPTIONS.md` | Decisions vs assumptions | `CONFIRMED · DECIDED · ASSUMED · OPEN` | exactly FOUR columns |
| P41 | `BRIEF.md` | Founder brief spine | `PROBLEM · MECHANISM · WEDGE · MOAT · RISK` | exactly FIVE stacked bands |
| P42 | `financials/comps_exits.md` | Acquirer landscape | `MSP PLATFORMS · AUTOMATION · INCUMBENT` | exactly THREE grouped clusters |
| P43 | `financials/unit_economics.md` | Two node cases | `MSP OWNS · WE PROVIDE` | exactly TWO facing columns |
| P44 | `narrative/founder_story.md` | Founder edge and gap | `MECHANISM COVERED · MARKET MISSING` | exactly TWO facing blocks |
| P45 | `narrative/future_press.md` | 2026 to 2032 | `2027 RESULT WAS BELOW THRESHOLD` | exactly SIX timeline markers, ONE amber |
| P46 | `narrative/mission_vision.md` | Five values as trade-offs | `EACH VALUE HAS A COST` | exactly FIVE paired blocks |
| P47 | `narrative/one_pager.md` | One page, seven claims | `PROBLEM · GAP · MECHANISM · WHY NOW · LIMITS · MARKET · ASK` | exactly SEVEN stacked bands |
| P48 | `narrative/pitch_deck.md` | Fourteen slides, three limits | `SLIDES 10 11 12 ARE LIMITS` | exactly FOURTEEN ticks, THREE amber |
| P49 | `narrative/vc_memo.md` | Memo structure, risks longest | `THESIS · TEARDOWN · ARCH · EXAMPLES · WIN · RISKS · TRACTION` | exactly SEVEN bars, RISKS longest |
| P50 | `product/PRD.md` | Nine principles to features | `P1-P9` | exactly NINE numbered nodes fanning to a feature column |
| P51 | `product/features_flagship.md` | Twenty features, one circuit | `WATCH · DISTIL · REHEARSE · GATE · ACT · VERIFY · LEARN` | exactly SEVEN groups on a ring |
| P52 | `research/capability_table.md` | Nine capabilities, three gaps | `READY · PARTIAL · UNEVIDENCED` | exactly NINE rows, three shaded amber |
| P53 | `research/competitors.md` | Ten competitors on two axes | `CONFIGURED · OBSERVED · ARTIFACT · EXECUTES` | a 2x2 with exactly TEN dots |
| P54 | `research/landscape.md` | Six tiers, nearest to farthest | `DISCOVERY · AI DESKS · AGENTIC · RESEARCH · MANUAL · HYBRID` | exactly SIX horizontal bands |
| P55 | `research/sources.md` | Source authority mix | `PRIMARY · ANALYST · VENDOR · JOURNALISM` | exactly FOUR proportional bars |
| P56 | `research/survey.md` | Forty years, four dead ends | `PbD · PROCESS MINING · TASK MINING · RPA` | exactly FOUR timeline markers |
| P57 | `strategy/business_model_canvas.md` | Nine blocks, one test each | `9 BLOCKS · 9 KILL CONDITIONS` | a 3x3 grid, each cell one short label |
| P58 | `strategy/channel_plan.md` | Six channels against one ceiling | `VIABLE · MARGINAL · IMPOSSIBLE` | exactly SIX bars against one dashed ceiling line |
| P59 | `strategy/gtm.md` | Twelve-month motion | `MONTH 1 · MONTH 8 · MONTH 10 · MONTH 12` | exactly FOUR milestones on one track |
| P60 | `strategy/lean_canvas.md` | Lean canvas, riskiest cell marked | `UNFAIR ADVANTAGE = VARIANCE ENVELOPE` | nine cells, exactly ONE filled amber |
| P61 | `strategy/market_type.md` | Hybrid market type | `RE-SEGMENTED BY BUYER · NEW MARKET BY BUDGET` | exactly TWO overlapping regions |
| P62 | `strategy/personas.md` | Five seats, one system | `PRIYA · DANA · RAY · MARCUS · SONIA` | exactly FIVE cards in a row |
| P63 | `strategy/petal_diagram.md` | Six budget pools | `ONBOARDING LABOUR · HEADCOUNT · ITSM · DOCS · DISCOVERY · SCRIPTING` | exactly SIX petals around a centre |
| P64 | `strategy/sales_roadmap.md` | Seven-step sale, two vetoes | `STEP 4 RAY · STEP 5 SONIA` | exactly SEVEN steps, two flagged amber |
| P65 | `strategy/value_prop_canvas.md` | Jobs, pains, gains vs relievers | `JOBS · PAINS · GAINS` | two facing triangles, exactly THREE labels each |
| P66 | `tech/architecture/00_INDEX.md` | Three trust zones | `CLIENT · MSP · VENDOR` | exactly THREE nested boundaries |
| P67 | `tech/architecture/D09.md` | One node per MSP | `3 PARTNERS = 3 NODES` | exactly THREE node icons, not 123 |
| P68 | `tech/deep_dives.md` | Seven deep dives, one research bet | `DD1 IS THE BET` | exactly SEVEN cards, ONE filled indigo |
| P69 | `tech/not_vaporware.md` | Buildable vs research risk | `BUILDABLE · HARD · RESEARCH` | exactly THREE proportional bands |
| P70 | `tech/techniques/wave1.md` | Wave 1 borrowed vs adapted | `23 BORROWED · 8 ADAPTED` | exactly TWO proportional bars |
| P71 | `tech/techniques/wave2.md` | Wave 2 clusters | `5 CLUSTERS · 24 TECHNIQUES` | exactly FIVE grouped blocks |
| P72 | `tech/techniques/wave3.md` | Wave 3 is a pipeline, not a plan | `SPECULATIVE` | exactly FOUR outlined cards, none filled |
| P73 | `tech/whitepaper.md` | Four frictions, five mechanisms | `F1 F2 F3 F4 → M1 M2 M3 M4 M5` | exactly FOUR blocks mapping to FIVE |
| P74 | `validation/discovery_guide.md` | Twenty questions, all past-tense | `PROBLEM 14 · SOLUTION 6` | exactly TWO proportional bars |
| P75 | `validation/get_keep_grow.md` | Funnel with a review throttle | `GET · KEEP · GROW` | exactly THREE funnel stages, GROW pinched |
| P76 | `validation/mvp_definition.md` | Two MVPs, one is not software | `LOW-FI: NOT SOFTWARE · HI-FI: NO EXECUTION` | exactly TWO facing cards |

**None of these is rendered.** A founder with an image tool can produce the set from this table in an afternoon; a later session with a renderer should verify each in two stages (file exists · file is *this* visual) before marking any row `rendered`.