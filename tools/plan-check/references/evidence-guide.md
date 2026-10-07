# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

Where it lives: In eval mode, compare the candidate plan's diagnosis
and proposed approach with the issue context and repro-evidence
block, including inputs, steps, and artifacts. In live mode, compare
plan.md with the GitHub issue, posted reproduction comment, and
reproduction evidence quoted in the plan.

What good looks like: The stated cause explains the observed behavior
without contradicting the evidence. A suspected cause is identified
as a hypothesis with a concrete verification step; the approach
addresses the supported cause rather than merely hiding its symptom.

## Scope

Where it lives: In eval mode, read the candidate plan's scope
statement, proposed changes, exclusions, and named files or areas
against the issue's requested outcome. In live mode, read these
parts of plan.md against the GitHub issue.

What good looks like: The proposed work has one defined outcome,
and each change contributes to it. Several related files may be
needed; unrelated features or an open-ended rewrite do not establish
bounded work.

## Executability

Where it lives: In eval mode, inspect the candidate plan's named
files, functions or components, implementation actions, and order
of work against any supplied code context. In live mode, inspect
these parts of plan.md alongside the relevant repository files.

What good looks like: Another contributor can identify a starting
location and an action to take, then understand how it advances the
fix. An investigation step can supply an unresolved detail when it
states what to inspect and how the finding will guide implementation.

## Test plan

Where it lives: In eval mode, compare the candidate plan's proposed
tests and expected results with the repro-evidence block's trigger
steps, inputs, and observed output. In live mode, compare plan.md's
test plan with the posted reproduction evidence and relevant
existing tests.

What good looks like: The checks would distinguish the original bug
from the intended behavior after the change, using the original
trigger or an explained equivalent. They also check relevant existing
behavior the change could break; "run tests" alone does not identify
an observable success condition.

## Honesty

Where it lives: In eval mode, compare the candidate plan's claims,
risks, assumptions, and investigation steps with the issue context
and repro-evidence block. In live mode, inspect those parts of
plan.md and its Deviations section against the actual code changes
and test evidence available.

What good looks like: The plan distinguishes observations from
hypotheses and explains how important unknowns will be resolved.
During the build, deviations record what changed and why; planned
tests are not presented as tests already run.

## Comms

Where it lives: In eval mode, compare the candidate plan comment
with the issue context, thread highlights, candidate plan, and
repo-facts contribution policy. In live mode, compare comment.md
with plan.md, the GitHub issue thread, contribution docs, templates,
and AI policy; also review voice-guide.md.

What good looks like: The comment describes this issue's approach
and tests, respects relevant maintainer directions, and does not
contradict the plan. It supplies disclosures required by the
repository's policy; missing required information is unclear,
and no unstated disclosure requirement is invented.

Path Review: Another student's plan does not block this student's
plan. The comment must explain the student's own evidence and
approach rather than merely saying "same as above."