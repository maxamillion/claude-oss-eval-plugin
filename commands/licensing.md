---
description: "Phase 4: Conduct thorough analysis of licensing implications including dependencies, commercial use restrictions, and compliance requirements."
---

# OSS Evaluation - Phase 4: Licensing Deep Dive

## Purpose

Conduct thorough analysis of licensing implications for each candidate, including dependencies, commercial use restrictions, and compliance requirements.

## Prerequisites

- Phase 3 (Feature Matrix) completed
- Read `.oss-eval/phase-03-features/feature-matrix.md` for candidate list

## Required Skills

- **@skills/source-validation/SKILL.md** - Verify license information accuracy
- **@skills/bias-prevention/SKILL.md** - Objective license assessment

## Licensing Analysis Process

### Step 1: Primary License Identification

For each candidate, verify via web search:

1. **Official License File**
   - WebSearch: `"<framework>" license site:github.com`
   - Check: LICENSE, LICENSE.md, LICENSE.txt in repository root

2. **License Type Classification**
   - Permissive: MIT, Apache 2.0, BSD
   - Copyleft: GPL, LGPL, AGPL
   - Weak Copyleft: MPL, EPL
   - Commercial: Proprietary, dual-license

3. **Version Specificity**
   - Some projects change licenses between versions
   - Document: License changes, version thresholds

### Step 2: Dependency License Audit

**CRITICAL**: A project's usability depends on ALL its dependencies.

```markdown
## Dependency License Scan

### Direct Dependencies
| Dependency | License | Compatibility | Notes |
|------------|---------|---------------|-------|
| <dep> | MIT | ✅ Compatible | - |
| <dep> | GPL-3.0 | ⚠️ Copyleft | May require disclosure |

### Transitive Dependencies (High-Risk)
| Dependency | License | Risk | Mitigation |
|------------|---------|------|------------|
| <dep> | AGPL-3.0 | 🔴 High | Network copyleft |
```

### Step 3: Commercial Use Analysis

For each candidate, document:

```markdown
## Commercial Use Assessment: <Candidate>

### Permitted Uses
- [ ] Internal tools
- [ ] SaaS products
- [ ] Embedded in proprietary software
- [ ] Redistribution
- [ ] Modification without disclosure

### Required Actions
- [ ] Attribution required
- [ ] License file inclusion
- [ ] Source disclosure (if modified)
- [ ] Patent grant conditions

### Restrictions
- [ ] Trademark restrictions
- [ ] Patent litigation clauses
- [ ] Network use triggers (AGPL)
```

### Step 4: Dual/Commercial Licensing

Many OSS projects offer commercial licenses. Document:

```markdown
## Commercial Licensing Options

### <Candidate>

**Open Source License**: <license>
**Commercial License**: <available/not available>

| Tier | Price | Features |
|------|-------|----------|
| Community | Free | <features> |
| Enterprise | $X/yr | <additional features> |

**Trigger for Commercial License**:
- <when required>
```

### Step 5: Create Licensing Report

Create `.oss-eval/phase-04-licensing/licensing-analysis.md`:

```markdown
# Licensing Analysis

Analyzed: <timestamp>

## License Summary

| Candidate | Primary License | Category | Commercial Safe | Dependencies Risk |
|-----------|-----------------|----------|-----------------|-------------------|
| <A> | MIT | Permissive | ✅ Yes | 🟢 Low |
| <B> | Apache 2.0 | Permissive | ✅ Yes | 🟡 Medium |
| <C> | AGPL-3.0 | Strong Copyleft | ⚠️ Conditional | 🔴 High |

## Detailed Analysis

### <Candidate A>

**License**: MIT
**SPDX**: MIT
**Category**: Permissive

#### Permissions
- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use

#### Conditions
- ℹ️ License and copyright notice

#### Limitations
- ⚠️ No liability
- ⚠️ No warranty

#### Dependency Analysis
<dependency license breakdown>

#### Commercial License Option
<if available>

---

### <Candidate B>
...

## Compatibility Matrix

For combining candidates with each other or existing systems:

| | <A> | <B> | <C> | Proprietary |
|---|-----|-----|-----|-------------|
| <A> | ✅ | ✅ | ⚠️ | ✅ |
| <B> | ✅ | ✅ | ⚠️ | ✅ |
| <C> | ⚠️ | ⚠️ | ✅ | ❌ |

## Recommendations

### Low Risk
<candidates with permissive licenses and clean dependencies>

### Medium Risk (Manageable)
<candidates requiring specific compliance actions>

### High Risk (Careful Evaluation)
<candidates with copyleft or complex licensing>

## Legal Review Needed

<any candidates requiring legal consultation>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Primary Source Verification**: License verified from repository, not assumptions
- [ ] **Dependency Audit**: Transitive dependencies checked for license conflicts
- [ ] **Version Accuracy**: License version and any historical changes documented
- [ ] **No FUD**: Copyleft licenses assessed fairly, not dismissed reflexively
- [ ] **Commercial Path Clear**: Commercial licensing options documented where available

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "4": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 5
}
```

## Next Step

> **Phase 4 Complete**: Licensing analysis for all candidates documented.
>
> Run `/oss-eval:community` to begin Phase 5 (Community Health Check).
