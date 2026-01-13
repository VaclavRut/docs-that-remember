# Definition of Done

> **When docs/code are "done"**
>
> Clear, unambiguous criteria for when a task, feature, or document is complete. This prevents miscommunication and ensures consistent quality.

---

## Purpose

This document defines what "done" means for:
- Features
- Bug fixes
- Documentation
- Refactoring
- Technical debt

Clear "done" criteria ensure:
- Nothing gets shipped half-finished
- Quality standards are maintained
- Everyone has the same expectations
- No confusion about whether something is complete

---

## Feature is Done When...

### Code Complete
- [ ] All acceptance criteria from feature spec are met
- [ ] Code follows existing patterns and style guide
- [ ] No obvious performance issues
- [ ] No security vulnerabilities
- [ ] Error handling is comprehensive
- [ ] Edge cases are handled
- [ ] Code is readable and well-organized

### Tests Complete
- [ ] Unit tests written for business logic
- [ ] Integration tests written for APIs
- [ ] E2E tests written for critical user paths
- [ ] All tests passing in CI
- [ ] Code coverage meets target (typically 80%+)
- [ ] Edge cases and error paths tested

### Documentation Complete
- [ ] Code comments added for complex logic
- [ ] API documentation updated (if API changes)
- [ ] User guide updated (if user-facing changes)
- [ ] System map updated (if architecture changes)
- [ ] README updated (if setup/usage changes)
- [ ] Implementation log updated (what changed and why)

### Review Complete
- [ ] Code reviewed by at least one other developer
- [ ] All review comments addressed or discussed
- [ ] Changes approved by reviewer
- [ ] No unresolved discussions

### Deployment Complete
- [ ] Merged to main branch
- [ ] Deployed to staging environment
- [ ] Smoke tested on staging
- [ ] Deployed to production
- [ ] Feature flag configured (if applicable)
- [ ] Rollback plan documented and ready

### Validation Complete
- [ ] Feature works in production
- [ ] No spike in errors or monitoring alerts
- [ ] Analytics/metrics tracking working
- [ ] Success criteria met (or tracking toward them)
- [ ] Validation log entry created (within first week)

### Communication Complete
- [ ] Team notified of deployment
- [ ] Users notified (if customer-facing change)
- [ ] Support team trained (if needed)
- [ ] Documentation shared with stakeholders

---

## Bug Fix is Done When...

### Fix Complete
- [ ] Root cause identified and documented
- [ ] Fix implemented
- [ ] Bug no longer reproducible
- [ ] No regressions introduced (related features still work)

### Tests Complete
- [ ] Test written that catches this bug
- [ ] Test fails on old code, passes on new code
- [ ] Regression tests pass
- [ ] All tests passing in CI

### Documentation Complete
- [ ] Bug log updated with:
  - Root cause
  - How it was fixed
  - How to prevent similar bugs
- [ ] Implementation log updated (if significant change)

### Review Complete
- [ ] Code reviewed
- [ ] Fix verified by reviewer

### Deployment Complete
- [ ] Merged and deployed
- [ ] Verified fixed in production
- [ ] Monitoring confirms no recurrence

### Prevention Complete
- [ ] Prevention measures identified (tests, linting, process changes)
- [ ] Prevention measures implemented
- [ ] Team informed of learnings

---

## Documentation is Done When...

### Content Complete
- [ ] All sections filled out (no TODOs or placeholders)
- [ ] Information is accurate and up-to-date
- [ ] Examples are relevant and tested
- [ ] Links work and point to correct locations

### Quality Complete
- [ ] Writing is clear and concise
- [ ] Spelling and grammar are correct
- [ ] Formatting is consistent
- [ ] Code examples are properly formatted

### Review Complete
- [ ] Reviewed by at least one other person
- [ ] Technical accuracy verified
- [ ] Clarity verified (would a new team member understand?)

### Accessibility Complete
- [ ] Organized with clear headings
- [ ] Table of contents (if long doc)
- [ ] Easy to navigate
- [ ] Findable from relevant entry points

---

## Refactoring is Done When...

### Code Complete
- [ ] Code is cleaner/more maintainable than before
- [ ] Functionality is identical to before (no behavior changes)
- [ ] Performance is same or better
- [ ] Code complexity reduced (measurable via tools if possible)

### Tests Complete
- [ ] All existing tests still pass
- [ ] No new tests needed (behavior unchanged)
- [ ] Code coverage same or improved

### Documentation Complete
- [ ] Implementation log updated with:
  - What was refactored
  - Why it was refactored
  - What improved
- [ ] Code comments updated (if old comments now incorrect)

### Review Complete
- [ ] Reviewed by another developer
- [ ] Reviewer confirms code is clearer/better

### Deployment Complete
- [ ] Deployed to production
- [ ] No regressions observed
- [ ] Monitoring confirms no issues

---

## Technical Debt Paydown is Done When...

### Issue Resolved
- [ ] Technical debt item fully addressed
- [ ] Code/architecture is now in desired state
- [ ] No half-measures or temporary fixes

### Tests Complete
- [ ] Tests updated for new approach
- [ ] All tests passing
- [ ] Coverage maintained or improved

### Documentation Complete
- [ ] Technical debt log updated (moved from "current" to "resolved")
- [ ] Implementation log updated
- [ ] Decision log updated (if approach changed)
- [ ] Code comments removed (if debt was commented as "TODO" or "HACK")

### Review Complete
- [ ] Reviewed by another developer
- [ ] Reviewer confirms debt is resolved

### Team Informed
- [ ] Team notified of changes
- [ ] New patterns/approaches communicated
- [ ] Old patterns deprecated (if applicable)

---

## Pull Request is Done When...

### Before Creating PR
- [ ] All commits have clear messages
- [ ] Branch is up-to-date with main
- [ ] PR description filled out completely
- [ ] Self-review completed
- [ ] All tests passing locally

### PR Description Includes
- [ ] What changed
- [ ] Why it changed
- [ ] How it was implemented
- [ ] Testing done
- [ ] Screenshots (if UI changes)
- [ ] Breaking changes (if any)
- [ ] Related issues/docs linked

### After Review
- [ ] All comments addressed or discussed
- [ ] Requested changes made
- [ ] Approvals received
- [ ] CI checks passing
- [ ] Conflicts resolved

### After Merge
- [ ] Branch deleted (after successful merge)
- [ ] Related issues closed/updated
- [ ] Deployment verified

---

## Sprint/Milestone is Done When...

### All Tasks Complete
- [ ] All planned tasks meet their "done" criteria
- [ ] No critical bugs open
- [ ] All code merged and deployed

### Documentation Updated
- [ ] Feature specs accurate (reflect what was actually built)
- [ ] System map updated
- [ ] User docs updated
- [ ] API docs updated

### Validation Started
- [ ] Metrics tracking configured
- [ ] Success criteria being measured
- [ ] Validation log entries created (or scheduled)

### Retrospective Complete
- [ ] Team met to discuss what went well/poorly
- [ ] Action items identified
- [ ] Learnings documented in insights.md

---

## Quality Gates

These are non-negotiable minimums. Work cannot be considered "done" without meeting these:

### Code Quality Gates
- ✅ Passes linter with no errors
- ✅ No critical security vulnerabilities (from security scanner)
- ✅ Code coverage ≥ 80% (or same as before)
- ✅ No console.log or debug code left in
- ✅ No hardcoded credentials or secrets

### Testing Quality Gates
- ✅ All tests passing
- ✅ All acceptance criteria tested
- ✅ Critical paths have E2E tests

### Review Quality Gates
- ✅ At least one approval from another developer
- ✅ No unresolved "must fix" comments

### Deployment Quality Gates
- ✅ Deployed to staging first
- ✅ Tested on staging
- ✅ Rollback plan ready
- ✅ No production errors after deployment

---

## Exceptions

Sometimes we need to ship before meeting all "done" criteria. This is okay IF:

### Documented Exception
- [ ] Reason for exception documented
- [ ] What's missing documented
- [ ] Plan to complete documented
- [ ] Stakeholders informed and agreed

### Time-Boxed
- [ ] Deadline set for completing missing items
- [ ] Reminder/task created to finish

### Not Critical
- [ ] Missing items are not critical (e.g., docs can follow code by a few days)
- [ ] No security/data/critical functionality issues

### Example Exception
```markdown
## Known Incomplete Items

**What's missing:** User guide for new export feature

**Why:** Feature needs to ship today for customer demo, user guide takes 2 more hours

**Plan:** User guide will be completed by Friday (2 days)

**Impact:** Internal users can use feature without docs, external users won't see it until docs done

**Approved by:** [Product Manager name]
```

---

## Checklist Template

Use this checklist for every feature:

```markdown
## Feature Done Checklist

### Code
- [ ] All acceptance criteria met
- [ ] Code follows style guide
- [ ] No security issues
- [ ] Error handling comprehensive
- [ ] Edge cases handled

### Tests
- [ ] Unit tests written and passing
- [ ] Integration tests written and passing
- [ ] E2E tests written and passing (if applicable)
- [ ] Code coverage ≥ 80%

### Documentation
- [ ] Code comments added
- [ ] API docs updated
- [ ] User guide updated
- [ ] System map updated
- [ ] Implementation log updated

### Review
- [ ] Code reviewed and approved
- [ ] All comments addressed

### Deployment
- [ ] Deployed to staging and tested
- [ ] Deployed to production
- [ ] Monitoring confirms healthy

### Validation
- [ ] Analytics tracking working
- [ ] No production errors
- [ ] Success metrics being measured

### Communication
- [ ] Team notified
- [ ] Users notified (if needed)
- [ ] Support trained (if needed)
```

---

## Related Documents

- [Dev Workflow](dev-workflow.md) - How we build features
- [Feature Specs](../02-features/*/feature-spec.md) - Acceptance criteria
- [Test Plans](../02-features/*/test-plan.md) - Testing requirements
- [Implementation Log](../03-logs/implementation-log.md) - What we built
