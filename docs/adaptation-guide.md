# Adaptation Guide

How to adapt this workflow for your stack, team, and project.

---

## Stack Adaptations

### Python (Django/FastAPI)

**Issue template changes:**
```markdown
**Arquivo(s):**
- `app/models/user.py` — Add User model
- `app/services/auth.py` — Implement auth service
- `tests/test_auth.py` — Unit tests
```

**Testing commands:**
```bash
pytest --cov=app --cov-report=html
pytest tests/e2e/
```

**Linting:**
```bash
black . --check
flake8 app/
mypy app/
```

### Go

**Testing commands:**
```bash
go test ./... -cover
go test ./... -race
```

**Linting:**
```bash
golangci-lint run
```

### Rust

**Testing commands:**
```bash
cargo test
cargo clippy -- -D warnings
```

---

## CI/CD Platform Adaptations

### GitLab CI

Replace GitHub CLI commands:

```bash
# GitHub
gh issue list --state open
gh pr create --title "..."
gh pr merge --merge

# GitLab
glab issue list --opened
glab mr create --title "..."
glab mr merge
```

### Bitbucket

Use Bitbucket CLI or API:

```bash
# List PRs
curl -u user:token https://api.bitbucket.org/2.0/repositories/{workspace}/{repo}/pullrequests

# Create PR
curl -X POST -u user:token \
  https://api.bitbucket.org/2.0/repositories/{workspace}/{repo}/pullrequests \
  -H "Content-Type: application/json" \
  -d '{"title": "...", "source": {"branch": {"name": "..."}}, "destination": {"branch": {"name": "main"}}}'
```

---

## Team Size Adaptations

### Solo Developer

Full automation is ideal:
- `/pick-next-issue` → implement → `/review-pr` → merge
- No human review bottleneck
- Maximum velocity

**Recommended settings:**
- Coverage threshold: 70%+
- PR size limit: 400 lines
- Auto-merge on 100% score

### Small Team (2-5)

Add light human review:
- `/review-pr` validates automatically
- Human approves before merge
- Share `/pick-next-issue` ownership by domain

**Recommended settings:**
- Coverage threshold: 80%+
- PR size limit: 300 lines
- Require 1 human approval + 100% score

### Larger Team (5+)

Domain ownership becomes critical:
- Split issues by domain expert
- Parallel `/pick-next-issue` by domain
- Rotate review duties

**Recommended settings:**
- Coverage threshold: 85%+
- PR size limit: 200 lines
- Require 2 human approvals + 100% score
- Add CODEOWNERS file

---

## Quality Gate Adjustments

### Startup / MVP Phase

Prioritize speed over perfection:

```markdown
# Relaxed thresholds (temporary)
- Coverage: ≥50% backend, ≥40% frontend
- PR size: ≤600 lines
- Documentation: Critical paths only
- Architecture: Complexity ≤15
```

**Important:** Set a date to tighten these. Technical debt compounds.

### Enterprise / Regulated

Maximum strictness:

```markdown
# Enterprise thresholds
- Coverage: ≥90% backend, ≥80% frontend
- PR size: ≤200 lines
- Documentation: 100% all functions
- Security: 0 vulnerabilities (including MEDIUM)
- Audit: All changes logged
- Compliance: SOC2/HIPAA checks
```

---

## AI Assistant Adaptations

### Claude (Anthropic)

This workflow is optimized for Claude. Use as documented.

**Tips:**
- Use Claude Code CLI for terminal integration
- Provide full context in system prompt
- Include command files in project memory

### GPT-4 (OpenAI)

Minor adaptations needed:

**Context management:**
- GPT-4 has shorter context window
- Split long commands into separate prompts
- Use Custom Instructions for persistent context

**Prompt style:**
- More explicit step numbering
- Add "Do not skip steps" reminders
- Break complex commands into phases

### Local Models (Llama, Mistral)

Significant adaptations:

**Simplify commands:**
- Remove nested logic
- Explicit intermediate outputs
- More guardrails for format

**Lower expectations:**
- May need multiple iterations
- Human verification more important
- Best for simple, repetitive tasks

---

## Project Type Adaptations

### API-Only Backend

Remove frontend-specific checks:

```markdown
# /review-pr adjustments
- Frontend coverage: N/A
- UI tests: N/A
- Accessibility: N/A

# Add API-specific
- OpenAPI spec updated: Required
- Contract tests: Required
- Rate limiting documented: Required
```

### Frontend-Only (SPA)

Remove backend-specific checks:

```markdown
# /review-pr adjustments
- Backend coverage: N/A
- DB migrations: N/A
- API security: N/A

# Add frontend-specific
- Lighthouse score: ≥90
- Bundle size: No increase >5%
- Accessibility: WCAG 2.1 AA
```

### Monorepo

Domain-specific adaptations:

```markdown
# /pick-next-issue adjustments
- Add domain prefix: [backend], [frontend], [shared]
- Scope tests to affected packages
- Parallel execution by domain

# /review-pr adjustments
- Validate only affected packages
- Cross-package impact analysis
- Dependency version alignment
```

---

## Milestone Adaptations

### Feature-Based Milestones

```
M1: User Authentication
M2: Dashboard
M3: Reporting
M4: Admin Panel
M5: API v2
M6: Performance
```

### Time-Based Milestones

```
M1: Sprint 1 (Jan 1-14)
M2: Sprint 2 (Jan 15-28)
M3: Sprint 3 (Jan 29 - Feb 11)
...
```

### Risk-Based Milestones

```
M1: Critical Path (launch blockers)
M2: High Risk (complex features)
M3: Medium Risk (standard features)
M4: Low Risk (nice-to-haves)
```

---

## Custom Labels

Adapt labels to your domain:

### E-commerce
```
priority/revenue-impact
type/checkout
type/catalog
type/payments
risk/pci-compliance
```

### Healthcare
```
priority/patient-safety
type/ehr-integration
type/billing
risk/hipaa
risk/phi
```

### Fintech
```
priority/regulatory
type/transactions
type/reporting
risk/sox
risk/pci
```

---

## Getting Started Checklist

1. [ ] Fork this repository
2. [ ] Update tech stack in examples
3. [ ] Adjust coverage thresholds
4. [ ] Configure CI/CD platform commands
5. [ ] Customize labels for your domain
6. [ ] Define your milestones
7. [ ] Train team on workflow
8. [ ] Start with one small feature as pilot
9. [ ] Measure and iterate

---

## Support

If you need help adapting this workflow:

- 📧 tiago.sasaki@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/tiagosasaki)
- 🐙 [GitHub Issues](https://github.com/tjsasakifln/ai-dev-workflow/issues)
