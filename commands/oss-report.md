# OSS Evaluation - Report Generation

**Command**: `/oss-eval:report [--interim] [--format <format>]`

## Purpose

Generate comprehensive evaluation reports from completed phases. Supports interim reports (after Phase 6) and final reports (after Phase 15).

## Arguments

- `--interim`: Generate interim report with Phases 1-6 findings
- `--format <format>`: Output format (`markdown` default, `html`, `pdf-ready`)
- No arguments: Generate full report (requires all 15 phases complete)

## Prerequisites

### For Interim Report
- Phases 1-6 completed
- Read `.oss-eval/config.json` to verify completion

### For Final Report
- All 15 phases completed
- Adversarial review completed (Phase 15)

## Report Generation Process

### Step 1: Verify Phase Completion

```javascript
// Check config.json for phase status
const config = readConfig();
const completedPhases = Object.values(config.phases)
  .filter(p => p.status === 'completed').length;

if (args.interim && completedPhases < 6) {
  error("Interim report requires Phases 1-6 complete");
}
if (!args.interim && completedPhases < 15) {
  error("Final report requires all 15 phases complete");
}
```

### Step 2: Gather Phase Outputs

Collect all phase output files:

```markdown
## Source Documents

### Discovery & Analysis (Phases 1-6)
- `.oss-eval/phase-01-discovery/candidates.md`
- `.oss-eval/phase-01-discovery/sources.md`
- `.oss-eval/baseline-criteria.md`
- `.oss-eval/phase-02-analysis/*.md`
- `.oss-eval/phase-03-features/feature-matrix.md`
- `.oss-eval/phase-04-licensing/licensing-analysis.md`
- `.oss-eval/phase-05-community/community-health.md`
- `.oss-eval/phase-06-risk/risk-assessment.md`

### Technical Deep-Dive (Phases 7-9) [Final only]
- `.oss-eval/phase-07-architecture/*/code-analysis.md`
- `.oss-eval/phase-08-requirements/requirements-alignment.md`
- `.oss-eval/phase-09-gaps/gap-mitigation.md`

### Integration Analysis (Phases 10-12) [Final only]
- `.oss-eval/phase-10-ui/ui-integration.md`
- `.oss-eval/phase-11-costs/operational-costs.md`
- `.oss-eval/phase-12-dx/developer-experience.md`

### Validation (Phases 13-15) [Final only]
- `.oss-eval/phase-13-context/product-context.md`
- `.oss-eval/phase-14-hybrid/hybrid-strategies.md`
- `.oss-eval/phase-15-validation/adversarial-review.md`
- `.oss-eval/phase-15-validation/dissenting-views.md`
- `.oss-eval/phase-15-validation/final-validation.md`
```

### Step 3: Synthesize Executive Summary

For the executive summary, distill:

1. **Recommendation**: Clear statement of selected solution
2. **Confidence Level**: Based on evidence strength and adversarial review
3. **Key Decision Factors**: Top 3-5 factors that drove the decision
4. **Critical Trade-offs**: What was accepted in making this choice
5. **Implementation Highlights**: Effort, cost, timeline summary

### Step 4: Generate Report

Use template from `@templates/final-report.md`:

```markdown
## Report Generation

1. Read all source documents
2. Extract key findings from each phase
3. Populate template sections
4. Generate comparison tables
5. Compile recommendations
6. Include appendix references
```

### Step 5: Write Report File

Output location: `.oss-eval/final-report.md` or `.oss-eval/interim-report.md`

## Interim Report Structure

For `--interim` flag:

```markdown
# OSS Evaluation Interim Report: <Topic>

**Phases Completed**: 6/15
**Report Type**: Interim (Discovery & Analysis)
**Date**: <date>

---

## Purpose

This interim report summarizes findings from the Discovery and Analysis phases (1-6). It provides sufficient information to:
- Confirm candidate selection for detailed analysis
- Identify early blockers or concerns
- Validate evaluation direction with stakeholders

---

## Executive Summary

### Candidates Under Evaluation
<list of candidates proceeding>

### Key Findings So Far
<top 3-5 findings>

### Preliminary Recommendation
<early indication, subject to Phases 7-15>

---

## Phase Summaries

### Phase 1: Discovery
<summary>

### Phase 2: Candidate Analysis
<summary>

### Phase 3: Feature Matrix
<summary with key table>

### Phase 4: Licensing
<summary>

### Phase 5: Community Health
<summary>

### Phase 6: Risk Assessment
<summary with risk scores>

---

## Decision Point

**Candidates Proceeding to Deep-Dive**:
1. <candidate A> - <rationale>
2. <candidate B> - <rationale>

**Candidates Eliminated**:
1. <candidate X> - <reason>

---

## Next Steps

1. Run `/oss-eval:architecture` to begin Phase 7
2. Complete Phases 7-15 for full recommendation
3. Final report available after Phase 15

---

## Appendices

<references to phase detail files>
```

## Final Report Structure

For full report (no `--interim` flag):

Use complete template from `@templates/final-report.md`

## Report Quality Checks

Before generating report:

```markdown
## Pre-Generation Checklist

- [ ] All required phases show "completed" status
- [ ] All phase output files exist and are non-empty
- [ ] Feature matrix has [OSS]/[PAID] annotations
- [ ] Risk scores have documented evidence
- [ ] Adversarial review is complete (final report)
- [ ] Dissenting views are documented (final report)
```

## Output

### Interim Report Output
```
📊 Interim Report Generated

Phases summarized: 1-6
Candidates analyzed: X
Output: .oss-eval/interim-report.md

Key findings:
- <finding 1>
- <finding 2>
- <finding 3>

Next: Run /oss-eval:architecture to continue evaluation
```

### Final Report Output
```
📊 Final Report Generated

Phases summarized: 1-15
Candidates analyzed: X
Recommendation: <candidate>
Confidence: X%

Output: .oss-eval/final-report.md

The report includes:
- Executive summary
- Detailed phase findings
- Implementation roadmap
- Risk register
- Appendices with full data

Adversarial review: ✅ Completed
Dissenting views: ✅ Documented
```

## Bias Prevention in Report Generation

When synthesizing the report:

1. **Represent all candidates fairly** - Don't minimize rejected candidates
2. **Include trade-offs** - Show what was sacrificed in the choice
3. **Document uncertainty** - Confidence levels should reflect evidence quality
4. **Preserve dissent** - Adversarial concerns should be visible
5. **Link evidence** - Claims should reference phase findings

## Format Options

### Markdown (Default)
Standard markdown output, viewable in any markdown reader.

### HTML (--format html)
Generates HTML version with:
- Styled tables
- Collapsible sections
- Navigation links

### PDF-Ready (--format pdf-ready)
Markdown optimized for PDF conversion:
- Page break hints
- Print-friendly tables
- Embedded images (if any)
