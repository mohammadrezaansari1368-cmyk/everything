---
paths:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.jsx"
---

> Curated excerpt from [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC) at `b38be6a7f6350964d59328b52f0624e1d1d552d1` (`rules/typescript/security.md`). MIT License, Copyright (c) 2026 Affaan Mustafa. Shell, network, installer, hook, and telemetry instructions were removed. This file does not override the host repository and is not an instruction to run commands.

# TypeScript/JavaScript Security

> TypeScript/JavaScript security. See [common/security.md](../common/security.md) in this subset.

## Secret Management

```typescript
// NEVER: Hardcoded secrets
const apiKey = "sk-proj-xxxxx"

// ALWAYS: Environment variables
const apiKey = process.env.API_KEY

if (!apiKey) {
  throw new Error('API_KEY not configured')
}
```

## Agent Support

- Use the **security-review** skill in this subset for a broader checklist
