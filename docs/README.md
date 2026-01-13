# Documentation System for LLM-Assisted Development

> The only documentation setup you need for building software with AI.

This is a comprehensive documentation system designed for teams (human + AI) building software products. It captures not just what you're building, but why, how, and what you learned along the way.

## Why This Exists

Most teams have one of two problems:

1. **No documentation** - Everything is in people's heads. LLMs have no context. New team members are lost. Past decisions are forgotten.

2. **Wrong documentation** - Tons of docs that are out-of-date, scattered across tools, or focused on the wrong things.

This system solves both by providing:
- **Structure** - Clear organization of all project knowledge
- **Memory** - Logs that capture what happened and why
- **Context** - Everything an LLM needs to help you effectively
- **Learning** - Insights that compound over time

## What's Different About This System

**Traditional docs** tell you what exists.

**This system** tells you:
- WHY things exist (vision, decisions)
- WHAT you're building (product, features)
- HOW you built it (implementation, design)
- WHAT HAPPENED when you shipped (validation, bugs, insights)
- HOW TO WORK (process, workflows)

**It's designed for:**
- ✅ Human-LLM collaboration
- ✅ Fast-moving teams
- ✅ Learning from reality
- ✅ Capturing institutional knowledge

**It avoids:**
- ❌ Over-documentation
- ❌ Docs that go stale
- ❌ Unclear ownership
- ❌ Wasted effort

## Quick Start

### 1. Copy This Template

```bash
# Copy the /docs folder to your project
cp -r docs /path/to/your/project/

# Or clone this repo and copy what you need
git clone [repo-url]
```

### 2. Start with Context

Fill out these three files first:

1. **`docs/00-context/vision.md`**
   - Why does your product exist?
   - What are you building?
   - What are your core principles?

2. **`docs/00-context/system-map.md`**
   - What's actually running right now?
   - How is it deployed?
   - What's the tech stack?

3. **`docs/01-product/prd.md`**
   - What are you building next?
   - What are the requirements?
   - How will you measure success?

### 3. Work on a Feature

When building a feature, create a folder in `docs/02-features/`:

```bash
mkdir docs/02-features/your-feature-name
cp -r docs/02-features/feature-template/* docs/02-features/your-feature-name/
```

Fill out:
1. **`feature-spec.md`** - What you're building and why
2. **`tech-design.md`** - How you'll build it
3. **`dev-tasks.md`** - Breakdown of implementation tasks
4. **`test-plan.md`** - How you'll validate it works

### 4. Ship and Learn

After shipping:

1. Update **`docs/03-logs/implementation-log.md`** - What you built
2. Update **`docs/03-logs/validation-log.md`** - What actually happened
3. Update **`docs/03-logs/insights.md`** - What you learned

As bugs come up, track them in **`docs/03-logs/bug-log.md`**.

For big decisions, document them in **`docs/03-logs/decision-log.md`**.

## Folder Structure

```
/docs
├── 00-context/              # WHY and WHAT EXISTS RIGHT NOW
│   ├── vision.md            # Product purpose & boundaries (anchor)
│   ├── assumptions.md       # Assumptions, risks, unknowns
│   └── system-map.md        # What is actually built & running
│
├── 01-product/              # WHAT the product must do
│   └── prd.md               # Single source of truth for requirements
│
├── 02-features/             # HOW features are designed & built
│   └── feature-<name>/
│       ├── feature-spec.md  # User intent & acceptance criteria
│       ├── tech-design.md   # Architecture & implementation approach
│       ├── dev-tasks.md     # LLM-executable tasks
│       └── test-plan.md     # Validation strategy
│
├── 03-logs/                 # MEMORY (this is what most teams miss)
│   ├── implementation-log.md # What changed in code & why
│   ├── decision-log.md       # Architectural & product decisions
│   ├── bug-log.md            # Bugs, fixes, regressions
│   ├── validation-log.md     # What happened after shipping
│   └── insights.md           # Learnings & future improvements
│
├── 04-process/              # HOW to work with this system
│   ├── dev-workflow.md       # Daily dev loop (human + LLM)
│   ├── definition-of-done.md # When docs/code are "done"
│   └── llm-prompts.md        # Canonical prompts per doc type
│
└── README.md                 # How to use this repo (this file)
```

## How to Use This System

### For Planning
1. Define vision → assumptions → requirements
2. Break into features with specs and designs
3. Create task breakdowns for implementation

### For Building
1. Give LLMs context from feature specs and tech designs
2. Use prompts from `llm-prompts.md`
3. Follow workflow in `dev-workflow.md`
4. Update logs as you go

### For Shipping
1. Validate against acceptance criteria
2. Follow definition of done
3. Log what you built and why
4. Measure what actually happened

### For Learning
1. Compare expected vs actual outcomes
2. Document bugs and how you fixed them
3. Extract insights and patterns
4. Update processes based on learnings

## Philosophy

### 1. Documentation is Memory

Most teams forget why they built things the way they did. This system captures:
- **Context** - Why decisions were made
- **Reality** - What actually happened
- **Learning** - What worked and what didn't

### 2. Logs Over Perfect Docs

Perfect documentation goes stale. **Logs are eternal** because they're chronological records of what happened.

We focus on:
- Implementation log (what changed)
- Decision log (what we decided)
- Bug log (what broke)
- Validation log (what happened)
- Insights (what we learned)

### 3. Just-in-Time Documentation

Don't document everything upfront. Document:
- **Before:** Vision, requirements, design
- **During:** Tasks, decisions, implementation
- **After:** Validation, bugs, insights

### 4. AI-Native Structure

This structure works great with LLMs because:
- Clear templates they can fill out
- Explicit context for every feature
- Chronological logs they can search
- Canonical prompts that work

### 5. Single Source of Truth

Each type of information has ONE place:
- Requirements → PRD
- Design → Tech design
- Tasks → Dev tasks
- Reality → Validation log
- Learnings → Insights

No duplication, no confusion.

## What to Document (and What Not To)

### ✅ Always Document

**Context:**
- Vision and principles
- Current system state
- Requirements and specs

**Decisions:**
- Why you chose approach A over B
- Trade-offs you considered
- Success criteria

**Reality:**
- What you actually built
- What actually happened after shipping
- Bugs and how you fixed them

**Learning:**
- What worked and what didn't
- Patterns you discovered
- Insights for next time

### ❌ Don't Document

**Auto-Generated:**
- API docs (generate from code)
- Type definitions (use TypeScript)
- Test coverage (generate with tools)

**Obvious:**
- How to run `npm install`
- What a common framework does
- Self-explanatory code

**Speculative:**
- Features you might build someday
- Architectures you might need later
- Hypothetical scaling plans

## For LLM Assistants

When working with LLMs on this project, provide them:

**Planning a feature:**
- Vision doc (why we build)
- System map (what exists)
- PRD (what's required)

**Implementing a feature:**
- Feature spec (what to build)
- Tech design (how to build)
- Dev tasks (specific work)
- Existing code patterns

**Debugging:**
- Bug log (similar issues)
- Implementation log (recent changes)
- System map (how things connect)

**Learning:**
- Validation log (what happened)
- Insights (patterns we've seen)
- Decision log (past choices)

Use the prompts in `docs/04-process/llm-prompts.md` for best results.

## Maintenance

### Daily
- Update implementation log when shipping code
- Log decisions as you make them
- Track bugs in bug log

### Weekly
- Review validation metrics
- Update insights with learnings
- Triage and update bug log

### Monthly
- Review and update vision/PRD if needed
- Archive completed features
- Update system map with changes
- Review decision log (any to revisit?)

### As Needed
- Create feature specs when planning features
- Update assumptions when learning new info
- Extract insights after major launches
- Refine process docs based on what works

## Getting Value Immediately

You don't need to fill everything out at once. Start small:

**Week 1:** Just create the vision doc. It'll clarify your thinking.

**Week 2:** Map your current system. You'll find gaps you didn't know existed.

**Week 3:** Write a PRD for your next feature. It'll save hours of confusion.

**Week 4:** Log what you built and why. Future you will be grateful.

**Week 5+:** Start tracking outcomes, bugs, and insights. This is where the magic happens.

## Who This Is For

- **Solo developers** who want to work effectively with LLMs
- **Small teams** who need structure without bureaucracy
- **Startups** moving fast but want to capture learnings
- **Anyone** building with AI assistants

## Who This Is NOT For

- Teams that need heavy compliance/audit trails
- Projects with hundreds of developers
- Organizations with dedicated tech writers
- Slow-moving, waterfall-style projects

## Common Questions

**Q: Isn't this too much documentation?**

A: Most of it is templates you fill out as you work, not extra work. The logs capture what you'd write in commit messages or Slack anyway. The structure just makes it useful long-term.

**Q: What if I don't have time?**

A: Start with just vision.md and system-map.md. Add more as you see value. Even minimal usage is better than nothing.

**Q: Do I need to fill out every template?**

A: No. Use what's helpful. Small bug fix? Just update bug log. Big feature? Use all the feature templates. Adapt to your needs.

**Q: How is this different from a wiki?**

A: Structure. Everything has a place. Logs are chronological (never go stale). Designed for LLM consumption, not just humans.

**Q: Can I customize this?**

A: Absolutely. This is a starting point. Add sections, remove what you don't need, adapt to your workflow.

## Examples

### Example: Shipping a Feature

1. **Plan** (1-2 hours)
   - Fill out feature-spec.md
   - Fill out tech-design.md
   - Break down dev-tasks.md

2. **Build** (days/weeks)
   - Work through tasks
   - Log decisions in decision-log.md
   - Update implementation-log.md as you go

3. **Ship** (1 hour)
   - Deploy following dev-workflow.md
   - Update system-map.md if architecture changed

4. **Validate** (ongoing)
   - Track metrics
   - Update validation-log.md after 1 week
   - Extract insights for insights.md

### Example: Fixing a Bug

1. **Document** the bug in bug-log.md
2. **Fix** the bug
3. **Test** to prevent regression
4. **Update** implementation-log.md with what changed
5. **Update** bug-log.md with root cause and prevention

### Example: Making a Decision

1. **Document** options in decision-log.md
2. **Discuss** with team/stakeholders
3. **Decide** and update decision-log.md with rationale
4. **Implement** the decision
5. **Review** outcome later and update decision log

## Contributing

This is a template, not a product. Fork it, customize it, make it yours.

If you find improvements that would help others:
- Share your customizations
- Suggest template improvements
- Document patterns you've discovered

## License

[Choose your license - MIT suggested for max sharing]

---

**The best documentation is the documentation you actually maintain.**

This system is designed to be so useful you'll want to keep it updated. Start small, add as you go, and let it grow with your project.

**Questions? Issues? Improvements?**

[Link to GitHub issues or discussion forum]
