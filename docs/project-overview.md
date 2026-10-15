# Project Overview — Library Management System

> Status: Phase 00 — repository preparation. No application code exists yet.

## Purpose

The system manages the day-to-day operation of a university library:

- People: managers, employees, students, and guests
- Catalogue: books and their individual physical copies
- Circulation: borrow requests, reservations, waiting queues, loans, return
  and renewal requests
- Time and money: due dates, renewal eligibility, fines
- Users: profiles and in-app notifications
- Governance: audit records, application logs, database backups and recovery

## User Roles

| Role | Privileges |
|------|------------|
| Manager | To be defined by course requirements — not invented here (R08) |
| Employee | To be defined by course requirements — not invented here (R08) |
| Student | To be defined by course requirements — not invented here (R08) |
| Guest | To be defined by course requirements — see open decision D12 |

Role privileges are deliberately **not** described: they are business rules
that must not be invented (R08). They will be documented once the course
requirements decide them.

## Domain Glossary

Neutral definitions only — behavior and policies are open decisions
(see [open-decisions.md](open-decisions.md)).

| Term | Meaning |
|------|---------|
| Book | The catalogue entry describing a title; distinct from its copies |
| Physical copy | One individual, identifiable physical item of a book |
| Borrow request | A request to borrow a copy; its approval flow is an open policy |
| Reservation | A hold on a book or copy; policy open (D11) |
| Waiting queue | An ordered queue of people waiting for a title; policy open (D11) |
| Loan | An active borrowing of a copy by a person, with a due date |
| Return request | A request to give a borrowed copy back |
| Renewal request | A request to extend a loan; eligibility open (D10) |
| Due date | The date by which a loan must be returned |
| Renewal eligibility | Conditions under which a loan may be extended — open (D10) |
| Fine | A monetary penalty related to late returns; calculation open (D09) |
| User profile | A person's account details in the system |
| Notification | An in-app message produced by the system for a user |
| Audit record | A recorded trace of a significant action, for accountability |
| Application log | Technical log of application events |
| Backup / recovery | Procedures for database backups and restoration |

## Delivery Phases

1. **Phase 00 — Repository inspection and preparation** (this phase;
   documentation only)
2. **Console application** — first runnable version; all functionality through
   a console user interface
3. **REST API** — later phase
4. **Web interface** — after the REST API

## Fixed Architectural Constraints

- The shared application logic must not depend on the console interface —
  console, API, and web are front-ends over the same core.
- Simple modular application, not a microservices architecture (R12).
- No AI features in the application (R13).

## Deliberately Undecided

Business rules (fines, renewal limits, waiting-queue policy, guest privileges,
loan durations) and technical choices (target Java version, build tool,
persistence) are listed in [open-decisions.md](open-decisions.md) and are not
invented here.
