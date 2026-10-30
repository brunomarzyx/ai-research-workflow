# Putting the routing system into ChatGPT

ChatGPT can't run my Claude agents or switch models itself. The goal is the same rules, the same skills as reference, and a one-line warning when I'm on the wrong model.

## 1. Custom instructions (all chats)
Paste the two boxes from `../chatgpt-custom-instructions.md`.

## 2. A ChatGPT Project for this work
- Instructions: paste `project-instructions.md` (next to this file).
- Files: upload `AGENTS.md`, `agents/ROUTING.md` and the `skills/v2/*/SKILL.md` files I use there (research-note, stock-pitch, recruiting-pack, markets-note, the-council). Skip network-outreach; it depends on my Gmail connector in Claude.

## 3. GitHub (optional, keeps it in sync)
If GitHub is connected in ChatGPT, point it at `brunomarzyx/ai-research-workflow` and ask it to read `AGENTS.md` first. Codex reads `AGENTS.md` automatically when working in the repo. Uploaded Project files don't update themselves; re-upload after I change a skill, or rely on the GitHub link.

## Known limits
- No subagents: ChatGPT does the worker steps itself, so savings come from model choice and lean context only.
- Exact model names and limits change; check the model picker rather than trusting names in these files.
