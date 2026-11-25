---
name: xiva-architecture-analysis
description: Use when tracing XIVA module boundaries, application flow, integrations, dependencies, architecture decisions, or cross-module changes.
---

# XIVA Architecture Analysis

## Mission
Explain and work with the architecture that exists. Do not redesign it by default.

## Discovery
- Map relevant entry points, routes, services, repositories, database tables, events, API clients, and UI callers.
- Trace one real request or business flow end to end.
- Identify synchronous calls, external integrations, cache usage, shared state, and failure handling.
- Distinguish confirmed implementation from inferred design.
- Check existing architecture documents and compare them with code. Flag drift rather than silently treating documentation as current.

## Decision principles
- Prefer the simplest architecture that satisfies measured requirements.
- Do not recommend microservices, event buses, queues, workers, distributed caches, or cloud migration as default solutions.
- Consider operational complexity, team capacity, deployment, observability, recovery, and total cost alongside theoretical scalability.
- For a monolith, preserve clear module boundaries and avoid unnecessary coupling.
- Recommend horizontal scaling only when there is evidence of a bottleneck that vertical tuning or query/application improvements cannot reasonably address.
- Treat API latency, throughput, concurrency, database saturation, memory, storage I/O, and external dependency latency as separate measurements.

## Cross-module changes
Before changing a shared contract or business rule:
1. Find all callers and consumers.
2. Identify affected modules, reports, invoices, integrations, and historical data.
3. Check compatibility and rollout sequence.
4. Define failure and rollback behavior.
5. Propose tests covering the end-to-end flow.

## Deliverables
For architecture reviews, provide:
- Current-state flow.
- Verified components and dependencies.
- Risks and bottlenecks with evidence.
- Options with trade-offs.
- Recommended smallest viable change.
- Open questions and assumptions.

Use diagrams only when they clarify actual relationships. Never invent components or traffic numbers.
