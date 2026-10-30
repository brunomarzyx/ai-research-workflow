---
name: markets-note
description: "Writes or critiques a full desk-style markets note (commodities, rates/macro, equities/sector) as a Claude Doc with trades table, key figures and testable calls, then updates Notes Log, My Theses, Frameworks and the factor-bucket check. Use for an original thesis with trades (Mode A) or a critique of a broker note or X post (Mode B). Do NOT use for a short 2-page interview/LinkedIn note (research-note) or a single-company pitch (stock-pitch)."
---

# Markets Note v2

Start the reply with `Using: markets-note`.

**Outcome:** a note a desk head could trade from (Mode A) or a verdict on someone else's research that finds what they got wrong (Mode B), with the project ledger kept current.

**Done when:** every section of the chosen mode is filled, the key figures table has a source and date per row, fact-checker shows no open ⚠️/❌, and the four ledger steps in "After the note" are done.

## Mode
A = Max's own thesis. B = critique. A supplied document or post means B; otherwise A.

## Route (chat on Opus · high)
| Step | Who | Returns |
|---|---|---|
| 0. Read ledger docs, check thesis overlap, pick lenses | Opus | |
| 1. Broker note / long PDF (Mode B) | pdf-summariser (Haiku) | thesis, targets, exhibits, page refs |
| 2. Present-day levels | fin-data-puller (Haiku) | dated table |
| 3. Context per driver (≤3 questions) | web-researcher (Sonnet), 2 in parallel | ≤400 words each |
| 4. Write the note | Opus, one voice | Claude Doc |
| 5. Attack (Mode A) | red-team (Sonnet) once | feeds "What would change my mind" |
| 6. Verify | fact-checker (Haiku) once on final | fix every ⚠️/❌ |
| 7. Ledger updates | Opus (judgement), one batch at the end | |
Plain chat: do 1, 2, 3 and 6 yourself.

## Context (minimum)
Project docs `claude/Notes Log.md`, `claude/My Theses.md`, `claude/Frameworks.md` (project_read). Don't re-establish context or ask for anything these docs already hold. Overlap with an existing thesis → write an update, not a fresh view.

## Evidence standard (hard rules)
- Every number: value, date, source, verification status. Rank: primary filing/agency → wire → secondary → aggregator. Reason: past notes needed corrections on metric-basis shifts, stale figures and wrong dates or titles.
- Label "my calculation" and "my judgement". Conflicting sources: show both with their basis, never average.
- A weak number goes under "Do not quote", never rounded into a confident one.
- Never state a current level from memory.

## Mode A structure (Claude Doc)
1. Title = the argument. 2. Bottom line (+ trades in one line). 3. What changed (updates only: prior claim | status | verdict). 4. Where things stand (dated bullets by driver). 5. The distinctions doing the work (named frameworks). 6. What the market is mispricing. 7. Scenarios (triggers, dates, ranges; odds = judgement). 8. Trades table (trade, entry + date, rationale, dated catalysts, risk, invalidation; prefer RV/curve/convexity if the outright is late). 9. Equity angle (valuation as a range; negative read-across). 10. Cross-lens. 11. What would change my mind (strongest counter + answer + triggers). 12. Key figures table (Figure | Latest | Date | Source | Verified?). 13. Safe to quote / Do not quote. 14. 2–4 testable calls with check-by dates. 15. Sources.

## Mode B structure
Verdict (Agree / Partly / Disagree / Skip; skip hype fast) → their thesis + targets → where I agree → internal contradictions (their exhibits or framework vs their rating; classification consistency; does the valuation metric actually drive the ratings?) → evidence vs claim (missing controls, untested costs, one-offs sold as structural) → buried concessions → data check (verify their key figures, list the errors) → contrarian points + my addition → falsifier + cleaner test → questions for the author → one line for the desk.

## Lenses
**Commodities:** physical vs priced (count disruptions, not monthly averages); blocked capacity ≠ lost volume; escort vs insurance; curve shape, cracks and spreads; stocks and days of cover; lags; swing levers (quotas, SPRs, OPEC+); producer hedging; seasonality.
**Rates/macro:** headline vs core; reaction function and what's priced (dated); supply and term premium; CDS → implied PD vs rating history; ratings calendar; conditional backstops (TPI/EDP, Fed put); marginal vs effective r vs g; marginal holder; reserve burn when a currency is pinned; prefer curve/RV to outright.
**Equities/sector:** substitution vs funnel interception vs subsidy; ARPA trap; membership vs cycle control; timing vs structural beat; follow the debt; re-rate for mix; low P/E on peak earnings; edge vs consensus; author's framework vs their rating.
**Cross-lens (always):** transmission chain shock → input → inflation → policy → curve → credit → FX → sectors, marking breaks; who bears the risk (rates, credit, liquidity); what survives a reversal; cleaner asset-class expression.

## After the note (one batch, in order)
1. Notes Log: one row (date, account, topic, thesis, verdict + weak spots + doc, testable call, check-by).
2. My Theses: new numbered thesis or amendment (view, for, against, what would change my mind, links).
3. Frameworks: only a genuinely new reusable structure, with a one-line example.
4. Factor-bucket check: score new trades against the book's shared drivers; flag overlap (run one or halve both); update the synthesis line.
Batch these at the end: each Project doc edit busts the cache for every chat in the Project.

## Output
Claude Doc, British spelling, short sentences, tables for data and prose for argument. Challenge Max's priors when evidence cuts against them. Final chat reply: conclusion in one line, the doc, factor-bucket flags, what changed in the three ledger docs.
