---
name: run
description: "Execute a complete 15-phase OSS framework evaluation automatically with a single command. Runs all phases sequentially with progress tracking."
---

# OSS Evaluation - Full Automated Run

## Purpose

Execute a complete 15-phase OSS framework evaluation automatically with a single command. This orchestrator runs all phases sequentially, tracks progress, and generates reports at appropriate milestones.

## Arguments

- `$ARGUMENTS`: The technology domain or problem space to evaluate (e.g., "Python web frameworks", "JavaScript state management")
- `--resume`: Continue from the last incomplete phase (reads state from `.oss-eval/config.json`)
- `--to-phase N`: Stop after completing phase N (e.g., `--to-phase 6` for interim analysis)
- `--interactive`: Pause for user input at key decision points (after Phase 6 and Phase 14)

## Quick Start

```bash
# Full automated run
/oss-eval:run Python web frameworks

# Resume interrupted evaluation
/oss-eval:run --resume

# Stop after initial analysis for review
/oss-eval:run JavaScript testing frameworks --to-phase 6

# Interactive mode with checkpoints
/oss-eval:run container orchestration --interactive
```

## Required Skills

Load these skills at the start for bias prevention throughout:

1. **@skills/bias-prevention/SKILL.md** - Core AI pitfall prevention rules
2. **@skills/source-validation/SKILL.md** - Web source verification
3. **@skills/feature-verification/SKILL.md** - Cross-platform feature checking

---

# ORCHESTRATION WORKFLOW

## Initialization

### Step 1: Parse Arguments and Check State

If `--resume` flag is present:
1. Read `.oss-eval/config.json`
2. Find last completed phase
3. Resume from next incomplete phase
4. Display: "Resuming evaluation from Phase X"

Otherwise:
1. Extract topic from arguments
2. Create fresh workspace

### Step 2: Create Evaluation Workspace

Create `.oss-eval/` directory structure:

```
.oss-eval/
├── config.json
├── progress.md
├── baseline-criteria.md
└── [phase directories created as each phase completes]
```

### Step 3: Initialize Configuration

Create `.oss-eval/config.json`:
```json
{
  "topic": "<topic from arguments>",
  "startedAt": "<ISO timestamp>",
  "currentPhase": 1,
  "status": "in_progress",
  "runMode": "automated",
  "flags": {
    "interactive": false,
    "toPhase": 15
  },
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

### Step 4: Display Start Message

```
═══════════════════════════════════════════════════════════════
  OSS EVALUATION: <topic>
  Mode: Automated Full Run
  Phases: 1-15 (or 1-N if --to-phase specified)
═══════════════════════════════════════════════════════════════

Starting comprehensive 15-phase evaluation...
Bias prevention safeguards: ACTIVE
```

---

# PHASE EXECUTION

Execute each phase in sequence. After each phase:
1. Save outputs to phase directory
2. Update config.json with completion status
3. Check if `--to-phase` limit reached
4. Check if `--interactive` checkpoint reached
5. Continue to next phase or stop as appropriate

---

## PHASE 1: Discovery

**Objective**: Identify candidate frameworks via comprehensive web search.

### Actions

1. **Multi-Source Search**: Use WebSearch to query:
   - GitHub: `"<topic> framework" site:github.com`
   - Awesome Lists: `"awesome <topic>" curated list`
   - Comparisons: `"<topic> comparison 2024 2025"`
   - Discussions: `"<topic> recommendations" site:reddit.com OR site:news.ycombinator.com`
   - Package Registries: npm, PyPI, crates.io as appropriate

2. **Collect Initial Metrics** for each candidate:
   - Repository URL
   - Package URL
   - Stars/Downloads (VERIFY via web search)
   - License
   - Last release date

3. **Apply Discovery Filters** - Remove candidates that:
   - No updates in >2 years (unless stable/mature)
   - <100 GitHub stars (unless niche)
   - Lack documentation
   - Incompatible licenses

4. **Establish Baseline Criteria**:
   - Define functional requirements
   - Define non-functional requirements
   - List must-have features
   - List nice-to-have features
   - Document dealbreakers

### Outputs

Create `.oss-eval/phase-01-discovery/`:
- `candidates.md` - Discovered candidates with metrics
- `sources.md` - Sources consulted with credibility notes

Create `.oss-eval/baseline-criteria.md` with locked comparison criteria.

### Completion Criteria

- [ ] At least 3 viable candidates identified
- [ ] All metrics verified via web search
- [ ] Baseline criteria documented and locked

### Update Config

```json
{ "phases": { "1": { "status": "completed", "completedAt": "<timestamp>", "candidateCount": N } }, "currentPhase": 2 }
```

---

## PHASE 2: Candidate Analysis

**Objective**: Deep-dive analysis of each candidate's capabilities and fit.

### Actions

1. **Per-Candidate Analysis** using WebSearch:
   - Official documentation review
   - GitHub/repository analysis (contributors, issues, PRs)
   - Adoption indicators (notable users, case studies)

2. **Structured Assessment** for each candidate:
   - Core capabilities with verification
   - Baseline criteria alignment
   - Strengths with sources
   - Weaknesses with sources
   - Red flags identified

3. **Comparative Summary**:
   - Rank candidates by initial fit
   - Document eliminations with reasons
   - Identify focus areas for Phase 3

### Outputs

Create `.oss-eval/phase-02-analysis/`:
- `<candidate-name>.md` - Per-candidate analysis
- `summary.md` - Comparative summary

### Completion Criteria

- [ ] All candidates analyzed with same criteria
- [ ] Evidence-based claims with sources
- [ ] Clear proceed/eliminate decisions

### Update Config

```json
{ "phases": { "2": { "status": "completed", "completedAt": "<timestamp>", "proceedingCount": N } }, "currentPhase": 3 }
```

---

## PHASE 3: Feature Matrix Development

**Objective**: Build comprehensive feature comparison with [OSS]/[PAID] annotations.

### Actions

1. **Define Feature Categories** based on baseline:
   - Core Functionality
   - Integration Capabilities
   - Developer Experience
   - Operations & Monitoring
   - Security

2. **Feature Verification Protocol** for each feature:
   - Check official documentation
   - Verify in source code if unclear
   - Check issue tracker for limitations
   - Cross-platform name checking (same feature, different names)

3. **Build Annotated Matrix**:
   - Every feature tagged: `[OSS]`, `[PAID]`, `[PLUGIN]`, `[COMMUNITY]`, `[DEPRECATED]`, `[BETA]`
   - Status symbols: ✅ Full, ⚠️ Partial, ❌ Not available
   - Verification links for each claim

### Outputs

Create `.oss-eval/phase-03-features/`:
- `feature-matrix.md` - Complete annotated matrix with scores

### Completion Criteria

- [ ] All features have [OSS]/[PAID] annotations
- [ ] All claims have verification links
- [ ] Cross-platform name equivalents identified

### Update Config

```json
{ "phases": { "3": { "status": "completed", "completedAt": "<timestamp>", "featureCount": N } }, "currentPhase": 4 }
```

---

## PHASE 4: Licensing Deep Dive

**Objective**: Comprehensive licensing analysis including dependencies.

### Actions

1. **Primary License Identification**:
   - Verify license from repository (LICENSE file)
   - Classify: Permissive/Copyleft/Weak Copyleft/Commercial
   - Note any version-specific changes

2. **Dependency License Audit**:
   - Scan direct dependencies
   - Identify high-risk transitive dependencies
   - Document compatibility concerns

3. **Commercial Use Analysis**:
   - Document permitted uses
   - Document required actions (attribution, disclosure)
   - Document restrictions

4. **Commercial Licensing Options**:
   - Document dual-licensing if available
   - Enterprise tier features and pricing

### Outputs

Create `.oss-eval/phase-04-licensing/`:
- `licensing-analysis.md` - Complete licensing report with compatibility matrix

### Completion Criteria

- [ ] All primary licenses verified from repositories
- [ ] Dependency audit completed
- [ ] Commercial use implications documented

### Update Config

```json
{ "phases": { "4": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 5 }
```

---

## PHASE 5: Community Health Check

**Objective**: Assess community sustainability and responsiveness.

### Actions

1. **Contributor Analysis**:
   - Core maintainer count (bus factor)
   - Contributor diversity (single company vs. diverse)
   - New contributor rate

2. **Issue/PR Metrics** (verify via current web search):
   - Open issues count and trend
   - Issue close rate
   - PR merge rate and review time
   - Stale issues percentage

3. **Communication Channels**:
   - Assess activity levels (GitHub Discussions, Discord, Slack, Stack Overflow)
   - Maintainer engagement quality

4. **Governance & Sustainability**:
   - Governance model (BDFL/Committee/Foundation/Corporate)
   - Funding model and major sponsors
   - Corporate backing and risk assessment

5. **Release Cadence**:
   - Release frequency pattern
   - LTS policy
   - Migration guide availability

### Outputs

Create `.oss-eval/phase-05-community/`:
- `community-health.md` - Health scorecard and detailed analysis

### Completion Criteria

- [ ] All metrics from current web search
- [ ] Consistent metrics across candidates
- [ ] Sustainability risks identified

### Update Config

```json
{ "phases": { "5": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 6 }
```

---

## PHASE 6: Risk Assessment

**Objective**: Synthesize Phases 1-5 into quantified risk scores.

### Actions

1. **Score Each Candidate** across risk categories (1-5 scale):
   - Technical Risk (25%)
   - Adoption Risk (20%)
   - Operational Risk (20%)
   - Business Risk (20%)
   - Community Risk (15%)

2. **Document Evidence** for each score from prior phases

3. **Identify Blockers and Concerns**:
   - Critical blockers
   - Significant concerns with mitigations

4. **Generate Recommendations**:
   - Candidates to proceed to deep-dive
   - Candidates to eliminate

### Outputs

Create `.oss-eval/phase-06-risk/`:
- `risk-assessment.md` - Risk matrix and recommendations

### Completion Criteria

- [ ] Consistent scoring rubric applied
- [ ] Every score has evidence from prior phases
- [ ] Clear proceed/eliminate decisions

### Update Config

```json
{ "phases": { "6": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 7 }
```

---

## CHECKPOINT: After Phase 6

### Generate Interim Report

Create `.oss-eval/interim-report.md` summarizing Phases 1-6.

### Interactive Mode Check

If `--interactive` flag is set:
```
═══════════════════════════════════════════════════════════════
  PHASE 6 COMPLETE - DECISION CHECKPOINT
═══════════════════════════════════════════════════════════════

Phases 1-6 (Discovery & Analysis) complete.
Interim report: .oss-eval/interim-report.md

Candidates proceeding to deep-dive:
  1. <Candidate A> - Risk Score: X.X/5
  2. <Candidate B> - Risk Score: X.X/5

Continue with Phases 7-15 for selected candidates?
```

Wait for user confirmation before proceeding.

### To-Phase Check

If `--to-phase 6` specified, stop here:
```
═══════════════════════════════════════════════════════════════
  EVALUATION PAUSED AT PHASE 6
═══════════════════════════════════════════════════════════════

Completed Phases 1-6 as requested.
Interim report: .oss-eval/interim-report.md

To continue: /oss-eval:run --resume
Or manually: /oss-eval:architecture
```

---

## PHASE 7: Architecture Analysis

**Objective**: Deep technical analysis of candidate architectures.

### Actions

1. **Architectural Pattern Analysis**:
   - Core architecture pattern (MVC, Hexagonal, etc.)
   - Modularity and extension points
   - Data flow patterns

2. **Code Quality Assessment**:
   - Test coverage
   - Code organization
   - Documentation quality
   - Static analysis tools used

3. **Enterprise Readiness**:
   - Scalability (horizontal, vertical, clustering)
   - High availability (failover, session management)
   - Security (auth, authorization, OWASP)
   - Observability (logging, metrics, tracing)

4. **Performance Characteristics**:
   - Benchmark data (verify via web search)
   - Known performance issues

### Sub-Agent Strategy

Use isolated sub-agents (`context: fork`) for unbiased code analysis of each candidate.

### Outputs

Create `.oss-eval/phase-07-architecture/<candidate>/`:
- `code-analysis.md` - Per-candidate architecture report

### Completion Criteria

- [ ] Isolated agents used for unbiased analysis
- [ ] Enterprise readiness assessed
- [ ] Performance data verified

### Update Config

```json
{ "phases": { "7": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 8 }
```

---

## PHASE 8: Requirements Alignment

**Objective**: Map capabilities against specific product requirements.

### Actions

1. **Categorize Requirements**:
   - P0 (Critical/Must Have) - 50% weight
   - P1 (Important/Should Have) - 30% weight
   - P2 (Desired/Nice to Have) - 10% weight
   - Non-Functional - 10% weight

2. **Capability Mapping** per candidate:
   - Status: Met/Partial/Not Met
   - Evidence and documentation links
   - Gap identification

3. **Gap Analysis**:
   - Document each gap
   - Assess impact
   - Identify initial mitigation options

4. **Calculate Fit Scores** based on weighted requirements

### Outputs

Create `.oss-eval/phase-08-requirements/`:
- `requirements-alignment.md` - Alignment matrix and fit scores

### Completion Criteria

- [ ] Original baseline used (not adjusted)
- [ ] Evidence-based status for each requirement
- [ ] Gaps documented objectively

### Update Config

```json
{ "phases": { "8": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 9 }
```

---

## PHASE 9: Gap Mitigation Strategy

**Objective**: Develop comprehensive mitigation plans for identified gaps.

### Actions

1. **Prioritize Gaps**:
   - Calculate priority score: Impact × Urgency × Complexity
   - Tier 1 (>0.6): Address immediately
   - Tier 2 (0.3-0.6): Address in initial implementation
   - Tier 3 (<0.3): Address post-launch

2. **Develop Mitigation Strategies** for each gap:
   - Option 1: Custom Development (effort, risk, pros/cons)
   - Option 2: Community Plugin (availability, maturity)
   - Option 3: Architectural Workaround (trade-offs)
   - Option 4: Accept Gap (justification)
   - Recommended approach with rationale

3. **Aggregate Effort** per candidate:
   - Total effort in days
   - Risk profile (low/medium/high effort)
   - Implementation timeline

4. **Comparative Analysis**:
   - Effort comparison
   - Risk comparison
   - TCO impact

### Outputs

Create `.oss-eval/phase-09-gaps/`:
- `gap-mitigation.md` - Prioritized gaps with mitigation strategies

### Completion Criteria

- [ ] Realistic effort estimates (component-level)
- [ ] Multiple options considered
- [ ] Clear recommendations with rationale

### Update Config

```json
{ "phases": { "9": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 10 }
```

---

## PHASE 10: UI Integration Analysis

**Objective**: Assess integration with existing/planned user interfaces.

### Actions

1. **Document UI Context**:
   - Current/planned stack (React, Vue, etc.)
   - Styling approach
   - Build tools
   - Accessibility requirements

2. **Per-Candidate UI Assessment**:
   - Framework support quality
   - Component integration options
   - Styling integration
   - Build tool compatibility

3. **Accessibility Assessment**:
   - Built-in accessibility features
   - WCAG compliance level
   - Accessibility documentation

4. **Real-time & Interactive Features**:
   - WebSocket/SSE support
   - Data fetching integration
   - Form integration

### Outputs

Create `.oss-eval/phase-10-ui/`:
- `ui-integration.md` - UI integration comparison and scores

### Completion Criteria

- [ ] Current capabilities verified
- [ ] Accessibility assessed objectively
- [ ] Integration effort estimated

### Update Config

```json
{ "phases": { "10": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 11 }
```

---

## PHASE 11: Operational Cost Quantification

**Objective**: Calculate total cost of ownership (TCO).

### Actions

1. **Define Operational Context**:
   - Scale parameters (users, transactions, data)
   - Infrastructure context (cloud provider, regions)
   - Team context (size, skills)
   - Time horizon (typically 3 years)

2. **Calculate Direct Costs**:
   - Licensing costs (verify pricing via web)
   - Infrastructure costs
   - Third-party service costs

3. **Calculate Implementation Costs**:
   - Initial development
   - Training
   - Migration (if applicable)

4. **Calculate Ongoing Costs**:
   - Maintenance (upgrades, patches)
   - Operations (monitoring, incidents)
   - Support

5. **Estimate Hidden/Risk Costs**:
   - Technical debt
   - Risk-adjusted costs
   - Opportunity costs

6. **TCO Comparison** across candidates

### Outputs

Create `.oss-eval/phase-11-costs/`:
- `operational-costs.md` - TCO analysis and comparison

### Completion Criteria

- [ ] Pricing verified from current sources
- [ ] All cost categories included
- [ ] Consistent methodology across candidates

### Update Config

```json
{ "phases": { "11": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 12 }
```

---

## PHASE 12: Developer Experience Evaluation

**Objective**: Evaluate DX including documentation, tooling, and learning curve.

### Actions

1. **Assess Team Context**:
   - Current skills
   - Learning preferences
   - Development environment

2. **Documentation Assessment**:
   - Quality (completeness, accuracy, organization)
   - Types available (getting started, API, tutorials)
   - Learning resources (courses, books, videos)

3. **Tooling Assessment**:
   - CLI tools
   - IDE support
   - Debugging capabilities
   - Testing tools

4. **Development Workflow**:
   - Setup time
   - Hot reload support
   - Build times
   - Configuration complexity

5. **Community Support**:
   - Help channels and response times
   - Community content quality

6. **Learning Curve**:
   - Time to productivity milestones
   - Team fit assessment

### Outputs

Create `.oss-eval/phase-12-dx/`:
- `developer-experience.md` - DX comparison and team fit analysis

### Completion Criteria

- [ ] DX assessed against actual team
- [ ] Evidence-based assessments
- [ ] Learning curve realistic

### Update Config

```json
{ "phases": { "12": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 13 }
```

---

## PHASE 13: Product Context Introduction

**Objective**: Ground evaluation in specific product context and constraints.

### Actions

1. **Gather Product Context**:
   - Product overview (type, stage, users)
   - Business context (model, competition, strategic importance)
   - Technical context (existing stack, integrations)
   - Team context (size, timeline, budget, risk tolerance)

2. **Map Constraints**:
   - Hard constraints (non-negotiable)
   - Soft constraints (preferences)
   - Constraint conflicts and resolutions

3. **Contextualize Candidates**:
   - Re-evaluate against product constraints
   - Assess timeline feasibility
   - Assess budget feasibility

4. **Stakeholder Alignment**:
   - Engineering perspective
   - Product perspective
   - Business perspective
   - Alignment assessment and conflict resolution

5. **Context-Adjusted Rankings**:
   - Compare pre/post context rankings
   - Document ranking changes with rationale

### Outputs

Create `.oss-eval/phase-13-context/`:
- `product-context.md` - Context report and adjusted rankings

### Completion Criteria

- [ ] Context not retrofitted to favor candidate
- [ ] Genuine constraints documented
- [ ] Ranking changes explained

### Update Config

```json
{ "phases": { "13": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 14 }
```

---

## PHASE 14: Hybrid Strategy Exploration

**Objective**: Explore combining candidates or using different solutions for different use cases.

### Actions

1. **Identify Hybrid Opportunities**:
   - Complementary strengths between candidates
   - Gap coverage across candidates
   - Use case segmentation

2. **Define Architecture Options**:
   - Option 1: Parallel Deployment
   - Option 2: Primary + Plugin
   - Option 3: Migration Path
   - Option 4: Facade Abstraction

3. **Cost-Benefit Analysis**:
   - Compare single vs. hybrid approaches
   - Determine when hybrid makes sense
   - Document recommendation

4. **Implementation Planning** (if hybrid viable):
   - Integration design
   - Implementation phases
   - Risk mitigation

### Outputs

Create `.oss-eval/phase-14-hybrid/`:
- `hybrid-strategies.md` - Hybrid exploration and recommendation

### Completion Criteria

- [ ] Hybrid genuinely evaluated
- [ ] Complexity honestly assessed
- [ ] Clear recommendation with rationale

### Update Config

```json
{ "phases": { "14": { "status": "completed", "completedAt": "<timestamp>" } }, "currentPhase": 15 }
```

---

## CHECKPOINT: Before Phase 15

### Interactive Mode Check

If `--interactive` flag is set:
```
═══════════════════════════════════════════════════════════════
  PHASE 14 COMPLETE - PRE-VALIDATION CHECKPOINT
═══════════════════════════════════════════════════════════════

Ready to proceed to Phase 15 (Adversarial Review).

Current recommendation: <Candidate or Hybrid>
Confidence: X%

The adversarial review will challenge this recommendation.
Continue to final validation?
```

Wait for user confirmation before proceeding.

---

## PHASE 15: Final Validation & Adversarial Review

**Objective**: Stress-test recommendation through isolated adversarial review.

### Actions

1. **Compile Recommendation Summary**:
   - Primary recommendation
   - Key decision factors with weights
   - Alternatives considered
   - Critical assumptions
   - Known gaps and mitigations

2. **Spawn Adversarial Reviewer** (CRITICAL: Use isolated agent):
   ```yaml
   agent: general-purpose
   context: fork  # Isolated to prevent bias contamination
   ```

   Provide to adversarial agent:
   - Primary recommendation (name only)
   - Key decision factors (summary)
   - Rejected alternatives (names only)
   - Stated assumptions

3. **Adversarial Review Questions**:
   - What are the strongest arguments AGAINST the recommended candidate?
   - What scenario would make a rejected candidate better?
   - What information might be missing?
   - What biases might have influenced this?
   - What could go wrong in 12 months?

4. **Respond to Adversarial Findings**:
   - Address each concern
   - Reconsider underweighted factors
   - Investigate blind spots
   - Mitigate identified biases
   - Validate assumptions

5. **Final Decision Documentation**:
   - Post-review recommendation (same or changed)
   - Confidence adjustment
   - Dissenting views preserved
   - Risk acceptance documented

### Outputs

Create `.oss-eval/phase-15-validation/`:
- `adversarial-review.md` - Output from isolated agent
- `dissenting-views.md` - Record of dissent and responses
- `final-validation.md` - Final decision documentation

### Completion Criteria

- [ ] Adversarial review by isolated agent
- [ ] All concerns addressed or acknowledged
- [ ] Dissenting views preserved
- [ ] Final decision documented

### Update Config

```json
{
  "phases": { "15": { "status": "completed", "completedAt": "<timestamp>" } },
  "currentPhase": "complete",
  "status": "completed",
  "completedAt": "<timestamp>"
}
```

---

# COMPLETION

## Generate Final Report

Create `.oss-eval/final-report.md` using template from `@templates/final-report.md`.

The report includes:
- Executive summary with recommendation
- Detailed phase findings
- Implementation roadmap
- Risk register
- Appendices with full data

## Display Completion Message

```
═══════════════════════════════════════════════════════════════
  OSS EVALUATION COMPLETE
═══════════════════════════════════════════════════════════════

Topic: <topic>
Duration: <time elapsed>
Phases Completed: 15/15

RECOMMENDATION: <candidate or hybrid>
Confidence: X%

Key Decision Factors:
  1. <factor 1>
  2. <factor 2>
  3. <factor 3>

Reports Generated:
  - .oss-eval/interim-report.md (Phases 1-6)
  - .oss-eval/final-report.md (Complete evaluation)

Adversarial Review: ✅ Completed
Dissenting Views: ✅ Documented

All outputs available in .oss-eval/
═══════════════════════════════════════════════════════════════
```

---

# BIAS PREVENTION THROUGHOUT

The following safeguards are active during all phases:

1. **Web Verification Required**: Never make claims about features, versions, or capabilities without web search verification
2. **[OSS]/[PAID] Tagging**: All features annotated with availability status
3. **Cross-Platform Checking**: Verify features exist under different names across frameworks
4. **Component-Level Breakdown**: Estimate complexity at component level, not holistically
5. **Baseline Consistency**: Comparison criteria locked from Phase 1
6. **Marketing Translation**: Convert marketing language to technical specifications
7. **Isolated Agents**: Use forked context for code analysis and adversarial review
8. **Evidence-Based Claims**: All claims require verification sources

---

# ERROR HANDLING

## Phase Failure

If any phase fails:
1. Update config.json with current state
2. Display error with context
3. Suggest remediation: `/oss-eval:run --resume`

## Workspace Corruption

If config.json is corrupt or missing:
```
❌ Evaluation workspace corrupted.

Options:
  1. /oss-eval:start <topic> - Start fresh evaluation
  2. Manually repair .oss-eval/config.json
```

## No Candidates Found

If Phase 1 yields no viable candidates:
```
⚠️ No viable candidates found for "<topic>"

Suggestions:
  - Broaden search terms
  - Relax filtering criteria
  - Consider adjacent technology domains
```

---

# REFERENCE

## Individual Phase Commands

For manual step-by-step execution or detailed phase documentation:

| Phase | Command | Purpose |
|-------|---------|---------|
| 1 | `/oss-eval:discover` | Web search discovery |
| 2 | `/oss-eval:analyze` | Candidate analysis |
| 3 | `/oss-eval:matrix` | Feature matrix |
| 4 | `/oss-eval:licensing` | License analysis |
| 5 | `/oss-eval:community` | Community health |
| 6 | `/oss-eval:risk` | Risk assessment |
| 7 | `/oss-eval:architecture` | Architecture analysis |
| 8 | `/oss-eval:requirements` | Requirements alignment |
| 9 | `/oss-eval:gaps` | Gap mitigation |
| 10 | `/oss-eval:ui` | UI integration |
| 11 | `/oss-eval:costs` | Operational costs |
| 12 | `/oss-eval:dx` | Developer experience |
| 13 | `/oss-eval:context` | Product context |
| 14 | `/oss-eval:hybrid` | Hybrid strategies |
| 15 | `/oss-eval:validate` | Final validation |

## Utility Commands

- `/oss-eval:status` - View current progress
- `/oss-eval:report --interim` - Generate interim report
- `/oss-eval:report` - Generate final report
