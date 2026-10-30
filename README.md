# ai-research-workflow

How I use AI for markets research and recruiting. I'm a second-year Economics & Finance student at Loughborough, I've traded US index futures, FX and crude on my own account since 2022, and I sit on the Loughborough Student Managed Fund as a Real Assets Sector Analyst. Everything in this repo is what I actually run day to day, not a course project.

## What's in it

| Folder | What it is |
|---|---|
| `skills/v2/` | Seven Claude skills I wrote: `research-note`, `markets-note`, `stock-pitch`, `recruiting-pack`, `network-outreach`, `the-council`, `model-router` |
| `agents/max-finance-agents/` | A Claude plugin with seven worker subagents (data puller, fact-checker, PDF summariser, vault updater, web researcher, red team, editor) |
| `agents/ROUTING.md` | Which model does which job, and why |
| `prompts/` | My Claude preferences and the same setup ported to ChatGPT |
| `iteration/usage-log.md` | Where I measure whether the routing actually saves tokens |

## How it works

One Opus model orchestrates. It plans, makes the judgement calls and writes the final piece in one voice. Mechanical work goes down to cheaper workers: Haiku pulls data, checks every number and summarises PDFs; Sonnet does web research, red-teams the thesis and edits. Max two workers in parallel, no nesting, and each one gets only the task, the file paths and the output format, never the chat history.

The rule I care most about: every market or company number has to come from a tool, a filing or a source I gave it. If it can't, it gets labelled "estimate". Whatever comes out of this ends up in front of an interviewer or a PM, so a made-up multiple is worse than no number.

Context comes from an Obsidian vault I use as a second brain (theses, notes log, firm briefs, morning briefs). Skills read the index first and then only the one or two notes the task needs.

## What I've made with it

- A Strait of Hormuz note (Sep 2026, updated Oct 2026) tracing the crude disruption through freight, diesel cracks and CPI to long-end yields
- A France sovereign-debt note (Oct 2026) on debt-to-GDP, interest costs and the risk OATs reprice from core to semi-core
- LSMF stock pitch work off a 135-name real assets screen

Both notes are on my LinkedIn.

## Things I've learned building it

- A skill can't change the model it runs on. Routing only happens in two places: the model I pick for the chat, and the model each subagent file pins.
- Subagents aren't free. Each starts cold and re-reads its setup, so a two-line lookup is cheaper done inline. I only delegate work that is mechanical and either bulky or parallel.
- Every skill ends with a "Done when" line. Without it the model keeps going and pads.
- Stable text at the top of a prompt, variable input last, so the prompt cache actually gets hit.

I dictate most of my prompts with Wispr Flow; my rough guess is it saves 20–30 minutes of typing a week (not measured).

## Using it

The skills install as Claude skills; the plugin installs in Claude Code or Cowork from `agents/max-finance-agents/`. `CLAUDE.md` and `AGENTS.md` point Claude Code and other agents at the routing table. Setup for ChatGPT is in `prompts/chatgpt/SETUP.md`.

Max Brenner · [LinkedIn](https://www.linkedin.com/in/max-brenner-2646a5333)
