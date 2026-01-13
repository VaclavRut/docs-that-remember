# Docs That Remember 🧠

> A documentation system that captures what you built, why you built it, and what you learned. Designed for human-LLM collaboration.

## The Problem

Most development teams have one of two problems:

1. **No documentation** - Everything lives in people's heads. LLMs have no context. New team members are lost.
2. **Stale documentation** - Tons of outdated docs scattered across tools that nobody maintains.

## The Solution

**Docs That Remember** is different. It's a documentation system that captures:

- **WHY** things exist (vision, decisions)
- **WHAT** you're building (product specs, features)
- **HOW** you built it (implementation, design)
- **WHAT HAPPENED** when you shipped (validation, bugs)
- **WHAT YOU LEARNED** (insights that compound over time)

It's the **MEMORY** that most teams miss.

## Structure

```
/docs
├── 00-context/              # WHY & WHAT EXISTS NOW
│   ├── vision.md            # Product purpose & principles
│   ├── assumptions.md       # Risks & unknowns
│   └── system-map.md        # Current system state
│
├── 01-product/              # WHAT TO BUILD
│   └── prd.md               # Product requirements
│
├── 02-features/             # HOW TO BUILD IT
│   └── feature-<name>/
│       ├── feature-spec.md  # User intent & acceptance
│       ├── tech-design.md   # Architecture & approach
│       ├── dev-tasks.md     # Implementation tasks
│       └── test-plan.md     # Testing strategy
│
├── 03-logs/                 # MEMORY (the magic)
│   ├── implementation-log.md # Code changes & why
│   ├── decision-log.md       # Key decisions
│   ├── bug-log.md            # Bugs & fixes
│   ├── validation-log.md     # Post-ship reality
│   └── insights.md           # Learnings
│
└── 04-process/              # HOW TO WORK
    ├── dev-workflow.md       # Daily workflow
    ├── definition-of-done.md # Quality standards
    └── llm-prompts.md        # Prompts for AI
```

See **[docs/README.md](docs/README.md)** for complete documentation.

## What Makes This Different

### 1. Logs Over Perfect Docs
Chronological logs never go stale. We capture reality as it happens, not aspirational documentation that becomes outdated.

### 2. Built for AI Collaboration
Clear structure and templates that LLMs can understand and fill out. Every feature has the context an AI needs to help you effectively.

### 3. Learning Built-In
Track what you expected vs what actually happened. Extract insights. Get smarter with every feature you ship.

### 4. Just-in-Time Documentation
Don't document everything upfront. Document before (specs), during (decisions), and after (outcomes). Only what matters, when it matters.

## Quick Start

### 1. Copy the Template

```bash
# Clone this repo
git clone https://github.com/VaclavRut/docs-that-remember.git

# Copy the docs folder to your project
cp -r docs-that-remember/docs /path/to/your/project/
```

### 2. Fill Out Your Context (30 minutes)

Start with these three files:

1. **`docs/00-context/vision.md`** - Why your product exists
2. **`docs/00-context/system-map.md`** - What's running right now
3. **`docs/01-product/prd.md`** - What you're building

### 3. Build Your First Feature

Create a feature folder:

```bash
mkdir docs/02-features/your-feature-name
cp -r docs/02-features/feature-template/* docs/02-features/your-feature-name/
```

Fill out:
- `feature-spec.md` - What and why
- `tech-design.md` - How you'll build it
- `dev-tasks.md` - Task breakdown
- `test-plan.md` - How you'll validate it

### 4. Ship and Learn

After shipping, update:
- `docs/03-logs/implementation-log.md` - What you built
- `docs/03-logs/validation-log.md` - What actually happened
- `docs/03-logs/insights.md` - What you learned

## Philosophy

### Documentation is Memory

Most teams forget why they made decisions. This system captures the **context**, **reality**, and **learning** at every step.

### Logs Are Eternal

Perfect docs go stale. Chronological logs of what happened are forever useful.

### AI-Native Structure

Templates LLMs can fill out. Context for every feature. Prompts that work. Built for human-AI collaboration from day one.

### Single Source of Truth

Every type of information has ONE place. No duplication, no confusion.

## Who This Is For

- **Solo developers** working with AI assistants
- **Small teams** who need structure without bureaucracy
- **Startups** moving fast but wanting to capture learnings
- **Anyone** building with LLMs

## Examples

### Shipping a Feature
1. **Plan** - Fill out feature spec, tech design, tasks (1-2 hours)
2. **Build** - Work through tasks, log decisions (days/weeks)
3. **Ship** - Deploy, update system map (1 hour)
4. **Validate** - Track metrics, update logs (ongoing)

### Fixing a Bug
1. Document in bug log
2. Fix and test
3. Update implementation log
4. Update bug log with root cause

### Making a Decision
1. Document options in decision log
2. Choose and explain rationale
3. Implement
4. Review outcome later

## Get Started in 5 Minutes

Don't overthink it. Start small:

**Day 1:** Create vision.md - Clarify your thinking

**Day 2:** Map your current system - Find gaps

**Day 3:** Write a PRD for next feature - Save hours of confusion

**Day 4:** Log what you built - Future you will thank you

**Day 5+:** Track outcomes and extract insights - This is where magic happens

## What People Are Saying

> "Finally, documentation that doesn't feel like busywork. The logs are gold." - [Your testimonial here]

> "My AI assistant is 10x more helpful with this context." - [Your testimonial here]

## Contributing

This is a template meant to be customized. Fork it, make it yours, share improvements.

Found something that works well? Open an issue or PR to help others.

## License

MIT License - Use freely, modify as needed, share improvements.

---

**Stop forgetting why you built what you built.**

Start using Docs That Remember today.

[⭐ Star this repo](https://github.com/VaclavRut/docs-that-remember) | [📖 Full Documentation](docs/README.md) | [🐛 Issues](https://github.com/VaclavRut/docs-that-remember/issues)
