---
name: xiva-security-review
description: Use when reviewing XIVA code for application security, authorization, sensitive data exposure, API security, uploads, or configuration risks.
---

# XIVA Security Review

## Scope
Review the actual code and configuration. Prioritize exploitable risks and business impact. Do not claim compliance or certification from a code review.

## Review areas
- Authentication, session lifecycle, token validation, expiration, revocation, and secret storage.
- Authorization at every server-side endpoint and object-level access check.
- SQL injection, command injection, path traversal, SSRF, unsafe deserialization, and unsafe file handling.
- XSS, CSRF, clickjacking, CORS, and security headers where applicable.
- Input validation, output encoding, rate limiting, and abuse controls.
- Sensitive information in logs, error messages, URLs, exports, backups, and API responses.
- Encryption in transit and at rest where applicable; verify actual implementation rather than assuming it.
- Dependency and runtime configuration risks.
- Audit trails for sensitive claim, member, provider, payment, and administrative actions.

## Healthcare data handling
Treat member identity, medical information, claims, diagnoses, documents, policy details, and payment information as sensitive. Use synthetic examples. Do not copy real data into prompts, logs, test fixtures, or documentation.

## Findings format
For each finding include:
- Severity: Critical / High / Medium / Low / Informational.
- Affected file and relevant function/route.
- Evidence and realistic attack path.
- Impact.
- Recommended fix.
- Whether the finding is confirmed or needs runtime verification.

Avoid speculative findings. Explain compensating controls if visible. Never silently modify authentication or authorization behavior during a review.

## Safe testing
Do not attack production systems, exfiltrate data, brute-force credentials, or run destructive tests. Use local or explicitly authorized environments. Ask before running intrusive tests or changing security configuration.
