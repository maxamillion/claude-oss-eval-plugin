---
description: "Phase 7: Conduct deep technical analysis of candidate architectures including code-level examination and scalability characteristics."
---

# OSS Evaluation - Phase 7: Architecture Analysis

## Purpose

Conduct deep technical analysis of candidate architectures, including code-level examination, enterprise readiness assessment, and scalability characteristics.

## Prerequisites

- Phase 6 (Risk Assessment) completed
- Candidates selected for deep-dive documented
- Read `.oss-eval/phase-06-risk/risk-assessment.md` for proceeding candidates

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective technical assessment
- **@skills/feature-verification/SKILL.md** - Verify architectural claims

## Sub-Agent Strategy

**IMPORTANT**: Use isolated sub-agents for unbiased code analysis.

For each candidate, spawn a dedicated analysis agent:

```yaml
agent: general-purpose
context: fork  # Isolated context prevents bias contamination
prompt: |
  Analyze the architecture of <framework> focusing on:
  1. Core architectural patterns
  2. Extension/plugin mechanisms
  3. Performance characteristics
  4. Enterprise readiness indicators

  Examine the source code at <repository-url>
  Provide evidence-based findings only.
```

## Architecture Analysis Process

### Step 1: Architectural Pattern Analysis

For each candidate:

```markdown
## Architectural Patterns: <Candidate>

### Core Architecture
- **Pattern**: <MVC/MVVM/Hexagonal/etc.>
- **Design Philosophy**: <description>
- **Key Abstractions**: <core concepts>

### Modularity
- **Plugin System**: <description and capability>
- **Extension Points**: <where/how to extend>
- **Dependency Injection**: <support and approach>

### Data Flow
- **Request Lifecycle**: <flow description>
- **State Management**: <approach>
- **Event System**: <if applicable>
```

### Step 2: Code Quality Assessment

Analyze repository for quality indicators:

```markdown
## Code Quality: <Candidate>

### Testing
- **Test Coverage**: X% (verified via CI badges/reports)
- **Test Types**: Unit/Integration/E2E
- **Test Quality**: <assessment>

### Code Organization
- **Directory Structure**: <pattern>
- **Separation of Concerns**: Good/Fair/Poor
- **Naming Conventions**: Consistent/Inconsistent

### Documentation
- **Code Comments**: Adequate/Sparse/Excessive
- **API Documentation**: Generated/Manual/Missing
- **Architecture Docs**: Available/Partial/Missing

### Static Analysis
- **Linting**: <tools used>
- **Type Safety**: <TypeScript/Flow/None>
- **Security Scanning**: <tools, if any>
```

### Step 3: Enterprise Readiness Assessment

```markdown
## Enterprise Readiness: <Candidate>

### Scalability
| Aspect | Assessment | Evidence |
|--------|------------|----------|
| Horizontal Scaling | ✅/⚠️/❌ | <how/limitations> |
| Vertical Scaling | ✅/⚠️/❌ | <how/limitations> |
| Clustering | ✅/⚠️/❌ | <support level> |
| Load Balancing | ✅/⚠️/❌ | <integration approach> |

### High Availability
| Aspect | Assessment | Evidence |
|--------|------------|----------|
| Failover Support | ✅/⚠️/❌ | <mechanism> |
| Session Management | ✅/⚠️/❌ | <distributed support> |
| Graceful Degradation | ✅/⚠️/❌ | <patterns> |

### Security
| Aspect | Assessment | Evidence |
|--------|------------|----------|
| Authentication | ✅/⚠️/❌ | <built-in/plugin> |
| Authorization | ✅/⚠️/❌ | <RBAC/ABAC/etc.> |
| Input Validation | ✅/⚠️/❌ | <approach> |
| OWASP Top 10 | ✅/⚠️/❌ | <mitigations> |
| CVE History | X issues | <severity breakdown> |

### Observability
| Aspect | Assessment | Evidence |
|--------|------------|----------|
| Logging | ✅/⚠️/❌ | <structured/levels> |
| Metrics | ✅/⚠️/❌ | <Prometheus/StatsD/etc.> |
| Tracing | ✅/⚠️/❌ | <OpenTelemetry/etc.> |
| Health Checks | ✅/⚠️/❌ | <endpoints> |
```

### Step 4: Performance Characteristics

```markdown
## Performance Profile: <Candidate>

### Benchmarks
| Metric | Value | Source | Date |
|--------|-------|--------|------|
| Requests/sec | X | <benchmark source> | <date> |
| Latency (p50) | Xms | <benchmark source> | <date> |
| Latency (p99) | Xms | <benchmark source> | <date> |
| Memory Footprint | XMB | <measurement> | <date> |
| Startup Time | Xs | <measurement> | <date> |

### Performance Considerations
- **Hot Paths**: <identified bottlenecks>
- **Caching**: <built-in support>
- **Async Support**: <implementation quality>
- **Resource Management**: <connection pooling, etc.>

### Known Performance Issues
- <documented issues from GitHub/forums>
```

### Step 5: Create Architecture Report

Create `.oss-eval/phase-07-architecture/<candidate>/` for each:

```markdown
# Architecture Analysis: <Candidate>

Analyzed: <timestamp>
Repository: <URL>
Version Analyzed: <version>

## Executive Summary

<2-3 sentence summary of architectural fitness>

## Architectural Patterns

<from Step 1>

## Code Quality

<from Step 2>

## Enterprise Readiness

<from Step 3>

## Performance Characteristics

<from Step 4>

## Technical Debt Indicators

- **Deprecated APIs**: <usage of deprecated features>
- **TODO/FIXME Count**: X occurrences
- **Complexity Hotspots**: <files with high complexity>
- **Outdated Dependencies**: <dependency age assessment>

## Architecture Risks

| Risk | Severity | Impact | Mitigation |
|------|----------|--------|------------|
| <risk> | High/Med/Low | <impact> | <mitigation> |

## Architecture Score

| Dimension | Score (1-5) | Weight | Weighted |
|-----------|-------------|--------|----------|
| Design Quality | X | 20% | X |
| Code Quality | X | 20% | X |
| Enterprise Features | X | 25% | X |
| Performance | X | 20% | X |
| Maintainability | X | 15% | X |
| **Total** | - | 100% | **X.X** |

## Recommendations

### Proceed With
<candidates with strong architecture>

### Concerns to Address
<specific architectural concerns for each>

### Architecture Blockers
<fundamental architectural issues>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Isolated Analysis**: Sub-agents used for unbiased code review
- [ ] **Evidence-Based**: All claims verified via code/documentation
- [ ] **Consistent Criteria**: Same dimensions evaluated for all candidates
- [ ] **No Complexity Overestimation**: Component-level assessment, not holistic
- [ ] **Current Data**: Benchmarks and metrics are recent and verifiable

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "7": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 8
}
```

## Next Step

> **Phase 7 Complete**: Architecture analysis finalized for `<n>` candidates.
>
> Run `/oss-eval:requirements` to begin Phase 8 (Requirements Alignment).
