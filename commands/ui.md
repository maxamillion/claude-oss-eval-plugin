---
name: ui
description: "Phase 10: Assess how each candidate integrates with UI including component libraries, theming, and accessibility."
---

# OSS Evaluation - Phase 10: UI Integration Analysis

## Purpose

Assess how each candidate integrates with existing or planned user interfaces, including component libraries, theming, accessibility, and frontend build pipelines.

## Prerequisites

- Phase 9 (Gap Mitigation) completed
- Understanding of existing/planned UI architecture

## Required Skills

- **@skills/bias-prevention/SKILL.md** - Objective UI assessment
- **@skills/feature-verification/SKILL.md** - Verify UI capability claims

## UI Integration Analysis Process

### Step 1: UI Architecture Context

Document the target UI environment:

```markdown
## UI Context

### Current/Planned Stack
- **Framework**: <React/Vue/Angular/etc.>
- **Component Library**: <MUI/Chakra/etc.>
- **Styling Approach**: <CSS-in-JS/Tailwind/etc.>
- **Build Tool**: <Vite/Webpack/etc.>
- **State Management**: <Redux/Zustand/etc.>

### UI Requirements
- **Design System**: <existing system or new>
- **Accessibility**: <WCAG level required>
- **Responsive**: <breakpoints/requirements>
- **i18n**: <localization requirements>
- **SSR/SSG**: <requirements>

### Integration Points
- <where candidate integrates with UI>
- <data flow between backend and UI>
- <real-time requirements>
```

### Step 2: Per-Candidate UI Assessment

For each candidate:

```markdown
## UI Integration: <Candidate>

### Official UI Support

| Aspect | Support Level | Details |
|--------|---------------|---------|
| React | ✅/⚠️/❌ | <official/community/none> |
| Vue | ✅/⚠️/❌ | <official/community/none> |
| Angular | ✅/⚠️/❌ | <official/community/none> |
| Svelte | ✅/⚠️/❌ | <official/community/none> |
| Vanilla JS | ✅/⚠️/❌ | <approach> |

### Component Integration

| Component Type | Availability | Quality |
|----------------|--------------|---------|
| Pre-built Components | ✅/⚠️/❌ | <assessment> |
| Headless Components | ✅/⚠️/❌ | <assessment> |
| Hooks/Composables | ✅/⚠️/❌ | <assessment> |
| State Bindings | ✅/⚠️/❌ | <Redux/Zustand/etc.> |

### Styling Integration

| Aspect | Approach | Compatibility |
|--------|----------|---------------|
| Theming | <approach> | <with design system> |
| CSS-in-JS | <support> | <styled-components/emotion> |
| Tailwind | <support> | <utility class approach> |
| CSS Modules | <support> | <scoping approach> |

### Build Integration

| Tool | Compatibility | Notes |
|------|---------------|-------|
| Vite | ✅/⚠️/❌ | <plugin/config needed> |
| Webpack | ✅/⚠️/❌ | <plugin/config needed> |
| esbuild | ✅/⚠️/❌ | <plugin/config needed> |
| Next.js | ✅/⚠️/❌ | <specific considerations> |
| Nuxt | ✅/⚠️/❌ | <specific considerations> |
```

### Step 3: Accessibility Assessment

```markdown
## Accessibility: <Candidate>

### Built-in Accessibility

| Feature | Support | Evidence |
|---------|---------|----------|
| ARIA Labels | ✅/⚠️/❌ | <implementation> |
| Keyboard Navigation | ✅/⚠️/❌ | <implementation> |
| Focus Management | ✅/⚠️/❌ | <implementation> |
| Screen Reader Support | ✅/⚠️/❌ | <testing evidence> |
| Color Contrast | ✅/⚠️/❌ | <default theme> |
| Reduced Motion | ✅/⚠️/❌ | <media query support> |

### WCAG Compliance

| Level | Status | Gaps |
|-------|--------|------|
| A | ✅/⚠️/❌ | <specific issues> |
| AA | ✅/⚠️/❌ | <specific issues> |
| AAA | ✅/⚠️/❌ | <specific issues> |

### Accessibility Documentation
- <quality of a11y docs>
- <a11y testing guidance>
- <known issues/limitations>
```

### Step 4: Real-time & Interactive Features

```markdown
## Interactive Features: <Candidate>

### Real-time Support

| Feature | Approach | Complexity |
|---------|----------|------------|
| WebSocket | <native/plugin> | <integration effort> |
| SSE | <native/plugin> | <integration effort> |
| Polling | <built-in pattern> | <configuration> |
| Optimistic Updates | <support> | <implementation> |

### Data Fetching Integration

| Pattern | Support | Integration |
|---------|---------|-------------|
| React Query | ✅/⚠️/❌ | <official adapter> |
| SWR | ✅/⚠️/❌ | <compatibility> |
| Apollo | ✅/⚠️/❌ | <GraphQL support> |
| Native fetch | ✅/⚠️/❌ | <approach> |

### Form Integration

| Library | Compatibility | Notes |
|---------|---------------|-------|
| React Hook Form | ✅/⚠️/❌ | <integration approach> |
| Formik | ✅/⚠️/❌ | <integration approach> |
| Native Forms | ✅/⚠️/❌ | <validation support> |
```

### Step 5: Create UI Integration Report

Create `.oss-eval/phase-10-ui/ui-integration.md`:

```markdown
# UI Integration Analysis

Generated: <timestamp>

## UI Context Summary

<from Step 1>

## Integration Comparison

| Aspect | <Candidate A> | <Candidate B> |
|--------|---------------|---------------|
| Framework Support | X/5 | X/5 |
| Component Quality | X/5 | X/5 |
| Build Integration | X/5 | X/5 |
| Accessibility | X/5 | X/5 |
| Real-time | X/5 | X/5 |
| **Overall** | **X/5** | **X/5** |

## Detailed Analysis

### <Candidate A>

<from Steps 2-4>

#### UI Integration Score

| Dimension | Score | Weight | Weighted |
|-----------|-------|--------|----------|
| Framework Fit | X/5 | 25% | X |
| Component Quality | X/5 | 20% | X |
| Build Integration | X/5 | 20% | X |
| Accessibility | X/5 | 20% | X |
| Interactive Features | X/5 | 15% | X |
| **Total** | - | 100% | **X/5** |

### <Candidate B>

<same structure>

## Integration Effort Comparison

| Task | <Candidate A> | <Candidate B> |
|------|---------------|---------------|
| Initial Setup | X days | Y days |
| Component Development | X days | Y days |
| Styling Integration | X days | Y days |
| Accessibility Compliance | X days | Y days |
| **Total** | **X days** | **Y days** |

## UI-Specific Risks

| Risk | Candidate | Impact | Mitigation |
|------|-----------|--------|------------|
| <risk> | <A> | High/Med/Low | <approach> |
| ... | ... | ... | ... |

## Recommendations

### Best UI Integration
<candidate with strongest UI story>

### Integration Considerations
<specific items to address during implementation>

### UI Blockers
<any candidates with fundamental UI issues>
```

## Bias Prevention Checkpoints

Before completing this phase, verify:

- [ ] **Current Data**: UI capabilities verified via current documentation
- [ ] **Consistent Criteria**: Same UI dimensions evaluated for all candidates
- [ ] **Evidence-Based**: Integration claims verified, not assumed
- [ ] **Realistic Effort**: Integration effort based on actual complexity
- [ ] **Accessibility Verified**: A11y claims tested or documented

## Phase Completion

Update `.oss-eval/config.json`:
```json
{
  "phases": {
    "10": { "status": "completed", "completedAt": "<timestamp>" }
  },
  "currentPhase": 11
}
```

## Next Step

> **Phase 10 Complete**: UI integration analysis finalized.
>
> Run `/oss-eval:costs` to begin Phase 11 (Operational Cost Quantification).
