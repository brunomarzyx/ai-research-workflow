---
name: network-outreach
description: "Finds people and firms to contact (funds, brokers, prop shops, research boutiques, alumni) and drafts cold emails or LinkedIn notes in Max's voice, loaded as Gmail drafts with a tracker. Use for outreach batches, follow-ups and reply drafts. Do NOT use for formal applications or cover letters (recruiting-pack)."
---

# Network Outreach v2

Start the reply with `Using: network-outreach`.

**Outcome:** the highest reply rate per minute of Max's time. He only reviews and hits send.

**Done when:** every draft is in Gmail with a verified address and source URL, all word counts are under 105 by script, the tracker CSV is saved, and Max has the send plan.

## Route (chat on Sonnet · medium; this is templated work)
| Step | Who | Returns |
|---|---|---|
| 0. Exclude list from Gmail sent, bounces, replies | chat model | list |
| 1. Find targets, split by city/segment | web-researcher (Sonnet), 2 in parallel | pipe table per split |
| 2. Pick the ask per firm | chat model | |
| 3. Build drafts from template + hooks | script (JSON → word counts → Gmail drafts) | counts |
| 4. Tracker | script | CSV |
| Follow-ups / reply drafts | Haiku chat | ≤50 words |
Plain chat: research the targets yourself in smaller batches.

## 0. Before starting
- Load my-writing-style; every draft is Register A.
- Gmail: `in:sent newer_than:60d internship OR coffee OR enquiry` → EXCLUDE list; check `from:postmaster` bounces and replies; note what worked.
- At most one question: channel, firm types, cities, batch size. Default: email, 40–60 firms.

## 1. Targets
Table: firm | type | city | size (small <75 / large) | name | role | email | source URL | hook.
Email only if seen verbatim on a public page (contact/careers page, exchange directory, regulator register, PDF); Cloudflare-hidden addresses don't count.
Best sources: EEX broker directory, CME find-a-broker, careers pages, DFSA/FSRA registers, SEC Form ADV.
Hook = one specific, true fact from the page read. Never claim Max read their research unless he said so.

## 2. The ask (one per email)
- Small shop: internship ("Would X consider me for summer 2027 or an off-cycle stint? Happy to send my CV.")
- Large firm / named desk person: 15-minute call ("Would you have 15 minutes for a call in the next few weeks? I'd like to hear how you got into [area].")
- Grad-scheme firm: "Is there any route in for a second-year before the graduate programme?"
- Overseas with visa barrier: call only, "I'm UK-based, so this isn't a job request."

## 3. Email standard (60–100 words before sign-off)
`Dear Mr X,` or `Dear [Firm] team,` (+ "Could you pass this to whoever runs X?") → hook (1–2 sentences) → proof, 2 lines max, matched to the reader (second-year Econ & Finance at Loughborough; own-account trading in crude, indices and FX since 2022; BGC sales trading; BofA Merrill equities; Jefferies MENA equities week in the DIFC, lead with it for Gulf firms; Hormuz and French debt notes only when the hook is research) → one ask → Kind regards, / Max Brenner / 07734 695507 / linkedin.com/in/max-brenner-2646a5333.
Subject: `Internship enquiry: [area] (Loughborough student)` or `15 minutes on [area]? (Loughborough student)`.
No em dashes, no "I hope this finds you well", no "passionate".

## 4. Deliver
Drafts from a script; template changes after drafts exist → update_draft by ID, never duplicates. No attachments (connector can't attach local files); offer the CV. Tracker: Firm, City, Ask, To, Subject, Email source, Sent date, Follow-up due, Status, Notes. Send plan: 10–15 a day, so replies stay manageable and Gmail doesn't flag him.

## 5. Follow-up
One follow-up after ~7 days, <50 words, same thread, one new thing or a polite bump. Never restate the full ask, never apologise. Replies: log in tracker, update the person's memory file, offer a reply with 2–3 call slots.

## 6. LinkedIn
Max filters the Loughborough alumni page (company, role keywords, location) or shared interests, pastes 30–50 profiles. One note each (<300 chars connect, <75 words DM) into a sheet. Shape: shared link first, one line on Max, the 15-minute ask. Connect the same day as emailing named people; it lifts reply odds and costs nothing.

## Hard rules
- An email address only if seen verbatim on a public page, with the URL logged; never pattern-guess. Reason: bounces damage Max's sender reputation.
- Never use LinkedIn automation tools (Waalaxy, Expandi, Dripify). Reason: they breach LinkedIn's terms and risk his account.
- Word count checked by script, not by eye. Reason: length is the main reply-rate lever.
