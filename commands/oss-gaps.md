# OSS Evaluation - Phase 9: Gap Mitigation Strategy

**Command**: `/oss-eval:gaps`

## Purpose

Develop comprehensive mitigation strategies for identified gaps, including effort estimation, risk assessment, and implementation planning.

## Prerequisites

- Phase 8 (Requirements Alignment) completed
- Read `.oss-eval/phase-08-requirements/requirements-alignment.md` for gap inventory

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Realistic effort estimation
- **@skills/feature-verification/SKILL.md** - Verify mitigation approaches

## Gap Mitigation Process

### Step 1: Gap Prioritization

Rank gaps by impact and urgency:

```markdown
## Gap Priority Matrix

### Priority Calculation
- **Impact**: Business value affected (1-5)
- **Urgency**: Time sensitivity (1-5)
- **Complexity**: Implementation difficulty (1-5, inverted: 5=easy)
- **Priority Score**: Impact × Urgency × Complexity / 25

| Gap | Candidate | Impact | Urgency | Complexity | Priority |
|-----|-----------|--------|---------|------------|----------|
| <gap 1> | <A> | 5 | 4 | 3 | 0.48 |
| <gap 2> | <A> | 3 | 3 | 4 | 0.36 |
| ... | ... | ... | ... | ... | ... |

### Priority Tiers

**Tier 1 (Score > 0.6)**: Address immediately
**Tier 2 (Score 0.3-0.6)**: Address in initial implementation
**Tier 3 (Score < 0.3)**: Address post-launch
```

### Step 2: Mitigation Strategy Development

For each prioritized gap:

```markdown
## Mitigation Strategy: <Gap Name>

**Candidate**: <candidate>
**Requirement**: <P0/P1/P2 - requirement description>
**Current State**: <what exists or is missing>
**Priority Tier**: 1/2/3

### Option Analysis

#### Option 1: Custom Development

**Description**: Build the capability from scratch

**Implementation Approach**:
1. <step 1>
2. <step 2>
3. <step 3>

**Effort Breakdown**:
| Component | Effort | Complexity | Risk |
|-----------|--------|------------|------|
| Design | X days | Medium | Low |
| Implementation | X days | High | Medium |
| Testing | X days | Medium | Low |
| **Total** | X days | - | - |

**Pros**:
- Full control over implementation
- Tailored to exact requirements

**Cons**:
- Maintenance burden
- May diverge from upstream

**Risk Assessment**: Medium
**Confidence Level**: 70%

---

#### Option 2: Community Plugin/Extension

**Plugin**: <name>
**Repository**: <URL>
**License**: <license>
**Maintenance Status**: Active/Sporadic/Abandoned

**Implementation Approach**:
1. Install plugin
2. Configure for requirements
3. Test integration

**Effort Breakdown**:
| Component | Effort | Complexity | Risk |
|-----------|--------|------------|------|
| Integration | X days | Low | Low |
| Configuration | X days | Low | Low |
| Testing | X days | Medium | Low |
| **Total** | X days | - | - |

**Pros**:
- Lower implementation effort
- Community maintained

**Cons**:
- Dependency on third party
- May not perfectly fit requirements

**Risk Assessment**: Low
**Confidence Level**: 85%

---

#### Option 3: Architectural Workaround

**Description**: Achieve requirement through alternative approach

**Approach**:
<description of workaround>

**Trade-offs**:
- <what's gained>
- <what's sacrificed>

**Effort**: X days
**Risk Assessment**: <assessment>
**Confidence Level**: X%

---

### Recommended Strategy

**Selected Option**: Option X
**Rationale**: <why this option>
**Residual Risk**: <remaining risk after mitigation>
**Dependencies**: <what this depends on>
**Timeline**: <when to implement>
```

### Step 3: Effort Aggregation

```markdown
## Total Mitigation Effort by Candidate

### <Candidate A>

| Gap | Strategy | Effort | Risk | Timeline |
|-----|----------|--------|------|----------|
| <gap 1> | Custom dev | X days | Med | Phase 1 |
| <gap 2> | Plugin | X days | Low | Phase 1 |
| <gap 3> | Workaround | X days | Low | Phase 2 |
| **Total** | - | **X days** | - | - |

**Risk Profile**:
- Low risk items: X (Y days)
- Medium risk items: X (Y days)
- High risk items: X (Y days)

### <Candidate B>

<same structure>
```

### Step 4: Comparative Analysis

```markdown
## Mitigation Comparison

### Effort Comparison

| Metric | <Candidate A> | <Candidate B> |
|--------|---------------|---------------|
| Total Effort | X days | Y days |
| High Risk Effort | X days | Y days |
| Custom Dev Required | X% | Y% |
| Plugin Dependencies | X | Y |

### Risk Comparison

| Risk Category | <Candidate A> | <Candidate B> |
|---------------|---------------|---------------|
| Implementation Risk | Low/Med/High | Low/Med/High |
| Maintenance Risk | Low/Med/High | Low/Med/High |
| Integration Risk | Low/Med/High | Low/Med/High |
| Timeline Risk | Low/Med/High | Low/Med/High |

### Total Cost of Ownership Impact

| Factor | <Candidate A> | <Candidate B> |
|--------|---------------|---------------|
| Initial Investment | X days | Y days |
| Ongoing Maintenance | X days/year | Y days/year |
| Risk Premium | X days | Y days |
| **Adjusted Total** | **X days** | **Y days** |
```

### Step 5: Create Gap Mitigation Report

Create `.oss-eval/phase-09-gaps/gap-mitigation.md`:

```markdown
# Gap Mitigation Strategy Report

Generated: <timestamp>
Total Gaps Analyzed: X

## Executive Summary

| Candidate | Gaps | Total Effort | Avg Risk | Recommendation |
|-----------|------|--------------|----------|----------------|
| <A> | X | Y days | Low | Manageable |
| <B> | X | Y days | Medium | Challenging |

## Prioritized Gap List

<from Step 1>

## Detailed Mitigation Strategies

### Tier 1 Gaps (Critical Priority)

<detailed strategies from Step 2>

### Tier 2 Gaps (Standard Priority)

<detailed strategies from Step 2>

### Tier 3 Gaps (Low Priority)

<summary strategies>

## Effort Summary

<from Step 3>

## Comparative Analysis

<from Step 4>

## Implementation Roadmap

### Phase 1: Pre-Launch Critical
| Gap | Candidate | Effort | Owner | Due |
|-----|-----------|--------|-------|-----|
| ... | ... | ... | TBD | TBD |

### Phase 2: Post-Launch Important
| Gap | Candidate | Effort | Owner | Due |
|-----|-----------|--------|-------|-----|
| ... | ... | ... | TBD | TBD |

### Phase 3: Future Nice-to-Have
| Gap | Candidate | Effort | Owner | Due |
|-----|-----------|--------|-------|-----|
| ... | ... | ... | TBD | TBD |

## Recommendations

### Proceed With Confidence
<candidates where gaps are manageable>

### Proceed With Caution
<candidates requiring significant mitigation>

### Reconsider
<candidates where mitigation exceeds value>

## Decision Point

**Key Question**: Is the mitigation effort justified by the candidate's strengths?

Factors to consider:
- Total mitigation effort vs. evaluation timeline
- Risk concentration in critical vs. non-critical areas
- Maintenance burden over time
- Team capability for custom development
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Realistic Estimates**: Effort based on similar past work, not optimism
- [ ] **Component-Level Breakdown**: No holistic complexity overestimation
- [ ] **Consistent Standards**: Same estimation approach for all candidates
- [ ] **Risk Objectivity**: Risks identified regardless of candidate preference
- [ ] **Alternative Exploration**: Multiple options considered before recommending

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "9": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 10
}
```

## Next Step

> **Phase 9 Complete**: Gap mitigation strategies developed.
>
> Run `/oss-eval:ui` to begin Phase 10 (UI Integration Analysis).
