# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

## Posted upstream

**GitHub username**

Ataliosos

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/53#issuecomment-6026865498

I reproduced the parenthesized phone-number problem on Windows
with Python 3.13.0 at commit
2f4e82f52efbcfcc57d65b3fa5348672163ca088.

For `Call me at (555) 123-4567`, scrub() returned the input
unchanged and detect() returned an empty list.

My plan is to update the US phone-number pattern in
safety/pii_scrubber.py. The current pattern does not allow
the space after the closing parenthesis, and its leading
word boundary prevents matching from the opening parenthesis.

I will check complete redaction and detection positions,
parenthesized numbers at the beginning and end of text,
existing dashed, dotted, and +1 formats, and cases that
could produce partial matches inside longer numbers or identifiers.

I will update tests/unit/test_pii_scrubber.py and remove the
four phone-specific xfail markers once those tests pass.

The fifth xfailed test, test_mixed_pii_and_text, exposes a
separate street-address false positive. I will leave that
pattern and marker unchanged in this fix.

I used ChatGPT to help organize this plan and draft the wording.
I ran the reproduction commands myself. Implementation and
after-fix testing have not started.

---

## Your branch

**Branch**

`fix/53-parenthesized-phone-numbers`

Fork: https://github.com/Ataliosos/pathreview-ai301-fa26-s3

Implementation commit: `bf05700`

I committed and pushed the phone-number fix and tests to my fork.

**Evidence**

Before the change, I tested on Windows with Python 3.13.0 at commit
`2f4e82f52efbcfcc57d65b3fa5348672163ca088`.

Command:

```powershell
.\.venv\Scripts\python.exe -c "from safety.pii_scrubber import PIIScrubber; s = PIIScrubber(); text = 'Call me at (555) 123-4567'; print('Input:', text); print('Scrubbed:', s.scrub(text)); print('Detected:', s.detect(text))"
```

Output:

```text
Input: Call me at (555) 123-4567
Scrubbed: Call me at (555) 123-4567
2026-10-06 18:22:55 [info     ] pii_detected                   count=0 types=0
Detected: []
```

After changing the US phone-number pattern, I repeated the same
input using the same environment.

Command:

```powershell
.\.venv\Scripts\python.exe -c "from safety.pii_scrubber import PIIScrubber; s = PIIScrubber(); text = 'Call me at (555) 123-4567'; print('Scrubbed:', s.scrub(text)); print('Detected:', s.detect(text))"
```

Output:

```text
Scrubbed: Call me at [REDACTED]
2026-10-06 18:51:42 [info     ] pii_detected                   count=1 types=1
Detected: [{'type': 'phone_us', 'value': '(555) 123-4567', 'start': 11, 'end': 25}]
```

The full phone number is now redacted. Detection returns its complete
value and the correct position in the original text.

I removed the four fixed phone tests' xfail markers, strengthened
redaction and detection assertions, and added boundary checks.

Focused test command:

```powershell
.\.venv\Scripts\python.exe -m pytest tests/unit/test_pii_scrubber.py -q -rxX
```

Final summary:

```text
26 passed, 1 xfailed in 0.23s
```

The remaining expected failure is `test_mixed_pii_and_text`.
I reproduced its separate street-address false positive before the
phone fix and left that pattern and marker unchanged.

Broader unit test command:

```powershell
.\.venv\Scripts\python.exe -m pytest tests/unit -m unit -q -rxX --tb=short
```

Output summary:

```text
381 passed, 49 xfailed, 2 warnings in 36.89s
```

Code-quality commands and results:

```text
.\.venv\Scripts\python.exe -m ruff check .
All checks passed!

.\.venv\Scripts\python.exe -m black --check .
All done! ✨ 🍰 ✨
110 files would be left unchanged.

.\.venv\Scripts\python.exe -m mypy api/ core/ ingestion/ rag/ agent/ safety/
Success: no issues found in 76 source files

git diff --check
```

`git diff --check` produced no output.

I used ChatGPT for help with the implementation, test changes, and
documentation. I ran the commands and reviewed the results myself.

---

## Eval iterations

**Run history**

I completed one full evaluation run after filling the installed
rubric, evidence guide, and procedure. Earlier attempts stopped
because I was in the wrong directory or the installed rubric was
still empty; they produced no agreement score.

The completed run reported:

```text
categories: clear-accept 7/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)
```

This is the final run saved in `eval-run.txt`.

**Package analysis**

For `pkg-01`, my rubric returned `reject`, and the gold label was
also `reject`.

The candidate diagnosis says:

> The Python-version difference is a red herring; the tokenizer has
> always been too strict about colon items.

But the reproduction evidence says:

> `--debug` on the failing run shows the error is raised by
> argparse's `parse_args` while consuming positionals; the request
> items are never handed to HTTPie's item parser.

The same request items also work without the flag. The plan proposes
changing the tokenizer even though the evidence shows the failure
happens before the items reach it. That contradicts my Evidence-based
diagnosis check and leaves the observed cause unresolved.

**Check rationale**

My Evidence-based diagnosis check reads:

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Evidence-based diagnosis | The plan's stated cause compared with the issue context and reproduction steps and artifacts. | Pass if the diagnosis fits the reproduced behavior. A suspected cause may pass when identified as a hypothesis with a concrete way to verify it. Fail if the diagnosis ignores or contradicts relevant evidence. | required |

I wrote it this way because a detailed plan can still target the
wrong part of the code. I want the diagnosis checked against what
actually happened. I also allow a suspected cause when the author
explains how to test it, because investigation can be a useful first
step without pretending the cause is already proven.

**Trade-offs**

This check allows a hypothesis with a concrete verification step.
That means it can accept an investigation whose suspected cause
later turns out to be wrong. I accept that risk because the plan
makes the uncertainty visible and gives a way to resolve it.

It still rejects `pkg-01`, where the diagnosis dismisses evidence
that points to a different code path. My full evaluation matched all
20 gold labels, but that result does not prove the rubric will judge
every future plan correctly.

---

Related paths: `plan.md` and `eval-run.txt` in this directory;
the skill files in `tools/plan-check/`.
