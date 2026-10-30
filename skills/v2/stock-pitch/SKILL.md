---
name: stock-pitch
description: "Builds an LSMF/LFCS-style equity stock pitch end to end: screen, thesis and variant view, catalysts, DCF plus comps, risks, slide outline and Q&A drill. Use whenever the user mentions a stock pitch, long idea, a ticker plus pitch, target price, upside, valuing a single company, a stock competition, or LSMF/LFCS, even if he doesn't say pitch. Do NOT use for macro, rates, FX, commodity or sector views (research-note or markets-note) or applications (recruiting-pack)."
---

# Stock Pitch v2 (LSMF / LFCS)

Start the reply with `Using: stock-pitch`.

**Outcome:** a pitch that survives a PM asking "why now and why us": one variant view, sourced numbers, valuation that cross-checks, and answers ready for the 10 hardest questions.

**Done when:** variant view stated (or the idea killed), valuation built in a script/sheet with sensitivity, top 3 risks with kill metrics, 8–10 slide outline, 10-question drill, fact-checker clean, project note updated.

## Route (screen on Sonnet · medium; full pitch on Opus · high)
| Step | Who | Returns |
|---|---|---|
| 1. Screen (no name yet) | chat model, no subagents | 3 names × 3 lines |
| 2. Data: company + peers (Helios: US tower peers AMT, CCI, SBAC via SEC data; HTWS.L price via Yahoo) | fin-data-puller (Haiku); work from its table only | sourced table; raw to `_scratch/` |
| 2b. Annual report / long filing | pdf-summariser (Haiku) | ≤400 words + page refs |
| 3. Thesis, 3 pillars + variant view | Opus, never delegated | draft |
| 4. Catalysts | Opus | dated list |
| 5. Valuation: DCF + comps | model-builder / dcf / comps skills, maths in code | model + sensitivity |
| 6. Attack | red-team (Sonnet) once | objections → Risks, questions → drill |
| 7. Risks, slide outline, Q&A drill | Opus | |
| 8. Verify | fact-checker (Haiku) once on final | fix every ⚠️/❌ |
| 9. Save | vault-updater (Haiku) | diff line |
Stop for Max's input after steps 1, 3 and 5. Plain chat: do 2, 6 and 8 yourself, briefly.

## Context (minimum)
`00 Context/Index.md`, then the matching project note (`10 Projects/LSMF Helios Towers Pitch.md` or `10 Projects/LFCS Stock Pitch Competition.md`) and `30 Resources/LFCS Word Bank.md`.

## Format rules
- **LFCS:** 9-min pitch + 3-min Q&A. US/European listing, ≥$5bn market cap, long-only. Sectors: Tech, Consumer, Industrials, Comms, Financials, Healthcare. Scoring: Thesis 30 / Financials & valuation 30 / Q&A 25 / Presentation 15. Spend slides where the marks are.
- **LSMF:** Real Assets coverage (towers, infrastructure, real estate, REITs). Pitch to Head of Sector, then PMs.

## Content standards
- Variant view in one sentence: "The market thinks X; we think Y because Z." None → say so and stop.
- Catalysts dated, each with what it proves.
- Valuation: WACC build, terminal growth, sensitivity table, implied upside; DCF vs multiples cross-check.
- Risks: top 3, each with mitigant and the metric that says we're wrong.
- Drill: 10 questions, 2-line answers; at least one on WACC, one on terminal value, one on why the market is wrong.

## Hard rules
- Every number sourced (filing, market-data tool, company report) or labelled "estimate"; never invent tickers, prices or multiples. Reason: judges and PMs check, and the LSMF promotion rides on credibility.
- Arithmetic in code or a spreadsheet, never mental maths. Reason: valuation errors are the fastest way to lose the 30 financial marks.
- Use word-bank terms correctly (EV = market cap + debt − cash; alpha = differ from the market and be right).
- Plain, confident language. Humanize pass on anything Max will present.

## Save
vault-updater: project note Current state, Decisions (with reasons), Next actions, `updated:`.
