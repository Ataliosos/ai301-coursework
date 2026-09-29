# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

## Your identity upstream

**GitHub username**

Ataliosos

---

## Posted upstream

**Claim comment**

Not posted yet. My selected issue is:
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/53

Claude Code reached my Enterprise individual spending limit before I could check my claim draft in live mode. The CLI reported: "You've hit your individual spend limit". Running `/usage-credits` returned: "Contact your admin to manage usage credit settings."

I plan to continue tomorrow, September 30, after my Enterprise spending limit resets at 8:00 PM EDT. I will run the confirming full evaluation, check my claim draft in live mode, and then continue with claiming and reproducing issue #53.

**Reproduction comment**

Not posted yet. I have not reproduced issue #53 in my own environment, so I do not have reproduction evidence to report. After posting my checked claim, I plan to set up my fork, attempt the reproduction, and report what I actually observe.

---

## Eval iterations

**Run history**

1. My first full attempt encountered a Windows `UnicodeEncodeError` while sending package text to Claude. I interrupted it. It did not produce a usable complete score.
2. I enabled UTF-8 explicitly with `py -X utf8` and completed a full run. Its agreement line was:

   ```text
   agreement: 19/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in disclosure)
   ```

   The category results were clear-accept 8/8, disclosure 0/1, no-evidence 4/4, unfollowable-comms 3/3, and wrong-target 4/4. This is the complete run saved in `eval-run.txt`.
3. I read `pkg-20` and its detailed result. I revised Repo conventions and the Comms evidence guidance so silence would not count as proof that a required AI disclosure was unnecessary.
4. I ran `--only pkg-20,pkg-01`. The output was:

   ```text
   agreement: 2/2 scored items
   ```

   `pkg-20` changed to reject and `pkg-01` remained accept.
5. I attempted a confirming full run twice. Both attempts returned 20 package errors and:

   ```text
   agreement: 0/0 scored items
   ```

   These were execution failures, not rubric scores. The harness stated:

   ```text
   partial run: NOT written to eval-run.txt.
   ```

6. A direct Claude request reported that I had reached my individual spending limit. I could not complete another full evaluation before this submission. I plan to retry after the September 30 reset at 8:00 PM EDT.

The saved `eval-run.txt` is the earlier completed full run, before the disclosure revision. The revised files have only been checked on the two-package partial run; they have not passed a confirming full run. The committed transcript's agreement score is 19/20.

**Package analysis**

In the saved full run, `pkg-20` received **accept** from my rubric while its gold label was **reject**.

The package's contribution policy says: "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance".

The reproduction showed the issue's actual behavior: the single-theme run reported light mode while the conditional theme pair reported dark mode. The environment and commands were also recorded. However, neither comment addressed AI assistance.

The Repo conventions result said: "Comments are issue-specific and no AI usage is indicated anywhere in the package, so the strict AI-disclosure rule has nothing to flag as missing."

That reasoning treated missing information as evidence that disclosure was unnecessary. My revision makes compliance unclear when a required disclosure is not addressed. Silence alone does not establish that no AI assistance was used.

**Check rationale**

The current Repo conventions pass condition in my uploaded rubric is:

> Pass if the comments follow stated repository conventions. When the repository requires AI-use disclosure, the package must explicitly state whether AI assistance was used; if used, name the tool and extent required by the policy. Missing information is unclear, not evidence of no AI use. If no disclosure policy is stated, do not require a disclosure.

My principle is that a required policy needs evidence of compliance. I changed the check after reading `pkg-20`'s policy and the grader's explanation. I also updated the evidence guide so the decision rule and the instructions for finding evidence agree.

**Trade-offs**

This check can hold a report from someone who used no AI but did not explicitly say so, when the repository requires disclosure. That is the cost of treating missing compliance information as unclear.

I rechecked `pkg-20` and `pkg-01` together. The result was "agreement: 2/2 scored items": `pkg-20` was rejected and `pkg-01` stayed accepted. This checks one earlier accepted package, but it does not prove that all other packages stayed unchanged. The confirming full run remains unfinished because of the execution errors and spending limit.

---

Related paths: `eval-run.txt` in this directory; the skill files in
`tools/repro-check/`.
