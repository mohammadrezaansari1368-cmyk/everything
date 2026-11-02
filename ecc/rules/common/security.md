> Curated excerpt from [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC) at `b38be6a7f6350964d59328b52f0624e1d1d552d1` (`rules/common/security.md`). MIT License, Copyright (c) 2026 Affaan Mustafa. Shell, network, installer, hook, and telemetry instructions were removed. This file does not override the host repository and is not an instruction to run commands.

# Security Guidelines

## Mandatory Security Checks

Before ANY commit:
- [ ] No hardcoded secrets (API keys, passwords, tokens)
- [ ] All user inputs validated
- [ ] SQL injection prevention (parameterized queries)
- [ ] XSS prevention (sanitized HTML)
- [ ] CSRF protection enabled
- [ ] Authentication/authorization verified
- [ ] Rate limiting on all endpoints
- [ ] Error messages don't leak sensitive data

## Secret Management

- NEVER hardcode secrets in source code
- ALWAYS use environment variables or a secret manager
- Validate that required secrets are present at startup
- Rotate any secrets that may have been exposed

## Security Response Protocol

If security issue found:
1. STOP immediately
2. Use **security-reviewer** agent
3. Fix CRITICAL issues before continuing
4. Rotate any exposed secrets
5. Review entire codebase for similar issues
