# AI-Assisted Framework Evaluation

## Methodology: Framework Evaluation Through AI-Assisted Analysis

### Safeguards Against Bias
* Prevent contamination from previous chat histories, training data, or other sources. Include no previous context or memory.
* Generic framing to avoid mentioning company names or products initially to prevent bias from existing features or perceived company interests
* Neutral language maintained even when refining prompts to catch missed elements. No technology, project, or framework names mentioned
* Constant verification addressed Claude's tendency to make assumptions
* Self-validation loops required Claude to verify its own findings before presenting them
* Cross-model scrutiny using both Claude and ChatGPT as adversarial reviewers
* Human oversight with manual checking fed back into the process
* Prompt variation testing to avoid leading the witness
    
### 15-Phase Evaluation Process
* Phase 1: Discovery
    - Prompt Claude to distrust its training data and actively search the internet for frameworks, tools, projects, and techologies in the desired topic space provided by the user. Instruct it to search GitHub, GitLab, industry blogs, and other channels.
* Phase 2: Candidate Analysis
    - Prompt Claude to analyze complete feature sets and licensing models to eliminate partial fits and identify primary contenders.
* Phase 3: Feature Matrix Development
    - Instruct Claude to perform fine-grained feature analysis with special attention to functionally equivalent features hiding under different names.
* Phase 4: Licensing Deep Dive
    - Prompt Claude to filter out managed-service-only offerings and flag proprietary features in otherwise open solutions.
* Phase 5: Community Health Check
    - Instruct Claude to analyze source repository metrics from GitHub, GitLab, and other channels, package index download stats such as PyPI, governance models, and other adoption indicators for each product.
* Phase 6: Risk Assessment
    - Prompt Claude to evaluate licensing risks, governance concerns, vendor lock-in potential, self-hosting complexity, and feature trajectory.
* Phase 7: Architecture & Enterprise Readiness
    - Use Claude Code Analysis to compare architecture, employing subagents to compare against source code of top three contenders, prompting it to analyze for dependency issues, scalability problems, concurrency handling, and operational concerns.
* Phase 8: Product Requirements Alignment
    - User provided information about critical requirements for portfolio integration and on-premises deployment capability. Prompt Claude to compare against top contenders' requirements.
* Phase 9: Gap Mitigation Strategy
    - Prompt Claude not to eliminate candidates with missing features that are provided as critical necessities or strategic requirements, but instead to estimate the effort required to contribute missing features using AI tools and adjust rankings accordingly.
* Phase 10: UI Integration Analysis
    - Inform Claude to evaluate various UI integration costs by informing it of three available strategies: re-theming/repackaging, component reuse, and API-driven new UI development.
* Phase 11: Operational Cost Quantification
    - If earlier risk assessment flags operational burden with time estimates, prompted Claude to create detailed cost analyses for consistent comparison across candidates.
* Phase 12: Developer Experience Evaluation
    - Prompt Claude to assess installation difficulty, setup complexity, and overall developer friction for each option.
* Phase 13: Product Context Introduction
    - User provides the product intended to be integrated with and Claude needs to revise its analysis accordingly. Claude then needs to compare the generic vs. product-specific assessments using separate incognito subagents sessions.
* Phase 14: Hybrid Strategy Exploration
    - Prompt Claude to evaluate combining a preferred platform with BYO (Bring Your Own) integration options to balance user choice with implementation costs. Instruct it to compare single-solution vs. hybrid approaches factoring in both product value and total cost.
* Phase 15: Final Validation & Adversarial Review
    - Prompt Claude to read entire analysis and reassess all claims for inconsistencies and logical problems
	- Ask Claude to evaluate whether gap description language was fair and consistent
	- Verify executive summary alignment with detailed findings
	- All validation sessions conducted in incognito subagents that carry no context or memory to ensure no bias from previous sessions
	- Prompt Claude to generate decision reversal criteria
	- Instructed Claude to add dissenting viewpoints with rebuttals
	- Repeated Phase 14 validation steps after additions

## AI Analysis Pitfalls & Prevention Guide
1. Outdated Knowledge Leading to False Claims
    Error: Claude incorrectly stated an upstream project lacked a feature functionality and would require 3-6 months of contribution work.
    Solution: Always use web search to verify current feature availability before making definitive claims, especially for rapidly evolving platforms.
    Error: Claude incorrectly returned stale Github star values (e.g. 18k vs 20.5k) even though it was performing an internet fetch, since they also have a near cache.
    Solution: Modify prompt to disregard caches and fetch only uncached data when rechecking quantitative data.
2. False Feature Differentiation
    Error: Claude claimed one project had a differentiation feature without checking if other candidates had equivalent capabilities (they did).
    Solution: For any claimed differentiator, explicitly verify all platforms' capabilities—features may exist under different names or have been recently added.
3. Conflating OSS and Commercial Features
    Error: Claude mixed open-source and paid features indiscriminately 
    Solution: Always annotate features with [OSS] or [PAID] tags and maintain separate sections for open-source vs. commercial capabilities.
4. Overestimating Technical Complexity
    Error: Claude estimated 9-17 months for a specific project's feature contributions when it was actually 1.5-2.5 months.
    Solution: Break down technical work into specific components and verify architectural assumptions before estimating effort.
5. Executive Summary Misalignment
    Error: Over-emphasizing technical details (UI integration) in executive summaries rather than focusing on strategic decisions.
    Solution: Executive summaries should focus on strategic impact, licensing, and major architectural decisions—save implementation details for technical sections.
6. Format Drift Without Purpose
    Error: Switching from star-based decision matrices to checkmark tables without deliberate reasoning.
    Solution: Maintain consistent analytical frameworks throughout an analysis unless there's a specific reason to change.
7. Misinterpreting Documentation Context
    Error: Claude interpreted a project's configuration documentation as a customer-facing feature when it was actually for internal service debugging only.
    Solution: When documentation describes a configuration, verify its actual purpose and intended user (internal debugging vs. customer feature) through multiple sources or code examination.
8. Incomplete System Analysis
    Error: Claude analyzed a project's non-blocking API layer efficiency without considering synchronous database write operations in the full call path.
    Solution: When evaluating performance or architecture, analyze the complete system path including all dependencies, not just the surface layer.
9. Missing Configuration Options
    Error: Claude stated one project only operated in synchronous fashion, missing the async configuration flag that enables asynchronous operation.
    Solution: Thoroughly review configuration documentation and flags before making categorical statements about system capabilities or limitations.
10. Training Data Contamination
    Error: Despite being prompted to use online sources, Claude's ingrained knowledge about an older, or outdated release, of a project would override findings from web searches about the latest release, requiring explicit re-prompting to trust online verification.
    Solution: When web search results contradict internal knowledge, explicitly prioritize current documentation over training data, especially for version-specific information.
11. Comparison Baseline Drift
    Error: Changing evaluation criteria mid-analysis or comparing systems using different measurement standards (e.g., comparing one system's burst capacity against another's sustained throughput).
    Solution: Establish evaluation criteria upfront and apply consistently across all compared systems—document any baseline changes explicitly with justification.
12. Marketing Language Infiltration
    Error Pattern: Unconsciously adopting vendor marketing terminology that obscures technical reality (e.g., "enterprise-grade" without defining what that means technically).
    Solution: Translate all marketing terms into specific technical requirements or capabilities—if a term can't be technically defined, exclude it from the analysis.

## Rules for Future AI Analysis Research Prompts
* Use web search to verify all capability claims against current official documentation before stating them as facts.
* For any feature claimed as a differentiator, explicitly verify whether competing platforms have equivalent functionality, even under different names.
* Clearly distinguish between open-source and commercial features. Label each capability as [OSS] or [PAID/COMMERCIAL].
* Use a consistent comparison framework (matrix, table, etc.) throughout the analysis. Do not change formats without explaining why.
* Keep executive summaries focused on business/architectural decisions. Place implementation details in technical sections only.
* Break down any effort estimates into specific technical components with justification for each.
* When documentation describes a feature, verify whether it's customer-facing or internal-only through multiple sources or code review.
* Analyze complete system paths including all dependencies and operations, not just surface-level components.
* Thoroughly review all configuration options and flags before stating categorical limitations.
* When web search contradicts your training data, explicitly prioritize current documentation, especially for version-specific information.
* Establish comparison criteria upfront and apply them consistently across all systems—use the same measurement standards for all platforms being evaluated.
* Translate all marketing terms (e.g., "enterprise-grade", "production-ready") into specific technical requirements—exclude terms that cannot be technically defined.
* When retrieving sources from the web like Github stars, prompt Claude to not use cached data

