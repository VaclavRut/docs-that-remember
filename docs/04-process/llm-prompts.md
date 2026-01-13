# LLM Prompts

> **Canonical prompts per doc type**
>
> Reusable prompts for working with LLMs to create and maintain documentation, write code, and ship features. Copy, customize, and use these to get consistent, high-quality output from AI assistants.

---

## Purpose

This document provides:
- **Proven prompts** that work well with LLMs
- **Templates** for common tasks
- **Best practices** for prompting
- **Context** to include for better results

---

## General Prompting Best Practices

### 1. Be Specific
- ❌ "Write a function"
- ✅ "Write a TypeScript function that validates email addresses using regex and returns a boolean"

### 2. Provide Context
```
I'm working on [project description].
We use [tech stack].
I need to [specific task].
The code should follow [pattern/style].
```

### 3. Define Success Criteria
```
The solution should:
- [Requirement 1]
- [Requirement 2]
- Not use [anti-pattern]
```

### 4. Iterate
- Start with a plan
- Review and refine
- Implement in pieces
- Test and adjust

### 5. Reference Examples
```
Follow the same pattern as [file:line] in the codebase.
```

---

## Planning Prompts

### Creating a Feature Spec

```
I need to create a feature specification for [feature name].

Context:
- Target users: [who this is for]
- Problem it solves: [pain point]
- Success criteria: [how we measure success]

Please help me create a feature spec following the template in
docs/02-features/feature-template/feature-spec.md.

Focus on:
1. User intent and value proposition
2. Clear acceptance criteria
3. Edge cases to consider
4. How we'll validate success

Ask me questions if anything is unclear.
```

### Creating a Technical Design

```
I need to create a technical design for [feature name].

Feature spec: [link or paste spec]

Current architecture:
- We use [tech stack]
- Existing patterns: [describe or link to examples]
- Constraints: [performance, security, etc.]

Please help me design the implementation following the template
in docs/02-features/feature-template/tech-design.md.

Include:
1. Component/module architecture
2. Data model changes
3. API design (if applicable)
4. Integration points
5. Performance and security considerations

Suggest the approach but ask me to validate key decisions.
```

### Breaking Down Tasks

```
I need to break down this feature into implementation tasks.

Feature spec: [link or paste]
Tech design: [link or paste]

Please create a task list following the template in
docs/02-features/feature-template/dev-tasks.md.

Each task should:
- Be atomic and completable in < 4 hours
- Have clear acceptance criteria
- Specify files that will change
- Note dependencies on other tasks
- Include test requirements

Organize by: setup, backend, frontend, integration, testing, deployment.
```

---

## Implementation Prompts

### Starting a New Feature

```
I'm implementing [feature name].

Feature spec: [link]
Tech design: [link]
Dev tasks: [link]

I'm starting with task: [specific task]

Please:
1. Review the relevant existing code in [area of codebase]
2. Identify the pattern I should follow
3. Show me the plan for implementing this task
4. Ask if the approach looks good before writing code

After approval, write the code following our patterns.
```

### Writing a Component

```
I need to create a [React/Vue/etc] component for [purpose].

Requirements:
- Props: [list props and types]
- State: [what state it manages]
- Behavior: [what it does]
- Styling: [style approach]

Follow the pattern used in [existing similar component].
Use TypeScript with strict types.

Please:
1. Show me the component structure
2. Write the implementation
3. Write unit tests
4. Ensure it's accessible (ARIA labels, keyboard nav)
```

### Writing an API Endpoint

```
I need to create a new API endpoint.

Endpoint: [METHOD] /api/[path]
Purpose: [what it does]
Auth required: [yes/no, what level]

Request body:
{
  [field]: [type]
}

Response:
{
  [field]: [type]
}

Error cases:
- [400]: [when]
- [401]: [when]
- [500]: [when]

Follow the pattern in [existing endpoint file:line].
Use [framework] and [validation library].

Please:
1. Write the route handler
2. Add request validation
3. Add error handling
4. Write integration tests
```

### Refactoring Code

```
This code needs refactoring: [paste code or file:line]

Issues:
- [Problem 1]
- [Problem 2]

Goals:
- Make it more readable
- Reduce complexity
- Maintain exact same functionality

Please:
1. Explain what's hard to understand
2. Propose a refactored version
3. Ensure behavior is identical
4. Make sure existing tests still pass
```

### Fixing a Bug

```
I have a bug to fix.

Symptoms:
- [What user sees]
- Steps to reproduce: [steps]

Expected: [what should happen]
Actual: [what actually happens]

Relevant code: [file:line or paste code]

Please:
1. Help me identify the root cause
2. Suggest a fix
3. Write a test that catches this bug
4. Explain how to prevent similar bugs
```

---

## Testing Prompts

### Writing Unit Tests

```
I need unit tests for this code: [paste code or file:line]

Please write tests that:
- Test the happy path
- Test edge cases: [list specific cases]
- Test error handling
- Use [test framework]
- Follow the pattern in [existing test file]

Aim for >80% code coverage.
```

### Writing Integration Tests

```
I need integration tests for API endpoint: [METHOD] /api/[path]

Test cases:
- Happy path: [scenario]
- Error cases: [list]
- Edge cases: [list]

Use [test framework].
Mock [external services].
Follow pattern in [existing integration test].

Include:
- Request setup
- Expected responses
- Status codes
- Error messages
```

### Writing E2E Tests

```
I need an E2E test for this user flow:
1. [Step 1]
2. [Step 2]
3. [Expected outcome]

Use [Playwright/Cypress/etc].
Test in [browser].

Include:
- Setup/teardown (test data)
- Page object pattern (if we use it)
- Assertions for each step
- Error screenshots on failure

Follow pattern in [existing E2E test].
```

---

## Documentation Prompts

### Updating System Map

```
I've made changes to the system architecture.

Changes:
- [What changed]
- New components: [list]
- New integrations: [list]
- New data flows: [describe]

Please update docs/00-context/system-map.md to reflect:
1. New components in architecture diagram
2. Updated data flows
3. New dependencies
4. Configuration changes

Keep the existing format and style.
```

### Writing API Documentation

```
I've created a new API endpoint. Generate documentation for it.

Endpoint details:
- Path: [METHOD] /api/[path]
- Purpose: [description]
- Auth: [required level]
- Request: [schema]
- Response: [schema]
- Errors: [list]

Format as:
- OpenAPI/Swagger spec (if we use that)
- Markdown (if we use that)

Follow the pattern in [existing API docs].

Include:
- Clear descriptions
- Request/response examples
- Error code explanations
- Authentication requirements
```

### Creating a User Guide

```
I've shipped [feature name]. Create a user guide for it.

Feature description: [what it does]
Target users: [who will use it]

The guide should:
- Explain what the feature does (benefits)
- Show how to use it (step-by-step)
- Include screenshots [I'll provide these]
- Cover common issues/FAQs
- Be written for non-technical users

Format: Markdown
Tone: Friendly and clear
Length: Keep it concise (< 500 words)
```

### Updating Implementation Log

```
I've just completed [feature/bug fix].

Changes made:
- Files changed: [list]
- What changed: [description]
- Why: [reasoning]

Please create an implementation log entry following the template
in docs/03-logs/implementation-log.md.

Include:
- Technical details of what changed
- Why we made this change
- Alternatives considered (if applicable)
- Impact (breaking changes, performance, dependencies)
- Testing done
- Notes/gotchas for future developers
```

---

## Review Prompts

### Code Review

```
Please review this code: [paste code or link to PR]

Check for:
- Correctness (does it do what it should?)
- Tests (are edge cases covered?)
- Readability (is it clear?)
- Performance (any obvious issues?)
- Security (any vulnerabilities?)
- Patterns (does it follow our conventions?)

Be specific about issues and suggest improvements.
Reference our style guide: [link if available]
```

### Documentation Review

```
Please review this documentation: [paste or link]

Check for:
- Accuracy (is it correct?)
- Completeness (anything missing?)
- Clarity (is it understandable?)
- Examples (are they helpful and correct?)
- Links (do they work?)

Suggest improvements for:
- Readability
- Organization
- Helpful additions
```

---

## Validation Prompts

### Creating Validation Log Entry

```
We shipped [feature name] [date].

Please help me create a validation log entry in
docs/03-logs/validation-log.md.

Data I have:
- Expected metrics: [from feature spec]
- Actual metrics: [data]
- User feedback: [quotes/themes]
- Bugs found: [list]
- Usage stats: [data]

Please create an entry that:
1. Compares expected vs actual outcomes
2. Analyzes what went well and what didn't
3. Identifies surprises (positive and negative)
4. Suggests next steps based on learnings
5. Rates overall success
```

### Extracting Insights

```
I want to update our insights document with learnings from
[feature/bug/incident].

Context: [describe what happened]
Outcome: [what resulted]
Data: [metrics, feedback, etc.]

Please help me:
1. Identify the key insight/learning
2. Extract actionable principles
3. Suggest how to prevent/repeat this
4. Format it for docs/03-logs/insights.md

Focus on generalizable lessons, not just this specific case.
```

---

## Debugging Prompts

### Understanding Complex Code

```
I need to understand this code: [paste code or file:line]

Please:
1. Explain what it does (in plain English)
2. Walk through the logic step by step
3. Identify any gotchas or edge cases
4. Explain why it might be written this way
5. Suggest how it could be clearer (if applicable)
```

### Finding Root Cause

```
I'm debugging an issue.

Symptoms: [what's wrong]
Code: [relevant code]
Logs: [relevant logs]
What I've tried: [debugging steps so far]

Please:
1. Analyze the symptoms and code
2. Form hypotheses about root cause
3. Suggest debugging steps to narrow it down
4. Identify the most likely cause
5. Suggest a fix
```

### Performance Investigation

```
I have a performance issue.

Slow operation: [what's slow]
Current performance: [metrics]
Expected performance: [target]
Relevant code: [paste or file:line]

Please:
1. Identify potential bottlenecks
2. Suggest profiling approach
3. Recommend optimizations
4. Estimate impact of each optimization
```

---

## Prompt Templates by Document Type

### For Vision Doc (docs/00-context/vision.md)

```
Help me create/update the vision document for [product name].

Context:
- Problem we're solving: [description]
- Target users: [who]
- Current state: [what exists now]
- Future vision: [where we want to be]

Follow the template in docs/00-context/vision.md.

Focus on:
- WHY this product exists
- WHAT the boundaries are
- Anchor points (unchanging principles)

Ask me questions to fill in gaps.
```

### For PRD (docs/01-product/prd.md)

```
Help me create a PRD for [feature/product].

Context:
- User problem: [pain point]
- Target users: [who]
- Business goals: [objectives]
- Constraints: [limitations]

Follow the template in docs/01-product/prd.md.

Include:
- Clear problem statement
- User stories
- Requirements (must/should/nice-to-have)
- Success metrics
- Scope (in/out)

Ask clarifying questions as needed.
```

### For Decision Log (docs/03-logs/decision-log.md)

```
Help me document a decision we made.

Decision: [what we decided]
Context: [why we needed to decide]
Options considered: [list options]
Choice: [what we chose]
Rationale: [why]

Follow the template in docs/03-logs/decision-log.md.

Create an entry that:
- Clearly states the problem
- Lists all options with pros/cons
- Explains our reasoning
- Sets success criteria
- Defines review date
```

---

## Context to Always Provide

When prompting LLMs about code, include:

### Project Context
```
Project: [name and description]
Tech stack: [list]
Patterns we use: [conventions]
Documentation: [link to relevant docs]
```

### Code Context
```
Relevant files:
- [file:line] - [what it does]
- [file:line] - [what it does]

Existing patterns:
- [pattern] in [file]
```

### Quality Context
```
Requirements:
- Code style: [style guide]
- Testing: [coverage target, frameworks]
- Performance: [targets]
- Security: [requirements]
```

---

## Related Documents

- [Dev Workflow](dev-workflow.md) - When to use these prompts
- [Feature Templates](../02-features/feature-template/) - Templates referenced in prompts
- [Definition of Done](definition-of-done.md) - Quality standards
