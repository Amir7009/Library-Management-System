# Stakeholders — Library Management System

> Status: Phase 01 draft for approval · Date: 2026-10-15
> **[Approved]** roles are named in the project context
> ([AGENTS.md](../../AGENTS.md)). **[Assumed]** roles are inferred for
> planning and stand only until confirmed. Interests describe direction;
> concrete behaviors await the decisions referenced in the right column.

## System Roles vs Project Stakeholders

Only the first four rows are *system roles* (user accounts in the
application). The remaining stakeholders influence or judge the project but
do not necessarily log into the system.

| Stakeholder | Status | Interest | What success looks like for them | Open decisions they depend on |
|-------------|--------|----------|----------------------------------|-------------------------------|
| Library managers | [Approved] system role | Oversight: catalogue accuracy, circulation activity, overdue state, fines, audit trail | Trustworthy records and an audit trail they can rely on | D09, D13; report/export needs are a new open question |
| Library employees | [Approved] system role | Day-to-day circulation: process borrow requests during working hours (approved high-level requirement), loans, returns, renewals, queues | Console flows that are quick and make state transitions unambiguous | D10, D11, D13, D18; exact workflow steps await course spec |
| Students | [Approved] system role | Find books, borrow, reserve, renew, see their own status and notifications | Simple self-service in the console; timely in-app notifications | D10, D13; concurrent limits (new open question) |
| Guests | [Approved] system role | Whatever limited access the library grants them | Clarity about what they may and may not do | D12 (entirely open — nothing invented meanwhile) |
| Course instructor / graders | [Assumed] project stakeholder | Learning objectives, engineering discipline, honest reporting | Rules R01–R14 visibly followed; phased delivery; documentation current | Grading criteria (new open question) |
| Developers / maintainers (human and AI agents) | [Approved] process role (defined in AGENTS.md) | Clear durable instructions, modular core, low-friction handovers | AGENTS.md honored; core independent of any UI; decision register kept honest | — |
| System operators / backup owners | [Assumed] project stakeholder | Data safety: backups, recovery, logs | A documented recovery procedure that has been rehearsed successfully | Backup ownership and storage location (new open question) |

## Notes

- Stakeholder interests were derived from the approved project context and
  labeled accordingly; no privilege or workflow has been invented for any
  role (R08). Where a stakeholder's capability depends on an undecided
  value, the register reference is given instead.
- Open questions surfaced in Phase 01 are now registered:
  [../open-decisions.md](../open-decisions.md) D14 (concurrent
  borrowing/reservation limits), D15 (manager reports and exports), D16
  (backup ownership and storage), D17 (grading criteria), and D18 (automatic
  enforcement of working hours, holidays, and time zones — distinct from the
  approved operational requirement that employees process borrow requests
  during working hours).
