> Curated excerpt from [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC) at `b38be6a7f6350964d59328b52f0624e1d1d552d1` (`rules/common/testing.md`). MIT License, Copyright (c) 2026 Affaan Mustafa. Shell, network, installer, hook, and telemetry instructions were removed. This file does not override the host repository and is not an instruction to run commands.

# Testing Requirements

## Minimum Test Coverage: 80%

Test Types (ALL required):
1. **Unit Tests** - Individual functions, utilities, components
2. **Integration Tests** - API endpoints, database operations
3. **E2E Tests** - Critical user flows (framework chosen per language)

## Test-Driven Development

Required workflow:
1. Write the test first (RED)
2. Confirm the new test fails for the intended reason before any production edit
3. Write the minimal implementation (GREEN)
4. Confirm that same test now passes
5. Refactor (IMPROVE) while the tests stay passing
6. Confirm coverage meets the 80% bar

## Troubleshooting Test Failures

1. Use **tdd-guide** agent
2. Check test isolation
3. Verify mocks are correct
4. Fix implementation, not tests (unless tests are wrong)

## Agent Support

- **tdd-guide** - Use PROACTIVELY for new features, enforces write-tests-first

## Test Structure (AAA Pattern)

Prefer Arrange-Act-Assert structure for tests:

```typescript
test('calculates similarity correctly', () => {
  // Arrange
  const vector1 = [1, 0, 0]
  const vector2 = [0, 1, 0]

  // Act
  const similarity = calculateCosineSimilarity(vector1, vector2)

  // Assert
  expect(similarity).toBe(0)
})
```

### Test Naming

Use descriptive names that explain the behavior under test:

```typescript
test('returns empty array when no markets match query', () => {})
test('throws error when API key is missing', () => {})
test('falls back to substring search when Redis is unavailable', () => {})
```
