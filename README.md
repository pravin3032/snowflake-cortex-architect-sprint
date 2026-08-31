# Snowflake Cortex Architect Sprint

A framework-free, local-first learning and incident-response dashboard for developing production Snowflake + Cortex AI architecture judgment.

## Why this improves the original proposal

The initial concept had a useful reference architecture, but it was mainly a scaffold. This implementation adds:

- **Measurable L0–L6 progression** with explicit targets, outcomes, evidence, and production tests.
- **18 role-aligned modules** across data, incremental processing, governance, Cortex AI, application engineering, reliability, and FinOps.
- **Interactive architecture inspection** across runtime, security, and observability lenses.
- **Six scored incident drills** that require evidence selection, root-cause diagnosis, containment, and runbook review.
- **Architecture gates** covering grain, SLO/RPO/RTO, replay, least privilege, retention, telemetry, AI quality, and cost.
- **Evidence portfolio** for GitHub links, ADRs, diagrams, benchmarks, SQL labs, and incident write-ups.
- **Persistent progress** through browser local storage, with JSON export/import.
- **GitHub Pages deployment** without Node.js, a backend, or secrets.

## Run locally

Open `index.html` directly, or use a local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploy to GitHub Pages

1. Open **Settings → Pages** in the repository.
2. Under **Build and deployment**, select **GitHub Actions**.
3. Push to `main`. The included workflow publishes the static site.

## Repository map

```text
.
├── index.html                        # Accessible dashboard shell
├── assets/
│   ├── styles.css                    # Responsive design system
│   └── app.js                        # Curriculum, state, incidents, UI
├── docs/
│   └── architecture-review.md        # Audit and improvement rationale
└── .github/workflows/
    └── pages.yml                     # Static GitHub Pages deployment
```

## Mastery model

| Level | Meaning | Evidence expectation |
|---|---|---|
| L0 | Aware | Recognize the concept |
| L1 | Explain | Explain purpose and limits |
| L2 | Implement | Build a working example |
| L3 | Operate | Monitor and run it safely |
| L4 | Optimize | Improve performance, cost, or quality |
| L5 | Diagnose | Isolate failures using evidence |
| L6 | Defend | Lead design review and incident response |

Self-rating alone is not mastery. Each module includes a required artifact and a production test.

## Data and privacy

- Progress is stored only in the current browser using `localStorage`.
- Exported progress is a JSON file controlled by the user.
- The dashboard makes no network requests and contains no credentials.
- Example telemetry is explicitly labeled as simulated.

## Extending the project

Content is defined in `assets/app.js` as plain JavaScript objects:

- `MODULES` — add curriculum modules.
- `INCIDENTS` — add scored failure scenarios.
- `ARCH` — update architecture component controls and failure modes.
- `GATES` — change production review gates.

## Important implementation note

This dashboard is a learning and design-review tool, not a live Snowflake control plane. Production integrations should be added behind an authenticated service boundary and must not expose Snowflake or identity secrets to client-side code.
