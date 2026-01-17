# Bias Prevention Skill

## Purpose

Core safeguards against common AI analysis pitfalls during OSS framework evaluation. This skill implements the 12 pitfall prevention rules to ensure objective, accurate, and defensible evaluations.

## Activation

This skill is automatically loaded during all OSS evaluation phases. It provides behavioral rules that must be followed throughout the evaluation process.

## The 12 AI Analysis Pitfalls

### Pitfall 1: Stale/Outdated Knowledge

**Problem**: AI knowledge has a training cutoff and may not reflect current state.

**Prevention Rules**:
- NEVER claim version numbers, release dates, or metrics from memory
- ALWAYS use WebSearch to verify:
  - Current stable version
  - Last release date
  - GitHub stars/forks
  - Download counts
  - Maintenance activity
- Include verification timestamp with each metric
- If WebSearch fails, explicitly state "Unable to verify current data"

**Example**:
```markdown
<!-- BAD -->
FastAPI has 60k+ GitHub stars

<!-- GOOD -->
FastAPI has 78,234 GitHub stars [Verified: 2025-01-16 via github.com/tiangolo/fastapi]
```

---

### Pitfall 2: False Feature Differentiation

**Problem**: Same features may exist under different names across frameworks, creating false differentiation.

**Prevention Rules**:
- Before marking a feature as "missing", search for:
  - Alternative terminology (middleware vs interceptors vs plugins)
  - Different architectural approaches (built-in vs pattern-based)
  - Community implementations
- Document equivalent features with terminology mapping
- Use @skills/feature-verification/SKILL.md for systematic checking

**Example**:
```markdown
<!-- BAD -->
| Feature | Framework A | Framework B |
|---------|-------------|-------------|
| Middleware | ✅ | ❌ |

<!-- GOOD -->
| Feature | Framework A | Framework B |
|---------|-------------|-------------|
| Request Pipeline | ✅ Middleware | ✅ Interceptors (equivalent) |
```

---

### Pitfall 3: OSS vs Commercial Feature Conflation

**Problem**: Confusing open-source capabilities with paid/enterprise tiers.

**Prevention Rules**:
- EVERY feature must be annotated with availability:
  - `[OSS]` - Available in open source
  - `[PAID]` - Requires paid license
  - `[ENTERPRISE]` - Enterprise tier only
  - `[PLUGIN]` - Requires separate plugin
  - `[COMMUNITY]` - Community-maintained only
- Verify tier availability via official pricing/licensing pages
- When unclear, investigate and document uncertainty

**Example**:
```markdown
<!-- BAD -->
| Feature | Status |
|---------|--------|
| SSO Support | ✅ |

<!-- GOOD -->
| Feature | Status |
|---------|--------|
| SSO Support | ✅ [PAID] Enterprise tier, ✅ [OSS] via community SAML plugin |
```

---

### Pitfall 4: Complexity Overestimation

**Problem**: Holistic complexity estimates tend to be inflated.

**Prevention Rules**:
- Break down effort into component-level tasks
- Never provide holistic estimates like "this is complex"
- Use structured effort breakdown:
  - Design: X days
  - Implementation: X days
  - Testing: X days
  - Documentation: X days
- Compare to similar past work when available
- State confidence level with estimates

**Example**:
```markdown
<!-- BAD -->
Integration will be complex and time-consuming

<!-- GOOD -->
Integration effort breakdown:
- API adapter: 2-3 days (similar to existing adapters)
- Configuration: 0.5 days
- Testing: 1-2 days
- Documentation: 0.5 days
Total: 4-6 days (confidence: 70%)
```

---

### Pitfall 5: Baseline Drift

**Problem**: Comparison criteria shift during evaluation, favoring later-analyzed candidates.

**Prevention Rules**:
- Establish baseline criteria in Phase 1 BEFORE deep analysis
- Document criteria in `.oss-eval/baseline-criteria.md`
- Do NOT modify baseline criteria after Phase 1 unless:
  - Explicitly requested by stakeholder
  - Documented with change rationale
- Review baseline before each phase to ensure consistency

**Checkpoint Question**: "Am I using the same criteria I established in Phase 1?"

---

### Pitfall 6: Marketing Language Adoption

**Problem**: Marketing claims may be repeated without technical verification.

**Prevention Rules**:
- Translate marketing language to technical specifications
- Verify marketing claims with:
  - Documentation
  - Source code
  - Community discussions
  - Independent benchmarks
- Use neutral, technical language in reports

**Translation Examples**:
| Marketing | Technical Translation |
|-----------|----------------------|
| "Blazing fast" | "Xms p50 latency in benchmark Y" |
| "Enterprise-ready" | "Supports X, Y, Z enterprise features" |
| "Batteries included" | "Includes built-in: A, B, C" |
| "Zero-config" | "Sensible defaults for: X, Y" |

---

### Pitfall 7: Popularity Bias

**Problem**: Popular options may be favored over objectively better alternatives.

**Prevention Rules**:
- Stars and downloads are INPUTS, not decision criteria
- Evaluate technical merit independently of popularity
- Consider why something is popular (marketing vs. merit)
- Give equal analysis depth to less popular candidates

**Checkpoint Question**: "Would my assessment change if star counts were hidden?"

---

### Pitfall 8: Recency Bias

**Problem**: Recent changes may be overweighted vs. stable track record.

**Prevention Rules**:
- Consider full project history, not just recent activity
- Distinguish between:
  - Maintenance activity (good: ongoing support)
  - Churn (concerning: frequent breaking changes)
- Value stability for critical infrastructure
- Document both recent activity AND historical patterns

---

### Pitfall 9: Confirmation Bias

**Problem**: Seeking evidence that confirms initial impressions.

**Prevention Rules**:
- Actively seek disconfirming evidence
- For each strength, look for weakness in same area
- For each preferred candidate, advocate for alternatives
- Use adversarial review (Phase 15) to challenge conclusions
- Document findings that contradict initial impressions

**Checkpoint Question**: "What evidence would change my recommendation?"

---

### Pitfall 10: Halo Effect

**Problem**: One strong attribute causing overestimation of other attributes.

**Prevention Rules**:
- Evaluate each dimension independently
- Use structured scoring frameworks
- Don't let one strength "cover" for weaknesses
- Document strengths AND weaknesses for all candidates
- Apply same rigor to favored and unfavored options

**Example**:
```markdown
<!-- BAD -->
Excellent documentation, so overall score: 5/5

<!-- GOOD -->
| Dimension | Score |
|-----------|-------|
| Documentation | 5/5 |
| Performance | 3/5 |
| Community | 4/5 |
| Overall: 4/5 (weighted average)
```

---

### Pitfall 11: Anchoring Bias

**Problem**: First candidate analyzed sets expectations for others.

**Prevention Rules**:
- Randomize analysis order when possible
- Use absolute criteria, not relative comparison
- Re-evaluate early candidates after analyzing later ones
- Apply same checklist to all candidates
- Document any re-evaluation adjustments

---

### Pitfall 12: Sunk Cost Bias

**Problem**: Investment in analysis may bias toward justifying that investment.

**Prevention Rules**:
- "None of the above" is a valid conclusion
- Willingness to restart with different candidates
- Don't force a recommendation if none are suitable
- Document when evaluation reveals need for different approach

---

## Bias Prevention Checklist

Use this checklist at phase boundaries:

```markdown
## Phase X Bias Check

- [ ] All metrics verified via current WebSearch
- [ ] No marketing language repeated without verification
- [ ] [OSS]/[PAID] annotations complete
- [ ] Effort estimates are component-level
- [ ] Same criteria used for all candidates
- [ ] Evidence for and against each candidate documented
- [ ] Would recommend same if popularity hidden?
- [ ] Any assumptions documented and flagged for validation
```

## Integration with Evaluation Phases

| Phase | Primary Pitfalls to Watch |
|-------|---------------------------|
| 1. Discovery | Popularity bias, Recency bias |
| 2. Candidate Analysis | Halo effect, Confirmation bias |
| 3. Feature Matrix | False differentiation, OSS/Commercial conflation |
| 4. Licensing | Stale knowledge |
| 5. Community | Popularity bias, Stale knowledge |
| 6. Risk Assessment | Confirmation bias, Halo effect |
| 7. Architecture | Complexity overestimation, Anchoring |
| 8. Requirements | Baseline drift, Confirmation bias |
| 9. Gap Mitigation | Complexity overestimation |
| 10-12. Integration | Marketing language, Stale knowledge |
| 13-14. Context/Hybrid | Sunk cost bias |
| 15. Validation | All pitfalls - final check |
