# Procedure: how this tool grades a PR package

## Read order

1. Determine the mode from the request. In live mode, read scope.md
   first and apply SKILL.md's scope rules before gathering evidence.
   In eval mode, use only the supplied package; ignore scope.md
   and voice-guide.md.
2. Read rubric.md and references/evidence-guide.md. Record the check
   names, required evidence, weights, and verdict rule. Refuse to
   grade if the rubric or procedure is empty.
3. In live mode, read voice-guide.md before reviewing outgoing text.
4. Read the issue context and thread. Record the requested behavior,
   original trigger, and relevant maintainer directions.
5. Read the repository requirements. Record required checks, template
   information, contribution rules, and disclosure requirements.
   In eval mode, take these only from the bundle's repo facts.
6. Read the plan, including deviations, before the diff. Record its
   intended outcome, scope limits, implementation, and test plan.
7. Read the commits and actual diff. Record what behavior changed,
   which files changed, and any work the plan does not account for.
   In live mode, use git diff main...HEAD and git log main..HEAD.
   Inspect git status --short for relevant uncommitted changes.
8. Read the test evidence. Record the tested code state when supplied,
   commands or manual actions, inputs, observations, and results.
9. Read the PR title and description last. Compare their claims with
   the plan, diff, and evidence already gathered.

Read the plan before the diff to identify intended scope.
Read the artifacts before the description so confident wording
does not substitute for evidence.

## Evidence gathering

1. For Plan fidelity, pair each meaningful change in the diff with
   the plan or a deviation note. Also identify planned behavior
   that was omitted. Record whether changes and omissions are
   explained in both the plan and PR description.
2. For Accurate claims, list the title's and description's claims
   about behavior, completeness, testing, and scope. Match each
   material claim to a diff hunk or test artifact. Record any
   contradiction or missing support.
3. For Observable reproduction, locate the original trigger and
   before-and-after results. Record the input, action, expected
   behavior, actual behavior, and relevant environment or code state.
   Check that the observation concerns the issue being fixed.
4. For Regression evidence, compare the plan's behavior and risks
   with the tests or manual checks actually executed. Record what
   each check exercises and what its result demonstrates.
5. For Repository checks, list each applicable required check from
   the repository requirements. Pair it with its command, observed
   result, and any explanation of failure, blocked execution, or
   an empty suite. Record explicit exemptions separately.
6. For Focused diff, inspect every changed file and meaningful hunk.
   Record its connection to the issue's outcome or necessary support.
   Identify unrelated cleanup, generated files, and formatting churn.
7. For Reviewable changes, inspect the diff for debug output,
   abandoned code, accidental files, and debris that obscures review.
   Do not judge reviewability by length or commit count alone.
8. For Repository standards, compare the title and description with
   the issue link, thread directions, template requests, and
   contribution requirements. Check declarations against evidence.
   Record explanations for any N/A entries.
9. For AI disclosure, locate the actual disclosure statement and
   compare it with the applicable policy's requested information.
   In live Path Review mode, also apply the course requirement to
   describe actual AI assistance. In eval mode, apply only rules
   stated in the supplied bundle.
10. Keep a short quote or precise source location for every deciding
    fact. Do not invent missing evidence or assume a test was run.

## Check execution

1. Execute all checks in rubric.md, in table order, even after one
   required check fails.
2. Apply each check's written pass condition to the gathered evidence.
   Use pass when the condition is established, fail when evidence
   shows a violation, and unclear when necessary evidence is absent
   or ambiguous.
3. Distinguish missing evidence from an observed unsuccessful result.
   A disclosed failed check, blocked run, empty suite, or remaining
   bug is not automatically a failure of this review. Apply the
   rubric's conditions to the evidence and the actual claims.
4. Do not treat disclosure as permission for unrelated work or as
   a substitute for an applicable check that was never attempted.
5. Check that test evidence applies to the submitted changes.
   If it clearly predates a relevant change, it does not establish
   that the later change was tested. Do not demand a particular
   evidence format when its applicability is otherwise established.
6. Re-read the relevant source when facts conflict or a grade depends
   on exact wording. Otherwise, use the recorded evidence.
7. Do not fetch external sources or execute tests in eval mode.
   In live mode, do not change code, post text, or open a PR during
   grading. Report needed actions instead.
8. Report a procedure gap rather than inventing a missing step.
   Use unclear for an affected check when the gap prevents grading.
9. In live mode, report voice-guide violations separately. They
   affect the verdict only if an applicable rubric check reads them.

## Verdict assembly

1. Apply rubric.md's verdict rule to the completed grades.
   Accept only when every required check passes.
   A required fail or unclear means reject.
   Preferred checks never change the verdict.
2. In the readable summary, report every check's exact name, grade,
   and deciding evidence.
3. For a rejection, identify the first required fail or unclear
   in rubric order as the primary deciding check. Quote its
   relevant source evidence, or name the necessary evidence missing.
   Also report all other required problems and concrete next steps.
4. For an acceptance, summarize the evidence supporting readiness
   and retain any disclosed limitations without changing the verdict
   to a third category.
5. Include live voice feedback and procedure gaps before the JSON.
6. End with the exact JSON schema required by SKILL.md and CONTRACT.md.
   Use the PR URL, or the issue URL for an unopened live draft,
   or the eval bundle id as item.
   Include every rubric check with its grade and one-line evidence.
   Keep the required key order and add no extra fields.
7. Ensure the JSON is valid, fenced, and last. Write nothing after it.