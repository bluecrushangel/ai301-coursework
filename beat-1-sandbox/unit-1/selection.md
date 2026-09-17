# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54",
    "checks": [
      {"name": "Community alive", "grade": "pass", "evidence": "Last push 2026-09-16T21:48Z; main commits 2026-09-16 (x3) by Aburke225 — within 30 days of today"},
      {"name": "Repo in use", "grade": "pass", "evidence": "No releases, but last push 2026-09-16 is within the last 6 months"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "No 'Operating system' field in the issue body; field absent, so passes"},
      {"name": "Issue is unclaimed", "grade": "pass", "evidence": "assignees: (none); timeline has no cross-referenced/connected events and the repo has zero PRs"},
      {"name": "no-policy-ban", "grade": "pass", "evidence": "docs/CONTRIBUTING.md covers branches, commits, CI and xfail markers; no ban on AI-generated/AI-assisted contributions"}
    ],
    "verdict": "accept"
  }
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

9/20
17/20
18/20

**Issue analysis**

My rubric's verdict: accept. Gold label: reject.

My rubric accepted this issue because every other check genuinely passes: the repo is active (repo-in-use), a maintainer replies quickly (responds-to-issue, e.g. 0.3 days on a recent issue), it's unclaimed (not-already-claimed — no assignees, no linked PRs), and the ask itself is small and bounded (scope-bounded — one UI progress-bar tweak, not an umbrella issue).

The miss is in no-policy-ban. BookWyrm's CONTRIBUTING.md states under "Generative AI": "We do not accept AI-generated code or documentation." That's an outright ban, not a condition like disclosure or testing — and evidence-guide.md is explicit that an outright ban is a hard fail regardless of how strong the issue looks on every other axis. My no-policy-ban check should have caught this and didn't, which means either the check isn't reading the contribution-policy line correctly, or its pass condition isn't strict enough to catch this exact phrasing.

category floor unmet: no match in policy for issue-12

**Check rationale**

Check rationale: no-policy-ban

|no-policy-ban|contribution policy line under Repo facts (eval mode); CONTRIBUTING.md, AI_POLICY.md or similar in the repo root (live mode)|repo's contribution policy does not outright ban AI-generated/AI-assisted contributions|required|

This check covers the fifth surface named in evidence-guide.md: whether the repo's own rules allow the way I actually work. An issue can pass all four lecture families — maintainer alive, repo in use, scope fits a newcomer, nobody else on it — and still be a dead end if the maintainers have said outright that they won't take AI-assisted contributions. Since my workflow is AI-assisted, that's not a soft preference, it's a hard blocker specific to how I'd actually be submitting work.

I set the weight to required rather than preferred because a policy ban isn't something that should just lower an issue's rank — it should remove it from consideration entirely, the same way an already-claimed or unresponsive-maintainer issue would. Submitting against a stated ban wastes a maintainer's time regardless of how good the issue otherwise looks.

The pass condition is deliberately narrow — it only fails on an outright ban, not on conditions. evidence-guide.md draws this distinction explicitly: disclosure requirements, "you must personally understand and test every change," and human-review requirements are terms to follow, not reasons to reject the issue. Most policies I'll encounter are this kind, and gating on them too would eliminate a lot of otherwise-good issues for no real reason. Silence (no policy stated at all) also passes, per the same guidance — most repos say nothing, and that isn't itself a restriction.

**Trade-offs**

Trade-offs: no-policy-ban

This check gives up perfect precision on how strictly it reads a policy statement's exact wording. On issue-12 (BookWyrm), the contribution policy states plainly, "We do not accept AI-generated code or documentation" — an unambiguous outright ban by evidence-guide.md's own definition. My rubric still graded this issue accept (gold: reject), meaning no-policy-ban did not catch it in that run.

I re-ran that issue in isolation with --only issue-12 to confirm this wasn't a fluke from a batched run, and it reproduced the same miss. So the check as written is not reliably distinguishing an explicit ban from milder conditional language (like "disclose AI use" or "you must test your changes"), even though the pass condition's intent is to treat only the former as a fail. That's the concrete case I accept it will miss until I tighten the pass condition's wording — likely by having it quote or paraphrase the specific policy line it read, the same way responds-to-issue and scope-bounded require a one-line fact rather than a bare verdict, so a grading pass can catch exactly where the check's reasoning went wrong instead of just seeing that it passed.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**


1. The issue's fit to your interests and to the time available.
   > Yes, it's beginner friendly and I wanted to practice string manipulation.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
   > It identified the basics like, if its still alive, if the issue is unclaimed etc.. I personally weighed the content of the issue as well as the difficulty.
3. The anticipated difficulty in claiming it.
   > Pretty easy.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
