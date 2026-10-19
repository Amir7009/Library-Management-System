# Business Rules — Requirements Workflow Step 02

> Status: Requirements documentation only. Open policies below remain open;
> recommendations are explicitly unapproved.

Each rule has a unique `BR-NNN` identifier. A rule is labeled with its source
and approval state so that a proposed policy cannot silently become binding.

| ID | Rule | Status |
|---|---|---|
| BR-001 | A catalogue book/title is distinct from each physical copy associated with it. | Approved project context; project-overview.md |
| BR-002 | The system recognizes manager, employee, student, and guest as the four named roles. Naming a role does not define its privileges. | Approved project context; privileges open (D12, D30) |
| BR-003 | Requests already eligible for the same applicable queue are ordered FIFO by recorded submission time. This does not determine eligibility, queue membership, reservation allocation, priority exceptions, or equal-timestamp tie handling (D40). | User-directed in this Step 02 prompt; broader policy D11 remains open |
| BR-004 | Employees process borrowing requests during working hours as an operational practice. This statement does not require software enforcement of hours, holidays, or time zones. | Approved high-level requirement (2026-10-15); automatic enforcement open (D18) |
| BR-005 | Library circulation is recorded in a virtual system; physical handover and shelf logistics are outside the application's stated scope. | Approved charter and scope |
| BR-006 | Fines may be recorded for late returns, but no fine amount or calculation is established by this baseline. | Approved capability; D09 remains open |
| BR-007 | A due date is recorded for an approved loan, but this baseline does not set the duration or calendar calculation. | Approved capability; D13 remains open |
| BR-008 | A renewal request is supported, but this baseline does not establish eligibility, limits, or an automatic renewal outcome. | Approved capability; D10 remains open |
| BR-009 | In-app notifications are the initial notification channel under scope assumption A4; this does not decide which events create notifications or read/retention behavior. | Approved scope assumption; event policy D33 remains open |

## Policies deliberately not fixed here

Staff membership, category taxonomy, waiting-list enrollment, reservation
expiration, pending-request lifecycle, return review, effective return date,
loan and renewal configuration, fine calculation, exact role grants, dashboard
visibility, notification events, audit visibility/retention, and backup
operations are tracked in
[open-decisions.md](open-decisions.md). Its recommendations are unapproved.
