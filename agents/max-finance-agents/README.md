# max-finance-agents v0.2
Workers for the Opus orchestrator. Routing rules: ../ROUTING.md
- fin-data-puller (Haiku, low): sourced data tables
- fact-checker (Haiku, medium): verifies every number once on the final draft
- pdf-summariser (Haiku, low): long PDF / filing / broker note -> 400-word digest with page refs  [new]
- vault-updater (Haiku, low): dates, Inbox appends, ledger rows; never overwrites or deletes  [new]
- web-researcher (Sonnet, medium): one question, cited sources
- red-team (Sonnet, high): bear case + hardest Q&A
- editor (Sonnet, medium): humanize and trim a long draft in Max's voice  [new]
Run in Cowork and Claude Code, not plain chat. Max 2 in parallel, no nesting.
