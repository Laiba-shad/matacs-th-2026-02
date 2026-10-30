Assumptions: Dates are judged against today’s date. “Missing” is not the same as “fails.” Flagged proposals are never silently ranked or dropped.

1. AI vs. rules

AI does only the reading tasks: extracting facts and quotes from messy PDF text, and rating fuzzy items such as whether a team description names a lead, crew, safety plan and monitoring plan.
Plain code does everything that must be exact: the pass/fail mandatory checks, the arithmetic for price, timeline and warranty, weighted totals, ranking, and tie-breaking.
I drew the line there because AI is good at language and unreliable at arithmetic and consistency. The code never lets AI decide who wins.

2. Consistency and explainability

The AI extracts into a fixed JSON schema at temperature 0, and every value must come with a verbatim quote and page reference. Code checks that the quote really exists in the document.
Scoring formulas are deterministic, so the same extracted facts always give the same ranking. The extraction step could vary slightly, so extractions are cached and stored per proposal version, and a re-run reuses them.
The reviewer sees a per-criterion table of extracted value, evidence quote, points awarded and the rule used, plus a one-line reason generated from those numbers.

3. Human in the loop

A reviewer confirms the extraction for any flagged item and can override any extracted value, with a mandatory comment.
The final award is always a human decision. The tool only recommends.
The audit log records the uploader, file hash, prompt version, model version, criteria version, raw AI output, extracted values, scores, every override (who, when, why) and the final decision.

4. Changing criteria

Criteria are versioned. Editing creates a new version and never changes old results.
Existing scores stay tied to their old version and are marked “outdated.”
Because extraction is stored separately from scoring, re-scoring under new weights needs no new AI calls. The reviewer sees old and new rankings side by side before adopting the new one.

5. Risks

Risk	Safeguard
Wrong extraction	Quote-required output, quote verification in code, human confirmation of key facts
Made-up facts	“Not stated” is a valid answer; the prompt forbids guessing; missing data is flagged and not scored as zero or full
Prompt injection (C)	Proposal text is treated as data only. A scan flags instruction-like text addressed to AI or reviewers. Flagged proposals are held and never auto-ranked. The AI cannot change scores, because code scores
Bias	Scoring uses only the admin’s criteria. Company names are hidden from the scoring step where practical, and ranking is auditable
Vague or conditional claims (B, D)	Rules for “to be confirmed” and missing values route them to ineligible or flagged
Cost	One extraction call per proposal; re-scoring is free; caching; page and size limits on uploads
Data privacy	Uploads are restricted to authorised users, with a retention policy
