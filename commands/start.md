---
name: start
description: Initialize and orchestrate a comprehensive 15-phase OSS framework evaluation with built-in safeguards against AI analysis pitfalls.
---

# OSS Evaluation - Main Entry Point

## Purpose

Initialize and orchestrate a comprehensive 15-phase OSS framework evaluation with built-in safeguards against AI analysis pitfalls.

---

## Recommended: Single-Command Automated Run

For a fully automated evaluation, use the orchestrator command instead:

```bash
# Run complete 15-phase evaluation automatically
/oss-eval:run Python web frameworks

# Run with interactive checkpoints
/oss-eval:run JavaScript state management --interactive

# Run only through Phase 6 for initial analysis
/oss-eval:run container orchestration --to-phase 6

# Resume an interrupted evaluation
/oss-eval:run --resume
```

See `/oss-eval:run` for full documentation.

---

## Manual Step-by-Step Mode

Use `/oss-eval:start` if you prefer to run phases manually:

## Arguments

- `$ARGUMENTS`: The technology domain or problem space to evaluate (e.g., "Python web frameworks", "JavaScript state management", "container orchestration")

## Initialization Sequence

### Step 1: Create Evaluation Workspace

Create the `.oss-eval/` directory structure in the current project:

```
.oss-eval/
├── config.json                    # Evaluation configuration
├── progress.md                    # Phase completion tracking
└── [phase directories created as needed]
```

### Step 2: Initialize Configuration

Create `.oss-eval/config.json` with:
```json
{
  "topic": "<topic-space from arguments>",
  "startedAt": "<ISO timestamp>",
  "currentPhase": 1,
  "status": "in_progress",
  "phases": {
    "1": { "name": "Discovery", "status": "pending" },
    "2": { "name": "Candidate Analysis", "status": "pending" },
    "3": { "name": "Feature Matrix", "status": "pending" },
    "4": { "name": "Licensing Deep Dive", "status": "pending" },
    "5": { "name": "Community Health", "status": "pending" },
    "6": { "name": "Risk Assessment", "status": "pending" },
    "7": { "name": "Architecture Analysis", "status": "pending" },
    "8": { "name": "Requirements Alignment", "status": "pending" },
    "9": { "name": "Gap Mitigation", "status": "pending" },
    "10": { "name": "UI Integration", "status": "pending" },
    "11": { "name": "Operational Costs", "status": "pending" },
    "12": { "name": "Developer Experience", "status": "pending" },
    "13": { "name": "Product Context", "status": "pending" },
    "14": { "name": "Hybrid Strategies", "status": "pending" },
    "15": { "name": "Final Validation", "status": "pending" }
  }
}
```

### Step 3: Initialize Progress Tracker

Create `.oss-eval/progress.md`:

```markdown
# OSS Evaluation: <topic-space>

Started: <timestamp>
Status: In Progress

## Phase Progress

| Phase | Name | Status | Command | Completed |
|-------|------|--------|---------|-----------|
| 1 | Discovery | ⏳ Pending | `/oss-eval:discover` | - |
| 2 | Candidate Analysis | ⏳ Pending | `/oss-eval:analyze` | - |
| 3 | Feature Matrix | ⏳ Pending | `/oss-eval:matrix` | - |
| 4 | Licensing Deep Dive | ⏳ Pending | `/oss-eval:licensing` | - |
| 5 | Community Health | ⏳ Pending | `/oss-eval:community` | - |
| 6 | Risk Assessment | ⏳ Pending | `/oss-eval:risk` | - |
| 7 | Architecture Analysis | ⏳ Pending | `/oss-eval:architecture` | - |
| 8 | Requirements Alignment | ⏳ Pending | `/oss-eval:requirements` | - |
| 9 | Gap Mitigation | ⏳ Pending | `/oss-eval:gaps` | - |
| 10 | UI Integration | ⏳ Pending | `/oss-eval:ui` | - |
| 11 | Operational Costs | ⏳ Pending | `/oss-eval:costs` | - |
| 12 | Developer Experience | ⏳ Pending | `/oss-eval:dx` | - |
| 13 | Product Context | ⏳ Pending | `/oss-eval:context` | - |
| 14 | Hybrid Strategies | ⏳ Pending | `/oss-eval:hybrid` | - |
| 15 | Final Validation | ⏳ Pending | `/oss-eval:validate` | - |

## Candidates

(Populated after Phase 1)

## Key Findings

(Populated as evaluation progresses)
```

## Required Skills

Load these skills for bias prevention throughout the evaluation:

1. **@skills/bias-prevention/SKILL.md** - Core AI pitfall prevention rules
2. **@skills/source-validation/SKILL.md** - Web source verification
3. **@skills/feature-verification/SKILL.md** - Cross-platform feature checking

## Phase Navigation

After initialization, guide the user to begin Phase 1:

> **Evaluation workspace initialized for: `<topic-space>`**
>
> Ready to begin the 15-phase evaluation. Run `/oss-eval:discover` to start Phase 1 (Discovery).
>
> **Available Commands:**
> - `/oss-eval:discover` - Phase 1: Web search discovery
> - `/oss-eval:status` - View current progress
> - `/oss-eval:report` - Generate report (available after Phase 6+)

## Resume Existing Evaluation

If `.oss-eval/config.json` already exists:
1. Read current progress from config
2. Show completion status for all phases
3. Suggest next incomplete phase
4. Allow resumption from any incomplete phase

## Bias Prevention Activation

**CRITICAL**: Before any analysis, internalize these safeguards:

1. **Web Verification Required**: Never make claims about features, versions, or capabilities without web search verification
2. **[OSS]/[PAID] Tagging**: All features must be annotated with availability status
3. **Cross-Platform Checking**: Verify features exist under different names across frameworks
4. **Component-Level Breakdown**: Estimate complexity at component level, not holistically
5. **Baseline Consistency**: Establish and maintain comparison criteria from Phase 1
6. **Marketing Translation**: Convert marketing language to technical specifications

## Output

After initialization, provide:
1. Confirmation of workspace creation
2. Summary of the 15-phase methodology
3. Clear next step instruction
4. Reminder of active bias prevention safeguards
