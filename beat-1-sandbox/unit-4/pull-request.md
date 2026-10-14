# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/210

**Branch**

`fix/53-parenthesized-phone-numbers`

## Eval iterations

**Run history**

I completed one full evaluation run with my installed pr-precheck
skill. The run reported:

```text
categories: clear-accept 5/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3
agreement: 18/20 scored items  (bar: 18/20: PASS)
```

The disagreements were `pkg-02`, which failed Regression evidence,
and `pkg-08`, which failed Repository checks. Both had an accept
gold label, but my tool returned reject.

I read both packages after the run and kept my skill unchanged.
This is the complete run saved in eval-run.txt. The later live
reviews of my own PR were separate from this evaluation.

**Package analysis**

For `pkg-02`, my tool returned `reject`, while the gold label was
`accept`. The evaluation identified the failed check as:

> failed: Regression evidence

The package changes save_text, save_html, and save_svg so a failed
file write does not clear recorded output. Its new regression test
directly checks save_text, including the successful-save control.

The package states:

> a successful save still clears it (covered by the new test's second
> half). `pytest tests/ -q` passes (1462 passed, 12 skipped).

My check asks for evidence covering the changed behavior and relevant
existing behavior. The rejection appears to reflect a stricter
reading of coverage across all three changed save methods. The
package shows a direct regression test for save_text and a passing
full suite, but does not separately demonstrate the failed-write
case for save_html and save_svg.

I can see why the gold label accepts it: the test shows the original
failure is fixed, checks that successful saving still clears the
record, and reports the full suite passing. My result shows that
the coverage wording can reject evidence the instructor considers
sufficient. Without the detailed per-check explanation, I cannot
say exactly which coverage gap the model relied on.

**Check rationale**

My Repository checks check reads exactly:

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repository checks | The recorded check commands, results, and explanations compared with the repo-facts block's required checks; in live mode, the PR template and contribution instructions; see Test evidence and Standards and comms in references/evidence-guide.md. | Pass if each applicable required repository check has an observable execution result. A failed run, an empty test suite, or an environment-blocked run can pass when its actual result and reason are disclosed without claiming success. An explicit repository exemption can establish that a check is not applicable. Fail if an applicable required check was never attempted or its result is hidden. | required |

I wrote this check to separate missing work from an honest
unsuccessful result. Saying a check passed without evidence is
different from running it, showing the failure, and explaining what
remains unresolved.

I kept this wording after the evaluation. During the live review,
the tool found that my draft lacked formatting and frontend check
results. I ran those checks and added their actual output.
Formatting passed. The frontend suite timed out in the same test
twice, with 17 tests passing and one failing in each run.
I disclosed that result instead of calling the suite passed.

**Trade-offs**

Requiring an observable result for every applicable repository
check can reject a brief report that is actually sufficient.

For example, `pkg-08` says:

> Requirements: cheatsheets regenerated (no binding changes, no diff);
> code formatted; integration test added; new error text
> internationalised; no UserConfig changes.

It also reports:

> Integration test
> `stash_untracked_only_errors` passes; `go test ./...` passes;
> `go generate ./...` produces no cheatsheet diff.

The gold label accepts this package, but my tool rejected it on
Repository checks. Its brief formatting statement may not have
satisfied my rule's demand for an observable execution result,
although the summary alone does not establish the exact reason.

I kept the rule because I want missing checks to be visible.
The trade-off is that it can ask for more evidence than a reviewer
needs. My 18/20 result met the evaluation bar and matched every
category, but it does not mean the rubric judges every PR correctly.

---

Related paths: `eval-run.txt` in this directory;
the skill files in `tools/pr-precheck/`.
