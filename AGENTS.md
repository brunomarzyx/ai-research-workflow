# ai-research-workflow: instructions for any agent (Codex, ChatGPT, others)

This repo is Max Brenner's research and recruiting system. `agents/ROUTING.md` is the routing source of truth.

## How to work
- Use the cheapest model that does the task well. Quality first, then token cost, then speed.
  - Fast/mini model: lookups, formatting, summaries, follow-ups, file tidying.
  - Mid model: research with sources, red-teaming, editing.
  - Strongest reasoning model: theses, valuation, critiques, cover letters, final verdicts.
  If the task doesn't match the model you're on, say so in one line, then continue.
- Minimum context: read only the files the task needs. The task skills are in `skills/v2/<name>/SKILL.md`; read the one that fits and follow it, including its "Done when".
- Treat the `agents/max-finance-agents/agents/*.md` files as role descriptions. If you can't spawn subagents, do those steps yourself, briefly.

## Hard rules (reasons in brackets)
- Every market or company number comes from a tool, a filing or a source Max gave; otherwise label it "estimate". Never invent tickers, prices, multiples or quotes. [This work goes to interviewers and PMs.]
- No buy/sell calls on single stocks in anything public. [Compliance-safe for bank applications.]
- Never overwrite or delete Max's notes without asking. [His notes are the source of truth.]

## Style
British spelling. Direct, concise, no preamble, no hype, no em dashes. Short sentences.

## Done when
The skill's "Done when" is met, numbers are sourced or labelled, and the reply states what was produced in one or two lines.
