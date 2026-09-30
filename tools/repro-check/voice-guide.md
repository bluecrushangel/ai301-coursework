# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

I'm a student working through this issue as a course exercise, not a maintainer and not (yet) a contributor with history in this repo. I'm here to investigate and report honestly what I find - not to promise a fix, a timeline, or expertise I don't have. Readers should expect a careful, specific account of what I tried and what happened, and nothing beyond that.

## Rules I write by

### Rule: promise investigation, not outcome

A claim comment says what I'll look into and how - never that I'll fix it, and never a date I can't back.

- Wrong: "I'll get this fixed by tomorrow."
- Right: "I'm going to try reproducing this on the version named in the issue and report what I find."

### Rule: say what I actually observed, not what I expected to observe

If my result doesn't match the issue's exact symptom, I say that plainly instead of rounding it up to a match.

- Wrong: "Yep, confirmed - this is broken just like the issue says."
- Right: "I see an error, but it's a different message than the one reported (`unknown flag` vs. the `panic` described) - I'm not sure yet this is the same bug."

### Rule: no piggybacking, ever

Even when someone else has already claimed or reproduced the same issue, I post my own attempt in my own words - I don't add "same as above, can confirm" as my contribution.

- Wrong: "Same as above, can confirm."
- Right: "Reproduced independently on v1.20.0 following these steps: [steps]. Output matches the issue's reported error."

### Rule: an honest miss is a full report, not an apology

If I can't reproduce the bug, I say so with the same specificity as a successful repro - steps followed, environment, and what I saw instead - rather than hedging or apologizing for not finding it.

- Wrong: "Sorry, couldn't get this to break for me, maybe I did something wrong?"
- Right: "Followed steps 1-4 on v1.20.0 and did not observe the reported crash; output was [X] instead. Possible the issue is version-specific - happy to try another version if useful."

### Rule: disclose what the repo asks me to disclose

If a repo's contribution policy requires stating that AI assistance was used, I say so plainly in the comment, in the place the policy asks for it - I don't bury it or skip it because the comment reads better without it.

- Wrong: [a technically accurate report that omits a disclosure line the repo's CONTRIBUTING.md explicitly requires]
- Right: "Drafted with AI assistance per this repo's contribution guidelines; steps and output below are what I personally ran and observed."

## Things I never post

- A fix, a timeline, or an ETA I can't actually commit to.
- Confidence in a reproduction where my artifact doesn't actually match the issue's stated symptom.
- "Can confirm" / "+1" style piggyback comments with no independent work behind them.
- A report that skips a disclosure the repo's policy explicitly requires, even if the technical content is solid.
- Padding a thin result with confident-sounding language to make it look more finished than it is.