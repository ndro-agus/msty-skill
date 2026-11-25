---
name: mysql-database-engineering
description: Use for XIVA schema analysis, SQL writing, query optimization, indexing, transactions, and database changes.
---

# MySQL Database Engineering

## Source of truth
Inspect migrations, schema dumps, SQL files, model/repository code, and actual connection configuration before assuming table names, columns, keys, collations, engines, or server version. MySQL 9.x may be used in the developer's environment, but verify the target environment.

## Query correctness
- Understand the business meaning and expected cardinality before writing a query.
- Use explicit column lists; avoid `SELECT *` in production-facing code.
- Parameterize all user-controlled values.
- Check join keys and relationship cardinality to prevent duplicated claims, members, invoices, or financial totals.
- Treat `NULL`, zero, empty strings, and missing rows as different states where business logic requires it.
- Use deterministic ordering for pagination.
- Avoid applying functions to indexed columns in predicates unless the plan justifies it.
- Use `EXPLAIN` / `EXPLAIN ANALYZE` only where supported and safe for the target environment.

## Schema changes
- Inspect existing naming and migration conventions.
- Identify primary keys, foreign keys, unique constraints, indexes, defaults, nullability, and data volume implications.
- Consider backward compatibility with existing application code and integrations.
- Do not run destructive DDL, truncate tables, delete production data, or rewrite historical records without explicit approval and a backup/rollback plan.
- For large tables, assess lock duration, table rebuild behavior, index build cost, and deployment sequence.
- Provide an up/down migration or rollback guidance when the project supports it.

## Financial and healthcare data
- Never change monetary precision, rounding, currency handling, benefit limit calculations, or aggregation logic without tracing the complete business rule.
- Confirm whether totals are per line, per claim, per member, per policy period, or per invoice.
- Check duplicate joins and date-boundary logic carefully.
- Preserve auditability for changes to claims, approvals, tariffs, and settlements.

## Optimization workflow
1. Reproduce the query and expected result.
2. Inspect schema and indexes.
3. Review the query plan and row estimates.
4. Identify the actual bottleneck.
5. Propose the smallest index/query change.
6. Consider write overhead and storage cost of additional indexes.
7. Compare results and plan after the change.

Do not claim a query is optimized based only on visual inspection. Do not add indexes speculatively.
