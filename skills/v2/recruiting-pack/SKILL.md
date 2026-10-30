---
name: recruiting-pack
description: "Produces sales & trading and markets research internship materials: LFIS-rule cover letters, CV bullet tweaks, firm and desk briefs, HireVue and interview prep with model answers. Use whenever the user mentions an application, cover letter, CV, HireVue, superday, assessment centre, interview, a bank or desk he's applying to, or why markets / why this firm. Do NOT use to write stock pitches or market notes (stock-pitch, research-note), or for cold outreach emails (network-outreach)."
---

# Recruiting Pack v2 (S&T / Research)

Start the reply with `Using: recruiting-pack`.

**Outcome:** material that gets Max to the next round: specific to the firm, sourced, in his voice, nothing that restates the CV.

**Done when:** the requested part (A, B or C) passes its checklist below and the campaign row is updated.

## Route
| Part | Chat model | Workers |
|---|---|---|
| Firm brief (only if `30 Resources/Firm Briefs/<Firm>.md` is missing) | any | web-researcher (Sonnet) once; saves the brief |
| A. Cover letter / written answers | Opus · medium | none (one voice) |
| B. CV tweaks | Sonnet · medium | none |
| C. Interview / HireVue prep | Sonnet · medium (Opus for superdays) | none |
| Save | any | vault-updater (Haiku) |
Plain chat: one short web search instead of web-researcher.

## Context (minimum)
`10 Projects/Summer 2027 Internship Campaign.md` (already applied/rejected? referral?), `30 Resources/Firm Briefs/<Firm>.md` if it exists. Add `30 Resources/Application Playbook.md` for A, `30 Resources/People.md` only if a contact at the firm might exist, latest Morning Brief only for C.

## A. Cover letter (LFIS rules)
- 3–5 paragraphs. Formal address with firm location; named recruiter if known, else "Dear Sir/Madam". Role and how Max heard of it.
- Middle: why this firm (one specific, sourced fact), why this role, evidence matched to the job description. Expand on what the CV doesn't show.
- Close: thanks, CV attached, contact details. "Yours sincerely" if named, "Yours faithfully" if Sir/Madam.
- Evidence order: trading record (500+ trades, 2% risk cap, US indices/crude/FX) → Jefferies DIFC MENA equities week → LSMF Real Assets Sector Analyst → BofA / BGC → research notes (Hormuz, France).
- Checklist: firm name correct everywhere; matches CV font; file name `Max_Brenner_Cover_Letter_<Firm>_<Role>`; humanize pass; never mention Pete when contacting Investec.

## B. CV tweaks
Main CV = Goldman Sachs version (LFIS template). Only the 3–5 line changes that map to this job description. LSMF title: "Real Assets Sector Analyst".

## C. Interview / HireVue prep (each answer ≤60s spoken)
1. Why S&T (or research): personal, links trading record to desk work.
2. Why this firm: two sourced reasons.
3. A market view: today's Morning Brief soundbite + what would change your mind.
4. A stock: current pitch, 3 pillars + catalyst.
5. Failure / team / pressure: STAR, real examples only (Jefferies, Altius8, LSMF, trading drawdowns).
6. 5 technical questions for this desk with crisp answers.
7. 3 smart questions to ask.
HireVue: good light, camera level, dressed well, one practice on camera.

## Hard rules
- "Why this firm" facts must be sourced. Reason: generic praise is the most common cover-letter fail in the LFIS guidance.
- Real examples only, never invented. Reason: interviewers probe them.

## Save
vault-updater: firm's row in the campaign note (stage, next step, date), `updated:`.
