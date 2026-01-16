# Source Validation Skill

## Purpose

Ensure accuracy and recency of information sources during OSS evaluation. This skill provides protocols for verifying source credibility, data freshness, and multi-source validation.

## Activation

This skill is critical during:
- All phases requiring quantitative data (stars, downloads, versions)
- Phase 4: Licensing (license information must be current)
- Phase 5: Community Health (metrics must be current)
- Phase 11: Operational Costs (pricing must be current)
- Any phase using web search for research

## Source Hierarchy

### Tier 1: Primary Sources (Highest Authority)

```markdown
## Primary Sources

| Source Type | Example | Reliability |
|-------------|---------|-------------|
| Official repository | github.com/<org>/<repo> | Highest |
| Official documentation | docs.<project>.io | Highest |
| Official package registry | npmjs.com, pypi.org | Highest |
| Project announcements | Official blog, GitHub releases | High |
| Maintainer statements | Verified maintainer comments | High |
```

**Usage Rules**:
- Always prefer primary sources
- Link directly to evidence
- Note version/date of information

### Tier 2: Secondary Sources (Verified Third-Party)

```markdown
## Secondary Sources

| Source Type | Example | Reliability |
|-------------|---------|-------------|
| Reputable benchmarks | TechEmpower, js-framework-benchmark | High |
| Conference talks | Official recordings | High |
| Established tech blogs | Company engineering blogs | Medium-High |
| Security advisories | CVE database, Snyk | High |
| Stack Overflow (answers) | Highly-voted answers | Medium |
```

**Usage Rules**:
- Verify with primary source when possible
- Note publication date
- Cross-reference with other sources

### Tier 3: Community Sources (Unverified)

```markdown
## Community Sources

| Source Type | Example | Reliability |
|-------------|---------|-------------|
| Blog posts | Medium, Dev.to | Variable |
| Reddit discussions | r/<framework> | Low-Medium |
| Twitter/Social | Developer tweets | Low |
| Forum posts | Unverified claims | Low |
| AI-generated content | ChatGPT, etc. | Do not use |
```

**Usage Rules**:
- Use only for qualitative signals
- Never use for quantitative data
- Always seek primary verification
- Note as "community sentiment" not "fact"

## Data Freshness Requirements

### Critical Data (Must Be Current)

```markdown
## Data Requiring Real-Time Verification

| Data Type | Max Age | Verification Method |
|-----------|---------|---------------------|
| Version numbers | Real-time | WebSearch → repo/registry |
| Pricing | Real-time | WebSearch → pricing page |
| License | Real-time | WebSearch → LICENSE file |
| Stars/Forks | 24 hours | GitHub API or web |
| Download counts | 7 days | Registry API |
| Last commit | 24 hours | Repository check |
| Open issues | 7 days | Issue tracker check |
```

### Standard Data (Moderate Freshness)

```markdown
## Data with Moderate Freshness Needs

| Data Type | Max Age | Notes |
|-----------|---------|-------|
| Benchmarks | 6 months | Check for newer versions tested |
| Feature documentation | 1 month | Verify version matches |
| Tutorial content | 3 months | Check still applies |
| Community health | 1 month | Trends matter |
```

### Stable Data (Long-Term Valid)

```markdown
## Data with Long-Term Validity

| Data Type | Max Age | Notes |
|-----------|---------|-------|
| Architectural patterns | Years | Core design rarely changes |
| Historical milestones | Permanent | Facts don't change |
| Design philosophy | Years | Unless pivot announced |
```

## Verification Protocol

### Quantitative Data Verification

For any number (stars, downloads, version, price):

```markdown
## Verification Record

**Claim**: <the data point>
**Source**: <where obtained>
**Verification Date**: <timestamp>
**Verification Method**: <how verified>
**Result**: <confirmed value>
**Status**: ✅ Verified / ⚠️ Unable to verify / ❌ Contradicted

Example:
**Claim**: "FastAPI has 70k+ GitHub stars"
**Source**: Initial AI knowledge
**Verification Date**: 2025-01-16
**Verification Method**: WebSearch → github.com/tiangolo/fastapi
**Result**: 78,234 stars
**Status**: ✅ Verified (updated to current)
```

### Qualitative Claim Verification

For subjective claims (best practices, recommendations):

```markdown
## Claim Verification

**Claim**: "<qualitative statement>"
**Original Source**: <where claim originated>

**Corroborating Sources**:
1. <source 1> - <how it supports>
2. <source 2> - <how it supports>

**Contradicting Sources**:
1. <source if any> - <contradiction>

**Verification Status**:
- ✅ Well-supported (3+ corroborating)
- ⚠️ Mixed evidence
- ❌ Contradicted
- ❓ Unverifiable
```

## Multi-Source Validation

For critical decisions, require multiple sources:

```markdown
## Multi-Source Requirement Matrix

| Decision Impact | Required Sources | Source Tier |
|-----------------|------------------|-------------|
| Recommendation change | 3+ sources | At least 2 Tier 1 |
| Feature claim | 2+ sources | At least 1 Tier 1 |
| Risk assessment | 2+ sources | Mix of Tier 1-2 |
| Community sentiment | 3+ sources | Any tier |
| Pricing/licensing | 1 source | Must be Tier 1 |
```

## WebSearch Best Practices

### Effective Search Patterns

```markdown
## Search Query Templates

### Version/Release Info
- `<framework> latest version release`
- `<framework> changelog 2024 2025`
- `site:github.com/<org>/<repo>/releases`

### Pricing/Licensing
- `<product> pricing 2024 2025`
- `<project> license change announcement`
- `site:<product>.com/pricing`

### Community Health
- `<framework> maintenance status`
- `<framework> future roadmap`
- `"<framework>" "maintainers" OR "contributors" 2024`

### Security
- `<framework> CVE`
- `<framework> security vulnerability 2024`
- `site:snyk.io <framework>`

### Performance
- `<framework> benchmark 2024`
- `<framework> vs <competitor> performance`
```

### Search Result Evaluation

```markdown
## Result Quality Checklist

For each search result, assess:

- [ ] Publication date visible and recent
- [ ] Author/source credibility established
- [ ] Content matches current version
- [ ] No obvious bias (e.g., competitor hit piece)
- [ ] Specific evidence provided, not just claims

If < 3 checked, seek additional sources
```

## Handling Conflicting Information

When sources disagree:

```markdown
## Conflict Resolution Protocol

### Step 1: Identify Conflict
- Source A says: <claim>
- Source B says: <contradicting claim>

### Step 2: Assess Source Quality
| Criterion | Source A | Source B |
|-----------|----------|----------|
| Tier | X | Y |
| Date | <date> | <date> |
| Specificity | High/Med/Low | High/Med/Low |
| Evidence | <type> | <type> |

### Step 3: Resolution
- [ ] More recent source wins (if data could change)
- [ ] Higher tier source wins (if equal recency)
- [ ] More specific source wins (if equal tier)
- [ ] Document both if unresolvable

### Step 4: Documentation
**Resolved Claim**: <what we're using>
**Confidence**: High/Medium/Low
**Note**: <any caveats about conflicting info>
```

## Citation Format

Standard citation format for evaluation documents:

```markdown
## Citation Formats

### Inline Citation
"FastAPI supports async/await natively" [FastAPI Docs, 2025]

### Verification Citation
Stars: 78,234 [Verified: 2025-01-16, github.com/tiangolo/fastapi]

### Full Reference
[FastAPI Docs, 2025]: https://fastapi.tiangolo.com/async/
Retrieved: 2025-01-16
Version documented: 0.109.0
```

## Red Flags

Watch for these source reliability issues:

```markdown
## Source Red Flags

### Immediate Disqualification
- AI-generated content (including other AI assistants)
- Unverified social media claims
- Anonymous sources
- Sources with obvious commercial bias

### Requires Additional Verification
- Blog posts without dates
- Content older than 1 year
- Single-source claims for critical data
- Community forums without official confirmation

### Acceptable with Caveats
- Dated content with "as of <date>" note
- Community sentiment with "anecdotal" qualifier
- Older benchmarks with version context
```

## Integration with Bias Prevention

This skill directly addresses:
- **Pitfall 1**: Stale/Outdated Knowledge (verification protocol)
- **Pitfall 6**: Marketing Language Adoption (source hierarchy)
- **Pitfall 9**: Confirmation Bias (multi-source validation)
