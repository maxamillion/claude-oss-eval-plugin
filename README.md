# OSS Evaluation Claude Plugin

A comprehensive Claude Code plugin implementing a 15-phase methodology for evaluating open source software frameworks with built-in safeguards against AI analysis pitfalls.

This plugin is a work in progress and is subject to change.

The methodology used here to evaluate OSS frameworks was created by [@jwforres](https://github.com/jwforres) and [@n1hility](https://github.com/n1hility), and adapted here as a Claude Code Plugin.

## Overview

This plugin provides a structured, bias-resistant approach to evaluating OSS frameworks for adoption decisions. It addresses common AI analysis problems including:

- **Stale Knowledge**: Forces web verification of all metrics
- **False Differentiation**: Systematic cross-platform feature checking
- **OSS/Commercial Conflation**: Mandatory `[OSS]`/`[PAID]` annotations
- **Complexity Overestimation**: Component-level effort breakdown
- **Baseline Drift**: Locked comparison criteria from Phase 1
- **Marketing Language**: Technical translation requirements

## Installation

### Option 1: Plugin Marketplace (Recommended)

Install directly within Claude Code using the plugin system:

```bash
# Add the marketplace (one time)
/plugin marketplace add maxamillion/claude-oss-eval-plugin

# Install the plugin
/plugin install oss-eval
```

The plugin will be available immediately. Commands are namespaced as `/oss-eval:command`.

### Option 2: Local Development

For testing or contributing to the plugin:

```bash
# Clone the repository
git clone https://github.com/maxamillion/claude-oss-eval-plugin.git

# Run Claude Code with the plugin directory
claude --plugin-dir /path/to/claude-oss-eval-plugin
```

### Option 3: Project Scope Installation

Share the plugin with your team via git:

```bash
# Add marketplace and install with project scope
/plugin marketplace add maxamillion/claude-oss-eval-plugin
/plugin install oss-eval --scope project
```

This adds the plugin configuration to your project's `.claude/` directory.

### Plugin Management

```bash
# List installed plugins
/plugin list

# Update to latest version
/plugin update oss-eval

# Disable temporarily
/plugin disable oss-eval

# Re-enable
/plugin enable oss-eval

# Uninstall
/plugin uninstall oss-eval
```

## Quick Start

### Recommended: Single Command (Automated)

Run a complete 15-phase evaluation with a single command:

```bash
# Full automated evaluation
/oss-eval:run Python web frameworks

# With interactive checkpoints for user decisions
/oss-eval:run JavaScript state management --interactive

# Stop after Phase 6 for interim review
/oss-eval:run container orchestration --to-phase 6

# Resume an interrupted evaluation
/oss-eval:run --resume
```

### Alternative: Manual Step-by-Step

For more control, run phases individually:

```bash
# Initialize a new evaluation
/oss-eval:start Python web frameworks

# Check current progress
/oss-eval:status

# Work through phases sequentially
/oss-eval:discover     # Phase 1
/oss-eval:analyze      # Phase 2
/oss-eval:matrix       # Phase 3
# ... continue through all 15 phases

# Generate reports
/oss-eval:report --interim  # After Phase 6
/oss-eval:report            # After Phase 15
```

## The 15-Phase Methodology

### Discovery & Analysis (Phases 1-6)

| Phase | Command | Purpose |
|-------|---------|---------|
| 1 | `/oss-eval:discover` | Web search discovery of candidates |
| 2 | `/oss-eval:analyze` | Detailed candidate analysis |
| 3 | `/oss-eval:matrix` | Feature comparison matrix |
| 4 | `/oss-eval:licensing` | License and dependency analysis |
| 5 | `/oss-eval:community` | Community health assessment |
| 6 | `/oss-eval:risk` | Quantified risk scoring |

**Milestone**: After Phase 6, generate interim report with `/oss-eval:report --interim`

### Technical Deep-Dive (Phases 7-9)

| Phase | Command | Purpose |
|-------|---------|---------|
| 7 | `/oss-eval:architecture` | Code-level architecture analysis |
| 8 | `/oss-eval:requirements` | Requirements alignment mapping |
| 9 | `/oss-eval:gaps` | Gap mitigation strategy |

### Integration Analysis (Phases 10-12)

| Phase | Command | Purpose |
|-------|---------|---------|
| 10 | `/oss-eval:ui` | UI integration assessment |
| 11 | `/oss-eval:costs` | Total cost of ownership |
| 12 | `/oss-eval:dx` | Developer experience evaluation |

### Validation (Phases 13-15)

| Phase | Command | Purpose |
|-------|---------|---------|
| 13 | `/oss-eval:context` | Product context integration |
| 14 | `/oss-eval:hybrid` | Hybrid strategy exploration |
| 15 | `/oss-eval:validate` | Adversarial review & validation |

**Final**: Generate complete report with `/oss-eval:report`

## Key Features

### Bias Prevention Skills

Three core skills loaded automatically during evaluation:

1. **`bias-prevention`**: 12 pitfall prevention rules
2. **`feature-verification`**: Cross-platform capability checking
3. **`source-validation`**: Web source credibility verification

### Isolated Adversarial Review

Phase 15 uses an isolated sub-agent for unbiased review:

```yaml
agent: general-purpose
context: fork  # No access to prior evaluation context
```

This ensures the recommendation is stress-tested by a fresh perspective.

### Required Annotations

All features in the matrix must include availability tags:

- `[OSS]` - Open source availability
- `[PAID]` - Requires paid/enterprise tier
- `[PLUGIN]` - Requires additional plugin
- `[COMMUNITY]` - Community-maintained only
- `[DEPRECATED]` - Being phased out
- `[BETA]` - Not production-ready

### Evidence Requirements

Every claim requires verification:

```markdown
<!-- Required format -->
FastAPI has 78,234 GitHub stars [Verified: 2025-01-16 via github.com]
```

## Directory Structure

```
claude-oss-eval-plugin/
├── .claude-plugin/
│   ├── plugin.json           # Plugin manifest
│   └── marketplace.json      # Marketplace configuration
├── commands/
│   ├── oss-eval.md           # Main entry point (manual mode)
│   ├── oss-run.md            # Automated orchestrator (recommended)
│   ├── oss-discover.md       # Phase 1
│   ├── oss-analyze.md        # Phase 2
│   ├── oss-matrix.md         # Phase 3
│   ├── oss-licensing.md      # Phase 4
│   ├── oss-community.md      # Phase 5
│   ├── oss-risk.md           # Phase 6
│   ├── oss-architecture.md   # Phase 7
│   ├── oss-requirements.md   # Phase 8
│   ├── oss-gaps.md           # Phase 9
│   ├── oss-ui.md             # Phase 10
│   ├── oss-costs.md          # Phase 11
│   ├── oss-dx.md             # Phase 12
│   ├── oss-context.md        # Phase 13
│   ├── oss-hybrid.md         # Phase 14
│   ├── oss-validate.md       # Phase 15
│   ├── oss-report.md         # Report generation
│   └── oss-status.md         # Status checking
├── skills/
│   ├── bias-prevention/
│   │   └── SKILL.md          # 12 pitfall prevention rules
│   ├── feature-verification/
│   │   └── SKILL.md          # Cross-platform checking
│   └── source-validation/
│       └── SKILL.md          # Source credibility rules
├── agents/
│   ├── adversarial-reviewer.md  # Isolated validation agent
│   └── discovery-agent.md       # Web search discovery agent
├── templates/
│   ├── feature-matrix.md     # Feature comparison template
│   ├── risk-assessment.md    # Risk scoring template
│   └── final-report.md       # Executive summary template
└── README.md
```

## Evaluation Workspace

When you start an evaluation, a `.oss-eval/` directory is created:

```
.oss-eval/
├── config.json                # Evaluation configuration
├── progress.md                # Phase completion tracking
├── baseline-criteria.md       # Locked comparison criteria
├── phase-01-discovery/
│   ├── candidates.md
│   └── sources.md
├── phase-02-analysis/
│   ├── candidate-a.md
│   └── summary.md
├── phase-03-features/
│   └── feature-matrix.md
├── phase-04-licensing/
│   └── licensing-analysis.md
├── phase-05-community/
│   └── community-health.md
├── phase-06-risk/
│   └── risk-assessment.md
├── phase-07-architecture/
│   ├── candidate-a/
│   │   └── code-analysis.md
│   └── candidate-b/
├── phase-08-requirements/
│   └── requirements-alignment.md
├── phase-09-gaps/
│   └── gap-mitigation.md
├── phase-10-ui/
│   └── ui-integration.md
├── phase-11-costs/
│   └── operational-costs.md
├── phase-12-dx/
│   └── developer-experience.md
├── phase-13-context/
│   └── product-context.md
├── phase-14-hybrid/
│   └── hybrid-strategies.md
├── phase-15-validation/
│   ├── adversarial-review.md
│   ├── dissenting-views.md
│   └── final-validation.md
├── interim-report.md          # Generated after Phase 6
└── final-report.md            # Generated after Phase 15
```

## The 12 AI Analysis Pitfalls

This plugin specifically addresses these common issues:

| # | Pitfall | Prevention |
|---|---------|------------|
| 1 | Stale/Outdated Knowledge | WebSearch verification required |
| 2 | False Feature Differentiation | Cross-platform terminology mapping |
| 3 | OSS/Commercial Conflation | Mandatory [OSS]/[PAID] tags |
| 4 | Complexity Overestimation | Component-level breakdown |
| 5 | Baseline Drift | Locked criteria from Phase 1 |
| 6 | Marketing Language | Technical translation required |
| 7 | Popularity Bias | Technical merit over stars |
| 8 | Recency Bias | Full history consideration |
| 9 | Confirmation Bias | Adversarial review process |
| 10 | Halo Effect | Independent dimension scoring |
| 11 | Anchoring Bias | Consistent checklists |
| 12 | Sunk Cost Bias | "None suitable" is valid |

## Example Evaluation

### Automated (Recommended)

```bash
# Complete evaluation with a single command
/oss-eval:run Python web frameworks

# Output:
# ═══════════════════════════════════════════════════════════════
#   OSS EVALUATION: Python web frameworks
#   Mode: Automated Full Run
#   Phases: 1-15
# ═══════════════════════════════════════════════════════════════
#
# Starting comprehensive 15-phase evaluation...
# [Phases execute automatically with progress updates]
#
# ═══════════════════════════════════════════════════════════════
#   OSS EVALUATION COMPLETE
# ═══════════════════════════════════════════════════════════════
# RECOMMENDATION: FastAPI
# Confidence: 87%
```

### With Interactive Checkpoints

```bash
# Pause at key decision points
/oss-eval:run Python web frameworks --interactive

# Pauses after Phase 6 to confirm candidate selection
# Pauses after Phase 14 to confirm recommendation before adversarial review
```

### Manual Step-by-Step

```bash
# Initialize evaluation
/oss-eval:start Python web frameworks

# Run phases individually
/oss-eval:discover     # Phase 1
/oss-eval:analyze      # Phase 2
/oss-eval:matrix       # Phase 3
# ... continue through all 15 phases

# Check progress anytime
/oss-eval:status

# Generate reports
/oss-eval:report --interim  # After Phase 6
/oss-eval:report            # After Phase 15
```

## Best Practices

1. **Complete phases sequentially** - Each phase builds on previous findings
2. **Don't skip the adversarial review** - Phase 15 catches blind spots
3. **Use web search for all metrics** - Never trust cached knowledge for numbers
4. **Document rejected candidates** - Explain why alternatives weren't chosen
5. **Preserve dissenting views** - Even if not adopted, document them
6. **Maintain baseline criteria** - Don't shift goalposts during evaluation

## Contributing

Contributions welcome! Please ensure any additions:

- Follow the bias prevention principles
- Include evidence requirements
- Document clearly with examples
- Add appropriate checkpoints

## License

MIT License - See LICENSE file for details.
