# Procedure: how this skill grades a plan package

## Read order

1. Read rubric.md and references/evidence-guide.md to identify
   the checks, evidence locations, and verdict rule.
2. In eval mode, use only the supplied package snapshot.
   Do not fetch the current GitHub issue.
3. In live mode, read scope.md and confirm the issue is in scope.
   Read voice-guide.md before reviewing the draft comment.
4. Read the issue context and thread highlights. Record the
   requested outcome and relevant maintainer directions.
5. Read the reproduction environment, steps, and artifacts.
   Record what was observed and what remains unproven.
6. Read the proposed plan and draft comment. Record the diagnosis,
   scope, implementation steps, tests, and unresolved questions.
7. Read the repo-facts contribution policy. In live mode, also
   inspect relevant contribution docs, templates, and AI policy.

Read reproduction evidence before the plan so the plan's explanation
does not replace what the artifacts actually demonstrate.

## Evidence gathering

1. For Evidence-based diagnosis, compare the stated cause with
   the reproduction inputs and artifacts. Record supporting
   evidence, contradictions, and any proposed verification.
2. For Bounded scope, identify the intended outcome and proposed
   changes. Record any work unrelated to that outcome.
3. For Cause-directed approach, trace how the proposed change
   addresses the diagnosis. Record whether it resolves the cause
   or only suppresses the visible symptom.
4. For Executable approach, locate the named files, functions,
   components, or investigation starting points. Record the
   concrete actions another contributor could begin.
5. For Observable tests, record the original trigger, expected
   result after the change, and checks for existing behavior
   the change could affect.
6. For Honest uncertainty, compare confident claims with their
   evidence. Record important assumptions and how the plan
   proposes to resolve them.
7. For Thread alignment, collect relevant maintainer directions
   and unresolved questions from the supplied thread or live
   issue. Compare them with the draft comment and approach.
8. For Repo conventions, collect applicable requirements and
   compare them with the draft comment. Record required
   disclosures and whether the draft supplies them.
9. Keep a short quote or precise source reference for each fact.
   Do not invent missing evidence or assume a test was run.

## Check execution

1. Execute every check in rubric.md, in table order.
2. For each check, apply its pass condition to the gathered
   evidence. Use pass, fail, or unclear.
3. Use pass when the evidence establishes the pass condition.
   Use fail when the evidence shows a violation.
   Use unclear when necessary evidence is missing or ambiguous.
4. Do not require a particular heading, length, file count,
   or number of steps unless an applicable repository rule
   explicitly requires it.
5. A hypothesis is not automatically a failure. Apply the
   diagnosis and uncertainty checks to its verification plan.
6. Re-read the relevant source when evidence conflicts or a
   conclusion depends on wording. Otherwise, use the recorded
   evidence without re-reading the whole package.
7. Grade every check even after a required check fails.
   In live mode, also identify any voice-guide violations
   separately from the rubric grades.

## Verdict assembly

1. Apply the verdict rule in rubric.md to the completed grades.
2. Accept only when every required check passes.
   A required fail or unclear produces reject.
   Preferred checks do not change the verdict.
3. For each check, report its exact rubric name, grade, and
   evidence. Quote the relevant source wording when available.
4. For a deciding fail or unclear, explain which condition
   was violated or which necessary evidence is missing.
5. In the final fenced JSON block, include the per-check grades,
   evidence, and the binary verdict: accept or reject.
   Follow any output schema required by SKILL.md.
6. For a rejected package, name the concrete revisions or
   evidence needed before another review.
   Do not claim that comments were posted or code was tested
   unless the supplied evidence establishes those actions.