---
description: "Phase 8: Map candidate capabilities against specific product/project requirements to assess fit and identify gaps."
---

# OSS Evaluation - Phase 8: Requirements Alignment

## Purpose

Map candidate capabilities against specific product/project requirements to assess fit and identify gaps requiring mitigation.

## Prerequisites

- Phase 7 (Architecture Analysis) completed
- Read `.oss-eval/baseline-criteria.md` for requirements
- Read architecture reports from Phase 7

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective alignment assessment
- **@skills/feature-verification/SKILL.md** - Verify capability claims

## Requirements Alignment Process

### Step 1: Requirements Categorization

Structure requirements by priority and type:

```markdown
## Requirements Hierarchy

### P0 - Critical (Must Have)
Requirements that are absolute blockers if not met.

1. <requirement> - <brief description>
2. <requirement> - <brief description>

### P1 - Important (Should Have)
Requirements that significantly impact value but have workarounds.

1. <requirement> - <brief description>
2. <requirement> - <brief description>

### P2 - Desired (Nice to Have)
Requirements that add value but are not essential.

1. <requirement> - <brief description>
2. <requirement> - <brief description>

### Non-Functional Requirements
Cross-cutting concerns that apply across all functionality.

- Performance: <specific metrics>
- Security: <specific requirements>
- Scalability: <specific targets>
- Compliance: <regulatory requirements>
```

### Step 2: Capability Mapping

For each candidate, create detailed mapping:

```markdown
## Requirements Mapping: <Candidate>

### P0 Requirements (Critical)

| Requirement | Status | Capability | Gap | Evidence |
|-------------|--------|------------|-----|----------|
| <req 1> | ✅ Met | <how it's met> | - | [Docs](<url>) |
| <req 2> | ⚠️ Partial | <what's available> | <what's missing> | [Docs](<url>) |
| <req 3> | ❌ Not Met | - | <full gap> | Verified missing |

**P0 Score**: X/Y requirements met

### P1 Requirements (Important)

| Requirement | Status | Capability | Gap | Evidence |
|-------------|--------|------------|-----|----------|
| <req 1> | ✅ Met | <how it's met> | - | [Docs](<url>) |
| ... | ... | ... | ... | ... |

**P1 Score**: X/Y requirements met

### P2 Requirements (Desired)

| Requirement | Status | Capability | Gap | Evidence |
|-------------|--------|------------|-----|----------|
| <req 1> | ✅ Met | <how it's met> | - | [Docs](<url>) |
| ... | ... | ... | ... | ... |

**P2 Score**: X/Y requirements met

### Non-Functional Requirements

| Requirement | Target | Candidate Capability | Gap | Evidence |
|-------------|--------|---------------------|-----|----------|
| Response Time | <100ms | Xms (benchmarks) | +/-Xms | [Source](<url>) |
| Throughput | >10K rps | Xk rps | +/-Xk | [Source](<url>) |
| ... | ... | ... | ... | ... |
```

### Step 3: Gap Analysis

For each identified gap:

```markdown
## Gap Analysis: <Candidate>

### Critical Gaps (P0 Requirements)

#### Gap: <requirement not met>

**Requirement**: <description>
**Current State**: <what's available or missing>
**Impact**: <business/technical impact of gap>

**Mitigation Options**:
1. **Build Custom**:
   - Effort: X person-days
   - Complexity: High/Medium/Low
   - Maintainability: <concerns>

2. **Use Plugin/Extension**:
   - Plugin: <name>
   - Maturity: <assessment>
   - License: <compatibility>

3. **Alternative Approach**:
   - Description: <workaround>
   - Trade-offs: <what's sacrificed>

4. **Accept Gap**:
   - Justification: <why acceptable>
   - Risk: <residual risk>

**Recommended Mitigation**: <selected approach>
**Residual Risk**: High/Medium/Low

---

### Important Gaps (P1 Requirements)

<same structure as above>

### Desired Gaps (P2 Requirements)

<summary only, detailed analysis optional>
```

### Step 4: Fit Score Calculation

```markdown
## Fit Score: <Candidate>

### Scoring Methodology

| Priority | Weight | Max Points |
|----------|--------|------------|
| P0 (Critical) | 50% | 100 |
| P1 (Important) | 30% | 100 |
| P2 (Desired) | 10% | 100 |
| Non-Functional | 10% | 100 |

### Score Breakdown

| Category | Met | Partial | Not Met | Score |
|----------|-----|---------|---------|-------|
| P0 | X | Y | Z | X/100 |
| P1 | X | Y | Z | X/100 |
| P2 | X | Y | Z | X/100 |
| Non-Functional | X | Y | Z | X/100 |

### Weighted Total

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| P0 | X | 50% | X |
| P1 | X | 30% | X |
| P2 | X | 10% | X |
| Non-Functional | X | 10% | X |
| **Total** | - | 100% | **X/100** |
```

### Step 5: Create Requirements Report

Create `.oss-eval/phase-08-requirements/requirements-alignment.md`:

```markdown
# Requirements Alignment Report

Generated: <timestamp>
Requirements Count: P0: X, P1: Y, P2: Z

## Fit Score Summary

| Candidate | P0 Score | P1 Score | P2 Score | NF Score | Overall Fit |
|-----------|----------|----------|----------|----------|-------------|
| <A> | X% | X% | X% | X% | X% |
| <B> | X% | X% | X% | X% | X% |

## Critical Gap Summary

| Candidate | P0 Gaps | Mitigatable | Blockers |
|-----------|---------|-------------|----------|
| <A> | X | Y | Z |
| <B> | X | Y | Z |

## Detailed Alignment by Candidate

### <Candidate A>

<from Step 2-4>

### <Candidate B>

<from Step 2-4>

## Gap Mitigation Summary

| Gap | Candidate | Recommended Mitigation | Effort | Risk |
|-----|-----------|------------------------|--------|------|
| <gap> | <A> | <mitigation> | X days | Low |
| <gap> | <B> | <mitigation> | X days | Med |

## Recommendations

### Best Fit
<candidate with highest alignment and manageable gaps>

### Acceptable Fit
<candidates that work with mitigation>

### Poor Fit
<candidates with unbridgeable gaps>

## Decision Inputs for Phase 9

- Total gaps requiring mitigation: X
- Estimated mitigation effort: X person-days
- High-risk mitigations: X
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Requirements Unchanged**: Original baseline used, not adjusted to fit candidates
- [ ] **Evidence-Based Status**: Every Met/Partial/Not Met has verification
- [ ] **Consistent Evaluation**: Same rigor applied to all candidates
- [ ] **Gap Objectivity**: Gaps identified regardless of candidate preference
- [ ] **Mitigation Realism**: Effort estimates based on evidence, not optimism

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "8": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 9
}
```

## Next Step

> **Phase 8 Complete**: Requirements alignment scored for all candidates.
>
> Run `/oss-eval:gaps` to begin Phase 9 (Gap Mitigation Strategy).
