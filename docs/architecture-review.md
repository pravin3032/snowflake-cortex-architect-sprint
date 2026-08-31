# Architecture Review and Improvement Plan

## Executive assessment

The source proposal identifies the right capability areas—ingestion, incremental processing, governance, Cortex Analyst, Cortex Search, application services, and telemetry. Its main weakness is that it describes a repository more than it defines a learning system. A generated Next.js page with five checkboxes and three random incident strings does not create durable mastery.

This implementation changes the unit of learning from **content consumed** to **evidence produced and failure handled**.

## What was strong

1. One end-to-end reference platform anchors otherwise fragmented features.
2. It separates structured analytics from unstructured retrieval.
3. It recognizes identity propagation and telemetry as architecture concerns.
4. It distinguishes Dynamic Tables from Streams + Tasks at a high level.
5. It calls for failure simulation rather than passive reading.

## Gaps corrected

### 1. No mastery contract

**Original gap:** Completion was a Boolean checkbox that displayed `L5/L6` immediately.

**Correction:** Every module now has:

- current level and target level;
- observable outcome;
- required portfolio artifact;
- production-style verification test.

L0–L6 progression is therefore explicit and auditable.

### 2. Incidents were labels, not simulations

**Original gap:** A random string could be acknowledged but not investigated or scored.

**Correction:** Each incident now includes symptoms, relevant and distracting observations, alternative root causes, containment choices, a timer, scoring, and a resolution runbook.

### 3. Security was underspecified

**Original gap:** Identity propagation referenced session context or roles without a complete trust-boundary model.

**Correction:** The dashboard emphasizes:

- issuer, audience, signature, time, and scope validation;
- deny-by-default tenant filters in retrieval;
- delegated-user versus service-identity decisions;
- authorization on every data path, not in the UI;
- negative isolation tests as release gates.

### 4. AI quality lacked release engineering

**Original gap:** Groundedness appeared as a log field but not as a governed release decision.

**Correction:** The learning system treats recall@k, execution accuracy, groundedness, refusal behavior, latency, ACL safety, and cost as joint release gates supported by golden datasets.

### 5. Reliability and FinOps were secondary

**Original gap:** The proposal included telemetry fields but no SLOs, error budgets, workload isolation, or unit economics.

**Correction:** Dedicated curriculum and gates cover trace correlation, freshness, latency, cost per answer, scan/spill regressions, resource monitors, and workload blast radius.

### 6. Too much platform overhead for the first usable version

**Original gap:** Next.js, React, Tailwind, FastAPI, Terraform, dbt, and multiple CI pipelines were prescribed before validating the learning workflow.

**Correction:** The first version is static, dependency-free, and deployable to GitHub Pages. Backend and Snowflake integrations can be added when a drill requires real execution. This reduces setup cost and security exposure.

## Technical cautions in the source proposal

- Micro-partition size, automatic clustering behavior, Cortex feature interfaces, and identity-delegation mechanisms are product details that can evolve. Validate them against the Snowflake documentation for the account edition and release in use.
- A backend cannot safely "proxy" user identity merely by assigning session variables. Authentication, authorization, role activation, connection pooling, and audit attribution require an explicit, tested pattern.
- Cortex Search retrieval security must be enforced in query filters/index metadata and tested negatively. Hiding citations is not containment.
- Dynamic Tables and Streams/Tasks should be selected from semantics and operational needs, not preference. Declarative freshness and procedural side effects have different failure and replay models.
- An automated incident generator must not corrupt shared production resources. Use isolated schemas/accounts, fixtures, reversible fault injection, and budget guards.

## Recommended next implementation increments

1. Add runnable Snowflake SQL labs in isolated schemas with teardown scripts.
2. Add a semantic-model golden dataset and execution-accuracy evaluator.
3. Add a retrieval test pack with recall, groundedness, latency, and cross-tenant negative cases.
4. Add FastAPI middleware only when a real identity provider and Snowflake connection pattern are selected.
5. Add Terraform/dbt after the target account, cloud, edition, and deployment topology are known.
6. Link every module to one ADR, one runnable artifact, and one operational runbook.

## Definition of principal-ready

A learner is not principal-ready because every slider says L6. Readiness requires the ability to:

- state assumptions and business grain;
- quantify freshness, recovery, latency, quality, and cost targets;
- select and defend patterns under constraints;
- prove tenant isolation and safe failure behavior;
- diagnose from traces and query evidence;
- recover without losing or duplicating data;
- document trade-offs through reviewable artifacts;
- lead a timed incident and produce a preventive RCA.
