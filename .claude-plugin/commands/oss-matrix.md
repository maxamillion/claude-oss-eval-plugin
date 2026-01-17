# OSS Evaluation - Phase 3: Feature Matrix Development

**Command**: `/oss-eval:matrix`

## Purpose

Develop a comprehensive, annotated feature comparison matrix with rigorous [OSS]/[PAID] differentiation and cross-platform verification.

## Prerequisites

- Phase 2 (Candidate Analysis) completed
- Read `.oss-eval/phase-02-analysis/summary.md` for proceeding candidates
- Read `.oss-eval/baseline-criteria.md` for required features

## Required Skills

- **@skills/feature-verification/SKILL.md** - CRITICAL for this phase
- **@skills/bias-prevention/SKILL.md** - Prevent false differentiation

## Feature Matrix Development

### Step 1: Feature Category Definition

Based on baseline criteria, define feature categories:

```markdown
## Feature Categories

### Core Functionality
- <feature area 1>
- <feature area 2>

### Integration Capabilities
- <integration type 1>
- <integration type 2>

### Developer Experience
- <DX feature 1>
- <DX feature 2>

### Operations & Monitoring
- <ops feature 1>
- <ops feature 2>

### Security
- <security feature 1>
- <security feature 2>
```

### Step 2: Feature Verification Protocol

**CRITICAL**: For each feature claim, follow this verification process:

1. **Check Official Documentation**
   - WebSearch: `"<framework> <feature>" site:<docs-domain>`
   - Record: URL, version introduced, any limitations

2. **Verify in Source Code** (when documentation unclear)
   - Search repository for implementation
   - Note: actual capability vs. documented capability

3. **Check Issue Tracker**
   - Search for related feature requests or bugs
   - Identify any known limitations

4. **Cross-Platform Name Check**
   - Same feature may have different names across frameworks
   - Example: "middleware" vs "interceptors" vs "plugins"

### Step 3: Feature Annotation Requirements

Every feature entry MUST include:

```markdown
| Feature | Candidate A | Candidate B | Candidate C |
|---------|-------------|-------------|-------------|
| <name> | ✅ [OSS] v2.0+ | ⚠️ [PAID] Enterprise only | ❌ Not available |
| <name> | ✅ [OSS] (as "alt-name") | ✅ [OSS] | ✅ [OSS] Plugin required |
```

**Annotation Legend**:
- `[OSS]` - Available in open source version
- `[PAID]` - Requires paid/enterprise tier
- `[PLUGIN]` - Requires additional plugin/extension
- `[COMMUNITY]` - Community-maintained, not official
- `[DEPRECATED]` - Being phased out
- `[BETA]` - Not production-ready

**Status Symbols**:
- ✅ Full support
- ⚠️ Partial/limited support
- ❌ Not available
- 🔄 In development

### Step 4: Build Complete Matrix

Create `.oss-eval/phase-03-features/feature-matrix.md`:

```markdown
# Feature Comparison Matrix

Generated: <timestamp>
Candidates Compared: <list>

## Legend

| Symbol | Meaning |
|--------|---------|
| ✅ | Full support |
| ⚠️ | Partial/limited |
| ❌ | Not available |
| [OSS] | Open source |
| [PAID] | Paid/Enterprise |

## Core Functionality

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <feature> | ✅ [OSS] | ⚠️ [OSS] Limited | ❌ | [Source](<URL>) |
| ... | ... | ... | ... | ... |

## Integration Capabilities

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| ... | ... | ... | ... | ... |

## Developer Experience

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| ... | ... | ... | ... | ... |

## Operations & Monitoring

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| ... | ... | ... | ... | ... |

## Security

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| ... | ... | ... | ... | ... |

## Summary Scores

| Candidate | Core | Integration | DX | Ops | Security | Total |
|-----------|------|-------------|-----|-----|----------|-------|
| <A> | X/Y | X/Y | X/Y | X/Y | X/Y | X/Y |
| ... | ... | ... | ... | ... | ... | ... |

## Feature Parity Notes

<document where features are equivalent but named differently>

## Verification Gaps

<features that could not be fully verified>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **No False Differentiation**: Equivalent features under different names identified
- [ ] **[OSS]/[PAID] Tagged**: Every feature has availability annotation
- [ ] **Verification Links**: Every feature claim has source documentation
- [ ] **Cross-Platform Check**: Searched for alternate names for missing features
- [ ] **Version Specificity**: Features tagged with version requirements

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "3": { "status": "completed", "completedAt": "<timestamp>", "featureCount": <n> }
  },
  "currentPhase": 4
}
```

## Next Step

> **Phase 3 Complete**: Feature matrix with `<n>` features compared.
>
> Run `/oss-eval:licensing` to begin Phase 4 (Licensing Deep Dive).
