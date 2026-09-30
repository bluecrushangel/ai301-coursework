# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

bluecrushangel

---

## Posted upstream

**Claim comment**
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54#issuecomment-5901596052
I'd like to work on this issue. I'll reproduce the example from the issue body directly (ResumeParser().parse() on the leading-whitespace text) and run the related tests in tests/unit/test_resume_parser.py — test_parse_single_column_resume_text, test_parse_resume_no_work_experience, and test_detect_sections, plus any others marked xfail for this issue — against current main in my own fork. I'll post a repro report with my environment, exact steps, and observed output once I've run it, independent of the reports already posted here.

I'm working with AI assistance as part of AI 301 coursework.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54#issuecomment-5901636064
Repro report for #54: reproduced.

**Environment**
- Windows 11 (Git Bash / MINGW64)
- Python 3.14.3
- Commit: `f89c06fc3ff292df2a04a39ac51319d32a76b779` (my fork of `main`)
- Installed via a plain virtualenv, no Docker: `python -m venv .venv`, `.venv/Scripts/pip install -e ".[dev]"`. I did not run `docker compose up` or `make setup` — the parser unit tests don't touch the database or backing services, which I confirmed by running the test suite below with no Docker services running and seeing no connection errors.

**Steps**
1. From the repo root: `python -m venv .venv`
2. `.venv/Scripts/pip install -e ".[dev]"`
3. Saved the reproduction from the issue body as `repro54.py`:
```python
from ingestion.parsers.resume_parser import ResumeParser
r = ResumeParser()
res = r.parse('\n    John Smith\n    john@example.com\n\n    Education:\n    - B.S. Computer Science\n\n    Skills: Python\n')
print(res.metadata['detected_sections'])
```
4. `.venv/Scripts/python repro54.py`
5. `.venv/Scripts/python -m pytest tests/unit/test_resume_parser.py -rx -q`

**Observed**
Step 4 printed:

[]

matching the issue's reported output exactly (expected `Education`, `Skills`; got an empty list).

Step 5 gave `5 passed, 5 xfailed`. All five xfailed tests are marked with the reason `"issue #54: resume section detection fails on leading whitespace"`:
- `test_parse_single_column_resume_text`
- `test_parse_resume_no_work_experience`
- `test_parse_markdown_resume`
- `test_detect_sections`
- `test_strip_markdown_syntax`

The issue body names only the first three of these; the repo marks two additional tests (`test_parse_markdown_resume`, `test_strip_markdown_syntax`) as xfail for this same issue.

**Outcome**
Reproduced: indented resume text produces an empty `detected_sections` list, matching the issue exactly. No discrepancy between expected and observed behavior.

I'm working with AI assistance as part of AI 301 coursework.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

18/20
18/20 - saved run

**Package analysis**

pkg-05. Gold label: accept. My rubric's verdict: reject, failing repro-steps-runnable. My rubric requires steps to be exact commands/inputs "with zero guessing." This package's steps were evidently specific enough for the gold grader to consider them followable, but my check's evidence column or pass condition was strict enough to read them as under-specified — likely because it expected a literal command string rather than accepting a clearly-described procedural step as sufficient. This is a case where my check is calibrated tighter than the gold standard on what counts as "runnable."

**Check rationale**

"Pass if the steps are exact commands/inputs a stranger could run with zero guessing (not descriptions of what to do)." (repro-steps-runnable)

This reads this way because a rubric check whose evidence can't be pinned to something concrete is unenforceable — "clear steps" as a pass condition would let any confident-sounding paragraph through. I chose to require literal commands specifically to close that gap, at the cost of being stricter than a human reader might be about steps that are correct in substance but phrased as description rather than command.

**Trade-offs**
Trade-off: repro-steps-runnable's strict "exact commands, zero guessing" bar cost me two packages the gold label accepted — pkg-05 and pkg-12 — both failing this same check. I chose not to loosen it, since loosening it risks accepting vaguer steps elsewhere in the 4 "unfollowable-comms" category packages, which I did match correctly (3/3). I accept missing pkg-05 and pkg-12 as the cost of keeping that category clean.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
