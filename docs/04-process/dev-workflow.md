# Development Workflow

> **Daily dev loop (human + LLM)**
>
> How we work together with AI to build features, fix bugs, and ship code. This is the playbook for productive human-LLM collaboration.

---

## Purpose

This document defines:
- **How humans and LLMs collaborate** on development
- **The daily workflow** from idea to production
- **Quality gates** and checks along the way
- **Tools and processes** we use

---

## Workflow Overview

```
Idea/Task → Plan → Implement → Test → Review → Deploy → Validate → Learn
     ↑                                                                ↓
     └────────────────────── Feedback Loop ─────────────────────────┘
```

---

## Phase 1: Planning

### Human Responsibilities
1. **Define the problem**
   - What are we trying to solve?
   - Who is this for?
   - Why does it matter?

2. **Set success criteria**
   - How will we know it works?
   - What metrics matter?

3. **Clarify constraints**
   - Timeline/deadline
   - Technical limitations
   - Must-haves vs nice-to-haves

### LLM Responsibilities
1. **Ask clarifying questions**
   - Surface ambiguities
   - Identify missing requirements
   - Challenge assumptions

2. **Research the codebase**
   - Find relevant existing code
   - Identify patterns to follow
   - Surface potential conflicts

3. **Propose approach**
   - Suggest implementation strategy
   - Identify files to change
   - Estimate scope and complexity

### Outputs
- [ ] Feature spec or clear task description
- [ ] Technical approach agreed upon
- [ ] Success criteria defined
- [ ] Files/areas of codebase identified

---

## Phase 2: Implementation

### LLM Responsibilities
1. **Write code**
   - Follow existing patterns
   - Write self-documenting code
   - Include helpful comments for complex logic
   - Think about edge cases

2. **Write tests**
   - Unit tests for logic
   - Integration tests for APIs
   - E2E tests for critical paths
   - Test edge cases and errors

3. **Update documentation**
   - Update relevant docs (API docs, README, etc.)
   - Add code comments where needed
   - Update system map if architecture changes

### Human Responsibilities
1. **Review code as it's written**
   - Check approach makes sense
   - Verify edge cases considered
   - Ensure code is readable

2. **Test manually**
   - Try the feature in browser/app
   - Look for UX issues
   - Verify it solves the problem

3. **Provide feedback**
   - Request changes if needed
   - Clarify requirements if misunderstood

### Quality Checks
- [ ] Code follows existing patterns
- [ ] Tests cover main paths and edge cases
- [ ] No security vulnerabilities (injection, XSS, etc.)
- [ ] Performance is acceptable
- [ ] Code is readable and maintainable
- [ ] Documentation updated

---

## Phase 3: Testing

### Automated Testing

**Unit Tests**
- Test individual functions/components
- Mock dependencies
- Fast and focused

**Integration Tests**
- Test component interactions
- Test API endpoints
- Use test database

**E2E Tests**
- Test critical user flows
- Run in real browser
- Catch integration issues

### Manual Testing

**Developer Testing**
- Test happy path
- Test error cases
- Test edge cases
- Test on different browsers/devices (if UI)

**QA Testing** (if applicable)
- Follow test plan
- Exploratory testing
- Accessibility testing
- Performance testing

### Checklist
- [ ] All tests passing
- [ ] Manual testing complete
- [ ] No console errors
- [ ] Accessibility verified (keyboard nav, screen reader)
- [ ] Responsive design works (if UI)
- [ ] Performance acceptable

---

## Phase 4: Code Review

### Before Requesting Review
- [ ] Code is complete
- [ ] Tests are passing
- [ ] Self-review done (read your own code)
- [ ] Documentation updated
- [ ] PR description explains what/why

### PR Description Template
```markdown
## What
[Brief description of what changed]

## Why
[Why we made this change]

## How
[Technical approach, key decisions]

## Testing
- [ ] Unit tests added/updated
- [ ] Manual testing done
- [ ] E2E tests added/updated (if applicable)

## Screenshots (if UI changes)
[Screenshots of before/after]

## Checklist
- [ ] Code follows style guide
- [ ] Tests passing
- [ ] Documentation updated
- [ ] No new security issues
- [ ] Performance impact considered
```

### Code Review Guidelines

**What to Look For:**
- **Correctness:** Does the code do what it's supposed to?
- **Tests:** Are edge cases covered?
- **Readability:** Can you understand it?
- **Maintainability:** Can it be changed easily later?
- **Performance:** Are there obvious inefficiencies?
- **Security:** Any vulnerabilities?

**Good Feedback:**
- Be specific: "This function could be simplified" + example
- Explain why: "This approach might cause race conditions because..."
- Ask questions: "What happens if this API call fails?"
- Praise good work: "Nice abstraction, this is very readable"

**Review Checklist:**
- [ ] Logic is correct
- [ ] Tests are comprehensive
- [ ] Code is readable
- [ ] No security issues
- [ ] No performance issues
- [ ] Documentation updated
- [ ] Follows existing patterns

---

## Phase 5: Deployment

### Pre-Deployment
- [ ] All tests passing in CI
- [ ] Code review approved
- [ ] Branch is up-to-date with main
- [ ] Feature flag configured (if needed)

### Deployment Process

**1. Merge to Main**
```bash
git checkout main
git pull origin main
git merge feature-branch
git push origin main
```

**2. Deploy to Staging**
- Automated via CI/CD
- Verify deployment succeeded
- Smoke test on staging

**3. Deploy to Production**
- Automated via CI/CD (or manual trigger)
- Monitor deployment
- Verify health checks passing

**4. Enable Feature** (if behind feature flag)
- Start with internal users (0-1%)
- Gradual rollout (1% → 10% → 50% → 100%)
- Monitor metrics and errors at each step

### Post-Deployment
- [ ] Feature works in production
- [ ] No spike in errors
- [ ] Metrics look healthy
- [ ] Rollback plan ready if needed

---

## Phase 6: Validation

### Immediate (First Hour)
- Monitor error rates
- Check performance metrics
- Watch for user complaints
- Verify analytics tracking

### Short Term (First Week)
- Track feature usage
- Monitor success metrics
- Collect user feedback
- Watch for unexpected behavior

### Long Term (First Month)
- Analyze impact on key metrics
- Compare to success criteria
- Identify improvements needed
- Document learnings

### Update Logs
- [ ] Implementation log updated (what we built)
- [ ] Validation log updated (what actually happened)
- [ ] Bug log updated (if bugs found)
- [ ] Insights updated (what we learned)

---

## Phase 7: Iteration

### Based on Validation
- Did we hit our goals? If not, why?
- What's working well?
- What needs improvement?
- What did we learn?

### Next Steps
- Bug fixes (if needed)
- Improvements based on feedback
- New features based on usage patterns
- Documentation of learnings

---

## Human-LLM Collaboration Tips

### When to Use LLM

**Great for LLM:**
- Writing boilerplate code
- Generating tests
- Refactoring code
- Finding bugs
- Explaining complex code
- Suggesting approaches
- Researching codebase

**Not Great for LLM:**
- Making product decisions
- Understanding user needs (without context)
- Creative problem solving requiring deep domain knowledge
- Evaluating trade-offs without guidance

### How to Prompt LLM Effectively

**Be Specific:**
- ❌ "Add a feature for users"
- ✅ "Add a button to the user profile page that lets users export their data as CSV"

**Provide Context:**
- Link to relevant docs
- Share existing patterns to follow
- Explain why you need this
- Define success criteria

**Iterate:**
- Start with plan, get feedback
- Implement incrementally
- Review and refine
- Test thoroughly

**Examples of Good Prompts:**
```
"I need to add a new API endpoint for exporting user data.
It should:
- Require authentication
- Return CSV format
- Include all user data except passwords
- Follow the same pattern as the /api/users/:id endpoint
Can you create a plan for this?"
```

```
"This function is hard to read. Can you refactor it to be
more clear? Keep the same functionality, but break it into
smaller functions with descriptive names."
```

```
"I'm getting a race condition bug in the checkout flow.
When users click submit twice quickly, we create two orders.
Can you help me debug and fix this?"
```

---

## Tools We Use

### Development
- **IDE:** [Your IDE]
- **Version Control:** Git + GitHub/GitLab
- **Package Manager:** [npm/yarn/pnpm/etc]
- **Build Tool:** [Vite/webpack/etc]

### Testing
- **Unit Tests:** [Jest/Vitest/pytest/etc]
- **E2E Tests:** [Playwright/Cypress/etc]
- **Test Coverage:** [Coverage tool]

### CI/CD
- **CI Platform:** [GitHub Actions/CircleCI/etc]
- **Deployment:** [Vercel/AWS/etc]
- **Monitoring:** [Sentry/Datadog/etc]

### Documentation
- **Docs:** This `/docs` folder
- **API Docs:** [Swagger/Postman/etc]
- **Architecture:** System map in `/docs/00-context/`

### LLM Tools
- **Coding Assistant:** [GitHub Copilot/Claude/etc]
- **Chat Interface:** [ChatGPT/Claude/etc]
- **Code Review:** [AI-assisted review tool if any]

---

## Emergency Procedures

### Production Bug

**1. Assess Severity**
- Critical (all users affected, data loss): Fix immediately
- High (major feature broken): Fix within hours
- Medium (minor feature issue): Fix within day
- Low (cosmetic issue): Fix in next sprint

**2. Immediate Action**
- Rollback if possible and safe
- Add monitoring/logging if needed
- Communicate to team/users

**3. Fix**
- Reproduce bug
- Find root cause
- Write test that catches bug
- Fix bug
- Verify fix works
- Deploy fix

**4. Post-Mortem**
- Document in bug log
- Identify why it wasn't caught
- Add prevention measures
- Update processes if needed

---

### Rollback Procedure

**When to Rollback:**
- Error rate spikes significantly
- Critical feature broken
- Security vulnerability discovered
- Performance degradation severe

**How to Rollback:**
```bash
# If using feature flag
Set feature flag to 0% in admin panel

# If need to revert deploy
git revert [commit-hash]
git push origin main
# Trigger deployment

# If database migration
Run down migration
Verify data integrity
```

**After Rollback:**
- Communicate to team
- Investigate root cause
- Fix issue
- Re-deploy with fix

---

## Definition of Done

A task is "done" when:
- [ ] Code is written and reviewed
- [ ] Tests are written and passing
- [ ] Manually tested and verified
- [ ] Documentation updated
- [ ] Deployed to production
- [ ] Feature flag enabled (if applicable)
- [ ] Metrics tracking working
- [ ] Team informed
- [ ] Logs updated

See [definition-of-done.md](definition-of-done.md) for details.

---

## Related Documents

- [Definition of Done](definition-of-done.md)
- [LLM Prompts](llm-prompts.md)
- [Testing Strategy](../02-features/*/test-plan.md)
- [Deployment Guide](../00-context/system-map.md)
