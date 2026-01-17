---
name: risk
description: "Phase 6: Synthesize findings from Phases 1-5 into a comprehensive risk assessment with quantified basis for decision-making."
---

# OSS Evaluation - Phase 6: Risk Assessment

## Purpose

Synthesize findings from Phases 1-5 into a comprehensive risk assessment for each candidate, providing a quantified basis for decision-making.

## Prerequisites

- Phases 1-5 completed
- All phase output files available in `.oss-eval/`

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Ensure objective risk scoring
- **@skills/source-validation/SKILL.md** - Cross-reference findings

## Risk Assessment Framework

### Step 1: Risk Category Definition

Assess each candidate across these dimensions:

```markdown
## Risk Categories

### 1. Technical Risk
- Code quality and maintainability
- Architecture soundness
- Performance characteristics
- Security posture
- Technical debt indicators

### 2. Adoption Risk
- Learning curve
- Migration complexity
- Breaking change frequency
- Documentation quality
- Community support availability

### 3. Operational Risk
- Deployment complexity
- Monitoring/observability
- Scaling characteristics
- Incident response capability
- Upgrade path clarity

### 4. Business Risk
- Licensing implications
- Vendor lock-in potential
- Long-term viability
- Total cost of ownership
- Strategic alignment

### 5. Community Risk
- Maintainer sustainability
- Corporate backing stability
- Fork likelihood
- Ecosystem fragmentation
- Support availability
```

### Step 2: Scoring Methodology

**Quantified Scoring (1-5 Scale)**:

| Score | Label | Definition |
|-------|-------|------------|
| 1 | Critical | Fundamental issues, likely blockers |
| 2 | High | Significant concerns requiring mitigation |
| 3 | Moderate | Manageable issues with known workarounds |
| 4 | Low | Minor concerns, easily addressed |
| 5 | Minimal | No significant issues identified |

**Weighting by Importance** (adjust based on context):

| Category | Default Weight | Adjustable Range |
|----------|----------------|------------------|
| Technical | 25% | 20-30% |
| Adoption | 20% | 15-25% |
| Operational | 20% | 15-25% |
| Business | 20% | 15-25% |
| Community | 15% | 10-20% |

### Step 3: Evidence-Based Scoring

For each score, provide evidence:

```markdown
## Risk Score: <Candidate>

### Technical Risk: X/5

| Factor | Score | Evidence |
|--------|-------|----------|
| Code Quality | X | <finding from Phase 2/7> |
| Architecture | X | <finding from Phase 7> |
| Performance | X | <benchmarks, reports> |
| Security | X | <audit results, CVE history> |
| Tech Debt | X | <observable indicators> |

**Weighted Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations**: <available options>
```

### Step 4: Comparative Risk Matrix

Create `.oss-eval/phase-06-risk/risk-assessment.md`:

```markdown
# Risk Assessment Report

Generated: <timestamp>
Evaluation: <topic>

## Executive Summary

| Candidate | Overall Risk | Recommendation |
|-----------|--------------|----------------|
| <A> | 🟢 Low (4.2/5) | Recommended |
| <B> | 🟡 Moderate (3.5/5) | Consider with mitigations |
| <C> | 🔴 High (2.1/5) | Not recommended |

## Detailed Risk Scores

### Score Matrix

| Category | Weight | <Candidate A> | <Candidate B> | <Candidate C> |
|----------|--------|---------------|---------------|---------------|
| Technical | 25% | 4.5 | 3.5 | 2.0 |
| Adoption | 20% | 4.0 | 4.0 | 3.0 |
| Operational | 20% | 4.0 | 3.0 | 2.5 |
| Business | 20% | 4.5 | 3.5 | 2.0 |
| Community | 15% | 4.0 | 3.5 | 1.5 |
| **Weighted Total** | 100% | **4.2** | **3.5** | **2.1** |

### Risk Breakdown by Candidate

#### <Candidate A>

**Overall Risk Level**: 🟢 Low

| Category | Score | Key Findings |
|----------|-------|--------------|
| Technical | 4.5/5 | <summary> |
| Adoption | 4.0/5 | <summary> |
| Operational | 4.0/5 | <summary> |
| Business | 4.5/5 | <summary> |
| Community | 4.0/5 | <summary> |

**Strengths**:
1. <strength with evidence>
2. <strength with evidence>

**Concerns**:
1. <concern with evidence>

**Mitigation Required**:
- <specific actions if adopted>

---

#### <Candidate B>
...

## Risk Comparison

### Technical Risk Comparison
<comparative analysis of technical risks>

### Adoption Risk Comparison
<comparative analysis of adoption risks>

### Business Risk Comparison
<comparative analysis of business risks>

## Critical Findings

### Blockers Identified
| Candidate | Blocker | Severity | Workaround |
|-----------|---------|----------|------------|
| <C> | <issue> | Critical | None available |

### Significant Concerns
| Candidate | Concern | Impact | Mitigation |
|-----------|---------|--------|------------|
| <B> | <issue> | Medium | <mitigation strategy> |

## Recommendations

### Proceed to Technical Deep-Dive (Phase 7+)
1. **<Candidate A>** - Recommended, lowest risk
2. **<Candidate B>** - Conditional, address concerns

### Eliminate from Consideration
1. **<Candidate C>** - <reason for elimination>

## Phase 6 Checkpoint

This completes the initial evaluation phases. At this point:

- [ ] Candidates have been discovered and filtered
- [ ] Features have been compared with [OSS]/[PAID] annotations
- [ ] Licensing has been analyzed
- [ ] Community health has been assessed
- [ ] Risks have been quantified

**Decision Point**: Proceed with top candidates to technical deep-dive?
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Consistent Scoring**: Same rubric applied to all candidates
- [ ] **Evidence-Based**: Every score has supporting evidence from prior phases
- [ ] **Baseline Adherence**: Original criteria used, not shifted standards
- [ ] **No Confirmation Bias**: Findings that contradict initial impressions included
- [ ] **Transparent Methodology**: Scoring method documented and reproducible

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "6": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 7
}
```

## Decision Point

After Phase 6, the user should decide whether to:
1. **Continue**: Proceed to Phase 7 (Architecture Analysis) with top candidates
2. **Narrow**: Eliminate additional candidates before deep-dive
3. **Pause**: Generate interim report with findings so far

## Next Step

> **Phase 6 Complete**: Risk assessment finalized.
>
> **Decision Required**: Which candidates should proceed to technical deep-dive?
>
> - Run `/oss-eval:architecture` to begin Phase 7 (Architecture Analysis)
> - Run `/oss-eval:report --interim` to generate Phase 1-6 summary report
