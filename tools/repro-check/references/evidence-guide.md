# Evidence guide: where proof lives in a reproduction package

## Environment

Where it lives: In an eval package, compare the issue context and repo-facts block with the repro report's environment record. In live mode, compare the GitHub issue and repository setup docs with the student's draft report.

What good looks like: The report identifies the operating system, relevant software versions or dependencies, and the code state used. These match the issue's target, or the report explains a relevant difference so another person knows what was actually tested.

## Steps

Where it lives: In an eval package, read the repro report's setup and action steps against the issue context. In live mode, read the draft repro comment alongside the issue and the repository's setup instructions.

What good looks like: Starting from the stated code and environment, another person can perform the setup, run the command or action, and reach the observation. Commands include needed inputs and the action that triggers the reported behavior.

## Behavior shown

Where it lives: In an eval package, inspect the repro report's output excerpts, logs, screenshots, or other artifacts against the issue description. In live mode, inspect the artifacts in the draft comment against the GitHub issue.

What good looks like: The artifact shows the behavior the issue asks about, including the relevant input and observed result. An artifact showing a different error or a nearby feature does not establish this issue's behavior.

## Honesty

Where it lives: Compare the repro report's conclusion with its steps and artifacts, then compare both with the issue context. In live mode, compare the draft comment's claims with the evidence it includes.

What good looks like: The conclusion states what the evidence actually supports. A cannot-reproduce report can pass when it records the attempted steps, environment, and observed result; it must not claim the bug was reproduced. A report must not say the issue is confirmed when its artifact shows a different behavior.

## Comms

Where it lives: In an eval package, compare the claim comment and repro report with the issue context and the repo-facts block's contribution policy. In live mode, compare the draft comments with the GitHub issue, repository contribution docs, PR or issue templates, and any AI-use policy.

What good looks like: The claim names this issue and promises an investigation and report without claiming work that has not happened or promising a fix or date. The repro comment says what the student did in their own words. Both follow stated repo conventions, including an AI-assistance disclosure when the policy requires one.

When a repository requires AI-use disclosure, look for an explicit statement about whether AI assistance was used and, if used, the tool and extent required by that policy. Silence does not establish that no AI was used; missing information leaves compliance unclear. Do not invent a disclosure requirement where the repository states none.