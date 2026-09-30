# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

Where it lives:
- **Eval bundle:** the repro report's environment section, read against the issue context block (which names the version/commit the issue was filed against) and the repo-facts block (which may name a current release).
- **Live mode:** the top of the student's draft repro report, read against the GitHub issue thread (the version the reporter states or the repo's release tag at issue-open time).

What good looks like: the exact version, commit hash, or build tested is named - not "latest" or "current main" - and it matches (or explicitly reconciles a mismatch with) the version the issue targets. If the student tested a different version than the issue names, the report says so and says why that's still valid evidence, rather than leaving the reader to notice the gap.

## Steps

Where it lives:
- **Eval bundle:** the repro report's steps section, read against the repo-facts block for anything the repo's own docs say is required setup (install commands, config, fixtures).
- **Live mode:** the student's draft repro report, read against the target repo's README or CONTRIBUTING docs for setup prerequisites.

What good looks like: starting from a stated starting state (clean checkout, specific config), each step is a literal command or input a stranger could paste - not a description of an action ("run X with flag Y", not "run the build command"). No step requires the reader to infer a missing command, flag, or file path. The steps terminate in an observable result (an output, a file, an error) rather than trailing off into "and then check if it works."

## Behavior shown

Where it lives:
- **Eval bundle:** the repro report's artifacts (pasted error text, log lines, diffs, screenshots), read against the specific failure described in the issue context block - the exact symptom, flag, error message, or output the issue names.
- **Live mode:** the artifacts pasted into the student's draft, read against the exact wording of the GitHub issue.

What good looks like: the artifact contains the *same* concrete symptom the issue names (same flag, same error string, same misbehavior) - not merely "an error occurred" or a generic failure that could belong to a different bug in the same area. If the artifact shows something adjacent (a warning instead of the crash the issue reports, a different flag), that's a mismatch, not a match, even if it's in the same subsystem.

## Honesty

Where it lives:
- **Eval bundle:** the report's stated verdict (reproduced / could not reproduce), read against its own steps and artifacts sections - does the evidence shown actually support the conclusion claimed?
- **Live mode:** the student's draft repro report's conclusion sentence, read against everything above it in the same draft.

What good looks like: the stated outcome is exactly as strong as the evidence shown, no stronger. An honest "I followed steps 1-4 against version X and did not observe the reported behavior" is a pass when the steps and environment are solid - it's a true report, not a failed reproduction. A claimed "reproduced" with no artifact, or an artifact that shows a different symptom than the one claimed, is the failure mode this guide exists to catch, regardless of how confident the prose sounds.

## Comms

Where it lives:
- **Eval bundle:** the claim comment text, read against the issue context block; the repro comment text, read against the repo-facts block's stated contribution policy or comment template (including any AI-assistance disclosure requirement).
- **Live mode:** the student's draft claim and repro comments, read against the actual GitHub issue thread and the target repo's CONTRIBUTING.md or issue-template docs.

What good looks like: the claim comment names the specific issue and what will be investigated next (not "I'll look into this"), and promises investigation only - no fix, no date. Both comments follow any policy the repo explicitly states, most importantly a disclosure requirement for AI-assisted work: if the repo's docs require disclosing AI assistance and the comment doesn't, that's a fail regardless of how good the technical content is. Boilerplate template language with the blanks filled in mechanically (no issue-specific detail) is a fail even if technically compliant.