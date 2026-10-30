---
updated: 2026-10-30
---
# How my routing works

**Goal:** every task runs on the cheapest model that does it well. Quality first, then token cost, then speed.

## The one thing to understand first
A skill cannot change the model it runs on. The chat (or Cowork session) runs on whatever I pick in the model picker. So routing happens in two places only:
1. **Me, at the start of a chat:** pick the chat model from the table below. Opus only when the chat needs judgement.
2. **Subagents:** each agent file pins its own model and effort. The orchestrator hands mechanical work down to them.

Subagents run in Cowork and Claude Code, not plain chat. In plain chat the skill does those steps itself, briefly.

## Default mode: chat with Opus, Opus hands down
I stay in one Opus chat. Opus decides the route per step and does only the judgement: what to do, the final words, the verdict. Every mechanical step (listing or moving files, data pulls, vault edits, PDF digests, form filling, web lookups) goes to a worker via the Agent tool with `model` set (haiku for mechanical, sonnet for research/editing/red-team), even when it's small, as long as it takes more than ~2 tool calls. Opus writes one line before each hand-off: `→ Haiku: <task>`. In Claude Code, run `/model opusplan` so execution drops to Sonnet automatically.

## Roles
| Role | Model | Does | Never does |
|---|---|---|---|
| Orchestrator | Opus | plans, judges, writes the final piece in one voice, decides | fetching, formatting, bulk reading |
| Researcher / red-team / editor | Sonnet | web research, adversarial review, humanize and trim | final calls, the thesis |
| Fetch / verify / summarise / file | Haiku | data pulls, fact-checks, PDF digests, vault edits | analysis, opinions |

## Routing table
| Task | Pick chat model | Workers (model · effort) | Max output | Checked by |
|---|---|---|---|---|
| Quick fact / one number | Haiku | none, 1 search | 3 lines | source link |
| "gm" morning brief read-out | Haiku | none | 5 lines | none |
| Generate the morning brief (scheduled) | Sonnet | web-researcher only if a gap | 1 page | none |
| Quick market take (<300 words) | Sonnet | none, ≤3 searches | 300 words | sourced or "estimate" |
| Research note (LinkedIn / interview) | Opus · high | web-researcher S·med ×≤2, fin-data-puller H·low | 2 pages | red-team S·high, fact-checker H·med |
| Markets note (desk note + ledger) | Opus · high | same as above, pdf-summariser H·low for broker notes | Claude Doc | red-team, fact-checker |
| Stock screen (3 names) | Sonnet · med | none | 9 lines | Max |
| Full stock pitch | Opus · high | fin-data-puller H·low, model-builder, red-team S·high | deck outline + model | fact-checker H·med, script maths |
| Cover letter / application answer | Opus · med | web-researcher S·med once per firm (cached brief) | 1 page | LFIS checklist, Max |
| CV tweaks | Sonnet · med | none | 5 lines | Max |
| Interview / HireVue prep | Sonnet · med (Opus for superdays) | none (uses Firm Brief) | ≤60s per answer | Max out loud |
| Outreach batch | Sonnet · med | web-researcher S·med ×2 for targets | 60–100 words/email | script word count + source URL |
| Follow-ups / reply drafts | Haiku | none | 50 words | Max |
| Council (quick) | Opus · high | none | 1 screen | Chairman |
| Council (full) | Opus · high (Chairman only) | 5 advisors S·med, 2 at a time | 8 bullets each | cross-review |
| Long PDF / filing / broker note | any | pdf-summariser H·low | 400 words + page refs | fact-checker if numbers get quoted |
| Vault upkeep (dates, Inbox, rows) | Haiku | vault-updater H·low | diff summary | Max approves deletes |
| Data pull | any | fin-data-puller H·low | table | fact-checker on final draft only |
| System / skill design | Opus · high | none | as needed | Max |

## Context rules
- Index first, then only the 1–2 notes the task needs. Never load a folder.
- A subagent gets the task, the paths it needs and the output format. Nothing else, not the chat history.
- Bulky output goes to `_scratch/`. The orchestrator reads the summary, opens the file only if it must.
- Delegate any mechanical step that needs more than ~2 tool calls (see Default mode). Keep one-or-two-call lookups inline: each subagent starts cold, so below that it costs more than it saves.
- Max 2 subagents in parallel. No nesting.

## Cache rules
- Stable text at the top (skill rules, agent instructions), variable input last (ticker, question, paths).
- Same brief template for every subagent call, so the prefix repeats.
- Don't edit Project docs or instructions mid-session. Changing a doc busts the cache for every chat in the Project. Batch ledger updates at the end.

## Instruction rules
- Outcome first: one line on what "good" looks like.
- Every skill and agent ends with **Done when** so it stops instead of padding.
- Absolutes only for hard rules, each with its reason (sourcing, compliance, never overwrite notes).

## Subagent brief template
```
[stable] Role and rules live in the agent file. Do not restate them.
TASK: <one sentence>
INPUTS: <paths or tickers>
RETURN: <table | ≤N words> to chat; full output to <_scratch/path>
DONE WHEN: <condition>
```

## Measuring it
See `iteration/usage-log.md`. Log usage per task for two weeks, compare against the Opus-only baseline.
