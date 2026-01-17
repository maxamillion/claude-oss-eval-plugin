---
name: hybrid
description: "Phase 14: Explore hybrid approaches that combine multiple candidates for different use cases to optimize outcomes."
---

# OSS Evaluation - Phase 14: Hybrid Strategy Exploration

## Purpose

Explore hybrid approaches that combine multiple candidates or leverage different solutions for different use cases, potentially optimizing for the best of multiple worlds.

## Prerequisites

- Phase 13 (Product Context) completed
- Clear understanding of product requirements and constraints

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective hybrid assessment
- **@skills/feature-verification/SKILL.md** - Verify integration feasibility

## Hybrid Strategy Exploration Process

### Step 1: Hybrid Opportunity Identification

Analyze where hybrid approaches might add value:

```markdown
## Hybrid Opportunity Analysis

### Complementary Strengths

| <Candidate A> Strength | <Candidate B> Strength | Combination Value |
|------------------------|------------------------|-------------------|
| <strength> | <complementary strength> | <combined benefit> |

### Gap Coverage

| Gap in <A> | Covered by <B>? | Integration Complexity |
|------------|-----------------|------------------------|
| <gap> | Yes/No/Partial | High/Medium/Low |

### Use Case Segmentation

| Use Case | Best Fit | Reason |
|----------|----------|--------|
| <use case 1> | <Candidate A> | <why> |
| <use case 2> | <Candidate B> | <why> |
| <use case 3> | Either | <trade-offs> |

### Hybrid Viability Score: X/5
```

### Step 2: Hybrid Architecture Patterns

Define potential hybrid architectures:

```markdown
## Hybrid Architecture Options

### Option 1: Parallel Deployment

**Description**: Run both candidates for different parts of the system

**Architecture**:
```
┌─────────────────────────────────────────┐
│              Load Balancer              │
└─────────────────┬───────────────────────┘
                  │
      ┌───────────┴───────────┐
      │                       │
┌─────▼─────┐           ┌─────▼─────┐
│Candidate A│           │Candidate B│
│ (Use Case │           │ (Use Case │
│     1)    │           │     2)    │
└───────────┘           └───────────┘
```

**Pros**:
- Best-of-breed for each use case
- Clear separation of concerns

**Cons**:
- Operational complexity doubled
- Skill set fragmentation

**Effort**: X days
**Complexity**: High/Medium/Low

---

### Option 2: Primary + Plugin

**Description**: One candidate as primary, other's features via plugins

**Architecture**:
```
┌─────────────────────────────────────────┐
│           Candidate A (Primary)          │
│  ┌───────────────────────────────────┐  │
│  │    Candidate B Plugin/Adapter     │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

**Pros**:
- Single primary platform
- Leverages specific capabilities

**Cons**:
- Plugin maintenance
- Potential version conflicts

**Effort**: X days
**Complexity**: High/Medium/Low

---

### Option 3: Migration Path

**Description**: Start with one, migrate to other as scale increases

**Architecture**:
```
Phase 1: Candidate A (MVP-Scale)
    ↓
Phase 2: Candidate A + B features
    ↓
Phase 3: Candidate B (Enterprise-Scale)
```

**Pros**:
- Optimized for current needs
- Planned evolution path

**Cons**:
- Migration effort required
- Technical debt accumulation

**Effort**: X days (initial) + Y days (migration)
**Complexity**: High/Medium/Low

---

### Option 4: Façade Abstraction

**Description**: Abstract common interface, swap implementations

**Architecture**:
```
┌─────────────────────────────────────────┐
│         Application Layer               │
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│         Abstraction Façade              │
└─────────────────┬───────────────────────┘
                  │
      ┌───────────┴───────────┐
      │                       │
┌─────▼─────┐           ┌─────▼─────┐
│Candidate A│           │Candidate B│
│ Adapter   │           │ Adapter   │
└───────────┘           └───────────┘
```

**Pros**:
- Maximum flexibility
- Reduced lock-in

**Cons**:
- Abstraction overhead
- Lowest common denominator risk

**Effort**: X days
**Complexity**: High/Medium/Low
```

### Step 3: Hybrid Cost-Benefit Analysis

```markdown
## Hybrid Cost-Benefit Analysis

### Option Comparison

| Factor | Single (<A>) | Single (<B>) | Hybrid |
|--------|--------------|--------------|--------|
| Implementation | $X | $Y | $Z |
| Operations/year | $X | $Y | $Z |
| Flexibility | Low/Med/High | Low/Med/High | High |
| Complexity | Low/Med/High | Low/Med/High | High |
| Risk | Low/Med/High | Low/Med/High | Med/High |

### When Hybrid Makes Sense

**Hybrid Justified When**:
- [ ] Candidates have non-overlapping strengths worth combining
- [ ] Use cases are clearly separable
- [ ] Team has capacity for dual expertise
- [ ] Operational complexity is acceptable
- [ ] Cost premium is justified by value

**Hybrid NOT Justified When**:
- [ ] Overlap is high (pick one)
- [ ] Team is small (skill fragmentation)
- [ ] Timeline is tight (added complexity)
- [ ] Budget is constrained (operational overhead)

### Recommendation
<whether to pursue hybrid approach>
```

### Step 4: Hybrid Implementation Planning

If hybrid is viable:

```markdown
## Hybrid Implementation Plan

### Selected Hybrid Architecture
<chosen option from Step 2>

### Integration Design

#### Interface Boundaries
| Boundary | From | To | Protocol |
|----------|------|-----|----------|
| <boundary> | <A> | <B> | REST/gRPC/etc. |

#### Data Flow
| Data Type | Source | Destination | Sync Method |
|-----------|--------|-------------|-------------|
| <data> | <A> | <B> | Real-time/Batch |

#### Shared Components
| Component | Owner | Consumers |
|-----------|-------|-----------|
| <component> | <A/B/Shared> | <who uses> |

### Implementation Phases

| Phase | Focus | Deliverables | Effort |
|-------|-------|--------------|--------|
| 1 | Foundation | <deliverables> | X days |
| 2 | Integration | <deliverables> | X days |
| 3 | Optimization | <deliverables> | X days |

### Risk Mitigation

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Integration complexity | High/Med/Low | High/Med/Low | <approach> |
| Skill fragmentation | High/Med/Low | High/Med/Low | <approach> |
| Operational burden | High/Med/Low | High/Med/Low | <approach> |
```

### Step 5: Create Hybrid Strategy Report

Create `.oss-eval/phase-14-hybrid/hybrid-strategies.md`:

```markdown
# Hybrid Strategy Exploration Report

Generated: <timestamp>

## Executive Summary

**Hybrid Viability**: Viable/Not Viable/Conditional
**Recommended Approach**: <single candidate or specific hybrid>
**Rationale**: <key decision factors>

## Hybrid Opportunity Analysis

<from Step 1>

## Architecture Options Explored

<from Step 2>

## Cost-Benefit Analysis

<from Step 3>

## Recommendation

### Primary Recommendation
<single candidate or specific hybrid architecture>

### Rationale
1. <reason 1>
2. <reason 2>
3. <reason 3>

### Alternative Considered
<what was the close second choice>

### Implementation Approach
<if hybrid: from Step 4>
<if single: reference Phase 9 gaps>

## Comparison Summary

| Approach | TCO | Complexity | Flexibility | Risk | Fit |
|----------|-----|------------|-------------|------|-----|
| Single <A> | $X | Low/Med/High | Low/Med/High | Low/Med/High | X% |
| Single <B> | $Y | Low/Med/High | Low/Med/High | Low/Med/High | Y% |
| Hybrid | $Z | High | High | Med/High | Z% |

## Final Candidates

Based on hybrid analysis, candidates proceeding to validation:

1. **Primary**: <candidate or hybrid>
2. **Fallback**: <alternative if primary fails>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Genuine Evaluation**: Hybrid considered objectively, not dismissed reflexively
- [ ] **Complexity Honest**: Didn't underestimate hybrid complexity
- [ ] **Value Validated**: Hybrid benefits genuinely exceed single-solution benefits
- [ ] **Team Realistic**: Team capacity for hybrid approach honestly assessed
- [ ] **Cost Complete**: All hybrid costs including operational overhead included

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "14": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 15
}
```

## Next Step

> **Phase 14 Complete**: Hybrid strategies evaluated.
>
> Run `/oss-eval:validate` to begin Phase 15 (Final Validation & Adversarial Review).
