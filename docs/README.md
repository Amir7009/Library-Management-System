# Documentation Index

This folder holds the project's technical documentation. The durable
engineering rules live in [../AGENTS.md](../AGENTS.md) — read that file first.

## Language Policy

- **Technical documentation** (this folder): English (rule R09).
- **Learning notes**: Persian under `learning/fa/` (rule R10), with workflow-step
  notes named `step-NN.md`. Workflow steps are documentation workflow units;
  they are distinct from project phases, which describe the delivery stages
  such as project Phase 02, the console application.

## File Map

| File | Contents |
|------|----------|
| [../AGENTS.md](../AGENTS.md) | Engineering rules R01–R14 and project context |
| [project-overview.md](project-overview.md) | Purpose, user roles, domain glossary, delivery phases |
| [development-workflow.md](development-workflow.md) | Phase protocol, agent collaboration, reporting |
| [git-and-commits.md](git-and-commits.md) | Commit expectations, secrets policy, `.gitignore` limits |
| [open-decisions.md](open-decisions.md) | Decisions deliberately left unresolved |
| [project/project-charter.md](project/project-charter.md) | Problem statement, objectives, phases, constraints, assumptions |
| [project/scope.md](project/scope.md) | In-scope / out-of-scope functionality with approval labels |
| [project/stakeholders.md](project/stakeholders.md) | Stakeholders and their interests |
| [project/success-criteria.md](project/success-criteria.md) | Verifiable success criteria for the initial console version |
| [requirements/functional-requirements.md](requirements/functional-requirements.md) | Testable functional requirements for requirements-workflow Step 02 |
| [requirements/non-functional-requirements.md](requirements/non-functional-requirements.md) | Quality requirements and unapproved target questions |
| [requirements/permissions-matrix.md](requirements/permissions-matrix.md) | Role/action grants and explicitly open permissions |
| [requirements/business-rules.md](requirements/business-rules.md) | Approved and user-directed rules, with unresolved policies kept open |
| [requirements/open-decisions.md](requirements/open-decisions.md) | Preserved D01–D18 plus Step 02 policy questions and unapproved recommendations |
| [architecture/domain-model.md](architecture/domain-model.md) | Requirements-derived conceptual entities and relationships for workflow Step 03 |
| [architecture/use-cases.md](architecture/use-cases.md) | Supported use cases and their unresolved policy boundaries |
| [architecture/state-machines.md](architecture/state-machines.md) | Request and loan states, confirmed invalid transitions, and undefined transitions |
| [architecture/domain-glossary.md](architecture/domain-glossary.md) | Domain terms and distinctions used by the Step 03 model |
| [architecture/architecture-overview.md](architecture/architecture-overview.md) | Proposed conceptual architecture boundaries and dependency direction for Workflow Step 04 |
| [decisions/ADR-0001-language-and-build.md](decisions/ADR-0001-language-and-build.md) | Pending proposal for language version, build, and testing tools |
| [decisions/ADR-0002-database-and-persistence.md](decisions/ADR-0002-database-and-persistence.md) | Pending proposal for database, persistence, and schema migration |
| [decisions/ADR-0003-application-architecture.md](decisions/ADR-0003-application-architecture.md) | Pending proposal for modular core boundaries and cross-cutting concerns |
| [decisions/ADR-0004-future-web-architecture.md](decisions/ADR-0004-future-web-architecture.md) | Conceptual, pending proposal for later REST, security, and web choices |
| [learning/fa/step-00.md](learning/fa/step-00.md) | Persian learning notes for project Phase 00 |
| [learning/fa/step-01.md](learning/fa/step-01.md) | Persian learning notes for project Phase 01 |
| [learning/fa/step-02.md](learning/fa/step-02.md) | Persian learning notes for requirements-workflow Step 02 |
| [learning/fa/step-03.md](learning/fa/step-03.md) | Persian learning notes for domain-modeling workflow Step 03 |
| [learning/fa/step-04.md](learning/fa/step-04.md) | Persian learning notes for architecture and technology decisions in workflow Step 04 |

## Conventions

- When a phase changes how the project works, update the affected page in the
  same change — documentation that lags behind becomes misleading.
- When files are added, moved, or renamed, update this index.
- Decisions are never resolved silently: `open-decisions.md` is updated with
  the decision, date, and rationale.
