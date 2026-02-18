---
name: finish
description: Structured branch completion — verify, decide, and clean up when implementation is done
---
# Finish Directive

## Overview
Guide completion of development work by verifying tests and presenting clear options for what to do with the branch.

**Core principle:** Verify tests → Present options → Execute choice → Clean up.

## Below are what agent MUST do:

### Step 1: Verify Tests
Run the full test suite BEFORE presenting any options.
```bash
# Use the project's test command, e.g.:
pytest / npm test / go test ./... / cargo test
```
- If tests **fail**: Show failures. Do NOT proceed to Step 2. Fix first.
- If tests **pass**: Continue.

### Step 2: Present Options
Present exactly these 4 options — no more, no less:
```
Implementation complete. All tests pass. What would you like to do?

1. Merge into <base-branch> locally
2. Push and create a Pull Request
3. Keep the branch as-is (handle it later)
4. Discard this work

Which option?
```

### Step 3: Execute Choice

**Option 1 — Merge locally:**
```bash
git checkout <base-branch>
git pull
git merge <feature-branch>
<run tests again on merged result>
git branch -d <feature-branch>
```

**Option 2 — Create PR:**
```bash
git push -u origin <feature-branch>
gh pr create --title "<title>" --body "## Summary
- <bullet of what changed>

## Test Plan
- [ ] <verification steps>"
```

**Option 3 — Keep as-is:**
Report: "Branch `<name>` kept. No changes made."

**Option 4 — Discard:**
Require typed confirmation first:
```
This will permanently delete branch <name> and all its commits.
Type 'discard' to confirm.
```
Then:
```bash
git checkout <base-branch>
git branch -D <feature-branch>
```

## Red Flags — Never
- Proceed with failing tests
- Merge without re-running tests on the merged result
- Delete work without typed confirmation
- Force-push without explicit user request
- Add extra options beyond the 4 listed
