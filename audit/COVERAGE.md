# Coverage audit — 2026-09-04

> **What this is** — the run measured against `references/artifact-manifest.md`, row by row, from the glob at the moment of writing rather than from memory of what was generated.
> **Why it exists** — "done" in this pack is defined by the manifest, not by the author's sense of completeness. This file is also where the run's two genuine gaps are recorded as **open**, because a coverage audit that closes its own gaps is worthless.
> **How to read it** — §3 is the gap list and it is short. A skeptic should check §2's property-0 result, which is mechanical and was failing on eleven artifacts before this audit ran.
> **Depends on / feeds** — measures every layer against the manifest and `references/quality-bar.md`; feeds [../README.md](../README.md) and the site.

## 1 · Manifest coverage

**59 of 61 required rows present · 0 stubs · 2 open.** Counted from the glob on 2026-09-04.

| Layer | Rows | Status |
|---|---|---|
| A00–A01 brief | 2/2 | present |
| A02–A06 research | 5/5 | present |
| A07–A13, A58–A61 strategy | 11/11 | present |
| A14–A21 product | 8/8 | present |
| A22–A26, A28–A30 tech | 8/8 | present |
| A24 architecture (11 files individually) | 11/11 | present |
| A27 wave 3 | opt | present |
| A31–A35, A64 narrative | 6/6 | present |
| A36–A42, A62–A63 validation | 9/9 | present |
| A43–A48 financials | 6/6 | present |
| A49 visual manifest | 1/1 | present — 69 rows |
| A50 HTML infographics | req | present — 20 rendered, reconciled to the glob |
| A51 image prompts | 1/1 | present — 46 prompts |
| A52 rendered images | opt | **0** — no text-to-image tool in this run |
| **A52b docimages coverage** | req | **OPEN — see §3** |
| A53 ingest | opt | n/a — no sources ingested |
| **A54 this file** | req | present |
| A55 run README | req | present, refreshed from the glob |
| A56–A57 site | opt | not run |

**No stub rows.** Every required artifact exceeds 400 words and carries its owning contract's named sections. The lowest-word required artifacts were re-checked individually rather than trusted to a line count: `research/capability_table.md` and `strategy/lean_canvas.md` are dense tables whose substance is in cells, not lines.

## 2 · Quality-bar spot checks

| Property | Method | Result |
|---|---|---|
| **0 · orientation block** | **Checked on all 68 artifacts, not sampled** | **0 failures — after this audit fixed 10.** All ten architecture diagrams (D01–D10) were missing it. That is exactly the failure this check exists to catch, and it was invisible to every other review |
| 1 · mechanism over adjective | grep for load-bearing banned adjectives | 0 occurrences |
| 2 · every number sourced or flagged | count of `[Sn]` and `(assumption)` tags | 296 source tags · 66 assumption tags across the run |
| 5 · decision-forcing endings | grep for "Recommended next" | 50/68. **18 judged exemptions, listed below — not silent passes** |
| 7 · dense, not long | inspection | no artifact padded to length; three files (wave 2, wave 3, technique matrix) explicitly stop short and say the field is thinner rather than padding to a round number |

**The 18 property-5 exemptions, with the reason each was judged rather than fixed:**
- **11 architecture files** (`00_INDEX` + D01–D10) — diagram captions. Their job is "what a reviewer should notice", and appending a recommendation would be padding.
- **5 narrative artifacts** (`one_pager`, `vc_memo`, `founder_story`, `mission_vision`, `future_press`) — persuasion artifacts whose ending *is* the decision. The one-pager ends with the ask; the memo ends with the traction admission.
- **`BRIEF.md`, `ASSUMPTIONS.md`** — source-of-truth files that other artifacts read, not artifacts that force a decision themselves.

**Five research artifacts were fixed rather than exempted** during this audit — `landscape`, `competitors`, `capability_table`, `survey` and `sources` now end with what to research next, which is a genuine improvement rather than a compliance gesture.

## 2b · Cross-artifact numeric consistency sweep

Run 2026-09-06, mechanically: every figure superseded by a decision (D9, D11) or by a critic correction was searched across all 68 artifacts, and each occurrence classified as *live* or *historical*.

**31 live occurrences flagged · 26 correct on inspection · 5 genuinely stale and fixed.**

The 26 correct ones are the deliberate two-scenario tables in `revenue_build.md` and `unit_economics.md` (flat basis alongside the chosen banded one), the D9 decision record, and coincidental matches — a $9,000 CAC range and a 35% reseller margin are not the $9,000 fee revenue or the 35% automatable share.

**The five fixed:**

| File | Was | Now |
|---|---|---|
| `strategy/market_sizing.md` | D9's consequences read as current | marked superseded by D11 the same day, with current values stated |
| `product/PRD.md` | ~$7,100 year-1 model | ~$5,110 (D9, D11) |
| `tech/not_vaporware.md` | ~$1,494/month, ~$17,900/yr | ~$1,247/month, ~$14,930/yr at the banded fee |
| `validation/get_keep_grow.md` | steady state ~$17,900 | ~$14,930 |
| `tech/whitepaper.md`, `architecture/D06.md` | k≥3 distinct **tenants** | m≥3 distinct **MSPs**, with the hole the old threshold left explained |

**This check belongs in every future audit of this run.** Four cascades have passed through this pack (the penetration fix, D9, D11, the k-threshold correction), and each one left stale figures in files nobody thought to re-read. It is mechanical, it takes a minute, and it has found something every time.

## 3 · Open rows — deliberately not closed

### A52b · Dossier illustration coverage — **OPEN**

**58 substantive artifacts (>400 words). 21 covered by a rendered HTML infographic or a live Mermaid source. 37 uncovered.**

The manifest carries a row and a production-ready prompt for every one of the 37, and `visuals/image_prompts.md` §Dossier holds them. **They are not rendered because no text-to-image tool exists in this run.**

Two things worth recording precisely:

1. **The shipped `build_docimages.js` reports 0 documents and 66 unillustrated**, because it indexes rendered PNGs only. That is correct behaviour for the tool and it understates actual coverage — a separate `visuals/dochtml.json` records the 21 artifacts covered by HTML and Mermaid, which the builder cannot see.
2. **This row stays open on the founder's explicit instruction.** A pack that closes a coverage row by redefining what coverage means has learned nothing from the five claims its own critics killed.

**To close it:** a session with an image tool renders the 46 prompts, verifies each in two stages (the file exists · the file is *this* visual), and re-runs both builders.

### A56–A57 · Site — **not run**

The website phase has not been attempted. It is gated behind the audit by design, and behind four owed critic rounds.

## 4 · Critic coverage — the other honest gap

| Phase | Rounds run | State |
|---|---|---|
| 2 · strategy | **3 — all three critics PASS** | **gate passed** |
| 3 · product | 2 | revised; no fatals remain; **round 3 not run** |
| 4 · tech | 1 | revised; **round 2 killed twice by session rate limits** |
| 5 · narrative | **0** | **never critiqued** |
| 6 · validation | **0** | **never critiqued** |
| 7 · financials | **0** | **never critiqued** |
| 8 · visuals | **0** | **never critiqued** |

**Only one phase has actually passed its gate.** The critic loop is where this pack found its real errors — five load-bearing claims survived authorship and did not survive scrutiny, recorded as K7–K11 in `validation/pivot_log.md`. **Four layers have never been through it, and the run should be read accordingly.**

## 5 · Priority draw order

What to do next, in order, with effort:

| # | Action | Effort | Why first |
|---|---|---|---|
| 1 | **Critic rounds on phases 5–7** | 9 agent runs | Narrative, validation and financials have never been reviewed, and the financials layer contains the numbers a reader checks first |
| 2 | Critic round 2 on tech, round 3 on product | 6 agent runs | Both were interrupted, not completed |
| 3 | Render the 46 image prompts | 1 session with a tool | Closes A52b |
| 4 | `startup-website` | 1 phase | Gated on the above |

**Recommended next 3:** (1) run the phase 5–7 critic loops before the site, because a site built from an uncritiqued narrative layer propagates whatever is wrong in it; (2) do not mark A52b closed by any route other than rendered, verified images; (3) re-run this audit after the critic rounds — a coverage audit taken before four layers have been reviewed measures presence, not quality, and this one says so.
