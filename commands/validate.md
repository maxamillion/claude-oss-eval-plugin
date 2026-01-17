---
name: validate
description: "Phase 15: Conduct final validation through adversarial review ensuring all biases are addressed and recommendation is defensible."
---

# OSS Evaluation - Phase 15: Final Validation & Adversarial Review

## Purpose

Conduct final validation of the recommendation through adversarial review, ensuring all biases have been addressed and the recommendation is defensible.

## Prerequisites

- All phases 1-14 completed
- Primary recommendation identified from Phase 14

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Final bias check

## Required Agents

**CRITICAL**: This phase uses an **isolated sub-agent** for unbiased adversarial review.

```yaml
# Adversarial Reviewer Agent
agent: general-purpose
context: fork  # REQUIRED: Isolated context prevents bias contamination
```

The adversarial agent reviews the recommendation WITHOUT access to the full evaluation context, providing fresh perspective.

## Final Validation Process

### Step 1: Recommendation Summary

Compile the final recommendation for review:

```markdown
## Final Recommendation Summary

### Primary Recommendation
**Selected**: <candidate or hybrid approach>
**Confidence Level**: High/Medium/Low

### Key Decision Factors

| Factor | Weight | Score | Contribution |
|--------|--------|-------|--------------|
| Technical Fit | 25% | X/5 | X |
| Feature Coverage | 20% | X/5 | X |
| Operational Cost | 15% | X/5 | X |
| Community Health | 15% | X/5 | X |
| Developer Experience | 15% | X/5 | X |
| Risk Profile | 10% | X/5 | X |
| **Total** | 100% | - | **X/5** |

### Alternatives Considered

| Alternative | Why Not Selected |
|-------------|------------------|
| <Candidate B> | <specific reasons> |
| <Hybrid approach> | <specific reasons> |

### Critical Assumptions

1. <assumption 1> - <validation status>
2. <assumption 2> - <validation status>
3. <assumption 3> - <validation status>

### Known Gaps & Mitigations

| Gap | Mitigation | Residual Risk |
|-----|------------|---------------|
| <gap> | <mitigation plan> | Low/Med/High |
```

### Step 2: Spawn Adversarial Reviewer

**CRITICAL**: Use isolated agent for unbiased review.

```markdown
## Adversarial Review Request

### Instructions for Isolated Agent

You are an adversarial reviewer for an OSS evaluation. Your role is to:

1. **Challenge the Recommendation**: Find weaknesses in the selected candidate
2. **Advocate for Alternatives**: Make the strongest case for rejected options
3. **Identify Blind Spots**: Surface considerations that may have been missed
4. **Stress Test Assumptions**: Challenge critical assumptions

### Information Provided to Adversarial Agent

- Primary recommendation: <candidate>
- Key decision factors (summary only)
- Rejected alternatives (names only)
- Stated assumptions

### Questions for Adversarial Review

1. What are the strongest arguments AGAINST <recommended candidate>?
2. What scenario would make <rejected candidate> the better choice?
3. What information might be missing from this evaluation?
4. What biases might have influenced this recommendation?
5. What could go wrong with this choice in 12 months?

### Adversarial Review Format

```markdown
# Adversarial Review: <Recommended Candidate>

## Arguments Against Recommendation

### Critical Concerns
1. <concern with evidence/reasoning>
2. <concern with evidence/reasoning>

### Underweighted Factors
1. <factor that may have been undervalued>
2. <factor that may have been undervalued>

## Case for <Rejected Candidate>

### Strengths Overlooked
1. <strength that may have been undervalued>

### Scenarios Favoring Alternative
1. <scenario where alternative would be better>

## Potential Blind Spots

1. <consideration that may have been missed>
2. <consideration that may have been missed>

## Bias Assessment

| Potential Bias | Evidence | Risk Level |
|----------------|----------|------------|
| <bias type> | <indicators> | High/Med/Low |

## Stress Test Results

| Assumption | Challenge | Validity |
|------------|-----------|----------|
| <assumption> | <challenge> | Valid/Questionable/Invalid |

## Revised Risk Assessment

| Risk | Original | After Adversarial | Change |
|------|----------|-------------------|--------|
| <risk> | Low/Med/High | Low/Med/High | +/-/= |

## Recommendation Validity

**Recommendation Stands**: Yes/No/Conditional
**Conditions**: <if conditional, what must be true>
**Confidence Adjustment**: <higher/same/lower after review>
```
```

### Step 3: Respond to Adversarial Review

Address each adversarial finding:

```markdown
## Response to Adversarial Review

### Critical Concerns Response

| Concern | Response | Action Required |
|---------|----------|-----------------|
| <concern 1> | <rebuttal or acknowledgment> | Yes/No |
| <concern 2> | <rebuttal or acknowledgment> | Yes/No |

### Underweighted Factors Response

| Factor | Reconsideration | Weight Change |
|--------|-----------------|---------------|
| <factor 1> | <reconsidered assessment> | +/-/None |

### Blind Spots Addressed

| Blind Spot | Investigation | Finding |
|------------|---------------|---------|
| <blind spot 1> | <how addressed> | <result> |

### Bias Mitigation

| Bias Identified | Mitigation Applied | Status |
|-----------------|-------------------|--------|
| <bias 1> | <how addressed> | Mitigated/Acknowledged |

### Assumption Validation

| Assumption | Challenge Valid? | Updated Position |
|------------|------------------|------------------|
| <assumption 1> | Yes/No | <revised if needed> |

### Recommendation Status After Adversarial Review

**Original Recommendation**: <candidate>
**Post-Review Recommendation**: <same or changed>
**Confidence Level**: <updated confidence>

**Changes Made**:
- <change 1 based on review>
- <change 2 based on review>

**Unchanged Because**:
- <reason 1 for maintaining position>
```

### Step 4: Final Decision Documentation

```markdown
## Final Decision

### Selected Solution
**Primary**: <candidate or hybrid>
**Fallback**: <alternative if primary fails>

### Decision Confidence
**Pre-Adversarial**: X%
**Post-Adversarial**: X%
**Change Reason**: <why confidence changed or didn't>

### Dissenting Views Preserved

| Perspective | View | Validity | Response |
|-------------|------|----------|----------|
| Adversarial | <view> | Valid/Partial/Low | <how addressed> |

### Final Risk Acceptance

| Risk | Level | Owner | Acceptance |
|------|-------|-------|------------|
| <risk 1> | High/Med/Low | <role> | Accepted/Mitigated |

### Implementation Commitment

- [ ] Decision approved by: <stakeholders>
- [ ] Risks accepted by: <risk owners>
- [ ] Budget approved by: <finance>
- [ ] Timeline agreed by: <project management>
```

### Step 5: Create Validation Report

Create `.oss-eval/phase-15-validation/`:

**adversarial-review.md**:
```markdown
# Adversarial Review

<output from isolated agent>
```

**dissenting-views.md**:
```markdown
# Dissenting Views Record

## Summary of Dissent

| View | Source | Validity | Disposition |
|------|--------|----------|-------------|
| <view 1> | Adversarial Agent | Valid/Partial | Addressed/Noted |

## Detailed Dissenting Arguments

### <Dissenting View 1>

**Argument**: <the dissenting position>
**Evidence**: <supporting evidence>
**Response**: <how we addressed or why we disagree>
**Preserved For**: <future reference condition>

## Conditions That Would Trigger Reconsideration

1. <condition 1> - Would reconsider if <trigger>
2. <condition 2> - Would reconsider if <trigger>
```

**final-validation.md**:
```markdown
# Final Validation Report

Generated: <timestamp>
Evaluated: <topic>
Phases Completed: 15/15

## Final Recommendation

**Selected**: <candidate or hybrid>
**Confidence**: X%

## Validation Summary

### Adversarial Review
- Concerns Raised: X
- Concerns Addressed: Y
- Outstanding: Z

### Dissenting Views
- Views Captured: X
- Recommendation Changed: Yes/No

### Final Checks
- [ ] All 15 phases completed
- [ ] All bias prevention checkpoints passed
- [ ] Adversarial review completed
- [ ] Dissenting views documented
- [ ] Stakeholder alignment confirmed

## Evaluation Complete

This evaluation is ready for final report generation.

Run `/oss-eval:report` to generate the comprehensive final report.
```

## Bias Prevention - Final Verification

Before completing this phase, verify ALL prior checkpoints:

### Phase 1-6 Checkpoints
- [ ] Multiple source types used in discovery
- [ ] All metrics verified via current web search
- [ ] Baseline criteria established before analysis
- [ ] [OSS]/[PAID] annotations complete
- [ ] Consistent criteria used throughout

### Phase 7-12 Checkpoints
- [ ] Isolated agents used for code analysis
- [ ] Requirements not adjusted to fit candidates
- [ ] Effort estimates component-level
- [ ] DX assessed against actual team
- [ ] Costs include all categories

### Phase 13-15 Checkpoints
- [ ] Context not retrofitted to favor candidate
- [ ] Hybrid genuinely evaluated
- [ ] Adversarial review completed by isolated agent
- [ ] Dissenting views preserved

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "15": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": "complete",
  "status": "completed",
  "completedAt": "<timestamp>"
}
```

## Next Step

> **Phase 15 Complete**: Evaluation fully validated.
>
> All 15 phases complete. Run `/oss-eval:report` to generate the final comprehensive report.
