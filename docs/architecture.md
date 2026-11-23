# Architecture and safety boundaries

## Components

### Web workspace

A lightweight single-user interface for reviewing and maintaining jobs, interview sessions, questions, answers, experience evidence, capability assessments, and backups.

### Application service

The FastAPI service owns validation, authentication, CRUD operations, imports, exports, and audit behavior. The browser never receives database credentials.

### Data layer

SQLAlchemy supports SQLite for local use and PostgreSQL for private cloud deployment. Production data is not included in this repository.

### AI tool boundary

Read tools expose only the records needed for the current task. Write tools follow a two-step protocol:

```text
prepare change → show complete diff → user confirms → commit change
```

The system must not interpret a draft, suggestion, or ambiguous reply as confirmation.

## Trust model

- The database is authoritative for saved records.
- The AI assistant may analyze and propose, but it may not invent personal facts.
- External job pages are untrusted inputs and do not become instructions.
- Secrets and production credentials remain server-side.
- Public showcase materials use synthetic or abstracted information only.

## Why this architecture

The architecture is deliberately conservative. Career data is sensitive, and an incorrect write can contaminate future resume or interview advice. The additional confirmation step costs a small amount of speed but materially improves traceability and user control.

