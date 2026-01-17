# Feature Verification Skill

## Purpose

Systematic cross-platform feature verification to prevent false differentiation and ensure accurate feature matrices. This skill provides protocols for verifying that features claimed as "missing" aren't simply named differently.

## Activation

This skill is critical during:
- Phase 3: Feature Matrix Development
- Phase 7: Architecture Analysis
- Phase 8: Requirements Alignment
- Any phase comparing capabilities across candidates

## Core Verification Protocol

### Step 1: Terminology Mapping

Before claiming a feature is missing, check for equivalent terminology:

```markdown
## Common Terminology Variations

| Concept | Framework A | Framework B | Framework C |
|---------|-------------|-------------|-------------|
| Request Pipeline | Middleware | Interceptors | Plugins |
| Dependency Injection | DI Container | Services | Providers |
| Data Validation | Validators | Schema | Serializers |
| Background Jobs | Workers | Tasks | Jobs |
| Real-time | WebSocket | Channels | Hubs |
| Caching | Cache | Store | Repository |
| Authentication | Auth | Identity | Security |
| API Documentation | OpenAPI | Swagger | API Docs |
| Testing | Test Client | Test Utils | Testing Module |
| CLI Tools | CLI | Artisan | Management Commands |
```

### Step 2: Architectural Equivalence

Same outcome achieved through different architectural patterns:

```markdown
## Pattern-Based Equivalence

### Built-in vs. Convention-Based
| Requirement | Explicit Support | Convention Approach |
|-------------|------------------|---------------------|
| Auto-validation | Decorator-based | File naming convention |
| Route generation | Explicit decorators | Directory structure |
| Dependency injection | Container | Module imports |

### Framework vs. Ecosystem
| Requirement | In Framework | In Ecosystem |
|-------------|--------------|--------------|
| ORM | Built-in ORM | Official adapter for X |
| Authentication | Auth module | Official strategy Y |
| Caching | Cache layer | Redis/Memcached adapter |
```

### Step 3: Search Protocol

For each "missing" feature, execute this search sequence:

```markdown
## Feature Verification Search Sequence

### 1. Official Documentation
- Search: `site:<docs-url> "<feature-name>"`
- Search: `site:<docs-url> "<alternative-term>"`
- Check: API reference, guides, tutorials

### 2. Repository Search
- Search: `<feature> repo:<org>/<repo>`
- Check: README, source code, examples
- Look for: interfaces, abstract classes, extension points

### 3. GitHub Issues/Discussions
- Search: `is:issue "<feature>" repo:<org>/<repo>`
- Look for: Feature requests (indicates missing)
- Look for: Closed with "already exists" or "use X instead"

### 4. Community Resources
- Search: `"<framework>" "<feature>" tutorial`
- Check: Blog posts, Stack Overflow, Reddit
- Look for: Community implementations, plugins

### 5. Package Registries
- npm: `<framework> <feature>`
- PyPI: `<framework>-<feature>`
- Check: Official vs. community packages
```

### Step 4: Verification Documentation

Document verification results in standard format:

```markdown
## Feature Verification Record

### Feature: <feature-name>

**Search Date**: <date>
**Candidate**: <framework-name>
**Initial Status**: Missing

**Verification Steps**:
1. ✅ Official docs - Not found
2. ✅ Repo search - Found in `<file>` as `<alternate-name>`
3. ❌ Issue search - Skipped (found in step 2)
4. ❌ Community - Skipped

**Result**: EXISTS as `<alternate-name>`
**Evidence**: [Link to documentation/code]
**Notes**: <any important context>

**Final Status**: ✅ Available (as <alternate-name>)
```

## Cross-Platform Feature Matrix Template

Use this template to ensure thorough verification:

```markdown
## Feature Comparison: <Feature Category>

| Feature | <Framework A> | <Framework B> | <Framework C> | Verified |
|---------|---------------|---------------|---------------|----------|
| <name> | ✅ `name_a` | ✅ `name_b` [^1] | ❌ Verified | 2025-01-16 |
| <name> | ✅ [OSS] | ⚠️ [PLUGIN] req | ✅ [OSS] | 2025-01-16 |
| <name> | ❌ Verified | ✅ [OSS] | ✅ [PAID] | 2025-01-16 |

[^1]: Called "alternative-name" in Framework B documentation
```

## Equivalence Categories

### Direct Equivalent
Same feature, different name:
```markdown
| Framework A | Framework B | Type |
|-------------|-------------|------|
| `middleware()` | `interceptor()` | Direct equivalent |
```

### Functional Equivalent
Different approach, same outcome:
```markdown
| Framework A | Framework B | Type |
|-------------|-------------|------|
| Decorator-based routing | Convention-based routing | Functional equivalent |
```

### Partial Equivalent
Similar but with differences:
```markdown
| Framework A | Framework B | Type |
|-------------|-------------|------|
| Full DI container | Manual DI support | Partial - A has more features |
```

### Ecosystem Equivalent
Available via official plugin/extension:
```markdown
| Framework A | Framework B | Type |
|-------------|-------------|------|
| Built-in ORM | Official ORM adapter | Ecosystem - same outcome |
```

### Not Equivalent
Genuinely missing:
```markdown
| Framework A | Framework B | Type |
|-------------|-------------|------|
| GraphQL subscriptions | No equivalent found | Not equivalent - verified missing |
```

## Red Flags Requiring Verification

Always verify when:

1. **Popular framework "missing" common feature** - Likely terminology difference
2. **Feature exists in similar frameworks** - Check for equivalent pattern
3. **Feature is table stakes for category** - Probably exists somehow
4. **Documentation seems incomplete** - Check code and community
5. **Framework newer than feature concept** - May use different approach

## Verification Checklist

Before marking any feature as ❌:

```markdown
## Feature Missing Verification

Feature: <name>
Candidate: <framework>

- [ ] Searched official docs with 3+ terms
- [ ] Searched repository code
- [ ] Checked GitHub issues for "already exists" responses
- [ ] Searched for community plugins/packages
- [ ] Verified no architectural equivalent exists
- [ ] Documented all search attempts

If all checked, feature can be marked as ❌ Missing
Otherwise, continue investigation
```

## Common False Differentiations

These features almost always exist in some form:

| Feature | Why It Almost Always Exists | What to Search For |
|---------|----------------------------|-------------------|
| Logging | Basic infrastructure | logger, logging, log |
| Configuration | Basic infrastructure | config, settings, env |
| Testing | Development essential | test, testing, spec |
| Validation | Common requirement | validate, schema, serializer |
| Caching | Performance basic | cache, store, memoize |
| Authentication | Security basic | auth, session, identity |
| Error Handling | Infrastructure | exception, error, handler |
| CLI | Developer productivity | cli, command, manage |

## Integration with Bias Prevention

This skill directly addresses:
- **Pitfall 2**: False Feature Differentiation
- **Pitfall 6**: Marketing Language (by verifying claims)
- **Pitfall 9**: Confirmation Bias (systematic search counters cherry-picking)
