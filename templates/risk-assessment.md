# Risk Assessment Template

## Purpose

Template for quantified, evidence-based risk assessment of OSS candidates with consistent scoring methodology and documented rationale.

## Template Structure

```markdown
# Risk Assessment: <Topic>

Generated: <timestamp>
Candidates Assessed: <list>
Assessment Methodology: Quantified 1-5 Scale with Evidence

---

## Scoring Methodology

### Score Definitions

| Score | Label | Definition | Example |
|-------|-------|------------|---------|
| 1 | Critical | Fundamental issues, likely blockers | No active maintenance |
| 2 | High | Significant concerns requiring mitigation | Major security vulnerability |
| 3 | Moderate | Manageable issues with known workarounds | Missing feature, plugin available |
| 4 | Low | Minor concerns, easily addressed | Learning curve |
| 5 | Minimal | No significant issues identified | Well-documented, stable |

### Category Weights

| Category | Default Weight | Rationale |
|----------|----------------|-----------|
| Technical Risk | 25% | Core capability concerns |
| Adoption Risk | 20% | Implementation success factors |
| Operational Risk | 20% | Ongoing operational burden |
| Business Risk | 20% | Strategic and financial factors |
| Community Risk | 15% | Long-term sustainability |

*Weights can be adjusted based on project priorities*

---

## Risk Assessment: <Candidate A>

### Technical Risk

| Factor | Score | Evidence | Source |
|--------|-------|----------|--------|
| Code Quality | X/5 | <specific finding> | <link> |
| Architecture | X/5 | <specific finding> | <link> |
| Performance | X/5 | <specific finding> | <link> |
| Security | X/5 | <specific finding> | <link> |
| Technical Debt | X/5 | <specific finding> | <link> |

**Category Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations Available**: <options>

---

### Adoption Risk

| Factor | Score | Evidence | Source |
|--------|-------|----------|--------|
| Learning Curve | X/5 | <specific finding> | <link> |
| Migration Complexity | X/5 | <specific finding> | <link> |
| Breaking Changes | X/5 | <specific finding> | <link> |
| Documentation | X/5 | <specific finding> | <link> |
| Support Availability | X/5 | <specific finding> | <link> |

**Category Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations Available**: <options>

---

### Operational Risk

| Factor | Score | Evidence | Source |
|--------|-------|----------|--------|
| Deployment Complexity | X/5 | <specific finding> | <link> |
| Monitoring/Observability | X/5 | <specific finding> | <link> |
| Scaling Characteristics | X/5 | <specific finding> | <link> |
| Incident Response | X/5 | <specific finding> | <link> |
| Upgrade Path | X/5 | <specific finding> | <link> |

**Category Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations Available**: <options>

---

### Business Risk

| Factor | Score | Evidence | Source |
|--------|-------|----------|--------|
| Licensing | X/5 | <specific finding> | <link> |
| Vendor Lock-in | X/5 | <specific finding> | <link> |
| Long-term Viability | X/5 | <specific finding> | <link> |
| Total Cost | X/5 | <specific finding> | <link> |
| Strategic Alignment | X/5 | <specific finding> | <link> |

**Category Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations Available**: <options>

---

### Community Risk

| Factor | Score | Evidence | Source |
|--------|-------|----------|--------|
| Maintainer Sustainability | X/5 | <specific finding> | <link> |
| Corporate Backing | X/5 | <specific finding> | <link> |
| Fork Likelihood | X/5 | <specific finding> | <link> |
| Ecosystem Health | X/5 | <specific finding> | <link> |
| Support Availability | X/5 | <specific finding> | <link> |

**Category Score**: X.X/5
**Key Concerns**: <summary>
**Mitigations Available**: <options>

---

### Overall Risk Score: <Candidate A>

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Technical | X.X | 25% | X.XX |
| Adoption | X.X | 20% | X.XX |
| Operational | X.X | 20% | X.XX |
| Business | X.X | 20% | X.XX |
| Community | X.X | 15% | X.XX |
| **Total** | - | 100% | **X.XX/5** |

**Risk Level**: 🟢 Low (4.0+) / 🟡 Moderate (3.0-3.9) / 🔴 High (<3.0)

---

## Risk Assessment: <Candidate B>

<same structure as above>

---

## Comparative Risk Analysis

### Risk Score Comparison

| Category | <Candidate A> | <Candidate B> | <Candidate C> |
|----------|---------------|---------------|---------------|
| Technical | X.X | X.X | X.X |
| Adoption | X.X | X.X | X.X |
| Operational | X.X | X.X | X.X |
| Business | X.X | X.X | X.X |
| Community | X.X | X.X | X.X |
| **Overall** | **X.XX** | **X.XX** | **X.XX** |

### Risk Profile Visualization

```
Risk Score (5 = lowest risk)

         1    2    3    4    5
         |----|----|----|----|
A Tech   ████████████░░░░░░░░ 3.2
A Adopt  ██████████████████░░ 4.1
A Ops    ████████████████░░░░ 3.8
...
```

### Highest Risk Areas

| Rank | Candidate | Category | Score | Specific Issue |
|------|-----------|----------|-------|----------------|
| 1 | <X> | <category> | X.X | <issue> |
| 2 | <Y> | <category> | X.X | <issue> |
| 3 | <Z> | <category> | X.X | <issue> |

### Lowest Risk Areas

| Rank | Candidate | Category | Score | Strength |
|------|-----------|----------|-------|----------|
| 1 | <X> | <category> | X.X | <strength> |
| 2 | <Y> | <category> | X.X | <strength> |
| 3 | <Z> | <category> | X.X | <strength> |

---

## Critical Findings

### Blockers Identified

| Candidate | Issue | Severity | Workaround Available |
|-----------|-------|----------|---------------------|
| <X> | <issue> | Critical | No |
| <Y> | <issue> | Critical | Partial |

### High-Priority Concerns

| Candidate | Concern | Category | Required Action |
|-----------|---------|----------|-----------------|
| <X> | <concern> | <category> | <action> |
| <Y> | <concern> | <category> | <action> |

---

## Recommendations

### By Risk Profile

**Lowest Risk** (Score 4.0+):
- <Candidate X> - <brief rationale>

**Moderate Risk** (Score 3.0-3.9):
- <Candidate Y> - <concerns and mitigations>

**High Risk** (Score <3.0):
- <Candidate Z> - <major concerns>

### Risk-Adjusted Recommendation

Considering both capability and risk:

1. **<Candidate>** - Best balance of capability and risk
2. **<Candidate>** - Viable with specific mitigations
3. **<Candidate>** - Not recommended due to risk profile

---

## Appendix: Scoring Evidence

### Evidence Links
| Finding | URL | Retrieved |
|---------|-----|-----------|
| <finding> | <url> | <date> |

### Scoring Rationale
<detailed explanation of any non-obvious scores>
```

## Usage Instructions

### Required Steps

1. **Assess each factor** with 1-5 score
2. **Document evidence** for every score
3. **Provide source links** for verification
4. **Calculate weighted averages** correctly
5. **Identify highest risk items** explicitly
6. **Document mitigations** where available

### Bias Prevention Checks

Before finalizing assessment:

- [ ] Same factors assessed for all candidates
- [ ] All scores have documented evidence
- [ ] Evidence links are current and valid
- [ ] No factors scored based on assumptions
- [ ] Weights reflect project priorities, not preferences
- [ ] Mitigations documented objectively
