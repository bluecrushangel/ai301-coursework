# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| version-and-behavior | The repro report's environment record (version/commit tested) and its stated behavior | Pass if the environment record names an exact version or commit AND the behavior statement describes a concrete failure (not "it's broken"). | required |
| repro-steps-runnable | The repro report's steps section | Pass if the steps are exact commands/inputs a stranger could run with zero guessing (not descriptions of what to do). | required |
| artifacts-match-issue | The pasted artifacts (error text, log line, screenshot, diff) read against the specific failure the issue describes | Pass if the artifact content shows the *same* failure the issue names - same flag, same error, same behavior - not an adjacent or generic one. | preferred |
| honest-outcome | The report's stated verdict (reproduced / cannot-reproduce) read against the steps and artifacts actually shown | Pass if the claimed outcome is supported by the evidence shown: an evidenced cannot-reproduce (steps followed, no matching behavior) passes; a claimed reproduction with no matching artifact, or one that contradicts it, fails. | required |
| conventions-respected | The repo-facts block (contribution guide / stated policies) read against the wording of the claim comment and repro report | Pass if the comment complies with anything the repo requires - e.g. if the repo's policy requires disclosing AI assistance, the comment discloses it. If the repo states no such policy, this passes trivially. | required |

## Verdict rule

Accept (ready) if every `required` check passes. Reject (hold) if any `required` check is fail or unclear — `unclear` is treated as fail throughout. `preferred` checks are informational and never change the verdict.
