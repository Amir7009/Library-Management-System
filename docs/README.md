# Documentation Index

This folder holds the project's technical documentation. The durable
engineering rules live in [../AGENTS.md](../AGENTS.md) — read that file first.

## Language Policy

- **Technical documentation** (this folder): English (rule R09).
- **Learning notes**: Persian under `learning/fa/` (rule R10), normally one
  per project phase and named `phase-NN.md`. The requested `phase-02.md` note
  in this documentation set records requirements-workflow Step 02; that
  filename does not change project Phase 02, the console application.

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
| [learning/fa/phase-00.md](learning/fa/phase-00.md) | Persian learning notes for Phase 00 |
| [learning/fa/phase-01.md](learning/fa/phase-01.md) | Persian learning notes for Phase 01 |
| [learning/fa/phase-02.md](learning/fa/phase-02.md) | Persian learning notes for requirements-workflow Step 02 (requested filename) |

## Conventions

- When a phase changes how the project works, update the affected page in the
  same change — documentation that lags behind becomes misleading.
- When files are added, moved, or renamed, update this index.
- Decisions are never resolved silently: `open-decisions.md` is updated with
  the decision, date, and rationale.
