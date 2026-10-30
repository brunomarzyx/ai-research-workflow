---
name: model-router
description: "Picks the right model, effort and workers for a task before work starts, using Max's routing table, and says in one line if the current chat is on the wrong model. Use at the start of any multi-step task (note, pitch, application, outreach batch, vault cleanup, data pull, PDF digest) and whenever Max asks which model to use, how to route a task, or how to cut token use. Do NOT use for one-line questions."
---

# Model Router

**Outcome:** every task runs on the cheapest model that does it well. Quality first, then token cost, then speed.

**Done when:** the task has a chat model, effort, worker list and checker, and if the current chat model is wrong, Max has been told in one line, before any work starts. Then hand over to the task skill.

## Key fact
A skill can't switch the chat model. Max picks the chat model; agent files fix the worker models. Workers run in Cowork and Claude Code only. In plain chat, do worker steps inline and briefly.

## Routing table
| Task | Chat model · effort | Workers (model · effort) | Max output | Checked by |
|---|---|---|---|---|
| Quick fact / one number | Haiku | none, 1 search | 3 lines | source link |
| "gm" brief read-out | Haiku | none | 5 lines | none |
| Generate morning brief | Sonnet | web-researcher only for a gap | 1 page | none |
| Quick market take | Sonnet | none, ≤3 searches | 300 words | sourced or "estimate" |
| Research note | Opus · high | web-researcher S·med ×≤2, fin-data-puller H·low | 2 pages | red-team S·high, fact-checker H·med |
| Markets note | Opus · high | as above + pdf-summariser H·low | Claude Doc | red-team, fact-checker |
| Stock screen | Sonnet · med | none | 9 lines | Max |
| Full stock pitch | Opus · high | fin-data-puller, pdf-summariser, model-builder, red-team | outline + model | fact-checker, maths in code |
| Cover letter / written answers | Opus · med | web-researcher once per firm | 1 page | LFIS checklist |
| CV tweaks | Sonnet · med | none | 5 lines | Max |
| Interview / HireVue prep | Sonnet · med (Opus for superdays) | none | ≤60s per answer | Max out loud |
| Outreach batch | Sonnet · med | web-researcher ×2 | 60–100 words/email | script word count |
| Follow-ups / reply drafts | Haiku | none | 50 words | Max |
| Council quick / full | Opus · high | full: 5 advisors S·med in waves 2+2+1 | 8 bullets each | Chairman |
| Long PDF / filing | any | pdf-summariser H·low | 400 words + pages | fact-checker if quoted |
| Vault upkeep | Haiku | vault-updater H·low | diff lines | Max approves deletes |
| Data pull | any | fin-data-puller H·low | table | fact-checker on final only |
| System / skill design | Opus · high | none | as needed | Max |

## Delegation rules
- Delegate only mechanical work that is bulky (would pull several pages into the main thread) or parallel. Small lookups stay inline. Reason: each subagent starts cold and re-reads its setup.
- Brief = task + paths + return format + "Done when". Never the chat history.
- Workers return a table or ≤500 words; bulky output to `_scratch/`. Max 2 in parallel, no nesting.
- Opus keeps judgement and the final voice: thesis, valuation calls, verdicts, letters.

## Cache rules
Stable instructions first, variable input last. Same brief template every time. Batch Project doc and vault edits at the end of a task (a doc edit busts the cache for every chat in the Project).

## Output
One line before the work: `Route: <chat model · effort> | workers: <list> | check: <checker>`. Add `Switch to <model> for this` only if the current chat model is wrong.
