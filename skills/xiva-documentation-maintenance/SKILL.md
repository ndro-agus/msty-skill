---
name: xiva-documentation-maintenance
description: Use when creating, updating, validating, or reconciling XIVA technical and business documentation against the actual codebase.
---

# XIVA Documentation Maintenance

## Documentation principles
- Documentation must describe the implemented system, not an imagined target architecture.
- Inspect source code, configuration, SQL, API contracts, and tests before documenting behavior.
- Mark unverified information as `To be verified` rather than presenting it as fact.
- Keep business rules distinct from technical implementation details.
- Use consistent terminology for TPA, managed care, indemnity, cashless, reimbursement, membership, provider, claim, benefit, guarantee, and settlement.

## Suggested documentation structure
Follow the repository's existing structure if one exists. Otherwise consider:
1. System Overview
2. Business & Domain
3. Functional Modules
4. Application Architecture
5. Database & Data Dictionary
6. API & Integrations
7. Security & Access Control
8. Operations & Deployment
9. Testing & Troubleshooting
10. Glossary and Change History

## Update workflow
1. Identify which document is authoritative.
2. Locate the implementation and verify the behavior.
3. Update only the relevant section.
4. Preserve existing structure, language, formatting, and links.
5. Add examples only when they are accurate and non-sensitive.
6. Record unresolved questions explicitly.
7. Review links, headings, terminology, and contradictions.

## Automatic maintenance boundaries
- Do not rewrite all documentation after a small code change.
- Do not create duplicate documents when an existing page should be updated.
- Do not infer database fields, API payloads, roles, or workflow states.
- Do not include credentials, real patient/member data, production identifiers, or secrets.
- If code and documentation conflict, report the discrepancy and update the document only after the implementation is understood.

## Output
Summarize the document files changed, the source files used to verify them, and any remaining items requiring confirmation.
