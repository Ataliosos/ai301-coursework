# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Evidence-based diagnosis | The plan's stated cause compared with the issue context and reproduction steps and artifacts. | Pass if the diagnosis fits the reproduced behavior. A suspected cause may pass when identified as a hypothesis with a concrete way to verify it. Fail if the diagnosis ignores or contradicts relevant evidence. | required |
| Bounded scope | The plan's proposed changes and scope limits compared with the issue's requested outcome. | Pass if the work has one defined outcome and the proposed changes are needed to achieve it. Related changes across files can pass. Fail if the plan adds unrelated features or leaves the extent of the work open-ended. | required |
| Cause-directed approach | The proposed implementation compared with the diagnosis and reproduction evidence. | Pass if the approach addresses the supported cause or includes an investigation that will establish it before choosing a fix. Fail if it only hides the symptom while leaving the evidenced cause unresolved. | required |
| Executable approach | The plan's implementation steps and named code locations compared with the supplied code context. | Pass if another contributor can identify where to start and what behavior to change. Exact line numbers are unnecessary. Fail if essential implementation choices are left unexplained. | required |
| Observable tests | The test plan compared with the original reproduction inputs, steps, and observed result. | Pass if the checks would distinguish the original bug from the intended result after the change, and check relevant existing behavior that the change could break. Fail if the plan only says to run tests without explaining what result would demonstrate success. | required |
| Honest uncertainty | The plan's claims, assumptions, risks, and investigation steps compared with the available evidence. | Pass if claims stay within the evidence and important unknowns have a way to be resolved. Fail if an unsupported assumption is treated as established fact or a blocking unknown has no investigation step. | required |
| Thread alignment | The draft plan comment and proposed approach compared with issue context and thread highlights. | Pass if the plan respects relevant maintainer directions and addresses unresolved questions that affect implementation. Another student's plan alone does not block a Path Review plan. | required |
| Repo conventions | The draft plan comment compared with the repo-facts contribution policy; in live mode, contribution docs, templates, and AI policy. | Pass if the comment follows stated repository requirements. When AI-use disclosure is required, it must supply the information the policy asks for; missing information is unclear. Do not invent requirements where none are stated. | required |

## Verdict rule

Accept only when every required check passes.
Reject if any required check fails or is unclear.
Preferred checks never change the verdict.
Evaluate the evidence and proposed work, not the number of headings,
steps, files, or words.