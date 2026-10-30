# matacs-th-2026-02

**Full name:** Laiba Irshad
**Reference:** MATACS-TH-2026-02
**Time actually spent:** About 2 hours

## How I used AI
I used two AI tools (Claude and another assistant) to draft the write-up, the extraction prompt and the flow diagram, and I checked every output against the brief myself. The first AI's draft missed the traps in the sample set: the instruction hidden in C aimed at automated reviewers, B's licence being subcontracted and unconfirmed, and D's missing timeline. I re-read the proposals, found them, and changed the design so C is flagged, B is ineligible and D is flagged. I also corrected hard-coded scoring thresholds, since the brief says criteria must come from admin screens.

## Assumptions
- A proposal with missing information (D) is flagged for human review, not rejected.
- Proposal C is held for review and not ranked automatically.

## Files
- [WRITEUP.md](WRITEUP.md): answers to the five questions
- [PROMPTS.md](PROMPTS.md): extraction and reason-writing prompts
- [ranking.json](ranking.json): expected ranking of proposals A-E
- [diagram/flow.png](diagram/flow.png): process flow from upload to ranked output

No prototype is included.
