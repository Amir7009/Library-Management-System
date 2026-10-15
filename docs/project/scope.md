# Scope — Library Management System (Initial Console Version)

> Status: Phase 01 draft for approval · Date: 2026-10-15
> Labels used throughout:
> **[Approved]** — from the project context (see [AGENTS.md](../../AGENTS.md));
> **[Assumption]** — a reasonable default, not yet confirmed (charter §7);
> **[Open]** — deliberately undecided, register reference given.
> Nothing in this file invents values for loan durations, fine amounts,
> renewal limits, business hours, or reservation expiry.

## 1. In Scope — Initial Version (console)

All actions are performed **in the virtual environment**: the system records
operations; it does not manage physical handover. [Approved]

| Area | Capability | Status |
|------|------------|--------|
| Catalogue | Manage books and their individual physical copies | [Approved] |
| Membership | Manage user accounts in four roles: manager, employee, student, guest | [Approved] roles; privileges [Open] (D12 for guests; others await course spec) |
| Circulation | Borrow requests, approved into loans with due dates | [Approved]; durations [Open] (D13) |
| Circulation | Employees process borrowing requests during working hours | [Approved] as a high-level operational requirement (2026-10-15); automatic enforcement of hours/holidays/time zones [Open] (D18) |
| Circulation | Return processing | [Approved] |
| Circulation | Renewal requests | [Approved]; eligibility and limits [Open] (D10) |
| Demand | Reservations and waiting queues per title | [Approved]; policy incl. any expiry [Open] (D11) |
| Money | Record fines related to late returns | [Approved] capability; amounts [Open] (D09); collection out of scope (A2) |
| Users | User profiles | [Approved] |
| Communication | In-app notifications for relevant events | [Approved]; channel only in-app (A4) |
| Governance | Audit records for significant actions; application logs | [Approved] |
| Resilience | Database backup and recovery procedures | [Approved] |

## 2. Out of Scope — Initial Version

| Item | Rationale / status |
|------|--------------------|
| REST API | Future phase [Approved] |
| Web interface | Future phase, after the API [Approved] |
| Physical handover logistics (shelves, handover, hardware such as scanners/RFID) | Virtual environment by design [Approved] |
| AI features | Forbidden in the application (R13) [Approved] |
| Online fine payment / money collection | Assumption A2 — recording only |
| Email / SMS / push notifications | Assumption A4 — in-app only |
| Multi-branch support | Assumption A1 |
| Automatic enforcement of working hours, holidays, and time-zone rules | [Open] (D18) — the operational practice is approved (see §1); only automatic enforcement by the software is undecided. Do not build without a decision |
| Microservices architecture | Excluded by R12 [Approved] |

## 3. User Interface

- Initial version: **console interface only**. [Approved]
- Console UI language (English / Persian / both): [Open] (D07).
- The console is a replaceable front-end; the shared core must not depend on
  it. [Approved]

## 4. Explicitly Undecided Values and Policies

These are **not** defaults and **not** placeholders — they are empty until
the course specification decides them. Implementation of a rule that depends
on them may not begin before the decision is recorded.

| Value / policy | Register |
|----------------|----------|
| Loan durations and due-date rules | D13 |
| Fine amounts and calculation | D09 |
| Renewal eligibility conditions and limits | D10 |
| Waiting-queue and reservation policy, including whether reservations expire | D11 |
| Guest borrowing privileges | D12 |
| Concurrent borrowing/reservation limits per member | D14 |

## 5. Scope Boundaries Over Time

The initial version's scope is the console application above. Later phases
add the API and the web interface **over the same core** — no functionality
may exist only in the console layer.

## 6. Scope Change Control

Scope changes only by deliberate decision (R14): the change is agreed with
the user, this file is updated in the same change, and any affected entry in
[../open-decisions.md](../open-decisions.md) is resolved or added at the same
time. Approved items never silently become out-of-scope, and assumptions
never silently become requirements (R08).
