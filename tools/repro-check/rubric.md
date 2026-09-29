# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Specific claim | Claim comment read against the issue context; see Comms in references/evidence-guide.md. | Pass if the claim identifies this issue's behavior and promises an investigation and report without asserting an unperformed reproduction or promising a fix or date. | required |
| Environment match | Repro report's environment record read against the issue context and repo-facts block; see Environment in references/evidence-guide.md. | Pass if the OS, relevant versions or dependencies, and code state identify what was tested and match the issue's target, or any relevant difference is explained. | required |
| Followable steps | Repro report's setup and trigger steps read against the issue context; see Steps in references/evidence-guide.md. | Pass if a stranger can start from the stated environment, supply the needed input, and perform the action that produced the reported observation. | required |
| Issue behavior | Repro report's output excerpt, log, screenshot, or other artifact read against the issue description; see Behavior shown in references/evidence-guide.md. | Pass if the artifact and its input show the issue's described behavior. For a cannot-reproduce report, pass if the artifact shows what happened when the stated issue trigger was attempted. An unrelated setup error or different bug fails. | required |
| Supported conclusion | Repro report's stated outcome read against its steps and artifacts; see Honesty in references/evidence-guide.md. | Pass if the conclusion states only what the evidence supports, whether that is reproduced or cannot reproduce. Fail if it claims to confirm the issue while showing another behavior, or claims an unobserved result. | required |
| Repo conventions | Claim comment and repro report read against repo-facts contribution policy and issue context; in live mode also read the repository's contribution docs, templates, and AI policy; see Comms in references/evidence-guide.md. | Pass if the comments follow stated repository conventions. When the repository requires AI-use disclosure, the package must explicitly state whether AI assistance was used; if used, name the tool and extent required by the policy. Missing information is unclear, not evidence of no AI use. If no disclosure policy is stated, do not require a disclosure. | required |

## Verdict rule

For a claim-only draft, grade Specific claim and Repo conventions; mark the four reproduction checks not applicable. Accept only if both applicable required checks pass. For a full reproduction package, accept only if all six required checks pass. A fail or unclear on an applicable required check means reject. A not-applicable reproduction check on a claim-only draft does not count as a fail. An evidenced cannot-reproduce report can be accepted when its applicable checks pass.