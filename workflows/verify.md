---
name: verify
description: Verification before completion — ensure it's actually fixed before claiming done
---
# Verify Directive

## The Iron Law
```
NEVER claim a task is complete without running verification.
"It should work" is not verification. Evidence is verification.
```

## Below are what agent MUST do:

### Step 1: Run the Tests
- Execute the full test suite. Do NOT just run the specific test you wrote.
- Confirm: all tests pass, no new failures, no skipped tests without explanation.

### Step 2: Reproduce the Original Issue
- If fixing a bug: reproduce the original failure scenario and confirm it no longer occurs.
- If adding a feature: walk through the exact user flow end-to-end.

### Step 3: Check for Regressions
- Run any integration or smoke tests.
- Check that adjacent functionality still works.
- Review the diff: does anything look unintentionally changed?

### Step 4: Verify the Claim
Before saying "done", confirm:
- [ ] The specific issue/feature is resolved/implemented
- [ ] All tests pass (including pre-existing tests)
- [ ] No new warnings or errors in output
- [ ] Code is clean (no debug logs, no commented-out code)
- [ ] Documentation updated if public interface changed

### Step 5: Report
- State what was verified and how.
- If anything is still uncertain, say so explicitly. Do NOT hide uncertainty.

## Red Flags — Do NOT Mark as Done If:
- Tests pass but you haven't reproduced the original scenario
- "I believe it should work" without running it
- New warnings appeared that weren't there before
- You only ran the new test, not the full suite
