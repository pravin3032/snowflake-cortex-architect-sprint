# Snowflake Production & Cortex AI Architect Sprint

An interactive, local-first mastery system for becoming production-ready and principal-interview-ready across Snowflake Data Platform and Cortex AI architecture.

**Live dashboard:** https://pravin3032.github.io/snowflake-cortex-architect-sprint/

## Version 2 scope

The expanded dashboard maps the complete 62-section master prompt into:

- **69 granular modules** across 12 architecture domains;
- **1,095 named micro-topics** and searchable production details;
- a **62-section traceability matrix**;
- evidence-backed **L0–L6 mastery tracking**;
- guided study sessions using **Parts A–O**;
- a flagship Enterprise Customer Support Data + AI architecture;
- **12 scored production incidents** plus a broader failure taxonomy;
- nine decision guides and persistent ADRs;
- 30 principal interview/whiteboard prompts;
- eight-category interview scoring and gap plans;
- evidence portfolio, spaced-practice signals, and JSON import/export;
- verified product-accuracy notes with official Snowflake links.

## Design principle

The dashboard does not equate moving a slider with mastery. Every module includes:

1. an observable outcome;
2. micro-topics;
3. a required artifact;
4. a hands-on lab;
5. a production failure;
6. an interview defense;
7. a target depth based on role priority.

Progress is meaningful only when the artifact exists and the production test can be completed and defended without hints.

## Ten workspaces

1. **Command center** — readiness, weak-area adaptation, production gates.
2. **62-section coverage** — prompt-to-module traceability and failure taxonomy.
3. **Mastery roadmap** — filters for domain, depth, week, and any micro-topic.
4. **Guided session** — scenario, discovery, design, failure, recovery, security, cost, interview, score, and gap plan.
5. **Flagship system** — runtime, lineage, security, and recovery lenses.
6. **Decisions & ADRs** — trade-offs, evidence, risks, mitigation, reversal triggers.
7. **Incident lab** — timed evidence selection, diagnosis, containment, and runbooks.
8. **Interview lab** — audience-aware principal questions and eight-category scoring.
9. **Evidence portfolio** — code, SQL, diagrams, ADRs, evaluations, and postmortems.
10. **Product accuracy** — current official product notes and verification cautions.

## Run locally

Open `index.html`, or serve the directory with any static web server.

No build tool, framework, backend, database, secret, or network request is required. Progress is stored in browser `localStorage` and can be exported as JSON.

## GitHub Pages

The included workflow deploys the repository as a static GitHub Pages site after a push to `main`.

## Repository map

```text
.
├── index.html
├── assets/
│   ├── curriculum.js      # Modules, coverage, decisions, sources, failures
│   ├── app.js             # State, scoring, sessions, incidents, ADRs, interviews
│   └── styles.css         # Responsive design system
├── docs/
│   ├── architecture-review.md
│   └── research-sources.md
└── .github/workflows/pages.yml
```

## Product-accuracy rule

Snowflake syntax, model availability, regional support, edition requirements, privileges, limits, pricing, GA/Preview status, and replication behavior can change. The dashboard links to official documentation and labels change-sensitive behavior. Verify the target account and current documentation before implementation.

## Data and privacy

- Progress stays in the current browser unless exported.
- The dashboard contains no credentials and makes no application data calls.
- Example SLOs, incidents, and telemetry are simulations for training.
- The dashboard is a learning/design-review tool, not a live Snowflake control plane.
