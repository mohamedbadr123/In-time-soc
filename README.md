<div align="center">

# In Time

### An intelligent Security Operations Center (SOC) platform with two built-in AI models

Read security logs in plain language, investigate alerts, and learn the platform from your very first login.

![Status](https://img.shields.io/badge/status-proposal%20phase-orange)
![Type](https://img.shields.io/badge/type-university%20project-blue)
![AI](https://img.shields.io/badge/AI-advice%20only-green)

</div>

---

## What is In Time?

Security teams watch computer systems for attacks. They rely on **logs**: automatic records of what happens on a network, such as logins, errors and file changes. Logs are written for machines, so they are long, full of codes and hard for people to read. New analysts also need a long time to learn security tools.

**In Time** is a web application that brings log monitoring, alert handling and investigation into one place, and adds two AI models to make the work easier:

| AI model | What it does |
|---|---|
| **AI Guide** | Welcomes first-time users, gives a guided tour of every page and answers "how do I use this?" questions. |
| **AI Log Explainer** | Rewrites hard-to-read logs in plain language, explains why they may matter and highlights key details. |

Both models **only advise**. They separate facts from guesses, never claim an action was done when it was not, and change nothing without the user's approval.

![How In Time works](docs/images/how-it-works.png)

> **Project status:** In Time is in the **proposal phase** (Phase One). The features below are **planned**, not yet implemented. This README will be updated as development progresses.

---

## Planned features

**Must have**
- Secure login, roles and permissions (admin, SOC manager, Tier 1 and Tier 2 analyst, incident responder, auditor, read-only)
- AI Guide for first-time onboarding
- AI Log Explainer for plain-language logs
- Log collection from chosen sources and uploaded files (sources to be confirmed)
- Log processing into one common format
- Log search and filtering, with export
- Dashboard with alerts, severity levels, incidents and system health
- Alert management and incident management
- Audit trail of every user and AI action

**Should have**
- Charts and timelines
- Investigation workspace linking logs, alerts, incidents, users, devices and IP addresses
- AI-assisted analysis: summaries of related logs, suggested queries, recommended next steps
- Executive and technical reports (PDF, CSV)
- User and role management page

**Could have**
- Detection of unusual activity
- Customisable dashboards and dark mode
- Additional log sources
- Scheduled reports and a live log view

---

## System overview

![Block diagram](docs/images/block-diagram.png)

1. **Log sources** produce raw logs (sources to be confirmed; a test log generator is planned).
2. **Collection and processing** receives, queues, cleans and normalises the logs.
3. **Data layer** stores users, alerts, incidents and the audit trail, and indexes logs for fast search.
4. **Application services (REST API)** handle login, roles, search, alerts, incidents, dashboards and reports.
5. **AI layer** contains the two models, behind an orchestrator that applies guardrails and an approval gate.
6. **Web interface** gives analysts the dashboard, log search, case handling, reports and administration.

---

## Proposed technology stack

> These are proposals and may change.

| Area | Proposed tools |
|---|---|
| Front end | TypeScript, React |
| Back end | Python (for example FastAPI) |
| Database | PostgreSQL |
| Log search | OpenSearch or Elasticsearch |
| Ingestion | Message queue or task runner |
| AI | Two language models, through a cloud provider or run locally (to be confirmed) |
| Deployment | Docker, Git, continuous integration |

---

## Security and AI safety

- Role-based access control on every API endpoint, and multi-factor authentication for privileged roles.
- Encryption in transit and at rest, and protected storage of secrets.
- Protection against common attacks (SQL injection, XSS, CSRF), guided by [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/).
- A complete, append-only audit trail of user and AI actions.
- Log content is treated as untrusted input, to protect the AI from instructions hidden inside logs.
- Personal data is masked before it is sent to an AI model, and only synthetic or anonymised data is used for development and testing.
- High-impact actions (blocking an IP address, disabling an account) are **not** executed automatically.

---

## Goals and success criteria (proposed targets)

| Goal | Target |
|---|---|
| Log collection and processing | At least 95% of 100,000+ synthetic test logs processed and shown within 60 seconds |
| Search speed | Typical searches in 3 seconds or less on 1 million+ records |
| Audit trail | 100% of alert and incident changes saved with user, time and reason |
| AI Guide | At least 90% of 30 test questions answered correctly |
| AI Log Explainer | At least 85% of explanations on 50+ test logs rated correct and understandable |
| AI safety | No action executed without user approval in 100% of test cases |

These numbers are targets to be validated in testing, not results.

---

## Project structure

> Proposed layout. It will be created during development.

```text
in-time/
├── docs/                 # Proposal, requirements and images
├── backend/              # API, log collector, log processing
├── frontend/             # Web interface
├── ai/                   # AI Guide and AI Log Explainer
├── data/                 # Synthetic log generator and test sets
├── deploy/               # Docker and deployment files
└── tests/                # Unit, integration, security and AI tests
```

---

## Getting started

Installation and run instructions will be added when the first working prototype is ready.

---

## Roadmap

- [x] Phase One: proposal (idea, market analysis, business model, scope, plan)
- [ ] Phase Two: design and methodology
- [ ] Phase Two: prototype development (platform, log processing, AI models)
- [ ] Phase Two: testing and validation
- [ ] Phase Two: final report and defense

Dates are to be confirmed.

---

## Team

| Member | Role |
|---|---|
| Mohamed Badr Eldeen | Team Leader, Project Manager and Security |
| Marwan Osama | Backend, Integration and AI |
| Zaid | Frontend and UX |
| Ahmed Tarek Rihan | Security and Compliance |

**Supervisor:** to be confirmed
**University:** El Sewedy University of Technology

---

## Contributing

This is a university project, so contributions are limited to the team for now. Suggestions and bug reports are welcome through GitHub Issues.

---

## License

To be confirmed.
