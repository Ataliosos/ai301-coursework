# Contribution: Issue selection in progress

**Contribution Number:** [1]  
**Student:** Kevin Balbuena Montes  
**GitHub Username:** Ataliosos  
**Issue:** Pending — no course-eligible issue confirmed  
**Pull Request:** Not opened

---

## Toolkit

**Unit 5: Ranking and screening Python issues — November 10, 2026**

I configured issue-scout to search for small Python bugs that I could reproduce locally. My first search returned 100 results, but the scout stopped because I hadn’t added ranking rules. I added rules to skip assigned issues, prioritize titles about security or input validation, and sort by comment count with recent activity as a tie-breaker. The scout then graded five issues and accepted one; grading my CodePath picks separately showed me why I also needed to check issue comments and linked pull requests.

**Unit 6: Not completed**

I did not reach the voice guard or repository memory work for a selected issue.

**Unit 7: Not completed**

I did not reach the ship gate, repository checks, or implementation on a contribution branch.

**Unit 8: Not completed**

I did not run the PR monitor or draft a follow-up because I had not opened a pull request.

---

## Why I Chose This Issue

I used the CodePath Issue Selection site to shortlist issues and graded three of them with issue-scout. I passed on AetherSDR #6987, a Windows encoding bug that fit my Python and Windows experience, because someone had recently claimed it. I passed on Snapchat GiGL #299 because the thread questioned whether the bug still existed and did not give me a clear way to reproduce it. OWASP Nest #3483 matched my cybersecurity interests, but the scout found that several contributors had already asked to work on it and one had prepared a fix. The repository also requires contributors to be assigned before opening a pull request.

A broader search ranked [json-rpc #135](https://github.com/pavlov99/json-rpc/issues/135) first and gave it an accept verdict. It looked manageable because the report identified two Python files and a specific behavior I could test locally: setting an error on a response should remove its previous result. I wanted to practice writing a regression test that fails before the fix and passes afterward. I hadn’t confirmed that the issue was eligible for the course, so I left it as a candidate. The scout helped me find promising work, but its verdict did not confirm course eligibility, and a time limit on claim comments alone could miss a repository’s assignment requirement.

Claim: claim pending — November 11, 2026.

**Toolkit**

- Tool: I used issue-scout with my search strategy and rubric to rank GitHub issues and grade the issues I shortlisted from CodePath.
- What it produced: It rejected three CodePath picks and ranked json-rpc #135 first in a broader search.
- Difficulties: An empty Assignees field did not tell me whether someone was already working on an issue. OWASP Nest #3483 had no assignee, but the thread contained several claims and a link to a PR.
- What changed: I added ranking rules so the scan could finish. I would update my availability check to flag projects that require maintainer assignment before a PR, even when older claim comments fall outside the rubric’s time window.

---

## Understanding the Issue

The details below describe the report for json-rpc #135, a candidate I had not confirmed for the course.

**Problem Description**

The report says that when a JSON-RPC response already has a result, setting an error can leave the old result in the response.

**Expected Behavior**

After setting the error, the response should contain the `error` field and no longer contain the previous `result` field.

**Current Behavior**

According to the issue and the scout’s code inspection, the error setters try to remove a key named `value`. The existing field is named `result`, so the old result can remain alongside the error. I did not reproduce this locally.

**Affected Components**

The report and the scout identified the response error setters in `jsonrpc/jsonrpc1.py` and `jsonrpc/jsonrpc2.py`.

**Toolkit**

- Tool: I used issue-scout to compare the GitHub issue report with the code it inspected.
- What it produced: It identified the two Python files and the mismatch between `value` and `result`.
- Difficulties: The code inspection gave me a starting point, but I did not confirm the behavior by running the project locally.
- What changed: I recorded the reported behavior separately from what I had personally verified.

---

## Reproduction Process

**Environment Setup**

I used Windows, GitHub CLI, and Claude Code for issue screening. I did not clone or set up the candidate repository locally.

**Steps to Reproduce**

I did not run a reproduction. My proposed first check would be to create a response with a `result`, set its `error`, and inspect whether both fields remain.

**Reproduction Evidence**

- **Commit showing reproduction:** none
- **Screenshots/logs:** No local reproduction output.
- **My findings:** The scout identified a likely cause in the source code. The runtime behavior remains unverified on my machine.

**Toolkit**

- Tool: I used issue-scout to identify a possible reproduction check. I did not run repro-check.
- What it produced: A starting point for a focused test of the response fields.
- Difficulties: I had not confirmed an eligible issue or set up the project locally.
- What changed: No reproduction steps were run. I kept the proposed check separate from the evidence.

---

## Solution Approach

**Analysis**

The candidate issue points to the response error setters in `jsonrpc/jsonrpc1.py` and `jsonrpc/jsonrpc2.py`. The suspected cause is that the setters remove `value` when the old response field is `result`. This is based on the issue report and the scout’s source inspection.

**Proposed Solution**

If the issue is confirmed for the course and the behavior reproduces locally, update the error setters to remove `result` when an error is set. Keep the change limited to the two setters and their tests.

**Implementation Plan**

1. Add a regression test that sets a result, then an error, and checks that the old result is gone.
2. Confirm that the test fails on the original code, then update the relevant error setters in `jsonrpc/jsonrpc1.py` and `jsonrpc/jsonrpc2.py`.
3. Rerun the regression test and the repository’s documented checks.

This is a proposed plan. I did not implement or test it.

**Toolkit**

- Tool: I used the issue-scout readout to outline a possible fix. I did not run plan-check.
- What it produced: A proposed change limited to two error setters and a regression test.
- Difficulties: I did not verify the failure locally or confirm that I could use the issue for the course.
- What changed: No code changes were made.

---

## Testing Strategy

If I proceed with json-rpc #135, I would run the same regression test before and after the fix. Before the fix, I would check whether setting `error` leaves the old `result` in the response. After the fix, I would check that `error` remains present and `result` is absent. I would also run the repository’s documented test suite and record the commands and output. I did not run either check.

**Toolkit**

- Tool: I used the issue-scout readout to identify what a regression test should verify.
- What it produced: A specific before-and-after check for the `result` and `error` fields.
- Difficulties: I had no local test output.
- What changed: I recorded the expected observations as a test plan rather than reporting a passing result.

---

## Implementation Notes

**November 10, 2026**

My first search returned 100 results but stopped before grading because my strategy lacked ranking rules. I added the rules, resumed the scan, and saved the results. I also screened CodePath candidates and documented why I skipped issues with recent claims or unclear reproduction steps.

**November 11, 2026**

The broader scan ranked json-rpc #135 first. I kept it as a candidate because I had not confirmed its course eligibility. I did not claim it, create a contribution branch, or make a code change.

**Toolkit**

- Tool: I used issue-scout and kept notes in `scan-notes.md` and `scan-output.md`.
- What it produced: A dated record of the ranking changes, candidate verdicts, and reasons I passed on issues.
- Difficulties: Several issues looked workable until I checked the comments and related pull requests.
- What changed: I began checking those signs of existing work before committing to a candidate.

---

## Pull Request

**PR Link:** Not opened.

**PR Description:** None. I did not submit a change.

**Maintainer Feedback:**

- November 11, 2026: No maintainer feedback. I had not posted a claim or opened a PR.

**Status:** Not opened.

**Toolkit**

- Tool: No PR tool used.
- What it produced: No pull request or review output.
- Difficulties: I had not confirmed a course-eligible issue or built a fix.
- What changed: Nothing in the upstream repository.

---

## Learnings and Reflections

**Technical Skills Gained**

I practiced using GitHub CLI and issue-scout to filter and rank issues. I also practiced turning a bug report into a specific test: set a result, set an error, and check which fields remain in the response.

**Challenges Overcome**

My first scan stopped because I hadn’t supplied ranking rules. I added them and resumed the scan. OWASP Nest #3483 was the clearest example of why screening takes more than checking the Assignees field: the issue had no assignee, but several people had asked for it and a contributor had already prepared a PR.

**What I'd Do Differently Next Time**

I would check the course list, the repository’s contribution rules, the issue thread, and linked PRs earlier. Once I have an eligible, available issue, I would run the smallest local reproduction before drafting a fix.

---

## Resources Used

- [CodePath Issue Selection site](https://open-source-issue-tracker.onrender.com/) — where I shortlisted issues for the assignment.
- [OWASP Nest #3483](https://github.com/OWASP/Nest/issues/3483) — an example of why I need to check the thread and related PRs even when an issue has no assignee.
- [json-rpc #135](https://github.com/pavlov99/json-rpc/issues/135) — the candidate report I used to outline a possible regression test.
