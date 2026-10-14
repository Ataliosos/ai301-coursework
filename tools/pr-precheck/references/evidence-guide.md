# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Where it lives:

- In eval mode, read the plan-context block's intended behavior,
  scope limits, implementation steps, test plan, and deviation notes.
  Compare them with the candidate PR's diff, commits, title,
  description, and completion claims.
- In live mode, read plan.md, including its Deviations section.
  Compare it with git diff main...HEAD, git log main..HEAD,
  and the title and description in pr_draft.md.

What good looks like:

Each meaningful change and omitted deliverable is accounted for by
the plan or a deviation explaining what changed and why. The PR
description states what the diff actually delivers, including any
reduced scope or unresolved behavior, without claiming unsupported
completeness.

Use these sources for Plan fidelity and Accurate claims. An honest
deviation can account for a changed approach; it does not make
unrelated work necessary.

## Test evidence (harness category: not-tested)

Where it lives:

- In eval mode, compare the candidate PR's test-evidence section,
  captured commands, outputs, manual observations, and changed tests
  with the issue's reproduction and the plan-context test plan.
  Find required repository checks in the repo-facts block.
- In live mode, read test_evidence.md alongside plan.md, the original
  reproduction, and the committed test changes. Compare the results
  with the actual submitted behavior and the checks required by
  .github/PULL_REQUEST_TEMPLATE.md and docs/CONTRIBUTING.md.
  Cross-check testing claims and checked boxes in pr_draft.md.

What good looks like:

The evidence identifies the relevant trigger and observable before
and after, exercises the changed behavior and relevant regression
risks, and records actual results for applicable repository checks.
Repeatable manual observations can qualify; unsupported statements
such as "tests pass" do not establish what was tested.

Use these sources for Observable reproduction, Regression evidence,
Repository checks, and testing claims under Accurate claims.

Distinguish passed tests, expected failures, failed tests, blocked
runs, empty suites, and checks never attempted. A disclosed
unsuccessful result can satisfy an evidence requirement when its
output and reason are supplied; it must not be described as success.
Do not infer that tests ran merely because test code was added.

Check that evidence applies to the submitted code. A result known
to predate a relevant change does not establish testing of that change.

## Diff quality (harness category: unreviewable)

Where it lives:

- In eval mode, inspect the candidate PR's unified diff and commit
  list. Compare each meaningful hunk with the issue's outcome and
  the plan-context scope and deviations.
- In live mode, inspect git diff main...HEAD and git log main..HEAD
  from the fork's working copy. Use git status --short to identify
  relevant uncommitted changes that the committed diff does not cover.

What good looks like:

The diff contains the implementation and necessary supporting
changes for the issue, and a reviewer can assess them without
unrelated cleanup, accidental files, debug leftovers, abandoned
code, or broad formatting churn obscuring the work. Several files
or commits are acceptable when their changes serve the outcome.

Use these sources for Focused diff and Reviewable changes.
A deviation note does not excuse unrelated hunks. Local review
documents such as plan.md, comment.md, pr_draft.md, and
test_evidence.md must not be accidentally included in the live
Path Review code diff.

## Standards and comms (harness category: standards-wall)

Where it lives:

- In eval mode, read the repo-facts block's PR-template requests,
  required checks, contribution instructions, and stated AI policy.
  Read relevant directions in the supplied thread highlights.
  Compare these requirements with the candidate title, description,
  checklist declarations, and disclosure.
- In live mode, read .github/PULL_REQUEST_TEMPLATE.md,
  docs/CONTRIBUTING.md, any applicable AI policy, and relevant
  maintainer directions in the issue thread. Compare them with
  pr_draft.md and its supporting test_evidence.md.
  Apply the course requirement to disclose actual AI assistance
  in Notes for Reviewers.
- In live mode only, read voice-guide.md for separate feedback on
  the student's title and description.

What good looks like:

The PR identifies its issue and supplies the information the
repository requests, with truthful checklist declarations and
justified N/A entries where applicable. It respects relevant
maintainer directions and supplies the AI-use information required
by the applicable rules.

Use these sources for Repository standards, AI disclosure, and
the requirements portion of Repository checks.

When disclosure is required, locate an explicit statement providing
the required information. Silence does not establish that no AI
was used. In eval mode, do not import the course's live disclosure
requirement into a bundle that states no such requirement.

Assess whether the description matches the actual diff under
Plan fidelity and Accurate claims, rather than judging its polish.