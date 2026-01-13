# Insights & Learnings

> **Learnings & future improvements**
>
> Patterns, principles, and wisdom gained from building this product. This is where we distill the lessons from all other logs into actionable knowledge.

---

## Purpose

This document captures:
- **Patterns** we've discovered (good and bad)
- **Principles** we've learned
- **Practices** that work (or don't)
- **Wisdom** for future work

This helps:
- New team members understand how we work and why
- Avoid repeating mistakes
- Codify what works well
- Guide future decisions

---

## Development Insights

### What Works Well

#### 1. [Insight Title]
**Context:** [When/where this applies]

**What we learned:**
[Description of the insight]

**Evidence:**
- [Example 1]
- [Example 2]
- [Data/outcome]

**Action:**
[What we do now because of this learning]

**Related:**
- [Link to decision log / implementation log]

---

#### 2. Type-Safe API Clients Prevent Runtime Errors
**Context:** Frontend-backend integration

**What we learned:**
Generating TypeScript types from backend schemas (OpenAPI/Prisma) catches integration errors at compile-time rather than runtime, saving debugging time and preventing production bugs.

**Evidence:**
- Caught 15 integration bugs during development that would have been runtime errors
- Reduced API-related bugs in production by 80% (from 10/month to 2/month)
- Onboarding developers spend less time understanding API contracts

**Action:**
- Always generate frontend types from backend schema
- Make type generation part of CI/CD pipeline
- Use Zod or similar for runtime validation at API boundaries

**Related:**
- [DEC-001] - Decision to use TypeScript
- [BUG-012] - API mismatch bug that led to this insight

---

#### 3. Small, Frequent Deployments Reduce Risk
**Context:** Release process

**What we learned:**
Deploying small changes frequently (daily) is far less risky than big releases every 2 weeks. Easier to debug, easier to rollback, faster feedback.

**Evidence:**
- When deploying daily: avg rollback rate 2%, avg time to fix 1 hour
- When deploying bi-weekly: avg rollback rate 15%, avg time to fix 4 hours
- User complaints decreased 40% with frequent deployments

**Action:**
- Deploy to production at least once per day
- Keep PRs small (< 400 lines)
- Feature flags for anything that can't be deployed in one piece

**Related:**
- [Validation Log entries] - Faster feedback loop
- [Bug Log] - Fewer bugs per deployment

---

### What Doesn't Work

#### 1. [Anti-Pattern Title]
**Context:** [When we tried this]

**What we learned:**
[Why it didn't work]

**Evidence:**
- [Example of failure]
- [Cost/impact]

**What we do instead:**
[Better approach]

**Related:**
- [Link to relevant logs]

---

#### 2. Optimistic UI Without Rollback Handling
**Context:** Frontend state management

**What we learned:**
Showing optimistic UI updates (pretending the server call succeeded before it actually does) improves perceived performance, BUT only if you properly handle rollback when the server call fails. Otherwise users see inconsistent state.

**Evidence:**
- [BUG-045] - User data got out of sync when network request failed
- [BUG-052] - User performed action on optimistically-added item, then it disappeared
- Generated 23 support tickets before we fixed it

**What we do instead:**
- Always implement rollback logic for optimistic updates
- Show clear UI feedback when rolling back
- Consider whether optimistic update is worth the complexity
- For critical operations (payments, etc), don't use optimistic UI

**Related:**
- [BUG-045], [BUG-052]
- [Decision Log: State Management]

---

#### 3. Generic "Something Went Wrong" Error Messages
**Context:** User-facing error handling

**What we learned:**
Generic error messages frustrate users and generate support tickets. Specific, actionable error messages help users self-serve and reduce support burden.

**Evidence:**
- "Something went wrong": 45% of users contacted support
- "Email address already in use. Try logging in or resetting your password": 12% contacted support
- Support ticket volume reduced 30% after improving error messages

**What we do instead:**
- Write specific error messages explaining what happened
- Tell users what to do next (call to action)
- Provide link to help docs when relevant
- Include error code for support team

**Related:**
- [Support ticket analysis]
- [UX guidelines doc]

---

## Technical Patterns

### Recommended Patterns

#### Pattern: [Pattern Name]
**Use When:** [Scenario where this pattern applies]

**Implementation:**
```typescript
// Code example
```

**Benefits:**
- [Benefit 1]
- [Benefit 2]

**Tradeoffs:**
- [Tradeoff 1]
- [Tradeoff 2]

**Examples in Codebase:**
- `path/to/example1.ts:45`
- `path/to/example2.ts:12`

---

#### Pattern: React Query for Server State
**Use When:** Fetching, caching, and updating server data in React components

**Implementation:**
```typescript
// Good pattern
const { data, isLoading, error } = useQuery({
  queryKey: ['user', userId],
  queryFn: () => fetchUser(userId),
  staleTime: 5 * 60 * 1000, // 5 minutes
});

// Not this
const [data, setData] = useState(null);
useEffect(() => {
  fetch(`/api/users/${userId}`)
    .then(res => res.json())
    .then(setData);
}, [userId]);
```

**Benefits:**
- Automatic caching and deduplication
- Loading and error states handled
- Automatic refetching and background updates
- Less boilerplate code

**Tradeoffs:**
- One more dependency
- Learning curve for team

**Examples in Codebase:**
- `src/hooks/useUser.ts`
- `src/components/Dashboard/Dashboard.tsx:23`

---

### Anti-Patterns to Avoid

#### Anti-Pattern: [Pattern Name]
**Problem:** [What's wrong with this pattern]

**Example of Bad Code:**
```typescript
// Don't do this
```

**Why It's Bad:**
- [Reason 1]
- [Reason 2]

**Better Approach:**
```typescript
// Do this instead
```

---

## Process Insights

### What Works

#### 1. Writing Tests Before Code Review Catches More Bugs
**What we learned:**
Requiring tests before code review (not after) catches bugs earlier and improves code quality. Developers write better code knowing tests are watching.

**Evidence:**
- Bugs found in code review decreased 40% after enforcing "tests first"
- Regression rate decreased 35%
- Code coverage improved from 65% to 82%

**Action:**
- CI blocks PR if tests don't pass
- Code review checklist includes "Are tests comprehensive?"
- Tests are reviewed as carefully as implementation code

---

#### 2. Pair Programming for Complex Problems Saves Time
**What we learned:**
When tackling complex/unfamiliar problems, pair programming actually saves time despite "doubling" the cost. Two heads are better than one for difficult problems.

**Evidence:**
- [Feature X] estimated 5 days solo, completed in 3 days paired
- Bugs in paired code: 60% fewer than solo code
- Knowledge sharing reduces bus factor

**Action:**
- Pair on complex features, unfamiliar parts of codebase, and critical bugs
- Don't pair on routine work
- Switch pairs regularly to spread knowledge

---

### What Doesn't Work

#### 1. Large Sprint Planning Meetings
**What we learned:**
Planning all work for 2-week sprint in one 3-hour meeting is exhausting and inefficient. Energy drops, quality of discussion degrades, estimates get worse.

**What we do instead:**
- Pre-planning: PM prepares user stories ahead of time
- Async: Devs review and comment before meeting
- Meeting: 1 hour to discuss questions and finalize
- Just-in-time: Detailed planning happens when dev picks up task

---

## User Insights

### User Behavior Patterns

#### 1. [Behavior Pattern]
**Observation:** [What users do]

**Why it matters:** [Impact on product]

**How we've adapted:**
- [Product change]
- [Design change]

---

#### 2. Users Ignore Onboarding Flows
**Observation:**
Only 15% of users complete our onboarding tour. Most skip and just start using the product.

**Why it matters:**
Investing heavily in upfront onboarding has low ROI. Users prefer learning by doing.

**How we've adapted:**
- Made onboarding skippable and optional
- Show contextual tips when users encounter features (just-in-time learning)
- Provide "hints" section for discovery, but don't force it
- Focus on making UI self-explanatory rather than explaining it

**Evidence:**
- After switching to contextual tips: feature adoption up 25%
- User satisfaction with onboarding improved from 3.2/5 to 4.1/5

---

#### 3. Power Users Want Keyboard Shortcuts
**Observation:**
Top 10% of users (by activity) use keyboard shortcuts extensively and request more.

**Why it matters:**
Power users are our most valuable users and advocates. Making them efficient increases engagement and NPS.

**How we've adapted:**
- Added keyboard shortcuts for all common actions
- Made shortcuts discoverable (? key shows shortcut menu)
- Let users customize shortcuts
- Added "command palette" (Cmd+K) for quick access

**Evidence:**
- Power users spend 40% more time in product after shortcuts added
- NPS from power users increased from 65 to 78

---

### Feature Adoption Insights

#### 1. Features Require 3+ Exposures Before Adoption
**What we learned:**
Users rarely adopt a feature the first time they see it. They need to encounter it 3-5 times before trying it.

**How we've adapted:**
- Show new features in multiple contexts (announcement, in-app highlight, email)
- Persist feature hints for first week after launch
- Measure "seen feature" vs "tried feature" vs "adopted feature" separately

---

## Performance Insights

### What We've Learned

#### 1. Database Indexes Matter More Than Code Optimization
**What we learned:**
90% of our performance issues were solved by proper database indexing, not by optimizing application code.

**Evidence:**
- Query that took 2.5s reduced to 50ms with single index
- Spent 2 weeks optimizing code (10% improvement)
- Spent 2 hours adding indexes (500% improvement)

**Action:**
- Profile database queries first when investigating performance
- Review query plans in code review for new features
- Monitor slow queries in production

---

#### 2. Bundle Size Impacts Bounce Rate
**What we learned:**
Every 100KB increase in bundle size increases bounce rate by ~2% on mobile.

**Evidence:**
- 500KB bundle: 12% bounce rate
- 800KB bundle: 18% bounce rate
- 300KB bundle: 8% bounce rate

**Action:**
- Set bundle size budget (400KB max)
- CI fails if bundle size increases > 10%
- Code split heavy features
- Lazy load below-the-fold content

---

## Security Insights

### What We've Learned

#### 1. Most Security Issues Are Configuration, Not Code
**What we learned:**
80% of our security vulnerabilities were misconfigurations (CORS, auth settings, env vars), not actual bugs in code.

**Action:**
- Security checklist for all new services
- Automated scanning of configs in CI
- Default-secure configuration (opt-in, not opt-out)
- Regular security audits of infrastructure

---

## Testing Insights

### What Works

#### 1. E2E Tests for Critical Paths, Unit Tests for Everything Else
**What we learned:**
Full E2E test coverage is too slow and brittle. Focus E2E on critical user paths, use fast unit/integration tests for everything else.

**Action:**
- 5-10 E2E tests for critical flows (signup, checkout, etc.)
- Unit tests for business logic
- Integration tests for API endpoints
- Visual regression tests for UI components

**Evidence:**
- E2E suite runtime: 3 min (down from 45 min when we had 100+ E2E tests)
- Test reliability: 98% (up from 70% with more E2E tests)
- Bugs caught: same or better

---

## Future Improvements

### Technical Debt to Address

| Area | Issue | Impact | Priority | Plan |
|------|-------|--------|----------|------|
| [Area] | [Technical debt] | High/Med/Low | P0/P1/P2 | [How/when to fix] |

### Process Improvements

| Current State | Problem | Proposed Improvement | Expected Benefit |
|---------------|---------|---------------------|------------------|
| [How we work now] | [What's suboptimal] | [What we should do] | [Expected outcome] |

### Product Opportunities

| Insight | Opportunity | Potential Impact | Next Steps |
|---------|-------------|------------------|------------|
| [User behavior or pattern] | [Feature idea] | [Business impact] | [How to validate] |

---

## Wisdom for Future Team Members

### If we could tell our past selves one thing...

1. **[Key Learning]**
   [Why this matters and how it would have helped]

2. **[Key Learning]**
   [Why this matters and how it would have helped]

3. **[Key Learning]**
   [Why this matters and how it would have helped]

---

### Our Principles

Based on everything we've learned, these are the principles that guide our work:

1. **[Principle]:** [Description and why we believe this]

2. **Ship small, ship often:** Frequent small releases beat big bang releases. Easier to debug, easier to rollback, faster feedback.

3. **Measure everything:** Intuition is useful but data tells the truth. Track metrics for every feature and decision.

4. **User feedback > assumptions:** What we think users want is often wrong. Talk to users, watch them use the product, measure behavior.

5. **Performance is a feature:** Fast products feel better and convert better. Budget for performance from day one.

6. **Types prevent bugs:** Type safety (TypeScript, schemas, validation) catches bugs at compile-time instead of runtime.

7. **Simple beats clever:** Code that's easy to understand is easier to maintain, debug, and extend. Optimize for readability.

---

## Related Documents

- [Decision Log](decision-log.md) - Decisions that led to insights
- [Validation Log](validation-log.md) - Real-world outcomes
- [Implementation Log](implementation-log.md) - Technical changes
- [Bug Log](bug-log.md) - Bugs that taught us lessons
