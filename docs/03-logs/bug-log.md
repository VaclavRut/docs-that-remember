# Bug Log

> **Bugs, fixes, regressions**
>
> A chronological record of bugs discovered, how they were fixed, and whether they recurred. This helps identify patterns, prevent regressions, and improve quality over time.

---

## Purpose

This log tracks:
- **Bugs discovered** in production, staging, or development
- **Root causes** and how they were fixed
- **Patterns** in what breaks and why
- **Regressions** when old bugs resurface

This helps with:
- Understanding what types of bugs are common
- Preventing similar bugs in the future
- Identifying areas of the codebase that need improvement
- Training new team members on common pitfalls

---

## Bug Template

### [BUG-XXX] - [Short Description]

**Date Discovered:** YYYY-MM-DD

**Discovered By:** [Name/User Report/Monitoring]

**Severity:** [Critical | High | Medium | Low]

**Status:** [Open | In Progress | Fixed | Closed | Wontfix]

**Environment:** [Production | Staging | Development]

**Affected Users:** [Number/percentage of users affected]

**Symptoms:**
[What users see or experience]

**Steps to Reproduce:**
1. [Action 1]
2. [Action 2]
3. [Result]

**Expected Behavior:**
[What should happen]

**Actual Behavior:**
[What actually happens]

**Root Cause:**
[Technical explanation of why the bug occurred]

**Fix:**
[How it was fixed - technical details]

**Files Changed:**
- `path/to/file1.ts`
- `path/to/file2.ts`

**Prevention:**
[How we can prevent this type of bug in the future]
- Tests added: [describe]
- Process changes: [describe]
- Monitoring added: [describe]

**Related Issues:**
- Similar to [BUG-XXX]
- Caused by [Change in implementation-log]

**Fixed By:** [Name]

**Fixed Date:** YYYY-MM-DD

**Deployed:** YYYY-MM-DD

**Verified By:** [Name]

---

## Active Bugs

### Critical (P0)
> Must fix immediately, blocking users

| Bug ID | Description | Age (days) | Assigned To | Status |
|--------|-------------|------------|-------------|--------|
| [BUG-XXX] | [Brief description] | [#] | [Name] | [Status] |

### High Priority (P1)
> Impacting significant functionality, fix ASAP

| Bug ID | Description | Age (days) | Assigned To | Status |
|--------|-------------|------------|-------------|--------|
| [BUG-XXX] | [Brief description] | [#] | [Name] | [Status] |

### Medium Priority (P2)
> Fix in next sprint

| Bug ID | Description | Age (days) | Assigned To | Status |
|--------|-------------|------------|-------------|--------|
| [BUG-XXX] | [Brief description] | [#] | [Name] | [Status] |

### Low Priority (P3)
> Fix when convenient

| Bug ID | Description | Age (days) | Assigned To | Status |
|--------|-------------|------------|-------------|--------|
| [BUG-XXX] | [Brief description] | [#] | [Name] | [Status] |

---

## Resolved Bugs

### [BUG-001] - Users Unable to Save Profile Changes

**Date Discovered:** 2025-01-15

**Discovered By:** User report (support ticket #1234)

**Severity:** High

**Status:** Fixed

**Environment:** Production

**Affected Users:** ~5% of users (estimated 500 users)

**Symptoms:**
Users click "Save" button on profile page, see loading spinner, then nothing happens. Changes are not saved. No error message shown.

**Steps to Reproduce:**
1. Log in as user
2. Go to Profile page
3. Change email address
4. Click "Save"
5. Observe: spinner shows briefly, then disappears, but email not updated

**Expected Behavior:**
Profile should update and show success message

**Actual Behavior:**
No update, no feedback, just spinner disappearing

**Root Cause:**
API endpoint `/api/profile` was returning 401 Unauthorized due to middleware checking for `userId` in token payload, but we changed token structure to use `user_id` (underscore) in a recent update. Frontend was sending valid token but backend was rejecting it.

**Why It Wasn't Caught:**
- Tests were mocking the auth middleware
- We didn't have E2E tests for profile update
- Change was deployed without full regression testing

**Fix:**
1. Updated auth middleware to check both `userId` and `user_id` for backward compatibility
2. Added migration to reissue tokens with correct structure
3. Added explicit error handling in frontend to show error messages

**Files Changed:**
- `src/middleware/auth.ts` - Added backward compatibility
- `src/components/Profile/ProfileForm.tsx` - Added error handling
- `tests/e2e/profile.spec.ts` - Added E2E test for profile update

**Prevention:**
- **Added E2E test** for profile update flow
- **Added monitoring** for 401 errors on profile endpoint
- **Process change:** All token structure changes require migration plan
- **Added test case** to verify backward compatibility of auth changes

**Related Issues:**
- [DEC-003] Decision to change token structure

**Fixed By:** John Smith

**Fixed Date:** 2025-01-16

**Deployed:** 2025-01-16 14:30 UTC

**Verified By:** QA team + 10 affected users

**Time to Fix:** 1 day (discovered afternoon, fixed next morning)

---

### [BUG-002] - Memory Leak in Dashboard Component

**Date Discovered:** 2025-01-18

**Discovered By:** Monitoring alert (high memory usage)

**Severity:** Medium

**Status:** Fixed

**Environment:** Production

**Affected Users:** Users who keep dashboard open for > 1 hour

**Symptoms:**
Browser tab becomes slow and unresponsive after dashboard is open for extended periods. Memory usage grows continuously.

**Steps to Reproduce:**
1. Open dashboard
2. Leave tab open for 1+ hour
3. Observe increasing memory usage in browser task manager

**Expected Behavior:**
Memory usage should remain stable

**Actual Behavior:**
Memory grows from 50MB to 500MB+ over time

**Root Cause:**
`setInterval` in Dashboard component was not being cleaned up on component unmount. Additionally, WebSocket connection was accumulating listeners on every re-render.

```typescript
// Buggy code:
useEffect(() => {
  setInterval(() => {
    fetchDashboardData();
  }, 30000);
  // Missing cleanup!
}, []);
```

**Fix:**
Added proper cleanup in useEffect:

```typescript
useEffect(() => {
  const intervalId = setInterval(() => {
    fetchDashboardData();
  }, 30000);

  return () => {
    clearInterval(intervalId);
  };
}, [fetchDashboardData]);
```

**Files Changed:**
- `src/components/Dashboard/Dashboard.tsx`
- `src/hooks/useWebSocket.ts`

**Prevention:**
- **Added linting rule** to warn about setInterval without cleanup
- **Added E2E test** that keeps dashboard open and monitors memory
- **Code review checklist** now includes "Are effects cleaned up?"
- **Added monitoring** for client-side memory usage

**Fixed By:** Sarah Johnson

**Fixed Date:** 2025-01-19

**Deployed:** 2025-01-19

**Verified By:** Load testing team

**Time to Fix:** 1 day

---

## Bug Patterns

### Common Bug Types
Track patterns to improve processes:

| Category | Count | % of Total | Prevention Strategy |
|----------|-------|------------|---------------------|
| Authentication/Authorization | [#] | [%] | Better E2E tests for auth flows |
| Memory Leaks | [#] | [%] | Linting rules, code review checklist |
| Race Conditions | [#] | [%] | Better async handling patterns |
| Null/Undefined Errors | [#] | [%] | Stricter TypeScript config |
| Validation Errors | [#] | [%] | Schema validation library |
| CSS/Layout Issues | [#] | [%] | Visual regression testing |

### Most Buggy Areas
| Component/Module | Bug Count | Action Needed |
|------------------|-----------|---------------|
| [Path/Component] | [#] | [Refactor/Add tests/etc] |

### Recurring Bugs
Bugs that keep coming back:

| Bug Pattern | Times Occurred | Root Cause | Permanent Fix |
|-------------|----------------|------------|---------------|
| [Pattern description] | [#] | [Why it keeps happening] | [How to stop it] |

---

## Bug Statistics

### By Month
| Month | Bugs Reported | Bugs Fixed | Still Open | Avg Time to Fix |
|-------|---------------|------------|------------|-----------------|
| 2025-01 | [#] | [#] | [#] | [days] |

### By Severity
| Severity | Opened | Fixed | Fix Rate |
|----------|--------|-------|----------|
| Critical | [#] | [#] | [%] |
| High | [#] | [#] | [%] |
| Medium | [#] | [#] | [%] |
| Low | [#] | [#] | [%] |

### By Source
| Source | Count | % of Total |
|--------|-------|------------|
| User Reports | [#] | [%] |
| Monitoring/Alerts | [#] | [%] |
| Internal Testing | [#] | [%] |
| Production Incidents | [#] | [%] |

---

## Regression Tracking

Bugs that came back after being fixed:

| Original Bug | First Fixed | Regressed | Times Regressed | Permanent Fix Date |
|--------------|-------------|-----------|-----------------|-------------------|
| [BUG-XXX] | YYYY-MM-DD | YYYY-MM-DD | [#] | YYYY-MM-DD |

---

## Won't Fix

Bugs we've decided not to fix, and why:

### [BUG-XXX] - [Description]
**Reason:** [Why we won't fix]
**Workaround:** [What users can do instead]
**Date Closed:** YYYY-MM-DD

---

## Related Documents

- [Implementation Log](implementation-log.md) - Code changes that may introduce bugs
- [Validation Log](validation-log.md) - Production issues after shipping
- [Test Plans](../02-features/*/test-plan.md) - Testing strategies
- [Insights](insights.md) - Learnings from bugs
