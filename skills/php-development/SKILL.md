---
name: php-development
description: Use when reading, writing, debugging, or reviewing PHP code in XIVA, especially native PHP and PHP-FPM applications.
---

# PHP Development for XIVA

## Before coding
- Inspect `composer.json`, bootstrap files, entry points, routing, autoloading, and nearby PHP files. Do not assume Composer or a framework is used.
- Confirm the PHP version from project configuration or runtime evidence. The developer's environment may use PHP 8.5, but repository/runtime evidence takes precedence.
- Follow the project's existing naming, formatting, include, class, and error-handling conventions.

## Implementation rules
- Prefer straightforward, readable PHP over unnecessary abstractions, deep helper nesting, or framework-like structures.
- Keep business logic explicit and testable. Avoid duplicating benefit, eligibility, tariff, or claim calculations.
- Validate external input at the boundary. Do not trust request parameters, headers, uploaded files, or decoded JSON.
- Use PDO prepared statements or the project's established safe database layer. Never concatenate untrusted input into SQL.
- Handle failures deliberately. Do not suppress errors with `@`, expose stack traces or secrets to clients, or convert failures into misleading success responses.
- Preserve API contracts: HTTP status, response envelope, field names, types, and error semantics.
- Use strict comparisons where appropriate; handle null, empty string, zero, false, and missing fields distinctly.
- Use transactions for logically atomic multi-write operations. Roll back on failure.
- Avoid global state changes and hidden side effects. If the existing code uses globals, understand and follow the established pattern rather than introducing more casually.
- Keep functions focused, but do not split simple logic into many tiny helpers without benefit.

## Security
- Escape output for its actual context (HTML, attributes, JavaScript, URL).
- Apply authorization on the server for every protected operation; hiding a UI control is not authorization.
- Use secure session and token handling. Never log credentials, access tokens, patient/member identifiers, or sensitive claim data unnecessarily.
- Validate file type, size, extension, storage location, and access permissions for uploads.
- Protect state-changing requests against CSRF where session cookies are used.
- Do not reveal whether a member, policy, or claim exists unless the caller is authorized to know.

## Performance
- Look for N+1 queries, repeated expensive calculations, unbounded result sets, and unnecessary serialization.
- Add caching only after identifying a stable cache key, invalidation rule, and correctness implications.
- Do not introduce background workers or queues merely as a default optimization. First understand the current request/API flow and measured bottleneck.

## Verification
- Use `php -l` on changed PHP files when available.
- Run relevant tests or a focused request-level check if the project provides them.
- Inspect the final diff and confirm no unrelated formatting or generated files changed.
- Report checks accurately; syntax validation is not the same as functional testing.
