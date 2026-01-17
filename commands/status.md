---
name: status
description: "Display current evaluation progress, phase completion status, and next recommended actions."
---

# OSS Evaluation - Status Check

## Purpose

Display current evaluation progress, phase completion status, and next recommended actions.

## Prerequisites

- Evaluation workspace initialized via `/oss-eval:start`

## Status Display Process

### Step 1: Read Configuration

```javascript
// Read .oss-eval/config.json
const config = readConfig();
const progress = readProgress();
```

### Step 2: Generate Status Report

```markdown
# OSS Evaluation Status

**Topic**: <topic from config>
**Started**: <startedAt from config>
**Current Phase**: <currentPhase from config>
**Overall Status**: <status from config>

---

## Phase Progress

| Phase | Name | Status | Completed |
|-------|------|--------|-----------|
| 1 | Discovery | ✅ Completed | 2025-01-15 |
| 2 | Candidate Analysis | ✅ Completed | 2025-01-15 |
| 3 | Feature Matrix | 🔄 In Progress | - |
| 4 | Licensing Deep Dive | ⏳ Pending | - |
| 5 | Community Health | ⏳ Pending | - |
| 6 | Risk Assessment | ⏳ Pending | - |
| 7 | Architecture Analysis | ⏳ Pending | - |
| 8 | Requirements Alignment | ⏳ Pending | - |
| 9 | Gap Mitigation | ⏳ Pending | - |
| 10 | UI Integration | ⏳ Pending | - |
| 11 | Operational Costs | ⏳ Pending | - |
| 12 | Developer Experience | ⏳ Pending | - |
| 13 | Product Context | ⏳ Pending | - |
| 14 | Hybrid Strategies | ⏳ Pending | - |
| 15 | Final Validation | ⏳ Pending | - |

**Progress**: X/15 phases complete (Y%)

---

## Current Candidates

| Candidate | Status | Phase 6 Risk Score |
|-----------|--------|-------------------|
| <Candidate A> | Active | X.X/5 (if available) |
| <Candidate B> | Active | X.X/5 (if available) |
| <Candidate C> | Eliminated | - |

---

## Key Findings So Far

<summarize key findings from completed phases>

---

## Next Action

**Current Phase**: <name>
**Command**: `<next command>`
**Description**: <what this phase does>

---

## Available Commands

### Continue Evaluation
- `/oss-eval:discover` - Phase 1: Discovery
- `/oss-eval:analyze` - Phase 2: Candidate Analysis
- `/oss-eval:matrix` - Phase 3: Feature Matrix
- `/oss-eval:licensing` - Phase 4: Licensing
- `/oss-eval:community` - Phase 5: Community Health
- `/oss-eval:risk` - Phase 6: Risk Assessment
- `/oss-eval:architecture` - Phase 7: Architecture
- `/oss-eval:requirements` - Phase 8: Requirements
- `/oss-eval:gaps` - Phase 9: Gap Mitigation
- `/oss-eval:ui` - Phase 10: UI Integration
- `/oss-eval:costs` - Phase 11: Costs
- `/oss-eval:dx` - Phase 12: Developer Experience
- `/oss-eval:context` - Phase 13: Product Context
- `/oss-eval:hybrid` - Phase 14: Hybrid Strategies
- `/oss-eval:validate` - Phase 15: Final Validation

### Reports
- `/oss-eval:report --interim` - Generate interim report (after Phase 6)
- `/oss-eval:report` - Generate final report (after Phase 15)

### Utilities
- `/oss-eval:status` - This status view
```

## Status Symbols

| Symbol | Meaning |
|--------|---------|
| ✅ | Completed |
| 🔄 | In Progress |
| ⏳ | Pending |
| ❌ | Blocked |
| ⚠️ | Completed with warnings |

## Error Handling

### No Workspace Found

```markdown
❌ No OSS evaluation workspace found.

Run `/oss-eval:start <topic>` to initialize a new evaluation.

Example:
  /oss-eval:start Python web frameworks
```

### Incomplete Phase Data

```markdown
⚠️ Phase X appears incomplete.

Expected files not found:
- .oss-eval/phase-0X-name/expected-file.md

Run `/oss-eval:<phase-command>` to complete this phase.
```

## Quick Status (Compact View)

For quick reference:

```
OSS Eval: <topic>
Progress: ████████░░░░░░░ 8/15 (53%)
Current: Phase 9 - Gap Mitigation
Next: /oss-eval:gaps
```
