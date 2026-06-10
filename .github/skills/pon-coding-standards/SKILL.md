---
name: pon-coding-standards
description: Pon coding standards and conventions. Use when writing or
  reviewing code in this repo — covers constants over magic numbers, secure
  logging (ECS), commit message format, and pull request expectations.
---

# Pon coding standards

When writing or reviewing code in this repository, apply these rules.

## Constants

- Never use magic numbers; name them as constants with a clear, single purpose.
- Declare constants globally when used across multiple files.
- Use constants for configuration that varies between environments.

## Logging

- Log through a library using ECS levels (error/debug/notice); avoid
  `console.log`/`printf`.
- Never log secrets, credentials, or PII.

## Security

- Validate and sanitize all inputs at system boundaries.
- Follow OWASP guidance; treat third-party API data as untrusted.

## Commits & pull requests

- Use Conventional Commits (`type(scope): subject`), imperative mood.
- Keep pull requests small and focused on a single issue.
- The PR title references the issue/ticket.
