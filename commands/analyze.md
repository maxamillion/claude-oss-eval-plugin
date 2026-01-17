---
description: "Phase 2: Perform detailed analysis of each candidate identified in Phase 1, focusing on core capabilities, architecture, and initial fit assessment."
---

# OSS Evaluation - Phase 2: Candidate Analysis

## Purpose

Perform detailed analysis of each candidate identified in Phase 1, focusing on core capabilities, architecture, and initial fit assessment.

## Prerequisites

- Phase 1 (Discovery) completed
- Read `.oss-eval/phase-01-discovery/candidates.md` for candidate list
- Read `.oss-eval/baseline-criteria.md` for comparison framework

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Prevent analysis bias
- **@skills/feature-verification/SKILL.md** - Verify claimed features
- **@skills/source-validation/SKILL.md** - Validate information sources

## Analysis Process

### Step 1: Per-Candidate Deep Dive

For each candidate, use WebSearch to gather:

1. **Official Documentation Review**
   - Architecture overview
   - Core concepts and design philosophy
   - API surface area

2. **GitHub/Repository Analysis**
   - Contributor count and diversity
   - Issue/PR activity patterns
   - Code quality indicators (CI, tests, linting)

3. **Adoption Indicators**
   - Notable users/companies
   - Case studies or testimonials
   - Stack Overflow question volume

### Step 2: Structured Analysis Template

For each candidate, create analysis in `.oss-eval/phase-02-analysis/<candidate-name>.md`:

```markdown
# Candidate Analysis: <name>

Analyzed: <timestamp>

## Overview

- **Repository**: <URL>
- **Version**: <current stable version>
- **First Release**: <date>
- **Maturity**: <alpha/beta/stable/mature>

## Core Capabilities

### Primary Use Cases
1. <use case> - [VERIFIED via <source>]
2. ...

### Architecture
- **Pattern**: <architectural pattern>
- **Language**: <implementation language>
- **Dependencies**: <key dependencies>

## Baseline Criteria Alignment

| Criterion | Status | Notes |
|-----------|--------|-------|
| <from baseline> | ✅/⚠️/❌ | <evidence> |
| ... | ... | ... |

## Strengths
1. <strength> - [SOURCE: <reference>]
2. ...

## Weaknesses
1. <weakness> - [SOURCE: <reference>]
2. ...

## Red Flags
- <any concerning patterns observed>

## Initial Recommendation
- [ ] Proceed to detailed evaluation
- [ ] Deprioritize (reason: ...)
- [ ] Eliminate (reason: ...)
```

### Step 3: Comparative Summary

Create `.oss-eval/phase-02-analysis/summary.md`:

```markdown
# Candidate Analysis Summary

Completed: <timestamp>

## Candidates Proceeding to Phase 3

| Candidate | Strengths | Concerns | Priority |
|-----------|-----------|----------|----------|
| ... | ... | ... | High/Medium/Low |

## Candidates Eliminated

| Candidate | Reason |
|-----------|--------|
| ... | ... |

## Key Observations

<cross-cutting themes and patterns>

## Recommended Focus Areas for Phase 3

<specific features/capabilities to investigate in feature matrix>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Consistent Framework**: Used same criteria for all candidates
- [ ] **Evidence-Based Claims**: All strengths/weaknesses have sources
- [ ] **No Halo Effect**: Didn't let one strength overshadow weaknesses
- [ ] **Verified Claims**: Feature claims verified via documentation/code, not marketing
- [ ] **Baseline Reference**: Evaluated against established criteria, not shifted standards

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "2": { "status": "completed", "completedAt": "<timestamp>", "proceedingCount": <n> }
  },
  "currentPhase": 3
}
```

## Next Step

> **Phase 2 Complete**: Analyzed `<n>` candidates, `<m>` proceeding to feature matrix.
>
> Run `/oss-eval:matrix` to begin Phase 3 (Feature Matrix Development).
