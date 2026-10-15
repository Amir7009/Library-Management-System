# Project Charter — Library Management System

> Status: Approved for planning (Phase 01) · Date: 2026-10-15
> Sources of truth: [AGENTS.md](../../AGENTS.md) (rules R01–R14) and
> [../open-decisions.md](../open-decisions.md) (register D01–D13).
> This charter states goals and constraints. It deliberately avoids undecided
> values (loan durations, fine amounts, renewal limits, business hours,
> reservation expiry) — see [scope.md](scope.md) §4.

## 1. Problem Statement

A university library must keep reliable track of:

- which books exist and which individual physical copies are available,
- who is borrowing what and until when,
- who is waiting for a title,
- what is overdue and which fines apply,
- and a trustworthy record of what happened and when.

Without a dedicated system this bookkeeping is error-prone, invisible to
members (they receive no notifications), and hard to audit.

**The system is a virtual library management environment.** Physical handover
of books is not part of the application: borrowing, returning, and other
actions are *simulated by recording them in the system*. The system manages
the information of library operations — not the physical logistics of moving
books.

## 2. Project Objectives (goals)

Goals express direction; they are intentionally not individually testable
rules. Testable statements live in [success-criteria.md](success-criteria.md).

| # | Objective |
|---|-----------|
| G1 | Give the library one trustworthy catalogue of books and their individual physical copies. |
| G2 | Let each user role work through a clear, role-appropriate view of library operations. |
| G3 | Model the circulation lifecycle: borrow request → loan → return, plus renewal requests. |
| G4 | Support reservations and waiting queues so demand for a title is visible and fair. |
| G5 | Make time and money consequences visible: due dates, overdue state, fines. |
| G6 | Keep members informed through in-app notifications. |
| G7 | Preserve accountability: audit records for significant actions, logs for technical events. |
| G8 | Protect the data: documented backup and recovery procedures. |

## 3. Deliverables and Phases

| Phase | Deliverable | Status |
|-------|-------------|--------|
| 00 | Repository inspection and preparation | Done (commit `9c2e6f5`) |
| 01 | Project definition documents (this set) | This phase |
| next | **Console application** — the initial version; all functionality through a console interface | Authorized later, by decision |
| future | **REST API** over the same core | Future phase |
| future | **Web interface** over the same core | Future phase, after the API |

Architectural constraint (fixed): the shared application logic must not depend
on the console interface — console, API, and web are replaceable front-ends
over the same core.

## 4. Stakeholders (summary)

The four system roles come from the approved project context: **managers,
employees, students, guests**. Project-level stakeholders (instructor,
maintainers, operators) are identified in
[stakeholders.md](stakeholders.md), which also separates approved roles from
assumed ones.

## 5. Success Criteria (summary)

The initial version succeeds when the console application covers the approved
functionality, the shared core demonstrably runs without the console, and the
process criteria (documentation, decision register, no secrets) hold. The
full, verifiable list is in [success-criteria.md](success-criteria.md).

## 6. Known Constraints

**Technical**

- Target Java version is not yet ratified (D01 — IDE config suggests JDK 21,
  but that is not a project decision).
- No build tool chosen yet (D02); no test framework yet (D05).
- Persistence approach undecided (D03): DB engine, JDBC vs ORM, or file-based
  storage for the console phase.
- Simple modular application — not microservices (R12).
- No AI features in the application (R13).

**Operational**

- The initial user interface is console-only; console UI language is open (D07).
- Physical handover is out of the system's reach by design (virtual
  environment) — the system records operations, it does not control shelves.
- Notifications are in-app; no email/SMS channel is planned for the initial
  version (assumption A4 in [scope.md](scope.md)).
- Employees process borrowing requests during working hours — approved
  high-level operational requirement; automatic enforcement by the software
  is open (D18).
- All business parameters (fines, durations, limits, queue policy, guest
  privileges) await course specification (D09–D14) and must not be invented.

**Process**

- Work proceeds phase by phase within authorized scope only (R14).
- Changes are never committed or pushed automatically (R06).
- Technical documentation in English; Persian learning notes per phase
  (R09, R10).
- Secrets, credentials, personal data, and backups never enter Git (R07).

## 7. Assumptions

Assumptions are **not** approved requirements. Each stands only until the
user or course requirements confirm or reject it.

| # | Assumption | Consequence if wrong |
|---|------------|----------------------|
| A1 | A single library branch (no multi-branch modeling). | Data model needs a branch dimension. |
| A2 | Fines are *recorded* by the system; collecting payments (cash/online) is out of scope. | A payment workflow must be added. |
| A3 | The approved high-level requirement is operational: employees process borrowing requests during working hours (approved 2026-10-15). Whether the application must *automatically* enforce specific hours, holidays, and time-zone rules is undecided (D18); no hour values, calendars, or time-zone rules are defined. | If D18 decides for automatic enforcement, time-rule logic must be added. |
| A4 | In-app notifications only (no email/SMS/push). | An external channel integration is needed. |
| A5 | Data volumes are course-scale; no performance engineering is required. | Performance criteria and testing must be defined. |

## 8. Unresolved Questions

Tracked in the decision register
([../open-decisions.md](../open-decisions.md)): D01 Java version, D02 build
tool, D03 persistence, D05 test framework, D07 console UI language, D08
branching, D09 fines, D10 renewals, D11 reservations/queues (including any
expiry policy), D12 guest privileges, D13 loan durations and due dates,
D14 concurrent borrowing/reservation limits, D15 manager reports and
exports, D16 backup ownership and storage, D17 grading criteria, and D18
automatic enforcement of working hours, holidays, and time zones.

## 9. Change Control

This charter changes only by deliberate decision, recorded with date and
rationale (R11). The Approved / Assumption labeling must survive every edit:
nothing may silently migrate from "assumption" to "requirement" (R08).
