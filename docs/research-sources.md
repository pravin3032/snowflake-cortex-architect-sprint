# Official Product Research Notes

This dashboard distinguishes durable architecture concepts from Snowflake behavior that can change by release, account, cloud, region, edition, model, or driver.

## Verification rule

Before implementing exact syntax or selecting a product capability, recheck:

- GA versus Preview status;
- region and cross-region availability;
- account edition and required privileges;
- supported objects, models, drivers, and clouds;
- current limits, pricing, and service-consumption behavior;
- replication/failover support and known limitations.

Conceptual examples in the dashboard are not a substitute for current product documentation.

## Sources reviewed

### Dynamic Tables

Official source: https://docs.snowflake.com/en/user-guide/dynamic-tables/overview

Current documentation emphasizes declarative freshness, refresh modes, dependency graphs, monitoring, and cost. The overview states a minimum 60-second target lag and warns that refresh timing is not strictly guaranteed. Dynamic Tables are not the right choice for procedural side effects or stricter-than-supported latency.

### Streams

Official source: https://docs.snowflake.com/en/user-guide/streams-intro

Streams store offsets over table versions and expose change metadata. Important operational topics include repeatable-read behavior, staleness and retention, multiple consumers, Streams on views, the `CHANGES` clause, privileges, billing, and object-specific limitations.

### Tasks

Official source: https://docs.snowflake.com/en/user-guide/tasks-intro

Current Tasks documentation covers serverless and warehouse-backed compute, schedules and triggers, automatic retry and suspension, timeouts, versioned task runs, history, security, and user-privilege execution.

### Cortex Analyst

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-analyst

Current Analyst guidance centers on semantic views, access control, region availability, multi-turn conversations, verified query repositories, evaluations, model controls, and usage history. Warehouse cost for executing generated SQL is separate from Analyst AI usage.

### Cortex Search

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-search/cortex-search-overview

Current documentation covers primary keys, text splitting, embedding models, refresh behavior, multi-index services, user-provided embeddings, indexing suspension after refresh errors, serving auto-suspend, resource budgets, cross-region inference, replication, and known limitations.

### Cortex Agents

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-agents

Current Agents documentation includes agent objects and runs, threads, feedback, monitoring, evaluations, resource budgets, skills/toolsets, code execution, versioning, multi-tenancy, MCP connectors, and a Snowflake-managed MCP server. Exact availability and permissions must be rechecked before use.

### Cortex AI Functions

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/aisql

Current AI Functions include structured outputs and functions for generation, aggregation, extraction, sentiment, embeddings, similarity, document parsing, transcription, PII redaction, translation, and token counting. Individual functions can have different GA/Preview and regional status.

### Cortex AI Guardrails

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-ai-guardrails

The reviewed documentation marks Cortex AI Guardrails as an Enterprise Edition feature and describes protection for specific Snowflake AI experiences. Guardrails supplement—not replace—RBAC, row/masking policies, retrieval authorization, least-privilege tools, and human approval.

### AI Observability

Official source: https://docs.snowflake.com/en/user-guide/snowflake-cortex/ai-observability

Observability surfaces vary by feature. Native Cortex products can expose monitoring and evaluations; Account Usage exposes usage/cost metadata; custom applications can emit traces and evaluations using TruLens-related integrations. The application still needs its own request, identity, authorization, and business-context telemetry.

### External OAuth

Official source: https://docs.snowflake.com/en/user-guide/oauth-ext-overview

Current guidance includes scopes, secondary roles, network restrictions, token verification, error codes, and login-failure diagnostics. OAuth must not be reduced to assigning arbitrary session variables.

### Workload identity federation

Official source: https://docs.snowflake.com/en/user-guide/workload-identity-federation

Current documentation covers cloud workload identities, OIDC workloads, Kubernetes environments, GitHub/GitLab environments, SPIFFE/SPIRE, custom issuers, supported drivers, and hardening considerations.

### Replication and failover

Official sources:

- https://docs.snowflake.com/en/user-guide/account-replication-intro
- https://docs.snowflake.com/en/user-guide/multi-location-resilience-data-pipelines

Current guidance covers replication/failover groups, roles and grants, integrations, warehouses, Cortex Search services, schedules, editions, object-specific limitations, multi-location storage and notification integrations, dual-write versus routed ingestion, failback, pipe status, and load-history validation.

## Research conclusion

The strongest durable learning model is:

1. teach the architecture concept;
2. attach current official product behavior;
3. label edition/region/Preview constraints;
4. implement in an isolated environment;
5. verify failure, security, cost, and recovery behavior;
6. recheck documentation before production deployment.
