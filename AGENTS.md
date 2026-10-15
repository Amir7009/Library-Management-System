# AGENTS.md — Engineering Instructions

Durable engineering instructions for everyone who works on this repository —
human contributors and AI agents alike. Read this file before making any
change. Rules here are changed only by deliberate decision, never silently.

Last reviewed: 2026-10-14 (Phase 00 — repository inspection and preparation).

## 1. Project Context

The Library Management System will manage:

- Managers, employees, students, and guests
- Books and their individual physical copies
- Borrow requests, reservations, waiting queues, and loans
- Return and renewal requests
- Due dates, renewal eligibility, and fines
- User profiles and in-app notifications
- Audit records and application logs
- Database backups and recovery procedures

### Delivery phases

1. **Console application** — the system begins as a console program.
2. **REST API** — introduced in a later phase.
3. **Web interface** — introduced after the REST API.

### Architectural constraints

- The shared application logic must not depend on the console interface.
  Console, API, and web are front-ends over the same core.
- The project stays a simple modular application — not a microservices
  architecture (R12).
- The application must not include AI features (R13).

Business rules that are not yet decided (for example fines, renewal
eligibility, waiting-queue policy, guest privileges) are listed in
[docs/open-decisions.md](docs/open-decisions.md) and must not be invented (R08).

## 2. Working Rules

Rules are numbered (R01–R14) so that plans, reviews, and reports can reference
them unambiguously.

| Rule | Meaning |
|------|---------|
| **R01** | Inspect the existing repository before changing anything. |
| **R02** | Check Git status, branch, configured remotes, existing files, README, and existing documentation before proposing or making changes. |
| **R03** | Never discard, overwrite, or revert pre-existing user changes. |
| **R04** | Do not create application business logic in a phase that has not explicitly authorized it. |
| **R05** | Do not install software on the user's computer. |
| **R06** | Do not commit or push changes automatically — the user reviews and commits. |
| **R07** | Never include passwords, API keys, tokens, database credentials, personal data, or backup files in Git. |
| **R08** | Do not silently invent unresolved business rules — record them as open decisions. |
| **R09** | Keep technical documentation in English. |
| **R10** | Write Persian learning notes under `docs/learning/fa/`. |
| **R11** | Explain technical decisions and their alternatives. |
| **R12** | Keep the project a simple modular application, not a microservices architecture. |
| **R13** | Do not introduce AI features into the library application. |
| **R14** | Work only within the scope explicitly authorized for the current phase. |

## 3. Repository Layout

```text
├── AGENTS.md                     # this file — durable engineering instructions
├── README.md                     # short project summary and links
├── .gitignore                    # what Git must not track (see docs/git-and-commits.md)
├── docs/
│   ├── README.md                 # documentation index and organization
│   ├── project-overview.md       # purpose, roles, domain glossary, phases
│   ├── development-workflow.md   # how each phase proceeds
│   ├── git-and-commits.md        # commit expectations, secrets policy
│   ├── open-decisions.md         # decisions awaiting clarification
│   └── learning/
│       └── fa/                   # Persian learning notes, one file per phase (R10)
│           └── phase-00.md
└── src/                          # application source — added in a later, authorized phase
```

`src/` does not exist yet; it will be created only when a code phase is
authorized (R04, R14).

## 4. Definition of Done (every phase)

A phase is finished only when all the following hold:

1. Every created or modified file is listed in the final report with its purpose.
2. Unresolved decisions are recorded in `docs/open-decisions.md`, not silently
   resolved (R08).
3. No secrets, credentials, personal data, or backup files were added (R07).
4. Documentation reflects the current state; Persian learning notes were
   written for the phase (R09, R10).
5. All changes are left uncommitted for user review (R06).
6. Claims in the report match reality — including "no tests were run" when no
   tests were run.
