# Copy-ready XIVA Agent Prompts

## 1. Understand a module
Read the relevant module without changing files. Trace its entry point, main functions/classes, database tables, API calls, and UI callers. Explain the actual execution flow with file paths. Separate verified facts from assumptions.

## 2. Implement a small feature
First inspect the existing implementation and conventions. Identify the smallest set of files that must change and present a short plan. Do not edit until the plan is approved. Preserve existing API contracts and business behavior outside the requested scope. After editing, review the diff and run relevant safe checks.

## 3. Debug a problem
Do not guess or patch immediately. Trace the execution path and identify likely root causes with evidence. Ask for missing runtime details only if necessary. Propose a minimal fix and regression check before editing.

## 4. Review a database query
Inspect the actual schema, indexes, query callers, and expected result cardinality. Check correctness before performance. Identify duplicate-row risks, null behavior, date boundaries, and index implications. Do not change schema or data.

## 5. Architecture review
Map the current implementation and dependencies for the specified flow. Do not redesign it. Identify coupling, contracts, failure paths, and measurable risks. Recommend the smallest viable improvement and explain trade-offs.

## 6. Update documentation
Compare the specified documentation with the actual source code, schema, configuration, and tests. Update only the relevant sections. Do not invent behavior or rewrite unrelated documentation. List source files used as evidence and unresolved questions.

## 7. Security review
Review the specified files or flow for concrete security risks. Provide severity, evidence, realistic impact, and recommended remediation. Do not modify authentication, authorization, secrets, or security configuration unless explicitly asked.

## 8. Review my changes
Review the current Git diff only. Prioritize business logic, data integrity, authorization, API compatibility, edge cases, and regressions. Report findings first, ordered by severity. Do not edit files unless asked.
