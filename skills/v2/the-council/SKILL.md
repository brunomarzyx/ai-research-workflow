---
name: the-council
description: "Runs a five-advisor council (blind cross-review and a Chairman verdict) on a decision, thesis, trade or research note before acting on it. Use when Max asks to stress-test, pressure-test or council a decision. Do NOT use for a routine bear case on a draft (red-team agent does that)."
---

# The Council v2

Start the reply with `Using: the-council`.

**Outcome:** find what Max is missing, then commit to Proceed, Amend or Kill. The council exists to challenge, not approve.

**Done when:** the verdict, what decided it, the unresolved disagreement, changes, 1–3 dated Monday-morning actions and a dated kill switch are all written.

## Route (chat on Opus · high)
- **Quick council (default):** one run on the chat model. Honest caveat: one model plays every role, so blindness is approximate.
- **Full council (when Max says "full council"):** each advisor runs as a separate Sonnet · medium subagent with only the decision + context (same brief, so the prefix caches). Max 2 in parallel: run in waves 2 + 2 + 1. Cross-review and Chairman stay on Opus.

## 0. Set-up
- Restate the decision in one line. Vague → turn it into act or don't, size, structure, timing.
- Markets decisions: read `claude/My Theses.md`, `claude/Notes Log.md`, `claude/Frameworks.md`; check overlap with live trades and factor buckets; search any current level an advisor relies on.
- Non-markets: only the context given, plus profile where relevant.

## 1. Five advisors (4–8 bullets each, at least one point no one else makes)
1. **Contrarian:** what fails; bear case, worst scenario, crowding, what's already known. For a note: weakest claim and who happily takes the other side.
2. **Assumption-Ripper:** every assumption, explicit and hidden; facts vs estimates vs judgement; the single assumption that kills the thesis; dates, basis shifts, stale numbers.
3. **Expansionist:** missed upside; better expression (RV, curve, options, cleaner asset), second-order winners, bigger version, adjacent theses.
4. **Outsider:** obvious plain-language questions only. What is the jargon hiding?
5. **Executor:** Monday morning: first action, entry, size vs book, stop/invalidation, catalyst dates; or the condition that triggers action.

## 2. Blind cross-review
Anonymise and shuffle into Responses A–E. Each advisor reviews the other four on ideas only: strongest point, weakest point, one thing it changes in their own view. Then rank: which response costs most to ignore?

## 3. Chairman's verdict (does not average)
Verdict (Proceed / Amend / Kill) · What decided it (+ strongest argument overruled and why) · Unresolved disagreement + evidence that would settle it · Changes · Monday morning (1–3 dated actions) · Kill switch (observable signal + check-by date).

## 4. After the verdict (markets decisions)
Add verdict + kill switch to the Notes Log row (or a new "Council" row); update My Theses if something changed; flag factor-bucket overlap. One batch at the end.

## Output
Chat by default: advisors compact, cross-review as a short table, verdict in bold. Claude Doc only if asked or the decision is large. British spelling. Agreement has to be earned.

## Hard rule
Current levels from a search this session, never memory. Reason: a council built on a stale level reaches the wrong verdict confidently.
