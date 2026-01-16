# OSS Evaluation - Phase 5: Community Health Check

**Command**: `/oss-eval:community`

## Purpose

Assess the health, sustainability, and responsiveness of each candidate's open source community to evaluate long-term viability.

## Prerequisites

- Phase 4 (Licensing) completed
- Read `.oss-eval/config.json` for candidate list

## Required Skills

- **@skills/source-validation/SKILL.md** - Verify community metrics via web search
- **@skills/bias-prevention/SKILL.md** - Objective community assessment

## Community Health Assessment

### Step 1: Contributor Analysis

For each candidate, use WebSearch to gather current data:

1. **Core Maintainer Health**
   - WebSearch: `"<framework>" contributors maintainers`
   - Check: GitHub Insights, contributor graphs
   - Identify: Bus factor (how many critical maintainers)

2. **Contributor Diversity**
   - Single company vs. diverse contributors
   - Geographic distribution
   - New contributor onboarding rate

3. **Maintainer Activity**
   - Recent commits from core maintainers
   - Response time to issues/PRs
   - Communication activity

### Step 2: Issue & PR Metrics

**CRITICAL**: Verify these via current web search, not cached data.

```markdown
## Issue/PR Health: <Candidate>

Checked: <timestamp>
Source: <GitHub URL>

| Metric | Value | Trend | Benchmark |
|--------|-------|-------|-----------|
| Open Issues | X | ↑/↓/→ | vs 6mo ago |
| Issue Close Rate | X% | ↑/↓/→ | - |
| Median Issue Resolution | X days | ↑/↓/→ | - |
| Open PRs | X | ↑/↓/→ | - |
| PR Merge Rate | X% | ↑/↓/→ | - |
| Median PR Review Time | X days | ↑/↓/→ | - |
| Stale Issues (>1yr) | X | - | % of total |
```

### Step 3: Communication Channels

Assess community engagement venues:

```markdown
## Community Channels: <Candidate>

| Channel | URL | Activity Level | Official? |
|---------|-----|----------------|-----------|
| GitHub Discussions | <URL> | Active/Moderate/Low | Yes |
| Discord | <URL> | Active/Moderate/Low | Yes |
| Slack | <URL> | Active/Moderate/Low | Yes |
| Stack Overflow | [tag] | X questions/month | N/A |
| Reddit | r/<sub> | X posts/month | No |

### Response Quality
- Maintainer engagement: High/Medium/Low
- Community helpfulness: High/Medium/Low
- Documentation of resolutions: Good/Fair/Poor
```

### Step 4: Governance & Sustainability

```markdown
## Governance: <Candidate>

### Project Governance
- **Model**: BDFL / Committee / Foundation / Corporate
- **Decision Making**: <how decisions are made>
- **Roadmap Visibility**: Public/Private/Mixed

### Funding & Sustainability
- **Funding Model**: Donations / Sponsorship / Corporate / Foundation
- **Major Sponsors**: <list>
- **OpenCollective/GitHub Sponsors**: <if applicable>
- **Sustainability Concerns**: <any red flags>

### Corporate Backing
- **Primary Backer**: <company or none>
- **Risk Assessment**: <what happens if backer withdraws>
```

### Step 5: Release Cadence & Stability

```markdown
## Release Health: <Candidate>

### Release History (Last 2 Years)
| Version | Date | Type | Breaking Changes |
|---------|------|------|------------------|
| X.Y.Z | <date> | Major/Minor/Patch | Yes/No |

### Patterns
- **Release Frequency**: Monthly/Quarterly/Sporadic
- **LTS Policy**: Yes/No (duration: X years)
- **Deprecation Policy**: <description>
- **Migration Guides**: Available/Partial/Missing
```

### Step 6: Create Community Health Report

Create `.oss-eval/phase-05-community/community-health.md`:

```markdown
# Community Health Report

Analyzed: <timestamp>

## Summary Scorecard

| Candidate | Contributors | Activity | Responsiveness | Governance | Sustainability | Overall |
|-----------|--------------|----------|----------------|------------|----------------|---------|
| <A> | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 Excellent |
| <B> | 🟡 | 🟢 | 🟡 | 🟢 | 🟡 | 🟡 Good |
| <C> | 🔴 | 🟡 | 🔴 | 🔴 | 🔴 | 🔴 Concerning |

**Legend**: 🟢 Strong | 🟡 Adequate | 🔴 Weak

## Detailed Analysis

### <Candidate A>

#### Contributor Health
- **Bus Factor**: X core maintainers
- **Diversity**: <single company / diverse>
- **New Contributors**: X in last 6 months

#### Activity Metrics
- **Last Commit**: <date>
- **Commits (30 days)**: X
- **Active Contributors (30 days)**: X

#### Responsiveness
- **Issue Response Time**: Median X days
- **PR Review Time**: Median X days
- **Community Engagement**: <description>

#### Governance
- **Model**: <type>
- **Transparency**: High/Medium/Low
- **Conflict Resolution**: <observed patterns>

#### Sustainability
- **Funding**: <model>
- **Risk Factors**: <concerns>
- **Mitigation**: <available options>

#### Release Health
- **Cadence**: <pattern>
- **Stability**: <assessment>
- **LTS**: <availability>

---

### <Candidate B>
...

## Risk Assessment

### High Risk Indicators
<candidates with concerning patterns>

### Mitigation Strategies
<how to reduce community-related risks>

## Recommendations

### Strong Community (Low Risk)
<candidates with healthy, sustainable communities>

### Adequate Community (Manageable Risk)
<candidates with some concerns but viable>

### Weak Community (High Risk)
<candidates with significant community concerns>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Current Data**: All metrics from web search, not assumptions
- [ ] **Objective Criteria**: Same metrics applied to all candidates
- [ ] **Context Considered**: Small but healthy vs. large but declining
- [ ] **No Popularity Bias**: Stars don't equal health
- [ ] **Corporate Backing Neutral**: Neither penalized nor prioritized unfairly

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "5": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 6
}
```

## Next Step

> **Phase 5 Complete**: Community health assessed for all candidates.
>
> Run `/oss-eval:risk` to begin Phase 6 (Risk Assessment).
