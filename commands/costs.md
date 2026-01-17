---
description: "Phase 11: Quantify total cost of ownership (TCO) including infrastructure, licensing, maintenance, and hidden costs."
---

# OSS Evaluation - Phase 11: Operational Cost Quantification

## Purpose

Quantify the total cost of ownership (TCO) for each candidate, including infrastructure, licensing, maintenance, and hidden costs.

## Prerequisites

- Phase 10 (UI Integration) completed
- Understanding of operational context (cloud provider, scale, team)

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective cost assessment
- **@skills/source-validation/SKILL.md** - Verify pricing information

## Cost Quantification Process

### Step 1: Operational Context Definition

```markdown
## Operational Context

### Scale Parameters
- **Users**: X concurrent / Y monthly active
- **Transactions**: X/second peak, Y/day average
- **Data Volume**: X GB storage, Y GB/month growth
- **Requests**: X million/month

### Infrastructure Context
- **Cloud Provider**: AWS/GCP/Azure/On-prem
- **Region(s)**: <deployment regions>
- **Availability**: X% uptime requirement
- **Compliance**: <regulatory requirements>

### Team Context
- **Team Size**: X developers
- **Experience Level**: Junior/Mid/Senior mix
- **Current Skills**: <relevant expertise>
- **Available Training Budget**: $X

### Time Horizon
- **Evaluation Period**: X years TCO
- **Implementation Timeline**: X months
- **Growth Projection**: X% YoY
```

### Step 2: Direct Cost Analysis

For each candidate:

```markdown
## Direct Costs: <Candidate>

### Licensing Costs

| Tier | Annual Cost | Per-User Cost | Included Features |
|------|-------------|---------------|-------------------|
| OSS/Free | $0 | $0 | <features> |
| Pro | $X | $Y/user | <additional features> |
| Enterprise | $X | $Y/user | <additional features> |

**Projected License Cost**: $X/year
**Basis**: <tier selection rationale>

### Infrastructure Costs

| Resource | Specification | Monthly Cost | Annual Cost |
|----------|---------------|--------------|-------------|
| Compute | X instances × Y type | $X | $X |
| Database | X GB × Y type | $X | $X |
| Storage | X TB | $X | $X |
| Network | X GB egress | $X | $X |
| CDN | X requests | $X | $X |
| **Total** | - | **$X** | **$X** |

**Notes**:
- <scaling assumptions>
- <reserved vs. on-demand>
- <multi-region considerations>

### Third-Party Service Costs

| Service | Purpose | Monthly Cost | Annual Cost |
|---------|---------|--------------|-------------|
| Monitoring | <tool> | $X | $X |
| Logging | <tool> | $X | $X |
| APM | <tool> | $X | $X |
| Error Tracking | <tool> | $X | $X |
| **Total** | - | **$X** | **$X** |
```

### Step 3: Implementation Cost Analysis

```markdown
## Implementation Costs: <Candidate>

### Initial Development

| Phase | Effort (days) | Rate | Cost |
|-------|---------------|------|------|
| Setup & Configuration | X | $Y | $Z |
| Core Integration | X | $Y | $Z |
| Gap Mitigation (from Phase 9) | X | $Y | $Z |
| Testing | X | $Y | $Z |
| Documentation | X | $Y | $Z |
| **Total** | **X days** | - | **$Z** |

### Training

| Type | Attendees | Duration | Cost |
|------|-----------|----------|------|
| Official Training | X | Y days | $Z |
| Self-Paced Learning | X | Y hours | $Z (opportunity) |
| Pair Programming | X | Y days | $Z |
| **Total** | - | - | **$Z** |

### Migration (if applicable)

| Task | Effort | Risk | Cost |
|------|--------|------|------|
| Data Migration | X days | High/Med/Low | $Y |
| Integration Migration | X days | High/Med/Low | $Y |
| Testing & Validation | X days | High/Med/Low | $Y |
| **Total** | **X days** | - | **$Y** |
```

### Step 4: Ongoing Operational Costs

```markdown
## Ongoing Costs: <Candidate>

### Maintenance

| Activity | Frequency | Effort/Instance | Annual Effort | Cost |
|----------|-----------|-----------------|---------------|------|
| Version Upgrades | X/year | Y days | Z days | $W |
| Security Patches | X/year | Y hours | Z hours | $W |
| Dependency Updates | Monthly | Y hours | Z hours | $W |
| Bug Fixes (estimated) | Monthly | Y hours | Z hours | $W |
| **Total** | - | - | **Z days** | **$W** |

### Operations

| Activity | Frequency | Effort/Instance | Annual Effort | Cost |
|----------|-----------|-----------------|---------------|------|
| Monitoring Review | Daily | X min | Y hours | $Z |
| Incident Response | X/month | Y hours | Z hours | $W |
| Capacity Planning | Quarterly | Y hours | Z hours | $W |
| Backup Management | Weekly | X hours | Y hours | $Z |
| **Total** | - | - | **Y hours** | **$Z** |

### Support Costs

| Type | Level | Annual Cost |
|------|-------|-------------|
| Vendor Support | <tier> | $X |
| Community Support | (time) | $X (opportunity) |
| Consulting (projected) | X hours | $Y |
| **Total** | - | **$Z** |
```

### Step 5: Hidden & Risk Costs

```markdown
## Hidden Costs: <Candidate>

### Technical Debt

| Type | Likelihood | Impact | Expected Cost |
|------|------------|--------|---------------|
| Architecture Rework | X% | $Y | $Z |
| Performance Tuning | X% | $Y | $Z |
| Security Hardening | X% | $Y | $Z |
| **Expected Total** | - | - | **$Z** |

### Risk-Adjusted Costs

| Risk | Probability | Impact | Expected Value |
|------|-------------|--------|----------------|
| Major Version Migration | X% | $Y | $Z |
| Vendor Acquisition/Pivot | X% | $Y | $Z |
| Security Incident | X% | $Y | $Z |
| Scaling Issues | X% | $Y | $Z |
| **Total Risk Reserve** | - | - | **$Z** |

### Opportunity Costs

| Item | Description | Estimated Value |
|------|-------------|-----------------|
| Developer Productivity | <learning curve impact> | $X |
| Time to Market | <delay vs. alternatives> | $X |
| Innovation Capacity | <maintenance burden impact> | $X |
| **Total** | - | **$X** |
```

### Step 6: TCO Summary

Create `.oss-eval/phase-11-costs/operational-costs.md`:

```markdown
# Total Cost of Ownership Analysis

Generated: <timestamp>
Time Horizon: X years

## TCO Comparison Summary

| Cost Category | <Candidate A> | <Candidate B> |
|---------------|---------------|---------------|
| Licensing (X yr) | $X | $Y |
| Infrastructure (X yr) | $X | $Y |
| Implementation | $X | $Y |
| Training | $X | $Y |
| Maintenance (X yr) | $X | $Y |
| Operations (X yr) | $X | $Y |
| Support (X yr) | $X | $Y |
| Hidden/Risk | $X | $Y |
| **Total TCO** | **$X** | **$Y** |
| **Monthly Average** | **$X** | **$Y** |
| **Per-User (annual)** | **$X** | **$Y** |

## Cost Profile Visualization

### Year 1 Costs
| Category | <A> | <B> |
|----------|-----|-----|
| Initial Investment | $X | $Y |
| Recurring | $X | $Y |
| **Year 1 Total** | **$X** | **$Y** |

### Year 2-N Costs (Annual)
| Category | <A> | <B> |
|----------|-----|-----|
| Licensing | $X | $Y |
| Infrastructure | $X | $Y |
| Maintenance | $X | $Y |
| Operations | $X | $Y |
| **Annual Total** | **$X** | **$Y** |

## Detailed Cost Analysis

### <Candidate A>
<from Steps 2-5>

### <Candidate B>
<from Steps 2-5>

## Cost Sensitivity Analysis

### Scale Impact
| Scale (2x users) | <A> Cost Change | <B> Cost Change |
|------------------|-----------------|-----------------|
| Infrastructure | +X% | +Y% |
| Licensing | +X% | +Y% |
| Operations | +X% | +Y% |

### Worst Case Scenario
| Risk Materialized | <A> Impact | <B> Impact |
|-------------------|------------|------------|
| All hidden costs | +$X | +$Y |
| Major migration | +$X | +$Y |

## Cost Recommendations

### Lowest TCO
<candidate with best overall cost profile>

### Best Value (TCO vs. Capability)
<candidate with best cost/benefit ratio>

### Cost Risks to Monitor
<specific cost risks for each candidate>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Current Pricing**: All costs verified via current pricing pages
- [ ] **Consistent Methodology**: Same cost model applied to all candidates
- [ ] **Complete Accounting**: All cost categories included
- [ ] **Realistic Projections**: Growth and usage projections justified
- [ ] **Hidden Costs Included**: Not just obvious direct costs

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "11": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 12
}
```

## Next Step

> **Phase 11 Complete**: TCO analysis finalized.
>
> Run `/oss-eval:dx` to begin Phase 12 (Developer Experience Evaluation).
