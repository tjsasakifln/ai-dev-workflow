# AI-Augmented Development Workflow

> **From PRD to Production in hours, not weeks.**

A battle-tested methodology for AI pair programming that transforms Product Requirements Documents into merged, production-ready code through deterministic automation.

[![Methodology](https://img.shields.io/badge/methodology-AI%20Pair%20Programming-blueviolet)](/)
[![PRD-to-PR](https://img.shields.io/badge/flow-PRD%20→%20Issues%20→%20PRs%20→%20Merge-green)](/)
[![Zero Manual Merge](https://img.shields.io/badge/merge-100%25%20Automated-orange)](/)

---

## 🎯 What This Is

This repository documents my **production-grade workflow** for AI-augmented software development. It's not theory—it's the exact system I use to ship features in hours instead of days.

### The Core Loop

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   PRD Document                                                          │
│        │                                                                │
│        ▼                                                                │
│   ┌─────────────────┐                                                   │
│   │  /explode-prd   │  → Breaks PRD into atomic, executable issues      │
│   └────────┬────────┘                                                   │
│            │                                                            │
│            ▼                                                            │
│   ┌─────────────────┐                                                   │
│   │ /pick-next-issue│  → Deterministic selection + implementation       │
│   └────────┬────────┘                                                   │
│            │                                                            │
│            ▼                                                            │
│   ┌─────────────────┐                                                   │
│   │   /review-pr    │  → 100% score validation + auto-merge             │
│   └────────┬────────┘                                                   │
│            │                                                            │
│            ▼                                                            │
│   Production-Ready Code                                                 │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔥 Why This Matters

| Traditional Dev | AI-Augmented (This Workflow) |
|-----------------|------------------------------|
| PRD → Sprint Planning → 2 weeks | PRD → Production → 4-8 hours |
| Manual code review bottlenecks | Automated 8-category validation |
| "It works on my machine" | 3-layer post-merge safety net |
| Subjective PR decisions | Deterministic scoring algorithm |
| Context switching kills velocity | Single-issue focus until PR |

---

## 📁 Repository Structure

```
ai-dev-workflow/
├── README.md                    # You are here
├── commands/
│   ├── pick-next-issue.md       # Issue selection + implementation
│   ├── review-pr.md             # PR validation + auto-merge
│   └── explode-prd.md           # PRD → atomic issues
├── templates/
│   ├── issue-template.md        # Atomic issue structure
│   ├── pr-template.md           # PR with all required sections
│   └── prd-template.md          # PRD structure for explosion
├── examples/
│   ├── sample-prd.md            # Real PRD example
│   ├── exploded-issues/         # Resulting issues from PRD
│   └── merged-prs/              # Successful PR examples
└── docs/
    ├── philosophy.md            # Why this approach works
    ├── adaptation-guide.md      # How to adapt for your stack
    └── metrics.md               # Measured results
```

---

## ⚡ The Three Commands

### 1. `/pick-next-issue` — Deterministic Execution

Selects the highest-priority issue using a scoring algorithm, then implements it to PR creation.

**Selection Algorithm:**
```
Score = Priority_Weight + Age_Weight + Size_Weight + Label_Weight

Priority: P0(BLOCKER) > P1(HIGH) > P2(MEDIUM) > P3(LOW)
Age:      >72h (+4) | >48h (+2) | >24h (+1) | <24h (0)
Size:     <100 LOC (+3) | <200 (+2) | <400 (+1) | >400 (-2)
Labels:   security/deploy (+5) | test/docs (+2)
```

**Atomicity Validation:**
- ✅ 1-8 hours estimated effort
- ✅ Single responsibility
- ✅ No blocking dependencies
- ✅ Testable in isolation
- ✅ Complete specification

**If not atomic → Auto-split into sub-issues**

[📄 Full Command Spec →](commands/pick-next-issue.md)

---

### 2. `/review-pr` — Zero-Tolerance Validation

Only PRs achieving **100% score** across 8 categories are merged. No exceptions.

**8 Categories (12.5% each):**

| Category | Key Criteria |
|----------|--------------|
| **Code Quality** | 0 lint errors, 0 type errors, 100% Prettier |
| **Testing** | ≥70% coverage backend, ≥60% frontend, 100% passing |
| **Security** | 0 HIGH/CRITICAL vulns, 0 hardcoded secrets |
| **Documentation** | 100% public functions documented |
| **Architecture** | Cyclomatic complexity ≤10, <5% duplication |
| **Git Standards** | Semantic commits, linked issue, no conflicts |
| **Review Standards** | ≤400 LOC, single responsibility |
| **Operational** | Health checks, error handling, rollback plan |

**Post-Merge Safety Net (3 Layers):**
1. **Health Checks** (1-2 min): Build + unit tests
2. **Smoke Tests** (3-5 min): Critical user paths
3. **Full CI Pipeline** (5-10 min): Complete validation

**Any failure → Automatic rollback + PR reopened**

[📄 Full Command Spec →](commands/review-pr.md)

---

### 3. `/explode-prd` — Structured Decomposition

Transforms a PRD document into atomic, executable GitHub issues.

**Input:** Product Requirements Document with:
- Problem statement
- Success metrics
- Feature specifications
- Technical constraints

**Output:** 10-30 atomic issues with:
- Clear acceptance criteria (3-7 per issue)
- File locations specified
- Dependencies mapped
- Effort estimated (1-8h each)
- Priority assigned (P0-P3)
- Milestone tagged

[📄 Full Command Spec →](commands/explode-prd.md)

---

## 📊 Measured Results

From real production use on [ETP Express](https://github.com/CONFENGE/etp-express) (680+ commits):

| Metric | Before | After | Δ |
|--------|--------|-------|---|
| PRD → First PR | 3-5 days | 2-4 hours | **-95%** |
| PR Review Time | 1-2 days | 5-10 min | **-99%** |
| Merge Failures | ~15% | <2% | **-87%** |
| Context Switches/Day | 8-12 | 1-2 | **-85%** |
| Issues Reopened | ~20% | <5% | **-75%** |

---

## 🛠️ Stack Compatibility

This workflow is **stack-agnostic** but optimized for:

**Currently validated:**
- **Backend:** NestJS, Node.js, TypeScript
- **Frontend:** React, Next.js, Vite
- **Database:** PostgreSQL, TypeORM
- **CI/CD:** GitHub Actions
- **AI:** Claude (Anthropic), Claude Code CLI

**Adaptable to:**
- Python (Django, FastAPI)
- Go, Rust
- Any Git-based workflow
- GitLab, Bitbucket (with CLI adjustments)

---

## 🚀 Getting Started

### Prerequisites

```bash
# GitHub CLI (required)
brew install gh
gh auth login

# Your preferred AI assistant configured
# (Claude API, Claude Code, or similar)
```

### Quick Start

1. **Clone this repo:**
```bash
git clone https://github.com/tjsasakifln/ai-dev-workflow.git
```

2. **Copy commands to your project:**
```bash
cp -r ai-dev-workflow/commands your-project/.claude/
```

3. **Start with a PRD:**
```bash
# In your AI assistant
> /explode-prd docs/my-feature-prd.md
```

4. **Execute the loop:**
```bash
> /pick-next-issue  # Implements highest priority issue
> /review-pr        # Validates and merges
> /pick-next-issue  # Next iteration
```

---

## 🧠 Philosophy

### Why Deterministic Selection?

Human bias in issue selection causes:
- Developers cherry-picking "interesting" work
- High-priority bugs ignored for new features
- Paralysis when backlog grows

**Solution:** Algorithm selects. Human executes. No negotiation.

### Why 100% Score Requirement?

"Good enough" compounds into technical debt:
- 95% coverage → blind spots grow
- "Minor" lint warnings → code quality decay
- Skipped docs → onboarding friction

**Solution:** Binary pass/fail. No exceptions. No "just this once."

### Why Atomic Issues?

Large issues cause:
- Context overload
- Partial implementations
- Untestable PRs
- Merge conflicts

**Solution:** If >8 hours → split first. Always.

---

## 🤝 Hiring / Consulting

I use this workflow professionally for:

- **AI-Augmented Development Sprints** — PRD to production in days
- **Workflow Implementation** — Set up this system for your team
- **Technical Consulting** — GovTech, SaaS, automation

**Contact:**
- 📧 tiago.sasaki@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/tiagosasaki)
- 🐙 [GitHub](https://github.com/tjsasakifln)

---

## 📜 License

MIT — Use freely, attribute appreciated.

---

## ⭐ Star History

If this workflow helps you ship faster, consider starring the repo.

```
Your star = mass validation for unconventional approaches
```

---

<p align="center">
  <strong>Stop reviewing PRs manually. Start shipping.</strong>
</p>
