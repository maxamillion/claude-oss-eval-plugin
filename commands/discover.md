---
name: discover
description: "Phase 1: Conduct comprehensive web search discovery to identify candidate frameworks/libraries in the specified topic space."
---

# OSS Evaluation - Phase 1: Discovery

## Purpose

Conduct comprehensive web search discovery to identify candidate frameworks/libraries in the specified topic space.

## Prerequisites

- Evaluation workspace initialized via `/oss-eval:start`
- Read `.oss-eval/config.json` to get topic space

## Required Skills

- **@skills/source-validation/SKILL.md** - Verify source credibility
- **@skills/bias-prevention/SKILL.md** - Prevent discovery bias

## Discovery Process

### Step 1: Multi-Source Search

Use WebSearch to query multiple source types:

1. **GitHub Search**: `"<topic> framework" site:github.com`
2. **Awesome Lists**: `"awesome <topic>" curated list`
3. **Comparison Articles**: `"<topic> comparison 2024 2025"`
4. **Reddit/HN Discussions**: `"<topic> recommendations" site:reddit.com OR site:news.ycombinator.com`
5. **Official Registries**: Search npm, PyPI, crates.io, etc. as appropriate

### Step 2: Initial Candidate Collection

For each discovered candidate, collect:

```markdown
## Candidate: <name>

- **Repository**: <GitHub/GitLab URL>
- **Package**: <npm/PyPI/etc. URL>
- **Documentation**: <docs URL>
- **Stars/Downloads**: <metrics - VERIFY via web search>
- **License**: <license type>
- **Last Release**: <date - VERIFY via web search>
- **Discovery Source**: <where found>
```

### Step 3: Apply Discovery Filters

Remove candidates that:
- Have not been updated in >2 years (unless stable/mature)
- Have <100 GitHub stars (unless niche/specialized)
- Lack documentation
- Have restrictive licenses incompatible with requirements

### Step 4: Establish Baseline Criteria

**CRITICAL FOR BIAS PREVENTION**: Define comparison framework NOW before deep analysis.

Create `.oss-eval/baseline-criteria.md`:

```markdown
# Evaluation Baseline Criteria

Established: <timestamp>

## Functional Requirements
- [ ] <requirement 1>
- [ ] <requirement 2>
- [ ] ...

## Non-Functional Requirements
- [ ] Performance: <specific metric>
- [ ] Scalability: <specific metric>
- [ ] Security: <specific requirements>

## Must-Have Features
1. <feature>
2. <feature>

## Nice-to-Have Features
1. <feature>
2. <feature>

## Dealbreakers
1. <constraint>
2. <constraint>
```

## Output Files

Create `.oss-eval/phase-01-discovery/`:

### `candidates.md`
```markdown
# Discovery Results: <topic>

Discovered: <timestamp>
Sources Searched: <count>

## Candidates for Evaluation

| # | Name | Repository | Stars | License | Last Update |
|---|------|------------|-------|---------|-------------|
| 1 | ... | ... | ... | ... | ... |

## Filtered Out

| Name | Reason |
|------|--------|
| ... | ... |

## Discovery Notes

<observations about the landscape>
```

### `sources.md`
```markdown
# Discovery Sources

## Searches Performed
1. <query> - <result count> results
2. ...

## Sources Consulted
- <URL> - <credibility assessment>
- ...

## Source Validation Notes
<any concerns about source reliability>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Multiple Source Types**: Used at least 3 different source types
- [ ] **Recency Check**: All metrics verified via current web search (not cached knowledge)
- [ ] **Baseline Established**: Comparison criteria defined before deep analysis
- [ ] **No Premature Filtering**: Didn't exclude candidates based on assumptions

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "1": { "status": "completed", "completedAt": "<timestamp>", "candidateCount": <n> }
  },
  "currentPhase": 2
}
```

Update `.oss-eval/progress.md` with phase status.

## Next Step

> **Phase 1 Complete**: Discovered `<n>` candidates for evaluation.
>
> Run `/oss-eval:analyze` to begin Phase 2 (Candidate Analysis).
