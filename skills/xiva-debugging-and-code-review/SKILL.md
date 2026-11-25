---
name: xiva-debugging-and-code-review
description: Use when diagnosing bugs, reviewing diffs, investigating regressions, or validating a focused code change in XIVA.
---

# XIVA Debugging and Code Review

## Debugging workflow
1. Restate the observed symptom and expected behavior.
2. Reproduce or identify the exact execution path.
3. Inspect logs, inputs, outputs, database effects, and related callers where available.
4. Form the smallest set of testable hypotheses.
5. Verify the root cause before changing code.
6. Implement the narrowest fix.
7. Add or identify a regression test.
8. Review the diff and report remaining uncertainty.

Do not patch symptoms with broad catches, silent defaults, arbitrary delays, or duplicated special cases.

## Review priorities
Review in this order:
1. Incorrect business behavior or financial/benefit calculation.
2. Authorization and sensitive-data exposure.
3. Data integrity, duplicate writes, transaction boundaries, and concurrency.
4. API compatibility and integration failures.
5. Runtime errors and edge cases.
6. Performance and maintainability.

## XIVA-specific regression checks
Where relevant, consider:
- Member eligibility and effective dates.
- Policy and plan boundaries.
- Benefit limits, utilization, exclusions, and waiting periods.
- Provider network and tariff selection.
- Cashless guarantee / authorization decisions.
- Claim registration, verification, adjudication, and rejection.
- Reimbursement and payment calculations.
- Invoice, service fee, and settlement totals.
- Reports and downstream consumers.

Do not assume every checklist item applies to every task. Trace the affected flow.

## Final review
Inspect the complete diff for unintended edits, missing validation, inconsistent naming, unhandled errors, unsafe SQL, leaked data, and changed contracts. Report findings by severity and identify checks actually performed.
