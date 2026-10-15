# Success Criteria — Initial Console Version

> Status: Phase 01 draft for approval · Date: 2026-10-15
> Basis: capabilities marked [Approved] in
> [scope.md](scope.md) and the
> [charter](project-charter.md). Criteria deliberately avoid the undecided
> values (D09–D13): where a behavior depends on an open decision, the
> criterion verifies the *mechanism*, not the numbers.
> Acceptance authority: the user, and course requirements once provided.

## Functional Criteria (initial console version)

| # | Criterion | Depends on |
|---|-----------|------------|
| SC1 | Books and their individual physical copies can be created, found, and maintained through the console. | [Approved] catalogue scope |
| SC2 | User accounts can be created and stored for all four roles (manager, employee, student, guest); role-specific behavior activates per decisions D10–D13 as they are made — no role privilege is implemented from invention. | [Approved] roles; privileges [Open] |
| SC3 | End-to-end simulated circulation works: a borrow request becomes a loan with a due date, the copy is returned, and the loan history is visible. | [Approved]; durations [Open] (D13); borrowing limits [Open] (D14); automatic hours enforcement [Open] (D18) |
| SC4 | A reservation and a waiting queue can be recorded for a title and viewed in order. | [Approved]; policy [Open] (D11) |
| SC5 | A late return can have a fine recorded against it (calculation per D09 once decided). | [Approved] capability; amounts [Open] |
| SC6 | Relevant events produce in-app notifications for the affected user. | [Approved]; channel per A4 |
| SC7 | Significant actions leave audit records; technical events appear in application logs. | [Approved] |
| SC8 | A backup can be produced and restored by following the documented procedure, and the restore has been rehearsed at least once. | [Approved] |

## Quality and Process Criteria

| # | Criterion |
|---|-----------|
| SC9 | The shared application core compiles and runs without any console dependency — the console is demonstrably a replaceable front-end. |
| SC10 | Build and test commands are documented and reproducible, per the D02 (build tool) and D05 (test framework) decisions. |
| SC11 | No secrets, credentials, personal data, or backup files exist anywhere in Git history (R07); a pre-commit audit has been run before each phase commit. |
| SC12 | Documentation reflects the current state at phase end; a Persian learning note exists for every phase (R09, R10); the decision register is updated, never silently resolved (R08). |

## Verification and Acceptance Rules

- Each criterion is reported honestly: verified, not verified, or blocked by
  an open decision — "not verified" is a valid, acceptable report state.
- A criterion blocked by an open decision (e.g., SC5's calculation) is
  satisfied for this version when the mechanism exists and the decision is
  the only missing piece.
- Criteria may be amended only by recorded decision, with date and rationale,
  in this file (R11).
