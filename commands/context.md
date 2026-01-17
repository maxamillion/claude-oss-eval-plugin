---
name: context
description: "Phase 13: Introduce specific product context and constraints to ground the evaluation in real business needs."
---

# OSS Evaluation - Phase 13: Product Context Introduction

## Purpose

Introduce specific product context and constraints that may affect the final recommendation, ensuring the evaluation is grounded in real business needs.

## Prerequisites

- Phase 12 (Developer Experience) completed
- Product owner/stakeholder input available

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective context assessment

## Product Context Introduction Process

### Step 1: Gather Product Context

Collect comprehensive product information:

```markdown
## Product Context

### Product Overview
- **Product Name**: <name>
- **Product Type**: <SaaS/Platform/Library/Internal Tool>
- **Current Stage**: <Greenfield/Enhancement/Migration/Modernization>
- **Primary Users**: <target audience>
- **User Volume**: <current/projected>

### Business Context
- **Business Model**: <how product generates value>
- **Competitive Position**: <market standing>
- **Strategic Importance**: Critical/High/Medium/Low
- **Time Sensitivity**: <go-to-market constraints>

### Technical Context
- **Existing Stack**: <current technologies>
- **Integration Points**: <systems to integrate with>
- **Data Constraints**: <data residency, compliance>
- **Performance Requirements**: <specific SLAs>

### Team Context
- **Available Team**: <size and composition>
- **Timeline**: <implementation timeline>
- **Budget Constraints**: <financial limits>
- **Risk Tolerance**: Conservative/Moderate/Aggressive
```

### Step 2: Constraint Mapping

Map product constraints to evaluation criteria:

```markdown
## Constraint Analysis

### Hard Constraints (Non-Negotiable)

| Constraint | Type | Impact on Evaluation |
|------------|------|---------------------|
| <constraint 1> | Technical/Business/Legal | <how it affects choice> |
| <constraint 2> | Technical/Business/Legal | <how it affects choice> |

### Soft Constraints (Preferences)

| Constraint | Priority | Trade-off Acceptable? |
|------------|----------|----------------------|
| <constraint 1> | High/Medium/Low | Yes/No/Conditional |
| <constraint 2> | High/Medium/Low | Yes/No/Conditional |

### Constraint Conflicts

| Constraint A | Constraint B | Resolution |
|--------------|--------------|------------|
| <constraint> | <conflicts with> | <how to resolve> |
```

### Step 3: Candidate Contextualization

Re-evaluate each candidate against product context:

```markdown
## Contextualized Assessment: <Candidate>

### Hard Constraint Alignment

| Constraint | Status | Evidence | Blocker? |
|------------|--------|----------|----------|
| <constraint 1> | ✅/⚠️/❌ | <how met/not met> | Yes/No |
| <constraint 2> | ✅/⚠️/❌ | <how met/not met> | Yes/No |

### Soft Constraint Alignment

| Constraint | Status | Trade-off Required |
|------------|--------|-------------------|
| <constraint 1> | ✅/⚠️/❌ | <what's sacrificed> |
| <constraint 2> | ✅/⚠️/❌ | <what's sacrificed> |

### Product-Specific Strengths

| Strength | Relevance to Product | Impact |
|----------|---------------------|--------|
| <strength from earlier phases> | <why it matters here> | High/Med/Low |

### Product-Specific Concerns

| Concern | Relevance to Product | Mitigation |
|---------|---------------------|------------|
| <concern from earlier phases> | <why it matters here> | <approach> |

### Timeline Feasibility

| Milestone | Required Date | Achievable? | Risk |
|-----------|---------------|-------------|------|
| MVP | <date> | Yes/No/Risky | <details> |
| Full Launch | <date> | Yes/No/Risky | <details> |
| Scale Point | <date> | Yes/No/Risky | <details> |

### Budget Feasibility

| Category | Budget | Projected | Variance |
|----------|--------|-----------|----------|
| Implementation | $X | $Y | +/-$Z |
| Year 1 Ops | $X | $Y | +/-$Z |
| Year 2+ Ops | $X | $Y | +/-$Z |
```

### Step 4: Stakeholder Alignment

```markdown
## Stakeholder Perspectives

### Engineering Perspective
- **Preferred Candidate**: <name>
- **Key Concerns**: <technical concerns>
- **Requirements**: <must-haves for engineering>

### Product Perspective
- **Preferred Candidate**: <name>
- **Key Concerns**: <feature/timeline concerns>
- **Requirements**: <must-haves for product>

### Business/Leadership Perspective
- **Preferred Candidate**: <name>
- **Key Concerns**: <cost/risk concerns>
- **Requirements**: <must-haves for business>

### Alignment Assessment

| Perspective | <Candidate A> | <Candidate B> |
|-------------|---------------|---------------|
| Engineering | Aligned/Neutral/Opposed | Aligned/Neutral/Opposed |
| Product | Aligned/Neutral/Opposed | Aligned/Neutral/Opposed |
| Business | Aligned/Neutral/Opposed | Aligned/Neutral/Opposed |

### Conflict Resolution
<how to address misalignment between stakeholders>
```

### Step 5: Create Context Report

Create `.oss-eval/phase-13-context/product-context.md`:

```markdown
# Product Context Report

Generated: <timestamp>

## Product Context Summary

<from Step 1>

## Constraint Analysis

<from Step 2>

## Contextualized Candidate Assessment

### <Candidate A>

<from Step 3>

#### Context Fit Score

| Dimension | Score | Weight | Weighted |
|-----------|-------|--------|----------|
| Hard Constraints | X/5 | 40% | X |
| Soft Constraints | X/5 | 20% | X |
| Timeline Fit | X/5 | 20% | X |
| Budget Fit | X/5 | 20% | X |
| **Total** | - | 100% | **X/5** |

### <Candidate B>

<same structure>

## Stakeholder Alignment

<from Step 4>

## Context-Adjusted Rankings

### Pre-Context Ranking
1. <Candidate X> (from Phase 1-12 analysis)
2. <Candidate Y>

### Post-Context Ranking
1. <Candidate X or Y> - <reason for change/no change>
2. <Candidate Y or X>

### Ranking Changes Explained
<why context changed or didn't change rankings>

## Decision Implications

### If <Candidate A> Selected
- **Advantages in Context**: <specific product benefits>
- **Challenges in Context**: <specific product challenges>
- **Recommended Approach**: <how to maximize fit>

### If <Candidate B> Selected
- **Advantages in Context**: <specific product benefits>
- **Challenges in Context**: <specific product challenges>
- **Recommended Approach**: <how to maximize fit>

## Unresolved Questions

<questions requiring stakeholder input before final decision>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Context Not Retrofitted**: Didn't adjust context to favor a candidate
- [ ] **Constraints Genuine**: Constraints reflect real limits, not preferences
- [ ] **Stakeholder Input**: Multiple perspectives incorporated
- [ ] **Evidence-Based Context**: Context claims verifiable
- [ ] **Transparent Ranking Changes**: Any ranking shifts explained

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "13": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 14
}
```

## Next Step

> **Phase 13 Complete**: Product context integrated.
>
> Run `/oss-eval:hybrid` to begin Phase 14 (Hybrid Strategy Exploration).
