# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/53

**Verdict output**

Ranked read-out (accepted, in fit order):

1. #53 — PII scrubber: parenthesized phone numbers. Safety/cybersecurity, one regex, 4 failing tests.
2. #55 — Skill extractor: JS/TS detection. Python + 5 xfail tests, wider surface, no good-first-issue label.
3. #73 — README vs .env.example key mismatch. Clean but docs-only; no test to debug.

None rejected; all required checks pass on all three. Everything, including the ranking, is in the block below.

```json
[
  {
    "rank": 1,
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/53",
    "title": "PII scrubber fails to redact parenthesized US phone numbers",
    "fit_reason": "Safety/cybersecurity labeled; smallest reproducible loop: one regex in pii_scrubber.py, 4 named failing tests to watch go green.",
    "checks": [
      {"name": "Maintained code", "grade": "pass", "evidence": "archived: false; newest main commit 2026-09-16 by human Aburke225 (6 days ago)"},
      {"name": "In-use development", "grade": "pass", "evidence": "No releases, but human commits 2026-09-16 and 2026-08-24 are within 180 days"},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "One goal, one file: phone regex in pii_scrubber.py misses '(555) 123-4567'"},
      {"name": "Available work", "grade": "pass", "evidence": "No assignee, no linked PR; repo-wide /pulls?state=all is empty; zero comments"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template never mention AI, LLMs, or Copilot"},
      {"name": "Clear start", "grade": "pass", "evidence": "Repro calls scrub(...) and detect(...), target file, and 4 failing test names"}
    ],
    "verdict": "accept"
  },
  {
    "rank": 2,
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/55",
    "title": "Skill extractor fails to detect JavaScript and TypeScript",
    "fit_reason": "Python plus 5 xfail tests run locally, and JS/TS matches CodePath web background; ranks below #53 for wider surface and no good-first-issue label.",
    "checks": [
      {"name": "Maintained code", "grade": "pass", "evidence": "archived: false; newest main commit 2026-09-16 by human Aburke225 (6 days ago)"},
      {"name": "In-use development", "grade": "pass", "evidence": "No releases, but human commits 2026-09-16 and 2026-08-24 are within 180 days"},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Same missing behavior across 3 functions in one file, skill_extractor.py; rubric allows it"},
      {"name": "Available work", "grade": "pass", "evidence": "No assignee, no linked PR; repo-wide /pulls?state=all is empty; zero comments"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template never mention AI, LLMs, or Copilot"},
      {"name": "Clear start", "grade": "pass", "evidence": "Repro command 'pytest tests/unit/test_skill_extractor.py -q' and 5 failing test names"}
    ],
    "verdict": "accept"
  },
  {
    "rank": 3,
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "title": "README and .env.example disagree about which LLM API key to set",
    "fit_reason": "Tightly bounded two-file docs alignment, but documentation only: no failing test and nothing to debug.",
    "checks": [
      {"name": "Maintained code", "grade": "pass", "evidence": "archived: false; newest main commit 2026-09-16 by human Aburke225 (6 days ago)"},
      {"name": "In-use development", "grade": "pass", "evidence": "No releases, but human commits 2026-09-16 and 2026-08-24 are within 180 days"},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "One goal: align README.md and .env.example, with core/config.py as source of truth"},
      {"name": "Available work", "grade": "pass", "evidence": "No assignee, no linked PR; repo-wide /pulls?state=all is empty; zero comments"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template never mention AI, LLMs, or Copilot"},
      {"name": "Clear start", "grade": "pass", "evidence": "Names both files and the exact mismatch: README says OPENROUTER_API_KEY, .env.example omits it"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

1. My first full run had a Windows `UnicodeEncodeError`. It graded 13 issues and agreed on 10, but seven issues errored, so the harness did not save a run.
2. I set `PYTHONUTF8=1` and tried the full run again. This time it finished at **16/20**. It disagreed on `issue-01`, `issue-04`, `issue-09`, and `issue-19`.
3. I updated the Bounded contribution and Available work checks. Then I used `--only issue-01,issue-04,issue-09,issue-19` to check those four issues. That partial run agreed on **4/4**.
4. I ran the full eval again with `--save-run eval-run.txt`. The saved run agreed on **19/20**, passed the 18/20 bar, and matched at least one issue in every category. `issue-19` was the one disagreement.

**Issue analysis**

For `issue-19`, my rubric said **reject**, but the gold label said **accept**. The issue says, “Selecting large subgraphs in proof mode freezes the UI.” It lists slow matchers and the UI waiting for a matching thread as possible causes. My Bounded contribution check treated the different performance suggestions as too much work for a first issue. I can see why the gold label accepted it: all the suggestions are about fixing the same freeze.

**Check rationale**

My current Bounded contribution check says: “Pass if the issue has one defined goal and names an observable result, affected feature, or files. Related steps across several files, several examples of the same missing behavior, and multiple proposed causes of one bug still pass. Fail for a usage question, an open-ended tracking or umbrella issue without a specific deliverable, an unresolved product or design choice that blocks implementation, a maintainer-stated core redesign, or two or more abandoned unmerged attempts with no later settled plan.”

I changed this check after my 16/20 run. It had rejected `issue-01` because the documentation work touched several pages and `issue-04` because it listed several missing previews. Those issues still had clear goals. I wanted the check to look at the result of the work, not just how many files or examples the issue mentions.

**Trade-offs**

The change helped my rubric accept `issue-01` and `issue-04`. It still rejected `issue-19` in the final run. An issue with several possible fixes can be hard to judge: it might be one bug, but it might take more work than I expect. I kept this wording because the full run reached 19/20 and the check still filters out issues with no clear result.

---

## Selection rationale

**Selection rationale**

1. I chose #53 because I like cybersecurity and I have used Python before. The bug is about hiding a phone number, so I understand why it matters. There are four tests I can run, and the change looks small enough for me to start with.
2. My skill found that the repo is active, the issue has no assignee or open PR, and the bug has a clear way to reproduce it. It ranked #53 first. I also picked it because I want to practice debugging and see how the phone-number code works. The rubric cannot decide what I personally want to learn.
3. I think claiming the issue will be straightforward once I follow the Unit 2 instructions. I will check the comments again before posting. Other students can work on the same Path Review issue, so their claims would not stop me.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/issue-select/`.
