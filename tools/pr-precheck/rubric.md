# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | The committed diff and delivered behavior compared with the plan's scope, implementation steps, and deviation notes; see Plan fidelity in references/evidence-guide.md. | Pass if the implemented work is accounted for by the plan and its deviations. A reduced scope or changed approach can pass when the plan records what changed and why, and the PR description discloses the actual result. Fail if the diff silently adds, omits, or changes planned behavior. | required |
| Accurate claims | The PR title, description, and completion claims compared with the diff, plan deviations, and test artifacts; see Plan fidelity and Test evidence in references/evidence-guide.md. | Pass if the description accurately states what the change delivers and what remains unresolved. Fail if it claims a fix, coverage, successful check, or plan fidelity that the supplied artifacts contradict. Necessary evidence missing from a claim is unclear. | required |
| Observable reproduction | The before-and-after commands, inputs, outputs, or manual observations compared with the issue's reported behavior and the plan's test plan; see Test evidence in references/evidence-guide.md. | Pass if the evidence lets a reviewer compare the original behavior with the result of the submitted change using the relevant trigger. Manual evidence can pass when its actions and observations are specific and repeatable. An honestly disclosed remaining failure can pass when the artifacts show it. Fail if the evidence shows a different bug or gives no observable result. | required |
| Regression evidence | The changed or existing tests and their execution results compared with the behavior and risks named in the plan; see Test evidence in references/evidence-guide.md. | Pass if executed checks exercise the changed behavior and relevant existing behavior that the change could affect. Automated or repeatable manual checks can qualify. A disclosed limitation can pass when the evidence supports the limited claim. Fail if the relevant checks were not executed or the evidence does not exercise the changed behavior. | required |
| Repository checks | The recorded check commands, results, and explanations compared with the repo-facts block's required checks; in live mode, the PR template and contribution instructions; see Test evidence and Standards and comms in references/evidence-guide.md. | Pass if each applicable required repository check has an observable execution result. A failed run, an empty test suite, or an environment-blocked run can pass when its actual result and reason are disclosed without claiming success. An explicit repository exemption can establish that a check is not applicable. Fail if an applicable required check was never attempted or its result is hidden. | required |
| Focused diff | The changed files and hunks compared with the issue's outcome, plan, and deviations; see Diff quality in references/evidence-guide.md. | Pass if the changes contribute to the issue's outcome or are necessary supporting changes. Fail if unrelated features, cleanup, generated files, or formatting changes enlarge the diff without being needed for this work. Disclosure alone does not make unrelated work necessary. | required |
| Reviewable changes | The actual diff and relevant commit contents; see Diff quality in references/evidence-guide.md. | Pass if a reviewer can identify and assess the intended implementation and tests without debug debris, abandoned code, or accidental files obscuring them. Fail if such debris remains. Do not fail solely because the diff is long or has several commits. | required |
| Repository standards | The PR title and description compared with the issue, thread directions, and repo-facts template and contribution requirements; in live mode, the actual PR template and contribution docs; see Standards and comms in references/evidence-guide.md. | Pass if the draft identifies its issue, supplies the information required by the repository, and respects applicable maintainer directions. Explicitly justified N/A entries can satisfy inapplicable template requests. Fail if a stated requirement is ignored or a checked declaration contradicts the evidence. | required |
| AI disclosure | The PR's disclosure statement compared with the repo-facts AI policy and applicable submission requirements; in live mode, the course's disclosure requirement and repository policy; see Standards and comms in references/evidence-guide.md. | Pass if the submission supplies the AI-use information explicitly required by its applicable rules. When disclosure is required, silence is unclear rather than evidence that no AI was used. In live Path Review submissions, describe the actual tools and assistance used. In eval mode, apply only requirements stated in the bundle; do not invent a disclosure requirement. | required |

## Verdict rule

Accept only when every required check passes.
Reject when any required check fails or is unclear.
Preferred checks never change the verdict.

An honestly disclosed shortfall, changed approach, expected failure,
or unsuccessful repository check does not automatically mean reject.
Apply each check to the actual evidence and the limited claims made.

Disclosure does not excuse unrelated changes, missing observable
evidence, or an applicable required check that was never attempted.
