# Feature Matrix Template

## Purpose

Template for creating comprehensive, bias-resistant feature comparison matrices with mandatory [OSS]/[PAID] annotations and verification links.

## Template Structure

```markdown
# Feature Comparison Matrix: <Topic>

Generated: <timestamp>
Candidates: <list>
Verification Date: <date>

---

## Legend

### Availability Symbols
| Symbol | Meaning | Description |
|--------|---------|-------------|
| ✅ | Full support | Feature fully available and production-ready |
| ⚠️ | Partial support | Feature available with limitations |
| ❌ | Not available | Feature missing (verified) |
| 🔄 | In development | Feature planned or in progress |
| ❓ | Unknown | Unable to verify status |

### Availability Tags (REQUIRED)
| Tag | Meaning | Description |
|-----|---------|-------------|
| [OSS] | Open Source | Available in open source version |
| [PAID] | Paid/Enterprise | Requires paid license |
| [PLUGIN] | Plugin Required | Needs additional package |
| [COMMUNITY] | Community | Community-maintained, not official |
| [DEPRECATED] | Deprecated | Being phased out |
| [BETA] | Beta | Not production-ready |

### Naming Variations
When features exist under different names, use footnotes:
- `✅ [OSS] [^1]` where `[^1]: Called "alternative-name" in this framework`

---

## Category 1: Core Functionality

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <Feature 1> | ✅ [OSS] | ✅ [OSS] [^1] | ⚠️ [PLUGIN] | [A](<url>), [B](<url>), [C](<url>) |
| <Feature 2> | ✅ [OSS] | ❌ | ✅ [PAID] | [A](<url>), [C](<url>) |
| <Feature 3> | ⚠️ [COMMUNITY] | ✅ [OSS] | ✅ [OSS] | [A](<url>), [B](<url>), [C](<url>) |

[^1]: Feature called "alternate-name" in Candidate B

### Category 1 Summary
| Candidate | ✅ Full | ⚠️ Partial | ❌ Missing | Score |
|-----------|---------|------------|-----------|-------|
| <A> | X | Y | Z | X/N |
| <B> | X | Y | Z | X/N |
| <C> | X | Y | Z | X/N |

---

## Category 2: Integration Capabilities

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <Integration 1> | ✅ [OSS] | ✅ [OSS] | ⚠️ [PLUGIN] | [...] |
| <Integration 2> | ❌ | ✅ [PAID] | ✅ [OSS] | [...] |

### Category 2 Summary
| Candidate | ✅ Full | ⚠️ Partial | ❌ Missing | Score |
|-----------|---------|------------|-----------|-------|
| ... | ... | ... | ... | ... |

---

## Category 3: Developer Experience

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <DX Feature 1> | ✅ [OSS] | ✅ [OSS] | ✅ [OSS] | [...] |
| <DX Feature 2> | ⚠️ [OSS] | ✅ [OSS] | ❌ | [...] |

### Category 3 Summary
| Candidate | ✅ Full | ⚠️ Partial | ❌ Missing | Score |
|-----------|---------|------------|-----------|-------|
| ... | ... | ... | ... | ... |

---

## Category 4: Operations & Monitoring

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <Ops Feature 1> | ✅ [OSS] | ⚠️ [PAID] | ✅ [OSS] | [...] |
| <Ops Feature 2> | ✅ [PLUGIN] | ✅ [OSS] | ❌ | [...] |

### Category 4 Summary
| Candidate | ✅ Full | ⚠️ Partial | ❌ Missing | Score |
|-----------|---------|------------|-----------|-------|
| ... | ... | ... | ... | ... |

---

## Category 5: Security

| Feature | <Candidate A> | <Candidate B> | <Candidate C> | Verification |
|---------|---------------|---------------|---------------|--------------|
| <Security 1> | ✅ [OSS] | ✅ [OSS] | ⚠️ [PAID] | [...] |
| <Security 2> | ✅ [OSS] | ❌ | ✅ [OSS] | [...] |

### Category 5 Summary
| Candidate | ✅ Full | ⚠️ Partial | ❌ Missing | Score |
|-----------|---------|------------|-----------|-------|
| ... | ... | ... | ... | ... |

---

## Overall Summary

### Feature Coverage

| Category | Weight | <Candidate A> | <Candidate B> | <Candidate C> |
|----------|--------|---------------|---------------|---------------|
| Core Functionality | 30% | X/Y | X/Y | X/Y |
| Integration | 20% | X/Y | X/Y | X/Y |
| Developer Experience | 20% | X/Y | X/Y | X/Y |
| Operations | 15% | X/Y | X/Y | X/Y |
| Security | 15% | X/Y | X/Y | X/Y |
| **Weighted Total** | 100% | **X.X** | **X.X** | **X.X** |

### OSS vs Paid Breakdown

| Candidate | ✅ [OSS] | ✅ [PAID] | ⚠️ Any | ❌ Missing |
|-----------|----------|-----------|--------|-----------|
| <A> | X | Y | Z | W |
| <B> | X | Y | Z | W |
| <C> | X | Y | Z | W |

### Feature Parity Notes

Document features that are equivalent but named differently:

| Concept | <Candidate A> | <Candidate B> | <Candidate C> |
|---------|---------------|---------------|---------------|
| <concept> | `name_a` | `name_b` | `name_c` |
| <concept> | `approach_a` | `approach_b` | N/A |

---

## Verification Log

| Feature | Verification Attempts | Result | Date |
|---------|----------------------|--------|------|
| <feature> | 2 (docs + repo) | Confirmed present | <date> |
| <feature> | 3 (docs + repo + community) | Confirmed missing | <date> |

---

## Footnotes

[^1]: <explanation>
[^2]: <explanation>
```

## Usage Instructions

### Required Steps

1. **Fill category headers** based on baseline criteria from Phase 1
2. **For each feature**:
   - Assess availability in each candidate
   - Add [OSS]/[PAID]/etc. tag (REQUIRED)
   - Add verification link (REQUIRED)
3. **For each "missing" feature**:
   - Use @skills/feature-verification/SKILL.md to verify
   - Search for alternative names
   - Document verification attempts
4. **Complete summaries** for each category
5. **Calculate weighted totals** based on requirement priorities

### Bias Prevention Checks

Before finalizing matrix:

- [ ] Every feature has availability tag
- [ ] Every feature has verification link
- [ ] "Missing" features verified with multiple searches
- [ ] Alternative names documented
- [ ] Same depth of analysis for all candidates
