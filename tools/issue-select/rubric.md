# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintained code | Repo-facts block: archived flag and last 5 default-branch commit dates and authors. Live mode: archive banner and default-branch commit history. | Pass if the repo is not archived and at least one human-authored default-branch commit occurred within 180 days of the snapshot date (or today in live mode). A bot merge of a human PR counts. | required |
| In-use development | Repo-facts block: latest release date and last 5 default-branch commits. Live mode: Releases sidebar and commit history. | Pass if a release or human-authored default-branch commit occurred within 180 days. A release is not necessary when development is current. | required |
| Bounded contribution | Issue body and comment thread, including maintainer clarifications and abandoned PR history. Live mode: issue body and full thread. | Pass if the request identifies one change or a finite related set with observable expected behavior or named files. Fail for a usage question, an explicit tracking or umbrella list, an unresolved product or design choice, a maintainer-stated core redesign, or two or more abandoned unmerged attempts with no later settled plan. A short report can pass when its expected behavior is concrete. | required |
| Available work | Repo-facts block: assignees and linked PR states; issue comments with dates and maintainer replies. Live mode: Assignees, Development sidebar, and comment thread. | Pass if there is no assignee, no open PR, and no active claim. A claim older than 90 days with no activity passes if a maintainer later explicitly invites new takers. Closed unmerged PRs alone do not reserve the issue. In Path Review live mode, ignore other students' claim comments as the scope house rule directs; an open PR or assignee still blocks. | required |
| AI contribution allowed | Repo-facts block: contribution policy. Live mode: root or `.github/CONTRIBUTING.md`, linked policy documents, dedicated AI policy, and PR template. | Pass if no policy bans AI-generated code or documentation. Disclosure, review, understanding, and testing conditions pass when followed. An explicit AI-generated contribution ban fails. | required |
| Clear start | Issue body and maintainer comments. Live mode: body and thread. | Pass if the report supplies reproduction steps, acceptance criteria, target files, or a maintainer diagnosis. | preferred |

## Verdict rule

Accept only when every required check passes. Reject if any required check fails or is unclear. Preferred checks rank accepted issues and never change the verdict. Measure dates from the bundle capture date in eval mode and today's date in live mode. Apply the Path Review claim-comment exception only in live mode.
