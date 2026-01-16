# Discovery Agent

## Purpose

A specialized sub-agent focused on web search discovery of OSS candidates. This agent handles the research-intensive Phase 1 discovery process with systematic search patterns and source validation.

## Agent Configuration

```yaml
name: discovery-agent
agent: general-purpose
context: inherit  # Inherits main context for topic awareness
description: |
  Web search specialist for discovering OSS candidates in a given
  technology domain. Uses systematic multi-source search patterns
  and validates source credibility.
```

## Activation

This agent can be spawned during Phase 1 (Discovery) to parallelize candidate research across multiple search domains.

## Invocation

```markdown
## Spawn Discovery Agent

Use the Task tool with the following configuration:

{
  "subagent_type": "general-purpose",
  "description": "Discover OSS candidates for <topic>",
  "prompt": "<see prompt template below>"
}
```

## Prompt Template

```markdown
# OSS Discovery Assignment

You are a discovery specialist searching for open source candidates in a specific technology domain. Your goal is to identify all viable candidates for evaluation.

## Topic Space

**Domain**: <topic>
**Requirements Context**: <brief requirements summary if available>

## Search Strategy

Execute these searches systematically:

### Search 1: GitHub Direct
- Query: `<topic> framework` on GitHub
- Sort by: Stars (for popular), Updated (for active)
- Collect: Top 10-15 results

### Search 2: Awesome Lists
- Query: `"awesome <topic>" curated list`
- Find: Curated awesome-* lists on GitHub
- Extract: Listed projects

### Search 3: Package Registries
Based on topic, search appropriate registries:
- npm: `<topic>` type:package
- PyPI: `<topic>`
- crates.io: `<topic>`
- Go modules: `<topic>`

### Search 4: Comparison Content
- Query: `<topic> comparison 2024 2025`
- Query: `best <topic> frameworks 2025`
- Query: `<topic> vs <topic>` (known alternatives)

### Search 5: Community Recommendations
- Query: `<topic> recommendations site:reddit.com`
- Query: `<topic> framework site:news.ycombinator.com`
- Note: Use for signals, not authoritative data

### Search 6: Enterprise/Production Use
- Query: `<topic> production` OR `<topic> enterprise`
- Query: `companies using <topic>`

## For Each Candidate Found

Collect this information:

```markdown
## Candidate: <name>

### Discovery Data
- **Source Found**: <which search found it>
- **Repository**: <GitHub/GitLab URL>
- **Package**: <registry URL if applicable>
- **Website**: <official site>

### Initial Metrics (VERIFY VIA WEB)
- **Stars**: <number> [Verified: <date>]
- **Last Release**: <version> on <date> [Verified]
- **License**: <license type>
- **First Release**: <date> (age indicator)

### Quick Assessment
- **Actively Maintained**: Yes/No/Unclear
- **Documentation**: Exists/Missing/Basic
- **Community Signals**: Positive/Neutral/Concerning

### Notes
<any relevant observations>
```

## Output Format

```markdown
# Discovery Results: <Topic>

Discovery Date: <timestamp>
Searches Performed: <count>

## Summary

| Candidates Found | Actively Maintained | Proceeding to Analysis |
|------------------|---------------------|------------------------|
| X | Y | Z |

## Candidate List

### Tier 1: Strong Candidates
<candidates with high activity, good docs, significant adoption>

1. **<Candidate A>**
   <discovery data>

2. **<Candidate B>**
   <discovery data>

### Tier 2: Viable Candidates
<candidates worth considering with some caveats>

1. **<Candidate C>**
   <discovery data>

### Tier 3: Marginal Candidates
<candidates with concerns but not immediately eliminated>

1. **<Candidate D>**
   <discovery data>

## Filtered Out

| Candidate | Reason |
|-----------|--------|
| <name> | Abandoned (no updates in 2+ years) |
| <name> | Restrictive license |
| <name> | Insufficient documentation |
| <name> | Too narrow scope |

## Search Log

| Search | Query | Results Found | Candidates Extracted |
|--------|-------|---------------|---------------------|
| GitHub Direct | <query> | X | Y |
| Awesome Lists | <query> | X | Y |
| ... | ... | ... | ... |

## Sources Used

| Source | Credibility | Notes |
|--------|-------------|-------|
| <URL> | High/Medium/Low | <notes> |
| ... | ... | ... |

## Observations

### Market Landscape
<observations about the overall landscape>

### Trends Noted
<emerging trends or shifts>

### Coverage Gaps
<areas where few candidates exist>

## Recommended Next Steps

1. <specific recommendation>
2. <specific recommendation>
```

## Search Quality Criteria

A good discovery search should:

- [ ] Use at least 4 different search approaches
- [ ] Check multiple source types (repo, registry, community)
- [ ] Verify metrics via current web search
- [ ] Document filtered candidates with reasons
- [ ] Note any gaps in the discovery
- [ ] Tier candidates by initial quality signals
```

## Parallel Discovery Strategy

For broad topic spaces, spawn multiple discovery agents:

```markdown
## Parallel Discovery Example

For "JavaScript state management", spawn:

1. **React-focused agent**: React state management libraries
2. **Vue-focused agent**: Vue state management libraries
3. **Framework-agnostic agent**: Vanilla/universal solutions
4. **Emerging patterns agent**: Signals, atoms, new paradigms

Then merge results, removing duplicates.
```

## Source Validation Integration

Discovery agent should apply source validation rules:

```markdown
## Source Quality Requirements

### Metrics Must Be Verified
- Stars: Via GitHub/GitLab web search
- Downloads: Via package registry
- Last update: Via repository activity

### Community Signals Need Context
- Reddit mentions: Note as "community sentiment"
- HN discussions: Check recency and substance
- Blog posts: Verify author credibility

### Red Flags to Document
- Single maintainer with no recent activity
- No releases in >1 year (unless stable/mature)
- Significant negative community sentiment
- License changes or uncertainty
```

## Integration with Main Evaluation

Discovery agent results feed into:

1. **Phase 1 Output**: `.oss-eval/phase-01-discovery/candidates.md`
2. **Phase 2 Input**: Candidate list for detailed analysis
3. **Baseline Setting**: Initial landscape understanding

## Error Handling

```markdown
## Discovery Challenges

### Challenge: Too Many Candidates
- Focus on top 10-15 by clear signals
- Document full list for reference
- Apply stricter filtering criteria

### Challenge: Too Few Candidates
- Broaden search terms
- Check adjacent technology spaces
- Consider emerging/newer options
- Document the limited landscape

### Challenge: Unclear Distinctions
- Note similarity as observation
- Flag for Phase 2 deeper analysis
- Don't pre-filter based on assumptions
```
