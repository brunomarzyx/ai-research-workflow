# ai-research-workflow: instructions for Claude Code / Cowork

Read `agents/ROUTING.md` before any multi-step task. It is the routing source of truth; this file only points to it.

- Open every multi-step task with one line: `Route: <chat model · effort> | workers: <list> | check: <checker>`. If this session is on Opus and the task is mechanical, say so.
- Workers live in `agents/max-finance-agents/agents/`. Brief them with the template in ROUTING.md: task, paths, return format, Done when. Never pass chat history.
- Max 2 subagents in parallel, no nesting. Bulky output to the vault `_scratch/`.
- Every market or company number from a tool, filing or given source, else "estimate". Reason: everything here ends up in front of interviewers or PMs.
- Skills v2 are in `skills/v2/`; each ends with a "Done when". Stop when it's met.
- Never edit `.obsidian/`, never overwrite or delete vault notes without asking.
