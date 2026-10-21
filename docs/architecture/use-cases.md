# Use Cases — Workflow Step 03

> These use cases describe capabilities from the approved requirements. They
> do not grant roles or decide policies that remain open. Project Phase 02 is
> still the console application; this workflow step delivers documentation.

## Actors and access boundary

The named system roles are manager, employee, student, and guest (BR-002).
Role privileges are not inferred. The employee's borrow-request review action
is explicitly required (FR-009), but the role-by-action grant model remains
open (D12, D20, D30). Each use case below is therefore conditional on an
eventual approved permission where the requirements do not name the actor.

## Use-case catalog

| ID | Use case | Main outcome | Open boundary |
|---|---|---|---|
| UC-01 | Maintain catalog | An authorized operator records titles, copies, and categories. | Category taxonomy/cardinality D19; grants D30. |
| UC-02 | Search and view availability | A user with catalog access finds titles and sees copy-level availability. | Search behavior D31; access D12/D30; availability interpretation D11/D23. |
| UC-03 | Submit borrow request | A permitted requester submits a request with requester, target, and submission time recorded. | Target is title or eligible copy; eligibility and pending handling D11/D23. A request does not imply a reservation. |
| UC-04 | Review borrow request | An employee records an approval or rejection and decision time. | Employee review is required; pending expiry, rejection reason, and resubmission D23. Automatic working-hours enforcement D18 remains open. |
| UC-05 | Record a loan | For an approved borrow request, the system records a loan and due date. | Required by FR-014; creation timing, copy allocation, loan period, and due-date calculation D11/D13/D23. |
| UC-06 | Record reservation and waiting-queue demand | The system records title-associated reservation/queue records and presents applicable FIFO ordering. | Queue enrollment, allocation, hold/expiry, and ineligible-entry behavior D11 (including merged D21/D22/D39); equal timestamps D40. FIFO only orders requests already eligible for the same queue (BR-003). |
| UC-07 | Submit and review return request | A borrower submits a return request for an active loan; an authorized employee may review and record an outcome. | Whether every return is reviewed or exceptions are automatic D24; effective return date D25. |
| UC-08 | Submit and decide renewal request | A borrower submits a renewal request for an active loan and an outcome is recorded. | Eligibility, limits, decision authority, pending requests, and effect on due date D10/D13/D14/D23/D30. |
| UC-09 | View personal dashboard | A user views permitted personal library information. | Contents and role visibility D30/D32. |
| UC-10 | Receive in-app notification | The intended user can access a notification. | Event selection, read state, and retention D33. |
| UC-11 | Review audit history | An authorized reviewer accesses available significant-action history. | Event coverage, permitted roles, and retention D30/D34. |
| UC-12 | Record late-return fine | A fine can be recorded for a late return. | Formula, amount, grace period, cap, currency, and effective date D09/D25. No payment collection is implied (A2). |
| UC-13 | Produce and restore backup | An authorized operator produces a backup and follows the documented restore procedure. | Owner, storage, schedule, retention D16; availability and recovery targets D38; grants D30. |
| UC-14 | Use the initial interface | Users interact with the first application through a console. | Console language D07. Future REST and web front-ends use the shared core (FR-020–FR-022, R12). |

## Process notes

Requirement details are traceable in the
[functional requirements](../requirements/functional-requirements.md),
[business rules](../requirements/business-rules.md), and
[open-decision register](../open-decisions.md).

- Borrow approval and reservation are distinct outcomes/capabilities. FR-014
  requires a loan record for an approved borrow request, but the model does not
  claim that every request creates a reservation or that loan creation is
  immediate.
- FIFO is a confirmed ordering rule only within the same applicable queue and
  among requests already eligible for it. Queue membership, allocation, and
  tie-breaking are not settled by FIFO itself (D11, D40).
- Employee processing during working hours is an approved operational
  requirement. Whether software blocks, warns, or enforces based on hours,
  holidays, or time zone is open (D18).
- No use case here selects a recommendation from the Step 02 decision register.
  Every policy choice remains subject to explicit approval.
