---
name: research-note
description: "Writes a 2-page macro or markets research note in Max's house style for interviews and LinkedIn: call, why now, transmission, pricing vs view, scenarios, what would change my mind. Use for a market view, macro note, central bank, rates, FX, commodity or index outlook, data-release reaction or cross-asset idea, even if he just says what's your view on. Do NOT use for a full desk note with trades table and ledger updates (markets-note), a single company (stock-pitch) or applications (recruiting-pack)."
---

# Research Note v2

Start the reply with `Using: research-note`.

**Outcome:** a 2-page note an S&T interviewer would respect: a clear call, priced vs our view, and what would change my mind. Every number sourced or labelled.

**Done when:** all 8 sections are filled, fact-checker shows no open ⚠️/❌, the 30-second verbal version and 1-line hook are written, and the Research Library row is added.

## Route (chat on Opus · high; see agents/ROUTING.md)
| Step | Who | Returns |
|---|---|---|
| 1. Split topic into ≤3 sub-questions | Opus | list |
| 2. Research each | web-researcher (Sonnet), 2 in parallel | ≤400 words each |
| 3. Market levels (curve, futures, FX, crude) | fin-data-puller (Haiku) | table |
| 4. Write the note | Opus, one voice, never delegated | draft |
| 5. Attack it | red-team (Sonnet) once | ≤500 words → "What would change my mind" |
| 6. Humanize + trim if >800 words | editor (Sonnet); inline if shorter | edited draft |
| 7. Verify | fact-checker (Haiku) once on the final | table; fix every ⚠️/❌ |
| 8. Log | vault-updater (Haiku) | diff line |
Quick take: skip 5–8. Plain chat (no subagents): do 2, 3 and 7 yourself, briefly.

## Context (minimum)
`00 Context/Index.md`, then `20 Areas/Research Library.md` (don't repeat a past note). Add `30 Resources/Analytical Frameworks.md` only if a framework fits. Morning Brief only if relevant.

## Structure (2 pages max)
1. **Title + one-line call** (the view, not the topic).
2. **Why now:** the trigger, dated.
3. **Transmission:** rates → FX → commodities → equities; which instrument reacts and why.
4. **Priced vs our view:** with numbers (curve, futures, implied moves, positioning).
5. **Scenarios:** base / bull / bear, odds labelled "my judgement", market level in each.
6. **What would change my mind:** 2–3 observable signals.
7. **Trade expression (analysis, not advice):** how a desk might express it; risks.
8. **Sources:** primary first.
Then: 30-second verbal version and a 1-line X/LinkedIn hook.

## Hard rules
- Every number from a source found this session or labelled "estimate". Reason: interviewers check, and one wrong level sinks the note.
- No buy/sell calls on single stocks, no personal positions. Reason: compliance-safe for LinkedIn and bank applications.
- Frameworks (deal-then-break, oil→rates migration, structural fear vs cyclical data) only where they genuinely fit.

## Save
vault-updater: add a row to `20 Areas/Research Library.md` (note, date, file) and set `updated:`.
