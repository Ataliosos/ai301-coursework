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

1. My first full attempt hit a Windows `UnicodeEncodeError` while passing issue text to Claude. It graded 13 issues, with 10 agreements, but seven errors meant the harness did not write `eval-run.txt`.
2. I set `PYTHONUTF8=1` and ran the full eval again. It completed at **16/20**. The disagreements were `issue-01`, `issue-04`, `issue-09`, and `issue-19`.
3. I revised **Bounded contribution** to allow related steps under one goal and **Available work** to release claims with no work for over 90 days. A partial `--only issue-01,issue-04,issue-09,issue-19` run matched **4/4**.
4. I ran the full eval with `--save-run eval-run.txt`. It matched **19/20**, passed the **18/20** bar, and matched at least one verdict in every category. The remaining disagreement was `issue-19`.

**Issue analysis**

For scored `issue-19`, my rubric decided **reject**, while the gold label was **accept**. Its body says, “Selecting large subgraphs in proof mode freezes the UI,” and lists slow matchers and the UI waiting for a matching thread as potential causes. My **Bounded contribution** check requires one defined goal with an observable result, so fixing that freeze can fit it. The rubric still read the multiple performance and threading suggestions as a larger change and failed that required check. I think the gold label treats those suggestions as possible approaches to the single freeze rather than separate requirements.

**Check rationale**

My current **Bounded contribution** check says: “Pass if the issue has one defined goal and names an observable result, affected feature, or files. Related steps across several files, several examples of the same missing behavior, and multiple proposed causes of one bug still pass. Fail for a usage question, an open-ended tracking or umbrella issue without a specific deliverable, an unresolved product or design choice that blocks implementation, a maintainer-stated core redesign, or two or more abandoned unmerged attempts with no later settled plan.”

I changed it after the 16/20 run because a documentation update spanning several pages (`issue-01`) and several missing previews of the same feature (`issue-04`) were finite work. Counting files or examples alone made the check reject them. The updated check asks whether there is one defined goal and a result I could verify.

**Trade-offs**

This broader wording accepted `issue-01` and `issue-04` in the partial recheck, but `issue-19` still failed in the final full run. A report with several possible performance fixes can be read as one bug or as too much for a first contribution. I kept the check because it still rejects open-ended work while the final eval reaches 19/20.

---

## Selection rationale

**Selection rationale**

1. I chose #53 because I am interested in cybersecurity and have used Python for basic scripting. Redacting a phone number is a privacy problem I can understand. The issue names one code area and four failing tests, which feels manageable for my available time.
2. My skill correctly found recent activity, no assignee or open PR, and a clear way to reproduce the bug. It ranked #53 first. I also considered that I would enjoy learning how the scrubber handles different phone formats; that personal interest helps me choose among accepted issues.
3. I expect the hard part of claiming it to be following Path Review’s claim format and checking the current issue discussion before I post. The course allows students to share an issue, so another student’s claim would not block me. I will write the claim in Unit 2.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/issue-select/`.
